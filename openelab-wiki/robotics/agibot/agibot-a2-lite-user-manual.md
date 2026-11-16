# AgiBot A2 Lite User Manual

### AGIBOT A2 Lite Humanoid Robot for Robotics Research

{% embed url="https://openelab.io/products/agibot-a2-lite-humanoid-robot" %}

### Contents

Product overview, specifications, workspace, and network topology; operating guide; software architecture; secondary-development setup; motion, action, audio/video, diagnostics, and system-status interfaces; simulation; troubleshooting; and frequently asked questions

### Key Troubleshooting Index

* Startup, remote operation, and shutdown
* Secondary-development environment and deployment
* Fault diagnosis and system status
* Interface-call troubleshooting
* Frequently asked questions

### 1. A2 Lite Overview <a href="#web-01-1-a2-lite-overview" id="web-01-1-a2-lite-overview"></a>

#### 1.1 Component Description <a href="#web-01-1-1-component-description" id="web-01-1-1-component-description"></a>

<figure><img src="../../.gitbook/assets/unknown (107).webp" alt="1.1 Component Description"><figcaption><p>1.1 Component Description</p></figcaption></figure>

#### 1.2 Network Topology <a href="#web-01-1-2-network-topology" id="web-01-1-2-network-topology"></a>

The A2 Lite has two different hardware models, with different suppliers, so the network topology also varies. These are referred to as the T3 model and the P1 model.

You can determine which model it is by checking the network interface name using the `ip a` command on the actual machine.

**1.2.1 T3 Model**

Hardware Architecture Diagram

<figure><img src="../../.gitbook/assets/unknown (108).webp" alt="Hardware Architecture Diagram"><figcaption><p>Hardware Architecture Diagram</p></figcaption></figure>

Software Network Topology Diagram

<figure><img src="../../.gitbook/assets/unknown (109).webp" alt="Software Network Topology Diagram"><figcaption><p>Software Network Topology Diagram</p></figcaption></figure>

Where:

* The right debug network port is the debugging network port at the back of the robot, with a fixed IP address of 192.168.2.50.
* `enp3s0` is the reserved network port for adding a computing platform, and it is recommended to use this port when adding a computing platform.

**1.2.2 P1 Model**

Hardware Architecture Diagram

<figure><img src="../../.gitbook/assets/unknown (110).webp" alt="Hardware Architecture Diagram"><figcaption><p>Hardware Architecture Diagram</p></figcaption></figure>

Software Network Topology Diagram

<figure><img src="../../.gitbook/assets/unknown (111).webp" alt="Software Network Topology Diagram"><figcaption><p>Software Network Topology Diagram</p></figcaption></figure>

Where:

* The right debug network port is the debugging network port at the back of the robot, with a fixed IP address of 192.168.2.50.
* `eth_to_orin` is the reserved network port for adding a computing platform, and it is recommended to use this port when adding a computing platform.

#### 1.3 Robot Specifications <a href="#web-01-1-3-robot-specifications" id="web-01-1-3-robot-specifications"></a>

| **Primary Category**          | **Secondary Category**             | **Item**                            | **Details**                                                                                             |
| ----------------------------- | ---------------------------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Product Basic Information** |                                    | Height                              | 169cm                                                                                                   |
|                               |                                    | Dimensions                          | 169(H) \* 75(W) \* 30(L) cm                                                                             |
|                               |                                    | Net Weight                          | ≈63kg                                                                                                   |
|                               |                                    | Active Degrees of Freedom           | Dual arms &#x35;_&#x32;dof, dual legs &#x36;_&#x32;dof, head 1dof                                       |
| **Product Features**          | **Electrical Performance**         | Battery Life                        | Whole machine force control standing battery life: 4h35min, whole machine walking battery life: 1h35min |
|                               |                                    | Battery Capacity                    | 14.4Ah                                                                                                  |
|                               |                                    | Charging Time                       | 2h                                                                                                      |
|                               |                                    | Charging Power                      | ≤500W                                                                                                   |
|                               |                                    | Charging Input Voltage              | 110V-220V                                                                                               |
|                               |                                    | Charger Output                      | 54.6V 8A                                                                                                |
|                               | **Environmental Adaptability**     | Operating Temperature and Humidity  | 0\~40℃, relative humidity 10% \~ 90%, no condensation                                                   |
|                               |                                    | Storage Temperature and Humidity    | -20℃\~70℃, relative humidity 10% \~ 90%, no condensation                                                |
|                               |                                    | IP Rating                           | Joint module: IP5X                                                                                      |
|                               | **Site Adaptability**              | Minimum Passage Width               | Currently, the minimum width for remote control passage >1m, navigation minimum width >2m               |
|                               |                                    | Maximum Obstacle Height             | 20mm                                                                                                    |
|                               |                                    | Maximum Running Slope               | 8% (angle 4.57 degrees)                                                                                 |
|                               | **Operation and Interaction**      | Perception Capability               | Not supported                                                                                           |
|                               |                                    | Voice Capability                    | Not supported                                                                                           |
|                               |                                    | Light Task Capability               | Not supported                                                                                           |
|                               |                                    | Remote Control Operation            | Wireless remote controller                                                                              |
|                               |                                    | Speaker                             | 5W                                                                                                      |
|                               |                                    | Dance Development                   | Supported                                                                                               |
|                               |                                    | Group Control Software              | Supported                                                                                               |
|                               | **Mobility**                       | Maximum Speed                       | Maximum speed 0.8m/s, daily use ≤0.6m/s                                                                 |
|                               |                                    | Movement Modes                      | Supports parallel movement, diagonal movement, and in-place turning                                     |
|                               | **IoT Capabilities**               | Communication Protocol              | TCP/IP                                                                                                  |
|                               |                                    | Communication Module                | Wifi                                                                                                    |
|                               | **Intelligent Control Parameters** | Basic Computing Board               | 16-core high-performance CPU                                                                            |
|                               | **Arm Typical Parameters**         | Dexterous Hand                      | Soft artificial hand                                                                                    |
|                               |                                    | Single Arm Rated Load               | 1.5kg (excluding end effector)                                                                          |
|                               |                                    | End Effector Linear Speed           | 1m/s                                                                                                    |
|                               |                                    | Arm Workspace                       | J1(Shoulder pitch): ±170°                                                                               |
|                               |                                    |                                     | J2(Shoulder roll): -30°\~95°                                                                            |
|                               |                                    |                                     | J3(Shoulder yaw): ±170°                                                                                 |
|                               |                                    |                                     | J4(Elbow pitch): -1°\~118°                                                                              |
|                               |                                    |                                     | J5(Wrist roll): ±170°                                                                                   |
|                               | **Leg Typical Parameters**         | Leg Workspace (with some deviation) | J1(Hip roll): -37\~40°                                                                                  |
|                               |                                    |                                     | J2(Hip yaw): ±75°                                                                                       |
|                               |                                    |                                     | J3(Hip pitch): -50°\~110°                                                                               |
|                               |                                    |                                     | J4(Knee pitch): -5°\~140°                                                                               |
|                               |                                    |                                     | J5(Ankle pitch): -30°\~52°                                                                              |
|                               |                                    |                                     | J6(Ankle roll): ±28°                                                                                    |
|                               | **Head Typical Parameters**        | Head Workspace                      | Rotation joint: ±45°                                                                                    |

#### 1.4 Whole Machine Workspace <a href="#web-01-1-4-whole-machine-workspace" id="web-01-1-4-whole-machine-workspace"></a>

<figure><img src="../../.gitbook/assets/unknown (112).webp" alt="1.4 Whole Machine Workspace"><figcaption><p>1.4 Whole Machine Workspace</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (113).webp" alt="1.4 Whole Machine Workspace"><figcaption><p>1.4 Whole Machine Workspace</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (114).webp" alt="1.4 Whole Machine Workspace"><figcaption><p>1.4 Whole Machine Workspace</p></figcaption></figure>

### 2. Operation Guide <a href="#operating-guide" id="operating-guide"></a>

Before performing this operation, you need to complete the unboxing of the robot according to the unboxing documentation.

#### I. Power On <a href="#web-02-i-power-on" id="web-02-i-power-on"></a>

**Step1: Open the Aim Master Client**

Turn on the official Agibot controller. The power button is located at the top; press and hold the power button until the white light next to it lights up. After the controller powers on, AimMaster will automatically open and enter the robot power-on wizard. The charging port for the robot is located at the bottom of the controller.

<figure><img src="../../.gitbook/assets/unknown (115).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

On the robot type selection screen, choose "Raise A2" and follow the "Raise A2" power-on wizard, completing the robot power-on steps as prompted.

<figure><img src="../../.gitbook/assets/unknown (116).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

**Step2: Lift the Robot**

Before powering on the robot, you need to lift it first. The robot is connected to the hook at the top of the electric lifter via a shoulder ring and cable. Manually operate the electric lifter to lift the robot to the position shown in the image, ensuring that the robot's **feet are completely off the ground**.

> Note:
>
> When moving or lifting the robot, be careful not to let the dexterous hand get squeezed or hit.

<figure><img src="../../.gitbook/assets/unknown (117).webp" alt="When moving or lifting the robot, be careful not to let the dexterous hand get squeezed or hit."><figcaption><p>When moving or lifting the robot, be careful not to let the dexterous hand get squeezed or hit.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (118).webp" alt="When moving or lifting the robot, be careful not to let the dexterous hand get squeezed or hit."><figcaption><p>When moving or lifting the robot, be careful not to let the dexterous hand get squeezed or hit.</p></figcaption></figure>

After lifting the robot, click "Next" on the AimMaster interface.

**Step3: Install the Battery and Power On**

The robot's battery is installed on its back. Ensure the battery is fully charged and slide it into the battery slot on the robot's back from top to bottom. You will hear a "click" when the battery is properly installed.

<figure><img src="../../.gitbook/assets/unknown (119).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

Press and hold the power button on the back of the robot's waist to turn it on. The LED inside the power button will light up when the power is connected.

(Power button operation: Press and hold to power on; short press followed by a long press to power off)

<figure><img src="../../.gitbook/assets/unknown (120).webp" alt="(Power button operation: Press and hold to power on; short press followed by a long press to power off)"><figcaption><p>(Power button operation: Press and hold to power on; short press followed by a long press to power off)</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (121).webp" alt="(Power button operation: Press and hold to power on; short press followed by a long press to power off)"><figcaption><p>(Power button operation: Press and hold to power on; short press followed by a long press to power off)</p></figcaption></figure>

After the robot has powered on, click "Next" on the AimMaster interface.

**Step4: Wireless E-Stop Usage**

The e-stop remote control is simple to use and is pre-paired out of the box. By default, the remote control is in the release state, and the motors are normally powered. In case of an emergency, press the button to cut off the motor power; after the problem is resolved, rotate the button to return to the release state, and the motors will be re-powered. The green light indicates normal operation, red indicates an abnormality, and four battery lights indicate full charge.

<figure><img src="../../.gitbook/assets/unknown (122).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

E-Stop Remote Control

During the robot joint self-check, the robot's neck will move slightly for self-inspection. After the robot joint self-check is complete, click "Next" on the AimMaster interface.

**Step5: Connect the Robot**

After completing the e-stop release step, AimMaster will display the robot connection interface. Click the connect button to complete the connection, or manually input the IP address to connect.

<figure><img src="../../.gitbook/assets/unknown (123).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

**Connection Method and Safety Verification:**

It is recommended to set the robot authorization password before the first use to prevent unauthorized devices from connecting.

**Connection Steps:**

**2.1 Robot IP Connection**

* Click the prompt text at the bottom of the page to bring up the input box and manually enter the IP address to connect to the robot.
* An input box for the password will pop up; enter the correct password to connect.
* If the password is incorrect, a message "Connection error, please re-enter the password" will appear.
* Each time you connect via IP, you need to enter the password, which is stored on the device.
* The robot's IP can be viewed in Settings - Wireless LAN

<figure><img src="../../.gitbook/assets/unknown (124).webp" alt="Connection Steps:"><figcaption><p>Connection Steps:</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (125).webp" alt="Connection Steps:"><figcaption><p>Connection Steps:</p></figcaption></figure>

**View/Change Password**

* Go to Settings - Authorization Password to view or change the password.
* Enter a new password (at least 8 characters) and click "Confirm."

Once the robot is successfully connected, the AimMaster interface will display "Connection Successful." Click "Next."

<figure><img src="../../.gitbook/assets/unknown (126).webp" alt="Once the robot is successfully connected, the AimMaster interface will display &#x22;Connection Successful.&#x22; Click &#x22;Next.&#x22;"><figcaption><p>Once the robot is successfully connected, the AimMaster interface will display "Connection Successful." Click "Next."</p></figcaption></figure>

**Step6: Switch to Standing Posture**

Before the robot stands, it needs to be switched to the standing posture while lifted. On the AimMaster "Switch to Standing Posture" interface, click the "Switch Posture" button. The robot will automatically adjust the head, arms, and legs to the standing posture.

In the standing posture, the robot's arms are slightly bent, the wrists are parallel to the forearms, and the legs are slightly bent with the feet roughly parallel to the ground.

> Note:
>
> During the posture switch, the robot's joints will move. Stay away from the robot and ensure there is enough space around it.

<figure><img src="../../.gitbook/assets/unknown (127).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (128).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

After the standing posture switch is complete, click "Next" on the AimMaster interface.

**Step7: Lower the Robot**

Instructions for using the electric lifter: Place the electric lifter facing the back of the robot and ensure the robot is positioned between the two feet of the lifter. Once safety is confirmed, click the lower button on the electric lifter and observe the lowering process. Continue until the robot's **feet are completely on the ground** and the suspension rope is fully relaxed with some slack.

<figure><img src="../../.gitbook/assets/unknown (129).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (130).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

After completing the lowering operation, click "Next" on the AimMaster interface.

**Step8: Switch to Standing Mode**

On the AimMaster "Switch to Standing Mode" interface, click the "Enable Standing Mode" button. The robot will enter standing mode. When you see the "Standing Success!" message, the robot has completed standing. At this point, you can remove the shoulder strap, and the robot will maintain its balance.

> Note:
>
> Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact.

<figure><img src="../../.gitbook/assets/unknown (131).webp" alt="Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact."><figcaption><p>Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (132).webp" alt="Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact."><figcaption><p>Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact.</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/unknown (133).webp" alt="Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact."><figcaption><p>Before switching to standing mode, ensure the robot is on the ground with both feet fully in contact.</p></figcaption></figure>

Click "Complete" to exit the bipedal startup wizard, and AimMaster will enter the workspace page.

<figure><img src="../../.gitbook/assets/unknown (134).webp" alt="Click &#x22;Complete&#x22; to exit the bipedal startup wizard, and AimMaster will enter the workspace page."><figcaption><p>Click "Complete" to exit the bipedal startup wizard, and AimMaster will enter the workspace page.</p></figcaption></figure>

#### II. Power Off <a href="#web-02-ii-power-off" id="web-02-ii-power-off"></a>

**Step1: Install the Hoop**

Raise the standby station arm until the robot's feet are completely off the ground.

**Step2: Lift the Robot**

Install the hoop on the robot's shoulder and use the electric lifter to lift the robot until its feet are completely off the ground.

<figure><img src="../../.gitbook/assets/unknown (135).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

**Step3: Power Off**

Press the power button in the maintenance compartment on the back of the robot's waist to turn off the robot.

#### III. Motion Control <a href="#web-02-iii-motion-control" id="web-02-iii-motion-control"></a>

**3.1 Walking Preparation**

Before remotely controlling the "Raise A2" robot to walk, ensure the robot has completed the standing process. Refer to the previous sections for the standing procedure.

After the robot has stood up, click the Toolbox panel on the left side of the AimMaster main interface to view the corresponding mode function switch bar.

<figure><img src="../../.gitbook/assets/unknown (136).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

Double-click to switch to the "Walking, Natural Arm Swing" mode. Follow the flowchart and click to execute the relevant actions. The robot will start to march in place. Switch to "Motion," and the robot will be able to perform interactive actions.

<figure><img src="../../.gitbook/assets/unknown (137).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

**3.2 Remote Walking**

Click the "Control" button on the software sidebar to enter the "Remote Walking" page.

<figure><img src="../../.gitbook/assets/unknown (138).webp" alt="Click the &#x22;Control&#x22; button on the software sidebar to enter the &#x22;Remote Walking&#x22; page."><figcaption><p>Click the "Control" button on the software sidebar to enter the "Remote Walking" page.</p></figcaption></figure>

**3.3 Interactive Actions**

Click "Interaction" on the sidebar to switch to the interaction page. Click "Action List" at the top of the screen to enter the action list page. Scroll up and down to view the pre-set robot actions, and click the play button in the upper left corner of the card to play the action. The robot will start performing the action.

Click "Custom Announcement" at the top of the screen to enter the custom announcement list page. Users can create new announcements and scroll through the list, double-clicking to play.

<figure><img src="../../.gitbook/assets/unknown (139).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

#### IV. Charging & Battery Replacement <a href="#web-02-iv-charging-battery-replacement" id="web-02-iv-charging-battery-replacement"></a>

**4.1 Charging**

**Step1: Open the Maintenance Compartment**

Open the cover of the maintenance compartment on the back of the robot.

**Step2: Insert the Charging Connector**

The charging port is located under the rear cover on the back of the robot's waist. Remove the cover and insert the power adapter's charging connector into the charging port.

<figure><img src="../../.gitbook/assets/unknown (140).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

**4.2 Battery Replacement**

**Step1: Power Off**

Refer to the power-off process in section 3.3.

**Step2: Remove the Battery**

Press the square mechanical unlock button on the top of the battery with your thumb and pull the battery upward with your other fingers to remove it.

**Step3: Install the Battery**

Refer to the battery installation process in the power-on step 3.

<figure><img src="../../.gitbook/assets/unknown (141).webp" alt="Refer to the battery installation process in the power-on step 3."><figcaption><p>Refer to the battery installation process in the power-on step 3.</p></figcaption></figure>

### 3. Overview of the Software System <a href="#web-03-3-overview-of-the-software-system" id="web-03-3-overview-of-the-software-system"></a>

The robot is equipped with an x86\_64 architecture industrial PC, running Ubuntu 22.04, and uses systemd as the system service manager. The `agibot_em.service` is configured as the entry point for the Agibot software system. This service starts automatically on boot and launches the EM (process startup management) and SM (process status management) modules. The EM and SM then work together to start the remaining module processes. The SM manages the state (start and stop) of process lists under different system modes. The configuration file paths for EM and SM are `/agibot/software/v0/entry/bin/cfg/run_agibot.yaml` and `/agibot/software/v0/entry/bin/cfg/sm.yaml`, respectively. The former lists the default processes to be started, while the latter specifies which groups of processes are enabled in each system mode.

The following diagram shows the logical layout of the main processes on the robot, displaying only the primary interaction relationships. Not all processes are started at the same time.

<figure><img src="../../.gitbook/assets/unknown (142).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

The table below provides explanations for the terms used in the diagram:

|                                     | Name                               | Description/Function                                                                                                                                                   |
| ----------------------------------- | ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AimMaster                           | Client Software                    | Used to operate the basic functions of the robot                                                                                                                       |
| OMP                                 | Agibot Cloud Platform              | Responsible for receiving and processing telemetry data from the client side                                                                                           |
| Speaker                             | Speaker                            | Used to play sounds                                                                                                                                                    |
| VR                                  | Virtual Reality Device             | Used for remote operation of the robot                                                                                                                                 |
| MCU                                 | Microcontroller                    | Controls the robot's motors, receives motor and IMU information, communicates with HAL Ethercat to receive control instructions, and uploads motor and IMU information |
| MQTT Broker                         | MQTT Gateway                       | Gateway node that interfaces with AimMaster and the onboard software                                                                                                   |
| em                                  | Process Management Module          | Responsible for starting processes and querying their status                                                                                                           |
| sm                                  | System Status Management Module    | Manages system state transitions and controls the process list                                                                                                         |
| iox\_roudi                          | Iceoryx Shared Memory Central Node | Manages the central scheduling for Iceoryx communication                                                                                                               |
| ota\_mastersota\_slave0ota\_gateway | OTA Related Function Modules       | Handles downloading OTA packages and executing the OTA process                                                                                                         |
| recordbag0                          | Data Recording Module              | Records diagnostic data packets                                                                                                                                        |
| setting                             | System Settings Module             | Manages device settings such as WIFI and volume                                                                                                                        |
| osmonitor                           | System Monitoring Module           | Monitors system resource usage and basic operational status                                                                                                            |
| resource\_manager                   | Resource Management Module         | Manages actions on the robot                                                                                                                                           |
| skillpilot                          | Skill Scheduling Module            | Manages and arbitrates the execution of basic robot skills                                                                                                             |
| data\_exporter                      | Data Export Module                 | Compresses and exports diagnostic data packets                                                                                                                         |
| reboot0                             | Reboot Script                      | Reboots the system when called by the SM                                                                                                                               |
| hds                                 | Health Diagnosis Module            | Receives and processes fault information from various modules                                                                                                          |
| Interaction                         | Voice Interaction Module           | Used for playing music and prompts, does not handle large model interactions                                                                                           |
| rc                                  | Remote Control Module              | Provides an interface for AimMaster to call basic robot functions such as expressions, movements, and walking                                                          |
| motion\_player                      | Motion Playback Module             | Plays specified motion files                                                                                                                                           |
| motion\_streamer                    | Motion Streaming Module            | Dedicated to remote operation, maps VR and motion capture suit data to the robot's upper limb joint movements                                                          |
| gateway                             | Gateway Module                     | Forwards external requests to internal modules, primarily from AimMaster                                                                                               |
| mc                                  | Motion Control Module              | Manages the overall motion control of the robot                                                                                                                        |
| hal\_ethercat                       | Hardware Abstraction Layer Module  | Communicates with the MCU via EtherCAT, transmitting hardware status and commands                                                                                      |
| elink\_log\_dump                    | EtherCAT Communication Log Module  | Logs the communication between hal\_ethercat and the MCU                                                                                                               |

Different sets of software functionalities are enabled under different system modes. The specific configurations are as follows (excerpted from `/agibot/software/v0/entry/bin/cfg/sm.yaml`):

yaml

```
 system_modes:
    "Startup": # Status Name
      next_mode_list: [ "Ready", "OTA", "Poweroff" ]  # List of Transitionable States
      active_FG_list: [ "System", "EStop", "RC", "MoCap", "Gateway" ]  # List of Functional Groups to Maintain
      action_list:
        - [ DIFF ]

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

    "Ready":
      next_mode_list: [ "Manual", "EStop", "Poweroff" ]
      active_FG_list: [ "System", "EStop", "RC", "MoCap", "Gateway" ]
      action_list:
        - [ DIFF ]

    "OTA":
      next_mode_list: [ "Reboot", "Ready", "Poweroff" ]
      active_FG_list: [ "System", "OTA", "Gateway" ]
      action_list:
        - [ DIFF ]

    "Manual":
      next_mode_list: [ "OTA", "Auto", "Reset", "EStop", "Poweroff", "Safe", "MotionStream" ]
      active_FG_list: [ "System", "EStop", "RC", "MoCap", "Gateway", "Motion" ]
      action_list:
        - [ DIFF ]
        - [ activate rc ]
      post_process:
        - level: 47
          action_list: [ [ fallback mc ] ]

    "Reset":
      next_mode_list: [ "Reboot", "Poweroff" ]
      active_FG_list: [ "System", "OTA", "Gateway" ]
      action_list:
        - [ DIFF ]

    "EStop":
      next_mode_list: [ "Ready", "OTA", "Poweroff" ]
      active_FG_list: [ "System", "EStop", "RC", "MoCap", "Gateway" ]
      action_list:
        - [ DIFF ]

    "Safe":
      next_mode_list: [ "Manual", "EStop", "Poweroff" ]
      active_FG_list: [ "System", "EStop", "Gateway", "Motion", "RC", "MoCap"]
      action_list:
        - [ DIFF ]
        - [ deactivate mc, deactivate rc  ]

    # Real-time Teleoperation Status, used for real-time teleoperation
    "MotionStream":
      next_mode_list: [ "Manual", "EStop", "Poweroff" ]
      active_FG_list: [ "System", "EStop", "RC", "Gateway", "Motion", "MoStream" ]
      action_list:
        - [ DIFF ]
        - [ activate rc ]
```

Upon startup, the system transitions from Startup to Ready and then to Manual. When it reaches the Manual state, the initialization of the onboard software can be considered complete.

### 4. Overview of Secondary Development Interfaces <a href="#secondary-development" id="secondary-development"></a>

Most of the modules in the aforementioned software system use AimRT as the underlying framework. AimRT is a robot runtime framework that aligns with ROS2, open-sourced by Agibot Robotics in September 2024. AimRT provides two basic underlying communication methods: Channel and RPC (for more details, refer to the [AimRT official documentation](https://docs.aimrt.org/v0.10.0/tutorials/concepts/concepts.html#aimrt-channel)). These two communication methods can correspond to multiple different communication backends.

To reduce the cognitive burden of secondary development, we provide two forms of relatively simple and general interfaces for secondary development: HTTP JSON RPC and ROS2 Topic. HTTP JSON RPC is suitable for low-frequency, one-to-many interface calls, while ROS2 Topic is suitable for high-frequency, many-to-many interface calls. The following are diagrams of both:

<figure><img src="../../.gitbook/assets/unknown (143).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

> For development languages, there are no restrictions on the language used for secondary development programs. As long as they can send and receive HTTP messages, they can call all HTTP JSON RPC interfaces. As long as they support ROS2 Humble and can send and receive ROS2 topic messages, they can call all the body's ROS2 Topic interfaces.

Here are two specific interface call examples to provide a clearer understanding of the interfaces:

#### 4.1 HTTP JSON RPC <a href="#web-04-4-1-http-json-rpc" id="web-04-4-1-http-json-rpc"></a>

The following is an example of a command-line RPC request to get the battery level:

bash

```
curl -i     -H 'content-type:application/json' \
            -H 'timeout: 1000'   -X POST 'http://127.0.0.1:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState' \
            -d '{}'
```

Where:

* `127.0.0.1` is the IP address of the robot's X86 development board. Here, it is set to the localhost address, which can only be called locally on the X86. For remote calls, you can change this IP to the IP corresponding to the robot's X86 development board WiFi card (which can be checked using the AimMaster software or by running `ip a` on the X86).
* `56421` is the HTTP port number for the corresponding service. This will generally be provided in detailed interface examples.
* `content-type:application/json` is the request header, indicating that the request body is in JSON format. **This request header must be included**.
* `timeout: 1000` is the request header, indicating the request timeout time in milliseconds. Here, it is set to 1000 milliseconds, or 1 second. This field is optional.
* `aimdk.protocol.HalBmsService/GetBmsState` is the name of the RPC interface for getting the battery state. The specific names of each interface can be found in the corresponding interface documentation and examples.
* `'{}'` is the request body. Here, it is empty, representing that all fields are set to their default values. If you need to pass specific fields, you can pass a JSON string, for example, `'{"bms_state": 1}'` indicates passing the `bms_state` field with a value of 1 (this is just an example; the specific field names and values should be referenced from the corresponding interface documentation and examples).

#### 4.2 ROS2 Topic <a href="#web-04-4-2-ros2-topic" id="web-04-4-2-ros2-topic"></a>

**4.2.1 Environment Variable Setup**

The topic interface uses native ROS2 topics. The default on the machine is **ROS2 Humble with Fastdds**. Before calling any ROS2 Topic interface, **you must set some environment variables** as follows:

bash

```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml
```

> If your program needs to start with root privileges, change the above dds configuration file to the following:
>
> bash
>
> ```
> export FASTRTPS_DEFAULT_PROFILES_FILE=/agibot/software/v0/entry/bin/cfg/privileged_ros_dds_configuration.xml
> ```
>
> In `ros_dds_configuration.xml`, both shared memory communication and UDP communication are enabled, while in `privileged_ros_dds_configuration.xml`, only UDP communication is enabled to avoid permission issues with shared memory.

**4.2.2 QoS Settings**

Additionally, note that the default QoS for topics on the machine is:

yaml

```
  history: keep_last
  depth: 10
  reliability: best_effort
```

When using, ensure that the QoS is consistent to guarantee smooth communication.

**4.2.3 Call Example**

The following is an example script for subscribing to joint states via ROS2 Topic.

python

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
    # Arm Joint Status: /motion/control/arm_joint_state
    # Neck Joint Status: /motion/control/neck_joint_state
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

**4.2.4 External PC Communication for ROS2 Topics**

To ensure the stability of ROS2 communication on the machine, we have modified the DDS communication configuration file. For non-root processes, shared memory communication and UDP communication are enabled by default, as shown below (located at `/agibot/software/v0/entry/bin/cfg/ros_dds_configuration.xml` on the X86 development board):

xml

```
<?xml version="1.0" encoding="UTF-8"?>
<dds>
  <profiles xmlns="http://www.eprosima.com/XMLSchemas/fastRTPS_Profiles">
    <transport_descriptors>
      <transport_descriptor>
        <transport_id>UDPv4_transport</transport_id>
        <type>UDPv4</type>
        <interfaceWhiteList>
          <address>127.0.0.1</address>
          <address>10.42.0.100</address>
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
</dds>
```

The whitelist for network interfaces is configured with two IPs: 127.0.0.1 and 10.42.0.100, which are the local loopback IP and the IP for the remote control network interface, respectively. If you need to receive and send the corresponding ROS2 Topics on a third-party PC or an added industrial control computer, you need to add the IP of the local network interface (generally, you can choose **192.168.2.50**, which is the fixed IP for the debugging network port on the back of the robot, or the reserved IP for the added computing board **192.168.100.100**) to the whitelist (both **privileged** and non-privileged need to be added). After adding, restart the robot and connect via a wired connection to the corresponding network port to perform the communication.

> Using asymmetric dds whitelists in ROS2 Humble can sometimes lead to unpredictable communication issues. Please ensure that the dds whitelist configurations are consistent.
>
> Reference: [https://github.com/eProsima/Fast-DDS/pull/3733](https://github.com/eProsima/Fast-DDS/pull/3733)

### 5. Basic Constraints for Secondary Development <a href="#web-05-5-basic-constraints-for-secondary-development" id="web-05-5-basic-constraints-for-secondary-development"></a>

There are some basic constraints to follow when performing secondary development on the A2 Lite. Violating these constraints may cause damage to the robot's hardware, software, and system. Repairs due to violations of the following agreements are not covered by the warranty:

1. Do not deploy secondary development programs on the x86 industrial PC. The motion control program runs on the x86 system, and deploying programs on the x86 industrial PC may lead to CPU and memory resource competition, which can even cause the robot to crash in severe cases.
2. Do not modify the x86 industrial PC system configuration at will, such as file system mounting, system scheduling policies, default UDP/TCP buffer sizes, and other kernel-related configurations.
3. Do not modify the configuration of the onboard software modules at will, such as various configurations for motion control and other modules.
4. Do not modify the system software dependencies at will, and strictly prohibit the use of apt for installing and uninstalling software.
5. Do not frequently call RPC interfaces, as this can cause excessive load on the system, which may lead to a crash in severe cases. It is recommended to set the polling frequency for continuous status-type RPC interfaces to 0.2 Hz or lower, and the polling frequency for short-term status query interfaces to 1 Hz or lower.

### 6. Quick Start for Secondary Development <a href="#web-06-6-quick-start-for-secondary-development" id="web-06-6-quick-start-for-secondary-development"></a>

This chapter will demonstrate how to quickly run your first secondary development program through a few simple example programs, providing a basic understanding.

#### 6.1 Prerequisites <a href="#web-06-6-1-prerequisites" id="web-06-6-1-prerequisites"></a>

Secondary development programs are recommended to be deployed on a personal PC or an additional computing board. The system requirements are **Ubuntu 22.04 installed with ROS2 Humble and Fastdds**. Connect via Ethernet directly to the robot's debugging port (192.168.2.50) or the reserved to\_orin port (192.168.100.100). In this tutorial, we will use the example of a personal PC connected via Ethernet to the debugging port (192.168.2.50). If the network port is different, simply modify the IP address accordingly.

**6.1.1 Wired Connection to Debugging Port**

First, **set the IP address of the PC's wired network port to a static IP of 192.168.2.150**, then connect one end of the Ethernet cable to the PC's wired network port and the other end to the robot's right debugging port at the back.

After the robot is powered on, you should be able to ping 192.168.2.50 from your personal PC.

bash

```
ping 192.168.2.50
```

**6.1.2 Adding DDS Configuration Whitelist**

First, SSH into the robot, back up the relevant configuration files, and then modify them.

bash

```
ssh agi@192.168.2.50
```

bash

```
cd /agibot/software/v0/entry/bin/cfg/
cp ros_dds_configuration.xml ros_dds_configuration.xml.original
cp privileged_ros_dds_configuration.xml privileged_ros_dds_configuration.xml.original
```

Then use vim to modify the above two configuration files.

bash

```
vim ros_dds_configuration.xml
vim privileged_ros_dds_configuration.xml
```

Here is only the modified segment (the same for both files):

yaml

```
        <interfaceWhiteList>
          <address>127.0.0.1</address>
          <address>10.42.0.100</address>
          <address>192.168.2.50</address>
        </interfaceWhiteList>
```

After modifying, restart the robot. Once the robot has completed initialization, execute the following command on your personal PC. You should be able to see many topics and echo the corresponding topics successfully.

bash

```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
ros2 topic list --no-daemon
ros2 topic echo /motion/control/arm_joint_state
```

#### 6.2 Example of Running a Battery Level Retrieval Program <a href="#web-06-6-2-example-of-running-a-battery-level-retrieval-program" id="web-06-6-2-example-of-running-a-battery-level-retrieval-program"></a>

This example uses an HTTP request to get the robot's BMS status, relying only on the wired connection described in Section 5.1.1. Additionally, if the robot and PC are connected to the same local network, you can access the service using the robot's IP address in the local network.

Run the following script directly on your personal PC:

bash

```
curl -i     -H 'content-type:application/json' \
            -H 'timeout: 1000'   -X POST 'http://192.168.2.50:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState' \
            -d '{}'
```

The returned result should be as follows (the specific field meanings are explained in detail in the subsequent interface section):

text

```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Content-Type: application/json
Content-Length: 709

{"data":{"ver":{"hardware_major":49,"hardware_minor":48,"hardware_revision":49,"software_major":53,"software_minor":48,"software_revision":49},"voltage":54200,"current":28,"power":0,"temperature":285,"capacity":14090,"charge":100,"power_supply_health":"PowerSupplyHealth_GOOD","power_supply_status":"PowerSupplyStatus_IDEL","cycles_num":100,"cycles_capacity":10,"abnormal_state":"PowerAbnormalStatus_OVERVOLTAGE","charger_state":"ChargerConnected","bms_state":"BatteryStatus_Connected","max_current":29568,"battery_firmware_type":"BatteryFirmwareType_OLD","battery_key_state":"BatteryKeyStatus_SHORT_CURCUIT","battery_pack_state":"BatteryPackStatus_NORMAL","battery_comm_state":"BatteryCommunication_NORMAL"}}
```

#### 6.3 Example of Retrieving Robot Upper Limb Joint Status <a href="#web-06-6-3-example-of-retrieving-robot-upper-limb-joint-status" id="web-06-6-3-example-of-retrieving-robot-upper-limb-joint-status"></a>

This example uses a ROS2 program to subscribe to the corresponding topic on the robot, relying on all the prerequisites in Section 5.1. It is not recommended to use a local wireless network to obtain ROS2 topics and other data (due to high and uncontrollable latency, and potential interference issues with multiple robots, which significantly reduces security).

Save the following code on your PC as `joint_state.py`.

python

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
    # Arm Joint Status: /motion/control/arm_joint_state
    # Neck Joint Status: /motion/control/neck_joint_state
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

Then execute the following command:

bash

```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
python3 joint_state.py
```

#### 6.4 Example of Controlling Head Shaking Interface <a href="#web-06-6-4-example-of-controlling-head-shaking-interface" id="web-06-6-4-example-of-controlling-head-shaking-interface"></a>

We provide both HTTP and ROS2 interfaces for head control.

**6.4.1 Head Shaking HTTP Example**

Using the HTTP interface for control is relatively simple. Here is the script:

python

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
        "http://192.168.2.50:56322/rpc/aimdk.protocol.McMotionService/SetNeckCommand"
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

Note that `idx28_head_joint2` is invalid but must be retained. The Lite model robot has only one degree of freedom for head shaking, where `velocity` and `effort` are invalid, and only `position` will take effect.

**6.4.2 Head Shaking ROS2 Example**

Using the ROS2 interface to call the head shaking program requires some prerequisites:

1. First, switch the state machine of the motion control module to the RL\_LOCOMOTION\_ARM\_EXT\_JOINT\_SERVO state. This can be done on AimMaster, and the detailed interface explanation will also cover how to switch using program interfaces.
2.  Call the following command to release the control of the upper body joints by the action playback module.bash

    ```
    curl -i \
        -H 'content-type:application/json' \
        -H 'timeout: 1000' \
        -X POST http://192.168.2.50:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer \
        -d '{}'
    ```

Next, save the following script as `neck.py`:

python

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
        # The second value is unused but still needs to be provided.
        msg.name = ["idx27_head_joint1", "idx28_head_joint2"]
        msg.position = [0.5, 0.5]

        # The following fields have no actual effect but must be set; otherwise, they may cause the motion controller to crash
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

Then run:

yaml

```
source /opt/ros/humble/setup.bash
export ROS_DOMAIN_ID=232
export ROS_LOCALHOST_ONLY=0
python3 neck.py
```

### 7. Detailed Interface Documentation <a href="#web-07-7-detailed-interface-documentation" id="web-07-7-detailed-interface-documentation"></a>

To reduce redundancy and increase information density, the following conventions are used in the interface documentation:

1. The header fields in the request and response messages of HTTP JSON RPC are not explained in detail. Some headers are omitted in the example messages, and they can also be left unfilled in actual requests. Refer to the actual runnable examples for guidance.
2. The IP in the HTTP JSON RPC URLs is filled as 127.0.0.1. When actually accessing, it needs to be changed to the IP of the accessible x86 industrial PC.
3. All request methods in HTTP JSON RPC are POST and will not be listed separately in the following interface documentation.
4. In ROS2 Topics, if the message type is an input parameter, the secondary development program publishes the topic, and the onboard program subscribes to it. If it is an output parameter, the opposite is true.
5. Unexplained parameters are generally invalid. Fill in the default values as shown in the examples without modification.
6. For unspecified units, angles are in radians (rad) by default, and lengths are in meters (m) by default.

### 7.1 Motion Control Section <a href="#web-08-7-1-motion-control-section" id="web-08-7-1-motion-control-section"></a>

**7.1.1 Overview**

The A2 Lite robot comes pre-installed with a motion control program, allowing users to directly control the robot's movement by sending high-level linear and angular velocity commands. There is no need to develop low-level control models for walking and other functions. Additionally, the joints for the upper limbs and neck are open to direct HAL layer hardware interfaces.

> By default, the low-level control interface for the lower limb joint motors is not open; only high-level speed commands can be used for overall control. If you need to develop your own motion control algorithms to replace the Agibot factory-installed algorithms, please contact the business or customer project manager to obtain the motion control development and deployment guide.

The Agibot motion control program is designed with a state machine that switches between different models and opens different upper limb control interfaces based on the current state. The state machine is shown in the following diagram:

<figure><img src="../../.gitbook/assets/unknown (144).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

Descriptions of each state are as follows:

| **Action Type**         | **Action Code**                        | **Chinese Name**                              | **Detailed Description**                                                                                                                                                                                                                | **Callable Interfaces** |
| ----------------------- | -------------------------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- |
| Safety Action           | DEFAULT                                | Default Mode                                  | The default action after the motion control starts.                                                                                                                                                                                     |                         |
| Position Control Action | RL\_JOINT\_DEFAULT                     | Reinforced Standing Mode                      | The robot stands with reinforced position control, standing with straight legs.                                                                                                                                                         |                         |
| Position Control Action | PASSIVE\_UPPER\_BODY\_JOINT\_SERVO     | Lower Limb Passive, Upper Limb Servo Mode     | The lower limbs are not enabled, and the arms can receive external joint servo commands.                                                                                                                                                | T2                      |
| Position Control Action | SIT\_DOWN                              | Sitting Mode                                  | The lower limbs perform the action, while the upper limbs remain stationary, coordinating with a chair to sit down.                                                                                                                     |                         |
| Position Control Action | STAND\_UP                              | Standing Up Mode                              | The lower limbs perform the action, while the upper limbs remain stationary, coordinating with a chair to stand up.                                                                                                                     |                         |
| Force Control Action    | RL\_LOCOMOTION\_DEFAULT                | Reinforced Walking Mode                       | A human-like walking mode trained through reinforcement learning, where the arms swing during walking.                                                                                                                                  | T1                      |
| Force Control Action    | RL\_LOCOMOTION\_ARM\_EXT\_JOINT\_SERVO | Reinforced Walking with Upper Limb Servo Mode | The lower limbs walk or stand in a human-like manner, while the upper limbs accept external joint servo commands, performing actions during walking or standing (using a full-body control reinforcement model for better stability).   | T1, T2                  |
| Force Control Action    | RL\_WHOLE\_BODY\_EXT\_JOINT\_SERVO     | Full-Body Action with Upper Limb Servo Mode   | Similar to RL\_LOCOMOTION\_ARM\_EXT\_JOINT\_SERVO, but with additional control over waist movements. The A2 robot does not have actual degrees of freedom in the waist, so waist movements are achieved through leg motor coordination. | T1, T2, T3              |
| Force Control Action    | RL\_WHOLE\_BODY\_DANCE                 | Full-Body Dance Mode                          | Can perform specified full-body dance actions.                                                                                                                                                                                          | S1                      |

> It is generally not recommended to switch between non-force control states using the program. Only switching between force control states is recommended. Other state transitions, which involve lifting and lowering the robot, should be performed manually.### 7.1.2 State Machine Switching and Query RPC Interface

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McActionService/SetAction</code></td></tr><tr><td>Function Overview</td><td>Switch the motion control state machine</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McActionService/SetAction</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "timestamp": {
      "seconds": 1762800293,
      "nanos": 849579000,
      "ms_since_epoch": 1762800293849
    },
    "control_source": "ControlSource_SAFE"
  },
  "command": {
    "action": "McAction_USE_EXT_CMD",
    "ext_action": "RL_JOINT_DEFAULT"
  }
}
</code></pre><ul><li>action: Fixed to McAction_USE_EXT_CMD</li><li>ext_action: The actual motion control action to switch to</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "called successfully.",
    "timestamp": {
      "seconds": "1762829093",
      "nanos": 853246996,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: The status of the request call</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/SetAction.py</td></tr><tr><td>Notes</td><td><ul><li>Asynchronous interface, completion of the call does not mean the switch is complete; use the GetAction interface to check if the switch is complete</li><li>This interface has no action restrictions</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McActionService/GetAction</code></td></tr><tr><td>Function Overview</td><td>Query the motion control state machine</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McActionService/GetAction</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "called successfully.",
    "timestamp": {
      "seconds": "1762828518",
      "nanos": 763620392,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "info": {
    "current_action": "McAction_DEFAULT",
    "ext_action": "",
    "status": "McActionStatus_RUNNING"
  }
}
</code></pre><ul><li>current_action: The currently running action</li><li>ext_action: Extended action, generally not used</li><li>status: Action status, generally not used</li></ul></td></tr><tr><td>Example Script</td><td>example/mc/actions.py</td></tr><tr><td>Notes</td><td><ul><li>This interface has no action restrictions</li></ul></td></tr></tbody></table>

Generally, the above two interfaces are used together, as shown in the following code example:

python

```
def ensure_action(action_name: str, retries=3, retry_interval=1.0, mc_ip: str = "127.0.0.1"):
    try:
        for i in range(retries):
            if get_action(mc_ip) == action_name:
                return True
            set_action(action_name, mc_ip)
            time.sleep(0.1 if i == 0 else retry_interval)
    except Exception as e:
        print(f"Failed to set action: {e}")
        return False
    return False
```

**7.1.3 Locomotion Control Command Topic Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>/motion/control/locomotion_velocity</code></td></tr><tr><td>Function Overview</td><td>Locomotion control command</td></tr><tr><td>Interface Type</td><td>ROS2 Topic</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "mode": 0,
    "forward_velocity": 0.1,
    "lateral_velocity": 0.0,
    "angular_velocity": 0.0
  }
}
</code></pre><ul><li><p>mode: Velocity control mode</p><ul><li>0 for remote control scenarios</li><li>1 for navigation mode, with faster velocity response; 0.05 m/s activates stepping, and stepping stops after 500 ms without a velocity command</li></ul></li><li>forward_velocity: Forward velocity, range -0.3-0.8 m/s</li><li>lateral_velocity: Lateral velocity, range -0.25-0.25 m/s</li><li>angular_velocity: Angular velocity, range -0.5-0.5 rad/s</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/walk.py</td></tr><tr><td>Notes</td><td><ul><li>The ROS2 message type is ros2_plugin_proto/msg/RosMsgWrapper, which requires sourcing prebuilt/ros2_plugin_proto_x86_64/share/ros2_plugin_proto/local_setup.bash before use.</li><li>The call code for this interface is <strong>T1</strong>, and commands work better under RL_LOCOMOTION_DEFAULT</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>/motion/control/move_waist</code></td></tr><tr><td>Function Overview</td><td>Waist control instruction</td></tr><tr><td>Interface Type</td><td>ROS2 Topic</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "x": 0.0,
    "y": 0.0,
    "z": -0.1,
    "roll": 0.0,
    "pitch": 0.0,
    "yaw": 0.0
  }
}
</code></pre><ul><li>x: Invalid field</li><li>y: Invalid field</li><li>z: Squat, range -0.25 to 0.00 m</li><li>roll: Invalid field</li><li><p>pitch: Bend forward, range 0 to 0.5236 rad, note the coupling relationship with z squat</p><ul><li>As z increases, the maximum bend (pitch maximum value) linearly increases from 0 to 0.5236, then remains at the maximum value of 0.5236, and finally linearly decreases to 0.436</li><li>The three segments of z ranges are [0, -0.08], [-0.08, -0.17], [-0.17, -0.25]</li><li>The minimum pitch value is 0, it can only lean forward, not backward</li></ul></li><li>yaw: Turn, range -0.5236 to 0.5236 rad</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/move_waist.py</td></tr><tr><td>Notes</td><td><ul><li>The ROS2 type of this message is ros2_plugin_proto/msg/RosMsgWrapper, which requires sourcing prebuilt/ros2_plugin_proto_x86_64/share/ros2_plugin_proto/local_setup.bash before use</li><li>The call code for this interface is <strong>T3</strong>, and it can only be called in RL_WHOLE_BODY_EXT_JOINT_SERVO mode</li><li>The A2 robot does not have an independent waist degree of freedom in its physical design; this waist degree of freedom is a virtual one, simulated by reinforcement learning algorithms through leg joint motors</li></ul></td></tr></tbody></table>

**7.1.5 Neck Control Instruction and State Topic Interfaces**

| Interface Name    | `/motion/control/neck_joint_command`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Overview | Neck control instruction                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Interface Type    | ROS2 Topic                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Input Parameters  | <p><a href="https://docs.ros.org/en/humble/p/sensor_msgs/msg/JointState.html">sensor_msgs::msg::JointState</a></p><ul><li>name: Joint name, fixed as ["idx27_head_joint1", "idx28_head_joint2"], the second one is invalid but needs to be filled</li><li>position: Joint angle, the first value represents the head shaking degree of freedom, range -0.785 to 0.785 rad, the second value is invalid but needs to be filled</li><li>velocity: Invalid field, leave blank</li><li>effort: Invalid field, leave blank</li></ul> |
| Example Script    | examples/motion\_control/neck.py                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Notes             | <ul><li>The call code for this interface is <strong>T2</strong>, and it can only be called in modes with JOINT_SERVO suffix</li><li>Note that in JOINT_SERVO mode, this interface is taken over by the motion_player module by default. Please disable it using examples/motion_player/disable_motion_player before sending instructions</li></ul>                                                                                                                                                                              |

| Interface Name    | `/motion/control/neck_joint_state`                                                                                                                                                                                               |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Overview | Neck state topic                                                                                                                                                                                                                 |
| Interface Type    | ROS2 Topic                                                                                                                                                                                                                       |
| Output Parameters | <p><a href="https://docs.ros.org/en/humble/p/sensor_msgs/msg/JointState.html">sensor_msgs::msg::JointState</a></p><ul><li>position: Joint angle, the first value represents head shaking, other values are meaningless</li></ul> |
| Example Script    | examples/motion\_control/joint\_state.py                                                                                                                                                                                         |
| Notes             | <ul><li>This interface has no Action restrictions</li></ul>                                                                                                                                                                      |

The above neck control topic interface is suitable for scenarios requiring continuous and precise control of the neck angle, such as remote operation, and can only be called in JOINT\_SERVO mode. For certain scenarios where simple control to a specific angle is needed, the following RPC interface can be used.

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/SetNeckCommand</code></td></tr><tr><td>Function Overview</td><td>Set neck command</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/SetNeckCommand</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "shake": {
      "name": "idx27_head_joint1",
      "position": 0.5,
      "velocity": 0.0,
      "effort": 0.0
    },
    "nod": {
      "name": "idx28_head_joint2",
      "position": 0.0,
      "velocity": 0.0,
      "effort": 0.0
    }
  }
}
</code></pre><ul><li>Only the position field in the shake section is meaningful; the other fields should remain unchanged. The range is -0.785 to 0.785 rad.</li><li>The nod-related content is not meaningful and should be filled out as is.</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "called successfully.",
    "timestamp": {
      "seconds": "1762845079",
      "nanos": 921954699,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/SetNeckCommand.py</td></tr><tr><td>Notes</td><td><ul><li>This interface has no Action restrictions.</li><li>Note that in JOINT_SERVO mode, this interface is taken over by the motion_player module by default. Please disable it using examples/motion_player/disable_motion_player before sending commands.</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/GetNeckState</code></td></tr><tr><td>Function Overview</td><td>Get neck state</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetNeckState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "called successfully.",
    "timestamp": {
      "seconds": "1762846182",
      "nanos": 679221245,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "data": {
    "shake": {
      "name": "",
      "sequence": 0,
      "position": 0,
      "velocity": 0,
      "effort": 0
    },
    "nod": {
      "name": "",
      "sequence": 0,
      "position": 0,
      "velocity": 0,
      "effort": 0
    }
  }
}
</code></pre><ul><li>state: Call request status</li><li>Only the position field in the shake section is meaningful, with a range of -0.785 to 0.785 rad. The other fields can be ignored.</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetNeckState.py</td></tr><tr><td>Notes</td><td>This interface has no Action restrictions.</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>/motion/control/arm_joint_command</code></td></tr><tr><td>Function Overview</td><td>Arm joint control command</td></tr><tr><td>Interface Type</td><td>ROS2 Topic</td></tr><tr><td>Input Parameters</td><td><p><a href="https://docs.ros.org/en/humble/p/sensor_msgs/msg/JointState.html">sensor_msgs::msg::JointState</a></p><ul><li>name: Joint names, fixed to ["idx13_left_arm_joint1", "idx14_left_arm_joint2", "idx15_left_arm_joint3", "idx16_left_arm_joint4", "idx17_left_arm_joint5", "idx18_left_arm_joint6", "idx19_left_arm_joint7", "idx20_right_arm_joint1", "idx21_right_arm_joint2", "idx22_right_arm_joint3", "idx23_right_arm_joint4", "idx24_right_arm_joint5", "idx25_right_arm_joint6", "idx26_right_arm_joint7"], joints 6 and 7 of both arms are invalid but need to be filled as placeholders</li><li>position: Joint angles, must fill in the angle values for 14 joints, where joints 6 and 7 of both arms are invalid but need to be filled as placeholders</li><li>velocity: Invalid field, set to 0.0</li><li>effort: Invalid field, set to 0.0</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/arm.py</td></tr><tr><td>Notes</td><td><ul><li>The call code for this interface is <strong>T2</strong>, and it can only be called in modes with the suffix JOINT_SERVO</li><li><p>Note that in JOINT_SERVO mode, this interface is taken over by the motion_player module by default. Please disable it using examples/motion_player/disable_motion_player before sending commands.</p><ul><li>This interface is recommended to be called at a frequency of 100 Hz. When calling, ensure that the interval between adjacent commands does not exceed 0.03, ensuring that the <strong>speed does not exceed 3 rad/s and the maximum acceleration does not exceed 6.28 rad/s^2</strong>. The commands should be as smooth as possible; otherwise, there may be jitter. It is recommended to use at least a basic low-pass filter method: y(k) = (1 - a) * y(k - 1) + a * x(k).</li></ul></li><li><p>Angle limits are as follows (in radians)</p><ul><li>idx13_left_arm_joint1: -2.91 ~ 2.91</li><li>idx14_left_arm_joint2: -0.46 ~ 1.60</li><li>idx15_left_arm_joint3: -2.91 ~ 2.91</li><li>idx16_left_arm_joint4: -2.00 ~ -0.03</li><li>idx17_left_arm_joint5: -2.94 ~ 2.94</li><li>idx20_right_arm_joint1: -2.91 ~ 2.91</li><li>idx21_right_arm_joint2: -1.60 ~ 0.46</li><li>idx22_right_arm_joint3: -2.91 ~ 2.94</li><li>idx23_right_arm_joint4: 0.03 ~ 2.00</li><li>idx24_right_arm_joint5: -2.94 ~ 2.94</li><li><p><strong>7.1.10 Full-Body Dance Playback RPC Interface</strong></p><h3 id="web-09-7-2-action-playback-section">7.2 Action Playback Section</h3><p><strong>7.2.1 Overview</strong></p><p>The A2 Lite provides basic preset action playback capabilities, with some preset actions pre-installed on the machine (additional actions can be recorded using remote operation devices to meet more personalized needs; for more information, please refer to the relevant documentation on remote operation). The list of default preset actions is as follows:</p><p>text</p><pre><code>wave-both-hands/wave-both-hands
wave-right-hand/wave-right-hand
right-hand-handshake/right-hand-handshake
right-hand-handshake_long/right-hand-handshake_long
look-right/1758103570432482028
look-left/1758103588180395683
wave-left-hand/wave-left-hand
left-hand-handshake/left-hand-handshake
left-hand-handshake_long/left-hand-handshake_long
posed-photo_strongman-pose/posed-photo_strongman-pose
salute/salute
look-around/1758103607745291736
look-at-both-hands/1758104272873252746
look-at-right-hand/1758104294863353043
look-at-right-arm/1758103484383524451
look-at-left-hand/175810431583786588
look-at-left-arm/1758103505321711264
</code></pre><p>The above action files are located in the x86 directory <code>/agibot/data/resources/default/motion/motion_player/default</code>. Custom recorded actions should be placed in the <code>/agibot/data/resources/default/motion/motion_player/custom</code> directory. The above list is obtained by specifying the following command in the corresponding directory:</p><p>bash</p><pre><code>find . -name "*.db" -type f | sed 's|^\./\([^/]*\)/\(.*\)\.db|\1/\2|' | sort
</code></pre><p>The specific action effects can be viewed using the motion control simulation provided in subsequent chapters or directly on the real machine.</p><p>Onboard action playback is handled by the <code>motion_player</code> module, which controls the arm and neck joints in JOINT_SERVO mode. The basic control principle involves reading and parsing the specified action file, playing the action file at 100 Hz, and sending <code>/motion/control/arm_joint_command</code> and <code>/motion/control/neck_joint_command</code> to the motion control module, which then performs the corresponding actions.</p><p><strong>7.2.2 Action Playback RPC Interface</strong></p><p><strong>7.2.3 Action Playback Status Query RPC Interface</strong></p><p><strong>7.2.4 Disable and Enable Action Playback Module RPC Interface</strong></p><p>The action playback module continuously sends /motion/control/arm_joint_command and /motion/control/neck_joint_command control instructions to the motion control module in JOINT_SERVO mode. If a secondary program also sends instructions, it can cause conflicts. You can use the following interfaces to disable and enable the action playback module.</p><p><strong>7.2.5 Disable and Enable Neck Control for Action Playback RPC Interface</strong></p><p>In some cases, it is necessary to disable the neck's action playback function separately, thereby transferring control of the neck to a secondary program for head tracking, etc. You can use the following interfaces to disable and enable neck control for action playback.</p><h3 id="web-10-7-3-audio-playback-section">7.3 Audio Playback Section</h3><p><strong>7.3.1 Overview</strong></p><p>The A2 Lite robot does not have a microphone and thus cannot perform voice interaction functions. However, it is equipped with a speaker that can play basic audio files and adjust volume. It also supports queue playback, playback status queries, and interruption control logic.</p><p><strong>7.3.2 Audio File Playback RPC Interface</strong></p><p><strong>7.3.3 Audio File Playback Status Query RPC Interface</strong></p><p><strong>7.3.4 Audio File Playback Interruption RPC Interface</strong></p><p>We provide interfaces for interrupting a single file playback and clearing the entire playback queue.</p><p><strong>7.3.5 Volume Get and Set RPC Interfaces</strong></p><h3 id="fault-diagnosis">7.4 Fault Diagnosis Section</h3><p><strong>7.4.1 Overview</strong></p><p>The robot itself provides basic fault diagnosis and health monitoring capabilities, capable of monitoring some basic anomalies and faults, such as joint overheating, sensor failure, system occupancy consistently too high, low battery power, etc.</p><p>There are two basic concepts in fault diagnosis: Alert and Exception. An Alert is a cluster of Exceptions. An Alert represents a broad category of faults, while an Exception is a specific fault. For example, repositioning failure is an Alert, which corresponds to many different failure reasons, each being a specific Exception. AimMaster generally displays Alerts, as Exceptions can be numerous and less intuitive. If you need to continuously monitor the robot's abnormal state, it is recommended to query the current alert list at regular intervals (not too frequently, a frequency of 0.2 Hz or lower is recommended).</p><p>The full list of alerts can be found in the file <code>/agibot/software/v0/config/hds_master/database/alert_info.yaml</code> on the x86 machine.</p><p><strong>7.4.2 Get Current Alert List RPC Interface</strong></p><p><strong>7.4.3 Attempt to Clear Alert RPC Interface</strong></p><h3 id="web-12-7-5-system-status-section">7.5 System Status Section</h3><p><strong>7.5.1 Overview</strong></p><p>System status refers to the state of the software system, which can be referenced in the previous section <em>Software System Overview</em>.</p><p><strong>7.5.2 System Status Retrieval RPC Interface</strong></p><p><strong>7.5.3 BMS Status Retrieval RPC Interface</strong></p><p><strong>7.5.4 Emergency Stop Status Retrieval RPC Interface</strong></p><p>When an emergency stop is triggered, an alert will also be issued, and the emergency stop status can be obtained through the GetAlertList. This section provides a separate interface to query the emergency stop status.</p><p><strong>7.5.5 Software Version Retrieval RPC Interface</strong></p><h3 id="web-13-8-guide-to-motion-control-simulation">8. Guide to Motion Control Simulation</h3><h4 id="web-13-8-1-simulation-description">8.1 Simulation Description</h4><p>We provide a mujoco-based simulation system for the A2 robot, designed to serve as a testing ground for basic calls to the A2 robot's motion control and action playback interfaces. This serves as a basic validation before actual operation, reducing the risk of damaging the robot while facilitating the debugging of secondary development program logic.</p><div><figure><img src="../../.gitbook/assets/unknown (145).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure></div><p>The system runs the mujoco_sim, motion_control, and motion_player components. mujoco_sim acts as the underlying simulation engine, simulating the robot's physical body and hal_ethercat. motion_control interacts with mujoco_sim to exchange control commands and status, thereby controlling the simulated robot. motion_player, on the other hand, calls the high-level interfaces provided by motion_control to play actions. The motion_control and motion_player components are identical to those on the real robot, allowing the system to call all interfaces of the motion control and action playback modules.</p><h4 id="web-13-8-2-prerequisites">8.2 Prerequisites</h4><p>This simulation system is provided as a container image, containing executable files for each component, action resource files, and calling scripts. To use this simulation system, the following conditions must be met:</p><ol><li>An x86_64 architecture Linux system with Docker installed.</li><li><p>An X11 desktop system.</p><ul><li>You can check this by running <code>echo $XDG_SESSION_TYPE</code>, and the expected output should be <code>x11</code>.</li></ul></li></ol><h4 id="web-13-8-3-usage-tutorial">8.3 Usage Tutorial</h4><p><strong>8.3.1 Pulling the Image</strong></p><ol><li>Log in to the read-only account of the image repository</li></ol><p>bash</p><pre><code>docker login tongyong-public-cn-shanghai.cr.volces.com -u crrobot@aima-public-reader -p Aima123456
</code></pre><ol start="2"><li>Pull the corresponding image</li></ol><p>bash</p><pre><code>docker pull tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
</code></pre><p><strong>8.3.2 Starting the Image</strong></p><ol><li><p>Allow Docker to access the display, which is used to configure the access control list for the X Window System. Running <code>xhost +</code> will allow all hosts to connect to the current user's X server, effectively disabling access control for the X server and allowing any user to access and operate it.bash</p><pre><code>xhost +
</code></pre></li><li><p>Start the Docker containerbash</p><pre><code>docker run -it \
--name=a2-lite-sim \
--privileged \
--net=host \
--ipc=host \
--pid=host \
-e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v /run/dbus/system_bus_socket:/run/dbus/system_bus_socket:ro \
-d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
</code></pre><p><br>If you find that the simulation interface runs sluggishly on a machine with an NVIDIA graphics card after starting the container with the above command, try using the following command to start the container:bash</p><pre><code>docker run -it \
        --name=a2-lite-sim \
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
        -d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
</code></pre></li><li><p>Enter the containerbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash
</code></pre></li></ol><p><strong>8.3.3 Starting the Simulation, Motion Control, and Action Playback Modules</strong></p><ol><li><p>After entering the image, run the following command to start the simulationbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash

cd /home/agi/a2_simulation/mujoco_sim/bin
./start_a2_lite.sh
</code></pre></li><li><p>In a new window, connect to the container and start the motion control programbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash

cd /home/agi/a2_simulation/motion_control_lite_2.0.10/scripts/motion_control
./start_motion_control.sh
</code></pre></li><li><p>In another new window, connect to the container and start the action playback programbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash

cd /home/agi/a2_simulation/motion_player_lite_2.0.10/scripts/motion_player
./start_motion_player.sh
</code></pre></li></ol><p><strong>8.3.4 Controlling Robot Walking</strong></p><p>Here, we will use robot walking as an example to explain the basic logic of calling a motion control interface. For other interfaces, refer to the motion control interface documentation and example scripts.</p><ol><li><p>Open a new window, enter the container, and switch the motion control Action to the joint standing mode (RL_JOINT_DEFAULT)bash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_control
./SetAction.py # Select the number corresponding to RL_JOINT_DEFAULT
</code></pre></li><li><p>Click the Load-Key button in the mujoco_sim interface to stabilize the robot<br></p><div><figure><img src="../../.gitbook/assets/unknown (146).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure></div></li><li><p>Continue to switch the motion control Action to the enhanced walking mode (RL_LOCOMOTION_DEFAULT)bash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_control
./SetAction.py # Select the number corresponding to RL_LOCOMOTION_DEFAULT
</code></pre></li><li><p>Call the walking example scriptbash</p><pre><code>source /home/agi/a2_simulation/prebuilt/ros2_plugin_proto_x86_64/share/ros2_plugin_proto/local_setup.bash
./walk.py
</code></pre></li></ol><p><strong>8.3.5 Controlling Robot to Perform Actions</strong></p><ol><li><p>Switch the motion control state to the enhanced walking upper limb servo mode (RL_LOCOMOTION_ARM_EXT_JOINT_SERVO)bash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_control
./SetAction.py # Select the number corresponding to RL_LOCOMOTION_ARM_EXT_JOINT_SERVO
</code></pre></li><li><p>Call the SendMotionCommand interface to perform the actionbash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_player
./send_motion_id.sh /agibot/data/resources/default/motion/motion_player/default/wave-both-hands/wave-both-hands
</code></pre></li></ol><h3 id="troubleshooting-interface-calls">9. Troubleshooting Interface Call Issues</h3><h4 id="web-14-9-1-troubleshooting-approach">9.1 Troubleshooting Approach</h4><p>The general troubleshooting methods for HTTP JSON RPC and ROS2 Topic are different, but there are also some common troubleshooting methods for on-board issues.</p><p><strong>9.1.1 HTTP JSON RPC</strong></p><ol><li>Check if the corresponding IP is the correct x86 industrial PC IP and if it can be pinged.</li><li>Check if the HTTP URL is correct; you can refer to the example scripts or interface documentation.</li><li>Check if the corresponding service is started on the port. After SSHing into the x86, you can use the command <code>lsof -i:xxxx</code> in the terminal to check if the service is running on the port.</li><li>If you get a "Connection Refused" error, it means the IP might not be reachable or the service on the port has not started.</li><li>If you get an "HTTP deserialize failed" error, it means the JSON body fields might be incorrectly filled. You can refer to the example scripts or interface documentation for comparison.</li></ol><p><strong>9.1.2 ROS2 Topic</strong></p><ol><li>Check if the on-board ROS2 DDS configuration includes the IP of the network card being used. Ensure that both privileged and non-privileged configurations correctly add the network card IP. After adding, a full reboot is required.</li><li>Check if you are using the ROS2 Humble with Fastdds version.</li><li>Check if the local environment variables <code>ROS_DOMAIN_ID=232</code> and <code>ROS_LOCALHOST_ONLY=0</code> are loaded. The exported environment variables only take effect in the current terminal. A new terminal will need to re-export these variables. You can use the command <code>env | grep ROS</code> to view the relevant environment variable settings in the current terminal.</li><li><p>Ensure that the QoS of the topic is consistent with the default QoS on the board.yaml</p><pre><code>  history: keep_last
  depth: 10
  reliability: best_effort
</code></pre></li><li>After SSHing into the x86 industrial PC, execute <code>aima em load-env</code> (to load the ROS2 environment variables) and then use the <code>ros2 topic</code> command to check if the related topics are being sent or received by any modules.</li></ol><p><strong>9.1.3 Common Troubleshooting Methods</strong></p><ol><li>Use AimMaster to check if the robot has any health alerts. In the case of a robot fault, it may affect some interface calls. For example, if there is a joint fault, the motion control interface may not function properly.</li><li>If not connected to AimMaster, you can log in to the robot's x86 industrial PC and execute the <code>aima doctor</code> command to quickly view health alert information.</li></ol><h4 id="web-14-9-2-common-interface-questions">9.2 Common Interface Questions</h4><ol><li><p>Why does calling the upper limb action interface or neck interface result in no response or severe shaking?</p><ol><li>First, confirm that the robot is in the corresponding Action mode, which should end with JOINT_SERVO.</li><li>In the JOINT_SERVO mode, the control of the upper limbs and neck is preempted by the motion playback module. You need to call the DisableMotionPlayer interface to disable the control of the motion playback module before you can normally call the upper limb or neck control interfaces.</li></ol><p>yaml</p><pre><code>curl -i \
    -H 'content-type:application/json' \
    -H 'timeout: 1000' \
    -X POST http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer \
    -d '{}'
</code></pre></li><li><p>Why does calling any motion playback only result in the right hand lifting action?</p><ol><li>This is the default action of the motion playback module. When the <code>motion_id</code> parameter is incorrect, it will default to this action.</li><li><p>A correct motion path should find the corresponding .db file and pass the complete path without the .db suffix, for example:bash</p><pre><code>/agibot/data/resources/default/motion/motion_player/default/wave-both-hands/wave-both-hands
</code></pre></li></ol></li></ol><h4 id="web-14-9-3-feedback-channels">9.3 Feedback Channels</h4><p>If you encounter bugs in secondary development interfaces, you can provide feedback through the following channels:</p><p><a href="https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k">https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k</a></p><p>Note</p><ol><li>This channel is only for answering questions or reporting bugs related to secondary development interfaces. For robot body faults or after-sales maintenance, please contact the delivery, operation, and after-sales teams directly. Unrelated issues will not be responded to.</li><li>Please describe the problem in detail in the form, preferably providing reproducible steps. Clear and detailed problem descriptions will be given priority, while vague and general descriptions will have lower priority and may be ignored.</li><li>Please fill out all information carefully. Inconsistent or casually filled forms will be ignored.</li><li>Each ticket should focus on a single or similar issue. Do not mix multiple issues in one ticket, as this will significantly delay the processing time.</li></ol><h4 id="web-15-title-2-frequently-asked-questions-hideh1-true">title: 2. Frequently Asked Questions hideH1: true</h4><h3 id="frequently-asked-questions">2. Frequently Asked Questions</h3><h4 id="web-15-2-1-what-is-the-onboard-software-version">2.1 What is the onboard software version?</h4><p>The A2 robot comes with a series of onboard software, which will be upgraded along with the OTA (Over-The-Air) updates.</p><p>Generally, the software version (current application version) is printed when you ssh into the robot, and it can also be viewed through the AimMaster software. The version number is usually in the format of 1.2.x.</p><h4 id="web-15-2-2-what-are-p1-and-t3">2.2 What are P1 and T3?</h4><p>P1 and T3 are the hardware models of the A2 robot. The main difference between these hardware models lies in the configuration of the industrial PC, including network card configurations, but the system performance and upper-layer interfaces are generally unified.</p><p>After logging into the x86 industrial PC via ssh, you can check the /etc/bsp_version file to confirm the version. If this file exists, it is P1; if it does not exist, it is T3.</p><h4 id="web-15-2-3-how-to-handle-the-over-speed-anomaly-reported-by-the-arm-joint-motor">2.3 How to handle the over-speed anomaly reported by the arm joint motor?</h4><div><figure><img src="../../.gitbook/assets/unknown (147).webp" alt="2.3 How to handle the over-speed anomaly reported by the arm joint motor?"><figcaption><p>2.3 How to handle the over-speed anomaly reported by the arm joint motor?</p></figcaption></figure></div><p>Reason: When calling the arm interface, there is a step change between the input position and the current position, leading to an over-speed condition that triggers current limiting. At this point, the embedded system will disable the joint for protection and report the alarm.</p><p>Solution: In most cases, restarting the robot will resolve the issue. To avoid this problem, when calling the arm ROS2 Topic interface, filter and smooth the joint positions before passing them in, ensuring that the input values do not have a large step change compared to the current state.</p><h4 id="web-15-2-4-is-it-possible-to-develop-your-own-motion-control-program">2.4 Is it possible to develop your own motion control program?</h4><p>By default, the low-level control interfaces for the lower limb joint motors are not open, and they can only be controlled through high-level speed commands. If you need to develop your own motion control algorithms to replace the ones provided by Agibot, please contact the sales or project manager to obtain the motion control development and deployment guide.</p></li></ul></li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.OTAService/GetRobotOtaInfo</code></td></tr><tr><td>Function Summary</td><td>Retrieve software version information</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:57900/rpc/aimdk.protocol.OTAService/GetRobotOtaInfo</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "robot_info": {
    "model": "A2_T3D1_LITE"
  },
  "current_apk_info": {
    "apk_version": "A2_LITE-v1.2.4-0-g17e2f79fe-2510271122",
    "pub_time": "",
    "soc_info": [],
    "mcu_info": [],
    "contents": "",
    "fota_version": ""
  },
  "support_rollback_apk_infos": []
}
</code></pre><ul><li>apk_version: Software version information</li></ul><p>Other fields are not of concern.</p></td></tr><tr><td>Example Script</td><td>examples/status/get_version_info.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalEmergencyService/GetEmergencyState</code></td></tr><tr><td>Function Summary</td><td>Retrieve emergency stop status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56421/rpc/aimdk.protocol.HalEmergencyService/GetEmergencyState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "active": true,
    "reason": "Reason_WIRELESS_ESTOP",
    "left_front_sensor_alarm": false,
    "right_front_sensor_alarm": false,
    "left_sensor_alarm": false,
    "right_sensor_alarm": false,
    "left_back_sensor_alarm": false,
    "right_back_sensor_alarm": false,
    "lift_upper_limit_alarm": false,
    "lift_lower_limit_alarm": false,
    "tray_limit_alarm": false,
    "front_left_tof_alarm": false,
    "front_right_tof_alarm": false,
    "right_front_tof_alarm": false,
    "right_back_tof_alarm": false,
    "back_tof_alarm": false,
    "left_back_tof_alarm": false,
    "left_front_tof_alarm": false,
    "wired_emergency_stop": false,
    "wireless_emergency_stop": true,
    "software_emergency_stop": false
  }
}
</code></pre><ul><li>active: Whether the emergency stop is triggered</li><li>reason: Reason for the emergency stop</li><li>wireless_emergency_stop: Whether the wireless emergency stop is triggered</li><li>software_emergency_stop: Whether the software emergency stop is triggered</li></ul><p>Other fields are not of concern.</p></td></tr><tr><td>Example Script</td><td>examples/status/get_estop_status.sh</td></tr><tr><td>Notes</td><td><ul><li>The soft emergency stop interface is not yet open for secondary development, and cannot be triggered via the interface.</li><li>If an empty JSON body is returned, it indicates that all parameters are at their default values, meaning the emergency stop has not been triggered.</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalBmsService/GetBmsState</code></td></tr><tr><td>Function Summary</td><td>Retrieve system status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "ver": {
      "hardware_major": 49,
      "hardware_minor": 48,
      "hardware_revision": 49,
      "software_major": 55,
      "software_minor": 48,
      "software_revision": 49
    },
    "voltage": 45460,
    "current": -1156,
    "power": 52551,
    "temperature": 289,
    "capacity": 4220,
    "charge": 29,
    "power_supply_health": "PowerSupplyHealth_GOOD",
    "power_supply_status": "PowerSupplyStatus_IDEL",
    "cycles_num": 1,
    "cycles_capacity": 21,
    "abnormal_state": "PowerAbnormalStatus_NORMAL",
    "charger_state": "ChargerNotPulgin",
    "bms_state": "BatteryStatus_Connected",
    "max_current": 0,
    "battery_firmware_type": "BatteryFirmwareType_OLD",
    "battery_key_state": "BatteryKeyStatus_SHORT_CURCUIT",
    "battery_pack_state": "BatteryPackStatus_NORMAL",
    "battery_comm_state": "BatteryCommunication_NORMAL"
  }
}
</code></pre><ul><li>ver: Version information</li><li>voltage: Current voltage, unit mV</li><li>current: Current current, unit mA</li><li>power: Current power, unit mW</li><li>temperature: Current temperature, unit 0.1 degrees Celsius</li><li>capacity: Current capacity, unit: mAh</li><li>charge: Current charge percentage</li><li>power_supply_health: Not currently available</li><li><p>power_supply_status: Charging status</p><ul><li>PowerSupplyStatus_IDEL</li><li>PowerSupplyStatus_CHARGING</li><li>PowerSupplyStatus_FULL</li></ul></li><li>cycles_num: Number of cycles</li><li>cycles_capacity: Cycle capacity (total charge and discharge capacity of the current battery pack), unit: Ah</li><li><p>abnormal_state: Abnormal status</p><ul><li>PowerAbnormalStatus_NORMAL</li><li>PowerAbnormalStatus_SHORT_CIRCUIT</li><li>PowerAbnormalStatus_DISCHARGE_OVERCURRENT</li><li>PowerAbnormalStatus_CHARGING_OVERCURRENT</li><li>PowerAbnormalStatus_UNDERVOLTAGE</li><li>PowerAbnormalStatus_OVERVOLTAGE</li><li>PowerAbnormalStatus_EXCEED_DISCHARGE_TEMP_LIMIT</li><li>PowerAbnormalStatus_EXCEED_CHARGING_TEMP_LIMIT</li></ul></li><li><p>charger_state: Whether the charger is plugged in</p><ul><li>ChargerNotPulgin</li><li>ChargerConnected</li></ul></li><li><p>bms_state: Whether the battery is connected</p><ul><li>BatteryStatus_NotPulgin</li><li>BatteryStatus_Connected</li></ul></li><li>max_current: Maximum current</li><li><p>battery_firmware_type: Battery pack firmware version</p><ul><li>BatteryFirmwareType_OLD</li><li>BatteryFirmwareType_NEW</li></ul></li><li><p>battery_key_state: Battery pack key status</p><ul><li>BatteryKeyStatus_SHORT_CURCUIT</li><li>BatteryKeyStatus_CONNECTED</li></ul></li><li><p>battery_pack_state: Battery pack abnormal status</p><ul><li>BatteryPackStatus_NORMAL</li><li>BatteryPackStatus_ABNORMAL</li></ul></li><li><p>battery_comm_state: Battery pack communication status</p><ul><li>BatteryCommunication_NORMAL</li><li>BatteryCommunication_ABNORMAL</li></ul></li></ul></td></tr><tr><td>Example Script</td><td>examples/status/get_bms_status.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.SystemService/GetSystemState</code></td></tr><tr><td>Function Summary</td><td>Retrieve system status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:51011/rpc/aimdk.protocol.SystemService/GetSystemState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "trace_id": "",
    "domin": ""
  },
  "cur_state": "EStop",
  "cur_status": "SystemStatus_IN_READY"
}
</code></pre><ul><li><p>cur_state: Current system state</p><ul><li>Startup: Starting up state</li><li>Ready: Startup completed state</li><li>Manual: Manual operation state</li><li>MotionStream: Remote operation state</li><li>OTA: Remote upgrade state</li><li>Estop: Emergency stop state</li><li>Poweroff: Power off state</li><li>Reboot: Rebooting state</li><li>Reset: Resetting state</li><li>Safe: Safe state</li></ul></li><li><p>cur_status: Current system condition</p><ul><li>SystemStatus_IN_INITIAL: Initializing</li><li>SystemStatus_IN_READY: Transition completed</li><li>SystemStatus_IN_MOVE: Transitioning</li><li>SystemStatus_IN_ROLLBACK: Rolling back</li><li>SystemStatus_IN_RECOVERY: Recovering</li></ul></li></ul></td></tr><tr><td>Example Script</td><td>examples/status/get_system_status.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HDSService/ClearAlert</code></td></tr><tr><td>Function Summary</td><td>Attempt to clear an alert, requiring the alert ID to be passed in</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:50587/rpc/aimdk.protocol.HDSService/ClearAlert</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "id": "c92f2fdd-cea5-4209-b02f-d0eb62ae18ce"
}
</code></pre><ul><li>id: You need to fill in the specific alert ID, which can be obtained through the GetAlertList interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "1",
    "msg": "clear alert failed!",
    "trace_id": "",
    "domin": ""
  },
  "data": {
    "data": "c92f2fdd-cea5-4209-b02f-d0eb62ae18ce"
  }
}
</code></pre><ul><li>data: The alert ID passed in</li><li>The header returns information about whether the current clearing was successful, a code of 0 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/hds/clear_alert.sh</td></tr><tr><td>Notes</td><td><ul><li>Although the emergency stop alert has manual_clear set to true, it will still fail to clear. The emergency stop must be manually released before it can be cleared.</li><li>In general, do not call this interface to clear alerts. Please fully understand the meaning of the alert before considering using this interface to clear it.</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HDSService/GetAlertList</code></td></tr><tr><td>Function Summary</td><td>Get the current alert list</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:50587/rpc/aimdk.protocol.HDSService/GetAlertList</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "alerts": [
      {
        "id": "c39f6ccc-85d9-4976-a2e9-08f2906cc237",
        "appeared_timestamp": "1762933137153",
        "disappeared_timestamp": "0",
        "alert_code": "A2000003",
        "state": "AlertState_ACTIVE",
        "exception_list": [
          {
            "type": "ExceptionType_Normal",
            "module_id": 81,
            "code": 100,
            "info": "Emergency stop pressed",
            "module_name": "Health Management HDS"
          }
        ],
        "description": "Emergency stop pressed",
        "level": "AlertLevel_HIDDEN_DANGERS",
        "manual_clear": true,
        "show_type": "AlertShowType_Normal",
        "solution_list": [
          {
            "type": "txt",
            "content": "Please rotate the emergency stop button counterclockwise to release the emergency stop state."
          }
        ]
      }
    ]
  }
}
</code></pre><ul><li>id: The ID of this alert</li><li>appeared_timestamp: The timestamp when the alert appeared</li><li>disappeared_timestamp: The timestamp when the alert disappeared</li><li>alert_code: The alert code</li><li><p>state: The alert state</p><ul><li>AlertState_UNDEFINED: Unknown</li><li>AlertState_ACTIVE: In alert</li><li>AlertState_CLEARED: Cleared</li><li>AlertState_ExceptionChanged: Alert with changed exception</li><li>AlertState_Recovering: Recovering</li></ul></li><li>exception_list: The list of exceptions</li><li><p>exception_list[i].type: The type of exception</p><ul><li>ExceptionType_Normal: Normal type, this type of exception needs to be reported periodically</li><li>ExceptionType_Trigger_Appear: Triggered exception (reported once when the exception occurs), set this exception to the occurrence state</li><li>ExceptionType_Trigger_Disappear: Triggered exception (reported once when the exception disappears), set this exception to the disappearance state</li></ul></li><li>exception_list[i].module_id: The ID of the module where the exception occurred</li><li>exception_list[i].code: The module exception code</li><li>exception_list[i].info: The exception information</li><li>exception_list[i].module_name: The name of the module</li><li>description: The alert description</li><li><p>level: The alert level</p><ul><li>AlertLevel_UNDEFINED: No alert</li><li>AlertLevel_FATAL: Fatal alert</li><li>AlertLevel_SERIOUS: Serious alert</li><li>AlertLevel_WARNING: Warning alert</li><li>AlertLevel_HIDDEN_DANGERS: The current system has potential hazards</li><li>AlertLevel_STATUS: The current system has status-related alerts</li></ul></li><li>manual_clear: Whether manual clearing is supported</li><li><p>show_type: The type of alert display</p><ul><li>AlertShowType_Normal</li><li>AlertShowType_Toast</li></ul></li><li>solution_list: The list of solutions</li><li>solution_list[i].type: The type of solution</li><li>solution_list[i].content: The content of the solution</li></ul></td></tr><tr><td>Example Script</td><td>examples/hds/get_alert_list.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalAudioService/SetAudioVolume</code></td></tr><tr><td>Function Summary</td><td>Adjust the volume</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.HalAudioService/SetAudioVolume</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "audio_volume": 70,
  "is_mute": false
}
</code></pre><ul><li>audio_volume: Volume level, a value between 0-100. <strong>Note: Do not set the volume above 70, as exceeding this range will cause the speaker to exceed its rated operating capacity, leading to damage</strong></li><li>is_mute: Whether muted</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "SetAudioVolume successfully",
    "trace_id": "",
    "domin": ""
  },
  "pkg_name": "",
  "is_success": false
}
</code></pre><ul><li>pkg_name: Invalid field, no need to pay attention</li><li>is_success: Invalid field, no need to pay attention</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/set_audio_volume.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalAudioService/GetAudioVolume</code></td></tr><tr><td>Function Summary</td><td>Get the current volume level</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.HalAudioService/GetAudioVolume</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "GetAudioVolume successfully",
    "trace_id": "",
    "domin": ""
  },
  "audio_volume": 80,
  "is_mute": false
}
</code></pre><ul><li>audio_volume: Volume level, a value between 0-100</li><li>is_mute: Whether muted</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/get_audio_volume.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/StopTTS</code></td></tr><tr><td>Function Summary</td><td>Terminate all audio file playback, including the current playback task and all tasks in the queue</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/StopTTS</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_UNKNOWN"
}
</code></pre><ul><li>state: Request status, no need to pay attention to the specific value, HTTP request returning 200 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/stop_all.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/StopTTSTraceId</code></td></tr><tr><td>Function Summary</td><td>Interrupt a single file playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/StopTTSTraceId</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "trace_id": "hafhjkqwjwefk"
}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_UNKNOWN"
}
</code></pre><ul><li>state: Request status, no need to pay attention to the specific value, HTTP request returning 200 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/stop_trace_id.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/GetAudioStatus</code></td></tr><tr><td>Function Summary</td><td>Audio file playback status query</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/GetAudioStatus</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "trace_id": "hafhjkqwjwefk"
}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "tts_status": {
    "text": "",
    "priority": 0,
    "trace_id": "",
    "tts_status": "TTSStatusType_Playing",
    "domain": "",
    "error_message": ""
  }
}
</code></pre><ul><li><p>tts_status: Playback status, enumeration values</p><ul><li>TTSConfigStatusType_Unknown: Unknown status</li><li>TTSStatusType_Begin: Start playback, brief, usually not queried</li><li>TTSStatusType_Playing: Playing</li><li>TTSStatusType_End: End of playback, brief, usually not queried</li><li>TTSStatusType_Stop: Pause playback/cancel playback/interrupt playback</li><li>TTSStatusType_Error: Playback failed</li><li>TTSStatusType_InQue: In the playback queue, not yet started</li><li>TTSStatusType_NOTInQue: No such text in the playback queue, not playing, enters this state after playback ends</li></ul></li><li>The rest of the fields are invalid and do not need to be paid attention to</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/get_audio_status.sh</td></tr><tr><td>Notes</td><td>A successful playback queried through this RPC interface generally returns InQue, Playing, and NOTInQue states</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/PlayMediaFile</code></td></tr><tr><td>Function Summary</td><td>Audio file playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/PlayMediaFile</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "file_name": "wake.pcm",
  "priority_level": "INTERACTION_L6",
  "domain": "example",
  "trace_id": "hafhjkqwjwefk",
  "is_interrupted": true
}
</code></pre><ul><li>file_name: File name (stored in <code>/agibot/data/var/interaction/audio/</code>, for example, wake.pcm. The file should be a 24kHz, 16-bit, mono PCM file. A separate folder needs to be created, and the input should be in the format of folder name/file name, such as file/wake.pcm)</li><li>priority_level: Priority level, keep INTERACTION_L6</li><li>domain: Caller source identifier, you can pass in a custom client string for easier troubleshooting, etc.</li><li>trace_id: Playback ID, if you need to get the playback status, you need to pass this field and use its value as the parameter to query the playback status</li><li>is_interrupted: Whether to interrupt playback of the same priority, please default to true. For queue playback requirements, you can use false</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "text": "wake.pcm",
  "priority_level": "INTERACTION_L6",
  "priority_weight": 0,
  "domain": "example",
  "trace_id": "hafhjkqwjwefk",
  "is_sucess": true,
  "error_message": "",
  "estimated_duration": 0
}
</code></pre><ul><li>text: File name</li><li>priority_level: Priority level, no need to pay attention</li><li>pritority_weight: Priority weight, no need to pay attention</li><li>domain: Caller source identifier, returns the custom string passed in the request for easier troubleshooting</li><li>trace_id: Playback ID, returns the custom string passed in the request for easier troubleshooting</li><li>is_success: Whether the priority check was successful, generally true, but it does not mean it will play. For example, passing an incorrect or non-existent file name will still return true. Only when there is a higher-priority content being played, such as a fault alarm, will it return true</li><li>estimated_duration: Invalid field, no need to pay attention, unable to estimate playback duration</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/play_media_file.sh</td></tr><tr><td>Notes</td><td><ul><li>Supports standard 44-byte header Linear PCM wav files. Other header formats and compressed formats are not supported. It is recommended to use 24kHz, 16-bit, mono PCM files</li><li>If an incorrect or non-existent file name is passed, it will silently fail without playing, and is_success will return true</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/EnableNeckMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Enable the action playback module to control the neck, start continuously sending neck control instructions to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/EnableNeckMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/enable_neck_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/DisableNeckMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Disable the action playback module from controlling the neck motor, the process will not exit, and no neck instructions will be sent to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableNeckMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/disable_neck_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/EnableMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Enable the action playback module, start continuously sending instructions to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/EnableMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/enable_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/DisableMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Disable the action playback module, the process will not exit, and no instructions will be sent to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/disable_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/</code>GetMotionStatus</td></tr><tr><td>Function Summary</td><td>Get the action playback status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/GetMotionStatus</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762852836",
      "nanos": 502608623,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "time_to_end_ms": "235",
  "status": "MotionCommandStatus_OPERATING",
  "is_neck_enable": true,
  "motion_id": "1Wave Hello"
}
</code></pre><ul><li>time_to_end_ms: Time remaining until the end of the action, in milliseconds</li><li><p>status: Action playback status</p><ul><li>MotionCommandStatus_IDLE: No action, idle</li><li>MotionCommandStatus_START: Action starts playing</li><li>MotionCommandStatus_OPERATING: Action is playing</li><li>MotionCommandStatus_PAUSE: State when calling the action playback interface with cmd_pause=true</li><li>MotionCommandStatus_STOP: State after calling DisableMotionPlayer</li></ul></li><li>is_neck_enable: Whether the neck is controlled by the motion_player</li><li>motion_id: Action name</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/get_motion_status.sh</td></tr><tr><td>Notes</td><td>This interface call code is <strong>T2</strong>, and can only be called under the JOINT_SERVO suffix motion control Action</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/SendMotionCommand</code></td></tr><tr><td>Function Summary</td><td>Play the specified action file</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/SendMotionCommand</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "motion_id": "/agibot/data/resources/default/motion/motion_player/default/Wave Both Hands/Wave Both Hands",
  "duration_ms": 10000,
  "cmd_end": true,
  "cmd_pause": false,
  "cmd_reset": false
}
</code></pre><ul><li><p>motion_id: Absolute path of the action file, up to the last .db file, without the .db suffix, for example:</p><ul><li>/agibot/data/resources/default/motion/motion_player/default/Wave Both Hands/Wave Both Hands</li></ul></li><li>duration_ms: An invalid field, leave it as is</li><li>cmd_end: Whether to automatically return to the initial posture after the action is executed, <code>true</code> indicates automatic reset, <code>false</code> indicates no automatic reset</li><li>cmd_pause: Action pause flag, <code>true</code> indicates pause, which will stop sending control signals to the robot, generally not used</li><li>cmd_reset: Reset flag, <code>true</code> indicates reset, <code>false</code> indicates no reset. The reset operation will reset the current action state to the initial state</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762851946",
      "nanos": 693223585,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/send_motion_id.sh</td></tr><tr><td>Notes</td><td>This interface call code is <strong>T2</strong>, and can only be called under the JOINT_SERVO suffix motion control Action</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/SelectDanceType</code></td></tr><tr><td>Function Overview</td><td>Full-body dance playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/SelectDanceType</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "timestamp": {
      "seconds": 1762818960,
      "nanos": 172949000,
      "ms_since_epoch": 1762818960172
    },
    "control_source": "ControlSource_SAFE"
  },
  "dance_name": "jiangnan"
}
</code></pre><ul><li>dance_name: Dance name, which needs to be obtained from the above dance list retrieval interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762847760",
      "nanos": 178468357,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/SelectDanceType.py</td></tr><tr><td>Notes</td><td><ul><li>The call code for this interface is <strong>S1</strong>, and it can only be called in RL_WHOLE_BODY_DANCE mode</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/GetDanceTypeList</code></td></tr><tr><td>Function Overview</td><td>Retrieve the list of supported full-body dances</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetDanceTypeList</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "dance_name": [
    "Swing Dance",
    "Victory Dance"
  ],
  "dance_model_path": [
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/policy_ybw_1127.onnx",
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/policy_vict_1203.onnx"
  ],
  "dance_data_path": [
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/export_data_ybw.npy",
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/export_data_vict_v6.npy"
  ],
  "dance_time": [
    93.64,
    75.56
  ]
}
</code></pre><ul><li>dance_name: Dance name, used for input to the play interface</li><li>dance_model_path: Location of the dance model file, no need to pay attention</li><li>dance_data_path: Location of the dance data file, no need to pay attention</li><li>dance_time: Duration of the dance in seconds</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetDanceTypeList.py</td></tr><tr><td>Notes</td><td><ul><li>This interface has no call restrictions</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McDataService/GetJointState</code></td></tr><tr><td>Function Overview</td><td>Retrieve the state of upper and lower limb joints</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetJointState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "states": [
    {
      "name": "idx01_left_hip_roll",
      "sequence": 0,
      "position": 0.006256103515625,
      "velocity": 0.0048847198486328125,
      "effort": -13.367523193359375
    },
    {
      "name": "idx02_left_hip_yaw",
      "sequence": 0,
      "position": 0.013275146484375,
      "velocity": 0.024419784545898438,
      "effort": -11.658126831054688
    },
    {
      "name": "idx03_left_hip_pitch",
      "sequence": 0,
      "position": -0.11947822570800781,
      "velocity": -0.0048847198486328125,
      "effort": 1.015869140625
    },
    {
      "name": "idx04_left_tarsus",
      "sequence": 0,
      "position": 0.28732776641845703,
      "velocity": -0.0048847198486328125,
      "effort": -10.862030029296875
    },
    {
      "name": "idx05_left_toe_pitch",
      "sequence": 0,
      "position": -0.17624187469482422,
      "velocity": 0,
      "effort": 3.44881189007971
    },
    {
      "name": "idx06_left_toe_roll",
      "sequence": 0,
      "position": -0.012819436684095006,
      "velocity": 0.009888242426560891,
      "effort": 2.4995190811765715
    },
    {
      "name": "idx07_right_hip_roll",
      "sequence": 0,
      "position": -0.009918212890625,
      "velocity": -0.014652252197265625,
      "effort": 14.119659423828125
    },
    {
      "name": "idx08_right_hip_yaw",
      "sequence": 0,
      "position": -0.011749267578125,
      "velocity": 0.024419784545898438,
      "effort": 14.25640869140625
    },
    {
      "name": "idx09_right_hip_pitch",
      "sequence": 0,
      "position": -0.12344551086425781,
      "velocity": -0.0048847198486328125,
      "effort": -7.423675537109375
    },
    {
      "name": "idx10_right_tarsus",
      "sequence": 0,
      "position": 0.30014514923095703,
      "velocity": -0.014652252197265625,
      "effort": -18.676422119140625
    },
    {
      "name": "idx11_right_toe_pitch",
      "sequence": 0,
      "position": -0.18814373016357422,
      "velocity": -0.004883766174316406,
      "effort": 4.751964842417327
    },
    {
      "name": "idx12_right_toe_roll",
      "sequence": 0,
      "position": 0.012819560417340213,
      "velocity": 0.01981031932552883,
      "effort": -0.06747343675733508
    },
    {
      "name": "idx13_left_arm_joint1",
      "sequence": 0,
      "position": -0.053559280931949615,
      "velocity": -5.885322389076464e-05,
      "effort": -1.253999948501587
    },
    {
      "name": "idx14_left_arm_joint2",
      "sequence": 0,
      "position": 1.3100006580352783,
      "velocity": -6.644718814641237e-05,
      "effort": -2.2799999713897705
    },
    {
      "name": "idx15_left_arm_joint3",
      "sequence": 0,
      "position": 0,
      "velocity": 0,
      "effort": 2.2660000324249268
    },
    {
      "name": "idx16_left_arm_joint4",
      "sequence": 0,
      "position": -0.03490660712122917,
      "velocity": -4.366529537946917e-05,
      "effort": 1.715999960899353
    },
    {
      "name": "idx17_left_arm_joint5",
      "sequence": 0,
      "position": 1.5707954168319702,
      "velocity": 0,
      "effort": 0.06880000233650208
    },
    {
      "name": "idx18_left_arm_joint6",
      "sequence": 0,
      "position": 0.75,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx19_left_arm_joint7",
      "sequence": 0,
      "position": 2.995796503389102e-08,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx20_right_arm_joint1",
      "sequence": 0,
      "position": 0.03456582874059677,
```json
      "velocity": 6.644718723691767e-06,
      "effort": 0.722000002861023
    },
    {
      "name": "idx21_right_arm_joint2",
      "sequence": 0,
      "position": -1.3099987506866455,
      "velocity": 0,
      "effort": 1.7100000381469727
    },
    {
      "name": "idx22_right_arm_joint3",
      "sequence": 0,
      "position": -9.492455319559667e-07,
      "velocity": 7.40411487640813e-05,
      "effort": 1.5839999914169312
    },
    {
      "name": "idx23_right_arm_joint4",
      "sequence": 0,
      "position": 0.08476477861404419,
      "velocity": -5.1259259635116905e-05,
      "effort": 0.7919999957084656
    },
    {
      "name": "idx24_right_arm_joint5",
      "sequence": 0,
      "position": 1.5707954168319702,
      "velocity": 0,
      "effort": -0.5504000186920166
    },
    {
      "name": "idx25_right_arm_joint6",
      "sequence": 0,
      "position": -0.75,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx26_right_arm_joint7",
      "sequence": 0,
      "position": 3.001038685424783e-08,
      "velocity": 0,
      "effort": 0
    }
  ]
}
```
The 6th and 7th joints of both arms are invalid values
</code></pre></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetJointState.py</td></tr><tr><td>Notes</td><td>This interface has no Action restrictions</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>/motion/control/arm_joint_state</code></td></tr><tr><td>Function Overview</td><td>Arm joint state topic</td></tr><tr><td>Interface Type</td><td>ROS2 Topic</td></tr><tr><td>Output Parameters</td><td><p><a href="https://docs.ros.org/en/humble/p/sensor_msgs/msg/JointState.html">sensor_msgs::msg::JointState</a></p><ul><li>name: 14 joint names, where joints 6 and 7 of both arms are invalid</li><li>position: 14 joint angles, where joints 6 and 7 of both arms are invalid</li><li>velocity: 14 joint velocities, where joints 6 and 7 of both arms are invalid</li><li>effort: 14 joint torques, where joints 6 and 7 of both arms are invalid</li></ul></td></tr><tr><td><p></p><p></p><p><strong>7.1.10 Full-Body Dance Playback RPC Interface</strong></p><h3 id="web-09-7-2-action-playback-section">7.2 Action Playback Section</h3><p><strong>7.2.1 Overview</strong></p><p>The A2 Lite provides basic preset action playback capabilities, with some preset actions pre-installed on the machine (additional actions can be recorded using remote operation devices to meet more personalized needs; for more information, please refer to the relevant documentation on remote operation). The list of default preset actions is as follows:</p><p>text</p><pre><code>wave-both-hands/wave-both-hands
wave-right-hand/wave-right-hand
right-hand-handshake/right-hand-handshake
right-hand-handshake_long/right-hand-handshake_long
look-right/1758103570432482028
look-left/1758103588180395683
wave-left-hand/wave-left-hand
left-hand-handshake/left-hand-handshake
left-hand-handshake_long/left-hand-handshake_long
posed-photo_strongman-pose/posed-photo_strongman-pose
salute/salute
look-around/1758103607745291736
look-at-both-hands/1758104272873252746
look-at-right-hand/1758104294863353043
look-at-right-arm/1758103484383524451
look-at-left-hand/175810431583786588
look-at-left-arm/1758103505321711264
</code></pre><p>The above action files are located in the x86 directory <code>/agibot/data/resources/default/motion/motion_player/default</code>. Custom recorded actions should be placed in the <code>/agibot/data/resources/default/motion/motion_player/custom</code> directory. The above list is obtained by specifying the following command in the corresponding directory:</p><p>bash</p><pre><code>find . -name "*.db" -type f | sed 's|^\./\([^/]*\)/\(.*\)\.db|\1/\2|' | sort
</code></pre><p>The specific action effects can be viewed using the motion control simulation provided in subsequent chapters or directly on the real machine.</p><p>Onboard action playback is handled by the <code>motion_player</code> module, which controls the arm and neck joints in JOINT_SERVO mode. The basic control principle involves reading and parsing the specified action file, playing the action file at 100 Hz, and sending <code>/motion/control/arm_joint_command</code> and <code>/motion/control/neck_joint_command</code> to the motion control module, which then performs the corresponding actions.</p><p><strong>7.2.2 Action Playback RPC Interface</strong></p><p><strong>7.2.3 Action Playback Status Query RPC Interface</strong></p><p><strong>7.2.4 Disable and Enable Action Playback Module RPC Interface</strong></p><p>The action playback module continuously sends /motion/control/arm_joint_command and /motion/control/neck_joint_command control instructions to the motion control module in JOINT_SERVO mode. If a secondary program also sends instructions, it can cause conflicts. You can use the following interfaces to disable and enable the action playback module.</p><p><strong>7.2.5 Disable and Enable Neck Control for Action Playback RPC Interface</strong></p><p>In some cases, it is necessary to disable the neck's action playback function separately, thereby transferring control of the neck to a secondary program for head tracking, etc. You can use the following interfaces to disable and enable neck control for action playback.</p><h3 id="web-10-7-3-audio-playback-section">7.3 Audio Playback Section</h3><p><strong>7.3.1 Overview</strong></p><p>The A2 Lite robot does not have a microphone and thus cannot perform voice interaction functions. However, it is equipped with a speaker that can play basic audio files and adjust volume. It also supports queue playback, playback status queries, and interruption control logic.</p><p><strong>7.3.2 Audio File Playback RPC Interface</strong></p><p><strong>7.3.3 Audio File Playback Status Query RPC Interface</strong></p><p><strong>7.3.4 Audio File Playback Interruption RPC Interface</strong></p><p>We provide interfaces for interrupting a single file playback and clearing the entire playback queue.</p><p><strong>7.3.5 Volume Get and Set RPC Interfaces</strong></p><h3 id="fault-diagnosis">7.4 Fault Diagnosis Section</h3><p><strong>7.4.1 Overview</strong></p><p>The robot itself provides basic fault diagnosis and health monitoring capabilities, capable of monitoring some basic anomalies and faults, such as joint overheating, sensor failure, system occupancy consistently too high, low battery power, etc.</p><p>There are two basic concepts in fault diagnosis: Alert and Exception. An Alert is a cluster of Exceptions. An Alert represents a broad category of faults, while an Exception is a specific fault. For example, repositioning failure is an Alert, which corresponds to many different failure reasons, each being a specific Exception. AimMaster generally displays Alerts, as Exceptions can be numerous and less intuitive. If you need to continuously monitor the robot's abnormal state, it is recommended to query the current alert list at regular intervals (not too frequently, a frequency of 0.2 Hz or lower is recommended).</p><p>The full list of alerts can be found in the file <code>/agibot/software/v0/config/hds_master/database/alert_info.yaml</code> on the x86 machine.</p><p><strong>7.4.2 Get Current Alert List RPC Interface</strong></p><p><strong>7.4.3 Attempt to Clear Alert RPC Interface</strong></p><h3 id="web-12-7-5-system-status-section">7.5 System Status Section</h3><p><strong>7.5.1 Overview</strong></p><p>System status refers to the state of the software system, which can be referenced in the previous section <em>Software System Overview</em>.</p><p><strong>7.5.2 System Status Retrieval RPC Interface</strong></p><p><strong>7.5.3 BMS Status Retrieval RPC Interface</strong></p><p><strong>7.5.4 Emergency Stop Status Retrieval RPC Interface</strong></p><p>When an emergency stop is triggered, an alert will also be issued, and the emergency stop status can be obtained through the GetAlertList. This section provides a separate interface to query the emergency stop status.</p><p><strong>7.5.5 Software Version Retrieval RPC Interface</strong></p><h3 id="web-13-8-guide-to-motion-control-simulation">8. Guide to Motion Control Simulation</h3><h4 id="web-13-8-1-simulation-description">8.1 Simulation Description</h4><p>We provide a mujoco-based simulation system for the A2 robot, designed to serve as a testing ground for basic calls to the A2 robot's motion control and action playback interfaces. This serves as a basic validation before actual operation, reducing the risk of damaging the robot while facilitating the debugging of secondary development program logic.</p><p><img src="../../.gitbook/assets/unknown (375).webp" alt="Official AgiBot illustration" data-size="original"></p><p>The system runs the mujoco_sim, motion_control, and motion_player components. mujoco_sim acts as the underlying simulation engine, simulating the robot's physical body and hal_ethercat. motion_control interacts with mujoco_sim to exchange control commands and status, thereby controlling the simulated robot. motion_player, on the other hand, calls the high-level interfaces provided by motion_control to play actions. The motion_control and motion_player components are identical to those on the real robot, allowing the system to call all interfaces of the motion control and action playback modules.</p><h4 id="web-13-8-2-prerequisites">8.2 Prerequisites</h4><p>This simulation system is provided as a container image, containing executable files for each component, action resource files, and calling scripts. To use this simulation system, the following conditions must be met:</p><ol><li>An x86_64 architecture Linux system with Docker installed.</li><li><p>An X11 desktop system.</p><ul><li>You can check this by running <code>echo $XDG_SESSION_TYPE</code>, and the expected output should be <code>x11</code>.</li></ul></li></ol><h4 id="web-13-8-3-usage-tutorial">8.3 Usage Tutorial</h4><p><strong>8.3.1 Pulling the Image</strong></p><ol><li>Log in to the read-only account of the image repository</li></ol><p>bash</p><pre><code>docker login tongyong-public-cn-shanghai.cr.volces.com -u crrobot@aima-public-reader -p Aima123456
</code></pre><ol start="2"><li>Pull the corresponding image</li></ol><p>bash</p><pre><code>docker pull tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
</code></pre><p><strong>8.3.2 Starting the Image</strong></p><ol><li><p>Allow Docker to access the display, which is used to configure the access control list for the X Window System. Running <code>xhost +</code> will allow all hosts to connect to the current user's X server, effectively disabling access control for the X server and allowing any user to access and operate it.bash</p><pre><code>xhost +
</code></pre></li><li><p>Start the Docker containerbash</p><pre><code>docker run -it \
--name=a2-lite-sim \
--privileged \
--net=host \
--ipc=host \
--pid=host \
-e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v /run/dbus/system_bus_socket:/run/dbus/system_bus_socket:ro \
-d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
</code></pre><p><br>If you find that the simulation interface runs sluggishly on a machine with an NVIDIA graphics card after starting the container with the above command, try using the following command to start the container:bash</p><pre><code>docker run -it \
        --name=a2-lite-sim \
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
        -d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
</code></pre></li><li><p>Enter the containerbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash
</code></pre></li></ol><p><strong>8.3.3 Starting the Simulation, Motion Control, and Action Playback Modules</strong></p><ol><li><p>After entering the image, run the following command to start the simulationbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash

cd /home/agi/a2_simulation/mujoco_sim/bin
./start_a2_lite.sh
</code></pre></li><li><p>In a new window, connect to the container and start the motion control programbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash

cd /home/agi/a2_simulation/motion_control_lite_2.0.10/scripts/motion_control
./start_motion_control.sh
</code></pre></li><li><p>In another new window, connect to the container and start the action playback programbash</p><pre><code>docker start a2-lite-sim &#x26;&#x26; docker exec -it a2-lite-sim /bin/bash

cd /home/agi/a2_simulation/motion_player_lite_2.0.10/scripts/motion_player
./start_motion_player.sh
</code></pre></li></ol><p><strong>8.3.4 Controlling Robot Walking</strong></p><p>Here, we will use robot walking as an example to explain the basic logic of calling a motion control interface. For other interfaces, refer to the motion control interface documentation and example scripts.</p><ol><li><p>Open a new window, enter the container, and switch the motion control Action to the joint standing mode (RL_JOINT_DEFAULT)bash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_control
./SetAction.py # Select the number corresponding to RL_JOINT_DEFAULT
</code></pre></li><li><p>Click the Load-Key button in the mujoco_sim interface to stabilize the robot<br></p><div><figure><img src="../../.gitbook/assets/unknown (376).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure></div></li><li><p>Continue to switch the motion control Action to the enhanced walking mode (RL_LOCOMOTION_DEFAULT)bash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_control
./SetAction.py # Select the number corresponding to RL_LOCOMOTION_DEFAULT
</code></pre></li><li><p>Call the walking example scriptbash</p><pre><code>source /home/agi/a2_simulation/prebuilt/ros2_plugin_proto_x86_64/share/ros2_plugin_proto/local_setup.bash
./walk.py
</code></pre></li></ol><p><strong>8.3.5 Controlling Robot to Perform Actions</strong></p><ol><li><p>Switch the motion control state to the enhanced walking upper limb servo mode (RL_LOCOMOTION_ARM_EXT_JOINT_SERVO)bash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_control
./SetAction.py # Select the number corresponding to RL_LOCOMOTION_ARM_EXT_JOINT_SERVO
</code></pre></li><li><p>Call the SendMotionCommand interface to perform the actionbash</p><pre><code>cd /home/agi/a2_simulation/tools-lite/motion_player
./send_motion_id.sh /agibot/data/resources/default/motion/motion_player/default/wave-both-hands/wave-both-hands
</code></pre></li></ol><h3 id="troubleshooting-interface-calls">9. Troubleshooting Interface Call Issues</h3><h4 id="web-14-9-1-troubleshooting-approach">9.1 Troubleshooting Approach</h4><p>The general troubleshooting methods for HTTP JSON RPC and ROS2 Topic are different, but there are also some common troubleshooting methods for on-board issues.</p><p><strong>9.1.1 HTTP JSON RPC</strong></p><ol><li>Check if the corresponding IP is the correct x86 industrial PC IP and if it can be pinged.</li><li>Check if the HTTP URL is correct; you can refer to the example scripts or interface documentation.</li><li>Check if the corresponding service is started on the port. After SSHing into the x86, you can use the command <code>lsof -i:xxxx</code> in the terminal to check if the service is running on the port.</li><li>If you get a "Connection Refused" error, it means the IP might not be reachable or the service on the port has not started.</li><li>If you get an "HTTP deserialize failed" error, it means the JSON body fields might be incorrectly filled. You can refer to the example scripts or interface documentation for comparison.</li></ol><p><strong>9.1.2 ROS2 Topic</strong></p><ol><li>Check if the on-board ROS2 DDS configuration includes the IP of the network card being used. Ensure that both privileged and non-privileged configurations correctly add the network card IP. After adding, a full reboot is required.</li><li>Check if you are using the ROS2 Humble with Fastdds version.</li><li>Check if the local environment variables <code>ROS_DOMAIN_ID=232</code> and <code>ROS_LOCALHOST_ONLY=0</code> are loaded. The exported environment variables only take effect in the current terminal. A new terminal will need to re-export these variables. You can use the command <code>env | grep ROS</code> to view the relevant environment variable settings in the current terminal.</li><li><p>Ensure that the QoS of the topic is consistent with the default QoS on the board.yaml</p><pre><code>  history: keep_last
  depth: 10
  reliability: best_effort
</code></pre></li><li>After SSHing into the x86 industrial PC, execute <code>aima em load-env</code> (to load the ROS2 environment variables) and then use the <code>ros2 topic</code> command to check if the related topics are being sent or received by any modules.</li></ol><p><strong>9.1.3 Common Troubleshooting Methods</strong></p><ol><li>Use AimMaster to check if the robot has any health alerts. In the case of a robot fault, it may affect some interface calls. For example, if there is a joint fault, the motion control interface may not function properly.</li><li>If not connected to AimMaster, you can log in to the robot's x86 industrial PC and execute the <code>aima doctor</code> command to quickly view health alert information.</li></ol><h4 id="web-14-9-2-common-interface-questions">9.2 Common Interface Questions</h4><ol><li><p>Why does calling the upper limb action interface or neck interface result in no response or severe shaking?</p><ol><li>First, confirm that the robot is in the corresponding Action mode, which should end with JOINT_SERVO.</li><li>In the JOINT_SERVO mode, the control of the upper limbs and neck is preempted by the motion playback module. You need to call the DisableMotionPlayer interface to disable the control of the motion playback module before you can normally call the upper limb or neck control interfaces.</li></ol><p>yaml</p><pre><code>curl -i \
    -H 'content-type:application/json' \
    -H 'timeout: 1000' \
    -X POST http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer \
    -d '{}'
</code></pre></li><li><p>Why does calling any motion playback only result in the right hand lifting action?</p><ol><li>This is the default action of the motion playback module. When the <code>motion_id</code> parameter is incorrect, it will default to this action.</li><li><p>A correct motion path should find the corresponding .db file and pass the complete path without the .db suffix, for example:bash</p><pre><code>/agibot/data/resources/default/motion/motion_player/default/wave-both-hands/wave-both-hands
</code></pre></li></ol></li></ol><h4 id="web-14-9-3-feedback-channels">9.3 Feedback Channels</h4><p>If you encounter bugs in secondary development interfaces, you can provide feedback through the following channels:</p><p><a href="https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k">https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k</a></p><p>Note</p><ol><li>This channel is only for answering questions or reporting bugs related to secondary development interfaces. For robot body faults or after-sales maintenance, please contact the delivery, operation, and after-sales teams directly. Unrelated issues will not be responded to.</li><li>Please describe the problem in detail in the form, preferably providing reproducible steps. Clear and detailed problem descriptions will be given priority, while vague and general descriptions will have lower priority and may be ignored.</li><li>Please fill out all information carefully. Inconsistent or casually filled forms will be ignored.</li><li>Each ticket should focus on a single or similar issue. Do not mix multiple issues in one ticket, as this will significantly delay the processing time.</li></ol><hr><h4 id="web-15-title-2-frequently-asked-questions-hideh1-true">title: 2. Frequently Asked Questions hideH1: true</h4><h3 id="frequently-asked-questions">2. Frequently Asked Questions</h3><h4 id="web-15-2-1-what-is-the-onboard-software-version">2.1 What is the onboard software version?</h4><p>The A2 robot comes with a series of onboard software, which will be upgraded along with the OTA (Over-The-Air) updates.</p><p>Generally, the software version (current application version) is printed when you ssh into the robot, and it can also be viewed through the AimMaster software. The version number is usually in the format of 1.2.x.</p><h4 id="web-15-2-2-what-are-p1-and-t3">2.2 What are P1 and T3?</h4><p>P1 and T3 are the hardware models of the A2 robot. The main difference between these hardware models lies in the configuration of the industrial PC, including network card configurations, but the system performance and upper-layer interfaces are generally unified.</p><p>After logging into the x86 industrial PC via ssh, you can check the /etc/bsp_version file to confirm the version. If this file exists, it is P1; if it does not exist, it is T3.</p><h4 id="web-15-2-3-how-to-handle-the-over-speed-anomaly-reported-by-the-arm-joint-motor">2.3 How to handle the over-speed anomaly reported by the arm joint motor?</h4><p><img src="../../.gitbook/assets/unknown (377).webp" alt="2.3 How to handle the over-speed anomaly reported by the arm joint motor?" data-size="original"></p><p>Reason: When calling the arm interface, there is a step change between the input position and the current position, leading to an over-speed condition that triggers current limiting. At this point, the embedded system will disable the joint for protection and report the alarm.</p><p>Solution: In most cases, restarting the robot will resolve the issue. To avoid this problem, when calling the arm ROS2 Topic interface, filter and smooth the joint positions before passing them in, ensuring that the input values do not have a large step change compared to the current state.</p><h4 id="web-15-2-4-is-it-possible-to-develop-your-own-motion-control-program">2.4 Is it possible to develop your own motion control program?</h4><p>By default, the low-level control interfaces for the lower limb joint motors are not open, and they can only be controlled through high-level speed commands. If you need to develop your own motion control algorithms to replace the ones provided by Agibot, please contact the sales or project manager to obtain the motion control development and deployment guide.Example Script</p></td><td>examples/motion_control/joint_state.py</td></tr><tr><td>Notes</td><td>This interface has no Action restrictions</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.OTAService/GetRobotOtaInfo</code></td></tr><tr><td>Function Summary</td><td>Retrieve software version information</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:57900/rpc/aimdk.protocol.OTAService/GetRobotOtaInfo</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "robot_info": {
    "model": "A2_T3D1_LITE"
  },
  "current_apk_info": {
    "apk_version": "A2_LITE-v1.2.4-0-g17e2f79fe-2510271122",
    "pub_time": "",
    "soc_info": [],
    "mcu_info": [],
    "contents": "",
    "fota_version": ""
  },
  "support_rollback_apk_infos": []
}
</code></pre><ul><li>apk_version: Software version information</li></ul><p>Other fields are not of concern.</p></td></tr><tr><td>Example Script</td><td>examples/status/get_version_info.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalEmergencyService/GetEmergencyState</code></td></tr><tr><td>Function Summary</td><td>Retrieve emergency stop status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56421/rpc/aimdk.protocol.HalEmergencyService/GetEmergencyState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "active": true,
    "reason": "Reason_WIRELESS_ESTOP",
    "left_front_sensor_alarm": false,
    "right_front_sensor_alarm": false,
    "left_sensor_alarm": false,
    "right_sensor_alarm": false,
    "left_back_sensor_alarm": false,
    "right_back_sensor_alarm": false,
    "lift_upper_limit_alarm": false,
    "lift_lower_limit_alarm": false,
    "tray_limit_alarm": false,
    "front_left_tof_alarm": false,
    "front_right_tof_alarm": false,
    "right_front_tof_alarm": false,
    "right_back_tof_alarm": false,
    "back_tof_alarm": false,
    "left_back_tof_alarm": false,
    "left_front_tof_alarm": false,
    "wired_emergency_stop": false,
    "wireless_emergency_stop": true,
    "software_emergency_stop": false
  }
}
</code></pre><ul><li>active: Whether the emergency stop is triggered</li><li>reason: Reason for the emergency stop</li><li>wireless_emergency_stop: Whether the wireless emergency stop is triggered</li><li>software_emergency_stop: Whether the software emergency stop is triggered</li></ul><p>Other fields are not of concern.</p></td></tr><tr><td>Example Script</td><td>examples/status/get_estop_status.sh</td></tr><tr><td>Notes</td><td><ul><li>The soft emergency stop interface is not yet open for secondary development, and cannot be triggered via the interface.</li><li>If an empty JSON body is returned, it indicates that all parameters are at their default values, meaning the emergency stop has not been triggered.</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalBmsService/GetBmsState</code></td></tr><tr><td>Function Summary</td><td>Retrieve system status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "ver": {
      "hardware_major": 49,
      "hardware_minor": 48,
      "hardware_revision": 49,
      "software_major": 55,
      "software_minor": 48,
      "software_revision": 49
    },
    "voltage": 45460,
    "current": -1156,
    "power": 52551,
    "temperature": 289,
    "capacity": 4220,
    "charge": 29,
    "power_supply_health": "PowerSupplyHealth_GOOD",
    "power_supply_status": "PowerSupplyStatus_IDEL",
    "cycles_num": 1,
    "cycles_capacity": 21,
    "abnormal_state": "PowerAbnormalStatus_NORMAL",
    "charger_state": "ChargerNotPulgin",
    "bms_state": "BatteryStatus_Connected",
    "max_current": 0,
    "battery_firmware_type": "BatteryFirmwareType_OLD",
    "battery_key_state": "BatteryKeyStatus_SHORT_CURCUIT",
    "battery_pack_state": "BatteryPackStatus_NORMAL",
    "battery_comm_state": "BatteryCommunication_NORMAL"
  }
}
</code></pre><ul><li>ver: Version information</li><li>voltage: Current voltage, unit mV</li><li>current: Current current, unit mA</li><li>power: Current power, unit mW</li><li>temperature: Current temperature, unit 0.1 degrees Celsius</li><li>capacity: Current capacity, unit: mAh</li><li>charge: Current charge percentage</li><li>power_supply_health: Not currently available</li><li><p>power_supply_status: Charging status</p><ul><li>PowerSupplyStatus_IDEL</li><li>PowerSupplyStatus_CHARGING</li><li>PowerSupplyStatus_FULL</li></ul></li><li>cycles_num: Number of cycles</li><li>cycles_capacity: Cycle capacity (total charge and discharge capacity of the current battery pack), unit: Ah</li><li><p>abnormal_state: Abnormal status</p><ul><li>PowerAbnormalStatus_NORMAL</li><li>PowerAbnormalStatus_SHORT_CIRCUIT</li><li>PowerAbnormalStatus_DISCHARGE_OVERCURRENT</li><li>PowerAbnormalStatus_CHARGING_OVERCURRENT</li><li>PowerAbnormalStatus_UNDERVOLTAGE</li><li>PowerAbnormalStatus_OVERVOLTAGE</li><li>PowerAbnormalStatus_EXCEED_DISCHARGE_TEMP_LIMIT</li><li>PowerAbnormalStatus_EXCEED_CHARGING_TEMP_LIMIT</li></ul></li><li><p>charger_state: Whether the charger is plugged in</p><ul><li>ChargerNotPulgin</li><li>ChargerConnected</li></ul></li><li><p>bms_state: Whether the battery is connected</p><ul><li>BatteryStatus_NotPulgin</li><li>BatteryStatus_Connected</li></ul></li><li>max_current: Maximum current</li><li><p>battery_firmware_type: Battery pack firmware version</p><ul><li>BatteryFirmwareType_OLD</li><li>BatteryFirmwareType_NEW</li></ul></li><li><p>battery_key_state: Battery pack key status</p><ul><li>BatteryKeyStatus_SHORT_CURCUIT</li><li>BatteryKeyStatus_CONNECTED</li></ul></li><li><p>battery_pack_state: Battery pack abnormal status</p><ul><li>BatteryPackStatus_NORMAL</li><li>BatteryPackStatus_ABNORMAL</li></ul></li><li><p>battery_comm_state: Battery pack communication status</p><ul><li>BatteryCommunication_NORMAL</li><li>BatteryCommunication_ABNORMAL</li></ul></li></ul></td></tr><tr><td>Example Script</td><td>examples/status/get_bms_status.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.SystemService/GetSystemState</code></td></tr><tr><td>Function Summary</td><td>Retrieve system status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:51011/rpc/aimdk.protocol.SystemService/GetSystemState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "trace_id": "",
    "domin": ""
  },
  "cur_state": "EStop",
  "cur_status": "SystemStatus_IN_READY"
}
</code></pre><ul><li><p>cur_state: Current system state</p><ul><li>Startup: Starting up state</li><li>Ready: Startup completed state</li><li>Manual: Manual operation state</li><li>MotionStream: Remote operation state</li><li>OTA: Remote upgrade state</li><li>Estop: Emergency stop state</li><li>Poweroff: Power off state</li><li>Reboot: Rebooting state</li><li>Reset: Resetting state</li><li>Safe: Safe state</li></ul></li><li><p>cur_status: Current system condition</p><ul><li>SystemStatus_IN_INITIAL: Initializing</li><li>SystemStatus_IN_READY: Transition completed</li><li>SystemStatus_IN_MOVE: Transitioning</li><li>SystemStatus_IN_ROLLBACK: Rolling back</li><li>SystemStatus_IN_RECOVERY: Recovering</li></ul></li></ul></td></tr><tr><td>Example Script</td><td>examples/status/get_system_status.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HDSService/ClearAlert</code></td></tr><tr><td>Function Summary</td><td>Attempt to clear an alert, requiring the alert ID to be passed in</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:50587/rpc/aimdk.protocol.HDSService/ClearAlert</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "id": "c92f2fdd-cea5-4209-b02f-d0eb62ae18ce"
}
</code></pre><ul><li>id: You need to fill in the specific alert ID, which can be obtained through the GetAlertList interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "1",
    "msg": "clear alert failed!",
    "trace_id": "",
    "domin": ""
  },
  "data": {
    "data": "c92f2fdd-cea5-4209-b02f-d0eb62ae18ce"
  }
}
</code></pre><ul><li>data: The alert ID passed in</li><li>The header returns information about whether the current clearing was successful, a code of 0 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/hds/clear_alert.sh</td></tr><tr><td>Notes</td><td><ul><li>Although the emergency stop alert has manual_clear set to true, it will still fail to clear. The emergency stop must be manually released before it can be cleared.</li><li>In general, do not call this interface to clear alerts. Please fully understand the meaning of the alert before considering using this interface to clear it.</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HDSService/GetAlertList</code></td></tr><tr><td>Function Summary</td><td>Get the current alert list</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:50587/rpc/aimdk.protocol.HDSService/GetAlertList</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "alerts": [
      {
        "id": "c39f6ccc-85d9-4976-a2e9-08f2906cc237",
        "appeared_timestamp": "1762933137153",
        "disappeared_timestamp": "0",
        "alert_code": "A2000003",
        "state": "AlertState_ACTIVE",
        "exception_list": [
          {
            "type": "ExceptionType_Normal",
            "module_id": 81,
            "code": 100,
            "info": "Emergency stop pressed",
            "module_name": "Health Management HDS"
          }
        ],
        "description": "Emergency stop pressed",
        "level": "AlertLevel_HIDDEN_DANGERS",
        "manual_clear": true,
        "show_type": "AlertShowType_Normal",
        "solution_list": [
          {
            "type": "txt",
            "content": "Please rotate the emergency stop button counterclockwise to release the emergency stop state."
          }
        ]
      }
    ]
  }
}
</code></pre><ul><li>id: The ID of this alert</li><li>appeared_timestamp: The timestamp when the alert appeared</li><li>disappeared_timestamp: The timestamp when the alert disappeared</li><li>alert_code: The alert code</li><li><p>state: The alert state</p><ul><li>AlertState_UNDEFINED: Unknown</li><li>AlertState_ACTIVE: In alert</li><li>AlertState_CLEARED: Cleared</li><li>AlertState_ExceptionChanged: Alert with changed exception</li><li>AlertState_Recovering: Recovering</li></ul></li><li>exception_list: The list of exceptions</li><li><p>exception_list[i].type: The type of exception</p><ul><li>ExceptionType_Normal: Normal type, this type of exception needs to be reported periodically</li><li>ExceptionType_Trigger_Appear: Triggered exception (reported once when the exception occurs), set this exception to the occurrence state</li><li>ExceptionType_Trigger_Disappear: Triggered exception (reported once when the exception disappears), set this exception to the disappearance state</li></ul></li><li>exception_list[i].module_id: The ID of the module where the exception occurred</li><li>exception_list[i].code: The module exception code</li><li>exception_list[i].info: The exception information</li><li>exception_list[i].module_name: The name of the module</li><li>description: The alert description</li><li><p>level: The alert level</p><ul><li>AlertLevel_UNDEFINED: No alert</li><li>AlertLevel_FATAL: Fatal alert</li><li>AlertLevel_SERIOUS: Serious alert</li><li>AlertLevel_WARNING: Warning alert</li><li>AlertLevel_HIDDEN_DANGERS: The current system has potential hazards</li><li>AlertLevel_STATUS: The current system has status-related alerts</li></ul></li><li>manual_clear: Whether manual clearing is supported</li><li><p>show_type: The type of alert display</p><ul><li>AlertShowType_Normal</li><li>AlertShowType_Toast</li></ul></li><li>solution_list: The list of solutions</li><li>solution_list[i].type: The type of solution</li><li>solution_list[i].content: The content of the solution</li></ul></td></tr><tr><td>Example Script</td><td>examples/hds/get_alert_list.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalAudioService/SetAudioVolume</code></td></tr><tr><td>Function Summary</td><td>Adjust the volume</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.HalAudioService/SetAudioVolume</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "audio_volume": 70,
  "is_mute": false
}
</code></pre><ul><li>audio_volume: Volume level, a value between 0-100. <strong>Note: Do not set the volume above 70, as exceeding this range will cause the speaker to exceed its rated operating capacity, leading to damage</strong></li><li>is_mute: Whether muted</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "SetAudioVolume successfully",
    "trace_id": "",
    "domin": ""
  },
  "pkg_name": "",
  "is_success": false
}
</code></pre><ul><li>pkg_name: Invalid field, no need to pay attention</li><li>is_success: Invalid field, no need to pay attention</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/set_audio_volume.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalAudioService/GetAudioVolume</code></td></tr><tr><td>Function Summary</td><td>Get the current volume level</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.HalAudioService/GetAudioVolume</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "GetAudioVolume successfully",
    "trace_id": "",
    "domin": ""
  },
  "audio_volume": 80,
  "is_mute": false
}
</code></pre><ul><li>audio_volume: Volume level, a value between 0-100</li><li>is_mute: Whether muted</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/get_audio_volume.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/StopTTS</code></td></tr><tr><td>Function Summary</td><td>Terminate all audio file playback, including the current playback task and all tasks in the queue</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/StopTTS</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_UNKNOWN"
}
</code></pre><ul><li>state: Request status, no need to pay attention to the specific value, HTTP request returning 200 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/stop_all.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/StopTTSTraceId</code></td></tr><tr><td>Function Summary</td><td>Interrupt a single file playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/StopTTSTraceId</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "trace_id": "hafhjkqwjwefk"
}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_UNKNOWN"
}
</code></pre><ul><li>state: Request status, no need to pay attention to the specific value, HTTP request returning 200 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/stop_trace_id.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/GetAudioStatus</code></td></tr><tr><td>Function Summary</td><td>Audio file playback status query</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/GetAudioStatus</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "trace_id": "hafhjkqwjwefk"
}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "tts_status": {
    "text": "",
    "priority": 0,
    "trace_id": "",
    "tts_status": "TTSStatusType_Playing",
    "domain": "",
    "error_message": ""
  }
}
</code></pre><ul><li><p>tts_status: Playback status, enumeration values</p><ul><li>TTSConfigStatusType_Unknown: Unknown status</li><li>TTSStatusType_Begin: Start playback, brief, usually not queried</li><li>TTSStatusType_Playing: Playing</li><li>TTSStatusType_End: End of playback, brief, usually not queried</li><li>TTSStatusType_Stop: Pause playback/cancel playback/interrupt playback</li><li>TTSStatusType_Error: Playback failed</li><li>TTSStatusType_InQue: In the playback queue, not yet started</li><li>TTSStatusType_NOTInQue: No such text in the playback queue, not playing, enters this state after playback ends</li></ul></li><li>The rest of the fields are invalid and do not need to be paid attention to</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/get_audio_status.sh</td></tr><tr><td>Notes</td><td>A successful playback queried through this RPC interface generally returns InQue, Playing, and NOTInQue states</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/PlayMediaFile</code></td></tr><tr><td>Function Summary</td><td>Audio file playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/PlayMediaFile</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "file_name": "wake.pcm",
  "priority_level": "INTERACTION_L6",
  "domain": "example",
  "trace_id": "hafhjkqwjwefk",
  "is_interrupted": true
}
</code></pre><ul><li>file_name: File name (stored in <code>/agibot/data/var/interaction/audio/</code>, for example, wake.pcm. The file should be a 24kHz, 16-bit, mono PCM file. A separate folder needs to be created, and the input should be in the format of folder name/file name, such as file/wake.pcm)</li><li>priority_level: Priority level, keep INTERACTION_L6</li><li>domain: Caller source identifier, you can pass in a custom client string for easier troubleshooting, etc.</li><li>trace_id: Playback ID, if you need to get the playback status, you need to pass this field and use its value as the parameter to query the playback status</li><li>is_interrupted: Whether to interrupt playback of the same priority, please default to true. For queue playback requirements, you can use false</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "text": "wake.pcm",
  "priority_level": "INTERACTION_L6",
  "priority_weight": 0,
  "domain": "example",
  "trace_id": "hafhjkqwjwefk",
  "is_sucess": true,
  "error_message": "",
  "estimated_duration": 0
}
</code></pre><ul><li>text: File name</li><li>priority_level: Priority level, no need to pay attention</li><li>pritority_weight: Priority weight, no need to pay attention</li><li>domain: Caller source identifier, returns the custom string passed in the request for easier troubleshooting</li><li>trace_id: Playback ID, returns the custom string passed in the request for easier troubleshooting</li><li>is_success: Whether the priority check was successful, generally true, but it does not mean it will play. For example, passing an incorrect or non-existent file name will still return true. Only when there is a higher-priority content being played, such as a fault alarm, will it return true</li><li>estimated_duration: Invalid field, no need to pay attention, unable to estimate playback duration</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/play_media_file.sh</td></tr><tr><td>Notes</td><td><ul><li>Supports standard 44-byte header Linear PCM wav files. Other header formats and compressed formats are not supported. It is recommended to use 24kHz, 16-bit, mono PCM files</li><li>If an incorrect or non-existent file name is passed, it will silently fail without playing, and is_success will return true</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/EnableNeckMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Enable the action playback module to control the neck, start continuously sending neck control instructions to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/EnableNeckMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/enable_neck_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/DisableNeckMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Disable the action playback module from controlling the neck motor, the process will not exit, and no neck instructions will be sent to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableNeckMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/disable_neck_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/EnableMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Enable the action playback module, start continuously sending instructions to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/EnableMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/enable_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/DisableMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Disable the action playback module, the process will not exit, and no instructions will be sent to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/disable_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/</code>GetMotionStatus</td></tr><tr><td>Function Summary</td><td>Get the action playback status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/GetMotionStatus</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762852836",
      "nanos": 502608623,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "time_to_end_ms": "235",
  "status": "MotionCommandStatus_OPERATING",
  "is_neck_enable": true,
  "motion_id": "1Wave Hello"
}
</code></pre><ul><li>time_to_end_ms: Time remaining until the end of the action, in milliseconds</li><li><p>status: Action playback status</p><ul><li>MotionCommandStatus_IDLE: No action, idle</li><li>MotionCommandStatus_START: Action starts playing</li><li>MotionCommandStatus_OPERATING: Action is playing</li><li>MotionCommandStatus_PAUSE: State when calling the action playback interface with cmd_pause=true</li><li>MotionCommandStatus_STOP: State after calling DisableMotionPlayer</li></ul></li><li>is_neck_enable: Whether the neck is controlled by the motion_player</li><li>motion_id: Action name</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/get_motion_status.sh</td></tr><tr><td>Notes</td><td>This interface call code is <strong>T2</strong>, and can only be called under the JOINT_SERVO suffix motion control Action</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/SendMotionCommand</code></td></tr><tr><td>Function Summary</td><td>Play the specified action file</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/SendMotionCommand</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "motion_id": "/agibot/data/resources/default/motion/motion_player/default/Wave Both Hands/Wave Both Hands",
  "duration_ms": 10000,
  "cmd_end": true,
  "cmd_pause": false,
  "cmd_reset": false
}
</code></pre><ul><li><p>motion_id: Absolute path of the action file, up to the last .db file, without the .db suffix, for example:</p><ul><li>/agibot/data/resources/default/motion/motion_player/default/Wave Both Hands/Wave Both Hands</li></ul></li><li>duration_ms: An invalid field, leave it as is</li><li>cmd_end: Whether to automatically return to the initial posture after the action is executed, <code>true</code> indicates automatic reset, <code>false</code> indicates no automatic reset</li><li>cmd_pause: Action pause flag, <code>true</code> indicates pause, which will stop sending control signals to the robot, generally not used</li><li>cmd_reset: Reset flag, <code>true</code> indicates reset, <code>false</code> indicates no reset. The reset operation will reset the current action state to the initial state</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762851946",
      "nanos": 693223585,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/send_motion_id.sh</td></tr><tr><td>Notes</td><td>This interface call code is <strong>T2</strong>, and can only be called under the JOINT_SERVO suffix motion control Action</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/SelectDanceType</code></td></tr><tr><td>Function Overview</td><td>Full-body dance playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/SelectDanceType</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "timestamp": {
      "seconds": 1762818960,
      "nanos": 172949000,
      "ms_since_epoch": 1762818960172
    },
    "control_source": "ControlSource_SAFE"
  },
  "dance_name": "jiangnan"
}
</code></pre><ul><li>dance_name: Dance name, which needs to be obtained from the above dance list retrieval interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762847760",
      "nanos": 178468357,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/SelectDanceType.py</td></tr><tr><td>Notes</td><td><ul><li>The call code for this interface is <strong>S1</strong>, and it can only be called in RL_WHOLE_BODY_DANCE mode</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/GetDanceTypeList</code></td></tr><tr><td>Function Overview</td><td>Retrieve the list of supported full-body dances</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetDanceTypeList</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "dance_name": [
    "Swing Dance",
    "Victory Dance"
  ],
  "dance_model_path": [
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/policy_ybw_1127.onnx",
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/policy_vict_1203.onnx"
  ],
  "dance_data_path": [
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/export_data_ybw.npy",
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/export_data_vict_v6.npy"
  ],
  "dance_time": [
    93.64,
    75.56
  ]
}
</code></pre><ul><li>dance_name: Dance name, used for input to the play interface</li><li>dance_model_path: Location of the dance model file, no need to pay attention</li><li>dance_data_path: Location of the dance data file, no need to pay attention</li><li>dance_time: Duration of the dance in seconds</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetDanceTypeList.py</td></tr><tr><td>Notes</td><td><ul><li>This interface has no call restrictions</li></ul></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McDataService/GetJointState</code></td></tr><tr><td>Function Overview</td><td>Retrieve the state of upper and lower limb joints</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetJointState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "states": [
    {
      "name": "idx01_left_hip_roll",
      "sequence": 0,
      "position": 0.006256103515625,
      "velocity": 0.0048847198486328125,
      "effort": -13.367523193359375
    },
    {
      "name": "idx02_left_hip_yaw",
      "sequence": 0,
      "position": 0.013275146484375,
      "velocity": 0.024419784545898438,
      "effort": -11.658126831054688
    },
    {
      "name": "idx03_left_hip_pitch",
      "sequence": 0,
      "position": -0.11947822570800781,
      "velocity": -0.0048847198486328125,
      "effort": 1.015869140625
    },
    {
      "name": "idx04_left_tarsus",
      "sequence": 0,
      "position": 0.28732776641845703,
      "velocity": -0.0048847198486328125,
      "effort": -10.862030029296875
    },
    {
      "name": "idx05_left_toe_pitch",
      "sequence": 0,
      "position": -0.17624187469482422,
      "velocity": 0,
      "effort": 3.44881189007971
    },
    {
      "name": "idx06_left_toe_roll",
      "sequence": 0,
      "position": -0.012819436684095006,
      "velocity": 0.009888242426560891,
      "effort": 2.4995190811765715
    },
    {
      "name": "idx07_right_hip_roll",
      "sequence": 0,
      "position": -0.009918212890625,
      "velocity": -0.014652252197265625,
      "effort": 14.119659423828125
    },
    {
      "name": "idx08_right_hip_yaw",
      "sequence": 0,
      "position": -0.011749267578125,
      "velocity": 0.024419784545898438,
      "effort": 14.25640869140625
    },
    {
      "name": "idx09_right_hip_pitch",
      "sequence": 0,
      "position": -0.12344551086425781,
      "velocity": -0.0048847198486328125,
      "effort": -7.423675537109375
    },
    {
      "name": "idx10_right_tarsus",
      "sequence": 0,
      "position": 0.30014514923095703,
      "velocity": -0.014652252197265625,
      "effort": -18.676422119140625
    },
    {
      "name": "idx11_right_toe_pitch",
      "sequence": 0,
      "position": -0.18814373016357422,
      "velocity": -0.004883766174316406,
      "effort": 4.751964842417327
    },
    {
      "name": "idx12_right_toe_roll",
      "sequence": 0,
      "position": 0.012819560417340213,
      "velocity": 0.01981031932552883,
      "effort": -0.06747343675733508
    },
    {
      "name": "idx13_left_arm_joint1",
      "sequence": 0,
      "position": -0.053559280931949615,
      "velocity": -5.885322389076464e-05,
      "effort": -1.253999948501587
    },
    {
      "name": "idx14_left_arm_joint2",
      "sequence": 0,
      "position": 1.3100006580352783,
      "velocity": -6.644718814641237e-05,
      "effort": -2.2799999713897705
    },
    {
      "name": "idx15_left_arm_joint3",
      "sequence": 0,
      "position": 0,
      "velocity": 0,
      "effort": 2.2660000324249268
    },
    {
      "name": "idx16_left_arm_joint4",
      "sequence": 0,
      "position": -0.03490660712122917,
      "velocity": -4.366529537946917e-05,
      "effort": 1.715999960899353
    },
    {
      "name": "idx17_left_arm_joint5",
      "sequence": 0,
      "position": 1.5707954168319702,
      "velocity": 0,
      "effort": 0.06880000233650208
    },
    {
      "name": "idx18_left_arm_joint6",
      "sequence": 0,
      "position": 0.75,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx19_left_arm_joint7",
      "sequence": 0,
      "position": 2.995796503389102e-08,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx20_right_arm_joint1",
      "sequence": 0,
      "position": 0.03456582874059677,
```json
      "velocity": 6.644718723691767e-06,
      "effort": 0.722000002861023
    },
    {
      "name": "idx21_right_arm_joint2",
      "sequence": 0,
      "position": -1.3099987506866455,
      "velocity": 0,
      "effort": 1.7100000381469727
    },
    {
      "name": "idx22_right_arm_joint3",
      "sequence": 0,
      "position": -9.492455319559667e-07,
      "velocity": 7.40411487640813e-05,
      "effort": 1.5839999914169312
    },
    {
      "name": "idx23_right_arm_joint4",
      "sequence": 0,
      "position": 0.08476477861404419,
      "velocity": -5.1259259635116905e-05,
      "effort": 0.7919999957084656
    },
    {
      "name": "idx24_right_arm_joint5",
      "sequence": 0,
      "position": 1.5707954168319702,
      "velocity": 0,
      "effort": -0.5504000186920166
    },
    {
      "name": "idx25_right_arm_joint6",
      "sequence": 0,
      "position": -0.75,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx26_right_arm_joint7",
      "sequence": 0,
      "position": 3.001038685424783e-08,
      "velocity": 0,
      "effort": 0
    }
  ]
}
```
The 6th and 7th joints of both arms are invalid values
</code></pre></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetJointState.py</td></tr><tr><td>Notes</td><td>This interface has no Action restrictions</td></tr></tbody></table>



| Interface Name    | `/motion/control/arm_joint_state`                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Overview | Arm joint state topic                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Interface Type    | ROS2 Topic                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Output Parameters | <p><a href="https://docs.ros.org/en/humble/p/sensor_msgs/msg/JointState.html">sensor_msgs::msg::JointState</a></p><ul><li>name: 14 joint names, where joints 6 and 7 of both arms are invalid</li><li>position: 14 joint angles, where joints 6 and 7 of both arms are invalid</li><li>velocity: 14 joint velocities, where joints 6 and 7 of both arms are invalid</li><li>effort: 14 joint torques, where joints 6 and 7 of both arms are invalid</li></ul> |
| Example Script    | examples/motion\_control/joint\_state.py                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Notes             | This interface has no Action restrictions                                                                                                                                                                                                                                                                                                                                                                                                                     |

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McDataService/GetJointState</code></td></tr><tr><td>Function Overview</td><td>Retrieve the state of upper and lower limb joints</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetJointState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "states": [
    {
      "name": "idx01_left_hip_roll",
      "sequence": 0,
      "position": 0.006256103515625,
      "velocity": 0.0048847198486328125,
      "effort": -13.367523193359375
    },
    {
      "name": "idx02_left_hip_yaw",
      "sequence": 0,
      "position": 0.013275146484375,
      "velocity": 0.024419784545898438,
      "effort": -11.658126831054688
    },
    {
      "name": "idx03_left_hip_pitch",
      "sequence": 0,
      "position": -0.11947822570800781,
      "velocity": -0.0048847198486328125,
      "effort": 1.015869140625
    },
    {
      "name": "idx04_left_tarsus",
      "sequence": 0,
      "position": 0.28732776641845703,
      "velocity": -0.0048847198486328125,
      "effort": -10.862030029296875
    },
    {
      "name": "idx05_left_toe_pitch",
      "sequence": 0,
      "position": -0.17624187469482422,
      "velocity": 0,
      "effort": 3.44881189007971
    },
    {
      "name": "idx06_left_toe_roll",
      "sequence": 0,
      "position": -0.012819436684095006,
      "velocity": 0.009888242426560891,
      "effort": 2.4995190811765715
    },
    {
      "name": "idx07_right_hip_roll",
      "sequence": 0,
      "position": -0.009918212890625,
      "velocity": -0.014652252197265625,
      "effort": 14.119659423828125
    },
    {
      "name": "idx08_right_hip_yaw",
      "sequence": 0,
      "position": -0.011749267578125,
      "velocity": 0.024419784545898438,
      "effort": 14.25640869140625
    },
    {
      "name": "idx09_right_hip_pitch",
      "sequence": 0,
      "position": -0.12344551086425781,
      "velocity": -0.0048847198486328125,
      "effort": -7.423675537109375
    },
    {
      "name": "idx10_right_tarsus",
      "sequence": 0,
      "position": 0.30014514923095703,
      "velocity": -0.014652252197265625,
      "effort": -18.676422119140625
    },
    {
      "name": "idx11_right_toe_pitch",
      "sequence": 0,
      "position": -0.18814373016357422,
      "velocity": -0.004883766174316406,
      "effort": 4.751964842417327
    },
    {
      "name": "idx12_right_toe_roll",
      "sequence": 0,
      "position": 0.012819560417340213,
      "velocity": 0.01981031932552883,
      "effort": -0.06747343675733508
    },
    {
      "name": "idx13_left_arm_joint1",
      "sequence": 0,
      "position": -0.053559280931949615,
      "velocity": -5.885322389076464e-05,
      "effort": -1.253999948501587
    },
    {
      "name": "idx14_left_arm_joint2",
      "sequence": 0,
      "position": 1.3100006580352783,
      "velocity": -6.644718814641237e-05,
      "effort": -2.2799999713897705
    },
    {
      "name": "idx15_left_arm_joint3",
      "sequence": 0,
      "position": 0,
      "velocity": 0,
      "effort": 2.2660000324249268
    },
    {
      "name": "idx16_left_arm_joint4",
      "sequence": 0,
      "position": -0.03490660712122917,
      "velocity": -4.366529537946917e-05,
      "effort": 1.715999960899353
    },
    {
      "name": "idx17_left_arm_joint5",
      "sequence": 0,
      "position": 1.5707954168319702,
      "velocity": 0,
      "effort": 0.06880000233650208
    },
    {
      "name": "idx18_left_arm_joint6",
      "sequence": 0,
      "position": 0.75,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx19_left_arm_joint7",
      "sequence": 0,
      "position": 2.995796503389102e-08,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx20_right_arm_joint1",
      "sequence": 0,
      "position": 0.03456582874059677,
```json
      "velocity": 6.644718723691767e-06,
      "effort": 0.722000002861023
    },
    {
      "name": "idx21_right_arm_joint2",
      "sequence": 0,
      "position": -1.3099987506866455,
      "velocity": 0,
      "effort": 1.7100000381469727
    },
    {
      "name": "idx22_right_arm_joint3",
      "sequence": 0,
      "position": -9.492455319559667e-07,
      "velocity": 7.40411487640813e-05,
      "effort": 1.5839999914169312
    },
    {
      "name": "idx23_right_arm_joint4",
      "sequence": 0,
      "position": 0.08476477861404419,
      "velocity": -5.1259259635116905e-05,
      "effort": 0.7919999957084656
    },
    {
      "name": "idx24_right_arm_joint5",
      "sequence": 0,
      "position": 1.5707954168319702,
      "velocity": 0,
      "effort": -0.5504000186920166
    },
    {
      "name": "idx25_right_arm_joint6",
      "sequence": 0,
      "position": -0.75,
      "velocity": 0,
      "effort": 0
    },
    {
      "name": "idx26_right_arm_joint7",
      "sequence": 0,
      "position": 3.001038685424783e-08,
      "velocity": 0,
      "effort": 0
    }
  ]
}
```
The 6th and 7th joints of both arms are invalid values
</code></pre></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetJointState.py</td></tr><tr><td>Notes</td><td>This interface has no Action restrictions</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/GetDanceTypeList</code></td></tr><tr><td>Function Overview</td><td>Retrieve the list of supported full-body dances</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/GetDanceTypeList</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "dance_name": [
    "Swing Dance",
    "Victory Dance"
  ],
  "dance_model_path": [
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/policy_ybw_1127.onnx",
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/policy_vict_1203.onnx"
  ],
  "dance_data_path": [
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/export_data_ybw.npy",
    "/home/agi/a2_simulation/motion_control_lite_1.2.22/bin/../config/motion_control/configuration/robot/raise_a2_lite/learning_controller_dance/models/export_data_vict_v6.npy"
  ],
  "dance_time": [
    93.64,
    75.56
  ]
}
</code></pre><ul><li>dance_name: Dance name, used for input to the play interface</li><li>dance_model_path: Location of the dance model file, no need to pay attention</li><li>dance_data_path: Location of the dance data file, no need to pay attention</li><li>dance_time: Duration of the dance in seconds</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/GetDanceTypeList.py</td></tr><tr><td>Notes</td><td><ul><li>This interface has no call restrictions</li></ul></td></tr></tbody></table>

**7.1.10 Full-Body Dance Playback RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.McMotionService/SelectDanceType</code></td></tr><tr><td>Function Overview</td><td>Full-body dance playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56322/rpc/aimdk.protocol.McMotionService/SelectDanceType</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "timestamp": {
      "seconds": 1762818960,
      "nanos": 172949000,
      "ms_since_epoch": 1762818960172
    },
    "control_source": "ControlSource_SAFE"
  },
  "dance_name": "jiangnan"
}
</code></pre><ul><li>dance_name: Dance name, which needs to be obtained from the above dance list retrieval interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762847760",
      "nanos": 178468357,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_control/SelectDanceType.py</td></tr><tr><td>Notes</td><td><ul><li>The call code for this interface is <strong>S1</strong>, and it can only be called in RL_WHOLE_BODY_DANCE mode</li></ul></td></tr></tbody></table>

### 7.2 Action Playback Section <a href="#web-09-7-2-action-playback-section" id="web-09-7-2-action-playback-section"></a>

**7.2.1 Overview**

The A2 Lite provides basic preset action playback capabilities, with some preset actions pre-installed on the machine (additional actions can be recorded using remote operation devices to meet more personalized needs; for more information, please refer to the relevant documentation on remote operation). The list of default preset actions is as follows:

text

```
wave-both-hands/wave-both-hands
wave-right-hand/wave-right-hand
right-hand-handshake/right-hand-handshake
right-hand-handshake_long/right-hand-handshake_long
look-right/1758103570432482028
look-left/1758103588180395683
wave-left-hand/wave-left-hand
left-hand-handshake/left-hand-handshake
left-hand-handshake_long/left-hand-handshake_long
posed-photo_strongman-pose/posed-photo_strongman-pose
salute/salute
look-around/1758103607745291736
look-at-both-hands/1758104272873252746
look-at-right-hand/1758104294863353043
look-at-right-arm/1758103484383524451
look-at-left-hand/175810431583786588
look-at-left-arm/1758103505321711264
```

The above action files are located in the x86 directory `/agibot/data/resources/default/motion/motion_player/default`. Custom recorded actions should be placed in the `/agibot/data/resources/default/motion/motion_player/custom` directory. The above list is obtained by specifying the following command in the corresponding directory:

bash

```
find . -name "*.db" -type f | sed 's|^\./\([^/]*\)/\(.*\)\.db|\1/\2|' | sort
```

The specific action effects can be viewed using the motion control simulation provided in subsequent chapters or directly on the real machine.

Onboard action playback is handled by the `motion_player` module, which controls the arm and neck joints in JOINT\_SERVO mode. The basic control principle involves reading and parsing the specified action file, playing the action file at 100 Hz, and sending `/motion/control/arm_joint_command` and `/motion/control/neck_joint_command` to the motion control module, which then performs the corresponding actions.

**7.2.2 Action Playback RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/SendMotionCommand</code></td></tr><tr><td>Function Summary</td><td>Play the specified action file</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/SendMotionCommand</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "motion_id": "/agibot/data/resources/default/motion/motion_player/default/Wave Both Hands/Wave Both Hands",
  "duration_ms": 10000,
  "cmd_end": true,
  "cmd_pause": false,
  "cmd_reset": false
}
</code></pre><ul><li><p>motion_id: Absolute path of the action file, up to the last .db file, without the .db suffix, for example:</p><ul><li>/agibot/data/resources/default/motion/motion_player/default/Wave Both Hands/Wave Both Hands</li></ul></li><li>duration_ms: An invalid field, leave it as is</li><li>cmd_end: Whether to automatically return to the initial posture after the action is executed, <code>true</code> indicates automatic reset, <code>false</code> indicates no automatic reset</li><li>cmd_pause: Action pause flag, <code>true</code> indicates pause, which will stop sending control signals to the robot, generally not used</li><li>cmd_reset: Reset flag, <code>true</code> indicates reset, <code>false</code> indicates no reset. The reset operation will reset the current action state to the initial state</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762851946",
      "nanos": 693223585,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "state": "CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/send_motion_id.sh</td></tr><tr><td>Notes</td><td>This interface call code is <strong>T2</strong>, and can only be called under the JOINT_SERVO suffix motion control Action</td></tr></tbody></table>

**7.2.3 Action Playback Status Query RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/</code>GetMotionStatus</td></tr><tr><td>Function Summary</td><td>Get the action playback status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/GetMotionStatus</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "timestamp": {
      "seconds": "1762852836",
      "nanos": 502608623,
      "ms_since_epoch": "0"
    },
    "trace_id": "",
    "domin": ""
  },
  "time_to_end_ms": "235",
  "status": "MotionCommandStatus_OPERATING",
  "is_neck_enable": true,
  "motion_id": "1Wave Hello"
}
</code></pre><ul><li>time_to_end_ms: Time remaining until the end of the action, in milliseconds</li><li><p>status: Action playback status</p><ul><li>MotionCommandStatus_IDLE: No action, idle</li><li>MotionCommandStatus_START: Action starts playing</li><li>MotionCommandStatus_OPERATING: Action is playing</li><li>MotionCommandStatus_PAUSE: State when calling the action playback interface with cmd_pause=true</li><li>MotionCommandStatus_STOP: State after calling DisableMotionPlayer</li></ul></li><li>is_neck_enable: Whether the neck is controlled by the motion_player</li><li>motion_id: Action name</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/get_motion_status.sh</td></tr><tr><td>Notes</td><td>This interface call code is <strong>T2</strong>, and can only be called under the JOINT_SERVO suffix motion control Action</td></tr></tbody></table>

**7.2.4 Disable and Enable Action Playback Module RPC Interface**

The action playback module continuously sends /motion/control/arm\_joint\_command and /motion/control/neck\_joint\_command control instructions to the motion control module in JOINT\_SERVO mode. If a secondary program also sends instructions, it can cause conflicts. You can use the following interfaces to disable and enable the action playback module.

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/DisableMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Disable the action playback module, the process will not exit, and no instructions will be sent to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/disable_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/EnableMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Enable the action playback module, start continuously sending instructions to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/EnableMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/enable_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

**7.2.5 Disable and Enable Neck Control for Action Playback RPC Interface**

In some cases, it is necessary to disable the neck's action playback function separately, thereby transferring control of the neck to a secondary program for head tracking, etc. You can use the following interfaces to disable and enable neck control for action playback.

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/DisableNeckMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Disable the action playback module from controlling the neck motor, the process will not exit, and no neck instructions will be sent to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableNeckMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/disable_neck_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.MotionCommandService/EnableNeckMotionPlayer</code></td></tr><tr><td>Function Summary</td><td>Enable the action playback module to control the neck, start continuously sending neck control instructions to the motion control module</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/EnableNeckMotionPlayer</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_SUCCESS"
}
</code></pre><ul><li>state: Call request status</li></ul></td></tr><tr><td>Example Script</td><td>examples/motion_player/enable_neck_motion_player.sh</td></tr><tr><td>Notes</td><td>This interface has no call code restriction</td></tr></tbody></table>

### 7.3 Audio Playback Section <a href="#web-10-7-3-audio-playback-section" id="web-10-7-3-audio-playback-section"></a>

**7.3.1 Overview**

The A2 Lite robot does not have a microphone and thus cannot perform voice interaction functions. However, it is equipped with a speaker that can play basic audio files and adjust volume. It also supports queue playback, playback status queries, and interruption control logic.

**7.3.2 Audio File Playback RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/PlayMediaFile</code></td></tr><tr><td>Function Summary</td><td>Audio file playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/PlayMediaFile</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "file_name": "wake.pcm",
  "priority_level": "INTERACTION_L6",
  "domain": "example",
  "trace_id": "hafhjkqwjwefk",
  "is_interrupted": true
}
</code></pre><ul><li>file_name: File name (stored in <code>/agibot/data/var/interaction/audio/</code>, for example, wake.pcm. The file should be a 24kHz, 16-bit, mono PCM file. A separate folder needs to be created, and the input should be in the format of folder name/file name, such as file/wake.pcm)</li><li>priority_level: Priority level, keep INTERACTION_L6</li><li>domain: Caller source identifier, you can pass in a custom client string for easier troubleshooting, etc.</li><li>trace_id: Playback ID, if you need to get the playback status, you need to pass this field and use its value as the parameter to query the playback status</li><li>is_interrupted: Whether to interrupt playback of the same priority, please default to true. For queue playback requirements, you can use false</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "text": "wake.pcm",
  "priority_level": "INTERACTION_L6",
  "priority_weight": 0,
  "domain": "example",
  "trace_id": "hafhjkqwjwefk",
  "is_sucess": true,
  "error_message": "",
  "estimated_duration": 0
}
</code></pre><ul><li>text: File name</li><li>priority_level: Priority level, no need to pay attention</li><li>pritority_weight: Priority weight, no need to pay attention</li><li>domain: Caller source identifier, returns the custom string passed in the request for easier troubleshooting</li><li>trace_id: Playback ID, returns the custom string passed in the request for easier troubleshooting</li><li>is_success: Whether the priority check was successful, generally true, but it does not mean it will play. For example, passing an incorrect or non-existent file name will still return true. Only when there is a higher-priority content being played, such as a fault alarm, will it return true</li><li>estimated_duration: Invalid field, no need to pay attention, unable to estimate playback duration</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/play_media_file.sh</td></tr><tr><td>Notes</td><td><ul><li>Supports standard 44-byte header Linear PCM wav files. Other header formats and compressed formats are not supported. It is recommended to use 24kHz, 16-bit, mono PCM files</li><li>If an incorrect or non-existent file name is passed, it will silently fail without playing, and is_success will return true</li></ul></td></tr></tbody></table>

**7.3.3 Audio File Playback Status Query RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/GetAudioStatus</code></td></tr><tr><td>Function Summary</td><td>Audio file playback status query</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/GetAudioStatus</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "trace_id": "hafhjkqwjwefk"
}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "tts_status": {
    "text": "",
    "priority": 0,
    "trace_id": "",
    "tts_status": "TTSStatusType_Playing",
    "domain": "",
    "error_message": ""
  }
}
</code></pre><ul><li><p>tts_status: Playback status, enumeration values</p><ul><li>TTSConfigStatusType_Unknown: Unknown status</li><li>TTSStatusType_Begin: Start playback, brief, usually not queried</li><li>TTSStatusType_Playing: Playing</li><li>TTSStatusType_End: End of playback, brief, usually not queried</li><li>TTSStatusType_Stop: Pause playback/cancel playback/interrupt playback</li><li>TTSStatusType_Error: Playback failed</li><li>TTSStatusType_InQue: In the playback queue, not yet started</li><li>TTSStatusType_NOTInQue: No such text in the playback queue, not playing, enters this state after playback ends</li></ul></li><li>The rest of the fields are invalid and do not need to be paid attention to</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/get_audio_status.sh</td></tr><tr><td>Notes</td><td>A successful playback queried through this RPC interface generally returns InQue, Playing, and NOTInQue states</td></tr></tbody></table>

**7.3.4 Audio File Playback Interruption RPC Interface**

We provide interfaces for interrupting a single file playback and clearing the entire playback queue.

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/StopTTSTraceId</code></td></tr><tr><td>Function Summary</td><td>Interrupt a single file playback</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/StopTTSTraceId</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "trace_id": "hafhjkqwjwefk"
}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_UNKNOWN"
}
</code></pre><ul><li>state: Request status, no need to pay attention to the specific value, HTTP request returning 200 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/stop_trace_id.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.TTSService/StopTTS</code></td></tr><tr><td>Function Summary</td><td>Terminate all audio file playback, including the current playback task and all tasks in the queue</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.TTSService/StopTTS</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre><ul><li>trace_id: Playback ID, fill in the custom ID passed when calling the PlayMediaFile interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "state":"CommonState_UNKNOWN"
}
</code></pre><ul><li>state: Request status, no need to pay attention to the specific value, HTTP request returning 200 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/stop_all.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

**7.3.5 Volume Get and Set RPC Interfaces**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalAudioService/GetAudioVolume</code></td></tr><tr><td>Function Summary</td><td>Get the current volume level</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.HalAudioService/GetAudioVolume</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "GetAudioVolume successfully",
    "trace_id": "",
    "domin": ""
  },
  "audio_volume": 80,
  "is_mute": false
}
</code></pre><ul><li>audio_volume: Volume level, a value between 0-100</li><li>is_mute: Whether muted</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/get_audio_volume.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalAudioService/SetAudioVolume</code></td></tr><tr><td>Function Summary</td><td>Adjust the volume</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:59201/rpc/aimdk.protocol.HalAudioService/SetAudioVolume</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "audio_volume": 70,
  "is_mute": false
}
</code></pre><ul><li>audio_volume: Volume level, a value between 0-100. <strong>Note: Do not set the volume above 70, as exceeding this range will cause the speaker to exceed its rated operating capacity, leading to damage</strong></li><li>is_mute: Whether muted</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "SetAudioVolume successfully",
    "trace_id": "",
    "domin": ""
  },
  "pkg_name": "",
  "is_success": false
}
</code></pre><ul><li>pkg_name: Invalid field, no need to pay attention</li><li>is_success: Invalid field, no need to pay attention</li></ul></td></tr><tr><td>Example Script</td><td>examples/audio/set_audio_volume.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

### 7.4 Fault Diagnosis Section <a href="#fault-diagnosis" id="fault-diagnosis"></a>

**7.4.1 Overview**

The robot itself provides basic fault diagnosis and health monitoring capabilities, capable of monitoring some basic anomalies and faults, such as joint overheating, sensor failure, system occupancy consistently too high, low battery power, etc.

There are two basic concepts in fault diagnosis: Alert and Exception. An Alert is a cluster of Exceptions. An Alert represents a broad category of faults, while an Exception is a specific fault. For example, repositioning failure is an Alert, which corresponds to many different failure reasons, each being a specific Exception. AimMaster generally displays Alerts, as Exceptions can be numerous and less intuitive. If you need to continuously monitor the robot's abnormal state, it is recommended to query the current alert list at regular intervals (not too frequently, a frequency of 0.2 Hz or lower is recommended).

The full list of alerts can be found in the file `/agibot/software/v0/config/hds_master/database/alert_info.yaml` on the x86 machine.

**7.4.2 Get Current Alert List RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HDSService/GetAlertList</code></td></tr><tr><td>Function Summary</td><td>Get the current alert list</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:50587/rpc/aimdk.protocol.HDSService/GetAlertList</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "alerts": [
      {
        "id": "c39f6ccc-85d9-4976-a2e9-08f2906cc237",
        "appeared_timestamp": "1762933137153",
        "disappeared_timestamp": "0",
        "alert_code": "A2000003",
        "state": "AlertState_ACTIVE",
        "exception_list": [
          {
            "type": "ExceptionType_Normal",
            "module_id": 81,
            "code": 100,
            "info": "Emergency stop pressed",
            "module_name": "Health Management HDS"
          }
        ],
        "description": "Emergency stop pressed",
        "level": "AlertLevel_HIDDEN_DANGERS",
        "manual_clear": true,
        "show_type": "AlertShowType_Normal",
        "solution_list": [
          {
            "type": "txt",
            "content": "Please rotate the emergency stop button counterclockwise to release the emergency stop state."
          }
        ]
      }
    ]
  }
}
</code></pre><ul><li>id: The ID of this alert</li><li>appeared_timestamp: The timestamp when the alert appeared</li><li>disappeared_timestamp: The timestamp when the alert disappeared</li><li>alert_code: The alert code</li><li><p>state: The alert state</p><ul><li>AlertState_UNDEFINED: Unknown</li><li>AlertState_ACTIVE: In alert</li><li>AlertState_CLEARED: Cleared</li><li>AlertState_ExceptionChanged: Alert with changed exception</li><li>AlertState_Recovering: Recovering</li></ul></li><li>exception_list: The list of exceptions</li><li><p>exception_list[i].type: The type of exception</p><ul><li>ExceptionType_Normal: Normal type, this type of exception needs to be reported periodically</li><li>ExceptionType_Trigger_Appear: Triggered exception (reported once when the exception occurs), set this exception to the occurrence state</li><li>ExceptionType_Trigger_Disappear: Triggered exception (reported once when the exception disappears), set this exception to the disappearance state</li></ul></li><li>exception_list[i].module_id: The ID of the module where the exception occurred</li><li>exception_list[i].code: The module exception code</li><li>exception_list[i].info: The exception information</li><li>exception_list[i].module_name: The name of the module</li><li>description: The alert description</li><li><p>level: The alert level</p><ul><li>AlertLevel_UNDEFINED: No alert</li><li>AlertLevel_FATAL: Fatal alert</li><li>AlertLevel_SERIOUS: Serious alert</li><li>AlertLevel_WARNING: Warning alert</li><li>AlertLevel_HIDDEN_DANGERS: The current system has potential hazards</li><li>AlertLevel_STATUS: The current system has status-related alerts</li></ul></li><li>manual_clear: Whether manual clearing is supported</li><li><p>show_type: The type of alert display</p><ul><li>AlertShowType_Normal</li><li>AlertShowType_Toast</li></ul></li><li>solution_list: The list of solutions</li><li>solution_list[i].type: The type of solution</li><li>solution_list[i].content: The content of the solution</li></ul></td></tr><tr><td>Example Script</td><td>examples/hds/get_alert_list.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

**7.4.3 Attempt to Clear Alert RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HDSService/ClearAlert</code></td></tr><tr><td>Function Summary</td><td>Attempt to clear an alert, requiring the alert ID to be passed in</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:50587/rpc/aimdk.protocol.HDSService/ClearAlert</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "id": "c92f2fdd-cea5-4209-b02f-d0eb62ae18ce"
}
</code></pre><ul><li>id: You need to fill in the specific alert ID, which can be obtained through the GetAlertList interface</li></ul></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "1",
    "msg": "clear alert failed!",
    "trace_id": "",
    "domin": ""
  },
  "data": {
    "data": "c92f2fdd-cea5-4209-b02f-d0eb62ae18ce"
  }
}
</code></pre><ul><li>data: The alert ID passed in</li><li>The header returns information about whether the current clearing was successful, a code of 0 indicates success</li></ul></td></tr><tr><td>Example Script</td><td>examples/hds/clear_alert.sh</td></tr><tr><td>Notes</td><td><ul><li>Although the emergency stop alert has manual_clear set to true, it will still fail to clear. The emergency stop must be manually released before it can be cleared.</li><li>In general, do not call this interface to clear alerts. Please fully understand the meaning of the alert before considering using this interface to clear it.</li></ul></td></tr></tbody></table>

### 7.5 System Status Section <a href="#web-12-7-5-system-status-section" id="web-12-7-5-system-status-section"></a>

**7.5.1 Overview**

System status refers to the state of the software system, which can be referenced in the previous section _Software System Overview_.

**7.5.2 System Status Retrieval RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.SystemService/GetSystemState</code></td></tr><tr><td>Function Summary</td><td>Retrieve system status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:51011/rpc/aimdk.protocol.SystemService/GetSystemState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "header": {
    "code": "0",
    "msg": "",
    "trace_id": "",
    "domin": ""
  },
  "cur_state": "EStop",
  "cur_status": "SystemStatus_IN_READY"
}
</code></pre><ul><li><p>cur_state: Current system state</p><ul><li>Startup: Starting up state</li><li>Ready: Startup completed state</li><li>Manual: Manual operation state</li><li>MotionStream: Remote operation state</li><li>OTA: Remote upgrade state</li><li>Estop: Emergency stop state</li><li>Poweroff: Power off state</li><li>Reboot: Rebooting state</li><li>Reset: Resetting state</li><li>Safe: Safe state</li></ul></li><li><p>cur_status: Current system condition</p><ul><li>SystemStatus_IN_INITIAL: Initializing</li><li>SystemStatus_IN_READY: Transition completed</li><li>SystemStatus_IN_MOVE: Transitioning</li><li>SystemStatus_IN_ROLLBACK: Rolling back</li><li>SystemStatus_IN_RECOVERY: Recovering</li></ul></li></ul></td></tr><tr><td>Example Script</td><td>examples/status/get_system_status.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

**7.5.3 BMS Status Retrieval RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalBmsService/GetBmsState</code></td></tr><tr><td>Function Summary</td><td>Retrieve system status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56421/rpc/aimdk.protocol.HalBmsService/GetBmsState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "ver": {
      "hardware_major": 49,
      "hardware_minor": 48,
      "hardware_revision": 49,
      "software_major": 55,
      "software_minor": 48,
      "software_revision": 49
    },
    "voltage": 45460,
    "current": -1156,
    "power": 52551,
    "temperature": 289,
    "capacity": 4220,
    "charge": 29,
    "power_supply_health": "PowerSupplyHealth_GOOD",
    "power_supply_status": "PowerSupplyStatus_IDEL",
    "cycles_num": 1,
    "cycles_capacity": 21,
    "abnormal_state": "PowerAbnormalStatus_NORMAL",
    "charger_state": "ChargerNotPulgin",
    "bms_state": "BatteryStatus_Connected",
    "max_current": 0,
    "battery_firmware_type": "BatteryFirmwareType_OLD",
    "battery_key_state": "BatteryKeyStatus_SHORT_CURCUIT",
    "battery_pack_state": "BatteryPackStatus_NORMAL",
    "battery_comm_state": "BatteryCommunication_NORMAL"
  }
}
</code></pre><ul><li>ver: Version information</li><li>voltage: Current voltage, unit mV</li><li>current: Current current, unit mA</li><li>power: Current power, unit mW</li><li>temperature: Current temperature, unit 0.1 degrees Celsius</li><li>capacity: Current capacity, unit: mAh</li><li>charge: Current charge percentage</li><li>power_supply_health: Not currently available</li><li><p>power_supply_status: Charging status</p><ul><li>PowerSupplyStatus_IDEL</li><li>PowerSupplyStatus_CHARGING</li><li>PowerSupplyStatus_FULL</li></ul></li><li>cycles_num: Number of cycles</li><li>cycles_capacity: Cycle capacity (total charge and discharge capacity of the current battery pack), unit: Ah</li><li><p>abnormal_state: Abnormal status</p><ul><li>PowerAbnormalStatus_NORMAL</li><li>PowerAbnormalStatus_SHORT_CIRCUIT</li><li>PowerAbnormalStatus_DISCHARGE_OVERCURRENT</li><li>PowerAbnormalStatus_CHARGING_OVERCURRENT</li><li>PowerAbnormalStatus_UNDERVOLTAGE</li><li>PowerAbnormalStatus_OVERVOLTAGE</li><li>PowerAbnormalStatus_EXCEED_DISCHARGE_TEMP_LIMIT</li><li>PowerAbnormalStatus_EXCEED_CHARGING_TEMP_LIMIT</li></ul></li><li><p>charger_state: Whether the charger is plugged in</p><ul><li>ChargerNotPulgin</li><li>ChargerConnected</li></ul></li><li><p>bms_state: Whether the battery is connected</p><ul><li>BatteryStatus_NotPulgin</li><li>BatteryStatus_Connected</li></ul></li><li>max_current: Maximum current</li><li><p>battery_firmware_type: Battery pack firmware version</p><ul><li>BatteryFirmwareType_OLD</li><li>BatteryFirmwareType_NEW</li></ul></li><li><p>battery_key_state: Battery pack key status</p><ul><li>BatteryKeyStatus_SHORT_CURCUIT</li><li>BatteryKeyStatus_CONNECTED</li></ul></li><li><p>battery_pack_state: Battery pack abnormal status</p><ul><li>BatteryPackStatus_NORMAL</li><li>BatteryPackStatus_ABNORMAL</li></ul></li><li><p>battery_comm_state: Battery pack communication status</p><ul><li>BatteryCommunication_NORMAL</li><li>BatteryCommunication_ABNORMAL</li></ul></li></ul></td></tr><tr><td>Example Script</td><td>examples/status/get_bms_status.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

**7.5.4 Emergency Stop Status Retrieval RPC Interface**

When an emergency stop is triggered, an alert will also be issued, and the emergency stop status can be obtained through the GetAlertList. This section provides a separate interface to query the emergency stop status.

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.HalEmergencyService/GetEmergencyState</code></td></tr><tr><td>Function Summary</td><td>Retrieve emergency stop status</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:56421/rpc/aimdk.protocol.HalEmergencyService/GetEmergencyState</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "data": {
    "active": true,
    "reason": "Reason_WIRELESS_ESTOP",
    "left_front_sensor_alarm": false,
    "right_front_sensor_alarm": false,
    "left_sensor_alarm": false,
    "right_sensor_alarm": false,
    "left_back_sensor_alarm": false,
    "right_back_sensor_alarm": false,
    "lift_upper_limit_alarm": false,
    "lift_lower_limit_alarm": false,
    "tray_limit_alarm": false,
    "front_left_tof_alarm": false,
    "front_right_tof_alarm": false,
    "right_front_tof_alarm": false,
    "right_back_tof_alarm": false,
    "back_tof_alarm": false,
    "left_back_tof_alarm": false,
    "left_front_tof_alarm": false,
    "wired_emergency_stop": false,
    "wireless_emergency_stop": true,
    "software_emergency_stop": false
  }
}
</code></pre><ul><li>active: Whether the emergency stop is triggered</li><li>reason: Reason for the emergency stop</li><li>wireless_emergency_stop: Whether the wireless emergency stop is triggered</li><li>software_emergency_stop: Whether the software emergency stop is triggered</li></ul><p>Other fields are not of concern.</p></td></tr><tr><td>Example Script</td><td>examples/status/get_estop_status.sh</td></tr><tr><td>Notes</td><td><ul><li>The soft emergency stop interface is not yet open for secondary development, and cannot be triggered via the interface.</li><li>If an empty JSON body is returned, it indicates that all parameters are at their default values, meaning the emergency stop has not been triggered.</li></ul></td></tr></tbody></table>

**7.5.5 Software Version Retrieval RPC Interface**

<table data-header-hidden><thead><tr><th></th><th></th></tr></thead><tbody><tr><td>Interface Name</td><td><code>pb:/aimdk.protocol.OTAService/GetRobotOtaInfo</code></td></tr><tr><td>Function Summary</td><td>Retrieve software version information</td></tr><tr><td>Interface Type</td><td>HTTP JSON RPC</td></tr><tr><td>URL</td><td>http://127.0.0.1:57900/rpc/aimdk.protocol.OTAService/GetRobotOtaInfo</td></tr><tr><td>Input Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{}
</code></pre></td></tr><tr><td>Output Parameters</td><td><p>text</p><pre class="language-json"><code class="lang-json">{
  "robot_info": {
    "model": "A2_T3D1_LITE"
  },
  "current_apk_info": {
    "apk_version": "A2_LITE-v1.2.4-0-g17e2f79fe-2510271122",
    "pub_time": "",
    "soc_info": [],
    "mcu_info": [],
    "contents": "",
    "fota_version": ""
  },
  "support_rollback_apk_infos": []
}
</code></pre><ul><li>apk_version: Software version information</li></ul><p>Other fields are not of concern.</p></td></tr><tr><td>Example Script</td><td>examples/status/get_version_info.sh</td></tr><tr><td>Notes</td><td></td></tr></tbody></table>

### 8. Guide to Motion Control Simulation <a href="#web-13-8-guide-to-motion-control-simulation" id="web-13-8-guide-to-motion-control-simulation"></a>

#### 8.1 Simulation Description <a href="#web-13-8-1-simulation-description" id="web-13-8-1-simulation-description"></a>

We provide a mujoco-based simulation system for the A2 robot, designed to serve as a testing ground for basic calls to the A2 robot's motion control and action playback interfaces. This serves as a basic validation before actual operation, reducing the risk of damaging the robot while facilitating the debugging of secondary development program logic.

<figure><img src="../../.gitbook/assets/unknown (378).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>

The system runs the mujoco\_sim, motion\_control, and motion\_player components. mujoco\_sim acts as the underlying simulation engine, simulating the robot's physical body and hal\_ethercat. motion\_control interacts with mujoco\_sim to exchange control commands and status, thereby controlling the simulated robot. motion\_player, on the other hand, calls the high-level interfaces provided by motion\_control to play actions. The motion\_control and motion\_player components are identical to those on the real robot, allowing the system to call all interfaces of the motion control and action playback modules.

#### 8.2 Prerequisites <a href="#web-13-8-2-prerequisites" id="web-13-8-2-prerequisites"></a>

This simulation system is provided as a container image, containing executable files for each component, action resource files, and calling scripts. To use this simulation system, the following conditions must be met:

1. An x86\_64 architecture Linux system with Docker installed.
2. An X11 desktop system.
   * You can check this by running `echo $XDG_SESSION_TYPE`, and the expected output should be `x11`.

#### 8.3 Usage Tutorial <a href="#web-13-8-3-usage-tutorial" id="web-13-8-3-usage-tutorial"></a>

**8.3.1 Pulling the Image**

1. Log in to the read-only account of the image repository

bash

```
docker login tongyong-public-cn-shanghai.cr.volces.com -u crrobot@aima-public-reader -p Aima123456
```

2. Pull the corresponding image

bash

```
docker pull tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
```

**8.3.2 Starting the Image**

1.  Allow Docker to access the display, which is used to configure the access control list for the X Window System. Running `xhost +` will allow all hosts to connect to the current user's X server, effectively disabling access control for the X server and allowing any user to access and operate it.bash

    ```
    xhost +
    ```
2.  Start the Docker containerbash

    ```
    docker run -it \
    --name=a2-lite-sim \
    --privileged \
    --net=host \
    --ipc=host \
    --pid=host \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v /run/dbus/system_bus_socket:/run/dbus/system_bus_socket:ro \
    -d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
    ```

    \
    If you find that the simulation interface runs sluggishly on a machine with an NVIDIA graphics card after starting the container with the above command, try using the following command to start the container:bash

    ```
    docker run -it \
            --name=a2-lite-sim \
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
            -d tongyong-public-cn-shanghai.cr.volces.com/aima-public/a2-lite-simulator:v2.0
    ```
3.  Enter the containerbash

    ```
    docker start a2-lite-sim && docker exec -it a2-lite-sim /bin/bash
    ```

**8.3.3 Starting the Simulation, Motion Control, and Action Playback Modules**

1.  After entering the image, run the following command to start the simulationbash

    ```
    docker start a2-lite-sim && docker exec -it a2-lite-sim /bin/bash

    cd /home/agi/a2_simulation/mujoco_sim/bin
    ./start_a2_lite.sh
    ```
2.  In a new window, connect to the container and start the motion control programbash

    ```
    docker start a2-lite-sim && docker exec -it a2-lite-sim /bin/bash

    cd /home/agi/a2_simulation/motion_control_lite_2.0.10/scripts/motion_control
    ./start_motion_control.sh
    ```
3.  In another new window, connect to the container and start the action playback programbash

    ```
    docker start a2-lite-sim && docker exec -it a2-lite-sim /bin/bash

    cd /home/agi/a2_simulation/motion_player_lite_2.0.10/scripts/motion_player
    ./start_motion_player.sh
    ```

**8.3.4 Controlling Robot Walking**

Here, we will use robot walking as an example to explain the basic logic of calling a motion control interface. For other interfaces, refer to the motion control interface documentation and example scripts.

1.  Open a new window, enter the container, and switch the motion control Action to the joint standing mode (RL\_JOINT\_DEFAULT)bash

    ```
    cd /home/agi/a2_simulation/tools-lite/motion_control
    ./SetAction.py # Select the number corresponding to RL_JOINT_DEFAULT
    ```
2.  Click the Load-Key button in the mujoco\_sim interface to stabilize the robot<br>

    <figure><img src="../../.gitbook/assets/unknown (379).webp" alt="Official AgiBot illustration"><figcaption><p>Official AgiBot illustration</p></figcaption></figure>
3.  Continue to switch the motion control Action to the enhanced walking mode (RL\_LOCOMOTION\_DEFAULT)bash

    ```
    cd /home/agi/a2_simulation/tools-lite/motion_control
    ./SetAction.py # Select the number corresponding to RL_LOCOMOTION_DEFAULT
    ```
4.  Call the walking example scriptbash

    ```
    source /home/agi/a2_simulation/prebuilt/ros2_plugin_proto_x86_64/share/ros2_plugin_proto/local_setup.bash
    ./walk.py
    ```

**8.3.5 Controlling Robot to Perform Actions**

1.  Switch the motion control state to the enhanced walking upper limb servo mode (RL\_LOCOMOTION\_ARM\_EXT\_JOINT\_SERVO)bash

    ```
    cd /home/agi/a2_simulation/tools-lite/motion_control
    ./SetAction.py # Select the number corresponding to RL_LOCOMOTION_ARM_EXT_JOINT_SERVO
    ```
2.  Call the SendMotionCommand interface to perform the actionbash

    ```
    cd /home/agi/a2_simulation/tools-lite/motion_player
    ./send_motion_id.sh /agibot/data/resources/default/motion/motion_player/default/wave-both-hands/wave-both-hands
    ```

### 9. Troubleshooting Interface Call Issues <a href="#troubleshooting-interface-calls" id="troubleshooting-interface-calls"></a>

#### 9.1 Troubleshooting Approach <a href="#web-14-9-1-troubleshooting-approach" id="web-14-9-1-troubleshooting-approach"></a>

The general troubleshooting methods for HTTP JSON RPC and ROS2 Topic are different, but there are also some common troubleshooting methods for on-board issues.

**9.1.1 HTTP JSON RPC**

1. Check if the corresponding IP is the correct x86 industrial PC IP and if it can be pinged.
2. Check if the HTTP URL is correct; you can refer to the example scripts or interface documentation.
3. Check if the corresponding service is started on the port. After SSHing into the x86, you can use the command `lsof -i:xxxx` in the terminal to check if the service is running on the port.
4. If you get a "Connection Refused" error, it means the IP might not be reachable or the service on the port has not started.
5. If you get an "HTTP deserialize failed" error, it means the JSON body fields might be incorrectly filled. You can refer to the example scripts or interface documentation for comparison.

**9.1.2 ROS2 Topic**

1. Check if the on-board ROS2 DDS configuration includes the IP of the network card being used. Ensure that both privileged and non-privileged configurations correctly add the network card IP. After adding, a full reboot is required.
2. Check if you are using the ROS2 Humble with Fastdds version.
3. Check if the local environment variables `ROS_DOMAIN_ID=232` and `ROS_LOCALHOST_ONLY=0` are loaded. The exported environment variables only take effect in the current terminal. A new terminal will need to re-export these variables. You can use the command `env | grep ROS` to view the relevant environment variable settings in the current terminal.
4.  Ensure that the QoS of the topic is consistent with the default QoS on the board.yaml

    ```
      history: keep_last
      depth: 10
      reliability: best_effort
    ```
5. After SSHing into the x86 industrial PC, execute `aima em load-env` (to load the ROS2 environment variables) and then use the `ros2 topic` command to check if the related topics are being sent or received by any modules.

**9.1.3 Common Troubleshooting Methods**

1. Use AimMaster to check if the robot has any health alerts. In the case of a robot fault, it may affect some interface calls. For example, if there is a joint fault, the motion control interface may not function properly.
2. If not connected to AimMaster, you can log in to the robot's x86 industrial PC and execute the `aima doctor` command to quickly view health alert information.

#### 9.2 Common Interface Questions <a href="#web-14-9-2-common-interface-questions" id="web-14-9-2-common-interface-questions"></a>

1.  Why does calling the upper limb action interface or neck interface result in no response or severe shaking?

    1. First, confirm that the robot is in the corresponding Action mode, which should end with JOINT\_SERVO.
    2. In the JOINT\_SERVO mode, the control of the upper limbs and neck is preempted by the motion playback module. You need to call the DisableMotionPlayer interface to disable the control of the motion playback module before you can normally call the upper limb or neck control interfaces.

    yaml

    ```
    curl -i \
        -H 'content-type:application/json' \
        -H 'timeout: 1000' \
        -X POST http://127.0.0.1:56444/rpc/aimdk.protocol.MotionCommandService/DisableMotionPlayer \
        -d '{}'
    ```
2. Why does calling any motion playback only result in the right hand lifting action?
   1. This is the default action of the motion playback module. When the `motion_id` parameter is incorrect, it will default to this action.
   2.  A correct motion path should find the corresponding .db file and pass the complete path without the .db suffix, for example:bash

       ```
       /agibot/data/resources/default/motion/motion_player/default/wave-both-hands/wave-both-hands
       ```

#### 9.3 Feedback Channels <a href="#web-14-9-3-feedback-channels" id="web-14-9-3-feedback-channels"></a>

If you encounter bugs in secondary development interfaces, you can provide feedback through the following channels:

[https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k](https://agirobot.feishu.cn/share/base/form/shrcndpGW6r8FIdt2mT3uX02z6k)

Note

1. This channel is only for answering questions or reporting bugs related to secondary development interfaces. For robot body faults or after-sales maintenance, please contact the delivery, operation, and after-sales teams directly. Unrelated issues will not be responded to.
2. Please describe the problem in detail in the form, preferably providing reproducible steps. Clear and detailed problem descriptions will be given priority, while vague and general descriptions will have lower priority and may be ignored.
3. Please fill out all information carefully. Inconsistent or casually filled forms will be ignored.
4. Each ticket should focus on a single or similar issue. Do not mix multiple issues in one ticket, as this will significantly delay the processing time.

***

#### title: 2. Frequently Asked Questions hideH1: true <a href="#web-15-title-2-frequently-asked-questions-hideh1-true" id="web-15-title-2-frequently-asked-questions-hideh1-true"></a>

### 2. Frequently Asked Questions <a href="#frequently-asked-questions" id="frequently-asked-questions"></a>

#### 2.1 What is the onboard software version? <a href="#web-15-2-1-what-is-the-onboard-software-version" id="web-15-2-1-what-is-the-onboard-software-version"></a>

The A2 robot comes with a series of onboard software, which will be upgraded along with the OTA (Over-The-Air) updates.

Generally, the software version (current application version) is printed when you ssh into the robot, and it can also be viewed through the AimMaster software. The version number is usually in the format of 1.2.x.

#### 2.2 What are P1 and T3? <a href="#web-15-2-2-what-are-p1-and-t3" id="web-15-2-2-what-are-p1-and-t3"></a>

P1 and T3 are the hardware models of the A2 robot. The main difference between these hardware models lies in the configuration of the industrial PC, including network card configurations, but the system performance and upper-layer interfaces are generally unified.

After logging into the x86 industrial PC via ssh, you can check the /etc/bsp\_version file to confirm the version. If this file exists, it is P1; if it does not exist, it is T3.

#### 2.3 How to handle the over-speed anomaly reported by the arm joint motor? <a href="#web-15-2-3-how-to-handle-the-over-speed-anomaly-reported-by-the-arm-joint-motor" id="web-15-2-3-how-to-handle-the-over-speed-anomaly-reported-by-the-arm-joint-motor"></a>

<figure><img src="../../.gitbook/assets/unknown (380).webp" alt="2.3 How to handle the over-speed anomaly reported by the arm joint motor?"><figcaption><p>2.3 How to handle the over-speed anomaly reported by the arm joint motor?</p></figcaption></figure>

Reason: When calling the arm interface, there is a step change between the input position and the current position, leading to an over-speed condition that triggers current limiting. At this point, the embedded system will disable the joint for protection and report the alarm.

Solution: In most cases, restarting the robot will resolve the issue. To avoid this problem, when calling the arm ROS2 Topic interface, filter and smooth the joint positions before passing them in, ensuring that the input values do not have a large step change compared to the current state.

#### 2.4 Is it possible to develop your own motion control program? <a href="#web-15-2-4-is-it-possible-to-develop-your-own-motion-control-program" id="web-15-2-4-is-it-possible-to-develop-your-own-motion-control-program"></a>

By default, the low-level control interfaces for the lower limb joint motors are not open, and they can only be controlled through high-level speed commands. If you need to develop your own motion control algorithms to replace the ones provided by Agibot, please contact the sales or project manager to obtain the motion control development and deployment guide.
