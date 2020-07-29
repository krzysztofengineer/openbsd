# DWM installation

## Get the copy

Clone the repository:

```
mkdir app
cd app
git clone git://git.suckless.org/dwm
```

## Compile dwm

```
cd dwm
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