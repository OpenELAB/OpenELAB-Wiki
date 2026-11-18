# M5Stack StopWatch C152 Development Guide

{% hint style="info" %}
[**View M5Stack StopWatch C152 on OpenELAB**](https://openelab.io/products/m5stack-stopwatch-dev-kit-esp32-s3)

**Covered model:** M5Stack StopWatch C152 · **SKU:** `M5-C152`
{% endhint %}

![M5Stack StopWatch C152 Development Guide](../../.gitbook/assets/stopwatch-c152-development-guide.webp)

_Manufacturer image: M5Stack._ [_Image source_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1242/C152_stopwatch_mainpictures_01.webp)_._

[Product at OpenELAB](https://openelab.io/products/m5stack-stopwatch-dev-kit-esp32-s3) · [Manufacturer wiki hub](./)

## Product and revision check

**M5Stack StopWatch C152** is a compact ESP32-S3 handheld development device with a round AMOLED touchscreen. It suits a portable control panel, electronic badge, timer interface or sensor display. It includes audio, motion sensing and battery operation; application behavior is defined by the installed firmware.

**Check hardware revision before using the rear power pin.** M5Stack documents a v1.0 sticker error: a pin marked BAT on some units is actually **5 V IN**. In v1.0.1, the revised BAT pin is a battery connection. Do not connect a battery according to the sticker alone. Use USB-C for the first tutorial and compare the actual board/revision with the manufacturer's notice.

## Specifications and interfaces

| Item         | Specification                                                           |
| ------------ | ----------------------------------------------------------------------- |
| Controller   | ESP32-S3R8, 16 MB flash, 8 MB PSRAM                                     |
| Display      | 1.75-inch round AMOLED, 466 × 466, touch input                          |
| User input   | Two programmable buttons, power control and vibration feedback          |
| Audio        | ES8311 codec, microphone and 1 W speaker path                           |
| Sensors/time | BMI270 IMU; RX8130CE RTC                                                |
| Power        | USB-C 5 V; built-in 450 mAh battery; M5PM1 management                   |
| Expansion    | HY2.0-4P port and rear header; verify revision-specific pin definitions |
| Size/mass    | 52 × 52 × 15.5 mm; 39 g                                                 |

The HY2.0-4P port is documented as GND/5 V/G10/G11. Rear multiplexed pins and power rails require the M5IOE1/M5PM1 configuration shown in the pin map. Do not infer always-on peripheral power or generic ESP32 pin availability from the connector alone.

Source: [M5Stack StopWatch hardware reference](https://docs.m5stack.com/en/core/StopWatch). Revision notes take priority over a generic wiring diagram.

## Software options

Arduino development uses **M5Unified** and **M5GFX**, with M5PM1/M5IOE1 support for power and expansion functions. UiFlow2 offers the manufacturer-supported visual/Python route. The factory firmware is an additional application that can be restored through its documented M5Burner workflow.

Use the [StopWatch-specific Arduino guide](https://docs.m5stack.com/en/arduino/stopwatch/program); a nearby ESP32-S3 board preset may compile while selecting the wrong display or power configuration.

## Getting started: run the official BarGraph example

Prepare StopWatch, a USB-C data cable, a computer and Arduino IDE 2.x.

1. Install the M5Stack board package using the [official board-manager setup](https://docs.m5stack.com/en/arduino/arduino_board). Select **M5StopWatch** in the board menu, then the device's serial port.
2. Install **M5Unified** and **M5GFX** through Library Manager and accept their dependencies. Record the selected versions. For explicit peripheral-power work, use the linked M5PM1 and M5IOE1 guides/libraries.
3. Open the official **BarGraph** example referenced by the StopWatch Arduino guide. Build it first. If the selected library installation lacks the example, follow the current manufacturer link rather than substituting a sketch for another display board.
4. Upload using a data cable. If automatic bootloader entry fails, hold the power/reset control until the green indicator signals download mode, release it and select the enumerated port again. Use the current manufacturer animation/instructions for the exact physical operation.
5. Restart into the application if necessary and inspect the graph rendering on the round screen. The first checkpoint is a working upload and correctly rendered display; it does not validate the speaker, IMU, battery or sleep current.

The example is linked rather than copied so the device-specific display initialization remains with its maintained upstream version. Save the working example/library versions before extending it.

## Add input, sensors and low-power behavior

Use `M5.update()` in an M5Unified application before reading button state. Add a single button or touch interaction to the known working display application, then test IMU, audio and RTC independently. Follow the [power-management guide](https://docs.m5stack.com/en/arduino/stopwatch/m5pm1_m5ioe1) when enabling rails or peripherals: a peripheral that has no power can resemble a failed driver.

For battery projects, measure idle and sleep current with the intended rails, screen state and wake sources. A program that uses an ESP32 sleep call without accounting for the external power-management chips can behave differently from the vendor's low-power demo.

## Recovery and FAQ

| Problem                              | Check                                                                                               |
| ------------------------------------ | --------------------------------------------------------------------------------------------------- |
| Board does not enumerate             | Data cable, charged/powered device, USB port and documented download-mode entry.                    |
| Code builds but screen is blank      | M5StopWatch preset, recent compatible M5Unified/M5GFX versions and peripheral-power initialization. |
| BAT label differs from documentation | Stop using the rear power pin; identify v1.0 versus v1.0.1 and follow the official revision notice. |
| Button reads never change            | Update the M5Unified state each loop and use the model's button mapping.                            |
| Need the original application back   | Follow the official factory-restoration guide for C152; preserve required settings before flashing. |
| Battery drains rapidly               | Inspect display/radio/rail state and wake frequency; compare with the manufacturer's power demo.    |

## Technical documents and software

| Resource                                                                                                                            | Use                                              |
| ----------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| [Hardware and revision notice](https://docs.m5stack.com/en/core/StopWatch)                                                          | Specifications, pin map and power-pin correction |
| [Arduino quick-start](https://docs.m5stack.com/en/arduino/stopwatch/program)                                                        | M5StopWatch preset and BarGraph example          |
| [Schematics](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1242/C152-SCH_Stopwatch_PRJ_Main_VA_20251201_2026_04_24_17_46_22.pdf) | Electrical reference                             |
| [Dimension drawing](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1242/C152-StopWatch-model-size.pdf)                            | Mechanical dimensions                            |
| [CAD/structure files](https://github.com/m5stack/M5_Hardware/tree/master/Products/C152_StopWatch/Structures)                        | Mechanical integration                           |
| [M5Unified](https://github.com/m5stack/M5Unified)                                                                                   | Arduino device API                               |
| [M5GFX](https://github.com/m5stack/M5GFX)                                                                                           | Display library and examples                     |
| [Power-management guide](https://docs.m5stack.com/en/arduino/stopwatch/m5pm1_m5ioe1)                                                | M5PM1 and M5IOE1                                 |
| [Factory restoration](https://docs.m5stack.com/en/guide/stopwatch/restore_factory)                                                  | Return to manufacturer firmware                  |
| [Factory firmware source](https://github.com/m5stack/M5StopWatch-UserDemo)                                                          | Application reference                            |
| [Low-power demo](https://github.com/m5stack/M5StopWatch-PowerDemo)                                                                  | Power-measurement development reference          |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
