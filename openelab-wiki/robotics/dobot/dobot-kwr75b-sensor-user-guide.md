---
description: >-
  User guide for the DOBOT KWR75B six-axis force/torque sensor, covering
  specifications, dimensions, mechanical and electrical installation, plugin
  setup, calibration, homing, and dragging modes.
---

# DOBOT KWR75B Sensor User Guide

## DOBOT Kunwei KWR75B Six-Axis Force Torque Transducer

{% embed url="https://openelab.io/products/dobot-kunwei-kwr75b-force-torque-transducer" %}

## DOBOT KWR75B Six-Axis Force Torque Sensor for Cobots

{% embed url="https://openelab.io/products/dobot-kwr75b-six-axis-sensor" %}

## Contents

* Preface
* Description on Sensor
* Performance parameter
* Dimensions
* Installation Instruction
* Mechanical installation
* Electrical connection
* Installation of Plug-in
* Installation in Windows
* Installation in Android & iOS
* Sensor Calibration and Functions
* Sensor Calibration
* Homing the sensor
* Dragging mode

## Preface

Purpose This manual introduces the parameters, installation and operation of KWR75B sensor, which is convenient for users to understand and use the sensor. Intended Audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Change History Date Change Description 2021-8-27 The first release Symbol Conventions The symbols that may be founded in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could result in death or

**DANGER**

serious injury Indicates a hazard with a medium level or low level of risk which, if not avoided, could

**WARNING**

result in minor or moderate injury, robot damage Indicates a potentially hazardous situation which, if not avoided, can result in equipment

**NOTICE**

damage, data loss, or unanticipated result

**NOTE Provides additional information to emphasize or supplement important points in the main**

text

## Description on Sensor

KWR75 series sensor is a strain type six-axis force/torque sensor. It can simultaneously detect three forces and three torques. The sensor detects the relative deformations between the tool-end flange and the main body caused by applied forces, and uses a resistance strain gauge to measure changes in the elastic element of the sensor. The sensor contains an embedded system, which can collect and process the signal changes of the resistance strain gauge in real time, and output the magnitude and direction of the applied force in real time, with high precision and response ability.

_Figure 1.1 KWR75 sensor_

### Performance parameter

The specifications of KWR75B sensor are listed in Table 1.1.

_Table 1.1 Specifications of AG-95 gripper_

Specifications Description Fx, Fy (N) 200 Fz (N) 200 Mx, My (Nm) 8 Mz (Nm) 8 Diameter (mm) 75 Height (mm) 31.5 Material Aluminum alloy Surface treatment Anodization Overload level (%) 300 Repetition accuracy (%FS) 0.1 Accuracy of FS (%)\ 0.5 Sampling resolution (Bit) 24 Weight 0.28 Protection grade IP64

Working temperature 5~~80 Sampling frequency (kHz) 1 Power supply voltage (VDC) 9~~24 Communication interface RS422/RS485/MODBUS/EtherCAT/EtherNET/USB

### Dimensions

_Figure 1.2 shows the dimensions of KWR75B sensor._

_Figure 1.2 Dimensions of KWR75B_

![Figure 1.2 shows the dimensions of KWR75B sensor.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMZ5Nh6Yy4KSoi0WOu2SV%2Fkwr75-p006-img02.png?alt=media)

## Installation Instruction

### Mechanical installation

_Figure 2.1 Sensor installation diagram_

![Figure 2.1 Sensor installation diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrZSKugsSThhfcFsayuM3%2Fkwr75-p007-img21.png?alt=media)

_Figure 2.2 Sequence of screwing_

**NOTICE**

The flange locating pin on the tool end of the sensor is used for the consistency of the tool installation. If the locating pin is not used, the sensor performance will not be affected.

### Electrical connection

The figure below shows the connection between CR robot and KWR75B sensor. You should plug the KWR75B cable to CR I/O port following the right cable sequence.

_Figure 2.3 Electrical connection_

![Figure 2.2 Sequence of screwing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7FkXng5Cf4mxRs803BTm%2Fkwr75-p008-img06.jpg?alt=media)

![Figure 2.3 Electrical connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfHmtLSGdT1goBBFpd1fg%2Fkwr75-p008-img08.png?alt=media)

## Installation of Plug-in

The sensor plug-in needs to be installed through CR software. For Windows, please use DobotSCStudio V2.0.6Beta or later versions; For Android, please use Android CRStudioV4.0.0.6 or later versions. For iOS, please use iOS CRStudio V2.1.0 or later versions.

### Installation in Windows

This chapter mainly introduces how to use DobotSCStudio software in Windows to install the sensor plug-in.

_Figure 3.1 EndEffector Page_

![Figure 3.1 EndEffector Page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzafFz6TKrcLSFZRzzB08%2Fkwr75-p009-img17.png?alt=media)

_Figure 3.2 Install ForceTorqueSensor.zip_

_Figure 3.3 Panel tab_

_Table 3.1 Description on Panel parameters_

No. Description 1 Open/close six force 2 Force value 3 Moment value 4 Status of sensor

![Figure 3.2 Install ForceTorqueSensor.zip](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9405PkOjOxey0Z7diPCH%2Fkwr75-p010-img01.jpg?alt=media)

![Figure 3.3 Panel tab](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ffpc0ebislSQ29X5i25wM%2Fkwr75-p010-img02.png?alt=media)

When the sensor is turned on, the icon will turn green

_Figure 3.4 Open six force_

![Figure 3.4 Open six force](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpIDyqmhzIH5bAlDeF2lv%2Fkwr75-p011-img20.png?alt=media)

### Installation in Android & iOS

Prerequisites Select the right WiFi of the robot and connect it. The default WiFi name of CR robots is Dobot\_WIFI\_xxx and the default password is 1234567890. Procedure

_Figure 3.5 Install ForceTorqueSensor plug-in_

![Figure 3.5 Install ForceTorqueSensor plug-in](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh7qP9WEZ1Ee3u3WvlOsA%2Fkwr75-p012-img23.jpg?alt=media)

_Figure 3.6 Panel tab_

_Table 3.2 Description on Panel parameters_

No. Description 1 Open/close six force 2 Force value 3 Moment value 4 Status of sensor When the sensor is turned on, the icon will turn green

![Figure 3.6 Panel tab](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhtYQ6bzIzYdwDrxApkmI%2Fkwr75-p013-img20.png?alt=media)

_Figure 3.7 Open six force_

![Figure 3.7 Open six force](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqeqRHTDCfku9jBVYmBmg%2Fkwr75-p014-img01.png?alt=media)

## Sensor Calibration and Functions

### Sensor Calibration

_Figure 4.1 Position of X+_

_Figure 4.2 X+ at the bottom_

![Figure 4.1 Position of X+](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrhO7bS7gv5IN1H9hXIo8%2Fkwr75-p015-img10.jpg?alt=media)

![Figure 4.2 X+ at the bottom](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7TLrqWsDpjPv70DwJs0Z%2Fkwr75-p015-img11.jpg?alt=media)

_Figure 4.3 Calibrate X-axis direction_

_Figure 4.4 Y+ at the bottom_

![Figure 4.3 Calibrate X-axis direction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaLFDO17hTjmYfFnfr7je%2Fkwr75-p016-img06.png?alt=media)

![Figure 4.4 Y+ at the bottom](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F78XrNIQRXOupuOrCVw6P%2Fkwr75-p016-img07.jpg?alt=media)

_Figure 4.5 Calibrate Y-axis direction_

_Figure 4.6 Sensor parallel to the ground_

![Figure 4.5 Calibrate Y-axis direction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvAN1cp0ITCsZAEJeEteP%2Fkwr75-p017-img06.png?alt=media)

![Figure 4.6 Sensor parallel to the ground](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTVTG5uqlV1JnTLpDJOyG%2Fkwr75-p017-img07.jpg?alt=media)

_Figure 4.7 Calibrate Z-axis direction_

_Figure 4.8 Calibration is finished_

### Homing the sensor

Before calibrating the sensor, you need to click “Sensor Home” on “Setting” tab to reset the sensor, as shown in Figure 4.9.

![Figure 4.7 Calibrate Z-axis direction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXcRFUdNdJK0J3ykeJAPN%2Fkwr75-p018-img04.png?alt=media)

![Figure 4.8 Calibration is finished](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYEcZbVWq7VJIfQJhW0VF%2Fkwr75-p018-img05.jpg?alt=media)

_Figure 4.9 Homing the sensor_

### Dragging mode

You can enter the “Teach” tab to select the dragging mode and dragging speed, as shown in Figure 4.10.

* Full drag: Change the posture and position of the end tool according to the force on the end.

![Figure 4.9 Homing the sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu7mOKh0fnKRy6sVZ1HL0%2Fkwr75-p019-img02.png?alt=media)

![Figure 4.10.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4ZyhPIB5sRgS3CKWRLsE%2Fkwr75-p019-img03.jpg?alt=media)

* Moving drag: The robot changes its position according to the value change of the sensor. The posture of the end tool does not change during movement.
* Pose drag: The position of the end tool does not change, while the posture of the end tool changes.

**NOTICE**

It is recommended to drag with a tool at the robot end. You need to grab the bottom of the sensor when dragging without a tool. Holding the side of the sensor does not work!
