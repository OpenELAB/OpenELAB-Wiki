# M5Stack Cap CC1101 and NFC U219 Development Guide

{% hint style="info" %}
[**View M5Stack Cap CC1101 and NFC U219 on OpenELAB**](https://openelab.io/products/m5stack-cap-cc1101-nfc-for-cardputer-adv)

**Product model/family:** M5Stack Cap CC1101 and NFC U219 · **OpenELAB SKU:** `M5-U219`
{% endhint %}

[Product at OpenELAB](https://openelab.io/products/m5stack-cap-cc1101-nfc-for-cardputer-adv)

## Product and interfaces

**U219 Cap CC1101** adds sub-GHz RF and NFC to **Cardputer-Adv / CardputerZero**. It is a different accessory from the SX1262 LoRa cap.

| Function         | Hardware                                                             |
| ---------------- | -------------------------------------------------------------------- |
| Sub-GHz radio    | TI CC1101                                                            |
| Matched RF bands | 315 / 433 / 868 / 915MHz paths                                       |
| Modulations      | 2-FSK, 4-FSK, GFSK, MSK, ASK and OOK                                 |
| NFC front end    | ST25R3916                                                            |
| NFC protocols    | ISO14443A/B, FeliCa and ISO15693; supported modes depend on software |
| Host bus         | SPI; separate control/chip-select signals                            |
| RF connector     | RP-SMA                                                               |

Use it for your own wireless-device prototypes and NFC tag interfaces. Select a permitted RF band and compatible antenna for the deployment region.

## Getting started: NFC tag detection

1. Power off the Cardputer host and attach the cap correctly.
2. Prepare the manufacturer's Cardputer-Adv development environment.
3. Install **M5Unit-NFC** and dependencies, select the **CapCC1101NFC** target, and build the official detection example.
4. Upload and place a supported test tag near the sensing area. Use the example's documented keyboard action.
5. Confirm tag detection before attempting writing or emulation.

**Checkpoint:** the example identifies your test tag repeatedly. Preserve the example and dependency versions as a baseline.

## Development resources

The U219 page contains the **pin map, schematic and dimensional links**. Check SPI bus sharing, NFC IRQ and separate chip selects before adding other accessories. The official library includes target-dependent functionality; a generic NFC example can initialize a different chip or bus.

Treat the CC1101 and NFC paths as separate bring-up tasks. For RF, begin with the official configuration for a known band and your own compatible transmitter/receiver; attach the correct antenna before transmission.

## FAQs and recovery

**Does CC1101 provide LoRa?** It is a different radio from the LoRa-cap SX1262; match protocol and modulation explicitly.

**No NFC response?** Confirm the cap target, host board, tag standard, sensing position and SPI wiring.

**Will every NFC mode work on every tag?** Protocol support does not imply permission or technical ability to modify arbitrary tags. Start with a writable test tag you control.

**Firmware no longer boots?** Remove the cap, recover the host using its documented download procedure, then restore the known-working example.

## Sources and validation

* [U219 hardware, pin map and technical resources](https://docs.m5stack.com/en/cap/Cap_CC1101)
* [Official Arduino NFC examples](https://docs.m5stack.com/en/arduino/projects/cap/cap_cc1101)
* [Official NFC library and supported targets](https://github.com/m5stack/M5Unit-NFC)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [Cap CC1101](https://docs.m5stack.com/en/cap/Cap_CC1101) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U219`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1250/SCH_Cap_CC1101_SCH_V0.3_20260528.pdf) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/cap/cap_cc1101)                        |
| Official source: M5Unit-NFC  | [Read official source: m5unit-nfc](https://github.com/m5stack/M5Unit-NFC)                                               |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
