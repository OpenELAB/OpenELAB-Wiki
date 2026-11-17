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

# M5Stack DAC Converter Digital

### M5Stack DAC Converter Digital

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

### EasyLoader <a href="#easyloader" id="easyloader"></a>

[download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Unit/EasyLoader_DAC.exe)

What is EasyLoader?1.EasyLoader is a simple and fast program burner. Every product page in EasyLoader provides a product-related case program. It can be burned to the master through simple steps, and a series of function verification can be performed.

2. After downloading the software, double-click to run the application, connect the M5 device to the computer through the data cable, select the port parameters, click **"Burn"** to start burning. (**For M5StickC burning, please Set the baud rate to 750000 or 115200**)

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE A) | GPIO22 | GPIO21 | 5V | GND |
| --------------- | ------ | ------ | -- | --- |
| DAC Unit        | SCL    | SDA    | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/dac/dac_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet** - [MCP4725](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/MCP4725_en.pdf)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

The code below is incomplete (just for reference). To get the complete code, please click [here](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/DAC_MCP4725)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

**Feature Introduction**

Perform DA conversion and output voltage, up to 3.7V

* **output voltage save** Output voltage 0-3.3, and confirm whether to save to EEPROM
* **output voltage with raw data save** Output voltage 0-4096, and confirm whether to save to EEPROM

**Usage**

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/DAC/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/dac/dac_uiflow_01.webp" alt=""><figcaption></figcaption></figure>
