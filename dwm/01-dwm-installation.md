# DWM installation

## Get the copy

Clone the repository:

```
mkdir app
cd app
git clone git://git.suckless.org/dwm
```

## Compile dwm

Edit `config.mk` and uncomment `OpenBSD` specific code:

```
# FREETYPEINC = /usr/include/freetype2
FREETYPEINC = ${X11INC}/freetype2
```

Compile from `dwm` code directory:

```
doas make clean install
```

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