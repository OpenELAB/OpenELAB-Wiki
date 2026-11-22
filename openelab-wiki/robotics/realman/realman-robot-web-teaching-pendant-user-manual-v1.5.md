---
description: >-
  Shared WEB Teaching Pendant operation reference. For product-specific setup
  and specifications, use RealMan RM65 Series User Manual V1.2.0 or RealMan
  ECO65 Series User Manual V1.2.0.
---

# RealMan Robot WEB Teaching Pendant User Manual V1.5

{% hint style="info" %}
[**View RM65-B on OpenELAB**](https://openelab.io/products/realman-rm65-b-6-dof)

**Model:** RM65-B · **SKU:** `Realman-RM65-B`

[**View RM65-6F on OpenELAB**](https://openelab.io/products/realman-rm65-6f-6-dof)

**Model:** RM65-6F · **SKU:** `Realman-RM65-6F`

[**View RM65-B-V on OpenELAB**](https://openelab.io/products/realman-rm65-b-v-6dof)

**Model:** RM65-B-V · **SKU:** `Realman-RM65-B-V`

[**View ECO65-B on OpenELAB**](https://openelab.io/products/realman-eco65-b-6-dof)

**Model:** ECO65-B · **SKU:** `Realman-ECO65-B`

[**View ECO65-6F on OpenELAB**](https://openelab.io/products/realman-eco65-6f-6-dof)

**Model:** ECO65-6F · **SKU:** `Realman-ECO65-6F`
{% endhint %}

## Model and firmware entry points

Use [RM65](realman-rm65-series-user-manual-v1.2.0.md) or [ECO65](realman-eco65-series-user-manual-v1.2.0.md) for product-specific setup and the newer supplied revisions; use [shared commissioning/SDK guide](realman-arm-commissioning-and-sdk.md) before running development examples. This V1.5 page retains the existing source material and figures; it is not a universal current-firmware screen reference. Motion, force control, calibration and program execution require the exact delivered controller manual. Reviewed 22 November 2026; software/hardware tests not run.

## Preserved teaching-pendant reference

### RealMan RM65-B 6-DOF Ultra-Lightweight Robot Arm

{% embed url="https://openelab.io/products/realman-rm65-b-6-dof" %}

### RealMan RM65-6F Robot Arm With Six-Axis Force Sensor

{% embed url="https://openelab.io/products/realman-rm65-6f-6-dof" %}

### RealMan RM65-B-V Vision Robot Arm With Depth Camera

{% embed url="https://openelab.io/products/realman-rm65-b-v-6dof" %}

### RealMan ECO65-B 6-DOF Collaborative Robot Arm

{% embed url="https://openelab.io/products/realman-eco65-b-6-dof" %}

### RealMan ECO65-6F Robot Arm With Six-Axis Force Sensor

{% embed url="https://openelab.io/products/realman-eco65-6f-6-dof" %}

###

For model-specific installation wiring specifications maintenance and troubleshooting use the dedicated manuals below

[realman-rm65-series-user-manual-v1.2.0.md](realman-rm65-series-user-manual-v1.2.0.md "mention")

[RealMan ECO65 Series User Manual V1.2.0](realman-eco65-series-user-manual-v1.2.0.md)

### Contents

### Model and Version Applicability

This page reproduces the official RealMan Robot WEB Teaching Pendant User Manual V1.5 dated November 1 2023. The shared operating instructions apply to the RM65 and ECO65 basic integrated six-axis force and supported vision-arm configurations listed above.

Before using controller-specific or interface-specific instructions compare the installed controller and software versions with the official version correspondence. Later firmware may change screen layouts supported functions model adaptations and API compatibility.

* Current RealMan version correspondence and release notes https://develop.realman-robotics.com/en/robot/releaseNotes/releaseNotes/
* \- Official hardware preparation guide for RealMan robot series https://develop.realman-robotics.com/en/robot/quickUseManual/index.html
* \- Official RM65 series parameters and model identification https://develop.realman-robotics.com/en/robot/robotParameter/RM65OntologyParameters/
* \- Official online programming guide https://develop.realman-robotics.com/en/robot/teachingPendant/onlineCode/

**RM65-B-V Vision Configuration**

The V1.5 content covers installation controller access teaching motion IO programming and the functions shared by the vision-arm configuration. Camera calibration visual recognition and application deployment require the applicable vision package and its own setup procedure. Confirm the complete arm model and controller version before following a vision example. Current official release notes explicitly list RM65-B-V among the supported vision-arm models.

* [Introduction and Product Composition](realman-robot-web-teaching-pendant-user-manual-v1.5.md#introduction-and-product-composition)
* [Safety, Handling, Maintenance and Quality Assurance](realman-robot-web-teaching-pendant-user-manual-v1.5.md#safety-handling-maintenance-and-quality-assurance)
* [Robot Hardware and Interfaces](realman-robot-web-teaching-pendant-user-manual-v1.5.md#robot-hardware-and-interfaces)
* [Installation, Wiring and First Startup](realman-robot-web-teaching-pendant-user-manual-v1.5.md#installation-wiring-and-first-startup)
* [Teaching and Jogging the Robot](realman-robot-web-teaching-pendant-user-manual-v1.5.md#teaching-and-jogging-the-robot)
* [Creating and Running Programs](realman-robot-web-teaching-pendant-user-manual-v1.5.md#creating-and-running-programs)
* [Robot Configuration and Calibration](realman-robot-web-teaching-pendant-user-manual-v1.5.md#robot-configuration-and-calibration)
* [System Information, Logs and Expansion](realman-robot-web-teaching-pendant-user-manual-v1.5.md#system-information-logs-and-expansion)
* [Programming Examples and System Update](realman-robot-web-teaching-pendant-user-manual-v1.5.md#programming-examples-and-system-update)
* [MODBUS and External Interfaces](realman-robot-web-teaching-pendant-user-manual-v1.5.md#modbus-and-external-interfaces)
* [Technical Specifications](realman-robot-web-teaching-pendant-user-manual-v1.5.md#technical-specifications)
* [Optional Functions and Additional Materials](realman-robot-web-teaching-pendant-user-manual-v1.5.md#optional-functions-and-additional-materials)
* [Quick Troubleshooting Index](realman-robot-web-teaching-pendant-user-manual-v1.5.md#quick-troubleshooting-index)

### Introduction and Product Composition

![Official RealMan figure](<../../.gitbook/assets/Unknown image (50)>)

Version Record No.

Date Comment V1.0 2/08/2023 Draft V1.1 4/18/2023 Update on web teaching pendant V1.2 7/21/2023 Update on default programming, controller digital IO multiplexing, standby time settings, and teaching pendant interface, etc V1.3 8/26/2023

Update on IO wiring instructions IO multiplexing function, coordinate system calibration diagram, optional accessories

Modbus-TCP, etc V1.4 10/14/2023 Update on DC power supply instructions, multi-coil encoder, singularity area diagram, online programming file saving, etc v1.5 11/01/2023 Script programming, communication configuration

IO mode added modbusRTU, modbusTCP, and electronic fence.

**Foreword**

We appreciate your purchasing and using our ultra-lightweight robotic arms. There are two versions of the robotic arm: the basic version and the integrated six-axis force version. The usage process can all refer to this manual.

RealMan Intelligent Technology (Beijing) Co., Ltd. has launched 4 series of 8 models, plus a visual version of the robotic arm. The robot adopts joint modular design, integrated controller at the bottom, no need for control cabinet.

Users can build their own robot control platform based on the API provided by our collaborative robot platform.

Furthermore, our company's entire series of collaborative robots has special programmable operating interfaces through which users may view the robot's real-time running state and control settings.

The WEB teaching pendant allows for online simulation of robots but not offline simulation.

![Official RealMan figure](<../../.gitbook/assets/Unknown image (51)>)

**Product composition**

The product composition of a complete set of collaborative robots is as follows:

**Product composition**

| Name                               | Quantity |
| ---------------------------------- | -------- |
| Robotbody                          | 1        |
| Power cable                        | 1        |
| 6-core tool endIO cable            | 1        |
| 16-core IO cable                   | 1        |
| Network cable                      | 1        |
| M6\*20fixing screw                 | 4        |
| Tablet teaching pendant (optional) | 1        |

Schematic diagram of the robot overall composition

![Official RealMan figure](<../../.gitbook/assets/Unknown image (52)>)
