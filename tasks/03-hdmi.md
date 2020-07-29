# Mirror the display via HDMI

## List current settings

```
xrandr -q
```

Find the primary display (mine is `eDP-1`) and the desired HDMI output (e.g. `HDMI-2`)

## Mirror the display

```
xrandr --output HDMI-2 --auto --same-as eDP-1 --mode 1920x1080
```


