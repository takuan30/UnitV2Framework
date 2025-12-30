# M5Stack UnitV2 Framework

A minimal C++ framework for **M5Stack UnitV2 (Linux-based AI camera)**,
focused on **ARM Linux cross-compilation** with **NCNN** and **OpenCV**.

---

## Overview

This repository provides a simple and reproducible development environment
for building and running C++ applications on **M5Stack UnitV2**.

Target platform:
- M5Stack UnitV2
- Linux (glibc, hard-float)

---

## Features

- ARM Linux cross toolchain (**arm-linux-gnueabihf**)
- **NCNN** inference support
- OpenCV-based image processing
- CMake build system
- VS Code Dev Container support

---

## Requirements

### Host
- Docker
- Visual Studio Code
- VS Code Dev Containers extension

### Target
- M5Stack UnitV2 (Linux)

---

## Development Environment

All required tools and libraries are provided inside the **Dev Container**.

No manual installation is needed for:
- ARM cross toolchain
- OpenCV
- NCNN

---

## Build

```bash
mkdir -p build
cd build
cmake ..
make

The main program source file is located at test/main.cpp.
The resulting executable will be generated in bin/example.

If you try to build repeatedly, you shoud remove /build at first.

## Build  
```bash
rm -rf build
mkdir -p build
cd build
cmake ..
make

---

```md
## Project Structure

UnitV2Framework/
├── bin/                  # Output executables
├── build/                # Build directory (not tracked)
├── test/
│   └── main.cpp          # Main program source
├── platforms/
│   └── arm-toolchain.cmake
├── src/
│   └── ...               # Other source files
├── CMakeLists.txt
├── .devcontainer/
│   ├── Dockerfile
│   └── devcontainer.json
└── README.md

The primary source code for the example application is located in `test/main.cpp`.  
CMake automatically compiles this file into the `bin/example` executable.

License
MIT License
---
Author
Yasuhiro Kajiyama
