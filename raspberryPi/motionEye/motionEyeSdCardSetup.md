# Setup SD Card

## Mac

Get latest version of of motioneye and get writeImage.sh from the github repo

insert sd card and find the diskID for the SD card.



```
diskutil list
```

unmount the disk so it can be worked on

```
diskutil unmountDisk /dev/disk2
```

write the image to the sd card with the following network settings.

```
sudo ./writeimage.sh -d /dev/disk2 -i "motioneyeos-raspberrypi-20181129.img" -n '<WIFINAME>:<WIFIPASSWORD>'
```
# Sources
https://learn.pimoroni.com/tutorial/sandyj/motioneye-os-on-your-octocam

http://www.whatimade.today/motioneyeos-writeimage-sh-how-to-configure-for-mac/


## Motion Eye Releases
https://github.com/ccrisan/motioneyeos/releases
