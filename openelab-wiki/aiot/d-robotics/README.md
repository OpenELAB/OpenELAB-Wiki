---
description: >-
  Choose D-Robotics X3, X5, S100/S100P and S600 boards, modules, cameras and
  expansion guides, with release-specific development resources and clear
  unlisted-product references.
---

# D-Robotics

D-Robotics RDK platforms combine Linux application processing, BPU acceleration and robotics software. Choose the exact board, module, carrier and release before using a camera, peripheral or model example. This directory separates products currently listed by OpenELAB from manufacturer references whose store listings have not been verified.

## Product range <a href="#product-range" id="product-range"></a>

| Platform                     | Engineering selection                                                                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| RDK X3 and X3 Module         | Bernoulli2 development; standalone-board and carrier/module power requirements differ                                                             |
| RDK X5 and X5 Module         | Bayes BPU development with the model-specific Bayes-E compiler target; distinguish board options from module order codes and carrier requirements |
| RDK S100 / S100P             | Robot-computing kits, camera expansion and MCU interfaces; retain exact image, MCU and runtime pairing                                            |
| RDK S600 and S600 Module     | KS6 kit versus MS6 module integration; kit supply and ports do not define bare-module wiring                                                      |
| Cameras, audio and expansion | Match the specific sensor/adapter, cable, host connector and documentation revision                                                               |
| RDK Ultra                    | Separately labeled archived-document reference; archive status does not prove discontinuation                                                     |

The linked model guides cite the relevant official documents and distinguish source-reviewed procedures from bounded references. Publication does not establish hardware testing, current stock or a qualified custom carrier.

## Popular products and starting points <a href="#popular-products-and-starting-points" id="popular-products-and-starting-points"></a>

Current OpenELAB listings cover **10 SKU/options across four product pages**. Consult each listing for current availability and kit contents:

* [RDK X3 4GB board and kits](https://openelab.io/products/d-robotics-rdk-x3-4gb)
* [RDK X5 4GB / 8GB boards and basic kits](https://openelab.io/products/d-robotics-rdk-x5-development)
* [RDK S100 / S100P robotics kits](https://openelab.io/products/d-robotics-rdk-s100-robotics)
* [RDK S100 Camera Expansion Board](https://openelab.io/products/d-robotics-rdk-s100-camera)

The modules and other peripherals below are manufacturer references. No matching OpenELAB product URL or retailer SKU has been invented for them.

## Popular applications <a href="#popular-applications" id="popular-applications"></a>

* **First boot and system identity:** identify the board, kit option, boot medium, supply and compatible image before installation or recovery.
* **BPU inference:** retain the exact SoC target, compiler/runtime pairing, operators, preprocessing and expected model output.
* **Camera integration:** distinguish CSI versus serialized links, camera power, cable polarity, lane routing, calibration and supported image configurations.
* **Robotics and MCU development:** establish interface ownership, message format, timestamp/frame conventions and read-only checkpoints before controlled equipment is connected.
* **Carrier design:** use the exact module design package. A kit power input, pin count or photograph is insufficient evidence for a custom carrier.

## Wiki product guides and manuals <a href="#wiki-product-guides-and-manuals" id="wiki-product-guides-and-manuals"></a>

### X3 boards, modules and archive <a href="#x3-boards-modules-and-archive" id="x3-boards-modules-and-archive"></a>

* [D-Robotics RDK X3 4GB: Board, Kit Setup and Bernoulli2 Development](rdk-x3-4gb-development-guide.md)
* [D-Robotics RDK X3 Module: Carrier, Boot and Development Reference](rdk-x3-module-hardware-and-development-reference.md)
* [D-Robotics RDK Ultra: Archived Hardware, Bayes APIs and System Identification](rdk-ultra-archived-manufacturer-reference.md)

### X5 boards and modules <a href="#x5-boards-and-modules" id="x5-boards-and-modules"></a>

* [D-Robotics RDK X5: Setup, BPU Inference, Cameras and I/O](rdk-x5.md)
* [D-Robotics RDK X5 Module: carrier, power, boot and AI development reference](rdk-x5-module.md)

### S-series kits and development <a href="#s-series-kits-and-development" id="s-series-kits-and-development"></a>

* [D-Robotics RDK S100/S100P — hardware, image and BPU development](rdk-s100-s100p-engineering-guide.md)
* [RDK S100 MCU1, CANHAL and IPC development reference](rdk-s100-mcu-canhal-ipc-reference.md)
* [D-Robotics RDK S600 — V1P0 hardware and RDKOS 5.1.1 development](rdk-s600-manufacturer-engineering-reference.md)

### S600 module integration <a href="#s600-module-integration" id="s600-module-integration"></a>

* [D-Robotics RDK S600 Module: MS6 Specifications and Carrier Integration Reference](rdk-s600-module.md)

### Vision, inertial and audio peripherals <a href="#vision-inertial-and-audio-peripherals" id="vision-inertial-and-audio-peripherals"></a>

* [D-Robotics RDK X5 Magicbox: Stereo, Voice and Safe Peripheral Setup](rdk-x5-magicbox.md)
* [D-Robotics SC230AI, GS130W and GS130WI Stereo Cameras: Wiring and Capture](rdk-stereo-camera.md)
* [D-Robotics BMI088 IMU Module: X5 Wiring, C/Python and ROS2 Data](rdk-bmi088-imu-module.md)
* [D-Robotics RDK Audio Kit: 4/6-Mic Wiring, USB/I2S and Eight-Channel Capture](rdk-audio-kit.md)

### S100 expansion boards <a href="#s100-expansion-boards" id="s100-expansion-boards"></a>

* [D-Robotics RDK S100 Camera Expansion Board: MIPI/GMSL wiring and first video](rdk-s100-camera-expansion-board.md)
* [D-Robotics RDK S100 MCU Port Expansion Board: pinout, CANHAL and first readback](rdk-s100-mcu-port-expansion-board-reference.md)

### Additional S-series expansion boards <a href="#additional-s-series-expansion-boards" id="additional-s-series-expansion-boards"></a>

* [RDK S100 Camera Expansion Board 12L: PoC, pinout and capture reference](rdk-s100-camera-expansion-board-12l-reference.md)
* [RDK S600 Camera Expansion Board: eight-link GMSL and power reference](rdk-s600-camera-expansion-board-reference.md)
* [RDK S600 MCU Port Expansion Board: CAN ownership and pin reference](rdk-s600-mcu-port-expansion-board-reference.md)

## Manufacturer resources <a href="#manufacturer-resources" id="manufacturer-resources"></a>

* [Current D-Robotics resource center](https://developer.d-robotics.cc/rdk_doc_center/en): select the exact product and release; X-series, S-series, toolchains, Model Zoo and TogetheROS.Bot have separate version scopes.
* [X-series documentation](https://d-robotics.github.io/rdk_x_doc/en/): X3, X5 and their modules; retain each model/version selector.
* [S-series documentation](https://d-robotics.github.io/rdk_s_doc/en/): S100/S100P and S600; use the model-specific download and release pages linked in each guide.
* [Official D-Robotics GitHub organization](https://github.com/D-Robotics): verify the actual repository support table, target, release and license before using an example.
* [OpenELAB D-Robotics collection](https://openelab.io/collections/brands-d-robotics)

### Development and recovery tools <a href="#development-and-recovery-tools" id="development-and-recovery-tools"></a>

| Tool                                                                                                            | Choose by supported task and model                                                                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [RDK Studio hardware support](https://d-robotics.github.io/rdk_studio_doc/en/product-intro/supported-hardware/) | Check its actual connection/feature matrix. Generic SSH access does not establish every RDK-specific feature; X3 Type-C access is not supported.                                                                      |
| [XBurn support and capabilities](https://d-robotics.github.io/xburn_doc/en/overview/)                           | The published matrix names S100, S600, X5 and X5 Module. Region/partition backup differs between S-series and X5; X3 support must not be inferred. Flash only with the exact guide, image and recovery prerequisites. |

Public sources include incomplete or conflicting peripheral electrical details and commercial/FAE-only module design materials. The affected guides name the blocked operations and missing evidence. Original examples have only the validation stated on their individual pages; no SDK execution, flashing, ROS deployment or hardware bench test is implied.
