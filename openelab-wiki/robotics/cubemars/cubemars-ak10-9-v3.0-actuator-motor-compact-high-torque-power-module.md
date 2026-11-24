---
description: >-
  Commission AK10-9 V3.0 KV60 with exact power/UART/CAN pins, distinguish
  current extended-frame MIT protocol, and decode passive feedback before
  motion.
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

# CubeMars AK10-9 V3.0 Actuator Motor Compact High-Torque Power Module

{% hint style="info" %}
[**View CubeMars AK10-9 V3.0 KV60 actuator on OpenELAB**](https://openelab.io/products/cubemars-ak10-9-v3-0-actuator)

**Model:** AK10-9 V3.0 KV60 · **SKU:** `CubeMars-AK10-9-V3.0D` · **Option:** actuator with integrated driver; external debug interface is separate
{% endhint %}

## Product overview

### Description <a href="#description" id="description"></a>

The AK10-9 V3.0 KV60 is a 48 V robotic actuator with 9:1 planetary reduction, 18 N·m rated output and 53 N·m peak output. Its motor/output feedback is a dual-encoder configuration. This guide starts with controller identity, parameters and passive feedback, then explains the boundaries needed before a small unloaded movement. [Exact manufacturer product](https://www.cubemars.com/product/ak10-9-v3-0-kv60-robotic-actuator.html).

**V3 firmware is a material compatibility boundary.** The current model page links the V3 driver software manual and AK60-4820-1C-A2 installation instructions. In that software manual, servo **and MIT force-control commands use extended CAN frames**; an older AK2.0 standard-frame MIT sender is not interchangeable. Match the actual controller and installed firmware before selecting a packet format. [V3 software manual V1.0.1, §§2.1–2.2](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

### Product Link <a href="#product-link" id="product-link"></a>

The opening link resolves the KV60 V3.0 actuator selection. A RUBIK/R-LINK interface is setup equipment, not another actuator or proof that a bare replacement board is configured. Keep [AK80-64's AK2.0 guide](cubemars-ak80-64-actuator-bldc-motor-compact-high-torque-power.md) separate from this V3 procedure.

## Applications

Use AK10-9 V3.0 for robot joint and mobile mechanism prototypes requiring more speed and backdrivability than a much higher-reduction actuator. Evaluate rated torque at the actual speed, acceleration/impact peaks, mounting and bearing loads, thermal path and duty cycle. The published maximum torque is not a continuous stall or human-contact limit.

The second encoder does not cancel gear backlash or prove multi-turn retention. Record the feedback source, motor/output units, zero reference and startup behavior with the individual actuator. [Manufacturer parameters and drawing](https://www.cubemars.com/product/ak10-9-v3-0-kv60-robotic-actuator.html).

## Specifications

### Specification <a href="#specification" id="specification"></a>

| Parameter                              | AK10-9 V3.0 KV60 reference                                                  |
| -------------------------------------- | --------------------------------------------------------------------------- |
| Nominal supply                         | 48 V                                                                        |
| Rated / peak output torque             | 18 / 53 N·m                                                                 |
| Rated / peak current                   | 10.7 / 31.9 A as published; distinguish from driver RMS/peak specifications |
| Rated / no-load output speed           | 235 / 320 rpm                                                               |
| Reduction / pole pairs                 | 9:1 / 21                                                                    |
| KV / motor-side KT                     | 60 rpm/V / 0.16 N·m/A; not the firmware's output-torque coefficient         |
| Motor/output encoder resolution        | 21-bit / 15-bit magnetic; two encoders                                      |
| Mass / envelope                        | 940 g / Ø98 × 61.7 mm                                                       |
| Phase-to-phase resistance / inductance | 248 mΩ / 213 µH                                                             |
| Rotor inertia                          | 1002 g·cm²                                                                  |
| Ambient operating range                | −20 to 50 °C                                                                |
| Temperature sensor                     | NTC MF51B103F3950                                                           |

[Exact manufacturer specifications](https://www.cubemars.com/product/ak10-9-v3-0-kv60-robotic-actuator.html). The current torque-density value is 56.4 N·m/kg; the earlier wiki's 86 N·m/kg entry is not used. Calculated 53/0.940≈56.4 checks that reference; it does not establish continuous operation at 53 N·m.

### Driver rating versus actuator rating

The matched **AK60-4820-1C-A2** instruction identifies **AK-DRV-12S-V3.00** hardware, 48 V nominal, 18–52 V allowable input, 20 A rated RMS output and 60 A maximum peak output, 1 Mbit/s CAN, and 63 × 57 mm board dimensions. Driver ambient−20 to 65 °C and board maximum 100 °C are not higher allowable motor ambient or a permission to ignore motor heating. [Installation manual V1.0.0, 25 June 2025, PDF pp. 4–5](https://www.cubemars.com/data/cms/202610/ak60-4820-1c-a2-driver-installation-instructions.pdf).

The V3 software manual's AK10-9 force-control **encoding** table gives position ±12.56 rad, speed ±28 rad/s, torque ±54 N·m, Kp 0–500 and Kd 0–5, with output-torque coefficient 1.3137 N·m/A. These are protocol quantizer ranges, **not approved travel, speed, gain or continuous torque limits**. The physical peak 53 N·m and the ±54 wire range have different meanings. Do not substitute the motor-side 0.16 constant into output-torque firmware conversion. [V3 software manual, p. 31](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

## Hardware and connections

### CubeMars AK10-9 V3.0 Actuator Motor Compact High-Torque Power Module <a href="#cubemars-ak10-9-v3.0-actuator-motor-compact-high-torque-power-module" id="cubemars-ak10-9-v3.0-actuator-motor-compact-high-torque-power-module"></a>

Existing manufacturer figures are preserved with stable native references:

<figure><img src="../../.gitbook/assets/image (116).png" alt="Retained CubeMars AK10-9 V3.0 manufacturer illustration"><figcaption><p>Original CubeMars product illustration retained.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (117).png" alt="Retained CubeMars AK10-9 V3.0 assembly illustration"><figcaption><p>Original manufacturer reference; identify actual controller revision before servicing.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (118).png" alt="Retained CubeMars AK10-9 V3.0 engineering graphic"><figcaption><p>Original manufacturer technical/product graphic.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (119).png" alt="Retained CubeMars AK10-9 V3.0 transmission graphic"><figcaption><p>Original CubeMars illustration, not a new mechanical drawing.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (120).png" alt="Retained CubeMars AK10-9 V3.0 connection illustration"><figcaption><p>Use the versioned connector definition below for wiring.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (121).png" alt="Retained CubeMars AK10-9 V3.0 application illustration"><figcaption><p>Manufacturer application reference; system-level performance requires separate validation.</p></figcaption></figure>

### Connector orientation: V3 UART differs from the older AK2 diagram

Use the **driver-side numbered drawing** in the AK60-4820-1C-A2 manual, PDF p. 7. Do not infer pin numbering from a cable-facing photograph.

| Interface              | Numbered pins in that drawing                                     |
| ---------------------- | ----------------------------------------------------------------- |
| UART A 1257WR-S-3P     | 1 GND; **2 RX into driver; 3 TX from driver**                     |
| Combined XT30PW(2+2)-M | 1 supply+; 2 supply−; 3 CAN-H; 4 CAN-L                            |
| Matching harness       | A 1257H-3P serial; XT30(2+2)-F power/CAN, according to the manual |

This 3-pin UART definition reverses RX/TX relative to the AK2.0 manual's numbered serial table. The labels and actual board-specific drawing take precedence; **do not reuse an AK80-64 harness assumption**. The public instruction does not establish universal 5 V UART tolerance, so use the matched manufacturer interface. CAN is a differential bus requiring a transceiver, not a direct UART/GPIO connection. [Inspected V3 connector drawing/definitions, pp. 7–8](https://www.cubemars.com/data/cms/202610/ak60-4820-1c-a2-driver-installation-instructions.pdf).

1. Secure the unloaded actuator housing and support any attached link. Keep the whole sweep, including return-to-zero motion, clear.
2. With power off, inspect controller label, keyed connector, polarity, cable strain and the actual supply limit. Prepare drive-power isolation independently of software.
3. Connect the matched power/CAN harness and setup interface. USB powers the adapter; the actuator needs its separate supported supply. Do not hot-plug combined power/data connectors.
4. For CAN, confirm 1 Mbit/s or the unit's known stored rate, ID, topology and termination at the two physical ends. Do not add a terminator at every chained motor.
5. Preserve the calibrated factory assembly. If servicing the driver/magnet, the installation manual specifies a recommended 1 mm encoder magnet air gap, maximum 3 mm and maximum 0.3 mm eccentricity; those are service-alignment values, not reasons to disassemble a functioning unit. Use the proper dimensional drawing and fasteners.

### V3 controller indicators and service dimensions

For **AK60-4820-1C-A2**, blue is power, green indicates motor operation, and red indicates a driver fault. The manual describes green and red illuminating for about two seconds during power-up before going out, while blue remains on. This differs from the older AK2 driver's green communication indication; do not require a motor-operation LED merely to establish a passive connection.

The installation drawing specifies M3 mounting hardware, ±0.15 mm general dimensional tolerance, + 0.1/−0 mm mounting-hole tolerance and ±0.16 mm PCB-thickness tolerance. Its encoder magnet gap and eccentricity requirements belong to deliberate driver service; do not disassemble a factory-calibrated actuator to check them. The listed harness uses a 100 ± 10 mm combined power/CAN cable and a 200 ± 10 mm UART cable; inspect the supplied connector and stripped-end protection before use. [Installation instruction §§3–6, PDF pp. 6–9](https://www.cubemars.com/data/cms/202610/ak60-4820-1c-a2-driver-installation-instructions.pdf#page=6)

## Software and development resources

| Resource              | Verified scope                                                                                                         |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| PC host               | **AK Series V3.23 Upper Computer for AK3.0 Motor**, linked on this exact model page                                    |
| Software manual       | **V3 Drive Software User Manual V1.0.1**, 47 pages, current October 2026 resource                                      |
| Driver installation   | AK60-4820-1C-A2 V1.0.0, hardware AK-DRV-12S-V3.00, exact-model-linked                                                  |
| CAN                   | Extended frames for servo and current V3 MIT force control; function in bits 28:8, drive ID in bits 7:0                |
| Arduino example       | Official AK3.0 demo archive; inspect its exact board/CAN peripheral dependencies and protocol revision before building |
| Driver/mechanical CAD | Separate motor 3D and driver STEP archives; neither is firmware                                                        |

[Exact product resources](https://www.cubemars.com/product/ak10-9-v3-0-kv60-robotic-actuator.html), [official download center](https://www.cubemars.com/technical-support-and-software-download.html). This is not a claim that the demo, driver or host application was compiled/executed. Old “V3.0” motor branding alone does not prove the installed software already uses the October 2026 packet format; read actual firmware first.

### Parameter management and data interpretation

The host provides Basic/Advanced configuration, real-time status/data, unit selection, control, connection, Stop and firmware update. Use **Read Parameters** and **Export Parameters** before writes; retain `.AppParams` and `.McParams` where supplied. The manufacturer warns that writing from an unread configuration can overwrite other values. [Software manual §§1.1.1–1.1.3, pp. 6–11](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

Real-time data separates input current from motor phase current and motor temperature from MOSFET temperature. Electrical rpm is not output rpm. The host's unit configuration uses **pole pairs 21** and reduction 9; read these settings before interpreting displayed RPM/rad/s/DPS. A displayed converted value and a raw CAN field may occupy different domains. [Manual pp. 11, 14, 35](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

Factory calibration is already performed according to the software manual. Motor/encoder identification is required after applicable driver replacement, phase rewiring or firmware service; it rotates/heats the motor. The manual describes approximately 10 seconds for motor identification and 45 seconds for encoder identification, followed by Write. Do not invoke these steps merely to obtain identity or solve a serial-port problem. [Manual §§1.2–1.3, pp. 15–16](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

### V3 protocol reference: servo addressing and every function

This appendix applies to **AK10-9 V3.0 KV60 with firmware matching V3 Software Manual V1.0.1**. It is a field reference, not a startup command sequence. Validate the actual board, saved limits and firmware before implementing a sender. Do not transfer the older AK2 standard-frame MIT layout, serial opcodes or temperature representation to this controller. Representable values below are encoding limits, not approved motion/current targets.

Both servo and MIT use **29-bit extended CAN data frames**, with identifier `(function << 8) | drive_id`. The drive ID occupies the low byte. Multibyte servo integers are big-endian and signed two's complement unless stated otherwise. The function-specific routines determine DLC: the generic eight-byte heading does not mean a zero-length disable must contain eight invented bytes. [V3 manual §§2.1–2.1.9, PDF pp. 23–30](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf#page=23)

| CAN function, decimal / hex         | Payload / conversion                                                                              | Meaning and boundary                                                                                                                                                                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0 / `0x00`: duty                    | Bytes 0–3: `int32(duty × 100000)`                                                                 | Signed duty ratio; not a voltage/current setpoint. GUI default window 0.005–0.95 differs from a universal actuator limit.                                                                                                                                       |
| 1 / `0x01`: current                 | Bytes 0–3: `int32(Iq_A × 1000)`                                                                   | ±60000 represents ±60 A on the wire; do not exceed the model/drive's actual limits.                                                                                                                                                                             |
| 2 / `0x02`: current brake           | Bytes 0–3: `int32(brake_A × 1000)`                                                                | Text defines 0…60000, or 0…60 A. Later examples also show negative values, so negative-brake semantics require firmware confirmation; brake is energized and can heat the motor.                                                                                |
| 3 / `0x03`: speed                   | Bytes 0–3: signed `int32 ERPM`                                                                    | Wire table ±100000 ERPM; GUI demonstration ±50000 ERPM. Electrical rpm is not mechanical output rpm.                                                                                                                                                            |
| 4 / `0x04`: position                | Bytes 0–3: `int32(position_deg × 10000)`                                                          | ±360000000 encodes ±36000°. Position-only motion uses default maximum speed/acceleration.                                                                                                                                                                       |
| 5 / `0x05`: set origin              | One-byte selector                                                                                 | `0`: temporary origin, cleared by power loss; `1`: permanent zero with automatic parameter saving. Changes coordinates/persistent state.                                                                                                                        |
| 6 / `0x06`: position/velocity       | Bytes 0–3: signed position × 10000; bytes 4–5: signed speed/10; bytes 6–7: signed acceleration/10 | Eight bytes. Speed count × 10 gives ERPM. See the source discrepancies below before using the acceleration or position-range prose.                                                                                                                             |
| 8 / `0x08`: MIT/force control       | Eight packed bytes in the separate table below                                                    | One function supports position, velocity and feedforward torque through different gains/targets. It is not AK2's standard-frame MIT.                                                                                                                            |
| 15 / `0x0F`: disable                | **No data**, DLC 0 in the routine                                                                 | Disables drive; one `0x29` feedback with status byte `0x77` acknowledges it. Torque removal may release a load.                                                                                                                                                 |
| 16 / `0x10`: feedback configuration | Bytes 0–5 reserved; bytes 6–7 unsigned configuration word, big-endian                             | Bit 15 enables additional `0x2A` position feedback; bit 14 enables single-turn position mode, 0–360° reference. Writes **flash** and survives power loss; never stream as a control-loop command. Preserve reserved fields according to the confirmed firmware. |

**Do not hide source defects in an implementation.** In §2.1.7 the position-range prose says ±360000°, but its × 10000 routine and the preceding position section imply ±36000° for the stated ±360000000 integers. The speed prose repeats a negative upper endpoint although `int16` has a positive upper endpoint. The acceleration paragraph uses ERPM/s² while the serial example describes ERPM/s. The documented packing factors are useful, but the physical ramp-unit definition and accepted ranges need an exact-firmware confirmation before motion. Signed negative ramp bytes in a demonstration do not establish a safe deceleration contract. The printed sender also accepts speed/ramp arguments as `int16` before dividing by 10; its argument width can truncate values that the wire field itself could represent. Review narrowing and scaling together rather than copying that helper unchanged.

### V3 MIT packing and exact-model ranges

For this generation, gains come first. Let `KP`, `KD`, `P`, `V` and `T` denote unsigned quantized values. The entire command uses function **8**, extended CAN, DLC 8. [V3 manual §2.2, PDF pp. 30–34](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf#page=30)

| Byte | V3 MIT command content                          |
| ---- | ----------------------------------------------- |
| 0    | `KP[11:4]`                                      |
| 1    | Upper nibble `KP[3:0]`; lower nibble `KD[11:8]` |
| 2    | `KD[7:0]`                                       |
| 3, 4 | `P[15:8]`, `P[7:0]`                             |
| 5    | `V[11:4]`                                       |
| 6    | Upper nibble `V[3:0]`; lower nibble `T[11:8]`   |
| 7    | `T[7:0]`                                        |

| AK10-9 V3.0 KV60 field    | Bits / exact model row                                                   |
| ------------------------- | ------------------------------------------------------------------------ |
| Position                  | 16 bits, −12.56…+12.56 rad                                               |
| Velocity                  | 12 bits, −28…+28 rad/s                                                   |
| Feedforward output torque | 12 bits, −54…+54 N·m                                                     |
| Kp / Kd                   | 12 bits each; 0…500 / 0…5                                                |
| Output-torque conversion  | Manual coefficient 1.3137 N·m/A, with `output_torque = Iq × coefficient` |

For a field with range `[minimum, maximum]` and width `n`, the V3 routine clamps the physical value, then truncates `(value − minimum) × (2^n − 1) / (maximum − minimum)` to the integer field. The inverse is `minimum + code × (maximum − minimum) / (2^n − 1)`. This differs from the endpoint inconsistency in the older AK2 routine. A mathematically valid packed command still needs correct feedback sign, zero, gains and hardware limits. For this model, ±54 N·m is the wire window, while the product peak is 53 N·m and rated torque is 18 N·m. The motor-side 0.16 N·m/A reference is not the output-torque coefficient.

The manual's MIT position behavior combines target position, Kp and Kd; velocity behavior uses a velocity target and damping; torque behavior uses feedforward torque. Zero gains do not make arbitrary nonzero torque harmless. A position value of zero is an actual coordinate target, not “do nothing.” This V3 document does not require the older seven-`FF` plus `FC` enable packet; do not send that AK2 special pattern as a V3 status probe. [Host control demonstrations, PDF pp. 20–21; force protocol, pp. 30–34](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf#page=20)

### V3 feedback types, units and fault interpretation

Periodic reporting and request/response are configurable modes. The latter replies when a valid control command is received; sending motion to make a silent drive reply is inappropriate during the passive baseline. Record actual feedback mode before interpreting silence. The manual specifies configurable **1–2000 Hz** periodic status, which is a firmware capability reference, not a recommendation to saturate a shared CAN bus. [Configuration p. 6; feedback §§2.3.1, pp. 34–35](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf#page=34)

| Extended CAN function         | Content / interpretation                                                                                                                                                                  |
| ----------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x2C` startup                | Entry/start event; the source lists marker values `FA`, `FB`, `FC`, `FD`. Preserve the received bytes rather than decoding them as measurements or assuming an undocumented event layout. |
| `0x29` live state             | DLC 8. Bytes 0–1 signed position × 0.1°; 2–3 signed speed × 10 ERPM; 4–5 signed Iq × 0.01 A; byte 6 signed driver temperature in °C; byte 7 status/fault.                                 |
| `0x2A` optional position      | Bytes 0–3 signed `int32` position × 0.01°. Do not apply the `0x29` eight-byte decoder. Only the first four data bytes are defined for this position value.                                |
| `0x29` disable acknowledgment | Status byte `0x77`, sent once after disable. This is a distinct state marker, not an ordinary fault index.                                                                                |

The `0x29` fault values are 0 none, 1 motor overtemperature, 2 overcurrent, 3 overvoltage, 4 undervoltage, 5 encoder, 6 MOSFET overtemperature and 7 stall. Temperature here is signed °C, not the AK2 MIT routine's offset-coded temperature. Position readbacks, raw encoder resolution and a retained multi-turn coordinate are different things; the optional wider position field does not prove nonvolatile multi-turn retention.

For AK10-9 V3.0 KV60, an **electrical** speed readback converts to output rpm by dividing by 21 pole pairs and the 9:1 reduction. A host display already converted to output rpm must not be divided again. Current is Iq for the named field, not supply current; the firmware output-torque coefficient and a product table's motor-side KT are not interchangeable.

### V3 UART framing and operation map

The short envelope is **`AA | payload_length | payload | CRC_hi | CRC_lo | BB`**. Length counts the opcode plus operation data, excluding header, length, CRC and footer. The longer-packet routine uses `AB` followed by a two-byte big-endian length. Its short-path test includes 256 despite a one-byte length field; avoid that boundary until firmware behavior is confirmed. CRC is computed **only over payload**, polynomial `0x1021`, initial value 0, MSB-first, no final XOR in the listed implementation. It is not an additive checksum or a CRC over the entire envelope. [V3 manual §§2.3.2–2.3.2.3, PDF pp. 36–44](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf#page=36)

| UART opcode, hex / decimal                                  | Data after opcode / purpose                                                                                                                                                                  |
| ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `41` / 65                                                   | Firmware-version operation named by the enum; use exact reply definition before parsing.                                                                                                     |
| `42` / 66, `43` / 67, `44` / 68                             | Bootloader jump, app erase, app write. Firmware maintenance only, not passive discovery.                                                                                                     |
| `45` / 69                                                   | One-shot operating values; fields described below.                                                                                                                                           |
| `46` / 70                                                   | Duty, signed big-endian `int32(duty ×100000)`.                                                                                                                                               |
| `47` / 71, `48` / 72, `4B` / 75                             | Iq, brake current, handbrake current: signed big-endian `int32(A ×1000)`. These are active controls, not read requests.                                                                      |
| `49` / 73                                                   | Speed: signed `int32 ERPM`.                                                                                                                                                                  |
| `4A` / 74                                                   | Position: signed `int32(degrees ×1000000)`; this differs from CAN position × 10000.                                                                                                          |
| `4C` / 76                                                   | Position-stream selection; the shown selector `04` produces a reply every 10 ms. Reporting state changes even though no position target is included.                                         |
| `57` / 87                                                   | Position-stream reply; four bytes interpreted as IEEE-754 float by this manual, not an AK2 scaled integer.                                                                                   |
| Selective values: **unresolved `10` / 16 versus `13` / 19** | The enum gives decimal 16 but the parameter-request/reply example uses hex `13`. Payload is a four-byte selection mask. Do not guess which opcode a delivered firmware implements.           |
| `3C` / 60                                                   | Position/velocity/acceleration: three signed big-endian `int32` values; position × 1000 degrees, velocity ERPM, electrical ramp value with unit conflict noted above.                        |
| `3D` / 61, `3E` / 62, `3F` / 63                             | Multi-turn, single-turn, reserved mode per enum. The V3 section does not fully define their data/persistence semantics; do not copy the older AK2 payloads.                                  |
| `40` / 64                                                   | Set origin per enum; exact V3 UART selector/persistence semantics are not fully specified here. Use the documented CAN origin definition or matched host workflow only after identification. |
| `60` / 96                                                   | MIT serial: **five signed big-endian `int32` fields** in order position, velocity, torque, Kp, Kd; each scaled × 1000. It is not the eight-byte CAN quantized layout.                        |

The current manual's data-conversion code reads big-endian 32-bit bit patterns then reinterprets them as floats for serial angle feedback. Its example bytes and numeric angle annotations are not a sufficient conformance capture. Validate length, CRC, opcode and firmware before decoding; never treat a plausible float as proof that a packet is from this protocol.

### V3 serial status fields and documented ambiguities

A full `45` status reply lists this sequence: opcode; MOS and motor temperatures (two bytes each, signed ÷10 °C); output, input, Id and Iq currents (four bytes each, signed ÷100 A); duty (two bytes, signed ÷1000); speed (four-byte signed ERPM); supply voltage (two-byte signed ÷10 V); 24 reserved bytes; serial fault byte; four-byte outer-loop position float; drive-ID byte; six reserved bytes; Vd and Vq (four-byte signed ÷1000 V each); then four-byte current-control mode, inner-encoder float and outer-encoder float. [V3 manual pp. 36–39, 41–44](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf#page=36)

This listed structure totals **85 payload bytes** including opcode, matching the prose length `55` hex, but the example begins with length `49` hex (73). The first 73 bytes through Vq form the shorter structure; the additional three four-byte fields account for the difference. Accept only the actual validated length and the exact firmware schema; do not read beyond a short packet or assume missing encoder fields are zero. No new UART hardware parser is claimed tested here.

For selective replies, bits 0–8 request MOS temperature, motor temperature, output current, input current, Id, Iq, duty, speed and input voltage. Bits 9–14 are reserved; bit 15 requests fault, bit 16 a four-byte position float and bit 17 the one-byte drive ID; remaining bits are reserved. Replies contain selected fields in ascending bit order with the selection mask. This is a **read selection mask**, distinct from CAN function 16's persistent feedback-configuration word.

Serial fault numbering differs from CAN. The listed sequence starts with 0 none, 1 overvoltage, 2 undervoltage, 3 driver, 4 absolute overcurrent, 5 FET overtemperature, 6 motor overtemperature, 7/8 gate-driver over/undervoltage, 9 MCU undervoltage, 10 watchdog-reset and 11 SPI encoder, followed by low/high sin/cos-amplitude faults. The printed V3 enum duplicates those last two names before its flash/current-offset/current-imbalance entries, so numbering after that point cannot be treated as a clean, verified map. Preserve the raw serial code and obtain the exact firmware enum; do not import AK2's later-number mapping or CAN's seven-code map.

### V3 parameter, calibration and recovery reference

| Official manual chapter              | Original procedure / expected checkpoint                                                                                                                                                                                                                                                                                                                                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Basic configuration, pp. 6–7         | Read motor/encoder parameters and communication state first: CAN reporting mode, CAN rate, feedback rate, ID and serial baud. Identify one motor before assigning IDs. Motor and encoder identification are active operations, not reads.                                                                                                                                                               |
| Advanced settings, pp. 7–9           | Read the entire configuration before edits, export both AppParams and McParams where supplied, and retain model/winding/firmware with them. Loading/restoring values in the host is distinct from writing them to the drive. If parameters are corrupted, use only that exact motor's defaults; never a neighboring model's file.                                                                       |
| Status/data/language, pp. 10–12      | Record hardware/software/firmware, parameter state, operating mode and faults. Distinguish DC input current, motor/phase current, D/Q current/voltage, electrical speed, rotor position and inner/outer encoder angles. CN/EN changes presentation, not units or calibration.                                                                                                                           |
| Controls/unit conversion, pp. 12–14  | Multi-turn GUI reference is ±100 turns; single-turn reference 0–359°. Set current position as zero changes coordinates; Return to Zero moves at maximum speed. Enter verified pole pairs/reduction for display conversion, then compare raw and converted values without double scaling.                                                                                                                |
| Connection/Stop, pp. 14–15           | Refresh/select the actual port and saved baud, then Connect Port. “Connected to COMX” proves a host port opened, not correct motor identity or a safe startup configuration. Stop experiment is a software operation, not a verified independent safety stop or proof of torque removal.                                                                                                                |
| Calibration, pp. 15–16               | Factory-commissioned units do not need routine recalibration. After the documented driver/phase/firmware changes, use an unloaded isolated fixture: Read → Motor Identifications → Encoder Identifications → Write. The guide illustrates roughly 10 s then 45 s, with motion/noise/heating; observe completion state rather than relying on a timer. Repeated calibrations can rapidly heat the motor. |
| Servo/MIT demonstrations, pp. 16–21  | Select constrained position/velocity/acceleration when appropriate; position-only and speed modes can use maximum default dynamics. Current/torque/duty/braking modes can accelerate or heat an unloaded motor. The published gains and large trajectories are demonstrations, not this mechanism's tuning recipe.                                                                                      |
| Firmware update, p. 22               | Back up exact parameters first; select matching firmware, Jump to IAP, Upload (the printed UI label is “Ipload”), wait for 100%, then Jump to App and allow the documented 5 s restart interval. Re-read version/status and perform calibration only where required. No alternate-board recovery image or forced erase sequence is established.                                                         |
| Protocol/example chapters, pp. 23–47 | Use the on-page tables above for ID, payload and unit review. The original final command examples are active trajectories; their motor ID and numerical targets are not defaults to transmit. Check a planned implementation against known captures and physical limits before commissioning.                                                                                                           |

The separate **AK60-4820-1C-A2 installation manual V1.0.0** covers this controller’s electrical ratings, driver-side connector orientation, R-LINK connections, indicators and driver-replacement/alignment precautions. Those hardware facts remain in Hardware and connections above; the software protocol does not change its numbered CAN pins. [Exact controller manual](https://www.cubemars.com/data/cms/202610/ak60-4820-1c-a2-driver-installation-instructions.pdf).

[V3 Software Manual V1.0.1, full source](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf). This reference retains unresolved source defects visibly rather than claiming a compiled or hardware-tested implementation. The original offline feedback example decodes only the stated CAN frame; it does not exercise UART, persistent settings, calibration, firmware update or motion.

## Getting started

### Read identity and parameters before control

1. Fixture the unloaded, supported actuator and verify AK10-9 V3.0 KV60 plus actual driver/firmware. Confirm the V3 wiring diagram and supply before power.
2. Install the matched V3 host/interface driver from official resources. Open the host, choose **Refresh Port**, select the observed adapter port and its documented communication baud, then **Connect Port**. Do not guess a UART rate from the CAN 1 Mbit/s value.
3. Confirm the transition from **Not connected** to **Connected to COM…**, then read **Real-time Status** for hardware/software/motor firmware and faults. Opening a host port alone is only an adapter checkpoint.
4. In Configuration, use **Read Parameters** and **Export Parameters**. Record motor model, pole pairs, gear ratio, ID, CAN rate, feedback mode/rate and current/speed/temperature limits.
5. Compare reported voltage/temperature and encoder fields with the physical setup. Leave motor/encoder identification, zero-return, control activation, feedback-configuration writes and firmware update untouched during the first baseline.

**Expected result:** readable matching identity/status and a preserved parameter baseline without sending a movement target. If the host or actual board uses a different firmware generation, stop and obtain that release's manual before using the packet examples below. [Host connection/status/read functions, manual pp. 6–15](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

### Original passive V3 feedback decoder

For a unit already configured to emit periodic feedback, capture its **extended** `0x29` function frame without sending a control command. V3 supports periodic and request-response feedback modes. No periodic packet in request-response mode is not itself a drive fault; do not send a force-control or zero command simply to provoke feedback. [Software manual pp. 6, 34–35](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

Save this original Python 3 example as `decode_ak10_v3.py`. It accepts text only and does not open any serial/CAN interface.

```python
import argparse
import struct

p = argparse.ArgumentParser()
p.add_argument('identifier', help='extended CAN identifier such as 0x2901')
p.add_argument('payload', help='eight hexadecimal data bytes')
a = p.parse_args()
identifier = int(a.identifier, 0)
assert 0 <= identifier <= 0x1fffffff and identifier >> 8 == 0x29
raw = bytes.fromhex(a.payload)
assert len(raw) == 8
position, speed, iq, temperature, error = struct.unpack('>hhhbB', raw)
electrical_rpm = speed * 10.0
output_rpm = electrical_rpm / 21.0 / 9.0
print('drive_id=', identifier & 0xff)
print('reported_position_deg=', position / 10.0)
print('motor_electrical_ERPM=', electrical_rpm)
print('calculated_output_rpm=', output_rpm)
print('iq_A=', iq / 100.0, 'driver_C=', temperature, 'fault=', hex(error))
print('Do not infer output torque from a motor-side KT without firmware scope.')
```

```bash
python3 decode_ak10_v3.py 0x2901 "0000076200001900"
```

**Expected result for these synthetic bytes:** ID 1, reported position 0°, 18900 ERPM, calculated output 100 rpm, 0 A, 25 °C and fault 0. They are constructed test input, not a captured motor frame or a command to transmit. The conversion uses the exact model's 21 pole pairs and 9:1 ratio, as stated in the V3 feedback formula. Optional `0x2A` position feedback is a different 4-byte format; reject it in this 8-byte decoder rather than silently reading the wrong position. [Manual pp. 34–35](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

### Bounded movement after commissioning

6. Review units, stored zero, current/speed bounds and a low-energy stop/disable test before motion. Begin from the current measured pose, empty fixture and a clear return path.
7. Use the matched host's position-velocity mode with conservative fixture-specific limits and one small displacement. Avoid the generic position-only mode's maximum-speed/default-acceleration behavior.
8. Observe direction, feedback and faults; support the mechanism before removing torque. Normal disconnect/closing a host or Ctrl-C is not a physical emergency stop.

The V3 **Return to Zero** control is explicitly described as operating at maximum speed. It is not an initial communication test. “Stop experiment” and “disable torque” are different functions; the protocol includes function 15 for disable and reports `0x77` in the feedback status for that operation. Keep those states distinct from ordinary fault codes. Feedback-message configuration(function 16) writes flash; it is not a setting to stream at control-loop frequency. [Manual pp. 13, 15, 23, 29](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

## Troubleshooting and FAQs

| Symptom                                   | Diagnosis and bounded recovery                                                                                                                       |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB opens, no motor identity              | Verify adapter/harness, external supply, port baud and actual controller firmware. USB alone does not power the actuator.                            |
| Old MIT sender fails                      | Match V3 extended function 8 and payload order; do not reuse AK2.0 standard-frame packing or enable bytes.                                           |
| Output speed wrong by 189 ×               | Recheck ERPM, 21 pole pairs and 9:1 reduction; don't apply them twice to already converted host values.                                              |
| Unexpected fast movement toward zero      | The Return to Zero control uses maximum speed. Stop/support, inspect zero/target and use bounded position-velocity control only after commissioning. |
| No periodic state                         | Check configured periodic versus request-response mode. Do not equate silence with permission to send enable or torque commands.                     |
| Parameters become incorrect after a write | Preserve/read the current configuration; use only this model's parameter file. Avoid importing an AK2.0 or another KV profile.                       |
| Temperature rises during identification   | Identification is an active no-load maintenance operation. Stop repeated cycles, allow cooling and inspect friction/wiring before retrying.          |

### Firmware and recovery

Preserve parameters, actual firmware version and model before updating. The current V3 manual describes selecting the corresponding firmware, **Jump to IAP**, upload to 100%, then **Jump to App** and a five-second wait. Recalibration requirements follow the exact service change. The old AK2.0 Bootloader/Download sequence is not a universal replacement for this workflow. Use stable power and a supported interface; verify identity/readback again before any control activation. [V3 firmware and calibration, manual pp. 15–16, 22](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

## Downloads and technical documents

### Dimensions <a href="#dimensions" id="dimensions"></a>

<figure><img src="../../.gitbook/assets/image (123).png" alt="Existing CubeMars AK10-9 V3.0 dimensional drawing"><figcaption><p>Original dimensioned graphic retained. Select the actual housing/output bolt pattern, bracket thickness and thread depth before fabrication.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (122).png" alt="Existing CubeMars AK10-9 V3.0 performance chart"><figcaption><p>Original performance chart retained; read operating conditions and axes together.</p></figcaption></figure>

### Resource <a href="#resource" id="resource"></a>

| Direct manufacturer resource                                                                                                              | Scope / access distinction                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| [V3 software manual](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf)               | V1.0.1, 47 pages, read; host, calibration, controls, firmware, servo/MIT CAN and serial protocols                    |
| [AK60-4820-1C-A2 installation instruction](https://www.cubemars.com/data/cms/202610/ak60-4820-1c-a2-driver-installation-instructions.pdf) | V1.0.0, 9 pages, read; voltage/current, numbered connectors, installation and indicators                             |
| [V3.23 host ZIP](https://www.cubemars.com/data/cms/202606/ak-series-v3-2-3-upper-computer-for-ak-3-0-motor.zip)                           | Exact-model-listed host; not executed                                                                                |
| [Current motor 3D STEP/X\_T ZIP](https://www.cubemars.com/data/cms/202608/ak10-9-v3-0-robotic-actuator-3d-drawing.zip)                    | Match mechanical revision; not a driver image                                                                        |
| [Driver STEP ZIP](https://www.cubemars.com/data/cms/202604/driver-ak60-4820-1c-a2.zip)                                                    | Separate driver-board mechanical model                                                                               |
| [Official Arduino AK3.0 demo ZIP](https://www.cubemars.com/data/cms/202603/arduino-demo-for-ak-3-0-series-motor.zip)                      | Check its board/CAN dependencies and firmware packet generation before building                                      |
| [Current motor 2D drawing entry](https://www.cubemars.com/data/cms/202602/ak10-9-v3-0-robotic-actuator-2d-drawing.pdf)                    | Manufacturer-listed; direct response did not provide a readable PDF in this review; native dimension figure retained |
| [Original AK10-9 KV60 V3.0 sheet](https://www.cubemars.com/images/file/20241126/1732601780310205.pdf)                                     | Original reference retained; direct response unreadable here                                                         |
| [Original AK Series manual v3.0.1](https://www.cubemars.com/images/file/20241217/1734428582786471.pdf)                                    | Historical model-era reference; match actual firmware before using older layouts                                     |
| [Original model 3D ZIP](https://www.cubemars.com/images/file/20250114/1736835456393125.zip)                                               | Historical mechanical resource retained separately                                                                   |

The V3 software manual's complete topic map is configuration/limits/import-export(pp. 6–10), status/data/units/connection/Stop(pp. 10–15), calibration(pp. 15–16), servo/MIT controls(pp. 16–22), firmware(p. 22), servo functions(pp. 23–30), force-control format/model ranges(pp. 30–34), CAN/serial feedback(pp. 34–43), and command examples(pp. 44–47). The on-page protocol reference covers the core layouts and identifies source contradictions. Original documents retain diagrams and official active-control examples; the original local example implements only passive feedback decoding.

## References and validation

Reviewed **24 November 2026**: exact manufacturer model/specifications/download entries, V3 software V1.0.1 and AK60 installation V1.0.0. Important numbered connector and software protocol pages were visually/textually inspected. Original native images and download references remain intact.

**Validation:** source reviewed. Host/SDK execution, Arduino compilation, firmware flashing, serial/CAN traffic, calibration, thermal/load testing and motor movement were **not run**. The decoder sample is synthetic and expected; no measured motor output is claimed. The listed 2D/legacy-sheet access gaps are distinct from the read installation/pinout documents.
