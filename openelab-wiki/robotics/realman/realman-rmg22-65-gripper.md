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

Source: [RMG22-65 English V1.3 manual, PDF pp. 7–8, 13 \[RMG22\]](realman-source-library.md). Grasp stability depends on finger contact and load; a 5 kg figure does not validate every grasp.

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

Source: [RMG22-65 English V1.3 manual, PDF pp. 10–13 \[RMG22\]](realman-source-library.md). Use the connector drawing's orientation and the actual numbered cores; colors do not establish pin position. Wire with power isolated. Connect the USB–RS485 adapter reference to the gripper power ground as documented. Keep fingers, loose objects and clothing outside the jaw travel.

## Software and development resources

Use the gripper host utility delivered for the unit. V1.3 describes a portable Windows utility with its executable and dependencies in one folder; an independently verified current public binary download was not established. The legacy `RealManRobot/Two-Finger-Gripper` URL returned 404 during review. Do not replace it with a similarly named community repository.

The current [manufacturer RMG22-65 resources](https://github.com/RealManRobot/Dev_Center/tree/main/endeffector/rmg22_65) include a newer Chinese manual dated 2026-11-05 and a drawing dated 2026-06-25. They are separate revisions, not an English V1.3 SDK compatibility guarantee.

## Getting started

1. Confirm the RMG22-65 label, supplied harness orientation, standalone protected supply and clear jaw travel. Do not enable, calibrate or command the jaws.
2. With power off, connect RS485 A/B, signal reference and the approved 24 V supply using the pin table. Connect the USB adapter to the PC and identify its assigned serial port in Windows Device Manager.
3. Apply power according to the delivery procedure. Open the supplied utility, select that port, choose `115200`, 8N1 and device ID `1` for a factory-default unit, then open the connection. Use recorded configured settings for a previously commissioned gripper.
4. Use **Read gripper parameters** and **Read joint status** in the utility. Record ID, baud rate, software version, supply voltage, jaw opening and error code. Do not select enable, zero calibration, reset, firmware upgrade or an opening/closing command.
5. If the selected firmware/protocol differs, stop and identify it before sending raw frames. The proprietary protocol is not Modbus RTU framing.

**Expected result:** readable identity/parameters and status without commanded jaw movement. A fault must be investigated rather than repeatedly cleared. Source: [RMG22-65 English V1.3 manual, PDF pp. 13–16 \[RMG22\]](realman-source-library.md).

## Troubleshooting and FAQs

**No reply:** check supply and indicator, then serial port ownership, A/B/reference wiring, stored ID and baud, then selected protocol. Use a single gripper for initial identification; avoid broadcast operations on a populated bus.

**Unexpected movement or pinching:** isolate the control source and use the delivered stop/power procedure while keeping clear of the jaws. Check whether the utility enabled the actuator or sent a stored target. Do not use calibration as a connection test.

**Protocol examples disagree:** V1.3's Modbus baud table repeats 19200 for one selector, while its proprietary table lists 38400; an ID-change example also contains inconsistent values. Do not copy those configuration frames. Verify the installed protocol's current corrected documentation before changing bus settings. The basic 115200/8N1/ID1 factory configuration is separately stated on PDF p. 13.

## Downloads and technical documents

| Resource                                                                                                         | Use                                                                 |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [English V1.3 manual \[RMG22\]](realman-source-library.md)                                                       | Specifications, connector orientation, utility, protocol and errors |
| [Current official RMG22-65 documents](https://github.com/RealManRobot/Dev_Center/tree/main/endeffector/rmg22_65) | Newer manual and mechanical drawing; match delivery revision        |
| [Arm commissioning](realman-arm-commissioning-and-sdk.md)                                                        | Controller/tool power boundary and arm SDK selection                |

## References and validation

[RMG22-65 English V1.3 manual, PDF pp. 7–16, 19, 28–30 \[RMG22\]](realman-source-library.md). Reviewed 22 November 2026. Software and hardware tests: **not run**. Raw protocol writes and mechanical calibration require corrected, version-matched documentation; the first result is status reading only.

[RealMan index](./)
