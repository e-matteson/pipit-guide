# Terminology


| term               | definition                                                                                                                                                                                   |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| key                | A single character that can be sent to the computer (including alphabet letters, arrow keys, `backspace`, `ctrl`, etc).                                                                      |
| switch             | A physical switch you can press on the keyboard.                                                                                                                                             |
| chord              | A combination of one or more switches pressed simultaneously.                                                                                                                                |
| sequence           | A sequence of one or more keys that will be sent to the computer when a particular chord is pressed.                                                                                         |
| `plain_modifier`   | A chord that's mapped to one of the following 4 keys: `shift`, `ctrl`, `alt`, `GUI/super/win`                                                                                                |
| `word_modifier`    | A chord that's used to modify a word: `mod_capital`, `mod_nospace`, etc.                                                                                                                     |
| anagrams           | Two words that would be assigned the same chord by default, causing ambiguity. This can happen because they contain the same set of letters (`"the"`/`"teeth"`), or because their letters have overlapping chords: if pressing `m` + `p` produces `z`, then `"map"` and `"zap"` are anagrams. |
| `anagram_modifier` | A chord that's used to select one particular anagram of a word: `mod_anagram1`, `mod_anagram2`, etc.                                                                                         |
| `.kmap` file       | A file that lets you describe which switches are in each chord.                                                                                                                              |
| mode               | A collection of `.kmap` files used for looking up which sequence to send when a chord is pressed. You can switch between modes while typing (for example, to switch to a one-handed layout). |
