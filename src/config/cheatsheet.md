# Cheatsheet

If you modify a mode's layout or create a new mode, you might want to generate a new cheatsheet that illustrates the layout.

<img src="assets/cheatsheet_short.png" width="500"/>

The cheatsheet is made up of a grid of many keyboard images. Typically, all the chords consisting of just a single switch should be shown together on one keyboard. Groups of multi-switch chords can be shown together on other keyboard images, as long as the chords don't overlap with each other too much. Each chord should have at least one switch that's not shared with any other chord in the group - otherwise, there's nowhere to put the label for that chord.

You're responsible for deciding how to group the chords in the cheatsheet.


## Writing the config file 

First, create a `.yaml` file that describes which chords to show on which keyboard images. See `settings/cheatsheet/cheatsheet.yaml` for an example.

Each entry in the `keyboards:` list describes one of the keyboard images. If the entry looks like this,

    - chord_names:
      - "key_a"
      - "key_c"
      - "key_d"
      # ...and so on...

then each of those chords will be shown in that keyboard image.

If the entry looks like this instead:

    - null
    
then there will be a blank space in the grid where that keyboard would have gone.
    

## Generating the cheatsheet

After writing the config file (called `my_new_cheatsheet.yaml` in this example), pass the file name to the config tool like this:

    $ cargo run -- -c settings/cheatsheet/my_new_cheatsheet.yaml
    
This will generate a vector graphics file called `my_new_cheatsheet.svg` that can be opened in programs like Inkscape or Illustrator. If a file called `my_new_cheatsheet.svg` already exists, you'll be prompted to confirm before overwriting it.

As usual, you can instead specify a non-default settings file at the end of the command:

    $ cargo run -- -c settings/cheatsheet/my_new_cheatsheet.yaml settings/settings_evan.yaml


If you see an error about `Missing ___ from 'cheatsheet symbol lookup'`, that means you need to specify what symbol/text will be used to label that chord on the cheatsheet. You can do that by opening `src/cheatsheet/cheatsheet.rs` and editing the `get_symbol()` function at the end of the file.
