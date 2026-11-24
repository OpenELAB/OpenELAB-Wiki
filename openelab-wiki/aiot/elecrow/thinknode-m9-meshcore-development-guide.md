---
description: >-
  Set up the 868 MHz ThinkNode M9 MeshCore terminal, check shared SPI and
  standalone Ripple controls, and verify private messages, GNSS and maps.
---

# Elecrow ThinkNode M9 MeshCore Development Guide

{% hint style="info" %}
[**View Elecrow ThinkNode M9 MeshCore with 2.4 inch LCD & Keyboard on OpenELAB**](https://openelab.io/products/elecrow-thinknode-m9-meshcore-with-2-4inch-lcd-keyboard)

**Model / option:** 868 MHz With Case · **SKU:** `ELECROW-LMM16509D-868`
{% endhint %}

## Product overview <a href="#product-and-firmware-scope" id="product-and-firmware-scope"></a>

ThinkNode M9 LMM16509D is a standalone **MeshCore/Ripple** keyboard terminal. This page covers the purchased 868 MHz with-case option, M9 V1.0 hardware and the manufacturer guide's Ripple v12.0 interface. The similarly shaped **Meshtastic M9 LMM15409D** uses another application and has its own [Meshtastic guide](thinknode-m9-meshtastic-development-guide.md). Two devices must share a protocol as well as compatible radio settings.

Default M9 Standalone/Client operation does not make the handheld a repeater. Its local keyboard/display permit the basic text test without a phone. [Elecrow M9 MeshCore guide, 13 August 2026](https://www.elecrow.com/wiki/ThinkNode_M9_MeshCore_Communication_Terminal_with_Full_Keyboard.html).

## Applications

Use M9 for typed text, public/private channels, contact conversations, GNSS/map trials and diagnosing paths through an existing MeshCore repeater. Begin with two handhelds directly reachable, then introduce one routing change at a time. Offline LoRa chat does not need Wi-Fi licensing or a GNSS fix.

Treat map, time, sensor and Internet functions as separate acceptance checks. A Wi-Fi icon, cached position or previously heard node is evidence of a different boundary from a received private reply.

## Specifications

| Subsystem                    | M9 V1.0 scope                                                                                                                   |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Main / keyboard host         | ESP32-S3-R8 / separate ESP32-S2                                                                                                 |
| Radio                        | LR1110; purchased 868 MHz option                                                                                                |
| Screen                       | 2.4-inch LCD, 320 × 240                                                                                                         |
| GNSS                         | ATGM336H-5NR32 /BM72A named by manufacturer                                                                                     |
| RTC / sensors                | PCF8563, QMC6309, QMI8658B                                                                                                      |
| Battery / external interface | 2300 mAh rechargeable pack; USB-C charge/data; CH340K serial bridge                                                             |
| Flash / card                 | ZD25Q128CSIGT; microSD/TF. ZD25Q128 is a 128 Mbit (16 MB) flash device; old “16 GB” storage wording is not its onboard capacity |
| Local wireless               | 2.4 GHz Wi-Fi/BLE; radio-network interoperability is separate                                                                   |

The reviewed wiki specifies USB-C but no complete input-current rating or replacement-cell procedure. Use the assembled device's USB charging path and original pack; do not bypass its charger or fit a mechanically similar cell based on nominal capacity alone. [Hardware table](https://www.elecrow.com/wiki/ThinkNode_M9_MeshCore_Communication_Terminal_with_Full_Keyboard.html#131-key-specifications).

## Hardware and connections <a href="#hardware-and-developer-interfaces" id="hardware-and-developer-interfaces"></a>

### Power, bus sharing and pin namespaces

Fit the matching antenna before radio operation. Keep the enclosure/charging harness intact during first setup; no internal wiring is needed. USB supply and GPIO logic are different domains. The LCD, radio and card share SPI: keep non-target CS lines high, including during initialization.

| Internal connection                      | Main ESP32-S3 GPIO                      |
| ---------------------------------------- | --------------------------------------- |
| SPI SCK/MOSI/MISO                        | 40/47/38                                |
| LR1110 NSS/busy/IRQ/reset                | 39/41/42/45                             |
| LCD CS/reset/DC/backlight/TE             | 16/14/15/17/19                          |
| microSD CS                               | 48                                      |
| GNSS host RX/TX/PPS/reset                | 2/3/4/5                                 |
| GNSS on-off/power                        | 10/11                                   |
| RTC/sensor SDA/SCL                       | 7/6; QMC6309/QMI8658B through resistors |
| Peripheral enable / battery ADC / buzzer | 18/13/9                                 |
| Keyboard link SDA/SCL/wakeup             | 20/21/12                                |
| Main BOOT / key-light net                | 0/46                                    |

The keyboard matrix belongs to **ESP32-S2**, with its own GPIO numbering and firmware. The main host does not scan that matrix directly. LCD FPC J6 pins are also not the same as MCU numbers. Use the wiki's complete tables 2.2–2.8 for FPC, S2 rows/columns and maintenance-net details before custom wiring. [Official pin reference](https://www.elecrow.com/wiki/ThinkNode_M9_MeshCore_Communication_Terminal_with_Full_Keyboard.html#2-product-pinout).

No complete revision-specific schematic/CAD download was linked in that reviewed resource section. The pin tables enable software review but do not establish replacement-battery, power-injection or daughterboard wiring.

## Software and development resources <a href="#firmware-recovery-and-development" id="firmware-recovery-and-development"></a>

The source-reviewed user interface is **Ripple v12.0**, documented 13 August 2026 for M9 V1.0. Preserve that version/identity before updates. The general MeshCore source/flasher is a protocol/device resource; it does not establish that an arbitrary open-source M9 binary reproduces Ripple's entire standalone UI, licensed Wi-Fi features or map functions.

The manufacturer directs updates to the [MeshCore flasher](https://meshcore.io/flasher). Select firmware explicitly naming **ThinkNode M9** and the intended standalone/Companion application. Back up channels, identities and map/media first. An M9 Companion Bluetooth image changes how the phone communicates with it; it is not automatically the purchased standalone Ripple experience.

In Ripple's Terminal, **`get radio`** is a read-only configuration check. Its response is frequency in MHz, bandwidth in kHz, spreading factor, coding rate. Record those values; the network's displayed profile name does not prove they match a peer. [Radio and maintenance sections](https://www.elecrow.com/wiki/ThinkNode_M9_MeshCore_Communication_Terminal_with_Full_Keyboard.html#33-network-and-radio-settings).

## Getting started <a href="#getting-started-a-two-terminal-message-exchange" id="getting-started-a-two-terminal-message-exchange"></a>

### Original staged first result

Prerequisites: charged 868 MHz M9, correct antenna and a compatible MeshCore peer. Use local controls: D-pad focus, center confirm, Home home, Back return and Menu actions. A roughly 1 s center hold can blank/wake the screen on applicable pages; it is not proof of shutdown.

1. Verify startup identifies **MeshCore Ripple**, then finish the built-in selection/menu tutorial. Record firmware, physical node identity and the network profile before altering it.
2. Choose **New Network → MeshCore → appropriate complete local preset**. Give it a recognizable local name. At **Extra → Networks → selected profile → Profile Details**, compare frequency, BW, SF, CR with the peer. Keep Scope compatible; a MeshCore logical Region/Scope is not the 868/915 MHz hardware selection.
3. On A, open **Discover → Menu → Send ID Local**; on B use **Scan Local**. Reverse the roles. Inspect fresh last-heard identity rather than relying on an old contact row.
4. Open **Public**, send `M9-A-01`, receive it at B, and return `M9-B-01`. Wait for retries before repeating; rapidly flooding duplicate messages obscures the test.
5. Create/enable one private channel with the same name/slot/key at both ends, then exchange distinct messages. For a private contact, verify/save the discovered identity and test a reply separately. The channel name alone does not provide confidentiality.
6. Remove USB and repeat one private reply. Only after the direct pair works introduce a repeater and compare **Trace/Optimise**, last-heard, RSSI/SNR and actual delivery.

**Expected result:** two fresh message receipts in Public, then in the intended private channel/contact. “Heard” or a local chat-history entry alone does not confirm remote delivery. [Manufacturer operation guide](https://www.elecrow.com/wiki/ThinkNode_M9_MeshCore_Communication_Terminal_with_Full_Keyboard.html).

### GNSS, maps and optional online services <a href="#gnss-maps-and-service-dependencies" id="gnss-maps-and-service-dependencies"></a>

For GNSS, open **Extra → GPS Info**, enable the receiver and wait outdoors for a current Fix/Valid, time and coordinates. GNSS is not required for basic text. Use a FAT32 card with the installed release's map directory/tile format; test pan/zoom and an existing tile without a fix, then center on a fresh position. `none`, `share` and `prefs` location policies respectively omit, use current fix or use a stored location; choose deliberately before an advert.

Treat **Extra** as separate controls: Sound/Vib-LED alerts, timestamps, brightness/day-night, display sleep, timezone, GPS Config, waypoints and canned messages. Check one setting at a time with a received test message; enabled hardware does not prove every UI mode has been configured.

Wi-Fi/Internet Link/Core Browser/OTA features can require a device-specific **official Ripple license**. Use **Extra → Unlock** or the installed About/Activate/License entry and the [manufacturer-linked registration service](https://register.rippleradios.com). After activation/restart, scan/select a 2.4 GHz SSID and confirm Connected plus an IP before a time/Internet test. Licensing failure is independent of LoRa chat; no shared license or alternate firmware is assumed compatible.

Before updates export configuration and card contents, retain the working binary/version, and verify a vendor-provided checksum when available. Use only an exact M9 release, keep power/card stable, then repeat the direct message test. The reviewed documentation does not establish a universal raw flash offset or coprocessor recovery image, so those operations are excluded.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faq" id="troubleshooting-and-faq"></a>

| Failure                                | Isolate in this order                                                                                            |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| No discovery                           | Exact MeshCore application, four RF parameters, antenna/band, Send ID Local/Scan Local, then fresh time/Scope    |
| Public works, private fails            | Channel key/slot versus contact identity, recipient online, learned path; Trace/Optimise after a direct baseline |
| No map but GNSS fix                    | Card recognition, FAT32, release-specific tiles/directory/coverage/zoom                                          |
| Map works, no position                 | Device GPS enable, sky view, new fix and timestamp; cached tiles are not GNSS                                    |
| Wi-Fi icon only                        | Official unlock, 2.4 GHz SSID, credentials, Connected/IP, router access                                          |
| Radio fails after display/card changes | Shared SPI chip selects, peripheral power and exact M9 board support                                             |

Can a stock M9 extend everyone else's traffic? Its default Standalone/Client role does not automatically forward; use a supported Repeater role/device. Can the Meshtastic M9 and this MeshCore M9 exchange text unchanged? They need a compatible application protocol, not just the same RF band.

## Downloads and technical documents <a href="#technical-documents-and-software" id="technical-documents-and-software"></a>

| Resource                                                                                                                                                                                         | Exact scope                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| [Complete M9 MeshCore wiki](https://www.elecrow.com/wiki/ThinkNode_M9_MeshCore_Communication_Terminal_with_Full_Keyboard.html)                                                                   | V1.0 hardware/Ripple v12.0; 13 August 2026; full pins and local UI                  |
| [Manufacturer product/resources](https://www.elecrow.com/thinknode-m9-meshcore-communication-terminal-with-full-keyboard-2-4inch-lcd-esp32-s3-lr1110-gps-2300mah.html)                           | M9 MeshCore option and linked certification resources                               |
| [MeshCore flasher](https://meshcore.io/flasher) /[source](https://github.com/meshcore-dev/MeshCore)                                                                                              | Exact device/application selection; not proof of Ripple feature/license equivalence |
| [CE report](https://www.elecrow.com/download/product/LMM16509D/CE_Report_of_ThinkNode-M9.pdf) /[RoHS report](https://www.elecrow.com/download/product/LMM16509D/RoHS_Report_of_ThinkNode-M9.pdf) | Manufacturer-listed reports; separate from a schematic or firmware license          |

For a PCB, cell or enclosure redesign obtain the received revision's complete drawings; the current wiki's net tables are not a dimensional/power substitute.

### Retained illustrations

![Retained Elecrow ThinkNode M9 MeshCore Development Guide illustration](../../.gitbook/assets/thinknode-m9-meshcore-development-guide.webp)

[Original OpenELAB product photograph](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/global-elecrow-lmm16509d-01-thinknode-m9-white.webp?v=1786354648).

## References and validation

The manufacturer's complete hardware and Ripple operation sections were read, including pin namespaces, radio inspection, private channels/contacts, GNSS/maps, license-bound online features, roles/Scope and maintenance. The guide retains its canonical identity and original asset. The numbered acceptance sequence separates local UI, RF, routing and Internet failures.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
