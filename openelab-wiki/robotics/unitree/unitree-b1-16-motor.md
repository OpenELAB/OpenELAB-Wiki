---
description: >-
  Identify the B1-16 motor component, separate its published hardware ratings
  from the B1 actuator SDK category, and prepare an offline integration evidence
  checkpoint.
---

# Unitree B1-16 Waterproof Joint: Hardware and Development Boundaries

> **Manufacturer reference — no verified OpenELAB SKU.** This guide covers the [Unitree B1-16 Waterproof Joint](https://www.unitree.com/b1-16), a **motor component**, not the B1 quadruped robot. No store listing or SKU has been fabricated.

## Product overview <a href="#product-overview" id="product-overview"></a>

B1-16 combines a high-torque joint motor and driver in a sealed assembly. The manufacturer's product table gives component ratings and a feedback/control feature set. The public actuator SDK separately names a **B1 motor** category, but the read README/header do **not explicitly identify B1-16 hardware or a compatible firmware release**. That distinction governs this page: the related software category is useful evidence, not a complete compatibility assurance. [Pinned actuator README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md)

Research snapshot: 24 November 2026. The actual manufacturer B1-16 product page, motor support table, pinned actuator headers/build configuration and B1 C++/Python example text were read. No full B1-16-specific portal manual or firmware release pair was established.

## Applications <a href="#applications" id="applications"></a>

The manufacturer positions the joint for demanding mechanisms, including inspection and agricultural/research applications where water and dust protection matter. The **IP68 headline** belongs to the component product description. It does not establish a depth/time immersion rating for every installed joint, connector state, modified harness or complete robot. Obtain the exact revision's test conditions and installation limits before environmental use. [Manufacturer B1-16](https://www.unitree.com/b1-16)

Mechanical design still needs the actual load spectrum, impact and bearing limits, mounting engagement, cable strain relief, thermal path and access for isolation. Peak torque does not establish continuous underwater duty or safe load-holding on loss of power. An unqualified B1 speed example is not a commissioning plan for a high-torque B1-16 mechanism.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                         | Manufacturer B1-16 value / boundary                                |
| ---------------------------- | ------------------------------------------------------------------ |
| Component identity           | B1-16 Super Robot Waterproof Joint                                 |
| Mass                         | 1740 g                                                             |
| Maximum instantaneous torque | 140 Nm                                                             |
| Working voltage              | 36–64 V DC                                                         |
| Torque constant              | 2.165 Nm/A                                                         |
| Protection headline          | IP68; exact depth/time/connector conditions not established here   |
| Communication                | RS485                                                              |
| Communication control period | 1 kHz advertised, not a measured host/adapter rate                 |
| Encoder resolution           | 15 bit                                                             |
| Advertised feedback          | Torque, angle, angular velocity, angular acceleration, temperature |
| Advertised commands          | Torque, angle, angular velocity, stiffness, damping                |

These are the exact [B1-16 product-table](https://www.unitree.com/b1-16) statements. Continuous torque/current, maximum speed, ambient temperature limits, complete ingress test conditions, connector pinout, reduction ratio and revision-specific fault behavior are not supplied by that read table. Do not fill them with GO, A1, IM6014 or a whole B1 robot specification.

The general motor SDK table gives **B1 category 6 Mbps**, and a general development example table gives a B1 ratio of **8.66**. Those are category-level software references, **not independently verified B1-16 firmware or gear-ratio assignments**. [Motor SDK support table](https://doc-cdn.unitree.com/8/156/en/8_156_en) [Python/model reference table](https://doc-cdn.unitree.com/8/157/en/8_157_en)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

The confirmed B1-16 electrical facts are a 36–64 V working supply and RS485 communication. The read sources do not establish the delivered connector orientation, cable assembly, grounding diagram, termination scheme or exact compatible adapter. Obtain those from Unitree for the identified hardware revision. Do not use a GO XT30 drawing or servo TTL wiring as a substitute.

Size the power path for the actual load, drive current and regenerated energy; a torque constant alone does not establish a fuse or supply-current rating. Design independent accessible power removal and mechanical load support. A last host message cannot guarantee stop over a failed communication link, and an unpowered mechanism may move under gravity.

The IP68 headline is not permission to connect exposed live contacts underwater or use an unspecified cable gland. The exact sealing, mating and environmental maintenance instructions remain missing. No mount torque or internal repair procedure is invented here. [Manufacturer B1-16 product page](https://www.unitree.com/b1-16)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Related SDK evidence, with an explicit model gap <a href="#related-sdk-evidence-with-an-explicit-model-gap" id="related-sdk-evidence-with-an-explicit-model-gap"></a>

The pinned [unitree\_actuator\_sdk README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md) names B1 motor alongside A1 and GO-M8010-6. It does not name B1-16. Its common [public API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/unitreeMotor.h) provides `MotorType.B1`, a mode-query function and a gear-ratio query, plus command/data objects. The exact B1-16 hardware, bootloader, firmware and binary-library compatibility need manufacturer confirmation before any device use. The presence of that enum alone cannot close the gap.

Dependencies described by the source are GCC ≥5.4 for x86 and ≥7.5 for ARM, CMake ≥3.1 and C++14. The actual [CMakeLists.txt](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/CMakeLists.txt) selects prebuilt Arm64 for `aarch64`, otherwise Linux64, and builds active examples, ID-changing utility and a bundled-pybind11 Python extension. Matching CPU, OS, shared-library ABI and Python interpreter ABI are necessary; no universal Python minimum or support for every non-aarch64 CPU is established. No package was built or installed here.

Build-only reference for a later reviewed compatible checkout, separate from execution:

```sh
cmake -S /path/to/reviewed/unitree_actuator_sdk -B /path/to/local/build
cmake --build /path/to/local/build
```

Even a successful build would not prove an exact B1-16 firmware match. The portal's generic STM32 HAL support category does not establish a B1-16-specific BSP, wiring or MCU pin assignment.

### B1/A1 wire generation is not GO or servo <a href="#b1a1-wire-generation-is-not-go-or-servo" id="b1a1-wire-generation-is-not-go-or-servo"></a>

The packed [A1/B1 header](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_A1B1.h) defines 34-byte host and 78-byte reply structures, including an eight-bit ID with 0xBB broadcast/no-reply in a source comment. Torque, speed, position and gain encodings differ from GO; it also declares modify/read and low-frequency fields, sensor-related payloads and a CRC word. These are read source contracts for the **B1/A1 category**, not a claim that a delivered B1-16 uses every field or sensor. Exact encoder implementation and packet-CRC coverage were not verified from the linked binary; this guide does not publish a guessed complete B1-16 raw parser.

The general example table's small motor-ID ranges and the packed field's full eight-bit capacity do not establish B1-16-supported addressing. Likewise, SerialPort's default 4-Mbps/16-byte receive settings are not the general B1 category's 6-Mbps/78-byte configuration. The common API's transaction validity and `MotorData.correct` must be checked if a future matched integration is approved. Plausible stale values do not constitute a valid sample. [Serial declarations](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/serialPort/SerialPort.h) [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en) [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en)

### Coordinates and active examples <a href="#coordinates-and-active-examples" id="coordinates-and-active-examples"></a>

The actuator README describes rotor-side command quantities, gear conversion and A1/B1-specific gain factors: divide output position/velocity gains by `r²`, additionally divide position gain by **26.07** and multiply velocity gain by **100** for that SDK generation. Do not extend those factors to other motor families or claim they are B1-16-calibrated without the missing firmware match. No B1-16-specific ratio or output conversion is applied in this page's first result. [Coordinate/gain notes](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md)

The B1 C++ and Python examples select B1 FOC, nonzero damping and a rotor velocity proportional to the queried gear ratio, then loop over `sendRecv`. They cause actuation. Their print statements and 200-µs sleeps do not make them passive viewers or measured real-time benchmarks. [B1 C++ example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_b1_motor.cpp) [B1 Python example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/python/example_b1_motor.py)

A later live integration needs the delivered model, drive and hardware revision, firmware identifier, adapter, operating system, serial device, bus rate and ID recorded together. Assign one process exclusive ownership of the serial bus; close the assistant, other terminal tools and any robot controller before a qualified bench session. Each active status poll can transmit a control/state transaction. None of these motors provides a DDS subscriber-only first result. A successful frame CRC is not proof of model identity, firmware compatibility, safe mounting or fresh physical measurement.

For an eventual receive log, preserve immutable frame bytes with model provenance, monotonic receipt time, local frame counter and the exact parser revision. Reject mismatched IDs, length, header, CRC and invalid SDK results. Measure arrival age separately from changes in position: a stationary motor can have valid fresh feedback. On loss or stale feedback, stop the application under a separately engineered stop procedure; closing a port or attempting a final zero command cannot guarantee delivery over a broken link.

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Save the complete original Python block below as a local file.
2. Run that file with an existing Python 3 interpreter; no package installation is needed.
3. Compare the printed OFFLINE PASS result and preserve all unverified metadata flags.

### First result: preserve unresolved compatibility offline <a href="#first-result-preserve-unresolved-compatibility-offline" id="first-result-preserve-unresolved-compatibility-offline"></a>

This complete original Python worksheet checks the component identity and published voltage range, then reports missing engineering evidence. It imports no vendor package, opens no port and calculates no unverified B1-16 output ratio. Run it with an existing Python 3 interpreter.

```python
"""Original B1-16 evidence checkpoint; no inference of a live protocol match."""
def inspect(record):
    if record['component'] != 'B1-16 joint' or record['whole_robot']:
        raise ValueError('B1-16 is a component, not the B1 robot')
    if record['advertised_voltage'] != (36, 64):
        raise ValueError('Do not substitute another motor voltage range')
    missing = [key for key in ('exact_firmware_sdk_pair', 'connector_drawing',
                              'independent_stop_plan') if not record.get(key)]
    return dict(component='B1-16 joint', related_sdk_category='B1 motor',
                missing=missing, exact_protocol_verified=False,
                data_origin='original offline worksheet')

if __name__ == '__main__':
    result = inspect(dict(component='B1-16 joint', whole_robot=False,
                          advertised_voltage=(36, 64)))
    print('B1-16 OFFLINE PASS: unresolved evidence retained')
    print('exact_protocol_verified=False missing=%d' % len(result['missing']))
```

Expected output is `B1-16 OFFLINE PASS: unresolved evidence retained`, then `exact_protocol_verified=False missing=3`. “PASS” means the worksheet retained the gaps correctly; it does not mean the motor or SDK passed a test. The false compatibility field is intentional, including when worksheet entries are later populated: documents must be independently reviewed, not converted into compatibility by a truthy string.

### Gate before bench work <a href="#gate-before-bench-work" id="gate-before-bench-work"></a>

Obtain a manufacturer statement pairing the exact B1-16 hardware/firmware with an SDK release and adapter. Obtain wiring, mounting, supply-current/regeneration, ingress conditions, fault/timeout and stopped-state feedback instructions. Review the independent stop/load-support plan and exclusive bus ownership. Until those are resolved, stay with offline source and worksheet checks; no motor-control, calibration or flash sequence is established here.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Question                                              | Source-backed response                                                                                                                  |
| ----------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Is B1-16 a B1 robot SKU?                              | No. It is a separate joint component; no exact OpenELAB listing was verified.                                                           |
| Does the B1 enum prove B1-16 support?                 | No. The read source names the B1 motor category without an explicit B1-16 firmware/hardware pair.                                       |
| Can I use 6 Mbps and ratio 8.66 immediately?          | Those are B1-category references. Their exact application to B1-16 remains unverified.                                                  |
| Does IP68 allow any underwater installation?          | No complete depth/time/connector conditions were established; obtain the exact component and installation test conditions.              |
| Which firmware, fault code or timeout should I use?   | No B1-16-specific matched release or complete table was established. Do not copy GO/IM6014/servo semantics.                             |
| Why does an SDK program print numbers after no reply? | A stale or invalid data object may still contain values. A future approved integration must check actual transaction and data validity. |
| Can I run the B1 example to identify the part?        | No. It commands FOC velocity and cannot establish identity safely.                                                                      |
| Does 1 kHz mean any USB host can deliver it?          | It is a manufacturer control-period headline, not a verified multi-node host benchmark.                                                 |

For a support request, supply the exact B1-16 nameplate, drive/firmware IDs, intended load and environment, proposed adapter and wiring, and relevant source pin. Do not repeatedly change modes or flash an unrelated firmware package to diagnose silence. The manufacturer product page and pinned SDK README are the appropriate source boundaries for this evidence request.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

Read sources: [B1-16 manufacturer page](https://www.unitree.com/b1-16), [motor SDK support table](https://doc-cdn.unitree.com/8/156/en/8_156_en), [pinned actuator README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md), [build configuration](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/CMakeLists.txt), [command/data API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/unitreeMotor.h), [serial API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/serialPort/SerialPort.h), [A1/B1 packed structures](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_A1B1.h), [B1 C++ example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_b1_motor.cpp) and [B1 Python example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/python/example_b1_motor.py).

No exact B1-16 wiring drawing, CAD package, firmware binary, BSP archive, full service manual or current release matrix was established by these read sources. A GO or IM6014 download page is not a substitute. The related repository's [BSD 3-Clause root license](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/LICENSE) applies to material covered by it, not automatically to manufacturer manuals, photos, firmware or all third-party/prebuilt content.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The source evidence distinguishes manufacturer B1-16 hardware ratings, the B1 motor software category and the whole B1 robot. Read sources are linked directly and the repository is pinned to 5b79a42d81cd69adac1367db79efdb972a898fd1. No unlisted SKU, exact firmware match or complete B1-16 portal coverage has been invented.

Validation consists of static document checks and original offline synthetic worksheet cases. No Unitree SDK was installed, imported, built or executed; there was no serial, DDS, ROS, motor, hardware, motion, firmware or immersion test. Exact B1-16 SDK compatibility, connector/mounting details, continuous duty, environment, fault and release behavior remain open engineering items. Readiness: **draft for independent review**, with offline preparation only until those model-specific gaps are resolved.

### Read source catalog <a href="#read-source-catalog" id="read-source-catalog"></a>

| Actual read primary chapter                                         | Treatment on this page                                                                                                       |
| ------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en)            | Support categories, rotor command and rate table versus whole robot                                                          |
| [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en) | Python wrapper/model selector, actuation and calibration-table conflict                                                      |
| [DownloadPage](https://doc-cdn.unitree.com/8/1483/en/8_1483_en)     | Manuals, SDK/tools, examples, CAD, HW2release, drivers/thirdparty/hardware links and footprints with read/listed distinction |

**Related documentation:** [Unitree model and development directory](./).
