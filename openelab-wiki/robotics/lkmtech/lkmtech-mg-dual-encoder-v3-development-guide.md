---
description: >-
  Compare MG4010E-i36, MG4005E-i10 and MG5010E-i10 V3; identify exact
  drive/interface, read status and decode CAN voltage without mixing RS485
  scaling.
---

# LKMTECH MG Dual-Encoder V3 Actuator Engineering Guide

{% hint style="info" %}
[**View MG4010E-i36 V3 options on OpenELAB**](https://openelab.io/products/mg4010e-i36-v3-dual-encoder-robot-motor?variant=44578459353286) · **Current CAN SKU:** `LKM-MG4010E-i36-CAN` · **Historical ordering code:** `TB-LKM-MG4010E-i36C`

[**View MG4005E-i10 V3 options on OpenELAB**](https://openelab.io/products/mg4005e-i10-v3-dual-encoder-robot-motor?variant=44574202855622) · **Current CAN SKU:** `LKM-MG4005E-i10-CAN` · **Historical ordering code:** `TB-LKM-MG4005E-i10C`

[**View MG5010E-i10 V3 options on OpenELAB**](https://openelab.io/products/mg5010e-i10-v3-high-torque-dual-encoder-drive-motor?variant=44573070491846) · **Current CAN SKU:** `LKM-MG5010E-i10-CAN` · **Historical ordering code:** `TB-LKM-MG5010E-i10C`

**Option boundary:** these exact model pages currently offer separate CAN and RS485 variants under new `LKM-…-CAN` / `LKM-…-RS485` SKUs. The historical-code-to-interface correspondence is not confirmed; verify the order and received label before choosing a bus or harness.
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

This guide covers three distinct **V3 dual-encoder geared motors**: MG4010E-i36, MG4005E-i10 and MG5010E-i10. Their 36:1/10:1 gearing, motor currents, torque/speed ratings and recommended drives differ. Shared protocol concepts do not make their wiring, parameter files or torque scaling interchangeable. The initial goal is **readable identity and status**, with motion, zero writes and firmware updates kept separate.

The existing [MG4010E-i10 guide](mg4010e-i10-v3-dual-encoder-robot-motor.md) and [MG6010-i6 guide](mg6010-i6-v3-dual-encoder-robot-motor.md) remain separate model guides. “E” identifies the dual-encoder configuration in the manufacturer naming scheme; “B” is a brake option, not another name for the same mechanism. [Manufacturer MG40–50 manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>), [manufacturer product categories](http://en.lkmotor.cn/Product.aspx?TypeID=18).

{% hint style="warning" %}
**MG5010E-i10 identity discrepancy:** the current store title/URL says i10, while its description includes 13/25 N·m, 54 rpm and an i36 gearbox. The manufacturer i10 catalog gives 4/7 N·m and 235 rpm. Those are not alternative ratings of one confirmed unit. Before powering or controlling a motor sold under the historical code above, obtain the received model/drive label and matching parameter sheet. The procedures below are conditional on that positive identification; no 13 N·m i10 motion profile is supplied.
{% endhint %}

## Applications

Choose MG4005E-i10 for a smaller joint where mass and speed matter, MG4010E-i36 for slower higher-reduction motion, and MG5010E-i10 for a larger 10:1 joint. Treat these as integration patterns, not payload guarantees. A robotic shoulder's moment, an AGV's wheel force and an exoskeleton's torque limit require different load-cycle and bearing calculations.

Two encoders provide motor/output feedback possibilities; they do not remove gearbox backlash, guarantee zero startup movement or establish permanent multi-turn retention. Use feedback domain, zero behavior and restart handling from the exact drive firmware. [OEM catalog, relevant model pages](https://teika-machine.co.jp/wp-content/uploads/2024/09/%E4%B8%8A%E6%B5%B7%E7%93%B4%E7%A9%BA%E7%A7%91%E6%8A%80%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8%E3%80%80%E6%96%B0%E3%82%AB%E3%82%BF%E3%83%AD%E3%82%B0.pdf).

## Specifications

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

The following values are **manufacturer catalog references**, with source/model pages kept together. They are not a sign-off for an unidentified shipped revision. PDF page numbers below are file pages, not marketing-page numbering.

| Parameter                       | MG4005E-i10 V3, PDF p. 52     | MG4010E-i36 V3, PDF p. 55     | MG5010E-i10 V3, PDF p. 56     |
| ------------------------------- | ----------------------------- | ----------------------------- | ----------------------------- |
| Nominal voltage                 | 24 V                          | 24 V                          | 24 V                          |
| Reduction / gearbox             | 10:1 / PG4210                 | 36:1 / PG5336                 | 10:1 / PG5110                 |
| Rated / maximum output torque   | 1 / 2.5 N·m                   | 9 / 18 N·m                    | 4 / 7 N·m                     |
| Rated / maximum speed           | 255 / 320 rpm                 | 72 / 90 rpm                   | 235 / 320 rpm                 |
| Rated current                   | 1.8 A                         | 3.5 A                         | 4.4 A                         |
| Published maximum power         | 65 W                          | 135 W                         | 160 W                         |
| Recommended drive               | DF40                          | DG40V3                        | DG50                          |
| Drive-input range in that sheet | 7.4–32 V                      | 12–24 V                       | 7.4–32 V                      |
| Feedback in those sheets        | 18-bit motor + 14-bit reducer | 18-bit motor + 14-bit reducer | 18-bit motor + 14-bit reducer |
| Backlash reference              | ≤10 arcmin                    | ≤6 arcmin                     | ≤8 arcmin                     |
| Bearing rated load              | 1000 N                        | 1120 N                        | 1000 N                        |
| Mass                            | 183 g                         | 350 g                         | 420 g                         |

[OEM English catalog hosted by Teika, pp. 52, 55, 56](https://teika-machine.co.jp/wp-content/uploads/2024/09/%E4%B8%8A%E6%B5%B7%E7%93%B4%E7%A9%BA%E7%A7%91%E6%8A%80%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8%E3%80%80%E6%96%B0%E3%82%AB%E3%82%BF%E3%83%AD%E3%82%B0.pdf), [later OEM MG4010E-i36/MG5010E-i10 extract](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf). Motor-side KV/KT numbers in a catalog cannot be turned into output torque per protocol count without identifying the electrical-current and shaft domains.

### Current catalog options and unresolved revisions

| Exact model page | Current CAN SKU       | Current RS485 SKU       | What still requires confirmation                                                    |
| ---------------- | --------------------- | ----------------------- | ----------------------------------------------------------------------------------- |
| MG4010E-i36      | `LKM-MG4010E-i36-CAN` | `LKM-MG4010E-i36-RS485` | Historical `TB-LKM-MG4010E-i36C` option correspondence; received DG40 revision      |
| MG4005E-i10      | `LKM-MG4005E-i10-CAN` | `LKM-MG4005E-i10-RS485` | Historical `TB-LKM-MG4005E-i10C` correspondence; DF40 versus another received drive |
| MG5010E-i10      | `LKM-MG5010E-i10-CAN` | `LKM-MG5010E-i10-RS485` | Historical code correspondence **and i10/i36 content mismatch**                     |

The new catalog names are observed options, not proven aliases for the old codes. Do not infer bus type just from the last letter of a historical SKU. The [Riotech MG4005E-i10 sheet](https://riotech.co.kr/wp-content/uploads/2024/10/MG4005E-i10-V3.pdf) and [MG5010E-i10 sheet](https://riotech.co.kr/wp-content/uploads/2024/10/MG5010E-i10-V3.pdf) remain useful distinct dimensional references, but their direct endpoints did not yield readable PDFs in this review. No uninspected numerical field from them overrides the read OEM catalog.

## Hardware and connections

### Separate motor power, control bus and setup UART

| Signal / connector in MG40–50 DG40R/C7 manual | Function / boundary                                                                                   |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| V+ / V−                                       | Motor-drive DC supply; repeated pins share the corresponding rail                                     |
| A/H                                           | RS485-A **or** CAN-H according to the actual manufactured bus variant                                 |
| B/L                                           | RS485-B **or** CAN-L according to that variant                                                        |
| T / R / G                                     | Separate setup UART transmit / receive / signal ground                                                |
| ZH1.5 six-pin                                 | The manual's drive-specific power/bus harness; do not assume another drive uses the same cavity order |
| MX1.25 three-pin                              | The manual's setup UART harness; follow the keyed drive-side diagram, not a mirrored cable view       |

The important **DG40R/C7 diagram on PDF p. 5** was inspected. It shows a six-pin order in its drawing orientation of V+, V+, V−, V−, A/H, B/L and a separate G, R, T UART drawing. Treat the drawing as authoritative for **that board only**; DF40, DG40V3, DG50 and different revisions require their matching connector diagram. Do not expose a controller UART to CAN/RS485 electrical signals or a motor supply. The public material reviewed does not establish blanket 5 V tolerance of the setup UART: use the matched LK interface rather than an arbitrary USB-serial voltage. [MG40–50 manual, connection pages 5–7](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

1. Identify one unloaded motor and its full drive/model label before applying supply power. If the label does not resolve the MG5010E-i10/i36 discrepancy or the harness, stop at identification.
2. Secure the housing and support any attached link. Keep its full motion path clear, including a possible startup/zero-return path. Provide accessible drive-power isolation independently of the PC software.
3. With power off, verify supply polarity and actual unit voltage range, then route power separately from the bus. A USB adapter does not supply motor power.
4. For CAN or RS485, match the **hardware interface variant** and terminate the physical bus ends as documented, generally 120 Ω at each end. A/H and B/L have different protocol semantics despite common labels.
5. Connect the setup UART only through the matching interface and confirmed pin orientation. For the read-only baseline use an otherwise disconnected, single-motor setup; a shared bus with duplicate IDs makes replies ambiguous.

The manufacturer's CAN protocol describes an on state after power-up; **power-up must not be assumed torque-off**. Its `Motor Off` command also clears stored turns/previous command state, whereas `Motor Stop` does not clear the same state. Neither is a universally harmless initial probe or a substitute for physical isolation and support. [CAN V2.35 §§1–3](http://en.lkmotor.cn/upload/20230706100134f.pdf).

## Software and development resources

### Development software and recovery <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

| Route          | Version/interface boundary                                                                                                                                                          |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| LK Motor Tool  | Manufacturer currently lists **V2.35**, V2.33 and V2.32; select the version matching the received drive/firmware                                                                    |
| UART setup     | Manual documents observed COM port, 115200 baud and ID 1 as defaults; read actual settings rather than overwriting them                                                             |
| CAN protocol   | Manufacturer **CAN V2.35**, standard 11-bit data frames, 8-byte DLC, ID `0x140 + motor ID`; IDs 1–32                                                                                |
| RS485 protocol | Manufacturer framed serial protocol, `0x3E` header, header/data checksums; not a CAN payload with a serial wrapper guessed by the reader                                            |
| USB drivers    | Official download center lists Windows, Mac and Linux entries; match the actual interface chip/OS. A 0 KB listing is not a validated driver package.                                |
| Source/demo    | Manufacturer links software, protocols and examples; no official Python SDK covering every supplied V3 revision was established. Community wrappers are not compatibility evidence. |

[Official software center](http://en.lkmotor.cn/Download.aspx?ClassID=45), [protocol center](http://en.lkmotor.cn/Download.aspx?ClassID=47), [USB drivers](http://en.lkmotor.cn/Download.aspx?ClassID=44), [read MG40–50 setup manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>). The site was readable over its published HTTP links; HTTPS endpoints were not accessible in this review. Retain original vendor package/version provenance before installing anything.

### Parameter and protection workflow

Use **Product → Read Info** for model, motor version, driver model, hardware and firmware; **Setting → Read Setting** for the baseline; **Encoder → Read** for encoder configuration. Screenshot/export the complete settings before writes. **Set RAM** and permanent save/ROM operations differ. ID/baud changes can require Save Setting plus reboot/power cycle; make them deliberately on one isolated unit, then read back before reconnecting a larger bus. Do not rewrite a factory-configured ID merely because ID 1 is used in a tutorial. [MG40–50 manual pp. 8–12](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

The manual covers protection thresholds, signal-loss behavior, torque/speed/angle limits, PID, encoder/gear ratio and product/firmware information. Some listed protections are explicitly unavailable in the documented software. A visible field is not proof that a fault limit is implemented. The CAN V2.35 torque-command description further states that `0xA1` is not constrained by the host's Max Torque Current setting; do not rely on that UI field as an independent safety limit. [Manual protection/limits pages](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>), [CAN torque protocol](http://en.lkmotor.cn/upload/20230706100134f.pdf).

## Getting started <a href="#getting-started" id="getting-started"></a>

### Identify the drive, then read a baseline

1. Resolve the received model/interface and power label. **For an unresolved historical SKU or the MG5010 listing mismatch, do not proceed to electrical commissioning.** The following path applies only after a matching motor/drive/harness has been positively identified.
2. Fixture the unloaded motor and clear/support the entire motion path. With power off, wire the confirmed DC supply and setup UART according to that drive's drawing. Keep bus/other controllers disconnected during this initial host-tool check.
3. Open the matching LK Motor Tool. Choose the actual enumerated COM port, the known stored baud rate and motor ID. For an untouched unit whose manual/label confirms the documented defaults, these are 115200 and 1. Click **CONNECT**.
4. Select **Product → Read Info**; compare model, reduction, driver and firmware with the actual order/label. Select **Setting → Read Setting** and retain the baseline. On **Encoder**, use **Read** only.
5. On **Test**, choose **Read State1** to obtain temperature, bus voltage and faults, then **Read State2** for raw current/speed/encoder data. Do not click Motor On, Send, Align, zero-setting, loop-clear or Download during this status check.

**Expected result:** a coherent identity, a saved settings record and plausible state readings for the exact motor, without a sent motion target. A port opening or green indicator alone is insufficient. If the host reports i36 for an i10 order, stop and reconcile the model before further work. [MG40–50 host/status pages 8–14](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

### Read-only CAN check for a confirmed CAN/V2.35 unit

6. Use a Linux SocketCAN-capable interface and the already known bus bitrate/ID. The example assumes a single confirmed motor at **ID 1, 1 Mbit/s** on `can0`; replace the interface/bitrate/ID with verified values before use. Configuring the host's interface does not change the motor's stored configuration.
7. Start capture in one terminal, then send **only the status1 request** in another. These commands are for the confirmed CAN interface, not RS485 or the setup UART.

```bash
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000
sudo ip link set can0 up
candump can0
```

```bash
cansend can0 141#9A00000000000000
```

**Expected result:** an 8-byte standard-frame reply on `0x141` with command byte `0x9A`, temperature, supply voltage and an error byte as defined in CAN V2.35. A captured request without a matching reply does not establish motor communication. Do not substitute `0x88`, `0xA1`, `0xA2`, origin writes or a movement sample while debugging this read. [Official CAN V2.35, pp. 5, 17–18](http://en.lkmotor.cn/upload/20230706100134f.pdf), [retained manufacturer's CAN test-command reference](<../../.gitbook/assets/LK test command-CAN.txt>), [can-utils command descriptions](https://github.com/linux-can/can-utils).

### Original offline status1 decoder: keep transport units separate

Save the following as `decode_lk_can_status1.py`. It accepts a supplied payload; it performs **no bus I/O** and refuses to decode an RS485 packet using CAN units.

```python
import argparse

parser = argparse.ArgumentParser()
parser.add_argument('payload', help='eight CAN payload bytes, hexadecimal')
args = parser.parse_args()
data = bytes.fromhex(args.payload)
assert len(data) == 8 and data[0] == 0x9A, 'Expected CAN V2.35 status1'
temperature = int.from_bytes(data[1:2], 'little', signed=True)
voltage = int.from_bytes(data[3:5], 'little') / 10.0
fault = data[7]
print('temperature_C=', temperature, 'voltage_V=', voltage)
print('fault_byte=', hex(fault))
print('under_voltage=', bool(fault & 0x01))
print('over_temperature=', bool(fault & 0x08))
print('other_bits=', hex(fault & ~0x09))
```

```bash
python3 decode_lk_can_status1.py "9A1900F000000000"
```

\*\*Expected result for this synthetic example:\*\*25 °C, 24.0 V, fault 0. These are constructed bytes, not a measured motor result. CAN V2.35 status1 uses 0.1 V/count and its published error map defines bits 0/3. **RS485 V2.35 uses 0.01 V/count and a different payload/error layout.** Dividing the CAN value by 100 instead of 10 would report 2.4 V for this example. [CAN status1](http://en.lkmotor.cn/upload/20230706100134f.pdf), [RS485 status1](http://en.lkmotor.cn/upload/20230706100146f.pdf).

The MG40–50 host manual and the general CAN protocol also disagree on some current full-scale/encoder details. Therefore this example does not convert status2 current counts to amperes or encoder counts to output angle. Resolve those fields using the **actual firmware's** scaling rather than silently choosing 16.5 A versus 33 A or assuming 18-bit values arrive in a full 18-bit field.

### From status to motion: preserve the scaling boundary

Only after identification, settings and first status are sound should a supported small unloaded movement be considered. The MG40–50 manual's Test descriptions use **motor-shaft degrees and degrees/second**; output motion requires the matched reduction factor. The same 360 motor degrees corresponds to 10 output degrees on 36:1 and 36 output degrees on 10:1. These are arithmetic examples, not commands to transmit.

Keep current/torque constants, gear ratio, direction and zero reference with each actuator. Avoid large absolute-zero commands, maximum-speed samples and generic PID imports. **Align** moves back and forth. The manual explicitly states that a completed firmware update triggers automatic calibration; keep the full sweep clear before starting an update, not only before a later Test command. A normal host disconnect or Ctrl-C is not a guaranteed stationary torque-off. [MG40–50 manual calibration/firmware/test pages 12–14](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>).

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom / question                          | Ordered checks and bounded recovery                                                                                               |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Current page SKU differs from old paperwork | Compare model, option and received label. Current CAN/RS485 names are not proof of the historical code's bus selection.           |
| MG5010 torque/speed table looks like i36    | Stop commissioning; the title/body discrepancy is explicit above. Obtain a model/ratio-matched parameter sheet.                   |
| Host port appears but no Read Info          | Check actual adapter chip, UART pins/ground, drive power, stored baud and ID. Do not connect CAN/RS485 data to the setup UART.    |
| CAN request visible, no response            | Check real CAN hardware, termination, bitrate, ID and duplicate nodes. The serial tool's 115200 baud is not CAN bitrate.          |
| Voltage differs by 10 ×                     | Compare CAN 0.1 V/count with RS485 0.01 V/count; check transport before assuming a supply fault.                                  |
| Current or output angle is implausible      | Keep raw counts. Resolve full-scale current, truncated encoder fields, motor/output domain and gear ratio before converting.      |
| Motor moves during maintenance              | Align, zero control and post-flash calibration are active operations. Support/clear the mechanism and isolate power separately.   |
| Error will not clear                        | Resolve the underlying supply/thermal condition before Clear Error. Repeated resets are not a diagnosis.                          |
| Does an E encoder remove backlash?          | No; feedback resolution and mechanical lost motion are distinct. A brake/B option adds another hardware/holding-state difference. |

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                      | Scope and actual access                                                                                                                  |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| [Official manual center](http://en.lkmotor.cn/Download.aspx?ClassID=21)                                                                                                                                                                       | Lists MG manual V2.33; the downloaded file identifies **MGv2** and is not automatically a V3 DF40/DG50 wiring authority                  |
| [MG40–50 servo manual](<../../.gitbook/assets/MG(40-50 series)servo motor manual.pdf>)                                                                                                                                                        | Existing OEM 15-page attachment, read; DG40R/C7 connector/host/calibration/state reference; copyright retained, not reproduced wholesale |
| [Official CAN V2.35 PDF](http://en.lkmotor.cn/upload/20230706100134f.pdf)                                                                                                                                                                     | 21 pages, read; identifiers, controls, readbacks, current/units and command limits                                                       |
| [Official RS485 protocol PDF](http://en.lkmotor.cn/upload/20230706100146f.pdf)                                                                                                                                                                | Read separately; framed serial checksums and transport-specific scaling                                                                  |
| [Official LK Tool V2.35 ZIP](http://en.lkmotor.cn/upload/20230707104924f.zip)                                                                                                                                                                 | Manufacturer-listed Windows host package; not executed                                                                                   |
| [Official USB drivers](http://en.lkmotor.cn/Download.aspx?ClassID=44)                                                                                                                                                                         | Match the actual adapter/OS; download listing is not runtime validation                                                                  |
| [Official 3D library](http://en.lkmotor.cn/Download.aspx?ClassID=49)                                                                                                                                                                          | Individual model files; do not substitute MG4005-i10 V2 CAD for MG4005E-i10 V3                                                           |
| [OEM full catalog, Teika-hosted](https://teika-machine.co.jp/wp-content/uploads/2024/09/%E4%B8%8A%E6%B5%B7%E7%93%B4%E7%A9%BA%E7%A7%91%E6%8A%80%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8%E3%80%80%E6%96%B0%E3%82%AB%E3%82%BF%E3%83%AD%E3%82%B0.pdf) | Exact model specifications/dimensional drawings: pp. 52, 55, 56 inspected                                                                |
| [OEM MG4 catalog extract](https://makerselectronics.com/wp-content/uploads/2025/05/LK%E4%BA%A7%E5%93%81%E6%89%8B%E5%86%8C%EF%BC%88%E8%8B%B1%E6%96%87%EF%BC%8925.02.11-1-MG4.pdf)                                                              | Later distributor-hosted OEM sheet, four pages read; source of i36 and i10 comparisons                                                   |
| [MG4005E-i10 V3 sheet](https://riotech.co.kr/wp-content/uploads/2024/10/MG4005E-i10-V3.pdf) / [MG5010E-i10 V3 sheet](https://riotech.co.kr/wp-content/uploads/2024/10/MG5010E-i10-V3.pdf)                                                     | Original distinct references retained; endpoints not readable as PDFs in this review                                                     |
| [Firmware-upgrade instruction](<../../.gitbook/assets/Lk Motor firmware upgrade instrucion.pdf>)                                                                                                                                              | OEM two-page attachment read; exact firmware and the newer manual's automatic-calibration warning remain essential                       |

### Protocol/document coverage index

The CAN document covers bus/addressing, on/off/stop, MS-only open loop, MG/MF/MH torque, speed, multi/single/incremental position, PID/acceleration/torque-limit reads/writes, encoder/zero, status1–3 and multi-motor torque. The RS485 document covers its frame/checksums and corresponding commands separately. They are linked for complete layouts; this guide intentionally implements a **read-only status1** example. The MG40–50 manual's naming/drive, wiring, host basics, IDs/baud, protection/limits/PID, encoders, calibration, Product/Firmware and Test/Status topics are addressed in the sections above. Resources not matched to an exact V3 hardware revision remain references, not approved substitute configuration files.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026**: manufacturer product/download categories, original CAN/RS485 PDFs, the retained MG40–50 manual and firmware note, the OEM catalogs hosted by Teika/Makers Electronics, and exact OpenELAB model pages/current options. The DG40R/C7 connector and active-calibration pages and relevant catalog model/dimensional pages were visually inspected. No new full manual pages or proprietary examples are reproduced.

**Validation:** source reviewed within the stated model/revision boundaries; historical SKU/interface mapping and the MG5010 i10/i36 listing discrepancy remain unresolved. Software installation, host communication, CAN/RS485/UART reads, flashing, calibration and motor movement were **not run**. Synthetic decoder output is a prospective example, not hardware evidence. Keep the received motor/drive/firmware identity and approved parameter sheet with any later result.
