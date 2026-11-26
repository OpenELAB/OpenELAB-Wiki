---
description: >-
  Preserved WEB Teaching Pendant V1.5 introduction and figures, with links to
  separate RM65 and ECO65 operating references. Match the delivered model,
  controller and manual revision.
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

Use [RM65](realman-rm65-series-user-manual-v1.2.0.md) or [ECO65](realman-eco65-series-user-manual-v1.2.0.md) for product-specific setup and separate supplied manual revisions; use [shared commissioning/SDK guide](realman-arm-commissioning-and-sdk.md) before running development examples. This V1.5 page retains the existing source material and figures; it is not a universal current-firmware screen reference. Motion, force control, calibration and program execution require the exact delivered controller manual. Reviewed 22 November 2026; software/hardware tests not run.

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

### Model and Version Applicability

This page preserves only the introduction, version record, product composition and figures from the RealMan Robot WEB Teaching Pendant User Manual V1.5 dated November 1, 2023. It does not reproduce the complete V1.5 operating manual. The model-specific references below are separate documents; match the delivered arm, controller and software version before using them.

Before using controller-specific or interface-specific instructions compare the installed controller and software versions with the official version correspondence. Later firmware may change screen layouts supported functions model adaptations and API compatibility.

* Current RealMan version correspondence and release notes https://develop.realman-robotics.com/en/robot/releaseNotes/releaseNotes/
* \- Official hardware preparation guide for RealMan robot series https://develop.realman-robotics.com/en/robot/quickUseManual/index.html
* \- Official RM65 series parameters and model identification https://develop.realman-robotics.com/en/robot/robotParameter/RM65OntologyParameters/
* \- Official online programming guide https://develop.realman-robotics.com/en/robot/teachingPendant/onlineCode/

**RM65-B-V Vision Configuration**

The preserved V1.5 introduction lists the vision-arm configuration; detailed installation, teaching and programming procedures are not present on this page. Camera calibration visual recognition and application deployment require the applicable vision package and its own setup procedure. Confirm the complete arm model and controller version before following a vision example. Current official release notes explicitly list RM65-B-V among the supported vision-arm models.

* [Introduction and Product Composition](realman-robot-web-teaching-pendant-user-manual-v1.5.md#introduction-and-product-composition)

### Current model-specific operating references <a href="#current-model-specific-operating-references" id="current-model-specific-operating-references"></a>

The references below link to separate RM65/RM75 (58 PDF pages) and ECO (56 PDF pages) hardware manuals, and to the RM65/ECO65 model guides titled V1.2.0. They are not chapters of the WEB Teaching Pendant V1.5 manual. Match the delivered arm, controller and software version; detailed V1.5 programming, calibration, log-viewer and firmware-update procedures are not reproduced here.

| Topic                                                | RM65 reference                                                                                                                                                                            | ECO65 reference                                                                                                                                                               |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Safety, quality assurance, handling and maintenance  | [Safety and quality assurance, pp. 1–10](realman-source-library/complete-rm65-rm75-manual.md); [Handling and maintenance, pp. 56–58](realman-source-library/complete-rm65-rm75-manual.md) | [Safety and quality assurance, pp. 1–10](realman-source-library/complete-eco-manual.md); [Handling and maintenance, pp. 54–56](realman-source-library/complete-eco-manual.md) |
| Controller and tool hardware interfaces              | [Hardware interfaces, pp. 21–29](realman-source-library/complete-rm65-rm75-manual.md)                                                                                                     | [Hardware interfaces, pp. 21–29](realman-source-library/complete-eco-manual.md)                                                                                               |
| Mounting, wiring and power-on                        | [Installation and power-on, pp. 12–15](realman-source-library/complete-rm65-rm75-manual.md)                                                                                               | [Installation and power-on, pp. 12–15](realman-source-library/complete-eco-manual.md)                                                                                         |
| Teach-pendant connection and drag teaching           | [Connection, pp. 16–19](realman-source-library/complete-rm65-rm75-manual.md); [Drag teaching, pp. 20–21](realman-source-library/complete-rm65-rm75-manual.md)                             | [Connection, pp. 16–19](realman-source-library/complete-eco-manual.md); [Drag teaching, pp. 20–21](realman-source-library/complete-eco-manual.md)                             |
| Programming and SDK resource selection               | [Software and development resources](realman-rm65-series-user-manual-v1.2.0.md)                                                                                                           | [Software and development resources](realman-eco65-series-user-manual-v1.2.0.md)                                                                                              |
| Electrical and tool configuration context            | [Installation and electrical integration](realman-rm65-series-user-manual-v1.2.0.md)                                                                                                      | [Installation and electrical integration](realman-eco65-series-user-manual-v1.2.0.md)                                                                                         |
| Startup and controller-status checks                 | [Getting started](realman-rm65-series-user-manual-v1.2.0.md)                                                                                                                              | [Getting started](realman-eco65-series-user-manual-v1.2.0.md)                                                                                                                 |
| Manual downloads and controller-generation selection | [Downloads and technical documents](realman-rm65-series-user-manual-v1.2.0.md)                                                                                                            | [Downloads and technical documents](realman-eco65-series-user-manual-v1.2.0.md)                                                                                               |
| RS485 and Modbus RTU interface reference             | [Communication interface, pp. 28–29](realman-source-library/complete-rm65-rm75-manual.md)                                                                                                 | [Communication interface, pp. 28–29](realman-source-library/complete-eco-manual.md)                                                                                           |
| Exact-model specifications and parameters            | [RM65 parameters, from p. 29](realman-source-library/complete-rm65-rm75-manual.md)                                                                                                        | [ECO65 parameters, from p. 40](realman-source-library/complete-eco-manual.md)                                                                                                 |
| Additional developer resources                       | [Additional Information, p. 58](realman-source-library/complete-rm65-rm75-manual.md)                                                                                                      | [Additional Information, p. 56](realman-source-library/complete-eco-manual.md)                                                                                                |
| Operating and communication FAQs                     | [FAQs, pp. 53–56](realman-source-library/complete-rm65-rm75-manual.md)                                                                                                                    | [FAQs, pp. 51–54](realman-source-library/complete-eco-manual.md)                                                                                                              |

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
