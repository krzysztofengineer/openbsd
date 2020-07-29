# Installation

## Booting from the USB

Press `F12` during the splash screen, select your USB from the list and hit enter. 
You can also keep hitting `Enter` during the Lenovo splash screen and press `F12` while on the selection menu.

## Starting the installer

The installer will then do some work (many lines of white text on the blue background will appear). 
If there are any issues with your hardware, there will probably be some useful information along the lines.

```
Welcome to the OpenBSD/amd64 6.7 installation program.
(I)nstall, (U)pgrade, (A)utoinstall or (S)hell?
```
You will be prompted with a welcome text and some options. 
Type `I` for install and press `Enter` (it can be lowercase).

## Keyboard layout

```
Choose your keyboard layout ('?' or 'L' for list)[default]?
```

First, you will be prompted for a keyboard layout. If you're not sure which one to select, type the question mark `?` and confirm with `Enter`.
Find a suitable layout from available ones and type its name. 
You can also confirm without typing anything for a default choice if you're not sure which one to choose.

## Hostname

```
System hostname? (short form, e.g. 'foo')
```

During the boot process, `netstart` utility will use this value to name your machine for networking. 
You can change this value later (with root privileges) by editing `/etc/myname` file. 
I personally name my machines by their manufacturer/type, in this case `thinkpad`, so I can easily identify them.

## Network interface configuration

```
Available network interfaces are: iwm0 em0 vlan0
Which network do you wish to configure?
```

Next, you will be promted for network configuration with available interfaces listed. For Thinkpad T480 that should be `iwm0`, which is wi-fi, `em0` for ethernet and `vlan0`.
Because OpenBSD installation media does not contain firmware for T480 wi-fi adapter, the best option is to configure ethernet for now (but you can download the firmware file onto the USB and load it now using `fw_update` utility).

```
IPv4 address for em0? (or 'dhcp' or 'none') [dhcp]
```

I will connect an ethernet cable and type `em0`. When asked for `IPv4` address I will select default option `dhcp` so the IP address will automatically be assigned by the router (just confirm with `Enter` and for `IPv6` I will also select default option or type `none`).

You can now configure another network interface, but if you're done just hit `Enter`.

```
DNS domain name? (e.g. 'example.com') [my.domain]
```

Next, you'll be asked for `DNS domain name`, which will be used with a hostname you've provided earlier for FQDN (fully qualified domain name). 
Because we will be using Thinkpad as a personal workstation, we can leave it on default `my.domain`.

## Root password

```
Password for root account? (will not echo)
Password for root account? (again)
```

You will be asked to provide a root password. 
It will not be your daily password as we will create a user account later on, but you will need it when root privileges are required. 
Type your password twice to confirm it's correct.

## SSHD

```
Start sshd(8) by default? [yes]
```

`sshd` listens to ssh clients connections. If you do not intend to accept incoming connections feel free to answer `no`. Otherwise, accept the default answer with `Enter`.

## X Window System

```
Do you want the X Window System to be started by xenodm(1)? [no]
```

The X Window System is the widely unix-supported graphics service. Because I will be installing `dwm` windows manager later, which happens to be built on top of `X`, I will type `yes` as an aswer. We will only need to call our window manager from a config file and `xenodm` will start it automatically on login.

## User account

```
Setup a user? (enter a lower-case loginname, or 'no') [no]
```

It is a best practice not to use `root` account for everything, so I would recommend to create a separate user account here.
I will be using my name, but feel free to use yours ( ͡° ͜ʖ ͡°)

```
Full name for user krzysztof? [krzysztof]
Password for user krzysztof (will not echo)
Password for user krzysztof (again)
```

To finish creating account, provide a full name (or just hit `Enter`) and password alogn with the confirmation.

```
WARNING: root is targeted by password guessing attacks, pubkeys are safer. Allow root ssh login? (yes, no, prohibit-password) [no]
```

If you do not need to access the machine remotely as root, hit `Enter`. 
Even if you do, it is a best practice to create a separate account without all the root privileges.

## Timezone

```
What timezone are you in? ('?' for list) [Europe/Warsaw]
```

You can list available timezone using question mark, but if you're connected to the Internet I think it should guess the proper one. 
(Or maybe it uses some other magic? ╰( ͡° ͜ʖ ͡° )つ──☆*:・ﾟ)


## Disk partitioning

```
Available disks are: sd0, sd1, sd2.
Which disk is the root disk? ('?' for details) [sd0]
```

Now it's finally time to install the OS. First, we need to select a disk to write it to. 
The best choice is to type `?` and double check if the default choice is correct. 
If you're on T480, look for something like `sd0: NVMe` and check if the disk size matches. 
Next, you will be prompted with a choice I've mentioned during the BIOS setup:

```
Use (W)hole disk MBR, whole disk (G)PT or (E)dit?
```

Because I'm using UEFI, I will select `G` for `GPT` partitioning scheme.

OpenBSD will then do its magic and generate a proposal list for new partitions (it uses many partitions as opposed to other distributions).

```
Use (A)uto layout, (E)dit auto layout, or create (C)ustom layout? [a]
```

If you believe in magic, select `A`.

```
Which disk do you wish to initialize? (or 'done') [done]
```

You now have a chance to initialize other disks. Otherwise, hit `Enter`.

## OpenBSD installation

Now that we have a disk ready for OpenBSD, we will select the source of installation packages (grouped in so called `sets`).

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

Next, you will be able to select (or deselect) which sets you want to install. 
I tend to leave all of them selected, but if you are a real minimalist, feel free to only leave what's required.
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
For beginners, it is recommended to leave the selection untouched.
The installer will then fetch and verify all sets that's been selected.

After it's done, if you're not intending to install more packages from a different source, hit `Enter` for `done`:

```
Location of sets? (disk http nfs or 'done') [done]
```

The system will now do some more magic (including creating a kernel). 
And that should be it. The last prompt will ask you what to do next.

```
Exit to (S)hell, (H)alt or (R)eboot? [reboot]
```

Go to shell if you're a PRO user and want to tinker a bit more, 
halt if you want to go to bed already to continue tomorrow 
or reboot to start setting up your machine right away.

[Next: Post install configuration](/configuration/01-post-install.md)

