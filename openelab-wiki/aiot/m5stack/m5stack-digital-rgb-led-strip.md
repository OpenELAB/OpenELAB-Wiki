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

# M5Stack Digital RGB LED Strip

{% hint style="info" %}
[**View M5Stack Digital RGB LED Weatherproof Strip SK6812 on OpenELAB**](https://openelab.io/products/m5stack-digital-rgb-led)

**Store SKU / option:** `M5-A093`, `M5-A093-B`, `M5-A093-C`, `M5-A093-D`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Digital RGB LED Strip

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rgb_led_strip/rgb_led_strip_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/rgb_led_strip/rgb_led_strip_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/rgb_led_strip/rgb_led_strip_06.webp)

### Pinout <a href="#pinmap" id="pinmap"></a>

| Led Strip PIN | VCC | GND   | DATA  |
| ------------- | --- | ----- | ----- |
| Color         | Red | White | Green |

### Related Links <a href="#related-links" id="related-links"></a>

* [**FastLED Library**](https://github.com/FastLED/FastLED/wiki/Overview)

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/1321561/_kz3Inh09E4.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Roller Mill Remote Scale Display](https://www.hackster.io/eathan-rethmeier/roller-mill-remote-scale-display-9fd088)[Roller Mill Remote Scale Display](https://www.hackster.io/eathan-rethmeier/roller-mill-remote-scale-display-9fd088)A practical use of the M5Stack Atom RS232 as part of a remote display.

### Example <a href="#example" id="example"></a>

* [Click here to download the Arduino example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RGB_LED_SK6812/display_rainbow)

### FAQ <a href="#faq" id="faq"></a>

<details>

<summary>How can the long light belt be connected to stickc plus? The voltage is not enough?</summary>

As shown in the figure, connect 1 and 3 together, then connect the grove port of stickc plus, and then connect the red and white lines of 2 to the external 5v power supply respectively. The specifications of the power supply are selected according to the length of the lamp: the reference power is about: ±18w/ m /60 RGB lamps, the current required for a lamp is 60mA, for example, if the lamp is 1 meter, the power supply specification needs to be selected as 5v@3.6A

</details>

## Official documentation and development resources

Use [Unit RGB LED Strip](https://docs.m5stack.com/en/unit/Unit_RGB_LED_Strip) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A093/A093-B/A093-C/A093-D`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                    |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RGB_LED_SK6812/display_rainbow) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
