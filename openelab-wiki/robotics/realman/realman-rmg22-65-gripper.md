# RealMan RMG22-65: parallel gripper commissioning

{% hint style="info" %}
[**View RMG22-65 on OpenELAB**](https://openelab.io/products/realman-rmg22-65-two-finger-parallel-gripper)

**Model:** RMG22-65 · **SKU:** `RealMan-RMG22-65`
{% endhint %}

## Product overview

RMG22-65 is a two-finger parallel gripper using an RS485 link, with proprietary serial and Modbus RTU protocols. This guide follows the supplied English V1.3 manual, August 2026. Do not substitute the older RMG24 product page or the L2's 90 mm gripper specification.

## Applications

Bench grasping, sorting and manipulation integration after checking workpiece retention, finger geometry and payload. The encompassing-grip and friction-grip limits describe different retention conditions.

## Specifications

| Parameter                     | Value and scope                                                        |
| ----------------------------- | ---------------------------------------------------------------------- |
| Stroke / opening-closing time | 65 mm / 2 s                                                            |
| Dimensions / mass             | 167 × 112 × 60 mm / 745 g                                              |
| Payload                       | Maximum encompassing grip 5 kg; recommended maximum friction grip 2 kg |
| Force / repeatability         | 130 N maximum / ±0.05 mm                                               |
| Supply                        | 24 V DC                                                                |
| Rated / maximum current       | 1.9 A / 5.7 A                                                          |
| Rated / maximum power         | 45.6 W / 136.8 W                                                       |
| Factory serial settings       | ID 1; 115200 baud; 8 data bits, no parity, 1 stop bit                  |

Source: [RMG22-65 English V1.3 manual, PDF pp. 7–8, 13 \[RMG22\]](realman-source-library/). Grasp stability depends on finger contact and load; a 5 kg figure does not validate every grasp.

## Hardware and connections

{% hint style="warning" %}
**Power budget:** the gripper manual specifies 1.9 A rated and 5.7 A maximum current, while the supplied arm manuals specify a 1.5 A maximum tool output. Do not power this gripper from that arm tool port without a manufacturer-approved power arrangement. Use the delivered, separately protected 24 V supply architecture and common RS485 reference; avoid backfeeding an arm output.
{% endhint %}

| Pin | Wire in supplied gripper harness | Function            |
| --- | -------------------------------- | ------------------- |
| 1   | Yellow                           | RS485 A+            |
| 2   | White                            | RS485 B−            |
| 3   | Red                              | Multiplexed DI1/DO1 |
| 4   | Black                            | Multiplexed DI2/DO2 |
| 5   | Green                            | Power ground        |
| 6   | Blue                             | +24 V input         |

Source: [RMG22-65 English V1.3 manual, PDF pp. 10–13 \[RMG22\]](realman-source-library/). Use the connector drawing's orientation and the actual numbered cores; colors do not establish pin position. Wire with power isolated. Connect the USB–RS485 adapter reference to the gripper power ground as documented. Keep fingers, loose objects and clothing outside the jaw travel.

## Software and development resources

Use the gripper host utility delivered for the unit. V1.3 describes a portable Windows utility with its executable and dependencies in one folder; an independently verified current public binary download was not established. The legacy `RealManRobot/Two-Finger-Gripper` URL returned 404 during review. Do not replace it with a similarly named community repository.

The current [manufacturer RMG22-65 resources](https://github.com/RealManRobot/Dev_Center/tree/main/endeffector/rmg22_65) include a newer Chinese manual dated 2026-11-05 and a drawing dated 2026-06-25. They are separate revisions, not an English V1.3 SDK compatibility guarantee.

## Complete supplied document and engineering details

[RMG22-65 parallel gripper manual V1.3 — all 53 PDF pages](realman-source-library/complete-rmg22-65-manual.md). The full reference is readable inside the wiki, with an original-page view and searchable text for every page. It includes the material not repeated in this entry guide.

| Source section                                                           | Full in-wiki reference                                                      |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------------- |
| Safety, revisions and contents                                           | [PDF 1–6](realman-source-library/complete-rmg22-65-manual.md#pdf-page-1)    |
| Product specifications and packing list                                  | [PDF 7–9](realman-source-library/complete-rmg22-65-manual.md#pdf-page-7)    |
| Mechanical/electrical installation and serial configuration              | [PDF 10–13](realman-source-library/complete-rmg22-65-manual.md#pdf-page-10) |
| Host software controls, status, calibration and firmware                 | [PDF 13–17](realman-source-library/complete-rmg22-65-manual.md#pdf-page-13) |
| Modbus coil and holding registers                                        | [PDF 18–20](realman-source-library/complete-rmg22-65-manual.md#pdf-page-18) |
| RS485 framing, checksum and command catalogue                            | [PDF 21–24](realman-source-library/complete-rmg22-65-manual.md#pdf-page-21) |
| Every proprietary command, request and response example, I/O and support | [PDF 25–53](realman-source-library/complete-rmg22-65-manual.md#pdf-page-25) |

### Full electrical and commissioning requirements

The source packing list includes the gripper, 6-pin connector/short harness and six M4×6 screws; its power adapter is optional. Check the actual delivered mounting hardware and adapter. The V1.3 specification gives 24 V input, 1.9 A rated / 5.7 A maximum current, and 45.6 W rated / 136.8 W maximum power. This is a different electrical budget from the arm tool output. The supplied arm manual gives 1.5 A maximum tool-output current, so even the gripper's rated-current figure exceeds that maximum. Use an approved separate-power integration instead of assuming that a matching connector guarantees power compatibility.

| Gripper pin | Wire color in this manual | Function                        |
| ----------- | ------------------------- | ------------------------------- |
| 1           | Yellow                    | RS485\_A / A+                   |
| 2           | White                     | RS485\_B / B−                   |
| 3           | Red                       | DI1 / DO1 multiplexed interface |
| 4           | Black                     | DI2 / DO2 multiplexed interface |
| 5           | Green                     | Power GND                       |
| 6           | Blue                      | **24 V power input**            |

The same position on an arm's tool connector can be a programmable power **output**. Confirm both sides of the harness. With power isolated, verify polarity and the connector view before connecting. The manual's PC example uses a USB-to-RS485 adapter with an appropriate common reference to the gripper supply. Factory serial configuration is **ID 1, 115200 baud, 8 data bits, 1 stop bit, no parity**. Query identification/parameters/status before selecting an open/close, force, position, calibration, reset or upgrade function.

### Complete Modbus register coverage

The four coil addresses `0x0001`–`0x0004` cover DIO1 mode/state and DIO2 mode/state. The following holding registers are preserved in the supplied table; read/write and restart behavior must be taken from that firmware-specific table.

| Holding register    | Source function              | Access / integration note                                      |
| ------------------- | ---------------------------- | -------------------------------------------------------------- |
| `0x0001`            | Save parameters              | Writes persistent configuration                                |
| `0x0002`            | Restore defaults             | Destructive configuration change                               |
| `0x0003`            | Device address, 1–254        | Saving/restart conditions apply                                |
| `0x0004`            | Baud-rate code               | The source repeats 19200 for two codes; confirm before writing |
| `0x0005`            | Single / continuous clamping | Can actuate the gripper                                        |
| `0x0006`            | Release                      | Can actuate the gripper                                        |
| `0x0007`            | Stop                         | Does not replace the system's physical emergency stop          |
| `0x0008`            | Clear error                  | Investigate the fault and follow restart requirements first    |
| `0x0009`            | Target opening, 0–1000       | Motion command; not millimetres                                |
| `0x000A`            | Speed, 0–1000                | Dimensionless source scale                                     |
| `0x000B`            | Force setting, 0–1000        | Dimensionless source scale; not newtons                        |
| `0x000C` / `0x000D` | Maximum / minimum opening    | Changes motion bounds                                          |
| `0x000E`            | Actual strength              | Read-only, dimensionless                                       |
| `0x000F`            | Actual position              | Read-only, dimensionless                                       |
| `0x0010`            | Actual current               | Read-only; source unit mA                                      |
| `0x0011`            | Actual voltage               | Read-only; source unit V                                       |
| `0x0012`            | Actual temperature           | Read-only; source unit °C                                      |
| `0x0013`            | Error code                   | Read-only; retain raw value and firmware context               |
| `0x0014`            | Gripper status code          | Read-only; decode with the supplied status table               |

### Proprietary RS485 protocol and source ambiguities

The proprietary command frame is `EB 90 | ID | Len | CMD | Data | Sum`. Its length includes the command byte plus data; total frame length is `Len + 5`. IDs 1–254 identify devices; broadcast `0xFF` does not produce replies. The proprietary checksum is the low byte of the sum after the two header bytes; it is **not** a Modbus RTU CRC. The original command/reply tables and every payload example are preserved in the full manual.

Read/query commands include identification `0x05`, opening limits `0x13`, force setting `0x1A`, DIO state `0x1D`, running state `0x41`, system parameters `0x42`, motor state `0x43` and actual opening `0x55`. Use the exact response structure from the corresponding manual page; a valid serial frame is not proof that a commanded grip succeeded. Do not turn the source's normalized force or speed settings into engineering units without the correct calibration/firmware contract.

The V1.3 document contains a **2 s specification versus 0.4 s scale example**, a torque-scale reference to **4 kg** alongside **5 kg encompassing / recommended 2 kg friction-grip payloads**, duplicate baud-code wording and duplicate `0xDA` command labels. These are distinct, unresolved source statements. Keep motion, ambiguous configuration writes and zero-setting blocked until the exact firmware behavior is confirmed. The source's zeroing, transparent-teleoperation, persistent-save, factory-reset and firmware-upgrade procedures are retained as references, with their power-cycle and calibration requirements.

Sources: [specifications](realman-source-library/complete-rmg22-65-manual.md#pdf-page-8), [wiring](realman-source-library/complete-rmg22-65-manual.md#pdf-page-10), [Modbus tables](realman-source-library/complete-rmg22-65-manual.md#pdf-page-18), [proprietary protocol](realman-source-library/complete-rmg22-65-manual.md#pdf-page-21).

## Getting started

1. Confirm the RMG22-65 label, supplied harness orientation, standalone protected supply and clear jaw travel. Do not enable, calibrate or command the jaws.
2. With power off, connect RS485 A/B, signal reference and the approved 24 V supply using the pin table. Connect the USB adapter to the PC and identify its assigned serial port in Windows Device Manager.
3. Apply power according to the delivery procedure. Open the supplied utility, select that port, choose `115200`, 8N1 and device ID `1` for a factory-default unit, then open the connection. Use recorded configured settings for a previously commissioned gripper.
4. Use **Read gripper parameters** and **Read joint status** in the utility. Record ID, baud rate, software version, supply voltage, jaw opening and error code. Do not select enable, zero calibration, reset, firmware upgrade or an opening/closing command.
5. If the selected firmware/protocol differs, stop and identify it before sending raw frames. The proprietary protocol is not Modbus RTU framing.

**Expected result:** readable identity/parameters and status without commanded jaw movement. A fault must be investigated rather than repeatedly cleared. Source: [RMG22-65 English V1.3 manual, PDF pp. 13–16 \[RMG22\]](realman-source-library/).

## Troubleshooting and FAQs

**No reply:** check supply and indicator, then serial port ownership, A/B/reference wiring, stored ID and baud, then selected protocol. Use a single gripper for initial identification; avoid broadcast operations on a populated bus.

**Unexpected movement or pinching:** isolate the control source and use the delivered stop/power procedure while keeping clear of the jaws. Check whether the utility enabled the actuator or sent a stored target. Do not use calibration as a connection test.

**Protocol examples disagree:** V1.3's Modbus baud table repeats 19200 for one selector, while its proprietary table lists 38400; an ID-change example also contains inconsistent values. Do not copy those configuration frames. Verify the installed protocol's current corrected documentation before changing bus settings. The basic 115200/8N1/ID1 factory configuration is separately stated on PDF p. 13.

## Downloads and technical documents

| Resource                                                                                                         | Use                                                                 |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [English V1.3 manual \[RMG22\]](realman-source-library/)                                                         | Specifications, connector orientation, utility, protocol and errors |
| [Current official RMG22-65 documents](https://github.com/RealManRobot/Dev_Center/tree/main/endeffector/rmg22_65) | Newer manual and mechanical drawing; match delivery revision        |
| [Arm commissioning](realman-arm-commissioning-and-sdk.md)                                                        | Controller/tool power boundary and arm SDK selection                |

## References and validation

[RMG22-65 English V1.3 manual, PDF pp. 7–16, 19, 28–30 \[RMG22\]](realman-source-library/). Reviewed 22 November 2026. Software and hardware tests: **not run**. Raw protocol writes and mechanical calibration require corrected, version-matched documentation; the first result is status reading only.

[RealMan index](./)
