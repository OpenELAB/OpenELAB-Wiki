# LILYGO T-SIM7080G S3 H606 Engineering Guide

{% hint style="info" %}
[**View LILYGO T-SIM7080G S3 H606 on OpenELAB**](https://openelab.io/products/lilygo-t-sim7080g-s3)

**Product model/family:** LILYGO T-SIM7080G S3 H606 · **OpenELAB SKU:** `LILYGO-H606`
{% endhint %}

[LILYGO-H606](https://openelab.io/products/lilygo-t-sim7080g-s3)

## Product and scope

**H606 T-SIM7080G S3** combines ESP32-S3 with a SIM7080G **LTE-M / NB-IoT** modem and positioning capability. It is intended for low-bandwidth telemetry. It is not a conventional LTE Cat4 modem; a general mobile-data SIM may lack the required service.

## Hardware and technical documents

| Item                 | Reference                                           |
| -------------------- | --------------------------------------------------- |
| MCU                  | ESP32-S3                                            |
| Modem                | SIM7080G                                            |
| Cellular service     | Cat-M / NB-IoT with operator and band support       |
| Positioning          | GNSS; verify the antenna connection                 |
| Revision distinction | H606 differs from newer H795 Standard documentation |

The legacy manufacturer repository contains the **H606 pinout, schematic, power-control sequence and antenna connections**. Use it for the delivered hardware. Modem peak current, SIM voltage and RF routing must follow that design; a USB-connected MCU does not prove the modem is powered.

## Getting started

1. With power off, install a provisioned LTE-M/NB-IoT SIM and the correct cellular/GNSS antennas.
2. Open the H606 repository and select its **ATDebug** example with the documented board configuration.
3. Power the modem through the example's sequence and send **AT**; expect **OK**.
4. Inspect SIM and registration status using the modem's documented AT commands, then set the operator-provided APN.
5. Perform one small data transfer using the matching example before testing sleep or GNSS upload.

**Expected checkpoint:** AT communication, SIM recognition and registration on a supported service.

## Development software and recovery

Use the H606 examples and required library versions. The newer **LilyGo-Modem-Series** distinguishes board variants and uses its own TinyGSM fork; retain the target/commit rather than mixing dependencies. Recover the ESP32 application and modem firmware as separate devices.

## FAQs

**SIM works in a phone but not here?** Verify LTE-M/NB-IoT provisioning, APN, bands and local network support.

**SIM not detected after insertion?** The manufacturer instructs inserting the SIM before modem startup.

**AT is silent?** Check modem power key sequence, supply and H606 UART pins.

## Sources and validation

* [Exact legacy manufacturer repository](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/master/README.MD)
* [Current modem-series target distinctions](https://github.com/Xinyuan-LilyGO/LilyGo-Modem-Series)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
