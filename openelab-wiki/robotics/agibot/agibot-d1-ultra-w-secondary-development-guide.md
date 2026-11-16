# AgiBot D1 Ultra-W Secondary Development Guide

### AGIBOT D1 Ultra W IP54 Wheeled-Legged Quadruped Robot Dog

{% embed url="https://openelab.io/products/agibot-d1-ultra-wheeled-robot" %}

**Applicability:** This guide is specific to the D1 Ultra-W wheeled-legged robot. Do not apply Ultra-W-only commands to D1 Edu or D1 Ultra unless the official API explicitly states compatibility.

| Revision date | Revision                                                         | sdk version   |
| ------------- | ---------------------------------------------------------------- | ------------- |
| 2025-07-16    | • Initial version sdk                                            | v2.0.5        |
| 2025-07-19    | • New senior sdk interface                                       | v2.0.6        |
| 2025-09-15    | • Rehabilitation of “checkcontract” interface abnormality        | v0.2.6-patch1 |
| 2025-11-04    | • New bottom sdk interface — new D1 Ultra-W topsdk Answer. mouth | v2.0.7        |

### 1. Product Introduction

#### 1.1 Product Overview

D1 Ultra-W, with 12 degrees of freedom, has a wide range of motion and motion. At the same time, the product has opened up motion control algorithms for the development of SDK and communication protocols, allowing users to redevelop as required.

#### 1.2 Package Contents

![Photo 15.png](<../../.gitbook/assets/assetsfigure-001 (1).png>)

#### 1.3 Product Specifications

| Classification                     | Specifications                                                                                                                                                        | Annotations                                                                     |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| Basic information                  | Material Information                                                                                                                                                  | Aluminium alloys + high-intensity engineering plastics                          |
| Standing (long x wide x high)      | 630mm×430mm×485mm                                                                                                                                                     |                                                                                 |
| Punctuation (long x high)          | 690mm×540mm×165mm                                                                                                                                                     |                                                                                 |
| Whole weight (including batteries) | 22kg                                                                                                                                                                  |                                                                                 |
| Freedom                            | Freedom 16, single leg 4.                                                                                                                                             |                                                                                 |
| Working temperature                | 0℃ \~40℃                                                                                                                                                              |                                                                                 |
| Protection level                   | IP54                                                                                                                                                                  |                                                                                 |
| Battery                            | Standard capacity 4.6 Ah, voltage 43.2v                                                                                                                               |                                                                                 |
| Charge duration                    | 1h                                                                                                                                                                    |                                                                                 |
| Time of renewal.                   | 1-2h                                                                                                                                                                  |                                                                                 |
| Keep going.                        | 9km                                                                                                                                                                   |                                                                                 |
| Performance parameters             | Maximum speed                                                                                                                                                         | 3.7m/s                                                                          |
| Rating Load                        | 5kg                                                                                                                                                                   |                                                                                 |
| Climbing the stairs.               | 16cm                                                                                                                                                                  |                                                                                 |
| Maximum slope angle                | Standard environment 30°, maximum 40°                                                                                                                                 |                                                                                 |
| Jumping above ground height        | 35cm                                                                                                                                                                  |                                                                                 |
| Maximum climbing height            | 60cm                                                                                                                                                                  |                                                                                 |
| Organ section parameters           | Maximum joint twist                                                                                                                                                   | 48N m                                                                           |
| Joint motion space (airframe)      | -28°-28°                                                                                                                                                              |                                                                                 |
| Joint motion space (legs)          | -170°-66°                                                                                                                                                             |                                                                                 |
| Joint motion space (legs)          | 35°-156°                                                                                                                                                              |                                                                                 |
| Sensors                            | CameraFOV                                                                                                                                                             | One camera, pixel 1920\*1080p, field of view DFOV122°, HFOV111°, VFOV70°        |
| IMU                                | Mark                                                                                                                                                                  |                                                                                 |
| Function List                      | Standard Actions                                                                                                                                                      | Stand up, fall down, stand down, bow down, high and low, and turn horizontally. |
| Real-time image transfer           | Support                                                                                                                                                               |                                                                                 |
| Secondary development              | Support for the provision of SDK development kits, standardized interfaces, robotic models and simulation interfaces to support analog environments such as Issac Sim |                                                                                 |
| Communications function            | Support WIFI 5.0, Bluetooth 5.0                                                                                                                                       |                                                                                 |
| Functional Extension Interface     | Etherne&#x74;_&#x31;, USB interfac&#x65;_&#x32;, power interfac&#x65;_&#x32;, SBUS interfac&#x65;_&#x31;, UART interface\* One.                                       |                                                                                 |

#### 1.4 Back-Mounted Payload Installation

![Image 16.png](<../../.gitbook/assets/assetsfigure-002 (1).png>)

#### 1.5 Electrical Expansion Interfaces

| Serial number | Interface Name  | Number | Annotations                                                                                                                                                                                                                                       | Remarks |
| ------------- | --------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| 1             | Ethernet        | 1      | RJ45 interface to support 1,000 Mbps transmission rate for high-speed data transmission, support for network connectivity, remote monitoring, data transmission, etc.                                                                             |         |
| 2             | USB interface   | 2      | Type A interface to connect external storage equipment, United StatesB equipment such as cameras, sensors, and provide high-speed data transmission and power supply                                                                              |         |
| 3             | Power interface | 2      | SDC power interface, which provides stable power supply, supports 12V and BAT output, with a total power of no more than 36W for 12V output, and 100 W for BAT output, and meets the power requirements of quadruped robots and loaded equipment. |         |
| 4             | SBUS interface  | 1      | Standard SBUS interface to connect remote controller receivers or other communication devices supporting SBUS protocols to achieve accurate remote command transmission                                                                           |         |
| 5             | UART interface  | 1      | Standard UART interface for connecting embedded systems, communication equipment or other equipment supporting UART protocols to achieve data exchange and control between devices by walk-through communication                                  |         |

![1.5 Replace picture.jpg](<../../.gitbook/assets/assetsfigure-003 (1).jpg>)

![Photo 18.png](<../../.gitbook/assets/assetsfigure-004 (1).png>)

### II. System architecture

#### 2.1 AGIBOT architecture

![Photo 19.png](<../../.gitbook/assets/assetsfigure-005 (1).png>)

| Note: Fiction diagrams are functional and dotted frames can be developed twice |
| ------------------------------------------------------------------------------ |

#### 2.2 SDK software frame

Existing open motion control related SDK interfaces, including upper movement control interfaces, IMU customary guide data interfaces and electrical status data interfaces

![Photo 20.png](<../../.gitbook/assets/assetsfigure-006 (1).png>)

#### 2.3 List of software service interfaces

| Serial number | Interface Name                   | Functions                                                                                                      | SDK Version |
| ------------- | -------------------------------- | -------------------------------------------------------------------------------------------------------------- | ----------- |
| 1             | Upper Movement Control Interface | High-level motor control of robots and dogs, including back-to-back velocity, down, spin, limbs standing, etc. | V0.2.7      |
| 2             | Device status service interface  | Query and obtain information on the current state of equipment and the use of system resources                 | V0.2.7      |
| 3             | IMU Service Interface            | Fetch IMU raw data information                                                                                 | V0.2.7      |
| 4             | Video streaming data interface   | Push camera home stream to client                                                                              | V0.2.7      |

### III. SDK development guide

#### 3.1 Introduction to SDK

• This document describes the software development toolkit (SDK) for D1 Ultra-W, which provides detailed information on its core service interface, including the upper movement control interface, the IMU customary guide data interface and the electrical status data interface.

• Each chapter presents the method of calling different service interfaces, standard format definitions for data input/output and examples of some functional development.

• The definition of interface will vary with the development of the mass product, depending on the latest version of the interface definition document.

• The SDK program has a specific protocol for communication with the dog's own program, so there are differences between different versions of the SDK program and the dog's own program. Select the corresponding version of the SDK program according to the device version. If conditions permit, it is recommended that the internal dog program be updated to the latest version to achieve better compatibility.

• When the SDK interface is controlled, the entire state is designed by a secondary developer and no additional intervention and state jumps are performed by the HMO.

• When running SDK, please ensure that the system is adequately resourced, otherwise there may be cases where the motion control module has failed.

#### 3.2 Environmental dependency

• ubuntu22.04

• Cmake 3.8+

• GCC 11+

• Eligen3

• Boost

• python3+

#### 3.3 Network connectivity

The device is equipped with a wireless network interface with wireless network information on the right side or abdomen of the device, with the device SID and password information on the label, and the quadruped robot body default IP table as follows:

| Network Interface | IP Address      | DHCP  |
| ----------------- | --------------- | ----- |
| Wireless network  | 192.168.234.1   | Yeah. |
| Wireless Network  | 192.168.168.168 | None  |

Wireless networks, equipped with DHCP services and connected to the Wireless Network, ensure that the operating equipment wireless network is not equipped with a fixed IP and that communications can be established directly with robots through 192.168.234.1.

Wireless networks are not equipped with DHCP services, and re-operated equipment cable networks are required to configure fixed IPs, and IPs are 168 segments to allow communication with robots.

#### 3.4 Equipment login

The equipment provides ssh login, which allows the device to login via ssh when a connection to the device is created by wireless or wired

![Photo 21.png](<../../.gitbook/assets/assetsfigure-007 (1).png>)

• Wireless connectivity

| #Plain Text sh firefly@192.168.234.1 |
| ------------------------------------ |

• Wireless connection

| Plain Text sh firefly@192.168.168.168 #cipher:firefly |
| ----------------------------------------------------- |

#### 3.5 Firmware version number query

After login, the following command is given to view the current version of the device:

| Bash grep -oP 'motion-control\_\K\[^\_]+' /etc/release/_\[^rootfs]_.yaml |
| ------------------------------------------------------------------------ |

![Photo 22.png](<../../.gitbook/assets/assetsfigure-008 (1).png>)

Example: 602002057TBD.yaml: 0.2.7

Firmware version number: 567 bit, i.e. 2.0.5 solid

SDK version number: Output content, i.e. transport version 0.2.7

If the post-execution version number is less than 0.2.6, this means that the equipment version is too low and requires upgrading after sale in contact.

| This document applies to SDK version 0.2.6 and above, and if less, contact post-sale technicians for upgrade |
| ------------------------------------------------------------------------------------------------------------ |

| The following version of the quadruped robot: during sdk control, the remote controller cannot use 0.3.4 or more versions of the quadruped robot: during sdk control, the control of the remote controller and the switch control of sdk can be replaced, and if the control switch is required, contact the post-sale technical support officer for upgrading |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### 3.6 SDK Access

Way 1: Accessable to support after sale

Go: Get it through the github address below

| Plain Text git clone https://github.com/AgibotTech/agibot\_D1\_Edu-Ultra.git |
| ---------------------------------------------------------------------------- |

#### 3.7 sdk file configuration

**3.7.1 Wireless connection mode**

step1 Modify sdk communications profile

```
Pass.vimCommand to change quadruped robot body/opt/export/config/sdk_config.yamlDocuments:
```

| Plain Text target\_ip: "192.168.234.xx" #local\_iptarget\_port: 43988 |
| --------------------------------------------------------------------- |

```
• target_ip: Quadruped robot control endIPAddress, do not.IPConflict(I can't.192.168.234.1)
```

```
• target_port: Default43988Do not modify
```

Reactivate quadruped robot after modification of the step2 configuration parameter

**3.7.2 Wireless connection mode**

step1 Modify sdk communications profile

```
Pass.vimCommand to change quadruped robot body/opt/export/config/sdk_config.yamlDocuments:
```

| Plain Text target\_ip: "192.168.168.xxx" #local\_iptarget\_port: 43988 |
| ---------------------------------------------------------------------- |

```
• target_ip: Quadruped robot control endIPAddress, do not.IPConflict(I can't.192.168.168.168)
```

```
• target_port: Default43988Do not modify
```

step2 Configure SDK CLIENT IP

If network lines or other non-192.168.234.X-net IP controls are required, modified by vim command

```
/opt/app_launch/start_motion_control.shDocuments:
```

| Bash#!/bin/bashecho "start movement control"# Share memory path SHM FILE="/dev/shm/spline shm"# # Circulation check device exists while true; do if \[-e-$SHM FILE]; then echo " Share memory file $SHM FILE already exists. "Break else echo " shared memory file $SHM FILE does not exist and waits for a second to retry... 'sleep 1 fidone# command cho " shared memory file is ready for subsequent operation. "sudo ifconfig lo multiculturalasundo route add-net 224.0.0 netmask 240.0.0.0 dev loexport LD LIBRARY PATH=/opt/export/mc/binexport ROBOT TYPE=P2export SDK CLIENT IP= "Bob ip"cd /opt/export/mc/bin & taskset-c 7 /mc ctrl rr |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```
• It's the code on it.27All right, add configuration:export SDK_CLIENT_IP="Robots.ip"And the robot.IPAddress filled in the corresponding parameter
```

```
• If you use a wired network, you will use robots.IPModify to192.168.168.168,If it's otherIPModify to CorrespondIPYeah.
```

step3 Modify webcard name

```
Change the quadruped robot book./etc/systemd/system/robot-launch.serviceDocumentation
```

```
Yes.ServiceAdd a line insideEnvironment="ROBOT_NET_INTERFACES=wlan0"of whichwlan0For the corresponding card name, the use of a cable network can be changed toeth0
```

The complete profile is as follows:

| JSON \[Unit]Description=Run robot-launch at startupAfter=network.target\[Service]ExecStart=robot-launch serviceExpecStop=/usr/local/bin/robot lanch stop.shTimeoutSopSec=5sRestart=alwaysUser=RootEnvironment="ROBOT HOME/firely'Environment=" ROBOT LOG DER=/userdata/log'Environment="RoBOT NET NETINFACES=wlan0"#Wlan0 is used to change to "ethlan0" \[Install]WantBy=user.target0" |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| This parameter is configured with the probability that the robot dog will not be able to use the remote! The configuration of SDK CLIENT IP and the failure of the corresponding webcard to allocate IP addresses when the network has not been initialized after the device has been installed has led to the failure of the control program to bind IP addresses, thus preventing dogs from using remote controllers. |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### 3.8 Modify SDK Demo Configuration

**3.8.1 Configure python IP and port**

```
Yes. {User Directory}/agibot_D1_Edu-Ultra-main/demo/zsl-1w/python/examples/highlevel_demo.py, ModifyinitRobot()FunctionIPAddress
```

| Python app.initRobot("127.0.0.1", 43988, "127.0.0.1") #local\_ip, local\_port, dog\_ip |
| -------------------------------------------------------------------------------------- |

**3.8.2 Configure C++ IP and port**

```
Yes. {User Directory}/agibot_D1_Edu-Ultra-main/demo/zsl-1w/cpp/highlevel_demo.cpp, change as required
```

| C++ constexpr int CLIENT\_PORT = 43988; // local port std::string CLIENT\_IP = "127.0.0.1"; // local IP address std::string DOG\_IP = "127.0.0.1"; // dog ip |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ |

| The robot IP and the local port in the configuration parameter need to be consistent with the parameters of the sdk config medium target ip and target port. Make sure the robot IP matches the port number, otherwise communication cannot be created! If the sdk config.yaml's ip is deleted or denoted, the machine's transport service cannot start from now on! When the device program is updated or the control program is updated, the profile will be reset and the configuration will need to be reconfigured! |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

| If you run the sdk demo program via Wi-Fi connection in the four-foot robotic body, the local ip and dog ip are set at 192.168.234.1. |
| ------------------------------------------------------------------------------------------------------------------------------------- |

#### 3.9 Example: Demo Run Steps

**3.9.1 Compiled demo**

At local PC end, enter to sdk file Medium

| Bash cd demo/zsl-1w/cppmkdir buildcd buildcmake..make -j6 |
| --------------------------------------------------------- |

**3.9.2 Operational sdk demo**

• Run Python demo

| Plain Text cd demo/zsl-1w/python/examplespython highlevel\_demo.py |
| ------------------------------------------------------------------ |

• Run C++ demo

| Plain Text cd demo/zsl-1w/cpp/build./highlevel\_demo |
| ---------------------------------------------------- |

**3.9.3 Call sdk**

• Python-based call sdk

| Python import osimport platformimport sysarch = platform.machine().replace('amd64', 'x86\_64').replace('arm64', 'aarch64')lib\_path = os.path.abspath(f'{os.path.dirname(**file**)}/../../../../lib/zsl-1w/{arch}')sys.path.insert(0, lib\_path)import mc\_sdk\_zsl\_1w\_pyimport timeapp=mc\_sdk\_zsl\_1w\_py.HighLevel()app.initRobot("127.0.0.1",43988, "127.0.0.1") #local\_ip, local\_port, dog\_ipapp.standUp()time.sleep(4)app.move(0.1, 0, 0)time.sleep(5)app.standUp()time.sleep(4)app.attitudeControl(0.1,0.1,0.1,0.1)time.sleep(4)app.crawl(1.0, 0.0, 0.0)time.sleep(5)while True: time.sleep(2) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

#### 3.10 Two-part control statement

Instructions are issued in the following conditions, which may result in abnormal situations such as machine fall, failure, non-response, etc.

![Photo 23.png](<../../.gitbook/assets/assetsfigure-009 (1).png>)

**3.10.1 Description of joint control orders**

Order Order

FR (front right)

• FL (front left)

RR (back right)

• RL (back left)

**3.10.2 Definition of joint orientation**

A, H, K joint coordinates: Front X, Left Y, Upper Z

Coordinates match the right-hand coordinates, forward X, left Y, up Z.

The order of legs is right front left, back right left.

![Photo 24.png](<../../.gitbook/assets/assetsfigure-010 (1).png>)

| Note: When using sdk controls, the low-power warning logic is required, the sdk connection is automatically disconnected when quadruped robot power is insufficient, and the corresponding processing logic is required for upper sdk control |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

### IV. Introduction to API Functions

Detailed interface description, see the corresponding version of the sdk description document:

```
https://github.com/AgibotTech/agibot_D1_Edu-Ultra/blob/main/docs/api_zsl-1w.md
```

### Official Resources

[Official AGIBOT development guide](https://www.agibot.com.cn/filepage/325.html)

[Official AGIBOT downloads and software packages](https://www.agibot.com.cn/filepage/330.html)
