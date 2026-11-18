# HELTEC WiFi LoRa 32 Expansion Kit V2 Engineering Guide

[HT-ExpansionT-V2](https://openelab.io/products/heltec-wifi-lora-32-expansion-kit-v2-v4-r8-touch-gnss)

### Product and scope

**HT-ExpansionT-V2** is the touch/GNSS expansion-kit configuration for **WiFi LoRa 32 V4-R8**. The manufacturer says the complete kit includes the V4 board; verify the actual OpenELAB order contents, especially battery. V1 firmware is incompatible with V2.

### Hardware and technical documents

| Item       | Reference                                                |
| ---------- | -------------------------------------------------------- |
| Host       | ESP32-S3R8 V4-R8, 8MB PSRAM                              |
| Display    | 2.8-inch touch TFT                                       |
| GNSS       | Quectel L76K                                             |
| Storage    | microSD/TF slot                                          |
| Battery    | Optional flat-top 18650; verify package and polarity     |
| Protection | Manufacturer explicitly states the kit is not waterproof |

The product page supplies the **pin map and component datasheets**. Use the V2 enclosure and expansion connections; generic V4 examples may not initialize the display, GNSS, buzzer or SD power correctly.

### Getting started

1. Confirm V4-R8 and V2 labels; inspect fitted battery/GNSS and attach the antenna.
2. Connect USB-C to a computer and preserve the delivered configuration.
3. For Meshtastic, use the manufacturer-identified **firmware-heltec-v4-r8-tft-…factory.bin** family for this kit.
4. For USB flashing, hold USER, press RST once, release USER, then follow the supported flashing tool and reset afterward.
5. Set region/channel and exchange a short message; test touch, GNSS and microSD separately.

**Expected checkpoint:** a functioning V2 touch interface and a received message, followed by independent GNSS/storage checks.

### Development software and recovery

Use a V2/V4-R8-compatible source and record firmware revision. HELTEC's page distinguishes touch mode, companion mode and programming mode; Bluetooth availability depends on the selected mode. Restore the matching factory image through the same download-mode sequence if custom firmware fails.

### FAQs

**Can ordinary V4 or V1 kit firmware be used?** Match the V4-R8 memory and V2 peripheral configuration explicitly.

**No battery supplied?** Battery is optional; confirm the purchased package.

**Unusual buzzer during GNSS acquisition?** HELTEC documents a timing interaction during initial acquisition; check the current firmware notes.

### Sources and validation

* [Official V2 hardware and firmware notes](https://heltec.org/project/v4-r8-ex/)
* [HELTEC documentation](https://wiki.heltec.org/docs/platform/f%26t/flash)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
