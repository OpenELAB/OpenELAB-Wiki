---
description: >-
  Power, connector allocation, firmware setup, original first-result procedures
  and recovery for M5Stack StickS3 K150.
---

# M5StickS3 ESP32-S3 Mini IoT Dev Kit Engineering Guide

{% hint style="info" %}
[**View M5Stack StickS3 K150 on OpenELAB**](https://openelab.io/products/m5sticks3-esp32s3-mini-iot-dev-kit)

**Model:** StickS3 K150 · **SKU:** `M5-K150`
{% endhint %}

## Product overview <a href="#m5sticks3-esp32-s3-mini-iot-dev-kit-engineering-guide" id="m5sticks3-esp32-s3-mini-iot-dev-kit-engineering-guide"></a>

<a href="https://openelab.io/products/m5sticks3-esp32s3-mini-iot-dev-kit" class="button primary">Product link: M5StickS3 ESP32S3 Mini IoT Dev Kit on OpenELAB</a>

### Quick Summary

* **Product:** M5Stack M5StickS3, OpenELAB SKU M5-K150.
* **Processor:** ESP32-S3-PICO-1-N8R8, dual-core Xtensa LX7 up to 240 MHz.
* **Memory:** 8 MB flash and 8 MB octal PSRAM.
* **Connectivity:** 2.4 GHz Wi-Fi; Bluetooth capability is provided by the ESP32-S3 platform, but check the chosen framework and firmware example for support.
* **Human interface:** 135 x 240 ST7789P3 LCD, two buttons, microphone, speaker, IR TX/RX, IMU, and magnetic back.
* **Best fit:** compact IoT controllers, voice assistants, BLE/Wi-Fi remotes, smart home panels, infrared bridges, handheld debugging tools, and education projects.

### What Is the M5StickS3?

The M5StickS3 is a self-contained mini development kit rather than a bare ESP32-S3 module. Engineers get a ready-to-use enclosure, display, power management, battery, audio, IMU, IR, and expansion connectors, which reduces wiring work for early prototypes. Compared with a generic ESP32-S3 board, the engineering value is the integrated human-machine interface and M5Stack software ecosystem: Arduino with M5Unified/M5GFX, UiFlow2, ESP-IDF, PlatformIO, and example applications.

Because the board is small and battery powered, it is especially useful when the project needs local status display, simple buttons, motion sensing, voice/audio interaction, or IR control in a handheld form factor. For permanent industrial installations, validate operating temperature, Grove current, enclosure mounting, power source, and RF environment before deployment.

## Applications

### Project References and Application Ideas

* [M5Stack Xiaozhi Voice Assistant for StickS3](https://docs.m5stack.com/en/guide/realtime/xiaozhi/sticks3): official example showing the StickS3 as a compact Wi-Fi voice interaction device with microphone, speaker, and display.
* [M5Stack ESP-Claw Firmware Flashing for StickS3](https://docs.m5stack.com/en/guide/agent/esp_claw/sticks3): official agent/firmware workflow for turning the StickS3 into a compact interactive controller.
* [openbrt/omniremote](https://github.com/openbrt/omniremote): community project using M5StickS3 as a Wi-Fi/IR air-conditioner remote and local smart-home controller.
* [openbrt/voxstick](https://github.com/openbrt/voxstick): community project using StickS3 as a USB push-to-talk dictation stick with microphone, HID keyboard behavior, and IMU-based auto-mute ideas.
* [Saqoosha/HDZap](https://github.com/Saqoosha/HDZap): community reference for using M5StickS3 as a BLE and ESP-NOW bridge in an FPV timing/OSD workflow.
* [steveruizok/chat-stick](https://github.com/steveruizok/chat-stick): community live-chat experiment for M5StickS3 that demonstrates a small-screen connected interaction pattern.

## Specifications

### Key Specifications

| Parameter             | M5StickS3                                                                                 | Engineering note                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| SoC                   | ESP32-S3-PICO-1-N8R8, dual-core Xtensa LX7, up to 240 MHz                                 | Suitable for Wi-Fi IoT, local UI, audio/voice front ends, and edge-control tasks.                |
| Flash                 | 8 MB                                                                                      | Use an 8 MB partition table for PlatformIO/Arduino projects.                                     |
| PSRAM                 | 8 MB octal PSRAM                                                                          | Useful for display buffers, networking, audio buffers, and larger applications.                  |
| Display               | ST7789P3, 135 x 240 resolution                                                            | Use M5GFX or M5Unified for display initialization and drawing.                                   |
| IMU                   | BMI270                                                                                    | 6-axis sensing for gesture input, orientation, vibration, and motion state detection.            |
| Audio                 | ES8311 24-bit I2S audio codec, MEMS microphone, AW8737 amplifier, 8 ohm 1 W speaker       | Good for voice assistant prototypes, alerts, push-to-talk devices, and local audio feedback.     |
| IR                    | Infrared transmitter and receiver                                                         | IR receiving requires the speaker amplifier to be turned off according to M5Stack's notice.      |
| Power input           | USB Type-C 5 V; configurable Grove/EXT\_5V power modes                                    | Do not feed power into an interface that is currently configured as 5 V output.                  |
| Battery               | 250 mAh lithium battery                                                                   | Useful for portable demos; measure runtime under your actual Wi-Fi, display, and audio workload. |
| Grove load capacity   | No load: 5 V max; up to about 4.88 V at 0.38 A                                            | Budget external module current carefully; high-current loads should use a separate supply.       |
| Power consumption     | Power off 14.02 uA; L1 52.47 uA; L2 102.40 uA; L3A 36.69 mA; full load 519.02 mA at 4.2 V | Use sleep modes and disable display/audio/peripherals for battery projects.                      |
| Operating temperature | 0 to 40 C                                                                                 | Not specified for harsh outdoor or high-temperature industrial environments.                     |
| Dimensions            | 48.0 x 24.0 x 15.0 mm                                                                     | Use the official model-size PDF for enclosure, mount, and panel design.                          |
| Weight                | 20.0 g                                                                                    | Light enough for handheld, wearable-style, and mobile robot accessory use.                       |

## Hardware and connections

### Hardware Architecture

* **ESP32-S3 compute core:** handles Wi-Fi networking, application logic, UI rendering, audio I/O, sensor reading, and expansion bus control.
* **LCD and buttons:** provide a local UI for configuration, status, pairing, or menu-driven control without an external display.
* **BMI270 IMU:** enables orientation, tap/motion events, pedometer-style applications, gesture input, and simple vibration monitoring.
* **ES8311 audio path:** supports microphone input and speaker output over I2S for voice assistant, push-to-talk, sound meter, notification, and alert projects.
* **IR transmitter/receiver:** supports smart home remote-control experiments, but IR reception conflicts with the speaker power amplifier state.
* **M5PM1 power management:** manages battery, external output control, power states, charge status, and related power-control signals.
* **Expansion connectors:** Grove HY2.0-4P and Hat2-Bus expose GPIO, 5 V, 3.3 V, battery, and power inputs for M5Stack units, hats, and custom hardware.

### Pin Map and Interfaces

| Function          | ESP32-S3 pins / interface                                                              | Notes                                                                                                  |
| ----------------- | -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| LCD ST7789P3      | MOSI G39, SCK G40, RS G45, CS G41, RST G21, BL G38                                     | Prefer M5GFX/M5Unified initialization to avoid mismatched display timing or backlight behavior.        |
| IMU and M5PM1 I2C | SCL G48, SDA G47; BMI270 address 0x68; M5PM1 address 0x6e                              | Shared I2C bus for IMU and power-management device.                                                    |
| Audio ES8311      | MCLK G18, DOUT G14, BCLK G17, LRCK G15, DIN G16, SCL G48, SDA G47; ES8311 address 0x18 | I2S audio plus shared I2C control bus.                                                                 |
| Buttons           | KEY1 G11, KEY2 G12                                                                     | Use debouncing and consider long-press/double-click behavior in UI firmware.                           |
| IR                | IR\_TX G46, IR\_RX G42                                                                 | Turn off the speaker amplifier before using IR receive.                                                |
| Grove HY2.0-4P    | Black GND, Red 5 V, Yellow G9, White G10                                               | Can be used with compatible M5Stack units or custom 5 V/GPIO peripherals.                              |
| Hat2-Bus          | GND, G5, EXT\_5V, G4, Boot, G6, G1, G7, G8, G43, BAT, G44, 3V3\_L2, G2, 5V\_IN, G3     | Check the schematic before connecting hats or custom boards, especially where power pins are involved. |

### Power and Integration Notes

* **USB Type-C is the simplest bench supply.** Use USB for first programming, serial logs, and firmware recovery.
* **Grove and Hat2-Bus power modes matter.** The bottom Grove interface can be configured as 5 V input or output. In output mode, power input should only come from USB or the 5VIN pin on the top Hat2-Bus. Feeding power into another output interface can damage the device.
* **M5Unified disables EXT\_5V output by default.** If an external Grove/Hat/IR circuit does not power up, check whether `M5.Power.setExtOutput(true)` is required for your design.
* **Battery audio has a practical limit.** M5Stack recommends keeping speaker volume below 75% when USB is not connected to avoid unexpected reboots from excessive power draw.
* **IR receive and speaker amplifier conflict.** Turn off the speaker amplifier before receiving IR signals.
* **For production enclosures:** review thermal path, speaker opening, microphone opening, USB access, reset/power button access, RF clearance, and magnet mounting force.

### Exact StickS3 routing

| Function                    | Connection                                                    |
| --------------------------- | ------------------------------------------------------------- |
| Internal I2C                | SDA47 / SCL48; BMI2700x68, M5PM10x6E, ES83110x18              |
| Screen                      | ST7789P3;135×240                                              |
| User buttons                | GPIO11 /12                                                    |
| IR                          | TX46 / RX42                                                   |
| Grove yellow / white        | GPIO9 /10; black GND, red configurable5V rail                 |
| Codec                       | MCLK18, DOUT14, BCLK17, LRCK15, DIN16                         |
| PMIC-controlled peripherals | M5PM1 PYG2 L3B rail, PYG3 speaker control, PYG4 IMU interrupt |

The Grove/EXT\_5V rail defaults to **input** mode. In output mode, power the system only through USB or the dedicated Hat2 **5VIN**; do not feed another5V supply into an output-enabled Grove/EXT\_5V rail. The reported maximum Grove load point is4.88V at0.38A, not an unlimited5V supply. Hat Mini JoyC U156, Hat Mini EncoderC U157 and Hat18650C U080 are structurally incompatible. [Exact power and fit notes](https://docs.m5stack.com/en/core/StickS3).

## Software and development resources

### Software Development Workflow

1. **Start with the official docs.** Confirm the current M5Stack StickS3 documentation, schematic, model-size PDF, and quick-start guides.
2. **Choose a framework.** Use UiFlow2 for fast visual prototyping, Arduino/M5Unified for C++ firmware, PlatformIO for reproducible builds, or ESP-IDF for lower-level ESP32-S3 control.
3. **Install board support and libraries.** For Arduino/PlatformIO projects, use M5Unified, M5GFX, and M5PM1 where needed.
4. **Configure the ESP32-S3 build.** Use an 8 MB partition table, enable PSRAM, and set USB CDC on boot when serial console behavior is required.
5. **Verify each subsystem separately.** Test display, buttons, Wi-Fi, battery status, IMU, microphone, speaker, IR TX/RX, and Grove expansion before combining features.
6. **Measure power early.** Battery runtime depends strongly on Wi-Fi duty cycle, display brightness, audio volume, sleep mode, and external module current.

### Useful PlatformIO Configuration

M5Stack's documentation provides this PlatformIO starting point for Arduino-based projects:

```ini
[env:m5stack-sticks3]
platform = espressif32@6.12.0
board = esp32-s3-devkitc-1
framework = arduino
board_build.arduino.partitions = default_8MB.csv
board_build.arduino.memory_type = qio_opi
build_flags =
    -DESP32S3
    -DBOARD_HAS_PSRAM
    -mfix-esp32-psram-cache-issue
    -DCORE_DEBUG_LEVEL=5
    -DARDUINO_USB_CDC_ON_BOOT=1
    -DARDUINO_USB_MODE=1
lib_deps =
    M5Unified=https://github.com/m5stack/M5Unified
    M5PM1=https://github.com/m5stack/M5PM1
```

For Arduino choose **M5StickS3**, M5Unified and M5GFX; add M5PM1 for explicit power work. The official first demonstration is **ScrollGraph**. The documented PlatformIO baseline uses espressif32@6.12.0,8MB partitions and qio\_opi PSRAM; do not change it to a Quad-PSRAM CoreS3 profile. [Current Arduino route](https://docs.m5stack.com/en/arduino/m5sticks3/program).

## Getting started

### Bring-Up Checklist

1. Inspect the device and confirm USB-C power, display boot, and battery charge behavior.
2. Open the official M5Stack StickS3 docs and download the schematic and model-size PDF.
3. Flash a minimal Arduino or UiFlow2 example and confirm serial logging works.
4. Run subsystem tests: LCD, buttons, Wi-Fi, IMU, microphone, speaker, IR TX/RX, battery reading, and Grove output.
5. For custom hardware, check the Hat2-Bus and Grove pin map against the schematic before connecting power.
6. Measure current draw in active, idle, display-on, audio-on, Wi-Fi-connected, and sleep states.
7. Save a known-good firmware image and document library versions before adding application complexity.

### Engineering Best Practices

* **Use official libraries first.** Start with M5Unified, M5GFX, and M5PM1 before writing low-level drivers.
* **Separate UI and network loops.** Avoid display redraws or blocking Wi-Fi calls that make the device feel unresponsive.
* **Keep audio power in mind.** Speaker playback, Wi-Fi transmission, and display backlight can create peak current events.
* **Debounce buttons and define power gestures.** Reserve long press or double click for reset, pairing, menu, or safe shutdown behavior.
* **Design around the 0 to 40 C rating.** For outdoor, vehicle, or industrial use, validate temperature and enclosure heating.
* **Use the schematic before attaching custom hats.** The expansion bus exposes useful power rails, but wrong power direction can damage the device.

### Original local button counter

After the stock display example works, replace it with this original sketch. It uses the model's M5Unified initialization, not raw display wiring. Select the exact target listed above, then upload with external wiring disconnected.

```cpp
#include <M5Unified.h>
unsigned presses = 0;
void setup() {
  M5.begin();
  Serial.begin(115200);
  M5.Display.fillScreen(TFT_BLACK);
  M5.Display.setTextColor(TFT_WHITE, TFT_BLACK);
  M5.Display.setTextSize(2);
  M5.Display.setCursor(8, 12);
  M5.Display.println("Input check");
}
void loop() {
  M5.update();
  if (M5.BtnA.wasPressed()) {
    Serial.printf("presses=%u\n", ++presses);
    M5.Display.fillRect(8, 44, M5.Display.width()-16, 32, TFT_BLACK);
    M5.Display.setCursor(8, 44);
    M5.Display.printf("%u", presses);
  }
  delay(5);
}
```

Expected result is an increasing count on the screen and at 115200 baud for each model-mapped A-button press. Holding the button is not intended to generate continuous counts. A count lost after reboot is normal: this example keeps no persistent state. Keep the loop responsive before adding an animation, network request or sensor transaction. Source API: [M5Unified](https://github.com/m5stack/M5Unified); source-reviewed, not compiled or run.

### Audio, IR and power commissioning

Play one moderate tone with M5Unified before adding microphone capture. Check the ES8311 clock/rate and speaker rail when only one direction works. For IR, use a known compatible receiver and one deliberate user-triggered frame on46, then a separate receive test on42; the speaker and receiver do not share an application protocol. For the IMU, record stationary acceleration and one axis rotation before adding orientation filtering.

Use [M5PM1 layer control](https://docs.m5stack.com/en/arduino/m5sticks3/m5pm1) to plan L1/L2/L3A/L3B transitions. Record supply path and enabled rails when measuring sleep: the manufacturer reports14.02µA power-off,52.47µA L1 and102.40µA L2 at4.2V, with much higher active-state consumption. These are vendor state measurements, not measured battery-life results for this program. Configure one wake source and confirm wake before switching off another rail.

UiFlow2 uses the StickS3 firmware and controller selection, USB WebTerminal or the current Access Code. Run Once tests temporarily; Run Always plus a restart establishes autonomous operation. Voice/ESP-Claw packages are separate applications; verify their backend/account requirements after local display and audio. Use current [StickS3 XiaoZhi](https://docs.m5stack.com/en/guide/sticks3/xiaozhi_voice_assistant) and [ESP-Claw](https://docs.m5stack.com/en/guide/sticks3/esp_claw) entries rather than the retired realtime/agent paths.

## Troubleshooting and FAQs

### FAQ

<details>

<summary>What is the M5StickS3 used for?</summary>

The M5StickS3 is used for compact IoT controllers, smart home remotes, voice assistant prototypes, handheld status displays, Wi-Fi tools, IR bridges, motion-aware gadgets, and rapid ESP32-S3 development.

</details>

<details>

<summary>What chip does the M5StickS3 use?</summary>

It uses the ESP32-S3-PICO-1-N8R8 with a dual-core Xtensa LX7 processor up to 240 MHz, 8 MB flash, and 8 MB octal PSRAM.

</details>

<details>

<summary>Does the M5StickS3 have a display?</summary>

Yes. It has a 1.14 inch ST7789P3 LCD with 135 x 240 resolution, suitable for local status, menus, QR codes, simple dashboards, and debugging output.

</details>

<details>

<summary>Can the M5StickS3 run Arduino?</summary>

Yes. M5Stack provides an Arduino quick-start guide and recommends M5Unified, M5GFX, and M5PM1 libraries for common device features.

</details>

<details>

<summary>Can the M5StickS3 run UiFlow2?</summary>

Yes. M5Stack provides a UiFlow2 quick-start guide for visual programming and rapid application development.

</details>

<details>

<summary>Can I use ESP-IDF or PlatformIO?</summary>

Yes. The official product page lists ESP-IDF and PlatformIO as supported development platforms. For PlatformIO, start with the ESP32-S3 DevKitC board profile, 8 MB partition table, PSRAM enabled, and M5Stack libraries.

</details>

<details>

<summary>Does the M5StickS3 support audio?</summary>

Yes. It includes an ES8311 24-bit I2S audio codec, MEMS microphone, AW8737 power amplifier, and 8 ohm 1 W speaker, making it useful for voice input, alerts, and audio feedback.

</details>

<details>

<summary>Does the M5StickS3 support IR remote control?</summary>

Yes. It integrates IR transmitter and receiver pins. M5Stack notes that the speaker power amplifier must be turned off when using IR reception.

</details>

<details>

<summary>What should I know about Grove power?</summary>

The Grove interface can be configured as 5 V input or output. When configured as output, power input should only come through USB or 5VIN on the top Hat2-Bus. Avoid feeding power into an output interface.

</details>

<details>

<summary>Is the M5StickS3 good for battery projects?</summary>

It is suitable for portable prototypes, but battery runtime depends heavily on Wi-Fi, display brightness, audio volume, external modules, and sleep strategy. Measure your actual firmware rather than relying on a single nominal runtime estimate.

</details>

<details>

<summary>Where can I find the schematic and mechanical drawing?</summary>

The official M5Stack StickS3 documentation links both the StickS3 schematic PDF and the StickS3 model-size PDF. Use these files before designing custom hats, mounts, or enclosures.

</details>

## Downloads and technical documents

### Official Resources and Downloads

| Resource                            | Use                                                                         | Link                                                                                                                                    |
| ----------------------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| OpenELAB product page               | Purchase and listing details                                                | [M5StickS3 on OpenELAB](https://openelab.io/products/m5sticks3-esp32s3-mini-iot-dev-kit)                                                |
| M5Stack StickS3 documentation       | Official specifications, notices, pin map, quick starts, and software links | [M5Stack StickS3 docs](https://docs.m5stack.com/en/core/StickS3)                                                                        |
| StickS3 schematic                   | Electrical design, connector reference, power path, and subsystem review    | [StickS3 Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1207/K150_Stick_S3_PRJ_V0.6_20251111_2025_11_17_16_10_24.pdf) |
| StickS3 model size drawing          | Mechanical integration and enclosure planning                               | [StickS3 Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1207/K150-sticks3.pdf)                                        |
| ESP32-S3 technical reference manual | SoC peripherals, memory, timers, Wi-Fi/Bluetooth platform details           | [ESP32-S3 TRM](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/477/esp32-s3_technical_reference_manual_en.pdf)                         |
| ES8311 datasheet                    | Audio codec integration reference                                           | [ES8311 PDF](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/atom/Atomic%20Echo%20Base/ES8311.pdf)                  |
| BMI270 datasheet                    | IMU behavior, registers, motion features, and sensor limits                 | [BMI270 PDF](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMI270.PDF)                        |
| M5PM1 datasheet                     | Power management behavior and registers                                     | [M5PM1 Power Management Chip](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1207/M5PM1_Datasheet_EN.pdf)                             |
| Arduino quick start                 | First C++ firmware workflow                                                 | [StickS3 Arduino Quick Start](https://docs.m5stack.com/en/arduino/m5sticks3/program)                                                    |
| UiFlow2 quick start                 | Visual programming and rapid prototype workflow                             | [StickS3 UiFlow2 Quick Start](https://docs.m5stack.com/en/uiflow2/sticks3/program)                                                      |
| M5PM1 Arduino guide                 | Battery and power output control                                            | [StickS3 M5PM1 Power Management](https://docs.m5stack.com/en/arduino/m5sticks3/m5pm1)                                                   |
| M5Unified                           | Unified Arduino driver layer for M5Stack devices                            | [m5stack/M5Unified](https://github.com/m5stack/M5Unified)                                                                               |
| M5GFX                               | Display graphics library                                                    | [m5stack/M5GFX](https://github.com/m5stack/M5GFX)                                                                                       |
| M5PM1 library                       | Arduino power-management library                                            | [m5stack/M5PM1](https://github.com/m5stack/M5PM1)                                                                                       |
| ESP-Claw firmware flashing          | Official flashing workflow for the ESP-Claw agent example                   | [StickS3 ESP-Claw Firmware Flashing](https://docs.m5stack.com/en/guide/agent/esp_claw/sticks3)                                          |
| Xiaozhi voice assistant             | Official voice-assistant application guide                                  | [StickS3 Xiaozhi Voice Assistant](https://docs.m5stack.com/en/guide/realtime/xiaozhi/sticks3)                                           |

| Official file or repository                                                                                                             | Use                                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [StickS3 GeaStack Firmware Flashing](https://github.com/geastack/targets/tree/main/targets/esp32-s3-m5stack-sticks3)                    | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [StickS3 Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1207/K150_Stick_S3_PRJ_V0.6_20251111_2025_11_17_16_10_24.pdf) | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [StickS3 Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1207/K150-sticks3.pdf)                                        | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [StickS3 Structure Files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K150_StickS3/Structures)                          | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ESP32S3](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/477/esp32-s3_technical_reference_manual_en.pdf)                              | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ES8311](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/atom/Atomic%20Echo%20Base/ES8311.pdf)                      | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [BMI270](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMI270.PDF)                            | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [M5PM1 Arduino Library](https://github.com/m5stack/M5PM1)                                                                               | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [StickS3 Arduino M5Unified Driver Library](https://github.com/m5stack/M5Unified)                                                        | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [StickS3 Arduino M5GFX Driver Library](https://github.com/m5stack/M5GFX)                                                                | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [StickS3 UiFlow2 Docs](https://uiflow-micropython.readthedocs.io/en/latest/controllers/sticks3.html)                                    | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [M5PM1 Power Management Chip](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1207/M5PM1_Datasheet_EN.pdf)                             | Manufacturer-listed exact model document / maintained source; use the scope described above. |

## References and validation

Exact-model [manufacturer hardware reference](https://docs.m5stack.com/en/core/StickS3) and model-specific software links in the procedures establish this guide's hardware scope. Electrical values are manufacturer-reported; external-project behavior and diagnostic order are original engineering guidance.

### Source Notes

* Product details: [OpenELAB M5StickS3 product page](https://openelab.io/products/m5sticks3-esp32s3-mini-iot-dev-kit).
* Official specifications, notices, pin map, software links, schematics, and model-size drawing: [M5Stack StickS3 documentation](https://docs.m5stack.com/en/core/StickS3).
* Official software libraries: [M5Unified](https://github.com/m5stack/M5Unified), [M5GFX](https://github.com/m5stack/M5GFX), and [M5PM1](https://github.com/m5stack/M5PM1).
* Community project references are included as examples of possible application patterns; review each repository's license, maturity, and code quality before reuse.
* Reviewed for OpenELAB wiki publication on 2026-05-25.

### Official documentation and development resources

Use [StickS3](https://docs.m5stack.com/en/core/StickS3) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K150`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                       |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5sticks3/program)                                     |
| UIFlow2 workflow             | [Read uiflow2 workflow](https://docs.m5stack.com/en/uiflow2/sticks3/program)                                                   |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5sticks3/m5pm1?id=spk%20amp)                          |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K150_StickS3/Structures)             |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K150_StickS3/Structures/StickS3.stl) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5sticks3/m5pm1)                                       |
| Official source: M5PM1       | [Read official source: m5pm1](https://github.com/m5stack/M5PM1)                                                                |
| Official source: M5Unified   | [Read official source: m5unified](https://github.com/m5stack/M5Unified)                                                        |
| Official source: M5GFX       | [Read official source: m5gfx](https://github.com/m5stack/M5GFX)                                                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.

**Review:** 24 November 2026. Manufacturer documentation and the linked SDK interfaces were reviewed. **Compilation, firmware flashing and hardware operation: not run.** Expected results above are commissioning checkpoints, not observed bench measurements.
