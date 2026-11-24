---
description: >-
  Identify IM6014 N6014B-12.6 power and wiring limits, decode synthetic
  feedback, and compare its documented C++, Python and embedded development
  paths.
---

# Unitree IM6014 Motor: Wiring, Protocol and Development Guide

> **Manufacturer reference — no verified OpenELAB SKU.** This page covers [Unitree IM6014](https://www.unitree.com/IM6014), full model **N6014B-12.6**. It does not assign a store listing or whole-robot SKU. The similarly named text in the older GO-M8010-6 page is not GO hardware identification.

## Product overview <a href="#product-overview" id="product-overview"></a>

IM6014 integrates the motor, planetary reducer, driver and encoders into a single joint component. Its FOC current control reduces torque ripple; an outer application still has to provide motion planning, limits and system fault handling. The portal identifies single-turn absolute encoders at the rotor and output. The 15-bit rotor measurement supplies operating feedback; the output encoder is described as a power-on calibration reference, not a continuously exposed absolute output feedback channel. Gear reduction is **3:38**, or `r=38/3` (often rounded to 12.66). [About IM6014](https://doc-cdn.unitree.com/30/1371/en/30_1371_en) [Motor Overview](https://doc-cdn.unitree.com/30/1375/en/30_1375_en) [FAQ](https://doc-cdn.unitree.com/30/1385/en/30_1385_en)

This guide covers the full text of 18 selected English portal records: 16 substantive chapters and two empty container nodes, plus the manufacturer range page. It does not claim that the entire Unitree portal or linked binary archives were read. Documentation snapshot: 24 November 2026; individual portal update dates and content hashes are retained with the evidence.

## Applications <a href="#applications" id="applications"></a>

Use IM6014 as a designed-in joint in a legged mechanism, manipulator or other controlled test assembly where the mounting, peak power and bus timing suit the load. The peak torque and free speed do not establish a continuous duty rating. A wire-ring mount suitable for a light static load is not a walking-joint qualification. No robot model becomes supported by SDK2 merely because it uses this component. [About IM6014](https://doc-cdn.unitree.com/30/1371/en/30_1371_en) [Structure Installation](https://doc-cdn.unitree.com/30/1302/en/30_1302_en)

An initial development milestone can be a correct offline decoder and model record, followed later by a manufacturer-approved, mechanically restrained bench process. Direct torque control on an unloaded shaft can accelerate it rapidly; high stiffness and abrupt reversals can excite vibration or regenerate energy into the supply.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                   | Source-backed value / limit                                                                      |
| ---------------------- | ------------------------------------------------------------------------------------------------ |
| Full model             | N6014B-12.6, marketed as IM6014                                                                  |
| Mass; outline          | 535 g; approximately φ65 × 60 mm                                                                 |
| Supply                 | Table: 24–75 V DC; power-supply prose: 24–72 V under “M6014”; revision conflict unresolved       |
| Maximum line current   | 40 A headline; not a system continuous-current allocation                                        |
| Peak output torque     | 34.4 Nm opposing rotation; 31.7 Nm in the same direction                                         |
| Maximum speed          | 54.2 rad/s at 60 V, not simultaneous with peak torque                                            |
| Reduction              | 38/3; advertised curve uses 12.66                                                                |
| Rotor encoder          | 15-bit single-turn absolute; output encoder used for power-on reference                          |
| Bus                    | Half-duplex RS485; 6 Mbps factory, documented 4 Mbps option; 8 data bits, no parity, 1 stop bit  |
| Addressing             | IDs 0–14; 15 broadcast, no reply                                                                 |
| Temperature statements | Manufacturer minimum −20°C; driver protection 90°C and winding 130°C; not an ambient upper limit |

The [manufacturer table](https://www.unitree.com/IM6014) and portal curves have conditions, including the plotted 60 V supply and 25°C environment. The 72/75 V discrepancy needs a delivered-revision answer before power selection; the overvoltage protection figure is not a usable operating ceiling. Do not derive continuous torque, cooling or ingress certification from the peaks. [About IM6014](https://doc-cdn.unitree.com/30/1371/en/30_1371_en)

For electrical budgeting, include acceleration, simultaneous motor loading, cable losses and regenerated energy. A switching supply that cannot sink braking energy can suffer bus overvoltage even if the drive trips. Select a properly protected battery or regenerative-capable supply under the final system design; avoid large position steps and rapid reversals during commissioning.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Motor wiring and bus layout <a href="#motor-wiring-and-bus-layout" id="motor-wiring-and-bus-layout"></a>

Use the orientation in the official interface figure, the delivered connector keying and the matching cable. The two XT30(2+2) ports are functionally equivalent for power and daisy chaining. In the exact motor-facing view shown, the **left port has B above A, with power − to the left of +; the right port has B above A, with power + to the left of −**. Only the horizontal power-contact order reverses between ports; the B-above-A signal order does not. Read these coordinates in the shown motor-facing view, not as a mating-cable pinout, and verify the delivered connector keying and matching harness. [About IM6014](https://doc-cdn.unitree.com/30/1371/en/30_1371_en) [Line connection](https://doc-cdn.unitree.com/30/1367/en/30_1367_en)

![Official IM6014 connector orientation; both ports must be read in the shown view](https://doc-cdn.unitree.com/static/2026/9/16/c23bd6bf69b848229390439416369e6a_1879x995.png)

Connect power positive and negative only to their power contacts, and communication A/B only to their designated contacts. Match controller/transceiver ground to the motor reference through the intended harness. Power off before changing any cable. Use a high-speed half-duplex adapter and cable validated for 6 Mbps or the configured 4 Mbps; an ordinary low-speed RS485 converter is insufficient. Every device on one bus needs the same baud rate and a unique ID. ID 15 cannot be used for a receive test because broadcasts do not reply. The desktop assistant is **single-motor only**, even though custom protocol applications can address a daisy chain. [Line connection](https://doc-cdn.unitree.com/30/1367/en/30_1367_en) [FAQ](https://doc-cdn.unitree.com/30/1385/en/30_1385_en)

### CAN adapter boundary <a href="#can-adapter-boundary" id="can-adapter-boundary"></a>

The IM6014 portal lists a CAN-to-485 module, but its model text still includes an unresolved placeholder. Treat that chapter as an adapter reference, not proof that the GO-specific CAN protocol or every adapter firmware supports this drive. It describes module IDs 0–3 (default 3), 1 Mbps CAN or 500 kbps with DIP 4 on, and a 115200-baud 8N1 maintenance UART. The module's 80 V maximum and 5 V signal limit do not enlarge the motor's supply range. The linked protocol PDF was listed, not opened. Diagnostic `AT+T`, reset `AT+R`, bootloader `AT+P` and especially `AT+D` are not passive checks: the last command makes all connected motors rotate. [CAN to 485 Module](https://doc-cdn.unitree.com/30/1626/en/30_1626_en)

### Mounting <a href="#mounting" id="mounting"></a>

The light-load method combines the provided wire ring and adhesive and is described for light/static, low-vibration use. Heavy loads need the matching clamping groove and fixture. The source's recommendation of 70% of a clamp's rated tightening torque cannot be converted to an invented universal bolt torque. Obtain the exact clamp rating, groove drawing and load case. Avoid self-disassembly; encoder alignment and sealing can be lost. [Structure Installation](https://doc-cdn.unitree.com/30/1302/en/30_1302_en) [FAQ](https://doc-cdn.unitree.com/30/1385/en/30_1385_en)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Hybrid control and outer loops <a href="#hybrid-control-and-outer-loops" id="hybrid-control-and-outer-loops"></a>

The drive combines feedforward torque with proportional position and velocity feedback:

`tau = tau_ff + kp * (q_des - q) + kd * (dq_des - dq)`.

`kp` has units Nm/rad and `kd` has units Nm/(rad/s). Position control uses nonzero position gain and damping; speed control sets position gain to zero and uses velocity gain; damping sets a zero desired speed with velocity gain; pure torque sets both gains to zero. Zero feedforward and zero gains remove the commanded torque contribution while the drive can remain enabled. That is neither an independent power disconnect nor a guarantee that a gravity-loaded linkage will hold position. Feedforward plus feedback creates hybrid control. These are combinations of fields within FOC, not necessarily distinct packet mode numbers.

A gear ratio `r` relates rotor and ideal output quantities as `q_out=q_rot/r`, `dq_out=dq_rot/r`, and `tau_out≈tau_rot*r`; friction and losses make torque conversion an estimate. Equivalent output position and velocity gains scale by `r²`. Always identify which side an API uses before applying a ratio. A source integer's representable range describes serialization, not a safe mechanical command envelope.

The portal discusses proportional control's steady-state error and adding an outer PI velocity or position loop. An integrator needs measured timing, saturation and anti-windup; the supplied pseudocode is not a tuned motion controller. Do not copy the source's dimensional typo for `kp` or its suggestion to increase torque when a torque-controlled motor is already too fast. Small integer steps have a fixed physical quantization at the selected scale; they do not become coarser simply because the stored value is larger. [Control Mode](https://doc-cdn.unitree.com/30/1382/en/30_1382_en)

### Exact wire contract <a href="#exact-wire-contract" id="exact-wire-contract"></a>

IM6014 uses a **20-byte host command starting FE EE** and **26-byte reply starting FC EE**. It is not the GO 17/16-byte protocol. Byte 2 packs a four-bit ID, three-bit mode and a timeout-protection flag. In the command, torque is at offsets 4–5, speed 6–7, position 8–11, position gain 12–13 and velocity gain 14–15; follow the frame table and structure rather than a conflicting prose byte number. [Motor Protocol](https://doc-cdn.unitree.com/30/1383/en/30_1383_en)

| Rotor-side quantity     | Raw representation                                                  |
| ----------------------- | ------------------------------------------------------------------- |
| Torque                  | signed 16-bit; physical Nm = raw / 2560                             |
| Velocity                | signed 16-bit; rad/s = raw / 64 × 2π                                |
| Position                | signed 32-bit; rad = raw / 32768 × 2π                               |
| Position gain (`k_pos`) | signed `int16_t`; ordinary raw 0–32767; physical gain = raw / 12800 |
| Velocity gain (`k_spd`) | signed `int16_t`; ordinary raw 0–32767; physical gain = raw / 51200 |

The IM6014 command structure reserves gain values −32768 through −1; they are not ordinary gain settings. Do not accept 32768–65535 as unsigned gains: those bit patterns represent negative signed values in this contract. The scales above remain unchanged, and serialization limits do not establish safe physical gains. These signed declarations differ from the GO packed-header gain fields. [Motor Protocol](https://doc-cdn.unitree.com/30/1383/en/30_1383_en)

The reply has signed driver/case temperature at byte 3, winding temperature at 4, supply voltage at 5 (raw/2 V), torque at 6–7, velocity at 8–9, position at 10–13 and a 32-bit fault mask at 14–17. Bytes 18–19 reserve the low 13 bits and carry the three-bit warning in the upper bits; bytes 20–21 are reserved. Do not interpret the reserved low bits as the servo's output encoder. Checksum bytes 22–25 are little-endian. The CRC is the documented **wordwise CRC32**, seed FFFFFFFF and polynomial 04C11DB7: command coverage is bytes 0–15, while reply coverage is bytes 2–21, deliberately excluding the reply header. A generic `zlib.crc32` call is not equivalent. [Motor Protocol](https://doc-cdn.unitree.com/30/1383/en/30_1383_en)

### C++, Python and embedded paths <a href="#c-python-and-embedded-paths" id="c-python-and-embedded-paths"></a>

The dedicated C++ chapter declares C++17, CMake ≥3.10 and Windows MSVC or MinGW. Its layers are `SerialPort` (connection, sending and asynchronous receive), `MotorProtocol` (packing, special commands, parsing and fault/warning decoding) and `MotorController` (connection, asynchronous control, basic/advanced control, fault management and cached feedback). Advanced control methods automatically begin periodic transmission; the documented default is 100 Hz, with a suggested 50–1000 Hz range. A setting is not a measured real-time guarantee, and `getLatestFeedback` returns a cache rather than forcing a new device transaction. The CLI and GUI can also transmit immediately. [C++ Example](https://doc-cdn.unitree.com/30/1380/en/30_1380_en)

The source's configure-only example omits a separate build step. A future, reviewed build would configure a matching extracted archive with `cmake -S . -B build` and compile with `cmake --build build`; neither was run for this guide. The archive implementation and its dependencies/license have not been inspected, so the documented classes are source-document contracts rather than an independently built API. The Python example asks for Python 3.11+ and `pyserial`. The STM32 example targets STM32F413RGT6, recommending floating-point hardware, with PA9 TX, PA10 RX and PA11 DE for the external transceiver. Both require the actual high-speed UART path. Their provided routines command motors and are unsuitable as a first passive result. [Python Example](https://doc-cdn.unitree.com/30/1379/en/30_1379_en) [STM32 Example](https://doc-cdn.unitree.com/30/1377/en/30_1377_en) [Data Download](https://doc-cdn.unitree.com/30/1384/en/30_1384_en)

### Assistant, configuration and release control <a href="#assistant-configuration-and-release-control" id="assistant-configuration-and-release-control"></a>

The assistant has communication, transmit, receive, configuration and plotting areas. Rotor/output display selection performs conversions; plot checkboxes select traces, not whether traffic is transmitted. Auto Refresh, Auto Scale and zoom control display. Receipt-order plots are not a synchronized robot clock. The Windows latency-setting discussion for rates above 60 Hz depends on the actual driver; it is not a universal Windows throughput ceiling. The IM6014 and M8010 assistants are explicitly not interchangeable. [Motor Debugging Assistant](https://doc-cdn.unitree.com/30/1306/en/30_1306_en) [FAQ](https://doc-cdn.unitree.com/30/1385/en/30_1385_en)

Configuration includes ID changes, selecting 6 or 4 Mbps, firmware updates, factory versus high-precision power-on position, temporary bootloader entry/exit and fault recovery. Factory power-on mode accepts arbitrary angles. High-precision mode instead needs physical limits A/B, a configured output position and travel within the documented ±360° bounds; incorrect setup makes startup position unreliable. Firmware transfer is described as 10–20 s, not guaranteed completion time. Exiting temporary bootloader still requires restoring motor mode. All are state-changing operations and excluded from the offline checkpoint. The download chapter currently says no firmware updates; “factory latest” is not a version identifier for a delivered unit. [Motor configuration](https://doc-cdn.unitree.com/30/1378/en/30_1378_en) [Data Download](https://doc-cdn.unitree.com/30/1384/en/30_1384_en)

A later live integration needs the delivered model, drive and hardware revision, firmware identifier, adapter, operating system, serial device, bus rate and ID recorded together. Assign one process exclusive ownership of the serial bus; close the assistant, other terminal tools and any robot controller before a qualified bench session. Each active status poll can transmit a control/state transaction. None of these motors provides a DDS subscriber-only first result. A successful frame CRC is not proof of model identity, firmware compatibility, safe mounting or fresh physical measurement.

For an eventual receive log, preserve immutable frame bytes with model provenance, monotonic receipt time, local frame counter and the exact parser revision. Reject mismatched IDs, length, header, CRC and invalid SDK results. Measure arrival age separately from changes in position: a stationary motor can have valid fresh feedback. On loss or stale feedback, stop the application under a separately engineered stop procedure; closing a port or attempting a final zero command cannot guarantee delivery over a broken link.

The documented controller API also exposes synchronous connection setup, start/stop of its asynchronous worker, direct basic commands, advanced torque/velocity/position/damping/hybrid convenience calls, fault operations and last-feedback retrieval. Its command-line interface wraps those same responsibilities. Serial-port open/close, transmit and receive-thread management are separate from protocol packet packaging and from the application controller. A CLI help entry is not a read-only safety property: any command that starts periodic control, changes mode or clears/reset faults needs the matched hardware procedure. Archive implementations, overload behavior and measured scheduling were not audited here; API names and responsibilities describe the read chapter only.

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Save the complete original Python block below as a local file.
2. Run that file with an existing Python 3 interpreter; no package installation is needed.
3. Compare the printed OFFLINE PASS result and preserve all unverified metadata flags.

### First result: decode a synthetic reply without equipment <a href="#first-result-decode-a-synthetic-reply-without-equipment" id="first-result-decode-a-synthetic-reply-without-equipment"></a>

This original standard-library Python exercise creates one IM6014-format reply in memory, checks length, address and CRC, and converts its documented rotor fields. It imports no Unitree code, opens no port and transmits nothing. Save the complete block as a local file and run it with an existing Python 3 interpreter. Expected result: `IM6014 OFFLINE PASS 26 bytes`, followed by `rotor_torque=0.100 Nm output_estimate=1.267 Nm`. That proves this synthetic exercise only. It does not validate real feedback, a firmware revision or a power supply.

```python
"""Original synthetic feedback exercise. Select one documented model, never autodetect."""
import math
import struct
MODEL = 'IM6014'  # This file's example; servo guide uses J288 explicitly.

def crc_words(data):
    if len(data) % 4:
        raise ValueError('CRC input must contain whole little-endian words')
    value = 0xffffffff
    for offset in range(0, len(data), 4):
        word = int.from_bytes(data[offset:offset+4], 'little')
        for bit in range(31, -1, -1):
            top = value >> 31
            value = (value << 1) & 0xffffffff
            if top ^ ((word >> bit) & 1):
                value ^= 0x04c11db7
    return value

def decode(frame, expected_id=0):
    if MODEL not in ('IM6014', 'J288', 'S288'):
        raise ValueError('Unknown model contract')
    frame = bytes(frame)
    if len(frame) != 26 or frame[:2] != b'\xfc\xee':
        raise ValueError('Expected a 26-byte feedback frame, no host padding')
    if crc_words(frame[2:22]) != int.from_bytes(frame[22:], 'little'):
        raise ValueError('CRC mismatch')
    if (frame[2] & 15) != expected_id or (frame[2] & 15) == 15:
        raise ValueError('Unexpected or broadcast ID')
    ratio, torque_scale, speed_scale = ((38/3, 2560, 64) if MODEL == 'IM6014'
                                       else (288.35, 256000, 2.56))
    torque, speed, position = struct.unpack_from('<hhi', frame, 6)
    status = int.from_bytes(frame[18:20], 'little')
    return dict(model=MODEL, mode=(frame[2] >> 4) & 7,
                timeout=bool(frame[2] & 128), voltage=frame[5] / 2,
                driver_or_case_temp=struct.unpack_from('b', frame, 3)[0],
                winding_temp=frame[4],
                error=int.from_bytes(frame[14:18], 'little'), warning=status >> 13,
                rotor_torque=torque / torque_scale,
                output_torque_estimate=torque / torque_scale * ratio,
                output_position_from_rotor=position / 32768 * math.tau / ratio,
                output_speed_from_rotor=speed / speed_scale * math.tau / ratio,
                output_encoder_raw=(status & 8191) if MODEL != 'IM6014' else None,
                data_origin='synthetic offline frame')

if __name__ == '__main__':
    frame = bytearray(26)
    frame[:2] = b'\xfc\xee'
    frame[3:6] = bytes([25, 30, 96])
    struct.pack_into('<hhi', frame, 6, 256, 0, 0)
    frame[22:] = crc_words(frame[2:22]).to_bytes(4, 'little')
    result = decode(frame)
    print(result['model'], 'OFFLINE PASS', len(frame), 'bytes')
    print('rotor_torque=%.3f Nm output_estimate=%.3f Nm' %
          (result['rotor_torque'], result['output_torque_estimate']))
```

Select the model from trusted physical/source metadata before parsing. A servo reply shares this header, size and CRC but uses different scales; no header-based autodetection is possible. The synthetic zero position is not a captured or calibrated position. The decoder exposes raw fault and warning fields rather than clearing them.

### Conditions before a later powered bench session <a href="#conditions-before-a-later-powered-bench-session" id="conditions-before-a-later-powered-bench-session"></a>

Record the exact nameplate and firmware, resolve the supply-range discrepancy, obtain the matching wiring and clamp drawings, confirm one bus owner and independently accessible power removal, and mechanically support the mechanism. Have the manufacturer approve the adapter and a stopped-state status transaction for this firmware. A validated receive path should be established before gains, trajectories or timeout-recovery actions are considered. This guide supplies no motion, calibration or flash command to run.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### Communication, identity and plotting checks <a href="#communication-identity-and-plotting-checks" id="communication-identity-and-plotting-checks"></a>

The following groups cover the portal's 24 FAQ topics without using a motion demonstration as a connection test. [FAQ](https://doc-cdn.unitree.com/30/1385/en/30_1385_en)

| Symptom / question                      | Read-only planning and evidence to collect                                                                                                                                                                                           |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Unknown factory settings or ID          | Source says ID 0, 6 Mbps and factory startup position mode; confirm delivered records. Green indicator flashes per cycle are described as ID+1. The GUI's Query ID transmits, so it is not an offline step.                          |
| Empty ID / powered but no communication | Check correct IM6014 software, configured baud, supplied harness, power and transceiver. Inspect configuration without starting an active demo.                                                                                      |
| USB device absent                       | Check the adapter identity, host port enumeration and matching driver; do not install an unrelated download based only on the connector shape.                                                                                       |
| Third-party converter                   | Establish actual 4/6 Mbps half-duplex capability and timing; the official package is the documented starting reference, not a universal adapter requirement.                                                                         |
| Which motor port / multi-motor topology | Either equivalent port can be used; unique IDs and matching rates are essential. GUI supports one motor only; custom examples are active multi-device applications.                                                                  |
| Wrong host software / pins              | Use the IM6014 package and exact connector drawing; M8010 software and remembered pin order are insufficient.                                                                                                                        |
| Trace checked but blank                 | Check Auto Refresh, Auto Scale and selected traces. Trace visibility does not stop transmission.                                                                                                                                     |
| Encoder / gearbox / repair              | Dual absolute single-turn encoders, rotor 15 bit, output used at power-on, 38/3 planetary reduction. Avoid self-disassembly.                                                                                                         |
| Firmware or battery                     | Download page says no firmware updates and offers no dedicated motor battery. Record the delivered firmware; design power against confirmed revision limits.                                                                         |
| CAN or help                             | A bridge is required for CAN; see the adapter qualification limits above. Contact the purchase platform or [Unitree service](https://serviceconsole.unitree.com/index.html#/) with model, firmware and a de-energized wiring record. |
| Cable reconnected but still stopped     | Enabled communication-timeout protection latches. Clear-error is not timeout recovery; approved transition to stop/reset is separate from reconnecting a cable.                                                                      |
| Speed vibration / undervoltage          | Excess velocity gain can cause chatter, current spikes and supply sag. Source no-load examples cite 0.5–6 Nm/(rad/s), with problems above 10; these are conditional examples, not universal gains for a loaded mechanism.            |

### Fault and timeout boundaries <a href="#fault-and-timeout-boundaries" id="fault-and-timeout-boundaries"></a>

| Bit        | Fault meaning                                                        | Clear after cause removed? |
| ---------- | -------------------------------------------------------------------- | -------------------------- |
| 0          | Overcurrent                                                          | Reset/power cycle required |
| 1, 2       | Transient / sustained overvoltage                                    | Clear supported            |
| 3          | Transient undervoltage                                               | Clear supported            |
| 4          | Chip overheating                                                     | Clear supported            |
| 5, 6       | MOS hot/cold / abnormal temperature                                  | Clear supported            |
| 8, 9       | Housing temperature abnormal / winding overheat                      | Clear supported            |
| 10         | Rotor encoder error                                                  | Reset/power cycle required |
| 12         | Output encoder error                                                 | Clear supported            |
| 13         | Stored data error                                                    | Reset/power cycle required |
| 14         | Abnormal reset                                                       | Clear supported            |
| 16, 17     | Chip verification / calibration mode                                 | Reset/power cycle required |
| 19, 20, 22 | Driver version too low / wrong firmware model / hardware overcurrent | Reset/power cycle required |

These are simultaneous bit flags, not a sequential error enum. Warning bit 0 means an abnormal low-voltage supply. “Clear supported” describes the protocol's recovery option after the physical cause is removed, not permission to mask an active fault. Unsupported bits remain unknown. A clear-error transaction uses special mode 6 and prescribed fields; mode 7 resets the drive. Both mutate its state. The source quotes about 0.3 s for reset and 1.3 s for power-up; lack of replies during either interval is expected, not proof of a healthy stop.

The documented timeout option stops after an interruption exceeding about one second, but only when enabled; it is not an independent certified stop. Its latched state is cleared through the approved FOC-to-stop transition or reset/power cycle, not the error-clear operation. A fault log must retain all asserted bits and supply/temperature context before any recovery. [Motor Fault Handling](https://doc-cdn.unitree.com/30/1299/en/30_1299_en) [Motor configuration](https://doc-cdn.unitree.com/30/1378/en/30_1378_en)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

The [IM6014 resource summary](https://doc-cdn.unitree.com/30/1384/en/30_1384_en) directly lists the model-specific assistant, USB driver, STM32, Python and C++ examples, motor CAD and fixed-structure drawings. Those are upstream resources, not packages verified or executed by OpenELAB. The Quick Start and summary point to different assistant ZIP URLs without a verified semantic version; obtain an exact model/revision answer rather than choosing an archive by date. [Quick Start](https://doc-cdn.unitree.com/30/1381/en/30_1381_en) [Data Download](https://doc-cdn.unitree.com/30/1384/en/30_1384_en)

The dedicated [C++ API chapter](https://doc-cdn.unitree.com/30/1380/en/30_1380_en), [Python chapter](https://doc-cdn.unitree.com/30/1379/en/30_1379_en), [STM32 chapter](https://doc-cdn.unitree.com/30/1377/en/30_1377_en), [protocol](https://doc-cdn.unitree.com/30/1383/en/30_1383_en), [fault table](https://doc-cdn.unitree.com/30/1299/en/30_1299_en) and [mounting instructions](https://doc-cdn.unitree.com/30/1302/en/30_1302_en) were read as text. CAD, executables, firmware and referenced archive contents were listed only. Downloading and testing them is a separate integration activity.

### Direct upstream resource links (listed only) <a href="#direct-upstream-resource-links-listed-only" id="direct-upstream-resource-links-listed-only"></a>

These resource targets are preserved from the read articles. None of the following file contents was opened or executed; a link is not a compatible-package recommendation.

* [CAN to 485 Protocol Document](https://oss-global-cdn.unitree.com/static/5795e9ce313b4dcfb4f0e9ad7f2c9e35.pdf) — [listing chapter](https://doc-cdn.unitree.com/30/1626/en/30_1626_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/a14bc99cfd6842b78120150494fa639f.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).
* [Quick Start resource](https://oss-global-cdn.unitree.com/static/d91f3e33a11446189092696f04462cef.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1381/en/30_1381_en).
* [Software and Control Design for the MIT Cheetah Quadruped Robots](https://oss-global-cdn.unitree.com/static/1cc5acc6389441ada2883dc627d75c4e.pdf) — [listing chapter](https://doc-cdn.unitree.com/30/1382/en/30_1382_en).
* [Learning Unified Force and Position Control for Legged Loco-Manipulation](https://oss-global-cdn.unitree.com/static/422487dc4ff64f8baad16ad229f19c19.pdf) — [listing chapter](https://doc-cdn.unitree.com/30/1382/en/30_1382_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/a0542aa67f4b4b1f9095682e4c5c3292.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/953db01bd5ac41588dccca9307475e93.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/bd68bae979024bba9bb1a9add90eac0f.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/2050f36b02de459ab425eb464b2317b3.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/3f6a975c71384113b9fd83239c40c756.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/719b81237a394dd5938ad15e758e684a.zip) — [listing chapter](https://doc-cdn.unitree.com/30/1384/en/30_1384_en).

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The [manufacturer IM6014 range page](https://www.unitree.com/IM6014) and every substantive chapter in the selected [IM6014 English portal space](https://support.unitree.com/home/en/Motor_IM6014%20Development%20Guide/about_IM6014) were read from actual cached article responses. The two empty Development Guide/example nodes contain no additional technical instructions. Interface and wiring figures were visually inspected. This is original English synthesis, with short factual tables and an original offline decoder; upstream text, imagery and binary archives retain their owners' rights.

Validation covers original synthetic examples and static document checks only. No Unitree package was installed, imported, built or executed, and there was no serial, DDS, ROS, hardware or firmware test. Supply range, assistant archive version and exact delivered firmware behavior remain open engineering items. Readiness: **draft for independent review**, not hardware-qualified. References throughout this page link to the actual read articles rather than claiming access to all 628 portal articles.

### Read source catalog <a href="#read-source-catalog" id="read-source-catalog"></a>

| Actual read primary chapter                                                    | Treatment on this page                                                                                                                           |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| [About IM6014](https://doc-cdn.unitree.com/30/1371/en/30_1371_en)              | Power, curve conditions, dimensions, interface and purchasing identity                                                                           |
| [Motor Overview](https://doc-cdn.unitree.com/30/1375/en/30_1375_en)            | Integrated motor/FOC/encoder concepts; output reference boundary                                                                                 |
| [Line connection](https://doc-cdn.unitree.com/30/1367/en/30_1367_en)           | Materials, high-speed adapter, common reference and equivalent ports                                                                             |
| [CAN to 485 Module](https://doc-cdn.unitree.com/30/1626/en/30_1626_en)         | Adapter ID/rate/UART/AT functions with unresolved exact model and linked PDF                                                                     |
| [Development Guide](https://doc-cdn.unitree.com/30/1368/en/30_1368_en)         | Empty container; no additional instructions                                                                                                      |
| [Quick Start](https://doc-cdn.unitree.com/30/1381/en/30_1381_en)               | Driver/GUI entry and active torque/speed/position hazards; source error qualified                                                                |
| [Control Mode](https://doc-cdn.unitree.com/30/1382/en/30_1382_en)              | Hybrid fields, proportional steady-state error, outer PI loops and unit corrections                                                              |
| [Motor configuration](https://doc-cdn.unitree.com/30/1378/en/30_1378_en)       | ID/firmware/baud, factory and high-precision startup, bootloader/fault recovery                                                                  |
| [Motor Protocol](https://doc-cdn.unitree.com/30/1383/en/30_1383_en)            | Frame lengths, field offsets/scales, rotor conversion, CRC and reserved-word boundary                                                            |
| [Motor Fault Handling](https://doc-cdn.unitree.com/30/1299/en/30_1299_en)      | Bitmask/warning, clear/reset/power timing and timeout separation                                                                                 |
| [example](https://doc-cdn.unitree.com/30/1376/en/30_1376_en)                   | Empty example container; children individually covered                                                                                           |
| [STM32 Example](https://doc-cdn.unitree.com/30/1377/en/30_1377_en)             | MCU, transceiver pins, active reference routine and parameters                                                                                   |
| [Python Example](https://doc-cdn.unitree.com/30/1379/en/30_1379_en)            | Python/serial dependency, example context and command-coordinate boundary                                                                        |
| [C++ Example](https://doc-cdn.unitree.com/30/1380/en/30_1380_en)               | Three API layers, connection/TX/async/protocol/special/parse/fault/cache/control/CLI responsibilities, dependencies and active periodic behavior |
| [Motor Debugging Assistant](https://doc-cdn.unitree.com/30/1306/en/30_1306_en) | Five areas, model/display conversion, traces/refresh/scale/zoom and driver-specific latency                                                      |
| [Structure Installation](https://doc-cdn.unitree.com/30/1302/en/30_1302_en)    | Light/static wire-ring/adhesive versus rated heavy clamp; no invented bolt torque                                                                |
| [Data Download](https://doc-cdn.unitree.com/30/1384/en/30_1384_en)             | Each linked package/CAD resource listed; no archive read/execution; no firmware update/version assurance                                         |
| [FAQ](https://doc-cdn.unitree.com/30/1385/en/30_1385_en)                       | All24 FAQ topics grouped explicitly; fault/timeout/velocity-gain boundaries                                                                      |

**Related documentation:** [Unitree model and development directory](./).
