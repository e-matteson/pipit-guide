# Installation

You don't need to install anything to simply use the keyboard - it acts like a normal USB keyboard, and doesn't require any special drivers. Just plug it in and start typing.

If you want to run the typing tutor on your computer or change the keyboard configuration (like to re-arrange keys or add words to the dictionary), then follow these instructions.


## Configuration tool and typing tutor

The configuration tool and typing tutor have been tested on Linux and Mac OSX. They might also work on Windows, especially if using the Linux subsystem.

1. Install rust, following instructions from the [rust website](https://www.rust-lang.org). Rust 1.27 or later is required.

2. Clone or download the [pipit-keyboard repository](https://github.com/e-matteson/pipit-keyboard) from github. This repository contains the configuration tool, the typing tutor, and the keyboard firmware.

3. In a terminal, navigate to the `pipit-keyboard` directory. Run `$ cargo build` to download and compile the required rust libraries and the config tool / tutor itself.


## Arduino IDE

The Arduino IDE allows you to re-program the microcontroller inside the keyboard, updating the firmware configuration.

1. Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software). You must install the offline IDE version, instead of using the online "Arduino Create" tool.

2. Install the [Teensyduino](https://www.pjrc.com/teensy/teensyduino.html) add-on to the Arduino IDE, to support the `TeensyLC` board used in the keyboard.

<!-- * If your keyboard contains a `Teensy LC` microcontroller (USB keyboard support only): -->

<!-- * If your keyboard contains an `Adafruit Feather BLE M0` microcontroller (bluetooth keyboard support): install SAMD support through the arduino boards manager, according to [adafruit's instructions](https://learn.adafruit.com/adafruit-feather-m0-bluefruit-le/using-with-arduino-ide). -->


