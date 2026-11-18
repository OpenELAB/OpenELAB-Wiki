# Waveshare ESP32-S3-ETH Engineering Guide

[Waveshare-28972](https://openelab.io/products/esp32-s3-eth-dev-board)

### Product and scope

**28972 ESP32-S3-ETH** is the base Ethernet development board. **PoE and camera kits are separate configurations**; a reserved PoE connector does not mean a PoE module is included.

### Hardware and technical documents

| Item      | Reference                                             |
| --------- | ----------------------------------------------------- |
| Core      | ESP32-S3R8; 16MB flash / 8MB PSRAM                    |
| Ethernet  | SPI-connected W5500, 10/100Mbps                       |
| Wireless  | 2.4GHz Wi-Fi / BLE                                    |
| Storage   | microSD                                               |
| Expansion | Camera connection and Pico-style header               |
| PoE       | Optional compatible module; POE-named kits include it |

Use the official **schematic, pin map and camera/PoE diagrams**. Verify supply and signal levels before using Pico-compatible accessories. External-antenna selection may require the documented RF resistor change; plugging in an antenna alone does not switch the path.

### Getting started

1. Begin with USB-C data/power and no camera or external expansion.
2. Install the model's documented environment and open its W5500 Ethernet example.
3. Retain the supplied SPI pin assignments and dependency versions.
4. Connect Ethernet and verify link plus DHCP/static address in the serial log.
5. Test local network reachability, then add camera or SD functions separately.

**Expected checkpoint:** stable Ethernet link and a valid network configuration from the W5500 path.

### Development software and recovery

Use model-specific Arduino/ESP-IDF examples and save the source/toolchain versions. SPI bus sharing and camera pins must be checked before combining peripherals. Restore the official factory example through its BOOT/download sequence if required.

### FAQs

**No power over Ethernet?** The base SKU lacks the separately specified PoE module.

**W5500 initializes but no IP?** Check link, network configuration and DHCP reachability.

**A Pico accessory conflicts?** Compare every used signal and power pin; compatible shape is not universal electrical compatibility.

### Sources and validation

* [Current model/SKU matrix, pinout and resources](https://docs.waveshare.com/ESP32-S3-ETH)
* [Manufacturer detailed hardware reference](https://docs.waveshare.net/ESP32-S3-ETH/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
