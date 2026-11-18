# Seeed Studio Semtech LR2021 LoRa Plus Evaluation Kit Development Guide

{% hint style="info" %}
[**View Seeed Studio Semtech LR2021 LoRa Plus Evaluation Kit on OpenELAB**](https://openelab.io/products/seeed-studio-semtech-lr2021-lora)

**Model/variant:** Seeed Studio Semtech LR2021 LoRa Plus Evaluation Kit · **OpenELAB SKU:** `Seeed-100039980`
{% endhint %}

[Product at OpenELAB](https://openelab.io/products/seeed-studio-semtech-lr2021-lora)

## Exact kit and applications

This page covers the **Semtech LR2021 LoRa Plus evaluation kit**, including OpenELAB **Seeed-100039980**. It uses a **XIAO nRF54L15** core board and an LR2021 expansion board. The separately documented **Wio-LR2021 Dev Kit uses ESP32-S3** and requires a different software target.

| Item             | Evaluation-kit reference                              |
| ---------------- | ----------------------------------------------------- |
| Core             | nRF54L15, Cortex-M33 up to 128MHz                     |
| Host input       | USB-C, 5V                                             |
| RF variants      | EU868, US915 and CN490 packages                       |
| Radio modes      | LoRa and additional supported LR2021 modulation modes |
| Expansion        | Grove interfaces and two RF antenna connectors        |
| Example software | Semtech USP with Zephyr                               |

Use it for radio evaluation and custom telemetry prototypes. A raw radio example is not automatically a configured LoRaWAN or Meshtastic node.

## Documents and first build

The manufacturer guide supplies **board diagrams, signal mapping and hardware references**. Match the region-specific RF board and antenna before enabling transmit.

1. Install the guide's Zephyr dependencies and SDK on a supported host; Ubuntu 22.04 is its recommended reference.
2. Create a Python virtual environment, install `west`, and obtain **Lora-net/usp\_zephyr**.
3. Initialize from its manifest, run `west update`, and install the project's Python requirements and toolchain.
4. Choose the guide's **XIAO nRF54L15 + LR2021** board/sample combination. Build and flash using the documented runner.
5. Open its serial log and verify radio initialization. For a packet test, configure a second compatible node with the same frequency and modulation settings.

**Checkpoint:** a reproducible build and packet reception with the selected RF configuration. Record both nodes' manifests, radio settings and firmware revisions.

## FAQs and recovery

**Can I copy an ESP32-S3 Wio build command?** No; these are different host processors.

**No packets?** Check frequency plan, antenna, modulation, spreading factor/bandwidth and payload settings on both ends.

**Build worked yesterday?** Export the resolved West manifest and pin the source revision rather than relying on a moving branch.

**Recovery?** Follow the nRF54L15 kit's documented flashing/debug procedure. Do not use an nRF52840 UF2 or an ESP32 image.

## Sources and validation

* [Exact evaluation-kit hardware and setup](https://wiki.seeedstudio.com/semtech_lr2021_evk_getting_started/)
* [Semtech USP Zephyr software](https://github.com/Lora-net/usp_zephyr)
* [EU868 kit reference](https://www.seeedstudio.com/LR2021-LoRa-Plus-Evaluation-kit-868Mhz-EU-V2-0-p-6697.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
