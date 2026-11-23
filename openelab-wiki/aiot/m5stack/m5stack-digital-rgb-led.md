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

# M5Stack Digital RGB LED

{% hint style="info" %}
[**View M5Stack Digital RGB LED Weatherproof Strip SK6812 on OpenELAB**](https://openelab.io/products/m5stack-digital-rgb-led)

**Store SKU / option:** `M5-A093`, `M5-A093-B`, `M5-A093-C`, `M5-A093-D`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Digital RGB LED Weatherproof Strip SK6812

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-digital-rgb-led" %}

### Description <a href="#description" id="description"></a>

**RGB LED Strip** is a programmable RGB LED strip,utilizing SK6812 RGB LEDs. The LED strip supports digital addressing, which means that you can individually control the color and brightness of each individual LED on the LED strip. Single bus programming is supported to expand the LED strip.

The outer layer of the LED strip is coated with a transparent protective silica gel which supports IP65 waterproof protection, thus it can be adapted to a variety of applicable environments. The LED strip consists of a flexible FPC (soft light strip)/PCB (hard light strip board) for the substrate, and uses 5050 RGB LEDS, and 3M strong double-sided tape on the back for easy pasting and fixing. The working voltage is 5V DC voltage, and various lighting effects can be realized through controller programming.

It should be noted that with the gradual increase in the number of LED strip connections, the accompanying power consumption will also increase. Therefore, when using RGB LED strips with a large number of LEDs, it is recommended to provide additional power for them.

### Specifications <a href="#specifications" id="specifications"></a>

* Product type:RGB LED Strip
* LED Type:xdx-5050RGB-60-60
* IC Model:SK6812
* Operating Voltage:5V
* Power:±18W/per metre
* Thickness:10MM
* RGB Value:256
* LED Count: 60LEDs/per Metre
* IC Count: 60 ICs/per Metre（ICs spaced between LEDs)
* Operating Temp:-40°C---80°C
* Life Span:30Kh
* Strip Background color:Black/ White
* LED color:Full color RGB
* Data transfer rate:800K/S
* Waterproof:Waterproof Epoxy-IP65
* Strip Lengths: 0.5m/30,1m/60,2m/120,5m/300
* Programming Method: Arduino, UIFlow(Blockly, Python)
* Extendable

### Applications <a href="#applications" id="applications"></a>

* lighting decoration

### Specifications <a href="#specifications" id="specifications"></a>

| Resource            | Parameter                             |
| ------------------- | ------------------------------------- |
| Length/Net Weight   | 0.5m/37g, 1m/55g, 2m/86g, 5m/211g     |
| Length/Gross Weight | 0.5m/45g, 1m/65g, 2m/96g, 5m/220g     |
| Length/LED Count    | 0.5m/30,1m/60,2m/120,5m/300           |
| Led Strip Thickness | 10mm                                  |
| Packaging Type      | Anti-static bag packaging, fixed reel |

### PinMap <a href="#pinmap" id="pinmap"></a>

| Led Strip PIN | VCC | GND   | DATA  |
| ------------- | --- | ----- | ----- |
| Color         | Red | White | Green |

### Datasheetss <a href="#datasheetss" id="datasheetss"></a>

* [**FastLED Library**](https://github.com/FastLED/FastLED/wiki/Overview)

### Compatible

<figure><img src="../../.gitbook/assets/image (961).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit RGB LED Strip](https://docs.m5stack.com/en/unit/Unit_RGB_LED_Strip) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A093/A093-B/A093-C/A093-D`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                    |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RGB_LED_SK6812/display_rainbow) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
