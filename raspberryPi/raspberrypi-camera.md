# Troubleshoot

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