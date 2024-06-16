# set up qlc rPi


## 

uname dane
pwd dane

## General 

```
sudo apt upgrade
sudo apt install git 




to open qlc - qlcplus -platform eglfs 

to close ctrl + alt + backspace 


```




## the 3.5"  monitor: 
it's git install script needs a Cmake chain - not present in the QLC version ... 

### Enable it
edit `/boot/config.txt`
add `dtoverlay=piscreen,speed=16000000,rotate=270` at the bottom 
alt add `dtoverlay=piscreen2r,speed=16000000,rotate=270` at the bottom 


add fbcon=map:10 to the end of the file `/boot/cmdline.txt`

change line 21 of `/etc/init.d/qlcplus`
to `QLCPLUS_OPTS="-platform linuxfb:fb=/dev/fb1 -plugin evdevtouch:invertx --nowm --web --web-auth --operate --overscan"`
QLCPLUS_OPTS="-platform linuxfb:fb=/dev/fb1 -plugin evdevtouch:invertx:inverty --nowm --web --w
invertx inverty rotate=90 rotate=180 rotate=270


I really don't thing that the params get passed to evdevtouch 

// close. have an inverted Y?? Can't seem to fix it . 
https://www.qlcplus.org/forum/viewtopic.php?t=16253 


export QT_QPA_FB_TSLIB=1
export QT_QPA_EVDEV_TOUCHSCREEN_PARAMETERS=invertx
export QT_QPA_EVDEV_TOUCHSCREEN_PARAMETERS=/dev/input/event:rotate=90

tried having these in envvars . Then doing a qlc restart . 
No changes. 
Also tried parking them in sudo nano /etc/init.d/qlcplus
No changes. really need to do it lower I think. 

Giving up 

to get to term on pi - ctrl+alt+bsp 
to go to design mode ctrl+F12


restart qlc+ 
systemctl daemon-reload 
    auth
sudo service qlcplus restart


## local host wifi 

First setup 2 options: 

File /etc/wpa_supplicant/wpa_supplicant.conf
`
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
        ssid="TPW4G_8CG7D6"
        psk=5413f2f384d90c3476195b9686729bff7c84d12b2e097a0076d59f9c960b9575
        priority=5
}

network={
        ssid="Pixel_8056"
        psk=4p9zttkx6impqtr
        priority=4
}


`


## ssh 
Can't use hostname without a DNS server - use IP address - the hotspot lets you look that up ... 

winscp works for an scp. 
VSCode didn't work until I changes the settings: ssh-remote config path to the absolute path of the same config file. god knows why.  

Default wifi hotspot - TPWXXX - 192.168.0.126 

## DMXUSB 
Works out of the box (on Bullseye at least) no issues. 


## Remote shows 
### Pi config 
Configuration - 
Universe   | Input              | Output  | 
Universe 1 | Artnet 127.0.0.1   | DMXUSB  | 

### PC config 
Universe   | Input              | Output  | 
Universe 1 | None   | ArtNet 192.168.0.x  | 
In the settings inside the artnet, it actually goes to 192.168.0.255, setting it to the Pi seems to give a slightly faster reaction time. 







TODO: 
- [ ] Create a project for the Pi. (include the IOs)
- [x] set it to use it's own monitor (again)
- [ ] get touch screen working 
    - still got inverted. 
- [ ] Get a PSU for it 
- [ ] get a case 
- [ ] setup a fallback WiFi 
- [ ] finish stylesheets 
- [ ] Get all manuals 
- [ ] add Circuit diagrams from KiCad 

