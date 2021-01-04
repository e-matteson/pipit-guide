# Options

The following options are available in `settings.yaml`.

## Timing options

These timing options control how the firmware recognizes switch presses and releases as chords.

| Option                       | Description                                                                                                                                                                                                                                                                | Required?                                     | Value                         |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|-------------------------------|
| `chord_delay`                | How quickly all the switches in a chord must be pressed for them to be recognized as a single chord. Increase it if you often fail to press whole chords at once. Decrease it if you often type too quickly and accidentally combine separate presses into a single chord. | Required                                      | Milliseconds                  |
| `held_delay`                 | How long a switch must be held down before it will be reused in future chords.                                                                                                                                                                                             | Required                                      | Milliseconds                  |

### Examples of timing options

This timing diagram shows a few examples of switch-pressing scenarios, to illustrate the meanings of the different delay options. Assume that pressing one switch sends `p`, pressing another sends `m`, and pressing them both at once sends `z`.

```
keys    |
sent:   | timer name:     states of switches and timers over time:
________|________________________________________________________________
        |                 |-m----------|
        |                         |-p---|
   z    |
        | chord_delay     <..........>
        | held_delay      <.........................>
________|________________________________________________________________
        |                 |-m------------------|
        |                                 |-p---|
  mp    |
        | chord_delay     <..........>
        | held_delay      <.........................>
________|________________________________________________________________
        |                 |-m----------------------------------|
        |                                                 |-p---|
  mz    |
        | chord_delay     <..........>
        | held_delay      <.........................>
________|________________________________________________________________
```

Note that the `chord_delay` and `held_delay` timers reset after every new switch is pressed. This reset is not shown in the diagrams, because it's not relevant to these examples. It does mean that if you're pressing a large chord with many switches, you don't need to press all of them within `chord_delay` milliseconds - you just can't wait longer than that in between any two presses.


## Hardware options

The correct values of these options are determined by the keyboard's hardware. They should not be changed, unless you are building/modifying your own keyboard harware.

| Option                   | Description                                                                                                                                                                                                                  | Required?                                     | Value                         |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|-------------------------------|
| `board_name`             | The name of the microcontroller board used inside the keyboard.                                                                                                                                                              | Required                                      | `TEENSY_LC`, `FEATHER_M0_BLE` |
| `row_pins`               | The microcontroller pins connected to each row in the switch matrix, split up by hand.                                                                                                                                       | Required                                      |                               |
| `column_pins`            | The microcontroller pins connected to each column in the switch matrix, split up by hand.                                                                                                                                    | Required                                      |                               |
| `kmap_format`            | The format of the chord blocks in the .kmap files. Each pair of numbers represents the row and column pins of one switch. The number of switches on each line must match the number of dots on each line of the kmap blocks. | Required.                                     |                               |
| `rgb_led_pins`           | The microcontroller pins connected to the red, green, and blue channels of a RGB LED, if one is present.                                                                                                                     | Optional, LED disabled by default             | [pin, pin, pin]               |
| `battery_level_pin`      | The microcontroller pin used to sense battery voltage, if a battery is present.                                                                                                                                              | Optional, battery sensing disabled by default | pin                           |
| `use_standby_interrupts` | Use interrupts to detect presses instead of polling the switches. Interrupts are preferred, but require hardware support and may not be available for all boards and pin assignments.                                        | Optional, default `true`                      | `true` or `false`             |


## Other options

| Option                         | Description                                                                                                                                                                                                        | Required?                          | Value                     |
|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------|---------------------------|
| `debug_messages`               | How much debugging info to send over the serial connection. Messages can be viewed in the Arduino serial monitor.                                                                                                  | Optional, default `None`           | `None`, `Some`, `All`     |
| `output_directory`             | Where to save the auto-generated `.cpp`/`.h` files containing the firmware configuration.                                                                                                                          | Optional, default `pipit-firmware` | path                      |
| `word_space_position`          | Whether to automatically add space to the beginning or end of chorded words, or not at all. Recommended value is `Before`.                                                                                         | Optional, default `Before`         | `Before`, `After`, `None` |
| `enable_led_typing_feedback`   | If true, flash the LED when a unrecognized chord is typed.                                                                                                                                                         | Optional, default `false`          | `true`, `false`           |
| `enable_audio_typing_feedback` | If true, send a short serial message whenever a chord is typed. The host computer can listen for this message and produce a sound (see [audio](www.github.com/e-matteson/pipit-keyboard/blob/master/extras/audio)) | Optional, default `false`          | `true`, `false`           |
