---
description: >-
  Power, connector allocation, firmware setup, original first-result procedures
  and recovery for M5Stack Cap LoRa-1262 U214.
---

# M5Stack Cap LoRa-1262 U214 Radio and GNSS Guide

{% hint style="info" %}
[**View M5Stack Cap LoRa-1262 U214 on OpenELAB**](https://openelab.io/products/m5stack-cap-lora-1262)

**Model:** Cap LoRa-1262 U214 · **SKU:** `M5-U214`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

**Cap LoRa-1262 U214** adds an SX1262 radio and ATGM336H-6N GNSS receiver to **Cardputer-Adv** through the14-pin Cap-Bus. It is an accessory, not a standalone ESP32 controller and not the complete K152 Mesh Kit. The current official page also covers CardputerZero compatibility; the explicit pin table and examples here use Cardputer-Adv. Do not apply these GPIO numbers to another host without its own map.

Unlike the older Cap LoRa868, U214 contains a PI4IOE5V6408 expander whose P0 must enable the RF antenna switch. An application that can talk to the SX1262 over SPI can still have no useful RF path if that switch is left disabled. [Exact U214 reference](https://docs.m5stack.com/en/cap/Cap_LoRa-1262).

## Applications

Build a portable LoRa packet tester, GNSS logger or custom mesh terminal using a known working Cardputer-Adv. A two-node message and an outdoor valid GNSS fix are separate commissioning results. Meshtastic authorization of the K152 bundle is a distinct product entitlement; a separately purchased cap does not establish it.

## Specifications

| Parameter                        | U214 scope                                                        |
| -------------------------------- | ----------------------------------------------------------------- |
| Radio / host bus                 | SX1262; SPI                                                       |
| Hardware band / TX / sensitivity | 868–923MHz; maximum+22dBm;−147dBm in low-data-rate LoRa mode      |
| Modems / bitrate                 | LoRa≤62.5kbps; FSK≤300kbps; FSK/GFSK/MSK/LoRa support             |
| Radio supply observation         | 5V at163.4mA manufacturer operating point; budget host separately |
| GNSS                             | ATGM336H-6N / AT6668; NMEA0183v4.1; UART115200baud8N1             |
| Constellations                   | GPS/QZSS/BeiDou/Galileo/GLONASS;50channels                        |
| Position/update                  | <1.5m CEP50; up to10Hz; values depend on reception/configuration  |
| Nominal first fix                | 23s cold /1s hot manufacturer figures, not indoor guarantees      |
| Antenna / mounting               | RP-SMA868MHz whip,3dBi; recommended M2×4mm fixing screws          |
| Size / mass                      | 84×24×15.2mm;22.1g excluding antenna                              |

[Manufacturer specifications](https://docs.m5stack.com/en/cap/Cap_LoRa-1262). Band coverage is hardware capability; configure the permitted regional channel/power before transmission. Mechanical screw length must not press into the PCB.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

1. Turn off the Cardputer host before installing/removing the cap. CardputerZero explicitly does **not** support hot-swapping.
2. Align the14-pin header with the exact host socket and seat it evenly; do not offset by a row.
3. Fit the matched RP-SMA LoRa antenna before powering the RF system. Keep the GNSS antenna area clear for an outdoor reception test.

| Cap function                    | Cardputer-Adv connection                       |
| ------------------------------- | ---------------------------------------------- |
| SX1262 NSS / IRQ / reset / BUSY | 5 /4 /3 /6                                     |
| SX1262 SCK / MOSI / MISO        | 40 /14 /39                                     |
| GNSS module TX → host RX        | GPIO15                                         |
| GNSS module RX ← host TX        | GPIO13                                         |
| PI4IOE system I2C               | SDA8/SCL9, address0x43 in official code        |
| RF switch                       | PI4IOE P0 output HIGH, high-impedance disabled |
| Cap Grove                       | GND/5V/SDA8/SCL9; differs from host Grove2/1   |

The main product table labels `GPS-RX`/`GPS-TX` from the **module** perspective. The official tutorial's UART host arguments are RX15/TX13. Keep that direction explicit when connecting or initializing HardwareSerial. SPI is shared with the Cardputer's SD card: keep inactive selects high and use transaction-specific settings.5V supplies the accessory; its GPIO signals belong to the3.3V host domain. [U214 pin map](https://docs.m5stack.com/en/cap/Cap_LoRa-1262#pinmap), [current Arduino tutorial](https://docs.m5stack.com/en/arduino/projects/cap/cap_lora868).

![M5Stack Cap LoRa-1262 radio, GNSS and expansion circuit](../../.gitbook/assets/m5stack-rank-098-diagram.png)

_M5Stack official technical illustration:_ [_original_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1208/U214-sche-Cap-LoRa1262_SCH_1.1_20251029_2025_11_07_22_53_19_page_02.png)_. Verify drawing and physical revision together._

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Select **M5Cardputer** for the Cardputer-Adv host. Install M5Cardputer/M5Unified/M5GFX, **RadioLib** for SX1262, and the manufacturer's **TinyGPSPlus** route for parsed GNSS examples. Record library releases. U214 has no separately flashable MCU application: your host sketch initializes radio, GNSS and the IO expander.

The [shared LoRa868/LoRa-1262 tutorial](https://docs.m5stack.com/en/arduino/projects/cap/cap_lora868) detects the expander to choose the cap variant. For an exact U214 project, treat absence of0x43 as a diagnostic error; do not silently fall back to LoRa868 wiring. Its RadioLib constructor is `Module(5,4,3,6)` in NSS/IRQ/reset/BUSY order. Before `radio.begin`, initialize internal I2C, make P0 an output, disable its high-impedance state and drive it high.

UiFlow2 uses the **host** Cardputer-Adv image and the [LoRa1262 cap API](https://uiflow-micropython.readthedocs.io/en/latest/cap/lora1262.html). A Meshtastic image is a different application with an exact supported host/cap target. Preserve existing settings before any host firmware replacement.

## Getting started

### Original GNSS transport checkpoint

1. Establish the host display/keyboard baseline without the cap, then power off and install U214/antenna.
2. Select M5Cardputer, install its dependencies and upload this original passive GNSS logger.
3. Open the115200-baud monitor and place the antenna outdoors with a clear sky view. Do not transmit LoRa during this first UART test.
4. Confirm complete NMEA lines, then use a parsed GNSS example to distinguish valid position/time from received-but-invalid data.

```cpp
#include <M5Cardputer.h>
#include <HardwareSerial.h>
HardwareSerial gnss(1);
uint32_t bytesSeen=0, lastReport=0;
void setup() {
  auto cfg=M5.config();
  M5Cardputer.begin(cfg, true);
  Serial.begin(115200);
  gnss.begin(115200, SERIAL_8N1, 15, 13);
  Serial.println("U214_NMEA: host RX15,TX13");
}
void loop() {
  M5Cardputer.update();
  while (gnss.available()) {
    Serial.write(gnss.read());
    ++bytesSeen;
  }
  if (millis()-lastReport>=5000) {
    lastReport=millis();
    Serial.printf("\nGNSS_BYTES=%lu\n", (unsigned long)bytesSeen);
  }
  delay(2);
}
```

Expected result is increasing byte count and readable `$...` NMEA sentences. A valid checksum, valid fix flag and fresh timestamp must be checked by the parser before using coordinates; a byte count alone proves only reception. If text is corrupted, verify1152008N1 and host RX15/TX13 before changing GNSS configuration. The source's default baud is not a claim that every previously reconfigured module retains that rate.

### SX1262 initialization and a controlled two-node test

Use the official tutorial's RadioLib receiver first. Initialize internal I2C8/9 and IO expander0x43; configure P0 output, high-impedance false and HIGH. Construct SX1262 on5/4/3/6 and verify `radio.begin` returns `RADIOLIB_ERR_NONE`. If it fails, print the actual code and stop; do not launch an unconditional transmit loop.

Configure a second compatible node using the **same** carrier, bandwidth, spreading factor, coding rate, sync word, preamble and packet settings. The source example uses125kHz bandwidth, SF12, coding parameter5, sync0x34 and20symbol preamble, but its868MHz/+22dBm defaults must be adapted to the deployment's permitted settings. Start at a conservative allowed power. Send a short numbered payload on deliberate input, then verify its bytes, RSSI and SNR on the receiver. Swap roles and repeat. A local transmit-complete interrupt is not peer delivery, and LoRa packets with these raw settings are not automatically Meshtastic packets.

For an interrupt-driven design, keep the callback to a flag, process completion in the main loop, and check the RadioLib return code before rearming receive/transmit. Run GNSS and radio separately before combining them so SPI, UART and RF failures have independent evidence. [Exact initialization and modem arguments](https://docs.m5stack.com/en/arduino/projects/cap/cap_lora868).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                      | Check / recovery                                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------ |
| SX1262 initializes but no RF | Matched antenna → region/modem match → PI4IOE P0 enabled → packet CRC/sync settings → peer payload check.    |
| No expander at0x43           | Power off/reseat cap, verify U214 identity and internal8/9 bus; do not silently treat it as old LoRa868.     |
| GNSS silent                  | RX15/TX13,1152008N1, accessory power and byte counter before sky-view diagnosis.                             |
| NMEA but no fix              | Move outdoors, allow acquisition, inspect valid flags/satellites/freshness; do not accept stale coordinates. |
| SD breaks radio              | Shared40/14/39 signals; inactive CS high, transaction mode/clock and independent device test.                |
| Firmware restore             | Restore the exact Cardputer-Adv host image; the cap itself has no separate application image.                |

## Downloads and technical documents

The links below include both the carrier-cap schematic and the smaller Stamp LoRa-1262 radio schematic. Use both when tracing power/reset/RF switch behavior; the product names are related but not interchangeable. The CAD drawing establishes mounting geometry, not allowable screw force.

| Official file or repository                                                                                                                                                                              | Use                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [Cap LoRa-1262 Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1208/U214-sche-Cap-LoRa1262_SCH_V1.1_20251029_2025_11_07_22_53_19.pdf)                                                   | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Stamp LoRa-1262 Mini Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1208/NEW-1262-SCH_A1-Lora_2025_08_27_10_58_52.pdf)                                                                | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Cap LoRa-1262 Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1208/U214-00-cap1262-model-size.pdf)                                                                                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Cap LoRa-1262 Structure Files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U214_Cap_LoRa-1262/Structures)                                                                               | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [SX1262](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1177/DS_SX1261_2_V2-2.pdf)                                                                                                                     | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [ATGM336H-6N](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-GPS%20v1.1/ATGM336H-6N.pdf)                                                                                  | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [CASIC Multi-Mode Satellite Navigation Receiver Protocol Specification](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1173/CASIC_Multi-mode_Satellite_Navigation_Receiver_Protocol_Specification.pdf) | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Cap LoRa-1262 Arduino LoRa Driver Library](https://github.com/jgromes/RadioLib)                                                                                                                         | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Cap LoRa-1262 Arduino GPS Driver Library](https://github.com/m5stack/TinyGPSPlus)                                                                                                                       | Manufacturer-listed exact model document / maintained source; use the scope described above. |
| [Cap LoRa-1262 UiFlow2 Docs](https://uiflow-micropython.readthedocs.io/en/latest/cap/lora1262.html)                                                                                                      | Manufacturer-listed exact model document / maintained source; use the scope described above. |

### Additional model references <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

* [Existing complete-kit guide](https://wiki.openelab.io/aiot/m5stack/m5stack-cardputer-mesh-kit-for-meshtastic-engineering-guide)
* [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U214_Cap_LoRa-1262/Structures/Cap_LoRa-1262.stl)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

This guide uses the exact sold SKU and the [manufacturer reference](https://docs.m5stack.com/en/cap/Cap_LoRa-1262). Specifications are manufacturer-reported; diagnostic order and first-result programs are original engineering work. The U214 schematic and official host/module-direction naming were compared with the Arduino UART setup. GNSS accuracy, radio sensitivity and acquisition times are vendor figures; no RF range or GNSS test was performed.

**Review:** 24 November 2026. Manufacturer documentation and the linked SDK interfaces were reviewed. **Compilation, firmware flashing and hardware operation: not run.** Expected results above are commissioning checkpoints, not observed bench measurements.
