This is a crazy exploit chain that chains badrecovery, oobescape, and icarus all together to remove fwmp, even on devices that may be keyrolled or never had a shim (dedede, etc)
## Pre-requirements
1. Complete [sh1ttyOOBE](https://github.com/crosbreaker/sh1ttyOOBE) or [oobescape](https://discord.com/channels/419123358698045453/1293414364488925196)
# Steps:
1. Build and flash a [dededeicarus](https://github.com/HarryJarry1/dededeicarus) image on a USB drive or a SD card
2. Press power + esc + refresh
3. Press control + d, then enter
4. Press power + esc + refresh once you reach the developer mode is blocked screen
5. Insert the [dededeicarus](https://github.com/HarryJarry1/dededeicarus) image
6. Use [Icarus](https://github.com/HarryJarry1/Icarus-Lite) to unenroll

## Web builder?
https://harryjarry1.github.io/dededeicarus/builder.html
## Why does this work?
I discovered that vpd and crossystem are set to not block devmode when oobescape is done, so you can recover to unverified images.  This is because fwmp is never checked for when recovering.
thanks to olyb for help wiping stateful and for badrecovery

## Other features?
If you have write protect disabled, you can unkeyroll by running ``bash /usb/usr/sbin/unkeyroll.sh``

## What changes have been made to badrecovery for this to work?
I added the [PKImetadata](https://github.com/HarryJarry1/dededeicarus/tree/main/unverified/PKIMetadata) folder, and updated [payload.sh](https://github.com/HarryJarry1/dededeicarus/blob/main/unverified/payload.sh) to wipe stateful, mount stateful, copy PKImetadata to stateful/unencrypted, then disable devmode.
