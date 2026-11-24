---
description: >-
  Commission the ThinkNode M6 solar mesh node, verify Meshtastic and GNSS, plan
  energy checks and recover its exact UF2 firmware.
---

# Elecrow ThinkNode M6 Development Guide

{% hint style="info" %}
[**View Elecrow ThinkNode M6 Outdoor Solar Power for Meshtastic on OpenELAB**](https://openelab.io/products/elecrow-thinknode-m6-outdoor-solar)

**Model / option:** Default Title · **SKU:** `ELECROW-LMM14106D`
{% endhint %}

## Product overview <a href="#product-and-applications" id="product-and-applications"></a>

ThinkNode M6 LMM14106D is an outdoor nRF52840/SX1262 Meshtastic node integrating a 6 W solar panel, GNSS and a 7000 mAh 18650 battery system. Commission it on the ground over USB before mounting. The first result is a received radio reply; GNSS and solar energy balance are separate checks.

The two SP11 ports identify I²C and UART roles, but their connector-contact power/polarity/current map was not established in the reviewed manual. **External sensor wiring is excluded until that received-revision diagram is obtained.** This does not prevent the assembled USB/antenna/radio procedure. [Manual](https://www.elecrow.com/download/product/LMM14106D/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_User_Manual.pdf).

## Applications

Use M6 as a surveyed fixed messaging/position node and evaluate relay placement after a direct link works. A rated solar panel and battery capacity do not establish winter autonomy. Treat antenna height, shading, routing role, traffic, GNSS interval and sensor load as recorded experiment inputs.

For deployment, retain a reachable recovery plan and a way to inspect fresh telemetry. A dark low-power indicator or a stale map icon is not a reliable power-status test.

## Specifications <a href="#hardware-specifications-and-power" id="hardware-specifications-and-power"></a>

| Parameter           | M6 scope                                                             |
| ------------------- | -------------------------------------------------------------------- |
| Host                | nRF52840, 64 MHz; 256 KB RAM, 1 MB internal flash                    |
| Radio               | SX1262; received EU868/US915 band and antenna must match deployment  |
| GNSS                | L76K; external GNSS antenna                                          |
| Battery / panel     | 7000 mAh 18650 system; 6 W rated solar output                        |
| Mainboard input     | 5 V/1 A; USB-C charge/data                                           |
| Expansion           | Two SP11 ports, I²C and UART; pin/current map not verified here      |
| Enclosure           | IP65 when properly sealed; not immersible                            |
| Operation / storage | −20 to +60 °C / −30 to +70 °C in manual; not battery charging limits |
| Dimensions / mass   | 210 × 156 × 42 mm excluding antenna/bracket; 533.1 g                 |

Sources: [manufacturer manual](https://www.elecrow.com/download/product/LMM14106D/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_User_Manual.pdf),[firmware variant](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/ELECROW-ThinkNode-M6/variant.h). The manual's Bluetooth 5.4 label does not establish optional 5.4 features on an nRF52840.

## Hardware and connections

### Connect and mount

Fit the correct LoRa and GNSS antennas. Use the factory battery/charger and regulated 5 V USB path; do not infer that two 18650 positions form a series input or substitute a pack by connector fit. Attach/remove peripherals only with power isolated, including solar. The port near the antenna is I²C; the lower one is UART. Keep both capped for this first test because contact orientation and power budget remain unverified.

The bracket document identifies 6 mm mounting apertures. Choose a sound support, orient the panel for local sunlight, avoid mast/tree shadow and check cable strain before tightening. Restore seals/caps after USB or service. IP65 does not permit immersion or pressure-washing. [Manual installation and overview pages](https://www.elecrow.com/download/product/LMM14106D/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_User_Manual.pdf).

### Internal firmware reference <a href="#firmware-update-and-development" id="firmware-update-and-development"></a>

| Role                        | nRF52840 native signal                      |
| --------------------------- | ------------------------------------------- |
| I²C SDA/SCL                 | P1.09/P0.08; not an SP11 contact-number map |
| Peripheral power            | P0.27                                       |
| SX1262 CS/DIO1/busy/reset   | P1.12/P1.06/P1.11/P1.10                     |
| SX1262 switch/TCXO          | DIO2 RF-switch; 3.3 V TCXO driver setting   |
| Battery ADC/control         | P0.28/P0.11                                 |
| Charger status              | P0.15, active LOW                           |
| Function button / power LED | P0.17/P0.12                                 |

These are occupied internal board nets. Use the [complete variant](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/ELECROW-ThinkNode-M6/variant.h) for SPI/GNSS/QSPI routing; do not turn native pins into an invented waterproof-connector drawing.

## Software and development resources

The reviewed Meshtastic environment is **`thinknode_m6`**, board `ThinkNode-M6`, at commit `d0f4096788545fb3c5e22d2a7e52ac6c268caac1`. The source marks it a release-level target but `custom_meshtastic_actively_supported=false`; that metadata is not evidence that every newer release has been bench-qualified on M6. Record the actual chosen release and retain a working image. [Environment](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/ELECROW-ThinkNode-M6/platformio.ini).

The factory Meshtastic workflow and alternate MeshCore firmware form separate networks. Confirm the exact M6 model and intended role before changing ecosystems; a generic nRF52840 or ESP32 ThinkNode image is not equivalent. Meshtastic source is GPL-3.0 with separate library notices.

## Getting started <a href="#getting-started-verify-before-outdoor-mounting" id="getting-started-verify-before-outdoor-mounting"></a>

### Bench-to-mount acceptance

Prepare the M6, supplied antennas, USB data cable, Meshtastic client and a compatible peer. Leave the sensor ports capped.

1. Charge over USB, start the installed application and pair the physical M6. The wiki's factory PIN is `123456`; use its current configured PIN if changed. Read the firmware and node identity.
2. Set the permitted region and match the peer's modem preset, frequency slot and channel name/key. Wait for restart. Keep a simple client role for the first direct test.
3. Send `M6-BENCH-01`, confirm receipt at the other radio, then return `M6-RETURN-01`. Repeat several numbered pairs and log receipts at both receivers.
4. Enable GPS in the installed settings or with the documented triple-click. Outdoors, check a current fix, time and position. A double-click requests an update; it cannot create a fix without GNSS reception.
5. Disconnect USB and repeat one reply. Place the panel in useful sunlight and inspect charging and battery telemetry. A single LED observation does not establish energy balance.
6. Mount at the planned height, seal the ports and repeat the numbered test. Record node IDs, radio settings, antenna orientation, GNSS interval, USB state and battery voltage. Compare day/night trends before unattended deployment.

**Expected result:** reply reception before and after mounting, independent fresh GNSS data and repeatable charging observations. A declining overnight battery trace is an energy/workload question, not automatically a radio fault. [Manufacturer procedure](https://www.elecrow.com/wiki/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_Powered_By_nRF52840_Supports_GPS.html).

### Controls and recovery depend on firmware <a href="#controls-and-external-interfaces" id="controls-and-external-interfaces"></a>

The wiki describes a 3-second power-on and 10-second power LED, while the current manual describes a 1-second start and another LED pattern. Both describe a 5-second hold for shutdown/sleep, triple-click GPS toggle, double-click position request and USB double-reset DFU. Use live client identity and telemetry to verify the state; do not classify hardware from one LED/timing table. [Current manual](https://www.elecrow.com/download/product/LMM14106D/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_User_Manual.pdf).

For recovery, back up configuration, connect stable USB power, press Reset twice within about 250 ms and select **ThinkNode M6** in the Meshtastic flasher. If downloaded manually, copy the exact M6 UF2 to the observed ThinkNode M6 drive and wait for restart. Restore region/channel settings and repeat the reply test. Do not use an ESP32 `.bin` or replace the bootloader merely because the application is quiet.

### Source build checkpoint

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e thinknode_m6
```

Expected output is an M6 artifact under `.pio/build/thinknode_m6/`; the build was not run here. Retain the unchanged-source build log before altering GPS, power, sleep or sensor code. Verify M6 support in the chosen release before flashing.

## Troubleshooting and FAQs <a href="#deployment-troubleshooting-and-faq" id="deployment-troubleshooting-and-faq"></a>

| Symptom                            | Ordered checks                                                                                                                 |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Dark LED makes the node appear off | Check fresh BLE/client identity, battery telemetry and a new packet; the power LED has deliberate low-power behavior           |
| Voltage falls despite sunlight     | Inspect shadows, dirt, orientation, cell state, GNSS/reporting intervals and accessory load; compare complete day/night cycles |
| No GPS                             | Check the correct GNSS antenna, receiver enable, sky view and a current timestamp                                              |
| App connected but no radio message | Match protocol, region, modulation and channel settings, then verify both actual receiving radios                              |
| DFU does not mount                 | Check data cable, stable USB power, double-reset timing and the exact M6 target                                                |
| External sensor cannot be read     | Obtain the SP11 contact orientation, rail/current rating and matching firmware driver before wiring                            |

The manual and wiki disagree on startup and LED timing. Record the installed firmware and live state rather than repeatedly resetting the device. IP65 depends on intact caps and seals and does not establish suitability for immersion.

## Downloads and technical documents <a href="#technical-documents-and-software" id="technical-documents-and-software"></a>

| Resource                                                                                                                                                                                                                                                                                              | Scope                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [M6 wiki](https://www.elecrow.com/wiki/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_Powered_By_nRF52840_Supports_GPS.html)                                                                                                                                                                         | Controls, LEDs, app setup and UF2 recovery                                        |
| [Complete 11-page user manual](https://www.elecrow.com/download/product/LMM14106D/ThinkNode_M6_Outdoor_Solar_Power_for_Meshtastic_User_Manual.pdf)                                                                                                                                                    | Mounting, solar care, controls, 5 V input, specifications and regulatory appendix |
| [Variant](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/ELECROW-ThinkNode-M6/variant.h) /[build](https://github.com/meshtastic/firmware/blob/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/ELECROW-ThinkNode-M6/platformio.ini) | Exact native pins, target and dependencies                                        |
| [CE/FCC archive](https://www.elecrow.com/download/product/LMM14106D/CE_and_FCC_Report.zip)                                                                                                                                                                                                            | Manufacturer-listed certification resource; not a schematic                       |

The [OpenELAB product](https://openelab.io/products/elecrow-thinknode-m6-outdoor-solar) also preserves battery MSDS, IEC 62133, UL 2054, UN 38.3 and transport documents. Consult the actual received battery label before using those certificates for a substituted cell. A complete SP11 pin/power drawing and mechanical CAD were not located in the above engineering resources.

### Retained illustrations

![Retained Elecrow ThinkNode M6 Development Guide illustration](../../.gitbook/assets/thinknode-m6-development-guide.webp)

### Existing reference links

* [Manufacturer wiki hub](./)
* [Manufacturer specifications](https://www.elecrow.com/thinknode-m6-outdoor-solar-power-for-meshtastic-powered-by-nrf52840-supports-gps.html)
* [Meshtastic flasher](https://flasher.meshtastic.org/)
* [Meshtastic hardware reference](https://meshtastic.org/docs/hardware/devices/elecrow/thinknode/)
* [MeshCore flasher](https://flasher.meshcore.co.uk/)

[Original OpenELAB product photograph](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/thinknode_m6_1_1_1.webp?v=1770871902).

## References and validation

The M6 wiki, full manual and pinned variant/build configuration were read. Control/indicator version differences and the undocumented SP11 electrical contact map are explicit. The bench-to-mount message/energy sequence is original engineering guidance; no RF distance or autonomy measurement is claimed.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
