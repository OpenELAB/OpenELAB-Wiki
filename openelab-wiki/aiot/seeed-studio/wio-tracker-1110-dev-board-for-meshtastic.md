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

# Wio Tracker 1110 Dev Board for Meshtastic

### Seeed Studio Wio Tracker 1110 Dev Board for Meshtastic

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-wio-tracker-1110-dev-board-for-meshtastic" %}

### Description

Featuring a Wio Tracker 1110 Dev Board (based on Nordic nRF52840 for BLE, Semtech LR1110 for LoRa), Grove Air530 GPS Module, Grove0.96" OLED Display and native compatibility with Meshtastic firmware, it's a plug and play dev kit for you to build your low-power Meshtatstic tracker device.

### Features

* **Easy Setup**: Simply flash the firmware to experience the powerful features of the Meshtastic network.
* **Real-time Positioning**: Equipped with a GPS (Air530) module, supporting high-precision GPS positioning.
* **Information Display**: Features a Grove - OLED Display 0.96" screen for clear real-time data visualization.
* **Extensive Expansion Interfaces**: Compatible with the Grove ecosystem, allowing easy expansion with more sensors and modules.
* **Open-source Hardware and Software**: Supports secondary development and customization, providing rich development resources and Meshtastic community support.

### Specification

| General                                             |                                                                                            |                                                                  |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- |
| Voltage - supply                                    | 5V (USB 2.0 Type-C)                                                                        |                                                                  |
| Battery Connector                                   | 3.7V                                                                                       |                                                                  |
| Interface                                           | RFIO                                                                                       | <p>GNSS Antenna Connector* 1</p><p>LoRa Antenna Connector* 1</p> |
| USB type-C                                          | \* 1                                                                                       |                                                                  |
| Grove Interface                                     | <p>ADC* 1I2C* 1UART* 1</p><p>Digital*3</p>                                                 |                                                                  |
| Button                                              | USER                                                                                       | Configurable button                                              |
| RESET                                               | Reset                                                                                      |                                                                  |
| Exterior FLASH Memory                               | 4M                                                                                         |                                                                  |
| LoRa® and Positioning (Semtech LR1110)              |                                                                                            |                                                                  |
| LoRaWAN® Protocol                                   | V1.0.4                                                                                     |                                                                  |
| Frequency Plan                                      | 863\~928MHz                                                                                |                                                                  |
| Sensitivity                                         | <p>-125dBm @125K/SF7</p><p>-141dBm @125K/SF12</p>                                          |                                                                  |
| Output Power                                        | 20dBm max @LoRa®                                                                           |                                                                  |
| Positioning Technology                              | GNSS(GPS/BeiDou), WiFi Sniffer                                                             |                                                                  |
| Range                                               | 2\~10km (Depends on antenna and environment)                                               |                                                                  |
| Bluetooth(Nordic nRF52840)                          |                                                                                            |                                                                  |
| Bluetooth                                           | Bluetooth 5.3                                                                              |                                                                  |
| Flash                                               | 1MB                                                                                        |                                                                  |
| RAM                                                 | 256KB                                                                                      |                                                                  |
| Protocol                                            | Bluetooth LE, Bluetooth mesh, Thread, Zigbee, 802.15.4, ANT and 2.4 GHz proprietary stacks |                                                                  |
| Output Power                                        | 6dBm max @Bluetooth                                                                        |                                                                  |
| Onboard Sensors -- TH Sensor (SHT41)                |                                                                                            |                                                                  |
|                                                     | Range                                                                                      | Accuracy                                                         |
| Temperature                                         | -40\~85°C                                                                                  | ± 0.2°C                                                          |
| Humidity                                            | 0\~100%RH                                                                                  | ±1.8%RH                                                          |
| Onboard Sensors -- 3-Axis Accelerometer( Not used ) |                                                                                            |                                                                  |
| Range                                               | ±2g, 4g, 8g, 16g                                                                           |                                                                  |
| Bandwidth                                           | 0\\.5Hz \~ 625Hz                                                                           |                                                                  |
| Sensitivity (LSB/g)                                 | 1000 (±2g) \~ 83 (±16g)                                                                    |                                                                  |

**Grove - OLED Display 0.96 inch**

| **Power Voltage (VCC)**                 | 3.3 / 5 V              |
| --------------------------------------- | ---------------------- |
| **Driver IC**                           | SSD1308Z               |
| **Display Color**                       | White                  |
| **Dot Matrix**                          | 128×64                 |
| **Panel Size**                          | 26.7(W)×19.26(H) mm    |
| **Active Area**                         | 21.74(W)×11.175 (H) mm |
| **Dot Pitch**                           | 0.17(W)×0.175 (H) mm   |
| **Dot Size**                            | 0.15(W)×0.15 (H) mm    |
| **Wide range of operating temperature** | -20\~70 ℃              |

### Get Started

#### Hardware Connection

Connect the `Grove-GPS module` to the `UART` port, and the `Grove-OLED Display` to the `I2C` port.

<figure><img src="../../.gitbook/assets/image (1030).png" alt=""><figcaption></figcaption></figure>

### Configuration

**Device Connection**[**​**](https://wiki.seeedstudio.com/meshtastic_kit_wio_tracker_1110/#device-connection)

Different connection types, find out which client is best for your type of connection.

{% tabs %}
{% tab title="IOS App" %}


* Download the `Meshtastic` App.<br>
* Select the target device on the Bluetooth panel.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/connect-radio.png" alt="" width="300">

* The display will show the name and PIN code

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/pin-code.png" alt="" width="400">

* Enter the code and then click `Pair` to connect the device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/pair1.png" alt="" width="600">
{% endtab %}

{% tab title="Android App" %}


* Download the `Meshtastic` App.<br>
* Click `+` and choose the target device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/an-choose.png" alt="" width="600">

* The display will show the name and PIN code

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/pin-code.png" alt="" width="400">

* Enter the code and then click `OK` to connect the device.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/click-ok.png" alt="" width="300">
{% endtab %}

{% tab title="Web Client" %}
Open [Web Client](https://client.meshtastic.org/), click `New Connection`.

<figure><img src="../../.gitbook/assets/image (1031).png" alt=""><figcaption></figcaption></figure>

*   **Connect via Bluetooth**

    Enable the Bluetooth of your PC, and select the `Bluetooth` tab to connect a new device.

    <img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/ble-new.png" alt="" width="600">

    Select the device and enter the PIN code on the display to connect the device.

<figure><img src="../../.gitbook/assets/image (1032).png" alt=""><figcaption></figcaption></figure>

* **Connect via Serial**

Connect the board to your PC and select the `Serial` tab to connect a new device.

<figure><img src="../../.gitbook/assets/image (1033).png" alt=""><figcaption></figcaption></figure>

You can check the port via:

```
ls /dev/cu.*
```

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/usb-port.png" alt="" width="600">

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/web-serial-connect.png" alt="" width="600">
{% endtab %}

{% tab title="CLI" %}
This library provides a command-line interface (CLI) for managing the user settings of Meshtastic nodes and provides an easy API for sending and receiving messages over mesh radios.
{% endtab %}
{% endtabs %}

**Parameters Configuration**[**​**](https://wiki.seeedstudio.com/meshtastic_kit_wio_tracker_1110/#parameters-configuration)

In order to start communicating over the mesh, you must set your region. This setting controls which frequency range your device uses and should be set according to your regional location.

{% tabs %}
{% tab title="IOS App" %}
<figure><img src="../../.gitbook/assets/image (1034).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Android App" %}
<figure><img src="../../.gitbook/assets/image (1037).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Web Client" %}
<figure><img src="../../.gitbook/assets/image (1036).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="CLI" %}
un the following command, replacing `REGION-CODE` with the region code listed above according to your regional location.

```
meshtastic --set lora.region <REGION-CODE>
```

For example:

<figure><img src="../../.gitbook/assets/image (1038).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

**Region List**

Refer to [LoRa Region by Country](https://meshtastic.org/docs/configuration/region-by-country/) for a more comprehensive list.

| **Region Code** |     **Description**     | **Frequency Range (MHz)** | **Duty Cycle (%)** | **Power Limit (dBm)** |
| :-------------: | :---------------------: | :-----------------------: | :----------------: | :-------------------: |
|      UNSET      |          Unset          |            N/A            |         N/A        |          N/A          |
|        US       |      United States      |       902.0 - 928.0       |         100        |           30          |
|     EU\_433     |  European Union 433MHz  |       433.0 - 434.0       |         10         |           12          |
|     EU\_868     |  European Union 868MHz  |       869.4 - 869.65      |         10         |           27          |
|        CN       |          China          |       470.0 - 510.0       |         100        |           19          |
|        JP       |          Japan          |       920.8 - 927.8       |         100        |           16          |
|       ANZ       | Australia & New Zealand |       915.0 - 928.0       |         100        |           30          |
|        KR       |          Korea          |       920.0 - 923.0       |         100        |                       |
|        TW       |          Taiwan         |       920.0 - 925.0       |         100        |           27          |
|        RU       |          Russia         |       868.7 - 869.2       |         100        |           20          |
|        IN       |          India          |       865.0 - 867.0       |         100        |           30          |
|     NZ\_865     |    New Zealand 865MHz   |       864.0 - 868.0       |         100        |           36          |
|        TH       |         Thailand        |       920.0 - 925.0       |         100        |           16          |
|     UA\_433     |      Ukraine 433MHz     |       433.0 - 434.7       |         10         |           10          |
|     UA\_868     |      Ukraine 868MHz     |       868.0 - 868.6       |          1         |           14          |
|     MY\_433     |     Malaysia 433MHz     |       433.0 - 435.0       |         100        |           20          |
|     MY\_919     |     Malaysia 919MHz     |       919.0 - 924.0       |         100        |           27          |
|     SG\_923     |     Singapore 923MHz    |       917.0 - 925.0       |         100        |           20          |
|     LORA\_24    |  2.4 GHz band worldwide |      2400.0 - 2483.5      |         100        |           10          |

{% hint style="warning" %}
info

**EU\_433** and **EU\_868** have to adhere to an hourly duty cycle limitation of 10%, calculated every minute on a rolling 1-hour basis. Your device will stop transmitting if you reach it, until it is allowed again.
{% endhint %}

Now that you have set the LoRa region on your device, you can continue with configuring any [additional configs](https://meshtastic.org/docs/configuration/) to suit your needs.

### Resource[​](https://wiki.seeedstudio.com/meshtastic_kit_wio_tracker_1110/#resource) <a href="#resource" id="resource"></a>

[Wio Tracker 1110 Dev Board v1.0\_SCH](https://files.seeedstudio.com/products/SenseCAP/Wio-Tracker/Wio%20Tracker%201110%20v1.0_SCH_PDF_20230822.pdf)

[Meshtastic Doc](https://meshtastic.org/docs/introduction/)

[Github-Meshtastic Firmware](https://github.com/meshtastic/firmware/blob/master/boards/wio-tracker-wm1110.json)

[Enclosure File(3D-Print)](https://files.seeedstudio.com/products/E24070201/wio%20tracker%20723.stp)

[Enclosure File(Acrylic)](https://files.seeedstudio.com/products/114993370/%E4%BA%9A%E5%85%8B%E5%8A%9B%E5%A4%96%E5%A3%B3%E5%9B%BE%E7%BA%B8.zip)
