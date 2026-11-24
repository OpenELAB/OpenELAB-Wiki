---
description: >-
  Bring up the 868 MHz T-Watch Ultra with the correct LilyGoLib target, verify
  AMOLED and touch, and inspect GNSS, NFC and power sequencing.
---

# LILYGO T-Watch Ultra Engineering Guide

{% hint style="info" %}
[**View LILYGO T-Watch Ultra ESP32S3 LoRa With GNSS & AMOLED on OpenELAB**](https://openelab.io/products/lilygo-t-watch-ultra-lora)

**Model / option:** 868 MHz\[K253-01] · **SKU:** `LILYGO-K253-01`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

T-Watch Ultra K253-01 is the **868 MHz** ESP32-S3 wearable development platform with AMOLED/touch, GNSS, NFC and a sub-GHz radio. Select the **Ultra + SX1262** hardware target; T-Watch S3, S3Plus and the Ultra's SX1280 2.4 GHz option have different support scopes. An image merely mentioning “T-Watch” is insufficient.

This guide first verifies local display/touch, then treats GNSS and radio as separate tests. The factory demonstration application is not automatically a Meshtastic or MeshCore terminal. [Exact Ultra hardware reference](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/hardware/lilygo-t-watch-ultra.md).

## Applications

Use Ultra for wearable UI, GNSS logging, motion-sensor demonstrations, reading known NFC tags and controlled radio experiments. Its sensor set does not establish a certified health, navigation or emergency function. Measure runtime at the actual display brightness, GNSS interval, radio duty cycle and sleep/wake configuration.

Separate a display refresh, a touch event, an actual receiver fix and a peer packet receipt. Success at one does not prove the others.

## Specifications

| Subsystem        | Ultra specification / integration consequence                                               |
| ---------------- | ------------------------------------------------------------------------------------------- |
| Host / memory    | ESP32-S3; 16 MB QSPI flash, 8 MB QSPI PSRAM                                                 |
| Display / touch  | CO5300 QSPI AMOLED, 410 × 502, 2.06-inch; CST9217                                           |
| GNSS / RTC       | MIA-M10Q /PCF85063A                                                                         |
| Radio            | Purchased 868 MHz SX1262 path; SX1280 is a separate 2.4 GHz option                          |
| NFC / motion     | ST25R3916 /BHI260AP                                                                         |
| Audio / haptics  | T3902 PDM mic, MAX98357A amplifier, DRV2605                                                 |
| Power / expander | AXP2101 /XL9555                                                                             |
| Card             | microSD up to 32 GB, FAT32                                                                  |
| Battery          | 3.7 V 1100 mAh, 4.07 Wh                                                                     |
| USB input        | 3.9–6 V documented; use ordinary regulated 5 V for the bench                                |
| Charge setting   | Programmable 0–1024 mA range; **use below 500 mA and no more than 0.5 C** per manufacturer  |
| Case             | 63.5 × 49 × 22 mm without strap; display −20 to +70 °C is not a charging-temperature rating |

Sources: [hardware/power tables](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/hardware/lilygo-t-watch-ultra.md), [Ultra wiki](https://wiki.lilygo.cc/products/t-watch-series/t-watch-ultra/). The programmable charger maximum is not a recommended assembly setting. USB-C is for charging/programming and **does not power external devices**.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Occupied signals and power rails

Keep the installed battery and enclosure harness intact for first setup. The USB supply is distinct from 3.3 V logic. Leave the PMU/expander sequencing to the exact Ultra board support; an uninitialized display power rail can make a correctly wired panel appear dead.

| Internal bus/function          | ESP32-S3 GPIO                                                    |
| ------------------------------ | ---------------------------------------------------------------- |
| I²C SDA/SCL                    | 3/2                                                              |
| Shared SPI MOSI/MISO/SCK       | 34/33/35                                                         |
| Radio CS/reset/busy/IRQ        | 36/47/48/14                                                      |
| Card CS                        | 21                                                               |
| NFC CS/IRQ                     | 4/5                                                              |
| GNSS TX/RX/PPS labels          | 43/44/13; preserve the driver's host/module direction convention |
| RTC IRQ / PMU IRQ / BHI260 IRQ | 1/7/8                                                            |
| AMOLED CS/SCK/reset/TE         | 41/40/37/6                                                       |
| AMOLED data 0/1/2/3            | 38/39/42/45                                                      |
| Speaker BCLK/WCLK/data         | 9/10/11                                                          |
| BOOT/user                      | 0; reset is a separate non-programmable control                  |

The shared I²C addresses are touch 0x1A, expander 0x20, motion 0x28, PMU 0x34, RTC 0x51 and haptic 0x5A. Expander offsets are **not MCU GPIOs**: offset 6 enables haptics, 7 display power, 10 touch reset and 12 card detect. [Full pin/address table](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/hardware/lilygo-t-watch-ultra.md).

PMU channels are also distinct: DC1 host, ALDO1 card, ALDO2 display, ALDO3 radio, ALDO4 sensor, BLDO1 GNSS, BLDO2 speaker, DLDO1 NFC and VRTC GNSS backup. Do not raise a rail merely because a component is silent. NFC card detection requires its reader powered; this board lacks an external capacitive card-presence circuit. [V1.0 schematic](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGoLib/9116bf41ca551d75a42d16cab391fe254f21ab2c/schematic/T-Watch%20Ultra%20V1.0%20SCH%2025-07-24.pdf).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

### Use a coherent current SDK

The reviewed LilyGoLib commit is **`9116bf41ca551d75a42d16cab391fe254f21ab2c`**. Its current Arduino quick start requires **Arduino-ESP32 3.3.11 or later**, tested third-party library versions, board **LilyGo T-Watch-Ultra**, revision **Radio-SX1262**, 16M Flash (3MB APP/9.9MB FATFS), USB CDC enabled and Hardware CDC/JTAG. Keep the third-party library collection as a set until the basic example works. [Pinned Ultra setup](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/lilygo-t-watch-ultra.md).

The public wiki's older 3.3.0-alpha1 / separate PlatformIO instructions differ from the current source. The pinned source now supplies a **pioarduino** workflow with platform release **55.03.311**, environment **`twatch_ultra_sx1262`**. Its default environment is a different board, so explicitly select Ultra. `src_dir` chooses the example; the radio suffix chooses the hardware. [Current PlatformIO instructions](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/platformio.md), [actual configuration](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/platformio.ini).

Do not mix older LilyGoLib-PlatformIO libraries with this current main-tree example. The upstream `helloworld` file identifies MIT licensing; bundled LVGL, radio and peripheral libraries retain their own notices.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First local result

1. Charge through USB-C with the original pack. Leave the factory charging configuration within the documented below 500 mA limit. Hold POWER about 1 second to start; its approximately 6 second hold is shutdown, not the BOOT/download button.
2. Record factory firmware and hardware identity. Check a new display change and touch response, then save configuration before replacing the application.
3. In Arduino install the exact board/library set above, open **LilyGoLib → helloworld**, select **Ultra / Radio-SX1262**, and compile before upload. Select the actual USB port; do not choose S3/S3Plus or the 2.4 GHz radio.
4. Upload with stable power, open 115200 baud serial, and touch the example button several times. Compare the displayed count with distinct serial click events.
5. Reset and repeat on battery. A black display only after custom initialization calls for checking PMU/expander sequencing before changing panel voltages.

**Expected result:** readable display, a touch-driven count and matching serial events. This is an expected first-run result, not a reported build or hardware observation. [Exact example](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/examples/helloworld/helloworld.ino).

### Original small touch-event diagnostic

This newly written sketch uses the reviewed LilyGoLib/LVGL initialization interfaces. It prints one event counter per click and leaves the board-specific peripheral setup to `instance.begin()`. It replaces the application and has not been compiled here.

```cpp
#include <LilyGoLib.h>
#include <LV_Helper.h>
static uint32_t touches = 0;
static void touched(lv_event_t *event) {
  if (lv_event_get_code(event) == LV_EVENT_CLICKED) {
    Serial.printf("ultra_touch=%lu\n", (unsigned long)++touches);
  }
}
void setup() {
  Serial.begin(115200);
  instance.begin();
  beginLvglHelper(instance);
  instance.setBrightness(100);
  lv_obj_t *button = lv_button_create(lv_screen_active());
  lv_obj_set_size(button, 180, 90);
  lv_obj_center(button);
  lv_obj_add_event_cb(button, touched, LV_EVENT_CLICKED, nullptr);
  lv_obj_t *label = lv_label_create(button);
  lv_label_set_text(label, "Touch check");
  lv_obj_center(label);
}
void loop() {
  lv_timer_handler();
  delay(2);
}
```

**Expected result:** each completed touch click adds one `ultra_touch` line at 115200 baud. If display works but no events arrive, check the Ultra touch driver/reset and matched LVGL dependencies. A button press on GPIO0 is not this touch test. Interfaces are sourced from the [MIT upstream example](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/examples/helloworld/helloworld.ino).

For a pinned command-line build, use a pioarduino IDE Terminal, set `src_dir = examples/helloworld` in the existing repository and run:

```sh
git clone --recursive https://github.com/Xinyuan-LilyGO/LilyGoLib.git
cd LilyGoLib
git checkout 9116bf41ca551d75a42d16cab391fe254f21ab2c
git submodule update --init --recursive
# Set src_dir = examples/helloworld before the following build.
pio run -e twatch_ultra_sx1262
```

Expected output is an Ultra SX1262 artifact; the command is a source-reviewed procedure and was not executed.

### Add GNSS, radio and other peripherals separately

For GNSS use the matched MIA-M10Q example, enable its BLDO1 rail through board support and inspect new receiver data outdoors. Check time/fix separately from a stored map marker. For NFC use the ST25R3916 example and a known tag you control; PN532 code from T-Embed is a different interface. Validate motion, haptic, microphone/speaker and card tests separately; the 32 GB FAT32 card limit is a documented test scope, not every card's guarantee.

The repository's generic SX126xPingPong example contains **915 MHz, 22 dBm and 3.0 V TCXO setters**. Those values must not be copied blindly to this 868 MHz SKU. Use the exact board radio initialization, a locally permitted matching profile and a verified TCXO configuration before a transmit experiment; until then use the local non-transmit test above. A generic RadioLib example is not evidence that arbitrary radio parameters suit every LilyGoLib board.

For USB recovery, connect the data cable, hold BOOT, press/release RST, release BOOT, select the stable port and upload the exact Ultra image. Press RST afterward to run. Restore the matching factory firmware if a custom application fails; a different T-Watch image is not a hardware test.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                          | Ordered checks                                                                                                                 |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| USB repeatedly disconnects       | Manual BOOT/RST download entry, correct data cable, stable power and exact Ultra image                                         |
| Black AMOLED                     | Ultra CO5300 driver, ALDO2 and expander power sequencing, matched memory/partition settings                                    |
| Touch inactive                   | CST9217 driver/address, reset via expander and dependency versions; display refresh alone is insufficient                      |
| PMU gets hot during charging     | Charging configuration below 500 mA, source/pack and peripheral load; do not increase current to fix a slow charge             |
| GNSS absent                      | MIA-M10Q power/data, sky view, new fix/time; radio operation does not prove GNSS                                               |
| Sleep current differs from chart | Record wake sources, backup rail, touch and USB measurement boundary; manufacturer's 840 µA–mA reference modes are conditional |
| Radio example uses 915 MHz       | Stop and match this 868 MHz SKU and exact board support before TX                                                              |

The watch's USB-C port cannot supply an external accessory. A spare-looking pad or expander number does not establish a free 3.3 V GPIO or available power budget.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                         | Exact scope                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| [Current Ultra wiki](https://wiki.lilygo.cc/products/t-watch-series/t-watch-ultra/)                                                                                                                                                                                              | Product/peripheral reference; toolchain text can lag the source                           |
| [Pinned hardware and power reference](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/hardware/lilygo-t-watch-ultra.md)                                                                                                           | Pins, addresses, PMU rails, charge and conditional current tables                         |
| [Pinned Arduino quick start](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/lilygo-t-watch-ultra.md) /[pioarduino](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/platformio.md) | Coherent SDK/board selection and recovery                                                 |
| [V1.0 schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGoLib/9116bf41ca551d75a42d16cab391fe254f21ab2c/schematic/T-Watch%20Ultra%20V1.0%20SCH%2025-07-24.pdf)                                                                                                  | Five-sheet board resource; match received revision                                        |
| [Third-party dependency record](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/9116bf41ca551d75a42d16cab391fe254f21ab2c/docs/third_party.md)                                                                                                                                   | Version-specific library collection                                                       |
| [Examples](https://github.com/Xinyuan-LilyGO/LilyGoLib/tree/9116bf41ca551d75a42d16cab391fe254f21ab2c/examples)                                                                                                                                                                   | Local UI, radio, GNSS, NFC, motion, power and storage; inspect each board/parameter scope |

The hardware reference links manufacturer ESP32-S3, SX1262, MIA-M10Q, BHI260AP, AXP2101 and other component documents. Use those for detailed component design; do not change panel/PMU rails using another watch's defaults.

### Additional existing resources

* [Manufacturer product](https://lilygo.cc/products/t-watch-ultra)
* [Exact Ultra hardware reference](https://github.com/Xinyuan-LilyGO/LilyGoLib/blob/master/docs/hardware/lilygo-t-watch-ultra.md)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Read sources include the exact hardware and SDK documents, build configuration, current wiki, third-party record and HelloWorld/radio examples at the pinned commit. The schematic's main-host/card sheet was visually inspected. The original touch diagnostic and staged acceptance use the exact initialization interfaces. Generic radio parameter setters remain explicitly outside the local first-result scope.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
