# Franka (Agile Robots): research robot wiki series

{% hint style="info" %}
[**View Franka Research 3 on OpenELAB**](https://openelab.io/products/franka-research-fr3-force-sensitive-robotic-arm)

[**View the Mobile FR3 Duo kit on OpenELAB**](https://openelab.io/products/franka-mobile-fr3-duo-vision-manipulation-kit)

Choose the exact robot, tool and hardware/software revision below. Franka belongs to the Agile Robots group; **AgileX is a separate manufacturer**.
{% endhint %}

## Complete documents and training inside the wiki

This library now contains **174 public PDF pages and 43 training slides** from **10 distinct supplied sources**, with complete original-page views and native searchable text. Longer references are divided into numbered reading sections without omitting any original page. Full safety, declarations, installation, interface/parameter tables, diagrams, examples, maintenance, troubleshooting and appendices are retained.

| Complete in-wiki source                                                          | Coverage      |
| -------------------------------------------------------------------------------- | ------------- |
| [TMR brochure](source-library/complete-tmr.md)                                   | 2 PDF pages   |
| [Franka Hand manual R50010/1.2](source-library/complete-hand.md)                 | 36 PDF pages  |
| [Franka GELLO Duo brochure](source-library/complete-gello.md)                    | 1 PDF pages   |
| [Franka Research 3 brochure](source-library/complete-fr3-brochure.md)            | 13 PDF pages  |
| [Mobile FR3 Duo brochure](source-library/complete-mobile.md)                     | 2 PDF pages   |
| [FR3 Arm v2.1 hardware manual R02210/1.2](source-library/complete-fr3-hardware/) | 118 PDF pages |
| [FR3 Duo brochure](source-library/complete-duo.md)                               | 2 PDF pages   |
| [Franka training 1 — System Startup](source-library/complete-startup.md)         | 14 slides     |
| [Franka training 2 — Franka Desk](source-library/complete-desk.md)               | 21 slides     |
| [Franka training 3 — Franka World](source-library/complete-world.md)             | 8 slides      |

The seven PDF copies repeated in the Agile Robots upload are byte-identical and use these same canonical readers. Later official editions remain separately linked and are not silently merged into the supplied revisions.

**How to use the readers:** original images preserve layout, columns, figures and connector orientation. Text is native extraction and can retain PDF reading-order or presentation formatting defects. Historical training mistakes and source-specific conflicts are preserved with explicit notes; they are not silently converted into new control instructions. These source readers complement the model and workflow guides above.

## Products and exact scope

This series combines the seven supplied PDF brochures/manuals and three October 2025 training decks with current manufacturer operating, compatibility and development sources. Use product-specific specifications and procedures rather than one generic seven-axis-arm workflow.

| Guide                                    | Scope                                                                                  |
| ---------------------------------------- | -------------------------------------------------------------------------------------- |
| [Franka Research 3 Arm v2.1](fr3-arm.md) | Arm/Control hardware, mounting and first UI connection; current store SKU `Franka-FR3` |
| [Franka Hand](franka-hand.md)            | R50010/1.2 parallel gripper; mounting, power-off behavior and control limits           |
| [FR3 Duo](fr3-duo.md)                    | Stationary bimanual prototype, two separately identified FR3 arms                      |
| [Mobile FR3 Duo](mobile-fr3-duo.md)      | TMR + dual-arm prototype; OpenELAB Vision & Manipulation Kit SKU `Franka-MFR3D`        |
| [Tactile Mobile Robot](tmr.md)           | Mobile-base brochure and prototype revision boundaries                                 |
| [Franka GELLO Duo](gello-duo.md)         | Leader hardware, serial mapping and safe pre-synchronization checks                    |

## Training and development

[Start the training/development sequence](development/): startup → Desk/Settings/Watchman → World/registration → FCI/ROS 2 → simulation and data acceptance. Each tutorial names a first result and separates inspection from operations that can enable or move the robot.

## Read the version notes first

* **Hardware versus operating manual:** Arm v2.1 instructions and the installed System Image's operating manual are separate documents.
* **UI versus FCI:** arm X5 serves initial browser access; Control C2 is the FCI workstation path.
* **Hand versus arm loop:** a 1 kHz arm FCI statement does not promise real-time Franka Hand control.
* **Prototype revisions:** brochure and v0.2 manual payload/speed/dimensions/camera counts differ. Use the delivered technical agreement and manuals.
* **Duo counts:** two seven-axis arms have 14 arm joints. Brochure total-DOF figures may include other mechanisms; use the actual delivered joint list.
* **Separate products:** OpenELAB also lists Diana 7 under its Franka collection. Its manufacturer/controller platform is Agile Robots; the expanded Diana guides cover its own hardware, Industrial software and specific FS FCI adaptation. FR3 procedures are not reused as Diana commissioning instructions.

## Sources and validation

[Source library and document/revision map](source-library/) includes the seven PDF originals as hosted reading parts, slide-numbered reading copies of all three training decks, and current official source links. Manufacturer-reference guides without a verified separate store match say so explicitly.

Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**. Published documentation does not constitute physical commissioning or safety acceptance of a robot/workcell.

[Robotics directory](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)

Related Agile Robots coverage: [Diana 7](../agile-robots/diana-7.md) · [Diana FS FCI](../agile-robots/development/diana-fci.md) · [combined Agile Robots / Franka directory](../agile-robots/).
