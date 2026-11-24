---
description: >-
  Commission the battery-powered RAK10724 WisMesh booster kit, identify VD code
  001, select RAK3401 1W firmware and test power-backed two-way messages.
---

# RAK10724 battery-powered WisMesh booster kit: power and Meshtastic setup

{% hint style="info" %}
[**View RAKwireless RAK10724 WisMesh 1W Booster Kit, Battery Powered on OpenELAB**](https://openelab.io/products/rakwireless-wismesh-1w-booster-starter)

**Model / option:** 868MHz · **SKU:** `Rak-115280`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

RAK10724 **Rak-115280, 868 MHz battery-powered option** combines RAK3401, the RAK13302 SX1262/SKY66122 booster and RAK19007 base. **A suitable rechargeable battery is required for this power variant. USB is useful for configuration/charging but cannot independently supply its high-power radio path.**

Identify the radio-board revision before following a power diagram. Current **VD code 001** is battery-only; VD code 002 is a different external-5 V assembly. Older VC had a jumper. This guide covers the purchased battery option and preserves those differences rather than treating them as software settings. [Current kit guide](https://docs.rakwireless.com/product-categories/meshtastic/wismesh-starter-kit-rak3401/quickstart/), [manufacturer option table](https://store.rakwireless.com/products/meshtastic-1w-lora-booster-kit-rak3401).

## Applications

Use the kit for controlled Meshtastic links, battery-backed fixed nodes and modular sensor integration. Begin in an ordinary client role with a direct peer before changing routing behavior or increasing output power.

Separate RF hardware capability from a permitted configuration. “1 W” is a peak RF capability, not average energy use, a guaranteed range or a required first-test power level. Compare actual packet receipts and source voltage under load.

## Specifications

| Item                | Battery-powered RAK10724 scope                                                             |
| ------------------- | ------------------------------------------------------------------------------------------ |
| Core                | RAK3401, Nordic nRF52840; external radio module required                                   |
| Radio               | RAK13302, SX1262 + SKY66122 PA/LNA/filter path                                             |
| Base                | RAK19007, 30 × 60 mm; core, IO and four sensor slots                                       |
| Purchased RF option | 868 MHz; match 863–870 MHz antenna/hardware label                                          |
| Firmware family     | `rak3401-1watt`; not generic RAK4631 LoRa firmware                                         |
| Battery             | Rechargeable 3.7 V nominal Li-ion/LiPo, 4.2 V charge chemistry; correct connector polarity |
| Battery connector   | Base P2, JST PHR-2 mating housing, 2 mm pitch                                              |
| USB charging        | Base documented 350 mA; source 4.5–5.5 V charging range                                    |
| Solar charging      | 5 V panel to base P1; **must not exceed 5.5 V**; JST ZHR-2, 1.5 mm pitch                   |
| Base logic          | 3.3 V and switched 3V3\_S; not a 5 V logic interface                                       |

The RAK19007 datasheet's generic battery discharge recommendation of at least 500 mA is **not enough to size the 1 W booster at maximum output**. The VD amplifier table reaches 1000 mA at its 5 V rail near 30 dBm. Battery current before boost is higher: ideally `Ibat = 5 V × I5V / Vbat`, then increases with conversion losses. At 3.7 V and 1 A/5 V that ideal lower bound is about 1.35 A. Select a documented cell/harness for the actual workload and conversion peaks; no universal battery rating is inferred here.

The VD component datasheet currently describes 902–928 MHz while the kit/store explicitly offer this 868 MHz option. Its RF/current curves are therefore **reference conditions, not independently verified 868 MHz performance**. Do not copy its 30 dBm/US certification configuration as an EU setting. [Base electrical data](https://docs.rakwireless.com/product-categories/wisblock/rak19007/datasheet/), [VD module data](https://docs.rakwireless.com/product-categories/wisblock/rak13302/datasheet-vd).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Identify VD versus VC before attaching power

| RAK13302 hardware   | Identification                                          | Power action                                                      |
| ------------------- | ------------------------------------------------------- | ----------------------------------------------------------------- |
| VD battery variant  | Label code **001**, no underside external-5 V connector | Use suitable battery on the base; USB/solar charge it             |
| VD external variant | Label code **002**, underside external-power connector  | Different purchased hardware; use its dedicated 5 V instructions  |
| Older VC            | Physical three-pin power selector                       | Follow the VC drawing; do not transfer its jumper procedure to VD |

![RAKwireless VD battery-supply label showing code 001](https://res.rakwireless.com/ext/images.docs.rakwireless.com/wisblock/rak13302/datasheet/vd-battery-variant.png?fm=webp)

_RAKwireless illustration, from the VD datasheet. Code 001 identifies the battery variant; it is not a connector polarity drawing._

With all sources disconnected, inspect the core/IO modules and secure them with their matching M1.2 × 3 mm fasteners. Apply removal force only at the documented connector support, never pry a module by its RF socket. Fit the LoRa antenna to **RAK13302** and BLE antenna to **RAK3401** before power. Press IPEX connectors vertically with alignment; keep pigtails strain-relieved.

Connect the rechargeable cell to **base P2** only after its V+/GND orientation matches the board's marked polarity and [official connector drawing](https://images.docs.rakwireless.com/wisblock/rak19007/datasheet/battery-connector.svg). Do not infer polarity from wire color or plug fit. Base solar **P1** is a different connector and charging input; do not attach a 12 V panel or use it as a battery substitute. Keep 5 V USB distinct from 3.3 V signal headers. [Battery first-step diagram](https://downloads.rakwireless.com/Meshtastic/Quick%20Start%20Guide_WisMesh%20High%20Power%20Booster%20Starter%20Kit%20RAK10724%20\(Battery-Powered\).pdf).

### Occupied radio nets and expansion

| Role                           | Pinned nRF52840 native signal            |
| ------------------------------ | ---------------------------------------- |
| RAK13302 SCK / MOSI / MISO     | P0.03 / P0.30 / P0.29                    |
| Radio CS / DIO1 / busy / reset | P0.26 / P0.10 / P0.09 / P0.04            |
| Radio power enable             | P0.21                                    |
| Main I²C SDA / SCL             | P0.13 / P0.14                            |
| Switched 3V3\_S enable         | P1.02, `WB_IO2`; shared peripheral power |
| Battery ADC                    | P0.05 in reviewed target                 |

The radio uses SPI1; do not take the variant's unrelated primary-SPI aliases as its physical bus. DIO2 RF switching and a **1.8 V TCXO driver setting** belong to the exact target. The radio pin assignments consume IO lines that generic WisBlock sensor examples may expect to use.

The base's J12 numbered header is 1 VDD, 2 GND, 3 SCL, 4 SDA; J10 is 1 BOOT, 2 GND, 3 TX1, 4 RX1. Match actual pin-1 orientation and RAK3401 routing before attaching a peripheral. `WB_IO2` is also a shared power control: turning it off to save one GPS module can remove other devices. Select compatible sensor slots and check conflicts before installation. [Base headers/slot map](https://docs.rakwireless.com/product-categories/wisblock/rak19007/datasheet/), [exact variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/rak3401_1watt/variant.h).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The reviewed Meshtastic environment is **`rak3401-1watt`**, commit **`d0f4096788545fb3c5e22d2a7e52ac6c268caac1`**. It intentionally uses board `wiscore_rak4631` while adding **RAK3401 and RAK13302** definitions and the external-radio map. That build-board reuse does not make a normal RAK4631 radio binary suitable. The manufacturer specifies filename family **`firmware-rak3401-1watt-…uf2`** for this kit.

The target includes booster support; retain its RF power handling. A generic SX1262 example setting is not the final amplified RF output. The module datasheet's chip-setting/output table is a separate characterization, not a universal Meshtastic `tx_power` conversion table. [Pinned build configuration](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/rak3401_1watt/platformio.ini).

For custom Arduino sensor code RAK documents BSP compatibility with the RAK4631 board, but explicitly excepts the ordinary RAK4631 **LoRa/LoRaWAN examples**, because RAK3401 has no integrated radio. Use the RAK13302-specific external-radio example/driver. Core bootloader updates, application UF2 and radio support are different layers. Meshtastic is GPL-3.0; BSP/example dependencies keep their own licenses.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Original battery-backed direct-link acceptance

Prepare the verified 868 MHz kit, both antennas, suitable rechargeable cell/harness, USB data cable and a compatible Meshtastic peer. Keep the supplied application for the first pass.

1. With power removed inspect RAK13302 revision and code 001 for current VD battery hardware. If the label is 002 or hardware differs, stop and use that variant's power guide. Save module revisions, battery specification and antenna identity.
2. Attach both correct antennas, verify P2 battery polarity and connect the battery, then USB for configuration. Read live firmware/node identity in the client. USB enumeration alone does not establish booster power.
3. Select the permitted Region and a conservative permitted transmit-power configuration in the exact target. Match the peer's modem preset, frequency slot and complete channel name/key. Do not use maximum RF power to compensate for unmatched settings.
4. Send `RAK10724-A-01`, confirm receipt at the second physical radio, return `RAK10724-B-01` and confirm the kit receives it. Repeat several numbered pairs, recording receive time and RSSI/SNR.
5. Disconnect USB while keeping the suitable battery connected. Repeat a reply and read battery telemetry. Monitor for resets or voltage droop during transmissions before blaming RF range.
6. Only after direct acceptance evaluate planned placement or routing role. Record duty cycle, battery trend, enclosure temperature and charging conditions over complete day/night cycles before unattended use.

**Expected result:** confirmed text in both directions on the correct battery-backed hardware, including a reply with USB removed. No 1 W output, range or runtime was measured. [Exact kit quick start](https://docs.rakwireless.com/product-categories/meshtastic/wismesh-starter-kit-rak3401/quickstart/).

### Read-only host backup

Replace `YOUR_PORT` with the observed USB serial device and close other serial clients. Keep resulting channel/security data private.

```sh
python3 -m venv .venv-rak
. .venv-rak/bin/activate
python -m pip install meshtastic
meshtastic --port YOUR_PORT --info > rak10724-info.txt
meshtastic --port YOUR_PORT --nodes > rak10724-nodes.txt
```

Expected result is readable identity/configuration and known-node records. This does not send radio traffic or change region/power. If the installed CLI has changed, inspect its local help before modifying configuration.

### Build and application recovery

```sh
git clone --recursive https://github.com/meshtastic/firmware.git
cd firmware
git checkout d0f4096788545fb3c5e22d2a7e52ac6c268caac1
git submodule update --init --recursive
python3 -m venv .venv
. .venv/bin/activate
python -m pip install platformio
pio run -e rak3401-1watt
```

Expected output is the exact target artifact under `.pio/build/rak3401-1watt/`; no compile was run. Preserve a known-good released application and configuration before flashing.

For UF2 recovery, connect stable USB and double-press the **base Reset** button. The RAK3401 guide documents a drive named **RAK4631** because of the shared bootloader; inspect `INFO_UF2.TXT` and actual hardware identity rather than choosing application firmware by drive name. Copy only the **RAK3401 1W** UF2, wait for restart, restore Region/channel settings and repeat the battery-backed reply. Do not copy a generic RAK4631, LR2021 or a repeater-specific application merely because it also mentions RAK3401.

The core guide includes USB/BLE/J-Link bootloader maintenance. Those procedures replace a different firmware layer and are excluded from ordinary application recovery; a quiet radio or changed drive date alone is not enough reason to reflash a bootloader.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                             | Ordered checks                                                                                              |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| USB/BLE works, RF unreliable        | Actual VD battery variant, battery present/suitable, rail droop, exact 1W target and antenna                |
| Cannot find power jumper            | Current VD has fixed variants; do not follow obsolete VC jumper steps                                       |
| Reset during TX                     | Cell/harness load capability and boost demand; base charger/current recommendations do not size the booster |
| Receiver sees no packet             | Region/modem/slot/key, correct 868 MHz assembly/antenna and actual receiver; no generic RAK4631 firmware    |
| Sensor disappears when GPS sleeps   | Shared `WB_IO2` / 3V3\_S power and radio/slot pin conflicts                                                 |
| RAK4631 drive name causes confusion | Shared bootloader is documented; application remains `rak3401-1watt`                                        |
| Battery declines while charging     | Workload, duty cycle, base 350 mA charging and solar availability; observe a full energy cycle              |

Can software convert VD battery power to external-5 V? No; these are separate VD hardware variants. Does the stock kit include GNSS? Not in the documented core/radio/base kit; it is an expansion module, not an inferred built-in feature.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                                            | Exact scope                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [Battery-powered quick-start PDF](https://downloads.rakwireless.com/Meshtastic/Quick%20Start%20Guide_WisMesh%20High%20Power%20Booster%20Starter%20Kit%20RAK10724%20\(Battery-Powered\).pdf)                                                                                                                         | Antenna/core/base connections and correct UF2 family                                          |
| [Current kit full guide](https://docs.rakwireless.com/product-categories/meshtastic/wismesh-starter-kit-rak3401/quickstart/)                                                                                                                                                                                        | VD versus VC, module mounting and power variants                                              |
| [RAK19007 datasheet](https://docs.rakwireless.com/product-categories/wisblock/rak19007/datasheet/)                                                                                                                                                                                                                  | Battery/solar polarity, headers, slot map, charge/input limits and schematic diagrams         |
| [RAK13302 VD datasheet](https://docs.rakwireless.com/product-categories/wisblock/rak13302/datasheet-vd)                                                                                                                                                                                                             | Current fixed power variants, RF/current conditions and schematic; 868 MHz scope caveat above |
| [RAK3401 core guide](https://docs.rakwireless.com/product-categories/wisblock/rak3401/quickstart/) / [datasheet](https://docs.rakwireless.com/product-categories/wisblock/rak3401/datasheet)                                                                                                                        | BSP reuse, interfaces, bootloader layers and module drawings                                  |
| [Base STEP](https://downloads.rakwireless.com/3D_File/WisBlock/3D_RAK19007.stp) / [radio STEP](https://downloads.rakwireless.com/3D_File/WisBlock/3D_RAK13302.stp)                                                                                                                                                  | Manufacturer mechanical files; fit not tested                                                 |
| [Pinned variant](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/rak3401_1watt/variant.h) / [build](https://raw.githubusercontent.com/meshtastic/firmware/d0f4096788545fb3c5e22d2a7e52ac6c268caac1/variants/nrf52840/rak3401_1watt/platformio.ini) | Exact external-radio implementation                                                           |

The store's link labeled “RAK3401 3D” currently resolves to a **RAK4631** STEP filename. It is not treated here as verified exact RAK3401 mechanical evidence. Keep that mismatch separate from the observed RAK19007/RAK13302 models.

### Additional existing resources

* [Manufacturer comparison of power variants](https://forum.rakwireless.com/t/which-wismesh-high-power-booster-starter-kit-fits-your-setup/17605)

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

The kit guide, battery/DC first-step PDFs, current VD and historical VC distinctions, full base/core documentation and exact firmware target were read. The battery first-step assembly diagram and VD battery label were visually inspected. Original additions separate configuration power from booster power, estimate the ideal battery-current lower bound and require actual peer receipts before deployment.

[Manufacturer guides](./). Reviewed 24 November 2026. **Firmware/SDK installation, compilation, flashing, radio/serial operation and hardware tests not run.** Examples and expected results are source-reviewed procedures, not observed bench results.
