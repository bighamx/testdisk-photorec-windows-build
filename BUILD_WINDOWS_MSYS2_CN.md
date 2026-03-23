# TestDisk / PhotoRec Windows 构建说明

本文档记录了在 Windows 11 上使用 `MSYS2 + MinGW-w64 + Qt5` 构建 `TestDisk`、`PhotoRec` 和 `QPhotoRec` 的一套可复现流程。

## 本次构建环境

- 系统: Windows 11 x64
- 构建工具链: `MSYS2`
- 编译目标: `mingw64` / `x86_64-w64-mingw32`
- Qt 版本: `Qt 5.15.18`
- 仓库版本: `51df2f24c7de15e46c9ada329d59ef7ced180ba5`

## 安装 MSYS2

可通过 `winget` 安装:

```powershell
winget install --id MSYS2.MSYS2 --accept-source-agreements --accept-package-agreements --silent
```

安装完成后，使用 `C:\msys64\usr\bin\bash.exe` 进入 MSYS2 shell。

## 安装依赖

基础工具链:

```bash
pacman -Sy --noconfirm
pacman -S --noconfirm --needed \
  base-devel autoconf automake libtool pkgconf \
  mingw-w64-x86_64-binutils \
  mingw-w64-x86_64-crt \
  mingw-w64-x86_64-gcc \
  mingw-w64-x86_64-headers \
  mingw-w64-x86_64-libwinpthread \
  mingw-w64-x86_64-make \
  mingw-w64-x86_64-pkgconf \
  mingw-w64-x86_64-tools \
  mingw-w64-x86_64-winpthreads \
  mingw-w64-x86_64-ncurses \
  mingw-w64-x86_64-zlib \
  mingw-w64-x86_64-libjpeg-turbo
```

Qt 图形界面依赖:

```bash
pacman -S --noconfirm --needed \
  mingw-w64-x86_64-qt5-base \
  mingw-w64-x86_64-qt5-tools \
  mingw-w64-x86_64-qt5-imageformats
```

## 生成 configure

仓库是 autotools 工程，克隆后需要先生成 `configure`:

```bash
export PATH=/mingw64/bin:/usr/bin:$PATH
mkdir -p config
autoreconf --install -W all -I config
```

## 编译命令行版本

```bash
export PATH=/mingw64/bin:/usr/bin:$PATH
mkdir -p build-mingw64
cd build-mingw64
../configure --host=x86_64-w64-mingw32 \
  CC=x86_64-w64-mingw32-gcc \
  CFLAGS='-O2'
make -j4
```

生成文件位于:

- `build-mingw64/src/testdisk.exe`
- `build-mingw64/src/photorec.exe`
- `build-mingw64/src/fidentify.exe`

## 编译 Qt 版本

```bash
export PATH=/mingw64/bin:/usr/bin:$PATH
mkdir -p build-mingw64-qt
cd build-mingw64-qt
../configure --host=x86_64-w64-mingw32 \
  CC=x86_64-w64-mingw32-gcc \
  CXX=x86_64-w64-mingw32-g++ \
  CFLAGS='-O2' \
  CXXFLAGS='-O2'
make -C src -j4 qphotorec.exe
```

生成文件位于:

- `build-mingw64-qt/src/qphotorec.exe`

## 发布包整理

本次已整理出一个可直接运行的 Qt 版发布目录:

- `dist/windows-x64-qt/`

其中包含:

- `testdisk.exe`
- `photorec.exe`
- `fidentify.exe`
- `qphotorec.exe`
- Qt 运行库
- MinGW 运行库
- Qt 平台插件和图片插件

命令行版本目录:

- `dist/windows-x64/`

## 已知说明

- 本次构建成功生成了 Windows x64 可执行文件。
- `QPhotoRec` 需要的不仅是 `Qt5*.dll`，还需要 ICU、PCRE2、double-conversion、字体渲染等二级依赖。
- `windeployqt` 可以部署 Qt 主库和插件，但并不总会自动带齐全部 MinGW 依赖，因此发布前需要手动检查。
- 本次构建没有补齐 `ext2fs`、`ntfs`、`ntfs-3g`、`ewf`、`reiserfs` 等可选库，所以属于核心可用构建，而不是“全部可选特性开启”的构建。
