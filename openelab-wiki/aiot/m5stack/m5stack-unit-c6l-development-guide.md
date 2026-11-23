# M5Stack Unit C6L U202 Development Guide

{% hint style="info" %}
[**View M5Stack Unit C6L U202 on OpenELAB**](https://openelab.io/products/m5stack-c6l-unit-for-meshtastic)

**Product/option:** M5Stack Unit C6L U202 · **Workbook SKU:** `M5-U202`
{% endhint %}

[M5-U202](https://openelab.io/products/m5stack-c6l-unit-for-meshtastic)

## Product and scope

**U202 Unit C6L** is a self-contained ESP32-C6/SX1262 development unit for LoRa telemetry and supported mesh applications. Unlike a Cardputer cap, it includes its own application processor.

## Hardware and technical documents

| Item      | Reference                        |
| --------- | -------------------------------- |
| Processor | ESP32-C6, RISC-V                 |
| Flash     | 16MB                             |
| Radio     | SX1262                           |
| Display   | 0.66-inch SSD1306 OLED, 64 × 48  |
| Power     | USB-C, 5V                        |
| Envelope  | 62 × 24 × 8mm, excluding antenna |

Use the product's **schematic, pin map and model-size resources**. Check the radio and Wi-Fi antenna connections; they serve different bands. A maximum radio power specification is not a recommended regional transmit setting.

## Getting started

1. Attach the proper antennas and connect USB-C data/power.
2. For Meshtastic, follow M5Stack's guide and select **M5Stack Unit C6L** in the official web flasher.
3. After flashing, set the legal region and match a second node's channel/modem settings.
4. Send a short test message and confirm the other node receives it.
5. For custom Arduino code, use the documented **M5UnitC6L** board target; the reviewed button example requires M5Stack board manager **3.2.4 or later**.

**Expected checkpoint:** successful node identification and a received test message, or a working model-specific local example.

## Development software and recovery

Arduino, UiFlow2 and Meshtastic are separate firmware paths. The product page links RadioLib/M5Unified integration and official program instructions. Record board-package and library versions before updates. Enter the model's download mode to recover a bad application; preserve configuration before an erase.

## FAQs

**Can I flash a generic ESP32-S3 image?** No. This unit uses ESP32-C6.

**No packets?** Check region, antenna and channel/modem settings before changing output power.

**Why did the UI change?** Firmware paths and versions expose different interfaces.

## Sources and validation

* [Hardware and schematic](https://docs.m5stack.com/en/unit/Unit_C6L)
* [Arduino target and upload](https://docs.m5stack.com/en/arduino/unit_c6l/program)
* [Meshtastic setup](https://docs.m5stack.com/en/guide/unit_c6l/meshtastic)
* [Board-package minimum reference](https://docs.m5stack.com/en/arduino/unit_c6l/button)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Unit C6L](https://docs.m5stack.com/en/unit/Unit_C6L) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U202`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/unit_c6l/program)                                                   |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1185/SCH_Unit_C6L_SCH_B0.4.1_20250827_2025_09_02_15_04_22.pdf) |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1223/S012-SCH_Sch_M5_C6_Lora_v0.2.3_2025_12_02_19_14_35.pdf)   |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U202_Unit_C6L/Structures)                         |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U202_Unit_C6L/Structures/Unit_C6L.stl)            |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
