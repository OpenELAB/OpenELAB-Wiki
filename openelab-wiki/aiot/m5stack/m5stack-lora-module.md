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

# M5Stack LoRa Module

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack LoRa Module( 868MHz )

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**LoRa868** is a LoRa communication module in the M5Stack stack module series (working frequency is 868MHz). A certain expansion space is reserved on the module, which defeats you for more functional design. For wireless communication or projects with more customized elements, the LoRa868 module will be a suitable choice.

### Product Features <a href="#product-features" id="product-features"></a>

* LoRa Module: Ra-01H
* Communication Protocol: SPI
* Universal Perfboard
* Working Frequency: 803\~930 MHz
* Supports: FSK, GFSK, MSK, GMSK, LoRa™ and OOK modulation modes
* Receive sensitivity: lowest to -140 dBm
* Programmable bit rate up to 300Kbps
* Built-in FPC Antenna
* External IPX Antenna connector
* Program platform: Arduino

### Applications <a href="#applications" id="applications"></a>

* Remote electricity meter reading
* Home automation
* Remote irrigation system

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter        |
| ------------ | ---------------- |
| Net weight   | 14g              |
| Gross weight | 24g              |
| Product Size | 54.2\*54.2\*13mm |
| Package Size | 60\*57\*17mm     |

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/lora868/lora868_05.webp" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/MODULE/EasyLoader_LoRa868_MODULE.exe) [Download MacOS Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/MODULE/EasyLoader_LoRa868_MODULE.dmg)

**Description:**\
Two devices will send and receive messages from each other.

### MBUS PinMap <a href="#mbus-pinmap" id="mbus-pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/module_bus.webp" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/lora/lora_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module LoRa868](https://docs.m5stack.com/en/module/Module_LoRa868) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M029`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                                                            |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic              | [Read electrical schematic](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/schematic/Modules/module_lora_sch.pdf)       |
| Example source: LoRaSender.ino    | [Read example source: lorasender.ino](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaSender/LoRaSender.ino)          |
| Example source: M5-SX127x         | [Read example source: m5-sx127x](https://github.com/m5stack/M5-SX127x/tree/master/examples/LoRaReceiver)                            |
| Example source: LoRaSetSpread.ino | [Read example source: lorasetspread.ino](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaSetSpread/LoRaSetSpread.ino) |
| Example source: LoRaDuplex.ino    | [Read example source: loraduplex.ino](https://github.com/m5stack/M5-SX127x/blob/master/examples/LoRaDuplex/LoRaDuplex.ino)          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
