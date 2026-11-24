---
description: >-
  Set up the HELTEC V4-R8 Expansion Kit V2 touchscreen, select TFT firmware,
  test two-way messages and distinguish BLE, GNSS and map failures.
---

# HELTEC WiFi LoRa 32 Expansion Kit V2 Engineering Guide

{% hint style="info" %}
[**View HELTEC WiFi LoRa 32 Expansion Kit V2 for V4-R8 Touch GNSS on OpenELAB**](https://openelab.io/products/heltec-wifi-lora-32-expansion-kit-v2-v4-r8-touch-gnss)

**Model / option:** Default Title · **SKU:** `HT-ExpansionT-V2`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

WiFi LoRa 32 Expansion Kit **V2** is the assembled **V4-R8 touchscreen** platform: ESP32-S3 with 8 MB PSRAM, SX1262/FEM radio, 2.8-inch TFT/touch, GNSS, buzzer and microSD. It includes the V4 board and installed accessories; it is not an empty case or the older R2/V1 kit. Use the **`heltec-v4-r8-tft`** firmware target.

The first test separates local touch, two-way mesh text and a fresh GNSS fix. Firmware for V1 or the R8 OLED bare board is not equivalent. [Manufacturer V2 guide and FAQ](https://heltec.org/project/v4-r8-ex/), [bare R2/R8 guide](heltec-wifi-lora-32-v4.3.1-sx1262-engineering-guide.md).

## Applications

Use the kit for a standalone Meshtastic UI, offline maps, GNSS position reporting and controlled field messaging. Establish a direct two-node link before evaluating routing or high RF output. A touchscreen event, GNSS fix, BLE connection and peer packet receipt are four independent checkpoints.

The manufacturer explicitly says the enclosure is **not waterproof**. A rugged metal base does not make it a sealed outdoor node.

## Specifications

| Item                        | V2 R8 touchscreen kit                                           |
| --------------------------- | --------------------------------------------------------------- |
| Host / memory               | ESP32-S3-R8; 8 MB PSRAM, 16 MB flash board                      |
| Radio                       | SX1262 with KCT8103L PA/LNA in reviewed V4.3 source             |
| Display                     | 2.8-inch TFT; 240 × 320 portrait in target                      |
| Touch                       | I²C `0x2E` in reviewed target                                   |
| GNSS                        | Quectel L76K accessory; host TX38/RX39                          |
| Card                        | microSD on display SPI bus, CS3                                 |
| Enclosure                   | Touch front; aluminum sides/rear; no waterproofing              |
| Battery                     | Optional flat-top 18650; manufacturer specifies 3.3–4.2 V       |
| Optional pack / listed mass | 2800 mAh option; 200 g excluding battery, manufacturer reported |

The manufacturer lists 52 × 52 × 15 mm but also a 2.8-inch screen; verify received mechanical dimensions before designing a mount rather than using this inconsistent listing as a fabrication drawing. Battery inclusion depends on the ordered option and must be checked against the actual package. [Kit specification/purchasing scope](https://heltec.org/project/v4-r8-ex/).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Assembled power and occupied buses

Use the assembled USB-C input and a regulated 5 V source for commissioning. Keep the original battery polarity/protection path intact. Do not assume a mating SH1.25 connector establishes cell polarity or add an independent 5 V header supply while USB is attached. The V4 board's solar/battery circuits are not permission to feed USB voltage into 3.3 V signals.

| Function                         | V2 R8 target GPIO                        |
| -------------------------------- | ---------------------------------------- |
| Radio SCK / MOSI / MISO / CS     | 9 / 10 / 11 / 8                          |
| Radio reset / IRQ / busy         | 12 / 14 / 13                             |
| Display/card SCK / MOSI / MISO   | 16 / 15 / 45                             |
| TFT CS / DC / backlight / reset  | 47 / 48 / 44 / 21                        |
| microSD CS                       | 3                                        |
| Touch SDA / SCL                  | 17 / 18; no separate INT/reset in target |
| GNSS host TX / RX / PPS / enable | 38 / 39 / 41 / 42; enable active LOW     |
| Buzzer / secondary button        | 4 / 46                                   |
| Vext / battery ADC               | 40 active LOW in source / 1              |

The radio and display/card use different SPI assignments; keep each non-target CS inactive. Do not transfer R2 kit routing to this board. The FEM additionally reserves GPIO7, GPIO2 and GPIO5 for supply/control. Its PA calibration and DIO2 switching must remain under the exact board driver; a generic SX1262 power setting is not the kit's calibrated antenna output. TCXO is configured to 1.8 V by the radio driver, not externally injected. [Exact variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4_r8/variant.h), [TFT pin/dependency configuration](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4_r8/platformio.ini).

The **V2.03 expansion schematic** is useful for connector labels, card, GNSS and supply topology, but contains optional/alternate signal annotations. It is not authority to transplant an older expansion routing onto the actual R8 assembly. Obtain received-revision connector contact orientation and sensor power budgets before wiring B2B expansion. Raw Vext/ADC gate code is excluded because R8 documents disagree with its firmware; the supplied target handles those paths. [Official expansion drawing](https://resource.heltec.cn/download/WiFi_LoRa_32_Expansion_Kit-V2/schematic/Expansion_board_V2.03.pdf).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Use Meshtastic target **Heltec V4 R8 TFT**, not R2, V1 or R8 OLED. The reviewed source commit is **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**, environment **`heltec-v4-r8-tft`**. It selects a 16 MB partition scheme, LovyanGFX 1.2.28, pinned CHSC6x touch driver and device-UI dependencies. Keep these together.

The manufacturer download directory currently lists `firmware-heltec-v4-r8-tft-2.7.26.54e0d8d.factory.bin`. A `factory.bin` has a specific bundled layout; do not write it at a guessed offset. The official flasher or exact vendor instructions must select the correct target/layout. MeshCore support is separately described as awaiting merge/temporary downloads; the existence of that file does not establish the same UI or official support level.

Meshtastic is GPL-3.0; dependencies retain their own notices. The factory UI and BLE companion mode differ as described below; do not diagnose absent BLE in touch mode as a failed antenna.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original staged acceptance

Prepare the assembled kit, supplied LoRa antenna, USB data cable and a compatible Meshtastic peer. Preserve the supplied image/configuration.

1. Fit the antenna, connect USB-C and verify startup reports the R8 TFT application. Record firmware, region and physical node identity. Inventory the optional battery and GNSS accessory rather than relying on a generic packing photo.
2. Open two local menus and verify fresh touch selections. Check brightness and return navigation. A lit panel without responding coordinates calls for the TFT/touch target, not changed radio settings.
3. Set the permitted Region and match modem preset, frequency slot and complete channel name/key on the peer. Wait for required restart.
4. Send `KIT-V2-A-01`, observe receipt at the peer, return `KIT-V2-B-01` and confirm receipt on the kit. Repeat five numbered pairs and record each receiver's timestamp/RSSI/SNR.
5. Enable device GNSS outdoors and inspect fresh fix/time independently. Test an existing offline map tile with the card recognized, then center on the current position. Back up card data before reformatting or replacing it; use the installed release's actual map format/directories.
6. If a battery is fitted, disconnect USB and repeat a reply. Check a new screen update and GNSS state; do not treat an unchanged display as proof the battery path works.

**Expected result:** repeatable touch operation, confirmed text in both directions and a separate fresh fix/map checkpoint. No radio range or battery runtime has been measured here. [Manufacturer kit operation/FAQ](https://heltec.org/project/v4-r8-ex/).

### Bluetooth modes and audio diagnostics

The documented touch mode does **not** offer Bluetooth companion operation. At the shutdown page's Bluetooth icon, a **long press** selects BASE UI for companion mode; a **short press** selects programming mode, described as a Bluetooth firmware-update mode. Record the installed release and actual screen before selecting a mode. Pair with the current displayed/configured credentials and return to touch mode separately.

The vendor reports that initial GNSS identification can disturb buzzer timing for about a minute. First wait for GNSS acquisition and retest a known notification; do not immediately replace the buzzer or alter its drive voltage. LNA options are firmware/version-specific: the manufacturer describes Meshtastic System → LoRa settings and different temporary MeshCore builds, not one universal toggle.

### Development and recovery

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e heltec-v4-r8-tft
```

Expected output is a TFT-specific artifact under `.pio/build/heltec-v4-r8-tft/`; no compile was run. Before flashing, back up channels/configuration and card files, confirm the exact received target and preserve the known-good released image.

For documented USB download entry: connect USB-C, hold **USER**, press/release **RST**, then release USER. Use the supported flasher with the exact V2/R8 TFT image, wait for completion and press RST to run. Re-select a changed serial port, restore Region/channels and repeat the reply test. Keep V1 and OLED images out of this restore path.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                | Ordered checks                                                                                                          |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Display works, BLE absent              | Touch versus BASE UI versus programming mode; current release and credentials                                           |
| Display/touch/card breaks after update | R8 TFT target, SPI16/15/45, TFT CS47, card CS3, touch GPIO17/18 and coherent dependencies                               |
| Text works, map blank                  | Card detection, actual map data/format/coverage and free space; GNSS is a separate centering dependency                 |
| No GNSS fix                            | L76K assembly/antenna, enable GPIO42, host RX39/TX38, open sky and current time                                         |
| Unusual buzzer at startup              | Vendor-reported GNSS timing interaction, then a controlled notification after acquisition                               |
| RF problems after custom code          | Exact FEM/power implementation, received RF band, antenna and peer settings; do not apply bare SX1262 power assumptions |
| Firmware will not start                | Correct V2 factory layout, stable USB, USER/RST entry and exact target; preserve old version for restore                |

Is the metal case waterproof? The manufacturer says no. Is a V1 binary compatible? The manufacturer explicitly says V2 and V1 firmware are not interchangeable.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                                                      | Scope                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [V2 product/manual/FAQ](https://heltec.org/project/v4-r8-ex/)                                                                                                                                                                                                                                                                 | Kit contents, controls, BLE modes, battery and enclosure limitations      |
| [V2.03 expansion schematic PDF](https://resource.heltec.cn/download/WiFi_LoRa_32_Expansion_Kit-V2/schematic/Expansion_board_V2.03.pdf)                                                                                                                                                                                        | GNSS/card/battery topology and labeled connector drawings; match revision |
| [V2 resource center](https://resource.heltec.cn/download/WiFi_LoRa_32_Expansion_Kit-V2/)                                                                                                                                                                                                                                      | Model-specific schematic and firmware directories                         |
| [Meshtastic factory downloads](https://resource.heltec.cn/download/WiFi_LoRa_32_Expansion_Kit-V2/firmware/Meshtastic)                                                                                                                                                                                                         | Exact R8 TFT factory files, not V1 binaries                               |
| [Pinned variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4_r8/variant.h) / [build configuration](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4_r8/platformio.ini) | Board/FEM and TFT/touch/card support                                      |

The expansion drawing is attributed to Heltec and should be read with the board revision, not used as an unqualified generic sensor pinout.

### Additional existing resources

* [HELTEC documentation](https://wiki.heltec.org/docs/platform/f%26t/flash)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The complete V2 manufacturer page/FAQ, download inventory and exact firmware variant/build configuration were read. The V2.03 drawing was visually inspected. The original staged test distinguishes UI, RF, GNSS, storage, BLE mode and battery behavior; optional connector modifications remain bounded.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
