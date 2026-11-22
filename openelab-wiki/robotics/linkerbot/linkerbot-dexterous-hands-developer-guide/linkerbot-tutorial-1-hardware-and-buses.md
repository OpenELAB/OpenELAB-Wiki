---
description: >-
  Device identity, flange and bus setup with no motor commands; source-backed
  CAN versus CAN FD settings.
---

# Tutorial 1 — LINKERBOT Power, Connectors and CAN/CAN-FD Setup

{% hint style="info" %}
[**L6 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l6-11) · [**L20 Lite on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-lite) · [**L20 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-21) · [**L30 Tendon on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l30-l30) · [**O6 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-o6-11)

**Models:** seven source manuals; O20 and O30 store matches remain pending.
{% endhint %}

[**Complete seven-manual library — all 137 original PDF pages and downloads**](../source-library/)

[Back to LINKERBOT developer series](./)

## Product overview

This tutorial explains the **model-specific electrical and communication preflight** that must be completed before any joint motion. CAN, CAN FD, RS485 and optional EtherCAT versions cannot be swapped merely because they use the LINKERBOT family name.

## Applications

* Confirm the actual hand, side, interface variant, original power adapter and physical flange.
* Distinguish classic CAN and CAN FD adapter modes before running a host driver.
* Record a no-motion adapter diagnostic result.

## Specifications

| Models                 | Native CAN / CAN FD setup in current OEM ROS 2 guide             |
| ---------------------- | ---------------------------------------------------------------- |
| L6, O6, L20 Lite, L20  | Classic CAN, **1 Mbit/s** (only a **purchased CAN variant**)     |
| O20, L30 Standard, O30 | CAN FD, **1 Mbit/s arbitration / 5 Mbit/s data** reference       |
| O30                    | CAN FD **BRS off** per vendor                                    |
| RS485 options          | Separate vendor transport/cabling required, not native SocketCAN |

**Critical:** the L30 Standard manual specifies 24 V and CAN FD, while the matched store information offers 12 V and CAN/RS485. Keep the affected hand **unpowered** until the exact JQ variant is confirmed.

## Hardware and connections

1. Identify model, left/right, SKU, hardware revision, cable and adapter. Read the **original model-specific connector drawing**.
2. Confirm the supply on the actual unit, then use only the approved adapter. **O20** uses connector `O20_V1.0_PAB20251123`; **O30** uses `R20_V3.0_PAB20260529`; these are not the XT30 (2+2) of several L models.
3. Mount the hand to the correct flange with the specified screw depth. Keep fingers and cables clear.
4. Avoid energizing unidentified hardware or choosing a different bus mode to “try” a command.

## Software and development resources

* [Official bus connection guidance](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/connection.md).
* [Model matrix and native bus capabilities](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).
* [LINKERBOT model manuals](../).

## Getting started

### First working result: Linux adapter inspection without finger movement

1. With the hand **unpowered**, inspect the actual adapter interface (replace `can0` as appropriate):

```bash
ip -details link show can0
```

2. Only for a **confirmed classic CAN model** and approved adapter, the current OEM guide shows:

```bash
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000
sudo ip link set can0 up
ip -details -statistics link show can0
```

3. For a **confirmed CAN-FD hand** and approved FD adapter, use the separate setup:

```bash
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000 dbitrate 5000000 fd on
sudo ip link set can0 up
ip -details -statistics link show can0
```

**Expected result:** the interface exists and reports the correct mode/rate. These steps only configure the host adapter, not motors, power, wiring, or device safety.

## Troubleshooting and FAQs

**Adapter missing?** Inspect vendor driver and firmware; a serial device does not automatically provide SocketCAN FD.

**No frames?** Verify the ordered variant's real protocol, physical cable/termination and confirmed supply without issuing motion commands.

**Can CAN-only adapters operate O20?** The supplied O20 manual requires USB-to-CAN-FD; do not assume compatibility.

## Downloads and technical documents

* [OEM socketCAN/native adapter setup](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/connection.md).
* [Exact-model manuals and mounting drawings](../).

## References and validation

* Seven OEM manuals uploaded by OpenELAB, examined 2026-11-21.
* [Current LINKERBOT ROS 2 connection guide](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/connection.md), reviewed 2026-11-21.

**Documentation:** source-reviewed. **Software execution:** not run. **Hardware validation:** not run. L30 voltage/bus and O20/O30 store-match gaps remain.

## Complete source coverage and revision checkpoints

| Model / revision                               | Complete supplied reference                            | Key interpretation                                          |
| ---------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------- |
| L6 V1.4 · 2026-05-18                           | [15 PDF pages](../source-library/complete-l6.md)       | LED and speed-unit note                                     |
| L20 Lite V1.0 · 2025-09-11                     | [19 PDF pages](../source-library/complete-l20-lite.md) | 10 active / 20 physical joints; optional sensor variants    |
| L20 V1.3 · 2026-08-04                          | [14 PDF pages](../source-library/complete-l20.md)      | 24–48 V table / 24 V connector; V1.3 joint angles           |
| L30 Standard (tendon-driven) V1.3 · 2025-10-27 | [17 PDF pages](../source-library/complete-l30.md)      | Tendon/wrist model; voltage, bus and rate conflicts         |
| O6 V1.4 · 2026-07-21                           | [17 PDF pages](../source-library/complete-o6.md)       | Optional 4×10 tactile; actual protocol option               |
| O20 V1.2 · 2026-06-05                          | [30 PDF pages](../source-library/complete-o20.md)      | 30 Hz tactile / 1000 Hz communication; unique connector     |
| O30 V1.0 · 2026-07-10                          | [25 PDF pages](../source-library/complete-o30.md)      | 6×11 pressure array; unique connector and descriptor layout |

### Pin orientation, mounting and rate decisions

Read the exact source drawing before making a harness: L6 PDF page 13; L20 Lite page 13; L20 page 12; L30 page 13; O6 page 14; O20 pages 13–14; O30 page 12. M3 mounting is specified for L20 Lite/L20/O6/O20/O30; L30 specifies M4 and provides end-flange plus mounting-seat drawings. L6 uses its own flange drawing on page 12. Choose screw length from fixture thickness and the drawing; do not invent a universal screw depth or torque.

The SDK adapter profile is a software reference for a confirmed compatible device. In particular, L30’s manual 500 kbps/overview 500 Hz and the SDK’s 1 Mbit/s arbitration/5 Mbit/s data do not establish one interchangeable setting. Keep L30 hardware unpowered until the exact supply, cable, PCB/firmware and transport are confirmed. O6 manual support for EtherCAT does not make the CAN tutorial applicable to an EtherCAT unit.

A no-motion first result records the adapter mode/rate and error counters before and after an identity query. If errors rise, end the session and inspect wiring, termination, bus variant and the approved supply; do not repeatedly send resets, calibration or movement to discover a device.

Current software reference: [ROS 2 source at `8d56b3355d2c`](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/8d56b3355d2cfcd90e4e3c6b377ebceb7a5c09ac/README.md), reviewed 22 November 2026. This is a documentation review; **software execution and hardware validation were not run**.
