# NERO User Manual

### AgileX NERO 7-DOF 3kg Payload Robotic Arm for Embodied A

### AgileX NERO Gripper

{% embed url="https://openelab.io/products/agilex-nero-gripper" %}



Accessory reference see Gripper Master-Slave Control and Legacy Gripper Compatibility in this manual.

{% embed url="https://openelab.io/products/agilex-nero-embodied-ai-arm" %}

<img src="../../.gitbook/assets/image (1171).png" alt="image.png" width="592">

Document Version: V1.0.0

<img src="../../.gitbook/assets/image (1172).png" alt="image.png" width="449">

Version Update Description

| No. | Version | Date       | Editor  | Reviewer     | Note          |
| --- | ------- | ---------- | ------- | ------------ | ------------- |
| 1   | V.1.0.0 | 2025/12/18 | Cynthia | <p>​<br></p> | File Creation |
|     |         |            |         |              |               |
|     |         |            |         |              |               |
|     |         |            |         |              |               |

## **Important Safety Information** <a href="#odniv" id="odniv"></a>

This chapter contains crucial safety instructions. Any individual or organization must read and understand this information before using the device, especially before powering it on for the first time. It is essential to follow all assembly instructions and guidelines provided in this manual. Pay special attention to the text with warning signs. Before using the Nero device, be sure to read the **NERO User Manual**. For any questions regarding usage, please contact us at support@agilex.ai.

> **Warning**: ⚠ This indicates a potentially hazardous situation. Failure to avoid it may result in personal injury, property damage, and severe equipment damage.

> **WARNING ⚠**: Agilex Robotics shall not be liable for any damage caused by a robotic arm that has been damaged, altered, or modified in any way. Agilex Robotics shall not be held responsible for any damage to the robotic arm or other equipment arising from program errors or non-standard operations.

**​**<br>

Limitation of Liability: By using this robotic arm, you acknowledge that you have read, understood, and accepted all terms and content of this user manual and safety information. The user undertakes full responsibility for their actions and all resulting consequences. The user agrees to use the robotic arm solely for legitimate purposes and complies with these terms as well as any related policies or guidelines established by Agilex Robotics. During operation, strictly adhere to all requirements, including but not limited to the user manual and safety information. Agilex Robotics shall not be liable for personal injury, accidents, property damage, legal disputes, or conflicts of interest caused by non-compliance with usage instructions or unavoidable factors. This robotic arm is not suitable for use by individuals under 18 years of age or those without full civil capacity. Please prevent such individuals from accessing this product, and exercise extra caution when operating the device in their presence.

The information in this manual does not cover the design, installation, and operation of a complete robotic arm application, nor does it include all peripheral equipment that may affect the safety of the complete system. The design and use of the complete system must comply with safety requirements specified in the standards and regulations of the country where the robotic arm is installed.

Integrators and end-users of the robotic arm are responsible for ensuring compliance with relevant regulations and applicable laws, and for ensuring that no significant hazards exist in the complete robotic arm application.

This includes but is not limited to the following:

1. **Validity and Responsibility**

* Conduct a risk assessment of the complete robotic arm system.
* Integrate additional safety devices for machinery as defined in the risk assessment.
* Verify the accuracy of the design and installation of the entire robotic arm system, including software and hardware components.
* Integrators and end-users must conduct safety assessments in accordance with relevant regulations and applicable laws for all functions related to this robotic arm, ensuring no significant hazards or safety risks exist in practical applications.
* Be aware of potential safety risks before operating and using the equipment.
* Ensure that users do not modify any safety measures.
* Collect all documents in the technical files, including the risk assessment and this manual.

2. **Environment**

* Read this manual carefully before first use to understand the basic operation content and specifications.
* Use the robotic arm in a relatively open area. The robotic arm is not equipped with any automatic obstacle avoidance or sensing sensors.
* Operate within an ambient temperature range of -20℃ to 50℃.
* Unless customized with a specific IP rating, the robotic arm has an IP22 rating for dust and water resistance.

3. **Inspection**

* Ensure the robotic arm has no obvious abnormalities.
* Verify that all wire connections are secure during use.

4. **Operation**

* Maintain a clear and unobstructed area around the robotic arm during operation.
* Operate the robotic arm within the line of sight.
* The maximum payload capacity of the robotic arm is 3KG. Ensure the effective load does not exceed this limit during use.
* Immediately stop using the device if any abnormality occurs to avoid secondary damage.
* Contact relevant technical personnel if the device malfunctions. Do not attempt to handle the issue without authorization.
* Use the device in an environment that meets the requirements of its IP rating.

5. **Usage Warnings ⚠**

* Ensure the robotic arm and tools/end-effectors are always correctly and securely fastened in place.
* Wear safety goggles and protective equipment when entering the robotic arm's workspace is unavoidable.
* Ensure the robotic arm has sufficient space for unrestricted movement.
* Ensure safety measures are established as defined in the risk assessment.
* Do not wear loose clothing when operating the robotic arm. Tie long hair back before the operation.
* Do not use the robotic arm if it is damaged or shows any signs of abnormality.
* If the host computer software displays an error message, perform an emergency stop immediately and contact technical personnel.
* Ensure that people keep their heads, faces, and other body parts outside the reach of the robotic arm during operation or before starting the operation.
* Do not modify the robotic arm. Modifications may lead to unpredictable hazards for integrators.
* Do not expose the robotic arm to permanent magnetic fields. Strong magnetic fields may damage the robotic arm.
* The robotic arm generates heat during operation. Do not handle or touch the robotic arm while it is operating or immediately after stopping, as prolonged contact may cause discomfort. Disconnect the power supply and wait for one hour for the robotic arm to cool down completely.
* Connecting different machinery may increase hazards or create new ones. Always conduct a comprehensive risk assessment of the entire installation. Different functional safety levels may apply based on the risk assessment; therefore, always select the highest performance level when different safety and emergency stop performance levels are required. Always read and understand the manuals of all equipment used in the installation.
* This robotic arm is not suitable for use by individuals under 18 years of age or those without full civil capacity.

## 1 Robotic Arm Overview <a href="#sygvh" id="sygvh"></a>

This 7-degree-of-freedom (DOF) robotic arm is specially designed for the education and research industry, consumer application scenarios, and industrial automation. It has a payload capacity of 3kg and is suitable for various scientific research and industrial applications, such as humanoid robots, automatic assembly, and automatic handling. The 7 joints provide comprehensive operational flexibility, ensuring high precision and repeatability. The robotic arm adopts a modular design for easy maintenance and upgrades. It provides an intuitive user interface that simplifies programming and operation processes, enabling even non-professionals to get started quickly. It can be widely used in scientific research, education and teaching, automobile manufacturing, electronic assembly, food processing, laboratory automation, and medical equipment operation.

### 1.1 Product List <a href="#xvxiq" id="xvxiq"></a>

| Name                                 | Quantity |
| ------------------------------------ | -------- |
| 7 DOF Robotic Arm                    | 1        |
| USB to CAN module                    | 1        |
| Power Adapter (Adapter + Power Cord) | 1        |
| MicroUSB cable                       | 1        |
| Base Mounting Screws                 | 4        |
| Base Mounting Wrench                 | 1        |

### 1.2 Performance Parameters <a href="#mnuck" id="mnuck"></a>

| **Parameter Type**          | **Item**                                                                                                       | **Specification**                                                                                                                                           |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Structural Parameters**   | Degrees of Freedom                                                                                             | 7                                                                                                                                                           |
| Payload                     | 3KG                                                                                                            |                                                                                                                                                             |
| Weight                      | 4.8KG                                                                                                          |                                                                                                                                                             |
| Repeat Positioning Accuracy | ±0.1mm                                                                                                         |                                                                                                                                                             |
| Working Radius              | 580mm                                                                                                          |                                                                                                                                                             |
| Standard Supply Voltage     | DC24V                                                                                                          |                                                                                                                                                             |
| Power Consumption           | <p>Max Power ≤ 150W;</p><p>Comprehensive Power ≤ 60W</p>                                                       |                                                                                                                                                             |
| Material                    | <p>Aluminum Alloy Frame;</p><p>Plastic Shell</p>                                                               |                                                                                                                                                             |
| Controller                  | Integrated                                                                                                     |                                                                                                                                                             |
| Communication Method        | CAN/HTTP/TCP                                                                                                   |                                                                                                                                                             |
| Control Method              | Drag Teaching/Offline Trajectory/API/Host Software teaching                                                    |                                                                                                                                                             |
| External Interfaces         | 1×Power Interface, 1×CAN Interface, 1×Ethernet Interface                                                       |                                                                                                                                                             |
| Base Mounting Dimensions    | 70mm×70mm×M5×4                                                                                                 |                                                                                                                                                             |
| Operating Environment       | Temperature: -20℃ to 50℃; Humidity: 25% to 85%, Non-condensing                                                 |                                                                                                                                                             |
| Noise                       | <60dB                                                                                                          |                                                                                                                                                             |
| Mounting Method             | <p>Table Mounting, Side Mounting, Upside-down Mounting;</p><p>Compatible with All Agilex Robotics Products</p> |                                                                                                                                                             |
| **Motion Parameters**       | Joint Motion Range                                                                                             | <p>J1: -157° ~ 157°</p><p>J2: -15° ~ 190°</p><p>J3: -160° ~ 160°</p><p>J4: -60° ~ 125°</p><p>J5: -160° ~ 160°</p><p>J6: -43° ~ 58°</p><p>J7: -90° ~ 90°</p> |
| <p><br></p>                 | Maximum Joint Speed                                                                                            | <p>J1: 180°/s</p><p>J2: 180°/s</p><p>J3: 180°/s</p><p>J4: 225°/s</p><p>J5: 225°/s</p><p>J6: 225°/s</p><p>J7: 225°/s</p>                                     |

**Note**: The above data are test results of Agilex robotic arms in a controlled test environment. Results may vary under different environments and usage conditions; please refer to actual experience.

## 2 Basic Introduction <a href="#ouh54" id="ouh54"></a>

This robotic arm features 7 degrees of freedom and a 3kg end-effector payload. The seven rotating joints provide comprehensive operational flexibility, ensuring high precision and repeatability. It adopts a lightweight design, enabling the robotic arm to achieve fast movement while maintaining a high load capacity. It can be widely used for real-scenario data collection in embodied intelligence research.

<img src="../../.gitbook/assets/微信图片_20260118225938_441_140 (2).png" alt="微信图片_20260118225938_441_140.png" width="934">

> **Precautions**：
>
> * **Joint Zero-Point Calibration:** The joint zero-point must be set while the robotic arm is in its default vertical upright position. Otherwise, the gravity compensation function in Teaching mode and Master-Slave mode may not function correctly.
> * **Mode Management:** The system utilizes a state machine for mode management. Teaching mode, Trajectory mode, Master-Slave (Linkage Control) mode, and Web Control mode are mutually independent. For example, if you need to adjust the speed while in Trajectory Control mode, you must first switch to Web Control mode via the Web button; trajectory motion will stop upon switching, after which the speed can be configured.
> * **Automatic Zero-Setting:** During the automatic joint zero-setting process, the motors will first move to the mechanical limit positions before returning to the correct position. Do not obstruct or interfere with the robotic arm during this process.
> * **Joint 6 Calibration:** After any manual or automatic zero-setting of Joint 6, the system will execute a calibration process. Please do not obstruct this process.
> * **Master-Slave Connection:** When connecting the master and slave arms, ensure that the master arm and slave arm are in close proximity. Otherwise, the slave arm will move rapidly to track the master arm's position, posing a safety risk.
> * **Gripper Master-Slave Control:** To use master-slave control for the gripper, select the "Gripper" type in the custom controller column and enable the gripper before operation.
> * **Kinematic Control:** During kinematic control, avoid positioning joints J2, J3, J4, and J5 at 0 position as much as possible to reduce the risk of the robotic arm entering a singularity configuration.
> * **Legacy Gripper Compatibility:** If using a previously purchased Piper gripper on Nero (not required for new purchases), the gripper ID must be modified according to the 《_Nero Gripper ID Modification Guide》_ before the first use. Failure to do so will cause ID conflicts, which will severely impact kinematics and gravity compensation.
> * **Mounting Definitions:** Side mounting is defined as installing the arm with the Ethernet port facing downward at the default zero-point position. Inverted mounting is defined as installing the robotic arm completely upside down.

### 2.1 Electrical Interface <a href="#e8e54" id="e8e54"></a>

#### 2.1.1 Electrical Panel Introduction <a href="#mt4wn" id="mt4wn"></a>

The robotic arm base panel is equipped with an aviation connector, a standard Ethernet port, a WIFI antenna, and status indicator lights. The aviation connector contains two sets of lines: one for power supply to the robotic arm and one for CAN communication between the upper system and the robotic arm.

Electrical Panel Status Light Indication

<img src="../../.gitbook/assets/电器面板 (2).png" alt="电器面板.png" width="764.3636363636364">

<img src="../../.gitbook/assets/image (1173).png" alt="image.png" width="680.48828125">

> **Note**: Align the red dot on the base panel with the red dot on the cable. The textured part of the aviation connector is a retractable area under force. For insertion, align the red dots and insert directly. For pulling out, press the textured part and pull out.

#### 2.1.2 End-Effector Connection Description <a href="#g9qjn" id="g9qjn"></a>

The end joint reserves an XT30 2+2 interface, with power and CAN definitions shown in the figure below. The voltage is 24V, with a maximum current of 2A. The end-effector CAN communication only supports AgileX's own devices. Unauthorized connection of other CAN devices is strictly prohibited, as it may cause uncontrollable damage.

<img src="../../.gitbook/assets/NERO User Manual image 6 (2)" alt="NERO User Manual image 6" width="292">

### 2.2 Robotic Arm Workspace and Payload <a href="#cgwnl" id="cgwnl"></a>

This chapter clearly defines the motion space boundaries and joint movement ranges of the robotic arm through kinematic diagrams, providing a basis for users to design workstation layouts, plan trajectories, and implement safety protection measures.

<img src="../../.gitbook/assets/image (1174).png" alt="image.png" width="1074">

<img src="../../.gitbook/assets/image (1175).png" alt="image.png" width="964">

### 2.3 Mechanical Installation Instructions <a href="#guu5a" id="guu5a"></a>

#### 2.3.1 Base Mounting Instructions <a href="#dwawn" id="dwawn"></a>

The robotic arm base is fixed with screws. The base has 4 pre-reserved M5 threaded through holes, and 4 M5 screws are included in the accessory package. The included hexagon tool can be used for installation. The hole spacing is 70mm. If you are designing an adapter structure for mobile equipment or fixed platforms, you can make the hole positions with a 70mm spacing.

\
Base Mounting Diagram

#### 2.3.2 End-Effector Installation Instructions <a href="#wp2ga" id="wp2ga"></a>

**Dexterous Hand Installation**

1. Secure the robotic arm to the installation platform. Take out the dexterous hand, flange accessories, including the flange and accessory bolts.
2. Install the flange plate as shown in the diagram:
3. Use 6 M3×6 hexagon socket countersunk head bolts to mount the baffle to the motor output shaft.
4. Use 4 M3×8 hexagon socket countersunk head bolts to fix the flange on both sides of the baffle.
5. Insert the dexterous hand into the flange plate (ensure the cable outlet is aligned with the gap in the flange plate).

<img src="../../.gitbook/assets/灵巧手安装 (2).png" alt="灵巧手安装.png" width="698.5454711914062">

d. Install four M3×6 screws to mount the dexterous hand onto the flange.

<img src="../../.gitbook/assets/安装手 (2).png" alt="安装手.png" width="669.8181818181819">

<br>

3. After installing the dexterous hand, connect the power and communication cable from the accessory package to the J6 end interface and the interface on the gripper teach pendant.
4. Connect the aviation cable to the robotic arm. Connect the USB-to-CAN module to the aviation cable by matching CAN-H to yellow and CAN-L to blue. Plug the USB cable of the USB-to-CAN module into the computer. Connect the aviation cable to the adapter and power on the adapter.

<br>

#### 2.3.3 Installation Instructions on Desktop <a href="#bemxi" id="bemxi"></a>

The desktop installation module is an optional accessory and is not included with the standard product. Dimensions are shown in the figure below. Ensure the module is securely fixed before using the robotic arm.

<img src="../../.gitbook/assets/NERO User Manual image 12 (2)" alt="NERO User Manual image 12" width="1213">

## 3 Robotic Arm Operation <a href="#vkpyt" id="vkpyt"></a>

#### 3.1 CAN cable connection <a href="#wgh5f" id="wgh5f"></a>

Find the CAN cable from the aviation connector. Connect CAN\_H and CAN\_L in the CAN cable to the CAN\_TO\_USB adapter, respectively. Connect the CAN\_TO\_USB adapter to the USB port of the laptop. Refer to the connection diagram for details.

<img src="../../.gitbook/assets/NERO User Manual image 13 (2)" alt="NERO User Manual image 13" width="552">

**Note**: If a non-standard charger is used, the input power supply must not exceed 26V, and the current must be at least 10A.

#### 3.2 Power-On Instructions <a href="#kkruz" id="kkruz"></a>

Follow the steps below for the first power-on of the robotic arm:

1. Connect the CAN cable of the aviation connector to the CAN\_H and CAN\_L terminals of device B, respectively.
2. Align and insert the XT30 foolproof connector of device C.
3. Align the red dot of the aviation connector D with the red dot of the aviation socket on the arm base and insert it.
4. Plug the adapter E into the mains power supply.
5. Check and confirm that the AC plug F of adapter E is properly connected and powered on. Wait until the indicator light on the electrical panel of the robotic arm base flashes green.
6. Insert the USB cable G into the computer to start using the robotic arm.

**Note**: Align the red dot with the red dot on the cable below. The textured part of the aviation connector is a retractable area under force.

<img src="../../.gitbook/assets/7轴 (2).png" alt="7轴.png" width="3055">

<br>

#### 3.3 DH for robotic arm <a href="#hyhqd" id="hyhqd"></a>

| joint | aᵢ₋₁(m) | αᵢ₋₁(°) | dᵢ (m)  | θᵢ offset (°) |
| ----- | ------- | ------- | ------- | ------------- |
| j1    | 0       | 0       | 0.138   | 0             |
| j2    | 0       | 90      | 0       | 180           |
| j3    | 0       | 90      | 0.31    | 180           |
| j4    | 0       | 90      | 0       | 180           |
| j5    | 0       | 90      | 0.27001 | 90            |
| j6    | 0       | 90      | 0       | 90            |
| j7    | 0       | 90      | 0.0235  | 0             |

## 4 Robotic Arm Connection <a href="#rqecy" id="rqecy"></a>

### 4.1 WIFI connection <a href="#wc5sc" id="wc5sc"></a>

WIFI name：agx-7ax-xx WIFI password：12345678

Backend IP Address for Login : [http://192.168.31.1/](http://192.168.31.1/)，

Web Login Username: admin Web Login Password: 123456

### &#x20;<a href="#ffsaj" id="ffsaj"></a>

### 4.2 Ethernet Connection <a href="#ia38d" id="ia38d"></a>

Connect the controller to the computer via an Ethernet cable. Connect one end of the cable to the controller's network interface and the other end to the computer's or local area network's network interface. If the connection is successful, the Ethernet port indicator light will flash frequently. The default IP address of the robotic arm controller is 10.90.0.150. For communication with the robotic arm, the IP addresses of all computers must be in the same network segment as the robotic arm controller.

## 5 Web-Based Host Computer Introduction <a href="#wddhs" id="wddhs"></a>

### 5.1 Page Introduction <a href="#fit2d" id="fit2d"></a>

### &#x20;<a href="#f1zmr" id="f1zmr"></a>

#### 5.1.1 System Usage Rate <a href="#wws92" id="wws92"></a>

The robotic arm has a built-in control board. The system usage rate displays the disk, CPU, and memory usage of the main board. This control board is not open to users.

<img src="../../.gitbook/assets/image (1179).png" alt="image.png" width="767.7777981169435">

#### 5.1.2 Robotic Arm Status <a href="#gbndg" id="gbndg"></a>

Displays the status of each joint motor of the robotic arm.

### &#x20;<a href="#z7gt8" id="z7gt8"></a>

#### 5.1.3 Top Function Button Description <a href="#pjqyc" id="pjqyc"></a>

| **Function Button**    | **Function Button**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | **Function Button**                                                 |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Robotic Arm Speed      | <img src="../../.gitbook/assets/image (1181).png" alt="image.png" data-size="original">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Adjust the movement speed of the robotic arm by dragging the button |
| Emergency Stop         | <img src="../../.gitbook/assets/image (1182).png" alt="image.png" data-size="original">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Stop the movement of the robotic arm immediately                    |
| Web Mode               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Switch to web control mode                                          |
| Clear Error            | <img src="../../.gitbook/assets/image (1183).png" alt="image.png" data-size="original">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Clear error information of robotic arm joints                       |
| Enable                 | <img src="../../.gitbook/assets/image (1184).png" alt="image.png" data-size="original">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Enable individual robotic arm joints or all joints                  |
| Restart System         | <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB0AAAAkCAYAAAB15jFqAAACNklEQVRYCe2WO08CQRDH/TwkWlrYGAoaY2gkxNaEBgsLKxso7YwJoTAhIbEgWlBBQmNCjJ0aobGwUQTlqSAcx/M4xszCLXCZvQOioblNLrc7O//53cw+YA1W0NZWwAQL+q9Vt8prlfdPKmBtJNMyZmw2wGeZtlR5O/f3DIhQ7GtNlSSta/g2h6oqDKpV6L+9gVKpsGAUVMlm2YcU3G5Qm83FoXIiAR8OB2Q3N3lGLKuHByG09/zMfSsnJ4tDUdF5fITc1hYPhNDWzY0QihM/Fxfcv3F5KQQblrd4cADv4w2DUCkaNYTiZPnwkIMH4+XQ04XQ9u0tEyMUS43QRjhsCu2m0xyKMagmhNbOzrgYA335/VA7PzeFDns9yGxsMG0tGKSY4n8O3z4fE37u7nLhTyDA+5g5PlQruFxsDktNNWGmJa93BN3ZoXSGNm05vv1+0k8I1TLNrK/DUFFIMWVUGw32sWwPRCKUi7i8cizGxf3XV1JMGbupFNd1np4oFzEUbyBt3erjXUtG0Bmrp6dMl7PbQW21dLOjobC8OF0+PuZgUq0zKsUi96+HQrrZydAQqtbrgGuKGRf290F02DEcHg+tMnmnU5gl+hpC0UGOx3kwDIrBpasraCWTgHc0nt2SxzPjI11fT9IieqZQ1Ez/qmjZUO/83h607+4IzKxpLihKBqUSlI+O+JWoQT+2t5lddPvM4kajuaHTYlWWoffyAv1cbto8d38p6NzRBY4WVFCYvzGvpLy/L0piAzJyZt0AAAAASUVORK5CYII=" alt="image.png" data-size="original"> | Restart the entire web operating system                             |
| Search                 | <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACMAAAAjCAYAAAAe2bNZAAABzElEQVRYCe2Wv8tBYRTH/TUUgwxkFIMBu8FgsBgMophNdMugmFmUDFYTg4nCqEwGg1JKfm2+OmcQdZ/7PPe972B4nrp17znnOefT9znn6brwQ8v1QyzQMKLT0MpoZUQKiOy6Z7QyIgVEdls9cz6f0el0kMlk+MnlchiPx3g+n6L8tuzKMKPRCH6/Hz6fD+l0mmGSySTcbjdSqRT2+72twmbBSjDT6ZSLFotFnE6nrzzL5RKRSATRaBT3+/3LZ/dDCkMFwuEwqtWqMPfxeEQoFEKj0RDGqDikMP1+n4/ner1a5uv1ehz3eDws46ycUphKpYJsNmuVg3273Y6PcrVaSWNFAVKYcrmMfD4v2v+2Xy4XhpnNZm+b3RcpTLPZRCwWk+ZdLBYM42SqpDCbzYaLTCYTS6BCoYB4PO7ozpHCEEGpVEIwGMR2uzUFoouP7hu6ApwsJRiapEQiAa/XC8MwsF6vQVNDcHSMHo+HYdrtthMW9R9yatB6vY5AIMCFSQl6qJ9ImW63y9804n9dSsp8Jr/dbpjP56ARPhwOXz3SarUYaDgcfm5RfrcNI8tcq9UwGAxkYab+f4cxraJo1DAiobQyWhmRAiK77hmRMi8imY+52D5ZtQAAAABJRU5ErkJggg==" alt="image.png" data-size="original">                                                                                                                                             | Search function                                                     |
| Switch Chinese/English | <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB8AAAAoCAYAAAAG0SEsAAAByElEQVRYCe2Uy0tCQRTG/VOjRdHCFhGiSe2KrLCSFHr5oKCSHuKrdvlalKmoGGYLA8M2trilLmxz4kzMcBnlPpzwbu7AcM98d875zfm4dyxg4LAYyAYTboj7pu2m7RN1wPzgJmo3hem2XZIkmiv81A2fmp6Bm0hUGIwFFOHrri3gJ8J5DdflclX3gRTh/kBoJIjC5Qep11/+Fy6vhsV7vR6TAsETQHir9c40vYFi5/JiCFpdcxGp3+8T8I5nT75Fd6wZfnUdIcD7VAbOzsMkrtWeGfDg0A849QzN8MHgB6zzC2SiC0fHQcZpNF7JYVBvNt+YrhZohmOhTDbHIJ3OJ6sdDJ0y/SJ8yXS1QBfc7lhmENo5foSzc1bY2HSDw7kCizaHGpO91wT/7nbB69sn4ETyjlwyaDFeNrF4kuiFYgmisQSJHx7zDKAUqMLzTwWwL/11nEpnWa10Jgft9gfpFjvGXxEnHsq97WH7lAJVOF4oNrsTisXSUJ1KpUpgCOSnJH0N7ecFVTifIF/verwESrumTzxIPHEr3zoyFoIjBK9gftBrmdf5tRAcOxUZQnARMOaacFEHx8o3bR/LNtEk03ZRB8fKN9T2X1lcvUQOQoJEAAAAAElFTkSuQmCC" alt="image.png" data-size="original">                                                                                                                                                     | Switch the language of the web interface                            |
| Full Screen            | <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACMAAAAmCAYAAABOFCLqAAAAw0lEQVRYCe2VwQnAIAxFu4xDOYK6nK7gLq7g1ZLC7yEiiHhQ+IcQElPzfU3rU2ttp9hzihDRQTGjt0EyJDMiMMpzZkhmRGCUv39mnHPNGPNbSqm7bGOM/7rUeu+7Gk1oiUwIoVlrW875s1JK10hyWJdaeUY31/GSGCEzc1I0m62/XwxOvNsvkdktAvtRDEhov0Rm9utAs9n6+8Uc99M75jrALOz2SzOzWwT2oxiQ0J5kNBHEJAMS2pOMJoKYZEBC+6PIvNuC0vCTtkweAAAAAElFTkSuQmCC" alt="image.png" data-size="original">                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Set the web page to full-screen display                             |
| Notification           | <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACQAAAAoCAYAAACWwljjAAABXElEQVRYCe1Uz0sCURD2T40QiRXpUgevEai0pdRBSuiQeFYM+mGm0UnMm4Xd2tCL/Qt7mPge7oIrj3m7bw97mIFh5833vZ2Pb0dzlLHIZUwPiSDui4hD4hDnAIfLDolDnAMcnniHfN+nk9OKStRpRSJBnvdL/fsH2tsvqESNXhoRW9BwOKJ8waGz8wa5m0SNHjDbiCVo/vmlHJl+zHbmogfHwLEJY0HL5YoOnBL9eJ52HjBwwE0axoImkynVG1fsHHCeBy8sT0cwFvT4NKC7dkf3nrAPTvO6FZ7jFsaCur0+IbkAp1pzOZoWF0FaazaAOGTtEP7wsKiVmqsSCxvUeEbP6B0dl9Wd19GYm7+Ds59s/PauhmKIUzw0Tgg1+VVGFbGCoheC83r9R4vFd5hB3/aZWBAG37Ru6aJ+aath676VoK03pXQQQZyR4pA4xDnA4bJD4hDnAIdnbof+Af6S/nP8IOWQAAAAAElFTkSuQmCC" alt="image.png" data-size="original">                                                                                                                                                                                                                                                                                                     | Notification function                                               |
| Web Settings           | <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAjCAYAAACD1LrRAAAB4ElEQVRYCe2Wz6pBURTG78uQGVH+jAxIPIKJJEoiJgZ4C8pMmZAxmXkKQjJhgomJf9Pv9u06u9O+R4fudtPNYOXsdXb7t9a3z1rL1+12wyvser1CtcvlAtr5fMbXK6A88x70f4LVbLk2y/wyqd8GbGRr3O+fZfwBf6TW1jrVcnqbj+t0Oj3fq3u9HrLZLPL5PPr9vqVKdhk/DT4ej/D7/YhEIsKCwSDoUweNFvBut0Oj0cBkMkE6nYbH48F2u8Vms4Hb7UYmkxHvuGe/34sgtIBTqRQcDoeAlEolrFYrmeF8Pgd9DIB7GNgjI9FWakJ44GAwkDBVVmPN++be9XptO4ttwdPpFF6vF/V6XYKHwyFisZgwPhvgWq0Gn8+H2Wz2ezAPbTabCIVCEkBopVIREsfjcekntN1ui7WWO261WuDXa2RGGMHFYhFmcCAQ0Ae+J3U0GkUikcBoNJIBVatVfVIvl0s4nU6Mx2MJMDJXf3nfLpdLlJkWqZmJUU7lchmLxUIGwXIqFAqynFjLDEgL+HA4iAbCjNgq1QaSy+WE5IQaXUwL2CwpB3g4HJYtk62TEPMebRmrh3Y6HSSTSWHdbvcH9GVgNRCrtXaprSBWvg9Y/etjOySsZHzE95H6raT+BszpQ/D+qzixAAAAAElFTkSuQmCC" alt="image.png" data-size="original">                                                                                                                     | Customize the interface according to personal preference            |

## 6 User Control Area <a href="#gu7uu" id="gu7uu"></a>

### 6.1 Motion Control <a href="#mffqi" id="mffqi"></a>

| **Motion Mode** | **Motion Mode**                                                                                                                                                                                                                                                                                                                   | **Note**                                                                                                                                                                                                                                                                                                                  |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Point           | Enter the end-effector position (x, y, z, rx, ry, rz) and click Apply. The robotic arm will move to the specified position. Alternatively, click the x, y, and z icons to increase or decrease the coordinate values, modify the end-effector coordinates, and click **Apply to move the robotic arm to the specified position.** | The entered position may be unreachable. In this case, the robotic arm will not move, and an error prompt will appear.                                                                                                                                                                                                    |
| Circle          | <p>Enter three positions: start point (x, y, z, rx, ry, rz), midpoint (x, y, z, rx, ry, rz), and end point (x, y, z, rx, ry, rz). The robotic arm will plan and execute circular motion based on these three points.</p><p>​<br></p>                                                                                              | The entered positions or positions in the planned circular trajectory may be unreachable. In this case, the robotic arm will not move, and an error prompt will appear.                                                                                                                                                   |
| Joint           | Enter the joint angle of each joint and click Apply. The robotic arm's underlying system will respond and execute the command. In addition, drag the slider to change the value. **Note that you still need to click "Apply" for the changes to take effect.**                                                                    | If the sent joint angle exceeds the joint limit, the robotic arm will not move. Commands must be issued within the joint limit range.                                                                                                                                                                                     |
| Line            | Enter the position and posture (x, y, z, rx, ry, rz) of the robotic arm. The robotic arm will move linearly to the specified position.                                                                                                                                                                                            | If there are unreachable positions between the entered point or within the planned linear trajectory, the motion state will have no solution.                                                                                                                                                                             |
| MIT             | Select the target joint number. Enter the robotic arm joint angle, speed, kp (position gain), kd (speed gain), and joint torque.                                                                                                                                                                                                  | This mode allows direct control of joint motor position, speed, and torque. Mixing control of joint position, speed, and torque can be achieved by adjusting relevant parameters (target speed, kp, kd, torque). This mode is relatively dangerous. Contact technical support to confirm relevant information before use. |

Note: If the prompt "Please configure the correct control mode" appears during web interface control, it indicates that the system is not in web control mode. Click the "WEB" button at the top of the interface to switch to web control mode.

### 6.2 Drag Teaching <a href="#ztlxj" id="ztlxj"></a>

Click to add a new teaching program, enter the teaching name, and confirm it. Then click Add in the operation panel — the robotic arm will then enter the gravity compensation mode, allowing you to manually drag the arm to move. After completing the recording, click Pause to end the process.

<img src="../../.gitbook/assets/image (1185).png" alt="image.png" width="390">

### 6.3 Dexterous hand <a href="#fddbu" id="fddbu"></a>

（Wa）

### 6.4 Coordinated control <a href="#i8jvi" id="i8jvi"></a>

The core function of this interface is to set and switch the operating modes of the operating modes of the robotic arm.

`normal`: This is the independent operating mode. When this mode is selected, the robotic arm（or the control unit）will not participate in any leader-follower coordination and will operate as an independent unit.

`leader`: This is the master control mode. Designate the currently controlled robotic arm as the "leader unit". In the leader-follower mode, the leader arm is responsible for leading the movement and is used to drive the 'follower arm'.

`follower`: This is the follower control mode. Designate the currently controlled robotic arm as the 'follower unit'. The follower arm will follow the motion commands of the leader arm in real time to achieve precise synchronous movement.

<img src="../../.gitbook/assets/image (1186).png" alt="image.png" width="548.8889034294791">

Note: When using the leader-follower arms, do not set both robotic arms to follower arm mode simultaneously, and do not enable CAN push at the same time when the two robotic arms are connected. Otherwise, it will cause abnormal external network CAN communication. If this happens, the device needs to be restarted.

### 6.5 Speed Regulation <a href="#bgcrw" id="bgcrw"></a>

In the speed adjustment interface, you can drag the progress bar to adjust the percentage of the overall speed of the robotic arm.

### 6.6 Trajectory

Trajectory Management is a core control interface that integrates the creation, management, execution, and storage of robotic arm motion trajectories. Through this interface, users can conveniently plan a continuous path composed of multiple "motion points", as well as save, retrieve, and batch-process the path.

​<br>

**Includes Buttons**：

* **`New Trajectory`:** Create a new blank trajectory.
* **`Refresh`**: Refresh the trajectory list below to obtain the latest data.
* **`Export`**: Export the selected trajectory file to the local device for backup or sharing.
* **`Import`**: Import existing trajectory files from the local device for quick loading and use.

<img src="../../.gitbook/assets/image (1187).png" alt="image.png" width="767.7777981169435">

### 6.7 Set Zero Position <a href="#auyaw" id="auyaw"></a>

After long-term operation of the robotic arm, the zero position of the arm may deviate due to various factors, such as mechanical wear. When the zero position of the robotic arm joints deviates, we need to recalibrate the zero position of the joints in the Zero Point Setting section of the control panel. This calibration is divided into two methods: manual zero point setting and automatic zero point setting.

#### 6.7.1 Auto Set Zero Position <a href="#aqj79" id="aqj79"></a>

For Auto Set Zero Point, you can select a specific joint, choose Auto Set, and click Confirm.

<img src="../../.gitbook/assets/image (1188).png" alt="image.png" width="768.888909257489">

#### 6.7.2 Manual Set Zero Position <a href="#nmifu" id="nmifu"></a>

For Manual Set Zero Point, you can select a specific joint, disable the joint, then rotate it manually to the zero position and click Confirm.

<img src="../../.gitbook/assets/image (1189).png" alt="image.png" width="765.5555758358526">

### 6.8 System Settings <a href="#e0zbr" id="e0zbr"></a>

#### 6.8.1 Joint Limit Settings <a href="#yht1m" id="yht1m"></a>

This interface allows users to precisely define **the motion range** and **maximum allowable speed** of each joint of the robotic arm according to practical application scenarios. This prevents the robotic arm from performing hazardous movements due to program errors, misoperations, or unexpected interference, which may result in equipment collision, overload, or damage. To reset the original settings, simply click Reset.

<img src="../../.gitbook/assets/image (1190).png" alt="image.png" width="768.888909257489">

#### 6.8.2 End Effector Speed Settings <a href="#til6j" id="til6j"></a>

**This is an advanced parameter setting interface for fine-tuning the motion performance of the robotic arm's end effector**. It allows users to set the upper limits of speed and acceleration for the movement of the end effector tool in accordance with specific process tasks and safety requirements.

<img src="../../.gitbook/assets/image (1191).png" alt="image.png" width="783.763916015625">

<img src="../../.gitbook/assets/image (1192).png" alt="image.png" width="613">

#### 6.8.3 Collision Protection Settings <a href="#mapdt" id="mapdt"></a>

This is a **collision safety sensitivity adjustment panel**, used to set the level of each robotic arm joint in response to collisions or abnormal resistance. When the robotic arm experiences an accidental collision or encounters excessive resistance, the system will detect the incident in a timely manner and trigger an emergency stop according to the preset level, thus protecting personnel safety and preventing equipment damage.

<img src="../../.gitbook/assets/image (1193).png" alt="image.png" width="747.7777975871245">

#### 6.8.4 Mounting Position Settings <a href="#q0xjw" id="q0xjw"></a>

This interface is used to set **the physical mounting posture of the robotic arm body**, which serves as a fundamental step for the robotic arm's coordinate system calibration. Its results directly affect the robotic arm's motion control logic and spatial coordinate calculation. Users can select vertical mounting, horizontal mounting, and inverted mounting according to actual application scenarios.

<img src="../../.gitbook/assets/image (1194).png" alt="image.png" width="744.444464165488">

#### 6.8.5 End Effector Configuration <a href="#rpdak" id="rpdak"></a>

This interface is used for parameter calibration of the robotic arm's end effector tool, which serves to precisely define the physical properties of the tool mounted on the end effector. This enables the robotic arm control system to accurately calculate the tool's parameters, such as mass, center of gravity, and dimensions, thereby achieving precise motion control and torque compensation

<img src="../../.gitbook/assets/image (1195).png" alt="image.png" width="744.444464165488">

## 7 Configuration <a href="#d7lwh" id="d7lwh"></a>

### 7.1 Ethernet Port Settings <a href="#osr14" id="osr14"></a>

This module provides users with the function of configuring core parameters for network connections. By manually setting the device's network protocol and other relevant parameters, it enables the device to achieve network identity identification, route addressing, and domain name resolution, ensuring that the device can access the target network normally and conduct data communication with other devices or servers in the network.

<img src="../../.gitbook/assets/image (1196).png" alt="image.png" width="768.888909257489">

After manually setting the ip address of the robotic arm, you can connect the robotic arm and the host computer via the Ethernet port. Ensuring that the host computer and the robotic arm are on the same network segment will enable successful communication between them.

### 7.2 Hotspot Settings <a href="#c3mor" id="c3mor"></a>

This interface is used to configure **the** **basic network parameters** for the robotic arm to act as a **Wi-Fi hotspot**, enabling other devices(mobile devices)to connect to it via Wi-Fi and realize wireless data transmission and control functions.

<img src="../../.gitbook/assets/image (1197).png" alt="image.png" width="768.888909257489">

<br>

## 8 Upgrade <a href="#li6zm" id="li6zm"></a>

### 8.1 Software Upgrade <a href="#einpj" id="einpj"></a>

This module provides the robotic arm with software version management and system upgrade capabilities, and supports functions including firmware version query, system update, and soft restart.

<img src="../../.gitbook/assets/image (1198).png" alt="image.png" width="768.888909257489">

### 8.2 Firmware Upgrade <a href="#abh87" id="abh87"></a>

This module provides a firmware upgrade function for the robotic arm's joint modules. It also supports features including joint information monitoring and joint hardware version query, which ensures the reliability of the firmware upgrade process and system compatibility of the joint modules.

\
**Note**: **When upgrading the firmware, you must first click the Upgrade Mode button to enter the upgrade mode, then perform the joint firmware upgrade. The robotic arm will be disabled during the upgrade. Ensure the robotic arm is placed in a safe posture. After the firmware upgrade of all joint modules is completed, you must click the Exit Upgrade button. Otherwise, the robotic arm will be unavailable for use.**

<img src="../../.gitbook/assets/image (1199).png" alt="image.png" width="767.7777981169435">

## 9 Secondary Development <a href="#m3qcd" id="m3qcd"></a>

You need to get a Python-based API interface for the secondary development of the robotic arm currently provided. Only links are provided here; for detailed secondary development of the robotic arm, please refer to the GitHub link.

Before using the sdk, please go to the web page and enable the CAN publishing.

<img src="../../.gitbook/assets/image (1200).png" alt="image.png" width="1727.2726898351">

| Content               | Address                                                                                  |
| --------------------- | ---------------------------------------------------------------------------------------- |
| SDK API Documentation | [https://github.com/agilexrobotics/pyAgxArm](https://github.com/agilexrobotics/pyAgxArm) |

## 10 Robotic Arm CAN Protocol <a href="#egpj6" id="egpj6"></a>

The robotic arm provides a CAN interface for users'development, and users can perform command control on the robotic arm via this interface.

The CAN communication standard adopted by the robotic arm is CAN 2.0B, with a communication baud rate of 1000k and the message format following the MOTOROLA(MSB) format.

If you need to develop with CAN commands, please contact AgileX Robotics Support Tea to obtain the CAN Protocol Manual.

## 11 Maintenance and Servicing <a href="#djrl0" id="djrl0"></a>

To ensure the robotic arm maintains high performance for an extended period, regular maintenance must be performed. All maintenance and servicing operations must strictly comply with all instructions specified in this manual. The purpose of maintenance and servicing is to ensure the normal operation of the robotic arm and its accessories.

### 11.1 Storage Notes <a href="#jwysf" id="jwysf"></a>

After use, perform a zero position calibration before powering off and storing the robotic arm. Tidy up and organize all wire harnesses to avoid entanglement or excessive pulling.

Operating and Storage Environmental Requirements: Temperature:-20 to 50 ℃, Humidity:25% to 85% non-condensing.

### 11.2 Servicing Notes <a href="#gb3xn" id="gb3xn"></a>

Maintenance and servicing must be performed when the robotic arm is in a zero-reset and power-off state. After powering-off, perform the following operations:

> **Note：**\
> **Robotic Arm Cleaning**: Use wet wipes or dry rags dampened with water to remove dust, dirt, and oil stains from the robotic arm.
>
> **Motor Inspection**: Check for damage or deformation of the motor and its structural components.
>
> **Cable Inspection**: Check for the security of power cables and CAN cables, and any damage to their outer sheaths.

### 11.3 Emergency Handling <a href="#g4akm" id="g4akm"></a>

In case of an emergency, you can unplug the aviation connector directly to cut off the power supply. Note that the robotic arm will be deactivated and drop directly after power-off. Take extreme care to prevent damage to the robotic arm, as well as harm to the surrounding environment and personnel. Power off by unplugging the connector is an emergency response measure only, and is not intended to prevent injury.

## Appendix: Dimension Drawings <a href="#f42f0" id="f42f0"></a>

### 1 Robotic Arm Dimensions <a href="#hltmk" id="hltmk"></a>

<img src="../../.gitbook/assets/资源 7 (2).png" alt="资源 7.png" width="9612">

### 2 Robotic Arm with Dexterous Hand <a href="#iw9im" id="iw9im"></a>

<div><img src="../../.gitbook/assets/image (1201).png" alt="image.png" width="277"> <img src="../../.gitbook/assets/image (1202).png" alt="image.png" width="235.25"></div>

### 3 Base <a href="#wdxps" id="wdxps"></a>

### 4 Dexterous Hand Diagram <a href="#kyqfk" id="kyqfk"></a>

<img src="../../.gitbook/assets/image (1204).png" alt="image.png" width="1256.2499812804165">

<br>

### 5 Dexterous Hand Flange Mounting Diagram <a href="#wif9z" id="wif9z"></a>

<img src="../../.gitbook/assets/image (1205).png" alt="image.png" width="952">



### Development Resources

* [pyAgxArm Python SDK](https://github.com/agilexrobotics/pyAgxArm) — official CAN communication, status, motion-control, and end-effector SDK for NERO.
* [AgileX arm ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/ros2) — use `arm_type:=nero`.
* [NERO URDF, Xacro, and mesh resources](https://github.com/agilexrobotics/agx_arm_urdf) — official `nero` model directory.
* [NERO firmware compatibility reference](https://github.com/agilexrobotics/pyAgxArm/blob/master/docs/nero/firmware_reference.md) — select the SDK driver from the firmware reported by `get_firmware()`; this is a compatibility matrix, not a firmware binary download.
