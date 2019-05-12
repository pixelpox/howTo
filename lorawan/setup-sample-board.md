# How to set up TTGO ESP32 lorawan board

## Setup Arduino Environment

Download the library for the LCD if that is going to be used

```bash
git clone https://github.com/ThingPulse/esp8266-oled-ssd1306.git
```

Also add the following libraries

```bash
git clone https://github.com/sandeepmistry/arduino-LoRa.git
git  clone https://github.com/matthijskooijman/arduino-lmic.git
```

If you don't know where the library is stored then goto the preferences dialogue and take note of the system path.
![](image/Screen&#32;Shot&#32;2019-04-23&#32;at&#32;11.58.44.png)

## Set the board settings

Add an additional board by using preferences. The URL you will want to add is;

```html
https://dl.espressif.com/dl/package_esp32_index.json
```

You will want to setup the board the same as mine

![](image/Screen&#32;Shot&#32;2019-04-23&#32;at&#32;11.50.35.png)


#€ Get a copy of the code

...

#€ Set the following variables

Set the following variables from the TTN application page.

```c
NWKSKEY[]
APPSKEY[]
DEVADDR
```

## Use the correct pin layout

Here is the correct pin layout for the TTGO v1 board (The one without a SD card slot).

```c
// Pin mapping
const lmic_pinmap lmic_pins = {
    .nss = 18,
    .rxtx = LMIC_UNUSED_PIN,
    .rst = 14,
    .dio = {/*dio0*/ 26, /*dio1*/ 33, /*dio2*/ 32} // Pins for the Heltec ESP32 Lora board/ TTGO Lora32 with 3D metal antenna
};
```

## Turn off frame counting

For development purposes its best to disable the frame counter on the TTN website, this can be found under the application you are working on.

The reason for turning this off is because if the frame counter doesn't match then it will be rejected and the reason why it wouldn't match is because when the device is power cycled the counter will start at 0 again.