# Power management

## Check power status

```
apm
```

## Set the performance adjustment mode

Start `apm` daemon:

```
doas rcctl -f enable apmd
```

Set automatic mode:

```
doas apm -A
```
