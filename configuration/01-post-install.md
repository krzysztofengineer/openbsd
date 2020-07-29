# Post-install configuration

If the installation went smooth, we should be able to reboot and see the login screen.
You can log in using the account credentials you've chosen during the installation.

By default, OpenBSD will start some basic X environment, but we will change it soon.
There should be a terminal window of `xterm` open after you successfully log in, 
but you can also click on the desktop and select `XTerm` to open a new one.

## Root privileges

Right now, we cannot do much using our user account. 
If you'd try to install a package or even reboot the machine, the error message like that would appear:

```
thinkpad$ pkg_add vim
pkg_add: pkg_add must be run as root
```

(`pkg_add` is a way to install packages from OpenBSD "ports" repository)

To temporarily act as root, OpenBSD ships with `doas` utility (`sudo` alternative). 
However, on a fresh install, prepending command with `doas` would also fail:

```
thinkpad$ doas pkg_add vim
doas: doas is not enabled, /etc/doas.conf: No such file or directory
```

So how can we deal with this?

Like the error message states, we need a config file for `doas` to work.
It contains a list of permissions but in order to edit it we also need to act as root.

The solution is to switch to the root account and edit that file there. 
If you don't want to log out/reboot to do so, you can type `su` into the terminal:

```
su
```

and provide the root password (the first one you've typed during the installation).

Now you should be able to edit the configuration file for `doas` (`vi` editor is already preinstalled);

```
vi /etc/doas.conf
```

To allow our user account to call root commands, put the following line in that file:

```
permit :wheel
```

This will allow user from the `wheel` group to run commands as root (your account should be in that group already).
Now, you should be able to use `doas` to call root commands. Let's check it by installing `vim`:

```
doas pkg_add vim
```

`doas` will ask you for your password before running the command (your current user password, not the root one). 

*In case of `vim` there are multiple choices available, so we also need to select the version we want by typing the number (I choose `10`).*

If you don't want to be asked for a password every time you run `doas` command, you can add `persist` keyword to the line we've added earlier inside `/etc/doas.conf`:

```
permit persist :wheel
```

It should then persist the login information for five minutes.

> If you're stuck during this step, feel free to email me at [krzysztof@engineer.com](mailto:krzysztof@engineer.com) and I will do my best to help.

## Installing basic packages

We've already installed the `vim` package earlier, so here's the quick refresher.

To search if a package is available, you can use `pkg_info` command with `Q` option:

```
pkg_info -Q firefox
```

We can then install the package:

```
doas pkg_add firefox
```

If you want to follow along with my minimalist environment, now it's time to install `git` package yourself.

[Next: Wi-fi](/configuration/02-wifi.md)