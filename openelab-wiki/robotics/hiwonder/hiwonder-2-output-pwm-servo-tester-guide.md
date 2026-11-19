---
description: >-
  A stand-alone knob-operated PWM tester for centering and checking servos
  without writing a program. The two outputs share the knob command; they are
  not two independently programmable channels.
---

# Hiwonder 2-Output PWM Servo Tester Guide

{% hint style="info" %}
[**View Hiwonder 2-Channel Digital Servo Tester with Voltage Display on OpenELAB**](https://openelab.io/products/digital-servo-tester)

**SKU:** `Hiwonder-13040034`

**Model / revision scope:** 2-Output PWM Servo Tester. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![2-Output PWM Servo Tester — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-71.jpg)

## Product overview

A stand-alone knob-operated PWM tester for centering and checking servos without writing a program. The two outputs share the knob command; they are not two independently programmable channels.

### Models and purchasing options

| OpenELAB SKU        | Purchased option |
| ------------------- | ---------------- |
| `Hiwonder-13040034` | Default Title    |

## Applications

Bench integration, education and development with the exact hardware listed above. Start with the first-result workflow before expanding the assembly or enabling autonomous operation.

## Specifications

| Parameter         | Value / scope                                  |
| ----------------- | ---------------------------------------------- |
| PWM outputs       | 2                                              |
| Supply            | 5–8.4 V; additionally constrained by the servo |
| Modes             | Manual knob control and Neutral mode           |
| Display           | Input voltage                                  |
| Dimensions / mass | 50 × 35 mm / 13.5 g                            |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/digital-servo-tester-controller-with-voltage-display-hiwonder) and [OpenELAB listing](https://openelab.io/products/digital-servo-tester). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Connect the servo lead to the marked **S / + / −** pins. Choose one board power input and match the supply to the servo; the board does not convert an 8.4 V battery into a 6 V servo rail. Keep exposed pins away from metal parts and mount the board on insulating spacers.

## Software and development resources

No PC application, firmware installation or SDK is required for manual testing. This tester does not save motion sequences and does not control serial-bus servos.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Remove the servo horn/load and turn the tester off before wiring.
2. Connect one compatible PWM servo with S, + and − aligned to the labels.
3. Apply a regulated voltage within both board and servo ratings. Read the displayed voltage before using the knob.
4. Select **Neutral Mode** with the mode/reset button to center the servo. Its physical angle depends on whether the servo has 180° or 270° travel.
5. Switch to Manual Mode and turn the corresponding knob a small amount. Return to Neutral Mode and confirm repeatable centering.
6. Power off before fitting the horn or adding another servo.

**Expected result:** The displayed supply remains stable, the unloaded servo follows a small knob change, and Neutral Mode returns it to its midpoint.

Procedure reference: [official model or interface manual](https://www.hiwonder.com/products/digital-servo-tester-controller-with-voltage-display-hiwonder). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No response:** start with the power indicator and cable connections, then verify the selected product/controller profile. Restore communication before running a motion example.

**A function is missing:** compare the order option with the required sensors, controller and software package. A demonstration on an advanced kit does not establish support on an accessory-only or controller-excluded option.

## Downloads and technical documents

* [Official user / interface manual](https://www.hiwonder.com/products/digital-servo-tester-controller-with-voltage-display-hiwonder)
* [Manufacturer Hiwonder 2-Channel Digital Servo Tester with Voltage Display specifications and option drawings](https://www.hiwonder.com/products/digital-servo-tester-controller-with-voltage-display-hiwonder)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/digital-servo-tester).
* [Official user / interface manual](https://www.hiwonder.com/products/digital-servo-tester-controller-with-voltage-display-hiwonder)
* [Manufacturer Hiwonder 2-Channel Digital Servo Tester with Voltage Display specifications and option drawings](https://www.hiwonder.com/products/digital-servo-tester-controller-with-voltage-display-hiwonder)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
