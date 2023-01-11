---
title: Energy measurement device
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_energy_measurement_device/
---

## Energy measurement

The chosen energy measurement device was required to be able to accurately measure large currents. As these high currents can pose challenges with traditional measuring techniques, a solution was selected that utilizes Rogowski coils.

A Rogowski coil is a type of current transformer that is used to measure alternating current (AC) in high-voltage power systems. It consists of a single, continuous wire or strip of conductive material that is wound in a spiral or helical shape around a core. The core can be made of a ferromagnetic material such as iron, or it can be made of a non-ferromagnetic material such as plastic or air.

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\acuct-flex-24-rogowski-coil-combo.jpg" width="400"/>

To measure current, the Rogowski coil is placed around the conductor whose current is to be measured. As the current flows through the conductor, it produces a magnetic field around the conductor. This magnetic field causes a current to be induced in the wire of the Rogowski coil. The magnitude of the induced current is proportional to the magnitude of the current flowing through the conductor.

The induced current in the Rogowski coil can be measured using a current transformer or a voltage transformer, and the measured value can be used to determine the magnitude of the current flowing through the conductor. Rogowski coils are often used in high-voltage power systems because they can measure high currents without the need for electrical contact with the conductor. This makes them suitable for use in hazardous or hard-to-reach environments.

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\acurev-1310-front-quarter-left.jpg" width="400"/>

The Acurev 1310 was chosen for this job because it offers several features that make it well-suited for the task. These features include support for a wide range of Rogowski coils for measuring different current ranges, the ability to calculate energy consumption for a three-phase system, and the capability to expose measurements through a RS485 Modbus interface.





## Modbus

Modbus is a protocol that enables communication between a server and one or more clients. In this case, the server is a modbus to DASH7 device and the client is the energy measurement device. Modbus defines a set of function codes that determine the type of action to be taken and the data to be transferred. These function codes include reading and writing holding registers (used to store data on the server), reading and writing input registers (used to store data input to the server from external devices), and reading and writing coils (used to represent the state of a digital output or the value of a digital input). The Acurev stores the calculated energy consumption in these registers, which can be read by the modbus to DASH7 device.



## Device settings

The schematic below shows the electrical setup:

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\acurev_schematic.png" width="500"/>

For this schematic, the following settings are required:

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\acurev_settings.png" width="800"/>

These settings can be configured either directly on the device or by using a MODBUS to USB device and the acuUtils software. For more details, refer to the official manual at the following link: [https://www.accuenergy.com/products/acurev-1310-din-rail-power-energy-meter/](https://www.accuenergy.com/products/acurev-1310-din-rail-power-energy-meter/)