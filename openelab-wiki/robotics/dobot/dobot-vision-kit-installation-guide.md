---
description: >-
  Installation guide for the DOBOT vision kit used with Magician, M1 Pro, MG400,
  and Magician E6 robots.
---

# DOBOT Vision Kit Installation Guide

## DOBOT Vision System for Magician E6, MG400 and M1 Pro

{% embed url="https://openelab.io/products/dobot-vision-system-robot-arms" %}

## Contents

* Preface
* 1\. Vision Kit Description
* 2\. Installation Instructions

Copyright © Shenzhen Yuejiang Technology Co., Ltd. 2024. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Yuejiang Technology Co., Ltd (hereinafter referred to as “Dobot”). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software, and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses will be happening in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure of following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot. Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

Purpose This document describes the Dobot vision kit and its installation, making it easy for users to fully understand and use it. Intended Audience This document is intended for:

* Customer Engineer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Change History Date Issue Change Description 2024/02/02 V1.3 Added Magician E6 installation instructions Added instructions on how to use the aviation plug cable Update document styles 2022/12/13 V1.2 Replace M1-related contents with M1 Pro Add MG400 installation instructions 2019/09/09 V1.1 Update vision kit specification and installation 2018/04/27 V1.0 The first release Symbol Conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could

**DANGER**

result in death or serious injury Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot damage Indicates a potentially hazardous situation which, if not avoided, can

**NOTICE**

result in equipment damage, data loss, or unanticipated result Provides additional information to emphasize or supplement important

**NOTE**

points in the main text

## 1. Vision Kit Description

### Overview

The image processing system extracts the characteristics of the objects through setting the range of hue, saturation, value and pixel area of the images obtained from the vision kit, transforms the image coordinates into Cartesian coordinates and transmits to the robot. Therefore, the robot can complete intelligent sorting tasks.

### 1.2 Vision Kit List

_Figure 1.1 shows the vision kit list._

_Figure 1.1 Vision kit list_

### 1.3 Camera Parameter Description

_Table 1.1 Camera Parameters Description_

Parameters Description Camera model MV-CE050-30UC Sensor size 1/2.5"CMOS Sensor model AR0521 Effective pixels 5,000,000 pixels Color Color

![Figure 1.1 shows the vision kit list.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F129lZDH9n2MTJ48ZwF13%2Fvision-p005-img02.png?alt=media)

Pixel Size 2.2um×2.2um Frame rate/Resolution 31 @2592×1944 SNR >40dB Dynamic range >60dB Shutter type Rolling shutter Exposure time Bayer format：16μs~~1s Other formats：28μs~~1s Exposure control Automatic/Manual Dimension 29m&#x6D;_&#x32;9m&#x6D;_&#x33;0mm Data interface USB3.0 Operating temperature 0\~50°C Lens mount Mount C

### 1.4 Light Source Parameter Description

_Table 1.2 Light Source Parameters Description_

Parameters Description Light source model JHZM-A40-W Emitting color White LED quantity 48 light-emitting diode Illumination 40000Lux Brightness Continuously adjustment, adjustable range: 0%~~100% The color temperature remains unchanged Wavelength 455nm~~457.5nm Output voltage 12V Output power 3.5W\~5W Working distance 35mm-110mm Specifications Internal diameter: 40mm External diameter: 70mm Height: 25mm Ring Diameter Inside Max φ39mm Weight 0.48KG

Parameters Description Working environment Temperature: 0℃~~40℃ Humidity: 20%RH~~85%RH Storage environment Temperature: -20℃~~40℃ Humidity: 20%RH~~85%RH

### 1.5 Camera Lens Parameter Description

_Table 1.3 Camera Lens Parameters Description_

Parameters Description Lens model MVL-HF1228M-6MP Focal distance 12mm Maximum imaging size 1/1.8＂(φ9mm) Aperture range F2.8-F16 Aperture Manual Control mode Focus Manual D 41.2° Field angle H 1/1.8＂ 34.4° V 23.4° Operating temperature -10℃\~+50℃ Optical distortion -0.38% Back focal length 17.526mm Shortest photography distance 0.06m Mount Mount C Filter M2&#x37;_&#x30;.5 Size φ29m&#x6D;_&#x33;5.36mm

## 2. Installation Instructions

### Installing Camera

Procedure

1. Fix the camera flange support to the bottom of the extension pole using screws.

_Figure 2.1 Install camera flange support_

2. Connect the two extension poles.

_Figure 2.2 Connect the two extension poles_

3. Fix the end of the extension pole with camera flange support to the camera holder using

four M4\*10 hexagon socket head screws.

![Figure 2.1 Install camera flange support](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6mU1wpd3PN9WINI2YG2L%2Fvision-p008-img02.jpg?alt=media)

![Figure 2.2 Connect the two extension poles](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVMdLQdvPAM1RdYLb1zz%2Fvision-p008-img03.jpg?alt=media)

_Figure 2.3 Fix extension pole_

4. Assemble the camera surpport using two M4\*10 hexagon socket head cap screws, as

shown in Figure 2.4.

_Figure 2.4 Install camera support_

5. Fix the camera support to the extension pole by adjusting the stationary fixture.

![Figure 2.3 Fix extension pole](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FswcPRJqIGmBjLGJ2GsTR%2Fvision-p009-img01.jpg?alt=media)

![Figure 2.4 Install camera support](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0iQqaYQpbNVKBEUjyz7B%2Fvision-p009-img02.jpg?alt=media)

_Figure 2.5 Fix the camera support_

**NOTE**

Please adjust the height of the camera support based on site requirements. Make sure that the camera support does not hinder the movement of robot.

6. Fix the camera to the camera mounting plate with three M3\*8 hexagon socket countersunk

head screws.

_Figure 2.6 Fix camera plate_

7. Fix the camera to the camera support using two M3\*6 hexagon socket head cap screws

![Figure 2.5 Fix the camera support](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsgMY6JI1K3cJxK6p9t0y%2Fvision-p010-img01.jpg?alt=media)

![Figure 2.6 Fix camera plate](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUstqL1hta2IMel7mezE0%2Fvision-p010-img02.jpg?alt=media)

and two 3mm washers.

_Figure 2.7 Fix camera mounting plate_

8. Connect the camera to the computer using a USB cable (plug the blue connector into

USB3.0 interface of the computer).

_Figure 2.8 Connect camera to computer_

9. Adjust camera parameters.

MVS is a software for adjusting camera parameters. You can get MVS software from the DobotVisionStudio package. Prerequisite:

* MVS has been installed.
* The camera has been connected to the computer.

Procedure:

![Figure 2.7 Fix camera mounting plate](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhRbF0AhwVf6uhQMuInya%2Fvision-p011-img01.jpg?alt=media)

![Figure 2.8 Connect camera to computer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqUe1uEnd6QXNBolmCDmo%2Fvision-p011-img02.jpg?alt=media)

1. Open MVS, and click to connect the camera.

_Figure 2.9 Connect camera_

_Figure 2.10 Connect camera successfully_

2. Click to capture an image.

![Figure 2.9 Connect camera](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsEgF9KaJLwjIaIYqoqjA%2Fvision-p012-img02.jpg?alt=media)

![Figure 2.10 Connect camera successfully](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVIBOpaw7endBDeyxRd4h%2Fvision-p012-img03.png?alt=media)

_Figure 2.11 Capture imaging_

3. Adjust the focal length, aperture, and exposure time according to the image.

* Adjust the focal length by rotating the aperture, and lock the focal length by rotating the helix switch.

_Figure 2.12 Adjust focal length_

**NOTE**

If there is not enough light in the environment, turn on the light source.

* Adjust brightness by rotating the aperture shown in the red box below, and lock the aperture by rotating the helix switch.

![Figure 2.11 Capture imaging](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Frrey6322WO4wqK22oJSB%2Fvision-p013-img01.png?alt=media)

![Figure 2.12 Adjust focal length](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdNyqYWaLGMQA743z8N6i%2Fvision-p013-img02.jpg?alt=media)

_Figure 2.13 Adjust aperture_

* Adjust exposure time or other parameters based on site requirements until imaging can be appeared clearly.

_Figure 2.14 Adjust exposure time or other parameters_

![Figure 2.13 Adjust aperture](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3ehLYPx4AtULzV4631iO%2Fvision-p014-img01.jpg?alt=media)

![Figure 2.14 Adjust exposure time or other parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrOORQuuyz4iCIC6v0mPe%2Fvision-p014-img02.jpg?alt=media)

![Figure 2.15 Result imaging](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNAxnNv8Hd4rKk5pt7aQr%2Fvision-p014-img03.png?alt=media)

10. Attach the light source kit to the camera, and fasten the kit with its three fixing knobs.

_Figure 2.16 Fasten the light source kit_

11. Connect the light source switch.

* Connect the light source switch to Magician

1. Connect the light source switch to the light source. 2) Plug the light source switch to the power interface of Dobot Magician. 3) Connect the light source switch to the power adapter of Dobot Magician.

_Figure 2.17 Connect light source switch_

* Connect the light source switch to M1 Pro

1. Connect the adapter cable to the M1 Pro light source switch. The red interface is 24V power interface, the black interface is GND interface. 2) Connect the M1 Pro light source switch to the light source.

![Figure 2.16 Fasten the light source kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FktddGygmYLGDj7wMqYG4%2Fvision-p015-img01.jpg?alt=media)

![Figure 2.17 Connect light source switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZEoLd4gJge7QX09LtaAq%2Fvision-p015-img02.jpg?alt=media)

3. Connect the adapter cable to the I/O interface on the base of Dobot M1 Pro, with red cable connected to 24V and black cable connected to GND.

_Figure 2.18 Connect light source switch_

**NOTE**

If you need to use light source switch and air pump box at the same time. Please connect the power cable of air pump box to the adapter cable. As shown below, the red interface is 24V power interface, and the black interfaces is GND interface.

_Figure 2.19 Connect air pump box_

![Figure 2.18 Connect light source switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHCGZl593SMKVlgPq61un%2Fvision-p016-img01.jpg?alt=media)

![Figure 2.19 Connect air pump box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtbDgIxEwbuNXDDuZN2zl%2Fvision-p016-img02.jpg?alt=media)

* Connect the light source switch to MG400

1. Connect the adapter cable to the M1 Pro light source switch. The red interface is 24V power interface, and the black interface is GND interface. 2) Connect the MG400 light source switch to the light source. 3) Connect the adapter cable to the I/O interface on the base of Dobot MG400, with red cable connected to 24V and black cable connected to GND.

_Figure 2.20 Connect MG400 to light source_

* Connect the light source switch to Magician E6

The light source is connected to the Magician E6 in the same way as the MG400, refer to the MG400 figure. 1) Connect the adapter cable to the light source switch (same as M1 Pro). The red interface is 24V power interface, and the black interface is GND interface. 2) Connect the light source switch to the light source. 3) Connect the adapter cable to the I/O interface on the base of Dobot Magician E6, with red cable connected to 24V and black cable connected to GND.

12. If it is necessary to use a robot to control the camera to take pictures (e.g., vision conveyor

tracking process), an aerial plug cable can be used to connect the camera to the robot. 1) Plug one end of the aviation plug cable into the aviation plug on top of the camera.

_Figure 2.21 Connect aviation plug cable to camera_

![Figure 2.20 Connect MG400 to light source](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FywdfOxQHDXc7ZCBAyR2W%2Fvision-p017-img01.jpg?alt=media)

![Figure 2.21 Connect aviation plug cable to camera](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGZgBy3TRjXJwaoLbPwIt%2Fvision-p017-img02.jpg?alt=media)

2. Connect the other end of the cable to the I/O connector on the base of the robot. The blue cable (I/O Input 1) is connected to any DO port, and the green cable (I/O GND) is connected to any GND port. Please refer to the cable label for the correspondence between cable color and function. The following figure takes MG400 as an example, other robotic arms have the same wiring method.

_Figure 2.22 Connect aviation plug cable to robot_

3. After completing the connection, trigger the corresponding DO of the robot to control the camera to take pictures. If you want to use the vision conveyor tracking process of MG400/M1 Pro, you can set the corresponding trigger IO port in the conveyor process setting interface.

_Figure 2.23 Setting the camera trigger DO_

![Figure 2.22 Connect aviation plug cable to robot](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz3xh4N8pg6Ct1FQbBeC8%2Fvision-p018-img01.jpg?alt=media)

![Figure 2.23 Setting the camera trigger DO](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCTDiq71smtizlqPKA3SR%2Fvision-p018-img02.png?alt=media)

### Installing Dobot Magician

Procedure

1. Fix Dobot Magician on the platform. For details, see Dobot Magician User Guide.
2. Adjust the camera support to ensure that the camera can view the workspace of Dobot

Magician.

_Figure 2.24 Install Dobot Magician_

### Installing Dobot M1 Pro

Procedure

1. Fix Dobot M1 Pro on the platform. For details, see Dobot M1 User Guide.
2. Adjust the camera support to ensure that the camera can view the workspace of Dobot M1

Pro.

![Figure 2.24 Install Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F641UlZDbtz7zjaRKr1wI%2Fvision-p019-img03.jpg?alt=media)

![Figure 2.25 Install Dobot M1 Pro](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHlD2InI38lnbsxDkOjoF%2Fvision-p019-img04.jpg?alt=media)

### Installing Dobot MG400

Procedure

1. Fix Dobot MG400 on the platform. For details, see Dobot MG400 User Guide.
2. Adjust the camera support to ensure that the camera can view the workspace of Dobot

MG400.

_Figure 2.26 Install Dobot MG400_

### Installing Dobot Magician E6

Procedure

1. Fix Dobot Magician E6 on the platform. For details, see Dobot Magician E6 User Guide.
2. Adjust the camera support to ensure that the camera can view the workspace of Dobot

Magician E6.

![Figure 2.26 Install Dobot MG400](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhWL4kM1rbWhy5UpkD6Nk%2Fvision-p020-img03.jpg?alt=media)
