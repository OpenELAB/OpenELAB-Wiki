---
description: >-
  Set up the HELTEC T114 V2 with-display node, verify native pin assignments,
  test two-way Meshtastic packets and distinguish accessory and revision
  differences.
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN

{% hint style="info" %}
[**View HELTEC Mesh Node T114 V2 nRF52840 SX1262 GPS Meshtastic LoRaWAN 868Mhz on OpenELAB**](https://openelab.io/products/heltec-mesh-node-t114-nrf52840-sx1262-gps-meshtastic-lorawan-868mhz)

**Model / option:** With Display · **SKU:** `HT-T114D`
{% endhint %}

## Product overview

### Displayed T114 hardware <a href="#heltec-mesh-node-t114-nrf52840-sx1262-gps-meshtastic-lorawan-868mhz" id="heltec-mesh-node-t114-nrf52840-sx1262-gps-meshtastic-lorawan-868mhz"></a>

Mesh Node T114 **HT-T114D** is the **with-display** nRF52840/SX1262 development-board option.

### Purchased option and revision <a href="#product-link" id="product-link"></a>

The store identifies V2 hardware; verify the received PCB revision and whether a GNSS module/case was actually included. The display suffix does not establish that every optional accessory is fitted.

### Description: firmware and radio boundary <a href="#description" id="description"></a>

Begin with a Meshtastic two-way message test over the assembled USB path. LoRaWAN, Heltec F\&T and Meshtastic are separate applications; choosing the same radio band does not make their messages compatible. [Manufacturer product/revision scope](https://heltec.org/project/mesh-node-t114/).

## Applications

### Feature <a href="#feature" id="feature"></a>

Use the T114 for low-power mesh messaging, a GNSS endpoint when its accessory is installed, or a supported LoRaWAN end device. Compare display/GNSS duty cycles at a fixed workload rather than treating a deep-sleep number as average deployed current.

For header-based sensors, reserve the radio, TFT, flash and power-control nets before selecting pins. A package's optional peripheral names are not proof that the corresponding device is populated.

## Specifications

### Specification <a href="#specification" id="specification"></a>

| Item                 | T114 with-display scope                                                       |
| -------------------- | ----------------------------------------------------------------------------- |
| Host / memory        | nRF52840 at 64 MHz; 1 MB internal flash, 256 KB RAM                           |
| Radio                | SX1262; purchased 868 MHz/high-band configuration                             |
| Published RF ceiling | 21 ± 1 dBm; regional/antenna conditions still govern use                      |
| Display              | 1.14-inch TFT, 135 × 240                                                      |
| USB / cell           | 5 V USB-C first setup; documented single-cell range 3–4.2 V                   |
| Solar                | Manufacturer FAQ 5–6.5 V, approximately 5 V recommended; separate solar input |
| Connectors           | SH1.25 two-contact battery/solar; eight-contact GNSS; two 13-position headers |
| Bare board           | 50.80 × 22.86 mm                                                              |
| Environment          | −20 to +70 °C, non-condensing; separate battery charge limits required        |

Manufacturer current examples include roughly 9 mA with GNSS/TFT off, 20 mA with TFT on, and 51 mA with both on. Its 11 µA LoRaWAN sleep and approximately 23 µA Meshtastic low-power figures describe specific modes, not a runtime guarantee. The datasheet also has inconsistent generic operating-current rows; do not use them as a peripheral power budget. [Product electrical table](https://heltec.org/project/mesh-node-t114/), [11-page datasheet](https://resource.heltec.cn/download/Mesh_Node_T114/Datasheet.pdf).

![Heltec T114 manufacturer current trace for GNSS, TFT, radio and sleep modes](<../../.gitbook/assets/image (247).png>)

_Manufacturer measurement illustration, including its 3.81 V test boundary; this review did not reproduce the measurement. Its workload is not a guaranteed runtime._

## Hardware and connections

### Power, revision and connector orientation

Use USB-C for first setup. Match the LoRa antenna to the received hardware before transmitting. Do not replace the fixed ceramic BLE antenna as if it were the LoRa IPEX connector. Keep solar and cell commissioning separate from the USB test; match polarity against the received schematic/PCB, not just a connector fit. No cell charging-temperature or external-load current limit is inferred from operating temperature.

The V2.0 schematic identifies GNSS connector contacts **1 RST\_GPS, 2 PPS, 3 WAKE\_UP, 4 RX\_GPS, 5 TX\_GPS, 6 VDD\_nRF, 7 Ve\_3V3, 8 GND**, in its numbered orientation. The drawing’s TX\_GPS/RX\_GPS names are net labels; confirm their host/module direction against the exact accessory before wiring. Identify the actual contact-1 marker before translating this into left/right. A newer V2.1 drawing also exists; custom wiring must match the received revision. [V2.0 drawing](https://resource.heltec.cn/download/Mesh_Node_T114/MeshNode-T114_V2.0_SCH\(2\).pdf), [later V2.1 drawing](https://resource.heltec.cn/download/Mesh_Node_T114/schematic/MeshNode-T114_V2.1.pdf).

### Pin Map <a href="#pin-map" id="pin-map"></a>

![Heltec T114 Rev2.0 pin map: native ports, headers and occupied radio/GNSS/TFT nets](<../../.gitbook/assets/image (248).png>)

_Heltec manufacturer Rev2.0 diagram retained from the original page and visually inspected. Match the received revision and the pin namespaces below before wiring._

| Occupied role                     | Nordic native signal                      |
| --------------------------------- | ----------------------------------------- |
| Radio SCK / MOSI / MISO           | P0.19 / P0.22 / P0.23                     |
| Radio CS / DIO1 / busy / reset    | P0.24 / P0.20 / P0.17 / P0.25             |
| TFT SCK / MOSI / CS / DC / reset  | P1.08 / P1.09 / P0.11 / P0.12 / P0.02     |
| TFT supply / backlight control    | P0.03 / P0.15; source controls active LOW |
| GNSS host TX / RX / standby / PPS | P1.07 / P1.05 / P1.02 / P1.04             |
| Vext / ADC gate / battery ADC     | P0.21 / P0.06 / P0.04                     |
| Meshtastic header I²C SDA / SCL   | P0.16 / P0.13 on second bus               |
| USER / status LED                 | P1.10 / P1.03                             |

Nordic P1.xx notation is not a connector-contact number: the reviewed core encodes P1.08 as 40. The TFT and radio use separate SPI buses. Radio DIO2 performs RF switching; TCXO is a **1.8 V radio driver setting**, not a host output to drive. QSPI nets and optional footprints remain reserved even if a generic Arduino header defines a plausible alias. [Exact Meshtastic variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/heltec_mesh_node_t114/variant.h).

For a sensor, obtain its rail/current requirements and confirm the actual header map. The Heltec framework's default Wire bus and Meshtastic's header bus differ; this table is not a promise that any example will automatically use the desired connector.

## Software and development resources

### Choose a coherent firmware route

For Meshtastic, the pinned environment is **`heltec-mesh-node-t114`**, board `heltec_mesh_node_t114`, commit **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**. It includes the exact TFT driver dependency. The environment metadata says `board_level = pr`; record the selected released artifact rather than claiming every development commit has been qualified. [Build environment](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/heltec_mesh_node_t114/platformio.ini).

For custom Arduino/LoRaWAN, the manufacturer quick start links Heltec-nRF52 package index release **1.7.0**. Install Heltec-nRF52 and select **Mesh Node T114 (HT-n5262)**, not a generic nRF52840. Reviewed framework commit `b69d5fb6cc497555047467a36e7a256aa1b6bd56` defines that exact board. Framework pin aliases and shared peripheral sequencing must remain paired with that version. Its variant header carries LGPL notices; Meshtastic is GPL-3.0 and bundled libraries have their own licenses.

The quick start's LoRaWAN path describes 1.0.2, OTAA identifiers/keys, region/sub-band and a matching gateway/server. OTAA is an activation method; Class A/C is a device behavior class, despite the page's mixed terminology. Do not upgrade the declared network-server version to 1.0.4/1.1 merely because those standards exist. ESP32/license wording copied into the nRF quick start is not proof of a universal license requirement for open-source Meshtastic. [Actual nRF quick start](https://wiki.heltec.org/docs/devices/open-source-hardware/nrf52840-series/nrf52840-series-quick-start).

## Getting started

### Original direct-link and packet-length test

Prepare the T114 with its supplied antenna, USB data cable, Meshtastic client and a compatible peer. Keep the known working application for the first pass.

1. Record the received **PCB revision**, display/GNSS accessory inventory, firmware and node ID. Use a live client read or new display update; retained pixels or a bootloader drive alone are not application acceptance.
2. Set the permitted Region, then match the peer's modem preset, frequency slot and complete channel name/key. Use ordinary client roles for the initial direct pair.
3. Send `T114-A-01`, observe it at the peer, return `T114-B-01` and confirm reception on T114. Record each receive time and RSSI/SNR where provided.
4. Repeat several uniquely numbered short pairs. If investigating the historical long-packet issue, record revision and preset, then send one permitted message longer than 50 characters with a unique sequence suffix. Confirm its actual remote text before repeating; do not flood the mesh or treat a local send entry as delivery.
5. If GNSS is fitted, enable it outdoors and check fresh time/position separately. Phone-provided coordinates do not prove the accessory works. If absent, text testing remains valid.
6. With an appropriately connected cell, repeat a reply after USB removal and compare display/GNSS settings. Measure sleep at the cell boundary only after the actual low-power mode and wake procedure are established.

**Expected result:** fresh text receipts in both directions and a revision/preset-specific record of any longer-message failure. Heltec's historical report concerned some earlier high-band T114s in Long\_Fast; V2 is a hardware change, not a generic firmware-only fix. [Manufacturer FAQ](https://heltec.org/project/mesh-node-t114/), [historical long-packet diagnostics](https://github.com/meshtastic/firmware/issues/4723#issuecomment-2369336696).

### Restore through the exact UF2 path

Back up configuration and retain a released **T114** UF2. Connect USB-C and press **RST twice quickly**. The manufacturer documents a storage volume named **HT-n5262**. Copy the exact target's UF2, wait for restart, reconnect the client, restore Region/channels and repeat the reply test. A with-display board should use a display-compatible build; the old screenless V2.4.2 download is historical, and its legacy direct URL was not available in this review. Use the current exact-model release inventory instead. [USB-CDC upload guide](https://wiki.heltec.org/docs/devices/open-source-hardware/nrf52840-series/mesh-node-t114/firmware_upload).

For unchanged-source development:

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e heltec-mesh-node-t114
```

Expected output is the target artifact under `.pio/build/heltec-mesh-node-t114/`; no build or upload was executed here.

### Project: ultrasonic telemetry and LoRaWAN checkpoint <a href="#project" id="project"></a>

![Heltec T114 ultrasonic telemetry application shown on a local display and web/mobile dashboard](<../../.gitbook/assets/image (254).png>)

_Retained manufacturer application illustration; it is not a connector-voltage or echo-level wiring specification._

The earlier page linked an ultrasonic-distance LoRaWAN project. Retain it as an application reference, not an unreviewed wiring authority: choose a sensor whose supply and output levels are documented compatible with the received T114 interface. A 5 V ultrasonic echo must not be connected directly to 3.3 V logic merely because the application uses the same host family. First confirm local distance readings in the sensor's documented units with a stationary target; then add the radio payload.

In the Heltec framework choose the exact board and its LoRaWAN example. Register its DevEUI/JoinEUI/AppKey securely in the selected server, match the documented MAC/regional parameters and gateway sub-band, then set a conservative application interval. Require a join-accept plus an uplink with an incrementing application counter at the server. An RF packet or a node serial “sending” line does not establish a successful join. Preserve keys privately and verify the decoded bytes/units against your own payload format.

## Troubleshooting and FAQs

### FAQ <a href="#faq" id="faq"></a>

**Can the BLE antenna be replaced?** Heltec identifies it as a fixed ceramic antenna; it is separate from the LoRa IPEX connector. A better LoRa antenna does not change BLE coupling.

**What fits the optional case?** The manufacturer states a battery space of 42 × 28 × 11 mm and an example pack of 40 × 25 × 10 mm. These are mechanical constraints, not battery electrical/charge approval. Verify actual pack polarity and temperature/current ratings.

**Which solar panel range is documented?** Heltec's FAQ says 5–6.5 V and recommends about 5 V. This is the solar input, not the 3–4.2 V battery connector. Verify the received revision and panel open-circuit behavior before connection.

**Does V2 address the historical long-string problem?** Heltec describes a six-layer PCB, revised RF/crystal grounding and changed antenna layout for V2. That hardware change is separate from software configuration. Record revision and preset when reproducing a failure; old high-band Long\_Fast reports are historical diagnostics, not a blanket present-day defect claim.

| Symptom                    | Ordered checks                                                                                          |
| -------------------------- | ------------------------------------------------------------------------------------------------------- |
| BLE pairs but text fails   | Actual protocol, Region/preset/slot/channel key, antenna and physical receiver                          |
| Only longer packets fail   | Exact PCB revision, Long\_Fast settings and fresh receiver record; consult historical V1/V2 diagnostics |
| UF2 drive absent           | Data cable, stable USB, rapid RST double press and actual bootloader; do not replace bootloader first   |
| Display fails after update | T114 display target, separate TFT bus and active-LOW power/backlight controls                           |
| GNSS absent                | Accessory actually installed, contact orientation, host TX/RX, enable/standby and current outdoor fix   |
| Sensor I²C scan empty      | Actual bus choice and populated device; default framework Wire differs from Meshtastic header bus       |
| Current exceeds 11 µA      | USB/LED/TFT/GNSS state, radio role, wake sources and measurement boundary; sleep figure is conditional  |

Can this act as a multi-channel LoRaWAN gateway? It is a single-radio end-device board. Is factory F\&T interoperable with stock Meshtastic? Use the same application protocol at both ends; F\&T also has its own activation workflow.

## Downloads and technical documents

### Resource <a href="#resource" id="resource"></a>

| Resource                                                                                                                                                                                                     | Model/revision and role                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [T114 product and FAQ](https://heltec.org/project/mesh-node-t114/) / [wiki](https://wiki.heltec.org/docs/devices/open-source-hardware/nrf52840-series/mesh-node-t114/)                                       | Accessories, power, revision history and usage entry points                                                                                                                                                               |
| [Datasheet](https://resource.heltec.cn/download/Mesh_Node_T114/Datasheet.pdf)                                                                                                                                | Electrical/mode figures, header names, dimensions; revision history includes V2                                                                                                                                           |
| [V2.0 schematic](https://resource.heltec.cn/download/Mesh_Node_T114/MeshNode-T114_V2.0_SCH\(2\).pdf) / [V2.1 schematic](https://resource.heltec.cn/download/Mesh_Node_T114/schematic/MeshNode-T114_V2.1.pdf) | Match received revision; V1 drawing remains a historical comparison                                                                                                                                                       |
| [Official pin-map image](https://resource.heltec.cn/download/Mesh_Node_T114/Mesh_node_t114_Pin_Map.png)                                                                                                      | Attributed Heltec orientation reference; verify revision before wiring                                                                                                                                                    |
| [TFT module datasheet](https://resource.heltec.cn/download/Mesh_Node_T114/1.14inch%20LH114T-IF03%20VER%20C.pdf)                                                                                              | Separate module electrical/mechanical resource                                                                                                                                                                            |
| [Resource center](https://resource.heltec.cn/download/Mesh_Node_T114/) / [mechanical directory](https://resource.heltec.cn/download/Mesh_Node_T114/3D)                                                       | Firmware, certificates, drawings and `3D_button.STEP` listing                                                                                                                                                             |
| [Heltec-nRF52 package index](https://github.com/HelTecAutomation/Heltec_nRF52/releases/download/1.7.0/package_heltec_nrf_index.json)                                                                         | Manufacturer quick-start installation URL                                                                                                                                                                                 |
| [Historical T114 long-message demonstration](https://www.youtube.com/watch?v=TGNeAgeDcaE)                                                                                                                    | Legacy video retained from the earlier guide; its demonstrated firmware/revision was not established. Use the exact-target packet-length checkpoint above rather than treating the video as current flashing instructions |
| [Pinned Meshtastic variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/heltec_mesh_node_t114/variant.h)                                | Exact occupied nets, radio and GNSS implementation                                                                                                                                                                        |

The resource center also preserves the L76 GNSS presentation and certificates. They do not establish that an optional receiver or enclosure is included with the display-only SKU.

### Retained illustrations

![Retained Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN illustration](<../../.gitbook/assets/image (249).png>)

![Retained Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN illustration](<../../.gitbook/assets/image (250).png>)

![Retained Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN illustration](<../../.gitbook/assets/image (251).png>)

![Retained Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN illustration](<../../.gitbook/assets/image (252).png>)

![Retained Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN illustration](<../../.gitbook/assets/image (253).png>)

### Additional existing resources

* [User Manual](https://docs.heltec.org/en/node/nrf/index.html)
* [SnapEmu IoT Platform](https://platform.snapemu.com/user/login)
* [Shematic diagram](https://resource.heltec.cn/download/Mesh_Node_T114/schematic_diagram.pdf)
* [Meshtastic](https://meshtastic.org/)
* [screenless version](https://resource.heltec.cn/download/Mesh_Node_T114/firmware/nrf-mestastic-V242-no-screen.uf2)
* [Historical diagnostic: link](https://github.com/meshtastic/firmware/issues/4723#issuecomment-2404889735)
* [Ultrasonic Sensor Distance Measurement with LoRaWAN](https://www.hackster.io/ashley15/ultrasonic-sensor-distance-measurement-with-lorawan-78c30d)

## References and validation

The complete current T114 product/wiki, nRF quick start/upload guide, datasheet, V2 drawing and exact source variants/environments were read. V2.0 power/GNSS/radio drawing was visually inspected. Later V2.1 is explicitly a separate revision reference. The controlled short/long-message procedure and power-mode record are original engineering guidance.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
