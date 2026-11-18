# M5Stack Core2 v1.3 K010-V13 Development Guide

[Product at OpenELAB](https://openelab.io/products/m5stack-core2-esp32-v1-3)

### Product and revision

This page covers **K010-V13, Core2 v1.3**. It is an ESP32 touch controller for dashboards, sensor logging and interactive devices. Earlier Core2, Core2 v1.1 and CoreS3 guides do not establish exact v1.3 peripheral support.

| Item             | v1.3 specification                                 |
| ---------------- | -------------------------------------------------- |
| MCU              | ESP32-D0WDQ6-V3, dual-core LX6 up to 240MHz        |
| Memory           | 16MB flash, 8MB PSRAM                              |
| Wireless         | 2.4GHz Wi-Fi                                       |
| User interface   | 2-inch capacitive-touch color display              |
| Power management | AXP192                                             |
| Bottom-board IMU | BMI270                                             |
| Software         | M5Unified; model-specific Arduino/PlatformIO setup |

The **BMI270** differs from earlier Core2 motion-sensor examples. Use the current library's supported API and the v1.3 schematic.

### First program

1. Begin with the supplied unit and no stacked expansion module. Connect a USB data cable.
2. Follow the v1.3 Arduino setup or use the manufacturer's PlatformIO reference, which identifies **espressif32 6.12.0**, board **m5stack-core2**, and **default\_16MB.csv** partitions.
3. Install M5Unified and open its basic display example.
4. Build/upload, reset and verify the display output. Then test touch and IMU separately.
5. Record the working dependency versions; the reference platform version alone does not pin the library.

**Expected result:** a visible screen update and reliable restart. A new display test is more useful than flashing a complex network demo before basic hardware is verified.

### Electrical integration and drawings

Use the product's **Core Section** and **Bottom Section** schematics and pin table. The manufacturer warns **not to stack Core2 v1.3 with Base-series expansion bases**. When using M5 modules, follow its instructions concerning removal or replacement of the battery bottom; do not stack solely because the connector fits.

### Recovery and FAQs

Restore using the model's official factory firmware if a custom application fails. Confirm the selected serial port, USB cable and upload mode before erasing flash.

**Older IMU code reports no device?** Check for a BMI270-compatible library.

**A stack no longer reads microphone/IMU data?** Verify which bottom board is fitted and the shared signals in the v1.3 schematic.

**Can an ESP32-S3 board target be used?** Core2 uses an ESP32 LX6 processor. Select the actual Core2 target.

### Sources and validation

* [Core2 v1.3 hardware and software reference](https://docs.m5stack.com/en/core/Core2_v1.3)
* [Core and bottom schematics, pinouts and dimensions](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/static/pdf/static/en/core/Core2_v1.3.pdf)
* [M5Unified library](https://github.com/m5stack/M5Unified)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
