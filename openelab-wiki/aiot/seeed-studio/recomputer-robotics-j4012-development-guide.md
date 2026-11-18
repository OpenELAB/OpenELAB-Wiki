# Seeed Studio reComputer Robotics J4012 Development Guide

{% hint style="info" %}
[**View Seeed Studio reComputer Robotics J4012 on OpenELAB**](https://openelab.io/products/seeedstudio-recomputer-robotics-j4012-intelligent)

**Product model/family:** Seeed Studio reComputer Robotics J4012 · **OpenELAB SKUs:** `Seeed-114110310`, `Seeed-100026552` · Verify each ordered model/kit option against the instructions below.
{% endhint %}

![Seeed Studio reComputer Robotics J4012 Development Guide](../../.gitbook/assets/recomputer-robotics-j4012-development-guide.jpg)

_Manufacturer image: Seeed Studio._ [_Image source_](https://media-cdn.seeedstudio.com/media/catalog/product/cache/bb49d3ec4ee05b6f018e93f896b8a25d/1/-/1-114110310-recomputer-robotics_2.jpg)_._

[Product at OpenELAB](https://openelab.io/products/seeedstudio-recomputer-robotics-j4012-intelligent) · [Manufacturer wiki hub](./)

## Product and variant scope

**reComputer Robotics J4012** combines Orin NX 16 GB with Seeed's Robotics J401 carrier for robot perception and control integration. This guide covers the base configuration **114110310** and the same carrier sold with optional **GMSL expansion**. That expansion and its supported cameras require a corresponding driver/image; the base system must not be assumed to include it.

## Hardware specifications

| Item          | Robotics J4012                                                 |
| ------------- | -------------------------------------------------------------- |
| Module        | Jetson Orin NX 16 GB                                           |
| Storage       | M.2 Key M NVMe, documented 128 GB configuration                |
| Ethernet      | Two Gigabit RJ45 ports                                         |
| USB           | Six USB 3.2 Type-A; USB-C host/DP; separate USB-C device/debug |
| Display       | DP 1.4 through the documented USB-C host connector             |
| Robot I/O     | CAN0/CAN1, UART and I2C headers                                |
| Camera option | GMSL2 expansion board and matching camera/serializer support   |
| Input         | 19–54 V XT30(2+2) carrier reference                            |
| Envelope      | 115 × 115 × 38 mm                                              |

Several physical connectors share the same CAN bus. Do not count every connector as an independent channel. Sources: [Robotics J401 setup](https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/), [carrier datasheet](https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer_robotics_J401_datasheet.pdf).

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

## Camera, CAN and power integration

For the first video check, use one supported camera and its stock driver/example. With GMSL, match the fitted extension, camera sensor, serializer, cable and power-over-coax arrangement to the release's supported configuration. A Mini-Fakra connector is not sufficient evidence of camera compatibility.

Read the XT30 power/signal drawing and header tables before connecting a robot battery or CAN bus. Use the supported transceiver/termination configuration and distinguish the two bus identities. First inspect feedback/interface errors without sending arbitrary control traffic to a connected robot.

## Firmware recovery and software

Select **Robotics J401 / Orin NX 16 GB** and the **fitted GMSL option** in the manufacturer image matrix. Back up data, use its specified Ubuntu host and follow the REC-switch/USB procedure for this carrier. A Super J4012 or original J401 image is not the correct default just because the module name matches.

Complete the vendor flash procedure and return recovery controls to normal operation. Recheck boot, storage, network and cameras before installing Isaac ROS, ROS or inference packages. Keep their versions compatible with the actual JetPack/L4T release and selected image.

## Troubleshooting and FAQ

| Symptom                                  | Check                                                                                                              |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| USB-C connection gives no monitor output | Correct host/DP-capable port, supported adapter/cable and display input; the debug connector has a different role. |
| GMSL hardware present but no camera      | Exact extension/sensor driver, cable/POC and GMSL-enabled image.                                                   |
| CAN traffic appears on another connector | Connectors can share a bus; compare against CAN0/CAN1 mapping in the datasheet.                                    |
| System resets under workload             | Correct supply, XT30 seating, cooling and power-mode configuration.                                                |
| After flashing, interfaces are missing   | Verify Robotics carrier/module/optional-GMSL image rather than another J4012 family.                               |

## Technical documents and software

| Resource                                                                                                           | Use                                     |
| ------------------------------------------------------------------------------------------------------------------ | --------------------------------------- |
| [Robotics J401 setup and images](https://wiki.seeedstudio.com/recomputer_robotics_j401_getting_started/)           | Exact model, recovery and image matrix  |
| [Carrier datasheet](https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer_robotics_J401_datasheet.pdf)   | Power, CAN and connector mapping        |
| [Schematic](https://files.seeedstudio.com/products/NVIDIA-Jetson/reComputer%20Robotics%20J401_V1.0_SCH_250421.pdf) | J401 Robotics v1.0 electrical reference |
| [Mechanical STEP](https://files.seeedstudio.com/products/NVIDIA-Jetson/recomputer_robotics_j401.stp)               | Mechanical integration                  |
| [GMSL camera guide](https://wiki.seeedstudio.com/sensing_gmsl_cameras/)                                            | Supported camera and extension workflow |
| [JetPack SDK](https://developer.nvidia.com/embedded/jetpack)                                                       | Matched Jetson software components      |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
