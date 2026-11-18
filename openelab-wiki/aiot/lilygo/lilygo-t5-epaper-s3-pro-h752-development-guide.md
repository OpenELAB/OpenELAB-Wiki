# LILYGO T5 E-Paper S3 Pro H752-01 Engineering Guide

{% hint style="info" %}
[**View LILYGO T5 E-Paper S3 Pro H752-01 on OpenELAB**](https://openelab.io/products/lilygo-t5-s3-pro)

**Model/option:** LILYGO T5 E-Paper S3 Pro H752-01 · **OpenELAB SKU:** `LILYGO-H752-01`
{% endhint %}

[LILYGO-H752-01](https://openelab.io/products/lilygo-t5-s3-pro)

## Product and scope

**H752-01 T5 E-Paper S3 Pro** is a connected ePaper development device. Distinguish it from the older H752 and **Lite**, which omits GPS/LoRa. Panel power hardware and firmware must match the actual revision.

## Hardware and technical documents

| Item           | Reference                                               |
| -------------- | ------------------------------------------------------- |
| MCU / memory   | ESP32-S3-WROOM-1; 16MB flash, 8MB PSRAM                 |
| Display        | 4.7-inch ED047TC1, 960 × 540, 16-level grayscale        |
| Display power  | TPS65185 in the documented newer Pro design             |
| Interfaces     | Touch, SX1262 LoRa, GNSS, RTC and microSD               |
| Power features | Model-specific battery management and magnetic charging |

The official hardware guide links **pin maps, schematics and software resources**. Use the fitted panel's drive/VCOM requirements; do not tune display voltages using another revision's defaults.

## Getting started

1. Identify H752-01 and the RF/GNSS configuration; preserve factory firmware details.
2. Install the manufacturer-recommended library/build environment for this Pro revision.
3. Select a basic ePaper test for the correct panel and power driver.
4. Upload, wait for a complete refresh, and verify text, grayscale and touch response.
5. Add GNSS and radio tests independently, attaching the proper antenna and selecting the regional plan.

**Expected checkpoint:** a complete, repeatable image refresh with correct orientation before networking is added.

## Development software and recovery

Use the current Pro hardware documentation and its linked SDK/examples, preserving source and dependency versions. The H752-01 revision adds a different display-power path and GPS; old firmware is not automatically compatible. Restore the matching factory image if custom firmware fails.

## FAQs

**Image remains after shutdown?** That is normal ePaper persistence.

**Wrong grayscale or incomplete refresh?** Check revision, panel driver, power sequencing and waveform settings.

**Lite code has no GPS/LoRa?** Lite is a different peripheral configuration.

## Sources and validation

* [Manufacturer product](https://lilygo.cc/products/t5-e-paper-s3-pro)
* [Exact Pro hardware documentation](https://wiki.lilygo.cc/products/t5-series/t5-e-paper-s3-pro/)
* [Revision history reference](https://github.com/LILYGOpp/LILYGO_wiki/blob/main/docs/get_started/en/Wearable/T5-E-Paper-S3-Pro/T5-E-Paper-S3-Pro.md)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
