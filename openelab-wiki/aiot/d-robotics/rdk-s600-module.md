---
description: >-
  Compare MS6 S600 modules, interfaces and S600 software resources; record an
  existing carrier while module power, pinout and boot requirements remain
  explicit.
---

# D-Robotics RDK S600 Module: MS6 Specifications and Carrier Integration Reference

{% hint style="info" %}
**Manufacturer reference: D-Robotics RDK S600 Module.** This module is not yet listed on OpenELAB; no retailer SKU or product URL has been verified.

**Manufacturer models:** `MS6X032064I` and `MS6X064256I` · **Hardware reference:** the two-page V1P0 module brief · **Integration scope:** the bare compute module and its required model-matched carrier, power design, cooling and software package.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

The RDK S600 Module combines application CPUs, Nash AI accelerators, graphics, image-processing engines, memory and storage in a **120 × 83 mm compute module with a 699-pin board-to-board connector**. It is intended for integration into a carrier designed for the actual module revision. The public V1P0 brief names two MS6 configurations; the complete RDK S600 developer kits use separate KS6 identifiers. [Module brief, pp.1–2](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf); [developer-kit model table and J2 description](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/02_rdk_s600/01_rdk_s600_kit?v=5.1.1\&p=RDK+S600).

The distinction matters before connecting power: the S600 developer kit's **12–28 V input belongs to its carrier-board J1**. It does not establish a permissible input voltage, connector pin or sequencing rule for the bare MS6 module. The public documents reviewed here do not provide a complete module power/pinout design package. Custom-carrier power-up, signal wiring and module-only flashing remain blocked until the corresponding manufacturer information is available. [M1](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/02_rdk_s600/01_rdk_s600_kit?v=5.1.1\&p=RDK+S600).

### Select the actual module and its carrier <a href="#select-the-actual-module-and-its-carrier" id="select-the-actual-module-and-its-carrier"></a>

| Hardware identity | Memory and integrated storage | What the identity establishes                                                                    |
| ----------------- | ----------------------------- | ------------------------------------------------------------------------------------------------ |
| `MS6X032064I`     | 32 GB DDR; 64 GB UFS          | Module configuration named by the V1P0 brief                                                     |
| `MS6X064256I`     | 64 GB DDR; 256 GB UFS         | Different module memory/storage configuration                                                    |
| `KS6X032064C`     | 32 GB LPDDR5; 64 GB UFS       | Complete S600 developer-kit model, including carrier interfaces                                  |
| `KS6X064256C`     | 64 GB LPDDR5; 256 GB UFS      | Complete developer-kit configuration; its case and carrier dimensions are not the module outline |

The MS6 values come from the module brief; the KS6 values come from the kit's V1P0 hardware chapter. Record the actual module label, carrier part/revision and supplied firmware together. A Linux device-tree model string can describe a carrier and cannot replace the physical MS6 part marking. [M1](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/02_rdk_s600/01_rdk_s600_kit?v=5.1.1\&p=RDK+S600).

The [original module photograph and specification tables are available in the manufacturer PDF](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf). Page 1 shows the module; page 2 contains the package, processor, interface and multiplexing specifications. The photograph is a component-location reference, not a 699-contact pin map.

## Applications <a href="#applications" id="applications"></a>

* **Robot perception and model deployment:** integrate camera processing and supported CNN/Transformer workloads with the S600-specific compiler, runtime and image. Validate the complete preprocessing, model and postprocessing path.
* **Custom robot computers:** design a carrier that exposes the documented interfaces needed by the system, with the matching power tree, signal levels, connector and cooling design.
* **Mixed application and real-time control:** keep Linux application processing and MCU-domain control ownership explicit. The brief identifies FreeRTOS development for the MCU domain; the available package and supported core/cluster configuration must be confirmed.
* **Multi-camera processing:** plan receiver lanes, ISP/pyramid/GDC use, external PHY/serializer requirements and buffer bandwidth before choosing physical camera connectors.
* **Display and media systems:** use the documented display transmitters and codec engines through the selected carrier and BSP. Module-level transmitter capability does not establish that the carrier has a particular HDMI connector.

These applications are capability-based integration paths. The published TOPS and media rates are manufacturer limits rather than measured application throughput or robot safety certification. [M1](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf).

## Specifications <a href="#specifications" id="specifications"></a>

### Compute, memory and package <a href="#compute-memory-and-package" id="compute-memory-and-package"></a>

| Item                        | V1P0 module specification                                   | Interpretation for development                                                                                         |
| --------------------------- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Mechanical outline          | 120 × 83 mm                                                 | Module outline only; height, keep-outs, mounting and mating-stack details require the design package                   |
| Connector                   | 699-pin B2B                                                 | Contact count does not identify a pin assignment, mating part or orientation                                           |
| CPU                         | 18 Arm Cortex-A78AE cores, up to 2.0 GHz                    | Four MP4 clusters and one MP2 cluster; DynamIQ Shared Unit and Lock/Split/Hybrid execution modes are listed \[M1, p.2] |
| CPU caches                  | Per core: 64 KB L1 instruction, 64 KB L1 data and 256 KB L2 | L3 is stated as 1 MB per MP4 cluster and 512 KB per MP2 cluster                                                        |
| BPU                         | Four Nash cores, up to 560 TOPS at INT8                     | Aggregate manufacturer figure; model operators, shapes, precision and data movement affect achieved performance        |
| BPU local memory            | 8 MB L1M                                                    | The brief also describes a full-duplex load/store path and time-division support for up to two virtual machines        |
| GPU                         | Arm Mali-G78AE, up to 857 MHz; 220 FP32 GFLOPS              | Graphics capability does not establish current BSP support for every API/application                                   |
| On-chip SRAM                | Up to 24 MB, with ECC protection                            | Separate from the LPDDR capacity                                                                                       |
| LPDDR                       | 32/64 GB LPDDR5, 256-bit, up to 6400 MT/s                   | Match the MS6 order code; available Linux memory is affected by the running system's reservations                      |
| Integrated storage          | 64/256 GB UFS 3.1                                           | UFS is distinct from the X5 board's removable-media configuration                                                      |
| External storage capability | NVMe through PCIe                                           | Requires appropriate carrier routing, power and BSP support                                                            |
| Operating-temperature entry | −40 to +105 °C, printed as “OP Temp.”                       | The brief does not establish the complete carrier/enclosure ambient or sustained-load thermal qualification            |

[Manufacturer module brief, pp.1–2](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf). The brief advertises more than 160 ONNX standard operators and hardware acceleration for supported operations. This is not evidence that an arbitrary ONNX graph, operator version or precision profile will compile entirely to the BPU. Check the selected toolchain's actual operator and target reports. [M1](https://d-robotics.github.io/rdk_s_doc/en/Quick_start/download?v=5.1.1\&p=RDK+S600).

### Vision, display and media engines <a href="#vision-display-and-media-engines" id="vision-display-and-media-engines"></a>

| Engine/interface       | Documented capability                                                      | Required qualification                                                                                                                                                      |
| ---------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Camera receive         | Six MIPI CSI-2 receivers, four lanes; D-PHY up to 4.5 Gb/s per lane        | Physical camera power, lane routing and supported sensor configuration belong to the carrier and BSP                                                                        |
| C-PHY entry            | The brief lists 23.9 Gb/s in C-PHY mode                                    | The short brief does not define the aggregation/trio-rate convention; do not use it as a derived per-lane routing budget                                                    |
| ISP                    | Four engines, each stated at 1.34 Gpixel/s                                 | Sensor/ISP configuration, format and simultaneous-use conditions still apply                                                                                                |
| Pyramid                | Five engines, each up to 1.34 Gpixel/s                                     | Account for the selected scaling graph and shared memory traffic                                                                                                            |
| GDC                    | Two geometric-distortion-correction engines, each up to 4K at 90 fps       | Panoramic, cylindrical, stereographic and digital PTZ transformations are listed; transform tables, calibration and buffer layout must match the actual pipeline \[M1, p.2] |
| Other image processing | 2D/3D noise reduction; stitching from four virtual camera inputs in DDR    | These are processing capabilities, not four ready-to-connect physical sockets                                                                                               |
| Vision DSP             | Two Vision Q8 processors described as 5-way SIMD/VLIW, each up to 1000 MHz | Use the appropriate software interface and release                                                                                                                          |
| Display transmit       | Two four-lane CSI-2/DSI 1.2 transmitters, up to 2.5 Gb/s per lane          | A carrier bridge/display, pin map and compatible driver are required                                                                                                        |
| JPEG                   | Three engines; 4K at 150 fps in total                                      | Aggregate figure, not a rate guaranteed independently on each engine                                                                                                        |
| H.264/H.265            | Three engines; 4K at 240 fps in total                                      | End-to-end frame rate also depends on input, processing, buffers and output                                                                                                 |

[Module brief, p.2](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf). “Up to” rates should be used for feasibility planning and then measured on the actual pipeline. Do not sum independent maxima into an unqualified simultaneous operating point.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Separate the main and MCU domains <a href="#separate-the-main-and-mcu-domains" id="separate-the-main-and-mcu-domains"></a>

The following counts are module capabilities. The manufacturer's footnote says that low-speed interface counts are maxima and that interfaces have multiplexing relationships. A carrier pin assignment and implemented firmware determine the usable combination. \[M1, p.2].

| Domain | Advertised interfaces                                                                | What must be checked before connection                                                                   |
| ------ | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| Main   | PCIe Gen4 ×4, up to 16 Gb/s per lane, RC/EP                                          | Carrier lane routing, reference clocks, reset, endpoint power and supported mode                         |
| Main   | Three 1 Gb/s SGMII GMACs and three 10 Gb/s USXGMII XGMACs, with TSN capability       | PHYs, magnetics, actual connector exposure and BSP support; these are not six integrated RJ45 sockets    |
| Main   | Four CAN, ten I2C, four I2S/PCM, eight UART, four master/slave SPI                   | Pinmux, electrical levels, domain ownership and driver mapping                                           |
| Main   | One USB 2.0 and one SD interface                                                     | Carrier implementation; do not assign the developer kit's expanded USB 3.x port count to the bare module |
| MCU    | One 1 Gb/s GMAC with TSN, 32 PWM, four UART, twelve CAN                              | Pin assignment, transceivers/PHYs and the actual MCU software configuration                              |
| MCU    | Eight SPI: four master/slave and four master-only; three I2C, eight LIN and nine ADC | Signal conditioning, voltage limits, multiplexing and channel ownership                                  |

The MCU specification states Cortex-R52+ operation up to 1.2 GHz and lists 16 KB data cache, 32 KB instruction cache, 64 KB ATCM, 256 KB BTCM and 256 KB CTCM per core. The brief's front page advertises six MCU cores; its detailed table describes one DCLS core pair and “two Split-Lock cores.” The S600 kit chapter describes the arrangement as `1× DCLS, 2× Split-Lock`. Confirm the exact physical/logical core configuration with the applicable MCU design documentation before allocating independent firmware workloads. Lockstep execution is not the same as that many independent application cores. [M1](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/02_rdk_s600/01_rdk_s600_kit?v=5.1.1\&p=RDK+S600).

### Carrier-design information required before power-up <a href="#carrier-design-information-required-before-power-up" id="carrier-design-information-required-before-power-up"></a>

Obtain and reconcile these items for the exact MS6 revision:

| Design item                               | Current public evidence                                                 | Operation requiring further evidence                                                                        |
| ----------------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Power rails, limits and sequencing        | The short module brief provides no complete module power tree           | Selecting input rails, constructing a custom supply or connecting a bare module                             |
| 699-contact assignment and mating details | Kit chapter identifies J2 and directs the reader to D-Robotics FAE      | Routing signals, choosing connector stack-up, cable adaptation or probing assumed contacts                  |
| Logic levels and power-domain behavior    | Interface capabilities are listed; complete per-contact ratings are not | Connecting GPIO/UART/I2C/SPI or externally powered peripherals                                              |
| Mechanical and thermal design             | 120 × 83 mm outline and general power-management features               | Manufacturing an exact footprint/enclosure or qualifying continuous operation from outline dimensions alone |
| Boot straps and storage initialization    | The kit has its own boot controls and image workflow                    | Transferring kit switch settings or flashing targets to a custom carrier                                    |

The kit's public resource page offers developer-kit 3D models and documentation. A kit STEP file is not automatically the bare module's mechanical release. The mainboard's J1 supply and J2 connector roles must remain separate. [M2](https://d-robotics.github.io/rdk_s_doc/en/Quick_start/download?v=5.1.1\&p=RDK+S600).

The module brief identifies DVFS for CPU/BPU, thermal-zone control, independently controlled compute power domains and Normal/DeepSleep/LightSleep modes. These are reasons to design and validate the complete power/thermal policy; the brief supplies no justified default module wattage or custom-carrier sleep/wake recipe. [M1](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf).

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Keep the module, carrier and release together <a href="#keep-the-module-carrier-and-release-together" id="keep-the-module-carrier-and-release-together"></a>

The current S600 resource-center route selects `p=RDK+S600&v=5.1.1`. Its download table lists the following family resources; the reviewed page also distinguishes online downloads from commercial FTP materials. Reading a download table does not establish that the corresponding archive or SDK has been retrieved or validated. [R1](https://developer.d-robotics.cc/rdk_doc_center/en).

| Resource                    | Version shown on the reviewed S600 resource page | Use                                                                                                   |
| --------------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| System image and BSP        | V5.1.1, dated 23 October 2026                    | Match the carrier, boot/storage implementation and release manifest                                   |
| MCU Cluster-1 image and SDK | V5.1.1                                           | The label does not prove that every MCU cluster/core has an identical public package or configuration |
| OE algorithm toolchain      | V3.7.0                                           | Select the documented S600 target, supported operations and runtime pairing                           |
| OE LLM development package  | V2.0.0                                           | Verify the supported model, target and runtime rather than applying an older S100-only example        |
| XBurn                       | Online table V1.2.2; FTP tool row V1.2.1         | The page contains different labels; confirm the actual supplied tool/release before flashing          |
| hbplayer                    | V2.7                                             | Family image-viewer resource; not proof of a complete custom-carrier camera pipeline                  |

Use the [S600 Model Zoo](https://d-robotics.github.io/model_zoo_doc/en/model_zoo_intro?v=5.1.0\&p=RDK+S600) and [S600 TogetheROS.Bot documentation](https://d-robotics.github.io/tros_doc/en/tros?v=5.1.0\&p=RDK+S600) for family applications, then check their declared board/image/runtime support. A software example for a KS6 development kit needs a demonstrated port to a custom MS6 carrier. An S100 or X5 model binary is not established as compatible merely because all are D-Robotics products. [C1](https://d-robotics.github.io/rdk_s_doc/en/Quick_start/download?v=5.1.1\&p=RDK+S600).

The brief also describes multithreaded VPU/VAE acceleration with FP16 and FP32 support, naming LayerNorm and Softmax as examples. These are vendor-described capabilities, rather than measured performance or proof of arbitrary model support. \[M1, p.1].

The brief introduces HUCP as a unified heterogeneous-compute framework with graph and chained-model optimization, and describes x86 simulation/prototyping support. It does not provide a public, complete callable API contract for a bare module. No function signature, binary-loading flag, MCU packet or pin register is invented here. [M1](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf).

### Plan the development layers <a href="#plan-the-development-layers" id="plan-the-development-layers"></a>

1. **Hardware release:** establish MS6 part, carrier revision, connector/power design and cooling.
2. **Boot/BSP release:** obtain the manufacturer's carrier-compatible image and boot/storage procedure, with checksums and release notes.
3. **Runtime and model:** match the S600 runtime, compiler target, operators, shapes, quantization and preprocessing/postprocessing.
4. **Peripherals:** select sensors, transceivers and bridges actually routed and supported on the carrier.
5. **Robotics integration:** verify frames, timestamps, topic types/QoS and command ownership before connecting an application to controlled equipment.

For the public-reference stage, the smallest useful software action is to record an already commissioned carrier's identity and release. It is not a substitute for missing hardware design information.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: an integration identity record <a href="#first-result-an-integration-identity-record" id="first-result-an-integration-identity-record"></a>

**Prerequisites:** a module whose MS6 code has been physically identified; a manufacturer-approved or already commissioned carrier; its established supply/cooling and boot procedure; a working Linux console; Python 3. This procedure writes a local report only. It does not configure clocks, open control buses, load an SDK or change firmware.

1. Read the module label and carrier revision. Select the corresponding MS6 row above, and retain the vendor delivery/image record. Do not infer the module code from the carrier's KS6 label.
2. If the carrier is not already electrically qualified and commissioned, complete the hardware-design requirements above before applying power. The kit's 12–28 V specification is not a bare-module power instruction.
3. On the commissioned carrier, save the following original example as `module_record.py`. Enter the observed part number at the command line; it is an operator-supplied record, not an automatic hardware identification result.

```python
import argparse
import json
import platform
from pathlib import Path

parser = argparse.ArgumentParser(description="Read-only S600 integration record")
parser.add_argument("--part-number", required=True,
                    choices=["MS6X032064I", "MS6X064256I"])
args = parser.parse_args()

def text(path):
    try:
        return Path(path).read_bytes().replace(b"\x00", b"\n").decode(
            "utf-8", errors="replace").strip()
    except OSError:
        return None

meminfo = text("/proc/meminfo")
mem_total = next((line for line in (meminfo or "").splitlines()
                  if line.startswith("MemTotal:")), None)
print(json.dumps({
    "operator_recorded_module_part": args.part_number,
    "machine_architecture": platform.machine(),
    "kernel_release": platform.release(),
    "device_tree_model": text("/proc/device-tree/model"),
    "device_tree_compatible": text("/proc/device-tree/compatible"),
    "os_release": text("/etc/os-release"),
    "linux_mem_total": mem_total,
    "hardware_match_verified_by_script": False
}, indent=2))
```

4. Run it with the part number actually read from the module. For example, use this command only when the observed label is `MS6X032064I`:

```bash
python3 module_record.py --part-number MS6X032064I > module-bringup.json
python3 -m json.tool module-bringup.json
```

5. Compare the record to the supplied carrier/BSP release manifest. A missing device-tree property is a diagnostic observation; it is not permission to flash an assumed image. Linux `MemTotal` is usable memory reported by the running system and does not independently prove the physical DDR package or order code. `/etc/os-release` describes the operating-system image. [Linux proc documentation](https://www.kernel.org/doc/html/latest/filesystems/proc.html); [os-release specification](https://www.freedesktop.org/software/systemd/man/latest/os-release.html).
6. Keep the report with the physical part/carrier record, toolchain/runtime versions and any future measurement. Add the manufacturer's module-specific power and connector documents before creating a custom-carrier bring-up or application-control procedure.

**Expected result:** a readable JSON record with the operator-entered MS6 part, actual kernel/OS observations and available device-tree/memory fields. No fixed output values, installed S600 runtime, successful BPU inference, MCU communication or physical module match are asserted by this example. The example was syntax checked; it has not been run on S600 hardware.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### The carrier does not boot <a href="#the-carrier-does-not-boot" id="the-carrier-does-not-boot"></a>

Check the exact module/carrier pair, carrier documentation, power sequence, cooling, boot straps and image provenance with the supplier. Avoid repeated power cycling or applying the developer-kit input voltage to an unidentified module contact. Record the carrier's documented LED/serial observations before any supported recovery procedure. The public two-page module brief is insufficient to supply a custom-carrier boot or flashing sequence.

### Linux reports a KS6/carrier model rather than the MS6 order code <a href="#linux-reports-a-ks6carrier-model-rather-than-the-ms6-order-code" id="linux-reports-a-ks6carrier-model-rather-than-the-ms6-order-code"></a>

Keep the software-reported carrier name and the physical module label as separate fields. The device tree is part of the running boot/image configuration. It cannot alone prove which memory/storage module was fitted.

### Available RAM or filesystem space is smaller than the advertised capacity <a href="#available-ram-or-filesystem-space-is-smaller-than-the-advertised-capacity" id="available-ram-or-filesystem-space-is-smaller-than-the-advertised-capacity"></a>

Compare the actual MS6 model, kernel reservations, memory usage, partition layout and mounted storage with its release manifest. A filesystem's free space is not the UFS device's physical capacity, and a `MemTotal` observation alone does not establish a wrong module. Avoid repartitioning a running system to make displayed figures resemble the product brief.

### Can developer-kit USB, RJ45 or display connectors be copied into the module BOM? <a href="#can-developer-kit-usb-rj45-or-display-connectors-be-copied-into-the-module-bom" id="can-developer-kit-usb-rj45-or-display-connectors-be-copied-into-the-module-bom"></a>

Use the module's signal capabilities together with the carrier schematic and pin assignment. Carrier PHYs, bridges, hubs, connectors and their power supplies determine the exposed ports. The kit's six USB 3.2 Type-A ports and populated RJ45 sockets do not become bare-module connectors. [M1](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/02_rdk_s600/01_rdk_s600_kit?v=5.1.1\&p=RDK+S600).

### Can every advertised CAN/PWM/SPI controller be used simultaneously? <a href="#can-every-advertised-canpwmspi-controller-be-used-simultaneously" id="can-every-advertised-canpwmspi-controller-be-used-simultaneously"></a>

The manufacturer explicitly qualifies low-speed counts as maxima with multiplexing. Confirm the required contacts, pinctrl, domain ownership, transceivers and MCU/BSP configuration. Controller counts are not a complete routing map or a guarantee of simultaneous availability. \[M1, footnote on p.2].

### Does the industrial-temperature line or lockstep capability certify the robot system? <a href="#does-the-industrial-temperature-line-or-lockstep-capability-certify-the-robot-system" id="does-the-industrial-temperature-line-or-lockstep-capability-certify-the-robot-system"></a>

Treat those as component-level manufacturer specifications and architectural features. The brief does not establish a finished carrier/enclosure operating envelope, cooling qualification, fault response or application safety certification. Validate the complete system against its actual requirements and applicable documentation.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                           | Purpose and scope                                                                              | Access state                                                                                                       |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| [RDK S600 Module V1P0 brief, Chinese/English specification table, two pages](https://archive.d-robotics.cc/downloads/hardware/rdk_s600/rdk_s600/brief/drobotics_rdk_s600_module_brief_v1p0_zh.pdf) | Exact MS6 codes, module photo, package, compute and interface capabilities                     | Retrieved and read; both pages visually inspected                                                                  |
| [S600 V1P0 developer-kit hardware chapter](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/02_rdk_s600/01_rdk_s600_kit?v=5.1.1\&p=RDK+S600)                      | KS6 models, carrier J1/J2 distinction and family interface context                             | Read; kit-specific instructions remain carrier-specific                                                            |
| [S600 V5.1.1 resource summary](https://d-robotics.github.io/rdk_s_doc/en/Quick_start/download?v=5.1.1\&p=RDK+S600)                                                                                 | Software versions, public module/kit briefs, commercial-material paths and certification links | Index read; commercial archives and their contents not retrieved                                                   |
| [Current D-Robotics resource center](https://developer.d-robotics.cc/rdk_doc_center/en)                                                                                                            | Supported documentation and toolchain entry points                                             | Read                                                                                                               |
| [S600 Model Zoo](https://d-robotics.github.io/model_zoo_doc/en/model_zoo_intro?v=5.1.0\&p=RDK+S600)                                                                                                | Family model examples and deployment documentation                                             | Resource-center destination identified; actual example support must be checked before execution                    |
| [S600 TogetheROS.Bot](https://d-robotics.github.io/tros_doc/en/tros?v=5.1.0\&p=RDK+S600)                                                                                                           | Robotics middleware, components and application documentation                                  | Resource-center destination identified; not a custom-carrier compatibility certification                           |
| Module power/699-contact pinout, mating-stack drawings and carrier design package                                                                                                                  | Necessary for wiring, manufacturing and new-carrier power-up                                   | Not established by the public brief; obtain the applicable manufacturer package through the hardware-page FAE path |
| Bare-module CAD                                                                                                                                                                                    | Exact module height, keep-outs and mechanical release                                          | Not established by the reviewed index; its developer-kit 3D model is a separate asset                              |

The resource summary lists module certification documents separately from kit and expansion-board documents. Match a certificate's exact product/revision and scope rather than treating a directory link as certification of the completed robot. [R1](https://d-robotics.github.io/rdk_s_doc/en/Quick_start/download?v=5.1.1\&p=RDK+S600).

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The primary reference is the manufacturer's V1P0 S600 Module brief, including the footnote limiting interface counts. Its two pages were text-read and visually inspected. The current S600 kit and resource-summary pages were read to distinguish MS6 module identity, KS6 carrier interfaces and the available V5.1.1 family resources.

The original identity-record script passed Python syntax checking. No S600 board connection, SDK/model execution, firmware download/flash, MCU operation, power/thermal measurement or carrier manufacturing was performed. The module's power rails, complete connector assignment and custom-carrier boot procedure remain explicit information gaps. This page provides a manufacturer specification/integration reference while those procedures remain excluded.

**Related guides:** [D-Robotics boards, modules and peripherals](./).

* [D-Robotics RDK S600 — V1P0 hardware and RDKOS 5.1.1 development](rdk-s600-manufacturer-engineering-reference.md)
* [RDK S600 Camera Expansion Board: eight-link GMSL and power reference](rdk-s600-camera-expansion-board-reference.md)
* [RDK S600 MCU Port Expansion Board: CAN ownership and pin reference](rdk-s600-mcu-port-expansion-board-reference.md)
