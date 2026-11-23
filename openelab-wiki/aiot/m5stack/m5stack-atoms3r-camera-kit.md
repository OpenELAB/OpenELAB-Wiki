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

# M5Stack ATOMS3R Camera Kit

{% hint style="info" %}
[**View M5Stack ATOMS3R Camera Kit (8MB PSRAM) on OpenELAB**](https://openelab.io/products/m5stack-atoms3r-camera-kit)

**Store SKU / option:** `M5-C126-CAM`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack ATOMS3R Camera Kit

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/m5stack-atoms3r-camera-kit" %}

### Description <a href="#description" id="description"></a>

**AtomS3R Cam** is a mini programmable controller integrated with a camera, featuring the **ESP32-S3-PICO-1-N8R8** main controller with built-in WiFi, 8MB onboard **FLASH**, and 8MB **PSRAM**. It includes a power management circuit that converts 5V to 3.3V, along with a built-in three-axis **BMM150** geomagnetic sensor and six-axis **BMI270** attitude sensor. Additionally, the product is equipped with a **0.3MP GC0308** camera, supporting image capture and infrared transmission control. The camera is protected by a glass cover to prevent dust and improve image quality. Compared to previous products, the **3D antenna** of the **AtomS3R Cam** has been enhanced, offering improved performance and greater stability. The product comes pre-installed with **UVC** (USB Video Class) firmware, allowing it to function as a driver-free USB camera. Users can use the camera directly via the USB interface without installing any drivers. The product also includes a **Type-C interface** for power supply and firmware downloads, and features a **HY2.0-4P** expansion port. Six **GPIO** and power pins are reserved at the bottom for easy expansion. With a compact size of **24x24x13.5mm**, it is suitable for embedded scenarios such as IoT device monitoring and educational development tools.

### Features <a href="#product-features" id="product-features"></a>

* Integrated ESP32-S3-PICO-1-N8R8 main controller
* 300,000-pixel GC0308 camera
* Nine-axis sensor system (six-axis BMI270 + three-axis BMM150 geomagnetic sensor)
* 8MB Flash and 8MB PSRAM
* Supports infrared control
* Expandable pins and interfaces
* Development platforms: Arduino, UIFlow, Micropython

### Applications <a href="#applications" id="applications"></a>

* Driver-free USB camera
* Motion detection and direction sensing
* Wearable devices
* Smart device control
* IoT applications

### Specifications <a href="#specifications" id="specifications"></a>

| Specification                          | Details                                                                                                                                                                                                                                      |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SoC                                    | ESP32-S3-PICO-1-N8R8 @Dual-core Xtensa LX7 processor, up to 240MHz @USB-OTG                                                                                                                                                                  |
| PSRAM                                  | 8MB PSRAM                                                                                                                                                                                                                                    |
| FLASH                                  | 8MB FLASH                                                                                                                                                                                                                                    |
| Six-axis sensor (BMI270)               | <p>Accuracy: 0.05% (acceleration), 0.05°/s (angular velocity)<br>I2C address: 0x68</p>                                                                                                                                                       |
| Three-axis geomagnetic sensor (BMM150) | <p>Accuracy: 0.3 μT<br>Mounted on BMI270, magnetometer data accessed via BMI270</p>                                                                                                                                                          |
| Camera                                 | <p>GC0308<br>Max frame rate: 30 fps<br>Various output formats:YCbCr4:2:2, RGB565, Raw Bayer<br>Focal Length: 2.43mm<br>Aperture: F2.6<br>Resolution: 0.3MP<br>Sensor Size(Camera diagonal length): 1/6.5''<br>Field of View (FOV): 57.6°</p> |
| Camera panel material                  | Glass                                                                                                                                                                                                                                        |
| IR                                     | Infrared transmission range: 12.46m @ ∠180°, 1.45m @ ∠90°, 3.88m @ ∠45°                                                                                                                                                                      |
| Sleep current                          | <p>GPIO-5V power: DC5V @ 11.63 μA<br>Grove-5V power: DC5V @ 10.75 μA<br>USB-5V power: DC5V @ 92.50 μA</p>                                                                                                                                    |
| Bottom reserved GPIO pins              | G5/G6/G7/G8/G38/G39                                                                                                                                                                                                                          |
| Operating temperature                  | 0°C \~ 40°C                                                                                                                                                                                                                                  |
| Product dimensions                     | 24x24x13.5mm                                                                                                                                                                                                                                 |
| Packaging dimensions                   | 85x65.5x13.6mm                                                                                                                                                                                                                               |
| Product weight                         | 7.3g                                                                                                                                                                                                                                         |
| Packaging weight                       | 13.5g                                                                                                                                                                                                                                        |

<figure><img src="../../.gitbook/assets/image (446).png" alt="" width="375"><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

* [ESP32-S3-PICO-1-N8R8](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/AtomS3R/esp32-s3-pico-1_datasheet_en.pdf)
* [GC0308](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/GC0308.PDF)
* [BMI270](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMI270.PDF)
* [BMM150](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMM150.PDF)

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (444).png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

BMM150 & BMI270 & IR

| ESP32-S3-PICO-1-N8R8 | G0       | G45      | BMI270\_ASDx | BMI270\_ASCx | G47          |
| -------------------- | -------- | -------- | ------------ | ------------ | ------------ |
| LP5562 (RGB control) | SYS\_SCL | SYS\_SDA |              |              |              |
| BMI270               | SYS\_SCL | SYS\_SDA |              |              |              |
| BMM150               |          |          | A\_SDA       | A\_SCL       |              |
| IR                   |          |          |              |              | IR\_LED\_DRV |

Screen

| ESP32-S3-PICO-1-N8R8 | LP5562\_W | G48       | G42      | G21       | G15      | G14      |
| -------------------- | --------- | --------- | -------- | --------- | -------- | -------- |
| 0.85-Inch IPS        | LCD\_BL   | DISP\_RST | DISP\_RS | SPI\_MOSI | SPI\_SCK | DISP\_CS |

GC0308

| GC0308   | ESP32-S3-PICO-1-N8R8 |
| -------- | -------------------- |
| CAM\_SDA | G12                  |
| CAM\_SCL | G9                   |
| VSYNC    | G10                  |
| HREF     | G14                  |
| Y9       | G13                  |
| XCLK     | G21                  |
| Y8       | G11                  |
| Y7       | G17                  |
| PCLK     | G40                  |
| Y6       | G4                   |
| Y2       | G3                   |
| Y5       | G48                  |
| Y3       | G42                  |
| Y4       | G46                  |
| POWER\_N | G18                  |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="../../.gitbook/assets/image (442).png" alt=""><figcaption></figcaption></figure>

### Example <a href="#example" id="example"></a>

* [AtomS3R CAM User Demo](https://github.com/m5stack/M5AtomS3/blob/main/examples/Basics/camera/camera.ino)

## Official documentation and development resources

Use [AtomS3R-CAM](https://docs.m5stack.com/en/core/AtomS3R-CAM) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`C126-CAM`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5atoms3r-cam/program)                                             |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/681/main_board_schematic.pdf)                                 |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/681/ext_board_schematic.pdf)                                  |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/C126-CAM_AtomS3R-CAM/Structures)                 |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/C126-CAM_AtomS3R-CAM/Structures/AtomS3R-CAM.stl) |
| Example source: camera.ino   | [Read example source: camera.ino](https://github.com/m5stack/M5AtomS3/blob/main/examples/Basics/camera/camera.ino)                         |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
