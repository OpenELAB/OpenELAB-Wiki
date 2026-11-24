---
description: >-
  Commission the ThinkNode M7 Meshtastic Ethernet gateway, test local radio and
  LAN access, and validate MQTT forwarding without antenna removal or M5
  firmware.
---

# Elecrow ThinkNode M7 Meshtastic Gateway Engineering Guide

{% hint style="info" %}
[**View Elecrow ThinkNode M7 Meshtastic Wireless Communication Gateway on OpenELAB**](https://openelab.io/products/elecrow-thinknode-m7-meshtastic-gateway)

**Model / option:** Default Title · **SKU:** `ELECROW-LMM15507D`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

ThinkNode M7 LMM15507D is a fixed **Meshtastic LoRa node with Ethernet, Wi-Fi/BLE and optional IEEE 802.3af PoE**. It combines ESP32-S3, LR1110 and a CH390D Ethernet path. “Gateway” here means a Meshtastic/IP/MQTT bridge, not a multi-channel LoRaWAN concentrator.

Start with USB power, local BLE configuration and a second physical Meshtastic radio. Add Ethernet and then MQTT only after the direct radio link works. [Manufacturer wiki](https://www.elecrow.com/wiki/ThinkNode_M7_Meshtastic_Wireless_Communication_Gateway.html), [CM01 V1.0 manual, 8 September 2026](https://www.elecrow.com/download/product/LMM15507D/ThinkNode_M7_for_Meshtastic.pdf).

## Applications

Use M7 as a fixed indoor mesh endpoint, a wired network-managed node or a deliberate MQTT bridge between supported Meshtastic networks. Keep radio delivery, local IP access and broker delivery as separate measurements.

An Ethernet link light does not prove DHCP, a connected phone does not prove radio delivery, and an MQTT session does not prove a remote gateway rebroadcast the intended packet. Record the complete path and unique payload at each boundary.

## Specifications

| Item                       | M7 scope                                                                 |
| -------------------------- | ------------------------------------------------------------------------ |
| Host                       | ESP32-S3, dual-core up to 240 MHz                                        |
| Reviewed build layout      | 8 MB flash partition; PSRAM-enabled source target                        |
| LoRa                       | LR1110; EU868/US915 hardware options; match received antenna/band        |
| Published transmit maximum | 22 dBm; not a universal legal/default setting                            |
| Network                    | 10/100 Mbps RJ45; 2.4 GHz 802.11 b/g/n; BLE                              |
| USB input                  | 5 V / 1 A USB-C, console/power                                           |
| PoE                        | IEEE 802.3af, 37–57 V DC documented; verify actual PoE-equipped assembly |
| Antenna interfaces         | Separate RP-SMA LoRa and WLAN/BLE paths; listed 4 dBi antennas           |
| Size / mass                | 75 × 75 × 30 mm excluding antennas / 108 g                               |
| GNSS / display             | Neither is enabled in reviewed M7 source                                 |

The quick card's BR/EDR wording is not established by this review; the full manual identifies BLE 5.0. Sensitivity figures are conditional on spreading factor/bandwidth. The source's memory configuration is a build layout, not proof of every accessory/production memory option. [Full manual specifications](https://www.elecrow.com/download/product/LMM15507D/ThinkNode_M7_for_Meshtastic.pdf), [exact board definition](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/boards/ThinkNode-M7.json).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Commission power and Ethernet separately

Attach the two correctly identified antennas, then use USB-C 5 V / 1 A. For the first LAN test connect ordinary Ethernet to the router **while retaining USB power**. The full manual's “without PoE” diagram explicitly separates the power cable and data cable.

For a verified PoE-equipped M7, use an IEEE 802.3af source/injector and the manufacturer's data-in/data-and-power-out arrangement. A passive injector is not equivalent merely because it has RJ45 connectors. This guide does not authorize applying 37–57 V to USB or signal pads, or simultaneous independent power-source experiments. [Manual physical wiring, printed p.12](https://www.elecrow.com/download/product/LMM15507D/ThinkNode_M7_for_Meshtastic.pdf).

Mount only after the bench reply test: fasten the base, align the bottom slots and rotate clockwise to lock. Retain cable strain relief and access to Reload/USB. This indoor assembly has no established weatherproof rating in the reviewed documents.

### Internal source reference

| Role                                  | M7 ESP32-S3 GPIO       |
| ------------------------------------- | ---------------------- |
| LR1110 SCK / MOSI / MISO / CS         | 11 / 10 / 9 / 12       |
| LR1110 reset / IRQ / busy             | 39 / 38 / 13           |
| Ethernet SCK / MOSI / MISO / CS / INT | 47 / 48 / 14 / 21 / 45 |
| UART TX / RX                          | 43 / 44                |
| Button / LED                          | 4 / 3; active LOW      |
| BLE/LoRa indicator                    | 46                     |

These are occupied internal nets, not externally exposed connector contacts. Keep Ethernet and radio drivers on their own bus definitions. The radio uses LR1110 DIO RF switching and a **1.8 V TCXO driver setting**. M9 also uses LR1110 but has a different pin map, TCXO setting and UI. [M7 variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M7/variant.h).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The reviewed source environment is **`thinknode_m7`**, board **`ThinkNode-M7`**, at commit **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**. It uses the 8 MB partition table and ESP32-CH390 **v1.2**. Its comments warn that excluding Arduino Ethernet can remove required IDF component headers. Keep the exact dependency/configuration set rather than transplanting an M5 image. The environment is marked `board_level = pr`; source presence is not certification of a released recovery binary. [Build file](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M7/platformio.ini).

The source requests LR1110 firmware `0x0402`; comments describe a shipped `0x0303` limitation on 500 kHz LoRa reception. Preserve the exact board update implementation; this is not an instruction to flash a generic transceiver image. Begin with an ordinary mutually supported preset.

**Firmware conflict:** the live manufacturer wiki still points to M5 as a temporary flashing reference. M5 hardware/firmware is not interchangeable with M7. This guide's main procedure uses the supplied M7 application; raw firmware offsets, bootloader replacement and M5-image recovery are excluded. Meshtastic source is GPL-3.0 with separate dependency notices.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original direct radio and LAN acceptance

Prepare M7, both supplied antennas, USB power/data cable, a phone/client and a compatible peer. Back up the working configuration before changing it.

1. Power by USB-C and record the M7 node ID/firmware. The documented factory PIN is `123456`; use its current configured PIN if changed. Pair the actual device, not a similarly named node from a scan.
2. Select the permitted Region and match the peer's modem preset, frequency slot and complete channel name/key. Save and wait for restart. Do not copy the manual's 22 dBm/frequency-override screenshot as a universal configuration.
3. Send `M7-RF-A-01`, confirm receipt at the peer, return `M7-RF-B-01` and confirm receipt at M7. Repeat several numbered pairs, logging each actual receiver's time and RSSI/SNR.
4. Keeping USB power, connect the RJ45 data cable to the router. Put the management phone/computer on the same LAN, verify the assigned IP in router/device records and choose the app's **Network** connection. Read the same node ID over that connection.
5. Send a new numbered message while managing over Ethernet and confirm an RF reply. Distinguish a configuration transport change from a radio-path change.
6. If Wi-Fi is needed instead, first configure the 2.4 GHz SSID/password through BLE or Ethernet. The manufacturer states BLE management is disabled after Wi-Fi is enabled; reconnect by Network on the same LAN rather than treating lost BLE as hardware failure.

**Expected result:** direct RF receipt in both directions plus the same node identity read over the chosen LAN transport. No Internet or MQTT result is implied. [Manual BLE/LAN procedure](https://www.elecrow.com/download/product/LMM15507D/ThinkNode_M7_for_Meshtastic.pdf).

### Original bounded MQTT bridge test

Use a broker and two gateways/networks you control. Preserve channel keys and avoid publishing location by default. Follow the installed Meshtastic release's actual MQTT fields:

1. Establish each gateway's IP access and broker reachability. Configure the broker address, authentication, TLS and a dedicated root topic/ACL. Use matching intended channel configuration at both ends.
2. Enable the MQTT module and the chosen channel's uplink/downlink only as required. The **Okay to MQTT** flag and channel permissions are separate from the module's server connection.
3. Choose the transport deliberately. **Client Proxy Enabled** sends through a connected phone/client; for an independent Ethernet gateway use the node's own network path, rather than copying the wiki's proxy-on setting unconditionally. The current official docs also state web-client proxy is not functional.
4. Send one unique payload, confirm it at the broker, then at the remote gateway/receiving node. Record packet/node IDs, topic and receive times, separating RF repeats from Internet forwarding.
5. To isolate the Internet path, use documented transmit-disable settings on the relevant controlled nodes or adequate physical separation and broker logs. **Keep antennas attached**. The manufacturer's suggestion to remove an antenna during the test is not used here.

**Expected result:** a traceable payload across the intended broker path, not just two gateways that can already hear each other directly. A broker outage should leave the separately tested local RF path diagnosable. [Official MQTT field semantics](https://meshtastic.org/docs/configuration/module/mqtt/), [manufacturer bridge architecture](https://www.elecrow.com/wiki/ThinkNode_M7_Meshtastic_Wireless_Communication_Gateway.html).

### Source build and recovery boundary

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e thinknode_m7
```

Expected output is an M7 artifact under `.pio/build/thinknode_m7/`; no successful build is claimed. Preserve the correct board's partition layout and verify a supported release/recovery path before upload.

The full manual assigns **15-second Reload hold** to factory reset. This can erase working settings; use it only after backing up and exhausting read-only connection checks, then restore Region/channels and repeat the RF test. It is not documented here as an ESP32 bootloader-entry gesture. If the supplied application cannot boot, obtain exact M7 recovery instructions/image rather than following the stale M5 redirect.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                              | Ordered checks                                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| No power                             | USB 5 V / 1 A path, cable and actual PoE hardware/source; no passive-PoE assumption                                 |
| BLE disappears after Wi-Fi enabled   | Expected management-mode change; same-LAN Network connection and current IP                                         |
| Ethernet link but app cannot connect | DHCP/static IP, same subnet, router/client isolation, discovered node identity                                      |
| Nodes visible but no reply           | Fresh last-heard, full channel key/slot, Region/preset, antennas and actual receiver                                |
| MQTT enabled but no remote delivery  | Broker/TLS/auth/root topic, channel permissions, node-network versus client-proxy transport, broker and remote logs |
| Only wide-band presets fail          | Host/transceiver versions and exact M7 LR1110 update support; do not substitute M9/M5 binaries                      |
| Settings appear unchanged            | Save/sync/restart first; backup before destructive Reload reset                                                     |

Does this have built-in GNSS? The reviewed M7 target disables GPS. Does MQTT make it a LoRaWAN gateway? It remains a Meshtastic single-radio/IP bridge.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                                                              | Scope                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [23-page M7 manual](https://www.elecrow.com/download/product/LMM15507D/ThinkNode_M7_for_Meshtastic.pdf)                                                                                                                                                                                                                               | CM01 V1.0, 8 September 2026; controls, mounting, power, BLE/LAN and FAQ                      |
| [Four-page quick card](https://www.elecrow.com/download/product/LMM15507D/Quick_Guide_of_ThinkNode_M7_for_Meshtastic.pdf)                                                                                                                                                                                                             | Physical controls, base installation and power summary; BLE wording differs from full manual |
| [M7 wiki](https://www.elecrow.com/wiki/ThinkNode_M7_Meshtastic_Wireless_Communication_Gateway.html)                                                                                                                                                                                                                                   | Mesh/MQTT architecture; apply antenna/proxy/firmware corrections above                       |
| [Pinned variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M7/variant.h) / [environment](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/esp32s3/ELECROW-ThinkNode-M7/platformio.ini) | Exact radio/Ethernet support and dependencies                                                |
| [MQTT module reference](https://meshtastic.org/docs/configuration/module/mqtt/)                                                                                                                                                                                                                                                       | Current field semantics and client/network distinctions                                      |

No exact complete M7 electrical schematic or mechanical CAD was located in these reviewed resources. The manual's physical power diagram is useful but does not establish internal PoE pin wiring.

### Additional existing resources

* [Exact manufacturer product and SKU](https://www.elecrow.com/thinknode-m7-wireless-communication-gateway-for-meshtastic-support-poe-powered-powered-by-esp32-s3-and-lr1110.html)
* [Meshtastic target reference](https://meshtastic.org/docs/hardware/devices/elecrow/thinknode/)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The full manual, quick card, complete manufacturer wiki and pinned M7 board/variant/environment were read. The power/Ethernet diagram was visually inspected. Official MQTT semantics resolve the unconditional client-proxy assumption. Original procedures isolate local RF, LAN and broker delivery while explicitly excluding stale M5 flashing guidance and antenna removal.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
