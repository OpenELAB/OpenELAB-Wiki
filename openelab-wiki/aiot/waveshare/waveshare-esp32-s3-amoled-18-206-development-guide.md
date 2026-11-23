# Waveshare ESP32-S3 AMOLED 1.8 and 2.06 Engineering Guide

{% hint style="info" %}
[**View Waveshare ESP32-S3 AMOLED 1.8 and 2.06 on OpenELAB**](https://openelab.io/products/waveshare-esp32-s3-amoled-1-8)

**Product/variant:** Waveshare ESP32-S3 AMOLED 1.8 and 2.06 · **OpenELAB SKUs:** `Waveshare-29957`, `Waveshare-31957` · Select the documented hardware variant before using a pinout or firmware image.
{% endhint %}

[Waveshare-29957](https://openelab.io/products/waveshare-esp32-s3-amoled-1-8) · [Waveshare-31957](https://openelab.io/products/waveshare-esp32-s3-amoled-watch)

## Product and scope

These ESP32-S3 touch-AMOLED boards target portable HMIs and wearable prototypes. **29957 is the 1.8-inch board; 31957 is the 2.06-inch watch configuration.** Their display, audio and power pin maps must remain separate.

## Hardware and technical documents

| Item             | Reference                                                       |
| ---------------- | --------------------------------------------------------------- |
| 29957            | ESP32-S3-Touch-AMOLED-1.8; 368 × 448                            |
| 31957            | ESP32-S3-Touch-AMOLED-2.06; 410 × 502                           |
| Processor        | ESP32-S3 family                                                 |
| Peripheral scope | Touch, motion sensor, RTC, audio and power management per model |
| Software         | Model-specific Arduino / ESP-IDF examples                       |

Each official page links its **schematic, dimensions, chip datasheets and demo**. Check the battery connector polarity/charging contract and actual supplied battery. A compatible-looking display connector does not justify using the other board's settings.

## Getting started

1. Read the PCB/model label and save the delivered firmware information.
2. Open the **matching model's** example archive/repository, keeping its dependency versions.
3. Select the model-specific display/touch test and its required board/PSRAM configuration.
4. Build/upload, then verify resolution, orientation and touch coordinates.
5. Test motion, RTC and audio independently before adding Wi-Fi or application UI code.

**Expected checkpoint:** a complete, responsive display/touch test on the exact model.

## Development software and recovery

The 2.06-inch repository provides a managed BSP component named **waveshare/esp32\_s3\_touch\_amoled\_2\_06** and release firmware. Use the 1.8-inch resources for 29957; do not swap BSPs. Preserve versions and restore through the model's factory/download-mode procedure.

## FAQs

**Blank screen after upload?** Check model target, PMU, display controller and reset sequence.

**Touch rotated relative to the picture?** Align the model's touch transform with display rotation.

**Battery does not charge?** Verify supported chemistry, connector/polarity and charging configuration before replacement.

## Sources and validation

* [1.8-inch hardware and demo](https://www.waveshare.com/wiki/ESP32-S3-Touch-AMOLED-1.8)
* [2.06-inch hardware and demo](https://www.waveshare.com/wiki/ESP32-S3-Touch-AMOLED-2.06)
* [2.06-inch official BSP/software](https://github.com/waveshareteam/ESP32-S3-Touch-AMOLED-2.06)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/ESP32-S3-Touch-AMOLED-1.8) and [Introduction](https://www.waveshare.com/wiki/ESP32-S3-Touch-AMOLED-2.06) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                            | Model-specific reference                                                                                        |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Official source: ESP32-S3-Touch-AMOLED-1.8  | [Read official source: esp32-s3-touch-amoled-1.8](https://github.com/waveshareteam/ESP32-S3-Touch-AMOLED-1.8)   |
| Official source: ESP32-AIChats              | [Read official source: esp32-aichats](https://github.com/waveshareteam/ESP32-AIChats)                           |
| Official source: ESP32-S3-Touch-AMOLED-2.06 | [Read official source: esp32-s3-touch-amoled-2.06](https://github.com/waveshareteam/ESP32-S3-Touch-AMOLED-2.06) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
