# Command

Commands are used for calling functions in the firmware, like to delete the last word, or switch to a different mode. The chord is defined in a `.kmap` file, the command name is defined in `settings.yaml`, and the behavior is defined in the `doCommand()` function at the top of `pipit-firmware/Pipit.cpp`. 

Command chords cannot be modified by any kind of modifier.
