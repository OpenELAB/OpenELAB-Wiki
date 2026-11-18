# LILYGO T-2CAN and T-2CAN-FD Engineering Guide

{% hint style="info" %}
[**View LILYGO T-2CAN and T-2CAN-FD on OpenELAB**](https://openelab.io/products/lilygo-t-2can-esp32s3-qwiic)

**Model/kit:** LILYGO T-2CAN and T-2CAN-FD · **OpenELAB SKU:** `LILYGO-H784`
{% endhint %}

[LILYGO-H784](https://openelab.io/products/lilygo-t-2can-esp32s3-qwiic)

## Product and scope

**H784 T-2CAN** and **H784-A CAN-FD** are related ESP32-S3 communication boards. The FD version changes the external CAN controller; do not assume both buses support CAN FD.

## Hardware and technical documents

| Item                        | Reference                                                                       |
| --------------------------- | ------------------------------------------------------------------------------- |
| Original T-2CAN             | External MCP2515-based CAN path                                                 |
| T-2CAN-FD                   | External MCP2518FD on one bus                                                   |
| Second bus                  | ESP32-S3 TWAI, Classical CAN 2.0B                                               |
| Host                        | ESP32-S3                                                                        |
| Documented example baseline | PlatformIO espressif32 6.5.0 / Arduino ESP32 2.0.14 in repository support table |

The official repository supplies **separate original/FD schematics, pin overview and firmware**. The FD hardware document explicitly distinguishes the MCP2518FD bus from TWAI. Check transceiver type, pinout, grounding and termination before connecting either bus.

## Getting started

1. Read the board label and select original or FD firmware/example configuration.
2. Use the repository's **can** or **original\_test** example and matching PlatformIO environment.
3. Begin on an isolated bench CAN network with a compatible peer; confirm required termination at the bus ends.
4. Match arbitration bitrate. On the FD-capable path, also match data bitrate and frame mode.
5. Send a harmless test frame on one bus at a time and verify receipt.

**Expected checkpoint:** error-free frame exchange on the selected physical bus with recorded bitrate and frame format.

## Development software and recovery

Preserve the repository commit and environment. Do not port MCP2515 driver settings directly to MCP2518FD. The official README also explains USB-CDC versus external-UART console routing. Use the correct factory firmware and BOOT/download procedure for recovery.

## FAQs

**Why do FD frames fail on bus 2?** The documented TWAI path is Classical CAN.

**No frames but controller starts?** Check wiring, transceiver power, termination, bitrates and peer acknowledgement.

**External UART is silent?** Check the repository's USB CDC console setting.

## Sources and validation

* [Official code, schematic and firmware repository](https://github.com/Xinyuan-LilyGO/T-2Can)
* [FD-specific hardware explanation](https://github.com/Xinyuan-LilyGO/documentation/blob/master/en/products/industrial-series/t-2can-fd/index.md)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
