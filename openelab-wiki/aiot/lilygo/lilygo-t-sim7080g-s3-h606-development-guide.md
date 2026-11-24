---
description: >-
  Bring up the H606 T-SIM7080G-S3 PMU board, inspect Cat-M/NB-IoT registration,
  separate GNSS from cellular operation and diagnose power sequencing.
---

# LILYGO T-SIM7080G S3 H606 Engineering Guide

{% hint style="info" %}
[**View LILYGO T-SIM7080G S3 ESP32-S3 Dev board With TF Card GPS LTE Antenna on OpenELAB**](https://openelab.io/products/lilygo-t-sim7080g-s3)

**Model / option:** Default Title · **SKU:** `LILYGO-H606`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

T-SIM7080G-S3 **H606** is the ESP32-S3/AXP2101 development board with a SIM7080G cellular modem, GNSS, camera interface, microSD and single-cell/solar charging. It is a **Cat-M/NB-IoT** platform, not a LoRa node or a general LTE Cat-4 modem. Confirm operator coverage, SIM provisioning and APN before a connectivity project.

This page covers the original **PMU H606** hardware and its LilyGo-T-SIM7080G repository. Do not substitute the newer T-SIM7080G Standard/H795 pin map. The first result below is a modem identity and SIM/registration record using read-only AT queries. [Manufacturer H606 source](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/README.MD).

## Applications

Use H606 for operator-provisioned telemetry, sequential position-and-upload jobs, camera experiments and battery/solar energy measurements. Cellular registration, IP bearer activation, TLS and MQTT delivery are separate acceptance stages.

The manufacturer states that cellular networking and GNSS cannot operate simultaneously on this modem path. Design a state machine that obtains a fix, stops GNSS, registers/connects and uploads, then sleeps. Do not promise continuous cellular streaming while acquiring GNSS.

## Specifications

| Item             | H606 scope                                                                   |
| ---------------- | ---------------------------------------------------------------------------- |
| Host             | ESP32-S3; 16 MB flash and 8 MB octal PSRAM hardware class                    |
| Modem            | SIM7080G Cat-M / NB-IoT; operator-supported bands/service required           |
| Power management | AXP2101; independent camera, card, modem and level-shifter rails             |
| USB-C            | ESP32-S3 upload and serial console                                           |
| Micro-USB        | Modem USB/firmware maintenance, not the normal sketch upload port            |
| Battery          | Manufacturer range 3.5–4.2 V; flat-top 18650 recommended                     |
| Solar            | 4.4–6 V input; 500 mA charge path; battery required for operation from solar |
| Card             | SDMMC CMD39 / CLK38 / DATA40                                                 |
| Modem serial     | Host RX4 / TX5, 115200 baud in reviewed ATDebug                              |

The battery table permits up to 1 A programmed charging, while solar charging is 500 mA. These are different paths; neither is permission to exceed the actual cell's charge specification. The README's capacity recommendation “2500mA” is dimensionally a capacity statement and must not be treated as a current rating. Use a documented suitable cell and verify polarity. [Power/voltage tables](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/README.MD).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Power domains and signal boundaries

Begin on regulated 5 V USB-C with solar disconnected and the supplied antenna arrangement fitted. Insert the provisioned SIM **before modem startup**, with all power removed; inserting it after startup is not reliably detected. Do not feed 5 V into signal pins. **VSYS follows the active input source**, so it is not a regulated 3.3 V peripheral output.

| Role                         | ESP32-S3 pin / PMU rail                                  |
| ---------------------------- | -------------------------------------------------------- |
| Modem UART host RX / TX      | GPIO4 / GPIO5                                            |
| Modem PWR control / RI / DTR | GPIO41 / GPIO3 / GPIO42                                  |
| PMU I²C SDA / SCL / IRQ      | GPIO15 / GPIO7 / GPIO6                                   |
| Host core                    | DC1, 3.3 V; do not change or disable                     |
| Modem main supply            | DC3; ATDebug explicitly sets 3000 mV                     |
| UART level conversion        | BLDO1, 3300 mV; keep enabled for communication           |
| GNSS antenna supply          | BLDO2, 3300 mV in the example                            |
| Camera                       | ALDO1 / ALDO2 / ALDO4; preserve module-specific voltages |
| Card                         | ALDO3                                                    |

The modem's native UART supply is not the host's logic voltage: the schematic includes level conversion. Keep the exact board driver between them. GPIO41 controls the board's PWRKEY transistor; its physical waveform is not a direct instruction to drive the modem pin with USB voltage. [ATDebug power sequence](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/examples/ATDebug/ATDebug.ino), [V1.0 schematic, PMU/modem sheets](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/schematic/T-SIM7080G_Schematic.pdf).

### Camera and expansion reservations

| Camera function          | GPIO              |
| ------------------------ | ----------------- |
| Reset / XCLK / SDA / SCL | 18 / 8 / 2 / 1    |
| VSYNC / HREF / PCLK      | 16 / 17 / 12      |
| D9 / D8 / D7 / D6        | 9 / 10 / 11 / 13  |
| D5 / D4 / D3 / D2        | 21 / 48 / 47 / 14 |

With the camera installed these are occupied nets. GPIO35–37 are unavailable because of octal PSRAM; do not follow the broad “all I/O available without camera” wording literally. The schematic marks GPIO33–37 as octal reservations. Header contact orientation must be read from the actual schematic/PCB, not inferred from a row of GPIO numbers.

The assembled board lacks an NTC in the reviewed design, and its charging examples disable PMU TS measurement. That board-specific configuration does not validate a substituted battery's temperature behavior. External 5 V pad soldering, PMU voltage modifications and replacement-cell commissioning are excluded from this USB first test.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The reviewed commit is **`39f7886a9436c8a460eb50c86e2d6c8e21de9b1e`**. PlatformIO uses environment **`lilygo-t-sim7080x-s3`**, `espressif32@6.12.0`, Arduino and `esp32s3box`; its configuration selects `examples/ATDebug`. Retain bundled libraries and the chosen partition configuration. The README's Arduino GUI option is ESP32S3 Dev Module with 16 MB QIO flash, OPI PSRAM and Hardware CDC/JTAG; it is a separate configuration path, not a reason to mix settings into the pinned PlatformIO build.

USB CDC is enabled in the bench configuration. Some examples wait at `while (!Serial)` and can appear frozen without a host terminal. An unattended battery application must explicitly handle that condition and be retested; it is not fixed by changing modem bands.

The repository inventories camera, PMU, card, GNSS, PSM, modem sleep, MQTT/MQTTS, HTTP/HTTPS and firmware-upgrade examples. Headers reviewed here carry MIT notices; dependencies retain their own licenses. Choose one source directory at a time. SIMCom's AT manual is a **family manual**; command availability still depends on the installed modem firmware.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original read-only modem acceptance record

Prepare H606, its correct cellular/GNSS antennas, a known USB data cable and an activated Cat-M/NB-IoT SIM. Keep operator identifiers and SIM details private.

1. Remove USB, battery and solar power before inserting the SIM. Restore USB-C power; keep the battery switch in the documented operating position if the battery is used. Record PCB/model markings and factory firmware first.
2. Clone the pinned repository, retain `src_dir = examples/ATDebug` as the only active example and build the exact environment. Do not replace the PMU initialization with a generic serial bridge.

```sh
git clone https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G.git
cd LilyGo-T-SIM7080G
git checkout 39f7886a9436c8a460eb50c86e2d6c8e21de9b1e
pio run -e lilygo-t-sim7080x-s3
pio run -e lilygo-t-sim7080x-s3 -t upload
pio device monitor -b 115200
```

3. At 115200 baud, wait for the sketch's AT-ready prompt. Configure the terminal to send CR/LF as needed; close other clients using that port. Send these queries one at a time and save each complete response:

```
AT
ATI
AT+CGMR
AT+CPIN?
AT+CEREG?
AT+CSQ
```

4. Require `OK` from `AT`, readable model/revision identity and `+CPIN: READY` before network diagnosis. A SIM PIN request is not a radio fault; do not guess PINs repeatedly. Interpret the second `+CEREG` field as registration state: 1 is home registration, 5 roaming, 2 searching and 3 denied. A signal reading alone is not registration or an active bearer.
5. Keep the operator-approved RAT/APN unchanged for this record. If registration fails, verify coverage, SIM service, antenna and the operator's Cat-M/NB-IoT support before changing persistent modem configuration.

**Expected result:** a reproducible modem version/SIM/registration transcript. Successful registration is conditional on the service; an `OK` bridge response is the local first result, not proof of Internet connectivity. [ATDebug source](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/examples/ATDebug/ATDebug.ino), [SIMCom manual V1.05, CPIN p.59 and CEREG pp.192–194](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/datasheet/SIM7070_SIM7080_SIM7090%20Series_AT%20Command%20Manual_V1.05.pdf).

### Add data, GNSS and sleep in stages

For data, select `MinimalModemNBIOTExample`, enter the **actual operator APN** and inspect its NB-IoT preference before use; Cat-M service needs its corresponding supported mode. The source configures `CGDCONT` and `CNCFG`, checks registration, then activates `CNACT`. Its `gprs` API naming does not mean the board offers a 2G network. Replace demonstration endpoints with a server you control and confirm both an assigned IP and a server-side unique payload receipt.

For GNSS, use `MinimalModemGPSExample` as a separate source selection with the antenna powered. Move outdoors and wait for valid time/fix. SIMCom `CGNSINF` reports run status, fix status, UTC, latitude, longitude, altitude in **metres** and speed in **km/h**; receiver-on alone is not a position fix. Stop GNSS before returning to cellular data operation. [GNSS example](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/examples/MinimalModemGPSExample/MinimalModemGPSExample.ino), [manual pp.200–203](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/datasheet/SIM7070_SIM7080_SIM7090%20Series_AT%20Command%20Manual_V1.05.pdf).

For MQTTS, the inspected example writes a CA, checks modem time, converts the certificate and configures SSL/MQTT. Its embedded CA, broker and credentials are sample configuration, not a current trust bundle for your server. Confirm current certificate validity, hostname, time and subscription at your broker before treating a modem “connected” line as delivered telemetry.

For sleep, preserve modem shutdown and PMU sequencing, then measure at the actual battery boundary with USB disconnected. The reviewed sleep source defines `TIME_TO_SLEEP = 3*60` despite comments saying five minutes/five seconds. Its roughly 360 µA manufacturer report is configuration-specific; the older 840 µA figure is not an independently measured result here. Establish wake reason and a new AT response on every cycle before optimizing current.

### Recovery separates host and modem

For ESP32 upload, hold BOOT while connecting USB-C, or hold BOOT, press/release RST, then release BOOT and select the re-enumerated port. If custom code disabled a host rail, the README describes BOOT with PWRKEY to recover while USB is connected. Restore the exact host power example first.

Modem firmware maintenance instead uses its dedicated Micro-USB plus the host enabling sketch and a matching SIM7080G package. The manufacturer's upgrade document links Windows drivers/tools and firmware via Drive. Those binaries were not executed or independently qualified here; modem reflashing is excluded from first-line registration recovery. Query `AT+CGMR` and retain the existing version before considering a vendor-directed update.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                         | Ordered checks                                                                                             |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| No USB console                  | Correct USB-C port/data cable, CDC setting, host terminal wait and observed enumerated port                |
| PMU initialization fails        | Exact H606 target, SDA15/SCL7, stable power; do not raise DC1 to compensate                                |
| No AT response                  | DC3 and BLDO1 sequence, host RX4/TX5, 115200 baud and exact PWRKEY implementation                          |
| SIM absent                      | Inserted before startup, correct physical orientation, full power cycle and SIM provisioning               |
| Searches or registration denied | Cat-M/NB-IoT coverage and SIM service, permitted bands/mode, APN/operator requirements and antenna         |
| GNSS starts but no fix          | BLDO2 antenna supply, correct GNSS connector, sky view and fresh fix field; cellular/GNSS mutual exclusion |
| Charge LED flashes              | Original board TS configuration and actual cell specification; no generic charger maximum substitution     |
| Works on USB but not battery    | Mechanical switch, cell voltage/polarity, `while (!Serial)` waits and complete power sequencing            |

Can a normal phone SIM guarantee service? No; the operator must provision the required LPWAN technology. Can the solar panel power a battery-less board? The manufacturer says this solar path charges a battery and cannot replace it.

## Downloads and technical documents

| Resource                                                                                                                                                                                                         | Purpose                                                                                |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [Pinned H606 README](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/README.MD)                                                                                | Examples, Arduino/PlatformIO, tips, pins, rails, voltage tables, LEDs and sleep report |
| [Five-sheet V1.0 schematic](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/schematic/T-SIM7080G_Schematic.pdf)                                      | Camera, host/card/headers, PMU, modem/level shifting, solar                            |
| [SIMCom AT manual V1.05](https://raw.githubusercontent.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/datasheet/SIM7070_SIM7080_SIM7090%20Series_AT%20Command%20Manual_V1.05.pdf) | Direct command definitions and firmware-dependent applicability                        |
| [Actual source examples](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/tree/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/examples)                                                                             | Camera/card/PMU, GNSS, data, TLS, MQTT and power management                            |
| [Modem update instructions](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/docs/sim7080_update_firmware.md)                                                   | Separate modem USB/driver/tool workflow; binaries not executed                         |
| [Mechanical source directory](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/tree/39f7886a9436c8a460eb50c86e2d6c8e21de9b1e/shell)                                                                           | Lists assembly/STEP files; verify exact H606 fit before manufacture                    |

The datasheet directory also indexes SIMCom HTTP(S), TCP/UDP, SSL, MQTT(S), GNSS, PSM and FOTA application notes plus certificates. These are direct optional protocol resources, not a claim that every example/cloud endpoint or modem command was tested.

### Additional existing resources

* [Exact legacy manufacturer repository](https://github.com/Xinyuan-LilyGO/LilyGo-T-SIM7080G/blob/master/README.MD)
* [Current modem-series target distinctions](https://github.com/Xinyuan-LilyGO/LilyGo-Modem-Series)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The full H606 README, build configuration, ATDebug/pins, five-sheet schematic and the applicable CPIN/CEREG/GNSS manual sections were read. Data, GNSS, TLS, sleep and modem-maintenance source paths were reviewed for their stated roles. PMU/modem drawings were visually inspected. The command-record procedure and separation of registration, bearer, fix and server receipt are original engineering guidance.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
