# Preparing the installation USB stick

## Downloading the image

The image can be downloaded from [OpenBSD website](https://www.openbsd.org/) *Downloads section). 
For USB stick, download the `installXX.fs` file (not the ISO, which is intended for CD/DVD).
Choose **amd64** for T480.

```sh
wget https://cdn.openbsd.org/pub/OpenBSD/6.7/amd64/install67.fs
```

## Writing the image into the USB

```sh
dd if=/path/to/install67.fs of=/dev/sdX bs=1M status=progress
```

`if` - path to your the downloaded image 

`of` - the usb device (list available devices using `lsblk` utility).

`bs` - block size of 1MB 

`status=progress` - get the live progress status.

[Next: BIOS Setup](/installation/02-bios-setup.md)

### WARNING

`dd` can be destructive if used incorrectly, that's why it's often called "Disk Destroyer". 
Make sure to double check your paths.
