# piserver
Setup scripts for home piserver

## Preperation steps
* Download image from https://www.raspberrypi.org/downloads/raspbian/ and extract the zip file to get a .img file.
* Format SD card (overwrite format) using [SD formatter](https://www.sdcard.org/downloads/formatter_4/eula_mac/)
* Flash the image to the sd card using [Etcher](https://etcher.io/)
* Remove and reinsert sd card
* Save following files on boot volume
  * `ssh` empty with no extension

## Initial login
General updates (default login is pi@192.168.1.xxx, password: raspberry)
* `passwd` to change default password
* `sudo raspi-config` to change settings
* `sudo apt-get update`
* `sudo apt-get upgrade -y`
* `sudo reboot`

## Install [unifi](https://www.ubnt.com/download/unifi/) controller 
* Install MongoDB `sudo apt-get install -y mongodb`
* Install Java 8 `sudo apt-get install oracle-java8-jdk`
* Disable the default MongoDB instance to free up resources (UniFi will run its own copy)
  * `sudo service mongodb stop`
	* `sudo service mongodb disable`
* Add Ubiquiti's source list 
   * `echo 'deb http://www.ubnt.com/downloads/unifi/debian stable ubiquiti' | sudo tee /etc/apt/sources.list.d/100-ubnt-unifi.list`
   * `sudo wget -O /etc/apt/trusted.gpg.d/unifi-repo.gpg https://dl.ubnt.com/unifi/unifi-repo.gpg`
   * `sudo apt-get update`
   * `apt-get install -y unifi`
* login to https://192.168.1.xxx:8443
* set a fixed IP address for pi

## Install [pihole](https://pi-hole.net/)
* `curl -sSL https://install.pi-hole.net | bash`
* config as dns server

## General

Clone this repository to get additional scripts
```
sudo apt install git
git clone https://github.com/iain-t-bennett/piserver
```
