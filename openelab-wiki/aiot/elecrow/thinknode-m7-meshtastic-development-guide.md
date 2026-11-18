# Elecrow ThinkNode M7 Meshtastic Gateway Engineering Guide

[ELECROW-LMM15507D](https://openelab.io/products/elecrow-thinknode-m7-meshtastic-gateway)

### Product and scope

**LMM15507D** is the **Meshtastic** ThinkNode M7 gateway. Elecrow also documents an **LML15607D LoRaWAN M7**. Despite the common M7 name, those network workflows are different.

### Hardware and technical documents

| Item              | Reference                                                          |
| ----------------- | ------------------------------------------------------------------ |
| Processor / radio | ESP32-S3 / LR1110                                                  |
| Networking        | Wi-Fi and Ethernet                                                 |
| Power             | USB-C 5V / 1A; supported IEEE 802.3af PoE, 37–57V input per manual |
| Interfaces        | USB-C, RJ45 and RF antenna connectors                              |
| Case              | 75 × 75 × 30mm excluding antenna in the quick guide                |

Use the **LMM15507D Meshtastic quick guide** for ports, supply and controls. Distinguish Ethernet connectivity, a mesh node role and any MQTT bridge configuration. They are not automatically equivalent.

### Getting started

1. Confirm LMM15507D and the RF region, then attach the correct antennas.
2. Power using USB-C or a compliant supported PoE source.
3. Connect using the manufacturer's Meshtastic setup route and inspect the installed version.
4. Set the legal region and matching channel/modem configuration for a second node.
5. Exchange a message first; then configure Ethernet/Wi-Fi and any intended MQTT bridge separately.

**Expected checkpoint:** local LoRa message exchange works before an internet bridge is introduced.

### Development software and recovery

The official Meshtastic hardware page identifies the **thinknode\_m7** firmware family. Use the manufacturer-supported flashing procedure and preserve configuration. Never substitute the LoRaWAN gateway's network-server setup or binary just because the enclosure is similar.

### FAQs

**Does RJ45 make it a LoRaWAN gateway?** This ordering code is the Meshtastic product.

**PoE does not power it?** Verify a standards-compliant source and the documented port; avoid an arbitrary passive injector.

**Local messages work but MQTT does not?** Check IP reachability, broker credentials and bridge settings as a separate layer.

### Sources and validation

* [Exact manufacturer product and SKU](https://www.elecrow.com/thinknode-m7-wireless-communication-gateway-for-meshtastic-support-poe-powered-powered-by-esp32-s3-and-lr1110.html)
* [Model-specific quick guide](https://www.elecrow.com/download/product/LMM15507D/Quick_Guide_of_ThinkNode_M7_for_Meshtastic.pdf)
* [Meshtastic target reference](https://meshtastic.org/docs/hardware/devices/elecrow/thinknode/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
