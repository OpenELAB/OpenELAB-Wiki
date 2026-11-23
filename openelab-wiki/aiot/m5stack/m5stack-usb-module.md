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

# M5Stack USB Module

{% hint style="info" %}
[**View M5Stack USB Module v1.2 with MAX3421E USB Host and Peripheral Support on OpenELAB**](https://openelab.io/products/m5stack-usb-module)

**Store SKU / option:** `M5-M020-V12`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack USB Module with MAX3421E v1.2

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-usb-module" %}

### Description <a href="#description" id="description"></a>

The **USB v1.2 Module** is a USB driver module in the M5Stack stackable module series, adopting the MAX3421E chip solution. It provides a standard USB interface, supporting both USB host and peripheral functions. It is compatible with a wide range of USB devices and operating systems, connecting to the system via SPI communication. The board is equipped with two dip switches to adapt to different M5 series hosts and reserves pins for controlling external devices or reading their status. Additionally, it features a battery holder, enhancing its flexibility and practicality. This device is suitable for smart home, industrial control, consumer electronics, medical devices, and education and research fields.

### Features <a href="#features" id="features"></a>

* Standard USB 2.0 interface
* SPI communication protocol is adopted
* GPIO Pin expansion (5x input, 5x output)
* Lithium battery seat
* Toggle the switch to adjust different hosts

### Applications <a href="#applications" id="applications"></a>

* USB key logger
* Read and write U disk

### Specification <a href="#specification" id="specification"></a>

| Resources              | Parameters         |
| ---------------------- | ------------------ |
| Chip                   | MAX3421E           |
| Supported USB standard | USB 2.0            |
| Interface type         | SPI                |
| Operating temperature  | 0-40°C             |
| Product Size           | 54.2\*54.2\*12.8mm |
| Package Size           | 60\*57\*17mm       |
| Product Weight         | 13g                |
| Package Weight         | 25g                |

![](https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-6086d652-c1aa-4cd5-97b1-8179c665a0f8.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-441de5c8-cbfe-4bfd-83a6-424dbe2f8521.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-8215b675-699d-4afb-8581-d74407d48b92.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-263475b3-8251-46e6-986d-b2c37f258cc9.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-c44ab4fa-7e2a-4a3c-a2f1-05f321f70726.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-ff0703be-8ba8-4c87-aaf9-782b13d6063c.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [MAX3421E](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/MAX3421E_en.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-89ba844e-f3dd-4098-900c-ca3728334cd1.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/pinMap-70b8e2ad-8325-4887-af33-44e3dae91520.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/USB%20v1.2%20Module/img-76853f1e-17c5-4a94-9c66-74e1b150a27c.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module USB v1.2](https://docs.m5stack.com/en/module/Module_USB_v1.2) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M020-V12`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                 |
| ---------------------------- | -------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/544/SCH_USBHost_V1.2.pdf)   |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/module/module_usb_v1.2) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
