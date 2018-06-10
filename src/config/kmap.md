# Kmap file format

A `.kmap` file contains blocks of characters that visually represent chords. In each block, the first line gives the name of a mapping (as defined in `settings.yaml`). The following lines show which switches must be pressed to trigger that mapping. The `*` symbols represent pressed switches and the `.` symbols represent un-pressed switches. 


```
key_h
....   ....
....   *...
  .     .
  ... ...
```

Multiple blocks can be put on the same lines, in adjacent columns.

Lines beginning with `#` are comments and will be ignored. You can give a block the name `blank_mapping` if it's not currently being used for a mapping, but you don't want to delete it or comment it out.

```
# This is a comment.

key_0            key_2          key_4
....   ....      ....   ....    ....   ....
....   **..      ....   .**.    ....   ..**
  .     .          .     .        .     .
  ... ...          ... ...        ... ...
```

There must be at least one blank line between blocks. There must not be any blank lines in the middle of a block. If there are multiple columns of blocks on the same lines, there must be at least one whitespace character separating each of the names on the first line. Whitespace (other than newlines) within the lines of dots has no effect - it is allowed anywhere and required nowhere.

<!-- The `.`'s and `*`'s are meant to be laid out in the same arrangement as the physical switches on the keyboard. If you make a keyboard with a different number or arrangement of switches, you can change the `.kmap` file format to match your hardware. You must update the `kmap_format` option in `settings.yaml`, so that the configuration program can parse the kmap blocks correctly and know which row and column pins correspond to which characters in the block. -->

An emacs mode providing syntax highlighting for `.kmap` files is available in [pipit-mode.el](www.github.com/e-matteson/pipit-keyboard/blob/master/extras/pipit-mode.el).
