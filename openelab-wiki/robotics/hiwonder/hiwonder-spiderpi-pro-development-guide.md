# Hiwonder SpiderPi Pro Engineering Guide

[Hiwonder-21060060](https://openelab.io/products/spiderpi-pro-pi5) · [Hiwonder-21060050](https://openelab.io/products/spiderpi-pro-pi5)

### Product and scope

This page covers **SpiderPi Pro**, including OpenELAB **21060060 / 21060050** package rows. Inspect Raspberry Pi generation, included accessories and power equipment against the order. The non-Pro SpiderPi does not include the same manipulation scope.

### Hardware and technical documents

| Item                        | Reference                                                    |
| --------------------------- | ------------------------------------------------------------ |
| Legs                        | Six legs, three DoF per leg                                  |
| Arm                         | Five-DoF vision arm                                          |
| Host                        | Raspberry Pi 4B/5 package options                            |
| Published battery reference | 11.1V, 3500mAh LiPo for the cited manufacturer configuration |
| Communications              | Wi-Fi and Ethernet                                           |
| Approximate body mass       | 3.1kg in the cited configuration                             |

The manufacturer page supplies a **dimensional diagram, kit packing list** and official documentation links. Use those resources to verify the specific package, servo types, charging equipment and physical assembly.

### Getting started

1. Check mechanical fasteners and servo connections with power off. Support the chassis above the bench for first tests.
2. Use the supplied image matched to the Raspberry Pi generation; avoid replacing it with an arbitrary desktop image.
3. Connect through the official app/remote-access instructions and save the existing action/calibration data.
4. Run a documented neutral-posture test before walking. Keep the arm clear and begin without an object.
5. Test a simple vision display, then a small arm action; combine walking and manipulation only after independent checks.

**Expected checkpoint:** stable neutral posture, a working camera and predictable low-speed action playback.

### Development software and recovery

Official examples cover gait, OpenCV vision and arm coordination. Use **Hiwonder/SpiderPi-Pro** with the matching image and document the versions. For recovery, restore the correct image and preserve device-specific calibration. ROSpider launch files are not a drop-in SpiderPi Pro software stack.

### FAQs

**Why are there two order codes?** They represent package/configuration rows; confirm included controller and accessories rather than assuming equal contents.

**A joint twitches?** Inspect supply sag, connectors, IDs and calibration before increasing gains.

**Can I apply another robot's battery?** Match voltage, connector polarity and the specified charger exactly.

### Sources and validation

* [Model specifications and drawings](https://www.hiwonder.com/products/spiderpi-pro)
* [Official tutorials and hardware resources](https://docs.hiwonder.com/projects/SpiderPi_Pro/en/latest/)
* [Software repository](https://github.com/Hiwonder/SpiderPi-Pro)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
