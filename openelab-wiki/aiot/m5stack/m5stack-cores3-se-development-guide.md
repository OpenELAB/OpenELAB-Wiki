---
description: >-
  Power, connector allocation, firmware setup, original first-result procedures
  and recovery for M5Stack CoreS3-SE K128-SE.
---

# M5Stack CoreS3-SE K128-SE Touch and Development Guide

{% hint style="info" %}
[**View M5Stack CoreS3-SE K128-SE on OpenELAB**](https://openelab.io/products/m5stack-cores3-se-iot-controller-w-o-battery-bottom)

**Model:** CoreS3-SE K128-SE · **SKU:** `M5-K128-SE`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

**CoreS3-SE K128-SE** is the reduced-peripheral ESP32-S3 Core controller with a2-inch touch screen, speaker, microphones, RTC, storage and M5-Bus expansion. OpenELAB's assigned SKU is the controller **without the battery bottom**. It is not the full CoreS3 K128/DinBase kit: SE omits its GC0308 camera, LTR-553 proximity sensor, BMI270 IMU and BMM150 magnetometer. Do not interpret a shared Arduino target as evidence of those fitted devices.

Start on USB-C with a local touch test. Retain this established page separately from the full [CoreS3 guide](m5stack-cores3-esp32s3-lot-development.md), whose camera/sensing and base power instructions have a different hardware scope.

## Applications

Use SE for a USB-powered control panel, touch menu, network status display or audio/UI prototype where the full CoreS3 camera and motion sensors are unnecessary. Add an identified external sensor when required; a successful internal I2C scan cannot discover chips that SE does not contain.

## Specifications

| Parameter           | CoreS3-SE K128-SE                                                         |
| ------------------- | ------------------------------------------------------------------------- |
| MCU / memory        | ESP32-S3 dual-core240MHz;16MB flash;8MB Quad PSRAM                        |
| Display / touch     | 2-inch ILI9342C320×240; FT6336U capacitive touch with320×280 sensing area |
| Audio               | ES7210 dual-mic ADC; AW88298 I2S amplifier and1W speaker                  |
| Power / RTC         | AXP2101 power manager; AW9523B IO expander; BM8563 RTC                    |
| Storage / expansion | microSD; M5-Bus; Grove                                                    |
| Sold package        | K128-SE controller, no battery bottom; do not assume DinBase is supplied  |
| Envelope / mass     | 54×54×15.5mm;37.8g                                                        |
| Operating range     | 0–40°C                                                                    |

[SE specification and comparison table](https://docs.m5stack.com/en/core/CoreS3-SE). PSRAM is Quad, unlike the octal-memory AtomS3R/Tab5 configurations.

## Hardware and connections

### Power and bus boundaries

Use USB-C5V for commissioning. Any battery, bus supply or powered module needs an independently verified connector, voltage and PMIC direction. The full CoreS3 kit's9–24V DinBase input does **not** establish a high-voltage input on this bare SE controller. Never feed that voltage to USB, Grove5V,3V3 or BAT.

| Function           | SE route                                                                   |
| ------------------ | -------------------------------------------------------------------------- |
| Internal I2C       | SDA12/SCL11                                                                |
| Internal addresses | AXP21010x34, AW882980x36, FT6336U0x38, ES72100x40, BM85630x51, AW9523B0x58 |
| LCD SPI            | MOSI37, clock36, CS3, DC35; reset via expander P1\_1                       |
| microSD SPI        | MISO35, MOSI37, clock36, CS4                                               |
| Touch              | I2C12/11, reset P0\_0 and interrupt P1\_2 on AW9523B                       |
| Audio              | BCLK34, LRCK33, speaker data13, microphone data14, MCLK0                   |
| Grove PORT.A       | GND/5V/GPIO2/GPIO1                                                         |
| M5-Bus serial      | UART043/44; PORT.C-compatible TX17/RX18 on bus                             |

LCD/microSD share SPI lines and have separate chip selects; GPIO35 serves LCD DC and SD MISO in the documented routing. Let the display/SD drivers coordinate transactions rather than bit-banging those lines. `BUS_OUT_EN` and `USB_OTG_EN` determine power direction with AXP2101/AW9523B. Do not connect two powered sources merely because the connector fits. [SE pin map and power diagrams](https://docs.m5stack.com/en/core/CoreS3-SE), [power API](https://docs.m5stack.com/en/arduino/m5cores3/power).

The touch sensing area extends beyond the visible320×240 LCD to support virtual-button regions. Keep visible touch drawing within the actual framebuffer and test virtual-button behavior separately. Core2 and CoreS3 M5-Bus signal positions differ even when the stack connector is similar.

![M5Stack CoreS3-SE AXP2101 power-management circuit](../../.gitbook/assets/m5stack-rank-123-diagram.png)

_M5Stack official technical illustration:_ [_original_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/498/Sch_M5_CoreS3_SE_v1.0_page_01.png)_. Verify drawing and physical revision together._

## Software and development resources <a href="#software-and-recovery" id="software-and-recovery"></a>

Install the [M5Stack board package](https://docs.m5stack.com/en/arduino/arduino_board), select **M5CoreS3** and install **M5Unified/M5GFX** plus dependencies. The [SE-specific quick-start](https://docs.m5stack.com/en/arduino/m5cores3_se/program) intentionally uses this shared target and **BarGraph** first example. Preserve16MB flash and Quad PSRAM; an octal profile is not a compatible substitute.

Use current matching library releases and record them. The reviewed M5Unified metadata is0.3.0 with M5GFX≥0.3.0; the exact body of each project remains the reproducibility record. Older `M5CoreS3` library examples and current M5Unified examples expose different object names: do not combine initialization fragments casually.

UiFlow2 uses **CoreS3-SE** firmware/controller; the main hardware page links its setup and the shared family APIs. The linked CoreS3-UserDemo source is a family project: select the SE configuration and disable absent camera/IMU features before building an application.

## Getting started <a href="#getting-started-local-display-test" id="getting-started-local-display-test"></a>

### Original touch-coordinate check

1. Remove external modules; connect the bare SE to a computer by USB-C data cable.
2. Select **M5CoreS3**, install matching M5Unified/M5GFX and compile the stock BarGraph example before this small custom program.
3. If needed, hold the bottom reset key until the internal green LED lights, release and choose the newly enumerated port. Upload, then restart into the application.
4. Upload the original sketch below. Touch center and visible corners and compare green marks with115200-baud coordinates.

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

Expected result is a stable screen and marks following touch, with coordinates within rotated visible bounds. A touch logged beyond the LCD's visible height can belong to the extended virtual-button area. No camera or IMU operation is part of this SE test.

### RTC, SD and audio after the display baseline

Use BM8563 to set a known time and read it back before scheduling a wake. Confirm elapsed time across one controlled reset and keep timezone conversion in the application. Alarm wake and a radio-off idle state are different tests.

For storage, use the model's SD example on CS4/clock36/MOSI37/MISO35. Verify card detection/capacity, read a small text file, then create/close a single test log. Keep the panel update and card transaction serialized during first debugging; flush before power off. Do not assume a failed mount means the card is defective before checking the exact bus and supply state.

For audio, begin with a short moderate speaker tone, then stop playback and run the model microphone capture example. Check rate, buffers, ES7210 input and AW88298 initialization separately. Captured nonzero samples establish activity, not calibrated sound pressure or validated echo cancellation.

For Grove, enable the intended5V output state, connect a compatible Unit on2/1 with power off and compare its expected I2C address. Never scan the internal12/11 bus and infer that an external2/1 Unit is absent. With UiFlow2, use the SE image, establish WebTerminal or a current Access Code, Run Once, then Run Always and restart for persistence. [SE software resources](https://docs.m5stack.com/en/core/CoreS3-SE).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                    | Diagnosis and recovery                                                                                              |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Camera / IMU example fails | SE omits those peripherals; remove their initialization or use an identified external sensor.                       |
| Blank display              | Exact M5CoreS3 target → matching libraries → normal application restart → stock BarGraph.                           |
| USB port absent            | Data cable/direct port, bottom reset green-LED boot mode, reselect new port.                                        |
| External module absent     | Correct bus2/1 versus internal12/11, PMIC output direction, supply and Unit address.                                |
| Battery value meaningless  | Sold SE package has no battery bottom; do not infer a connected cell from a family API field.                       |
| Power conflict             | Disconnect sources, compare BUS\_OUT\_EN/USB\_OTG\_EN and module supply role before retrying.                       |
| Factory restore            | Choose exact SE factory entry/download; shared family source naming is not a generic image compatibility guarantee. |

## Downloads and technical documents

The official SE model-size link currently uses a `cores3-lite.pdf` filename. It is retained as an explicitly manufacturer-linked resource; compare its dimensions and drawing title with the fitted SE before using it for fabrication. The exact SE schematic and structure directory below establish its separate hardware scope.

| Official file or repository                                                                                                      | Use                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [CoreS3-SE Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/498/Sch_M5_CoreS3_SE_v1.0.pdf)                       | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [CoreS3-SE Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1162/cores3-lite.pdf)                                | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [CoreS3-SE Structure Files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K128-SE_CoreS3-SE/Structures)            | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [esp32-s3](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/490/esp32-s3_technical_reference_manual_en.pdf)                      | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ES7210](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/ES7210.PDF)                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [BM8563](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BM8563.PDF)                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [AXP2101](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/AXP2101_Datasheet_V1.0_en.pdf) | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [AW88298](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/AW88298.PDF)                   | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [AW9523B](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/CoreS3/AW9523B-EN.pdf)                        | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [CoreS3-SE Arduino Library](https://github.com/m5stack/M5CoreS3)                                                                 | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [CoreS3-SE Factory Firmware (pio)](https://github.com/m5stack/CoreS3-UserDemo)                                                   | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5CORES3%20SE/CoreS3%20SE%20Firmware.exe)    | Manufacturer-listed exact model document / maintained source; use the scope described above. |

### Additional model references <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

* [M5Unified source and examples](https://github.com/m5stack/M5Unified)
* [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K128-SE_CoreS3-SE/Structures/CoreS3-SE.stl)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

This guide uses the exact sold SKU and the [manufacturer reference](https://docs.m5stack.com/en/core/CoreS3-SE). Specifications are manufacturer-reported; diagnostic order and first-result programs are original engineering work. The exact SE omission list, internal address table, power-control path and shared M5CoreS3 software target were reviewed. Touch, SD, audio and power-direction commissioning remain expected procedures, not executed results.

**Review:** 24 November 2026. Manufacturer documentation and the linked SDK interfaces were reviewed. **Compilation, firmware flashing and hardware operation: not run.** Expected results above are commissioning checkpoints, not observed bench measurements.

### Related retained references

* [CoreS3 family comparison](https://docs.m5stack.com/en/core/CoreS3)
