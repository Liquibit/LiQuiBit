---
title: The Push7 development kit
permalink: /docs/The-push7-development-kit/
---

## Purpose of the Push7 development kit

The Push7 development kit is a collection of 2 hardware components. The Push7 device and the IOWAY gateway. The kit shows the capabilities of the DASH7 wireless protocol with a multifunctional sensor device and a versatile gateway that links the DASH7 communication to the internet using MQTT

## Push7 development kit content

![](({{ site.baseurl }}/assets/img/dev_kit.jpg)

-   IOWAY gateway (top)

    -   The IOWAY gateway receives DASH7 data and forwards this to the internet using a WiFi connection.

-   Push7 (middle)

    -   The Push7 is a battery powered device that wirelesly sends all sorts of data using DASH7.

-   Antenna (bottom)

    -   The IOWAY gateway uses this antenna to DASH7 data.

-   Magnet

    -   This magnet can be detected by the Push7. Can be used to detect an opening door.

-   Mounting materials

    -   Double-sided adhesive tape and Velcro to mount the Push7.

## General flow

![]({{ site.baseurl }}/assets/img/push7_DEV_SETUP.png)

The Push7, running sub-iot firmware, communicates, using DASH7, with the IOWAY gateway. The IOWAY gateway in turn uses a WiFi connection to forward the data send by the Push7 to an MQTT broker. Home automation software in turn can subscribe to the MQTT data published by the IOWAY gateway to display the send data of the Push7.
