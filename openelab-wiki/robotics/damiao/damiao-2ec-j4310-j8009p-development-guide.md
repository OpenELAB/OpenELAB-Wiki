---
description: >-
  Distinguish DAMIAO4310 24V V3 and8009P V3 wiring,voltage,encoder revisions and
  CAN layouts;read firmware and mapping ranges before motion.
---

# DAMIAO DM-J4310-2EC and DM-J8009P-2EC Engineering Guide

{% hint style="info" %}
[**View DAMIAO DM-J4310-2EC 24 V V3 on OpenELAB**](https://openelab.io/products/damiao-brushless-servo-dm-j4310) · [**View DAMIAO DM-J8009P-2EC V3 on OpenELAB**](https://openelab.io/products/damiao-brushless-servo-dm-j8009p)

**Models/options:** DM-J4310-2EC, 24 V, V3 · **SKU:** `DM-J4310-2EC-24V-V3`; DM-J8009P-2EC, V3 · **SKU:** `DM-J8009P-2EC-V3`. V4 and the 4310 48 V option are separate configurations.
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

These two DAMIAO joint actuators combine a brushless motor, gear reduction, drive and two encoders, but they are not electrically interchangeable. This guide uses **24 V for the first isolated read test** on either model and obtains firmware, gear ratio and the stored mapping ranges without enabling motion. The 4310 24 V SKU must never receive 48 V. The 8009 P has a separate CAN connector and opposite power-contact orientation in its manual’s face drawing. [4310 V1.1 hardware manual V1.3, 14 September 2026](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf), [8009 P manual V1.3 filename, 10 September 2026](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf).

The verified store options identify **V3** as the earlier 14-bit dual-encoder family: 4310 corresponds to the V1.1 hardware reference; 8009 P to the original 8009 P reference. The V4 options correspond to 4310 V1.2 and 8009 P V1.1 hardware with changed encoder specifications. A manual’s V1.3/V1.4 document revision is not the motor generation. Inspect the actual label/firmware before adopting that mapping; a swapped unit requires its own manual. The 8009 P September PDF’s filename/cover says V1.3 while internal page headers say V1.2; this guide identifies that document by date, filename and content, rather than silently treating those labels as different products. [Exact 4310 listing](https://openelab.io/products/damiao-brushless-servo-dm-j4310), [exact 8009 P listing](https://openelab.io/products/damiao-brushless-servo-dm-j8009p).

## Applications

The compact 4310 suits a small geared joint or benchtop control experiment; the larger 8009 P provides a different torque/bearing/load envelope. Select from the torque–speed curve, mounting drawing, phase current, cooling and duty cycle. Neither 7 N·m nor 40 N·m peak establishes continuous holding capability. Support gravity-loaded mechanisms before disabling or removing supply.

Use one actuator at a time to record serial/model, voltage option, firmware, command ID, feedback ID, control mode, mapping ranges and zero. Then build a joint-to-ID/sign map before connecting a multi-axis bus. A default-looking CAN reply is insufficient evidence that a motor was never recalibrated or reconfigured.

## Specifications <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

| Item                                             | DM-J4310-2EC24 V, V3                                                   | DM-J8009P-2EC, V3                                                                                                                |
| ------------------------------------------------ | ---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Source hardware scope                            | 4310 V1.1; manual V1.3, 2026-09-14                                     | Original 8009 P; dated 2026-09-10 PDF                                                                                            |
| Normal supply                                    | 24 V; manual normal band 24–28 V                                       | 24–48 V; first test 24 V                                                                                                         |
| Additional driver boundary                       | Minimum 20 V, maximum 28 V for this 24 V version                       | Manual lists 15 V minimum/52 V maximum outside its 24–48 V normal band; do not design nominal operation at protection boundaries |
| Rated / peak output torque                       | 3 /7 N·m                                                               | 20 /40 N·m                                                                                                                       |
| Reduction                                        | 10:1                                                                   | 9:1                                                                                                                              |
| Rated output speed                               | 120 rpm                                                                | 100 rpm at 24 V; 200 rpm at 48 V                                                                                                 |
| No-load output speed                             | 200 rpm at 24 V                                                        | 168 rpm at 24 V; 335 rpm at 48 V                                                                                                 |
| Rated / peak phase current                       | 2.5 /7.5 A                                                             | 20 /40 A                                                                                                                         |
| Pole pairs / phase resistance / phase inductance | 14 / 0.65Ω / 340µH                                                     | 21 / 0.145Ω / 80µH                                                                                                               |
| Encoders in this V3 scope                        | 14-bit dual encoder                                                    | 14-bit dual encoder                                                                                                              |
| Mass / envelope reference                        | 306 g; Ø57 × 46 mm                                                     | 963 g; Ø98 × 61.7 mm                                                                                                             |
| Output bearing                                   | Consult exact 4310 mechanical drawing                                  | Cross-roller; 8009 P is distinct from plain 8009                                                                                 |
| Communication                                    | Classical standard-frame CAN, default 1 Mbit/s; debug UART 921600 baud | Same reference CAN/UART rates; physical connector differs                                                                        |

[4310 specifications/driver conditions, PDF pp.5–10](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=5), [8009 P specifications/driver conditions, PDF pp.5–10](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=5). Phase-current ratings are not DC source-current ratings. The 4310 protection table’s suggested overvoltage threshold does **not** authorize exceeding its 28 V maximum for the 24 V driver maximum. Hot-plugging is unsuitable for this first test; connect with power removed and account for regenerated energy.

### V3 and V4 are not interchangeable files

| Store generation        | Appropriate document identity              | Integration consequence                                             |
| ----------------------- | ------------------------------------------ | ------------------------------------------------------------------- |
| 4310 V3 covered here    | Motor hardware V1.1, 14-bit dual encoder   | Use 24 V-specific limits and this harness/firmware                  |
| 4310 V4 outside scope   | Motor hardware V1.2, 16-bit encoder option | Do not import calibration/firmware from V3                          |
| 8009 P V3 covered here  | Original 8009 P, 14-bit dual encoder       | Use original 8009 P current/temperature/connector reference         |
| 8009 P V4 outside scope | 8009 P V1.1, 16-bit option                 | Different hardware revision; document/firmware selection must match |

The [4310 V1.2 reference reader](damiao-dm-j4310-2ec-v1.2-motor-instruction-manual.md) and [8009 P source reader](damiao-dm-j8009p-2ec-motor-instruction-manual.md) remain useful reference destinations; their existence does not replace this exact-option comparison. [DAMIAO guide index](./).

## Hardware and connections

### Use each model’s actual connector face

| Connection                                | 4310 V1.1 diagram                                                        | 8009 P original diagram                                                |
| ----------------------------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------- |
| Drive power                               | Two combined XT30(2+2) interfaces; either can be used                    | Separate XT30 power connector                                          |
| Power polarity in the published face view | Large contact left=VCC, right=GND; housing key as drawn                  | Large contact left=minus, right=plus; do not transfer 4310 orientation |
| CAN                                       | In the combined connector’s two small contacts: upper CAN-L, lower CAN-H | Separate GH1.25 two-pin: published face view left=H, right=L           |
| Debug serial                              | GH1.25 three-pin diagram left-to-right GND, RX, TX                       | Same labelled GND, RX, TX face drawing                                 |

These directions describe the manual figure, not an arbitrary mating-cable view; a cable face can be mirrored. Match the housing key and verify continuity unpowered. The 4310 combined contact includes both high-current power and differential CAN: it is not a four-pin UART header. UART RX/TX are motor-side names, so host TX goes to motor RX and host RX to motor TX. The inspected source does not explicitly establish an arbitrary host’s safe TTL amplitude; use the supported DAMIAO adapter/harness, not 5 V TTL inferred from a USB label. [4310 annotated connector/mounting figure, PDF p.10](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=10), [8009 P annotated connector/mounting figure, PDF p.10](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=10). Manufacturer diagrams remain ©DAMIAO; no pinout has been reconstructed from appearance.

Use the dimensioned thread-depth drawing before selecting screws. The 4310 drawing specifies several distinct M3 patterns/depths; a through-hole-looking feature is not proof that an arbitrary bolt can pass through. Keep rotating parts clear and do not use a long screw to find a hole’s bottom.

### Supplied harnesses and protection references

The 4310 manual lists one integrated motor, an XT30(2+2)-F power/CAN cable and a GH1.25 three-pin debug cable. The original 8009P list instead includes a 200mm XT30 power cable, 300mm GH1.25 two-pin CAN cable and 300mm three-pin debug cable. Those are manufacturer package references; confirm the received option rather than building a cable from its length or connector name alone. [4310 p.9](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=9), [8009P p.9](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=9)

The manuals describe driver overtemperature shutdown at 120°C, recommended motor-winding protection at or below 100°C, and an overcurrent coefficient no greater than 0.98. These protection settings are not continuous operating targets. The 4310 24V version remains limited to 28V even though a protection-table example names 32V; the 8009P manual separately gives 52V as its outer driver boundary. Match the installed source and thresholds to the exact model.

### CAN network and power path

Use a linear twisted-pair CAN bus, compatible common-reference/isolation arrangement and 120 Ω termination only at the two physical ends. With power removed, two 120 Ω terminators normally read about 60 Ω across CAN-H/CAN-L. Check built-in adapter termination before adding resistors. This resistance check does not prove correct bitrate or protocol.

Use a suitably protected 24 V source for the first result, with accessible drive isolation and no external load. Check voltage/polarity at the actuator before enabling its supply. A source that cannot absorb regenerated energy needs a designed absorption/discharge path before subsequent motion. Do not infer the required bus supply or branch fuse directly from phase-current peak.

## Software and development resources

### Supported setup utility and transport

The official **DMTool 2.2.2.2-hotfix** directory provides Windows x86\_64, Linux x86\_64/arm64, and macOS Intel/Apple Silicon packages. This is a proprietary application; its dynamically linked Qt/Qwt/libusb components have separate LGPL obligations. Obtain the matching binary from the official repository, read its included user guide and keep the package version with your configuration. No binary or driver was executed for this guide. [Official package README](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/README.en.md), [DMTool user guide](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/DMTool%E4%B8%8A%E4%BD%8D%E6%9C%BA%E8%BD%AF%E4%BB%B6%E8%AF%B4%E6%98%8E%E4%B9%A6.pdf).

DMTool’s **F2 adapter configuration** distinguishes USB2CAN-FD, serial and channel choices. CAN bitrate 1 Mbit/s and UART 921600 baud are different settings; selecting 921600 as the CAN bus rate will not configure a standard 1 Mbit/s motor. The V3 path does not support all newer V4 parameter reads over UART, so use the documented **CAN parameter-read path** for this guide’s range/version check. Do not assume every parameter shown in a new UI is implemented by a V3 motor. [DMTool connection/parameter chapters](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/DMTool%E4%B8%8A%E4%BD%8D%E6%9C%BA%E8%BD%AF%E4%BB%B6%E8%AF%B4%E6%98%8E%E4%B9%A6.pdf).

### Mode and byte-layout distinctions

| Mode or operation     | Integration rule                                                                        |
| --------------------- | --------------------------------------------------------------------------------------- |
| MIT motion            | Position 16 bits; velocity, Kp, Kd, torque 12 bits; mapping uses current PMAX/VMAX/TMAX |
| Position–velocity     | Two 32-bit floats for target rad and speed limit rad/s; distinct from packed MIT        |
| Velocity              | Float rad/s; use the documented frame length/mode ID                                    |
| Force–position hybrid | Additional torque/current limiting with its own payload; not a MIT decoder alias        |
| Parameter read        | Standard ID `0x7FF`, DLC4, `CANID_L CANID_H 33 RID`; reply at configured MST\_ID, DLC 8 |
| Parameter write /save | Opcodes `55` /`AA`; state changing and excluded from the first result                   |

The manuals describe mode-specific command offsets; match the selected mode before emitting any control packet. The original example below emits no mode-specific control packet at all. [4310 CAN chapter, pp.13–23](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=13), [8009 P CAN chapter, pp.13–24](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=13).

| Register               | Type / meaning                                        |
| ---------------------- | ----------------------------------------------------- |
| `0x07` MST\_ID         | uint32, feedback arbitration ID                       |
| `0x08` ESC\_ID         | uint32, command node ID                               |
| `0x0A` CTRL\_MODE      | uint32, stored control-mode selection                 |
| `0x0E` sw\_ver         | uint32, firmware version; do not reinterpret as float |
| `0x14` Gr              | float, gear ratio                                     |
| `0x15`, `0x16`, `0x17` | floats, PMAX(rad), VMAX(rad/s), TMAX(N·m)             |

The register-value bytes are **little endian** in response bytes 4–7. Ordinary packed motor feedback is different: position is bytes 1–2 high-byte first; velocity combines byte 3 and the high nibble of byte 4; torque combines byte 4’s low nibble and byte 5; bytes 6/7 give MOS/rotor temperatures. Data 0 packs node/status in nibbles. For a multi-motor design use IDs below 16 for unambiguous nibble identification and unique command/feedback routing. Decode using the actual read mapping ranges, not another library’s defaults. [Register map and feedback tables](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=14).

## Getting started

### First result with DMTool

1. Verify the physical model/voltage label and V3 option, fixture one unloaded actuator, and keep its output clear. Connect 24 V and the exact harness with power off. Use the supported adapter and one motor only.
2. Download the CPU/OS-matched DMTool package. For Linux x86\_64, extract its documented archive in an ordinary user directory and start the named application:

```bash
tar -xzf DMTool-v2.2.2.2-hotfix-x86_64.AppImage.tar.gz
./DMTool-v2.2.2.2-hotfix-x86_64.AppImage
```

3. Open **F2 adapter configuration**, select the observed adapter/channel and configured 1 Mbit/s CAN rate. Open the device connection; record the selected command CAN\_ID and feedback Master ID. If the identity is unknown, use the tool’s documented isolated-device ID read workflow. Reading/entering IDs may trigger a bus scan, so do this before joining a robot network.
4. Choose **Read Version**, then in **Parameter Settings** choose **Read Parameters**. Record firmware, ratio, PMAX/VMAX/TMAX, mode and IDs; save/export the displayed baseline where supported. Do not choose Write, Save ROM, Enable, Set Zero, encoder calibration or F3 command queue.
5. Compare the returned ratio with 10 for 4310 or 9 for 8009 P and reconcile the physical/firmware identity. A different ratio or missing required range is a failed identity/configuration checkpoint, not a reason to overwrite parameters.

**Expected result:** readable firmware/version and positive model-consistent ratio/mapping values, with the drive remaining disabled. Solid red is the documented normal disabled LED; flashing red is a fault, not the same state. **F3’s command queue defaults to repeated enable/disable rounds**, so it is unsuitable for a read-only check. [DMTool guide](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/DMTool%E4%B8%8A%E4%BD%8D%E6%9C%BA%E8%BD%AF%E4%BB%B6%E8%AF%B4%E6%98%8E%E4%B9%A6.pdf), [manufacturer parameter/LED procedure](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=11).

### Original Linux read-only register example

6. Use this alternative only if the adapter already exposes SocketCAN and the motor’s exact IDs/rate are recorded. A USB serial port is not automatically `can0`. Configure the actual interface:

```bash
ip -details -statistics link show can0
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000
sudo ip link set can0 up
```

7. Save the code below as `read_dm_v3.py`. It emits only opcode `0x33` register reads at standard ID `0x7FF`, **DLC4**. It checks standard-data flags, reply ID, DLC 8, echoed motor ID/opcode/register and value type. Its one-second wait is an original diagnostic bound.

```python
import argparse
import math
import socket
import struct
import time

ap = argparse.ArgumentParser()
ap.add_argument('--channel', default='can0')
ap.add_argument('--motor-id', required=True, type=lambda x: int(x, 0))
ap.add_argument('--master-id', required=True, type=lambda x: int(x, 0))
a = ap.parse_args()
if not 1 <= a.motor_id <= 15 or not 0 <= a.master_id <= 0x7FE:
    raise SystemExit('Use recorded isolated motor ID 1..15 and master ID 0..0x7fe')
frame = struct.Struct('=IB3x8s')
registers = [(0x0E, 'sw_ver', '<I'), (0x14, 'Gr', '<f'),
             (0x15, 'PMAX_rad', '<f'), (0x16, 'VMAX_rad_s', '<f'),
             (0x17, 'TMAX_Nm', '<f')]
with socket.socket(socket.PF_CAN, socket.SOCK_RAW, socket.CAN_RAW) as bus:
    bus.bind((a.channel,))
    bus.settimeout(0.1)
    for rid, name, fmt in registers:
        header = struct.pack('<HBB', a.motor_id, 0x33, rid)
        bus.send(frame.pack(0x7FF, 4, header + bytes(4)))
        deadline = time.monotonic() + 1.0
        while time.monotonic() < deadline:
            try:
                raw = bus.recv(frame.size)
            except socket.timeout:
                continue
            if len(raw) != frame.size:
                continue
            can_id, dlc, data = frame.unpack(raw)
            if can_id & 0xE0000000 or can_id != a.master_id:
                continue
            if dlc != 8 or data[:4] != header:
                continue
            value = struct.unpack(fmt, data[4:8])[0]
            if fmt == '<f' and (not math.isfinite(value) or value <= 0):
                raise SystemExit('Invalid range/ratio: retain raw data ' + data.hex())
            print(name, value, 'raw=', data.hex())
            break
        else:
            raise SystemExit(f'No matched read reply for register 0x{rid:02x}')
```

8. Substitute the observed motor and master IDs. The following 1/0 pair is a documented-style example, not a discovery result:

```bash
python3 read_dm_v3.py --channel can0 --motor-id 1 --master-id 0
```

**Expected result:** `sw_ver`, `Gr`, `PMAX_rad`, `VMAX_rad_s`, `TMAX_Nm` followed by raw bytes, or a bounded unmatched-read error. For an isolated ID1 node, the firmware read request is arbitration `7FF`, DLC4, data `01 00 33 0E`; the remaining four storage bytes in a Linux CAN frame are padding, not extra transmitted payload. The reply echoes those four bytes and returns a little-endian uint32. This check reads configuration rather than motor voltage or live motion telemetry; it never enables, clears a fault, zeros, writes, saves or calibrates. [4310 read-register frame, p.17](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=17), [8009 P frame, p.18](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=18).

### Before later motion or calibration

Keep the confirmed mapping ranges with the decoder. A zero-filled MIT payload maps signed fields to negative endpoints and is not a neutral test. Verify coordinate sign, zero, units and mode on a supported unloaded fixture before increasing demand. Establish current/torque/position/velocity limits and a tested stop workflow separately.

The manufacturer supplies factory calibration; encoder calibration can rotate the output a complete revolution. Do not run it merely because communication works or after mounting a constrained link. Serial parameter writes can reboot the drive; CAN changes may remain volatile until Save Parameters. The manual’s flash-save operation can take 30 ms and quotes finite endurance, so save intentional configuration changes rather than every control cycle. [Calibration/parameter management chapters](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=26).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                       | Ordered diagnostic and supported recovery                                                                                                                                                                            |
| --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| No register reply                             | Check actuator voltage/polarity; adapter mode/channel; CAN-H/L, reference and termination; recorded 1 Mbit/s rate; then command and master IDs. Do not diagnose by enabling or changing bitrate on a multi-node bus. |
| `sw_ver` looks nonsensical as a decimal float | Decode register 0x0E as uint32; retain raw bytes and use DMTool Read Version for the manufacturer presentation.                                                                                                      |
| New UI fields fail on V3                      | Use CAN for documented V3 parameters; check firmware support instead of writing V4-only current-loop/subversion fields.                                                                                              |
| All nodes seem to answer                      | Isolate one motor; reconcile duplicate IDs and MST\_ID routing before reconnecting the chain.                                                                                                                        |
| Incorrect motion scale                        | Disable, support the mechanism and re-read PMAX/VMAX/TMAX, mode, ratio and encoder reference; do not divide an output-referenced angle by the ratio again.                                                           |
| Flashing red                                  | Read the exact fault: 8 overvoltage, 9 undervoltage, A current, B MOS temperature, C winding temperature, D communication, E overload; encoder/calibration codes 3–5 need their specific repair procedure.           |
| Unit resets while decelerating                | Inspect regenerated bus voltage and supply absorption. A protection threshold is not a wider normal supply specification.                                                                                            |
| Saved change vanishes                         | Distinguish volatile CAN Write from disabled-state Save. Record the previous setting before retrying.                                                                                                                |

**Can I power both models from 48 V?** Not these exact options: the covered 4310 is 24 V and has a 28 V maximum. The 8009 P supports its own 24–48 V normal range.

**Is solid red always a failure?** No. The manual labels solid red as disabled and solid green as enabled. Flashing red requires fault interpretation.

**Does dual encoder eliminate calibration risk?** No. Factory zero, output reference and encoder generation must stay with the physical unit. Calibration involves motion and must be treated as a separate commissioning operation.

### Firmware and recovery boundaries <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Read version and archive parameters first. The official firmware library separates model/hardware images and bootloader/update requirements. The newer DMTool guide’s CAN upgrade requires a compatible bootloader (documented 3.2.0.5 or later) and adapter/rate; this is not evidence that every V3 motor can use every new update route. The [official pinned firmware notes](https://raw.githubusercontent.com/dmBots/motor-firmware/8a9125e5b269fdf49b4338d0e20df8f0164bdbee/%E7%89%88%E6%9C%AC%E8%AF%B4%E6%98%8E/%E5%9B%BA%E4%BB%B6%E7%89%88%E6%9C%AC%E8%AF%B4%E6%98%8E.md) require reading the current version and matching its two-digit model-family code; that is necessary in addition to model/encoder/voltage compatibility. They also document a zero-storage migration: upgrading an older unit directly toV17-02 can require resetting zero, whereasV17-01 is the stated migration path. Preserve the existing zero/configuration and follow the manufacturer’s exact staged route instead of treating a new image as a drop-in update. Use the exact model/revision package and manufacturer recovery sequence; preserve the existing image/version and zero. Do not rename another model’s binary or assume a shared filename prefix establishes compatibility. [DMTool update chapter](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/DMTool%E4%B8%8A%E4%BD%8D%E6%9C%BA%E8%BD%AF%E4%BB%B6%E8%AF%B4%E6%98%8E%E4%B9%A6.pdf), [official firmware repository](https://github.com/dmBots/motor-firmware).

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                       | Version and purpose                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [4310 V1.1 hardware manual](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf)                                                                                                                  | V1.3, 2026-09-14; 24 V/48 V distinction, dimensions, pinouts, LEDs, modes, CAN register map, host tool, calibration, updates |
| [Original 8009 P manual](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf)                                                                                                                            | 2026-09-10 file; coverV1.3/internalheadersV1.2; specifications, connector/dimensions, protocol, calibration, examples        |
| [4310 connector and dimension drawing](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=10)                                                                                               | Manufacturer figure; match housing view and screw depth                                                                      |
| [8009 P connector and dimension drawing](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=10)                                                                                                    | Separate XT30/CAN/debug layout; not 4310’s combined connector                                                                |
| [4310 official file repository](https://github.com/dmBots/DM-J4310-2EC)                                                                                                                                                                                                                        | Model-specific manual and mechanical resources; choose V1.1 hardware                                                         |
| [8009 P official file repository](https://github.com/dmBots/DM-J8009P-2EC)                                                                                                                                                                                                                     | Model-specific manual/mechanical resources; distinguish newer V1.1 hardware                                                  |
| [DM-J4310-2EC dimensioned drawing](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/2da08d236aa06743f85cde409811c005fbae0d5c/drawings/2d/DM_J4310_V1.1%20%E5%87%8F%E9%80%9F%E7%94%B5%E6%9C%BA%20Ver.B20230904.PDF)                                                                        | Exact observed model resource; drawing inspected, STEP listed, not fabricated                                                |
| [DM-J4310-2EC STEP](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/2da08d236aa06743f85cde409811c005fbae0d5c/models/3d/DM-J4310-2EC-V1.1_3d_20260228_1.stp)                                                                                                                              | Exact observed model resource; drawing inspected, STEP listed, not fabricated                                                |
| [DM-J8009P-2EC dimensioned drawing](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/42eaaf7f05cccba18d182b51504ee0349e16cff6/drawings/2d/8009-rau%205005-20240809.PDF)                                                                                                                  | Exact observed model resource; drawing inspected, STEP listed, not fabricated                                                |
| [DM-J8009P-2EC STEP](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/42eaaf7f05cccba18d182b51504ee0349e16cff6/models/3d/8009-RAU_5005_%E5%A4%96%E5%BD%A2%E5%B0%BA%E5%AF%B8-20240809.stp)                                                                                                | Exact observed model resource; drawing inspected, STEP listed, not fabricated                                                |
| [DMTool packages/README](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/README.en.md) and [complete tool guide](https://raw.githubusercontent.com/dmBots/motor-debugging-tool/master/DMTool%E4%B8%8A%E4%BD%8D%E6%9C%BA%E8%BD%AF%E4%BB%B6%E8%AF%B4%E6%98%8E%E4%B9%A6.pdf) | Adapter setup, parameter read, curves/queue, calibration, updates; packaged 2.2.2.2-hotfix                                   |
| [Firmware library](https://github.com/dmBots/motor-firmware)                                                                                                                                                                                                                                   | Match model, hardware/encoder and bootloader; not run by this guide                                                          |

The exact manuals include example implementations and the register/protocol definitions; the Linux reader here is original. Mechanical drawing/STEP links above use the actual observed pinned paths, not fabricated filenames. Consult the repository’s hardware revision folder before importing CAD.

### Complete CAN control and state reference

This reference describes the dated manuals' wire contract. It complements the non-enabling first result above; command documentation is not a request to transmit the table as a test sequence. Keep the selected control mode, physical limits, actual firmware, command ID and master/reply ID with every capture. [4310 manual, pp.13–21](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=13), [8009P manual, pp.13–22](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=13)

| Stored mode code         | Standard arbitration ID | Payload, beginning at byte 0                                                                               | Control meaning                                                                       |
| ------------------------ | ----------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| 1, MIT                   | `ID`                    | 16-bit position; 12-bit velocity; 12-bit Kp; 12-bit Kd; 12-bit feedforward torque, packed into eight bytes | Torque/current reference from the selected impedance terms; use actual PMAX/VMAX/TMAX |
| 2, position–velocity     | `0x100 + ID`            | Little-endian float32 target position in bytes 0–3, rad; float32 velocity limit in bytes 4–7, rad/s        | Cascaded position/velocity/current control; speed is the trapezoidal profile's limit  |
| 3, velocity              | `0x200 + ID`            | Little-endian float32 velocity, rad/s, four bytes                                                          | Sustained target velocity; do not append an unrelated four-byte field                 |
| 4, force–position hybrid | `0x300 + ID`            | Float32 position, rad; uint16 speed-limit code; uint16 current-limit code, all little endian               | Speed code/100 gives rad/s; current code/10000 gives per-unit phase-current limit     |

For the hybrid mode, speed/current codes are each specified as 0–10000, corresponding to 0–100rad/s and 0–1.0 per unit. Larger numeric codes are capped by the documented driver. These encoding limits do not raise the actual actuator's speed/current capability. The current fraction's reference is the measured maximum phase current in the protocol description; another GUI paragraph calls it a percentage of rated current. Resolve the installed tool/firmware convention before a current-limited load experiment.

The MIT packing is: position bytes 0–1; velocity byte 2 and high nibble of byte 3; Kp low nibble of byte 3 and byte 4; Kd byte 5 and high nibble of byte 6; torque low nibble of byte 6 and byte 7. Interpret each assembled field as an **unsigned code mapped onto its physical interval**, not a two's-complement integer. Position uses ±PMAX, velocity ±VMAX, torque ±TMAX; Kp maps 0–500 and Kd 0–5. For an n-bit field, decode with `minimum + code*(maximum-minimum)/(2^n-1)`. Consequently, zero bytes represent lower endpoints, not a neutral demand. Preserve the actual configured mapping ranges, including when interpreting feedback in non-MIT modes.

The 8009P manual p.16 gives example mapping bounds of ±12.5rad, ±45rad/s and ±54N·m, alongside Kp 0–500 and Kd 0–5. These are documented example encodings, not confirmation of the delivered configuration or permission to exceed that motor’s 40N·m physical peak. The same manual p.15 states startup position is within −π to +π rad and defines ordinary position, velocity and torque as output-shaft quantities after reduction. Re-read the actual stored ranges and zero before interpreting a real capture.

MIT derives torque from position error, velocity error and feedforward torque. With Kp zero, Kd and velocity demand can produce velocity behavior; with both gains zero, feedforward torque alone remains active and can accelerate an unloaded motor. Position control requires nonzero damping according to the manual. In the cascaded modes, the older GUI's automatic gain calculation requires a positive damping-factor value; its recommended example is 4.0 within a stated 2–10 range. Those are documented tuning references, not a universal gain set for an attached mechanism.

### Enable, disable, zero, faults and persistence

| Operation       | Documented payload / destination                                                     | State and persistence consequence                                                                                |
| --------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Enable          | Seven `FF` bytes followed by `FC`, using the selected mode's command ID              | Enables output; not a passive status query                                                                       |
| Disable         | Seven `FF` bytes followed by `FD`, same ID selection                                 | Removes enabled control. The manual describes equal phase-terminal modulation, not galvanic electrical isolation |
| Set zero        | Seven `FF` bytes followed by `FE`                                                    | Sets current output position as zero and clears the position command; preserve the prior coordinate record       |
| Clear fault     | Seven `FF` bytes followed by `FB`                                                    | Clears a fault state where supported; diagnose the actual cause before re-enabling                               |
| Read register   | Standard `0x7FF`, four bytes: node low, node high, `33`, register                    | Reply at MST\_ID: same four-byte header plus typed little-endian 32-bit value                                    |
| Write register  | Standard `0x7FF`, eight bytes: node low, node high, `55`, register, four value bytes | Immediate volatile change; reply at MST\_ID echoes the written header/value                                      |
| Save parameters | Standard `0x7FF`, four bytes: node low, node high, `AA`, `01`                        | Disabled-state flash operation; saves all parameters together; reply at MST\_ID echoes those four bytes          |

The manuals allow up to 30ms for saving and quote approximately 10,000 erase/write cycles. Save deliberate configuration changes rather than every control cycle. A CAN mode write clears position, velocity, feedforward torque, Kp and Kd without the serial method's automatic reboot; it is volatile until saved. The serial host's Write Parameters operation requires disabled output, saves/applies the configuration and reboots. Read back the mode afterward instead of trusting only the clicked menu item.

For position-mode migration, the manual recommends reading `0x50` at zero speed before switching. That register is the rotor-derived position; `0x51` is the direct output-encoder position. Preserve the coordinate/sign/zero relation rather than treating the two feedback sources as identical.

### Feedback layout and diagnostic interpretation

The ordinary state frame uses the configured master ID and eight bytes. Byte 0 combines node/status nibbles; position is `(byte1<<8)+byte2`, velocity `(byte3<<4)+(byte4>>4)`, torque `((byte4 & 15)<<8)+byte5`, followed by MOS and winding temperature bytes in °C. Position is a 16-bit mapped value, velocity/torque 12-bit mapped values. The manufacturer also describes an eight-bit node comparison while sharing byte 0 with status; choosing uniquely identified motor IDs 1–15 avoids relying on an ambiguous wider ID representation in that byte.

Status 0 means disabled and 1 enabled. Faults 3/4/5 concern output calibration/sensor/motor calibration; 8/9 are over/undervoltage; A overcurrent; B/C MOS/winding temperature; D communication loss; E overload. Solid red is the default disabled indication, solid green enabled, flashing red a fault indication. A decoded status is not proof that an external load is mechanically supported.

### Full register dictionary, with model differences

The following factual dictionary condenses the two manuals without replacing their hardware/firmware scope. `float` means little-endian float32, `u32` little-endian uint32. Ranges are **register acceptance/mapping ranges**, not safe physical operating limits; `fmax` is the source's floating-point bound, not a motor specification. Both manuals share these entries unless otherwise noted. [4310 dictionary, pp.20–21](https://raw.githubusercontent.com/dmBots/DM-J4310-2EC/master/manual/DM-J4310-2EC%20V1.1%20Geared%20Motor%20User%20Manual%20V1.3%202026-09-14.pdf#page=20), [8009P dictionary, pp.21–22](https://raw.githubusercontent.com/dmBots/DM-J8009P-2EC/master/manual/DM-J8009P-2EC%20Gear%20Motor%20User%20Manual%20V1.3%202026-09-10.pdf#page=21)

| Address (hex) | Name       | Access/type | Meaning / source range                                                                                      |
| ------------- | ---------- | ----------- | ----------------------------------------------------------------------------------------------------------- |
| `00`          | UV\_Value  | RW float    | Undervoltage threshold; >10 through fmax                                                                    |
| `01`          | KT\_Value  | RW float    | Torque constant; 0 through fmax                                                                             |
| `02`          | OT\_Value  | RW float    | Motor-temperature threshold; 80 inclusive to 200 exclusive                                                  |
| `03`          | OC\_Value  | RW float    | Overcurrent coefficient; >0 and <1                                                                          |
| `04`          | ACC        | RW float    | Positive acceleration, >0 and \<fmax                                                                        |
| `05`          | DEC        | RW float    | Negative deceleration, from −fmax inclusive to 0 exclusive                                                  |
| `06`          | MAX\_SPD   | RW float    | Maximum velocity, >0 through fmax; confirm motor/output domain in the actual GUI                            |
| `07`          | MST\_ID    | RW u32      | Reply/master arbitration ID, 0–`7FF`                                                                        |
| `08`          | ESC\_ID    | RW u32      | Command node ID, 0–`7FF`; first-reader scope is deliberately narrower                                       |
| `09`          | TIMEOUT    | RW u32      | Communication timeout, 0–2³²−1; 50µs/count in the parameter chapter, effective while enabled                |
| `0A`          | CTRL\_MODE | RW u32      | Dictionary accepts 0–4; defined operating modes are 1–4, so do not invent mode 0 semantics                  |
| `0B`          | Damp       | RO float    | Identified viscous damping                                                                                  |
| `0C`          | Inertia    | RO float    | Identified rotor inertia                                                                                    |
| `0D`          | hw\_ver    | RO u32      | Marked reserved in these dictionaries                                                                       |
| `0E`          | sw\_ver    | RO u32      | Firmware version                                                                                            |
| `0F`          | SN         | RO u32      | Marked reserved; do not assume a usable unique serial number                                                |
| `10`          | NPP        | RO u32      | Pole pairs: physical-model reference 14 for 4310, 21 for 8009P                                              |
| `11`          | Rs         | RO float    | Phase resistance                                                                                            |
| `12`          | Ls         | RO float    | Phase inductance                                                                                            |
| `13`          | Flux       | RO float    | Rotor flux linkage                                                                                          |
| `14`          | Gr         | RO float    | Reduction: 10 for 4310, 9 for 8009P                                                                         |
| `15`          | PMAX       | RW float    | Positive position mapping bound, rad                                                                        |
| `16`          | VMAX       | RW float    | Positive velocity mapping bound, rad/s                                                                      |
| `17`          | TMAX       | RW float    | Positive torque mapping bound, N·m                                                                          |
| `18`          | I\_BW      | RW float    | Current-loop bandwidth, 100–10000                                                                           |
| `19`          | KP\_ASR    | RW float    | Velocity-loop Kp, 0 through fmax                                                                            |
| `1A`          | KI\_ASR    | RW float    | Velocity-loop Ki, 0 through fmax                                                                            |
| `1B`          | KP\_APR    | RW float    | Position-loop Kp, 0 through fmax                                                                            |
| `1C`          | KI\_APR    | RW float    | Position-loop Ki, 0 through fmax                                                                            |
| `1D`          | OV\_Value  | RW float    | Overvoltage threshold; dictionary leaves the range unspecified, not an invitation to choose a higher supply |
| `1E`          | GREF       | RW float    | Gearbox torque-efficiency coefficient, >0 through 1                                                         |
| `1F`          | Deta       | RW float    | Damping coefficient, 1–30 in dictionary; GUI explanation differs between uses/versions                      |
| `20`          | V\_BW      | RW float    | Velocity filter bandwidth, >0 and <500Hz                                                                    |
| `21`          | IQ\_c1     | RW float    | Current-loop gain, 100–10000                                                                                |
| `22`          | VL\_c1     | RW float    | Velocity-loop gain factor, >0 through 10000                                                                 |
| `23`          | can\_br    | RW u32      | CAN-rate code, 0–9, version-dependent transport behavior below                                              |
| `24`          | sub\_ver   | RO u32      | Firmware sub-version; may be absent on an older fitted V3 firmware                                          |
| `37`          | dir        | RO float    | Direction reference; shared address                                                                         |
| `50`          | p\_m       | RO float    | Rotor-derived position in rad; retain its zero/reference                                                    |
| `51`          | xout       | RO float    | Direct output-shaft encoder position in rad                                                                 |

These **non-shared entries must not be merged into one universal map**:

| Address (hex)    | 4310 V1.1 September-14 manual                           | Original 8009P September-10 manual         |
| ---------------- | ------------------------------------------------------- | ------------------------------------------ |
| `25`             | Boot\_ver, RO u32                                       | Not listed                                 |
| `32`, `33`       | Not listed                                              | u\_off, v\_off, RO float phase offsets     |
| `34`, `35`       | Not listed                                              | k1, k2, RO float compensation coefficients |
| `36`             | Not listed                                              | m\_off, RO float angle offset              |
| `38`             | m\_off, RO float motor-side angle offset                | Not listed                                 |
| `3B`             | Imax, RO float driver-current limit                     | Not listed                                 |
| `3C`             | VBus, RO float bus voltage                              | Not listed                                 |
| `3D`, `3E`       | Tpcb, Tmtr, RO float temperatures                       | Not listed                                 |
| `3F`, `40`, `41` | I\_U\_OFF, I\_V\_OFF, I\_W\_OFF, RO float phase offsets | Not listed                                 |

An unlisted register is not established by this manual, even if a newer DMTool UI displays it. Keep the read-only starter limited to the actual supported range/version registers; extend a parser only after confirming the fitted firmware's contract.

### Rate changes, timeout units and CAN-FD boundary

| Rate code         | Documented rate                     |
| ----------------- | ----------------------------------- |
| 0 / 1 / 2 / 3 / 4 | 125k / 200k / 250k / 500k / 1Mbit/s |
| 5 / 6 / 7 / 8 / 9 | 2M / 2.5M / 3.2M / 4M / 5Mbit/s     |

The September manuals describe replying at the old rate before changing to the new rate. A stored value above 5Mbit/s falls back to 1Mbit/s at startup. Their >1Mbit/s mode uses CAN-FD feedback, while ≤1Mbit/s uses CAN2.0B. A classic-only host may still have commands received but fail to receive FD replies. These statements do not supply complete arbitration/data-phase timing for every adapter or establish that every earlier V3 unit implements the newer mode. Verify firmware, controller and adapter together before changing the rate; keep the first result on the recorded 1Mbit/s classic path.

TIMEOUT uses 50µs/count in the parameter chapter: for example, 2000 counts arithmetically corresponds to 100ms. This is an interpretation example, not a suggested setting. The manual says timeout protection acts while enabled; it does not define a universal meaning for zero. Changing a node's rate/ID on an assembled multi-motor bus can make recovery harder, so inventory and deliberate reconfiguration belong to separate sessions.

### Calibration, tuning and physical-model interpretation

| Maintenance activity           | Specific procedure / acceptance clue                                                                                                                                                                                                                        |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor-side encoder calibration | Factory-calibrated; when applicable, the matched tool initiates forward/reverse electrical-cycle motion, parameter identification and compensation collection. Inspect identified pole count and waveform; the manual's compensation-data guideline is ±300 |
| Motor parameter identification | Identifies resistance, inductance and flux; requires a secured unloaded motor and produces movement. Except for the reference viscous coefficient, negative identified values require investigation                                                         |
| Output encoder calibration     | Select Output Shaft Encoder with the tool's calibration selector; requires a complete free revolution. Excessive deviation produces fault 3 and flashing red; support is needed for an unresolved sensor issue                                              |
| Parameter management           | Read first; preserve the four groups—drive, identified motor, input/feedback mapping, control settings. Disabled-state serial Write reboots; CAN writes and flash Save have different persistence                                                           |
| GUI control experiment         | Verify mode from startup output/readback, choose its matching tab, verify node, then apply deliberately bounded targets on a fixture. Timed/Periodic Send, Update and Send are distinct controls; exit with Stop then Disable and confirm disabled state    |

The manual's acceleration/deceleration GUI uses **krad/s²**, with negative deceleration; do not silently interpret the displayed number as rad/s². A velocity-limit paragraph refers to rotor speed before reduction, while mapped feedback is output-referenced: keep source domains explicit and compare a known displacement rather than dividing every angle by Gr.

The source's example position and velocity targets are demonstrations, not first-run defaults. Its hybrid GUI example labels `0.2%FS`, while the protocol uses a 0–1 per-unit current fraction. Do not assume a displayed `0.2` means the same thing in both interfaces. Likewise, the source's current-limit and damping descriptions vary between chapters; retain the actual installed GUI/firmware and confirm the conversion before active tuning.

The visually reviewed p.9 formulas are `VMAX = 0.57735*VBUS/(Npp*Gr*flux)` in rad/s and `Kt = 1.5*Npp*flux*Gr*GREF`. They are model/parameter relationships, not substitutes for the physical speed/thermal ratings. The 4310 p.9 caption says 36rpm, while the plotted speed trace is near 120rpm; do not derive a qualified efficiency curve by silently choosing one. The graph's supply, ambient, torque, electrical input, mechanical power and efficiency axes need to be interpreted together.

### Firmware-family and full manual navigation

The 4310 manual names firmware prefix **70**; the original 8009P manual names **73**. Match that family in addition to voltage, encoder, hardware and bootloader revision. Serial update is Select file → verify filename/family → Upgrade Firmware → completion; CAN update additionally requires the documented compatible bootloader (3.2.0.5+), a supported USB-CAN adapter, matching recorded bus rate and target ID. Preserve zeros and parameters before applying the firmware repository's staged migration instructions.

| Manual topic                                                             | 4310 PDF pages | 8009P PDF pages |
| ------------------------------------------------------------------------ | -------------- | --------------- |
| Revision, identity, restrictions, features                               | 1–6            | 1–6             |
| Specifications, supply/current, formulas, curve, package                 | 7–9            | 7–9             |
| Connector faces and mounting                                             | 10             | 10              |
| LEDs and four operating modes                                            | 11–13          | 11–13           |
| Frames, state commands, typed parameters, rate changes                   | 13–19          | 13–20           |
| Complete register dictionary                                             | 20–21          | 21–22           |
| Tool connection, both calibrations, identification, parameter management | 22–32          | 23–33           |
| Mode verification and MIT/position/velocity/hybrid GUI demonstrations    | 32–47          | 33–48           |
| Firmware check, serial and CAN update                                    | 48–50          | 49–51           |

The originals retain complete screen illustrations and assembly drawings. This on-page reference supplies the technical fields and model differences in searchable form, while the starter remains a separately bounded read-only workflow. None of these maintenance or control operations was executed on a motor during this review.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Source review completed **24 November 2026** using the two dated manufacturer PDFs, the actual DMTool documentation/package README, and verified live OpenELAB options plus the 23 November catalog. The manufacturer diagrams were inspected for contact polarity and the differences between the two models. Specifications, byte layouts and numerical units above are scoped to those documents; source inconsistencies are stated beside the affected facts.

**Validation:** Python syntax and synthetic packet fixtures were checked; the four-byte read header and typed reply layout were reviewed against both PDFs. DMTool installation, SDK builds, firmware updates, real CAN requests, power and motion were **not run**. A successful expected result is a reproduction checkpoint, not a claimed hardware observation.
