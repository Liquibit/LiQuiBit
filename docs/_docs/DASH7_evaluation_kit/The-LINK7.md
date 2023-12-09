---
title: The LINK7
permalink: /docs/The-LINK7/
---

## Capabilities

The Link7 is designed to facilitate the connection of various external sensors using DASH7 technology. It provides access to all microcontroller pins and features a charging circuit for battery power, as well as an FTDI chip for USB-based serial communication. Its versatility allows you to attach a wide range of sensors to suit your needs.

The on-board serial-to-USB converter allows us to easily reprogram the chip and view logs from the microcontroller during development as the PA2 and PA3 pins are connected to the UART chip. Additionally, the swd header can be used to facilitate a connection to a [J-link programmer](https://www.segger.com/products/debug-probes/j-link/).

## Components

![]({{ site.baseurl }}/assets/img/link7_dev.jpg)


## Default firmware

There is a simple example application added in the Sub Iot stack called link7-basic. It reuses some of the same components used for the Push7 sensor and serves as a clean slate to create a custom application. By default it sends a message upon a button press and sends the device state file every 5 minutes.

## Specifications

|                            |                                                                      |
|---------------------|---------------------------------------------------|
| Supply                     | Typ: 5V (regulated to 3.3V)                                          |
| Power consumption          | Max: 200 mA                                                          |
| TX power                   | Max: 20 dB                                                           |
| Transmit/receive frequency | 858 Mhz,                                                   |
| Wireless capabilities      | DASH7                                               |
| User interaction           | 1 reset button, 1 program button, 1 user button, 1 power led, 1 user led |
| Size (mm)                  | 115X34X10                                                            |

