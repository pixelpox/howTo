# How to get MQTT working with TTN network

The main commant to recieve messages from a device is;

```
mosquitto_sub -h eu.thethings.network -t '+/devices/+/up' -u '<AppID>' -P '<AppKey>' -v
```

These can both be found unser the application page on The Things Network.

* AppId = Application Id
* Appkey = Access Key

![](images\LORAWAN\appid-example.PNG "appId example")


![](images\LORAWAN\accesskey-example.PNG "Application Key Example")

The following information can be used in MQTTBox client to listen for any updates. 

![](images\LORAWAN\mqttbox-client-settings.PNG)

A wide scope example of listening to all devices that upload information to the MQTT server.

![](images\LORAWAN\mqttbox-client-settings.PNG)
# Source

1. https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-the-mosquitto-mqtt-messaging-broker-on-ubuntu-16-04

2. https://www.thethingsnetwork.org/docs/applications/mqtt/quick-start.html