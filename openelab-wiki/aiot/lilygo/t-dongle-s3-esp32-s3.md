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

# T-Dongle S3 ESP32-S3

LILYGO T-Dongle S3 ESP32-S3 Development Board

***

### Product Link

{% embed url="https://openelab.io/products/t-dongle-s3?_pos=1&_psq=LILYGO-K193" %}

### Description

An ESP32S3 development board that can freely use WIFI, BLE, TF, LED, TFT\_LCD functions.

<figure><img src="../../.gitbook/assets/image (330).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (328).png" alt=""><figcaption></figcaption></figure>

### Specifications

{% hint style="warning" %}
**Note**: With TF Card, but TF card has no function.
{% endhint %}

| MCU                   |  ESP32-S3 Xtensa LX7 microprocessor    |
| --------------------- | -------------------------------------- |
| Wireless Connectivity | Wi-Fi 802.11 b/g/n, bluetooth5         |
| Platform              | Arduino-ide、PlatformlO-ide、Micropython |
| Onboard functions     | 16M Flash, Boot button, TF card        |

|  **0.96 inch ST7735 IPS LCD** |
| ----------------------------- |

|  Full color (65k) Display, 4-Wire SPI interface |
| ----------------------------------------------- |

| Resolution           |  80 X 160, 0.96 diagonal |
| -------------------- | ------------------------ |
| Model                | ST7735 LCD               |
| Working Power Supply | 3.3V                     |

### Get Start

#### Arduino

In Arduino Preferences, on the Settings tab, enter the `https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json` URL in the `Additional boards manager URLs` input box. **Please pay attention to the version. The test phase is using 2.0.14. It is not certain that versions above 2.0.14 can run. When the operation is abnormal, please downgrade to a version below 2.0.14.** , As of 2024/08/02, TFT\_eSPI does not work on versions higher than 2.0.14, see [TFT\_eSPI/issue3329](https://github.com/Bodmer/TFT_eSPI/issues/3329)

<figure><img src="../../.gitbook/assets/image (331).png" alt=""><figcaption></figcaption></figure>

* Copy all files in the lib folder to `\Arduino\libraries`
* Select the settings as shown. Note that the FLASH size partition and size may be modified depending on the board.

<figure><img src="../../.gitbook/assets/image (332).png" alt=""><figcaption></figcaption></figure>

#### PlatfromIO

* PlatformIO plug-in installation: Click on the extension on the left column -> search platformIO -> install the first plug-in
* Click Platforms -> Embedded -> search Espressif 32 in the input box -> select the corresponding firmware installation

#### ESP-IDF

* The installation method is also inconsistent depending on the system, it is recommended to refer to the [official manual](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html) for installation

#### Micropython

* tft\_config.py is already built into the firmware. The examples in the examples directory can be used directly.
* For detailed function query, please refer to the following link.
* \[[Micropython doc](https://docs.micropython.org/en/latest/index.html)]

{% hint style="warning" %}
The program can be written normally, but there is still no display after writing

* There are factory test files in the firmware folder, which can be flashed into the board to check whether the board is normal. if there is still no display, then it can be judged that there is a problem with the board or the screen
* Delete the \<TFT\_eSPI> in the libraries, and replace the \<TFT\_eSPI> in the folder of the main page to the libraries directory
* When opening the Arduino IDE, it prompts whether to upgrade the library, place choose not to upgrade, otherwise it will overwrite the configuration of the \<TFT\_eSPI> display
{% endhint %}

### FAQ

1. The program can be written normally, but there is still no display after writing
   1. There are factory test files in the firmware folder, which can be flashed into the board to check whether the board is normal. If there is still no display, then it can be judged that there is a problem with the board or the screen
   2. Delete the \<TFT\_eSPI> in the libraries, and replace the \<TFT\_eSPI> in the folder of the main page to the libraries directory
   3. When opening the Arduino IDE, it prompts whether to upgrade the library, please choose not to upgrade, otherwise it will overwrite the configuration of the \<TFT\_eSPI> display
2. The board uses USB as the JTAG upload port. When printing serial port information on USB\_CDC\_ON\_BOOT configuration needs to be turned on. If the port cannot be found when uploading the program or the USB has been used for other functions, the port does not appear. Please enter the upload mode manually.
   1. Press and hold the BOOT button , While still pressing the BOOT button, Insert USB
   2. Release the BOOT button
   3. Upload sketch
3. If the above is invalid, burn the [binary file](https://github.com/Xinyuan-LilyGO/T-Dongle-S3/blob/main/firmware/README.MD) to check whether the hardware is normal
