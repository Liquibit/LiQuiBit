---
title: MODBUS to DASH7 device
permalink: /EnergyTrackingCaMeX-IA/EnergyTrackingCaMeX-IA_MODBUS-to-DASH7/
---
<img src="{{ site.baseurl }}\assets\img\energyTrackingCaMeX-IA\DASH7_MODBUS1.jpg" width="800"/>

Our custom PCB features an isolated RS485 transceiver (TDH541S485S) that converts RS485 signals to UART signals. This allows seamless communication with RS485 devices using serial Modbus commands from the STM32 microcontroller on the PCB. Additionally, the PCB includes a Semtech chip for DASH7 communication, as well as various LEDs and buttons for debugging and reprogramming purposes.

Designed for easy integration into larger systems, this PCB offers a reliable and efficient communication method between devices. Screw terminals facilitate the connection of the RS485 signal and 5-volt supply to the PCB. The form factor is compatible with an [off-the-shelf enclosure](https://www.budind.com/product/general-use-boxes/din-rail-mount-multi-board-box-series/dmb-4771/#group=series-products&external_dimensions_group=0) that can be mounted on a DIN rail. An external 868 MHz antenna connects via the onboard SMA connector. A [flexible 868 antenna](https://www.molex.com/en-us/products/part-detail/2067640150) is mounted externally in the fuse box and linked using an [SMA plug to U.FL jack adapter](https://benl.rs-online.com/web/p/coaxial-adapters/7385939?searchId=9a1e18cb-c5df-4e7d-9f22-e701860b726d&gb=s) to the PCB's SMA connector.

The hardware design files are available here: [design files](https://github.com/Liquibit/EnergyTrackingCaMeX-IA/tree/main/Hardware).


## Sub-IoT

The board utilizes firmware that was created with [the Sub-IoT stack](https://sub-iot.github.io/Sub-IoT-Stack/).

The process followed by the firmware is:

1. Read out the energy measurement device through the serial Modbus-RS485 interface.
1. Collect active energy, reactive energy, current, voltage and check if the readout was successful.
1. Transmit this data using the DASH7 protocol.
1. Wait for an acknowledgement from the gateway to confirm receipt of the data.
1. If the acknowledgement is not received, retry sending the package.
1. Set a timer for 10 minutes to schedule the next readout.

Additionally, a feature was added that resets the Acurev accumulated energy data when the button on the Modbus-to-D7 device is pressed during power-on of the device.

You can find the entire firmware of the Modbus to DASH7 device [here](https://github.com/Liquibit/EnergyTrackingCaMeX-IA/tree/main/DASH7-firmwares).

## Modbus server

To read out energy consumption, the firmware first establishes a connection with the device using the Modbus protocol. It then sends a request for the energy consumption data to the device, specifying the address of the energy consumption registers in the device's memory. The device responds with the requested data. This data then gets processed and transmitted to the gateway.
The modbus registers are specified in [the datasheet of the energy measurement device](https://www.accuenergy.com/products/acurev-1310-din-rail-power-energy-meter/).

## Programming

1. To program the modbus to DASH7 device, you will need to remove the bottom screw terminal cover of the device. This will expose some of the internal components, including the connector for the micro USB cable.
1. Attach a micro USB cable to the connector on the DASH7 device and your computer. This will allow you to transfer data between the device and the computer.
1. Hold the reset button (B2) and the boot button (B1) simultaneously. Then, release the reset button and then release the boot button. This will put the device into a state where it is ready to be programmed.
1. Start the [STM32CubeProgrammer software](https://www.st.com/en/development-tools/stm32cubeprog.html) on your computer. This software will allow you to upload new firmware to the DASH7 device.
1. Open the programmer and select 'USB' as the source. This will tell the software to use the micro USB cable to communicate with the device.
1. Click the refresh button next to the port. Your device should appear as one of the options. Select it and press the 'Connect' button, establishing a connection between the device and the software.
1. Now, press the 'Open file' button and select your firmware file. This file contains the new code that you want to upload to the device. Select 'Download' and the software will begin flashing the device with the new firmware. When the process is complete, a pop-up will show 'File download complete.'.
1. Lastly, disconnect the micro USB cable and push the reset button (B2). At this point, the programming process is finished and the device will be running the new firmware.

Alternatively, the SWD connector, located next to the USB connector, can be used with a [J-Link programmer](https://www.segger.com/products/debug-probes/j-link/) to reprogram the device.