The [SparkFun STC3x Python Package](https://github.com/sparkfun/qwiic_stc3x_py) is based off the Arduino libraries for the STX3x family of CO<sub>2</sub> sensors from Sensirion<sup>&trade;</sup>. It works for Python, MicroPython and CircuitPython so you can choose which "flavor" of Python to use. This section goes over how to install the package in each supported Python environment along with the necessary tools for installation and running examples.

## Python Installation

For users on a Linux-based system (Raspberry Pi, etc.), install this package in Python with PyPi using the `pip3` command with the following steps:

* Set up a virtual environment from a specific directory using `venv`: `python3 -m venv path/to/venv (You can use any path here just remember to use the same one for each step).
* Install the Qwiic package: `path/to/venv/bin/pip3 install sparkfun-qwiic-stcx

That's it. Now you can run any example (or your own custom scripts) by running it with a command like: `path/to/venv/bin`

## MicroPython Installation

If you prefer to use MicroPython to run the examples on a microcontroller running MicroPython, follow these steps to install the package on your computer:

* Install [mpremote](https://docs.micropython.org/en/latest/reference/mpremote.html) on your computer.
* Connect the IoT RedBoard - ESP32 (or other MicroPython device) to your computer and install the package directly using mpremote mip: `mpremote mip install github:sparkfun/qwiic_stcx_py`
* Install the examples to the IoT RedBoard with the following mip command: `mpremote mip install github:sparkfun/qwiic_stcx_py@examples`

## CircuitPython Installation

Lastly, users who prefer CircuitPython can install the package with the following steps:

* Install [CircUp](https://docs.circuitpython.org/projects/circup/en/latest/#installation) on your computer.
* Make sure you have the latest version of the SparkFun Qwiic CircuitPython module installed with this command: `circup bundle-add sparkfun/Qwiic_py`
* Connect your CircuitPython device to your computer and install the package to the device with circup: `circup install --py qwiic_stcx`

If you want to install specific examples from the repository, use the corresponding circup command from below:

```
circup example qwiic_stc3x\qwiic_stc3x_ex1_basic
circup example qwiic_stc3x\qwiic_stc3x_ex2_PHT_compensation
circup example qwiic_stc3x\qwiic_stc3x_ex4_self_test
circup example qwiic_stc3x\qwiic_stc3x_ex5_auto_calibration
```
Note, the syntax used here are for Windows commands; Linux and Mac have different path separators. Refer to the [CircUp "example command documentation](https://learn.adafruit.com/keep-your-circuitpython-libraries-on-devices-up-to-date-with-circup/example-command) for more information.