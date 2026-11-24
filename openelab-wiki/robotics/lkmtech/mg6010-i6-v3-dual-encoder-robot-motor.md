---
description: >-
  Identify MG6010 versus MG6010E, reconcile legacy CAN/RS485 sales options, read
  exact drive information and decode CAN V2.35 status before motion.
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

# MG6010-i6 V3 Dual Encoder Robot Motor

{% hint style="info" %}
[**View MG6010-i6 V3 dual-encoder robot motor on OpenELAB**](https://openelab.io/products/mg6010-i6-v3-dual-encoder-robot-motor?variant=44578665758918)

**Original sales SKU:** `TB-LKM-MG6010-i6C` · **Identity check required:** current CAN/RS485 SKUs and the manufacturer's MG6010 versus MG6010E distinction

**Current verified CAN listing:** `LKM-MG6010-i6-CAN`. This identifies the current store option only; the original sales-row code remains an unconfirmed alias.
{% endhint %}

## Product overview

### MG6010-i6 V3 Dual Encoder Robot Motor <a href="#mg6010-i6-v3-dual-encoder-robot-motor" id="mg6010-i6-v3-dual-encoder-robot-motor"></a>

### Description <a href="#description" id="description"></a>

The manufacturer's **MG6010E-i6 V3** is a 6:1 integrated servo actuator with an 18-bit motor encoder and 14-bit reducer encoder. Its documented output is 5 N·m rated and 10 N·m maximum, with separate 24 V and 48 V performance columns. This guide covers identifying the delivered option, reading its drive information and interpreting a versioned status capture before active control. [Official MG6010E product and technical images](http://en.lkmotor.cn/ProDetail.aspx?ProId=268).

**Resolve the exact identity first.** The original workbook calls this `TB-LKM-MG6010-i6C`; the current store selector instead shows `LKM-MG6010-i6-CAN` and an RS485 option. Its title omits “E” while its description says MG6010E and dual encoder. LK itself has separate [MG6010-i6](http://en.lkmotor.cn/ProDetail.aspx?ProId=269) and [MG6010E-i6](http://en.lkmotor.cn/ProDetail.aspx?ProId=268) pages. No observed manufacturer/store alias establishes the legacy SKU's interface or E revision. Obtain the delivered label, order option and drive Read Info before treating this as CAN or dual encoder. A trailing “C” alone is insufficient evidence.

### Product Link <a href="#product-link" id="product-link"></a>

The original [OpenELAB product URL](https://openelab.io/products/mg6010-i6-v3-dual-encoder-robot-motor) is retained. Its CAN default does not verify an older order's option. Do not create a separate duplicate wiki for the same store model while that naming is reconciled.

## Applications

Potential uses include supported robot arms, rotary fixtures and mobile mechanisms. Check continuous output torque at operating speed, acceleration and impact peaks, bearing load, cooling and duty cycle. The no-load speed is not a loaded operating point, and two encoders do not eliminate gear backlash.

Preserved single-turn position is different from a retained multi-turn joint coordinate. A gravity-loaded joint also needs mechanical support independently of motor holding torque. No brake or certified safety-stop function is established for this sales row.

## Specifications

### Specification <a href="#specification" id="specification"></a>

The following table applies to the **MG6010E-i6 V3 manufacturer's current model image**, not an unidentified MG6010 or another DG drive.

| Parameter                      | 24 V column             | 48 V column |
| ------------------------------ | ----------------------- | ----------- |
| Rated / maximum output torque  | 5 / 10 N·m              | 5 / 10 N·m  |
| Rated output speed             | 170 rpm                 | 391 rpm     |
| Maximum output speed           | 251 rpm                 | 505 rpm     |
| Rated current                  | 5.5 A                   | 5.3 A       |
| Published maximum power        | 120 W                   | 400 W       |
| Motor-side KV / KT             | 62.9 rpm/V / 0.16 N·m/A | Same        |
| Rotor inertia / magnetic poles | 805 g·cm² / 28 poles    | Same        |

[Inspected official MG6010E parameter image](http://en.lkmotor.cn/upload/image/20230323/6381518793281490231438589.jpg). “28 poles” means 14 pole pairs if a tool asks for pairs; do not enter 28 into a pairs field. The current image also specifies PG4106, 1:6, ≤6 arcmin backlash, 900 N bearing-rated load, 343 g mass and recommended **DG60Ev2**, 12–60 V drive input. A motor's 24/48 V performance columns and a drive's allowable input range serve different purposes.

### Feature <a href="#feature" id="feature"></a>

| Identity / interface    | Exact distinction                                              |
| ----------------------- | -------------------------------------------------------------- |
| MG6010-i6 V3            | Manufacturer's single-encoder model                            |
| MG6010E-i6 V3           | Motor 18-bit + reducer 14-bit; E identifies the extra encoder  |
| CAN option              | Differential CAN interface; model image lists up to 1 Mbit/s   |
| RS485 option            | Differential RS485 interface; model image lists up to 2 Mbit/s |
| UART service connection | Separate G/R/T setup interface; not the RS485 bus              |

[Manufacturer's encoder comparison](http://en.lkmotor.cn/upload/image/20230331/6381587365198844021668272.jpg), [model parameter image](http://en.lkmotor.cn/upload/image/20230323/6381518793281490231438589.jpg). The old combined “up to 2 Mbps” wording must not be applied to CAN. Protocol update frequency, bus bit rate, encoder bit depth and achievable mechanical accuracy are separate quantities.

The earlier distributor-hosted OEM catalog's C8 sheet contains a conflicting 1217 g mass and ≤8 arcmin reference. The current official model image supports 343 g and ≤6 arcmin. Keep the exact drawing/revision with a mechanical acceptance record rather than averaging the figures. [Older OEM catalog, C8](https://teika-machine.co.jp/wp-content/uploads/2024/09/%E4%B8%8A%E6%B5%B7%E7%93%B4%E7%A9%BA%E7%A7%91%E6%8A%80%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8%E3%80%80%E6%96%B0%E3%82%AB%E3%82%BF%E3%83%AD%E3%82%B0.pdf).

## Hardware and connections

![LK MG6010E-i6 manufacturer interface definition, with separate UART and power/bus labels](http://en.lkmotor.cn/upload/image/20230331/6381587365205100455181597.jpg)

Original LK-TECH interface illustration from the [exact MG6010E page](http://en.lkmotor.cn/ProDetail.aspx?ProId=268), visually inspected. The housing drawing shows G/R/T service labels, V+/V− power and two bus connectors. Match this view to the actual connector-facing orientation before wiring; do not mirror it into a cable-side pin order.

| Marking | Manufacturer definition and connection boundary                                 |
| ------- | ------------------------------------------------------------------------------- |
| V+ / V− | Positive / negative actuator supply; confirm keyed XT30 polarity with power off |
| A/H     | RS485-A **or** CAN-H, according to installed interface                          |
| B/L     | RS485-B **or** CAN-L, according to installed interface                          |
| G       | Service signal ground                                                           |
| R       | UART receiver into the drive; connect the matched adapter TX                    |
| T       | UART transmitter from the drive; connect the matched adapter RX                 |

The drawing does not establish universal 5 V logic tolerance or make RS485/CAN contacts compatible with USB-TTL GPIO. Use the matched service adapter and harness. Two bus sockets enable a bus connection; they do not prove simultaneous CAN and RS485 support.

1. Photograph the complete motor and drive markings, connector labels and option label. Leave the power disconnected while reconciling MG versus MGE and the legacy SKU.
2. Fixture the unloaded housing and support any attached link. Keep the whole possible path, including return to zero, clear. Establish independent physical power isolation.
3. Match V+/V−, G/R/T and A/H/B/L to the exact board/harness. Use the current model's 24 V or 48 V performance context and its approved drive input, rather than selecting a supply from another MG model.
4. Establish the actual bus type and stored bit rate before connecting a host. A UART service tool, RS485 adapter and CAN adapter serve different ports.
5. For a confirmed CAN/RS485 chain, terminate the two physical ends as documented, assign unique IDs and begin with one node. Record the original switch state before changing ID or termination.

The inspected [MG6010E installation drawing](http://en.lkmotor.cn/upload/image/20230323/6381518793284617393195252.jpg) shows a roughly Ø76 mm body and 38.5 mm plus 0.5 mm axial dimensions. Read the full drawing's datums, tolerances and blind-hole depths when choosing brackets and screws; the approximate Ø76 × 39 mm envelope is not a fabrication drawing.

Original native figures are retained:

<figure><img src="../../.gitbook/assets/image (1081).png" alt="Retained MG6010 product illustration"><figcaption><p>Original product figure; identify the delivered E and interface revision.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1082).png" alt="Retained MG6010 engineering illustration"><figcaption><p>Original manufacturer/store technical reference.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1083).png" alt="Retained MG6010 specification graphic"><figcaption><p>Use the current model-scoped specifications above when values differ.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1084).png" alt="Retained MG6010 drawing or performance reference"><figcaption><p>Original engineering reference retained.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1085).png" alt="Retained MG6010 manufacturer illustration"><figcaption><p>Original native asset retained.</p></figcaption></figure>

## Software and development resources

The retained MG60 package contains **LK Motor Tool V2.36**, CAN and RS485 V2.35 protocol PDFs, matching C/text command references and a CP210x driver archive. Those filenames are an inventory, not proof that every included example is correct for every V3 unit. Its nominal “MG servo motor manual V2.36” still describes **MGv2 and DG80R/C7**, and its screenshots describe V2.33. Use it for the documented UI workflow, while obtaining exact DG60E firmware/parameter support for the delivered board. [Retained original MG60 package](../../.gitbook/assets/MG60.zip).

### State and protocol boundaries

| Reference                | Useful scope                                                                                                                                             |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CAN V2.35                | Standard 11-bit, eight-byte messages, base ID `0x140 + motor ID`; default 1 Mbit/s in this document                                                      |
| RS485 V2.35              | Distinct header/checksum framing and fields; do not send a CAN payload directly to a serial port                                                         |
| `0x9A` CAN status1       | Temperature, voltage and fault byte; suitable for interpreting a confirmed version's capture                                                             |
| `0x80` / `0x81` / `0x88` | Off / stop / on have different state effects; off clears accumulated position/previous command in the protocol, stop retains state, on enables operation |
| `0xA1` torque control    | Not a passive current query; the documented current command is not necessarily bounded by the host's Max Torque Current setting                          |

[Official CAN V2.35](http://en.lkmotor.cn/upload/20230706100134f.pdf), [official RS485 V2.35](http://en.lkmotor.cn/upload/20230706100146f.pdf). The CAN document describes power-on as motor-on state. Thus merely choosing not to transmit does not establish a de-energized output. Treat startup configuration, host lifecycle and power isolation as separate commissioning questions.

The service tool's Read, SET/RAM, Save/ROM, Align, zero-setting and firmware Download operations are materially different. Read and archive Product information and parameters first. Align rotates the motor and saves results; firmware update is documented to trigger automatic calibration afterward. Clear reducer alignment, Set Zero and off-state commands can alter the coordinate reference used by an attached mechanism. Do not include them in discovery.

The public resources establish a Windows tool and wire protocols; they do not establish a current official Python/ROS package compatible with every MG6010 V3 firmware. A third-party wrapper's API name is not a substitute for checking the on-wire version. Keep OS/tool version, firmware, ID, baud, raw packets, units and configuration backups with the project.

## Getting started

### First result: reconcile identity and read drive information

**Before powering or connecting:** secure the unloaded motor, support links and clear the full possible motion/return path. The documented drive can be on after power-up, Align and firmware completion can move it, and normal host disconnect/Ctrl+C is not verified instantaneous stationary torque-off. Provide physical isolation independently; do not use an undocumented flag to bypass this boundary.

1. Confirm the order option and exact physical label against MG6010E, MG6010 and the current store selector. If legacy SKU mapping is unresolved, keep the actuator unpowered and request the mapping with those identifiers.
2. For an identified supported unit, connect the matched USB-UART service adapter and separate supply as documented. In LK Motor Tool choose the adapter's COM port, documented service rate (115200 in the retained workflow) and the known drive ID. Do not scan by sending control commands.
3. Open **Product → Read Info**. Record motor name/version, drive name, hardware revision, firmware and chip identifier. A displayed MG8016/DG80 example is not the expected identity of this motor.
4. On **Setting** and **Encoder**, use **Read** to capture the existing bus type/rate, ID, reduction and encoder configuration. Do not press Align, Set, Clear, Save, Download, Motor On or a Test Send control.
5. Once the installed protocol is confirmed, use the tool's **Read State1** and retain its raw TX/RX and displayed temperature/voltage/fault state. Cross-check supply voltage independently. A read request alone is not a successful reply.

**Expected result:** a product/drive/firmware identity record, original configuration readback, and a plausible state response for the confirmed interface. If the reported model or interface differs, preserve that observation and stop before active testing. Do not overwrite settings to make the display resemble the store description. [MG60 package's UI and state workflow](../../.gitbook/assets/MG60.zip), [manufacturer tool/encoder illustration](http://en.lkmotor.cn/upload/image/20230331/6381587365222282323895983.jpg).

### Original offline CAN status1 decoder

This Python 3.10+ example sends no frames. Use it only for an eight-byte **CAN V2.35 `0x9A` reply** after the model/protocol has been identified. RS485 voltage scaling differs and is deliberately excluded. Save as `mg6010_status1.py`.

```python
import argparse
import json

p = argparse.ArgumentParser()
p.add_argument("identifier", type=lambda x: int(x, 0))
p.add_argument("payload")
a = p.parse_args()
if not 0x141 <= a.identifier <= 0x160:
    p.error("expected CAN V2.35 ID 0x140 + motor ID 1..32")
try:
    data = bytes.fromhex(a.payload)
except ValueError:
    p.error("invalid hexadecimal data")
if len(data) != 8 or data[0] != 0x9A:
    p.error("expected eight-byte CAN V2.35 status1 reply")
error = data[7]
print(json.dumps({
    "motor_id": a.identifier - 0x140,
    "temperature_C": int.from_bytes(data[1:2], "little", signed=True),
    "bus_voltage_V": int.from_bytes(data[3:5], "little") * 0.1,
    "raw_error": f"0x{error:02x}",
    "undervoltage_bit": bool(error & 0x01),
    "overtemperature_bit": bool(error & 0x08),
    "other_error_bits": f"0x{error & 0xF6:02x}"
}, indent=2))
```

```sh
python3 mg6010_status1.py 0x141 9a1900f000000000
```

The **synthetic** result is ID 1, 25 °C, 24.0 V and raw error `0x00`. Zero decoded faults do not prove an unloaded, disabled or correctly calibrated motor. Unknown bits remain visible rather than being discarded. [CAN V2.35, status1 definition](http://en.lkmotor.cn/upload/20230706100134f.pdf).

For later control development, define the shaft domain for every quantity before calculating a target. A motor-side angle of 60° corresponds geometrically to 10° output through 6:1 reduction, but only use that conversion for fields explicitly defined as motor-side. Do not rescale an output-encoder field a second time, treat a truncated CAN encoder field as the full 18-bit raw sensor, or convert raw current to amperes without the exact drive's documented current scale.

## Troubleshooting and FAQs

| Observation                                       | Diagnosis before changing persistent state                                                                                                |
| ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Tool cannot connect                               | Confirm UART service port versus CAN/RS485 bus, matched USB-UART driver/harness, actual COM/rate/ID and separate supply                   |
| Store says dual encoder but readback lacks it     | Compare E suffix and physical driver/encoder assembly; resolve the SKU/option discrepancy before assuming a firmware defect               |
| Speed wrong by × 6                                | Check motor/output units and whether the displayed value is already reduced; verify the actual 6:1 setting before changing gains          |
| CAN silent while UART works                       | Read stored bus type/rate/ID; distinguish 1 Mbit/s CAN from 2 Mbit/s RS485; inspect topology/termination                                  |
| Fault indicator persists                          | Record status and raw error first; fix supply, temperature, wiring or load before considering clear/restart                               |
| Position jumps after off/reboot                   | Compare retained single-turn feedback, multi-turn accumulation and documented off-state clearing; support the mechanism before recovering |
| Upgrade appears to finish and motor starts moving | Automatic calibration is documented; isolate/support, preserve logs and follow exact firmware support instructions                        |

**Can I reuse a DG40 or DG80 pin/rating table?** Not as proof of this DG60E assembly. The exact product's interface illustration and drive label take precedence over a generic manual bundled with several models.

**Are all GUI protections implemented?** The retained manual explicitly marks several protection/settings entries unavailable. A visible control or checkbox is not evidence of enforcement. Confirm the actual firmware feature and hardware protection before relying on it.

**Can I recover by uploading any “MG” binary?** No. Read Info, back up configuration and obtain a binary matching model, encoder, drive and hardware revision. Firmware change can recalibrate and alter zero; never attempt it on an unsupported or loaded joint.

## Downloads and technical documents

### Resource <a href="#resource" id="resource"></a>

{% file src="../../.gitbook/assets/MG60.zip" %}

| Resource                                                                                                                                           | Verified scope                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| [Official MG6010E model](http://en.lkmotor.cn/ProDetail.aspx?ProId=268) and [single-encoder MG6010](http://en.lkmotor.cn/ProDetail.aspx?ProId=269) | Distinct products; model images read/inspected                                                         |
| [Current parameter image](http://en.lkmotor.cn/upload/image/20230323/6381518793281490231438589.jpg)                                                | 24/48 V performance, DG60Ev2, 18+14-bit, dimensions/mass context                                       |
| [Installation and curves](http://en.lkmotor.cn/upload/image/20230323/6381518793284617393195252.jpg)                                                | Inspected mounting and motor-performance plots; raw plot speed is not automatically output rpm         |
| [Official CAN V2.35 PDF](http://en.lkmotor.cn/upload/20230706100134f.pdf)                                                                          | Full command inventory, state effects, units and status fields                                         |
| [Official RS485 V2.35 PDF](http://en.lkmotor.cn/upload/20230706100146f.pdf)                                                                        | Separate serial framing/checksums; not substituted into the CAN example                                |
| [Official CAD list](http://en.lkmotor.cn/Download.aspx?ClassID=49)                                                                                 | Model-labelled STEP resources; confirm E/revision before fabrication                                   |
| [Official software list](http://en.lkmotor.cn/Download.aspx?ClassID=45)                                                                            | Tool releases; existing MG60 native archive additionally contains V2.36 executable and command samples |

The original package and native figures remain attached to this canonical page. Manuals and command references are manufacturer-authored; no blanket reproduction license is asserted, and executables/C examples were not run. No exact current MG6010E firmware binary or supported modern robotics SDK release was independently verified.

## References and validation

Sources and relevant engineering images were reviewed on 24 November 2026. The current official MG6010E images establish clearer model/pin/performance information than the generic MGv2 manual inside the legacy package. Remaining blockers are the old SKU alias, MG/MGE sales identity and exact delivered drive/firmware applicability. The offline parser is an original diagnostic aid, not a hardware result. Software/SDK/firmware execution and hardware tests were **not run**.

Related canonical guides: [LK MG dual-encoder V3 family](lkmtech-mg-dual-encoder-v3-development-guide.md) and [MG4010E-i10](mg4010e-i10-v3-dual-encoder-robot-motor.md). Compare their exact model/drive tables before reusing a procedure.
