---
description: >-
  Set up the screenless HELTEC Wireless Stick Lite V3, choose SX1262 firmware,
  check supply and occupied pins, and confirm two-way Meshtastic messages.
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

# Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN V3

{% hint style="info" %}
[**View HELTEC Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN 868Mhz V3 on OpenELAB**](https://openelab.io/products/heltec-wireless-stick-lite-esp32s3)

**Model / option:** Default Title · **SKU:** `HT-WS-Lite-V3`
{% endhint %}

## Product overview

### Screenless V3 platform <a href="#heltec-wireless-stick-lite-esp32s3-sx1262-meshtastic-lorawan-868mhz-v3" id="heltec-wireless-stick-lite-esp32s3-sx1262-meshtastic-lorawan-868mhz-v3"></a>

Wireless Stick Lite **V3 HT-WS-Lite-V3** is the **screenless ESP32-S3FN8/SX1262** board with CP2102 USB-UART and single-cell charging.

### Listing scope and revision <a href="#product-link" id="product-link"></a>

It is distinct from Wireless Stick with an OLED and from V2's ESP32/SX1276 hardware. Use an SX1262-aware V3 target rather than the old SX127x LoRa library.

### Description: first-result scope <a href="#description" id="description"></a>

The first result is a live device identity and a confirmed message/reply with a second Meshtastic radio. No OLED or onboard GNSS result is expected. [Exact Lite overview](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/lora-32/wireless-stick-lite/), [V3 datasheet](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3\(Rev1.1\).pdf).

## Applications <a href="#features" id="features"></a>

Use Lite V3 for screenless mesh endpoints, LoRaWAN sensor development and controlled Wi-Fi/BLE/LoRa experiments. Establish a stock radio baseline before connecting sensors or optimizing sleep.

A USB terminal, BLE pairing and received LoRa frame are separate states. Measure the actual firmware's sleep and transmit cycles; USB bridge/LED activity can dominate a current measurement even when the MCU sleeps.

## Specifications <a href="#specification" id="specification"></a>

| Parameter             | Exact V3 Lite scope                                                |
| --------------------- | ------------------------------------------------------------------ |
| MCU                   | ESP32-S3FN8, dual LX7 up to 240 MHz                                |
| Memory                | 8 MB flash; 512 KB SRAM, 16 KB RTC SRAM; no PSRAM inferred         |
| Radio                 | SX1262 with TCXO; purchased high-band/868 MHz scope                |
| Published TX ceiling  | 21 ± 1 dBm; not a universal permitted setting                      |
| Wi-Fi / BLE           | 2.4 GHz 802.11 b/g/n / Bluetooth LE                                |
| Display / GNSS        | No onboard display or GNSS established                             |
| USB bridge            | CP2102; host UART TX43/RX44                                        |
| Cell                  | Single rechargeable lithium cell, 3.3–4.2 V operating supply range |
| Size                  | 58.08 × 22.6 × 8.2 mm                                              |
| Operating temperature | −20 to +70 °C; not a battery charging-temperature limit            |

The current wiki's 128 × 296 display and 88 × 36.6 × 12 mm rows contradict its screenless description and the exact Lite datasheet; they are not used here. The old linked Wireless Stick page concerns the **OLED model**, so its screen dimensions are not a Lite technical reference. [Lite Rev1.1 datasheet](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3\(Rev1.1\).pdf).

| Supply/output                     | Manufacturer condition                                                            |
| --------------------------------- | --------------------------------------------------------------------------------- |
| USB-C or 5 V input pin            | 4.7–6 V, 5 V nominal; source at least 500 mA                                      |
| Battery supply                    | 3.3–4.2 V, 3.7 V nominal; source requirement at least 250 mA in datasheet         |
| 3.3 V pin direct supply           | 2.7–3.5 V, 3.3 V nominal; alternate supply path, not used in first test           |
| Listed 3.3 V output / Vext output | 500 mA / 350 mA maxima; board consumption and regulator/source limits still apply |
| Listed 5 V output                 | 500 mA, **USB-powered only**                                                      |

Do not sum the output figures into a guaranteed simultaneous external-load budget. Manufacturer mode figures include roughly 230 mA at a 22 dBm TX condition, 90 mA receive, 2 mA USB sleep and 15 µA battery sleep; these differ from older summary claims. Use the actual mode and measurement boundary. [Supply, output and mode tables, datasheet pp.11–13](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3\(Rev1.1\).pdf).

## Hardware and connections

### Pin Map <a href="#pin-map" id="pin-map"></a>

![Heltec Wireless Stick Lite V3 exact-model header and GPIO map](<../../.gitbook/assets/image (283).png>)

_Heltec manufacturer V3 diagram, retained and visually inspected. Exposed header pins can remain occupied by the onboard radio or power controls._

Start on 5 V USB-C with the correct LoRa antenna fitted. Never attach independent USB and header supplies together. A battery may be charged through the documented USB path, but match received connector V+/GND and the cell's charge limits; a plug fit does not prove polarity. Do not power a non-rechargeable cell through the charger. USB/header supply voltage is distinct from 3.3 V GPIO logic.

| Function                     | V3 Lite GPIO                      |
| ---------------------------- | --------------------------------- |
| Radio SCK / MOSI / MISO / CS | 9 / 10 / 11 / 8                   |
| Radio reset / IRQ / busy     | 12 / 14 / 13                      |
| PRG/BOOT                     | 0                                 |
| Host UART TX / RX to CP2102  | 43 / 44                           |
| Status LED / Vext gate       | 35 / 36                           |
| Battery ADC / gate           | 1 / 37; gate active LOW in source |

GPIO12 appears on a header but is also radio reset; “exposed” does not mean free. Vext GPIO36 is active LOW in the pinned target and schematic. Radio DIO2 controls RF switching; DIO3 TCXO is a **1.8 V driver setting**. Keep those under the exact board implementation. [Pinned variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_wsl_v3/variant.h), [schematic](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3_Schematic_Diagram.pdf).

The datasheet labels headers J2/J3 while the schematic uses JP2/JP3. Match the received pin-1 marker and actual net names before translating numbered tables to physical left/right. The same external connector geometry as V2 does not preserve V2's GPIO sequence.

The battery-divider drawing uses 390 kΩ/100 kΩ, so ideally `Vbat = 4.9 × Vadc`. The printed inverted formula is incorrect for reconstructing battery voltage; actual ADC calibration and gate timing remain board-specific. The pinned firmware includes a calibration multiplier. Do not feed battery voltage directly into ADC1 or copy a V4/R8 raw ADC sketch.

## Software and development resources

### Choose the exact target

The reviewed Meshtastic commit is **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**, environment **`heltec-wsl-v3`**, hardware slug **HELTEC\_WSL\_V3**. The source intentionally reuses build-board definition `heltec_wifi_lora_32_V3` with Lite-specific macros and an 8 MB partition table. That internal build-board reuse is not a request to select the OLED model in a flasher. [Exact environment](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_wsl_v3/platformio.ini).

For Arduino, the current Heltec quick start installs the Heltec ESP32 framework through its package index and the **HELTEC ESP32** example library separately. It warns that framework 3.x and library 2.x changed together; do not mix the earlier framework with new examples. Select **Wireless Stick Lite V3** in the installed package, record both versions, preserve the target defaults and compile unchanged source before adding sensors.

The SX127x-oriented Sandeep Mistry LoRa API used by older boards is not an SX1262 drop-in driver. Use the exact manufacturer example/target or another SDK with explicitly reviewed pin/switch/TCXO support. Generic MCU support alone does not establish that board's radio or power implementation. [Current SDK/flash/LoRaWAN/Meshtastic guide](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/esp32-quick-start?esp32=ff).

For the manufacturer's LoRaWAN library, the reviewed guide declares 1.0.2 and a chip-specific activation license. That requirement is separate from GPL Meshtastic. Keep network-server MAC/regional parameters consistent with the actual stack; do not infer 1.0.4/1.1 compliance. Preserve framework/library licenses and avoid redistributing private activation/network keys.

## Getting started

### Original screenless two-radio test

Prepare Lite V3, supplied high-band antenna, USB data cable, Meshtastic client and a compatible peer. Save existing firmware/configuration first.

1. Attach the correct LoRa antenna and connect USB. Identify the CP2102 serial device and read the actual firmware/node identity in the client. If no port appears, check the data cable and the official CP210x driver for the host OS.
2. If Meshtastic is already installed, retain it for the first pass. Otherwise use the official flasher only when **Heltec Wireless Stick Lite V3** is explicitly offered; select the exact board, an appropriate released version and its supported layout. Save configuration before any erase.
3. Pair the actual screenless device. Heltec documents `123456` as a usual screenless factory PIN; use the current configured PIN if changed. A wrong PIN is not a LoRa antenna failure.
4. Select the permitted Region and match the peer's modem preset, frequency slot and complete channel name/key. Wait for restart. Keep normal client roles during the direct baseline.
5. Send `WSL-A-01`, confirm receipt at the other physical radio, return `WSL-B-01` and confirm local receipt. Repeat five numbered pairs and record receiver timestamps/RSSI/SNR. A local sending entry or a BLE connection is not a radio receipt.
6. If a suitable cell was installed with verified polarity, disconnect USB and repeat a reply. Check fresh battery telemetry; USB-only and cell-powered current measurements describe different circuits.

**Expected result:** readable live identity and independently observed text in both directions on the screenless Lite. No compile, flash, RF or current measurement was performed here. [Manufacturer Meshtastic setup](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/esp32-quick-start?esp32=ff).

### Preserve a private configuration record

Use the observed port in place of `YOUR_PORT` and close other serial clients. The following host commands are read-only:

```sh
python3 -m venv .venv-wsl
. .venv-wsl/bin/activate
python -m pip install meshtastic
meshtastic --port YOUR_PORT --info > wsl-v3-info.txt
meshtastic --port YOUR_PORT --nodes > wsl-v3-nodes.txt
```

Expected result is a pair of readable files identifying this board and known nodes. Keep channel keys/private configuration out of published logs. Missing peer data is not evidence of a failed local serial connection.

For unchanged-source development:

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e heltec-wsl-v3
```

Expected output is a target artifact under `.pio/build/heltec-wsl-v3/`; this build was not run. Confirm the exact target/partition and retain logs before upload.

### LoRaWAN and restore checkpoints

For LoRaWAN select the exact board/library example, provision its actual DevEUI/JoinEUI/AppKey privately and match region/sub-band with a gateway and server. Set a sparse test interval and a simple incrementing application counter. Require both a join-accept and a server-side uplink payload/counter; a local serial “sending” line is insufficient. Do not use a public mesh channel as a LoRaWAN service.

If upload fails, connect stable USB, hold **PRG/BOOT**, press/release **RST**, then release PRG and re-select the port. Restore an exact V3 Lite image using its supported tool/layout, wait for restart and repeat identity/reply checks. Full erase removes settings and may remove manufacturer activation data; do not erase as the first response to a mismatched channel.

## Troubleshooting and FAQs

### FAQ <a href="#faq" id="faq"></a>

| Symptom                                 | Ordered checks                                                                                             |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| No display appears                      | Lite is screenless; verify serial/BLE identity rather than an OLED boot screen                             |
| Old sketch compiles but radio fails     | V2 SX1276 versus V3 SX1262, exact map, DIO2 switching/TCXO and selected driver                             |
| No USB port                             | CP2102 data cable/driver, actual host port and PRG/RST entry                                               |
| Radio reset when sensor attached        | GPIO12 occupation, connector orientation, 3.3 V logic and actual source/load budget                        |
| Battery reading inverted or implausible | Correct divider reconstruction, active-LOW gate GPIO37 and calibration; no direct VBAT-to-ADC wiring       |
| Sleep exceeds a headline figure         | USB bridge, LED, Vext, Wi-Fi/BLE/radio state and actual firmware role                                      |
| LoRaWAN never joins                     | Exact stack/version, license if using Heltec stack, secure credentials, region/sub-band and gateway/server |
| App pairs but text is absent            | Region/preset/slot/channel key, actual antenna and receiver; send a unique return message                  |

#### Can V2 code or binaries be reused? <a href="#is-wireless-stick-v3-compatible-with-v2-code" id="is-wireless-stick-v3-compatible-with-v2-code"></a>

V3 changes the MCU to ESP32-S3, the modem to SX1262 and the GPIO/TCXO implementation. A V2 binary is not the V3 Lite target. Port application logic separately, then replace its board and radio integration with the exact V3 implementation. The SX127x-oriented Sandeep Mistry LoRa library is not a drop-in SX1262 driver; Heltec's current examples use different APIs. Preserve a known-good radio exchange before adding the ported sensor logic. [Lite hardware changes](https://docs.heltec.org/en/node/esp32/wireless_stick_lite/hardware_update_log.html), [current framework guide](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/esp32-quick-start?esp32=ff).

#### How can LoRa support home automation? <a href="#how-can-lora-be-useful-in-your-home-automation-projects" id="how-can-lora-be-useful-in-your-home-automation-projects"></a>

A practical design separates a remote sensor node from a collector with a Wi-Fi connection. For example, a garden sensor can send a sequence number, measurement and explicit units periodically; the collector records the newest sequence and displays the reading's age. Begin with a fixed known test value, verify its reception and return acknowledgement, then connect the separately qualified sensor. A sensor's supply/output levels and pin allocation must be checked against the V3 Lite pin map; no moisture-sensor pinout is assumed here.

Choose the application protocol before building the collector. A private LoRa link, Meshtastic telemetry and LoRaWAN do not share an interchangeable packet format. Test loss, retries and stale-data handling before a reading triggers a pump or other physical output. Measure the complete duty cycle, including the USB bridge, LEDs and external sensor, rather than deriving battery life from MCU deep sleep alone. This is an original application procedure, not a claim that this board includes a sensor, collector or home-automation firmware. [Exact board interfaces](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/lora-32/wireless-stick-lite/).

#### How is the Heltec activation license obtained? <a href="#how-to-get-the-license" id="how-to-get-the-license"></a>

This is the manufacturer LoRa-library activation mechanism, separate from open-source firmware licenses and LoRaWAN network keys. Factory activation may already be present; preserve it before erasing flash. If the matched Heltec example stops at its chip-ID/activation prompt, obtain that board's ID with the documented example and use the [Heltec chip-ID lookup](https://resource.heltec.cn/search). Keep the returned key associated with that physical board. Use only the activation method documented for the installed framework/example; do not send its AT activation command to unrelated Meshtastic firmware. [Manufacturer license procedure](https://docs.heltec.org/general/how_to_use_license.html), [current framework/version context](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/esp32-quick-start?esp32=ff).

The linked legacy license page is no longer updated, so its command-format examples do not establish compatibility with every current sketch. A failed join can instead be region, credentials or gateway configuration; diagnose those independently. No activation, flash erase or network join was performed for this guide.

**Does it include GNSS because a related Heltec guide does?** No onboard receiver is established for Lite V3; a related board's GNSS features are not included by association.

## Downloads and technical documents <a href="#resource" id="resource"></a>

| Resource                                                                                                                                                                                                                                                                                                               | Exact scope                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Current Lite wiki](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/lora-32/wireless-stick-lite/)                                                                                                                                                                                               | Screenless model; apply incorrect display/dimension-row corrections above      |
| [15-page Lite Rev1.1 datasheet](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3\(Rev1.1\).pdf)                                                                                                                                                                                                  | Header names, power/input/output/mode tables, dimensions and V2/V3 comparison  |
| [V3 schematic PDF](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3_Schematic_Diagram.pdf)                                                                                                                                                                                                       | CP2102, power/ADC/Vext, SX1262 and headers                                     |
| [Official pin-map PNG](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3.png) / [resource directory](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/)                                                                                                                                 | Received-revision orientation and HF archive; no wrong-model OLED illustration |
| [Lite hardware update log](https://docs.heltec.org/en/node/esp32/wireless_stick_lite/hardware_update_log.html)                                                                                                                                                                                                         | Historical MCU/modem/USB/TCXO changes; GPIO sequence changed                   |
| [Current SDK/projects guide](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/esp32-quick-start?esp32=ff)                                                                                                                                                                                        | Framework/library, boot entry, LoRaWAN and screenless Meshtastic paths         |
| [Pinned Lite variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_wsl_v3/variant.h) / [build](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/heltec_wsl_v3/platformio.ini) | Exact radio/control map and 8 MB target                                        |

The HF ZIP is a manufacturer download archive, not an executable to run. No exact mechanical CAD was identified in the reviewed Lite V3 directory; use the datasheet dimensions and received board before enclosure manufacture.

### Retained illustrations

![Retained Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN V3 illustration](<../../.gitbook/assets/image (282).png>)

### Additional existing resources

* [Heltec ESP32 framework and lib installation](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series)
* [Hardware Update Logs](https://docs.heltec.org/en/node/esp32/wireless_stick/hardware_update_log.html)
* [User Manual Document](https://docs.heltec.org/en/node/esp32/wireless_stick/index.html)
* [Heltec LoRaWAN test server based on SnapEmu](https://platform.snapemu.com/dashboard/)
* [How to Use License — main latest documentation (heltec.org)](https://docs.heltec.org/general/how_to_use_license.html)

## References and validation

The complete exact-model datasheet, current Lite wiki, historical Lite update log, SDK/LoRaWAN/Meshtastic guide and exact variant/environment were read. The V3 schematic was visually inspected. Wrong-model OLED references and the current wiki's inconsistent display/dimension rows are explicitly separated. The original screenless acceptance and read-only host record do not imply SDK compilation or RF testing.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
