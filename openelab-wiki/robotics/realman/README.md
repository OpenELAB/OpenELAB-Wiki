---
description: RM and ECO robot arms, WHJ joint modules, grippers, and manuals.
---

# RealMan

{% hint style="info" %}
[**Browse RealMan products on OpenELAB**](https://openelab.io/collections/brands-realman)

Choose the exact model below. Each matched product guide opens with verified `.io` product/SKU links; manufacturer references without a verified catalog match say so explicitly.
{% endhint %}

## Complete manuals inside the wiki

Every page of the ten supplied documents is now available as an original-page view with searchable text: **405 PDF pages in total**. This includes full safety/warranty material, installation procedures, connectors, parameter and dynamics tables, diagrams, protocols, software examples, maintenance and appendices. The engineering entry guides remain linked above; use the complete source readers for details and exact page layout.

| Complete source reader                                                                                             | Pages | Coverage                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------ | ----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RM65 and RM75 hardware manual — all 58 PDF pages](realman-source-library/complete-rm65-rm75-manual.md)            |    58 | Safety, hardware, full parameters, kinematics/dynamics, operation, maintenance and appendices                                                                                                                                                                                                                                                                                                              |
| [RML63 hardware manual — all 48 PDF pages](realman-source-library/complete-rml63-manual.md)                        |    48 | Safety, responsibilities and warranty; Composition, mounting, power, pendant connection and teaching; Controller and tool wiring, I/O, external power and RS485; Parameters, MDH, dynamics, workspace, singularities and load curves; FAQs, handling, maintenance, repair and disposal                                                                                                                     |
| [RX series hardware manual — all 49 PDF pages](realman-source-library/complete-rx-manual.md)                       |    49 | Safety, responsibilities and warranty; Composition, mounting, startup, teaching and shutdown; Controller and tool wiring, I/O, external power and RS485; RX75 parameters, MDH, dynamics, dimensions, workspace and load curves; FAQs, handling, maintenance, repair and disposal                                                                                                                           |
| [ECO series hardware manual — all 56 PDF pages](realman-source-library/complete-eco-manual.md)                     |    56 | Safety, responsibilities and warranty; Composition, mounting, startup, teaching and shutdown; Controller and tool wiring, I/O, external power and RS485; ECO63 specifications, MDH, dynamics, workspace and load curve; ECO65 specifications, MDH, dynamics, workspace and load curve; FAQs, handling, maintenance, repair and disposal                                                                    |
| [ECO62 specification sheet — all 4 PDF pages](realman-source-library/complete-eco62-specification.md)              |     4 | Composite flyer; Product overview; Complete arm/controller specification table; Application panels                                                                                                                                                                                                                                                                                                         |
| [GEN62 specification sheet — all 3 PDF pages](realman-source-library/complete-gen62-specification.md)              |     3 | Product overview; Complete arm/controller specification table; Application panels                                                                                                                                                                                                                                                                                                                          |
| [RMG22-65 parallel gripper manual V1.3 — all 53 PDF pages](realman-source-library/complete-rmg22-65-manual.md)     |    53 | Safety, revisions and contents; Product specifications and packing list; Mechanical/electrical installation and serial configuration; Host software controls, status, calibration and firmware; Modbus coil and holding registers; RS485 framing, checksum and command catalogue; Every proprietary command, request and response example, I/O and support                                                 |
| [RealBot-S2 user manual — all 38 PDF pages](realman-source-library/complete-s2-user-manual.md)                     |    38 | Cover, revision and original contents; Features, architecture, full-unit/arm/computer/camera specifications; Mechanical dimensions, controls, charging, emergency stop and interfaces; Local networking, SSH, Wi-Fi and wired networking; Android/desktop teach pendant and operating controls; Arm connection and six-axis force calibration; Safety, transport, storage, unpacking and further resources |
| [RealBot2.0 / S2 interface manual V1.3 — all 70 PDF pages](realman-source-library/complete-s2-interface-manual.md) |    70 | All 17 chapters, complete schemas/fields, every interface example, safety and appendices A/B                                                                                                                                                                                                                                                                                                               |
| [RealBot-L2 solution white paper V2+ — all 26 PDF pages](realman-source-library/complete-l2-white-paper.md)        |    26 | Positioning, applications and value propositions; Architecture, modules and complete technical specification tables; Perception, computing, teleoperation software and hardware; Application scenarios, equipment list, deployment and service                                                                                                                                                             |

**How to read revisions:** RM65/RM75 share one family source; ECO63/ECO65 share another. ECO62 and GEN62 are specification sheets, not substitutes for those operating manuals. S2 has a separate hardware manual and V1.3 software contract. L2 is a separate V2+ solution white paper, not an RMC-DA-LIII or S2 manual. The original legacy wiki pages and PDF downloads are retained.

**Original-page versus text view:** original images preserve complete tables, connector orientations and drawings. Extracted text is searchable but can retain native PDF reading-order/character defects. The ECO62/GEN62 sheets have visually checked transcriptions. Discrepancy notes accompany the applicable manual; supplied values have not been silently reconciled.

## Choose your robot or component

RealMan documentation covers complete robots, standalone arms, joints, tools and software. Match the model, controller generation, end-effector and delivery revision before following a procedure. The existing RM65, ECO65, teaching-pendant, joint and RMC-DA-LIII URLs remain canonical.

| Existing canonical guide                                                            | Scope                                                                              |
| ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| [RM65 series](realman-rm65-series-user-manual-v1.2.0.md)                            | RM65-B, RM65-6F and RM65-B-V; revised source comparison and retained V1.2.0 manual |
| [ECO65 series](realman-eco65-series-user-manual-v1.2.0.md)                          | ECO65-B/6F; explicit older/newer brake distinction and retained manual             |
| [RMC-DA-LIII lifting platform](embodied-double-arm-lifting-platform-user-manual.md) | Existing platform, distinct from S2/L2                                             |
| [WEB teaching pendant V1.5](realman-robot-web-teaching-pendant-user-manual-v1.5.md) | Shared historical UI reference; use exact-model commissioning first                |
| [WHJ joint modules](realman-whj-series-joint-module-user-manual.md)                 | Full model-code/option matching; independent joint electrical documentation        |

## Model-specific guides and development

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

## Keep the platform differences explicit

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

## Sources and first results

[Ten supplied PDF sources and revision notes](realman-source-library/) provides original PDF page-range references. Begin with identity/status reading, not a movement demo. Specification-only/solution-white-paper guides explicitly stop at de-energized document acceptance where an installation or SDK contract is missing.

Sources reviewed 22 November 2026. No SDK compilation, robot communication or physical tests were performed. Source review and publication do not constitute hardware commissioning or system-level safety certification.

[Explore Robotics](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)
