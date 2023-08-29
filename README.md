## Recovery Device Tree for the Samsung Galaxy Tab A8 Wifi

## How-to compile it:

# Create dirs
$ mkdir tw; cd tw

# Init repo
$ repo init --depth=1 -u https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1

# Clone gta8wifi repo
$ git clone https://github.com/MrFluffyOven/android_device_samsung_gta8wifi_classic.git

# Clone gta8wifi kernel
$ git clone https://github.com/MrFluffyOven/android_device_samsung_kernel_x200.git
kernel/samsung/gta8wifi

# Sync
$ repo sync --no-repo-verify -c --force-sync --no-clone-bundle --no-tags --optimized-fetch --prune -j`nproc`

# Build
$ source build/envsetup.sh; export ALLOW_MISSING_DEPENDENCIES=true; lunch twrp_gta8wifi-eng; mka recoveryimage

# Disable File Based Encryption (FBE) after installing TWRP.
$ Boot TWRP; format DATA partition; start TWRP SHELL; execute: multidisabler.
Your DATA partition will be secured against re-encryption.


Blobs version:
> Kernel base: Compiled from source.
> Ramdisk, DTB, DTBO base: 

