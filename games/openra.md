# How to install OpenRA in linux

## Quick information

Current version: release-20190314

download location: https://www.openra.net/download/

## pre prerequisites

mono 4.2 or later
64 bit system

## How to find current version of ubuntu

run the following command in terminal

```bash
lsb_release -a
```

## How to find if you have a 64 bit operating system

run the following command in terminal and look for 'x86_64'

```bash
uname -a
```

## How to install mono

### Add the Mono repo

```bash
#steps for ubuntu 18.04
sudo apt install gnupg ca-certificates
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
echo "deb https://download.mono-project.com/repo/ubuntu stable-bionic main" | sudo tee /etc/apt/sources.list.d/mono-official-stable.list
sudo apt update
```

### Install Mono

```bash
#steps for ubuntu 18.04
sudo apt install mono-complete -y
```

## Download and Run OpenRA

```bash
wget https://github.com/OpenRA/OpenRA/releases/download/release-20190314/OpenRA-Red-Alert-x86_64.AppImage
```

change permission to execute for current user

```bash
chmod u+x OpenRA-Red-Alert-x86_64.AppImage
```

run the game

```bash
./OpenRA-Red-Alert-x86_64.AppImage
```

## Sources

* [how to install mono](https://www.mono-project.com/download/stable/#download-lin-ubuntu)
* [how to find current ubuntu version](https://www.hostingadvice.com/how-to/ubuntu-show-version/)
* [How to check if you are running 64bit ubuntu](https://askubuntu.com/questions/41332/how-do-i-check-if-i-have-a-32-bit-or-a-64-bit-os)