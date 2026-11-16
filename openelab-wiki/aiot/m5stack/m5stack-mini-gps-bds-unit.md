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

# M5Stack Mini GPS/BDS Unit

### M5Stack Mini GPS/BDS Unit

***

### Product Link

{% embed url="https://openelab.io/products/mini-gps-bds-unit" %}

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

### Features <a href="#product-features" id="product-features"></a>

* Support single system positioning of BDS/GPS satellite navigation systems, or multi-system joint positioning in any combination
* Support D-GNSS differential positioning
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* Vehicle positioning and navigation
* Smart law enforcement positioning

### Specification <a href="#specification" id="specification"></a>

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_06.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_07.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

[download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Unit/EasyLoader_GPSRaw.exe)

What is EasyLoader?1.EasyLoader is a simple and fast program burner. Every product page in EasyLoader provides a product-related case program. It can be burned to the master through simple steps, and a series of function verification can be performed. .

2. After downloading the software, double-click to run the application, connect the M5 device to the computer through the data cable, select the port parameters, click **"Burn"** to start burning. (**For M5StickC burning, please Set the baud rate to 750000 or 115200**)

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE C) | U2RXD(GPIO16)           | U2TXD(GPIO17)        | 5V | GND |
| --------------- | ----------------------- | -------------------- | -- | --- |
| GPS Unit        | Signal Transmitter(TXD) | Signal Receiver(RXD) | 5V | GND |

| M5Core2(PORT C) | U2RXD(GPIO13)            | U2TXD(GPIO14)         | 5V | GND |
| --------------- | ------------------------ | --------------------- | -- | --- |
| GPS Unit        | Signal Transmitter (TXD) | Signal Receiver (RXD) | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

* **Datasheet** - [AT6558 ](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/AT6558_en.pdf)- [MAX2659](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/MAX2659_en.pdf)
* [**TinyGPS++ library**](http://arduiniana.org/libraries/tinygpsplus/)
* [**CASIC Multimode satellite navigation receiver protocol specification**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/Multimode_satellite_navigation_receiver_cn.pdf)
* [**GnssToolKit3(Windows Version)**](http://www.icofchina.com/d/file/xiazai/2018-05-23/2b29a8da746eec0ef1dcd9deae895298.zip)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

To get the complete code, please click [here](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/GPS_AT6558)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

**Feature Introduction**

Get GPS information

* **get time** Get local time
* **get latitude** Get latitude
* **get longitude** Get longitude
* **get satellite num** Number of satellites acquired
* **get positioning quality** Get positioning quality
* **get speed** Obtain relative ground speed
* **get course** Get geographic north pole location
* **set time zone** Set local time zone

**Usage**

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/GPS/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

**Analysis:**

**$GNRMC,063012.000,A,2258.11953,N,11395.35722,E,0.69,171.74,240419,,,A\*7A**

Indicates that the positioning information is UTC time is 06:30:12, north latitude 22.58119°, east longitude 113.95357°, date is April 24, 2019

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_08.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/gps/gps_09.webp" alt=""><figcaption></figcaption></figure>
