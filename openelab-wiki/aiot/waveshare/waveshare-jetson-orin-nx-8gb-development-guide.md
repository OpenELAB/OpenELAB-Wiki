# Waveshare Jetson Orin NX 8GB Dev Kit Engineering Guide

{% hint style="info" %}
[**View Waveshare Jetson Orin NX 8GB Dev Kit on OpenELAB**](https://openelab.io/products/jetson-orin-nx-dev-kit-8gb)

**Product/variant:** Waveshare Jetson Orin NX 8GB Dev Kit · **OpenELAB SKU:** `Waveshare-24444`
{% endhint %}

[Waveshare-24444](https://openelab.io/products/jetson-orin-nx-dev-kit-8gb)

## Product and scope

**24444** is a Waveshare **Orin NX 8GB carrier-board kit** for edge AI and robotics. It is not NVIDIA's AGX Orin developer kit or the 16GB NX configuration. The store's eMMC wording must not be interpreted as onboard Orin NX storage.

## Hardware and technical documents

| Item         | Reference                                                                                        |
| ------------ | ------------------------------------------------------------------------------------------------ |
| Module       | Jetson Orin NX 8GB LPDDR5                                                                        |
| Storage      | Orin NX has no built-in storage; the documented kit uses an external 256GB NVMe SSD              |
| Carrier      | Verify fitted JETSON-ORIN-IO-BASE/revision before flashing                                       |
| AI reference | Original 8GB configuration up to 70 TOPS; supported Super upgrades change operating requirements |
| Kit options  | Cooling, wireless card, supply and camera/display accessories vary by package                    |

Use the 8GB kit's **carrier manual, schematic/resource links and mounting diagram**. Match the exact module/carrier combination when choosing BSP, recovery wiring and peripherals.

## Getting started

1. Keep the fitted cooling and use the supported supply. Attach monitor, keyboard and Ethernet while powered off.
2. Boot the delivered image and complete its initial setup.
3. Record **cat /etc/nv\_tegra\_release**, **free -h**, **lsblk** and **sudo nvpmodel -q**.
4. Verify storage capacity and the installed power mode before adding an application.
5. Use a supported small Jetson inference example and retain its container/model version.

**Expected checkpoint:** stable boot, correct 8GB-class memory identification and visible external storage.

## Development software and recovery

Use the Waveshare **8G-DEV-KIT** image/instructions. JetPack, carrier drivers, firmware and containers must be compatible. Back up data before flashing. Super performance requires a supported software, cooling and power configuration, not a renamed product label.

## FAQs

**Where is eMMC?** The NX module does not provide built-in system storage; inspect the fitted NVMe.

**Can a 16GB-kit image be assumed compatible?** Verify module/carrier support explicitly.

**Recovery fails?** Check the kit's recovery jumper/button sequence, USB data cable and supported host.

## Sources and validation

* [Manufacturer kit/module comparison](https://www.waveshare.com/jetson-orin-nx-16g-dev-kit.htm)
* [Exact 8GB setup wiki](https://www.waveshare.com/wiki/JETSON-ORIN-NX-8G-DEV-KIT)
* [Kit contents and image scope](https://www.waveshare.com/product/ai/boards-kits/jetson-orin-nx-16g-dev-kit.htm)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
