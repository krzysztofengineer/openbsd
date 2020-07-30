# Sound

Sound should work out of the box.

You should be able to use dedicated keyboard keys for manipulating volume and toggle mute.


## Get volume & mute status

To get only values, provide `-n` flag.

Volume level: (0 - 1)

```
sndioctl -n output.level
```

Mute (0 or 1):

```
sndioctl -n output.mute
```

[Next: DWM Installation](/dwm/01-dwm-installation.md)
