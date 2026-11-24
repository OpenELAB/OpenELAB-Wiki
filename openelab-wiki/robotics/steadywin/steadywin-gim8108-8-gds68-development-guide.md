---
description: >-
  Commission the exact GIM8108-8 GDS68 dual-encoder no-brake option with
  versioned power/CAN/USB checks, passive status and an original offline CAN
  decoder.
---

# SteadyWin GIM8108-8 GDS68 Dual-Encoder Engineering Guide

{% hint style="info" %}
[**View SteadyWin GIM8108-8 GDS68 dual-encoder actuator on OpenELAB**](https://openelab.io/products/steadywin-gim8108-8-robot-motor)

**Exact SKU:** `SW-GIM8108-8-S68-2E` · **Selector:** GDS68 / Dual Encoder / None (no brake)
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

This GIM8108-8 option combines an 8:1 planetary actuator, GDS68 drive and secondary encoder without the optional brake. The manufacturer lists 48 V nominal operation, 7.5 N·m rated output and 110 rpm rated output speed for the GDS68 column. Begin commissioning with hardware/firmware identity and passive status; do not treat a GDZ468, GDK468 or brake-equipped option as this SKU. [Manufacturer GIM8108-8 specifications](https://www.steadywin.cn/en/pd.jsp?fromColId=0\&id=133).

The current store's default selection may show `SW-GIM8108-8-S68D-48-B`, which includes a brake. Select **GDS68 → Dual Encoder → None** and check the SKU before ordering. The original product URL remains the family storefront; the exact option is established by its selector and SKU, not the default photograph. [OpenELAB product/options](https://openelab.io/products/steadywin-gim8108-8-robot-motor).

The manufacturer's download page separates hardware V3.7, V3.9 and V3.11 firmware. It also explicitly permits GIM6010-8 documentation as a **GDS68 driver reference**. That permission does not transfer GIM6010 motor constants, pole count, encoder resolution or mechanical dimensions to GIM8108-8. [Official download center](https://www.steadywin.cn/pd.jsp?id=134).

## Applications

Suitable projects include supported robot-joint prototypes and low-inertia rotary test fixtures. Size the actuator for sustained torque at the required output speed, acceleration and bearing load. Evaluate backlash, mounting compliance and thermal path separately from encoder counts. A second output encoder can support retained single-turn feedback but does not eliminate mechanical backlash or establish safe multi-turn travel.

This option has **no brake**. A suspended link can fall after idle, drive fault or power removal. Support the mechanism independently and establish emergency isolation before applying power. A host program that exits does not prove that a previously commanded drive is idle.

## Specifications

| Parameter                           | GIM8108-8 with GDS68                                                                                       |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Nominal supply / product-page range | 48 V / 12–56 V; use the exact delivered board's instructions before using the range extremes               |
| Rated power / output torque         | 336 W / 7.5 N·m                                                                                            |
| Stall torque                        | 22 N·m; not a continuous holding allowance                                                                 |
| Rated / maximum output speed        | 110 / 320 rpm                                                                                              |
| Rated current                       | 7 A                                                                                                        |
| Stall current discrepancy           | Product column 22 A; GIM8108 manual Rev1.4 gives 25 A; do not use either as an unqualified sustained limit |
| Reduction / pole pairs              | 8:1 / 21                                                                                                   |
| Backlash                            | 15 arcmin                                                                                                  |
| Onboard encoder                     | 16-bit in the GDS68 product column; secondary encoder is a separate feedback source                        |
| Envelope with / without driver      | Ø92 × 55 / Ø92 × 44 mm                                                                                     |
| Mass with / without driver          | 396 / 378 g; option hardware can change the assembled mass                                                 |
| Maximum axial / radial load         | 225 / 900 N; confirm combined-load conditions for a design                                                 |
| Protection grade / product ambient  | IP54 / −20 to 80 °C; this is not a higher permissible driver temperature                                   |

[Exact manufacturer's GDS68 column](https://www.steadywin.cn/en/pd.jsp?fromColId=0\&id=133), [GIM8108-8 manual Rev1.4, electrical/mechanical and driver specifications](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf). The manual lists a different board-only minimum/maximum range and a driver ambient limit of 70 °C. Use **48 V nominal** for the documented configuration; neither a board absolute maximum nor a newer family table authorizes raising the motor supply or temperature. Obtain revision-specific current confirmation before a stall/peak acceptance test.

### Exact option and interface comparison

| Option / document                           | What changes                                                                                                   |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **This SKU: GDS68, dual encoder, no brake** | CAN plus Type-C setup; GIM8108-specific motor parameters; no brake holding function                            |
| GDS68, dual encoder, with brake             | Different SKU and mechanical drawing; power-off behavior and brake wiring require that assembly's instructions |
| GDZ468                                      | Manufacturer's separate 24 V, 6.6 N·m, CAN/RS485 column; not this GDS68 performance/SDK assignment             |
| GDZ468H                                     | Separate 48 V column; do not equate the similar name with GDS68                                                |
| GDK468                                      | Store selector exists, but the cited GIM8108 specification page does not establish a GDK468-specific table     |
| GIM6010-8 GDS68 reference                   | Shared driver workflows only; its 14 pole pairs and motor/encoder values must not replace this model's values  |

[Manufacturer product](https://www.steadywin.cn/en/pd.jsp?fromColId=0\&id=133), [manufacturer's explicit shared-driver reference](https://www.steadywin.cn/pd.jsp?id=134). Later GDS documentation discusses additional physical-interface multiplexing on sufficiently new hardware. That does not prove an arbitrary GDS68 unit supports RS485, PWM or pulse/direction, and those modes can reuse the CAN contacts.

## Hardware and connections

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

The **GIM8108-8 Rev1.4 manual p. 9** contains the inspected connector-facing drawing. It names the board connector XT30PB(2+2)-M and mating cable XT30(2+2)-F. In that illustrated view, the two large contacts are VBUS and GND; the small signal contacts are labelled CAN-H above CAN-L. Follow the keyed view and actual markings; do not assign another motor's pin numbering or infer polarity from wire color alone. [Connector drawing and Type-C definition](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf).

| Connection                      | Engineering boundary                                                                                                 |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| VBUS / GND                      | Separate actuator power; the manual states no reverse-polarity protection                                            |
| CAN-H / CAN-L                   | Differential bus with a CAN transceiver; not direct UART or microcontroller GPIO                                     |
| USB Type-C                      | Data cable required; a charge-only cable will not enumerate; USB is not actuator power                               |
| Secondary encoder header        | Versioned UART/I²C connection; supplied option is already integrated, so do not rewire from an unrelated board photo |
| SWD, extension and endstop pads | Service/expansion interfaces; consult the exact revision drawing, logic voltage and supported firmware before use    |
| Brake/resistor pads             | Brake and regeneration resistor are different functions; this no-brake SKU does not imply a fitted braking resistor  |

The manual discusses a 12 V limit-switch supply and SWD 3.3 V connections. Those labels do not establish 12 V-tolerant digital inputs. Do not connect an external supply or sensor to bare pads without the actual board's interface definition. [Rev1.4, §§2.4–2.5](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf).

1. Secure the unloaded motor housing to a rigid fixture. Support attached links and keep the entire potential sweep clear.
2. Disconnect power before mating the combined connector. Verify polarity and absence of shorts. Use appropriate overcurrent, overvoltage and regeneration handling for the supply; avoid live insertion and uncontrolled inrush.
3. Connect one motor initially, a matching Type-C data cable and the supported actuator supply. Do not rely on USB power for operation.
4. For a CAN bus, record the stored bit rate and node ID, and terminate the two physical bus ends. Factory CAN Simple defaults in Rev1.4 are 500 kbit/s and node 0, with IDs 0–63; these are starting references, not proof of a used unit's settings.
5. Check the actual termination configuration before adding another node. Hardware ≤V3.7 has documented USB/CAN switching restrictions; later hardware has a different coexistence path. Do not change protocols merely because USB enumeration is absent.

## Software and development resources

### Development software and recovery <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

| Tool / interface                         | Verified documentary support and compatibility limit                                                                                                                                    |
| ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| MotorWizard                              | Official Windows 2.1 download; GDS68 reference Rev2.2 describes status and Motor Parameters screens                                                                                     |
| odrivetool / Python                      | Documented vendor ODrive-compatible USB object interface; manual does not pin a current PyPI package version, so retain a vendor-supported environment and record the installed version |
| CAN Simple                               | Standard 11-bit identifiers `(node_id << 5) \| command`; little-endian integer/float fields                                                                                             |
| Arduino                                  | Manual describes ODriveArduino, Uno R4 CAN, Teensy/FlexCAN\_T4 and MCP2515 alternatives; each requires a matching CAN transceiver/peripheral and clock/bit-rate configuration           |
| C/C++                                    | GDS reference points to [manufacturer-linked mwmotorsdk](https://gitee.com/cyberbeast/mwmotorsdk); inspect release and endpoint data before integration                                 |
| ROS                                      | Manufacturer's stated example environment is Ubuntu 23.04 / ROS 2 Iron; compatibility with another ROS release is not established by that statement                                     |
| CANopen / Modbus / PWM / pulse-direction | Newer shared GDS reference has separate chapters; actual board, firmware and physical-interface selection must support them first                                                       |

[GIM8108-8 manual Rev1.4](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf), [shared GDS68 reference Rev2.2, SDK and protocol chapters](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgzpi6wQYoh9D9CQ.pdf). These are vendor support statements, not locally executed SDK/ROS tests. The official Arduino example enables closed-loop control and repeatedly commands a sine trajectory; its startup loop is not a passive discovery program.

For Windows USB, identify **CyberBeast Motor Driver Device, Interface 2** before any driver replacement. The references distinguish WinUSB for odrivetool and libusb for MotorWizard. Changing a different interface can break an unrelated device or workflow. Keep a record of the existing driver and use the manual for the selected host application.

### Preserve configuration and unit domains

Read hardware/firmware, node, bit rate, encoder settings, calibration state and limits first. Save a supported configuration backup before editing. In the documented ODrive-compatible interface, save-configuration reboots the controller; reads and a backup belong before that operation. Do not restore a GIM6010 motor configuration to GIM8108 simply because the driver is shared.

USB control quantities use rotor turns/turns per second in the documented interface; CAN MIT uses output-side radian quantities. For a rotor-side observation, output turns = rotor turns ÷ 8. A value already converted to output units must not be divided again. Current limit, DC-bus current, phase/Q-axis current and torque constant require their own definitions; a supply-current readback is not an output-torque measurement. [Rev1.4, configuration and MIT sections](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf).

Calibration, anticogging, closed-loop state entry and zero-setting change the machine or its coordinate system. Factory calibration flags must not be forced true to suppress an error. In torque mode, a configured speed limit may need its separate enable setting; inspect this before active testing rather than assuming position-mode limits apply universally. [GDS reference Rev2.2, setup and control chapters](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgzpi6wQYoh9D9CQ.pdf).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: versioned status without a motion command

1. Confirm `SW-GIM8108-8-S68-2E`, the no-brake assembly and physical hardware revision. Use the hardware section to fixture and power a single unloaded actuator.
2. In MotorWizard, observe connection/status and supply voltage, then open **Motor Parameters / 电机参数** to read hardware and firmware. Do not click Start Motor, calibration or any parameter synchronization/write button. The shared manual describes a calibration prompt after Start Motor on an uncalibrated device; do not accept it during this read-first pass.
3. Record the versions, existing fault state, calibration flags, node ID, bus rate and exact feedback source. Compare measured bus voltage with the intended supply before any operation.
4. If using a supported odrivetool environment instead, run the read-only expressions below. Save their output with the version record. No assignment, state request, reset, error-clear or save operation is included.
5. On an already configured CAN Simple bus, receive existing heartbeat/encoder broadcasts in the adapter's listen facility. Default periods are 100 ms heartbeat and 10 ms encoder estimates in Rev1.4. A different saved configuration can suppress them; lack of a broadcast is not proof that an enable command is needed.

**Power-on and exit boundary:** keep the complete path clear and independently support the output before powering or connecting. The following expressions do not request motion, but they cannot make an existing startup configuration safe. Calibration and Start/closed-loop actions can move the actuator. Normal host exit or Ctrl+C is not verified stationary torque-off; physical isolation and support remain separate.

```
odrv0.hw_version_major
odrv0.hw_version_minor
odrv0.hw_version_variant
odrv0.vbus_voltage
odrv0.axis0.current_state
odrv0.axis0.error
odrv0.axis0.config.can.node_id
odrv0.can.config.baud_rate
odrv0.axis0.encoder.pos_estimate
odrv0.axis0.encoder.vel_estimate
```

**Expected result:** the actual revision, plausible bus voltage, raw state/error, node/rate and stationary feedback are recorded, with no motion command sent. A nonzero error is a diagnostic observation: retain it before considering a clear/reset. If fields are absent, stop and compare the vendor's firmware-specific endpoint map rather than assigning values or updating blindly. [Rev1.4, common read commands and CAN setup](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf).

### Original offline CAN Simple decoder

Save as `gim8108_feedback.py`, requiring Python 3.10 or later. This program opens no adapter and sends nothing. It decodes only the documented `Get_Encoder_Estimates` command (`0x009`), retaining rotor units before the explicitly labelled 8:1 conversion.

```python
import argparse
import json
import math
import struct

p = argparse.ArgumentParser()
p.add_argument("identifier", type=lambda value: int(value, 0))
p.add_argument("payload")
a = p.parse_args()
if not 0 <= a.identifier <= 0x7FF or (a.identifier & 0x1F) != 9:
    p.error("expected standard CAN Simple encoder-estimates identifier")
try:
    data = bytes.fromhex(a.payload)
except ValueError:
    p.error("invalid hexadecimal data")
if len(data) != 8:
    p.error("encoder estimates require eight bytes")
position, velocity = struct.unpack("<ff", data)
if not all(math.isfinite(x) for x in (position, velocity)):
    p.error("non-finite feedback: check protocol and capture")
print(json.dumps({
    "node": a.identifier >> 5,
    "rotor_turns": position,
    "rotor_turns_per_s": velocity,
    "output_degrees_from_rotor": position * 360 / 8,
    "output_rpm_from_rotor": velocity * 60 / 8
}, indent=2))
```

```sh
python3 gim8108_feedback.py 0x69 000000400000003f
```

This **synthetic** example is node 3, rotor position 2 turns and velocity 0.5 turn/s: calculated output 90° and 3.75 rpm. It is not an encoder calibration or a prediction of startup position. Do not feed a CAN MIT reply, GDZ proprietary frame or CANopen PDO to this decoder. [Rev1.4, CAN identifier and encoder-estimate definitions, pp. 34–41](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf).

For a later motion test, resolve the revision-specific current data, preserve zero, specify bounded output travel and a low speed, and verify the supported stop/idle path with an unloaded fixture. The provided offline example deliberately avoids the manual's high-speed or multi-turn demonstrations.

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                        | Useful diagnostic and recovery                                                                                                                      |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB not found                                  | Check actuator supply and a data-capable cable; verify Interface 2's driver and the ≤V3.7 USB/CAN restriction before changing firmware              |
| MotorWizard connected but no plausible voltage | Confirm actual device/interface and separate supply; do not use Start Motor as a communication test                                                 |
| CAN silent                                     | Match stored rate, protocol, physical-interface selection, unique node IDs and termination; check whether periodic messages are enabled             |
| Encoder/pole-pair mismatch                     | Preserve raw error and read GIM8108's actual settings; a GIM6010 reference has different motor constants and cannot be copied wholesale             |
| Overvoltage during deceleration                | Investigate regenerative energy and supply absorption; a bench supply's current limit is not a sink specification                                   |
| Position changes across reboot                 | Distinguish user offset, rotor/output feedback and single-turn retention; record both sides rather than rewriting zero to hide a discrepancy        |
| Heartbeat flags seem inverted or misplaced     | Match firmware generation: Rev1.4 describes differing heartbeat layouts through 0.5.11, from 0.5.12 and from 0.5.13; preserve raw bytes and version |

**Does the second encoder remove backlash?** No. Mechanical backlash and feedback resolution are different; compare approach direction when measuring repeatability.

**Can I flash a newer GIM8108 binary onto any board?** No. The manufacturer explicitly warns that V3.7 cannot use V3.9 firmware. V3.11 has its own files. First back up parameters, confirm model/hardware, detach or support the mechanism, and follow the matching DFU/SWD procedure. A reset/upgrade may discard configuration or require active recalibration. Do not perform an erase or calibration as a first recovery step. [Official hardware-specific firmware list](https://www.steadywin.cn/pd.jsp?id=134).

**Is a Python/Arduino/ROS example read-only?** Inspect startup and callbacks. The official examples include closed-loop entry and motion. Build success alone would not establish a safe lifecycle or correct gearbox units.

## Downloads and technical documents

| Resource                        | Direct manufacturer link and scope                                                                                                                                                                                                                                                                              |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GIM8108-8 V3.9 reference manual | [Rev1.4 PDF](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg6qyVtgYoiJyM2gU.pdf), read: specifications, interface drawings, setup, calibration, control, firmware, CAN, Python/Arduino/ROS and errors                                                                                                  |
| Earlier GIM8108 hardware        | [Rev1.3 / V3.7 PDF](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgjtyStAYojNL5ggc.pdf); version comparison, not an upgrade target                                                                                                                                                                     |
| Shared GDS68 driver             | [GIM6010 Rev2.2 PDF](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgzpi6wQYoh9D9CQ.pdf), read relevant driver/setup/CAN/SDK sections; [Rev2.0 reference](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg4YT9uwYow_28jgU.pdf), listed historical resource                                      |
| V3.11 firmware                  | [0.6.0, 2025-09-02](https://download.s21i.co99.net/14180476/0/0/ABUIABBjGAAgy8XlxQYo8KOYzgU.bin), [0.5.16, 2025-05-20](https://download.s21i.co99.net/14180476/0/0/ABUIABBjGAAgpMXlxQYo-vquYg.bin); binaries linked, not executed/flashed                                                                       |
| V3.9 / V3.7 firmware            | [V3.9 0.5.13](https://download.s21i.co99.net/14180476/0/0/ABUIABBjGAAg0Ib8uAYo_tny2wU.bin), [V3.7 0.5.13](https://download.s21i.co99.net/14180476/0/0/ABUIABBjGAAgx4f8uAYogKD8kgY.bin), dated 2024-10-15                                                                                                        |
| MotorWizard Windows             | [Official 2.1 installer](https://download.s21i.co99.net/14180476/0/0/ABUIABBLGAAgzZa3uAYo34TkywQ.exe); [manufacturer shop's GDS68 package](https://islandcloud.co/link/69ae2df18caa112212f9d9a0/358d64c2-0df0-471f-9229-452cb1500db3) additionally inventories a 2.1.1.241017 archive; software not executed    |
| Standard no-brake mechanics     | [2D installation PDF](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAg-fH5xQYo8Kn63AI.pdf), [STEP](https://download.s21i.co99.net/14180476/0/0/ABUIABBrGAAg7PH5xQYoiLDc8AQ.step); verify exact option before fixture fabrication                                                                        |
| Other mechanical options        | [Core 2D](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgk-L5xQYoiP3y0gQ.pdf), [shaft 2D](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgoPqixwYo6oSLxgc.pdf), [brake 2D](https://download.s21i.co99.net/14180476/0/0/ABUIABA9GAAgsPqixwYo2M25OA.pdf); distinct assemblies, not substitutions |
| Additional CAD / selection      | [Official product drawing tabs](https://www.steadywin.cn/en/pd.jsp?fromColId=0\&id=133), [manufacturer shop with GDS selection/downloads](https://steadywin-motor.com/products/planetary-reduction-motor-robot-dog-humanoid-robot-joint-module-flat-thin-large-torque)                                          |

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The [manufacturer specifications](https://www.steadywin.cn/en/pd.jsp?fromColId=0\&id=133), [hardware-specific download center](https://www.steadywin.cn/pd.jsp?id=134), model manual and relevant shared-driver sections were reviewed on 24 November 2026. Official diagrams are linked in their original manuals; no new electrical drawing is inferred. The GIM6010 RS485/PWM chapters and GDZ driver package do not establish those interfaces for this assigned GDS68 option. The selection spreadsheet and CAD archives are listed resources rather than claims of executed or comprehensive engineering verification.

Software/SDK/firmware and hardware operation were **not run**. Offline arithmetic or syntax checks, if separately recorded, do not validate device operation. Peak-current differences between the product and older manual remain a revision-specific acceptance boundary. For another integrated-motor family, use its own canonical procedure, such as [LK MG dual-encoder V3](../lkmtech/lkmtech-mg-dual-encoder-v3-development-guide.md), without transferring its pinout or CAN format.
