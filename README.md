# DellXPSUbuntuSetup
So you fried your laptop again...

I found this handy: https://medium.com/@asad.manji/my-journey-installing-ubuntu-20-04-on-the-dell-xps-15-9500-2020-8ac8560373d1

**NOTE: IF AT ANY TIME YOU GET THE BLACK SCREEN WITH A BLINKING CURSOR, PRESS CTRL+ALT+F# KEYS UNTIL THE LOGIN SCREEN APPEARS**

## Install Ubuntu 20.04
Insert your bootable Ubuntu USB Stick, restart and hit F12 when you see the Dell logo to access the boot menu.  
Once you’re into Ubuntu, click on the “Install Ubuntu” icon and follow the installer wizard.  
Do not select to install any 3rd party applications.  

## Update and Upgrade
```console
sudo apt-get update -y
sudo apt-get upgrade -y
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
Add "nomodeset" next to "quiet splash" in /etc/default/grub

```console
sudo update-grub
```


After rebooting you can confirm that your drivers are active by running the nvidia-smi command from a terminal window which will either print driver information or an error similar to “NVIDIA-SMI has failed because it couldn’t communicate with the NVIDIA driver” if the driver is not active.


