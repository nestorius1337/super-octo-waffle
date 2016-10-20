# super-octo-waffle
Retropie emulation with SPI screen
Just a short writeup.

## Parts used
* Pi 1B
* 2.2" LCD 2.2 inch SPI TFT LCD Display ILI9341 240x320 (http://www.ebay.de/itm/172117966610?_trksid=p2057872.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT)

## Software
* Retropie
* tft overlay file (https://github.com/philenotfound/rpi_elecfreaks_22_tft_dt_overlay) __mind the change from *.dtb to *-dtbo__
* fbcp (https://github.com/tasanakorn/rpi-fbcp)

## Guides
* https://learn.adafruit.com/running-opengl-based-games-and-emulators-on-adafruit-pitft-displays/
* http://appdictive.dk/blog/projects/2015/10/30/cheap_tft_display_on_raspberry_pi/
* https://raspberrypi.stackexchange.com/questions/44179/rpi-2-and-3-95-tft-ili9488/44472#44472

## Process
* install retropie (duh...)
* SPI connection
* clone overlay from github -> copy elecfreaks_22_tft.dtb to /boot/overlays/elecfreaks_22_tft.__dtbo__
* clone fbcp from github and compile + install (https://learn.adafruit.com/running-opengl-based-games-and-emulators-on-adafruit-pitft-displays/3-dot-5-pitft)
* install raspi-config and activate SPI in raspi-config (or do it in /boot/config.txt)
* modify /boot/config.txt
```
hdmi_force_hotplug=1
hdmi_group=2
hdmi_mode=87
hdmi_cvt=320 240 60 1 0 0 0

dtoverlay=elecfreaks_22_tft,rotate=270,speed=80000000,fps=60

#dtdebug=on
```
* add `/usr/local/bin/fbcp &` to /etc/rc.local
* reboot
