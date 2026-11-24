---
description: >-
  Identify AKH70-48 KV41 power and numbered CAN/UART connectors, review
  current/encoder discrepancies and decode passive V3 feedback before motion.
---

# CubeMars AKH70-48 V1.0 KV41 Engineering Guide

{% hint style="info" %}
[**View CubeMars AKH70-48 V1.0 KV41 on OpenELAB**](https://openelab.io/products/cubemars-akh70-48-kv41)

**Exact SKU:** `CubeMars-AKH70-48-KV41` · **Option:** actuator with integrated driver; external debug board is a separate accessory
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

The AKH70-48 V1.0 KV41 is a 48 V integrated robotic actuator with 48:1 planetary reduction and a 7 mm through-bore. Its published output is 74 N·m rated and 222 N·m peak. The two power/CAN connections support a chained bus; they do not create two independent control channels. This guide establishes a versioned wiring and passive-feedback workflow before any motion. [Exact manufacturer product](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html).

**Two specifications require confirmation for the delivered unit.** The product page's detailed table gives 18 A peak, while its comparison table gives 21 A. The same page describes two 21-bit encoders, whereas the linked AK70-4820-2D-A3 driver manual gives 21-bit inner and 15-bit outer feedback. Preserve both statements in the commissioning record; do not choose the larger current or build output-angle resolution assumptions around either encoder statement. The controller label, firmware and manufacturer confirmation must settle these before motion or precision acceptance. [Product tables](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html), [driver manual V1.0.0, p. 6](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf).

## Applications

Use this high-reduction actuator for robot joints and supported mechanisms where output torque, package length and internal cable routing matter. Calculate bearing loads, acceleration torque and heat under the actual duty cycle. A 222 N·m brief peak is not a continuous holding rating, and the 7 mm bore is not a slip ring: cables need a defined twist allowance, strain relief and bend radius throughout the complete allowed travel.

A joint can move when power is removed if gravity or stored mechanical energy acts on it. Support the mechanism before testing disable or emergency isolation. Backdrive resistance and a second encoder do not establish a safety brake or safe human-contact force.

## Specifications

| Parameter                      | Exact AKH70-48 V1.0 KV41 reference                                              |
| ------------------------------ | ------------------------------------------------------------------------------- |
| Nominal supply                 | 48 V                                                                            |
| Rated / peak output torque     | 74 / 222 N·m                                                                    |
| Rated / no-load output speed   | 28 / 35 rpm                                                                     |
| Rated current                  | 6 A; retain the manufacturer's current convention                               |
| Peak current                   | **Unresolved: detailed table 18 A; comparison 21 A**                            |
| Ratio / pole pairs             | 48:1 / 21                                                                       |
| Motor-side KV / KT             | 41 rpm/V / 0.23 N·m/A; not an output-torque firmware coefficient                |
| Envelope / mass / bore         | Ø90 × 81.5 mm / 1396 g / Ø7 mm                                                  |
| Backlash / backdrive reference | 12 arcmin / 2.22 N·m                                                            |
| Basic bearing load ratings     | Dynamic 5680 N; static 8680 N; apply the manufacturer's bearing-load definition |
| Motor ambient range            | −20 to 50 °C                                                                    |

[Manufacturer specifications and drawing](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html). These reference values do not establish an allowable radial/axial combination, impact load, duty cycle or complete system safety limit. Request those details for a load-bearing design.

The linked controller is **AK70-4820-2D-A3**, hardware **AK-DRV-12S-HD\_V2.0**, explicitly matched to AKH70-16 and AKH70-48. Its permitted input is 18–52 V; its 20 A RMS / 60 A peak board ratings are not actuator current limits. Board temperature and current capability do not override motor limits. CAN is 1 Mbit/s. [Driver manual, pp. 5–6](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf).

### Protocol range is not an operating limit

The current V3 software manual includes an AKH70-48 KV41 row with a ±5 rad/s velocity encoding range, ±280 N·m torque encoding range and output-torque coefficient 8.8123 N·m/A. Those numbers specify the wire representation; they do not authorize 280 N·m or override the physical peak, current conflict, travel limits or thermal constraints. Motor-side KT and firmware output-torque scaling occupy different domains. [V3 software manual V1.0.1, p. 31](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

## Hardware and connections

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

![CubeMars AKH70-48 V1.0 technical drawing showing 7 mm bore, mounting circles and 81.5 mm length](https://www.cubemars.com/images/202602/48-en.png)

Manufacturer drawing, CubeMars, linked from the [exact model page](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html). Confirm the supplied assembly and the downloaded engineering drawing before making fixtures. The inspected image shows 12 M3 holes with 8 mm indicated depth and 9 M5 holes with 4.5 mm indicated depth on different mounting patterns. Hole depth is not an instruction to use a screw of that exposed length: subtract bracket thickness and allow clearance against bottoming.

The combined connector integrates high-current power and CAN contacts. A visually similar plug from another AK motor is not evidence of identical numbering. Use **the driver-side numbered view on p. 9 of this controller's manual**, and verify the supplied cable with power disconnected.

| AK70-4820-2D-A3 interface          | Pin definition in its own numbered drawing                      |
| ---------------------------------- | --------------------------------------------------------------- |
| A 1257WR-S-3P UART                 | 1 GND; 2 RX into driver; 3 TX from driver                       |
| Both XT30PW(2+2)-M power/CAN ports | 1 positive; 2 negative; **3 CAN-L; 4 CAN-H**                    |
| Named signal colors                | UART ground black, RX yellow, TX green; CAN-L blue, CAN-H white |

[Inspected connector diagram and definitions, pp. 9–10](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf). The numbered CAN assignment differs from the AK60-4820-1C-A2 table used with AK10-9 V3.0. Do not transfer a numbered harness table between boards. Colors help identify the documented harness but cannot validate a third-party replacement.

1. Clamp the unloaded housing securely and support any output link. Keep the complete return-to-zero path clear, not only the intended first increment.
2. With all power disconnected, match the controller revision, connector key, polarity and harness labels. Inspect insulation and bore routing. Provide independently reachable power isolation.
3. Connect the matched UART/R-LINK setup path or CAN adapter, then the supported actuator supply. Adapter USB power is not actuator power. Do not hot-plug the combined connector.
4. Establish the bus topology before adding more nodes. The board's termination switch is right/ON for 120 Ω and left/OFF without termination. Terminate the two physical bus ends, not every actuator; use the drawing to establish switch direction.
5. Power with the output unloaded and hands clear. The manual describes blue power illumination and a roughly two-second green/red startup indication before those two go out. Persistent fault indication needs diagnosis before enabling control.

The R-LINK accessory has its own USB supply and logic-voltage selection. The actuator UART drawing is not a universal 5 V-tolerance claim. Use the matched manufacturer interface rather than connecting an arbitrary USB-TTL cable or GPIO. [Driver manual, pp. 10–13](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf).

### Exact controller service and R-LINK interface

The AK70-4820-2D-A3 board is 68.1 × 70 mm, with −20 to 65 °C ambient and 100 °C maximum board-temperature references. These do not raise the motor's 50 °C ambient limit. For deliberate driver replacement, the manual specifies M3 mounting, a recommended 1 mm encoder-magnet air gap (3 mm maximum) and 0.3 mm maximum eccentricity. The drawing's general ±0.15 mm and hole + 0.1/−0 mm tolerances are service references, not a screw-torque specification. [Board/dimension sections, pp. 6–8](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf#page=6)

The matched R-LINK in this manual is a **different accessory from AK2's five-pin adapter**. It uses 5 V input and a VCC-selection switch with **3.3 V default**, ≤30 mA standby, 73.8 × 23.6 × 14.5 mm dimensions, −20 to 65 °C ambient and 85 °C maximum board temperature. Its eight named contacts are RXD, TXD, signal GND, selectable VCC output, RTS, CTS, power GND and a separate 5 V output. Follow the actual drawing's order and the matched eight-pin-to-three-pin harness; the adapter's VCC switch does not establish arbitrary 5 V tolerance at the motor UART. Do not connect an output supply contact to a motor signal. [R-LINK definitions, pp. 12–13](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf#page=12)

Its PWR, TXD and RXD indicators are all red: PWR is steady when powered, TXD/RXD flash on serial activity. These adapter LEDs are distinct from the motor driver's blue power, green operation and red fault indicators. The supplied power/CAN and UART cable descriptions are nominal harness dimensions, not proof of unlimited daisy-chain current capacity.

## Software and development resources

### Development software and recovery <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The exact model's downloads link the **V3 driver software manual**, **AK70-4820-2D-A3 driver manual**, **AK Series V3.23 upper computer**, and its own CAD. The current software manual's model table explicitly includes AKH70-48; a broad download-center association with other AK manuals is weaker evidence than the exact model/controller pairing. Record the installed firmware and tool version before selecting the protocol. [Product resources](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html), [official support center](https://www.cubemars.com/technical-support-and-software-download.html).

The V3 manual uses extended CAN identifiers for servo and MIT/force control. Function occupies the high identifier portion; drive ID occupies the low byte. Its force-control packing is not an older AK2 standard-frame MIT example. Use the actual firmware's documented format before writing an encoder or controller. Keep a protocol version in every log rather than identifying packets solely as “MIT.” [V3 manual §§2.1–2.2](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

Read and export parameters before any write. Keep both application and motor configuration exports where offered, with model, serial, firmware, CAN ID/rate, pole pairs, ratio, limits and zero reference. The tool's electrical rpm, motor rpm and output rpm are different quantities. For this ratio, output rpm = electrical rpm ÷ 21 ÷ 48; do not apply that division a second time to a value already displayed as output rpm.

**Actions that can move or change persistent state:** motor identification and encoder calibration actively rotate the actuator; Return to Zero is described as a maximum-speed operation; a feedback-configuration command writes flash. None belongs in a first passive diagnostic. GUI Stop and Ctrl+C in a host program are not independently verified emergency power isolation. Clear and support the complete motion path before any active operation. [V3 manual, calibration/control/configuration sections](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

### V3 protocol reference: servo addressing and every function

This appendix applies to **AKH70-48 V1.0 KV41 with firmware matching V3 Software Manual V1.0.1**. It is a field reference, not a startup command sequence. Validate the actual board, saved limits and firmware before implementing a sender. Do not transfer the older AK2 standard-frame MIT layout, serial opcodes or temperature representation to this controller. Representable values below are encoding limits, not approved motion/current targets.

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

| AKH70-48 V1.0 KV41 field  | Bits / exact model row                                                   |
| ------------------------- | ------------------------------------------------------------------------ |
| Position                  | 16 bits, −12.56…+12.56 rad                                               |
| Velocity                  | 12 bits, −5…+5 rad/s                                                     |
| Feedforward output torque | 12 bits, −280…+280 N·m                                                   |
| Kp / Kd                   | 12 bits each; 0…500 / 0…5                                                |
| Output-torque conversion  | Manual coefficient 8.8123 N·m/A, with `output_torque = Iq × coefficient` |

For a field with range `[minimum, maximum]` and width `n`, the V3 routine clamps the physical value, then truncates `(value − minimum) × (2^n − 1) / (maximum − minimum)` to the integer field. The inverse is `minimum + code × (maximum − minimum) / (2^n − 1)`. This differs from the endpoint inconsistency in the older AK2 routine. A mathematically valid packed command still needs correct feedback sign, zero, gains and hardware limits. For this model, ±280 N·m is the encoding window, while the product gives 222 N·m peak and 74 N·m rated torque. The unresolved 18 A versus 21 A peak-current statements and 21+21 versus 21+15 encoder statements remain commissioning gates; the protocol table resolves neither.

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

For AKH70-48 V1.0 KV41, an **electrical** speed readback converts to output rpm by dividing by 21 pole pairs and the 48:1 reduction. A host display already converted to output rpm must not be divided again. Current is Iq for the named field, not supply current; the firmware output-torque coefficient and a product table's motor-side KT are not interchangeable.

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

The separate **AK70-4820-2D-A3 manual V1.0.0** establishes the AKH70-48/AKH70-16 board pairing, 18–52 V board input, its own numbered power/CAN and UART contacts, termination switch, indicators, R-LINK and service alignment. Those hardware definitions remain in Hardware and connections above; AK10-9’s similar combined connector has a different numbered CAN assignment. [Exact controller manual](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf).

[V3 Software Manual V1.0.1, full source](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf). This reference retains unresolved source defects visibly rather than claiming a compiled or hardware-tested implementation. The original offline feedback example decodes only the stated CAN frame; it does not exercise UART, persistent settings, calibration, firmware update or motion.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: identity, saved parameters and an offline feedback check

1. Photograph the actuator/controller markings and record the two unresolved product/manual discrepancies above. Leave any mechanical load detached or supported. Confirm power and wiring from the hardware section.
2. Open the matched V3 host, select the actual interface/port and connect to read firmware and status. **Do not click Start, Return to Zero, identification, calibration or write/import-and-write controls.** If connection itself produces movement, isolate power and investigate the installed configuration before continuing.
3. Read the existing parameters and export a backup. Record ID, bit rate, ratio, pole-pair count, temperature/fault state and firmware. A blank status display is not permission to enable the drive: feedback may be configured for request/response rather than periodic reporting.
4. If periodic feedback is already present, capture it using a compatible adapter's receive/listen facility. Preserve extended-frame status, identifier, timestamp, DLC and all bytes. Do not send an “enter control” command as a status query.
5. Use the offline example below to check raw framing and speed scaling. Compare the result with a stationary capture before interpreting angle or accepting precision. Resolve the encoder/current conflicts before planning a motion test.

**Expected result:** a recorded firmware/controller identity, saved original configuration and either a correctly classified received frame or an explicit “no periodic feedback” observation. No motion or frame transmission is needed for the software example. A synthetically valid frame proves the parser's arithmetic, not the actuator's condition.

Save as `akh_feedback.py` and run with Python 3.10 or later. This original example opens no bus or serial port. It accepts only the V3 manual's eight-byte `0x29` feedback layout; optional `0x2A` frames use another layout and are rejected.

```python
import argparse
import json
import struct

parser = argparse.ArgumentParser()
parser.add_argument("identifier", type=lambda x: int(x, 0))
parser.add_argument("payload", help="eight data bytes, hexadecimal")
args = parser.parse_args()
if not 0 <= args.identifier <= 0x1FFFFFFF:
    parser.error("identifier is outside extended CAN range")
if args.identifier >> 8 != 0x29:
    parser.error("only function 0x29 is decoded; preserve other frames raw")
try:
    data = bytes.fromhex(args.payload)
except ValueError:
    parser.error("invalid hexadecimal payload")
if len(data) != 8:
    parser.error("expected exactly eight bytes")
angle, speed, current, temperature, state = struct.unpack(">hhhbB", data)
print(json.dumps({
    "drive_id": args.identifier & 0xFF,
    "feedback_angle_deg": angle * 0.1,
    "electrical_rpm": speed * 10,
    "output_rpm_from_electrical": speed * 10 / (21 * 48),
    "reported_current_A": current * 0.01,
    "temperature_C": temperature,
    "raw_state": f"0x{state:02x}",
    "disabled_marker": state == 0x77
}, indent=2))
```

```sh
python3 akh_feedback.py 0x2901 000003f000001900
```

For this **synthetic** packet, the result is drive 1, angle 0°, 10,080 electrical rpm, calculated 10 output rpm, reported current 0 A and temperature 25 °C. State zero is the manual's normal code; `0x77` is its disabled marker and must not be indexed as an ordinary fault number. A reported angle is not a decoded raw encoder count, proof of output resolution or a retained multi-turn coordinate. [V3 software manual, feedback pp. 34–35](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf).

### Plan a motion experiment only after identity is resolved

Specify travel in physical output units, independently bounded current, low speed, a supported mechanism and an isolation method before creating a control sender. First compare measured feedback sign with a known displacement permitted by the manufacturer's assembly instructions. Save the initial zero and reboot behavior. Do not infer multi-turn retention from a single-turn encoder feature. For a new firmware/controller combination, review its startup and disable behavior before attaching a payload.

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Observation                                 | Read-first diagnosis and recovery                                                                                                                        |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Adapter connects, no motor data             | Check separate actuator supply, actual firmware/interface/baud, ID and existing feedback mode; do not enable torque to force a response                  |
| CAN data absent across multiple motors      | Inspect CAN-H/L against this board's drawing, common topology and termination at the two ends; isolate to one known node before changing IDs             |
| Output speed differs by × 21 or × 48        | Check electrical, rotor and output domains; compare raw bytes with host unit settings before changing a control gain                                     |
| Position offset after reboot                | Preserve zero/calibration state and inspect actual single-turn/multi-turn semantics; resolve the 15/21-bit output conflict rather than rescaling blindly |
| Persistent red indicator or nonzero state   | Record raw code, voltage and temperatures; stop active tests and correct the underlying condition before clearing/re-enabling                            |
| A configuration change affects other fields | Restore the saved exact-unit backup through the documented read/import/write workflow; avoid writing a blank or another model's parameter set            |

**Can I chain power through an arbitrary number of actuators?** No current-carrying capacity for an unlimited chain is established. Size the harness, upstream connector, branch protection and supply for the actual combined load; separate that analysis from CAN node addressing.

**Can I update firmware to resolve a specification conflict?** Firmware installation is not a substitute for identifying hardware. Obtain the correct release and model confirmation first. The V3 manual's recovery sequence uses Select firmware, Jump IAP, Upload, completion, then Jump App; retain stable power and wait for the documented restart. An interrupted or rejected upload needs the exact board's support procedure, not a guessed image.

## Downloads and technical documents

| Official resource                                                                                                                                                    | Use and review scope                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [V3 drive software manual V1.0.1](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf)                             | Read: configuration, live data, calibration/control, firmware, servo/MIT formats, CAN/UART feedback and examples; installed-version gate applies               |
| [AK70-4820-2D-A3 driver manual V1.0.0](https://www.cubemars.com/data/cms/202605/ak70-4820-2d-a3-driver-manual.pdf)                                                   | Read: matched models, electrical limits, mechanical service, numbered connectors, termination, indicators, R-LINK                                              |
| [AKH70-48 STEP/X\_T archive](https://www.cubemars.com/data/cms/202608/akh70-48-v-1-0-robotic-atuator-3d-drawing.zip)                                                 | Exact-model mechanical integration; linked, CAD not opened                                                                                                     |
| [AKH70-48 2D PDF](https://www.cubemars.com/data/cms/202605/akh70-48-v-1-0-robotic-atuator-2d-drawing.pdf)                                                            | Listed by manufacturer; retrieval returned an empty HTML document, so use the visible official drawing above provisionally and obtain the PDF before machining |
| [V3.23 PC host archive](https://www.cubemars.com/data/cms/202606/ak-series-v3-2-3-upper-computer-for-ak-3-0-motor.zip)                                               | Linked on the exact model; software not executed                                                                                                               |
| [Exact product drawing, performance graph and wiring/packing information](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html) | Original attribution and revision context; do not use an AKH70-16 drawing for this 48:1 assembly                                                               |

Firmware selection belongs to the actual board/model and software release. The exact resource inventory does not establish a general ROS SDK or make another actuator's binary compatible. Keep CAD, host software, protocol examples and firmware as separate artifacts in a project record.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The sources above were reviewed on 24 November 2026. This guide is based on document review and an original offline parser. Host/SDK/firmware execution and hardware operation were **not run**. The product/driver encoder disagreement, peak-current disagreement and unreadable direct 2D PDF are explicit limits of this review. Related canonical guides: [AK10-9 V3.0](cubemars-ak10-9-v3.0-actuator-motor-compact-high-torque-power-module.md) and [AK80-64](cubemars-ak80-64-actuator-bldc-motor-compact-high-torque-power.md); their controller pin tables and protocol generations are not interchangeable.
