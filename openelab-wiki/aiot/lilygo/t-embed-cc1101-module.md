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

# T-Embed CC1101 Module

### LILYGO T-Embed CC1101 Module Bruce Launcher CapibaraZero

***

### Product Link

{% embed url="https://openelab.io/products/lilygo-t-embed-cc1101" %}

<figure><img src="../../.gitbook/assets/image (1008).png" alt=""><figcaption></figcaption></figure>

Video about T-Embed-CC1101:

{% embed url="https://www.youtube.com/watch?v=U06XI1wtp4U" %}

|      Product     | [T-Embed-CC1101](https://openelab.io/products/lilygo-t-embed-cc1101) |
| :--------------: | :------------------------------------------------------------------: |
|        MCU       |                           ESP32-S3-WROOM-1                           |
|   Flash / PSRAM  |                               16M / 8M                               |
|       Sub-G      |                                CC1101                                |
|        NFC       |                             PN532 (0x24)                             |
|    Display IC    |                           ST7789 (320x170)                           |
| Battery Capacity |                             3.7V-1300mAh                             |
|   Battery Chip   |                    BQ25896 (0x6B), BQ27220 (0x55)                    |
|    LED Driver    |                                WS2812                                |

Some interesting projects that support T-Embed-CC1101：

|     name     |                             code                            |                                     web                                    |
| :----------: | :---------------------------------------------------------: | :------------------------------------------------------------------------: |
|     Bruce    |     [github](https://github.com/pr3y/Bruce/tree/WebPage)    |                 [web](https://bruce.computer/flasher.html)                 |
|   Launcher   | [github](https://github.com/bmorcelli/M5Stick-Launcher.git) |         [web](https://bmorcelli.github.io/Launcher/webflasher.html)        |
| CapibaraZero |       [github](https://github.com/CapibaraZero/fw.git)      | [web](https://capibarazero.com/docs/esp32_s3/boards/LilyGo_T_Embed_CC1101) |

### Module

Datasheets on the chip are available in [./hardware](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware) directory.

|   Name   |                                      Dependency library                                     |
| :------: | :-----------------------------------------------------------------------------------------: |
|  CC1101  |                [jgromes/RadioLib@6.5.0](https://github.com/jgromes/RadioLib)                |
|   PN532  |    [https://github.com/Seeed-Studio/PN532.git](https://github.com/Seeed-Studio/PN532.git)   |
|  BQ25896 |             [lewisxhe/XPowersLib@^0.2.3](https://github.com/lewisxhe/XPowersLib)            |
|  ST7789  |                [bodmer/TFT\_eSPI@^2.5.43](https://github.com/Bodmer/TFT_eSPI)               |
|  Encode  | [mathertel/RotaryEncoder@^1.5.3](http://www.mathertel.de/Arduino/RotaryEncoderLibrary.aspx) |
|  WS2812  |                [fastled/FastLED@^3.9.12](https://github.com/FastLED/FastLED)                |
| Infrared |    [crankyoldgit/IRremoteESP8266@^2.8.6](https://github.com/crankyoldgit/IRremoteESP8266)   |
|   Audio  |        [esphome/ESP32-audioI2S@2.0.0](https://github.com/schreibfaul1/ESP32-audioI2S)       |
|   LVGL   |                [lvgl/lvgl@^8.3.11](https://github.com/lvgl/lvgl/tree/v8.3.11)               |

### Wireless transceiver

T-Embed-CC1101 has a built-in Sub-GHz module based on a `CC1101` transceiver and a radio antenna (the maximum range is 50 meters). Both the CC1101 chip and the antenna are designed to operate at frequencies in the 300-348 MHz, 387-464 MHz, and 779-928 MHz bands.

The Sub-GHz application supports external radio modules based on the CC1101 transceiver.

### PN532

The PN532 only supports high-frequency cards at 13.56MHz, does not support low-frequency cards at 125K, does not support CPU cards, and does not support encryption cards.

"✅" represents a card of support.

|       **Type**       |       **Encryption Method**       | **Anti-Copy Capability** |                               **Attack Risk**                               |                              Typical uses                              |
| :------------------: | :-------------------------------: | :----------------------: | :-------------------------------------------------------------------------: | :--------------------------------------------------------------------: |
| **Mifare Classic** ✅ | Weak (CRYPTO1 algorithm, cracked) |            Low           |                  Easily cloned (e.g., via Proxmark3 tools)                  |     Access control cards, public transportation cards (old system)     |
|      **NTAG** ✅      |    No encryption (UID lockable)   |         Very Low         |                         Data can be arbitrarily read                        | Smart labels, advertising interaction, and product anti-counterfeiting |
|    **Mifare Plus**   |         AES-128 encryption        |        Medium-High       |                      Requires physical access to crack                      |                                    -                                   |
|      **Felica**      |  Dynamic encryption (SAM module)  |           High           |                   Hard to crack (Japan-exclusive protocol)                  |            Japanese transportation cards, electronic wallets           |
|      **DESFire**     |        AES/TDES encryption        |         Very High        |          Supports multi-app isolation, resists side-channel attacks         |   High-security access control, campus one-card, electronic passport   |
|     **CPU Card**     | Hardware encryption (SM4/ECC/RSA) |         Very High        | Supports China's national cryptographic standards, financial-grade security |                Bank card, ID card, social security card                |

### Get Start

PlatformIO is recommended because these examples were developed on it.

PlatformIO

1. Install [Visual Studio Code](https://code.visualstudio.com/) and [Python](https://www.python.org/), and clone or download the project;
2. Search for the `PlatformIO` plugin in the `VisualStudioCode` extension and install it;
3. After the installation is complete, you need to restart `VisualStudioCode`
4. After opening this project, PlatformIO will automatically download the required tripartite libraries and dependencies, the first time this process is relatively long, please wait patiently;
5. After all the dependencies are installed, you can open the `platformio.ini` configuration file, uncomment in `example` to select a routine, and then press `ctrl+s` to save the `.ini` configuration file;
6. Click ☑️ under VScode to compile the project, then plug in USB and select COM under VScode;
7. Finally, click the ➡️ button to download the program to Flash;

### FAQ

Unable to detect sd card：

We were able to successfully test SD with SanDisk no larger than 32GB; But some other cards don't, and it's not clear why;

Therefore, when the SD card is not detected, it is recommended to change a SanDisk card not larger than 32G;

[![alt text](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/raw/master/docs/image-sd.png)](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/docs/image-sd.png)

Other questions

|                       Problem                       |                                               Link                                               |
| :-------------------------------------------------: | :----------------------------------------------------------------------------------------------: |
|            How do I enter download mode?            |    [docs](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/docs/download_mode.md)    |
|             How to download the program?            | [dosc](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/docs/flash_download_tool.md) |
|  How do I turn on the device after I shut it down?  |              [Issues #5](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/issues/5)              |
|      How do I configure Wifi with EspTouch?         |              [Issues #4](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/issues/4)              |
|            Why won't the battery charge？            |              [Issues #9](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/issues/9)              |

### Documents

For more information, see the `./hardware` directory.

Schematic : [T-Embed-CC1101](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/T-Embed-CC1101%20V1.0%2024-07-29.pdf)

CC1101 Schematic : [CC1101](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/cc1101-shield.pdf)

CC1101 Pins : [CC1101 Pins](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/hardware/CC1101_pin.png)

3D Files : [T-Embed CC1101.stp](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/master/3D_files/T-Embed%20CC1101.stp)
