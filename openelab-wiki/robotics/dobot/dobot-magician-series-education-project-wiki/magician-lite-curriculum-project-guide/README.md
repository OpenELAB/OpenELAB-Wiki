---
description: >-
  Model-specific DOBOT curriculum entry and connected educational project
  navigation.
---

# Magician Lite — Educational Curriculum and Project Guide

{% hint style="info" %}
[**View DOBOT Magician Lite Educational Robot Arm on OpenELAB**](https://openelab.io/products/dobot-magician-lite-education-robot)

**Model:** Magician Lite · **SKU:** `DOBOT-1100000080` · **Motion:** four-axis educational arm · **Accessories:** confirm ordered pen/suction/soft gripper/Magic Box/sensors separately
{% endhint %}

[Magician Series curriculum index](../) · [Existing Magician Lite User Guide](../../dobot-magician-lite-user-guide.md)

### Product overview

Magician Lite introduces small robotic arms through **Teach & Playback**, **DobotBlock/Blockly**, optional Magic Box sensors and cross-disciplinary AI lessons. This curriculum follows DOBOT-linked **V1.1 Dobot Lite Curriculum 2024**, _Graphical Programming & Robots (Scratch)_ and the _AI at Your Fingertips_ **AI Campus / AI Farm / AI Mall** experiment books. The separate official user guide remains the hardware authority.

### Applications

* Safe initial USB/DobotLab connection and motion concepts.
* Robot-arm coordinates, movement, loops, picks and pallet loading.
* Optional Bluetooth/Magic Box handshaking, sensors, color sorting and peripheral work cells.
* Scratch/Blockly stage projects and optional campus/farm/mall AI classroom simulations.

### Specifications

| Parameter            | Value / condition                                                                                                       |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Robot                | 4 axes; maximum payload **250 g**; reach **340 mm**                                                                     |
| Listed repeatability | ±0.2 mm                                                                                                                 |
| Power                | **Original 12 VDC, 5 A** adapter; input mains 100–240 VAC                                                               |
| Software             | DOBOT **DobotLab**, Teaching & Playback, DobotBlock; optional Magic Box supports MicroPython                            |
| Communication        | USB virtual serial / serial (robot)                                                                                     |
| Optional accessories | Pen holder, suction tool, soft gripper, sensor/Magic Box, AI camera, mini conveyor, rail; availability depends on order |

Product parameters: [OpenELAB Lite listing](https://openelab.io/products/dobot-magician-lite-education-robot) and [DOBOT Lite product information](https://www.dobot-robots.com/products/education/magician-lite.html?lang=en). Kit scope must be verified against delivered package.

### Hardware and connections

1. Remove power before attaching a pen, end effector or cable. Confirm keyed tool connector, orientation and installed tool as described in the **Lite** manual; do not copy the original Magician pen mounting method.
2. Connect the original 12 V/5 A supply and USB cable to the host. Keep the workspace clear and the robot stable on a non-slip surface.
3. Before homing, confirm no obstruction, loose object, or hand is in reach.
4. Do not wire Magic Box I/O or camera connectors from diagrams for the **original Magician**; consult Lite/Magic Box pinout and signal-level documentation.
5. The workbook uses a **non-spring-loaded pen** for Lite; apply very light paper pressure and place a compliant backing under the sheet when approved by an instructor.

### Software and development resources

* [Lite V1.1 2024 workbook](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view): four chapters plus resources/printable field diagrams.
* [Graphical Programming & Robots (Scratch)](https://drive.google.com/file/d/1AqvE_sonCGFOEYrdeKObKkBp2AimPu-Q/view): smart supermarket, sprite/robot motion, data, loops, branches and messages.
* [AI Farm](https://drive.google.com/file/d/17Tare_uJk6MZOTeyywWWV4LaXtk7198P/view), [AI Campus](https://drive.google.com/file/d/1ubqJ_JngHsy_4YPJVta871hhovIjOjnD/view), [AI Mall](https://drive.google.com/file/d/12dYdW64qOUzRTFheJoz4wC8MhThDEBMZ/view): accessory-heavy AI classroom projects.
* [Published Lite User Guide](../../dobot-magician-lite-user-guide.md) for current safe setup, interface selection and calibration.

### Getting started

#### First working result — connection and coordinate inspection

1. Check the Lite hardware label, supply, installed USB serial device and selected DobotLab version.
2. With the power supply disconnected, fit the intended pen bracket only if included and correct for **Lite**. Position a soft-mat work surface; remove loose items.
3. Connect the original supply and USB, power on the robot, open DobotLab → **Teaching & Playback Lab** → **Connect**, and confirm the detected COM connection. Do not send motion while searching for the device.
4. Open **Arm Control**, check the displayed **X/Y/Z/R** values. With the instructor and emergency-stop arrangement present, perform the manual-prescribed **Home** only if the entire work envelope is clear.
5. Move a small distance through the documented **joint and Cartesian jog controls** at instructor-approved slow speed, note coordinate changes, and return safely.

**Expected result:** connected status and plausible changing coordinates. Record the actual COM, UI version, coordinate units and tool. A first lesson is complete **without running an entire drawing path**.

**If no device appears:** verify correct Lite selection, original supply, USB cable, installed driver, serial port and hardware condition before any firmware changes.

### Magician Lite curriculum navigation

The first four tutorials follow the **V1.1 2024** workbook. The Scratch/AI volumes are independent, optional instructional tracks and may require additional Magic Box, camera or sensor hardware.

* [1. Robot Movement and Pallets](magician-lite-chapter-1-robot-movement.md)
* [2. Robot/Magic Box Communication](magician-lite-chapter-2-communication.md)
* [3. I/O, Sensors and Color Sorting](magician-lite-chapter-3-sensors.md)
* [4. Conveyor, Rail and Work Cells](magician-lite-chapter-4-peripherals.md)
* [Scratch/Blockly — Smart Supermarket](magician-lite-scratch-smart-supermarket.md)
* [AI Campus](magician-lite-ai-campus-projects.md)
* [AI Farm](magician-lite-ai-farm-projects.md)
* [AI Mall](magician-lite-ai-mall-projects.md)

**Not included by default:** a workbook experiment's AI camera, sensor board, conveyor, LCD, water pump or Magic Box unless the specific order/bundle contains it.

### Troubleshooting and FAQs

**The robot cannot reach an example from the original Magician book:** Lite reach/geometry are different; use the Lite field template and teach new points.

**Why is the pen icon represented by suction in an older classroom UI?** The workbook notes that some versions lack a pen tool selection; follow the exact software version and protect the end effector. Do not assume the icon sets correct calibration.

**Does the listed Lite arm include an AI camera or sensor kit?** Those are optional unless the order explicitly includes them. The AI chapters cannot be run on the bare arm alone.

### Downloads and technical documents

| Resource                                                                                                   | Use                                    |
| ---------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| [Magician Lite user guide](../../dobot-magician-lite-user-guide.md)                                        | USB, pinouts, safety, operating steps  |
| [Lite V1.1 curriculum](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view)             | Course lessons and printable fields    |
| [Scratch/Blockly curriculum](https://drive.google.com/file/d/1AqvE_sonCGFOEYrdeKObKkBp2AimPu-Q/view)       | Story-based programming projects       |
| [AI Campus/Farm/Mall collection](https://drive.google.com/drive/folders/1HduKhJvc59GwWua4ATOMgG59Dp18UcIo) | Optional AI/sensor integrated projects |

### References and validation

* _Dobot Lite Curriculum V1.1 (2024)_, uploaded curriculum folder, retrieved 2026-11-21.
* _Graphical Programming & Robots (Scratch)_ and _AI at Your Fingertips_ experiment books, retrieved 2026-11-21.
* OpenELAB product description, DOBOT official Lite specification and [existing Lite guide](../../dobot-magician-lite-user-guide.md), reviewed 2026-11-21.

**Documentation reviewed:** yes. **Software execution:** not run. **Hardware tested:** not run. Optional sensors/AI tutorials remain conditional on confirmed exact kit, drivers, pinouts and safety checks.
