# Waveshare ESP32-P4-NANO Engineering Guide

[Waveshare-29028](https://openelab.io/products/waveshare-esp32-p4-nano-development-board)

### Product and scope

**29028 ESP32-P4-NANO** is a RISC-V multimedia/control development board. Base board, camera, PoE and display kits have different contents. The P4 host and its wireless companion require the supported board software together.

### Hardware and technical documents

| Item         | Reference                                                       |
| ------------ | --------------------------------------------------------------- |
| Host         | ESP32-P4                                                        |
| Architecture | High-performance RISC-V MCU platform                            |
| Interfaces   | Ethernet, MIPI camera/display and board-specific expansion      |
| Wireless     | Board-supported companion path; not an ESP32-S3 firmware target |
| Kit options  | Camera/PoE/display accessories vary                             |

The NANO start page links **schematics, interface diagrams, dimensions and examples**. Use the matching FFC pinout and orientation; a Raspberry Pi-style camera cable is not proof of every sensor's compatibility. PoE requires the documented module/configuration.

### Getting started

1. Identify the base board and fitted accessories; connect supported power with cameras/displays attached only while powered off.
2. Install the vendor's documented ESP-IDF environment and component versions.
3. Select the **ESP32-P4** target and the NANO's minimal example.
4. Build/flash and confirm its serial startup log.
5. Add the supported display or camera example, then networking, one subsystem at a time.

**Expected checkpoint:** successful board initialization and one working peripheral under the model-specific BSP.

### Development software and recovery

Use the vendor BSP and any required companion firmware/ESP-Hosted integration as a matched set. Preserve the manifest and firmware revisions. Recover through the P4 board's documented download-mode procedure; S3/C6 images are not P4 application images.

### FAQs

**Wi-Fi unavailable in a bare P4 example?** Initialize the board's supported companion path.

**MIPI camera fails?** Check sensor support, FFC orientation, power and example configuration.

**Can a generic S3 Arduino sketch be flashed?** The host processor and BSP are different.

### Sources and validation

* [Official NANO start page and resources](https://www.waveshare.com/wiki/ESP32-P4-Nano-StartPage)
* [Kit contents and accessories](https://www.waveshare.com/product/esp32-p4-nano.htm)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
