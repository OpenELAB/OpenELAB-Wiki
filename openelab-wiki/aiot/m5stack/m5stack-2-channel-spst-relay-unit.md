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

{% hint style="info" %}
[**View M5Stack Unit 2Relay Dual-Channel SPST Relay GPIO Switching Module on OpenELAB**](https://openelab.io/products/2-channel-spst-relay-unit)

**Store SKU / option:** `M5-U131`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_06.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/2relay/2relay_07.webp)

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

## Official documentation and development resources

Use [Unit 2Relay](https://docs.m5stack.com/en/unit/Unit_2Relay) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U131`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                               | Model-specific reference                                                                                                                                                  |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U131_Unit_2Relay/Structures)                                                    |
| Mechanical / CAD files                         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U131_Unit_2Relay/Structures/Unit_2Relay.stl)                                    |
| Arduino development tutorial                   | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_2relay)                                                                        |
| Example source: Unit\_2RELAY\_M5Atom.ino       | [Read example source: unit\_2relay\_m5atom.ino](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5Atom/Unit_2RELAY_M5Atom.ino)                   |
| Example source: Unit\_2RELAY\_M5Core.ino       | [Read example source: unit\_2relay\_m5core.ino](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5Core/Unit_2RELAY_M5Core.ino)                   |
| Example source: Unit\_2RELAY\_M5Core2.ino      | [Read example source: unit\_2relay\_m5core2.ino](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5Core2/Unit_2RELAY_M5Core2.ino)                |
| Example source: Unit\_2RELAY\_M5StickC.ino     | [Read example source: unit\_2relay\_m5stickc.ino](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5StickC/Unit_2RELAY_M5StickC.ino)             |
| Example source: Unit\_2RELAY\_M5StickCPlus.ino | [Read example source: unit\_2relay\_m5stickcplus.ino](https://github.com/m5stack/M5Unit-RELAY/blob/master/examples/Unit_2RELAY_M5StickCPlus/Unit_2RELAY_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
