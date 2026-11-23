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

# M5Stack Mechanical Key Button Unit

{% hint style="info" %}
[**View M5Stack Mechanical Key Button Unit RGB Input Module on OpenELAB**](https://openelab.io/products/mechanical-key-button-unit)

**Store SKU / option:** `M5-U144`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Mechanical Key Button Unit

***

### Product Link

{% embed url="https://openelab.io/products/mechanical-key-button-unit" %}

### Introduction

Unit Key is a single mechanical key input unit with built-in RGB LED. The key shaft adopts Blue switch with tactile bump and audible click features. Embedded with one programable RGB LED - SK6812, supports 256 level brightness. Two digital IOs are available for key status and LED control key status and lighting control. Suitable for multiple HMI applications.

<figure><img src="../../.gitbook/assets/image (471).png" alt=""><figcaption></figcaption></figure>

### Features

* Blue switch with tactile bump and audible click
* Programable RGB LED - SK6812

### Specifications

| Specification         | Parameters         |
| --------------------- | ------------------ |
| Power Supply          | DC 5V              |
| Output Logical Signal | DC 3.3V            |
| Standby Current       | DC5V@2mA           |
| Operating current     | DC5V@13mA          |
| Net weight            | 7.6g               |
| Gross weight          | 13.1g              |
| Product Dimensions    | 40 \* 24 \* 22.6mm |
| Package Size          | 90 \* 135mm        |

### Pinout

<figure><img src="../../.gitbook/assets/image (476).png" alt=""><figcaption></figcaption></figure>

### Dimensions

size:13.1g

weight:40 \* 24 \* 22.6mm

### How to Use

* [UNIT Key Example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/KEY)
* [FastLED Library](https://github.com/FastLED/FastLED/wiki/Overview)
* [FastLED API Reference](http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/)

```cilkcpp
#include <FastLED.h>
#include <M5Stack.h>

uint8_t ledColor = 0;

#define KEY_PIN  36
#define LED_PIN 26

CRGB LED[1];

void setup() {
    M5.begin();
    M5.Lcd.setTextSize(3);
    M5.Lcd.print("\n UNIT-KEY Example\n\n    Key State:");
    /* Init key pin */
    pinMode(KEY_PIN, INPUT_PULLUP);
    /* Init RGB led */
    FastLED.addLeds<SK6812, LED_PIN, GRB>(LED, 1);
    LED[0] = CRGB::Blue;
    FastLED.setBrightness(0);
}

void loop() {
    /* If Key was pressed */
    if (!digitalRead(KEY_PIN)) {
        M5.Lcd.setCursor(75, 130);
        M5.Lcd.print((" Pressed "));
        FastLED.setBrightness(255);
        FastLED.show();
        /* Hold until the key released */
        while (!digitalRead(KEY_PIN))
            ;
    } else {
        M5.Lcd.setCursor(75, 130);
        M5.Lcd.println(("Released"));
        FastLED.setBrightness(0);
        FastLED.show();
    }
    delay(100);
}

```

## Official documentation and development resources

Use [Unit Key](https://docs.m5stack.com/en/unit/Unit_Key) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U144`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                         |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic    | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/599/SCH_unitKey_V1.0.pdf)                           |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U144_Unit_Key/Structures)              |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U144_Unit_Key/Structures/Unit_Key.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/KEY)                                 |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
