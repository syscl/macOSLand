# macOSLand
A utility and trips about improving usability of macOS

# No sound after waking from sleep
This happens on my Apple Sillicon MacBookPro, the headphone no sound after waking from sleep.
The reason remains unknown, but a reboot or the following will work for me
```sh
sudo killall coreaudiod
```

# tree commandline to display file structure
```sh
brew install tree
```

# Keyboard and mouse event modify
- [Karabiner-Elements](https://karabiner-elements.pqrs.org/) The killer software for modifying both keyboard and mouse event. I used to use `unnaturalscrollwheels` to reverse mouse scrolling, but on macOS Sonoma 14.2.1, it sometimes refused to launch. Since I also use Karbiner for keyboard event remap, I just found the karabiner supports modify mouse event as well. Just open `Karabiner-Elements` > `Devices` > [Your mouse] > `Modify events` > `Flip mouse vertical wheel`. (Note Karabiner reverse mouse will cause some weird mouse behavior).
- For K380 remap:
    - Remap F7: this is lock screen application launch (consumer/keycode: `al_terminal_lock_or_screensaver`). No option for it. To remap this key you can either: 1. selecting the `Media controls` > `Touch ID on Magic Keyboard` or 2. make a SimpleModification. More detail can be found [here](https://github.com/pqrs-org/Karabiner-Elements/issues/3408)


- Apple Sillicon Virtualization (UTM)
To run ARM Linux/Windows 'natively' on Apple Silicon, use [UTM](https://mac.getutm.app/), manjaro failed to start for some reason

# Display HiDPI & DDC for external monitors
- [Lunar](https://lunar.fyi/) for scale resolution, on MacBookPro 16" XDR (2177x1407 hidpi), I used 2557x1653 this days too. This increases 26% screen content. It is open source.
~- [BetterDisplay](https://github.com/waydabber/BetterDisplay), pro version is recommended
- This is particularly useful for 34" 3440x1440 display.~
- Also enable keybaord brightness control so that keyboard shortcut can control all monitors' brightness

# MTP support
For connecting to devices using [MTP protocol](https://en.wikipedia.org/wiki/Media_Transfer_Protocol) (e.g. Android, and new Kindle Scribe), you need to use either [Android File Transfer](https://www.android.com/filetransfer/) or [OpenMTP](https://github.com/ganeshrvel/openmtp).


# Docker without Docker Desktop app
Docker and docker desktop are always garbage. Desktop crashes every day/few days and stuck. An alternative solution maybe using (Rancher or Podman). Due to time constraint, let's just use colima:
Install colima first: `brew install colima`
Once Colima installs, install Docker and Docker Compose.
```
brew install docker docker-compose
```
Then configure docker-compose as a Docker plugin so you can use docker compose as a command instead of the legacy docker-compose script. First, create a folder in your home directory to hold Docker CLI plugins:
```
mkdir -p ~/.docker/cli-plugins
```
Then symlink the docker-compose command into that new folder:
```
ln -sfn $(brew --prefix)/opt/docker-compose/bin/docker-compose ~/.docker/cli-plugins/docker-compose
```
You’ll also need Buildx to build some Docker containers. This is installed with Docker Engine on macOS, but you can install this with Homebrew:
```
brew install docker-Buildx
```
Once downloaded, symlink it to the cli-plugins folder:
```
ln -sfn $(brew --prefix)/opt/docker-buildx/bin/docker-buildx ~/.docker/cli-plugins/docker-buildx
```
More detail can be found [here](https://smallsharpsoftwaretools.com/tutorials/use-colima-to-run-docker-containers-on-macos/)


# Safari AdBlock Plugin
I tried with many popular plugins, however most of them does not work on some websites, `DLPanda` is one example that keeps pop up or just throw warning of using adblockers.
 But `AdBlock Pro for Safari` works on iPhone.

# Enable more powerful mouse support
- Natural middle button (M4, M5, M6-Evoluent) support, this is ususally useful for macOS native app like Safari back/forward. It is called [sensible-side-buttons
](https://github.com/archagon/sensible-side-buttons), the project got updated (support for Apple Sillicon) in this [fork](https://github.com/thealpa/SaneSideButtons).
Note: this may affects the vscode back and forward.
Note: Karabinet modify mouse event will cause some weird behavior.~~To fix this we can use Karabinet Elements>Complex Modifications>import `Change mouse buttons (rev2)`. You may notice that the middle button M6 is not wokring, just go to simple modification and remap `Mouse button6` to `Mouse button5`.~~
This is a comprehensive article to read. [link](https://appflix.cc/mapping-the-mouse-backward-button-in-karabiner-for-mac/)
- Buttersmooth scrolling and disable natural scroll on mouse via [mos](https://github.com/Caldis/Mos)

- Chromium for less tracking?
