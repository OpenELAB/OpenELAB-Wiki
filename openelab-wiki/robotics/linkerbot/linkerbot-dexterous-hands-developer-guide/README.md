---
description: >-
  Seven-model LINKERBOT dexterous-hand comparison, integration safety, SDKs,
  source manuals and development tutorials.
---

# LINKERBOT Dexterous Hands — Seven-Model Developer Wiki

{% hint style="info" %}
[**L6 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l6-11) · [**L20 Lite on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-lite) · [**L20 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-21) · [**L30 Tendon-Driven on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l30-l30) · [**O6 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-o6-11)

**Family:** LINKERBOT dexterous hands · **Seven manual models:** L6 / L20 Lite / L20 / L30 Standard / O6 / O20 / O30. O20 and O30 currently have **no verified OpenELAB .io product match**.
{% endhint %}

### Product overview

This series provides seven **model-specific engineering entry guides** for Linkerbot dexterous robotic hands, using the exact manufacturer product manuals supplied by OpenELAB. It also explains correct power selection, CAN versus CAN FD versus RS485, mounting, commissioning, ROS 2/Python SDK support, and bounded first tests.

**The L series and O series are not electrically or mechanically interchangeable.** Some models have passive joints and fewer individually commanded DoF than physical joints; some have optional tactile sensors; some use unique multipin connectors. Consult the original [Linkerbot manual collection](../) for manufacturer diagrams.

### Applications

* Dexterous end-effector selection and mechanical integration for research robots.
* Joint-control and tactile-data acquisition, with validity, timestamp and freshness checks.
* Humanlike gestures and supervised grasp experiments after safe setup.
* ROS 2/Python development with exact model, side, transport, firmware and SDK pairing.

### Specifications

| Model (manual revision)                    | Controlled DoF / total joints                      | Bus; manual voltage                                               | Mass; closing time                       |
| ------------------------------------------ | -------------------------------------------------- | ----------------------------------------------------------------- | ---------------------------------------- |
| **L6** V1.4 (2026-05-18)                   | **6 / 11** (6 active, 5 passive)                   | CAN / RS485; **24 V ±10%**                                        | 607 g; 0.35 s                            |
| **L20 Lite** V1.0 (2025-09-11)             | **10 / 20** (10 active, 10 passive)                | CAN / RS485; **24 V ±10%**                                        | 800 g; 1.2 s                             |
| **L20** V1.3 (2026-08-04)                  | **16 / 21** (16 active, 5 passive)                 | CAN / RS485; manual says **24–48 V**, connector marks 24 V        | ≈1200 g; 0.98 s                          |
| **L30 Standard, tendon** V1.3 (2025-10-27) | **17 / 21** (17 active, 4 passive; wrist included) | CAN FD in manual; **24 V in manual, store information conflicts** | ≈1400 g; 0.2 s                           |
| **O6** V1.4 (2026-07-21)                   | **6 / 11** (6 active, 5 passive)                   | CAN / CAN FD / RS485 / EtherCAT in manual; **24–48 V**            | 370 g; time not confirmed in this manual |
| **O20** V1.2 (2026-06-05)                  | **16 / 16**, all active                            | **CAN FD**, distinct connector; **24 V ±10%**                     | 888 g; 0.88 s                            |
| **O30** V1.0 (2026-07-10)                  | **20 / 20**, all active                            | **CAN / CAN FD**, distinct connector; **24–48 V**                 | 730 g; 0.8 s                             |

Sources: the **seven supplied manuals**, product parameter and installation sections. Do not use these headline maximum-load values as a host robot's certified dynamic payload. The store title “L20 Lite 20-DOF” reflects 20 joints, whereas the manual and the newer ROS 2 model matrix describe **10 active joints**.

#### Identity and evidence gaps

* Exact matched OpenELAB variant examples: **L6** `Linker-Hand-L6-1`; **L20 Lite** `Linker-Hand-L20-Lite-1`; **L20** `Linker-Hand-L20-1`; **L30 tendon** `Linker-Hand-L30-JQ1`; **O6** `Linker-Hand-O6-1`. A SKU identifies a **particular side/interface option**, not every variant.
* **L30 Standard:** the OEM manual specifies **24 V / CAN FD**, while the matching storefront offers **12 V** in a comparison and CAN/RS485 choices. **Stop before powering or connecting this exact variant** until OEM/seller confirms matching power and transport. The separate **L30 direct-drive** item is not covered by the uploaded tendon-driven manual.
* **O20 / O30:** valid OEM manuals were provided, but no matching products appeared in the connected OpenELAB .io catalog; these guides remain source-backed drafts with product URL/SKU unverified.
* **O6:** the manual's latest interface options include CAN FD and EtherCAT, but the current store variants identified were CAN/RS485. Check the actually ordered interface.

### Hardware and connections

1. Read the label: **model, left/right side, exact variant, interface, serial/firmware**. Identify the supplied adapter and the correct physical mounting flange.
2. Read the original **model-specific mechanical and connector diagrams**. L6/L20 Lite/L20/L30 manuals describe XT30 (2+2) CAN connections; **O20 and O30 use different connectors** that must not be wired by an XT30 pin diagram.
3. Match DC voltage to the **exact delivered hand and cable revision**, and disconnect power before connecting. CAN, CAN FD, RS485 and EtherCAT require their own verified transport and compatible adapter.
4. Firmly mount the hand with the required screw diameter, penetration and clearance from the matching OEM drawing. Prevent finger trapping and confirm a physical or software stop/disconnect method before motion.
5. For L30, carry out documentation-only inspection pending resolution of its power/transport mismatch. Never use a successful network discovery message as permission for actuator writes.

### Software and development resources

| Source                                                                                                                       | Compatibility and use                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Linkerbot Hand ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                            | Current source documents **all seven models**; Humble / Ubuntu 22.04 or Jazzy / Ubuntu 24.04                                                                   |
| [ROS 2 model differences](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Active joint counts, CAN versus CAN FD and capability-specific methods                                                                                         |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                 | Original Python tooling and model-specific bus examples                                                                                                        |
| [Older ROS / ROS 2 SDKs](https://github.com/linker-bot/linkerhand-ros-sdk)                                                   | Manuals link these earlier repositories; check their exact support list before use                                                                             |
| OEM host tools                                                                                                               | L20 Lite: `can\_bridge.exe` plus `dashboard.exe` on localhost:9090; O20: `020\_hand\_ui.exe`; O30: `O30\_hand\_ui.exe`; L30: `dexterous\_hand\_controller.exe` |

The new ROS 2 driver lists native CAN and CAN-FD endpoints. A sold **RS485** option must not be assumed compatible with a CAN-only launch configuration. Use actual SDK capability discovery and live-state validity flags.

### Getting started

#### First working result — identify the hand and read state

1. Complete the exact model guide's **power, interface, mounting and manual checks**. For L30 or unverified O20/O30 SKU/electrical variants, stay at the documentation-only inventory stage.
2. After the manufacturer's [ROS 2 SDK setup and adapter preparation](https://github.com/linker-bot/linkerbot-hand-ros2-sdk), the README documents:

```bash
ros2 launch linkerbot_hand_ros hand.launch.py discover:=true
```

3. In a second ROS 2 shell, observe a **read-only** angle sample:

```bash
ros2 topic echo --once --qos-reliability best_effort /linkerbot_hand/state/angles
```

4. Inspect the manufacturer [model guide](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) for the hand's **joint names, expected count, raw units, identity and stale/valid status**. Record actual observed device, side, interface, firmware and SDK revision.

**Expected result:** one valid live angle observation matching the model's effective controlled joint count (6, 10, 16, 17 or 20). The commands shown do **not** send joint motion. **If no fresh sample arrives:** check actual bus/adapter, OS permissions, model-side identification and firmware, not a motion command.

### Model-specific developer guides

| Model                                                  | Engineering guide                                                       | Primary source                                                                  |
| ------------------------------------------------------ | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **L6** — 6 active, 11 total joints                     | [L6 development guide](linker-hand-l6-development-guide.md)             | [L6 OEM manual](../linker-hand-l6-product-manual.md)                            |
| **L20 Lite** — 10 active, 20 total joints              | [L20 Lite development guide](linker-hand-l20-lite-development-guide.md) | [L20 Lite OEM manual](../linker-hand-l20-lite-product-manual.md)                |
| **L20** — 16 active, 21 total joints                   | [L20 development guide](linker-hand-l20-development-guide.md)           | [L20 OEM manual](../linker-hand-l20-product-manual.md)                          |
| **L30 Standard (tendon)** — 17 active, 21 total joints | [L30 development guide](linker-hand-l30-tendon-development-guide.md)    | [L30 tendon OEM manual](../linker-hand-l30-standard-edition-product-manual.md)  |
| **O6** — 6 active, 11 total joints                     | [O6 development guide](linker-hand-o6-development-guide.md)             | [O6 OEM manual](../linker-hand-o6-product-manual.md)                            |
| **O20** — 16 active joints                             | [O20 development draft](linker-hand-o20-development-guide.md)           | Supplied V1.2 manual; **store match and permanent download pending**            |
| **O30** — 20 active joints                             | [O30 development draft](linker-hand-o30-development-guide.md)           | [O30 OEM manual](../linker-hand-o30-product-manual.md); **store match pending** |

**Important:** These are not interchangeable products. L30's store/manual voltage and transport conflict blocks power-up instructions; O20 and O30 lack verified .io product SKU links.

### Shared developer tutorials

1. [**Power, flange and CAN/CAN-FD setup**](linkerbot-tutorial-1-hardware-and-buses.md) — approved adapter and wiring preflight, Linux bus settings.
2. [**ROS 2 installation and read-only hand state**](linkerbot-tutorial-2-ros2-readonly-state.md) — driver build, identity/capability and live angle metadata.
3. [**Tactile telemetry and data validation**](linkerbot-tutorial-3-tactile-telemetry.md) — optional sensors, 4×10 vs 6×11 vs 6×12, presence/staleness, rate differences.
4. [**Windows host software commissioning**](linkerbot-tutorial-4-windows-commissioning.md) — L20 Lite Dashboard, O20/O30 version reads and L30's blocked commissioning.

Proceed in this order: **identify variant → verify voltage/mount/bus → read device state → inspect tactile options → test bounded motion separately only after safety validation**.

### Troubleshooting and FAQs

**Why does L20 Lite send 10 joint commands despite “20-DOF” in the listing?** Its manual distinguishes **20 physical joints, 10 active**. Passive joints should not be treated as independent actuators.

**Can O20 or O30 use the ordinary XT30 CAN wiring?** No. Their OEM manuals show distinct connector designs and CAN-FD tooling. Refer to the exact diagram, cable and orientation.

**Does every hand include tactile sensing?** No: **O6** and **L30 Standard** manuals describe tactile as **optional**. Confirm installed hardware before enabling tactile software.

**How fast is tactile data?** It varies; O20's manual states **30 Hz tactile refresh**, which is different from its **1000 Hz bus communication**.

### Downloads and technical documents

* [Existing LINKERBOT manuals, drawings and installation references](../).
* [Current seven-model ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk) and [per-model feature guide](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).
* [Python SDK](https://github.com/linker-bot/linkerhand-python-sdk).
* Uploaded **O20 V1.2 product manual** (not yet distributed as a permanent downloadable GitBook attachment).

### References and validation

* Seven original supplied LINKERBOT PDFs: L6 V1.4; L20 Lite V1.0; L20 V1.3; L30 Standard V1.3; O6 V1.4; O20 V1.2; O30 V1.0.
* Connected OpenELAB .io product catalog, exact five matched product records and options, reviewed 2026-11-21.
* [Current ROS 2 SDK README](https://github.com/linker-bot/linkerbot-hand-ros2-sdk), [models](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.

**Documentation reviewed:** manual text, diagrams and source documentation. **Software execution:** not run. **Hardware validation:** not run. **Before publishing powered integration instructions:** resolve L30 variant electrical conflict, O20/O30 store matches, and validate bus/firmware, actual joint data and stop behavior on a physical unit.
