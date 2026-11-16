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

# M5Stack NanoC6 Dev Kit

### M5Stack NanoC6 Dev Kit

***

### Product Link

{% embed url="https://openelab.io/products/nanoc6-dev-kit" %}

### Description <a href="#description" id="description"></a>

The **M5NanoC6** is a miniature, **low-power** IoT development board within the M5Stack development kit series. It is equipped with an ESP32-C6FH4 as the MCU, supporting advanced wireless communication methods such as Wi-Fi 6 and Zigbee, along with a built-in infrared emitter for convenient control of infrared IoT devices. Its onboard ceramic antenna ensures a stable wireless communication connection. Additionally, the device is equipped with programmable RGB beads, adding personalized visual effects to projects. The inclusion of the Grove interface allows the M5NanoC6 to flexibly expand a variety of M5 devices (customizable for different types of devices, such as those using UART, I2C, and other communication protocols), providing developers with rich hardware expansion possibilities. It is suitable for fields such as smart homes, industrial automation, health monitoring, and IoT devices, offering a comprehensive development solution for innovative projects.

The burning program needs to enter the download mode: press and hold the key (GPIO9), and then connect the data cable to enter the download mode.\
![schematics](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5NanoC6/M5PPT%20\(4\).gif)

The M5NanoC6 is the first WiFi-6-enabled core control board that supports the 2.4GHz Wi-Fi 6 protocol (802.11ax) and is backward compatible with 802.11b /g/n.\
The WiFi 6 protocol has higher speed, greater capacity, lower latency, and stronger security than previous WiFi protocols.

### Features <a href="#features" id="features"></a>

* Support 2.4Ghz Wi-Fi 6, Zigbee, and Thread, Matter wireless protocols.
* Built-in infrared LED and RGB
* Grove port
* Ceramic antenna
* Small in size

### Applications <a href="#applications" id="applications"></a>

* Intelligent housing system
* Industrial control system
* Environmental monitoring system
* Agricultural iot systems
* Medical treatment
* Consumer electronic
* Service robot

### Specification <a href="#specification" id="specification"></a>

<table><thead><tr><th width="275">Resources</th><th>Parameters</th></tr></thead><tbody><tr><td>SoC</td><td>ESP32-C6FH4@RISC-V 160MHz，4M Flash， Wi-Fi 6，Zigbee 3.0，Thread 1.3, Matter，CDC</td></tr><tr><td>WIFI protocol</td><td>2.4GHz Wi-Fi 6 protocol (802.11ax) and backward compatible with 802.11b /g/n</td></tr><tr><td>RGB</td><td>WS2812</td></tr><tr><td>IR remote control parameters</td><td>The infrared emission distance of &#x3C; 0° is 632CM<br>The infrared emission distance of &#x3C; 45° is 83CM<br>The infrared emission distance of &#x3C; 90° is 29CM</td></tr><tr><td>Grove outputs maximum current</td><td>DC 5V@600mA(Output capacity depends on USB power supply)</td></tr><tr><td>Standby current （Deep Sleep Mode)</td><td>Type-C Power supply DC 5V@125.5uA<br>Grove power supply DC 5V@50uA</td></tr><tr><td>Standby current (ULP Mode)</td><td>Type-C Power supply DC 5V@252uA<br>Grove power supply DC 5V@201.5uA</td></tr><tr><td>Operating current</td><td>In WIFI mode: DC 5V@106.2mA</td></tr><tr><td>WI-FI stretch test (antenna back up, back alignment test)</td><td>54.9m</td></tr><tr><td>Operating temperature</td><td>0-40°C</td></tr><tr><td>Product Size</td><td>23.5*12*9.5mm</td></tr><tr><td>Package Size</td><td>110*81*11mm</td></tr><tr><td>Product Weight</td><td>2.5g</td></tr><tr><td>Package Weight</td><td>11.2g</td></tr></tbody></table>

![](https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-a6ee31bc-623f-4d53-af92-797ccc6a03b4.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-1228b929-959f-4940-b4fa-b14451eed567.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-b877ed06-0039-4aff-b380-44d5b797c71b.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-5f49bf45-e2de-4c18-87a5-460cc78cffcf.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-1118efa7-1956-49c2-9023-bd96402f6d81.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-2e866aaa-29eb-42a2-a9fe-7808544e4e7d.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [ESP32-C6 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5NanoC6/esp32-c6_datasheet_cn.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-91614517-651d-4d8f-ba59-5d03d97372f9.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/pinMap-0b32b2eb-029a-48ae-9786-58ba5a5bd61d.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/pinMap-6943ad0d-0ae3-4d8c-9e3e-3ee58836a69c.png" alt=""><figcaption></figcaption></figure>

When using RGB, remember to turn on the RGB power supply switch, that is, the GPIO19 pin should be set to high level

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/M5NanoC6/img-a5c60e93-a3d5-4534-a8fb-bb4882a84adc.jpg" alt=""><figcaption></figcaption></figure>
