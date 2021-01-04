# Command

Commands are used for calling functions in the firmware, like to delete the last word or switch to a different mode. 
The command name is defined in `settings.yaml`, the chord is defined in a `.kmap` file, and the behavior is defined in the `doCommand()` function in `pipit-firmware/Pipit.cpp`.

The commands used for switching modes, however, are special cases. 
Their names are automatically defined and do not appear in `settings.yaml`. See the section on [modes](config/modes.html) for more details.

Command chords cannot be modified by any kind of modifier.
