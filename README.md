# Android device tree for samsung SM-X200 (gta8wifi)
 This device tree is still being worked on, things might change.
## Recovery Device Tree for the Samsung Galaxy Tab A8 Wifi

## Getting Started ##
To get started with AOSP sources to build TWRP, you'll need to get familiar
with [Git and Repo](https://source.android.com/source/using-repo.html).


## How-to compile it:

# Create dirs
    $ mkdir tw; cd tw

# Pre init
    $ mkdir -p ~/.bin

    PATH="${HOME}/.bin:${PATH}"

    curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

    chmod a+rx ~/.bin/repo

# Init repo
    $ repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-11

# Sync
    $ repo sync

# Clone gta8wifi repo
    $ git clone https://gitlab.com/MrFluffyOven/android_device_samsung_gta8wifi.git -b twrp-11 device/samsung/gta8wifi

# Build
    $ . build/envsetup.sh; export ALLOW_MISSING_DEPENDENCIES=true; lunch twrp_gta8wifi-eng; mka recoveryimage

# Disable File Based Encryption (FBE) after installing TWRP.
    $ Boot TWRP; format DATA partition; start TWRP SHELL; execute: multidisabler.
Your DATA partition will be secured against re-encryption.
