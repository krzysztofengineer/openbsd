# DWM installation

## Get the copy

Clone the repository:

```
mkdir app
cd app
git clone git://git.suckless.org/dwm
git clone git://git.suckless.org/st
git clone git://git.suckless.org/dmenu
```

## Compile dwm

Go into `dwm` directory:

```
cd dwm
```

Edit `config.mk` and uncomment `OpenBSD` specific code:

```
# FREETYPEINC = /usr/include/freetype2
FREETYPEINC = ${X11INC}/freetype2
```

Compile dwm:

```
doas make clean install
```

Repeat for `st` and `dmenu`.

## Configure to run on start

Edit `.xsession` configuration file:

```
vim ~/.xsession
```

Inside `.xsession` type:

```
exec dwm
```

Restart X or reboot.