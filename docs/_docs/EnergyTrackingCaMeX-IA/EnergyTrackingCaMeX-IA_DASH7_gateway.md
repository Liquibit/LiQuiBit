---
title: DASH7 gateway
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_DASH7_gateway/
---
# Overview

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\gateway1.jpg" width="600"/>
<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\gateway2.jpg" width="600"/>

 A gateway was set up to receive messages using the DASH7 protocol and then forward them over MQTT (Message Queuing Telemetry Transport). The gateway consists of two components: an IOWAY device and a Raspberry Pi. The IOWAY device is responsible for receiving the DASH7 messages, but it can only connect to the internet wirelessly. Therefore, the Raspberry Pi, which can support a wired internet connection, is used to provide internet access to the system. The Raspberry Pi and IOWAY device communicate with each other using the UART (Universal Asynchronous Receiver/Transmitter) protocol, which is a standard for serial communication transmission of data. Together, the Raspberry Pi and IOWAY device receive the DASH7 messages, and the Raspberry Pi forwards them over MQTT.

## Raspberry pi 

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\rpi.jpg" width="600"/>

The Raspberry Pi is running a Python script that uses the PYD7A library to convert ALP (Application Layer Protocol) messages into MQTT (Message Queuing Telemetry Transport) packages. The ALP messages are coming from the IOWAY device via a serial connection.

The PYD7A library is a Python library specifically designed to work with the DASH7 Alliance Protocol (D7A), which is a wireless communication protocol that uses the ALP as its application layer. The PYD7A library provides functions and classes that can be used to easily parse and encode D7A messages in Python.

In this case, the Python script is using the PYD7A library to convert the ALP messages received from the IOWAY device over the serial connection into MQTT packages, which can then be transmitted over a network. This allows the Raspberry Pi to receive the ALP messages from the IOWAY device and forward them using the MQTT protocol.

The format of these MQTT packages is determined by the mindsphere IOT platform.

Monit is used to ensure this script keeps running and is started when the Raspberry pi is rebooted. The device also keeps track of all received data in a text file. This can be used for debugging and recovering lost data.

## IOWAY

<img src="{{ site.baseurl }}/assets/img/ioway.jpg" width="600"/>

The IOWAY is a device that has been repurposed to function as a transceiver for the DASH7 communication protocol. It contains a Wi-Fi chip, but this has been disabled for the current use case. Instead, the device uses a serial to USB chip to transfer ALP (application layer protocol) messages from a microcontroller to a Raspberry Pi. Instructions on how to reprogram the firmware can be found here: https://docs.liquibit.be/docs/The-IOWAY-firmware/
Since the device is mounted in an enclosure with the raspberry pi, it is recommended to use a usb a extension cable to connect the IOWAY to your computer when reprogramming.
