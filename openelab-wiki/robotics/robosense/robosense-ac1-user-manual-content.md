# RoboSense AC1 User Manual Content

Product link: [https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale)

![RoboSense AC1 User Manual Content product image](<../../.gitbook/assets/robosense ac1 product (1).jpg>)RoboSense AC1 User Manual Content product image

This page is a local-file-based OpenELAB wiki copy of `AC1 .pdf`. The content below follows the extracted PDF page order as closely as possible. Contact/support blocks, emails, phone numbers, addresses, and working hours were omitted from the wiki copy.

Source note: Manual version 1.0, revision dated 2025-04-11. The source PDF contains an early E1R label while the main content refers to AC1.

## Manual Content

## Page 1

Version 1 .0

## Page 2

E1R User Guide 1

Change description

Version Revision Date Description

1.0 2025/04/11 Initial release

## Page 3

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

E1R User Guide 2

Reading Prompt

Warning: The usage process should be strictly followed, otherwise it may lead to potential dangerous situations such as minor injuries or property damage. Important: The usage process should be observed, otherwise it may cause potential harmful situations such as product damage. Tip: The usage process should be valued sufficiently to achieve maximum value of the product efficiently and smoothly. Please click the following link to download the latest product manual, RSview and other resources: [https://www.robosense.cn/resources](https://www.robosense.cn/resources) Manufacturer: Suteng Innovation Technology Co., Ltd. (RoboSense). Website: [https://www.robosense.cn/](https://www.robosense.cn/)

1213 Liuxian Avenue, Taoyuan Street, Nanshan District, Shenzhen, China

Symbolic instructions

Resource Download

More Information

## Page 4

AC1 User Guide 3

Content

Change description......................................................................................................... 1 Reading Prompt ............................................................................................................. 2 Content ........................................................................................................................... 3 Safety Notices ......................................................................................................... 4 Legal Statement ................................................................................................ 4 User Guidelines ................................................................................................. 4 Illegal Operation ............................................................................................... 4 Requirements for Operating Personnel ............................................................. 5 Work Safety and Special Hazards ..................................................................... 5 Product Description ................................................................................................ 7 Product Structure .............................................................................................. 7 Optical Envelope FOV Definition .................................................................... 7 Product Specifications ...................................................................................... 9 Product Installation ............................................................................................... 11 Product accessories ......................................................................................... 11 Interface specification ..................................................................................... 11 3.2.1 Interface and definition ......................................................................... 11 3.2.2 Power Interface ..................................................................................... 12 3.2.3 Data Interface ........................................................................................ 12 Product Usage ....................................................................................................... 13 Product Coordinate System............................................................................. 13 AC Viewer Useage .......................................................................................... 13 4.2.1 Install AC Viewer .................................................................................. 13 4.2.2 Use AC Viewer...................................................................................... 14 Communication Protocol ................................................................................ 14 Product Maintenance ............................................................................................ 18 Transportation and Logistics ........................................................................... 18 Storage ............................................................................................................ 18 Cleaning .......................................................................................................... 19 5.3.1 Attention ................................................................................................ 19 5.3.2 Required Materials ................................................................................ 19 5.3.3 Cleaning Method ................................................................................... 19 After-sale service .................................................................................................. 21 structural drawings ........................................................................... 22

## Page 5

AC1 User Guide 4

Safety Notices

Legal Statement

Unless otherwise stated, all rights (including copyrights, trademarks, patents, trade secrets, and other related rights) in RoboSense's products, t echnologies, software, programs, data, and other information (including text, icons, photographs, audio, video, graphics, color combinations, layout design, etc.) are owned by RoboSense and its licensors.

No one may use any content contained in this manual in any unauthorized manner

without the prior written consent of RoboSense. The words "RoboSense", " 速腾聚创", and other logos and product and service names are owned by RoboSense. If you need to use them for any advertising or display purposes, you must obtain prior written authorization from RoboSense.

User Guidelines

Please use this product in accordance with the following requirements: 1) Please strictly abide by relevant national laser safety laws and regulations; 2) Please read this product manual in detail before using the product; 3) Please use this product only in the relevant field of application; 4) Please avoid using this product in environments that are explosive, highly corrosive, or beyond the IP protection level of the equipment.

Illegal Operation

Please use this product in accordance with the regulations, otherwise it may cause product damage, property loss, and personal injury. Users are responsible for risk arising from unauthorized operations. 1) Do not disassemble or modify this product (including accessories); 2) Do not use power supplies and accessories that exceed specifications;

## Page 6

AC1 User Guide 5 3) Please avoid abnormal operations such as dropping, colliding, burning, etc.; 4) If you notice any damage to the appearance of the device, please immediately stop using it; 5) If you notice any abnormal operation of the product, please immediately stop using it and contact RoboSense in a timely manner.

Requirements for Operating Personnel

The use of this product requires certain basic professional knowledge and other

related requirements for operating personnel. Unreasonable operations performed by personnel without basic knowledge or training do not constitute a fault of RoboSense and may cause damage to equipment and personal property. 1) Please read the product manual in detail before using the device; 2) Prohibit illegal operations; 3) Before working, personnel must undergo training and obtain relevant construction qualifications; 4) Have some basic knowledge of computer data connection, electrical, and so on.

Work Safety and Special Hazards

To avoid risks of accidents, damage to sensor or violating of your product warranty, please read and follow the instructions in this manual carefully before operating the product. 1) Laser Safety: This product meets the following standards for laser products: IEC 60825-1:2014;： 2) High temperature warning: Please pay attention to the overheating sign on the AC1 surface to avoid a hot AC1 surface that may lead to sensor failure or undesirable consequences.

## Page 7

AC1 User Guide 6 3) Retain Instructions: The safety and operating instructions sho uld be retained for future reference. 4) Heed Warnings: All warnings on the product and in the operating instructions should be adhered to. 5) Servicing: Except for what’s described in this manual, the sensor has no field serviceable parts. For servicing, please contact RoboSense sales or the authorized distributors.

## Page 8

AC1 User Guide 7

Product Description

Product Structure

The shape diagram of AC1 is shown in Figure 1 . AC1 shape diagram

Optical Envelope FOV Definition

The optical envelope of the AC1 is shown in the figure below. After all limits are accumulated, the optical envelope of the AC1 cannot be blocked by external accessories, such as AC1 cover, forklift parts, and general mobile robot parts. After RoboSense is calibrated off the production line, there is a certain tolerance in the FOV Angle, which is subject to the final result of the manufacturer. Figure 2 shows partial FOV distribution of AC1 LiDAR. Figure 3 is a FOV diagram of the AC1 camera part.

## Page 9

AC1 User Guide 8 AC1 LiDAR FOV AC1 Camera FOV

## Page 10

AC1 User Guide 9

Product Specifications

AC1 (Active Camera 1) is a new type of active camera sensor developed by RoboSense, which combines the advantages of LiDAR and camera in sensing end and is mainly applied to robot env ironment perception. For specific parameters, refer to

Table 1.

AC1 Product Specifications

Product Specifications

LiDAR Part

Ranging

principle Time of Flight FOV(horizontal) 120° Wavelength 940 nm FOV(vertical) 60° safety class Class1 eye safe Angular resolution(horizontal) average 0.625°1 Ranging distance 2 20m @10% Angular resolution(vertical) Blind area 0.1 m@90% Ranging Precision3 ±3cm@1 sigma (indoor) ±5cm@1 sigma (outdoor)

Count of the

points \~173,333 points/second Frame rate 10Hz

RGB camera Part

Shutter type Rolling shutter FOV(horizontal) 144°

RAW output

format NV12，RGB24 FOV(vertical) 78° Frame rate 30Hz Resolution 1920\*800

IMU

Degree of

freedom 6 axis data output Gyroscope ±2000dps Accelerometer ±16g Data frequency 200Hz (adjustable) 1 The vertical & horizontal angular resolution is not uniform in the entire FOV . The angular resolution is 0.625° in the center of the FOV and 0.7° at the edges of the FOV; 2 The ranging capability of 30meters is measured with the 10% NIST diffuse reflector as the target, the test results may be affected by the environment conditions, including but not limited to factors such as ambient temperature and lights; 3 The ranging precision is tested in the range of 10m\~30m with 50% NIST diffuse reflector as the target. The test results may be affected by the environment conditions, including but not limited to factors such as ambient temperature and target distance. The precision value is applicable to most channels, but difference may exist between some channels.

## Page 11

AC1 User Guide 10

General

Form Standard probe module Power Consumption4 12.6 W (Typical)

Operating

Temperature 5 - 20℃ \~ + 60℃ Storage Temperature: - 20℃ \~ + 70℃

Protection

Rating IP 54 Weight 400g±10% Data interface USB 3.2 Gen1 Power interface DC

Size Outer Contour

length（mm） width（mm） height（mm）

95 42.6 80

4 The test results of product power consumption will be affected by external environment, including but not limited to environmental temperature, distance of target object, reflection intensity of target object and other factors; 5 The operating temperature of the product may be affected by the external environment, including but not limited to the lighting environment, air flow changes and other factors;

## Page 12

AC1 User Guide 11

Product Installation

Product accessories

The list of AC1 standard shipped accessories is shown in Table 2.

Connector scheme

No Parts name Specification Quantity

1 Active Camera AC1 1

2 Type-C data cable with screw lock 1m 1

3 DC power cord with screw lock 1m 1

4 DC adapter 12V⎓2A 1

5 Product specification 1

Interface specification

3.2.1 Interface and definition

Type-C with threaded lock pay, DC with threaded lock pay. As shown in .Figure 4

Direct Connection between LiDAR Equipment and Host Computer

DC interface pin definition: 1: VIN 2: GND

## Page 13

AC1 User Guide 12

3.2.2 Power Interface

The AC1 power supply uses standard DC 5.5-2.5 and DC 5.5-2.1 interfaces.

3.2.3 Data Interface

AC1 data transmission uses the standard USB3.2 GEN1 interface.

## Page 14

AC1 User Guide 13

Product Usage

Product Coordinate System

The AC1 coordinate system definition is shown in Figure 5 . AC1 Coordinate System Definition Please refer to wiki for how to obtain AC1 camera and IMU external parameters: [https://robosense-wiki-en.readthedocs.io/en/latest/ac\_studio/tools.html.](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools.html)

AC Viewer Useage

AC Viewer is a software designed for Active Camera and can be used to display all

Active Camera data (including point clouds, images) connected to the computer in real time. With AC Viewer, users can easily view, record, and store sensor data for later use.

4.2.1 Install AC Viewer

AC Viewer can run on Windows 64-bit, Ubuntu 18.04 or higher operating systems. From RoboSense AC Viewer's official website ( [https://www.robosense.ai/en/resources)](https://www.robosense.ai/en/resources)) to download the latest version of the software package. After the software is downloaded, do not contain Chinese characters in the decompression path. You do not need to install the software. After the decompression, run the executable file to use the software. The configuration requirements of PC hardware are shown in.

AC viewer requirements for PC configuration

## Page 15

AC1 User Guide 14

Minimum configuration Recommended configuration

CPU Seventh generation Intel Core

i3 or equivalent Intel 11500 or hugher, Mac M2 or higher GPU Integrated graphics NVIDIA RTX 3060 or above specifications RAM 8GB 16GB or higher Connection USB 3.0 USB 3.0 The physical connection of AC1 includes power cabl e connection and USB connection, and the USB connection is connected to the PC, as shown in Figure 6 AC1 Physical connection mode

4.2.2 Use AC Viewer

The AC viewer instruction manual can be found at wiki. The address of wiki is [https://robosense-wiki-en.readthedocs.io/en/latest/.](https://robosense-wiki-en.readthedocs.io/en/latest/)

Communication Protocol

The communication between AC1 and computer adopts USB 3.0 to output the data of IMU, LiDAR and image sensor. The data fields are shown as the data types. LiDAR output data structures include cloud\_point\_t and depth\_frame\_t. 1) cloud\_point\_t is relevant data for each point cloud, including x,y,z coordinates, reflection intensity, and timestamp information for the point cloud; 2) depth\_frame\_t is the data related to each frame point cloud, including the pixel

## Page 16

AC1 User Guide 15 width, height, image data format, time stamp and other information of each frame image. RGB output data structures is image\_frame\_t： 1) image\_frame\_t is the relevant data of each frame, including the pixel width, height, image data format, time stamp and other information of each frame. IMU output data structures is motion\_frame\_t: 1) motion\_frame\_t is the relevant data output of each frame of the IMU, including the measured value of the accelerometer and gyroscope in x,y, and z directions, temperature, and time stamp. AC1 data structure

Sensor Type Data field Data type Description

LiDAR

cloud\_point\_t points.x float 3D point cloud data x coordinates points.y float 3D point cloud data y coordinates points.z float 3D point cloud data z coordinates intensity uint8\_t 3D point cloud data reflection intensity depth\_frame\_t data void\* Pointer to depth data data\_bytes size\_t

Number of bytes of

the depth data buffer point\_nums uint16\_t

Number of points in

the depth data

RGB

image\_frame\_t width uint32\_t

The width of the

image in pixels

## Page 17

AC1 User Guide 16 height uint32\_t

The height of the

image in pixels frame\_format frame\_format\_t Format of image data step size\_t

The number of bytes

per line sequence uint32\_t

Serial number of the

image frame capture\_time struct timeval

Timestamp of image

data acquisition data void\* Pointer to image data data\_bytes size\_t number of bytes in the image data buffer

IMU

motion\_frame\_t accel.x float

Acceleration data of

the accelerometer in the X-axis direction (unit m/s²) accel.y float

Acceleration data of

the accelerometer in the Y-axis direction (unit m/s²) accel.z float

Acceleration data of

the accelerometer in the Z-axis direction (unit m/s²) gyro.x float

Angular velocity

data of the gyroscope

## Page 18

AC1 User Guide 17 in the X-axis direction (unit: dps, degrees per second) gyro.y float

Angular velocity

data of the gyroscope in the Y-axis direction (unit: dps, degrees per second) gyro.z float

Angular velocity

data of the gyroscope in the Z-axis direction (unit: dps, degrees per second) temperature float

Temperature data of

IMU sensor (unit: degrees Celsius) capture\_time struct timeval Timestamp of data collection

## Page 19

AC1 User Guide 18

Product Maintenance

Transportation and Logistics

Important

Improper transportation can cause damage to the equipment! 1) The products should be packaged with shock -proof and moisture -proof materials to avoid damage during transportation. It i s recommended to use original packaging; 2) During transportation, please handle the products carefully to avoid dangerous behaviors such as bumping and dropping; 3) Upon receiving each shipment, please thoroughly check the delivery list and product packaging fo r any damage (including physical damage to the products); 4) If there is any transportation damage, please refuse to accept the goods and contact RoboSense in a timely manner.

Storage

Important

Storage Inadequate can lead to equipment damage! 1) Please store the equipment in an indoor environment with normal temperature and dryness; 2) Handle the equipment carefully to avoid collisions, drops, and other dangerous behaviors; 3) The products should be stored in a safe environment to prevent corrosion, mechanical impact, and exposure to environments above the protective level; 4) Regularly check the status of all components and packaging. It is recommended to conduct inspections every 3 months.

## Page 20

AC1 User Guide 19

Cleaning

In order to be able to accurately sense the surrounding environment, AC1 needs to be kept clean, especially the window.

5.3.1 Attention

Please read the contents of this chapter carefully and completely before cleaning

your AC1, otherwise improper operation may damage the sensor. When the AC1 is used in a harsh environment, it is necessary to clean up the dirt on the surface in time to keep the AC1 clean, otherwise it will affect the normal use of the AC1.

5.3.2 Required Materials

1. Clean, dust-free cloths 2) Neutral solution at moderate temperature (such as soap water, distilled water, 99% alcohol concentration, etc.)

5.3.3 Cleaning Method

1. If only some dust/dust particles have adhered to the surface of the LiDAR: a) First, use a clean, dust-free cloth to dip into a small amount of neutral solution; b) Then, gently wipe and clean the AC1 surface; c) Finally, use a dry, clean, dust-free cloth to wipe it dry. 2) If mud or other blocky foreign objects have adhered to the surface of the AC1: a) First, clean water should be sprayed on the surface of the dirty part of the AC1 to remove foreign objects such as mud (Note: the mud cannot be wiped off directly with a dust -free cloth, which may scratch the surface, especially the surface of the window) b) Then, spray warm soap water on the dirty area to accelerate the removal of the foreign objects. Gently wipe the AC1 surface with a

## Page 21

AC1 User Guide 20 fiber cloth, but be careful not to scratch the surface; c) Finally, rinse the AC1 surface with clean water to remove any soap residue (if there are still traces left, you can use 99% alcohol to clean it again), and dry it with a dry, clean, dust-free cloth.

## Page 22

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

AC1 User Guide 21 After-sale service If you encounter any problems that cannot be solved during use, please contact RoboSense company in time. Official website: [https://www.robosense.cn/contact](https://www.robosense.cn/contact)

Note

1. Only after receiving confirmation of xx company's after-sales service, return the device; 2) The device can only be returned with the original packaging or equivalent moisture-proof packaging.

## Page 23

AC1 User Guide 22 structural drawings The structural drawings of AC1 are as follows:

## Page 24

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

Liuxian Avenue, Taoyuan Street, Nanshan District, Shenzhen, China www.robosense.ai

## Source Notes

* Review date: 2026-06-04.
* Local source file: `AC1 .pdf`.
* Product link: [https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale)
* Content basis: local PDF text extraction with page markers preserved.
* Omitted content: manufacturer contact emails, phone numbers, addresses, working hours, and support contact blocks.
