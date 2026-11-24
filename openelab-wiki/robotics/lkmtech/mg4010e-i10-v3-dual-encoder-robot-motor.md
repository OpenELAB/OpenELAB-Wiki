---
description: >-
  Read MG4010E-i10 V3 identity and status, distinguish CAN/RS485 units and
  encoder revisions, and check the10:1 rated operating point offline.
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

# MG4010E-i10 V3 Dual Encoder Robot Motor

{% hint style="info" %}
[**View MG4010E-i10 V3 Dual Encoder Robot Motor options on OpenELAB**](https://openelab.io/products/mg4010e-i10-v3-dual-encoder-robot-motor?variant=44578396963014)

**Model:** MG4010E-i10 V3 · **Historical ordering code:** `TB-LKM-MG4010E-i10C` · **Current options:** `LKM-MG4010E-i10-CAN` / `LKM-MG4010E-i10-RS485`

The historical code is absent from current variants; its exact CAN/RS485 alias is unconfirmed. Select the bus from the order/received label, not the suffix or a shared connector.

**Current verified CAN listing:** `LKM-MG4010E-i10-CAN`. This identifies the current store option only; the original sales-row code remains an unconfirmed alias.
{% endhint %}

## Product overview

### MG4010E-i10 V3 Dual Encoder Robot Motor <a href="#mg4010e-i10-v3-dual-encoder-robot-motor" id="mg4010e-i10-v3-dual-encoder-robot-motor"></a>

MG4010E-i10 V3 is an integrated brushless motor/drive with 10:1 planetary gearing and dual-encoder feedback. Manufacturer literature gives 2.5 N·m rated and 4.5 N·m maximum output torque at a 24 V nominal operating reference. The first integration result should be model/firmware identity and readable status. Do not substitute the slower [MG4010E-i36 configuration](lkmtech-mg-dual-encoder-v3-development-guide.md) or its position scaling. [OEM catalog extract](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf), [manufacturer software/protocol center](http://en.lkmotor.cn/Download.aspx?ClassID=47).

### Product Link <a href="#product-link" id="product-link"></a>

The model page above is verified, but current interface SKUs differ from the historical order code. CAN, RS485 and the separate setup UART have different electrical roles. A configurable baud rate does not mean software can change the hardware bus type; the MG40–50 manual explicitly says bus-type selection is unavailable in its documented host. [OEM MG40–50 manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

### Description <a href="#description" id="description"></a>

The “E” denotes dual encoders; a “B” configuration adds a brake. The second encoder can support reducer/output feedback, but encoder resolution, backlash and final joint accuracy are separate. This guide retains the existing manufacturer files and adds a read-first workflow, a revision/scaling comparison and an original offline load/power check.

## Applications

Use this 10:1 version for a compact robot joint, rotating mechanism or mobile-platform axis when its torque-speed envelope fits the load cycle. Check output-bearing forces and bending moments independently of torque. An application name such as exoskeleton or quadruped is not a mechanical-load or human-safety approval.

A 36:1 unit may produce more output torque at less speed, but its gearbox, mass and shaft scaling differ. Do not import its parameters or rescale an absolute position command using an assumed ratio. [Exact-model OEM data](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf).

## Specifications

### Feature <a href="#feature" id="feature"></a>

| Parameter                                  | MG4010E-i10 V3 manufacturer reference                                                |
| ------------------------------------------ | ------------------------------------------------------------------------------------ |
| Nominal voltage / recommended driver range | 24 V / 7.4–32 V for the catalog's DG40 configuration                                 |
| Rated / maximum output torque              | 2.5 / 4.5 N·m                                                                        |
| Rated / maximum output speed               | 260 / 320 rpm                                                                        |
| Rated current / maximum power              | 3.5 A / 140 W; maximum power is a separate operating-condition reference             |
| Reduction / gearbox                        | 10:1 / PG4210                                                                        |
| Backlash / bearing rated load              | ≤8 arcmin / 1000 N; not a lever-arm payload rating                                   |
| Mass / rotor inertia                       | 250 g / 202 g·cm²                                                                    |
| Phase resistance / inductance              | 0.604 Ω / 0.28 mH in the later OEM sheet                                             |
| Motor KV / KT                              | 108.3 rpm/V / 0.07 N·m/A; retain motor-side versus output-side units                 |
| Feedback in the OEM sheet                  | 18-bit motor + 14-bit reducer magnetic encoders                                      |
| Interfaces                                 | Separate CAN or RS485 product options, plus setup UART on documented drive revisions |
| Catalog control-loop references            | Torque 24 kHz, speed 8 kHz, position 4 kHz; not host-command/update rates            |

[Read OEM MG4 catalog, first page](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf). The original store/wiki table describes 18-bit **both** encoders, while this OEM sheet says 18+14. The received drive's **Encoder → Read** result and matching revision sheet must resolve that difference before converting raw output counts to angle or advertising an accuracy figure.

### Specification <a href="#specification" id="specification"></a>

At the stated rated output point, mechanical power calculated as `torque × angular_speed` is approximately **68.1 W** (`2.5 ×260 ×2π/60`). This calculation checks units; it is not a measured efficiency or a claim that the manufacturer's 140 W maximum-power figure occurs at the rated torque/speed point. Likewise, multiplying maximum torque by maximum speed assumes a simultaneous operating point that the table does not establish.

The existing specification graphics are retained here with their original file IDs:

<figure><img src="../../.gitbook/assets/image (1078).png" alt="Existing MG4010E-i10 V3 manufacturer illustration"><figcaption><p>Original manufacturer/product illustration retained; received revision and units take precedence over an unqualified image caption.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1079).png" alt="Existing MG4010E-i10 V3 technical illustration"><figcaption><p>Original technical illustration retained. Use the model-matched drawing for mounting and fastener engagement.</p></figcaption></figure>

## Hardware and connections

### Match the actual drive and harness

The detailed [MG40–50 manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>) shows **DG40R/C7**, whereas the model catalog calls its recommended drive **DG40**. Verify the received label before using a physical connector-order diagram. Do not silently equate a family drive name with a connector revision.

| Label     | Electrical role                                                         |
| --------- | ----------------------------------------------------------------------- |
| V+ / V−   | Drive supply positive/negative; repeated cavities can share these rails |
| A/H       | RS485-A or CAN-H, according to the actual hardware option               |
| B/L       | RS485-B or CAN-L, according to that option                              |
| T / R / G | Separate setup UART TX / RX / signal ground                             |

For **the DG40R/C7 orientation shown on manual p. 5 only**, the six-pin drawing is V+, V+, V−, V−, A/H, B/L and the separate three-pin drawing is G, R, T. The connector families shown are ZH1.5 six-pin and MX1.25 three-pin. Check the keyed **board-side** view; cable-side views are mirrored. No universal UART 5 V tolerance is established here, so use the matched LK interface. The UART is not RS485/CAN merely because both are serial communication. [Inspected OEM pinout](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

1. Fixture one unloaded motor, disconnect other controllers and support any linked mechanism against torque loss. Clear the entire possible movement/return path.
2. With power off, verify model/driver, supply polarity and the actual label's voltage range. Do not power an unresolved harness from a photograph alone.
3. Wire the matching setup UART interface separately from the motor DC supply. USB powers the interface, not the motor.
4. If using CAN/RS485, use the correct transceiver and end-of-bus termination, not a direct MCU GPIO connection. Start with one node and its known ID to avoid duplicate replies.
5. Keep a physical means of isolating drive power accessible. CAN V2.35 describes an on state after power-up; read-only software requests do not by themselves guarantee a torque-off physical state.

[OEM connection/host manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>), [CAN V2.35 power/control-state description](http://en.lkmotor.cn/upload/20230706100134f.pdf).

## Software and development resources

The official [software center](http://en.lkmotor.cn/Download.aspx?ClassID=45) lists LK Motor Tool V2.35, V2.33 and V2.32. The retained MG40–50 manual illustrates V2.35 with **Product/Setting/Encoder/Test** pages. Match the received firmware; a currently listed executable is not proof of compatibility with every historical board.

The [CAN V2.35 PDF](http://en.lkmotor.cn/upload/20230706100134f.pdf) uses standard 11-bit CAN identifiers `0x140 + ID` and 8-byte payloads. Its [RS485 counterpart](http://en.lkmotor.cn/upload/20230706100146f.pdf) uses `0x3E` framing, command/header checksum, optional data and data checksum. Their status1 voltage scales differ: **CAN 0.1 V/count, RS485 0.01 V/count**. They also have different field layouts; a copied decoder can produce plausible-looking wrong values.

On LK Tool, **Read Setting**, **Read Info** and **Encoder → Read** are distinct from parameter writes, Align, zero-setting and firmware Download. Some documented protection fields are unavailable in the corresponding software. The CAN torque-command documentation says `0xA1` is not constrained by the host's Max Torque Current setting. Preserve complete readback/settings before deliberate changes; do not treat one UI limit as an independent torque safety mechanism. [MG40–50 parameters/protection manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>), [CAN torque-command scope](http://en.lkmotor.cn/upload/20230706100134f.pdf).

## Getting started

### Product identity and state before motion

1. Resolve the historical ordering code to the received **CAN or RS485 option**, and match its drive/harness. If the label or encoder variant is unclear, retain this as an identification task and do not proceed with assumed wiring or angle scaling.
2. On an unloaded, supported fixture, wire the verified supply and the matching setup UART interface with power off. Then apply the unit's supported supply and connect host USB.
3. Open the matched LK Tool, select the actual COM port and known stored baud/ID. The documented untouched-unit defaults are 115200 baud and ID 1; do not rewrite an existing unit to force those defaults. Click **CONNECT**.
4. Open **Product → Read Info**, compare motor/drive/hardware/firmware and retain the results. Open **Setting → Read Setting** and **Encoder → Read**. Resolve the 18+14 versus 18+18 discrepancy before interpreting reducer counts.
5. In **Test**, use **Read State1** and **Read State2**. Save temperature, bus voltage, error byte and raw feedback. Do not click Motor On, Send, Align, clear loops, set zero or firmware Download during this baseline.

**Expected result:** a repeatable identity/state read and saved baseline for the exact 10:1 unit, without transmitting a movement target. A lit/green interface or open port alone does not verify the motor. [OEM host procedure, pp. 8–14](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

For a separately confirmed CAN/V2.35 interface, the [family guide's read-only CAN status1 procedure and decoder](lkmtech-mg-dual-encoder-v3-development-guide.md) applies only after matching bitrate, ID and firmware. Its payload example is synthetic. Do not use RS485 voltage scaling in that CAN decoder.

### Original offline comparison of operating points

Save this original Python 3 example as `inspect_mg4010_operating_points.py`. It performs a calculation only; it does not connect to a drive or generate a motion command.

```python
from math import pi

rated_torque_nm = 2.5
rated_speed_rpm = 260.0
max_torque_nm = 4.5
max_speed_rpm = 320.0
reduction = 10.0

rated_omega = rated_speed_rpm * 2 * pi / 60
print(f'Rated-point mechanical calculation: {rated_torque_nm * rated_omega:.1f} W')
print(f'Rated output speed: {rated_speed_rpm:.1f} rpm')
print(f'Ideal geometric motor speed: {rated_speed_rpm * reduction:.1f} rpm')
print('Maximum torque and maximum speed are separate references:',
      max_torque_nm, 'Nm;', max_speed_rpm, 'rpm')
print('Do not treat those maxima as a verified simultaneous operating point.')
```

Run `python3 inspect_mg4010_operating_points.py`. **Expected result:** a 68.1 W calculation and 2600 rpm geometric motor speed, accompanied by the explicit maximum-point caveat. These are derived values, not measured output, electrical input power or allowable continuous operation.

### Later controlled movement and maintenance

Before a small unloaded movement, confirm the actual firmware's shaft/angle units, direction, stored zero, current scaling and stop response. The MG40–50 Test manual describes **motor-shaft** degrees/second and degrees, with output values divided by the reduction ratio. For a 10:1 mechanism,100 motor degrees corresponds geometrically to 10 output degrees; verify whether the chosen API has already applied that conversion.

Support and clear the full path before enabling or issuing an absolute target. Do not use a large absolute-zero command as a communication test. `Motor Stop` and `Motor Off` have different state/turn-reset consequences in CAN V2.35; normal exit/Ctrl-C is not an independent emergency torque-off. **Align moves the motor back and forth, and the newer manual says firmware completion triggers automatic calibration.** Preserve the exact image/settings and use a no-load fixture before such maintenance. [OEM calibration/firmware/Test pages 12–14](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

## Troubleshooting and FAQs

| Symptom / question                           | Diagnosis and bounded recovery                                                                                                    |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Old SKU is not shown in the store            | Match model/interface with the received label and original order. Current option names are not a proven alias table.              |
| Dual encoder count looks wrong               | Resolve 18-bit motor versus 14-bit reducer and any truncated on-wire fields; retain raw values until confirmed.                   |
| Voltage is wrong by 10 ×                     | Check CAN versus RS485 framing/scaling before changing voltage settings.                                                          |
| Tool connects but Product identity differs   | Stop. Do not import this 10:1 motor's parameters into an i36 or another drive.                                                    |
| No status reply                              | Check supply, setup UART versus bus connector, adapter chip, stored baud/ID and bus termination/duplicate nodes.                  |
| Parameter disappears after restart           | Compare RAM write versus permanent Save/ROM workflow; read back before and after a deliberate restart.                            |
| Motor unexpectedly moves during an update    | Firmware completion can trigger calibration. Use an unloaded fixture and clear/support the mechanism before Download.             |
| Can the maximum torque be held indefinitely? | No continuous-duty result is established by a 4.5 N·m maximum. Check thermal and load-cycle limits at the actual operating point. |

## Downloads and technical documents

### Resource <a href="#resource" id="resource"></a>

| Original or current resource                                                                                                                                                             | Purpose / scope                                                                                      |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| [Official model/manual center](http://en.lkmotor.cn/Download.aspx?ClassID=21)                                                                                                            | Inspect model/driver revision; its MG V2.33 file identifies MGv2 and is not a blanket V3 replacement |
| [Official LK Tool V2.35](http://en.lkmotor.cn/upload/20230707104924f.zip)                                                                                                                | Manufacturer-listed host package; not executed                                                       |
| [Official CAN PDF](http://en.lkmotor.cn/upload/20230706100134f.pdf) / [RS485 PDF](http://en.lkmotor.cn/upload/20230706100146f.pdf)                                                       | Transport-specific frames, units, controls, status and parameter operations                          |
| [OEM exact-model catalog extract](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf) | First page's model/drawing reference, read                                                           |
| [Official 3D library](http://en.lkmotor.cn/Download.aspx?ClassID=49)                                                                                                                     | Match exact model/revision before manufacturing a bracket                                            |

Original model-specific attachments remain intact:

**3D model**

{% file src="../../.gitbook/assets/3D.zip" %}

**CAN controlling computer**

{% file src="../../.gitbook/assets/CAN Controlling Computer.zip" %}

**LK motor tool**

{% file src="../../.gitbook/assets/LK motor tool.zip" %}

**Firmware upgrade instruction**

{% file src="../../.gitbook/assets/Lk Motor firmware upgrade instrucion.pdf" %}

**LK CAN test-command reference**

{% file src="../../.gitbook/assets/LK test command-CAN.txt" %}

**MCF302CB CAN demo**

{% file src="../../.gitbook/assets/LK-demo-MCF302CB-CAN.zip" %}

**MG40–50 servo manual**

{% file src="../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf" %}

The host/manual and firmware note were read; existing program/demo/CAD attachments are preserved downloads, not software/hardware tests. The manufacturer manual's connection, host, IDs, protection/limits/PID, encoders, calibration, firmware and status topics are addressed above or in the linked family guide. Complete command layouts remain in the original protocol PDFs rather than being copied wholesale.

## References and validation

Reviewed **24 November 2026**: exact model catalog and live options, manufacturer download categories/CAN/RS485 PDFs, existing MG40–50 manual and upgrade instruction. Important DG40R/C7 connector/calibration pages were visually inspected. The historical SKU/interface alias and shipped reducer-encoder revision remain unresolved; these affect wiring/decoder sign-off.

**Validation:** source review and original calculation design. LK Tool/SDK installation, UART/CAN/RS485 exchange, firmware flashing, calibration, torque/current/position measurement and hardware movement were **not run**. Expected results are reproduction checkpoints. The calculated power point is not a measured motor result.
