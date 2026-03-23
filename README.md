# TestDisk Windows Build

This repository packages a Windows-friendly build workflow for `TestDisk`,
`PhotoRec`, and `QPhotoRec`, based on the upstream
[`cgsecurity/testdisk`](https://github.com/cgsecurity/testdisk) source tree.

It is intended for people who want:

- ready-to-run Windows x64 release packages
- a reproducible `MSYS2 + MinGW-w64 + Qt5` build flow
- a simple public repository with build notes and release assets

## Included tools

- `testdisk.exe`: partition recovery and partition table repair
- `photorec.exe`: file recovery command-line tool
- `qphotorec.exe`: Qt graphical interface for PhotoRec
- `fidentify.exe`: file signature identification helper

## Releases

Prebuilt Windows packages are published in GitHub Releases.

- Qt build: includes `qphotorec.exe` and bundled Qt runtime
- CLI build: includes `testdisk.exe`, `photorec.exe`, and `fidentify.exe`

## Repository Layout

- [BUILD_WINDOWS_MSYS2_CN.md](BUILD_WINDOWS_MSYS2_CN.md): Windows build notes in Chinese
- [USAGE_WINDOWS_EN.md](USAGE_WINDOWS_EN.md): end-user instructions in English
- [USAGE_WINDOWS_CN.md](USAGE_WINDOWS_CN.md): end-user instructions in Chinese
- [RELEASE_NOTES_windows-x64-qt.md](RELEASE_NOTES_windows-x64-qt.md): Qt release notes
- [RELEASE_NOTES_windows-x64-cli.md](RELEASE_NOTES_windows-x64-cli.md): CLI release notes
- [INSTALL](INSTALL): upstream generic build instructions

## Build Summary

The Windows builds in this repository were produced with:

- Windows 11 x64
- `MSYS2`
- `mingw-w64-x86_64`
- `Qt 5.15.18`

The current packaged source snapshot tracks upstream commit:

- `51df2f24c7de15e46c9ada329d59ef7ced180ba5`

## Notes

- This repository keeps the upstream source tree and adds packaging-oriented documentation.
- The bundled Windows builds focus on a working, redistributable package.
- Optional filesystem libraries such as `ext2fs`, `ntfs`, `ntfs-3g`, `ewf`, and `reiserfs` are not fully enabled in this packaged build.

## Upstream Project

The original project is maintained by Christophe GRENIER:

- Upstream repository: [cgsecurity/testdisk](https://github.com/cgsecurity/testdisk)
- Project site: [cgsecurity.org](https://www.cgsecurity.org/)
- Upstream documentation: [testdisk_documentation](https://github.com/cgsecurity/testdisk_documentation)

This repository is a redistribution and packaging effort for Windows users and is not the upstream project.
