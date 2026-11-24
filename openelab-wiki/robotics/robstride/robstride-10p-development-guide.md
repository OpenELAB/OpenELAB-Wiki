---
description: >-
  ROBSTRIDE10P wiring and first readback, classical-CAN/CANopen/MIT IDs and byte
  fields, 42 N·m scales, CAN-FD revision conflicts, calibration and recovery.
---

# RobStride 10P CAN and CAN-FD Engineering Guide

{% hint style="info" %}
[**View ROBSTRIDE10P joint motor on OpenELAB**](https://openelab.io/products/robstride-10p-qdd-joint-actuator)

**Model:** ROBSTRIDE10P · **SKU:** `ROBSTRIDE-10P` · **Option:** actuator module; host interface and system supply are separate · **Document:** RS10PUser Manual260907.pdf; classical CAN2.0 reference, not a CAN-FD image.
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

ROBSTRIDE10P integrates a brushless motor, reduction gear, encoder feedback and CAN drive. This guide takes one secured, unloaded actuator from verified wiring to **bus voltage, position and velocity readback without enabling torque**. Its 42 N·m headline is a peak output value; it is not continuous holding torque, power-supply current or a default controller limit. [Exact manufacturer manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf), [RobStride source library](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778).

The purchased motor option excludes the USB-CAN debugger. Use the [debug/power-board integration guide](robstride-debug-power-boards-development-guide.md) when selecting that accessory. A debug-board SKU sold on the same listing is a different item.

## Applications

Use ROBSTRIDE10P for an individually engineered robot joint, torque-controlled research mechanism or position/velocity test fixture. Determine the actual load envelope from torque–speed and overload curves, cooling, duty cycle, bearing loads and mechanism geometry before mounting a link. A high-ratio position loop and a five-parameter impedance loop have different response and fault behavior.

Start with one motor and a recorded identity. Later, assign unique CAN IDs and retain a physical-joint map, encoder sign, zero reference and firmware revision for each unit. Dual encoders do not establish permanent multi-turn retention, zero backlash or safe unpowered holding. The manual’s anti-backdrive feature concerns generated-voltage protection; it is not a rated holding brake. [Functions and operating modes, chapters 4–6](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

## Specifications

| Parameter                    | ROBSTRIDE10P dated-manual scope                                                                                |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Rated supply / working range | 48 V DC / 15–60 V for classical-CAN reference                                                                  |
| Rated output                 | 14 N·m at 50 rpm, with 210 × 210 mm heat sink in the classical-CAN manual                                      |
| Peak output torque           | 42 N·m; time/thermal limited                                                                                   |
| No-load speed                | 125 rpm ± 10%                                                                                                  |
| Reduction / mass             | 25:1 / 460 ± 3 g                                                                                               |
| Phase-current values         | 5.3 A peak-phase rated /19 A peak-phase maximum; not DC input current                                          |
| Torque-constant reference    | Not used for conversion here: classical-CAN and CAN-FD documents disagree; preserve RMS versus peak convention |
| Feedback                     | 14-bit absolute-turn driver reference; dual-encoder option                                                     |
| Bus                          | Classical CAN, 1 Mbit/s in the default private-protocol reference                                              |
| Environment                  | −20 to 50 °C; 5–85% RH, non-condensing                                                                         |

The sold listing specifies 1 Mbit/s CAN and the classical-CAN manual. The separate CAN-FD manual specifies 24–60 V, 5 Mbit/s in its driver table, a 100 rpm rated-load test and 9.5 N·m rated stall. Its torque-constant figure is 3.73 versus 7.73 N·m/A RMS in the classical document. These are not interchangeable control/calibration values. [Separate CAN-FD manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf). The first procedure uses 48 V, classical private-CAN status reads only; do not convert current to torque or select CAN-FD timing from this mixed evidence. [Motor/service/driver tables, chapters 1–2](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf). Regenerative deceleration or externally turning a motor can raise the DC bus. Choose supply absorption/discharge provisions from the complete system design; do not assume a bench supply can absorb returned energy.

## Hardware and connections

### Fixture, power and connector orientation

Use the exact STEP and thread-depth drawing. Keep fixing screws within the specified housing thread depth, maintain shaft/link clearance and support any gravity load before torque is removed. Power off before changing power or communication connectors.

The exact manual shows the **XT30(2+2) connector face**: VBAT+ is the left large power contact, GND the right large power contact; on the adjacent two signal contacts CAN-L is above CAN-H in that drawing. The board/line reference is XT30PB(2+2)-M.G.B /XT30(2+2)-F.G.B. A cable-side view is mirrored: compare the actual housing key and perform an unpowered continuity check. These contacts carry drive power and differential CAN, not TTL UART. Do not infer a service/SWD header from another model. [Chapter 2 connector diagrams](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

Use a twisted CAN pair and appropriate common-reference/isolation design. Put termination only at the physical bus ends; two 120 Ω ends normally measure approximately 60 Ω across an unpowered, fully connected pair. This is a wiring diagnostic, not a reason to add a resistor at every node. Verify adapter termination and board revision with power removed.

### Adapter mode is a separate choice

The documented RobStride debugger is a CH340- family **serial AT** adapter: serial packets start `41 54` and end `0D 0A`. On the documented board, DIP1 ON selects boot mode and prevents normal communication; DIP2 ON inserts 120 Ω. A serial port such as `/dev/ttyUSB0` is not a SocketCAN `can0` interface. The Linux example below requires a genuine SocketCAN-capable adapter, not a guessed serial framing bridge. [Host tool chapter 3](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

| Path                         | Exact interface and purpose                                                                                              |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Manufacturer host tool       | Matching USB-CAN serial adapter/CH340 driver; detect device, refresh/read parameters, export a baseline                  |
| Linux original example below | Python 3 standard-library SocketCAN; classical private protocol, 29-bit extended IDs, 8-byte data                        |
| CANopen                      | Separate protocol selection, EDS, CiA402 state machine and object units; do not send private frames to it                |
| MIT protocol                 | Separate standard-ID command packing, ranges and enable/disable behavior; not identical to private Type 1                |
| Firmware / OTA               | Exact 10P bus/hardware-revision build and matching updater; no named 10P binary identified in the reviewed model folders |

[Dated protocol and host-tool manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf), [official files at commit `9dcbce6df00b`](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778), [Linux SocketCAN interface](https://docs.kernel.org/networking/can.html). The repository contains the driver installer, OTA source and CANopen EDS; file presence does not prove compatibility with another hardware revision. No vendor SDK installation or updater execution is claimed here.

### Protocol scales and revision traps

The following values are checked against **RS10PUser Manual260907.pdf**, rather than inherited from an older page. These are wire-format ranges, not permitted operating demands. A revision-matched decoder may use them only after identifying the fitted firmware. The first-result script bypasses packed-command scaling and reads floats.

| Private Type 1/Type 2 item | Dated ROBSTRIDE10P reference                                                                                                                     |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Type 1 torque              | ID bits 23–8 contain a 16-bit unsigned value covering −42 to +42 N·m; this field spans two bytes, despite the source’s misleading “Byte 2” label |
| Type 1 payload             | bytes 0–1 angle; 2–3 velocity; 4–5 Kp; 6–7 Kd; each is unsigned 16-bit, high byte first                                                          |
| Angle range                | −4π to +4π rad; sample macros approximate the endpoints as −12.57/+12.57; firmware history changes the earlier ± 12.5 convention                 |
| Velocity range             | −13 to +13 rad/s                                                                                                                                 |
| Type 1 gain ranges         | Kp 0–500; Kd 0–5; do not substitute another motor’s gains                                                                                        |
| Type 2 payload             | bytes 0–1 angle, 2–3 velocity, 4–5 torque use the same 16-bit big-endian ranges; bytes 6–7 are temperature in tenths of °C                       |
| Type 2 routing             | source motor in ID bits 15–8; destination host bits 7–0; bits 22–23 report mode, bits 16–21 report faults                                        |

The exact manual’s sample code has a velocity-macro typo: `V_MIN` and `V_MAX` are both printed as +13.0. Copying those equal endpoints creates a zero mapping span. The Type 1/Type 2 control table establishes **−13 to +13 rad/s**; do not paste the erroneous velocity macros. The read-only float script does not use those macros.

For a 16-bit range `[a,b]`, the wire endpoint codes are 0 and 65535, so the original decoding equation is `a + code*(b-a)/65535`. That does **not** make an all-zero motion payload a zero-demand command: for a signed symmetric range it represents the negative endpoint. The function-description page contains a duplicated bit 20 label and a sign error in one `P_MIN` note; the control table and signed sample macros establish the intended angle endpoints. Keep undecoded fault bits/raw frames rather than guessing from the duplicated label. [Type 1/2 table, PDF p.39; sample macros, chapter 4.4](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=39).

### CANopen object scaling

| CANopen object                                   | Exact-model units in this manual                                                                  |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| `0x6062`, `0x6064`, `0x607A`, `0x6067`           | position/demand/window: 16384 pulses per revolution                                               |
| `0x606B`, `0x606C`, `0x6081`, `0x60FF`           | velocity: 0.1 rpm; do not reuse private-CAN rad/s                                                 |
| `0x6083`                                         | acceleration: 0.1 rpm/s                                                                           |
| `0x6071`, `0x6077`                               | signed 16-bit torque/load-ratio scale: **1000 = 14 N·m**, not peak torque                         |
| `0x6078`, `0x6079`                               | current: mA; DC-link voltage: mV                                                                  |
| `0x6040`, `0x6041`, `0x6060`, `0x6061`, `0x603F` | controlword/statusword, requested/displayed mode, error code; retain the exact dictionary’s types |

For this manual’s torque scale, `N·m = raw*14/1000`; negative signed values mean negative torque. The scale’s reference value can differ from the mechanical continuous rating: notably the 2 N·m CANopen base in EL05/RS05 documentation is not a revision of their 1.8/1.6 N·m thermal ratings. These objects belong to CANopen, not Type 17 parameter indices. Set mode while disabled and read the resulting state before any later enable. The manufacturer’s mode numbering uses PP 1, CSP 5, velocity 3, torque 4, homing 6; do not transplant a generic CSP 8 example. [CANopen status/control tables, PDF p.65 onward](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=65).

### MIT feedback layout

MIT feedback uses standard identifiers and a different packed layout: byte 0 is motor ID; angle is bytes 1–2; velocity is `(byte3<<4)|(byte4>>4)`; torque is `((byte4&15)<<8)|byte5`. Its manual tables print a 12-bit range “0–4096”, although a 12-bit field can carry only 0–4095. **Do not use 4096 as an emitted endpoint or choose the quantization denominator by copying that label.** Confirm the exact firmware quantizer before writing a packed MIT motion encoder; the reference below separately documents its commands and float-based position/velocity fields. The mechanical angle and velocity/torque endpoints are ± 12.57 rad, ± 13 rad/s and ± 42 N·m in that chapter. In this PDF byte 6 high bits carry mode/fault/warning and its low nibble plus byte 7 carry temperature × 10; decoding the whole word as temperature includes status bits. [Exact MIT response table, PDF p.70](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=70).

| Thermal quantity                                    | Dated reference and boundary                                                                                      |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Driver-board maximum                                | 145 °C in the driver specification; not a commanded application temperature                                       |
| Private Type 21 motor-overtemperature fault default | 145 °C in the fault-frame table                                                                                   |
| Type 21 warning default                             | 135 °C in the warning-word table                                                                                  |
| Type 21 payload                                     | fault word bytes 0–3; warning word bytes 4–7; preserve raw bytes unless byte order is confirmed for that firmware |

In particular, the temperature at which firmware reports a fault is not a recommended continuous winding temperature or a safety certification. Keep the mechanism unloaded while investigating thermal/fault inconsistencies. [Driver table, PDF p.11](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=11), [Type 21, PDF p.43](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=43).

### Type 17 source, destination and rejection checks

The dated manual’s **worked `loc_kp` read** resolves the garbled general reply table: its request is ID `0x1100FD7F` with `1E 70 00 00 00 00 00 00`; its successful reply is ID `0x11007FFD` with `1E 70 00 00 00 00 F0 41`. Thus request bits 15–8 carry host `FD` and low byte motor `7F`; reply bits 15–8 carry motor `7F` and low byte host `FD`. `00 00 F0 41` decodes little-endian float 30.0. The script checks that source/destination reversal and rejects non-zero reply bits 23–16 before decoding; byte order comes from the worked example. The general table states 00=success and 01=failure but mistranslates which CAN ID is in bits 15–8. That label is not used to reverse routing. [Worked example, PDF p.47; reply table in chapter 4.1](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=47).

The script also requires the echoed two-byte index, reserved bytes 2–3=`00 00`, extended-data-frame flags and DLC 8. A rejected or foreign frame cannot produce a successful value. This is a software fixture/source check; actual arbitration, responses and rejection behavior have not been tested on hardware.

### Read, write, save and protocol conversion

Private Type 17 reads a parameter; Type 18 writes it, and persistence depends on the documented Type 22 save operation. Types 23/25 change bitrate/protocol after power cycling. Mechanical-zero writes, factory restore, magnetic/cogging calibration and protocol changes are deliberate state changes, not detection tools. Stop before switching operating mode. [Chapter 4](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

| Read-only parameter     | Encoding / meaning                                                                                      |
| ----------------------- | ------------------------------------------------------------------------------------------------------- |
| `0x701C` VBUS           | Little-endian IEEE-754 float, V                                                                         |
| `0x7019` mechPos        | Little-endian float, output/load angle in rad                                                           |
| `0x701B` mechVel        | Little-endian float, output/load velocity in rad/s                                                      |
| Type 2 packed telemetry | Big-endian quantized angle/velocity/torque and temperature × 10; use this exact motor/firmware’s ranges |

The two encodings must not be decoded with one byte-order or scale rule. The original first-result script uses only the three float reads. [Parameter table and Type 17 examples](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result through the manufacturer tool

1. Verify the actuator label, chosen manual, **48 V** commissioning supply, mounting, polarity and documented harness. Keep the output unloaded and provide accessible drive-power isolation; support links before removing torque.
2. With power off, connect one motor to the supported debugger and set the documented adapter’s normal mode/termination. Install the official driver/tool from the download center and select the actual serial port.
3. Open the port and choose **Detect Device**. Compare the returned model and ID with the physical unit. Do not click JOG, Start, Set Zero, magnetic calibration or firmware upgrade.
4. While the motor is in standby, choose **Refresh Parameter Table**, then **Read Parameters**. Read bus voltage, position, speed, temperature and fault information; export the baseline before any write. Blue editable and observed fields have different roles.

**Expected result:** the correct model/ID and plausible, repeatable state values while the actuator remains stationary. USB enumeration alone is not motor detection. If the tool does not detect it, inspect supply, AT mode, termination and actual node/protocol before touching gains. [Manual connection/parameter procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

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

**Expected result:** `bus_V`, `position_rad` and `velocity_rad_s` with raw bytes, or a bounded timeout/rejection. Compare voltage with a meter and near-zero speed with a stationary shaft. The script filters extended ID, source/destination, parameter index and data length; traffic from another node must not satisfy the result. Its 1-second response window is an original diagnostic choice, not a control-loop deadline. [Type 17 wire format](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf), [SocketCAN frame/API](https://docs.kernel.org/networking/can.html).

### Advance to control only after readback

7. Save the current mechanical reference, operating mode and limits. Configure a communication timeout appropriate to the controller; the manual’s `canTimeout` uses 20000 counts per second and zero disables that protection. Confirm actual firmware behavior before treating it as a watchdog.
8. On a secured, unloaded mechanism, choose one supported mode while stopped. For position control, begin at the **observed current pose** with conservative velocity/current and a small displacement inside verified limits. Do not start from an arbitrary numeric zero or the host tool’s 1 rad/s JOG as an assumed safe movement.
9. Verify intended joint/sign and stop behavior, then support the output before disable. Keep the private stop command (Type 4), MIT stop and CANopen quick-stop/state transitions tied to the selected protocol. A host Stop button and physical power isolation have different effects.

**Expected result:** a small, repeatable motion of the intended joint with a demonstrated stop path. No universal motion packet or gain is supplied because protocol selection, zero and load conditions must be known first.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                   | Ordered diagnosis / recovery                                                                                                                                                                             |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Port opens but no motor                   | Verify external drive power, adapter normal/boot mode, CAN pair, end termination, bitrate and actual node/protocol.                                                                                      |
| Private read times out but traffic exists | Check 29-bit versus 11-bit frames, host/destination IDs and private versus CANopen/MIT selection. Retain raw frames.                                                                                     |
| Voltage or angle is implausible           | Compare bytes with Type 17 little-endian float; do not apply Type 2 quantization or gear ratio again.                                                                                                    |
| All motors react together                 | Stop; isolate and reconcile duplicate node IDs before adding the chain.                                                                                                                                  |
| Unexpected jump/oscillation               | Disable the control workflow, support the mechanism, inspect zero/sign/mode/current and loop gains; increasing stiffness is not a zero correction.                                                       |
| Parameter write disappears                | Confirm whether the field is volatile and whether the documented save operation was deliberately performed.                                                                                              |
| Thermal or overcurrent fault              | Record exact fault and conditions; unload/cool and inspect wiring/cooling before clearing. Peak torque is not a stall rating.                                                                            |
| Upgrade stalls                            | Use the exact 10P bus/revision-matched build supplied for the unit and the documented retry/re-power flow; retain firmware/parameters and fix bus stability. The common updater is not a firmware image. |

**Can a firmware update establish compatibility?** No. Match the physical motor, encoder/driver revision and protocol package first.

**Does no USB traffic mean failure?** Active reporting is disabled by default in the reference; a quiet bus can be normal until a read request. [Faults, reporting and update chapters](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf).

**Can an RS06 configuration be reused?** A configuration or firmware image for RS06 does not establish 10P support. Use the 10P’s own 25:1 gearing, ±13 rad/s packed range and ±42 N·m classical torque range, with the matching firmware/protocol revision.

**Does a CAN-FD adapter establish compatibility?** Adapter capability alone does not identify the motor’s firmware, nominal/data timing or motion scales. The separate CAN-FD manual’s contradictory torque/gain values remain bounded in the reference below.

## Downloads and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

| Resource                                                                                                                                                                                                              | Model/version and practical use                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| [Exact English manual PDF](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf)                     | RS10PUser Manual260907.pdf; specifications, connector faces, host tool, private/CANopen/MIT protocols and examples      |
| [Exact model STEP](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10P-20261030.stp)                                       | Manufacturer-listed RS10P-20261030.stp; inspect thread depth and swept clearance before fabrication                     |
| [Official resource tree](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778)                                                                                              | Chinese/English revisions, driver, OTA, EDS and accessory documents; select model and protocol generation               |
| [CANopen EDS](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/canopen/driver_v1.1.eds)                                                  | Configuration resource; verify firmware/object-dictionary agreement                                                     |
| [OTA updater source](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/OTA/OTA.py)                                                                             | Inspect model selection, transport and update prerequisites before running                                              |
| [Manufacturer MotorStudio instructions](https://raw.githubusercontent.com/RobStride/MotorStudio/main/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E4%B9%A6-Instructions/Instructions%20for%20using%20the%20Studio_241122.pdf) | Host-tool connection, serial framing and parameter UI; 2024 document, not the authority for newer motor-specific scales |
| [Manufacturer download center](https://robstride.com/download)                                                                                                                                                        | Current supported host application/driver route                                                                         |

The 2024 MotorStudio instructions use an older watchdog scaling example (2000=1 s); the selected 2026 motor manual uses **20000=1 s**. Do not combine those revisions.

Original manufacturer discovery links are retained: [classical 10P manual/CAD folder](https://github.com/RobStride/Product_Information/tree/main/Product%20Literature/CAN2.0/10P), [CAN-FD manual/CAD folder](https://github.com/RobStride/Product_Information/tree/main/Product%20Literature/CANFD/RS10P-CANFD), and [manufacturer resource repository](https://github.com/RobStride/Product_Information). The pinned direct files above identify the versions used for the numerical reference.

The detailed reference below supplies the 10P packet layouts, typed parameter tables, control-state procedures and dated thermal data. Use the separate CAN-FD comparisons before selecting an adapter, firmware or command scale.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026** against the exact PDF and official resource tree at `9dcbce6df00bfe5a887fd6839ec1f64b2a230778`, with the live OpenELAB product and catalog variant. The source’s ratings, thermal conditions and revision discrepancies are kept beside their claims. Manufacturer artwork remains attributed and retains its original rights; this guide adds original interpretation and diagnostics.

**Validation:** source reviewed; important mounting/connector drawings inspected. Python syntax and synthetic packet fixtures were checked without a real device. SDK installation, actual CAN requests, power, calibration, firmware update and motion were **not run**. Expected results are reproduction checkpoints, not observed hardware outputs.

### ROBSTRIDE10P dated reference: classical CAN and CAN-FD boundaries

The packet/control reference below uses **`RS10PUser Manual260907.pdf`** for classical CAN. The separate **`RS10PCANFDUser Manual261016.pdf`** supplies the CAN-FD comparison and its own parameter differences. An identical “10P” name does not establish that the two drive revisions share gains, current-to-torque calibration, bus timing or firmware. The first-result procedure earlier in this guide remains a classical-CAN, 48 V readback. [Classical manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf)., [CAN-FD manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf).

| Quantity                        | Classical CAN manual                           | CAN-FD manual                                                                                                         |
| ------------------------------- | ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Operating supply                | 15–60 V DC                                     | 24–60 V DC                                                                                                            |
| Rated torque test               | 14 N·m at 50 rpm, 210 × 210 mm heat sink       | 14 N·m at 100 rpm; service sink 210 × 210 mm                                                                          |
| Stalled thermal-table rated row | 9.5 N·m                                        | 9.5 N·m; also stated in its electrical table                                                                          |
| Torque constant                 | 7.73 N·m/A RMS                                 | 3.73 N·m/A RMS                                                                                                        |
| Bus statement                   | 1 Mbit/s classical CAN                         | “5 Mbit/s” CAN-FD; separate nominal/data-phase timing not specified here                                              |
| Type 1 feedforward torque range | −42 to +42 N·m                                 | Table: −14 to +14 N·m; sample defines `T_MIN=-42` but omits `T_MAX`, so a complete sample range cannot be established |
| Type 1 gains                    | Kp 0–500; Kd 0–5                               | Table: Kp 0–5000/Kd 0–100; sample macros: 0–500/0–5, an unresolved conflict                                           |
| Type 2 torque feedback          | ±42 N·m                                        | ±42 N·m                                                                                                               |
| Private velocity / angle        | ±13 rad/s; ±4π rad (sample ±12.57)             | ±13 rad/s; ±12.57 rad                                                                                                 |
| Thermal-test caption            | 210 × 210 mm, 25 °C, 135 °C constraint, 10 rpm | Caption says 90 × 85 mm despite 210 × 210 mm service sink; same 25 °C/135 °C/10 rpm context                           |

The CAN-FD manual’s command torque and gain contradictions prevent selecting a trustworthy motion encoder from that PDF alone. Obtain the exact drive revision’s confirmed limits, nominal/data timing and adapter/updater before CAN-FD control. The eight-byte application tables do not make a CAN-FD frame a classical CAN frame; the earlier classical SocketCAN structure is not a CAN-FD transport implementation. [CAN-FD electrical and thermal context](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=9)., [CAN-FD Type 1/2 tables](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=38)., [CAN-FD sample macro disagreement](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=53).

### 10P mechanics, cooling and thermal test data

Both selected manuals state 460 ±3 g, 28 poles, three-phase FOC, 25:1 reduction, 125 rpm ±10% no-load speed, 0.4 A RMS no-load current, and 5.3/19 A peak-phase rated/maximum currents. These are not DC input-current specifications. Their driver tables show 48 V nominal, 60 V maximum, ≤18 mA standby current, Φ57 mm driver envelope, 145 °C board maximum and 14-bit absolute-turn feedback. Mechanical mounting dimensions belong to the exact STEP/drawing, not the driver diameter. [Classical electrical/mechanical/driver tables](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=9)., [CAN-FD driver table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=11).

Common service conditions are −20 to 50 °C, 5–85% RH without condensation, standard ambient 25 ±5 °C, standard RH 65%, storage −30 to 70 °C and Class B insulation. Mount the output shaft horizontally or vertically, count rotation from the shaft view, and keep screw insertion within the drawing’s thread depth. The 600 V AC/1 s/2 mA dielectric figure is a manufacturer qualification condition, not a bench commissioning step; the separate insulation-test notation “DC 500 VAC” is internally inconsistent. [Service/mounting conditions](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=8).

The following source image tables were visually read in **both** PDFs. Times are seconds at the source’s load torque and test conditions. “Rated” preserves a table label; it is not a universal unlimited holding-time guarantee.

| Load (N·m) | Rotating duration (s) | Stalled duration (s) |
| ---------- | --------------------- | -------------------- |
| 42         | 4                     | 1                    |
| 35         | 6                     | 2                    |
| 30         | 10                    | 3                    |
| 25         | 22                    | 6                    |
| 20         | 68                    | 17                   |
| 14         | Rated                 | 120                  |
| 9.5        | Not tabulated         | Rated                |

The classical rotating rated-load test is at 50 rpm, but its overload caption specifies 10 rpm. The CAN-FD rated-load test says 100 rpm, while its overload caption also says 10 rpm and changes the sink caption. Do not combine those conditions into a new duty-cycle rating. The source estimates uneven single-phase stall heating from current and thermistor feedback and gives a 1.414 heating factor relative to rotation; this is not a current/torque allowance. The 135 °C thermal constraint, 145 °C board/fault figures and parenthetical 180 °C value describe different contexts. [Classical overload tables](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=10)., [CAN-FD overload tables](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=10).

### 10P connectors, host tool and configuration workflow

The compact connector is **XT30PB(2+2)-M.G.B** at the board and **XT30(2+2)-F.G.B** at the line side. Match the keyed board-face drawing: large left VBAT+, large right GND; signal CAN-L above CAN-H. A cable-side view is mirrored. The selected compact connector chapters do not establish an SWD header; do not import another motor’s four-pin service map. Use a twisted CAN pair and termination only at the physical bus ends. [Connector diagrams and mating parts](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=11)., [CAN-FD connector chapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=11).

The documented manufacturer adapter is serial AT through a CH340 driver. Packets start `41 54` and finish `0D 0A`; this transport is distinct from native SocketCAN. DIP1 ON selects boot mode and blocks ordinary detection; DIP2 ON inserts 120 Ω. The CAN-FD manual calls for its matched USB-CANFD tool, which is not established by an ordinary USB-CAN product name. [Classical host adapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=13)., [CAN-FD host adapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=12).

1. Secure the unloaded actuator, check power polarity/connector continuity with power off, and choose the adapter matching the motor’s actual bus revision.
2. Install the documented driver/tool, refresh the serial list, open the observed port and select **Detect Device**. Confirm the displayed model and node; opening a serial port alone is not a motor result.
3. Leave the motor stopped. Refresh/read parameters and retain identity, software version, CAN/host IDs, reporting/watchdog settings, zero convention and existing gains.
4. Use the parameter window’s **Read** before **Write**; **Restore Factory** changes configuration. Calibration, zero, ID change and active reporting are separate controls with different effects.
5. In the oscilloscope, choose named channels (Iq/Id, motor/board temperature, output speed/position or encoder position), select the report rate, start plotting and stop it after the observation. Confirm units against the schema below.

**Expected result:** a detected exact model/node and repeatable stationary values with saved original parameters. A timeout calls for power/AT-mode/termination/node/protocol checks before changing controller gains. [Host UI, detection and parameter/oscilloscope workflow](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=15).

For an authorized firmware update, select a build explicitly matching **10P and its CAN/CAN-FD hardware**, open the file, enter preparation, wait for the tool’s upgrade-mode confirmation, then start transfer and verify its success message. The manual documents stopping/re-powering and retrying after a stalled upgrade; fix communication first and retain the previous configuration/version. No exact 10P firmware binary is identified in the pinned repository’s model folders, so the common OTA utility is not itself a compatible firmware image. [Upgrade procedure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=17).

### 10P full host-function schema and sample snapshot

Refresh parameters with the motor stopped, then use **Read**, **Write** or **Restore Factory** for the selected field. Export/read the current configuration before a write or reset. The following is the classical 10P dated manual’s **host-tool schema and example snapshot**. Its `0x20xx`/`0x30xx` function codes are distinct from the private-CAN `0x70xx` indices. The sample values are not certified factory defaults or motor operating limits.

| Function code | Field                | Type   | Access        | Printed max | Printed min | Example value                  | Meaning / source limitation                                                                    |
| ------------- | -------------------- | ------ | ------------- | ----------- | ----------- | ------------------------------ | ---------------------------------------------------------------------------------------------- |
| `0X0000`      | `Name`               | String | R/W           | —           | —           | Unprogrammed string in example | —                                                                                              |
| `0X0001`      | `BarCode`            | String | R/W           | —           | —           | Unprogrammed string in example | —                                                                                              |
| `0X1000`      | `BootCodeVersion`    | String | R             | —           | —           | 0.1.5                          | —                                                                                              |
| `0X1001`      | `BootBuildDate`      | String | R             | —           | —           | Mar 16 2022                    | —                                                                                              |
| `0X1002`      | `BootBuildTime`      | String | R             | —           | —           | 20:22:09                       | —                                                                                              |
| `0X1003`      | `AppCodeVersion`     | String | R             | —           | —           | 0.0.0.1                        | Motor program version number                                                                   |
| `0X1004`      | `AppGitVersion`      | String | R             | —           | —           | 7b844b0fM                      | —                                                                                              |
| `0X1005`      | `AppBuildDate`       | String | R             | —           | —           | Apr 14 2022                    | —                                                                                              |
| `0X1006`      | `AppBuildTime`       | String | R             | —           | —           | 20:30:22                       | —                                                                                              |
| `0X1007`      | `AppCodeName`        | String | R             | —           | —           | Lingzu motor \_                | —                                                                                              |
| `0X2000`      | `echoPara1`          | uint16 | Configuration | 74          | 5           | 5                              | —                                                                                              |
| `0X2001`      | `echoPara2`          | uint16 | Configuration | 74          | 5           | 5                              | —                                                                                              |
| `0X2002`      | `echoPara3`          | uint16 | Configuration | 74          | 5           | 5                              | —                                                                                              |
| `0X2003`      | `echoPara4`          | uint16 | Configuration | 74          | 5           | 5                              | —                                                                                              |
| `0X2004`      | `echoFreHz`          | uint32 | R/W           | 10000       | 1           | 500                            | —                                                                                              |
| `0X2005`      | `MechOffset`         | float  | Configuration | 7           | -7          | 4.619583                       | Motor magnetic encoder Angle offset                                                            |
| `0X2006`      | `MechPos_init`       | float  | R/W           | 50          | -50         | 4.52                           | Reserved parameter                                                                             |
| `0X2007`      | `limit_torque`       | float  | R/W           | 17          | 0           | 17                             | Torque limitation                                                                              |
| `0X2008`      | `I_FW_MAX`           | float  | R/W           | 33          | 0           | 0                              | Weak magnetic current value, default 0                                                         |
| `0X2009`      | `motor_baud`         | uint8  | Configuration | 20          | 0           | 1                              | Baud rate flag bit                                                                             |
| `0X200a`      | `CAN_ID`             | uint8  | Configuration | 127         | 0           | 1                              | id of this object                                                                              |
| `0X200b`      | `CAN_MASTER`         | uint8  | Configuration | 127         | 0           | 0                              | can host id                                                                                    |
| `0X200c`      | `CAN_TIMEOUT`        | uint32 | R/W           | 100000      | 0           | 0                              | can timeout threshold. The default value is 0                                                  |
| `0X200d`      | `status2`            | int16  | R/W           | 1500        | 0           | 800                            | Reserved parameter                                                                             |
| `0X200e`      | `status3`            | uint32 | R/W           | 1000000     | 1000        | 20000                          | Reserved parameter                                                                             |
| `0X200f`      | `Status1`            | float  | R/W           | 64          | 1           | 7.75                           | Reserved parameter                                                                             |
| `0X2010`      | `status6`            | uint8  | R/W           | 1           | 0           | 1                              | Reserved parameter                                                                             |
| `0X2011`      | `cur_filt_gain`      | float  | R/W           | 1           | 0           | 0.9                            | Current filtering parameter                                                                    |
| `0X2012`      | `cur_kp`             | float  | R/W           | 200         | 0           | 0.025                          | Current kp                                                                                     |
| `0X2013`      | `cur_ki`             | float  | R/W           | 200         | 0           | 0.0258                         | Current ki                                                                                     |
| `0X2014`      | `spd_kp`             | float  | R/W           | 200         | 0           | 2                              | Velocity kp                                                                                    |
| `0X2015`      | `spd_ki`             | float  | R/W           | 200         | 0           | 0.021                          | Speed ki                                                                                       |
| `0X2016`      | `loc_kp`             | float  | R/W           | 200         | 0           | 30                             | Position kp                                                                                    |
| `0X2017`      | `spd_filt_gain`      | float  | R/W           | 1           | 0           | 0.1                            | Velocity filter parameter                                                                      |
| `0X2018`      | `limit_spd`          | float  | R/W           | 200         | 0           | 2                              | Location mode speed limit                                                                      |
| `0X2019`      | `limit_cur`          | float  | R/W           | 23          | 0           | 23                             | Position, Velocity mode current limit                                                          |
| `0X201a`      | `loc_ref_filt_gain`  | float  | R/W           | 100         | 0           | 0                              | Reserved parameter                                                                             |
| `0X201b`      | `limit_loc`          | float  | R/W           | 100         | 0           | 0                              | Reserved parameter                                                                             |
| `0X201c`      | `position_offset`    | float  | R/W           | 27          | 0           | 0                              | High speed segment offset                                                                      |
| `0X201d`      | `chasu_angle_offset` | float  | R/W           | 27          | 0           | 0                              | The low end is offset                                                                          |
| `0X201e`      | `spd_step_value`     | float  | R/W           | 150         | 0           | —                              | Velocity-mode acceleration                                                                     |
| `0X201f`      | `vel_max`            | float  | R/W           | 20          | 0           | —                              | PP mode speed                                                                                  |
| `0X2020`      | `acc_set`            | float  | R/W           | 1000        | 0           | —                              | PP mode acceleration                                                                           |
| `0X2021`      | `zero_sta`           | float  | R/W           | 100         | 0           | 0                              | Zero marker                                                                                    |
| `0x2022`      | `protocol_1`         | uint8  | R/W           | —           | —           | 0                              | Protocol flag                                                                                  |
| `0x2023`      | `damper`             | uint8  | R/W           | 0           | 20          | 0                              | Damping switch; printed bounds inconsistent with type/order; do not write from them            |
| `0x2024`      | `add_offset`         | float  | R/W           | -7          | 7           | 0                              | Position offset parameter; printed bounds inconsistent with type/order; do not write from them |
| `0X3000`      | `timeUse0`           | uint16 | R             | —           | —           | 5                              | —                                                                                              |
| `0X3001`      | `timeUse1`           | uint16 | R             | —           | —           | 0                              | —                                                                                              |
| `0X3002`      | `timeUse2`           | uint16 | R             | —           | —           | 10                             | —                                                                                              |
| `0X3003`      | `timeUse3`           | uint16 | R             | —           | —           | 0                              | —                                                                                              |
| `0X3004`      | `encoderRaw`         | int16  | R             | —           | —           | 11396                          | Magnetic encoder sampling value                                                                |
| `0X3005`      | `mcuTemp`            | int16  | R             | —           | —           | 337                            | mcu internal temperature, \*10                                                                 |
| `0X3006`      | `motorTemp`          | int16  | R             | —           | —           | 333                            | Motor ntc temperature, \*10                                                                    |
| `0X3007`      | `vBus(mv)`           | uint16 | R             | —           | —           | 24195                          | Bus voltage                                                                                    |
| `0X3008`      | `adc1Offset`         | int32  | R             | —           | —           | 2084                           | adc sampling channel 1 Zero current bias                                                       |
| `0X3009`      | `adc2Offset`         | int32  | R             | —           | —           | 2084                           | adc sampling channel 2 Zero current bias                                                       |
| `0X300a`      | `adc1Raw`            | uint16 | R             | —           | —           | 1232                           | adc sampling value 1                                                                           |
| `0X300b`      | `adc2Raw`            | uint16 | R             | —           | —           | 1212                           | adc sampling value 2                                                                           |
| `0X300c`      | `VBUS`               | float  | R             | —           | —           | 36                             | Bus voltage V                                                                                  |
| `0X300d`      | `cmdId`              | float  | R             | —           | —           | 0                              | id ring instruction, A                                                                         |
| `0X300e`      | `cmdIq`              | float  | R             | —           | —           | 0                              | iq ring command, A                                                                             |
| `0X300f`      | `cmdlocref`          | float  | R             | —           | —           | 0                              | Position loop command, rad                                                                     |
| `0X3010`      | `cmdspdref`          | float  | R             | —           | —           | 0                              | Speed loop command, rad/s                                                                      |
| `0X3011`      | `cmdTorque`          | float  | R             | —           | —           | 0                              | Torque instruction, nm                                                                         |
| `0X3012`      | `cmdPos`             | float  | R             | —           | —           | 0                              | mit Protocol Angle instruction                                                                 |
| `0X3013`      | `cmdVel`             | float  | R             | —           | —           | 0                              | mit Protocol Speed instruction                                                                 |
| `0X3014`      | `rotation`           | int16  | R             | —           | —           | 1                              | Number of turns                                                                                |
| `0X3015`      | `modPos`             | float  | R             | —           | —           | 4.363409                       | Motor uncounted coil mechanical Angle, rad                                                     |
| `0X3016`      | `mechPos`            | float  | R             | —           | —           | 0.777679                       | Load end loop mechanical Angle, rad                                                            |
| `0X3017`      | `mechVel`            | float  | R             | —           | —           | 0.036618                       | Load speed: rad/s                                                                              |
| `0X3018`      | `elecPos`            | float  | R             | —           | —           | 4.714761                       | Electrical Angle                                                                               |
| `0X3019`      | `ia`                 | float  | R             | —           | —           | 0                              | U-wire current, A                                                                              |
| `0X301a`      | `ib`                 | float  | R             | —           | —           | 0                              | V-wire current, A                                                                              |
| `0X301b`      | `ic`                 | float  | R             | —           | —           | 0                              | W-wire current, A                                                                              |
| `0X301c`      | `timeout`            | uint32 | R             | —           | —           | 31600                          | Timeout counter value                                                                          |
| `0X301d`      | `phaseOrder`         | uint8  | R             | —           | —           | 0                              | Directional marking                                                                            |
| `0X301e`      | `iqf`                | float  | R             | —           | —           | 0                              | iq filter value，A                                                                              |
| `0X301f`      | `boardTemp`          | int16  | R             | —           | —           | 359                            | Plate temperature， \*10                                                                        |
| `0X3020`      | `iq`                 | float  | R             | —           | —           | 0                              | iq Original value，A                                                                            |
| `0X3021`      | `id`                 | float  | R             | —           | —           | 0                              | id Original value，A                                                                            |
| `0X3022`      | `faultSta`           | uint32 | R             | —           | —           | 0                              | Fault status value                                                                             |
| `0X3023`      | `warnSta`            | uint32 | R             | —           | —           | 0                              | Warning status value                                                                           |
| `0X3024`      | `drv_fault`          | uint16 | R             | —           | —           | 0                              | The driver chip fault value is 1                                                               |
| `0X3025`      | `drv_temp`           | int16  | R             | —           | —           | 48                             | The driver chip fault value is 2                                                               |
| `0X3026`      | `Uq`                 | float  | R             | —           | —           | 0                              | Q-axis voltage                                                                                 |
| `0X3027`      | `Ud`                 | float  | R             | —           | —           | 0                              | D-axis voltage                                                                                 |
| `0X3028`      | `dtc_u`              | float  | R             | —           | —           | 0                              | The duty cycle of the U-phase output                                                           |
| `0X3029`      | `dtc_v`              | float  | R             | —           | —           | 0                              | The duty cycle of the V-phase output                                                           |
| `0X302a`      | `dtc_w`              | float  | R             | —           | —           | 0                              | The duty cycle of the W-phase output                                                           |
| `0X302b`      | `VBUS`               | float  | R             | —           | —           | 24.195                         | Vbus in the closed loop                                                                        |
| `0X302c`      | `torque_fdb`         | float  | R             | —           | —           | 0                              | Torque feedback value，nm                                                                       |
| `0X302d`      | `rated_i`            | float  | R             | —           | —           | 8                              | Rated current of motor                                                                         |
| `0X302e`      | `limit_i`            | float  | R             | —           | —           | 27                             | The motor limits the maximum current                                                           |
| `0X302f`      | `spd_ref`            | float  | R             | —           | —           | 0                              | Motor speed expectation                                                                        |
| `0X3030`      | `spd_reff`           | float  | R             | —           | —           | 0                              | Motor speed expectation 2                                                                      |
| `0X3031`      | `zero_fault`         | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X3032`      | `chasu_coder_raw`    | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X3033`      | `chasu_angle`        | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X3034`      | `as_angle`           | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X3035`      | `vel_max`            | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X3036`      | `judge`              | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X3037`      | `position`           | float  | R             | —           | —           | 0                              | Position value                                                                                 |
| `0X3038`      | `chasu_angle_init`   | float  | R             | —           | —           | -0.002301                      | Angle initialization                                                                           |
| `0X3039`      | `chasu_angle_out`    | float  | R             | —           | —           | -0.23012                       | Motor position determination parameters                                                        |
| `0X303a`      | `motormechinit`      | float  | R             | —           | —           | -0.000383                      | Motor position determination parameters                                                        |
| `0X303b`      | `mech_angle_init2`   | float  | R             | —           | —           | -0.000115                      | Motor position determination parameters                                                        |
| `0X303c`      | `mech_angle_rotat`   | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X303d`      | `fault1`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X303e`      | `fault2`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X303f`      | `fault3`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X3040`      | `fault4`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X3041`      | `fault5`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X3042`      | `fault6`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X3043`      | `fault7`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X3044`      | `fault8`             | uint32 | R             | —           | —           | 0                              | Log failure                                                                                    |
| `0X3045`      | `ElecOffset`         | float  | R             | —           | —           | 0                              | electrical Angle offset                                                                        |
| `0X3046`      | `mcOverTemp`         | int16  | R             | —           | —           | 0                              | Overtemperatur e threshold                                                                     |
| `0X3047`      | `Kt_Nm/Amp`          | float  | R             | —           | —           | 0                              | Moment coefficient                                                                             |
| `0X3048`      | `Tqcali_Type`        | uint8  | R             | —           | —           | 0                              | Motor type                                                                                     |
| `0X3049`      | `low_position`       | float  | R             | —           | —           | 0                              | Motor position determination parameters                                                        |
| `0X304a`      | `theta_mech_1`       | float  | R             | —           | —           | 0                              | Type 2 Low speed Angle                                                                         |
| `0X304b`      | `instep`             | float  | R             | —           | —           | 0                              | Motor protection decision parameters                                                           |
| `0X304c`      | `adc0ffset_1`        | int32  | R             | —           | —           | 2034                           | adc sampling channel 1 Zero current bias                                                       |
| `0X304d`      | `adc0ffset_2`        | int32  | R             | —           | —           | 2040                           | adc sampling channel 2 Zero current bias                                                       |
| `0X304e`      | `pos_cnt1`           | uint16 | R             | —           | —           | 0                              | System parameters                                                                              |
| `0X304f`      | `H’`                 | uint8  | R             | —           | —           | 72                             | System parameters; source label garbled, no API meaning inferred                               |

[Host parameter table, PDF pp. 20–26](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=20). Bounds reproduced here are the manual’s UI bounds, not recommended settings. In particular, an unsigned field cannot have a negative minimum, and a `uint8` cannot represent 300. Blank source cells are shown as “—”; they do not mean zero. Firmware examples in this table identify the photographed/documented software, not the firmware installed in a purchased motor. Read back by field name and version before relying on an address.

The CAN-FD PDF contains the same 127 addresses, access/type/value rows, apart from truncated/garbled display labels at `0x201A`, `0x201D` and `0x304F`; no new numerical default is inferred from those label differences. The `0x1003` snapshot says `0.0.0.1` and its app build date is 14 April 2022. These are sample UI values, not evidence that a sold motor runs that firmware. Read its actual version. Both schemas retain internally inconsistent unsigned or reversed bounds, and the last system-field label is not a usable API name. [CAN-FD schema](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=19).

### 10P private-CAN command IDs, data and persistence

Use classical **extended 29-bit data frames, DLC 8** for this section. For ordinary addressed requests define `ID(type) = (type << 24) | (host << 8) | motor`; exceptions are explicitly listed below. Byte numbering starts at zero. Multi-byte typed parameters are little-endian; packed motion fields are high byte first. Do not apply one byte-order rule to every command. [Classical private frame structure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=38).

| Type (decimal / hex)       | Identifier / payload                                            | Response and effect                                                                        |
| -------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| 0 / `0x00` identity        | Addressed ID; zero data                                         | Type 0: source motor in ID data area, destination `0xFE`; payload is 64-bit MCU identifier |
| 1 / `0x01` motion          | Torque code replaces ID bits 23–8; packed payload below         | Type 2 status; used after deliberate enable in motion mode                                 |
| 3 / `0x03` enable          | Addressed ID; initialize data to zeros                          | Type 2; drive enters running state                                                         |
| 4 / `0x04` stop/clear      | Addressed ID; zero payload for stop; byte 0 = 1 for fault clear | Type 2; clearing does not remove the fault cause                                           |
| 4 version signature        | Addressed Type 4; `00 C4 00 00 00 00 00 00`                     | Type 2 signature `00 C4 56`; version components bytes 3–6, high component first            |
| 6 / `0x06` zero            | Addressed ID; byte 0 = 1                                        | Type 2; mechanical-reference change, not a connection probe                                |
| 7 / `0x07` motor ID        | New ID in bits 23–16; host 15–8; old motor in 7–0               | Type 0 identity; new ID effective immediately                                              |
| 17 / `0x11` read           | Bytes 0–1 index LE; 2–7 zero                                    | Type 17 typed reply described below                                                        |
| 18 / `0x12` write          | Index LE at 0–1; reserved 2–3 zero; typed data LE at 4–7        | Type 2; volatile unless supported settings are deliberately saved                          |
| 21 / `0x15` fault feedback | Source motor in ID bits 15–8; host destination low byte         | Bytes 0–3 fault word; 4–7 warning word                                                     |
| 22 / `0x16` save           | Addressed ID; `01 02 03 04 05 06 07 08`                         | Type 2; saves supported configuration fields, not every transient target                   |
| 23 / `0x17` bitrate        | Listed bytes `01 02 03 04 05 06 F_CMD`; byte 7 unspecified      | Type 0; power-cycle effect; `F_CMD` 1/2/3/4 selects 1M/500k/250k/125k in classical table   |
| 24 / `0x18` reporting      | Listed prefix as Type 23; `F_CMD` 0 off, 1 on                   | Default 10 ms; response table labels Type 24, function chapter says Type 2                 |
| 25 / `0x19` protocol       | Listed prefix as Type 23; `F_CMD` 0 private, 1 CANopen, 2 MIT   | Type 0; power-cycle effect                                                                 |

The seven-octet configuration lists under an eight-byte heading leave byte 7 unresolved. Keep those packets as reference, and resolve their complete transaction through the matched firmware/host tool before automation; an invented eighth byte is not source verification. The Type 24 source also disagrees about the report type/destination label. Capture the actual firmware’s reporting transaction and retain its ID, rather than loosening all receive filters. A version-signature reply is not an angle/velocity telemetry payload. [Private command tables and worked read](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=40).

### 10P packed motion and feedback fields

| Location      | Type 1 classical motion request   | Type 2 classical feedback                          |
| ------------- | --------------------------------- | -------------------------------------------------- |
| ID bits 28–24 | 1                                 | 2                                                  |
| ID bits 23–8  | Torque uint16, −42 to +42 N·m     | Status/mode bits plus source motor ID in bits 15–8 |
| ID bits 7–0   | Target motor                      | Host destination                                   |
| Bytes 0–1     | Angle uint16, −4π to +4π rad      | Output angle, same range                           |
| Bytes 2–3     | Velocity uint16, −13 to +13 rad/s | Output velocity, same range                        |
| Bytes 4–5     | Kp uint16, 0–500                  | Torque uint16, −42 to +42 N·m                      |
| Bytes 6–7     | Kd uint16, 0–5                    | Temperature ×10, divide by 10 for °C               |

All data pairs are big-endian. Motion ID torque uses bits 23–8 as a full 16-bit value, despite the PDF’s misleading single “Byte 2” label. Codes 0–65535 cover each affine range; a zero-valued byte pair represents its lower endpoint. Symmetric ranges with 65535 intervals do not have an exact integer code for mathematical zero. The sample macros approximate ±4π as ±12.57 rad. [Type 1/2 field ranges](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=39).

Type 2 ID bits 23–22 are mode (0 reset, 1 calibration, 2 running); bits 21/20/19/18/17/16 report uncalibrated/stall-overload/encoder/overtemperature/phase-overcurrent/undervoltage flags. The duplicated bit-20 label in source prose does not create another flag. Read the full raw ID alongside decoded state.

**Source macro erratum:** classical PDF p.54 prints both `V_MIN` and `V_MAX` as `+13.0f`. That creates a zero conversion span. The Type 1/2 table on PDF p.39 establishes **−13 to +13 rad/s**. Do not paste the equal-endpoint velocity macros. The function note also prints a positive `P_MIN` beside `P_MAX`; use the signed range established by the actual field table/sample, not equal endpoints. [Classical macros with V\_MIN typo](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=54).

#### Original offline packet builder

Save the following as `tenp_packets.py`, then run `python3 tenp_packets.py`. It constructs and prints classical packets without opening a serial/CAN device. Its explicit ranges apply to the classical manual, and its nonzero-span check makes the documented macro failure visible.

```python
import math
import struct

# Offline classical-CAN reference only: this program opens no device.
def read_parameter(node, host, index):
    if not (1 <= node <= 127 and 0 <= host <= 255):
        raise ValueError("Invalid node/host")
    return (17 << 24) | (host << 8) | node, struct.pack("<H", index) + bytes(6)

def encode16(value, lower, upper):
    if not math.isfinite(value) or not lower < upper:
        raise ValueError("Finite value and a nonzero span are required")
    value = min(upper, max(lower, value))
    return round((value - lower) * 65535 / (upper - lower))

def motion_packet(node, position, velocity, kp, kd, torque):
    if not 1 <= node <= 127:
        raise ValueError("Invalid motor node")
    # Documented classical 10P sample angle endpoints; not a CAN-FD profile.
    fields = (encode16(position, -12.57, 12.57),
              encode16(velocity, -13.0, 13.0),
              encode16(kp, 0.0, 500.0), encode16(kd, 0.0, 5.0))
    torque_code = encode16(torque, -42.0, 42.0)
    return (1 << 24) | (torque_code << 8) | node, struct.pack(">4H", *fields)

ident, data = read_parameter(0x7F, 0xFD, 0x701C)
print(f"read ID={ident:08X} data={data.hex(' ')}")
ident, data = motion_packet(0x7F, 0.0, 0.0, 0.0, 0.0, 0.0)
print(f"offline motion ID={ident:08X} data={data.hex(' ')}")
```

**Expected result:** `read ID=1100FD7F data=1c 70 00 00 00 00 00 00` and `offline motion ID=0180007F data=80 00 80 00 00 00 00 00`. The second output is an encoding example, not an instruction to transmit. Enabling a real drive requires the fixture, reference/limits and selected mode described below; zero gains provide no position holding. This program deliberately does not select a CAN-FD profile.

### 10P manufacturer C integration target and SDK boundaries

The classical manual’s program chapter uses **GD32F303** and the vendor CAN library as its example target. It presents integration fragments rather than a complete, versioned SDK project: peripheral clocks, bit timing, GPIO assignment, acceptance filters, interrupt/polling setup and the application scheduling loop must come from the actual board/toolchain. The manual does not identify a specific GD32 firmware-library release or make the example a CAN-FD peripheral driver. The Python examples in this guide use Python 3 standard-library interfaces; they do not require a manufacturer Python SDK.

| Manufacturer example entry point                             | Actual protocol operation / integration dependency                                                                                                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `float_to_uint(x, x_min, x_max, bits)`                       | Clamp/quantize a physical field; its source conversion truncates. Establish nonzero endpoints before division; the offline example above uses its stated round-to-nearest convention. |
| `motor_enable(id, master_id)`                                | Type 3 extended ID, DLC 8; preserve host bits and initialize payload, then call the configured CAN transmitter.                                                                       |
| `motor_controlmode(id, torque, MechPosition, speed, kp, kd)` | Type 1; torque in identifier bits 23–8 and four high-byte-first payload pairs using the classical 10P ranges.                                                                         |
| `motor_reset(id, master_id)`                                 | Constructs the Type 4 stop identifier and initializes eight zero payload bytes; requesting a fault clear is the separate byte-0 = 1 transaction.                                      |
| `float_to_uint(x, x_min, x_max, bits)`                       | Clamps the physical value, scales to `2^bits − 1`, and casts to integer. It requires a nonzero range; the printed equal-positive velocity endpoints violate that requirement.         |
| `motor_modechange(id, master_id)`                            | Type 18 using the selected index and byte-sized run mode; writes index at bytes 0–1 and mode at byte 4.                                                                               |
| `motor_write(id, master_id)`                                 | Type 18 using the selected index and float reference; index at bytes 0–1 and float at bytes 4–7.                                                                                      |
| `can_txd()` / `can_rxd()`                                    | Wrappers around the board’s configured transmit/receive path; they do not initialize a CAN bus or prove that its filters accept replies.                                              |

The manufacturer’s conversion casts the scaled nonnegative value to integer, whereas the original Python builder above uses nearest-integer rounding. Define one rounding convention for a port rather than mixing them; the first-result float reads do not use either packed conversion.

The source overlays a C bitfield structure on the extended identifier (`id:8`, data:16, type:5, reserved:3). Bitfield allocation and aliasing depend on compiler/ABI; a port must check the actual integer against the explicit identifier tables or construct it with masks/shifts. Likewise, `memcpy` of index/float depends on the intended little-endian representation and 32-bit IEEE-754 float. These assumptions do not transfer automatically to another target.

**Additional sample correction:** the printed enable fragment sets its identifier’s data field to `master_id` and later overwrites that same identifier field with zero. That is not payload initialization: it discards the host address. Construct the Type 3 identifier with host bits preserved and initialize all eight payload bytes separately, as established by the Type 3 table. This is separate from the equal-positive-endpoint velocity typo. [GD32 target and examples, PDF pp.53–60](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=53).

No embedded SDK build, CAN peripheral execution or firmware update was run for this guide. The printed offline packet vectors and mocked private-reader checks exercise application fields without claiming target-board validation.

### 10P typed parameter reads and complete wire list

The worked read demonstrates host `0xFD` → motor `0x7F`: request ID `0x1100FD7F`, bytes `1E 70 00 00 00 00 00 00`; successful reply ID `0x11007FFD`, bytes `1E 70 00 00 00 00 F0 41`. Bytes 4–7 are little-endian IEEE-754 **30.0**, not the default guaranteed on a unit. Require Type 17, motor source bits 15–8, host destination bits 7–0, DLC 8, echoed index, reserved zeros and success byte bits 23–16 = 0 before decoding; status 1 means read failure. This worked example resolves the general reply table’s merged columns and mistranslated “master ID” label. [Typed list and worked loc\_kp reply](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=47).

| Wire index | Field            | Purpose                                                                | Type   | Bytes | Published range / default          | Access |
| ---------- | ---------------- | ---------------------------------------------------------------------- | ------ | ----- | ---------------------------------- | ------ |
| `0x7005`   | `run_mode`       | Operating mode: 0 impedance/motion; 1 PP; 2 velocity; 3 current; 5 CSP | uint8  | 1     | —                                  | W/R    |
| `0x7006`   | `iq_ref`         | Current mode Iq command                                                | float  | 4     | -19 to 19 A                        | W/R    |
| `0x700A`   | `spd_ref`        | Rotational Velocity mode Rotational speed command                      | float  | 4     | -13 to 13 rad/s                    | W/R    |
| `0x700B`   | `limit_torque`   | torque limit                                                           | float  | 4     | 0 to 42 N·m                        | W/R    |
| `0x7010`   | `cur_kp`         | Kp                                                                     | float  | 4     | The default value is 0.17          | W/R    |
| `0x7011`   | `cur_ki`         | Ki                                                                     | float  | 4     | The default value is 0.012         | W/R    |
| `0x7014`   | `cur_filt_gain`  | filt gain                                                              | float  | 4     | 0 to 1.0, The default value is 0.1 | W/R    |
| `0x7016`   | `loc_ref`        | Position Mode Angle instruction                                        | float  | 4     | rad                                | W/R    |
| `0x7017`   | `limit_spd`      | Location mode (CSP) speed limit                                        | float  | 4     | 0 to 13 rad/s                      | W/R    |
| `0x7018`   | `limit_cur`      | Velocity position mode Current limitation                              | float  | 4     | 0 to 19 A                          | W/R    |
| `0x7019`   | `mechPos`        | Mechanical Angle of the loading coil                                   | float  | 4     | rad                                | R      |
| `0x701A`   | `iqf`            | iq Filter                                                              | float  | 4     | -19 to 19 A                        | R      |
| `0x701B`   | `mechVel`        | Speed of the load                                                      | float  | 4     | -13 to 13 rad/s                    | R      |
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

[Exact-model private parameter table, PDF pp. 45–47](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=45). Multi-byte index and typed value are little-endian; data occupy bytes 4–7 with unused bytes zeroed. `R` means read-only, `W` means write-only in this dated table, and `W/R` means both. The source’s garbled run-mode line is resolved by the actual current-mode procedure (`run_mode = 3`); it does not establish a current mode 4. The `loc_kp` name is resolved by the worked `0x701E` read. The displayed defaults must not overwrite an existing tuned drive without checking its firmware and readback.

The CAN-FD list uses the same 29 indices/types/permissions. Its explicit differences are `cur_kp` default **0.1** versus classical **0.17**, `iqf` described only in A rather than an explicit ±19 A range, and `mechVel` described only in rad/s rather than explicit ±13. Missing printed bounds are not new unlimited ranges. [CAN-FD typed list](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=44).

### 10P fault fields, thermal context and recovery

| Fault-word bit | Meaning                                |
| -------------- | -------------------------------------- |
| 16             | A-phase sampling overcurrent           |
| 14             | Stall/overload algorithm protection    |
| 9              | Position initialization fault          |
| 8              | Hardware identification fault          |
| 7              | Encoder uncalibrated                   |
| 5 / 4          | C-phase / B-phase sampling overcurrent |
| 3 / 2          | Overvoltage / undervoltage             |
| 1              | Driver chip fault                      |
| 0              | Motor overtemperature                  |

Type 21’s bytes 0–3 are a 32-bit fault field; bytes 4–7 are a separate warning field (warning bit 0 = overtemperature). Zero means no active bits. The source specifies the bit meanings but does not unambiguously establish the four-byte word order; preserve raw bytes and verify firmware packing before writing one universal decoder. Its default overtemperature fault is **145 °C**, warning **135 °C**, in both selected manuals. Those values are separate from the 135 °C thermal-test constraint and are not application temperature setpoints. [Classical Type 21](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=43)., [CAN-FD Type 21](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf#page=42).

The host schema names `faultSta`/`warnSta` and two driver-register fields; identify them by the current tool/version, then retain raw registers and the exact model. A missing encoder calibration, initialization fault or hardware-ID mismatch is a reason to stop the recovery sequence and establish the correct board/motor/firmware, rather than repeatedly clearing it. For overvoltage, inspect regenerative energy, wiring and supply absorption. For timeout, first distinguish AT-mode adapter failure from wrong bitrate/protocol/node. A stop/clear packet is supported only after its actual cause has been corrected and any gravity load is supported. [Fault and host-tool sections](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=28).

### 10P modes, zero reference and calibration procedures

Before control, secure one unloaded motor, identify its firmware/node, read position, choose a nearby reachable target and deliberate current/torque/speed/acceleration caps, and provide a verified stop path. Stop before a mode change. A controller’s protocol range is not a permissible continuous mechanical demand.

| Private mode                        | Type 18 setup and units                                               | Operation sequence                                                     |
| ----------------------------------- | --------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Motion / impedance (`run_mode = 0`) | Type 1 fields above                                                   | Type 3 enable → Type 1 command → Type 2 feedback → Type 4 stop         |
| Current (`run_mode = 3`)            | `iq_ref` 0x7006, float A                                              | Set mode/known current target → deliberately enable → update Iq → stop |
| Velocity (`run_mode = 2`)           | `limit_cur` 0x7018 A; `acc_rad` 0x7022 rad/s²; `spd_ref` 0x700A rad/s | Set limits and known target → enable → command speed → stop            |
| CSP (`run_mode = 5`)                | `limit_spd` 0x7017 rad/s; `loc_ref` 0x7016 rad                        | Set reachable target/limit → enable → update position → stop           |
| PP (`run_mode = 1`)                 | `vel_max` 0x7024 rad/s; `acc_set` 0x7025 rad/s²; `loc_ref` 0x7016 rad | Set profile/target → enable → move through profile → stop              |

Motion control follows `torque = Kp × (position_target − position_actual) + Kd × (velocity_target − velocity_actual) + feedforward_torque`. With Kp = 0, Kd > 0 and zero velocity target, it acts as damping; external rotation regenerates energy. With Kp > 0 and a reachable position target, it supplies restoring torque, and Kd damps approach. The manual’s 1 rad/s and 5 rad examples illustrate that equation; they are not universal first-motion settings for an assembled robot. PP’s `vel_max = 0` is a stop through its planner, not a promise of an instantaneous emergency stop. [Control modes and equation](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=51).

`zero_sta` selects a power-on interval: 0 means 0–2π, 1 means −π to π. The selected source has a missing minus sign in one prose instance, resolved by the parameter definition. Type 6 zero is supported in CSP/motion but blocked in PP in the function chapter. Older firmware may move toward the prior target when zero changes; newer behavior resets the target to zero. The document gives no universal minimum build for that change, so verify the exact firmware before calibrating a mounted joint.

`add_offset` 0x702B is a radian shift of the previous zero reference, applied after power cycling; it is not a new physical hard stop. Save supported reference settings with Type 22 when persistence is needed. `damper = 1` disables the named post-power-off generated-voltage damping protection; it does not release a rated brake. `canTimeout` 0x7028 is zero by default (disabled), with 20000 meaning 1 s. Active-report interval `EPScan_time` 0x7026 uses 1 = 10 ms and +5 ms per increment. CANopen node ID follows the private node ID on the documented newer firmware. [Function description and parameter units](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=48).

For documented cogging calibration, set `iq_test = 1`, restart unloaded, perform the host-tool calibration and confirm `max_alve` becomes nonzero; then enable `alveolous_open = 1` in motion mode. Initialization takes longer with `iq_test = 1` to improve the reference. Separate PP ramps use the named flag `acc_stutus = 1` and `dcc_set` at 0x702E in rad/s²; at flag 0, the acceleration setting controls both ramps. The short wire list does not supply an index for `acc_stutus` or `max_alve`; find them in matching firmware/tool rather than inventing a parameter handle. [Initialization, cogging and PP deceleration](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=50).

### 10P CANopen object dictionary and state sequence

The classical manual documents CANopen as a separate protocol using standard identifiers and an EDS. It describes NMT network state, SDO parameter transfer, PDO process data, EMCY faults, SYNC coordination, node guarding and heartbeat. The generic official EDS is a 26 August 2024 CAN Drive Rev1.0 schema; read identity/mappings and reconcile it with the actual 10P firmware before import. It does not establish CAN-FD support. [CANopen chapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=61)., [Official EDS](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/canopen/driver_v1.1.eds).

| Object          | Type / access                 | Exact classical 10P units or function                                   |
| --------------- | ----------------------------- | ----------------------------------------------------------------------- |
| 0x603F          | uint16 R                      | Error code                                                              |
| 0x6040 / 0x6041 | uint16 R/W / R                | Controlword / statusword                                                |
| 0x6060 / 0x6061 | int8 R/W / R                  | Requested / displayed mode                                              |
| 0x6062 / 0x6064 | int32 R                       | Demand / actual position; 16384 pulses/revolution                       |
| 0x606B / 0x606C | int32 R                       | Demand / actual velocity; 0.1 rpm                                       |
| 0x6077          | int16 R                       | Actual torque; raw 1000 = **14 N·m**                                    |
| 0x6078 / 0x6079 | int16 R / int32 R             | Current mA / DC-link voltage mV                                         |
| 0x6067 / 0x6068 | uint32 / uint16 R/W           | Position window in pulses / window time ms                              |
| 0x6071          | int16 R/W                     | Target torque; raw 1000 = **14 N·m**; position/velocity mode torque cap |
| 0x607A          | int32 R/W                     | Target position, 16384 pulses/revolution                                |
| 0x6081 / 0x6083 | uint32 R/W                    | Profile speed 0.1 rpm / acceleration 0.1 rpm/s                          |
| 0x60FF          | int32 R/W                     | Target velocity, 0.1 rpm                                                |
| 0x6099:01       | Watchdog in this motor manual | Raw 20000 = 1 s; 0 disabled                                             |

Thus a signed torque raw value of 100 corresponds to 1.4 N·m, not 10% of the 42 N·m peak. Position 8192 pulses is half a revolution; velocity raw 100 is 10 rpm. These units are distinct from private/MIT radians and rad/s. The older generic EDS calls 0x6099:01 a homing speed; the motor manual’s watchdog semantics must not be overwritten by that generic name. [State/watchdog and object tables](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=64).

1. Start in `SWITCH_ON_DISABLED`. Set the requested mode and its mandatory limits before enabling; confirm statusword/displayed mode readback.
2. The manual permits controlword 6 → 7 → 15, or direct 15, to reach `OPERATION_ENABLE`. A state readback must confirm the actual transition.
3. Normal stop uses controlword 1 and returns to disabled. Quick stop uses 11 and can cause regenerative voltage rise; it is not an invitation to remove the DC energy-absorption path.
4. Correct a fault’s cause before resetting. The chapter does not supply an exact fault-reset word, so a generic “clear fault” recipe is not enough to construct a source-verified packet.

| CANopen mode                 | Mode value       | Required settings before enable / demand afterward                                                                           |
| ---------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Homing/current-position zero | 6 while disabled | Current position becomes zero; controlword 15 enables holding afterward                                                      |
| PP                           | 1                | Torque cap `0x6071`, speed `0x6081`, acceleration `0x6083`; then target `0x607A`; optional `0x6067` / `0x6068` window checks |
| CSP                          | **5**            | Torque cap `0x6071` and speed `0x6081`; then target `0x607A`; optional window/time                                           |
| Velocity                     | 3                | Torque cap `0x6071`; then target `0x60FF`                                                                                    |
| Torque                       | 4                | Then signed target `0x6071`                                                                                                  |

The manufacturer’s CSP value is 5 here; do not substitute generic CiA402 CSP 8. For switching away from CANopen, the manual specifies a special **extended** ID `0xFFF`, bytes `01 02 03 04 05 06 F_CMD` (0 private, 1 CANopen, 2 MIT), effective after power cycle, with an MCU identity response on the motor’s standard ID. The eighth byte remains unspecified by its nominal eight-byte heading. [CANopen modes and protocol switch](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=65).

### 10P MIT standard-ID commands and packed response

This section is supported by the **classical** manual’s MIT chapter. The CAN-FD manual has no corresponding CANopen/MIT chapter; its copied protocol-selector values alone do not establish those modes on a particular CAN-FD build. Standard ID bits 10–8 hold a command group and bits 7–0 the motor ID where the command uses a group. Ordinary status arrives on the host ID. [MIT frame structure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=70).

| MIT request                         | Standard ID         | Eight-byte data / response                                                       |
| ----------------------------------- | ------------------- | -------------------------------------------------------------------------------- |
| Enable                              | motor               | `FF FF FF FF FF FF FF FC`; status                                                |
| Stop                                | motor               | `FF FF FF FF FF FF FF FD`; status                                                |
| Zero (documented non-position case) | motor               | `FF FF FF FF FF FF FF FE`; status                                                |
| Fault clear/query                   | motor               | `FF FF FF FF FF FF F_CMD FB`; F\_CMD FF clears, any other value queries          |
| Select mode                         | motor               | `FF FF FF FF FF FF F_CMD FC`; 0 motion, 1 position, 2 velocity; status           |
| Change motor ID                     | old motor           | `FF FF FF FF FF FF new_ID FA`; MCU identity                                      |
| Change protocol                     | motor               | `FF FF FF FF FF FF protocol FD`; 0 private, 1 CANopen, 2 MIT; power-cycle effect |
| Change host ID                      | motor               | `FF FF FF FF FF FF host_ID 01`; MCU identity                                     |
| Position command                    | `(1 << 8) \| motor` | LE float rad at bytes 0–3 and LE float rad/s at4–7; status                       |
| Velocity command                    | `(2 << 8) \| motor` | LE float rad/s at bytes 0–3 and current cap A at4–7; status                      |
| Save data                           | motor               | `FF FF FF FF FF FF FF F8`; MCU identity                                          |
| Active report                       | motor               | `FF FF FF FF FF FF 00 F9` off, `... 01 F9` on; status                            |
| Typed read                          | `(3 << 8) \| motor` | Index uint16 LE at0–1; zeros2–7; typed result at4–7                              |
| Typed write                         | `(4 << 8) \| motor` | Index LE at0–1; reserved2–3 zero; typed value LE at4–7                           |

The 10P manual includes save/report/read/write without stating a minimum firmware number in those headings. Do not borrow RS00/RS04’s firmware gate. The typed-read/write response table repeats the request ID group; a locally echoed transmission is not proof of a motor response. Resolve actual firmware direction before making those transactions a first-result test. The earlier private Type 17 reader has a clearly worked source/destination reply. [MIT commands and extensions](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=71).

For MIT motion, the motor’s standard ID carries this packed payload:

| Data location               | Width and physical range                           |
| --------------------------- | -------------------------------------------------- |
| Bytes 0–1                   | Angle uint16 high byte first; −12.57 to +12.57 rad |
| Byte 2 + byte 3 high nibble | Velocity uint12; −13 to +13 rad/s                  |
| Byte 3 low nibble + byte 4  | Kp uint12; 0–500                                   |
| Byte 5 + byte 6 high nibble | Kd uint12; 0–5                                     |
| Byte 6 low nibble + byte 7  | Torque uint12; −42 to +42 N·m                      |

Feedback uses host ID, byte 0 motor ID, bytes 1–2 angle uint16, byte 3/byte 4 high nibble velocity uint12, and byte 4 low nibble/byte 5 torque uint12. Byte 6 bits 7–6 are mode (0 reset, 1 calibration, 2 running), bit 5 fault, bit 4 warning; low nibble plus byte 7 is temperature×10. Do not decode status bits as temperature. MCU identity replies instead use motor ID and an eight-byte unique identifier. The fault-query response uses byte 0 motor ID and bytes 1–4 the detailed fault word with the Type 21 bit meanings, not ordinary angle bytes; word order is not established by that table. [MIT status/packing/fault response](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=70).

The source labels 12-bit fields 0–4096, but the actual bit field can carry only 0–4095. Confirm its firmware quantizer rather than emitting 4096 or guessing the denominator. The all-zero payload is a layout illustration and maps signed fields to negative endpoints. The position example `00 00 A0 40 00 00 A0 40` means 5 rad/5 rad/s, and velocity example `00 00 A0 40 00 00 00 40` means 5 rad/s/2 A. These establish little-endian float order, not appropriate targets for an assembled robot.

For MIT motion: select motion mode if necessary, enable, send the dynamic packet, verify status, and stop. For velocity: select mode 2 while stopped, deliberately enable, send speed/current-cap packet, verify feedback, stop. For position: select mode 1 while stopped, deliberately enable, send reachable position/speed-cap packet, verify feedback, stop. An enable prefix is not interchangeable with the mode-select prefix even though both end in FC. [MIT mode procedures](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf#page=76).

### 10P exact resources and reproduction limits

| Resource                         | Exact source and use                                                                                                                                                                                                                                                                        |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Classical manual                 | [RS10PUser Manual260907.pdf](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10PUser%20Manual260907.pdf); 79 PDF pages; history records version 1.0, initial release 25 November 2025            |
| CAN-FD manual                    | [RS10PCANFDUser Manual261016.pdf](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10PCANFDUser%20Manual261016.pdf);60 PDF pages; history records version 1.0, initial release 28 May 2026 |
| Classical-folder CAD             | [RS10P-20261030.stp](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/10P/RS10P-20261030.stp)                                                                                                           |
| CAN-FD-folder CAD                | [RS10P-20261030.stp](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CANFD/RS10P-CANFD/RS10P-20261030.stp); do not infer identical hardware from the shared filename                                          |
| EDS                              | [driver\_v1.1.eds](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/canopen/driver_v1.1.eds); generic 2024 schema, not fitted-firmware validation                                                              |
| OTA utility                      | [OTA.py](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/OTA/OTA.py); tool source, not a model-specific image                                                                                                                      |
| Official versioned resource tree | [Product\_Information at the reviewed commit](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778)                                                                                                                                               |

For a reproducible support/recovery record, retain the exact model and bus revision, measured supply, adapter identity/termination state, node/host IDs, firmware readback, parameter export, raw fault/report frames and the manual filename/hash. The two PDFs’ date-like filenames differ from their internal version-history dates; neither alone proves the installed firmware. No exact compatible CAN-FD timing recipe, resolved CAN-FD motion scale, or named 10P firmware binary is established here.

The original packet builder was run offline for its stated byte vectors; the guide’s reader has separate mocked-source checks. Host-tool installation, device communication, embedded SDK compilation, firmware transfer, power, calibration and motion were **not run**. Manufacturer thermal durations remain attributed source data, not measurements by this guide.
