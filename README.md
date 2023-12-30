# macOSLand
A utility and trips about improving usability of macOS

# No sound after waking from sleep
This happens on my M2 MacBookPro 16", the headphone no sound after waking from sleep.
The reason remains unknown, but a reboot or the following will work for me
```sh
sudo killall coreaudiod
```

# tree commandline to display file structure
```sh
brew install tree
```

# Keyboard and mouse event modify
- [Karabiner-Elements](https://karabiner-elements.pqrs.org/) The killer software for modifying both keyboard and mouse event. I used to use `unnaturalscrollwheels` to reverse mouse scrolling, but on macOS Sonoma 14.2.1, it sometimes refused to launch. Since I also use Karbiner for keyboard event remap, I just found the karabiner supports modify mouse event as well. Just open `Karabiner-Elements` > `Devices` > [Your mouse] > `Modify events` > `Flip mouse vertical wheel`. And works flawsless.

# Display DDC for external monitors
- [BetterDisplay](https://github.com/waydabber/BetterDisplay)
