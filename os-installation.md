# OS Installation
Master page: https://wiki.archlinux.org/title/installation_guide

## Using WiFi
This guide is very useful: https://wiki.archlinux.org/title/Iwd#iwctl

## Formatting the disk
I ended up using fdisk going for gpt. The disk was mapped as nvme0n1 in /dev.

This page was also useful: https://wiki.archlinux.org/title/EFI_system_partition

## Setting up GRUB
The arch guide doesn't go into any specific bootloader so I follow the latter half o f this video - https://www.youtube.com/watch?v=rUEnS1zj1DM

Just read the comments as its slightly different to what the arch guide says. The efi partition was actually supposed to be at /boot/efi and the /boot folder should live in the rootfs partition.

To sort this out I have to move /boot/* to a temp folder, unmount /boot, mkdir /boot and /boot/efi, mount the efi partition as /boot/efi and then move the old /boot/* files back into the new /boot folder (which is on the rootfs partition now).

Then also redo the fstab file as it'll be wrong otherwise.

## Internet on boot
Annoyingly the basic guide above doesn't give you an arch install with internet ready.

In the chroot I added iwctl via pacman:
```
pacman -S iwd iw networkmanager
```

On reboot add these systemctls:
```
systemctl enable NetworkManager
systemctl enable iw

```
(you'll need to start them too first time)

Useful pages on network stuff:
https://wiki.archlinux.org/title/Network_configuration
https://wiki.archlinux.org/title/Iwd#iwctl

## Microcode
TODO

## Users
TODO

