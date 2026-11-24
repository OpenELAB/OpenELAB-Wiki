---
description: >-
  Inventory the12 RobStride humanoid actuators,verify the biped BOM,bus/ID map
  and commissioning side effects,then stage state-only calibration.
---

# RobStride LeRobot Humanoid Motor Set Development Guide

{% hint style="info" %}
[**View the Hugging Face LeRobot Humanoid Motor Set on OpenELAB**](https://openelab.io/products/lerobot-humanoid-robstride-motor-set)

**SKU:** `ROBSTRIDE-Huggingface` · **Contents:** RS00 × 2, RS02 × 2, RS03 × 4, RS05 × 4 · **Scope:** twelve actuator modules; a controller, power system, structure and walking policy are separate integration work.
{% endhint %}

## Product overview <a href="#product-scope-and-applications" id="product-scope-and-applications"></a>

This set supplies the **four exact actuator classes** in the reviewed 12-DOF LeRobot Humanoid biped BOM. The useful first result is a reconciled physical inventory and valid status from each isolated motor, followed by the correct twelve-node/runtime map. It is not a completed humanoid or a ready-to-run locomotion package. [Verified packing list](https://openelab.io/products/lerobot-humanoid-robstride-motor-set), [pinned hardware BOM](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/bom/bom_buy.csv).

![LeRobot RobStride motor set](../../.gitbook/assets/lerobot-humanoid-motor-set-development-guide.webp)

_Existing OpenELAB product illustration; retained native asset. Reference build details come from the dated project files, not the illustration._

## Applications <a href="#applications" id="applications"></a>

Use the set for one-motor commissioning, bench validation of a biped joint, model/encoder identification and the documented legged-research build. Inventory and interface validation precede simulation-to-real or policy evaluation. The reviewed runtime is a 12-DOF **biped without arms**; upper-body CAD and HOPE-Jr arm/hand tutorials do not expand this kit’s contents or establish software compatibility. [Hardware README](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/README.md), [runtime README](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md).

Peak torque, reduction, mass, cooling and connector layout differ by motor. Design joint loading, harness branches and the DC supply for the combined duty cycle. Never add the four peak-torque values to obtain a robot payload or size supply current by adding peak **phase** currents.

## Specifications <a href="#confirmed-contents-and-integration-map" id="confirmed-contents-and-integration-map"></a>

| Supplied model | Count | Peak /rated output reference | Supply range | Reduction | Reference joint IDs |
| -------------- | ----- | ---------------------------- | ------------ | --------- | ------------------- |
| RS00           | 2     | 14 /5 N·m                    | 24–60 V      | 10:1      | 1, 7 torso          |
| RS02           | 2     | 17 /6 N·m in exact manual    | 24–60 V      | 7.75:1    | 2, 8 hip-Z          |
| RS03           | 4     | 60 /20 N·m in October manual | 24–60 V      | 9:1       | 3, 4, 9, 10 thigh   |
| RS05           | 4     | 5.5 /1.6 N·m                 | 15–60 V      | 7.75:1    | 5, 6, 11, 12 shin   |

Rated torque depends on the individual manual’s speed, cooling and thermal test conditions. All four have a 48 V nominal reference; **24–60 V is their common published overlap**, not a guarantee of full performance throughout it. Choose a specific supply/test point and control limits for the mechanism. [RS00](robstride-00-instruction-manual.md), [RS02](robstride-02-instruction-manual.md), [RS03](robstride-03-instruction-manual.md), [RS05](robstride-05-instruction-manual.md), [reference ID map](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/electronics/motor_commissioning.md).

| Reference build item                         | Required outside this motor set / implication                                            |
| -------------------------------------------- | ---------------------------------------------------------------------------------------- |
| Raspberry Pi 5                               | Controller in upstream BOM; not included by the motor list                               |
| BNO055 or BNO085                             | IMU in BOM; mount orientation/calibration must match selected backend                    |
| SAVVYCANFD2CH adapter                        | Project’s proven reference; two Linux CAN channels                                       |
| Bearings, fasteners, printed/metal structure | Use the exact BOM and assembly revision                                                  |
| Host                                         | Ubuntu, Python 3.13, `uv` in reviewed runtime                                            |
| Software split                               | Hardware repository, real/simulation runtime and LeRobot integration are separate layers |

[BOM](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/bom/bom_buy.csv), [runtime environment](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md). A CAN-FD-capable adapter does not itself change an installed motor from its private protocol to MIT or CAN-FD firmware.

## Hardware and connections <a href="#hardware-and-software-prerequisites" id="hardware-and-software-prerequisites"></a>

### Build a physical map before making a chain <a href="#build-a-physical-map-before-making-a-chain" id="build-a-physical-map-before-making-a-chain"></a>

Label every motor with model, serial, voltage/driver revision, physical joint, desired node ID and bus. Keep RS03’s separate power/signal connectors distinct from the compact motors’ combined XT30(2+2) layout. Use each exact connector face drawing; a wire-side view is mirrored. Check continuity and polarity with all drive supplies removed. [Individual model guides above](./), [project connector catalog](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/electronics/connectors.md).

The reference adapter’s DB9 pins are **2=CAN-L, 3=GND, 7=CAN-H**. This statement applies to that project adapter/harness, not every DB9 product. The upstream connector catalog explicitly marks motor/inter-cable pin maps as **partial**. Do not fill unspecified contacts from colors or connector appearance. Use the actual manufacturer motor drawing and approved harness documentation before power. It calls for bus-end 120 Ω termination and power lines designed for the actual branch current; its 30 A branch target is not a fuse or connector rating for arbitrary cable. [Connector catalog](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/electronics/connectors.md).

### Logic-only power is not full-drive commissioning <a href="#logic-only-power-is-not-full-drive-commissioning" id="logic-only-power-is-not-full-drive-commissioning"></a>

The first-power document starts with controller logic only, a **2 A** bench limit and roughly 1 A maximum expected idle current. It then separately introduces one actuator with low limits and only later tiny motion around neutral. This does **not** tell a builder to power all twelve motors through a 2 A logic supply. Keep the structure supported, provide accessible drive-power isolation and inspect voltage/temperature/noise/communication at each stage. [First-power phases](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/electronics/first_power_on.md).

Mounting sequence, bearings, link alignment and cable routing are described in the [assembly guide](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/assembly/assembly_guide.md). Check the exact CAD/STL and screw engagement against the motor’s real housing; do not force a link onto a miscentered output or use zero calibration to hide wrong mechanical assembly.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Three separately versioned layers <a href="#three-separately-versioned-layers" id="three-separately-versioned-layers"></a>

| Layer               | Reviewed source / role                                                                                                              |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Hardware            | Commit `8171f5799b046f8a696e7b787a34226f119c4797`; BOM, CAD, assembly, cables, commissioning utility                                |
| Runtime             | Commit `e4dc62795e83b2e69580cad4d3229bdb558e912e`; Python 3.13/uv, CAN+IMU, simulation, state guards, calibration and policy runner |
| LeRobot integration | In-repository humanoid implementation/config; not automatically installed by a generic arm workflow                                 |

[Hardware source](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/README.md), [runtime source](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md). Retain the runtime’s submodules and dependency lock. Use `uv sync --extra sim` for simulation, and only the documented policy/imu/viz/gamepad extras needed for the actual real build. Do not run arbitrary installation scripts copied from a source without examining the selected version.

The hardware commissioning script imports `python-can` and opens classical SocketCAN at 1 Mbit/s. The runtime README configures CAN interfaces with 1 Mbit/s arbitration plus 5 Mbit/s data phase and `fd on`; match the **actual adapter, firmware and frame type** instead of assuming every motor sends CAN-FD merely because the adapter supports it. [Commissioning source](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/config/commission_motor.py), [runtime bus configuration](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md).

### Source behavior that changes the commissioning decision <a href="#source-behavior-that-changes-the-commissioning-decision" id="source-behavior-that-changes-the-commissioning-decision"></a>

The pinned wizard can scan, switch protocol, change IDs and request power cycles. Its scan is **not passive**: it transmits probes including a MIT clear-fault command. Its default motion routine enables the motor and requests a broad ± 180° sway; the brief prose recipe elsewhere in the project describes a different 90° test. Use the actual code as the behavior reference and keep **`--skip-motion-test`** during initial setup. Skipping the sway does not turn protocol/ID writes into read-only operations. [Exact source](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/config/commission_motor.py).

The reference runtime requires calibration of motor signs, offsets, joint limits, IMU frame and ankle mappings. Start in **`state_only` with `auto_enable=False`** and inspect all valid state before selecting control. The staged policy runner eventually enables drives and sends a zero pose; it is not a first passive test. [Calibration and lifecycle README](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md), [reference helper](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/ipython_helper.py).

## Getting started <a href="#getting-started-inspect-and-commission-one-actuator" id="getting-started-inspect-and-commission-one-actuator"></a>

### Original offline inventory check <a href="#original-offline-inventory-check" id="original-offline-inventory-check"></a>

1. Count and label the twelve received motors against the packing table. Save serial/role/revision information before assembly. Download the pinned hardware repository, then inspect the BOM without connecting a CAN adapter:

```bash
git clone https://github.com/huggingface/lerobot-humanoid-hardware.git
cd lerobot-humanoid-hardware
git checkout 8171f5799b046f8a696e7b787a34226f119c4797
```

2. Save the following original checker at the repository root as `check_motor_bom.py`:

```python
import csv
from collections import Counter

counts = Counter()
with open('hardware/bom/bom_buy.csv', newline='', encoding='utf-8') as stream:
    for item in csv.DictReader(stream):
        if item['category'] == 'motor':
            counts[item['name']] += int(item['qty_robot'])
expected = {'RobStride O0':2, 'RobStride O2':2,
            'RobStride O3':4, 'RobStride O5':4}
assert dict(counts) == expected, f'BOM changed: {dict(counts)}'
print('BOM_12_MATCH', dict(counts))
```

```bash
python3 check_motor_bom.py
```

**Expected result:** `BOM_12_MATCH` with 2, 2, 4, 4 counts, or an assertion identifying a changed source BOM. This checks the reference file, not delivered hardware; compare the printed record with actual labels. `O0` in the CSV is the model label, while the tool token below is lowercase letter `o` followed by digit 0. [Pinned BOM fields](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/bom/bom_buy.csv).

### Isolated motor readback before state changes <a href="#isolated-motor-readback-before-state-changes" id="isolated-motor-readback-before-state-changes"></a>

3. Fixture one unloaded motor, connect its exact power/CAN harness with power off, and establish the individually confirmed node/protocol. Use its model guide’s **read-only voltage/position/speed** workflow first. Do not run a whole-robot enable or use the wizard to replace a missing electrical check.
4. Record a baseline and only then prepare the pinned commissioning utility in a separate Python environment:

```bash
python3 -m venv .venv-commission
source .venv-commission/bin/activate
python -m pip install python-can
python hardware/config/commission_motor.py --help
python hardware/config/commission_motor.py wizard --help
```

5. For an isolated RS00 assigned reference ID1, after verifying intended state changes, use the documented CLI form with the motion test suppressed:

```bash
python hardware/config/commission_motor.py wizard   --channel can0 --motor-model o0 --new-id 1 --skip-motion-test
```

Follow its power-cycle checkpoints, retain the prior state and verify the **final ID and MIT protocol** before moving the cable. Repeat one unit at a time using the exact model/ID map. Do not use `--yes` to bypass the initial physical checks.

**Expected result:** the selected isolated motor verifies at its intended ID/protocol without the wizard’s sway test. An unexpected ID or protocol result blocks adding the next unit. [Source CLI and model map](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/config/commission_motor.py).

### Whole system: state, calibration, then small motion <a href="#assembly-first-power-and-runtime-progression" id="assembly-first-power-and-runtime-progression"></a>

6. Assemble the documented mechanism and bus routing; the reference runtime maps `can0` to IDs 1–6 and `can1` to 7–12. Verify labels and branch wiring against that specific runtime before assuming left/right correspondence.
7. Install the pinned runtime with Python 3.13/uv and its submodules. Use the documented `state_only`/`auto_enable=False` workflow and validate joint states, pose, limits and IMU orientation. Preserve motor signs/offsets with the physical robot.
8. Follow the runtime’s interactive zeroing, IMU calibration and single-joint nudge procedures only after state is coherent. Keep state bounds, command-jump checks, ankle guards and E-STOP logic active. Support the robot before a controlled low-amplitude test; no free-standing policy run is part of this first-result procedure.

**Expected result:** twelve correctly mapped valid states and a calibrated supported mechanism before one intentional small-joint movement. A simulated policy rollout does not establish physical torque limits or balance. [Runtime calibration steps](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md), [hardware first-power phases](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/electronics/first_power_on.md).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faq" id="troubleshooting-and-faq"></a>

| Symptom                                     | Specific checks / supported recovery                                                                                       |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Only one class of motors responds           | Compare private/MIT protocol state and node IDs, not only electrical bitrate. Isolate before changing it.                  |
| Duplicate IDs or unexpected wizard result   | Stop adding motors; reconcile physical labels, protocol and power-cycle sequence one unit at a time.                       |
| Visualized limb is mirrored                 | Inspect bus assignment, model map, sign and offset tables before moving or recalibrating it.                               |
| IMU orientation wrong                       | Select actual backend/address/frame and complete calibration; do not compensate by disabling ankle/state guards.           |
| Current exceeds logic-only stage limit      | Remove power and inspect logic wiring before introducing motor power.                                                      |
| E-STOP at start                             | Read exact bounds/ankle/feedback reason; support near the correct reference pose and inspect state-only data.              |
| CAN interface up but state missing          | Verify motor power, termination, bitrate, frame/protocol and expected ID on the correct channel.                           |
| Can this set walk after installing LeRobot? | No complete tested system is implied; hardware, runtime, calibration and a compatible policy remain separate requirements. |

## Downloads and technical documents <a href="#technical-documents-and-software" id="technical-documents-and-software"></a>

| Resource                                                                                                                                                                                                                                                                         | Scope                                                                     |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [Hardware repository](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/README.md) / [BOM](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/bom/bom_buy.csv) | Selected biped revision and parts outside the motor set                   |
| [Assembly guide](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/assembly/assembly_guide.md)                                                                                                                         | Subassembly order, bearings, fasteners and structure                      |
| [Connector catalog](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/electronics/connectors.md)                                                                                                                   | Actual adapter pins and explicitly partial harness maps                   |
| [Commissioning tool](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/config/commission_motor.py)                                                                                                                 | Exact options, write/protocol/reboot/motion behavior                      |
| [First power](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/electronics/first_power_on.md)                                                                                                                         | Logic-only, one-actuator and tiny-motion phases                           |
| [Runtime](https://github.com/Virgileboat/lerobot-humanoid-runtime/blob/e4dc62795e83b2e69580cad4d3229bdb558e912e/README.md)                                                                                                                                                       | Environment, simulation, CAN, IMU, logging, calibration and LeRobot layer |
| [Individual RobStride manuals/CAD](https://github.com/RobStride/Product_Information)                                                                                                                                                                                             | Use 00/02/03/05 exact model resources; not a generic all-motor pinout     |

### Pinned cabling and runtime resources

* [Humanoid electronics/cabling source](https://github.com/huggingface/lerobot-humanoid-hardware/tree/8171f5799b046f8a696e7b787a34226f119c4797/hardware/electronics/cabling) — source-specific harness layout and assembly context; verify actual connectors, conductor sizing and protection for the received build.
* [Reviewed humanoid runtime snapshot](https://github.com/Virgileboat/lerobot-humanoid-runtime/tree/e4dc62795e83b2e69580cad4d3229bdb558e912e) — complete code/configuration navigation for the commit discussed above. Inspect the selected startup path and command ownership before running a connected robot.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **24 November 2026** against the store’s exact packing list, upstream BOM, commissioning source, assembly/connector/first-power files and pinned runtime. The source utility’s default motion and nonpassive scan are explicitly distinguished from original offline inspection and individual readback.

**Validation:** source reviewed; original Python inventory example parsed for syntax. Installation, CAN communication, protocol/ID writes, calibration, simulation and physical motion were **not run**. Manufacturer/project resources retain their licenses; expected outcomes are reproducible checkpoints, not bench claims.
