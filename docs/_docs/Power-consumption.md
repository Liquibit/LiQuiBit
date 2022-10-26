---
title: Power consumption
permalink: /docs/Power-consumption/
---

!This is only measured for **Push7** as the power consumption is not relevant for IOWAY as it's permanently plugged in!

## Estimated battery life
### Calculation tool
  <script>
    function calcule2() {
        var i = 0; for (i = 0; i <= 5; i++) { calcule(); }
    }
    function calcule() {
        if (Excel2Html.tx_power_selection.value == 0) {
            if (Excel2Html.pir_count.value == 0) 
            {
                Excel2Html.bat_life.value = ((300 / ((parseFloat(Excel2Html.magnet_count.value) * 0.000045 * 2) + (parseFloat(Excel2Html.pir_count.value) * 0.000045 * 2) + (parseFloat(Excel2Html.button_count.value) * 0.000045 * 2) + ((60 / parseFloat(Excel2Html.sensor_interval.value)) * 24 * 0.000045 * (light_sensor.checked + temperature_sensor.checked)) + ((60 / parseFloat(Excel2Html.battery_interval.value)) * 24 * 0.000045) + 0.007)) / 24 / 30).toFixed(2);
            }
            else 
            {
                Excel2Html.bat_life.value = ((300 / ((parseFloat(Excel2Html.magnet_count.value) * 0.000045 * 2) + (parseFloat(Excel2Html.pir_count.value) * 0.000045 * 2) + (parseFloat(Excel2Html.button_count.value) * 0.000045 * 2) + ((60 / parseFloat(Excel2Html.sensor_interval.value)) * 24 * 0.000045 * (light_sensor.checked + temperature_sensor.checked)) + ((60 / parseFloat(Excel2Html.battery_interval.value)) * 24 * 0.000045) + 0.015)) / 24 / 30).toFixed(2);
            }
        } 
        else 
        {
            if (Excel2Html.pir_count.value == 0) 
            {
                Excel2Html.bat_life.value = ((300 / ((parseFloat(Excel2Html.magnet_count.value) * 0.0001 * 2) + (parseFloat(Excel2Html.pir_count.value) * 0.0001 * 2) + (parseFloat(Excel2Html.button_count.value) * 0.0001 * 2) + ((60 / parseFloat(Excel2Html.sensor_interval.value)) * 24 * 0.0001 * (light_sensor.checked + temperature_sensor.checked)) + ((60 / parseFloat(Excel2Html.battery_interval.value)) * 24 * 0.0001) + 0.007)) / 24 / 30).toFixed(2);
            }
            else 
            {
                Excel2Html.bat_life.value = ((300 / ((parseFloat(Excel2Html.magnet_count.value) * 0.0001 * 2) + (parseFloat(Excel2Html.pir_count.value) * 0.0001 * 2) + (parseFloat(Excel2Html.button_count.value) * 0.0001 * 2) + ((60 / parseFloat(Excel2Html.sensor_interval.value)) * 24 * 0.0001 * (light_sensor.checked + temperature_sensor.checked)) + ((60 / parseFloat(Excel2Html.battery_interval.value)) * 24 * 0.0001) + 0.015)) / 24 / 30).toFixed(2);
            }
        }
        if(light_sensor.checked || temperature_sensor.checked)
        {
                document.getElementById("sensor_interval").style.display = "block";
                document.getElementById("sensor_interval_label").style.display = "block";
            }
        else
        {
                document.getElementById("sensor_interval").style.display = "none";
                document.getElementById("sensor_interval_label").style.display = "none";
        }
    }
</script>
<body onload="calcule2()">
<div class="container">
        <div class="row justify-content-center">
            <div class="title col-md-12 col-lg-10">
                <h3 class="mbr-section-title mbr-fonts-style align-center mb-4 display-2"><strong></strong></h3>
                <form name="Excel2Html">
                    <div class="rendered-form">
                        <div class="formbuilder-select form-group field-tx_power_selection">
                            <label for="tx_power_selection" class="formbuilder-select-label mbr-section-title">Transmit power of the sensor</label>
                            <select class="form-control" onchange="calcule2()" name="tx_power_selection" id="tx_power_selection">
                                <option value="0" selected="true" id="tx_power_selection-0">Tx power 15</option>
                                <option value="1" id="tx_power_selection-1">Tx power 17</option>
                            </select>
                        </div>
                        <div class="formbuilder-number form-group field-sensor_interval">
                            <label for="sensor_interval" id="sensor_interval_label" class="formbuilder-number-label mbr-section-title">Sensor transmit interval
                                (minutes)</label>
                            <input type="number" class="form-control" name="sensor_interval" onchange="calcule2()"
                                access="false" value="5" id="sensor_interval">
                        </div>
                        <div class="formbuilder-number form-group field-enabled_sensors">
                            <label for="temperature_sensor" class="formbuilder-number-label mbr-section-title">Enabled sensors </label><br>
                            <input type="checkbox" id="temperature_sensor" name="temperature_sensor" checked onchange="calcule2()">
                            <label for="temperature_sensor"> Temperature sensor enabled</label><br>
                            <input type="checkbox" id="light_sensor" name="light_sensor" checked onchange="calcule2()">
                            <label for="light_sensor"> Light sensor sensor enabled</label><br>
                        </div>
                        <div class="formbuilder-number form-group field-battery_interval">
                            <label for="battery_interval" class="formbuilder-number- mbr-section-title">Battery voltage transmit interval
                                 (minutes)</label>
                            <input type="number" class="form-control" name="battery_interval" onchange="calcule2()"
                                access="false" value="120" id="battery_interval">
                        </div>
                        <div class="formbuilder-number form-group field-magnet_count">
                            <label for="magnet_count" class="formbuilder-number-label mbr-section-title">Magnetic field
                                changes per day</label>
                            <input type="number" class="form-control" name="magnet_count" onchange="calcule2()"
                                access="false" value="12" id="magnet_count">
                        </div>
                        <div class="formbuilder-number form-group field-pir_count">
                            <label for="pir_count" class="formbuilder-number-label mbr-section-title">Movement detections per day</label>
                            <input type="number" class="form-control" name="pir_count" onchange="calcule2()"
                                access="false" value="0" id="pir_count">
                        </div>
                        <div class="formbuilder-number form-group field-button_count">
                            <label for="button_count" class="formbuilder-number-label mbr-section-title">Button presses per day</label>
                            <input type="number" class="form-control" name="button_count" onchange="calcule2()"
                                access="false" value="12" id="button_count">
                        </div>
                        <div class="formbuilder-number form-group field-bat_life">
                            <label for="bat_life" class="formbuilder-number-label mbr-section-title">Battery lifetime (months)
                                </label>
                            <input type="number" class="form-control" name="bat_life" disabled="disabled"
                                access="false" id="bat_life">
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</body>

### Table calculations
To calculate the estimated lifetime we start from the measured power consumption of transmitting a message and the sleep current.
The sleep current was considered in 2 cases (*A small arbitrary margin was taken to take the self discharge of the battery into account*):
* When the PIR sensor is turned on the considered sleep current is 15µA
* When the PIR sensor is turned off the considered sleep current is 7µA


For the current consumption of transmissions, we take into account how long the transmission takes, and the average current we consume during this period. We once again consider two cases:
* Tx power 15: 270ms - 14.4mA
* Tx power 17: 270ms - 32mA

Then, we calculate the average current consumption that is consumed when we have to transmit the selected amount of messages. We get this average value by considering how long we will be in the active current mode, by adding up all the required send messages, versus how long we are sleeping.

Finally, we take the battery capacity and divide this by the average current and convert this to the amount of months the battery would last. 

*Notes*
* The sleep current is still counted when transmitting for simplicity
* A button press/magnetic change/pir always result in 2 messages being send
* We consider a month to be 30 days in the tool for simplicity
* The used formula can be viewed in the html code of the page

## Power consumption optimizations
### Temperature/humidity
This sensor is already very low power when not in use (100nA), the current consumption cannot be further reduced. The sensor does not need to be initialized to enter low power mode. It only consumes more current during measurements.
### Pir sensor
The pir sensor, when placed on the board, consumes quite a bit of power. It needs to be initialized to enter the low power mode as we need to put it in "Wake Up" operation mode. In the other modes, the PIR will constantly provide raw data on the output. To allow the used to turn off the sensor completely, the vdd of the sensor was connected to a GPIO pin. For the push7 V2, the VDD pin is connected to PB14. For push7 V3, the VDD is connected to PB13
### Accelerometer
The accelerometer enters sleep mode (100nA) by default and does not need to be initialized.
### Light sensor
The light sensor does not need to be initialized to enter low power mode (500nA). It only consumes more current during measurements.

### Hall effect sensor
The hall effect sensor consumes about 500nA. On the push7 V2 it can be turned off by turning off pin PH0. The push7 V3 won't have this ability.