# RAK10724 battery-powered WisMesh booster kit: power and Meshtastic setup

{% hint style="info" %}
[**View RAK10724 battery-powered WisMesh booster kit on OpenELAB**](https://openelab.io/products/rakwireless-wismesh-1w-booster-starter)

**Model/option:** RAK10724 battery-powered WisMesh booster kit · **Top-200 SKU:** `Rak-115280`
{% endhint %}

[Rak-115280](https://openelab.io/products/rakwireless-wismesh-1w-booster-starter)

## Product and scope

The battery-powered RAK10724 WisMesh kit supports Meshtastic mesh experiments, repeaters and portable/off-grid nodes. OpenELAB Rak-115280 is scoped here as the battery-powered variant. Current battery and external-5 V kits use different amplifier power hardware; a software setting does not convert one into the other.

## Hardware and technical documents

| Item                | Reference                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------- |
| Compute             | RAK3401 with Nordic nRF52840                                                              |
| Radio and amplifier | RAK13302: SX1262 radio and SKY66122 amplifier                                             |
| Base                | RAK19007                                                                                  |
| Hardware capability | Up to 1 W RF output; permitted operating power depends on region and antenna              |
| Power requirement   | Battery version requires the specified Li-ion battery; USB alone cannot power the booster |

Download the battery-powered RAK10724 quick-start PDF from RAK's Meshtastic download center. Follow that exact diagram for battery connector polarity, supported cell and charging input. The external-5 V variant's instructions are different. Attach the correct antenna before transmitting and inspect RF connectors with power removed.

## Getting started

1. Check kit labels and verify it is the battery-powered version. Compare board revisions with the battery quick-start guide.
2. Connect the specified battery with verified polarity. Do not expect USB or the solar input alone to operate this version's amplifier.
3. Use the RAK-supported Meshtastic firmware target and initial configuration instructions. Record firmware release and board identity before changing firmware.
4. Set the permitted regional plan and appropriate transmit power, then configure a second compatible Meshtastic node with matching channel/modem settings.
5. Exchange short messages at close range and record delivery, RSSI/SNR and battery behavior before evaluating range or solar charging.

**Expected checkpoint:** Stable operation from the correct battery supply and a successful two-node message exchange with documented radio settings.

## Development software and recovery

Use the manufacturer quick-start guide and Meshtastic tools for the supported target. A 1 W hardware ceiling is not a recommendation to transmit at that setting. Investigate supply sag and antenna path before raising power when messages fail. Preserve a configuration backup before reflashing.

## FAQs

**Why does the node connect over USB but fail to transmit reliably?** USB can expose the controller while the booster still lacks its required battery power.

**Can I switch the current battery model to external 5 V with a jumper?** The manufacturer states that current hardware uses separate modules for the two power options; follow the exact revision's instructions.

**Does 1 W guarantee longer range?** Range also depends on antennas, terrain, placement and radio settings.

## Sources and validation

* [RAK10724 manufacturer hardware and variant notes](https://store.rakwireless.com/products/meshtastic-1w-lora-booster-kit-rak3401)
* [RAK quick-start PDF download center](https://downloads.rakwireless.com/Meshtastic/)
* [Manufacturer comparison of power variants](https://forum.rakwireless.com/t/which-wismesh-high-power-booster-starter-kit-fits-your-setup/17605)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
