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

# SenseCAP Indicator for Meshtastic & LoRa

### Seeed Studio SenseCAP Indicator for Meshtastic & LoRa

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description

SenseCAP Indicator is a 4-inch touchscreen device designed for Meshtastic®, powered by dual MCUs, the ESP32 and RP2040, and supports Wi-Fi, BLE, and LoRa®. It is an open-source, powerful IoT development platform.

### Feature

* **Supports Meshtastic:** Pre-flashed with Meshtastic firmware, it is ready to work once powered on. You can also upgrade the firmware using Meshtastic Flasher.<br>
* **Dual MCUs and Rich GPIOs:** Equipped with powerful ESP32S3 and RP2040 dual MCUs and over 400 Grove-compatible GPIOs for flexible expansion options.<br>
* **Local LoRa® Hub for IoT Connectivity:** Integrated with the Semtech SX1262 LoRa® chip, the device can be converted to a LoRaWAN® Single-Channel Gatewa via tutorial. Alternatively, connect LoRa® devices to popular IoT platforms like Matter via Wi-Fi.<br>
* **Fully Open Source Platform:** Leverage the extensive ESP32 and Raspberry Pi open-source ecosystem for infinite application possibilities.<br>
* **Suitable for Multiple Application Scenarios:** Can be used as a Meshtastic desktop node or a car node, as well as a LoRaWAN® Single-Channel Gateway.

### Specification

| Screen                        | 3.95 Inch, Capacitive RGB Touch Screen                                                                                                   |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Screen Resolution**         | 480 x 480 pixels                                                                                                                         |
| **Power Supply**              | 5V-DC, 1A                                                                                                                                |
| **Battery**                   | N/A                                                                                                                                      |
| **Processor**                 | <p><strong>ESP32-S3:</strong> Xtensa® dual-core 32-bit up to 240 MHz</p><p><strong>RP2040:</strong> Dual ARM Cortex-M0+ up to 133MHz</p> |
| **Flash**                     | <p><strong>ESP32-S3:</strong> 8MB</p><p><strong>RP2040:</strong> 2MB</p>                                                                 |
| **External Storage**          | Support up to 32GB Micro SD Card (not included)                                                                                          |
| **Wi-Fi**                     | 802.11b/g/n, 2.4GHz                                                                                                                      |
| **Bluetooth**                 | Bluetooth 5.0 LE                                                                                                                         |
| **LoRa(SX1262**)              | Support 862-930MHz                                                                                                                       |
| **Buzzer(Not developed yet)** | MLT-8530, Resonant Frequency：2700Hz                                                                                                      |
| **Certification**             | CE/FCC                                                                                                                                   |

### Hardware

<figure><img src="../../.gitbook/assets/image (1039).png" alt=""><figcaption></figcaption></figure>

#### Flash

{% hint style="success" %}


To enter the 2.6 MUI preview page, press keys on your computer keyboard: ↑ ↑ ↓ ↓ ← → ← → b a\
Then the page will turn black, you can see the pre-release option now.

<p align="center"><img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/2.6-ver.png" alt="" data-size="original"></p>
{% endhint %}

### Flash Application Firmware

{% embed url="https://www.youtube.com/watch?v=55Sz8kHSyV4" %}

Visit [Meshtastic Web Flasher](https://flasher.meshtastic.org/).

Select the target device to `Seeed SenseCAP Indicator` and choose the latest firmware, then click `Flash`.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/indicator-flash.png" alt="" width="800">

Press and hold the button while plugging in the USB cable.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/press-button.png" alt="" width="400">

Enable the `Full Erase and Install`, and click `Erase Flash and Install`.

There will show 2 ports, select the `USB serial port` and click `Connect`.

{% hint style="warning" %}
note

Please select the `USB Serial` one, not the INDICATOR RP2040.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (1041).png" alt=""><figcaption></figcaption></figure>

#### Flash GPS Firmware <a href="#flash-gps-firmware" id="flash-gps-firmware"></a>

The SenseCAP Indicator doesn't have a GPS built-in, to get the GPS location, a [Grove GPS Module](https://www.seeedstudio.com/Grove-GPS-Air530-p-4584.html) is required.\
Connect the GPS Module to the Grove port and then flash the GPS firmware.

* [**GPS Firmware Download**](https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/meshtastic_gps.ino.uf2)

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/gps-connect.png" alt="" width="800">

Long press this internal button using a needle, then connect the device to your PC by the provided USB type-C cable, release the button once connected.

<figure><img src="../../.gitbook/assets/image (1042).png" alt=""><figcaption></figcaption></figure>

Download the `UF2` file and copy it to the `RPI-RP2` drive. Firmware should be flashed after the file is downloaded and the device reboots.

<figure><img src="../../.gitbook/assets/image (1043).png" alt=""><figcaption></figcaption></figure>

### Get Started[​](https://wiki.seeedstudio.com/sensecap_indicator_meshtastic/#get-started) <a href="#get-started" id="get-started"></a>

Download `Meshtastic` App:

* [IOS App](https://meshtastic.org/docs/category/apple-apps/)
* [Android App](https://meshtastic.org/docs/category/android-app/)

#### Connect via App[​](https://wiki.seeedstudio.com/sensecap_indicator_meshtastic/#connect-via-app) <a href="#connect-via-app" id="connect-via-app"></a>

* Power on the device, the device page will display the mac address of the current device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/device-name4.png" alt="" width="700">

{% tabs %}
{% tab title="IOS App" %}


* Select the target device on the Bluetooth panel.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/connect-radio.png" alt="" width="300">

* Enter the code and then click `Pair` to connect the device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/pair111.png" alt="" width="800">
{% endtab %}

{% tab title="Android App" %}


* Click `+` and choose the target device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/an-choose.png" alt="" width="600">

* Enter the code(default code is `123456`) and then click `OK` to connect the device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/click-ok.png" alt="" width="300">
{% endtab %}
{% endtabs %}

#### Configure the Parameters[​](https://wiki.seeedstudio.com/sensecap_indicator_meshtastic/#configure-the-parameters) <a href="#configure-the-parameters" id="configure-the-parameters"></a>

In order to start communicating over the mesh, you must set your region. This setting controls which frequency range your device uses and should be set according to your regional location.

{% tabs %}
{% tab title="IOS App" %}
<figure><img src="../../.gitbook/assets/image (1045).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Android App" %}
<figure><img src="../../.gitbook/assets/image (1046).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

**Region List**

| **Region Code** |    **Description**    | **Frequency Range (MHz)** | **Duty Cycle (%)** | **Power Limit (dBm)** |
| :-------------: | :-------------------: | :-----------------------: | :----------------: | :-------------------: |
|      UNSET      |         Unset         |            N/A            |         N/A        |          N/A          |
|        US       |     United States     |       902.0 - 928.0       |         100        |           30          |
|     EU\_868     | European Union 868MHz |       869.4 - 869.65      |         10         |           27          |

Refer to [LoRa Region by Country](https://meshtastic.org/docs/configuration/region-by-country/) for a more comprehensive list.

{% hint style="success" %}
**EU\_868** has to adhere to an hourly duty cycle limitation of 10%, calculated every minute on a rolling 1-hour basis. Your device will stop transmitting if you reach it, until it is allowed again.
{% endhint %}

Now that you have set the LoRa region on your device, you can continue with configuring any [LoRa Configs](https://meshtastic.org/docs/configuration/radio/lora/) to suit your needs.

### Precautions[​](https://wiki.seeedstudio.com/sensecap_indicator_meshtastic/#precautions) <a href="#precautions" id="precautions"></a>

**Role Selection**[**​**](https://wiki.seeedstudio.com/sensecap_indicator_meshtastic/#role-selection)

{% hint style="warning" %}
DO NOT select the Repeater role, which will cause the device to repeatedly reboot.
{% endhint %}

**GPS Module**[**​**](https://wiki.seeedstudio.com/sensecap_indicator_meshtastic/#gps-module)

If you didn't connect the GPS module, please disable the GPS function in the `Meshtastic` App, otherwise the device will keep trying to find the GPS module, which will cause the device to take a long time to boot up the screen.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/gps-module.png" alt="" width="600">
