

## Example 01 - Basic Readings

Example 1 shows how to get basic CO<sub>2</sub> and temperature data from the STC31. It initializes the sensor with default settings to measure CO<sub>2</sub> in air up to 25% concentration. Open the example in your preferred Python interpreter and run it. You should see some initialization messages print out followed by CO<sub>2</sub> concentration and temperature data every second. Try breathing on the sensor or holding it up to a different CO<sub>2</sub>C source and you should see the values change.

**Code to Note**

The STC31 has four different measurement modes available for the `set_binary_gas()` function. This lets you change between measuring either up to 25% or 100% CO<sub>2</sub> concentration measured either in nitrogen (N<sub>2</sub>) or air. You can adjust the measurement mode by modifying the line of code below with the corresponding concentration/gas:

``` py
	# Possible values are:
	# kBinaryGasCO2N2_100   : Set binary gas to CO2 in N2.  Range: 0 to 100 vol%
	# kBinaryGasCO2Air_100  : Set binary gas to CO2 in Air. Range: 0 to 100 vol%
	# kBinaryGasCO2N2_25    : Set binary gas to CO2 in N2.  Range: 0 to 25 vol%
	# kBinaryGasCO2Air_25   : Set binary gas to CO2 in Air. Range: 0 to 25 vol%
	if mySTC31.set_binary_gas(mySTC31.kBinaryGasCO2Air_25):
```


## Example 02 - PHT Compensation

The second example shows how set values for temperature, humidity and pressure to improve the accuracy of the CO<sub>2</sub> data. The example initializes the STC31 to measure in air at concentrations up to 25% volume and then sets the temperature, humidity and barometric pressure to fixed reference values.

**Code to Note**

As mentioned above, this example sets static compensation values for temperature, pressure and humidity. You may want to adjust these values for your testing environment:

``` py
	# These are example compensation variables and you can change them as needed to fit your environment
	pressure = 840
	humidity = 25
	temperature = 25
```

## Example 05 - Self Calibration

Example 5 demonstrates how to enable the STC31's automatic self calibration feature as well as how to perform a forced recalibration. Automatic calibration helps improve the STC31's accuracy when used in applications where the target gas is not present most of the time. Refer to the [STC31 Field Calibration Guide](./assets/component_documentation/Sensirion_TC_AN_STCxx_FieldCalibration_D1.pdf) for more information on calibrating the STC31.

After initializing the sensor, the code attempts to perform a forced recalibration of the STC31 with a CO<sub>2</sub> value of 0. After performing the forced recalibration, the code enables the STC31's automatic calibration feature and then prints out CO<sub>2</sub> and temperature data every second.