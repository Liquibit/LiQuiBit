---
title: The Push7 sensor
permalink: /docs/The-Push7-sensor/
---

## Capabilities

A devkit containing all sorts of sensors, three buttons and DASH7 communication while being battery powered and rechargeable. By default, the devkit contains a program able to send all relevant sensor data over DASH7 with configurable interval settings. The power consumption of the device is very low and the lifetime for the default application is about 1 year. All of this in a small form factor contained in a custom 3D printed enclosure allowing access to the buttons and USB port.

## Components

![]({{ site.baseurl }}/assets/img/push7.jpg)

## Default firmware

The device has a couple different states. We will first discuss the operational state.

### Operational state

Operational state gets activated by clicking the reset button (button marked with a circle) without holding any other buttons. In this state the device will periodically transmit all sensor values using DASH7. Besides that, the device will also transmit when any of the 3 user buttons is pressed or released. It will also transmit when the movement PIR sensor gets triggered, or the hall effect switch (magnet sensor) gets activated. Besides the actual sensors, the device will also periodically send its battery voltage level. This data can be used to estimate the remaining battery life. Every time a message is received by a nearby gateway, the blue led on the side will light up.

### Configuration state

Next up we have the configuration state. This state can be entered by holding the reset button, then holding the button marked '1' and then letting go of the reset button. After this 'button 1' can be released as well. While in the configuration menu you will be able to turn off specific sensors. For example, if we wish to turn off the transmission of the humidity/temperature sensor we would first press button 1 to view the state of the sensor. When the blue LED blinks once, it means the sensor was previously on, if it blinks twice, it means the sensor was already turned off. By pressing button 1 once more we can toggle the on/off state. Here is a list of button id's and their related sensors:

| Button combination             | Sensor                                 |
|--------------------------------|----------------------------------------|
| Button 1                       | Humidity/temperature                   |
| Button 2                       | Light                                  |
| Button 3                       | PIR                                    |
| Button 1 + Button 2            | Hall effect switch                     |
| Button 1 + Button 3            | Buttons                                |
| Button 2 + Button 3            | LED on when message successfully transmitted |
| Button 1 + Button 2 + Button 3 | *High transmission power                |

*: Default Push7 is configured to transmit at a lower transmission power to save battery, if it does not reach your gateway, it can be configured to use a higher power

### Interval configuration state

Interval configuration state is entered by holding the '2' button while resetting the device. This state is used to configure the transmission tresholds of the periodic sensors (humidity, temperature and light). The state initiates at a period of 0 seconds and you can add time by pushing the different buttons. Here is a list of the periods you can add by pushing the buttons:

| Button   | Period addition               |
|----------|----------------------|
| Button 1 | 30 seconds |
| Button 2 | 10 minutes                |
| Button 3 | 2 hours      |

Example: Configuring it to send every 2 hours and 11 minutes is done by pressing the following buttons in no particular order: one time button 3, one time button 2 and two times button 1.

The configured interval will be sent when entering operational state again (by resetting without holding any other buttons).

### Testing state

The next mode is the testing mode. It can be entered by holding the button marked '2' and '3' at the same time while resetting the device. In this mode each button press will trigger a specific sensor measurement/transmission. Here is a list of button id's - sensor combinations:

| Button   | Sensor               |
|----------|----------------------|
| Button 1 | Humidity/temperature |
| Button 2 | Light                |
| Button 3 | Battery voltage      |

### Sleep state

Lastly there is the sleep state. In this state the device won't do anything. It can be entered by holder the button marked '3' and pressing the reset button.

When moving from the sleep state/configuration state to operational state, the sensor will transmit all configuration files over DASH7.

## Specifications

|                                          |                                                                                         |
|------------------------------------------|-----------------------------------------------------------------------------------------|
| Supply                                   | LiPo battery 300mA, 3.7V                                                                |
| Charging                                 | Charging current: 100mA, charge with micro USB cable 5V                                 |
| Sleep power consumption                  | 5 µA                                                                                    |
| Sleep power consumption with PIR enabled | 15 µA                                                                                   |
| Sensors                                  | Humidity/temperature, light, hall effect switch, accelerometer, PIR movement (optional) |
| User interaction                         | charging LED (white), user LED (blue), 3 user buttons, 1 boot button, 1 reset button    |
| Size enclosure (mm)                      | 60x35x14                                                                                |
|                                          |                                                                                         |
