# macOSLand
A utility and trips about improving usability of macOS

# No sound after waking from sleep
This happens on my M2 MacBookPro 16", the headphone no sound after waking from sleep.
The reason remains unknown yet, but a reboot or the following will work for me
```sh
sudo killall coreaudiod
```
