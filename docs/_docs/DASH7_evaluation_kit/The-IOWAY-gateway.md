---
title: The IOWAY gateway
permalink: /docs/The-IOWAY-gateway/
---

## Capabilities

The IOWAY PCB contains two elements. A minimal Link7 and an [Olimex ESP32-PoE](https://www.olimex.com/Products/IoT/ESP32/ESP32-POE/open-source-hardware).

The Link7 provides us with DASH7 communication. An external antenna should be attached to the SMA connector and all received data will be forwarded to the next module.

The Olimex ESP32-PoE is connected to this Link7 and takes care of the internet connection through Wi-Fi or ethernet. This board is programmable without any interaction and provides Power over Ethernet capabilities to the entire setup. It is a proven, open-source hardware design

The serial-to-USB converter allows us to easily reprogram the other two chips. It also allows us to view logs from either microcontroller during development.

The ESP32 chip takes care of the internet connection through Wi-Fi communication. Two buttons are provided to interact with the ESP32: a reset button and the boot button. However, these buttons won't be necessary as the serial-to-USB converter also toggles the boot and reset pins without any extra user-interaction.

The last chip provides us with DASH7 communication. An external antenna should be attached to the SMA connector. Two buttons are available to interact with the DASH7 modem: a reset button and a boot button.

## Components

![]({{ site.baseurl }}/assets/img/gw.jpg)


## Default firmware

### ESP32

On boot the gateway esp32 will become a WiFi access point. When connected to the access point, we can interact with the IOWAY by going to the IP address of the device or to <http://dash7-gateway.local/>. The following image shows the webpage that should be displayed: <img src="{{ site.baseurl }}/assets/img/IOWAY_interface.png" width="400" height="400"/>

Here we need to fill in the WiFi credentials of the access point we want our gateway to connect to and the MQTT broker details. See [Home Assistant-integration](../Home-assistant-integration) for more info about connecting to your Home Assistant instance.

After filling in the details and pressing the submit button the device will disconnect as access point and connect to the chosen WiFi access point. The same webpage can now be reached with the IP address assigned by the router or by going to <http://dash7-gateway.local/>.

### DASH7 modem

The DASH7 modem will forward the received DASH7 messages to the ESP32. If the ESP32 has an internet connection and an MQTT broker address, it will forward these messages to the MQTT broker. Additionally, it will blink the LED whenever it receives a DASH7 messages. This feature can be turned off by pressing the user button marked '1'.

## Specifications

|                            |                                                                      |
|---------------------|---------------------------------------------------|
| Supply                     | Typ: 5V (regulated to 3.3V)                                          |
| Power consumption          | Max: 500 mA                                                          |
| TX power                   | Max: 20 dB                                                           |
| Transmit/receive frequency | 858 Mhz, 2.4 Ghz                                                      |
| Wireless capabilities      | DASH7, WiFi, Bluetooth                                               |
| User interaction           | 4 buttons for reprogramming, 1 user button, 1 power led, 2 user leds |
| Size (mm)                  | 115X34X10                                                            |

