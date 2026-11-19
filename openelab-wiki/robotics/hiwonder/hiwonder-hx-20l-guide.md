---
description: >-
  HX-20L is an addressable serial-bus actuator with position, voltage and
  temperature feedback. Its 240° position range and 115200-baud interface
  identify the control family covered by this guide.
---

# Hiwonder HX-20L Guide

{% hint style="info" %}
[**View Hiwonder HX-20L 20kg.cm Dual-Shaft Metal Gear Serial Bus Servo on OpenELAB**](https://openelab.io/products/hx-20l-bus-servo)

**SKU:** `Hiwoner-21100030`

**Model / revision scope:** HX-20L. Match the purchased option below; hardware revisions and controller images are not interchangeable.
{% endhint %}

![HX-20L — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-57.jpg)

## Product overview

HX-20L is an addressable serial-bus actuator with position, voltage and temperature feedback. Its 240° position range and 115200-baud interface identify the control family covered by this guide.

### Models and purchasing options

| OpenELAB SKU       | Purchased option |
| ------------------ | ---------------- |
| `Hiwoner-21100030` | Default Title    |

## Applications

Joint positioning, grippers and small robotic mechanisms; choose the mechanism and duty cycle from the electrical and mechanical limits below.

## Specifications

| Parameter               | Value / scope                                         |
| ----------------------- | ----------------------------------------------------- |
| Supply range            | 6–8.4 V                                               |
| Position range          | 240°; command values 0–1000                           |
| Direct bus baud rate    | 115,200 bit/s                                         |
| Torque reference        | 17 kgf·cm at 6 V; 19.5 kgf·cm at 7.4 V                |
| Mass                    | 54 g                                                  |
| Stall-current reference | 2.4–3 A                                               |
| Initial identity        | Default ID 1; read the existing ID before changing it |

Specifications: [manufacturer product data](https://www.hiwonder.com/products/hx-20l) and [OpenELAB listing](https://openelab.io/products/hx-20l-bus-servo). Figures describe the stated configuration; accessory-only options do not inherit the complete kit specifications.

## Hardware and connections

This is a **serial-bus servo**, not a PWM servo. Use its matching three-wire keyed cable and a compatible half-duplex bus interface. Identify signal, supply and ground from the connector diagram and board labels; connector shape alone is not a pinout. Power the motor rail externally at a voltage shared by the servo and interface board.

The initial check below uses the Hiwonder Bus Servo Controller and its **Servo Test** tool. The controller’s host UART is **9600 baud**, while the direct servo bus is **115200 baud**; these are separate interfaces. Use a regulated 7.4 V supply for this check, within the controller’s 6–12 V range as well as the servo range. Do not apply the servo’s maximum voltage blindly to an attached controller.

## Software and development resources

Use the Hiwonder Bus Servo Controller application for the first check. Direct MCU control requires the legacy bus-servo command protocol and a half-duplex electrical interface, not a bare RS-232 adapter. The controller’s action-group protocol differs from direct servo packets.

## Getting started

**Prerequisites:** the selected hardware, its matching power source, the required data cable, and a clear work area. Begin with the supplied firmware and an unloaded mechanism.

1. Disconnect all other servos, remove the load and secure the body. Confirm the exact model suffix on the case and the supply voltage before connecting the keyed bus cable.
2. With power off, connect one servo to the Bus Servo Controller. Attach the external regulated 7.4 V supply with red to + and black to −, then connect USB and switch the controller on.
3. Open **Bus Servo Control V3.4** from the official controller Appendix. Confirm the wired connection indicator and open **Servo Test** for the single connected servo.
4. Read the servo ID, position, voltage and temperature before editing anything. A factory-new unit is normally ID 1; a previously used unit may retain another ID.
5. Select servo/position mode. With the horn unloaded, command a small nearby position and read it back. Keep values within 0–1000 and the mechanism’s limits. Do not start with an end-to-end sweep.
6. After successful readback, power off before fitting the linkage. Set unique IDs individually, then connect additional compatible servos and test them one at a time.

**Expected result:** The single servo is detected, plausible voltage/temperature/position values are returned, and a small unloaded position command changes the readback. Readback alone does not prove loaded accuracy or continuous torque.

Procedure reference: [official model or interface manual](https://wiki.hiwonder.com/projects/Bus-Servo-Controller/en/latest/docs/1.Bus_Servo_Controller_User_Manual.html). The steps above are a bounded initial check, not a substitute for the full assembly and development chapters.

## Troubleshooting and FAQs

**No movement:** first check the servo power rail under load, ground continuity and the selected control interface. USB connection alone does not establish motor power. Test one unloaded servo before adding a chain.

**Jitter, heat or repeated resets:** disconnect the mechanical load, check for an obstructed horn and measure supply droop. A stall-torque figure is not a continuous operating torque. Reduce the load and duty cycle; do not increase supply voltage beyond the specified limit.

**Wrong travel:** verify the exact suffix and position scale. Mechanical joint limits can be narrower than the servo specification. Set limits for the installed mechanism before running a sequence.

## Downloads and technical documents

* [Official user / interface manual](https://wiki.hiwonder.com/projects/Bus-Servo-Controller/en/latest/docs/1.Bus_Servo_Controller_User_Manual.html)
* [Manufacturer Hiwonder HX-20L 20kg.cm Dual-Shaft Metal Gear Serial Bus Servo specifications and option drawings](https://www.hiwonder.com/products/hx-20l)

Use the manual’s download or appendix section for the matching revision. A linked download directory is not a claim that every firmware archive, CAD file or installer has been tested. Do not flash an image for a similarly named product.

## References and validation

* [OpenELAB product and SKU options](https://openelab.io/products/hx-20l-bus-servo).
* [Official user / interface manual](https://wiki.hiwonder.com/projects/Bus-Servo-Controller/en/latest/docs/1.Bus_Servo_Controller_User_Manual.html)
* [Manufacturer Hiwonder HX-20L 20kg.cm Dual-Shaft Metal Gear Serial Bus Servo specifications and option drawings](https://www.hiwonder.com/products/hx-20l)

Reviewed against the linked sources on 19 November 2026. Software installation, compilation and physical hardware tests were not performed for this guide. Use the observable checkpoints above to verify your own unit before integrating it into a larger system.
