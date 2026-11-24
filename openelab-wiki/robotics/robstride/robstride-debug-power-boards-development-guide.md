---
description: >-
  Distinguish RobStride Debug and Power boards,wire DC/auxiliaries
  safely,understand00/11 andbleed limits,andread anASCII boardversion
  withoutenablingloads.
---

# RobStride Debug Board and Power Board Integration Guide

{% hint style="info" %}
[**View the RobStride Debug Board option on OpenELAB**](https://openelab.io/products/robstride-can-to-usb-debugging-module?variant=44550413189318) · [**View the RobStride Power Supply Board on OpenELAB**](https://openelab.io/products/robstride-power-supply-board?variant=45757973463238)

**Accessories:** Debug Board · **SKU:** `ROBSTRIDE-Debug` · the opening link selects the dedicated CAN-to-USB debugger listing. Power distribution board · **SKU:** `ROBSTRIDE-Power`. These are separately purchased accessories with different roles.
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The **RobStride Debug Board** connects a supported host tool to an actuator’s CAN bus. The **RobStride Power Supply Board** distributes an external DC source to motor branches and regulated auxiliary outputs, with sequencing, precharge/discharge, monitoring and fault control. Neither accessory is a ROBSTRIDE04 motor. The power board is not a mains AC/DC converter, and debugger USB power does not supply the motors. [Verified Debug Board option](https://openelab.io/products/robstride-can-to-usb-debugging-module?variant=44550413189318), [verified power board listing](https://openelab.io/products/robstride-power-supply-board?variant=45757973463238).

This guide separates a debugger’s first USB/tool result from a power board’s **non-enabling version read**. Power-board numbers below use the English **V1.3 manual, 2025-12-26**, checked against the newer Chinese **V1.5, 2026-05-07**. A manual version is not a guarantee that a photographed PCB with POWER\_V1.2 silkscreen is your hardware revision. Match the actual board/connector layout before wiring. [English manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf), [Chinese V1.5 manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf).

## Applications <a href="#applications" id="applications"></a>

Use the Debug Board for isolated actuator identification, parameter export, status/fault observation and documented updates. Its serial AT transport differs from a native SocketCAN adapter; pick the interface before selecting software.

Use the Power Board when a robot needs independently controlled motor branches, 24 V/12 V/5 V auxiliaries, supervised startup and a designed regenerated-energy path. Choose source, branch wiring, fusing, bleed resistor and mechanical support for the actual robot. Four output labels are not permission to draw four times every headline current continuously. A Power Board that accepts 65 V does not make a 60 V motor or 24 V-only actuator safe at 65 V.

## Specifications <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Debug Board: host interface, not motor power <a href="#debug-board-host-interface-not-motor-power" id="debug-board-host-interface-not-motor-power"></a>

| Item               | Documented debugger scope                                                  |
| ------------------ | -------------------------------------------------------------------------- |
| Host interface     | CH340-family serial USB adapter with manufacturer host software            |
| CAN framing        | Motor’s classical 29-bit private protocol reference, 1 Mbit/s default      |
| Host serial packet | `41 54` (“AT”) header and `0D 0A` tail; not raw Linux CAN frames           |
| DIP1               | ON=boot mode; normal communication requires the documented normal position |
| DIP2               | ON inserts 120 Ω termination on the documented board                       |
| Motor supply       | Separate verified DC source matching the exact actuator                    |

[ROBSTRIDE04 host/debug interface chapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS04/RS04User%20Manual260713.pdf#page=16), [manufacturer MotorStudio instructions](https://raw.githubusercontent.com/RobStride/MotorStudio/main/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E4%B9%A6-Instructions/Instructions%20for%20using%20the%20Studio_241122.pdf). These switch meanings apply to the documented adapter, not every third-party CH340/USB-CAN product.

### Power Board: electrical and protection conditions <a href="#power-board-electrical-and-protection-conditions" id="power-board-electrical-and-protection-conditions"></a>

| Parameter                        | Dated power-board reference                                                                       |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| External input                   | 20–65 V DC; do not connect AC mains                                                               |
| 24 V output prerequisite         | Automatically off when input is below 30 V                                                        |
| Motor-branch rating              | 20 A rated, 40 A peak in the manufacturer branch specification                                    |
| Aggregate branch overcurrent     | 80 A/30 ms software; 100 A/1 ms hardware                                                          |
| Short-circuit threshold          | 150 A/1.2 µs; one-time fuse I²t 5270 A²s in the source                                            |
| 24 V rail                        | 4 A rated, 6 A current limit at 25 °C                                                             |
| 12 V rail                        | 2 A rated, 3 A current limit at 25 °C                                                             |
| 5 V rail                         | 2 A rated, 3 A current limit at 25 °C                                                             |
| Sampling                         | Voltage ± 1%; total current ± 2%; individual branch current ± 1%                                  |
| Board overtemperature protection | 100 °C; not an application operating target                                                       |
| Precharge/discharge resistor     | 3–10 Ω, 50 W or greater reference; increase energy/power capability for the actual discharge duty |
| Mechanical                       | Four M3 mounting screws; maximum height 16.5 mm in the manual; use exact STEP for envelope        |

[English electrical table, PDF pp.4–6](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=4), [Chinese V1.5 electrical table](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf#page=4). The store’s duplicated total-current accuracy entries do not override the manual’s ± 2% aggregate figure. Current-limit/protection trip figures are not continuous load ratings or a guarantee that an arbitrary wire/connector can carry them.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Separate the three power/control roles <a href="#separate-the-three-power-control-roles" id="separate-the-three-power-control-roles"></a>

| Connection group             | Function and installation check                                                                                |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------- |
| DC source input              | Check input+ and− on actual labelled board; verify supply/pack maximum voltage and polarity with power removed |
| VMBUS /motor branches        | Switched source-voltage motor distribution; not regulated 24 V; motor limits still govern                      |
| 24/12/5 V auxiliaries        | Separate regulated loads within rated currents; 24 V output unavailable below 30 V input                       |
| Precharge/discharge resistor | Required connected component; place clear of wiring/printed parts and allow rated heat dissipation             |
| E-stop input                 | Normally-open default logic; only motor branch power is interrupted                                            |
| CAN /COM                     | Control/monitor transport; not motor power terminals                                                           |
| Fan                          | 12 V fan interface; connector revision must match the fitted board                                             |

Inspect the [manufacturer annotated interface figure, English PDF p.5](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=5) and [newer Chinese interface figure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf#page=4) before choosing a connector. These are attributed RobStride drawings, not a newly invented pinout. The manufacturer’s STEP is linked below. Do not reverse a board view into a cable pin order or infer a connector’s current rating from a photograph.

The V1.5 document states the board will not complete normal power-up self-check with the required precharge/discharge resistor absent. The resistor handles charging/bleeding energy as well as steady heat; 50 W is a starting document rating, not proof that any 50 W resistor is adequate for the robot’s capacitance or regenerative pulses. As an engineering sizing check, capacitor energy is `E=0.5*C*(Vhigh²−Vlow²)`; compare that energy, duty cycle and initial `V/R` current with the resistor/board ratings. Use the actual circuit path and source conditions rather than applying that equation as a complete design. [V1.5 precautions/precharge requirements](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf).

### Power-up modes and revision traps <a href="#power-up-modes-and-revision-traps" id="power-up-modes-and-revision-traps"></a>

| MODE1/MODE0 pair as a two-bit setting | Actual documented behavior                                                                                   |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| `00`                                  | Automatic sequence: 24 V, 12 V and 5 V first; motor power after 1 s                                          |
| `11`                                  | No automatic motor/controlled-rail enable; remote/communication controls startup                             |
| Internal logic                        | 5 V output and internal 3.3 V are powered by default; “not powered on” does not mean every conductor is dead |

Both reviewed manuals use **00 and 11**. A listing that calls the second mode 01 is inconsistent with those documents; do not configure 01 by inference. Change switches only with supply removed. For first checks leave **every motor/auxiliary load disconnected**, choose the documented 11 mode and verify actual outputs with a meter. Switching mode does not substitute for disconnecting the source. [Power sequencing, English pp.6–7](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=6), [Chinese V1.5](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf).

The English manual describes an older X2510WRS-04-9TSN fan connector and a later standard-PC four-pin change; the newer Chinese manual describes the PC-style 2510 connector. Confirm the fitted connector/key/pin labels rather than forcing an older cable. The fan supply is 12 V, not input voltage. [Fan section](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=7).

### Emergency stop and regenerated energy <a href="#emergency-stop-and-regenerated-energy" id="emergency-stop-and-regenerated-energy"></a>

The documented E-stop action removes motor-branch power; 5 V/control circuits can remain live. The vendor claims about 5 µs branch cutoff, not a certified system stop or mechanical brake. A gravity load may fall when drive power disappears. E-stop is latched in this reference: release the input, fix the condition and reapply input power before restoring controlled branches. [Protection section](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=6).

Default bleed thresholds are 64 V on/60 V off. The configurable full-supply setting produces bleed-on=`maximum voltage+6 V` and bleed-off=`maximum voltage+2 V`. The V1.5 document adds that **discharge operation requires the 12 V rail on**. Thus a configuration with 12 V disabled must not assume the bleed path is working. Check the complete power-cycle/deceleration behavior against the actual motor’s lower maximum voltage; the board’s 65 V boundary is not protective enough by itself for every 60 V motor. Never raise a motor overvoltage limit merely to match the board’s default bleed threshold. [English discharge section](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=7), [V1.5 discharge condition](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

### Choose serial AT or native CAN deliberately <a href="#choose-serial-at-or-native-can-deliberately" id="choose-serial-at-or-native-can-deliberately"></a>

| Route                    | Prepare                                                                                             | First result                                                     |
| ------------------------ | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Debug Board +MotorStudio | Official CH340 driver, matching host app, observed serial port and adapter mode                     | USB enumeration, open port, detect one motor and read parameters |
| Power Board COM          | Documented USB/serial route, default 921600 baud with AT wrapper                                    | Supported tool’s board query; not a raw SocketCAN socket         |
| Power Board native CAN   | Known SocketCAN adapter, recorded POWER\_ID, classical 1 Mbit/s, 29-bit extended data frames, DLC 8 | Original Type 5 ASCII version query below                        |

[MotorStudio instructions](https://raw.githubusercontent.com/RobStride/MotorStudio/main/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E4%B9%A6-Instructions/Instructions%20for%20using%20the%20Studio_241122.pdf), [Power Board transport/protocol chapters](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=7). A Linux `/dev/ttyUSB0` port is not `can0`; do not run the native-CAN example against a serial endpoint. The 2024 host-tool manual’s older motor watchdog scaling is not the power-board protocol or a replacement for the dated motor manual.

### Power-board protocol and register scope <a href="#power-board-protocol-and-register-scope" id="power-board-protocol-and-register-scope"></a>

The native-CAN request identifier is `(type<<24)|(data_area2<<8)|POWER_ID`. Read the exact per-type table: the response puts POWER\_ID in bits 23–16, not necessarily in the request’s low byte. Do not copy an actuator’s source/host routing filter onto this accessory. [CAN data format and version query, English pp.8–13](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=8).

| Type | Meaning / first-run policy                                                                                    |
| ---- | ------------------------------------------------------------------------------------------------------------- |
| 1    | Rail/motor enable/disable, restart, clear fault; state changing, excluded                                     |
| 2    | Status query; byte 0=`00` for Type 3 status or `CA` for Type 4 branch current                                 |
| 3 /4 | Status or four branch currents; preserve raw fields until model/endianness confirmed                          |
| 5    | Read ASCII version, zero 8-byte payload; used by original example                                             |
| 6    | Configure automatic reporting; state changing, excluded                                                       |
| 7 /8 | Read/write typed parameter; write changes configuration and needs the documented persistence/restart handling |

The Type 3 voltage fields are tenths-of-a-hundredth-style unsigned 16-bit scales: the table maps 0–65535 to 0–655.35 V, so the stated resolution is 0.01 V. It gives temperature in byte 4 and fault/state information in bytes 5–7. Type 4 allocates two bytes per AL/AR/LL/LR current with 0.01 A scaling. **The status tables do not unambiguously specify multi-byte endianness, and the current-in-ID description has an inconsistent bit range.** The first-result code therefore decodes neither voltage nor current from those ambiguous fields; it reads ASCII version only. This bounds the source defect instead of silently assigning an actuator’s byte order. [Status tables, English pp.10–12](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=10).

| Register | Documented purpose / distinction                                                             |
| -------- | -------------------------------------------------------------------------------------------- |
| `0x6001` | CAN rate selection: 1=1 Mbit/s, 2=500 kbit/s, 3=250 kbit/s, 4=125 kbit/s                     |
| `0x6002` | COM rate: 1=921600, 2=115200, 3=19200, 4=9600 baud                                           |
| `0x6003` | Factory restore; not a connection test                                                       |
| `0x6004` | Remote control flag: 1 **disables**, 0 enables; do not invert this meaning                   |
| `0x6005` | Fan level 1–5; default 3, documented 50%                                                     |
| `0x6006` | POWER\_ID; table default `0xAA`, verify actual saved value                                   |
| `0x6007` | Sound setting                                                                                |
| `0x8001` | Overcurrent threshold float 10–80 A; not permission to exceed wiring ratings                 |
| `0x8003` | Maximum/full battery voltage parameter 24–58 V, default 58; used in bleed threshold formulas |
| `0x8004` | Auto-report interval 5 ms–2 s; default 5 ms                                                  |

These are the manufacturer’s parameter ranges, not values to write during discovery. Parameter read/write tables explicitly place the index low byte first and multi-byte values low byte first; that does not resolve the separate status-table ambiguity. Archive original configuration before any change. [Parameter tables, English pp.14–16](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=14).

## Getting started <a href="#getting-started" id="getting-started"></a>

### Debug Board first result <a href="#debug-board-first-result" id="debug-board-first-result"></a>

1. Select the **Debug Board** option and inspect the delivered adapter revision/connector labels. Prepare the official host application/CH340 driver from the manufacturer download route and a separately secured, unloaded actuator with its exact manual.
2. Connect the debugger to the host only. Check enumeration: Windows Device Manager should show its serial port; on Linux inspect `lsusb` and the actual `/dev/serial/by-id/` entry. Enumeration proves USB transport, not CAN/motor compatibility.
3. With motor power removed, wire the documented CAN pair/reference and exact motor power connector. Set the documented debugger DIP1 to normal mode; set DIP2 termination only if it is a physical bus end. Verify approximately 60 Ω across an unpowered bus with two 120 Ω ends.
4. Apply the motor’s own correct supply. Open its actual serial port in MotorStudio, then choose **Detect Device**, **Refresh Parameter Table** and **Read Parameters**. Record model, ID, firmware, voltage and fault state. Do not choose JOG, Start, Set Zero, calibration or upgrade.

**Expected result:** a stable serial connection and the correct isolated motor identity/status, without commanded movement. No motor response means supply/CAN/protocol investigation is still needed even if the USB port exists. [MotorStudio connection/parameter sequence](https://raw.githubusercontent.com/RobStride/MotorStudio/main/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E4%B9%A6-Instructions/Instructions%20for%20using%20the%20Studio_241122.pdf), [motor manual host chapter](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS04/RS04User%20Manual260713.pdf#page=16).

### Power Board first result without load enable <a href="#power-board-first-result-without-load-enable" id="power-board-first-result-without-load-enable"></a>

5. Inspect the board revision and labelled input/outputs; keep all motor/auxiliary loads disconnected. Install the required correctly rated precharge/discharge resistor. With input power removed, set the documented mode 11 and connect one suitable CAN interface plus correct bus-end termination. Prepare a protected 48 V DC bench input within the board range, with accessible input isolation; no motor is attached for this board-only test.
6. Confirm polarity and intended zero-load outputs with a meter, then apply input power. Logic/5 V may already be live. Observe startup indication and verify that no fault/self-test failure is present. Do not clear a fault to bypass an absent resistor or wiring defect.
7. With the board in its known native-CAN protocol and recorded POWER\_ID, configure the actual SocketCAN adapter:

```bash
ip -details -statistics link show can0
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000
sudo ip link set can0 up
```

8. Save the original code as `read_powerboard_version.py`. It sends only Type 5, a read-only version request. Reply filtering follows the power-board version table, not the motor’s Type 17 layout.

```python
import argparse
import socket
import struct
import time

p = argparse.ArgumentParser()
p.add_argument('--channel', default='can0')
p.add_argument('--board-id', required=True, type=lambda s: int(s, 0))
a = p.parse_args()
if not 1 <= a.board_id <= 255:
    raise SystemExit('Use the recorded POWER_ID, 1..255')
frame = struct.Struct('=IB3x8s')
with socket.socket(socket.PF_CAN, socket.SOCK_RAW, socket.CAN_RAW) as bus:
    bus.bind((a.channel,))
    bus.settimeout(0.1)
    request = (5 << 24) | a.board_id
    bus.send(frame.pack(request | 0x80000000, 8, bytes(8)))
    end = time.monotonic() + 2.0
    while time.monotonic() < end:
        try:
            packet = bus.recv(frame.size)
        except socket.timeout:
            continue
        if len(packet) != frame.size:
            continue
        flags, dlc, data = frame.unpack(packet)
        if not flags & 0x80000000 or flags & 0x60000000 or dlc != 8:
            continue
        ident = flags & 0x1FFFFFFF
        if ident >> 24 != 5 or (ident >> 16) & 0xFF != a.board_id:
            continue
        value = data.rstrip(b'\x00')
        if not value or any(c < 32 or c > 126 for c in value):
            raise SystemExit('Non-ASCII version payload: ' + packet.hex())
        print('board_version=', value.decode('ascii'),
              'reply_id=', hex(ident), 'raw=', data.hex())
        break
    else:
        raise SystemExit('No matched Type5 version reply; check ID/revision/bus')
```

9. Pass the recorded ID; `0xaa` below is the manual’s reference default, not a claim that an altered board still uses it:

```bash
python3 read_powerboard_version.py --channel can0 --board-id 0xaa
```

**Expected result:** `board_version=` followed by the actual printable ASCII version, the reply identifier and raw bytes. `PBV1.00` is the manual’s example string, not an enforced firmware version. For reference IDAA, the request identifier is `0x050000AA`; the response is Type 5 with source boardAA in bits 23–16. No rails are enabled, no registers changed and no fault reset is sent by this code. USB COM requires the separate AT wrapper; this example does not implement it. [Version-query table, English p.13](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=13).

### Pairing and controlled-output checks later <a href="#pairing-and-controlled-output-checks-later" id="pairing-and-controlled-output-checks-later"></a>

Pair a remote only after the unloaded board’s read/measurement checks. The documented sequence holds any remote key, briefly presses the board pairing button twice, releases both, then presses the remote again to verify the indicator. ButtonA controls the four motor branches; B controls 24 V; C controls 12 V; doubleD shuts controlled rails off in the documented motor→12 V→24 V order. These are **output-changing actions**, not a diagnostic version query. Recheck measured voltage and branch identity before connecting one load. [Remote/sequencing section](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=6).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                       | Ordered checks and recovery                                                                                                                                                                 |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB serial port exists but no motor detected  | Check motor supply/polarity; adapter DIP1 normal mode; termination; CAN-H/L/reference; actual motor protocol/ID; then correct host tool.                                                    |
| Power Board fails startup/self-test           | Remove input power, inspect required resistor and wiring, check polarity/supply and actual revision. Do not bridge protection or keep clearing faults.                                      |
| 24 V output absent with 24 V input            | Expected below 30 V input in the manual; check load/rating after using a suitable source. Do not raise the source beyond any attached motor’s limit.                                        |
| 5 V remains after motor E-stop                | Documented scope: the E-stop affects motor branches; logic/5 V can remain powered. Isolate input before rewiring.                                                                           |
| Bleed path does not clamp regeneration        | Verify resistor energy/rating and wiring, actual thresholds and **12 V rail on** requirement in V1.5. Stop motion and redesign the energy path rather than increasing motor voltage limits. |
| Remote appears ineffective                    | Check paired state, mode, latched faults and 0x6004 polarity (1 disables remote); avoid factory restore as first response.                                                                  |
| Native-CAN script times out                   | Check native versus COM AT transport, adapter state/termination, 1 Mbit/s rate, actual POWER\_ID and revision; retain raw traffic before changing IDs.                                      |
| Low-current 24 V ripple                       | The newer manual notes ripple at very light load below 20 mA; measure under the actual allowed load before treating it as an overcurrent fault.                                             |
| Motor-branch short/E-stop/overvoltage latched | Remove input, fix cause, release E-stop if applicable, then power-cycle and remeasure before reconnecting loads.                                                                            |

Undervoltage and auxiliary-rail current-limit/short faults have different recovery behavior from latched motor-branch/overvoltage/E-stop faults. Do not repeat reset/enable commands against a persistent short. [Protection/fault chapters](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=6), [V1.5 notes](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf).

**Does the Debug Board include a motor?** The verified store option is the accessory only; select the motor SKU separately.

**Can I use this board as a 24 V-only motor protector?** Its source-voltage branches are not regulated 24 V, and its default overvoltage/bleed settings are far above a 28 V-limited motor. Design the source and independent limits for the attached motor.

**Does mode 11 guarantee a safe dead board?** No. 5 V/control logic are live by default and an output command/remote can change state. Disconnect input before touching wiring.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                | Verified version / use                                                                                                     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| [Power Board English manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf)                                           | V1.3, 2025-12-26; mounting, interface, electrical ratings, sequencing, faults, fan, full CAN/COM protocol and register map |
| [Power Board Chinese manual](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard/%E7%94%B5%E6%BA%90%E6%9D%BF%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8EV1.5_20260507.pdf) | V1.5, 2026-05-07; newer resistor/self-test, fan and 12 V/discharge notes                                                   |
| [Annotated power-board connector figure](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=5)                        | Manufacturer drawing; match actual PCB and view                                                                            |
| [POWER\_PCB\_V1.3\_1105 STEP](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/POWER_PCB_V1.3_1105.step)                                                                        | Exact observed official CAD filename; check physical revision before fabrication                                           |
| [MotorStudio instructions](https://raw.githubusercontent.com/RobStride/MotorStudio/main/%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E%E4%B9%A6-Instructions/Instructions%20for%20using%20the%20Studio_241122.pdf)                                                                | 2024 host UI/serial-AT reference; not a current motor-specific parameter-scale authority                                   |
| [ROBSTRIDE04 host/debug reference](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/CAN2.0/RS04/RS04User%20Manual260713.pdf#page=16)                                                       | Documented debugger switches and standalone motor connection                                                               |
| [Pinned official resource tree](https://github.com/RobStride/Product_Information/tree/9dcbce6df00bfe5a887fd6839ec1f64b2a230778)                                                                                                                                         | Per-model manuals, driver/EDS/OTA and accessory files                                                                      |
| [Manufacturer download route](https://robstride.com/download)                                                                                                                                                                                                           | Current supported host application/driver                                                                                  |

[ROBSTRIDE04 motor guide](robstride-04-instruction-manual.md) · [RobStride manufacturer index](./). Motor guides retain their own power, pinout, firmware and protocol limits; this accessory guide does not expand those limits.

### Power-board field reference for driver authors <a href="#power-board-field-reference-for-driver-authors" id="power-board-field-reference-for-driver-authors"></a>

The following condenses the English manual's complete communication tables, pp.8–16. Requests use an extended identifier with communication type in bits 28–24, data area 2 in bits 23–8 and target POWER\_ID in bits 7–0. Replies put source POWER\_ID in bits 23–16 according to each reply table. The status/current table's other identifier field is internally inconsistent; retain its raw ID rather than extracting total current from an assumed bit allocation. All eight payload bytes and frame flags should remain in a diagnostic capture. [Original protocol tables](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=8)

| Type | Defined request bytes                                                                    | Defined reply / effect                                                                                                                                 |
| ---- | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1    | Byte 0: 12V; byte 1: VMBUS; byte 2: 24V. `A1` enables and `A0` disables the named output | Type 3 status. Byte 3=`A1` requests restart; byte 4 contains the clear-fault control. Other values/reserved fields are not established as a safe no-op |
| 2    | Byte 0=`00` requests general status; `CA` requests branch currents                       | Type 3 or Type 4, respectively                                                                                                                         |
| 5    | Eight zero bytes                                                                         | Type 5 ASCII version, e.g. the source's `PBV1.00` illustration                                                                                         |
| 6    | Byte 0=`01` enables automatic reporting; `00` disables it                                | Type 3 status; interval is the separate `8004` parameter                                                                                               |
| 7    | Bytes 0–1: little-endian parameter index                                                 | Type 7, same index; value in bytes 4–7, low byte first                                                                                                 |
| 8    | Bytes 0–1: little-endian index; bytes 4–7: typed value                                   | Type 3 status; parameter write changes configuration, so follow with an intentional readback                                                           |

For Type 3, bytes 0–1 represent battery voltage and bytes 2–3 motor-bus voltage at 0.01V/code; byte 4 is board temperature in °C. Bytes 5–7 contain the 24-bit fault/output-state field below. The manual does not clearly establish the status words' multi-byte order, so these are **documented bit meanings, not an implemented endian choice**. The runnable first result remains the ASCII query.

| Logical bit in status field | Meaning when set                                                                                         |
| --------------------------- | -------------------------------------------------------------------------------------------------------- |
| 0 / 1                       | Power-chip overcurrent / overtemperature                                                                 |
| 2 / 3                       | Board overtemperature (100°C reference) / sampled overcurrent                                            |
| 4 / 5                       | Input VBUS overvoltage / undervoltage                                                                    |
| 6 / 7                       | Motor VMBUS overvoltage / undervoltage                                                                   |
| 8 / 9                       | 24V rail overvoltage / undervoltage                                                                      |
| 10 / 11                     | 12V rail overvoltage / undervoltage                                                                      |
| 12                          | Output-branch sampled overcurrent                                                                        |
| 13                          | INA238 fault                                                                                             |
| 14                          | Soft-start abnormality                                                                                   |
| 15–19                       | Not assigned by the source table; preserve raw values                                                    |
| 20 / 21 / 22 / 23           | 12V on / soft-start on / motor VMBUS on / 24V on; these are state bits, not four additional fault alarms |

Type 4 allocates byte pairs 0–1, 2–3, 4–5 and 6–7 to AL, AR, LL and LR current, respectively, at 0.01A/code. Its printed upper code is 65536, which a 16-bit word cannot carry; the representable maximum is 65535. This mathematical correction does not establish byte order or authorize that current physically—the branch's electrical rating remains separate.

### Complete parameter types, defaults and immediate effects <a href="#complete-parameter-types-defaults-and-immediate-effects" id="complete-parameter-types-defaults-and-immediate-effects"></a>

| Hex index / name    | Documented value type    | Documented range and default                                                                                       |
| ------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `6001` Can\_baud    | uint8 value in byte 4    | Codes 1–4; default 1; 1M/500k/250k/125kbit/s                                                                       |
| `6002` Com\_baud    | uint8 value in byte 4    | Codes 1–4; default 1; 921600/115200/19200/9600baud                                                                 |
| `6003` RDF          | Write-only uint8/control | Factory restore; the source requires bytes 2–7 all zero for this operation                                         |
| `6004` remoteCtrl   | uint8 value in byte 4    | 0–1; default 0. Zero enables remote control, one disables it; immediate effect                                     |
| `6005` fanspeedCtrl | uint8 value in byte 4    | Levels 1–5; default 3. Duty references 15%, 25%, 50%, 75%, 99%; immediate effect                                   |
| `6006` POWER\_ID    | uint8 value in byte 4    | Table minimum 0, maximum/default `AA` hex; retain the actual saved ID rather than assuming it                      |
| `6007` soundEffect  | uint8 value in byte 4    | 0–1, default 0; power-on sound setting                                                                             |
| `8001` currocpt     | float32 in bytes 4–7     | 10–80A, default 80A; does not increase connector/wire ratings                                                      |
| `8003` sdT          | float32 in bytes 4–7     | 24–58V, default 58V; set to the intended source's full-charge reference for documented bleed-threshold calculation |
| `8004` arTime       | float32 in bytes 4–7     | 5ms–2s, default 5ms; reporting interval, not a guarantee of host sample delivery                                   |

Read/write index and multi-byte parameter values are explicitly little endian in the source. That statement applies to the parameter frames, not automatically to the separately ambiguous status words. Do not invent a generic “save all” opcode or persistence guarantee for this accessory by copying one from a motor manual.

A smaller discharge resistance improves clamping but increases pulse current, resistor dissipation and potential bus transients; a larger resistance reduces current at the cost of weaker clamping. Long supply wiring changes those transients. Choose resistance, energy rating, thermal mounting and source capacitance together, then verify the actual board's precharge and discharge behavior. Rated auxiliary currents use 25°C test conditions and may need derating or the documented fan. The English manual also notes larger 24V ripple below 20mA load. [Operating notes, pp.17–18](https://raw.githubusercontent.com/RobStride/Product_Information/9dcbce6df00bfe5a887fd6839ec1f64b2a230778/Product%20Literature/powerBoard/Power%20supply%20board%20instructionsV1.3_20251226.pdf#page=17)

The source's final pages contain its manufacturer service/warranty policy and exclusions. Keep the original regional policy with the purchase record; current OpenELAB terms, purchase channel and applicable rights must be checked separately rather than turning that historical policy into a global-store promise.

### Related board and purchasing references

* [English Power Board source folder](https://github.com/RobStride/Product_Information/tree/main/Product%20Literature/powerBoard) and [Chinese Power Board source folder](https://github.com/RobStride/Product_Information/tree/main/%E4%BA%A7%E5%93%81%E8%B5%84%E6%96%99/powerBoard) — original document, illustration and revision navigation. The version-specific field reference above remains the implementation basis.
* [Shared ROBSTRIDE04 listing, Debug Board variant](https://openelab.io/products/robstride04-qdd-120n-m-integrated-joint-motor-module?variant=45204236435654) — established alternate listing for `ROBSTRIDE-Debug`; the unselected family page can instead default to a motor. The opening link uses the dedicated debugger page.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026** against the live verified OpenELAB options, the 23 November catalog, actual English/Chinese accessory PDFs at commit `9dcbce6df00bfe5a887fd6839ec1f64b2a230778`, and the manufacturer’s debugger/host documentation. Connector/control-frame diagrams were inspected; manual/PCB revision distinctions, status-byte ambiguities and E-stop scope are stated beside the affected guidance. Manufacturer documents/artwork retain their original rights; the procedures and Python version reader are original.

**Validation:** source reviewed; Python syntax and synthetic packet fixtures checked; identifier/ASCII filtering reviewed against the version-query table. Driver/tool installation, real USB/CAN traffic, power-board switching, fault injection, firmware updates and motor hardware tests were **not run**. Expected results are user reproduction checkpoints, not observed hardware outcomes.
