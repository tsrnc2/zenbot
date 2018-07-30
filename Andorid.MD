## Android

prerequisites
-You will need a armv6 or newer device. Don't know what you have https://www.quora.com/How-do-I-know-if-an-Android-device-is-running-on-ARMv7-or-ARMv6. 

-Internet access to the device and access to the google play store. It is possible to perform installation off-line but I won’t go into that here.

-You will need background data turned on and battery saver turn off

-Root (optional) for optimizing your device. Not necessary

1) Start by installing Termux from the play store, and start it up. On first startup it will download and install a base gnu OS and chroot into it. On some systems Termux will start with limited permissions, in that case enter 
$ su 

2) Install arch linux inside termux 

$ pkg install wget

$ wget https://raw.githubusercontent.com/sdrausty/TermuxArch/master/setupTermuxArch.sh

$ bash setupTermuxArch.sh

3) Enter archlinux chroot

$ startarch

4) Install dependices
 
$ pacman -Sy nodejs-lts-carbon python2 base-devel npm
 
$ ln -s /usr/bin/python2 /usr/bin/python

5) Download zenbot and configure

$ git clone https://github.com/deviavir/zenbot.git

$ cd zenbot

$ cp conf-sample.js conf.js

$ nano conf.js

$ npm install

6) install mongodb
you have 2 options 
 Option 1)Arch mongodb 
 In a new termux session(scroll from left side of screen)
 
 $ startarch
 
 $ pacman -S mongodb
 
 $ mongod 
 
 Option 2) native android mongodb with "dory mongodb" in play store

7) After you have mongodb running start zenbot with

$ bash zenbot.sh (standard options)

8) restarting
close all termux sessions
from a fresh termux session

 $ startarch
 
 $ cd zenbot
 
 $ bash zenbot.sh


9) Optimizing (Optional) Only if your know what your doing

- You will need root on the device.

- You will need to know a bit about linux to continue namely how to find the pid of your termux process.

- You will need a native terminal(not termux) and enable shell access in development options.

SOFT and HARD being your SOFT and HARD no file limits, 10000 works nicely on a pixel2 you will need to experiment with your device
enter this as root, a warning asking for root permissions may appear, grant them.

$ su

$ pr limit ${PID} 7 SOFT HARD 

 Inside your termux arch chroot you will need to edit the file /etc/security/limits.conf and adjust your no file to match.
