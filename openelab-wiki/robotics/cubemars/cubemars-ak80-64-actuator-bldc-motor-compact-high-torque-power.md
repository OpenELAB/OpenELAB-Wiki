---
description: >-
  Commission the AK80-64 KV80 With Driver option with verified power/connectors,
  AK2.0 parameter backup and a passive servo-feedback decoder before motion.
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

# CubeMars AK80-64 Actuator BLDC Motor Compact High-Torque Power

{% hint style="info" %}
[**View CubeMars AK80-64 KV80 actuator with driver on OpenELAB**](https://openelab.io/products/cubemars-ak80-64-actuator-motor)

**Model:** AK80-64 KV80 · **SKU:** `CubeMars-AK80-64D` · **Option:** actuator **With Driver**; RUBIK LINK V2.0 is a separate accessory option
{% endhint %}

## Product overview

### Description <a href="#description" id="description"></a>

The AK80-64 KV80 combines a brushless motor, a 64:1 planetary reducer, a single 14-bit motor encoder and an integrated controller. It is a low-speed, high-torque joint actuator, with 48 N·m rated and 120 N·m peak output torque. This guide uses the **AK2.0-era driver/manual family linked for AK80-64**, not an AK10-9 V3 driver recipe. First obtain a parameter/status baseline without issuing motion commands. [Exact manufacturer model](https://www.cubemars.com/product/ak80-64-kv80-robotic-actuator.html), [model-specific download entries](https://www.cubemars.com/technical-support-and-software-download.html).

### Product Link <a href="#product-link" id="product-link"></a>

The verified global-store selection is **With Driver / CubeMars-AK80-64D**. [The original regional listing](https://openelab.de/products/cubemars-ak80-64-aktuator-bldc) is retained separately. “Without debug board” describes omission of the external setup adapter, not omission of the integrated actuator drive. Selecting RUBIK LINK buys the adapter only. Match the received controller label/firmware to the manual before wiring or importing parameters. [Verified kit/option description](https://openelab.io/products/cubemars-ak80-64-actuator-motor).

## Applications

AK80-64 is suited to slower high-load joints, robot research mechanisms and bench actuator rigs where 64:1 reduction is useful. Size a mechanism from its complete torque-speed cycle, not 120 N·m alone. Check acceleration, impacts, bearing reactions, mechanical stops and the supported thermal duty cycle. Its published backdrive torque and backlash affect feel and positioning; it is not an ideal direct-drive torque source.

Keep early testing unloaded and fixture the housing independently of the output. An exoskeleton application additionally needs application-specific sensing, limits and human protection; a motor's product application list does not establish system certification. [Manufacturer application/specification reference](https://www.cubemars.com/product/ak80-64-kv80-robotic-actuator.html).

## Specifications

### Specification <a href="#specification" id="specification"></a>

| Parameter                              | AK80-64 KV80 manufacturer value / meaning                                                   |
| -------------------------------------- | ------------------------------------------------------------------------------------------- |
| Rated supply references                | 24 / 48 V; slash-separated speed values follow this same voltage order                      |
| Rated output torque / current          | 48 N·m / 7 A as published; validate actual installed cooling/duty cycle                     |
| Peak output torque / current           | 120 N·m / 19 A; not a continuous holding allowance                                          |
| Rated output speed                     | 23 / 48 rpm at 24 / 48 V respectively                                                       |
| No-load output speed                   | 37 / 75 rpm at 24 / 48 V respectively                                                       |
| Reduction / pole pairs                 | 64:1 / 21 pole pairs                                                                        |
| KV / motor torque constant             | 80 rpm/V / 0.136 N·m/A; motor-side constant is not an output torque-per-bus-unit conversion |
| Feedback                               | One 14-bit magnetic motor encoder; no independent output encoder specified                  |
| Backlash / backdrive torque            | 0.18° / 4.7 N·m manufacturer references                                                     |
| Dimensions / mass                      | Ø98 × 61.9 mm / 850 g                                                                       |
| Operating ambient                      | −20 to 50 °C; driver thermal limits do not raise the actuator's ambient rating              |
| Phase-to-phase resistance / inductance | 220 mΩ / 133.5 µH                                                                           |
| Rotor inertia / motor constant         | 564.5 g·cm² / 0.29 N·m/√W                                                                   |
| Dynamic / static bearing load ratings  | 2000 / 2520 N; not payload ratings for an arbitrary lever arm                               |
| Connectors                             | XT30PW-M power; A 1257WR-S-4P CAN; A 1257WR-S-3P UART                                       |

[Exact manufacturer specification and comparison table](https://www.cubemars.com/product/ak80-64-kv80-robotic-actuator.html). The old introductory “40 rpm” summary is superseded here by the current voltage-specific 23/48 rpm table. Gearbox backlash, encoder resolution and assembled-axis accuracy are separate quantities. A 14-bit encoder has 16384 counts per motor revolution; dividing a nominal count size by 64 is a calculation, not proof of output accuracy or retained multi-turn position.

### Drive limits and physical mounting

The current **AK Series Module Driver Manual V1.0.18**, linked for AK80-64, gives **18–52 V** allowable voltage for its listed AK-DRV-V2.1 driver variants and **1 Mbit/s CAN**. Those are controller-family limits; use them only after matching the installed board, and keep the actuator's 24/48 V operating references distinct. The driver's maximum-current rating is not a motor continuous-current rating. [Manual §§1.1–1.2, PDF pp. 8–13](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

The [current 2D drawing](https://www.cubemars.com/data/cms/202602/ak80-64-robotic-actuator-2d-drawing.pdf) shows multiple different bolt patterns, including 6 × M4 with 8 mm marked depth and 8 × M3 patterns with different 7/10 mm depths. Read the correct housing/output view and account for bracket thickness; these dimensions are **not tightening torque specifications**. Prevent fasteners from bottoming into internal parts. Do not press-fit or hammer the output to compensate for a bracket alignment error.

## Hardware and connections

### Power, UART and CAN pin definitions

The following numbers use the **driver-side orientation drawn in manual §1.2.1, PDF p. 12**, not a mirrored cable-side view. Inspect the actual harness against the drawing before power. [Connector diagram and definitions, pp. 12–13](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

| Interface  | Driver pin    | Meaning                                                         |
| ---------- | ------------- | --------------------------------------------------------------- |
| UART 3-pin | 1             | Signal ground                                                   |
| UART 3-pin | 2             | Driver TX, to adapter RX                                        |
| UART 3-pin | 3             | Driver RX, from adapter TX                                      |
| Power XT30 | 1 / 2         | Negative / positive in the manual's numbered view               |
| CAN 4-pin  | 1 / 2 / 3 / 4 | CAN-L / CAN-H / CAN-H / CAN-L; duplicated bus pair for chaining |

UART is a logic-level serial interface, not a ±RS-232 port and not RS485. Use the matched R-LINK/harness for initial setup; the reviewed manual does not establish a universal exposed-UART tolerance for arbitrary 5 V USB adapters. The R-LINK 5-pin connector has a **different** pin sequence from the motor's 3-pin UART. Match both ends, not wire colors. [R-LINK and cable definitions, manual §§1.4, 2.2, 3](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

1. Fixture the unloaded housing and leave room for its full possible output movement. Support any attached link before torque is removed; avoid hand restraint as a substitute for mounting.
2. With drive power off, connect the approved power and signal harnesses. Verify DC polarity at the connector, protective current limits and a means to isolate drive power independently of the host application.
3. Use a supply matching the actual motor/controller label. Account for regeneration when decelerating a load; an ordinary bench supply may not absorb returned energy. Do not treat an over-voltage trip as an energy dump circuit.
4. For CAN, use a real transceiver/adapter, correct bitrate and termination only at the physical bus ends. Avoid a star network made from long branches. For initial R-LINK setup, follow its dedicated harness diagram.
5. Connect R-LINK USB to the host separately. USB powers the interface, **not the actuator drive**. Keep CAN, UART, USB and motor supply roles explicit.

### AK2 R-LINK adapter and diagnostic indicators

The AK2 manual's R-LINK is a **5 V interface accessory**, rated ≤30 mA standby, 39.2 × 29.2 × 10 mm, −20 to 65 °C ambient and 85 °C maximum board temperature. Those are adapter ratings, not motor supply or UART-tolerance ratings. Its numbered five-pin connector is different from the motor UART and the later eight-pin R-LINK. [V1.0.18 §§2–3, pp. 16–19](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=16)

| AK2 R-LINK connector pin | Definition in its own drawing        |
| ------------------------ | ------------------------------------ |
| 1 / 2                    | CAN-L / CAN-H                        |
| 3 / 4 / 5                | Adapter RX / adapter TX / signal GND |

The documented harness connects R-LINK USB to the PC, its five-pin branch to the adapter, its four-pin CAN branch to the motor CAN connector and its three-pin UART branch to the motor UART. Check every branch rather than joining equal pin numbers across different connectors. The accessory list describes 30 AWG signal leads and 16 AWG power leads; a stock cable description is not an unlimited current or chain-length rating. Model-specific capacitors, MOSFETs and other board parts listed for different actuators do not become this SKU's packing list.

| Indicator location | Documented interpretation                                                                                              |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| AK2 motor driver   | Blue power; green communication; red drive fault. Isolate a suspect unit before repeated power attempts.               |
| AK2 R-LINK         | Green power; blue UART TX activity; red UART RX activity. A red adapter activity LED is not the motor's red fault LED. |

### CubeMars AK80-64 Actuator BLDC Motor Compact High-Torque Power <a href="#cubemars-ak80-64-actuator-bldc-motor-compact-high-torque-power" id="cubemars-ak80-64-actuator-bldc-motor-compact-high-torque-power"></a>

The existing manufacturer illustrations remain available below. They complement the versioned pinout/manual; they do not authorize a different controller board or firmware.

<figure><img src="../../.gitbook/assets/image (184).png" alt="Retained CubeMars AK80-64 manufacturer illustration"><figcaption><p>CubeMars original product illustration retained from this guide.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (185).png" alt="Retained CubeMars AK80-64 assembly illustration"><figcaption><p>CubeMars original assembly/product illustration.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (187).png" alt="Retained CubeMars AK80-64 engineering illustration"><figcaption><p>Original CubeMars technical/product reference.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (188).png" alt="Retained CubeMars AK80-64 transmission illustration"><figcaption><p>Original CubeMars illustration; use current drawing for fabrication.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (189).png" alt="Retained CubeMars AK80-64 connector/product illustration"><figcaption><p>Original CubeMars illustration; compare the actual board revision before wiring.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (190).png" alt="Retained CubeMars AK80-64 application illustration"><figcaption><p>Manufacturer application reference, not a completed-system validation.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (191).png" alt="Retained CubeMars AK80-64 specification graphic"><figcaption><p>Original manufacturer specification graphic; current numerical conditions are stated in the table above.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (192).png" alt="CubeMars AK80-64 performance graph"><figcaption><p>Original CubeMars performance graph. Interpret voltage, speed, current and torque together rather than selecting independent maxima.</p></figcaption></figure>

## Software and development resources

| Resource / route     | Exact scope                                                                                                          |
| -------------------- | -------------------------------------------------------------------------------------------------------------------- |
| AK2.0 upper computer | **AK Series V1.32 Upper Computer for AK2.0 Motor**, listed specifically under AK80-64 in the current download center |
| Protocol/manual      | **AK Series Module Driver Manual V1.0.18**, 71 pages; servo and MIT interfaces differ                                |
| USB interface        | Matched RUBIK/R-LINK V2.0 and its documented cable/USB driver; this is a separate accessory selection                |
| Servo CAN            | Extended frame; function ID plus motor ID; periodic state upload supported                                           |
| MIT CAN              | Standard-frame packed position/velocity/gains/feedforward; limits are model-specific                                 |
| UART                 | Versioned servo/other-mode framing in the same manual; do not reuse an RS485 packet                                  |
| Firmware/parameters  | Exact **AK80-64 KV80 V2.1 firmware and parameters** package; keep servo/MIT images and parameter types separate      |

[Current model-filtered download center](https://www.cubemars.com/technical-support-and-software-download.html), [V1.0.18 manual](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf). The AK3.0 V3.23 host and V3 driver manual are a different software generation. A connector that fits or an application that opens a port does not establish compatibility.

### Read, export and write are different operations

The manual's upper-computer pages include waveform/status display, system limits, motor/encoder parameters, CAN ID/rate/timeouts, read/write, parameter export/import, mode selection, reset and firmware update. Establish a baseline using **Read Parameters**, then **Export Settings**. Preserve both **`.McParams`** and **`.AppParams`** with the motor serial/revision. Do not press Write Parameters after changing only one visible field without reading the complete current configuration first. The manufacturer warns that doing so can overwrite other parameters. [Manual §4.1, pp. 20–26](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

Calibration after driver replacement, phase rewiring or firmware update is an **active** identification operation. It can move/heat the motor and change electrical offsets. It is not required simply to inspect a correctly commissioned assembled actuator and should not be used to hide an unknown gearbox zero. Servo and MIT calibration workflows differ; reserve those workflows for a supported, unloaded fixture. [Manual §4.2, pp. 27–28](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

The manual's revision record matters: V1.0.15 added AK80-64 MIT ranges, V1.0.16 revised CAN examples/feedback and outer-loop position conversion, V1.0.17 revised serial messages, and V1.0.18 revised parameter-write, single-turn and selective-read descriptions. Its broad introductory encoder/software claims cover a family; they do not replace this motor's 14-bit encoder or authorize a V3 format. Retain the actual firmware and manual revision with any codec. [Version record, PDF pp. 5–7](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=5)

### AK2.0 protocol reference: addressing and servo functions

This reference applies to **AK80-64 with the AK2.0/V1.0.18 protocol**, not the V3 controller. It describes fields for implementation review and captured-data interpretation; it is not a sequence of commands to run. A representable field value is not a permitted operating point. Retain the configured current, speed, thermal and travel limits, support the mechanism and establish a separate power-isolation path before active control.

For servo CAN, the 29-bit extended identifier is `(function << 8) | motor_id`; the low eight bits select the configured drive. The multibyte integer fields below are **big-endian, signed two's complement**, except the one-byte origin selector. DLC follows the actual function payload, despite the generic eight-byte frame illustrations. [V1.0.18 §§5.1–5.1.7, PDF pp. 35–43](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=35)

| Function, decimal / hex            | Payload and conversion                                                         | Meaning / implementation boundary                                                                                                                                                                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 0 / `0x00`, duty                   | Bytes 0–3: `int32(duty × 100000)`; four bytes                                  | Signed duty ratio, not volts or amperes. The host's illustrated 0.005–0.95 input window is not a universal command limit.                                                                                                                        |
| 1 / `0x01`, current                | Bytes 0–3: `int32(Iq_A × 1000)`                                                | Wire reference ±60000 represents ±60 A; the motor's continuous/peak limits can be much lower.                                                                                                                                                    |
| 2 / `0x02`, current brake          | Bytes 0–3: `int32(brake_A × 1000)`                                             | CAN table specifies 0–60000, or 0–60 A. Braking is an energized, heating state, not torque-off.                                                                                                                                                  |
| 3 / `0x03`, velocity               | Bytes 0–3: `int32(ERPM)`                                                       | Table reference ±100000 ERPM; electrical speed is not output rpm. The host demonstration uses a narrower ±50000 ERPM window.                                                                                                                     |
| 4 / `0x04`, position               | Bytes 0–3: `int32(position_deg × 10000)`                                       | ±360000000 encodes ±36000°. The position-only mode moves at maximum speed; it supplies no independent speed limit in this packet.                                                                                                                |
| 5 / `0x05`, origin                 | Byte 0: `uint8` selector                                                       | `0`: temporary origin, lost on power removal; `1`: permanent zero for dual-encoder models. This AK80-64 is documented with one encoder; do not infer permanent-zero support. The table shows a range ending at 2 but does not define selector 2. |
| 6 / `0x06`, position with velocity | Bytes 0–3: position × 10000; 4–5: signed speed/10; 6–7: signed acceleration/10 | Eight-byte layout. Speed count × 10 gives ERPM. Acceleration encoding also uses a factor of 10, but the text labels its unit ERPM/s²; confirm the actual firmware's ramp-time meaning before deriving a physical acceleration limit.             |

For the last row, the position field uses the same degree scale as function 4. Speed is an `int16` reference (−32768…32767 counts); acceleration is described as nonnegative 0…32767 counts. The printed sender takes speed/ramp arguments as `int16` before scaling; do not assume its input arguments span the entire representable wire range without reviewing integer narrowing. Do not obtain a negative braking ramp by copying a signed byte pattern from another generation's example. The enum also names function 8 for MIT, but the AK2.0 manual's actual MIT command interface is the **standard-frame** layout below; the enum alone does not authorize the V3 extended-frame layout.

### AK2.0 CAN feedback and MIT packing

Servo uploads use an extended identifier with the function above the low-byte motor ID. Upload frequency is configurable over **1–500 Hz** in this manual. Different startup and live-status functions must be classified before decoding. [V1.0.18 §5.2.1, PDF pp. 44–45](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=44)

| Feedback function | Payload / interpretation                                                                                                                                              |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x09`            | Jump/start-state indication; not the live servo measurement layout.                                                                                                   |
| `0x2C`            | Servo-entry startup message; documented fixed marker `FA FB FC FD`. Classify the event rather than inventing position/current values from it.                         |
| `0x29`            | Eight bytes: 0–1 signed position × 0.1°; 2–3 signed speed × 10 ERPM; 4–5 signed current × 0.01 A; byte 6 signed driver temperature in °C; byte 7 unsigned fault code. |

For this servo feedback, faults are **0** none, **1** motor overtemperature, **2** overcurrent, **3** overvoltage, **4** undervoltage, **5** encoder, **6** MOSFET overtemperature and **7** stall. They are not the serial-status enum described later. The position field's documented ±3200° reference is narrower than the position-command range; retain wrap/coordinate context rather than using that readback as proof of unrestricted multi-turn travel.

AK2.0 MIT uses the configured motor ID as a **standard 11-bit CAN identifier**, an eight-byte command and 1 Mbit/s CAN. Let `P`, `V`, `KP`, `KD` and `T` denote the unsigned quantized fields. This layout starts with position, unlike the V3 layout that starts with gains. [V1.0.18 §5.3, PDF pp. 60–68](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=60)

| Byte | AK2.0 MIT command content                      |
| ---- | ---------------------------------------------- |
| 0, 1 | `P[15:8]`, `P[7:0]`                            |
| 2    | `V[11:4]`                                      |
| 3    | Upper nibble `V[3:0]`; lower nibble `KP[11:8]` |
| 4    | `KP[7:0]`                                      |
| 5    | `KD[11:4]`                                     |
| 6    | Upper nibble `KD[3:0]`; lower nibble `T[11:8]` |
| 7    | `T[7:0]`                                       |

| AK80-64 MIT quantizer        | Bits / source range                                       |
| ---------------------------- | --------------------------------------------------------- |
| Position                     | 16 bits, −12.5…+12.5 rad                                  |
| Velocity                     | 12 bits, −8…+8 rad/s                                      |
| Feedforward torque           | 12 bits, −144…+144 N·m                                    |
| Proportional / damping gains | 12 bits each; Kp 0…500, Kd 0…5 in the illustrated routine |

The **AK80-64-specific table on p. 63** is the range reference. The generic routine on pp. 64–68 instead contains ±30 rad/s and ±18 N·m: those are not this motor's quantizers. Likewise, a ±144 N·m encoding window does not raise the actuator's 120 N·m physical peak rating or its 48 N·m rated torque. The manual's encoder routine multiplies by `2^bits`, while its inverse divides by `2^bits − 1`; their endpoint behavior disagrees. An implementation must obtain the installed firmware's confirmed quantizer and check endpoints against known captures before transmitting; do not silently wrap the upper endpoint or claim the printed routines are a tested codec.

The eight-byte MIT reply is documented as byte 0 drive ID, bytes 1–2 16-bit position, byte 3 plus the high nibble of byte 4 12-bit velocity, low nibble of byte 4 plus byte 5 12-bit torque, byte 6 temperature and byte 7 error. The receive routine labels temperature as **raw − 40 °C**, unlike the servo frame's signed temperature byte. The reply table has a duplicated “position” label where the receive routine extracts velocity; preserve raw frames and use the matching firmware decoder rather than treating that typo as a second position field. The manual describes a standard-frame `0x00 + drive ID` reply identifier; retain both the actual arbitration ID and payload drive ID.

The special MIT eight-byte patterns contain seven `FF` bytes and a final selector: **`FC` enables control**, **`FD` exits control**, **`FE` changes the current position to zero**. All change state. `FC` is not a passive status request, `FE` is not a move to an old zero, and an exit/disable can release a gravity-loaded mechanism. The active MIT demonstrations also include default position-mode dynamics of 12000 ERPM and an acceleration reference of 40000; they must not be reused as a cautious first movement.

### AK2.0 UART framing, operations and reply fields

The short UART envelope is **`02 | payload_length | payload | CRC_hi | CRC_lo | 03`**. Length counts the command/reply opcode and its data, excluding envelope and CRC. The manual's longer-packet routine uses header `03` plus a two-byte big-endian length. Its short-path condition includes 256 although its length field is one byte: do not assume 256 is representable in the short envelope. CRC covers **payload only**, using polynomial `0x1021`, initial value 0, MSB-first, no final XOR in the listed algorithm. Serial baud rate must match the saved drive/interface configuration. These logic-level bytes are not an RS485 electrical interface. [V1.0.18 §5.2.2, PDF pp. 46–59](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=46)

| UART opcode, hex   | Payload following opcode / behavior                                                                                                                                         |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `00`               | Firmware-version operation named by the enum; use the exact firmware reply definition before parsing.                                                                       |
| `01` / `02` / `03` | Bootloader jump / app erase / app write; maintenance operations, not discovery. No generic flashing packet sequence is prescribed here.                                     |
| `04`               | One-shot operating-values read; the reply field map is below.                                                                                                               |
| `05` / `06` / `07` | Duty `int32 ×100000` / Iq `int32 ×1000 A` / brake `int32 ×1000 A`. These are active controls.                                                                               |
| `08` / `09` / `0A` | Velocity `int32 ERPM` / position `int32 ×1000000 degrees` / handbrake `int32 ×1000 A`. UART position does **not** use CAN's × 10000 scale.                                  |
| `0B`               | Position-stream selection; documented selector `04` causes position output every 10 ms. Enabling a stream changes reporting state.                                          |
| `16`               | Position reply, four-byte signed position ÷10000 in the listed routine. Do not reuse the position-command scale.                                                            |
| `32`               | Selective values request: four-byte mask, followed in replies by selected fields in mask order.                                                                             |
| `5B`               | Position/velocity/acceleration: three big-endian `int32` values; position × 1000 degrees, velocity in ERPM, acceleration in the command's documented electrical ramp units. |
| `5C` / `5D` / `5E` | Multi-turn ±100 turns / single-turn / reserved position mode. The demonstrated `5C`/`5D` packets carry four zero bytes; reserved `5E` has no usable control contract.       |
| `5F`               | Set the current position as zero; the demonstrated payload is one byte `01`. Persistence/support must match the installed encoder/firmware.                                 |
| `65`               | Shortest-path return to relative zero; an active movement operation documented outside the initial enum.                                                                    |

For a `04` reply, the documented payload is 73 bytes including the opcode. All offsets below start **at payload byte 0**, after removing the envelope and checking length/CRC. [Values acquisition, PDF pp. 49–52](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=49)

| Payload offsets            | Field / conversion                                                                     |
| -------------------------- | -------------------------------------------------------------------------------------- |
| 0                          | Reply opcode `04`                                                                      |
| 1–2 / 3–4                  | MOS / motor temperature, signed 16-bit ÷10 °C                                          |
| 5–8 / 9–12 / 13–16 / 17–20 | Output / input / D-axis / Q-axis current, signed 32-bit ÷100 A                         |
| 21–22 / 23–26 / 27–28      | Duty signed 16-bit ÷1000; speed signed 32-bit ERPM; supply voltage signed 16-bit ÷10 V |
| 29–52 / 53                 | 24 reserved bytes / serial fault enum                                                  |
| 54–57 / 58                 | Outer-loop position signed 32-bit ÷1000; drive ID byte                                 |
| 59–64 / 65–68 / 69–72      | Six reserved bytes / Vd ÷1000 V / Vq ÷1000 V, signed 32-bit voltage fields             |

Selective-read mask bits 0–8 request MOS temperature, motor temperature, output current, input current, Id, Iq, duty, speed and input voltage respectively. Bits 9–14 are reserved; bit 15 requests fault, bit 16 position and bit 17 drive ID; higher bits are reserved. The selective position conversion is listed as signed 32-bit ÷1000000, different from the full-status position and streamed-position scales. Parse the opcode/mask first; a universal “position scale” across all three reply types is incorrect.

The **serial** fault enum on p. 52 is: 0 none; 1 overvoltage; 2 undervoltage; 3 driver; 4 absolute overcurrent; 5 FET overtemperature; 6 motor overtemperature; 7/8 gate-driver over/undervoltage; 9 MCU undervoltage; 10 watchdog reset; 11 SPI encoder; 12/13 sin/cos amplitude low/high; 14 flash corruption; 15/16/17 current-sensor channel offsets; 18 current imbalance. Preserve the numeric value and originating transport when recording a fault.

MIT UART uses the same `02`/`03` envelope and CRC but a **different operation family**: `14` carries terminal text and `15` returns printed text. The documented `encoder` operation emits electrical angle (0…2π), mechanical angle and raw encoder counts (0…16383). The `calibrate` terminal operation rotates the motor, heats it and changes calibration; `exit` leaves debugging. These are not servo `04` replies, and calibration is not an encoder-read prerequisite on a factory-calibrated unit. [MIT serial, PDF pp. 69–71](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=69)

### AK2.0 parameter, calibration and recovery decisions

| Manual area                                         | On-page engineering procedure / expected checkpoint                                                                                                                                                                                                                                                                                                                                                                                                                 |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Waveforms / system / motor parameters, pp. 20–23    | Read current, temperatures, rotor/encoder signals, DQ values and position error alongside supply. Separate voltage/current/power/temperature/duty protection limits from current/speed-loop gains, encoder offset and reduction settings. Preserve units and firmware with exports.                                                                                                                                                                                 |
| Application / read/write / import/export, pp. 23–26 | Read the whole current configuration first; export both `.McParams` and `.AppParams`. Import loads a candidate configuration into the host; writing commits host parameters. Compare motor/winding/drive revision before applying defaults. The illustrated Restore Factory feature is not open. System Reset restarts the motor; it is not a harmless read.                                                                                                        |
| Servo calibration, p. 27                            | Required after the documented driver/phase/firmware changes, not routine identification. On an unloaded isolated fixture, the manual's stages are Measure R/L → Measure Lamba → Update → Start → Update. Confirm each stage in the matching host before saving; no arbitrary gains or another motor's parameters.                                                                                                                                                   |
| MIT calibration, pp. 27–28                          | Enter the matched MIT/debug environment only for deliberate service. Calibration rotates the motor and ends with an electrical-offset report and automatic restart. Retain the offset/version and re-read identity afterward; the manual's illustrated current/time are not acceptance limits for every assembled mechanism.                                                                                                                                        |
| Controls, pp. 28–33                                 | Single-turn GUI reference is 0–359°, multi-turn ±100 revolutions. Position-only mode can use maximum speed; position/velocity/acceleration mode provides separate constraints. MIT position/speed/torque behaviors depend on gains and feedforward. None is a read-only startup action.                                                                                                                                                                             |
| Update and stalled progress, pp. 33–35              | Back up first, select the exact `.bin`, enter Bootloader, Download, and verify completion before the documented restart. Where servo and MIT images are separate, both require their own matched images. Stalled-upload recovery involves the Jump Guide control coordinated with a power cycle; perform it only on a supported isolated unit with no attached load. Then restore the correct defaults and complete required active calibration before re-enabling. |

[Full parameter/calibration/control/recovery sections, V1.0.18 pp. 20–35](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf#page=20). An interrupted update does not justify cross-flashing an AK3.0 binary, copying a gearbox ratio from a different actuator or repeatedly cycling a loaded mechanism. A successful download is only a firmware checkpoint; verify identity, saved settings, faults and passive feedback again before any movement.

## Getting started

### Read a known actuator before enabling it

1. Record motor, winding, board hardware and firmware labels. Confirm this is AK80-64 KV80 with the integrated drive, not a bare motor or an AK3.0 controller replacement. Inspect the exact drawing and pin numbers.
2. Fixture the unloaded motor. Verify supply polarity, supported voltage, current limit, cable condition and physical power isolation. Keep the output and any return path clear; loss of torque may allow a mechanism to fall.
3. Install the matched AK2.0 host tool and USB interface driver from the model's download entries. Connect the R-LINK harness and host USB as shown in manual §3. Power the actuator separately after wiring checks.
4. In the host's serial-port selector choose the observed R-LINK port. Read the reported mode/identity/status before selecting a control mode. Open **Read Parameters**, then **Export Settings**, retaining both parameter files. Inspect temperature, voltage, motor ID and error fields without sending a position/current command.
5. Confirm the drive's communication state and compare the software values with the actual supply and motor label. Preserve one screenshot/export and firmware version with the unit's record. Stop here if the ID/model/voltage is inconsistent.

**Expected result:** a readable, reproducible parameter/status baseline for one identified actuator and no commanded motion. A blue power LED alone does not establish communication. A controller responding under the wrong model profile is not a valid result. [Manual §§1.3, 3, 4.1](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

{% hint style="warning" %}
**MIT's `FF FF FF FF FF FF FF FC` is an enter-control command.** The manual also describes using it to elicit status when no state is present; it must not be treated as a passive probe. It can enable the drive. Likewise, setting a zero/origin, resetting or invoking calibration is a state-changing action. Do not send such commands during the read-only baseline. [V1.0.18 §5.3, PDF p. 60](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).
{% endhint %}

### Original offline servo-feedback decoder

For a driver already configured to upload **servo-mode state**, capture a frame without sending control requests. V1.0.18 §5.2.1 identifies an **extended** `0x29` function frame with 8 data bytes for current feedback; `0x09` indicates a jump/start state and `0x2C` a startup message, so they must not be indiscriminately interpreted as live measurements. Retain the observed arbitration ID and firmware with the capture. [Feedback definition, PDF pp. 44–45](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

Save this original decoder as `decode_ak80_servo.py`. It processes supplied text only and never opens a CAN interface:

```python
import argparse
import struct

parser = argparse.ArgumentParser()
parser.add_argument('identifier', help='extended identifier, e.g. 0x2901')
parser.add_argument('payload', help='eight bytes as hexadecimal text')
args = parser.parse_args()
identifier = int(args.identifier, 0)
assert 0 <= identifier <= 0x1fffffff, 'Not a 29-bit identifier'
assert identifier >> 8 == 0x29, 'Not V1.0.18 servo current-state function'
raw = bytes.fromhex(args.payload)
assert len(raw) == 8, 'Expected exactly eight bytes'
pos, speed, current, temperature, error = struct.unpack('>hhhbB', raw)
print('motor_id=', identifier & 0xff)
print('reported_position_deg=', pos / 10.0)
print('electrical_speed_ERPM=', speed * 10)
print('reported_current_A=', current / 100.0)
print('driver_temperature_C=', temperature, 'error_code=', error)
print('Units remain driver/firmware scoped; do not infer output torque.')
```

```bash
python3 decode_ak80_servo.py 0x2901 "0000000000001900"
```

**Expected result for this synthetic example:** ID 1, zero position/speed/current, 25 °C and error 0. These bytes are illustrative, not a motor capture. A motor's current/position domain must still be interpreted using the installed firmware: electrical rpm is not output rpm, and a motor-side torque constant is not gearbox output torque. If converting a verified electrical speed to mechanical output rpm, the arithmetic requires both 21 pole pairs and 64:1 reduction; confirm that the particular field has not already been converted before applying either factor.

### A bounded movement is a later checkpoint

6. After the passive baseline, review the actual mode, current/speed limits, saved zero reference and stop response. Start from the **current measured pose**, not an assumed zero pose. Clear the whole sweep and support any linked load.
7. In the matched host's servo control, use the documented position-velocity interface with conservative limits and one small unloaded change appropriate to the fixture. Do not copy the manual's large multi-turn demonstration angle, default MIT position example or high-gain settings as a first movement.
8. Confirm actual direction and feedback, then test the documented stop/disable behavior at low energy. “Stop” and torque removal have different mechanical consequences; keep physical isolation available separately. Do not treat closing the host application as an emergency stop.

**Expected result:** a small deliberate displacement with coherent feedback and an understood stop response. No torque/gain recipe is implied for an attached robot or gravity-loaded joint. The manual's duty/current/brake/velocity/position/origin/position-velocity modes use different units and state transitions. [Control demonstrations and protocol, manual §§4.3, 5.1–5.3](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

## Troubleshooting and FAQs

| Symptom / question                               | Checks and bounded recovery                                                                                                                        |
| ------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| No blue power indicator                          | Isolate power immediately; inspect polarity, connector seating and supply before another attempt. Do not repeatedly power a suspect drive.         |
| Power present, no green communication indication | Inspect matched interface/harness, USB port, CAN pair/termination, bitrate and actual mode. USB enumeration alone is not motor communication.      |
| Red drive-fault indication                       | Isolate/support the mechanism and inspect the decoded fault. Resolve supply/thermal/encoder/current cause before clearing or re-enabling.          |
| Strange speed or torque                          | Verify mode, firmware, frame type, signedness and electrical/motor/output units. Do not multiply already output-scaled data by 64.                 |
| Status disappears after switching mode           | Match the mode's own standard/extended frame and feedback format. Do not send MIT enable as a supposedly passive read.                             |
| Unexpected movement after zero change            | Stop and support; restore the reviewed parameter baseline where supported. A permanent origin write changes future position interpretation.        |
| Why do diagrams show several controller sizes?   | The manual covers multiple boards. Identify the installed board and its specific voltage/interface configuration; do not infer interchangeability. |
| Can 120 N·m be held continuously?                | Peak torque is a transient capability. Validate current, temperature and duty cycle against the 48 N·m rated reference and installed cooling.      |

V1.0.18's servo fault codes are 0 none, 1 motor overtemperature, 2 overcurrent, 3 overvoltage, 4 undervoltage, 5 encoder, 6 MOSFET overtemperature and 7 stall. This mapping is **for that feedback definition**; do not assign it to a different V3 protocol. [Manual pp. 44–45](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

### Firmware recovery without losing the baseline

Back up both parameter files and exact firmware/mode first. Select only the model-matched AK80-64 package, use the documented Bootloader/Download workflow with stable power, and follow the calibration requirements after firmware changes. Servo and MIT images may be separate components. A stalled update is not a reason to import another actuator's parameters or repeatedly toggle a loaded axis's power. The manual provides a specific recovery sequence; perform it only on an isolated fixture with the correct image and adapter. [Manual §4.4, pp. 33–34](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf).

## Downloads and technical documents

### Resource <a href="#resource" id="resource"></a>

| Direct official download                                                                                                                                          | Exact scope                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| [AK80-64 2D drawing](https://www.cubemars.com/data/cms/202602/ak80-64-robotic-actuator-2d-drawing.pdf)                                                            | Current drawing entry; inspected mounting pattern/depths                                          |
| [AK80-64 3D STEP ZIP](https://www.cubemars.com/data/cms/202602/ak80-64-robotic-actuator-3d-drawing.zip)                                                           | Manufacturer-listed mechanical CAD; verify revision before fabrication                            |
| [AK2.0 manual V1.0.18](https://www.cubemars.com/data/cms/202605/ak-series-driver-manual-v1-0-18-for-ak-2-0-robotic-actuator.pdf)                                  | 71-page controller/R-LINK/GUI/calibration/recovery/protocol reference, downloaded and read        |
| [AK2.0 upper computer V1.32](https://www.cubemars.com/data/cms/202602/ak-series-v1-32-upper-computer-for-ak-2-0-motor.zip)                                        | Listed for AK80-64; downloaded executables were not run in this review                            |
| [AK80-64 KV80 V2.1 firmware and parameters](https://www.cubemars.com/data/cms/202602/ak80-64-kv80-v2-1-firmware-and-parameters.rar)                               | Model-specific firmware/parameters; exact received controller/mode must match                     |
| [CH340 driver for AK2.0](https://www.cubemars.com/data/cms/202602/ch340-driver-download-for-ak-2-0-Series-motor.zip)                                              | Manufacturer-listed interface driver; verify actual USB device before installation                |
| [Official model-filtered support center](https://www.cubemars.com/technical-support-and-software-download.html)                                                   | CH340 USB driver and updated resources; retain complete model filter                              |
| [Legacy manual V1.0.15.X](https://www.cubemars.com/images/file/20240611/1718085712815162.pdf)                                                                     | Retained historical reference; protocol corrections exist in newer V1.0.18                        |
| [Legacy 2D](https://www.cubemars.com/images/file/20220211/1644551405464306.pdf) / [legacy 3D](https://www.cubemars.com/images/file/20220211/1644551412523712.zip) | Original resource URLs retained; compare revision rather than silently swapping a mechanical file |

The manual chapter index is: driver/connectors/indicators/accessories(pp. 8–15), R-LINK(pp. 16–18), wiring(p. 19), host/read-export-write(pp. 20–26), calibration(pp. 27–28), controls(pp. 28–33), firmware/recovery(pp. 33–34), servo modes(pp. 35–43), servo CAN/UART(pp. 44–59), MIT CAN/UART(pp. 60–71). The on-page protocol reference above explains the core fields and source ambiguities. Use the original document for its diagrams and official active-control examples; the original decoder implements only the stated passive servo-feedback format.

## References and validation

Reviewed **24 November 2026**: [exact AK80-64 page](https://www.cubemars.com/product/ak80-64-kv80-robotic-actuator.html), [official support center](https://www.cubemars.com/technical-support-and-software-download.html), V1.0.18 manual and current 2D drawing. Important connector diagrams and the mechanical drawing were visually inspected. Existing native manufacturer figures/resources remain retained.

**Validation:** source reviewed. Host installation, CAN/UART traffic, firmware flashing, calibration, current/temperature measurement and motor motion were **not run**. The decoder's example data is synthetic; expected output is not observed hardware output. Record the motor serial, controller revision, firmware/mode, supply and exported parameters with any real test.
