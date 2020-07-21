# BIOS setup

![](01-bios.png)

## Entering the BIOS setup

Press `F1` during the Lenovo splash screen. 
You can also keep pressing `Enter` until hearing the beep and then `F1` from a selection menu.

## Security settings

Before altering settings I've performed factory reset by selecting `Load Setup Defaults` from `Restart` tab.
Then, I've made sure that Thunderbolt is disabled both inside `Config` tab as well as `Security`/`I/O Port Access`.
I also disable `Wireless WAN`, because that has caused problems with OpenBSD for me in the past.

The options above should be fine tuned from factory reset (at least were for me), however you have to disable `Secure boot` by yourself.
You will find this option on `Security` tab.

## Startup settings

You can install OpenBSD both in UEFI or legacy mode (I will leave UEFI option checked).
That choice will have impact later when choosing partition table type (GPT for UEFI/MBR for Legacy).

## Saving changes

That should be enough for BIOS setup. You can `Exit Saving Changes` and proceed for installation.

However, you can face various issues while using OpenBSD so be aware, that tinkering with BIOS settings can sometimes be the solution to the problem.
