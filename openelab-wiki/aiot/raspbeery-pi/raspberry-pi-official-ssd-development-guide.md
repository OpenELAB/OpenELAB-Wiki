---
description: >-
  Install the Raspberry Pi 1 TB M.2 2230 NVMe SSD (Waveshare-32467), verify
  adapter and capacity, configure Pi 5 boot and check a bounded filesystem
  result.
---

# Raspberry Pi Official SSD Integration Guide

{% hint style="info" %}
[**View Waveshare Official Raspberry Pi SSD on OpenELAB**](https://openelab.io/products/waveshare-official-raspberry-pi-ssd?variant=46885207572678)

**Model / option:** 1TB · **SKU:** `Waveshare-32467`
{% endhint %}

## Product overview

The **Raspberry Pi official SSD, sold as Waveshare-32467**, is the **1TB M.2 2230 NVMe drive**. It is a storage device, not a complete Raspberry Pi SSD Kit: the Pi, compatible M.2 adapter/HAT, cable, power supply and enclosure are separate unless the order explicitly includes them.

### Product and scope

The exact 1TB option is selected by the OpenELAB product link above. Check the ordered option and physical drive label before installation;256GB and512GB drives share the product family but provide different capacity and performance figures.

For a Raspberry Pi 5, use a compatible **PCIe-to-M.2 NVMe adapter** such as M.2 HAT+ or HAT+ Compact. An M.2 SATA socket or a camera/display FFC connector is not equivalent. [Raspberry Pi SSD specification](https://www.raspberrypi.com/products/ssd/).

## Applications

* Raspberry Pi 5 system storage and boot media after a verified OS installation and boot-order change.
* Local databases, source trees and application files that benefit from a random-I/O-oriented storage path.
* Data logging or media/model storage where capacity, free space, temperature and clean shutdown are monitored.
* An NVMe learning platform for identifying devices, checking health and separating filesystem verification from performance testing.

Keep an independent backup of valuable data. Storage capacity or an apparently successful boot does not establish recovery from power loss, endurance for a particular workload or a guaranteed application throughput.

## Specifications

| Parameter                       | Assigned 1TB drive                                                                                                         |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Capacity                        | 1TB decimal; OS display is approximately 931GiB before partition/filesystem overhead                                       |
| Form factor                     | M.2 2230, nominal 22 × 30mm                                                                                                |
| Interface                       | PCIe Gen3 compliant NVMe, not SATA                                                                                         |
| Command/register set            | NVMe 1.4                                                                                                                   |
| Manufacturer random-I/O figures | 90k IOPS for 4kB random reads and 90k for 4kB random writes                                                                |
| Ambient operating temperature   | 0–70°C in the November2026 product brief                                                                                   |
| Board physical drawing          | 0.8mm PCB and maximum1.35mm component-height dimension shown in the official drawing; use the actual drawing for clearance |
| Raspberry Pi 5 link baseline    | PCIe Gen2 ×1 at5GT/s by default                                                                                            |
| Host power                      | Through the compatible adapter's regulated M.2 supply; no direct USB/DC input on this bare SSD                             |

Sources: [Raspberry Pi SSD product brief](https://datasheets.raspberrypi.com/ssd/raspberry-pi-ssd-product-brief.pdf), specification page2 and physical drawing page3; [Pi PCIe documentation](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#pcie). The IOPS figures are manufacturer references, not measurements on this Pi/adapter/filesystem. A Gen3-compliant drive does not make the Pi 5's link a certified Gen3 path.

The family also has256GB/512GB models with different IOPS figures. They are not the assigned32467 capacity. Do not use a256GB screenshot as evidence of the received1TB drive's identity.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Fit and power before first boot

1. Shut down the Pi, disconnect external power and wait for the system to stop. Do not install/remove an M.2 drive or its PCIe FFC while energized.
2. Confirm the adapter supports **M-Key NVMe and2230 retention**. Inspect the SSD connector/key, mounting position and standoff so the PCB lies flat without bending.
3. Insert the SSD into the adapter according to its guide, then secure it with the matching retention hardware. Do not force an M.2 SATA carrier or over-tighten a screw through the board.
4. Connect the Pi5 **PCIe FFC** to the adapter with the correct cable/contact orientation. The Pi's CSI/DSI connectors do not carry this storage link.
5. Check cooler, case, cable and component clearance against the official SSD drawing and the adapter assembly. Keep ventilation around both host and drive.
6. Restore power using a supply suitable for the Pi and the adapter/peripheral load. Do not apply5V/12V directly to the SSD's edge contacts.

The [official NVMe boot guide](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#nvme-ssd-boot) recommends a supported adapter. Its adapter-specific cable, power and standoff instructions are part of the installation; the SSD itself has no general-purpose GPIO pinout.

### PCIe enablement versus boot enablement

A HAT+ device can be detected automatically. With a non-HAT+ adapter, the Pi documentation may require `dtparam=pciex1` in `/boot/firmware/config.txt`, followed by a reboot. That enables the operating-system PCIe path. Booting through a **non-HAT+ adapter additionally requires `PCIE_PROBE=1` in the EEPROM configuration**, as well as an NVMe-enabled `BOOT_ORDER`. These are three separate settings: Linux PCIe enablement, bootloader PCIe probing, and boot priority. The `raspi-config` boot-order menu changes `BOOT_ORDER`; it does not set `PCIE_PROBE`.

Begin at the default Gen2 speed. The official documentation warns that Pi5 is not certified for Gen3 and that enabling Gen3 may be unstable. If a later speed experiment produces link/I/O errors, restore the supported baseline before blaming the SSD. [PCIe configuration and speed conditions](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#pcie).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

No product-specific compiler target, firmware SDK or Arduino library applies to the bare SSD. Use the Linux NVMe/block-storage stack and a supported Raspberry Pi OS/bootloader. Record the Pi model, EEPROM version, OS/kernel and exact adapter/cable with the drive.

| Tool/resource                   | Purpose                                                                         |
| ------------------------------- | ------------------------------------------------------------------------------- |
| Raspberry Pi Imager             | Install a supported OS to the deliberately selected destination                 |
| `lsblk`, `findmnt`, kernel logs | Identify the namespace, partitions, current root filesystem and link errors     |
| `raspi-config`                  | Supported boot-order configuration route                                        |
| `rpi-eeprom-config`             | Inspect actual EEPROM settings; avoid arbitrary copied BOOT\_ORDER strings      |
| Optional `nvme-cli`             | Read controller identity and SMART/health information on a supported Linux host |
| Python3                         | Run the original small filesystem round-trip example below                      |

The drive firmware is not a Pi system image. Do not run a generic controller firmware updater or a low-level `nvme format` operation as a routine setup step. The manufacturer brief provides product/physical specifications; a public SSD circuit schematic or custom drive-firmware development SDK is not part of the reviewed offering.

## Getting started

### Identify the drive without modifying it

1. Boot the Pi from a known-good microSD or other existing system with the SSD installed. Confirm the adapter is powered and its PCIe configuration is appropriate.
2. Inspect block devices and the current root mount:

```bash
lsblk -o NAME,MODEL,SIZE,TYPE,FSTYPE,MOUNTPOINTS
ls -l /dev/nvme*
findmnt /
sudo dmesg | tail -80
```

3. Match the **drive label, model and1TB capacity**. The NVMe controller commonly appears as `/dev/nvme0` and its block namespace as `/dev/nvme0n1`; actual enumeration can differ. Do not use those example names as permission to format a device.
4. Record existing partitions/mounts before creating any. A blank drive can enumerate correctly without a filesystem.

**Expected result:** a readable NVMe controller/namespace with the correct capacity and no repeated link resets or I/O errors. Approximately931GiB is consistent with1TB decimal capacity; a256GB/512GB result is a different device/option, not filesystem overhead.

### Install an OS and prove NVMe boot

1. Back up any existing drive data. In Raspberry Pi Imager select the actual Pi model, a supported OS and the SSD destination identified by capacity/model. Installing an image erases the selected destination; keep the known-good recovery card available.
2. Configure the intended local account/network using Imager, complete the write and verification, and shut down before changing media/cables.
3. From a working Pi OS, run `sudo raspi-config`, choose **Advanced Options → Boot Order**, and select an option that includes NVMe in the intended priority. The official boot mode is **6**; EEPROM order is interpreted from the least-significant/rightmost entry.
4. **For a non-HAT+ adapter**, run `sudo rpi-eeprom-config --edit`. Preserve the intended NVMe-enabled `BOOT_ORDER` and add `PCIE_PROBE=1`. Save and reboot to apply the EEPROM update. A HAT+ adapter does not require this additional non-HAT+ probing step. [Official PCIe boot requirements](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#pcie).
5. Inspect the applied EEPROM settings with `sudo rpi-eeprom-config`; for non-HAT+ boot, confirm `PCIE_PROBE=1` separately from `BOOT_ORDER`. Reboot with the intended media arrangement and inspect `findmnt /` and `lsblk` again. A drive appearing in `/dev` after an SD boot does not prove the bootloader can probe it or that Linux root is on it.
6. Record the observed root mount, bootloader/OS versions and boot behavior with/without the recovery card.

The [official boot guide](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#nvme-ssd-boot) covers Pi5 as well as distinct CM4/CM5 cases. Do not apply a CM4 `rpiboot` instruction or a USB-mass-storage boot mode to a Pi5 direct-PCIe setup without its matching context.

**Expected result:** Linux's root filesystem resolves to the intended NVMe partition after a normal reboot. Keep a known-good SD recovery path until this is repeatable.

### Original small file-integrity checkpoint

Choose an existing mounted directory **on the SSD** and verify it first with `findmnt -T /your/ssd/directory`. The script below creates a temporary64KiBfile in that directory, flushes it, rereads it and removes its temporary directory. It does not partition, format or write the raw namespace. Save as `ssd_roundtrip.py`:

```python
import hashlib
import os
from pathlib import Path
import sys
import tempfile

mount_directory = Path(sys.argv[1]).resolve(strict=True)
if not mount_directory.is_dir():
    raise SystemExit("Pass an existing mounted SSD directory")
payload = os.urandom(65536)
expected = hashlib.sha256(payload).hexdigest()
with tempfile.TemporaryDirectory(prefix="ssd-check-", dir=mount_directory) as temp:
    path = Path(temp) / "roundtrip.bin"
    with path.open("wb") as stream:
        stream.write(payload)
        stream.flush()
        os.fsync(stream.fileno())
    observed = hashlib.sha256(path.read_bytes()).hexdigest()
    print("bytes:", len(payload))
    print("sha256 match:", expected == observed)
    if observed != expected:
        raise SystemExit("Read/write mismatch: stop and inspect storage logs")
```

```bash
findmnt -T /your/ssd/directory
python3 ssd_roundtrip.py /your/ssd/directory
```

**Expected result:** `bytes:65536` and `sha256 match:True`, with no new kernel I/O errors. This is a filesystem-path sanity check, not a destructive surface test, endurance test, uncached read benchmark or proof that all flash cells were tested.

### Health, thermal and maintenance checks

If using `nvme-cli`, read controller identity and health on the actual controller, for example `sudo nvme id-ctrl /dev/nvme0` and `sudo nvme smart-log /dev/nvme0`. Record temperature, critical warnings and error counters before/after your workload; do not present the manufacturer's90kIOPS as your measured result.

Leave free space for logs/updates and confirm the OS's supported filesystem maintenance/TRIM configuration. Do not schedule an aggressive raw-disk write benchmark on a system with valuable data. Use clean shutdown before removing power, and keep backup/recovery separate from a single successful file checksum.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                      | Ordered checks and recovery                                                                                                     |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| No `/dev/nvme*`              | Adapter is NVMe/M-Key compatible, SSD retention, PCIe FFC contact orientation, adapter power, then PCIe enablement              |
| Drive visible but no boot    | Valid OS/boot partition, correct EEPROM boot order including mode6, actual boot medium and supported image                      |
| Root still on microSD        | Inspect `findmnt /`; adjust the intended boot order/media after verifying the SSD OS is complete                                |
| Repeated PCIe/AER/I/O errors | Restore default Gen2, inspect cable/seating/power and thermal conditions; avoid repeated writes until stable                    |
| Capacity around931GiB        | Consistent with1TB decimal; inspect partitions separately for usable filesystem space                                           |
| Capacity256/512GB            | Recheck physical drive/selected option; this is not normal overhead for the assigned1TB SKU                                     |
| Slow workload                | Measure the actual pipeline, link speed, thermal state, free space and competing I/O; avoid conflating IOPS with sequentialMB/s |
| Mount/filesystem fails       | Preserve data and logs; do not start by formatting or running repair on a mounted filesystem                                    |
| Wrong destination imaged     | Stop further writes and use the independent backup/recovery plan; a new image does not preserve old files                       |

For a drive visible after SD boot but skipped at power-on, inspect `BOOT_ORDER` and, specifically for a non-HAT+ adapter, applied `PCIE_PROBE=1`; also check Linux-side `dtparam=pciex1` where required. The boot-order menu alone does not enable non-HAT+ probing. Use a known-good card, inspect kernel logs and return to the last working adapter/link configuration. The Pi bootloader repository is an official support resource, but this guide does not submit logs or contact anyone.

## Downloads and technical documents

The product brief was downloaded and its physical drawing visually inspected. Use page3's actual outline/height callouts for enclosure work. The SSD has no separate user-wiring schematic or firmware SDK; the adapter's own installation/electrical documentation supplies the missing host-specific details.

| Resource                                                                                                 | Purpose and exact scope                                  |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| [SSDproductbrief](https://datasheets.raspberrypi.com/ssd/raspberry-pi-ssd-product-brief.pdf)             | DownloadedNovember2026specificationsandmechanicaldrawing |
| [OfficialNVMe boot](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#nvme-ssd-boot) | Hostcompatibility,discoveryandbootorder                  |
| [OfficialPCIeguide](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#pcie)          | AdapterenablementandGen2/Gen3conditions                  |
| [RaspberryPiImager](https://www.raspberrypi.com/software/)                                               | OfficialhostOSinstallationtool                           |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November2026**: exact global-store32467/1TBvariant, the November2026 Raspberry Pi SSD product brief and official NVMe/PCIe documentation source. The original bounded file round-trip procedure is separate from performance and endurance testing.

**OS installation, boot-order changes, file-test execution, SMART queries and hardware measurements: not run.**

* [Raspberry Pi SSD1TB specifications and mechanical drawing](https://datasheets.raspberrypi.com/ssd/raspberry-pi-ssd-product-brief.pdf) — November2026 product brief.
* [Official NVMe discovery and boot-order procedure](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#nvme-ssd-boot) — current official documentation source downloaded24Nov2026.
* [Official Pi5 PCIe enablement/speed and adapter conditions](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#pcie) — current official documentation source downloaded24Nov2026.
* [Observed global-store SKU32467/1TB](https://openelab.io/products/waveshare-official-raspberry-pi-ssd?variant=46885207572678) — publicpage reviewed24Nov2026.

### Retained source links

* [Waveshare-32467](https://openelab.de/products/waveshare-official-raspberry-pi-ssd)

### Related retained references

* [Raspberry Pi official documentation](https://www.raspberrypi.com/documentation/)
