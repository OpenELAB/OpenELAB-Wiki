# Waveshare ESP32-S3 8DI 8RO Relay Controller Engineering Guide

{% hint style="info" %}
[**View Waveshare ESP32-S3 8DI 8RO Relay Controller Engineering Guide on OpenELAB**](https://openelab.io/products/waveshare-industrial-8-channel-esp32-s3-wifi-relay-eth-8di-8ro-module-rs485)

**Model:** Waveshare ESP32-S3 8DI 8RO Relay Controller Engineering Guide · **OpenELAB SKUs:** `Waveshare-30838`, `Waveshare-31130` · Verify the hardware variant before use.
{% endhint %}

[Waveshare-30838](https://openelab.io/products/waveshare-industrial-8-channel-esp32-s3-wifi-relay-eth-8di-8ro-module-rs485) · [Waveshare-31130](https://openelab.io/products/waveshare-industrial-8-channel-esp32-s3-wifi-relay-eth-8di-8ro-module-rs485)

## Product and scope

These **eight-input/eight-relay** controllers support networked switching and automation prototypes. **30838 is the PoE version; 31130 is the non-PoE version.** The similarly named 8DI-8DO transistor-output board is different.

## Hardware and technical documents

| Item       | Reference                                                                |
| ---------- | ------------------------------------------------------------------------ |
| 31130      | ESP32-S3-ETH-8DI-8RO                                                     |
| 30838      | ESP32-S3-POE-ETH-8DI-8RO                                                 |
| Processor  | ESP32-S3, Wi-Fi/BLE                                                      |
| Interfaces | Ethernet, isolated RS485 and digital inputs                              |
| Power      | 7–36V terminal input per manufacturer; PoE only on the PoE configuration |
| Outputs    | Relay contacts; consult load-specific AC/DC ratings                      |

Use the **exact controller schematic, terminal diagram and dimensional drawing** from the manufacturer's resource page. Relay contacts are not powered logic outputs. Initial tests should use a low-voltage isolated test load; contact ratings do not replace load/inrush and enclosure design.

## Getting started

1. Identify the full model label and disconnect external loads.
2. Connect documented bench power and USB data; inspect host enumeration.
3. Follow the official factory-control or Arduino example for **8DI-8RO**.
4. Toggle one unloaded relay and verify the expected contact pair using an appropriate continuity test with power/load conditions controlled.
5. Add one documented low-voltage input, check its status, and then test Ethernet or RS485 separately.

**Expected checkpoint:** one input and one relay channel behave predictably before adding the remaining channels or network automation.

## Development software and recovery

Use the exact Arduino demo, libraries and pin map in the manufacturer's resources. Save factory firmware and serial/network configuration. Enter its BOOT/download mode for restoration if custom firmware prevents normal communication.

## FAQs

**Does SKU 31130 accept PoE?** The manufacturer maps PoE to 30838; inspect the fitted model.

**A relay clicks but the load is off?** Check COM/NO/NC wiring and the load's separate supply.

**USB powers the board but no port appears?** Check data cable, boot mode and host device enumeration before declaring a hardware fault.

## Sources and validation

* [Exact SKU 30838](https://www.waveshare.com/esp32-s3-eth-8di-8ro.htm?sku=30838)
* [Exact SKU 31130](https://www.waveshare.com/esp32-s3-eth-8di-8ro.htm?sku=31130)
* [Current manufacturer SKU/power map](https://docs.waveshare.net/ESP32-S3-ETH-8DI-8RO/)
* [English examples and resources](https://www.waveshare.com/wiki/ESP32-S3-ETH-8DI-8RO)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
