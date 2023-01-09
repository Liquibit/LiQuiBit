---
title: Quickstart
permalink: /docs/Summary-quickstart/
---

## DASH7 evaluation kit

![]({{ site.baseurl }}/assets/img/dev_kit.jpg)

The DASH7 evaluation kit is a collection of 2 hardware components. The Push7 device and the IOWAY gateway. The kit shows the capabilities of the DASH7 wireless protocol with a multifunctional sensor device and a versatile gateway that links the DASH7 communication to the internet using MQTT.

## Setting up the IOWAY

1.  Gather the required information for setting up the gateway

    1.  WiFi credentials (SSID and password)

    2.  MQTT broker (username and password)

2.  Connect the antenna

3.  Verify the correct jumper configuration is selected <img src="{{ site.baseurl }}/assets/img/gw_operational.jpg" width="200" height="200"/>

4.  Plugin the device in a USB power adapter

5.  Connect to the WiFi access point of the IOWAY called DASH7-gateway or scan the following QR code <img src="{{ site.baseurl }}/assets/img/qr-code_wifi.png" width="200" height="200"/>

6.  Go the device webpage: <http://dash7-gateway.local> or scan the following QR code <img src="{{ site.baseurl }}/assets/img/qr-code-page.png" width="200" height="200"/>

7.  Fill in the required information (SSID info and MQTT info) and press submit

## Setting up the Push7

1.  Ensure the IOWAY is setup first

2.  Recharge the battery of the device using the micro USB connector. The white light will turn on when charging and turn off when the device is fully charged.

3.  Press the reset button (button marked with a circle) to exit the sleep state and wait a few moments

    \<insert picture of reset button press\>

4.  Press any user button (marked '1'/'2'/'3') and verify that the blue led lights up.

    \<insert picture of led blinking\>

5.  Check your MQTT broker to verify data is being received
