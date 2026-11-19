---
description: >-
  Green Tracked Chassis is a mechanical drive platform for a separately chosen
  controller and motor-driver system. Select the exact encoder, driver and layer
  option from the SKU table.
---

# Hiwonder Green Tracked Chassis Guide

{% hint style="info" %}
[**View Hiwonder Tank Car Chassis Kit (Green) on OpenELAB**](https://openelab.io/products/track-chassis-kit-green)

**SKU:** `Hiwonder-21030018`, `Hiwonder-210300130`

**Model / revision scope:** Green Tracked Chassis. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![Green Tracked Chassis — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-126.jpg)

## Product overview

Green Tracked Chassis is a mechanical drive platform for a separately chosen controller and motor-driver system. Select the exact encoder, driver and layer option from the SKU table.

### Models and purchasing options

| OpenELAB SKU         | Purchased option      |
| -------------------- | --------------------- |
| `Hiwonder-21030018`  | DC Gear Motor         |
| `Hiwonder-210300130` | DC Gear Encoder Motor |

## Applications

Bench integration, education and development with the exact hardware listed above. Start with the first-result workflow before expanding the assembly or enabling autonomous operation.

## Specifications

| Parameter     | Value / scope                                                |
| ------------- | ------------------------------------------------------------ |
| Motor voltage | 8 V motor specification                                      |
| Drive         | Geared drive motors; encoder option depends on purchased kit |
| Dimensions    | 306 × 230 × 128 mm                                           |
| Mass          | Approximately 1.4 kg                                         |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/tank-car-chassis-kit-green) and [OpenELAB listing](https://openelab.io/products/track-chassis-kit-green). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Match the motor driver’s voltage and current capability to the installed motor. Route motor-power wires separately from encoder signals and keep cables away from wheels/tracks. Identify each motor and encoder connector using the supplied drawing; connector shape alone does not establish pin order. Check track tension and roller alignment before applying power; an overtight track increases current and wear.

## Software and development resources

The chassis itself has no firmware image. Use the selected motor-driver examples, then configure the real wheel diameter, wheelbase/track width and encoder counts in your controller. A Mecanum, differential-track and Ackermann drive use different kinematics.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Lay out the chassis parts and match the selected packing option. Confirm whether encoder motors and a driver board are included.
2. Assemble the frame and wheels/tracks using the manufacturer’s product drawings, with all electronics unpowered.
3. Secure the chassis with wheels/tracks clear of the work surface. Confirm free cable routing and no frame contact.
4. Connect one motor to a suitably rated driver using its verified terminal diagram. Use a supply matched to the motor voltage above, not a voltage copied from a different-colour chassis.
5. Command a brief low-speed movement, stop, and reverse. Repeat for the other motor channels and record each direction before coordinated driving.
6. For encoder-equipped options, verify counts change when that motor turns before enabling closed-loop speed control.

**Expected result:** Each installed motor responds individually, stops reliably and turns in a recorded direction; encoder-equipped channels produce changing feedback. The chassis is then ready for controller-specific kinematic calibration.

Procedure reference: [official model or interface manual](https://www.hiwonder.com/products/tank-car-chassis-kit-green). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**Robot turns instead of moving straight:** test motors individually and compare the channel/direction map. For Mecanum wheels also verify handedness and mounting order.

**High current or poor travel:** inspect track tension, wheel/frame contact, binding bearings and supply droop before raising the command.

**No encoder data:** first confirm the purchased option actually includes encoders, then verify its power and A/B signal mapping.

**Controller absent:** this is a chassis listing; only the selected packing option determines the supplied electronics.

## Downloads and technical documents

* [Official user / interface manual](https://www.hiwonder.com/products/tank-car-chassis-kit-green)
* [Manufacturer Hiwonder Tank Car Chassis Kit (Green) specifications and option drawings](https://www.hiwonder.com/products/tank-car-chassis-kit-green)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/track-chassis-kit-green).
* [Official user / interface manual](https://www.hiwonder.com/products/tank-car-chassis-kit-green)
* [Manufacturer Hiwonder Tank Car Chassis Kit (Green) specifications and option drawings](https://www.hiwonder.com/products/tank-car-chassis-kit-green)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
