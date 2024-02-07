---
title: Sub-IoT
permalink: /docs/Sub-iot/
---

## General information

Sub-IoT is an open-source DASH7 and LoRaWAN stack. This stack is used for the Push7 and the DASH7 modem of the IOWAY gateway. You can find more information about the stack on [the documentation](https://sub-iot.github.io/Sub-IoT-Stack/).

## Tools

* [git](https://git-scm.com): using this tool, you can clone the [LiQuiBit repository](https://github.com/Liquibit/LiQuiBit).
* [Cmake](https://cmake.org)(v3.5 or greater): a flexible build system
* GCC-based toolchain: For example [GNU ARM Embedded](https://developer.arm.com/Tools%20and%20Software/GNU%20Toolchain) for ARM Cortex-M based platforms. By default, the build system assumes the GNU ARM Embedded toolchain is located in the PATH environment variable (meaning you can run arm-none-eabi-gcc without specifying the full path). The version of the GNU ARM Embedded toolchain that most well supports Sub-IoT is gcc-arm-none-eabi-8-2018-q4-major.
* [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html): multi-OS tool for programming STM32 products.

### Tool installation

#### Windows

When using windows, it is recommended to use [WSL](https://learn.microsoft.com/en-us/windows/wsl/install). This can be installed using the following command in a Windows Command Prompt in administrator mode:
   
     wsl --install

After installation, the wsl environment can be entered with the following command:
    
    wsl

When you've entered the wsl environment, you can follow the steps for Linux to get the required tools. You can find your files created in the WSL environment (the build firmware files for instance) in your windows environment using windows explorer with the following de address: 

    \\wsl.localhost\Ubuntu\home

We recommend to use visual studio code to write code for the sub-iot stack. Instructions on how to use visual studio code in combination with wsl are listed here: [https://code.visualstudio.com/docs/remote/wsl](https://code.visualstudio.com/docs/remote/wsl)

#### Linux (Ubuntu)

    sudo apt-get update -y
    sudo apt install cmake -y
    wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/8-2018q4/gcc-arm-none-eabi-8-2018-q4-major-linux.tar.bz2
    sudo tar xvf gcc-arm-none-eabi-8-2018-q4-major-linux.tar.bz2 --directory /opt/
    sudo ln -s /opt/gcc-arm-none-eabi-8-2018-q4-major/bin/arm-none-eabi-*  /usr/local/bin/

#### Mac OS

    brew install cmake
    wget https://developer.arm.com/-/media/Files/downloads/gnu-rm/8-2018q4/gcc-arm-none-eabi-8-2018-q4-major-mac.tar.bz2
    sudo tar xvf gcc-arm-none-eabi-8-2018-q4-major-mac.tar.bz2 --directory /opt/
    sudo ln -s /opt/gcc-arm-none-eabi-8-2018-q4-major/bin/arm-none-eabi-*  /usr/local/bin/


## Building instructions {#building}

To build the Push7 and DASH7 gateway application, clone the [LiQuiBit repository](https://github.com/Liquibit/LiQuiBit) and build it.

    $ git clone https://github.com/Liquibit/LiQuiBit --recursive
    $ cd LiQuiBit/
    $ cmake .
    -- Cross-compiling using gcc-arm-embedded toolchain
	-- Cross-compiling using gcc-arm-embedded toolchain
    ...
	-- Build files have been written to: /your/path/LiQuiBit
    $ make
    [  3%] Built target d7ap_fs
    [  5%] Built target HAL_COMMON
    ...
    [100%] Built target gateway.elf
    Built target ioway

This will have created a build folder containing firmware for the Push7 and for the DASH7-modem of the IOWAY gateway. Both have a release, debug and RTT-debug build. 

Release will make sure everything is optimised for a long battery lifetime.
The debug build will enable logging and forward them over the UART port. 
The RTT-debug build will enable logging and make it available through RTT.

Thus the following are available:

| Board    | Type               | Filename               |
|----------|----------------------|----------------------|
| Push7 | Release      | /your/path/LiQuiBit/build/PUSH7-release/apps/push7_button/push7_button-full.hex      |
| Push7 | Debug      | /your/path/LiQuiBit/build/PUSH7-debug/apps/push7_button/push7_button-full.hex      |
| Push7 | RTT-Debug      | /your/path/LiQuiBit/build/PUSH7-rtt-debug/apps/push7_button/push7_button-full.hex      |
| Push7 v3 | Release      | /your/path/LiQuiBit/build/PUSH7_V3-release/apps/push7_button/push7_button-full.hex      |
| Push7 v3 | Debug      | /your/path/LiQuiBit/build/PUSH7_V3-debug/apps/push7_button/push7_button-full.hex      |
| Push7 v3 | RTT-Debug      | /your/path/LiQuiBit/build/PUSH7_V3-rtt-debug/apps/push7_button/push7_button-full.hex      |
| LINK7 gateway | Release      | /your/path/LiQuiBit/build/Link7-gateway/apps/gateway/gateway-full.hex      |
| LINK7 example app | Release      | /your/path/LiQuiBit/build/Link7-release/apps/link7_basic/link7_basic-full.hex     |
|  LINK7 example app  | Debug      | /your/path/LiQuiBit/build/Link7-debug/apps/link7_basic/link7_basic-full.hex     |

