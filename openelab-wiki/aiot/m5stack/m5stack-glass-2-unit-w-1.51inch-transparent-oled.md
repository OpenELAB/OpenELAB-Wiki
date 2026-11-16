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

# M5Stack Glass 2 Unit w/ 1.51inch Transparent OLED

### M5Stack Glass 2 Unit w/ 1.51inch Transparent OLED

***

### Product Link

{% embed url="https://openelab.io/products/glass-2-unit-w" %}

### Introduction

**Glass2 Unit** is a 1.51-inch transparent OLED display unit that adopts the SSD1309 driver solution. It supports the I2C communication interface (default address 0x3C) and has a built-in solder pad that allows changing the communication address to 0x3D. It is suitable for home products and control devices, and can be used for information display, status indicators, or user interfaces, embedded into various home products or control devices to achieve interaction with users.

Glass2 Unit has a glass area of 42x27.16mm, with a display area of 35.5x18mm and a resolution of 128x64 pixels. It features 256-level brightness control, allowing users to see the display content clearly with rich details and sharp images. The excellent brightness and contrast ensure clear and readable display effects in various lighting environments.

Glass2 Unit is compatible with M5Stack's development platform and rich product ecosystem, allowing users to unleash their creativity and develop various applications and functions. Whether it's developing small games, creating personalized information display interfaces, or connecting with other M5Stack devices, the Glass2 Unit provides strong support and endless possibilities.

Compared to Glass Unit, the Glass2 Unit does not include an STM32 MCU. By changing the I2C address through the onboard solder pad, it can only control two Glass2 Units simultaneously. If you need to control multiple Glass Units simultaneously in a project, you will need to connect them using the PaHUB2 Unit. Additionally, by eliminating the intermediate processing step of the STM32 MCU, the Glass2 Unit improves refresh efficiency, enabling faster content updates or response to input signals, as well as providing smoother and more fluid image or animation displays.

<figure><img src="../../.gitbook/assets/image (525).png" alt=""><figcaption></figcaption></figure>

### Features

* 128x64 total pixels
* Display area 35.5 x 18mm
* Glass area 42mm x 27.16mm
* 1-bit color depth
* I2C Addresses: 0x3D
* support for programming platforms：Arduino、UIFlow

### Specifications

<table><thead><tr><th width="232">Resources</th><th>Parameters</th></tr></thead><tbody><tr><td>Screen</td><td>1.51 inch transparent OLED</td></tr><tr><td>resolution</td><td>128*64</td></tr><tr><td>Display color</td><td>blue</td></tr><tr><td>Display area</td><td>35.05*18（mm）</td></tr><tr><td>Panel size</td><td>42.04*27.16*1.25（mm）</td></tr><tr><td>Perspective direction</td><td>Full view</td></tr><tr><td>Operating temperature</td><td>0-40°C</td></tr><tr><td>Logic voltage</td><td>3.3V</td></tr><tr><td>I2C address</td><td>default:0x3C（You can switch the communication address to 0x3D with bonding pad）</td></tr><tr><td>Product Size</td><td>53*42*6mm</td></tr><tr><td>Package Size</td><td>136*92*13mm</td></tr><tr><td>Product Weight</td><td>9.1g</td></tr><tr><td>Package Weight</td><td>13.9g</td></tr></tbody></table>

### Pinout

<figure><img src="../../.gitbook/assets/image (527).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (526).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to a Microcontroller**: Use the I2C interface to connect the Glass 2 Unit to your microcontroller (e.g., Arduino or ESP32).
* **Install Necessary Libraries**: Ensure you have the correct libraries installed in your development environment to communicate with the OLED display.
* **Initialize the Display**: Write initialization code to set up the display.
* **Display Content**: Use provided functions to display text, images, or graphics on the screen.
* **Adjust Brightness and Contrast**: Customize the display settings for optimal visibility in your application.

### FAQ

<details>

<summary><strong>Can I use the M5Stack Glass 2 Unit with any microcontroller?</strong></summary>

Yes, as long as the microcontroller supports I2C communication, you can integrate the Glass 2 Unit.

</details>

<details>

<summary><strong>How do I power the display?</strong></summary>

A: The display operates at 3.3V, so ensure your power supply matches this requirement.

</details>

<details>

<summary><strong>Is the display sunlight readable?</strong></summary>

The transparent OLED display is designed for indoor use. Visibility in direct sunlight may be limited

</details>

<details>

<summary><strong>What libraries are needed to operate the display with Arduino?</strong></summary>

&#x20;You will need the U8g2 library, which supports a wide range of OLED displays, including the M5Stack Glass 2 Unit.

</details>

<details>

<summary><strong>Can I display images on the OLED screen?</strong></summary>

Yes, you can display images by converting them into a format compatible with the screen and using appropriate library functions.

</details>
