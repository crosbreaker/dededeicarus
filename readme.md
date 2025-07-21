# This is used to do [Icarus](https://github.com/HarryJarry1/Icarus-Lite) on keyrolled dedede chromebooks.
It is recommened to use [this 124 recovery image](https://dl.google.com/dl/edgedl/chromeos/recovery/chromeos_15823.40.0_dedede_recovery_stable-channel_mp-v48.bin.zip) (it doesn't matter that it is 124, even if your on kernver 4)
# Usage instructions:
```
git clone https://github.com/HarryJarry1/dededeicarus
cd dededeicarus
```
```
sudo ./build_badrecovery.sh -i <image.bin> -t unverified
```
**MAKE SURE YOU USE ``unverified`` IF YOU DON'T, IT WILL DESTORY YOUR LOCAL CHROMEOS.**
# On Chromebook instructions:
1. Complete [oobescape](https://github.com/HarryJarry1/dededeicarus/blob/main/oobescape.md) or [sh1ttyOOBE](https://github.com/crosbreaker/sh1ttyOOBE)
# Steps:
1. Build and put a [dededeicarus](https://github.com/HarryJarry1/dededeicarus) image on a USB drive or a SD card
2. Press power + esc + refresh
3. Press control + d, then enter
4. Press power + esc + refresh once you reach the developer mode is blocked screen
5. Insert the [dededeicarus](https://github.com/HarryJarry1/dededeicarus) image
6. Use [Icarus](https://github.com/HarryJarry1/Icarus-Lite) to unenroll

## WebBuilder?
Yes!  [here](https://harryjarry1.github.io/dededeicarus/builder.html)
## Why does this work?
I discovered that vpd and crossystem are set to not block devmode when oobescape is done, so you can recover to unverified images.  This is because fwmp is never checked for when recovering.
thanks to olyb for help wiping stateful and for badrecovery
## What changes have been made to badrecovery for this to work?
I added the [PKImetadata](https://github.com/HarryJarry1/dededeicarus/tree/main/unverified/PKIMetadata) folder, and updated [payload.sh](https://github.com/HarryJarry1/dededeicarus/blob/main/unverified/payload.sh) to wipe stateful, mount stateful, copy PKImetadata to stateful/unencrypted, then disable devmode.
