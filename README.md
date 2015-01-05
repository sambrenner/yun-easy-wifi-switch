Yun Easy Wifi Switch
====================

A more user-friendly method for WiFi network toggling on Arduino Yun (or any OpenWrt device with removable storage). For when you want to give a Yun-based project to your non-tech-folk friends!

It works by reading a wifi network's SSID, password and encryption method from a text file that is stored on a USB drive or MicroSD card. This file is accessed every time the Yun boots up and the WiFi settings are applied accordingly. If you need to change WiFi networks, you can take the USB drive or MicroSD card out of the Yun, plug it into a computer, edit the file, and place it back in the Yun.

I have tested it switching between WiFi networks and switching from AP mode (where the Arduino broadcasts its own network) to a WiFi network.

Installing
-------

1. Move `easy-wifi-switch` into your Yun's `/usr/bin/` directory.
2. Move `wifi.cfg` on to the root of a USB drive or MicroSD card and plug that into the Yun. I recommend USB due to its ubiquity.
3. In your Yun's `/etc/rc.local` file, add a call to `easy-wifi-switch` before the call to `wifi-live-or-reset`. If you haven't made changes to the stock `rc.local` file, you can use the one provided here.

Using
------

1. Remove the USB drive or MicroSD card from the Yun and plug it into a computer.
2. Open `wifi.cfg` in any text editor and update the SSID, password and encryption variables to the desired values.
3. Remove the USB drive from your computer and place it back into the Yun.
4. Reboot the Yun. When it boots up, it will apply the new settings.

Background
------

This was created for my [Trophy of the Future](https://github.com/sambrenner/future-trophy), an internet-connected fantasy football trophy built with an Arduino Yun. Because the trophy will change hands every year, I needed a simple way for its recipients to configure it to their WiFi networks without having to connect to the Yun's network or depend on an ethernet connection.

More Reading
------

* [OpenWrt Wireless Configuration Docs](http://wiki.openwrt.org/doc/uci/wireless)
* [OpenWrt DHCP Configuration Docs](http://wiki.openwrt.org/doc/uci/dhcp)
* [OpenWrt UCI Docs](http://wiki.openwrt.org/doc/uci)
* [`wifi-live-or-reset`](https://github.com/arduino/linino/blob/master/trunk/package/linino/yun-scripts/files/usr/bin/wifi-live-or-reset)
* [Trophy of the Future Documentation Part 1](http://samjbrenner.com/notes/making-the-worlds-first-internet-enabled-fantasy-football-trophy-part-1-fabrication/), [Part 2](http://samjbrenner.com/notes/making-the-worlds-first-internet-enabled-fantasy-football-trophy-part-2-programming/)