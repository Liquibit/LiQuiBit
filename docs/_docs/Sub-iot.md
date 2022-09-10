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

## Building instructions {#building}

To build the Push7 and DASH7 gateway application, clone the [LiQuiBit repository](https://github.com/Liquibit/LiQuiBit) and build it.

    $ git clone https://github.com/Liquibit/LiQuiBit
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

This will have created a build folder containing firmware for the Push7 and for the DASH7-modem of the IOWAY gateway. Both have a debug and release build. 

The debug build will enable logging and forward them over the UART port. Release will make sure everything is optimised for a long battery lifetime.

Thus the following are available:

| Board    | Type               | Filename               |
|----------|----------------------|----------------------|
| Push7 | Release      | /your/path/LiQuiBit/build/Push7-release/apps/push7_button/push7_button-full.hex      |
| Push7 | Debug      | /your/path/LiQuiBit/build/Push7-debug/apps/push7_button/push7_button-full.hex      |
| IOWAY | Release      | /your/path/LiQuiBit/build/IOWay-release/apps/gateway/gateway-full.hex      |
| IOWAY | Debug      | /your/path/LiQuiBit/build/IOWay-debug/apps/gateway/gateway-full.hex      |

