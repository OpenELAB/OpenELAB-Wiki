---
description: RM and ECO robot arms, WHJ joint modules, grippers, and manuals.
---

# RealMan

{% hint style="info" %}
[**Browse RealMan products on OpenELAB**](https://openelab.io/collections/brands-realman)

Choose the exact model below. Each matched product guide opens with verified `.io` product/SKU links; manufacturer references without a verified catalog match say so explicitly.
{% endhint %}

### Choose your robot or component

RealMan documentation covers complete robots, standalone arms, joints, tools and software. Match the model, controller generation, end-effector and delivery revision before following a procedure. The existing RM65, ECO65, teaching-pendant, joint and RMC-DA-LIII URLs remain canonical.

| Existing canonical guide                                                            | Scope                                                                              |
| ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| [RM65 series](realman-rm65-series-user-manual-v1.2.0.md)                            | RM65-B, RM65-6F and RM65-B-V; revised source comparison and retained V1.2.0 manual |
| [ECO65 series](realman-eco65-series-user-manual-v1.2.0.md)                          | ECO65-B/6F; explicit older/newer brake distinction and retained manual             |
| [RMC-DA-LIII lifting platform](embodied-double-arm-lifting-platform-user-manual.md) | Existing platform, distinct from S2/L2                                             |
| [WEB teaching pendant V1.5](realman-robot-web-teaching-pendant-user-manual-v1.5.md) | Shared historical UI reference; use exact-model commissioning first                |
| [WHJ joint modules](realman-whj-series-joint-module-user-manual.md)                 | Full model-code/option matching; independent joint electrical documentation        |

### Model-specific guides and development

* [RealMan RM75: seven-axis arm reference](realman-rm75-reference.md)
* [RealMan RML63: long-reach six-axis arm reference](realman-rml63-reference.md)
* [RealMan RX75: force and vision arm reference](realman-rx75-reference.md)
* [RealMan ECO63: collaborative arm reference](realman-eco63-reference.md)
* [RealMan ECO62: compact embedded arm reference](realman-eco62-reference.md)
* [RealMan GEN62: desktop arm reference](realman-gen62-reference.md)
* [RealMan RMG22-65: parallel gripper commissioning](realman-rmg22-65-gripper.md)
* [RealBot-S2: wheeled folding robot guide](realbot-s2-guide.md)
* [RealBot-L2: platform and teleoperation reference](realbot-l2-guide.md)
* [RealMan arms: commissioning and SDK selection](realman-arm-commissioning-and-sdk.md)
* [RealBot-S2: development and interface guide](realbot-s2-development/)

### Keep the platform differences explicit

| Model/family          | Key distinction                                                                                        |
| --------------------- | ------------------------------------------------------------------------------------------------------ |
| S2                    | Four-wheel steering/drive, 4 body joints and 2 head joints; S2-specific SDK                            |
| L2                    | Differential-drive base, independent lift column, 1 head and 1 waist pitch axis; white-paper reference |
| RMC-DA-LIII           | Existing dual-arm lift platform; separate delivered hardware/software                                  |
| RM65 / RM75           | Six versus seven axes; separate joint/brake/software models                                            |
| ECO62 / ECO63 / ECO65 | Compact 2 kg / long-reach 3 kg / 5 kg families                                                         |
| RML63                 | 3 kg long-reach humanoid family; not ECO63 brake behavior                                              |
| RX75 / RX75S          | Different geometry and system integration; S2 uses RX75S                                               |
| GEN62 / GEN72         | Different models; GEN72 in a driver list does not establish GEN62 support                              |
| RMG22-65 / L2 tool    | 65 mm gripper versus white-paper 90 mm option; different power/protocol evidence                       |

### Sources and first results

[Ten supplied PDF sources and revision notes](realman-source-library.md) provides original PDF page-range references. Begin with identity/status reading, not a movement demo. Specification-only/solution-white-paper guides explicitly stop at de-energized document acceptance where an installation or SDK contract is missing.

Sources reviewed 22 November 2026. No SDK compilation, robot communication or physical tests were performed. Source review and publication do not constitute hardware commissioning or system-level safety certification.

[Explore Robotics](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)
