---
description: >-
  Wire ROBSTRIDE02-IP67, distinguish rated/peak limits, read private-CAN
  voltage/position/speed, and retain its dated manual and control references.
---

# RobStride 02-IP67 Instruction Manual

{% hint style="info" %}
[**View ROBSTRIDE02-IP67 joint motor on OpenELAB**](https://openelab.io/products/robstride02-ip67-robot-joint-actuator)

**Model:** ROBSTRIDE02-IP67 · **SKU:** `ROBSTRIDE-02IP67` · **Option:** motor without Debug Board · **Document:** RS02-IP67User Manual260713.pdf; classical CAN2.0 reference, not a CAN-FD image.
{% endhint %}

## Product overview

ROBSTRIDE02-IP67 integrates a brushless motor, reduction gear, encoder feedback and CAN drive. This guide takes one secured, unloaded actuator from verified wiring to **bus voltage, position and velocity readback without enabling torque**. Its 17 N·m headline is a peak output value; it is not continuous holding torque, power-supply current or a default controller limit. [Exact manufacturer manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf), [RobStride source library](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778).

The purchased motor option excludes the USB-CAN debugger. Use the [debug/power-board integration guide](robstride-debug-power-boards-development-guide.md) when selecting that accessory. A debug-board SKU sold on the same listing is a different item.

## Applications

Use ROBSTRIDE02-IP67 for an individually engineered robot joint, torque-controlled research mechanism or position/velocity test fixture. Determine the actual load envelope from torque–speed and overload curves, cooling, duty cycle, bearing loads and mechanism geometry before mounting a link. A high-ratio position loop and a five-parameter impedance loop have different response and fault behavior.

Start with one motor and a recorded identity. Later, assign unique CAN IDs and retain a physical-joint map, encoder sign, zero reference and firmware revision for each unit. Dual encoders do not establish permanent multi-turn retention, zero backlash or safe unpowered holding. The manual’s anti-backdrive feature concerns generated-voltage protection; it is not a rated holding brake. [Functions and operating modes, chapters 4–6](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

## Specifications

| Parameter                    | ROBSTRIDE02-IP67 dated-manual scope                                                         |
| ---------------------------- | ------------------------------------------------------------------------------------------- |
| Rated supply / working range | 48 V DC / 24–60 V                                                                           |
| Rated output                 | 6 N·m at 100 rpm with 260 × 280 mm heat sink in the model manual                            |
| Peak output torque           | 17 N·m; time/thermal limited                                                                |
| No-load speed                | 410 rpm ± 10%                                                                               |
| Reduction / mass             | 7.75:1 / 490 g in the manufacturer selection overview; the English manual repeats 380 ± 3 g |
| Phase-current values         | 7 A peak-phase rated /23 A peak-phase maximum; not DC input current                         |
| Torque-constant reference    | 1.22 N·m/A RMS; preserve RMS versus peak convention                                         |
| Feedback                     | 14-bit absolute-turn driver reference; dual-encoder option                                  |
| Bus                          | Classical CAN, 1 Mbit/s in the default private-protocol reference                           |
| Environment                  | −20 to 50 °C; 5–85% RH, non-condensing                                                      |

Use the sealed model’s actual dimension drawing and mass for load/inertia design: the English mechanical table appears to repeat the unsealed 380 g value while the manufacturer overview identifies 490 g. That disagreement does not change the 48 V, 24–60 V read-only commissioning path. IP67 does not make an open/unmated connector waterproof or authorize hot-plugging. [Motor/service/driver tables, chapters 1–2](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf). Regenerative deceleration or externally turning a motor can raise the DC bus. Choose supply absorption/discharge provisions from the complete system design; do not assume a bench supply can absorb returned energy.

## Hardware and connections

### Fixture, power and connector orientation

![ROBSTRIDE02-IP67 manufacturer mounting drawing](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/03bcfb89-38cb-45da-b265-991b99f3492d/image/w=1920,quality=90,fit=scale-down)

_RobStride Dynamics, retained original model-specific drawing. Compare it with the dated PDF and STEP before choosing screw engagement._

Use the exact STEP and thread-depth drawing. Keep fixing screws within the specified housing thread depth, maintain shaft/link clearance and support any gravity load before torque is removed. Power off before changing power or communication connectors.

The sealed model uses its own **male front-view six-contact connector drawing**, not the unsealed XT30 face or cable colors. In that exact keyed view, the small upper-left signal is CAN-H (red), the upper-center small signal is CAN-L (black); the lower large contacts are GND (thick black, left) and 48 V+ (thick red, right). Two positions are marked unused in the drawing. Do not number or populate those unused positions by inference. Cable-side views are mirrored. Inspect the key, actual harness and continuity with power removed; preserve the mating seal and use the exact IP67 assembly drawing. [Chapter 2 connector diagrams](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

Use a twisted CAN pair and appropriate common-reference/isolation design. Put termination only at the physical bus ends; two 120 Ω ends normally measure approximately 60 Ω across an unpowered, fully connected pair. This is a wiring diagnostic, not a reason to add a resistor at every node. Verify adapter termination and board revision with power removed.

### Adapter mode is a separate choice

The documented RobStride debugger is a CH340- family **serial AT** adapter: serial packets start `41 54` and end `0D 0A`. On the documented board, DIP1 ON selects boot mode and prevents normal communication; DIP2 ON inserts 120 Ω. A serial port such as `/dev/ttyUSB0` is not a SocketCAN `can0` interface. The Linux example below requires a genuine SocketCAN-capable adapter, not a guessed serial framing bridge. [Host tool chapter 3](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

## Software and development resources

| Path                         | Exact interface and purpose                                                                               |
| ---------------------------- | --------------------------------------------------------------------------------------------------------- |
| Manufacturer host tool       | Matching USB-CAN serial adapter/CH340 driver; detect device, refresh/read parameters, export a baseline   |
| Linux original example below | Python 3 standard-library SocketCAN; classical private protocol, 29-bit extended IDs, 8-byte data         |
| CANopen                      | Separate protocol selection, EDS, CiA402 state machine and object units; do not send private frames to it |
| MIT protocol                 | Separate standard-ID command packing, ranges and enable/disable behavior; not identical to private Type 1 |
| Firmware / OTA               | Exact `rs-0x` model image and matching updater; preserve configuration before updates                     |

[Dated protocol and host-tool manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf), [official files at commit `9dcbce6df00b`](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778), [Linux SocketCAN interface](https://docs.kernel.org/networking/can.html). The repository contains the driver installer, OTA source and CANopen EDS; file presence does not prove compatibility with another hardware revision. No vendor SDK installation or updater execution is claimed here.

### Protocol scales and revision traps

The following values are checked against **RS02-IP67 User Manual 260713.pdf**, rather than inherited from an older page. These are wire-format ranges, not permitted operating demands. A revision-matched decoder may use them only after identifying the fitted firmware. The first-result script bypasses packed-command scaling and reads floats.

| Private Type 1/Type 2 item | Dated ROBSTRIDE02-IP67 reference                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Type 1 torque              | ID bits 23–8 contain a 16-bit unsigned value covering −17 to +17 N·m; this field spans two bytes, despite the source’s misleading “Byte 2” label |
| Type 1 payload             | bytes 0–1 angle; 2–3 velocity; 4–5 Kp; 6–7 Kd; each is unsigned 16-bit, high byte first                                                          |
| Angle range                | −4π to +4π rad; sample macros approximate the endpoints as −12.57/+12.57; firmware history changes the earlier ± 12.5 convention                 |
| Velocity range             | −44 to +44 rad/s                                                                                                                                 |
| Type 1 gain ranges         | Kp 0–500; Kd 0–5; do not substitute another motor’s gains                                                                                        |
| Type 2 payload             | bytes 0–1 angle, 2–3 velocity, 4–5 torque use the same 16-bit big-endian ranges; bytes 6–7 are temperature in tenths of °C                       |
| Type 2 routing             | source motor in ID bits 15–8; destination host bits 7–0; bits 22–23 report mode, bits 16–21 report faults                                        |

For a 16-bit range `[a,b]`, the wire endpoint codes are 0 and 65535, so the original decoding equation is `a + code*(b-a)/65535`. That does **not** make an all-zero motion payload a zero-demand command: for a signed symmetric range it represents the negative endpoint. The function-description page contains a duplicated bit 20 label and a sign error in one `P_MIN` note; the control table and signed sample macros establish the intended angle endpoints. Keep undecoded fault bits/raw frames rather than guessing from the duplicated label. [Type 1/2 table, PDF p.42; sample macros, chapter 4.4](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=42).

### CANopen object scaling

| CANopen object                                   | Exact-model units in this manual                                                                  |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| `0x6062`, `0x6064`, `0x607A`, `0x6067`           | position/demand/window: 16384 pulses per revolution                                               |
| `0x606B`, `0x606C`, `0x6081`, `0x60FF`           | velocity: 0.1 rpm; do not reuse private-CAN rad/s                                                 |
| `0x6083`                                         | acceleration: 0.1 rpm/s                                                                           |
| `0x6071`, `0x6077`                               | signed 16-bit torque/load-ratio scale: **1000 = 6 N·m**, not peak torque                          |
| `0x6078`, `0x6079`                               | current: mA; DC-link voltage: mV                                                                  |
| `0x6040`, `0x6041`, `0x6060`, `0x6061`, `0x603F` | controlword/statusword, requested/displayed mode, error code; retain the exact dictionary’s types |

For this manual’s torque scale, `N·m = raw*6/1000`; negative signed values mean negative torque. The scale’s reference value can differ from the mechanical continuous rating: notably the 2 N·m CANopen base in EL05/RS05 documentation is not a revision of their 1.8/1.6 N·m thermal ratings. These objects belong to CANopen, not Type 17 parameter indices. Set mode while disabled and read the resulting state before any later enable. The manufacturer’s mode numbering uses PP 1, CSP 5, velocity 3, torque 4, homing 6; do not transplant a generic CSP 8 example. [CANopen status/control tables, PDF p.69 onward](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=69).

### MIT feedback layout

MIT feedback uses standard identifiers and a different packed layout: byte 0 is motor ID; angle is bytes 1–2; velocity is `(byte3<<4)|(byte4>>4)`; torque is `((byte4&15)<<8)|byte5`. Its manual tables print a 12-bit range “0–4096”, although a 12-bit field can carry only 0–4095. **Do not use 4096 as an emitted endpoint or choose the quantization denominator by copying that label.** Confirm the exact firmware/SDK before writing a MIT decoder or motion encoder; no runnable MIT command is supplied here. The mechanical angle and velocity/torque endpoints are ± 12.57 rad, ± 44 rad/s and ± 17 N·m in that chapter. In this PDF byte 6 high bits carry mode/fault/warning and its low nibble plus byte 7 carry temperature × 10; decoding the whole word as temperature includes status bits. [Exact MIT response table, PDF p.73](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=73).

| Thermal quantity                                    | Dated reference and boundary                                                                                      |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Driver-board maximum                                | 145 °C in the driver specification; not a commanded application temperature                                       |
| Private Type 21 motor-overtemperature fault default | 135 °C in the fault-frame table                                                                                   |
| Type 21 warning default                             | 135 °C in the warning-word table                                                                                  |
| Type 21 payload                                     | fault word bytes 0–3; warning word bytes 4–7; preserve raw bytes unless byte order is confirmed for that firmware |

The winding test criterion, driver-board maximum and protection message defaults are different quantities. A board maximum must not replace the winding protection threshold. In particular, the temperature at which firmware reports a fault is not a recommended continuous winding temperature or a safety certification. Keep the mechanism unloaded while investigating thermal/fault inconsistencies. [Driver table, PDF p.12](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=12), [Type 21, PDF p.46](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=46).

### Type 17 source, destination and rejection checks

The dated manual’s **worked `loc_kp` read** resolves the garbled general reply table: its request is ID `0x1100FD7F` with `1E 70 00 00 00 00 00 00`; its successful reply is ID `0x11007FFD` with `1E 70 00 00 00 00 F0 41`. Thus request bits 15–8 carry host `FD` and low byte motor `7F`; reply bits 15–8 carry motor `7F` and low byte host `FD`. `00 00 F0 41` decodes little-endian float 30.0. The script checks that source/destination reversal and rejects non-zero reply bits 23–16 before decoding; byte order comes from the worked example. The general table states 00=success and 01=failure but mistranslates which CAN ID is in bits 15–8. That label is not used to reverse routing. [Worked example, PDF p.51; reply table in chapter 4.1](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=51).

The script also requires the echoed two-byte index, reserved bytes 2–3=`00 00`, extended-data-frame flags and DLC 8. A rejected or foreign frame cannot produce a successful value. This is a software fixture/source check; actual arbitration, responses and rejection behavior have not been tested on hardware.

### Read, write, save and protocol conversion

Private Type 17 reads a parameter; Type 18 writes it, and persistence depends on the documented Type 22 save operation. Types 23/25 change bitrate/protocol after power cycling. Mechanical-zero writes, factory restore, magnetic/cogging calibration and protocol changes are deliberate state changes, not detection tools. Stop before switching operating mode. [Chapter 4](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

| Read-only parameter     | Encoding / meaning                                                                                      |
| ----------------------- | ------------------------------------------------------------------------------------------------------- |
| `0x701C` VBUS           | Little-endian IEEE-754 float, V                                                                         |
| `0x7019` mechPos        | Little-endian float, output/load angle in rad                                                           |
| `0x701B` mechVel        | Little-endian float, output/load velocity in rad/s                                                      |
| Type 2 packed telemetry | Big-endian quantized angle/velocity/torque and temperature × 10; use this exact motor/firmware’s ranges |

The two encodings must not be decoded with one byte-order or scale rule. The original first-result script uses only the three float reads. [Parameter table and Type 17 examples](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

## Getting started

### First result through the manufacturer tool

1. Verify the actuator label, chosen manual, **48 V** commissioning supply, mounting, polarity and documented harness. Keep the output unloaded and provide accessible drive-power isolation; support links before removing torque.
2. With power off, connect one motor to the supported debugger and set the documented adapter’s normal mode/termination. Install the official driver/tool from the download center and select the actual serial port.
3. Open the port and choose **Detect Device**. Compare the returned model and ID with the physical unit. Do not click JOG, Start, Set Zero, magnetic calibration or firmware upgrade.
4. While the motor is in standby, choose **Refresh Parameter Table**, then **Read Parameters**. Read bus voltage, position, speed, temperature and fault information; export the baseline before any write. Blue editable and observed fields have different roles.

**Expected result:** the correct model/ID and plausible, repeatable state values while the actuator remains stationary. USB enumeration alone is not motor detection. If the tool does not detect it, inspect supply, AT mode, termination and actual node/protocol before touching gains. [Manual connection/parameter procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

### Original bounded read-only Linux example

5. Use this alternative only with a known SocketCAN adapter and an actuator confirmed in the private protocol. Replace `can0` with the observed interface. Bring up the bus at the motor’s recorded bitrate; these commands configure the host interface, not a motor ID:

```bash
ip -details -statistics link show can0
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000
sudo ip link set can0 up
ip -details -statistics link show can0
```

6. Save the original code as `read_robstride.py`. It sends **only Type 17 parameter reads**, no enable, reset, clear-fault, zero, write or scan broadcast. Pass the individually observed node ID; `0x7f` below is an example, not a claimed factory default.

```python
import argparse
import math
import socket
import struct
import time

parser = argparse.ArgumentParser()
parser.add_argument('--channel', default='can0')
parser.add_argument('--node', type=lambda s: int(s, 0), required=True)
args = parser.parse_args()
if not 1 <= args.node <= 127:
    raise SystemExit('Use an individually identified node ID 1..127')
host = 0xFD
frame = struct.Struct('=IB3x8s')
with socket.socket(socket.PF_CAN, socket.SOCK_RAW, socket.CAN_RAW) as bus:
    bus.bind((args.channel,))
    bus.settimeout(0.1)
    for index, label in [(0x701C, 'bus_V'), (0x7019, 'position_rad'),
                         (0x701B, 'velocity_rad_s')]:
        payload = struct.pack('<H', index) + bytes(6)
        request_id = (17 << 24) | (host << 8) | args.node
        bus.send(frame.pack(request_id | 0x80000000, 8, payload))
        deadline = time.monotonic() + 1.0
        while time.monotonic() < deadline:
            try:
                raw = bus.recv(frame.size)
            except socket.timeout:
                continue
            if len(raw) != frame.size:
                continue
            can_id, size, data = frame.unpack(raw)
            if not can_id & 0x80000000 or can_id & 0x60000000:
                continue
            ident = can_id & 0x1FFFFFFF
            if ((ident >> 24) != 17 or (ident & 0xFF) != host
                    or ((ident >> 8) & 0xFF) != args.node or size != 8
                    or data[:2] != payload[:2] or data[2:4] != bytes(2)):
                continue
            if (ident >> 16) & 0xFF:
                raise SystemExit('Parameter read rejected: ' + raw.hex())
            value = struct.unpack('<f', data[4:8])[0]
            if not math.isfinite(value):
                raise SystemExit('Non-finite feedback; retain raw frame and check revision')
            print(label, value, 'raw=', data.hex())
            break
        else:
            raise SystemExit(f'Timeout reading 0x{index:04X}; inspect ID/protocol/bus')
```

```bash
python3 read_robstride.py --channel can0 --node 0x7f
```

**Expected result:** `bus_V`, `position_rad` and `velocity_rad_s` with raw bytes, or a bounded timeout/rejection. Compare voltage with a meter and near-zero speed with a stationary shaft. The script filters extended ID, source/destination, parameter index and data length; traffic from another node must not satisfy the result. Its 1-second response window is an original diagnostic choice, not a control-loop deadline. [Type 17 wire format](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf), [SocketCAN frame/API](https://docs.kernel.org/networking/can.html).

### Advance to control only after readback

7. Save the current mechanical reference, operating mode and limits. Configure a communication timeout appropriate to the controller; the manual’s `canTimeout` uses 20000 counts per second and zero disables that protection. Confirm actual firmware behavior before treating it as a watchdog.
8. On a secured, unloaded mechanism, choose one supported mode while stopped. For position control, begin at the **observed current pose** with conservative velocity/current and a small displacement inside verified limits. Do not start from an arbitrary numeric zero or the host tool’s 1 rad/s JOG as an assumed safe movement.
9. Verify intended joint/sign and stop behavior, then support the output before disable. Keep the private stop command (Type 4), MIT stop and CANopen quick-stop/state transitions tied to the selected protocol. A host Stop button and physical power isolation have different effects.

**Expected result:** a small, repeatable motion of the intended joint with a demonstrated stop path. No universal motion packet or gain is supplied because protocol selection, zero and load conditions must be known first.

## Troubleshooting and FAQs

| Symptom                                   | Ordered diagnosis / recovery                                                                                                                       |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Port opens but no motor                   | Verify external drive power, adapter normal/boot mode, CAN pair, end termination, bitrate and actual node/protocol.                                |
| Private read times out but traffic exists | Check 29-bit versus 11-bit frames, host/destination IDs and private versus CANopen/MIT selection. Retain raw frames.                               |
| Voltage or angle is implausible           | Compare bytes with Type 17 little-endian float; do not apply Type 2 quantization or gear ratio again.                                              |
| All motors react together                 | Stop; isolate and reconcile duplicate node IDs before adding the chain.                                                                            |
| Unexpected jump/oscillation               | Disable the control workflow, support the mechanism, inspect zero/sign/mode/current and loop gains; increasing stiffness is not a zero correction. |
| Parameter write disappears                | Confirm whether the field is volatile and whether the documented save operation was deliberately performed.                                        |
| Thermal or overcurrent fault              | Record exact fault and conditions; unload/cool and inspect wiring/cooling before clearing. Peak torque is not a stall rating.                      |
| Upgrade stalls                            | Use the matching `rs-0x` firmware and documented retry/re-power flow; preserve the previous version/parameters and first fix bus stability.        |

**Can a firmware update establish compatibility?** No. Match the physical motor, encoder/driver revision and protocol package first. **Does no USB traffic mean failure?** Active reporting is disabled by default in the reference; a quiet bus can be normal until a read request. [Faults, reporting and update chapters](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

## Downloads and technical documents

| Resource                                                                                                                                                                                                              | Model/version and practical use                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| [Exact English manual PDF](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf)                | RS02-IP67 User Manual 260713.pdf; specifications, connector faces, host tool, private/CANopen/MIT protocols and examples |
| [Exact model STEP](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-ip67-20261013.stp)                                  | Manufacturer-listed RS02- ip 67-20261013.stp; inspect thread depth and swept clearance before fabrication                |
| [Official resource tree](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778)                                                                                              | Chinese/English revisions, driver, OTA, EDS and accessory documents; select model and protocol generation                |
| [CANopen EDS](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/canopen/driver_v1.1.eds)                                                  | Configuration resource; verify firmware/object-dictionary agreement                                                      |
| [OTA updater source](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/OTA/OTA.py)                                                                             | Inspect model selection, transport and update prerequisites before running                                               |
| [Manufacturer MotorStudio instructions](https://raw.githubusercontent.com/RobStride/MotorStudio/main/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E4%B9%A6-Instructions/Instructions%20for%20using%20the%20Studio_241122.pdf) | Host-tool connection, serial framing and parameter UI; 2024 document, not the authority for newer motor-specific scales  |
| [Manufacturer download center](https://robstride.com/download)                                                                                                                                                        | Current supported host application/driver route                                                                          |

The 2024 MotorStudio instructions use an older watchdog scaling example (2000=1 s); the selected 2026 motor manual uses **20000=1 s**. Do not combine those revisions.

The retained reference below supplies the existing detailed chapter anchors and diagrams. Direct PDFs remain the authoritative document-version record. No new schematic or pinout has been drawn from appearance.

The selected PDF filename is `RS02-IP67User Manual260713.pdf`, but its final version-history page records **1.0, initial release, 25 November 2025**. Keep both identifiers with a local copy; the filename date and history entry do not establish the firmware fitted to a motor. [Version-history page](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=81).

## References and validation

Reviewed **24 November 2026** against the exact PDF and official resource tree at `9dcbce6df00bfe5a887fd6839ec1f64b2a230778`, with the live OpenELAB product and catalog variant. The source’s ratings, thermal conditions and revision discrepancies are kept beside their claims. Manufacturer artwork remains attributed and retains its original rights; this guide adds original interpretation and diagnostics.

**Validation:** source reviewed; important mounting/connector drawings inspected. Python syntax and synthetic packet fixtures were checked without a real device. SDK installation, actual CAN requests, power, calibration, firmware update and motion were **not run**. Expected results are reproduction checkpoints, not observed hardware outputs.

### Complete model reference

The following reference preserves the established manual sections, working tables, control examples and manufacturer figures. The diagrams hosted on the original image service are retained historical figures; compare connector and mechanical revisions with the linked exact-model PDF. Host-tool screenshots show the documented interface, not a claim that the software was executed for this guide.

### Precautions <a href="#block-33ad4c79856d817abb21ff4d85233cc4" id="block-33ad4c79856d817abb21ff4d85233cc4"></a>

1. Please use according to the working parameters specified in this article, otherwise it may cause serious damage to the product!
2. Do not switch the control mode when the joint is running. If you need to switch, send the command to stop the operation before switching.
3. Check whether the parts are in good condition before use. If the parts are missing or damaged, contact technical support in time.
4. Do not disassemble the motor at will, so as to avoid unrecoverable failure.
5. Ensure that there is no short circuit when the motor is connected, and the interface is correctly connected as required.

### 1. Motor specification <a href="#block-33ad4c79856d812ab82ddd0d089200ec" id="block-33ad4c79856d812ab82ddd0d089200ec"></a>

#### 1.1 Outline and mounting dimensions <a href="#block-33ad4c79856d81b6b660cf7c40c8f25f" id="block-33ad4c79856d81b6b660cf7c40c8f25f"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/03bcfb89-38cb-45da-b265-991b99f3492d/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.1 Outline and mounting dimensions — retained manufacturer figure 1" height="1426" width="2324">

When fixing, the screw depth should not exceed the depth of the casing thread.

#### 1.2 Standard service condition <a href="#block-33ad4c79856d81f4a995c1190862c745" id="block-33ad4c79856d81f4a995c1190862c745"></a>

| Condition                        | Dated exact-model value                                               |
| -------------------------------- | --------------------------------------------------------------------- |
| Rated / operating supply         | 48 V DC / 24–60 V DC                                                  |
| Rated load and cooling           | 6 N·m; aluminum heat sink 260 × 280 mm                                |
| Directions / mounting attitude   | CW and CCW viewed from the output shaft; shaft horizontal or vertical |
| Standard ambient / working range | 25 ±5 °C / −20 to 50 °C                                               |
| Standard RH / allowed RH         | 65% / 5–85%, non-condensing                                           |
| Storage temperature              | −30 to 70 °C                                                          |
| Insulation class                 | B                                                                     |

[RS02-IP67User Manual260713.pdf: §1.2 service conditions](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 1.3 Electrical characteristic <a href="#block-33ad4c79856d81d3bf5fe62d34e73c69" id="block-33ad4c79856d81d3bf5fe62d34e73c69"></a>

| Electrical characteristic                                              | Dated value / test condition                                                                                                 |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| No-load output speed                                                   | 410 rpm ±10%                                                                                                                 |
| No-load phase current                                                  | 0.5 A RMS                                                                                                                    |
| Rated load / test speed                                                | 6 N·m at 100 rpm                                                                                                             |
| Rated phase current                                                    | 7 A peak ±10%                                                                                                                |
| Peak torque / maximum phase current                                    | 17 N·m / 23 A peak ±10%                                                                                                      |
| Insulation resistance / winding                                        | 100 MΩ; source test-voltage notation “DC 500 VAC” is inconsistent and must be clarified before reproducing a dielectric test |
| Housing/winding dielectric test (manufacturer qualification condition) | 600 V AC, 1 s, 2 mA; not a commissioning procedure                                                                           |
| Back EMF                                                               | 9.6 V RMS/krpm ±10%                                                                                                          |
| Torque constant                                                        | 1.22 N·m/A RMS                                                                                                               |

[RS02-IP67User Manual260713.pdf: §1.3 electrical values, torque–speed and overload tests](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

The dated overload test uses 25 °C ambient, an aluminum heat sink and a stated 145 °C winding constraint; the service-condition sink is 260 × 280 mm. The source’s parenthetical 180 °C value is distinct from the test/protection constraint. It is not an application operating limit. The thermal model estimates phase heating from phase current and the thermistor; a stalled joint heats unevenly. The manual states a 1.414 factor for single-phase stall heating relative to rotation, not a blanket 1.414 multiplier for permitted torque or supply current.

#### Dated rotating and stalled overload data

These are manufacturer-reported thermal test durations read from the dated manual’s image tables, not measured results from this guide. “Rated” is retained as the table label rather than converted to an unlimited dwell time. The load is torque in N·m in this motor’s surrounding torque/overload context; elapsed times are seconds. Preserve the ambient, heat-sink, speed and temperature conditions stated above.

| Load (N·m) | Rotating test: time (s) | Stalled test: time (s) |
| ---------- | ----------------------- | ---------------------- |
| 17         | 10                      | 6                      |
| 16         | 14                      | Not tabulated          |
| 15         | 18                      | 10                     |
| 14         | 29                      | Not tabulated          |
| 13         | 42                      | 22                     |
| 12         | 71                      | Not tabulated          |
| 11         | 165                     | 40                     |
| 10         | 250                     | Not tabulated          |
| 9          | 838                     | 174                    |
| 7          | rated                   | 867                    |
| 6          | Not tabulated           | rated                  |

The rows describe separate tests; “Not tabulated” means the source supplies no duration at that load in that condition. They do not define a repetitive duty cycle or authorize disabling protection. The rotating table labels **7 N·m** as rated, while the same PDF’s service/electrical sections specify **6 N·m**; its stalled table labels 6 N·m as rated. Keep the 6 N·m service specification and this thermal-table conflict distinct. [Dated overload image tables, PDF pp. 10, 11](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=10).

**Retained manufacturer curves and test tables:** these original figures include the torque–speed plots, overload curve, test data and rotating/stalled thermal tables. They retain the historical figure captions and numerical curves from this page’s source revision. Where a caption conflicts with the dated values above, use it only as historical test data; do not combine its durations with a newer cooling/temperature condition.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8fd82a6b-48d4-4e57-86d7-1717239c9d75/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.3 Electrical characteristic — retained manufacturer figure 1" height="289.12998976458545" width="528">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9871c0ae-a952-496b-87bf-d82be0bfe3ab/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.3 Electrical characteristic — retained manufacturer figure 2" height="258.8659160696008" width="528">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/120ba076-c0a4-49b5-a9d6-30e006f1b95e/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.3 Electrical characteristic — retained manufacturer figure 3" height="314.41478439425055" width="528">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1113f60d-98f5-4eaf-9f82-06484d7908c7/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.3 Electrical characteristic — retained manufacturer figure 4" height="237.68674698795184" width="288">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2b807017-75fa-451e-99b5-a2189b26c5fe/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.3 Electrical characteristic — retained manufacturer figure 5" height="236.46918489065607" width="288">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/53b9a92a-0b22-4b4a-91b9-8852c06f0ff6/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 1.3 Electrical characteristic — retained manufacturer figure 6" height="151.64418938307028" width="288">

#### 1.4 Mechanical characteristic <a href="#block-33ad4c79856d817ea3b6d2ae98c27520" id="block-33ad4c79856d817ea3b6d2ae98c27520"></a>

| Mechanical characteristic | Exact-model value                                |
| ------------------------- | ------------------------------------------------ |
| Mass                      | 380 ±3 in this PDF; manufacturer overview: 490 g |
| Motor poles               | 28                                               |
| Phases / drive            | 3 / FOC                                          |
| Reduction ratio           | 7.75:1                                           |

[RS02-IP67User Manual260713.pdf: §1.4 mechanical characteristics](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf). The sealed-model overview’s 490 g and this PDF’s repeated unsealed 380 ±3 g disagree. Verify the delivered assembly mass/drawing for inertia and mounting; do not silently use the unsealed housing as the sealed model.

### 2. Driver Product Information <a href="#block-33ad4c79856d811db0e7d1f6437ba98b" id="block-33ad4c79856d811db0e7d1f6437ba98b"></a>

#### 2.1 Driver product Specifications <a href="#block-33ad4c79856d812d996bd9d7a1b363bb" id="block-33ad4c79856d812d996bd9d7a1b363bb"></a>

| Driver characteristic                                  | Value as specified     |
| ------------------------------------------------------ | ---------------------- |
| The rated working voltage                              | 48 VDC                 |
| The maximum allowable voltage                          | 60 VDC                 |
| Rated working phase current                            | 7 Apk                  |
| Maximum allowable phase current                        | 23 Apk                 |
| Standby current (source labels this “power”)           | ≤18 mA                 |
| CAN bus bit rate                                       | 1 Mbps                 |
| Dimensions                                             | Φ58 mm                 |
| Working environment temperature                        | -20 °C to 50 °C        |
| The maximum allowable temperature of the control board | 145 °C                 |
| encoder resolution                                     | 14 bit (absolute turn) |

[RS02-IP67User Manual260713.pdf: §2.1 driver table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=12). Standby values expressed in mA are current, despite the source’s “power” label. Board temperature, winding temperature and fault thresholds are separate fields.

#### 2.2 Driver interface definition <a href="#block-33ad4c79856d8104be70e1a601d05b31" id="block-33ad4c79856d8104be70e1a601d05b31"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/708dd0b7-76ca-4247-a052-d228ef8e4fc0/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 2.2 Driver interface definition — retained manufacturer figure 1" height="447.42637644046096" width="624">

#### 2.3 Driver function pin and device description <a href="#block-33ad4c79856d810eb2bae0d05c60d4d8" id="block-33ad4c79856d810eb2bae0d05c60d4d8"></a>

1. Power supply and CAN communication
2. Download port
3. Indicator light

| **Pin** | **description**                                                                            |
| ------- | ------------------------------------------------------------------------------------------ |
| 1       | If the blue indicator blinks, the program is running normally                              |
| 2       | Power indicator. If the indicator is red, the power supply to the entire network is normal |

| **Pin** | **description**     |
| ------- | ------------------- |
| 1       | SWDIO (data)        |
| 2       | SWCLK (clock)       |
| 3       | 3V3 (positive 3.3V) |
| 4       | GND                 |

| **Pin** | **description**                                |
| ------- | ---------------------------------------------- |
| 1       | The positive electrode of the power supply (+) |
| 2       | Negative electrode of the power supply (-)     |
| 3       | CAN CAN\_L                                     |
| 4       | CAN the high side of the communication CAN\_H  |

The numbers 1–4 in the power/CAN list describe **functions**, not four adjacent cavity numbers on the sealed six-position connector. The indicator list’s 1/2 are LED items, not connector pins. For the actual **male front view**, the small upper-left red signal is CAN-H and the upper-center small black signal is CAN-L; lower-left thick black is GND and lower-right thick red is VBAT+. Two positions are marked unused. Keep this keyed sealed drawing with the harness; the cable-side view is mirrored. The SWD list is a separate service-port table. [Exact sealed-model connector drawing and port table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

### 3. Upper computer instructions <a href="#block-33ad4c79856d810fa5c0ee4f932e7fed" id="block-33ad4c79856d810fa5c0ee4f932e7fed"></a>

Please go to [www.robstride.com](http://www.robstride.com/) website download center

#### 3.1 Hardware disposition <a href="#block-33ad4c79856d8142ae8dc16ea06e6cb9" id="block-33ad4c79856d8142ae8dc16ea06e6cb9"></a>

The articulated motor uses the CAN communication mode and has two communication cables. It is connected to the debugger through the can to USB tool. The debugger needs to be installed with the ch340 driver in advance and works in AT mode by default.

It should be noted that we are based on the specific can to USB tool development of the debugger, so we need to use our recommended serial port tool to debug the debugger, if you want to transplant to other debugger platform can refer to the third chapter of the instructions for development.

The CAN to USB tool is recommended to use the official USB-to-CAN module of RobStride. The frame header of the corresponding serial port protocol is 4154, and the frame tail is 0D 0A.

When using the CAN-to-USB module, pay attention to the settings of the DIP switches on the module: When DIP switch 1 is in the ON position, the module enters Boot mode and cannot establish a connection with the host computer. When DIP switch 2 is in the ON position, a 120Ω terminal resistor is connected to the module port, allowing normal communication with the host computer.

#### 3.2 Upper computer interface and description <a href="#block-33ad4c79856d81a0954bd740f950d6ca" id="block-33ad4c79856d81a0954bd740f950d6ca"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9072c1f0-5a05-45ee-bd7d-6c7ab2a5fe23/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.2 Upper computer interface and description — retained manufacturer figure 1" height="1514" width="2460">

Mainly includes:

1. Motor Connection Module
2. Refreshing the Serial Port
3. Opening the Serial Port
4. Testing the Device
5. Motor Configuration Module
6. Starting the Upgrade
7. Opening a File
8. Starting the Upgrade
9. Modifying the Motor CAN ID
10. Setting the Motor's Mechanical Zero Position
11. Motor Upgrade Module
12. Magnetic Encoder Calibration
13. Motor Active Reporting Switch
14. Setting the Motor Active Reporting Time
15. Modifying the Motor CAN ID
16. Setting the Motor's Mechanical Zero Position
17. Motor Main Interface
18. Parameter Settings
19. Motor Oscilloscope
20. Run and Debug Area
21. Parameter Debugging Buttons
22. Motor Mode Configuration and Parameter Modification
23. Sine Signal Testing

#### 3.3 Motor settings <a href="#block-33ad4c79856d81e28fdfe6cfced8aef2" id="block-33ad4c79856d81e28fdfe6cfced8aef2"></a>

#### 3.3.1 Motor connection settings <a href="#block-33ad4c79856d8167b8a2fb3cd65ffb72" id="block-33ad4c79856d8167b8a2fb3cd65ffb72"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b850fc1e-d6a1-40c0-bf33-d97df6819365/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.1 Motor connection settings — retained manufacturer figure 1" height="345.59999999999997" width="288">

Connect the CAN to USB tool (install the ch340 driver, which works in AT mode by default), click Refresh Serial Port, open the serial port, and click Detect Device to detect the corresponding motor. The green text below is the motor type.

#### 3.3.2 Motor configuration module <a href="#block-33ad4c79856d816f8df8de1024020ace" id="block-33ad4c79856d816f8df8de1024020ace"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/430fdfe5-5fc1-4b32-b4b8-4eaf6fd71bfb/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.2 Motor configuration module — retained manufacturer figure 1" height="352.3404255319149" width="288">

1. Recalibrate the motor magnetic encoder. Reinstalling the motor board and motor, or reconnecting the motor's three-phase wiring requires recalibrating the magnetic encoder.
2. Enable active motor reporting. Click Start Reporting to enable active motor reporting in communication type 2. You can set the interval below, with a minimum of 10 ms.
3. Set ID: Set the motor's CAN ID.
4. Set Zero Position: Set the current position to 0.

#### 3.3.3 Motor upgrade module <a href="#block-33ad4c79856d81c09ae3e3e409c9d2c2" id="block-33ad4c79856d81c09ae3e3e409c9d2c2"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b365de8b-b2ef-478f-84e1-0880611ec65a/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.3 Motor upgrade module — retained manufacturer figure 1" height="343.644908616188" width="288">

1\. Click to open the file and select the firmware to upgrade. The rs-0x in the firmware name is the selected motor type.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1e0cecaf-d8df-47eb-ba3a-91709366098d/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.3 Motor upgrade module — retained manufacturer figure 2" height="329.78238341968915" width="288">

2. Click Start Upgrade, and the motor will enter the upgrade preparation stage.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d66027c6-c687-4e81-9ccb-27b2957af15f/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.3 Motor upgrade module — retained manufacturer figure 3" height="347.96915167095113" width="288">

3. When the green text "Device has entered upgrade mode" pops up, click to start the upgrade

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1254900e-0b3f-4e72-b74b-a6a29ef7b7c3/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.3 Motor upgrade module — retained manufacturer figure 4" height="346.96062992125985" width="288">

4. When the green text "Upgrade Successfully" pops up, the upgrade is complete.
5. If the green progress bar gets stuck halfway through the upgrade, you can click to stop the upgrade, or re-power on and re-enter the upgrade process. The internal program of the motor will not be lost after the upgrade fails. Please check whether the communication environment is good before upgrading again.

#### 3.3.4 Parameter settings <a href="#block-33ad4c79856d81cda2c4ca4845d118b3" id="block-33ad4c79856d81cda2c4ca4845d118b3"></a>

Refresh parameters with the motor stopped, then use **Read**, **Write** or **Restore Factory** for the selected field. Export/read the current configuration before a write or reset. The following is the exact dated manual’s **host-tool schema and example snapshot**. Its `0x20xx`/`0x30xx` function codes are distinct from the private-CAN `0x70xx` indices. The sample values are not certified factory defaults or motor operating limits.

| Function code | Field                  | Type   | Access        | Printed max | Printed min | Example value                  | Meaning / source limitation                                        |
| ------------- | ---------------------- | ------ | ------------- | ----------- | ----------- | ------------------------------ | ------------------------------------------------------------------ |
| `0X0000`      | `Name`                 | String | R/W           | —           | —           | Unprogrammed string in example | —                                                                  |
| `0X0001`      | `BarCode`              | String | R/W           | —           | —           | Unprogrammed string in example | —                                                                  |
| `0X1000`      | `BootCodeVersion`      | String | R             | —           | —           | 0.1.5                          | —                                                                  |
| `0X1001`      | `BootBuildDate`        | String | R             | —           | —           | Mar 16 2022                    | —                                                                  |
| `0X1002`      | `BootBuildTime`        | String | R             | —           | —           | 20:22:09                       | —                                                                  |
| `0X1003`      | `AppCodeVersion`       | String | R             | —           | —           | 0.0.0.1                        | Motor program version number                                       |
| `0X1004`      | `AppGitVersion`        | String | R             | —           | —           | 7b844b0fM                      | —                                                                  |
| `0X1005`      | `AppBuildDate`         | String | R             | —           | —           | Apr 14 2022                    | —                                                                  |
| `0X1006`      | `AppBuildTime`         | String | R             | —           | —           | 20:30:22                       | —                                                                  |
| `0X1007`      | `AppCodeName`          | String | R             | —           | —           | Lingzu motor \_                | —                                                                  |
| `0X2000`      | `echoPara1`            | uint16 | Configuration | 74          | 5           | 5                              | —                                                                  |
| `0X2001`      | `echoPara2`            | uint16 | Configuration | 74          | 5           | 5                              | —                                                                  |
| `0X2002`      | `echoPara3`            | uint16 | Configuration | 74          | 5           | 5                              | —                                                                  |
| `0X2003`      | `echoPara4`            | uint16 | Configuration | 74          | 5           | 5                              | —                                                                  |
| `0X2004`      | `echoFreHz`            | uint32 | R/W           | 10000       | 1           | 500                            | —                                                                  |
| `0X2005`      | `MechOffset`           | float  | Configuration | 7           | -7          | 4.619583                       | Motor magnetic encoder Angle offset                                |
| `0X2006`      | `status2`              | float  | R/W           | 50          | -50         | 4.52                           | Reserved parameter                                                 |
| `0X2007`      | `limit_torque`         | float  | R/W           | 17          | 0           | 17                             | Torque limitation                                                  |
| `0X2008`      | `I_FW_MAX`             | float  | R/W           | 33          | 0           | 0                              | Weak magnetic current value, default 0                             |
| `0X2009`      | `motor_baud`           | uint8  | Configuration | 20          | 0           | 1                              | Baud rate flag bit                                                 |
| `0X200a`      | `CAN_ID`               | uint8  | Configuration | 127         | 0           | 1                              | id of this object                                                  |
| `0X200b`      | `CAN_MASTER`           | uint8  | Configuration | 127         | 0           | 0                              | can host id                                                        |
| `0X200c`      | `CAN_TIMEOUT`          | uint32 | R/W           | 100000      | 0           | 0                              | can timeout threshold. The default value is 0                      |
| `0X200d`      | `status2`              | int16  | R/W           | 1500        | 0           | 800                            | Reserved parameter                                                 |
| `0X200e`      | `status3`              | uint32 | R/W           | 1000000     | 1000        | 20000                          | Reserved parameter                                                 |
| `0X200f`      | `Status1`              | float  | R/W           | 64          | 1           | 7.75                           | Reserved parameter                                                 |
| `0X2010`      | `status6`              | uint8  | R/W           | 1           | 0           | 1                              | Reserved parameter                                                 |
| `0X2011`      | `cur_filt_gain`        | float  | R/W           | 1           | 0           | 0.9                            | Current filtering parameter                                        |
| `0X2012`      | `cur_kp`               | float  | R/W           | 200         | 0           | 0.025                          | Current kp                                                         |
| `0X2013`      | `cur_ki`               | float  | R/W           | 200         | 0           | 0.0258                         | Current ki                                                         |
| `0X2014`      | `spd_kp`               | float  | R/W           | 200         | 0           | 2                              | Velocity kp                                                        |
| `0X2015`      | `spd_ki`               | float  | R/W           | 200         | 0           | 0.021                          | Speed ki                                                           |
| `0X2016`      | `loc_kp`               | float  | R/W           | 200         | 0           | 30                             | Position kp                                                        |
| `0X2017`      | `spd_filt_gain`        | float  | R/W           | 1           | 0           | 0.1                            | Velocity filter parameter                                          |
| `0X2018`      | `limit_spd`            | float  | R/W           | 200         | 0           | 2                              | Location mode speed limit                                          |
| `0X2019`      | `limit_cur`            | float  | R/W           | 23          | 0           | 23                             | Position, Velocity mode current limit                              |
| `0X201a`      | `loc_ref_filt_gain`    | float  | R/W           | 100         | 0           | 0                              | Reserved parameter                                                 |
| `0X201b`      | `limit_loc`            | float  | R/W           | 100         | 0           | 0                              | Reserved parameter                                                 |
| `0X201c`      | `position_offset`      | float  | R/W           | 27          | 0           | 0                              | High speed segment offset                                          |
| `0X201d`      | `chasu_angle_offset`   | float  | R/W           | 27          | 0           | 0                              | The low end is offset                                              |
| `0X201e`      | `zero_sta`             | float  | R/W           | 150         | 0           | —                              | Zero marker                                                        |
| `0x201f`      | `protocol_1`           | float  | R/W           | 20          | 0           | —                              | Protocol flag                                                      |
| `0X3000`      | `timeUse0`             | float  | R/W           | 1000        | 0           | —                              | —                                                                  |
| `0X3001`      | `timeUse1`             | float  | R/W           | 100         | 0           | 0                              | —                                                                  |
| `0X3002`      | `timeUse2`             | uint16 | R             | —           | —           | 5                              | —                                                                  |
| `0X3003`      | `timeUse3`             | uint16 | R             | —           | —           | 0                              | —                                                                  |
| `0X3004`      | `encoderRaw`           | uint16 | R             | —           | —           | 10                             | Magnetic encoder sampling value                                    |
| `0X3005`      | `mcuTemp`              | uint16 | R             | —           | —           | 0                              | mcu internal temperatur e, \*10                                    |
| `0X3006`      | `motorTemp`            | int16  | R             | —           | —           | 11396                          | Motor ntc temperatur e, \*10                                       |
| `0X3007`      | `vBus(mv)`             | int16  | R             | —           | —           | 337                            | Bus voltage                                                        |
| `0X3008`      | `adc1Offset`           | int16  | R             | —           | —           | 333                            | adc sampling channel 1 Zero current bias                           |
| `0X3009`      | `adc2Offset`           | uint16 | R             | —           | —           | 24195                          | adc sampling channel 2 Zero current bias                           |
| `0X300a`      | `adc1Raw`              | int32  | R             | —           | —           | 2084                           | adc sampling value 1                                               |
| `0X300b`      | `adc2Raw`              | int32  | R             | —           | —           | 2084                           | adc sampling value 2                                               |
| `0X300c`      | `VBUS`                 | uint16 | R             | —           | —           | 1232                           | Bus voltage V                                                      |
| `0X300d`      | `cmdId`                | uint16 | R             | —           | —           | 1212                           | id ring instruction, A                                             |
| `0X300e`      | `cmdIq`                | float  | R             | —           | —           | 36                             | iq ring command, A                                                 |
| `0X300f`      | `cmdlocref`            | float  | R             | —           | —           | 0                              | Position loop command, rad                                         |
| `0X3010`      | `cmdspdref`            | float  | R             | —           | —           | 0                              | Speed loop command, rad/s                                          |
| `0X3011`      | `cmdTorque`            | float  | R             | —           | —           | 0                              | Torque instruction, nm                                             |
| `0X3012`      | `cmdPos`               | float  | R             | —           | —           | 0                              | mit Protocol Angle instruction                                     |
| `0X3013`      | `cmdVel`               | float  | R             | —           | —           | 0                              | mit Protocol Speed instruction                                     |
| `0X3014`      | `rotation`             | float  | R             | —           | —           | 0                              | Number of turns                                                    |
| `0X3015`      | `modPos`               | float  | R             | —           | —           | 0                              | Motor uncounted coil mechanical Angle, rad                         |
| `0X3016`      | `mechPos`              | int16  | R             | —           | —           | 1                              | Load end loop mechanical Angle, rad                                |
| `0X3017`      | `mechVel`              | float  | R             | —           | —           | 4.363409                       | Load speed: rad/s                                                  |
| `0X3018`      | `elecPos`              | float  | R             | —           | —           | 0.777679                       | Electrical Angle                                                   |
| `0X3019`      | `ia`                   | float  | R             | —           | —           | 0.036618                       | U-wire current, A                                                  |
| `0X301a`      | `ib`                   | float  | R             | —           | —           | 4.714761                       | V-wire current, A                                                  |
| `0X301b`      | `ic`                   | float  | R             | —           | —           | 0                              | W-wire current, A                                                  |
| `0X301c`      | `timeout`              | float  | R             | —           | —           | 0                              | Timeout counter value                                              |
| `0X301d`      | `phaseOrder`           | float  | R             | —           | —           | 0                              | Directional marking                                                |
| `0X301e`      | `iqf`                  | uint32 | R             | —           | —           | 31600                          | iq filter value，A                                                  |
| `0X301f`      | `boardTemp`            | uint8  | R             | —           | —           | 0                              | Plate temperatur e，\*10                                            |
| `0X3020`      | `iq`                   | float  | R             | —           | —           | 0                              | iq Original value，A                                                |
| `0X3021`      | `id`                   | int16  | R             | —           | —           | 359                            | id Original value，A                                                |
| `0X3022`      | `faultSta`             | float  | R             | —           | —           | 0                              | Fault status value                                                 |
| `0X3023`      | `warnSta`              | float  | R             | —           | —           | 0                              | Warning status value                                               |
| `0X3024`      | `drv_fault`            | uint32 | R             | —           | —           | 0                              | The driver chip fault value is 1                                   |
| `0X3025`      | `drv_temp`             | uint32 | R             | —           | —           | 0                              | The driver chip fault value is 2                                   |
| `0X3026`      | `Uq`                   | uint16 | R             | —           | —           | 0                              | Q-axis voltage                                                     |
| `0X3027`      | `Ud`                   | int16  | R             | —           | —           | 48                             | D-axis voltage                                                     |
| `0X3028`      | `dtc_u`                | float  | R             | —           | —           | 0                              | The duty cycle of the U-phase output                               |
| `0X3029`      | `dtc_v`                | float  | R             | —           | —           | 0                              | The duty cycle of the V-phase output                               |
| `0X302a`      | `dtc_w`                | float  | R             | —           | —           | 0                              | The duty cycle of the W-phase output                               |
| `0X302b`      | `VBUS`                 | float  | R             | —           | —           | 0                              | Vbus in the closed loop                                            |
| `0X302c`      | `torque_fdb`           | float  | R             | —           | —           | 0                              | Torque feedback value，nm                                           |
| `0X302d`      | `rated_i`              | float  | R             | —           | —           | 24.195                         | Rated current of motor                                             |
| `0X302e`      | `limit_i`              | float  | R             | —           | —           | 0                              | The motor limits the maximum current                               |
| `0X302f`      | `spd_ref`              | float  | R             | —           | —           | 8                              | Motor speed expectation                                            |
| `0X3030`      | `motor_mech_angle`     | float  | R             | —           | —           | 27                             | Motor speed expectation 2                                          |
| `0X3031`      | `position`             | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3032`      | `chasu_angle_init`     | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3033`      | `chasu_angle_out`      | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3034`      | `motormechinit1`       | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3035`      | `mech_angle_init2`     | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3036`      | `mech_angle_rotations` | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3037`      | `cmdlocref_1`          | float  | R             | —           | —           | 0                              | Motor position determinati on parameters                           |
| `0X3038`      | `Status1`              | float  | R             | —           | —           | 0                              | Retention parameter                                                |
| `0X3039`      | `ElecOffset`           | uint32 | R             | —           | —           | 0                              | electrical Angle offset                                            |
| `0X303a`      | `mcOverTemp`           | uint32 | R             | —           | —           | 0                              | Overtempe rature threshold                                         |
| `0X303b`      | `Kt_Nm/Amp`            | uint32 | R             | —           | —           | 0                              | Moment coefficient                                                 |
| `0X303c`      | `Tqcali_Type`          | uint32 | R             | —           | —           | 0                              | Motor type                                                         |
| `0X303d`      | `fault1`               | uint32 | R             | —           | —           | 0                              | Log failure                                                        |
| `0X303e`      | `fault2`               | uint32 | R             | —           | —           | 0                              | Log failure                                                        |
| `0X303f`      | `fault3`               | uint32 | R             | —           | —           | 0                              | Log failure                                                        |
| `0X3040`      | `fault4`               | uint32 | R             | —           | —           | 0                              | Log failure                                                        |
| `0X3041`      | `fault5`               | float  | R             | —           | —           | 0                              | Log failure                                                        |
| `0X3042`      | `fault6`               | int16  | R             | —           | —           | 0                              | Log failure                                                        |
| `0X3043`      | `fault7`               | float  | R             | —           | —           | 0                              | Log failure                                                        |
| `0X3044`      | `fault8`               | uint8  | R             | —           | —           | 0                              | Log failure                                                        |
| `0X3045`      | `theta_mech_1`         | float  | R             | —           | —           | 0                              | Type 2 Low speed Angle                                             |
| `0X3046`      | `adc0ffset_1`          | int32  | R             | —           | —           | 2051                           | adc sampling channel 1 Zero current bias                           |
| `0X3047`      | `adc0ffset_2`          | int32  | R             | —           | —           | 2080                           | adc sampling channel 2 Zero current bias                           |
| `0X3048`      | `can_status`           | uin8   | R             | —           | —           | 1                              | CAN status; source type is printed “uin8”; verify width before use |

[Host parameter table, PDF pp. 21–29](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=21). Bounds reproduced here are the manual’s UI bounds, not recommended settings. In particular, an unsigned field cannot have a negative minimum, and a `uint8` cannot represent 300. Blank source cells are shown as “—”; they do not mean zero. Firmware examples in this table identify the photographed/documented software, not the firmware installed in a purchased motor. Read back by field name and version before relying on an address.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/83fd5db5-0ba6-4b8a-b6b5-454a13792e94/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.4 Parameter settings — retained manufacturer figure 1" height="548.535120412844" width="832.9921875">

#### 3.3.5 Oscilloscope <a href="#block-33ad4c79856d8181bc4dc05813cbf33a" id="block-33ad4c79856d8181bc4dc05813cbf33a"></a>

The interface supports viewing and observing the graph generated by realtime data, including motor Id/Iq current, temperature, real-time speed at the output end, rotor (encoder) position, output end position, etc.

Click on the oscilloscope module in the analysis module, select the appropriate parameters in the channel (parameter meaning can be referred to the parameter table), set the output frequency, click on the start plot to observe the data graph, stop the plot to stop the observation graph.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e60922ae-c4dc-44fa-aba4-9b40bbab8541/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.5 Oscilloscope — retained manufacturer figure 1" height="1492" width="2190">

The command sent is in the communication command box below

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ccf2ed0c-dbe1-49c7-b93c-7900c7a42409/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.5 Oscilloscope — retained manufacturer figure 2" height="1376" width="2212">

Communication box instruction example:

41 54 90 07 e8 0c 08 05 70 00 00 01 00 00 00 0d 0a

The meaning is as follows

| 41 54        | 90 07 e8 0c                    | 08  | 05 70 00 00 01 00 00 00 | 0d 0a      |
| ------------ | ------------------------------ | --- | ----------------------- | ---------- |
| frame header | Adapter-encoded CAN identifier | DLC | data frame              | frame tail |

The translation of extended frame canid into real canid requires the following transformations:

90 07 e8 0c converts to binary as 1001 0000 0000 0111 1110 1000 0000 1100, shift three positions to the right and it becomes 1 0010 0000 0000 1111 11010000 0001, convert it to hexadecimal, It is 12 00 FD 01. According to the communication protocol, the meaning is as follows:

| 12 in hexadecimal                       | 0          | FD      | 1            |
| --------------------------------------- | ---------- | ------- | ------------ |
| Communication type 18 (in decimal base) | No meaning | host id | motor CAN ID |

The adapter identifier `0x9007E80C` includes its frame-format bits: shifting it right by 3 yields CAN identifier `0x1200FD01`. The following `08` is the CAN data length, not the extended-frame flag. The payload `05 70 00 00 01 00 00 00` writes private `run_mode` to PP (1); it is a **state-changing decoded example**, not a discovery probe. [RS02-IP67User Manual260713.pdf: §3.3.5 adapter log example](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 3.3.6 can communication failure protection <a href="#block-33ad4c79856d817cb706d7c79a619407" id="block-33ad4c79856d817cb706d7c79a619407"></a>

When the value of CAN\_TIMEOUT is 0, this function is disabled When the CAN\_TIMEOUT value is non-0, when the motor does not receive the can command within a certain period of time, the motor enters the reset mode, and 20000 is 1 s

#### 3.3.7 Motor fault instructions <a href="#block-33ad4c79856d81e79d86cfb58c9f1cc9" id="block-33ad4c79856d81e79d86cfb58c9f1cc9"></a>

Function code 0x3022 indicates the fault code, where Bit 16: Motor current fault: A-phase current sampling overcurrent Bit 14: Motor stall overload algorithm protection Bit 9: Position initialization fault Bit 8: Hardware identification fault Bit 7: Encoder uncalibrated: Motor encoder not calibrated Bit 5: Motor current fault: C-phase current sampling overcurrent Bit 4: Motor current fault: B-phase current sampling overcurrent Bit 3: Overvoltage fault: the motor voltage exceeds the protection voltage by 60V Bit 2: Undervoltage fault: the motor voltage is lower than the protection voltage of 12V Bit 1: Driver chip failure: Motor driver chip failure reported Bit 0: Motor overtemperature fault: motor thermistor temperature exceeds 135 degrees Function code 0x3024 is driver chip fault code 1. The specific faults are as follows

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ca1c7ac2-4369-4027-bb8f-10c3cc898b9e/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.7 Motor fault instructions — retained manufacturer figure 1" height="958" width="2242">

Function code 0x3025 is driver chip fault code 2. The specific faults are as follows

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/03c5eaf3-40af-4ab9-b587-c56e9ed3d682/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.3.7 Motor fault instructions — retained manufacturer figure 2" height="1078" width="2364">

**Address-version check:** the host schema in this same dated PDF lists `0X3022` faultSta, `0X3023` warnSta, `0X3024` drv\_fault, `0X3025` drv\_temp. The fault-instructions prose may still use the previous addresses (`0x3022`, `0x3024`, `0x3025`). Where these differ, read by the verified field name/firmware in the host tool; do not treat the prose and schema as an identical address map. The Type 21 wire fault definition below avoids guessing a GUI address. The two retained driver-register diagrams belong to their documented driver chip and are not a generic fault mask for every revision. [RS02-IP67User Manual260713.pdf: §3.3.7 versus §3.3.4](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 3.4 Control Demo <a href="#block-33ad4c79856d8151adb8f7d7738557d6" id="block-33ad4c79856d8151adb8f7d7738557d6"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5a1065ba-20cb-400a-8aaa-bb3547295b26/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4 Control Demo — retained manufacturer figure 1" height="793.1964809384165" width="336">

Jog Run

Click JOG +/- to run the motor forward and reverse at a speed of 1 rad/s. Control Mode Switching

Select the desired control mode in the command box to the right of the run mode.

#### 3.4.1 Operation and control mode <a href="#block-33ad4c79856d818d9341ce3d34da2859" id="block-33ad4c79856d818d9341ce3d34da2859"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a60892ff-7fc0-409e-8fb9-48d8b7a4b91e/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.1 Operation and control mode — retained manufacturer figure 1" height="469.1014492753623" width="336">

1. Switch the control mode to operation mode.
2. The motor starts running and enters motor\_mode.
3. Set five parameter values and click Start or Send continuously. The motor will return feedback frames and run according to the target command.
4. Click Stop to stop the motor and terminate the continuous sending of commands.

#### 3.4.2 Current Mode <a href="#block-33ad4c79856d8131bd47c93f2eeda7c9" id="block-33ad4c79856d8131bd47c93f2eeda7c9"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7bbca233-8fe0-4393-925f-5b3c5c822f5a/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.2 Current Mode — retained manufacturer figure 1" height="476.3943661971831" width="336">

1. Switch the control mode to current mode.
2. The motor starts running and enters motor\_mode.
3. Set the current command value for Iq Command 1 (A). Click the >>button on the right. The motor will follow the current command.
4. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/228d9d90-1ec3-45bb-823f-a66f77968ec1/image/w=1920,quality=80,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.2 Current Mode — retained manufacturer figure 2" width="100%">

Motor Current Sine Test

1. Switch the control mode to current mode.
2. The motor starts running and enters motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command will be planned according to the sine law.
4. Click Stop to stop the motor.

#### 3.4.3 Speed Mode <a href="#block-33ad4c79856d8197aa77d8a32b2333eb" id="block-33ad4c79856d8197aa77d8a32b2333eb"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/58aac5d5-bc43-46df-81f5-b213c82e764c/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.3 Speed Mode — retained manufacturer figure 1" height="466.1621621621622" width="336">

1. Switch the control mode to speed mode.
2. The motor starts running and enters motor\_mode.
3. First, set the current limit (maximum phase current) and speed step value(motor acceleration). If no settings are made, the motor will operate at the default values. Finally, set the speed command (target speed). The motor will follow the command.
4. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f91ffac0-7179-4807-bd0c-3243dd6f1e25/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.3 Speed Mode — retained manufacturer figure 2" height="172.11581291759467" width="336">

Motor Speed Sine Test

1. Switch the control mode to speed mode.
2. The motor starts running and enters motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command will be planned according to the sine law.
4. Click Stop to stop the motor.

#### 3.4.4 Position Mode (PP) <a href="#block-33ad4c79856d818b84d7da86fc7bea08" id="block-33ad4c79856d818b84d7da86fc7bea08"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0ba4a66c-7552-43ac-aad9-2dc7ba2af0dc/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.4 Position Mode (PP) — retained manufacturer figure 1" height="464.25" width="336">

1. Switch the control mode to interpolation position mode.
2. Start the motor and enter motor\_mode.
3. First, set the speed and acceleration. If not set, the motor will operate at the default values. Finally, set the position command (target position). The motor will follow the command.
4. Set the speed to 0 to stop the motor at the current position. To continue operation, re-issue the speed and position.
5. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bb4c3b10-2dcc-49ee-a548-5c2306e2307d/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.4 Position Mode (PP) — retained manufacturer figure 2" height="170.24" width="336">

Motor Position Sine Test

1. Switch the control mode to interpolation position mode.
2. Start the motor and enter motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command will be planned according to the sine law.
4. Click Stop to stop the motor.

#### 3.4.5 Location Mode (CSP) <a href="#block-33ad4c79856d81b8aebdcd79986515fc" id="block-33ad4c79856d81b8aebdcd79986515fc"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9695776f-918b-4032-8339-ed4f6f48a105/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.5 Location Mode (CSP) — retained manufacturer figure 1" height="471.7808219178082" width="336">

1. Switch the control mode to position mode.
2. The motor starts running and enters motor\_mode.
3. Set the speed first. If no speed setting is made, the motor will run at the default value. Finally, set the position command (target position). The motor will follow the command.
4. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8645a7f3-4c56-4499-bcd8-c8e727e4d994/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 3.4.5 Location Mode (CSP) — retained manufacturer figure 2" height="170.25" width="336">

Motor position sinusoidal test

1. Switch the control mode to position mode.
2. The motor starts running and enters motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command is then sinusoidally planned.
4. Click Stop to stop the motor.

### 4. Driver protocol and instructions <a href="#block-33ad4c79856d8145bb5fed0fa1cc1726" id="block-33ad4c79856d8145bb5fed0fa1cc1726"></a>

The motor communication is the CAN 2.0 communication interface, the baud rate is 1 Mbps, and the extended frame format is adopted as follows:

| data field  | 29-bit ID          |             |                     | 8Byte data field |
| ----------- | ------------------ | ----------- | ------------------- | ---------------- |
| Size        | Bit28\~bit24       | bit23\~8    | bit7\~0             | Byte0\~Byte7     |
| Description | Communication type | data area 2 | Destination address | data area 1      |

The control modes supported by the motor include:

* Operation control mode: set 5 parameters of motor operation control;
* Current mode: the specified Iq current of the given motor;
* Velocity mode: the specified running speed of the given motor;
* Position mode: Given the specified position of the motor, the motor will run to the specified position;

#### 4.1 Description of the communication protocol type <a href="#block-33ad4c79856d81dabdf4d8605021517b" id="block-33ad4c79856d81dabdf4d8605021517b"></a>

The following command tables describe the classical private protocol in [this exact model’s dated manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf). All byte offsets start at zero. A command number written as decimal (for example Type 17) differs from its hexadecimal value (`0x11`).

#### 4.1.1 Communication type 0: Get device ID <a href="#block-33ad4c79856d815c9bb8c75cf66f559a" id="block-33ad4c79856d815c9bb8c75cf66f559a"></a>

Gets the device's ID and 64-bit MCU unique identifier

| data field  | 29-bit ID    |                                   |                      | 8Byte data field |
| ----------- | ------------ | --------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                          | bit7\~0              | Byte0\~Byte7     |
| Description | 0x0          | bit15\~8: identifies host CAN\_ID | target motor CAN\_ID | 0                |

Response frame:

| data field  | 29-bit ID    |                      |         | 8Byte data field             |
| ----------- | ------------ | -------------------- | ------- | ---------------------------- |
| Size        | Bit28\~bit24 | bit23\~8             | bit7\~0 | Byte0\~Byte7                 |
| Description | 0x0          | target motor CAN\_ID | 0XFE    | 64-bit MCU unique identifier |

#### 4.1.2 Communication Type 1: operation control mode motor control instruction <a href="#block-33ad4c79856d8169a54fd1a5e71edab8" id="block-33ad4c79856d8169a54fd1a5e71edab8"></a>

| Location               | Field                  | Encoding / model range              |
| ---------------------- | ---------------------- | ----------------------------------- |
| Extended ID bits 28–24 | Type                   | 1                                   |
| Extended ID bits 23–8  | Feedforward torque     | uint16, −17 to +17 N·m              |
| Extended ID bits 7–0   | Destination            | Motor CAN ID                        |
| Data bytes 0–1         | Target output angle    | uint16 big-endian, −4π to +4π rad   |
| Data bytes 2–3         | Target output velocity | uint16 big-endian, −44 to +44 rad/s |
| Data bytes 4–5         | Kp                     | uint16 big-endian, 0 to 500         |
| Data bytes 6–7         | Kd                     | uint16 big-endian, 0 to 5           |

Each 16-bit field uses codes 0–65535. A bounded affine encoder is `round((x − xmin) × 65535 / (xmax − xmin))` after clamping; use one defined rounding convention consistently. Torque occupies the identifier’s **16-bit data area**, not one payload byte. Select motion mode and establish the fixture/limits before enabling with Type 3; Type 1 then returns Type 2 telemetry. [RS02-IP67User Manual260713.pdf: §4.1 Type 1](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### Communication Type 2: motor feedback data <a href="#block-33ad4c79856d81e895a0e91b4d4aa40b" id="block-33ad4c79856d81e895a0e91b4d4aa40b"></a>

| Location               | Meaning                                                                                                                      |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Extended ID bits 28–24 | 2 (decimal)                                                                                                                  |
| ID bits 15–8 / 7–0     | Source motor ID / destination host ID for Type 2; the Type 24 reply destination label is inconsistent in the manual          |
| ID bits 21–16          | Fault flags: 21 uncalibrated, 20 stall overload, 19 encoder fault, 18 overtemperature, 17 phase overcurrent, 16 undervoltage |
| ID bits 23–22          | 0 reset, 1 calibration, 2 running                                                                                            |
| Data bytes 0–1         | uint16 big-endian angle: −4π to +4π rad                                                                                      |
| Data bytes 2–3         | uint16 big-endian velocity: −44 to +44 rad/s                                                                                 |
| Data bytes 4–5         | uint16 big-endian torque: −17 to +17 N·m                                                                                     |
| Data bytes 6–7         | uint16 big-endian temperature ×10; divide by 10 for °C                                                                       |

The manual repeats the bit-20 label in places; it does not define a second independent bit 20. Record the raw identifier together with the decoded flags. [RS02-IP67User Manual260713.pdf: §4.1 Type 2 / Type 24](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.3 Communication Type 3: Motor enabled to run <a href="#block-33ad4c79856d81898bb1ce768fd2cf15" id="block-33ad4c79856d81898bb1ce768fd2cf15"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field |
| ----------- | ------------ | ------------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7     |
| Description | 0x3          | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID |                  |

Response frame: Response motor feedback frame (see communication type 2)

#### 4.1.4 Communication Type 4: Motor stops running <a href="#block-33ad4c79856d81509ff2ef3c9f325fc2" id="block-33ad4c79856d81509ff2ef3c9f325fc2"></a>

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                           |
| ----------- | ------------ | ------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                               |
| Description | 0x4          | bit15\~8: used to identify the main CAN\_ID | target motor CAN\_ID | When the motor is running normally, 0 must be cleared in the data field. Byte\[0]=1: The fault is cleared. |

Response frame: Response motor feedback frame (see communication type2)

For an ordinary stop, all eight payload bytes are zero; byte 0 = 1 requests fault clearing. Clearing a bit does not remove its electrical/thermal cause. This stop command shares Type 4 with the distinct `00 C4` version-query signature described below; do not confuse the two payloads. [Private stop/clear table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.5 Communication type 6: Set motor mechanical zero <a href="#block-33ad4c79856d81adb217d4d1a3488d47" id="block-33ad4c79856d81adb217d4d1a3488d47"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field |
| ----------- | ------------ | ------------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7     |
| Description | 0x6          | bit15\~8: Identifies the main CAN\_ID | target motor CAN\_ID | Byte\[0]=1       |

Response frame: Response motor feedback frame (see communication type2)

#### Communication type 7: Set motor CAN\_ID <a href="#block-33ad4c79856d81e78b4eecbf71b7aa71" id="block-33ad4c79856d81e78b4eecbf71b7aa71"></a>

Change the current motor CAN\_ID, effective immediately.

| data field  | 29-bit ID    |                                                                           |                      | 8Byte data field |
| ----------- | ------------ | ------------------------------------------------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                                                                  | bit7\~0              | Byte0\~Byte7     |
| Description | 0x7          | **bit15\~8**: used to identify main CAN\_ID **Bit16\~23**: preset CAN\_ID | target motor CAN\_ID |                  |

Response frame: Answer motor broadcast frame (see communication type 0)

The new motor ID occupies **identifier bits 23–16**; host ID remains in bits 15–8 and the old motor ID is the destination low byte. The command takes effect immediately and responds with the device-ID/MCU-identifier frame. Update the recorded node map before sending further commands; one shared identifier must not address multiple enabled motors. [Type 7 definition](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.6 Communication type 17: Single parameter read <a href="#block-33ad4c79856d8125badaec289c7648c7" id="block-33ad4c79856d8125badaec289c7648c7"></a>

| Direction / location     | Exact field                                                |
| ------------------------ | ---------------------------------------------------------- |
| Request extended ID      | `(17 << 24) \| (host_id << 8) \| motor_id`                 |
| Request bytes 0–1        | Parameter index, uint16 little-endian                      |
| Request bytes 2–7        | All zero                                                   |
| Reply ID bits 28–24      | 17                                                         |
| Reply ID bits 15–8 / 7–0 | Source motor ID / destination host ID                      |
| Reply ID bits 23–16      | 0x00 success; 0x01 read failure                            |
| Reply bytes 0–1 / 2–3    | Echoed index / reserved zeros                              |
| Reply bytes 4–7          | Typed parameter value, little-endian for multi-byte fields |

The general reply table in the PDF has merged columns and mislabels the source as the master. Its worked `loc_kp` example establishes the actual direction: request `0x1100FD7F`, response `0x11007FFD`. A reader must require the expected extended/data frame, DLC 8, type, motor source, host destination, success byte and echoed index before decoding. Reject a nonzero status byte rather than interpreting an error payload as a float. [RS02-IP67User Manual260713.pdf: §4.1 single-parameter read and worked example](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.7 Communication type 18: Single parameter write (lost in power failure) <a href="#block-33ad4c79856d81ae989dfd0c18574aeb" id="block-33ad4c79856d81ae989dfd0c18574aeb"></a>

With type 22, the parameter starting with function code 0x20 of the parameter table in the upper computer module can be saved

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                                                                                                                                |
| ----------- | ------------ | ------------------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                                                                                                                                    |
| Description | 0x12         | bit15\~8: Used to identify the main CAN\_ID | target motor CAN\_ID | **Byte0\~1**: index. For details, see the read ability parameter table below **Byte2\~3**: 00 **Byte4\~7**: Parameter data In the preceding data, the low byte is in the front and the high byte is in the rear |

Response frame: Response motor feedback frame (see communication type2)

#### 4.1.8 Communication type 21: Fault feedback frame <a href="#block-33ad4c79856d81ac9bdaff847790ee03" id="block-33ad4c79856d81ac9bdaff847790ee03"></a>

| data field  | 29-bit ID    |                         |                             | 8Byte data field                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ----------- | ------------ | ----------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Size        | Bit28\~bit24 | bit23\~8                | bit7\~0                     | Byte0\~Byte7                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Description | 0x15         | bit15\~8: motor CAN\_ID | identifies the main CAN\_ID | **Byte0\~3**: fault value (non-0: faulty; 0: normal) **Bit 16**: A-phase current sampling overcurrent **Bit 14**: Motor stall overload algorithm protection **Bit 9**: Position initialization fault **Bit 8**: Hardware identification fault **Bit 7**: Encoder uncalibrated: Motor encoder not calibrated **Bit 5**: C-phase current sampling overcurrent **Bit 4**: B-phase current sampling overcurrent **bit 3**: overvoltage fault **bit 2**: undervoltage fault **bit 1**: driver chip fault **bit 0**: motor overtemperature fault, Default 135 °C **Byte4\~7**: warning Value **bit 0**: motor overtemperature warning, the default is 135 °C |

The payload contains a 32-bit fault word in bytes 0–3 and a separate 32-bit warning word in bytes 4–7. Zero means no active bits. Do not reuse the compact Type 2 identifier flags as this payload’s bit positions. The table specifies the words and bit numbers but does not unambiguously state their multi-byte byte order; retain raw bytes and confirm firmware packing before constructing a universal word decoder. [RS02-IP67User Manual260713.pdf: §4.1 Type 21](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf). The Type 21 fault threshold is 135 °C, while the thermal/board chapters use 145 °C. This is an unresolved source-context difference, not permission to raise a cutoff.

#### 4.1.9 Communication type 22: Motor data save frame <a href="#block-33ad4c79856d81379517ee547ca7c3fb" id="block-33ad4c79856d81379517ee547ca7c3fb"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field        |
| ----------- | ------------ | ------------------------------------- | -------------------- | ----------------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7            |
| Description | 0x16         | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 07 08 |

Response frame: Response motor feedback frame (see communication type2)

#### 4.1.10 Communication type 23: Motor baud rate modification frame (re-power-on effect) <a href="#block-33ad4c79856d8116abcbe14b8f3ea715" id="block-33ad4c79856d8116abcbe14b8f3ea715"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field                                                                                                                  |
| ----------- | ------------ | ------------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7                                                                                                                      |
| Description | 0x17         | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 F\_CMD Among them, the F\_CMD byte is the motor baud rate Among them, 01 is 1M 02 is 500K 03 is 250K 04 is 125K |

Response frame: Response motor feedback frame (see communication type0)

The table names a nominal 8-byte data field but lists only bytes 0–6. Byte 7 is not specified here; do not fabricate it from another protocol. Match the exact firmware/host-tool transaction before issuing this configuration write. A bitrate/protocol change takes effect after power cycling; reconnect using the selected protocol and timing. [RS02-IP67User Manual260713.pdf: Type 23](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.11 Communication type 24: The motor actively reports frames <a href="#block-33ad4c79856d81ab87c7dd97380e3b18" id="block-33ad4c79856d81ab87c7dd97380e3b18"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field                                                                                                                                                                                      |
| ----------- | ------------ | ------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7                                                                                                                                                                                          |
| Description | 0x18         | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 F\_CMD Among them, the F\_CMD byte is the motor reporting switch 00 is to disable active reporting (default) 01 To enable active reporting, the default reporting interval is 10 ms |

Response frame layout (as labelled Type 24 in its table):

| Location               | Meaning                                                                                                                      |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Extended ID bits 28–24 | 24 (decimal)                                                                                                                 |
| ID bits 15–8 / 7–0     | Source motor ID / destination host ID for Type 2; the Type 24 reply destination label is inconsistent in the manual          |
| ID bits 21–16          | Fault flags: 21 uncalibrated, 20 stall overload, 19 encoder fault, 18 overtemperature, 17 phase overcurrent, 16 undervoltage |
| ID bits 23–22          | 0 reset, 1 calibration, 2 running                                                                                            |
| Data bytes 0–1         | uint16 big-endian angle: −4π to +4π rad                                                                                      |
| Data bytes 2–3         | uint16 big-endian velocity: −44 to +44 rad/s                                                                                 |
| Data bytes 4–5         | uint16 big-endian torque: −17 to +17 N·m                                                                                     |
| Data bytes 6–7         | uint16 big-endian temperature ×10; divide by 10 for °C                                                                       |

The manual repeats the bit-20 label in places; it does not define a second independent bit 20. Record the raw identifier together with the decoded flags. [RS02-IP67User Manual260713.pdf: §4.1 Type 2 / Type 24](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf). The function chapter instead describes active reports as Type 2. Preserve this source discrepancy when implementing filters: capture the returned type on the installed firmware, then validate its routing and payload; do not accept every identifier merely to receive data. The control table lists seven payload octets (`01 02 03 04 05 06 F_CMD`) under an 8-byte header and leaves byte 7 unspecified. Use the matched host tool or firmware implementation to resolve the eighth byte before automating this write. [RS02-IP67User Manual260713.pdf: Type 24 versus active-report function](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.12 Communication type 25: Motor protocol modification frame (re-power-on effect) <a href="#block-33ad4c79856d8141a5c0f7f4c8147c86" id="block-33ad4c79856d8141a5c0f7f4c8147c86"></a>

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                                                                                             |
| ----------- | ------------ | ------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                                                                                                 |
| Description | 0x19         | bit15\~8: used to identify the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 F\_CMD Among them, the F\_CMD byte is themotor protocol type Among them, 0 is a private protocol (default) 1 is the Canopen protocol 2 is the MIT protocol |

Response frame: Response motor feedback frame (see communication type0)

The table names a nominal 8-byte data field but lists only bytes 0–6. Byte 7 is not specified here; do not fabricate it from another protocol. Match the exact firmware/host-tool transaction before issuing this configuration write. A bitrate/protocol change takes effect after power cycling; reconnect using the selected protocol and timing. [RS02-IP67User Manual260713.pdf: Type 25](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.1.13 Communication type 26：Version number read frame <a href="#block-33ad4c79856d819aa6e0d38d7d3333e2" id="block-33ad4c79856d819aa6e0d38d7d3333e2"></a>

| Field              | Version-query transaction                                                                       |
| ------------------ | ----------------------------------------------------------------------------------------------- |
| Request            | Extended Type 4: `(4 << 24) \| (host_id << 8) \| motor_id`                                      |
| Request payload    | `00 C4 00 00 00 00 00 00`                                                                       |
| Response type      | Type 2 in the selected dated manual                                                             |
| Response signature | bytes 0–2: `00 C4 56`                                                                           |
| Version bytes      | bytes 3–6, most-significant component first                                                     |
| Response ID status | Source motor in bits 15–8; status flags in bits 23–16; source destination label is inconsistent |

**Legacy title correction:** “type 26” was the old section title, but its own request table used `0x04`. The selected PDF calls this a version read frame, sent under **Type 4**, with a Type 2 response. Do not send decimal 26 based on the heading, and do not decode the `00 C4 56` version payload as ordinary angle/velocity telemetry. The request also shares Type 4 with stop/clear; select the documented signature exactly. [RS02-IP67User Manual260713.pdf: version-number read frame adjacent to Type 3/4](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### Private-CAN typed parameter list

| Wire index | Field            | Purpose                                                                | Type   | Bytes | Published range / default          | Access |
| ---------- | ---------------- | ---------------------------------------------------------------------- | ------ | ----- | ---------------------------------- | ------ |
| `0x7005`   | `run_mode`       | Operating mode: 0 impedance/motion; 1 PP; 2 velocity; 3 current; 5 CSP | uint8  | 1     | —                                  | W/R    |
| `0x7006`   | `iq_ref`         | Current mode Iq command                                                | float  | 4     | -16 to 16 A                        | W/R    |
| `0x700A`   | `spd_ref`        | Rotational Velocity mode Rotational speed command                      | float  | 4     | -33 to 33 rad/s                    | W/R    |
| `0x700B`   | `limit_torque`   | torque limit                                                           | float  | 4     | 0 to 14 N·m                        | W/R    |
| `0x7010`   | `cur_kp`         | Kp                                                                     | float  | 4     | The default value is 0.17          | W/R    |
| `0x7011`   | `cur_ki`         | Ki                                                                     | float  | 4     | The default value is 0.012         | W/R    |
| `0x7014`   | `cur_filt_gain`  | filt gain                                                              | float  | 4     | 0 to 1.0, The default value is 0.1 | W/R    |
| `0x7016`   | `loc_ref`        | Position Mode Angle instruction                                        | float  | 4     | rad                                | W/R    |
| `0x7017`   | `limit_spd`      | Location mode (CSP) speed limit                                        | float  | 4     | 0 to 33 rad/s                      | W/R    |
| `0x7018`   | `limit_cur`      | Velocity position mode Current limitation                              | float  | 4     | 0 to 16 A                          | W/R    |
| `0x7019`   | `mechPos`        | Mechanical Angle of the loading coil                                   | float  | 4     | rad                                | R      |
| `0x701A`   | `iqf`            | iq Filter                                                              | float  | 4     | -16 to 16 A                        | R      |
| `0x701B`   | `mechVel`        | Speed of the load                                                      | float  | 4     | -33 to 33 rad/s                    | R      |
| `0x701C`   | `VBUS`           | Bus voltage                                                            | float  | 4     | V                                  | R      |
| `0x701E`   | `loc_kp`         | Position-loop gain; name confirmed by worked read example              | float  | 4     | The default value is 40            | W/R    |
| `0x701F`   | `spd_kp`         | Indicates the speed kp                                                 | float  | 4     | The default value is 6             | W/R    |
| `0x7020`   | `spd_ki`         | ki                                                                     | float  | 4     | The default value is 0.02          | W/R    |
| `0x7021`   | `spd_filt_gain`  | Speed filter value                                                     | float  | 4     | The default value is 0.1           | W/R    |
| `0x7022`   | `acc_rad`        | velocity mode acceleration                                             | float  | 4     | The default value is 20 rad/s²     | W/R    |
| `0x7024`   | `vel_max`        | Location mode (PP) speed                                               | float  | 4     | The default value is 10 rad/s      | W/R    |
| `0x7025`   | `acc_set`        | Location mode (PP) acceleration                                        | float  | 4     | The default value is 10 rad/s²     | W/R    |
| `0x7026`   | `EPScan_time`    | Active-report interval: 1 → 10 ms; each increment adds 5 ms            | uint16 | 2     | The default value is 1             | W/R    |
| `0x7028`   | `canTimeout`     | Communication watchdog: 20000 → 1 s; 0 disables                        | uint32 | 4     | The default value is 0             | W/R    |
| `0x7029`   | `zero_sta`       | Power-on angle interval: 0 → 0 to 2π; 1 → −π to π                      | uint8  | 1     | The default is 0                   | W/R    |
| `0x702A`   | `damper`         | Damping switch                                                         | uint8  | 1     | The default value is 0             | W/R    |
| `0x702B`   | `add_offset`     | Zero offset                                                            | float  | 4     | The default is 0                   | W/R    |
| `0x702C`   | `alveolous_open` | Cogging compensation switch                                            | uint8  | 1     | The default is 0                   | W/R    |
| `0x702D`   | `iq_test`        | Initialization calibration switch                                      | uint8  | 1     | The default is 0                   | W/R    |
| `0x702E`   | `dcc_set`        | Separate PP deceleration; controlled by acc\_stutus                    | float  | 4     | The default is 10 rad/s²           | W/R    |

[Exact-model private parameter table, PDF pp. 49–51](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=49). Multi-byte index and typed value are little-endian; data occupy bytes 4–7 with unused bytes zeroed. `R` means read-only, `W` means write-only in this dated table, and `W/R` means both. The source’s garbled run-mode line is resolved by the actual current-mode procedure (`run_mode = 3`); it does not establish a current mode 4. The `loc_kp` name is resolved by the worked `0x701E` read. The displayed defaults must not overwrite an existing tuned drive without checking its firmware and readback.

**Conflicting limits within this manual:** the float-write list prints ±16 A for `iq_ref`/`iqf`, ±33 rad/s for `spd_ref`/`mechVel`, 0–16 A for `limit_cur`, and 0–14 N·m for `limit_torque`. The same model’s electrical table gives 23 A maximum phase current, while Type 1/2 and MIT use ±44 rad/s and ±17 N·m. These are different published encodings with an unresolved revision discrepancy; the table above preserves the float-interface values rather than substituting the packed-interface limits. Confirm the installed firmware’s float-write limits with RobStride before using those writes. Read-only voltage/position/velocity acquisition does not depend on a torque/current write.

#### 4.1.14 Read example <a href="#block-33ad4c79856d813e8700ff3028c70334" id="block-33ad4c79856d813e8700ff3028c70334"></a>

| Direction              | Extended CAN ID | Payload                   | Decoded meaning                                   |
| ---------------------- | --------------- | ------------------------- | ------------------------------------------------- |
| Host 0xFD → motor 0x7F | `0x1100FD7F`    | `1E 70 00 00 00 00 00 00` | Type 17, read index 0x701E                        |
| Motor 0x7F → host 0xFD | `0x11007FFD`    | `1E 70 00 00 00 00 F0 41` | Success; little-endian float `00 00 F0 41` = 30.0 |

The number 30.0 is the manual’s example observation, not the installed motor’s guaranteed gain; the same PDF may list a different default elsewhere. [RS02-IP67User Manual260713.pdf: worked loc\_kp read example](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.2 Motor Function Description <a href="#block-33ad4c79856d81039a79e2425ec31a6b" id="block-33ad4c79856d81039a79e2425ec31a6b"></a>

_(If the following features are unavailable, please upgrade to the latest version via the official Git repository.)_

#### 4.2.1 Active Reporting <a href="#block-33ad4c79856d819e8ca5df6e0dcf9435" id="block-33ad4c79856d819e8ca5df6e0dcf9435"></a>

* **Disabled by default**. Enable via **Type 24**.
* Report type: **Type 2** (default interval:\*\* 10 ms\*\*). Adjust interval by modifying EPScan\_time via **Type 18**.

#### 4.2.2 Zero-Point Flag (zero\_sta) <a href="#block-33ad4c79856d810c8877f2c2ba447606" id="block-33ad4c79856d810c8877f2c2ba447606"></a>

* Modify via:
* **Host computer (software)**
* **Type 18** _(requires saving via **Type 22** for communication)_
* **Default flag**: 0 → Power-on position range:\*\* 0–2π\*\*.
* **If set to 1**: Power-on position range:\*\* −π to π\*\*.

The signed interval is also stated by wire parameter `0x7029`. Save a supported changed setting with Type 22 when persistence is required. [RS02-IP67User Manual260713.pdf: zero\_sta function and parameter table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.2.3 Type 2 Update <a href="#block-33ad4c79856d810ebfdfda109715d6d1" id="block-33ad4c79856d810ebfdfda109715d6d1"></a>

* Updated to **periodic looping within -4π–4π** (enables cycle counting).
* **Note**: Position interface parameters must be adjusted:
* P\_MIN: **-12.57f**
* P\_MAX: **12.57f**

The function-note macro is printed with a positive `P_MIN` in some dated PDFs. That would give a zero span. The Type 1/2 table and signed program sample establish the intended −12.57 to +12.57 rad endpoints; do not use equal endpoints. [RS02-IP67User Manual260713.pdf: Type2 update and Type1/2 angle range](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.2.4 Protocol Switching (Requires CAN adapter) <a href="#block-33ad4c79856d81b08a1cfdccc18407ba" id="block-33ad4c79856d81b08a1cfdccc18407ba"></a>

* Methods:
* Modify protocol\_1 via host computer.
* Send **Type 25** command.
* **Reboot required** after switching.
* **Post-switch CAN commands:**
* **CANopen**: Send extended frame (protocol switch frame).
* **MIT Protocol**: Send standard frame (**Command 8**).

#### 4.2.5 Post-Power-Off Anti-Backdrive Protection <a href="#block-33ad4c79856d810c80abc2f217eba862" id="block-33ad4c79856d810c80abc2f217eba862"></a>

* **Default**: Motor imposes damping if rotated rapidly while powered off (prevents surge).
* Disable: Set damper = 1.

This is generated-voltage damping/protection, not a holding brake. The function chapter names `damper = 1` to disable it; the parameter table maps it to `0x702A`. [RS02-IP67User Manual260713.pdf: post-power-off protection](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.2.6 Zero Calibration Rules <a href="#block-33ad4c79856d813abeead2efaded888e" id="block-33ad4c79856d813abeead2efaded888e"></a>

* **Supported modes: CSP** and **Motion Control**.
* **PP Mode**: Zero calibration is **blocked**.
* **Old vs. New Versions**:
* **Old**: Zero calibration causes large deviation → motor immediately moves to target
* **New (CSP/Motion Control)**: Target updates to 0 instantly → motor remains stationary.

#### 4.2.7 Position Offset (add\_offset) <a href="#block-33ad4c79856d81d089a1fcdff49acd22" id="block-33ad4c79856d81d089a1fcdff49acd22"></a>

`add_offset` is a position-reference offset in rad, not a request to move the joint or a way to change a physical hard stop. The manual’s example shifts the **previous zero reference** by 1 rad when `add_offset = 1`; the reference is applied after a power cycle. It does not mean “current shaft position plus 1 rad” every time the field is written. Retain the measured zero, `zero_sta` convention and physical sign in the joint map, and verify the resulting readback in an unloaded fixture before later enabling. The wire list maps it to float `0x702B`; save supported settings with Type 22 when persistence is required. [Dated position-offset function](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.2.8 CANopen ID <a href="#block-33ad4c79856d81abaaded94119ffb3fd" id="block-33ad4c79856d81abaaded94119ffb3fd"></a>

* **Old version**: Fixed to 1.
* **New version**: Matches the **private protocol CAN ID**.

#### 4.2.9 Notes for Implementation <a href="#block-33ad4c79856d813e974bf2101dbb8d19" id="block-33ad4c79856d813e974bf2101dbb8d19"></a>

* Always **save settings** (e.g., Type 22 for zero\_sta).
* Verify **CAN adapter compatibility** for protocol switching.
* For zero offsets, ensure mechanical safety limits are respected.

#### 4.3 Control mode instructions <a href="#block-33ad4c79856d814c9b7aeebd46d741fd" id="block-33ad4c79856d814c9b7aeebd46d741fd"></a>

#### 4.3.1 Operation control mode <a href="#block-33ad4c79856d81a5a61ac21834af0ae6" id="block-33ad4c79856d81a5a61ac21834af0ae6"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/34dd5fa7-ae19-40e3-a173-f6e81e763515/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 4.3.1 Operation control mode — retained manufacturer figure 1" height="608" width="2582">

The motor is in operation control mode by default after power-on.

Send motor Enable Run frame (communication type 3) --> Send operation mode motor control command (communication type 1) --> Receive motor feedback frame (communication type 2)

Operation control mode description: The control logic of the operation and control mode is t\_ref=Kd \* (v\_vset-v\_actual)+Kp \* (p\_set-p\_actual)+t\_ff. Tref is converted to the expected iq current through an internal formula and output through the current loop Simple control demonstration: Set t\_ff to 0, v\_vset to 1, Kd to 1, p\_set to 0, Kp to 0. If there is no external load on the motor, it will run at a speed of 1 rad/s. If there is an external load, kd needs to be increased to resist the external load Set t\_ff to 0, v\_vset to 0, Kd to 1, p\_set to 0, Kp to 0, the motor is in damping mode. When the motor is externally rotated, a damping is applied, which increases with the increase of kd. It should be noted that the motor generates electricity under this condition and requires power supply to prevent overvoltage Set t\_ff to 0, v\_vset to 0, Kd to 1, p\_set to 5, Kp to 1. If there is no external load on the motor, it will run to the target position of 5. Increasing kp will increase the force required to maintain the target position, and kd is damping. Without kd, the motor will sway to the target position

Before the enable step, secure the unloaded actuator, remove links, read its position/identity, set a reachable nearby target and deliberately chosen current/torque limits, and provide a stop path. The 1 rad/s damping example and 5 rad position example illustrate the equation; they are not universal first-motion settings for a mounted mechanism. [RS02-IP67User Manual260713.pdf: motion-control mode](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.3.2 Current mode <a href="#block-33ad4c79856d8160b1a8d47bdfa30f82" id="block-33ad4c79856d8160b1a8d47bdfa30f82"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1959b9c2-fc2f-45c2-b317-796093a41b6b/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 4.3.2 Current mode — retained manufacturer figure 1" height="722" width="2474">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 3 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set the iq\_ref parameter to the default current instruction

Use byte-sized `run_mode = 3` at `0x7005`, then Type 3 enable, then a float current command at `0x7006` (`iq_ref`, A). The wire table’s current range and the mechanical continuous-load rating serve different purposes. Choose an unloaded fixture and an application current cap; current control does not hold position against gravity. [Current-mode sequence](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.3.3 Velocity mode <a href="#block-33ad4c79856d81d4ade6f1164b317331" id="block-33ad4c79856d81d4ade6f1164b317331"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a19898ea-15a6-42e4-a571-e30ca122c741/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 4.3.3 Velocity mode — retained manufacturer figure 1" height="524" width="2576">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 2 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set limit\_cur parameter as default maximum current instruction-->Send motor mode parameter write command (communication type 18) Set acc\_rad parameter as default acceleration instruction --> Send motor mode parameter write command (communication type 18) Set spd\_ref parameter as default speed instruction

The target is float `spd_ref` at `0x700A` in rad/s; `limit_cur` (`0x7018`) is A and `acc_rad` (`0x7022`) is rad/s². Configure `run_mode = 2` before enable. The source’s diagram enables before setting limits; for a controlled integration, preload applicable limits and a zero/known target in the stopped state where supported, then deliberately enable and check feedback. Do not inherit unknown defaults as an application limit. [Velocity sequence and typed parameter table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.3.4 Location Mode (CSP) <a href="#block-33ad4c79856d81b1828cfb0e13b37a84" id="block-33ad4c79856d81b1828cfb0e13b37a84"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/39753d84-20fa-4f01-93a1-e8b7e7017569/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 4.3.4 Location Mode (CSP) — retained manufacturer figure 1" height="464" width="2592">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 5 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set limit\_spd parameter as default maximum speed instruction -->Send motor mode parameter write command (communication type 18) Sets loc\_ref parameter as default position instruction

CSP uses `run_mode = 5`, float speed cap `limit_spd` (`0x7017`, rad/s), and float target `loc_ref` (`0x7016`, rad). These private indices and mode number are distinct from the CANopen objects below. Read the current output position and choose a nearby reachable target before enabling a mechanism. [CSP procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.3.5 Location Mode (PP) <a href="#block-33ad4c79856d818db6b5daac4c5ba181" id="block-33ad4c79856d818db6b5daac4c5ba181"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7a59549c-7803-4ed5-acd3-60b14c7346e2/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 4.3.5 Location Mode (PP) — retained manufacturer figure 1" height="554" width="2562">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 1 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set The vel\_max parameter is the default maximum speed instruction--> Send motor mode parameter write command (communication type 18) Set the acc\_set parameter to the default acceleration instruction -->Send motor mode parameter write command (communication type 18) Set the loc\_ref parameter to the default position instruction

**Note: This mode does not support changing the speed and acceleration during operation. If you want to make an emergency stop, you can change vel\_max to 0 during the process, and it will stop at the current speed and acceleration plan**

PP uses `run_mode = 1`, `vel_max` (`0x7024`, rad/s), `acc_set` (`0x7025`, rad/s²), and `loc_ref` (`0x7016`, rad). The source’s “set vel\_max to 0” is a planned stop through its profile, not a guaranteed zero-time emergency stop; Type 4 is the explicit drive stop transaction. The separate deceleration feature and its firmware-dependent flag are described in the added function reference. [PP procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.3.6 Stop running <a href="#block-33ad4c79856d81e8812bc99b704bc757" id="block-33ad4c79856d81e8812bc99b704bc757"></a>

Sending motor stop frame (communication type 4)

#### 4.4 Program sample <a href="#block-33ad4c79856d81db8c54c63ec93d9716" id="block-33ad4c79856d81db8c54c63ec93d9716"></a>

Examples of various mode control motors are provided below (take GD32F303 as an example)

The following are library, function, and macro definitions for the various instances

```cpp
#define P_MIN -12.57f
#define P_MAX 12.57f
#define V_MIN -44.0f
#define V_MAX 44.0f
#define KP_MIN 0.0f
#define KP_MAX 500.0f
#define KD_MIN 0.0f
#define KD_MAX 5.0f
#define T_MIN -17.0f
#define T_MAX 17.0f

struct exCanIdInfo {
  uint32_t id:8;
  uint32_t data:16;
	uint32_t mode:5;
  uint32_t res:3;
};

can_receive_message_struct rxMsg;
can_trasnmit_message_struct txMsg = {
  .tx_sfid = 0,
  .tx_efid = 0xff,
  .tx_ft = CAN_FT_DATA,
  .tx_ff = CAN_FF_EXTENDED,
  .tx_dlen = 8, 
};

#define txCanIdEx (*((struct exCanIdInfo*)&(txMsg.tx_efid)))
#define rxCanIdEx (*((struct exCanIdInfo*)&(rxMsg.rx_efid))) //Parses the extended frame id into a custom data structure

int float_to_uint(float x, float x_min, float x_max, int bits) {
  float span = x_max - x_min;
  float offset = x_min;
  if(x > x_max) x = x_max;
  else if(x < x_min) x = x_min;
  return (int) ((x-offset)*((float)((1<<bits)-1))/span);
}

#define can_txd() can_message_transmit(CAN0, &txMsg)
#define can_rxd() can_message_receive(CAN0, CAN_FIFO1, &rxMsg)
```

The following lists the common types of communication sent:

**Model and code correction:** these retained GD32F303 integration fragments now use this model’s Type 1 ranges. Earlier snippets contained RS00 scales and equal positive velocity endpoints; the latter cause division by zero in `float_to_uint`. The source’s signed range tables, not an equal-endpoint macro, define the physical bounds. This is partial vendor-HAL integration code: initialize clocks/CAN/filters and provide the GD32 headers, types and context before building it. C bitfield layout and aliasing are compiler-dependent; verify the actual extended identifier against the explicit ID tables or replace the overlay with masks/shifts in a port. Compilation and hardware execution were not run. [RS02-IP67User Manual260713.pdf: Type1 range table and program sample](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.4.1 Motor Enabled Run frame (communication type 3) <a href="#block-33ad4c79856d8145bf42f36ee35c79b3" id="block-33ad4c79856d8145bf42f36ee35c79b3"></a>

```cpp
void motor_enable(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 3;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for (uint8_t i = 0; i < 8; ++i) txMsg.tx_data[i] = 0;
  can_txd();
}
```

The final initialization clears the **payload**, preserving `master_id` in the identifier. The earlier transcription wrote `txCanIdEx.data = 0` a second time, erasing the host address instead. Match the Type 3 identifier and eight zero data bytes before transmission. [RS02-IP67User Manual260713.pdf: Type3 enable frame and program sample](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 4.4.2 Operation control mode Motor control instruction (communication type 1) <a href="#block-33ad4c79856d81eca45ecc937c36d07e" id="block-33ad4c79856d81eca45ecc937c36d07e"></a>

```cpp
void motor_controlmode(uint8_t id, float torque, float MechPosition, float
speed, float kp, float kd) {
  txCanIdEx.mode = 1;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = float_to_uint(torque,T_MIN,T_MAX,16);
  txMsg.tx_dlen = 8;
  txMsg.tx_data[0]=float_to_uint(MechPosition,P_MIN,P_MAX,16)>>8;
  txMsg.tx_data[1]=float_to_uint(MechPosition,P_MIN,P_MAX,16);
  txMsg.tx_data[2]=float_to_uint(speed,V_MIN,V_MAX,16)>>8;
  txMsg.tx_data[3]=float_to_uint(speed,V_MIN,V_MAX,16);
  txMsg.tx_data[4]=float_to_uint(kp,KP_MIN,KP_MAX,16)>>8;
  txMsg.tx_data[5]=float_to_uint(kp,KP_MIN,KP_MAX,16);
  txMsg.tx_data[6]=float_to_uint(kd,KD_MIN,KD_MAX,16)>>8;
  txMsg.tx_data[7]=float_to_uint(kd,KD_MIN,KD_MAX,16);
  can_txd();
}
```

#### 4.4.3 Motor stop frame (communication type 4) <a href="#block-33ad4c79856d81a993c0fb7560ae9c4d" id="block-33ad4c79856d81a993c0fb7560ae9c4d"></a>

```cpp
void motor_reset(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 4;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for(uint8_t i=0; i<8; i++) {
    txMsg.tx_data[i]=0;
  }
  can_txd();
}
```

#### 4.4.4 Motor mode parameter write command (communication type 18, running mode switch) <a href="#block-33ad4c79856d81f59af3ec2e17050eab" id="block-33ad4c79856d81f59af3ec2e17050eab"></a>

```cpp
uint8_t runmode;
uint16_t parameter_index;
void motor_modechange(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 0x12;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for(uint8_t i=0; i<8; i++) {
    txMsg.tx_data[i] = 0;
  }
  memcpy(&txMsg.tx_data[0], &parameter_index, 2);
  memcpy(&txMsg.tx_data[4], &runmode, 1);
  can_txd();
}
```

#### 4.4.5 Motor mode parameter write command (communication type 18, control parameter write) <a href="#block-33ad4c79856d8140beb7c79e8c0d24ea" id="block-33ad4c79856d8140beb7c79e8c0d24ea"></a>

```cpp
uint16_t parameter_index;
float ref;
void motor_write(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 0x12;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for(uint8_t i=0;i<8;i++) {
    txMsg.tx_data[i]=0;
  }
  memcpy(&txMsg.tx_data[0],&parameter_index,2);
  memcpy(&txMsg.tx_data[4],&ref,4);
  can_txd();
}
```

### 5. Explanation of Canopen Communication Protocol Types <a href="#block-33ad4c79856d81dfa8e6e44d01eeec31" id="block-33ad4c79856d81dfa8e6e44d01eeec31"></a>

#### 5.1 Introduction to CANopen Communication <a href="#block-33ad4c79856d819ab91dc0ac243ee230" id="block-33ad4c79856d819ab91dc0ac243ee230"></a>

CANopen is a "higher-level protocol" based on the CAN bus. This means that the CAN bus (ISO 11898) acts like a container truck, serving as the "transportation vehicle" for CANopen information. CAN simply implements the transmission of frames with an 11-bit CAN ID, a Remote Transmission (RTR) bit, and 64 data bits (related to higher-level protocols). The CAN bus plays the same role in CANopen as it does in the J1939 protocol. CANopen implements Layer 7 of the OSI model and is compatible with other data link layer protocols besides CAN. Please download the necessary EDS files for CANopen from the official website download center at [www.robstride.com](http://www.robstride.com/).

#### 5.2 Canopen Protocol Message Classification <a href="#block-33ad4c79856d8138a295df72d1943394" id="block-33ad4c79856d8138a295df72d1943394"></a>

| Classification                     | Function                                                                                                                                                                                                                                                                                                    |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NMT Network Management Messages    | Manage the network and switch node states. NMT network management messages are typically sent by the master station                                                                                                                                                                                         |
| SDO Service Data Object Message    | Used for setting device parameters or transmitting critical data. Typically, the master station initiates an SDO message, and the slave station responds. However, a slave station can also initiate an SDO message, with the master station responding, for example, in the transmission of critical data. |
| PDO (Process Data Object) messages | Transmit process data from various devices, such as temperature and speed. Both the master and slave stations send these messages.                                                                                                                                                                          |
| EMCY Emergency Message             | Transmits fault information about the transmission equipment. Both the master and slave stations send this message.                                                                                                                                                                                         |
| SYNC Synchronization Message       | Synchronization data, used to synchronize TPDO data on the slave station. Generally sent by the master station.                                                                                                                                                                                             |
| NODE GUARDING Message              | The master station requests the slave station's status; the master station queries, and the slave station responds.                                                                                                                                                                                         |
| Heartbeat Message                  | A device actively sends a heartbeat to indicate that it is online. Both the master and slave devices can send heartbeats.                                                                                                                                                                                   |

#### Official EDS routing and PDO schema (26 August 2024)

The official repository also contains `driver_v1.1.eds`, whose internal file name is `motor.eds`, creation/modification date is 26 August 2024, and product string is generic **CAN Drive Rev1.0**. It declares four receive and four transmit PDOs. Those declarations describe this file; they do not identify the installed ROBSTRIDE02-IP67 firmware or establish that its defaults match the 2026 manual. Import it only after checking identity/revision readback.

| Object / subindex             | File-declared purpose / default                                                        |
| ----------------------------- | -------------------------------------------------------------------------------------- |
| `0x1200:01`, `0x1200:02`      | Client→server SDO ID `0x600 + node`; server→client `0x580 + node`                      |
| `0x1014`                      | Emergency COB-ID `0x80 + node`                                                         |
| `0x1016`, `0x1017`            | Consumer heartbeat parameters / producer heartbeat time                                |
| `0x100C`, `0x100D`            | Guard time / life-time factor                                                          |
| `0x1400`–`0x1403`, subindex 1 | RPDO COB-IDs: node + `0x200`, `0x300`, `0x400`, `0x500`                                |
| `0x1800`–`0x1803`, subindex 1 | TPDO COB-IDs: node + `0x180`, `0x280`, `0x380`, `0x480`                                |
| PDO communication subindex 2  | Transmission type, unsigned 8-bit; file default 0                                      |
| TPDO subindices 3 / 5         | Inhibit time / event timer, unsigned 16-bit; file defaults 0                           |
| `0x1600`–`0x1603`             | Receive mapping records; subindex 0 is entry count; subindices 1–8 are 32-bit mappings |
| `0x1A00`–`0x1A03`             | Transmit mapping records with the same mapping-entry structure                         |

Each mapping word encodes `index << 16 | subindex << 8 | bit_length`. In the file, RPDO1’s first two nonzero words are `0x60400010` (controlword, 16 bits) and `0x607A0020` (target position, 32 bits); TPDO1 starts with statusword and displayed mode. The file prints entry count 8 even where later mapping words are zero, and the other PDO maps are zero placeholders. Read the live count and mappings before choosing a DLC or interpreting byte offsets; the EDS alone does not prove an active eight-entry map.

The 2026 motor manual repurposes `0x6099:01` as the CAN watchdog, while the older generic EDS calls it a homing search speed. Use the exact motor manual and firmware confirmation for that object; do not push a generic homing configuration into it. Read-only commissioning in this guide uses private CAN and does not import an EDS or remap PDOs. [Official dated EDS](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/canopen/driver_v1.1.eds).

#### 5.3 State Machine Description <a href="#block-33ad4c79856d81cca9f3e5e1ef7d7db7" id="block-33ad4c79856d81cca9f3e5e1ef7d7db7"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/48518d23-ee01-42f7-b334-e40407d69dab/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 5.3 State Machine Description — retained manufacturer figure 1" height="961.4701378254211" width="720">

**Motor Enable:**

When initially powered on, the motor defaults to the **SWITCH\_ON\_DISABLED** state. To transition to **OPERATION\_ENABLE**, modify the **Controlword(6040H)** to **6, 7, or 15** (step-by-step transition), or directly set it to **15** for immediate enablement.

**Stopping the Motor:**

If the motor is in **OPERATION\_ENABLE** state and needs to stop normally, modify the **Controlword (6040H)** to **1**. The motor will return to the disabled state (**SWITCH\_ON\_DISABLED**).

**Emergency Stop (Use with Caution—Risk of Voltage Surge):**

During operation, an emergency stop can be triggered by setting the **Controlword (6040H)** to **11**.

**Fault Clearance:**

If the motor enters a **FAULT** state due to protection mechanisms, modifying the **Controlword (6040H)** can clear standard errors.

**Important Note:**

Mode changes for this motor must be performed in the **disabled state** (**SWITCH\_ON\_DISABLED**). Ensure the desired mode is configured **before** enabling **OPERATION\_ENABLE** to avoid unexpected behavior.

The dated manual also places the CANopen watchdog at object `0x6099`, subindex 1: raw 20000 means 1 s, and zero disables it. A timeout disables the motor. This is a CANopen object, not private wire index `0x7028`. The chapter does not supply an exact fault-reset controlword value, so do not turn “modify Controlword” into a fabricated reset packet. [RS02-IP67User Manual260713.pdf: CiA402 state machine/watchdog](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 5.4 Status Feedback Parameters <a href="#block-33ad4c79856d81d597dee558886a8663" id="block-33ad4c79856d81d597dee558886a8663"></a>

| **Index** | **Name**                      | **Attribute** | **Type**   | **Unit**                       |
| --------- | ----------------------------- | ------------- | ---------- | ------------------------------ |
| 603F      | Error\_code                   | Read-only     | UINTEGER16 | /                              |
| 6041      | Statusword                    | Read-only     | UINTEGER16 | /                              |
| 6061      | Modes\_of\_operation\_display | Read-only     | INTEGER8   | /                              |
| 6062      | Position\_demand\_value       | Read-only     | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 6064      | Position\_actual\_value       | Read-only     | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 606B      | Velocity\_demand\_value       | Read-only     | INTEGER32  | 0.1 rpm                        |
| 606C      | Velocity\_actual\_value       | Read-only     | INTEGER32  | 0.1 rpm                        |
| 6077      | Torque\_actual\_value         | Read-only     | INTEGER16  | 0.1% load ratio (1000 = 6 N·m) |
| 6078      | Current\_actual\_value        | Read-only     | INTEGER16  | mA                             |
| 6079      | DC\_link\_circuit\_voltage    | Read-only     | INTEGER32  | mV                             |

#### 5.5 Homing Mode (Zero Position Setting) <a href="#block-33ad4c79856d8153ac75fb69c5cf0a83" id="block-33ad4c79856d8153ac75fb69c5cf0a83"></a>

| **Index** | **Name**           | **Attribute** | **Type**   | **Unit** |
| --------- | ------------------ | ------------- | ---------- | -------- |
| 6040      | Controlword        | Read-write    | UINTEGER16 | /        |
| 6060      | Modes of operation | Read-write    | INTEGER8   | /        |

**Homing method:**

* Set **Modes of operation to 6** while the motor is in the **disabled state (SWITCH\_ON\_DISABLED)**. The motor will then define the current position as the zero point.
* To **hold the zero position**, modify the **Controlword to 15**, and the motor will maintain its position at the home location.

#### 5.6 Position Mode (PP - Profile Position) <a href="#block-33ad4c79856d81b29133c69abf300844" id="block-33ad4c79856d81b29133c69abf300844"></a>

| **Index** | **Name**               | **Attribute** | **Type**   | **Unit**                       |
| --------- | ---------------------- | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword            | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation     | Read-write    | INTEGER8   | /                              |
| 6067      | Position\_window       | Read-write    | UINTEGER32 | Pulses (1 rev =16,384 pulses)  |
| 6068      | Position\_window\_time | Read-write    | UINTEGER16 | ms                             |
| 6071      | Target\_torque         | Read-write    | INTEGER16  | 0.1% load ratio (1000 = 6 N·m) |
| 607A      | Target\_position       | Read-write    | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 6081      | Profile\_velocity      | Read-write    | UINTEGER32 | 0.1 rpm                        |
| 6083      | Profile\_acceleration  | Read-write    | UINTEGER32 | 0.1 rpm/s                      |

**Steps to Configure Position Mode (PP):**

1. While the motor is in the **disabled state** (**SWITCH\_ON\_DISABLED**), set **Modes of operation to 1**.
2. **Mandatory parameters:**
3. **Target\_torque** (absolute max torque in position mode)
4. **Profile\_velocity** (absolute speed in position mode)
5. **Profile\_acceleration** (absolute acceleration in position mode)
6. **Optional parameters:**
7. **Position\_window** (if not set, window check is disabled)
8. **Position\_window\_time** (if not set, window check is disabled)
9. Set **Controlword (6040) to 15** to enable operation.
10. Set **Target\_position (absolute position)** to move the motor to the desired position.

#### 5.7 Position Mode (CSP - Cyclic Synchronous Position) <a href="#block-33ad4c79856d8198a274f4018a31e725" id="block-33ad4c79856d8198a274f4018a31e725"></a>

| **Index** | **Name**               | **Attribute** | **Type**   | **Unit**                       |
| --------- | ---------------------- | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword            | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation     | Read-write    | INTEGER8   | /                              |
| 6067      | Position\_window       | Read-write    | UINTEGER32 | Pulses (1 rev =16,384 pulses)  |
| 6068      | Position\_window\_time | Read-write    | UINTEGER16 | ms                             |
| 6071      | Target\_torque         | Read-write    | INTEGER16  | 0.1% load ratio (1000 = 6 N·m) |
| 607A      | Target\_position       | Read-write    | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 6081      | Profile\_velocity      | Read-write    | UINTEGER32 | 0.1 rpm                        |

**Steps to Configure Position Mode (CSP):**

1. While the motor is in the disabled state (SWITCH\_ON\_DISABLED), set Modes of operation to 5.
2. **Mandatory parameters:**
3. **Target\_torque** (absolute max torque in position mode)
4. **Profile\_velocity** (absolute speed in position mode)
5. **Optional parameters:**
6. **Position\_window** (0 = disabled)
7. **Position\_window\_time** (0 = disabled)
8. Set **Controlword (6040) to 15** to enable operation.
9. **Set Target\_position** (absolute position) to move the motor to the desired position.

#### 5.8 Velocity Mode <a href="#block-33ad4c79856d81739019cc02a64201e3" id="block-33ad4c79856d81739019cc02a64201e3"></a>

| **Index** | **Name**           | **Attribute** | **Type**   | **Unit**                       |
| --------- | ------------------ | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword        | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation | Read-write    | INTEGER8   | /                              |
| 6071      | Target\_torque     | Read-write    | INTEGER16  | 0.1% load ratio (1000 = 6 N·m) |
| 60FF      | Target\_velocity   | Read-write    | INTEGER32  | 0.1 rpm                        |

**Steps to Configure Velocity Mode:**

1. While the motor is in the **disabled state (SWITCH\_ON\_DISABLED)**, set **Modes of operation to 3**.
2. **Mandatory parameter:**
3. **Target\_torque** (absolute max torque in velocity mode)
4. Set **Controlword (6040) to 15** to enable operation.
5. **Set Target\_velocity** to reach the desired speed.

#### 5.9 Torque Mode <a href="#block-33ad4c79856d8158bc3ee3e2f3c66d86" id="block-33ad4c79856d8158bc3ee3e2f3c66d86"></a>

| **Index** | **Name**           | **Attribute** | **Type**   | **Unit**                       |
| --------- | ------------------ | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword        | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation | Read-write    | INTEGER8   | /                              |
| 6071      | Target\_torque     | Read-write    | INTEGER16  | 0.1% load ratio (1000 = 6 N·m) |

**Steps to Configure Torque Mode:**

1. While the motor is in the **disabled state (SWITCH\_ON\_DISABLED)**, set **Modes of operation to 4**.
2. Set **Controlword (6040) to 15** to enable operation.
3. **Set Target\_torque** to output the desired torque.

#### 5.10 Protocol Switching (Extended Frame): SwitchMotor Protocol (Takes Effect After Power Cycle) <a href="#block-33ad4c79856d8121995cf288ae54926d" id="block-33ad4c79856d8121995cf288ae54926d"></a>

| Data Field  | 29-bit ID | 8-Byte Data Area         |
| ----------- | --------- | ------------------------ |
| Size        | Bit 28\~0 | Byte 0\~6                |
| Description | 0xFFF     | 01 02 03 04 05 06 F\_CMD |

* **F\_CMD** (Byte 6) defines the motor protocol:
* **0:** Private protocol (default)
* **1:** CANopen protocol
* **2:** MIT protocol

**Response Frame:**

| Data Field  | 11-bit ID | 8-Byte Data Area             |
| ----------- | --------- | ---------------------------- |
| Size        | Bit 10\~0 | Byte 0\~7                    |
| Description | Motor ID  | 64-bit MCU unique identifier |

This is the special **extended-ID `0xFFF`** switch transaction, despite CANopen normally using standard identifiers. It lists bytes 0–6 and leaves the eighth byte unspecified under its 8-byte heading. Do not turn it into an ordinary 11-bit `0xFFF` frame (outside the 11-bit range), or guess missing data from a private/MIT command. [RS02-IP67User Manual260713.pdf: CANopen protocol switch](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

### 6. MIT Communication Protocol Description <a href="#block-33ad4c79856d81759646e9262754d667" id="block-33ad4c79856d81759646e9262754d667"></a>

The motor communication adopts the CAN 2.0 interface with a default baud rate of 1 Mbps. The baud rate can be modified by switching to the private protocol. The standard frame format is as follows:

| Data Field  | 11-bit ID |          | 8-byte Data Area |
| ----------- | --------- | -------- | ---------------- |
| Size        | Bit 10\~8 | Bit 7\~0 | Byte 0\~7        |
| Description | Mode type | ID       |                  |

Supported Control Modes:

* **MIT Mode**: Provides five motion control parameters to the motor.
* **Velocity Mode**: Specifies the target speed for the motor.
* **Position Mode**: Specifies the target position and speed, allowing the motor to run to the designated position at the configured speed.

The standard-ID commands, response fields and procedures below are from [the exact-model MIT chapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf). They do not use CANopen torque ratios or private-CAN extended identifiers.

#### 6.1 Response Command 1: Data Feedback(Motor Status) <a href="#block-33ad4c79856d81b29b48f43f78803dcf" id="block-33ad4c79856d81b29b48f43f78803dcf"></a>

| Location                      | Feedback field / decoding                                  |
| ----------------------------- | ---------------------------------------------------------- |
| Standard CAN ID               | Host ID                                                    |
| Byte 0                        | Source motor ID                                            |
| Bytes 1–2                     | Unsigned 16-bit angle, big-endian; −12.57 to +12.57 rad    |
| Byte 3 and byte 4 high nibble | Unsigned 12-bit velocity; −44 to +44 rad/s                 |
| Byte 4 low nibble and byte 5  | Unsigned 12-bit torque; −17 to +17 N·m                     |
| Byte 6 high two bits          | Mode: 0 reset, 1 calibration, 2 running                    |
| Byte 6 bit 5 / bit 4          | Fault-present / warning-present                            |
| Byte 6 low nibble and byte 7  | 12-bit temperature ×10; `((b6 & 0x0F) << 8 \| b7) / 10` °C |

The manual labels 12-bit code ranges “0–4096”, although a 12-bit field can contain only 0–4095. Keep the transmitted field width distinct from the conversion denominator; confirm the installed firmware’s quantizer before commanding an endpoint. The 16-bit angle field uses codes 0–65535. [RS02-IP67User Manual260713.pdf: MIT data-feedback table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 6.2 Response Command 2: MCU Identification <a href="#block-33ad4c79856d81c19c58f6fbd92653d5" id="block-33ad4c79856d81c19c58f6fbd92653d5"></a>

| Data Field  | 11-bit ID | 8-byte Data Area             |
| ----------- | --------- | ---------------------------- |
| Size        | Bit 10\~0 | Byte 0\~7                    |
| Description | Motor ID  | 64-bit MCU unique identifier |

#### 6.3 Command 1: Enable Motor Operation <a href="#block-33ad4c79856d81ea8cceda3d93b18ddc" id="block-33ad4c79856d81ea8cceda3d93b18ddc"></a>

| Data Field  | 11-bit ID           | 8-byte Data Area        |
| ----------- | ------------------- | ----------------------- |
| Size        | Bit 10\~0           | Byte 0\~7               |
| Description | Target motor CAN ID | FF FF FF FF FF FF FF FC |

**Response**: Response Command 1

#### 6.4 Command 2: Stop Motor Operation <a href="#block-33ad4c79856d819ca86dd5314e5c89b2" id="block-33ad4c79856d819ca86dd5314e5c89b2"></a>

| Data Field  | 11-bit ID           | 8-byte Data Area        |
| ----------- | ------------------- | ----------------------- |
| Size        | Bit 10\~0           | Byte 0\~7               |
| Description | Target motor CAN ID | FF FF FF FF FF FF FF FD |

**Response**: Response Command 1

#### 6.5 Command 3: MIT Dynamic Parameters <a href="#block-33ad4c79856d81e382b0d30d54706136" id="block-33ad4c79856d81e382b0d30d54706136"></a>

| Data location               | Command field                       | Physical range       |
| --------------------------- | ----------------------------------- | -------------------- |
| Bytes 0–1                   | Angle, unsigned 16-bit big-endian   | −12.57 to +12.57 rad |
| Byte 2 + byte 3 high nibble | Velocity, unsigned 12-bit           | −44 to +44 rad/s     |
| Byte 3 low nibble + byte 4  | Kp, unsigned 12-bit                 | 0 to 500             |
| Byte 5 + byte 6 high nibble | Kd, unsigned 12-bit                 | 0 to 5               |
| Byte 6 low nibble + byte 7  | Feedforward torque, unsigned 12-bit | −17 to +17 N·m       |

Send to the target motor’s standard ID in MIT motion mode; response is the status feedback defined above. The packed 12-bit values occupy 0–4095, while the manual’s printed 0–4096 endpoint is an arithmetic inconsistency. Do not reuse the private Type 1 sixteen-bit gain/velocity encoder for these fields. The all-zero payload printed in the manual is a field-layout example: in a signed affine encoding it represents the negative endpoints, **not a zero-motion command**. [RS02-IP67User Manual260713.pdf: MIT dynamic parameters](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 6.6 Command 4: Set Zero Position (Non-Position Mode) <a href="#block-33ad4c79856d816a959afc868c0bd372" id="block-33ad4c79856d816a959afc868c0bd372"></a>

| Data Field  | 11-bit ID           | 8-byte Data Area        |
| ----------- | ------------------- | ----------------------- |
| Size        | Bit 10\~0           | Byte 0\~7               |
| Description | Target motor CAN ID | FF FF FF FF FF FF FF FE |

**Response**: Response Command 1

#### 6.7 Command 5: Clear Errors \&Read Fault Status <a href="#block-33ad4c79856d81b8babacb90c21737c4" id="block-33ad4c79856d81b8babacb90c21737c4"></a>

| Field                    | Content                                                          | Meaning                                                              |
| ------------------------ | ---------------------------------------------------------------- | -------------------------------------------------------------------- |
| Standard CAN ID (11-bit) | Destination motor CAN ID                                         | Command group 0; send to the motor’s current ID                      |
| Data bytes 0–5           | `FF FF FF FF FF FF`                                              | Six-byte special-command prefix                                      |
| Data byte 6              | `F_CMD`                                                          | 0xFF clears the active fault; any other value queries the fault word |
| Data byte 7              | `FB`                                                             | Special-command terminator                                           |
| Complete data shape      | `FF FF FF FF FF FF F_CMD FB`                                     | Eight bytes total                                                    |
| Response                 | Status feedback for clear; detailed fault-status reply for query | Select the correct response layout, not a locally echoed request     |

**Response (Fault Clear)**: Response Command 1

**Fault Status Response:**

| Response field                 | Value / interpretation                                                                                          |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| Standard CAN ID                | Host CAN ID; source example is `0xFD`                                                                           |
| Data byte 0                    | Source motor CAN ID                                                                                             |
| Data bytes 1–4                 | 32-bit fault word; zero normal, nonzero active faults; word byte order not explicitly established               |
| Fault bits 16 / 14 / 9 / 8 / 7 | A-phase overcurrent / stall-overload / position initialization / hardware identification / encoder uncalibrated |
| Fault bits 5 / 4 / 3 / 2 / 1   | C-phase overcurrent / B-phase overcurrent / overvoltage / undervoltage / driver-chip fault                      |
| Fault bit 0                    | Motor overtemperature; dated MIT table threshold 135 °C                                                         |
| Data bytes 5–7                 | No additional field meaning assigned by the source fault-status table; retain raw bytes                         |

The detailed fault response is on the host standard ID: byte 0 identifies the motor and bytes 1–4 carry the fault word (zero normal). Bits 16/14/9/8/7/5/4/3/2/1/0 mean A-phase overcurrent, stall overload, position-initialization fault, hardware-identification fault, uncalibrated encoder, C-phase overcurrent, B-phase overcurrent, overvoltage, undervoltage, driver fault and motor overtemperature. This is separate from the ordinary status response. The prose’s “byte 1” shorthand does not reduce the detailed four-byte field to one byte. Its word byte order is not explicitly established by that table; confirm from firmware/raw capture before converting it to an integer. [RS02-IP67User Manual260713.pdf: MIT clear/query and detailed fault-status response](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

[RS02-IP67User Manual260713.pdf: MIT command 5](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=75).

For example, a query with `F_CMD = 00` is `FF FF FF FF FF FF 00 FB`; clearing with `F_CMD = FF` is `FF FF FF FF FF FF FF FB`. The query result’s four-byte field is distinct from ordinary MIT angle/velocity feedback.

#### 6.8 Command 6: Set Operation Mode <a href="#block-33ad4c79856d8105ae27c163998664ed" id="block-33ad4c79856d8105ae27c163998664ed"></a>

| Field                    | Content                              | Meaning                                                          |
| ------------------------ | ------------------------------------ | ---------------------------------------------------------------- |
| Standard CAN ID (11-bit) | Destination motor CAN ID             | Command group 0; send to the motor’s current ID                  |
| Data bytes 0–5           | `FF FF FF FF FF FF`                  | Six-byte special-command prefix                                  |
| Data byte 6              | `F_CMD`                              | 0 selects MIT motion (default); 1 position; 2 velocity           |
| Data byte 7              | `FC`                                 | Special-command terminator                                       |
| Complete data shape      | `FF FF FF FF FF FF F_CMD FC`         | Eight bytes total                                                |
| Response                 | Status feedback (Response Command 1) | Select the correct response layout, not a locally echoed request |

**Response**: Response Command 1

[RS02-IP67User Manual260713.pdf: MIT command 6](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=76).

The mode-select packet for motion uses byte 6 = `00`; enable uses byte 6 = `FF`. Both end in `FC`, so the last byte alone does not identify the action. Stop before a mode change.

#### 6.9 Command 7: Modify Motor CAN ID <a href="#block-33ad4c79856d81ce9ea8e90704dc6679" id="block-33ad4c79856d81ce9ea8e90704dc6679"></a>

| Field                    | Content                           | Meaning                                                          |
| ------------------------ | --------------------------------- | ---------------------------------------------------------------- |
| Standard CAN ID (11-bit) | Destination motor CAN ID          | Command group 0; send to the motor’s current ID                  |
| Data bytes 0–5           | `FF FF FF FF FF FF`               | Six-byte special-command prefix                                  |
| Data byte 6              | `F_CMD`                           | New motor CAN ID                                                 |
| Data byte 7              | `FA`                              | Special-command terminator                                       |
| Complete data shape      | `FF FF FF FF FF FF F_CMD FA`      | Eight bytes total                                                |
| Response                 | MCU identity (Response Command 2) | Select the correct response layout, not a locally echoed request |

**Response**: Response Command 2

[RS02-IP67User Manual260713.pdf: MIT command 7](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=76).

#### 6.10 Command 8: Change Communication Protocol (Takes Effect After Power Cycle) <a href="#block-33ad4c79856d81b1b0bbeeb16324dad7" id="block-33ad4c79856d81b1b0bbeeb16324dad7"></a>

| Field                    | Content                           | Meaning                                                          |
| ------------------------ | --------------------------------- | ---------------------------------------------------------------- |
| Standard CAN ID (11-bit) | Destination motor CAN ID          | Command group 0; send to the motor’s current ID                  |
| Data bytes 0–5           | `FF FF FF FF FF FF`               | Six-byte special-command prefix                                  |
| Data byte 6              | `F_CMD`                           | 0 private; 1 CANopen; 2 MIT; effective after power cycle         |
| Data byte 7              | `FD`                              | Special-command terminator                                       |
| Complete data shape      | `FF FF FF FF FF FF F_CMD FD`      | Eight bytes total                                                |
| Response                 | MCU identity (Response Command 2) | Select the correct response layout, not a locally echoed request |

**Response**: Response Command 2

[RS02-IP67User Manual260713.pdf: MIT command 8](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=76).

An ordinary MIT stop has byte 6 = `FF` and byte 7 = `FD`; a switch to the private protocol uses byte 6 = `00` and byte 7 = `FD`. The protocol switch requires power cycling.

#### 6.11 Command 9: Modify Host CAN ID <a href="#block-33ad4c79856d81cd965dc763126ed516" id="block-33ad4c79856d81cd965dc763126ed516"></a>

| Field                    | Content                           | Meaning                                                          |
| ------------------------ | --------------------------------- | ---------------------------------------------------------------- |
| Standard CAN ID (11-bit) | Destination motor CAN ID          | Command group 0; send to the motor’s current ID                  |
| Data bytes 0–5           | `FF FF FF FF FF FF`               | Six-byte special-command prefix                                  |
| Data byte 6              | `F_CMD`                           | New host CAN ID                                                  |
| Data byte 7              | `01`                              | Special-command terminator                                       |
| Complete data shape      | `FF FF FF FF FF FF F_CMD 01`      | Eight bytes total                                                |
| Response                 | MCU identity (Response Command 2) | Select the correct response layout, not a locally echoed request |

**Response**: Response Command 2

[RS02-IP67User Manual260713.pdf: MIT command 9](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf#page=77).

#### 6.12 Command 10: Position Mode Control Command <a href="#block-33ad4c79856d81558260d6f7708a6201" id="block-33ad4c79856d81558260d6f7708a6201"></a>

| Data Field  | 11-bit ID |                     | 8-byte Data Area                                                                                     |
| ----------- | --------- | ------------------- | ---------------------------------------------------------------------------------------------------- |
| Size        | Bit 10\~8 | Bit 7\~0            | **Byte 0\~3**: Target position (rad, 32-bit float) **Byte 4\~7**: Target speed (rad/s, 32-bit float) |
| Description | 1         | Target motor CAN ID | Target motor CAN ID                                                                                  |

**Response**: Response Command 1

Use standard ID `(1 << 8) | motor_id`. Payload bytes 0–3 are little-endian IEEE-754 position in rad, and bytes 4–7 are little-endian IEEE-754 speed in rad/s. The PDF example `00 00 A0 40 00 00 A0 40` means position 5 rad and speed 5 rad/s; it establishes byte order, not a suitable first target. Select MIT position mode (mode byte 1), enable deliberately, then send a reachable target; stop with the documented stop command. [RS02-IP67User Manual260713.pdf: MIT position command and mode procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 6.13 Command 11: Velocity Mode Control Command <a href="#block-33ad4c79856d81cf9be4f75c56c9926f" id="block-33ad4c79856d81cf9be4f75c56c9926f"></a>

| Data Field  | 11-bit ID |                     | 8-byte Data Area                                                                                                        |
| ----------- | --------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit 10\~8 | Bit 7\~0            | **Byte 0\~3**: Target speed (rad/s, 32-bit float) **Byte 4\~7**: Current limit in speed/position mode (A, 32-bit float) |
| Description | 2         | Target motor CAN ID | Target motor CAN ID                                                                                                     |

**Response**: Response Command 1

Use standard ID `(2 << 8) | motor_id`. Bytes 0–3 are little-endian IEEE-754 rad/s; bytes 4–7 are the current limit in A. The source example `00 00 A0 40 00 00 00 40` decodes as 5 rad/s and 2 A. Configure mode byte 2 before enabling; choose an appropriate current cap and stop path before commanding velocity. [RS02-IP67User Manual260713.pdf: MIT velocity command and mode procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### 6.14 Motion Control Mode <a href="#block-33ad4c79856d81f184d2d883436f0163" id="block-33ad4c79856d81f184d2d883436f0163"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3f91e610-4eb3-447e-ad66-11452905aa86/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 6.14 Motion Control Mode — retained manufacturer figure 1" height="568" width="2526">

The motor defaults to Motion Control Mode upon power-up.

1. Send the _Motor Enable Command_ (Command 1).
2. Send the _Motion Control Command_ (Command 3) to activate dynamic parameter control.
3. Send the _Motor Stop Command_ (Command 2) to halt operation when needed.

#### 6.15 Velocity Mode <a href="#block-33ad4c79856d81c1bcbce73a4d512d22" id="block-33ad4c79856d81c1bcbce73a4d512d22"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/25f04a1b-775a-4cd5-a24e-1cf738021636/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 6.15 Velocity Mode — retained manufacturer figure 1" height="528" width="2514">

1. Configure the motor's operation mode by sending _Set Operation Mode Command_ (Command 6) with **Mode = 2 (Velocity Mode).**
2. Send the _Motor Enable Command_ (Command 1) to activate the motor.
3. Send the _Velocity Mode Control Command_ (Command 11) to set the **maximum current (absolute value)** and **target speed**.
4. To stop, send the _Motor Stop Command_ (Command 2).

#### 6.16 Position Mode (CSP - Cyclic Synchronous Position) <a href="#block-33ad4c79856d816a84bae88c9c6be50c" id="block-33ad4c79856d816a84bae88c9c6be50c"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6bc2d8f3-920c-4ac1-81ef-6db4de105119/image/w=1920,quality=90,fit=scale-down" alt="ROBSTRIDE02-IP67 — 6.16 Position Mode (CSP - Cyclic Synchronous Position) — retained manufacturer figure 1" height="489.99999999999994" width="2586">

1. Configure the motor's operation mode by sending Set _Operation Mode Command_ (Command 6) with **Mode = 1 (Position Mode)**.
2. Send the _Motor Enable Command_ (Command 1) to activate the motor.
3. Send the _Position Mode Control Command_ (Command 10) to set the **maximum speed (absolute value)** and **target position**.
4. To stop, send the _Motor Stop Command_ (Command 2).

#### Initialization, cogging calibration and separate PP deceleration

`iq_test = 1` extends initialization to improve its reference. For documented cogging calibration, set that flag, restart with the actuator unloaded, run the host-tool cogging calibration, and confirm `max_alve` becomes nonzero. Set `alveolous_open = 1` to apply compensation in motion-control mode. These are calibration/state changes; keep the fixture unloaded and do not run them as a connection test. The wire table maps the two switches to `0x702D` and `0x702C`.

For separate PP acceleration/deceleration, the source names `acc_stutus = 1` and deceleration at float index `0x702E` (`dcc_set`, rad/s²); when the flag is 0, the acceleration value controls both ramps. The manual does not give a private index for `acc_stutus` in its short wire list. Find the named field in the matching host/firmware rather than inventing an address. [RS02-IP67User Manual260713.pdf: motor-function calibration and PP deceleration](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).

#### MIT save, reporting and typed parameter extension

The selected ROBSTRIDE02-IP67 manual requires firmware **`0.2.3.32`** for these four MIT additions. This is a model-specific prerequisite, not evidence that the purchased unit already has that build. Verify its version before using the extension.

| Operation             | Standard CAN ID        | Eight-byte request                                          | Response / persistence                                                                 |
| --------------------- | ---------------------- | ----------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Save motor data       | `motor_id`             | `FF FF FF FF FF FF FF F8`                                   | MCU-identification response; saves supported motor data                                |
| Active reporting      | `motor_id`             | `FF FF FF FF FF FF F_CMD F9`                                | Status response; F\_CMD 0 off (default), 1 on                                          |
| Read typed parameter  | `(3 << 8) \| motor_id` | Index uint16 LE at 0–1; zeros at 2–7                        | Source shows reply on the same ID group with index/reserved/value fields               |
| Write typed parameter | `(4 << 8) \| motor_id` | Index uint16 LE at 0–1; zeros at 2–3; typed value LE at 4–7 | Source shows reply on the same ID group; explicitly save supported persistent settings |

The parameter indices/types are the private parameter list above. For motor `0x7F`, the manual’s read example is ID `0x37F`, payload `05 70 00 00 00 00 00 00`; the write example is ID `0x47F`, payload `29 70 00 00 00 00 00 00` (zero\_sta = 0). The latter changes an angle-reference setting. Because the printed read response uses the same ID and all-zero example as the request, a receive-own-message echo is not sufficient proof of a motor reply. Use the matched firmware implementation or a separately observed direction/source before treating that frame as confirmed readback. The main first-result script uses the better specified private Type 17 transaction instead. [RS02-IP67User Manual260713.pdf: MIT commands 12–15](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS02/RS02-IP67User%20Manual260713.pdf).
