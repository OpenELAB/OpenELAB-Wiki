# PiPER-L User Manual

### &#x20;AgileX PiPER-L 6-DOF Robotic Arm for Education and Robotics

{% embed url="https://openelab.io/products/agilex-piper-l-robotic-arm" %}

<img src="../../.gitbook/assets/PiPER-L official image 1 image.png" alt="PiPER-L official image 1: image.png" width="657">

Revision History:

| No. | Version | Date      | Modified By | Reviewed By  | Remarks            |
| --- | ------- | --------- | ----------- | ------------ | ------------------ |
| 1   | V.1.0.0 | 2026/1/5  | Dennis      | <p>​<br></p> | Document created   |
| 2   | V.1.1.0 | 2026/1/25 | Dennis      | <p>​<br></p> | Document finalized |

## **Important Safety Information** <a href="#odniv" id="odniv"></a>

This chapter contains important safety information that every individual or organization must read and understand before using the device, especially before powering it on for the first time. It is essential to follow all assembly instructions and guidelines in this manual. Pay particular attention to text associated with warning symbols. Before using the device, obtain and read the PiPER-L User Manual. For questions about use, contact support@agilex.ai.

> **Warning symbol:⚠**&#x49;ndicates a potentially hazardous situation which, if not avoided, may result in personal injury, property damage, or serious equipment damage.

> WARNING⚠: AgileX Robotics accepts no liability if the robotic arm is damaged, altered, or modified in any way. AgileX Robotics is not liable for damage to the robotic arm or any other equipment caused by programming errors or operational malfunctions.

Limitation of Liability: By using this robotic arm, you acknowledge that you have read, understood, accepted, and agreed to all terms and content in the user manual and safety information. Users are responsible for their actions and all resulting consequences, and agree to use the robotic arm only for lawful purposes in accordance with these terms and any related policies or guidelines established by AgileX Robotics. During use, strictly follow all requirements in the user manual and safety information. AgileX Robotics is not liable for personal injury, accidents, property loss, legal disputes, or conflicts of interest caused by prohibited use or force majeure. The robotic arm is not suitable for persons under 18 years of age or anyone without full civil capacity. Keep such persons away from the product and exercise additional caution when operating in their presence.

This manual does not cover the design, installation, or operation of a complete robotic-arm application system, nor all peripheral equipment that may affect the safety of such a system. The complete system must be designed and used in accordance with the safety requirements, standards, and regulations of the country where the robotic arm is installed.

The robotic-arm integrator and end customer are responsible for complying with applicable regulations and laws and for ensuring that the complete robotic-arm application presents no significant hazards.

This includes, but is not limited to, the following:

1. **Validation**&#x20;

* Perform a risk assessment of the complete robotic-arm system.
* Interconnect any additional safety equipment for other machinery identified by the risk assessment.
* Verify that the complete robotic-arm system, including its software and hardware, is correctly designed and installed.
* Integrators and end customers must assess all robotic-arm functions for safety in accordance with applicable regulations and laws, ensuring that the completed application presents no significant hazards or safety risks in actual use.
* Understand all potential safety risks before operating or using the equipment.
* Ensure that users do not modify any safety measures.
* Collect all technical documentation, including the risk assessment and this manual.

2. **Environment**

* Before first use, read this manual carefully to understand the basic operating procedures and requirements.
* Operate in a relatively open area. The robotic arm has no automatic obstacle-avoidance or sensing system.
* Use at an ambient temperature of -20 °C to 50 °C.
* Unless a custom IP rating is specified, the robotic arm has an IP22 dust- and water-protection rating.

3. **Inspection**

* Ensure that the robotic arm has no visible abnormalities.
* Ensure that all wiring harnesses are correctly connected before use.

4. **Operation**

* Keep the surrounding area relatively clear during operation.
* Operate within line of sight.
* The robotic arm has a maximum payload of 1.5 kg. Ensure that the payload does not exceed 1.5 kg during use.
* If the device behaves abnormally, stop using it immediately to prevent further injury or damage.
* If the device behaves abnormally, contact qualified technical personnel. Do not attempt unauthorized repairs.
* Use the device only in an environment that satisfies its specified IP protection rating.

5. **Operating Warnings⚠：**

* Always ensure that the robotic arm and its tool/end effector are correctly and securely mounted.
* If entering the robotic arm workspace is unavoidable, wear safety glasses and appropriate protective equipment.
* Ensure that the robotic arm has sufficient space to move freely.
* Do not wear loose clothing while operating the robotic arm. Tie back long hair.
* Do not use the robotic arm if it is damaged or abnormal.
* If the host-computer software reports an error, perform an emergency stop immediately and contact qualified technical personnel.
* Keep your head, face, and other body parts outside the reach of a robotic arm that is operating or about to operate.
* Never modify the robotic arm. Modifications may introduce hazards that the integrator cannot predict.
* Do not expose the robotic arm continuously to permanent magnetic fields. Strong magnetic fields may damage it.
* The robotic arm generates heat during operation. Do not handle or touch it while it is operating or immediately after it stops, as prolonged contact may cause discomfort. Disconnect power and allow one hour for the robotic arm to cool.
* Connecting different machines may increase existing hazards or introduce new ones. Always perform a comprehensive risk assessment of the entire installation. Different functional-safety levels may apply; when different safety or emergency-stop performance levels are required, always select the highest level. Read and understand the manuals for all equipment used in the installation.
* The robotic arm is not suitable for persons under 18 years of age or anyone without full civil capacity.

## 1. Robotic Arm Introduction <a href="#sygvh" id="sygvh"></a>

This six-degree-of-freedom robotic arm is designed for education and research, consumer applications, and industrial automation. With a 1.5 kg payload capacity, it is suitable for research and industrial applications such as humanoid robots, automated assembly, and automated handling. Six rotary joints provide comprehensive operating flexibility with high precision and repeatability. Its modular design simplifies maintenance and upgrades, while the intuitive user interface streamlines programming and operation so that non-specialists can get started quickly. Applications include scientific research, education, automotive manufacturing, electronics assembly, food processing, laboratory automation, and medical-equipment operation.

### 1.1 Product List <a href="#xvxiq" id="xvxiq"></a>

<br>

| Item                                     | Quantity |
| ---------------------------------------- | -------- |
| PiPER-L 6-DOF Robotic Arm                | 1        |
| Power adapter (adapter + power cord)     | 1        |
| Communication module (USB-to-CAN module) | 1        |
| Aviation connector                       | 1        |
| Base mounting screws                     | 4        |
| Base installation wrench                 | 1        |

### 1.2 Performance Specifications <a href="#mnuck" id="mnuck"></a>

| Parameter Type                                                                                                                                                                                                                                    | Item                                                              | Specification                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| <p>​<br></p><p>​<br></p><p><br></p><p>​<br></p><p>​<br></p><p><br></p><p><br></p><p><br></p><p><br></p><p>Structural Parameters</p><p><br></p><p><br></p><p><br></p><p><br></p><p><br></p><p><br></p><p><br></p><p><br></p><p><br></p><p><br></p> | Degrees of freedom                                                | 6                                                                                                |
| Payload                                                                                                                                                                                                                                           | 1.5KG                                                             |                                                                                                  |
| Main unit weight                                                                                                                                                                                                                                  | 4.5KG                                                             |                                                                                                  |
| Repeatability                                                                                                                                                                                                                                     | ±.0.1mm                                                           |                                                                                                  |
| Working radius                                                                                                                                                                                                                                    | 750mm                                                             |                                                                                                  |
| Standard supply voltage                                                                                                                                                                                                                           | DC24V                                                             |                                                                                                  |
| Power consumption                                                                                                                                                                                                                                 | Maximum power consumption ≤ 120 W; total power consumption ≤ 40 W |                                                                                                  |
| Material                                                                                                                                                                                                                                          | Aluminum-alloy frame; plastic housing                             |                                                                                                  |
| Controller                                                                                                                                                                                                                                        | Integrated                                                        |                                                                                                  |
| Communication method                                                                                                                                                                                                                              | CAN                                                               |                                                                                                  |
| Control method                                                                                                                                                                                                                                    | Drag teaching / offline trajectory / API / host computer          |                                                                                                  |
| External interfaces                                                                                                                                                                                                                               | Power interface × 1; CAN interface × 1                            |                                                                                                  |
| Base mounting dimensions                                                                                                                                                                                                                          | 70mm\*_70mm\*_&#x4D;5\*4                                          |                                                                                                  |
| Operating environment                                                                                                                                                                                                                             | Temperature: -20 to 50 °C; humidity: 25%–85%, non-condensing      |                                                                                                  |
| Noise                                                                                                                                                                                                                                             | <60dB                                                             |                                                                                                  |
| Installation                                                                                                                                                                                                                                      | Desktop installation                                              |                                                                                                  |
| <p>​<br></p><p>​<br></p><p>​<br></p><p>Motion Parameters</p>                                                                                                                                                                                      | Joint travel range                                                | <p>J1:±154°</p><p>J2:0°~195°</p><p>J3:-175°~0°</p><p>J4:±127°</p><p>J5:±89.5°</p><p>J6:±170°</p> |
| <p><br></p>                                                                                                                                                                                                                                       | Maximum joint speed                                               | <p>J1:180°/s</p><p>J2:195°/s</p><p>J3:180°/s</p><p>J4:225°/s</p><p>J5:225°/s</p><p>J6:225°/s</p> |
| Note: The above data are test results obtained by AgileX Robotics under controlled conditions. Results may vary depending on the environment and method of use; actual performance shall prevail.                                                 |                                                                   |                                                                                                  |

> **Important: The robotic-arm supply voltage must not exceed 26 V; otherwise, the circuitry may be damaged. When using an external power supply, ensure regulated voltage and a current rating of at least 10 A.**

| Two-Finger Gripper Parameters (Optional) | <p><br></p>                                                      |
| ---------------------------------------- | ---------------------------------------------------------------- |
| Main unit weight                         | 500g                                                             |
| Accuracy                                 | ±.0.5mm                                                          |
| Opening range                            | 0-100mm                                                          |
| Rated gripping force                     | 40N                                                              |
| Maximum gripping force                   | 50N                                                              |
| Supply voltage                           | DC24V                                                            |
| Power consumption                        | Maximum power consumption ≤ 50 W; total power consumption ≤ 30 W |
| Contact-surface material                 | Rubber                                                           |
| Controller                               | Integrated                                                       |
| Communication method                     | CAN                                                              |
| Control method                           | Drag teaching / offline trajectory / API / host computer         |
| External interfaces                      | Power interface\*1; CAN interface\*1                             |
| Installation method                      | Flange mounting                                                  |
| Operating environment                    | Temperature: -20 to 50 °C; humidity: 25%–85%, non-condensing     |
| Noise                                    | <60dB                                                            |
| Teach Pendant Parameters (Optional)      | <p><br></p>                                                      |
| Main unit weight                         | 550g                                                             |
| Accuracy                                 | ±.0.5mm                                                          |
| Opening range                            | 0-100mm                                                          |
| Rated gripping force                     | 40 N (force control and force feedback)                          |
| Maximum gripping force                   | 50 N (force control and force feedback)                          |
| Supply voltage                           | DC24V                                                            |
| Power consumption                        | Maximum power consumption ≤ 50 W; total power consumption ≤ 30 W |
| Contact-surface material                 | Rubber                                                           |
| Controller                               | Integrated                                                       |
| Communication method                     | CAN                                                              |
| Control method                           | Drag teaching / offline trajectory / API / host computer         |
| External interfaces                      | Power interface\*1; CAN interface\*1                             |
| Installation method                      | Flange mounting                                                  |
| Operating environment                    | Temperature: -20 to 50 °C; humidity: 25%–85%, non-condensing     |
| Noise                                    | <60dB                                                            |

Modified DH

| **Link** | **d (mm)** | **a (mm)** | **alpha (radians)** | **offset (radians)** |
| -------- | ---------- | ---------- | ------------------- | -------------------- |
| L(1)     | 123        | 0          | 0                   | 0                    |
| L(2)     | 0.0        | 0.0        | -pi/2               | -pi\*172.22/180      |
| L(3)     | 0.0        | 338.23     | 0.0                 | -102.78/180\*pi      |
| L(4)     | 320.75     | -23.01     | ​pi/2               | 0                    |
| L(5)     | 0          | 0          | -pi/2               | 0                    |
| L(6)     | 91         | 0.0        | pi/2                | 0                    |

## 2. Basic Introduction <a href="#ouh54" id="ouh54"></a>

The robotic arm has six degrees of freedom, a 1.5 kg end payload, and six rotary joints that provide comprehensive operating flexibility with high precision and repeatability. Its lightweight design combines fast motion with strong payload capacity, making it suitable for real-world data collection in embodied-intelligence applications.

<img src="../../.gitbook/assets/PiPER-L official image 2 image.png" alt="PiPER-L official image 2: image.png" width="516">

### 2.1 Electrical Interface Description <a href="#e8e54" id="e8e54"></a>

The robotic-arm accessory kit includes an aviation connector, a USB-to-CAN module, a data cable, a power adapter, and an XT30 2+2 interface reserved for an end-effector motor. Follow the instructions below.

**2.1.1 Arm-Base Electrical Interfaces**

<img src="../../.gitbook/assets/PiPER-L official image 3 official image 3" alt="PiPER-L official image 3: official image 3" width="1441">

​<br>

| 1 | Power and communication port | 2           | Status indicator |
| - | ---------------------------- | ----------- | ---------------- |
| 3 | Main controller–J2 connector | 4           | Positive supply  |
| 5 | Negative supply              | 6           | CAN-H            |
| 7 | CAN-L                        | <p><br></p> | <p><br></p>      |

> Note:Align the red dot with the red dot on the cable. The ribbed section of the aviation connector retracts when pulled backward. To install, point the red dot downward, align it with the raised mark, and insert the connector directly. To remove it, press/pull back the ribbed section and unplug it, as shown below.

<img src="../../.gitbook/assets/PiPER-L official image 4 official image 4" alt="PiPER-L official image 4: official image 4" width="762">

Indicator description for position 2 on the electrical panel:

| Indicator Color | Status Description                                                                                                                  |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Green flashing  | Robotic arm operating normally                                                                                                      |
| Green steady    | Main controller initializing                                                                                                        |
| Red flashing    | A flashing red indicator means the robotic arm is abnormal or has entered upgrade mode. In the former case, troubleshoot the fault. |

Teach-indicator description for the final joint:

| Teach Indicator Color | Status Description                               |
| --------------------- | ------------------------------------------------ |
| Off                   | Drag-teaching stopped / drag recording completed |
| Green steady          | Recording a drag-teaching trajectory             |
| Green flashing        | Replaying a drag-teaching trajectory             |

**Main-controller CAN termination-resistor switches:**

The main-controller CAN termination-resistor switches are primarily used when one master arm controls multiple follower arms:

No adjustment is required for single-arm use.

Factory default: switch 1 ON (down), switch 2 OFF (up), providing a default resistance of 60 Ω.

When more than two follower arms are used, set switch 1 ON (down) and switch 2 OFF (up) on one follower arm. Set both switches 1 and 2 OFF (up) on all other arms.

<img src="../../.gitbook/assets/PiPER-L official image 5 official image 5" alt="PiPER-L official image 5: official image 5" width="132">

**2.1.2 End-Effector Electrical Connection**

An XT30 2+2 interface is reserved at the final joint. Power and CAN definitions are shown below. Supply: 24 V, 2 A maximum. The end CAN interface supports only AgileX devices. Connecting any other CAN device is strictly prohibited and may cause uncontrolled damage.

<img src="../../.gitbook/assets/PiPER-L official image 6 official image 6" alt="PiPER-L official image 6: official image 6" width="187">

**2.1.3 Power-On Instructions**

For the first power-on, perform steps A–G in the following order:

1\. Connect the J2 connector at A.

2\. Connect the CAN wires of aviation connector B.

3\. Mate the XT30 connectors at C.

4\. Insert aviation connector D with its red dot facing downward.

5\. Connect the plug of power adapter E.

6\. Verify that the AC input of adapter E is connected, then apply power and wait until the electrical-panel indicator flashes green.

7\. Connect the USB cable to the computer.

<img src="../../.gitbook/assets/PiPER-L official image 7 official image 7" alt="PiPER-L official image 7: official image 7" width="775">

Note: Align the red dot with the red dot on the cable. The ribbed section of the aviation connector retracts when pulled backward. To install, point the red dot downward, align it with the raised mark, and insert the connector directly. To remove it, press/pull back the ribbed section and unplug it.

<img src="../../.gitbook/assets/PiPER-L official image 8 official image 8" alt="PiPER-L official image 8: official image 8" width="343">

### 2.2 Robotic Arm Coordinate Systems <a href="#tzq88" id="tzq88"></a>

#### 2.2.1 Origin Coordinate System (Same as Standard PiPER) <a href="#p1ela" id="p1ela"></a>

The PiPER-L origin (x: 0, y: 0, z: 0) is at the center of the circle shown in the figure.

<img src="../../.gitbook/assets/PiPER-L official image 9 image.png" alt="PiPER-L official image 9: image.png" width="462.4000244140625">

#### 2.2.2 User Coordinate System <a href="#tj8in" id="tj8in"></a>

The user coordinate system is the robotic-arm base coordinate system (coordinate system 1 in the figure).

<img src="../../.gitbook/assets/PiPER-L official image 10 image.png" alt="PiPER-L official image 10: image.png" width="506">

#### 2.2.3 Singular Positions <a href="#vawd8" id="vawd8"></a>

① The J1 axis is coaxial with the J4 axis.

② J4axis andJ6axis are coaxial.

③ The J1 axis is coaxial with the J6 axis.

#### 2.2.4 Zero-Point Setting <a href="#ecju1" id="ecju1"></a>

<img src="../../.gitbook/assets/PiPER-L official image 11 image.png" alt="PiPER-L official image 11: image.png" width="362">

The zero-point position is shown above. To set it, align joint J1 with the base scale; lower J2 and J3 naturally until they contact their limits; raise J5 to its limit; while facing the arm, rotate J4 clockwise to its limit; and place J6 at its current zero-point position. Then click Set All Zero Points.

### 2.3 Robotic Arm Load Curve <a href="#cgwnl" id="cgwnl"></a>

<br>

<img src="../../.gitbook/assets/PiPER-L official image 12 image.png" alt="PiPER-L official image 12: image.png" width="445">

End-Payload Curve

### 2.4 Mechanical Installation <a href="#guu5a" id="guu5a"></a>

#### 2.4.1 Base Installation <a href="#dwawn" id="dwawn"></a>

Secure the robotic-arm base with screws. The base has four M5 threaded through-holes, and the accessory kit includes four M5 screws that can be tightened with the supplied hex tool. Hole spacing is 70 mm in both directions. When designing an adapter for mobile equipment or a fixed worktop, use 70 mm hole spacing.

<img src="../../.gitbook/assets/PiPER-L official image 13 official image 13" alt="PiPER-L official image 13: official image 13" width="600.4000244140625">

#### 2.4.2 End-Tool Installation <a href="#wp2ga" id="wp2ga"></a>

<img src="../../.gitbook/assets/PiPER-L official image 14 image.png" alt="PiPER-L official image 14: image.png" width="589">

Other tools can be mounted to the end flange. Optional accessories include a two-finger gripper and teach pendant. As shown below, both are secured to the end using the flange.

<img src="../../.gitbook/assets/PiPER-L official image 15 image.png" alt="PiPER-L official image 15: image.png" width="429">

* Secure the robotic arm to the mounting surface. Remove the gripper, teach pendant, flange, and mounting bolts from the accessory set.
* Install the stop screw (M3 × 4, head diameter 4.5 mm) at the upper-left of the J6 motor when viewed as shown.
* Align the flange stop slot with the installed stop screw, then tighten six M3 ×\*8 hex-socket countersunk screws, as shown:

<br>

<img src="../../.gitbook/assets/PiPER-L official image 16 official image 16" alt="PiPER-L official image 16: official image 16" width="693">

* After installing the flange, take out the gripper or teach pendant. Their rear covers have a keyed structure. Insert the gripper or teach pendant as shown, then secure it with M3 × 14 hex-socket countersunk screws.

<br>

<img src="../../.gitbook/assets/PiPER-L official image 17 official image 17" alt="PiPER-L official image 17: official image 17" width="753">

* After installing the gripper or teach pendant, connect the power/communication cable from the accessory kit between J6 and the installed accessory.
* Connect the aviation cable to the robotic arm. Connect the USB-to-CAN module to the aviation cable—yellow to CAN-H and blue to CAN-L—then connect the module to the computer with the USB cable. Connect the aviation cable to the power adapter and power on the adapter.
* After power-on, confirm that the base indicator flashes green slowly. Open the host-computer software. Once communication is established, rotate the gripper or teach pendant to the limit position shown, click Set J6 Joint Zero Point, and then enable the robotic arm. Use the software to return J6 to zero and verify that the zero-point marks on J6 and the gripper/teach pendant align, as shown.

<br>

<img src="../../.gitbook/assets/PiPER-L official image 18 official image 18" alt="PiPER-L official image 18: official image 18" width="380">

#### 2.4.3 Desktop Installation <a href="#jmf5m" id="jmf5m"></a>

#### 2.4.3 Desktop Installation <a href="#sp9cj" id="sp9cj"></a>

The desktop mounting module is optional and is not included with the standard product. Contact us to purchase it separately. Dimensions are shown below. Ensure that it is securely fixed before operating the robotic arm.

<img src="../../.gitbook/assets/PiPER-L official image 19 official image 19" alt="PiPER-L official image 19: official image 19" width="1213">

#### 2.4.5 Robotic Arm Installation Orientation <a href="#dlgkw" id="dlgkw"></a>

Different mounting orientations require different settings. Select the appropriate installation orientation in the host-computer motor configuration according to the actual mounting position.

<img src="../../.gitbook/assets/PiPER-L official image 20 official image 20" alt="PiPER-L official image 20: official image 20" width="1672">

## 3. CAN Connection and Preparation <a href="#acbtv" id="acbtv"></a>

Expose the CAN wires from the connector. Connect CAN-\_H and CAN-\_L respectively to the CAN-to-\_TO\_USB adapter.

Connect the CAN-to-USB adapter to the laptop USB port. The connection is shown below.

<img src="../../.gitbook/assets/PiPER-L official image 21 示意图.jpg" alt="PiPER-L official image 21: 示意图.jpg" width="7022">

Crimp the CAN-H and CAN-L wires at the center of the terminals in the orientation shown below. Tightening the screw presses the terminal plate down onto the wire. After tightening, the terminal cavity should appear as shown, and the wire must not pull out under firm tension.

<img src="../../.gitbook/assets/PiPER-L official image 22 official image 22" alt="PiPER-L official image 22: official image 22" width="622">

#### 3.1 Teach Mode <a href="#b2ata" id="b2ata"></a>

The button indicator shows the drag-teaching state of the robotic arm.

<img src="../../.gitbook/assets/PiPER-L official image 23 image.png" alt="PiPER-L official image 23: image.png" width="560">

**3.1.1 Robotic Arm Indicator States**

1. Indicator off: drag teaching stopped / drag recording completed.
2. Green steady: recording a drag-teaching trajectory.

3\. Green flashing: replaying a drag-teaching trajectory.

**3.1.2 Switching the Drag-Teaching State**

1\. Single-click the button to switch between trajectory recording and recording completed.

2\. Double-click the button to replay the drag-teaching trajectory.

**3.1.3 Instructions**

First, check the indicator state.

1\. If the indicator is off, single-click the button. The green indicator should remain steady. You can then drag the robotic arm directly; this indicates trajectory-recording mode and begins recording.

2\. If the indicator is off and a trajectory has previously been recorded, double-click the button. The green indicator flashes at 500 ms intervals, indicating trajectory-replay mode. The robotic arm replays the recorded trajectory once.

3\. A steady indicator means trajectory recording is active. To end recording, single-click the button; the indicator turns off, showing that recording has ended. To replay the trajectory, follow step 2.

4\. A flashing indicator means trajectory replay is active.

> **Precautions:**
>
> 1\. During trajectory replay, maintain a safe distance from the robotic arm to prevent injury.
>
> 2\. Each time the robotic arm enters trajectory-recording mode, the previous trajectory is erased. Replay always uses the most recently recorded trajectory.
>
> 3\. The maximum trajectory-recording time is three minutes. Any trajectory exceeding this duration is invalid.
>
> 4\. After drag teaching, ensure that the indicator is off and drag teaching is stopped.
>
> 5\. Before using host-computer motion control or command control, ensure that the indicator is off and drag teaching is stopped. Use the host computer to switch the operating mode to Standby, then from Standby to CAN mode. For command control, likewise send Standby mode first, then CAN control mode.

#### 3.2 Cascading and Teleoperation <a href="#ifedj" id="ifedj"></a>

For dual-arm cascade control and teleoperation, first use the host-computer software to configure one arm as the master and the other as the follower. The linkage-control area is shown below. To enable dual-arm linkage, configure the input/output states and offsets on this page, and connect both USB-to-CAN modules to the same computer.

<img src="../../.gitbook/assets/PiPER-L official image 24 official image 24" alt="PiPER-L official image 24: official image 24" width="1499">

## 4. Host-Computer Software <a href="#gxfbr" id="gxfbr"></a>

### 4.1 ArmRobotUA Overview <a href="#oem47" id="oem47"></a>

Software download (operation is the same as for standard PiPER):

**Attachment:** [ArmRobotUA\_V1.5.0.251210\_beta (1).zip](https://agilexsupport.yuque.com/attachments/yuque/0/2026/zip/29291030/1769354133588-2a7dd436-81d2-4515-af8f-b2066ab1c018.zip) — ArmRobotUA host-computer software package.

On a PC running Windows 7 or later, double-click the host-computer application. This human-machine interface controls the robotic arm and reads external feedback data. The interface is shown below.

Host-computer application desktop icon

<img src="../../.gitbook/assets/PiPER-L official image 25 official image 25" alt="PiPER-L official image 25: official image 25" width="1266">

Host-computer operating interface

Host-Computer Panel Areas

| No. | Item                                         |
| --- | -------------------------------------------- |
| 1   | Robotic-arm communication button             |
| 2   | Vertical menu options                        |
| 3   | Speed-percentage setting                     |
| 4   | Robotic-arm enable button                    |
| 5   | Robotic-arm emergency-stop button            |
| 6   | Window minimize, maximize, and close buttons |
| 7   | Operating area                               |
| 8   | 3D simulation model                          |
| 9   | Trajectory library                           |
| 10  | Robotic-arm joint status                     |
| 11  | Robotic-arm status bar                       |

### 4.2 Robotic Arm Communication <a href="#pqvz3" id="pqvz3"></a>

Click the robotic-arm communication button at the upper left of the window to open the\[Connect Robotic Arm]window. It automatically detects CAN devices connected to the PC and displays them. You can manually connect or disconnect the selected CAN device. After a successful connection, the button monitors and displays the real-time online status of the connected CAN device.

<img src="../../.gitbook/assets/PiPER-L official image 26 official image 26" alt="PiPER-L official image 26: official image 26" width="1712">

Robotic-arm communication button

<div><img src="../../.gitbook/assets/PiPER-L official image 27 official image 27" alt="PiPER-L official image 27: official image 27" width="303"> <img src="../../.gitbook/assets/PiPER-L official image 28 official image 28" alt="PiPER-L official image 28: official image 28" width="288"></div>

Robotic-arm status (left: online; right: offline)

### 4.3 Vertical Menu <a href="#yanfw" id="yanfw"></a>

Click an option name on the left to switch to its panel and select the required function. The selected item has a light-blue background.

<img src="../../.gitbook/assets/PiPER-L official image 29 official image 29" alt="PiPER-L official image 29: official image 29" width="1712">

Vertical menu options

### 4.4 Speed Percentage <a href="#bt73u" id="bt73u"></a>

After connecting the CAN device, use the speed-percentage control at the top of the window to set the robotic-arm motion speed as a percentage of its maximum speed.

<img src="../../.gitbook/assets/PiPER-L official image 30 official image 30" alt="PiPER-L official image 30: official image 30" width="1280">

Speed-percentage setting

### 4.5 Robotic Arm Enable Button <a href="#ozkvk" id="ozkvk"></a>

After connecting the CAN device, the enable button at the top of the window displays the current states of all six joints. Clicking it toggles all six joints simultaneously.

<img src="../../.gitbook/assets/PiPER-L official image 31 official image 31" alt="PiPER-L official image 31: official image 31" width="679">

Robotic-arm enable button

<img src="../../.gitbook/assets/PiPER-L official image 32 official image 32" alt="PiPER-L official image 32: official image 32" width="1672">

### 4.6 Robotic Arm Emergency-Stop Button <a href="#c8zrd" id="c8zrd"></a>

After connecting the CAN device, press the emergency-stop button at the top of the window to stop all robotic-arm motion immediately. Press it again to recover, then enable the arm before resuming operation.

<img src="../../.gitbook/assets/PiPER-L official image 33 official image 33" alt="PiPER-L official image 33: official image 33" width="650">

Robotic-arm emergency-stop button

<img src="../../.gitbook/assets/PiPER-L official image 34 official image 34" alt="PiPER-L official image 34: official image 34" width="1672">

<img src="../../.gitbook/assets/PiPER-L official image 35 official image 35" alt="PiPER-L official image 35: official image 35" width="1672">

### 4.7 Window Controls <a href="#huhog" id="huhog"></a>

The three buttons at the upper right minimize, maximize, and close the window respectively.

<img src="../../.gitbook/assets/PiPER-L official image 36 official image 36" alt="PiPER-L official image 36: official image 36" width="616">

Window minimize, maximize, and close buttons

### 4.8 Operating Area <a href="#cjug3" id="cjug3"></a>

The center of the window is the operating area. It switches together with the\[2. Vertical Menu]selection. Choose the required panel; for example, the motion-control area shown below provides direct joint control.

<img src="../../.gitbook/assets/PiPER-L official image 37 official image 37" alt="PiPER-L official image 37: official image 37" width="459">

Motion-control area

Select one of the following motion modes:

| Motion Mode           | Procedure                                                                                                                                                                                                                                                                                                                   | Remarks                                                                                                                                                                                                                         |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Point-to-Point Motion | <p>Enter the target end pose (x, y, z, rx, ry, rz) and click Apply. The robotic arm moves to the specified point.</p><p>You can also click the x, y, and z icons to increase or decrease the coordinate values and change the end position.<strong>Click Apply to move the robotic arm to the specified point.</strong></p> | The entered point may be unreachable. In that case, the robotic arm does not move and an error is displayed.                                                                                                                    |
| Arc Motion            | <p>Enter three poses: start (x, y, z, rx, ry, rz), intermediate (x, y, z, rx, ry, rz), and end (x, y, z, rx, ry, rz). The robotic arm plans and executes an arc through these points.</p><p>​<br></p>                                                                                                                       | An entered point or a point on the planned arc may be unreachable. In that case, the robotic arm does not move and an error is displayed.                                                                                       |
| Joint Motion          | <p>Enter the angle for each joint and click Apply; the robotic-arm controller executes the command.</p><p>You can also drag the sliders to change the values.<strong>You must still click Apply for the changes to take effect.</strong></p>                                                                                | If a commanded joint angle exceeds its joint limit, the arm does not move. Send only angles within the joint limits.                                                                                                            |
| Linear Motion         | Enter the robotic-arm pose (x, y, z, rx, ry, rz). The robotic arm moves in a straight line to the specified point.                                                                                                                                                                                                          | If the entered point or any point on the planned linear trajectory is unreachable, the motion has no valid solution.                                                                                                            |
| MIT Control           | Select the target joint number and enter the joint angle, velocity, kp (position gain), kd (velocity gain), and joint torque.                                                                                                                                                                                               | This mode directly controls joint-motor position, velocity, and torque. Adjusting target velocity, kp, kd, and torque enables hybrid control of these quantities. This mode is hazardous; contact technical support before use. |

### 4.9 Motion-Control Area <a href="#po7g9" id="po7g9"></a>

The robotic arm has six joints, named Joint 1 through Joint 6 from bottom to top. They correspond to the six joint controls. Edit a joint angle or use the plus/minus buttons to operate the joint (unit: °).

<img src="../../.gitbook/assets/PiPER-L official image 38 official image 38" alt="PiPER-L official image 38: official image 38" width="869">

Joint angles

The three lower buttons are ① Return to Zero, ② Load, and ③ Send. Button ① sends the factory initial joint angles; button ② loads the current angles of all six joints into the edit fields; button ③ sends the six edited joint angles to the robotic arm. Actual behavior shall prevail.

<img src="../../.gitbook/assets/PiPER-L official image 39 official image 39" alt="PiPER-L official image 39: official image 39" width="991">

Joint buttons

The lighting-control area is shown below. If joint light boards are installed, it controls the lights on all six joints.

<img src="../../.gitbook/assets/PiPER-L official image 40 official image 40" alt="PiPER-L official image 40: official image 40" width="506">

Lighting-control area

The joint number and RGB channels at the top identify the light board and channel grayscale values to operate. The result field below shows the calculated color. Click Confirm to apply it to the light board.

### 4.10 Linkage-Control Area <a href="#l3v1a" id="l3v1a"></a>

The linkage-control area is shown below. To implement dual-arm linkage, configure the input/output states and offsets on this page.

<img src="../../.gitbook/assets/PiPER-L official image 41 official image 41" alt="PiPER-L official image 41: official image 41" width="1499">

Linkage-control area

### 4.11 Gripper Control (Gripper-Equipped Models Only) <a href="#m2cb4" id="m2cb4"></a>

The gripper/teach-pendant control area is shown below. It sets gripper enable status, opening, torque, and related values. The right side of the software displays corresponding gripper feedback.

<img src="../../.gitbook/assets/PiPER-L official image 42 official image 42" alt="PiPER-L official image 42: official image 42" width="1672">

Gripper-control area

### 4.12 Joint Settings <a href="#tsr2u" id="tsr2u"></a>

The joint-settings area is shown below. It edits maximum/minimum angles, maximum velocity, and maximum acceleration for all six joints. Procedure: Edit → Save.

<img src="../../.gitbook/assets/PiPER-L official image 43 official image 43" alt="PiPER-L official image 43: official image 43" width="1672">

Joint-settings area

### 4.13 Motion-Profile Settings <a href="#je1j0" id="je1j0"></a>

The motion-profile area is shown below. It configures maximum end linear/angular velocity and maximum linear/angular acceleration. Initialize restores the factory settings.

<img src="../../.gitbook/assets/PiPER-L official image 44 official image 44" alt="PiPER-L official image 44: official image 44" width="1672">

Joint-settings area

<img src="../../.gitbook/assets/PiPER-L official image 45 official image 45" alt="PiPER-L official image 45: official image 45" width="409">

Initialize button

### 4.14 Collision Level <a href="#ymhlh" id="ymhlh"></a>

The collision-level settings shown below assign levels 1–8 to each of the six joints. Procedure: Edit → Save.

<img src="../../.gitbook/assets/PiPER-L official image 46 official image 46" alt="PiPER-L official image 46: official image 46" width="1672">

<img src="../../.gitbook/assets/PiPER-L official image 47 official image 47" alt="PiPER-L official image 47: official image 47" width="1672">

Collision-level settings

### 4.15 Joint Information <a href="#loov1" id="loov1"></a>

The joint-information area shown below displays joint motion and status information.

<img src="../../.gitbook/assets/PiPER-L official image 48 official image 48" alt="PiPER-L official image 48: official image 48" width="1672">

<img src="../../.gitbook/assets/PiPER-L official image 49 official image 49" alt="PiPER-L official image 49: official image 49" width="1672">

<img src="../../.gitbook/assets/PiPER-L official image 50 official image 50" alt="PiPER-L official image 50: official image 50" width="1672">

### 4.16 Motor Settings <a href="#x7vw8" id="x7vw8"></a>

The motor-settings area shown below configures enable/disable status, zero points, and error clearing for all six joint motors.

<img src="../../.gitbook/assets/PiPER-L official image 51 official image 51" alt="PiPER-L official image 51: official image 51" width="1672">

<img src="../../.gitbook/assets/PiPER-L official image 52 official image 52" alt="PiPER-L official image 52: official image 52" width="1672">

Motor settings

### 4.17 Firmware Upgrade <a href="#d9xif" id="d9xif"></a>

The robotic-arm firmware-upgrade page is shown below. Follow these steps:

① Check the information area (area 1) for node information. If it appears, the robotic arm has entered upgrade mode normally and the upgrade may proceed.

② Click Load Package (area 5), select the provided firmware file (.bin), and confirm. The selected package information appears in area 4.

③ Click Start Upgrade (area 6) and wait for the progress bar (area 2) to complete. The normal duration is approximately 2–3 minutes.

<img src="../../.gitbook/assets/PiPER-L official image 53 official image 53" alt="PiPER-L official image 53: official image 53" width="1498">

<img src="../../.gitbook/assets/PiPER-L official image 54 official image 54" alt="PiPER-L official image 54: official image 54" width="1265">

<img src="../../.gitbook/assets/PiPER-L official image 55 official image 55" alt="PiPER-L official image 55: official image 55" width="1672">

Upgrade area

### 4.18 3D Simulation Model <a href="#isvkx" id="isvkx"></a>

The right side of the window shows a real-time 3D model of the robotic arm. The upper left displays the current feedback pose and six joint angles. The three lower buttons are ① Help, ② Reset View, and ③ Settings. Help describes use of the 3D area; Reset View restores the initial view; Settings configures host-computer parameters. Actual behavior shall prevail.

<img src="../../.gitbook/assets/PiPER-L official image 56 official image 56" alt="PiPER-L official image 56: official image 56" width="812">

3D simulation model

### 4.19 Trajectory Library <a href="#drr5e" id="drr5e"></a>

Click Trajectory Library below the vertical menu to open a window where you can create, edit, and run a complete robotic-arm trajectory.

<img src="../../.gitbook/assets/PiPER-L official image 57 official image 57" alt="PiPER-L official image 57: official image 57" width="1280">

Trajectory-library window

① Import File: import a local trajectory-library .log file.

② Create: create a new motion trajectory.

③ Delete: delete the selected trajectory.

④ Send: send the selected trajectory and run it once, multiple times, or continuously.

⑤ Export File: export the selected trajectory to a local file.

Double-click any trajectory to open its secondary menu and edit its details as shown below. Right-click for create, read, update, and delete operations.

<img src="../../.gitbook/assets/PiPER-L official image 58 official image 58" alt="PiPER-L official image 58: official image 58" width="1280">

Trajectory-library secondary menu

### 4.20 Robotic Arm Joint-Status Button <a href="#kesuv" id="kesuv"></a>

Click the robotic-arm joint-status button at the lower left of the window to open the\[Joint Status]window shown below. It monitors the status of all six joints in real time, and the button displays the current connected-joint status.

<img src="../../.gitbook/assets/PiPER-L official image 59 official image 59" alt="PiPER-L official image 59: official image 59" width="1506">

Joint-status window

<img src="../../.gitbook/assets/PiPER-L official image 60 official image 60" alt="PiPER-L official image 60: official image 60" width="643">

Real-time joint-status monitoring

### 4.21 Robotic Arm Status Bar <a href="#ugoiy" id="ugoiy"></a>

The robotic-arm status bar at the lower right monitors robotic-arm status information in real time, as shown below.

<img src="../../.gitbook/assets/PiPER-L official image 61 official image 61" alt="PiPER-L official image 61: official image 61" width="1496">

<img src="../../.gitbook/assets/PiPER-L official image 62 official image 62" alt="PiPER-L official image 62: official image 62" width="1280">

Robotic-arm status bar

## 5. Secondary Development <a href="#a2lpk" id="a2lpk"></a>

For secondary development, Python SDK and ROS 2 driver packages are currently provided. Links are listed below. For detailed development instructions, refer to the linked GitHub repositories.

| Category                                       | Link                                                                                                                                     |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| SDK                                            | [https://github.com/agilexrobotics/pyAgxArm](https://github.com/agilexrobotics/pyAgxArm)                                                 |
| ROS2-HUMBLE                                    | [https://github.com/agilexrobotics/agx\_arm\_ros](https://github.com/agilexrobotics/agx_arm_ros)                                         |
| URDF                                           | [https://github.com/agilexrobotics/agx\_arm\_urdf](https://github.com/agilexrobotics/agx_arm_urdf)                                       |
| MOVEIT2                                        | [https://github.com/agilexrobotics/agx\_arm\_sim/tree/master/Moveit2](https://github.com/agilexrobotics/agx_arm_sim/tree/master/Moveit2) |
| <p>GAZEBO</p><p>(Integrated with MoveIt 2)</p> | [https://github.com/agilexrobotics/agx\_arm\_sim/tree/master/Moveit2](https://github.com/agilexrobotics/agx_arm_sim/tree/master/Moveit2) |
| ISSAC SIM                                      | [https://github.com/agilexrobotics/agx\_arm\_sim](https://github.com/agilexrobotics/agx_arm_sim)                                         |

## 6. Robotic Arm CAN Protocol <a href="#wygk8" id="wygk8"></a>

The robotic arm provides a CAN interface for user development. Commands can be sent through this interface to control the arm.

CAN communication uses the CAN 2.0B standard, a 1000 kbit/s bit rate, and MOTOROLA (MSB) message format.

To develop with CAN commands, contact AgileX technical support for the CAN protocol manual.

CAN protocol manual:[https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/qii9wce225nvworv?singleDoc#7305](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/qii9wce225nvworv?singleDoc#7305)Robotic Arm External Communication Protocol 2025010

## 7. Maintenance and Care <a href="#aqikj" id="aqikj"></a>

Maintenance is required to preserve high performance over the service life of the robotic arm. Follow all instructions in this manual strictly. Maintenance ensures normal operation of the robotic arm and its accessories.

### 7.1 Storage <a href="#kxgqa" id="kxgqa"></a>

After use, return the robotic arm to its zero point, disconnect power, and store it. Organize the wiring harness to prevent tangling or excessive pulling.

Operating and storage environment: temperature:-20-50 °C; humidity: 25%–85%, non-condensing.

### 7.2 Maintenance <a href="#xhbsh" id="xhbsh"></a>

Perform maintenance only when the robotic arm is at its zero point and powered off. After disconnecting power, perform the following:

> **Note:**\
> Cleaning: Remove dust, dirt, and oil with a wet wipe or a dry cloth lightly dampened with water.
>
> Fastener inspection: Check for loose screws.
>
> Motor inspection: Check the motors and structural components for damage or deformation.
>
> Cable inspection: Check that the power and CAN cables are secure and that their jackets are undamaged.

## 7.3 Emergency Handling <a href="#fqriz" id="fqriz"></a>

### 7.3.1 Power-Off <a href="#hz7ht" id="hz7ht"></a>

In an emergency, disconnect power by unplugging the aviation connector. Be aware that the robotic arm becomes unpowered and may drop immediately; prevent injury and damage to the arm or its surroundings. Unplugging is an emergency response and is not a protective measure against injury.

### 7.3.2 Emergency Stop <a href="#i1cqe" id="i1cqe"></a>

When connected to the host computer, use the software Pause button to pause and resume robotic-arm motion.

<br>

<br>

## 8. Dimensional Drawings <a href="#wkqun" id="wkqun"></a>

3D STEP model files:

[https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/qqnssyindu0y2vgw?singleDoc#](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/qqnssyindu0y2vgw?singleDoc)PiPER-L Model Files

### 8.1 Robotic Arm Dimensions <a href="#sj0qk" id="sj0qk"></a>

<img src="../../.gitbook/assets/PiPER-L official image 63 image.png" alt="PiPER-L official image 63: image.png" width="582">

<img src="../../.gitbook/assets/PiPER-L official image 64 image.png" alt="PiPER-L official image 64: image.png" width="1227">

### 8.4 Base <a href="#dnp30" id="dnp30"></a>

<img src="../../.gitbook/assets/PiPER-L official image 65 official image 65" alt="PiPER-L official image 65: official image 65" width="829">

### 8.5 End Mounting Surface <a href="#wmnpr" id="wmnpr"></a>

<img src="../../.gitbook/assets/PiPER-L official image 66 official image 66" alt="PiPER-L official image 66: official image 66" width="738">

### 8.6 Flange Dimensions <a href="#y0qgc" id="y0qgc"></a>

<img src="../../.gitbook/assets/PiPER-L official image 67 official image 67" alt="PiPER-L official image 67: official image 67" width="1170">

### 8.7 Gripper Dimensions <a href="#cx5ts" id="cx5ts"></a>

<img src="../../.gitbook/assets/PiPER-L official image 68 official image 68" alt="PiPER-L official image 68: official image 68" width="1359">

### 8.8 Teach Pendant Dimensions <a href="#xmhna" id="xmhna"></a>

<img src="../../.gitbook/assets/PiPER-L official image 69 official image 69" alt="PiPER-L official image 69: official image 69" width="1279">

### 8.9 G-Clamp Dimensions <a href="#z4amv" id="z4amv"></a>

<img src="../../.gitbook/assets/PiPER-L official image 70 official image 70" alt="PiPER-L official image 70: official image 70" width="1290">

### 8.10 Exploded View of 100 mm Gripper <a href="#nnhpp" id="nnhpp"></a>

<img src="../../.gitbook/assets/PiPER-L official image 71 微信图片_20260610102303_2_2.png" alt="PiPER-L official image 71: 微信图片_20260610102303_2_2.png" width="1020">



### Development Resources

* [pyAgxArm Python SDK](https://github.com/agilexrobotics/pyAgxArm) — current official SDK for PiPER, PiPER-H, PiPER-L, and PiPER-X.
* [PiPER SDK repository](https://github.com/agilexrobotics/piper_sdk) — legacy and V2 Python interfaces, CAN setup, examples, and release history.
* [AgileX arm ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/ros2) — select the exact model with `arm_type:=piper`, `piper_h`, `piper_l`, or `piper_x`.
* [PiPER-series URDF, Xacro, and mesh resources](https://github.com/agilexrobotics/agx_arm_urdf) — separate official model directories are provided for PiPER, PiPER-H, PiPER-L, and PiPER-X.
* [PiPER-series firmware compatibility reference](https://github.com/agilexrobotics/pyAgxArm/blob/master/docs/piper/firmware_reference.md) — read the arm firmware first and choose the matching SDK driver; PiPER-X has additional version-specific joint-sign behavior. This page is a compatibility reference, not a firmware binary download.
