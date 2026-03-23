# Windows Usage Guide

## Packages

This repository provides two Windows x64 package styles:

- Qt package: includes `qphotorec.exe`
- CLI package: includes `testdisk.exe`, `photorec.exe`, and `fidentify.exe`

## Before Running

1. Download the release asset from GitHub Releases.
2. Extract the zip file to a normal folder such as `C:\Tools\TestDisk`.
3. Do not run the executables directly from inside the zip file.

## Main Programs

### `qphotorec.exe`

Use this when you want a graphical interface for file recovery.

1. Start `qphotorec.exe`.
2. Select the disk or image.
3. Choose the partition.
4. Choose the destination directory for recovered files.
5. Start the recovery.

### `photorec.exe`

Use this when you prefer the terminal interface.

1. Open `photorec.exe`.
2. Select the disk or image.
3. Choose the partition and filesystem options.
4. Pick a destination folder on another disk if possible.
5. Start recovery.

### `testdisk.exe`

Use this when you need partition analysis or partition recovery.

1. Start `testdisk.exe`.
2. Create a log if needed.
3. Select the disk.
4. Choose the partition table type.
5. Run `Analyse` and review the detected partitions carefully before writing changes.

## Important Safety Notes

- Recover files to a different disk or partition when possible.
- Avoid writing to the damaged disk before recovery is complete.
- If you are unsure, start with read-only analysis and log collection.
- Partition repair can change disk metadata. Review every step carefully.

## Contents of the Qt Package

The Qt package includes:

- application executables
- Qt runtime DLLs
- MinGW runtime DLLs
- platform plugins
- image format plugins

## Known Scope of This Build

This Windows package is a practical redistribution build.
It does not claim to enable every optional upstream library.
