# Basic setup for raspberry pi

1. write img file to sd card
2. in the root of the sd card make a file called ssh
3. find the ip address of the pi
4. ssh to raspberry pi by using user pi password raspberry

## Change to a real editor

```bash
sudo update-alternatives --config editor
```

## Add personal user

```bash
sudo adduser simon
sudo visudo

simon   ALL=(ALL:ALL) ALL
```

## switch accounts

```bash
su simon
```

## generate ssh keys

```bash
ssh-keygen
```

## Change the network interface

Set the eth0 interface to static

```bash
sudo vi /etc/dhcpcd.conf
```

```bash
interface eth0
  static ip_address=192.168.0.195/24
  static routers=192.168.0.251
  static domain_name_servers=192.168.0.234 8.8.8.8
```

## Generate SSH keys

```bash
ssh-keygen
```

## Get SSH keys

```bash
cd ~/.ssh
wget -O authorized_keys www.pixelpox.co.uk/sshkeys
```

## Change Hostname

```bash
sudo vi /etc/hostname
sudo vi /etc/hosts
```

## Update Raspberry Pi

```bash
sudo apt-get update
sudo apt-get upgrade
```

## Install software

```bash
sudo apt-get -y install git curl screen
```

## reboot the pi

```bash
sudo reboot now
```

## Remove the pi user

```bash
sudo deluser -remove-home pi
```

## configure git

read this to setup ssh keys
[https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

read this to setup ssh pushing
[https://gist.github.com/developius/c81f021eb5c5916013dc](https://gist.github.com/developius/c81f021eb5c5916013dc)

configure the local Client

```bash
git config --global user.email ""
git config --global user.name ""
```

## cheatsheet for github

```bash
git push  <REMOTENAME> <BRANCHNAME>
```

## source

1. <https://hackernoon.com/raspberry-pi-headless-install-462ccabd75d0>

2. <https://raspi.tv/2012/how-to-create-a-new-user-on-raspberry-pi>

3. <https://www.modmypi.com/blog/how-to-give-your-raspberry-pi-a-static-ip-address-update>

4. <https://www.jeffgeerling.com/blog/2018/setting-static-ip-address-raspbian-jessie-lite-on-raspberry-pi>

5. <https://thepihut.com/blogs/raspberry-pi-tutorials/19668676-renaming-your-raspberry-pi-the-hostname>
