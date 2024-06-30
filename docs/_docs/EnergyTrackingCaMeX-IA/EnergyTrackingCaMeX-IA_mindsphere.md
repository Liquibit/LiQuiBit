---
title: Mindsphere
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_mindsphere/
---

SCorp-io is a cloud-based platform designed to enhance industrial monitoring and control systems, particularly for SCADA (Supervisory Control and Data Acquisition) applications. Developed with a focus on simplifying the integration and management of industrial data, SCorp-io offers several key modules:

Connecter Module: This module enables the collection and local storage of data from various industrial devices. It ensures data security and reliability, even during network outages, by storing data locally and forwarding it to the cloud once connectivity is restored​ (SCADA-as-a-service | SCorp-io)​​ (SCADA-as-a-service | SCorp-io)​.

Designer Module: A no-code platform that allows users to design and customize their industrial applications. Users can create object models, interactive dashboards, and graphical representations of their equipment without needing to write code​ (SCADA-as-a-service | SCorp-io)​.

Exploiter Module: Provides real-time monitoring and control from any device with internet access. This module supports secure access through protocols like OAuth2 and two-factor authentication, ensuring that users can safely monitor and manage their systems from anywhere​ (SCADA-as-a-service | SCorp-io)​.

SCorp-io aims to optimize industrial processes, reduce software ownership costs, and accelerate digital transformation in the industrial sector. The platform is tailored for industries like manufacturing, energy, and transportation, offering features such as real-time notifications, energy consumption dashboards, and integration with third-party systems like ERP and maintenance 



Scorp-io supports MQTT as a protocol for sending data to the platform. This means that devices that are connected to Scorp-io can use MQTT to publish data to the platform, and applications running on the platform can use MQTT to subscribe to data from these devices.

To use MQTT with Scorp-io, you will need to configure your devices to connect to the Scorp-io MQTT broker, and use the appropriate MQTT topics to publish and subscribe to data. You can then use Scorp-io's APIs and tools to access and analyze the data that is being transmitted over MQTT.

Using MQTT with Scorp-io allows you to easily and efficiently transmit large amounts of data from your connected devices to the platform, where it can be stored, processed, and visualized. It is a key component of the Scorp-io IoT ecosystem.

## MQTT API

First an agent needs to be created on the mindsphere platform. This process provides you with a certificate with which an mqtt connection can be made with the broker of mindsphere. The credentials of an agent is only able to establish and maintain one active connection to the IoT platform at a time.

To create the data model on mindsphere the following instructions were followed:

[https://documentation.mindsphere.io/MindSphere/howto/howto-send-data-from-mqtt-agent.html](https://documentation.mindsphere.io/MindSphere/howto/howto-send-data-from-mqtt-agent.html)

Here is a list of steps taken to send the data to mindsphere:

1. Instantiate model on topic: tc/camexia/camexia_dash7_gateway_1/o/amo_v3/m

  <html>
    <pre>

    {
      "id": "12314",
      "data":{
        "externalId":"<span style="color :#7636C9; ">Energy_4</span>",
        "typeModel":{
          "aspectTypes":[
            {
              "id":"<span style="color :blue; ">camexia.energy_4_AspectType</span>",
              "name":"energy_4_AspectType",
              "category":"dynamic",
              "scope":"private",
              "variables":[
                {
                  "name":"<span style="color :red; ">realEnergy</span>",
                  "dataType":"LONG",
                  "unit":"Wh",
                  "searchable":true,
                  "qualityCode":true
                },
                {
                  "name":"<span style="color :yellow; ">apparentEnergy</span>",
                  "dataType":"LONG",
                  "unit":"VAh",
                  "searchable":true,
                  "qualityCode":true
                },
                {
                  "name":"<span style="color :grey; ">validEnergy</span>",
                  "dataType":"BOOLEAN",
                  "searchable":true,
                  "qualityCode":true
                },
                {
                  "name":"<span style="color :green; ">linkBudget</span>",
                  "dataType":"INT",
                  "searchable":true,
                  "qualityCode":true
                }
              ],
              "description":"measured energy_4"
            }
          ],
          "assetTypes":[
            {
              "id":"<span style="color :#9B111E; ">camexia.energy_4_AssetType</span>",
              "name":"energy_4_AssetType",
              "parentTypeId":"core.basicasset",
              "aspects":[
                {
                  "name":"<span style="color :#422666; ">energy_4_Aspect</span>",
                  "aspectTypeId":"<span style="color :blue; ">camexia.energy_4_AspectType</span>"
                }
              ],
              "description":"Asset Type with energy measured",
              "instantiable":true,
              "scope":"private"
            }
          ]
        },
        "instanceModel":{
          "assets":[
            {
              "referenceId":"<span style="color :#CDA434; ">energy_4_AssetReference</span>",
              "parentReferenceId":"root",
              "typeId":"<span style="color :#9B111E; ">camexia.energy_4_AssetType</span>",
              "name":"energy_4_Asset",
              "description":"Asset with energy measured"
            }
          ]
        },
        "mappingModel":{
          "mappings":[
            {
              "dataPointId":"<span style="color :brown; ">realEnergy</span>",
              "assetReferenceId":"<span style="color :#CDA434; ">energy_4_AssetReference</span>",
              "aspectName":"<span style="color :#422666; ">energy_4_Aspect</span>",
              "variableName":"<span style="color :red; ">realEnergy</span>"
            },
            {
              "dataPointId":"<span style="color :orange; ">apparentEnergy</span>",
              "assetReferenceId":"<span style="color :#CDA434; ">energy_4_AssetReference</span>",
              "aspectName":"<span style="color :#422666; ">energy_4_Aspect</span>",
              "variableName":"<span style="color :yellow; ">apparentEnergy</span>",
            },
            {
              "dataPointId":"<span style="color :cyan; ">validEnergy</span>",
              "assetReferenceId":"<span style="color :#CDA434; ">energy_4_AssetReference</span>",
              "aspectName":"<span style="color :#422666; ">energy_4_Aspect</span>",
              "variableName":"<span style="color :grey; ">validEnergy</span>"
            },
            {
              "dataPointId":"<span style="color :#26666D; ">dataPoint4</span>",
              "assetReferenceId":"<span style="color :#CDA434; ">energy_4_AssetReference</span>",
              "aspectName":"<span style="color :#422666; ">energy_4_Aspect</span>",
              "variableName":"<span style="color :green; ">linkBudget</span>"
            }
          ]
        }
      }
    }
  </pre>

2. Subscribe to topic: tc/camexia/camexia_dash7_gateway_1/i/amo_v3/#  <br />


3. Publish to topic: tc/camexia/camexia_dash7_gateway_1/o/amo_v3/i

  <!-- <html> -->
    <pre>
    {
        "id": "Energy_4_DeviceInstantiationRequest",
        "data": {
            "modelExternalId": "<span style="color :#7636C9; ">Energy_4</span>",
            "parameterization": {
                "values": []
            }
        }
    }

    </pre>

4. (Optional) To test the connection, publish data to timeseries: tc/camexia/camexia_dash7_gateway_1/o/mc_v3/ts.

   <!-- <html> -->
  <pre>
   {
     "timeseries": [
       {
         "timestamp": "2022-12-01T20:05:10Z",
         "values": [
           {
             "dataPointId": "<span style="color :brown; ">realEnergy</span>",
             "value": 605,
             "qualityCode": "0"
           },
           {
             "dataPointId": "<span style="color :orange; ">apparentEnergy</span>",
             "value": 15,
             "qualityCode": "0"
           },
           {
             "dataPointId": "<span style="color :cyan; ">validEnergy</span>",
             "value": "true",
             "qualityCode": "0"
           },
           {
             "dataPointId": "<span style="color :#26666D; ">dataPoint4</span>",
             "value": 87,
             "qualityCode": "0"
           }
         ]
       }
     ]
   }
  </pre>


note: This format also gets used in the raspberry pi gateway software.
</html>

## Energy measurement visualisation

<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\mindsphere_example.png" width="800"/>
