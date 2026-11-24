---
description: >-
  MyActuator RMD-X V4 engineering guides: exact P20 E models, wiring, CAN V4.4
  commands, EtherCAT objects and PDOs, SDK differences, feedback and
  commissioning.
---

# MyActuator

MyActuator develops integrated servo actuators and motor-control hardware for robotics. Its RMD products combine compact motors with drive electronics and, depending on the family, a reduction gearbox for joint and motion-control applications.

[Browse MyActuator products on OpenELAB](https://openelab.io/collections/brands-myactuator)

### Popular product guides

Products in the OpenELAB Top200 net-sales snapshot for 17 August–17 November 2026, ordered by their original sales rank. Shared model-family guides appear once; match the exact model, SKU and purchased option. This dated sales order is separate from manufacturer website-traffic ranking.

| Product guide                                                                                           | Models / order codes                                     |
| ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| [MyActuator RMD-X12-P20-320-E Development Guide](rmd-x12-p20-320-e-development-guide.md)                | MyActuator-RMD-X12-P20-320-E                             |
| [MyActuator RMD-X6-P20 and RMD-X8-P20 Engineering Guide](myactuator-rmd-x6-x8-p20-development-guide.md) | MyActuator-RMD-X6-P20-60-E · MyActuator-RMD-X8-P20-120-E |

### Product guide directory

Choose the complete model and purchased option. The directory covers the 12 MyActuator product listings on OpenELAB IO reviewed on 19 November 2026. Accessory-only options in a motor listing are not additional motors.

| Product / model              | Guide                                                                                                   | OpenELAB product                                                                                            |
| ---------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| RMD-L-7015 CAN               | [Development guide](rmd-l-7015-can-development-guide.md)                                                | [MyActuator-RMD-L-7015-CAN](https://openelab.io/products/myactuator-rmd-l-7015-23t-can)                     |
| RMD-X2-P28-7-E               | [Development guide](rmd-x2-p28-7-e-development-guide.md)                                                | [MyActuator-RMD-X2-P28-7-E](https://openelab.io/products/myactuator-rmd-x2-p28-actuator)                    |
| RMD-X4-P12-10-E              | [Development guide](rmd-x4-p12-10-e-development-guide.md)                                               | [MyActuator-RMD-X4-P12-10-E](https://openelab.io/products/myactuator-rmd-x4-p12-actuator)                   |
| RMD-X4-P36-36-E              | [Development guide](rmd-x4-p36-36-e-development-guide.md)                                               | [MyActuator-RMD-X4-P36-36-E](https://openelab.io/products/myactuator-rmd-x4-p36-actuator)                   |
| RMD-X4-P36-36-E-L            | [Development guide](rmd-x4-p36-36-e-l-development-guide.md)                                             | [MyActuator-RMD-X4-P36-36-E-L](https://openelab.io/products/myactuator-rmd-x4-p36-36-e-l)                   |
| RMD-X6-P20-60-E              | [MyActuator RMD-X6-P20 and RMD-X8-P20 Engineering Guide](myactuator-rmd-x6-x8-p20-development-guide.md) | [MyActuator-RMD-X6-P20-60-E](https://openelab.io/products/myactuator-rmd-x6-p20-actuator)                   |
| RMD-X8-P20-120-E             | [MyActuator RMD-X8-P20-120-E Development Guide](rmd-x8-p20-120-e-development-guide.md)                  | [MyActuator-RMD-X8-P20-120-E](https://openelab.io/products/myactuator-rmd-x8-p20-actuator)                  |
| RMD-X12-P20-320-E            | [MyActuator RMD-X12-P20-320-E Development Guide](rmd-x12-p20-320-e-development-guide.md)                | [MyActuator-RMD-X12-P20-320-E](https://openelab.io/products/myactuator-rmd-x12-p20-actuator)                |
| RMD-X15-P20-450-E            | [Development guide](rmd-x15-p20-450-e-development-guide.md)                                             | [MyActuator-RMD-X15-P20-450-E](https://openelab.io/products/myactuator-rmd-x15-p20-actuator)                |
| EPS-RH-25-100-E — N-D / B-D  | [Development guide](eps-rh-25-100-e-development-guide.md)                                               | [MyActuator-EPS-RH-25-100-E-N-D / B-D](https://openelab.io/products/myactuator-epsrh25-100e-servo-actuator) |
| USB-CAN Communication Module | [Connection guide](usb-can-communication-module-guide.md)                                               | [MyActuator-USB-CAN](https://openelab.io/products/myactuator-usb-can-motor-converter)                       |
| RJ45 Adapter Plate V1.0      | [Connection guide](rj45-adapter-plate-v1-0-guide.md)                                                    | [MyActuator-RJ45-Adapter](https://openelab.io/products/myactuator-rj45-servo-network-adapter)               |

**Variant notes:** X4-P12-10-E has an actual 12.5:1 reduction. Standard X4-P36-36-E and X4-P36-36-E-L have separate guides and different peak/stall limits. RH-25's guide compares brake and no-brake versions. USB-CAN and RJ45 are communication accessories; choose the appropriate guide for CAN or EtherCAT.

### RMD-X V4 E actuator development

The three expanded RMD-X6-P20-60-E, RMD-X8-P20-120-E and RMD-X12-P20-320-E guides combine exact-model specifications and drawings with a shared V4 reference: installation, power and encoder state; all 36 ordinary-CAN commands; packed control modes; the EtherCAT PDF dictionary and additional ESI objects; eight PDO layouts; and seven operating modes.

Start with the model-specific status-only feedback procedure. The guides distinguish peak from continuous ratings, output from motor-side units, persistent writes from runtime settings, and the current protocol from older SDK parsers. PDF/ESI disagreements, unresolved firmware contracts and untested hardware procedures are identified beside the relevant tables.

### Product range

* RMD-X planetary robot actuators
* RMD-L direct-drive servo motors
* EPS-RH harmonic actuators, including brake/no-brake options
* CAN communication adapters and actuator integration accessories

### Product families and examples

| Product           | Typical use                              | Links                                                                            |
| ----------------- | ---------------------------------------- | -------------------------------------------------------------------------------- |
| RMD-L-7015        | Direct-drive servo experiments           | [OpenELAB product](https://openelab.io/products/myactuator-rmd-l-7015-23t-can)   |
| RMD-X4-P36-36-E   | Compact geared robot joints              | [OpenELAB product](https://openelab.io/products/myactuator-rmd-x4-p36-actuator)  |
| RMD-X8-P20-120-E  | Higher-torque articulated mechanisms     | [OpenELAB product](https://openelab.io/products/myactuator-rmd-x8-p20-actuator)  |
| RMD-X12-P20-320-E | Large joint and load-handling prototypes | [OpenELAB product](https://openelab.io/products/myactuator-rmd-x12-p20-actuator) |

### Popular applications

* Build robot-arm, quadruped, and humanoid joints.
* Prototype direct-drive motion axes and rotary mechanisms.
* Integrate networked servo drives into research and automation systems.

### Manufacturer resources

* [MyActuator technical downloads](https://www.myactuator.com/downloads-xseries)

[Explore Robotics documentation](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)
