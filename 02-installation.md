# Installation

## Booting from the USB

Press `F12` during the splash screen, select your USB from the list and press enter. You can also keep pressing `Enter` during the Lenovo splash screen and press `F12` while on the selection menu.

## Starting the installer

The installer will do some work (you will see many lines of white text on the blue background). If there are any issues with your hardware, there will probably be some information along the lines.

```
Welcome to the OpenBSD/amd64 6.7 installation program.
(I)nstall, (U)pgrade, (A)utoinstall or (S)hell?
```
When the installer finishes its job, you will be prompted with a welcome text and some options. Type `I` for install and press `Enter`.

## Keyboard layout

```
Choose your keyboard layout ('?' or 'L' for list)[default]?
```

First, you will be prompted for a keyboard layout. If you know what it is, just type it. If not, type the question mark `?` and confirm with `Enter`.
Now, find a suitable layout from available layouts list and type it in. You can also just confirm without typing anything for a default choice if you're not sure what to choose.

## Hostname

```
System hostname? (short form, e.g. 'foo')
```

During the boot process, `netstart` utility will use this value to name your machine for networking. You can change this value later with root privileges by editing `/etc/myname` file. I tend to name my machines by their type, in this case `thinkpad`.

## Network interface configuration

```
Available network interfaces are: iwwm0 em0 vlan0
Which network do you wish to configure?
```

Next, you will be promted for network configuration with available interfaces listed. For Thinkpad T480 that should be `iwm0`, which is wi-fi, `em0` for ethernet and `vlan0`.
Because OpenBSD installation media does not contain firmware for T480 wi-fi adapter, the best option is to configure ethernet for now (but you can e.g. download the firmware file onto the USB and load it now using `fw_update` utility).

```
IPv4 address for em0? (or 'dhcp' or 'none') [dhcp]
```

I will connect an ethernet cable and type `em0`. When asked for `IPv4` address I will select default option `dhcp` so it will be automatically assigned by the router (just confirm with `Enter` and for `IPv6` I will also select default option or type `'none'`.

You can now configure another network interface, but if you're done just hit `Enter` for `done` option.

```
DNS domain name? (e.g. 'example.com') [my.domain]
```

Next, you should be asked for `DNS domain name`, which will be used with a hostname you've provided earlier for FQDN (fully qualified domain name). Because we will be using Thinkpad as a personal workstation we can leave it on default `my.domain`.

## Root password

```
Password for root account? (will not echo)
Password for root account? (again)
```

Now you will be asked to provide a root password. It will not be your daily password as we will create a user account later on, but you will need it for actions requiring root privileges (but you can also configure the user account with root permissions). Type your password twice to confirm.

## SSHD

```
Start sshd(8) by default? [yes]
```

`sshd` listens to ssh clients connections. If you do not intend to accept incoming connections feel free to answer `no`. Otherwise, accept the default answer with `Enter`.

## X Window System

```
Do you want the X Window System to be started by xenodm(1)? [no]
```

The X Window System is the widely unix-supported graphics service. Because I will be installing `dwm` windows manager later, which happens to be built on top of `X`, I will type `yes` as an aswer. If you intend to install another desktop environment, e.g. `gnome` which can start desktop from its login manager `gdm`, feel free to accept the default answer to not start X by default.

## User account

```
Setup a user? (enter a lower-case loginname, or 'no') [no]
```

It is a best practice not to use `root` account for everything, so I would recommend to create a separate user account here. I will be using my name, but feel free to use yours ( ͡° ͜ʖ ͡°)

```
Full name for user krzysztof? [krzysztof]
Password for user krzysztof (will not echo)
Password for user krzysztof (again)
```

To finish creating account, provide a full name (or just hit `Enter`) and password with a confirmation.

```
WARNING: root is targeted by password guessing attacks, pubkeys are safer. Allow root ssh login? (yes, no, prohibit-password) [no]
```

If you do not need to access the machine remotely as root, hit `Enter`. Even if you do, it is a best practice to create a separate account without all the root privileges.

## Timezone

```
What timezone are you in? ('?' for list) [Europe/Warsaw]
```

You can list available timezone using question mark, but if you're connected to the Internet it should guess the proper one. Or maybe it uses other magic ╰( ͡° ͜ʖ ͡° )つ──☆*:・ﾟ


## Disk partitioning

```
Available disks are: sd0, sd1, sd2.
Which disk is the root disk? ('?' for details) [sd0]
```

Now it's finally time to install the OS. First, we need to select a disk to write it to. The best choice is to type `?` and double check if the default answer is right. If you're on T480, look for something like `sd0: NVMe` and check if the disk size matches. Next, you will be prompted with a choice I've mentioned during the BIOS setup:

```
Use (W)hole disk MBR, whole disk (G)PT or (E)dit?
```

Because I'm using UEFI, I will select `G` for `GPT` partitioning type.

OpenBSD will then do its magic and generate a proposal list for new partitions (it uses many partitions as opposed to other distributions).

```
Use (A)uto layout, (E)dit auto layout, or create (C)ustom layout? [a]
```

If you believe in magic, select `A`.

```
Which disk do you wish yo initialize? (or 'done') [done]
```

You now have a chance to initialize other disks. Otherwise, hit `Enter`.

## OpenBSD installation

Now that we have a disk ready for OpenBSD, we will select the source of installation files (called `sets` here).

```
Let's install the sets!
Location of sets? (disk http nfs or 'done') [http]
```

Because we have an active Internet connection, we can fetch fresh sets from the web, so choose `http`.
You will be then asked a couple of questions about the download mirror (which you should safely accept with `Enter`)

```
HTTP proxy URL?
HTTP Server?
Server directory?
```

Next, you will be able to select (or deselect) which sets you want to install.  


