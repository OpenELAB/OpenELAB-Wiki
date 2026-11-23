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

# M5Stack UnitV2 M12 with Cameras

{% hint style="info" %}
[**View M5Stack UnitV2 M12 Version with Cameras on OpenELAB**](https://openelab.io/products/m5stack-unitv2-m12-version)

**Store SKU / option:** `M5-U078-M12`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack UnitV2 M12 Version with Cameras

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-unitv2-m12-version" %}

### Description <a href="#description" id="description"></a>

UnitV2 is a high-efficiency AI recognition module from M5Stack, It adopts Sigmstar SSD202D (integrated dual-core Cortex-A7 1.2GHz processor) control core, integrated 128MB-DDR3 memory, 512MB NAND Flash, 1080P camera. Equipped with 1x regular focal length (FOV: 85°) + 1x wide-angle fisheye lens (FOV: 150°) two M12 general specifications lenses, support manual focus adjustment. Embedded Linux operating system, integrated with rich hardware and software resources and development tools brings you a simple and efficient AI development experience right out of the box!

### Features <a href="#features" id="features"></a>

* Sigmstar SSD202D
* Dual-core Cortex-A7 1.2GHz processor
* 128MB DDR3
* 512MB NAND Flash
* GC2053 1080P Colored Sensor
* Equipped with dual lenses: regular focal length (FOV: 85°) + wide-angle fisheye lens (FOV: 150°)
* Built-in microphone
* Wi-Fi 2.4GHz
* Development method:
  * Equipped with 12 ways AI image functions: QR code, face detection, line tracking, movement, shape matching, image streaming, classification, color tracking, face recognition, target tracking, shape detection, custom object recognition
  * Support web online preview, UIFlow (used as serial port json format)
  * Linux system (OpenCV, SSH, JupyterNotebook)

### Applications <a href="#applications" id="applications"></a>

* AI recognition function development
* Industrial visual recognition classification
* Machine vision learning

### UNIT-V2 series comparison <a href="#unit-v2-series-comparison" id="unit-v2-series-comparison"></a>

| Spec           | UNIT-V2                       | UNIT-V2 M12                                                         | UNIT-V2 USB                                                                      |
| -------------- | ----------------------------- | ------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Lens equipment | Normal focal length (FOV 68°) | Normal focal length (FOV 85°) + wide-angle focal length (FOV: 150°) | Without lens, USB-A universal interface, can be connected to various UVC cameras |
| CMOS           | GC2145                        | GC2053                                                              | /                                                                                |

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications          | Parameters                                                                             |
| ----------------------- | -------------------------------------------------------------------------------------- |
| Sigmstar SSD202D        | Dual Cortex-A7 1.2GHz Processor                                                        |
| Flash                   | 512MB NAND                                                                             |
| RAM                     | 128MB-DDR3                                                                             |
| Camera                  | GC2053 1080P Colored Sensor                                                            |
| Lens                    | 1x regular focal length (FOV: 85°) + 1x wide-angle fisheye lens (FOV: 150°)            |
| Input voltage           | 5V @ 500mA                                                                             |
| Hardware Peripherals    | TypeC x1, UART x1, TFCard x1, Button x1, Microphone x1, Built-in active cooling fan x1 |
| Indicator light         | Red, White                                                                             |
| Wi-Fi                   | 150Mbps 2.4GHz 802.11 b/g/n                                                            |
| Ethernet network card   | SR9900                                                                                 |
| product Size(with lens) | 48 \* 24 \* 32mm                                                                       |
| Package Size            | 122 \* 37 \* 44mm                                                                      |

### Driver Installation <a href="#driver-installation" id="driver-installation"></a>

Download the corresponding SR9900 driver according to the operating system used.

| Driver Name     | Download Link                                                                                                                                |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| SR9900\_Windows | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/sr9900.inf_amd64.zip)                                               |
| SR9900\_MacOS   | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/SR9900_macos_v1.3%20driver%20and%20installation%20instructions.zip) |

#### Windows10 <a href="#windows10" id="windows10"></a>

Extract the driver compressed package to the desktop path -> Enter the device manager and select the currently unrecognized device (named with SR9900) -> Right-click and select Custom Update -> Select the path where the compressed package is decompressed -> Click OK and wait for the update carry out.

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/static/assets/img/guide/ai_camera/unitv2/sr9900_01.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (361).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (362).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (364).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (365).png" alt=""><figcaption></figcaption></figure>

#### MacOS <a href="#macos" id="macos"></a>

Unzip the driver package -> double-click to open the SR9900\_v1.x.pkg file -> follow the prompts and click Next to install. (The compressed package contains a detailed version of the driver installation tutorial pdf)

* After the installation is complete, if the network card cannot be enabled normally, you can open the terminal and use the command below to re-enable the network card.

```python
sudo ifconfig en10 down
sudo ifconfig en10 up
```

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (366).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [UnitV2-M12](https://docs.m5stack.com/en/unit/UnitV2-M12) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U078-M12`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                 | Model-specific reference                                                                                                                                 |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U078%E2%80%91M12_UnitV2%E2%80%91M12/Structures)                |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U078%E2%80%91M12_UnitV2%E2%80%91M12/Structures/UnitV2-M12.stl) |
| Official source: UnitV2Framework | [Read official source: unitv2framework](https://github.com/m5stack/UnitV2Framework)                                                                      |
| Arduino development tutorial     | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unitv2)                                                            |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
