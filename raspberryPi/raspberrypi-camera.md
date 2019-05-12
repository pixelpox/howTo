# Setup streaming camera

```bash
sudo apt-get install mplayer
sudo apt-get install vlc
```

## OpenCV

To help the pi make the application faster set the swap to a larger size

```bash
sudo vi /etc/dphys-swapfile
sudo /etc/init.d/dphys-swapfile stop
sudo /etc/init.d/dphys-swapfile start

```

add opencv2 to the local/lib folder if it is missing

```bash
sudo ln -s /usr/local/python/cv2/python-3.5/cv2.so /usr/local/lib/python3.5/dist-packages/cv2.so
```

## Troubleshoot

When the following error is shown

```bash
* failed to open vchiq instance
```

It can be fixed by using the following command

```bash
sudo usermod -a -G video $(whoami)
```

## sources

* https://www.raspberrypi.org/documentation/usage/camera/raspicam/raspistill.md
* https://raspberrypi.stackexchange.com/questions/19436/how-can-i-permanently-fix-dev-vchiq-permission-errors

* https://averagemaker.com/2015/06/make-a-raspberry-pi-ip-camera-viewer.html

## opencv - sources

* (tutorial) https://www.pyimagesearch.com/2017/09/04/raspbian-stretch-install-opencv-3-python-on-your-raspberry-pi/
* https://www.pyimagesearch.com/2018/09/26/install-opencv-4-on-your-raspberry-pi/
* https://www.raspberrypi.org/forums/viewtopic.php?t=191188
* https://www.pyimagesearch.com/2016/04/18/install-guide-raspberry-pi-3-raspbian-jessie-opencv-3/
* https://dzone.com/articles/how-to-deploy-opencv-on-raspberry-pi-enabling-mach