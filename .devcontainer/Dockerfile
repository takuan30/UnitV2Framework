# Base image: Ubuntu 20.04 arm64
FROM ubuntu:20.04

# Set non-interactive mode for tzdata
ENV DEBIAN_FRONTEND=noninteractive

# Install basic tools and ARM cross compiler
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    git \
    wget \
    curl \
    python3 \
    python3-pip \
    vim \
    tzdata \
    gcc-arm-linux-gnueabihf \
    g++-arm-linux-gnueabihf \
    && rm -rf /var/lib/apt/lists/*

# Optional: ensure PATH includes /usr/bin
ENV PATH="/usr/bin:${PATH}"

# Set default shell
SHELL ["/bin/bash", "-c"]