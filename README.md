# DellXPSUbuntuSetup
So you fried your laptop again...

I found this handy: https://medium.com/@asad.manji/my-journey-installing-ubuntu-20-04-on-the-dell-xps-15-9500-2020-8ac8560373d1

**NOTE: IF AT ANY TIME YOU GET THE BLACK SCREEN WITH A BLINKING CURSOR, PRESS CTRL+ALT+F# KEYS UNTIL THE LOGIN SCREEN APPEARS**
https://askubuntu.com/questions/1251005/ubuntu-20-04-boots-to-black-screen-with-flashing-cursor

## Install Ubuntu 20.04
Insert your bootable Ubuntu USB Stick, restart and hit F12 when you see the Dell logo to access the boot menu.  
Once you’re into Ubuntu, click on the “Install Ubuntu” icon and follow the installer wizard.  
Do not select to install any 3rd party applications.  

## Update and Upgrade
```console
sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt update --fix-missing
sudo apt install -f
sudo apt-get --with-new-pkgs upgrade
sudo apt-get install aptitude
```

## Install Google Chrome
```console
cd ~/Downloads/
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
google-chrome &
```

## Nvidia Drivers
The Nvidia drivers weren’t installed by default.

```console
sudo ubuntu-drivers autoinstall
```
<!--
Add "nomodeset" next to "quiet splash" in /etc/default/grub

```console
sudo update-grub
```
-->

After rebooting you can confirm that your drivers are active by running the nvidia-smi command from a terminal window which will either print driver information or an error similar to “NVIDIA-SMI has failed because it couldn’t communicate with the NVIDIA driver” if the driver is not active.

## Display Link
<!-- 
https://github.com/AdnanHodzic/displaylink-debian

```console
sudo apt-get install git
cd ~/Downloads
git clone https://github.com/AdnanHodzic/displaylink-debian.git
cd displaylink-debian/ && sudo ./displaylink-debian.sh
```
-->

Download the DisplayLink drivers here:
https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu

unpack and chmod +x

then:

```console
sudo ./displaylink-driver-5.3.0.xx.run
```
