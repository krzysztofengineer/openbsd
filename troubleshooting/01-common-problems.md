# Common problems

## After successful login it log outs immediately

There is probably some runtime issue with X/dwm.

To find the cause, go into another tty with `Ctrl + Alt + 1` (+ `Fn` for T480) and login there.

Then, check `.xsession-errors` file for any errors.

