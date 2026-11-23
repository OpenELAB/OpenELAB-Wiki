# Seeed Studio reSpeaker Lite and Voice Assistant Kit Development Guide

{% hint style="info" %}
[**View reSpeaker Lite on OpenELAB**](https://openelab.io/products/seeed-studio-respeaker-lite-2) · [**View reSpeaker Lite Voice Assistant Kit on OpenELAB**](https://openelab.io/products/seeed-studio-respeaker-lite-voice-assistant-kit)

**Product model/family:** Seeed Studio reSpeaker Lite and Voice Assistant Kit · **OpenELAB SKUs:** `Seeed-110061601`, `Seeed-E24072601` · Check exact board/kit option and revision for firmware selection.
{% endhint %}

[Lite listing](https://openelab.io/products/seeed-studio-respeaker-lite-2) · [Voice Assistant Kit listing](https://openelab.io/products/seeed-studio-respeaker-lite-voice-assistant-kit)

## Identity and applications

The reSpeaker Lite is a **two-microphone** voice front end. OpenELAB **Seeed-110061601** and **Seeed-E24072601** describe different package configurations; inspect whether the XIAO ESP32S3, speaker, enclosure and cables are included before selecting a workflow.

Use the board for USB voice capture or as an I2S audio front end for a XIAO application. Speech recognition and Home Assistant's voice pipeline require their own host/services.

| Item                | Integration requirement                                |
| ------------------- | ------------------------------------------------------ |
| Microphones         | Two-microphone array                                   |
| Audio paths         | USB audio or I2S, selected by XMOS firmware            |
| Embedded host       | XIAO ESP32S3 for the corresponding voice-kit path      |
| Power contract      | 5V through USB or the documented 5V pad                |
| Firmware processors | XMOS audio firmware and ESP32 application are separate |

## Quick start: prove the microphone path first

1. Connect the **Lite board's USB data port** to the computer with a data cable.
2. With USB-mode firmware, select **ReSpeaker Lite** as the recording input. Record a short phrase, then play the file through a known-working output.
3. On Linux, use `arecord -l` to confirm capture enumeration. Query the actual supported format before setting a recorder; do not copy another reSpeaker model's channel count.
4. Save a baseline recording and the firmware version.

**Expected result:** a visible capture device and intelligible audio. If the unit is already configured for XIAO/I2S, follow the official switch-to-USB firmware procedure before expecting a sound card.

## Home Assistant and development

Follow the manufacturer-linked Home Assistant tutorial for the kit. Its XMOS I2S image and the ESPHome configuration must agree on sample rate and clocking. The tutorial identifies `respeaker_lite_i2s_dfu_firmware_48k_v1.1.0.bin` for its playback workflow; confirm the currently supported configuration before adopting a different image.

Use the project's current ESPHome requirements and record its commit and your ESPHome version. Build and test the audio pipeline before enabling wake-word automations.

## Resources, recovery and FAQs

The board guide's Resources section links firmware, source and a **3D file**. Consult it for the current hardware package rather than assuming compatibility with XVF3800/Flex drawings.

**No USB audio after flashing?** Confirm USB firmware, power-cycle and inspect the host's device/driver binding.

**DFU is invisible on Windows?** Follow Seeed's interface-specific WinUSB instructions. Changing the wrong interface's driver can disrupt normal audio.

**Can I apply 12V like a Flex board?** No. Lite's published supply contract is 5V.

**Does flashing ESPHome update XMOS?** No. Treat recovery and version records for both processors separately.

## Sources and validation

* [Lite board, firmware, SDK and 3D resource links](https://wiki.seeedstudio.com/reSpeaker_usb_v3/)
* [Voice Assistant Kit](https://wiki.seeedstudio.com/xiao_respeaker/)
* [Home Assistant integration tutorial](https://wiki.seeedstudio.com/respeaker_lite_ha/)
* [Manufacturer troubleshooting](https://wiki.seeedstudio.com/respeaker_lite_faq/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Getting Started with reSpeaker Lite](https://wiki.seeedstudio.com/reSpeaker_usb_v3/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                             |
| ---------------------- | ---------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/respeakerv3/ReSpeakerLitev1.1.step) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
