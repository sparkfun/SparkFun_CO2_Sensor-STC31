In this Quick Start guide we'll connect the SparkFun CO2 Sensor - STC31 to a SparkFun IoT RedBoard - ESP32 and use the SparkFun STC31 and SHTC3 Arduino libraries to report environmentally compensated CO<sub>2</sub> percentages. This example takes the live pressure, humidity and temperature data reported by the SHTC3 environmental sensor on the breakout and feeds them to the STC31 to provide accurate CO<sub>2</sub> measurements that are compensated with live environmental data.

If you're not familiar with using sensor breakouts, development boards or the development environments covered in this guide, refer to the [Hardware](./hardware_overview.md) & [Arduino](./arduino_setup.md) sections of this Hookup Guide for a detailed overview of the board along with instructions on setting up and using the SparkFun STC31 and SHTC3 Arduino Libraries.

## Basic Assembly

Since this is a Qwiic breakout, assembling the circuit only requires connecting the sensor breakout to a Qwiic-compatible development board like the IoT RedBoard - ESP32. Connect the STC31 Breakout to the IoT RedBoard with a Qwiic cable and then connect the RedBoard to your computer with a USB-C cable like the photo below:

<figure markdown>
[![Photo of completed Qwiic assembly with the STC31 breakout and IoT RedBoard - ESP32](./assets/img/){ width="600"}](./assets/img/ "Click to enlarge")
</figure>

## Arduino Example - PHT Compensation

This [Arduino](https://docs.arduino.cc/software/ide/) example prints out CO<sub>2</sub> concentration percentages compensated with real-time pressure, humidity and temperature data measured by the SHTC3.

* Open the [Arduino IDE](https://docs.arduino.cc/software/ide-v2/tutorials/getting-started-ide-v2/).
* Install the SparkFun STC31 and STHC3 Arduino libraries with the [Arduino Library Manager](https://docs.arduino.cc/software/ide-v1/tutorials/installing-libraries/). Open the tool and search for "SparkFun STC31" and "SparkFun SHTC3". Make sure to install the latest releases.
* If necessary, install board definitions for the IoT RedBoard - ESP32. Open the [Board Manager](https://docs.arduino.cc/software/ide-v2/tutorials/ide-v2-board-manager/) and search for "ESP32" to install the latest release of espressif's ESP32 boards package.
* Open the example in Arduino by navigating to **File** > **Libraries** > **SparkFun STC31 Arduino Library** > **Example2_PHTCompensation**.
* Select your Board and Port and click "Upload".
* Once the code finishes compiling and uploading, open the [serial monitor](https://learn.sparkfun.com/tutorials/terminal-basics/arduino-serial-monitor-windows-mac-linux) with the baud set to **115200** and you should see values for CO<sub>2</sub> concentration percentage like the screenshot below:

<figure markdown>
[![Screenshot of serial monitor output for example 1](./assets/img/){ width="600"}](./assets/img/ "Click to enlarge")
</figure>