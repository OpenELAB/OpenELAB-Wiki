---
description: >-
  Identify the A1 motor component and its OpenELAB listing, compare its legacy
  actuator contract, and complete an offline coordinate checkpoint before bench
  integration.
---

# Unitree A1 Motor: Component Identification and SDK Development

> **Verified OpenELAB listing identity:** [**Unitree High Torque Ultra-thin Four-legged Robot Joint Micromotor**](https://openelab.io/products/unitree-high-torque-ultra-thin-four-legged-robot-joint-micromotor), motor option **SKU `Unitree-4Motor`**. The store label does not literally say “A1”; its description and 605 g / 33.5 Nm / 21 rad/s / 20–40 V specification tuple match the [manufacturer A1 Motor](https://www.unitree.com/A1/motor). Confirm the delivered A1 nameplate and revision before selecting a protocol. No SKU named “A1 motor” has been invented.

## Product overview <a href="#product-overview" id="product-overview"></a>

This is the integrated **A1 joint motor component**, not the A1 quadruped robot. The motor's serial SDK and the robot's network/legacy SDK are separate interfaces with different ownership and release boundaries. Naming an A1 motor category in an actuator README does not qualify every assembled A1 robot or third-party joint installation. [Pinned actuator SDK README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md)

The research snapshot is 24 November 2026: the manufacturer A1 product table, actual OpenELAB catalog record, relevant motor-space support table and pinned public C++/Python/header/build sources were read. There is no separate A1-specific portal manual coverage claim in this guide.

## Applications <a href="#applications" id="applications"></a>

The manufacturer positions A1 Motor for load-bearing foot-robot and other machinery joints. It integrates the brushless motor, optimized planetary reduction, driver and a crossed-roller bearing in a compact housing. Application mechanics still determine impact load, support, cooling, joint range and wiring strain relief. Its maximum instantaneous torque is not a continuous torque rating. [Manufacturer A1 Motor](https://www.unitree.com/A1/motor)

Use the component-specific SDK to design an integration only after the delivered motor has been identified. Do not connect a host motor program to a motor bus that an assembled robot controller owns. No power, firmware, cable or mechanical compatibility with a GO-M8010-6 or IM6014 follows from all three exposing torque and position abstractions.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                                | Manufacturer A1 motor value                                        |
| ----------------------------------- | ------------------------------------------------------------------ |
| Mass                                | 605 g                                                              |
| Maximum instantaneous output torque | 33.5 Nm                                                            |
| Maximum joint speed                 | 21 rad/s                                                           |
| Working voltage                     | 20–40 V DC                                                         |
| Torque constant                     | 0.9287 Nm/A                                                        |
| Communication                       | RS485                                                              |
| Communication control period        | 1 kHz headline; not a measured host implementation rate            |
| Encoder resolution                  | 15 bit                                                             |
| Advertised feedback                 | Torque, angle, angular velocity, angular acceleration, temperature |
| Advertised commands                 | Torque, angle, angular velocity, stiffness, damping                |

These values come from the [A1 motor table](https://www.unitree.com/A1/motor). They do not establish a simultaneous torque/speed operating point, ambient temperature range, continuous current rating, ingress rating, exact joint travel or connector torque. The product page's winding, coating and salt-spray descriptions concern manufacturing characteristics, not a complete assembly's environmental certification.

The motor SDK support table separately states **4.8 Mbps** for the A1 motor category. Do not substitute the GO motor's 4 Mbps or B1 category's 6 Mbps. The 9.1 reduction value used in the motor development examples is a software-reference value; confirm the physical variant and returned ratio against the delivered motor. [Motor SDK support table](https://doc-cdn.unitree.com/8/156/en/8_156_en) [Motor Python example and model table](https://doc-cdn.unitree.com/8/157/en/8_157_en)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

The confirmed electrical interface is RS485 with a 20–40 V operating supply. A1-specific connector orientation and the delivered cable/adapter revision were not established by the read product page and SDK headers. **Do not reuse the GO XT30 drawing, the IM6014 mirrored-port drawing or the servo TTL pinout.** Obtain the A1 motor drawing and inspect the actual harness before applying power.

A qualified host adapter must support the A1 category's 4.8-Mbps half-duplex rate, direction turnaround and motor reference grounding. It is not enough for an adapter to advertise “RS485.” Supply capacity, wire gauge, termination, protection and braking-energy absorption must be designed for the actual load and topology rather than borrowed from a GO demo. [Manufacturer A1 motor](https://www.unitree.com/A1/motor) [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en)

The OpenELAB listing's `Unitree-MotorAccessory` option is an **accessory kit**, not another motor SKU. Its existence does not establish contents or pinout for every revision. The current motor-space Download Page links an A1 STEP file, listed-only in this research; use the exact mechanical drawing and mounting engagement provided for the delivered component. No fastener torque or hot-plug permission is established here.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Source pin, dependencies and build boundary <a href="#source-pin-dependencies-and-build-boundary" id="source-pin-dependencies-and-build-boundary"></a>

The read repository is [unitree\_actuator\_sdk at 5b79a42d81cd69adac1367db79efdb972a898fd1](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md), which names **GO-M8010-6 motor, A1 motor and B1 motor**. The source provides C++ and Python examples; the portal also lists an STM32 HAL platform, without proving that the GO F103 wiring/example is an A1 BSP.

The pinned README states GCC ≥5.4 for x86 and ≥7.5 for ARM. Its actual [CMakeLists.txt](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/CMakeLists.txt) requires CMake ≥3.1 and C++14; `aarch64` selects a prebuilt Arm64 library and the alternative branch selects Linux64. Other CPUs, Windows/macOS and Python ABIs are not thereby qualified. Bundled pybind11 builds a compiled Python module; the exact interpreter ABI, shared-library dependencies and architecture must match. The source pin does not declare a general Python minimum version.

Build-only reference after a later reviewed checkout, not performed here:

```sh
cmake -S /path/to/reviewed/unitree_actuator_sdk -B /path/to/local/build
cmake --build /path/to/local/build
```

Those targets include motor actuation examples, an ID-changing tool and a Python extension. No target was built or run for this guide. A successful build would not qualify firmware, wiring or live motion.

### Public API and old wire family <a href="#public-api-and-old-wire-family" id="public-api-and-old-wire-family"></a>

The high-level command names are `motorType`, `id`, `mode`, `tau`, `dq`, `q`, `kp` and `kd`; command and data must both select the A1 motor category. `queryMotorMode` and `queryGearRatio` are declared in the public header, but their implementations are in a prebuilt library. Inspect `MotorData.correct` and the transaction result before consuming feedback; its initial false value and an old data object must not be reported as a fresh valid receive. SerialPort's 4-Mbps/16-byte defaults are GO-shaped defaults, not proof of an A1 transport configuration. [Public command/data API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/unitreeMotor.h) [Serial API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/serialPort/SerialPort.h)

The packed A1/B1 source defines a **34-byte command** (`4+26+4`) and **78-byte reply** (`4+70+4`). The four-byte header has two start bytes, an eight-bit motor ID and a reserved byte; its comment assigns **0xBB** to broadcast without reply. This is not GO's 17/16-byte nibble-ID protocol, nor the IM6014/servo 20/26-byte family. A portal example table discusses IDs 0–2 for A1/B1, whereas the raw field is wider; that field width is not approval for every numeric ID or bus size. Exact delivered firmware addressing still needs confirmation. [Pinned packed A1/B1 header](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_A1B1.h) [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en)

Raw command comments use torque ×256, velocity ×128, position ×16384/(2π), position gain ×2048 and velocity gain ×1024. They also include modify/read fields and low-frequency fan/music/LED fields. The reply structure includes temperatures, torque, velocities, acceleration, rotor/output position and sensor-related fields. A declared field is not proof that a particular motor has every sensor populated or calibrated. The CRC32 helper's word algorithm was read, but the complete packed-message encoder implementation is not visible in this source audit; no complete independent A1/B1 wire parser or CRC coverage rule is invented here. [CRC32 helper](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/crc/crc32.h)

### Coordinate convention and demo hazards <a href="#coordinate-convention-and-demo-hazards" id="coordinate-convention-and-demo-hazards"></a>

The SDK README describes command values on the **rotor side**. Ideal output position/speed divide by reduction ratio, ideal output torque multiplies by it, and equivalent rotor gains divide output gains by `r²`. In addition, the README and `example_a1_motor_output.cpp` apply A1/B1-specific gain factors: rotor position gain additionally divided by **26.07**, velocity gain additionally multiplied by **100**. These are API-generation-specific factors; do not apply them to GO, IM6014 or J288/S288, or remove them solely because the physical gear conversion seems sufficient. Their exact delivered firmware mapping must be checked. [Conversion notes](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md) [Output-side example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_a1_motor_output.cpp)

The A1 C++ and Python examples select FOC, use nonzero damping and a desired rotor speed proportional to the ratio, and call `sendRecv` repeatedly. The output-side example initially communicates in FOC, obtains a coordinate, then executes a sinusoidal output trajectory of approximately ±90°. It is **not** a read-only position viewer. A 200-µs sleep in an example is not a verified 5-kHz communication rate. [A1 C++ example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_a1_motor.cpp) [A1 Python example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/python/example_a1_motor.py)

A later live integration needs the delivered model, drive and hardware revision, firmware identifier, adapter, operating system, serial device, bus rate and ID recorded together. Assign one process exclusive ownership of the serial bus; close the assistant, other terminal tools and any robot controller before a qualified bench session. Each active status poll can transmit a control/state transaction. None of these motors provides a DDS subscriber-only first result. A successful frame CRC is not proof of model identity, firmware compatibility, safe mounting or fresh physical measurement.

For an eventual receive log, preserve immutable frame bytes with model provenance, monotonic receipt time, local frame counter and the exact parser revision. Reject mismatched IDs, length, header, CRC and invalid SDK results. Measure arrival age separately from changes in position: a stationary motor can have valid fresh feedback. On loss or stale feedback, stop the application under a separately engineered stop procedure; closing a port or attempting a final zero command cannot guarantee delivery over a broken link.

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Save the complete original Python block below as a local file.
2. Run that file with an existing Python 3 interpreter; no package installation is needed.
3. Compare the printed OFFLINE PASS result and preserve all unverified metadata flags.

### First result: identify the component and check coordinates offline <a href="#first-result-identify-the-component-and-check-coordinates-offline" id="first-result-identify-the-component-and-check-coordinates-offline"></a>

Use an existing Python 3 interpreter with this complete original block. It accepts only a deliberately labeled A1 motor worksheet, checks the component/baud distinction and converts a synthetic rotor angle with the example ratio 9.1. It opens no device and imports no Unitree software.

```python
"""Original offline A1 component checkpoint; no SDK or device access."""
from math import isfinite

def inspect(record):
    if record['component'] != 'A1 motor' or record['whole_robot']:
        raise ValueError('This is an A1 motor component, not an A1 robot')
    if record['sdk_selector'] != 'A1' or record['baud'] != 4_800_000:
        raise ValueError('Do not substitute a GO or B1 motor contract')
    ratio = 9.1
    rotor_q = float(record['synthetic_rotor_q'])
    if not isfinite(rotor_q):
        raise ValueError('Nonfinite sample')
    return dict(component='A1 motor', output_position=rotor_q / ratio,
                sdk_family_named=True, delivered_firmware_verified=False,
                data_origin='original offline record')

if __name__ == '__main__':
    record = dict(component='A1 motor', whole_robot=False,
                  sdk_selector='A1', baud=4_800_000, synthetic_rotor_q=9.1)
    result = inspect(record)
    print('A1 motor OFFLINE PASS output_position=%.3f rad' % result['output_position'])
    print('delivered_firmware_verified=False')
```

Expected output is `A1 motor OFFLINE PASS output_position=1.000 rad` and `delivered_firmware_verified=False`. That false flag is intentional: mathematical consistency and a named SDK family do not verify the received product or its firmware. The synthetic 9.1-rad value is neither a live measurement nor a target to send.

### Conditions for a later bench plan <a href="#conditions-for-a-later-bench-plan" id="conditions-for-a-later-bench-plan"></a>

Resolve the listing-to-nameplate match, exact motor/drive/firmware revision, manufacturer wiring and mounting drawings, approved adapter and transport parameters, supported IDs and a stopped-state feedback method. Mechanically support the assembly, engineer independent power removal, and give one controller exclusive bus ownership. Record raw validated data with receipt time and source pin before considering gains or trajectories. A1 robot network development requires the robot-specific guide and does not follow from this component checkpoint.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Question                                             | Evidence-based answer                                                                                                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Is `Unitree-4Motor` an A1 robot?                     | No. It is the store's motor option; A1 correspondence is based on matching product text/specifications, with delivered-nameplate confirmation still required. |
| Does no reply mean the motor is broken?              | Not established. Record adapter, power, actual rate, ID, port ownership, firmware and validity results first. A GO-default serial configuration may be wrong. |
| Can I use GO's packet decoder?                       | No. The pinned A1/B1 header is 34/78 bytes and uses different ID and field conventions.                                                                       |
| Can I copy the A1 output example as a logger?        | No. It eventually commands a sinusoidal trajectory; the speed examples also actuate.                                                                          |
| Are `kp` and `kd` physical output gains?             | The source uses rotor-side values plus A1/B1-specific conversion factors. Match API generation before tuning.                                                 |
| What if a struct has plausible values after failure? | Reject invalid/stale data. Inspect transaction success and `MotorData.correct`; uninitialized command fields and stale cached state are not fresh feedback.   |
| Does a compiler/import success prove support?        | It proves that environment step only. The prebuilt binary, Python ABI, adapter and delivered firmware remain separate checks.                                 |
| What thermal or reset value should I use?            | No complete A1 revision-specific fault/timeout/recovery table was established. Do not borrow GO, IM6014 or servo thresholds/reset recipes.                    |

For an issue report, retain exact model, firmware, OS/architecture, SDK commit, adapter, de-energized wiring, port identity and raw transaction validity. Seek the purchase channel or Unitree's [support contact in the README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md) with that evidence. Do not repeatedly change IDs, modes, firmware or gains as a connection diagnostic.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

Read originals: [manufacturer A1 Motor](https://www.unitree.com/A1/motor), [motor support table](https://doc-cdn.unitree.com/8/156/en/8_156_en), [pinned README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md), [CMake build](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/CMakeLists.txt), [command/data API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/unitreeMotor.h), [serial declarations](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/serialPort/SerialPort.h), [A1/B1 packet structures](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_A1B1.h), [C++ speed example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_a1_motor.cpp), [output-coordinate example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_a1_motor_output.cpp) and [Python example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/python/example_a1_motor.py).

The actual [GO motor-space download chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en) lists an [A1 STEP model](https://unitree-firmware.oss-cn-hangzhou.aliyuncs.com/tool/A1_motor.STEP). It was listed, not opened or dimensionally verified. No exact A1 firmware package, connector drawing or full A1-specific service manual was established by these sources. Do not choose the GO HW2 firmware or an IM6014 archive for this component.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The [OpenELAB listing](https://openelab.io/products/unitree-high-torque-ultra-thin-four-legged-robot-joint-micromotor) uses its exact catalog title and actual motor SKU here. The accessory kit remains separate. Manufacturer A1 text/specifications and pinned SDK files were actually read; whole-robot network SDK support and every source in the wider portal were not inferred from them.

The repository root [license](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/LICENSE) is BSD 3-Clause, requiring its notices and disclaimer when redistributing covered source/binaries. That file does not establish a blanket license for manuals, photographs, firmware, all prebuilt dependencies or third-party code. This page's original worksheet is independent explanatory code.

Only static checks and original offline synthetic exercises were performed. No Unitree SDK was installed, imported, built or executed; there was no serial, DDS, ROS, hardware, firmware or motion test. Store model labeling, exact hardware/firmware/SDK pair, connector orientation, supported IDs, complete protocol coverage, fault recovery and continuous duty remain explicit gaps. Readiness: **draft for independent review**.

### Read source catalog <a href="#read-source-catalog" id="read-source-catalog"></a>

| Actual read primary chapter                                         | Treatment on this page                                                                                                       |
| ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en)            | Support categories, rotor command and rate table versus whole robot                                                          |
| [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en) | Python wrapper/model selector, actuation and calibration-table conflict                                                      |
| [DownloadPage](https://doc-cdn.unitree.com/8/1483/en/8_1483_en)     | Manuals, SDK/tools, examples, CAD, HW2release, drivers/thirdparty/hardware links and footprints with read/listed distinction |

**Related documentation:** [Unitree model and development directory](./).
