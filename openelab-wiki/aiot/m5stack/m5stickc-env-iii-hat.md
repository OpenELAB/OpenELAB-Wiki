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

# M5StickC ENV III HAT

{% hint style="info" %}
[**View M5Stack M5StickC ENV III HAT with SHT30 and QMP6988 on OpenELAB**](https://openelab.io/products/m5stickc-env-iii-hat)

**Store SKU / option:** `M5-U053-D`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5StickC ENV III HAT

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/m5stickc-env-iii-hat" %}

### Description <a href="#description" id="description"></a>

**ENV III HAT** is a multifunctional environmental sensor adapted to the M5StickC series. It integrates SHT30 and QMP6988 internally to detect temperature, humidity, and atmospheric pressure data. SHT30 (0x44) is a high-precision, low-power digital temperature sensor. Humidity sensor. QMP6988 (0x56) is an absolute air pressure sensor specially designed for mobile applications with high accuracy. For projects that require rapid collection and detection of environmental data, ENV-III HAT is a balanced performance Good choice with cost performance.

### Features <a href="#product-features" id="product-features"></a>

* Temperature, humidity, air pressure
* High reliability and long-term stability
* High accuracy

### Applications <a href="#applications" id="applications"></a>

* Weather station
* Storage barn environment monitoring

### Specification <a href="#specification" id="specification"></a>

| Resources                                               | Parameter                        |
| ------------------------------------------------------- | -------------------------------- |
| Maximum temperature measurement range                   | -40 \~ 120 ℃                     |
| Highest measurement accuracy                            | 0 \~ 60 ℃/±0.2℃                  |
| Humidity measurement range/error                        | 10 \~ 90 %RH / ±2%               |
| Maximum measured value of air pressure/resolution/error | 300 \~ 1100hPa / 0.06Pa / ±3.9Pa |
| Communication protocol                                  | I2C: SHT30(0x44), QMP6988(0x56)  |
| Working temperature                                     | 32°F to 104°F (0°C to 40°C )     |
| Net weight                                              | 4g                               |
| Gross weight                                            | 8g                               |
| Product Size                                            | 15\*24\*14mm                     |
| Package Size                                            | 136\*92\*20mm                    |
| Case Material                                           | Plastic ( PC )                   |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat_envIII/hat_envIII_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat_envIII/hat_envIII_06.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5StickC    | GPIO26 | GPIO0 | 3.3V | GND |
| ----------- | ------ | ----- | ---- | --- |
| ENV III HAT | SCL    | SDA   | 3.3V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_envIII/hat_envIII_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet**
  * [QMP6988](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/enviii/QMP6988%20Datasheet.pdf)
  * [SHT30](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/SHT3x_Datasheet_digital.pdf)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Hat-ENV III with M5StickC](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Hat_ENVIII_M5StickC/Hat_ENVIII_M5StickC.ino)
* [M5Hat-ENV III with M5StickCPlus](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Hat_ENVIII_M5StickCPlus/Hat_ENVIII_M5StickCPlus.ino)

#### UIFlow example <a href="#uiflow-example" id="uiflow-example"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_envIII/hat_enviii_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

### UIFlow <a href="#uiflow" id="uiflow"></a>

* get pressure

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_envIII/hat_enviii_uiflow_02.webp" alt=""><figcaption></figcaption></figure>

* get temperature

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_envIII/hat_enviii_uiflow_03.webp" alt=""><figcaption></figcaption></figure>

* get humidity

<figure><img src="../../.gitbook/assets/image (415).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat ENV-III](https://docs.m5stack.com/en/hat/Hat_ENV-III) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U053-D`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need           | Model-specific reference                                                                                                                                 |
| -------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U053%E2%80%91D_Hat_ENV%E2%80%91III/Structures)                 |
| Mechanical / CAD files     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U053%E2%80%91D_Hat_ENV%E2%80%91III/Structures/Hat_ENV-III.stl) |
| Example source: M5Unit-ENV | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Hat_ENVIII_M5StickC/Hat_ENVIII_M5StickC.ino)                |
| Example source: M5Unit-ENV | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Hat_ENVIII_M5StickCPlus/Hat_ENVIII_M5StickCPlus.ino)        |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
