# Typing Tutor

The typing tutor teaches you the layout of the keyboard. It gives you a line of text to copy and guides you with a hint showing how to type the next letter.

<img src="assets/quickbrownfox.png" width="500" />

As you learn each letter, the tutor will stop showing you hints for that letter. If you mis-type a letter, the hint for the correct letter will reappear in blue, and the location of the incorrect letter you *actually* pressed will appear in red.

The tutor also lets you practice chording whole words. It can present random words from the dictionary and give you a hint showing which switches make up each word's chord.

<img src="assets/random_words.jpeg" width="500" />

## Running the tutor

From the `pipit-keyboard` directory, enter:

    $ cargo run -- -t

This will start the tutor using the default `settings/settings.yaml` file. To use a different file instead, specify it at the end:

    $ cargo run -- -t settings/settings_evan.yaml

The tutor will open to a menu. 
You can use arrow keys to navigate between items in a menu or buttons in a dialog box, and `enter` to select one. 
You *might* be able to click on menu items and buttons as well, but this feature is not supported by all terminal emulators.

You can quit the tutor at any time by typing `ctrl-c`, or by selecting `Quit` in the main menu.

## Options

These options are available in the `Options` menu. All changes will be remembered next time you start the tutor.

### Mode

By default, the tutor will assume your keyboard is in `default_mode` and use that layout to decide where to place the hints. If you want to practice a different [mode](config/modes.html), you can press `enter` to show a list of all the modes found in the settings file, and then select the mode you want to use.

### Hint difficulty

This controls how quickly the tutor will stop showing you hints for letters you've learned. Use the left and right arrows to move the slider. Left is easier and right is more difficult. If the slider is all the way to the right, the tutor will only show you a hint once, the first time the letter appears. 

### Show persistent hints for the lesson's new letters

If selected, always show hints for the letters that are being newly introduced in this lesson, regardless of the hint difficulty setting.

### Allow mistakes

By default, the tutor won't let you continue after typing a wrong letter. The wrong letter won't appear on the screen, and the cursor won't move until you try again and type the correct letter. This is helpful when you're first learning the layout, but it can become frustrating when you're typing quickly or practicing chording whole words. Turning on the `Allow Mistakes` option means that incorrect letters will appear (in red) and you can continue typing past them. After a mistake, the tutor will use a yellow hint to show you where `backspace` is, in case you want to correct your mistake.

<!-- ## Troubleshooting -->
<!--    cargo run -- -t 2>tutorlog.txt; cat tutorlog.txt -->

-----------------------------------------

# Note: 

The tutor has no way of knowing which physical switches you're actually pressing on the keyboard. It only knows which letters the computer received. If you mash an unused combination of many switches that doesn't actually type anything, the tutor won't display any red hints. If you accidentally chord a whole word, it will only display a red hint for the last letter in that word.

Similarly, the tutor can't know the true layout of your keyboard, it can only assume the layout matches the settings file you gave it. If you update the settings file without re-loading the new keyboard firmware, or you switch the keyboard's mode without switching to the same mode in the tutor's options menu, then the hints will be incorrect.

----------------------------------------------------------------
