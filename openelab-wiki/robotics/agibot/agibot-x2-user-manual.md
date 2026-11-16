# AgiBot X2 User Manual

### AGIBOT X2 Humanoid Robot for Embodied AI

{% embed url="https://openelab.io/products/agibot-x2-humanoid-ai-robot" %}

### Contents

* Safety, operating environment, and emergency stop
* Product configuration and specifications
* Battery status and charging
* Startup procedures
* Agibot Go app and remote controller
* Shutdown procedures

### Key Troubleshooting Index

* Unsafe floor, insufficient clearance, and fall risk
* Low battery and charging problems
* Wi-Fi, AP hotspot, and app connection
* Remote-controller pairing and mode switching
* Safe shutdown and zero-torque handling

### Safety and Operating Environment <a href="#safety-and-operating-environment" id="safety-and-operating-environment"></a>

* Operate only on a hard, level, dry, stable surface. Keep the robot away from slopes, drops, fragile floors, vibration, moisture, and extreme temperatures.
* Reserve a clear safety area around the robot. Keep personnel outside the motion path and maintain at least 0.5 m distance during normal operation; allow at least 1 m for startup, recovery, and demonstration motions.
* Before startup, verify that the battery, cables, plugs, joints, sensors, and support equipment are in normal condition.
* Use the emergency-stop combination only when necessary. Zero-torque mode releases all joints and can cause the robot to collapse; support the robot with a gantry or trained assistants.
* Never dismantle, adjust, or repair the powered robot. Stop operation immediately after a fault, fall, collision, abnormal heat, odor, sound, or battery damage.

### Product Specifications

| Parameter             | AgiBot X2                                                                                        |
| --------------------- | ------------------------------------------------------------------------------------------------ |
| Dimensions            | 1310 mm (H) x 460 mm (W) x 210 mm (L)                                                            |
| Weight                | Approx. 35 kg                                                                                    |
| Total DoF             | 25                                                                                               |
| Arm DoF               | 5 per arm                                                                                        |
| Waist DoF             | 3                                                                                                |
| Leg DoF               | 6 per leg                                                                                        |
| Arm reach             | 558 mm, excluding end effector                                                                   |
| Payload               | <p>Max. 3 kg in specified postures;<br>&#x3C;=1 kg across full range, excluding end effector</p> |
| Perception            | <p>Interactive RGB camera and head touch sensor;<br>no LiDAR or RGB-D camera</p>                 |
| Communication         | Wi-Fi and Bluetooth                                                                              |
| Battery               | Approx. 500 Wh                                                                                   |
| Operating time        | Approx. 2 hours at 0.5 m/s                                                                       |
| Charging time         | <=1.5 hours                                                                                      |
| Main compute          | RK3588 x2                                                                                        |
| Secondary development | Not supported                                                                                    |

### Battery and Charging <a href="#battery-and-charging" id="battery-and-charging"></a>

| Battery indication | State     | Required action                               |
| ------------------ | --------- | --------------------------------------------- |
| Four LEDs on       | 75-100%   | Normal operation                              |
| Three LEDs on      | 50-75%    | Normal operation                              |
| Two LEDs on        | 25-50%    | Monitor remaining runtime                     |
| One LED on         | 15-25%    | Prepare to charge or replace the battery      |
| LED1 flashing      | Below 15% | Charge immediately and prevent a powered fall |

* Power the robot off before charging. Do not send motion commands while charging.
* Charge either through the robot charging port or after removing the battery, using the approved adapter.
* Keep the charging area dry, ventilated, and away from combustible materials and heat sources.
* After a fall, inspect the battery. Do not reuse a battery with dents, cracks, swelling, leakage, or other visible damage.

### 2.1 Startup Guide <a href="#id1" id="id1"></a>

#### 2.1.1 Startup While Suspended (Gantry Required) (Recommended for SDK use)

**Step 1: Unbox and Position Properly** Open the package as shown and carefully lift the robot out. Use the support frame to suspend the robot naturally, ensuring that the feet do not touch the ground.

<figure><img src="../../.gitbook/assets/unknown (73).webp" alt="Illustration of Step 1" width="1800"><figcaption><p>Illustration of Step 1</p></figcaption></figure>

***

**Step 2: Install the Battery** If the battery is not installed, slide it from the outside into the battery slot on the robot’s back. When fully inserted, a ‘click’ sound indicates successful installation. Press again to ensure the battery is securely seated.

<figure><img src="../../.gitbook/assets/unknown (74).webp" alt="Step 2: Check and Install the Battery" width="1800"><figcaption><p>Step 2: Check and Install the Battery</p></figcaption></figure>

***

**Step 3: Power On**

* Before powering on, ensure the battery has more than 2 bars (over 50%).
* Short-press the power button on the battery to wake the device, then long-press for 5 seconds to start up.
* After powering on, the battery’s LED1–4 indicators will light up sequentially within 2 seconds, then stabilize to show battery level.

<figure><img src="../../.gitbook/assets/unknown (75).webp" alt="Step 3: Press the Power Button" width="1800"><figcaption><p>Step 3: Press the Power Button</p></figcaption></figure>

***

**Step 4: Switch to Standing Preparation (Position-Control Standing) Mode**

* **Initialization**: After powering on, wait about 1 minute without operating the robot. When all joints enter zero-torque mode, initialization is complete.
* **Adjust Suspension**: After initialization, lower the suspension rope until both feet fully touch the ground, transitioning into standing-prep mode.
* **Activate Standing-Prep Mode**: Short-press 【L2 + X】 on the controller to enter Standing Preparation (Position-Control Standing) Mode.

<figure><img src="../../.gitbook/assets/unknown (76).webp" alt="Step 13" width="1800"><figcaption><p>Step 13</p></figcaption></figure>

***

**Step 5: Complete Body Lowering**

* Use the powered gantry to slowly lower the robot until both feet fully touch the ground and the suspension rope becomes slack with extra margin.
* Ensure the robot remains upright during the process without tilting.

**Step 6: Enter Stable Standing (Force Control Standing) Mode**

Important

Note: Ensure the robot is fully lowered and both feet are fully touching the ground before switching to Stable Standing Mode.

* **Activate Stable Standing Mode**: Short-press 【R2 + X】 on the controller to switch to Standing Preparation (Position-Control Standing) Mode. Refer to the illustration for posture details.
* **Release the Hook**: Once the robot is stably standing, fully release the suspension hook.
* In Stable Standing Mode, the robot maintains balance under slight pushes and supports body motion control.

<figure><img src="../../.gitbook/assets/unknown (77).webp" alt="Step 3: Press the Power Button" width="1800"><figcaption><p>Step 3: Press the Power Button</p></figcaption></figure>

**Step 7: Enter Locomotion Mode**

After entering Stable Standing Mode, the robot supports **“push-to-walk”** behavior:

* Use the left joystick (up/down/left/right) to control walking direction.
* Push the right joystick to control in-place rotation.

***

#### 2.1.2 Startup from Supine Position (No Gantry Required)

**Step 1: Unbox and Position Properly** Open the package as shown and gently lift the robot to avoid collisions. Position the robot as shown to check battery level or install the battery.

<figure><img src="../../.gitbook/assets/unknown (78).webp" alt="Illustration of Step 1" width="1800"><figcaption><p>Illustration of Step 1</p></figcaption></figure>

***

**Step 2: Install the Battery** Slide the battery into the back slot until a ‘click’ confirms installation. Gently pull to ensure it is securely locked.

<figure><img src="../../.gitbook/assets/unknown (79).webp" alt="Step 2: Check and Install the Battery" width="1800"><figcaption><p>Step 2: Check and Install the Battery</p></figcaption></figure>

***

**Step 3: Power On**

* Before powering on, ensure the battery has more than 2 bars (over 50%).
* Short-press the power button on the battery to wake the device, then long-press for 5 seconds to start up.
* After powering on, the battery’s LED1–4 indicators will light up sequentially within 2 seconds, then stabilize to show battery level.

<figure><img src="../../.gitbook/assets/unknown (80).webp" alt="Step 3: Press the Power Button" width="1800"><figcaption><p>Step 3: Press the Power Button</p></figcaption></figure>

**Step 4: Lay the Robot Flat on Its Back**

* Place the robot in a face-up lying posture with arms and legs extended. The robot is now in zero-torque mode. _Refer to the illustration to correctly position the head, legs, arms, torso, waist, and hips, ensuring the hip orientation matches the robot’s forward direction._
* Ensure a 0.5m radius of clear space around the robot before triggering the stand-up-from-lying motion.

<figure><img src="../../.gitbook/assets/unknown (81).webp" alt="Step 4" width="1800"><figcaption><p>Step 4</p></figcaption></figure>

**Step 5: Execute Supine-to-Stand Power-On**

* Short-press 【↑ + △】 on the controller to trigger the supine-to-stand motion. The robot will then enter stable Stable Standing Mode.

<figure><img src="../../.gitbook/assets/unknown (82).webp" alt="Step 5: Supine-to-stand motion illustration" width="1800"><figcaption><p>Step 5: Supine-to-stand motion illustration</p></figcaption></figure>

**Step 6: Enter Locomotion Mode**

After entering Stable Standing Mode, the robot supports **“push-to-walk”** behavior:

* Use the left joystick (up/down/left/right) to control walking direction.
* Push the right joystick to control in-place rotation.

***

Important

1. **Do Not Perform Supine-to-Stand in the Following Cases:** When using the dexterous hand or gripper, standing up from lying is not supported to avoid hardware damage.
2. **Posture Requirements Before Standing Up**: Ensure the robot is face-up and all limbs and critical parts are positioned correctly to avoid damage.
3. **Ground Requirements:** Place the robot on a flat, hard surface with no slope before performing the stand-up motion.
4.

    #### 2.1.3 Startup from Sitting Position (No Gantry Required)

    **Step 1: Unbox and Position Properly** Open the robot’s package as shown and lift it out carefully. Position the robot as shown to check the battery or install it.

    <figure><img src="../../.gitbook/assets/unknown (83).webp" alt="Illustration of Step 1" width="1800"><figcaption><p>Illustration of Step 1</p></figcaption></figure>

    **Step 2: Install the Battery** Slide the battery into the back slot until a ‘click’ confirms installation. Gently pull to ensure it is securely locked.

    <figure><img src="../../.gitbook/assets/unknown (84).webp" alt="Step 2: Check and Install the Battery" width="1800"><figcaption><p>Step 2: Check and Install the Battery</p></figcaption></figure>

    **Step 3: Power On**

    * Before powering on, ensure the battery has more than 2 bars (over 50%).
    * Short-press the power button on the battery to wake the device, then long-press for 5 seconds to start up.
    * After powering on, the battery’s LED1–4 indicators will light up sequentially within 2 seconds, then stabilize to show battery level.

    <figure><img src="../../.gitbook/assets/unknown (85).webp" alt="Step 3: Press the Power Button" width="1800"><figcaption><p>Step 3: Press the Power Button</p></figcaption></figure>

    **Step 4: Position the Robot in Sitting Posture**

    1. **Posture Adjustment:** Position the robot as shown.
    2. **Key Requirements:**
       * Ensure the **head, legs, arms, chest, waist, and knees** are positioned correctly, especially keeping the knees facing the same direction as the robot’s front.
       * Place the robot on a **chair 35–40 cm** high with a backrest to ensure proper support.
       * The robot is now in zero-torque mode. An operator should hold the rear handle to maintain balance.
    3. **Mode Activation:** Press **【↑ + X】** simultaneously to enter sitting-prep (position-control sitting) mode.
       * During this process, an operator must hold the robot’s rear handle for balance.

    <figure><img src="../../.gitbook/assets/unknown (86).webp" alt="Step 4: Robot Positioned in Sitting Posture, Switching to Sitting-Prep Mode" width="1800"><figcaption><p>Step 4: Robot Positioned in Sitting Posture, Switching to Sitting-Prep Mode</p></figcaption></figure>

    Important

    1. **Sitting Posture Requirements:** Use the controller to adjust the robot into the sitting position-control state. Place the robot on a stable stool 35–40 cm high. Ensure both feet fully touch the ground before triggering the stand-up motion.
    2. **Limb Posture Requirements:** Ensure the head, legs, arms, chest, waist, and hips are positioned correctly and facing forward to avoid damage during mode switching.

    **Step 5: Stand Up**

    * Short-press 【↑ + □】 on the controller to trigger the stand-up-from-sitting motion. The robot will automatically enter Stable Standing Mode afterward.

    Important

    An operator must pull on the rear handle to assist balance during the stand-up-from-sitting motion to prevent falls.

    <figure><img src="../../.gitbook/assets/unknown (87).webp" alt="Step 5: Robot Standing Up" width="1800"><figcaption><p>Step 5: Robot Standing Up</p></figcaption></figure>

    **Step 6: Enter Locomotion Mode** After entering Stable Standing Mode, the robot supports **“push-to-walk”** behavior:

    * Use the left joystick (up/down/left/right) to control walking direction.
    * Push the right joystick to control in-place rotation.
    *

        ### 2.2 Robot Mobile App Connection (Agibot Go APP)

        The latest app version must match the robot’s latest firmware version. Please download the correct version.

        #### 2.2.1 Download Links

        **iOS**

        * Search the App Store for _Agibot Go APP_
        * Scan the QR code below to download Agibot Go APP

        <figure><img src="../../.gitbook/assets/unknown (88).webp" alt="iOS download QR code" width="1800"><figcaption><p>iOS download QR code</p></figcaption></figure>

        **Android**

        * Search Android app stores for _Agibot Go APP_
        * Scan the QR code below to download Agibot Go APP

        <figure><img src="../../.gitbook/assets/unknown (89).webp" alt="Android download QR code" width="1800"><figcaption><p>Android download QR code</p></figcaption></figure>

        **Operation Steps**

        **Add Robot**

        1.  Open the “Add Robot” page.

            <figure><img src="../../.gitbook/assets/unknown (90).webp" alt="Open the add page" width="1800"><figcaption><p>Open the add page</p></figcaption></figure>
        2.  Add the robot.

            <figure><img src="../../.gitbook/assets/unknown (91).webp" alt="Add Robot" width="1800"><figcaption><p>Add Robot</p></figcaption></figure>

        **Connect to the robot via Wi-Fi**

        1.  Tap **Wi-Fi Connection**.

            <figure><img src="../../.gitbook/assets/unknown (92).webp" alt="Wi-Fi Connection" width="1800"><figcaption><p>Wi-Fi Connection</p></figcaption></figure>
        2.  Enter the Wi-Fi password.

            <figure><img src="../../.gitbook/assets/unknown (93).webp" alt="Enter Wi-Fi password" width="1800"><figcaption><p>Enter Wi-Fi password</p></figcaption></figure>

        **Connect to the robot via AP Hotspot**

        1.  Tap **AP Hotspot Connection**.

            <figure><img src="../../.gitbook/assets/unknown (94).webp" alt="AP Connection" width="1800"><figcaption><p>AP Connection</p></figcaption></figure>
        2.  Select the connection.

            <figure><img src="../../.gitbook/assets/unknown (95).webp" alt="Select connection" width="1800"><figcaption><p>Select connection</p></figcaption></figure>

        **Connection Result Notification**

        1.  Connection successful.

            <figure><img src="../../.gitbook/assets/unknown (96).webp" alt="Connection successful" width="1800"><figcaption><p>Connection successful</p></figcaption></figure>
        2.  Interaction available.

            <figure><img src="../../.gitbook/assets/unknown (97).webp" alt="Interaction available" width="1800"><figcaption><p>Interaction available</p></figcaption></figure>

        ### 2.3 Remote Controller Connection

        Note

        The remote controller is pre-paired at the factory and does not require re-pairing. Simply press the central PS5-logo button to quickly establish a connection.

        #### 2.3.1 Operation Steps

        **1. Open the “Add Robot” page**

        <figure><img src="../../.gitbook/assets/unknown (98).webp" alt="Enter the Bluetooth connection interface" width="1800"><figcaption><p>Enter the Bluetooth connection interface</p></figcaption></figure>

        **2. After connecting to the robot, go to Robot Settings → Bluetooth → Select the controller to connect**

        <figure><img src="../../.gitbook/assets/unknown (99).webp" alt="Tap Bluetooth settings" width="1800"><figcaption><p>Tap Bluetooth settings</p></figcaption></figure>

        **3. Select the controller and tap to connect**

        <figure><img src="../../.gitbook/assets/unknown (100).webp" alt="Select the controller and tap to connect" width="1800"><figcaption><p>Select the controller and tap to connect</p></figcaption></figure>



        ### 2.4 Shutdown Guide

        #### 2.4.1 Assist the Robot to Lie Down (No Gantry Required)

        Important

        After the robot switches into the Standing Preparation (Position-Control Standing) mode and before it is fully laid on the ground, ensure one or two operators assist in keeping the robot stable and balanced.

        **Step 1: Enter Standing Preparation Mode (Position-Control Standing)**

        * Short-press **\[L2 + X]** on the controller to switch the robot into Standing Preparation (Position-Control Standing) mode.
        * During the operation, manually support the robot from the rear handle to prevent imbalance or falling.

        **Step 2: Lay the Robot Down**

        * Slowly lower the robot from the standing posture in Standing Preparation mode to the ground, ensuring a controlled and steady movement.
        * It is recommended that at least two operators assist to avoid the robot tipping or entering an abnormal posture during the process.

        **Step 3: Enter Zero-Torque Mode**

        * After ensuring the robot is stable and facing forward, switch it to Zero-Torque Mode using the remote controller to ensure safe shutdown.
        * During the state transition, support the robot from the rear handle or secure its back against a chair to maintain balance.

        **Recommended Procedure (Safer):**

        * First switch to Damping Mode: short-press **\[L2 + R2 + Create]** on the controller.
        * Then switch to Zero-Torque Mode: short-press **\[L1 + R1 + Create]** on the controller.

        **Emergency Stop Procedure: If an immediate stop is required, directly switch to Zero-Torque Mode via the controller.**

        <figure><img src="../../.gitbook/assets/unknown (101).webp" alt="Step 1: shutdown1" width="1800"><figcaption><p>Step 1: shutdown1</p></figcaption></figure>

        **Step 4: Power Off**

        * Short-press the power button on the back of the battery to wake the device, then long-press for about 5 seconds to shut it down.
        * During shutdown, the **LED1–4 indicators** on the battery will turn off sequentially, indicating the device has powered off.

        <figure><img src="../../.gitbook/assets/unknown (102).webp" alt="Step 4: Press the Power Button" width="1800"><figcaption><p>Step 4: Press the Power Button</p></figcaption></figure>

        **Step 5: Pack the Robot as Illustrated**

        * Open the side door of the packaging case and ensure sufficient space for placing the robot inside.
        * Follow the illustrated steps: place the robot’s legs into the positioning slot first, then fold and place the upper body into the case.
        * Ensure all parts of the robot are securely positioned in the slots, then close and lock the case.

        <figure><img src="../../.gitbook/assets/unknown (103).webp" alt="Step 5: Packing" width="1800"><figcaption><p>Step 5: Packing</p></figcaption></figure>

        #### 2.4.2 Shutdown from Sitting Posture (No Gantry Required)

        **Step 1: Use the Controller to Make the Robot Sit**

        * Short-press **\[L2 + ←]** on the controller to trigger the robot’s sitting action.
        * Place the robot on a stable platform or stool with a height of **35–40 cm** to ensure proper support.

        <figure><img src="../../.gitbook/assets/unknown (104).webp" alt="Step 1: Trigger the Sitting Motion via Controller" width="1800"><figcaption><p>Step 1: Trigger the Sitting Motion via Controller</p></figcaption></figure>

        **Step 2: Enter Zero-Torque Mode**

        * Ensure the robot is sitting stably and facing forward, then switch to Zero-Torque Mode with the controller for safe shutdown.
        * During the state transition, support the robot from the rear handle or ensure its back rests securely against a chair to prevent falls in Zero-Torque Mode.

        **Recommended Procedure (Safer):**

        * **Switch to Damping Mode first:** short-press **\[L2 + R2 + Create]**.
        * **Then switch to Zero-Torque Mode:** short-press **\[L1 + R1 + Create]**.

        **Emergency Stop:** If immediate stopping is required, directly switch to Zero-Torque Mode via the controller.

        **Step 3: Power Off**

        * Short-press the power button on the back of the battery to wake the device, then long-press for about 5 seconds to shut it down.
        * During shutdown, the **LED1–4 indicators** on the battery will turn off sequentially, indicating the device has powered off.

        <figure><img src="../../.gitbook/assets/unknown (105).webp" alt="Step 3: Press the Power Button" width="1800"><figcaption><p>Step 3: Press the Power Button</p></figcaption></figure>

        **Step 4: Pack the Robot as Shown**

        * Open the side door of the packaging case and ensure sufficient space for placing the robot inside.
        * Follow the illustrated steps: place the robot’s legs into the positioning slot first, then fold and place the upper body into the case.
        * Ensure all parts of the robot are securely positioned in the slots, then close and lock the case.

        <figure><img src="../../.gitbook/assets/unknown (106).webp" alt="shutdown_3" width="1800"><figcaption><p>shutdown_3</p></figcaption></figure>

        Important

        * During the sitting operation, ensure the robot is securely positioned on a 35–40 cm-high stool or platform with proper back support.
        * When switching from sitting posture to Zero-Torque Mode, manually support the robot from the rear handle to maintain balance and prevent falls.
