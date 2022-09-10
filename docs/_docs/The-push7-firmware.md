---
title: The Push7 firmware
permalink: /docs/The-push7-firmware/
---

## Default firmware architecture

![]({{ site.baseurl }}/assets/img/architecture.png)

## Writing custom firmware

You can write your own applications instead of our default firmware. All drivers and the platform itself are available apart from the application. If you want to write your own firmware, create a new folder in the Sub-IoT-Stack/stack/apps folder. Add a CMakelist.txt like the one from the push7_button folder and add a file containing a ```void bootstrap()``` function. This will be the first function that is executed after initializing the platform and can be used to strap your application upon.

## Flashing custom firmware

Building the firmware is discussed in [the Sub-IoT page](../Sub-iot#Building-instructions). When your firmware is fully built without any errors, the firmware-files should be available in the build folder.

Make sure your Push7 is connected through the micro-USB to your computer.

Flashing the firmware is done through the [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html). 

Open up the programmer and select 'USB' as the source:

![]({{ site.baseurl }}/assets/img/STM32CubeProg-USB-source.png)

Now activate the bootloader on the Push7 by holding the reset button (with circle symbol) and the boot button (with triangle symbol), then first releasing the reset button and after the boot button. 

Click the refresh button next to the port. Your device should pop-up as one of the options. Select it and press the 'Connect' button.

![]({{ site.baseurl }}/assets/img/STM32CubeProg-USB-connected.png)

Now press the 'Open file' button and select your firmware file. Then select 'Download' and it will start flashing the device. When it's done, a pop-up will show 'File download complete'.

![]({{ site.baseurl }}/assets/img/STM32CubeProg-USB-done.png)