---
description: >-
  Choose the correct HELTEC V4-R2 or V4-R8 OLED firmware, power and FEM
  configuration, then verify a two-node link and safe USB recovery.
---

# HELTEC WiFi LoRa 32 V4.3.1 SX1262 Engineering Guide

{% hint style="info" %}
[**View HELTEC WiFi LoRa 32 V4.3.1 SX1262 LoRa Node Meshtastic LoRaWAN without GPS module version on OpenELAB**](https://openelab.io/products/heltec-wifi-lora-32-v4-sx1262-lora-node-meshtastic-lorawan-gps)

**Model / option:** WiFi LoRa 32 V4-R8 · **SKU:** `HT-LoRa32V4-R8`

[**View HELTEC WiFi LoRa 32 V4.3.1 SX1262 LoRa Node Meshtastic LoRaWAN without GPS module version on OpenELAB**](https://openelab.io/products/heltec-wifi-lora-32-v4-sx1262-lora-node-meshtastic-lorawan-gps)

**Model / option:** WiFi LoRa 32 V4-R2 · **SKU:** `HT-LoRa32V4`
{% endhint %}

## Product overview

### R2 and R8 hardware scope <a href="#what-is-the-heltec-wifi-lora-32-v4.3.1" id="what-is-the-heltec-wifi-lora-32-v4.3.1"></a>

WiFi LoRa 32 V4 combines ESP32-S3, SX1262 and a power-amplifier/low-noise-amplifier front end. **HT-LoRa32V4-R8** is the 8 MB PSRAM board; **HT-LoRa32V4** is the 2 MB PSRAM R2 option. Their common product URL does not make their pin use or firmware identical. This canonical page covers both OLED board options and keeps the [V2 touchscreen kit](heltec-wifi-lora32-expansion-kit-v2-development-guide.md) separate.

### GNSS inventory and first-test scope <a href="#quick-summary" id="quick-summary"></a>

The live store title now says “GPS Included,” while the original row described no GPS and the manufacturer's bare-board list provides a GNSS connector. Inventory any delivered GNSS accessory separately; a connector is not proof of a receiver. The first radio test below needs no GNSS wiring. [Current manufacturer variants](https://heltec.org/project/wifi-lora-32-v4/).

## Applications

Use the board for a two-node mesh link, an explicitly supported LoRaWAN end device, or a private LoRa telemetry experiment. Meshtastic, MeshCore and LoRaWAN are different firmware/network paths. Start with one and preserve its known-good version before switching.

For solar work, measure the assembled workload and charging behavior over complete cycles. The high-power radio stage changes both current demand and the relation between a chip-level output setting and actual RF output; a generic SX1262 demo is not a complete V4 power-control implementation.

## Specifications <a href="#key-specifications" id="key-specifications"></a>

| Parameter            | V4-R2                                                           | V4-R8                                                          |
| -------------------- | --------------------------------------------------------------- | -------------------------------------------------------------- |
| Exact SKU            | HT-LoRa32V4                                                     | HT-LoRa32V4-R8                                                 |
| Host / PSRAM         | ESP32-S3R2 /2 MB                                                | ESP32-S3R8 /8 MB                                               |
| External flash       | 16 MB                                                           | 16 MB                                                          |
| Bare-board display   | SSD1315 0.96-inch 128 × 64 OLED                                 | Same OLED class; not the TFT kit                               |
| Radio                | SX1262 plus revision-specific FEM                               | SX1262 plus KCT8103L FEM in reviewed source                    |
| High-band hardware   | 863–928 MHz product family; configure a permitted regional plan | Same family; use the received RF option                        |
| Published RF ceiling | 28±1 dBm high-power family                                      | 28±1 dBm high-power family                                     |
| USB / solar supply   | 5 V nominal; datasheet range 4.7–6 V                            | 5 V nominal; datasheet range 4.7–6 V                           |
| Battery              | Single-cell lithium, 3.3–4.2 V                                  | Single-cell lithium, 3.3–4.2 V                                 |
| Board dimensions     | 51.7 × 25.4 × 10.7 mm                                           | Same nominal form factor; use exact CAD/board revision for fit |

Sources: [R2 Rev1.4 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/datasheet/WiFi_LoRa_32_V4.2.0.pdf), [R8 Rev1.1.0 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4-R8/datasheet/WiFi_LoRa_32_V4R8.pdf), [current product page](https://heltec.org/project/wifi-lora-32-v4/). The older sheet lists broader silicon/board temperature limits than the current product's −20 to +70 °C; use the current product scope and the battery's separate charging limits. Neither range guarantees charging suitability.

At 25 °C the data sheets list roughly 75 mA RX, 750 mA at a 27 dBm transmit condition, 500 mA USB charging, 2 mA USB sleep and 20 µA battery sleep. These are manufacturer mode figures, not independently measured current or a promise that a 500 mA USB port supports simultaneous high-power TX and charging.

## Hardware and connections

### Supply and connector boundaries

Use regulated 5 V USB-C for first setup. Do not connect USB and an independent 5 V header supply together. Battery and solar inputs may coexist as the documented charger arrangement, but verify SH1.25-2P polarity against PCB markings before attaching a cell/panel. A mating connector alone does not establish polarity. Do not apply USB5 V to 3.3 V logic or bypass the charging path. The old guide's 4.4 V battery maximum is replaced here by the current 4.2 V limit.

Attach the matched LoRa antenna before radio use. The 2.4 GHz FPC/IPEX path is a separate network. Keep the factory FPC route intact for first setup; the V4.2 and V4.3 RF resistor modifications differ. Do not bridge both routes as a routine troubleshooting step. [Product hardware/antenna notes](https://heltec.org/project/wifi-lora-32-v4/).

| Internal function       | R2 reviewed source          | R8 reviewed source                             |
| ----------------------- | --------------------------- | ---------------------------------------------- |
| SX1262 SCK/MISO/MOSI/CS | 9/11/10/8                   | 9/11/10/8                                      |
| Reset/IRQ/busy          | 12/14/13                    | 12/14/13                                       |
| OLED SDA/SCL/reset      | 17/18/21                    | 17/18/21                                       |
| Vext control            | 36, active LOW              | 40, active LOW in firmware                     |
| LED                     | 35                          | 46                                             |
| Battery ADC             | 1; gate GPIO37 in R2 source | 1; **no ADC gate GPIO37 defined** in R8 source |
| GNSS host TX/RX/PPS     | 38/39/41                    | 38/39/41                                       |
| GNSS enable             | 34, active LOW              | 42, active LOW                                 |
| User/BOOT               | 0                           | 0                                              |

Exact sources: [R2 variant](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4/variant.h), [R8 variant](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4_r8/variant.h). These are MCU identities, not a connector contact-order diagram. R8 reserves more memory-related pins; do not reuse R2 “free GPIO” assumptions.

### Hardware Revision Notes <a href="#hardware-revision-notes" id="hardware-revision-notes"></a>

**R8 document conflicts:** its datasheet repeats the R2 GPIO37 ADC note and says Vext GPIO40 should be HIGH, while the reviewed firmware marks Vext GPIO40 active LOW. The later R8 V4.3.2 schematic shows the switched path; it is a later revision than the store's V4.3.1 naming. Use the stock exact-board implementation for this first result; custom Vext loads or a raw ADC-control routine are excluded until the received revision is matched. The divider drawing uses 390 kΩ/100 kΩ, so the ideal battery reconstruction is approximately `Vbat=4.9×Vadc`, not the inverted formula printed in the table; actual ADC calibration remains board-specific. [R8 schematic](https://resource.heltec.cn/download/WiFi_LoRa_32_V4-R8/Schematic/HTIT-WBR8H_V4.3.2.pdf).

V4.2 uses GC1109 and V4.3 uses KCT8103L. The current Arduino instructions require **USE\_GC1109\_PA** or **USE\_KCT8103L\_PA** accordingly. The FEM handles PA/LNA paths and its output calibration; do not wire generic TXEN/RXEN over its control signals. Both reviewed radio variants use DIO2 switching and a 1.8 V TCXO setting. [Current wiki](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/lora-32/wifi-lora-32-v4/).

## Software and development resources

### Meshtastic, MeshCore, and LoRaWAN <a href="#meshtastic-meshcore-and-lorawan" id="meshtastic-meshcore-and-lorawan"></a>

| Hardware/application    | Reviewed Meshtastic source environment |
| ----------------------- | -------------------------------------- |
| R2 OLED board           | `heltec-v4`                            |
| R8 OLED board           | `heltec-v4-r8-oled`                    |
| R8 Expansion Kit V2 TFT | `heltec-v4-r8-tft`, separate kit guide |

The source snapshot is `d0f4096788545fb3c5e22d2a7e52ac6c268caac1`; [R2 environments](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4/platformio.ini) and [R8 environments](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_v4_r8/platformio.ini) also define the 16 MB partitioning. The manufacturer's minimum-version guidance differs: R2 Meshtastic above 2.7.20, R8 above 2.7.25; choose a current release explicitly offering the correct target. Do not select touchscreen “Meshtastic UI” for an ordinary OLED board.

For Arduino, the observed **Heltec-esp32 board package 3.3.8** is listed in the official package index. Add that index, install the package/library, reload board data and select the V4 board/memory/FEM options matching the received revision. Package availability is source-verified; SDK installation/build was not run. Legacy docs redirect to the current wiki. LoRaWAN examples additionally require a suitable network server, activation keys, frequency plan and any Heltec library license; Meshtastic keys are not LoRaWAN credentials.

MeshCore requires an exact R2/R8 and hardware-generation image. The manufacturer's temporary firmware archives and LNA-specific builds are version-bound resources, not interchangeable defaults. Preserve the package release and read its target before any update.

## Getting started

### First radio result without external wiring <a href="#radio-antenna-and-regulatory-checklist" id="radio-antenna-and-regulatory-checklist"></a>

Prepare a known-good 5 V data connection, matched antenna and a second compatible Meshtastic radio. Start with installed firmware when it already runs the desired application.

1. Inspect the board's R2/R8 and hardware revision markings. Read the installed identity over the supported serial/BLE client and save the version/configuration. Confirm an OLED target rather than a TFT kit build.
2. Select the permitted region, wait for restart, and match the peer's modem preset, frequency slot and channel name/key. Keep the FEM-aware target's power behavior; do not override it with a chip-level 22/28 dBm assumption.
3. Send `V4-A-01`, observe it at the peer, then return `V4-B-01`. Keep both receive timestamps and available RSSI/SNR. Repeat with unique sequence numbers before increasing separation.
4. Check OLED updates independently from BLE and radio receipts. If custom firmware fails only on battery, inspect board-specific peripheral power rather than borrowing a V3/V4-R2 pin definition.
5. Add GNSS only after identifying the delivered accessory, connector orientation and matched power-control implementation. Verify fresh receiver data outdoors separately from text reception.

**Expected result:** exact board identity, a live OLED and two received text messages in opposite directions. A factory “LORA ERROR” can mean its test application found no matching factory-test peer; inspect firmware identity before diagnosing damaged hardware. [Product FAQ](https://heltec.org/project/wifi-lora-32-v4/).

### Firmware and Development Workflow <a href="#firmware-and-development-workflow" id="firmware-and-development-workflow"></a>

The command below selects R8 OLED. For R2 use `heltec-v4`; never substitute the TFT environment just to obtain a UI option.

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e heltec-v4-r8-oled
```

Expected build output is a target-specific artifact under `.pio/build/heltec-v4-r8-oled/`; no successful compilation is claimed. First build unchanged source and inspect the target/configuration before any upload.

### USB recovery

Export configuration before erasing. Connect USB-C, hold PRG, press/release RST, then release PRG. Select the exact board/application in the supported flasher and the newly observed USB port. Flash only its documented image/partition layout, reset afterward and repeat the identity/reply test. Do not apply an assumed raw offset to an app-only binary. [Manufacturer recovery instructions](https://heltec.org/project/wifi-lora-32-v4/).

### Field Deployment Checklist <a href="#field-deployment-checklist" id="field-deployment-checklist"></a>

Use the same known-good firmware/radio configuration for a bench-to-field comparison:

1. Record R2/R8 identity, received PCB revision, firmware target, antenna and any GNSS accessory. Keep a recoverable image/configuration locally.
2. Repeat a short direct message/reply at the bench, then at the intended mounting location. Log actual receiver times, missed replies and RSSI/SNR; do not compare only local send histories.
3. With a suitable cell and verified connector polarity, measure sleep, receive and transmit peaks at the battery boundary. USB sleep and battery sleep include different circuits.
4. For the documented solar charger path, record panel voltage under useful light, charging state, battery trend, shading, local temperature and message/GNSS workload over full day/night cycles. The 4.7–6 V input range and 4.2 V cell maximum remain applicable; a connector does not establish panel polarity.
5. Recheck enclosure moisture protection, cable strain, antenna clearance from metal and access for service. The bare board is not a sealed outdoor product. Do not leave it inaccessible until battery trends support the intended workload.

**Expected result:** a repeatable baseline and a measured energy/delivery record for the actual assembly. No autonomous-runtime or range claim is made from the board's headline sleep/current values.

### Engineering Best Practices <a href="#engineering-best-practices" id="engineering-best-practices"></a>

Change one interface at a time. If a sensor addition breaks RF, compare the last working build, pin ownership, Vext state and peak supply voltage before changing modem parameters. If GNSS alone fails, keep the established radio profile fixed and inspect the installed accessory, host UART and receiver-specific driver. A direct LoRa project must match bandwidth, spreading factor, coding rate, sync word, preamble, CRC and IQ inversion at both endpoints; Meshtastic and LoRaWAN manage those through their own application configuration.

## Troubleshooting and FAQs

### FAQ <a href="#faq" id="faq"></a>

**What changed from V3?** V4 changes flash/PSRAM options, native USB behavior, the PA/LNA path, antenna routing and solar/GNSS expansion. The R2/R8 memory and occupied-pin distinctions in this guide must also be preserved; familiar dimensions do not make the firmware interchangeable.

**Does a GNSS connector mean GPS is installed?** No. The live listing's title changed, while the manufacturer describes a connector/accessory path. Inventory the received module and confirm a fresh fix separately from text delivery.

**Can MeshCore, LoRaWAN and Meshtastic share a binary?** They are separate firmware/application paths. Select exact R2/R8 and intended UI support, preserve a working release and retest the direct result after switching.

| Symptom                              | Useful diagnosis                                                                                                              |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| OLED black after flashing            | R2 versus R8 and OLED versus TFT target; do not select touchscreen UI for OLED                                                |
| Radio fails only at higher settings  | Supply sag, antenna, exact FEM revision and calibration; do not raise power to diagnose it                                    |
| App works but no peer messages       | Protocol, complete RF preset/channel key, receiving device and actual replies                                                 |
| Battery reading implausible          | R2 ADC gate versus R8 implementation, divider direction and calibration; do not drive R8 GPIO37 from the copied note          |
| GNSS absent                          | Is a receiver actually supplied/fitted? Verify its connector and R2/R8 enable pins; bare GNSS connector alone is insufficient |
| Sleep current much higher than 20 µA | Measurement boundary, USB path, active OLED/GNSS/FEM and actual firmware sleep state                                          |
| LNA changes reception                | Record firmware/hardware and RF environment; compare packets rather than assuming higher gain always improves a noisy site    |

V3's similar shape does not establish compatible flash, pin reservations, power mapping or PA calibration. Custom power loads remain outside this first-result scope until the exact board revision is confirmed.

## Downloads and technical documents <a href="#official-resources-and-downloads" id="official-resources-and-downloads"></a>

| Resource                                                                                                                                                                                                              | Version/scope                                                                                                                                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Current product](https://heltec.org/project/wifi-lora-32-v4/) /[current wiki](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/lora-32/wifi-lora-32-v4/)                                       | R2/R8 comparison, FEM selection, firmware/antenna/FAQ notes                                                                                                                          |
| [R2 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/datasheet/WiFi_LoRa_32_V4.2.0.pdf) /[R2 V4.3 schematic](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/Schematic/HTIT-WB32LAF_V4.3.pdf)       | Older R2 data and V4.3 circuit; do not transfer all pins to R8                                                                                                                       |
| [R8 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4-R8/datasheet/WiFi_LoRa_32_V4R8.pdf) /[R8 V4.3.2 schematic](https://resource.heltec.cn/download/WiFi_LoRa_32_V4-R8/Schematic/HTIT-WBR8H_V4.3.2.pdf) | R8-specific resources; apply ADC/Vext conflicts above                                                                                                                                |
| [R2 resource center](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/) /[R8 resource center](https://resource.heltec.cn/download/WiFi_LoRa_32_V4-R8/)                                                             | Pin maps, firmware, data sheets and revision-specific schematics                                                                                                                     |
| [R2 mechanical files](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/3D/)                                                                                                                                        | Mechanical resource directory; verify R8 physical fit separately                                                                                                                     |
| [Historical V4 pin-map URL](https://heltec.org/wp-content/uploads/2025/09/V4_pinmap-scaled.png)                                                                                                                       | Retained older V4/R2-context reference; this URL served HTML rather than the drawing at review. Use the revision-specific R2/R8 resources above; do not transfer an R2 pin map to R8 |
| [Board package index](https://resource.heltec.cn/download/package_heltec_esp32_index.json)                                                                                                                            | Observed Heltec-esp32 v3.3.8; Arduino package configuration                                                                                                                          |
| [Heltec library](https://github.com/HelTecAutomation/Heltec_ESP32)                                                                                                                                                    | Factory/display/LoRaWAN examples and licenses                                                                                                                                        |

The retained technical links below also expose the ESP32-S3, SX1261/2 and SSD1315 component documents, LoRaWAN/mesh introductions and earlier example/manual resources. They are references, not proof that every historical example supports every V4 option.

### Project References and Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

The Heltec mesh-node application collection and MeshSolar reference below are useful for thinking about fixed-node placement and energy balance. They are **other projects**, not electrical or firmware authorities for this R2/R8 board. MeshPocket illustrates an assembled handheld form factor; it does not establish V4 charging or antenna wiring. For a new sensor project, begin with a documented 3.3 V interface and a local decoded reading, then add sparse telemetry and confirm the exact payload at the receiver/server before field mounting.

* [Heltec documentation](https://docs.heltec.org/en/node/esp32/wifi_lora_32/index.html)
* [ESP32-S3 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/datasheet/esp32-s3_datasheet_en.pdf)
* [SX1261/2 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/datasheet/SX1261_2%20V2-2.pdf)
* [SSD1315 datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/datasheet/SSD1315_1.0_withcomand_.pdf)
* [Heltec ESP32 Series Quick Start](https://docs.heltec.org/en/node/esp32/esp32_general_docs/quick_start.html)
* [WiFi LoRa 32 example manual](https://docs.heltec.org/en/node/esp32/wifi_lora_32/example.html)
* [Heltec ESP32 framework](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series)
* [Heltec LoRaWAN sample](https://docs.heltec.org/en/node/esp32/esp32_general_docs/lorawan/index.html)
* [Heltec Meshtastic Introduction](https://docs.heltec.org/en/node/esp32/esp32_general_docs/meshtastick.html)
* [Meshtastic Web Flasher](https://flasher.meshtastic.org/)
* [Meshtastic LoRa32 peripherals](https://meshtastic.org/docs/hardware/devices/heltec-automation/lora32/peripherals/)
* [MeshCore](https://meshcore.co.uk/)
* [MeshCore flasher](https://flasher.meshcore.co.uk/)
* [heltec-v4.3-meshcore-1.14.zip](https://resource.heltec.cn/download/WiFi_LoRa_32_V4/firmware/meshcore/heltec-v4.3-meshcore-1.14.zip)
* [Heltec LoRa Node Series Application for Meshtastic](https://heltec.org/eadge-computing/)
* [Heltec MeshSolar reference](https://heltec.org/meshsolar-where-solar-power-meets-meshtastic-freedom/)
* [Heltec MeshPocket](https://heltec.org/meshpocket/)
* [Heltec ESP32 examples](https://github.com/HelTecAutomation/Heltec_ESP32/tree/master/examples)
* [Meshtastic](https://meshtastic.org/)

## References and validation <a href="#source-notes" id="source-notes"></a>

Read sources include both data sheets, current manufacturer/wiki comparison, exact Meshtastic variants/environments, package index and the R2 V4.3/R8 V4.3.2 schematics. The R8 drawing was visually inspected. Original additions separate model-specific pin reservations, FEM handling, source-build selection and the two-way acceptance procedure. The older published guide's R2-only memory/power assumptions are explicitly corrected.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
