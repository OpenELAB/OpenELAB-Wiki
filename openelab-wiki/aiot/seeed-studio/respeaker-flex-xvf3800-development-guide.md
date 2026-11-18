# Seeed Studio reSpeaker Flex XVF3800 Development Guide

{% hint style="info" %}
[**View Seeed Studio reSpeaker Flex XVF3800 on OpenELAB**](https://openelab.io/products/seeed-studio-respeaker-flex-xvf3800-circular-4-with-xiao-esp32s3)

**Model/family:** Seeed Studio reSpeaker Flex XVF3800 · **OpenELAB SKUs:** `Seeed-100070894`, `Seeed-100099135`, `Seeed-100005504`, `Seeed-100026178` · Confirm exact purchased model and option before following wiring/firmware instructions.
{% endhint %}

[Product at OpenELAB](https://openelab.io/products/seeed-studio-respeaker-flex-xvf3800-circular-4-with-xiao-esp32s3) · [Seeed hub](./)

## Product and variant selection

reSpeaker Flex separates an XMOS XVF3800 processing board from a four-microphone array using an FPC cable. It suits robot heads, voice terminals and products whose microphones must be positioned away from the processor.

| Ordering code | Array      | XIAO ESP32S3 |
| ------------- | ---------- | ------------ |
| 100070894     | Circular-4 | Included     |
| 100005504     | Circular-4 | Not included |
| 100026178     | Linear-4   | Included     |
| 100099135     | Linear-4   | Not included |

Circular and linear arrays have different geometry and directivity. This guide excludes the all-in-one circular XVF3800 USB array.

## Hardware and technical documents

The Flex supports USB UAC 2.0 or I2S operation, with I2C control. Its processing includes AEC, AGC, beamforming, direction of arrival and voice activity detection. The microphone connection is a **24-pin, 0.5mm-pitch FPC**. Disconnect power before opening the latch, align the cable contacts with connector contacts and fully close the latch.

Use the official hardware guide's complete pin table and 2D DXF links when designing an enclosure or a cable. The STEP models below cover each array and the separate core board. External **12V** power supports the onboard speaker amplifier; select the documented speaker load and power path. Do not apply 12V to a USB or logic pin.

## First useful test: USB capture

1. For USB operation, install the **Flex USB firmware**, using the matching two- or six-channel profile. XIAO-equipped units may instead arrive with I2S firmware.
2. Connect the XMOS USB data port to a host. On Linux, inspect device enumeration and capture capabilities:

```bash
lsusb
arecord -l
```

3. Select the Flex in an audio recorder, using formats actually exposed by that firmware. Record a short spoken phrase and play it back.
4. From the official repository's `python_control` directory, install its dependencies and inspect the read-only control interface:

```bash
python xvf_host.py VERSION
python xvf_host.py DOA_VALUE
```

**Checkpoint:** intelligible capture and a reported firmware version. Change one DSP setting at a time and retain a baseline recording.

## Embedded development and recovery

The XIAO path uses **I2S firmware on the XMOS** and a separate application on the ESP32S3. Use Seeed's pin map and Arduino Audio Tools integration; firmware for one processor does not update the other. Record both versions.

If USB disappears after flashing, confirm the firmware mode, then use the Flex's documented SafeMode button/power-on sequence and DFU procedure. Do not use another reSpeaker model's image.

## FAQs

**No speaker output?** Check the selected output, power and mixer; the AUX connection takes precedence when both outputs are connected.

**No sound card on a XIAO model?** Check whether its XMOS is running I2S firmware.

**Poor pickup inside an enclosure?** Keep the microphone inlets clear and facing the acoustic environment; preserve array geometry and evaluate echo with the actual loudspeaker placement.

## Sources and validation

* [Flex hardware, firmware, Python control and drawings](https://wiki.seeedstudio.com/respeaker_flex_introduction/)
* [XIAO ESP32S3 integration](https://wiki.seeedstudio.com/respeaker_flex_xiao_introduction/)
* [Official firmware and Python SDK](https://github.com/respeaker/reSpeaker_Flex)
* [Circular array CAD](https://files.seeedstudio.com/wiki/reSpeaker_flex/reSpeaker_xvf3800_flex_circular_260210.step)
* [Linear array CAD](https://files.seeedstudio.com/wiki/reSpeaker_flex/reSpeaker_xvf3800_flex_linear.step)
* [Core board CAD](https://files.seeedstudio.com/wiki/reSpeaker_flex/reSpeaker_xvf3800_flex_Separate.step)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
