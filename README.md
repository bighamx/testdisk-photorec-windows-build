# TestDisk Windows 构建版

本仓库提供适用于 Windows 的 `TestDisk`、`PhotoRec` 和 `QPhotoRec` 构建工作流。该版本基于上游的 [`cgsecurity/testdisk`](https://github.com/cgsecurity/testdisk) 源码树进行优化，旨在为 Windows 用户提供开箱即用的二进制包。

[View English Documentation / 查看英文文档](README_EN.md)

## 软件功能介绍

### TestDisk (分区恢复)
`TestDisk` 是一款著名的开源数据恢复软件。它主要用于恢复因软件故障、病毒攻击或误操作而丢失的分区，或者修复由于这些原因导致的驱动器无法启动的问题。
- **修复分区表**: 能够分析磁盘结构并恢复已删除的分区。
- **引导修复**: 修复 FAT32、NTFS 的引导扇区（Boot Sector），以及 MFT 错误。
- **文件恢复**: 支持从已删除的分区中拷贝文件，也支持从多种文件系统（FAT, NTFS, ext2/3/4）中恢复已删除的文件。
- **跨平台**: 虽然本仓库专注于 Windows，但 TestDisk 原生支持多种操作系统。

### PhotoRec (文件数据恢复)
`PhotoRec` 是一款文件数据恢复软件，其特点是忽略文件系统层，直接通过文件头特征（File Signature）来恢复底层的媒体文件、文档、压缩包等。
- **不受文件系统损伤影响**: 即便文件系统已严重受损或已格式化，只要底层数据块未被覆盖，PhotoRec 就能将其搜寻并恢复出来。
- **支持数百种格式**: 能够识别多达数百种不同的文件扩展名。
- **QPhotoRec**: 本仓库提供了 PhotoRec 的 Qt 图形界面版本 (qphotorec.exe)，使普通用户可以通过点击操作轻松进行文件恢复，告别繁冗的命令行。

## 本仓库包含的工具
- `testdisk.exe`: 核心分区恢复工具。
- `photorec.exe`: 核心文件恢复命令行工具。
- `qphotorec.exe`: 易于操作的文件恢复图形界面工具。
- `fidentify.exe`: 用于文件签名识别的小工具。

## 发布版本 (Releases)
预编译的 Windows 软件包发布在 GitHub Releases 中：
- **Qt 构建版**: 包含 `qphotorec.exe` 及所有必要的运行时库。
- **CLI 构建版**: 仅包含命令行版程序，体积更小。

## 仓库布局
- [README_EN.md](README_EN.md): 英文文档
- [USAGE_WINDOWS_CN.md](USAGE_WINDOWS_CN.md): 中文用户使用指南
- [BUILD_WINDOWS_MSYS2_CN.md](BUILD_WINDOWS_MSYS2_CN.md): 中文 Windows 构建说明
- [RELEASE_NOTES_windows-x64-qt.md](RELEASE_NOTES_windows-x64-qt.md): Qt 版发布记录
- [RELEASE_NOTES_windows-x64-cli.md](RELEASE_NOTES_windows-x64-cli.md): CLI 版发布记录

## 上游项目信息
原始项目由 Christophe GRENIER 维护：
- 上游仓库: [cgsecurity/testdisk](https://github.com/cgsecurity/testdisk)
- 项目官网: [cgsecurity.org](https://www.cgsecurity.org/)

**注意**：本仓库是一个分发布和打包项目，旨在方便 Windows 用户，并非上游官方仓库。
