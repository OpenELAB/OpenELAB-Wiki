---
description: >-
  Select13.3-inch60-pin EE02 versus7.3-inch50-pin EE04, verify panel power/model
  and run an original six-color GFX2 chart.
---

# Seeed Studio Spectra 6 Panels and XIAO ePaper Kit Development Guide

{% hint style="info" %}
[**View Seeed 13.3-inch Spectra 6 panel on OpenELAB**](https://openelab.io/products/seeed-studio-13-3-inch-epaper) · **SKU:** `Seeed-100088646` · 1200×1600, 60-pin panel; EE02 controller is separate.

[**View Seeed 7.3-inch Spectra 6 panel on OpenELAB**](https://openelab.io/products/seeed-studio-7-3-epaper) · **SKU:** `Seeed-100064541` · 800×480, 50-pin panel; EE04 controller is separate.

[**View Seeed XIAO 7.3-inch ePaper DIY Kit on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-epaper-7-3-inch-diy-kit) · **SKU:** `Seeed-E25102101` · EE04 + 7.3-inch panel + 2.4 GHz antenna; no battery implied by a battery connector.
{% endhint %}

## Product overview <a href="#product-boundaries-and-applications" id="product-boundaries-and-applications"></a>

These are two six-pigment ePaper panels and one controller/panel bundle. The bare 13.3-inch panel is driven by **EE02**, while the 7.3-inch panel and DIY kit use **EE04**. A panel cannot be connected directly to MCU GPIO merely because its interface is called SPI: the driver board also supplies power sequencing and panel rails. They are not enclosed reTerminal E1002/E1004 units. [Manufacturer selection matrix](https://wiki.seeedstudio.com/seeed_epaper_displays/), [EE02](https://wiki.seeedstudio.com/getting_started_with_ee02), [EE04](https://wiki.seeedstudio.com/epaper_ee04/).

## Applications

Use the panels for color labels, information boards and low-refresh photo displays. Design images for black, white, red, yellow, green and blue pigment; smooth RGB gradients require quantization or dithering. A six-color frame is not a six-channel sensor reading, and a static image is not proof that a network service is still online.

For mechanical integration, support the complete glass/module, keep torsion off the flex and provide clearance behind the driver. Match the exact panel drawing before cutting a bezel; active area and outline are different dimensions. Keep a timestamp/validity indicator on data dashboards.

## Specifications

### Exact SKU and hardware differences

| Parameter                        | 100088646: 13.3-inch panel                        | 100064541: 7.3-inch panel                                | E25102101: 7.3-inch DIY kit                     |
| -------------------------------- | ------------------------------------------------- | -------------------------------------------------------- | ----------------------------------------------- |
| Panel / current driver reference | T133A01, A1 datasheet                             | ED2208 / EL073TF1 family                                 | Same 7.3-inch panel class with EE04             |
| Pixels                           | 1200×1600                                         | 800×480                                                  | 800×480                                         |
| Active area                      | 202.8×270.4 mm                                    | 160×96 mm                                                | Panel as at left                                |
| Pixel pitch                      | 0.169×0.169 mm                                    | 0.200×0.200 mm                                           | Panel as at left                                |
| Connector                        | **60 pins**, 0.5 mm                               | **50 pins**, 0.5 mm                                      | EE04's 50-pin connector; select 50-pin jumper   |
| Outline                          | 208.8×284.7×0.85 mm, A1 module drawing            | 170.2×111.2 mm; thickness/weight vary by source revision | Separate board and panel; no finished enclosure |
| External controller              | EE02, separate                                    | EE04, separate                                           | EE04 included                                   |
| Panel accessory scope            | Listing includes 60-pin adapter and FFC extension | Panel-only listing                                       | EE04, 7.3-inch panel, 2.4 GHz FPC antenna       |

Identity/contents: verified OpenELAB links in the opening callout and their exact SKU/variant records. Model-specific documents: [13.3-inch manufacturer page](https://www.seeedstudio.com/13-3inch-Six-Color-eInk-ePaper-Display-with-1200x1600-Pixels-p-6569.html), [7.3-inch manufacturer page](https://www.seeedstudio.com/7-3inch-Six-Color-eInk-ePaper-Display-with-800x480-Pixels-p-6567.html), [T133A01 A1 datasheet](https://files.seeedstudio.com/wiki/Epaper/EE02/13_3_E6_eInk_Display_module_Datasheet.pdf), [7.3-inch tentative datasheet](https://files.seeedstudio.com/wiki/Other_Display/7.3-E6-color/7.3_E6_eInk_%20Display_%20module_%20Datasheet.pdf). The 7.3-inch retail table contains inconsistent weights; do not design a fixture from those conflicting numbers. Its older tentative datasheet leaves thickness/weight unspecified.

### Power and temperature are model-dependent

| Domain                    | Documented limit / reference condition                                                         |
| ------------------------- | ---------------------------------------------------------------------------------------------- |
| EE02 input                | 5 V USB-C or supported 3.7 V single-cell battery; board operates at 3.3 V                      |
| EE04 input                | USB-C or supported 3.7 V single-cell battery; JST 2.0 mm connector                             |
| T133A01 VDD / VDDIO       | 2.4–3.6 V, typical3.3 V in A1 DC characteristics at25 °C                                       |
| ED2208 VDD                | 2.5–3.6 V, typical3.0 V in tentative DC table                                                  |
| Panel temperature         | Manufacturer panel documents give 0–50 °C operation; driver-board range is a separate rating   |
| Frame storage, calculated | 4 bits/pixel needs960,000 bytes at1200×1600 or192,000 bytes at800×480, excluding extra buffers |

Sources: [EE02 board](https://wiki.seeedstudio.com/getting_started_with_ee02), [EE04 board](https://wiki.seeedstudio.com/epaper_ee04/), T133A01 A1 pp.4/11–12 and ED2208 tentative electrical section in the linked PDFs. **VDD is not the only panel rail.** Absolute maximum tables are damage limits, not target operating values. Use the matched driver board rather than wiring USB5 V to a panel pin.

## Hardware and connections <a href="#hardware-documents-and-software" id="hardware-documents-and-software"></a>

### 13.3-inch panel on EE02

EE02 has a dedicated **60-pin, 0.5 mm** display connector. Match the received panel label to **T133A01** and the current supported EE02 profile before powering. The 13.3-inch model needs **two chip-select signals**; a generic one-CS display example can update only part of the image. Install the supplied adapter/extension according to connector contact orientation, with both board and battery disconnected.

The [EE02 schematic](https://files.seeedstudio.com/wiki/Epaper/EE02/202000224_XIAO_ePaper_Display_Board_EE02_V1.pdf) contains the 60-pin power/logic circuit and revision history; the [A1 panel drawing](https://files.seeedstudio.com/wiki/Epaper/EE02/13_3_E6_eInk_Display_module_Datasheet.pdf) defines the FPC geometry and pins. The schematic explicitly describes the move from earlier connector arrangements to 60 pins. Connector count/pitch alone does not prove another panel is compatible.

### 7.3-inch panel or DIY kit on EE04

With power removed, fit the **50-pin** panel into the correct EE04 connector, check contact side and fully close the latch. Set the selector to the **50-pin** side. The nearby 24-pin connector is for other supported panels, including monochrome models; it is not a substitute for this Spectra 6 panel. The DIY SKU includes the EE04 and antenna; the panel-only SKU does not.

Use the [EE04 V1.2 schematic](https://files.seeedstudio.com/wiki/Epaper/EE04/XIAO_ePaper_Display_Board_EE04_SCH_V1.2.pdf), [official board orientation diagram](https://files.seeedstudio.com/wiki/Epaper/EE04/hardwareoview.png) and [7.3-inch module datasheet](https://files.seeedstudio.com/wiki/Other_Display/7.3-E6-color/7.3_E6_eInk_%20Display_%20module_%20Datasheet.pdf). EE04's XIAO ESP32-S3 version does **not** provide NFC merely because another board/pin drawing mentions NFC.

### Driver-board signals and limits

| Function       | EE04 V1.2 reference                                    | EE02 boundary                                                                                |
| -------------- | ------------------------------------------------------ | -------------------------------------------------------------------------------------------- |
| Panel SPI      | SCK7, MOSI9, CS44, DC10, RESET38, BUSY4                | Use the EE02 dual-CS product profile and schematic; do not transplant the EE04 pin constants |
| User buttons   | KEY0 GPIO2, KEY1 GPIO3, KEY2 GPIO5                     | Three board buttons; identify in the exact board drawing                                     |
| Battery sample | ADC GPIO1; enable GPIO6 HIGH                           | Matched board circuit/profile; verify revision before adopting a calibration constant        |
| Power          | USB input / single-cell connector; no live FPC changes | Same input classes; different screen power circuit                                           |
| Host GPIO      | 3.3 V domain                                           | 3.3 V domain; panel high-voltage rails generated on board                                    |

[EE04 hardware/software](https://wiki.seeedstudio.com/epaper_ee04/), [EE02 hardware/software](https://wiki.seeedstudio.com/getting_started_with_ee02). On both boards, perform USB-based bring-up before battery duty-cycle optimization. Do not hot-plug FPC, switch connector selection while powered, or probe adjacent fine-pitch high-voltage panel pins with unsecured leads.

## Software and development resources

| Hardware         | Seeed\_GFX2 exact product selection     | First example                                                         |
| ---------------- | --------------------------------------- | --------------------------------------------------------------------- |
| 13.3-inch + EE02 | `Seeed_Product::Seeed_ePaper_13INCH3_C` | EE02 →13.3-inch →`13_3_inch_Spectra6_HelloWorld`                      |
| 7.3-inch + EE04  | `Seeed_Product::Seeed_ePaper_7INCH3_C`  | EE04 →7.3-inch Spectra6 →`7_3_inch_Spectra6_HelloWorld`               |
| E25102101 kit    | Same EE04 7.3-inch selection            | Same example; included board/antenna, not a different firmware target |

The source examples were read from [Seeed\_GFX2](https://github.com/Seeed-Studio/Seeed_GFX2) on24 November2026; their file blob identities were respectively `31c02e9b85e413a005bb649b97f9ffc6d8b5c739` and `a7f26e82d847d492a37edbe81ab6a78873652d91`. Use the same library snapshot/product catalog rather than mixing legacy TFT\_eSPI `driver.h` with GFX2.

The board wikis name an S3 Plus preset; the current official Espressif core exposes **XIAO\_ESP32S3**. Install the intended package, enable **OPI PSRAM**, verify the actual memory configuration, and record core/library versions. A product-page statement of Arduino/MicroPython compatibility is not proof that every generic MicroPython framebuffer/driver supports these controllers; the on-page runnable baseline is the verified manufacturer GFX2 route.

## Getting started <a href="#first-display-test" id="first-display-test"></a>

### Prerequisites and original six-color test

1. Identify panel label, exact board and connector/jumper. Bare-panel purchasers must provide the matching EE02 or EE04. Connect the antenna before wireless testing; use USB data/power for the first display result.
2. Install Arduino IDE, Espressif's ESP32 package using `https://espressif.github.io/arduino-esp32/package_esp32_index.json`, and [Seeed\_GFX2](https://github.com/Seeed-Studio/Seeed_GFX2). Select **XIAO\_ESP32S3**, observed port and **OPI PSRAM**. Remove header/library ambiguity by inspecting the compiler's selected library path.
3. Save this complete original sketch. Set `PANEL_13IN3` to **1 only for T133A01+EE02**, or **0 for ED2208+EE04**, including E25102101. Upload once and wait for the complete refresh.

```cpp
#include <Arduino.h>
#include <Seeed_GFX.h>
#define PANEL_13IN3 0
#if PANEL_13IN3
Seeed_GFX screen(Seeed_Product::Seeed_ePaper_13INCH3_C);
#else
Seeed_GFX screen(Seeed_Product::Seeed_ePaper_7INCH3_C);
#endif
void setup() {
  Serial.begin(115200);
  if (!screen.begin()) {
    Serial.println(screen.lastResult().message);
    return;
  }
  const uint16_t inks[] = {TFT_BLACK, TFT_WHITE, TFT_RED,
                           TFT_YELLOW, TFT_GREEN, TFT_BLUE};
  screen.fillScreen(TFT_WHITE);
  screen.setTextColor(TFT_BLACK);
  screen.setTextSize(3);
  screen.drawString("Spectra 6: geometry check", 25, 25);
  int width = screen.width(), height = screen.height();
  int band = (width-40)/6;
  for (int i=0; i<6; ++i) {
    int x = 20+i*band;
    screen.fillRect(x, 100, band-8, height/3, inks[i]);
    screen.drawRect(x, 100, band-8, height/3, TFT_BLACK);
  }
  screen.drawRect(3, 3, width-6, height-6, TFT_BLACK);
  const GfxResult result = screen.refresh();
  if (!result) Serial.println(result.message);
  else Serial.printf("FRAME_SENT %dx%d\n", width, height);
}
void loop() { delay(1000); }
```

**Expected result:** black, white, red, yellow, green and blue swatches in that order, a complete border and the expected resolution/orientation. For13.3 inches, inspect **both halves**; a partial image is not a successful result. Firmware messages are prospective checkpoints, not observed logs. [EE02 example route](https://wiki.seeedstudio.com/getting_started_with_ee02), [EE04 example route](https://wiki.seeedstudio.com/epaper_ee04/).

4. Change the label, upload again and verify that the image actually changes. Keep the working source and a photograph before adding network/SD features. Avoid rapid repeated refreshes during debugging; rendering to a buffer is distinct from completing a panel refresh.

### EE04 buttons and battery inspection

After a working frame, run a separate small button test with `INPUT_PULLUP` on GPIO2/3/5; pressed reads LOW. For battery measurement, drive GPIO6 HIGH, allow the measurement circuit to settle, sample GPIO1 and disable it afterward. Verify the board's divider and ADC calibration against a meter before reporting volts or state of charge. The EE04 example's raw conversion scale is a specific example, not a portable battery calibration.

A single-cell battery is optional and is not listed in E25102101's packing list. Inspect connector polarity, cell protection and the actual board charging circuit before connection. Do not apply the unrelated reTerminal battery ADC-enable21/40 map to EE04. [EE04 buttons/battery source](https://wiki.seeedstudio.com/epaper_ee04/).

### SenseCraft Seeedash setup

1. For **EE04**, select the board **and 7.3-inch Spectra6 screen** in the supported Seeedash firmware tool before flashing. The board wiki's screenshots use a 7.5-inch monochrome panel; do not choose that firmware merely to match the screenshot. A new generic EE04 can remain blank until a panel-specific image is installed.
2. **EE02** is documented as shipped with Seeedash firmware for13.3 inches. If the current firmware is appropriate, keep it; otherwise select the EE02/13.3 profile rather than a reTerminal image.
3. Join the device AP displayed after the matching firmware boots, open its provisioning portal, select an authorized2.4 GHz network and bind the displayed device/pairing code in [Seeedash](https://sensecraft.seeed.cc/hmi). Use the model-specific wiki for current buttons/AP details rather than assuming identical factory behavior across both boards.
4. Deploy a model-sized six-color label/template and verify a fresh update on the intended physical panel. Only then adjust the refresh interval and consider battery sleep.

**Expected result:** correctly oriented cloud-delivered content, not only an online-device badge. The board's USB/GPIO configuration and panel waveform remain model-specific even though the dashboard service is shared. [EE02 Seeedash flow](https://wiki.seeedstudio.com/getting_started_with_ee02), [EE04 Seeedash flow](https://wiki.seeedstudio.com/epaper_ee04/).

### Image pipeline and custom-driver boundary

First resize/crop to the intended canvas, quantize to the six physical inks and render a known color chart. Compare nearest-color and a chosen dither method before testing photographs. A large RGB888 source plus error-diffusion scratch buffers can exceed available PSRAM; a packed4-bit framebuffer calculation does not include decoder, network or secondary buffers. Use a small source or ordered dithering if allocation fails.

For a custom bare-panel driver, follow the exact module's command table, BUSY timing, dual-CS routing where applicable and power-on/off sequence. The matched board/library is the supported first-run route here. Do not borrow an E1004 integration's enclosure pin map or an E1002 controller merely because the panel dimensions look similar. Confirm the received label/revision before modifying waveforms.

## Troubleshooting and FAQs <a href="#faqs-and-recovery" id="faqs-and-recovery"></a>

| Symptom                         | Ordered diagnosis / recovery                                                                                                      |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| New EE04 is blank               | First install exact panel-specific firmware; the generic board may have no screen-specific factory app.                           |
| 13.3-inch shows one half        | Verify T133A01 profile, two chip selects, matching EE02 revision and full FPC insertion; stop using a generic single-CS driver.   |
| 7.3-inch wrong colors           | Check 50-pin selection, ED2208 profile and six-ink conversion; 7.5-inch monochrome firmware is incompatible.                      |
| Serial works, panel does not    | Inspect model/profile, panel power, cable contact side and OPI PSRAM. USB communication does not verify panel rails.              |
| Wi-Fi works, stale image        | Confirm exact physical device, latest content timestamp and full refresh completion. Test a local chart before network rendering. |
| Memory failure                  | Enable PSRAM and reduce decoder/scratch buffers; a4-bit final frame is smaller than an RGB image pipeline.                        |
| Battery results implausible     | Check exact board ADC/enable/divider, actual battery and independent measurement before applying a cutoff.                        |
| Need a raw pin-for-pin adapter? | Verify complete power/logic mapping in both drawings; matching pitch/count alone is insufficient.                                 |

Recover with the correct board's BOOT/reset upload sequence and the known minimal sketch, disconnecting battery/peripherals as its documentation requires. Back up firmware/configuration first; reset/erase is not a remedy for a physically reversed FPC. The old13.3-inch retail PDF and upgrade-PCN URLs returned access errors during review; the readable EE02-linked **T133A01 A1** document is used for this scope. A differently labelled received panel needs its own matched specification before custom driver work.

## Downloads and technical documents <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

| Resource                                                                                                                                            | Exact scope / access                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [T133A01 A1 module datasheet](https://files.seeedstudio.com/wiki/Epaper/EE02/13_3_E6_eInk_Display_module_Datasheet.pdf)                             | Readable34-page document, revision A1,24April2025; geometry,60-pin interface, electrical and sequencing |
| [7.3-inch ED2208-family datasheet](https://files.seeedstudio.com/wiki/Other_Display/7.3-E6-color/7.3_E6_eInk_%20Display_%20module_%20Datasheet.pdf) | Tentativev0.1,11October2023; linked as original E Ink document, no drawings/prose republished here      |
| [EE02 schematic PDF](https://files.seeedstudio.com/wiki/Epaper/EE02/202000224_XIAO_ePaper_Display_Board_EE02_V1.pdf)                                | V1.0;60-pin circuit; Seeed CC BY-SA4.0                                                                  |
| [EE02 SCH/PCB ZIP](https://files.seeedstudio.com/wiki/Epaper/EE02/XIAO_ePaper_Display_Board_EE02_V1.0_final_SCH_and_PCB_251202.zip)                 | Manufacturer-listed design package                                                                      |
| [EE04 V1.2 schematic PDF](https://files.seeedstudio.com/wiki/Epaper/EE04/XIAO_ePaper_Display_Board_EE04_SCH_V1.2.pdf)                               | 24/50-pin selection and host/power circuits; CC BY-SA4.0                                                |
| [EE04 V1.2 SCH/PCB ZIP](https://files.seeedstudio.com/wiki/Epaper/EE04/XIAO_ePaper_Display_Board_EE04_V1.2_SCH\&PCB.zip)                            | Manufacturer-listed design package                                                                      |
| [GFX2 examples/source](https://github.com/Seeed-Studio/Seeed_GFX2)                                                                                  | Choose exact EE02/13.3 or EE04/7.3 product                                                              |
| [Firmware and hardware collection](https://github.com/Seeed-Projects/OSHW-reTerminal-Series-E-D)                                                    | Match board/panel before choosing an image                                                              |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November2026** against the live exact-SKU storefronts, [manufacturer panel matrix](https://wiki.seeedstudio.com/seeed_epaper_displays/), [EE02](https://wiki.seeedstudio.com/getting_started_with_ee02), [EE04](https://wiki.seeedstudio.com/epaper_ee04/), model-specific example source and the documents above. Important panel drawings/electrical pages and driver schematics were visually inspected. The proprietary E Ink document remains an original-source link; its full protected prose/examples/figures are not reproduced.

**Validation:** source reviewed. Compilation, flashing, panel connection, power sequencing, refresh and hardware tests were **not run**. The original chart is API-reviewed; expected results are reproduction checkpoints. No claim is made that a generic MicroPython binary or another panel revision was tested.
