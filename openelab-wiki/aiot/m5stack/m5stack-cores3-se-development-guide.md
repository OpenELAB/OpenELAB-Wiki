# M5Stack CoreS3-SE K128-SE Development Guide

[Product at OpenELAB](https://openelab.io/products/m5stack-cores3-se-iot-controller-w-o-battery-bottom) · [M5Stack hub](./)

### Product and scope

**K128-SE** is the CoreS3-SE controller, not a full CoreS3 package with its battery base and other peripherals. It is useful for touch dashboards, audio interfaces and embedded Wi-Fi prototypes. Check the manufacturer's family comparison before reusing camera or motion examples.

| Item          | CoreS3-SE                                                                      |
| ------------- | ------------------------------------------------------------------------------ |
| MCU           | ESP32-S3, dual-core Xtensa LX7 up to 240MHz                                    |
| Memory        | 16MB flash, 8MB PSRAM                                                          |
| Display       | 2-inch capacitive-touch IPS                                                    |
| Audio         | Dual microphones; ES7210 input codec and AW88298 output amplifier with speaker |
| Power / clock | AXP2101 PMU / BM8563 RTC                                                       |
| Expansion     | microSD and model-specific headers                                             |
| USB           | USB-C with CDC and OTG functions                                               |

The product page links the **schematics, pin map and dimensional resources**. Check the exact SE hardware map before attaching a module.

### Getting started: local display test

1. Connect USB-C power/data and install the Arduino/M5Stack environment referenced by the product page.
2. Install **M5Unified** and its required graphics dependencies. Select the board settings documented for CoreS3-SE.
3. Open the library's basic display example. Build and upload it without external modules attached.
4. Confirm a visible screen update and touch response using the corresponding example.
5. Save the working sketch, board package version and library versions before adding audio or networking.

**Checkpoint:** a repeatable display update after reset. Establish this before diagnosing wireless or external peripheral code.

### Software and recovery

M5Unified supplies the common controller API; Arduino and UiFlow paths have separate setup instructions. Use the model's official factory-firmware/download route for restoration.

If uploads fail, use the documented reset-button download-mode procedure and reconnect to the newly enumerated port. A charge-only cable will supply power without allowing uploads.

### FAQs

**Can I run every CoreS3 demo unchanged?** Confirm the peripheral exists in the SE and its pin/driver requirements first.

**Black screen after a successful upload?** Check board selection, PMU/display initialization, power and graphics-library compatibility.

**Can I assume a battery is installed?** No. Verify the actual package and base.

**Audio is silent?** Test input and output independently, verify the selected codec path and start at low output volume.

### Sources and validation

* [CoreS3-SE hardware, schematics and examples](https://docs.m5stack.com/en/core/CoreS3-SE)
* [M5Unified source and examples](https://github.com/m5stack/M5Unified)
* [CoreS3 family comparison](https://docs.m5stack.com/en/core/CoreS3)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
