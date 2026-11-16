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

# ATOMIC Barcode/QR-Code Scanner

### ATOMIC Barcode/QR-Code Scanner 2 Base

***

### Product Link

{% embed url="https://openelab.io/products/atomic-barcode" %}

### Description <a href="#description" id="description"></a>

**Atomic QRCode2 Base** is specifically designed for the ATOM series hosts. It is a 1D/2D barcode scanning base that supports 3 major types of 2D barcodes and 8 types of 1D barcodes. The base features a built-in buzzer and supplementary LED light, providing sound effects in different states, and a red LED for focus and aiming assistance. The module uses TTL communication, making it easy to transmit data via a serial port. You can use the ESP32 built into the M5Atom host to transmit scanned data to the receiving end via wired or wireless means. The back of the base is equipped with magnets, M3 screw holes, and LEGO-compatible holes, offering various mounting options. It is suitable for logistics, retail, manufacturing, and other fields.

### Features <a href="#features" id="features"></a>

* Supports 3 types of two-dimensional code and 8 types of one-dimensional code
* Built-in buzzer sound prompts
* Built-in lighting LED
* High resolution imaging
* Focusing and aiming functions

### Applications <a href="#applications" id="applications"></a>

* Logistics
* Retail
* Manufacture

### Specification <a href="#specification" id="specification"></a>

| Resources                   | Parameters                                                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Sensor                      | 640x480 CMOS@M14 Module Module                                                                               |
| Illumination                | White LED                                                                                                    |
| Focus Indicator             | RED LED                                                                                                      |
| Recognized 2D Barcode Types | PDF417, QR Code, Data Matrix                                                                                 |
| Recognized 1D Barcode Types | Code39, Code93, Code 128, EAN-13, EAN-8, UPC-A, UPC-E, Interleaved 2 of 5                                    |
| Recognition Precision       | ≥5mil                                                                                                        |
| Print Contrast              | ≥20%                                                                                                         |
| Scan Angle                  | Rotation 360°, Tilt ±55°, Skew ±55°                                                                          |
| Field of View               | Horizontal 34°, Vertical 28°                                                                                 |
| Communication Interface     | UART@115200                                                                                                  |
| Power Consumption           | <p>Standby current (without ATOM Lite): DC5V/116.57mA<br>working current (with ATOM Lite): DC5V/174.18mA</p> |
| Casing Material             | Plastic (PC)                                                                                                 |
| Operating Temperature       | 0-40°C                                                                                                       |
| Product Size                | 48\*24\*17.5mm                                                                                               |
| Package Size                | 136\* 92\* 18mm                                                                                              |
| Product Weight              | 12g                                                                                                          |
| Package Weight              | 14.2g                                                                                                        |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20QRCode2%20Base/img-2e99dfee-f3c8-47ed-8490-ea99fd88df29.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

| Atomic QRCode2 Base     | TX  | RX  | TRIG | LED |
| ----------------------- | --- | --- | ---- | --- |
| ATOM Lite / ATOM Matrix | G22 | G19 | G23  | G33 |
| ATOMS3 / ATOMS3 Lite    | G5  | G6  | G7   | G8  |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20QRCode2%20Base/img-2c572f0f-1ddb-4f41-931d-2c816f3e484b.png" alt=""><figcaption></figcaption></figure>

### Compatible <a href="#example" id="example"></a>

<figure><img src="../../.gitbook/assets/image (949).png" alt=""><figcaption></figcaption></figure>
