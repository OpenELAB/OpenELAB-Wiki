# M5Stack Cap LoRa-1262 U214 Development Guide

{% hint style="info" %}
[**View M5Stack Cap LoRa-1262 U214 on OpenELAB**](https://openelab.io/products/m5stack-cap-lora-1262)

**Product model/family:** M5Stack Cap LoRa-1262 U214 · **OpenELAB SKU:** `M5-U214`
{% endhint %}

[M5-U214](https://openelab.io/products/m5stack-cap-lora-1262)

## Product and scope

**U214** is the SX1262/GNSS expansion cap for Cardputer-Adv. It is related to the Cardputer Mesh Kit but is an accessory, not a complete host. It differs from the older Cap LoRa868 in RF-switch control.

## Hardware and technical documents

| Item                      | Reference                                    |
| ------------------------- | -------------------------------------------- |
| LoRa                      | SX1262; documented band range 868–923MHz     |
| GNSS                      | ATGM336H-6N                                  |
| Host data                 | SPI radio; GNSS serial interface             |
| Expansion                 | HY2.0-4P Grove                               |
| Important revision detail | RF switch controlled through an I/O expander |

The U214 page links its **schematic, model-size PDF, structure files**, SX1262 datasheet and CASIC GNSS protocol. Follow that pin map; the radio must not be initialized with another cap's RF-switch assumptions.

## Getting started

1. Power off the compatible Cardputer host, fit the cap and attach its antenna.
2. Install the host's Arduino environment plus **M5Unified, M5GFX, RadioLib and M5Stack's TinyGPSPlus fork**.
3. Open the official Cap LoRa868/LoRa-1262 example, which detects the cap variant.
4. Build/upload and verify radio initialization. Test a packet against a matching second node.
5. Test GNSS separately outdoors with a clear sky view and allow time for acquisition.

**Expected checkpoint:** a received packet on a matched link and separately verified GNSS data; a satellite fix is not required to prove LoRa reception.

## Development software and recovery

For Meshtastic, use the complete **Cardputer-Adv + U214** target supported by the firmware, rather than a generic SX1262 image. Preserve radio region, channel settings and firmware version. Recover the host through its documented download mode and restore the matching kit image.

## FAQs

**Older cap code transmits nothing?** Check I/O-expander RF switching and the correct example.

**No position?** Verify GNSS power, serial data and sky view.

**Does the cap alone run a mesh app?** It requires the compatible host and firmware.

## Sources and validation

* [Hardware and downloads](https://docs.m5stack.com/en/cap/Cap_LoRa-1262)
* [Official Arduino bring-up](https://docs.m5stack.com/en/arduino/projects/cap/cap_lora868)
* [Existing complete-kit guide](https://wiki.openelab.io/aiot/m5stack/m5stack-cardputer-mesh-kit-for-meshtastic-engineering-guide)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
