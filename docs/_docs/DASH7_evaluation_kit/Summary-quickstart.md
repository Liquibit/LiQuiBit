---
title: Quickstart
permalink: /docs/Summary-quickstart/
---

## DASH7 evaluation kit

![]({{ site.baseurl }}/assets/img/dev_kit.jpg)

The DASH7 evaluation kit comprises three distinct hardware components, each serving a unique purpose, making it an adaptable and comprehensive solution. Included in the kit are the Push7, Link7, and the IOWAY gateway. This kit effectively demonstrates the capabilities of the DASH7 wireless protocol through a multifunctional sensor device, a sensor that can be tailored to specific needs, and a flexible gateway that establishes a connection between DASH7 communication and the internet via MQTT.

## Setting up the IOWAY

1.  Gather the required information for setting up the gateway

    1.  MQTT broker (username and password)

    2.  Decide if you want to use Wi-Fi or ethernet. If Wi-Fi is your interface of choice, gather the SSID and password.

2.  Connect the antenna

3.  Plugin the device in a USB power adapter or using Power over Ethernet

4.  If you chose the setup using Wi-Fi, connect to the Wi-Fi access point of the IOWAY called DASH7-gateway or scan the following QR code <img src="{{ site.baseurl }}/assets/img/qr-code_wifi.png" width="200" height="200"/>

5.  Go the device webpage: <http://dash7-gateway.local> or scan the following QR code <img src="{{ site.baseurl }}/assets/img/qr-code-page.png" width="200" height="200"/>

7.  Fill in the required information and press submit

## Setting up the Push7

1.  Ensure the IOWAY is setup first

2.  Recharge the battery of the device using the micro USB connector. The white light will turn on when charging and turn off when the device is fully charged.

3.  Press the reset button (button marked with a circle) to exit the sleep state and wait a few moments

    \<insert picture of reset button press\>

4.  Press any user button (marked '1'/'2'/'3') and verify that the blue led lights up.

    \<insert picture of led blinking\>

5.  Check your MQTT broker to verify data is being received
