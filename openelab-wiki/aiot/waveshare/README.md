---
description: >-
  Develop Waveshare Jetson and ESP32 boards, displays and interfaces with exact
  carrier selection, pinouts, first-result workflows and recovery.
---

# Waveshare

Waveshare supplies development boards, displays, cameras, and interface modules for embedded projects. Its broad module range helps developers add a screen, connectivity, or industrial I/O to a microcontroller or single-board computer.

[Browse Waveshare products on OpenELAB](https://openelab.io/collections/brands-waveshare)

## Expanded engineering guides

These guides provide on-page commissioning procedures, source-backed specifications, attributed diagrams and model-specific troubleshooting. Each page states its software and hardware test status.

| Exact model or family                                                         | Development workflow                                                                        |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [Jetson Orin NX 16GB kit](jetson-orin-nx-16gb-waveshare-development-guide.md) | Carrier identification, RAM versus NVMe, first boot, CUDA execution check and BSP recovery. |
| [Jetson Orin NX 8GB kit](waveshare-jetson-orin-nx-8gb-development-guide.md)   | Exact 8GB module and package, power/cooling, Linux/CUDA baseline and recovery.              |
| [ESP32-S3-ETH](waveshare-esp32-s3-eth-development-guide.md)                   | Wired DHCP, full example map, SD/camera integration and recovery.                           |
| [ESP32-S3-Nano](esp32-s3-nano-development-board.md)                           | Nano/native GPIO, RGB, UART, Wi-Fi/BLE, MicroPython and firmware offsets.                   |

## Choose a board, interface and host

This directory retains 61 existing guide URLs. A screen size or ESP32 family name is not enough to select wiring, firmware or an example. Use the exact module/kit and host platform, then the model page's official documentation links for schematics, example code and advanced features.

Start with [ESP32-S3-ETH wired networking](waveshare-esp32-s3-eth-development-guide.md) for explicit board settings and a DHCP checkpoint. For the [0.96-inch C/D/E OLED family](0.96-inch-oled-display-module-spi-i2c-communication.md), use the SSD1315 guide and its SPI/I2C configuration; the guide also documents source-archive issues found during review. Existing product ordering and guide URLs are preserved.

### Popular product guides

Guides for products in our Top 200 sales list, shown in popularity order. Shared guides appear once; use the model or order code to select the correct variant.

| Product guide                                                                                                      | Models / order codes                                |
| ------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------- |
| [Waveshare Jetson Orin NX 16GB Dev Kit Development Guide](jetson-orin-nx-16gb-waveshare-development-guide.md)      | Waveshare-24212                                     |
| [Waveshare 7-DSI-TOUCH-C Development Guide](7-dsi-touch-c-development-guide.md)                                    | Waveshare-33259                                     |
| [Waveshare SIM7600G-H 4G Module Engineering Guide](waveshare-sim7600g-h-module-development-guide.md)               | Waveshare-23992                                     |
| [Waveshare ESP32-S3 8DI 8RO Relay Controller Engineering Guide](waveshare-esp32-s3-8di-8ro-development-guide.md)   | Waveshare-30838 · Waveshare-31130                   |
| [Waveshare ESP32-S3 PoE 8DI 8DO Controller Engineering Guide](waveshare-esp32-s3-poe-8di-8do-development-guide.md) | Waveshare-32108                                     |
| [Waveshare ESP32-S3 Touch AMOLED 1.75 Engineering Guide](waveshare-esp32-s3-amoled-175-development-guide.md)       | Waveshare-31264 · Waveshare-31262 · Waveshare-31261 |
| [Waveshare ESP32-P4-NANO Engineering Guide](waveshare-esp32-p4-nano-development-guide.md)                          | Waveshare-29028                                     |
| [Waveshare Jetson Orin NX 8GB Dev Kit Engineering Guide](waveshare-jetson-orin-nx-8gb-development-guide.md)        | Waveshare-24444                                     |
| [Waveshare ESP32-S3 AMOLED 1.8 and 2.06 Engineering Guide](waveshare-esp32-s3-amoled-18-206-development-guide.md)  | Waveshare-29957 · Waveshare-31957                   |
| [Waveshare ESP32-S3 Touch LCD 1.85C BOX Engineering Guide](waveshare-esp32-s3-lcd-185c-box-development-guide.md)   | Waveshare-30684                                     |
| [Waveshare 27-inch FHD Touch Monitor Engineering Guide](waveshare-27inch-fhd-touch-monitor-development-guide.md)   | Waveshare-33975                                     |
| [Waveshare ESP32-S3-ETH Engineering Guide](waveshare-esp32-s3-eth-development-guide.md)                            | Waveshare-28972                                     |
| [Waveshare ESP32-S3 Touch LCD 4 and 4B Engineering Guide](waveshare-esp32-s3-lcd-4-4b-development-guide.md)        | Waveshare-32052 · Waveshare-28154                   |
| [Waveshare UGV Beast Engineering Guide](waveshare-ugv-beast-development-guide.md)                                  | Waveshare-28695                                     |

### Product range

* LCD, AMOLED, OLED, and e-paper displays and touch interfaces
* ESP32 boards, Raspberry Pi HATs, cameras, and sensors
* Ethernet, cellular, LoRa, RS485, and relay-control modules

### Product families and examples

| Product                         | Typical use                                   | Links                                                                                                                        |
| ------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| ESP32-S3 ETH                    | Networked ESP32-S3 projects with Ethernet     | [OpenELAB product](https://openelab.io/products/esp32-s3-eth-dev-board)                                                      |
| ESP32-S3 WiFi Relay ETH 8DI 8RO | Multi-channel relay and digital-input control | [OpenELAB product](https://openelab.io/products/waveshare-industrial-8-channel-esp32-s3-wifi-relay-eth-8di-8ro-module-rs485) |
| ESP32-S3-ePaper-1.54            | Low-power status and information displays     | [OpenELAB product](https://openelab.io/products/waveshare-esp32-s3-epaper-aiot)                                              |
| ESP32-S3-Touch-AMOLED-1.8       | Compact AMOLED touch interfaces               | [OpenELAB product](https://openelab.io/products/waveshare-esp32-s3-amoled-1-8)                                               |

### Popular applications

* Create touch-screen dashboards and low-power information displays.
* Add network connectivity and sensor interfaces to embedded systems.
* Prototype relay control, data acquisition, and automation interfaces.

### More manuals and tutorials

<details>

<summary>Browse 47 additional guides</summary>

* [OV5640 Camera Board (A), 5 Megapixel (2592x1944)](ov5640-camera-board-a-5-megapixel-2592x1944.md)
* [OV2640 Camera Board (1622x1200)](ov2640-camera-board-1622x1200.md)
* [ESP32-S3-Nano - Development Board](esp32-s3-nano-development-board.md)
* [Waveshare RM500U-CNV Raspberry PI 5G/4G/3G Hat](waveshare-rm500u-cnv-raspberry-pi-5g-4g-3g-hat.md)
* [Waveshare ESP8266 for Raspberry Pi Pico Wifi Module TCP UDP](waveshare-esp8266-for-raspberry-pi-pico-wifi-module-tcp-udp.md)
* [Waveshare MAX-M8Q GNSS HAT for Raspberry Pi](waveshare-max-m8q-gnss-hat-for-raspberry-pi.md)
* [Waveshare SX1262 LoRa HAT for Raspberry UART](waveshare-sx1262-lora-hat-for-raspberry-uart.md)
* [Waveshare SX1268 LoRa HAT for Raspberry UART](waveshare-sx1268-lora-hat-for-raspberry-uart.md)
* [Waveshare SIM7070G NB-IoT / Cat-M / GPRS / GNSS HAT for Raspberry Pi](waveshare-sim7070g-nb-iot-cat-m-gprs-gnss-hat-for-raspberry-pi.md)
* [Waveshare SIM7600G-H M.2 4G HAT for Raspberry Pi 4G/3G/2G GNSS](waveshare-sim7600g-h-m.2-4g-hat-for-raspberry-pi-4g-3g-2g-gnss.md)
* [Waveshare SIM7600CE-CNSE 4G HAT for Raspberry Pi 4G 3G 2G GNSS](waveshare-sim7600ce-cnse-4g-hat-for-raspberry-pi-4g-3g-2g-gnss.md)
* [Waveshare 10.1 inch IPS Capacitive Touch Display](waveshare-10.1-inch-ips-capacitive-touch-display.md)
* [Waveshare 10.1 inch QLED Touch Display](waveshare-10.1-inch-qled-touch-display.md)
* [Waveshare 9.7 inch IPS Capacitive Touch Display](waveshare-9.7-inch-ips-capacitive-touch-display.md)
* [Waveshare 10.1 inch IPS Capacitive Touch LCD](waveshare-10.1-inch-ips-capacitive-touch-lcd.md)
* [Waveshare 9.3 inch LCD Capacitive Touch Display High Brightness](waveshare-9.3-inch-lcd-capacitive-touch-display-high-brightness.md)
* [Waveshare 9 inch QLED Quantum Dot Display](waveshare-9-inch-qled-quantum-dot-display.md)
* [Waveshare 8 inch 2K IPS Capacitive Touch Display](waveshare-8-inch-2k-ips-capacitive-touch-display.md)
* [Waveshare 8DP-CAPLCD 8 inch Capacitive Touch Display](waveshare-8dp-caplcd-8-inch-capacitive-touch-display.md)
* [Waveshare 7.9 inch IPS LCD Touch Screen, 400×1280 HDMI](waveshare-7.9-inch-ips-lcd-touch-screen-400-1280-hdmi.md)
* [Waveshare 8 inch DSI LCD Display Touch Screen I2C](waveshare-8-inch-dsi-lcd-display-touch-screen-i2c.md)
* [Waveshare 7 inch IPS Integrated Display, With Touch Function](waveshare-7-inch-ips-integrated-display-with-touch-function.md)
* [Waveshare 7HP-CAPQLED 7 inch QLED Quantum Dot Display](waveshare-7hp-capqled-7-inch-qled-quantum-dot-display.md)
* [Waveshare 7 inch Capacitive Touch Screen HDMI](waveshare-7-inch-capacitive-touch-screen-hdmi.md)
* [Waveshare 7 inch Capacitive Touch Screen with Case HDMI](waveshare-7-inch-capacitive-touch-screen-with-case-hdmi.md)
* [2.8inch USB Monitor,Water Cooler Screen/ PC Case Secondary Screen](2.8inch-usb-monitor-water-cooler-screen-pc-case-secondary-screen.md)
* [Waveshare 5inch Desktop RGB Ambient Screen](waveshare-5inch-desktop-rgb-ambient-screen.md)
* [Waveshare 5inch IPS Round Touch DisplayHDMI](waveshare-5inch-ips-round-touch-displayhdmi.md)
* [Waveshare 5.5inch 2K Touch LCD Display HDMI](waveshare-5.5inch-2k-touch-lcd-display-hdmi.md)
* [2.1 inch USB Monitor, Water Cooler Screen/ PC Case Secondary Screen](2.1-inch-usb-monitor-water-cooler-screen-pc-case-secondary-screen.md)
* [Waveshare 8.8inch Desktop RGB Ambient Screen Type-C](waveshare-8.8inch-desktop-rgb-ambient-screen-type-c.md)
* [Waveshare 8inch Desktop RGB Ambient Screen Type-C](waveshare-8inch-desktop-rgb-ambient-screen-type-c.md)
* [Waveshare 7 inch Desktop RGB Ambient Screen](waveshare-7-inch-desktop-rgb-ambient-screen.md)
* [Waveshare 5inch HDMI Touch Screen LCD with Bicolor Case](waveshare-5inch-hdmi-touch-screen-lcd-with-bicolor-case.md)
* [Waveshare 65K RGB General 1.28inch Round LCD Display Module](waveshare-65k-rgb-general-1.28inch-round-lcd-display-module.md)
* [0.96 inch OLED Display Module, SPI / I2C Communication](0.96-inch-oled-display-module-spi-i2c-communication.md)
* [1.5 inch LCD Display Module, IPS Panel SPI 262K colors](1.5-inch-lcd-display-module-ips-panel-spi-262k-colors.md)
* [Waveshare 1.8inch colorful display module for micro:bit](waveshare-1.8inch-colorful-display-module-for-micro-bit.md)
* [Waveshare 3.5inch RPi LCD (A)](waveshare-3.5inch-rpi-lcd-a.md)
* [Waveshare 5 inch LCD Touch Screen Display for Raspberry Pi](waveshare-5-inch-lcd-touch-screen-display-for-raspberry-pi.md)
* [Waveshare 1.47inch LCD Display Module SPI](waveshare-1.47inch-lcd-display-module-spi.md)
* [7.3 inch 7 Color E-Paper](7.3-inch-7-color-e-paper.md)
* [Waveshare 15.6 inch QLED Touch](waveshare-15.6-inch-qled-touch.md)
* [Waveshare 7.5 inch NFC-Powered](waveshare-7.5-inch-nfc-powered.md)
* [Rotation Sensor](rotation-sensor.md)
* [MQ-135 Gas Sensor](mq-135-gas-sensor.md)
* [SIM7028 NB-IoT HAT](sim7028-nb-iot-hat.md)

</details>

[Explore AIoT documentation](../aiot-wiki-home-page.md) · [OpenELAB Wiki home](../../)
