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

# M5Stack 2-Channel SPST Relay Unit

### M5Stack 2-Channel SPST Relay Unit

***

### Product Link

{% embed url="https://openelab.io/products/2-channel-spst-relay-unit" %}

### Description <a href="#description" id="description"></a>

**2-Channel SPST Relay Unit** is a 2-channel SPST relay module, equipped with two high-current relays that work under AC250V 8A or DC28V 8A. Each relay adopts independent IO control, and status indicator LED. It is suitable for home appliance power control, or ON/OFF switch for industrial equipment.

The relay is driven by IO output high and low level signals, so before connecting to the main control, please make sure that the connected port IO supports configuration as output mode. (Note: G36 of ESP32 is not allowed to be configured as output mode, so PortB will not be able to drive normally)

### Product Features <a href="#product-features" id="product-features"></a>

* 2-channel relay
* AC-250V/DC-28V @ 8A
* Status Indicator LED

### Include <a href="#include" id="include"></a>

* 1x 2RELAY Unit
* 1x HY2.0-4P cable (20cm)
* 2x VH3.96-4P Plug terminal

### Applications <a href="#applications" id="applications"></a>

* AC/DC signal switching
* Digital equipment power on and off

### Specification <a href="#specification" id="specification"></a>

| Specifications         | Parameters           |
| ---------------------- | -------------------- |
| Maximum on-off voltage | AC-250V/DC-28V       |
| Rated current          | 8A                   |
| Coil control voltage   | DC5V                 |
| Coil power consumption | 5V@154mA             |
| Coil action time       | ≤ 8ms                |
| Coil release time      | ≤ 5ms                |
| Contact form           | A normally open type |
| Contact material       | AgSnO2               |
| Relay indicator        | Blue x2              |
| Net weight             | 20g                  |
| Gross weight           | 31g                  |
| Product size           | 56 \* 24 \* 19mm     |
| Packing size           | 93 \* 138mm          |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_06.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_07.webp)

### Pinout <a href="#pinmap" id="pinmap"></a>

* 2RELAY

| M5CORE - PORT A | G21     | G22     |
| --------------- | ------- | ------- |
| 2RELAY          | RELAY-A | RELAY-B |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Unit-2RELAY - with M5ATOM](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5Atom/Unit_2RELAY_M5Atom.ino)
* [M5Unit-2RELAY - with M5CORE](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5Core/Unit_2RELAY_M5Core.ino)
* [M5Unit-2RELAY - with M5CORE2](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5Core2/Unit_2RELAY_M5Core2.ino)
* [M5Unit-2RELAY - with M5STICKC](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5StickC/Unit_2RELAY_M5StickC.ino)
* [M5Unit-2RELAY - with M5STICKC-PLUS](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5StickCPlus/Unit_2RELAY_M5StickCPlus.ino)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/unit_2relay_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

### UIFlow Functions <a href="#uiflow-functions" id="uiflow-functions"></a>

The relay is driven by IO output high and low level signals, so before connecting to the main control, please make sure that the connected port IO supports configuration as output mode. (Note: G36 of ESP32 is not allowed to be configured as output mode, so PortB will not be able to drive normally)

* Control relay(relay no., status)

<figure><img src="../../.gitbook/assets/image (450).png" alt=""><figcaption></figcaption></figure>

<br>
