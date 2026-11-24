---
description: >-
  Bring up the original H784 T-2CAN, select MCP2515 rather than FD firmware,
  verify a 500 kbit/s bench loop and use a receive-only TWAI diagnostic.
---

# LILYGO T-2CAN and T-2CAN-FD Engineering Guide

{% hint style="info" %}
[**View LILYGO T-2CAN ESP32-S3 H784 CAN / H784-A CAN FD Board on OpenELAB**](https://openelab.io/products/lilygo-t-2can-esp32s3-qwiic)

**Model / option:** T-2CAN \[H784] · **SKU:** `LILYGO-H784`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

T-2CAN **H784** is the original ESP32-S3 dual Classical CAN board: channel A uses an SPI MCP2515 and channel B uses the ESP32-S3 TWAI controller. **H784-A/T-2CAN-FD** changes channel A to MCP2518FD; its second TWAI channel remains Classical CAN. This guide preserves the existing family page but covers the assigned H784 row only.

The current source defaults to the FD definition. Select the original hardware explicitly before a build; successful compilation alone cannot detect a wrong controller choice. [Manufacturer source](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/README.md), [actual configuration header](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/libraries/private_library/pin_config.h).

## Applications

Use H784 for isolated bench CAN communication, two-bus protocol experiments and host logging. Begin with a local two-channel loop and a known frame before considering a gateway application. Controller, transceiver and connector references are distinct parts of the electrical path.

The stock examples transmit repeated frames. Keep them on the isolated test assembly used here. A controller's SPI initialization result does not prove a valid CAN waveform, peer acknowledgement or correct termination.

## Specifications

| Item                    | H784 original                                                    | H784-A comparison only                                                |
| ----------------------- | ---------------------------------------------------------------- | --------------------------------------------------------------------- |
| Host / memory           | ESP32-S3-WROOM-1U N16R8 family, 16 MB flash/8 MB PSRAM           | Same host family                                                      |
| Channel A controller    | MCP2515, Classical CAN                                           | MCP2518FD, CAN FD-capable                                             |
| Channel B controller    | ESP32-S3 TWAI, Classical CAN                                     | Still Classical CAN                                                   |
| Driver libraries        | Bundled arduino-mcp2515                                          | Bundled Longan\_CAN FD                                                |
| Isolated interface      | TD501MCAN transceiver modules in original schematic              | Match FD schematic's module and timing scope                          |
| Original oscillator     | MCP2515 crystal 16 MHz                                           | Do not reuse original oscillator/driver assumptions                   |
| Bench power             | USB-C 5 V path, no external terminal supply needed for this test | Verify received revision                                              |
| External supply drawing | Terminal net labeled +24 V                                       | A schematic net label is not a complete operating-range specification |

Source: [original schematic](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-2Can/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/project/T-2Can_V1.0.pdf), [FD schematic](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-2Can/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/project/T-2Can-Fd_V1.0.pdf), [README](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/README.md). No external terminal voltage range or isolation withstand rating is inferred from a component maximum.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Main pins and bus-side references

| Function                   | H784 ESP32-S3 GPIO                               |
| -------------------------- | ------------------------------------------------ |
| MCP2515 SPI SCK/MOSI/MISO  | 12/11/13                                         |
| MCP2515 CS/reset/interrupt | 10/9/8                                           |
| TWAI TX/RX                 | 7/6                                              |
| BOOT                       | 0                                                |
| USB data                   | 19D−/20D+; separate from an external UART header |

These are host logic nets. The board's transceiver path performs its own electrical conversion; do not connect GPIO7/6 directly to CANH/CANL. [Pin configuration](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/libraries/private_library/pin_config.h).

The original schematic shows bus B connector P1 and bus A connector P2. In the schematic's numbered orientation, each is **pin 1 DGND, pin 2 CANH, pin 3 CANL, pin 4 SGND**. Match the actual connector pin 1 marker before translating that to physical left/right. SGND is the isolated signal reference; DGND belongs to the protection/reference network. Do not bridge either to ESP32 logic ground merely because the word “ground” appears. Both channels include 120 Ω termination in the reviewed circuit. [Connector/protection drawing](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-2Can/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/project/T-2Can_V1.0.pdf).

For the short isolated loop, with power removed connect A-CANH to B-CANH, A-CANL to B-CANL, and the matching bus-side SGND references. Leave external field equipment and the +24 V terminal disconnected. Verify the received board actually has the shown terminations; two 120 Ω ends give approximately 60 Ω across H/L with power off. Additional termination would change that load. This continuity/resistance check precedes USB power; it is not an insulation test.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The reviewed repository commit is `4e9eddd5f39f27d43360de9fb8904734cce9f0cb`, PlatformIO `espressif32@6.5.0`, Arduino-ESP32 baseline 2.0.14, board `esp32s3_flash_16MB`, 16 MB partitioning and OPI PSRAM. Keep its bundled libraries. [Build configuration](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/platformio.ini).

Three source changes are required before this H784 USB test:

1. In `libraries/private_library/pin_config.h`, enable **`T_2Can`** and disable `T_2Can_Fd`. Define exactly one. The current file enables FD by default.
2. For USB serial output, set **`-D ARDUINO_USB_CDC_ON_BOOT=1`** in this project's flags. The current configuration is 0, which routes the normal console differently. For deliberate external UART use select 0 and its correct 3.3 V logic connection instead.
3. In `examples/can/can.ino`, inside `Can_B_Twai_Send_Message()`, replace the local declaration `twai_message_t message;` with the following initializer before assigning the identifier, DLC and payload:

```cpp
twai_message_t message = {};
```

This is a **correction to the pinned upstream example**. Its original declaration leaves `extd`, `rtr`, `ss`, `self` and `dlc_non_comp` indeterminate. Zero-initialization gives the intended standard data-frame flags; keep the existing `0xBB` identifier, DLC 8 and eight data assignments. The same defect occurs in `examples/original_test/original_test.ino` if that example is later used. The repeatable two-way result below assumes this correction. [Pinned transmit function](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/examples/can/can.ino), [ESP-IDF 4.4.7 message definition](https://github.com/espressif/esp-idf/blob/v4.4.7/components/hal/include/hal/twai_types.h).

The `can` example is a two-controller message test. `original_test` adds Wi-Fi/AP/HTTP logging and timing; it is not a quiet read-only monitor. Avoid copying its demonstration network credentials into another deployment. The README/source identify GPL-3.0; preserve this and library notices when distributing modified firmware.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original isolated two-channel first result

1. Identify H784/MCP2515 and save the factory version before changing it. With power off make the short A↔B loop described above and check termination/reference continuity. Do not attach a vehicle or operational machine bus.
2. Clone the pinned repository, select `T_2Can` and USB CDC 1 as above, then set `default_envs = can`. The configuration derives `src_dir` from that environment; changing only `-e` while leaving `default_envs` at `original_test` would still select the wrong source folder.
3. Apply the three corrections above, including zero-initializing the TWAI transmit message, then compile. Inspect the selected macros and artifact before uploading to the identified board with stable USB power.

```sh
git clone https://github.com/Xinyuan-LilyGO/T-2Can.git
cd T-2Can
git checkout 4e9eddd5f39f27d43360de9fb8904734cce9f0cb
# Apply T_2Can, USB CDC=1, default_envs=can and the TWAI initializer correction.
pio run -e can
pio run -e can -t upload
pio device monitor -b 115200
```

4. Require the channel A SPI/configuration/bitrate/mode checks to succeed and channel B driver to install/start. The example prints failures and can continue; a running loop alone is not acceptance.
5. Verify **500 kbit/s Classical CAN** on both channels. In the original branch A transmits ID `0xAA` with 8 bytes `08 07 06 05 04 03 02 01`; B transmits ID `0xBB` with `01 02 03 04 05 06 07 08`. Confirm each is received by the opposite controller and that errors do not keep increasing.
6. Record the firmware/commit, controller branch, bitrate, frame format, IDs/data, termination and error counts. Remove power before changing the loop wiring.

**Expected result:** successful initialization and repeatable reception in both directions on the isolated loop. No successful compile, flash or CAN test is claimed here. [Actual source](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/examples/can/can.ino).

### Original receive-only TWAI diagnostic

For observing a controlled bench bus, this alternative initializes only channel B in **listen-only** mode. It does not acknowledge packets or transmit. The bench must already have two normal peers supplying acknowledgement, or a compatible generator explicitly configured for its supported no-ACK test. Use matching 500 kbit/s Classical frames; it does not decode CAN FD.

```cpp
#include <Arduino.h>
#include "driver/twai.h"
static bool started = false;
void setup() {
  Serial.begin(115200);
  twai_general_config_t g = TWAI_GENERAL_CONFIG_DEFAULT(
      GPIO_NUM_7, GPIO_NUM_6, TWAI_MODE_LISTEN_ONLY);
  twai_timing_config_t t = TWAI_TIMING_CONFIG_500KBITS();
  twai_filter_config_t f = TWAI_FILTER_CONFIG_ACCEPT_ALL();
  esp_err_t install = twai_driver_install(&g, &t, &f);
  started = install == ESP_OK && twai_start() == ESP_OK;
  Serial.println(started ? "TWAI listen ready" : "TWAI init failed");
}
void loop() {
  if (!started) { delay(100); return; }
  twai_message_t frame = {};
  if (twai_receive(&frame, pdMS_TO_TICKS(200)) == ESP_OK) {
    Serial.printf("id=%lX extended=%u dlc=%u\n",
      (unsigned long)frame.identifier, frame.extd, frame.data_length_code);
  }
}
```

Expected output is `TWAI listen ready` followed by received frame IDs/lengths when a peer sends. A quiet bus produces no frame lines. The code uses the reviewed board TX7/RX6 and [ESP-IDF 4.4 TWAI API](https://github.com/espressif/esp-idf/blob/v4.4.7/components/driver/include/driver/twai.h); it has not been compiled or run.

### Recovery

If upload fails, keep field buses disconnected, hold BOOT0 and retry the supported USB download procedure, then reset to run. Restore the original-model factory image with its documented layout; do not use an FD factory image or guess an offset. Keep the previous binary and settings because erasing can remove custom application/network configuration.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                           | Ordered checks                                                                               |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| “Chip/SPI check” fails                            | H784 versus FD macro, SPI12/11/13, CS10, controller reset and correct library                |
| TWAI starts but no frames                         | Physical channel, 500 kbit/s, Classical frame format, H/L/reference and termination          |
| ACK errors rise                                   | Correct normal peer, not only a listen-only observer; match bitrate and wiring               |
| USB console silent                                | Actual CDC flag is 0 by default; set 1 for USB logging or use deliberate external UART       |
| FD frames fail on channel B                       | ESP32-S3 TWAI is Classical CAN; FD capability on H784-A is only the external-controller path |
| Factory UI/web log appears instead of simple test | `default_envs` also selects source directory; align it with `can`                            |

No external supply range or isolation withstand rating is established by a generic chip data sheet. Keep the first result on the documented USB power path; obtain the exact system rating before using the external terminal.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                     | Scope                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| [Pinned repository](https://github.com/Xinyuan-LilyGO/T-2Can/tree/4e9eddd5f39f27d43360de9fb8904734cce9f0cb)                                                                                                                                                                  | Source, examples, drivers, boardconfig and factory firmware               |
| [Original schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-2Can/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/project/T-2Can_V1.0.pdf)                                                                                                                           | MCP2515, 16 MHz clock, isolated transceivers, USB and terminal references |
| [FD schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-2Can/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/project/T-2Can-Fd_V1.0.pdf)                                                                                                                              | Comparison only; not the assigned H784 controller                         |
| [Pin/macro header](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/libraries/private_library/pin_config.h)                                                                                                                            | Select exactly one original/FD branch                                     |
| [CAN source](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/examples/can/can.ino) /[factory source](https://github.com/Xinyuan-LilyGO/T-2Can/blob/4e9eddd5f39f27d43360de9fb8904734cce9f0cb/examples/original_test/original_test.ino) | Protocol/bitrate, readback diagnostics and separate network logging       |

The repository's `docs` directory lists MCP2515/MCP2518FD component data sheets; `firmware` separates original/FD and deprecated binaries. Use those exact resources rather than old README `information/` links when a path has moved.

### Additional existing resources

* [FD-specific hardware explanation](https://github.com/Xinyuan-LilyGO/documentation/blob/master/en/products/industrial-series/t-2can-fd/index.md)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The README, actual build/macro files, both example sources and original/FD schematic resources were read. The original schematic was visually inspected. The guide adds the explicit H784 branch/USB console and upstream transmit-message initialization corrections, isolated A↔B acceptance and a new receive-only TWAI example. Its static C++ literal scan is not SDK compilation.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
