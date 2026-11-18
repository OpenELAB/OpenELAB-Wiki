# NVIDIA Jetson AGX Orin 64GB Developer Kit Engineering Guide

{% hint style="info" %}
[**View NVIDIA Jetson AGX Orin 64GB Developer Kit on OpenELAB**](https://openelab.io/products/waveshare-nvidia-jetson-agx-orin)

**Product model/family:** NVIDIA Jetson AGX Orin 64GB Developer Kit · **OpenELAB SKU:** `NVIDIA-AGX-64G`
{% endhint %}

[Product at OpenELAB](https://openelab.io/products/waveshare-nvidia-jetson-agx-orin) · [AIoT documentation](../aiot-wiki-home-page.md)

## Product and applications

The NVIDIA Jetson AGX Orin 64GB Developer Kit is a reference platform for GPU inference, multi-camera perception and robotics software development. This page covers OpenELAB **NVIDIA-AGX-64G**, rather than an Orin NX carrier kit or the earlier 32GB developer-kit package. Production deployment needs its own electrical, thermal and lifecycle assessment.

## Hardware reference

| Item               | 64GB developer kit                                                   |
| ------------------ | -------------------------------------------------------------------- |
| CPU / GPU          | 12-core Arm Cortex-A78AE; 2,048-core Ampere GPU with 64 Tensor Cores |
| Memory             | 64GB LPDDR5; 204.8GB/s bandwidth                                     |
| Built-in storage   | 64GB eMMC 5.1; external NVMe expansion                               |
| Advertised compute | Up to 275 INT8 TOPS; workload and power mode affect results          |
| Module power modes | 15–60W; distinguish module consumption from complete-system input    |
| Display            | DisplayPort; HDMI monitor requires a suitable active adapter         |
| Expansion          | 40-pin header, M.2, USB and camera connectors                        |
| Networking         | RJ45 up to 10GbE                                                     |

Use NVIDIA's **carrier-board specification** linked from Hardware Layout for connector pinouts, electrical limits and mechanical integration. The 40-pin connector is not evidence that arbitrary Raspberry Pi accessories are electrically compatible.

## Getting started: establish a reproducible baseline

1. Keep the fitted cooling system. With power disconnected, attach a DisplayPort monitor, USB keyboard/mouse and network.
2. Connect the included supply to the USB-C power-input port above the DC jack. The other USB-C port, near the 40-pin header, serves host/flashing functions.
3. Complete Ubuntu's initial user setup on the factory eMMC image. Confirm the desktop and network before changing firmware.
4. In a terminal, capture the installed platform information:

```bash
cat /etc/nv_tegra_release
uname -a
free -h
lsblk
sudo nvpmodel -q
```

**Expected checkpoint:** an NVIDIA L4T release is reported, memory and storage are visible, and the current power mode is identified. These commands inspect configuration; they do not benchmark AI throughput.

## Software and recovery

Use the JetPack release supported by the application and NVIDIA's current compatibility guidance. CUDA, TensorRT, camera drivers and containers must match the installed Jetson Linux generation. Save package versions and the image source before upgrades.

For a blank or damaged installation, follow NVIDIA's BSP installation flow, using its recovery-button sequence and the correct host USB-C port. Back up datasets and configuration first; flashing can erase storage. Recovery detection is separate from a working Ubuntu boot.

## FAQs

**No HDMI output?** The reference kit exposes DisplayPort. Check the monitor input and active adapter.

**A container starts but the GPU is unavailable?** Check that the image supports the installed L4T release and that the runtime was configured for Jetson.

**Can a 275-TOPS label predict my model's speed?** Measure the actual model, precision, input resolution, batch size, thermal state and power mode. Published peak compute is not an application latency guarantee.

## Sources and validation

* [NVIDIA current specifications](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson/back-to-school/)
* [AGX Orin kit quick start](https://docs.nvidia.com/jetson/agx-orin-devkit/user-guide/latest/quick_start.html)
* [Carrier layout and specification links](https://docs.nvidia.com/jetson/agx-orin-devkit/user-guide/latest/hardware-layout.html)
* [Jetson software and hardware downloads](https://developer.nvidia.com/embedded/learn/getting-started-jetson)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
