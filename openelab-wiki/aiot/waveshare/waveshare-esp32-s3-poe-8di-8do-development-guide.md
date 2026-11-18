# Waveshare ESP32-S3 PoE 8DI 8DO Controller Engineering Guide

{% hint style="info" %}
[**View Waveshare ESP32-S3 PoE 8DI 8DO Controller on OpenELAB**](https://openelab.io/products/waveshare-industrial-esp32-s3-poe-eth-8di-8do-control-board)

**Model/family:** Waveshare ESP32-S3 PoE 8DI 8DO Controller · **OpenELAB SKU:** `Waveshare-32108`
{% endhint %}

[Waveshare-32108](https://openelab.io/products/waveshare-industrial-esp32-s3-poe-eth-8di-8do-control-board)

## Product and scope

**32108 ESP32-S3-POE-ETH-8DI-8DO** has transistor digital outputs for low-voltage industrial I/O. It is **not the 8RO relay controller**; their output wiring and examples differ.

## Hardware and technical documents

| Item       | Reference                                                                                      |
| ---------- | ---------------------------------------------------------------------------------------------- |
| Controller | ESP32-S3; Wi-Fi/BLE                                                                            |
| Inputs     | Eight optocoupler-isolated inputs                                                              |
| Outputs    | Eight optocoupled Darlington sinking outputs; up to 500mA per documented channel specification |
| Networking | W5500 10/100 Ethernet; IEEE 802.3af PoE                                                        |
| Fieldbus   | Isolated RS485 and CAN                                                                         |
| Power      | 7–36V terminal or documented USB-C 5V/1A path                                                  |

Use the current manufacturer's **interface diagram, output/load circuit, schematic and dimensions**. A sinking output requires the correct external load supply and reference wiring. Check per-channel and total thermal/load limits before connecting inductive loads.

## Getting started

1. Leave outputs unloaded and verify the exact model/terminal labels.
2. Power using one supported path and connect USB data.
3. Build or restore the manufacturer's **8DI-8DO** example using its supplied dependency versions.
4. Connect one supported low-voltage input and confirm its reported state.
5. Test one output with a suitably limited low-voltage indicator/load using the manufacturer's sinking-output diagram.

**Expected checkpoint:** correct single-channel input/output behavior, followed by stable Ethernet enumeration.

## Development software and recovery

The manufacturer provides Arduino instructions, firmware flashing/erasing and a dedicated FAQ. Its output-expander map differs from the relay board. Save the demo, library versions and network settings. Recover through the documented BOOT/USB workflow.

## FAQs

**Can a load be wired like a dry relay contact?** No; use the transistor-output circuit.

**No Ethernet connection?** Check W5500 initialization, cable, link, IP configuration and SPI pin map.

**Can RS485 and CAN share a cable pinout?** They are distinct electrical buses and connectors.

## Sources and validation

* [Exact model specifications and pin map](https://docs.waveshare.com/ESP32-S3-POE-ETH-8DI-8DO)
* [First-use instructions](https://docs.waveshare.com/ESP32-S3-POE-ETH-8DI-8DO/Instructions-For-Use)
* [Legacy resource index](https://www.waveshare.com/wiki/ESP32-S3-POE-ETH-8DI-8DO)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
