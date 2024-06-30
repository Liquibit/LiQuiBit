---
title: Introduction
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_Summary/
---

## EnergyTrackingCaMeX-IA

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\camex_energy_diagram.png" width="1000"/>

For this project, we developed a system for measuring and transmitting energy consumption data for high currents on the Arts et Métiers de Metz campus. The measurements are transmitted wirelessly using the DASH7 protocol, which has a medium range, and then sent to the internet using MQTT. The MQTT data is read by the Siemens MindSphere Internet of Things (IoT) platform for further analysis and storage. The goal of this project is to monitor energy usage in real-time and make informed decisions about energy management in the building.
To measure energy consumption, we are using specialized equipment such as Rogowski coils, which are designed to measure high currents without electrical contact. The wireless communication using the DASH7 protocol ensures that the data can be transmitted over a suitable distance, and the use of MQTT and the MindSphere platform allows the data to be easily accessed, analyzed, and integrated into other IoT applications.

All the used software for this project can be found in this repo: [https://github.com/Liquibit/EnergyTrackingCaMeX-IA](https://github.com/Liquibit/EnergyTrackingCaMeX-IA)