---
description: >-
  Model scope, hardware, first-run tutorial, firmware, troubleshooting and
  official development resources.
---

# Seeed Studio Wio Tracker L1 Pro Development Guide

![Seeed Studio Wio Tracker L1 Pro Development Guide](../../.gitbook/assets/wio-tracker-l1-pro-development-guide.jpg)

_Manufacturer image: Seeed Studio._ [_Image source_](https://files.seeedstudio.com/wiki/SenseCAP/Meshtastic/wio-tracker-l1.jpg)_._

[Product at OpenELAB](https://openelab.io/products/seeed-studio-wio-l1-pro) · [Manufacturer wiki hub](./)

### Product and development scope

**Wio Tracker L1 Pro** is an enclosed nRF52840/SX1262 LoRa tracker with an OLED, GNSS and an internal battery. It suits a phone-linked mesh endpoint, portable location-sharing experiments or a platform for low-rate field sensors.

The **Pro** has an enclosure and built-in battery. L1 Lite, L1 and **L1 E-Ink** differ in packaging/display; the E-Ink firmware target is separate. This page covers OpenELAB Pro configurations 114993649 and 100030144, with Meshtastic or MeshCore selected by firmware.

### Hardware specifications

| Item               | Wio Tracker L1 Pro                                        |
| ------------------ | --------------------------------------------------------- |
| Controller         | nRF52840, up to 64 MHz; 1 MB internal flash, 256 kB RAM   |
| LoRa               | Wio-SX1262, documented 862–930 MHz hardware range         |
| GNSS               | L76K                                                      |
| Wireless host link | Bluetooth 5.0                                             |
| Display            | 1.3-inch OLED, 128 × 64                                   |
| Battery            | Built-in 2000 mAh in Pro configuration                    |
| USB input          | 5 V / 1 A                                                 |
| Solar input        | 5 V maximum; consult the board connector/polarity drawing |
| Expansion          | Grove, PTH signals and SWD pads                           |

Source: [manufacturer hardware reference](https://wiki.seeedstudio.com/wio_tracker_l1_node/). Match the radio/antenna variant and physical board revision before selecting firmware or adding hardware.

### Choose the network and device role

Meshtastic and MeshCore are different firmware ecosystems. Sharing the LoRa radio band does not make their application protocols compatible. Use two nodes running the same ecosystem for the first test. A phone-linked **companion** and an infrastructure **repeater** also serve different purposes; choose the role that matches the intended deployment.

Use the current country/region settings provided by that firmware and the matching antenna. An unset or mismatched region, channel or key can prevent communication even when both devices appear connected to their phones. Record firmware versions, hardware targets and radio/channel configuration with each test; keep private channel keys out of published logs.

### Getting started: one controlled radio test

1. Charge/power the Pro using a USB data cable and connect its matching LoRa antenna. Switch the device on as shown in the [hardware guide](https://wiki.seeedstudio.com/wio_tracker_l1_node/).
2. For Meshtastic, the [official L1 setup](https://wiki.seeedstudio.com/get_started_with_meshtastic_wio_tracker_l1/) selects **Seeed Wio Tracker L1** for L1/Lite/Pro. Do not select **L1 E-Ink** for the Pro OLED model. Use the supported UF2/DFU workflow; Seeed specifically warns against NRF-OTA for these devices.
3. For MeshCore, the [manufacturer guide](https://wiki.seeedstudio.com/get_started_with_other_mesh_firmware/) selects **Seeed Studio Wio Tracker L1 Pro** in Community Firmware and **Companion Bluetooth** for a phone-linked device. Use the app belonging to that ecosystem.
4. Pair the phone with the physical node shown on its display, then set the correct region/radio settings. Verify that the selected companion/mesh app can retrieve live node information.
5. Configure a second node using matching firmware family and radio/channel settings, then exchange a short test message in both directions.

For a meaningful first test, send a unique short message or the firmware's supported node-information/ping request, verify its receipt at the other node, then test the return path. Start with a short unobstructed separation. A USB connection or successful phone pairing does not establish that radio traffic is reaching another node. A node list can contain old information, so use a fresh timestamp/message to identify the current result.

Record the two node identities, firmware versions, physical locations, antenna orientation, reported RSSI/SNR where available, and delivery result. Increase distance only after a repeatable nearby test. Hardware range claims are not a guaranteed link budget for a building or field installation.

### Firmware, SDK and hardware development

The manufacturer provides the [L1 board diagrams](https://wiki.seeedstudio.com/wio_tracker_l1_node/) and a [Meshtastic source development tutorial](https://wiki.seeedstudio.com/meshtastic_source_code_practical_tutorial/). Add a Grove peripheral only after checking its signal voltage, protocol and shared pins. GNSS operation needs suitable sky visibility; give it time to establish a fix before treating an absent position as a radio fault. Track power consumption with your display/GNSS/transmission settings rather than inferring runtime from capacity alone.

For custom development, retain a known working vendor image and configuration first. Build for the exact target and preserve its bootloader/board definition. Confirm a stock image still works before diagnosing your own application. Use the official source projects and their release notes for supported build tools; do not assume an ESP32 binary can be flashed onto an nRF52840 device.

### Troubleshooting and recovery

| Symptom                               | Check and next action                                                                                         |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Pairing works but messages fail       | Match radio region, channel/key and firmware ecosystem across two nodes; check antennas.                      |
| No display after using an E-Ink image | Restore the Pro/L1 OLED target, not L1 E-Ink.                                                                 |
| No UF2/DFU device                     | Use a data cable and the manufacturer reset/DFU sequence; keep the transfer connected through re-enumeration. |
| Old Bluetooth pairing no longer works | Use the firmware-specific app and re-pair after changing application firmware.                                |
| No GNSS fix indoors                   | Test with clear sky visibility; distinguish GNSS acquisition from LoRa link health.                           |

After a firmware change, verify both host connection and the two-node radio test again. Restore the same network/application family before comparing against an earlier result.

### Technical documents and software

| Resource                                                                                                   | Use                                     |
| ---------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| [Hardware and variant comparison](https://wiki.seeedstudio.com/wio_tracker_l1_node/)                       | Pin/interface diagrams and power limits |
| [Meshtastic guide](https://wiki.seeedstudio.com/get_started_with_meshtastic_wio_tracker_l1/)               | L1/Pro target and DFU/recovery          |
| [MeshCore guide](https://wiki.seeedstudio.com/get_started_with_other_mesh_firmware/)                       | Pro companion target and migration      |
| [Meshtastic development tutorial](https://wiki.seeedstudio.com/meshtastic_source_code_practical_tutorial/) | Build workflow and board target         |
| [Meshtastic source](https://github.com/meshtastic/firmware)                                                | SDK/build sources                       |
| [MeshCore source](https://github.com/meshcore-dev/MeshCore)                                                | Alternative firmware sources            |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
