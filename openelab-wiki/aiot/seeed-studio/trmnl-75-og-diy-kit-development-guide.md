---
description: >-
  Assemble and program the OG 7.5-inch kit: 24-pin jumper, exact SPI pins,
  original display/button/battery tests, ESPHome and TRMNL setup.
---

# Seeed Studio TRMNL 7.5-inch OG DIY Kit Development Guide

{% hint style="info" %}
[**View Seeed Studio TRMNL 7.5-inch (OG) DIY Kit on OpenELAB**](https://openelab.io/products/seeed-studio-trmnl-diy-kit)

**Model:** TRMNL 7.5-inch (OG) DIY Kit · **SKU:** `Seeed-104991005` · **Scope:** XIAO ESP32-S3 Plus driver, 800 × 480 monochrome panel, battery and FPC parts; enclosure is separate.
{% endhint %}

## Product overview <a href="#product-and-kit-scope" id="product-and-kit-scope"></a>

This kit builds a programmable ePaper dashboard from a bare panel and XIAO-based driver board. It is distinct from the enclosed reTerminal E1001 and from a bare Spectra 6 panel: panel palette, controller, pinout and firmware differ. Choose Arduino for local rendering, ESPHome for Home Assistant, or TRMNL's device/server workflow. [Kit overview](https://wiki.seeedstudio.com/trmnl_7inch5_diy_kit_main_page/).

![Seeed TRMNL OG DIY Kit](../../.gitbook/assets/trmnl-75-og-diy-kit-development-guide.jpg)

_Seeed Studio_ [_original kit image_](https://files.seeedstudio.com/wiki/XIAO_Gadget/TRMNL_Kit_Pic/head.jpg)_._ [Seeed Studio hub](./).

## Applications

Build a calendar, a room/status dashboard or a low-duty-cycle Home Assistant display. Separate the source-data update cadence from the physical refresh cadence. For a battery design, network association and rendering can consume more energy than retaining a frame; a fixed ePaper image does not mean that Wi-Fi or the MCU is asleep.

A custom enclosure must support the fragile panel, isolate the PCB from conductive mounting surfaces and leave USB, buttons, switch and FPC accessible. Use the manufacturer's enclosure links/drawings as a starting point and check fit against the actual shipped board revision.

## Specifications

| Item             | Kit-specific reference                                                       |
| ---------------- | ---------------------------------------------------------------------------- |
| Controller       | XIAO ESP32-S3 Plus on ePaper display driver board                            |
| Panel            | 7.5-inch monochrome, 800 × 480, UC8179 driver path                           |
| Power            | 5 V USB input; supported single-cell lithium battery circuit                 |
| Supplied battery | 2000 mAh rechargeable Li-ion in documented kit                               |
| Display cable    | 24-pin FPC, 0.5 mm pitch on the driver; 10 cm extension and connector listed |
| User inputs      | D1/GPIO2, D2/GPIO3, D4/GPIO5; Reset                                          |
| Software         | Arduino / ESPHome / TRMNL BYOD                                               |
| Enclosure        | Not included                                                                 |

[Kit parts/specifications](https://wiki.seeedstudio.com/trmnl_7inch5_diy_kit_main_page/), [Arduino electrical examples](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/). The overview lists −40 to 85 °C and a three-month deep-sleep battery scenario; neither establishes that the complete display/battery assembly can operate or charge across that entire range. Use each component's rating and measure the actual duty cycle before making a deployment claim.

## Hardware and connections <a href="#hardware-and-assembly" id="hardware-and-assembly"></a>

### Assemble with power removed

1. Support the glass panel on a flat surface. Unlock the driver FPC latch, insert the supplied cable evenly and close it without sideways force. For the orientation shown in Seeed's kit assembly photo, the FPC metal-contact side faces upward. Match the actual connector's contact side rather than applying that phrase to a reversed extension.
2. Attach the panel through its 24-pin connector/extension. Check both ends and the extension coupler; an apparently locked latch can still hold a partly inserted cable.
3. Set the driver selection jumper to **24Pin–GND**, as documented for the included 7.5-inch panel. A 50-pin Spectra panel is a different board/screen configuration.
4. Confirm the battery plug polarity against the actual board. Connect only the supported single-cell battery, then connect USB-C data/power. Keep the PCB clear of metal surfaces.

Source: [kit assembly and jumper procedure](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/), [driver schematic PDF](https://files.seeedstudio.com/wiki/XIAO_Gadget/TRMNL_Kit_Pic/XIAO_ePaper_driver_board_sch.pdf). Do not reconnect the FPC or change jumpers while powered.

### Pin and resource map

| Signal                    | Actual ESP32-S3 GPIO           | Constraint                                                           |
| ------------------------- | ------------------------------ | -------------------------------------------------------------------- |
| SPI clock / data to panel | SCK7 / MOSI9                   | Fixed display route in this kit profile                              |
| Panel select              | CS44                           | Not E1001 CS10; conflicts with a physical UART RX route using GPIO44 |
| Display command/data      | DC10                           | Dedicated panel control                                              |
| Display reset / busy      | RESET38 / BUSY4                | ESPHome example uses inverted BUSY                                   |
| Buttons                   | KEY0=2, KEY1=3, KEY2=5         | XIAO labels D1/D2/D4; pressed LOW                                    |
| Battery ADC               | GPIO1 / A0                     | Divided voltage; not direct cell input                               |
| ADC enable                | GPIO6 / A5, HIGH while reading | Disable after measurement                                            |
| GPIO domain               | 3.3 V                          | 5 V USB supply does not make GPIO 5 V-tolerant                       |

[ESPHome exact kit pins](https://wiki.seeedstudio.com/ogdiy_kit_works_with_esphome), [Arduino battery/button map](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/). A board label such as D4 is not GPIO4. Keep the physical panel connector and battery switch accessible for diagnosis.

## Software and development resources <a href="#choose-the-application" id="choose-the-application"></a>

| Route           | Exact target / selection                                                                  |
| --------------- | ----------------------------------------------------------------------------------------- |
| Arduino core    | Espressif ESP32 package; current official core target `XIAO_ESP32S3`                      |
| Legacy graphics | Seeed\_GFX; `BOARD_SCREEN_COMBO 502` plus `USE_XIAO_EPAPER_DISPLAY_BOARD_EE04`            |
| Seeed\_GFX2     | Successor library; product/panel selection uses its own API rather than legacy `driver.h` |
| ESPHome         | ESP32-S3 board, `waveshare_epaper`, model `7.50inv2`, kit pin map below                   |
| TRMNL           | Select **TRMNL 7.5-inch (OG) DIY Kit** in the official model-specific flasher/setup flow  |

The kit cookbook calls the hardware preset `XIAO_ESP32S3_PLUS`; the reviewed [official core boards definition](https://github.com/espressif/arduino-esp32/blob/master/boards.txt) supplies **XIAO\_ESP32S3**, with the [S3 variant map](https://github.com/espressif/arduino-esp32/blob/master/variants/XIAO_ESP32S3/pins_arduino.h). Record which core/package you install rather than looking for a nonexistent Plus preset in that package. The legacy example below follows Seeed\_GFX commit `0dfdd7135425be82b5bb4b4b58d74dd51ab29a59`; its current README recommends GFX2 for new development. [Kit cookbook](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/), [graphics source](https://github.com/Seeed-Studio/Seeed_GFX).

## Getting started <a href="#getting-started-with-arduino-one-display-refresh" id="getting-started-with-arduino-one-display-refresh"></a>

### Original one-frame Arduino test

1. Complete the unpowered cable/jumper check. Install Arduino IDE, add `https://espressif.github.io/arduino-esp32/package_esp32_index.json`, install esp32 by Espressif, then select **XIAO\_ESP32S3** and the actual USB port. Enable USB CDC for `Serial` diagnostics; OPI PSRAM is appropriate for image-heavy work.
2. Install the [reviewed Seeed\_GFX source archive](https://github.com/Seeed-Studio/Seeed_GFX/archive/0dfdd7135425be82b5bb4b4b58d74dd51ab29a59.zip). Ensure a second TFT\_eSPI installation is not selected instead. Create `driver.h` beside the sketch:

```cpp
#define BOARD_SCREEN_COMBO 502
#define USE_XIAO_EPAPER_DISPLAY_BOARD_EE04
```

3. Upload this complete original layout check. It deliberately draws once instead of attempting LCD-style animation.

```cpp
#include <Arduino.h>
#include <TFT_eSPI.h>
#ifndef EPAPER_ENABLE
#error Configure the 502 panel and EE04 board in driver.h
#endif
EPaper canvas;
void setup() {
  Serial.begin(115200);
  canvas.begin();
  canvas.setRotation(0);
  canvas.fillScreen(TFT_WHITE);
  canvas.setTextColor(TFT_BLACK);
  canvas.setTextSize(3);
  canvas.drawString("OG kit: first frame", 25, 30);
  canvas.drawRect(4, 4, canvas.width()-8, canvas.height()-8, TFT_BLACK);
  for (int i=0; i<4; ++i)
    canvas.fillRect(25+i*90, 120, 30+10*i, 100, TFT_BLACK);
  canvas.update();
  Serial.println("OG_FRAME_SENT");
}
void loop() { delay(1000); }
```

**Expected result:** one new label, four unequal bars and an unclipped border on the 800×480 panel. If the old image remains, inspect the 502/EE04 configuration, cable contacts, 24Pin jumper and power before adding Wi-Fi. The library API was source-reviewed against its `EPaper` example; no compile or physical refresh was run. [Arduino panel procedure](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/).

### Original button and battery diagnostic

Run this separately from the display test. It uses the actual MCU GPIO values and averages calibrated millivolt reads. The factor 2 follows the documented divider; measure against a meter before relying on it for battery cutoffs.

```cpp
#include <Arduino.h>
constexpr int buttons[] = {2, 3, 5};
void setup() {
  Serial.begin(115200);
  for (int pin : buttons) pinMode(pin, INPUT_PULLUP);
  pinMode(6, OUTPUT); digitalWrite(6, LOW);
  analogReadResolution(12);
  analogSetPinAttenuation(1, ADC_11db);
}
void loop() {
  digitalWrite(6, HIGH);
  delay(10);
  uint32_t sum = 0;
  for (int i=0; i<16; ++i) { sum += analogReadMilliVolts(1); delay(2); }
  digitalWrite(6, LOW);
  Serial.printf("D1=%d,D2=%d,D4=%d,battery_mV=%lu\n",
      digitalRead(2), digitalRead(3), digitalRead(5),
      (unsigned long)(2UL*sum/16UL));
  delay(1000);
}
```

**Expected result:** each pressed button reads 0, and battery voltage is plausible and agrees sufficiently with an independent measurement. A voltage threshold is not a chemically calibrated charge percentage. The manufacturer's raw-ADC example includes a 0.968 correction factor for its setup; that is not a universal calibration constant for your board or for `analogReadMilliVolts()`. [Battery example and circuit reference](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/).

### ESPHome static page, then one live entity <a href="#home-assistant-dashboards-and-power" id="home-assistant-dashboards-and-power"></a>

1. Create a new ESP32-S3 device in Home Assistant's ESPHome Device Builder. Retain your generated API/OTA secrets. Before sleep or screenshot retrieval, use this complete original baseline, replacing the two Wi-Fi secrets in `secrets.yaml`.

```yaml
esphome:
  name: openelab-og-kit
esp32:
  board: seeed_xiao_esp32s3
  framework:
    type: esp-idf
logger:
  baud_rate: 0
api:
ota:
  - platform: esphome
wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
font:
  - file: "gfonts://Roboto"
    id: label_font
    size: 28
spi:
  clk_pin: GPIO7
  mosi_pin: GPIO9
display:
  - platform: waveshare_epaper
    model: 7.50inv2
    cs_pin: GPIO44
    dc_pin: GPIO10
    reset_pin: GPIO38
    busy_pin:
      number: GPIO4
      inverted: true
    update_interval: 300s
    lambda: |-
      it.rectangle(4, 4, 792, 472);
      it.print(25, 40, id(label_font), "OG kit on Home Assistant");
```

2. Validate/compile in Device Builder and install initially over USB. Network log access is available through the API after provisioning; UART logging is disabled here to avoid using a display pin as a serial route.
3. Confirm a settled static page, then add **one** actual `homeassistant` sensor/text\_sensor entity from your installation. Render an unavailable state before data arrives. Only after that add icon glyphs or a monochrome image.

**Expected result:** the local page is stable and a later live value changes after a scheduled refresh. Keep `GPIO44` CS and inverted BUSY4; the reTerminal E1001 map is wrong for this kit. [Official ESPHome kit reference](https://wiki.seeedstudio.com/ogdiy_kit_works_with_esphome).

### Screenshots, TRMNL and sleep

The official ESPHome cookbook also covers fonts/icons, binary image conversion, dashboard screenshots through a Home Assistant screenshot service and a comprehensive sleeping dashboard. Verify the screenshot URL directly first, then its dimensions/orientation and authorization, then display it. A working source dashboard does not prove that the renderer fetched a current image.

For battery operation, establish a wake window long enough for Wi-Fi/API data and the complete display update; only then enable deep sleep and a documented wake source. Keep an awake firmware/configuration for recovery. A device sleeping most of the time cannot accept OTA at arbitrary moments. Measure current with USB and unused peripherals accounted for rather than treating a calendar interval as a runtime guarantee. [ESPHome images and sleep examples](https://wiki.seeedstudio.com/ogdiy_kit_works_with_esphome).

A new OG DIY Kit is documented as shipping with TRMNL firmware; preserve a working factory setup and skip flashing when it is already suitable. For replacement firmware, the manufacturer specifies **TRMNL FW 1.5.12 or newer** and the [TRMNL Web Flasher](https://usetrmnl.com/flash). For TRMNL, follow [Work with TRMNL](https://wiki.seeedstudio.com/reterminal_e10xx_trmnl/): choose the **OG DIY Kit** profile, install its firmware, provision its access point/Wi-Fi and bind that device to the intended TRMNL backend/account. Create one simple plugin/view and verify a fresh timestamp before adding a playlist. BYOD license/account and hosted versus self-hosted requirements belong to the selected TRMNL workflow. The kit is not an entitlement to every third-party service feature. Keep its firmware target separate from enclosed reTerminal profiles.

## Troubleshooting and FAQs <a href="#troubleshooting-and-recovery" id="troubleshooting-and-recovery"></a>

| Symptom                             | Ordered diagnosis / recovery                                                                                                               |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Screen unchanged after upload       | Confirm current application boot, correct board/panel profile, 24Pin–GND jumper, FPC contact side and latch. Re-seat only while unpowered. |
| Serial output absent                | Check native USB CDC selection and actual port; a charge cable is insufficient. Do not claim GPIO44 for UART while it is panel CS.         |
| Button label seems wrong            | Compare D1/GPIO2, D2/GPIO3 and D4/GPIO5; labels and MCU numbers differ.                                                                    |
| Battery shows an impossible voltage | Check ADC enable6, ADC1/GPIO1, divider factor and measurement API; compare a meter before changing thresholds.                             |
| ESPHome source data empty           | Confirm the actual entity, native API connection, `has_state`/availability and update cadence; first render a static string.               |
| OTA never connects                  | Wake or reset during its active window; use USB and a no-sleep sketch if necessary.                                                        |
| Clock example time wrong            | A compile-time clock is a drawing example, not NTP/RTC synchronization. Define a real time source before using it as a clock.              |
| More ghosting over time             | Use the selected driver's documented full/partial update policy; do not assume every refresh mode is valid on another panel.               |

If uploading is blocked by the application, use the XIAO S3 BOOT/reset download procedure with external loads disconnected, reselect its port and upload the known no-sleep baseline. Keep your previous configuration before erasing or changing application families. [Kit recovery FAQs](https://wiki.seeedstudio.com/ogdiy_kit_works_with_esphome).

## Downloads and technical documents <a href="#technical-documents-and-software" id="technical-documents-and-software"></a>

| Resource                                                                                                                    | Use / scope                                                                      |
| --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| [Driver-board schematic PDF](https://files.seeedstudio.com/wiki/XIAO_Gadget/TRMNL_Kit_Pic/XIAO_ePaper_driver_board_sch.pdf) | XIAO ePaper Monitor Kit V1.0, May 2025; CC BY-SA 4.0; original circuit reference |
| [Kit assembly and drawing links](https://wiki.seeedstudio.com/trmnl_7inch5_diy_kit_main_page/)                              | Components, enclosure links and physical assembly                                |
| [Arduino cookbook](https://wiki.seeedstudio.com/ogdiy_kit_works_with_arduino/)                                              | Board jumper, battery, buttons and display API                                   |
| [Seeed\_GFX source archive](https://github.com/Seeed-Studio/Seeed_GFX/archive/0dfdd7135425be82b5bb4b4b58d74dd51ab29a59.zip) | Reviewed legacy example API                                                      |
| [TRMNL ePaper project](https://github.com/Seeed-Projects/Seeed_TRMNL_Eink_Project)                                          | Manufacturer-linked firmware/software resources                                  |
| [ESPHome cookbook](https://wiki.seeedstudio.com/ogdiy_kit_works_with_esphome)                                               | Exact pin map, entities, icons, images and deep sleep                            |
| [TRMNL setup](https://wiki.seeedstudio.com/reterminal_e10xx_trmnl/)                                                         | Select OG DIY Kit rather than another device                                     |

## References and validation <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

Reviewed **24 November 2026** against the kit overview, Arduino/ESPHome/TRMNL cookbooks and the official Espressif core definitions linked above. The driver schematic was read, including its 24-pin/50-pin selection circuit. The original manufacturer illustration is retained; no substitute technical drawing was generated.

**Validation:** source reviewed. Compilation, firmware installation, display refresh, network commissioning, voltage measurements and hardware tests were **not run**. Expected results describe reproduction checkpoints, not observed bench results.
