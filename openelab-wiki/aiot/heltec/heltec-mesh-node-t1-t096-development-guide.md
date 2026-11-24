---
description: >-
  Compare HELTEC T1 and T096 power, antenna and native pin differences;
  commission the exact firmware, test two-way text, GNSS and F&T tracks.
---

# HELTEC Mesh Node T1 and T096 Engineering Guide

{% hint style="info" %}
[**View HELTEC Mesh Node T1 LoRa Position Tag nRF52840 Meshtastic LoRaWAN on OpenELAB**](https://openelab.io/products/heltec-mesh-node-t1-lora-position-tag)

**Model / option:** Default Title · **SKU:** `HT-Mesh-T1`

[**View HELTEC Mesh Node T096 nRF52840 GPS Meshtastic MeshCore LoRaWAN on OpenELAB**](https://openelab.io/products/heltec-mesh-node-t096-863-870mhz)

**Model / option:** Default Title · **SKU:** `HT-MeshT096`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

**Mesh Node T1 HT-Mesh-T1** is the assembled positioning tag with battery, GNSS and IMU. **Mesh Node T096 HT-MeshT096** is the separate GNSS/display development board with a high-power radio front end. Both use nRF52840 and SX1262, but they require different power assumptions, pin maps, firmware targets and DFU controls.

Use this comparison to identify the purchased model, then follow its specific first-result procedure. Preserve the installed application: Heltec F\&T, Meshtastic and other MeshCore builds have different UI/activation behavior. [T1 manufacturer](https://heltec.org/project/mesh-node-t1/), [T096 manufacturer](https://heltec.org/project/t096/).

## Applications

Use T1 for an assembled portable position/message endpoint, motion/heading experiments and controlled track recording. Use T096 for GNSS and supported mesh/LoRaWAN development when you need accessible headers and deliberate PA-aware power design.

Neither a GNSS chipset's precision claim nor a compass arrow proves a validated navigation system. Test fresh position, timestamp, selected target and actual packet receipt separately; record antenna orientation and firmware.

## Specifications

| Item                 | T1 tag                                                         | T096 board                                           |
| -------------------- | -------------------------------------------------------------- | ---------------------------------------------------- |
| Exact SKU / RF scope | `HT-Mesh-T1`; verify received regional option                  | `HT-MeshT096`; OpenELAB 863–870 MHz listing          |
| Host / memory        | nRF52840, 64 MHz, 1 MB flash, 256 KB RAM                       | Same host class; distinct board configuration        |
| LoRa path            | SX1262, manufacturer 21 ± 1 dBm ceiling                        | SX1262 plus KCT8103L PA/LNA, 28 ± 1 dBm ceiling      |
| GNSS                 | UC6580; **stock antenna is L1**, not effective L1+L5 reception | UC6580 L1+L5 hardware; default LDS antenna route     |
| Display              | ST7735S, 0.96-inch 80 × 160                                    | ST7735S, 0.96-inch 80 × 160; different wiring        |
| Motion/heading       | ICM-42607-P plus MMC5983MA                                     | No T1 IMU/compass feature inferred                   |
| Battery              | Integrated 1850 mAh assembly                                   | External single-cell path, product range 3.3–4.2 V   |
| Initial supply       | 5 V USB-C                                                      | 5 V USB-C                                            |
| Protection           | Manufacturer IP65; intact assembly required                    | No T1 enclosure rating transferred                   |
| Size / mass          | 85 × 55 × 9.5 mm / 53 g                                        | Approximately 52 × 25.4 × 10.26 mm; bare-board scope |
| DFU entry            | Double-press **Power**                                         | Double-press **RST**                                 |

T1 product text says −10 to +65 °C while the preliminary datasheet gives −20 to +60 °C. Use their conservative overlap **−10 to +60 °C** pending revision confirmation; charge only in its separately documented **0–45 °C** range. T096's −20 to +70 °C operating range is not a battery charging limit. Sources: [T1 datasheet Rev1.0.0, 16 May 2026](https://resource.heltec.cn/download/Mesh_Node_T1/Datasheet/Mesh-Node-T1.pdf), [T096 datasheet Rev1.0.0, 25 March 2026](https://resource.heltec.cn/download/Mesh_Node_T096/Datasheet/Mesh%20Node%20T096.pdf), manufacturer pages above.

Sleep figures of 11 µA (T1) and 12–13 µA (T096 documents) are mode-specific. T096 data lists approximately 407 mA at a 22 dBm TX condition and 776 mA near 29 dBm at 3.7 V, versus a listed 500 mA charge setting. These are different current paths; a charger rating does not establish enough source power for simultaneous high-power transmission and charging.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Use the correct supply and antenna path

Keep T1's original pack and enclosure intact; charge through USB-C. Do not infer replacement-cell suitability from capacity alone. T096 has separate battery/solar inputs and exposed headers: use USB first, and verify the received connector polarity plus exact solar input/cell requirements before external-power commissioning. **Solar wiring and additional loads are excluded here until their revision-specific voltage/current budget is established.** USB voltage is not a logic-pin voltage.

T1's stock antenna is calibrated for **L1** despite the UC6580 silicon's dual-frequency capability. T096 defaults to its LDS GNSS antenna; its product page describes moving an RF selection resistor to use IPEX. That is a physical RF modification, not a software toggle. It is excluded from the first test; leave the original route intact, keep the antenna bracket clear of metal and test outdoors first.

### Occupied native-port assignments

These are Nordic native port names, not physical header contacts or interchangeable Arduino board numbers.

| Role                                  | T1                                    | T096                                  |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| Radio SCK / MOSI / MISO               | P1.13 / P1.14 / P0.03                 | P1.08 / P0.11 / P0.14                 |
| Radio CS / IRQ / busy / reset         | P1.11 / P0.31 / P0.29 / P0.02         | P0.05 / P0.21 / P0.19 / P0.16         |
| Display SCK / MOSI / CS / DC / reset  | P1.00 / P0.24 / P0.12 / P0.22 / P0.20 | P0.20 / P0.17 / P0.22 / P0.15 / P0.13 |
| Display backlight                     | P0.15                                 | P1.12                                 |
| GNSS host TX / RX                     | P0.07 / P0.08                         | P0.25 / P0.23                         |
| GNSS reset / enable / PPS             | P0.26 / P0.04 active LOW / P1.09      | P1.14 / P0.06 active LOW / P1.11      |
| Battery ADC / gate                    | P0.05 / P0.11 active HIGH             | P0.03 / P1.15 active HIGH             |
| USER                                  | P1.10; second key P0.14               | P1.10                                 |
| IMU/compass SDA / SCL / sensor enable | P1.03 / P0.10 / P1.06 active LOW      | No T1 sensor implementation assumed   |
| Additional FEM supply / CSD / CTX     | Not the T096 PA path                  | P0.30 / P0.12 / P1.09                 |

Both exact variants use DIO2 RF switching and a **1.8 V TCXO driver setting**. Do not externally drive DIO3 or transfer T1's radio settings into the T096 FEM. The T096 driver reserves supply/control signals and handles output calibration; generic chip-level dBm is not calibrated antenna output. [T1 variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/heltec_mesh_node_t1/variant.h), [T096 variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/heltec_mesh_node_t096/variant.h).

The T1 datasheet calls P0.09 a white LED while the source assigns P0.09 to the buzzer and P0.16 to status LED. **Raw LED/buzzer pin driving is excluded until revision reconciliation**; normal exact-board firmware retains its own implementation. T096's datasheet also disagrees with its own header-count summary; use its numbered P2/P3 tables and received board drawing, not a generic “two 13-pin” sentence. [T1 V1.0 schematic](https://resource.heltec.cn/download/Mesh_Node_T1/schematic/Mesh_Node_T1_V1.0.pdf), [T096 V0.2 schematic](https://resource.heltec.cn/download/Mesh_Node_T096/Schematic/Mesh_Node_T096_V0.2.pdf).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

| Workflow                        | T1 target                      | T096 target                           |
| ------------------------------- | ------------------------------ | ------------------------------------- |
| Reviewed Meshtastic environment | `heltec-mesh-node-t1`          | `heltec-mesh-node-t096`               |
| Reviewed Meshtastic board       | `heltec_mesh_node_t1`          | `heltec_mesh_node_t096`               |
| Heltec Arduino board menu       | Mesh Node T1                   | Mesh Node T096 (HT-n5262G)            |
| Source peripheral scope         | ST7735, UC6580, IMU and buzzer | ST7735, UC6580, FEM power/calibration |

The Meshtastic snapshot is **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**; both environments pin TFT\_eSPI **2.5.43**. Heltec's framework snapshot **`b69d5fb6cc497555047467a36e7a256aa1b6bd56`** explicitly defines separate Arduino boards. The manufacturer nRF quick start uses package-index release 1.7.0; record the installed package and actual board menu before building. Do not select T114 simply because its MCU matches.

F\&T firmware is downloaded by exact device through **DevRemote**, copied by UF2 and then activated through its **Activate** operation. That is the manufacturer application's requirement, not a license requirement for GPL Meshtastic. The F\&T information page exposes a MeshCore-app PIN and describes MeshCore forwarding; interoperability still requires the intended application/RF/channel configuration. The arbitrary installed image must not be assumed to retain every F\&T UI feature.

For LoRaWAN, the reviewed manufacturer quick start describes MAC 1.0.2, matching OTAA credentials, region/sub-band and gateway/server. Activation methods OTAA/ABP are distinct from Class A/C. Newer standards are not automatically compatible with these examples. Preserve upstream GPL/LGPL and individual library notices.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original model-specific first result

Prepare the identified device, its supplied antenna arrangement, USB data cable and a compatible peer running the **same application protocol**. Record current firmware before replacement.

1. **T1:** charge within 0–45 °C, hold the rear Power button to start (preliminary manual: about 3 seconds) and record the device identity. **T096:** attach the matched LoRa antenna and use USB-C; record board revision and actual application. Do not use a T1 battery/antenna assumption on T096.
2. For supplied F\&T, verify activation in DevRemote if required. Select the local Region in **System**, then inspect **Radio** frequency/SF/BW/CR and compare the peer. Enable Bluetooth only if using the companion app. For Meshtastic instead, select Region, modem preset, slot and complete channel name/key in its client; keep ordinary CLIENT roles during the direct baseline.
3. **F\&T T1 controls:** Button1 moves back/up, Button2 forward/down; hold to select; Button1 double press opens Function Selection, Button2 double press opens Quick Access. **F\&T T096 controls:** USER single press advances, hold confirms, double press opens Function Selection/back, triple press opens Quick Access. Start a hold to show selection when none is highlighted.
4. Send `T1-A-01` or `T096-A-01` through the installed app/QuickPing and confirm it at the second physical radio. Return a distinct `-B-01` message and confirm local receipt. In F\&T inspect **Recent** and the received-message count; in Meshtastic inspect the receiving conversation/packet record.
5. Repeat several uniquely numbered pairs. Record actual receive time, radio parameters and current power source. A local sent entry, advert or old friend row is insufficient.
6. Enable GNSS outdoors and verify a fresh fix/time, keeping the display/antenna bracket toward clear sky. On T1 do not expect effective L5 reception from the stock antenna. Disconnect USB only after the actual model's battery path is established, then repeat a reply.

**Expected result:** current device identity, received text in both directions and a separate fresh GNSS checkpoint. No range, positioning accuracy or runtime was measured here. [F\&T controls](https://wiki.heltec.org/docs/platform/f%26t/qs/), [information/radio fields](https://wiki.heltec.org/docs/platform/f\&t/qs/information).

### F\&T positioning, heading and tracks

In **GPS**, enabling Location Sharing or GPS Track also enables GNSS. Sharing determines what peers can receive; leave it off unless the test requires disclosure. **Find Friend is documented only for T1**: the target must share location, then choose Friend or a deliberate Waypoint and verify the selected ID/coordinates. Do not infer T096 has T1's compass UI.

On T1, enter the Compass page, hold Button1/2 and follow the displayed calibration instructions away from magnetic hardware. Compare a known direction after calibration; a quaternion or heading value is not a validated bearing without the calibration/target check.

For tracks, enable GPS Track, obtain a fix and walk a short controlled outdoor route. Connect USB to DevRemote, select the actual serial port and **Route Map**. The current F\&T guide states about **one point per 50 m**, up to **600 points**. A stationary test may add no points; this is not evidence of broken storage. Export/retain the route before **Clear Data** or Factory Reset. [GPS](https://wiki.heltec.org/docs/platform/f\&t/qs/gps), [T1 Find Friend](https://wiki.heltec.org/docs/platform/f\&t/qs/find), [track recording](https://wiki.heltec.org/docs/platform/f\&t/qs/track), [compass/QuickPing](https://wiki.heltec.org/docs/platform/f\&t/qs/quick).

### Build and restore the exact model

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
# Select ONE environment matching the physical device:
pio run -e heltec-mesh-node-t1
# For T096 instead: pio run -e heltec-mesh-node-t096
```

Expected output is the selected model's artifact under `.pio/build/`; no compile was run. Preserve the configuration, original image and logs before flashing.

For UF2 recovery, connect USB, **double-press Power on T1** or **double-press RST on T096**, observe the mounted drive and copy only the exact model/application UF2. Wait for restart, reconnect, restore Region/channels and repeat the reply test. For F\&T, obtain the exact device image from DevRemote and perform the documented activation after copying. Never substitute the other model's UF2 or erase the bootloader as first-line recovery. [Model-specific flashing](https://wiki.heltec.org/docs/platform/f%26t/flash).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                    | Ordered checks                                                                                               |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| UF2 storage absent                         | Correct model's double-press control, USB data cable and observed bootloader; T1 Power differs from T096 RST |
| GNSS remains 0,0                           | Outdoors/sky view, actual power enable and current fix; preserve original LDS/stock antenna route            |
| T1 L5 unavailable                          | Stock L1 antenna limitation; chip capability alone does not change the RF path                               |
| T096 RF fails after generic sketch         | FEM supplies/control/calibration and exact target; T1 pin map is unrelated                                   |
| Find Friend/Compass absent on T096         | These F\&T pages are explicitly T1-only                                                                      |
| Track shows zero new points                | GPS Track enabled, valid fix, enough movement for current \~50 m logging rule and DevRemote correct device   |
| T1 LED/buzzer differs from manual          | Revision conflict; restore exact board driver and avoid raw P0.09 drive assumptions                          |
| F\&T image starts but features unavailable | Exact device firmware and manufacturer activation; this is independent of Meshtastic licensing               |

Does the T096 wiki's Wi-Fi bullet establish Wi-Fi hardware? The reviewed board is nRF52840/BLE plus LoRa/GNSS; no Wi-Fi interface was established. Do T1 and T096 share one binary? Their radio/display/power maps and targets are distinct.

## Downloads and technical documents

| Resource                                                                                                                                                                                             | Exact scope                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [T1 wiki](https://wiki.heltec.org/docs/devices/open-source-hardware/nrf52840-series/mesh-node-t1/) / [T1 datasheet](https://resource.heltec.cn/download/Mesh_Node_T1/Datasheet/Mesh-Node-T1.pdf)     | Assembled tag, controls, environment, L1 antenna footnote and display        |
| [T096 wiki](https://wiki.heltec.org/docs/devices/open-source-hardware/nrf52840-series/t096/) / [T096 datasheet](https://resource.heltec.cn/download/Mesh_Node_T096/Datasheet/Mesh%20Node%20T096.pdf) | PA/GNSS board, numbered headers, current conditions and revisions            |
| [T1 V1.0 schematic](https://resource.heltec.cn/download/Mesh_Node_T1/schematic/Mesh_Node_T1_V1.0.pdf)                                                                                                | Actual tag nets and power/sensor/antenna topology                            |
| [T096 V0.2 schematic](https://resource.heltec.cn/download/Mesh_Node_T096/Schematic/Mesh_Node_T096_V0.2.pdf)                                                                                          | FEM, header numbers, charging and GNSS antenna selection                     |
| [T1 resource center](https://resource.heltec.cn/download/Mesh_Node_T1/) / [T096 resource center](https://resource.heltec.cn/download/Mesh_Node_T096/)                                                | Model-specific firmware, GNSS/display/sensor and certification resources     |
| [F\&T full quick start](https://wiki.heltec.org/docs/platform/f%26t/qs/) / [flash/activation](https://wiki.heltec.org/docs/platform/f%26t/flash)                                                     | Controls, System/GPS, QuickPing, T1 heading/friend mode and track extraction |
| [Heltec nRF framework](https://github.com/HelTecAutomation/Heltec_nRF52/tree/b69d5fb6cc497555047467a36e7a256aa1b6bd56)                                                                               | Separate T1 and HT-n5262G board definitions and LoRaWAN examples             |

Manufacturer UC6580 reset UF2 and antenna-resistor modification resources exist, but clear receiver configuration or change hardware. They are excluded from first-line GNSS diagnosis until exact received-revision compatibility is confirmed. No exact mechanical CAD was located in the reviewed directories; dimensional figures remain linked in the model datasheets.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Both complete model datasheets/product pages, model wiki entries, separate firmware variants/environments and F\&T flash/activation plus all six operation pages were read. The T1/T096 schematics were visually inspected. The comparison and staged acceptance procedures distinguish model, application, radio, fresh GNSS, track spacing and recovery; unresolved optional electrical actions are stated beside their use.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
