# M5Stack Cardputer-Adv K132-Adv Development Guide

{% hint style="info" %}
[**View M5Stack Cardputer-Adv K132-Adv on OpenELAB**](https://openelab.io/products/m5stack-cardputer-adv-esp32-s3a)

**Model/variant:** M5Stack Cardputer-Adv K132-Adv · **SKU:** `M5-K132-Adv`
{% endhint %}

![M5Stack Cardputer-Adv K132-Adv Development Guide](../../.gitbook/assets/cardputer-adv-k132-development-guide.webp)

_Manufacturer image: M5Stack._ [_Image source_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/Cardputer-Adv_01.webp)_._

[Product at OpenELAB](https://openelab.io/products/m5stack-cardputer-adv-esp32-s3a) · [Manufacturer wiki hub](./)

## Product identity and applications

**Cardputer-Adv K132-Adv** is an ESP32-S3 handheld computer with a keyboard, small color LCD, audio and expansion. Use it for a portable test console, a sensor interface, a keyboard-driven terminal or a self-contained embedded UI. It uses Stamp-S3A and differs from the original Cardputer in audio, sensing and hardware details.

## Key specifications

| Item           | Cardputer-Adv                                            |
| -------------- | -------------------------------------------------------- |
| Core           | Stamp-S3A / ESP32-S3FN8, 8 MB flash                      |
| Display        | 1.14-inch ST7789V2 LCD, 240 × 135                        |
| Keyboard       | 56 keys, 4 × 14 layout                                   |
| Audio          | ES8311 codec, MEMS mic, 1 W speaker and 3.5 mm output    |
| Motion/storage | BMI270 IMU; microSD                                      |
| Expansion      | HY2.0-4P Grove and 2.54 mm rear bus                      |
| Power          | USB-C/battery; current manufacturer table lists 1500 mAh |
| Envelope       | 84 × 54 × 19.6 mm                                        |

Source: [current Cardputer-Adv hardware reference](https://docs.m5stack.com/en/core/Cardputer-Adv). Check the actual battery label and board revision when working with older documentation. Cardputer Mesh Kit adds radio/GNSS hardware; the bare Adv should not be assumed to include that kit's LoRa module.

## SDK and development setup

Use the **M5Cardputer** Arduino library and its supported M5Unified/M5GFX dependencies. The [official quick-start](https://docs.m5stack.com/en/arduino/m5cardputer/program) explicitly covers both Cardputer and Cardputer-Adv and selects the **M5Cardputer** board preset in the M5Stack package.

For lower-level work, use the Adv schematic and its **CardputerADV** factory-firmware branch. Avoid copying a raw pin map or audio driver from the original device merely because the SDK entry point is shared.

## Getting started: display, then keyboard

Prepare Cardputer-Adv, a USB-C data cable, a computer and Arduino IDE. Save required settings from the current application before replacing it.

1. Install the M5Stack board package through the [official board-manager setup](https://docs.m5stack.com/en/arduino/arduino_board). Choose **M5Cardputer** and the connected device's port.
2. Install **M5Cardputer** and all prompted dependencies. Record versions; the library must include support for the Adv hardware.
3. Open **Basic → display** from the M5Cardputer examples, as selected in the manufacturer quick-start. Build and upload it unchanged before adding application code.
4. If the device does not enter download mode automatically, use its documented G0/USB boot procedure. Do not assume another M5 product's power-button sequence is identical.
5. Confirm the stock display example renders on the 240 × 135 panel. Next open the SDK's keyboard example and enter a short test string, including a modifier and a navigation key.
6. Compare the actual characters/keys with the intended input. A lit LCD alone does not prove the keyboard scanning works; test audio and microSD separately after those first two checks.

Expected result: a correct display example, then recognized keyboard input using the supported SDK example. Preserve those working examples before building a terminal or radio client.

## Interfaces and further development

Use the Adv pin map for Grove, rear bus, microphone, speaker and microSD connections. Check supply versus GPIO signal voltage and shared functions before attaching peripherals. Start with one module and confirm the base keyboard/display still works before adding another.

For audio, use the Adv-capable ES8311 example rather than a sketch written for the original Cardputer's audio path. For a wireless application, test the network stack separately from display rendering and storage. Add buffers and error handling only after each subsystem has an observable working result.

## Recovery and FAQ

| Problem                               | Check                                                                                                       |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Upload port missing                   | Data cable, power, G0/boot procedure and actual enumerated port.                                            |
| Display works, keyboard does not      | Current Adv-capable M5Cardputer library, correct preset and use of the SDK update/input loop.               |
| Original Cardputer audio sketch fails | Adv uses a different audio path; select the Adv-supported driver/example.                                   |
| LoRa/GNSS missing                     | Those require the relevant expansion/mesh kit; they are not established by the bare K132-Adv specification. |
| Need factory application              | Use the Adv-specific firmware/restoration instructions and branch, retaining settings first.                |

## Technical documents and software

| Resource                                                                                                               | Use                                          |
| ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| [Adv hardware reference](https://docs.m5stack.com/en/core/Cardputer-Adv)                                               | Pin map, connectors and revisions            |
| [Arduino quick-start](https://docs.m5stack.com/en/arduino/m5cardputer/program)                                         | M5Cardputer preset and first display example |
| [Arduino SDK](https://github.com/m5stack/M5Cardputer)                                                                  | Device library and examples                  |
| [Adv schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/Sch_M5CardputerAdv_v1.0_2025_06_20_17_19_58.pdf) | Main board electrical reference              |
| [Dimension drawing](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/K132-Adv-cardputer-ADV.pdf)                  | Mechanical dimensions                        |
| [CAD/structure files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K132-Adv_Cardputer-Adv/Structures)   | Enclosure integration                        |
| [Adv factory source](https://github.com/m5stack/M5Cardputer-UserDemo/tree/CardputerADV)                                | Adv-specific factory application             |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.

## Official documentation and development resources

Use [Cardputer-Adv](https://docs.m5stack.com/en/core/Cardputer-Adv) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K132-Adv`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                       |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5cardputer/program)                                                   |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/Sch_M5CardputerAdv_v1.0_2025_06_20_17_19_58.pdf)             |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1150/Sch_StampS3_v0.3.3.pdf)                                      |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K132-Adv_Cardputer-Adv/Structures)                   |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K132-Adv_Cardputer-Adv/Structures/Cardputer-Adv.stl) |
| Official source: M5Cardputer | [Read official source: m5cardputer](https://github.com/m5stack/M5Cardputer)                                                                    |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
