---
title: DASH7 gateway
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_DASH7_gateway/
---
# Overview

<style>
    .image-container {
        display: flex;

    }

    .image-container img {
        margin-right: 10px; /* Adds some space between the images */
    }
</style>

<div class="image-container">
    <img src="{{ site.baseurl }}/assets/img/energyTrackingCaMeX-IA/gateway1.jpg" width="250"/>
    <img src="{{ site.baseurl }}/assets/img/energyTrackingCaMeX-IA/gateway2.jpg" width="520"/>
</div>


A gateway was developed to receive messages via the DASH7 protocol and transmit them over MQTT (Message Queuing Telemetry Transport). It comprises two main components: the LiQuiBit LINK7 for DASH7 message reception and a Raspberry Pi for internet connectivity. These devices communicate with each other using the UART (Universal Asynchronous Receiver/Transmitter) protocol. The Raspberry Pi serves to forward the received DASH7 messages over MQTT.

## Raspberry pi 

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\rpi.jpg" width="500"/>

The Raspberry Pi is running a Python script that uses the PyD7A library to convert ALP (Application Layer Protocol) messages into MQTT (Message Queuing Telemetry Transport) packages. The ALP messages are coming from the LINK7 via a serial connection.

The PyD7A library is written in Python specifically designed to work with the DASH7 Alliance Protocol (D7A), which is a wireless communication protocol that uses the ALP as its application layer. It provides functions and classes that can be used to easily parse and encode D7A messages in Python.

In this case, the Python script is using the PyD7A library to convert the ALP messages received from the LINK7 over the serial connection into MQTT packages, which can then be transmitted over a network. This allows the Raspberry Pi to receive the ALP messages from the LINK7 and forward them using the MQTT protocol.

The format of these MQTT packages is determined by the Scorp-IO platform. You can find their documentation [here](https://scorp-io.gitbook.io/guide-to-scorp-io/broker-public/configuration-mqtts).

Monit is used to ensure this script keeps running and is started when the Raspberry Pi is rebooted. 

The device also log all received data in a text file. This can be used for debugging and recovering lost data. This file gets rotated every week to make sure it's not filling up memory of the Raspberry Pi.

You can find Raspberry Pi gateway software [here](https://github.com/Liquibit/EnergyTrackingCaMeX-IA/tree/main/Gateway-software).

## LINK7

<img src="{{ site.baseurl }}\assets\img\link7_dev.jpg" width="500"/>

The [LiQuiBit LINK7](https://docs.liquibit.be/docs/The-LINK7/) is designed to connect various external sensors and wirelessly transmit their data using DASH7 technology. However, in our gateway, the device utilizes the serial to USB chip to transfer ALP (Application Layer Protocol) messages received over the Dash7 interface from the microcontroller to the Raspberry Pi. 

Instructions for reprogramming the firmware can be found [here](https://docs.liquibit.be/docs/The-LINK7-firmware/), and the LINK7 firmware is available [here](https://github.com/Liquibit/EnergyTrackingCaMeX-IA/tree/main/DASH7-firmwares).