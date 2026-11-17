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

# M5Stack DAC

### M5Stack DAC Converter Digital to Analog I2C Unit

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**DAC**, is a unit with the ability to convert digital signal to analog signal (voltage waveform signal) with support for audio waveform and more. It integrates a 12-bit high resolution DAC chip named **MCP4725** which has an on-board non-volatile memory (EEPROM). The unit communicates with the M5Core using the I2C protocol.

The DAC input and configuration data can be programmed to the EEPROM in order for the data to be saved after reboot or system shutdown.

The device I2C address is 0x60 by default unless changed manually.

### Features <a href="#product-features" id="product-features"></a>

* Up to 12 bits of resolution
* Output 0\~3.3V voltage GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* MP3 Audio Player
* mini Oscilloscope

### Specification <a href="#specification" id="specification"></a>

| Resources              | Parameter          |
| ---------------------- | ------------------ |
| Resolution             | 12 bit             |
| voltage range          | 0-3.3V             |
| Communication protocol | I2C: 0x60          |
| Net weight             | 4g                 |
| Gross weight           | 19g                |
| Product Size           | 32.2\*24.2\*10.3mm |
| Package Size           | 67\*53\*12mm       |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/dac/dac_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/dac/dac_06.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE A) | GPIO22 | GPIO21 | 5V | GND |
| --------------- | ------ | ------ | -- | --- |
| DAC Unit        | SCL    | SDA    | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/dac/dac_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/dac/MODULE%20SIZE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (938).png" alt=""><figcaption></figcaption></figure>
