# Raspberry Pi Official SSD Integration Guide

{% hint style="info" %}
[**View Waveshare Official Raspberry Pi SSD on OpenELAB**](https://openelab.io/products/waveshare-official-raspberry-pi-ssd)

**Product:** Raspberry Pi SSD, M.2 2230 NVMe · **OpenELAB SKU:** `Waveshare-32467` · **Variant:** 1 TB capacity. Raspberry Pi 5 requires a compatible M.2 HAT or carrier (sold separately); this is a storage device and needs no separate firmware SDK.
{% endhint %}

[Waveshare-32467](https://openelab.de/products/waveshare-official-raspberry-pi-ssd)

## Product and scope

This guide covers the **official Raspberry Pi NVMe SSD**, sold under the OpenELAB/Waveshare **32467** listing. Verify capacity from the ordered variant and drive label. The SSD is separate from an M.2 adapter or complete HAT/drive kit.

## Hardware and technical documents

| Item                | Reference                                               |
| ------------------- | ------------------------------------------------------- |
| Form factor         | M.2 2230                                                |
| Interface           | PCIe Gen3-compliant NVMe                                |
| Command set         | NVMe 1.4                                                |
| Official capacities | 256GB / 512GB / 1TB family options; verify actual unit  |
| Raspberry Pi host   | Pi 5 requires a compatible M.2 adapter such as M.2 HAT+ |

Use the SSD **product brief** and the actual adapter's mechanical/power/FFC guide. An M.2 SATA adapter is not a substitute for NVMe. Power off before fitting the SSD and securing it with the correct standoff/screw.

## Getting started

1. Install the drive in a supported Pi 5 M.2 adapter with power disconnected.
2. Boot a supported Raspberry Pi OS using existing known-good media.
3. Inspect storage without modifying it using **lsblk -o NAME,MODEL,SIZE,TYPE,MOUNTPOINTS**.
4. Confirm the SSD identity/capacity and the adapter's link before creating partitions or installing an OS.
5. For SSD boot, follow Raspberry Pi's supported boot/storage workflow and carefully select the destination drive.

**Expected checkpoint:** the NVMe device appears with the expected model/capacity. Data migration and OS installation are separate steps that can erase the selected drive.

## Development software and recovery

No product-specific development SDK is required; use the OS NVMe/block-storage stack. Record bootloader/OS version and adapter model. Back up data before firmware, partition or boot-order changes.

## FAQs

**No drive detected?** Check adapter compatibility, FFC seating/orientation, power and host PCIe support.

**Advertised capacity differs from OS display?** Check decimal GB versus binary units and partition usage.

**Can it plug directly into the Pi board?** A compatible M.2 adapter is required.

## Sources and validation

* [Manufacturer specifications and product brief](https://www.raspberrypi.com/products/ssd/)
* [Raspberry Pi official documentation](https://www.raspberrypi.com/documentation/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
