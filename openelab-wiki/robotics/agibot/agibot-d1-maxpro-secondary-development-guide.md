# AgiBot D1 MaxPro Secondary Development Guide

### AGIBOT D1 MaxPro IP67 Quadruped Robot with 50 kg Payload

{% embed url="https://openelab.io/products/agibot-d1-maxpro-robot-dog" %}

**Applicability:** This guide is specific to D1 MaxPro. Select an SDK package that matches the software version installed on the robot.

Document Revision Record

| Revision date | Revision                                                                                                                                                                                                                                                                                                                                                            | sdk version |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| 2025-12-25    | • Optimizing the success of autonomous stakes — increasing the SlickToCrawlMode                                                                                                                                                                                                                                                                                     | V2.0.5      |
| 2026-01-16    | New Part interface.SDK Adds new anomalous interface GetAllAllAlerts().sdk Adds new mileage interfaces GetOdometry().sdk Adds new charge detection interfaces between GetRobotChargingSate().sdk Adds new capture joint angle \ angular speed interface between GetJointSate().sdk Adds new IMU accelerator interface between GetImuLinearAcceleration()             | V2.0.6      |
| 2026-01-24    | • Rehabilitation of kernel-driven bugs to the application layer • Controls increase the problem of receiving kernel error automatic grounding and red light alerts • autoboot updating BAT for 2s and GPS for 2s • Restoration of SDK control has been released to the remote controller, which, by pressing B, will enable dogs to continue with the SDK directive | V2.0.7      |

### 1. Product Introduction

#### 1.1 Product Overview

D1 MaxPro, a four-foot robot with 3 electric machines on each leg, with 12 degrees of freedom and motor skills, such as walking, running, climbing stairs, crossing trenches, etc. The main features of this product are high load capacity, continuous navigation and adaptive capacity in complex terrain. At the same time, the product has opened up motion control algorithms for the development of SDK and communication protocols, allowing users to develop twice as needed, and has made significant progress in the development of several key functions and applications:

#### 1. Burden capacity: The main heavy load characteristic, with a long load of up to 50 kg and an instant load of up to 100 kg, is 2.5 times greater than in previous generations and meets heavy load demand scenarios such as material transport, industrial handling, etc.

2. Autonomous patrolling and environmental awareness: autonomous patrolling capability can be achieved by relying on LiDAR, and remote deployment and image retrieval through the 4G network. At the same time, LiDARs, head cameras, IMUs and GPS are a rich sensor capable of providing a full sense of the environment in complex environments, building maps and charting paths, and adapting to different scenarios such as public security patrols, water patrols and oil inspections.
3. Motionability: An excellent motor flexibility to move up and down the 45° stairs, a steady climb over the industrial stairs, and a strong ability to cross the 30cm barrier of a single step. The fall recovery mechanism matures, falls up for less than 20 seconds, and is able to quickly resume operations in complex terrain or unexpected conditions. Its air-borne speed is 3 m/s, allowing rapid response to sudden mission demands, deep into complex scenes and operational blind areas.
4. Environmental adaptation: Having IP67 industrial-grade protection, operating normally in broad temperature zones - 20°C to 55°C, and in water-related depths - 20 cm, without fear of extreme heat and wind and weather, ensuring steady operation under many harsh natural conditions.

#### Resuscitation security: Battery power of 2160 Wh, load renewal time increase of 28%, and battery support for rapid on-site dismantling, provision of robust continuity guarantees for special missions and emergency situations in industrial applications, reduction of downtime and increased efficiency.

#### 1.2 Package Contents

![Photo 55.png](<../../.gitbook/assets/assetsfigure-001 (3).png>)

#### 1.3 Hardware composition

![Photo 56.png](<../../.gitbook/assets/assetsfigure-002 (3).png>)

#### 3D LiDAR

| Lines                  | 96                                                              | Horizontal field of view    | 360°         |
| ---------------------- | --------------------------------------------------------------- | --------------------------- | ------------ |
| Laser wavelength       | 940 nm                                                          | Vertical field of view      | 0\~90°       |
| Laser security level   | Class1, eyes safe.                                              | Horizontal Angle Resolution | 0.4°         |
| Range capabilities     | 60 m(30 m @10% NIST)                                            | Vertical angle resolution   | 0.947°       |
| Blind                  | 0.1 m                                                           | Precision (typical)         | 1.5 cm (1 σ) |
| Turn!                  | 600                                                             | Frame Rate                  | 10 Hz        |
| Point                  | 856,320 pts/s (one-round mode), 1,712,640 pts/s (two-back mode) |                             |              |
| Ethernet transfer rate | 100 Base-TX                                                     |                             |              |
| Output data protocol   | UDP Packets Over Ethernet                                       |                             |              |

Camera

| Image Sensor                   | 1/2.9 inch CMOS                                                                             |
| ------------------------------ | ------------------------------------------------------------------------------------------- |
| Maximum Resolution             | 1920 x 1080                                                                                 |
| Output Data Format             | MJPEG/YUV2                                                                                  |
| Pixels Size                    | 2.8umX2.8um                                                                                 |
| Camera control                 | saturation;comparison; sharpness                                                            |
| White balance/exposure         | Auto                                                                                        |
| Work voltage                   | DC 5.0V                                                                                     |
| Work current.                  | 150 mA                                                                                      |
| Storage temperature & humidity | -40~~80 ℃/0~~90RH                                                                           |
| Working temperature            | -20℃—+70℃                                                                                   |
| Driver Standard                | UVC                                                                                         |
| Interface Mode                 | USB2.0                                                                                      |
| UVC/OTG                        | Support                                                                                     |
| Resolution and frame           | MJPEG: 1080P\~30FPS                                                                         |
| Compatibility system           | WindowsXP/SP2/Vista/7.0/8.1/Win10/seven/MacAndroid, Linux and embmbedded operating systems, |
| Focus                          | Focus                                                                                       |

Battery

| Standard voltage                     | 48V                                                                                                                                                                                                                |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Battery grouping method              | 9P13S                                                                                                                                                                                                              |
| Name Capacity                        | 45Ah                                                                                                                                                                                                               |
| Minimum capacity                     | 45Ah (temperature: 25°C ± 5°C, humidity: 65% ± 20% RH, discharge capacity as of voltage: 2.75V/section 0.2C).                                                                                                      |
| Standard charge (recommended)        | Constant current charge phase: 4A constant current charge to 4.2V/Section (note: non-charging electrical current). Recharge phase: 54.6 V constant charge. Trickle up charging phase: 200 mA until end of current. |
| Standard discharge current           | 18A (0.4C), ambient temperature 25°C                                                                                                                                                                               |
| Maximum continuous discharge current | 50 A (T≥-20°C) ambient temperature 25°C                                                                                                                                                                            |
| Battery charge voltage               | 54.6V                                                                                                                                                                                                              |
| Battery working voltage              | 39\~54.6V (0.5C), ambient temperature 25°C                                                                                                                                                                         |
| Standard battery charge current      | 9A (0.2C ambient temperature 25°C)                                                                                                                                                                                 |
| Overload protection.                 | Single Section 3.00±80mV                                                                                                                                                                                           |
| The charge is off.                   | Single Section 2.75±0.05V                                                                                                                                                                                          |
| Transport voltage                    | ≥48V (test at delivery)                                                                                                                                                                                            |
| Interception                         | ≤20mΩ                                                                                                                                                                                                              |
| Charge temperature range             | 0～+45ºC                                                                                                                                                                                                            |
| Emission temperature range           | -20～+60ºC                                                                                                                                                                                                          |
| Storage temperature range            | -20～+35 ºC                                                                                                                                                                                                         |
| Cycle life                           | A thousand times.                                                                                                                                                                                                  |
| Storage life                         | 2 years (25°C); 2 months (45°C)                                                                                                                                                                                    |

Charge stakes

| Item                                | Parameters |
| ----------------------------------- | ---------- |
| Enter voltage                       | 220V       |
| Output voltage                      | 54.5V      |
| Output current                      | 10A        |
| Control the precision of the pillar | +-3cm      |

#### 1.4 Product Specifications

| Classification                     | Specifications                                                                                                                                                                                                 | Annotations                                                                                            |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Basic information                  | Material Information                                                                                                                                                                                           | Aluminium alloys + high-intensity engineering plastics                                                 |
| Standing (long x wide x high)      | 1230mm×530mm×730mm                                                                                                                                                                                             |                                                                                                        |
| Punctuation (long x high)          | 1313mm×530mm×300mm                                                                                                                                                                                             |                                                                                                        |
| Whole weight (including batteries) | 68kg                                                                                                                                                                                                           |                                                                                                        |
| Freedom                            | The whole plane is 12 degrees free, one leg free 3.                                                                                                                                                            |                                                                                                        |
| Working temperature                | -20℃ \~55℃                                                                                                                                                                                                     |                                                                                                        |
| Protection level                   | IP67                                                                                                                                                                                                           |                                                                                                        |
| Battery                            | PQ45Ah, voltage 48V±2V                                                                                                                                                                                         |                                                                                                        |
| Charge duration                    | 4.5h (10-90% electricity)                                                                                                                                                                                      |                                                                                                        |
| Time of renewal.                   | 5.5h empty, 2h and above in load 20kg                                                                                                                                                                          |                                                                                                        |
| Keep going.                        | Empty 10km                                                                                                                                                                                                     |                                                                                                        |
| Performance parameters             | Keep walking.                                                                                                                                                                                                  | 0-1.2m/s                                                                                               |
| Maximum speed                      | 3m/s                                                                                                                                                                                                           |                                                                                                        |
| Rating Load                        | 50kg                                                                                                                                                                                                           |                                                                                                        |
| Climbing the stairs.               | 30cm                                                                                                                                                                                                           |                                                                                                        |
| Maximum slope angle                | 45°                                                                                                                                                                                                            |                                                                                                        |
| Organ section parameters           | Maximum joint twist                                                                                                                                                                                            | Max. 300N·m., software limit 180N·m.                                                                   |
| Joint motion space (airframe)      | -45°\~45°                                                                                                                                                                                                      |                                                                                                        |
| Joint motion space (legs)          | -200°\~20°                                                                                                                                                                                                     |                                                                                                        |
| Joint motion space (legs)          | 30°\~160°                                                                                                                                                                                                      |                                                                                                        |
| Sensor Unit                        | Laser radar                                                                                                                                                                                                    | A 96-line LiDAR with an angle of 360° \* 90°, with a diameter range of 120 m and a precision of 1.5 cm |
| Wide-angle Camera                  | A wide-angle camera, 2 million pixels industrial, field of view: DFOV 150°, HFOV 130°, VFOV 73°                                                                                                                |                                                                                                        |
| IMU                                | Number one, car code.                                                                                                                                                                                          |                                                                                                        |
| Function List                      | Standard Actions                                                                                                                                                                                               | Stand, get down, stop, unload, get up and down the stairs, get over the barrier.                       |
| Real-time image transfer           | Support                                                                                                                                                                                                        |                                                                                                        |
| Secondary development              | Currently SDK supports the provision of SDK packages based on TCP and ROS communications, X86 and ARM architecture                                                                                             |                                                                                                        |
| Communications function            | Support WIFI6.0, Bluetooth 5.2, 4G modules optional                                                                                                                                                            |                                                                                                        |
| Functional Extension Interface     | Communications interfaces are Gggne&#x74;_&#x33;, USB 3.&#x30;_&#x32;, Ggnet\*1, serial. Power interfaces 12V, 24V, 48V, maximum output power 720w. Charge interface to support straight plugging of batteries |                                                                                                        |
| Spare parts                        | Adapter                                                                                                                                                                                                        | Mark                                                                                                   |
| Battery charge switch.             | Mark                                                                                                                                                                                                           |                                                                                                        |
| Remote control                     | With a screen remote, with a manual stop.                                                                                                                                                                      |                                                                                                        |
| Autocharge stakes                  | Selection                                                                                                                                                                                                      |                                                                                                        |

#### 1.5 Artificial parameters

| Type                   | Parts     | Parameters | Value (twice: Nm; rotation: RPM; weight: Kg; power: kw) |
| ---------------------- | --------- | ---------- | ------------------------------------------------------- |
| D1 MaxPro              | Airframe. | Max.       | 180                                                     |
| Maximum rotation speed | 136       |            |                                                         |
| Weight                 | 1.407     |            |                                                         |
| Legs.                  | Max.      | 300        |                                                         |
| Maximum rotation speed | 147       |            |                                                         |
| Weight                 | 2.57      |            |                                                         |
| Legs.                  | Max.      | 300        |                                                         |
| Maximum rotation speed | 114       |            |                                                         |
| Weight                 | 2.57      |            |                                                         |

#### 1.6 Plasma pre-positioned

• Quadruped robots have self-adaptation loads with loads ranging from 0 to 50 kg;

• The quadruped robot machine has the corresponding screwhole, and the user can make his/her own fittings from the screwhole, which can be used to fix the loading equipment, the size of which is as follows:

![Photo 57.png](<../../.gitbook/assets/assetsfigure-003 (1).png>)

| The load will require the quadruped robot to be on the ground, load the load, secure it, and keep the quadruped robot on the stand, which will automatically recognize the load weight, wait until the load mass recognition of 3s is complete and other operations can be performed. |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### 1.7 Electrical Expansion Interfaces

**1.7.1 Definition of back interfaces**

![Photo 58.png](<../../.gitbook/assets/assetsfigure-004 (3).png>)

| Note: The back interface consists mainly of two modules, headline and tail power. |
| --------------------------------------------------------------------------------- |

| Serial number | Interface                    | Interface Type              | Plugin                  | Number | Functions                                        |
| ------------- | ---------------------------- | --------------------------- | ----------------------- | ------ | ------------------------------------------------ |
| 1             | Double-light cloud interface | M12A-12P Mother             | M12A-12P Head           | 1      | +24V/3A power source                             |
| 2             | Laser radar interface        | M12A-8P mother              | M12A-8P Head of Office  | 1      | +24V/3A power source                             |
| 3             | Outreach Network Interface   | M12A-17P mother             | M12A-17P Head of Office | 1      | +24V/3A power source                             |
| 4             | Extension Type-C interface   | Type-C waterproofing plugin | USB Type-C              | 1      | Expand USB 3.1 10Gbps interface                  |
| 5             | Power interface              | M12K Mother                 | M12K Head               | 1      | Power for loading equipment 12,24,48V/10A output |

#### 1. Definition of the head connector box M12A-12P parent carrier plug-in interface

![Photo 59.png](<../../.gitbook/assets/assetsfigure-005 (3).png>)

| M12A mother header serial number | Definitions   | Webline Crystal Number | Functions                 |
| -------------------------------- | ------------- | ---------------------- | ------------------------- |
| 1                                | 24V plus      |                        | 24V power source positive |
| 2                                | 24V Negative  |                        | 24V power negative pole   |
| 3                                | 24V Negative  |                        | 24V power negative pole   |
| 4                                | RX+           | 1                      | Data Reception Backend    |
| 5                                | RX-           | 2                      | Data Reception Negative   |
| 6                                | TX+           | 3                      | Data Reception Backend    |
| 7                                | TX-           | 6                      | Data Reception Negative   |
| 8                                | Empty         |                        |                           |
| 9                                | 24V plus      |                        | 24V power is positive.    |
| 10                               | Empty         |                        |                           |
| 11                               | 12 V plus.    |                        | 12V power is positive.    |
| 12                               | 12V negative. |                        | 12V power negative.       |

#### 2. Definition of the head connector box M12A-8P parent carrier plug-in interface

![Image 60.png](<../../.gitbook/assets/assetsfigure-006 (3).png>)

| M12A mother's number. | Definitions  | Webline Crystal Number | Functions                 |
| --------------------- | ------------ | ---------------------- | ------------------------- |
| 1                     | 24V plus     |                        | 24V power source positive |
| 2                     | RX+          | 1                      | Data Reception Backend    |
| 3                     | RX-          | 2                      | Data Reception Negative   |
| 4                     | TX+          | 3                      | Data Reception Backend    |
| 5                     | TX-          | 6                      | Data Reception Negative   |
| 6                     | Empty        |                        |                           |
| 7                     | Empty        |                        |                           |
| 8                     | 24V negative |                        | 24V power negative pole   |

#### 3. Definition of the end connector box M12A-17P parent carrier plug-in interface

![Image 61.png](<../../.gitbook/assets/assetsfigure-007 (3).png>)

| M12A mother's number. | Definitions   | Webline Crystal Number | Functions               |
| --------------------- | ------------- | ---------------------- | ----------------------- |
| 1                     | 48 V plus.    |                        | 48V positive.           |
| 2                     | RX+           | 1                      | Data Reception Backend  |
| 3                     | RX-           | 2                      | Data Reception Negative |
| 4                     | TX+           | 3                      | Data Reception Backend  |
| 5                     | TX-           | 6                      | Data Reception Negative |
| 6                     | 12 V plus.    |                        | 12V power is positive.  |
| 7                     | 12V negative. |                        | 12V power negative.     |
| 8                     | 12 V plus.    |                        | 12V power is positive.  |
| 9                     | 12V negative. |                        | 12V power negative.     |
| 10                    | 24V plus      |                        | 24V power is positive.  |
| 11                    | 24V negative  |                        | 24V power negative.     |
| 12                    | 24V plus      |                        | 24V power is positive.  |
| 13                    | 24V negative  |                        | 24V power negative.     |
| 14                    | 48 V plus.    |                        | 48V positive.           |
| 15                    | 48V negative. |                        | 48V power negative.     |
| 16                    | 48 V plus.    |                        | 48V positive.           |
| 17                    | 48V negative. |                        | 48V power negative.     |

#### 4. Definition of the tail source M12K parent interface

![Image 62.png](<../../.gitbook/assets/assetsfigure-008 (3).png>)

| M12A mother's number. | Definitions      | Webline Crystal Number | Functions                  |
| --------------------- | ---------------- | ---------------------- | -------------------------- |
| 1                     | 48 V plus.       |                        | 48V positive.              |
| 2                     | 48V negative.    |                        | 48V power negative.        |
| 3                     | 24V plus         |                        | 24V power is positive.     |
| 4                     | 24\12 V negative |                        | 24\12V power negative pole |
| 5                     | 12 V plus.       |                        | 12V power is positive.     |

**1.7.2 Definition of left interface**

![Photo 63.png](<../../.gitbook/assets/assetsfigure-009 (3).png>)

| Serial number | Device Name            | Model                      | Functions                                                       |
| ------------- | ---------------------- | -------------------------- | --------------------------------------------------------------- |
| 1             | Debug Interface        | DB15 Mother                | Electrical CAN Diagnosis, Battery CAN Diagnosis, Debugging Zero |
| 2             | Wi-Fi antenna          | 2.4G                       | Wi-Fi and Master Board Communication                            |
| 3             | Bluetooth antenna      |                            | Wireless Bluetooth and Master Board Communication               |
| 4             | Pressure balance valve | M12                        | Balance internal and external pressure                          |
| 5             | typepec interface      | E10T-FT3-PWF/MT3-NWA-xxFPC | typepec interface and console communication                     |
| 6             | Charge mouth.          | E13T-P2B-PPF-01            | 48V charge mouth                                                |
| 7             | Net                    | E13T-FR5-PRF-180           | 100 mega/debug gateways                                         |

### II. System architecture

#### 2.1 AGI MaxPro system architecture

![Photo 64.png](<../../.gitbook/assets/assetsfigure-010 (3).png>)

Quadruped robot.

#### 1. MQTT Clinic is responsible for MQTT-based communications with cloud platforms, which include OTA, status reports, remote controller, etc.;

#### 2. WebRTC Client communicates with the turns/stun services of the APP and cloud platforms, which are responsible for video push, cloud extraction, etc.;

#### 3. RC Client communicates with remote controllers and achieves wireless remote controller;

#### 4. HTTP CLient communicates on the side of the platform, enabling upgrade package downloads, log uploads, map uploads, etc.

#### 5. Video feed via RTSP

#### 6. Internal communications using ROS Topic

Cloud Platform

#### 1. mqt for long-linking when quadruped robots are electrocuted to receive reported state, heartbeat, and direction (e.g. OTA, WebRTC)

#### 2. Reestful API provides platform services externally, as well as user and equipment management functions for APP

#### 3. turns/stun service to create a WebRTC-based point-to-point connection to achieve a video stream at p2p (when no point-to-point is possible) Company

Other Organiser

#### 4. Allegation systems/robots management platforms provide robotic life cycle management, OTA, map editing, remote monitoring/control, missions Pipe

Equivalent functions;

APP

#### 1. User management/equipment management module: Communication with the Platform through Restful API. Responsible for user management, equipment management and user and installation

Preparation of relationship management;

#### Remote control: provision of remote controller based on MQTT signal communications

#### 3. Pull services: providing point-to-point push services based on WebRTC

Remote control

#### Remote control: Communication with the equipment end-end RC Clinic, providing 2.4 GHz-based wireless remote controller;

#### 2. Pull: video pull based on RTSP;

#### 3. Charts: Remotely controlled side launches/terminations achieved by push;

#### 4. Map editing: functions of remote controller end map editing, including map displays, rotations,

(b) Scale, virtual wall editing, distribution, etc.;

#### 2.2 Hardware architecture

![Photo 65.png](<../../.gitbook/assets/assetsfigure-011 (2).png>)

### III. SDK development guide

#### 3.1. Introduction to SDK

• This document describes D1 MaxPro's software development toolkit (SDK), which covers the capabilities of machines and dogs (including high-level motion control, bottom power/width control, graphics, clouds, mileage, etc.) and facilitates secondary development by users with a certain development capability.

• Each chapter presents the method of calling different service interfaces, standard format definitions for data input/output and examples of some functional development.

• The definition of interface will vary with the development of the mass product, depending on the latest version of the interface definition document.

• The SDK program has a specific protocol for communication with the dog's own program, so there are differences between different versions of the SDK program and the dog's own program. Select the corresponding version of the SDK program according to the device version. If conditions permit, it is recommended that the internal dog program be updated to the latest version to achieve better compatibility.

• When the SDK interface is controlled, the entire state is designed by a secondary developer and no additional intervention and state jumps are performed by the HMO.

• When running SDK, ensure that the system is adequately resourced, otherwise there may be a failure of the movement control module

• Programming languages: current support for C++ development, not for other programming languages

#### 3.2 Environmental dependency

Recommended development on Ubuntu 20.04, not supporting Mac, Windows

• High-level development, sdk, not required to install the ros1 system

• Bottom development, sdk, must install the ros1 system

#### 3.3 Network configuration

• Users' development computers can connect machines and dogs through wireless, cable and typeC mouths, recommending the use of wired connections

• Note that users develop computer IPs without setting them the same as quadruped robots, avoiding conflicts

• Once the setup is complete, the IP for computer development can be used to verify network connectivity through the ping command

| Network Interface | Machine Dog IP address | DHCP  |
| ----------------- | ---------------------- | ----- |
| Wireless network  | 192.168.12.1           | Yeah. |
| Wireless Network  | 192.168.144.3          | None  |
| Type-C            | 192.168.55.1           | None  |

| wfi name: lxai (after machine number eg:lxaic2-3) Wi-Fi password: lxai2024 |
| -------------------------------------------------------------------------- |

The equipment provides ssh login, which allows the device to login via ssh when a connection to the device is created by wireless or wired

| Plain Text #wireless connection ssh jetson@192.168.12.1 # password: lxai2023 #wireline connection ssh jetson@192.168.143 # password: lxai2023 #type-C mouth link ssh jetson@192.168.55.1 # password: lxai2023 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### 3.4 sdk access

**3.4.1 Version queries**

| TOML ssh jetson@192.168.144.3 #cipher: lxi2023cat Linx/active/versions.json |
| --------------------------------------------------------------------------- |

**3.4.2 Access to sdk versions of corresponding solidware**

way1: Please send a screenshot to your technical support colleagues for the corresponding version of sdk after searching for the version number Package

Go: Get it through the github address below

| Plain Text git clone https://github.com/AgibotTech/Agibot\_D1\_MaxPro.git |
| ------------------------------------------------------------------------- |

| Note: As sdk is continuously being upgraded, please refer to SDK corresponding to the firmware version |
| ------------------------------------------------------------------------------------------------------ |

#### 3.5 SDK installation and compilation

#### Case1 Upper sdk installation

Different sdk files will be provided depending on whether the ros1 system is installed in the user development environment

This is the directory where the zip file is unplugged:

![Photo 66.png](<../../.gitbook/assets/assetsfigure-012 (2).png>)

Execute the following commands, and when compiled successfully, the demoo program high level demo.cpp

| Bash make cleanmake -j6./high\_level\_demo |
| ------------------------------------------ |

The zip file unpressed without the ros1 system is the following directory:

![Image 67.png](<../../.gitbook/assets/assetsfigure-013 (2).png>)

Execute the bild.sh command and then run the available demo program high level remote tcp client test.cpp

| Bash./build.shcd build/./high\_level\_remote\_tcp\_client\_test |
| --------------------------------------------------------------- |

#### Case2 Bottom sdk installation

Unlike senior sdk, the bottom sdk does not rely on dynamic library development, and users simply have to write their own programs, subscribe to them

```
rt/lowstateAnd publishrt/lowcmdThese two topics can be controlled.
```

### IV. Introduction to API Functions

#### 4.1 Introduction to the High Lever function

The upper motion control interface achieves control over the attitude, speed, walking, specific actions, etc. of the quadruped robot, and can also access the state of the quadruped robot.

**4.1.1 Stand**

| Function Name      | Standup                                                                 |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t Standup()                                                      |
| Function Overview  | Stand!                                                                  |
| Parameters         | None                                                                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            |                                                                         |

**4.1.2 Get down!**

| Function Name      | Getdown                                                                 |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t Getdown()                                                      |
| Function Overview  | Get down!                                                               |
| Parameters         | None                                                                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            |                                                                         |

**4.1.3 Zero Force Rectangular Mode**

| Function Name      | ZeroTorque                                                              |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t ZeroTorque()                                                   |
| Function Overview  | Zero Force Rectangular Mode                                             |
| Parameters         | None                                                                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            |                                                                         |

**4.1.4 Interdiction**

| Function Name      | Damp                                                                    |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t Damp()                                                         |
| Function Overview  | Stop!                                                                   |
| Parameters         | None                                                                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            |                                                                         |

**4.1.5 Enhanced learning model transition**

| Function Name      | SwitchToRLMode                                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| Function Prototype | int32\_t SwitchToRLMode(bool val)                                                                                        |
| Function Overview  | Switch to Enhanced Learning Mode                                                                                         |
| Parameters         | val: Set true for opening, false for closing.                                                                            |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned.                                              |
| Remarks            | For complex terrain such as stairs, slopes, grasslands, sands, etc., there is a need to switch to enhanced learning mode |

**4.1.6 Movement**

| Function Name      | Move                                                                                                                                                                                                                                    |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t Move(double lm, double vm, double lrm)                                                                                                                                                                                         |
| Function Overview  | Move back and forth                                                                                                                                                                                                                     |
| Parameters         | Im: lateral movement (m/s): \[0,04] (m/s) vm: horizontal right (-0.4,0] (m/s) vm: backward movement: \[0,1.5] (m/s) backward movement: (-0.5,0] (m/s) lrm: left and right turn to left: \[0,0.5 (rad/s) turn to right: (-0.5,0] (rad/s) |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code.                                                                                                                                                                 |
| Remarks            | Keep moving. Everybody call StopMove.                                                                                                                                                                                                   |

**4.1.7 Overturn**

| Function Name      | Rotate\_up\_and\_down                                                       |
| ------------------ | --------------------------------------------------------------------------- |
| Function Prototype | int32\_t Rotate\_up\_and\_down(float ang)                                   |
| Function Overview  | Overlooking                                                                 |
| Parameters         | +: Angle (14,11) degrees - x indicates anometric x x x indicates aometric x |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code.     |
| Remarks            |                                                                             |

**4.1.8 Stop sports**

| Function Name      | StopMove                                                                |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t StopMove()                                                     |
| Function Overview  | Stop moving.                                                            |
| Parameters         | None                                                                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            | Set speed command zero.                                                 |

**4.1.9 Access to state of motion**

| Function Name      | GetActionStatus                                                                                                                                                                                                                                                                              |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t GetActionStatus()                                                                                                                                                                                                                                                                   |
| Function Overview  | Get the machine's motion state                                                                                                                                                                                                                                                               |
| Parameters         | None                                                                                                                                                                                                                                                                                         |
| Return value       | Detachment status: 0; return to standing action and automatically switch to balanced station after completion: 2 balanced station status: 3; detoxification status: 5; walking in progress: 6; automatically convert detoxification status after completion of the grounding: 7; unknown: 1; |
| Remarks            |                                                                                                                                                                                                                                                                                              |

**4.1.10 Move specified distance (back and forth)**

| Function Name      | MoveForward                                                             |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t MoveForward(float distance)                                    |
| Function Overview  | Move the specified distance back and forth                              |
| Parameters         | Distance: Moving distance                                               |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            | To be achieved                                                          |

**4.1.11 Move specified distance (right and left)**

| Function Name      | MoveSideways                                                            |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t MoveSideways(float distance)                                   |
| Function Overview  | Move the specified distance around                                      |
| Parameters         | Distance: Moving distance                                               |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            | To be achieved                                                          |

**4.1.12 End movement**

| Function Name      | FinishMovement                                                          |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t FinishMovement()                                               |
| Function Overview  | End move action                                                         |
| Parameters         | None                                                                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            | To be achieved                                                          |

**4.1.13 Set Body Height**

| Function Name      | SetHeight                                                               |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t SetHeight(float height)                                        |
| Function Overview  | Set Body Height                                                         |
| Parameters         | Height: quadruped robot height, range \[0.38, 0.58]m                    |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            |                                                                         |

**4.1.14 Setting speed**

| Function Name      | SetSpeed                                                                |
| ------------------ | ----------------------------------------------------------------------- |
| Function Prototype | int32\_t SetSpeed(float speed)                                          |
| Function Overview  | Set Speed                                                               |
| Parameters         | Speed: The speed at which the dog runs                                  |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code. |
| Remarks            |                                                                         |

**4.1.15 Access to moving speed**

| Function Name      | GetSpeed                                  |
| ------------------ | ----------------------------------------- |
| Function Prototype | float GetSpeed()                          |
| Function Overview  | Call speed of successful return operation |
| Parameters         | None                                      |
| Return value       |                                           |
| Remarks            | Xyz axle velocity calculations            |

**4.1.16 Access to tilt angles**

| Function Name      | GetAngle                                                                                              |
| ------------------ | ----------------------------------------------------------------------------------------------------- |
| Function Prototype | float GetAngle()                                                                                      |
| Function Overview  | Get tilt angle                                                                                        |
| Parameters         | None                                                                                                  |
| Return value       | The angle calling the successful return to the robot dog leans up to 14 over the maximum angle to 11. |
| Remarks            | Negative values are overlooking, positive values are overlooking and range taken \[14,11]             |

**4.1.17 Acquiring inverted height**

| Function Name      | GetHeight                                          |
| ------------------ | -------------------------------------------------- |
| Function Prototype | float GetHeight()                                  |
| Function Overview  | Get Body Height                                    |
| Parameters         | None                                               |
| Return value       | Call for successful return to the actual HB height |
| Remarks            |                                                    |

**4.1.18 Retrieving moving distance (right and left)**

| Function Name      | GetSideways                                             |
| ------------------ | ------------------------------------------------------- |
| Function Prototype | float GetSideways()                                     |
| Function Overview  | Get left and right moving distance                      |
| Parameters         | None                                                    |
| Return value       | Call successful back to quadruped robot left and right. |
| Remarks            | To be achieved                                          |

**4.1.19 Access to mobile distance (back and forth)**

| Function Name      | GetForward                                                |
| ------------------ | --------------------------------------------------------- |
| Function Prototype | float GetForward()                                        |
| Function Overview  | Get back and forth moving distance                        |
| Parameters         | None                                                      |
| Return value       | Called successful back to quadruped robot moving distance |
| Remarks            | To be achieved                                            |

**4.1.20 Parameter adjustment mode**

| Function Name      | ParameterAdjustmentMode                                                                                                                                        |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t ParameterAdjustmentMode(bool flag)                                                                                                                    |
| Function Overview  | Parameter Adjustment Mode                                                                                                                                      |
| Parameters         | flag: Set the true for opening, false for closing.                                                                                                             |
| Return value       | Call successfully returns 0, otherwise returns the relevant error code.                                                                                        |
| Remarks            | Sets the height and speed to be effective only if you set the interface to True. Set to false quadruped robot speed and height will restore the default status |

**4.1.21 Acquisition of mechanical dog status**

| Function Name      | GetRobotStatus                                                                                                                                                                                 |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Prototype | struct Robotstate GetRobotStatus()                                                                                                                                                             |
| Function Overview  | Get Machine Dog Status                                                                                                                                                                         |
| Parameters         | None                                                                                                                                                                                           |
| Return value       | Successfully returned to electrical temperature {double diver temperature \[12]; // / Electric temperature 3 electrics per foot 0-2 for foot 1 3-5 for foot 2 6-8 for foot 3 9-11 for foot 4}; |
| Remarks            |                                                                                                                                                                                                |

**4.1.22 Retrieving quadruped robot speed**

| Function Name      | GetRobotSpeed                                                                                                                                  |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Prototype | struct Robotspeed GetRobotSpeed()                                                                                                              |
| Function Overview  | Get quadruped robots x, y, z-axis speed and angle speed                                                                                        |
| Parameters         | None                                                                                                                                           |
| Return value       | (b) // / Body velocity (m/s) float body y; // / Body velocity (m/s) float body z; / / Body velocity (m/s) float body z; / Body velocity (m/s); |
| Remarks            |                                                                                                                                                |

**4.1.23 Access to SDK version number**

| Function Name      | GetSDKVersion                                 |
| ------------------ | --------------------------------------------- |
| Function Prototype | float GetSDKVersion()                         |
| Function Overview  | Get sdk version number                        |
| Parameters         | None                                          |
| Return value       | Call successfully returned sdk version number |
| Remarks            |                                               |

**4.1.24 Acquisition of location on cloud maps**

| Function Name      | GetRobotCloudMapLocation                                                                                                                                                 |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Function Prototype | struct RobotCloudMapLocation GetRobotCloudMapLocation()                                                                                                                  |
| Function Overview  | Get a little cloud map to locate                                                                                                                                         |
| Parameters         | None                                                                                                                                                                     |
| Return value       | (c) The coordinates xyz (in units: m) fload position y; fload position z; fload rotation x; / / / four-digit rotation (attitude); fload attitude y; fload orientation z; |
| Remarks            |                                                                                                                                                                          |

**4.1.25 Start charging**

| Function Name      | StartRobotCharging                                                          |
| ------------------ | --------------------------------------------------------------------------- |
| Function Prototype | int32\_t StartRobotCharging()                                               |
| Function Overview  | Start charging.                                                             |
| Parameters         | None                                                                        |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned. |
| Remarks            |                                                                             |

**4.1.26 Closure of charge**

| Function Name      | StopRobotCharging                                                           |
| ------------------ | --------------------------------------------------------------------------- |
| Function Prototype | int32\_t StopRobotCharging()                                                |
| Function Overview  | Stop Charging                                                               |
| Parameters         | None                                                                        |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned. |
| Remarks            |                                                                             |

**4.1.27 Access to map lists**

| Function Name      | GetRobotMapList                        |
| ------------------ | -------------------------------------- |
| Function Prototype | std::vectorGetRobotMapList()           |
| Function Overview  | Fetch Map List                         |
| Parameters         | None                                   |
| Return value       | Call for successful return of map list |
| Remarks            |                                        |

**4.1.28 Access to map documents**

| Function Name      | GetRobotMapFiles                                                                                                 |
| ------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t GetRobotMapFiles( const std::string& map\_name, const std::string& save\_directory)                     |
| Function Overview  | Get Map Files                                                                                                    |
| Parameters         | Map name: Map Name (accessed through GetRobotMapList), Save directory: Local Saver Directory specified by Caller |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned.                                      |
| Remarks            |                                                                                                                  |

**4.1.29 Access to SDK switch control state**

| Function Name      | GetSDKSwitch                                                                                                     |
| ------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t GetSDKSwitch()                                                                                          |
| Function Overview  | Get sdk to switch control state                                                                                  |
| Parameters         | None                                                                                                             |
| Return value       | Successfully called return 0 indicates no control, return 1 indicates control or return the relevant error code. |
| Remarks            |                                                                                                                  |

**4.1.30 Artificial locking mode**

| Function Name      | JointLockMode                                                                                                    |
| ------------------ | ---------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t JointLockMode(bool val)                                                                                 |
| Function Overview  | Joint Lock Mode                                                                                                  |
| Parameters         | val: Set true for opening, false for closing.                                                                    |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned.                                      |
| Remarks            | The int32 t Rotate up and down function needs to be called first so the quadruped robot can lean forward or back |

**4.1.30 Acquisition of robotic charge results**

| Function Name      | GetRobotChargeResult                                                                                                                                                                                                                                                                                                                                                      |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Function Prototype | int32\_t GetRobotChargeResult()                                                                                                                                                                                                                                                                                                                                           |
| Function Overview  | Get robot charge results.                                                                                                                                                                                                                                                                                                                                                 |
| Parameters         | None                                                                                                                                                                                                                                                                                                                                                                      |
| Return value       | The call for successful return 0 indicates no return from charge 1 indicates that the recovery is under way and the return of charge 2 indicates that the return of charge 3 indicates that the return is under way and the failure of recovery 1 indicates that the recovery of charge 2 indicates that the charge is abnormal or the associated error code is returned. |
| Remarks            | This interface needs to be used in conjunction with the interface Start RobotCharging                                                                                                                                                                                                                                                                                     |

**4.1.31 Turn left to right**

| Function Name      | Rotate\_right\_and\_left                                                    |
| ------------------ | --------------------------------------------------------------------------- |
| Function Prototype | int32\_t Rotate\_right\_and\_left(double radian)                            |
| Function Overview  | Turn left to right.                                                         |
| Parameters         | Radian: angle (-8, 8 degrees)                                               |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned. |
| Remarks            |                                                                             |

**4.1.32 Acquisition of battery power**

| Function Name      | GetRobotBatteryPercentage            |
| ------------------ | ------------------------------------ |
| Function Prototype | int32\_t GetRobotBatteryPercentage() |
| Function Overview  | Get battery capacity                 |
| Parameters         | None                                 |
| Return value       | Battery power as a percentage        |
| Remarks            |                                      |

**4.1.33 Crash mode switching**

| Function Name      | SwitchToCrawlMode                                                           |
| ------------------ | --------------------------------------------------------------------------- |
| Function Prototype | int32\_t SwitchToCrawlMode(bool val)                                        |
| Function Overview  | Switch to Crash Mode                                                        |
| Parameters         | val: Set true for opening, false for closing.                               |
| Return value       | Call successfully returns 0, otherwise the relevant error code is returned. |
| Remarks            |                                                                             |

#### 4.2 Bottom service interface

**4.2.1 Bottom control instructions**

```
Users subscribe to topics rt/lowcmd The data structure for sending the electrical control instructions is as follows:
```

| g g g g g, |
| ---------- |

**4.2.2 Bottom data reception**

```
User Subscriptionsrt/lowstateThe topic of access to electric power,IMUData, the structure of the data is as follows:
```

#### IMU status information:

| Plain Text float32 \[3] imu angular velocity / /roll Rate (rolling angle speed around X-axis) / pitch rate (opposite angle speed around Y-axis) / / yaw rate (round Z axis) fload32\[3] imu linear acceleration/// x-axis acceleration// y-axis acceleration speed float32 \[4] imu orientation / / iv-point attitude imus is validuint16 imu packet idid |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### 2. Electrical status information:

| float32\[4] q knee / hip anglefloat32\[4] q knee / knee / knee joint anglefloat32\[4] qd bad /Abduit joint angle speed (unit:rad/s)float32\[4] qd hip / qd hip / gill joint angle velocityfloat32\[4] \[4] qd knee / klip / klip angle float 32\[4] tau knoe / kloat / kloatgs / knobg 32\[4] tau knob / klags intmat mat mat/ mat matr 32 t t matr/gt matr t t mat t t tal t t 32 t t t t |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

#### 4.3 Controlled diagnostic anomalies

The unusual information that appears during the current operation of the control is shown on the bullet window on the remote controller and the error code is shown in the table below:

| key | Meaning of the project                                                                                  | key\_str                        | Code Parsing                                                                                                                                                                                                                                                                                                                                                              | Note                                                                              |
| --- | ------------------------------------------------------------------------------------------------------- | ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| 0   | Empty items, meaningless.                                                                               | None                            |                                                                                                                                                                                                                                                                                                                                                                           | No hint                                                                           |
| 1   | Reactivate stand-up diagnostics. Is it because of the wrong joint position that the dog can't stand up? | RecoverStand\_JointPos          | 0: No error reported; other: 12 joints 0-11 against code 0-11bit, which is not in the right position and which bit is 1.                                                                                                                                                                                                                                                  | Fault code: $code                                                                 |
| 2   | Reactivate stand-up diagnostics. Whether the dog could not stand up because the power was wrong.        | RecoverStand\_MotorWarningLevel | 0: No error reported; other: Motor WarningLeve grade, 1-3, the larger the number, the more serious the problem                                                                                                                                                                                                                                                            | Artificial hardware abnormal to stand, failure code: $code                        |
| 3   | Reactivate stand-up diagnostics. Is it because of low battery power that dogs can't stand up?           | RecoverStand\_SocWarningLevel   | 0: No error; other: SocWarningLeve grade, 1-3, the larger the number, the more serious the problem                                                                                                                                                                                                                                                                        | Power is too low to stand, failure code: $code                                    |
| 4   | Reactivate stand-up diagnostics. Whether the dog could not stand up because IMU was wrong.              | RecoverStand\_ImuStatus         | 0: no error reported; other: bit0: 0:ok; 1: IMU modules not available; bit1: 0:ok; 1: IMU postures are not appropriate to restore standing;                                                                                                                                                                                                                               | IMU sensor abnormal, unable to stand, failure code: $code                         |
| 5   | Reactivate stand-up diagnostics. Is it because the order isn't right that the dog can't stand up?       | RecoverStand\_CmdError          | 0: No error reported; 1: The stopping command is still in place and cannot respond to the recovery standing directive; 2: The defusing directive is still in place and cannot respond to the restoration standing directive;                                                                                                                                              | There is a resistance or detachment command, unable to stand, failure code: $code |
| 6   | Error reporting under visual mode. Whether there is an error at the height chart node.                  | VisualMode\_ElevationMapping    | 0: no error reported; 1: timeout of the high scale map node; 1: error in the front depth camera; 2: error in the mileage of the front depth camera;                                                                                                                                                                                                                       | High map abnormal, visual mode unavailable, failure code: $code                   |
| 7   | Error reporting under visual mode. Whether there is an error at the miles node.                         | VisualMode\_Odom                | 0: no error reported; 1: mileage timeout; 1: mileage is not in visual mode; 2: mileage is in initialization; 3: mileage data entry error;                                                                                                                                                                                                                                 | The mileage is abnormal, visual mode is unavailable, failure code: $code          |
| 8   | Error reporting under visual mode. Controls whether there is an error in the internal sensor module.    | VisualMode\_Perception          | 0: No errors reported; 1: error;                                                                                                                                                                                                                                                                                                                                          | Getting map abnormal, visual mode not available, failure code: $code              |
| 9   | Front right leg state                                                                                   | Leg\_frontRight                 | 0: no error reported; other values: the following bit values indicate no error reported and the value is 1 deciphered as follows: bit0: loss of joint A; bit1: loss of joint H; bit2: loss of joint K; bit3: error of joint A; bit5: error of joint H; bit6: error of joint K; bit8: feedback of joint A; bit9: feedback of joint H; bit10: feedback of specific Errcode; | Hardware anomaly on right front leg, failure code: $code                          |
| 10  | Front left leg state                                                                                    | Leg\_frontLeft                  | Hardware anomaly for left front leg, failure code: $code                                                                                                                                                                                                                                                                                                                  |                                                                                   |
| 11  | Back right leg state                                                                                    | Leg\_rearRight                  | Right rear leg hardware anomaly, failure code: $code                                                                                                                                                                                                                                                                                                                      |                                                                                   |
| 12  | Back left leg state                                                                                     | Leg\_rearLeft                   | Hardware anomaly for left rear leg, failure code: $code                                                                                                                                                                                                                                                                                                                   |                                                                                   |
| 13  | Electrical temperature level                                                                            | MotroTempWarning                | 0:OK; other values: 1 \~3, the larger the number, the more serious the problem                                                                                                                                                                                                                                                                                            | Electric high temperature warning, failure code: $code                            |
| 14  | Battery status level                                                                                    | SocWarning                      | 0:OK; other values: 1 \~3, the larger the number, the more serious the problem                                                                                                                                                                                                                                                                                            | Low power warning, failure code: $code                                            |
| 15  | Imu Status                                                                                              | Imu                             | 0:OK; 1: Imu not available                                                                                                                                                                                                                                                                                                                                                | IMU sensor module abnormal, failure code: $code                                   |
| 16  | Run-time security detection                                                                             | SafetyChecker                   | 0:OK; other values: the following bit values indicate no error and the values are 1 deciphered as follows: bit0: imu error; bit1: a body attitude angle exceeding limit; bit2: joint angle or speed limit; bit3: joint hardware anomaly; bit4: joint angle reached hard limit; bit5: foot position limit;                                                                 | Runtime security detection anomaly, failure code: $code                           |
| 17  | UserMode Switch (general, high-speed, visual)                                                           | UserModeSwitch                  | 0:OK; 1: Switch to visual mode failed; 2: Switch to high speed mode failed;                                                                                                                                                                                                                                                                                               | Switch to xx mode failed, retrying in static mode, failure code: $code            |

Users can access the results of all these diagnostics by subscription to the topic "report all item". The data structure of the diagnostic items is as follows:

| Plain Textstatus report set#Outside message definition of the number of Header header #uint16 total count # several pieces of uint16 error # several status report\[] report set# Group |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| Plain Textstatus report#Intra-level message definitionstringkey str#key is converted to string to enhance readability id, which is the only recognized id of the #key diagnostic project, which is different from int16 code# failure code, for details, see string information, code hint, above, to reduce the time of searching code |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### V. Introduction to other services

#### 5.1 Fax Services

Videos of the wide-angle cameras are pushed to the following URLs by Gstreamer:

| Plain Text rtsp://192.168.144.3:8554/cambrtsp://192.168.144.3:8554/camf |
| ----------------------------------------------------------------------- |

The default displays real-time images on the side pull side of the remote, previewing and calling via VLC or OpenCV

### Official Resources

[Official AGIBOT development guide](https://www.agibot.com.cn/filepage/327/detail/41.html)

[Official AGIBOT downloads and software packages](https://www.agibot.com.cn/filepage/332.html)
