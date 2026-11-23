---
description: >-
  XIAO ESP32C3 hardware and power reference with retained diagrams, boot-pin
  constraints and a link to the consolidated development guide.
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# XIAO ESP32C3 Hardware Reference

{% hint style="info" %}
[**View Seeed Studio XIAO ESP32C3 on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-esp32c3)

**Model:** XIAO ESP32C3 · **SKU:** `Seeed-113991054` · This retained URL is the hardware reference. Use the [main development guide](xiao-esp32-c3-wifi.md) for complete programming, radio, battery, sleep and recovery procedures.
{% endhint %}

## Description

XIAO ESP32C3 combines a single-core 160 MHz RISC-V ESP32-C3, 4 MB flash, 400 KB SRAM, 2.4 GHz Wi-Fi and Bluetooth LE with eleven exposed I/O and a single-cell charging circuit. It has no hardware floating-point unit and no general-purpose onboard Blink LED. Its USB interface provides Serial/JTAG; CircuitPython does not expose a CIRCUITPY mass-storage drive on this chip. [Chip data sheet](https://files.seeedstudio.com/wiki/XIAO_WiFi/Resources/esp32-c3_datasheet.pdf), [CircuitPython board reference](https://circuitpython.org/board/seeed_xiao_esp32c3/).

## Specifications

| Integration item         | Scope / limit                                                           |
| ------------------------ | ----------------------------------------------------------------------- |
| Logic and ADC domain     | 3.3 V; analog measurable range also depends on attenuation              |
| Initial supply           | USB5 V; distinguish VBUS, regulated3V3 and battery contacts             |
| Size                     | 21 ×17.8 mm in Seeed's board reference                                  |
| Reliable first ADC route | A0–A2 on ADC1; D3/GPIO5 is ADC2 and has a documented reliability caveat |
| External interfaces      | D4/D5 I2C, D6/D7 UART, D8/D9/D10 SPI                                    |
| Revision reference       | v1.3 schematic dated15 January2026; check received board                |

[Schematic](https://files.seeedstudio.com/wiki/XIAO_WiFi/Resources/XIAO_ESP32C3_v1.3_SCH_260116.pdf) and [exact Arduino variant](https://github.com/espressif/arduino-esp32/blob/master/variants/XIAO_ESP32C3/pins_arduino.h) establish routes. This hardware reference and the main guide describe the **same purchased SKU**, not two separately sold products.

## Hardware overview

Use the [main guide's full pin table and original front/back diagrams](xiao-esp32-c3-wifi.md#hardware-and-connections) when wiring. D0/A0→GPIO2, D1/A1→3, D2/A2→4, D3→5, D4→6, D5→7, D6→21, D7→20, D8→8, D9→9, D10→10. Pin labels in code are not interchangeable with native numbers from another XIAO model.

The included antenna attaches to U.FL/IPEX. The back pads include battery contacts and debug signals. A shield's SWD spring contacts do not establish an ESP32-C3-compatible debug path. Disconnect power before fitting a shield or soldering contacts.

## Power Pins

VBUS/5V is the USB rail,3V3 is regulated output and GND is the common reference. The v1.3 drawing includes a 700 mA-rated regulator and 500 mA USB fuse; the usable external-load budget also includes supply, temperature and the board's own current. The wiki's500 mA test condition and 700 mA regulator statement are not an unconditional load guarantee. Never apply5 V to an I/O simply because USB or a Grove module uses5 V supply.

Battery contacts support the documented single-cell arrangement. Verify polarity, cell charging requirements and actual board revision. Do not create a capacity percentage from a nonexistent onboard battery ADC. The [main battery workflow](xiao-esp32-c3-wifi.md#battery-usage) explains an optional external divider, calibration and its pin/boot implications.

## Strapping Pins

D0/GPIO2, D8/GPIO8 and D9/GPIO9 affect boot configuration; D9 also serves BOOT. Check peripheral loading during reset. For upload recovery, disconnect external wiring and hold BOOT while connecting USB, then release and reselect the observed port. A continually forced strap level can prevent a good image from starting.

## Development routes

The [main guide](xiao-esp32-c3-wifi.md) contains complete Arduino LED/ADC/PWM/UART/OLED/Wi-Fi/BLE examples, battery and sleep procedures, plus PlatformIO, CircuitPython, NuttX, Zephyr and ESPHome paths. Use one exact framework/target and a known first result before combining peripherals. Existing URLs are retained for readers/bookmarks; development instructions are maintained in that one main guide.

## Official documentation and development resources

| Resource                                                                                                         | Use                                            |
| ---------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| [Official product wiki](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/)                              | Product identity, original galleries and files |
| [v1.3 schematic](https://files.seeedstudio.com/wiki/XIAO_WiFi/Resources/XIAO_ESP32C3_v1.3_SCH_260116.pdf)        | Power, battery and pin circuit                 |
| [Main OpenELAB guide](xiao-esp32-c3-wifi.md)                                                                     | Complete consolidated development procedures   |
| [Framework variant](https://github.com/espressif/arduino-esp32/blob/master/variants/XIAO_ESP32C3/pins_arduino.h) | Arduino aliases and bus defaults               |

## Existing illustrations

<figure><img src="../../.gitbook/assets/image (987).png" alt="Retained OpenELAB XIAO ESP32C3 reference illustration"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (988).png" alt="Retained OpenELAB XIAO ESP32C3 reference illustration"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (989).png" alt="Retained OpenELAB XIAO ESP32C3 reference illustration"><figcaption></figcaption></figure>

![Retained OpenELAB XIAO ESP32C3 reference illustration](https://files.seeedstudio.com/wiki/XIAO_WiFi/20.png)

## References and validation

Hardware/framework sources reviewed23 November 2026. Existing page ID/URL and illustrations are retained; the main guide contains the consolidated procedures. Source review is not a build or bench test. No flashing, battery or physical validation was performed for this revision.
