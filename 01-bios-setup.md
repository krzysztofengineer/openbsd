# BIOS setup

## Entering the BIOS setup

Press `F1` during the Lenovo splash screen. 
You can also keep hitting `Enter` until hearing the old-school beep and press `F1` later while on selection screen.

## Config & Security settings

Firstly, I've performed a factory reset by selecting `Load Setup Defaults` from `Restart` tab.
Then, I've made sure that Thunderbolt is disabled both inside `Config` tab as well as `Security`/`I/O Port Access` (it sometimes causes issues on OpenBSD).
I also disable `Wireless WAN`, because that caused problems for me in the past.

From the `Security` tab disable `Secure boot`.

## Startup settings

You can install OpenBSD both in UEFI or legacy mode (I will leave UEFI option checked).
That choice will have impact later when choosing partition table type (GPT for UEFI / MBR for Legacy).

## Saving changes

You can now `Exit Saving Changes` and proceed for installation.

Be aware, that when you'll face some issues later on, it can sometimes be helpful to go back to BIOS and tinker with some options (which we may actually do together in later sections of this book).


[Next: Installation](02-installation.md)
