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

# M5Stack Mini GPS/BDS

### M5Stack Mini GPS/BDS Unit (AT6558)

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**GPS** is an M5Stack Unit that integrates a **AT6558** navigation chip and a **MAX2659** amplification chip which is used for amplifying the antenna signal.

**AT6558** is an high performance chip that supports many types of satellite navigation systems, able to receive satellite signals on 56 channels GNSS signal from 6 satellite navigation system, joint location, navigation, timing and more.

The module is able to obtain accurate global location information, quick and accurate positioning for anywhere in the city, in the canyon, under the overhead and inside the car.

The module can be widely used in vehicle monitoring, bus reporting, car navigation, onboard navigation, notebook navigation and other products.

You can plug it into port C on M5core via GROVE cable, which is a standard UART interface.

UART settings :

* Baudrate(**default: 9600bps**)
* Start bits(1 bit)
* Stop bits(1 bit)
* Parity(no)

### Features <a href="#features" id="features"></a>

* Support single system positioning of BDS/GPS satellite navigation systems, or multi-system joint positioning in any combination
* Support D-GNSS differential positioning
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* Vehicle positioning and navigation
* Smart law enforcement positioning

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                    | Parameter                                                         |
| ---------------------------- | ----------------------------------------------------------------- |
| Positioning accuracy         | 2.5m                                                              |
| Channel                      | 56                                                                |
| Positioning update frequency | 1-10Hz                                                            |
| Maximum speed                | 515m/s                                                            |
| Maximum acceleration         | <= 4g                                                             |
| Sensitivity                  | Tracking: -162dBm,Capture: -148dBm,Cold start: -146dBm            |
| Start Time                   | Cold start: 35 seconds,Warm start: 32 seconds,Hot start: 1 second |
| Operating temperature        | -40°C - 85°C                                                      |
| Net weight                   | 13g                                                               |
| Gross weight                 | 26g                                                               |
| Product Size                 | 48\*24\*8mm                                                       |
| Package Size                 | 136 \* 92 \* 13mm                                                 |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE C) | U2RXD(GPIO16)           | U2TXD(GPIO17)        | 5V | GND |
| --------------- | ----------------------- | -------------------- | -- | --- |
| GPS Unit        | Signal Transmitter(TXD) | Signal Receiver(RXD) | 5V | GND |

| M5Core2(PORT C) | U2RXD(GPIO13)            | U2TXD(GPIO14)         | 5V | GND |
| --------------- | ------------------------ | --------------------- | -- | --- |
| GPS Unit        | Signal Transmitter (TXD) | Signal Receiver (RXD) | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Datasheetss <a href="#datasheetss" id="datasheetss"></a>

* [AT6558 ](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/AT6558_en.pdf)- [MAX2659](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/MAX2659_en.pdf)
* [**TinyGPS++ library**](http://arduiniana.org/libraries/tinygpsplus/)

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/gps/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (971).png" alt=""><figcaption></figcaption></figure>
