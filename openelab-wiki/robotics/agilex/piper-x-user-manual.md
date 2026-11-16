# PiPER-X User Manual

## AgileX PiPER-X 6-DOF Robotic Arm for Manipulation Research

{% embed url="https://openelab.io/products/agilex-piper-x-robot-arm" %}

![Official PiPER-X manual figure 1](<../../.gitbook/assets/Official PiPER-X manual figure 1 (1)>)

### Version Update Log

| No. | Version | Date      | Modified By | Reviewer    | Remarks                   |
| --- | ------- | --------- | ----------- | ----------- | ------------------------- |
| 1   | V.1.0.0 | 2026/1/5  | Dennis      | <p><br></p> | Initial document creation |
| 2   | V.1.1.0 | 2026/1/25 | Dennis      | <p><br></p> | Document finalized        |
| 3   | V.1.2.0 | 2026/3/9  | Felix       | <p><br></p> | Document translation      |

***

## **Important Safety Information**

This chapter contains important safety information. All individuals and organizations must read and understand this information before using the equipment, especially before the first power-on. It is essential to follow and execute all assembly instructions and guidelines in this manual. Pay special attention to text marked with warning symbols. Before using the equipment, please obtain and read the _PiPER-X User Manual_. For any questions regarding use, please contact support@agilex.ai.

> **Warning Symbol: ⚠** This indicates situations that may cause danger. If not avoided, they may result in personal injury, property damage, or serious equipment damage.

> **Warning ⚠:** AgileX Robotics shall not be held liable if the robotic arm is damaged, altered, or modified in any way. AgileX Robotics shall not be liable for any damage to the robotic arm or any other equipment caused by program errors or operational failures.

**Limitation of Liability:** By using this robotic arm, you are deemed to have read, understood, acknowledged, and accepted all terms and content of the User Manual and Safety Information. The user agrees to be responsible for their own actions and all consequences arising therefrom. The user agrees to use the robotic arm only for legitimate purposes and agrees to these terms and any policies or guidelines that AgileX Robotics may establish. When using the robotic arm, strictly follow and execute the requirements including but not limited to the User Manual and Safety Information. AgileX Robotics shall not be liable for personal injury, accidents, property damage, legal disputes, or conflicts of interest caused by violations of the stated usage requirements or force majeure. The robotic arm is not suitable for persons under 18 years of age or those without full legal capacity. Please prevent such persons from coming into contact with this product and exercise extra caution when operating in their presence.

The information in this manual does not cover the design, installation, and operation of a complete robotic arm application system, nor does it cover all peripheral equipment that may affect the safety of such a system. The design and use of the complete system must comply with the safety requirements established in the standards and regulations of the country where the robotic arm is installed.

Integrators and end customers of the robotic arm are responsible for ensuring compliance with relevant regulations and applicable laws, and for ensuring that there are no significant hazards in the complete robotic arm application. This includes but is not limited to:

#### 1. **Validity**

* Conduct a risk assessment of the complete robotic arm system.
* Connect additional safety equipment for other machinery as defined by the risk assessment.
* Verify that the design and installation of the entire robotic arm system, including software and hardware, are correct.
* The relevant functions of this robotic arm require integrators and end customers to conduct safety assessments in accordance with relevant regulations and applicable laws to ensure that the developed robotic arm has no significant hazards or safety risks in actual applications.
* Be aware of potential safety risks before operating and using the equipment.
* Ensure that users do not modify any safety measures.
* Collect all documents in the technical file, including the risk assessment and this manual.

#### 2. **Environment**

* Before first use, carefully read this manual to understand basic operations and operating procedures.
* Use in a relatively open area. The robotic arm itself does not have any automatic obstacle avoidance or sensing sensors.
* Operate in ambient temperatures of -20°C to 50°C.
* If the robotic arm is not custom-ordered with a specific IP rating, its water and dust resistance is IP22.

#### 3. **Inspection**

* Ensure the robotic arm shows no obvious abnormalities.
* Ensure cable connections are normal during use.

#### 4. **Operation**

* Ensure the surrounding area is relatively open during operation.
* Operate within line of sight.
* The maximum payload of the robotic arm is 1.5 kg. Ensure the effective payload does not exceed 1.5 kg during use.
* When the equipment shows abnormalities, stop use immediately to avoid secondary injury.
* When the equipment shows abnormalities, contact relevant technical personnel. Do not attempt to handle it yourself.
* Use the equipment in environments that meet the IP protection rating requirements according to the device’s IP rating.

#### 5. **Usage Warnings ⚠:**

* Ensure the robotic arm and tools/end effectors are always correctly and securely fixed in place.
* When it is necessary to enter the robotic arm workspace, protective goggles and protective equipment must be worn.
* Ensure the robotic arm has sufficient space to move freely.
* Do not wear loose clothing when operating the robotic arm. Ensure long hair is tied back when operating.
* Do not use the robotic arm if it is damaged or shows any abnormality.
* If the host computer software displays error messages, perform emergency stop immediately and contact relevant technical personnel.
* Keep the head, face, and other body parts outside the reach of the robotic arm being operated or about to be operated.
* Never modify the robotic arm. Modifications may cause unpredictable hazards for integrators.
* Do not expose the robotic arm to permanent magnetic fields. Strong magnetic fields can damage the robotic arm.
* The robotic arm generates heat during operation. Do not handle or touch the robotic arm while it is operating or immediately after stopping, as prolonged contact may cause discomfort. Disconnect power and wait one hour for the robotic arm to cool down.
* Connecting different machinery may increase hazards or create new hazards. Always conduct a comprehensive risk assessment of the entire installation. Different functional safety levels may apply based on the risk assessment; therefore, when different safety and emergency stop performance levels are required, always select the highest performance level. Always read and understand the manuals of all equipment used in the installation.
* The robotic arm is not suitable for persons under 18 years of age or those without full legal capacity.

***

## 1. Robotic Arm Introduction

This 6-DOF (degree of freedom) robotic arm is designed for education and research, consumer applications, and industrial automation. It has a payload capacity of 1.5 kg and is suitable for humanoid robots, automatic assembly, automatic handling, and various other research and industrial applications. Six rotary joints provide full-range operational flexibility with high precision and repeatability. The robotic arm features a modular design for easy maintenance and upgrades. It provides an intuitive user interface that simplifies programming and operation, allowing even non-professionals to get started quickly. It can be widely used in scientific research, education, automotive manufacturing, electronic assembly, food processing, laboratory automation, and medical device operation.

### 1.1 Product List

| Item                                     | Quantity |
| ---------------------------------------- | -------- |
| 6-DOF Robotic Arm PIPER-X                | 1        |
| Power Adapter (adapter + power cord)     | 1        |
| Communication Module (USB to CAN module) | 1        |
| Aviation Connector                       | 1        |
| Base Mounting Screws                     | 4        |
| Base Installation Wrench                 | 1        |

### 1.2 Performance Parameters

| Parameter Type                                                                                                                                                                                           | Item                                                        | Specification                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Structural Parameters                                                                                                                                                                                    | Degrees of Freedom                                          | 6                                                                                                     |
| Payload                                                                                                                                                                                                  | 1.5 kg                                                      |                                                                                                       |
| Body Weight                                                                                                                                                                                              | 4.5 kg                                                      |                                                                                                       |
| Repeatability                                                                                                                                                                                            | ±0.1 mm                                                     |                                                                                                       |
| Working Radius                                                                                                                                                                                           | 669.59 mm                                                   |                                                                                                       |
| Standard Supply Voltage                                                                                                                                                                                  | DC 24V                                                      |                                                                                                       |
| Power Consumption                                                                                                                                                                                        | Max ≤120W, Average ≤40W                                     |                                                                                                       |
| Material                                                                                                                                                                                                 | Aluminum alloy frame, plastic housing                       |                                                                                                       |
| Controller                                                                                                                                                                                               | Integrated                                                  |                                                                                                       |
| Communication                                                                                                                                                                                            | CAN                                                         |                                                                                                       |
| Control Method                                                                                                                                                                                           | Drag teaching / Offline trajectory / API / Host computer    |                                                                                                       |
| External Interfaces                                                                                                                                                                                      | Power interface ×1, CAN interface ×1                        |                                                                                                       |
| Base Mounting Dimensions                                                                                                                                                                                 | 70mm × 70mm, M5×4                                           |                                                                                                       |
| Operating Environment                                                                                                                                                                                    | Temperature: -20 to 50°C, Humidity: 25%-85%, non-condensing |                                                                                                       |
| Noise                                                                                                                                                                                                    | <60 dB                                                      |                                                                                                       |
| Installation                                                                                                                                                                                             | Desktop mounting                                            |                                                                                                       |
| Motion Parameters                                                                                                                                                                                        | Joint Motion Range                                          | <p>J1:±154°</p><p>J2:0°~195°</p><p>J3:-175°~0°</p><p>J4:-90°~90°</p><p>J5:-90°~90°</p><p>J6:±165°</p> |
| <p><br></p>                                                                                                                                                                                              | Joint Max Speed                                             | <p>J1:180°/s</p><p>J2:195°/s</p><p>J3:180°/s</p><p>J4:225°/s</p><p>J5:225°/s</p><p>J6:225°/s</p>      |
| **Note:** The above data are test results of AgileX robotic arms in controlled test environments. Results may vary under different environments and usage conditions. Please refer to actual experience. |                                                             |                                                                                                       |

#### Two-Finger Gripper Parameters (Optional)

| Item                     | Specification                                               |
| ------------------------ | ----------------------------------------------------------- |
| Body Weight              | 500 g                                                       |
| Precision                | ±0.5 mm                                                     |
| Opening Range            | 0-100 mm                                                    |
| Rated Gripping Force     | 40 N                                                        |
| Max Gripping Force       | 50 N                                                        |
| Supply Voltage           | DC 24V                                                      |
| Power Consumption        | Max ≤50W, Average ≤30W                                      |
| Contact Surface Material | Rubber                                                      |
| Controller               | Integrated                                                  |
| Communication            | CAN                                                         |
| Control Method           | Drag teaching / Offline trajectory / API / Host computer    |
| External Interfaces      | Power interface ×1, CAN interface ×1                        |
| Mounting Method          | Flange mounting                                             |
| Operating Environment    | Temperature: -20 to 50°C, Humidity: 25%-85%, non-condensing |
| Noise                    | <60 dB                                                      |

#### Teach Pendant Parameters (Optional)

| Item                     | Specification                                               |
| ------------------------ | ----------------------------------------------------------- |
| Body Weight              | 550 g                                                       |
| Precision                | ±0.5 mm                                                     |
| Opening Range            | 0-100 mm                                                    |
| Rated Gripping Force     | 40 N (force control, force feedback)                        |
| Max Gripping Force       | 50 N (force control, force feedback)                        |
| Supply Voltage           | DC 24V                                                      |
| Power Consumption        | Max ≤50W, Average ≤30W                                      |
| Contact Surface Material | Rubber                                                      |
| Controller               | Integrated                                                  |
| Communication            | CAN                                                         |
| Control Method           | Drag teaching / Offline trajectory / API / Host computer    |
| External Interfaces      | Power interface ×1, CAN interface ×1                        |
| Mounting Method          | Flange mounting                                             |
| Operating Environment    | Temperature: -20 to 50°C, Humidity: 25%-85%, non-condensing |
| Noise                    | <60 dB                                                      |

#### Modified DH Parameters

| **Link** | **d (mm)** | **a (mm)** | **alpha (radians)** | **offset (radians)** |
| -------- | ---------- | ---------- | ------------------- | -------------------- |
| L(1)     | 123        | 0          | 0                   | π                    |
| L(2)     | 0.0        | 0.0        | π/2                 | π×7.78/180           |
| L(3)     | 0.0        | 285.03     | 0.0                 | 162.61/180×π         |
| L(4)     | 0          | 273.64     | 0                   | π×4.62/180           |
| L(5)     | 0          | 74.66      | -π/2                | π/2                  |
| L(6)     | 35.26      | 0.0        | π/2                 | 0                    |

***

## 2. Basic Introduction

This robotic arm has 6 degrees of freedom and a 1.5 kg end-effector payload. Six rotary joints provide full-range operational flexibility with high precision and repeatability. The lightweight design enables both fast motion and high load capacity, making it suitable for embodied intelligence applications and real-world data collection.

![Official PiPER-X manual figure 2](<../../.gitbook/assets/Official PiPER-X manual figure 2 (1)>)

### 2.1 Electrical Interface Description

The robotic arm package includes an aviation connector, USB-to-CAN module, data cable, adapter, and a reserved XT30 2+2 interface on the end motor. Please follow the instructions below for use.

#### 2.1.1 Arm Base Electrical Interface Diagram

![Official PiPER-X manual figure 3](<../../.gitbook/assets/Official PiPER-X manual figure 3 (1)>)

| 1 | Power & Communication Port      | 2           | Status Indicator |
| - | ------------------------------- | ----------- | ---------------- |
| 3 | Main Controller - J2 Connection | 4           | Power Positive   |
| 5 | Power Negative                  | 6           | CAN-H            |
| 7 | CAN-L                           | <p><br></p> | <p><br></p>      |

> **Note:** Align the red dot on the connector with the red dot on the cable. The textured area on the aviation connector is the retractable force-bearing area. During installation, align the red dot downward with the protrusion and insert directly. To remove, press the textured area and pull out. See installation diagram below:

![Official PiPER-X manual figure 4](<../../.gitbook/assets/Official PiPER-X manual figure 4 (1)>)

**Electrical Panel Position 2 Indicator Light Description:**

| Indicator Color | Status                                                   |
| --------------- | -------------------------------------------------------- |
| Green flashing  | Robotic arm operating normally                           |
| Green solid     | Main controller initialization/startup                   |
| Red flashing    | Robotic arm error or upgrade mode; troubleshoot if error |

**End Joint Teaching Indicator Description:**

| Teaching Indicator | Status                                             |
| ------------------ | -------------------------------------------------- |
| No light           | Drag teaching stopped / Trajectory recording ended |
| Green solid        | Robotic arm in trajectory recording mode           |
| Green flashing     | Robotic arm in trajectory playback mode            |

**Main Controller CAN Termination Resistor Switch:**

The main controller CAN termination resistor switch is used when one master arm controls multiple slave arms. **Single arm use does not require adjustment.** Factory default: 1 ON (down), 2 OFF (up), resulting in 60Ω termination. When more than two slave arms: one slave arm has 1 ON (down), 2 OFF (up); others have both 1 and 2 OFF (up).

![Official PiPER-X manual figure 5](<../../.gitbook/assets/Official PiPER-X manual figure 5 (1)>)

#### 2.1.2 End Connection Electrical Description

The end joint has a reserved XT30 2+2 interface for power and CAN. See diagram below. Voltage 24V, current 2A MAX. The end CAN communication is only compatible with AgileX devices. Do not connect other CAN devices without authorization, as this may cause uncontrollable damage.

![Official PiPER-X manual figure 6](<../../.gitbook/assets/Official PiPER-X manual figure 6 (1)>)

#### 2.1.3 Power-On Instructions

For first power-on, follow steps A-G in order:

1. Connect J2 connector (A).
2. Connect CAN cables (B) on aviation connector.
3. Connect XT30 connectors (C).
4. Connect aviation connector (D) with red dot downward.
5. Connect adapter plug (E).
6. Check and confirm adapter AC plug is connected, power on, and wait for green indicator on electrical panel.
7. Connect USB cable to computer for use.

![Official PiPER-X manual figure 7](<../../.gitbook/assets/Official PiPER-X manual figure 7 (1)>)

**Note:** Align the red dot on the connector with the red dot on the cable. The textured area on the aviation connector is the retractable force-bearing area. During installation, align the red dot downward with the protrusion and insert directly. To remove, press the textured area and pull out.

![Official PiPER-X manual figure 8](<../../.gitbook/assets/Official PiPER-X manual figure 8 (1)>)

### 2.2 Robotic Arm Coordinate System

#### 2.2.1 Origin Coordinate System (Same as PIPER Standard)

PIPER-X origin (x:0, y:0, z:0) position:

![Official PiPER-X manual figure 9](<../../.gitbook/assets/Official PiPER-X manual figure 9 (1)>)

#### 2.2.2 User Coordinate System

The user coordinate system is the robotic arm base coordinate system (Coordinate System 1 in the diagram).

![Official PiPER-X manual figure 10](<../../.gitbook/assets/Official PiPER-X manual figure 10 (1)>)

#### 2.2.3 Singular Positions

① J1 axis coincides with J5 axis

② J1 axis coincides with J6 axis

#### 2.2.4 Zero Point Setting

![Official PiPER-X manual figure 11](<../../.gitbook/assets/Official PiPER-X manual figure 11 (1)>)

Zero position as shown above: J1 aligned with base scale, J2 and J3 naturally lowered against limit, J4 raised against limit, J5 rotated clockwise against limit when facing the arm, J6 current position is zero. Click “Set All Zero Points.”

### 2.3 Robotic Arm Payload Curve

![Official PiPER-X manual figure 12](<../../.gitbook/assets/Official PiPER-X manual figure 12 (1)>)

End-effector payload curve diagram

### 2.4 Mechanical Installation

#### 2.4.1 Base Installation

The robotic arm base is mounted using screws. The base has four M5 threaded through-holes. Four M5 screws are included. Use the included hex tool for installation. Hole spacing is 70 mm. For mobile devices or fixed surfaces, design adapter structures with 70 mm hole spacing.

![Official PiPER-X manual figure 13](<../../.gitbook/assets/Official PiPER-X manual figure 13 (1)>)

#### 2.4.2 End-Effector Installation

![Official PiPER-X manual figure 14](<../../.gitbook/assets/Official PiPER-X manual figure 14 (1)>)

Other tools can be mounted on the robotic arm end via flange. Optional accessories include two-finger gripper and teach pendant. Installation method: Mount the two-finger gripper and teach pendant to the end via flange.

![Official PiPER-X manual figure 15](<../../.gitbook/assets/Official PiPER-X manual figure 15 (1)>)

* Fix the robotic arm to the mounting surface. Remove gripper, teach pendant, flange parts, flange, and mounting bolts.
* Install limit bolts (M3×4, head diameter 4.5) at the position shown (upper left of J6 motor when viewing).
* Align the flange limit slot with the installed limit bolt, then secure with six M3×8 hex socket cap screws.

![Official PiPER-X manual figure 16](<../../.gitbook/assets/Official PiPER-X manual figure 16 (1)>)

* After installing the flange, take out the gripper and teach pendant. The back covers have fool-proof design. Insert the gripper/teach pendant and secure with M3×14 hex socket cap screws.

![Official PiPER-X manual figure 17](<../../.gitbook/assets/Official PiPER-X manual figure 17 (1)>)

* After installing gripper/teach pendant, connect the power and communication cable from the accessory pack to J6 and the gripper/teach pendant.
* Connect the aviation cable to the robotic arm. Connect the USB-to-CAN module and aviation cable (yellow to CAN-H, blue to CAN-L). Connect the USB-to-CAN module to the computer via USB. Connect the aviation cable to the adapter and power on.
* After power-on, observe green slow flash on the base. Open the host software. After communication is established, rotate the gripper/teach pendant to the limit position as shown, then click “Set J6 Joint Zero.” After setting, enable the robotic arm and use the host to return J6 to zero. Verify J6 and gripper/teach pendant zero marks align.

![Official PiPER-X manual figure 18](<../../.gitbook/assets/Official PiPER-X manual figure 18 (1)>)

#### 2.4.3 Desktop Installation

The desktop installation module is optional. Standard products do not include this part. Contact us for separate purchase if needed. Dimensions as shown below. Ensure secure mounting before using the robotic arm.

![Official PiPER-X manual figure 19](<../../.gitbook/assets/Official PiPER-X manual figure 19 (1)>)

#### 2.4.5 Robotic Arm Mounting Orientation

Different mounting orientations require different settings. Configure mounting orientation in the host software motor configuration according to the installation position.

![Official PiPER-X manual figure 20](<../../.gitbook/assets/Official PiPER-X manual figure 20 (1)>)

***

## 3. CAN Connection and Preparation

Connect the CAN wires from the connector. Connect CAN\_H and CAN\_L to the CAN-to-USB adapter respectively. Connect the CAN-to-USB adapter to the laptop USB port. See connection diagram below.

![Official PiPER-X manual figure 21](<../../.gitbook/assets/Official PiPER-X manual figure 21 (1)>)

> **Note:** If using a non-standard charger, power input must not exceed 26V and current must not be less than 10A.

### 3.1 Teaching Mode Instructions

The robotic arm drag teaching state is indicated by the button indicator.

![Official PiPER-X manual figure 22](<../../.gitbook/assets/Official PiPER-X manual figure 22 (1)>)

#### 3.1.1 Robotic Arm Status Indicator

1. No light: Drag teaching stopped / Trajectory recording ended.
2. Green solid: Robotic arm in trajectory recording mode.
3. Green flashing: Robotic arm in trajectory playback mode.

#### 3.1.2 Switching Drag State

1. Single click: Switch between trajectory recording and recording ended.
2. Double click: Enter trajectory playback mode.

#### 3.1.3 Usage Instructions

First observe the indicator state:

1. If no light: Single click to enter trajectory recording. Green light should be solid. Drag the arm to record.
2. If no light and trajectory was previously recorded: Double click to enter playback. Green light flashes at 500 ms. The arm will replay the recorded trajectory once.
3. If light is solid: Recording in progress. Single click to end recording.
4. If light is flashing: Playback in progress.

> **Precautions:**
>
> 1. During playback, maintain a safe distance from the robotic arm.
> 2. Each time the arm enters recording mode, the previous trajectory is cleared. Playback uses the most recently recorded trajectory.
> 3. Maximum recording time is 3 minutes. Trajectories exceeding this are invalid.
> 4. After using drag teaching, ensure the indicator is off (teaching stopped).
> 5. For host motion control or command control, ensure the indicator is off, then switch operation mode to standby via host, then switch standby to CAN mode. Same for command control: send standby mode, then CAN control mode.

### 3.2 Dual-Arm Cascade and Teleoperation

For dual-arm cascade control and teleoperation, first use the host to set master and slave modes for each arm. The linkage control area is shown below. For dual-arm linkage, configure input/output states and offset values on this page. Connect both arms’ USB-to-CAN to the same computer.

![Official PiPER-X manual figure 23](<../../.gitbook/assets/Official PiPER-X manual figure 23 (1)>)

***

## 4. Host Software Instructions

### 4.1 ArmRobotUA Introduction

Software download: (Same as PIPER standard version)

[ArmRobotUA\_V1.5.0.251210\_beta (1).zip](https://agilexsupport.yuque.com/attachments/yuque/0/2026/zip/39017709/1772762047575-c5025ff3-d7a0-4112-a178-901dc6dba0f7.zip)

On PC with Windows 7 or later, double-click to open the host software. This HMI software allows operation of the robotic arm and reading of feedback data. User interface:

Host software desktop icon

![Official PiPER-X manual figure 24](<../../.gitbook/assets/Official PiPER-X manual figure 24 (1)>)

Host software panel function areas:

| No. | Name                                   |
| --- | -------------------------------------- |
| 1   | Robotic Arm Communication Button       |
| 2   | Vertical Menu Bar Options              |
| 3   | Speed Percentage Setting               |
| 4   | Robotic Arm Enable Button              |
| 5   | Robotic Arm Emergency Stop Button      |
| 6   | Window Minimize/Maximize/Close Buttons |
| 7   | Operation Function Area                |
| 8   | 3D Simulation Model                    |
| 9   | Trajectory Library                     |
| 10  | Robotic Arm Joint Status               |
| 11  | Robotic Arm Status Bar                 |

### 4.2 Robotic Arm Communication

Click setting to switch the language.

![Official PiPER-X manual figure 25](<../../.gitbook/assets/Official PiPER-X manual figure 25 (1)>)

Click the communication button in the upper left. A \[Connect Robotic Arm] window appears. It automatically detects CAN devices connected to the PC. Users can manually connect or disconnect selected CAN devices. On successful connection, the button displays the current status based on connected CAN devices.

![Official PiPER-X manual figure 26](<../../.gitbook/assets/Official PiPER-X manual figure 26 (1)>)

Robotic arm communication button

![Official PiPER-X manual figure 27](<../../.gitbook/assets/Official PiPER-X manual figure 27 (1)>) ![Official PiPER-X manual figure 28](<../../.gitbook/assets/Official PiPER-X manual figure 28 (1)>)

Robotic arm status display (left: online, right: offline)

### 4.3 Vertical Menu Bar

Click option names on the left to switch panels. Selected items have a light blue background.

![Official PiPER-X manual figure 29](<../../.gitbook/assets/Official PiPER-X manual figure 29 (1)>)

Vertical menu

### 4.4 Speed Percentage Setting

After connecting the CAN device, use the speed percentage setting to set motion speed as a percentage of maximum.

![Official PiPER-X manual figure 30](<../../.gitbook/assets/Official PiPER-X manual figure 30 (1)>)

Speed Percent Setting

### 4.5 Robotic Arm Enable Button

After successfully connecting to the CAN device, the user can press the robotic arm enable button at the top of the window. The display shows the current status of the six joints. Clicking it will reverse the positions of the six joints at the same time.

![Official PiPER-X manual figure 31](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGYAAAAzCAYAAABlnH0mAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAQWSURBVHhe7ZxLThtBFEW9BhBeAlP2wCpgwAaYsgTWEiVKlIkHBokMEDYSCImJAQEC8f+Yr3dQ0e1wW4/y67LdscuF/K50JFz1qrvr3a6Pge5Kp9Nx5P393b29vbnX19eMl5cXIzL0IjeGpqDy+fnZPT09ZbTbbSMin4yBKRgh7dtb11hedr+qVfetUjHGQG4MTcHogClasBGP3BhMXzDl/v7e/ZyZUYONeHAGq2BNeXx8dBcXF2qgEReu9RUs9Hd3d+709FQNNOKSG4Np7Obmxh0fH6uBRly45mfGXF9fu6OjIzXQiEtuDPbOMObw8FANNOJixiTKJ2Ourq7MmEQwYxLFjEkUMyZRJt6Y39Wq219ZcX/m59X6EGirlQ+DiTZG6rZWU2N8mgsLHy36b1OGoRtTn5v7uOywarOzantAlbmLywD1m2T0D7GDtCnDSEcMJcsw/NkxSNYRqrW6qtYPG2jQJJdpMwjRjSGY1yGtcxhNqPfLR0XRdYQo02YQxmYMoELTWgygFI3Bn2LGYoxcSFnGXRKkdZx1Uv7owtrkK7SDgnAueT1Qr3VQuz7t3FiX/LhedBlzcHCgBpaB0uoAOk6xTMrvOCWTzGTyMxPDZCCWYowPhfMhXrYpMhTyr483jdy0YJ2EBp0VxmoMoLRyzRjtLoXkz5CsRxu/TELJMppTtAGB5LXwJtPWRsovD/HljIGK7mKAkYJRJMv6MabIcMgvZ51sQ8kY0uv8Gl/KGHYQwp0cMgigXq5JWgyANGNCCYVkG0rG9FNXRHJrDIG0ZPkLtBYjjyu/EPpxBNKOE2oHyTb9SLbvxViN4d2szeOQliyChEv55Vz8QSxjQtc7KF3GjON7jDYlQX5HtV/RUEWfQSjBANKSSvnlrPONgWTM/zA2Y7iN1HYxAPKTBfkm+kmHtHaQLJNQsgzngfq9Pl6HdvOAovIiohsj5/+iTgNIS7DccTF5Mo5CHL/TUDh30eiEOKWG1j4CFd0AKMcxUMapNdRXjaEb48/9mkI7Kk2s4yiT8jvsnx+faSDFWCkcxz9+yEQpuZ5p1zjoaAEjHTFGeWDMxP6hLGXMmEQxYxLFjEkUMyZRzJhEMWMS5ZMx9t/+6WDGJEpuDB/1wxNlP6an1WAjHl3G4BnM+tKSGmzEIzdGPrW8v7vraouL7vvUlNrIGD0wJntqGb/JxHP+l5eX2XS2s7PjNjc33cbGhltfX89YW1vLqNfrxghgfkH+Aga+GQOj5vz83LVaLbe3t5cZtL297ZrNpms0GqXY2tqaSLRc9ANynRvDOQ3m4LUl+E5zdnaWTW0nJyfZ2mPEI3+XDB2COVhvsH3G1Pbw8JAZBTCajNGDXH8yhuZgWsOaA4PkO8uMeHQZQ3NokASjyYjDPy867i8OcTaNk0GIzgAAAABJRU5ErkJggg==) ![Official PiPER-X manual figure 32](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAG0AAAAzCAYAAACdfIbRAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAQFSURBVHhe7ZzLTttAFIZ5BiryCGx5B54CFrwAWx6BRTet2i676KYL1hWVAAlVQkAkEOqKi4CCuEO45w2m+i1+6XA4tscEO7Y4v/QtMp45SebL2ONIyUC32w15PD4+On1E+8iVhkEPDw/h/v4+4e7uzqkY7SRTGoVh4O3tbbi5uUm4vr52KkR7SZUGYVhZ553zMPl7MrS+tsLAxwGnD2gvpjQKw6qCMKuQUx3aywtpPCVC2OXlZRj6MmQWcqpDe3kmjQdwDet0OuHo6Mgs4lSL9mJKw6bj4uIi7O/vm0WcatFeXkjjtezs7Czs7u6aRZxq0V5SpZ2enoadnR2ziFMt2ospDfcGOLi9vW0WcapFe3FpDSBa2snJiUurCdqLS2sALq2BuLQG4tIUrW+tMPVnKozOjJrHs8BYq/2tcWkCmdl/s2YfzdivsacR8WN6pS/SRn6MPL3NuFg1ygSJFYD3gr5FxvRK31caYx3jp9g6ViZIUQGvGfNaai1t+Ptw6rEyQRotDV//90sayDpWFkjdpUkvtZGGa4Vuw+5suj2d9MfuDo8xUTLWDg59dbJ2egjqyk0GgpVv9QeIJc16buu9FaGQtK2tLbNILzBWu9XGYFuOYKIwMZSJyDGcNE4UZDGyn4RBbfSXY9JkI1oaXyNeA9v4OrM+AHk0Shph9AQyeW2YXN0mYWQbxWHSZTtBpDRejyFO9gOMbo+lNtKsWP0Boj/VwJKBFYbTnGyLkWbVZ3Q7j8kxjOxD8p4/j8auNGtS8yYDq4WnLMTqA5Ci9RE5hpF9Yo7F8C6k8VSFyJth3Y8gReoDRI6JiRxfhNpKywKJnVRIQuSOLWvyARJbnyByjH78lhSSVpf7NCR2UhnZljX5ALHqM7qdx+QYRvZ5K2otjatEtyNFpOm+jGyTMLKNu0drNwgQ+Tx8LXK7L0lrj6HW0tK+e0SKSENQi/dsDK511n0Xw+29vCbqvgRJ+3Cgnfdl/CCmyY+hL9L4wmPDcVay6lnH8JirhrHqY1LlDTuSJVgGz8HjugbSyyoDudLK/sLYKY724tIagEtrIC6tgbi0BuLSGohLayAurYFES/NfzdQH7cWlNYAoafyZKH4J+uHzB7OQUx3aS6Y0/OZ6YmbCLORUR640/e8G63/Xw/jP8TD4adAs6JSP9vJMGsXhG2X8X8Xx8XFyilxbWwtLS0thcXExLCwsJMzPzyfMzc05JcD5BdqLKQ1WsRRh9fDwMGxuboaNjY1EXrvdDqurq2FlZeVVLC8vv0usuYgBc629vJDGDjyH4q+WcG9wcHCQnC739vaSa51THdqLKQ2wA86j2GpiWV5dXSUSAVahUz6Ya+0lVRrgksS5FPIAVp9TLc+9dMN/1qqAuqQlDwIAAAAASUVORK5CYII=)

Robotic arm Enable button

### 4.6 Robotic Arm Emergency Stop Button

After successfully connecting to the CAN device, the user can press the robot arm emergency stop button above the window. After pressing the emergency stop button, the robot arm will immediately stop any movement. Press the button again to resume use. It can be resumed after enabling.

![Official PiPER-X manual figure 33](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGkAAAAzCAYAAACUlyarAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAPdSURBVHhe7ZxLTuNQEEVZAwiWwJQ9sAoYsAGmLIG1tLrVrZ5kEJDoASJBAiExCSBAIP6f8M0OXutafVGlXM92LMWx1XWlw6DqvXx87GeTKJ4aDAZB8/n56UwQ7SMlCYM+Pj7C+/t7wtvbm1Mx2smQJArCwNfX1/Dy8pLQ7/edCpFOwJckCMKR07+/D53V1fBrbi58m5pyJoAUBBJJFISjBoKsiU51pCRxiYOgx8fH8HN21pzoVEdKEs9Bz8/P4erqypzkVIspCRcJDw8P4fz83JzkVEtKEs9Fd3d34fT01JzkVEtU0u3tbTg5OTEnOdViSsK1OSQdHx+bk5xqcUkNICrp5ubGJdUEl9QAXFIDcEkNwCU1AJfUAMYqqb2wEEaJ9RgWrfn5fzOG01tfHxo3an6rr2Niz4P3JceBIu8Vr08/RxHGKknCWL3u0lK0p+HG0EL4GH8WF79qCOpyHCNrlCHnHq6tJTX9PKzft1pDdQkja1L4qKJqIYlvwOppmFhPS8Jj6zGIrLHOuRShBRPuEFogYXRditK9LFKS8DVF1ZJAVk+CxPZiRC5FiOyzhlh1zMVezugxEkbvBLKn63m9GBOXZK3vWTBWrwiM1QM4OhAcTVafZC17jK7n9WJkSjo6OjInlYGx6rqWhUyZkzBj9QCTt/NkLV2Mruf1YjROklyOGGvJicFYPcBYPQ1TtJ53LotRuSQr1vgsIArLjE4RWYzVA4zV0zB5dbxeLqOIHFuEyiVZdV0rCt48zw1M3jLFWD3AWD0NE6vLYKca5YiX1FKSFT1GU3RPZaweYMZ1TirDxCVZYANorHEaxuoRxuoBLqNFr+6s8wuj62XJlFTX/5Ni0riBrR5hrB7AYzNWnzDWFSaj62WphSQsLbGeBpGfKugeYvUIY/UIl868TxxiRxtj9cpQC0l801ZPw8iavNrLWxoZqyehKL2ccZnLWg4Zq1eGsUriEVI01mNocBTFYi09IOt1ZF0gyKVPxtoRsp5Djx2VlCT/Pql+uKQG4JIagEtqAC6pAbikBuCSGoBLagBRSf6rivrgkhqAKYk/x8Qv/X7MzJgTnerIlITfzLZXVsyJTnWkJOlfnx/u74fW8nL4Pj1tPoAzflKScLMNfBKO+zhcX18nS97e3l7Y3t4OW1tbYXNzM2FjYyOh3W47Y4DbF5iSeEcUHE2Xl5eh1+uFg4ODRNbu7m7odruh0+mUYmdn57/E2hZFwLZOScIfeW8h3LoG/zNdXFwky9/Z2VlyrnKqw5QEKArnJ1ySY/l7enpKpAEcZc74wbaWgkDm/e7kPe+c6pBOBoNB+As+VVeDb3tHdgAAAABJRU5ErkJggg==) ![Official PiPER-X manual figure 34](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGgAAAAzCAYAAAB7VU2VAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAOmSURBVHhe7ZzLTttAFIbzDCDyCGx5B54CFrwAWx6BRTet2i676KYL1hWVAAkhISBSEOqKi4CCuEMSbnmDqf4Rf3M0OpM4KB6P1PNLH5LneMx4PtuxF3at2+068vr6alSIdEH+CcIKLy8v7vn52fP09GQkRoohXhDlYKXHx0fX6XQ87XbbSEgoB9QgB2fMbevWzf+ad/UvdVf7UDMqQBUEOThbIEfrZKRDFQQ59/f3buLzhNrJSIcqqNVquYuLC7WDkRZV0N3dnTs9PVU7GGlRBd3c3Ljj42O1g5EWVdD19bU7OjpSOxhpiQo6PDxUOxhpMUGZowq6uroyQZlggjLHBGWOCcocE5Q5JihzShE09X3KFcnkt0m1v9GjFEESRrbVv9bfWp2XKWtlsPxn2aPVcqcSQUBKCmujBjFBEZhha6MEMUERmGFr00vTb9VetMvhwsbCW7UXtKEGKVpYJ9r/QptcB+Cs5/9bbCz6NhnUuW7R8Q8iKujg4EDtMCxM2M4bCe3I5iTIScKEIPLGgpETM/NzxrdxmevFziBKlJPHsVECkWE/jgvhOIqOvwiVCOIOILIdYAeQ8CgHjFzWJh4Jl7X1eJRDalijaO1MYrTaMOMvQjJBYbSdk+trNR61XGbkGaSBxEQiYTthirYPqoXjL0IyQVqbNrFM2K7VuMMILiExUcioBWnbYw0ZthajEkG8DPSbtH6R6/NSxMS2mVpQv2j9YlQiaFB7bOf7wR92RtaQlILeM/4YUUFl32Yz4V0NI9ti9PsBD9tSCkK02nuoTBAvTeHdDnYcid1EyHYk/N1hf9mGaBOKbSHa/+pXQ2KChhl/ESoThIllwhqDneUZxkuYFIrIW2RuM5w8hsvymYfRnoMQtkmQmCDADBp/EUoRJHcwjFyPRxsSPhTKB0AmPPq0dbQJQJtMuB0sh9GOdC1SrKTI+ItQiiBjdJigzDFBmWOCMscEZY4JyhwTlDkmKHNUQfZ2Qz6YoMxRBeEVSLxhN/5pXO1kpCMqCO+ozi3NqZ2MdKiC+Jb37u9dN/tj1o19HFM7G+WjCsJ3Ei4vL/1lrtlsus3NTbe+vu7W1tY8q6urnpWVFaMEOL9AFYQvjeAsOj8/d/v7+25vb8+LajQabmdnx21vb7+Lra2t/xJtLoqAuVYF8Vs9+BwMnonOzs78Je/k5MT/NhnpUAXxa1f4DBk+iYVL3sPDgxcGcHYZ5YO5VgXhT/i9OPnNOCMdoZxut+v+Apmx3YQlJ1XaAAAAAElFTkSuQmCC)

Robotic Arm e-stop button

### 4.7 Window Minimize/Maximize/Close Buttons

The three buttons on the upper right are window minimize, window maximize, and window close. Pressing them can realize the corresponding functions of the window.

![Official PiPER-X manual figure 35](<../../.gitbook/assets/Official PiPER-X manual figure 35 (1)>)

Window zoom and close button

### 4.8 Operation Function Area

The central area of the window is the operation function area, which can be switched synchronously by \[2. Vertical menu bar options] to switch to different partitions according to user needs. For example, the figure below is the motion control area, which can realize the actual joint control of the robot arm.

![Official PiPER-X manual figure 36](<../../.gitbook/assets/Official PiPER-X manual figure 36 (1)>)

Motion control area

#### Motion Control Modes

| Motion Mode   | Usage                                                                                                                                                                     | Notes                                                                                                |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Point Motion  | Enter end-effector position (x,y,z,rx,ry,rz), click Apply. The arm moves to the specified point. Can also use x/y/z icons to adjust coordinates. **Click Apply to move.** | Unreachable points will not move the arm; error prompt will appear.                                  |
| Arc Motion    | Enter three points: start, middle, end. The arm plans and executes arc motion.                                                                                            | Unreachable points in the arc may prevent motion.                                                    |
| Joint Motion  | Enter joint angles, click Apply. Can also use sliders. **Click Apply to execute.**                                                                                        | Joint angles exceeding limits will not move.                                                         |
| Linear Motion | Enter position (x,y,z,rx,ry,rz). The arm moves linearly to the point.                                                                                                     | Unreachable points in the path may cause no solution.                                                |
| MIT Control   | Select target joint, enter angle, velocity, kp, kd, torque.                                                                                                               | Directly controls joint position, velocity, torque. Dangerous; contact technical support before use. |

### 4.9 Motion Control Area

The robotic arm has a total of 6 joints, named Joint 1 to Joint 6 from bottom to top, corresponding to the 6 joint settings in the operation bar. Users can edit the joint degrees by themselves or click the plus and minus buttons to realize the joint operation of the robotic arm (unit: °).

![Official PiPER-X manual figure 37](<../../.gitbook/assets/Official PiPER-X manual figure 37 (1)>)

Joint degree

The 3 buttons below are ①Return to zero button, ②Load button, and ③Send button. Button ①: automatically sends the factory initial position angle value of the robot arm, button ②: fills the current degree of the 6 joints of the robot arm into the user edit bar, and button ③: sends the 6 joint degrees in the user edit bar to the robot arm. The specific content is subject to actual experience.

![Official PiPER-X manual figure 38](<../../.gitbook/assets/Official PiPER-X manual figure 38 (1)>)

Joint button

<br>

<br>

<br>

The picture below shows the lighting control area. If the joint light board is installed, the lighting control of the six joints of the robot arm can be realized.

![Official PiPER-X manual figure 39](<../../.gitbook/assets/Official PiPER-X manual figure 39 (1)>)

Light control area

The joint number and RGB channel above are the light board that the user needs to operate and the grayscale value of the corresponding channel. The effect bar below is the actual calculated light color. Click the \[Confirm] button to operate the light board.

### 4.10 Linkage Control Area

Note:

When using the robotic arm independently (i.e., not in master-slave teleoperation mode), you must first set it to slave mode!

<br>

If the arm is set to master mode, it cannot be controlled. You will need to use the host computer to switch it back to slave mode before operation.

The following figure shows the linkage control area. If the user needs to achieve dual-arm linkage, the Master and servant status and offset value can be configured on this page.

![Official PiPER-X manual figure 40](<../../.gitbook/assets/Official PiPER-X manual figure 40 (1)>)

Linkage control area

### 4.11 Gripper Control Area (Gripper Required)

The following figure shows the gripper control area, where you can set the gripper enable status, torque value, etc. The right area of the host computer will feedback the corresponding gripper value.

![Official PiPER-X manual figure 41](<../../.gitbook/assets/Official PiPER-X manual figure 41 (1)>)

Gripper/claw setting area

### 4.12 Joint Settings Area

The figure below shows the joint setting area, where you can edit the maximum and minimum angles, maximum speed, and maximum acceleration of the six joints of the robot arm. The operation process is \[Edit] - \[Save].

![Official PiPER-X manual figure 42](<../../.gitbook/assets/Official PiPER-X manual figure 42 (1)>)

Joint setting area

### 4.13 Speed Settings Area

The following figure shows the speed setting area, where the maximum linear speed and angular speed and the maximum linear acceleration and angular acceleration of the end of the robot arm can be set. The \[Initialization button] is used to restore the factory settings.

![Official PiPER-X manual figure 43](<../../.gitbook/assets/Official PiPER-X manual figure 43 (1)>)

End speed setting area

![Official PiPER-X manual figure 44](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJ8AAABSCAIAAADFD5HdAAAACXBIWXMAABJ0AAASdAHeZh94AAAFVUlEQVR4nO2cXUhbZxiA36QVpbNq1bCuMUnFq0YwSwbC3I+1xOrKmloQjLU6iKzQgbYdkc3VbgPtLqrsxx86Igbmf8HW9qZTEufKZi5WWnexHm9E8KfiZuJ0qEVYk118cJpGPTkTNZ8v70MuTs77vcnLeXK+v5AoAoEAEEhRRroAYgchu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5jZLxFz3rq3a3UQW8ZWdGazkJRdADjxpkmpUGx3PcS24fY8koiG6ZlJ7Z6Gxl3MkF3MkF3MkF3MkF3MkF3MhFnvRhC/3z8zM+P1ehUKhUqVrFanKGh59j/h0e7q6urd/jvDw8M+n088maxSncw9+f7p0zExMWtraw8e/JydfTw6OjqCdfIPd3YFQai/cWNpaVGj0eTknHj18GEA+HNu7uHD37q7u1wuV3V19V/z89/fvJmQcCgzMzPS9XINX3Z9Pt+XX3weCATKyj6wnDmjVL6YFliLiwcHBjo62q9e/ayoyAoAz5//G7lK9wZ82Y2LiysoOJuVlXU0NTUkpFQq3zt1KsOQUWW39/ffiUh50pTbbADQ5nRGupAX8DVnjoqKOldSsl6tiFqdUlpatrS0tJtVycTtdkW6hFD4siuHvPz8ZJUKAOh/1MKy9+wqlcq0tDQAWFhYWB/1+bytDodOq2loqAcAnVbDHj6flzXweEbEkzqtZkwQgtNZrvhodTiCo5vllttsOq0GANxu14aJkYIXu4IglJWeF16+1ptxKCEBAP7ZqH82GY11dbUAMCaM6bSaisrK4Girw1Fstfb09k5OTU9OTVdUVubn501MTLCoTqupq6t9PDrKok3NLeylwua2OZ2TU9MAYDbnsuiHFy5s8UJsK7zY/X308fLy8sivv8hp/PY778bGxr5uNK0PsYsLAG63q6e3126vYmeSkpInJibq6mpraq5lZb3FGtvtVQCQczxbTDebc5OSktmxxWIRz8vJ5RBe7MbFxwPA34uLchrr9fr2jk69Xi/dTDTBYCZC7iqzOTf4qdvtEvtwAGAfFJm5HMKL3cTERAAYHx/3+/3b8oIyL33wRJelmIzGhob6YMdycvmEF7tsD9k7Pz84MLCjbxQ8LWJTIZE2p7OpuQUAmhobTUYjW7/KzOUTvnYz4uPjOzraMwwZanXKhg3m5uZmZ2dNpg1GXDmYzbnSuw0Wi8VisYwJQn5+HpsAi51z2FwO4eXeZRQUnFUoFFV2+4/374d00X6//25//6XKim+/+XrLvbd0X+rxjLCDY3q9KFVmLp/wYnffvv0A8NqRI9evf3XwYFxrq+PjK5e7Ojt/GhoaGhrq7uq8cvlSe/sPBw688smn1cH7z/Jhw6qoUEQ8U2y1Bg+3wSN32Fw+4cWuwWC4ePEjg8FwNDX1u8bGcyXnV589u327r7m5qaW5qa+vb2VlpbCwsLmlJT09fWtvwfrVYqu13GZj69QxQdBpNU/+eCK2GRnxsAOfz+t2u0TBcnIh6P4ek7dw32kUEvt5zlv3zFlv7GY1wQQCgadPZ+bnvYFAQKVSqdVqObdsyGRnYGDw2MsLp4aG+qbGRvFpT2+vuHAKCdXUXAtZAknkAkCrwyHufoSEdg6355HEbxH4tUvIQdouLz0zsROQXcyQXcyQXcyQXcyQXcyQXcyE+RZB+qfdBOdI7WYQex3qmTFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjHzH7YvAbKOTUVhAAAAAElFTkSuQmCC)

Reset area

### 4.14 Collision Level

The picture shows the collision level setting. The collision level of level 1 to level 8 can be configured for the 6 joints of the robot arm. The operation process is \[Edit] - \[Save].

![Official PiPER-X manual figure 45](<../../.gitbook/assets/Official PiPER-X manual figure 45 (1)>)

Collision Level Setting Area

### 4.15 Joint Information

View joint motion and status information.

![Official PiPER-X manual figure 46](<../../.gitbook/assets/Official PiPER-X manual figure 46 (1)>)

![Official PiPER-X manual figure 47](<../../.gitbook/assets/Official PiPER-X manual figure 47 (1)>)

### 4.16 Motor Settings

The figure below shows the motor settings, which can be used to set the status (enable, disable), zero position setting, and clear errors of the six joint motors of the robot arm.

![Official PiPER-X manual figure 48](<../../.gitbook/assets/Official PiPER-X manual figure 48 (1)>)

Motor setting

### 4.17 Firmware Upgrade

The following figure is the page related to the robot version upgrade. The upgrade steps are as follows:

① Check whether there are words such as node information generated in the information display area (area 1). If there are words, it means that the robot has entered the upgrade state normally. If the check is correct, it can be upgraded normally;

② Click the \[Load Package] button (area 5), select the version firmware configured by R\&D (suffixed with bin), and after confirmation, the information area (area 4) will display the firmware package information selected by the user;

③ Click the \[Start Upgrade] button (area 6) and wait for the progress bar (area 2) to complete. The normal time is about 2\~3 minutes.

![Official PiPER-X manual figure 49](<../../.gitbook/assets/Official PiPER-X manual figure 49 (1)>)

![Official PiPER-X manual figure 50](<../../.gitbook/assets/Official PiPER-X manual figure 50 (1)>)

![Official PiPER-X manual figure 51](<../../.gitbook/assets/Official PiPER-X manual figure 51 (1)>)

Upgrade area

### 4.18 3D Simulation Model

On the right side of the window is the real-time 3D simulation model of the robot arm. The upper left corner shows the real-time feedback coordinate values and 6 joint degrees of the current robot arm. The three buttons below are ① Help, ② View Restore, and ③ Settings. Button ①: Pop-up window displays the usage of the 3D area, button ②: Restore the original 3D display view, and button ③: Set various parameters of the host computer. The specific content is subject to actual experience.

![Official PiPER-X manual figure 52](<../../.gitbook/assets/Official PiPER-X manual figure 52 (1)>)

3D simulation model

### 4.19 Trajectory Library

Click the \[TraceLib] below the vertical menu bar, and a pop-up window will appear. Users can customize and edit a complete robot arm motion trajectory and run it.

![Official PiPER-X manual figure 53](<../../.gitbook/assets/Official PiPER-X manual figure 53 (1)>)

![Official PiPER-X manual figure 54](<../../.gitbook/assets/Official PiPER-X manual figure 54 (1)>)

Trajectory Library Pop-up

① Import: Import the local trajectory library log file.

② Create: Create a new motion trajectory.

③ Delete: Delete the selected trajectory.

④ Send: Send the selected trajectory to make the robot arm run the trajectory once, multiple times, or in a cycle.

⑤ Export file: Export the selected trajectory to the local.

At the same time, the user can double-click any trajectory to enter the secondary menu, edit the specific content of the trajectory (as shown below), and right-click to add, delete, modify, and check.

![Official PiPER-X manual figure 55](<../../.gitbook/assets/Official PiPER-X manual figure 55 (1)>)

TraceLib secondary menu

### 4.20 Joint Status Button

Click the robot arm joint status button at the bottom left of the window, and a \[Joint Status] window will pop up (as shown below), which will monitor the status information of the 6 joints in real time. The button will monitor and display the current status in real time according to the status of the connected joints (as shown below).

![Official PiPER-X manual figure 56](<../../.gitbook/assets/Official PiPER-X manual figure 56 (1)>)

Joint status window

![Official PiPER-X manual figure 57](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAALYAAABNCAYAAAALpZ7eAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAViSURBVHhe7Z29bhs5FEYNWOqsx/CbpLBUqJK6tFKXN8gDpJUDbJdSSrVAmgWCNCpWgIEUBoINjAUW+vFDuOb6jHENLnMpKWtn5KG+4sA2L38k85Bzh1PMyd3dXRCiNCS2KBKJLYpEYosikdiiSCS2KJKfFnu5XIbJZBIuLi7C+fl5ODs7CycnJ0I8GVzCKdzCMVzzHNyHvcVerVZhNBqF09NT90MJ8dy0Wq3KufV67Tq5jb3Ens1modPpVIO12+3Q7/fD5eVlmM/n4ebmJtze3grxZHAJp3ALx3AN53BvOp26bubYKXav13tcQd1uNywWC/dDCfHc4BrOmX+46DnqsVVsVol1OhwOw2azcT+AEL8KnMM985DswXM1JSs2ObWlH3TsDSpEXQwGg8pFnNwn586KTdJOR2z/2qnFocFBS0vG47HrbIwrNscsnH6QvCunFi8FXOSkBMgoPHcNV2zOEFkZ3Jl6AwhxKHASNzk58dw1XLE5ILfGXudCHAqcxE0c9dw1XLF5+kNjzhS9zoU4FDiJmzjquWu4Yttjcj18ES8NnMRNHPXcNVyxaQhex0IcGvPTc9eQ2KJxSGxRJBJbFInEFkUisUWRSGxRJBJbFInEFkUisUWRSGxRJBJbFInEFi7X/1y75U1BYotH3l+9Dye/3c/rPa9+f+XWaQpHLbZNopHGP//1+Yc6Xr1S4PsiNN9RYjudNg0T9uP1RzcOJQudIrELExtyuaXEbhYS+x4m8s2XN49y5+p45SUisQsS234CuWaujgcpjLU1vLSGq8Hb+dsqzkKiLG5D/Pvye9X29R+vw/xmHq7+vvpPG+K0I2blwO8WS/E+37ZTD+IS2+m0aTCR/EQWm/hcnRQEIBYvBrvpNHkN6xusXXylQDZOJqzsw9cP1e/0Z32++/PdY51P3z5Vn5l6FovHA5PaPh9j8DekdQ1iEtvptGnEk2xHXunEeiKYNLRJY9aPt3NTnosZxNm1410YcXPt2LE9GW2suMwWVVwWQ0xiO502jXSSTYZ4F/ZEsHppuZGL72oHxNmJ4zLbmeOyXTG+Q7rwJPYDRye2d7n2REjrpOTilO0ShzrPIXYM3yvOy706QExiO502DW+S05TEq0OZV27k4pTVKXZ878AOzti5ukBMYjudNo3cJJsMJkYunpYbuThldYltN51xWiWxHzhaseOUxKuTKze2tatLbMrScon9wNGKDZaSeHXsVMQ7pdgWo7xOsdOxKMv1A16bpiGx79k2ybBNBIvFl3q7/G9rU6fYwAK1xWaQYnFV8tpIbKfTphBPshELalhKkpYbqTCQ26lT0vEQkPNri9tRXXzlQDor58lk/JCHtjy4sf7iRQb8nUux4jLD+380gaMWW5SLxBZFIrFFkUhsUSQSWxSJxBZFIrFFkUhsUSQSWxSJxBZFIrFFkfxvsfUCU/FSedILTPXKafFSedIrp3kBO415IbvXuRCHAidxE0c9dw1X7MlkUjXu9/tu50IcCpy0Tddz13DFXi6XodVqhXa7HRaLhTuAEHWDi3gJq9XqB29jXLFhNBpVK6Pb7YbNZuMOJERd4CAu4uR4PHadjcmKvV6vQ6fTqToaDofuYELUxWAwqFzESdz0nI3Jig3T6bTqDOhYO7eoG5wzqWE2m7mupmwVG3q93mOnXAqUc4u6wDVLPwAXPUc9dooNrBJLS7ih5M6Uu1LOFPUQRzwXuIRTuIVj3CTiHO6RPXhu5thLbOAulKTdBhPiV4NrOLdPTp2yt9gGgrOiOCDn6Y89fhfiqeASTuEWju060tvGT4stRBOQ2KJIJLYoEoktikRiiyKR2KJIJLYokLvwL8adm5wzUQCRAAAAAElFTkSuQmCC) ![Official PiPER-X manual figure 58](<../../.gitbook/assets/Official PiPER-X manual figure 58 (1)>)

Joint status

### 4.21 Robotic Arm Status Bar

The robot arm status bar at the bottom right of the window will monitor the robot arm status information in real time (as shown below).

![Official PiPER-X manual figure 59](<../../.gitbook/assets/Official PiPER-X manual figure 59 (1)>)

Robotic arm status

***

## 5. Secondary Development

The robotic arm supports Python SDK and ROS1/ROS2 driver packages. Links below. For detailed development, refer to GitHub.

| Content   | URL                                                                                                                                                                                                                     |
| --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SDK       | [https://github.com/agilexrobotics/pyAgxArm](https://github.com/agilexrobotics/pyAgxArm)                                                                                                                                |
| URDF      | [https://github.com/agilexrobotics/piper\_ros/tree/humble\_beta1/src/robot\_description/piper\_x\_description](https://github.com/agilexrobotics/piper_ros/tree/humble_beta1/src/robot_description/piper_x_description) |
| Isaac Sim | [https://github.com/agilexrobotics/piper\_ros/tree/humble\_beta1/src/robot\_description/USD](https://github.com/agilexrobotics/piper_ros/tree/humble_beta1/src/robot_description/USD)                                   |

***

## 6. Robotic Arm CAN Protocol

The robotic arm provides a CAN interface for user development. Users can control the arm via commands. CAN communication uses CAN 2.0B standard, 1000 kbps baud rate, MOTOROLA (MSB) format. For CAN protocol development, contact AgileX technical support for the CAN protocol manual.

CAN Protocol Manual: [Robotic Arm External Communication Protocol 2025010](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/qii9wce225nvworv?singleDoc#7305)

***

## 7. Maintenance and Care

To maintain long-term performance, regular maintenance is required. Follow all instructions in this manual strictly. The purpose is to ensure normal operation of the robotic arm and accessories.

### 7.1 Storage

After use, return to zero point and power off before storage. Organize cables to avoid tangling or excessive pulling. Operating and storage environment: Temperature -20 to 50°C, Humidity 25%-85%, non-condensing.

### 7.2 Maintenance

Perform maintenance with the arm at zero point and powered off. After power off:

**Note:**

* **Cleaning: Use wet wipes or damp cloth to remove dust, dirt, and oil.**
* **Screw check: Check for loose screws.**
* **Motor check: Check motors and structure for damage or deformation.**
* **Cable check: Check power and CAN cables for secure connection and damaged insulation.**

### 7.3 Emergency Handling

#### 7.3.1 Power Off

In emergencies, disconnect the aviation connector to cut power. Note: After power off, the arm will lose power and may fall. Avoid damage to the arm, surroundings, or personnel. Disconnecting is an emergency measure, not for injury prevention.

#### 7.3.2 Emergency Stop

When the host is connected, use the host pause button to stop and resume arm motion.

***

## 8. Dimension Drawings

3D STEP model: [PiPER-X Model Files](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/nv0dsc0nnfgy8272?singleDoc)

### 8.1 Robotic Arm Dimensions

![Official PiPER-X manual figure 60](<../../.gitbook/assets/Official PiPER-X manual figure 60 (1)>)

![Official PiPER-X manual figure 61](<../../.gitbook/assets/Official PiPER-X manual figure 61 (1)>)

![Official PiPER-X manual figure 62](<../../.gitbook/assets/Official PiPER-X manual figure 62 (1)>)

![Official PiPER-X manual figure 63](<../../.gitbook/assets/Official PiPER-X manual figure 63 (1)>)

### 8.2 Base

![Official PiPER-X manual figure 64](<../../.gitbook/assets/Official PiPER-X manual figure 64 (1)>)

### 8.3 End Mounting Surface

![Official PiPER-X manual figure 65](<../../.gitbook/assets/Official PiPER-X manual figure 65 (1)>)

### 8.4 Flange Dimensions

![Official PiPER-X manual figure 66](<../../.gitbook/assets/Official PiPER-X manual figure 66 (1)>)

### 8.5 Gripper Dimensions

![Official PiPER-X manual figure 67](<../../.gitbook/assets/Official PiPER-X manual figure 67 (1)>)

### 8.6 Teach Pendant Dimensions

![Official PiPER-X manual figure 68](<../../.gitbook/assets/Official PiPER-X manual figure 68 (1)>)

### 8.7 G-Type Woodworking Clamp Dimensions

![Official PiPER-X manual figure 69](<../../.gitbook/assets/Official PiPER-X manual figure 69 (1)>)



### Development Resources

* [pyAgxArm Python SDK](https://github.com/agilexrobotics/pyAgxArm) — current official SDK for PiPER, PiPER-H, PiPER-L, and PiPER-X.
* [PiPER SDK repository](https://github.com/agilexrobotics/piper_sdk) — legacy and V2 Python interfaces, CAN setup, examples, and release history.
* [AgileX arm ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/ros2) — select the exact model with `arm_type:=piper`, `piper_h`, `piper_l`, or `piper_x`.
* [PiPER-series URDF, Xacro, and mesh resources](https://github.com/agilexrobotics/agx_arm_urdf) — separate official model directories are provided for PiPER, PiPER-H, PiPER-L, and PiPER-X.
* [PiPER-series firmware compatibility reference](https://github.com/agilexrobotics/pyAgxArm/blob/master/docs/piper/firmware_reference.md) — read the arm firmware first and choose the matching SDK driver; PiPER-X has additional version-specific joint-sign behavior. This page is a compatibility reference, not a firmware binary download.
