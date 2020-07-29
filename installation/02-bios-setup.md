# BIOS setup

## Entering the BIOS setup

Press `F1` during the Lenovo splash screen. 
You can also keep hitting `Enter` until hearing the beep and press `F1` later while on selection screen.

## Config & Security settings

`Load Setup Defaults` from `Restart` tab.

Then, make sure that Thunderbolt is disabled both inside `Config` tab as well as `Security`/`I/O Port Access`.

Disable `Wireless WAN` if it causes issues (does for my setup).

At the `Security` tab disable `Secure boot`.

## Startup settings

You can install OpenBSD both in UEFI or legacy mode (I choose UEFI).

That choice will have impact later when choosing partition table type (GPT for UEFI / MBR for Legacy).

`Exit Saving Changes` and proceed for installation.

[Next: Installation](/installation/03-installation.md)
