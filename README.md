mGBA
====

## Why the fork?

The [version that is shipped with the ODROID emulationstation image](https://github.com/OtherCrashOverride/mgba-libretro-go2/commits/master) feels really old and the saves of the current version are not compatible with it. 
Since I'm a <abbr title="a.k.a. playing for fun">dirty cheater</abbr> and I want to use my savegames across all my platforms, I need a current version of mgba that runs on the GO ADVANCE.

## About mgba

mGBA is an emulator for running Game Boy Advance games. It aims to be faster and more accurate than many existing Game Boy Advance emulators, as well as adding features that other emulators lack. It also supports Game Boy and Game Boy Color games.

The projects original website can be found at [mgba.io](https://mgba.io/).

## Building

*Building is currently only tested on the GO ADVANCE itself.*

1. Install the dependencies
    - *These are actually based on the dependencies for [building emulationstation](https://github.com/OtherCrashOverride/emulationstation-go2#building), mgba happens to build with those installed and I'm not sure which of these are not needed 🙈.*
    - `sudo apt-get install git libsdl2-dev libfreeimage-dev libfreetype6-dev libcurl4-openssl-dev rapidjson-dev libasound2-dev libgl1-mesa-dev build-essential cmake fonts-droid-fallback premake4`
2. Clone this repo
    - `git clone https://github.com/lfuelling/mgba-go-advance ~/mgba`
3. Build mgba
    - `mkdir build`
    - `cd build`
    - `cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr ..`
    - `make`
4. Install the `libmgba.so` library (and mgba)
    - `sudo make install`
5. Build mgba for the GO ADVANCE
    - `cd ../odroid/`
    - `premake4 gmake`
    - `make`
6. Overwrite the executable
    - `sudo mv mgba /usr/bin/mgba`
7. Test run
    - `/usr/bin/mgba`
    - *The output should end with the line `missing filename.` instead of an error.*

