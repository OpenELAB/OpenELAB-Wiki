# Seeed Studio reTerminal E1002 Development Guide

{% hint style="info" %}
[**View Seeed Studio reTerminal E1002 on OpenELAB**](https://openelab.io/products/seeed-studio-reterminal-e1002-full-color-epaper-display)

**Model/variant:** Seeed Studio reTerminal E1002 · **SKU:** `Seeed-100017057`
{% endhint %}

![Seeed Studio reTerminal E1002 Development Guide](../../.gitbook/assets/reterminal-e1002-development-guide.jpg)

_Manufacturer image: Seeed Studio._ [_Image source_](https://files.seeedstudio.com/wiki/reterminal_e10xx/img/132.jpg)_._

[Product at OpenELAB](https://openelab.io/products/seeed-studio-reterminal-e1002-full-color-epaper-display) · [Manufacturer wiki hub](./)

## Product and applications

**reTerminal E1002, Seeed code 100017057,** is an ESP32-S3 ePaper terminal for color-coded status boards, image frames and low-update signage. Its retained image and intermittent updates suit information that changes slowly. This is a complete terminal, distinct from a bare ePaper panel or a XIAO driver board.

## Hardware specifications

| Item           | E1002                                                              |
| -------------- | ------------------------------------------------------------------ |
| Panel          | 7.3-inch E Ink Spectra 6 full color                                |
| Resolution     | 800 × 480 pixels                                                   |
| Compute        | ESP32-S3, 8 MB PSRAM, 32 MB flash                                  |
| Wireless       | 2.4 GHz Wi-Fi and Bluetooth                                        |
| Battery        | 2000 mAh                                                           |
| Input          | USB-C, 5 V / 1 A                                                   |
| Interaction    | No touchscreen                                                     |
| Other features | Temperature/humidity sensing, buzzer, microSD and expansion header |
| Dimensions     | 176 × 120 × 17 mm without stand                                    |

Source: [E1002 hardware reference](https://wiki.seeedstudio.com/getting_started_with_reterminal_e1002/). Use its schematic and connector-orientation illustration for expansion wiring. A header's supply pin and its GPIO signal voltage are separate specifications. Check the fitted board revision before using a drawing.

## Choose firmware before developing

Use the factory **SenseCraft Seeedash** route for a first visible result. For a local integration, use the supported ESPHome configuration; for custom firmware, use the manufacturer's Arduino/ESP-IDF resources. These are different applications that replace one another when flashed. Export project/configuration data before switching.

The [firmware hub](https://seeed-projects.github.io/OSHW-reTerminal-Series-E-D/) selects the exact device and software route. Do not flash an E1001 image onto E1002 just because both use ESP32-S3. Panel dimensions, driver selection and peripheral pins are model-specific.

## Getting started: deploy one readable test page

Prepare the terminal, a USB data cable/5 V supply, a computer or phone, and a 2.4 GHz Wi-Fi network. This route uses the manufacturer's hosted service and requires the corresponding account. Choose the ESPHome route instead if that dependency does not suit your deployment.

1. Inspect the display/USB connector, attach the stand as instructed, supply power and switch the terminal on. Wake it before setup if it has gone to sleep.
2. With factory firmware, join the access point identified on the terminal's screen. Open its setup page; if automatic redirection fails, use `http://192.168.4.1` while connected to that device access point.
3. Supply the 2.4 GHz network credentials. Wait for the pairing information on the display, then bind the device in [SenseCraft Seeedash](https://sensecraft.seeed.cc/hmi) using the shown code. Treat the code and network credentials as private.
4. Create a simple page containing a large test label, the device model and a manually entered revision number. Avoid adding weather/API widgets until this static page works.
5. Deploy to the selected terminal and allow a full ePaper refresh to finish. Check the label, orientation, edges and revision number physically. Change the revision and redeploy to distinguish a newly transferred page from the image retained by the panel.

The expected result is the new page on the physical device. A retained image after power-off is normal ePaper behavior and does not prove that the processor is still running. Refresh flashing is also normal; judge the final settled image.

## Custom firmware and expansion

For an Arduino first program, use the [manufacturer display cookbook](https://wiki.seeedstudio.com/reterminal_e10xx_with_arduino/) and select the exact model's panel/driver configuration. Start with its simple display example and expected orientation before adding sensors or battery sleep. Record ESP32 core and display-library versions with your sketch.

For Home Assistant, start from the [ESPHome display guide](https://wiki.seeedstudio.com/reterminal_e10xx_esphome/). Add one sensor/value and one display update first; then consider update interval and sleep. A network-connected development configuration can consume far more power than the factory low-duty-cycle application. Neither battery capacity nor an advertised months-long runtime guarantees your application's runtime.

For external hardware, use the model's expansion pin map and schematic. Add one interface at a time, check signal voltage and shared pins, and verify the display still refreshes after each change. Avoid driving all header pins as generic outputs: some may be shared with fitted hardware.

## Firmware recovery

Use the firmware hub's exact model selection and a supported Web Serial browser with a data cable. Follow the model's documented BOOT/reset sequence if its serial port does not appear. A firmware flash can replace the application and configuration; do not use full-chip erase as the default troubleshooting step.

After restoring the intended firmware, repeat the single-page test. Keep a copy of the working configuration and version before adding integrations.

## Troubleshooting and FAQ

| Symptom                                      | Check and next step                                                                                                     |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Device access point is missing               | Wake the terminal, check power and confirm that the factory setup application is installed.                             |
| Cannot join home/office Wi-Fi                | Confirm 2.4 GHz availability and credentials; check captive portal or enterprise-network requirements separately.       |
| Serial port missing                          | Use a data cable; check the model's USB driver and BOOT/reset instructions.                                             |
| Page appears unchanged                       | Deploy a unique revision label, select the correct device, wake it and wait for the full refresh.                       |
| Wrong colors/orientation or clipped graphics | Confirm exact model, panel driver and canvas dimensions before changing application drawing code.                       |
| microSD is not mounted                       | Check the documented capacity/format; the guides specify FAT32 and cards up to 32 GB. Back up data before reformatting. |
| Battery life is shorter than expected        | Measure refresh frequency, Wi-Fi active time, peripherals and sleep behavior in your own firmware.                      |

The color panel requires a comparatively long full refresh. Firmware support for a platform does not guarantee that platform uses all panel colors; check the current TRMNL/color support before planning a color application.

## Technical documents and software

| Resource                                                                                                                  | Use                                          |
| ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| [Model setup and pin map](https://wiki.seeedstudio.com/getting_started_with_reterminal_e1002/)                            | Exact hardware, controls and recovery        |
| [Model schematic](https://files.seeedstudio.com/wiki/reterminal_e10xx/res/202004321_reTerminal_E1002_V1_2_SCH_251120.pdf) | Electrical reference; compare board revision |
| [Enclosure STEP model](https://files.seeedstudio.com/wiki/reterminal_e10xx/res/reTerminal_E1001_E1002_3D.stp)             | Mechanical design reference                  |
| [Firmware and SDK selection](https://seeed-projects.github.io/OSHW-reTerminal-Series-E-D/)                                | Select exact model and application           |
| [Arduino display cookbook](https://wiki.seeedstudio.com/reterminal_e10xx_with_arduino/)                                   | First display sketch and model selection     |
| [ESPHome display cookbook](https://wiki.seeedstudio.com/reterminal_e10xx_esphome/)                                        | Home Assistant/local application route       |
| [Seeedash documentation](https://sensecraft-hmi-docs.seeed.cc/en/)                                                        | Factory UI design and deployment             |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.

## Official documentation and development resources

Use [Getting Started with reTerminal E1002](https://wiki.seeedstudio.com/getting_started_with_reterminal_e1002/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                             |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/reterminal_e10xx/res/reTerminal_E1001_E1002_3D.stp) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
