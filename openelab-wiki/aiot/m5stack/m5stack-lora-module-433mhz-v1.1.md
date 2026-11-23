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

# M5Stack LoRa Module (433MHz) v1.1

{% hint style="info" %}
[**View M5Stack LoRa433 v1.1 Module with SX1278 and SMA Antenna on OpenELAB**](https://openelab.io/products/lora-module-v1-1)

**Store SKU / option:** `M5-M005-V11`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack LoRa Module (433MHz) v1.1

***

### Product Link

{% embed url="https://openelab.io/products/lora-module-v1-1" %}

### Description <a href="#description" id="description"></a>

The **LoRa433\_V1.1 Module** is a part of the M5Stack stackable module series and is a LoRa communication module operating at a frequency of 433MHz, utilizing the **Ra-02 module** (SX1278 chip) solution. This module comes with a default **external SMA antenna** and also features two additional patch MCX pad interfaces, allowing users to switch between different types of antennas based on their needs. Additionally, the module is equipped with a **dip switch**, enabling users to easily switch between different communication pins. It supports multiple stackable uses simultaneously, offering more customization and flexibility. It is suitable for remote monitoring, smart cities, home and industrial automation, IoT devices, and more.

### Features <a href="#features" id="features"></a>

* Serial communication protocol: SPI
* Operating frequency:410MHz\~525MHz
* Supports FSK,GFSK,MSK,GMSK,LoRa™ and OOK modulation modes
* Reception sensitivity: as low as -140 dBm
* Programmable bit rate up to 300Kbps
* External antenna interface
* Built-in dip switch toggle pin
* Development platform: Arduino, Micropython, UIFlow(Blockly)

### Applications <a href="#applications" id="applications"></a>

* Remote Control
* Intelligent city
* Home and industrial automation
* Internet of Things (IoT) devices

### Specification <a href="#specification" id="specification"></a>

| Resources               | Parameters                                                     |
| ----------------------- | -------------------------------------------------------------- |
| Spectral range          | 410MHz\~525MHz                                                 |
| Communication interface | SPI                                                            |
| Programmable bit rate   | Up to 300kbps                                                  |
| Antenna                 | Glue stick antenna @2.5dBi total length 110mm SMA inner needle |
| Operating temperature   | 0-40°C                                                         |
| Product Size            | 54\*54\*13.1mm                                                 |
| Package Size            | 92\*63\*25mm                                                   |
| Product Weight          | 16.1g                                                          |
| Package Weight          | 44.6g                                                          |

![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-df7edfb7-0825-4dac-b4f7-e891bd1fb2cd.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-6d4a69c2-0eaf-4938-bc8e-9dacddef0686.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-e511537d-4657-4816-a8ee-d84385c4fe48.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-d64e3825-3d1c-4c43-9888-b93854d75662.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-566f39c2-4eb1-4bd3-91d0-2139978b2918.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-976688b9-0be6-4911-bc9e-f06457fcf5c8.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [Ra-02\_CH](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module-LoRa433_V1.1/sx1278.pdf)
* [Ra-02\_EN](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module-LoRa433_V1.1/c048ps01a1_ra-02_product_specification_v1.1.pdf)
* [SX127X](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module-LoRa433_V1.1/sx1278.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module-LoRa433_V1.1/%E5%8E%9F%E7%90%86%E5%9B%BE1.png" alt=""><figcaption></figcaption></figure>

### Pinout <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module-LoRa433_V1.1/b9c85869aabc06312f753e986990708.png" alt=""><figcaption></figcaption></figure>

### Dimensions <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-cba38900-1914-4903-81e4-b5e49268d3f8.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [LoRa433\_V1.1 Module Arduino Library](https://github.com/m5stack/M5-SX127x/blob/master/examples)
* [LoRa433\_V1.1 Module Arduino Demo(LoRaSender)](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaSender/LoRaSender.ino)
* [LoRa433\_V1.1 Module Arduino Demo(LoRaReceiver)](https://github.com/m5stack/M5-SX127x/tree/master/examples/LoRaReceiver)
* [LoRa433\_V1.1 Module Arduino Demo(LoRaSetSpread)](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaSetSpread/LoRaSetSpread.ino)
* [LoRa433\_V1.1 Module Arduino Demo(LoRaDuplex)](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaDuplex/LoRaDuplex.ino)

### Version Change <a href="#version-change" id="version-change"></a>

| Listing Date | Changed                            | Note                                                                                                                                                                                                       |
| ------------ | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /            | Product Released LoRa433(SKU:M005) | /                                                                                                                                                                                                          |
| 2024.05.17   | LoRa868\_V1.1(SKU:M005\_V11)       | Compared with the previous version, the dip switch is added, which can switch different communication pins, suitable for M5Core\M5Core2\M5CoreS3 generation host, and can also be used for multiple stacks |

![](https://static-cdn.m5stack.com/resource/docs/products/module/lora/lora_01.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/module/Module-LoRa433_V1.1/img-dac09b0a-7367-4ed9-9374-b604f646ec3b.webp)

## Official documentation and development resources

Use [Module LoRa433 v1.1](https://docs.m5stack.com/en/module/Module_LoRa433_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M005-V11`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                                                            |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Example source: LoRaSender.ino    | [Read example source: lorasender.ino](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaSender/LoRaSender.ino)          |
| Example source: M5-SX127x         | [Read example source: m5-sx127x](https://github.com/m5stack/M5-SX127x/tree/master/examples/LoRaReceiver)                            |
| Example source: LoRaSetSpread.ino | [Read example source: lorasetspread.ino](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaSetSpread/LoRaSetSpread.ino) |
| Example source: LoRaDuplex.ino    | [Read example source: loraduplex.ino](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaDuplex/LoRaDuplex.ino)          |
| UIFlow1 workflow                  | [Read uiflow1 workflow](https://docs.m5stack.com/en/uiflow/blockly/module/lora433)                                                  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
