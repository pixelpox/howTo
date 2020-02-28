When I tried to follow the online guides I found that running `cloudflared -v` would cause a Segmentation fault on the raspberry pi.

I found the following solution that replaces the equinox source with hobins.

The commands below have been adapted for this.


```bash
wget -O cloudflared-stable-linux-arm.tgz https://hobin.ca/cloudflared/latest?type=tar

tar -xvzf cloudflared-stable-linux-arm.tgz
sudo cp ./cloudflared /usr/local/bin
sudo chmod +x /usr/local/bin/cloudflared
cloudflared -v
```

## add user

```bash
sudo useradd -s /usr/sbin/nologin -r -M cloudflared
```

## add config file

```bash
sudo vi /etc/default/cloudflared
```

paste the following;

```
# Commandline args for cloudflared
CLOUDFLARED_OPTS=--port 5053 --upstream https://1.1.1.1/dns-query --upstream https://1.0.0.1/dns-query
```

## update permissions

```bash
sudo chown cloudflared:cloudflared /etc/default/cloudflared
sudo chown cloudflared:cloudflared /usr/local/bin/cloudflared
```

## create service file

```bash
sudo vi /etc/systemd/system/cloudflared.service
```

paste in the following contents;

```
[Unit]
Description=cloudflared DNS over HTTPS proxy
After=syslog.target network-online.target

[Service]
Type=simple
User=cloudflared
EnvironmentFile=/etc/default/cloudflared
ExecStart=/usr/local/bin/cloudflared proxy-dns $CLOUDFLARED_OPTS
Restart=on-failure
RestartSec=10
KillMode=process

[Install]
WantedBy=multi-user.target
```

## enable and start the service

```bash
sudo systemctl enable cloudflared
sudo systemctl start cloudflared
sudo systemctl status cloudflared
```

if at this point there is a SEG FAULT then make sure to change the wget to hobin source for the latest file

## how to update

```bash

sudo systemctl stop cloudflared
wget -O cloudflared-stable-linux-arm.tgz https://hobin.ca/cloudflared/latest?type=tar

tar -xvzf cloudflared-stable-linux-arm.tgz
sudo cp ./cloudflared /usr/local/bin
sudo chmod +x /usr/local/bin/cloudflared
sudo systemctl start cloudflared
sudo systemctl status cloudflared

```

## dnsmasq config

```bash
sudo vi /etc/dnsmasq.d/50-cloudflared.conf
```

```
server=127.0.0.1#5053
```


## pihole gui setup

goto `http://pihole/admin/settings.php?tab=dns`

add the following to upstream DNS Servers

```
127.0.0.1#5053
``` 

## verify setup

goto the following link to make sure everything is working correctly https://1.1.1.1/help

## troubleshoot

if any of the checks come back as no, use the following steps to work it out

### localhost (on the pi)

do a local dig
```bash
dig @127.0.0.1 -p 5053 google.com
```

### Windows
in windows get a command prompt and use

```cmd
ipconfig /all
```

note the ip address of the dns server, if it is anything other then pihole remove it

### windows - flush dns

use the following command to flush the dns cache

```cmd
ipconfig /flushdns
```

## source

1. https://docs.pi-hole.net/guides/dns-over-https/

2. https://github.com/cloudflare/cloudflared/issues/38

3. https://bendews.com/posts/implement-dns-over-https/

