---
description: >-
  Identify H743-SLIM V4 rails and ports, select the correct dual-IMU firmware
  target, obtain USB/attitude feedback and recover through DFU.
---

# MATEKSYS H743-SLIM V4 Flight Controller Engineering Guide

{% hint style="info" %}
[**View MATEK H743-SLIM V4 Flight Controller on OpenELAB**](https://openelab.io/products/matek-h743-slim-v4-drone-flight-controller)

**Model:** MATEKSYS H743-SLIM V4 · **SKU:** `MATEK-H743-SLIM-V4` · **Firmware hardware target:** `MATEKH743` / ArduPilot directory `MatekH743`
{% endhint %}

## Product overview

### Identity and development scope <a href="#identity-and-development-scope" id="identity-and-development-scope"></a>

The H743-SLIM V4 is a 36 mm flight-controller board for ArduPilot, INAV or Betaflight. It combines an STM32H743 processor, two ICM42688P inertial sensors, analog OSD and numerous peripheral connections. This guide establishes **USB configuration access and a correct attitude response before connecting propulsion**. WING, WLITE, MINI and earlier SLIM revisions share firmware ancestry but have different power circuits and sensors. [MATEKSYS firmware/revision matrix](https://www.mateksys.com/?p=5159), [exact V4 product and layout reference](https://openelab.io/products/matek-h743-slim-v4-drone-flight-controller).

The [legacy manufacturer product URL](https://www.mateksys.com/?portfolio=h743-slim-v4) was unavailable during this review. The V4-labelled manufacturer layout/wiring images hosted with the product were inspected; the firmware hub and ArduPilot source remain the references for firmware behavior. The [ArduPilot family page](https://ardupilot.org/copter/docs/common-matekh743-wing.html) explicitly warns that its illustrated board is WING. Its servo BEC and integrated current sensor must not be assigned to SLIM V4.

## Applications

Use SLIM V4 for an existing vehicle upgrade, a peripheral-rich UAV, an analog-video FPV platform or autopilot development. Seven physical UARTs allow separate GNSS, receiver and telemetry connections; CAN supports compatible DroneCAN devices; microSD records logs needed to diagnose sensor and power problems. None of these features establishes a completed aircraft's flightworthiness.

For a new installation, budget the actual camera, VTX, GNSS, receiver and radio current on the appropriate rails. A separate servo power system may be necessary. The SLIM V4 does **not** provide WING's high-current servo regulator. See [MATEKSYS V4 wiring reference](https://openelab.io/products/matek-h743-slim-v4-drone-flight-controller) and [ArduPilot hardware definitions](https://github.com/ArduPilot/ardupilot/blob/master/libraries/AP_HAL_ChibiOS/hwdef/MatekH743/hwdef.dat).

## Specifications

### Specifications and connections <a href="#specifications-and-connections" id="specifications-and-connections"></a>

| Parameter              | H743-SLIM V4 scope                                                                        |
| ---------------------- | ----------------------------------------------------------------------------------------- |
| MCU / memory           | STM32H743VIH6, up to 480 MHz; 1 MB RAM, 2 MB flash                                        |
| IMUs                   | Two ICM42688P; older revision sensor names do not identify this PCB                       |
| Barometer / analog OSD | DPS368 / AT 7456E on SPI2                                                                 |
| Logging                | microSD socket; card is a separate item unless included by the order                      |
| Serial                 | UART1, 2, 3, 4, 6, 7, 8; logical firmware numbering differs                               |
| Other I/O              | Two I2C buses, one CAN interface, SPI3 breakout, six analog measurement inputs            |
| Outputs                | S1–S12 plus the LED pad, 13 PWM-capable signals; protocol/timer groups apply              |
| Main battery input     | 6–36 V DC, described as 2–8S LiPo; **36 V remains the maximum**, including transients     |
| 5 V BEC                | 2.5 A continuous, 3 A maximum; include onboard and peripheral loads in the budget         |
| 3.3 V LDO              | 200 mA maximum reference; not a servo supply                                              |
| Switched video supply  | Selectable 5 V or filtered VBAT, maximum 2 A; select according to the attached VTX/camera |
| Current sensing        | No onboard current sensor; `Cur` / `Cur2` require a compatible external sensor            |
| USB                    | Type-C USB 2.0 data/configuration connection                                              |
| Mechanical             | 36 × 36 × 5 mm; 7 g; 30.5 × 30.5 mm mounting, Ø4 mm holes with Ø3 mm grommets             |

Electrical/mechanical values above follow the V4 product specification and the **V4-labelled manufacturer layout** linked below, not the older WING-family table. [V4 listing and manufacturer graphics](https://openelab.io/products/matek-h743-slim-v4-drone-flight-controller), [sensor support matrix](https://www.mateksys.com/?p=5159). The DPS368 component's environmental protection does not make the assembled flight controller waterproof.

## Hardware and connections

### Inspect the actual V4 board and connector orientation

![MATEKSYS H743-SLIM V4 manufacturer layout, rails and connector labels](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-05-700_cfe2e47b-e327-47df-94c9-247649f36279.webp?v=1775185743)

_Manufacturer-labelled V4 layout, hosted by OpenELAB; visually inspected. Read the pad labels and mating direction on the received PCB. This is an original manufacturer graphic, not a newly drawn pinout; no general reuse license was established._

| Connection               | Function and wiring boundary                                                                                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| JST-SH 1.0 mm 8-pin      | Carries VBAT, GND, current-sensor input, RX8 and S1–S4. A matching housing does not establish another ESC's wire order. Check each signal against the layout before plugging in. |
| JST-GH 1.25 mm 4-pin CAN | Labelled 5 V, CAN-H, CAN-L, GND. Follow the graphic's mating orientation; do not count pins from an assumed cable-side view.                                                     |
| TXn / RXn                | UART logic signals: controller TX→peripheral RX and RX←TX, with a common reference. Power comes from a separately verified rail.                                                 |
| DA1/CL1 and DA2/CL2      | I2C data/clock pairs; check pull-up voltage and device addresses.                                                                                                                |
| C1 / C2 / VTX            | Analog camera1/camera2 inputs and video output; use the same PAL/NTSC standard on both cameras.                                                                                  |
| Vsw jumper               | Select 5 V **or** VBAT as documented; never bridge both selections. The output can carry battery voltage when selected.                                                          |
| R6/T6                    | Receiver function depends on firmware and `BRD_ALT_CONFIG`; see the logical-port table below.                                                                                    |
| Boot / USB               | Bootloader entry and host USB; preserve access when mounting.                                                                                                                    |
| D / C / G debug pads     | `D` is SWDIO, `C` is SWCLK, and `G` is ground. The adjacent `3` / `3V3` labels identify the 3.3 V LDO rail. Read the actual V4 layout before connecting a debugger.              |
| SI / SO / CK beside CAN  | SPI3 breakout labels in the V4 layout; this separate group is not the SWD debug interface. Do not confuse these labels with the S1–S12 PWM output bank.                          |

### Analog inputs are not interchangeable power inputs

| Input     | Published measurement scope / ArduPilot mapping                                                                               |
| --------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Main VBAT | 6–36 V power input with voltage divider; `BATT_VOLT_PIN=10`; V4 graphic gives `BATT_VOLT_MULT=11`                             |
| Cur       | External current-sensor signal; `BATT_CURR_PIN=11`; scale must match the actual sensor                                        |
| Vbat2     | Voltage-sensing pad, divider 20:1 plus lower resistor; maximum 69 V measurement reference; `BATT2_VOLT_PIN=18`, multiplier 21 |
| Cur2      | 0–3.3 V external sensor signal; `BATT2_CURR_PIN=7`                                                                            |
| RSSI      | Analog RSSI input; `RSSI_ANA_PIN=8`; match the firmware/input configuration                                                   |
| AirS      | Analog airspeed input, 0–6.6 V with onboard 1:1 divider; `ARSPD_PIN=4`                                                        |

The **69 V Vbat2 measurement limit does not raise the main power-input limit above 36 V**. The family ArduPilot page includes older divider defaults; use the V4 drawing, measure a known voltage and calibrate rather than copying a WING/WLITE value. These settings describe signal routing, not calibration results. [V4 manufacturer layout](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-05-700_cfe2e47b-e327-47df-94c9-247649f36279.webp?v=1775185743), [ArduPilot family settings and scope warning](https://ardupilot.org/copter/docs/common-matekh743-wing.html).

### Power-up preparation

1. Remove propellers and disconnect ESC signal/power and servo loads. For the first configuration test, connect USB only.
2. Inspect polarity, solder bridges, conductive mounting contact and cable strain. Mount with the correct grommets; the board's marked up/forward orientation must agree with the configured orientation.
3. Before adding a battery, check the Vsw selection against the exact VTX voltage. Camera/video and power labels have different roles.
4. Budget each regulator separately, then verify its output with peripherals disconnected. The adjacent 4V5 rail can be USB-powered; the 5 V battery-derived rail can behave differently. Do not infer peripheral power solely from a lit FC LED.
5. When adding an ESC, trace the eight-wire harness pin by pin. Use its documented current-sensor scale; the flight controller does not generate a current measurement by itself.

![MATEKSYS H743-SLIM V4 multirotor wiring](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-06-700.webp?v=1775185743)

_Original manufacturer multirotor wiring, OpenELAB-hosted; inspected. The illustrated ESC/sensor/GNSS are integration examples, not contents guaranteed by this FC SKU._

## Software and development resources

### Software, diagnostics and recovery <a href="#software-diagnostics-and-recovery" id="software-diagnostics-and-recovery"></a>

| Stack                         | Target / supported boundary                                                                                                                                                               |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ArduPilot                     | Manufacturer target `MATEKH743`; actual firmware directories are `MatekH743`. Use the vehicle-specific image, e.g. Copter versus Plane.                                                   |
| INAV                          | `MATEKH743`; match configurator to the installed firmware release. The firmware hub notes that an ICM42688P may be shown using the ICM42605 driver name.                                  |
| Betaflight                    | `MATEKH743`; manufacturer-custom `betaflight_4.5.1_MATEKH743_V3.hex` is explicitly listed for V1.5/V2/V3/V4. The hub warns ordinary configurator firmware may support only the first IMU. |
| ArduPilot bidirectional DShot | A distinct `MatekH743-bdshot` build changes receiver/output resources; do not assume the standard timer map still applies.                                                                |
| Host tools                    | ArduPilot ground station such as Mission Planner; the matched INAV/Betaflight configurator; STM32 DFU tools only for deliberate firmware recovery.                                        |

These are **source-reviewed target selections**, not claims that every current release was tested on this board. The manufacturer's historical download matrix is not an instruction to downgrade a functioning aircraft. [MATEKSYS firmware hub](https://www.mateksys.com/?p=5159), [ArduPilot firmware/loading documentation](https://ardupilot.org/copter/docs/common-matekh743-wing.html).

### ArduPilot logical serial ports

| Parameter port | Physical UART                                                                                          |
| -------------- | ------------------------------------------------------------------------------------------------------ |
| SERIAL 0       | USB console                                                                                            |
| SERIAL 1       | UART7, CTS/RTS available                                                                               |
| SERIAL 2       | USART1                                                                                                 |
| SERIAL 3       | USART2, commonly GPS1                                                                                  |
| SERIAL 4       | USART3, commonly GPS2                                                                                  |
| SERIAL 5       | UART8                                                                                                  |
| SERIAL 6       | UART4                                                                                                  |
| SERIAL 7       | UART6; RX6 is not a normal UART receive input until the applicable alternate configuration is selected |

### ArduPilot receiver wiring and serial options

By default RX6 is a timer input. It accepts supported receiver protocols except CRSF/ELRS and SRXL2; FPort on that default input provides RC without telemetry. The following **UART6/SERIAL 7** reference instead requires `BRD_ALT_CONFIG=1` and `SERIAL7_PROTOCOL=23`, which make RX6 a true UART input. Save the current parameters before changing that routing; PPM is unavailable in this alternate mode.

| Receiver protocol | Signal connection in this alternate configuration | `SERIAL7_OPTIONS`                             | Source-specific boundary                                                                                                            |
| ----------------- | ------------------------------------------------- | --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| SBUS              | Receiver signal to R6                             | `3`                                           | Inversion and half-duplex settings follow this target's primary guide.                                                              |
| DSM / SRXL        | Receiver signal to R6                             | Follow the exact receiver protocol's settings | The family guide groups these with R6 receivers but specifies `3` specifically for SBUS; do not extend that value to all receivers. |
| FPort             | Receiver bus to T6                                | `7`                                           | Bidirectional RC/telemetry uses T6; default timer-input FPort lacks telemetry.                                                      |
| CRSF / ELRS       | Receiver TX to R6 and receiver RX to T6           | `0`                                           | Full UART pair; telemetry is provided automatically by the protocol.                                                                |
| SRXL2             | Receiver bus to T6                                | `4`                                           | Single-wire bidirectional bus; telemetry is provided automatically.                                                                 |

Power the receiver from its verified supply rail and share ground; the signal-pad names do not specify its supply voltage. Any other UART can also support RC in ArduPilot except PPM, but its logical `SERIALx` parameter number and wiring must be mapped separately. These values describe the documented ArduPilot target, not INAV/Betaflight configuration. [ArduPilot RC Input section](https://ardupilot.org/copter/docs/common-matekh743-wing.html#rc-input), [target definition](https://github.com/ArduPilot/ardupilot/blob/master/libraries/AP_HAL_ChibiOS/hwdef/MatekH743/hwdef.dat).

### Outputs, CAN, video and logging

For the standard ArduPilot target, timer groups are **S1–S2**, **S3–S6**, **S7–S10**, **S11–S12**, and **LED/S13**. DShot and ordinary PWM cannot be mixed arbitrarily inside a group. The `-bdshot` firmware reorganizes resources; its documented bidirectional-capable outputs are 1–8 with different pairs. Confirm the exact build before assigning motors or servos. [Primary output constraints](https://ardupilot.org/copter/docs/common-matekh743-wing.html).

CAN wiring requires CAN-H/CAN-L, correct reference/power and termination at the two physical ends. Select a supported DroneCAN peripheral and firmware protocol; a CAN connector alone does not make every motor/GNSS protocol compatible. The manufacturer's example includes a separate CAN power distributor:

![MATEKSYS CAN peripheral wiring using H743-SLIM V4](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-07-700.webp?v=1775185743)

_Original MATEKSYS CAN example, OpenELAB-hosted; inspected. Additional power-distribution hardware is not a feature of the FC itself._

For ArduPilot camera/Vsw control, the family reference assigns GPIO81 to Vsw and GPIO82 to camera switching. The active state can turn Vsw **off** or select camera2; verify behavior with unloaded outputs before powering video equipment. Configure logs on a compatible microSD, confirm creation of a new log after a bench session, and inspect IMU/voltage records before interpreting an airborne fault. [Camera switch behavior](https://ardupilot.org/copter/docs/common-matekh743-wing.html).

## Getting started

### Bench setup before installing a vehicle <a href="#bench-setup-before-installing-a-vehicle" id="bench-setup-before-installing-a-vehicle"></a>

1. Leave propellers and actuators disconnected. Photograph the revision and wiring; connect a known USB data cable directly to the host.
2. Identify the installed firmware/vehicle type using its own configurator. For an existing ArduPilot installation, open Mission Planner, select the enumerated USB serial port and connect. Use the existing installation first rather than reflashing merely to identify it.
3. Record board/firmware identity, vehicle type and sensor status. In the attitude display, keep the board still, then gently tilt it about one axis at a time. Compare roll/pitch direction and level response with the physical movement.
4. Save the full parameter file before edits. In ArduPilot's parameter view, inspect `BRD_ALT_CONFIG`, `SERIALx_PROTOCOL`, battery settings and board orientation. Separate reading/exporting from changing settings.
5. If orientation/calibration is required, perform the selected firmware's accelerometer procedure on the disconnected bench. Reboot and confirm the intended values persist. Do not arm or start a motor test as part of this first result.
6. Reconnect in the same host tool, repeat the attitude check and record one diagnostic checkpoint: actual firmware string, USB identity and whether both expected inertial sensors are reported by that build.

**Expected result:** repeatable USB access, a saved parameter baseline and correct attitude changes without actuator movement. A firmware connection is not proof that sensor calibration, failsafes or motor ordering are flight-ready. For a missing second IMU, check firmware support before replacing hardware. [MATEKSYS sensor/target matrix](https://www.mateksys.com/?p=5159), [ArduPilot family setup](https://ardupilot.org/copter/docs/common-matekh743-wing.html).

### Original offline parameter-review helper

Save a ground-station parameter export as `vehicle.param`. This original Python 3 helper accepts comma-separated or whitespace-separated name/value rows and prints settings that frequently differ between a USB-only bench and a wired vehicle. It does not connect to the FC or change parameters.

```python
from pathlib import Path
import re

values = {}
for raw in Path('vehicle.param').read_text(encoding='utf-8-sig').splitlines():
    line = raw.strip()
    if not line or line.startswith('#'):
        continue
    parts = re.split(r'[,\s]+', line)
    if len(parts) >= 2:
        values[parts[0]] = parts[1]

keys = ['BRD_ALT_CONFIG', 'AHRS_ORIENTATION', 'BATT_MONITOR',
        'BATT_VOLT_PIN', 'BATT_VOLT_MULT', 'BATT_CURR_PIN',
        'BATT_AMP_PERVLT', 'BATT2_VOLT_PIN', 'BATT2_CURR_PIN',
        'BATT2_VOLT_MULT']
keys += [f'SERIAL{i}_PROTOCOL' for i in range(8)]
for name in keys:
    print(f'{name:22s} {values.get(name, "NOT_IN_EXPORT")}')
print('OFFLINE_REVIEW: compare values with V4 wiring and installed firmware.')
```

Run `python3 inspect_h743_params.py` after saving the code under that name. **Expected result:** the exported values or an explicit `NOT_IN_EXPORT` indication. This is a file inspection, not proof that a battery divider, sensor or receiver works. Retain the original export, actual firmware string and hardware diagram together.

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom / question                              | Ordered checks and recovery                                                                                                                                           |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB device absent                               | Change cable/host port; disconnect peripherals and battery; inspect connector/shorts. A power LED does not prove a data connection.                                   |
| FC reports one IMU                              | Check V4 label, stack/build and manufacturer dual-IMU support matrix. Ordinary Betaflight target builds can differ from the listed dual-IMU custom build.             |
| GNSS/receiver has no power on USB               | Check 4V5 versus 5 V rail selection with a meter; do not bridge rails to force power.                                                                                 |
| Receiver works without telemetry                | Check physical UART versus logical SERIAL number, alternate RX6 configuration, inversion and half-duplex settings for that exact protocol.                            |
| Battery voltage plausible but current wrong     | SLIM V4 has no current sensor. Identify the external sensor, current signal and scale; zero/calibrate with a known reference.                                         |
| Output protocol conflicts                       | Recheck the timer group and standard versus bidirectional-DShot build. A working individual pad does not prove a mixed group is valid.                                |
| Vbat2 senses a high voltage: can VBAT take it?  | No. The secondary divider's measurement range is distinct from the 6–36 V power input.                                                                                |
| Can I restore another vehicle's parameter dump? | Match model, firmware and actual wiring. Start from the selected firmware's supported defaults after a deliberate migration, retaining the old export for comparison. |

### DFU recovery is a separate operation

Only reflash after identifying the installed firmware, backing up parameters and removing propulsion. MATEKSYS documents entering DFU by connecting **USB while holding Boot**, without battery/external 5 V. On Windows, select **STM32 BOOTLOADER**, not a normal Virtual COM Port, before changing a driver. A powered device on UART1/UART3 can prevent DFU entry; disconnect it before suspecting a damaged bootloader. [Manufacturer DFU instructions](https://www.mateksys.com/?p=5159).

For an initial ArduPilot load, the official family page specifies the target's **`with_bl.hex`** through DFU; subsequent ground-station updates use **`.apj`**. Match the vehicle and exact `MatekH743` build. INAV/Betaflight have separate image formats/settings workflows. Reapply only reviewed settings appropriate to the new release, then repeat the USB/attitude checkpoint before reconnecting actuators. A successful flash does not validate motor mapping or failsafes. [ArduPilot loading procedure](https://ardupilot.org/copter/docs/common-matekh743-wing.html).

## Downloads and technical documents

| Resource                                                                                                                                                                                                             | Model/revision and purpose                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| [V4 layout and connector labels](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-05-700_cfe2e47b-e327-47df-94c9-247649f36279.webp?v=1775185743)                                                         | MATEKSYS original V4 graphic, OpenELAB-hosted and visually inspected                                                   |
| [V4 multirotor wiring](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-06-700.webp?v=1775185743) / [CAN example](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/image-07-700.webp?v=1775185743) | Original manufacturer diagrams; peripheral examples are optional hardware                                              |
| [Manufacturer firmware/driver hub](https://www.mateksys.com/?p=5159)                                                                                                                                                 | Target matrix, dual-IMU note, matched configurators and DFU/VCP tools                                                  |
| [MatekH743 Copter releases](https://firmware.ardupilot.org/Copter/stable/MatekH743/) / [Plane releases](https://firmware.ardupilot.org/Plane/stable/MatekH743/)                                                      | Vehicle-specific ArduPilot image directories; inspect release/build before downloading                                 |
| [MatekH743 hardware definition](https://github.com/ArduPilot/ardupilot/blob/master/libraries/AP_HAL_ChibiOS/hwdef/MatekH743/hwdef.dat)                                                                               | Primary pin/mode definitions; moving source, retain resolved commit for development                                    |
| [ArduPilot family guide](https://ardupilot.org/copter/docs/common-matekh743-wing.html)                                                                                                                               | Serial numbering, receiver modes, timer groups and firmware loading; WING power specifications are not SLIM V4 ratings |
| [Legacy V4 manufacturer page](https://www.mateksys.com/?portfolio=h743-slim-v4)                                                                                                                                      | Original model reference; returned 404 during this review                                                              |

No public editable schematic/PCB CAD archive for this exact board was established from the accessible resources. The layout is a wiring reference, not an editable schematic. Do not recreate a board or approve mounting screw engagement from an estimated photograph.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026**: MATEKSYS firmware hub, the primary ArduPilot family documentation and target definition, the live exact product listing, and V4-labelled manufacturer layout/multirotor/CAN diagrams hosted there. The original family-reference URL [retained here](https://shop.ardupilot.org/sub/docs/common-matekh743-wing.html) is a separate legacy reference; the ardupilot.org documentation cited above is the reviewed primary page.

**Validation:** source review and visual diagram inspection only. Configurator installation, firmware flashing, USB/sensor/receiver tests, flight, power-rail loading and hardware operation were **not run**. Expected results are prospective checkpoints. The legacy manufacturer's V4 page was unavailable; the linked firmware hub and inspected V4 diagram provide the usable references, with that access limitation retained explicitly.
