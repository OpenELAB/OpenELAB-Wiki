---
description: >-
  Controller guide for the DOBOT DSC collaborative robot controller, covering
  safety, interfaces, installation, wiring, functional safety, and applicable
  standards.
---

# DOBOT DSC Controller User Guide

## DOBOT DSC Collaborative Robot Teach Pendant Controller

{% embed url="https://openelab.io/products/dobot-dsc-teach-pendant-nova-controller" %}

## Contents

* Preface
* 1\. Safety
* 2\. Product Introduction
* 3\. Mechanical Specifications
* 4\. Electrical Characteristics
* 5\. Installation and Use
* 6\. Warranty
* Appendix A Technical Specifications
* Appendix B Functional Safety
* Appendix C Applicable Standards

Copyright © SHENZHEN DOBOT CORP LTD 2026. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "DOBOT"). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. DOBOT makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will DOBOT be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. DOBOT shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

### SHENZHEN DOBOT CORP LTD

Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

### DOBOT Europe GmbH

Address: Waldeckerstraße 11,64546 Mörfelden-Walldorf Contact: Lang Xulin, lang@dobot-robots.com

## Preface

### Purpose

This document describes the functions, technical specifications, installation guide of Dobot DSC controller, making it easy for users to fully understand and use it.

### Scope of application

* DOBOT DSC

You can find the information of the controller on its nameplate.

### Compatibility specifications

Controller model DOBOT DSC Controller version V4.6.7.0 and above CRA series Compatible robot arm Nova series Compatible software & DobotStudio Pro V4.6.7.0-stable and above version

### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

![Official manual figure, page 3](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgYK0eJ9H4wcnMY7JUJ2Z%2Fdsc-p003-img01.png?alt=media)

### Related documents

Document Description Download link DobotStudio Pro User Explains how to use the robot control Guide software, DobotStudio Pro. Describes how to use the secondary development interface based on DOBOT TCP\_IP Remote TCP/IP protocol. In addition to the Control Interface Guide document, you can also access multi- language development DEMOs from Github. DOBOT Bus Introduces the usage of the robot's Communication Protocol bus communication functions Visit the Download Guide (EtherNetIP/Profinet). Center to search by (EtherNetIP\_Profinet) document name or filter by product Explains how to use the Teach DOBOT Cobot Teach series. Pendant that accompanies the Pendant User Guide collaborative robot. Describes the functions, technical DOBOT CRA Series specifications, installation guides of Hardware User Guide the DOBOT CRA series collaborative robots. Describes the functions, technical DOBOT Nova Series specifications, installation guides of Hardware User Guide the DOBOT Nova series collaborative robots.

### Revision history

Date Version Revision history 2026/09/03 V1.3 Added step for Cable connection to the DSC controller. 2026/07/31 V1.2 Change the weight of the DSC. Added descriptions regarding functional safety and applicable 2026/06/23 V1.1 standards. 2026/05/06 V1.0 The first release

### Symbol conventions

The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could

**DANGER**

result in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot arm damage. Indicates a potentially hazardous situation which, if not avoided, could

**NOTICE**

result in robot arm damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement important

**NOTE**

points in the main text.

## 1. Safety

### 1.1 Safety statement

Prior to use, please read and adhere to the safety precautions outlined in the respective robot arm user guide.

### 1.2 Safety warning sign

The following safety warning signs may appear on the product, and their meanings are as follows: Symbol Description Indicates a hazard with a high level of risk which, if not

**DANGER**

avoided, could result in death or serious injury. Indicates a potentially dangerous electrical situation that, if ELECTRICITY not avoided, could result in injury, death, or serious damage to the equipment. HOT May cause dangerous hot surface, if touched, may cause personal injury. Indicates a hazard with a medium level or low level of risk

**WARNING which, if not avoided, could result in minor or moderate injury,**

robot arm damage. Indicates a potentially hazardous situation which, if not

**NOTICE avoided, could result in robot arm damage, data loss, or**

unanticipated result. Indicates a situation that, if not avoided, could result in personnel injury or damage to the equipment. CAUTION For items marked with such signs, depending on the specific situation, there is sometimes a possibility of significant consequences

## 2. Product Introduction

The DOBOT DSC is used to control the DOBOT CRA and Nova series robot arms. Nova series robots are equipped with DOBOT DSC. For its installation and use, refer to DOBOT Nova Series (Compatible with DSC) Hardware User Guide. CRA Series robots can also be equipped with DOBOT DSC. When the installation space for CRA Series robots is limited (e.g. when it is used with AGV), you can use the DOBOT DSC with CRA Series robots in reference to this document. The controller's appearance is shown in the figure below. For detailed definitions of its electrical interfaces, please refer to the Electrical Characteristics section.

_Figure 2.1 DSC controller_

After connecting to the external power supply and the robot arm, briefly press and release the controller power button. The controller will power on and supply power to the robot arm. A solid green light indicates the controller has started successfully. When the controller is powered on, briefly pressing and releasing the power button again will shut down the controller and cut power to the robot arm. The green light turning off indicates successful shutdown.

![Figure 2.1 DSC controller](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Finpy09szSCx4bmkjXhah%2Fdsc-p008-img01.jpg?alt=media)

## 3. Mechanical Specifications

All dimensions in this chapter are in millimeters (mm).

_Figure 3.1 Controller dimensions_

_Figure 3.2 Horizontal installation dimensions_

![Figure 3.1 Controller dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0YmQNrwt3uWoBEcCdtxu%2Fdsc-p009-img01.png?alt=media)

![Figure 3.2 Horizontal installation dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6phHkXbS3bMlGmfCcZTV%2Fdsc-p009-img02.png?alt=media)

_Figure 3.3 Vertical installation dimensions_

![Figure 3.3 Vertical installation dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfUOawFrh3DGYWyVQD7We%2Fdsc-p010-img01.png?alt=media)

## 4. Electrical Characteristics

### 4.1 Electrical warnings and precautions

When designing and installing robot applications, please strictly follow the warnings and precautions listed below.

**WARNING**

The following warnings must be observed when designing and installing safety signal-related functions, as failure to do so may result in the loss of safety functions and cause injury or death.

* Never connect safety signals to a non-safety PLC with an inappropriate safety level. Always separate safety signals from regular I/O signals.
* All safety signals must use a dual-channel redundant design, with both channels remaining independent. This ensures that if one channel fails, the safety function will still be maintained.

**WARNING: ELECTRICITY**

* Make sure that the equipment is protected from water ingress. If water gets into the equipment, disconnect the power and contact technical supinterface. Do not reconnect the power until the issue is resolved.
* Only use the robot's original cables and avoid bending the cables.
* Make sure that the power supply connected to the controller is properly grounded and avoid leaving the grounding prong of the power plug floating.

**NOTICE**

* The robot has passed electromagnetic compatibility (EMC) tests according to relevant standards. Electromagnetic interference exceeding these standards may affect the robot's behavior. Extremely high signal levels or excessive exposure to electromagnetic fields may cause permanent damage to the robot. DOBOT assumes no responsibility for any damage caused by EMC issues beyond the standards.
* The length of I/O cables used to connect the controller to other machinery or equipment should not exceed 30 meters unless confirmed feasible through on-site testing. If necessary, use shielded cables.

### 4.2 Controller interfaces

The electrical interfaces of the DSC controller are concentrated on the front panel, with their layout shown in the figure below.

_Figure 4.1 Interfaces on the controller_

No. Description Controller power button (Maintained button). After connecting the controller to the external power supply, briefly press and release the power button to start the controller. When the controller is powered on, briefly press and release the power button again to shut down the controller and power off the robot arm. ①

**NOTE**

The user can also utilize a remote switch to power the controller on or off. Power interface, used to connect an external power supply to provide power ② to the controller. Robot arm interface. Used to connect the robot arm's heavy-duty cable for power supply and ③ communication. This interface is used to connect a teach pendant via an adapter cable, or to function as a LAN interface for connecting a computer for debugging ④ purposes, or for connecting other external devices that use TCP/IP or Modbus TCP protocols. The default IP address for LAN2 is 192.168.200.1. LAN1 interface. Default IP address: 192.168.5.1. This interface can be used to connect a computer for debugging or to connect other external devices ⑤ using TCP/IP or Modbus TCP protocols. Only the IP address of LAN1 can be modified through the control software DobotStudio Pro. USB interface, used for WiFi module connection. ⑥

![Figure 4.1 Interfaces on the controller](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fa8L4YtYCgaVwUCKIoWCc%2Fdsc-p012-img01.png?alt=media)

No. Description Digital I/O interface, used for connecting external devices. For details, please ⑦ refer to the Digital I/O interface section. I/O power interface. For details, please refer to the I/O power interface instruction. RS485 interface. For details, please refer to the RS485 interface instruction. ⑧ Remote switch interface. For details, please refer to the Remote switch interface instruction. E-stop interface, refer to the E-stop interface for details. Three-position enable switch/teach pendant power interface. For details, ⑨ please refer to the Teach pendant interface section. Analog I/O interface, used for connecting external devices. For details, please ⑩ refer to the Analog I/O interface section.

### 4.3 Power interface

It connects to an external DC power supply to provide power to the controller. For the CRA series robot arm, you need to provide your own 30 – 60 V DC power supply (48 V recommended).

_Figure 4.2 Power interface_

Pin Name Definition V+ DC 48V power positive (+) ① DC 48V power negative (-) V- ② Protective earth PE ③

![Figure 4.2 Power interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZfZOOndW50tCN17ph8U5%2Fdsc-p013-img01.png?alt=media)

### 4.4 Robot arm interface

It connects to the heavy-duty receptacle on the robot arm base via a heavy-duty cable, providing both power and communication to the robot arm.

_Figure 4.3 Robot arm interface_

Pin Name Definition V+ DC 48V power positive (+) ① V+ DC 48V power positive (+) ② DC 48V power negative (-) Robot arm power interface V- ③ DC 48V power negative (-) V- ④ Protective earth PE ⑤ Robot arm communication ECAT/CAN Receive/Transmit data interface ⑥

![Figure 4.3 Robot arm interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTX7t9x13qvV2OwOk3DxI%2Fdsc-p014-img01.png?alt=media)

The pin definitions for the ECAT/CAN communication interface are as follows:

_Figure 4.4 ECAT/CAN pin definitions_

Pin Name Definition Pin1 TD+ Transmit data+ Pin2 TD- Transmit data- Pin3 RD+ Receive data+ Pin4 / Pin5 -- Reserved Pin6 RD- Receive data- Pin7 CANH CAN High Pin8 CANL CAN Low

### 4.5 Teach pendant interface

Connect to interface (teach pendant communication interface), and pins 5 to 10 of interface (used for three-position enable switch and teach pendant power supply) via a teach pendant adapte①r cable. ②

![Figure 4.4 ECAT/CAN pin definitions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuNS4o8uqyfkHKBKDCv58%2Fdsc-p015-img01.png?alt=media)

_Figure 4.5 Teach pendant interface_

Pin Name Definition TP/LAN2 Teach pendant communication interface ① Pin5 3PE1 Pin6 24V Reserved for teach pendant three-position enable switch (Connect to either pin 6 or pin 8 for 24V) Pin7 3PE2 ② Pin8 24V Pin9 GND Reserved for power supply Pin10 24V

**NOTE**

Pins 1 to 4 of interface are designated for the E-stop button. See E-stop interface section for details. ②

![Figure 4.5 Teach pendant interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaHJCxSRSionPhant4nRx%2Fdsc-p016-img01.png?alt=media)

### 4.6 LAN interface

The small controller is equipped with two LAN interfaces for TCP/IP and Modbus TCP communication. The LAN1 interface has a default IP address of 192.168.5.1, which can be modified via the control software. For details, please refer to the control software's user guide. The LAN2 interface has a default IP address of 192.168. 200.1 and currently does not support modification.

_Figure 4.6 LAN interface_

### 4.7 USB interface

The DSC is equipped with one USB interface for connecting a wireless receiver.

_Figure 4.7 USB interface_

![Figure 4.6 LAN interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpK0eJcIarU1bgaAZaylM%2Fdsc-p017-img01.png?alt=media)

![Figure 4.7 USB interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTTCtInn5gbzjvLvxBSuT%2Fdsc-p017-img02.png?alt=media)

### 4.8 I/O power interface

The I/O interface can be powered by either an internal or external 24 V power supply.

_Table 4.1 I/O interface supply specifications_

Interface Parameter Min Typical value Max Unit Internal 24V power supply Voltage 23 24 25 V 24V-0V Current 0-2 A External 24V power supply Voltage 20 24 29 V External power supply Current 0-3 A When using the internal power supply, short-circuit the 0V and 24V pins to the nearest I/O 0V and I/O 24V pins respectively (factory default: short-circuited), as shown in the figure below.

_Figure 4.8 I/O with internal power_

If a higher total output current is required, an external 24 V power supply can be connected as shown in the figure below. The external and internal power supplies are isolated and will not interfere with each other.

_Figure 4.9 I/O with external power_

![Table 4.1 I/O interface supply specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsCRv8b5YOmYlt6Ni1jDk%2Fdsc-p018-img01.png?alt=media)

![Figure 4.8 I/O with internal power](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoxX59wyFZh2fVEfPK2sM%2Fdsc-p018-img02.png?alt=media)

**NOTE**

All subsequent chapters are based on the premise that the I/O power is connected. Instructions for I/O power wiring will not be repeated.

### 4.9 Digital I/O interface

16 channels for digital input and 16 for output, dedicated to reading and writing digital signals as shown below. The default type for digital signals is PNP, but it can be configured to NPN using the control software. When using the built-in I/O power supply, the voltage is 24V, with a total output current of up to 2A and a maximum single channel output of 0.5A. It supports external power supply, with a maximum current of up to 3 A. All interfaces with identical silkscreen labels are functionally identical. Any available interface can be selected for connection during wiring.

_Figure 4.10 Digital signal interfaces_

![Figure 4.10 Digital signal interfaces](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEZhOCjH7gi003f2US9YC%2Fdsc-p019-img01.png?alt=media)

#### 4.9.1 Digital I/O interface specifications

Interface Parameter Min Typical value Max Unit Digital input (DI1 – DI16) Voltage -3-30 V OFF range -3-5 V ON range 20-30 V DIx Current 2-4 mA (ON range) Type-NPN/PNP - - Digital output (DO1 – DO16) Current 0-0.5 A Voltage drop 0-0.5 V DOx Leakage 0-0.1 mA current Type-NPN/PNP - -

#### 4.9.2 DI wiring instruction

1. DI connected to a simple switch: The wiring diagram is shown in the figure below.

Either the PNP or NPN wiring method can be selected based on field requirements.

_Figure 4.11 DI connected to a simple switch (PNP wiring method)_

_Figure 4.12 DI connected to a simple switch (NPN wiring method)_

![Figure 4.11 DI connected to a simple switch (PNP wiring method)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyXjTH3etAG4yJ1Tf1l7D%2Fdsc-p020-img01.png?alt=media)

![Figure 4.12 DI connected to a simple switch (NPN wiring method)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkNvrTfVn7u6hprPXU4aq%2Fdsc-p020-img02.png?alt=media)

2. DI connected to external PNP/NPN three-wire sensor: The wiring method is the same;

you only need to switch between PNP and NPN modes using the control software.

* If the three-wire sensor is powered by the controller, V+ and V- need to be connected to the I/O 24V and I/O 0V of controller. The wiring configuration is shown in the figure below.

_Figure 4.13 DI connected to a three-wire sensor (powered by controller)_

* If the three-wire sensor is powered by an external power source, the negative terminal of the external power source needs to be connected to the I/O 0V of the controller. The wiring configuration is shown in the figure below.

_Figure 4.14 DI connected to a three-wire sensor (externally powered)_

#### 4.9.3 DO wiring instruction

The DO is set to PNP by default but can be configured to NPN through the control software. If the configuration in the control software is opposite to the load wiring (for instance, the software is set to PNP, but the load wiring is NPN), the load will not function properly. For DO configured as PNP, the wiring method to connect an external load is shown in the

![Figure 4.13 DI connected to a three-wire sensor (powered by controller)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiUBcwfKHlAKXFkLwhStl%2Fdsc-p021-img01.png?alt=media)

![Figure 4.14 DI connected to a three-wire sensor (externally powered)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3YVwOb2GqKCN9Ziso0LI%2Fdsc-p021-img02.png?alt=media)

diagram below.

_Figure 4.15 PNP-type DO connected to external load_

* For DO configured as NPN, the wiring method to connect an external load is shown in the diagram below.

_Figure 4.16 NPN-type DO connected to external load_

It is recommended that there be a minimum interval of 15ms between two DI signals or two DO signals.

### 4.10 Analog I/O interface

The analog input/output interface provides two channels each for analog signal input and output. Analog signals support either voltage (0 – 10V) or current signals (4 – 20mA), with the default set to voltage signals. You can configure it to current signals using control software. To enhance the accuracy of analog signals, it is recommended to use shielded cables or twisted pairs for connections.

![Figure 4.15 PNP-type DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdWSU5eWX2HiI2YUya17M%2Fdsc-p022-img01.png?alt=media)

![Figure 4.16 NPN-type DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUZsUMRcx5uaXfrLlD56W%2Fdsc-p022-img02.png?alt=media)

#### 4.10.1 Analog I/O interface specifications

Interface Parameter Min Typical value Max Unit Analog input (Voltage mode) Voltage 0-10 V AIx Resistance-14.7-kΩ Resolution-12-Bit Analog input (Current mode) Current 4-20 mA AIx Resistance-499-Ω Resolution-12-Bit Analog output (Voltage mode) Voltage 0-10 V Current 4-20 mA AOx Resistance-150-Ω Current-12-Bit Analog output (Current mode) Current 4-20 mA AOx Current-12-Bit

#### 4.10.2 AI wiring instruction

The wiring diagram for connecting AI interfaces to the device under test (DUT) is shown in the figure below.

_Figure 4.17 AI connected to Device Under Test_

![Figure 4.17 AI connected to Device Under Test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fb4WK1mGENqiuNjtBOyn1%2Fdsc-p023-img01.png?alt=media)

#### 4.10.3 AO wiring instruction

The wiring diagram for connecting AO interfaces to an external load is shown in the figure below.

_Figure 4.18 AO connected to external load_

### 4.11 RS485 interface

The RS485 interface is primarily used for Modbus RTU communication. When connecting to an external device (e.g., a PLC), connect the 485A (or 485+) and 485B (or 485-) interfaces of both devices correspondingly. The ground wire should also be connected based on the actual field conditions.

_Figure 4.19 RS485 connected to PLC_

### 4.12 Remote switch interface

The remote switch is used for the remote power-on/off operation of the controller. Before use, ensure the controller's power button is in the pressed (ON) position. When the remote switch is closed (circuit completed), the controller powers OFF. When the remote switch is open (circuit broken), the controller powers ON. The wiring method for connecting an external switch is shown in the figure below.

![Figure 4.18 AO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkt2tnCwHlFGVNLJRPp6F%2Fdsc-p024-img01.png?alt=media)

![Figure 4.19 RS485 connected to PLC](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDhlORVXy2KSRuRH5m88U%2Fdsc-p024-img02.png?alt=media)

_Figure 4.20 Remote switch wiring_

### 4.13 E-stop interface

Connect the E-stop button for the emergency stop control of the robot arm.

_Figure 4.21 Wiring for E-stop button_

**NOTICE**

Pressing the emergency stop, the robot arm stops all motion and loses power.

![Figure 4.20 Remote switch wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJCoZ9CypYkz9wH8ZIGNm%2Fdsc-p025-img01.png?alt=media)

![Figure 4.21 Wiring for E-stop button](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjs3W7iZVYFES6hMxdJBz%2Fdsc-p025-img02.png?alt=media)

## 5. Installation and Use

### 5.1 Installation environment

To maintain the performance of the controller and robot arm and ensure safe use, please place the controller in an environment that meets the following conditions.

**NOTICE**

Please make sure that the installation environment meets the following conditions to avoid potential damage.

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight and radiant heat.
* Keep away from dust, oil mist, smoke, salinity, metal powder, corrosive gases, and other contaminants.
* Do not use in a closed environment. A closed environment may cause the controller to overheat and shorten its service life.
* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Keep away from sources of electromagnetic interference.

### 5.2 Unpacking

Upon unpacking, check the attached shipping list to ensure that all items are included. If anything is missing, please contact your supplier.

### 5.3 Controller installation

The controller can be installed either horizontally or vertically. A minimum clearance of 50 mm should be maintained on all sides (except the mounting surface) to ensure adequate heat dissipation.

* Horizontal installation

Attach the two side mounting brackets from the accessory kit to the bottom of the controller. Then, place the controller horizontally on a flat and stable surface. Secure it using M3\*4 cross recessed countersunk head screws.

_Figure 5.1 Horizontal installation_

* Vertical installation

After installing the two side fixing brackets from the accessory kit onto the rear of both sides of the controller, place the controller vertically on a flat and stable mounting surface. Secure it using four M3\*4 cross recessed countersunk head screws.

_Figure 5.2 Vertical installation_

![Figure 5.1 Horizontal installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFsiG8aW64DrMDDSmtQ82%2Fdsc-p027-img01.png?alt=media)

![Figure 5.2 Vertical installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8dp8omj6GSE6MEhxiKVq%2Fdsc-p027-img02.png?alt=media)

### 5.4 Cable connection

_Figure 5.3 Cable connection_

1. Connect the heavy-duty cable: To connect the robot arm, insert the heavy-duty

connector into the interface on the robot arm base (NOTE: some robot models come with a pre-attached heavy-duty cable), and connect the opposite end to the robot arm interface on the controller. Specifically, connect the power wires to the power interface ( ) via the terminal block, and insert the communication cable into the ECAT/CAN interface ( ), ensuring all cable labels match the controller's silkscreen and securely ti①ghtening all terminal screws after wiring. ②

![Figure 5.3 Cable connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvs4rSKabHr9jLDZoPeBP%2Fdsc-p028-img01.png?alt=media)

2. Connect the teach pendant (Optional): Connect the teach pendant to the controller

using the adapter cable. Plug the RJ45 connector into the TP/LAN2 Ethernet interface ( ), and connect the three-position enable switch / teach pendant power to the corresponding interface ( ) via the terminal block. Ensure labels on the cable end m③atch the controller's silkscreen markings, then securely tighten all terminal screws after wiring. ④

3. Connect the E-stop button: Connect the E-stop button (included with the controller)

to the E-stop interface ( ) on the controller via the terminal block. Ensure all cable end labels match the controller's silkscreen markings, then securely tighten all terminal screws after wiring. ④

4. Connect the wireless receiver (Optional): Insert the wireless receiver into the USB

interface ( ) on the controller.

5. Connect the DC power supply: Connect the DC power supply (required for CRA

⑤ series robot arm; to be provided by yourself) to the power interface ( ) on the controller. ⑥

6. Connect the I/O module: Connect the factory pre wired I/O module to the controller

interface ( ) as shown in the figure below. - - ⑦

![Official manual figure, page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvndCu86v6zB49bxF5veJ%2Fdsc-p029-img01.jpg?alt=media)

**NOTICE**

* The specifications and installation method of the external cables should comply with local laws and regulations.
* Do not disassemble the robot by yourself, as this may result in electrical leakage.
* Make sure that the device is properly grounded.
* Do not bend the cable excessively, otherwise it may cause poor connections or cable breakage.
* Before connecting external devices, make sure the power outlet of the control system is disconnected. If not disconnected, may result in electric shock or device failure.
* To ensure device and personal safety, use supplied cables.
* After wiring, make sure that there are no loose screws or exposed cables inside the device.
* During normal operation, do not plug or remove the power cables and communication cables.
* The device must be fully wired before powering it on.
* Make sure that the cables are connected correctly to avoid damage to internal modules or external devices.
* Before connecting, check that the insulation and shielding of external cables are not damaged.

### 5.5 Power on and debugging

After turning on the external power supply, briefly press and release the power button on the controller. Once the button indicator turns solid green, connect to the robot arm via the control software, enable it, and proceed with jogging for debugging purposes. For detailed operation instructions, refer to DobotStudio Pro User Guide. Precautions for connecting to DobotStudio Pro are as follows:

* A wired connection is recommended for communication between the robot and the

DobotStudio Pro software. Wired connections improve communication security, help reduce latency, prevent interference from other devices on the internal network, and ensure that data is not intercepted by unauthorized devices.

* If an internal network is used, keep only essential devices on that network and isolate the robot's network from office or home networks.

**NOTICE**

If the network is not isolated, the robot will be exposed to a complex internal network environment, making it vulnerable to cyberattacks that could lead to data leaks or downtime.

* It is recommended to use a gateway with a firewall and configure it properly to restrict communication between external devices and the robot, ensuring that only whitelisted devices can communicate with the robot. This enhances the security of the robot's network environment.

**NOTICE**

Without firewall protection, the robot will face a more complex network environment and greater security risks.

* Prevent password leaks. It is recommended to raise user awareness of network security through internal training sessions. Avoid transmitting or storing sensitive information such as SSH passwords or Wi-Fi credentials via social media or email.
* Improve users' ability to identify phishing attacks and suspicious links, establish an emergency response plan, and define a clear vulnerability reporting process. If a vulnerability is found, contact DOBOT technical support promptly, share the vulnerability details, and seek a solution.

## 6. Warranty

### 6.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, DOBOT shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repair the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the device or components that are replaced or returned to DOBOT shall remain with DOBOT. Any other claims arising from or related to the device are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, DOBOT reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the device, DOBOT shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production device.

**NOTICE**

For a list of wearable parts, please contact DOBOT technical support.

### 6.2 Disclaimer

DOBOT is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. DOBOT strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

## Appendix A Technical Specifications

Product name DOBOT DSC 220m&#x6D;_&#x31;50m&#x6D;_&#x34;5mm Size (8.66inc&#x68;_&#x35;.91inc&#x68;_&#x31;.77inch) Weight 1.2kg (2.65lb) Input power 30–60VDC Voltage 24V IO power Built-in power supply: Max 2A, external power Current supply: Max 3A, single channel current: Max 0.5A DI 16 channels (NPN or PNP) DO 16 channels (NPN or PNP) General I/O interface AI 2 channels, voltage/current mode, 0–10V, 4–20mA AO 2 channels, voltage/current mode, 0–10V, 4–20mA SI Safety I/O 16 channels (DI/DO configured via control interface software) SO Remote power on/off Supported 2 interfaces, used for teach pendant, TCP/IP, Ethernet Modbus TCP, Ethernet/IP, and Profinet interface communication Communication interface USB 1 interface, used for Wi-Fi module connection 1 interface, used for RS485 and Modbus RTU RS485 communication Temperature 0 – 50 Environment Humidity ≤ ℃95 %, n℃on-condensing IP rating IP22 Cooling method Fan cooling Teaching method Teach pendant, PC, APP

## Appendix B Functional Safety

### B.1 Safety requirements

The safety functions generally comply with EN ISO 10218-1 and specifically meet the following requirements. When a safety-related control system is required, the safety-related components shall be designed so that:

* A single fault in any component does not lead to the loss of the safety function.
* Where reasonably practicable, a single fault is detected at or before the next demand on the safety function.
* When a single fault occurs, the safety function remains operational, and the system remains in a safe state until the detected fault is rectified.
* All reasonably foreseeable faults shall be detected.

This requirement is considered equivalent to Category 3 as described in ISO 13849-1. Category 3 is typically achieved through redundant circuits, such as dual-channel. The safety functions and the robot controller comply with Performance Level d (PLd) according to ISO 13849-1.

### B.2 Stop categories

According to IEC 60204-1, the Nova series robots provide three stop categories: Stop Category 0, Stop Category 1, and Stop Category 2. Stop Category 0 is an uncontrolled stop, while Stop Category 1 and Stop Category 2 are controlled stops.

* When Stop Category 0 is triggered, the robot’s power is cut off immediately, and the robot stops instantaneously.
* When Stop Category 1 is triggered, the robot decelerates to a stop. After the robot stops, power to the robot is disconnected.
* When Stop Category 2 is triggered, the robot decelerates to a stop along its programmed trajectory. After stopping, the robot remains enabled.

### B.3 Overview

The Nova series robot system features 30 safety functions, designed and tested in accordance with the following standards:

* IEC 60204-1:2018+A1:2025
* ISO 13849-1: 2023
* ISO 13849-2:2012

Safety functions can be divided into the following four categories:

* Safety SI (Safe Input) Category
* Safety SO (Safe Output) Category
* Safety Limit Category
* Other

Stop Response Stop Assessment Category SF Name Category Time Distance Result Emergency Stop SF1 Stop ≤300ms ≤300mm PLd/Cat. 3 category 1 (System) Emergency Stop SF2 ≤300ms ≤300mm PLd/Cat. 3 Stop (User) category 1 Safeguard Stop SF3 ≤500ms ≤500mm PLd/Cat. 2 Stop category 2 Safeguard Stop SF4 Stop Reset ≤500ms ≤500mm PLd/Cat. 2 Safety SI category 2 Input Reduced Stop SF5 ≤300ms ≤300mm PLd/Cat. 2 Mode Input category 1 Mode Switch Stop SF6 Input ≤500ms ≤500mm PLd/Cat. 2 category 2 (Manual/Auto) 3-Position Stop SF7 Enabling ≤300ms ≤300mm PLd/Cat. 2 category 1 Device Input Emergency DO output SF8 Stop Status ≤10ms NA PLd/Cat. 3 low level Output System Emergency DO output SF9 ≤10ms NA PLd/Cat. 3 Stop Status low level Output Safeguard DO output SF10 Stop Status ≤10ms NA PLd/Cat. 3 low level Output Safety SO Reduced DO output SF11 Mode Status ≤10ms NA PLd/Cat. 2 low level Output Moving DO output SF12 ≤10ms NA PLd/Cat. 2 Status Output low level Not Stopping DO output SF13 ≤10ms NA PLd/Cat. 3 Status Output low level Safe Home DO output SF14 Position ≤10ms NA PLd/Cat. 2 low level Output Safety SF15 Joint Position Stop ≤300ms ≤300mm PLd/Cat. 2 Limit (Soft

Stop Response Stop Assessment Category SF Name Category Time Distance Result Limit Axis Limiting) category 1 Pose Limit Stop SF16 ≤300ms ≤300mm PLd/Cat. 2 (Safety Zone) category 1 Joint Speed Stop SF17 ≤300ms ≤300mm PLd/Cat. 2 Limit category 1 TCP Speed Stop SF18 ≤300ms ≤300mm PLd/Cat. 2 Limit category 1 TCP Speed Limit in Stop SF19 ≤300ms ≤300mm PLd/Cat. 2 Teaching category 1 Mode Momentum Stop SF20 ≤300ms ≤300mm PLd/Cat. 2 Limit category 1 Stopping Stop SF21 ≤300ms ≤300mm PLd/Cat. 2 Time Limit category 0 Stopping Stop SF22 ≤300ms ≤300mm PLd/Cat. 2 Distance Limit category 0 Stop SF23 Power Limit ≤300ms ≤300mm PLd/Cat. 2 category 1 TCP Force Stop SF24 ≤300ms ≤300mm PLd/Cat. 2 Limit category 1 Joint Torque Stop SF25 ≤300ms ≤300mm PLd/Cat. 2 Limit category 1 TCP Position Stop SF26 Deviation ≤300ms ≤300mm PLd/Cat. 2 category 1 Limit Start/Restart Stop Other SF27 ≤300ms ≤300mm PLd/Cat. 2 Interlock category 1 Stop Safety SI SF28 Normal Stop ≤300ms ≤300mm PLd/Cat. 3 category 1 Hand-Guided Stop Other SF29 Control (Drag ≤500ms ≤500mm PLd/Cat. 2 category 1 Teaching) Hold-to-Run Stop Other SF30 ≤500ms ≤500mm PLd/Cat. 2 Control category 2

### B.4 Detailed description

* SF1 System Emergency Stop
* The robot can be triggered into emergency stop state via the emergency stop button or the emergency stop switch on the teach pendant, performing a Category 1 stop.
* The system emergency stop input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into emergency stop state.
* When the safety controller detects that the emergency stop button has been pressed, it notifies the servo to perform an emergency stop and monitors the stopping time. If the stopping time exceeds the stopping time limit, a Category 0 stop is executed.
* SF2 User Emergency Stop
* The robot can be triggered into emergency stop state via the user emergency stop input signal in Safety SI, performing a Category 1 stop.
* The user emergency stop input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into emergency stop state. The emergency stop logic is the same as that of the system emergency stop.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* SF3 Safeguard Stop
* The robot can be triggered into safeguard stop state via the safeguard stop input signal in Safety SI, performing a Category 2 stop.
* The safeguard stop input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into the safeguard stop state. In this state, starting a program is not allowed if no program is running, and any running program will be paused.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* SF4 Safeguard Stop Reset
* Used in conjunction with the safeguard stop signal:

When no reset signal is configured, the robot program automatically resumes  running after the safeguard stop signal is cleared. When a reset signal is configured, after the safeguard stop signal is cleared,  the safeguard stop reset must be triggered first, followed by clicking "Resume" for the robot program to automatically continue running.

* The safeguard stop reset input is set by default to a normally open signal with a high level. A rising edge on both channels triggers the reset of the safeguard stop state, and the time interval between the two channel triggers must be ≤ 100 ms.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* SF5 Reduced Mode
* The robot can be triggered into reduced mode via the reduced mode input signal in Safety SI.
* In reduced mode, the robot's motion speed and safety limits switch to the values configured for reduced mode (i.e., reduced parameters). The robot monitors and alarms according to these reduced parameters. When an alarm is triggered, a Category 1 stop is executed.
* The reduced mode input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into reduced mode. When the input returns to high level, the robot exits reduced mode and enters normal mode.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* SF6 Manual/Auto Mode Switch
* When the manual/auto mode switch function is enabled in the safety settings, the robot can be switched between manual and auto modes via the manual/auto mode switch input signal in Safety SI. A low level on either channel triggers the robot to enter manual mode. When both channels are at high level, the robot enters auto mode.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* Once this function is configured, disabling the manual/auto mode function in the settings will prompt the user that it cannot be disabled.
* SF7 3-Position Enabling
* In manual mode, the robot can be triggered into the enabled state via the 3- position enabling input signal in Safety SI. A low level on either channel triggers the robot into the disabled state, while a high level on both channels triggers the enabled state. The characteristics of the external 3-position enabling device are identical to those of the 3-position enabling switch on the teach pendant when it is set to the enabled state.
* The 3-position enabling signal is not active in automatic mode.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* SF8 Emergency Stop Status Output
* When the robot is in the emergency stop state, the emergency stop status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* The maximum output current per channel is 500 mA (this applies to all single- channel outputs described below).
* SF9 System Emergency Stop Status Output
* When the robot is in the system emergency stop state, the system emergency stop status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.

**NOTE: This signal is primarily used when interlocking two safety devices to**

prevent the emergency stop state from becoming locked and unrecoverable.

* SF10 Safeguard Stop Status Output
* When the robot is in the safeguard stop state, the safeguard stop status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* SF11 Reduced Mode Status Output
* When the robot is in the reduced mode state, the reduced mode status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* SF12 Moving Status Output
* When one or more joints of the robot move faster than 1°/s (excluding drag teaching mode), the robot is considered to be in the moving state. In this state, the moving status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* SF13 Not Stopping Status Output
* When the robot is in automatic mode and the program is not paused, the robot is considered to be in the not stopping state. In this state, the not stopping status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* SF14 Safe Home Position Status Output
* When the robot is within ±10mm of the safe home position set by the control software, the safe home position status output signal in Safety SO outputs a high level; otherwise, it outputs a low level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* SF15 Joint Position Limit
* The robot uses proper motion planning to prevent each joint from exceeding the allowable motion range set by the control software.
* If a joint exceeds its allowable motion range, a safety controller alarm is triggered and a Category 1 stop is executed.
* SF16 Safety Zone Limit
* Two types of safety zones can be defined: alarm safety zone and reduced safety zone. When configured as an alarm safety zone, the robot uses proper motion  planning to prevent the currently active TCP from entering the unsafe zone. If the TCP enters the unsafe zone, a safety controller alarm is triggered and a Category 1 stop is executed. When configured as a reduced safety zone, if the robot enters the unsafe  zone, it switches to reduced mode, and the safety controller monitors the robot using reduced mode parameters.
* Two methods are available for defining the robot's safety zone:

Safety Wall: When configured as a physical wall (alarm wall) or a virtual wall  (reduced wall), the positive direction of the wall is the safe zone, and the opposite direction is the unsafe zone. Safety Zone: When configured with "Alarm" or "Reduced" behavior, the  positive direction of the safe side is the safe zone, and the opposite direction is the unsafe zone.

* SF17 Joint Speed Limit

During automatic program execution, the robot uses proper motion planning to prevent joint speeds from exceeding the safety limits set by the control software. If any joint speed exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

* SF18 TCP Speed Limit
* During automatic program execution, the robot uses proper motion planning to prevent TCP speed from exceeding the safety limit set by the control software. If TCP speed exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.
* SF19 TCP Speed Limit in Manual Mode

In manual mode, the robot uses proper motion planning to prevent TCP speed from exceeding the safety limit set by the control software. If TCP speed exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

* SF20 Momentum Limit
* During automatic program execution, the robot uses proper motion planning to prevent the total momentum of the robot from exceeding the safety limit set by the control software. If the total momentum exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.
* SF21 Stopping Time Limit
* During automatic program execution, the robot uses proper motion planning to ensure that when an alarm stop is triggered at any point, the stopping time does not exceed the safety limit set by the control software. If the actual stopping time exceeds the safety limit, a safety controller alarm is triggered and a Category 0 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.
* SF22 Stopping Distance Limit
* During automatic program execution, the robot uses proper motion planning to ensure that when an alarm stop is triggered at any point, the stopping distance does not exceed the safety limit set by the control software. If the actual stopping distance exceeds the safety limit, a safety controller alarm is triggered and a Category 0 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.
* SF23 Power Limit
* Based on the power safety limits set by the control software, the robot calculates the allowable fluctuation range of the actual torque at each joint and limits the actual torque magnitude to prevent the sum of power calculated from the difference between the planned torque and the actual torque at each joint from exceeding the safety limit. If the deviation between actual power and planned power exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.
* SF24 TCP Force Limit
* Based on the TCP force safety limits set by the control software, the robot calculates the allowable fluctuation range of the actual torque at each joint and limits the actual torque magnitude to prevent the sum of TCP force calculated from the difference between the planned torque and the actual torque at each joint from exceeding the safety limit. If the deviation between actual TCP force and planned TCP force exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.
* SF25 Joint Torque Limit

The robot continuously monitors the actual joint torque values. If the torque exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

* SF26 TCP Position Deviation Limit

The robot continuously monitors the deviation between the actual TCP position and the target TCP position. If the deviation exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

* SF27 Start/Restart Interlock

When starting or restarting, the robot is in the disabled state and cannot run automatically. To start the robot, you must first enable it and then press the run button. After enabling, the safety controller continuously monitors the deviation between the actual position and the target position of each joint via the encoder. If the deviation exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

* SF28 Normal Stop
* The robot can be triggered into the stop state via an external button, performing a Category 1 stop.
* The normal stop input is set by default to a normally closed signal with a high level. A falling edge on either channel triggers the robot into the normal stop state.
* When the safety controller detects that the external button has been pressed, it notifies the servo to perform a Category 1 stop and monitors the stopping time. If the stopping time exceeds the stopping time limit, a Category 0 stop is executed.
* SF29 Hand-Guided Control (Drag Teaching)
* The robot can only enter hand-guided control mode when it is in a Category 2 stop state.
* When the hand-guided control button is pressed, the robot can be manually moved. When the button is released, a Category 2 stop is executed.
* In hand-guided control mode, the TCP speed is limited to the user-configured value, with a maximum upper limit of 250 mm/s.
* In hand-guided control mode, position limits remain in effect.
* SF30 Hold-to-Run Control
* When the hand-guided control button is pressed, the robot can be manually moved.
* When the button is released, a Category 2 stop is executed.

## Appendix C Applicable Standards

UL 1740 4th Edition, Revised August 11, 2023: Standard for Safety for Robots and Robotic Equipment NFPA 79-2024, Dated December 21, 2023: Electrical Standard for Industrial Machinery CAN/CSA Z434-14 (R2019), Reaffirmed 2019: Industrial robots and robot systems ANSI/RIA R15.06-2012: American National Standard for Industrial Robots and Robot Systems-Safety Requirements CSA C22.2 No. 301:23, Rev. September 2023: Industrial electrical machinery EN ISO 10218-1:2011 Robots and robotic devices-Safety Safety Standards requirements for industrial robots-Part 1: Robots; EN IEC 60204-1:2018+A1:2025 Safety of machinery-Electrical equipment of machines-Part 1: General requirements; EN ISO 12100:2010 Safety of machinery-General principles for design-Risk assessment and risk reduction; ISO/TS 15066:2016 Robot and Robotic Devices-Collaborative Robots; EN ISO 13849-1:2023 Safety of machinery-Safety-related parts of control systems-Part 1: General principles for design ISO 13849-2:2012 Safety of machinery-Safety-related parts of control systems Part 2: Validation EN IEC 61000-6-2:2019 Electromagnetic compatibility (EMC) - Part 6-2: Generic standards-Immunity standard for industrial environments; EN IEC 61000-6-4:2019 Electromagnetic compatibility (EMC) - EMC Standards Part 6-4: Generic standards-Emission standard for industrial environments EN 55011:2016+A1:2017+A2:2021: Industrial, scientific and medical equipment-Radio-frequency disturbance characteristics-Limits and methods of measurement
