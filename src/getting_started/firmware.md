# Configuring and loading firmware

## Running the configuration tool

From the `pipit-keyboard` directory in a terminal, compile and run the configuration tool by entering:

```
$ cargo run
```

This will look for a settings file in the default location, `settings/settings.yaml`. You can specify a different file instead:


```
$ cargo run -- settings/settings_evan.yaml
```

The configuration tool will read the settings file, generate C++ code expressing the desired configuration, and save that code in the `pipit-firmware` directory. The tool will warn you about possible issues with your choices, like if two mappings conflict with each other, or if the settings contain unused chords or sequences. You can choose to ignore these warnings and load the new firmware anyway, as long as you see that it successfully `Saved keyboard configuration to...`. For more information, see the chapter on [configuration](config/README.html).


## Loading the keyboard firmware

After changing settings and running the config tool, you can load the new firmware onto the keyboard.

1. Connect the keyboard to the computer with a USB cable, if it wasn't already plugged in.

2. Launch the Arduino IDE. 

3. Open the file `pipit-firmware/pipit-firmware.ino`. 

4. In the menu bar, select `Tools -> Board: -> "Teensy LC"`. 

5. Select `Tools -> USB Type: -> "Serial + Keyboard + Mouse + Joystick"`.

6. Select `Tools -> CPU Speed: -> "24 MHz"`.

7. Go to `Tools -> Port` and select which port the keyboard is connected to. The port name will vary, but might look something like `/dev/cu.usbmodem*` on a Mac, or `/dev/ttyACM*` in linux. You can check by unplugging the keyboard and seeing which entry in the port list disappears.

8. Compile and upload the firmware by clicking the round arrow button, or by selecting `Sketch -> Upload` in the menu bar. Look for messages printed in the bottom part of the window. If the upload was successful, you can now use the reconfigured keyboard. If it was not, see the troubleshooting steps below.


### Troubleshooting compilation errors:

- `Wrong board_name`: Check that you selected the right board in the IDE in step 4, and that it matches the `board_name` option in your settings file.

- `'Keyboard' was not declared in this scope`: Check that you selected the right `USB Type` in step 5.

- `Error compiling for board Teensy LC`, following `...ld: region 'FLASH' overflowed by ___ bytes`: The configuration is too large to fit on the microcontroller. Try removing unused words, macros, or modes to make space. Disabling unused features like `enable_audio_typing_feedback` can help save space as well.

Other issues can be reported and discussed using the github [issue tracker](https://github.com/e-matteson/pipit-keyboard/issues).
