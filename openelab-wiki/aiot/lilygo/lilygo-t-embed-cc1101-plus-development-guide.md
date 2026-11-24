---
description: >-
  Develop the external-antenna T-Embed CC1101 Plus with correct shared SPI,
  PN532 and nRF24 pins, and verify a controlled two-way packet test.
---

# LILYGO T-Embed CC1101 Plus Engineering Guide

{% hint style="info" %}
[**View LILYGO T‑Embed CC1101 Plus ESP32‑S3 NFC/RFID Wireless Lab Board on OpenELAB**](https://openelab.io/products/lilygo-t-embed-cc1101-plus)

**Model / option:** External Antennas / Transparent\[K268-01] · **SKU:** `LILYGO-K268-01`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

T-Embed CC1101 Plus K268-01 is the transparent **external-antenna** ESP32-S3 handheld with CC1101, PN532 and an added nRF24L01 radio. CC1101 is a sub-GHz FSK/OOK-family transceiver; it is not a LoRa modem. The nRF24L01 is a separate 2.4 GHz device, not a CC1101 operating mode. This Plus guide retains its own canonical page rather than replacing the older [CC1101 base-model guide](t-embed-cc1101-module.md).

The current manufacturer repository is shared with the base board, but explicitly defines the nRF24 CS44/CE43 interface. Match the actual Plus board and external-antenna enclosure before mechanical or RF changes. [Plus product](https://lilygo.cc/products/t-embed-cc1101-plus), [reviewed board definitions](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/examples/utilities.h).

## Applications

Use the Plus for your own packet-radio experiments, reading a known NFC test tag, local infrared controls, display/encoder UI and instrument logging. Establish local display and power behavior before configuring either radio.

A useful radio trial has two controlled endpoints and a known payload. Keep CC1101 modulation, frequency and packet format separate from nRF24 channel, data rate, pipe address and acknowledgements. A successful nRF24 packet is not evidence that the sub-GHz path or PN532 reader works.

## Specifications

| Parameter               | Plus/base-family scope                                                 |
| ----------------------- | ---------------------------------------------------------------------- |
| Host / memory           | ESP32-S3-WROOM-1; 16 MB flash, 8 MB PSRAM                              |
| Display                 | 1.9-inch ST7789, 170 × 320 portrait /320 × 170 landscape               |
| Sub-GHz                 | CC1101; documented 300–348, 387–464 and 779–928 MHz hardware bands     |
| Plus added radio        | nRF24L01, separate 2.4 GHz packet radio                                |
| NFC                     | PN532 over I²C, 7-bit address 0x24; 13.56 MHz tags                     |
| Battery / charger       | 3.7 V 1300 mAh family pack; BQ25896 charger and BQ27220 fuel gauge     |
| Other interfaces        | Encoder, IR TX/RX, microSD, microphone, speaker, 8 WS2812 LEDs         |
| External antenna option | K268-01; do not assume internal-antenna CAD/cable routing is identical |

The manufacturer's README limits programmed charging current to **600 mA** for this assembly. Use its USB-C charging path and original pack; do not substitute the charger's silicon maximum for a battery/system rating. [Manufacturer README](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/README.md).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Power and occupied buses

Use USB-C for the initial bench test. Peripheral supply enable is GPIO15; the board schematic identifies 3.3 V peripheral domains. USB voltage is not a GPIO logic level. Keep the assembled battery harness intact. The IR assembly and antenna wiring can be damaged during a casual enclosure swap; use the correct K268-01 mechanical files rather than reshaping the case around a connector.

| Function                        | ESP32-S3 GPIO                     |
| ------------------------------- | --------------------------------- |
| Shared SPI SCK/MOSI/MISO        | 11/9/10                           |
| LCD CS/DC/backlight             | 41/16/21                          |
| CC1101 CS/GDO0/GDO2             | 12/3/38                           |
| CC1101 RF switch SW1/SW0        | 47/48                             |
| nRF24 CS/CE/IRQ                 | 44/43/not connected; polling used |
| Card CS                         | 13                                |
| I²C SDA/SCL                     | 8/18                              |
| PN532 reset/IRQ                 | 45/17                             |
| Encoder A/B/push                | 4/5/0                             |
| User button / peripheral enable | 6/15                              |
| IR TX/RX /WS2812                | 2/1 /14                           |
| Microphone data/clock           | 42/39                             |
| Speaker BCLK/LRCLK/data         | 46/40/7                           |

I²C devices include PN532 0x24, fuel gauge 0x55 and charger 0x6B. Keep non-selected SPI devices inactive. The current helper functions `board_spi_prepare_display/lora/nrf24/sd` preserve bus switching; a library constructor alone does not manage every other peripheral. Some legacy SDA/SCL aliases in `utilities.h` are reversed; use **BOARD\_I2C\_SDA 8 / SCL 18**, not those older alias names. [Exact definitions](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/examples/utilities.h).

For CC1101, the README defines logical SW1/SW0 states 315 MHz=`1/0`, 868/915 MHz=`0/1`, 434 MHz=`1/1`. These are GPIO-driven RF-path selectors, not universal physical DIP-switch positions. A compatible chip frequency does not by itself establish a matched antenna or regional operating permission.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Use repository commit **`c36826e0f91311cb591c4545fccf91e254fc55dc`**, environment **`T_Embed_CC1101`**, board `T_Embed_PN532`. The actual configuration uses `espressif32@6.13.0` and RadioLib `^7.7.1`; the README's older 6.5.0 library table is not the current dependency declaration. Preserve the selected configuration and bundled libraries rather than mixing examples across releases. [Pinned platformio.ini](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/platformio.ini).

Select exactly one `src_dir`. The current tree contains `examples/test_nrf24_send_recv/test_nrf24_send_recv.ino`; its README mentions an older `examples/nrf24_send_recv_test` path that is absent at this commit. Use the actual directory below. The main factory example is an alternate starting point, not a Meshtastic image.

The repository also includes display/encoder, CC1101 send/receive, battery/charger, PN532, IR, card, record/speaker, BLE-UART and LED examples. BLE GATT UART is not A2DP audio. Source files and bundled libraries retain their respective licenses; do not infer one blanket license for all third-party firmware named in the README.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Establish a local baseline

1. Record the Plus model, antenna/case option, board markings and factory firmware. Fit the supplied antennas and use a known USB data connection.
2. Check the factory display and encoder separately. Open a known local menu and confirm focus follows rotation and the center push confirms. Verify a new screen transition rather than a retained image.
3. If developing, clone the pinned repository and set the sole `src_dir` to `examples/display_test`. Build `T_Embed_CC1101`, upload only after preserving the existing image/configuration, then verify a stable display pattern. Use `examples/encode_test` for the encoder if needed.
4. Return to a known-good factory build before combining peripherals. Validate card, audio and NFC as separate tests; do not enable all radios just to diagnose a black screen.

**Expected result:** a stable display and repeatable encoder input before radio integration. [Manufacturer examples/build procedure](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/README.md).

### Original two-endpoint nRF24 test

Use two confirmed nRF24-equipped boards and a permitted test channel. Keep each radio's antenna assembly intact. In a development checkout:

```sh
git clone https://github.com/Xinyuan-LilyGO/T-Embed-CC1101.git
cd T-Embed-CC1101
git checkout c36826e0f91311cb591c4545fccf91e254fc55dc
```

Edit `platformio.ini` so only `src_dir = examples/test_nrf24_send_recv` is active, retaining the existing environment/dependencies. With PlatformIO installed:

```sh
pio run -e T_Embed_CC1101
# Upload only to the identified Plus after saving the working application.
pio run -e T_Embed_CC1101 -t upload
pio device monitor -b 115200
```

On each console first use `status`. For a short controlled test the following commands match the reviewed parser; use the same permitted channel and settings on both devices. Channel 76 corresponds to 2476 MHz by the example's `2400+channel` formula; it is an example, not a worldwide permission.

```
ch 76
rate 1000
power -18
ack on
rx
status
```

Keep B in RX. At A issue `send PLUS-A-01`; verify **Last RX** and incremented RX count at B. Then keep A in RX and issue `send PLUS-B-01` at B. Record both receipts, channel, data rate, power and ACK state. Avoid TXBURST for the first test because repeated traffic makes individual failures harder to distinguish.

**Expected result:** two unique packets received in opposite directions and an ACK when enabled. “ACK not received” can mean the peer isn't in RX or differs in channel/rate/address/ACK policy; do not equate it with a dead transmitter. The reviewed source uses a 5-byte pipe `01 23 45 67 89`. [Actual sketch](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/examples/test_nrf24_send_recv/test_nrf24_send_recv.ino).

### NFC, card and recovery checkpoints

Use a known 13.56 MHz NTAG or supported test card you control. In the factory NFC page, present it near the side opposite USB-C and confirm a fresh UID/read. That is a reader test, not proof that protected data can be read or another card protocol is supported. The PN532 is not a 125 kHz reader. For microSD, the vendor reports successful testing with SanDisk cards up to 32 GB; test the actual card and filesystem before recording audio.

If upload fails, hold the encoder-center BOOT button, press/release rear RST, release BOOT, select the stable USB port and retry the exact main-MCU image. Reset to run afterward. Restore a matching factory image/layout; do not guess a raw binary offset. [Download-mode instructions](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/docs/download_mode.md).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                             | Ordered check                                                                                                      |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| README example path not found       | Use the inspected tree's `examples/test_nrf24_send_recv`; do not rename files just to match old prose              |
| nRF24 not detected                  | Plus module present, CS44/CE43, SPI11/9/10, power and shared-bus chip selects                                      |
| Packet arrives but ACK fails        | Peer RX mode, pipe address, data rate, channel and ACK policy; distinguish one-way reception from a round trip     |
| NFC fails                           | PN532 I²C8/18, power/IRQ/reset, known 13.56 MHz tag and correct antenna side                                       |
| CC1101 fails after changing band    | Logical RF switch path, matched antenna, modulation and packet parameters; nRF24 settings are unrelated            |
| Display/card fails during radio use | Shared SPI arbitration and non-target CS states; return to one peripheral test                                     |
| Charging abnormal after custom code | Restore charger configuration and the 600 mA assembly limit; inspect USB/pack rather than forcing a larger setting |

Can this run a LoRa network because the source calls its pins `BOARD_LORA_*`? Those names are legacy aliases for this CC1101 path; they do not change the modem into SX1262.

## Downloads and technical documents

| Resource                                                                                                                                                                           | Exact scope                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| [Plus product](https://lilygo.cc/products/t-embed-cc1101-plus)                                                                                                                     | K268 external-antenna option and physical module distinction                         |
| [Pinned manufacturer source](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/tree/c36826e0f91311cb591c4545fccf91e254fc55dc)                                                       | Examples, dependencies, firmware, hardware and CAD                                   |
| [Base-board schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Embed-CC1101/c36826e0f91311cb591c4545fccf91e254fc55dc/hardware/T-Embed-CC1101%20V1.0%2024-07-29.pdf) | V1.0 base design; does not by itself establish all Plus module wiring                |
| [CC1101 shield schematic](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Embed-CC1101/c36826e0f91311cb591c4545fccf91e254fc55dc/hardware/cc1101-shield.pdf)                     | Sub-GHz daughterboard                                                                |
| [STEP/CAD directory](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/tree/c36826e0f91311cb591c4545fccf91e254fc55dc/3D_files)                                                      | Includes K268-01 keys and external-antenna models; verify actual mechanical revision |
| [Actual nRF24 test](https://github.com/Xinyuan-LilyGO/T-Embed-CC1101/blob/c36826e0f91311cb591c4545fccf91e254fc55dc/examples/test_nrf24_send_recv/test_nrf24_send_recv.ino)         | Current parser, shared SPI, polling and packet behavior                              |

The hardware directory additionally lists PN532, CC1101, BQ25896, BQ27220 documents. They are component references; charger integration limits remain the assembled board's limits.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Read sources include the Plus product, pinned README/configuration/definitions, actual display/encoder/nRF24 tests, download-mode/NFC instructions and base/shield schematics. The base power sheet was visually inspected. Original additions are the staged local/radio procedure, unique return messages and correction of the stale sample path/dependency table. No RF transmission or protected-card operation was executed.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
