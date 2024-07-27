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
- [Karabiner-Elements](https://karabiner-elements.pqrs.org/) The killer software for modifying both keyboard and mouse event. I used to use `unnaturalscrollwheels` to reverse mouse scrolling, but on macOS Sonoma 14.2.1, it sometimes refused to launch. Since I also use Karbiner for keyboard event remap, I just found the karabiner supports modify mouse event as well. Just open `Karabiner-Elements` > `Devices` > [Your mouse] > `Modify events` > `Flip mouse vertical wheel`. (Note Karabiner reverse mouse will cause some weird mouse behavior).
- For K380 remap:
    - Remap F7: this is lock screen application launch (consumer/keycode: `al_terminal_lock_or_screensaver`). No option for it. To remap this key you can either: 1. selecting the `Media controls` > `Touch ID on Magic Keyboard` or 2. make a SimpleModification. More detail can be found [here](https://github.com/pqrs-org/Karabiner-Elements/issues/3408)


- Apple Sillicon Virtualization (UTM)
To run ARM Linux/Windows 'natively' on Apple Silicon, use [UTM](https://mac.getutm.app/)

# Display HiDPI & DDC for external monitors
- [Lunar](https://lunar.fyi/) for scale resolution, on MacBookPro 16" XDR (2177x1407 hidpi). This increases 26% screen content. It is open source.
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
