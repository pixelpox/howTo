# Basic setup for raspberry pi

1. write img file to sd card
2. in the root of the sd card make a file called ssh
3. find the ip address of the pi
4. ssh to raspberry pi by using user pi password raspberry

# Add personal user
sudo adduser simon
sudo visudo

add your user here

# Remove the pi user
sudo deluser -remove-home pi

# Change the network interface
Set the eth0 interface to static
```
sudo vi /etc/dhcpcd.conf
```
```
interface eth0
  static ip_address=192.168.0.34/24
  static routers=192.168.0.251
  static domain_name_servers=192.168.0.234 8.8.8.8
```
# Get ssh keys
```
cd ~/.ssh
wget -O authorized_keys www.pixelpox.co.uk/sshkeys
```
# Change Hostname

sudo vi /etc/hostname
sudo vi /etc/hosts

# Update Raspberry Pi
```
sudo apt-get update
sudo apt-get upgrade
```

# Install software
```
sudo apt-get install git
```

# source
* https://hackernoon.com/raspberry-pi-headless-install-462ccabd75d0

* https://raspi.tv/2012/how-to-create-a-new-user-on-raspberry-pi

* https://www.modmypi.com/blog/how-to-give-your-raspberry-pi-a-static-ip-address-update

* https://www.jeffgeerling.com/blog/2018/setting-static-ip-address-raspbian-jessie-lite-on-raspberry-pi

* https://thepihut.com/blogs/raspberry-pi-tutorials/19668676-renaming-your-raspberry-pi-the-hostname
