# RobStride LeRobot Humanoid Motor Set Development Guide

{% hint style="info" %}
[**View ROBSTRIDE LeRobot Humanoid Motor Set on OpenELAB**](https://openelab.io/products/lerobot-humanoid-robstride-motor-set)

**Model/family:** ROBSTRIDE LeRobot Humanoid Motor Set · **OpenELAB SKU:** `ROBSTRIDE-Huggingface`
{% endhint %}

![RobStride LeRobot Humanoid Motor Set Development Guide](../../.gitbook/assets/lerobot-humanoid-motor-set-development-guide.webp)

_Product image: OpenELAB._ [_Image source_](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/TB-ROBSTRIDE-huggingface_01.webp?v=1779450854)_._

[Product at OpenELAB](https://openelab.io/products/lerobot-humanoid-robstride-motor-set) · [Manufacturer wiki hub](./)

## Product scope and applications

The **Hugging Face LeRobot Humanoid Motor Set, ROBSTRIDE-Huggingface**, supplies 12 integrated RobStride actuators for biped development. The current OpenELAB packing list matches the motor counts in the upstream **LeRobot Humanoid biped** BOM. This is an actuator set: controller, IMU, CAN adapter, power system, printed structure, bearings and fasteners are separate build requirements unless expressly included in your quotation.

Use it for actuator commissioning, joint-mechanism experiments and the documented 12-DOF biped build. The upstream hardware repository currently scopes its build assets to the biped platform; an upper-body CAD view is not a complete upper-body kit or a validated walking policy. HOPE-Jr arm/hand instructions describe a different hardware path.

## Confirmed contents and integration map

| Actuator    | Quantity | Upstream BOM location | Reference final IDs |
| ----------- | -------: | --------------------- | ------------------- |
| ROBSTRIDE00 |        2 | Torso                 | 1, 7                |
| ROBSTRIDE02 |        2 | Hip-Z                 | 2, 8                |
| ROBSTRIDE03 |        4 | Thigh assemblies      | 3, 4, 9, 10         |
| ROBSTRIDE05 |        4 | Shin assemblies       | 5, 6, 11, 12        |

Sources: [current set contents](https://openelab.io/products/lerobot-humanoid-robstride-motor-set), [pinned BOM](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/bom/bom_buy.csv) and [commissioning procedure](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/electronics/motor_commissioning.md). These IDs belong to that reference build; match your runtime configuration before adopting them.

Read the individual [00 manual](robstride-00-instruction-manual.md), [02 manual](robstride-02-instruction-manual.md), [03 manual](robstride-03-instruction-manual.md) and [05 manual](robstride-05-instruction-manual.md) for model-specific supply limits, torque ratings, mounting, connector drawings and protocol details. Peak torque is not a continuous operating rating. Do not apply one actuator's wiring or thermal limits to the entire set.

## Hardware and software prerequisites

The reference BOM specifies a **Raspberry Pi 5**, **BNO055 or BNO085 IMU**, and a **SAVVYCANFD dual-channel USB CAN-FD adapter**. Use the full BOM for mechanical parts and the project's wiring resources for each branch. Specify the supply and protection for the actual actuator combination and operating loads; a logic-only bench current limit is not the full robot's supply requirement.

The runtime README reviewed at commit **e4dc62795e83b2e69580cad4d3229bdb558e912e** documents **Ubuntu, Python 3.13 and uv**. Follow its dependency profiles and record hardware, runtime and robot-model revisions together. This runtime is a separate repository; installing the main LeRobot Python package alone does not complete the biped's CAN/IMU integration.

## Getting started: inspect and commission one actuator

Prepare a secured, unloaded actuator with an accessible hardware power cutoff. Keep the output clear of people and mechanisms. Follow the exact model's power polarity, supply range and CAN wiring before energizing it. Commission one motor at a time before installing it in a limb.

1. Obtain the hardware repository and select the reviewed revision. Open the [commissioning tool](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/config/commission_motor.py), its dependencies and model-ID map.
2. Set up the actual SocketCAN interface as documented for your adapter and reference runtime. Confirm the interface and error counters with `ip -details -statistics link show can0`. The commissioning code opens a 1 Mbit/s bus; the runtime's CAN-FD setup also specifies its data bitrate. Match both host and actuator configuration.
3. From the hardware repository root, inspect the available command arguments without connecting to a bus:

```bash
python hardware/config/commission_motor.py --help
python hardware/config/commission_motor.py wizard --help
```

4. For the first reference-build **00** motor assigned **ID 1**, the source-checked configuration command is:

```bash
python hardware/config/commission_motor.py wizard   --channel can0 --motor-model o0 --new-id 1 --skip-motion-test
```

This **changes protocol/ID and requests power cycling**; it is not a read-only diagnostic. The model token uses the letter **o** followed by a digit. Repeat for each motor with the correct model and an unused permitted ID.

**Keep `--skip-motion-test` for initial setup.** The reviewed script's default motion routine enables the actuator and requests a ±180-degree sway. That is unsuitable for an assembled constrained joint. Its scan also transmits protocol probes and a MIT clear-fault command, so it is not passive monitoring.

Expected commissioning result: the tool reports the selected ID in **MIT mode** after the requested restarts, without running its default sway. Record serial number, model, physical joint, final ID, protocol and firmware. Investigate any unexpected device/protocol result before connecting the next motor.

## Assembly, first power and runtime progression

Use the project's [assembly guide](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/assembly/assembly_guide.md), connector photos and cabling diagrams. Connector documentation marks several harness pin maps as partial: verify actual polarity/continuity rather than filling the gaps from color or plug shape. Use correct bus-end termination and check CAN-H/CAN-L and ground policy for the actual harness.

After wiring checks, follow the [first-power procedure](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/electronics/first_power_on.md). Its **2 A limit is for the first logic-only phase**, where motion is not expected. Progress to one actuator at low limits, sign/encoder checks and small movements only after those checks pass.

Start the assembled robot runtime in **state\_only** with automatic motor enable disabled. Check all IDs, valid joint states, IMU orientation, offsets, watchdogs and mechanical limits. Complete the runtime's zeroing/calibration and one-joint direction validation before a supported low-amplitude test. Keep the structure supported; policy inference and free-standing locomotion require a separately validated model, calibration and policy.

## Troubleshooting and FAQ

| Symptom or question                      | Check and next step                                                                                                                             |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor not detected                       | One motor connected, correct supply/polarity, CAN interface state, bus termination, bitrate and actual firmware/protocol.                       |
| ID/protocol changes do not persist       | Follow the requested power-cycle sequence and verify on the isolated motor before continuing.                                                   |
| More than one motor responds             | Stop batch commissioning; isolate motors and reconcile duplicate IDs and logs.                                                                  |
| Wrong direction or zero pose             | Disable motion; compare joint mapping, encoder sign, offsets and mechanism assembly before calibration.                                         |
| Can I run a LeRobot example immediately? | Use the biped runtime and its state-only/calibration sequence; examples for an arm, hand or unrelated motor bus do not establish compatibility. |
| Is the set a complete humanoid?          | It is the listed motor set. Compare all remaining mechanical/electrical parts with the selected BOM revision.                                   |

## Technical documents and software

| Resource                                                                                                                                                           | Use                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------- |
| [Hardware repository](https://github.com/huggingface/lerobot-humanoid-hardware)                                                                                    | Build scope, BOM and reference CAD                       |
| [Pinned BOM](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/bom/bom_buy.csv)                      | Motor counts and remaining buy parts                     |
| [Commissioning source](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/config/commission_motor.py) | Exact CLI arguments, protocol/ID and motion behavior     |
| [Connector catalog](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/hardware/electronics/connectors.md)     | Photos, known pin mapping and documented gaps            |
| [Cabling diagrams](https://github.com/huggingface/lerobot-humanoid-hardware/tree/8171f5799b046f8a696e7b787a34226f119c4797/hardware/electronics/cabling)            | Branch routing                                           |
| [Assembly](https://github.com/huggingface/lerobot-humanoid-hardware/blob/8171f5799b046f8a696e7b787a34226f119c4797/docs/assembly/assembly_guide.md)                 | Mechanical build                                         |
| [Runtime and calibration](https://github.com/Virgileboat/lerobot-humanoid-runtime/tree/e4dc62795e83b2e69580cad4d3229bdb558e912e)                                   | CAN/IMU integration, state-only bring-up and calibration |
| [Official motor documents](https://github.com/RobStride/Product_Information)                                                                                       | Actuator-specific documents and drawings                 |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
