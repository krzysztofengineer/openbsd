# Wallpaper

## Install feh

```
doas pkg_add feh
```

## Set the wallpaper

```
feh --bg-scale ~/wallpapers/wallpaper.png
```

To set it automatically, put that line into `~/.xsession` file.

## Login screen

To set the wallpaper for login screen, edit `/etc/X11/xenodm/Xsetup_0` and append the following line:

```
/usr/local/bin/feh --bg-scale /home/krzysztof/wallpapers/wallpaper.png
```

Use absolute paths, because there is no login context on that screen.

While you're here, you can also comment the following line to get rid of the annoying console window:

```
# xconsole -geometry 480x130-0-0 -daemon -notify -verbose -fn fixed -exitOnFail
```

[Next: Status bar](/dwm/04-statusbar.md)