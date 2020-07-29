# Wi-fi

We can now disconnect the ethernet cable an connect using in-built wi-fi module.

## Network interfaces

To list available network interfaces:

```
ifconfig
```

Install the missing firmware:

```
doas fw_update
```

## Connecting wi-fi

Because our interface is identified as `iwm0`, let's create `hostname.imw0` file inside `/etc` directory:

```
doas vim /etc/hostname.iwm0
```

If your network is called **My_Wifi** and you connect using **Password1234** password, type the following contents into the file:

```
nwid My_Wifi wpakey Password1234
dhcp
```

Reboot or restart the networking service to apply changes:

```
doas sh /etc/netstart
```

You should now be connected to your wi-fi hotspot and also after logging in.

[Next: Sound](/configuration/03-sound.md)
