# Bypass vpn

## example

```bash
sudo route -n

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.251   0.0.0.0         UG    100    0        0 enp0s3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s3
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s3
```

when vpn is started routing table looks like the following

```bash

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.2.1        128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.0.251   0.0.0.0         UG    100    0        0 enp0s3
10.8.2.0        0.0.0.0         255.255.255.0   U     0      0        0 tun0
89.238.143.60   192.168.0.251   255.255.255.255 UGH   0      0        0 enp0s3
128.0.0.0       10.8.2.1        128.0.0.0       UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s3
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp0s3

```


sudo ip rule add table 192 from 192.168.0.199
sudo ip route add table 192 to 192.168.0.0/24 dev enp0s3
sudo ip route add table 192 default via 192.168.0.251 dev enp0s3
sudo ip route flush cache

dosent work
sudo ip rule add fwmark 22 table 192
sudo iptables -t mangle -I OUTPUT -p tcp --sport 22 -d !192.168.1.0/24 -j MARK --set-mark 22
----
<https://unix.stackexchange.com/questions/145635/debian-cli-torrent-program-through-vpn/145783#145783>
sudo iptables -t mangle -A OUTPUT -p tcp --sport 22 -j MARK --set-mark 22
sudo iptables -A INPUT -i tun0 -p tcp -m tcp --dport 22 -j DROP

sudo route add -h 192.168.0.208 gw 192.168.0.251


----

ip rule add from x.x.x.x table 128
ip route add table 128 to y.y.y.y/y dev eth0
ip route add table 128 default via z.z.z.z

sudo ip route add 192.168.0.0/24 via 192.168.0.251 dev enp0s3

----

working example
<https://www.digitalocean.com/community/tutorials/iptables-essentials-common-firewall-rules-and-commands>
<https://support.nordvpn.com/Connectivity/Linux/1182453582/Installing-and-using-NordVPN-on-Linux.htm>

sudo iptables -A INPUT -s 192.168.0.0/24 -p tcp --dport 22 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --sport 22 -m conntrack --ctstate ESTABLISHED -j ACCEPT

sudo iptables -A INPUT -s 192.168.0.0/24 -p tcp --dport 58846 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --sport 58846 -m conntrack --ctstate ESTABLISHED -j ACCEPT

sudo iptables -A INPUT -s 192.168.0.0/24 -p tcp --dport 8112 -m conntrack --ctstate NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --sport 8112 -m conntrack --ctstate ESTABLISHED -j ACCEPT