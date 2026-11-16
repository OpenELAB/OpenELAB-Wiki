---
description: >-
  Operation guide for the DOBOT Magician E6 Mini Training Station (PLC version):
  safety, hardware, software installation, the robot handling application, and
  key PLC/HMI/robot programs.
---

# DOBOT Magician E6 Mini Training Station Operation Guide

### DOBOT Magician E6 Mini Training Station for Automation Education

{% embed url="https://openelab.io/products/dobot-e6-mini-training-station" %}

### Contents

* Safety precautions
* Product and hardware introduction
* Software installation (DobotStudio Pro, Siemens PLC, and Siemens HMI)
* Robot handling application (hardware, wiring, IO configuration, and program debugging)
* Key program description (PLC, HMI, and robot programs)

### Safety Precautions

* Read this guide carefully before using the training station for the first time.
* Use the device within the specified environmental range; exceeding specifications or load conditions shortens product life and may damage the device.
* Only personnel who have been trained or have equivalent professional skills may install, operate, and maintain the device.
* Set up safety guardrails to keep personnel out of the robot's workspace, and always operate the robot from outside the guardrails.
* Use the emergency stop switch in emergencies. Do not disassemble, modify, or repair the device without authorization.
* Do not frequently power the robot on and off (keep it below once per minute).

### About the Training Station

The Magician E6 Mini Training Station is a compact 600 × 480 mm automation teaching platform that integrates the Magician E6 six-axis robot (controller embedded in the base), an emergency stop switch, a total control unit, an air pump box, a conveyor, and a PLC box. It is designed for hands-on learning of robot motion control, PLC programming, and HMI development through a complete point-to-point material handling application.

### Preface

**Purpose** This manual provides guidance on operating the Magician E6 Mini Training Station, enabling users to better understand and use the platform.

**Intended audience** This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

**Revision history**

**Symbol conventions** The symbols that may be found in this document are defined as follows.

| Date       | Version | Revision history                                                                                                                                                                                                      |
| ---------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 2026/09/17 | V1.3    | Update the software screenshots related to "Robot debugging > Debugging points".                                                                                                                                      |
| 2026/03/16 | V1.2    | <p>• Added guidance for creating user coordinate system 1, as well as explanations for coordinate systems 0 and 1.<br>• Update the methods for downloading HMI software and the description of the robot program.</p> |
| 2026/01/19 | V1.1    | <p>• Added user coordinate system requirement for the P2 point.<br>• Added instructions for downloading PLC documentation.</p>                                                                                        |
| 2025/06/24 | V1.0    | The first release.                                                                                                                                                                                                    |

| Symbol  | Description                                                                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER  | Indicates a hazard with a high level of risk which, if not avoided, could result in death or serious injury.                                   |
| WARNING | Indicates a hazard with a medium level or low level of risk which, if not avoided, could result in minor or moderate injury, robot arm damage. |
| NOTICE  | Indicates a potentially hazardous situation which, if not avoided, could result in robot arm damage, data loss, or unanticipated result.       |
| NOTE    | Provides additional information to emphasize or supplement important points in the main text.                                                  |

## Chapter 1 Magician E6 Mini Training Station

### 1. Safety Precautions

This chapter introduces the safety precautions to be taken during use of this product. Please read this document carefully before using the Training Station for the first time. This product needs to be used in an environment meeting design specification. You cannot remold the product without authorization, otherwise, it could lead to product failure, and even personal injury, electric shock, fire, etc. Personnel who use this product for system design and manufacturing must be the ones who have been trained by our company or corresponding institutions or the ones with equivalent professional skills, and must strictly follow the specifications in the operating guide to use the Training Station.

#### 1.1 Safety warning signs

The safety warning signs as shown in table below may appear in this chapter, and the meanings they represent are as shown as follows.

| Symbol      | Description                                                                                                                                                                                            |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DANGER      | Indicates a high potential danger that, if not avoided, could result in death or serious injury.                                                                                                       |
| ELECTRICITY | Indicates an imminent dangerous electrical situation that, if not avoided, could result in personal injury or serious device damage.                                                                   |
| HOT         | Indicates a potentially hazardous hot surface that, if touched, may cause personal injury.                                                                                                             |
| WARNING     | Indicates a hazard with a medium level or low level of risk which, if not avoided, could result in minor or moderate injury, robot arm damage.                                                         |
| NOTICE      | Indicates a potential risk, if ignored, could result in device damage, data loss, or unanticipated result.                                                                                             |
| CAUTION     | Indicates a situation that, if not avoided, could result in personnel injury or damage to the device. For items marked with this symbol, there is sometimes a possibility of significant consequences. |

#### 1.2 General safety

The safety instructions below should be followed while starting and using the Training Station for the first time.

**DANGER**

* The training platform is an electrified device. Non-professionals are not allowed to change the route without authorization. Otherwise, it could easily cause harm to devices or personnel.
* During operation of the device, local laws and regulations should be strictly observed, and the safety precautions described in the Operating Guide serve only as a supplement to local safety regulations.
* Please use the device within the specified environmental range. Using beyond the devices specifications and load conditions will shorten the service life of the product and even damage the devices.
* Users need to ensure that the devices are operating under safe conditions and there are objects that may harm the devices around.
* Do not frequently turn on or off the power of CR3A. Otherwise, it may lead to a decrease in performance of internal main circuit components. If it is necessary to repeatedly and continuously turn on or off the power supply, please keep it less than once per minute.

**NOTICE**

* Personnel responsible for installing, operating, and maintaining the device must undergo rigorous training, understand all safety precautions, and master correct operation and maintenance methods before operating and maintaining the device.
* Personnel without professional training must not disassemble and repair the device without authorization. In case of a malfunction, contact SHENZHEN DOBOT CORP LTDs technical support engineer in time.
* Please be sure to perform daily inspections and regular maintenance and promptly replace faulty components to ensure the safe operation of the device.
* If the device is scrapped, please comply with relevant laws for proper disposal of industrial waste to protect the environment.
* To prevent personnel from entering the workspace of the device by mistake, please be sure to set up safety guardrails to prohibit personnel from entering hazardous regions.
* Before operating the robot, please be sure that there is no one inside the safety guardrails; When operating the robot, be sure to operate outside the safety guardrails.
* Do not keep the Training Platform exposed to permanent magnetic fields, as strong magnetic fields will cause device damage.
* SHENZHEN DOBOT CORP LTD assumes no responsibility for the device damage or personal injury caused by failure to follow the product instructions or by other improper operations.
* SHENZHEN DOBOT CORP LTD is not responsible for the damage generated during the transport and handling of the device.
* After removal of the outer packaging, make sure that the robot maintains its original packing posture and the brakes on all axes are in normal working condition.

**WARNING**

* Before operating the device, please put on anti-static clothing and gloves.
* It is strictly prohibited to change, remove, or modify the nameplates, instructions, icons, and markings of the device.
* Always be careful while handling and installing the device, and avoid collision. The device should be handled with care according to the tips on the packaging box and placed correctly in the direction of the arrows. Otherwise, it may easily damage the device.
* During handling of the robot, both hands are required. Hold the large arm or the small arm with one hand, and hold the base with the other hand. Keep the body stable to avoid damage caused by arbitrary rotation of the base or loosening of other shafts.
* To protect the device and personnel safety, please use the supplied cables.
* Be sure that both the robot and the tools are correctly and safely installed in place.
* Be sure that the robot has enough space for free activities.
* Any impact will release a large amount of kinetic energy, which is much higher than that under high-speed and high-load situations.

**(3) WARNING** Before operating the device, please put on anti-static clothing and gloves. It is strictly prohibited to change, remove, or modify the nameplates, instructions, icons, and markings of the device. Always be careful while handling and installing the device, and avoid collision. The device should be handled with care according to the tips on the packaging box and placed correctly in the direction of the arrows. Otherwise, it may easily damage the device. During handling of the robot, both hands are required. Hold the large arm or the small arm with one hand, and hold the base with the other hand. Keep the body stable to avoid damage caused by arbitrary rotation of the base or loosening of other shafts. To protect the device and personnel safety, please use the supplied cables. Be sure that both the robot and the tools are correctly and safely installed in place. Be sure that the robot has enough space for free activities. Any impact will release a large amount of kinetic energy, which is much higher than that under high-speed and high-load situations.

#### 1.3 Personal safety

During running of the robot system, always ensure the personnel safety of the operators. Please strictly follow the general precautions listed below.

**WARNING** During handling of the device, the maximum weight permitted by local laws or regulations for single person handling must not be exceeded. Do not touch the wiring terminals or disassemble the device while it is powered on. Otherwise, electric shock accidents may occur. Please confirm that the device is well grounded. Otherwise, it will endanger personal safety. Do not touch the power terminals or disassemble the internal components within 10 minutes of cutting off the power supply of the device to prevent residual voltage in the internal capacitors of the device from causing electric shock accidents. Even if the power switch of the device is already in the “OFF” state, it is still not allowed to touch or disassemble the internal components of the device to prevent residual voltage in the internal capacitors of the device from causing electric shock accidents. Be sure to establish safety measures (such as guardrails) near the robot operating region to protect the operator and the surrounding persons.

### 2. Product Introduction

The Magician E6 Mini Training Station is an educational solution designed for vocational and higher education, which helps trainees understand the functions and roles of standard automation systems and improve the effectiveness of training. A standard Magician E6 Mini Training Station is shown in the figure below. The Magician E6 Mini Training Station can implement the following applications: Robot programming and commissioning; User/tool coordinate system setting; Robot trajectory programming; Robot handling and palletizing;

![2. Product Introduction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXOgEVkxvwLrDcHjEUqkH%2Fimg_e466c7f11849.jpeg?alt=media)

### 3. Hardware Introduction

#### 3.1 Hardware configuration of Magician E6 Mini training station

The size of the Magician E6 Training Station is 600 × 480 mm, and the installation positions of the component are as shown in figure below.

![3.1 Hardware configuration of Magician E6 Mini training station](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeQf9GsjPGnlBpSgJw0GM%2Fimg_1197327fc889.jpeg?alt=media)

#### 3.2 Magician E6 robot

The Magician E6 robot working system consists of the robot body, emergency stop switch, and robot control software (installed in tablet or PC).

![3.2 Magician E6 robot](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnZSb9uQIPhOiFiOTR269%2Fimg_ae2f2bdb2d8e.jpeg?alt=media)

The functions of the main components of Magician E6 are shown in the table below.

**3.2.1 Robot components** The Magician E6 robot consists of a base, six rotational joints, two connecting links (upper arm and forearm), and a tool flange at the end effector. The flange is equipped with an aviation connector port on its side.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2n4vhHC144dzpQoVBeZC%2Fimg_27ed8189552a.png?alt=media)

**3.2.2 Indicators and buttons** The Magician E6 robot is equipped with a circle of status indicators near the J1 and J6 joints, with the meanings described below:

| No. | Name                  | Description                                                                                 |
| --- | --------------------- | ------------------------------------------------------------------------------------------- |
| 1   | Magician E6 robot     | Six-axis robot arm featuring an integrated design with the controller embedded in the base. |
| 2   | Emergency stop switch | Connected to the controller to implement emergency stop function.                           |

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXIoQ1pHbfbph5j8XR5rk%2Fimg_e2cc41fa5bde.jpeg?alt=media)

* : **Power switch**. Short-press (in 0.5s) to switch on; Long press for 1.5s in\
  power-on state, the indicator light will flash red fast, and then release the button to turn off the power.
* : **Run/stop button**. When the robot is enabled and idle, long press to start\
  running; when the robot is running, short-press to stop running. You can configure the functions (trajectory playback by default) of the button in DobotStudio Pro.\
  **Trajectory playback**: Play back the last trajectory recorded by ◦ at the

| Indicator color | Status      | Definition                                                                                                       |
| --------------- | ----------- | ---------------------------------------------------------------------------------------------------------------- |
| Blue            | Steady on   | The robot arm has been started but not enabled.                                                                  |
| Blue            | Quick flash | The robot arm is starting.                                                                                       |
| Green           | Steady on   | The robot arm is enabled (not running).                                                                          |
| Green           | Slow flash  | Automatic running status (project debugging/running/pause, TCP motion commands except jog, trajectory playback). |
| Green           | Quick flash | Single running status (jog/runto in software) / drag mode / trajectory recording status.                         |
| Red             | Slow flash  | Joint brake switched on in disabled status.                                                                      |
| Red             | Steady on   | Alarm status.                                                                                                    |
| Yellow          | Steady on   | Collision detected.                                                                                              |

original speed. **Run projec**t: configure the project to be run via DobotStudio Pro. After the ◦ configuration is completed, you can run the project directly via this button, with no need to connect to the operating terminal. Powering off the robot will not clear the configuration.

* : **Enabling button**. When the robot arm is not enabled, long-press the button\
  to enable the robot. When the robot arm is enabled and idle, short-press the button to disable the robot.
* : **Hand-guiding button**. When the robot arm is enabled and idle, long-press\
  the button and the robot arm will enter the drag mode. Long-press the button again in the drag mode, and the robot arm will enter the trajectory recording mode. Short- press the button, and the robot arm will exit the drag mode and stop trajectory recording.
* : **Tool control button**. When the robot is disabled, enabled and idle or in the\
  drag mode, short-pressing the button can switch the status of the specified tool DO for controlling the end tool. You can configure the tool DO via the tool IO plug- in in DobotStudio Pro. **NOTE** Except for the power button, pressing a button and releasing it within 1.5s is a short press, and more than 1.5s is a long press. Some of the button functions are affected by the manual/automatic mode of the controller. See the instructions on mode switch in the DobotStudio Pro user guide for details.

#### 3.3 Coordinate system

**3.3.1 Joint coordinate system** The joint coordinate system is determined based on all motion joints. All joints are rotating joints.

![3.3 Coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHayKYILK6t5MNnA1ZL8z%2Fimg_79bd3d07e6a8.png?alt=media)

**3.3.2 User coordinate system** The user coordinate system is a custom workpiece or workbench coordinate system. The origin and the orientations of axes can be defined based on the site requirement to measure the points within the workspace and arrange tasks conveniently. The origin of the default user coordinate system is the intersection of the J1 axis with the lower surface of robot base. Y+ direction faces the shorter side of the base.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOzjfHcJq6QqJXh6xej7d%2Fimg_a377842e7569.png?alt=media)

**3.3.3 Tool coordinate system** The tool coordinate system defines the tool center point (TCP) and tool posture, of which the origin and orientations vary with the position and angle of the workpiece at the end of robot. The default tool coordinate system is determined based on the center point of the end flange. The Y+ direction is the opposite direction of the aviation socket, as shown in Figure 1-8.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLPEPv8CdIPFiBHJMptst%2Fimg_b527fd5b7a02.png?alt=media)

#### 3.4 Base interface

#### 3.4.1 Overview

The base interface panel is shown below.

![3.4.1 Overview](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpM4NvZyK3pyctee1bJTG%2Fimg_9a451e2344c4.png?alt=media)

| No. | Interface                       | Description                               |
| --- | ------------------------------- | ----------------------------------------- |
| 1   | Emergency stop switch interface | For connecting the emergency stop switch. |
| 2   | Digital I/O interface           | Universal DI/DO.                          |
| 3   | Power interface                 | For connecting matched power adapter.     |
| 4   | Encoder interface               | For connecting conveyor encoder.          |
| 5   | USB interface                   | For connecting WiFi module, etc.          |
| 6   | LAN interface                   | Default address: LAN1.                    |

**3.4.2 Emergency stop switch interface** The emergency stop switch is included in the shipping accessories, which has been connected to the wiring terminals. You just need to plug it into the corresponding interface.\
If you use a self-prepared emergency stop switch, please wire as below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FumC4d3zY74pYnyLWcUMH%2Fimg_b3dbe4d8a8ef.png?alt=media)

**3.4.3 Digital I/O interface** The digital I/O interfaces at the rear of the base include 16 universal DOs (500mA maximum single output current), 16 universal DIs, 2 24V power supplies and 2 GNDs, with a total current load capacity of 2A. DI and DO are both PNP type.\
The wiring of DI connected to a simple switch is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrJ13rWPWg5JR5TvJywoJ%2Fimg_58268b9af441.png?alt=media)

The wiring of DI connected to external PNP-type 3-wire sensor is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDTTfxIZTpNc0Hb8Ajqsf%2Fimg_6883304e0b51.png?alt=media)

The wiring of DO connected to external load is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLXTW5XRgW4BZxkpJoEu4%2Fimg_4b8a4c0304b7.png?alt=media)

**3.4.4 Encoder interface** The socket pins of the encoder interface are distributed and defined as follows.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6fm3coQcKFgNe4A3LGSe%2Fimg_db1d0c7e77f9.png?alt=media)

**3.4.5 Tool I/O interface** The tool interface is an aviation socket located on the side of the end flange. The socket pins are distributed and defined as follows.

| Pin | Name    | Definition                 |
| --- | ------- | -------------------------- |
| 1   | En A+   | ABZ encoder data interface |
| 2   | En A-   | ABZ encoder data interface |
| 3   | En B+   | ABZ encoder data interface |
| 4   | En B-   | ABZ encoder data interface |
| 5   | En Z+   | ABZ encoder data interface |
| 6   | En Z-   | ABZ encoder data interface |
| 7   | EX 5VDC | 5V power output            |

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVUFohsZxLAhquKbQ0Nfj%2Fimg_7a2e408c639c.png?alt=media)

The tool digital inputs and digital outputs are PNP type. The maximum output current for a single circuit is 500mA, with a total current load capacity of 2A. **WARNING** When connecting end tools, ensure that power interruptions do not cause any hazards, such as a workpiece falling off the tool. The robot on Magician E6 Mini Training Station connects the PLC controller, and air pump box via IO interfaces. The corresponding IO mapping is shown in the table below.

| Pin | Name | Definition       |
| --- | ---- | ---------------- |
| 1   | 24V  | 24V output       |
| 2   | DO 1 | Digital output 1 |
| 3   | DO 2 | Digital output 2 |
| 4   | DI 1 | Digital input 1  |
| 5   | DI 2 | Digital input 2  |
| 6   | GND  | Ground           |

#### 3.5 Total control unit

In Magician E6 Mini Training Station, Siemens PLC 200SMART controller is used to complete communication between PLC and external devices. The total control unit is equipped with Siemens 200SMART PLC and HMI touch screen, as shown in the figure below (on the left is the HMI touch screen, and on the right is the PLC below the touch screen). In which, the core component PLC (programmable logic controller) is a digital arithmetic controller with microprocessor for automation control, which can load control

| Pin   | Input             | Description       | Pin    | Output             | Description                                  |
| ----- | ----------------- | ----------------- | ------ | ------------------ | -------------------------------------------- |
| DI6   | R1 IN06           | Reserved          | I/O22  | R1 OUT06           | Material-Pushing Cylinder Extends / Retracts |
| DI7   | R1 IN07           | Reserved          | I/O23  | R1 OUT07           | Reserved                                     |
| DI8   | R1 IN08           | Reserved          | I/O24  | R1 OUT08           | Reserved                                     |
| I/O0V | IO Power Supply   | IO Power Supply   | I/O24V | IO Power Supply    | IO Power Supply                              |
| 0V    | Internal Power 0V | Internal Power 0V | 24V    | Internal Power 24V | Internal Power 24V                           |

instructions into memory at any time for storage and execution. A PLC consists of functional units such as functional units such as CPU, instruction and data memory, input/output interface, power supply, digital-to-analog conversion, etc. Quick commissioning and control for the total control system can be implemented through HMI, greatly improving the application efficiency and accuracy of the device.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm0BPk31KQFZVOgz4VP4G%2Fimg_7ba406e01454.jpeg?alt=media)

PLC is used for controlling the start, reset, stop, and sensor sensing, three-color light, buzzer, and conveyor of the system. The IO comparison between the PLC and the robot and external devices is as shown in the table below (Module Model: 200SMART).

#### 3.6 Air pump box

Magician E6 Mini Training Station adopts mini air pump box. Compared to traditional gas supply modes with loud noise, large volume, and high cost, this air pump box provides users with a more convenient and simpler way of gas supply and usage. The air pump box can provide an air pressure range of -70 – 110 kPa. Its exterior is designed exquisite, facilitating it to directly adapt to the robot through the I/O control interface, plug and play, suitable for most daily scenarios of suction cups and flexible gripper applications.\*\*\*\*

| Pin | Input | Description       | Pin | Output | Description                   |
| --- | ----- | ----------------- | --- | ------ | ----------------------------- |
| 0   | I0.0  | Start             | 0   | Q0.0   | Green Light                   |
| 1   | I0.1  | Stop              | 1   | Q0.1   | Yellow Light                  |
| 2   | I0.2  | Reset             | 2   | Q0.2   | Red Light                     |
| 3   | I0.3  | Manual/Auto Mode  | 3   | Q0.3   | Conveyor Start                |
| 4   | I0.4  | Emergency Stop    | 4   | Q0.4   | ROB Start                     |
| 5   | I0.5  | Material Detected | 5   | Q0.5   | ROB Pause                     |
| 6   | I0.6  | Reserved          | 6   | Q0.6   | ROB Enable                    |
| 7   | I0.7  | Reserved          | 7   | Q0.7   | ROB Stop                      |
| 8   | I1.0  | ROB Enable        | 8   | Q1.0   | ROB Clear Alarm               |
| 9   | I1.1  | ROB Stop Status   | 9   | Q1.1   | Allow ROB to Unload Materials |

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FobNRhRJr8RUQnWGN8IIb%2Fimg_0786fb4faffd.jpeg?alt=media)

#### 3.7 Control buttons and indicators

The control buttons include “Start”, “Stop”, “Reset”, “Emergency stop” and “Manual/Auto Mode”, totaling 5 buttons. Emergency stop controls the entire machine table and the robot to power off, while the other 4 buttons can be used to set the running status of the device. If the robot body fails to be powered on, it may due to the “Emergency stop” button being pressed. The control buttons are as shown below.

![3.7 Control buttons and indicators](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F60fxsZmJn7tW9G4kKyNM%2Fimg_73277f407e89.jpeg?alt=media)

**Description of Operational Buttons:** (1) "Emergency Stop" Button: Pressing the emergency stop button immediately halts the robot and conveyor operation. (2) "Start" button (green light): Used to start the device after initialization is complete. This button functions the same as the "Start" button on the touchscreen. When pressed, the "Start" button light stays steadily lit. After initialization, the "Start" button light blinks. (3) "Stop" Button (red light): Stops the device during operation. This button functions the same as the "Stop" button on the touchscreen. The red light turns on when the button is pressed, or the device stops due to a fault. (4) "Reset" Button (yellow light): Clears device alarms, functioning identically to the "Reset" button on the touchscreen. The yellow light remains steadily lit when the button is pressed. The light flashes when the device triggers an alarm condition. (5) "Manual/Auto Mode" Switch Button: When switched to the left (Manual Mode), operators can test conveyor belts and robot interaction signals. When switched to the right (Auto Mode), it allows for device initialization. After successful initialization, pressing the Start button will enter automatic operation mode.

#### 3.8 Conveyor

The feeding conveyor is mainly used to push materials from the loading plate onto the conveyor belt to implement the transport of the materials between different positions. The conveyor is driven by a DC motor, and the belt operates at a fixed speed to transport various materials. Additionally, the conveyor blet is equipped with a photoelectric sensor and a pneumatic pusher cylinder, which can precisely detect the position of materials on the belt and assist robots in locating and gripping the materials. This enhances both the efficiency and accuracy of material handling.

![3.8 Conveyor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPB4TBC6BRfQSHbZypMjF%2Fimg_8369a19b192a.jpeg?alt=media)

### 4. Software Installation

#### 4.1 Install the robot control software

(1) Enter the official website of DOBOT

1. Click to open Download Center in the browser, enter the official download center of DOBOT.

![4.1 Install the robot control software](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVdYuK2U7usOIJBfXy7NX%2Fimg_475ab516ac14.png?alt=media)

2. In the “Download Center” interface, click on “Software”, find DobotStudio Pro in the left search bar, click on in the upper right corner, and download the robot control software.

![4.1 Install the robot control software](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKONs813iW7x3sACkTfkl%2Fimg_0e79ba0cc1db.png?alt=media)

(2) Enter the installation wizard interface After the software is downloaded, double click to open, select the installation language, and click**Start Installation**.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIqWMjHbHMtJsumlViG0%2Fimg_d7d7c5752708.jpeg?alt=media)

(3) Select the installation path In the installation interface of the software, click on **custom** and **Preview** to select the installation directory.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOqhDIzMk4MpVQzNbzCTY%2Fimg_c94fcc83795d.jpeg?alt=media)

(4) Start to install the software Click on **One click installation** to start installing DobotStudio Pro.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfLkyPG0TDGCTQSml0jBX%2Fimg_4021e205fd2e.jpeg?alt=media)

(5) The installation is completed After the installation is completed, click on **Experience Now**, to enter the software interface for experience.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F51VlpKDRA1vl3A938nE9%2Fimg_4749ed5beec1.jpeg?alt=media)

(6) Learn the software interface After the software is connected to the robot, the main interface appears as shown below:

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbCe0qR48854SYdJ2WJmB%2Fimg_efab2f57fd03.jpeg?alt=media)

| No. | Description                                                                                                                                                                                                         |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Click to open the main interface. The color of the robot icon synchronizes with the indicator on the robot. If a robot alias has been set, it is displayed below the icon; otherwise the model number is displayed. |
| 2   | Click to open Settings to set parameters related to robot installation, motion, safety, etc.                                                                                                                        |
| 3   | Click to open Log to view alarms and logs.                                                                                                                                                                          |
| 4   | Click to open Dobot+ to install and use Dobot+ plugins.                                                                                                                                                             |
| 5   | Click to open Application for programming via Blockly or Script.                                                                                                                                                    |
| 6   | Click to open Help and feedback to view the software user guide and provide feedback.                                                                                                                               |
| 7   | Click to open the control panel for installed plugins.                                                                                                                                                              |
| 8   | Click to open Jog panel to jog or step the robot.                                                                                                                                                                   |
| 9   | Click to open Monitor panel to monitor the robot's I/O and global variables.                                                                                                                                        |

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTA0a7s57Nc6ELKCg1D3L%2Fimg_0b976ba14072.png?alt=media)

**NOTE** Please refer to the corresponding user guide for the specific functions of each tool.

| No. | Description                                                                                                             |
| --- | ----------------------------------------------------------------------------------------------------------------------- |
| 10  | Used to display and set the global speed, which controls the robot speed.                                               |
| 11  | E-Stop button. Press this button in an emergency, and the robot stops immediately.                                      |
| 12  | Used to display running background process and status.                                                                  |
| 13  | This panel is used to enable the robot, switch user roles, set device information, display load and safety information. |
| 14  | 3D model of the robot, synchronized with the real robot's posture.                                                      |
| 15  | Robot S/N, software and firmware version information. Send a screenshot of this when contacting support.                |
| 16  | Click to view the robot's current status, including voltage, current, and temperature.                                  |

#### 4.2 Installing Siemens PLC software

(1) Download the Latest PLC Software Package Search the Siemens official website in the browser for PLC software. Scroll down the webpage to see “Download & Support” - “Configuration Software,” and find “Micro/WIN SMART V2.8.2.1” to download the software installation package. If you need to study PLC, you can download materials in the documentation section on the same page. The software installation package and documentation materials can be downloaded as shown in the figure below.

![4.2 Installing Siemens PLC software](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5TXLfHRMuXYTYniumJ06%2Fimg_6db71e1aff6f.png?alt=media)

**NOTE** The PLC/HMI software used in the E6 Starter Training Platform is free of charge, and you are not required to make any purchases. (2) Locate the PLC Software Locate and extract the installation package. In the extracted folder, find the file named "STEP-7-MicroWIN-SMART-V2.8.2.1.iso".\
Double-click to open**STEP\_7\_MicroWIN\_SMART\_V2.8.2.1**,\*\*\*\*and then locate the **setup.exe**file.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZkZQL44cAnRn03ak9sNY%2Fimg_720af0e247ac.png?alt=media)

(3) Select the Language Here, "English" is used as an example. Click "OK" to confirm.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhRkZCHCulfiwhy49eDt8%2Fimg_7cfaee25a3a3.png?alt=media)

(4) Installation Wizard Click "Next" and follow the installation wizard to install the software.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj3ZFpaWNFkEyyEhgZ4MR%2Fimg_bc24ce5edca2.jpeg?alt=media)

(5) Accept the License Agreement On the selection interface, check "I accept the license agreement" and then click "Next".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx6oGHfZj6wFcDtpdZEfc%2Fimg_94068875b531.png?alt=media)

(6) Choose Local Installation Click "Browse..." to customize the installation path for the software. Then, click "Next" to begin the installation process.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHWdlP2kcWTnjfKJ6hFZ8%2Fimg_d93bb71b749f.png?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwKxsQUyKtO6VIlJtsG69%2Fimg_c8b700ad2fde.jpeg?alt=media)

(7) Installation Complete Check "Yes, I want to restart my computer now" and click "Finish" to exit the installation wizard.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6aoOGHx4R6tzy1I6Tom0%2Fimg_185b54d3dd7c.png?alt=media)

#### 4.3 Installing Siemens HMI software

(1) Download the Latest Software Package Search for Siemens official website in the browser for HMI software. Scroll down the webpage to see "Download & Support" – "SMART LINE PLUS Configuration Software", then click the**WinCC flexible SMART V5 SP1 Update1** download link to download the software installation package.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAZynOBaRkwBFeVLXBzRw%2Fimg_1a065db68548.png?alt=media)

**NOTE** The software is updated periodically. If you are unable to obtain the installation package, please contact technical support for assistance. (2) Locate the HMI Software\*\*\*\* Locate and extract the installation package. In the package folder, find the file **WinCC-** **flexible-SMART-V5-SP1-Update1**, and double-click to open the **WinCC\_flexible\_SMART\_V5SP1\_Upd1.exe** file.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEInVpR77z9H8sFGqDE69%2Fimg_6ac5ff2e8fbe.jpeg?alt=media)

(3) Installation Wizard Click "Next" and follow the installation wizard to install the software.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1xDQKGR5c1QVpe89WTBo%2Fimg_d6d57b8f62a8.png?alt=media)

(4) Accept the License Agreement On the selection interface, click "Yes".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuU3BB64z3FDhL4W78seq%2Fimg_5329130c4177.png?alt=media)

(5) Click "Next" then click "Browse..." to customize the installation path for the software. After setting the path, click "Next" again to start the software installation.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaMqtisZ85mymw1kzvUpj%2Fimg_7e67d5ef9117.png?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlKzHsSaW8hoTcTY9qt87%2Fimg_abbd42938e32.png?alt=media)

(6) Installation Complete Click "Finish" to exit the installation wizard.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuyLwYVr1O36qiLhAVGX0%2Fimg_266423cfee0b.png?alt=media)

## Chapter 2 Robot Handling Application

### 1. Introduction

The task of the robot handling application is to transfer two square workpieces from a loading plate onto a conveyor belt using the robot arm and then return the workpieces from the conveyor belt back to the loading plate. During system operation, the device can be controlled via the touch screen buttons or the buttons on the control box. These include stop, reset, and start functions. Additionally, the operational status of the device is displayed through the status indicators on the touch screen's main interface.

![1. Introduction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F60fxsZmJn7tW9G4kKyNM%2Fimg_73277f407e89.jpeg?alt=media)

The robot handling application is controlled via a touch screen and offers two operational modes: manual control and automatic mode. Manual Control: This mode is primarily intended for debugging. To activate this mode, switch the fifth black button on the control box to the left (manual mode), then use the buttons on the touchscreen's manual control interface to manage the start and stop functions of the conveyor belt and robot. Automatic mode: first switch the fifth black button on the control box to the right (automatic mode). Press the "Start Initialization" button on the main interface of the touchscreen. Once the status interface shows "Initialization Complete" and the green light turns on, press the "START" button on the control box or the "Start" button on the touchscreen to enable automatic operation. The status interface on the touchscreen will display "Running Automatically" "Paused" or "Alarm" to indicate the system's state, corresponding to the green, yellow, and red indicator lights, respectively. First, the robot moves to a safe point and initiates the conveyor belt’s forward motion. The PLC sends a signal to the robot indicating “Allow ROB to Unload Materials onto Belt”. Upon receiving this signal, the robot begins picking up the first material from the loading plate and placing it onto the belt. After completing the placement, the robot sends a “ROB Material Unload to Belt Complete” signal back to the PLC and proceeds to pick the second material from the loading plate for transfer to the conveyor belt. When the position detection sensor detects that the material has reached the specified location, the conveyor belt stops. The PLC then sends a signal to the robot indicating “Allow ROB to Pick Material from Belt”. Upon receiving the signal, the robot picks up the material from the conveyor belt and transfers it to the third empty position on the loading plate. After the transfer, the robot sends a “ROB Material Pick from Belt Complete” signal back to the PLC. Then, the conveyor belt resumes operation, transporting the second material. The cyclic sensor detects the robot's material pickup process, and eventually, the material is transported to the fourth empty position on the loading plate. The conveyor belt then resumes forward motion, and the PLC continues to send the signal “Allow ROB to Unload Materials onto Belt” to the robot. Upon receiving the signal, the robot picks up the third material from the loading plate and places it onto the conveyor belt. After completing the placement, the robot sends the “ROB Material Unload to Belt Complete” signal back to the PLC. The robot then proceeds to pick up the fourth material from the loading plate and place it onto the conveyor belt. When the position detection sensor detects that the material has reached the designated location, the conveyor belt stops. The PLC sends a signal to the robot indicating "Allow ROB to Pick Material from Belt". After receiving the signal, the robot picks the material from the conveyor belt and transfers it to the first empty position on the loading plate. Once the robot completes the transfer, it sends a “ROB Material Pick from Belt Complete” signal back to the PLC. Meanwhile, the conveyor belt resumes operation and begins transporting the material for the fourth position on the loading plate. The cyclic sensor detects the robot's material pickup process, and eventually, the material is transported to the second empty position on the loading plate, thereby completing one full automatic operation cycle.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl2trckmqS0Op5AW3TNva%2Fimg_84b6fd3fb7ab.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjTml8uY6r07TYW5Mjnf1%2Fimg_8ddbee261934.jpeg?alt=media)

### 2. Hardware Description

#### 2.1 Installation of Magician E6 electric suction cup

Install the suction cup onto the robot's end effector according to the installation guide for Magician E6 electric suction cup.

![2.1 Installation of Magician E6 electric suction cup](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyZL5uzrj9gyiLKePSKrK%2Fimg_c4582d2ecfe5.jpeg?alt=media)

**2.2 Wiring instructions**

**2.2.1 External interface description of the PLC box** The interfaces of the PLC box are shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fb9NN8x1zR1YvSJAl4OOX%2Fimg_8c25b9880b65.jpeg?alt=media)

| No. | Name                | Definition                               |
| --- | ------------------- | ---------------------------------------- |
| 1   | Debug ethernet port | Used for external connection to the PLC. |
| 2   | 10P port            | Used for connecting I/O signals.         |
| 3   | 9P port             | Used for connecting input signals.       |
| 4   | 8P port             | Used for connecting output signals.      |
| 5   | 6P port             | Used for connecting I/O signals.         |
| 6   | Power interface     | Used for connecting to mains power.      |

**2.2.2 Cable wiring instructions** **1. Wiring Connections Required for a PLC-Based System (PLC as the Main**

**Controller):** (1) 10P-IO Cable The 10P-IO cable primarily connects the button box with the PLC's IO signals. It directly plugs into the 10P port of the PLC box. The wiring diagram is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff74pUDLYd7joXfTDA5KR%2Fimg_ec771087bd23.jpeg?alt=media)

(2) 6P-IO cable The 6P-IO cable is mainly used to connect the conveyor belt with the PLC for controlling and detecting IO signals. It directly plugs into the 6P port of the PLC box. The wiring diagram is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPd015NLuF8ZemB9woYoc%2Fimg_de0dfc063ec8.jpeg?alt=media)

(3) 8/9P-IO cable The 8/9P-IO cables are primarily used to connect the PLC with the robot for IO signal interaction. The 8P-IO cable handles the robot's output signals, while the 9P-IO cable handles its input signals. Both cables are directly plugged into the 8P and 9P ports of the PLC box, respectively. The black 20P connector directly plugs into the 20P port located on the right side of the robot's base. The wiring diagram is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLmkzC1raeimLigmOswBC%2Fimg_0d835fd09406.jpeg?alt=media)

(4) Air Pump Box Cable (With PLC) The air pump box cable is primarily used to connect the robot's output signals to control the air pump box. The black 20P connector is directly plugged into the 20P port located on the left side of the robot's base, while the black 4P connector is directly plugged into the electrical interface of the air pump box. The wiring diagram is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FClIOw8iYlXfFyrTijjOY%2Fimg_f1abe57f81a6.jpeg?alt=media)

**2. Wiring Connections Required for Non-PLC System (Robot as Master Controller)**

**(For Reference Only)** (1) 10P/6P-IO Cable The 10P-IO cable is primarily used to connect the button box to the robot arm’s IO signals. The 6P-IO cable is used to connect the conveyor belt to the robot for control and IO signal detection. The black 20P connector is directly plugged into the 20P port located on the left side of the robot's base. The 10P-IO cable female connector is directly plugged into the button box’s 10P male connector, while the 6P-IO cable female connector is directly plugged into the conveyor’s 6P male connector. The wiring diagram is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV2GUyvc7fR4PN0Nbme0m%2Fimg_71a5e07ccd11.jpeg?alt=media)

(2) Air Pump Box Cable (Without PLC) The air pump box cable is used to connect the robot’s output signals to control the air pump box. The wiring process differs slightly from setups with PLC as the main controller. First, directly plug the black 20P connector into the 20P interface on the right side of the robot base. Then, disconnect the two wires labeled "Vacuum" and "Pressure" from the 20P connector and connect them to the DO5 and DO6 signal interfaces of the 20P connector on the left side of the robot base, respectively. The two wires labeled "24V" and "GND" on the right 20P connector should remain unchanged. The wiring diagram is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdMOxIqGZD6XTRs2JVsCe%2Fimg_d6cfb0ff2336.jpeg?alt=media)

**2.3 IO configuration instructions** The IO configuration for the robot's outputs in the robot handling application is shown in the table below. The IO configuration for PLC inputs is outlined is shown in the table below.

| No. | Output | Description                        |
| --- | ------ | ---------------------------------- |
| 1   | DO05   | Material-pushing Cylinder Extends  |
| 2   | DO06   | Material-pushing Cylinder Retracts |

| No. | DI       | Description                    |
| --- | -------- | ------------------------------ |
| 1   | PLC IN01 | Start                          |
| 2   | PLC IN02 | Stop                           |
| 3   | PLC IN03 | Reset                          |
| 4   | PLC IN04 | Manual/Auto Mode               |
| 5   | PLC IN05 | Emergency Stop                 |
| 6   | PLC IN06 | Material in Position Detection |
| 7   | PLC IN09 | ROB Enable Status              |

The IO configuration for PLC outputs is shown in the table below.

| No. | DI       | Description                      |
| --- | -------- | -------------------------------- |
| 8   | PLC IN10 | ROB Stop Status                  |
| 9   | PLC IN11 | ROB Running Status               |
| 10  | PLC IN12 | ROB Alarm Status                 |
| 11  | PLC IN13 | ROB Completed Unloading Material |
| 12  | PLC IN14 | ROB Completed Picking Material   |

| No. | Output    | Description                              |
| --- | --------- | ---------------------------------------- |
| 1   | PLC OUT01 | Green Light                              |
| 2   | PLC OUT02 | Yellow Light                             |
| 3   | PLC OUT03 | Red Light                                |
| 4   | PLC OUT04 | Conveyor Start                           |
| 5   | PLC OUT05 | ROB Start                                |
| 6   | PLC OUT06 | ROB Pause                                |
| 7   | PLC OUT07 | ROB Enable                               |
| 8   | PLC OUT08 | ROB Stop                                 |
| 9   | PLC OUT09 | ROB Clear Alarm                          |
| 10  | PLC OUT10 | Allow ROB to Unload Materials            |
| 11  | PLC OUT11 | Allow ROB to Pick Material from Conveyor |

### 3. Program Debugging

#### 3.1 Preparation

**3.1.1 Powering on the Magician E6 Mini training station** Connect the power plugs of the Magician E6 Training Station and the robot to the power supply, then turn on the power switch.

![3.1 Preparation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff6B89P6ZEacNh45LOffa%2Fimg_2666042714de.jpeg?alt=media)

**3.1.2 Turning on the air pump box** Turn on the power switch of the air pump box, and rotate the control button to the "Auto" position.

![3.1 Preparation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgR4iZx0szunX40qkllf9%2Fimg_d2d8fd4feb95.jpeg?alt=media)

**3.1.3 Material preparation** Place two square workpieces onto positions 1 and 2 of the loading plate.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqOG4dKNA0WufFtee3qd2%2Fimg_d8b2975e1669.jpeg?alt=media)

**3.1.4 Powering on the robot** Check if the robot base's power plug is securely connected and if the power switch is turned on. If it is not turned on, press the start button.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFl5xqI3dWH9ohBFicR9D%2Fimg_9dc64756c323.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpmRiKAeTxagusXoy2XvK%2Fimg_b3dd2bcdccd5.jpeg?alt=media)

**3.1.5 Ethernet cable connection** Connect one end of an Ethernet cable to the LAN1 port on the robot base, and the other end to the upper Ethernet port of the PLC box. Then, connect another Ethernet cable with one end plugged into the lower Ethernet port of the PLC box and the other end connected to the computer.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FByw7tgyLIt42eXG17XWk%2Fimg_c78a2bd80fc3.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fax1femkN8jD8pjivy98l%2Fimg_e2709aab4588.jpeg?alt=media)

**3.1.6 Changing the PC IP address** Open the computer's Control Panel and navigate to "Network and Internet/Network and Sharing Center" to access the Network and Sharing Center window. Click on “Ethernet”, select “Properties”, and open the Ethernet properties page. Double-click “Internet Protocol Version 4 (TCP/IPv4)” to enter the "Internet Protocol Version 4 (TCP/IPv4) Properties" interface. Reset the PC's IP address as shown in Figure below. The robot’s default IP address is “192.168.5.1.” Modify the PC's IP address to any unused IP address in the same subnet as the robot. Ensure that the subnet mask and default gateway match those of the robot. Here, take "192.168.5.222" as an example.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIRokJhHOjUnuLnuXNBZB%2Fimg_d6e5a998a5fe.png?alt=media)

#### 3.2 Robot debugging

**3.2.1 Connect DobotStudio Pro with the robot** Double-click on the DobotStudio Pro 4.6 icon to open the software. Once inside DobotStudio Pro 4.6, the software will automatically scan for robots and display the search results on the interface with the robot labeled as "Magician E6". Click "Connect" on the right side of the device to establish the connection. **NOTE** The IP address provided is a virtual example intended solely for manual writings. Please refer to the actual IP address in real-world use. The same applies to similar instances throughout the operating guide.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqzUGzhPjGmLR2ENE17gD%2Fimg_822e4b14362e.jpeg?alt=media)

Once the connection is successful, the "Magician E6" interface will appear, displaying information related to the E6 and its 3D model. Additionally, a "Disconnect" option will be shown on the right side of the robot model "Magician E6".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLIqtj0peXBqcDTiua3AO%2Fimg_7671a7a7d08b.jpeg?alt=media)

**3.2.2 Enable the robot** Click on the icon next to Enable in the left toolbar of the DobotStudio Pro main interface. In the pop-up “Load Enable Settings” window, modify the parameter values based on actual requirements, and then click "Enable". The "Enable" switch in the Magician E6 interface will change to .

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7BBiqXnGyiru3wGT0xf9%2Fimg_21343e828141.png?alt=media)

**3.2.3 Speed setting** Click the “Speed” button on the top toolbar in the DobotStudio Pro interface, and set the speed to 34%.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAR9oK7StFEjHfO2xpxb1%2Fimg_e7bc155317be.jpeg?alt=media)

**3.2.4 Adjusting the robot posture** Adjust the robot's posture via the control panel to match the position. In this posture, the robot's joint coordinates are "0, 0, -90, 0, 90, 0".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVICRFV6qU1wetetWvAl2%2Fimg_ce77e439bad6.jpeg?alt=media)

**3.2.5 Import project** \*\*Step 1:\*\*In the main interface of the DobotStudio Pro software, click on "Application" and select "Script Programming" to enter the "Programming" interface.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FENPV4qkGnnmeN7WLW9fJ%2Fimg_36b8ecae61c4.jpeg?alt=media)

\*\*Step 2:\*\*In the "Script Programming" interface, click the dropdown menu icon "" and select "Import Project". Then, choose the example project folder for the robot handling application and click to open it. This will import the robot handling application into DobotStudio Pro.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fiv42uCXDgXacWAr113gi%2Fimg_9045fb4347f4.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw3quRgTcQ4rNbTbqvPoy%2Fimg_2ccfb1951ba6.jpeg?alt=media)

**3.2.6 Saving the project** Click the save icon "", then in the pop-up dialog box, name the project and click "Save".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzRNnNPfR6e2TZYRI45mk%2Fimg_64d93ae6de8f.jpeg?alt=media)

**3.2.7 Debugging points** The robot application involves a total of 4 points. The debugging steps are as follows:

**User coordinate system description** Currently, two user coordinate systems, 1 and 0, are being used. Here, we provide a brief explanation about the selection of the user coordinate system in the current demo. For detailed usage instructions, click "Help and Feedback" in the top toolbar to open the help documentation. Locate 10 Settings → 10.3 Coordinate System Management → 10.3.1 User Coordinate System. As shown in the figure below, establish, modify, and use the user coordinate system according to the document guidelines.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmfESljKgxPLQpj9Nkt3J%2Fimg_8dae57afd747.png?alt=media)

① Selection and use of user coordinate system “0” The user coordinate system "0" is the system's default setting. It is centered on the robot base, as shown in the figure below, and does not require configuration. The belt unloading point and the picking point use the user coordinate system “0”.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUo1KgmhnUNIol8Ms1I4O%2Fimg_5a2de219cf61.jpeg?alt=media)

② Selection and Use of User Coordinate System "1" The user coordinate system "1" needs to be established after installing the material storage platform. To prevent errors in the platform's position, a user coordinate system "1" must be established each time the platform is assembled or disassembled. HOME point and storage position 1 use user coordinate system "1". To establish a user coordinate system, the three-point positioning method is required. The order is from 1 to 3, with the three points shown as red indicators in the diagram below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FohVyREHufg094isiuyAD%2Fimg_869e9a90fc0c.jpeg?alt=media)

**Calibration process:**\
a. First, it is necessary to attach a sharp object to the end of the robot, as shown in the figure below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg7Dx48jP8xQtx7jsyPuc%2Fimg_80e29bccf5af.jpeg?alt=media)

b. After installing the end component, click Settings → Coordinate System Management → User Coordinate System → Select the coordinate system with ID 1 → Click Modify → Click Three-Point Settings. After that, click Jog in the top right corner.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FELPVjHM5Psy3AtDbOIK0%2Fimg_f3df51b5aca8.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVGD1zhCPF81IHO0Wm0NV%2Fimg_4a63590cb49d.png?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSq9bPRtwrHGuhBx9FoAw%2Fimg_414f3c4adf7b.jpeg?alt=media)

Move the robot to the position shown in the figure below and obtain the P1 coordinates. The operation to obtain points P2 and P3 is the same.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FptKFZU2ZTcm8mCJzaJYO%2Fimg_a5b4d1498ec9.jpeg?alt=media)

Then move the robot to the position shown in the figure below to obtain the P2 coordinates.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2GniqVkOOEcs3OpZxs8U%2Fimg_733636ef8b34.jpeg?alt=media)

Finally, move the robot to the position shown in the figure below to obtain point P3.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmwwIwtmqeNJbgavfGf42%2Fimg_bcdde5203a6f.jpeg?alt=media)

After confirming that all three points are correct, click “Confirm” in the upper right corner, then save. The user coordinate system “1” will be successfully created.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FL0wMRNEQSoqFjxVaFCpM%2Fimg_08c060492f2f.png?alt=media)

(1) Updating the Home point P1 ①. Use jog control to move the robot to the position between the conveyor belt and the storage area.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDATkMWx9y2UpPnPG0c6p%2Fimg_740d250d2f45.jpeg?alt=media)

②. In DobotStudio Pro, click "Points" page to enter the saved point list interface, select "P1" and click "Overwrite" in the upper-right corner. As shown in the figure below, click to save the program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHGqDaCE5i6Hs9GoXEbGV%2Fimg_872b89ef59b8.png?alt=media)

(2) Update the position P2 at storage location 1 ①. Move the robot to position 1 using jog control, as shown in Figure below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg6OQg58Zl4guJ0x4wQFc%2Fimg_022705647fe6.jpeg?alt=media)

②. In DobotStudio Pro, click “Points” to enter the point list interface, select “P2” and click “Overwrite” in the upper right corner. As shown in Figure below, click to save the program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnsH5D2J5NcVVC1kK1Xgi%2Fimg_22e76a7563ce.jpeg?alt=media)

**NOTICE** The P2 point needs to be set based on User Coordinate System 1. If another user coordinate system is used, the program will not run properly. (3) Updating the Belt Unloading Point P3 ①. Use jog control to move the robot to the belt unloading point.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FseCqAUB2rJ9DaAsRWCZq%2Fimg_266e2cb95809.jpeg?alt=media)

②. In DobotStudio Pro, click "Points" to enter the saved point list interface, select "P3" and click "Overwrite" in the upper-right corner. As shown in Figure below, click to save the program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fo4xWBs5bBxFv9PcbcrNt%2Fimg_79befc1f043c.jpeg?alt=media)

(4) Updating the Belt Picking Point P4 ①. Use jog control to move the robot to the belt picking point.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOabSJf3wy2xjJjbM42iq%2Fimg_1ed3716e3868.jpeg?alt=media)

②. In DobotStudio Pro, click “Points" to enter the saved point list interface, select "P4" and click "Overwrite" in the upper-right corner. As shown in Figure below, click to save the program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fck23fIVuoECrHjxpjNzo%2Fimg_af3f1633c047.png?alt=media)

#### 3.3 Importing the PLC program

\*\*Step 1:\*\*Open the STEP 7-MicroWIN SMART software.

![3.3 Importing the PLC program](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMXQ16tRWQMUzVSBBH9zW%2Fimg_77c4fbd9e2ad.png?alt=media)

**Step 2:** Click "File" and navigate to the storage location of the PLC program. Select the program named "Magician E6 Training Station EN" and open it.

![3.3 Importing the PLC program](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK6JDG1j1A6AaHRVuHsYV%2Fimg_2f01889acd9d.png?alt=media)

**Step 3:** Click "Communication" in the menu bar, then select "Communication Interface" from the dropdown menu and choose the "TCP/IP" network interface card for your programming device. Next, click "Find CPUs". Once the CPU is found, its IP address will be displayed. Verify if the PLC IP address belongs to the 192.168.5.\* network segment.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fhabk9HBnUx79pYb9Vq93%2Fimg_96a7b99f0384.png?alt=media)

If the IP address doesn't belong to the required segment, it needs to be updated. For example, set the PLC IP address to "192.168.5.10". Click "Edit" and then the IP address and subnet mask will become editable. Modify the values directly, and once the changes are completed, click "Edit" again to apply the update. The fields will now become non- editable, indicating that the IP address change is successful.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUpgvRmjQJ75hz6oRVpw0%2Fimg_a5f62744241b.png?alt=media)

**Step 4:** Expand the "Program Block" folder, and double-click "Main(OB1)" to open the main program, to check whether the opened program needs to be downloaded to the PLC. If correct, proceed to the next step; otherwise, reopen the proper PLC program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWAKlQQW1nFLbHg58wO3l%2Fimg_605230f92496.png?alt=media)

**Step 5:** Click "Download - All" on the top toolbar. In the "Download" popup window, click "Download".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuBROtoIXHgzPZB9bVzUQ%2Fimg_b742dac6df23.png?alt=media)

**Step 6:** Once the download is complete, click "Close" to finish the process.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ8T7mlb6LeNwvJqUSpOM%2Fimg_c4fa171e0697.png?alt=media)

**Step 7:** In the menu bar, click "Debug - Program Status" to switch the program to online mode. As shown in the figure below, it indicates that the PLC program has been successfully downloaded. You can now proceed with online debugging and monitoring.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkfBH0KB7oyMBS5b7eMjL%2Fimg_dcb48164212c.png?alt=media)

#### 3.4 Importing the HMI program

**Step 1:** Open the WinCC flexible SMART V5 software.

![3.4 Importing the HMI program](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuUw0m12oytxrWzKxMoQF%2Fimg_64d9998eae59.jpeg?alt=media)

**Step 2:** Click "Open an existing project", navigate to the storage location of the HMI program. Select the program named "Magician E6 Training Station", and open it.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjD3V2mErchYYLHAt79uv%2Fimg_617d9004eb22.jpeg?alt=media)

**Step 3:** Click "Download" in the menu bar. In the "Download and communication settings" popup window, select "Communication Interface" from the dropdown menu, choose "Qualcomm Atheros" as the network interface card, and then start searching. Once the HMI is found, its IP address will be displayed. Verify if the HMI IP address belongs to the 192.168.5.\* network segment.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFGqheHAlCQ99svNsmTkc%2Fimg_c3411539c02f.jpeg?alt=media)

If the IP address doesn't belong to the required segment, it needs to be updated. For example, set the HMI IP address to "192.168.5.11". Click the address field beneath "IP address" and the IP address and subnet mask fields will become editable. Modify the values directly, and once the changes are completed, click "Apply" to save the updates. This will successfully update the IP configuration.\*\*\*\*

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgiWhW9olEvdiGFsqg6Ze%2Fimg_af23df1c73eb.jpeg?alt=media)

**Step 4:** Expand the "Screens" section. Verify whether the opened program is the one to be downloaded to the HMI. If it is correct, proceed to the next step; if not, reopen the correct HMI program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F68fB4ajLDnuRbOCEDYbZ%2Fimg_d8aad537a025.jpeg?alt=media)

\*\*Step 5:\*\*In the "Download and communication settings" popup window, click "Download".

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGEgt45AFKeXEnVSLt3oa%2Fimg_0bb5875dce84.jpeg?alt=media)

**Step 6:** The download progress is displayed below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNaPEKxye8AkeVxPvfKd2%2Fimg_fba8ca884d03.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBuiacVKTkmDxfqAjXP5G%2Fimg_b58b53fd2af9.jpeg?alt=media)

**Step 7:** Once the download is complete, a "Transfer Successful" message will be displayed.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyZFE1J8pvPgKfO2FxS2x%2Fimg_0875df2b46b3.jpeg?alt=media)

#### 3.5 System Integration debugging

(1) Open the PLC program for the project. In the menu bar, select "PLC" and then "RUN" to enable CPU operation mode.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZgK2MnfU21M9RuIcVCPJ%2Fimg_5a5af7c68ae2.png?alt=media)

(2) Switch the black rotary switch on the control box to automatic mode. Turn the black rotary switch to the right to enter automatic mode.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKsuLLNX8csU55vKv0QjF%2Fimg_e2ae831cd169.jpeg?alt=media)

(3) Run the Offline Project ①. Program Selection After opening the software, set the robot to Remote IO mode (ON), then select the program intended for the project's operation.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA5rN6rbjlGaAU1TNFiKa%2Fimg_6107faaa4161.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fya6WmvSjsroNJxyPQj2K%2Fimg_c17117e57416.png?alt=media)

②. IO Configuration Configure the IO settings according to the requirements.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnlqDvJecQTD1A0smzpkI%2Fimg_8450246c92c8.jpeg?alt=media)

(4) Switch the touchscreen interface to the main interface. Tap the "Start Initialization" button on the touchscreen. The robot will move back to its safe position, and the "Initialization Completed" indicator on the touchscreen will turn green. Meanwhile, the green light on the "Start" button on the control box will begin to flash. At this point, press and hold the "Start" button to transition the system into automatic operation mode. The "Automatic Operation" indicator on the touchscreen will light up green. Observe whether the system operates as follows:

1. The robot first moves to the safe position and initiates the forward movement of the conveyor belt. The PLC sends an "Allow ROB to place materials onto the conveyor belt" signal to the robot. Upon receiving the signal, the robot picks up the first material from the loading plate and places it onto the conveyor belt. After completing the task, the robot sends a "ROB Completed Unloading Materials on Belt” signal back to the PLC. Subsequently, the robot picks up the second material from the loading plate and places it onto the conveyor belt.
2. When the position sensor detects the material in position (as shown in Figure 2- 2), the conveyor stops moving. The PLC sends an "Allow ROB to Pick Material from Belt" signal to the robot. Upon receiving the signal, the robot picks up the material from the conveyor belt and transfers it to the third empty position on the loading plate. Once completed, the robot sends a "ROB Completed Picking Materials from Belt" signal back to the PLC. Meanwhile, the conveyor resumes forward motion, transporting the second material. The cyclic sensor detects the robot's material pickup process, and eventually, the material is transported to the fourth empty position on the loading plate.
3. The conveyor then resumes forward movement, and the PLC sends another "Allow ROB to Unload Materials onto Belt" signal. Upon receiving the signal, the robot picks up the third material from the loading plate and places it onto the conveyor belt. After completing this, the robot sends a "ROB placement on conveyor complete" signal back to the PLC, proceeding to pick up the fourth material from the loading plate and place it onto the conveyor belt.
4. When the position sensor detects the material in position, the conveyor stops moving. The PLC then sends the "Allow ROB to Pick Material from Belt" signal to the robot. Upon receiving the signal, the robot picks up the material from the conveyor belt and places it into the first empty position on the loading plate. After completing the operation, the robot sends the "ROB Completed Picking Materials from Belt" signal back to the PLC. Meanwhile, the conveyor resumes movement, transporting the material from the fourth position on the loading plate. The cyclic sensor continues to monitor material locations, enabling the robot to repeat the process and eventually transfer the material to the second empty position on the loading plate. This sequence completes one full automated operation cycle. If any discrepancies are encountered during operation: Press the "Stop" button on the touchscreen, the "Stop" button on the control box, or the "Stop" option on the "Main Interface" of the touchscreen. Based on the observed operational status, make the necessary adjustments to the robot program, PLC program, or HMI program.

### 4. Key Program Description

The following section provides explanations for critical codes. For the complete program, please refer to the project files.

#### 4.1 PLC program description

There are two modes available to control the robotic handling application: manual mode and automatic mode. (1) Control Requirements for Manual Mode: To enable manual mode, rotate the black rotary switch on the control box to the left. Then, on the manual control interface of the touchscreen:

* Press the "Start" button to begin forward movement of the conveyor belt.
* Press the "Enable" button to enable the robot.
* Press the "Start" button again to initiate robot program execution.
* Press the "Pause" button to temporarily halt the robot's program.
* Press the "Stop" button to terminate the robot's program. (2) Control Requirements for Automatic Flow Mode: In automatic mode, the robot handling system is governed by the PLC. First, rotate the black rotary switch on the control box to the right to enable automatic mode. Next, press the "Start Initialization" button on the touchscreen. Once initialization is complete, press the "Start" button to activate the system's automatic operation mode. Using the task analysis as a basis, the PLC program for the robot handling system is designed. The structure of the PLC program blocks and variable distribution is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fee1c5ovC7kskLRS3PdTU%2Fimg_385c9b884c28.png?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjH2QwyeeosPCSbnln0gQ%2Fimg_f102502dd717.png?alt=media)

**4.1.1 Main (OB1) program** The Main (OB1) program is shown below. Among them:

* The calls to the Panel Control / Robot Control / Conveyor Control subroutine blocks are shown in Figure (a);
* The call to the Alarm subroutine block is shown in Figure (b);
* The calls to the Initialization / Automatic Process subroutine blocks are shown in Figure (c).

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5OB0uEl5lYpa2ywaI1vE%2Fimg_91973c029234.png?alt=media)

(a) Panel Control / Robot Control / Conveyor Belt Control Subroutine Block

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fly8Zm4rTH05sNv9DLDiR%2Fimg_65db7b59ede7.png?alt=media)

(b) Alarm Subroutine Block

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK5MG5HK4N6zclhLBTLGn%2Fimg_0a390e6eeeeb.png?alt=media)

(c) Initialization / Automatic Flow Subroutine Block

**4.1.2 Panel control subroutine** The panel control Subroutine (SBR0) is shown below. It consists of three main components: button control (Figure a), automatic operation conditions (Figure b), and button indicator light control (Figure c).

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG9XoxGyTQo6UOjhSXcNC%2Fimg_c869cba79723.png?alt=media)

(a) Button Control

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOCiwXym8ydx8PY48Gv6q%2Fimg_cea8e7ea7e00.png?alt=media)

(b) Automatic Operation Conditions

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtQvp3iYeh6hzW3nW4WII%2Fimg_b32518e0ff88.png?alt=media)

(c) Button Indicator Light Control

**4.1.3 Robot control subroutine (SBR1)** The robot control Subroutine (SBR1) includes operations such as enabling, starting, pausing, stopping the robot, and clearing robot alarms.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV5nMeT4xHtTiD7XJ4eQZ%2Fimg_d19b018db838.png?alt=media)

**4.1.4 Conveyor belt startup subroutine (SBR2)** The conveyor belt startup Subroutine (SBR2) includes starting, stopping, and resetting the conveyor belt. This subroutine is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNjY2U6K04SJCWbimumWV%2Fimg_304d5b616e52.png?alt=media)

**4.1.5 Subroutine calling the panel control (SBR3)** The SBR3 program primarily invokes calls the SBR0 subroutine block and integrates several input control conditions.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPj8ftbTaF5nPH35D29Se%2Fimg_2d3a5a5cf1fa.png?alt=media)

**4.1.6 Subroutine calling the robot control (SBR4)** The SBR4 program primarily calls the SBR1 program block and integrates certain input control conditions.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FavcckzirTLD61BbafM5l%2Fimg_e66f20d3b035.png?alt=media)

**4.1.7 Subroutine calling the conveyor belt startup (SBR5)** The SBR5 program primarily calls the SBR2 subprogram block and integrates several input control conditions.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUv0J7SNSWetYA3c15XiR%2Fimg_6d73b7aeffc9.png?alt=media)

**4.1.8 Full system initialization sequence subroutine (SBR6)** The Full System Initialization Sequence Subroutine (SBR6) is shown in the figure below, which includes clearing flags for manual/automatic modes (Figure a), Initialization conditions (Figure b), and Initialization Sequences (Figure c).

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlNSBIELy1mtvRbAkmuDG%2Fimg_d509ae2b88f7.png?alt=media)

(a) Clearing Flags for Manual/Automatic Modes

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQUOum3LHORBlyqBquf7r%2Fimg_8ce6363ad075.png?alt=media)

(b) Initialization Conditions

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fit5kKWuevtG4pJPs6m6x%2Fimg_9e1db2a13da6.png?alt=media)

(c) Initialization Sequence

**4.1.9 Automatic sequence subroutine (SBR7)** The automatic flow sequence subroutine (SBR7) is shown below.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWGXswqInBtovIsqBGFaR%2Fimg_8ffb1715fc73.png?alt=media)

**4.1.10 Alarm subroutine (SBR8)** The alarm subroutine (SBR8) includes functions such as alarm summary information and reset alarm.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F35vNCs9hBLN9GRaOjCwb%2Fimg_d8ea0d85b7a4.png?alt=media)

#### 4.2 HMI program description

The touchscreen interface consists of the main interface, manual interface, IO monitoring interface, and alarm interface. Buttons are located at the bottom of each interface, allowing the user to navigate to the desired interface by pressing the corresponding button.

**4.2.1 Main interface** (1) The main interface is shown below and features five buttons: “Start Initialization”, “Start”, “Stop”, “Reset”, and “Emergency Stop”, along with four status indicator lights “Initialization Complete”, “Automatic Running”, “Paused” and “Alarm Active”.

* Turn the black rotary switch on the button box to the right side (Auto Mode), press the "Start Initialization" button to make the robot return to its safe position and stop the conveyor belt.
* When initialization is completed, the status indicator will illuminate green. Press the "Start" button to enter automatic operation mode (status light turns green). Note: The "Start" button has identical functionality to the physical "START" button.
* Press the "Stop" button to pause the system (status light turns yellow). Note: The "Stop" button has identical functionality to the physical "STOP" button.
* Press the "Emergency Stop" button to immediately halt the system ("Alarm Active" status light turns red). Note: This functions the same as the physical emergency stop button.
* Press the "Reset" button to clear any resolved system alarms.

![4.2 HMI program description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FappaSN9kO5ly2xdVCB69%2Fimg_5d5ae9028cae.jpeg?alt=media)

(2) In the top-left corner of the main interface, there is a **Language Selection** dropdown (Figure 2-69). Select the **Chinese flag** to display all interface content in Chinese. Select the **US flag** to display all interface content in English.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWj6xJ9DytptWzCOZRMAJ%2Fimg_3dff4254a313.jpeg?alt=media)

**4.2.2 Manual operation interface** The manual operation interface includes five buttons:

* Press "Start" for conveyor belt to activate the conveyor belt in forward motion; press again to stop.
* Press "Enable" to power the robot.
* Press "Start" for Magician E6 to execute the program.
* Press "Pause" to temporarily halt program execution.
* Press "Stop" to terminate the program.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeZrdwssXFlmSmqKl8j8Z%2Fimg_145d4929fc53.jpeg?alt=media)

**4.2.3 I/O monitoring interface** The I/O monitoring interface consists of two screens: **INPUT** and **OUTPUT**, which display the status of all input and output signals.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FL6WtcVVnDoHy7YUtxbVo%2Fimg_2d745f71a3f8.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0mqdwqts4H0NBehMJ1bY%2Fimg_36b4a5db8096.jpeg?alt=media)

**4.2.4 Alarm interface** The alarm interface is divided into two sections: real-time alarm and historical alarm interfaces. The real-time alarm interface monitors alarms currently occurring, while the historical alarm interface tracks alarms that occurred in the past.

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCuNQrz5uW5PKmMj339qK%2Fimg_a09df336159f.jpeg?alt=media)

![Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fb0yYMD4PtmncadcbXR9z%2Fimg_c7b9e723ca71.jpeg?alt=media)

#### 4.3 Robot program description

The following description focuses solely on key code segments. For the complete code, refer to the project files. For detailed explanations of related functions, please consult the programming documentation provided by DOBOT. No further elaboration will be provided in this section.

**4.3.1 Description of functional modules in the global thread** (1) Signal Module Settings This module enables quick configuration of output signals, such as controlling the status of the suction cup at the robot's end-effector (grip and release), or setting all output signals to "OFF". The program is illustrated as follows:

```lua
-------------------Set Signal（）------------------------------------
function Signal(form)
if form=="catch" then
print("No.",K,"grasping")
ToolDO(2, 0)
ToolDO(1, 1)
Wait_ToolDI (1,1) ---Wait for signal to be 1
print("No."..K.." sucking".."\n")
elseif form=="put" then
ToolDO(2, 1)
ToolDO(1, 0)
Wait_ToolDI (1,0) ---Wait for signal to be 0
print("No."..K.." releasing".."\n")
DO(14, 0)
elseif form=="reset" then
CP(100)
ToolDO(1, 0)
ToolDO(2, 1)
ToolDO(2, 0)
for a=13,16,1 do        --Reset robot output
DO(a, 0)
end
for a=1,8,1 do        --Reset robot output
DO(a, 0)
end
end
end
```

(2) Point-Point Motion Module Settings The single-point offset program is configured through this module. It facilitates rapid setup of the target point, offset value, user coordinate system, and suction cup status at the end- effector.

```lua
---------------------Point settings----------------------------
function WorkPath(Location,X,S,OffZ,form)
MovL(RelPointUser(Location, {0+50*X, Y, 50, 0, 0, 0}),{user = S,tool = 0,a = 100,v =
100,cp = 100})
MovL(RelPointUser(Location, {0+50*X, Y, 10, 0, 0, 0}),{user = S,tool = 0,a = 100,v =
100,cp = 100})
MovL(RelPointUser(Location, {0.25+50*X, Y, OffZ, 0, 0, 0}),{user = S,tool = 0,a = 10,v
= 20,cp = 0})
Signal(form)
MovL(RelPointUser(Location, {0+50*X,Y, 50, 0, 0, 0}),{user = S,tool = 0,a = 100,v =
100,cp = 100})
end
```

(3) External Input Signal Settings This module primarily detects input IO signals. The program is shown below:

```lua
----------------Waiting signal--------------------------------------
function Wait_DI (signal,Value) --Wait_DI (IO,Value,time)
local timecount=0
local cycletime=10
print("Wait_DI="..Value)
repeat
Wait(cycletime)
timecount=cycletime+timecount
--[[ if timecount>=3000 then
print("No."..i.."grasping".."  Suction abnormality, timeout alarm".."\n")
Pause()
Signal("reset")
ToolDO(1, 0)
ToolDO(1, 1)
end ]]----
until (DI(signal)==Value)
print("Wait_DIed="..Value)
end
---------------------------------------------------------------
function Wait_ToolDI (signal,Value) --Wait_DI (IO,Value,time)
local timecount=0
local cycletime=10
print("Wait_DI="..Value)
repeat
Wait(cycletime)
until (ToolDI(signal)==Value)
print("Wait_DIed="..Value)
end

```

**4.3.2 Program description for the main thread (src0)** (1) Pick Program Functionality implemented: The robot picks materials from the warehouse and places them onto the conveyor. The conveyor runs until the materials reach the material detection station. When the station detects materials, the conveyor stops, a pneumatic cylinder pushes the materials, and the robot picks the materials from the conveyor belt and places them back into the warehouse. This cycle repeats twice, handling two materials per cycle. The program is shown in the following illustration:

```lua
while(true)
do
for i=0,2,2 do
if i==0 then
K=i+1
Wait_DI (14,1)
WorkPath(P2,i,1,0,"catch")
WorkPath(P3,0,0,2,"put")
DO(13,1)
MovJ(P1)
DO(13,0)
Wait_DI (14,1)
WorkPath(P2,i+1,1,0,"catch")
WorkPath(P3,0,0,2,"put")
DO(13,1)
MovJ(P1)
DO(13,0)
Wait_DI (15,1)
DOGroup({5, 1},{6, 0})  --Push material
Wait(2000)
DOGroup({5, 0},{6, 1})  --Release material
WorkPath(P4,0,0,0,"catch")
DO(14, 1)
DO(6,0)
WorkPath(P2,2+i,1,2,"put")
MovJ(P1)
Wait_DI (15,1)
DO(13,0)
DOGroup({5, 1},{6, 0})  --Push material
Wait(2000)
DOGroup({5, 0},{6, 1})  --Release material
WorkPath(P4,0,0,0,"catch")
DO(14, 1)
DO(6,0)
WorkPath(P2,3+i,1,2,"put")
MovJ(P1)
end
if i==2 then
K=i
Wait_DI (14,1)
WorkPath(P2,i,1,0,"catch")
WorkPath(P3,0,0,2,"put")
DO(13,1)
MovJ(P1)
DO(13,0)
Wait_DI (14,1)
WorkPath(P2,i+1,1,0,"catch")
WorkPath(P3,0,0,2,"put")
DO(13,1)
MovJ(P1)
DO(13,0)
Wait_DI (15,1)
DOGroup({5, 1},{6, 0})  --Push material
Wait(2000)
DOGroup({5, 0},{6, 1})  --Release material
WorkPath(P4,0,0,0,"catch")
DO(14, 1)
DO(6,0)
WorkPath(P2,i-2,1,2,"put")
MovJ(P1)
Wait_DI (15,1)
DO(13,0)
DOGroup({5, 1},{6, 0})  --Push material
Wait(2000)
DOGroup({5, 0},{6, 1})  --Release material
WorkPath(P4,0,0,0,"catch")
DO(14, 1)
DO(6,0)
WorkPath(P2,i-1,1,2,"put")
MovJ(P1)
K=0
end
```

(2) Exit Loop Program When an input signal DI16 is detected, the robot completes the current task and exits the program.

```lua
if DI(16)==1 then
os.exit()
end
```
