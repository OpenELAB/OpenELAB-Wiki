# Waveshare Jetson Orin NX 16GB Dev Kit Development Guide

{% hint style="info" %}
[**View Waveshare Jetson Orin NX 16GB Dev Kit on OpenELAB**](https://openelab.io/products/jetson-orin-nx-dev-kit-16gb)

**Product model/family:** Waveshare Jetson Orin NX 16GB Dev Kit · **OpenELAB SKU:** `Waveshare-24212`
{% endhint %}

![Waveshare Jetson Orin NX 16GB Dev Kit Development Guide](../../.gitbook/assets/jetson-orin-nx-16gb-waveshare-development-guide.webp)

_Product image: OpenELAB._ [_Image source_](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/01_jetson_orin_nx_devkit_16gb_angle.webp?v=1781147734)_._

[Product at OpenELAB](https://openelab.io/products/jetson-orin-nx-dev-kit-16gb) · [Manufacturer wiki hub](./)

## Product identity and kit selection

This guide covers the **Waveshare Jetson Orin NX 16 GB Dev Kit**, including OpenELAB **Waveshare-24212** and the related **24291 Dev Kit B** configuration. This is a Waveshare carrier-board kit, not NVIDIA's AGX Orin developer kit. Typical applications are edge vision, robot perception and Jetson application development.

**Memory and storage:** the 16 GB figure describes **LPDDR5 RAM**. The manufacturer states that the Orin NX module has no built-in storage; the documented Dev Kit configuration adds a **256 GB NVMe SSD**. Use these separate specifications when selecting a system image and planning datasets.

## Hardware and revision scope

| Item                | Documented kit                                                                            |
| ------------------- | ----------------------------------------------------------------------------------------- |
| Compute             | NVIDIA Orin NX 16 GB, eight-core Arm CPU and Ampere GPU                                   |
| Original AI maximum | Up to 100 TOPS; Super modes require supported upgrade/power/cooling configuration         |
| System storage      | External NVMe; documented Dev Kit includes 256 GB SSD                                     |
| Expansion           | Display, USB, Ethernet, M.2 and camera interfaces through the fitted Waveshare carrier    |
| Cooling             | Kit heatsink/fan; retain its cooling arrangement for first use                            |
| Dev Kit B           | Manufacturer B package adds camera/display accessories; confirm the actual order contents |

Sources: [manufacturer kit page](https://www.waveshare.com/jetson-orin-nx-16g-dev-kit.htm), [manufacturer setup wiki](https://www.waveshare.com/wiki/JETSON-ORIN-NX-16G-DEV-KIT). Current product information identifies JETSON-ORIN-IO-BASE; older wiki text references JETSON-IO-BASE-B. **Read the carrier label/revision on the received unit before choosing wiring, a display adapter or a flash procedure.** Do not resolve that documentation difference by guessing.

## First boot and a useful baseline

Prepare the correct manufacturer power supply, monitor/HDMI cable, keyboard and wired network. Attach peripherals while powered off, then apply power and finish the Linux first-run setup. Start with the installed image if it boots; reflashing is a recovery or version-management operation and can overwrite the system disk.

On the **Jetson**, open a terminal and capture a baseline:

```bash
cat /etc/nv_tegra_release
uname -a
lsblk -o NAME,SIZE,TYPE,MOUNTPOINTS
ip -brief address
dpkg-query -W nvidia-jetpack
sudo nvpmodel -q
tegrastats --interval 1000
```

Stop the last command with **Ctrl+C** after several readings. Expected checkpoints are a readable L4T release, an NVMe root filesystem, a network interface/address, a reported power mode and changing memory/CPU/temperature statistics. The `nvidia-jetpack` meta-package may be absent on a minimal image; that result alone does not prove the BSP or CUDA is missing. Keep this output with the exact image identifier before installing project software.

Do not use a desktop-PC CUDA installer or an arbitrary x86 container. Select Jetson/aarch64 packages and containers that explicitly match the installed JetPack/L4T release. Begin with a small camera or inference example from that release before adding multiple streams. The commands above establish platform visibility, not an inference-performance benchmark.

Sources: [NVIDIA Jetson Linux developer guide](https://docs.nvidia.com/jetson/archives/r36.4.3/DeveloperGuide/), [tegrastats reference](https://docs.nvidia.com/jetson/archives/r36.4.3/DeveloperGuide/AT/JetsonLinuxDevelopmentTools/TegrastatsUtility.html).

## Getting the correct BSP and restoring the system

Start from the working factory image if available. Back up files and record the carrier label, NX 16 GB module, installed NVMe, JetPack/L4T release and power supply before changing firmware. Match the [Waveshare flashing/upgrade guide](https://www.waveshare.com/wiki/JETSON-ORIN-NX-16G-DEV-KIT) to that carrier revision and supported image.

Use the guide's exact force-recovery connection and an Ubuntu host version supported by the selected NVIDIA/board release. An Orin NX production module is not flashed like an SD-card-based Nano developer kit. Confirm the host detects the recovery device before running the board-specific flash procedure; select external NVMe as directed by that package.

Treat a Super upgrade as a deliberate platform change with matching BSP, power mode and cooling. Do not publish a higher TOPS value as the observed performance of an unmodified unit. After any restore/upgrade, repeat the baseline and verify one camera/inference workload before adding other packages.

## Technical integration and troubleshooting

| Symptom or question                       | Check and next action                                                                                           |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Where is the “16 GB storage”?             | It is system RAM; inspect the NVMe device for operating-system/data storage.                                    |
| A carrier drawing disagrees with the unit | Record the physical board label/revision and use its specific resources before wiring or flashing.              |
| Blank monitor                             | Actual carrier display interface, correct DP/HDMI adapter, monitor input and normal boot versus recovery state. |
| Camera not detected                       | Exact sensor, cable orientation and supported driver/BSP. Add one camera at a time.                             |
| SDK installation fails                    | Host-versus-target distinction, JetPack/L4T release, aarch64 packages and external storage configuration.       |
| Need B-kit accessories                    | Verify the selected SKU/order; a shared store page does not mean every variant includes a camera and screen.    |

## Technical documents and software

| Resource                                                                                                 | Use                                               |
| -------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| [Manufacturer kit and package matrix](https://www.waveshare.com/jetson-orin-nx-16g-dev-kit.htm)          | Memory, NVMe and variant contents                 |
| [Board setup/flashing wiki](https://www.waveshare.com/wiki/JETSON-ORIN-NX-16G-DEV-KIT)                   | Carrier-dependent image, recovery and upgrade     |
| [Orin NX module datasheet](https://files.waveshare.com/wiki/common/Jetson_Orin_NX_DS-10712-001_v1.0.pdf) | Module-level electrical/mechanical specifications |
| [JetPack SDK](https://developer.nvidia.com/embedded/jetpack)                                             | Matched NVIDIA tools and libraries                |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/JETSON-ORIN-NX-16G-DEV-KIT) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
