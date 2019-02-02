# Modes

Modes let you switch between multiple layouts on-the-fly, without re-loading your keyboard firmware.

Here are examples of extra modes you might want to create, in addition to the `default_mode`:

* A mode that puts photoshop hotkeys under your left hand, to use while you operate the mouse with your right hand. 
* A one-handed typing layout that lets you access the whole alphabet with either hand.
* Gaming modes that have layouts optimized for particular games, and act like a conventional keyboard instead of a chording keyboard when you press multiple switches at once. 
* Windows mode: If your `default_mode` has macros that send Mac shortcuts, you can create another mode that overrides just those macros to send the Windows shortcuts instead, or vice versa.


## Configuring modes

The `settings.yaml` file has a `modes:` list, where each entry is the name of a mode followed by information about it:

    modes:
      default_mode:
        keymaps:
          - {file: "settings/keymaps/dvorak24.kmap", use_words: true}
    
      windows_mode:
        keymaps:
          - {file: "settings/keymaps/windows_shortcuts.kmap"}
          - {file: "settings/keymaps/dvorak24.kmap", use_words: true}
    
      gaming_mode:
        keymaps:
          - {file: "settings/keymaps/gaming_test.kmap"}
        gaming: true
      
      
      
### Keymaps

When describing a mode, the first piece of information you need to give is which keymap file(s) it uses. All modes draw from the same set of sequences defined in the settings file. The difference between modes is in which chord (if any) they assign to each of those sequences. 

If you list multiple keymaps for a mode, like in the `windows_mode` example, keymaps higher up in the list will override the ones below. 

      windows_mode:
        keymaps:
          - {file: "settings/keymaps/windows_shortcuts.kmap"}
          - {file: "settings/keymaps/dvorak24.kmap", use_words: true}

Let's say that `dvorak24.kmap` assigns a certain chord to `macro_save_as` (which sends `⌘-shift-s`), and `windows_shortcuts.kmap` assigns the *same chord* to `macro_windows_save_as` (which sends `ctrl-shift-s`). Now, pressing that chord while in `windows_mode` will trigger `macro_windows_save_as`, while all other chords act just the same as they would in `default_mode`. This makes it simple to toggle between Mac and Windows-style shortcuts by switching modes.

For each `.kmap` file you list, you can say whether you want to use this keymap to generate word chords. If you add `use_words: true`, then the chords for the alphabet letters in this keymap will be combined together to create a chord for every word in the dictionary. If you add `use_words: false` or just leave it blank, no word chords will be generated. 

You'll probably only have one `.kmap` file that's suitable for generating word chords - in this case, it's `dvorak24.kmap`. It needs to have a chord for each letter in the alphabet, and the anagram numbers in the dictionary need to be carefully chosen to avoid conflicts caused by those particular letter chords. So it wouldn't make sense to try using the same dictionary with two different keymaps.

### Gaming

After listing a mode's keymap files, you can specify whether it's a special gaming mode by adding `gaming: true`.

      gaming_mode:
        keymaps:
          - {file: "settings/keymaps/gaming_test.kmap"}
        gaming: true
        
This changes how the keyboard handles multiple presses. Chording keyboards don't normally work well for gaming. If you're using `wasd` keys for movement, you'd want to be able to move diagonally by pressing `w` and `d` together. A chording keyboard, however, would treat that combination as an entirely new chord, and unless you had manually defined that chord already, it would just send nothing. Setting `gaming: true` fixes this: pressing `w` and `d` will send both `w` and `d` at the same time, like a conventional keyboard. 

This of course means that all the chords used in a gaming mode can only contain a single switch. Multiple-switch chords won't be detected.
        
<!-- Kmap files specify which chord you press to type each plain_key, macro, or command.  -->
<!-- If `use_words` is true, use this kmap to generate chords for all the words in the dictionary. -->

<!-- Each mode can use multiple keymap files. If the same chord appears in more than 1 keymap, the last keymap takes priority. This is useful if you want to override just a few chords, like to change apple shortcuts to windows shortcuts when you switch between computers. -->

## Switching modes

The keyboard will always start in the mode named `default_mode` after powering on. You switch to a mode using a [command](config/mappings/command), like `command_switch_to_windows_mode` or `command_switch_to_default_mode`. These commands are special: unlike others, they're not written in the `commands:` list in `settings.yaml`. Instead, they're automatically created for each mode, by prepending `command_switch_to_` to the mode name. The chords for these commands are defined in `.kmap` files, as usual.


