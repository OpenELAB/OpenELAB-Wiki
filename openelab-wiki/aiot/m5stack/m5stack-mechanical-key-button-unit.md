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
