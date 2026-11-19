---
description: >-
  Exact-model specifications, wiring, first CAN status read, troubleshooting and
  official technical resources.
---

# MyActuator EPS-RH-25-100-E Development Guide

{% hint style="info" %}
[**View MyActuator EPS-RH-25-100-E on OpenELAB**](https://openelab.io/products/myactuator-epsrh25-100e-servo-actuator)

**Model:** EPS-RH-25-100-E · **SKU:** `MyActuator-EPS-RH-25-100-E-N-D` (no brake), `MyActuator-EPS-RH-25-100-E-B-D` (brake) · **Revision / option:** 100:1 dual-encoder N-D (no brake) and B-D (brake) versions
{% endhint %}

## Product overview

The RH-25 combines a harmonic reduction stage, motor, driver and dual absolute encoders. This page covers both OpenELAB 100:1 variants: N-D without a brake and B-D with a holding brake. The optional manufacturer 50:1 version is not the product configured here.

![MyActuator EPS-RH-25-100-E, product photograph from OpenELAB](../../.gitbook/assets/myactuator-rh25.jpg)

Product photograph: OpenELAB product listing. Check the ordered option for package contents; accessories shown in manufacturer packaging examples are not a guarantee that the selected motor-only variant includes them.

## Applications

The hollow axis and low backlash make it a candidate for compact precision robot joints and rotary mechanisms. Account for the brake option's extra length/mass and the actual duty cycle when designing the assembly.

## Specifications

| Parameter                           | Value / scope                                         |
| ----------------------------------- | ----------------------------------------------------- |
| Reduction                           | 100:1 harmonic reduction; not the optional 50:1 model |
| Nominal supply / range              | 48 V DC / 20–55 V                                     |
| Rated / peak output torque          | 108 / 157 N·m                                         |
| Rated / no-load speed               | 25 / 30 rpm                                           |
| Rated output power                  | 282 W                                                 |
| Rated / peak phase current          | 10.6 / 14.1 Arms                                      |
| Input / output encoder              | 17-bit / 17-bit absolute                              |
| Backlash / repeat position accuracy | ≤40 arcsec / <0.01°                                   |
| Diameter / through-hole             | 110 / 22 mm                                           |
| N-D: length / mass                  | 89.5 mm / 2.42 kg; no brake                           |
| B-D: length / mass                  | 105.2 mm / 2.74 kg; holding brake                     |
| Communication                       | CAN and EtherCAT                                      |

Source: [RH-25 product manual 260805 and N/B drawings](https://www.myactuator.com/_files/archives/cab28a_bc732701dadf4512a0d917ecaab12747.zip). Rated and peak figures are distinct operating points, not simultaneous maxima.

The 108 N·m rated-torque test is at rated speed, 24°C ambient, no additional heat-dissipation method and thermal balance at a 60°C temperature rise. The B-D brake is a static holding brake supplied from the module's DC connector, not a routine high-speed dynamic brake. The standard model is not waterproof; an optional IP54 configuration must be confirmed when ordering.

## Hardware and connections

Required equipment: a secured unloaded actuator, a 48 V DC nominal (20–55 V operating range) supply, suitable power wiring and isolation, one CAN interface with its supported host software, and the model-specific mating cables. Phase current in a motor table is not a substitute for calculating the DC supply requirement.

Use the RH-25 interface diagram in the [model archive](https://www.myactuator.com/_files/archives/cab28a_bc732701dadf4512a0d917ecaab12747.zip), including the connector-view orientation. Connect the external supply to VCC/DC+ and GND/DC−, CAN\_H to CAN\_H and CAN\_L to CAN\_L. Keep BAT+/BAT− and RES+/RES− separate from motor power and communications. The communication, battery and resistor cable appearances are not a wiring specification.

For the B-D variant, support the load before brake release. Its brake is powered by the module DC connection; follow the RH manual rather than adding an external brake supply. Use the correct N-D or B-D drawing for screw engagement and axial clearance.

For a CAN bench connection, use a linear bus with 120 Ω termination at each physical end and a common reference as specified by the manufacturer. Count any built-in USB-CAN termination; do not add a resistor at every motor. With power off, two 120 Ω end resistors in parallel measure about 60 Ω between CAN\_H and CAN\_L. This resistance check is a wiring diagnostic, not proof of communication.

## Software and development resources

The [manufacturer setup-software page](https://www.myactuator.com/downloads-setupsoftware) is the source for the setup utility and its supported model list. The [RH manual bundle](https://www.myactuator.com/_files/archives/cab28a_be98b58973d34f7aaa50bdf3f2aa12ed.zip) includes CAN protocol V4.4-260520 and EtherCAT protocol V2.0-260425. Match the full model and firmware generation before changing parameters.

A compatible raw CAN frame utility is sufficient for the first result below. Install the driver that matches the actual USB-CAN hardware and host operating system; this guide does not assume that the adapter exposes Linux SocketCAN or a serial COM protocol. The manufacturer's [SDK downloads](https://www.myactuator.com/downloads-sdk) provide optional integration starting points. Their exact OS, dependency and model coverage must be checked in the selected release before building; no SDK build is required for this status-read procedure. Preserve calibration and parameter backups before any firmware change.

For EtherCAT integration, use the [official ESI downloads](https://www.myactuator.com/downloads-ethercatesi) and the protocol's object dictionary for the fitted firmware. Confirm slave identity and process-data mapping before enabling operation.

## Getting started

### First working result: read status over CAN

1. Record the label, controller/firmware revision and saved motor ID. Connect only one unloaded motor; secure it and leave motion disabled.
2. With power off, connect power and CAN as described above. Verify polarity, common reference and the two end terminations. Set the supply within the documented range; use nominal voltage for rated-condition work.
3. Install the interface's matching driver, open the CAN utility and select its channel. For the cited protocol, select **1 Mbit/s, standard 11-bit data frames, DLC 8**. If this motor has a previously changed bitrate, use that saved setting rather than writing a new one blindly.
4. Send one read-status command to arbitration ID **0x140 + motor ID**. For a motor confirmed as ID 1, enter transmit ID **0x141** and payload **9A 00 00 00 00 00 00 00**. ID 1 is an example, not a discovery result.
5. Inspect the reply at **0x240 + motor ID** (**0x241** for ID 1). The command byte should be 0x9A. Decode temperature, bus voltage and fault flags using the **Read Motor Status 1 and Error Flag** table in the [cited protocol package](https://www.myactuator.com/_files/archives/cab28a_be98b58973d34f7aaa50bdf3f2aa12ed.zip); byte layouts can differ across firmware generations.
6. Repeat the read and record the actual voltage, temperature and fault state. Resolve any fault before a separate motion test. Only after confirming angle units, direction, current limits and stop behavior should a bounded, low-speed, unloaded movement be attempted.

**Expected result:** repeatable status replies from the intended ID, with plausible bus voltage/temperature and fault information that can be decoded for the recorded firmware. A status reply establishes communication, not motion or load qualification.

**If this check fails:** verify supply at the actuator, adapter enumeration, CAN\_H/CAN\_L and reference wiring, termination, saved bitrate and ID, then protocol/firmware pairing. Do not repeatedly send enable or motion commands to diagnose a missing reply.

## Troubleshooting and FAQs

**The replacement no longer fits the housing**

Check N-D versus B-D. The brake option increases length from 89.5 to 105.2 mm and mass from 2.42 to 2.74 kg.

**The B-D shaft remains held**

Read faults and brake-command status first. Follow the RH manual's release sequence with the load supported; do not force the shaft or apply an improvised external brake voltage.

**Can the battery and resistor leads be interchanged?**

No. BAT+/BAT− are memory-battery terminals and RES+/RES− are bleeder-resistor terminals. Their similar cable format does not make the circuits interchangeable.

**EtherCAT cable is connected but the slave is absent**

Check motor power, IN/OUT direction, cable pair mapping and the master's active interface. Then verify ESI/product identity and inspect master diagnostics before changing drive parameters.

## Downloads and technical documents

| Resource                                       | Purpose and revision                                                                                       | Link                                                                                                   |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Exact-model parameters and mechanical drawings | RH-25 product manual 260805 and N/B drawings; use supplied drawings/CAD rather than dimensions from images | [Official ZIP](https://www.myactuator.com/_files/archives/cab28a_bc732701dadf4512a0d917ecaab12747.zip) |
| Manuals and protocols                          | RH user manual V1.4, CAN V4.4-260520, EtherCAT V2.0-260425                                                 | [Official ZIP](https://www.myactuator.com/_files/archives/cab28a_be98b58973d34f7aaa50bdf3f2aa12ed.zip) |
| Model document center                          | Current revision listings and CAD packages                                                                 | [Manufacturer downloads](https://www.myactuator.com/downloads-rhseries)                                |
| Host setup utility                             | Select model/driver generation before installation                                                         | [Setup software](https://www.myactuator.com/downloads-setupsoftware)                                   |
| Optional development SDK                       | Check release README, dependencies and licensing before use                                                | [SDK downloads](https://www.myactuator.com/downloads-sdk)                                              |
| EtherCAT ESI                                   | Match actuator firmware/product identity                                                                   | [ESI downloads](https://www.myactuator.com/downloads-ethercatesi)                                      |

## References and validation

The specifications and procedure use the manufacturer packages linked above; the [OpenELAB listing](https://openelab.io/products/myactuator-epsrh25-100e-servo-actuator) identifies the sold model and options. Reviewed 19 November 2026. Manufacturer PDFs, relevant tables and interface documentation were inspected. The CAN procedure is a documentation-based first check; software compilation, adapter-driver installation and physical motor tests were **not run**. Keep the actual firmware, host environment, ID and measured results with the device.

[All MyActuator product guides](./)
