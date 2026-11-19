---
description: >-
  X8-120 specifications, CAN and EtherCAT setup, commissioning, troubleshooting
  and official technical resources.
---

# MyActuator RMD-X8-P20-120-E Development Guide

Hardware specifications, CAN and EtherCAT setup, commissioning checkpoints, and official downloads for the X8-120 actuator.

{% hint style="info" %}
[**View RMD-X8-P20-120-E on OpenELAB**](https://openelab.io/products/myactuator-rmd-x8-p20-actuator)

**Covered model:** MYACTUATOR RMD-X8-P20-120-E · **OpenELAB SKU:** `MyActuator-RMD-X8-P20-120-E`. The shortened spelling “RMD-X8-P20-120E” refers here to the manufacturer's full `RMD-X8-P20-120-E` designation.
{% endhint %}

![MYACTUATOR X8-120 integrated planetary actuator](../../.gitbook/assets/myactuator-x8-120.png)

_Manufacturer image: MYACTUATOR._ [_Original product page_](https://www.myactuator.com/x8-120details)_._

[MyActuator documentation](./) · [Shared X6/X8 engineering overview](myactuator-rmd-x6-x8-p20-development-guide.md)

## Product and development scope

The X8-120 combines a motor, planetary gearbox, drive electronics and dual absolute encoders in one robotic joint actuator. The `-E` configuration supports **EtherCAT and CAN BUS** and is listed **without a brake**.

This guide uses the manufacturer's **X8-120 Motor Parameter 260903.pdf**, supplied in its **260920 parameter archive**, together with the current official V4 software and documentation listings. Match the received actuator's label, driver generation and firmware before using any configuration. Other X8 ratios, the X8-150, older single-encoder models and CAN-only variants require their own documentation.

## Technical specifications

| Parameter                    | X8-120 reference value                                |
| ---------------------------- | ----------------------------------------------------- |
| Full model                   | RMD-X8-P20-120-E                                      |
| Actual reduction ratio       | 19.612:1                                              |
| Nominal input voltage        | 48 V DC                                               |
| Operating voltage range      | 20–55 V DC                                            |
| Rated / peak output torque   | 43 / 120 Nm                                           |
| Rated / no-load output speed | 127 / 158 rpm                                         |
| Rated output power           | 574 W                                                 |
| Rated / peak phase current   | 17.6 / 43.8 A RMS                                     |
| No-load input current        | 1.6 A                                                 |
| Encoder feedback             | Absolute dual encoder: 17-bit input and 17-bit output |
| Communication                | EtherCAT and CAN BUS                                  |
| Backlash                     | ≤15 arcmin                                            |
| Backdrive torque             | 1.5 Nm                                                |
| Output bearing               | Crossed roller bearing                                |
| Mass                         | 1.40 kg                                               |
| Brake                        | None in this reference configuration                  |

Source: [official X8-120 parameter and CAD archive](https://www.myactuator.com/_files/archives/cab28a_2f52d96407934978a1b0e6c98b33a928.zip).

**P20 is the model-family designation; use 19.612 when a calculation requires the documented actual reduction.** First determine whether the selected feedback or command already uses output-shaft units, so the ratio is not applied twice.

**120 Nm is peak torque, not a continuous holding rating.** Phase-current RMS values are not DC supply-current ratings. Size the supply and thermal duty from the actual application rather than treating these columns as interchangeable.

The parameter sheet specifies a **55 V maximum operating voltage**, recommends an external capacitor to stabilize battery supply voltage, and states that operation above nominal voltage must not exceed rated speed. Include regenerated energy during deceleration when evaluating the DC bus; a capacitor alone is not a complete regeneration design.

## Mechanical and electrical preparation

The official archive contains:

* `X8-120 Motor Parameter 260903.pdf`
* `RMD-X8-P20-120 2D -A0.pdf`
* A STEP outline model dated 260920

Use the dimensioned drawing for mounting-hole positions, fastener engagement and through-hole clearance. Support gravity-loaded mechanisms independently because the listed actuator has no brake.

Prepare a rigid fixture, a suitably protected DC supply, an accessible means of isolating drive power, and the correct manufacturer cables or verified harness. Check connector orientation, polarity and communication pin assignments against the manual for the received driver. Connect and inspect wiring with power removed.

## Choose a communication path

| Path     | Prepare                                                                                       | First checkpoint                                                                 |
| -------- | --------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| CAN BUS  | A compatible CAN interface and its driver; matching bus rate, node ID, wiring and termination | Repeatable status replies from the intended node, with motion disabled           |
| EtherCAT | An EtherCAT master, suitable network interface, and firmware-matched ESI XML                  | Correct device identity and stable communication before enabling drive operation |

The [setup software page](https://www.myactuator.com/downloads-setupsoftware) lists **MYACTUATOR Setup Software V4.0\_250704** for planetary V4 models including X8-120. Follow its installation and interface requirements; preserve the existing configuration before changing parameters.

The [X-series download center](https://www.myactuator.com/downloads-xseries) lists **CAN BUS Motor Motion Protocol V4.4-260520**, **EtherCAT control protocol V2.0-260425**, **User Manual for X Series Products V1.1-250516**, and **X Series-V4 product manual-261029**. Match applicability to the actual unit instead of assuming every V4 example works unchanged.

For EtherCAT, the [official ESI page](https://www.myactuator.com/downloads-ethercatesi) explicitly associates **MT-Device-260424.XML** with firmware **26042402** and also lists an older XML. Select by device/firmware compatibility, not simply by the newest filename. An EtherCAT port is not a general-purpose TCP/IP connection.

## First power-up and commissioning

1. **Record the hardware.** Note the full model, serial number, driver revision and firmware. Secure one unloaded actuator and keep the output clear.
2. **Verify the power path.** Check polarity and the applicable connector drawing. Set conservative limits appropriate to the test and ensure drive power can be isolated.
3. **Configure one interface.** For CAN, check bus rate, termination and unique node ID. For EtherCAT, install the matching ESI and identify the device through the master.
4. **Read before moving.** With drive motion disabled, read identity and available voltage, temperature, position and fault status using the revision-specific tool or protocol.
5. **Save a baseline.** Export parameters where supported and record IDs, offsets, limits and software versions. Do not overwrite encoder calibration or load another actuator's parameter file.
6. **Perform a controlled motion check.** Follow the manufacturer's low-speed, small-displacement procedure with the shaft unloaded. Verify direction, units, feedback and stop behavior before increasing load.
7. **Integrate gradually.** Establish application-specific position, current/torque and thermal limits. Check the DC bus during deceleration and support any gravity-loaded link during shutdown.

**Pass criterion:** stable and plausible telemetry, followed by a repeatable small motion and a verified stop without faults. This page deliberately leaves pinouts and motion payloads to the exact driver documentation rather than presenting a packet that may target another revision.

## Troubleshooting and FAQ

| Symptom or question                             | Checks and next step                                                                                                                  |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Powered, but no CAN reply                       | Verify pinout, bus rate, node ID, termination and adapter configuration. Test a single node first.                                    |
| EtherCAT slave is detected but will not operate | Compare device identity, firmware and ESI; inspect the master's state and diagnostic messages before enabling motion.                 |
| Position or velocity scaling looks wrong        | Check units, motor-side versus output-side feedback, zero offset and whether reduction is already included.                           |
| DC bus rises during deceleration                | Review regeneration handling and supply absorption capability; keep the complete operating cycle within the documented voltage range. |
| High temperature while holding still            | Review holding current, torque demand, cooling and duty cycle. Peak torque is not a continuous thermal rating.                        |
| Mechanism moves when power is removed           | This configuration has no brake; provide a designed support or holding arrangement.                                                   |
| Can X6 or X12 parameters be reused?             | Do not copy model-specific gains, limits, calibration or scaling without manufacturer validation.                                     |
| Can I follow an older X8 guide?                 | Compare the complete model and document revision. Similar names do not establish electrical, mechanical or firmware compatibility.    |

## Official technical resources

| Resource                                                                                                                             | Purpose                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------- |
| [X8-120 product page](https://www.myactuator.com/x8-120details)                                                                      | Full model and supported interfaces                     |
| [X8-120 parameters, 2D PDF and STEP archive](https://www.myactuator.com/_files/archives/cab28a_2f52d96407934978a1b0e6c98b33a928.zip) | Specifications and mechanical integration               |
| [V4 protocol and manual archive, 261029](https://www.myactuator.com/_files/archives/cab28a_a5b8b24b40ac4f6d87bae373b0de459a.zip)     | Installation, CAN and EtherCAT references               |
| [X-series download center](https://www.myactuator.com/downloads-xseries)                                                             | Check document revisions and model applicability        |
| [Setup software](https://www.myactuator.com/downloads-setupsoftware)                                                                 | Manufacturer configuration software                     |
| [EtherCAT ESI and TwinCAT resources](https://www.myactuator.com/downloads-ethercatesi)                                               | Firmware-matched device description and setup resources |

**Reviewed:** 19 November 2026. **Validation:** the official X8 parameter PDF was extracted and visually checked; manufacturer product, software and download listings were reviewed. No hardware commissioning or motion-code execution was performed for this guide. Record hardware, firmware, software versions and actual results when reproducing the procedure.
