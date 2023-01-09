---
title: MODBUS to DASH7 device
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_MODBUS-to-DASH7/
---
<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\DASH7_MODBUS1.jpeg" width="800"/>
Our custom PCB contains a RS485 to serial converter module that was used to speed up development time. This module isolates the RS485 signal and serial signal, allowing us to easily communicate with the RS485 device using serial Modbus commands sent from the stm32 microcontroller on the PCB. In addition to the RS485 to serial converter, we also included a Semtech chip for DASH7 communication and various LEDs and buttons for debugging and reprogramming purposes. The PCB is designed to be easily integrated into a larger system, providing a reliable and efficient method for communication between devices. Screw terminals are used to connect the RS485 signal and 5 volt supply to the PCB. The form factor of the PCB is compadible with a off the shelf enclosure that can be mounted on a DIN rail. An external 868 Mhz antenna has to be connected with the on board SMA connector. As you can see on the picuture, the antenna is glued on the cover plate of the DIN rail enclosure, so care must be taken when opening up the device.


## Sub-IoT

The board utilizes firmware that was created with the Sub-IoT stack. For more information, please visit https://sub-iot.github.io/Sub-IoT-Stack/.

The firmware follows this process:

1. Reads out the energy measurement device through the serial Modbus-RS485 interface.
1. Collects active energy, reactive energy, and checks if the readout was successful.
1. Transmits this data using the DASH7 protocol.
1. Waits for an acknowledgement from the gateway to confirm receipt of the data.
1. If the acknowledgement is not received, retries sending the package a set number of times.
1. Sets a timer for 15 minutes to schedule the next readout.

## Modbus server

To read out energy consumption using the Modbus interface, the firmware first establishes a connection with the device using the Modbus protocol. It then sends a request for the energy consumption data to the device, specifying the address of the energy consumption registers in the device's memory. The device responds with the requested data, which the firmware receives and processes. The firmware can then use this data as needed, such as transmitting it to a gateway.
The addresses are specified in the datasheet of the energy measurement device: https://www.accuenergy.com/products/acurev-1310-din-rail-power-energy-meter/

## Reprogramming

1. To reprogram the modbus to DASH7 device, you will need to carefully open the cover of the device. This will expose the internal components, including the connector for the micro USB cable.
1. Attach a micro USB cable to the connector on the DASH7 device and your computer. This will allow you to transfer data between the device and the computer.
1. Hold the reset button (B2) and the boot button (B1) simultaneously. Then, release the reset button and then release the boot button. This will put the device into a state where it is ready to be reprogrammed.
1. Start the STM32CubeProgrammer software on your computer. This software will allow you to upload new firmware to the DASH7 device.
1. Open the programmer and select 'USB' as the source. This will tell the software to use the micro USB cable to communicate with the device.
1. Click the refresh button next to the port. Your device should appear as one of the options. Select it and press the 'Connect' button. This will establish a connection between the device and the software.
1. Now, press the 'Open file' button and select your firmware file. This file contains the new code that you want to upload to the device. Then, select 'Download' and the software will begin flashing the device with the new firmware. When the process is complete, a pop-up will show 'File download complete.' At this point, the reprogramming process is finished and the device will be running the new firmware.
