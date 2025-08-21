Let's take a closer look at a few of the examples included in the STC3x Arduino Library

## Example 01 - Basic Readings

The first example demonstrates how to get basic CO<sub>2</sub> data from the sensor along with temperature measurements from the on-chip temperature sensor. It initializes the STC31 with default settings to measure CO<sub>2</su> in air up to 25% concentration. Open the example by navigating to **File** > **Libraries** > **SparkFun STC3x Arduino Library** > **Example1_BasicReadings**. Select your Board (Sparkfun RedBoard IoT if you're following along to the letter) and Port and click the "Upload" button. After the code finishes uploading, open the [serial monitor](https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-serial-monitor) with the baud set to **115200** and you should see CO<sub>2</sub> concentrations and temperature (in &deg;C) print out every second. Try breathing on the sensor and you should see the values move slightly (we only breath out roughly 4% CO<sub>2</sub>).

**Code to Note**

The STC31 has four measurement modes to adjust what gas/environment it's measuring in along with the percentage volume of CO<sub>2</sub>. Possible values for `setBinaryGas` are

``` c++
  //  STC3X_BINARY_GAS_CO2_N2_100   : Set binary gas to CO2 in N2.  Range: 0 to 100 vol%
  //  STC3X_BINARY_GAS_CO2_AIR_100  : Set binary gas to CO2 in Air. Range: 0 to 100 vol%
  //  STC3X_BINARY_GAS_CO2_N2_25    : Set binary gas to CO2 in N2.  Range: 0 to 25 vol%
  //  STC3X_BINARY_GAS_CO2_AIR_25   : Set binary gas to CO2 in Air. Range: 0 to 25 vol%

  if (mySensor.setBinaryGas(STC3X_BINARY_GAS_CO2_AIR_25) == false)
  {
    Serial.println(F("Could not set the binary gas! Freezing..."));
    while (1)
```

## Example 02 - PHT Compensation

The second example shows how to use the SHTC3 to send actual temperature and humidity data to the STC31 to improve the accuracy of the CO<sub>2</sub> data from the sensor. The example initializes the STC31 to measure in air at concentrations up to 25% volume, sets the temperature and humidity values to those measured by the SHTC3 and then sets the barometric pressure to an arbitrary value (840 millibars). Open the example by navigating to **File** > **Libraries** > **SparkFun STC3x Arduino Library** > **Example2_PHTCompensation**. After uploading, open the serial monitor with the baud set to **115200** and you should see the values set for pressure, temperature and humidity followed by CO<sub>2</sub> measurements print out every second:

<figure markdown>
[![Screenshot of example two serial printout](./assets/img/STC31_Example2.jpg){ width="600"}](./assets/img/CO2-Sensor-STC31-HG-Banner.png "Click to enlarge")
</figure>

**Code to Note**

Since we don't have a pressure sensor to provide real-time pressure data the example sets the barometric pressure to match the pressure at SparkFun headquarters (840 millibars). You'll most likely want to adjust this value to the pressure in millibars (mbar) to your location. For example, typical barometric pressure at sea level is typically ~1013 millibars.

``` c++
  //If we have a pressure sensor available, we can compensate for ambient pressure too.
  //As an example, let's set the pressure to 840 mbar (== SF Headquarters)
  uint16_t pressure = 840;
```

## Example 05 - Automatic Self Calibration

The fifth example demonstrates how to enable the STC31's automatic self calibration feature. Automatic calibration helps improve the STC31's accuracy when used in applications where the target gas is not present most of the time. Refer to the [STC31 Field Calibration Guide](./assets/component_documentation/Sensirion_TC_AN_STCxx_FieldCalibration_D1.pdf) for more information. Open the example by navigating to **File** > **Libraries** > **SparkFun STC3x Arduino Library** > **Example5_AutomaticSelfCalibration**. Once the code upload completes, open the serial monitor with the baud set to **115200** and after the sensor initializes, you should see "Forced Recalibration was successful" print out followed by "Automatic self calibration is enabled!". After these prints, the code will begin to print out CO<sub>2</sub> and temperature data from the STC31 once every second.

**Code to Note**

Before running the STC31 in automatic calibration mode, the example attempts to perform a forced recalibration with a concentration of 0%. This is used to improve the sensor's accuracy with a known reference value.

``` c++
if (mySensor.forcedRecalibration(0.0) == true) // Force a recalibration with a concentration of 0%
  {
    Serial.println(F("Forced Recalibration was successful!"));
  }
  else
  {
    Serial.println(F("Forced Recalibration FAILED! Please check the debug messages for more details"));
  }

```

