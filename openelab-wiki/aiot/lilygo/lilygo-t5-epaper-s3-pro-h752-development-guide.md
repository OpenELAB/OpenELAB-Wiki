---
description: >-
  Bring up the H752-01 T5 E-Paper S3 Pro with GPS and 868 MHz radio, verify
  touch and I2C, and distinguish panel power, RTC and GNSS revisions.
---

# LILYGO T5 E-Paper S3 Pro H752-01 Engineering Guide

{% hint style="info" %}
[**View LILYGO T5 E‑Paper S3 Pro ESP32‑S3 4.7" LoRa Wi‑Fi BLE IoT Dev Kit on OpenELAB**](https://openelab.io/products/lilygo-t5-s3-pro)

**Model / option:** With GPS / 868MHz · **SKU:** `LILYGO-H752-01`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

T5 E-Paper S3 Pro **H752-01, with GPS / 868 MHz** is a 4.7-inch ESP32-S3 parallel e-paper development device with SX1262, touch, GNSS and TPS65185 display power management. It is distinct from **Pro Lite**, which omits LoRa/GNSS, and the older **H752**, which uses a different display power design.

Begin with a fresh factory screen change, touch response and read-only bus identification. Preserve the installed firmware before trying a radio or display example. The purchased 868 MHz option is not established as tested by a third-party 915 MHz Meshtastic build. [Manufacturer H752-01 version table](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/README.md).

## Applications

Use the Pro for low-refresh dashboards, e-paper UI, location logging, controlled radio experiments and touch interfaces. Separate image retention from active operation: e-paper can keep an old image after power is removed.

For power optimization, measure complete wake/update/sleep cycles at the battery boundary. A retained image does not establish the charger, GNSS, radio or sleep state. Do not use high-refresh experiments as a baseline for panel lifetime or normal power consumption.

## Specifications

| Item                | H752-01 scope                                                                                |
| ------------------- | -------------------------------------------------------------------------------------------- |
| Host / memory       | ESP32-S3-WROOM-1; 16 MB flash, 8 MB OPI PSRAM                                                |
| Panel               | ED047TC1, 4.7-inch, 960 × 540, 16 grayscale levels                                           |
| Display power       | TPS65185-family power manager; distinct from old H752                                        |
| Radio               | SX1262; purchased 868 MHz option                                                             |
| GNSS                | MIA-M10Q or L76K assemblies; identify by software response                                   |
| Touch               | GT911 reference design, I²C `0x5D`; later touch examples do not prove every panel is GT6972P |
| RTC                 | **PCF8563TS**, `0x51`, in schematic/current README; old wiki PCF85063 label differs          |
| Expander            | PCA9535PW, `0x20`                                                                            |
| Charge / fuel gauge | BQ25896 `0x6B` / BQ27220 `0x55`                                                              |
| Battery / inputs    | Original 3.7 V 1500 mAh assembly; USB-C and magnetic charging features                       |
| Expansion / storage | Two QWIIC connectors and microSD                                                             |
| Listed dimensions   | 129 × 69 × 11 mm; verify mechanical drawings/received enclosure                              |

Sources: [manufacturer wiki](https://wiki.lilygo.cc/products/t5-series/t5-e-paper-s3-pro/), [current pinned README](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/README.md), [schematic-derived pin reference](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/docs/pinmap.md). Display timing and battery runtime are workload-dependent and were not measured here.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Preserve the power sequence

Use ordinary regulated 5 V USB-C and the original pack for the first test. The wiki lists magnetic charging as another feature, but no independent charging-current or dual-source operating envelope was established here; simultaneous-input experiments and replacement-cell configuration are excluded. Do not alter charger voltage/current from a silicon maximum.

E-paper panel rails include voltages outside ordinary MCU logic. Keep the TPS/expander sequencing and panel-specific waveform under the exact driver. **VCOM tuning, raw high-voltage register writes and repeated high-refresh stress tests are excluded until the received panel calibration and driver procedure are confirmed.** The sample's hard-coded VCOM is not a universal panel calibration.

### Occupied buses and pin namespaces

| Role                                    | ESP32-S3 GPIO         |
| --------------------------------------- | --------------------- |
| Main I²C SDA / SCL                      | 39 / 40               |
| Shared radio/card SPI SCK / MOSI / MISO | 14 / 13 / 21          |
| SX1262 CS / IRQ / reset / busy          | 46 / 10 / 1 / 47      |
| microSD CS                              | 12                    |
| GNSS host TX / RX                       | 43 / 44               |
| Touch interrupt / reset                 | 3 / 9                 |
| RTC IRQ / expander IRQ                  | 2 / 38                |
| Front-light enable / BOOT               | 11 / 0                |
| E-paper D0/D1/D2/D3                     | 5 / 6 / 7 / 15        |
| E-paper D4/D5/D6/D7                     | 16 / 17 / 18 / 8      |
| E-paper CKH / CKV / STH / LEH / STV     | 4 / 48 / 41 / 42 / 45 |

The parallel display is not a small SPI e-paper module. GPIO48 is its CKV signal in the pin definition, not a spare user-button assumption. Also do not treat GPIO35–37 as free because the schematic lacks board net labels; this assembly uses OPI PSRAM.

PCA9535 **IO0\_0** enables the **shared radio/GNSS 3.3 V rail**. It is an expander offset, not ESP32 GPIO0. Port-1 offsets control EPD output/mode, TPS wake/power-up/VCOM and read power-good/interrupt; IO1\_2 is a function-button input. Never set every expander bit as an output merely because a different firmware fork reports that as a fix. Keep non-selected radio CS46 and card CS12 HIGH on the shared SPI bus. [Exact pin definition](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/docs/pin_define.md), [four-sheet schematic](https://raw.githubusercontent.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/hardware/T5%20E-paper%20S3%20Pro%20V1.0%2024-12-24.pdf).

QWIIC supplies and signals must be matched from the actual schematic/connector orientation; no external sensor current budget was established. Leave external loads disconnected for commissioning.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The reviewed **H752-01 branch** commit is **`87436b5c9d0d4fc09f44ef43a4fb5d41a757494a`**. PlatformIO environment **`T5_E_PAPER_S3_V7`** selects board `T5-ePaper-S3`, Arduino and `espressif32@6.5.0`; README identifies the legacy Arduino-ESP32 2.0.14 path. Keep the bundled `lib` collection and selected environment rather than upgrading libraries independently. Current platform configuration also lists M5GFX `^0.2.24`; the wiki's dependency table alone is not a lockfile.

The default source is `examples/factory/main`. Select exactly one alternative such as `examples/touch/main`, `examples/GPS/main`, card, RTC, charger/gauge, expander or display. Some `.ino` files are only wrappers: their implementation is in the adjacent `main.cpp`, so copying the wrapper alone is insufficient. Reviewed touch code uses GT911, waits for a serial host and prints point coordinates.

The generic RadioLib transmit/receive examples explicitly configure 868 MHz, BW 250 kHz, SF10, coding rate 6, sync `0xAB`, preamble 15, CRC off and TCXO 2.4 V. Those are **sample defaults**, not a verified received-module operating prescription. The LoRa-Top module's exact oscillator/revision must be matched before using that TCXO setting; radio transmission is excluded from this first local test. The repository's Meshtastic README links a third-party fork, says official merge is pending and labels 868 MHz untested. That is not verified official 868 MHz support.

Reviewed touch source carries MIT licensing. EPDiy, RadioLib, LVGL, SensorLib and other libraries retain separate notices; preserve them when distributing modified firmware.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original local display and touch acceptance

Prepare the identified H752-01, USB data cable, supplied battery/antenna assembly and a private backup of the working application/configuration. No external sensor is needed.

1. Start the supplied factory application and record its reported software/hardware version. Open two different pages and require a fresh screen transition; an old image after shutdown does not prove a boot succeeded.
2. Test taps near the center and four corners. Record each screen response and orientation. Distinguish a coordinate transform error from missing I²C communication.
3. For development, clone the pinned H752-01 source and change only `src_dir` to **`examples/touch/main`**, leaving one active source directory. Retain its local `main.cpp`, wrapper and libraries.

```sh
git clone --branch H752-01 https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO.git
cd T5S3-4.7-e-paper-PRO
git checkout 87436b5c9d0d4fc09f44ef43a4fb5d41a757494a
# Select src_dir = examples/touch/main in platformio.ini first.
pio run -e T5_E_PAPER_S3_V7
pio run -e T5_E_PAPER_S3_V7 -t upload
pio device monitor -b 115200
```

4. Open the USB terminal so the example passes its host wait. Expect GT911 initialization, then timestamped `X[index]`/`Y[index]` coordinates for a touch. Test separate points and reset once to check repeatability. A successful upload does not establish panel refresh or radio behavior.
5. Restore the known-good factory application before integrating display, touch and storage. Do not run a high-voltage display calibration just to diagnose a failed touch input.

**Expected result:** independently confirmed fresh factory screen behavior and, in the development touch test, changing coordinate output. No compilation, upload or touch test was run in this review. [Actual touch implementation](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/examples/touch/main/main.cpp).

### Original read-only I²C diagnostic

This independent sketch replaces the main application but **does not write charger, expander or panel registers**. Use the same board/core, save the factory image first and select a new example directory containing this sketch as the sole `src_dir`.

```cpp
#include <Arduino.h>
#include <Wire.h>
void setup() {
  Serial.begin(115200);
  delay(1000);
  Wire.begin(39, 40);
  Wire.setClock(100000);
  unsigned found = 0;
  for (uint8_t address = 8; address < 120; ++address) {
    Wire.beginTransmission(address);
    if (Wire.endTransmission() == 0) {
      Serial.printf("I2C_ACK=0x%02X\n", address);
      ++found;
    }
  }
  Serial.printf("ACK_COUNT=%u\n", found);
}
void loop() { delay(1000); }
```

Expected output is one line per responding device. Compare with the model table (`0x20`, `0x51`, `0x55`, `0x5D`, `0x68`, `0x6B`); power/reset state can affect which devices respond. An ACK identifies an address, not a fully working peripheral or the exact chip revision. If no device responds, check the correct board, GPIO39/40, power and terminal before changing EPD rails. This newly written diagnostic was checked lexically, not compiled for the SDK.

### GNSS, display, card and restore checkpoints

For GNSS, the exact sample enables the shared rail through expander IO0\_0 and tries L76K at 9600 baud, then u-blox recovery at 38400/9600. Its configuration writes are receiver-specific. Prefer passive data/identity observation first; a fixed baud can leave one shipped assembly silent. The `BOARD_GPS_PPS 1` macro in that sample is not established as a physical PPS route and GPIO1 is already radio reset in the board definition; do not add a PPS wire based on it.

For display work, keep the ED047TC1, EPDiy board-V7 and TPS/expander implementation together. The inspected display example prints rotated dimensions, then performs panel updates and sleeps; it hard-codes a VCOM setting. **Do not run that display example unchanged until the received panel's VCOM is confirmed.** Use a known-good factory image for initial refresh acceptance.

For microSD, power down before inserting/removing the card, retain CS12/shared-bus arbitration and test an expendable file with the model example. RTC work must use the current PCF8563 driver and its backup supply; a filename is not enough to select the RTC family.

For USB recovery, connect stable USB, hold **BOOT**, press/release **RST**, then release BOOT and select the observed port. Restore the exact H752-01 factory application through the manufacturer-selected layout/tool, wait for restart and repeat the local test. Do not flash an H752/Lite/third-party factory binary at a guessed offset. [Pinned recovery/firmware instructions](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/README.md).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                     | Ordered checks                                                                                      |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Old image remains after power-off           | Expected e-paper retention; require a new screen change or live serial identity                     |
| Touch example appears frozen                | Open serial host, retain adjacent `main.cpp`, verify GT911 versus actual touch revision             |
| Radio/GNSS both absent                      | Shared expander IO0\_0 rail, correct Pro rather than Lite assembly, source target                   |
| GNSS silent                                 | Correct receiver identity, host RX44/TX43 and baud; no improvised PPS/receiver commands             |
| Card disrupts radio                         | Shared SPI14/13/21, CS12 versus CS46 and exact driver sequencing                                    |
| EPD bad contrast/partial updates            | Exact panel/waveform/calibration and power-good sequence; no guessed VCOM tuning                    |
| Wrong RTC identity                          | Schematic/current README PCF8563TS versus older wiki PCF85063 label                                 |
| Meshtastic image boots but fails on 868 MHz | Third-party/pending-merge support and actual hardware revision; not a verified official target here |

Does Lite have the same radio because it shares a schematic? Its LoRa/GNSS parts are omitted. Does “IO48 button” make GPIO48 free? The exact panel definition assigns CKV there; use the received schematic and expander input map.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                                      | Exact scope                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [Manufacturer wiki](https://wiki.lilygo.cc/products/t5-series/t5-e-paper-s3-pro/)                                                                                                                                                                                                                             | Overview, tools, addresses, version table and source resources; apply RTC/pin qualifications |
| [Pinned H752-01 source](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/tree/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a)                                                                                                                                                                                 | Actual configuration, examples, dependencies and factory images                              |
| [Four-sheet schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/hardware/T5%20E-paper%20S3%20Pro%20V1.0%2024-12-24.pdf)                                                                                                             | Power/charger, MCU, expander/touch/RTC/panel, TPS circuitry                                  |
| [Pin mapping](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/docs/pinmap.md) / [pin definitions](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/blob/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/docs/pin_define.md)                               | Namespaces and shared rails; do not adopt the “unused” OPI-memory-pin statement              |
| [Board DXF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/DXF/H752-Board%20size.dxf) / [shell DWG](https://raw.githubusercontent.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/DXF/H752-Shell%20size.dwg) | Manufacturer mechanical files; actual fit not tested                                         |
| [Hardware datasheet directory](https://github.com/Xinyuan-LilyGO/T5S3-4.7-e-paper-PRO/tree/87436b5c9d0d4fc09f44ef43a4fb5d41a757494a/hardware)                                                                                                                                                                 | ED047TC1, GNSS, LoRa-Top, PCA9535 and TPS component references                               |

The source also includes FastEPD/M5GFX, LVGL, charger/gauge, card and optional active-pen projects. They are alternate development paths; their presence does not establish that every touch controller, RF default or high-refresh mode is appropriate for this received assembly.

### Additional existing resources

* [Manufacturer product](https://lilygo.cc/products/t5-e-paper-s3-pro)
* [Revision history reference](https://github.com/LILYGOpp/LILYGO_wiki/blob/main/docs/get_started/en/Wearable/T5-E-Paper-S3-Pro/T5-E-Paper-S3-Pro.md)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The full wiki, pinned README/configuration/pins, actual touch/display/GNSS/radio source and four-sheet schematic were read. Power and panel/expander/RTC sheets were visually inspected. The original local acceptance and register-write-free bus diagnostic avoid unverified VCOM, oscillator or third-party radio defaults. Component and application examples remain linked rather than copied wholesale.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
