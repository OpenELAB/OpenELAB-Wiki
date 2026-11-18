# Seeed Studio reCamera Pro 2GB Engineering Guide

[Seeed-100092895](https://openelab.io/products/seeed-studio-recamera-pro-2gb-open-ai-camera)

### Product and scope

This guide covers **Seeed-100092895, reCamera Pro 2GB** for local vision inference and event-driven camera applications. The original reCamera and current 4GB Pro packages have different hardware or memory scope; select binaries and models for the actual device.

### Hardware and technical documents

| Item             | Reference                                                                    |
| ---------------- | ---------------------------------------------------------------------------- |
| Processor        | RV1126B, quad-core Cortex-A53 up to 1.2GHz                                   |
| NPU              | 3 TOPS; mixed INT8/INT16 support                                             |
| Memory / storage | This listing: 2GB LPDDR4; Pro hardware reference: 16GB eMMC and SD expansion |
| Imaging          | SC850SL, 4K-capable imaging                                                  |
| Interfaces       | Ethernet, USB-C, debug UART, CAN and expansion interfaces                    |
| Power            | Manufacturer Pro reference: 12–24V DC input and supported PoE path           |

Use the **Pro hardware-specification diagrams** for connector orientation and signal levels. Processor/NPU capability is distinct from a model's measured throughput. The official image and an alternative OS may expose different features.

### Getting started

1. Check the model and installed firmware. Boot using the documented Pro power/USB connection.
2. Follow the official first-detection guide to reach the Web UI. The factory USB virtual-network path uses **192.168.42.1** when supported.
3. Complete initial setup, inspect the live camera preview and aim/focus for the intended working distance.
4. Enable a supported built-in detection model and observe detections against a simple scene.
5. Save a short result sample, selected model, input resolution and firmware version.

**Expected checkpoint:** a live image and plausible detection results in the browser before custom model/API work.

### Development software and recovery

Use the Pro **development-path selector**, API documentation and Downloads/Release Notes. Select model conversion and native application tools for RV1126B. Preserve firmware, model and application versions. Follow the Pro recovery procedure before replacing the OS; the official documentation notes that alternative software can remove the original USB-network interface or Bluetooth support.

### FAQs

**Cannot reach the factory address?** Check firmware type, USB data capability and host network adapter; try the documented Ethernet/Wi-Fi path.

**A model loads but runs slowly?** Check supported operators, compiled target, input size and available memory.

**Is a 4GB image/package identical?** Confirm supported firmware and memory requirements rather than inferring from the Pro name.

### Sources and validation

* [First detection](https://wiki.seeedstudio.com/recamera_pro_getting_started/)
* [Hardware specifications](https://wiki.seeedstudio.com/recamera_pro_hardware_specifications/)
* [Choose a development path](https://wiki.seeedstudio.com/recamera_pro_dev_path/)
* [Firmware and SDK downloads](https://wiki.seeedstudio.com/recamera_pro_downloads/)
* [Network access](https://wiki.seeedstudio.com/recamera_pro_wifi_access/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
