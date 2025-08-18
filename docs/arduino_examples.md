Let's take a closer look at a few of the examples included in the STC3x Arduino Library

## Example 01 - Basic Readings

The first example demonstrates how to get basic CO<sub>2</sub> readings from the sensor with static values for temperature, pressure and humidity. It initializes the sensor with default settings

**Code to Note**

The STC31 has four measurement modes to adjust what environment it's measuring in along with the percentage volume of CO<sub>2</sub>. 

``` c++

  if (mySensor.setBinaryGas(STC3X_BINARY_GAS_CO2_AIR_25) == false)
  {
    Serial.println(F("Could not set the binary gas! Freezing..."));
    while (1)
```

## Example 02 - PHT Compensation

The second example shows how to use the SHTC3 to send live temperature, pressure and humidity data to the STC31 to improve the accuracy of the CO<sub>2</sub> data from the sensor. 

## Example 05 - Automatic Self Calibration

The fifth example demonstrates how to enable the STC31's automatic self calibration feature. 