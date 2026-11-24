---
description: >-
  Commission the 868 MHz T-Deck Plus, verify keyboard/touch and two-node
  Meshtastic, and develop with the correct shared SPI and GNSS pins.
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

# T-Deck Plus Meshtastic

{% hint style="info" %}
[**View LILYGO T-Deck Plus Meshtastic Support Meshtastic UI With Antennas on OpenELAB**](https://openelab.io/products/lilygo-t-deck-plus)

**Model / option:** Meshtastic Firmware / 868Mhz \[External Antennas] Black \[H736-03-Mesh] · **SKU:** `LILYGO-H736-03-Mesh`
{% endhint %}

## Product overview

### Plus hardware platform <a href="#lilygo-t-deck-plus-meshtastic-support-meshtastic-ui" id="lilygo-t-deck-plus-meshtastic-support-meshtastic-ui"></a>

T-Deck Plus is an ESP32-S3 handheld with keyboard, touch display, SX1262 radio and onboard GNSS.

### Purchased Plus option <a href="#product-link" id="product-link"></a>

This guide covers the **black 868 MHz external-antenna Meshtastic option H736-03-Mesh**. It is different from T-Deck Pro and from the original T-Deck without onboard GNSS. Keep the factory Meshtastic application for the first radio test; loading a manufacturer hardware demo replaces that application.

### Description: GNSS and expansion boundary <a href="#description" id="description"></a>

The Plus dedicates GPIO43/44 to GNSS, so its Grove connector is **not a spare expansion UART**. The manufacturer's current documentation identifies MIA-M10Q, while the repository also supports L76K GPS assemblies. Identify the received GNSS revision before sending receiver-specific configuration commands. [Plus documentation](https://wiki.lilygo.cc/products/t-deck-series/t-deck-plus/), [manufacturer GPS source](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/examples/GPSShield/GPSShield.ino).

## Applications

Use the assembled handheld for off-grid text, position reporting and local keyboard/touch interaction. Test a short direct link before exploring multi-hop routing. The ESP32-S3 also supports Wi-Fi/BLE development; these local/IP transports do not prove a LoRa message reached a peer.

For custom UI work, validate keyboard, touch, display, card and audio separately. A successful display initialization does not establish microphone operation or GNSS reception, and a cached map marker is not a new position fix.

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter          | Purchased Plus scope                                                                                     |
| ------------------ | -------------------------------------------------------------------------------------------------------- |
| Host               | ESP32-S3FN16R8, dual-core LX7 up to 240 MHz                                                              |
| Memory             | 16 MB flash; 8 MB PSRAM                                                                                  |
| Screen             | 2.8-inch ST7789, 320 × 240; GT911 capacitive touch                                                       |
| Inputs             | Separate I²C keyboard controller; trackball; touch                                                       |
| Radio              | SX1262; this SKU 868 MHz external antenna; +22 dBm chip/module limit is not a default deployment setting |
| GNSS               | Plus onboard receiver on GPIO43/44; MIA-M10Q and L76K source paths differ                                |
| Battery / charging | Built-in 2000 mAh pack; charge through the assembled USB-C interface                                     |
| Storage / audio    | microSD, ES7210 microphone path and speaker output                                                       |

Sources: [LILYGO Plus specifications](https://wiki.lilygo.cc/products/t-deck-series/t-deck-plus/), [reviewed pin definitions](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/examples/UnitTest/utilities.h).

## Hardware and connections

### Shared buses, power and occupied pins

Start with USB-C and the installed battery; do not feed external power into signal pads. Peripheral enable **GPIO10 must be HIGH** for battery operation. Main logic and schematic peripheral rails are 3.3 V domains; USB supply voltage is not permission to use 5 V GPIO.

| Function                                       | Main ESP32-S3 GPIO |
| ---------------------------------------------- | ------------------ |
| Peripheral power / battery ADC                 | 10 / 4             |
| I²C SDA / SCL; keyboard address                | 18 / 8; `0x55`     |
| Shared SPI SCK / MISO / MOSI                   | 40 / 38 / 41       |
| Radio CS / DIO1 / reset / busy                 | 9 / 45 / 17 / 13   |
| LCD CS / DC / backlight                        | 12 / 11 / 42       |
| Card CS / touch interrupt / keyboard interrupt | 39 / 16 / 46       |
| Trackball directions / center BOOT             | 3, 2, 15, 1 / 0    |
| Host GNSS TX / RX                              | 43 / 44            |
| Speaker I²S WS / BCK / output                  | 5 / 7 / 6          |
| ES7210 MCLK / LRCK / SCK / data                | 48 / 21 / 47 / 14  |

Keep **all non-selected SPI chip-select lines HIGH**, especially LCD12 and card CS39 while starting the radio. GPIO0 is the trackball-center/BOOT input. The pinned microphone source assigns audio MCLK48, LRCK21, SCK47 and data GPIO14; an I²S controller index is not a GPIO number. [Pin source](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/examples/UnitTest/utilities.h), [main schematic](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/schematic/schematic.pdf).

The old README and newer wiki describe the keyboard programming header in opposite physical orders. **Keyboard-coprocessor reflashing is excluded here until the received PCB orientation and schematic are matched.** Normal USB main-MCU recovery and keyboard reads do not require that header. Avoid the old suggestion to remove a resistor as a routine recovery step.

## Software and development resources

### Select an application and preserve its dependencies

For Meshtastic choose **T Deck**, using the [official hardware instructions](https://meshtastic.org/docs/hardware/devices/lilygo/tdeck/); do not choose T-Deck Pro. The reviewed Meshtastic source contains the `t-deck` environment.

For manufacturer demos the reviewed T-Deck repository commit is `9aac147a313975ad063594b3fe11e28a96d94936`. Its `T-Deck` environment pins `espressif32@6.3.0`, uses Arduino, 921600 upload and 115200 monitor. Choose **one** `src_dir`: UnitTest, Touchpad, Keyboard\_T\_Deck\_Master, GPSShield, Microphone, SD/audio or LVGL as applicable. Use bundled libraries; its legacy Arduino instructions specify core 2.0.14. Do not transplant the old TFT\_eSPI setup into an arbitrary newer core. The 26 July 2024 ST7789 initialization change is particularly relevant to incorrect colors/geometry. The separate Microphone example explicitly gates execution to Arduino-ESP32 core **2.0.9** (lines 15–23); do not assume the README’s general 2.0.14 configuration runs that legacy VAD example.

New factory work is directed by the README to LilyGoLib. That is a separate codebase/version decision; neither factory-demo target implies Meshtastic compatibility. LILYGO demo headers identify MIT licensing; Meshtastic is GPL-3.0. Preserve upstream licenses when redistributing modifications. [Pinned build configuration](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/platformio.ini).

## Getting started

### First working result: two-node Meshtastic message <a href="#first-working-result-two-node-meshtastic-message" id="first-working-result-two-node-meshtastic-message"></a>

Prerequisites: charged Plus, supplied 868 MHz antenna fitted, Meshtastic client and a second compatible radio. Record existing firmware/configuration before changing it.

1. Switch on and read the reported hardware and application version. Verify it is T-Deck/Plus firmware, then connect the client over the supported BLE/USB transport.
2. Set the permitted region. After restart, match the peer's modem preset, frequency slot and primary channel name/key. Start with ordinary client behavior; do not change multiple routing settings at once.
3. Type `DECK-A-01` locally or in the connected client. Observe it on the second physical radio, then return `DECK-B-01` and confirm that receipt.
4. Test touch coordinates, keyboard input and trackball navigation independently. A radio reply with a failed local key points to an input/UI boundary rather than an RF fault.
5. Enable device GNSS, move outdoors and check a fresh fix/time. Distinguish the node's receiver from phone-supplied position.
6. Remove USB and repeat the reply test. If peripherals fail only on battery after custom firmware, check GPIO10 power enable before changing RF parameters.

**Expected result:** two distinct received messages, working local controls and a separately confirmed current GNSS fix when enabled. See [Meshtastic device setup](https://meshtastic.org/docs/hardware/devices/lilygo/tdeck/).

### Original keyboard diagnostic for a development checkout

This small sketch reads key bytes without altering keyboard firmware. It replaces the main application, so save the stock image/configuration first. Use the repository's `T-Deck` environment and bundled Arduino dependencies, select a new example directory as `src_dir`, then compile before any upload.

```cpp
#include <Arduino.h>
#include <Wire.h>
void setup() {
  Serial.begin(115200);
  pinMode(10, OUTPUT);
  digitalWrite(10, HIGH);
  delay(500);
  Wire.begin(18, 8);
}
void loop() {
  Wire.requestFrom(uint8_t(0x55), uint8_t(1));
  while (Wire.available()) {
    int b = Wire.read();
    if (b > 0) Serial.printf("key_hex=%02X\n", b);
  }
  delay(20);
}
```

Press a printable key: **expected result** is a nonzero `key_hex` line at 115200 baud. No output calls for checking keyboard power, I²C pins/address and the selected example, not reflashing the coprocessor immediately. The interface comes from the [MIT manufacturer keyboard example](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/examples/Keyboard_T_Deck_Master/Keyboard_T_Deck_Master.ino); the diagnostic is newly written.

For GNSS diagnostics, the reviewed GPSShield source uses host RX44/TX43, tries L76K at 9600 and u-blox at 38400/9600. Its receiver configuration writes are model-specific: first identify which receiver is actually installed. For touch/card/audio use the corresponding manufacturer example individually, retaining shared-SPI selects and each example’s own core/dependency requirements.

### PlatformIO <a href="#platformio" id="platformio"></a>

For the legacy manufacturer project, install PlatformIO, clone the pinned source and open the **repository root** containing `platformio.ini`. Select exactly one source directory; for the newly written keyboard diagnostic, create `examples/OpenELABKeyboard` with that sketch and set `src_dir = examples/OpenELABKeyboard`. Keep its bundled libraries and the `T-Deck` environment.

```sh
git clone https://github.com/Xinyuan-LilyGO/T-Deck.git
cd T-Deck
git checkout 9aac147a313975ad063594b3fe11e28a96d94936
# Set the sole src_dir before compiling.
pio run -e T-Deck
```

Expected output is the selected example's artifact under `.pio/build/T-Deck/`; the build was not run here. After preserving the working application, choose the observed USB port for upload and monitor at 115200 baud. A manufacturer demo replaces Meshtastic and must be restored separately afterward.

### ArduinoIDE <a href="#arduinoide" id="arduinoide"></a>

For the **main ESP32-S3**, the inspected manufacturer settings image selects **ESP32S3 Dev Module**, core **2.0.14**, 16 MB QIO flash at 80 MHz, OPI PSRAM, **16M Flash (3MB APP/9.9MB FATFS)**, USB CDC enabled, Hardware CDC/JTAG, 921600 upload and Core 1 for sketch/events. USB DFU and Firmware MSC are disabled. Copy the individual bundled library directories into the Arduino libraries directory rather than nesting the entire `lib` folder inside it. Open the full chosen example and compile before upload. [Exact main-board settings image](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Deck/9aac147a313975ad063594b3fe11e28a96d94936/images/s3.jpg).

That image is for the S3 host, not the keyboard's C3 coprocessor. The legacy microphone sketch separately checks core 2.0.9; its I²S controller constant does not reserve GPIO0. Keep those example-specific constraints instead of interpreting a generic “downgrade” instruction as permission to mix arbitrary core/library versions.

#### Legacy S3 and C3 Arduino settings screenshots

The manufacturer supplied these **IDE settings screenshots**, not connector pinouts. The S3 image belongs to the main host; the C3 image documents a separate legacy coprocessor-development configuration. Its 4 MB/DIO settings must not replace the main host's 16 MB/QIO/OPI settings. These screenshots do not resolve the disputed keyboard programming-header orientation, so coprocessor reflashing remains excluded.

| Main ESP32-S3 host                                                                                                                                                                       | Legacy ESP32-C3 coprocessor reference                                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![LILYGO main ESP32-S3 Arduino settings: 16 MB flash, QIO and OPI PSRAM](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Deck/9aac147a313975ad063594b3fe11e28a96d94936/images/s3.jpg) | ![LILYGO legacy ESP32-C3 Arduino settings, a separate 4 MB DIO configuration rather than the Plus host target](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Deck/9aac147a313975ad063594b3fe11e28a96d94936/images/c3.jpg) |

_Attributed LILYGO repository documentation, commit `9aac147a313975ad063594b3fe11e28a96d94936`; both images were retrieved and visually inspected. Historical moving-source references retained:_ [_S3 image_](https://github.com/Xinyuan-LilyGO/T-Deck/raw/master/images/s3.jpg)_,_ [_S3 source file_](https://github.com/Xinyuan-LilyGO/T-Deck/blob/master/images/s3.jpg)_,_ [_C3 image_](https://github.com/Xinyuan-LilyGO/T-Deck/raw/master/images/c3.jpg)_,_ [_C3 source file_](https://github.com/Xinyuan-LilyGO/T-Deck/blob/master/images/c3.jpg)_. Use the pinned images above for this guide's reviewed configuration._

### Get Start: USB recovery and keyboard boundary <a href="#get-start" id="get-start"></a>

If automatic upload fails, keep the USB data connection attached, hold the **trackball center/BOOT**, press/release **RST**, release BOOT and reselect the enumerated port. Upload only the identified main-host target, then reset to run. If no port appears, check cable, power and the actual host/device mode before modifying hardware.

The former keyboard-header instructions described TX/RX/BOOT/RST/GND/VCC, but the newer wiki reverses the physical order. This guide preserves the topic as an **unresolved orientation boundary**, not an actionable pin order. Normal keyboard reads need no coprocessor flashing. The old resistor-removal issue is a historical diagnostic and is not a routine repair instruction. [Historical USB upload issue 62](https://github.com/Xinyuan-LilyGO/T-Deck/issues/62).

## Troubleshooting and FAQs

| Symptom                              | Ordered checks                                                                                                             |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| Radio initialization `-2`            | GPIO10 high, radio pins 9/45/17/13, SPI40/38/41 and LCD CS12 / card CS39 inactive; correct firmware target                 |
| LCD corrupted after a library update | Restore the pinned library/core pair and ST7789 sequence; check orientation separately from touch                          |
| Keyboard silent                      | Peripheral power, `0x55`, SDA18/SCL8 and main application; avoid unverified header wiring                                  |
| GNSS bytes but no fix                | Received module type, sky view, fresh time and receiver protocol; do not send L76K commands to u-blox                      |
| No USB upload                        | Known data cable; hold trackball center/BOOT, press/release reset, release BOOT, upload exact main-MCU image, reset to run |
| Messages only one direction          | Match region/modulation/channel key; verify each actual receiving radio rather than its send history                       |

Can the Grove connector accept another UART sensor? On Plus its pins belong to GNSS. Can the manufacturer UnitTest restore Meshtastic? No; reinstall the exact Meshtastic T Deck application and restore its configuration afterward.

## Downloads and technical documents

| Resource                                                                                                                                                                     | Scope                                                                   |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| [Plus wiki](https://wiki.lilygo.cc/products/t-deck-series/t-deck-plus/)                                                                                                      | Hardware, Arduino settings, examples and FAQ                            |
| [Pinned repository](https://github.com/Xinyuan-LilyGO/T-Deck/tree/9aac147a313975ad063594b3fe11e28a96d94936)                                                                  | Examples, libraries, images and enclosure/shell directory               |
| [Main schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Deck/9aac147a313975ad063594b3fe11e28a96d94936/schematic/schematic.pdf)                               | Main board; match physical PCB before modification                      |
| [MIA-M10Q GPS schematic PDF](https://raw.githubusercontent.com/Xinyuan-LilyGO/T-Deck/9aac147a313975ad063594b3fe11e28a96d94936/schematic/T-Deck-GPS%20V1.0%20%2024-03-29.pdf) | GNSS daughterboard, V1.0 29 March 2024                                  |
| [L76K alternative schematic](https://github.com/Xinyuan-LilyGO/T-Deck/blob/9aac147a313975ad063594b3fe11e28a96d94936/schematic/T-Deck-L76K%20V1.0%20%2024-08-12.pdf)          | Separate GNSS assembly; not permission to interchange receiver commands |
| [Meshtastic T-Deck support](https://meshtastic.org/docs/hardware/devices/lilygo/tdeck/)                                                                                      | Purchased firmware ecosystem and target                                 |

The manufacturer repository also indexes LoRaWAN\_Starter, microphone, LVGL/VNC, TF and audio projects. They are alternate application examples, not features proven in the purchased Meshtastic image.

### GitHub and historical development resources <a href="#github" id="github"></a>

The [pinned T-Deck repository](https://github.com/Xinyuan-LilyGO/T-Deck/tree/9aac147a313975ad063594b3fe11e28a96d94936) separates `examples`, bundled `lib`, `schematic`, `images` and shell/enclosure resources. Use `utilities.h` beside the chosen example as well as the build configuration; filenames from another example or the Pro repository do not establish Plus compatibility. The retained ST7789 commit and issues below explain historical initialization/upload failures; they do not replace the current model-specific procedure.

* [TFT\_eSPI ST7789 initialization sequence](https://github.com/Xinyuan-LilyGO/T-Deck/commit/6adb8884c689f174c29a6d7172a0daa367a582eb)
* [VisualStudioCode](https://code.visualstudio.com/)
* [Python](https://www.python.org/)
* [Arduino IDE](https://www.arduino.cc/en/software)
* [Historical diagnostic: TFT\_eSPI/issue 3329](https://github.com/Bodmer/TFT_eSPI/issues/3329)
* [Historical diagnostic: issue 62](https://github.com/Xinyuan-LilyGO/T-Deck/issues/62)

## References and validation

The Plus wiki, pinned manufacturer README/configuration/pins/keyboard/GPS sources, main and MIA-M10Q schematics and Meshtastic hardware support were read. Main/GNSS drawings were visually inspected; their model-specific details govern custom work. Source review corrected the old Grove expansion assumption and bounded the conflicting keyboard programming-header orientation. No full-copy reproduction of manufacturer tutorials is used.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
