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

# M5Stack COMMU Module Extend

### M5Stack COMMU Module Extend RS485/TTL CAN/I2C Port

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-commu-module" %}

### Description <a href="#description" id="description"></a>

**COMMU** is a Multi-Communication-Interface-Converter. Integrated with 2\*I2C, 1\*TTL, 1\*CAN, 1\*RS485. Apparently COMMU has packed with most of series communications.

Default connection: TTL - UART0, RS485 - UART2. Since ESP32 pin map is allowed for re-assign, you can re-assign or re-mapping the TTL or RS485 interface to other pins.

Be care about TTL Interface. It is a UART Interface actually by default. But you can switch it to connect with UART2 after changed those jumpers(J6, J7, J9, J10).

**Note:**\
When using with the Core2, the base needs to be removed in order to burn the program properly.

### Features <a href="#product-features" id="product-features"></a>

* 2x I2C Interface
* 1x CAN Interface
* 1x RS485 Interface
* 1x TTL Interface
* CAN controller: MCP2515-1/SO
* RS485 Transceiver: SP3485EN-L/TR

### Specification <a href="#specification" id="specification"></a>

| Resources         | Parameter                        |
| ----------------- | -------------------------------- |
| Interface         | I2C x2, CAN x1, RS485 x1, TTL x1 |
| CAN Controller    | MCP2515-1/SO                     |
| RS485 transceiver | SP3485EN-L/TR                    |
| Net weight        | 13.5g                            |
| Gross weight      | 24g                              |
| Product Size      | 54.2\*54.2\*13mm                 |
| Package Size      | 133\*95\*16mm                    |
| Material          | Plastic ( PC )                   |

### PinMap <a href="#pinmap" id="pinmap"></a>

|  MCP2515  | ESP32 Chip |
| :-------: | :--------: |
|  CAN\_CS  |   GPIO12   |
|  CAN\_INT |   GPIO15   |
|  CAN\_SCK |   GPIO18   |
| CAN\_MISO |   GPIO19   |
| CAN\_MOSI |   GPIO23   |

| I2C Interface | ESP32 Chip |
| :-----------: | :--------: |
|    I2C\_SDA   |   GPIO21   |
|    I2C\_SCL   |   GPIO22   |

### MBUS PinMap <a href="#mbus-pinmap" id="mbus-pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/module_bus.webp" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/commu/commu_sch_01.webp" alt=""><figcaption></figcaption></figure>
