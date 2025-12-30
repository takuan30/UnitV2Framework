M5Stack UnitV2 Framework

A minimal C++ framework for M5Stack UnitV2 (Linux-based AI camera),
focused on ARM Linux cross-compilation and NCNN + OpenCV development.

⸻

Overview

This repository provides:
	•	A reproducible Dev Container environment
	•	ARM Linux cross-compilation setup
	•	Example applications for UnitV2

Target device:
	•	M5Stack UnitV2
	•	Linux (glibc, hard-float)

⸻

Features
	•	ARM Linux cross toolchain (arm-linux-gnueabihf)
	•	NCNN inference support
	•	OpenCV-based image processing
	•	CMake build system
	•	VS Code Dev Container ready

⸻

Requirements

Host
	•	Docker
	•	Visual Studio Code
	•	VS Code Dev Containers extension

Target
	•	M5Stack UnitV2 (Linux)

⸻

Development Environment

All dependencies are provided inside the Dev Container.

You do not need to install:
	•	ARM toolchain
	•	OpenCV
	•	NCNN

on the host machine.

⸻

Build
mkdir -p build
cd build
cmake ..
make

Executable output:
bin/example

Run on UnitV2

scp bin/example user@<unitv2-ip>:/home/user/
ssh user@<unitv2-ip>
chmod +x example
./example

If required:

export LD_LIBRARY_PATH=/home/user/lib:$LD_LIBRARY_PATH

Notes
	•	ZBar is not used
	•	Target toolchain: arm-linux-gnueabihf (Linux + glibc)
	•	This project assumes a Linux-based runtime environment

⸻

License

MIT License

⸻

Author

Yasu Kajiyama