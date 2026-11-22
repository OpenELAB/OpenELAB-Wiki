# Agile Robots and Franka: product and development directory

{% hint style="info" %}
[**View Diana 7 on OpenELAB**](https://openelab.io/products/franka-diana-7-agile-robots-7-axis-robotic-arm)

**Model:** Diana 7 · **SKU:** `Franka-Diana7` · **Scope:** Agile Robots industrial arm; separate controller/software route from Franka FR3
{% endhint %}

## Choose the exact product

Agile Robots and Franka are integrated here through canonical product guides and reciprocal links. **AgileX is a separate manufacturer.** The existing Franka URLs, files and model-specific pages remain the canonical FR3 references.

| Product guide               | Exact scope                                                       |
| --------------------------- | ----------------------------------------------------------------- |
| [Diana 3](diana-3.md)       | 7 axes, 3 kg, 772 mm; CB-FS-0.3KW                                 |
| [Diana 7](diana-7.md)       | 7 axes, 7 kg, 923 mm; store SKU Franka-Diana7, CB-FS-0.6KW        |
| [Thor 3](thor-3.md)         | 6 axes, 3 kg, 600 mm; RCB 200–240 V AC                            |
| [Thor 7](thor-7.md)         | 6 axes, 7 kg, 900 mm; distinct from Pro                           |
| [Thor 7 Pro](thor-7-pro.md) | 6 axes, force-controlled 7 kg variant; brochure/manual boundaries |
| [Thor 12](thor-12.md)       | 6 axes, 12 kg, 1,300 mm                                           |
| [Thor 20](thor-20.md)       | 6 axes, 20 kg, 1,700 mm; six M10 base/six M6 tool holes           |
| [Agile Hand](agile-hand.md) | Five fingers, 16 DoF/21 joints; distinct from Franka Hand         |
| [H10-W](h10-w.md)           | Wheeled humanoid; supplied and public configuration differences   |
| [H20](h20.md)               | Bipedal humanoid specification reference                          |

Except Diana 7, no separate exact OpenELAB SKU/product match for these Agile Robots products was verified. Their pages are manufacturer-document references and identify missing powered-setup/SDK evidence where applicable. No substitute listing is asserted.

## Existing Franka research series

| Canonical guide                                    | Scope                                                          |
| -------------------------------------------------- | -------------------------------------------------------------- |
| [Franka Research 3 Arm v2.1](../franka/fr3-arm.md) | Standalone FR3 Arm/Control hardware and first UI connection    |
| [Franka Hand](../franka/franka-hand.md)            | Separate two-finger gripper and power-loss/tool limits         |
| [FR3 Duo](../franka/fr3-duo.md)                    | Stationary bimanual research configuration                     |
| [Mobile FR3 Duo](../franka/mobile-fr3-duo.md)      | Mobile prototype and exact Vision/Manipulation Kit scope       |
| [Tactile Mobile Robot](../franka/tmr.md)           | TMR base revision boundaries                                   |
| [Franka GELLO Duo](../franka/gello-duo.md)         | Leader hardware, serial mapping and follower-motion boundaries |

[Open the Franka research hub](../franka/) · [Franka training/development](../franka/development/). The seven repeated Franka PDFs in this batch are identical to the previously reviewed files; their source downloads are reused.

## Controllers and development

[CB-FS-3.2T controller family](cb-fs-controller.md) · [RCB2.1.1T-0.3KW controller](rcb-controller.md) · [Six training topics and development workflows](development/)

Use the exact software route: external Industrial API, embedded Python/Lua, specific Diana FS FCI or Franka FR3 FCI. Do not transfer mains ranges, tool connector pins, control vectors or units between models.

## Sources and validation

[Source library and revision map](source-library.md): all 34 supplied files reviewed, with seven Franka PDF duplicates reused, internal H10-W/H20 specifications summarized without distributing those files, and current official product/brochure sources checked.

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.

[Robotics directory](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)
