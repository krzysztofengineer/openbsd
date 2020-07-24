# Wi-fi

It's finally time to disconnect the ethernet cable an connect using in-built wi-fi module.
I should actually do this a lot earlier, but I've kinda forgot.

## Network interfaces

To list available interfaces, you can use `ifconfig` utility you're probably familiar with from Linux.
If you've never used Linux and jump straight into BSD- I respect. 

```
ifconfig
```

There should be `em0` interface with `status: active` for our ethernet connection and `iwm0` wi-fi interface I've mentioned during the installation.

Because OpenBSD does not ship with proprietary firmware, we have to install it first.
Lucky for us, we don't have to search & download any of that. 
There is a simple command that will check for missing firmware and automatically download the necessary files.
And it works great for T480.

```
doas fw_update
```

## Connecting wi-fi

To create a persistent connection to our wi-fi network, we need to create a corresponding hostname file.
Because our interface is identified as `iwm0`, let's create `hostname.imw0` file inside `/etc` directory (to write into that directory we need root permissions):

```
doas vim /etc/hostname.iwm0
```

Inside, we will configure the connection. If you'd look inside `/etc/hostname.em0`, which was created by the installer, there is only one line inside:

```
dhcp
```

But for wifi we also need credentials. If your network is called **My_Wifi** and you connect using **Password1234** password, type the following contents into the file:

```
nwid My_Wifi wpakey Password1234
dhcp
```

This will connect to your wifi using those credentials and get the IP automatically from the router.
After saving the file, you have to reboot or restart the networking service:

```
doas sh /etc/netstart
```

You should now be connected to your wi-fi hotspot and also after logging in.

[Next: Sound](/05-sound.md)
