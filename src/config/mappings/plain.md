# plain_key and plain_modifier

The `plain_key` group includes most of the keys you'd typically find on a keyboard: letters, numbers, arrow keys, `backspace`, and so on. Their names all start with `key_` (like `key_a`).

Modifiers like `ctrl` and `shift`, however, are in a separate group - they're called `plain_modifiers`, and their names start with `mod_` (like `mod_shift`).

`plain_keys` can be modified by any `plain_modifier`. This means that if you press the chords for `key_a` and `mod_shift` at the same time, the keyboard will recognize them both and send capital `A`.

You should never need to change the sequences for `plain_key` mappings. They're already defined in `settings.yaml`, in terms of the all-caps key names used internally by the keyboard firmware (like `KEY_A`). 

You can edit the chords in a `.kmap` file if you want to re-arrange a mode's layout, or create a new mode. Note that if the mode uses words, changing `plain_key` chords will also affect the chords for `word` mappings. See the [word](#word) section for more details.


<!-- TODO don't overlap key and mod chord definitions -->

