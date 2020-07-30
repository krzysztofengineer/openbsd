# Status bar

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

## Battery percentage

```
apm -l
```

## Formatted date

```
date '+%Y-%m-%d %H:%M'
```

## Change status bar text

To change the status bar text:

```
xsetroot -name Test
```

## Putting it alltoghether

We can put a little script inside `~/.xsession` to periodically display those values on status bar:

```
while true
do
    mute=`sndioctl -n output.mute`
    volume=`sndioctl -n output.level`
    if [ $mute == 1 ] ; then vol=0; else vol="$volume"; fi
    date=`date '+%Y-%m-%d %H:%M'`
    battery=`/usr/sbin/apm -l`
    xsetroot -name "vol: ${vol} / bat: ${battery} / ${date}`";
    sleep 1
done &
```


[Next: Screenshots](/dwm/05-screenshots.md)
