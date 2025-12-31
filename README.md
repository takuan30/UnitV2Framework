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

### Mac Host and Devcontainer Environment

This diagram shows the relationship between the **Mac host** and the **Devcontainer Linux environment** used for building M5Stack UnitV2 binaries.

Mac Host (arm64)
┌─────────────────────────────┐
│ /usr/bin                     │  ← Mac system binaries
│    ├── gcc (for arm64 Mac)  │
│    └── …                  │
│ /Users/kj/…                │  ← Home directory
└─────────────────────────────┘
│
│ Docker / Devcontainer
▼
Devcontainer Linux (aarch64)
┌─────────────────────────────┐
│ /usr/bin                     │  ← Linux binaries inside the Devcontainer
│    ├── arm-linux-gnueabihf-gcc │  ← Cross compiler for 32-bit ARM (M5Stack)
│    ├── arm-linux-gnueabihf-g++ │
│    └── gcc (for aarch64 Linux) │
│ /workspaces/UnitV2Framework    │  ← Project workspace
└─────────────────────────────┘
**Notes:**

- The Devcontainer is a **Linux environment isolated from the Mac host**, even though it runs on the Mac.  
- Cross-compilation for M5Stack UnitV2 is performed inside the Devcontainer using `arm-linux-gnueabihf-gcc` and `g++`.  
- Mac binaries (like `/usr/bin/gcc` for arm64) **cannot be used directly** for building 32-bit ARM Linux targets.  

## Requirements

### ARM Cross Toolchain

This project uses the **32-bit ARM Linux cross compiler** provided by Ubuntu/Debian packages.

- **C Compiler:** `arm-linux-gnueabihf-gcc`
- **C++ Compiler:** `arm-linux-gnueabihf-g++`

#### Installation

Install on Ubuntu/Debian systems with:

```bash
sudo apt-get update
sudo apt-get install gcc-arm-linux-gnueabihf g++-arm-linux-gnueabihf

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

Default Binary Location
After installation, the compilers are usually located at:
/usr/bin/arm-linux-gnueabihf-gcc
/usr/bin/arm-linux-gnueabihf-g++

You can verify the path with:
which arm-linux-gnueabihf-gcc
which arm-linux-gnueabihf-g++
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
