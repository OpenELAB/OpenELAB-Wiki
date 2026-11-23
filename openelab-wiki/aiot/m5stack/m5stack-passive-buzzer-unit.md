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

# M5Stack Passive Buzzer Unit

{% hint style="info" %}
[**View M5Stack Passive Buzzer Unit 4KHz Audible Alert Module on OpenELAB**](https://openelab.io/products/passive-buzzer-unit)

**Store SKU / option:** `M5-U132`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Passive Buzzer Unit

***

### Product Link

{% embed url="https://openelab.io/products/passive-buzzer-unit" %}

### Description <a href="#description" id="description"></a>

**Passive Buzzer Unit** is a mini passive buzzer unit, drove by 4KHz signal, that sounds up to 72dB within 10cm distance under rating input power. With the feature of compact size, low-power consumption, awesome audio performance, and a protective housing. Applied for varied buzzer alarm scenario.

### Features <a href="#product-features" id="product-features"></a>

* Drive signal:
  * 4KHz oscillation frequency
  * Up to 72dB (within 10cm, at rating power)
  * Drive signal: 4KHz 1/2duty square wave

### Applications <a href="#applications" id="applications"></a>

* Buzzer/reminder

### Specification <a href="#specification" id="specification"></a>

| Specifications    | Parameters               |
| ----------------- | ------------------------ |
| Drive frequency   | 4KHz 1/2duty square wave |
| Power consumption | 5V@86mA                  |
| Net weight        | 3.5g                     |
| Gross weight      | 8.5g                     |
| Product size      | 24 \* 24 \* 8mm          |
| Packing size      | 93 \* 138mm              |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/buzzer/buzzer_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/buzzer/buzzer_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/buzzer/buzzer_06.webp)

### Pinout <a href="#pinmap" id="pinmap"></a>

* BUZZER

| M5CORE - PORT B | G26    |
| --------------- | ------ |
| BUZZER          | SIGNAL |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/buzzer/buzzer_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

```cpp

#include <Arduino.h>

#define buzzer_pin 26
int freq = 4000;
int ledChannel = 0;
int resolution = 10;

void setup() {
  ledcSetup(ledChannel, freq, resolution);  //Sets the frequency and number of counts corresponding to the channel.  设置通道对应的频率和计数位数
  ledcAttachPin(buzzer_pin, ledChannel); //Binds the specified channel to the specified I/O port for output.  将指定通道绑定到指定 IO 口上以实现输出
  ledcWrite(ledChannel, 512);  //Output PWM.  输出PWM
}

void loop() {
    ledcWrite(ledChannel, 512);  //Output PWM.  输出PWM
    delay(3000);
    ledcWrite(ledChannel, 0);  //Output PWM.  输出PWM
    delay(3000);
}
 
```

#### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/buzzer/unit_buzzer_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

### UIFlow Functions <a href="#uiflow-functions" id="uiflow-functions"></a>

**Notice:** If you set the BuzzerState first, the Buzzer may not sound. Turn on Buzzer state after setting the frequency.

* Set buzzer state
  * ON\
    Buzzer on.**notice:** default frequency is 4,000Hz.
  * OFF\
    Buzzer off.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/buzzer/unit_buzzer_uiflow_02.webp" alt=""><figcaption></figcaption></figure>

* Set frequency of buzzer\
  20\~20,000Hz

<figure><img src="../../.gitbook/assets/image (448).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Buzzer](https://docs.m5stack.com/en/unit/Unit_Buzzer) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U132`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                               |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U132_Unit_Buzzer/Structures)                 |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U132_Unit_Buzzer/Structures/Unit_Buzzer.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
