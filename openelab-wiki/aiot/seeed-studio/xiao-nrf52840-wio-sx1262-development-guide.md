# Seeed Studio XIAO nRF52840 and Wio-SX1262 Kit Development Guide

{% hint style="info" %}
[**View Seeed Studio XIAO nRF52840 and Wio-SX1262 Kit on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-nrf52840-wio-sx1262-kit)

**Product model/family:** Seeed Studio XIAO nRF52840 and Wio-SX1262 Kit · **OpenELAB SKU:** `Seeed-102010710`
{% endhint %}

[Product at OpenELAB](https://openelab.io/products/seeed-studio-xiao-nrf52840-wio-sx1262-kit)

## Identity and hardware

**102010710** combines **XIAO nRF52840** with **Wio-SX1262** for a compact LoRa mesh node. It is not the similarly named ESP32-S3 kit.

| Item                     | This kit                                                        |
| ------------------------ | --------------------------------------------------------------- |
| MCU                      | Nordic nRF52840                                                 |
| LoRa radio               | Semtech SX1262-based Wio board                                  |
| Board connection         | Through-hole pin-header version matched to nRF52840             |
| Factory/application path | Meshtastic                                                      |
| Optional features        | GNSS requires the appropriate external module and configuration |

The S3 expansion uses a different board-to-board connector. Do not interchange these expansion boards based on the Wio name. The kit guide links the **XIAO schematic and radio hardware resources** for wiring and integration.

## Quick start: one message between two nodes

1. Assemble the correct board pair and attach its region-compatible antenna before transmission.
2. Connect USB to a computer and open the Meshtastic flasher.
3. Select **Seeed → Seeed XIAO nRF52840 Kit**. Use a compatible release and follow its DFU flow.
4. Copy the downloaded **UF2** to the enumerated DFU drive when instructed; allow it to reboot.
5. Pair with the Meshtastic app, set the legal region and match a second node's modem/channel configuration.
6. Send a short text and confirm reception at the second node.

**Expected result:** a recognized node and an acknowledged/reliably received test message. Save the firmware release, region, modem preset and channel settings.

## Development, recovery and FAQs

Use Meshtastic source and this kit's target for firmware development. Protect exported channel keys and configuration.

**How should firmware be updated?** The reviewed Seeed guide explicitly warns against **NRF-OTA** for this kit; use its supported DFU/UF2 path.

**No DFU drive?** Follow the XIAO's documented bootloader-entry procedure, use a data cable and inspect host enumeration.

**No location?** The basic MCU/radio combination is not proof of installed GNSS.

**Can two mesh protocols communicate?** Matching RF hardware does not make Meshtastic and MeshCore message formats compatible.

## Sources and validation

* [Manufacturer kit setup and technical resources](https://wiki.seeedstudio.com/xiao_nrf52840&_wio_SX1262_kit_for_meshtastic/)
* [Official Meshtastic flasher](https://flasher.meshtastic.org/)
* [Different ESP32-S3 kit and connector warning](https://wiki.seeedstudio.com/wio_sx1262_with_xiao_esp32s3_kit/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Get Started with XIAO nRF52840 & Wio-SX1262 Kit](https://wiki.seeedstudio.com/xiao_nrf52840&_wio_SX1262_kit_for_meshtastic/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
