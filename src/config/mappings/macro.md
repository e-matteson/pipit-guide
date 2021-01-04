# Macro

`macros` are similar to `words`, except that:
- `macro` sequences can contain arbitrary modifiers, like `ctrl`.
- `macro` sequences are not automatically prefixed with `space`.
- `macro` chords are not automatically generated - you pick them yourself, and write them in a `.kmap` file.
- `macro` chords cannot be modified by any kind of modifier. If you press a modifer at the same time, the chord will no longer be recognized as a `macro`.


## Macro definitions
 
A `macro` sequence is defined as a list of keypresses. 
Each keypress is on a separate line and includes a `key` and/or a list of modifiers.

```
  macro_save_as:
    - {key: "KEY_S", mods: ["MODIFIERKEY_CTRL", "MODIFIERKEY_SHIFT"]}

  macro_save_and_quit:
    - {key: "KEY_S", mods: ["MODIFIERKEY_CTRL"]}
    - {key: "KEY_Q", mods: ["MODIFIERKEY_CTRL"]}

  macro_emacs_save:
    - {key: "KEY_X", mods: ["MODIFIERKEY_CTRL"]}
    - {key: "KEY_S", mods: ["MODIFIERKEY_CTRL"]}

  macro_emacs_insert_euro:
    - {key: "KEY_X", mods: ["MODIFIERKEY_CTRL"]}
    - {key: "KEY_8"}
    - {key: "KEY_8", mods: ["MODIFIERKEY_SHIFT"]}
    - {key: "KEY_E", mods: ["MODIFIERKEY_SHIFT"]}
```

The `mods` list can contain the following names:

| mods              |                                                           |
|-------------------|-----------------------------------------------------------|
| MODIFIERKEY_CTRL  |                                                           |
| MODIFIERKEY_SHIFT |                                                           |
| MODIFIERKEY_ALT   |                                                           |
| MODIFIERKEY_GUI   | A.K.A. windows key (❖), apple command key (⌘), or `super` |

The `key` can be any of the following names:

 |                     |                    |                     |                 |
 |---------------------|--------------------|---------------------|-----------------|
 | KEY_A	           | KEY_B              | KEY_C	           | KEY_D           |
 | KEY_E	           | KEY_F	          | KEY_G	           | KEY_H           |
 | KEY_I	           | KEY_J	          | KEY_K	           | KEY_L           |
 | KEY_M	           | KEY_N	          | KEY_O	           | KEY_P           |
 | KEY_Q	           | KEY_R	          | KEY_S	           | KEY_T           |
 | KEY_U	           | KEY_V	          | KEY_W	           | KEY_X           |
 | KEY_Y	           | KEY_Z	          | KEY_1	           | KEY_2           |
 | KEY_3	           | KEY_4	          | KEY_5	           | KEY_6           |
 | KEY_7	           | KEY_8	          | KEY_9	           | KEY_0           |
 | KEY_ENTER	       | KEY_ESC	        | KEY_BACKSPACE	   | KEY_TAB         |
 | KEY_SPACE	       | KEY_MINUS	      | KEY_EQUAL	       | KEY_LEFT_BRACE  |
 | KEY_RIGHT_BRACE	 | KEY_BACKSLASH	  | KEY_NUMBER	      | KEY_SEMICOLON   |
 | KEY_QUOTE	       | KEY_TILDE	      | KEY_COMMA	       | KEY_PERIOD      |
 | KEY_SLASH	       | KEY_CAPS_LOCK	  | KEY_F1	          | KEY_F2          |
 | KEY_F3	          | KEY_F4	         | KEY_F5	          | KEY_F6          |
 | KEY_F7	          | KEY_F8	         | KEY_F9	          | KEY_F10         |
 | KEY_F11	         | KEY_F12	        | KEY_PRINTSCREEN	 | KEY_SCROLL_LOCK |
 | KEY_PAUSE	       | KEY_INSERT	     | KEY_HOME	        | KEY_PAGE_UP     |
 | KEY_DELETE	      | KEY_END	        | KEY_PAGE_DOWN	   | KEY_RIGHT       |
 | KEY_LEFT	        | KEY_DOWN	       | KEY_UP	          | KEY_NUM_LOCK    |
 | KEYPAD_SLASH	    | KEYPAD_ASTERIX	 | KEYPAD_MINUS	    | KEYPAD_PLUS     |
 | KEYPAD_ENTER	    | KEYPAD_1	       | KEYPAD_2	        | KEYPAD_3        |
 | KEYPAD_4	        | KEYPAD_5	       | KEYPAD_6	        | KEYPAD_7        |
 | KEYPAD_8	        | KEYPAD_9	       | KEYPAD_0	        | KEYPAD_PERIOD   |

