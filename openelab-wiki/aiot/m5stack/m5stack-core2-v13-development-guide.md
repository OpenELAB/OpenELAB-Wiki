---
description: >-
  Power, connector allocation, firmware setup, original first-result procedures
  and recovery for M5Stack Core2 v1.3 K010-V13.
---

# M5Stack Core2 v1.3 K010-V13 Development Guide

{% hint style="info" %}
[**View M5Stack Core2 v1.3 K010-V13 on OpenELAB**](https://openelab.io/products/m5stack-core2-esp32-v1-3)

**Model:** Core2 v1.3 K010-V13 · **SKU:** `M5-K010-V13`
{% endhint %}

## Product overview <a href="#product-and-revision" id="product-and-revision"></a>

**Core2 v1.3 K010-V13** is the original-ESP32 Core2 platform with a touch screen, battery, audio, vibration, RTC and the newer BMI270 IMU. It uses **AXP192**, ESP32-D0WDQ6-V3 and a CH9102F USB-to-UART bridge. Do not substitute an ESP32-S3 CoreS3 preset or assume an earlier Core2 revision's IMU/power circuit.

The manufacturer records an LCD change from ILI9342C to ILI9342E on7August2026; the later panel needs M5GFX≥0.2.27. Keep the actual board and panel generation with the library version before diagnosing blank-display behavior. [Exact v1.3 model/revision reference](https://docs.m5stack.com/en/core/Core2_v1.3).

## Applications

Use Core2 v1.3 for a portable sensor instrument, touch dashboard, classroom embedded UI or audio/motion prototype. Test display, touch, IMU, microphone and battery behavior independently before a combined network application. Its enclosure and M5-Bus simplify assembly but do not make another Core module's wiring or power role automatically compatible.

## Specifications

| Parameter                  | Core2 v1.3                                                           |
| -------------------------- | -------------------------------------------------------------------- |
| MCU                        | ESP32-D0WDQ6-V3, dual-core LX6 up to240MHz                           |
| Memory                     | 16MB flash;8MB PSRAM                                                 |
| Supply / battery           | 5V500mA documented input;3.7V500mAh cell                             |
| Display / touch            | 2-inch320×240 ILI9342C/ILI9342E; FT6336U                             |
| IMU / RTC                  | BMI270; BM8563; separate MS412FE3V1mAh rechargeable RTC cell         |
| Audio                      | SPM1423 PDM microphone; NS4168 I2S amplifier                         |
| Power / USB bridge         | AXP192 / CH9102F                                                     |
| HMI                        | Three screen virtual buttons, vibration motor, green power indicator |
| Envelope / operating range | 54×54×16.5mm,58.8g;0–60°C                                            |

[Manufacturer specifications](https://docs.m5stack.com/en/core/Core2_v1.3). Input500mA is not a GPIO or peripheral-output current rating. RTC backup-cell capacity is not the main battery capacity.

## Hardware and connections <a href="#electrical-integration-and-drawings" id="electrical-integration-and-drawings"></a>

### Base and Module compatibility before stacking

**Do not stack Core2 v1.3 with any Base-series expansion base.** Its built-in vibration motor physically interferes with those bases and can damage the unit. For an M5 Module, power off and remove the Core2 v1.3 battery bottom before stacking. If the project must retain the bottom's I2S microphone, IMU and battery functions while adding Modules, M5Stack recommends its **M5GO Bottom2** arrangement; follow that exact accessory's compatibility instructions rather than treating other Base products as equivalent. [Core2 v1.3 compatibility notes](https://docs.m5stack.com/en/core/Core2_v1.3), [M5GO Bottom2 reference](https://docs.m5stack.com/en/base/Base_M5GO_Bottom2).

### v1.3 connections and reserved functions

| Function              | Exact ESP32 / PMIC route                                                       |
| --------------------- | ------------------------------------------------------------------------------ |
| LCD                   | MISO38, MOSI23, clock18, CS5, DC15; AXP192 IO4 reset/DC3 backlight/LDO2 supply |
| microSD               | MISO38, MOSI23, clock18, CS4                                                   |
| Internal I2C          | SDA21/SCL22: AXP1920x34, touch0x38, BM85630x51, BMI2700x68                     |
| Touch interrupt       | 39; screen buttons are touch regions, not three dedicated GPIO switches        |
| Speaker               | BCLK12, LRCK0, data2; AXP192 IO2 amplifier enable                              |
| PDM microphone        | Clock0/data34                                                                  |
| Vibration / indicator | AXP192 LDO3 / IO1                                                              |
| Grove PORT.A          | GND/5V/GPIO32/GPIO33                                                           |
| M5-Bus UART           | UART RX3/TX1; secondary RX13/TX14                                              |
| Bus supply            | 3V3/5V/BAT/GND as marked; NC positions are not high-voltage inputs             |

The USB bridge owns programming/logging through UART0. Internal I2C21/22 differs from external Grove32/33. LCD and SD share SPI with distinct selects. Audio shares clock0 between playback/capture, so sequence their drivers rather than configuring both blindly. GPIO34/35/36/38/39 belong to the input-only range on this original ESP32; do not transfer generic S3 output recipes to them. [v1.3 schematic/pin table](https://docs.m5stack.com/en/core/Core2_v1.3#pinmap).

Use USB-C5V for the first test. Power off before connecting a permitted M5 Module or touching the reserved PCB battery/USB-TTL headers; compare polarity and the exact1.25mm connector definitions before making a cable.3.3V GPIO compatibility is separate from Grove5V supply. Keep the mounting screws clear of the PCB and use the official structure drawing rather than inferring internal clearance from the outside case.

![M5Stack Core2 core-board power, display and bus circuit](../../.gitbook/assets/m5stack-rank-130-diagram.png)

_M5Stack official technical illustration:_ [_original_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/644/CORE2_V1.0_SCH_page_01.png)_. Verify drawing and physical revision together._

## Software and development resources

Install the M5Stack board package and choose **M5Core2**, then install matching **M5Unified/M5GFX**. The [current Core2 Arduino guide](https://docs.m5stack.com/en/arduino/m5core2/program) starts with **ScrollGraph**. For a newer ILI9342E panel meet the M5GFX≥0.2.27 requirement; for a recent M5Unified release follow its own declared M5GFX dependency as well.

For this v1.3 board use the **CH9102F** driver path if the bridge does not enumerate. The shared Core2 tutorial also discusses older CP2104 variants; that does not make CP210x the fitted v1.3 USB bridge. Use the signed driver for the observed hardware and OS rather than lowering system security settings.

UiFlow1 and UiFlow2 are separate firmware generations. Select the exact Core2-compatible image/driver support for the fitted v1.3 IMU and panel; UIFlow1 API KEY and UIFlow2 Access Code are different identifiers. The manufacturer links [M5Core2](https://github.com/m5stack/M5Core2), [M5Unified](https://github.com/m5stack/M5Unified) and its model-specific factory resources; keep legacy `M5Core2.h` examples separate from newer M5Unified code.

## Getting started <a href="#first-program" id="first-program"></a>

### Original touch first result

1. Disconnect all external modules and connect USB-C using a data cable. Identify the CH9102F serial port.
2. Select M5Core2, install the dependencies and compile/upload the stock ScrollGraph example as a baseline.
3. Upload this original touch-coordinate program; open the115200-baud serial monitor.
4. Touch each visible corner and the center. Then test the front virtual-button areas separately so their extended sensing region is not mistaken for an LCD coordinate fault.

```cpp
#include <M5Unified.h>
uint32_t lastLog=0;
void setup() {
  M5.begin();
  Serial.begin(115200);
  M5.Display.setRotation(1);
  M5.Display.fillScreen(TFT_BLACK);
  M5.Display.setTextSize(2);
  M5.Display.setTextColor(TFT_WHITE,TFT_BLACK);
  M5.Display.setCursor(8,8);
  M5.Display.println("Touch each corner");
}
void loop() {
  M5.update();
  int32_t x=0,y=0;
  if (M5.Display.getTouch(&x,&y) && millis()-lastLog>=100) {
    lastLog=millis();
    M5.Display.fillCircle(x,y,3,TFT_GREEN);
    Serial.printf("touch=%ld,%ld,bounds=%d,%d\n",long(x),long(y),
                  M5.Display.width(),M5.Display.height());
  }
  delay(5);
}
```

Expected result is a stable panel with markers at touched positions and a coordinate log. A lit green power indicator alone does not establish display initialization. `M5.update()` keeps virtual-button state fresh; long blocking tasks can delay input handling.

### Original stationary IMU check

After display/touch works, use this separate M5Unified sketch on the **same M5Core2 target**. It requests accelerometer data with the model's driver instead of assuming the earlier MPU6886 register map.

```cpp
#include <M5Unified.h>
void setup() {
  M5.begin();
  Serial.begin(115200);
}
void loop() {
  M5.update();
  float x=0,y=0,z=0;
  if (M5.Imu.getAccel(&x,&y,&z))
    Serial.printf("accel_g=%.3f,%.3f,%.3f\n",x,y,z);
  else Serial.println("IMU_READ_FAILED");
  delay(250);
}
```

Expected result is approximately one-g magnitude while stationary, with the dominant signed axis changing as the unit is rotated. The axes follow the manufacturer's orientation illustration; a stationary offset does not constitute calibrated accuracy. This is an original diagnostic program, not a measured sensor result.

### RTC, storage, audio and power

Set/read BM8563 time, verify it advances, then test RTC backup across a controlled main-power interruption. Do not replace/recharge the RTC cell using assumptions from a nonrechargeable coin-cell design. Test one alarm wake before adding periodic logging.

For microSD use CS4 and the shared18/23/38 SPI route. Read one small file, then create/flush/close one test log before shutdown. A card failure must be separated from bus selection and power-state failures. The SD slot, internal sensors and touch controller are independent resources despite sharing one application.

For audio first test an NS4168 speaker tone at moderate level with amplifier enable correctly managed, stop playback, then capture SPM1423 samples using clock0/data34. Inspect sample count/level before cloud streaming. Test vibration with a short bounded pulse using the model power API; AXP192 LDO3 is its power rail, not an arbitrary PWM GPIO. The green power indicator is not an onboard addressable RGB chain.

For UIFlow2, flash the Core2 image, connect with USB WebTerminal or the current Access Code, run one screen block, then Run Always and restart. For UIFlow1 use its own API KEY and matching image. Save the sketch and necessary configuration before restoring factory firmware. Use the current v1.3 model page's restoration link rather than an image for another Core2 power/IMU generation. [Current v1.3 resources](https://docs.m5stack.com/en/core/Core2_v1.3).

## Troubleshooting and FAQs <a href="#recovery-and-faqs" id="recovery-and-faqs"></a>

| Symptom                            | Checks / recovery                                                                                                                  |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Blank newer LCD                    | Check ILI9342E generation, M5GFX minimum and M5Core2 target before changing wiring.                                                |
| IMU example fails                  | Exact v1.3 BMI270 support; remove MPU6886-specific raw-register initialization.                                                    |
| No serial port                     | Data cable/direct USB → CH9102F enumeration → matching driver; shared CP2104 notes describe another revision.                      |
| Touch/buttons sluggish             | Frequent M5.update; isolate from blocking SD/network work; separate physical touch coordinates from virtual-button classification. |
| Grove sensor missing               | External32/33, not internal21/22; check supply, pull-ups and the attached Unit address.                                            |
| Audio capture fails after playback | Release playback driver/shared clock0 before PDM capture; use correct12/0/2 versus0/34 routes.                                     |
| Wake/power unexpected              | AXP192 configuration, RTC alarm state, connected USB and actual battery state; do not transplant AXP2101 settings.                 |

## Downloads and technical documents

Use both the manufacturer-linked core-board schematic and the v1.3 expansion-board schematic. Their filenames reflect different subassemblies; together they establish the complete unit. The model drawing/STL and bridge drivers are listed below with the original source URLs.

| Official file or repository                                                                                                                      | Use                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- |
| [M5Tool](https://github.com/m5stack/M5Tools)                                                                                                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Core2 v1.3 Core Section Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/644/CORE2_V1.0_SCH.pdf)                                | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Core2 v1.3 Expansion Board Section Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/486/core2_v1.3_SCH_2025_11_14_09_40_33.pdf) | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Core2 v1.3 Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1231/K010-V13_Core2_v1.3_model-size.pdf)                            | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Core2 v1.3 Structure Files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K010-V13_Core2_v1.3/Structures)                         | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ESP32](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/644/esp32_datasheet_en.pdf)                                                             | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [NS4168](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/NS4168_CN_datasheet.pdf)                                      | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [BMI270](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMI270.PDF)                                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ILI9342C](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/ILI9342C-ILITEK.pdf)                                        | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [SPM1423](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/SPM1423HM4H-B_datasheet_en.pdf)                              | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [BM8563](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/BM8563_V1.1_cn.pdf)                                           | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [SY7088](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/SY7088-Silergy.pdf)                                           | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [AXP192 Datasheet](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1231/AXP192_datasheet_en.pdf)                                                | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [1027DC Motor](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/1027RFN01-33d.pdf)                                      | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ILI9342E](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/644/ILI9342E.pdf)                                                                    | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Core2 v1.3 Arduino Library](https://github.com/m5stack/M5Core2)                                                                                 | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CH9102_VCP_SER_Windows.exe)                                             | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Download](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1231/Core2_Factory_FirmWare.exe)                                                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |

### Additional model references <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

* [Core and bottom schematics, pinouts and dimensions](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/static/pdf/static/en/core/Core2_v1.3.pdf)
* [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K010-V13_Core2_v1.3/Structures/Core2_v1.3.stl)
* [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5core2/button)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

This guide uses the exact sold SKU and the [manufacturer reference](https://docs.m5stack.com/en/core/Core2_v1.3). Specifications are manufacturer-reported; diagnostic order and first-result programs are original engineering work. The v1.3 BMI270/AXP192/CH9102F hardware identity, pin ownership and7August2026 LCD revision note were reviewed. Display, motion, RTC retention, audio and low-power behavior were not exercised on hardware.

**Review:** 24 November 2026. Manufacturer documentation and the linked SDK interfaces were reviewed. **Compilation, firmware flashing and hardware operation: not run.** Expected results above are commissioning checkpoints, not observed bench measurements.
