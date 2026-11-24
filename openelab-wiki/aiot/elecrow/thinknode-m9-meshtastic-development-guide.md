---
description: >-
  Configure the 868 MHz ThinkNode M9 Meshtastic keyboard terminal, test two-way
  text, distinguish GNSS revisions and preserve maps before firmware updates.
---

# Elecrow ThinkNode M9 Meshtastic Engineering Guide

{% hint style="info" %}
[**View Elecrow ThinkNode M9 Meshtastic with 2.4inch LCD and Keyboard on OpenELAB**](https://openelab.io/products/elecrow-thinknode-m9-meshtastic-2-4inch-lcd-keyboard)

**Model / option:** 868MHz With Case · **SKU:** `ELECROW-LMM15409D-868`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

ThinkNode M9 LMM15409D is the **868 MHz standalone Meshtastic keyboard terminal**, with ESP32-S3, LR1110, color display and GNSS. The first useful result is a text message received by a second physical radio and a reply received on the M9. It is a different application from the [MeshCore M9](thinknode-m9-meshcore-development-guide.md); matching radio hardware does not make those protocols interoperable.

This guide follows Elecrow's **M9 V1.0 operation document dated 26 August 2026** and separately identifies changes in the pinned Meshtastic source. Preserve the working factory application before installing a development build. [Exact operation manual](https://www.elecrow.com/wiki/ThinkNode_M9_Meshtastic_Communication_Terminal_with_Full_Keyboard.html).

## Applications

Use M9 for local keyboard messaging, group channels, direct messages, position sharing and offline map experiments. A phone is optional for everyday messaging but useful for configuration and backups. Establish a direct pair before evaluating route tracing, relays or MQTT.

Record received packet time and the actual recipient. A node-list entry, send animation, Wi-Fi icon or old map marker proves a different state from current end-to-end delivery.

## Specifications

| Item                       | M9 V1.0 manual scope                                                              |
| -------------------------- | --------------------------------------------------------------------------------- |
| Main controller            | ESP32-S3-R8, up to 240 MHz; 8 MB PSRAM class                                      |
| Flash                      | ZD25Q128, 128 Mbit = 16 MB; not the old “16 GB” wording                           |
| Radio                      | LR1110; this purchased option is 868 MHz                                          |
| Display / keyboard         | 2.4-inch 320 × 240 TFT; dedicated keyboard coprocessor                            |
| GNSS                       | V1.0 manual: ATGM336H-5NR32 / BM72A; current source also handles AG3352 revisions |
| RTC / sensors              | PCF8563, QMC6309 magnetometer, QMI8658B motion sensor                             |
| Battery / input            | 2300 mAh rechargeable pack; USB-C charging/data                                   |
| Storage / local networking | microSD, 2.4 GHz Wi-Fi and BLE                                                    |

The manual does not establish a complete USB input-current rating or replacement-cell charging limits. Use the original pack and assembled USB path rather than adjusting the charger from its component formula. [Manufacturer specifications and pinout](https://www.elecrow.com/wiki/ThinkNode_M9_Meshtastic_Communication_Terminal_with_Full_Keyboard.html#13-hardware-architecture-and-specifications).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Occupied internal interfaces

Fit the correct antenna before radio use. Begin through USB-C without opening the enclosure or attaching external signals. These are internal MCU assignments, not a connector-contact drawing or permission to apply USB voltage to logic.

| Role                                     | ESP32-S3 GPIO / signal                              |
| ---------------------------------------- | --------------------------------------------------- |
| Shared SPI SCK / MOSI / MISO             | 40 / 47 / 38                                        |
| LR1110 CS / busy / IRQ / reset           | 39 / 41 / 42 / 45                                   |
| LCD CS / reset / DC / backlight / TE     | 16 / 14 / 15 / 17 / 19                              |
| microSD CS                               | 48; shared SPI                                      |
| GNSS host RX / TX / PPS / reset          | 2 / 3 / 4 / 5                                       |
| GNSS control / power enable              | 10 / 11; role/polarity depends on hardware revision |
| RTC/sensor I²C SDA / SCL                 | 7 / 6                                               |
| Keyboard host SDA / SCL / wake           | 20 / 21 / 12                                        |
| Peripheral enable / battery ADC / buzzer | 18 / 13 / 9                                         |
| Main BOOT / keyboard light               | 0 / 46                                              |

Keep LR1110 CS39, LCD CS16 and card CS48 inactive when another SPI device is selected. The pinned variant sets peripheral-enable GPIO18 active LOW and an LR1110 TCXO driver setting of 3.3 V; the latter is not a host GPIO voltage to inject. [Pinned variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M9/variant.h).

**Revision boundary:** the manual's keyboard table describes an ESP32-S2 and its own GPIO namespace. The current variant comments identify an STC8H keyboard. Its GNSS handling also changes GPIO11 polarity by detected M9 version and uses GPIO10 as an AG3352 sleep interrupt. Therefore this guide excludes keyboard-coprocessor flashing, raw GNSS power/configuration commands and connector modifications until the received assembly is matched. Normal supplied UI, USB and radio operation do not need those procedures.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

### Match the application as well as the board

The reviewed Meshtastic commit is **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**. It provides `thinknode_m9` and the standalone device-UI environment **`thinknode_m9-tft`**. The TFT environment adds the UI dependencies, 320 × 240 view and FTP/storage configuration; the generic environment is not proof of identical factory UI behavior. Both select the M9 pin map, 16 MB partition layout and LR1110. [Exact environments](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M9/platformio.ini).

The variant requests LR1110 firmware `0x0402` because some shipped `0x0303` transceivers cannot receive 500 kHz LoRa presets. That is a source-specific transceiver update path, not an instruction to flash an arbitrary LR1110 binary. Preserve its implementation and use a released M9 target rather than bypassing the update. Start with a mutually supported normal preset before investigating Turbo-only failures.

Meshtastic source is GPL-3.0; dependency licenses remain separate. Keep upstream revisions and notices. The released flasher must explicitly offer M9 and the intended UI/application before use; a generic ESP32-S3 image is insufficient.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original two-radio acceptance record

Prepare the charged M9, correct antenna, a compatible Meshtastic peer and clients as needed. Keep the installed standalone firmware for the first pass.

1. Start M9 and record hardware/application version and node ID. Use Home, Chat, Back and navigation-center to verify local controls. Enter a harmless unsent text string, edit it and clear it to separate keyboard faults from radio faults.
2. In Settings select the permitted Region, a compatible modem preset and primary channel, then **OK** and restart if requested. Match the peer's frequency slot and complete channel name/key. Leave frequency overrides at normal defaults unless the network requires them.
3. Open a group channel, type `M9-MT-A-01`, press Enter/send and confirm reception on the peer. Return `M9-MT-B-01` and confirm the M9 receives it. Record both receive times and available RSSI/SNR.
4. Repeat five numbered pairs. Inspect Packet Log/Statistics when a reply is missing; distinguish a locally queued outgoing entry from a received frame. Keep diagnostics sparse because requests also occupy airtime.
5. Select a freshly heard peer in Node List and hold to open a direct message where the installed UI supports it. Exchange a second unique pair. Keep the normal **CLIENT** role during the baseline rather than assigning router roles to every handheld.
6. Disconnect USB and repeat a reply. Only then enable device GNSS outdoors and verify a fresh fix/time before sharing location.

**Expected result:** independently observed group and direct receipts in both directions, followed by a separate current GNSS position. A stale node entry or position is not acceptance. [Controls, chat and radio settings](https://www.elecrow.com/wiki/ThinkNode_M9_Meshtastic_Communication_Terminal_with_Full_Keyboard.html#3-meshtastic-operation).

### Maps, BLE and maintenance as separate checkpoints

The Positioning key sends a temporary position ping; a roughly 3-second hold toggles GNSS in the documented UI. On the map, navigation pans, **Sym+O / Sym+I** zoom, and a center hold opens settings. First browse an existing tile, then center on a fresh fix. Back up the factory microSD contents before replacing the card; map directory/format must match the installed release. Do not invent a universal tile path from a different terminal.

For phone configuration, open **Settings & Tools → Settings → Reboot / Shutdown → Bluetooth icon**. After restart, use the displayed **Programming mode** number to pair the actual M9. Hold navigation-center to leave that mode. Remove old phone/app pairing records if the number is rejected; screenshot PINs are examples, not credentials.

Wi-Fi enabling is distinct from obtaining an IP and Internet access. MQTT also needs correct server/authentication/uplink/downlink settings; FTP exposes a local storage service when enabled. Leave both off for the isolated radio trial. Home-page alerts, brightness, time/uptime, coordinates, SD state and heap/LVGL display can be checked individually without changing radio parameters.

Before any update use **Settings → Backup & Restore**, copy map/media files, retain the working version and protect backups containing channel keys. Select a released image explicitly supporting the received M9 and UI. Maintain power, wait for completion, restore Region/channels and repeat the two-way test. No guessed raw flash offset or keyboard recovery image is supplied here.

### Unchanged-source build checkpoint

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e thinknode_m9-tft
```

Expected output is a target-specific artifact under `.pio/build/thinknode_m9-tft/`; this build was not run. Read its log and release support before upload. Successful compilation alone would not validate the keyboard/GNSS revision.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                             | Ordered checks                                                                                                             |
| ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| App cannot find M9                  | Enter documented Bluetooth programming mode, use its current PIN, remove stale pairings and grant nearby-device permission |
| Node visible but no reply           | Fresh last-heard time, complete channel key/slot, Region/preset/slot, actual receiving peer and Packet Log                 |
| Only 500 kHz presets fail           | Record host/transceiver versions; reviewed source handles LR1110 `0x0303` limitation through its exact update path         |
| Blank map with valid GNSS           | SD detection, backed-up tile data, directory/format, coverage and zoom; test an existing tile                              |
| Map works but no fix                | GNSS enable, open sky, fresh timestamp and actual receiver revision; do not send another model's commands                  |
| Card fails after custom firmware    | CS48 and shared SPI selection; power down before reseating                                                                 |
| Wi-Fi icon but online service fails | 2.4 GHz SSID, credentials, IP/router access; MQTT configuration is an additional dependency                                |

Can this exchange messages with the MeshCore M9 unchanged? No: the application protocol must match. Can a supplied screenshot's EU/US frequency be copied? Select the operating jurisdiction and received RF band; screenshots do not define a universal plan.

## Downloads and technical documents

| Resource                                                                                                                                                                      | Scope                                                                                          |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| [Complete M9 Meshtastic manual](https://www.elecrow.com/wiki/ThinkNode_M9_Meshtastic_Communication_Terminal_with_Full_Keyboard.html)                                          | V1.0, 26 August 2026; all pin tables, UI, maps, app mode, storage, maintenance and diagnostics |
| [Pinned variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M9/variant.h)              | Actual GNSS revision logic, SPI/TCXO and transceiver update definition                         |
| [Build/UI configuration](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M9/platformio.ini) | Standard versus standalone TFT environments and dependencies                                   |
| [Meshtastic downloads](https://meshtastic.org/downloads/) / [flasher](https://flasher.meshtastic.org/)                                                                        | Confirm exact model/application availability before installation                               |

The manual includes subsystem diagrams and application screenshots. Its complete net tables are useful references but do not substitute for received-revision mechanical CAD or an independently inspected complete PCB drawing.

### Additional existing resources

* [Official Meshtastic hardware support](https://meshtastic.org/docs/hardware/devices/elecrow/thinknode/)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The complete manufacturer operation guide and pinned M9 variant/build files were read. Source revision differences are disclosed beside the affected operations. The staged acceptance record, separate UI/RF/GNSS checkpoints and unchanged-source build command are original procedures; their outputs are expected, not measured.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
