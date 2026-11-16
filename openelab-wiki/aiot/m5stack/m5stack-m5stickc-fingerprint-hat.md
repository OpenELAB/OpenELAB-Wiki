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

# M5Stack M5StickC Fingerprint HAT

### M5Stack M5StickC Fingerprint HAT

***

### Product Link

{% embed url="https://openelab.io/products/m5stickc-fingerprint-hat" %}

### Description <a href="#description" id="description"></a>

**FINGER Hat** comes with "FPC1020SC" fingerprint sensor inside. This all-in-one fingerprint sensor makes adding, verification and management of fingerprints super easy. Compact size, serial protocol and 'ultra-low power consumption'- all make this M5 Unit very attractive to be used along with the M5StickC. It performs fast fingerprint matching with the highest security level at the most optimal user convenience. The M5 Unit can be programmed to set customized fingerprint recognition comparison levels and security levels. if you ever consider to make your project more secure with biometrics, don’t forget to include this M5 Unit: "FINGER HAT".

UART settings:

* Baudrate: 19200bps(default)
* 1 Start bit
* 1 Stop bit
* No parity

### Features <a href="#product-features" id="product-features"></a>

* Fingerprint: 150
* Capacitive area array semiconductor fingerprint sensor
* The sensor has a pixel quality of 256 gray levels per pixel
* 1:N recognition and 1:1 verification
* Support finger 360 Rotate recognition
* Security level that can be adjusted appropriately 0-9, default level 5
* Output format: User name、finger image、feature value
* Characteristic value size: 193 Bytes
* Communication Interface: UART
* Supported Baudrate: 9600bps-115200bps（Default:19200bps）
* Operating temperature: -10°C - 60°C
* Operating humidity: 20% - 80%

### Applications <a href="#applications" id="applications"></a>

* Fingerprint Attendance Machine
* Passwordless authentication
* User identification

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter    |
| ------------ | ------------ |
| Net weight   | 14g          |
| Gross weight | 26g          |
| Product Size | 24\*65\*20mm |
| Package Size | 75\*46\*29mm |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-finger/hat-finger_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-finger/hat-finger_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-finger/hat-finger_06.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/EasyLoader_M5StickC_logo.webp" alt=""><figcaption></figcaption></figure>

[download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/HAT/EasyLoader_Finger_HAT.exe)

EasyLoader is a simple and fast program burner. Every product page in EasyLoader provides a product-related case program. It can be burned to the M5 device through simple steps, and a series of function verification can be performed.

2. After downloading the software, double-click to run the application, connect the M5 device to the computer through the data cable, select the port parameters, click **"Burn"** to burn the program (**For M5StickC, set the baud rate to 750000 or 115200**)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-finger/hat-finger_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* Protocol [**FINGER series communication protocol**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/biovo_fingerprint_Protocol.pdf)
* Datasheet [**FPC1020A**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/1020A_datasheet_cn.pdf)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Hat-Finger with M5StickC](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Hat_Finger_M5StickC/Hat_Finger_M5StickC.ino)
* [M5Hat-Finger with M5StickCPlus](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Hat_Finger_M5StickCPlus/Hat_Finger_M5StickCPlus.ino)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

Open [http://flow.m5stack.com ](http://flow.m5stack.com/)and Load Demo

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-finger/hat-finger_uiflow_01.webp" alt=""><figcaption></figcaption></figure>
