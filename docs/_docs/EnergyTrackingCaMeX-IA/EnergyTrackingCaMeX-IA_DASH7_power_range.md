---
title: DASH7 power range meter
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_DASH7_power_range/
---

<img src="{{ site.baseurl }}/assets/img/energyTrackingCaMeX-IA/power_range.jpg" width="400"/>

A compact device was developed to assess network strength visually, based on received signal strength acknowledgments from gateways. The device utilizes the [LiQuiBit Link7](https://docs.liquibit.be/docs/The-LINK7/) and a LINK7 add-on board with extra LEDs.

Powered by a small internal battery, rechargeable via the micro-USB connector underneath, the device initiates a range test when the button depicted in the image is pressed. During this test, messages are transmitted and the received signal strength is indicated by the LEDs. Below is the signal strength table:

- Signal strength < 50: all LEDs on -> very good signal
- Signal strength 50–70: LEDs 1-6 on -> good signal
- Signal strength 70–80: LEDs 1-5 on -> moderate signal
- Signal strength 80–90: LEDs 1-4 on -> weak signal
- Signal strength 90–100: LEDs 1-3 on -> very weak signal
- Signal strength 100–110: LEDs 1-2 on -> poor signal
- Signal strength > 110: LED 1 on -> very poor signal

The range test transmits messages every 2 seconds for 20 seconds, extendable by pressing the button during the test for an additional 20 seconds per press. This feature allows you to place the device in a location for thorough testing without physically holding it.

When a message is successfully acknowledged by the gateway, the corresponding LED will blink once. For instance, if the signal strength is 45, LED 7 blinks once while remaining lit. If no messages are acknowledged at the start of the test, LED 1 blinks once and remains off for subsequent attempts.

To halt the test prematurely or reset an unresponsive device, insert a pin in the hole to press the underlying reset button.


