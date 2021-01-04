# Snippet

<!-- Like words, snippets let you send a sequence of keys by pressing a chord. -->
Snippets are similar to words, except they aren't preceded by a space and they can't be modified by `word_modifiers` or `anagram_modifiers` (or any other type of modifier). Here's the definition for a snippet that will type a smiley face when you press `(` and `:` at the same time:

```
  - {snippet: "(:"}
```

It's better to define this as a snippet than as a word because it wouldn't make sense to capitalize a smiley face.
If we had defined it as a word, pressing `mod_capital` at the same time would produce `9:`, which is never what we want.

By default, the snippet's chord will be generated by combining the existing `plain_key` chords mapped to every character in the snippet's sequence. However, it's usually more useful to specify a different, simpler chord. This snippet will type your email address when you press `space`, `m`, and `e` at the same time:

```
  - {snippet: "me@example.com", chord: " me"}
```

<!-- If you don't want the snippet's chord to depend on the chords assigned to `space`, `m`, and `e`, consider using a [macro](#macro) instead of a snippet. -->

## Special symbols

These special symbols can appear in a snippet definition to represent keys that can't be displayed normally:

| symbol | key               | unicode |
|--------|-------------------|---------|
| `\n`   | `key_enter`       |         |
| `\t`   | `key_tab`         |         |
| `\"`   | `key_doublequote` |         |
| `\\`   | `key_backslash`   |         |
| `←`    | `key_left`        | U+2190  |
| `↑`    | `key_up`          | U+2191  |
| `→`    | `key_right`       | U+2192  |
| `↓`    | `key_down`        | U+2193  |
| `◀`    | `key_home`        | U+25C0  |
| `▶`    | `key_end`         | U+25B6  |


For example, these snippets type a pair of parentheses of quotation marks, and then position the cursor inside:

```
  - {snippet: "()←", chord: "()"}
  - {snippet: "\"\"←", chord: " \""}
```

This snippet types out a C if-statement, and positions the cursor inside the parentheses:
```
  - {snippet: "if () {\n}↑▶←←", chord: " if"} 
```