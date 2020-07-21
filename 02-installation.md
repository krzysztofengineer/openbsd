# Installation

## Booting from the USB

Press `F12` during the splash screen, select your USB from the list and press enter. You can also keep pressing `Enter` during the Lenovo splash screen and press `F12` while on the selection menu.

## Starting the installer

The installer will do some work (you will see many lines of white text on the blue background). If there are any issues with your hardware, there will probably be some information along the lines.

When the installer finishes its job, you will be prompted with a welcome text and some options. Type `I` for install and press `Enter`.

## Choose keyboard layout

First, you will be prompted for a keyboard layout. If you know what it is, just type it. If not, type the question mark `?` and confirm with `Enter`.
Now, find a suitable layout from available layouts list and type it in. You can also just confirm without typing anything for a default choice if you're not sure what to choose.

## System hostname

During the boot process, `netstart` utility will use this value to name your machine for networking. You can change this value later with root privileges by editing `/etc/myname` file. I tend to name my machines by their type, in this case `thinkpad`.

## Network interface configuration

Next, you will be promted for network configuration with available interfaces listed. For Thinkpad T480 that should be `iwm0`, which is wi-fi, `em0` for ethernet and `vlan0`.
Because OpenBSD installation media does not contain firmware for T480 wi-fi adapter, the best option is to configure ethernet for now (but you can e.g. download the firmware file onto the USB and load it now using `fw_update` utility).

I will connect an ethernet cable and type `em0`. When asked for `IPv4` address I will select default option `dhcp` so it will be automatically assigned by the router (just confirm with `Enter` and for `IPv6` I will also select default option or type `'none'`.
