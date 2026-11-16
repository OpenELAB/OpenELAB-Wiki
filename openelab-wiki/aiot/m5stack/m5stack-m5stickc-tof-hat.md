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

# M5Stack M5StickC ToF HAT

### M5Stack M5StickC ToF HAT

***

### Product Link

{% embed url="https://openelab.io/products/m5stickc-tof-hat" %}

### Description <a href="#description" id="description"></a>

**ToF HAT** is a high precision laser-ranging sensor specifically designed for M5StickC. Integrated with **VL53L0X** and **940nm VCSEL** emitter. It can provide high precision and low latency performance on object distance detection. The VL53L0X is a new generation Time-of-Flight (ToF) laser-ranging module housed in the smallest package on the market today, providing accurate distance measurement whatever the target reflectances, unlike conventional technologies. It can measure absolute distances up to 2m, setting a new benchmark in ranging performance levels, opening the door to various new applications. The VL53L0X integrates a leading-edge SPAD array (Single Photon Avalanche Diodes) and embeds ST’s second generation FlightSenseTM patented technology. The VL53L0X’s 940 nm VCSEL emitter (Vertical-Cavity Surface-Emitting Laser), is invisible to the human eye, coupled with internal physical infrared filters, it enables longer ranging distances, higher immunity to ambient light, and better robustness to cover glass optical crosstalk.

Communication Info: I2C, **0x29**, GPIO0/26.

### Features <a href="#product-features" id="product-features"></a>

* High precision
* Maximum measuring distance 2m
* Measurement accuracy ±3%
* 940nm laser VCSEL
* Development platform: Arduino, UIFlow(Blockly, Python)
* Security:      - Class 1 laser equipment meeting the latest standards      - Standard IEC 60825-1: 2014 - 3rd edition

### Applications <a href="#applications" id="applications"></a>

* Obstacle recognition
* Gesture Recognition
* Laser Ranging
* 3D structured light imaging (3D sensing)
* Camera assist (super fast auto focus and depth of field map)

### Specification <a href="#specification" id="specification"></a>

| Resources              | Parameter        |
| ---------------------- | ---------------- |
| Communication protocol | I2C:0x29         |
| Measuring distance     | 0.3-2m           |
| Measurement accuracy   | ±3%              |
| Net weight             | 4g               |
| Gross weight           | 8g               |
| Product Size           | 24\*20.3\*13.8mm |
| Package Size           | 136\*92\*15mm    |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-tof/hat-tof_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-tof/hat-tof_06.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/EasyLoader_M5StickC_logo.webp" alt=""><figcaption></figcaption></figure>

[download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/HAT/ToF/EasyLoader_ToF_HAT.exe)

What is EasyLoader?1.EasyLoader is a simple and fast program burner. Every product page in EasyLoader provides a product-related case program. It can be burned to the master through simple steps, and a series of function verification can be performed.

2. After downloading the software, double-click to run the application, connect the M5 device to the computer through the data cable, select the port parameters, click **"Burn"** to start burning. (**For M5StickC burning, please Set the baud rate to 750000 or 115200**)

#### Pinout <a href="#pin-map" id="pin-map"></a>

| M5StickC | GPIO0 | GPIO26 | 3.3V | GND |
| -------- | ----- | ------ | ---- | --- |
| ToF HAT  | SDA   | SCL    | 3.3V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-tof/hat-tof_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* [**VL53L0X Datasheet**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/VL53L0X_en.pdf)

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/1294638/_ccbGm2BrAs.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[M5StickC Laser Rangefinder](https://www.hackster.io/framework-labs/m5stickc-laser-rangefinder-86d0f0)[M5StickC Laser Rangefinder](https://www.hackster.io/framework-labs/m5stickc-laser-rangefinder-86d0f0)Turns your M5StickC with the ToF HAT into a laser rangefinder.

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Click here to download the Arduino example](https://github.com/m5stack/M5StickC/tree/master/examples/Hat/TOF)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Hat/hat-yun/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-tof/hat-tof_uiflow_01.webp" alt=""><figcaption></figcaption></figure>
