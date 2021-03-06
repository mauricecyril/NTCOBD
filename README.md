#OBD on pocket chip
Some scattered notes on working with On Board Diagnostics and PocketCHIP.

The interesting files in this repo:
  * blue.py - processes commands in python and logs them to a text file
  * obd_commands_complete.txt - a list of commands that I discovered on the Prius. You can make your own by messing with blue.py
  * cairo_dial.py - uses cairo graphics to draw the rudiments of a speedometer.
  * cairo_animation.py - example of animating cairo graphics, including speedometer.
  * carsync.sh - beginnings of syncing with a WebDAV folder, ideally music files for a 'playlist for the day's commute'

Besides that, there's some examples and unfinished work.

```
sudo apt-get install -y screen openssh-server x11vnc bluez-tools rfkill
sudo apt-get install -y samba cifs-utils smbclient
sudo apt-get install -y python-setuptools python-dev build-essential 
sudo easy_install pip 
sudo pip install --upgrade virtualenv 
pip install obd
pip install subprocess
```
Bluetooth Control in Python [in a gist](https://gist.github.com/egorf/66d88056a9d703928f93)


Connect to ODB II Bluetooth device:
```
	bluetoothctl
```
at bluetoothctl prompt, use:
```
	agent on
	power on
	scan on
	pair <MAC>
	if pin, then 1234
	trust <MAC>
	ctl-D
```
in bash:
```
	sudo rfcomm connect hci0 <MAC>
```
now
```
	screen /dev/rfcomm0
```
and follow this guide for basic serial commands
```
	http://gersic.com/connecting-your-raspberry-pi-to-a-bluetooth-obd-ii-adapter/
```
We can now proceed to installing [pyserial](https://github.com/pyserial/pyserial) and [pyodb](https://github.com/peterh/pyobd) to actually do something with this data

We can use https://github.com/brendan-w/python-OBD to provide an interface to the ODB commands.

This has some ui widgets that might be interesting: https://github.com/brendan-w/piHud

Documentation on python and ODB: http://python-obd.readthedocs.io/en/latest/Connections/

