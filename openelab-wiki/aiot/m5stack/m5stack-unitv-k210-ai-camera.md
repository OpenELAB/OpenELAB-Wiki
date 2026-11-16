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

# M5Stack UnitV K210 AI Camera

### M5Stack UnitV K210 AI Camera M12 Version

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-unitv-k210-ai-camera" %}

### Description <a href="#description" id="description"></a>

**UNIT-V M12** is an AI camera unit with M12 lens specifications and K210 processor, which integrates dual-core 64-bit RISC-V CPU and neural network processor edge computing system-on-chip, it equippes with M12 optical lens **OV7740 wide-angle camera module** (can replace other M12 lenses), the body is equipped with two programmable buttons and TF card expansion slot. Its bottom provides an HY2.0-4P interface and a TYPE-C interface for data connection to the controller. The UNIT-V M12 AI camera is very small, it is suitable for embedding in various devices, with machine vision processing capabilities, supporting a variety of image recognition capabilities (such as real-time acquisition of the size and coordinates of the detected target **Real-time** acquisition of the type of detected target), and it can perform convolutional neural network calculations, which is a low-threshold machine vision embedded solution.

### Features <a href="#features" id="features"></a>

* Dual-Core 64-bit RISC-V RV64IMAFDC (RV64GC) CPU / 400Mhz(Normal)
* Dual Independent Double Precision FPU
* 8MiB 64bit width On-Chip SRAM
* Neural Network Processor(KPU) / 0.8Tops
* Field-Programmable IO Array (FPIOA)
* AES, SHA256 Accelerator
* Direct Memory Access Controller (DMAC)
* Micropython Support
* Firmware encryption support
* On-board Hardware resources:
  * Flash: 16M
  * Camera :OV7740
  * Button: button \* 2
  * External storage: TF card/Micro SD
  * Interface: HY2.0/compatible GROVE

### Applications <a href="#applications" id="applications"></a>

* Face recognition/detection
* Object detection/classification
* Obtaining size and coordinates of the target in real-time
* Obtaining the type of detected target in real-time
* Shape recognition
* Video recorder

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                         | Parameters                                                       |
| --------------------------------- | ---------------------------------------------------------------- |
| Kendryte K210                     | Dual-Core 64-bit RISC-V RV64IMAFDC (RV64GC) CPU / 400Mhz(Normal) |
| SRAM                              | 8MiB                                                             |
| Flash                             | 16M                                                              |
| Input voltage                     | 5V @ 500mA                                                       |
| KPU Neural network parameter size | 5.5MiB - 5.9MiB                                                  |
| Interface                         | TypeC x 1, GROVE(I2C+I/0+UART) x 1                               |
| Button                            | Custom button x 2                                                |
| Image Sensor                      | M12 wide-angle lens ov7740                                       |
| FOV                               | 80°                                                              |
| External storage                  | TF Card/Micro SD                                                 |
| shell material                    | Plastic ( PC )+CNC (ALUMINIUM)                                   |
| Product Size                      | 40\* 24\* 16.4mm                                                 |
| Package Size                      | 70\* 50\* 30mm                                                   |
| Product Weight                    | 13.9g                                                            |
| Package Weight                    | 52.6g                                                            |

### Datasheets <a href="#datasheets" id="datasheets"></a>

* [OV7740 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/stickv/OV7740_datasheet.pdf)

#### SD card test <a href="#sd-card-test" id="sd-card-test"></a>

UNIT-V does not currently recognize all types of MicroSD cards. We have tested some common SD cards. The test results are as follows.

<br>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/unitv_ov7740/unitv_ov7740_11.webp" alt=""><figcaption></figcaption></figure>

| Brand    | Storage | Type | Class   | Format | Test Results |
| -------- | ------- | ---- | ------- | ------ | ------------ |
| Kingston | 8G      | HC   | Class4  | FAT32  | OK           |
| Kingston | 16G     | HC   | Class10 | FAT32  | OK           |
| Kingston | 32G     | HC   | Class10 | FAT32  | NO           |
| Kingston | 64G     | XC   | Class10 | exFAT  | OK           |
| SanDisk  | 16G     | HC   | Class10 | FAT32  | OK           |
| SanDisk  | 32G     | HC   | Class10 | FAT32  | OK           |
| SanDisk  | 64G     | XC   | Class10 | /      | NO           |
| SanDisk  | 128G    | XC   | Class10 | /      | NO           |
| XIAKE    | 16G     | HC   | Class10 | FAT32  | OK(purple)   |
| XIAKE    | 32G     | HC   | Class10 | FAT32  | OK           |
| XIAKE    | 64G     | XC   | Class10 | /      | NO           |
| TURYE    | 32G     | HC   | Class10 | /      | NO           |

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT-V%20M12/pinMap-5ada3512-a9c4-4a77-8dcd-984a8009c797.png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT-V%20M12/img-0463d15d-73b2-4f6a-904d-20676f8a3197.jpg" alt=""><figcaption></figcaption></figure>
