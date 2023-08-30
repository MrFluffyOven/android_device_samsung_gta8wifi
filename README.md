# Android device tree for samsung SM-X200 (gta8wifi)
 This device tree is still being worked on, things might change.
## Recovery Device Tree for the Samsung Galaxy Tab A8 Wifi

## How-to compile it:

# Create dirs
$ mkdir tw; cd tw

# Pre init
$ mkdir -p ~/.bin

PATH="${HOME}/.bin:${PATH}"

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

chmod a+rx ~/.bin/repo

# Init repo
$ repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

# Sync
$ repo sync

# Clone gta8wifi repo
$ git clone https://github.com/MrFluffyOven/android_device_samsung_gta8wifi.git device/samsung/gta8wifi

# Clone gta8wifi kernel
$ git clone https://github.com/MrFluffyOven/android_device_samsung_kernel_x200.git
kernel/samsung/gta8wifi

# Make yourself owner of the kernel
$ sudo chown -R (your linux username) kernel

# Unzip 7z File
Locate the 7z file in the tw file in tw/kernel/samsung/gta8wifi/tools/lib64, and "Extract Here"

# Build
$ source build/envsetup.sh; export ALLOW_MISSING_DEPENDENCIES=true; lunch twrp_gta8wifi-eng; mka recoveryimage

# Disable File Based Encryption (FBE) after installing TWRP.
$ Boot TWRP; format DATA partition; start TWRP SHELL; execute: multidisabler.
Your DATA partition will be secured against re-encryption.


Blobs version:
> Kernel base: Compiled from source.
> Ramdisk, DTB, DTBO base: X200XXS3CWG2
