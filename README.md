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
## Recover Backup

```console
sudo apt-get install deja-dup
```
Go to folder you want restored, right click, and "Restore to Previous Version"

## Thunderbird

```console
sudo aptitude install thunderbird
```
http://weberlab.wikidot.com/thunderbird

## Mattermost

```console
wget https://releases.mattermost.com/desktop/4.7.2/mattermost-desktop-4.7.2-linux-amd64.deb
sudo dpkg -i mattermost-desktop-4.7.2-linux-amd64.deb
sudo apt-get -f install
```

## Dropbox

Download: https://www.dropbox.com/download?dl=packages/ubuntu/dropbox_2020.03.04_amd64.deb

```console
sudo dpkg -i dropbox_2020.03.04_amd64.deb
```

## Zoom

https://zoom.us/download?os=linux

```console
sudo apt install ./zoom_amd64.deb
```

## Todoist

```console
sudo apt update
sudo apt install snapd
sudo snap install todoist
```

## Calendar

```console
sudo apt-get install -y gnome-calendar
```

## Slack
https://slack.com/intl/en-ca/downloads/instructions/ubuntu

```console
sudo dpkg -i slack-desktop-4.20.0-amd64.deb
```
## Spotify

```console
sudo aptitude install curl
curl -sS https://download.spotify.com/debian/pubkey_0D811D58.gpg | sudo apt-key add -
echo "deb http://repository.spotify.com stable non-free" | sudo tee /etc/apt/sources.list.d/spotify.list
sudo apt update
sudo aptitude install spotify-client
```
## LibreOffice

```console
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt update
sudo apt upgrade
sudo apt install libreoffice
```

## Git

```console
sudo aptitude install git
```

## Bash-it

```console
git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it
~/.bash_it/install.sh
```

## Tmux

```console
sudo aptitude install tmux 
git clone https://github.com/samoshkin/tmux-config.git
./tmux-config/install.sh
```
copy a config file from another computer

## Misc
```console
sudo aptitude install htop
sudo aptitude install xclip
sudo aptitude install imagemagick
```

