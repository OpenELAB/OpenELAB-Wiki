---
description: >-
  Model-specific DOBOT curriculum entry and connected educational project
  navigation.
---

# Magician — Educational Curriculum and Project Guide

{% hint style="info" %}
[**View DOBOT Magician Desktop Robot Arm for Education on OpenELAB**](https://openelab.io/products/dobot-magician-education-robot-arm)

**Model:** DOBOT Magician · **Basic SKU:** `DOBOT-1100000015` · **Edition:** Basic Plan / Educational Plan (verify ordered variant/SKU) · **Robot:** four-axis desktop arm
{% endhint %}

[Magician Series index](../) · [Existing DOBOT Magician User Guide](../../dobot-magician-user-guide.md)

### Product overview

This is the engineering companion for **V3.2 Dobot Magician Curriculum (2024)**, an extensive education workbook organized into robot movement, robot communication, sensors, peripheral scenarios and printable resources. It uses **Teaching & Playback (T\&P)** and **DobotBlock** exercises in DobotLab, with selected peripheral/sensor modules requiring separately configured hardware. Related PPT lessons cover drawing, 3D printing, robotic arm experience, joystick control, stamping, piano playing and a final competition; those are separate scenarios rather than verified ready-made APIs.

### Applications

* Robot teaching, joint versus linear movement, repeatability, drawing and safe pick-and-place.
* Palletization, multi-robot and microcontroller handshaking.
* Digital inputs, Magic Box sensor exercises, color sensing and conveyor sorting.
* Work-cell design with conveyor, sliding rail, stack light and optional AI camera.

### Specifications

| Parameter        | Value / condition                                                              |
| ---------------- | ------------------------------------------------------------------------------ |
| Robot            | Four axes, 500 g maximum payload, 320 mm maximum reach                         |
| Repeatability    | ±0.2 mm                                                                        |
| Power            | Original **12 VDC, 7 A** robot adapter; mains input 100–240 VAC                |
| Communication    | USB and model-specific extension interfaces                                    |
| Software         | DobotLab/DobotStudio, Teaching & Playback, DobotBlockly                        |
| Basic Plan       | Magician arm, vacuum pump, gripper, writing/drawing kit, 3D printing kit       |
| Educational Plan | Basic contents **plus** laser engraving, Wi-Fi, joystick and Bluetooth modules |

Specifications and packing comparison: [OpenELAB Magician listing](https://openelab.io/products/dobot-magician-education-robot-arm).

### Hardware and connections

1. Confirm the **actual Magician edition** and delivered end effector before selecting a workbook activity. Do not assume Educational Plan accessories on Basic Plan.
2. Power off before connecting power/USB, changing end tools or attaching the sensor kit; use only original Magician 12 V/7 A supply, not Lite's 5 A unit.
3. Clamp/secure the arm and keep the complete work envelope clear. Home and verify robot motion under instructor supervision.
4. For drawing, install the matching spring-loaded pen accessory and use the printed field; do not teach pen contact coordinates from Lite or E6.
5. For two-robot communication, sensor kit, Magic Box, mini conveyor or sliding rail, obtain the exact peripheral manual and verify supply/logic voltages and wiring **before energizing**.
6. Laser/3D-printing activities require their manufacturer-specific ventilation, guarding, heat/optics safety and instructor supervision; they are not assumed to be beginner exercises.

### Software and development resources

* [V3.2 Magician curriculum PDF (2024)](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) — 4 chapters, field diagrams and glossary.
* [Magician PPT curriculum](https://drive.google.com/drive/folders/10SdZaCVoLyD2wvaeECOjXwgtNNYHOkm5) — 16 slide decks spanning introductory motion through production scenarios.
* [Existing Magician User Guide](../../dobot-magician-user-guide.md) — precise setup and supported software.
* [Conveyor User Guide](../../dobot-conveyor-belt-user-guide.md), [Sliding Rail Guide](../../dobot-sliding-rail-user-guide.md), [AI Vision Kit Guide](../../dobot-vision-kit-installation-guide.md) — optional peripherals.

### Getting started

#### First working result — teach a safe point list

1. Identify Magician, original 12 V/7 A adapter, USB cable, mounted tool and selected software revision.
2. With power disconnected, mount the compatible **pen accessory** or approved dummy pointer. Secure the robot and field sheet.
3. Power on, open **DobotLab → Teaching & Playback**, select **Connect** and confirm the robot's COM status.
4. Verify the reachable volume is clear; under supervision use the manual's **Home** function.
5. Open **Arm Control**, inspect current X/Y/Z and **joint** values. Using the taught-point mode, record **Home**, **Above A** and **Above B** at verified safe positions; do not yet lower onto paper or start an automatic loop.
6. Save the point list locally with date, device model and firmware/software version.

**Expected result:** working connection, three labeled taught points and a saved job file. A successful first result does **not** require movement near paper, a grasp or unattended playback.

### Magician V3.2 curriculum navigation

Four chapters follow the **Dobot Magician Curriculum V3.2 (2024)**, with the four main chapter topics retained and peripherals clearly separated from Basic Plan contents.

* [1. Robot Movement](magician-chapter-1-robot-movement.md)
* [2. Robot Communication](magician-chapter-2-communication.md)
* [3. Sensors and Color Sorting](magician-chapter-3-sensors.md)
* [4. Peripherals and Work-Cell Design](magician-chapter-4-workcell.md)

The workbook's chapter 5 **resources and printable help files** remain linked directly to the source PDF, including field diagrams, I/O and peripheral connection guides, glossary and assessment sheets.

### Troubleshooting and FAQs

**Does Magician Lite use the same coordinates as Magician?** No. Both have four axes, but their dimensions, accessories and calibration differ. Teach each model's points separately.

**Can Basic Plan complete the wireless or laser PPT lessons?** Not from the stated Basic packing list. They require Educational Plan modules or other separately sourced components and relevant safety controls.

**Why do I see different software names in curricula?** The 2024 workbook uses DobotLab/DobotBlock/T\&P, while some older firmware/user manual pages mention DobotStudio. Confirm the exact installed version, not a guessed command.

### Downloads and technical documents

| Resource                                                                                                | Scope                               |
| ------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| [V3.2 Magician 2024 curriculum](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) | Primary workbook                    |
| [PPT curriculum folder](https://drive.google.com/drive/folders/10SdZaCVoLyD2wvaeECOjXwgtNNYHOkm5)       | Lesson slides and projects          |
| [Magician manual](../../dobot-magician-user-guide.md)                                                   | Hardware and software               |
| [Accessory manuals](../../dobot-conveyor-belt-user-guide.md)                                            | Model-specific work-cell components |

### References and validation

* _Dobot Magician Curriculum V3.2 2024_, Chris & Jim CIM, provided Drive folder.
* OpenELAB verified Basic/Educational Plan product page and [existing Magician user guide](../../dobot-magician-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software/hardware:** not run or bench-tested. Peripheral-dependent procedures require exact wiring and edition verification.
