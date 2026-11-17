# M5Stack Dial v1.1 Development Guide

![M5Stack Dial v1.1 Development Guide](../../.gitbook/assets/dial-v11-development-guide.webp)

_Manufacturer image: M5Stack._ [_Image source_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1126/K130_v11_01.webp)_._

[Product at OpenELAB](https://openelab.io/products/m5stack-dial-v1-1) · [Manufacturer wiki hub](./)

### Product and applications

**M5Stack Dial v1.1, K130-V11**, is a rotary/touch control terminal for embedded dashboards, menu navigation, access-control prototypes and smart-home interfaces. It uses **Stamp-S3A** rather than the original Dial's StampS3. Match that revision when selecting enclosure files, firmware and power expectations.

### Hardware specifications and expansion

| Item         | Dial v1.1                                                                  |
| ------------ | -------------------------------------------------------------------------- |
| MCU/memory   | ESP32-S3FN8, dual-core up to 240 MHz; 8 MB flash                           |
| Display      | 1.28-inch 240 × 240 round TFT; GC9A01                                      |
| Touch        | FT3267                                                                     |
| Rotary input | 16 positions; 64 pulses per revolution                                     |
| RFID         | WS1850S, 13.56 MHz, ISO/IEC 14443 Type A/B                                 |
| Other        | RTC, buzzer and under-screen button                                        |
| Power        | USB-C 5 V; separate 6–36 V DC input and lithium-battery charging interface |
| Size         | 51.0 × 51.0 × 32.3 mm                                                      |

Source: [manufacturer model reference](https://docs.m5stack.com/en/core/Dial_v1.1). The 6–36 V range belongs to its **DC input**, not USB, battery, Grove power or GPIO. Confirm connector polarity and battery compatibility before using an alternative supply.

| HY2.0-4P port | Black | Red | Yellow | White  |
| ------------- | ----- | --- | ------ | ------ |
| PORT.A        | GND   | 5 V | GPIO13 | GPIO15 |
| PORT.B        | GND   | 5 V | GPIO2  | GPIO1  |

The red wire's 5 V supply does not establish 5 V GPIO tolerance. Use the pin map and schematic for signal functions and logic-level compatibility. The internal encoder uses GPIO41/A and GPIO40/B; let the model driver handle it for first-run tests.

### Development environment

Install Arduino IDE and the [M5Stack board package](https://docs.m5stack.com/en/arduino/arduino_board). The [official Arduino route](https://docs.m5stack.com/en/arduino/m5dial/program) selects **M5Dial** and installs the **M5Dial** library plus its M5Unified/M5GFX dependencies. Record their installed versions. UiFlow2 and the ESP-IDF BSP are alternative development paths with separate dependencies.

### Getting started: display and rotary count

Prepare a USB-C data cable and computer. Save needed factory configuration before replacing its application.

1. Hold the Stamp module's rear **G0** button while connecting USB-C, then release it to enter download mode.
2. Select **M5Dial** and the actual USB port. Begin with **M5Dial → Basic → display** to verify the model preset, upload and display path.
3. Open **M5Dial → Basic → encoder**. The official example initializes `M5Dial.begin(cfg, true, false)`, enabling the encoder while leaving RFID disabled, then calls `M5Dial.update()` and reads `M5Dial.Encoder.read()`.
4. Upload, restart the application and turn the ring in both directions. Check that its displayed/serial count changes consistently. Press the front button and verify the example's reset behavior.

Expected result: a working screen followed by an encoder count that changes with rotation. A count is an encoder event value, not automatically a calibrated physical angle or application setpoint. Debounce/scaling, allowed ranges and persistence belong in your application.

The reviewed [encoder source](https://github.com/m5stack/M5Dial/blob/735eb55beefe6577c646ebf164a19793a01375d4/examples/Basic/encoder/encoder.ino) also contains a long-press behavior that writes a count of 100. Keep the example's behavior separate from a final control application.

### Add touch, RFID, RTC and networking

Test each peripheral with its dedicated Basic example before combining features. Confirm touch coordinates/rotation, a known RFID tag, RTC operation and any external Grove module separately. A read RFID UID is useful for identification demonstrations but does not alone create a secure access-control system.

For a network dashboard or Home Assistant integration, use the selected firmware's current installation and service requirements. First establish a local display/encoder baseline; network/backend failures should not be mistaken for defective input hardware. For battery applications, measure the selected firmware's real sleep current and wake behavior rather than applying a datasheet's battery-only figure to a USB-powered test.

### Recovery and troubleshooting

| Symptom                    | Check and next step                                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------------------------------- |
| No upload port             | Known data cable, rear G0 download sequence, actual port and model board package.                             |
| Blank display after upload | Exact M5Dial preset, driver dependencies and normal application restart; try stock display example.           |
| Encoder count unchanged    | Encoder enabled in begin arguments, update called in loop and official encoder example.                       |
| RFID not detected          | RFID-enabled initialization, compatible tag/protocol, physical placement and stock RFID example.              |
| Grove module fails         | Correct port/pins, power and logic levels, address/protocol and independent module example.                   |
| Need factory behavior      | Use the exact Dial v1.1 factory/M5Burner application referenced by the manufacturer; preserve settings first. |

Provide model/revision, board-package and library versions, minimal sketch, compiler output and the observed count/serial log when reporting a problem.

### Technical documents and software

| Resource                                                                                                        | Use                                                                    |
| --------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| [Hardware/pin map](https://docs.m5stack.com/en/core/Dial_v1.1)                                                  | Exact revision, power and connectors                                   |
| [Arduino quick-start](https://docs.m5stack.com/en/arduino/m5dial/program)                                       | Board selection, download and stock example                            |
| [M5Dial driver](https://github.com/m5stack/M5Dial/tree/735eb55beefe6577c646ebf164a19793a01375d4)                | Reviewed API/example revision                                          |
| [Official schematic link](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/499/Sch_M5Dial.pdf)                  | Electrical reference linked by the v1.1 page; confirm drawing revision |
| [v1.1 structure/CAD](https://github.com/m5stack/M5_Hardware/tree/master/Products/K130-V11_Dial_v1.1/Structures) | Revision-specific mechanical integration                               |
| [Factory demo source](https://github.com/m5stack/M5Dial-UserDemo)                                               | Manufacturer application reference                                     |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
