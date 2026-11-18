# CubeMars AKH70-48 V1.0 KV41 Engineering Guide

{% hint style="info" %}
[**View CubeMars AKH70-48 V1.0 KV41 on OpenELAB**](https://openelab.io/products/cubemars-akh70-48-kv41)

**Product/option:** CubeMars AKH70-48 V1.0 KV41 · **Workbook SKU:** `CubeMars-AKH70-48-KV41`
{% endhint %}

[CubeMars-AKH70-48-KV41](https://openelab.io/products/cubemars-akh70-48-kv41)

## Product and scope

**AKH70-48 V1.0 KV41** is a hollow-shaft integrated actuator for articulated robots and other high-torque joints. It is distinct from AK70-10, AK80-64 and other AK/AKH revisions.

## Hardware and technical documents

| Item                   | Reference                                            |
| ---------------------- | ---------------------------------------------------- |
| Nominal supply / ratio | 48V / 48:1                                           |
| Rated / peak torque    | 74Nm / 222Nm in the cited product specification      |
| Rated / no-load speed  | 28rpm / 35rpm                                        |
| Feedback               | Two 21-bit magnetic encoders                         |
| Mass                   | 1396g                                                |
| Interfaces             | CAN power/data connector and separate UART connector |

The exact product page provides the **technical drawing, performance curves, wiring pack and support/download links**. Distinguish motor-side torque constant from output torque scaling. Mounting and hollow-shaft cable routing must allow the full intended motion.

## Getting started

1. Fixture the unloaded actuator, record revision/firmware and inspect connector polarity.
2. Use the documented supply and matching CubeMars setup interface.
3. Read firmware, encoder feedback and error status before enabling the motor.
4. Select the exact actuator and control mode, preserving current, speed and position limits.
5. Run a small low-speed movement and verify disable/stop before applying a mechanism or payload.

**Expected checkpoint:** correct model/status and bounded, predictable output motion.

## Development software and recovery

Use the **October 2026 AK-series V3 driver software manual** only where its supported-model table covers this AKH70-48 configuration. MIT-style packing, servo modes and torque/current definitions differ. Preserve parameters and zero reference before firmware changes; use the documented recovery procedure.

## FAQs

**Can a generic AK70 torque constant be used?** No; use this model's mode-specific units and output scaling.

**Can peak torque be held continuously?** Observe the rated, thermal and duty-cycle limits.

**A packet produces unexpected motion?** Disable and check model selection, units, scaling and control mode.

## Sources and validation

* [Exact specifications, drawing and downloads](https://www.cubemars.com/product/akh70-48-v-1-0-kv41-hollow-shaft-planetary-actuator.html)
* [Manufacturer driver manual](https://www.cubemars.com/data/cms/202610/ak-series-motor-module-v3-driver-software-user-manual-en.pdf)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
