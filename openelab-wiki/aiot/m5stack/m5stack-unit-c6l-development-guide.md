---
description: >-
  Power, connector allocation, firmware setup, original first-result procedures
  and recovery for M5Stack Unit C6L U202.
---

# M5Stack Unit C6L U202 Meshtastic and Development Guide

{% hint style="info" %}
[**View M5Stack Unit C6L U202 on OpenELAB**](https://openelab.io/products/m5stack-c6l-unit-for-meshtastic)

**Model:** Unit C6L U202 · **SKU:** `M5-U202`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

**Unit C6L U202** is a standalone ESP32-C6/SX1262 communication node with a small OLED, front button, RGB indicator and buzzer. It includes separate2.4GHz and868MHz RP-SMA antennas. It has no onboard GNSS receiver in the reviewed model; a Meshtastic position field can come from an authorized phone location share instead.

Unlike a passive Grove LoRa peripheral, C6L runs its own firmware and has its own USB programming target. Start with a local button/display program, then configure a Meshtastic two-node message. [Exact Unit C6L reference](https://docs.m5stack.com/en/unit/Unit_C6L).

## Applications

Use C6L as a USB-powered Meshtastic node, a compact raw-LoRa experiment or a local status terminal. TheOLED can show messages/configuration but is not a full keyboard interface. Plan an appropriate5V supply for portable operation; the product documentation does not establish a built-in battery or GNSS device.

## Specifications

| Parameter         | Unit C6L U202                                                             |
| ----------------- | ------------------------------------------------------------------------- |
| Controller        | ESP32-C6, HP RISC-V160MHz plus LP core20MHz                               |
| Flash             | 16MB                                                                      |
| LoRa              | SX1262; hardware868–923MHz range                                          |
| RF figures        | Maximum+22dBm;−147dBm sensitivity in low-data-rate LoRa mode              |
| OLED              | SSD1306,0.66inch,64×48 monochrome                                         |
| Antennas supplied | 2.4GHz3dBi Wi-Fi whip and868MHz3dBi LoRa whip; different connectors/roles |
| Supply            | 5V via USB-C or documented Grove input                                    |
| Local IO          | WS2812C RGB, buzzer, expander-connected front button                      |
| Size / mass       | 62×24×8mm excluding antennas;13.6g                                        |

[Model specification](https://docs.m5stack.com/en/unit/Unit_C6L). Vendor sleep/current figures are tied to supply path and firmware state; they do not establish battery runtime or your radio duty cycle.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Antennas, power and shared SPI

Install the antenna matching each **marked** connector before powering or transmitting. The2.4GHz antenna and868MHz LoRa antenna are not interchangeable by shape. Use the LoRa hardware's matched antenna and regional radio settings; the advertised868–923MHz capability does not authorize arbitrary transmission in that range.

| Subsystem                | ESP32-C6 route                                     |
| ------------------------ | -------------------------------------------------- |
| SX1262 SPI               | MOSI21/MISO22/clock20/CS23; BUSY19/IRQ7            |
| IO expander              | SDA10/SCL8, interrupt3; reset tied to system reset |
| SX1262 expander channels | P5 LNA enable, P6 RF switch, P7 reset              |
| OLED SPI                 | CS6, MOSI21, clock20, DC18, reset15                |
| RGB / buzzer             | Data2 / signal11                                   |
| Front button             | IO expander P0; use M5Unified button API           |
| USB                      | D+13/D−12                                          |
| Grove                    | Black GND/red5V/yellow5/white4                     |

Radio and OLED share clock20/MOSI21 with separate selects. Initialize the radio reset low for100ms then high, RF switch high and LNA enable high through the expander; bare SX1262 SPI communication alone does not enable the complete RF frontend. Grove5/4 is a different route from the internal expander10/8 bus.5V supply is not5V GPIO tolerance. Power off before changing Grove or antenna connections. [Exact pin/init table](https://docs.m5stack.com/en/unit/Unit_C6L#pinmap).

The manufacturer reports sleep currents696.86µA from Grove versus866.42µA from USB and active RX standby85.18mA from USB. Supply route and state must accompany these figures; they are not universal minima. Measure the actual application after disabling unnecessary display/radio loads.

![M5Stack C6L SX1262 RF front-end circuit](../../.gitbook/assets/m5stack-rank-144-diagram.png)

_M5Stack official technical illustration:_ [_original_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1185/U202-SCH_Sch_M5_C6_Lora_v0.2.3_2025_06_25_16_54_56_page_01.png)_. Verify drawing and physical revision together._

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Select **M5UnitC6L** in the M5Stack board package and install **M5Unified/M5GFX**. The [button API](https://docs.m5stack.com/en/arduino/unit_c6l/button) requires board manager≥3.2.4 and M5Unified≥0.2.11. The [Arduino first example](https://docs.m5stack.com/en/arduino/unit_c6l/program) is M5GFX **Basic→GameOfLife**. Add RadioLib only when developing raw-LoRa firmware.

The product's PlatformIO example uses the pioarduino ESP32-C6 platform and `esp32-c6-devkitc-1`, native-USB CDC and recorded M5Unified/RadioLib dependencies. Its moving develop ZIP is not a reproducible version pin; record the resolved revision or use the exact Arduino board target for the first run.

Meshtastic uses the distinct **M5Stack Unit C6L** firmware target. The manufacturer-linked Easyloader is an older diagnostic demo with MQTT/webserver disabled by default; it is not the current Meshtastic release. UiFlow2 similarly requires Unit C6L firmware, its controller selection and downloaded application. [Current model resources](https://docs.m5stack.com/en/unit/Unit_C6L).

## Getting started

### Original small-screen button counter

1. Fit both correctly marked antennas and disconnect external Grove devices.
2. Connect a USB-C data cable, install/select **M5UnitC6L** and compatible M5Unified/M5GFX.
3. Upload the sketch below. If needed, hold the side reset/power control until its green indicator turns red, release and reselect the bootloader port.
4. Restart, open115200baud and press the front button. Compare theOLED count with the serial count.

```cpp
#include <M5Unified.h>
unsigned presses=0;
void drawCount() {
  M5.Display.fillScreen(TFT_BLACK);
  M5.Display.setCursor(0,0);
  M5.Display.printf("C6L\nA:%u",presses);
}
void setup() {
  M5.begin();
  Serial.begin(115200);
  M5.Display.setTextSize(1);
  M5.Display.setTextColor(TFT_WHITE,TFT_BLACK);
  drawCount();
}
void loop() {
  M5.update();
  if (M5.BtnA.wasPressed()) {
    ++presses; drawCount();
    Serial.printf("C6L_BUTTON=%u\n",presses);
  }
  delay(5);
}
```

Expected result is one count increment per press on the64×48OLED and serial monitor. The code uses the expander-aware button API; guessing a direct button GPIO would bypass the actual circuit. It initializes no raw radio transmit loop. [Button support and minimum versions](https://docs.m5stack.com/en/arduino/unit_c6l/button).

### Meshtastic install, pairing and two-node message

Save any needed node/channel configuration before changing firmware. Follow the [current manufacturer Meshtastic procedure](https://docs.m5stack.com/en/guide/unit_c6l/meshtastic): open the official [web flasher](https://flasher.meshtastic.org/), select **M5Stack→M5Stack Unit C6L**, choose a release supporting this target and record its version. The reviewed tutorial demonstrates an Alpha release and115200baud; treat release channel as a deliberate choice rather than assuming a future release has the same support. Its **Full Erase and Install** removes existing configuration, so use that only for the intended clean install after backup.

After flashing, restart. Use short front-button presses to cycle the region choices and a long press to confirm the correct deployment region. Pair the mobile app with the four-character node name shown on theOLED and the displayed six-digit pairing code. Name the node, then configure a second node with the same channel/key and modem preset. Send a unique short message each way and compare the actual received payload/time. A phone BLE connection alone is not a LoRa link test.

In the reviewed C6L Meshtastic firmware, Bluetooth and Wi-Fi are **not simultaneously available**. Enabling Wi-Fi disables phone BLE access. To recover, connect USB to the [web client](https://client.meshtastic.org/) and disable Wi-Fi; Bluetooth is then re-enabled. This is a firmware-specific constraint, not a claim that every ESP32-C6 application has identical coexistence behavior.

### Understand device pages and location

Short-press the front key to move through home, latest messages, signal/node information, location, LoRa configuration, memory/version and time pages. Long-press opens a page menu; short-press selects and long-press confirms. The GNSS/location page stays empty without a location source because U202 has no built-in GNSS. Grant phone-location sharing only when intended, then verify the reported source rather than inventing satellite data. Current time display may depend on phone connection in the reviewed application.

For raw-LoRa firmware, first reset/enable the expander-controlled RF path described above, confirm RadioLib initialization and use a matched peer modem configuration. Separate this from Meshtastic networking: replacing mesh firmware with a raw packet sketch changes protocol behavior. UiFlow2 first tests should similarly use one localOLED/RGB block, then Run Always and a restart to verify persistence.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                | Diagnosis / recovery                                                                                                 |
| -------------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| No USB port                            | Data cable/direct USB → side hold until green-to-red boot indicator → release and reselect port.                     |
| OLED works, front button does not      | Use M5UnitC6L/M5Unified minimums, frequent M5.update and the expander-aware BtnA mapping.                            |
| RF init but no reception               | Antenna identity → region/modem match → expander P5/P6/P7 sequence → actual peer payload/CRC.                        |
| Phone disappeared after enabling Wi-Fi | Use USB Meshtastic Web Client to disable Wi-Fi and restore BLE in this firmware.                                     |
| Location page empty                    | No onboard GNSS; configure an intended external/phone location source instead of waiting for nonexistent satellites. |
| Factory demo lacks MQTT/webserver      | Older diagnostic Easyloader limitation; use exact current Meshtastic target when that is the required application.   |

## Downloads and technical documents

The download set below separates the Unit carrier schematic from the Stamp C6LoRa radio circuit. The manufacturer Meshtastic guide covers mobile permissions, button menus and Wi-Fi/BLE recovery; preserve its firmware-version context.

| Official file or repository                                                                                                                 | Use                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [Unit C6L Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1185/SCH_Unit_C6L_SCH_B0.4.1_20250827_2025_09_02_15_04_22.pdf)   | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Stamp C6LoRa Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1223/S012-SCH_Sch_M5_C6_Lora_v0.2.3_2025_12_02_19_14_35.pdf) | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Unit C6L Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1185/U202-MODEL-SIZE-unit-2sma.pdf)                              | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Unit C6L Structure Files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U202_Unit_C6L/Structures)                            | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [SX1262](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1177/DS_SX1261_2_V2-2.pdf)                                                        | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ESP32-C6](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/505/esp32-c6_datasheet_en.pdf)                                                  | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [download](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1185/Unit-C6L-UserDemo-easyloader.exe)                                          | Manufacturer-listed exact model document / maintained source; use the scope described above. |

### Additional model references <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

* [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U202_Unit_C6L/Structures/Unit_C6L.stl)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

This guide uses the exact sold SKU and the [manufacturer reference](https://docs.m5stack.com/en/unit/Unit_C6L). Specifications are manufacturer-reported; diagnostic order and first-result programs are original engineering work. The exact U202 contents, radio/OLED shared bus, expander initialization and Meshtastic firmware limitations were reviewed. No phone pairing, firmware flash, current measurement or RF exchange was run.

**Review:** 24 November 2026. Manufacturer documentation and the linked SDK interfaces were reviewed. **Compilation, firmware flashing and hardware operation: not run.** Expected results above are commissioning checkpoints, not observed bench measurements.
