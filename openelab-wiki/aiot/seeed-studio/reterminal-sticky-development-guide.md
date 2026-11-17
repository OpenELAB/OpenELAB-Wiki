---
description: >-
  Model scope, hardware, first-run tutorial, firmware, troubleshooting and
  official development resources.
---

# Seeed Studio reTerminal Sticky Development Guide

![Seeed Studio reTerminal Sticky Development Guide](../../.gitbook/assets/reterminal-sticky-development-guide.png)

_Manufacturer image: Seeed Studio._ [_Image source_](https://files.seeedstudio.com/wiki/reterminal_sticky/img/developer_docs/Hardware_Diagram.png)_._

[Product at OpenELAB](https://openelab.io/products/seeed-studio-reterminal-sticky-3-97-inch-ai-magnetic-epaper-display) · [Manufacturer wiki hub](./)

### Product and applications

**reTerminal Sticky, Seeed code 100056818**, is a card-sized ESP32-S3 ePaper terminal with magnetic mounting and capacitive touch. It suits a compact status display, room label, note interface or battery-powered information panel. Voice/cloud capabilities depend on the selected application; the onboard microphone alone does not supply a conversational AI model.

### Hardware specifications

| Item              | Documented configuration                                    |
| ----------------- | ----------------------------------------------------------- |
| Controller/memory | ESP32-S3; 8 MB PSRAM; 32 MB external flash                  |
| Display           | 3.97-inch monochrome ePaper, 800 × 480, four gray levels    |
| Interaction       | Capacitive touch; AI/power, Up and Down buttons; reset hole |
| Sensors           | SHT40 temperature/humidity; LSM6DS3TR-C IMU; PCF8563 RTC    |
| Audio/storage     | PDM microphone, buzzer and microSD                          |
| Network           | 2.4 GHz Wi-Fi and BLE                                       |
| Battery/input     | 750 mAh battery; USB-C power/data, standard 5 V USB supply  |
| Enclosure         | 106 × 65.5 × 7.3 mm; 70 g; IP40                             |

The [hardware reference](https://www.seeedstudio.com/sticky/docs/en/device-guide/hardware-overview/) maps the display's SPI, touch's I2C and peripheral power/control signals. Sticky is not waterproof. Keep its magnetic mounting and glass front in mind when designing a fixture; use the official CAD rather than another reTerminal enclosure.

### Software choices

The factory Seeedash application is a ready-to-use route for pairing and content. Arduino offers display/peripheral development; ESP-IDF offers the manufacturer's fuller dashboard demo and firmware structure. Third-party applications in the Playground have their own capabilities, licenses and server requirements. Flashing any of them replaces the current application; preserve needed settings/content first.

### Getting started with ESP-IDF: build the official dashboard

Prepare Sticky, a USB data cable, a Windows/Linux/macOS computer, and an **ESP-IDF v5.4** terminal. The [manufacturer ESP-IDF tutorial](https://www.seeedstudio.com/sticky/docs/en/device-guide/esp-basics/) identifies v5.4 as its hardware-tested upstream baseline; OpenELAB has not repeated that bench test.

In that terminal:

```bash
git clone https://github.com/Seeed-Projects/sticky-esp-idf-dashboard.git
cd sticky-esp-idf-dashboard
git rev-parse HEAD
idf.py set-target esp32s3
idf.py build
```

Save the displayed commit and build environment. Connect the data cable and identify its serial port. Replace `PORT` below with the actual port, for example the correct COM port on Windows:

```bash
idf.py -p PORT flash monitor
```

Allow the first complete panel refresh to finish. Expected behavior from this demo is a Home page followed by navigable sensor, battery, note, IMU and microphone pages using buttons or swipe gestures. Check an actual changing sensor/interaction result as well as the retained image. Exit the serial monitor with **Ctrl+]**.

The current official demo handles the supported SSD1677/SSD2677 controller variants automatically. Use that maintained board configuration instead of manually forcing a generic display driver. A successful build does not prove the hardware works; the physical display/touch/peripheral checks are separate steps.

### Arduino and factory setup routes

The [Arduino guide](https://www.seeedstudio.com/sticky/docs/en/device-guide/arduino-basics/) uses **Seeed\_GFX2**, the **XIAO\_ESP32S3** preset and its Sticky-specific HelloWorld example. Follow its PSRAM requirements when adding grayscale or SD-image examples. Select the actual CH343 serial port; this is different from assuming a native USB-CDC connection.

To use the factory experience, follow the [official quick-start](https://www.seeedstudio.com/sticky/docs/en/quick-start/) to power on, pair the matching serial number in the Seeedash app and join 2.4 GHz Wi-Fi. Use the app/device's documented update flow for that firmware. The [Playground firmware page](https://www.seeedstudio.com/sticky/playground/firmware/) lists alternative applications; review the selected application's data/backup and restore instructions before switching.

### Troubleshooting and FAQ

| Symptom                                  | Check and next action                                                                                                                          |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Power present but no serial port         | Data cable, actual CH343 bridge/driver, OS permissions and another USB port.                                                                   |
| Build cannot find ESP-IDF components     | Confirm the v5.4 environment and project root; record repository commit and dependency-resolution output.                                      |
| Screen unchanged after flashing          | Reset into the new application, inspect serial output and wait for full refresh; an old ePaper image can remain without a running application. |
| Grayscale/SD example fails               | Check the Arduino guide's PSRAM setting, matching library and model-specific example.                                                          |
| Touch is not responding                  | Verify the selected firmware supports touch and uses the Sticky configuration; test its upstream example first.                                |
| Factory pairing selects the wrong device | Match the serial number shown on Sticky; keep the phone close during pairing.                                                                  |
| Need the original application            | Use the official Sticky restoration/update route; back up needed content before application replacement.                                       |

### Technical documents and software

| Resource                                                                                                             | Use                                    |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| [Hardware and pin map](https://www.seeedstudio.com/sticky/docs/en/device-guide/hardware-overview/)                   | Exact signals and board architecture   |
| [Schematic](https://files.seeedstudio.com/wiki/reterminal_sticky/res/reTerminal_Sticky_Schematic_diagram_260609.pdf) | Electrical reference                   |
| [Official STEP model](https://files.seeedstudio.com/wiki/reterminal_sticky/res/reTerminal_Sticky_3D.stp)             | Mechanical integration                 |
| [ESP-IDF tutorial](https://www.seeedstudio.com/sticky/docs/en/device-guide/esp-basics/)                              | v5.4 dashboard workflow                |
| [Dashboard SDK/example](https://github.com/Seeed-Projects/sticky-esp-idf-dashboard)                                  | Source project used in this guide      |
| [Arduino tutorial](https://www.seeedstudio.com/sticky/docs/en/device-guide/arduino-basics/)                          | Sticky HelloWorld and display library  |
| [Factory quick-start](https://www.seeedstudio.com/sticky/docs/en/quick-start/)                                       | Pairing and normal application setup   |
| [Firmware Playground](https://www.seeedstudio.com/sticky/playground/firmware/)                                       | Application selection and distribution |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
