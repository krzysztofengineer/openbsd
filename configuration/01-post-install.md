# Post-install configuration

You can log in using the account credentials you've chosen during the installation.

OpenBSD will start a basic X environment with a terminal window of `xterm` opened.

Yyou can also click on the desktop and select `XTerm` to open a new one.

## Root privileges

Right now, we cannot do much using our user account. 
If you'd try to install a package (using `pkg_add` utility) or even reboot the machine, the error message like that would appear:

```
thinkpad$ pkg_add vim
pkg_add: pkg_add must be run as root
```

OpenBSD ships with `doas` utility (`sudo` alternative). 
However, on a fresh install, prepending command with `doas` would also fail:

```
thinkpad$ doas pkg_add vim
doas: doas is not enabled, /etc/doas.conf: No such file or directory
```

We need to create a config file for `doas` as a root.
If you don't want to log out/reboot to do so, you can type `su` into the terminal:

```
su
```

and provide the root password (the first one you've typed during the installation).

Now you should be able to edit the configuration file for `doas` (`vi` editor is already preinstalled);

```
vi /etc/doas.conf
```

Put the following line in that file:

```
permit :wheel
```

This will allow user from the `wheel` group to run commands as root (your account should be in that group already).
Now, you should be able to use `doas` to call root commands, e.g.:

```
doas pkg_add vim
```

Type your current user password (not root). 

*If you don't want to be asked for a password every time you run `doas` command, you can add `persist` keyword:*

```
permit persist :wheel
```

## Installing basic packages

Search packages:

```
pkg_info -Q firefox
```

Install the package:

```
doas pkg_add firefox
```

[Next: Wi-fi](/configuration/02-wifi.md)
