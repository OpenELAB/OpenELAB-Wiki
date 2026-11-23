---
description: >-
  Connect the SKU23739 10.1DP-CAPLCD through HDMI and USB touch, with correct
  DP-versus-HP scope and host troubleshooting.
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Waveshare 10.1 inch IPS Capacitive Touch Display

{% hint style="info" %}
[**View Waveshare 10.1-inch IPS touch display on OpenELAB**](https://openelab.io/products/101inchipscapacitivetouchdisplay)

**Model:** 10.1DP-CAPLCD · **OpenELAB / manufacturer code:** `Waveshare-23739` / `23739` · HDMI video with separate USB touch.
{% endhint %}

## Product overview

SKU23739 identifies **10.1DP-CAPLCD**. The earlier page described the different 10.1HP-CAPLCD Monitor, including a USB-C video capability that must not be assumed for DP. Use HDMI for this model's video and USB for its touch interface. [Manufacturer product and SKU](https://www.waveshare.com/10.1DP-CAPLCD.htm), [DP model wiki](https://www.waveshare.com/wiki/10.1DP-CAPLCD).

## Applications

Use it as a touch interface for an HDMI host or an integrated panel project. Treat video, touch and power as three separate connections to validate. For mechanical integration, use the DP drawing rather than the HP monitor's enclosure dimensions.

## Specifications

| Item                      | 10.1DP-CAPLCD                                |
| ------------------------- | -------------------------------------------- |
| Panel / native resolution | 10.1-inch IPS / 1280 × 800                   |
| Touch                     | Capacitive, up to 10 points; USB interface   |
| Display signal            | HDMI                                         |
| Supply                    | 5 V through the labelled Type-C power input  |
| Adjustment                | On-screen brightness/contrast menu           |
| Audio                     | HDMI audio, 3.5 mm output and speaker header |

These are the [DP product specifications](https://www.waveshare.com/10.1DP-CAPLCD.htm). The [electrical table](https://www.waveshare.com/wiki/10.1DP-CAPLCD) specifies a 4.75–5.25 V input window; its PC instructions recommend an external **5 V, 1 A** adapter if host USB power is insufficient.

## Hardware and connections

Connect the labelled **Touch** interface to a USB data port and **HDMI** to the host's HDMI output. Use the separate **Power** input where required. A USB cable connected only for power does not supply video or prove touch communication. Check the DP interface diagram before connecting; do not substitute a photograph of another screen. [Connection reference](https://www.waveshare.com/wiki/10.1DP-CAPLCD).

## Software and development resources

The panel is a host display, not a microcontroller board needing an Arduino SDK. The manufacturer documents Windows and Raspberry Pi/Linux routes. It also provides DDC/CI brightness guidance and mechanical downloads. OS display mode, rotation and touchscreen association are host configuration tasks; keep the host/OS version in the integration record.

## Getting started

1. Prepare the DP panel, an HDMI computer, HDMI cable, USB data cable and adequate 5 V power.
2. Connect touch USB and HDMI, then start the host. Select **1280 × 800** as the native display mode if it is not identified automatically.
3. Open a simple full-screen test image. Check all edges for cropping, then test touch at the corners and centre independently of video.
4. On a Windows multi-monitor system, use **Calibrate the screen for pen or touch input → Setup** to associate the touch device with the intended display.

**Expected result:** a correctly sized image and touches mapped to that same panel. The [official Windows procedure](https://www.waveshare.com/wiki/10.1DP-CAPLCD) supplies the setup screens. **Observed result:** not tested on a computer or panel in this review.

### Raspberry Pi and brightness

The [DP wiki](https://www.waveshare.com/wiki/10.1DP-CAPLCD) contains EDID timing, Raspberry Pi setup, DDC/CI brightness and Windows brightness references. Its `hdmi_group`/`hdmi_mode` recipe is a legacy configuration path; check the active display stack and OS documentation before applying it to a current image. Prefer a confirmed native mode before adding custom timings. Back up existing configuration rather than rewriting a working card for a display fault.

## Troubleshooting and FAQs

**No picture:** confirm HDMI source selection, power and the host's display detection. USB touch enumeration alone does not prove the video path.

**Picture works but touch does not:** verify a USB data cable and host device enumeration; then check display association. Diagnose rotation only after ordinary touch works.

**Flicker or repeated disconnects:** compare the supply and cables with the manufacturer's external-power arrangement before changing resolution or drivers.

**USB-C video does not work:** this SKU is DP, not the HP monitor described on the earlier page. Use the specified HDMI connection.

## Downloads and technical documents

| Resource                                                                                       | Purpose                                                                        |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Full DP wiki](https://www.waveshare.com/wiki/10.1DP-CAPLCD)                                   | Electrical table, EDID, connection diagrams, OS procedures, brightness and FAQ |
| [Drawing PDF](https://files.waveshare.com/wiki/10.1DP-CAPLCD/10.1DP-CAPLCD/10_1dp-caplcd.pdf)  | Model-specific dimensions                                                      |
| [2D source](https://files.waveshare.com/wiki/10.1DP-CAPLCD/10.1DP-CAPLCD/10.1DP-CAPLCD_2D.zip) | Mechanical integration                                                         |
| [3D source](https://files.waveshare.com/wiki/10.1DP-CAPLCD/10.1DP-CAPLCD/10_1DP-CAPLCD_3D.zip) | Mechanical integration                                                         |

## References and validation

Official model/SKU and wiki reviewed **23 November 2026**. This corrects DP-versus-HP scope while retaining the established OpenELAB URL. No OS configuration, download package execution or physical test was performed. Use the DP drawings as the authority for connectors and mounting; older general illustrations below do not establish DP pin positions or USB-C video support.

## Existing illustrations

Original page illustrations are retained below. Use the exact-model pin map and revision notes in this guide when interpreting them.

<figure><img src="https://www.waveshare.com/w/upload/7/78/10.1HP-CAPLCD_Monitor01.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/8/84/8DP-CAPLCD10.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/b/b9/8HP-CAPLCD_Monitor04.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/e/e3/8HP-CAPLCD_Monito03.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/9/99/Win10_touch02.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/4/43/8HP-CAPLCD_Monitor05.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/e/e6/8HP-CAPLCD_Monitor_06.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/c/c7/10.1HP-CAPLCD_Monitor09.jpg" alt=""><figcaption></figcaption></figure>
