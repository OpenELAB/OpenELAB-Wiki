# Waveshare ESP32-S3 Touch LCD 4 and 4B Engineering Guide

{% hint style="info" %}
[**View Waveshare ESP32-S3 4-inch display family on OpenELAB**](https://openelab.io/products/waveshare-esp32-s3-4inch-display-development-board) · [**Related smart 86-box variant**](https://openelab.io/products/waveshare-esp32-s3-smart-86-box)

**Model/option:** Waveshare ESP32-S3 Touch LCD 4 and 4B · **Top-200 SKUs:** `Waveshare-32052`, `Waveshare-28154` · Verify the exact 4-inch versus 4B display and board layout before using an example.
{% endhint %}

[Waveshare-32052](https://openelab.io/products/waveshare-esp32-s3-smart-86-box) · [Waveshare-28154](https://openelab.io/products/waveshare-esp32-s3-4inch-display-development-board)

## Product and scope

**28154 Touch-LCD-4** and **32052 Touch-LCD-4B** are distinct four-inch HMI boards. Both use 480 × 480 displays, but enclosure, power and connector wiring differ. Do not transfer a pin map solely because the screen resolution matches.

## Hardware and technical documents

| Item           | Reference                                                |
| -------------- | -------------------------------------------------------- |
| 28154          | ESP32-S3-Touch-LCD-4, touch version                      |
| 32052          | ESP32-S3-Touch-LCD-4B, 86-box HMI form factor            |
| Core memory    | ESP32-S3; manufacturer references 16MB flash / 8MB PSRAM |
| Networking     | 2.4GHz Wi-Fi and BLE                                     |
| UI development | LVGL-capable model-specific Arduino / ESP-IDF examples   |

Use each model's **schematic, dimensional drawing and terminal map**. The non-touch LCD-4 variant is another SKU. Verify supported supply and external-interface electrical levels from the chosen model's manual before connecting terminal blocks.

## Getting started

1. Check model/PCB label and use its own power instructions, leaving external loads disconnected.
2. Install the corresponding vendor demo and retain its library/LVGL versions.
3. Build and upload a basic display/touch example for **4 or 4B** as appropriate.
4. Verify full-screen geometry, color and touch at the corners.
5. Test each required CAN/RS485/GPIO function separately using its model-specific diagram.

**Expected checkpoint:** a correct local touch UI before field wiring and network services are introduced.

## Development software and recovery

Keep the exact example target, LVGL version, panel timings and power initialization. Use the appropriate board's factory firmware and download-mode instructions for recovery. Avoid mixing an example's LVGL API generation with an arbitrary newer library.

## FAQs

**Why does a 480 × 480 demo show nothing?** Panel timings, bus pins, reset and power are board-specific.

**No touch?** Verify the touch SKU, I2C driver and transform.

**Can an 86-box enclosure go outdoors?** Use documented protection/installation ratings; form factor is not an ingress rating.

## Sources and validation

* [LCD-4 exact SKU and hardware](https://docs.waveshare.net/ESP32-S3-Touch-LCD-4/)
* [LCD-4 English resource index](https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-4)
* [LCD-4B hardware and demo](https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-4B)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-4) and [Introduction](https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-4B) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                      | Model-specific reference                                                                            |
| ------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Official source: ESP32-S3-Touch-LCD-4 | [Read official source: esp32-s3-touch-lcd-4](https://github.com/waveshareteam/ESP32-S3-Touch-LCD-4) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
