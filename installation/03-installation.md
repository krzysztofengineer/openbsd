# Installation

## Booting from the USB

Press `F12` during the splash screen, select your USB from the list and hit enter. 
You can also keep hitting `Enter` during the Lenovo splash screen and press `F12` while on the selection menu.

## Starting the installer
```
Welcome to the OpenBSD/amd64 6.7 installation program.
(I)nstall, (U)pgrade, (A)utoinstall or (S)hell?
```
Type `I` for install and press `Enter` (it can be lowercase).

## Keyboard layout

```
Choose your keyboard layout ('?' or 'L' for list)[default]?
```

If you're not sure which one to select, type the question mark `?` and confirm with `Enter`.
Find a suitable layout from available ones and type its name. 

## Hostname

```
System hostname? (short form, e.g. 'foo')
```

During the boot process, `netstart` utility will use this value to name your machine for networking. 
You can change this value later (with root privileges) by editing `/etc/myname` file. 

## Network interface configuration

```
Available network interfaces are: iwm0 em0 vlan0
Which network do you wish to configure?
```

For Thinkpad T480 that should be `iwm0`, which is wi-fi or `em0` for ethernet.

Because OpenBSD installation media does not contain firmware for T480 wi-fi adapter, the best option is to configure ethernet for now.

```
IPv4 address for em0? (or 'dhcp' or 'none') [dhcp]
```

Type `dhcp` for automatic IP address.

```
DNS domain name? (e.g. 'example.com') [my.domain]
```

You can leave it on default option (`my.domain`).

## Root password

```
Password for root account? (will not echo)
Password for root account? (again)
```

Type your root password twice.

## SSHD

```
Start sshd(8) by default? [yes]
```

`sshd` listens to ssh clients connections. 

## X Window System

```
Do you want the X Window System to be started by xenodm(1)? [no]
```

Type `yes` if you'll be using X window manager (the default one or e.g. `dwm`).

Other wm's, like `gnome` does not need this as they can start X from login mananger.

## User account

```
Setup a user? (enter a lower-case loginname, or 'no') [no]
```

Enter your daily username.
I will be using my name, but feel free to use yours ( ͡° ͜ʖ ͡°)

```
Full name for user krzysztof? [krzysztof]
Password for user krzysztof (will not echo)
Password for user krzysztof (again)
```

Provide a full name (or just hit `Enter`) and password along with the confirmation.

```
WARNING: root is targeted by password guessing attacks, pubkeys are safer. Allow root ssh login? (yes, no, prohibit-password) [no]
```

If you do not need to access the machine remotely as root, hit `Enter`. 

## Timezone

```
What timezone are you in? ('?' for list) [Europe/Warsaw]
```

You can list available timezone using question mark, but if you're connected to the Internet it should guess the proper one. 


## Disk partitioning

```
Available disks are: sd0, sd1, sd2.
Which disk is the root disk? ('?' for details) [sd0]
```

Select a disk to write it to. 
Type `?` and double check if the default choice is correct. 
If you're on T480, look for something like `sd0: NVMe` and check if the disk size matches. 
Next, you will be prompted with a choice I've mentioned during the BIOS setup:

```
Use (W)hole disk MBR, whole disk (G)PT or (E)dit?
```

Because I'm using UEFI, I will select `G` for `GPT` partitioning scheme.

OpenBSD will then generate a proposal for new partitions:

```
Use (A)uto layout, (E)dit auto layout, or create (C)ustom layout? [a]
```

Select `A` to accept the proposal.

```
Which disk do you wish to initialize? (or 'done') [done]
```

You can initialize other disks. Otherwise, hit `Enter`.

## OpenBSD installation

```
Let's install the sets!
Location of sets? (disk http nfs or 'done') [http]
```

Because we have an active Internet connection, we can fetch fresh sets from the web, so choose `http`.
You will be then asked a couple of questions about the download mirror (which you should safely accept with `Enter`).

```
HTTP proxy URL?
HTTP Server?
Server directory?
```

Select (or deselect) which sets you want to install. 
If you're a beginner, leave all of them selected.
Here's the list from the official website:

```
bsd           The kernel (required)
bsd.mp        The multi-processor kernel (only on some platforms)
bsd.rd        The ramdisk kernel
baseXX.tgz    The base system (required)
compXX.tgz    The compiler collection, headers and libraries
manXX.tgz     Manual pages
gameXX.tgz    Text-based games
xbaseXX.tgz   Base libraries and utilities for X11 (requires xshareXX.tgz)
xfontXX.tgz   Fonts used by X11
xservXX.tgz   X11's X servers
xshareXX.tgz  X11's man pages, locale settings and includes
```

Follow the instructions and when you're done, hit `Enter` (or type `done`). 

After it's done, if you're not intending to install more packages from a different source, hit `Enter` for `done`:

```
Location of sets? (disk http nfs or 'done') [done]
```

And that should be it. The last prompt will ask you what to do next.

```
Exit to (S)hell, (H)alt or (R)eboot? [reboot]
```

[Next: Post install configuration](/configuration/01-post-install.md)

