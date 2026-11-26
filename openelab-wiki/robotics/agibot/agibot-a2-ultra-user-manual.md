# AgiBot A2 Ultra User Manual

### AgiBot A2 Ultra Humanoid Robot for Embodied AI

{% embed url="https://openelab.io/products/agibot-a2-ultra-humanoid-robot" %}

### Contents

Safety; product identification; unboxing; transfer-cart operation; battery replacement and charging; startup, remote control, emergency stop, and wireless microphone; Aim-Master remote control, mapping, tasks, workbench, settings, and notifications; current system architecture; secondary development; simulation; interface troubleshooting; and frequently asked questions

### Key Troubleshooting Index

* Safety and emergency handling
* Unboxing and transfer-cart setup
* Power, charging, startup, remote control, and shutdown
* Aim-Master maps, tasks, settings, and notifications
* Developer-interface troubleshooting
* Frequently asked questions

### Chapter 1: Safety Guidelines <a href="#chapter-1-safety-guidelines" id="chapter-1-safety-guidelines"></a>

#### 1.1 Safety Precautions <a href="#id-1-1-safety-precautions" id="id-1-1-safety-precautions"></a>

1\. Understand the Product: Before using the robot, carefully read the user manual

to understand its functions, operating procedures, and safety precautions. Only trained and qualified personnel are permitted to operate the robot.

2\. Follow Usage Requirements:Ensure the robot operates on even and stable

surfaces. Avoid environments with excessively high or low temperatures, high humidity, steep slopes, surfaces with significant height differences, fragile materials, or areas with strong vibrations.

3\. Operating Space: Provide sufficient operating space for the robot. Avoid using it

in narrow or crowded areas to minimize the risk of collisions and pinching.

4\. Emergency Stop Button: All robots are equipped with an emergency stop device.

Users must be familiar with the location and operation of the emergency stop button to halt the robot immediately in case of an emergency. Note: After activation, the robot’s joints will enter a damping collapse mode. Do not use the emergency stop in non-emergency situations or when the robot is not wearing protective equipment.

5\. Power Safety: Before operation, ensure all cables, plugs, and sockets are intact.

Immediately disconnect the power in case of abnormalities such as short circuits or overheating.

6\. Regular Inspection: Perform regular maintenance and inspections to ensure all

components-such as joints, sensors, and power systems-are functioning properly.

Avoid hazards caused by aging or damaged parts.

7\. Prevent Misuse: Ensure the robot is not used in any improper, hazardous, or

legally prohibited scenarios.

8\. Remote Controller Usage: Keep the remote controller accessible at all times

during operation.

Note: This robot is designed for indoor use and storage only to reduce the risk of fire,

electric shock, or injury.

#### 1.2 Safety Guidelines <a href="#id-1-2-safety-guidelines" id="id-1-2-safety-guidelines"></a>

**1.2.1 Pre-Startup Verification**

1\. Check battery level: Ensure the battery is sufficiently charged to complete the

intended tasks.

2\. Inspect the work area: Confirm that the work area is clear of personnel and

obstacles, paying special attention to the vicinity of the robot’s moving parts.

3\. Examine robot components: Verify that all parts of the robot are intact and free

from damage or abnormalities.

4\. Test the emergency stop button: Ensure the emergency stop button functions

correctly.

5\. Confirm system status: The operator must verify that the robot’s system status is

normal and that self-test procedures have been completed.

**1.2.2 Safety Distance**

Secure Operating Area: The robot’s operating area must be isolated with physical barriers. Unauthorized personnel are strictly prohibited from entering the operating zone to prevent accidental intrusion.

Maintain Safe Distance: During high-speed operations, do not stand near the robot’s movement path (maintain a distance of ≥1.5-2 meters).

Note: While the robot is in operation, the operator is responsible for ensuring that no

person enters the operating area.

**1.2.3 Payload and Operation**

1\. Strictly adhere to the robot’s designed payload limit. Overloading may cause

damage to the robot or result in unsafe conditions.

2\. When using the robot’s end-effectors, grippers, or other components, ensure they

are suitable for the object being manipulated to avoid generating unnecessary pressure or stress.

**1.2.4 Prohibition of Direct Intervention**

During robot operation, any form of direct physical intervention is strictly prohibited.

If adjustment or manual intervention is required, it must only be performed after the robot has come to a complete stop and has been powered off.

**1.2.5 Emergency Stop Measures**

In case of an emergency or robot malfunction, press the emergency stop button immediately. After the power is disconnected, inspect the equipment and the surrounding environment.

Note: Activating the emergency stop will cause the robot’s joints to enter

a damped collapse state. This function should be used only in genuine emergencies, and the robot must be properly supported to ensure safety.

**1.2.6 Prevention of Improper Operation**

Ensure all operators have received comprehensive training in robot operation.

They must understand correct operating procedures and emergency response protocols to prevent accidents caused by improper handling.

**1.2.7 Remote Operation Safety**

1\. If remote operation features are enabled during robot development, ensure the use

of a secure network environment to prevent control malfunctions caused by network failures or external intrusion.

2\. During remote control, the operator must have real-time monitoring equipment to

maintain full awareness of the robot and its surroundings.

3\. Operating the robot without direct visual contact is prohibited. Remote operation

requires the operator to maintain visible contact with the robot at all times.

**1.2.8 Malfunction Reporting**

In the event of any robot malfunction, immediately report the issue for repair to ensure prompt maintenance and safe operation.

**1.2.9 Safety Guidelines for Transferring the Robot**

1\. Always power off the robot before transferring it. Avoid direct contact with lasers

and other sensors, as this may affect their performance.。

2\. When transporting the robot by vehicle, use packing straps, boxes, wooden

planks, foam, or other protective materials to package and safeguard it against unnecessary damage.

Note: There is a risk of crushing the robot's body. Protective equipment must be used

during transfer.

#### 1.3 Privacy Policy <a href="#id-1-3-privacy-policy" id="id-1-3-privacy-policy"></a>

**1.3.1 Scope of Data Collection**

The robot's camera temporarily captures image data only within its necessary field of view when performing functions such as environmental perception and obstacle recognition. This data is used for real-time operational decisions, including obstacle avoidance and path planning.

**1.3.2 Information Protection Measures**

1\. Transmitted image data will be desensitized using techniques such as pixelation to

remove personally identifiable information (PII) or specific scenario details.

2\. Data is used solely for real-time computational purposes, is immediately purged

after processing, and is stored neither locally nor in the cloud.

#### 1.4 Maintenance and Management Guidelines <a href="#id-1-4-maintenance-and-management-guidelines" id="id-1-4-maintenance-and-management-guidelines"></a>

**1.4.1 Safety Warnings**

1\. Power-off Maintenance: Before performing any maintenance or replacing

components, the robot must be completely powered off to ensure it is in a safe power- off state.

2\. No Unauthorized Modifications: Unauthorized modifications to the robot or

changes to its original design and configuration are strictly prohibited.

3\. Professional Repairs: Users are not allowed to disassemble the robot themselves.

If repair is needed, contact manufacturer-certified professional technicians.

**1.4.2 Maintenance and Service**

1\. Regular Maintenance: Perform routine maintenance in accordance with the

manufacturer's (Agibot) recommendations to ensure the robot remains in optimal working condition.

2\. Use of Genuine Parts: Only use genuine replacement parts specified by the

manufacturer to guarantee device performance and safety.

**1.4.3 Malfunction Handling**

1\. Malfunction Response: In the event of a malfunction during robot operation,

immediately cease operation and notify professional technical personnel for inspection and repair.

2\. Unauthorized Repair Prohibited: Unauthorized disassembly or attempted

repair is strictly prohibited to prevent further damage.

**1.4.4 Battery and Power Management**

1\. Safe Charging: Do not remove the battery for charging; it must be connected to a

power source for charging

2\. Charging Environment: The robot uses a battery and must be charged in a safe, dry

environment. Avoid humid or high-temperature conditions.

3\. Avoid Overcharging: Prevent prolonged connection to the power source to avoid

overcharging or overheating, which helps extend battery life.

4\. Battery Replacement: Batteries should only be replaced by authorized personnel.

Using a charger designed for one battery type with another may pose a fire risk.

5\. Use Only the Provided Detachable Power Unit: Charge only using the detachable

power unit UY600L-W546080 provided with the device.

6\. Bat tery Disposal: Remove the battery and dispose of it safely before discarding

the device.

**1.4.5 Software Management**

Regular Updates: Regularly check and update the robot's operating system and control software to ensure vulnerabilities are patched and security is enhanced.

Note: Following these instructions ensures the robot operates safely and efficiently.

For any questions, please contact the manufacturer or authorized service provider for support.

Chapter 2：Product Introduction

#### 2.1 Product Model <a href="#id-2-1-product-model" id="id-2-1-product-model"></a>

Chinese English Brand Model Number A2 A2

#### 2.2 Product composition <a href="#id-2-2-product-composition" id="id-2-2-product-composition"></a>

#### 2.3 Basic Parameters <a href="#id-2-3-basic-parameters" id="id-2-3-basic-parameters"></a>

Level 1 Category Level 2 Category Entry Specific Content Basic Product Information Height 169cm Dimensions 169(H)\*75(W)\*30(L)cm Net Weight ≈69kg Active Degrees of Freedom Arms 7×2 DoF, Legs 6×2 DoF, Head 2 DoF, Dexterous Hands 6×2 DoF Electrical Performance Endurance Endurance under force-controlled standing with voice broadcast: approx. 3h Runtime during straight-leg walking on flat ground: approx. 1.5h Battery Capacity 14.4Ah Charging Time 2h Charging Power ≤500W

<figure><img src="../../.gitbook/assets/unknown (148).webp" alt="2.3 Basic Parameters - official illustration 11"><figcaption><p>2.3 Basic Parameters - official illustration 11</p></figcaption></figure>

Product Features Charging Voltage 48V DC Environmental Adaptability Operating Temperature & Humidity 0°C to 40°C, 10% to 90% relative humidity (non-condensing) Storage Temperature & Humidity -20°C to 70°C, 10% to 90% relative humidity (non-condensing) IP Rating Joint Module: IP5X Site Adaptability Minimum Passable Width Minimum Passable Width: >1m (current remote control mode), >2m (navigation mode) Maximum Obstacle Clearance Height 20mm Maximum Operating Slope 8% (4.57°) Safety Arm Collision Sensing Support Maximum Obstacle Avoidance Sensing Distance 5m Minimum Obstacle Avoidance Sensing Height 30cm Operation and Interaction Remote Control Operation Wireless Remote Controller Interactive Screen Interactive Face Screen with emotional expression display Overall module dimensions: 105.50 × 67.20 ×

#### 3.0 mm (including bezel) <a href="#id-3-0-mm-including-bezel" id="id-3-0-mm-including-bezel"></a>

Active display area: 95.04 × 53.86 mm Screen size: 4.3 inches Resolution: 800 × 480 pixels Brightness: 500 cd/m² Contrast ratio: 1500:1 (typical), 1000:1 (minimum) Microphone Microphone Array Speaker Dual 5W Speakers Indicator Light Multi-color Ambient Lighting Perception Capability Environmental Perception Sensing Suite: 1× LiDAR + 2× Fisheye Cameras + 2× RGBD Cameras + 1× RGB Camera Navigation Capability Positioning Accuracy ±10cm , ±10° Navigation & Obstacle Avoidance Real-time Autonomous Navigation & Obstacle Avoidance

Product Capability Mobility Capability Maximum Movement Speed 0.8m/s Movement Mode Supports omnidirectional translation, Left Turn, Right Turn IoT Capability Communication Protocol TCP、IP Communication Module WiFi、Mobile Network Arm Typical Parameters Dexterous Hand Delivery Capability Max Payload (Palm-Down): <3kg Max Payload (Palm-Up): <8kg Complete Unit (with Dexterous Hands) 2kg Maximum Arm Grabbing Weight 1m/s Arm Range of Motion J1(Shoulder pitch): ±170° J2(Shoulder roll): -30°\~95° J3(Shoulder yaw): ±170° J4(Elbow pitch): -1°\~118° J5(Wrist roll): ±170° J6(Wrist pitch): ±45° J7(Wrist yaw): ±30° Leg Typical Parameters Leg Range of Motion(with some deviation) J1(Hip roll):-37\~40° J2(Hip yaw): ±75° J3(Hip pitch): -50°\~110° J4(Knee pitch): -5°\~140° J5(Ankle pitch): -30°\~52° J6(Ankle roll): ±28° Head Typical Parameters Head Range of Motion Pitch Joint: ±23° Yaw Joint: ±45°

#### 2.4 Product Positioning <a href="#id-2-4-product-positioning" id="id-2-4-product-positioning"></a>

The Expedition A2 Upgraded Edition is AgiBot's general-purpose robot specifically designed for interactive services. It is suitable for roles including marketing and customer service, exhibition hall narration, retail guidance, front desk reception, and business consulting.

#### 2.5 Application Scenarios <a href="#id-2-5-application-scenarios" id="id-2-5-application-scenarios"></a>

Suitable for indoor flat environments such as exhibition halls, 4S dealerships, service halls, science museums, and research laboratories.

#### 2.6 Robot operating workspace <a href="#id-2-6-robot-operating-workspace" id="id-2-6-robot-operating-workspace"></a>

When using the robot,always maintain a sufficient safety distance.

<figure><img src="../../.gitbook/assets/unknown (149).webp" alt="2.6 Robot operating workspace - official illustration 14"><figcaption><p>2.6 Robot operating workspace - official illustration 14</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (150).webp" alt="2.6 Robot operating workspace - official illustration 15"><figcaption><p>2.6 Robot operating workspace - official illustration 15</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (151).webp" alt="2.6 Robot operating workspace - official illustration 15"><figcaption><p>2.6 Robot operating workspace - official illustration 15</p></figcaption></figure>

#### 2.7 Product Boundaries <a href="#id-2-7-product-boundaries" id="id-2-7-product-boundaries"></a>

**2.7.1 Voice Interaction**

1\. Supports Chinese and English interaction, but wake words are only supported in

Chinese.

2\. Highly network-dependent. To ensure interaction quality, upload/download speeds

must be ≥100Mbps.

3\. Voice interaction requires wake word activation. Average wake response delay is

1s; post-wake dialogue duration is 60s (resets with each interaction).

4\. Robot’s voice response delay is 2s.

5\. Speech recognition accuracy >95%.

6\. Supports personalized wake word customization.

7\. Built-in microphone interaction requires the user to stand 0.3m-1.5m directly in

front of the robot. For optimal performance, remain within ±45° of the chest camera’s field of view. If voice triggers robot movement, maintain a minimum safety distance of 1m.

8\. To ensure interaction quality, human voice must be ≥10dB above ambient noise. If

not satisfied, external microphone/speakers are recommended.

9\. External microphone interaction has no position restrictions but must be within

30m of the robot.

10.Voice interaction does not support stock/news queries but can recognize user

intent and provide voice responses.

11.Voice interaction is not supported overseas.

12.Voice interaction is not recommended during remote-controlled movement.

**2.7.2 Mobility Capabilities**

1\. Features anthropomorphic gait with straight-knee walking and natural arm

swinging.

2\. Supports movement on flat surfaces only. Unsuitable for surfaces with height

variations, mirrors, polished tiles, or long-pile carpets (>10mm).

3\. Capable of omnidirectional translation and left/right turning.

4\. Supports climbing slopes up to 5°, but does not support stationary slope stopping.

5\. Maximum movement speed: 0.8m/s (autonomous navigation speed: 0.5m/s).

Braking distance ≤50cm at maximum speed.

6\. Minimum turning radius: 800mm; minimum passable width: 1200mm (with

obstacle avoidance).

7\. Positional accuracy: ±30cm.

**2.7.3 Obstacle Avoidance Capability**

1\. Maximum obstacle detection range: 5m

2\. Forward safety distance: 1.5m

3\. Minimum detectable obstacle size: H>30cm, W>20cm

4\. Approximately 0.5m blind zone around the robot

5\. Cannot detect pure black, transparent, or mirrored objects

**2.7.4 Remote Operation Capability**

1\. Grip weight with palm facing down: < 3kg.

2\. Grip weight with palm facing up: < 8kg.

3\. The shape of the gripped object shall be a regular shape, and the hand-holding

size shall not exceed 8cm.

4\. Dual-hand obstacle avoidance is not supported; please exercise caution during

operation.

### Chapter 3: Product Unboxing <a href="#chapter-3-product-unboxing" id="chapter-3-product-unboxing"></a>

#### 3.1 Packaging <a href="#id-3-1-packaging" id="id-3-1-packaging"></a>

**3.1.1 Package Appearance**

The standard package of the Expedition A2 Upgraded Edition consists of two cases as shown in the figure below:

1\. The aviation case contains the robot body and related accessories.

2\. The cardboard box contains a transfer cart for assisting with robot positioning.

**3.1.2 Package Dimensions**

Package Length (cm) Width (cm) Height (cm) Weight (kg) Aviation Case (Robot) 185 85 65 130 Cardboard Box (Transfer Cart) 133 67 33 45

<figure><img src="../../.gitbook/assets/unknown (152).webp" alt="3.1.2 Package Dimensions - official illustration 19"><figcaption><p>3.1.2 Package Dimensions - official illustration 19</p></figcaption></figure>

#### 3.2 Transfer Cart Unboxing <a href="#id-3-2-transfer-cart-unboxing" id="id-3-2-transfer-cart-unboxing"></a>

<figure><img src="../../.gitbook/assets/unknown (153).webp" alt="3.2.1 Unboxing Procedure - official illustration 20"><figcaption><p>3.2.1 Unboxing Procedure - official illustration 20</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (154).webp" alt="3.2.1 Unboxing Procedure - official illustration 20"><figcaption><p>3.2.1 Unboxing Procedure - official illustration 20</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (155).webp" alt="3.2.1 Unboxing Procedure - official illustration 20"><figcaption><p>3.2.1 Unboxing Procedure - official illustration 20</p></figcaption></figure>

**3.2.1 Unboxing Procedure**

The transfer cart package contains the following components after unboxing: ： No. Component Name No. Component Name 1 Base Unit 5 Lifting Rope 2 Main Frame 6 Lifting Hook 3 Lifting Arm 7 Control Box 4 Manual & Handrail Cover 8 Electric Push Rod

**3.2.2 Transfer Cart Installation**

1\. Completed Assembly Reference

2\. Installation Steps

1\. Pay attention to the front and rear

direction of the main frame, insert the main frame into the base, and fasten it with hand-tightened bolts.

<figure><img src="../../.gitbook/assets/unknown (156).webp" alt="3.2.2 Transfer Cart Installation - official illustration 21"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 21</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (157).webp" alt="3.2.2 Transfer Cart Installation - official illustration 21"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 21</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (158).webp" alt="3.2.2 Transfer Cart Installation - official illustration 21"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 21</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (159).webp" alt="3.2.2 Transfer Cart Installation - official illustration 21"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 21</p></figcaption></figure>

2\. Connect the boom and the main

frame with hand-tightened bolts.

3\. Connect the electric push rod to

the main frame and the boom respectively using hand-tightened bolts.

4\. Pay attention to the direction of the

hook, and connect the boom and the hook with hand-tightened bolts.

5\. Connect the wire harnesses of the

electric push rod and the manual controller to the control box.

6\. Install the control box onto the

main frame: There are card slots on the back of the control box; align them with the clips on the main frame and slide down to install.

<figure><img src="../../.gitbook/assets/unknown (160).webp" alt="3.2.2 Transfer Cart Installation - official illustration 22"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 22</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (161).webp" alt="3.2.2 Transfer Cart Installation - official illustration 22"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 22</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (162).webp" alt="3.2.2 Transfer Cart Installation - official illustration 22"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 22</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (163).webp" alt="3.2.2 Transfer Cart Installation - official illustration 22"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 22</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (164).webp" alt="3.2.2 Transfer Cart Installation - official illustration 22"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 22</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (165).webp" alt="3.2.2 Transfer Cart Installation - official illustration 22"><figcaption><p>3.2.2 Transfer Cart Installation - official illustration 22</p></figcaption></figure>

7\. Hang the manual controller on the

handrail of the main frame, and organize the charging cable and the wire harness of the manual controller.

8\. Install the hanging rope and the

hook.

#### 3.3 Robot Unpacking <a href="#id-3-3-robot-unpacking" id="id-3-3-robot-unpacking"></a>

**3.3.1 Unpacking**

1\. There are two latches on each side

of the air case, totaling four latches.

<figure><img src="../../.gitbook/assets/unknown (166).webp" alt="3.3.1 Unpacking - official illustration 23"><figcaption><p>3.3.1 Unpacking - official illustration 23</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (167).webp" alt="3.3.1 Unpacking - official illustration 23"><figcaption><p>3.3.1 Unpacking - official illustration 23</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (168).webp" alt="3.3.1 Unpacking - official illustration 23"><figcaption><p>3.3.1 Unpacking - official illustration 23</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (169).webp" alt="3.3.1 Unpacking - official illustration 23"><figcaption><p>3.3.1 Unpacking - official illustration 23</p></figcaption></figure>

2\. Flip the latch tabs upward, then

rotate the tabs counterclockwise until the latches are fully raised.

2\. Pull outward to open the latches. 4. Two people stand at opposite ends

of the case, grip the handles, and lift upward to open the air case lid.

5\. After unpacking the robot, the package contents are as follows:

No. Component Name Qty.

① Robot Main Unit 1 ② Battery Charger 1 ③ Lapel Microphone 1 ④ Remote Controller 1 Emergency Stop Switch 1 Charger 1 ⑤ Battery 1

**3.3.2 Robot Removal Procedure**

It is recommended that 3 people operate to take out the robot, and at least 2 people are required. The following describes how to take out the robot when there are only 2 people.

Note： When adjusting the robot arm with external force, hold the upper limb shell of the robot; pulling the dexterous hand is strictly prohibited.

When lifting the robot's lower limbs, do not put your hands into the lower leg connecting rods to avoid crushing injuries.

Refer to the following method to take out the robot:

1.Insert the transfer cart into the

bottom of the robot packaging box from one end as shown in the diagram, and lower the boom to the position indicated in the diagram. Lock one wheel of the packaging box to avoid troubles caused

2.Two people stand on both sides of the

air case respectively, hold the robot's forearm at the position shown in the diagram and lift the arm to prevent the upper body from scraping the upper limbs when it sits up.

<figure><img src="../../.gitbook/assets/unknown (170).webp" alt="3.3.2 Robot Removal Procedure - official illustration 24"><figcaption><p>3.3.2 Robot Removal Procedure - official illustration 24</p></figcaption></figure>

by the box moving when taking out the robot.

3\. Each person holds one lifting ring

on the robot's shoulder, pulls the robot's upper body upward with force until the robot sits up. Note: Do not scratch the robot's head.

4\. One person holds the robot steadily,

<figure><img src="../../.gitbook/assets/unknown (171).webp" alt="3.3.2 Robot Removal Procedure - official illustration 25"><figcaption><p>3.3.2 Robot Removal Procedure - official illustration 25</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (172).webp" alt="3.3.2 Robot Removal Procedure - official illustration 25"><figcaption><p>3.3.2 Robot Removal Procedure - official illustration 25</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (173).webp" alt="3.3.2 Robot Removal Procedure - official illustration 25"><figcaption><p>3.3.2 Robot Removal Procedure - official illustration 25</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (174).webp" alt="3.3.2 Robot Removal Procedure - official illustration 25"><figcaption><p>3.3.2 Robot Removal Procedure - official illustration 25</p></figcaption></figure>

while the other ties two lifting ropes (one end tied to the lifting rings on the robot's shoulders, and the other end tied to the hook of the transfer cart).

5\. Release the robot's upper

body; note that the robot's arms must not be lowered. Operate the transfer cart to lift until the robot's hips are suspended, then lift the robot's legs- you may hold the outer shell of the robot's lower legs.

6\. Continue lifting until the robot

clears the top edge of the packaging case. Gradually move the transfer cart backward while maintaining stability. When sufficient clearance is achieved, gently lower the limbs and complete the robot extraction.

### Chapter 4: Product Operation <a href="#chapter-4-product-operation" id="chapter-4-product-operation"></a>

#### 4.1 Transfer Cart Usage <a href="#id-4-1-transfer-cart-usage" id="id-4-1-transfer-cart-usage"></a>

**4.1.1 Control Box Operations**

1\. Emergency Stop:

<figure><img src="../../.gitbook/assets/unknown (175).webp" alt="4.1.1 Control Box Operations - official illustration 26"><figcaption><p>4.1.1 Control Box Operations - official illustration 26</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (176).webp" alt="4.1.1 Control Box Operations - official illustration 26"><figcaption><p>4.1.1 Control Box Operations - official illustration 26</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (177).webp" alt="4.1.1 Control Box Operations - official illustration 26"><figcaption><p>4.1.1 Control Box Operations - official illustration 26</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (178).webp" alt="4.1.1 Control Box Operations - official illustration 26"><figcaption><p>4.1.1 Control Box Operations - official illustration 26</p></figcaption></figure>

Pressing the emergency stop button will lock the lifting arm height and disable the elevation buttons. The lifting arm will also remain locked if power is lost during operation.

2\. Rotate the emergency stop button

clockwise until it pops out. Elevation button functionality will be restored.

3\. Lifting Arm Elevation:

Press and hold the ascent button on the control box or manual controller to continuously raise the lifting arm.

4\. Lowering the Lifting Arm:

Press and hold the descent button on the control box or manual controller to continuously lower the lifting arm.

**4.1.2 Base Operations**

<figure><img src="../../.gitbook/assets/unknown (179).webp" alt="4.1.2 Base Operations - official illustration 27"><figcaption><p>4.1.2 Base Operations - official illustration 27</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (180).webp" alt="4.1.2 Base Operations - official illustration 27"><figcaption><p>4.1.2 Base Operations - official illustration 27</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (181).webp" alt="4.1.2 Base Operations - official illustration 27"><figcaption><p>4.1.2 Base Operations - official illustration 27</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (182).webp" alt="4.1.2 Base Operations - official illustration 27"><figcaption><p>4.1.2 Base Operations - official illustration 27</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (183).webp" alt="4.1.2 Base Operations - official illustration 27"><figcaption><p>4.1.2 Base Operations - official illustration 27</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (184).webp" alt="4.1.2 Base Operations - official illustration 27"><figcaption><p>4.1.2 Base Operations - official illustration 27</p></figcaption></figure>

1\. 1. 1. Expand Workspace:

Step on the right pedal to expand the transfer cart's workspace. This is required when operating the robot with protective measures.

2\. Reduce Workspace:

Step on the left pedal to reduce the workspace. Recommended during robot transportation or long-term storage.

3\. Locking and Unlocking the

Transfer Cart Wheels

2\. The left wheel in the diagram

below is in the locked state; once locked, the transfer cart cannot move, and you can lock the wheels when placing the machine for a long time. The right wheel in the diagram below is in the unlocked state; after unlocking, the transfer cart can move normally.

3\. In the locked state, step on the

<figure><img src="../../.gitbook/assets/unknown (185).webp" alt="4.1.2 Base Operations - official illustration 28"><figcaption><p>4.1.2 Base Operations - official illustration 28</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (186).webp" alt="4.1.2 Base Operations - official illustration 28"><figcaption><p>4.1.2 Base Operations - official illustration 28</p></figcaption></figure>

position indicated by the orange arrow in the specified direction to unlock the wheels.

4\. In the unlocked state, step on the

position indicated by the red arrow in the specified direction to lock the wheel

4\. Charging Instructions:

Charge the transfer cart when the battery indicator displays one bar (approximately 25% remaining).

Connect the control box charging cable to a 220V/50Hz power supply. During charging, the display will dynamically show the increasing power level.

#### 4.2 Battery Usage <a href="#id-4-2-battery-usage" id="id-4-2-battery-usage"></a>

**4.2.1 Battery Overview**

No. Component Name Description ① Handle Used for temporary carrying and moving of the battery ② Power Display Button Press to activate the power level indicators ③ Power Level Indicators 4 indicators in total. When pressed, lights correspond to battery level (each light = 25%). All lights show white above 25%; only first light shows red below 25%, others remain off.

④ Buckle Secures the battery to the robot's back during installation, providing additional stability ⑤ Charging Port Connect the dedicated charger to charge the battery ⑥ Buckle Button Press to retract the buckle for battery removal. Releases to pop out and secure to the robot's back.

⑦ Slot Engages with the robot's back during installation to provide additional stability.

<figure><img src="../../.gitbook/assets/unknown (187).webp" alt="4.2.1 Battery Overview - official illustration 29"><figcaption><p>4.2.1 Battery Overview - official illustration 29</p></figcaption></figure>

**4.2.2 Battery Installation**

Ensure the battery has sufficient charge before installation.

Hold the battery with both hands as shown in the diagram. Align it with the robot's back and slide downward firmly until it engages with the battery slot. The installation is complete when the battery reaches the state shown in the right diagram.

**4.2.3 Low Battery Alert**

Monitor power levels continuously during robot operation. Replace or charge the battery promptly when power is low.

Note: ：

When battery level drops below 15%, the indicator light will flash red and the robot will announce: "Battery level low. Please charge promptly." Operation without protective measures is strictly prohibited at this stage.

Never allow the robot to shut down abnormally due to complete power depletion, as this may damage system files.

<figure><img src="../../.gitbook/assets/unknown (188).webp" alt="4.2.3 Low Battery Alert - official illustration 30"><figcaption><p>4.2.3 Low Battery Alert - official illustration 30</p></figcaption></figure>

**4.2.4 Battery Charging**

Two charging methods are available:

(1) Direct Charging: Connect the charger directly to the battery. Full charge requires

2 hours.

(2) Indirect Charging: Install the battery on the robot. Connect the charger to the

charging port in the robot's debug compartment to power the robot while simultaneously charging the battery. Full charge requires 2 hours 40 minutes.

The figure below shows the standard robot charger. During charging:

Connect plug ① to a 100-240V power source.

Connect plug ② to either the robot's charging port or the battery charging port.

<figure><img src="../../.gitbook/assets/unknown (189).webp" alt="4.2.4 Battery Charging - official illustration 31"><figcaption><p>4.2.4 Battery Charging - official illustration 31</p></figcaption></figure>

The figure below illustrates the robot's normal charging state:

When charging, there is a 2-3 second delay after the power supply is connected.

Please observe carefully; the following conditions indicate normal charging:

(1) When the battery is not fully charged, the "power indicator lights" at Battery

<figure><img src="../../.gitbook/assets/unknown (190).webp" alt="4.2.4 Battery Charging - official illustration 32"><figcaption><p>4.2.4 Battery Charging - official illustration 32</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (191).webp" alt="4.2.4 Battery Charging - official illustration 32"><figcaption><p>4.2.4 Battery Charging - official illustration 32</p></figcaption></figure>

Position 1 will turn on in a number corresponding to the remaining power. Among them, the first one is a red breathing light, and the others are white and always on.

(2) The fan at Charger Position 2 will operate, and a "humming" wind sound can be

heard.

(3) The two indicator lights at Charger Position 3 are steadily red.

When the battery is fully charged, charging protection will be activated: the fan

stops running, all battery indicator lights go out, and both indicator lights on the charger also go out.

Note： Only use the standard charger provided. Non-standard chargers are strictly prohibited.

Avoid keeping the charger connected to the power source for extended periods.

**4.2.5 Battery Removal**

The Expedition A2 supports battery replacement without shutdown while the robot is charging. Two removal methods are available:

Shutdown Removal:Follow standard procedures to shut down the robot before removing the battery.

Note: The robot will immediately power off upon battery removal. Never remove the

battery while the system is operating without charging connection.

Hot-Swap Removal (without shutdown):Ensure the robot is in charging state during battery removal. Avoid significant movement of the robot.

Note:Charging has a 2-3 second delay. Confirm the charger is actively charging

before removal-do not remove immediately after power connection.

Replace the battery promptly after removal. Never operate the robot without a battery installed.

When removing the battery, refer to the diagram below: hold the battery handle with one hand while pressing the buckle button, and use the other hand to slide the battery out of the robot's back from bottom to top.

<figure><img src="../../.gitbook/assets/unknown (192).webp" alt="4.2.5 Battery Removal - official illustration 33"><figcaption><p>4.2.5 Battery Removal - official illustration 33</p></figcaption></figure>

#### 4.3 Robot Startup <a href="#id-4-3-robot-startup" id="id-4-3-robot-startup"></a>

**4.3.1 Debug Compartment Overview**

The debug compartment is located at the robot's lower back and remains closed during normal operation. Press the raised area of the compartment cover to release the latch and access the interior.

Debug Compartment Layout The opened debug compartment is shown in the figure below:

(1) Position ①: Orin industrial computer network port. Connect via Ethernet cable

for robot debugging.

(2) Position ②: Robot chassis charging port. Used to charge the battery when

installed. Supports simultaneous operation while charging.

(3) Position ③: USB port. Supports external devices (e.g., speakers, microphones).

(4) Position ④: Power button.

Press: Button depresses with solid green indicator light → robot powers on.

Press again: Button pops out with light off → robot powers off.

<figure><img src="../../.gitbook/assets/unknown (193).webp" alt="4.3.1 Debug Compartment Overview - official illustration 34"><figcaption><p>4.3.1 Debug Compartment Overview - official illustration 34</p></figcaption></figure>

Note: Unlabeled ports are reserved for debugging purposes. For access, please contact

AgiBot technical support.

**4.3.2 Robot Startup**

**4.3.2 Robot Startup**

1\. Pre-Startup Checklist

(1) Verify matching serial numbers for the robot, emergency stop switch, and remote

controller.

(2) Ensure the battery is fully charged and properly installed.

(3) Confirm the robot is suspended by the transfer cart.

2\. Startup Procedure

Open the debug compartment and press and hold the power button until the green indicator lights up. The robot will power on and begin startup (approximately 1 minute). Observe the following states:

(1) Ambient Lights: The body ambient lights will activate, with the chest indicator

displaying a blue flowing light pattern.

(2) Self-Test (\~10 seconds):

Head moves up/down/left/right, then faces forward.

Hands open and outward rotate, followed by sequential finger curling, finally forming fists and returning to neutral.

<figure><img src="../../.gitbook/assets/unknown (194).webp" alt="4.3.2 Robot Startup - official illustration 35"><figcaption><p>4.3.2 Robot Startup - official illustration 35</p></figcaption></figure>

Upper limbs initialize with joint locking after completion.

(3) Audio Alert: The robot will announce "Audio player is ready" during the process.

(4) Completion: After \~1 minute, the robot will reach the following state indicating

successful startup.

#### 4.4 Remote Controller & Emergency Stop Usage <a href="#id-4-4-remote-controller-emergency-stop-usage" id="id-4-4-remote-controller-emergency-stop-usage"></a>

Most functions of the Expedition A2 require operation via the remote controller.

The emergency stop switch is used to immediately cut off robot power in emergencies, forcing the robot to stop instantly to prevent personal injury, equipment damage, or escalation of hazardous situations.

The remote controller and emergency stop switch of the Expedition A2 are shown in the figure below:

<figure><img src="../../.gitbook/assets/unknown (195).webp" alt="4.4 Remote Controller &#x26; Emergency Stop Usage - official illustration 36"><figcaption><p>4.4 Remote Controller &#x26; Emergency Stop Usage - official illustration 36</p></figcaption></figure>

For convenience, the emergency stop switch is mounted on the right end of the remote controller and can be pulled upward for detachment.

<figure><img src="../../.gitbook/assets/unknown (196).webp" alt="4.4 Remote Controller &#x26; Emergency Stop Usage - official illustration 37"><figcaption><p>4.4 Remote Controller &#x26; Emergency Stop Usage - official illustration 37</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (197).webp" alt="4.4 Remote Controller &#x26; Emergency Stop Usage - official illustration 37"><figcaption><p>4.4 Remote Controller &#x26; Emergency Stop Usage - official illustration 37</p></figcaption></figure>

**4.4.1 Emergency Stop Usage**

No. Componen ① Identificatio n Label

Note: 1. Robot SN: Emergency stop switch is

paired with the robot (verify serial number match). 2. Input current: Do not exceed limits during charging.

② Power Button Press and hold to turn the emergency stop switch on/off.

③ Power Indicator Lights up after power-on. The number of lights indicates the power level.

<figure><img src="../../.gitbook/assets/unknown (198).webp" alt="4.4.1 Emergency Stop Usage - official illustration 38"><figcaption><p>4.4.1 Emergency Stop Usage - official illustration 38</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (199).webp" alt="4.4.1 Emergency Stop Usage - official illustration 38"><figcaption><p>4.4.1 Emergency Stop Usage - official illustration 38</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (200).webp" alt="4.4.1 Emergency Stop Usage - official illustration 38"><figcaption><p>4.4.1 Emergency Stop Usage - official illustration 38</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (201).webp" alt="4.4.1 Emergency Stop Usage - official illustration 38"><figcaption><p>4.4.1 Emergency Stop Usage - official illustration 38</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (202).webp" alt="4.4.1 Emergency Stop Usage - official illustration 38"><figcaption><p>4.4.1 Emergency Stop Usage - official illustration 38</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (203).webp" alt="4.4.1 Emergency Stop Usage - official illustration 38"><figcaption><p>4.4.1 Emergency Stop Usage - official illustration 38</p></figcaption></figure>

④ Charging Port Type-C port for charging the emergency stop switch.

⑤ Connection Status Indicator Glows green when the robot and emergency stop switch are both powered on and automatically connected.

Glows red when disconnected (e.g., after the r robot is powered off).

⑥ Emergency Stop Button Press to trigger emergency stop: all robot joints are disabled. Use with caution. To release, rotate the button clockwise until it pops out.

The robot's head and upper limbs will then perform a self-test. Normal operation resumes after successful self-test.

Button height in normal state

Button height in the e-stop state

**4.4.2 Remote Control Usage**

**4.4.2.1 Remote Control Function Description**

<figure><img src="../../.gitbook/assets/unknown (204).webp" alt="4.4.2.1 Remote Control Function Description - official illustration 39"><figcaption><p>4.4.2.1 Remote Control Function Description - official illustration 39</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (205).webp" alt="4.4.2.1 Remote Control Function Description - official illustration 39"><figcaption><p>4.4.2.1 Remote Control Function Description - official illustration 39</p></figcaption></figure>

No. Component Name Description ① Identification Label Note the following information:

1\. Robot SN: Verify serial number match before use

2\. Input current: Do not exceed limits during charging

② Cut-out Design (Right Side) Provides access to emergency stop functions: operate switch, check power level, and charge through this opening ③ Power Button Press and hold to turn the remote controller on/off ④ Charging Port (Bottom) Type-C port located at the bottom for charging the remote controller

**4.4.2.2 Remote Controller Operation**

1\. Press and hold the power button until the screen displays the following interface,

then release the button:

2\. Wait for the startup animation to end, and you will enter the following interface.

The date is displayed in the upper left corner of the interface, the remote control battery level in the upper right corner, and the time in the center. Please pay attention to the battery level and charge the remote control in a timely manner when it is not in use.

<figure><img src="../../.gitbook/assets/unknown (206).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 40"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 40</p></figcaption></figure>

3\. Slide up on the screen to unlock it and enter the "Robot Type Selection" interface

<figure><img src="../../.gitbook/assets/unknown (207).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 41"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 41</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (208).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 41"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 41</p></figcaption></figure>

of the robot control software Aim-Master. Currently, only AgiBot A2 is supported for selection. The language can be switched in the upper right corner of the interface, and Chinese and English are available at present; the remote control software version and launch date are displayed in the lower right corner of the interface.

Note: For subsequent operations that require synchronized control of the robot, you

must strictly follow the procedure and pay close attention to the prompt messages.

4\. Click on the robot image to enter the "Lifting Ring Installation" interface. Inspect

<figure><img src="../../.gitbook/assets/unknown (209).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 42"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 42</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (210).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 42"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 42</p></figcaption></figure>

the robot's lifting rings to confirm there are no abnormalities, then select the \[Next] button.

5\. Enter the "Lift the Robot" interface, confirm that the robot has been lifted, and

select the \[Next] button.

6\. Enter the "Power On" interface and press the power button. Wait for the robot to

start successfully (alternatively, you can power on the robot in advance before using the remote control). Select the \[Robot Started, Begin Connection] button; after clicking, a prompt "Connecting to the robot..." will pop up on the screen. Once the connection is successful, it will jump to the next page.

7\. After the robot is successfully connected, you will enter the "Switch to Standing

Mode" interface. Select the \[switch positions ] button, and a reminder "The robot will move" will pop up. Follow the reminder to ensure there are no people or other obstacles near the robot, then click the red \[switch posture] button to complete the robot's standing posture switch.

8\. After the posture switch is completed, you will enter the "Posture Switch

Completed" interface. The robot should exhibit the following condition: its lower limbs will adjust to the standard standing posture as shown in the diagram below and lock the joints.

This posture corresponds to the \[Assist in standing with straight legs] state (the robot has different states for different functions, which will be explained in detail later). The robot can stand stably after touching the ground.

Confirm there are no abnormalities, then select the \[Next] button.

<figure><img src="../../.gitbook/assets/unknown (211).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 43"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 43</p></figcaption></figure>

9\. Enter the "Lower the Robot" interface. Operate the transfer cart to lower the

robot until its feet are completely on the ground, and the lifting ropes on both shoulders are relaxed with a certain amount of slack left. Then click the button \[Placement Completed, Next Step].

<figure><img src="../../.gitbook/assets/unknown (212).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 44"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 44</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (213).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 44"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 44</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (214).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 44"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 44</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (215).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 44"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 44</p></figcaption></figure>

10\. Enter the "Switch to straight leg walking natural arm swinging" interface and

select the \[Enable straight leg walking mode] button. The system will pop up a reminder. Confirm again that the robot's feet are completely standing on the ground, then select the \[ok] button. The robot will switch to walking mode, which corresponds to the \[movement] state. At this time, each joint will output torque to maintain its own balance.

11\. After that, you will enter the remote control main interface.

Note:

After the remote control is successfully connected to the robot (starting from

<figure><img src="../../.gitbook/assets/unknown (216).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 45"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 45</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (217).webp" alt="4.4.2.2 Remote Controller Operation - official illustration 45"><figcaption><p>4.4.2.2 Remote Controller Operation - official illustration 45</p></figcaption></figure>

Step 7), you can skip the guidance process at each step of the guidance by clicking the

\[homepage] button in the lower left corner, and directly enter the main interface of the operation software. After skipping, the robot’s state will remain in the previous step;

if you want to use it normally, you need to switch the robot’s state through the \[Toolbox] function and operate the robot simultaneously.

It is recommended that you follow the guidance to operate the robot for the first time, and skip the guidance only after you are familiar with the robot.

Example of skipping the guidance:

**4.4.3 Aim-Master Main Interface Overview**

The Aim-Master main interface is divided into three sections:

1.Status Bar: The top row displays real-time robot status indicators.

2.Function Bar: The left column provides access to all robot functional controls.

3.Information Area: The central and right sections show detailed information

corresponding to the selected function.

<figure><img src="../../.gitbook/assets/unknown (218).webp" alt="4.4.3 Aim-Master Main Interface Overview - official illustration 46"><figcaption><p>4.4.3 Aim-Master Main Interface Overview - official illustration 46</p></figcaption></figure>

Every time you enter Aim-Master, you will default to the \[Workbench] (the button is displayed in blue), and the "Information Bar" will show information related to the Workbench accordingly, including: the map currently used by the robot, the robot status monitoring panel, and the robot task management panel.

**4.4.3.1 Introduction to the Status Bar**

The status bar displays various status information of the robot. All status icons are gray when normal and red when abnormal.

<figure><img src="../../.gitbook/assets/unknown (219).webp" alt="4.4.3.1 Introduction to the Status Bar - official illustration 47"><figcaption><p>4.4.3.1 Introduction to the Status Bar - official illustration 47</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (220).webp" alt="4.4.3.1 Introduction to the Status Bar - official illustration 47"><figcaption><p>4.4.3.1 Introduction to the Status Bar - official illustration 47</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRswFAABXRUJQVlA4IMAFAAAQHQCdASqkAEYAPj0cjEOiIaGVjeQ4IAPEtIvAASmEXU2330fIHs/6nv7N4bIh3yP7Vfe/Bm8MfgD/GeoF6o/w28ngA/I/5//t/CO1Au6v+N9UP9K/1PGmUA/z5+vHuq/1/kM+lf+97hP61E5gZsMoBNqnLhOFZ0Qct5Dnkgp1P81bnZk8D6EYvu2Sp84MTiL7I0vg2TjV1G89+HGOu4OYl5ZzrZulu6JHPtvyyTN/edgmYmaIT6ulDINiVI2zMDQ4nDSOQ3bsg8JpAkpy3MM5mQ0Ha0F3nt7h9AG5EQEkHHW/2n5PP0ZL9mlKf/3ekJSAAP7/9zb4geKED6xjKJhMcVdNoeBx+pvyKH60lxb9NKUWjkcXUC5SfDXue5lF1YJVGlBeAo0nV0X5dqcpoPNRmM6izj8pAipbWIlP8f9wxZG6FV9hVO3p48zZVuBtnSoUo83aHW5cefmuX/dOGevIZejl2ZydEE9Y0wsPYbY3iS7r/d4S0t80VB9XEwKDqQ5ZQ2R5jgsDPfdFRuVYXf3GN5iR4aZN3IKb1NBYoDEC/z8ccOTEc/JIVDL3TGKs+qrx5/3jCMVk2/fqe2+qDEx10RPeUZk9ktQ6+QZO918t0+DyJnydzZcJ7f5kQVYtR33eFO0rcd5Pt73ExhDMJv0jkZ3r8x9HS7+/ScVLShpLzCiROpjm+lm6SyosNlnKh3ZmoHsWSYik5+5xVtyQ+GsxO7/NPxGr2Oz0OIv72jrHprSPnik2/LNCY/xwetzlLt2htPReWI2NmeYUG7btr3r/Q12TlV1yB+S6uDnHbjTHSVGNn6RG2sCsO3/0GbSclR6i5VrJvVVJ3bHb1xo9JwMAz6WnOILXOv9r2LAqRj778DX7/OXL9A6WhF3zelolyp8i3l5ibwzAALIXC4AQRt5MB8tLptG0+6ch8sW1NQ5/2zSiA+MC3+vtv7Zv3L5/U95qrQzZnR52YOyyx24DZ4emp+9pXcrbjH4z+Mv/83iz+3XtpzatvhgfqQfOYnpE0aWhuoJ1t9+oBc9nf8ck+TZc5/WGxJFMbyDbGVQSwp02EQE5qHGTOhmgtay3DRuY+6OgEZqfYwiZxOH9twCU5rhIfBuifwsIatLPzBay+Y+IHbHVg7DxGiGHfH/KoiGPpzL2LGAdXZYiktrknoYaSuO3xRlFQYwORi9+hRO14hSSxLtdM5T2/A/QEt8kAMr9QUTQLnqTSA84L/Ml+NNuevWc35MuQCAJz4dhrckrQNOqwmbnMxUZWuQiml872H1sBSJ6bE1LUwdvdrJAzMoGiq7WVzrlBbetnNaijOF4U0I584ZBte5QGk2qkP/DW4dzSvy0F/EcTRWGMVKdWXL3EnykaeLT9992jAZkA3rVr/jKoV2wmKsGE2r1/cJ3kqN6vA5sTBNrMaW2bwnGAAk3cg7B3vrKVqyFArphvpQRP0egdn/wh0acJCePn5TQiA0EbgYM4quhv2ih+y6jFp5NbYMfW16a//8e7oDVU2ex5ykympOY7qCSGoRO2avm0XfrzWjboaaMO3zF6tbwBdFkc9t/rnbB663kcqyiAPYeWHuseR9Bxq7smxLkHleDKlM5OB4OfibZY2aiTIuFnxcpWpTHm6agS7fBFrPP7mYuBuRCx17HvBJAAc9Ukv6ZYs/p8HDzwXwawThgdsHkKMh8h1o14DNuuGXd9T9HEaBFeU1H2wnp026OzvG+8dTYFWrpYrfB1XTLFircLwXIZ+16YCxgiqu6aANihbdP3wp0Lfm6o17+IJTurv5rWAo3wNW8cwdUCypM5J4AJQxJO/BarX1yu3+S0MTCUgVL2Edh4H6Rdqz81/ClBQM1Nr75E6uGliwrfVuzxGkK9qhTTAgCCPhbhNU/qSZXVwzVwEWSzDxcWoJVych0OANxFbNdG1r189kmU3Y+bIEmXNrgYZXCNA4vgVtSYbBxHNsCeOB17QwAAA==" alt="4.4.3.1 Introduction to the Status Bar - official illustration 47"><figcaption><p>4.4.3.1 Introduction to the Status Bar - official illustration 47</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRn4FAABXRUJQVlA4IHIFAACQGgCdASqdAEcAPj0ejESiIaEQVaAgA8SzjNQLgDTtlnE2INPDA2813Dbz7PrOXPzn7XckmIv17/guJ/a//u+/qcs/nP+3/pPJHpfcxz+++iX/vebz6z9g/9YkqajYjYWrMaCtV5nIz9yuy0MC3QMasV1YXON71cvCEEJ20AbCNxZVO0rJAjmf8x14LW7md4vHPbMREPNpp/re28bKqrgsdk1bizf7iVcwuX/qD2ObtVcVElZUeilzfQTQLjhm/RJdK79xR+p90DFjug/m3f5Ka+nVC0Y6Z+4sxG6roAD+/jh//8Hn/fOmP+fW/KdypuEyonTIt7wYH3j/ID3bNP0zNSQLME6SlgO7Rf3dswnO+QDqCITpNlygmPSFWqbeO/5t5Vz6n4tyJHut6h/E9iv4UuagLYeqmP8tLhzv61nXgSvotiIBf4XbHhzTPueVQ+yZyDWq5neLRBibyc5ddqANkMhxn00EKvI3Xy/E6EFuJsT8AxzORwPXlsVKHMrJ1LymlXxkas6YgeuTZuFTD1r9/+WIdDSYdZwZMzWWLiIfeO+fsRkpT/6Frtis1YYXaP6Ie9bf0LtQphIsfI9NvpPDkjmy6KQ2INF5sAx4kvLR624MHB78D2LWNTdAieABrYhY5C++E8C6RLD0ZMAbptzhqlpqnY6UbPGR7o12ja7ElBtLskv4kuvxL/euVafLcUDqOUvvzGCGlUrJ1Nshi52Ga76C8iHMe4vc466P/C4Cp5ZXfafQx4rE/5BXXfpnFmx1K/9z86GU0BPVj6YsXpP6VnJ7mdwxx5LwigWkD6iJ5hfPxkbzuTdV9cGX8NIjLPOhCoSmqd7iOec2rpLc12R8f9kYzngZkI4Dff15FgLmn2RhrgD1Ry84v6NVolyfEhUiYSlQX5Q43bHU5/koLDo7+eWYqS5Vvjv82q+vylizY8SWlq8eW8kVg2koWbvYA2+BKVfB/AgnLhdBA6l0RqCulFeiEDnnSMPQgnmPhEGAe38/FQa6WrU6Nkk868rYa6dokhsuQ/v1RkLv/glxlCrTC2H0HxVI4J4TPRYPSP+jI7rmfyXfzSAYgaeYaqbt/thIaQ75y83QGK7CLwNHQmye9N82sE5ZQRli7P+Vbv48ILF5K/MXjuX8YXtIsrGyv69+F9UGsb/w6p0rn8Nsgs/kTCvU5kc7dVO3bsZj/Sq/l6lkHJEj0vIiz28Lf5Eq3BpAHj6pjf3vorSL+f1l8G4iLQzgk+5LykDqx7QnNUmneD6nAL7wq3b+JjwoJMfDcL4m0UTkTOp6r/Je/sjt/9MC4EyR/tF4UIowQhPFVujGCBd59U/KMGLDeluD2oDQsJqsEWKS6TYCCskUuFmOGeEjhSYKBob4CojKNanV4A3zBv1ohpaOBVP0AyCnnHyY0rhA+KYpLA249Sh16eaQANMyZjIo5/03RAJQ6PzlTD7y9T/6P/BltYD/dSm5S1Snz4s+IkBTiLBxLeLNRmPgVEPHy2z/rhadQDMHwsYmdXucVygdByV7WEf/alQ7ud+cVRKzYZ6pST/2Yc7ffl4fjzQU0q8sfcVwL4FvtO9gbjX1/lkx8peINIi8WNe8SgJHZgB46T4QZC0AJ6UowDwJsrfOcS4V/kf/Z3fCMSnQTiz//tDARZYXF/2sizxPv+9a1pVo1iee5dkp4yCzMTgok73/58SNyK//fYRLDGAkQHzjvIgXa/T15QdoY9CALilAEVc0BRunh86WQI20knM6f8Aw5g0a/3gtBUFkY3l9+w5QGkgROMBHScEJSMymDy8AI+Y32Wdz5lBlGFfmOf9GEjqYvKXBZFevWEbsAA772WUsWFhIiSYQ7eHGRUESsIDETLSAAA==" alt="4.4.3.1 Introduction to the Status Bar - official illustration 47"><figcaption><p>4.4.3.1 Introduction to the Status Bar - official illustration 47</p></figcaption></figure>

Below are the status bar interfaces of Aim-Master on the computer side and the remote control side:

The table below provides detailed information of the status bar： 1 Robot ID Displays the robot's serial number. Except for "One-Key Connection", verify this number matches the actual robot when connecting via other methods.

2 2-1 Power Display Robot Battery Icon color changes with power level.

Level Specific percentage is shown when not full. Monitor power and charge promptly.

2-1 Remote Control Battery Level:

Remote Controller Battery: Icon color changes with power level. Specific percentage is shown when not full.

Monitor power and charge promptly.

3 Control Mode Toggle by clicking the icon:

\- M (Manual): Robot can be controlled via remote controller - A (Automatic): Robot executes automated tasks only (remote control disabled). Used exclusively for autonomous narration missions.

4 Emergency Stop Status Indicates emergency stop state:

<figure><img src="data:image/webp;base64,UklGRlQEAABXRUJQVlA4IEgEAAAwGgCdASqlAEYAPj0YikMiIaEU+08kIAPEtIBqOMzMReqw0sBH3QZsUmPnx8QZzzNk/JvMVUNrnX3d5yr6RyCi6z8MFLbjxGPzN9Bf4ldKC8v9/T12/tRKOhedkCBMgX8ApJEg0rpIdCck/bAq5I5jKvy/uDX6qCgm/C+xp93c+9PXTqJRnYsjVUUYfkO3kB7AqCq3io2XDHkoCk3SODBQebTJpyWwXjyMH0xFUIAlZGgcRHp45WdosJPNXBq0Nq/73TYMPt9kvrTkFB8NvYGffAVZ5/c8aCZoAAD+/98QCJ/+42N/klBtJYJoR0h6IVoNZnlt3+KbzruiG+UJau2syzb1ogQ/2EQt0doQSZT98Zhsi8Z/i8v65i+hbA7xPmN7W/ZWK9HCxBtfalTb5QRPQblCG+hyDq1sY3/i88aGlpPckEffFDyDyFhdlhQE1GaNzKACU5YnIqAm4GqurIbu16Tc/Tfwh/R4KNAaMJc/uXcLFOFnqONNTe0/jzvSkFNb5xmj5+nYv/K18cRg0t1/RkfcIQOBkgz+9HLwo4qCWpDuj687TY7b1tMn3ynI9Sq/ULW9prmQxSqPaRugmAN0DsYfhv6zm+rnqgdivxyu5kvxux7D2aGXURjfpNdgq/rmstmiKcpmpJU3qJpbpNheIXZBuk5ioby5mW6gIWYarF1DBfNOi9bWLybDGrkzitT/EUmcqCQaVVLFfJjzOdmgyLd9CgIqY1yFiI0OussHZ8auSc8nIde2Y+vIaAxJ1P3O5KrUxz77BmT5REUdfKkm63texnUV+Vzq+GUm+WjnmPZSbv4RUFoaZD+/lnnJ8IyH1b0JpdUUbG5emJS7ygLmzeruL2qrOBMToP3srZi9BI+5z6udjqewKLhQDcmE2l+ga4FovKoPT3Pl/KEWTW3ivRd6eqEzCpEDc7Sssfvon0JcWk2rilJl7lQIAjGV046CSI1R6iZZTiaptjlGTMr6IUiElDl2DPuxRM7ClvfiA3aNecMnc7DlR6XjzXErKglj1CH6qVvXPQNF31Ft/PBJgMQOyorP8pIRj+x+5GfS7Ihtqs+lBNqyOyyPcGiK1odPmHuizOcxRVdbuaDW4f3RMcJfdVTHVH/DRxWkjwRB5RGYrZnBSLpyjh7uCQ2GVOraABnAXddB49dxmCV07C2mrdOGMZvQ+/m6QDuXLGGQoCx5eV01fDRnSyk6v+5xbOKJ2ZCrekfbeh9kTeeyaemHfgrLrnU1yUDj7dmJURR/sNmBsuJUUihIYX382VTlMYy2RxiXl6DfaWU/pemOIdDgWCKW4esct7rycaDPl8x6LS2aG+tdDfBsJcJcHcMHK7kf9lRFoEkc+hP9w/j8uJWY6ko3KnpZOwIOovLLkQ9AfR1oYsY3T4hE49FZrSKUee5lGXvcDS3/ncOh24OTeZxhorQkUeTxszN4s4l+PMsCSEmPtA0OIAAA" alt="4.4.3.2 Function Bar Overview - official illustration 48"><figcaption><p>4.4.3.2 Function Bar Overview - official illustration 48</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (221).webp" alt="4.4.3.2 Function Bar Overview - official illustration 48"><figcaption><p>4.4.3.2 Function Bar Overview - official illustration 48</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (222).webp" alt="4.4.3.2 Function Bar Overview - official illustration 48"><figcaption><p>4.4.3.2 Function Bar Overview - official illustration 48</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (223).webp" alt="4.4.3.2 Function Bar Overview - official illustration 48"><figcaption><p>4.4.3.2 Function Bar Overview - official illustration 48</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRiwCAABXRUJQVlA4ICACAADwFwCdASqkAI8APj0ajESiIaESfd0kIAPEs4HYDzkuNzqsYIFizNGHFK69DV75E8s2vG0p/FAYy/CgJg9ZjaHNVDSCvfiHdqLYoD+Mw4jtlRWj+sIAt6gPR0cJTQy4WG2QA2HCiYGvECeeFLBUFIyxVNE2GEY8Yuzub62w3l2rsY27q50ttyy7kZ90ZZ45ifepJvVKZ+FockZz55DVOWrIfenxoe1dcK6xCNwbBSXWpzWjrDzZB/6DHhAoqN8zUnRnyWLIqAA4gAD+/f7f3a//riIX/7t36h7+mRMOQuc7IFfnwAexqII5ATkbi1MOSt+EXMfobjF6phDXv0FVcOLALSbsu3pObm2zwewiQm66UMHA4U5PLptoyRB6iguE1gnko2QZM5BSmqlVoAEkVSh+VMXFfKzAIyxOz0eUxz5zAtGyWQx49X9PUP21C0AhRje3QZR8lY5V1DNRD+cXqKkKnp6JOCxSqbdf6k5E7mIz9Y8TY21jy4HmTIaaEusAwm+4cG7LIF4qH4BTRdENKEUu5XOuzGYIzRpKbF0LNPd6E5C2AIRt3o9kET+PHSucYzeT3NrxY2g1OJ05ZmSGLkjyajAKj0HOL0Wb+uCMCbh93ufiODcXkDwJJ08XmRuIqx9FdeT/nalbSdCQr8akh+YXMorItJzWtUsfNaMaVaH6i4vYVrRb5Tm1GNUTAVFl3RWYy/qSpy0baXTZMRwNKAAA" alt="4.4.3.2 Function Bar Overview - official illustration 48"><figcaption><p>4.4.3.2 Function Bar Overview - official illustration 48</p></figcaption></figure>

\- Gray icon: Normal operation - Red icon with exclamation mark:

Emergency stop activated 5 Positioning Status Displays robot localization status:

\- Shows "Abnormal" most of the time.

Status clears after successful relocation.

6 Network Status Shows network connection status of the Orin industrial computer:

\- Displays signal strength when connected - Light gray icon when disconnected

**4.4.3.2 Function Bar Overview**

The current version features 9 buttons in the Function Bar, enabling various robot functionalities. For detailed information, please refer to the next chapter.

#### 4.5 Lapel Microphone Usage <a href="#id-4-5-lapel-microphone-usage" id="id-4-5-lapel-microphone-usage"></a>

The Expedition A2 Upgraded Edition is equipped with a lapel microphone to meet voice interaction needs at medium to long distances. Using the lapel microphone can significantly improve voice interaction performance in noisy environments.

The lapel microphone has been pre-paired with the robot. The figure below shows a schematic diagram, with the red box indicating the Robot SN. Please verify that this number matches the robot's serial number before use.

<figure><img src="../../.gitbook/assets/unknown (224).webp" alt="4.5 Lapel Microphone Usage - official illustration 49"><figcaption><p>4.5 Lapel Microphone Usage - official illustration 49</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (225).webp" alt="4.5 Lapel Microphone Usage - official illustration 49"><figcaption><p>4.5 Lapel Microphone Usage - official illustration 49</p></figcaption></figure>

Lapel Microphone Usage The lapel microphone package includes a detailed user manual for basic operations.

This section specifically covers using the lapel microphone for voice interaction with the robot.

The following procedures assume the robot is in voice-interaction ready state.

1\. When stored in the charging case, the indicator light glows red. Upon removal, it

automatically pairs with the robot. The indicator turns blue when pairing is successful.

2\. Through the settings function of the remote control, switch the microphone type to

<figure><img src="../../.gitbook/assets/unknown (226).webp" alt="4.5 Lapel Microphone Usage - official illustration 50"><figcaption><p>4.5 Lapel Microphone Usage - official illustration 50</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (227).webp" alt="4.5 Lapel Microphone Usage - official illustration 50"><figcaption><p>4.5 Lapel Microphone Usage - official illustration 50</p></figcaption></figure>

"external microphone".

3\. Hold the wireless lapel microphone close to your mouth, or attach it to your collar. Refer

to section 5.3.2 "Voice Interaction" to interact with the robot via voice.

Note: Charge the wireless lapel microphone in a timely manner after use. Insufficient

battery power will cause connection failure. If the wireless lapel microphone fails to connect to the robot, check its battery level.

### Chapter 5: AgiBot A2 Functions <a href="#chapter-5-agibot-a2-functions" id="chapter-5-agibot-a2-functions"></a>

This chapter will elaborate on the functions of AgiBot A2, with explanations based on the function bar of Aim-Master. The specific order will prioritize the robot usage habits first, and then consider the connections between various functions.

#### 5.1 AgiBot Logo <a href="#id-5-1-agibot-logo" id="id-5-1-agibot-logo"></a>

In addition to displaying brand identity and conveying corporate values, the logo can be clicked in different ways to activate the following three functions:

(1) View the Aim-Master version information.

(2) Switch the connected robot.

(3) Toggle the Aim-Master interface between windowed and full-screen modes.

The logo functionality varies across different platforms. Below are details for two commonly used platforms (Windows and remote controller) after logging into Aim- Master:

<figure><img src="../../.gitbook/assets/unknown (228).webp" alt="5.1 AgiBot Logo - official illustration 51"><figcaption><p>5.1 AgiBot Logo - official illustration 51</p></figcaption></figure>

1\. Single-Click Logo:Used to switch the connected robot.

2\. Double-Click Logo:

Windows Platform: Toggles between full-screen and windowed modes. The interface defaults to windowed mode after startup, which may result in incomplete display of status bar information.

Remote Controller: Double-click functionality is not supported.

<figure><img src="../../.gitbook/assets/unknown (229).webp" alt="5.2 Toolbox - official illustration 52"><figcaption><p>5.2 Toolbox - official illustration 52</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (230).webp" alt="5.2 Toolbox - official illustration 52"><figcaption><p>5.2 Toolbox - official illustration 52</p></figcaption></figure>

#### 5.2 Toolbox <a href="#id-5-2-toolbox" id="id-5-2-toolbox"></a>

The Toolbox function is used to switch the robot between different states and is the 7th item in the function bar. All functions of the robot can only be realized by switching to the corresponding state, so this function is explained first.

This function involves the joint movement of the robot and has many precautions.

You must be familiar with the precautions during operation to avoid accidents.

After selecting the Toolbox function, click the drop-down triangle next to the "Function Switch" label in the upper left corner of the interface to pop up different functions of the robot. When you select a function, the operation process required for the robot to switch from its current state to the state that enables the corresponding function will be displayed.

Take the "Shutdown" process as an example:

The process for shutting down the robot after it is powered on is as follows:

The shutdown process from an interactive state is as follows(The status toggle bar can be swiped left to reveal the hidden statuses):

<figure><img src="../../.gitbook/assets/unknown (231).webp" alt="5.2 Toolbox - official illustration 53"><figcaption><p>5.2 Toolbox - official illustration 53</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (232).webp" alt="5.2 Toolbox - official illustration 53"><figcaption><p>5.2 Toolbox - official illustration 53</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (233).webp" alt="5.2 Toolbox - official illustration 53"><figcaption><p>5.2 Toolbox - official illustration 53</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (234).webp" alt="5.2 Toolbox - official illustration 53"><figcaption><p>5.2 Toolbox - official illustration 53</p></figcaption></figure>

In the operation process, the text with a border represents the robot state switch button, which can be switched manually or automatically. The manual switching method is to double-click the button.

Notes:

All operations affect the robot. Users must fully understand the following information and strictly adhere to it during operation:

Blue background with white text: Indicates the robot's current status (e.g., 【Straight-leg walking, upper limbs moving】).

Blue border with blue text: Represents switchable statuses (e.g., 【 Assisted straight-leg standing】). Special attention must be paid to prerequisite instructions or prompts before switching.

Gray border with gray text: Indicates currently non-switchable statuses. Prerequisite operations must be completed first (e.g., 【Initialization】 in the figure).

Borderless text: Provides operational instructions or prompts that must be carefully read and strictly followed (e.g., "Please stabilize the robot" and “lifting robot” in the figure).

**5.2.1 Status Description**

Robot States (Total of Four Types) \[Default]: This state is used to switch the joints on and off, with two application scenarios:

(1) Before landing: After the robot is powered on, it automatically switches to

\[Default] to power on the joints. Before landing, switch to the \[Assist in standing with stright legs] state, then lower the robot.

(2) Before shutdown: After hoisting the robot, first switch to \[Default] to power off

the joints, then shut down the robot.

Note: In \[Default] mode, the robot’s lower-limb joints are disabled. This state can

only be activated when the robot is hoisted by the transfer cart. You must fully understand and strictly follow this rule-never switch to \[Default] mode when the robot is on the ground.

\[Assit in standing with straight legs]: This state is used before the robot lands or is hoisted. After switching to this state, all the robot’s joints rotate to fixed positions and lock to maintain stable standing.

Note: In this state, the robot acts like a fixed model and cannot adjust its balance; it

easily falls when subjected to external forces. Therefore, do not remove protective devices or let the robot stand in this state for a long time after landing-switch to another state as soon as possible.

\[Walk with straight leg and perform upper limb Movements]: This state is used for remote control interaction with the robot. When the robot’s lower limbs are standing or walking, its upper limbs can perform interactive movements (voice interaction works in any state; see Chapter 5.3.2 "Voice Interaction" for details).

Notes:

In this state, each joint outputs a certain amount of torque to counteract external forces (e.g., gravity) that cause imbalance, thereby maintaining stability. If the robot is unbalanced but not to the point of falling, it will automatically move its lower limbs to readjust balance.

Never hoist the robot in this state. Sudden weightlessness will cause the robot’s lower limbs to swing randomly and violently, which may result in personal injury or equipment damage.

\[Humanoid Walking]: This state corresponds to the robot’s walking function. In this state, you can control the robot’s movement via the remote control-the robot can walk with a human-like gait, and its upper arms swing naturally.

Note: Hoisting the robot is also prohibited in this state.

**5.2.2 Function Implementation**

**5.2.2.1 Walking Function**

The walking function allows you to control the robot to achieve humanoid walking via the remote control.

In the "Function Switch" menu, select "Humanoid Walking". After selection, the operation process required for the robot to switch from its current state to the state enabling the walking function will be displayed at the bottom of the interface.

Follow the process to finally switch the robot’s state to \[Humanoid Walking]- only then can the walking function be activated.

<figure><img src="../../.gitbook/assets/unknown (235).webp" alt="5.2.2.1 Walking Function - official illustration 55"><figcaption><p>5.2.2.1 Walking Function - official illustration 55</p></figcaption></figure>

The operation steps are as follows. Since the switching process varies depending on the current state of the robot, this is for reference only. During actual operation, follow the real-time process displayed on the interface. Subsequent functions will not list switching steps separately.

(1) Switch the robot to the \[Assit in standing with straight legs] state.

(2) Operate the transfer cart to lower the robot.

(3) Switch the robot to the \[Humanoid Walking] state.

(4) Refer to Chapter 5.4.1 to control the robot using the remote control.

<figure><img src="../../.gitbook/assets/unknown (236).webp" alt="5.2.2.3 Teleoperation Function* - official illustration 56"><figcaption><p>5.2.2.3 Teleoperation Function* - official illustration 56</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (237).webp" alt="5.2.2.3 Teleoperation Function* - official illustration 56"><figcaption><p>5.2.2.3 Teleoperation Function* - official illustration 56</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (238).webp" alt="5.2.2.3 Teleoperation Function* - official illustration 56"><figcaption><p>5.2.2.3 Teleoperation Function* - official illustration 56</p></figcaption></figure>

**5.2.2.2 Interactive Functions**

Voice interaction can be performed in any state; here, we take robot remote control interaction as an example.

In "Function Switch", select the "Movement" function. The operation process required for the robot to switch from its current state to the state enabling the interaction function will be displayed at the bottom of the interface.

Operate the robot synchronously according to the process. After finally switching the robot’s state to \[Walk with straight legs and perform upper limb movements], you can use the remote control to control the robot’s interaction.

**5.2.2.3 Teleoperation Function\***

The robot state corresponding to the teleoperation function is the same as that of

the interaction function.

Operate the robot synchronously according to the process, and finally switch the robot’s state to \[Walk with straight legs and perform upper limb movements]

**5.2.2.4 Autonomous Explanation Function**

<figure><img src="../../.gitbook/assets/unknown (239).webp" alt="5.2.2.5 Shutdown - official illustration 57"><figcaption><p>5.2.2.5 Shutdown - official illustration 57</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (240).webp" alt="5.2.2.5 Shutdown - official illustration 57"><figcaption><p>5.2.2.5 Shutdown - official illustration 57</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (241).webp" alt="5.2.2.5 Shutdown - official illustration 57"><figcaption><p>5.2.2.5 Shutdown - official illustration 57</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (242).webp" alt="5.2.2.5 Shutdown - official illustration 57"><figcaption><p>5.2.2.5 Shutdown - official illustration 57</p></figcaption></figure>

In "Function Switch", select "Autonomous Narration". After selection, the operation process required for the robot to switch from its current state to the state enabling the autonomous explanation function will be displayed at the bottom of the interface.

Operate the robot synchronously according to the process. After finally switching the robot’s state to \[Humanoid Walking], refer to Chapter 5.7 "Workbench" to start the autonomous explanation task.

**5.2.2.5 Shutdown**

The shutdown operation will power off the robot and must be performed when the robot is under protection. If shutting down the robot when it is on the ground, strictly follow the process below:

1\. Connect the boom of the transfer cart to the lifting rings on both shoulders of

the robot.

2\. Hold the robot firmly to keep it stable.

3\. Switch to the \[Assist in Standing with straight legs] state.

4\. Operate the transfer cart to hoist the robot until its feet are higher than the

base of the transfer cart.

<figure><img src="../../.gitbook/assets/unknown (243).webp" alt="5.2.2.6 Other Functions - official illustration 58"><figcaption><p>5.2.2.6 Other Functions - official illustration 58</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (244).webp" alt="5.2.2.6 Other Functions - official illustration 58"><figcaption><p>5.2.2.6 Other Functions - official illustration 58</p></figcaption></figure>

5\. Switch the robot’s state to \[Default] to power off the joints.

6\. Perform a short-press and hold on the robot’s power-off button (press once, release

immediately, then press and hold) until the button indicator goes off to turn off the machine.

**5.2.2.6 Other Functions**

The robot in the current version has four additional switchable functions: Chair Standing, Chair Sitting, Teleoperation, and Data Acquisition. These four functions require additional equipment and are non-standard features.

For specific usage methods, please consult the on-site delivery engineer. This document will not elaborate further on

#### 5.3 Interaction <a href="#id-5-3-interaction" id="id-5-3-interaction"></a>

The interaction function enables the robot to interact with humans. The interaction capabilities of AgiBot A2 include: displaying a variety of expressions, performing multiple upper-limb movements, conducting voice conversations, and providing corresponding feedback in response to certain commands.

The interaction methods of AgiBot A2 are divided into two types: remote control interaction and voice interaction.

1\. Remote Control Interaction: Use the remote control to send commands to the

robot and control it to interact with humans.

2\. Voice Interaction: Interact with the robot through voice conversations.

<figure><img src="../../.gitbook/assets/unknown (245).webp" alt="5.3 Interaction - official illustration 59"><figcaption><p>5.3 Interaction - official illustration 59</p></figcaption></figure>

**5.3.1 Remote Control Interaction**

Remote control interaction includes two types: expression interaction and movement interaction. In addition to the robot’s built-in default movements, it supports customizing the robot’s interaction movements using motion capture equipment. For details, please consult Zhiyuan technicians.

Expression interaction allows the robot to display different expressions on its face, and can be performed in any state after the robot is powered on.

(1) Power on the robot, place it on the ground, and switch it to the \[Walk with

straight legs and perform upper limb movements] state.

(2) Ensure there are no personnel or obstacles within the robot’s overall working

space.

(3) If the robot is under the protection of the transfer cart, an additional

person is required to assist in moving the transfer cart.

Specific Operations

(1) On the interaction function details page, the status bar contains two interaction

options: "Emoji" (for expression interaction) and "Action" (for movement interaction). The default option is "Action", and you can switch between them by clicking the respective buttons.

<figure><img src="../../.gitbook/assets/unknown (246).webp" alt="5.3.1 Remote Control Interaction - official illustration 60"><figcaption><p>5.3.1 Remote Control Interaction - official illustration 60</p></figcaption></figure>

(2) The "Action" is used to control the robot’s upper-limb movements. Double-

click a movement label to make the robot perform the corresponding movement.

Each movement file is executed once, with a unique duration displayed at the top- left corner of the label. After the robot completes the movement, its upper limbs will return to the natural hanging posture.

(3) The "Emoji" is used to control the robot to display facial expressions. You

can double-click an expression label to make the robot show the corresponding facial expression, with the expression duration displayed at the top-left corner of the label. After selecting an expression, it will play in a loop unless another event triggers an expression switch.

(4)You can enter the name of an expression or movement in the search window to

accurately filter expressions or movements. The search function uses fuzzy matching, and the list will display all files containing the input text.

<figure><img src="../../.gitbook/assets/unknown (247).webp" alt="5.3.1 Remote Control Interaction - official illustration 61"><figcaption><p>5.3.1 Remote Control Interaction - official illustration 61</p></figcaption></figure>

**5.3.2 Voice Interaction**

The voice interaction function of Yuanzheng A2 supports real-time dialogue with humans and can respond to specified commands, enabling natural and intuitive human-robot interaction. It can be used in any state after the robot is powered on, without the need for additional state switching.

1\. Wake up the robot

Before starting voice interaction, you need to wake up the robot: Speak "Hi,luka" to the robot (this is the default wake word and can be modified). Confirm the robot is awakened after it responds verbally with "I’m here".

After voice wake-up, the robot’s facial expression will provide corresponding feedback: When not awakened, the face displays a "Prompt" expression showing the featuring vertical eyes with curved eyebrows.

<figure><img src="../../.gitbook/assets/unknown (248).webp" alt="5.3.2 Voice Interaction - official illustration 62"><figcaption><p>5.3.2 Voice Interaction - official illustration 62</p></figcaption></figure>

2\. Voice Interaction Process

You can have free conversations with the robot for voice interaction.With a normal network connection, after the robot is powered on, voice interaction can be conducted in any state, but the robot’s feedback varies by state:

(1) Only powered on or switched to \[Assist in standing with straight legs]

state: Supports voice chat and voice-controlled facial expression switching.Examples of commands: "Smile", "Make a sad expression".

(2) Powered on, placed on the ground, and not in \[Assist in standing with

straight legs] state: Supports voice chat, facial expression switching, and upper- limb movements. Examples of commands: "Wave hello", "Shake hands".

(3) Powered on, placed on the ground, not in \[Assist in standing with straight

legs] state, and with accurate positioning: Supports voice chat, facial expression switching, upper-limb movements, and lower-limb movement. Examples of commands: "Move forward", "Walk two steps forward".

3\. Notes

<figure><img src="../../.gitbook/assets/unknown (249).webp" alt="5.3.2 Voice Interaction - official illustration 63"><figcaption><p>5.3.2 Voice Interaction - official illustration 63</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (250).webp" alt="5.3.2 Voice Interaction - official illustration 63"><figcaption><p>5.3.2 Voice Interaction - official illustration 63</p></figcaption></figure>

(1) During voice interaction, if the robot is on the ground and not in the \[Assist

in standing with straight legs] state, it will accompany its voice responses with upper-limb movements (similar to hand gestures when a person speaks).

Maintain a safe distance.

(2) Only common interactive movements or expressions can be activated via

voice, such as handshakes, fist bumps, and waving.

(3) Voice interaction supports connection to external microphones and external

speakers.

(4) The duration of the robot’s movements is fixed. When making physical

contact with the robot (especially during handshakes), ensure the robot extends its hand first and you withdraw your hand first. This prevents

collisions or pulls that may cause personal injury.

**5.3.3 Multimodal Interaction**

The current version supports the robot’s multimodal interaction. To use this function: After waking up the robot, say to it, "What do you see?" The robot will recognize all elements within the camera’s view, including scenes, people, objects, and text. After processing and reasoning, it will describe these elements to you through voice playback.

#### 5.4 Control <a href="#id-5-4-control" id="id-5-4-control"></a>

The control function enables the robot to walk with a human-like gait. It is mainly controlled using a remote control, and also supports real-time synchronization of the operator’s movements via teleoperation equipment to complete specific tasks.

On the details page of the control function, there are two buttons in the status bar:

\[Joystick] and \[Teleoperation]. Click the buttons to switch to the corresponding control mode, with \[joystick] as the default mode.

1\. joystick Mode: Control the robot’s movement using the remote control.

2\. Teleoperation Mode: The robot can be teleoperated using a motion capture suit

and VR glasses. This is a non-standard feature, and the specific process will be provided in the teleoperation document; no further elaboration is given here.

<figure><img src="../../.gitbook/assets/unknown (251).webp" alt="5.4 Control - official illustration 64"><figcaption><p>5.4 Control - official illustration 64</p></figcaption></figure>

**5.4.1 Controlling the Robot with the Remote Control**

The robot is controlled via the virtual buttons on the remote control. In the current version, the robot supports three movement modes: omnidirectional translation, left/right rotation, and stop.

As shown in the figure below:The left button is the movement button, used to control the robot’s omnidirectional translation.The right button is the steering button, used to control the robot’s left or right rotation.

The two buttons can be used in combination to achieve left or right turning.

The Aim-Master state corresponding to the robot’s walking function is \[Humanoid Walking]. Before controlling the robot’s movement, you must switch to this state through the ToolBox function.

Control the robot to perform different movements using the remote control as follows:

<figure><img src="../../.gitbook/assets/unknown (252).webp" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 65"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 65</p></figcaption></figure>

Slide and hold the Movement Button in any direction The robot translates in the corresponding direction. The sliding distance directly affects the robot's speed: closer to the origin = slower, farther = faster.

Release the Movement Button The robot stops after stabilizing itself, with a 1-3s delay.

Slide and hold the Steering Button left The robot rotates left in place.

Slide and hold the Steering Button right The robot rotates right in place.

<figure><img src="../../.gitbook/assets/unknown (253).webp" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 66"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 66</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRiAFAABXRUJQVlA4IBQFAABQLACdASrRANYAPj0ejUUiIaERKtxsIAPEs7dwufiNiA0pbtH5XcIF23yafmP/Ofbp2ovMA/SbpAeYD9Yv2q7EvoAf1n+8dYh6AHli+yr+yP7X+zb/9NZsUJyHjbi2tC2fOOdR0MPR3sFfqFvkH7SB39ZtkioBwGxAa1e+q2j/djldM0IpEbMwqVDqUKW//KzZaScD3w6PfH7OXNetTwGP/AtycmVXevwD/YVpeD3hcaWnuhWsqi7IrS+H5qVHDB10oHpSc3ESBEFke6OH0X8W0DQgv2e1GTx9cw+QsepzjJ8TORJhONLQU10SKWsnpHQdQ5crAg5822M9WzG8wd2KOdkgQQtP4iRnakOOPV3v8LWA3BB7dsrV96sDkLHEW569t9RC0G+lmQF90ea+Dec19vx/SXy1lwNjHIdbXG2sJfoDPvOOSkhGI21pe6rKASlIdzP6pWwMBmgmVfDDfS7i7Gz3Yh3Jyd0Q6YAA/v4u/+nv/7QyX/38ol3X1dTybSIm/HrHEbGKW93dZHqadwZY5JdeYsHfnUPy/gSgXbCBF/t7ddL3gKEPKbMrnoAHwdZrH1WEoKQb1axnfj1T9YQWXogfyBYgLWG2FFRG1ZMUeAUoDNUu2+m362O4oBe+lKUBYOR5h8j/G4SM2kWXQSxA/aIhASRwLVYnG2gITyV8NXW/7NGcH+5v8Cn7CgyWEBEoF737lYH3+pe0nCmyn9+IJRJhQslrO3bIKaOoA5ttzb+OvWJ8jPvYpxMQWjwfqs0iBqikqRTGe7LcvcK2rQnGnsp/9DlB5z75VZee//NOKnw/ybrGzus3eYrYx2t8X5BZ3kmn730PlEvaZ09zvFqcMQP5k9dmfyDdr84crJ5lHy4zhHE+JF9O3hE33oZ2XmQHgoZ2uDGG20vLyPHsTp5IHRy7VGAuQMa+1PcQU7W8EvNe1wfmf7Eomsf4XvjxWCHNXeJ+GVYMEsnc2Jxh8EotaEvpP5lKGRyPzh1pVNn4+e85ITGmF6sJHEtCZsPk2CITq0PF8Uv3ETZq+2e1s+53fwd6SC9v63x/vImssyiucewtK3dxVEhIYNb8EzeN+Tu13UDfbKw/v/8MuWJR/jrQneH1gVALSPTR3x/F7XOi/ls9GykqI4JE0psw6ANkPAPc9JO1Mjs/xMuf2OicNfbGJ6px1bQofwBR0fS7G89u4oCNv6qzYnhvkjwwxa3MYDJI68cqU1916yzjLXXLGavMNNyZda+3sXNEOoCaKkaxhtSunl4KhsD4OEIuGrKy97FP+j+6xM9d6iQACerZz14W5AoYet3+fzpeuW3RdeiapTQCcOgBJhF9/vwzzil94dW4zLylA53xCZ7mL/V3JOIY7glksLjcvAWEnHaSXWBAJwpOCVK1hdwrfJmR01rJA2bKfhk5xMbrskToT7uTqb5YS0M2+cQa30up/4NeSWe3d78kvTgEOxdVMccNjgtahq0wkKEyUw100tdxELpfo2g5w5QthylamViVMLFNQHh+6F+O+hx79YIy54sDK5gcX4m9wuWRDx8CB+rkTpLcDIgeAbvBgvkJoFBpkLuwtJGtOqycPgR4KzBreWI9Yk/bKb6SeHij9h2QIIxL/wO7UqSHBQm6n6ywK3Mu9OFIBeQC7vNliDQiQW3/GFiXT0BlPUrOVL2JqI+3ahmW9HeY9ecaPJ+nzBPozKb2KGS1ltuYU1xLBLqLlJvg5J5MEyU7SQAAAAAA" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 66"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 66</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRpAEAABXRUJQVlA4IIQEAAAQHgCdASrEAGgAPj0ejESiIaESfSTIIAPEsoBrxuH5K974kBO0eRP8v0mfEY6b/mM/XLyQPeL6AH9u/wHW1+g75bP66fD55RWqfxOd8OZX0P6hAxr9qk6hMgZSGPYfAnHyegQID7lWwR+byj4kDEEegel6FJWPkLjJkVFr/aRTimtZogNIujEryt9f35gAoxfcnwivMUHkBdzbqLh7l/Dmix0WI0FVPP6t62edJWwL5CnXznWHl+xBWSZk4J4Mj57bhUwxR5yMCkFfw+0JQbvIYJGaiEkEC+00vSZ/h/nVVUmgf/6GoSbMgoYI1Q/XPcTEU+y3YL13MAAA/v4iP+3//9sFj/+F/hwHuKf9g7zX++QY71adg4aAGoWJmt0pWdCHdBpRycX2e6JFt7RLpUafrMCT+rKezdDu7he0X/DXXquDnIP1a1BsjiJknVyuzSWXPzaaZNhuRixnVNj+CAhUO8hIf7NIRoBQmmSteRgBE9iAIjR4cfffx83qstXZFesiMT8MKWZtRF7AmVCfUqbFj890Ff/nR3H+btL2sYRtf+R2b9MRR1YO2wqsOfxK/g4Vrzp5j9ugdjSjjj/2kiNSv6ypnj++yjK8922rqy3Kbd+0qC3a+h1UEyD1OMCsVVG2zRlVS+Pwg43t9ZTj93Z4zHRRSA+8O/Jhtc//VPbh1aXhXcw+UaudLbXfRgrSAtehVKoxhHpSeDmhCIEHJbbw4fbTtZ4ydF2gf5njnEXEyvQxPSf+s/7P8K6/quJCS/lqDad8D0i2h689XMK7LKm+2FORj2K4ZVEWefvc+D6ZNpGoJmJUhAR/fH04p/JW1DGHbxwTM/Cc5/gQf+UbNqffdZt6lbTnMd/f1CkiItlAPzLHHx/3XtCesytrzf2x6TCQQnYlGnOKXcbB9qcl0gRYsLnTJNnrllkZsa30fCDnToa+ppBt/Dmxxw48oax0FUvSLiEDyWBRuZJpSG96w91HPUQhUWHosAjSQyU+KuV7JUQIdQg9H+GuEnlThiDYMpFVnMruDGP87L3flL/0h36TKY/JhMFMon7iPhBofSnJ0zzRA6qa/AuBrx6mutC2NjJKThjOANiEYkuD40Y6HY+MWzZCL2/QqGQx9CAWvtSaXm8PhsryfnCxgV22MyvJqcR8QF8HLzn7o91sX3bj1YwkgRjRCMm5xsze7WXdgdEBjLbppSmAD7MfRVKHbv3gL6ll//t4lvPIHS6PiIyghunrUT5iT0S3Ipg6LLdq51tZ74k7GAKszqUXPD47Vsl7Gu2up+N6oK62ae2GfZyG10Q9P+Sgki7/PjM5ReMyIOqnuQf+eteVQd/BVLqgnJlSWJE/6Vwu+Cf+wSOY1ckdtvRo2xUGjTbdY/dPmXZJzvZXC+3+gdX/WCXUln24ctk4Mm9mqhr5D1Hol7vY4k8+4pFjCBmeYCwBI9YRlncdgL/aQmd4rowANeUmav2ptqf3Bj+a9QTwF/QG7K5Sbql5I6bWZlK3012jpbOEx+gOid4AVnfqR+SNidQ91wFAERo7d5QoAAAA" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 66"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 66</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRqoEAABXRUJQVlA4IJ4EAAAQHQCdASrEAGgAPj0ejUSiIaESTYy4IAPEsoHYD0IVPmNPF+R/8N7BfQ14O/U+8x36zfqB7SHQwdbl6EvTAfar7RmqNOlfRJ9HCvNaoi7iFJeBUpKtLo0a0SSzEwm7FOxhZvH5PYX1qyQLfEY3E5brM0L5qP4DjVWhyujibCmt4aDQmqWfUCd3NI39cSJNfpY9NkYPNyxHs4DGKXTDz6Fz2q5/foW6KTj1CpTjV9a6zsX/e0wzPYpfYTFfaZZGa88eQqydoHDsazG6VTPlCigVDgAebvhyZTr8l1AX7F72+cACOJYoJGG0LiRihsJ/fI7AAP79SF/gX/+0Ts/+/lgJzy1Y2kaBkHdUTA0/sUkNgdcsDRAbkCzgTkl7etbBFjX8B0MEM3I/2sn7lSWJHncOXUaLVFQwVcOxFEmjdvzLCcvm+GGdF7J0OA4JWbmF6hPlZUPjM1XSArLOdfC54JFgfRyV8I/1B4KpV+OXePGKeBU+03GExW7HtHxvZVjAKaMLM+/xQPZebBowowO/4OjsIXB1x+uHPuZhvxdVyGFGGfvneNj7D/f4e0mtA55QN/zrtecW8gwob+dJWhA43GUHQ98KNGnYr+tU22m6W67zj00x7U4TU4Y8R7XJuKlws+wwQyWoH9DR0wtb0vtO6OQTrcPU518DTiiygeor2J1jPCPZp8Go3koE7lhttKrn+XWNTEyd/L/157Q/iL3Ibff/fn/SN5bZ3IHRB5h7KKfVqFI/HesFZ6cIDzVFM5gD4zrjDwMrcH0KlR98zeHP+pYTGTzn9T2qgTBJW1nXNR/8IkJ5gAt5uI7WOf8kp3VRX+2RKotEDLwaTGjJSYfY2vwf7sTEccrdzdvAp94ltU8DRx9YtoVGsX6mQQUIBNVd0wkvlIUdMx/2FKtCqzYsWZPzBGWV2dOgDVpBKMlM+1nvl0861dim32WlEnlV9ynJDGfcZzZl8oQkYPKzpTnGLve/+8BeY2KWQRavo9lnpZLRaVfQxKpWQQCig7S6vWsh64YvaYtX5IOSueXNBMvDwhgYwQnLz3WsDC5DkHKHyFyBCMT93AyYzVsb23KaXoCQt20FAqF+Y1w7xnkIV+lwlPlkbL9JMA1AcmzEYZBAGZJPYOp1Kmu1bOo1YbZ131QBZDOUnSEOvZXKoDPXQRYiTxADoBn3kieXBNm3ZKR95nKpyrECuJtQqFYsTDcW9cY//CvQKr57eSKyOal+fWwelSRSKl8NgZdGXmT2cvOFfEmnZRdasN6TFIso7CCg3RnbCylhGHN0EKeKdP9EbmBQ1sO0mUFBJSN/9CIRlvitvV/aXHL40Ihpv8ExhapFlhsvsGk2doPOVm8oNVsEUEF0sYZvnrYKdX/kx/J3s1jP7O/9bUbDqQknWtqgFu36DyN2zL6ah7fEHQ8E0pGIJoEEpv/mfD7xeVKloXnp4U8fu5YdODt8LwcL1Q/HtWiYTzv+H9+319n3/JngEQSd37+gyWlwALmzE9nYbNl/v14gMbRTQrIxlGs+kmrQVHQ7QCv7RUqN8DBoIh8IB6H0XJXLeqLc+v/Kbw3kv2gLpAAAAAA=" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 66"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 66</p></figcaption></figure>

<figure><img src="data:image/webp;base64,UklGRloFAABXRUJQVlA4IE4FAADwHwCdASrQAGgAPj0ejEQiIaETWvTUIAPEsoBqtKZeD/A/L4mS6uf1H2wfQD0XeYB+pPS48xPm+dIB/QP851rHoAeWp7Pf7L/rl7NOqYX+hoflC+rxzn8BjU8WHHDNBwAMGDBgvIEWrLrejPVaePuW3xHshJkAYVH16/XxugXvyET2Lpumt2Gc69JIH31CgWV2+bWryDlExWcshRbisS3CSgC3/cn/PRGNqcpkNlV3eX/7DyAQiBUVDBlc0yRewDIzMHQ8cj/UfLcSLjCmlYPmQjCpeAgnnJMdSIXkLeIKDSMXDSl00NhxjFP61DiMWQ00NtLk/xA0mjhgSBykiOSjKSLsrkrVE+AA/v3yH+3//9sUS/+F/+AHdhv9yYijhctkPP58v70qgby/kgcKqNS/CknmboeNjOcd/bwso03Ba+s1f/sgCogkKEs0aYdb1RL62pSe/CFVBOqlOVmEm6dvZ3b6PiFrdy8n+7xpprhOhnL17FVhiFIJRNrfFKZRYShODCJanT8p5IaqVxUaSq95CMrI2wn9s/1hpIhH4YZA7lWosX2dMs0HBs9luuXjuq5jqpX+0zmH8YRE1VnWS43LdHtRSPF07lVBSSY+vAID8zuCFr7AFZIuaorxIz0FkLA5D2/A8J5u/fWl4oXdvCyUGq5G1wx6EUwgUDk+1kW+o/2GHtEk77uuFj2jwYbA3N+Gpf3+QCUWCt8NM6wzqAuqe7L3aLT4sE4KfNb3GsNGjYhOjAQgelwt2fLtv8Hzzob+A7aspnKeBjOQXcrJJE9V40nlc5xlJE+OwWRYQYtWdDaG2dq+h9FZlV9dz4UJ/V4H//chVd6ZDxhyRv6ZXPvDE2C+e/nNexrRr64H9Mepe4PeUN2650LEsvcwOztxoS09tMMQemRorKErBRqzWK3Zeg+7zb8C6O+ZLw74+ZMwPgMONVmiLZin1KJbG1OqbRSasrbKE9SD/oVfU+BOXPfRGF+39fsBMnHLAdX5HsQe17/MbixR5ombotmVdxbO0RcdpYKRO13OpOx+jg/bkI8hZ9ZifGeE+l+a+20Z/91TizTbulfrb9Q2v4dD8HmUrSTthDB4omnhtnhmo5Q/Me9tzev3Z4tIlQq6mr7hn7mwct58xpw8IG/TvV4fNbC5hM50mZnwUDTaAFtzZtZxrtYq+q/4/fQFypbMJnZDDZ5DRHkjC0L4tFEDACJqbagkaPd2hufnBTv/Ek6lDKJLs9Z2qgBEcTsxLoc92WiPZH3oAthdnIYpktiFxbZRNaBFI9JXLJf4Z91mAURPojr+YqJjwEWCsQ/cAPOnGlZeH1ff+ZQot329+CMWxKOLJqOAhJzZbK9bX3PLcZbSNMtbnSPiC6oc0PgfMcqMJfFaXSD0I22UxIzF/gdx0V5OiyNIdcPyUvQPj5wqw6GlUERGmxHw1QjlOHOlk6kiUY4wFBms6z50P46k9cdmlVQb2cCmfOiF7cOOeI3lilZPBskZWQPpGE4NJrMJ3OiHwJ6xzaRR9Wj3m9+n2x8ghD9wV0cNhc4lmQm0Q2B9AC4qD3G091DjJH/9+QBIY+UgAQ/g8wLY7GJSQ1jpMdQRMJ89I/hyXrWVHOE+xfmrqKCfwzwMeLlRMYtcneo/bPl1ZAgvq/9O9Ni5ucTqNxBwMX/UQZAes1LNSYffJp3h1BCp8x54oq8uI+X9ABmty7lFYmuwAfurKuEPP1REVekdCi0xFH7Ma0JPV5O6aoCiEl4m1U3wGBlELoKqI9tYqit3pXAjeaqAOrCPKItRMUUs/OueBnUGvCL1xTLiNYn3OD9U8AAAAA==" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 66"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 66</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (254).webp" alt="5.4.1 Controlling the Robot with the Remote Control - official illustration 66"><figcaption><p>5.4.1 Controlling the Robot with the Remote Control - official illustration 66</p></figcaption></figure>

Release the Steering Button The robot stops after stabilizing itself.

Slide Movement Button forward + Steering Button left simultaneously The robot turns forward-left.

Slide Movement Button forward + Steering Button right simultaneously The robot turns forward-right.

Screen Lock and Unlock

The screen lock is set to automatic: On the control function interface, if the robot’s limbs remain stationary for 30 consecutive seconds, the screen will lock automatically. This is to prevent accidental touches on the screen that could cause the robot to move unexpectedly.

To unlock: Swipe the on-screen slider to the right.

#### 5.5 Map <a href="#id-5-5-map" id="id-5-5-map"></a>

The map function can scan the actual scene to construct a map, upload it, and after relevant operations, provide it for the robot to use for navigation in the actual scene.

Relevant operations include map construction, map storage, map editing, and map application.

1\. Map Construction: In an unknown environment, the robot senses the surrounding

environment through its own sensors, calculates its position in real time, and gradually builds an environmental map.

2\. Map Storage: The constructed map is stored in the robot’s industrial computer,

and relevant operations on the map can be performed in Aim-Master.

3\. Map Editing: Operations such as renaming, deleting, adding points, and editing

information can be performed on the map.

4\. Map Application: Applying the map enables the robot to realize functions such as

autonomous navigation, environmental interaction, and task execution.

<figure><img src="../../.gitbook/assets/unknown (255).webp" alt="5.5 Map - official illustration 67"><figcaption><p>5.5 Map - official illustration 67</p></figcaption></figure>

**5.5.1 Map Construction**

1\. On the map function details page, select the \[Create a New Map] button. This will

<figure><img src="../../.gitbook/assets/unknown (256).webp" alt="5.5.1 Map Construction - official illustration 68"><figcaption><p>5.5.1 Map Construction - official illustration 68</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (257).webp" alt="5.5.1 Map Construction - official illustration 68"><figcaption><p>5.5.1 Map Construction - official illustration 68</p></figcaption></figure>

activate the LiDAR (Light Detection and Ranging) to scan the site, record information about the site’s boundaries and obstacle outlines, and display this data as dense red dots on the screen.

2\. Keep Aim-Master on the "Create a New Map" interface. Push the transfer

machine or remotely control the robot to move around the entire activity area of the site. At the same time, observe the screen to ensure that all site boundaries and obstacle outlines that may affect the robot’s movement have been recorded.

3\. Clicking the \[Save] button will bring up the map name editing interface.

4\. Enter the map name according to the actual situation, then select the \[Save] button

<figure><img src="../../.gitbook/assets/unknown (258).webp" alt="5.5.2 Map storage - official illustration 69"><figcaption><p>5.5.2 Map storage - official illustration 69</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (259).webp" alt="5.5.2 Map storage - official illustration 69"><figcaption><p>5.5.2 Map storage - official illustration 69</p></figcaption></figure>

in the top-right corner of the window to complete the map creation.

**5.5.2 Map storage**

All created maps are stored in the robot's on-board industrial computer. Meanwhile, the map names and map numbers are displayed in the "Map Management" interface of the "Maps" function details page in Aim-Master.

**5.5.3 Map Editing**

All saved maps can be edited when they are not in use. If the robot is using a map to perform an autonomous guided tour task, you must wait for the task to complete or manually end the task before editing.

(1) The map editing function mainly consists of three parts:

(2) Map Files Themselves: Support operations such as map searching, map

selection, information viewing, deletion, and renaming.

(3) Edit map: Adjust the base map, and modify elements like boundaries and

obstacle outlines in the map.

(4) Point: Support operations such as adding, deleting, and editing Point.

**5.5.3.1 Map Files Themselves**

1\. Map Search: On the "Map Management" interface, if there are too many maps,

you can enter the map name in the search box to precisely filter. The search function uses fuzzy matching, and all maps whose names contain the input content will be displayed in the list below.

2\. Map Selection and Information Viewing: After finding the target map, click its

name to select it. The right side of the screen will display information about the map, such as map boundaries and obstacle outlines. You can compare it with the actual scene to confirm the correspondence between the map and the actual site.

3\. Map Renaming or Deletion: After selecting a map, select the \[···] button to the

right of the map name. Two options will pop up:​  Rename: Modify the map name.

 Delete: Remove the map file from the robot system

**5.5.3.2 Edit map**

Modifying the base map information aims to adjust the boundary and obstacle outline data in the map, ensuring the map continuously matches the "real environment" and "actual tasks" while improving the map’s stability and usability.

1\. Scenarios Requiring Base Map Modification: Base map modification is not a

mandatory operation. However, adjustments are needed if the constructed map has the following issues:

(1) Map Construction Defects: During map construction, obstacles that are

transparent, reflective (mirror-like), or pure black cannot be accurately identified. Ensure there are no such obstacles in the robot’s movable area within the site. If such obstacles are unavoidable in the actual scene, the base map must be modified.

(2) Interference Information on the Map: Pedestrians or temporary objects

present at the site during map construction are recorded, but these obstacles no longer exist when the robot performs tasks.

(3) Minor Changes to the Site: Edit the base map information if there are small

changes to the site. If the changes are significant and repositioning fails, re- construct the map.

(4) Manual Planning of Robot Activity Area: When manual planning of the

<figure><img src="../../.gitbook/assets/unknown (260).webp" alt="5.5.3.2 Edit map - official illustration 71"><figcaption><p>5.5.3.2 Edit map - official illustration 71</p></figcaption></figure>

robot’s movable area is required.

2\. Specific Steps for Base Map Modification:

<figure><img src="../../.gitbook/assets/unknown (261).webp" alt="5.5.3.2 Edit map - official illustration 72"><figcaption><p>5.5.3.2 Edit map - official illustration 72</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (262).webp" alt="5.5.3.2 Edit map - official illustration 72"><figcaption><p>5.5.3.2 Edit map - official illustration 72</p></figcaption></figure>

(1) Access the Modification Page: Select the \[Edit] button in the top-right corner

of the screen. In the pop-up interface, select the \[Edit map] button to enter the "Edit map" interface. Operation buttons will pop up on the right side of the screen.

(2) Obstacle Removal: This function is generally used to eliminate interference

<figure><img src="../../.gitbook/assets/unknown (263).webp" alt="5.5.3.2 Edit map - official illustration 73"><figcaption><p>5.5.3.2 Edit map - official illustration 73</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (264).webp" alt="5.5.3.2 Edit map - official illustration 73"><figcaption><p>5.5.3.2 Edit map - official illustration 73</p></figcaption></figure>

information on the map, such as the removal of temporary objects. Follow the steps shown in the diagram: click \[Known Area] → select "Polygon" or "Rectangle" → draw a shape to enclose the obstacle marker to be eliminated → click \[Save] on the map → click \[Save] in the top-right corner.

(3) Add Obstacles: This function is generally used to add obstacles on the map,

enabling the robot to either bypass a location (via polygons) or be restricted from reaching a location (via polyline-blocked boundaries) when planning paths. It is often applied in scenarios where there are glass/mirrors or pure black boundaries.

Click \[Bound] → select "Polyline" or "Polygon" → add the corresponding shape at the location where the obstacle needs to be added on the map → click \[Save] on the map → click \[Save] in the top-right corner.

<figure><img src="../../.gitbook/assets/unknown (265).webp" alt="5.5.3.2 Edit map - official illustration 74"><figcaption><p>5.5.3.2 Edit map - official illustration 74</p></figcaption></figure>

**5.5.3.3 Points**

When the AgiBot A2 performs autonomous navigation tasks, Points serve as target locations for path planning and play a crucial role. In the current version, the robot cannot execute autonomous navigation tasks without points.

1.Adding points

There are two ways to add points: recording and drawing.

The recording method is suitable for scenarios requiring precise positioning and orientation of points.

The drawing method is suitable for scenarios where precision in the position and orientation of points is not critical.

The following is the point recording method:

After entering the map editing interface, follow the steps below to record the robot’s position and orientation in the actual site into the map and generate points. This method fully accounts for various conditions of the robot; during actual operation, some steps may be omitted. For example, if the robot is accurately positioned when recording points, the repositioning step is unnecessary.

(1)Select the \[Point] button. After the point-related operation buttons pop up

on the right side, select the \[Record] button. If the map currently being operated is inconsistent with the map used by the workbench, a "Set it as the map in use"

<figure><img src="../../.gitbook/assets/unknown (266).webp" alt="5.5.3.3 Points - official illustration 75"><figcaption><p>5.5.3.3 Points - official illustration 75</p></figcaption></figure>

interface will pop up; select the \[ok] button

<figure><img src="../../.gitbook/assets/unknown (267).webp" alt="5.5.3.3 Points - official illustration 76"><figcaption><p>5.5.3.3 Points - official illustration 76</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (268).webp" alt="5.5.3.3 Points - official illustration 76"><figcaption><p>5.5.3.3 Points - official illustration 76</p></figcaption></figure>

(2)After switching the map, positioning anomalies usually occur, and you

need to resolve the positioning error first. Select the \[Auto Position] button, which will activate the robot’s radar to scan the current scene in real time and generate a red map. Adjust the red map to align with the orange map, then select the \[Complete] button to successfully reposition the robot.

(3)After successful repositioning, select the \[Point] button on the right side. A

\[Marking] button will appear below the icon indicating the robot’s current location. Clicking this button will bring up a point naming window.

<figure><img src="../../.gitbook/assets/unknown (269).webp" alt="5.5.3.3 Points - official illustration 77"><figcaption><p>5.5.3.3 Points - official illustration 77</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (270).webp" alt="5.5.3.3 Points - official illustration 77"><figcaption><p>5.5.3.3 Points - official illustration 77</p></figcaption></figure>

(4)In the pop-up point naming window, enter the point name and click the

\[Save] button. The point recording will then be successful, and the recorded point will store information about the robot’s position and orientation in the actual

scene.

The following is the freehand point drawing method:

After entering the map editing interface, follow the steps below to manually add points on the map:

(1) Click the buttons in sequence: \[point] → \[Draw] (which pops up on the right side)

→ \[Nav] → the location on the map where you want to add the point. A editable point will then be added at the corresponding position on the map.

(2) Drag the dark blue dot and rotate it along the blue circle to adjust the orientation

of the point.

(3) Click another location on the map to move the point to that position; the point

cannot be repositioned by dragging.

<figure><img src="../../.gitbook/assets/unknown (271).webp" alt="5.5.3.3 Points - official illustration 78"><figcaption><p>5.5.3.3 Points - official illustration 78</p></figcaption></figure>

(5) Select the \[Save] button, and a point naming interface will pop up. Enter

<figure><img src="../../.gitbook/assets/unknown (272).webp" alt="5.5.3.3 Points - official illustration 79"><figcaption><p>5.5.3.3 Points - official illustration 79</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (273).webp" alt="5.5.3.3 Points - official illustration 79"><figcaption><p>5.5.3.3 Points - official illustration 79</p></figcaption></figure>

the point name and select the \[Save] button to successfully create the freehand- drawn point.

1\. Viewing point Information

The point icons on the map can display three types of information:

(1) Name: The name of the point, such as "init\_place" as shown in the diagram.

(2) Position: The location of the icon determines where the robot will conduct its

explanation in the actual scene.

<figure><img src="../../.gitbook/assets/unknown (274).webp" alt="5.5.3.3 Points - official illustration 80"><figcaption><p>5.5.3.3 Points - official illustration 80</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (275).webp" alt="5.5.3.3 Points - official illustration 80"><figcaption><p>5.5.3.3 Points - official illustration 80</p></figcaption></figure>

(3) Orientation: The direction the icon’s arrow points determines the robot’s

facing direction when it gives explanations in the actual scene.

2\. Editing points

(1) Bringing up the Editing Interface

Click the point editing button at position 1 in the diagram, and an interface (as shown by the green frame) will pop up, where you can edit the point.

(2)Renaming or Deleting points

Select the \[···] button to the right of the point name, then select "Delete" or "Rename" from the pop-up options to perform the corresponding operation on the point.

(3)Searching for points

If there are too many points, you can enter the point name in the search box to quickly find the target point.

(1) Adjusting point Position and Orientation

This operation must be performed in the drawing mode; it cannot be edited in the recording mode.

In the drawing mode, click the point name to switch the corresponding point on the map to edit mode. After that, the following editing operations can be carried out:

 Moving a point: Click any position on the map to move the point to the corresponding location.

 Adjusting point orientation: Drag the dark blue dot to adjust the orientation of the point.

 Exiting edit mode: Select the \[Cancel] button to cancel all modifications to the point and restore it to its initial state when first created.

 Confirming modifications: Select the \[Save] button to save the modified point information.

<figure><img src="../../.gitbook/assets/unknown (276).webp" alt="5.5.3.3 Points - official illustration 81"><figcaption><p>5.5.3.3 Points - official illustration 81</p></figcaption></figure>

#### 5.6 Tasks <a href="#id-5-6-tasks" id="id-5-6-tasks"></a>

<figure><img src="../../.gitbook/assets/unknown (277).webp" alt="5.6 Tasks - official illustration 82"><figcaption><p>5.6 Tasks - official illustration 82</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (278).webp" alt="5.6 Tasks - official illustration 82"><figcaption><p>5.6 Tasks - official illustration 82</p></figcaption></figure>

The Task function enables the creation and management of autonomous explanation tasks. After completing the corresponding configurations on the workbench interface in combination with the Map function, the robot can perform autonomous navigation and explanation according to the task content.

**5.6.1 Creating a Task**

1\. On the details page of the Task function, select the \[Create a New Task] button,

<figure><img src="../../.gitbook/assets/unknown (279).webp" alt="5.6.1 Creating a Task - official illustration 83"><figcaption><p>5.6.1 Creating a Task - official illustration 83</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (280).webp" alt="5.6.1 Creating a Task - official illustration 83"><figcaption><p>5.6.1 Creating a Task - official illustration 83</p></figcaption></figure>

and a "Create a New Task" window will pop up.

2\. Enter the task name and select the task type (only one type option is available by

default in the current version). Select the \[Complete Creation] button to finish creating the new task and access the task content configuration interface.

**5.6.2 Configuring Task Content**

After a task is created, its content must be fully configured before the robot can perform autonomous navigation and explanation according to the task requirements.

**5.6.2.1 Basic Parameters**

1\. Task Map

Bind the map for executing this task. Only after binding can you continue editing the task content. On the workbench interface, this autonomous navigation task can only be executed if the corresponding map is selected.

2\. Task Prompt and Task Description

These are reserved functions and are not yet available for use in the current version.

<figure><img src="../../.gitbook/assets/unknown (281).webp" alt="5.6.2.1 Basic Parameters - official illustration 84"><figcaption><p>5.6.2.1 Basic Parameters - official illustration 84</p></figcaption></figure>

**5.6.2.2 Path-base explanation task**

1\. Basic Content Configuration

As shown in the diagram below, you can configure task points for the robot.

When the robot performs an autonomous task, it uses the points added on the map as target locations. Each point requires configuration of corresponding task content, which specifically includes 4 parts: for the first 3 parts, you can directly click the drop-down triangle to select an option, while the fourth part requires text input. The specific content types are as follows:

(1) Position 1: Select the point corresponding to the current task point

(2) Position 2: Select the action the robot will perform at the current point.

(3) Position 3: Select the expression the robot will display at the current point.

(4) Position 4: Edit the voice broadcast content for the robot at the current point.

Enter the content in text form, and the robot will convert the text to voice for broadcast when executing the task. Note that during text input, if the content is formatted incorrectly, the text will be displayed in red. You must adjust it promptly; otherwise, the task cannot be executed.

<figure><img src="../../.gitbook/assets/unknown (282).webp" alt="5.6.2.2 Path-base explanation task - official illustration 85"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 85</p></figcaption></figure>

2\. Special Cases

(1) Scenario Where No Explanation is Needed from the Robot

If a point only requires the robot to arrive without any display, when configuring the corresponding content, select a small-movement action (e.g., nodding), choose the same expression as the previous one, and enter only a single space in the text content field.

(2) Scenario Where a 5th Content Item Needs to Be Added

A 5th content item must be added if any of the following situations apply:

 The explanation content for a single point exceeds 800 characters；  Multiple actions need to be displayed at a single point;；  Multiple expressions need to be displayed at a single point;；  The text content does not match the action duration, requiring the text to be split into multiple segments to align with the action duration.

Specific Operation: Select the \[+] button to add a configuration template for the corresponding point, allowing additional configuration of actions, expressions, and voice broadcast content for the current point (a maximum of 20 segments can be added). Select the \[-] button to delete unnecessary templates.

3\. Adding points

In the current version, you can add any number of points based on specific needs,

<figure><img src="../../.gitbook/assets/unknown (283).webp" alt="5.6.2.2 Path-base explanation task - official illustration 86"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 86</p></figcaption></figure>

corresponding to the number of explanations the robot will give in the actual scene.

After configuring the content for the previous point, select the \[Add point] button to add a new one. The content configuration method is the same for all points.

4\. Add a string Broadcast

<figure><img src="../../.gitbook/assets/unknown (284).webp" alt="5.6.2.2 Path-base explanation task - official illustration 87"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 87</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (285).webp" alt="5.6.2.2 Path-base explanation task - official illustration 87"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 87</p></figcaption></figure>

After the next point is selected, the system will calculate the walking time from the end of the broadcast at the previous point to the movement to the nextpoint.

Select the \[Add a string broadcast] button to enable the robot to broadcast voice while moving to the next point. When adding a string broadcast, pay attention to the following information:

1 Position : The transition script at Position 2 will start broadcasting after a specified interval (5 seconds) following the completion of the task at the previous point.

2 Position 2: Transition script content.

3 Position 3: Broadcast duration of the current transition script (3 seconds).

4 Position 4: Select the \[+] button to add a transition script, or select the \[-] button to delete the current transition script.

5 Position 5: Remaining time until reaching the next point.

6 Position 6: Broadcast interval between multiple transition scripts.

Note: If the total duration of the transition script broadcast plus the interval duration

exceeds the total time required for the robot to reach the next point, the transition script will fail to be added, and some of the scripts must be deleted.

<figure><img src="../../.gitbook/assets/unknown (286).webp" alt="5.6.2.2 Path-base explanation task - official illustration 88"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 88</p></figcaption></figure>

3\. Saving the Task

<figure><img src="../../.gitbook/assets/unknown (287).webp" alt="5.6.2.2 Path-base explanation task - official illustration 89"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 89</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (288).webp" alt="5.6.2.2 Path-base explanation task - official illustration 89"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 89</p></figcaption></figure>

You cannot save the task until its content is fully configured, and the \[Save] button will be grayed out. The \[Save] button can only be clicked to save the task when all task content has been completely configured.

Situations where the task cannot be saved include:

The task can be saved only when all content is completely configured, and the following conditions are met:

<figure><img src="../../.gitbook/assets/unknown (289).webp" alt="5.6.2.2 Path-base explanation task - official illustration 90"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 90</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (290).webp" alt="5.5.3.2 Edit map - official illustration 73"><figcaption><p>5.5.3.2 Edit map - official illustration 73</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (291).webp" alt="5.5.3.2 Edit map - official illustration 73"><figcaption><p>5.5.3.2 Edit map - official illustration 73</p></figcaption></figure>

information on the map, such as the removal of temporary objects. Follow the steps shown in the diagram: click \[Known Area] → select "Polygon" or "Rectangle" → draw a shape to enclose the obstacle marker to be eliminated → click \[Save] on the map → click \[Save] in the top-right corner.

(3) Add Obstacles: This function is generally used to add obstacles on the map,

enabling the robot to either bypass a location (via polygons) or be restricted from reaching a location (via polyline-blocked boundaries) when planning paths. It is often applied in scenarios where there are glass/mirrors or pure black boundaries.

Click \[Bound] → select "Polyline" or "Polygon" → add the corresponding shape at the location where the obstacle needs to be added on the map → click \[Save] on the map → click \[Save] in the top-right corner.

<figure><img src="../../.gitbook/assets/unknown (292).webp" alt="5.5.3.2 Edit map - official illustration 74"><figcaption><p>5.5.3.2 Edit map - official illustration 74</p></figcaption></figure>

**5.5.3.3 Points**

When the AgiBot A2 performs autonomous navigation tasks, Points serve as target locations for path planning and play a crucial role. In the current version, the robot cannot execute autonomous navigation tasks without points.

1.Adding points

There are two ways to add points: recording and drawing.

The recording method is suitable for scenarios requiring precise positioning and orientation of points.

The drawing method is suitable for scenarios where precision in the position and orientation of points is not critical.

The following is the point recording method:

After entering the map editing interface, follow the steps below to record the robot’s position and orientation in the actual site into the map and generate points. This method fully accounts for various conditions of the robot; during actual operation, some steps may be omitted. For example, if the robot is accurately positioned when recording points, the repositioning step is unnecessary.

(1)Select the \[Point] button. After the point-related operation buttons pop up

on the right side, select the \[Record] button. If the map currently being operated is inconsistent with the map used by the workbench, a "Set it as the map in use"

<figure><img src="../../.gitbook/assets/unknown (293).webp" alt="5.5.3.3 Points - official illustration 75"><figcaption><p>5.5.3.3 Points - official illustration 75</p></figcaption></figure>

interface will pop up; select the \[ok] button

<figure><img src="../../.gitbook/assets/unknown (294).webp" alt="5.5.3.3 Points - official illustration 76"><figcaption><p>5.5.3.3 Points - official illustration 76</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (295).webp" alt="5.5.3.3 Points - official illustration 76"><figcaption><p>5.5.3.3 Points - official illustration 76</p></figcaption></figure>

(2)After switching the map, positioning anomalies usually occur, and you

need to resolve the positioning error first. Select the \[Auto Position] button, which will activate the robot’s radar to scan the current scene in real time and generate a red map. Adjust the red map to align with the orange map, then select the \[Complete] button to successfully reposition the robot.

(3)After successful repositioning, select the \[Point] button on the right side. A

\[Marking] button will appear below the icon indicating the robot’s current location. Clicking this button will bring up a point naming window.

<figure><img src="../../.gitbook/assets/unknown (296).webp" alt="5.5.3.3 Points - official illustration 77"><figcaption><p>5.5.3.3 Points - official illustration 77</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (297).webp" alt="5.5.3.3 Points - official illustration 77"><figcaption><p>5.5.3.3 Points - official illustration 77</p></figcaption></figure>

(4)In the pop-up point naming window, enter the point name and click the

\[Save] button. The point recording will then be successful, and the recorded point will store information about the robot’s position and orientation in the actual

scene.

The following is the freehand point drawing method:

After entering the map editing interface, follow the steps below to manually add points on the map:

(1) Click the buttons in sequence: \[point] → \[Draw] (which pops up on the right side)

→ \[Nav] → the location on the map where you want to add the point. A editable point will then be added at the corresponding position on the map.

(2) Drag the dark blue dot and rotate it along the blue circle to adjust the orientation

of the point.

(3) Click another location on the map to move the point to that position; the point

cannot be repositioned by dragging.

<figure><img src="../../.gitbook/assets/unknown (298).webp" alt="5.5.3.3 Points - official illustration 78"><figcaption><p>5.5.3.3 Points - official illustration 78</p></figcaption></figure>

(5) Select the \[Save] button, and a point naming interface will pop up. Enter

<figure><img src="../../.gitbook/assets/unknown (299).webp" alt="5.5.3.3 Points - official illustration 79"><figcaption><p>5.5.3.3 Points - official illustration 79</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (300).webp" alt="5.5.3.3 Points - official illustration 79"><figcaption><p>5.5.3.3 Points - official illustration 79</p></figcaption></figure>

the point name and select the \[Save] button to successfully create the freehand- drawn point.

1\. Viewing point Information

The point icons on the map can display three types of information:

(1) Name: The name of the point, such as "init\_place" as shown in the diagram.

(2) Position: The location of the icon determines where the robot will conduct its

explanation in the actual scene.

<figure><img src="../../.gitbook/assets/unknown (301).webp" alt="5.5.3.3 Points - official illustration 80"><figcaption><p>5.5.3.3 Points - official illustration 80</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (302).webp" alt="5.5.3.3 Points - official illustration 80"><figcaption><p>5.5.3.3 Points - official illustration 80</p></figcaption></figure>

(3) Orientation: The direction the icon’s arrow points determines the robot’s

facing direction when it gives explanations in the actual scene.

2\. Editing points

(1) Bringing up the Editing Interface

Click the point editing button at position 1 in the diagram, and an interface (as shown by the green frame) will pop up, where you can edit the point.

(2)Renaming or Deleting points

Select the \[···] button to the right of the point name, then select "Delete" or "Rename" from the pop-up options to perform the corresponding operation on the point.

(3)Searching for points

If there are too many points, you can enter the point name in the search box to quickly find the target point.

(1) Adjusting point Position and Orientation

This operation must be performed in the drawing mode; it cannot be edited in the recording mode.

In the drawing mode, click the point name to switch the corresponding point on the map to edit mode. After that, the following editing operations can be carried out:

 Moving a point: Click any position on the map to move the point to the corresponding location.

 Adjusting point orientation: Drag the dark blue dot to adjust the orientation of the point.

 Exiting edit mode: Select the \[Cancel] button to cancel all modifications to the point and restore it to its initial state when first created.

 Confirming modifications: Select the \[Save] button to save the modified point information.

<figure><img src="../../.gitbook/assets/unknown (303).webp" alt="5.5.3.3 Points - official illustration 81"><figcaption><p>5.5.3.3 Points - official illustration 81</p></figcaption></figure>

#### 5.6 Tasks <a href="#id-5-6-tasks" id="id-5-6-tasks"></a>

<figure><img src="../../.gitbook/assets/unknown (304).webp" alt="5.6 Tasks - official illustration 82"><figcaption><p>5.6 Tasks - official illustration 82</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (305).webp" alt="5.6 Tasks - official illustration 82"><figcaption><p>5.6 Tasks - official illustration 82</p></figcaption></figure>

The Task function enables the creation and management of autonomous explanation tasks. After completing the corresponding configurations on the workbench interface in combination with the Map function, the robot can perform autonomous navigation and explanation according to the task content.

**5.6.1 Creating a Task**

1\. On the details page of the Task function, select the \[Create a New Task] button,

<figure><img src="../../.gitbook/assets/unknown (306).webp" alt="5.6.1 Creating a Task - official illustration 83"><figcaption><p>5.6.1 Creating a Task - official illustration 83</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (307).webp" alt="5.6.1 Creating a Task - official illustration 83"><figcaption><p>5.6.1 Creating a Task - official illustration 83</p></figcaption></figure>

and a "Create a New Task" window will pop up.

2\. Enter the task name and select the task type (only one type option is available by

default in the current version). Select the \[Complete Creation] button to finish creating the new task and access the task content configuration interface.

**5.6.2 Configuring Task Content**

After a task is created, its content must be fully configured before the robot can perform autonomous navigation and explanation according to the task requirements.

**5.6.2.1 Basic Parameters**

1\. Task Map

Bind the map for executing this task. Only after binding can you continue editing the task content. On the workbench interface, this autonomous navigation task can only be executed if the corresponding map is selected.

2\. Task Prompt and Task Description

These are reserved functions and are not yet available for use in the current version.

<figure><img src="../../.gitbook/assets/unknown (308).webp" alt="5.6.2.1 Basic Parameters - official illustration 84"><figcaption><p>5.6.2.1 Basic Parameters - official illustration 84</p></figcaption></figure>

**5.6.2.2 Path-base explanation task**

1\. Basic Content Configuration

As shown in the diagram below, you can configure task points for the robot.

When the robot performs an autonomous task, it uses the points added on the map as target locations. Each point requires configuration of corresponding task content, which specifically includes 4 parts: for the first 3 parts, you can directly click the drop-down triangle to select an option, while the fourth part requires text input. The specific content types are as follows:

(1) Position 1: Select the point corresponding to the current task point

(2) Position 2: Select the action the robot will perform at the current point.

(3) Position 3: Select the expression the robot will display at the current point.

(4) Position 4: Edit the voice broadcast content for the robot at the current point.

Enter the content in text form, and the robot will convert the text to voice for broadcast when executing the task. Note that during text input, if the content is formatted incorrectly, the text will be displayed in red. You must adjust it promptly; otherwise, the task cannot be executed.

<figure><img src="../../.gitbook/assets/unknown (309).webp" alt="5.6.2.2 Path-base explanation task - official illustration 85"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 85</p></figcaption></figure>

2\. Special Cases

(1) Scenario Where No Explanation is Needed from the Robot

If a point only requires the robot to arrive without any display, when configuring the corresponding content, select a small-movement action (e.g., nodding), choose the same expression as the previous one, and enter only a single space in the text content field.

(2) Scenario Where a 5th Content Item Needs to Be Added

A 5th content item must be added if any of the following situations apply:

 The explanation content for a single point exceeds 800 characters；  Multiple actions need to be displayed at a single point;；  Multiple expressions need to be displayed at a single point;；  The text content does not match the action duration, requiring the text to be split into multiple segments to align with the action duration.

Specific Operation: Select the \[+] button to add a configuration template for the corresponding point, allowing additional configuration of actions, expressions, and voice broadcast content for the current point (a maximum of 20 segments can be added). Select the \[-] button to delete unnecessary templates.

3\. Adding points

In the current version, you can add any number of points based on specific needs,

<figure><img src="../../.gitbook/assets/unknown (310).webp" alt="5.6.2.2 Path-base explanation task - official illustration 86"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 86</p></figcaption></figure>

corresponding to the number of explanations the robot will give in the actual scene.

After configuring the content for the previous point, select the \[Add point] button to add a new one. The content configuration method is the same for all points.

4\. Add a string Broadcast

<figure><img src="../../.gitbook/assets/unknown (311).webp" alt="5.6.2.2 Path-base explanation task - official illustration 87"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 87</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (312).webp" alt="5.6.2.2 Path-base explanation task - official illustration 87"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 87</p></figcaption></figure>

After the next point is selected, the system will calculate the walking time from the end of the broadcast at the previous point to the movement to the nextpoint.

Select the \[Add a string broadcast] button to enable the robot to broadcast voice while moving to the next point. When adding a string broadcast, pay attention to the following information:

1 Position : The transition script at Position 2 will start broadcasting after a specified interval (5 seconds) following the completion of the task at the previous point.

2 Position 2: Transition script content.

3 Position 3: Broadcast duration of the current transition script (3 seconds).

4 Position 4: Select the \[+] button to add a transition script, or select the \[-] button to delete the current transition script.

5 Position 5: Remaining time until reaching the next point.

6 Position 6: Broadcast interval between multiple transition scripts.

Note: If the total duration of the transition script broadcast plus the interval duration

exceeds the total time required for the robot to reach the next point, the transition script will fail to be added, and some of the scripts must be deleted.

<figure><img src="../../.gitbook/assets/unknown (313).webp" alt="5.6.2.2 Path-base explanation task - official illustration 88"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 88</p></figcaption></figure>

3\. Saving the Task

<figure><img src="../../.gitbook/assets/unknown (314).webp" alt="5.6.2.2 Path-base explanation task - official illustration 89"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 89</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (315).webp" alt="5.6.2.2 Path-base explanation task - official illustration 89"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 89</p></figcaption></figure>

You cannot save the task until its content is fully configured, and the \[Save] button will be grayed out. The \[Save] button can only be clicked to save the task when all task content has been completely configured.

Situations where the task cannot be saved include:

The task can be saved only when all content is completely configured, and the following conditions are met:

<figure><img src="../../.gitbook/assets/unknown (316).webp" alt="5.6.2.2 Path-base explanation task - official illustration 90"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 90</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (317).webp" alt="5.6.2.2 Path-base explanation task - official illustration 90"><figcaption><p>5.6.2.2 Path-base explanation task - official illustration 90</p></figcaption></figure>

After the task is saved, you will be directed to the Task List. You can add or switch tasks in the "Workbench" to allow the robot to execute them.

**5.6.3 Managing Tasks**

1\. Viewing Task Information

Each task label displays 5 items of information as shown in the diagram. When adding a task, you need to check whether the task information is correct:

The map where the task is located.

(2) Position 2: Task name.

<figure><img src="../../.gitbook/assets/unknown (318).webp" alt="5.6.3 Managing Tasks - official illustration 91"><figcaption><p>5.6.3 Managing Tasks - official illustration 91</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (319).webp" alt="5.6.3 Managing Tasks - official illustration 91"><figcaption><p>5.6.3 Managing Tasks - official illustration 91</p></figcaption></figure>

(3) Position 3: Task type.

(4) Position 4: Task number.

(5) Position 5: Last modification time of the task.

2\. Renaming or Deleting a Task

Select the \[···] button at the top-right corner of the task label to rename or delete the task.

Note: In the current version, each robot can store a maximum of 50 tasks. When the

limit is reached, no new tasks can be created, but there is no explicit prompt. Please be mindful of this when using the function.

3\. Viewing Tasks by Map

<figure><img src="../../.gitbook/assets/unknown (320).webp" alt="5.6.3 Managing Tasks - official illustration 92"><figcaption><p>5.6.3 Managing Tasks - official illustration 92</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (321).webp" alt="5.6.3 Managing Tasks - official illustration 92"><figcaption><p>5.6.3 Managing Tasks - official illustration 92</p></figcaption></figure>

After entering the task interface, all tasks saved on the robot are displayed by default. Click the drop-down triangle at the top-left corner of the interface to show all map names in a list. Select a specific map, and only the tasks created on that map will be displayed on the right side

4\. Modifying Task Content

On the task list interface, click a task label to enter the task content details interface and modify the task content. The operation method is the same as that for configuring task content

#### 5.7 Workbench <a href="#id-5-7-workbench" id="id-5-7-workbench"></a>

The workbench primarily monitors the robot’s operational status, including the currently used map, robot health status, and current task. The robot’s autonomous explanation function is enabled by configuring the navigation map and tasks, as well as resolving any abnormal status of the robot

**5.7.1 Autonomous Explanation Function**

Autonomous explanation is one of the robot’s core functions: the robot can independently plan routes in real-world scenarios, provide explanation services to users at specific points, and is accompanied by voice broadcasts, human-like walking gaits, vivid movements, and expressions. It is commonly used in scenarios such as exhibition halls, 4S stores, and science and technology museums.

To execute an autonomous explanation task, the following preparation steps must be completed (specific operations will be detailed later):

Place the robot in the scenario where the explanation task will be performed, and switch it to the \[Human-Like Walking] mode.

A usable task map has been created for the current scenario: all information on the map (such as obstacles and boundaries) matches the real scenario, and points have been added.

<figure><img src="../../.gitbook/assets/unknown (322).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 93"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 93</p></figcaption></figure>

A usable autonomous explanation task has been created: the task is bound to the points on the map, with movements, expressions, and text content configured, and the text content is free of errors.

The specific operations are as follows:

1\. Switching the Navigation Map

<figure><img src="../../.gitbook/assets/unknown (323).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 94"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 94</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (324).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 94"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 94</p></figcaption></figure>

(1) When the robot is turned on and enters Aim-Master for the first time, it will

display the navigation map used in the previous session by default.

(2) Click the drop-down triangle on the right side of the map name to show the

map list, then select the map corresponding to the current real scenario to complete the switch.

2\. Adding a Navigation Task

Note: When adding or switching navigation tasks, avoid connecting to the robot from

multiple terminals. Otherwise, the task will fail to be added (the task will appear in the "Task Management" interface for 1 second and then crash). To resolve this, simply disconnect the other terminal.

<figure><img src="../../.gitbook/assets/unknown (325).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 95"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 95</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (326).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 95"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 95</p></figcaption></figure>

(1) After the robot is turned on, when entering Aim-Master for the first time, the

"Task Management" interface in the bottom-right corner will have no tasks by default.

(2) Select the \[+] button, select the navigation task to be executed, and then click

the task label to add it to the Task Management interface.

3\. Resolving Localization Anomalies

Accurate localization is essential for the robot’s autonomous navigation. For AgiBot A2, the LiDAR does not work at times other than when executing navigation tasks or creating maps, which often leads to the "localization loss" fault. Therefore, it is necessary to resolve localization anomalies before executing navigation tasks.

Localization anomalies can be resolved through manual relocation and automatic relocation. Automatic relocation is recommended for its convenience and efficiency.

Select the \[Relocation] button, and two buttons-\[Manual position] and \[Auto position]-will pop up on the map.

Auto Relocation： Select the \[Auto position] button. The robot will automatically scan the scene;

once it identifies its own position, the icon representing the robot will automatically move to the location on the map that corresponds to the real-world scene.

Note: When using the automatic localization function, you must ensure that the

current map matches the real-world scene to allow the robot to accurately determine its position. If automatic localization fails, the robot will trigger its automatic exploration function and move within a small range in the area to confirm its position.

Please be cautious to avoid damage to the equipment or injury to personnel.

Manual Relocation：

(1) Click \[Manual position]. At this point, the LiDAR will start scanning the

scene and generate a red map.

<figure><img src="../../.gitbook/assets/unknown (327).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 96"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 96</p></figcaption></figure>

(2) Adjust the red map to align with the orange map:

 Drag the icon in the center of the blue circle to move the red map.

 Drag the dark blue dot along the blue circle to adjust the orientation of the red map.

(3) Once you confirm that the red map is aligned with the orange map, click the

\[Complete] button.

(4) If relocation is successful, a prompt will appear at the bottom of the screen,

and the robot’s "Health State" interface in the top-right corner will display "Normal".

<figure><img src="../../.gitbook/assets/unknown (328).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 97"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 97</p></figcaption></figure>

Following the above steps will typically result in successful relocation. If special circumstances arise, refer to the following operations:

(1) If the outline overlap between the red map and the orange map is too low,

relocation will fail. You can try relocation multiple times or move the robot to a different position and attempt relocation again.

(2) If a large number of items have been added to the scene after map creation, it is

recommended to remove these items during relocation; if the items are permanently present, re-scanning the map is advised.

(3) If the scene is too large and its boundaries exceed the LiDAR’s working range,

push the robot to a corner of the scene or an area with more facilities. This provides more reference boundaries to improve the success rate of relocation.

4\. Switching the Robot’s Control Mode

For the robot to execute the autonomous explanation task, its control mode must be set to "Automatic". You can switch the robot to Automatic mode by clicking the mode icon in the status bar.

<figure><img src="../../.gitbook/assets/unknown (329).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 98"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 98</p></figcaption></figure>

1\. Starting/Pausing/Resuming/Ending the Autonomous Explanation Task

(1) Button Switching for Different States of the Route Task and Interface

Display

<figure><img src="../../.gitbook/assets/unknown (330).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 99"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 99</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (331).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 99"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 99</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (332).webp" alt="5.7.1 Autonomous Explanation Function - official illustration 99"><figcaption><p>5.7.1 Autonomous Explanation Function - official illustration 99</p></figcaption></figure>

(2) Starting the Task

 Before the task starts, only the \[Start] button is displayed in the "Task Management" interface, and the task status shows "Not Started".

 Select the \[Start] button to initiate the task. The robot will move and explain autonomously according to the task content, with obstacle avoidance activated during the process.

 After the task starts, the \[Start] button disappears, and \[Pause] and \[End] buttons appear. The task status switches to "In Progress", and the task duration begins to be recorded.

 The task is a one-time task and will end automatically after completion.

(3) Pausing the Task

 After the task starts, select the \[Pause] button to pause the ongoing task. The \[Pause] button switches to a \[Resume] button, and the task status changes to "Paused".

 Once paused, the robot will stop and stay in place.

(4) Resuming the Task

 In the paused state, select the \[Resume] button to continue the task.

 The robot will resume the unfinished explanation task. If the task is paused while the robot is explaining, the unspoken part of the content will be lost after resuming.

(5) Ending the Task

 After the task starts, press the \[End] button to terminate the task.

 Once the task ends, any unfinished parts will no longer be executed.

 Only the \[Start] button remains in the task interface, and the task status switches to "Completed".

**5.7.2 Other Operations**

1\. Switching Tasks

On the Task Management interface, when a navigation task has already been added, select the \[Switch] button to switch tasks. The specific scenarios for different options are as follows:：

(1) If you select another task, the current navigation task will be switched to the

target task；

(2) If you select the task in use, the task content will be refreshed. This is

generally used during task debugging to check in real time how the robot executes the task after the task content is modified.

(3) If you select an empty task, the Task Management interface will be cleared,

and it will return to the initial state.

2\. Voice Control for Autonomous Explanation

(for reference only,the detaild instruction set will be released later) The autonomous explanation function supports voice control, and voice control can be used interchangeably with remote control.

(1) Preparations for Voice Control

Voice control requires the robot to be in a voice-controllable state, which means completing the following preparations. The Aim-Master interface will display the corresponding status as shown:

 The current map matches the real-world scenario.

 There is an executable autonomous explanation task, and it has been added to the "Task Management" interface.

 Localization is accurate.

 The robot’s control mode is set to "Automatic".

 The robot is connected to an external microphone, and all voice commands are issued through this external microphone.

<figure><img src="../../.gitbook/assets/unknown (333).webp" alt="5.7.2 Other Operations - official illustration 101"><figcaption><p>5.7.2 Other Operations - official illustration 101</p></figcaption></figure>

(2) Starting the Task

 Wake up the robot using the voice command "hi,luka"；  Initiate the task with the voice command "Start exhibition hall explanation".

The robot will respond "Okay, please follow me", automatically switch to the \[Human-Like Walking] state, and begin the autonomous explanation task.

(3) Pausing the Task

 During task execution, wake up the robot by saying "hi,luka".

After the robot responds "I’m here", the task will pause automatically, and its state will switch to \[Walk with straight legs and perform upper limb movements].

 The robot can interact with humans while in the paused state.

(4) Resuming the Task

 In the paused state, you can resume the ongoing task (after the robot responds) using either of the following two voice commands:

 Voice command: "Go to the next explanation point" → Robot responds:

"Okay, I will go to the next explanation point".

 Voice command: "Resume task" / "Continue explanation" → Robot responds: "Resuming the task now".

(5) Ending the Task

 Use the voice command "End task". The robot will respond "Canceling the task now" and then terminate the ongoing task.

(6) Voice-Controlled Robot Return to Origin

<figure><img src="../../.gitbook/assets/unknown (334).webp" alt="5.7.2 Other Operations - official illustration 102"><figcaption><p>5.7.2 Other Operations - official illustration 102</p></figcaption></figure>

 Select a point as the origin and name it "init\_place" (this point does not need to be configured in the task).

 When the robot is in a voice-controllable state, wake it up and use the voice command "Return to origin". The robot will respond "I am on my way to the origin", then automatically switch its state and head to the origin.

 After reaching the origin, the robot will respond "I have arrived at the navigation point".

 The robot can be interrupted by voice during the journey: after interruption, it will stop in place, and you need to repeat the "return to origin" operation for it to continue heading to the origin.

#### 5.8 Settings <a href="#id-5-8-settings" id="id-5-8-settings"></a>

The Settings function is mainly used to modify the configurations of the robot and Aim-Master.

**5.8.1 Wireless Local Area Network (WLAN)**

This section allows configuration of the network connection for the robot’s Orin industrial computer: click the wireless network you want to connect to, enter the password, and select the \[Join] button to establish the connection.

After the network is connected, the robot’s IP address (Orin) will be displayed.

<figure><img src="../../.gitbook/assets/unknown (335).webp" alt="5.8.1 Wireless Local Area Network (WLAN) - official illustration 103"><figcaption><p>5.8.1 Wireless Local Area Network (WLAN) - official illustration 103</p></figcaption></figure>

This supports Aim-Master connecting to the robot via the IP address.

**5.8.2 Mobile Network**

<figure><img src="../../.gitbook/assets/unknown (336).webp" alt="5.8.3 Authorization Password - official illustration 104"><figcaption><p>5.8.3 Authorization Password - official illustration 104</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (337).webp" alt="5.8.3 Authorization Password - official illustration 104"><figcaption><p>5.8.3 Authorization Password - official illustration 104</p></figcaption></figure>

This function supports using an IoT SIM card instead of external WiFi. It is currently under development; please stay tuned.

**5.8.3 Authorization Password**

This section allows you to modify the password used to connect to the robot via

IP. The default password is 02270227, and it is recommended to change it as soon as the robot is put into use.

<figure><img src="../../.gitbook/assets/unknown (338).webp" alt="5.8.3 Authorization Password - official illustration 105"><figcaption><p>5.8.3 Authorization Password - official illustration 105</p></figcaption></figure>

**5.8.4 Display**

<figure><img src="../../.gitbook/assets/unknown (339).webp" alt="5.8.4 Display - official illustration 106"><figcaption><p>5.8.4 Display - official illustration 106</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (340).webp" alt="5.8.4 Display - official illustration 106"><figcaption><p>5.8.4 Display - official illustration 106</p></figcaption></figure>

This function controls the display of the status bar on the robot’s face (tablet). It is disabled by default; when enabled, it will show status information such as battery level and WiFi connection status.

The following is the robot’s facial display under different states (when the facial status bar is disabled and enabled):

**5.8.5 Voice**

**5.8.5.1 Facial Display of the Robot Under Different Status Bar Modes**

<figure><img src="../../.gitbook/assets/unknown (341).webp" alt="5.8.5.1 Facial Display of the Robot Under Different Status Bar Modes - official illustration 107"><figcaption><p>5.8.5.1 Facial Display of the Robot Under Different Status Bar Modes - official illustration 107</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (342).webp" alt="5.8.5.1 Facial Display of the Robot Under Different Status Bar Modes - official illustration 107"><figcaption><p>5.8.5.1 Facial Display of the Robot Under Different Status Bar Modes - official illustration 107</p></figcaption></figure>

When the facial status bar is disabled, the robot’s face (tablet) only shows the default interactive interface (e.g., static/dynamic avatar, welcome messages) without any system status information, keeping the visual appearance concise and focused on user interaction.

Silent mode does not affect the robot’s voice broadcast function or the volume of the broadcast sound.

**5.8.5.2 Microphone Type**

The default setting is the built-in microphone (the robot's own microphone).

Voice interaction supports connecting an external microphone. An external lapel microphone is provided with the robot as standard. When using it, you need to switch to the external microphone.

You can also purchase an external microphone separately. When using it, insert the USB receiver into the robot’s debugging compartment, and the microphone type here will switch automatically.

**5.8.5.3 Identify language**

Chinese and English recognition are supported, with Chinese set as the default.

Generally, no manual switching is required-the robot will actively recognize the language: it uses Chinese for interaction when Chinese is detected, and English when English is detected.

**5.8.5.4 Face Recognition\&Face Following**

To enable this feature, the user’s facial data must first be collected and registered in the backend system. Once enrolled, whenever the registered user appears in front of the robot, face recognition is triggered: the robot greets the user proactively and turns

<figure><img src="../../.gitbook/assets/unknown (343).webp" alt="5.8.5.4 Face Recognition&#x26;Face Following - official illustration 108"><figcaption><p>5.8.5.4 Face Recognition&#x26;Face Following - official illustration 108</p></figcaption></figure>

its head to follow the person’s face.

If you wish to use this capability, please contact a Zhiyuan representative.

**5.8.5.5 Extended Listening time**

This refers to the interval for voice interaction after the robot is awakened once, with a default of 60 seconds. That is, after one awakening, there is no need to reawaken the robot for interaction within 60 seconds, and the time resets with each interaction. If there is no interaction for more than 60 seconds, this interaction session will end, and reawakening will be required for subsequent voice interactions.

You can set the interval here, and there are currently 3 options available: 10s, 30s, and 60s

**5.8.6 Volume**

This function is used to adjust the volume of the robot’s voice broadcast.

**5.8.7 Real time scanning of maps**

This function is enabled by default: after each successful positioning, map scanning will start, which is used to detect whether there are differences between the current map and previous maps. When there is a discrepancy between the new and old

<figure><img src="../../.gitbook/assets/unknown (344).webp" alt="5.8.7 Real time scanning of maps - official illustration 109"><figcaption><p>5.8.7 Real time scanning of maps - official illustration 109</p></figcaption></figure>

map layers, an "Update Map" button will appear on the map editing interface-you can click it to automatically update the map.

**5.8.8 Upper limb movements**

This function supports the robot’s upper limb collision detection and is disabled by default.

When enabled, all movements of the upper limbs will start real-time sensing of joint changes to detect potential collision risks. Once the system detects a collision risk, it will automatically stop the upper limb movements.

You can enable or disable this function according to actual needs.

<figure><img src="../../.gitbook/assets/unknown (345).webp" alt="5.8.8 Upper limb movements - official illustration 110"><figcaption><p>5.8.8 Upper limb movements - official illustration 110</p></figcaption></figure>

The figure below shows the feedback on the remote control after a collision is detected: the robot will stop interactive movements and maintain its current posture. It can be restored by clicking the \[Action Reset] button, replaying the movement, or voice wake-up.

<figure><img src="../../.gitbook/assets/unknown (346).webp" alt="5.8.8 Upper limb movements - official illustration 111"><figcaption><p>5.8.8 Upper limb movements - official illustration 111</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (347).webp" alt="5.8.8 Upper limb movements - official illustration 111"><figcaption><p>5.8.8 Upper limb movements - official illustration 111</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (348).webp" alt="5.8.8 Upper limb movements - official illustration 111"><figcaption><p>5.8.8 Upper limb movements - official illustration 111</p></figcaption></figure>

**5.8.9 About**

You can view various information of the robot, including its name, model, SN (Serial Number), system version, Aim-Master version, and Aim-Master language.

The language section allows you to set the display language of Aim-Master, and currently only Simplified Chinese and English are supported.

#### 5.9 Notifications <a href="#id-5-9-notifications" id="id-5-9-notifications"></a>

This section displays the robot’s health status and historical reports, and allows you to dismiss certain anomalies.

From the “Health state” screen on the workbench, tap any anomaly to jump directly to the Notifications page.

For each anomaly, tap \[Clearing faults] on the right to attempt an automatic fix. If the issue persists, tap \[Solution] to view troubleshooting steps. If the problem still cannot be resolved independently, contact Zhiyuan technical support.

<figure><img src="../../.gitbook/assets/unknown (349).webp" alt="5.9 Notifications - official illustration 112"><figcaption><p>5.9 Notifications - official illustration 112</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (350).webp" alt="5.9 Notifications - official illustration 113"><figcaption><p>5.9 Notifications - official illustration 113</p></figcaption></figure>

### Secondary Development <a href="#secondary-development" id="secondary-development"></a>

### 1. A2 Ultra Overview <a href="#web-01-1-a2-ultra-overview" id="web-01-1-a2-ultra-overview"></a>

#### 1.1 Component Description <a href="#web-01-1-1-component-description" id="web-01-1-1-component-description"></a>

<figure><img src="../../.gitbook/assets/unknown (351).webp" alt="1.1 Component Description"><figcaption><p>1.1 Component Description</p></figcaption></figure>

#### 1.2 Robot Specifications <a href="#web-01-1-2-robot-specifications" id="web-01-1-2-robot-specifications"></a>

| **Primary Category**          | **Secondary Category**         | **Item**                                      | **Specific Content**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------------- | ------------------------------ | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Product Basic Information** |                                | Height                                        | 169cm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                               |                                | Dimensions                                    | 169(H)×75(W)×30(L)cm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|                               |                                | Net Weight                                    | ≈69kg                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **Product Features**          | **Electrical Performance**     | Battery Life                                  | Whole machine force control standing + voice broadcast: about 3 hours. Machine walking on flat ground with straight legs: about 1.5 hours.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|                               |                                | Battery Capacity                              | 14.4Ah                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                               |                                | Charging Time                                 | 2h                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                               |                                | Charging Power                                | ≤500W                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                               | **Environmental Adaptability** | Operating Temperature and Humidity            | 0\~ 40℃, relative humidity 10% \~ 90%, no condensation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                               |                                | Storage Temperature and Humidity              | -20℃\~ 70℃, relative humidity 10% \~ 90%, no condensation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|                               |                                | IP Rating                                     | Joint Module: IP5X                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                               | **Site Adaptability**          | Minimum Passage Width                         | Currently, the minimum width for remote control passage is >1m, and the minimum width for navigation passage is >2m                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|                               |                                | Maximum Obstacle Height                       | 20mm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|                               | **Safety**                     | Arm Collision Sensing                         | Supported                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|                               |                                | Maximum Obstacle Avoidance Detection Distance | 5m                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|                               |                                | Minimum Obstacle Avoidance Detection Height   | 30cm                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|                               | **Operation and Interaction**  | Remote Control Operation                      | Wireless Remote Controller                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|                               |                                | Interaction Screen                            | Facial interaction screen with emoticon display function Module overall dimensions: 105.50 × 67.20 × 3.0 mm (including frame) Actual display area: 95.04 × 53.86 mm Screen size: 4.3 inches Screen resolution: 800 × 480 pixels Brightness: 500 cd/m² Contrast: typical 1500:1, minimum 1000:1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|                               |                                | Speaker                                       | Dual 5W                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                               |                                | Indicator Light                               | Multi-color ambient light                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **Product Capabilities**      | **Perception Capabilities**    | Environmental Perception                      | LiDAR: For collecting surrounding information, used for mapping and navigation. Parameters: Range: 0.2 - 40 m @ 10% reflectivity, 0.2 - 70 m @ 80% reflectivity, FOV: H: 360, V: -7～52, Ranging Error: 2 cm @ 10 m. RGBD Camera (Head) for target detection. Parameters: Depth map resolution: up to 1280x720, 640x480, Depth detection range: 0.3\~ 10 m, FOV: HFOV: 65° ± 2°, VFOV: 40° ± 1°. RGB Camera (Chest) for target detection. Parameters: FOV: H196V154, Resolution: 1920Hx1536V. RGBD Camera (Groin) for target detection. Parameters: Depth map resolution: 640 x 400@5/10/15fps, Depth detection range: Normal mode 0.15-3m, High mode 0.15-5m, FOV: HFOV: RGB FOV: 16:9: H86° V55°. Fisheye Camera (Left/Right Chest) for forward perception. Parameters: FOV: H196V154, Resolution: 1920Hx1536V |
|                               | **Navigation Capabilities**    | Positioning Accuracy                          | ±10cm, ±10°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|                               |                                | Navigation and Obstacle Avoidance             | Supports real-time autonomous navigation and obstacle avoidance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|                               |                                | Movement Modes                                | Supports forward, left turn, right turn                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                               | **IoT Capabilities**           | Communication Protocols                       | TCP, IP                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                               |                                | Communication Modules                         | WiFi, Cellular Network                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                               | **Arm Typical Parameters**     | Dexterous Hand Delivery Capability            | <p>Grasping weight (palm down): &#x3C;3kg<br>Hook grip weight (palm up): &#x3C;8kg</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                               |                                | Maximum Load for Arm (with Dexterous Hand)    | 2kg                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|                               |                                | Arm Workspace                                 | J1(Shoulder pitch): ±170°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|                               |                                |                                               | J2(Shoulder roll): -30°\~95°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|                               |                                |                                               | J3(Shoulder yaw): ±170°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|                               |                                |                                               | J4(Elbow pitch): -1°\~118°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|                               |                                |                                               | J6(Wrist pitch): ±45°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|                               |                                |                                               | J7(Wrist yaw): ±30°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|                               | **Typical Leg Parameters**     | Leg workspace (with some deviation)           | J1(Hip roll): -37\~40°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|                               |                                |                                               | J2(Hip yaw): ±75°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|                               |                                |                                               | J4(Knee pitch): -5°\~140°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|                               |                                |                                               | J5(Ankle pitch): -30°\~52°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|                               |                                |                                               | J6(Ankle roll): ±28°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|                               | **Typical Head Parameters**    | Head Movement Range                           | Pitch joint: ±23°                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

#### 1.3 Industrial PC Specifications <a href="#web-01-1-3-industrial-pc-specifications" id="web-01-1-3-industrial-pc-specifications"></a>

The A2 Ultra robot is pre-installed with two upper-level development boards, which communicate directly via Ethernet. One of the boards is for the cerebellum control and is not allowed to be modified; the other is the brain development board, using Nvidia Jetson AGX Orin 64 GB. The specifications can be found in the [Nvidia official documentation](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/).

#### 1.4 Whole Machine Workspace <a href="#web-01-1-4-whole-machine-workspace" id="web-01-1-4-whole-machine-workspace"></a>

Calculated from the center point of the wrist joint

<figure><img src="../../.gitbook/assets/unknown (352).webp" alt="Calculated from the center point of the wrist joint"><figcaption><p>Calculated from the center point of the wrist joint</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (353).webp" alt="Calculated from the center point of the wrist joint"><figcaption><p>Calculated from the center point of the wrist joint</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (354).webp" alt="Calculated from the center point of the wrist joint"><figcaption><p>Calculated from the center point of the wrist joint</p></figcaption></figure>

#### 1.5 Network Topology <a href="#web-01-1-5-network-topology" id="web-01-1-5-network-topology"></a>

The A2 robot has two different hardware models, with different suppliers and hardware designs, resulting in different network topologies. These are referred to as the T3 model and the P1 model.

You can determine the model by checking the network interface names using the `ip a` command on the actual machine.

**1.5.1 T3 Model**

Hardware architecture diagram

<figure><img src="../../.gitbook/assets/unknown (355).webp" alt="Hardware architecture diagram"><figcaption><p>Hardware architecture diagram</p></figcaption></figure>

Software network topology diagram

<figure><img src="../../.gitbook/assets/unknown (356).webp" alt="Software network topology diagram"><figcaption><p>Software network topology diagram</p></figcaption></figure>

Where:

* The left debug network port is for the orin debugging, with a fixed IP of 192.168.2.50. The right debug network port is for x86 debugging, using DHCP mode.

**1.5.2 P1 Model**

Hardware architecture diagram

<figure><img src="../../.gitbook/assets/unknown (357).webp" alt="Hardware architecture diagram"><figcaption><p>Hardware architecture diagram</p></figcaption></figure>

Software network topology diagram

<figure><img src="../../.gitbook/assets/unknown (358).webp" alt="Software network topology diagram"><figcaption><p>Software network topology diagram</p></figcaption></figure>

Where:

* The left debug network port is for the orin debugging, with a fixed IP of 192.168.2.50. The right debug network port is for x86 debugging, using DHCP mode.

**1.5.3 Network NAT Configuration**

Starting from software version V1.2, due to hardware and software architecture reasons, the default network policy of the robot has been adjusted to disable the ORIN's own WiFi and instead use the x86 WiFi for NAT internet access. The policy details are as follows:

1. When the X86 WiFi is enabled, the ORIN module's internet traffic defaults to flow through the 192.168.100.1 gateway to the X86 for NAT internet access.
2. When the X86 WiFi is disabled, the ORIN's external internet traffic defaults to flow through the 5G module. If the 5G module does not have a SIM card or no network, it will not be able to connect to the internet.

This network policy brings up an issue where users cannot directly access services on the ORIN. To address this, we provide two solutions:

1. You can connect to the ORIN's AP hotspot. The default password can be found in the `password.md` file in the AimDK package. This allows direct access to the ORIN hotspot IP.
2.  You can configure port forwarding on the X86, accessing the corresponding port on the X86 to forward to the ORIN's corresponding port. The configuration file is located at `/opt/orin_use_x86_wifi/x86_cfg.sh` on the X86. An example of the forwarding entry is as follows (the network interface names may differ for different models, but the principle is similar):bash

    <pre data-collapsed-line-count="10"><code>sudo iptables -t nat -A PREROUTING -i wifi_x86 -p tcp --dport 51056 -j DNAT --to-destination 192.168.100.110:51056
    sudo iptables -t nat -A POSTROUTING -d 192.168.100.110 -p tcp --dport 51056 -j SNAT --to-source 192.168.100.100
    </code></pre>

    \
    New forwarding entries can be added to modify the forwarding and destination ports to support more port forwarding.

#### 1.6 Camera Views <a href="#web-01-1-6-camera-views" id="web-01-1-6-camera-views"></a>

The A2 Pro is equipped with RGB-D cameras on the head and waist, and a fisheye camera on the chest. For exact locations, please refer to the component descriptions in the Overview section of this document.

*   FOV DiagramsSide\
    Side view diagram of the head/waist RGB-D camera FOV:<br>

    <figure><img src="../../.gitbook/assets/unknown (359).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

    \
    Front view diagram of the head/waist RGB-D camera FOV:<br>

    <figure><img src="../../.gitbook/assets/unknown (360).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

    \
    Top-down view diagram of the head/waist RGB-D camera and chest fisheye camera FOV:<br>

    <figure><img src="../../.gitbook/assets/unknown (361).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

Diagram of the Fisheye Camera's FOV after Distortion Correction\
Diagram of the Fisheye Camera's FOV before Distortion Correction：<br>

<figure><img src="../../.gitbook/assets/unknown (362).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

\
Diagram of the fisheye camera's FOV after distortion correction. The field of view represented in this diagram is used for the fisheye camera in practical applications.<br>

<figure><img src="../../.gitbook/assets/unknown (363).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

\
The distortion correction was performed using scatter points at a distance of 2m from the Baselink, with a vertical resolution of 5cm per point and a horizontal angular resolution of 5 degrees. The comparison of the effect before and after distortion correction is shown in the figure below: Before Distortion CorrectionAfter Distortion Correction

<figure><img src="../../.gitbook/assets/unknown (364).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (365).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

### 2. Overview of the Software System <a href="#web-02-2-overview-of-the-software-system" id="web-02-2-overview-of-the-software-system"></a>

#### 2.1 Basic Startup Mode <a href="#web-02-2-1-basic-startup-mode" id="web-02-2-1-basic-startup-mode"></a>

The robot is equipped with an x86\_64 architecture industrial PC and an arm64 architecture AGX Jetson Orin industrial PC, referred to as x86 and orin, respectively. Both are installed with Ubuntu 22.04 and use systemd as the system service manager. Both are configured with `agibot_em.service` as the entry point for the Agibot software system. This service starts automatically on boot and launches the EM (process startup management) and SM (process status management) modules. The EM and SM then work together to start the remaining module processes. The SM manages the startup and shutdown states of the process list under different system modes (to avoid issues with shared memory resource anomalies caused by process start and stop, since version 1.3, the system mode switching no longer turns processes on and off but instead calls the activate and deactivate interfaces of the processes, which remain active).

The configuration file paths for EM and SM are `/agibot/software/v0/entry/bin/cfg/run_agibot.yaml` (for x86 & orin) and `/agibot/software/v0/entry/bin/cfg/sm.yaml` (for x86), respectively. The former lists the default processes to be started, while the latter lists which functional groups of processes are enabled under each system mode.

#### 2.2 Module Function Overview <a href="#web-02-2-2-module-function-overview" id="web-02-2-2-module-function-overview"></a>

Some modules exist on both orin and X86, with a suffix of 1 for orin and 0 for X86.

| Module Type                                       | Industrial PC |                                                                                | Name                                       | Description / Function                                                                                                                                                                                                              |
| ------------------------------------------------- | ------------- | ------------------------------------------------------------------------------ | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SoC External Devices                              |               | AimMaster                                                                      | Client Software                            | Used to operate and control the robot’s basic functions                                                                                                                                                                             |
|                                                   |               | OMP                                                                            | Zhiyuan Cloud Platform                     | Responsible for receiving and reporting edge-side embedded data                                                                                                                                                                     |
|                                                   |               | VR                                                                             | Virtual Reality Device                     | Used for robot teleoperation                                                                                                                                                                                                        |
|                                                   |               | MCU                                                                            | Microcontroller Unit                       | Controls robot motors at the lower level; receives motor and IMU data; communicates upward with HAL EtherCAT to receive control commands and upload motor and IMU data                                                              |
| <p>Common Services<br>Infrastructure Services</p> | ORIN          | MQTT broker (mosquitto)                                                        | MQTT Gateway                               | MQTT gateway node, interfacing with AimMaster and onboard software                                                                                                                                                                  |
|                                                   |               | data\_exporter                                                                 | Log Export Service                         | Provides batch and time-range log export capabilities                                                                                                                                                                               |
|                                                   | ORIN & X86    | iox\_roudi                                                                     | Iceoryx Shared Memory Daemon               | Central scheduling node for iceoryx communication, providing shared memory storage locations                                                                                                                                        |
|                                                   |               | setting                                                                        | Settings Module                            | Provides basic industrial PC settings such as Wi-Fi and Bluetooth                                                                                                                                                                   |
|                                                   |               | recordbag                                                                      | Bag Recording                              | Continuously records bag files                                                                                                                                                                                                      |
|                                                   |               | reboot                                                                         | Reboot Command                             | Performs system reboot when invoked by SM                                                                                                                                                                                           |
|                                                   |               | poweroff                                                                       | Power-off Command                          | Executes system shutdown when invoked by SM                                                                                                                                                                                         |
| Management Modules                                | X86           | SM                                                                             | System State Management Module             | Responsible for switching system states and managing the process list                                                                                                                                                               |
|                                                   | ORIN & X86    | EM                                                                             | Process Management Module                  | Responsible for launching processes and querying process status                                                                                                                                                                     |
| Functional Modules                                | X86           | <p>sota_ota<br>ota_gateway<br>ota_master</p>                                   | OTA Functional Modules                     | Responsible for downloading OTA packages and executing OTA workflows                                                                                                                                                                |
|                                                   |               | hal\_ethercat                                                                  | Hardware Abstraction Layer                 | Handles EtherCAT communication with the MCU, transmitting hardware status and control commands                                                                                                                                      |
|                                                   |               | mc                                                                             | Motion Control Module                      | Responsible for overall robot motion control and issuing motion commands                                                                                                                                                            |
|                                                   |               | motion\_streamer                                                               | Motion Streaming Module                    | Dedicated to teleoperation, mapping VR motion-capture suit data to robot motions                                                                                                                                                    |
|                                                   |               | rc                                                                             | Remote Control Module                      | Provides interfaces for AimMaster to call robot basic functions and status, and records related information into logs                                                                                                               |
|                                                   |               | motion\_player                                                                 | Motion Playback Module                     | Responsible for solving, mapping, and playing specified motion files                                                                                                                                                                |
|                                                   |               | tf                                                                             | Coordinate Transformation Module           | Provides coordinate transformation services                                                                                                                                                                                         |
|                                                   |               | fota\_slave                                                                    | Firmware Upgrade Module                    | Responsible for FOTA upgrade processes                                                                                                                                                                                              |
|                                                   |               | health\_monitor                                                                | Health Monitoring Module                   | Monitors the health of all business modules and underlying hardware                                                                                                                                                                 |
|                                                   |               | legged\_odometry                                                               | Perception & Localization Module           | Reads joint angles of each leg and IMU data to compute the robot pose, and sends it to navigation or control modules                                                                                                                |
|                                                   |               | open\_long\_server                                                             | Persistent Connection Service              | Maintains a 24-hour persistent connection, allowing external devices to remotely control the robot, issue real-time motion commands, or retrieve logs                                                                               |
|                                                   |               | hds                                                                            | Health Diagnosis Service                   | Receives fault reports from various modules                                                                                                                                                                                         |
|                                                   | ORIN          | hal\_audio                                                                     | Audio Playback Module                      | Provides atomic audio playback capability for agent invocation                                                                                                                                                                      |
|                                                   |               | agent                                                                          | Voice Intelligent Agent Module             | Executes voice large language models, handles cloud interaction logic, and issues speech, motion, and expression commands                                                                                                           |
|                                                   |               | task\_engine                                                                   | Task Management Module                     | Responsible for executing tasks created by AimMaster                                                                                                                                                                                |
|                                                   |               | pnc                                                                            | Planning and Navigation Control Module     | Responsible for navigation path planning                                                                                                                                                                                            |
|                                                   |               | <p>slam<br>agivslam</p>                                                        | Mapping and Localization Module            | Responsible for mapping and localization                                                                                                                                                                                            |
|                                                   |               | mm                                                                             | Map Management Module                      | Handles map data loading and parsing, map fusion, and map updates                                                                                                                                                                   |
|                                                   |               | <p>perception<br>perception_object<br>perception_qr</p>                        | Perception Modules                         | Collects and processes navigation-related sensor data for pnc and operation modules                                                                                                                                                 |
|                                                   |               | <p>hal_dcw2<br>hal_d415<br>hal_lidar<br>hal_xinying (T3)<br>tz_camera (P1)</p> | Sensor Driver Modules                      | Loads camera and sensor drivers and publishes raw image frames via ROS 2 topics                                                                                                                                                     |
|                                                   |               | gateway                                                                        | External Gateway Communication             | Forwards external requests to internal modules                                                                                                                                                                                      |
|                                                   |               | data\_proxy                                                                    | Data Transfer Module                       | Packages robot logs, status, video streams, and files for on-demand forwarding to cloud, host PC, or debugging tools; also distributes external upgrade packages, motion files, and configuration commands to corresponding modules |
|                                                   |               | <p>colistener<br>coencoder<br>cobridge</p>                                     | Data Closed-loop Modules                   | Responsible for closed-loop data interaction between the robot and cloud                                                                                                                                                            |
|                                                   |               | embodied\_agent                                                                | Embodied Intelligence Orchestration Module | The core intelligent controller of the robot, enabling it to understand, reason, and act correctly to accomplish high-level tasks                                                                                                   |
|                                                   |               | manipulator                                                                    | Embodied Execution Module                  | Provides low-level atomic capabilities such as grasping and dispatching                                                                                                                                                             |
|                                                   |               | skillpilot                                                                     | Skill Scheduling Module                    | Unified management, arbitration, and scheduling of robot basic skills                                                                                                                                                               |
|                                                   |               | resource\_manager                                                              | Resource Management Module                 | Unified management of onboard motion, expression, and audio resource files                                                                                                                                                          |

text

{% code collapsedlinecount="10" %}
```
                                                                                                                                          |
```
{% endcode %}

**2.2.1 System Mode**

The modules activated and started in each system mode are different, as shown below (excerpt from sm.yaml).

python

{% code collapsedlinecount="10" %}
````
  # System status
  system_modes:
    "Startup":
      next_mode_list: [ "Ready", "OTA", "Poweroff" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "RC", "MoCap", "Gateway", "Perception", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]

    "Poweroff":
      next_mode_list: []
      active_FG_list: []
      action_list:
        - [ open Poweroff ]

    "Reboot":
      next_mode_list: []
      active_FG_list: []
      action_list:
        - [ open Reboot ]

    # The system's ready state, which starts the business management module and HAL
    "Ready":
      next_mode_list: [ "Manual", "EStop", "Poweroff" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ activate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ deactivate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
        - [ activate motion_player ]
      # post_process:
      #   - level: 34
      #     action_list: [ [ forbid Manual ] ]

    # OTA state, which starts the OTA functional group to complete OTA-related functions
    "OTA":
      next_mode_list: [ "Reboot", "Ready", "Poweroff" ]
      active_FG_list: [ "System", "HAL", "Manager", "SLAM", "RC", "MoCap", "Gateway","Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ deactivate agent ]
        - [ deactivate pnc ]
        - [ deactivate mc ]
        - [ deactivate slam ]
        - [ deactivate perception ]
        - [ deactivate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
        - [ deactivate motion_player ]

    # Manual state, which starts the RC and MC functional groups
    "Manual":
      next_mode_list: [ "OTA", "Auto", "Reset", "EStop", "Calibration", "Poweroff", "MotionStream", "DataCollection", "FreeExploration", "Mapping", "Manipulator" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ activate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ activate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
        - [ activate motion_player ]
      child_modes:
        - mode_name: "Safety"  # State entered by calling the enable script under tools
          extra_next_modes: [ "OTA", "Reset" ]
          action_list:
            - [ deactivate rc ]
            - [ close Motion ]
            - [ close EStop ]
      post_process:
        - level: 47
          action_list: [ [ fallback mc ] ]

    # Mapping state
    "Mapping":
      next_mode_list: [ "Manual" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ activate mc ]
        - [ activate slam ]
        - [ deactivate perception ]
        - [ activate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
        - [ activate motion_player ]

    # Auto state, which starts the task engine and all business functional groups
    "Auto":
      next_mode_list: [ "Manual", "EStop", "Poweroff", "FreeExploration" ]
```      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ activate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ deactivate rc ]
        - [ activate task_engine ]
        - [ activate motion_player ]
      child_modes:
        - mode_name: "Safety"
          extra_next_modes: [ "OTA", "Reset" ]
          action_list:
            - [ deactivate task_engine ]
            - [ close Motion ]
            - [ close EStop ]
      # post_process:
      #   # - level: 47
      #   #   action_list: [ [ MAID ] ]
      #   # - level: 43
      #   #   action_list: [ [ fallback motion_player ], [ fallback task_engine XXModule B ], [ Move Manual ] ]
      #   # - level: 40
      #   #   action_list: [ [ MAID ] ]
      #   - level: 37
      #     action_list: [ [ fallback task_engine ], [ move Manual ] ]
      #   - level: 34
      #     action_list: [ [ fallback task_engine, fallback mc ] ]
      #   # - level: 31
      #   #   action_list: [ [ MAID ] ]

    # Embodied Operation Mode
    "Manipulator":
      next_mode_list: [ "OTA", "Reset", "EStop", "Poweroff", "FreeExploration", "Manual" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ activate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ activate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
        - [ deactivate motion_player ]

    # Free Exploration Mode
    "FreeExploration":
      next_mode_list: [ "Manual", "EStop", "Poweroff", "Auto" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ activate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ deactivate rc ]
        - [ activate task_engine ]
        - [ activate motion_player ]
      child_modes:
        - mode_name: "Safety"
          extra_next_modes: [ "OTA", "Reset" ]
          action_list:
            - [ deactivate task_engine ]
            - [ close Motion ]
            - [ close EStop ]

    # Reset State, used for restoring factory settings
    "Reset":
      next_mode_list: [ "Reboot", "Poweroff" ]
      active_FG_list: [ "System", "OTA", "Gateway" ]
      action_list:
        - [ DIFF ]

    # Emergency Stop State, used for emergency stop
    "EStop":
      next_mode_list: [ "Ready", "OTA", "Poweroff" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ deactivate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ deactivate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
        - [ activate motion_player ]

    # Safety State, used for safety state
    # "Safe":
    #   next_mode_list: [ "Manual", "EStop", "Poweroff" ]
    #   active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoCap", "Gateway", "Perception", "Motion" ]
    #   action_list:
    #     - [ DIFF ]
    #     - [ deactivate mc, deactivate rc ]

    # Real-time Remote Operation State, used for real-time remote operation```yaml
    "MotionStream":
      next_mode_list: [ "Manual", "EStop", "Poweroff", "RemoteMotionStream", "DataCollection" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoStream", "Gateway", "Motion", "Perception", "OTA" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ deactivate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ activate rc ]
        - [ deactivate task_engine TaskMaster cancel ]

    "RemoteMotionStream":
      next_mode_list: [ "Manual", "EStop", "Poweroff", "MotionStream" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoStream", "Gateway", "Motion", "Perception", "OTA", "RTC" ]
      action_list:
        - [ deactivate tz_camera ]
        - [ deactivate hal_d415 ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ DIFF ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ deactivate mc ]
        - [ activate slam ]
        - [ activate perception ]
        - [ activate rc ]
        - [ deactivate task_engine TaskMaster cancel ]

    # Calibration state, used for calibration, enter upon client request for calibration
    "Calibration":
      next_mode_list: [ "Ready" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "Gateway", "Motion", "Perception", "OTA", "Calibration" ]
      action_list:
        - [ DIFF ]
        - [ activate recordbag0 ]
        - [ activate recordbag1 ]
        - [ activate tz_camera ]
        - [ activate hal_d415 d415 Calibration ]
        - [ deactivate agent ]
        - [ deactivate pnc ]
        - [ deactivate mc ]
        - [ deactivate slam ]
        - [ deactivate perception ]
        - [ deactivate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
      # post_process:
      # #   - level: 43
      # #     action_list: [ [ fallback calibration ] ]
      # #   - level: 37
      # #     action_list: [ [ fallback calibration ] ]
      #   - level: 34
      #     action_list: [ [ fallback task_engine, fallback mc ] ]

    "DataCollection":
      next_mode_list: [ "Manual", "EStop", "Poweroff", "MotionStream" ]
      active_FG_list: [ "System", "HAL", "EStop", "Manager", "SLAM", "RC", "MoStream", "Gateway", "Motion", "Perception", "OTA", "Data_Collector" ]
      action_list:
        - [ DIFF ]
        - [ deactivate recordbag0 ]
        - [ deactivate recordbag1 ]
        - [ activate tz_camera tzcamera DataCollection ]
        - [ activate hal_d415 d415 DataCollection ]
        - [ activate agent ]
        - [ activate pnc ]
        - [ deactivate mc ]
        - [ activate slam ]
        - [ deactivate perception ]
        - [ activate rc ]
        - [ deactivate task_engine TaskMaster cancel ]
````
{% endcode %}

**2.2.2 Module Disabling Method (Caution)**

Due to the numerous features, ORIN now has a high load. If you need to replace certain functional modules through secondary development, you must configure the system so that the module does not start.

Modules are managed in two ways, depending on whether they are controlled by `run_agibot.yaml` (x86 & orin) or `sm.yaml` (orin). Modules managed by the former will start by default at startup and remain resident, unaffected by `sm` management. Modules managed by the latter will switch between different system modes.

1. If you need to disable a module managed by `run_agibot.yaml` (i.e., part of `default_apps`), simply remove it from `default_apps`.
2. If you need to disable a module managed by `sm`, add a line with `deactivate` in the corresponding system mode to specify the module to be disabled.

Taking the motion\_play module as an example, follow the steps below to disable it. First, remove the motion\_play module from the default\_apps list in run\_agibot.yaml (x86):

diff

{% code collapsedlinecount="10" %}
```
@@ -20,7 +20,6 @@ process_manager:
     "iox_roudi",
     "hal_ethercat",
     "recordbag0",
-    "motion_player",
     "ota_gateway",
     "ota_master",
     "fota_slave",
```
{% endcode %}

Then, remove motion\_player from the group in SystemManagerModule within sm.yaml (orin), update the MoCap configuration to empty, and remove the activate / deactivate operations for motion\_player in all states.

diff

{% code collapsedlinecount="10" %}
```
@@ -14,7 +14,7 @@ SystemManagerModule:
-      group: [ota_master, motion_player, motion_streamer, sota_slave0, mc, tf, dr, rc, hal_ethercat, poweroff0, reboot0, setting0, recordbag0, data_collector, health_monitor0]
+      group: [ota_master, motion_streamer, sota_slave0, mc, tf, dr, rc, hal_ethercat, poweroff0, reboot0, setting0, recordbag0, data_collector, health_monitor0]
       url: "http://${AGIBOT_NEIGHBOR_HOST_IP}:50081"
```
{% endcode %}

diff

{% code collapsedlinecount="10" %}
```
@@ -40,7 +40,7 @@ SystemManagerModule:
     "RC":
       [ "rc" ]
     "MoCap":
-      [ "motion_player" ]
+      []
     "MoStream":
       [ "motion_streamer" ]
```
{% endcode %}

diff

{% code collapsedlinecount="10" %}
```
    "Ready":
@@ -100,7 +100,6 @@ SystemManagerModule:
         - [ activate perception ]
         - [ deactivate rc ]
         - [ deactivate task_engine TaskMaster cancel ]
-        - [ activate motion_player ]
    "OTA":
@@ -122,7 +121,6 @@ SystemManagerModule:
         - [ deactivate perception ]
         - [ deactivate rc ]
         - [ deactivate task_engine TaskMaster cancel ]
-        - [ deactivate motion_player]
    "Manual":
@@ -140,7 +138,6 @@ SystemManagerModule:
         - [ activate perception ]
         - [ activate rc ]
         - [ deactivate task_engine TaskMaster cancel ]
-        - [ activate motion_player ]
    "Mapping":
@@ -169,7 +166,6 @@ SystemManagerModule:
         - [ deactivate perception ]
         - [ activate rc ]
         - [ deactivate task_engine TaskMaster cancel ]
-        - [ activate motion_player ]
     "Auto":
@@ -188,7 +184,6 @@ SystemManagerModule:
         - [ activate perception ]
         - [ deactivate rc ]
         - [ activate task_engine ]
-        - [ activate motion_player ]
    "Manipulator":
@@ -227,7 +222,6 @@ SystemManagerModule:
         - [ activate perception ]
         - [ activate rc ]
         - [ deactivate task_engine TaskMaster cancel ]
-        - [ deactivate motion_player ]
    "FreeExploration":
@@ -246,7 +240,6 @@ SystemManagerModule:
         - [ activate perception ]
         - [ deactivate rc ]
         - [ activate task_engine ]
-        - [ activate motion_player ]
    "EStop":
@@ -279,7 +272,6 @@ SystemManagerModule:
         - [ activate perception ]
         - [ deactivate rc ]
         - [ deactivate task_engine TaskMaster cancel ]
-        - [ activate motion_player ]
```
{% endcode %}

#### 2.3 Onboard Disk Directories <a href="#web-02-2-3-onboard-disk-directories" id="web-02-2-3-onboard-disk-directories"></a>

**orin**

<figure><img src="../../.gitbook/assets/unknown (366).webp" alt="orin"><figcaption><p>orin</p></figcaption></figure>

**X86**

<figure><img src="../../.gitbook/assets/unknown (367).webp" alt="X86"><figcaption><p>X86</p></figcaption></figure>

text

{% code collapsedlinecount="10" %}
```
```
{% endcode %}

### 3. Overview of Secondary Development Interfaces <a href="#web-03-3-overview-of-secondary-development-interfaces" id="web-03-3-overview-of-secondary-development-interfaces"></a>

Most of the modules in the aforementioned software system use AimRT as the underlying framework. AimRT is a robot runtime underlying framework that benchmarks against ROS2, open-sourced by Agibot Robotics in 09/2024. AimRT provides two basic underlying communication methods: Channel and RPC (for more details, refer to the [AimRT official documentation](https://github.com/AimRT/AimRT/blob/v0.10.0/document/sphinx-cn/tutorials/concepts/concepts.md?plain=1#L74-L94)). These two communication methods can correspond to multiple different communication backends.

To reduce the cognitive load of secondary development, we provide two forms of relatively simple and general interfaces for secondary development: HTTP JSON RPC and ROS2 Topic. HTTP JSON RPC is suitable for low-frequency interface one-to-many calls, while ROS2 Topic is suitable for high-frequency interface many-to-many calls. The following are the two

<figure><img src="../../.gitbook/assets/unknown (368).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

> For the development language, there is no restriction on any development language for secondary development programs. As long as they can send and receive HTTP messages, all HTTP JSON RPC interfaces can be called. As long as they support ROS2 Humble with Fastdds, they can send and receive ROS2 topic messages and call all the body ROS2 Topic interfaces.

Here are two specific interface call examples to establish a clearer understanding of the interfaces:

#### 3.1 HTTP JSON RPC <a href="#web-03-3-1-http-json-rpc" id="web-03-3-1-http-json-rpc"></a>

The following is an example of a command-line RPC request to get the battery power level:

bash

{% code collapsedlinecount="10" %}
```
curl -i     -H 'content-type:application/json' \
            -H 'timeout: 1000'   -X POST 'http://192.168.100.100:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState' \
            -d '{}'
```
{% endcode %}

Where:

* `192.168.100.110` is the IP address of the robot's X86 industrial PC. This should be the IP address of the interconnected industrial PCs. You can execute the call on ORIN. If you need to call it remotely, change this IP to the IP corresponding to the WiFi network card of the robot's X86 development board (you can check this via the AimMaster software or by running `ip a` on the X86).
* `56421` is the HTTP port number for the corresponding service. This will generally be provided in detailed interface examples.
* `content-type:application/json` is the request header, indicating that the request body is in JSON format. **This request header must be included.**
* `timeout: 1000` is the request header, indicating the request timeout time in milliseconds. Here it is set to 1000 milliseconds, which is 1 second. This field can be omitted.
* `aimdk.protocol.HalBmsService/GetBmsState` is the name of the RPC interface to get the battery state. The specific names of each interface can be found in the corresponding interface documentation and examples.
* `'{}'` is the request body. An empty body here means that all fields are default values. If you need to pass specific fields, you can pass a JSON string, for example, `'{"bms_state": 1}'` indicates passing the `bms_state` field with a value of 1 (this is just an example; the specific field names and values should be referenced from the corresponding interface documentation and examples).

#### 3.2 ROS2 Topic <a href="#web-03-3-2-ros2-topic" id="web-03-3-2-ros2-topic"></a>

**3.2.1 Environment Variable Setup**

The topic interfaces use native ROS2 topics. The machine defaults to **ROS2 Humble with Fastdds**. Before calling any ROS2 Topic interface, **some environment variables must be set** as follows:

bash

{% code collapsedlinecount="10" %}
```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
```
{% endcode %}

> If your program needs to start with root privileges, change the above dds configuration file to use the following configuration file:
>
> bash
>
> {% code collapsedlinecount="10" %}
> ```
> export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/privileged_ros_dds_configuration.xml
> ```
> {% endcode %}
>
> In `ros_dds_configuration.xml`, both shared memory communication and UDP communication are enabled, while in `privileged_ros_dds_configuration.xml`, only UDP communication is enabled to avoid permission issues with shared memory.

> Note that environment variables are only effective in the current terminal. If you open a new terminal, you need to set them again.

**3.2.2 QoS Settings**

Additionally, note that the default QoS for topics on the machine is

yaml

{% code collapsedlinecount="10" %}
```
  history: keep_last
  depth: 10
  reliability: best_effort
```
{% endcode %}

When using, ensure that the QoS is consistent to guarantee smooth communication.

**3.2.3 Call Example**

The following is an example script for subscribing to joint state ROS2 Topics.

python

{% code collapsedlinecount="10" %}
```
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from rclpy.qos import QoSHistoryPolicy, QoSProfile, QoSReliabilityPolicy
from sensor_msgs.msg import JointState

class JointStateSubscriber(Node):
    def __init__(self, topic_name: str):
        super().__init__("joint_state_subscriber")

        self.topic_name = topic_name

        qos_profile = QoSProfile(
            history=QoSHistoryPolicy.KEEP_LAST, depth=10, reliability=QoSReliabilityPolicy.BEST_EFFORT
        )

        self.subscription = self.create_subscription(JointState, topic_name, self.listener_callback, qos_profile)

    def listener_callback(self, msg: JointState):
        self.get_logger().info(f"=== Received {self.topic_name} ===")
        self.get_logger().info(f"  header: {msg.header}")
        self.get_logger().info(f"  name: {msg.name}")
        self.get_logger().info(f"  position: {msg.position}")
        self.get_logger().info(f"  velocity: {msg.velocity}")
        self.get_logger().info(f"  effort: {msg.effort}")

def main(args=None):
    rclpy.init(args=args)
    # Arm joint status: /motion/control/arm_joint_state
    # Neck joint status: /motion/control/neck_joint_state
    joint_state_node = JointStateSubscriber("/motion/control/arm_joint_state")
    try:
        rclpy.spin(joint_state_node)
    except KeyboardInterrupt:
        pass
    finally:
        joint_state_node.destroy_node()
        rclpy.shutdown()

if __name__ == "__main__":
    main()
```
{% endcode %}

**3.2.4 External PC Communication for ROS2 Topics**

To ensure the stability of ROS2 communication on the machine, we have modified the default DDS communication configuration file to restrict ROS2 traffic to flow only between the X86 and ORIN industrial PCs, and not to external devices. For non-root processes, shared memory communication and UDP communication are enabled by default. The corresponding configuration files are located at `/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml` on both industrial PCs. The configuration file on ORIN is as follows:

xml

{% code collapsedlinecount="10" %}
```
<?xml version="1.0" encoding="UTF-8"?>
<dds>
  <profiles xmlns="http://www.eprosima.com/XMLSchemas/fastRTPS_Profiles">
    <transport_descriptors>
      <transport_descriptor>
        <transport_id>UDPv4_transport</transport_id>
        <type>UDPv4</type>
        <sendBufferSize>10388608</sendBufferSize>
        <receiveBufferSize>10388608</receiveBufferSize>
        <interfaceWhiteList>
          <address>192.168.100.110</address>
        </interfaceWhiteList>
      </transport_descriptor>
      <transport_descriptor>
        <transport_id>SHM_transport</transport_id>
        <type>SHM</type>
        <segment_size>8388608</segment_size>
        <port_queue_capacity>1024</port_queue_capacity>
      </transport_descriptor>
    </transport_descriptors>

    <participant profile_name="participant_profile" is_default_profile="true">
      <rtps>
        <useBuiltinTransports>false</useBuiltinTransports>
        <userTransports>
          <transport_id>SHM_transport</transport_id>
          <transport_id>UDPv4_transport</transport_id>
        </userTransports>
      </rtps>
    </participant>
  </profiles>
```
{% endcode %}

The whitelist includes the IP `192.168.100.110`, which is the IP of the network card connecting ORIN and X86. Adding this IP ensures that topics published and subscribed to on ORIN can communicate normally with the X86 industrial PC. If you need to receive and send the corresponding ROS2 Topics on a third-party PC or an additional industrial PC, you need to add the IP of the local network card, usually `192.168.2.50`, to the whitelist (`/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml` and `/agibot/software/v0/entry/bin/cfg/privileged_ros_dds_configuration.xml`). After adding, restart the robot and connect via a wired connection to the corresponding network port to perform the corresponding ROS2 communication.

For the X86 industrial PC, the debug network port on the right side of the back is in DHCP mode. If you need to connect the ROS2 communication on the X86 with a third-party PC/industrial PC, you need to configure the network port to manually specify a fixed IP of `192.168.2.150` (modify `/etc/netplan/01-netcfg.yaml`), and then directly connect or connect through a switch. The network topology is as follows:

<figure><img src="../../.gitbook/assets/unknown (369).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

If you only need to connect to one industrial PC, you do not need a switch and can directly connect with a network cable. In this case, you need to add the IP `192.168.2.150` to the dds whitelist on the X86 industrial PC (`/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml` and `/agibot/software/v0/entry/bin/cfg/privileged_ros_dds_configuration.xml`).

> Using asymmetric dds whitelists in ROS2 Humble version can sometimes lead to unpredictable communication issues. Please ensure that the dds whitelist configurations are consistent.
>
> Reference: [https://github.com/eProsima/Fast-DDS/pull/3733](https://github.com/eProsima/Fast-DDS/pull/3733)

### 4. Basic Constraints for Secondary Development <a href="#web-04-4-basic-constraints-for-secondary-development" id="web-04-4-basic-constraints-for-secondary-development"></a>

There are some basic constraints that need to be followed when performing secondary development based on the A2 Ultra model. Violating these constraints may cause damage to the robot's hardware, software, and system. Damage caused by violating the following agreements is not covered under the warranty:

1. Do not deploy secondary development programs on the x86 industrial PC. The motion control program runs on the x86 system, and deploying programs on the x86 industrial PC may lead to CPU and memory resource competition, which can even cause the robot to crash in severe cases.
2. Do not modify the system configurations of the x86 and orin industrial PCs at will, such as file system mounting, system scheduling policies, default UDP/TCP buffer sizes, and other kernel-related configurations.
3. Do not modify the configuration of the onboard software modules arbitrarily, such as various configurations of the motion control and other modules.
4. Do not modify the system software dependencies arbitrarily, and strictly prohibit using apt for installing and uninstalling software.
5. Do not frequently call RPC interfaces, as this can cause excessive load on the system, potentially leading to a crash. It is recommended to set the polling frequency for continuous state-based RPC interfaces to 0.2 Hz or below, and for short-term polling interfaces like status queries to 1 Hz or below.

### 5. Secondary Development Program Deployment <a href="#web-05-5-secondary-development-program-deployment" id="web-05-5-secondary-development-program-deployment"></a>

Secondary development programs are generally recommended to be deployed in two ways: on the main body ORIN or on a third-party industrial PC. The ORIN deployment is more hardware-efficient and suitable for secondary development programs that do not require much resource usage. If more resources are needed, some of the existing programs on the ORIN need to be closed to release CPU/GPU resources; deploying on a third-party industrial PC requires additional cabling, usually with external cabling configuration. The advantage is that all the original software functions on the machine can be retained, while also having relatively sufficient computing resources.

#### 5.1 Main Body ORIN Deployment <a href="#web-05-5-1-main-body-orin-deployment" id="web-05-5-1-main-body-orin-deployment"></a>

The recommended directory for program deployment is /agibot/data/home/agi/Desktop. The disk cleanup module on the machine will periodically clean up space, and this folder is on the whitelist and will not be cleaned.

bash

{% code collapsedlinecount="10" %}
```
mkdir -p /agibot/data/home/agi/Desktop
```
{% endcode %}

If you encounter permission issues, consider using the following command to create the folder:

bash

{% code collapsedlinecount="10" %}
```
sudo mkdir -p /agibot/data/home/agi/Desktop
sudo chown -R agi:agi /agibot/data/home/agi
```
{% endcode %}

**5.1.1 Python Virtual Environment**

For secondary development using Python, you only need to create a virtual environment. You can use tools like conda/venv to create a virtual environment, where venv is a built-in tool, and conda installation can refer to the [miniconda official installation documentation](https://www.anaconda.com/docs/getting-started/miniconda/install#aws-graviton2%2Farm64).

**5.1.2 Docker Deployment**

If using C++ or other compiled languages, or if certain system dependencies need to be installed or modified, consider using Docker for deployment.

Refer to [https://docs.docker.com/engine/install/ubuntu/#install-from-a-package](https://docs.docker.com/engine/install/ubuntu/#install-from-a-package) for Docker installation, and do not use apt for program installation.

**5.1.2.1 Modify Docker Default Data Path**

The default data path for Docker, /var/lib/docker, has a small partition capacity. You need to change its default data storage path to a whitelist path.

1.  Move the default storage pathbash

    <pre data-collapsed-line-count="10"><code># Stop the Docker service
    sudo systemctl stop docker

    # Move the default storage path（please create the target path first /agibot/data/home/agi/Desktop）
    sudo mv /var/lib/docker /agibot/data/home/agi/Desktop
    </code></pre>
2.  Modify the configuration filebash

    <pre data-collapsed-line-count="10"><code># Modify Docker configuration
    sudo vim /etc/docker/daemon.json
    </code></pre>

    \
    Add the following to the configuration file:json

    <pre data-collapsed-line-count="10"><code>{
      "data-root": "/agibot/data/home/agi/Desktop/docker"
    }
    </code></pre>
3.  Restart Docker:bash

    <pre data-collapsed-line-count="10"><code>sudo systemctl start docker
    </code></pre>

    \
    Docker configuration is complete.

**5.1.2.2 ROS2 Communication Settings Inside and Outside the Container**

By default, the container cannot normally communicate with the onboard system via ROS2, and some configuration is required.

1.  When creating the container, share IPC and network communication with the host, adding the following optionsbash

    <pre data-collapsed-line-count="10"><code>--ipc=host --net=host
    </code></pre>
2.  Use the same agi user inside the container as on the ORIN, with uid and gid both set to 1001bash

    <pre data-collapsed-line-count="10"><code>groupadd -g 1001 agi &#x26;&#x26; useradd -u 1001 -g 1001 -m -s /bin/bash agi
    </code></pre>
3.  Use the same DDS configuration file inside and outside the container. Copy the /agibot/software/v0/entry/bin/cfg/ros\_dds\_configuration.xml from the ORIN to the container. Before running ROS2 programs or using ros2 commands in the container, execute the following command (replace /path/to with the actual path)bash

    <pre data-collapsed-line-count="10"><code>source /opt/ros/humble/setup.bash
    export ROS_DOMAIN_ID=232
    export ROS_LOCALHOST_ONLY=0
    export FASTRTPS_DEFAULT_PROFILES_FILE=/path/to/ros_dds_configuration.xml
    </code></pre>
4.  At this point, the container should be able to receive ROS2 topics published by the ORINbash

    <pre data-collapsed-line-count="10"><code>ros2 topic list
    </code></pre>

#### 5.2 Third-Party Industrial PC Deployment <a href="#web-05-5-2-third-party-industrial-pc-deployment" id="web-05-5-2-third-party-industrial-pc-deployment"></a>

Recommended network topology configuration:

<figure><img src="../../.gitbook/assets/unknown (370).webp" alt="Recommended network topology configuration:"><figcaption><p>Recommended network topology configuration:</p></figcaption></figure>

1. Set the X86 debugging network port to a fixed IP of 192.168.2.150, and modify the eth\_debug or enp2s0f1 in the `/etc/netplan/01-netcfg.yaml` file to a fixed IP of 192.168.2.150.
2. Modify the DDS configuration files for the ORIN and X86, `/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml` and `/agibot/software/v0/entry/bin/cfg/privileged_ros_dds_configuration.xml`. Add `<address>192.168.2.50</address>` to the ORIN configuration file and `<address>192.168.2.150</address>` to the X86 configuration file, then restart the robot.
3.  Set the wired network port of the PC to a fixed IP of 192.168.2.100, and install ROS2 Humble with Fastdds on it. Following the wiring diagram above, you can correctly communicate with the robot's industrial PC via ROS2. Note that before running ROS2 programs, you need to set the following environment variablesbash

    <pre data-collapsed-line-count="10"><code>source /opt/ros/humble/setup.bash
    export ROS_DOMAIN_ID=232
    export ROS_LOCALHOST_ONLY=0
    </code></pre>

### 6. Quick Start for Secondary Development <a href="#web-06-6-quick-start-for-secondary-development" id="web-06-6-quick-start-for-secondary-development"></a>

This chapter will demonstrate how to quickly get your first secondary development program up and running through a few simple example programs, providing a basic understanding.

The quick start tutorial assumes that the secondary development program is deployed on ORIN and uses a Python venv virtual environment.

#### 6.1 Prerequisites <a href="#web-06-6-1-prerequisites" id="web-06-6-1-prerequisites"></a>

**6.1.1 Connecting to ORIN**

There are multiple ways to connect to ORIN; choose any one of the following methods.

1.  Wired Connection\
    **Set the IP address of the PC's wired network port to a static IP of 192.168.2.100**, then connect one end of the Ethernet cable to the PC's wired network port and the other end to the robot's right debugging network port at the back.yaml

    <pre data-collapsed-line-count="10"><code>ping 192.168.2.50 # Check whether it is connected
    ssh agi@192.168.2.50
    </code></pre>
2.  Wireless AP Hotspot Connection\
    Connect the development machine to the ORIN AP hotspot, which usually starts with Robot-. The default password can be found in the `password.md` file in the AimDK package. Then, log in to the robot via SSH using the AP hotspot IP.bash

    <pre data-collapsed-line-count="10"><code>ssh agi@192.168.88.88
    </code></pre>
3.  Via X86 WiFi Jump\
    Both the development machine and the robot need to be connected to the same wireless network. Obtain the robot's IP from the AimMaster settings - Wireless LAN interface, which is actually the X86 WiFi IP. After connecting via SSH, jump to ORIN using 192.168.100.110.bash

    <pre data-collapsed-line-count="10"><code>ssh agi@192.168.xxx.xxx # x86 ip
    ssh agi@192.168.100.110
    </code></pre>

    \
    ORIN and X86 are directly connected via an Ethernet cable in the 192.168.100.0/24 subnet, and you can jump between them using the IPs 192.168.100.100 and 192.168.100.110.\
    You can also use the ssh proxyjump function to make a one-time jump (you still need to enter the password twice).bash

    <pre data-collapsed-line-count="10"><code>ssh -J agi@192.168.xxx.xxx agi@192.168.100.110
    </code></pre>

    \
    The proxyjump function can also be used with rsync to quickly sync local folders to ORIN without transferring through the X86 (the X86 WiFi IP and folder need to be modified):bash

    <pre data-collapsed-line-count="10"><code>rsync -avzP --exclude ".git/" \
            -e "ssh -J agi@192.168.xxx.xxx" \
            /path/to/local/dir agi@192.168.100.110:/agibot/data/home/agi/Desktop/working_dir
    </code></pre>

**6.1.2 Creating a Deployment Folder**

The recommended directory for deploying programs is `/agibot/data/home/agi/Desktop`. The disk cleanup module on the machine will periodically clean up space, and this folder is on the whitelist and will not be cleaned.

> **Placing programs and data in other paths may result in partition full, files being mistakenly deleted, etc. Please strictly follow the convention of using the `/agibot/data/home/agi/Desktop` directory.**

bash

{% code collapsedlinecount="10" %}
```
mkdir -p /agibot/data/home/agi/Desktop
```
{% endcode %}

If you encounter permission issues, consider using the following command to create the folder:

bash

{% code collapsedlinecount="10" %}
```
sudo mkdir -p /agibot/data/home/agi/Desktop
sudo chown -R agi:agi /agibot/data/home/agi
```
{% endcode %}

**6.1.3 Creating a Python Virtual Environment**

bash

{% code collapsedlinecount="10" %}
```
cd /agibot/data/home/agi/Desktop
python -m venv mydev
source mydev/bin/activate
```
{% endcode %}

Subsequent examples assume that the virtual environment has been created and activated, and this step will not be repeated.

#### 6.2 Example of Running a Battery Power Retrieval Program <a href="#web-06-6-2-example-of-running-a-battery-power-retrieval-program" id="web-06-6-2-example-of-running-a-battery-power-retrieval-program"></a>

This example uses an HTTP request to obtain the BMS status of the robot.

Run the following script directly in the ORIN command line:

yaml

{% code collapsedlinecount="10" %}
```
curl -i     -H 'content-type:application/json' \
            -H 'timeout: 1000'   -X POST 'http://192.168.100.100:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState' \
            -d '{}'
```
{% endcode %}

The returned result should look like the following (the specific field meanings are explained in detail in the subsequent API chapters):

python

{% code collapsedlinecount="10" %}
```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Content-Type: application/json
Content-Length: 705

{"data":{"ver":{"hardware_major":48,"hardware_minor":48,"hardware_revision":49,"software_major":51,"software_minor":48,"software_revision":49},"voltage":54410,"current":-304,"power":0,"temperature":308,"capacity":13971,"charge":99,"power_supply_health":"PowerSupplyHealth_GOOD","power_supply_status":"PowerSupplyStatus_IDEL","cycles_num":129,"cycles_capacity":12,"abnormal_state":"PowerAbnormalStatus_NORMAL","charger_state":"ChargerConnected","bms_state":"BatteryStatus_Connected","max_current":25490,"battery_firmware_type":"BatteryFirmwareType_OLD","battery_key_state":"BatteryKeyStatus_SHORT_CURCUIT","battery_pack_state":"BatteryPackStatus_NORMAL","battery_comm_state":"BatteryCommunication_NORMAL"}}
```
{% endcode %}

#### 6.3 Example of Getting the Upper Limb Joint State <a href="#web-06-6-3-example-of-getting-the-upper-limb-joint-state" id="web-06-6-3-example-of-getting-the-upper-limb-joint-state"></a>

Save the following code on ORIN as /agibot/data/home/agi/Desktop/joint\_state.py.

python

{% code collapsedlinecount="10" %}
```
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from rclpy.qos import QoSHistoryPolicy, QoSProfile, QoSReliabilityPolicy
from sensor_msgs.msg import JointState

class JointStateSubscriber(Node):
    def __init__(self, topic_name: str):
        super().__init__("joint_state_subscriber")

        self.topic_name = topic_name

        qos_profile = QoSProfile(
            history=QoSHistoryPolicy.KEEP_LAST, depth=10, reliability=QoSReliabilityPolicy.BEST_EFFORT
        )

        self.subscription = self.create_subscription(JointState, topic_name, self.listener_callback, qos_profile)

    def listener_callback(self, msg: JointState):
        self.get_logger().info(f"=== Received {self.topic_name} ===")
        self.get_logger().info(f"  header: {msg.header}")
        self.get_logger().info(f"  name: {msg.name}")
        self.get_logger().info(f"  position: {msg.position}")
        self.get_logger().info(f"  velocity: {msg.velocity}")
        self.get_logger().info(f"  effort: {msg.effort}")

def main(args=None):
    rclpy.init(args=args)
    # Arm joint status: /motion/control/arm_joint_state
    # Neck joint status: /motion/control/neck_joint_state
    joint_state_node = JointStateSubscriber("/motion/control/arm_joint_state")
    try:
        rclpy.spin(joint_state_node)
    except KeyboardInterrupt:
        pass
    finally:
        joint_state_node.destroy_node()
        rclpy.shutdown()

if __name__ == "__main__":
    main()
```
{% endcode %}

Then execute the following command:

yaml

{% code collapsedlinecount="10" %}
```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
python3 /agibot/data/home/agi/Desktop/joint_state.py
```
{% endcode %}

#### 6.4 Example of Controlling the Head Shaking Interface <a href="#web-06-6-4-example-of-controlling-the-head-shaking-interface" id="web-06-6-4-example-of-controlling-the-head-shaking-interface"></a>

We provide both HTTP and ROS2 interfaces for the head.

**6.4.1 Head Shaking HTTP Example**

Using the HTTP interface is simpler. Save and run the following script:

python

{% code collapsedlinecount="10" %}
```
#!/usr/bin/env python3

## Function: Set head joint values

import requests
from datetime import datetime

# Generate request header
def create_header():
    now = datetime.utcnow()
    header = {
        "timestamp": {
            "seconds": int(now.timestamp()),
            "nanos": now.microsecond * 1000,
            "ms_since_epoch": int(now.timestamp() * 1000),
        },
        "control_source": "ControlSource_SAFE",
    }
    return header

def create_neck_data():
    neck_data = {
        "shake": {
            "name": "idx27_head_joint1",
            "position": 0.5,
            "velocity": 0.0,
            "effort": 0.0,
        },
        "nod": {
            "name": "idx28_head_joint2",
            "position": 0.5,
            "velocity": 0.0,
            "effort": 0.0,
        },
    }

    return neck_data

def service_call():
    # Send service request

    url = (
        "http://192.168.100.100:56322/rpc/aimdk.protocol.McMotionService/SetNeckCommand"
    )
    headers = {"Content-Type": "application/json", "timeout": "60000"}

    payload = {"header": create_header(), "data": create_neck_data()}

    response = requests.Session().post(url, headers=headers, json=payload)

    return response

# Main program entry point
def main():
    response = service_call()
    print(response.text)
    requests.Session().close()

if __name__ == "__main__":
    main()
```
{% endcode %}

In this, `velocity` and `effort` are ineffective; only `position` is a valid value.

**6.4.2 Head Shaking ROS2 Example**

Using the ROS2 interface to call the head shaking program requires some prerequisites:

1. You need to switch the state machine of the motion control module to the RL\_LOCOMOTION\_ARM\_EXT\_JOINT\_SERVO state. This can be done by switching to the upper body action mode on the AimMaster. The subsequent detailed interface explanation will also cover how to use the program interface for switching.
2.  Call the following command to release the control of the upper body joints by the action playback module.bash

    <pre data-collapsed-line-count="10"><code>curl -i \
        -H 'content-type:application/json' \
        -H 'timeout: 1000' \
        -X POST http://192.168.100.100:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer \
        -d '{}'
    </code></pre>

Next, save the following script as /agibot/data/home/agi/Desktop/neck.py

python

{% code collapsedlinecount="10" %}
```
#!/usr/bin/env python3
import rclpy
from rclpy.node import Node
from rclpy.qos import QoSHistoryPolicy, QoSProfile, QoSReliabilityPolicy
from sensor_msgs.msg import JointState

class NeckPublisher(Node):
    def __init__(self, neck_topic_name: str):
        super().__init__("neck_publisher")

        qos_profile = QoSProfile(
            history=QoSHistoryPolicy.KEEP_LAST,
            depth=10,
            reliability=QoSReliabilityPolicy.BEST_EFFORT,
        )

        self.publisher = self.create_publisher(JointState, neck_topic_name, qos_profile)

        timer_period = 0.02
        self.timer = self.create_timer(timer_period, self.timer_callback)

    def timer_callback(self):
        msg = JointState()
        msg.header.stamp = self.get_clock().now().to_msg()

        # Position control only is supported.
        # The first value represents head yaw, ranging from -0.785 to 0.785.
        # The second value is unused but must still be provided.
        msg.name = ["idx27_head_joint1", "idx28_head_joint2"]
        msg.position = [0.5, 0.5]

        # The following fields have no actual effect but must be set; otherwise, the motion controller may crash.
        msg.velocity = [0.0, 0.0]
        msg.effort = [0.0, 0.0]

        self.publisher.publish(msg)

def main(args=None):
    rclpy.init(args=args)
    neck_publisher = NeckPublisher("/motion/control/neck_joint_command")
    try:
        rclpy.spin(neck_publisher)
    except KeyboardInterrupt:
        pass
    finally:
        neck_publisher.destroy_node()
        rclpy.shutdown()

if __name__ == "__main__":
    main()
```
{% endcode %}

Then run

yaml

{% code collapsedlinecount="10" %}
```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
python3 /agibot/data/home/agi/Desktop/neck.py
```
{% endcode %}

### 7. Detailed Interface Documentation <a href="#web-07-7-detailed-interface-documentation" id="web-07-7-detailed-interface-documentation"></a>

To reduce redundancy and increase information density, the following conventions are used in the interface documentation below:

1. The header fields in the request and response messages of HTTP JSON RPC are not explained in detail. Some headers are omitted in the example messages, and they can also be left blank in actual requests. Please refer to the actual runnable example scripts for details.
2. In HTTP JSON RPC, the IP addresses in the URLs are filled as 192.168.100.110 or 192.168.100.100, corresponding to the ORIN industrial PC IP and X86 industrial PC IP, respectively. You can change them to other accessible IPs as needed.
3. All request methods in HTTP JSON RPC are POST, and they are not listed separately in the following interface documentation.
4. In ROS2 Topics, if the message type is an input parameter, the secondary development program will publish this topic, and the onboard program will receive it. If it is an output parameter, the opposite is true.
5. The message type for ROS2 Topic interfaces is `ros2_plugin_proto/msg/RosMsgWrapper`. You need to source `prebuilt/ros2_plugin_proto_aarch64/share/ros2_plugin_proto/local_setup.bash` before using it. If you are running on an x86 architecture machine, replace `ros2_plugin_proto_aarch64` with `ros2_plugin_proto_x86_64`. This is not further elaborated in the interface notes.
6. Unexplained parameters are generally invalid. Fill in the default values as shown in the examples without modification.
7. For unspecified units, angles are in radians (rad) by default, and lengths are in meters (m) by default.

### 8. Guide to Motion Control Simulation <a href="#web-08-8-guide-to-motion-control-simulation" id="web-08-8-guide-to-motion-control-simulation"></a>

#### 8.1 Simulation Description <a href="#web-08-8-1-simulation-description" id="web-08-8-1-simulation-description"></a>

We provide a mujoco-based simulation system for the A2 robot, designed to serve as a testing ground for basic calls to the A2 robot's motion control and action playback interfaces. This serves as a basic validation before actual operation, reducing the risk of damaging the robot while facilitating the debugging of secondary development program logic.

<figure><img src="../../.gitbook/assets/unknown (371).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

The system runs the mujoco\_sim, motion\_control, and motion\_player components. mujoco\_sim acts as the underlying simulation engine, simulating the robot's physical body and hal\_ethercat. motion\_control interacts with mujoco\_sim to exchange control commands and states, controlling the simulated robot. motion\_player then calls the high-level interfaces provided by motion\_control to play actions. The motion\_control and motion\_player components are identical to those on the real machine, allowing the system to call all interfaces of the motion control and action playback modules.

#### 8.2 Prerequisites <a href="#web-08-8-2-prerequisites" id="web-08-8-2-prerequisites"></a>

This simulation system is provided as a container image, containing executable files for each component, action resource files, and calling scripts. To use this simulation system, the following conditions must be met:

1. An x86\_64 architecture Linux system with Docker installed.
2. Use of an X11 desktop system.
   * You can check this by running `echo $XDG_SESSION_TYPE`; the expected output is `x11`.

#### 8.3 Usage Tutorial <a href="#web-08-8-3-usage-tutorial" id="web-08-8-3-usage-tutorial"></a>

**8.3.1 Pulling the Image**

1. Log in to the image repository with a read-only account.

bash

{% code collapsedlinecount="10" %}
```
docker login tongyong-public-cn-shanghai.cr.volces.com -u crrobot@aima-public-reader -p Aima123456
```
{% endcode %}

2. Pull the corresponding image.

bash

{% code collapsedlinecount="10" %}
```
docker pull tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-simulator:v1.3
```
{% endcode %}

**8.3.2 Starting the Image**

1.  Allow Docker to access the display, which is used to configure the access control list for the X Window System. Running `xhost +` will allow all hosts to connect to the current user's X server, effectively disabling access control for the X server and allowing any user to access and operate it.bash

    <pre data-collapsed-line-count="10"><code>xhost +
    </code></pre>
2.  Start the Docker container.bash

    <pre data-collapsed-line-count="10"><code>docker run -it \
            --name=a2-ultra-sim \
            --privileged \
            --net=host \
            --ipc=host \
            --pid=host \
            -e DISPLAY=$DISPLAY \
            -v /tmp/.X11-unix:/tmp/.X11-unix \
            -v /run/dbus/system_bus_socket:/run/dbus/system_bus_socket:ro \
            -d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-simulator:v1.3
    </code></pre>

    \
    If you find that the simulation interface is lagging when using an NVIDIA graphics card, try starting the container with the following command:bash

    <pre data-collapsed-line-count="10"><code>docker run -it \
            --name=a2-ultra-sim \
            --gpus all \
            --privileged \
            --net=host \
            --ipc=host \
            --pid=host \
            -e DISPLAY=$DISPLAY \
            -e NVIDIA_VISIBLE_DEVICES=all \
            -e NVIDIA_DRIVER_CAPABILITIES=all \
            -v /tmp/.X11-unix:/tmp/.X11-unix \
            -v /run/dbus/system_bus_socket:/run/dbus/system_bus_socket:ro \
            -d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-simulator:v1.3
    </code></pre>
3.  Enter the container.bash

    <pre data-collapsed-line-count="10"><code>docker start a2-ultra-sim &#x26;&#x26; docker exec -it a2-ultra-sim /bin/bash
    </code></pre>

**8.3.3 Starting the Simulation, Motion Control, and Action Playback Modules**

1.  Enter the image and run the following command to start the simulation.bash

    <pre data-collapsed-line-count="10"><code>docker start a2-ultra-sim &#x26;&#x26; docker exec -it a2-ultra-sim /bin/bash

    cd /home/agi/a2_simulation/mujoco_sim_ultra_1.3/bin
    ./start_a2_t2d0_ultra.sh
    </code></pre>
2.  In a new window, connect to the container and start the motion control program.bash

    <pre data-collapsed-line-count="10"><code>docker start a2-ultra-sim &#x26;&#x26; docker exec -it a2-ultra-sim /bin/bash

    cd /home/agi/a2_simulation/motion_control_ultra_1.3.26/scripts/motion_control
    ./start_motion_control.sh
    </code></pre>
3.  In another new window, connect to the container and start the action playback program.bash

    <pre data-collapsed-line-count="10"><code>docker start a2-ultra-sim &#x26;&#x26; docker exec -it a2-ultra-sim /bin/bash

    cd /home/agi/a2_simulation/motion_player_ultra_1.3.26/scripts/motion_player
    ./start_motion_player.sh
    </code></pre>

**8.3.4 Controlling Robot Walking**

Here, we will use robot walking as an example to explain the basic logic of calling a motion control interface. For other interfaces, refer to the motion control interface documentation and example scripts.

1.  Open a new window, enter the container, and switch the motion control Action to joint standing mode (RL\_JOINT\_DEFAULT).bash

    <pre data-collapsed-line-count="10"><code>docker start a2-ultra-sim &#x26;&#x26; docker exec -it a2-ultra-sim /bin/bash

    cd /home/agi/a2_simulation/tools-ultra/mc
    ./SetAction.py # Select the number corresponding to RL_JOINT_DEFAULT.
    </code></pre>
2.  Click the Load-Key button in the mujoco\_sim interface to stabilize the robot.<br>

    <figure><img src="../../.gitbook/assets/unknown (372).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>
3.  Continue to switch the motion control Action to enhanced walking mode (RL\_LOCOMOTION\_DEFAULT).bash

    <pre data-collapsed-line-count="10"><code>./SetAction.py # Select the number corresponding to RL_LOCOMOTION_DEFAULT.
    </code></pre>
4.  Call the walking example script.bash

    <pre data-collapsed-line-count="10"><code>source /home/agi/a2_simulation/ros2_plugin_proto_x86_64/share/ros2_plugin_proto/local_setup.bash
    ./walk.py
    </code></pre>

**8.3.5 Controlling Robot for Action Playback**

1.  Switch the motion control state to enhanced walking upper limb servo mode (RL\_LOCOMOTION\_ARM\_EXT\_JOINT\_SERVO).bash

    <pre data-collapsed-line-count="10"><code>cd /home/agi/a2_simulation/tools-ultra/mc
    ./SetAction.py # Select the number corresponding to RL_LOCOMOTION_ARM_EXT_JOINT_SERVO.
    </code></pre>
2.  Call the SendMotionCommand interface to perform the action.bash

    <pre data-collapsed-line-count="10"><code>cd ../motion_player
    ./send_motion_id.sh /agibot/data/resources/default/motion/speech10s/speech10s.mcap
    </code></pre>

### 9. Interaction Secondary Development Guide <a href="#web-09-9-interaction-secondary-development-guide" id="web-09-9-interaction-secondary-development-guide"></a>

Interaction-related secondary development on the device side provides two types of development modes:

1. Agibot Interaction Simple Extension
   * Agibot interaction capabilities are retained, with Agibot providing basic interfaces such as TTS and motion expressions. These interfaces can be used to control the robot for basic exhibition hall tours, explanations, etc., while the robot can still use the Agibot voice interaction solution.
2. Full Takeover by Secondary Development
   * Agibot interaction capabilities are disabled, and Agibot provides noise-reduced microphone input from the robot, along with speaker usage permissions and face recognition results. The secondary development program fully takes over the voice interaction content.

The following is a detailed comparison table for both modes:

| Mode                                   | Agibot Interaction Capabilities Retained | Interfaces Provided by Agibot Side                            | Network Requirements                                                           | Applicable Scenarios                                                     | Development Difficulty and Workload                                                   |
| -------------------------------------- | ---------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------- |
| Agibot Interaction Simple Extension    | Yes                                      | TTS, motion, expression, and face recognition interfaces      | Both Agibot interaction solution and TTS interface require internet connection | Developing simple exhibition hall tour demos, fixed process arrangements | Relatively simple, workload depends on the complexity of the process, generally small |
| Full Takeover by Secondary Development | No                                       | Noise-reduced audio, speaker, and face recognition interfaces | Internet connection required during robot initialization, not needed afterward | Independently developing a complete interaction solution                 | Higher difficulty, requires a full R\&D team, larger workload                         |

#### 9.1 Agibot Interaction Simple Extension <a href="#web-09-9-1-agibot-interaction-simple-extension" id="web-09-9-1-agibot-interaction-simple-extension"></a>

In this development mode, the available interfaces are as follows:

| Interface Name/Subscription Topic        | Interface Description                          | Request Message Type      | Response Message Type      | Notes                                                              | Communication Backend |
| ---------------------------------------- | ---------------------------------------------- | ------------------------- | -------------------------- | ------------------------------------------------------------------ | --------------------- |
| `TTSService.PlayTTS`                     | Text-to-speech playback                        | `PlayTTSRequest`          | `PlayTTSResponse`          | Supports priority control and interruption strategy                | http                  |
| `TTSService.PlayMediaFile`               | Play local audio file                          | `PlayMediaFileRequest`    | `PlayTTSResponse`          | Supports PCM/WAV format file playback                              | http                  |
| `TTSService.GetAudioStatus`              | Query TTS/audio file status                    | `GetTTSStatusRequest`     | `GetTTSStatusResponse`     | Get current playback status and queue information                  | http                  |
| `/interaction/tts_status`                | Query TTS/audio file status                    | `TTSStatus`               | `-`                        | Get current playback status and queue information                  | ros2                  |
| `TTSService.StopTTSTraceId`              | Stop TTS/audio file playback with specified id | `StopTTSTraceIdRequest`   | `CommonResponse`           | Only terminates the broadcast task with the specified trace\_id    | http                  |
| `TTSService.StopTTS`                     | Stop all TTS/audio file playback               | `CommonRequest`           | `CommonResponse`           | Terminates the current broadcast and all tasks in the queue        | http                  |
| `HalAudioService.GetAudioVolume`         | Get volume level                               | `CommonRequest`           | `VolumeResponse`           | Get current volume level                                           | http                  |
| `HalAudioService.SetAudioVolume`         | Set volume level                               | `VolumeRequest`           | `AudioCommonResponse`      | Adjust current volume level                                        | http                  |
| `MotionCommandService.SendMotionCommand` | Play specified motion file                     | `MotionCommandRequest`    | `CommonResponse`           | Can only be called under JOINT\_SERVO suffix motion control Action | http                  |
| `MotionCommandService.GetMotionStatus`   | Query motion playback status                   | `CommonRequest`           | `MotionCommandResponse`    | Get current motion playback status                                 | http                  |
| `ResourceService.GetMotion`              | Get motion list                                | `GetMotionReq`            | `GetMotionResp`            | Path can find corresponding files on x86                           | http                  |
| `RcMotionPlayerService.PlayerMotion`     | Play motion with specified id                  | `RcPlayerMotionRequest`   | `CommonResponse`           | Can only be called under JOINT\_SERVO suffix motion control Action | http                  |
| `ResourceService.GetEmoticon`            | Get emoticon list                              | `GetEmoticonReq`          | `GetEmoticonResp`          | Path can find corresponding files on x86                           | http                  |
| `RcEmoticonPlayerService.PlayerEmoticon` | Play emoticon with specified id                | `RcPlayerEmoticonRequest` | `RcPlayerEmoticonResponse` | Only plays the specified motion\_id emoticon                       | http                  |
| `/agent/vision/face_id`                  | Face recognition result                        | `FaceIdResult`            | `-`                        | Requires source environment to use                                 | ros2                  |

For detailed information on interaction-related interfaces, refer to the documentation for motion playback, emoticon playback, TTS/audio playback, and microphone management. Example files for interaction-related interfaces are provided in the AimDK package under the directories examples/rc, examples/motion\_player, examples/agent, and examples/hal\_audio.

#### 9.2 Complete Takeover of Secondary Development <a href="#web-09-9-2-complete-takeover-of-secondary-development" id="web-09-9-2-complete-takeover-of-secondary-development"></a>

The modules involved in the Agibot interaction chain are two, namely agent and hal\_audio, which can be simply understood as the agent module managing the microphone part, and the hal\_audio module managing the speaker part. The agent module collects audio and performs speech recognition, then interacts with the cloud model, and after obtaining the result, sends it to the hal\_audio module, which then performs corresponding voice playback, actions, expressions, etc., based on the result.

**9.2.1 Exit the Agibot Interaction Chain**

In this mode, it is necessary to have the Agibot interaction program exit the interaction chain, output only the noise-reduced microphone audio, face recognition results, and relinquish control of the speaker. Two operations need to be performed:

1. Adjust the agent module to only\_voice / voice\_face mode, using the `SetAgentPropertiesRequest` interface in the microphone management section.

* only\_voice: Outputs only the noise-reduced microphone audio /agent/process\_audio\_output, and all subsequent chains are disconnected.
*   voice\_face: Outputs the noise-reduced microphone audio /agent/process\_audio\_output and face recognition results /agent/vision/face\_id, and all subsequent chains are disconnected.\
    For example, the rpc call required to adjust to only\_voice mode is as follows:bash

    <pre data-collapsed-line-count="10"><code>curl -i \
        -H 'content-type:application/json' \
        -X POST 'http://192.168.100.110:59301/rpc/aimdk.protocol.AgentControlService/SetAgentPropertiesRequest' \
        -d '{ "contents": { "properties": { "2": "only_voice" } } }'
    </code></pre>

    \
    After the call, the robot needs to be restarted for the changes to take effect. You can wait until the second step's modifications are completed before restarting together. After the restart, you can use the `GetAgentPropertiesRequest` interface in the microphone management section to query the current interaction mode and determine if the mode has been successfully modified. (If recovery is needed, change "only\_voice / voice\_face" in the `SetAgentPropertiesRequest` interface to "normal" and restart the robot.)

2.  Modify the configuration to default not start the hal\_audio module (modify once, no need to repeat)\
    First, back up the /agibot/software/v0/entry/bin/cfg/run\_agibot.yaml file on ORIN.bash

    <pre data-collapsed-line-count="10"><code>cp /agibot/software/v0/entry/bin/cfg/run_agibot.yaml  /agibot/software/v0/entry/bin/cfg/run_agibot.yaml.backup
    </code></pre>

    \
    Then, in the run\_agibot.yaml file, delete the hal\_audio module from the default\_apps, do not modify other parts. After the modification, restart the robot. (If recovery is needed, restore the above file and restart the robot.)<br>

    <figure><img src="../../.gitbook/assets/unknown (373).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

After the above operations, the Agibot interaction has exited the interaction chain.

**9.2.2 Acquisition of Microphone Audio**

> Note: To obtain the following audio, the robot must be powered on and connected to the network for at least 2 minutes to complete audio-related authentication operations. Otherwise, there will be no raw audio output. For offline use, please ensure that this interface has audio output before disconnecting from the network.

After exiting the interaction chain, you can obtain the denoised microphone audio information of the body through the denoised microphone audio Topic interface `/agent/process_audio_output`. The sample program for obtaining the denoised microphone audio of the body is as follows:

python

{% code collapsedlinecount="10" %}
```
#!/usr/bin/env python3

import rclpy
from rclpy.node import Node
from rclpy.qos import QoSHistoryPolicy, QoSProfile, QoSReliabilityPolicy
from ros2_plugin_proto.msg import RosMsgWrapper

from aimdk.protocol_pb2 import ProcessedAudioOutput, AudioVADState

import datetime
import os

class AudioSubscriber(Node):
    def __init__(self):
        super().__init__("audio_subscriber")

        # Audio buffer, stored separately by stream_id
        self.audio_buffers = {}  # {stream_id: bytearray()}
        self.recording_state = {}  # {stream_id: bool} Record whether recording is in progress

        # Create audio file storage directory
        self.audio_output_dir = "audio_recordings"
        os.makedirs(self.audio_output_dir, exist_ok=True)

        qos_profile = QoSProfile(
            history=QoSHistoryPolicy.KEEP_LAST,
            depth=10,
            reliability=QoSReliabilityPolicy.BEST_EFFORT,
        )

        self.subscription = self.create_subscription(
            RosMsgWrapper,
            "/agent/process_audio_output/pb_3Aaimdk_2Eprotocol_2EProcessedAudioOutput",
            self.audio_callback,
            qos_profile,
        )

        self.get_logger().info("Start subscribing to denoised audio data...")

    def audio_callback(self, msg):
        try:
            # Check if the serialization type is pb
            if msg.serialization_type != "pb":
                self.get_logger().warn(f"Unsupported serialization type: {msg.serialization_type}")
                return

            # Convert the data field from list[bytes] to bytes
            audio_data_bytes = b"".join(msg.data)

            # Use the generated protobuf class to parse the message
            processed_audio = ProcessedAudioOutput()
            processed_audio.ParseFromString(audio_data_bytes)

            self.get_logger().info(
                f"Received audio data: stream_id={processed_audio.stream_id}, "
                f"vad_state={processed_audio.vad_state}, "
                f"audio_size={len(processed_audio.audio_data)} bytes"
            )

            # Process audio based on VAD state
            self.handle_vad_state(processed_audio)

        except Exception as e:
            self.get_logger().error(f"Error processing audio message: {e}")

    def handle_vad_state(self, processed_audio):
        """Process different VAD states"""
        vad_state = processed_audio.vad_state
        stream_id = processed_audio.stream_id
        audio_data = processed_audio.audio_data

        # Initialize the buffer for this stream_id (if it does not exist)
        if stream_id not in self.audio_buffers:
            self.audio_buffers[stream_id] = bytearray()
            self.recording_state[stream_id] = False

        # VAD state name mapping
        vad_state_names = {
            AudioVADState.AUDIO_VAD_STATE_NONE: "No Speech",
            AudioVADState.AUDIO_VAD_STATE_BEGIN: "Speech Begin",
            AudioVADState.AUDIO_VAD_STATE_PROCESSING: "Speech Processing",
            AudioVADState.AUDIO_VAD_STATE_END: "Speech End",
        }

        stream_names = {1: "Built-in Microphone", 2: "External Microphone"}

        self.get_logger().info(
            f"[{stream_names.get(stream_id, f'Unknown Stream {stream_id}')}] "
            f"VAD State: {vad_state_names.get(vad_state, f'Unknown State {vad_state}')} "
            f"Audio Data: {len(audio_data)} bytes"
        )

        # Process audio data based on VAD state
        if vad_state == AudioVADState.AUDIO_VAD_STATE_BEGIN:
            self.get_logger().info("🎤 Speech detected, starting")
            # Start a new recording, clear the buffer
            self.audio_buffers[stream_id].clear()
            self.recording_state[stream_id] = True
            # Add current audio data
            if len(audio_data) > 0:
                self.audio_buffers[stream_id].extend(audio_data)

        elif vad_state == AudioVADState.AUDIO_VAD_STATE_PROCESSING:
            self.get_logger().info("🔄 Speech processing...")
            # If recording, continue adding audio data to the buffer
            if self.recording_state[stream_id] and len(audio_data) > 0:
                self.audio_buffers[stream_id].extend(audio_data)

        elif vad_state == AudioVADState.AUDIO_VAD_STATE_END:
            self.get_logger().info("✅ Speech ended")
            # Add the final audio data
            if self.recording_state[stream_id] and len(audio_data) > 0:
                self.audio_buffers[stream_id].extend(audio_data)

            # Save the complete audio segment
            if (
                self.recording_state[stream_id]
                and len(self.audio_buffers[stream_id]) > 0
            ):
                self.save_audio_segment(bytes(self.audio_buffers[stream_id]), stream_id)

            # End recording
            self.recording_state[stream_id] = False

        elif vad_state == AudioVADState.AUDIO_VAD_STATE_NONE:
            # No speech state, do not record
            if self.recording_state[stream_id]:
                self.get_logger().info("⏹️ Recording state reset")
                self.recording_state[stream_id] = False

        # Output current buffer status
        if stream_id in self.audio_buffers:
            buffer_size = len(self.audio_buffers[stream_id])
            recording = self.recording_state[stream_id]
            self.get_logger().debug(
                f"[Stream {stream_id}] Buffer size: {buffer_size} bytes, Recording status: {recording}"
            )

    def save_audio_segment(self, audio_data, stream_id):
        """Save audio segment 16kHz, 16-bit, mono PCM"""
        if len(audio_data) > 0:
            timestamp = datetime.datetime.now().strftime("%Y%m%d_%H%M%S_%f")

            # Create subdirectory by stream_id
            stream_dir = os.path.join(self.audio_output_dir, f"stream_{stream_id}")
            os.makedirs(stream_dir, exist_ok=True)

            # Generate filename
            stream_names = {1: "internal_mic", 2: "external_mic"}
            stream_name = stream_names.get(stream_id, f"stream_{stream_id}")
            filename = f"{stream_name}_{timestamp}.pcm"
            filepath = os.path.join(stream_dir, filename)

            try:
                with open(filepath, "wb") as f:
                    f.write(audio_data)
                self.get_logger().info(
                    f"Audio segment saved: {filepath} (Size: {len(audio_data)} bytes)"
                )

                # Calculate audio duration (assuming 16kHz, 16-bit, mono)
                sample_rate = 16000
                bits_per_sample = 16
                channels = 1
                bytes_per_sample = bits_per_sample // 8
                total_samples = len(audio_data) // (bytes_per_sample * channels)
                duration_seconds = total_samples / sample_rate

                self.get_logger().info(
                    f"Audio duration: {duration_seconds:.2f} seconds ({total_samples} samples)"
                )

            except Exception as e:
                self.get_logger().error(f"Failed to save audio file: {e}")

    def get_buffer_info(self):
        """Get information about all buffers (for debugging)"""
        info = {}
        for stream_id in self.audio_buffers:
            info[stream_id] = {
                "buffer_size": len(self.audio_buffers[stream_id]),
                "recording": self.recording_state[stream_id],
            }
        return info

def main(args=None):
    rclpy.init(args=args)

    audio_subscriber = AudioSubscriber()

    try:
        audio_subscriber.get_logger().info("Listening for denoised audio data, press Ctrl+C to exit...")
        rclpy.spin(audio_subscriber)
    except KeyboardInterrupt:
        audio_subscriber.get_logger().info("Exit signal received, shutting down...")
    finally:
        audio_subscriber.destroy_node()
        rclpy.shutdown()

if __name__ == "__main__":
    main()
```
{% endcode %}

The above program depends on the Python protocol package a2\_aimdk and the ROS2 protocol package ros2\_plugin\_proto. The corresponding packages have been placed in the prebuilt directory of the AimDK development kit. Install the Python package using `pip install prebuilt/a2_aimdk-1.0.0-py3-none-any.whl`, and source the ROS2 package using `source prebuilt/ros2_plugin_proto_aarch64/share/ros2_plugin_proto/local_setup.bash`.

Please note that the above program receives ROS2 messages and requires the following environment variables to be set:

bash

{% code collapsedlinecount="10" %}
```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
```
{% endcode %}

The audio data is 16kHz sample rate, 16-bit mono PCM data (little-endian). The output audio is clean human voice that has undergone denoising, echo cancellation, etc., and can be directly used for ASR recognition.

The `ProcessedAudioOutput` message contains the following fields:

| Field Name  | Type          | Description                                                      |
| ----------- | ------------- | ---------------------------------------------------------------- |
| header      | Header        | General message header containing timestamp and message ID       |
| stream\_id  | uint32        | Audio stream ID (1: built-in microphone, 2: external microphone) |
| vad\_state  | AudioVADState | Voice Activity Detection (VAD) state                             |
| audio\_data | bytes         | Denoised PCM audio data                                          |

The `AudioVADState` enumeration is defined as:

| Enum Value                    | Value | Description       |
| ----------------------------- | ----- | ----------------- |
| AUDIO\_VAD\_STATE\_NONE       | 0     | No Speech         |
| AUDIO\_VAD\_STATE\_BEGIN      | 1     | Speech Begin      |
| AUDIO\_VAD\_STATE\_PROCESSING | 2     | Speech Processing |
| AUDIO\_VAD\_STATE\_END        | 3     | Speech End        |

Note: In the current version, there is an issue with the vad\_state output by the external microphone interface. The expected state sequence for a single voice input is 122222222223, whereas the actual output is 0111111111112. This issue occurs exclusively with the external microphone (the built-in microphone functions normally) and is scheduled to be fixed in a subsequent release. For the current version, it is recommended to manually apply a +1 offset compensation to the state values.

**9.2.3 Speaker audio playback**

> Note: The robot's speaker volume setting must not exceed 70%. Exceeding this range will cause the speaker to operate beyond its rated capacity after being amplified by the amplifier, resulting in damage to the speaker.

You can use the following devices for playback. Please implement the program calls yourself. Audio channels, logical devices, and other configurations can be found in the /etc/asound.conf file on ORIN. For detailed instructions on audio playback, please refer to the next section.

bash

{% code collapsedlinecount="10" %}
```
aplay -D multiplay_def -c 1 -r 24000 -f S16_LE /agibot/data/var/interaction/audio/wake.pcm
```
{% endcode %}

Here are the volume control instructions:

1. P1 Machine

* Set playback volume

bash

{% code collapsedlinecount="10" %}
```
amixer cset name='x Headphone Volume' 15（0~31）
```
{% endcode %}

* Get playback volume

bash

{% code collapsedlinecount="10" %}
```
amixer cget name='x Headphone Volume'
```
{% endcode %}

* Set mute

bash

{% code collapsedlinecount="10" %}
```
amixer sset 'x Headphone Left' off
amixer sset 'x Headphone Right' off
```
{% endcode %}

* Unmute
*   bash

    <pre data-collapsed-line-count="10"><code>amixer sset 'x Headphone Left' on
    amixer sset 'x Headphone Right' on
    </code></pre>

    2. T3 Machine

    * Set playback volume

    bash

    <pre data-collapsed-line-count="10"><code>amixer -c DefPDevice sset Speaker 80%（0~100%）
    </code></pre>

    * Get playback volume

    bash

    <pre data-collapsed-line-count="10"><code>amixer -c DefPDevice sget Speaker
    </code></pre>

    * Set mute

    bash

    <pre data-collapsed-line-count="10"><code>amixer -c DefPDevice set Speaker off
    </code></pre>

    * Unmute

    bash

    <pre data-collapsed-line-count="10"><code>amixer -c DefPDevice set Speaker on
    </code></pre>

    **9.2.4 Face Recognition**

    > Notice：If the release operation for the interactive camera in "7.4.4 Camera Device Release" is executed before obtaining the face recognition result, the camera data stream will be interrupted, causing the face recognition to be unable to obtain image data, thus affecting the normal use of the function.

    If the agent is set to voice\_face mode, in addition to the denoised microphone audio Topic interface, it will simultaneously return the face recognition result Topic interface `/agent/vision/face_id`. This message is not available in only\_voice mode.

    The sample program for obtaining face recognition results is as follows:

    python

    <pre data-collapsed-line-count="10"><code>#!/usr/bin/env python3

    import rclpy
    from rclpy.node import Node
    from rclpy.qos import QoSHistoryPolicy, QoSProfile, QoSReliabilityPolicy
    from ros2_plugin_proto.msg import RosMsgWrapper

    from aimdk.protocol_pb2 import FaceIdResult


    class FaceIdSubscriber(Node):
        def __init__(self):
            super().__init__("face_id_subscriber")

            qos_profile = QoSProfile(
                history=QoSHistoryPolicy.KEEP_LAST,
                depth=10,
                reliability=QoSReliabilityPolicy.BEST_EFFORT,
            )

            self.subscription = self.create_subscription(
                RosMsgWrapper,
                "/agent/vision/face_id/pb_3Aaimdk_2Eprotocol_2EFaceIdResult",
                self.face_id_callback,
                qos_profile,
            )

            self.get_logger().info("Subscription started FaceID data...")

        def face_id_callback(self, msg):
            try:
                if msg.serialization_type != "pb":
                    self.get_logger().warn(
                        f"Received unsupported serialization type: {msg.serialization_type}"
                    )
                    return

                # Concatenate bytes
                raw_bytes = b"".join(msg.data)

                # Parse protobuf
                face_id_result = FaceIdResult()
                face_id_result.ParseFromString(raw_bytes)

                # log output
                import json
                from google.protobuf.json_format import MessageToDict
                self.get_logger().info(
                    f"FaceID result: {json.dumps(MessageToDict(face_id_result, preserving_proto_field_name=True), ensure_ascii=False, indent=2)}")

            except Exception as e:
                self.get_logger().error(f"parse FaceID Error while processing data: {e}")


    def main(args=None):
        rclpy.init(args=args)
        node = FaceIdSubscriber()

        try:
            node.get_logger().info("Listening FaceID data，press Ctrl+C exit...")
            rclpy.spin(node)
        except KeyboardInterrupt:
            node.get_logger().info("Exiting...")
        finally:
            node.destroy_node()
            rclpy.shutdown()


    if __name__ == "__main__":
        main()
    </code></pre>

    The above program depends on the Python protocol package a2\_aimdk and the ROS2 protocol package ros2\_plugin\_proto. The corresponding packages have been placed in the prebuilt directory of the AimDK development kit. Install the Python package using `pip install prebuilt/a2_aimdk-1.0.0-py3-none-any.whl`, and source the ROS2 package using `source prebuilt/ros2_plugin_proto_aarch64/share/ros2_plugin_proto/local_setup.bash`.

    Please note that the above program receives ROS2 messages and requires the following environment variables to be set:

    bash

    <pre data-collapsed-line-count="10"><code>source /opt/ros/humble/setup.bash
    export ROS_DOMAIN_ID=232
    export ROS_LOCALHOST_ONLY=0
    export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
    </code></pre>

    A local face registration interface is also provided. This interface is neither a conventional HTTP JSON RPC nor a ROS2 Topic; instead, a dedicated invocation script is provided: examples/agent/run\_face\_id\_register.sh. The content is as follows:

    bash

    <pre data-collapsed-line-count="10"><code>#!/bin/bash

    # 1. Directory containing images to be registered (same level as the sh script)
    RUN_SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" &#x26;&#x26; pwd)"
    IMAGES_DIR="${RUN_SCRIPT_DIR}/images"

    # 2. Faceid base directory
    FACEID_SCRIPT_DIR="/agibot/software/v0/scripts/agent/face_id/"
    FACEID_LIB_DIR="/agibot/software/v0/bin"
    FACEID_OFFLINE_FEAT="/agibot/data/param/interaction/face_id/offline_face_features"

    # 3. Relative paths of the executable file and configuration file
    EXEC="${FACEID_SCRIPT_DIR}/face_id_register"
    CONF="${FACEID_SCRIPT_DIR}/face_id_config.json"

    chmod +x "$EXEC"
    export LD_LIBRARY_PATH="${FACEID_LIB_DIR}":$LD_LIBRARY_PATH

    # 4. Call
    rm -rf "$FACEID_OFFLINE_FEAT"/*
    "$EXEC" "$CONF" "$IMAGES_DIR"
    </code></pre>

    Place the facial data to be registered into the images directory located in the same folder as the script. Execute this script on the ORIN to complete the registration. After registration, the correspondence between IDs and images, along with the registration success status, will be stored in the Result.txt file in the same directory. See the example below (note that registration was successful even for blurred images and images where the face was too small; however, for actual usage, it is still recommended to use clear, frontal facial images as shown in the satisfied.png to avoid negative impacts on the recognition rate):

    text

    <pre data-collapsed-line-count="10"><code>GID17648293009168001    satisfactory.png          OK    Registration successful
    GID17648293018063607    side-face.png          FAIL  Face quality does not meet requirements
    GID17648293020281011    too-dark.png          FAIL  Face quality does not meet requirements
    GID17648293021878934    blurred.png          OK    Registration successful
    GID17648293024764703    overexposed.png          FAIL  Face quality does not meet requirements
    GID17648293026684491    No face.png       FAIL  No face detected
    GID17648293028768487    Not a face.png       FAIL  No face detected
    GID17648293030305970    Face too small.png    OK    Registration successful
    </code></pre>

    Face Registration and Recognition Logic Rules:

    1. Place facial images in the images directory. The images must be in JPG, PNG, or JPEG format and contain only one clear, frontal face. Run the script to register them. After registration, restart the agent by executing `aima em stop-app agent && aima em start-app agent` on the ORIN, or simply reboot the robot.
    2. The registered facial features will be stored locally on the ORIN at the following path: /agibot/data/param/interaction/face\_id/offline\_face\_features.
    3. The construction rule for the registered User ID (UID) is: "GID" + Timestamp + 4-digit random number. Upon publishing, the current machine's Serial Number (SN) from /agibot/data/info/sn will replace "GID" to form the new UID.
    4. Faces can also be uploaded via the Lingxin platform, which we refer to as the Cloud Face Database. This database allows configuration of greetings, etc. The corresponding content is downloaded and stored in the user\_info.json file on the ORIN at the following path: /agibot/data/param/interaction/face\_id/user\_info.json.
    5. Important: Each execution of the aforementioned script will clear the existing local database. Therefore, you must re-register all facial data completely every time. Maintain a single images folder containing all faces that need to be recognized, and rerun the registration script whenever there are any additions, deletions, or modifications.
    6. The matching rule always prioritizes the Cloud Face Database first, followed by the local database. Once the first successful match is found, the system will stop searching the remaining faces.

    **9.2.5 Wake-Up Result Reporting**

    If `agent` is set to `only_voice` mode, the wake-up result reporting topic is `/agent/wakeup/pb_3Aaimdk_2Eprotocol_2EWakeUpResult`.

    Example program for receiving wake-up result reports:

    python

    <pre data-collapsed-line-count="10"><code>#!/usr/bin/env python3

    import rclpy
    from rclpy.node import Node
    from rclpy.qos import (
        QoSDurabilityPolicy,
        QoSHistoryPolicy,
        QoSProfile,
        QoSReliabilityPolicy,
    )
    from ros2_plugin_proto.msg import RosMsgWrapper

    from aimdk.protocol_pb2 import WakeUpResult


    TOPIC = "/agent/wakeup/pb_3Aaimdk_2Eprotocol_2EWakeUpResult"


    class WakeUpSubscriber(Node):
        def __init__(self):
            super().__init__("wakeup_result_subscriber")

            qos_profile = QoSProfile(
                history=QoSHistoryPolicy.KEEP_LAST,
                depth=10,
                reliability=QoSReliabilityPolicy.RELIABLE,
                durability=QoSDurabilityPolicy.VOLATILE,
            )

            self.subscription = self.create_subscription(
                RosMsgWrapper,
                TOPIC,
                self.wakeup_callback,
                qos_profile,
            )

            self.get_logger().info(f"Subscription started WakeUpResult: {TOPIC}")

        def wakeup_callback(self, msg):
            try:
                if msg.serialization_type != "pb":
                    self.get_logger().warn(
                        f"Received unsupported serialization type: {msg.serialization_type}"
                    )
                    return

                # Join bytes
                raw_bytes = b"".join(msg.data)

                # Parse protobuf
                wakeup_result = WakeUpResult()
                wakeup_result.ParseFromString(raw_bytes)

                # Log output
                import json
                from google.protobuf.json_format import MessageToDict

                self.get_logger().info(
                    f"WakeUpResult: {json.dumps(MessageToDict(wakeup_result, preserving_proto_field_name=True), ensure_ascii=False, indent=2)}"
                )

            except Exception as e:
                self.get_logger().error(f"parse WakeUpResult Error while processing data: {e}")


    def main(args=None):
        rclpy.init(args=args)
        node = WakeUpSubscriber()

        try:
            node.get_logger().info("Listening WakeUpResult，press Ctrl+C exit...")
            rclpy.spin(node)
        except KeyboardInterrupt:
            node.get_logger().info("Exiting...")
        finally:
            node.destroy_node()
            rclpy.shutdown()


    if __name__ == "__main__":
        main()
    </code></pre>

    The above program depends on the Python protocol package `a2_aimdk` and the ROS2 protocol package `ros2_plugin_proto`. Both packages are already included in the `prebuilt` directory of the AimDK development package. Install the Python package with `pip install prebuilt/a2_aimdk-2.0.1-py3-none-any.whl`, and source the ROS2 package with `source prebuilt/ros2_plugin_proto_aarch64/share/ros2_plugin_proto/local_setup.bash`.

    Please note that the above program receives ROS2 messages and requires the following environment variables:

    bash

    <pre data-collapsed-line-count="10"><code>source /opt/ros/humble/setup.bash
    export ROS_DOMAIN_ID=232
    export ROS_LOCALHOST_ONLY=0
    export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
    </code></pre>

    ### 10. Troubleshooting Interface Calls <a href="#troubleshooting-interface-calls" id="troubleshooting-interface-calls"></a>

    #### 10.1 Troubleshooting Approach <a href="#web-10-10-1-troubleshooting-approach" id="web-10-10-1-troubleshooting-approach"></a>

    The general troubleshooting methods for HTTP JSON RPC and ROS2 Topic are different, but there are also some common troubleshooting methods for on-board issues.

    **10.1.1 HTTP JSON RPC**

    1. Check if the corresponding IP is the correct x86/orin industrial PC IP and if it can be pinged.
    2. Check if the HTTP URL is correct; you can refer to the example scripts or interface documentation.
    3. Check if the corresponding port has a service running. After SSHing into the x86, you can use the command `lsof -i:xxxx` in the terminal to check if a service is running on the corresponding port.
    4. If you get a "Connection Refused" error, it means the IP might not be reachable or the port service is not started.
    5. If you get an "HTTP deserialize failed" error, it means the JSON body fields may be incorrectly filled. You can refer to the example scripts or interface documentation for comparison.

    **10.1.2 ROS2 Topic**

    1. Check if the on-board ROS2 dds configuration includes the IP of the network card being used. Ensure that both privileged and non-privileged configurations correctly add the network card IP. After adding, a full reboot is required.
    2. Check if you are using the ROS2 Humble with Fastdds version.
    3. Check if the local environment variables `ROS_DOMAIN_ID=232` and `ROS_LOCALHOST_ONLY=0` are loaded. The exported environment variables only take effect in the current terminal. A new terminal will need to re-export these variables. You can use the command `env | grep ROS` to view the relevant environment variable settings in the current terminal.
    4.  Ensure that the QoS of the topic is consistent with the default QoS on the board.yaml

        <pre data-collapsed-line-count="10"><code>  history: keep_last
          depth: 10
          reliability: best_effort
        </code></pre>
    5. After SSHing into the x86/orin industrial PC, execute `aima em load-env` (to load the ROS2 environment variables) and then use the `ros2 topic` command to check if the related topics are being sent or received by any modules.

    **10.1.3 Common Troubleshooting Methods**

    1. Use AimMaster to check if the robot has any health alerts. In the case of a robot fault, it may affect some interface calls. For example, if there is a joint fault, the motion control interface may not work properly.
    2. If AimMaster is not connected, you can log into the x86 industrial PC of the robot and execute the `aima doctor` command to quickly view the health alert information.

    #### 10.2 Common Interface Questions <a href="#web-10-10-2-common-interface-questions" id="web-10-10-2-common-interface-questions"></a>

    1.  Why does calling the upper limb action interface or neck interface result in no response or severe shaking?

        1. First, confirm that the robot is in the corresponding Action mode, which should have the suffix JOINT\_SERVO.
        2. In JOINT\_SERVO mode, the control of the upper limbs and neck is preempted by the motion playback module. You need to call the `DisableMotionPlayer` interface to disable the control of the motion playback module before you can normally call the upper limb or neck control interfaces.

        yaml

        <pre data-collapsed-line-count="10"><code>curl -i \
            -H 'content-type:application/json' \
            -H 'timeout: 1000' \
            -X POST http://192.168.100.100:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer \
            -d '{}'
        </code></pre>
    2. Why does calling any motion playback only result in the right hand raising action?
       1. This is the default action of the motion playback module. When the `motion_id` parameter is incorrect, it will default to this action.
       2.  A correct motion path should find the corresponding .mcap (new version) or .db (old version) file and pass the complete path, for example:bash

           <pre data-collapsed-line-count="10"><code>/agibot/data/resources/default/motion/salute/salute.mcap
           </code></pre>

    #### 10.3 Feedback Channels <a href="#web-10-10-3-feedback-channels" id="web-10-10-3-feedback-channels"></a>

    If you encounter bugs in secondary development interfaces, you can provide feedback through the following channels:

    [https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k](https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k)

    Note

    1. This channel is only for answering questions or reporting bugs related to secondary development interfaces. For robot body faults or after-sales maintenance, please contact the delivery, operation, and after-sales teams directly. Unrelated issues will not be responded to.
    2. Please describe the problem in detail in the form, and provide reproducible steps if possible. Problems with rich information and clear descriptions will be prioritized for resolution. Vague and general problems will be given lower priority and may be ignored.
    3. Please fill out all information carefully. Inconsistent or casually filled forms will be ignored.
    4. Each ticket should focus on a single or similar issue. Do not mix multiple issues in one ticket, as this will significantly delay the processing time.

    ### 11. Frequently Asked Questions <a href="#frequently-asked-questions" id="frequently-asked-questions"></a>

    #### 11.1 What is the onboard software version? <a href="#web-11-11-1-what-is-the-onboard-software-version" id="web-11-11-1-what-is-the-onboard-software-version"></a>

    The A2 robot comes with a series of onboard software, which will be upgraded along with the OTA (Over-The-Air) updates.

    Generally, when you ssh into the robot, the software version (current application version) will be printed out. You can also check it through the AimMaster software. The version number is usually in the format of 1.2.x.

    #### 11.2 What are P1 and T3? <a href="#web-11-11-2-what-are-p1-and-t3" id="web-11-11-2-what-are-p1-and-t3"></a>

    P1 and T3 are the hardware models of the A2 robot. The main difference between these hardware models lies in the configuration of the industrial PC, such as network card configuration and hardware connections. However, the upper-level interfaces are generally unified.

    After logging into the x86 industrial PC via ssh, you can check the /etc/bsp\_version to confirm the model. If this file exists, it is P1; if it does not exist, it is T3.

    #### 11.3 How to handle the over-speed anomaly reported by the arm joint motor? <a href="#web-11-11-3-how-to-handle-the-over-speed-anomaly-reported-by-the-arm-joint-motor" id="web-11-11-3-how-to-handle-the-over-speed-anomaly-reported-by-the-arm-joint-motor"></a>

    <figure><img src="../../.gitbook/assets/unknown (374).webp" alt="11.3 How to handle the over-speed anomaly reported by the arm joint motor?"><figcaption><p>11.3 How to handle the over-speed anomaly reported by the arm joint motor?</p></figcaption></figure>

    Reason: When calling the arm interface, there is a step change between the input position and the current position, causing the motor to exceed the speed limit and trigger current limiting. At this point, the embedded system will disable the joint for protection and report an alarm.

    Solution: In most cases, restarting the robot will resolve the issue. To avoid this problem, when calling the arm ROS2 Topic interface, filter and smooth the joint positions before inputting them to ensure that the input values do not have a significant step change from the current state.

    #### 11.4 Is it possible to develop your own motion control program? <a href="#web-11-11-4-is-it-possible-to-develop-your-own-motion-control-program" id="web-11-11-4-is-it-possible-to-develop-your-own-motion-control-program"></a>

    By default, the low-level control interfaces for the lower limb joint motors are not open. Control can only be achieved through high-level speed commands. If you need to develop your own motion control algorithms to replace the Agibot factory-installed algorithms,please refer to the "A2 Ultra Low-Level Motion Control Development Guide" in the documentation. Please read the risk warnings and safety precautions for motion control development carefully before proceeding.
