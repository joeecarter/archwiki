# Installation Medium
I had some problems getting the live cd to boot so heres a few things I found.

## Getting into the boot menu on the x1 carbon
To get into the boot menu you must first enter the BIOS, save and exit and then spam press F12.

The BIOS was a little annoying to get into reliably because of windows fast boot functionality. To get around this I used this trick: 
- Right click start menu button
- Settings
- Update & security
- Recovery
- Advanced startup
-  Troubleshooting > Advanced Options > UEFI Firmware Settings
- On restart I also spam clicked F1 for good measure.
(Thanks for making it _really_ easy Microsoft)

## Making the boot medium
There are many methods on here: https://wiki.archlinux.org/title/USB_flash_installation_medium

Initially I tried a few windows tools but none worked (see below section) so in the end I plugged the USB stick into my linux server and used this approach:
```
# cat path/to/archlinux-version-x86_64.iso > /dev/sda
```
(obviously check you're slfashing the right drive)

## Secure Boot
After a few failed attempts to boot into the USB it turned out I had secure boot on.

This was an option in one of the BIOS settings menu that needed to be disabled.

After that the USB is bootable with no issues.