---
description: >-
  Hardware user guide for the DOBOT Nova Series collaborative robots (Nova 2 and
  Nova 5, DSC-compatible): safety, specifications, electrical interfaces,
  installation, maintenance and functional safety.
---

# DOBOT Nova Series Hardware User Guide

## Controller applicability

This page follows the official **DOBOT Nova Series (Compatible with DSC) Hardware User Guide V1.4 (2026-09-03)**. Its controller wiring, interfaces, and emergency-stop procedures apply only to Nova 2 or Nova 5 robots fitted with a **DOBOT DSC controller**. Check the controller nameplate before using those procedures.

The Nova 2 and Nova 5 variants currently listed by OpenELAB are **CCBOX** and **Pocket Go**, not DSC. For a CCBOX-equipped Nova, use the [official CCBOX hardware guide V2.1 (2026-07-17)](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260717/DOBOT%20Nova%20Series%20\(Compatible%20with%20CCBOX\)%20Hardware%20User%20Guide_V2.1_20260717_en.pdf). For a Pocket Go configuration, use the controller-specific documentation supplied with that configuration; do not assume that DSC or CCBOX wiring instructions apply to Pocket Go.

### Contents

* Safety
* Product introduction
* Product characteristics (coordinate system, home posture, singularities)
* Mechanical specifications (Nova 2 and Nova 5)
* Electrical characteristics (DSC controller interfaces)
* Transportation
* Installation and use
* Maintenance
* Disposal and environment protection
* Warranty
* Appendix (technical specifications, functional safety, applicable standards)

### Safety

* The robot is a semi-finished machine; a complete risk assessment must be performed by the integrator before use.
* Use the robot only for its intended purpose, within the specified environmental range.
* Only trained and qualified personnel may install, operate, and maintain the robot.
* Set up safety guardrails and keep personnel out of the robot workspace.
* Use the emergency stop device in emergencies; do not dismantle, modify, or repair the robot without authorization.

### Key Specifications

| Parameter         | Nova 2   | Nova 5   |
| ----------------- | -------- | -------- |
| Rated load        | 2 kg     | 5 kg     |
| Working radius    | 625 mm   | 850 mm   |
| Repeatability     | ±0.05 mm | ±0.05 mm |
| Weight            | 11 kg    | 14 kg    |
| IP rating         | IP54     | IP54     |
| Max working speed | 1.6 m/s  | 2 m/s    |

### Preface

#### Purpose

This document describes the functions, technical specifications, installation guide of DOBOT Nova series collaborative robot, making it easy for users to fully understand and use it.

#### Scope of application

**Robot arm:DOBOT Nova 2, DOBOT Nova 5** You can find the model of robot on the right-top corner of the nameplate on the robot base.

![Scope of application](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F88dBCZB9UsHtoW22OZMM%2Fimg_b44f8081f6df.png?alt=media)

![Scope of application](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHBmIVFqIcmohZG2E5q6j%2Fimg_6d9d9a4fb2b9.png?alt=media)

**C\*\*\*\*ontroller:DOBOT DSC** You can find the model of the controller in the upper right corner of the nameplate on the controller.

![Scope of application](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhdsbLQB5Ty28gWhalDkp%2Fimg_ddce88f37995.png?alt=media)

#### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

#### Related documents

#### Revision history

| Document                                                     | Description                                                                                                                                  | Download link                                                                     |
| ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| DobotStudio Pro User Guide                                   | Explains how to use the robot control software, DobotStudio Pro.                                                                             | Visit the Download Center to search by document name or filter by product series. |
| DOBOT TCP IP Remote Control Interface Guide                  | Describes how to use the secondary development interface based on TCP/IP protocol. Multi-language development DEMOs are available on Github. |                                                                                   |
| DOBOT Bus Communication Protocol Guide (EtherNetIP/Profinet) | Introduces the usage of the robot's bus communication functions (EtherNetIP/Profinet).                                                       |                                                                                   |
| DOBOT Collaborative Robot Teach Pendant User Guide           | Explains how to use the Teach Pendant that accompanies the collaborative robot.                                                              |                                                                                   |
| DOBOT DSC Controller User Guide                              | Describes the functions, technical specifications, and installation guide of the DSC controller.                                             |                                                                                   |

| Date       | Version | Revised content                                                               |
| ---------- | ------- | ----------------------------------------------------------------------------- |
| 2026/09/03 | V1.4    | Added step for Cable connection to the DSC controller.                        |
| 2026/07/31 | V1.3    | Modify the weight of the DSC.                                                 |
| 2026/06/23 | V1.2    | Added descriptions regarding functional safety and applicable standards.      |
| 2026/04/01 | V1.1    | Added a description that the robot arm will lose power during emergency stop. |
| 2025/12/22 | V1.0    | The first release.                                                            |

#### Symbol conventions

The symbols that may be found in this document are defined as follows.

| Symbol  | Description                                                                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER  | Indicates a hazard with a high level of risk which, if not avoided, could result in death or serious injury.                                   |
| WARNING | Indicates a hazard with a medium level or low level of risk which, if not avoided, could result in minor or moderate injury, robot arm damage. |
| NOTICE  | Indicates a potentially hazardous situation which, if not avoided, could result in robot arm damage, data loss, or unanticipated result.       |
| NOTE    | Provides additional information to emphasize or supplement important points in the main text.                                                  |

### 1. Safety

#### 1.1 Responsibility

**1.1.1 Responsibility and norms** The information in this document does not cover designing, installing and operating a complete robot system, nor does it cover all peripheral equipment that may affect the safety of the complete system. The complete system must be designed and installed in accordance with the safety requirements set forth in the standards and regulations of the country where the robot is installed. The integrators of DOBOT are responsible for ensuring that the applicable safety laws and regulations in the country concerned are observed and that any significant hazards in the complete robot application are eliminated. This includes, but is not limited to:

* Performing a risk assessment for the complete robot system.
* Adding safety machines and mechanisms based on the risk assessment, including but not limited to building a proper safety circuit to achieve safe stop.
* Setting up the appropriate safety settings in the software.
* Ensuring that the user will not modify any safety measures.
* Validating that the total robot system is designed and installed correctly.
* Specifying instructions for use.
* Marking relevant signs and contact information of the integrators on the robot.
* Archiving relevant technical files.

**1.1.2 Limitation of liability** Any safety information provided in this document should not be considered as a warranty from DOBOT. The robot may cause injury or damage even if all safety instructions are observed.

#### 1.2 Intended use

DOBOT Nova series robots are commercial robots only for general commercial use, such as processing or delivering food and other goods through end tools. DOBOT Nova series robots are equipped with special safety mechanisms including collision detection. These mechanisms are purposely designed for human-robot collaboration, but only intended for non-hazardous applications after risk assessment, where tools, products, environment and other machines have been demonstrated to be incapable of significant risk through application-specific risk assessments. Any use or application other than the intended use is not permitted:

* Do not use in potentially explosive environments.
* Do not use in vacuum environments.
* Do not use for transporting people or animals.
* Do not use in life-critical applications.
* Do not use without performing a risk assessment.
* Do not use beyond the specified ratings or limits.
* Do not use as a climbing aid.
* Do not use underwater.

#### 1.3 Risk assessment

As the robot is a **semi-finished machinery**, the integrator is responsible for conducting a risk assessment of the overall system after integration. It is recommended that integrators perform a risk assessment based on ISO 12100 and ISO 10218-2 and refer to the Technical Specification ISO/TS 15066 for integration guidance. The risk assessment should consider all workflows during the robot’s entire lifecycle, including but not limited to:

* Teaching the robot during the setup and development process.
* Maintenance and repairs.
* Robot installation. The risk assessment must be completed **before the robot is powered on for the first** **time**, including but not limited to confirming the safety function settings and evaluating whether additional emergency stop buttons or other protective measures are required. When performing the risk assessment, the integrator should focus on the following safety functions:
* Collision detection sensitivity settings: Limiting the force applied during a collision between the robot and the operator.
* Robot and tool pose limitations: Reducing the risk of the robot and tools colliding with the operator, especially in specific body areas such as the head and neck.
* Speed limit: Limiting the robot’s operating speed to reduce safety risks. The integrator must set permissions and passwords to prevent unauthorized personnel from modifying the safety function configurations. When conducting a risk assessment for collaborative robot applications, the integrator must consider potential collision risks caused by human error, including:
* The severity of potential collisions.
* The probability of potential collisions.
* The likelihood of avoiding potential collisions. If the robot is installed in a non-collaborative application where its built-in safety functions cannot effectively eliminate safety risks (e.g., using hazardous tools), the integrator must consider adding additional protective measures (e.g., safety barriers or safety lasers) during the risk assessment. The integrator must consider potential risks including but not limited to:

1. Cuts from sharp edges and points on the end tools or end effector connectors.
2. Cuts from sharp edges and points on obstacles in or near the robot’s workspace.
3. Scrapes caused by contact with the robot.
4. Sprains or fractures resulting from collisions between heavy payloads on the robot’s end and hard surfaces.
5. Consequences of loose bolts securing the robot or end tool.
6. Consequences of items falling off the end tool.
7. Consequences of incorrectly pressing the emergency stop button of other equipment.
8. Consequences of unauthorized changes to the safety function configurations. For robot emergency stop time and distance, please refer to the "Emergency stop time and distance" section.

#### 1.4 Pre-use assessment

Before using the robot for the first time or after any modifications are made, testing must be conducted to ensure that all safety inputs and outputs are correctly connected and functioning properly:

1. Test whether the emergency stop button and user emergency stop input can trigger an emergency stop.
2. Test whether the protective stop input can halt the robot’s motion. If a protective stop reset input is configured, test whether this input must be activated before the robot can resume operation.
3. If a reduced mode input is configured, test whether this input can switch the robot to reduced mode (reduced-speed operation).
4. If the teach pendant is selected and the three-position switch enable function is configured, verify that in manual mode the robot remains enabled only when the three- position switch is maintained in the middle position.
5. Test whether the system connected to the emergency stop status output can detect the output change and respond accordingly.
6. If other safety outputs are configured, test whether the system connected to the corresponding output can detect the output change and respond accordingly.

#### 1.5 Safety warning sign

The following safety warning signs may appear on the product, and their meanings are as follows:

| Symbol      | Description                                                                                                                                                                                              |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER      | Indicates a hazard with a high level of risk which, if not avoided, could result in death or serious injury.                                                                                             |
| ELECTRICITY | Indicates a potentially dangerous electrical situation that, if not avoided, could result in injury, death, or serious damage to the equipment.                                                          |
| HOT         | May cause dangerous hot surface; if touched, may cause personal injury.                                                                                                                                  |
| WARNING     | Indicates a hazard with a medium level or low level of risk which, if not avoided, could result in minor or moderate injury, robot arm damage.                                                           |
| NOTICE      | Indicates a potentially hazardous situation which, if not avoided, could result in robot arm damage, data loss, or unanticipated result.                                                                 |
| CAUTION     | Indicates a situation that, if not avoided, could result in personnel injury or damage to the equipment. For items marked with such signs, there is sometimes a possibility of significant consequences. |

**Symbol Description** Indicates a situation that, if not avoided, could result in personnel injury or damage to the equipment. For items marked with such signs, depending on the specific **CAUTION** situation, there is sometimes a possibility of significant consequences

#### 1.6 General safety

Follow the safety instructions below when starting and using the robot for the first time.

**DANGER**

* The robot control system is an electrically powered device. Non-professionals should not modify the circuit, otherwise, it may result in robot damage or personal injury.
* Strictly comply with local laws and regulations when operating the robot. The safety precautions described in this document serve only as a supplement to local safety standards.
* Use the robot within the specified environmental conditions. Operating beyond the rated specifications and load conditions may shorten the robot's lifespan or even damage it.
* Ensure that the robot is operated under safe conditions and there is no harmful object around the robot.
* Avoid frequently powering the robot on and off, as this may degrade the performance of the main circuit components inside. If repeated power cycling is necessary, limit it to no more than once per minute.

**HOT**

* The robot and controller generate heat during operation. Do not operate or touch the robot while it is running or immediately after it stops.
* Turn off the power and wait one hour for the robot to cool down.
* Do not place your fingers on the heat generating area of the controller. **NOTICE**
* Personnel responsible for installing, operating, and maintaining the equipment must undergo rigorous training, fully understand all safety precautions, and master proper operation and maintenance procedures before handling the equipment.
* Unauthorized personnel without professional training must not disassemble or repair the equipment. In case of a malfunction, contact DOBOT's technical support engineer in time.
* Perform daily inspections and periodic maintenance, replacing faulty components promptly to ensure the safe operation of the equipment.
* If the equipment is scrapped, please comply with the relevant laws for the proper disposal of industrial waste to protect the environment.
* Establish safety measures (e.g., fences, ropes, or warning lines) near the robot’s operating area to ensure that personnel stay out of the robot's reach while it is in operation or about to start.
* Do not enter the robot’s safety zone defined by the risk assessment or touch the robot while the system is running.
* Do not expose the robot to a permanent magnetic field, as strong magnetic fields can cause damage.
* DOBOT assumes no responsibility for robot damage or personal injury caused by improper operation or failure to follow the product’s instructions for use.
* Handling operations using lifting rings, cranes, or similar equipment must be conducted using appropriate and reliable lifting devices, and must be carried out by qualified personnel or those authorized by the company in accordance with local regulations.
* Make sure that there are no obstacles within 2 meters of the robot during the transportation, and personnel should stay away from the suspended robot.
* DOBOT is not responsible for any damage caused during the transportation and handling of the equipment.
* Make sure that the robot is in the packing posture before packaging, and the brakes on each axis are normal.
* Make sure that the packing area is free of obstacles to allow staff to evacuate quickly in case of emergencies.
* Secure the packaging firmly during transport to keep the robot stable.
* After removing the outer packaging, make sure that the robot maintains its original packing posture and the brakes on each axis are normal.
* Make sure that the unpacking area is free of obstacles to allow staff to evacuate quickly in case of emergencies.
* During debugging, make sure that no personnel or other equipment (including computer used for debugging) is present in the hazardous area of the machine.
* Wear appropriate personal protective equipment when necessary, such as safety helmets, safety shoes (with non-slip soles), face shields, safety goggles, and gloves. Inappropriate clothing may cause personal injury.
* Do not enter the robot’s workspace while the robot is operating, as this may result in injury to the robot or operator.
* If an abnormality occurs with the robot, ensure that the system is stopped before conducting an inspection.
* After debugging, operators must first test the system in manual mode. Once this is confirmed to be correct, switch to automatic operation.
* Before selecting automatic operation mode, all paused safety configurations must be restored to full functionality.
* If the controller needs to be restarted due to a power failure, the robot must be manually returned to the initial position of the automatic operation program before restarting automatic operation.
* Before performing maintenance, inspection, or wiring work, the power supply must be completely cut off, and a "No power supply" sign must be posted. Failure to do so may result in electric shock or personal injury.
* Observe ESD (Electrostatic Discharge) regulations when disassembling the robot or controller.
* Avoid disassembling the power supply system inside the controller. Even after the controller is turned off, high voltage may remain for several hours.
* For disassembly and repair of the robot, contact DOBOT's technical support engineer.
* Maintenance and repair work must be carried out by designated personnel, otherwise electric shock or personal injury may result.
* If the brake is manually released, the robot may move due to gravity. Therefore, when manually releasing the brake, ensure proper support for the robot and any attached tools or workpieces.
* If the power supply must be turned on while the controller door is open for maintenance or inspection, avoid direct exposure of the controller interior to strong light sources such as sunlight or spotlights, as this may cause malfunctions or errors.
* To prevent electric shock, turn off the circuit breaker and disconnect the main power before replacing any components.
* Wait at least five minutes after disconnecting the main power before replacing components.
* Component replacement must be performed by authorized personnel.
* The robot is designed and tested according to Group 1, Class A industrial, scientific, and medical (ISM) equipment standards. In household and light industrial environments, using this robot may cause radio interference, requiring protective measures.
* Do not operate the robot near strong radiation sources (e.g., unshielded RF sources), as this may interfere with normal operation.
* The maximum operating speed of the robot has been set to the optimal value at the factory. If a speed increase is required, please contact technical support to discuss potential solutions. Unauthorized adjustment of the maximum speed limit may result in issues such as joint torque exceeding permissible limits during robot movement.

**WARNING**

* Wear anti-static clothing and anti-static gloves before operating the equipment.
* It is prohibited to modify or remove the nameplate, instructions, icons, or labels on the equipment.
* Before operating the equipment, locate and be familiar with the emergency stop function to ensure that the robot can be stopped urgently in case of an emergency. The emergency stop function is classified as a Stop Category 1.
* Be careful when handling or installing the robot. Follow the instructions on the packaging box, place the robot gently, and position it according to the arrow markings to prevent damage.
* To ensure device and personal safety, use supplied cables.
* Make sure that both the robot and the tools are correctly and securely installed.
* Make sure that the robot has sufficient space to move freely.
* Do not continue using the robot if it is damaged.
* Any impact will release a large amount of kinetic energy, which can be much higher than during high-speed or high-load operations.

#### 1.7 Personal safety

When operating the robot system, please strictly follow the general precautions listed below to ensure the personal safety. **WARNING**

* Comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.
* Do not touch the wiring terminals or disassemble the equipment while it is powered on, as this may result in electric shock.
* Make sure that the equipment is properly grounded, otherwise, it may endanger personal safety.
* Do not touch the power terminals or disassemble internal components within 10 minutes of disconnecting the robot from the power supply, as residual voltage in the internal capacitors may cause electric shock.
* Even if the controller's power switch is already in the "OFF" status, do not touch or disassemble internal components, as residual voltage in the internal capacitors may cause electric shock.
* Do not wear loose clothing or jewelry when working with the robot. Tie your long hair back behind your head.
* If the robot appears to be stationary while the equipment is running, it may be in a standby state, waiting for a start signal. In such cases, the robot should still be considered active. Do not approach the robot.

#### 1.8 Residual risks

DOBOT have undergone rigorous safety design and testing, and a series of safety measures have been implemented to minimize risks during installation, commissioning, operation, and maintenance. However, certain **residual risks** may remain and should be handled with caution during operation:

* **Mechanical collision or pinching:** Unexpected collisions of mechanical components or abnormal gripping may occur during the robot's operation.\*\*\*\*
* **Electrical hazards:** Risks such as accidental electrical leakage may arise due to cable aging or improper installation environments.
* **Programming errors or loss of control:** Communication interference, incorrect parameter settings, or improper integration with other equipment could result in deviations from the intended robot actions.
* **Human operational errors:** Risks caused by failure to strictly adhere to operational requirements, unauthorized parameter adjustments, or untrained personnel entering the robot's motion area. **To reduce residual risks, follow these recommended practices during use:**
* **Wear protective equipment:** Always wear safety gear such as hard hats, safety glasses, and insulated gloves, especially when entering the robot's motion area.
* **Isolate the workspace:** Use barriers or warning signs to prevent unauthorized personnel from entering the robot's operating range.
* **Familiarize yourself with the emergency stop button:** Ensure the emergency stop button is always easily accessible and press it immediately in case of emergencies.
* **Perform regular maintenance:** Conduct routine inspections of all robot components as specified in the manual to ensure proper functioning.
* **Authorized use only:** Robots should only be operated by trained and qualified personnel. Unauthorized modification of parameters or disassembly of components is strictly prohibited. When using the robot, always operate it in strict accordance with the operational instructions and safety guidelines. DOBOT assumes no responsibility for any losses incurred due to failure to comply with these regulations.

#### 1.9 Emergencies

**1.9.1 Emergency stop device** In case of emergency, press the E-stop button to immediately halt all robot movements. According to IEC 60204-1 and ISO 13850, emergency stop devices are not safeguards. They serve as supplementary protective measures and are not intended to prevent injuries. Based on the results of the risk assessment for your robot application, you can connect additional E-stop buttons. The E-stop button must comply with the IEC 60947-5-5 standard.

**NOTICE** Pressing the emergency stop, the robot arm stops all motion and loses power.

**1.9.2 Emergency recovery** The E-stop button locks when pressed and must be rotated as indicated on the button to unlock it. After unlocking, the alarm can be cleared and the robot can be re-enabled via DobotStudio Pro to recover from the emergency status.

**WARNING** Operate the robot arm to recover from emergency status only after the danger to the robot system has been completely eliminated.

**1.9.3 Personnel rescue in emergency situations** In rare emergency cases, you may need to move the robot arm while in an emergency stop status to rescue a trapped person. In such cases, you can:

**Manually releasing the brakes** Open DobotStudio Pro and navigate to **"Settings > Safety > Joint brake"** page, click **"Edit"**, hold the joint with your hand and turn on the switch of the joint you want to move, then click **"Save"**. Once the brake is ON, you can drag the joint to rescue the trapped person.

**WARNING** When switching on the "Joint brake" function, be sure to hold the joint with your hand to prevent it from falling. **NOTICE**

* The robot arm's axis limits are set via software.
* When the brake is ON, the drop distance of the robot arm during the closing process is less than 1 mm.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPKHKljHbtm1ZkYfVUZI5%2Fimg_38200d92f267.png?alt=media)

**Removing the fixing screws from robot base** Refer to Robot installation. After removing the fixing screws from the robot base, you can move the robot arm to free the trapped person. **WARNING**

* Disconnect the robot from the power before removing the screws.
* Hold the robot throughout the process of removing the screws and moving the robot.

### 2. Product Introduction

#### 2.1 Overview

![2.1 Overview](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX9MIa8OhQx3AXkjaVTzH%2Fimg_45c76941d9f1.jpeg?alt=media)

The main components of the robot system include:

* **Nova robot arm:** Six-axis robot arm, main moving parts.
* **Small controller:** Core computing and electrical components. \*\*\*\*
* **E-Stop button:** Connected to the controller to enable the emergency stop function.
* \*\*Wireless receiver (Optional):\*\*Plugged into the controller, enabling the operation\
  terminal to connect to and control the robot via WiFi. In addition, the system includes an **operation terminal** (tablet, PC or teach pendant) for installing the robot's control software.

![2.1 Overview](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3fZdO1PPj1IEHwsP17so%2Fimg_74ae257ec948.jpeg?alt=media)

![2.1 Overview](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgN8GbCgjh0ZmzFoAyV0h%2Fimg_aeaff6662238.jpeg?alt=media)

#### 2.2 Robot arm

**2.2.1 Composition** As shown in Figure 2.3, the Nova series robot arm includes 6 rotary motion joints, and 2 connecting rods (upper arm and forearm). The robot's end is equipped with a hand-guiding button and an indicator light, while the tool flange side is fitted with an aviation socket.

![2.2 Robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3EKG2RRd77eE8Sr6EynJ%2Fimg_c5422f27b1a6.png?alt=media)

**2.2.2 End button and indicator light** The end of Nova series robot arm is equipped with a button and a ring of indicator light, as shown in Figure 2.4.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxyZihwSoEa7UuW0ELasa%2Fimg_3efcf58de083.jpeg?alt=media)

The meanings of the end indicator lights are as follows: When the robot is enabled, long-press the hand-guiding button for 3 seconds to enter drag teaching mode. After dragging the robot to the teaching point, short-press the hand-guiding button to exit drag teaching mode.

| Indicator color | Status    | Description                                                                                                                                     |
| --------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Blue            | Steady on | The robot is powered on but not enabled.                                                                                                        |
| Blue            | Flashing  | Hand-guiding status (fast flashing indicates the robot arm is starting up, or an abnormal connection between the robot arm and the controller). |
| Green           | Steady on | The robot is enabled (project not running).                                                                                                     |
| Green           | Flashing  | Automatic running status (project running).                                                                                                     |
| Yellow          | Steady on | Trajectory recording status.                                                                                                                    |
| Yellow          | Flashing  | Trajectory playback status.                                                                                                                     |
| Red             | Steady on | The robot is in alarm status.                                                                                                                   |

#### 2.3 Controller

The DOBOT Nova series robot must be used in conjunction with a small controller (DSC). The appearance of these controllers is as shown below, and detailed definitions of the electrical interfaces can be found in the Electrical Characteristics.

![2.3 Controller](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgrSX9VzKF1sJfsZknY65%2Fimg_49286e45424b.jpg?alt=media)

After connecting the external power supply and the robot arm, briefly press and release the controller’s power button to turn it on and provide power to the robot arm. A solid green light indicates the controller has successfully started. When the controller is powered on, briefly press and release the power button again to shut it down and cut power to the robot arm. The green light turning off indicates a successful shutdown.

#### 2.4 Operation terminal

The DOBOT Nova series robot supports control via both PC and App, as shown in Table 2.1. To enable control via WiFi, the WiFi module must be plugged into the controller.

| Terminal type             | PC                                                                                                                                                                                                                            | Tablet (Android)                                                        |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Operating system          | Windows 10 (64-bit) 1809 or above                                                                                                                                                                                             | Android 10 and above                                                    |
| Control software          | DobotStudio Pro (4.6.4.0 stable and above)                                                                                                                                                                                    |                                                                         |
| Recommended configuration | CPU: 64-bit Intel or AMD processor (SSE4.2 or later, 2.9 GHz or higher); Memory: 16G; Storage: 128GB (at least 4GB available); Network card: Gigabit NIC; Graphics card: 4GB, DirectX12 support; Display: 1920×1080 or higher | CPU: 4-core, 2.0 GHz or higher; RAM: 4GB; Storage: 32GB; Screen: 8-inch |
| Communication mode        | LAN/WiFi                                                                                                                                                                                                                      | WiFi                                                                    |

Graphics card: 4GB, DirectX12 support Display: 1920x1080 or higher resolution

**Communication** LAN/WiFi WiFi

**mode** When purchasing a DOBOT Nova series robot, you can request an optional Android tablet, or use self-prepared operation terminal as long as it meets or exceeds the recommended specifications in Table 2.1.

### 3. Product Characteristics

#### 3.1 Coordinate system

**3.1.1 Joint coordinate system** The joint coordinate system is determined based on all motion joints. All joints are rotational joints, as shown in Figure 3.1.

![3.1 Coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMDV8Rw6EVzIFe4MBLduU%2Fimg_6e860ad9dda8.png?alt=media)

**3.1.2 User coordinate system** The user coordinate system is a user-defined coordinate system based on the workbench or workpiece. The origin and axis directions can be defined as needed to measure points within the workspace and arrange tasks conveniently. The default user coordinate system is determined based on the center point of the robot base, and Y+ direction is the routing direction of the heavy-duty cable, as shown in Figure 3.2.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAmDRtPgh73Wn1NOSgr8r%2Fimg_f36db931bdff.png?alt=media)

**3.1.3 Tool coordinate system** The tool coordinate system defines the position and posture of the Tool Center Point (TCP). Its origin and direction change dynamically based on the position and angle of the end tool. The default tool coordinate system is determined based on the center point of the end flange, with the Y+ direction facing opposite to the aviation connector, as shown in Figure 3.3.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv4bcsDY1SJoPMwVSMqHk%2Fimg_0291816958ef.png?alt=media)

#### 3.2 Home posture

Each joint of the robot arm is marked with a home-posture sticker as shown in Figure 3.4. When a joint is at 0 degrees, the stickers on both sides of the joint will be perfectly aligned. When all joints are set to 0 degrees, the robot arm should be in a vertical posture, with the heavy-duty cable aligned parallel to the J2 axis and the aviation connector pointing straight upward.

![3.2 Home posture](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXIMG2osXjAfbaJUBajsn%2Fimg_732dc1b4afeb.jpeg?alt=media)

If the home posture changes due to component replacement or collision, you can move the robot arm to a state where all the home-posture stickers of each joint are aligned. Then calibrate the home posture through DobotStudio Pro.

#### 3.3 Singularities

When the robot moves in a linear or arc trajectory and approaches certain specific postures, an alarm will be triggered, and the robot will stop movement. These postures are referred to as singular positions or singular points.

**NOTICE**

* Joint motion is not affected by singular positions.
* Avoid stopping the robot near a singularity using drag mode or joint motion and then attempting linear or arc motion. The DOBOT Nova series robot arm has three types of singularities, as described below.

**3.3.1 Shoulder singularity** The singularity occurs when the intersection of the J5 and J6 axes is located in the plane formed by the J1 and J2 axes. This typically happens in the cylindrical space directly above or below the robot. Refer to the motion range in the Mechanical Specifications chapter for details about each model as shown in Figure 3.5.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLOE0dtuMA4jecl2ZauVz%2Fimg_b68ea02ee215.jpeg?alt=media)

**3.3.2 Elbow singularity** The singularity occurs when J3=0°±2°, where the upper arm and forearm are parallel. as shown in Figure 3.6.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfUHUyBw6RycvPxYROfP3%2Fimg_82de66db7d3a.jpeg?alt=media)

**3.3.3 Wrist singularity** The singularity occurs when J5=0°±2°, where the J4 axis and J6 axis are parallel. as shown in Figure 3.7.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgieSyizcb1YItX2CYjLI%2Fimg_46831781384d.jpeg?alt=media)

**3.3.4 Recommendations for avoiding singularities**

* Switch the motion type to joint motion when near a singularity.
* Add transition points in the trajectory to bypass the singularity.
* Adjust the installation posture of the robot to avoid singularities in the path. For example, switch from standard-angle mounting to hoisting or side mounting.
* Modify the length of the end tool.
* Adjust the installation angle of the end tool to bypass singularities in the path.

#### 3.4 Emergency stop time and distance

When the J1\~J3 axes trigger an emergency stop at 100% speed, maximum load and maximum arm span, the braking time and distance of each joint are shown in the table below. For the J1 axis, the test is performed by moving horizontally, namely, the rotation axis is perpendicular to the ground.

![3.4 Emergency stop time and distance](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqrFBmCBAngXa6r3H7XUj%2Fimg_5f5f3e72b230.jpeg?alt=media)

For the J2 and J3 axis tests, the robot follows a vertical trajectory, namely, the rotation axis is parallel to the ground, and triggers an emergency stop when the robot moves downward.

![3.4 Emergency stop time and distance](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF7MqR4TxmUFlWidKeugY%2Fimg_9d245ca1cf81.jpeg?alt=media)

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeHbSTJMlElKYlfPZtPPq%2Fimg_e7bc040b9426.jpeg?alt=media)

The table below includes the data of some models for your reference.

| Axis | Nova 2 (Emergency stop time / distance) | Nova 5 (Emergency stop time / distance) |
| ---- | --------------------------------------- | --------------------------------------- |
| J1   | 217 ms / 169.02 mm                      | 179 ms / 158.36 mm                      |
| J2   | 213 ms / 157.37 mm                      | 175 ms / 141.81 mm                      |
| J3   | 227 ms / 102.29 mm                      | 196 ms / 84.70 mm                       |

### 4. Mechanical Specifications

All dimensions in this chapter are in millimeters (mm).

#### 4.1 Nova 2 mechanical specifications

**4.1.1 Nova 2 dimensions and workspace** When selecting the installation position for the robot, you must consider the cylindrical space directly above and below the robot, and try to avoid moving the tool into this cylindrical space. As doing so may cause the joints to rotate too fast even when the tool moves slowly, resulting in low work efficiency and making risk assessment more difficult.

![4.1 Nova 2 mechanical specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ffj5xsi4WRGuYVkVWYnDI%2Fimg_7ca10e606e9b.png?alt=media)

**4.1.2 Nova 2 base mounting dimensions**

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNQ2ODRt23Gbj8XzTB0hT%2Fimg_7ff765992685.png?alt=media)

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO57QqaS8VAgx67fn4HHb%2Fimg_7afcbab53bff.png?alt=media)

**4.1.3 Nova 2 end flange dimensions** The end flange dimensions of the Nova series robot are all identical. The flange design conforms to ISO 9409-1.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNHufe3hM12a54mU4Hecg%2Fimg_cc06e0700e00.png?alt=media)

**4.1.4 Nova 2 end load curve** The origin of the coordinate system for the end load curve is the center of the robot's end center along the X and Y axes. The radial distance (r) is calculated as: r = √X2 + Y2. This flange. X and Y represent the offset distance of the load’s center of gravity from the flange r-value corresponds to the vertical axis (Y-axis) in the load curve graph, labeled as X, Y \[cm]. The horizontal axis (X-axis) represents Z \[cm], which is the distance from the load’s center of gravity to the flange along the Z direction. You can evaluate the working condition of the robot according to the statistical results. For example, if the load is 1.5kg, X = 6cm, According to r = √X2 + Y2, calculate r = 10cm. Y = 8cm, Z = 5cm, and you can get r = 10cm. The judgment steps are as follows:

* Select the corresponding curve based on the load mass. For a load of 1.5 kg, locate the curve corresponding to 1.5 kg.
* Locate the (r, Z) = (10cm, 5cm) point in the load curve graph and compare it with the 1.5kg curve. If the point is below the curve, the load is within the robot’s operational range (selection valid). If the point is above the curve, the load exceeds the robot’s limit (selection invalid). In this example, the point is below the curve, indicating that the selected load is acceptable, and the robot can operate safely under this condition.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKDqdx5AX8LIhMEync2GC%2Fimg_1e6b3de41f8c.png?alt=media)

#### 4.2 Nova 5 mechanical specifications

**4.2.1 Nova 5 dimensions and workspace** When selecting the installation position for the robot, you must consider the cylindrical space directly above and below the robot, and try to avoid moving the tool into this cylindrical space. As doing so may cause the joints to rotate too fast even when the tool moves slowly, resulting in low work efficiency and making risk assessment more difficult.

![4.2 Nova 5 mechanical specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Frmuyb7cstQPdE8AntUF7%2Fimg_efc156d364eb.png?alt=media)

Figure 4.5 Nova 5 dimensions and workspace

**4.2.2 Nova 5 base mounting dimensions**

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fegz2aJoDlHycf6I2Qx74%2Fimg_03df76d78416.png?alt=media)

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd7UEUOMDWeTf2ANNAKYM%2Fimg_b613fa9fe4e1.png?alt=media)

Figure 4.6 Nova 5 dimensions and workspace

**4.2.3 Nova 5 end flange diemensions** The end flange dimensions of the Nova series robot are all identical. The flange design conforms to ISO 9409-1.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNHufe3hM12a54mU4Hecg%2Fimg_cc06e0700e00.png?alt=media)

**4.2.4 Nova 5 end load curve** The origin of the coordinate system for the end load curve is the center of the robot's end center along the X and Y axes. The radial distance (r) is calculated as: r = √X2 + Y2. This flange. X and Y represent the offset distance of the load’s center of gravity from the flange r-value corresponds to the vertical axis (Y-axis) in the load curve graph, labeled as X, Y \[cm]. The horizontal axis (X-axis) represents Z \[cm], which is the distance from the load’s center of gravity to the flange along the Z direction. You can evaluate the working condition of the robot according to the statistical results. For example, if the load is 3.8kg, X = 6cm, According to r = √X2 + Y2, calculate r = 10cm. Y = 8cm, Z = 5cm, and you can get r = 10cm. The judgment steps are as follows:

* Select the appropriate curve based on the load weight. Since the load is 3.8kg, use the 4kg curve as a reference.
* Locate the (r, Z) = (10cm, 5cm) point in the load curve graph and compare it with the 4kg curve. If the point is below the curve, the load is within the robot’s operational range (selection valid). If the point is above the curve, the load exceeds the robot’s limit (selection invalid). In this example, the point is below the curve, indicating that the selected load is acceptable, and the robot can operate safely under this condition.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FB1GZvcxH7xBhmTshNkhh%2Fimg_274e16dbf0d1.png?alt=media)

#### 4.3 Controller dimensions

All dimensions provided in this section are specified in millimeters.

![4.3 Controller dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp2EnuWk6HA06bRWBX19n%2Fimg_7e15c493a980.jpeg?alt=media)

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvDJXflbzyaFXokCH6hCk%2Fimg_b3c21864f764.jpeg?alt=media)

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5HXOcdq1tMaOFZ1Xc12w%2Fimg_4f88efaebfba.jpeg?alt=media)

### 5. Electrical Characteristics

#### 5.1 Electrical warnings and precautions

When designing and installing robot applications, please strictly follow the warnings and precautions listed below.

**WARNING** The following warnings must be observed when designing and installing safety signal-related functions, as failure to do so may result in the loss of safety functions and cause injury or death.

* Never connect safety signals to a non-safety PLC with an inappropriate safety level. Always separate safety signals from regular I/O signals.
* All safety signals must use a dual-channel redundant design, with both channels remaining independent. This ensures that if one channel fails, the safety function will still be maintained.

**WARNING: ELECTRICITY**

* Make sure that the equipment is protected from water ingress. If water gets into the equipment, disconnect the power and contact technical support. Do not reconnect the power until the issue is resolved.
* Only use the robot's original cables and avoid bending the cables.
* Make sure that the power supply connected to the controller is properly grounded and avoid leaving the grounding prong of the power plug floating. **NOTICE**
* The robot has passed electromagnetic compatibility (EMC) tests according to relevant standards. Electromagnetic interference exceeding these standards may affect the robot's behavior. Extremely high signal levels or excessive exposure to electromagnetic fields may cause permanent damage to the robot. DOBOT assumes no responsibility for any damage caused by EMC issues beyond the standards.
* The length of I/O cables used to connect the controller to other machinery or equipment should not exceed 30 meters unless confirmed feasible through on-site testing. If necessary, use shielded cables.

#### 5.2 DSC controller interface

**5.2.1 Interface overview** The electrical interfaces of the DSC controller are concentrated on the front panel, with their layout shown in the figure below.

![5.2 DSC controller interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKVSw9jHsbbY3GZUOs7xC%2Fimg_d7918321591c.png?alt=media)

| No. | Description                                                                                                                                                                             |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ①   | Controller power button (maintained button). Briefly press and release to start; press again to shut down the controller and power off the robot arm. A remote switch can also be used. |
| ②   | Power interface, used to connect an external power supply.                                                                                                                              |
| ③   | Robot arm interface, for connecting the robot arm's heavy-duty cable for power supply and communication.                                                                                |
| ④   | Teach pendant / LAN2 interface. Connect a teach pendant via an adapter cable, or use as a LAN interface (default IP 192.168.200.1) for debugging or TCP/IP / Modbus TCP devices.        |
| ⑤   | LAN1 interface (default IP 192.168.5.1). Only the LAN1 IP address can be modified through DobotStudio Pro.                                                                              |
| ⑥   | USB interface, used for WiFi module connection.                                                                                                                                         |
| ⑦   | Digital I/O interface, for connecting external devices.                                                                                                                                 |
| ⑧   | I/O power interface / RS485 interface / Remote switch interface.                                                                                                                        |
| ⑨   | E-stop interface / three-position enable switch / teach pendant power interface.                                                                                                        |
| ⑩   | Analog I/O interface, for connecting external devices.                                                                                                                                  |

**5.2.2 Power interface** It connects to an external DC power supply to provide power to the controller. For the CRA series robot arm, you need to provide your own 30 – 60 V DC power supply (48 V recommended).

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff49fXYKz3oicDYgW4KPw%2Fimg_70add4020821.png?alt=media)

| Pin | Name | Definition                |
| --- | ---- | ------------------------- |
| ①   | V+   | DC 48V power positive (+) |
| ②   | V-   | DC 48V power negative (-) |
| ③   | PE   | Protective earth          |

**5.2.3 Robot arm interface** It connects to the heavy-duty receptacle on the robot arm base via a heavy-duty cable, providing both power and communication to the robot arm.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuH7Rzh8pB7RH1mg7ioqX%2Fimg_c21f6de0b1e0.png?alt=media)

| Interface                         | Pin | Name     | Definition                |
| --------------------------------- | --- | -------- | ------------------------- |
| Robot arm power interface         | ①   | V+       | DC 48V power positive (+) |
|                                   | ②   | V+       | DC 48V power positive (+) |
|                                   | ③   | V-       | DC 48V power negative (-) |
|                                   | ④   | V-       | DC 48V power negative (-) |
|                                   | ⑤   | PE       | Protective earth          |
| Robot arm communication interface | ⑥   | ECAT/CAN | Receive/Transmit data     |

The pin definitions for the ECAT/CAN communication interface are as follows:

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfkpqYFpUmwOdNrw1y6ne%2Fimg_4ef3c9ba1196.png?alt=media)

Connect to interface ① (teach pendant communication interface), and pins 5 to 10 of

**5.2.4 Teach pendant interface** interface ② (used for three-position enable switch and teach pendant power supply) via a teach pendant adapter cable.

| Pin         | Name | Definition     |
| ----------- | ---- | -------------- |
| Pin1        | TD+  | Transmit data+ |
| Pin2        | TD-  | Transmit data- |
| Pin3        | RD+  | Receive data+  |
| Pin4 / Pin5 | --   | Reserved       |
| Pin6        | RD-  | Receive data-  |
| Pin7        | CANH | CAN High       |
| Pin8        | CANL | CAN Low        |

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F23hIfIow44C2KyUOVff4%2Fimg_ccd096333747.png?alt=media)

**NOTE** Pins 1 to 4 of interface ② are designated for the E-stop button. See Emergency stop interface section for details.

| Pin | Name        | Definition                                                                              |
| --- | ----------- | --------------------------------------------------------------------------------------- |
| ①   | TP/LAN2     | Teach pendant communication interface                                                   |
| ②   | Pin5 (3PE1) | Reserved for teach pendant three-position enable switch (connect to pin 6 or 8 for 24V) |
|     | Pin6 (24V)  |                                                                                         |
|     | Pin7 (3PE2) |                                                                                         |
|     | Pin8 (24V)  |                                                                                         |
|     | Pin9 (GND)  | Reserved for power supply                                                               |
|     | Pin10 (24V) |                                                                                         |

**5.2.5 LAN interface** The small controller is equipped with two LAN interfaces for TCP/IP and Modbus TCP communication.\
The LAN1 interface has a default IP address of 192.168.5.1, which can be modified via the control software. For details, please refer to the control software's user guide. The LAN2 interface has a default IP address of 192.168.200.1 and currently does not support modification.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7NtUDT9jifSlIFp7OZN3%2Fimg_b63de84b7093.png?alt=media)

**5.2.6 USB interface** The DSC is equipped with one USB interface for connecting a wireless receiver.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FN9o1GC9JPlDakcP0yt5j%2Fimg_030b85aa143d.png?alt=media)

**5.2.7 I/O power interface** The I/O interface can be powered by either an internal or external 24 V power supply. When using the internal power supply, short-circuit the 0V and 24V pins to the nearest I/O 0V and I/O 24V pins respectively (factory default: short-circuited), as shown in the figure below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuhMtsumrfMkr3Xy98xEc%2Fimg_cd7a389932a1.png?alt=media)

If a higher total output current is required, an external 24 V power supply can be connected as shown in the figure below. The external and internal power supplies are isolated and will not interfere with each other.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg0m8GFw0xK4FsjvyNhXh%2Fimg_22fbf6a222f8.png?alt=media)

| Interface                 | Parameter | Min | Typical | Max | Unit |
| ------------------------- | --------- | --- | ------- | --- | ---- |
| Internal 24V power supply | Voltage   | 23  | 24      | 25  | V    |
|                           | Current   | 0   | -       | 2   | A    |
| External 24V power supply | Voltage   | 20  | 24      | 29  | V    |
|                           | Current   | 0   | -       | 3   | A    |

**NOTE** All subsequent chapters are based on the premise that the I/O power is connected. Instructions for I/O power wiring will not be repeated.

**5.2.8 Digital I/O interface** 16 channels for digital input and 16 for output, dedicated to reading and writing digital signals as shown below. The default type for digital signals is PNP, but it can be configured to NPN using the control software. When using the built-in I/O power supply, the voltage is 24V, with a total output current of up to 2A and a maximum single channel output of 0.5A. It supports external power supply, with a maximum current of up to 3 A. **All interfaces with identical silkscreen labels are functionally identical. Any available** **interface can be selected for connection during wiring.**

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaO7b6Ufr4ewMmAFGUkMT%2Fimg_050d377b31c2.png?alt=media)

**Digital I/O interface specifications**

| Interface                 | Parameter          | Min | Typical | Max | Unit |
| ------------------------- | ------------------ | --- | ------- | --- | ---- |
| Digital input (DI1–DI16)  | Voltage            | -3  | -       | 30  | V    |
|                           | OFF range          | -3  | -       | 5   | V    |
|                           | ON range           | 20  | -       | 30  | V    |
|                           | Current (ON range) | 2   | -       | 4   | mA   |
|                           | Type               | -   | NPN/PNP | -   | -    |
| Digital output (DO1–DO16) | Current            | 0   | -       | 0.5 | A    |

**DI wiring instruction**

1. DI connected to a simple switch: The wiring diagram is shown in the figure below. Either the PNP or NPN wiring method can be selected based on field requirements.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC70MMVm5F6wABFkHj4hE%2Fimg_1cea57a7d1e0.png?alt=media)

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4zsbQxWYpkrhgTkfIVOi%2Fimg_f0fcdb6ab065.png?alt=media)

2. DI connected to external PNP/NPN three-wire sensor: The wiring method is the same; you only need to switch between PNP and NPN modes using the control software.

* If the three-wire sensor is powered by the controller, V+ and V- need to be connected to the I/O 24V and I/O 0V of controller. The wiring configuration is shown in the figure below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcUoDbKKYuaUkd1YYwVkl%2Fimg_b907b49146a4.png?alt=media)

* If the three-wire sensor is powered by an external power source, the negative terminal of the external power source needs to be connected to the I/O 0V of the controller. The wiring configuration is shown in the figure below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQDZc3aAfLEKA8fEeV8s3%2Fimg_0e776bdaea05.png?alt=media)

**DO wiring instruction** The DO is set to PNP by default but can be configured to NPN through the control software. If the configuration in the control software is opposite to the load wiring (for instance, the software is set to PNP, but the load wiring is NPN), the load will not function properly.

* For DO configured as PNP, the wiring method to connect an external load is shown in the diagram below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQDkWToMZADENeVOfHJRy%2Fimg_77f09cf2e1a7.png?alt=media)

* For DO configured as NPN, the wiring method to connect an external load is shown in the diagram below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvv376vFs1gw9yh6cHKWw%2Fimg_d989bd75a3c5.png?alt=media)

It is recommended that there be a minimum interval of 15ms between two DI signals or two DO signals.

**5.2.9 Analog I/O interface** The analog input/output interface provides two channels each for analog signal input and output. Analog signals support either voltage (0 – 10V) or current signals (4 – 20mA), with the default set to voltage signals. You can configure it to current signals using control software. To enhance the accuracy of analog signals, it is recommended to use shielded cables or twisted pairs for connections.

**Analog I/O interface specifications**

| Interface                   | Parameter  | Min | Typical | Max | Unit |
| --------------------------- | ---------- | --- | ------- | --- | ---- |
| Analog input (voltage mode) | Voltage    | 0   | -       | 10  | V    |
|                             | Resistance | -   | 14.7    | -   | kΩ   |
|                             | Resolution | -   | 12      | -   | Bit  |
| Analog input (current mode) | Current    | 4   | -       | 20  | mA   |
|                             | Resistance | -   | 499     | -   | Ω    |
|                             | Resolution | -   | 12      | -   | Bit  |

**AI wiring instruction** The wiring diagram for connecting AI interfaces to the device under test (DUT) is shown in the figure below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4GnbFpal31CT73zsauKS%2Fimg_541a00aeeaa4.png?alt=media)

**AO wiring instruction** The wiring diagram for connecting AO interfaces to an external load is shown in the figure below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz0kJtUEd8h558TxOHfNH%2Fimg_588725cd44e8.png?alt=media)

**5.2.10 RS485 interface** The RS485 interface is primarily used for Modbus RTU communication. When connecting to an external device (e.g., a PLC), connect the 485A (or 485+) and 485B (or 485-) interfaces of both devices correspondingly. The ground wire should also be connected based on the actual field conditions.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAPAmvjqwA57Ou8OBIbsE%2Fimg_88f9afc1f539.png?alt=media)

**5.2.11 Remote switch interface** The remote switch is used for the remote power-on/off operation of the controller. Before use, ensure the controller's power button is in the pressed (ON) position. When the remote switch is closed (circuit completed), the controller powers OFF. When the remote switch is open (circuit broken), the controller powers ON. The wiring method for connecting an external switch is shown in the figure below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqqYg63GuKk2YTlLf56eq%2Fimg_974356341bf0.png?alt=media)

**5.2.12 Emergency stop interface** Connect the E-stop button for the emergency stop control of the robot arm.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2zLTNr5yEG1bO6BpSsJw%2Fimg_5d7d7793a06a.png?alt=media)

#### 5.3 Interface on the robot end

The end interface is an aviation connector located on the side of the robot arm's end flange. The pin layout and definitions are as follows.

![5.3 Interface on the robot end](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4P5g3NyZz5kJki6M3WAv%2Fimg_f28c80332221.png?alt=media)

The cable used for the tool I/O is specified by DOBOT (model: Lutronic FP-222460). The pin layout and wiring definitions for the cable are as follows.

![5.3 Interface on the robot end](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCPN3VzzWSyXAzQ4QujhQ%2Fimg_5280d85ec7b5.jpeg?alt=media)

![5.3 Interface on the robot end](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG0OlITPOTavGX1LQD9px%2Fimg_ad06a3ce2f06.png?alt=media)

| Pin | Name | Definition       |
| --- | ---- | ---------------- |
| 1   | 485A | 485A             |
| 2   | 485B | 485B             |
| 3   | DI 2 | Digital input 2  |
| 4   | DI 1 | Digital input 1  |
| 5   | 24V  | 24V output       |
| 6   | DO 2 | Digital output 2 |
| 7   | DO 1 | Digital output 1 |
| 8   | GND  | GND              |

The 24V output of the tool I/O has a maximum current of 2A (duration not exceeding 1 second), and the digital input is of PNP type. When using an external simple switch circuit as the DI input source, the wiring method is as follows.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv13rSHr7nHgrKpSeAUt0%2Fimg_9ea2261d55e0.png?alt=media)

When using a PNP three-wire sensor as the DI input source, the wiring is shown below.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl8APKFYUxZhNU3SkviAO%2Fimg_7bf4667cdbf4.png?alt=media)

The digital outputs of the end I/O can be changed between PNP and NPN types via Dobotstudio Pro, with a single-channel output current ≤ 400 mA and a total output current also not exceeding 400 mA. The wiring method is as follows.

| Pin | Cable color | Definition       |
| --- | ----------- | ---------------- |
| 1   | White       | 485A             |
| 2   | Brown       | 485B             |
| 3   | Green       | Digital input 2  |
| 4   | Yellow      | Digital input 1  |
| 5   | Gray        | 24V output       |
| 6   | Pink        | Digital output 2 |
| 7   | Blue        | Digital output 1 |
| 8   | Red         | GND              |

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FowZb8B9EkPSbGlB0mBrk%2Fimg_f86cc2385118.png?alt=media)

### 6. Transportation

#### 6.1 Transportation precautions

The robot arm should be restored to its packing posture before transportation. This can be set in DobotStudio Pro (refer to DobotStudio Pro User Guide for details). Use the original packaging for transportation. During transportation, ensure that the robot arm remains stable and is securely fastened. During transportation and long-term storage, maintain an ambient temperature range of - 20°C to +55°C, with humidity ≤95% and no condensation. When removing the robot from its packaging and moving it to the installation position, hold the robot arm with your hand until all base mounting bolts are fully tightened. After transportation, store the original packaging in a dry place for future repacking and transportation. **WARNING**

* Ensure that operators do not strain their backs or other body parts while lifting the equipment. Use appropriate lifting equipment if necessary.
* DOBOT assumes no responsibility for any damage incurred during transportation.
* Strictly follow the installation instructions when installing the robot.

#### 6.2 Unpackaged transportation

When moving the robot arm from its packaging to the installation position or relocating it, follow these handling guidelines:

* If the robot arm is not in the packing posture, restore it to the packing posture first.
* When handling and installing the robot, hold the robot arm with your hand until all base mounting bolts are fully tightened.

### 7. Installation and Use

#### 7.1 Installation environment

To maintain the performance of the controller and robot arm and ensure safe use, please place the controller and robot arm in an environment that meets the following conditions.

**NOTICE** Please make sure that the installation environment meets the following conditions to avoid potential damage.

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight and radiant heat.
* Keep away from dust, oil mist, smoke, salinity, metal powder, corrosive gases, and other contaminants.
* Do not use in a closed environment. A closed environment may cause the controller to overheat and shorten its service life.
* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Keep away from sources of electromagnetic interference.

#### 7.2 Unpacking

Upon unpacking, check the attached shipping list to ensure that all items are included. If anything is missing, please contact your supplier.

#### 7.3 Robot installation

**7.3.1 Installation platform requirements**

* When installing the robot, it must be securely fixed to a stable base. The base should be able to withstand at least 10 times the maximum torque of the J1 joint and at least 5 times the weight of the robot arm.
* If the robot arm is installed on a linear axis or a movable platform, the acceleration of the platform should be low, as high acceleration may trigger the robot’s collision detection mechanism, causing it to stop.
* If the connection cable between the robot and the controller needs to pass through a cable hole on the installation surface, the diameter of the cable hole should be no less than 30 mm.
* The Nova series robot supports both bottom cable routing and side cable routing. For side cable routing, the recommended distance between the cable routing hole and the robot base should be no less than 120mm (Calculated using L+8D, where L = 40 mm, the length of the Ethernet cable's RJ45 connector; D = 9.1 mm, the diameter of the cable).

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Flt2bq1KHDQfkw5YNgAoF%2Fimg_2e27e693be30.png?alt=media)

**7.3.2 Robot installation** The Nova series robot support 360° mounting at any angle. The figure below shows several typical installation postures.

**NOTE** The installation angle on the far left is the standard mounting angle. When installing the robot in a non-standard mounting angle, you need to calibrate the mounting angle through DobotStudio Pro after power-on. For details, refer to DobotStudio Pro User Guide.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F625q3H0JVP4abwfMvEMK%2Fimg_8e57b60afaca.jpeg?alt=media)

When installing the robot, position the mounting holes on the installation platform according to the base dimension. Then, secure the robot base to the platform using bolts. The specific dimensions of the robot base can be referenced from Mechanical Specifications. Be sure to observe the following during installation.

* During transportation, ensure that the robot is stable and properly secured in its position.
* When moving the robot arm from its packaging to the installation position, hold the robot with your hand until all bolts on the base are tightened.
* During installation, ensure the robot is properly aligned and positioned. The robot base must be secured to the platform using 4 hex bolts M6 (Nova 2) / M8 (Nova 5) (ISO898- 1: 2013, property class: 12.9) and tightened with a torque of 20 N•m.
* For wall-mounted or upside-down installations, safety measures must be taken to prevent the robot base from falling.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlhcXE7xa4IQzecteCyD2%2Fimg_807894cac5b6.png?alt=media)

**7.3.3 DSC controller installation** The DSC controller supports both horizontal and vertical installation. A minimum clearance of 50 mm must be maintained on all sides except the mounting surface to ensure sufficient heat dissipation. • **Horizontal installation** Attach the two side mounting brackets from the accessory kit to the bottom of the controller. Then, place the controller horizontally on a flat and stable surface. Secure it using M3\*4 cross recessed countersunk head screws.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTkxRuuhhZ31dhlxQkfvf%2Fimg_b626c2d5ce46.jpeg?alt=media)

**Vertical installation**• After installing the two side fixing brackets from the accessory kit onto the rear of both sides of the controller, place the controller vertically on a flat and stable mounting surface. Secure it using four M3\*4 cross recessed countersunk head screws.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEEOgU4BpquIFqJM4LJLJ%2Fimg_75f65b269630.png?alt=media)

**7.3.4 Tool installation** The robot's end flange is equipped with four M6 threaded holes, which can fix the tool to the end of the robot arm. To ensure precise alignment of the tool, the reserved Ф6 positioning holes can be used. The detailed dimensions of the end flange for the Nova series robot can be found in the Mechanical Specifications.

#### 7.4 Cable connection

**7.4.1 Precautions** **NOTICE**

* The specifications and installation method of the external cables should comply with local laws and regulations.
* Do not disassemble the robot by yourself, as this may result in electrical leakage.
* Make sure that the device is properly grounded.
* Do not bend the cable excessively, otherwise it may cause poor connections or cable breakage.
* Before connecting external devices, make sure the power outlet of the control system is disconnected. If not disconnected, may result in electric shock or device failure.
* To ensure device and personal safety, use supplied cables.
* After connection, make sure that there are no loose screws or exposed cables inside the device. **NOTICE**
* The specifications and installation method of the external cables should comply with local laws and regulations.
* Do not disassemble the robot by yourself, as this may result in electrical leakage.
* Make sure that the device is properly grounded.
* Do not bend the cable excessively, otherwise it may cause poor connections or cable breakage.
* Before connecting external devices, make sure the power outlet of the control system is disconnected. If not disconnected, may result in electric shock or device failure.
* To ensure device and personal safety, use supplied cables.
* After connection, make sure that there are no loose screws or exposed cables inside the device.

**7.4.2 Connect the DSC controller**

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6IMFYl1oKsTXtHwayrFr%2Fimg_b4c1704a4c69.png?alt=media)

\*\*Connect the heavy-duty cable:\*\*To connect the robot arm, insert the heavy-duty 1. connector into the interface on the robot arm base (NOTE: some robot models come with a pre-attached heavy-duty cable), and connect the opposite end to the robot arm (①) via the terminal block, and insert the communication cable into the ECAT/CAN interface on the controller. Specifically, connect the power wires to the power interface interface (②), ensuring all cable labels match the controller's silkscreen and securely tightening all terminal screws after wiring. **Connect the teach pendant (Optional):** Connect the teach pendant to the controller 2. (③), and connect the three-position enable switch / teach pendant power to the using the adapter cable. Plug the RJ45 connector into the TP/LAN2 Ethernet interface corresponding interface (④) via the terminal block. Ensure labels on the cable end match the controller's silkscreen markings, then securely tighten all terminal screws after wiring. to the E-stop interface (④) on the controller via the terminal block. Ensure all cable \*\*Connect the E-stop button:\*\*Connect the E-stop button (included with the controller) 3. end labels match the controller's silkscreen markings, then securely tighten all terminal screws after wiring. interface (⑤) on the controller. \*\*Connect the wireless receiver (Optional):\*\*Insert the wireless receiver into the USB 4. series robot arm; to be provided by yourself) to the power interface (⑥) on the \*\*Connect the DC power supply:\*\*Connect the DC power supply (required for CRA 5. \*\*Connect the I/O module:\*\*Connect the factory-pre-wired I/O module to the controller controller. interface (⑦) as shown in the figure below. 6.

![Nova](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMs9elq2wTRVv9mo2tkyk%2Fimg_264bbd81a43d.jpeg?alt=media)

#### 7.5 Power-on and debugging

After turning on the external power supply, press the power button on the controller. Once the indicator lights on both the end of robot arm and the controller turn solid blue, you can connect to the robot using the operation terminal, enable it, and jog it for debugging. For detailed operation instructions, refer to DobotStudio Pro User Guide. Precautions for connecting to DobotStudio Pro are as follows:

* A wired connection is recommended for communication between the robot and the DobotStudio Pro software. Wired connections improve communication security, help reduce latency, prevent interference from other devices on the internal network, and ensure that data is not intercepted by unauthorized devices.
* If an internal network is used, keep only essential devices on that network and isolate the robot's network from office or home networks.

**NOTICE** If the network is not isolated, the robot will be exposed to a complex internal network environment, making it vulnerable to cyberattacks that could lead to data leaks or downtime.

* It is recommended to use a gateway with a firewall and configure it properly to restrict communication between external devices and the robot, ensuring that only whitelisted devices can communicate with the robot. This enhances the security of the robot's network environment.

**NOTICE** Without firewall protection, the robot will face a more complex network environment and greater security risks.

* Prevent password leaks. It is recommended to raise user awareness of network security through internal training sessions. Avoid transmitting or storing sensitive information such as SSH passwords or Wi-Fi credentials via social media or email.
* Improve users' ability to identify phishing attacks and suspicious links, establish an emergency response plan, and define a clear vulnerability reporting process. If a vulnerability is found, contact DOBOT technical support promptly, share the vulnerability details, and seek a solution.

### 8. Maintenance

Maintenance and repairing must be performed in compliance with all safety instructions in this document. The purpose of maintenance and repairing is to ensure that the system is kept operational, or to return the system to an operational state in the event of a fault. Repairing includes troubleshooting in addition to the actual repair itself. Repairing must be performed by an authorized system integrator or DOBOT staff. Robots or parts returned to DOBOT should follow the instructions below:

* Remove all parts that do not belong to DOBOT.
* Before returning to DOBOT, please make a backup copy of the files. DOBOT will not be responsible for the loss of programs, data or files stored in robot.
* The robot should move to the package point before returning to DOBOT.

#### 8.1 Safety instructions

The following safety procedures and warnings must be observed when operating the robot arm or controller: **NOTICE**

* Replace faulty components with new components of the same model or equivalent components approved by DOBOT.
* Reactivate all deactivated safety measures immediately after completing maintenance work.
* Record all repairs and save them in the technical document associated with the robot system.
* Remove the main input cable from the back of the robot to ensure it is fully powered off. Take necessary precautions to prevent others from reconnecting the system power during maintenance.
* Observe ESD regulations when disassembling the robot.
* Prevent water or dust from entering the interior of the robot.

#### 8.2 Robot maintenance

To ensure the robot maintains high performance over the long term, regular maintenance checks must be conducted. The personnel in charge of the maintenance must develop a maintenance plan and carry out the necessary tasks. The inspection items are listed in the table below.

| Period | Inspection item | Inspection details                                                          |
| ------ | --------------- | --------------------------------------------------------------------------- |
| Daily  | Robot cleaning  | Wipe off dirt, dust, cutting residue on the body with water or 10% alcohol. |

The bolt tightening torques are shown in Table 8.2. The tightening torques vary depending on the type of bolt or base material. If not listed in the table, please contact DOBOT technical support.

**NOTICE** For a list of wearable parts, please contact DOBOT technical support.

| Period   | Inspection item     | Inspection details                                                                                                |
| -------- | ------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Daily    | Robot cleaning      | Wipe off dirt, dust, and cutting residue on the body.                                                             |
| Daily    | Joint bolts         | Check the torque of exposed bolts based on the specified tightening torque table.                                 |
| Daily    | Tool mounting bolts | Check the torque based on the specified tightening torque table.                                                  |
| Daily    | Motor               | Confirm abnormal heating or sound.                                                                                |
| Daily    | Brake               | Check whether the robot arm or end-effector will fall when the servo is powered off.                              |
| 3 months | Reducer             | Check abnormal vibration, noise, and oil leakage.                                                                 |
| 6 months | Cables              | Inspect power cables, heavy-duty cables, and IO cables to ensure stable connections and check for wear or damage. |

| Nominal thread diameter | Outer hexagonal bolt (joint) | Inner hexagonal bolt (12.9) | Inner hexagonal bolt (rear cover) |
| ----------------------- | ---------------------------- | --------------------------- | --------------------------------- |
| 3 mm                    | 2 Nm                         | 2.4 Nm                      | 0.7 Nm                            |
| 4 mm                    | 4 Nm                         | 4.5 Nm                      | -                                 |
| 5 mm                    | 7.5 Nm                       | 9 Nm                        | -                                 |
| 6 mm                    | 15 Nm                        | 18 Nm                       | -                                 |
| 8 mm                    | -                            | 37 Nm                       | -                                 |

### 9. Disposal and Environment Protection

DOBOT robots must be disposed of in accordance with the applicable national laws, regulations and standards. The following symbol indicates that the product must not be disposed of as general waste.

![9. Disposal and Environment Protection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgMqQWCh7d04CHfSwpSfg%2Fimg_936a10286683.png?alt=media)

### 10. Warranty

#### 10.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, DOBOT shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repair the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the device or components that are replaced or returned to DOBOT shall remain with DOBOT. Any other claims arising from or related to the device are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, DOBOT reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the device, DOBOT shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production device.

#### 10.2 Disclaimer

DOBOT is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. DOBOT strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

### Appendix Technical Specifications

#### Appendix A Robot technical specifications

| Parameter                 | Nova 2                                       | Nova 5                                       |
| ------------------------- | -------------------------------------------- | -------------------------------------------- |
| Weight                    | 11 kg (24.3 lb)                              | 14 kg (30.9 lb)                              |
| Rated load                | 2 kg (4.4 lb)                                | 5 kg (11 lb)                                 |
| Working radius            | 625 mm (24.6 inch)                           | 850 mm (33.5 inch)                           |
| Max working speed         | 1.6 m/s (63 inch/s)                          | 2 m/s (78.7 inch/s)                          |
| Joint working range       | J1 ±360°, J2 ±180°, J3 ±156°, J4/J5/J6 ±360° | J1 ±360°, J2 ±180°, J3 ±160°, J4/J5/J6 ±360° |
| Max joint speed           | 135°/s (all joints)                          | 100°/s (all joints)                          |
| Tool IO                   | DI 2 channels, DO 2 channels                 | DI 2 channels, DO 2 channels                 |
| RS485                     | Support                                      | Support                                      |
| Repeatability             | ±0.05 mm                                     | ±0.05 mm                                     |
| IP rating                 | IP54                                         | IP54                                         |
| Noise                     | 65 dB(A)                                     | 70 dB(A)                                     |
| Ambient temperature       | 0°C – 50°C                                   | 0°C – 50°C                                   |
| Typical power consumption | 100 W                                        | 230 W                                        |
| Maximum power consumption | 250 W                                        | 770 W                                        |
| Installation mode         | Any angle                                    | Any angle                                    |
| Cable length              | 3 m (118.1 inch)                             | 3 m (118.1 inch)                             |
| Material                  | Aluminum alloy, ABS                          | Aluminum alloy, ABS                          |

**Noise**65 dB(A) 70 dB(A) 0℃ – 50℃ 0\~50℃

**Ambient**

**temperature**

**Typical power** 100 W 230 W

**consumption**

**Maximum power** 250 W 770 W

**consumption** **Installation mode**Any angle Any angle **Cable length**①\*\*\*\*3 m 3 m 118.1 inch 118.1 inch **Material**Aluminum alloy, ABS Aluminum alloy, ABS ① : Cable length from robot arm to controller

#### Appendix B Controller technical specifications

| Parameter           | Specification                                                                                                         |
| ------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Product name        | DOBOT DSC                                                                                                             |
| Size                | 220 mm × 150 mm × 45 mm (8.66 × 5.91 × 1.77 inch)                                                                     |
| Weight              | 1.2 kg (2.65 lb)                                                                                                      |
| Input power         | 30–60 V DC                                                                                                            |
| IO power            | 24V; built-in power supply max 2A, external power supply max 3A, single channel max 0.5A                              |
| General I/O         | DI 16 channels (NPN/PNP); DO 16 channels (NPN/PNP); AI 2 channels (0–10V, 4–20mA); AO 2 channels (0–10V, 4–20mA)      |
| Safety I/O          | SI/SO 16 channels (DI/DO configured via control software)                                                             |
| Remote power on/off | Supported                                                                                                             |
| Communication       | 2 Ethernet interfaces (teach pendant, TCP/IP, Modbus TCP, EtherNet/IP, Profinet); 1 USB (Wi-Fi); 1 RS485 (Modbus RTU) |
| Environment         | 0°C – 50°C, ≤95% non-condensing humidity                                                                              |
| IP rating           | IP22                                                                                                                  |
| Cooling method      | Fan cooling                                                                                                           |
| Teaching method     | Teach pendant, PC, APP                                                                                                |

#### Appendix C Functional Safety

**C.1 Safety requirements** The safety functions generally comply with EN ISO 10218-1 and specifically meet the following requirements. When a safety-related control system is required, the safety-related components shall be designed so that:

* A single fault in any component does not lead to the loss of the safety function.
* Where reasonably practicable, a single fault is detected at or before the next demand on the safety function.
* When a single fault occurs, the safety function remains operational, and the system remains in a safe state until the detected fault is rectified.
* All reasonably foreseeable faults shall be detected. This requirement is considered equivalent to Category 3 as described in ISO 13849-1. Category 3 is typically achieved through redundant circuits, such as dual-channel. The safety functions and the robot controller comply with Performance Level d (PLd) according to ISO 13849-1.

**C.2 Stop categories** According to IEC 60204-1, the Nova series robots provide three stop categories: Stop Category 0, Stop Category 1, and Stop Category 2. Stop Category 0 is an uncontrolled stop, while Stop Category 1 and Stop Category 2 are controlled stops.

* When Stop Category 0 is triggered, the robot’s power is cut off immediately, and the robot stops instantaneously.
* When Stop Category 1 is triggered, the robot decelerates to a stop. After the robot stops, power to the robot is disconnected.
* When Stop Category 2 is triggered, the robot decelerates to a stop along its programmed trajectory. After stopping, the robot remains enabled.

**C.3 Overview** The Nova series robot system features 30 safety functions, designed and tested in accordance with the following standards:

* IEC 60204-1:2018+A1:2025
* ISO 13849-1: 2023
* ISO 13849-2:2012 Safety functions can be divided into the following four categories:
* Safety SI (Safe Input) Category
* Safety SO (Safe Output) Category
* Safety Limit Category
* Other

| Category  | SF   | Name                                | Stop category       | Response time | Stop distance | Assessment |
| --------- | ---- | ----------------------------------- | ------------------- | ------------- | ------------- | ---------- |
| Safety SI | SF1  | Emergency Stop (System)             | 1                   | ≤300 ms       | ≤300 mm       | PLd/Cat. 3 |
|           | SF2  | Emergency Stop (User)               | 1                   | ≤300 ms       | ≤300 mm       | PLd/Cat. 3 |
|           | SF3  | Safeguard Stop                      | 2                   | ≤500 ms       | ≤500 mm       | PLd/Cat. 2 |
|           | SF4  | Safeguard Stop Reset Input          | 2                   | ≤500 ms       | ≤500 mm       | PLd/Cat. 2 |
|           | SF5  | Reduced Mode Input                  | 1                   | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|           | SF6  | Mode Switch Input (Manual/Auto)     | 2                   | ≤500 ms       | ≤500 mm       | PLd/Cat. 2 |
|           | SF7  | 3-Position Enabling Device Input    | 1                   | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
| Safety SO | SF8  | Emergency Stop Status Output        | DO output low level | ≤10 ms        | NA            | PLd/Cat. 3 |
|           | SF9  | System Emergency Stop Status Output | DO output low level | ≤10 ms        | NA            | PLd/Cat. 3 |
|           | SF10 | Safeguard Stop Status Output        | DO output low level | ≤10 ms        | NA            | PLd/Cat. 3 |

| Category     | SF   | Name                                      | Stop category | Response time | Stop distance | Assessment |
| ------------ | ---- | ----------------------------------------- | ------------- | ------------- | ------------- | ---------- |
| Safety Limit | SF15 | Joint Position Limit (Soft Axis Limiting) | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF16 | Pose Limit (Safety Zone)                  | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF17 | Joint Speed Limit                         | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF18 | TCP Speed Limit                           | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF19 | TCP Speed Limit in Teaching Mode          | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF20 | Momentum Limit                            | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF21 | Stopping Time Limit                       | 0             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF22 | Stopping Distance Limit                   | 0             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF23 | Power Limit                               | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |
|              | SF24 | TCP Force Limit                           | 1             | ≤300 ms       | ≤300 mm       | PLd/Cat. 2 |

**C.4 Detailed description**

**SF1 System Emergency Stop**

* The robot can be triggered into emergency stop state via the emergency stop button or the emergency stop switch on the teach pendant, performing a Category 1 stop.
* The system emergency stop input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into emergency stop state.
* When the safety controller detects that the emergency stop button has been pressed, it notifies the servo to perform an emergency stop and monitors the stopping time. If the stopping time exceeds the stopping time limit, a Category 0 stop is executed.

**SF2 User Emergency Stop**

* The robot can be triggered into emergency stop state via the user emergency stop input signal in Safety SI, performing a Category 1 stop.
* The user emergency stop input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into emergency stop state. The emergency stop logic is the same as that of the system emergency stop.
* Any DI can be configured for this function, but both channels must be configured simultaneously.

**SF3 Safeguard Stop**

* The robot can be triggered into safeguard stop state via the safeguard stop input signal in Safety SI, performing a Category 2 stop.
* The safeguard stop input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into the safeguard stop state. In this state, starting a program is not allowed if no program is running, and any running program will be paused.
* Any DI can be configured for this function, but both channels must be configured simultaneously.

**SF4 Safeguard Stop Reset**

* Used in conjunction with the safeguard stop signal: When no reset signal is configured, the robot program automatically resumes running after the safeguard stop signal is cleared. When a reset signal is configured, after the safeguard stop signal is cleared, the safeguard stop reset must be triggered first, followed by clicking "Resume" for the robot program to automatically continue running.
* The safeguard stop reset input is set by default to a normally open signal with a high level. A rising edge on both channels triggers the reset of the safeguard stop state, and the time interval between the two channel triggers must be ≤ 100 ms.
* Any DI can be configured for this function, but both channels must be configured simultaneously.

**SF5 Reduced Mode**

* The robot can be triggered into reduced mode via the reduced mode input signal in Safety SI.
* In reduced mode, the robot's motion speed and safety limits switch to the values configured for reduced mode (i.e., reduced parameters). The robot monitors and alarms according to these reduced parameters. When an alarm is triggered, a Category 1 stop is executed.
* The reduced mode input is set by default to a normally closed signal with a high level. A low level on either channel triggers the robot into reduced mode. When the input returns to high level, the robot exits reduced mode and enters normal mode.
* Any DI can be configured for this function, but both channels must be configured simultaneously.

**SF6 Manual/Auto Mode Switch**

* When the manual/auto mode switch function is enabled in the safety settings, the robot can be switched between manual and auto modes via the manual/auto mode switch input signal in Safety SI. A low level on either channel triggers the robot to enter manual mode. When both channels are at high level, the robot enters auto mode.
* Any DI can be configured for this function, but both channels must be configured simultaneously.
* Once this function is configured, disabling the manual/auto mode function in the settings will prompt the user that it cannot be disabled.

**SF7 3-Position Enabling**

* In manual mode, the robot can be triggered into the enabled state via the 3- position enabling input signal in Safety SI. A low level on either channel triggers the robot into the disabled state, while a high level on both channels triggers the enabled state. The characteristics of the external 3-position enabling device are identical to those of the 3-position enabling switch on the teach pendant when it is set to the enabled state.
* The 3-position enabling signal is not active in automatic mode.
* Any DI can be configured for this function, but both channels must be configured simultaneously.

**SF8 Emergency Stop Status Output**

* When the robot is in the emergency stop state, the emergency stop status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.
* The maximum output current per channel is 500 mA (this applies to all single- channel outputs described below).

**SF9 System Emergency Stop Status Output**

* When the robot is in the system emergency stop state, the system emergency stop status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously. **NOTE:** This signal is primarily used when interlocking two safety devices to prevent the emergency stop state from becoming locked and unrecoverable.

**SF10 Safeguard Stop Status Output**

* When the robot is in the safeguard stop state, the safeguard stop status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.

**SF11 Reduced Mode Status Output**

* When the robot is in the reduced mode state, the reduced mode status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.

**SF12 Moving Status Output**

* When one or more joints of the robot move faster than 1°/s (excluding drag teaching mode), the robot is considered to be in the moving state. In this state, the moving status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.

**SF13 Not Stopping Status Output**

* When the robot is in automatic mode and the program is not paused, the robot is considered to be in the not stopping state. In this state, the not stopping status output signal in Safety SO outputs a low level; otherwise, it outputs a high level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.

**SF14 Safe Home Position Status Output**

* When the robot is within ±10mm of the safe home position set by the control software, the safe home position status output signal in Safety SO outputs a high level; otherwise, it outputs a low level.
* Any DO can be configured for this function, but both channels must be configured simultaneously.

**SF15 Joint Position Limit**

* The robot uses proper motion planning to prevent each joint from exceeding the allowable motion range set by the control software.
* If a joint exceeds its allowable motion range, a safety controller alarm is triggered and a Category 1 stop is executed.

**SF16 Safety Zone Limit**

* Two types of safety zones can be defined: alarm safety zone and reduced safety zone. When configured as an alarm safety zone, the robot uses proper motion planning to prevent the currently active TCP from entering the unsafe zone. If the TCP enters the unsafe zone, a safety controller alarm is triggered and a Category 1 stop is executed. When configured as a reduced safety zone, if the robot enters the unsafe zone, it switches to reduced mode, and the safety controller monitors the robot using reduced mode parameters.
* Two methods are available for defining the robot's safety zone: Safety Wall: When configured as a physical wall (alarm wall) or a virtual wall (reduced wall), the positive direction of the wall is the safe zone, and the opposite direction is the unsafe zone. Safety Zone: When configured with "Alarm" or "Reduced" behavior, the positive direction of the safe side is the safe zone, and the opposite direction is the unsafe zone.

**SF17 Joint Speed Limit** During automatic program execution, the robot uses proper motion planning to prevent joint speeds from exceeding the safety limits set by the control software. If any joint speed exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

**SF18 TCP Speed Limit**

* During automatic program execution, the robot uses proper motion planning to prevent TCP speed from exceeding the safety limit set by the control software. If TCP speed exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.

**SF19 TCP Speed Limit in Manual Mode** In manual mode, the robot uses proper motion planning to prevent TCP speed from exceeding the safety limit set by the control software. If TCP speed exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

**SF20 Momentum Limit**

* During automatic program execution, the robot uses proper motion planning to prevent the total momentum of the robot from exceeding the safety limit set by the control software. If the total momentum exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.

**SF21 Stopping Time Limit**

* During automatic program execution, the robot uses proper motion planning to ensure that when an alarm stop is triggered at any point, the stopping time does not exceed the safety limit set by the control software. If the actual stopping time exceeds the safety limit, a safety controller alarm is triggered and a Category 0 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.

**SF22 Stopping Distance Limit**

* During automatic program execution, the robot uses proper motion planning to ensure that when an alarm stop is triggered at any point, the stopping distance does not exceed the safety limit set by the control software. If the actual stopping distance exceeds the safety limit, a safety controller alarm is triggered and a Category 0 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.

**SF23 Power Limit**

* Based on the power safety limits set by the control software, the robot calculates the allowable fluctuation range of the actual torque at each joint and limits the actual torque magnitude to prevent the sum of power calculated from the difference between the planned torque and the actual torque at each joint from exceeding the safety limit. If the deviation between actual power and planned power exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.

**SF24 TCP Force Limit**

* Based on the TCP force safety limits set by the control software, the robot calculates the allowable fluctuation range of the actual torque at each joint and limits the actual torque magnitude to prevent the sum of TCP force calculated from the difference between the planned torque and the actual torque at each joint from exceeding the safety limit. If the deviation between actual TCP force and planned TCP force exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.
* Normal mode and reduced mode each have their own set of safety limits, which are applied for monitoring and alarm purposes.

**SF25 Joint Torque Limit** The robot continuously monitors the actual joint torque values. If the torque exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

**SF26 TCP Position Deviation Limit** The robot continuously monitors the deviation between the actual TCP position and the target TCP position. If the deviation exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

**SF27 Start/Restart Interlock** When starting or restarting, the robot is in the disabled state and cannot run automatically. To start the robot, you must first enable it and then press the run button. After enabling, the safety controller continuously monitors the deviation between the actual position and the target position of each joint via the encoder. If the deviation exceeds the safety limit, a safety controller alarm is triggered and a Category 1 stop is executed.

**SF28 Normal Stop**

* The robot can be triggered into the stop state via an external button, performing a Category 1 stop.
* The normal stop input is set by default to a normally closed signal with a high level. A falling edge on either channel triggers the robot into the normal stop state.
* When the safety controller detects that the external button has been pressed, it notifies the servo to perform a Category 1 stop and monitors the stopping time. If the stopping time exceeds the stopping time limit, a Category 0 stop is executed.

**SF29 Hand-Guided Control (Drag Teaching)**

* The robot can only enter hand-guided control mode when it is in a Category 2 stop state.
* When the hand-guided control button is pressed, the robot can be manually moved. When the button is released, a Category 2 stop is executed.
* In hand-guided control mode, the TCP speed is limited to the user-configured value, with a maximum upper limit of 250 mm/s.
* In hand-guided control mode, position limits remain in effect.

**SF30 Hold-to-Run Control**

* When the hand-guided control button is pressed, the robot can be manually moved.
* When the button is released, a Category 2 stop is executed.

#### Appendix D Applicable Standards

| Category         | Standards                                                                                                                                                                                                                                 |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Safety Standards | UL 1740 (4th Ed., Aug 2023); NFPA 79-2024; CAN/CSA Z434-14 (R2019); ANSI/RIA R15.06-2012; CSA C22.2 No. 301:23; EN ISO 10218-1:2011; EN 60204-1:2018+A1:2025; EN ISO 12100:2010; ISO/TS 15066:2016; EN ISO 13849-1:2023; ISO 13849-2:2012 |
| EMC Standards    | EN IEC 61000-6-2:2019; EN IEC 61000-6-4:2019; EN 55011:2016+A1:2017+A2:2021                                                                                                                                                               |
