---
description: >-
  Match the complete joint model code before using specifications. Standard and
  torque-series values must not be combined.
---

# RealMan WHJ Series Joint Module User Manual

{% hint style="info" %}
[**View WHJ10-80 S/I on OpenELAB**](https://openelab.io/products/realman-whj10-80)

**Model:** WHJ10-80 S/I · **SKU:** `WHJ10-80-S / WHJ10-80-I`

[**View WHJ30-80 S/I on OpenELAB**](https://openelab.io/products/realman-whj30-80)

**Model:** WHJ30-80 S/I · **SKU:** `WHJ30-80-S / WHJ30-80-I`

[**View WHJ60-100 S/I on OpenELAB**](https://openelab.io/products/realman-whj60-100)

**Model:** WHJ60-100 S/I · **SKU:** `WHI60-100-S / WHI60-100-I`
{% endhint %}

## Relationship to the RealMan series

This existing joint-module reference remains separate from complete-arm guides. Confirm the full module code, S/I option and torque-series designation; the ten supplied robot/arm/gripper files do not replace its joint electrical/protocol sources. The WHJ60-100 storefront currently uses `WHI60-100-S/I` SKU strings; verify the physical module code when reconciling inventory. All existing joint figures and technical content are retained below.

[RealMan series index](./) · [RMG22-65 guide](realman-rmg22-65-gripper.md) · [Complete-arm commissioning](realman-arm-commissioning-and-sdk.md)

## Preserved joint-module manual

### RealMan WHJ10-80 Harmonic Joint Module with S and I Version Options

{% embed url="https://openelab.io/products/realman-whj10-80" %}

### RealMan WHJ30-80 Harmonic Joint Module, 30 N·m Rated Torque

{% embed url="https://openelab.io/products/realman-whj30-80" %}

### RealMan WHJ60-100 High-Torque Harmonic Joint Module, 60 N·m Rated Torque

{% embed url="https://openelab.io/products/realman-whj60-100" %}

### Joint Overview

This section introduces the WHJ module architecture, integrated components, and intended applications.

WHJ series joint modules combine a compact mechanical design with integrated motion-control functions.

Each module incorporates the servo drive, motor-side and output-side absolute encoders, frameless torque motor, brake, and precision harmonic reducer.

This integration reduces component selection, procurement, assembly, and testing effort, allowing developers to focus on the final application.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/introduction_of_whj_series/image1.png)

All key components of the WHJ series joints, including the drive servo, motor and harmonic reducer, are independently developed and manufactured by WHJ.

The in-house harmonic reducer is smaller and lighter than comparable conventional reducers.

It weighs approximately 30%–50% less than conventional reducers with comparable specifications while delivering up to twice the torque of similarly sized products.

WHJ joint modules are available in multiple models, including WHJ03-100, WHJ10-80, WHJ30-80, WHJ60-100, and WHJ120-100. Across the series, maximum output torque reaches 360 N·m, while the smallest module diameter is 33 mm.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/introduction_of_whj_series/image.png)

Select a WHJ model according to the application requirements. The model code identifies the relevant configuration options, as explained below:

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/introduction_of_whj_series/jointModelDescription.png)

### Electrical Connections and Wiring

Review the power limits, interfaces, wiring, and battery requirements before connecting or energizing a joint module.

**Joint Input Power Instructions**

**Power Voltage and Rated Power**

The power supply uses 24VDC (the factory-set minimum allowable bus voltage is 20V, and the recommended maximum bus voltage is 30V).

The driver will trigger an over-voltage fault when it detects a voltage exceeding 35V, and an under-voltage alarm when it detects a voltage below 20V.

| Model     | Voltage | Power |
| --------- | ------- | ----- |
| WHJ10-80  | 24V     | 63W   |
| WHJ30-80  | 24V     | 137W  |
| WHJ60-100 | 24V     | 258W  |

**Limit Values of Joint Voltage**

The maximum voltage that the joint power interface can withstand is DC38V. An input voltage exceeding 38V may easily lead to driver failure.

When using a switch to control the joint power supply, there may be an overvoltage impact (＞38V) at the moment of power-on.

For this power supply method, a polarized capacitor (reference specification: 820uF, 50V) should be connected in parallel after the switch and before the joint power input to suppress the overvoltage phenomenon at the moment of power-on.

When using a 24V switch-mode power supply, it is necessary to connect the protection device specified by RealMan to protect the power supply and absorb regenerative back EMF.

When a battery powers the joint, regenerative back EMF charges the battery directly, so no additional suppression is normally required.

If the battery has limited capacity, connect the protection device specified by RealMan to improve system reliability.

**Joint Positive Rotation Direction**

Facing the output end of the reducer, the positive rotation direction of the joint is counterclockwise. This direction cannot be modified.

The rotation direction of the joint is determined by the direction of the target command, which is issued by the controller end.

<div align="center"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image1.png" alt="Positive Rotation Direction"></div>

**Electrical Interface Instructions**

**CAN Communication Interface**

The terminal model is PH2.0-2A, as shown in the figure below:

<div align="center"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image2.png" alt="CAN Communication Interface"></div>

**Multi-turn Power Supply Battery Interface**

The terminal model is PH2.0-2A. The positive and negative poles of the interface are shown in the figure below (red for positive and black for negative):

<div align="center"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image3.png" alt="Multi-turn Power Supply Battery Interface"></div>

**24V Power Supply Interface**

The positive and negative poles of the power line interface are shown in the figure below (red for positive and black for negative):

<div align="center"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image4.png" alt="24V Power Supply Interface"></div>

![Specifications](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image5.png)

**Cable Connection between Multi-joint Modules**

**Power Wiring Method Instructions**

Chain topology connection; if the power of a single joint is large, it can also be connected directly.

![Chain Topology](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image6.png)

**CANFD Communication Wiring Diagram**

1. CANFD communication lines use twisted pair cables, with a data transmission rate of 5Mbps, and chain topology connection;
2. A 120Ω terminal resistor (very important) needs to be connected in parallel at the CAN interface of the controller end and the end servo;
3. Ensure that the CAN ID of each joint module is set uniquely.

![CANFD Communication Wiring Diagram](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image7.png)

**Length Instructions of CANFD Line and Power Line**

WHJ10:

![WHJ10](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image8.png)

WHJ30:

![WHJ30](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image9.png)

WHJ60:

![WHJ60](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image10.png) ![Power Line](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/electrical_description_of_joints/image11.png)

**Cable and Terminal Specifications**

|                                          | Number of Interfaces               | Joint Input End Wire Type | Joint Output End Wire Type | Wire Material              | Overcurrent (A)        |                         |                                      |                                      |                     |
| ---------------------------------------- | ---------------------------------- | ------------------------- | -------------------------- | -------------------------- | ---------------------- | ----------------------- | ------------------------------------ | ------------------------------------ | ------------------- |
| Terminal                                 | Wire Length (mm)                   | Terminal                  | Wire Length (mm)           | Cross-sectional Area (mm²) | AWG                    |                         |                                      |                                      |                     |
| Power                                    | WHJ60 Single Joint Power Interface | 2P\*2                     | XT30U-M                    | 140-150                    | XT30U-F                | 35-45                   | 0.75 (150 strands/0.08)              | Approximately 16-18 based on current | Rated 15/Maximum 30 |
| WHJ30 Single Joint Power Interface       | 2P\*2                              | XT30U-M                   | 110-120                    | XT30U-F                    | 40-50                  | 0.75 (150 strands/0.08) | Approximately 16-18 based on current | Rated 15/Maximum 30                  |                     |
| WHJ10 Single Joint Power Interface       | 2P\*2                              | XT30U-M                   | 110-120                    | XT30U-F                    | 45-55                  | 0.75 (150 strands/0.08) | Approximately 16-18 based on current | Rated 15/Maximum 30                  |                     |
| Signal CAN                               | WHJ60 Single Joint Power Interface | 2P\*2                     | BX-PH2.0-2PJK Housing      | 155-165                    | A2001HM-2P Air Docking | 50-60                   | 0.5 (30 strands/0.08)                | 26                                   | Rated 3/Maximum 6   |
| Press-fit Terminal: A2001-TP/BX-PH2.0-DZ | Press-fit Terminal: A2001M-TP      |                           |                            |                            |                        |                         |                                      |                                      |                     |
| WHJ30 Single Joint Power Interface       | 2P\*2                              | BX-PH2.0-2PJK Housing     | 155-165                    | A2001HM-2P Air Docking     | 55-65                  | 0.5 (30 strands/0.08)   | 26                                   | Rated 3/Maximum 6                    |                     |
| Press-fit Terminal: A2001-TP/BX-PH2.0-DZ | Press-fit Terminal: A2001M-TP      |                           |                            |                            |                        |                         |                                      |                                      |                     |
| WHJ10 Single Joint Power Interface       | 2P\*2                              | BX-PH2.0-2PJK Housing     | 125-135                    | A2001HM-2P Air Docking     | 40-50                  | 0.5 (30 strands/0.08)   | 26                                   | Rated 3/Maximum 6                    |                     |
| Press-fit Terminal: A2001-TP/BX-PH2.0-DZ | Press-fit Terminal: A2001M-TP      |                           |                            |                            |                        |                         |                                      |                                      |                     |

Due to different product configurations and different joint positions, the length requirements for CAN lines and power lines vary. Both CAN lines and power lines are of default length.

If there are special length requirements, please contact us to make notes on the product order.

**Multi-turn Power Supply Battery Instructions**

**Battery Function**

To power the multi-turn encoder and save the multi-turn count of the joint, preventing the loss of the equipment's zero position.

**Battery-related Error Handling**

Reset the zero position, and a soft reset can be performed.

### Single-Joint Host Computer

The following workflow covers driver setup, device connection, monitoring, motion control, firmware updates, and CAN diagnostics.

**Environment and Driver Setup**

**Hardware Environment Configuration**

**Wiring Instructions**

This joint features three external terminal connectors and one electromagnetic lock connector.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/environment_preparation/image.png)

The hardware description of the joint is shown in the table below.

| No. | Name                                     |
| --- | ---------------------------------------- |
| 1   | 24V DC Power Input                       |
| 2   | CAN0 Communication Interface             |
| 3   | CAN1 Communication Interface             |
| 4   | Electromagnetic Lock (Hard Limit Module) |

**Power Input**

The red and black wire harnesses are for power input, with the red being the positive terminal and the black being the ground (GND). The external power supply for the joint is 24V DC.

**Joint Communication**

There are two pairs of communication interface terminals, designated as CAN0 and CAN1. The blue wire harness is for CANH, and the white wire harness is for CANL.

**CAN Communication Device Configuration**

1.  The ZLG USBCANFD-100U-mini CAN-to-USB tool is used (optional), as shown in the figure below.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/environment_preparation/image-31.png)
2. Click [Driver Tool](https://github.com/RealManRobot/Developer_Center/tree/main/joints/Single_Joint_Host/drivertools) to download the CAN to USB driver tool. ([Alternative Link](https://gitee.com/RealManRobot/Developer_Center/tree/main/joints/Single_Joint_Host/drivertools))
3. Extract the driver tool package to your local machine, and run the installation by double-clicking `USBCANFD_AllInOne_x86_x64_1.0.0.2.exe` to complete the installation of the driver tool.
4. Confirm whether the test computer has the VC++ environment installed. If not, please contact technical support to obtain the driver package and install it; otherwise, communication will not be successful.

WARNING

* To meet the needs of interface card integration, Realman offers a unified programming interface that supports both CAN and CANFD.
* In addition to a simple and easy-to-use interface, example routines and documentation for interface usage are provided.
* The following Microsoft Visual C++ Runtime Library versions are required (and must be present): 2005, 2008, 2010, 2012, 2013.
* Before initiating motion, ensure that the joint is securely fixed.
* If you encounter issues with opening the device, please check whether the operating environment on your computer is missing any necessary components based on the software structure provided.

**Introduction to the Single-Joint Host Computer**

1. Click [Single - Joint Host Computer](https://github.com/RealManRobot/Developer_Center/tree/main/joints/Single_Joint_Host/singlejointhostcomputersoftware) to download the single - joint host computer software.([Alternative Link](https://gitee.com/RealManRobot/Developer_Center/tree/main/joints/Single_Joint_Host/singlejointhostcomputersoftware))
2. Extract the software package to your local machine, and run the single - joint host computer tool by double-clicking `WHJoint.exe`.
3.  The Single-Joint Host Computer is designed for joint configuration and monitoring, enabling users to adjust joint parameters, query joint driver information, configure and upgrade firmware, and observe joint data in real-time.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/environment_preparation/image-1.png)<br>

**Function Area Names**:

| No. | Name                   |
| --- | ---------------------- |
| 1   | Main page Navigation   |
| 2   | Waveform Navigation    |
| 3   | Information Navigation |
| 4   | CAN Pro Navigation     |
| 5   | Function Menu          |

Below is a detailed explanation of each area/button in the order presented in the table above:

* **Main page Navigation**: Internal functional categories, including Devices, Real-time data, Motion control, and Real-time waveform classes.
* **Waveform Navigation**: Generates waveforms for current, speed, and position for easy viewing.
* **Information Navigation**: Internal functional categories for querying and setting driver information, and firmware upgrade functions.
* **CAN Pro Navigation**: Real-time display of CAN command transmission and reception.
*   **Function Menu**: Supports switching between Chinese and English. As shown in the figure below, select `Language` > `Chinese/English` from the drop-down menu to switch to a Chinese/English interface.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/environment_preparation/image-2.png)

**Connection, Monitoring, and Motion Control**

**Device Connection Class**

Device connection can only be established when the hardware status is normal.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-2.png)<br>

The functions of the device selection buttons are shown in the table below.

| No. | Name                    |
| --- | ----------------------- |
| 1   | CAN Connection          |
| 2   | Joint Device Scanning   |
| 3   | Joint Basic Information |

**CAN Connection**

* **Connection**:
  1. When the hardware device connection status is normal, click the function button `CAN Connection` to pop up the parameter settings page.
  2.  Supports setting `Protocol`, `Channel`, `Arbitration`, and `Data`.

      Different protocol configurations are as follows:

      | Protocol                 | Channel | Arbitration | Data                                      |
      | ------------------------ | ------- | ----------- | ----------------------------------------- |
      | CANFD\_ZLG/CANFD\_HK     | 0       | 1Mbps       | 5Mbps                                     |
      | CANOPEN\_ZLG/CANOPEN\_HK | 0       | 1Mbps       | Default 1Mbps, adjustable to 500HZ, 250HZ |

      The corresponding protocol descriptions are as follows. Different protocols correspond to different joint versions. For specific version details, please contact our technical support.

      | Protocol     | Description                                |
      | ------------ | ------------------------------------------ |
      | CANFD\_ZLG   | Compatible with ZLG brand CANFD protocol   |
      | CANOPEN\_ZLG | Compatible with ZLG brand CANOPEN protocol |
      | CANFD\_HK    | Compatible with HK brand CANFD protocol    |
      | CANOPEN\_HK  | Compatible with HK brand CANOPEN protocol  |
  3. After completing the CAN card communication configuration, click `Confirm` to connect the CAN card device. When the host prompts "Connection Successful," the function button changes to `Disconnection`.
*   **Disconnection**: Click the function button `Disconnection`. The host will prompt "Device Disconnected," and the function button will revert to `CAN Connection`.

    | Connect                                                                                                                                                                                       | Disconnection                                                                                                                                                                                 |
    | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-3.png) | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-4.png) |

**Scan**

After a successful device connection, click `Scan` to begin scanning joints. The system scans connected joints in real-time. Once the scan is complete, joint device information will be displayed in the device dialog box.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-5.png)

The device information display is explained as follows:

| No. | Name                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | Connected Device Serial Number | When multiple joints are connected, the serial number increments based on the number of joints.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 2   | Joint ID                       | Displays the set Joint ID number based on real-time scanning.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 3   | Enable Status                  | <p>Shows the current enable status of the joint, with different colors indicating different statuses based on real-time scanning.<br><strong>Disabled</strong>:<img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-27.png" alt="Official RealMan WHJ documentation image"><br><strong>Enabled</strong>:<img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-28.png" alt="Official RealMan WHJ documentation image"></p> |
| 4   | Joint Model                    | Displays the current joint model based on real-time scanning.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| 5   | Firmware Version               | Displays the current joint firmware version based on real-time scanning.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 6   | Globally Unique ID             | Displays the unique ID of the current joint based on real-time scanning. This ID cannot be modified after factory settings.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

**Real-time Display**

When the host connection is normal, the basic information of the currently selected joint can be viewed.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-6.png)<br>

**Explanation of Data Display Areas:**

| No. | Name                                  |
| --- | ------------------------------------- |
| 1   | Current Joint Angle Position          |
| 2   | Enable/Disable Real-time Data Display |
| 3   | Current Joint Internal Temperature    |
| 4   | Current Joint Speed                   |
| 5   | Current Joint Detection Voltage       |
| 6   | Current Joint Power Loss Current      |
| 7   | Current Joint MOS State               |
| 8   | Current Joint Tuning State            |
| 9   | Current Joint Error Codes Display     |
| 10  | Clear Current Error                   |

**Enable Real-time Data**

Real-time data is disabled by default. To view joint real-time information, click `Open` to start uploading current joint data information, as shown in the figure below.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-7.png) ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-8.png)

**Clear Errors**

When the joint malfunctions, the error code displays a description of the current fault, and the joint status bar will disable the enable signal simultaneously.

1. Identify and resolve the cause of the joint error.
2. Click `Clear error` to remove the error information.
3.  Click `Enabled` to restore the joint to an enabled state.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-9.png)

**Motion Control**

Joint control operations allow for joint state control and related motion settings.

**Joint State Settings**

The joint state settings function buttons enable corresponding joint operations.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-10.png)<br>

**Function descriptions:**

| No. | Name                    | Description                                                                                                                                                                                      |
| --- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1   | Enabled Joint           | After connecting the device, the joint is in an enabled state by default, allowing motion control. When disabled, the host cannot control joint motion.                                          |
| 2   | Disable Joint           | When the device is enabled, it can only be controlled via software. To manually control the joint, perform a disable operation first. In the disabled state, the device status bar appears gray. |
| 3   | Set Joint Zero Position | Click the `Zero Pos` button to set the current joint position as the zero position (0 degrees). Settings must be saved to take effect.                                                           |
| 4   | Save Parameter Settings | All joint parameters must be saved by clicking the `Save` button. Failure to save settings will result in the joint reverting to previous parameters after power cycling.                        |

**Motion Control**

Multiple modes for joint motion control are supported, including joint limit settings.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-11.png)<br>

**Function area descriptions:**

| No. | Name                     |
| --- | ------------------------ |
| 1   | Motion Mode              |
| 2   | Servo Mode               |
| 3   | Waveform Control         |
| 4   | Start/Stop/Zero Settings |
| 5   | Manual Control           |
| 6   | Origin/Stop              |

**Function area/button descriptions:**

*   **Motion Mode:** Motion modes include square wave, sinusoid, and manual modes, which can be set according to requirements.

    | Waveform Mode Options                                                                                                                                                                          | Square Wave                                                                                                                                                                                    | sinusoid                                                                                                                                                                                       |
    | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-12.png) | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-29.png) | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-30.png) |
*   **Servo Mode:** Servo modes include Target current, Target speed, Target position, and Test Mode, which can be set according to requirements.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-13.png)<br>

    WARNING

    Test mode is only for no-load testing (using with a load poses a risk of joint damage due to inertia at limit positions). In this mode, only manual motion mode is supported with adjustable speed.

    It is recommended to set joint limits to maximum (-214748～214748) to allow joint movement between the maximum and minimum position limits.
*   **Waveform Control:** Configure waveform frequency and amplitude to control joint speed and angle. Parameters such as frequency, amplitude, and bias can be set.

    The following example uses position servo with sine wave motion mode:

    * Setting frequency to 0.1HZ results in a 10-second sine wave period.
    * Amplitude set to 90 corresponds to the sine wave amplitude.
    *   Bias set to 100 means the sine wave equilibrium position deviates from y=0° by 100°.

        ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-14.png)<br>
* **Manual Control:** Manual control allows individual joint operation based on servo mode settings.
  * Adjust parameters via mouse in manual control.
  * Switch to manual mode and perform calibration first. Motion automatically adjusts to a controllable range.
  * In target position mode, calibration sets the adjustable range to ±100°.
  * In target speed or target current modes, it is recommended to manually adjust the slider to zero speed under normal operating conditions.
  *   In case of abnormal or dangerous situations, click the `Stop` button to halt joint motion.

      ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-15.png)<br>

**Limit Settings**

**Limit Settings:** Set the maximum and minimum joint angle limits. After configuration, click `Save` to store settings in the joint and restart for activation. The minimum limit can be set to -214748°, and the maximum limit to 214748°.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-16.png)<br>

**Real-time Waveform**

Joint data is displayed via waveforms, including Real Current, Target Current, Real Speed, Target Speed, Real Position, Target Position, and supports data export.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-17.png)<br>

**Function Area Descriptions:**

| No. | Name                                |
| --- | ----------------------------------- |
| 1   | Current Waveform Display Selection  |
| 2   | Speed Waveform Display Selection    |
| 3   | Position Waveform Display Selection |
| 4   | Independent X-axis Zoom             |
| 5   | Independent Y-axis Zoom             |
| 6   | Scroll Display                      |
| 7   | Waveform Origin                     |
| 8   | Start/Pause Waveform                |
| 9   | Clear Waveform                      |
| 10  | Data Export                         |
| 11  | Waveform Display                    |

**Function Area/Button Descriptions:**

*   **Waveform Display Options:** To view current, speed, or position waveforms, select the corresponding option and click `Start`. The waveform will be displayed in the graph.

    ![image-18.png](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-18.png)\
    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-19.png)<br>
* **Function Buttons:** Control and view waveforms as needed.
  * **X-axis Zoom:** When selected, adjust the mouse scroll wheel to modify the X-axis scale of the waveform. Unchecking disables this function.
  * **Y-axis Zoom:** When selected, adjust the mouse scroll wheel to modify the Y-axis scale of the waveform. Unchecking disables this function.
  * **Scroll:** When selected, the waveform scrolls in real-time. Unchecking fixes the waveform on the page, allowing axis adjustment for data viewing.
  * **Origin:** When scroll display is stopped, click the `Origin` button to reset the waveform display to the X-axis origin.
  *   **Start:** Click `Start` to display the selected waveform. The button changes to `Pause`. Click `Pause` to stop waveform display.

      | Start Button                                                                                                                                                                                   | Pause Button                                                                                                                                                                                   |
      | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
      | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-22.png) | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-23.png) |
  * **Clear:** Click the `Clear` button to remove the waveform displayed on the host.
  * **Data Export:**
    * Export Types: Export image and Export doc.
    * Export Targets: All waveform, Current wave, Pos wave, Speed wave, Torque wave.
    *   Image export allows selection of file storage location and name, with default png format as shown below.

        ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-20.png)<br>
    *   Document export has fixed file names and paths. A prompt "File Write Successful" appears upon export. Files are in txt format and stored in the host's date file directory as shown below.

        ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/main_page_navigation/image-21.png)<br>

**Waveform Monitoring**

You can display different types of waveforms separately. Currently, it supports current, speed, and position waveforms. Torque waveform output is not supported yet.

You can view the coordinates of a point in real-time by hovering the mouse over the curve.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/waveform_navigation/image-24.png)

**Waveform Display**

After starting the waveform display in the real-time page, the waveform is displayed normally in this navigation, as shown in the figure below.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/waveform_navigation/image-26.png)<br>

**Function Buttons**

**Page Function Buttons:** Waveform display options, origin, and clear.

*   **Waveform Display:** After starting the waveform display in the real-time page, the waveform is displayed normally after selecting the waveform type.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/waveform_navigation/image-25.png)
* **Origin:** When the waveform is not scrolling, switch to the waveform navigation and click the `Origin` button to reset the waveform display to start from the 0 position on the x-axis.
* **Clear:** Click the `Clear` button to clear the waveform displayed on the host.

**Device Information and Firmware Upgrade**

**Information navigation includes**: Driver information, firmware upgrade, as shown in the figure below.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-39.png)<br>

**Driver Information**

**Driver Information Display**

**Driver Information Display**: Driver model, Firmware version, Joint ID, Unique ID.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-32.png)<br>

**Function Buttons**

* **ID Setting**: Set the joint ID. After setting, click `Save` and restart the joint to activate. ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-33.png)<br>
* **Enable/Disable Terminal Resistance**: Set the terminal resistor for the CAN Module to Enable or Disable. ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-34.png)<br>

**Firmware Upgrades**

Upgrade the firmware version of the joint. A restart is required after upgrading for the changes to take effect.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-35.png)<br>

WARNING

CANOpen joints cannot be upgraded on this page. Please contact our technical support for assistance.

1. Enter the joint ID to be upgraded. ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-36.png)\
   <br>
2. Click `Select the File`, navigate to the firmware file path, choose the correct firmware file, and click `Open` to select the firmware file.\
   Firmware files have a .bin extension. ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-37.png)\
   <br>
3. Click `Start the Update` to begin the firmware upgrade. ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/information_navigation/image-38.png)<br>
4. After the upgrade is complete, restart the joint to activate the new firmware version.

**CAN Monitoring**

**CAN Real-Time Data**

You can monitor CAN command transmission in real-time to assist in troubleshooting.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/can_pro_navigation/image-40.png)

**Worked Examples**

**Export Target Speed Sine Wave**

**Preparation**

* Software: Download and install WHJoint on your computer.
* Hardware: CAN box, 24V power supply, joint.

**Connecting the Joint to the Software**

Reminder

Complete the hardware setup before connecting the software. Open WHJoint and connect the CAN box USB port to the computer, then connect the CAN side to the joint.

Install a 120 Ω termination resistor between CANH and CANL, and connect the joint to a 24 V switched-mode power supply.

1.  Enter the software configuration page and select the **Main page** tab.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image00.png)
2.  Click **CAN Connection** in the **Devices** module at the top left of the page.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image01.png)
3.  Open the **Set the Parameters** window, configure the relevant parameter information, and click **Confirm** after configuration.

    ![Image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image02.0.png)

    *   Select the **Protocols** column according to the CAN card you are using. Detailed descriptions are as follows:

        | Protocol     | Description                             |
        | ------------ | --------------------------------------- |
        | CANFD\_ZLG   | For Zhou Ligong brand CANFD protocol.   |
        | CANOPEN\_ZLG | For Zhou Ligong brand CANOPEN protocol. |
        | CANFD\_HK    | For Hongke brand CANFD protocol.        |
        | CANOPEN\_HK  | For Hongke brand CANOPEN protocol.      |
    * Select 0 for the **Channel** column.
    * Select 1Mbps for the **Arbitration** column (currently, the joint arbitration field only supports 1Mbps).
    * Select 5Mbps for the **Data** column (currently, the joint data field only supports 5Mbps).
4.  Confirm the connection status: Check the **Device** module. If **Disconnection** appears in the lower left instead of **CAN Connection**, it indicates that the CAN card is successfully connected to the computer.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image03.png)
5. Power on the joint.
6.  Click **Scan**, and the information of the connected joint will appear in the **Devices** module.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image04.png)

    The joint information in the figure is as follows:

    * **Num**: Device serial number. When multiple joints are connected, the serial number increases with the number of joints.
    * **ID**: Joint ID, showing the set joint ID number according to real-time scanning.
    * **State**: Enable status, showing the current joint enable status according to real-time scanning, and displayed in different colors based on the joint status.

    | Disabled                                                                                                                                                                            | Enabled                                                                                                                                                                             |
    | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image04.2.png) | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image04.1.png) |

    * **Joint**: Shows the current joint model according to real-time scanning.
    * **Firmware**: Shows the current joint firmware version model according to real-time scanning.
    * **Unique ID**: Shows the unique ID of the current joint according to real-time scanning, which cannot be changed after leaving the factory.

**Enable Real-time Data Button**

After the joint is successfully connected, you need to turn on the **Real-time Data** button to view the real-time data information of the joint.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image06.png) ![Image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image07.png)

| Serial Number | Name                                                             |
| ------------- | ---------------------------------------------------------------- |
| 1             | Current angular position of the joint.                           |
| 2             | Enable/disable real-time data display of the joint.              |
| 3             | Current internal temperature of the joint (must not exceed 90℃). |
| 4             | Current speed of the joint.                                      |
| 5             | Current detected voltage of the joint.                           |
| 6             | Current loss current of the joint.                               |
| 7             | Current MOS tube status of the joint.                            |
| 8             | Current setting and calibration status of the joint.             |
| 9             | Current error status display of the joint.                       |
| 10            | Clear the current error status.                                  |

**Configure Motion Information**

Note

Before sine wave and square wave motion, be sure to set the limits, otherwise the joint target position over-limit alarm will occur.

1.  **Limit Setting**: In the **Motion Control** module, click **Limit Setting** and configure the limit parameter information.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image09.png)

    * Configure **Minimum Limit** and **Maximum Limit**: ±360 is for reference only, and should be set according to the actual application scenario of the joint. The minimum limit can be set to -214748°, and the maximum limit can be set to 214748°.
    * After configuration, click **Save**.
2.  **Motion Control**: In the **Motion Control** module, click **Control** and configure the motion parameter information.

    ![Image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image011.png)

    * **Motion Mode**: Set to sine wave.
    * **Servo Mode**: Configure as needed, taking target speed as an example.
    * **Wave Control**: The joint speed, angle size, etc., can be controlled by configuring parameters such as frequency, amplitude, and offset. **Configuration example with speed servo and sine wave motion mode**:
      * Set the frequency to 0.2Hz, so the period of one sine wave motion is 20S.
      * Set the amplitude to 20, corresponding to the sine wave amplitude.
      * Set the offset to 100, so the equilibrium position angle of the sine wave deviates from y=0° by 100°.
      * After setting, click **Start**, and the joint will start rotating back and forth; click **Stop** to stop the joint.

**View and Export Waveforms**

1.  After configuring according to the above operations, you can view the corresponding waveform graph.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image015.png)

    | Serial Number | Name                                     |
    | ------------- | ---------------------------------------- |
    | 1             | Current waveform display selection box.  |
    | 2             | Speed waveform display selection box.    |
    | 3             | Position waveform display selection box. |
    | 4             | X-axis adjustment alone.                 |
    | 5             | Y-axis adjustment alone.                 |
    | 6             | Scroll display.                          |
    | 7             | Waveform origin.                         |
    | 8             | Waveform start/pause.                    |
    | 9             | Clear waveform.                          |
    | 10            | Data export.                             |
    | 11            | Waveform display.                        |
2.  When you need to view the relevant speed waveform, check the corresponding option and click **Start**, and the waveform will be displayed in the frame.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image016.png)
3. In the information box of the graph, the X-axis is the number of current points, and Y is the target value. Hover the mouse over the waveform to display the fuzzy coordinates of the current point.
4.  Data export: Click the export button at the bottom right of the page, and select the **Export type** and **Target** as needed.

    * Document export: The file name and file address cannot be selected. A prompt **File written successfully** will appear when exporting. The default file format is fixed as txt, and the file path is in the data folder of the upper computer.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image017.png)

    * Image export: You can select the file storage address and file name, and the default image format is png.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image018.png)

**Update the Firmware**

**Preparation**

* Software: Download and install WHJoint on your computer.
* Hardware: CAN box, 24V power supply, joint.

**Connecting the Joint to the Software**

Reminder

Complete the hardware setup before connecting the software. Open WHJoint and connect the CAN box USB port to the computer, then connect the CAN side to the joint.

Install a 120 Ω termination resistor between CANH and CANL, and connect the joint to a 24 V switched-mode power supply.

1.  Enter the software configuration page and select the **Main page** tab.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image00.png)
2.  Click **CAN Connection** in the **Devices** module at the top left of the page.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image01.png)
3.  Open the **Set the Parameters** window, configure the relevant parameter information, and click **Confirm** after configuration.

    ![Image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image02.0.png)

    *   Select the **Protocols** column according to the CAN card you are using. Detailed descriptions are as follows:

        | Protocol     | Description                             |
        | ------------ | --------------------------------------- |
        | CANFD\_ZLG   | For Zhou Ligong brand CANFD protocol.   |
        | CANOPEN\_ZLG | For Zhou Ligong brand CANOPEN protocol. |
        | CANFD\_HK    | For Hongke brand CANFD protocol.        |
        | CANOPEN\_HK  | For Hongke brand CANOPEN protocol.      |
    * Select 0 for the **Channel** column.
    * Select 1Mbps for the **Arbitration** column (currently, the joint arbitration field only supports 1Mbps).
    * Select 5Mbps for the **Data** column (currently, the joint data field only supports 5Mbps).
4.  Confirm the connection status: Check the **Device** module. If **Disconnection** appears in the lower left instead of **CAN Connection**, it indicates that the CAN card is successfully connected to the computer.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image03.png)
5. Power on the joint.
6.  Click **Scan**, and the information of the connected joint will appear in the **Devices** module.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image04.png)

    The joint information in the figure is as follows:

    * **Num**: Device serial number. When multiple joints are connected, the serial number increases with the number of joints.
    * **ID**: Joint ID, showing the set joint ID number according to real-time scanning.
    * **State**: Enable status, showing the current joint enable status according to real-time scanning, and displayed in different colors based on the joint status.

    | Disabled                                                                                                                                                                            | Enabled                                                                                                                                                                             |
    | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
    | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image04.2.png) | ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image04.1.png) |

    * **Joint**: Shows the current joint model according to real-time scanning.
    * **Firmware**: Shows the current joint firmware version model according to real-time scanning.
    * **Unique ID**: Shows the unique ID of the current joint according to real-time scanning, which cannot be changed after leaving the factory.

**Update Joint Firmware**

1.  Enter the software configuration page and select the **Information** tab.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image7.png)
2.  Click the **Firmware Upgrades** button on the left to enter the **Firmware Upgrades** page.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image8.png)
3. Customize the **Joint ID** and **File Path** information as needed.

* Joint ID: Select the joint ID displayed after the joint is connected to the software.
* File Path: Select the target update file.

4.  Click **Start the update**.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image9.png)
5.  When the progress bar reaches 100%, the update is successful.

    ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/getting_started/single_joint_host/use_case/image10.png)

### Joint Specifications

The standard and torque-series models use separate official parameter tables. Confirm the exact model designation before applying any value.

High-load or high-speed operation can return regenerative energy to the DC bus. Use the power bleeding module described later when required by the selected joint and power supply.

**WHJ10 Standard Series**

**Model: WHJ10-M-D50-80-B**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj10/10B--2.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                   | Value                                                                                                                           |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Reduction ratio             | 80                                                                                                                              |
| Weight                      | 455 g                                                                                                                           |
| Diameter of reducer mm      | 50                                                                                                                              |
| Size (D × L mm)             | 50 \* 73                                                                                                                        |
| Rated torque N.m            | 10                                                                                                                              |
| Maximum torque density      | 67.4                                                                                                                            |
| Repeatability               | ±15 arc-seconds                                                                                                                 |
| Peak speed (RPM)            | 37.5 (24V) / 75 (48V)                                                                                                           |
| Moment of inertia (kg\*m^2) | 1.13\*10^-5                                                                                                                     |
| Hollow aperture             | 8 mm                                                                                                                            |
| Working temperature         | 0 to 50°C                                                                                                                       |
| Rated power                 | 63 W                                                                                                                            |
| Rated voltage               | 24 V / 48 V                                                                                                                     |
| Rated current               | 2.6 A (24 V) / 1.3 A (48 V)                                                                                                     |
| Type of brake               | Latch brake                                                                                                                     |
| Incremental encoder         | 16 bits                                                                                                                         |
| Absolute position encoder   | 18 bits                                                                                                                         |
| Communication interface     | CANFD                                                                                                                           |
| Examples of scenarios       | Lightweight robotic arm, surgical robot, neck joint and wrist joint of humanoid robot, Service robot, precision turntable, etc. |

**Detailed dimensions**

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj10/CleanShot%202024-08-21%20at%2018.04.30.png)

**Model: WHJ10-M-D50-80-N**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj10/10-2.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                   | Value                                                                                    |
| --------------------------- | ---------------------------------------------------------------------------------------- |
| Reduction ratio             | 80                                                                                       |
| Weight                      | 445 g                                                                                    |
| Diameter of reducer mm      | 50                                                                                       |
| Size (D × L mm)             | 50 \* 64                                                                                 |
| Rated torque N.m            | 10                                                                                       |
| Maximum torque density      | 75                                                                                       |
| Repeatability               | ±15 arc-seconds                                                                          |
| Peak speed (RPM)            | 37.5                                                                                     |
| Moment of inertia (kg\*m^2) | 1.09\*10^-5                                                                              |
| Hollow aperture             | 8 mm                                                                                     |
| Working temperature         | 0 to 50°C                                                                                |
| Rated power                 | 63 W                                                                                     |
| Rated voltage               | 24 V                                                                                     |
| Rated current               | 2.6 A                                                                                    |
| Type of brake               | Soft brake                                                                               |
| Incremental encoder         | 16 bits                                                                                  |
| Absolute position encoder   | 18 bits                                                                                  |
| Communication interface     | CANFD                                                                                    |
| Examples of scenarios       | Lightweight robotic arm, neck joint of humanoid robot, intelligent travel products, etc. |

**Detailed dimensions**

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj10/CleanShot%202024-08-21%20at%2018.03.21.png)

**WHJ30 Standard Series**

**Model: WHJ30\_S\_D60\_80\_B**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj30/30-2.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                   | Value                                                                                                            |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Reduction ratio             | 80                                                                                                               |
| Weight                      | 750 g                                                                                                            |
| Diameter of reducer mm      | 60                                                                                                               |
| Size (D × L mm)             | 60 \* 86.5                                                                                                       |
| Rated torque N.m            | 30                                                                                                               |
| Maximum torque density      | 123                                                                                                              |
| Repeatability               | ±15 arc-seconds                                                                                                  |
| Peak speed (RPM)            | 37.5 (24V) / 75 (48V)                                                                                            |
| Moment of inertia (kg\*m^2) | 2.98\*10^-5                                                                                                      |
| Hollow aperture             | 9 mm                                                                                                             |
| Working temperature         | 0 to 50°C                                                                                                        |
| Rated power                 | 137 W                                                                                                            |
| Rated voltage               | 24 V / 48 V                                                                                                      |
| Rated current               | 5.7 A (24 V) / 2.8 A (48 V)                                                                                      |
| Type of brake               | Latch brake                                                                                                      |
| Incremental encoder         | 16 bits                                                                                                          |
| Absolute position encoder   | 18 bits                                                                                                          |
| Communication interface     | CANFD                                                                                                            |
| Examples of scenarios       | Robotic arm, surgical robot, and elbow joint, ankle joint, neck joint and shoulder joint of humanoid robot, etc. |

**Detailed dimensions**

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj30/CleanShot%202024-08-21%20at%2018.17.31.png)

**WHJ60 Standard Series**

**Model: WHJ60\_S\_D70\_100\_B**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj60/60-2.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                   | Value                                                                                                                     |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Reduction ratio             | 100                                                                                                                       |
| Weight                      | 1040 g                                                                                                                    |
| Diameter of reducer mm      | 70                                                                                                                        |
| Size (D × L mm)             | 70 × 91                                                                                                                   |
| Rated torque N.m            | 60                                                                                                                        |
| Maximum torque density      | 180                                                                                                                       |
| Repeatability               | ±15 arc-seconds                                                                                                           |
| Peak speed (RPM)            | 30 (24 V) / 60 (48 V)                                                                                                     |
| Moment of inertia (kg\*m^2) | 5.51\*10^-5                                                                                                               |
| Hollow aperture             | 9 mm                                                                                                                      |
| Working temperature         | 0 to 50°C                                                                                                                 |
| Rated power                 | 264 W                                                                                                                     |
| Rated voltage               | 24 V / 48 V                                                                                                               |
| Rated current               | 11 A (24 V) / 5.3 A (48 V)                                                                                                |
| Type of brake               | Latch brake                                                                                                               |
| Incremental encoder         | 16 bits                                                                                                                   |
| Absolute position encoder   | 18 bits                                                                                                                   |
| Communication interface     | CANFD                                                                                                                     |
| Examples of scenarios       | Robotic arm, and shoulder joint, waist joint, vertical hip joint and ankle joint of humanoid robot, heavy turntable, etc. |

**Detailed dimensions**

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj/whj60/CleanShot%202024-08-21%20at%2018.20.38.png)

**WHJ10 Torque Series**

**Model: WHJ10-S-D50-80-N-C-Y**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj_torque/torque_whj10/WHJTorque10.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                 | Value      |
| ------------------------- | ---------- |
| Weight                    | 489 g      |
| Size (D × L mm)           | 50 \* 78   |
| Hollow aperture           | 8 mm       |
| Rated voltage             | 24 V       |
| Rated current             | 4 A        |
| Rated power               | 90 W       |
| Rated speed (RPM)         | 37.5       |
| Peak speed (RPM)          | 37.5       |
| Rated torque N.m          | 10         |
| Reduction ratio           | 80         |
| Working temperature       | 0 to 50°C  |
| Incremental encoder       | 16 bits    |
| Absolute position encoder | 18 bits    |
| Type of brake             | Soft brake |
| Communication interface   | CANFD      |

**WHJ30 Torque Series**

**Model: WHJ30-S-D60-80-B-C-Y**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj_torque/torque_whj30/WHJTorque30.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                 | Value       |
| ------------------------- | ----------- |
| Weight                    | 820 g       |
| Size (D × L mm)           | 60 \* 101   |
| Hollow aperture           | 6.5 mm      |
| Rated voltage             | 24 V        |
| Rated current             | 11 A        |
| Rated power               | 256 W       |
| Rated speed (RPM)         | 37.5        |
| Peak speed (RPM)          | 37.5        |
| Rated torque N.m          | 30          |
| Reduction ratio           | 80          |
| Working temperature       | 0 to 50°C   |
| Incremental encoder       | 16 bits     |
| Absolute position encoder | 18 bits     |
| Type of brake             | Latch brake |
| Communication interface   | CANFD       |

**WHJ60 Torque Series**

**Model: WHJ60-S-D70-100-B-C-Y**

**Illustration**

<div align="left"><img src="https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/parameters/whj_torque/torque_whj60/WHJTorque60.png" alt="Official RealMan WHJ documentation image"></div>

**Performance parameters**

| Parameter                 | Value       |
| ------------------------- | ----------- |
| Weight                    | 1121 g      |
| Size (D × L mm)           | 70 \* 106   |
| Hollow aperture           | 9 mm        |
| Rated voltage             | 24 V        |
| Rated current             | 14 A        |
| Rated power               | 336 W       |
| Rated speed (RPM)         | 30          |
| Peak speed (RPM)          | 30          |
| Rated torque N.m          | 60          |
| Reduction ratio           | 100         |
| Working temperature       | 0 to 50°C   |
| Incremental encoder       | 16 bits     |
| Absolute position encoder | 18 bits     |
| Type of brake             | Latch brake |
| Communication interface   | CANFD       |

### Power Bleeding Module

Use the power bleeding module to absorb regenerative energy when high-speed or high-load operation raises the DC bus voltage.

**Product Overview**

**Product Positioning**

The HPD power bleeding module is specifically designed for HPD joint modules to handle regenerative braking energy under high-load and high-speed operating conditions.

The module absorbs regenerative energy and limits excessive DC bus voltage. This prevents overvoltage protection from causing unexpected shutdowns and helps the joint modules operate reliably.

**Application Scenarios**

A power bleeding module is required when high-torque, high-voltage joints are used with low-voltage dexterous hands or other precision end effectors. This is especially important in robotic-arm and integrated robot systems.

This helps prevent damage or burnout of the joints themselves or attached components such as dexterous hands.

When using HPD 48V high-torque joint modules, such as the WHG and WHJ series, it is recommended to pair them with this power bleeding module.

**Technical Information**

**Physical Specifications**

| Feature                 | Value      | Description                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dimensions L\*W\*H (mm) | 63.2×54×18 | These specifications refer to the braking resistor integrated with the bleeding module, which is sufficient for WHG and WHJ 10/30/60 series joints under rated conditions. The power bleeding module requires no additional cooling measures when installed normally with natural convection. If used with WHG and WHJ 120/240/360 series joints, additional cooling measures are required. |
| Weight (g)              | 66         |                                                                                                                                                                                                                                                                                                                                                                                             |

**Environmental Conditions**

| Feature                    | Specification                  |
| -------------------------- | ------------------------------ |
| Operating Temperature      | 0°C to 50°C                    |
| Storage Temperature        | -10°C to 60°C                  |
| Operating/Storage Humidity | 20% to 80% RH (non-condensing) |

**Electrical Interface**

The electrical interface of the power bleeding module is shown in the figure below:

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/power_discharge_module/image1.png)

The electrical interface definitions of the power bleeding module are shown in the table below:

| Terminal Mark | Terminal Function                          | Terminal Specification                                           |
| ------------- | ------------------------------------------ | ---------------------------------------------------------------- |
| DC+           | Connect to 24V/48VDC power supply positive | <p>Wire Gauge: 26-14AWG<br>Tool: Flat-head 3.0mm screwdriver</p> |
| DC-           | Connect to 24V/48VDC power supply negative |                                                                  |
| R+            | Connect to resistor                        |                                                                  |
| R-            |                                            |                                                                  |
| C+            | Connect to capacitor                       |                                                                  |
| C-            |                                            |                                                                  |

**Interaction Description**

The interaction indicators of the power bleeding module are shown in the figure below:

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/power_discharge_module/image2.png)

The detailed interaction definitions of the power bleeding module are shown in the table below:

| No. | Item Name                        | Status Description                                                                 |
| --- | -------------------------------- | ---------------------------------------------------------------------------------- |
| 1   | Operating Voltage Selection      | Manually select 48V or 24V operating mode. 48V joint modules require the 48V mode. |
| 2   | Overvoltage & Bleeding Indicator | See specific interaction modes below for details.                                  |
| 3   | Undervoltage Indicator           |                                                                                    |
| 4   | Power Indicator                  | Green light on: Module operating normally; Green light off: Module disconnected.   |

\
<br>

TIP

The bleeding resistor dissipates excess regenerative energy from the joint circuit. This prevents the returned energy from producing voltage spikes at the power supply.

The bleeding resistor must not be connected to the circuit for extended periods, as it will continuously generate heat, which may lead to component damage, circuit failure, and additional power consumption.

Therefore, it is recommended to implement a reliable bleeding resistor control logic. For details, please refer to Interaction Mode in 48V Setting , Interaction Mode in 24V Setting , and Undervoltage Compensation Method .

**Interaction Mode in 48V Setting**

| Operating Status | Undervoltage | Normal       | Bleeding    | Overvoltage |
| ---------------- | ------------ | ------------ | ----------- | ----------- |
| Voltage Range    | X ≤35V       | 35V ＜ X ＜52V | 52V≤ X ＜70V | 70V≤ X      |
| Bleeding Mode    | Off          | Off          | Activated   | Off         |

WARNING

Even if the voltage is lower than 35V, the motor will not stop rotating due to its wide operating voltage range and the system feedback mechanism.

When measuring the voltage thresholds of different discharge boards, there may be an error of 0.1–0.2V.

**Interaction Mode in 24V Setting**

| Operating Status | Undervoltage | Normal         | Bleeding      | Overvoltage |
| ---------------- | ------------ | -------------- | ------------- | ----------- |
| Voltage Range    | X ≤15V       | 15V ＜ X ＜25.5V | 25.5V≤ X ＜33V | 33V≤ X      |
| Bleeding Mode    | Off          | Off            | Activated     | Off         |

**Undervoltage Compensation Method**

| Function Name                                                               | Parameters                                                                  | Function Description                                                                                                                                                                                     |
| --------------------------------------------------------------------------- | --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Undervoltage Compensation                                                   | <p>48V:<br>3 FTR20D560KJ Varistors, 1 80V/820µF Electrolytic Capacitor.</p> | The 3 varistors and the electrolytic capacitor are all connected in parallel at the power supply terminals. Refer to: Recommended Accessory Specifications for Each Joint Model for specific quantities. |
| <p>24V:<br>3 FTR20D330KJ Varistors, 1 50V/820µF Electrolytic Capacitor.</p> |                                                                             |                                                                                                                                                                                                          |

**Recommended Accessory Specifications for Each Joint Model**

The discharge module must be used together with capacitors and resistors. Different joint models require capacitors and resistors of different specifications and quantities, as shown in the table below:

* WHJ10/30/60 and WHG1410E/1730E/2060E are equipped with one discharge box, one braking resistor (75W/5Ω), and one 820μF electrolytic capacitor (80V rating for 48V systems, 50V rating for 24V systems).
* WHJ120 and WHG25120E/32240E are equipped with one discharge box, one braking resistor (300W/5Ω), and two 820μF electrolytic capacitors (80V rating for 48V systems, 50V rating for 24V systems).

| WHJ Series Joint Model | WHJ Series DC Power Supply Specification | WHG Series Joint Model | WHG Series DC Power Supply Specification | Braking Resistor Specification | Electrolytic Capacitor Specification | Number of Capacitors |
| ---------------------- | ---------------------------------------- | ---------------------- | ---------------------------------------- | ------------------------------ | ------------------------------------ | -------------------- |
| WHJ10                  | 63W, 48VDC                               | WHG1410E               | 73W, 48VDC                               | 75W, 5Ω                        | 820uF, 80V                           | 1                    |
| 63W, 24VDC             | 73W, 24VDC                               | 75W, 5Ω                | 820uF, 50V                               | 1                              |                                      |                      |
| WHJ30                  | 137W, 48VDC                              | WHG1730E               | 155W, 48VDC                              | 75W, 5Ω                        | 820uF, 80V                           | 1                    |
| 137W, 24VDC            | 155W, 24VDC                              | 75W, 5Ω                | 820uF, 50V                               | 1                              |                                      |                      |
| WHJ60                  | 258W, 48VDC                              | WHG2060E               | 287W, 48VDC                              | 75W, 5Ω                        | 820uF, 80V                           | 1                    |
| 258W, 24VDC            | 287W, 24VDC                              | 75W, 5Ω                | 820uF, 50V                               | 1                              |                                      |                      |
| WHJ120                 | 720W, 48VDC                              | WHG25120E              | 611W, 48VDC                              | 300W, 5Ω                       | 820uF, 80V                           | 2                    |
| 720W, 24VDC            | 611W, 24VDC                              | 300W, 5Ω               | 820uF, 50V                               | 2                              |                                      |                      |
| /                      | WHG32240E                                | 873W, 48VDC            | 300W, 5Ω                                 | 820uF, 80V                     | 2                                    |                      |
| 873W, 24VDC            | 300W, 5Ω                                 | 820uF, 50V             | 2                                        |                                |                                      |                      |

**Wiring and Usage Instructions**

The wiring diagram of the power supply, discharge module, and joint module is shown in the figure below:

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/power_discharge_module/image3.png) ![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/power_discharge_module/image4.png)

The wiring instructions for the discharge module are shown in the table below:

| No. | Item Name                 | Description                                                                                    |
| --- | ------------------------- | ---------------------------------------------------------------------------------------------- |
| 1   | Power Supply              | Connect the positive terminal to DC+ of the discharge module, and the negative terminal to DC- |
| 2   | Discharge Module          | /                                                                                              |
| 3   | Discharge Module Resistor | Connect to R+ and R- terminals                                                                 |
| 4   | Capacitor                 | Connect to C+ and C- terminals                                                                 |
| 5   | Joint                     | Connected in parallel with the discharge module                                                |

TIP

The discharge module and the joint are connected in parallel. According to the rated voltage of the joint, manually switch the voltage mode to either 48V or 24V.

Connect the power supply positive terminal to the DC+ terminal of the discharge module, and the negative terminal to DC-.

Connect the matching braking resistor to the R+ and R- terminals, and the capacitor to the C+ and C- terminals (if multiple capacitors are required, connect them in parallel).

During wiring, strictly observe polarity and securely fasten all terminals.

**Outline and Installation**

**Outline Dimensions**

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/power_discharge_module/image5.png)

**Installation Method**

Note

The power bleeding module will generate heat during operation, and the resistor may become hot. Do not touch directly.

The installation environment should have good ventilation and heat dissipation conditions, such as mounting on a large metal plate or inside an electrical cabinet with cooling fans.

![Official RealMan WHJ documentation image](https://develop.realman-robotics.com/realman/docs/images/multimedia/en/joints/power_discharge_module/image6.png)

### CANFD Protocol and Operation

This section explains the CANFD frame format, control table, and command examples used to configure and operate WHJ modules.

**Protocol Overview**

WHJ modules use CANFD in a request-response communication model. The controller sends a command frame, and the addressed module returns a response frame.

A CAN bus can connect multiple modules, with each module assigned a unique ID.

The control command sent from the controller contain ID information, and only the module matching the ID number will receive this command completely and return the response information.

All query, control, and parameter modification commands will be completed through read-write operations on a memory control table stored inside the module's main control chip.

The basic storage unit of the memory control table is 2-byte signed integer.

All data longer than 1 byte will be transmitted and stored with the lower byte first.

In protocol analysis, the memcpy function in c programming language can be used in combination to realize the conversion from byte data to integer data or from integer data to byte data.

The command types include the following:

| Command         | Function                            | Value | Data segment length |
| --------------- | ----------------------------------- | ----- | ------------------- |
| CMD\_RD (read)  | Query the data in the control table | 0x01  | 1                   |
| CMD\_WR (write) | Write data into the control table   | 0x02  | 2                   |

**Frame Format**

Joints use the standard frame format of CANFD, where only data frames are used, and there is no response for remote frames. The data frame of the CANFD protocol is up to 64 bytes long, and the communication rate can reach 5M.

The data length codes of the CANFD protocol are shown below.

| CANFD data field |   |   |   |   |   |   |   |   |   |    |    |    |    |    |    |    |
| ---------------- | - | - | - | - | - | - | - | - | - | -- | -- | -- | -- | -- | -- | -- |
| DLC              | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  | 10 | 11 | 12 | 13 | 14 | 15 |
| Data Bytes       | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 12 | 16 | 20 | 24 | 32 | 48 | 64 |

**Command package**

The format of command package is as follows:

| Arbitration field | Control field | Data field | CRC and other fields |    |     |     |        |              |       |      |      |        |   |   |   |   |
| ----------------- | ------------- | ---------- | -------------------- | -- | --- | --- | ------ | ------------ | ----- | ---- | ---- | ------ | - | - | - | - |
| STID/11           | R1            | IDE        | FDF                  | R0 | BRS | ESI | DLC/4  | Data（64Byte） | CRC   | ACK  | EOF  | IFS    |   |   |   |   |
| ID                | 0             | 0          | 1                    | 0  | 1   | 0   | Length | CMD          | INDEX | DATA | DATA | ...... |   |   |   |   |

**Arbitration field**: Only the target ID segment needs arbitration. The arbitration field ID is the module ID. The module ID is 0x00 - 0x1E (0 - 30), and the broadcasting ID is 0x00 (0). Typically, ID0 is for the interface board.

Control field : DLC length, i.e., the length of data field bytes, is up to 64 bytes. The data length table is as shown above; BRS stands for the variable rate, where 1 means variable, and 0 means not variable;

ESI is temporarily set to 0, and the bus does not actively report errors.

Data field : The first byte of the data field represents the command type, the second byte represents the control table index, and the third to fourth bytes represent the data sent together with the command.

The read command has one byte of data representing the number of memory table registers to be read;

and the write command consists of two bytes of data, which are the contents to be written to the memory table, with the lower bits coming first.

**Response package**

The format of response package is as follows:

| Arbitration field | Control field | Data field | CRC and other fields |    |     |     |        |      |       |      |      |        |   |   |   |   |
| ----------------- | ------------- | ---------- | -------------------- | -- | --- | --- | ------ | ---- | ----- | ---- | ---- | ------ | - | - | - | - |
| STID/11           | R1            | IDE        | FDF                  | R0 | BRS | ESI | DLC/4  | Data | CRC   | ACK  | EOF  | IFS    |   |   |   |   |
| ID+0x100          | 0             | 0          | 1                    | 0  | 1   | 0   | Length | CMD  | INDEX | DATA | DATA | ...... |   |   |   |   |

The format of response package is substantially the same as that of the command package, except the following differences:

* If the module receives a read command, the returned data segment is the data of the specified length.
* If the module receives a write command, the returned data segment is whether the operation was successful, with 0x01 indicating success and 0x00 indicating failure.
* The ID of the response package is ID+0x100.

TIP

* When the issued CANFD control frame does not meet the protocol requirements, the actuator returns a CMD\_ERR response package in the following format.

| Arbitration field | Control field | Data field | CRC and other fields |    |     |     |       |             |     |     |     |     |   |
| ----------------- | ------------- | ---------- | -------------------- | -- | --- | --- | ----- | ----------- | --- | --- | --- | --- | - |
| STID/11           | R1            | IDE        | FDF                  | R0 | BRS | ESI | DLC/4 | Data（2Byte） | CRC | ACK | EOF | IFS |   |
| ID+0x100          | 0             | 0          | 1                    | 0  | 1   | 0   | 2     | CMD\_ERR    | ERR |     |     |     |   |

* ERR represents the error type, with the error codes shown as follows:

| Error bit | Definition      | Description                                               |
| --------- | --------------- | --------------------------------------------------------- |
| 0x01      | Format error    | The control frame data does not meet the protocol format. |
| 0x02      | Authority error | The control frame has no operation authority.             |

**Memory Control Table**

**1. Details of control table**

The information and control parameters of the module itself form a one-dimensional control table, which is stored in the RAM and Flash of the control chip respectively.

When the system is powered on, the control chip reads the control table from Flash to RAM. During the operation of the module, the user reads and writes the control table in RAM to obtain the module status or control the module.

If the user writes 1 to the "Save Data to Flash Flag" in the table, the control chip copies the contents of the present RAM table to Flash to realize power-off saving. The contents of the control table are shown below:

| **Address**    | **Designation**           | **Command**                                                                                                                                          | **Authority** | **Initial value**                                           |
| -------------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------- | ----------------------------------------------------------- |
| **0x00**       | Reserved                  | Reserved                                                                                                                                             | --            | 0x1314                                                      |
| **0x01**       | SYS\_ID                   | Driver ID                                                                                                                                            | --            | 1                                                           |
| **0x02**       | SYS\_MODEL\_TYPE          | Driver model, please refer to Definition of Driver Model for details.                                                                                | R             | --                                                          |
| **0x03**       | SYS\_FW\_VERSION          | Firmware version, for example, 0x0102 stands for the version 1.2                                                                                     | R             | --                                                          |
| **0x04**       | SYS\_ERROR                | Error code                                                                                                                                           | R             | --                                                          |
| **0x05**       | SYS\_VOLTAGE              | System voltage (0.01 V)                                                                                                                              | R             | --                                                          |
| **0x06**       | SYS\_TEMP                 | System temperature (0.1°C)                                                                                                                           | R             | --                                                          |
| **0x07**       | SYS\_REDU\_RATIO          | Reduction ratio                                                                                                                                      | R             | Consistent with program compilation 80/100                  |
| **0x08\~0x09** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x0A**       | SYS\_ENABLE\_DRIVER       | Enable the driver flag, 1: enable, 0: disable. (Do not issue any command until 5 ms later after disabling the driver)                                | R/W           | 0                                                           |
| **0x0B**       | SYS\_ENABLE\_ON\_POWER    | Power-on to enable the driver flag, 1: enable; 0: disable.                                                                                           | R/W           | 1                                                           |
| **0x0C**       | SYS\_SAVE\_TO\_FLASH      | Save data to Flash flag, 1: Save, 0: Not save. Save under the disabled state. (Do not issue a command until 50 ms later after sending Save to Flash) | R/W           | 0                                                           |
| **0x0D**       | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x0E**       | SYS\_SET\_ZERO\_POS       | Set the current position to zero point flag, 1: Set; 0: Not set                                                                                      | R/W           | 0                                                           |
| **0x0F**       | SYS\_CLEAR\_ERROR         | Clear the error flag, 1: Clear, 0: Not clear                                                                                                         | R/W           | 0                                                           |
| **0x10**       | CUR\_CURRENT\_L           | Current current low 16 bits (mA)                                                                                                                     | R             | 0                                                           |
| **0x11**       | CUR\_CURRENT\_H           | Current current high 16 bits (mA)                                                                                                                    | R             | --                                                          |
| **0x12**       | CUR\_SPEED\_L             | Current joint speed low 16 bits (RPM, with a resolution of 0.02 RPM)                                                                                 | R             | --                                                          |
| **0x13**       | CUR\_SPEED\_H             | Current joint speed high 16 bits (RPM, with a resolution of 0.02 RPM)                                                                                | R             | --                                                          |
| **0x14**       | CUR\_POSITION\_L          | Current position low 16 bits (units), with an accuracy of 0.0001°                                                                                    | R             | --                                                          |
| **0x15**       | CUR\_POSITION\_H          | Current position high 16 bits (units), with an accuracy of 0.0001°                                                                                   | R             | --                                                          |
| **0x16\~0x1E** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x1F**       | ON\_DELAY                 | 0 indicates a delay in powering up the joint, 1 indicates no delay in powering up the joint                                                          | R/W           | 0                                                           |
| **0x20\~0x29** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x2A**       | MOT\_MODEL\_ID0           | Globally unique ID of module: 15:0                                                                                                                   | R             | --                                                          |
| **0x2B**       | MOT\_MODEL\_ID1           | Globally unique ID of module: 31:16                                                                                                                  | R             | --                                                          |
| **0x2C**       | MOT\_MODEL\_ID2           | Globally unique ID of module: 47:32                                                                                                                  | R             | --                                                          |
| **0x2D**       | MOT\_MODEL\_ID3           | Globally unique ID of module: 63:48                                                                                                                  | R             | --                                                          |
| **0x2E**       | MOT\_MODEL\_ID4           | Globally unique ID of module: 79:64                                                                                                                  | R             | --                                                          |
| **0x2F**       | MOT\_MODEL\_ID5           | Globally unique ID of module: 95:80                                                                                                                  | R             | --                                                          |
| **0x30**       | TAG\_WORK\_MODE           | Work mode: 0-open loop, 1-current mode, 2-speed mode, 3-position mode                                                                                | R/W           | 3                                                           |
| **0x31**       | TAG\_OPEN\_PWM            | Duty ratio in open loop mode (0−100)                                                                                                                 | R/W           | 0                                                           |
| **0x32**       | TAG\_CURRENT\_L           | Target current low 16 bits (mA)                                                                                                                      | R/W           | 0                                                           |
| **0x33**       | TAG\_CURRENT\_H           | Target current high 16 bits (mA)                                                                                                                     | R/W           | 0                                                           |
| **0x34**       | TAG\_SPEED\_L             | Target joint speed low 16 bits (RPM, with a resolution of 0.002 RPM)                                                                                 | R/W           | 0                                                           |
| **0x35**       | TAG\_SPEED\_H             | Target joint speed high 16 bits (RPM, with a resolution of 0.002 RPM)                                                                                | R/W           | 0                                                           |
| **0x36**       | TAG\_POSITION\_L          | Target position low 16 bits (units), with an accuracy of 0.0001°                                                                                     | R/W           | 0                                                           |
| **0x37**       | TAG\_POSITION\_H          | Target position high 16 bits (units), with an accuracy of 0.0001°                                                                                    | R/W           | 0                                                           |
| **0x38**       | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x39**       | Speed feed forward switch | The stored value is the position loop following coefficient, with valid values ranging from 0 to 100 and a default value of 0.                       | R/W           | 0                                                           |
| **0x3A\~0x3F** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x40**       | LIT\_MAX\_CURRENT         | Maximum current (mA) (Reserved)                                                                                                                      | R/W           | --                                                          |
| **0x41**       | LIT\_MAX\_SPEED           | Maximum joint speed (RPM, resolution 1/gear ratio RPM)                                                                                               | R/W           | 3000                                                        |
| **0x42**       | LIT\_MAX\_ACC             | Maximum joint acceleration (0.1 rpm/s)                                                                                                               | R/W           | 5000                                                        |
| **0x43**       | LIT\_MAX\_DEC             | Maximum joint deceleration (0.1 rpm/s) (Reserved)                                                                                                    | R/W           | --                                                          |
| **0x44**       | LIT\_MIN\_POSITION\_L     | Minimum position low 16 bits (units), with an accuracy of 0.0001°                                                                                    | R/W           | --                                                          |
| **0x45**       | LIT\_MIN\_POSITION\_H     | Minimum position high 16 bits (units), with an accuracy of 0.0001°                                                                                   | R/W           | --                                                          |
| **0x46**       | LIT\_MAX\_POSITION\_L     | Maximum position low 16 bits (units), with an accuracy of 0.0001°                                                                                    | R/W           | --                                                          |
| **0x47**       | LIT\_MAX\_POSITION\_H     | Maximum position high 16 bits (units), with an accuracy of 0.0001°                                                                                   | R/W           | --                                                          |
| **0x48**       | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x49**       | IAP\_FLAG                 | IAP updates flag position online: 0-Not update, 1-Update                                                                                             | R/W           | 0                                                           |
| **0x4A\~0x50** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x51**       | SEV\_CURRENT\_P           | Current loop P parameter                                                                                                                             | R/W           | --                                                          |
| **0x52**       | SEV\_CURRENT\_I           | Current loop I parameter                                                                                                                             | R/W           | --                                                          |
| **0x53**       | SEV\_CURRENT\_D           | Current loop D parameter                                                                                                                             | R/W           | --                                                          |
| **0x54**       | SEV\_SPEED\_P             | Current loop P parameter                                                                                                                             | R/W           | --                                                          |
| **0x55**       | SEV\_SPEED\_I             | Speed loop I parameter                                                                                                                               | R/W           | --                                                          |
| **0x56**       | SEV\_SPEED\_D             | Speed loop D parameter                                                                                                                               | R/W           | --                                                          |
| **0x57**       | SEV\_SPEED\_DS            | Speed P dead zone                                                                                                                                    | R/W           | --                                                          |
| **0x58**       | SEV\_POSITION\_P          | Position loop P parameter                                                                                                                            | R/W           | --                                                          |
| **0x59**       | SEV\_POSITION\_I          | Position loop I parameter                                                                                                                            | R/W           | --                                                          |
| **0x5A**       | SEV\_POSITION\_D          | Position loop D parameter                                                                                                                            | R/W           | --                                                          |
| **0x5B**       | SEV\_POSITION\_DS         | Position P dead zone                                                                                                                                 | R/W           | --                                                          |
| **0x5C**       | SEV\_POS\_SMOOTH          | Position Loop Smoothing Coefficient                                                                                                                  | R/W           | The larger the coefficient, the better the following effect |
| **0x5D**       | SEV\_SPD\_FF              | Speed Feedforward Coefficient                                                                                                                        | R/W           | The larger the coefficient, the better the following effect |
| **0x5E\~0x68** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x69**       | LOW\_POWER\_MODE          | Low Power Consumption Mode                                                                                                                           | R/W           | --                                                          |
| **0x6A\~77**   | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |
| **0x78**       | ERROR                     | Error code                                                                                                                                           | R             | 0                                                           |
| **0x79**       | END\_BOARD\_MODE          | End-effector Mode                                                                                                                                    | R/W           | 0                                                           |
| **0x7A\~0x91** | Reserved                  | Reserved                                                                                                                                             | --            | --                                                          |

WARNING

1. After the ID is successfully set, it is necessary to de-energize and then restart the joint. The module will conduct communication with the new ID.
2. The parameters of the three closed loops have been set before leaving the factory. No re-adjustment is required if not necessary.

**2. Additional notes on the control table**

**2.1 Description of flags**

There are 6 flag variables in total, whose values can only be 1 or 0, and other values are invalid.

See the table below for more details.

| **Address** | **Definition**                                     | **Description**                                                                                                                                                                                                                                                                                                                                                             |
| ----------- | -------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0x0a        | Enable the driver flag                             | 1: Enable the driver; 0: Disable the driver and open the phase-locked relay.                                                                                                                                                                                                                                                                                                |
| 0x0b        | Power-on to enable the driver flag                 | 1: The driver is enabled and works in the given mode after power-on; 0: The driver is not enabled after power-on.                                                                                                                                                                                                                                                           |
| 0x0c        | Save data to Flash flag                            | 1: The chip writes the control table in the current RAM into Flash, and the system automatically resets.                                                                                                                                                                                                                                                                    |
| 0x0d        | Automatically calibrate the absolute position flag | 1: The driver will calibrate the absolute position sensor (digital potentiometer) according to the value of the encoder, and save the calibrated data to Flash. The module must be currently under no load, and can work stably in the position servo mode and in the enabled state; otherwise, unpredictable consequences will be caused. The system automatically resets. |
| 0x0e        | Set the current position to zero point flag        | 1: Save the current position as the zero point, which will take effect immediately. After the data is saved to Flash, the saved position will be used as the zero point after power-on next time. The system automatically resets.                                                                                                                                          |
| 0x0f        | Clear error flag                                   | 1: Attempt to clear the current error. The system automatically resets.                                                                                                                                                                                                                                                                                                     |

**2.2 Description of units**

* For 10-joint and 30-joint, the unit of the target current and the actual feedback current is 1 mA;<br>
* For 60-joint, the unit of the target current and the actual feedback current is 2 mA;<br>
* The unit of feedforward current of all joints is 2 mA;<br>
* The unit of target speed at the joint output end is 0.002 RPM;<br>
* The unit of actual speed at the joint output end is 0.002 RPM;<br>
* The unit of feedforward speed at the joint output end is 0.002 RPM;<br>
* The unit of target position and actual feedback position at the joint output end is 0.0001°;<br>
* The unit of voltage is 0.01 V;<br>
* The unit of system temperature is 0.1°C.<br>

**2.3 Description of work modes**

The module can work in four modes, namely the open loop mode, current mode, speed mode, and position mode. The module can switch among the four modes by changing the TAG\_WORK\_MODE field (0x30) in the control table.

1. The open loop mode directly controls the duty ratio of the driver output to the motor, which is prone to danger and therefore is not recommended.
2. The current mode controls the target output current (torque) of the motor.
3. The speed mode controls the output speed of motor. It is not recommended unless the module can rotate in a whole circle.
4. Position mode controls the motor servo position.

The target duty ratio, current, speed, and position in the 0x3\* field only work when the module is in the corresponding work mode.

The maximum current, speed, and acceleration/deceleration values in fields 0x40 to 0x46 apply in current, speed, and position modes.

The minimum and maximum position limits apply only in position-servo mode, and target positions must remain within that range.

If the set target position is less than the minimum value or exceeds the maximum value, the module will only move to the minimum or maximum value.

If the module is out of range when the driver is enabled, it will automatically move to the minimum/maximum value.

**2.4 Definition of Driver Model**

The joint types corresponding to the memory control table address 0x02 of the driver model are explained as follows:

| Joint Type | Character Definition | Memory Vector Table Definition |
| ---------- | -------------------- | ------------------------------ |
| Joint 10   | J14                  | 0x02                           |
| Joint 30   | J17                  | 0x03                           |
| Joint 60   | J20                  | 0x04                           |
| Joint 120  | J25                  | 0x05                           |
| Gripper    | GRIPPER              | 0x06                           |
| Joint 03   | J3                   | 0x07                           |

**3. Error code**

The error code has 16 bits, and each bit represents a type of error. If an error occurs, the corresponding bit will be displayed as 1.

If an unrecoverable error occurs, the module will automatically enter the driver disabled state, and users need to write 1 to the "Clear Error Flag" field (0x0f) to clear the error.

The meaning of each error bit is as follows:

| **Bit** | **Definition**                       | **Description**                                                                                             |
| ------- | ------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| 0x0001  | FOC rate too high                    | FOC rate too high                                                                                           |
| 0x0002  | Overvoltage                          | Input voltage exceeds the joint's voltage rating                                                            |
| 0x0004  | Undervoltage                         | Input voltage is below the joint's voltage rating                                                           |
| 0x0008  | Over-temperature                     | Joint temperature reaches the alarm temperature                                                             |
| 0x0010  | Startup failure                      | Joint startup FOC error                                                                                     |
| 0x0020  | Encoder error                        | Joint self-check failure or unable to recognize the current angle                                           |
| 0x0040  | Overcurrent                          | Motor current is too high                                                                                   |
| 0x0080  | Software error                       | Hardware and software do not corresponding, current detection error                                         |
| 0x0100  | Temperature sensor error             | Temperature sensor fails to obtain joint temperature properly                                               |
| 0x0200  | Position out-of-limit error          | Current position beyond the limit                                                                           |
| 0x0400  | Illegal joint ID                     | Incorrect joint ID                                                                                          |
| 0x0800  | Position tracking error out-of-limit | Target position and current position difference exceeds threshold; position error tracking limit protection |
| 0x1000  | Current detection error              | Current sensor detection error during power-on                                                              |
| 0x2000  | Brake failure                        | Brake release failure; internal Hall signal incorrect                                                       |
| 0x4000  | Position command step                | Current position and target position error is greater than 10 degrees                                       |
| 0x8000  | Multi-revolution data loss           | Multi-turn loss of count                                                                                    |

**Command and Usage Examples**

**1. Environment Configuration**

* Arbitration domain baud rate: 1Mbps 80%.
* Data and baud rate: 5Mbps 75%.

**2. Basic demo**

**Read the current position of the module whose ID is 1**

Command = CMD\_RD; Current position low 16-bit address = 0x14, read the data of two registers;

Command package:

| CAN-ID                 | DLC  | Byte1 | Byte2 | Byte3 |
| ---------------------- | ---- | ----- | ----- | ----- |
| 0x01                   | 0x03 | 0x01  | 0x14  | 0x02  |
| Current position query |      |       |       |       |

Response package:

| CAN-ID           | DLC  | Byte1 | Byte2 | Byte3 | Byte4 | Byte5 | Byte6 |
| ---------------- | ---- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x101            | 0x06 | 0x01  | 0x14  | 0x10  | 0x27  | 0x00  | 0x00  |
| Current position |      |       |       |       |       |       |       |

Current position: position = 0x00002710/10000 = 1°

**Set the target position of the module whose ID is 1 to 1°**

Command = CMD\_WR; address = 0x36; data = 10000 = 0x00002710;

**(1) Normal mode:**

Command package:

| CAN-ID                  | DLC  | Byte1 | Byte2 | Byte3 | Byte4 | Byte5 | Byte6 |
| ----------------------- | ---- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x01                    | 0x06 | 0x02  | 0x36  | 0x10  | 0x27  | 0x00  | 0x00  |
| Set the target position |      |       |       |       |       |       |       |

Response package:

| CAN-ID                           | DLC  | Byte1 | Byte2 | Byte3 |
| -------------------------------- | ---- | ----- | ----- | ----- |
| 0x101                            | 0x03 | 0x02  | 0x36  | 0x01  |
| Target position set successfully |      |       |       |       |

**(2) Servo mode:**

Command package:

| CAN-ID                  | DLC  | Byte1 | Byte2 | Byte3 | Byte4 |
| ----------------------- | ---- | ----- | ----- | ----- | ----- |
| 0x201                   | 0x04 | 0x10  | 0x27  | 0x00  | 0x00  |
| Set the target position |      |       |       |       |       |

Response package:

| CAN-ID                        | DLC                   | 1                | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | 12   |
| ----------------------------- | --------------------- | ---------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0x501                         | 0x10                  | 0x64             | 0x00 | 0x00 | 0x00 | 0x00 | 0x00 | 0x00 | 0x00 | 0x10 | 0x20 | 0x00 | 0x00 |
| Current current (100 mA)      | Current speed (0)     | Current position |      |      |      |      |      |      |      |      |      |      |      |
| 13                            | 14                    | 15               | 15   |      |      |      |      |      |      |      |      |      |      |
| 0x01                          | 0x00                  | 0x00             | 0x00 |      |      |      |      |      |      |      |      |      |      |
| Enable status (Enable status) | Error code (no error) |                  |      |      |      |      |      |      |      |      |      |      |      |

**3. Demo of common command package**

**Position servo command package**

When the joint is in the position servo mode, it enters the cyclic position servo control stage.

The controller sends position-command frames to each joint module. Each module performs position-servo control and returns its position, current, speed, enable status, and error code in a feedback frame.

If 7 modules on a bus participate in cyclic servo control, 14 frames of communication will be generated on the bus within one control cycle to reduce the bus load.

**Position servo command frame**:

| Arbitration field | Control field    | Data field | CRC and other fields |    |     |     |        |             |     |     |     |     |   |   |   |
| ----------------- | ---------------- | ---------- | -------------------- | -- | --- | --- | ------ | ----------- | --- | --- | --- | --- | - | - | - |
| STID/11           | R1               | IDE        | FDF                  | R0 | BRS | ESI | DLC/4  | Data（4Byte） | CRC | ACK | EOF | IFS |   |   |   |
| ID+0x200          | 0                | 0          | 1                    | 0  | 1   | 0   | Length | D0          | D1  | D2  | D3  |     |   |   |   |
| 4                 | Current position |            |                      |    |     |     |        |             |     |     |     |     |   |   |   |

**Servo feedback frame:**

| Arbitration field | Control field   | Data field    | CRC and other fields |               |            |         |          |          |        |
| ----------------- | --------------- | ------------- | -------------------- | ------------- | ---------- | ------- | -------- | -------- | ------ |
| STID/11           | R1              | ......        | DLC/4                | Data（16Byte）  | ......     |         |          |          |        |
| ID+0x500          | 0               | ......        | Length               | D0\~D3        | D4\~D7     | D8\~D11 | D12\~D13 | D14\~D15 | ...... |
| 16                | Current current | Current speed | Current position     | Enable status | Error code | ......  |          |          |        |

**Speed servo command package**

When the joint is in the speed servo mode, it enters the cyclic speed servo control stage.

The controller sends speed-command frames to each joint module. Each module performs speed-servo control and returns its position, current, speed, enable status, and error code in a feedback frame.

**Speed servo command frame**:

| Arbitration field | Control field | Data field | CRC and other fields |    |     |     |        |             |     |     |     |     |   |   |   |
| ----------------- | ------------- | ---------- | -------------------- | -- | --- | --- | ------ | ----------- | --- | --- | --- | --- | - | - | - |
| STID/11           | R1            | IDE        | FDF                  | R0 | BRS | ESI | DLC/4  | Data（4Byte） | CRC | ACK | EOF | IFS |   |   |   |
| ID+0x300          | 0             | 0          | 1                    | 0  | 1   | 0   | Length | D0          | D1  | D2  | D3  |     |   |   |   |
| 4                 | Target speed  |            |                      |    |     |     |        |             |     |     |     |     |   |   |   |

**Servo feedback frame:**

| Arbitration field | Control field   | Data field    | CRC and other fields |               |            |         |          |          |        |
| ----------------- | --------------- | ------------- | -------------------- | ------------- | ---------- | ------- | -------- | -------- | ------ |
| STID/11           | R1              | ......        | DLC/4                | Data（16Byte）  | ......     |         |          |          |        |
| ID+0x500          | 0               | ......        | Length               | D0\~D3        | D4\~D7     | D8\~D11 | D12\~D13 | D14\~D15 | ...... |
| 16                | Current current | Current speed | Current position     | Enable status | Error code | ......  |          |          |        |

**Current servo command package**

To control the joint current. Once a current servo command frame is issued, a servo feedback frame is returned.

**Current servo command frame**:

| Arbitration field | Control field | Data field | CRC and other fields |    |     |     |        |             |     |     |     |     |   |   |   |
| ----------------- | ------------- | ---------- | -------------------- | -- | --- | --- | ------ | ----------- | --- | --- | --- | --- | - | - | - |
| STID/11           | R1            | IDE        | FDF                  | R0 | BRS | ESI | DLC/4  | Data（4Byte） | CRC | ACK | EOF | IFS |   |   |   |
| ID+0x400          | 0             | 0          | 1                    | 0  | 1   | 0   | Length | D0          | D1  | D2  | D3  |     |   |   |   |
| 4                 | Target speed  |            |                      |    |     |     |        |             |     |     |     |     |   |   |   |

**Servo feedback frame:**

| Arbitration field | Control field   | Data field    | CRC and other fields |               |            |         |          |          |        |
| ----------------- | --------------- | ------------- | -------------------- | ------------- | ---------- | ------- | -------- | -------- | ------ |
| STID/11           | R1              | ......        | DLC/4                | Data（16Byte）  | ......     |         |          |          |        |
| ID+0x500          | 0               | ......        | Length               | D0\~D3        | D4\~D7     | D8\~D11 | D12\~D13 | D14\~D15 | ...... |
| 16                | Current current | Current speed | Current position     | Enable status | Error code | ......  |          |          |        |

**Joint status query command package**

To query the joint status in cycles.

To improve bus utilization, query common joint data with a command frame. The joint then returns its error code, system voltage, system temperature, enable status, and current position in one status-feedback frame.

**Joint status query command frame**:

| Arbitration field | Control field | Data field | CRC and other fields |    |     |     |        |             |     |     |     |     |
| ----------------- | ------------- | ---------- | -------------------- | -- | --- | --- | ------ | ----------- | --- | --- | --- | --- |
| STID/11           | R1            | IDE        | FDF                  | R0 | BRS | ESI | DLC/4  | Data（0Byte） | CRC | ACK | EOF | IFS |
| ID+0x600          | 0             | 0          | 1                    | 0  | 1   | 0   | Length |             |     |     |     |     |
| 0                 |               |            |                      |    |     |     |        |             |     |     |     |     |

**Joint status feedback frame**:

| Arbitration field | Control field | Data field     | CRC and other fields |                                            |                  |                 |        |         |          |         |
| ----------------- | ------------- | -------------- | -------------------- | ------------------------------------------ | ---------------- | --------------- | ------ | ------- | -------- | ------- |
| STID/11           | R1            | ......         | DLC/4                | Data（16Byte）                               | ......           |                 |        |         |          |         |
| ID+0x700          | 0             | .......        | Length               | D0\~D1                                     | D2\~D3           | D4\~D5          | D6\~D7 | D8\~D11 | D12\~D15 | ....... |
| 12                | Error code    | System voltage | System temperature   | <p>D6 Enable status<br>D7 Brake status</p> | Current position | Current current | ...... |         |          |         |

**4. Usage Examples**

**IAP Online Update Flag (Required Operation)**

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x49  | 0x00 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x49  | 0x01 |

**Get Current Joint Status**

Command package:

| CAN-ID | DLC  |
| ------ | ---- |
| 0x601  | 0x00 |

Response package:

| CAN-ID           | DLC             | D0                 | D1            | D2           | D3   | D4   | D5   | D6   | D7   |
| ---------------- | --------------- | ------------------ | ------------- | ------------ | ---- | ---- | ---- | ---- | ---- |
| 0x701            | 0x10            | 0x00               | 0x00          | 0xFC         | 0x08 | 0xEA | 0x01 | 0x01 | 0x00 |
| Error Code       | System Voltage  | System Temperature | Enable Status | Brake Status |      |      |      |      |      |
| D8               | D9              | D10                | D11           | D12          | D13  | D14  | D15  |      |      |
| 0x61             | 0x0D            | 0x03               | 0x00          | 0xFA         | 0xFF | 0xFF | 0xFF |      |      |
| Current Position | Current Current |                    |               |              |      |      |      |      |      |

**Position Mode Control**

**(1) Set Working Mode to Position Mode**:

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x30  | 0x03 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x30  | 0x01 |

**(2) Joint Movement via Position Servo Command**:

After querying the current angle using the joint status query command, send a position servo command to move the joint within ±10°. For example, if the current angle is 20°, move the joint to 30°.

Command package:

| CAN-ID | DLC  | DATA | DATA | DATA | DATA |
| ------ | ---- | ---- | ---- | ---- | ---- |
| 0x201  | 0x04 | 0xE0 | 0x93 | 0x04 | 0x00 |

Response package:

| CAN-ID                                      | DLC           | D0         | D1   | D2   | D3   | D4   | D5   | D6   | D7   |
| ------------------------------------------- | ------------- | ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0x501                                       | 0x10          | 0xC0       | 0xFF | 0xFF | 0xFF | 0x00 | 0x00 | 0x00 | 0x00 |
| Current Current                             | Current Speed |            |      |      |      |      |      |      |      |
| D8                                          | D9            | D10        | D11  | D12  | D13  | D14  | D15  |      |      |
| 0x40                                        | 0x0D          | 0x03       | 0x00 | 0x01 | 0x00 | 0x00 | 0x00 |      |      |
| Current Position (Position before movement) | Enable Status | Error Code |      |      |      |      |      |      |      |

After obtaining the joint status again, the current joint angle should be within ±10° of the initial position.

**Current Mode Control**

**(1) Set Working Mode to Current Mode**:

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x30  | 0x01 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x30  | 0x01 |

**(2) Joint Movement via Current Servo Command**:

Send a current-servo command to move the joint according to the sign of the current value. A negative value moves the joint in the negative direction, while a positive value moves it in the positive direction; for example, use 500 mA.

Command package:

| CAN-ID | DLC  | DATA | DATA | DATA | DATA |
| ------ | ---- | ---- | ---- | ---- | ---- |
| 0x401  | 0x04 | 0xF4 | 0x01 | 0x00 | 0x00 |

Response package:

| CAN-ID                                      | DLC           | D0         | D1   | D2   | D3   | D4   | D5   | D6   | D7   |
| ------------------------------------------- | ------------- | ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0x501                                       | 0x10          | 0xF3       | 0xFF | 0xFF | 0xFF | 0x02 | 0x00 | 0x00 | 0x00 |
| Current Current                             | Current Speed |            |      |      |      |      |      |      |      |
| D8                                          | D9            | D10        | D11  | D12  | D13  | D14  | D15  |      |      |
| 0xBB                                        | 0xB0          | 0x09       | 0x00 | 0x01 | 0x00 | 0x00 | 0x00 |      |      |
| Current Position (Position before movement) | Enable Status | Error Code |      |      |      |      |      |      |      |

**Speed Mode Control**

**(1) Set Working Mode to Speed Mode**:

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x30  | 0x02 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x30  | 0x01 |

**(2) Joint Movement via Speed Servo Command**:

Send a speed-servo command to move the joint according to the sign of the speed value. A negative value moves the joint in the negative direction, while a positive value moves it in the positive direction; for example, use 5 RPM.

Command package:

| CAN-ID | DLC  | DATA | DATA | DATA | DATA |
| ------ | ---- | ---- | ---- | ---- | ---- |
| 0x301  | 0x04 | 0xC4 | 0x09 | 0x00 | 0x00 |

Response package:

| CAN-ID                                      | DLC           | D0         | D1   | D2   | D3   | D4   | D5   | D6   | D7   |
| ------------------------------------------- | ------------- | ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0x501                                       | 0x10          | 0xC0       | 0xFF | 0xFF | 0xFF | 0x00 | 0x00 | 0x00 | 0x00 |
| Current Current                             | Current Speed |            |      |      |      |      |      |      |      |
| D8                                          | D9            | D10        | D11  | D12  | D13  | D14  | D15  |      |      |
| 0x76                                        | 0x14          | 0x03       | 0x00 | 0x01 | 0x00 | 0x00 | 0x00 |      |      |
| Current Position (Position before movement) | Enable Status | Error Code |      |      |      |      |      |      |      |

**Clear Joint Error**

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x0F  | 0x01 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x0F  | 0x01 |

WARNING

After clearing the joint error, switch the working mode to position servo mode, send an enable command, and the joint will be successfully enabled.

**Set Joint Zero Position**

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x0E  | 0x01 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x0E  | 0x01 |

**Set Enable Status**

**Enable**：

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x0A  | 0x01 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x0A  | 0x01 |

**Disable**：

Command package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x01   | 0x03 | 0x02 | 0x0A  | 0x00 |

Response package:

| CAN-ID | DLC  | CMD  | INDEX | DATA |
| ------ | ---- | ---- | ----- | ---- |
| 0x101  | 0x03 | 0x02 | 0x0A  | 0x01 |

**Low-Power Mode Description**

After enabling low-power mode, the maximum power consumption of each joint does not exceed 80W.

Low-power mode is activated when the memory vector table address 0x69 is set to 1, and it is deactivated when set to 0 returning, to the normal joint state.

TIP

Supported only for joints WHJ10N/WHJ30/WHJ60 with firmware version 519 and later versions.

**End-Effector Mode Description**

In end-effector mode, when the memory vector table address 0x79 is set to 0, the end-effector is non-joint; when set to 1, the end-effector is in joint mode, functioning as a joint.

TIP

Supported only for joints WHJ10N/WHJ30/WHJ60 with firmware version 519 and later versions.

**Time-Sharing Power-On Mode Description**

In time-sharing power-on mode, when the memory vector table address 0x1f is set to 0, the joint power-on is delayed; when set to 1, the joint power-on is immediate without delay.

TIP

Supported only for joints WHJ10N/WHJ30/WHJ60 with firmware version 519 and later versions.

### Troubleshooting and Error Codes

Use the error categories and codes below to identify likely causes and select the recommended corrective action.

**Definition of Error Categories**

* **General Error**: Joint errors caused by the design of the robot system, which can return to normal use after resolution; or the customer can use them normally by resetting parameters or powering on again.
* **Severe Error**: Requires re-flashing of firmware or factory repair.

**Error Codes**

| No. | Error Code (Hexadecimal) | Error Code (Decimal) | Error Content                 | Causes                                                                                                                                                    | Handling Suggestions                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Category        |
| --- | ------------------------ | -------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| 1   | 0x0000                   | 0                    | Joint normal                  | -                                                                                                                                                         | Our joints can be used normally.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                 |
| 2   | 0x0001                   | 1                    | FOC error                     | FOC frequency is too high                                                                                                                                 | Please contact our technical support in a timely manner.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Severe          |
| 3   | 0x0002                   | 2                    | Overvoltage                   | Input voltage exceeds the voltage withstand range of the joint                                                                                            | Check if the voltage input is between 20-27V.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | General         |
| 4   | 0x0004                   | 4                    | Undervoltage                  | Input voltage is lower than the voltage withstand range of the joint                                                                                      | <p>1. Common in battery-powered situations: insufficient battery power, insufficient power output when the joint starts or moves quickly under high load.<br>2. Check the power output. It is recommended to use a switching power supply with 20-27V output, power above 600W, and with hiccup mode and 1S constant current output function for the robot arm's self-inspection and self-tuning after power-on.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | General         |
| 5   | 0x0008                   | 8                    | Over-temperature              | Joint temperature reaches the alarm temperature                                                                                                           | <p>1. The joint temperature reaches the over-temperature threshold of 90℃, please let it stand or power off to cool down.<br>2. It is recommended to check if the joint is overloaded or has collided.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | General         |
| 6   | 0x0010                   | 16                   | Startup failure               | The joint does not start normally                                                                                                                         | 1. Check the power output. It is recommended to use a switching power supply with 20-27V output, power above 600W, and with hiccup mode and 1S constant current output function for the robot arm's self-inspection and self-tuning after power-on.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | General         |
| 7   | 0x0020                   | 32                   | Encoder error                 | Joint self-inspection failure or inability to recognize the current angle                                                                                 | <p>1. If multiple joints of the robot arm have encoding errors, it is recommended to check the power output and restart the robot arm. This phenomenon is caused by insufficient power output, making the robot arm unable to perform normal self-inspection and self-tuning.<br>2. If a single joint has an encoder error, you can try to clear it; if it cannot be cleared, it may be due to excessive joint load, which causes an error after startup. It is recommended to reduce the load and power on again to solve the problem.<br>3. The continuous deviation between the encoder reading position and the previous data is greater than 1 degree (considering the output flange position offset if there is no hard brake).<br>4. The error cannot be eliminated and the driver board lights up blue (not visible externally), indicating an encoder error.<br>5. The target position sent by the upper computer exceeds the set limit position.</p> | General         |
| 8   | 0x0040                   | 64                   | Overcurrent                   | Instantaneous current is too large                                                                                                                        | <p>1. Check if the power supply and load are normal.<br>2. Check if there is an excessively large step in the position command causing excessive instantaneous current.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | General         |
| 9   | 0x0080                   | 128                  | Software error                | <p>1. Mismatch between hardware and software.<br>2. Current detection error.</p>                                                                          | <p>Please contact our technical support in a timely manner.<br>1. Re-flashing the corresponding firmware can solve the problem of hardware and software mismatch.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Severe          |
| 10  | 0x0100                   | 256                  | Temperature sensor error      | The temperature sensor fails to obtain the joint temperature normally                                                                                     | Please contact our technical support in a timely manner.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Severe          |
| 11  | 0x0200                   | 512                  | Position overrun error        | The current position of the joint exceeds the joint limit                                                                                                 | <p>Solution ideas:<br>1. Check the current joint angle on the single-joint upper computer.<br>2. Adjust the joint limit to be greater than the current angle.<br>3. Clear the joint error.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | General         |
| 12  | 0x0400                   | 1024                 | Invalid joint ID              | Incorrect joint ID                                                                                                                                        | <p>Enter the correct joint ID information.<br>1. The correct setting range for the joint ID is 1-7. If the joint ID is less than 1 or greater than 7, this error will occur.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | General         |
| 13  | 0x0800                   | 2048                 | Position tracking error       | <p>1. Position error tracking over-limit protection.<br>2. The difference between the target position and the current position exceeds the threshold.</p> | 1. The error angle is greater than the maximum following angle limit (the difference between the target motor position and the encoder reading position is greater than 80 degrees).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | General         |
| 14  | 0x1000                   | 4096                 | Current detection error       | Current sensor detection error during power-on                                                                                                            | <p>Please contact our technical support in a timely manner.<br>1. The current detected by the circuit board is outside the correct range (most likely a circuit board problem).</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Severe Error    |
| 15  | 0x2000                   | 8192                 | Brake release failure         | <p>1. The joint brake is not released normally.<br>2. The internal Hall signal is incorrect.</p>                                                          | <p>1. It is recommended to check the power output. Use a switching power supply with 20-27V output, power above 600W, and with hiccup mode and 1S constant current output function for the robot arm's self-inspection and self-tuning after power-on.<br>2. The motor is stuck and cannot rotate, resulting in brake release failure. Please contact our technical support in a timely manner.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Severe /General |
| 16  | 0x4000                   | 16384                | Position command step warning | The error between the current position and the target position is large                                                                                   | <p>Often occurs during transparent transmission. It is recommended to check if the transparent transmission trajectory is smooth and the communication cycle is stable.<br>1. The angle between the target position sent by the upper computer and the existing position of the motor is greater than 10 degrees.<br>2. FOC state error.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | General         |
| 17  | 0x8000                   | 32768                | Multi-turn joint lost turns   | Encoder battery is low                                                                                                                                    | The end joint of the robot arm uses a multi-turn encoder. Check if the battery interface is loose and if the battery is low.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Severe          |

### Official Documentation Sources

The consolidated content above follows the official RealMan Developer Center pages listed below.

* [Introduction of WHJ Series Joint](https://develop.realman-robotics.com/en/joints/parameter/)
* [Joint Electrical Instructions](https://develop.realman-robotics.com/en/joints/electricalInstructions/)
* [Single-Joint Host Computer: Environmental Preparation](https://develop.realman-robotics.com/en/joints/guide/SinglejointToolUserManual/singlejointTool/)
* [Single-Joint Host Computer: Main Page Navigation](https://develop.realman-robotics.com/en/joints/guide/SinglejointToolUserManual/realtimeNavigation/)
* [Single-Joint Host Computer: Waveform Navigation](https://develop.realman-robotics.com/en/joints/guide/SinglejointToolUserManual/waveformNavigation/)
* [Single-Joint Host Computer: Information Navigation](https://develop.realman-robotics.com/en/joints/guide/SinglejointToolUserManual/informationNavigation/)
* [Single-Joint Host Computer: CAN Information Navigation](https://develop.realman-robotics.com/en/joints/guide/SinglejointToolUserManual/caninformation/)
* [Single-Joint Host Computer: Use Case](https://develop.realman-robotics.com/en/joints/guide/SinglejointToolUserManual/usecase/)
* [WHJ10 Series Specifications](https://develop.realman-robotics.com/en/joints/parameter/WHJ10/)
* [WHJ30 Series Specifications](https://develop.realman-robotics.com/en/joints/parameter/WHJ30/)
* [WHJ60 Series Specifications](https://develop.realman-robotics.com/en/joints/parameter/WHJ60/)
* [WHJ10 Torque Series Specifications](https://develop.realman-robotics.com/en/joints/parameter/WHJTorqueSeriesJoint/WHJTorque10/)
* [WHJ30 Torque Series Specifications](https://develop.realman-robotics.com/en/joints/parameter/WHJTorqueSeriesJoint/WHJTorque30/)
* [WHJ60 Torque Series Specifications](https://develop.realman-robotics.com/en/joints/parameter/WHJTorqueSeriesJoint/WHJTorque60/)
* [Power Bleeding Module](https://develop.realman-robotics.com/en/joints/usermanualforpowerdischargemodule/)
* [CANFD Protocol Introduction](https://develop.realman-robotics.com/en/joints/CANFD/explanation/)
* [CANFD Memory Control Table](https://develop.realman-robotics.com/en/joints/CANFD/memoryControlTable/)
* [CANFD Usage Demo](https://develop.realman-robotics.com/en/joints/CANFD/usageDemo/)
* [FAQ: Error Codes](https://develop.realman-robotics.com/en/joints/faq/errorcode/)
