---
description: >-
  An ESP32/CoreX vision arm with a separate bus-servo controller and selectable
  sensor/AI options.
---

# Hiwonder xArm AI Guide

{% hint style="info" %}
[**View Hiwonder xArm AI Robot Arm Kit - Arduino, Scratch & Python on OpenELAB**](https://openelab.io/products/hiwonder-xarm-ai-robot-arm)

**SKU:** `Hiwonder-20010060`, `Hiwonder-20010061`, `Hiwonder-20010062`

**Model / revision scope:** xArm AI. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![xArm AI — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-10.webp)

## Product overview

An ESP32/CoreX vision arm with a separate bus-servo controller and selectable sensor/AI options.

### Models and purchasing options

| OpenELAB SKU        | Purchased option |
| ------------------- | ---------------- |
| `Hiwonder-20010060` | Starter Kit      |
| `Hiwonder-20010061` | Standard Kit     |
| `Hiwonder-20010062` | Advanced Kit     |

## Applications

Bench integration, education and development with the exact hardware listed above. Start with the first-result workflow before expanding the assembly or enabling autonomous operation.

## Specifications

| Parameter    | Value / scope                                                                |
| ------------ | ---------------------------------------------------------------------------- |
| Main control | ESP32 family; exact expansion board as supplied                              |
| Power        | 7.5 V, 6 A supplied adapter                                                  |
| Mechanism    | 6-DOF arm family                                                             |
| Software     | Factory control firmware; Arduino / Python / graphical lessons vary by model |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/xarm-ai) and [OpenELAB listing](https://openelab.io/products/hiwonder-xarm-ai-robot-arm). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

Inspect the numbered servo/motor cables while power is off and use the supplied power system. Secure the base with its mounting hardware and leave the gripper empty. Do not overwrite the preloaded app firmware for the first test. Vision and voice functions require the modules named in the purchased kit.

## Software and development resources

The initial check uses the factory program. Use the model-specific Arduino, MicroPython or graphical-programming lessons only after it succeeds. Uploading an unrelated example can replace the app-control program; restore only from the exact model’s documented factory package.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Match the SKU, body, battery/adapter and optional modules to the order. Complete the model’s assembly before powering on.
2. Clear the motion envelope and power on with the supplied matching power system. For xArm AI, turn on both the servo controller and CoreX controller.
3. Install **Wonderbot** from the xArm AI official resources. Enable Bluetooth and nearby-device discovery permissions.
4. Select **Robot → xArm AI**, open Robot Control and tap the Bluetooth icon. Connect to the device named **xArm** inside the app; do not use a phone-settings passkey.
5. Confirm the connection indicator is steady and the reported battery/supply status is plausible. Use the manual control screen for a small unloaded motion, then return to the initial pose.
6. Stop and power off before changing mechanical parts. Save a backup of custom programs before any later factory-firmware restoration.

**Expected result:** The correct device is paired inside the app, supply status is visible, and a small manual motion completes without stalling or loss of connection.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/xArm_AI/en/latest/docs/2.Remote_Control.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**Bluetooth device missing:** power-cycle once, enable nearby-device/location permissions, close another connected phone and search inside the app.

**App connected but controls fail after programming:** a custom program may have replaced the factory app service. Back up the current program and use the model’s documented restoration package.

**Joints strain at startup:** switch off, check assembly and cable numbering, and confirm the initial posture; do not force a powered servo.

**Vision/voice unavailable:** verify that the selected kit contains the required module and that its own firmware and connection match the robot.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/xArm_AI/en/latest/docs/2.Remote_Control.html)
* [Manufacturer Hiwonder xArm AI Robot Arm Kit - Arduino, Scratch & Python specifications and option drawings](https://www.hiwonder.com/products/xarm-ai)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hiwonder-xarm-ai-robot-arm).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/xArm_AI/en/latest/docs/2.Remote_Control.html)
* [Manufacturer Hiwonder xArm AI Robot Arm Kit - Arduino, Scratch & Python specifications and option drawings](https://www.hiwonder.com/products/xarm-ai)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
