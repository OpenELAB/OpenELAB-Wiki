---
description: >-
  Set up ESP32-S3-ETH wired networking with exact Arduino settings, ESP-IDF
  components, kit differences and recovery.
---

# Waveshare ESP32-S3-ETH Engineering Guide

{% hint style="info" %}
[**View Waveshare ESP32-S3-ETH on OpenELAB**](https://openelab.io/products/esp32-s3-eth-dev-board)

**Model:** ESP32-S3-ETH · **OpenELAB SKU:** `Waveshare-28972` · Base board; camera and PoE modules are separate options.
{% endhint %}

## Product overview

ESP32-S3-ETH combines an ESP32-S3 controller with a W5500 wired network interface. This guide establishes a wired-network result before combining camera, storage and wireless functions. A reserved PoE header does not supply PoE by itself. The manufacturer distinguishes base `28972`, camera kit `28770`, PoE board `28771` and PoE-camera kit `28772`; newer `-M` variants have separate codes. Use the purchased board's documentation and package contents. [Manufacturer overview](https://docs.waveshare.com/ESP32-S3-ETH).

## Applications

Use the base board for a wired sensor node, network interface prototype or local Ethernet service. A compatible camera enables image-stream experiments; a matching PoE module changes the power arrangement. Establish each peripheral separately before combining them so a camera, supply or bus fault is distinguishable from network configuration.

## Specifications

| Integration item       | ESP32-S3-ETH base board                                   |
| ---------------------- | --------------------------------------------------------- |
| Processor              | ESP32-S3R8, dual-core LX7, up to 240 MHz                  |
| External flash / PSRAM | 16 MB / 8 MB                                              |
| Ethernet               | W5500 over SPI; 10/100 Mbps network interface             |
| Wireless               | 2.4 GHz Wi-Fi and Bluetooth LE                            |
| Interfaces             | USB-C, microSD, camera connector and Pico-style expansion |
| PoE                    | Requires the compatible module; verify the kit option     |

These are manufacturer specifications, not measured throughput or an assertion that all interfaces can run concurrently. [Board specification and interfaces](https://docs.waveshare.com/ESP32-S3-ETH).

## Hardware and connections

Start with USB-C and Ethernet, leaving optional loads disconnected. Use a USB cable carrying data. The manufacturer's ESP-IDF reference maps the W5500 as follows; these assignments belong to **ESP32-S3-ETH**, not another ESP32 board:

| W5500 signal        | ESP32-S3 GPIO |
| ------------------- | ------------- |
| MISO / MOSI         | 12 / 11       |
| Clock / chip select | 13 / 14       |
| Reset / interrupt   | 9 / 10        |

The microSD example instead uses MISO 5, MOSI 6, clock 7 and chip select 4. Preserve the board package's configuration rather than substituting a generic Pico or ESP32-S3-Zero pin map. [ESP-IDF board configuration](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-ESP-IDF).

GPIO33–37 are unavailable for general expansion in this board's FAQ. Switching the RF path to the IPEX connector requires the documented resistor rework; attaching an antenna alone does not perform that switch. [Board FAQ](https://docs.waveshare.com/ESP32-S3-ETH/FAQ). Use the [schematic and pin diagram](https://docs.waveshare.com/ESP32-S3-ETH/Resources-And-Documents) for electrical limits and connector orientation before adding hardware.

## Software and development resources

The Arduino reference specifies ESP32 board support **2.0.12 or later**; its `ETHClass2` camera path is scoped to **2.x**. The current ESP-IDF package documents **5.5.4**. Retain the package and dependency versions; a minimum version is not proof of later-major compatibility. [Arduino environment](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-Arduino), [ESP-IDF environment](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-ESP-IDF).

## Getting started

### Arduino: obtain a wired DHCP address

1. Connect USB data and Ethernet to a DHCP network. Get the model's [example package](https://docs.waveshare.com/ESP32-S3-ETH/Resources-And-Documents).
2. Install the documented ESP32 package and bundled `Ethernet` dependency; open `Arduino/examples/10_ETH_DHCP`.
3. Select the port and these settings:

| Arduino Tools setting  | Value                                       |
| ---------------------- | ------------------------------------------- |
| Board                  | ESP32S3 Dev Module                          |
| USB CDC On Boot        | Enabled                                     |
| CPU / flash            | 240 MHz / 16 MB                             |
| Partition              | Huge APP (3 MB No OTA/1 MB SPIFFS)          |
| PSRAM                  | OPI PSRAM                                   |
| Upload mode / USB mode | UART0 / Hardware CDC; Hardware CDC and JTAG |
| Upload speed           | 921600                                      |

4. Keep the supplied pins and serial baud; upload and check the wired address. A Wi-Fi address does not prove Ethernet works.

**Expected result:** the Ethernet example reports an address from the wired network. These steps and settings come from the [Arduino workflow](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-Arduino); they have not been executed by OpenELAB for this review.

### ESP-IDF: preserve shared components

Use the documented ESP-IDF 5.5.4 environment and the package's `ESP-IDF/example/09_ETH_DHCP` project. Keep its sibling `eth_w5500_common` directory: the project's `EXTRA_COMPONENT_DIRS` depends on that location. Camera projects additionally use `cam_web_common`. A missing shared directory is a build-layout fault, not evidence of defective hardware. Follow the [ESP-IDF build and example instructions](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-ESP-IDF).

### Continue from a working link

The [complete Arduino example catalogue](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-Arduino#example) covers static IP, MAC/DHCP fallback, SD, wireless and camera tasks. Choose one next feature and document its independent result before combining it with Ethernet.

## Troubleshooting and FAQs

**Upload port missing or flashing fails:** check cable and port, then hold BOOT, press RESET, release RESET and finally release BOOT. Re-select the port after download mode appears. [Recovery FAQ](https://docs.waveshare.com/ESP32-S3-ETH/FAQ).

**Ethernet link but no address:** check the DHCP service and cable first; then compare W5500 pins and the installed Ethernet library with the supplied project. Test the official static-address example only with an address valid for your network. Keep Wi-Fi and Ethernet results separately in the test record.

**Camera build fails after a toolchain change:** restore the documented package and library generation, or use the matching ESP-IDF example. The Arduino `ETHClass2` camera path is scoped to 2.x. [Arduino dependencies](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-Arduino).

**Camera gets excessively hot:** stop capture, remove power and let the assembly cool. Investigate the supply, connection and operating conditions before restarting. Normal camera heating is not a reason to ignore excessive temperature. [Camera FAQ](https://docs.waveshare.com/ESP32-S3-ETH/FAQ).

## Downloads and technical documents

| Resource                                                                                             | Purpose                                                           |
| ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| [Resources and documents](https://docs.waveshare.com/ESP32-S3-ETH/Resources-And-Documents)           | Model schematic, data sheets and example package                  |
| [Arduino development](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-Arduino) | Settings, dependencies and all Arduino example tasks              |
| [ESP-IDF development](https://docs.waveshare.com/ESP32-S3-ETH/Development-Environment-Setup-ESP-IDF) | Version, shared components and native example tasks               |
| [Firmware flashing](https://docs.waveshare.com/ESP32-S3-ETH/Firmware-Flashing)                       | Manufacturer flashing/erase workflow; erasure removes stored data |
| [FAQ](https://docs.waveshare.com/ESP32-S3-ETH/FAQ)                                                   | Board-specific recovery, reserved pins and antenna selection      |

## References and validation

Official source pages reviewed **23 November 2026**. The linked manufacturer references retain the full example catalogue and diagrams. This OpenELAB guide adds a staged integration path and separates board, dependency, storage and network faults. Software compilation, firmware upload and hardware tests were **not run**. Record the board revision, downloaded package, SDK/library versions and actual logs before reporting a tested result.
