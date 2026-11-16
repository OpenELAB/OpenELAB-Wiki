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

# T-ECHO BME280 Meshtastic LoRa SX1262 Wireless Module

### LILYGO T-ECHO BME280 Meshtastic LoRa SX1262 Wireless Module 433/868/915MHz nRF52840

***

### Product Link

{% embed url="https://openelab.io/products/lilygo-t-echo-bme280-meshtastic-lora" %}

### Description

<figure><img src="../../.gitbook/assets/image (314).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (316).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (317).png" alt=""><figcaption></figcaption></figure>

### Specification

| MCU                     | NRF52840                                                                                                                |
| ----------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| FLASH                   | 2MB                                                                                                                     |
| RAM                     | 2MB                                                                                                                     |
| Bus Interfaces          | UART, SPI, TWI, PDM, 12S, QSPI                                                                                          |
| Wireless Connectivity   | <p>Bluetooth 5, Thread,<br>Bluetooth Mesh, ANT, 802.15.4, Zigbee<br>With/Without BME280 temperature pressure sensor</p> |
| SX1262 LoRa Transceiver | <p> Long Range, Low Power<br>Global frequency coverage 433, 868, 915Mhz</p>                                             |
| Enclosure material      | ABS                                                                                                                     |
| Version                 | Normal version / BME280 version                                                                                         |
| Battry Capacity         | 850mAh                                                                                                                  |

**1.54-inch SPI E-Paper Display**

| Grey level         | 2       |
| ------------------ | ------- |
| Resolution         | 200x200 |
|  Full refresh time | 2S      |

**L76K Multi-System Positioning GNSS module**

| Support System   | GPS, GLONASS, BeiDou, QZSS                                                                  |
| ---------------- | ------------------------------------------------------------------------------------------- |
| Support Function | <p> LNA, SAW Filter, AGNSS, 1PPS<br>Improved receiving and anti-interference attributes</p> |

### Using Arduino IDE

1. Download [Arduino IDE](https://www.arduino.cc/en/software)
2. Open Arduino, open preferences-> add [https://adafruit.github.io/arduino-board-index/package\_adafruit\_index.json](https://adafruit.github.io/arduino-board-index/package_adafruit_index.json) to the board installation manager address list
3. Open the board installation manager, wait for the index update to complete, select 'Adafruit nRF52 by Adafruit' and click install
4. After the installation is complete, select 'Nordic nRF52840(PCA10056)' or 'Nordic nRF52840 DK' in the board list
5. Copy all the folders in the lib directory to `"C:\User\<YourName>\Documents\Arduino\libraries"`
6. Open the sketch => tool => port, select the port of the connected board, and click upload

### Using PlatformIO

1. Install [VSCODE](https://code.visualstudio.com/) and [Python](https://www.python.org/)
2. Search for the PlatformIO plug-in in the VSCODE extension and install it.
3. After the installation is complete and the reload is completed, there will be a small house icon in the lower left corner. Click to display the Platformio IDE home page
4. Go to file - > Open folder - > Select the LilyGO-T-ECHO folder and click the (√) symbol in the lower left corner to compile (→) for upload.
5. If you use USB to download the firmware (platformio.ini upload\_protocol = nrfutil), you need to double-click reset button to enter DFU mode before downloading

### Pin map

<figure><img src="../../.gitbook/assets/image (318).png" alt=""><figcaption></figcaption></figure>

### Antenna Actual Test Reference

<figure><img src="../../.gitbook/assets/image (321).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (322).png" alt=""><figcaption></figcaption></figure>

### Application

* [T-Echo SoftRF  T-Echo](https://github.com/lyusupov/SoftRF/wiki/Badge-Edition)
* [T-Echo Meshtastic  T-Echo](https://github.com/meshtastic/Meshtastic-device/releases)

### Precautions

1. Need to use the files in the **lib** directory, it includes:
   * [`arduino-lmic`](https://github.com/mcci-catena/arduino-lmic)
   * [`AceButton`](https://github.com/bxparks/AceButton)
   * [`Adafruit_BME280_Library`](https://github.com/adafruit/Adafruit_BME280_Library)
   * [`Adafruit_BusIO`](https://github.com/adafruit/Adafruit_BusIO)
   * [`Adafruit_EPD`](https://github.com/adafruit/Adafruit_EPD)
   * [`Adafruit-GFX-Library`](https://github.com/adafruit/Adafruit-GFX-Library)
   * [`Button2`](https://github.com/LennartHennigs/Button2.git)
   * [`GxEPD`](https://github.com/ZinggJM/GxEPD.git)
   * [`PCF8563_Library`](https://github.com/lewisxhe/PCF8563_Library.git)
   * [`RadioLib`](https://github.com/jgromes/RadioLib)
   * [`SerialFlash`](https://github.com/PaulStoffregen/SerialFlash)
   * [`SoftSPI`](https://github.com/MajenkoLibraries/SoftSPI.git)
   * [`TinyGPSPlus`](https://github.com/mikalhart/TinyGPSPlus.git)
2. Pins on boards are not compatible with the official SDK.If you want to use the SDK, pay special attention to the pin definition.
3. Use [Adafruit\_nRF52\_Arduino](https://github.com/adafruit/Adafruit_nRF52_Arduino) by default, so [Adafruit\_nRF52\_Bootloader](https://github.com/adafruit/Adafruit_nRF52_Bootloader) has been burned in the factory, if you use **nRF5-SDK** Programming the board will lose the original bootloader
4. If you need to use **nRF5-SDK** for programming, please click the link to download [**nRF5-SDK**](https://www.nordicsemi.com/Software-and-Tools/Software/nRF5-SDK/Download)
5. **NFC Function** is not supported in **Adafruit\_nRF52\_Arduino**, please use [**nRF5-SDK**](https://www.nordicsemi.com/Software-and-Tools/Software/nRF5-SDK/Download) for programming
6. Flash will choose MX25R1635FZUIL0 or ZD25WQ16B according to the availability.Pay attention to the difference when using.
7. If you need to burn a new bootloader, see [Burning a new bootloader](https://github.com/Xinyuan-LilyGO/T-Echo/blob/main/bootloader/README.MD)

### Battery life

Current consumption from 3.7 Volt battery:

|         Mode         | Average current |
| :------------------: | :-------------: |
| Active backlight OFF |      42 mA      |
|  Active backlight ON |      55 mA      |
|         Sleep        |     0.25 mA     |

Operating time from a full charge depends on your actual battery capacity.

The below figure represents a more specific test, and you can use the example [Sleep\_Display](https://github.com/Xinyuan-LilyGO/T-Echo/blob/main/examples/Sleep_Display) to write your low-power device program.

<figure><img src="https://github.com/Xinyuan-LilyGO/T-Echo/raw/main/image/T-Echo_V1.0_PowerConsumptionTest_BLU939_1.png" alt=""><figcaption></figcaption></figure>

### Github:

[T-Echo](https://github.com/Xinyuan-LilyGO/T-Echo)
