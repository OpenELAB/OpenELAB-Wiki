---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# T-Deck Plus Meshtastic

{% hint style="info" %}
[**View LILYGO T-Deck Plus Meshtastic on OpenELAB**](https://openelab.io/products/lilygo-t-deck-plus)

**Model/variant:** LILYGO T-Deck Plus Meshtastic · **SKU:** `LILYGO-H736-03-Mesh`
{% endhint %}

## LILYGO T-Deck Plus Meshtastic Support Meshtastic UI

***

## Product Link

{% embed url="https://openelab.io/products/lilygo-t-deck-plus" %}

## Description

1. T-Deck-Plus has assigned the pins on the **Grove** interface to the GPS module, so the **Grove** interface of T-Deck-Plus cannot be used.
2. T-Deck updated [TFT\_eSPI ST7789 initialization sequence](https://github.com/Xinyuan-LilyGO/T-Deck/commit/6adb8884c689f174c29a6d7172a0daa367a582eb) on 20240726. Currently, the changes have not been pushed to the TFT\_eSPI upstream branch. If you find that the screen display is incorrect during use, please check whether this is consistent with the initialization sequence in the warehouse.

## **Specifications**

| MCU                   | **ESP32-S3FN16R8** Dual-core LX7 microprocessor |
| --------------------- | ----------------------------------------------- |
| Wireless Connectivity | 2.4 GHz Wi-Fi & Bluetooth 5 (LE)                |
| Development           | Arduino, PlatformlO-IDE, Micropython            |
| Flash                 | 16MB                                            |
| PSRAM                 | 8MB                                             |
| Battery ADC PIN       | IO04                                            |
| Onboard functions     | **GPS,TF Card**,Microphone,Speaker              |

| <p><strong>2.8 inch ST7789 SPI Interface IPS LCD:</strong></p><p>Resolution: 320 x 240 Full viewing angle</p> |
| ------------------------------------------------------------------------------------------------------------- |

| **SX1262 LoRa Transceiver** |
| --------------------------- |

| Transmit power     | +22dBm         |
| ------------------ | -------------- |
| Frequency Optional | 433/868/915Mhz |

## Get Start

#### PlatformIO

1. Install [VisualStudioCode](https://code.visualstudio.com/) and [Python](https://www.python.org/)
2. Search for the `PlatformIO` plugin in the `VisualStudioCode` extension and install it.
3. After the installation is complete, you need to restart `VisualStudioCode`
4. After restarting `VisualStudioCode`, select `File` in the upper left corner of `VisualStudioCode` -> `Open Folder` -> select the `T-Deck` directory
5. Click on the `platformio.ini` file, and in the `platformio` column, cancel the sample line that needs to be used, please make sure that only one line is valid
6. Click the (✔) symbol in the lower left corner to compile
7. Connect the board to the computer USB
8. Click (→) to upload firmware
9. Click (plug symbol) to monitor serial output

#### ArduinoIDE

1. Install [Arduino IDE](https://www.arduino.cc/en/software)
2. In Arduino Preferences, on the Settings tab, enter the `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json` URL in the `Additional boards manager URLs` input box. **Please pay attention to the version. The test phase is using 2.0.14. It is not certain that versions above 2.0.14 can run. When the operation is abnormal, please downgrade to a version below 2.0.14.** , As of 2024/08/02, TFT\_eSPI does not work on versions higher than 2.0.14, see [TFT\_eSPI/issue3329](https://github.com/Bodmer/TFT_eSPI/issues/3329)
3. Copy all the folders in the `T-Deck/lib` directory to `<C:\Users\UserName\Documents\Arduino\libraries>`. If there is no `libraries` directory, please create a new one. Please note that you are not copying the `lib` directory, but copying the folders in the lib directory
4. Open ArduinoIDE ,`Tools` , Look at the picture to choose

| T-Deck(ESP32S3)                                                                                                                                | T-Keyboard(ESP32C3)                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [![s3](https://github.com/Xinyuan-LilyGO/T-Deck/raw/master/images/s3.jpg)](https://github.com/Xinyuan-LilyGO/T-Deck/blob/master/images/s3.jpg) | [![c3](https://github.com/Xinyuan-LilyGO/T-Deck/raw/master/images/c3.jpg)](https://github.com/Xinyuan-LilyGO/T-Deck/blob/master/images/c3.jpg) |

5. Insert USB into the PC and click Upload \<If the upload fails, keep pressing the BOOT button, click RST, and then click Upload. When the upload is complete, click RST to exit the download mode>

{% hint style="warning" %}
1) If a microphone is used, the GPIOO button cannot be used
2) If the sketch cannot be uploaded, then you need to press down the middle of the trackball, and then insert the USB, this means the chip is in the download mode, and then click to upload the sketch.
3) T-Keyboard the programming and burning interface of ESP32C3 is located at the 6Pin header on the side of the RST button, and the order starts from the top of the RST button, which are TX,RX,BOOT,RST,GND,VCC, You need to connect USB TO TTL externally to burn the keyboard firmware. For TTL without automatic download circuit, before powering on, short-circuit the BOOT Pin and GND, and then power on. At this time, T-Keyboard will enter the download mode. After the burning is completed, you need to disconnect GND and BOOT before running the program.
4) T-Deck can't upload any sketch，Please enter the upload mode manually.
   1. Connect the board via the USB cable
   2. Press and hold the BOOT button , While still pressing the BOOT(On the trackball above the keyboard, press down) button
   3. Press RST button
   4. Release the RST button
   5. Release the BOOT button
   6. Upload sketch
   7. If you still cannot upload the sketch successfully according to the above method, please check whether the resistor in this [issue62](https://github.com/Xinyuan-LilyGO/T-Deck/issues/62) exists. Please remove it and test again.
{% endhint %}

## Github

[https://github.com/Xinyuan-LilyGO/T-Deck](https://github.com/Xinyuan-LilyGO/T-Deck)

## First working result: two-node Meshtastic message

1. Confirm that this is **T-Deck Plus**, not T-Deck Pro or the original T-Deck. Install its antenna before any LoRa transmission and verify the purchased 868/915/433 MHz hardware variant, regional frequency configuration and legal operating constraints.
2. Power the unit on and record the displayed firmware version. If updating, use the [Meshtastic T-Deck/T-Deck Plus hardware guide](https://meshtastic.org/docs/hardware/devices/lilygo/tdeck/) to select the correct **T Deck** firmware target, or follow LILYGO's model-specific boot/upload procedure. Do not use the T-Deck Pro image.
3. Connect the device to a Meshtastic client over the documented transport, set the appropriate regional profile, and place it on the same channel as a second functioning Meshtastic node.
4. Send a short test text message between the two nodes, then reverse the direction. Record each node's reported radio configuration, firmware version and signal status.

**Expected result:** the message appears on the other node and a reply is received. **If this fails:** confirm the correct radio-frequency model, connected antenna, matching channel/keys, device region, firmware target, LoRa initialization and node separation.

**Hardware-specific constraint:** LILYGO states that the T-Deck Plus's GPS module uses the Grove connector pins, so do **not** treat the Grove header as a free general-purpose expansion port. The Plus version also has a capacitive touch interface absent from the original T-Deck. See the [official T-Deck Plus hardware reference](https://wiki.lilygo.cc/products/t-deck-series/t-deck-plus/).

**Validation:** this is a manufacturer-sourced setup sequence; software compilation and physical two-node testing were not run in this update.
