# LILYGO T-Embed CC1101 Plus Engineering Guide

{% hint style="info" %}
[**View LILYGO T-Embed CC1101 Plus on OpenELAB**](https://openelab.io/products/lilygo-t-embed-cc1101-plus)

**Model:** LILYGO T-Embed CC1101 Plus · **OpenELAB SKU:** `LILYGO-K268-01` · **Variant:** verify exact purchased revision/option before development or flashing.
{% endhint %}

[LILYGO-K268-01](https://openelab.io/products/lilygo-t-embed-cc1101-plus)

## Product and scope

**K268-01** is the external-antenna **T-Embed CC1101 Plus** configuration. LILYGO describes Plus as a T-Embed CC1101 with an added nRF24L01 module. Use it for your own RF/NFC/IR prototypes and portable instrumentation.

## Hardware and technical documents

| Item             | Reference                                                 |
| ---------------- | --------------------------------------------------------- |
| MCU / memory     | ESP32-S3; 16MB flash and 8MB PSRAM                        |
| Display          | 1.9-inch ST7789 IPS, 170 × 320                            |
| Radios           | CC1101 sub-GHz and added nRF24L01 2.4GHz module           |
| NFC              | PN532                                                     |
| Other interfaces | IR transmit/receive, encoder, audio and microSD resources |

The manufacturer-linked repository contains **schematics, chip datasheets, pin definitions and STEP/3D files**. K268 internal-antenna and K268-01 external-antenna configurations differ physically. Do not replace the case casually; LILYGO notes risks to the IR assembly.

## Getting started

1. Record the board revision, antenna version and factory firmware before changes.
2. Open **Xinyuan-LilyGO/T-Embed-CC1101** in PlatformIO and retain its supplied dependency configuration.
3. Select the repository's **display\_test** example first, then build/upload using the documented port.
4. Verify the screen and encoder independently.
5. Test the added nRF24L01, CC1101, NFC and IR functions separately with the correct pins and your own test devices.

**Expected checkpoint:** a working display/encoder baseline before any radio integration.

## Development software and recovery

The reviewed repository documents software **v1.3-250822** and hardware **v1.0-241103** for its base board; confirm the Plus/module-specific configuration. Its examples include radio receive/send, PN532 and factory tests. Preserve the exact commit and dependencies. Restore the matching factory image and boot procedure if uploads fail.

## FAQs

**Does CC1101 mean LoRa?** CC1101 is a different modem; use matching modulation and protocol.

**Does the added radio share CC1101 settings?** nRF24L01 is a separate 2.4GHz device with its own control pins.

**NFC code for ST25R3916 fails?** This documented device uses PN532.

## Sources and validation

* [Exact Plus product and antenna variants](https://lilygo.cc/products/t-embed-cc1101-plus)
* [Manufacturer software/hardware repository](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
