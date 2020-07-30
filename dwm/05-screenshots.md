# Screenshots

## Scrot

Install scrot utility:

```
doas pkg_add scrot
```

## Screenshot

To save a screenshot to your current working directory, just type:

```
scrot
```

## Save at folder

You can also pass the directory as a parameter and use formatting for dynamic names:

```
scrot ~/screenshots/%Y-%m-%d-%T-screenshot.png
```

## Bind Print Screen key

Edit `config.def.h` from your dwm directory and append the following line to `keys` array:

```
{ 0, XK_Print, spawn, SHCMD("sleep 0.2; scrot ~/screenshots/%Y-%m-%d-%T-screenshot.png") },
```

Notice the `sleep` command before taking the screenshot with `scrot`. There is a bug that requires that fix, but there is also a patch to fix it (but needs more work).


[Next: Shutdown](/tasks/01-shutdown.md)
