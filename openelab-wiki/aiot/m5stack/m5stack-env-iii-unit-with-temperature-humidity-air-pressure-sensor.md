---
description: >-
  Read ENV-III SHT30/QMP6988 measurements with explicit model selection, CoreS3
  or Atom wiring and pressure units.
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

# M5Stack ENV III Unit with Temperature Humidity Air Pressure Sensor

{% hint style="info" %}
[**View M5Stack ENV-III on OpenELAB**](https://openelab.io/products/env-iii-unit)

**Model:** Unit ENV-III · **Manufacturer code:** `U001-C` · **OpenELAB SKU:** `M5-U001-C` · SHT30 and QMP6988.
{% endhint %}

## Product overview

ENV-III measures temperature, relative humidity and pressure over I2C. Its SHT30/QMP6988 combination differs from ENV-II, ENV-IV and ENV-Pro. This guide gives a CoreS3 development route and explains the Atom-Lite pin difference. [ENV-III official guide](https://docs.m5stack.com/en/unit/Unit_ENV-III).

## Applications

Use it for an environmental logger, indoor trend display or sensor-integration exercise. Pressure-derived altitude is an estimate tied to a reference pressure; weather changes can alter that estimate without a physical height change. Record units and reference conditions alongside measurements.

## Specifications

| Parameter                                 | ENV-III integration value                                                    |
| ----------------------------------------- | ---------------------------------------------------------------------------- |
| Temperature / humidity sensor             | SHT30 at `0x44`                                                              |
| Pressure sensor                           | QMP6988 at `0x70`                                                            |
| Temperature measurement / stated accuracy | −40–120 °C measurement span; ±0.2 °C quoted over 0–60 °C                     |
| Relative humidity                         | Manufacturer table: 10–90 %RH, ±2%                                           |
| Pressure                                  | Manufacturer table: 300–1100 hPa; resolution/error figures 0.06 Pa / ±3.9 Pa |
| Module operating temperature              | 0–60 °C                                                                      |
| Module dimensions                         | 32 × 24 × 8 mm                                                               |
| Connection                                | I2C through Grove Port A                                                     |

The sensor's maximum measurement range is distinct from the assembled module's operating range. These are advertised figures from the [current official specification](https://docs.m5stack.com/en/unit/Unit_ENV-III), not independently measured accuracy. Older page copies listed a 0–40 °C module range; retain a supplied older revision's stricter limit until its applicable rating is confirmed. Use the linked sensor datasheets for accuracy conditions rather than extending a table value to all temperatures.

## Hardware and connections

Connect the Unit with host power removed. Grove wires are **black GND, red 5 V, yellow SDA and white SCL**. Use the host's actual port pin map; on CoreS3 Port A uses SDA2/SCL1, whereas the Atom-Lite Grove socket uses SDA26/SCL32. The supply conductor and GPIO logic level serve different purposes. [ENV-III wiring](https://docs.m5stack.com/en/unit/Unit_ENV-III), [CoreS3 pin map](https://docs.m5stack.com/en/core/CoreS3), [Atom-Lite pin map](https://docs.m5stack.com/en/core/Atom-Lite).

## Software and development resources

The [current official ENV Arduino tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_env) uses CoreS3 with M5Unified, M5GFX, M5UnitUnified and M5Unit-ENV. Install the dependencies requested by Arduino Library Manager, including M5HAL/M5Utility where required. Its initial example selects **ENV-IV**, so an unmodified copy is not an ENV-III program. The tutorial provides an explicit ENV-III branch.

## Getting started

### CoreS3: select ENV-III explicitly

1. Prepare CoreS3, ENV-III, a Grove cable, USB data cable and Arduino IDE with the CoreS3 environment. Connect ENV-III to Port A with power removed.
2. Install the libraries named above. Open the complete example in the [official ENV Arduino tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_env).
3. Enable `#define USING_ENV3` and disable `#define USING_ENV4`. The selected branch uses `m5::unit::UnitENV3` with `sht30` and `qmp6988`. Keep the example's model-aware `M5.getPin(...)` lookup and I2C configuration.
4. Select the CoreS3 port and build. Follow CoreS3's documented download mode if uploading requires it. After upload, observe the display and monitor configured at **115200 baud**.

**Expected result:** updated SHT30 temperature/humidity and QMP6988 pressure appear. The tutorial converts pressure from Pa to hPa by multiplying by `0.01`; keep units with any logged value. A responding address is not a calibrated measurement. [Example and upload procedure](https://docs.m5stack.com/en/arduino/projects/unit/unit_env). **Observed result:** not run.

### Atom-Lite route

Use the separate [official `Unit_ENVIII_M5Atom.ino` example](https://github.com/m5stack/M5Unit-ENV/blob/master/examples/Unit_ENVIII_M5Atom/Unit_ENVIII_M5Atom.ino), whose header identifies M5Atom plus ENV-III and Arduino M5Stack Board Manager **v2.1.0**. It initializes SDA26/SCL32 at 400 kHz and reports through Serial at 115200 baud. Preserve this host-specific configuration; do not paste the CoreS3 display code onto a screenless Atom-Lite. The example reports pressure in Pa, while the CoreS3 tutorial displays hPa.

## Troubleshooting and FAQs

**Neither sensor appears:** check the actual port, cable, supply and SDA/SCL selection first. Disconnect other I2C devices while isolating the fault.

**Temperature works but pressure fails:** check for QMP6988 at `0x70` and verify the selected ENV generation. ENV-IV uses BMP280; finding a humidity sensor at `0x44` does not distinguish ENV-III from ENV-IV.

**Pressure differs by a factor of 100:** compare Pa with hPa before diagnosing a sensor fault. Keep the original value and conversion in the log.

**Altitude drifts:** check the reference sea-level pressure and actual pressure trend. A pressure-based altitude estimate is not a direct height measurement.

## Downloads and technical documents

| Resource                                                                                                                     | Purpose                                                                                                 |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ENV-III official guide](https://docs.m5stack.com/en/unit/Unit_ENV-III)                                                      | Specifications, schematic, pin map, dimensions, SHT30/QMP6988 data sheets, UIFlow and model comparisons |
| [Current ENV Arduino tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_env)                                   | CoreS3 setup, model selection, complete code and expected display                                       |
| [M5Unit-ENV examples](https://github.com/m5stack/M5Unit-ENV/tree/master/examples)                                            | Separate model/host examples                                                                            |
| [Atom ENV-III example](https://github.com/m5stack/M5Unit-ENV/blob/master/examples/Unit_ENVIII_M5Atom/Unit_ENVIII_M5Atom.ino) | Exact C008 Grove pin configuration and serial workflow                                                  |
| [Mechanical files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U001-C_Unit_ENV-III/Structures)               | ENV-III structure source                                                                                |

## References and validation

Manufacturer documentation and the cited example reviewed **23 November 2026**. Compilation, flashing and hardware measurement were **not run**. Record the actual library releases, host/Unit revisions, environmental conditions and raw measurement units when reproducing a result.

## Existing illustrations

Original page illustrations are retained below. Use the exact-model pin map and revision notes in this guide when interpreting them.

<figure><img src="../../.gitbook/assets/image (536).png" alt=""><figcaption></figcaption></figure>
