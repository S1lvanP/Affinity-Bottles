# Affinity-Bottles
This is a guide for installing Affinity programs on linux using Bottles.

## Disclaimer
I don't know anything about the technical details that make this work. This is just a combination of [this tutorial](https://affinity.liz.pet/v2/2-wineprefix-setup/), [this post](https://forum.affinity.serif.com/index.php?/topic/166159-affinity-photo-running-on-linux-with-bottles/) and some trial and error.

## Installation
 - get the Affinity .exe (the older versions can be found here:
 https://store.serif.com/de/update/windows/photo/2/
 https://store.serif.com/de/update/windows/designer/2/
 https://store.serif.com/de/update/windows/publisher/2/)
 - install Bottles (this guide assumes the flatpak version is installed)
 - download the Recipe.yml file (from this project or the forum link mentioned above)
 - go to Settings>Runners and install caffe-9.7 (or the latest version)
 - create a new Bottle:
	 - type: custom
	 - runner: caffe-9.7
	 - import config: choose the .yml file 
 - add application, e.g. affinity-photo-msi-2.6.5.exe
 - run the installer (ignore the errors)
 - go to the main menu and back into bottle so the installed program shows up
 - run
   - `cd $HOME/.var/app/com.usebottles.bottles/data/bottles/bottles/BOTTLENAME/drive_c/` (replacing BOTTLENAME)
   - for Affinity Photo V2: `curl --output Program\ Files/Affinity/Photo\ 2/wintypes.dll --location https://github.com/ElementalWarrior/wine-wintypes.dll-for-affinity/raw/refs/heads/master/wintypes_shim.dll.so` 
   - for the Canva-all-in-1: `curl --output Program\ Files/Affinity/Affinity/wintypes.dll --location https://github.com/ElementalWarrior/wine-wintypes.dll-for-affinity/raw/refs/heads/master/wintypes_shim.dll.so`
   - `mkdir windows/system32/WinMetadata/`
   - `curl --output windows/system32/WinMetadata/Windows.winmd --location https://github.com/microsoft/windows-rs/raw/master/crates/libs/bindgen/default/Windows.winmd`
- in your bottle>Settings>runner change to `soda-9.0-1` (or latest)
- start the installed Photo programm
- when installing multiple Affinity programs/versions, just make sure to use caffe for the installation and switch to soda to run them
