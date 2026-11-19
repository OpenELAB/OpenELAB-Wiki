---
description: >-
  DaDa:bit V2 is a micro:bit-based construction kit. Start with a micro:bit LED
  test before connecting motors or sensors.
---

# Hiwonder DaDa:bit V2 Guide

{% hint style="info" %}
[**View Hiwonder DaDa:bit V2 micro:bit Robotics & Electronic Block Kit on OpenELAB**](https://openelab.io/products/hiwonder-dada-bit-v2)

**SKU:** `Hiwonder-21070138`, `Hiwonder-21070141`, `Hiwonder-21070139`, `Hiwonder-21070142`, `Hiwonder-21070140`, `Hiwonder-21070143`

**Model / revision scope:** DaDa:bit V2. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![DaDa:bit V2 — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-118.png)

## Product overview

DaDa:bit V2 is a micro:bit-based construction kit. Start with a micro:bit LED test before connecting motors or sensors.

The startup procedure intentionally covers the micro:bit itself. Expansion-board powered builds require the kit-specific instructions.

### Models and purchasing options

| OpenELAB SKU        | Purchased option                 |
| ------------------- | -------------------------------- |
| `Hiwonder-21070138` | Starter Kit / without micro:bit  |
| `Hiwonder-21070141` | Starter Kit / with micro:bit     |
| `Hiwonder-21070139` | Standard Kit / without micro:bit |
| `Hiwonder-21070142` | Standard Kit / with micro:bit    |
| `Hiwonder-21070140` | Advanced Kit / without micro:bit |
| `Hiwonder-21070143` | Advanced Kit / with micro:bit    |

A separately named bracket, horn, chassis or rail is the listed accessory, not a complete robot or servo. A “without controller / Raspberry Pi / Jetson / micro:bit” option requires the matching controller separately. Check the selected option’s packing list before starting.

## Applications

Bench integration, education and development with the exact hardware listed above. Start with the first-result workflow before expanding the assembly or enabling autonomous operation.

## Specifications

| Parameter   | Value / scope                                                                 |
| ----------- | ----------------------------------------------------------------------------- |
| Controller  | micro:bit with model-specific expansion board; check included/excluded option |
| Programming | MakeCode for the micro:bit first test                                         |
| Battery     | Supplied 3.7 V cells; follow expansion-board charging documentation           |
| Actuators   | Two 360° motors; one 270° servo(s)                                            |
| Kit scope   | AI module and building-piece counts depend on selected option                 |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/dada-bit-v2) and [OpenELAB listing](https://openelab.io/products/hiwonder-dada-bit-v2). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

For this first test, disconnect the micro:bit from the expansion board and power only the micro:bit through its USB data connector. Do not connect a motor or battery pack directly to the micro:bit edge pins. Reinsert it into the model’s expansion board only with both units powered off and with the orientation shown by the exact kit manual.

## Software and development resources

Use [MakeCode for micro:bit](https://makecode.microbit.org/) for the isolated first test. The linked V2 preparation chapter documents the manufacturer extension and expansion board. Add those only when moving to the matching kit project.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Verify whether the selected option includes a micro:bit. Obtain the correct board separately if excluded.
2. Disconnect the micro:bit from the robot and attach it to a computer using a USB data cable. Confirm the MICROBIT drive appears.
3. Open MakeCode for micro:bit and create a new project. Put a **show icon** block inside **forever**, choosing a heart or another visible icon.
4. Click Download and pair the micro:bit if the browser supports direct download. Otherwise save the generated HEX file and copy it to the MICROBIT drive.
5. Wait for the transfer indicator to finish, then check the LED matrix. Save the project before disconnecting USB.
6. For subsequent kit projects, use the exact V2 expansion-board extension and wiring manual. This USB-only example does not validate the motor supply, AI module or expansion-board port mapping.

**Expected result:** The bare micro:bit displays the chosen LED icon, confirming the basic editor/download path without moving the assembled kit.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/DaDabitV2/en/latest/docs/2_Preparation.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**MICROBIT drive missing:** try a USB data cable and a direct computer port. A charge-only cable can light the board without providing a drive.

**HEX disappears after copying:** this is normal flashing behaviour; confirm the LED output instead of expecting the file to remain.

**Icon works but the assembled robot does not:** the first test verifies the micro:bit only. Check the expansion-board battery, orientation, kit extension and port mapping separately.

**AI functions absent:** verify the AI-specific module is actually in the purchased kit; a basic V2 kit does not gain cloud functions by installing a generic extension.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/DaDabitV2/en/latest/docs/2_Preparation.html)
* [Manufacturer Hiwonder DaDa:bit V2 micro:bit Robotics & Electronic Block Kit specifications and option drawings](https://www.hiwonder.com/products/dada-bit-v2)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hiwonder-dada-bit-v2).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/DaDabitV2/en/latest/docs/2_Preparation.html)
* [Manufacturer Hiwonder DaDa:bit V2 micro:bit Robotics & Electronic Block Kit specifications and option drawings](https://www.hiwonder.com/products/dada-bit-v2)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
