# DellXPSUbuntuSetup
So you fried your laptop again...

I found this handy: https://medium.com/@asad.manji/my-journey-installing-ubuntu-20-04-on-the-dell-xps-15-9500-2020-8ac8560373d1

**NOTE: IF AT ANY TIME YOU GET THE BLACK SCREEN WITH A BLINKING CURSOR, PRESS CTRL+ALT+F# KEYS UNTIL THE LOGIN SCREEN APPEARS**
https://askubuntu.com/questions/1251005/ubuntu-20-04-boots-to-black-screen-with-flashing-cursor

Or if you get stuck at the beginning with something like "/dev/sda2: clean, ###/### files, ###/### blocks:

- Ctrl+Alt+F2 which will lead you to a tty,
- login into tty using username and password,
- then, enter `sudo apt install --reinstall gnome gdm3`

You may also need to purge nvidia* and install later:
```console
sudo apt-get purge nvidia*
sudo add-apt-repository ppa:graphics-drivers
sudo apt update
sudo apt upgrade
```

see here: https://askubuntu.com/questions/850670/ubuntu-stuck-on-boot-wont-get-past-fsck

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

## Zotero

https://www.zotero.org/download/

https://www.zotero.org/support/installation

```console
tar -xvf Zotero-5.0.96.3_linux-x86_64.tar.bz2
cd Zotero_linux-x86_64/
./zotero
cd ..
sudo mv Zotero_linux-x86_64 /opt/Zotero
cd /opt/Zotero/
./set_launcher_icon
ln -s /opt/Zotero/zotero.desktop ~/.local/share/applications/zotero.desktop
```

## Misc
```console
sudo aptitude install htop
sudo aptitude install xclip
sudo aptitude install imagemagick
sudo aptitude install smplayer
sudo aptitude install gimp
sudo aptitude install python3-pip
```

## Global Protect
https://hub.bcchr.ca/display/it/BCCHR+VPN+Setup?preview=/62457318/87884060/PanGPLinux-5.1.1-c17.tgz

Edit the /etc/hosts:
>192.168.34.174  CSPeirce  
192.168.34.81  AdaL  
192.168.34.141  Boltzmann  

```console
ssh-keygen
```
and
```console
ssh-copy-id username@computeraddress
```

## Fans and Sensors

https://www.reddit.com/r/Dell/comments/gqas5s/best_configuration_for_a_silent_fan_with_xps_15/

https://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/

https://askubuntu.com/questions/1227489/i8kctl-not-working-for-dell-inspiron-fan-control

```console
sudo modprobe -v i8k
sudo apt-get install i8kutils
cat /etc/i8kmon.conf
```

```
 # Sample i8kmon configuration file (/etc/i8kmon.conf, ~/.i8kmon).
 
 # External program to control the fans
 set config(i8kfan)  /usr/bin/i8kfan
 
 # Report status on stdout, override with --verbose option
 set config(verbose) 0
 
 # Status check timeout (seconds), override with --timeout option
 set config(timeout) 2
 # Temperature display unit (C/F), override with --unit option
 set config(unit)    C
 # Temperature threshold at which the temperature is displayed in red
 set config(t_high)  85
 # Minimum expected fan speed
 set config(min_speed) 2000
 
 # Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
 # These were tested on the I8000. If you have a different Dell laptop model
 # you should check the BIOS temperature monitoring and set the appropriate
 # thresholds here. In doubt start with low values and gradually rise them
 # until the fans are not always on when the cpu is idle. 
 set config(0)   {{0 0}  -1  70  -1  75}
 set config(1)   {{0 1}  65  80  65  80}
 set config(2)   {{1 1}  75  85  75  85}
 set config(3)   {{2 2}  80 128  80 128}
 
 # Speed values are set here to avoid i8kmon probe them at every time it starts.
 set status(leftspeed)   "0 1250 2500 5000"
 set status(rightspeed)  "0 1250 2500 5000"
 
 # end of file
 ```

## Power

### TLP

```bash
sudo apt install tlp tlp-rdw
systemctl enable tlp.service
sudo tlp start
```

### auto-cpufreq

don't use this with TLLP. Pick one.
https://github.com/AdnanHodzic/auto-cpufreq
