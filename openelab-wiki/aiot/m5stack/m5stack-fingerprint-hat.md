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

# M5Stack Fingerprint HAT

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack M5StickC Fingerprint HAT

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**FINGER Hat** comes with "FPC1020SC" fingerprint sensor inside. This all-in-one fingerprint sensor makes adding, verification and management of fingerprints super easy. Compact size, serial protocol and 'ultra-low power consumption'- all make this M5 Unit very attractive to be used along with the M5StickC. It performs fast fingerprint matching with the highest security level at the most optimal user convenience. The M5 Unit can be programmed to set customized fingerprint recognition comparison levels and security levels. if you ever consider to make your project more secure with biometrics, don’t forget to include this M5 Unit: "FINGER HAT".

UART settings:

* Baudrate: 19200bps(default)
* 1 Start bit
* 1 Stop bit
* No parity

### Features <a href="#features" id="features"></a>

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

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter    |
| ------------ | ------------ |
| Net weight   | 14g          |
| Gross weight | 26g          |
| Product Size | 24\*65\*20mm |
| Package Size | 75\*46\*29mm |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-finger/hat-finger_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat Finger](https://docs.m5stack.com/en/hat/Hat_Finger) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U074`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                              | Model-specific reference                                                                                                                                              |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Example source: Hat\_Finger\_M5StickC.ino     | [Read example source: hat\_finger\_m5stickc.ino](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Hat_Finger_M5StickC/Hat_Finger_M5StickC.ino)             |
| Example source: Hat\_Finger\_M5StickCPlus.ino | [Read example source: hat\_finger\_m5stickcplus.ino](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Hat_Finger_M5StickCPlus/Hat_Finger_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
