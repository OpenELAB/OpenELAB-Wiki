# M5Stack Unit NFC U216 Development Guide

{% hint style="info" %}
[**View M5Stack Unit NFC U216 on OpenELAB**](https://openelab.io/products/m5stack-nfc-universal-unit-st25r3916)

**Product/option:** M5Stack Unit NFC U216 · **Workbook SKU:** `M5-U216`
{% endhint %}

[M5-U216](https://openelab.io/products/m5stack-nfc-universal-unit-st25r3916)

## Product and scope

**U216 Unit NFC** is a 13.56MHz NFC front end for tag interfaces, identification prototypes and your own contactless applications. It uses a different host connection from the ST25R3916-based Cap CC1101 accessory.

## Hardware and technical documents

| Item               | Reference                                                          |
| ------------------ | ------------------------------------------------------------------ |
| Chip               | ST25R3916-AQWT                                                     |
| Host interface     | I2C, address 0x50; 100/400kHz                                      |
| Protocols          | NFC-A/B, NFC-F and NFC-V as supported by the selected library mode |
| Nominal connection | HY2.0-4P Grove; follow host-specific wiring                        |
| Size               | 48 × 24 × 8mm                                                      |

The official page links the **schematic and dimensional drawing**. Read its **CoreS3 Grove-port connection note** before wiring: a matching plug does not establish correct signal routing. Protocol support and tag permissions/lock bits constrain write operations.

## Getting started

1. Connect the unit to the supported host with power off, following its pin map.
2. Install **M5Unit-NFC**, M5UnitUnified and the documented host dependencies.
3. Select the **UnitNFC** target in the official detection example; do not select CapCC1101NFC, which uses another bus path.
4. Upload, approach a compatible test tag and observe identification.
5. Read a known NDEF test record before attempting writes.

**Expected checkpoint:** repeatable identification of a compatible test tag with the correct unit target.

## Development software and recovery

Use the official Arduino example and library target matrix. Record library/host versions. Reader, writer and emulation examples have different support; the library release notes explicitly distinguish modes. Recover the host application through its normal flashing procedure; this unit is not an independent ESP32 controller.

## FAQs

**I2C scans but NFC fails?** Check the target, host port wiring, IRQ/control requirements and tag standard.

**Can it emulate every contactless card?** No. Supported emulation modes are specific; MIFARE Classic emulation is not provided by the cited ST25R3916 path.

**Read range is short?** Check tag orientation, antenna proximity and metal near the coil.

## Sources and validation

* [Hardware, CoreS3 note and schematic](https://docs.m5stack.com/en/unit/Unit_NFC)
* [Official Arduino example](https://docs.m5stack.com/en/arduino/projects/unit/unit_nfc)
* [Library, target matrix and releases](https://github.com/m5stack/M5Unit-NFC)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Unit NFC](https://docs.m5stack.com/en/unit/Unit_NFC) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U216`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                         |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1229/SCH_Unit_NFC_V0.1_2025_11_28_12_15_35.pdf)     |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U216_Unit_NFC/Structures)              |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U216_Unit_NFC/Structures/Unit_NFC.stl) |
| Official source: M5Unit-NFC  | [Read official source: m5unit-nfc](https://github.com/m5stack/M5Unit-NFC)                                                        |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_nfc)                                  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
