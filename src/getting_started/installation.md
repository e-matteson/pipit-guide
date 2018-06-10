# Installation

After the keyboard has been programmed, it acts like a normal USB keyboard and should work with any type of computer. However, you will need to install rust to change the keyboard configuration, and install the Arduino IDE to program the keyboard with the new configuration.

## Configuration tool and typing tutor

The configuration tool and typing tutor have been tested only on Linux, but should also work on Mac OSX. It might work on Windows, especially if using the Linux subsystem, but there are no instructions available. 

Install rust, following instructions from the [rust website](https://www.rust-lang.org).

Clone or download the [pipit-keyboard repository](https://github.com/e-matteson/pipit-keyboard) from github. This repository contains the configuration tool, the typing tutor, and the keyboard firmware.

## Arduino IDE

The Arduino IDE allows you to re-program the microcontroller inside the keyboard, updating the firmware configuration.

Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software).

* If using the `Teensy LC`: install the [Teensyduino](https://www.pjrc.com/teensy/teensyduino.html) add-on to the Arduino IDE

* If using the `Adafruit Feather BLE M0`: install SAMD support through the arduino boards manager, according to [adafruit's instructions](https://learn.adafruit.com/adafruit-feather-m0-bluefruit-le/using-with-arduino-ide).


