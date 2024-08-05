Arduino Core for Zephyr OS
==========================

This repository contains the manifest for building the Arduino Core for Zephyr OS.

Preparing the workspace
-----------------------

To install this, please create an empty Zephyr workspace directory, then 
follow the instructions below:

    export SDK_VER=0.16.8
    python3 -m venv venv
    source venv/bin/activate
    pip install west
    west init -m https://github.com/pillo79/zephyr-manifest
    west update
    pip install -r zephyr/scripts/requirements.txt
    rm -rf zephyr-sdk-${SDK_VER}
    curl https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v${SDK_VER}/toolchain_linux-x86_64_arm-zephyr-eabi.tar.xz | tar xv -C zephyr-sdk-${SDK_VER}/
    ln -nsf zephyr-sdk-${SDK_VER} zephyr-sdk

Building the Arduino Core
-------------------------

To build the Arduino core for Zephyr for a specific target, run the following
command:

    core/build.sh <board> <variant>

For example, to build the Arduino core for the Arduino Giga board, run:

    core/build.sh arduino_giga_r1//m7 arduino_giga_r1_m7
