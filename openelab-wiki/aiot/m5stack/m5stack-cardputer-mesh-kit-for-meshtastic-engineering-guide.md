# M5Stack Cardputer Mesh Kit for Meshtastic Engineering Guide

{% hint style="info" %}
[**View M5Stack Cardputer Mesh Kit K152 on OpenELAB**](https://openelab.io/products/m5stack-cardputer-mesh-kit)

**Covered model:** M5Stack Cardputer Mesh Kit K152 · **OpenELAB SKU:** `M5-K152`
{% endhint %}

**Product link:** [M5Stack Cardputer Mesh Kit for Meshtastic on OpenELAB](https://openelab.io/products/m5stack-cardputer-mesh-kit)

## M5Stack Cardputer Mesh Kit for Meshtastic Engineering Guide

The M5Stack Cardputer Mesh Kit is a portable Meshtastic-ready LoRa mesh communication terminal built from the Cardputer-Adv controller and Cap LoRa-1262 expansion module. It combines an ESP32-S3FN8 computer with keyboard, 1.14 inch display, 1750 mAh battery, audio, IMU, microSD, SX1262 LoRa radio, external RP-SMA antenna, and multi-constellation GNSS positioning. This guide summarizes the engineering details needed to deploy the kit as an off-grid messaging node, field tracker, portable LoRa test terminal, or ESP32-S3 development platform.

### Quick Summary

* **Product:** M5Stack Cardputer Mesh Kit for Meshtastic, OpenELAB SKU M5-K152.
* **Core controller:** Cardputer-Adv with Stamp-S3A / ESP32-S3FN8, 8 MB flash, keyboard, display, battery, audio, IMU, IR, microSD, Grove, and EXT bus.
* **Radio/GNSS cap:** Cap LoRa-1262 with Semtech SX1262 LoRa radio and ATGM336H-6N / AT6668 GNSS.
* **LoRa band:** 868 to 923 MHz hardware range; configure the legal Meshtastic region for your country before transmitting.
* **Positioning:** GPS, QZSS, BeiDou BDS, Galileo, and GLONASS support, with NMEA GNSS output over UART.
* **Best fit:** off-grid messaging, outdoor mesh networking, field teams, GPS tracking, smart-city pilots, industrial inspection, and LoRa/Meshtastic development.

### What Is the Cardputer Mesh Kit?

The Cardputer Mesh Kit packages a handheld ESP32-S3 computer and an SX1262 LoRa/GNSS expansion cap into a ready-to-use Meshtastic device. Unlike a bare LoRa module, it includes the user interface needed for field work: physical keyboard, color display, battery, speaker, microphone, audio jack, microSD, and magnetic/LEGO-compatible mounting features.

The kit is pre-installed with Meshtastic firmware according to M5Stack, so basic mesh communication can begin without building firmware from source. Engineers can still reflash, customize, or develop new firmware using M5Burner, Meshtastic tools, Arduino, UiFlow2, ESP-IDF, PlatformIO, RadioLib, TinyGPSPlus, and the official M5Cardputer library.

### Key Specifications

| Parameter             | Specification                                                                            | Engineering note                                                                                               |
| --------------------- | ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| SoC                   | ESP32-S3FN8, dual-core Xtensa LX7 up to 240 MHz                                          | Enough compute for UI, LoRa control, GNSS parsing, BLE/Wi-Fi configuration, and custom apps.                   |
| Flash                 | 8 MB                                                                                     | Use firmware/partition settings appropriate for ESP32-S3FN8.                                                   |
| Storage               | microSD                                                                                  | Useful for logs, maps, message history, configuration files, and field diagnostics.                            |
| Display               | ST7789V2, 1.14 inch, 240 x 135 px                                                        | Compact display for Meshtastic status, channel info, GPS status, and menus.                                    |
| Keyboard              | 56 keys, 4 x 14 matrix, 160 gf actuation force                                           | Enables standalone field input without a phone for many workflows.                                             |
| Battery               | 1750 mAh lithium battery                                                                 | Runtime depends on LoRa duty cycle, display brightness, GNSS, audio, and sleep behavior.                       |
| Audio                 | ES8311 codec, NS4150B amplifier, 8 ohm 1 W speaker, MEMS microphone, 3.5 mm audio output | Supports notification sounds, voice/audio experiments, and local alerts.                                       |
| IMU                   | BMI270 6-axis IMU                                                                        | Can support motion-aware power states, gestures, orientation, or field-device state detection.                 |
| Expansion             | HY2.0-4P Grove plus EXT 2.54-14P                                                         | Use for sensors, custom hardware, and Cap LoRa-1262 connectivity.                                              |
| LoRa radio            | SX1262                                                                                   | Modern low-power LoRa transceiver with SPI control.                                                            |
| LoRa frequency range  | 868 to 923 MHz                                                                           | Hardware range is not the same as legal permission; set the Meshtastic region correctly.                       |
| LoRa TX power         | +22 dBm                                                                                  | Observe local EIRP, duty-cycle, antenna, and amateur/ISM-band rules.                                           |
| LoRa sensitivity      | -147 dBm in low data-rate mode                                                           | Real range depends on region settings, spreading factor, antenna placement, terrain, and interference.         |
| LoRa bit rate         | Up to 300 kbps                                                                           | Meshtastic long-range presets usually trade speed for range and reliability.                                   |
| LoRa antenna          | 108 x 9.3 mm, RP-SMA female connector, 3 dBi                                             | Always install a suitable antenna before powering the radio.                                                   |
| GNSS module           | ATGM336H-6N / AT6668                                                                     | UART interface, default 115200 bps, NMEA-style GNSS output.                                                    |
| GNSS systems          | GPS, QZSS, BD2, BD3, Galileo, GLONASS                                                    | Good for position-aware Meshtastic nodes and mobile tracker experiments.                                       |
| GNSS accuracy         | <1.5 m CEP50 listed by M5Stack                                                           | Validate in the target environment; buildings, trees, enclosure orientation, and antenna view affect accuracy. |
| GNSS update rate      | Up to 10 Hz                                                                              | Meshtastic position update interval is usually configured for power and network load, not maximum GNSS rate.   |
| Operating temperature | 0 to 40 C                                                                                | Protect from hot vehicles, direct sun heating, freezing conditions, and water ingress.                         |
| Size                  | Cardputer-Adv 84.0 x 54.0 x 19.6 mm; Cap LoRa-1262 84.0 x 24.0 x 15.2 mm                 | Use official model-size PDFs for enclosure, holder, or vehicle mount design.                                   |

### System Architecture

* **Cardputer-Adv controller:** handles UI, keyboard, Meshtastic firmware, BLE/Wi-Fi configuration workflows, local storage, audio, display, IMU, and expansion.
* **Cap LoRa-1262 radio module:** provides the SX1262 LoRa radio, antenna connector, GNSS receiver, RF shield, and Grove expansion.
* **Meshtastic software layer:** creates a long-range, low-bandwidth mesh network for text, telemetry, node position, and device status.
* **Phone/computer tools:** Meshtastic mobile apps, Meshtastic Web Client, M5Burner, serial tools, and firmware flashers are used for configuration and recovery.
* **External sensors:** the Grove and EXT interfaces can support environmental sensors, buttons, or application-specific peripherals for telemetry nodes.

### Important Safety and Regulatory Notes

* **Install the antenna before powering or transmitting.** M5Stack's Meshtastic tutorial warns that powering the device without the antenna installed may permanently damage the hardware.
* **Use the correct Meshtastic region.** The hardware covers 868 to 923 MHz, but legal ISM bands vary by region, for example EU868 and US915. Incorrect settings can violate local radio rules.
* **Mind duty cycle and channel utilization.** Long-range LoRa settings are low bandwidth. Avoid high-frequency telemetry that congests the mesh.
* **Use matched antennas.** The supplied antenna is intended for the kit; if replacing it, use the correct connector, frequency band, gain, and mechanical strain relief.
* **Validate field range realistically.** Terrain, antenna height, body blocking, buildings, vehicle interiors, weather, and RF noise can dominate range performance.

### Pin Map and Interfaces

| Interface                  | Signals                                                                                                                               | Notes                                                                                            |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Cardputer-Adv EXT 2.54-14P | G3 RESET, 5VIN, G4 INT, GND, G6 BUSY, 5VOUT, G40 SCK, G8 I2C\_SDA, G14 MOSI, G9 I2C\_SCL, G39 MISO, G13 UART\_RX, G5 CS, G15 UART\_TX | Main expansion bus used by Cap LoRa-1262; check orientation before mating boards.                |
| LoRa SPI mapping           | RST G3, IRQ G4, BUSY G6, SCK G40, MOSI G14, MISO G39, NSS G5                                                                          | Use these pins when writing custom RadioLib or ESP-IDF firmware.                                 |
| GNSS UART mapping          | GPS-RX G13, GPS-TX G15                                                                                                                | Default GNSS serial setting is 115200 bps, 8N1.                                                  |
| Cap LoRa-1262 I2C          | SDA G8, SCL G9                                                                                                                        | Used for the PI4IOE5V6408 I/O expander and Cap Grove I2C path.                                   |
| RF antenna switch          | PI4IOE5V6408 P0 controls SX\_ANT\_SW                                                                                                  | M5Stack notes that LoRa initialization requires setting P0 HIGH to enable the RF antenna switch. |
| Cardputer-Adv Grove        | GND, 5 V, G2, G1                                                                                                                      | HY2.0-4P custom port for external modules.                                                       |
| Cap LoRa-1262 Grove        | GND, 5 V, SDA, SCL                                                                                                                    | HY2.0-4P Port A for I2C sensors on the cap.                                                      |
| LCD                        | DISP\_BL G38, RST G33, RS G34, DAT G35, SCK G36, CS G37                                                                               | Use M5Cardputer library for display bring-up.                                                    |
| Audio                      | ES8311 SDA G8, SCL G9, SCLK G41, ASDOUT G46, LRCK G43, DSDIN G42                                                                      | Shared I2C bus for codec control.                                                                |
| Keyboard                   | TCA8418RTWR SDA G8, SCL G9, INT G11                                                                                                   | Matrix keyboard controller; use the official library where possible.                             |
| microSD                    | CS G12, MOSI G14, CLK G40, MISO G39                                                                                                   | Shared SPI pins; coordinate chip-select use in custom firmware.                                  |

### Meshtastic Bring-Up Workflow

1. **Assemble mechanically.** Seat the Cap LoRa-1262 into the Cardputer-Adv EXT 2.54-14P connector and secure it with the supplied screws.
2. **Attach the antenna.** Screw the included RP-SMA LoRa antenna onto the cap before powering the unit.
3. **Charge and power on.** M5Stack notes that the power switch should be ON before charging.
4. **Confirm firmware.** The kit is listed as Meshtastic pre-installed; if needed, use the M5Stack Meshtastic tutorial, M5Burner, or Meshtastic firmware tools to reflash.
5. **Select radio region.** In Meshtastic, configure the correct region/channel settings before transmitting.
6. **Pair with phone or computer.** Use the Meshtastic Android/iOS app or web/client tooling to configure node name, channel, GPS, telemetry, and power options.
7. **Test near-field first.** Verify two nodes communicate at short range before doing distance tests.
8. **Field test with logs.** Record GPS lock status, RSSI/SNR, battery behavior, antenna position, terrain, and node placement.

### Development Workflow

* **For Meshtastic users:** start with M5Stack's Cardputer Mesh Kit Meshtastic tutorial and Meshtastic's official documentation.
* **For Arduino firmware:** use the M5Cardputer library for display, keyboard, and board support; use RadioLib for SX1262 LoRa experiments; use TinyGPSPlus for GNSS parsing.
* **For UiFlow2:** use the Cardputer-Adv UiFlow2 quick start and Cap LoRa-1262 UiFlow2 docs for visual prototyping.
* **For PlatformIO:** start from M5Stack's ESP32-S3 Arduino environment and lock library versions for reproducible builds.
* **For ESP-IDF:** refer to the ESP32-S3 datasheet, schematics, and pin map before implementing lower-level SPI, UART, I2C, display, and power behavior.

### Useful PlatformIO Configuration

M5Stack's documentation provides this Arduino-based PlatformIO starting point:

```ini
[env:m5stack-cardputer-mesh-kit]
platform = espressif32@6.12.0
board = esp32-s3-devkitc-1
framework = arduino
upload_speed = 1500000
build_flags =
    -DESP32S3
    -DCORE_DEBUG_LEVEL=5
    -DARDUINO_USB_CDC_ON_BOOT=1
    -DARDUINO_USB_MODE=1
lib_deps =
    M5Cardputer=https://github.com/m5stack/M5Cardputer
    RadioLib=https://github.com/jgromes/RadioLib
    TinyGPSPlus=https://github.com/m5stack/TinyGPSPlus
```

### Official Resources and Downloads

| Resource                        | Use                                                                                     | Link                                                                                                                                                   |
| ------------------------------- | --------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| OpenELAB product page           | Purchase and listing details                                                            | [M5Stack Cardputer Mesh Kit on OpenELAB](https://openelab.io/products/m5stack-cardputer-mesh-kit)                                                      |
| M5Stack Cardputer Mesh Kit docs | Official product specifications, pin map, software, datasheets, schematics, model files | [M5Stack Cardputer Mesh Kit documentation](https://docs.m5stack.com/en/core/Cardputer_Mesh_Kit)                                                        |
| M5Stack SKU page                | Official K152 product page                                                              | [Cardputer Mesh Kit SKU K152](https://docs.m5stack.com/en/products/sku/K152)                                                                           |
| Meshtastic tutorial             | M5Stack setup guide for using Meshtastic with the kit                                   | [Using Meshtastic with Cardputer Mesh Kit](https://docs.m5stack.com/en/guide/lora/meshtastic/cardputer_mesh_kit)                                       |
| Meshtastic official site        | Meshtastic ecosystem, apps, settings, radio regions, concepts                           | [Meshtastic.org](https://meshtastic.org/)                                                                                                              |
| Meshtastic Web Flasher          | Browser-based firmware flashing workflow for supported Meshtastic targets               | [Meshtastic Web Flasher](https://flasher.meshtastic.org/)                                                                                              |
| Meshtastic firmware             | Open-source firmware reference                                                          | [meshtastic/firmware](https://github.com/meshtastic/firmware)                                                                                          |
| Cardputer-Adv schematic         | Electrical design reference for Cardputer-Adv                                           | [Cardputer-Adv Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/Sch_M5CardputerAdv_v1.0_2025_06_20_17_19_58.pdf)                  |
| Stamp-S3A schematic             | ESP32-S3 module reference                                                               | [Stamp-S3A Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1150/Sch_StampS3_v0.3.3.pdf)                                               |
| Cap LoRa-1262 schematic         | LoRa/GNSS cap electrical design                                                         | [Cap LoRa-1262 Schematics PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1208/U214-sche-Cap-LoRa1262_SCH_V1.1_20251029_2025_11_07_22_53_19.pdf) |
| Cardputer-Adv model size        | Mechanical integration                                                                  | [Cardputer-Adv Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/K132-Adv-cardputer-ADV.pdf)                                       |
| Cap LoRa-1262 model size        | Mechanical integration                                                                  | [Cap LoRa-1262 Model Size PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1208/U214-00-cap1262-model-size.pdf)                                   |
| Cardputer-Adv structure files   | Hardware structure/CAD resources                                                        | [Cardputer-Adv structure files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K132-Adv_Cardputer-Adv/Structures)                         |
| ESP32-S3 datasheet              | SoC hardware reference                                                                  | [ESP32-S3 datasheet](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/472/esp32-s3_datasheet_en.pdf)                                                   |
| SX1262 datasheet                | LoRa radio reference                                                                    | [SX1261/2 datasheet](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1177/DS_SX1261_2_V2-2.pdf)                                                       |
| ATGM336H-6N datasheet           | GNSS module reference                                                                   | [ATGM336H-6N PDF](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-GPS%20v1.1/ATGM336H-6N.pdf)                            |
| CASIC GNSS protocol             | GNSS protocol details                                                                   | [CASIC GNSS receiver protocol](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/950/Multimode_satellite_navigation_receiver_cn.pdf)                    |
| M5Cardputer library             | Arduino library for Cardputer hardware                                                  | [m5stack/M5Cardputer](https://github.com/m5stack/M5Cardputer)                                                                                          |
| RadioLib                        | SX1262 LoRa development library                                                         | [jgromes/RadioLib](https://github.com/jgromes/RadioLib)                                                                                                |
| TinyGPSPlus                     | GNSS/NMEA parsing library                                                               | [m5stack/TinyGPSPlus](https://github.com/m5stack/TinyGPSPlus)                                                                                          |
| Factory firmware EasyLoader     | M5Stack factory firmware recovery                                                       | [K152 factory firmware EasyLoader](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1240/K152-factory-firmware.exe)                                    |

### Field Deployment Checklist

1. Confirm the antenna is installed before power-on.
2. Confirm firmware version, Meshtastic region, channel, role, node name, and encryption/channel settings.
3. Verify GNSS lock outdoors with a clear sky view before relying on position reports.
4. Test short-range node-to-node communication before long-distance trials.
5. Record RSSI, SNR, hop count, packet success, location, antenna orientation, and terrain during range tests.
6. Measure battery runtime with the intended display brightness, GPS setting, and transmit interval.
7. For fixed nodes, protect from water, direct sun heating, theft, vibration, and antenna strain.
8. Document all configuration values so replacement units can be provisioned consistently.

### Engineering Best Practices

* **Keep transmissions sparse.** Meshtastic is low-bandwidth mesh networking; high-rate telemetry reduces network health.
* **Prefer good antenna placement over higher power.** Height, line of sight, and body/vehicle shielding often matter more than TX power.
* **Use GPS conservatively for battery life.** A mobile tracker may need frequent position updates; a static relay usually does not.
* **Check SPI sharing.** The LoRa radio and microSD use overlapping SPI-related pins, so custom firmware must manage chip-select and bus use carefully.
* **Lock firmware versions for deployments.** Record Meshtastic, M5Stack, and library versions before distributing multiple nodes.
* **Use legal bands and presets.** Select the region and modem preset that match local radio rules and the intended range/latency tradeoff.

### Project References and Application Ideas

* [M5Stack Meshtastic tutorial for Cardputer Mesh Kit](https://docs.m5stack.com/en/guide/lora/meshtastic/cardputer_mesh_kit): official setup path for deploying the kit as a Meshtastic handheld.
* [Meshtastic firmware](https://github.com/meshtastic/firmware): open-source firmware used by the Meshtastic ecosystem; useful for understanding supported features, releases, and configuration behavior.
* [d4rkmen/plai](https://github.com/d4rkmen/plai): community standalone Meshtastic node project for Cardputer ADV, useful as a reference for Cardputer-style field UI ideas.
* [reydeargentina/cardtastic](https://github.com/reydeargentina/cardtastic): community UI project for Meshtastic nodes on M5Stack Cardputer hardware.
* [RadioLib SX1262 examples](https://github.com/jgromes/RadioLib): useful for engineers building custom point-to-point LoRa or diagnostic firmware outside Meshtastic.
* [M5Cardputer library examples](https://github.com/m5stack/M5Cardputer): starting point for custom keyboard/display applications on Cardputer hardware.

### FAQ

<details>

<summary>What is the M5Stack Cardputer Mesh Kit used for?</summary>

It is used for portable Meshtastic messaging, off-grid LoRa mesh networking, GPS tracking, field-team communication, sensor telemetry, industrial inspection, and ESP32-S3 LoRa/GNSS prototyping.

</details>

<details>

<summary>Does the Cardputer Mesh Kit come with Meshtastic installed?</summary>

M5Stack lists the kit as pre-installed with Meshtastic firmware, so it is intended to be ready for basic LoRa mesh use out of the box. Engineers should still confirm firmware version and region settings before deployment.

</details>

<details>

<summary>What LoRa chip does the Cardputer Mesh Kit use?</summary>

The Cap LoRa-1262 module uses the Semtech SX1262 LoRa radio and supports the 868 to 923 MHz hardware range.

</details>

<details>

<summary>Can I use the kit in the United States or Europe?</summary>

The hardware covers bands used by common Meshtastic regions such as US915 and EU868, but users must configure the correct legal region and comply with local rules for frequency, power, antenna gain, and duty cycle.

</details>

<details>

<summary>Why must the antenna be attached before powering the device?</summary>

Operating a LoRa transmitter without a suitable antenna can reflect RF power back into the radio front end and damage the hardware. M5Stack specifically warns not to power the device without the antenna installed.

</details>

<details>

<summary>Does the kit include GPS?</summary>

Yes. The Cap LoRa-1262 includes an ATGM336H-6N / AT6668 GNSS module with support for GPS, QZSS, BeiDou, Galileo, and GLONASS.

</details>

<details>

<summary>Can the Cardputer Mesh Kit be programmed with Arduino?</summary>

Yes. M5Stack provides Arduino quick starts, and the relevant libraries include M5Cardputer, RadioLib, and TinyGPSPlus.

</details>

<details>

<summary>Can I use UiFlow2?</summary>

Yes. M5Stack provides UiFlow2 documentation for Cardputer-Adv and Cap LoRa-1262, which is useful for visual prototyping and simple experiments.

</details>

<details>

<summary>What is the difference between Meshtastic and custom LoRa firmware?</summary>

Meshtastic is a complete open-source mesh communication firmware and app ecosystem. Custom LoRa firmware using RadioLib or ESP-IDF gives more control, but you must implement protocol, routing, UI, configuration, and interoperability yourself.

</details>

<details>

<summary>What should I test before field deployment?</summary>

Test antenna installation, region setting, GPS lock, node-to-node messaging, battery runtime, enclosure protection, range under realistic terrain, and recovery/flashing procedure.

</details>

### Source Notes

* Product details: [OpenELAB M5Stack Cardputer Mesh Kit product page](https://openelab.io/products/m5stack-cardputer-mesh-kit).
* Official specifications, pin maps, schematics, model-size files, and software links: [M5Stack Cardputer Mesh Kit documentation](https://docs.m5stack.com/en/core/Cardputer_Mesh_Kit).
* Meshtastic setup reference: [M5Stack Meshtastic tutorial](https://docs.m5stack.com/en/guide/lora/meshtastic/cardputer_mesh_kit) and [Meshtastic official site](https://meshtastic.org/).
* Community project references are examples for engineering inspiration; review each repository's license, hardware assumptions, firmware maturity, and safety implications before reuse.
* Reviewed for OpenELAB wiki publication on 2026-05-25.

## Official documentation and development resources

Use [Cardputer Mesh Kit](https://docs.m5stack.com/en/core/Cardputer_Mesh_Kit) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K152`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                             |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5cardputer/program)                                                         |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1178/Sch_M5CardputerAdv_v1.0_2025_06_20_17_19_58.pdf)                   |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1150/Sch_StampS3_v0.3.3.pdf)                                            |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K152_Cardputer_Mesh_Kit/Structures)                        |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K152_Cardputer_Mesh_Kit/Structures/Cardputer_Mesh_Kit.stl) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/cap/cap_lora868)                                                    |
| Official source: M5Cardputer | [Read official source: m5cardputer](https://github.com/m5stack/M5Cardputer)                                                                          |
| Official source: TinyGPSPlus | [Read official source: tinygpsplus](https://github.com/m5stack/TinyGPSPlus)                                                                          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
