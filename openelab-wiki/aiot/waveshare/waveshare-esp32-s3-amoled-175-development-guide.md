# Waveshare ESP32-S3 Touch AMOLED 1.75 Engineering Guide

[Waveshare-31264](https://openelab.io/products/waveshare-esp32-s3-amoled-touch-display) · [Waveshare-31262](https://openelab.io/products/waveshare-esp32-s3-amoled-touch-display) · [Waveshare-31261](https://openelab.io/products/waveshare-esp32-s3-amoled-touch-display)

### Product and scope

The **1.75-inch AMOLED** family supports portable interfaces, audio and sensor prototypes. Some store titles say GPS for the whole family, but **only 31264 (-G) contains the documented GNSS hardware**.

### Hardware and technical documents

| Item            | Reference                                     |
| --------------- | --------------------------------------------- |
| 31261           | Standard board                                |
| 31262 (-B)      | Standard board with protective case           |
| 31264 (-G)      | LC76G GNSS version with antenna               |
| Display / touch | CO5300 QSPI, 466 × 466; CST9217               |
| Memory          | ESP32-S3R8, 8MB PSRAM, 16MB flash             |
| Peripherals     | AXP2101, QMI8658, PCF85063, audio and microSD |

The official **HARDWARE\_REFERENCE.md** contains the complete GPIO/I2C map and links to schematics. Audio MCLK is **GPIO42**, while GPIO16 is an expansion GPIO. On -G, GPIO17/18 may be routed to GNSS; check availability before adding UART devices.

### Getting started

1. Identify the printed SKU and preserve factory firmware details.
2. Open the official **waveshareteam/ESP32-S3-Touch-AMOLED-1.75** project and use its documented Arduino/ESP-IDF environment.
3. Select a basic display/touch example with the supplied BSP and PSRAM settings.
4. Build/upload and verify display geometry and touch coordinates.
5. Then test audio/storage/IMU. Test GNSS only on -G with a clear sky view.

**Expected checkpoint:** a stable display/touch baseline; GNSS capability is verified by hardware identity, not the listing title.

### Development software and recovery

The repository includes board-specific examples, release firmware and a complete factory recovery image. Record its commit/toolchain and retain BSP power/expander initialization. Use the documented recovery image and flashing offsets for restoration.

### FAQs

**No GPS on 31261 or 31262?** These are the standard configurations; -G is the documented GNSS variant.

**I2C peripherals disappear?** Initialize the shared bus once and use compatible clock settings.

**Audio fails with another screen's pin map?** Use this board's schematic/BSP; its codec and clocks are model-specific.

### Sources and validation

* [Official hardware map and exact SKU distinctions](https://github.com/waveshareteam/ESP32-S3-Touch-AMOLED-1.75/blob/main/HARDWARE_REFERENCE.md)
* [Examples, firmware and factory recovery](https://github.com/waveshareteam/ESP32-S3-Touch-AMOLED-1.75)
* [Manufacturer tutorial](https://www.waveshare.com/wiki/ESP32-S3-Touch-AMOLED-1.75)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
