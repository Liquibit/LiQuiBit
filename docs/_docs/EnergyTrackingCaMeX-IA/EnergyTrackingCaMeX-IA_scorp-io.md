---
title: SCorp-io
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_scorp-io/
---

SCorp-io is a cloud-based platform designed to enhance industrial monitoring and control systems, particularly for SCADA (Supervisory Control and Data Acquisition) applications. Developed with a focus on simplifying the integration and management of industrial data, SCorp-io offers several key modules:

1. Connecter Module: This module enables the collection and local storage of data from various industrial devices. It ensures data security and reliability, even during network outages, by storing data locally and forwarding it to the cloud once connectivity is restored​​.

1. Designer Module: A no-code platform that allows users to design and customize their industrial applications. Users can create object models, interactive dashboards, and graphical representations of their equipment without needing to write code​.

1. Exploiter Module: Provides real-time monitoring and control from any device with internet access. This module supports secure access through protocols like OAuth2 and two-factor authentication, ensuring that users can safely monitor and manage their systems from anywhere​​.

SCorp-io aims to optimize industrial processes, reduce software ownership costs, and accelerate digital transformation in the industrial sector. The platform is tailored for industries like manufacturing, energy, and transportation, offering features such as real-time notifications, energy consumption dashboards, and integration with third-party systems like ERP and maintenance.

## MQTT API

As described in the [SCorp-io documentation](https://scorp-io.gitbook.io/guide-to-scorp-io/broker-public/configuration-mqtts), you can use MQTT to send data to the platform. This supports Sparkplug B or a similar implementation over MQTT.

We decided to use the MQTT implementation for this project. 

For every new device that sends to the gateway, the gateway will first send a "DBIRTH" message to provision the device on the platform and let SCorp-io know what fields it should expect.

Once the device is discovered, the gateway will send a "DDATA" message for each message the physical device sends. This will update the values of the pre-configured fields while assigning it to a new timestamp. 

Here is a list of steps that automatically get done on the gateway for each device:

1. Discover the device on topic: mqtts/<project_id>/DBIRTH/<edge_node_id>/<Device_ID>
    
    ```
    {
      "metrics" : [
        { "name":"Énergie apparente/Phase 1",         "dataType":"Long"},
        { "name":"Énergie apparente/Phase 2",         "dataType":"Long"},
        { "name":"Énergie apparente/Phase 3",         "dataType":"Long"},
        { "name":"Énergie active/Phase 1",            "dataType":"Long"},
        { "name":"Énergie active/Phase 2",            "dataType":"Long"},
        { "name":"Énergie active/Phase 3",            "dataType":"Long"},
        { "name":"Intensité/Phase 1",                 "dataType":"Integer"},
        { "name":"Intensité/Phase 2",                 "dataType":"Integer"},
        { "name":"Intensité/Phase 3",                 "dataType":"Integer"},
        { "name":"Tension/Phase 1",                   "dataType":"Short"},
        { "name":"Tension/Phase 2",                   "dataType":"Short"},
        { "name":"Tension/Phase 3",                   "dataType":"Short"},
        { "name":"Force du signal radio DASH7",       "dataType":"Short"},
        { "name":"Bouton pressé",                     "dataType":"Boolean"},
        { "name":"État de la liaison Modbus - DASH7", "dataType":"Boolean"},
      ]
    }
    ```

1. Every message the device sends will trigger a data message on topic: mqtts/<project_id>/DDATA/<edge_node_id>/<Device_ID>

    ```
    {
          "metrics" : [
            { "name":"Énergie apparente/Phase 1",         "dataType":"Long",    "timestamp":timestamp, "value":0},
            { "name":"Énergie apparente/Phase 2",         "dataType":"Long",    "timestamp":timestamp, "value":0},
            { "name":"Énergie apparente/Phase 3",         "dataType":"Long",    "timestamp":timestamp, "value":0},
            { "name":"Énergie active/Phase 1",            "dataType":"Long",    "timestamp":timestamp, "value":0},
            { "name":"Énergie active/Phase 2",            "dataType":"Long",    "timestamp":timestamp, "value":0},
            { "name":"Énergie active/Phase 3",            "dataType":"Long",    "timestamp":timestamp, "value":0},
            { "name":"Intensité/Phase 1",                 "dataType":"Integer", "timestamp":timestamp, "value":0},
            { "name":"Intensité/Phase 2",                 "dataType":"Integer", "timestamp":timestamp, "value":0},
            { "name":"Intensité/Phase 3",                 "dataType":"Integer", "timestamp":timestamp, "value":0},
            { "name":"Tension/Phase 1",                   "dataType":"Short",   "timestamp":timestamp, "value":0},
            { "name":"Tension/Phase 2",                   "dataType":"Short",   "timestamp":timestamp, "value":0},
            { "name":"Tension/Phase 3",                   "dataType":"Short",   "timestamp":timestamp, "value":0},
            { "name":"Force du signal radio DASH7",       "dataType":"Short",   "timestamp":timestamp, "value":80},
            { "name":"État de la liaison Modbus - DASH7", "dataType":"Boolean", "timestamp":timestamp, "value":True},
          ]
        }
    ```
    Where timestamp is the current time in milliseconds.
