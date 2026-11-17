# RoboSense EM4 User Manual Content

Product link: [https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar](https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar)

![RoboSense EM4 User Manual Content product image](<../../.gitbook/assets/robosense em4 product (2).png>)RoboSense EM4 User Manual Content product image

This page is a local-file-based OpenELAB wiki copy of `RS-EM4_UserGuide_v1.1_EN.pdf`. The content below follows the extracted PDF page order as closely as possible. Contact/support blocks, emails, phone numbers, addresses, and working hours were omitted from the wiki copy.

Source note: EM4 User Manual V1.1.0, revision dated 2025-05-15.

## Manual Content

## Page 1

Manual version V1.1.0 EM4

User Manual

## Page 2

EM4 User Manual 1

Revision History

Version Date Description Author

1.0.0 2024/12/14 First version release PD

1.1.0 2025/05/15 Modify the content of DIFOP data. PD

## Page 3

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

EM4 User Manual 2

Reading Prompt

Warning: The usage process should be strictly follo wed, otherwise it may lead to potential dangerous situations such as mi nor injuries or property damage to potential dangerous situations such as minor injuries or property damage Important: The usage process should be observed, otherwise it may cause potential harmful situations such as product damage Tips: The u sage process should be valued sufficiently to achieve maximum value of the product efficiently and smoothly. Please click the following link to download the latest product manual, RSview and other resources: [https://www.robosense.cn/resources-114](https://www.robosense.cn/resources-114) Manufacturer: Suteng Innovation Technology Co., Ltd. (RoboSense). Website: [https://www.robosense.cn/](https://www.robosense.cn/)

1213 Liuxian Avenue, Taoyuan Street, Nanshan District, Shenzhen, China

Symbol Illumination

Resource Download

More Information

## Page 4

EM4 User Manual 3

Content

Revision History ............................................................................................................ 1 Reading Prompt ............................................................................................................. 2 Content ........................................................................................................................... 3 Safety Notices ......................................................................................................... 5 Legal Statement ................................................................................................ 5 User Guidelines ................................................................................................. 5 Illegal Operation ............................................................................................... 5 Requirements for Operating Personnel ............................................................. 6 Work Safety and Special Hazards ..................................................................... 6 Product Description ................................................................................................ 8 Product Overview ............................................................................................. 8 Product Structure .............................................................................................. 8 FOV Distribution .............................................................................................. 9 Specifications .................................................................................................... 9 Time Synchronization Mode ........................................................................... 10 2.5.1 gPTP synchronization principle ............................................................ 10 2.5.2 gPTP wiring method ............................................................................. 11 Product Installation ............................................................................................... 12 LiDAR Wiring and Interface Instructions ....................................................... 12

3.1.1 Interface and definition of onboard Ethernet harness ........................... 12

3.1.2 Interface Box ......................................................................................... 13 3.1.3 Power interface ..................................................................................... 13 3.1.4 RJ45 Ethernet port ................................................................................ 14 Quick Connection ........................................................................................... 14 Product usage ........................................................................................................ 17 Product Coordinate System............................................................................. 17 RSView Usage ................................................................................................ 17 4.2.1 Software Functions ............................................................................... 18 4.2.2 Installing RSView ................................................................................. 18 4.2.3 Using RSView ....................................................................................... 18 Communication Protocol ................................................................................ 19

4.3.1 Main data Stream Output Protocol（MSOP）..................................... 19

4.3.2 Device Information Output Protocol（DIFOP） ................................. 22

Fault diagnosis ...................................................................................................... 28

## Page 5

EM4 User Manual 4 Product maintenance ............................................................................................. 30 Transportation and Logistics ........................................................................... 30 Storage ............................................................................................................ 30 Product Cleaning ............................................................................................. 30 6.3.1 Precautions ............................................................................................ 31 6.3.2 Required Materials ................................................................................ 31 6.3.3 Cleaning methods.................................................................................. 31 After sales ............................................................................................................. 33 ROS\&ROS2 Package .............................................................................. 34 Definition of TE connector pins .............................................................. 35

## Page 6

EM4 User Manual 5

Safety Notices

Legal Statement

Unless otherwise stated, all rights (including copyrights, trademarks, patents, trade secrets, and other related rights) in RoboSense's products, technologies, software, programs, data, and other information (in cluding text, icons, photographs, audio, video, graphics, color combinations, layout design, etc.) are owned by RoboSense and its licensors

No one may use any content contained in this manual in any unauthorized manner

without the prior written consent of RoboSense. The word "RoboSense" and other logos and product and service names are owned by RoboSense. If you need to use them for any advertising or displaying purposes, you must obtain prior written authorization from RoboSense

User Guidelines

Please use this product in accordance with the following requirements: 1) Please strictly abide by relevant national laser safety laws and regulations; 2) Please read this product manual in detail before using the product; 3) Please use this product only in the relevant field of application; 4) Please avoid using this product in environments that are explosive, highly corrosive, or beyond the IP protection level of the equipment.

Illegal Operation

Please use this product in accordance with the regulations, otherwise it may cause product damage, property loss, and personal injury. Users are responsible for risk arising from unauthorized operations. 1) Do not disassemble or modify this product (including accompanying accessories);

## Page 7

EM4 User Manual 6 2) Non-specified power supply and accompanying accessories are prohibited; 3) Please avoid abnormal operations such as dropping, colliding, burning, etc.; 4) If you notice any damage to the appearance of the device (arc protection cover), please immediately stop using it; 5) If you notice any abnormal operation of the product, please immediately stop using it and contact RoboSense in a timely manner.

Requirements for Operating Personnel

The use of this product requires certain basic professional knowledge and other

related requirements for operating personnel. Unreasonable operations performed by personnel without basic knowledge or training do not constitute a fault of RoboSense and may cause damage to equipment and personal property. 1) Please read the product manual in detail before using the device; 2) Prohibit illegal operations; 3) Before working, personnel must undergo training and obtain relevant construction qualifications; 4) Have some basic knowledge of computer data connection, electrical, and so on.

Work Safety and Special Hazards

To avoid risks of accidents, damage to sensor or violating of your product warranty, please read and follow the instructions in this manual carefully before operating the product. 1) Laser Safety: This product meets the following standards for laser products: IEC 60825-1:2014; 2) High Temperature Warning: Please pay attention to the overheating sign on the LiDAR surface to avoid a hot LiDAR surface that may lead to sensor

## Page 8

EM4 User Manual 7 failure or undesirable consequences. 3) Retain Instructions: The safety and operating instructions should be retained for future reference. 4) Heed Warnings: All warnings on the product and in the operating instructions should be adhered to. 5) Servicing: Except for what’s described in this manual, the sensor has no field serviceable parts. For servicing, please contact RoboSense sales or the authorized distributors

## Page 9

EM4 User Manual 8

Product Description

The following content describes the status and functions of the EM4-B0 prototype. After the release of the new version of the prototype, the product manual will be updated to the latest status synchronously.

Product Overview

EM4 is a high -performance automotive-grade LiDAR. The maximum detection range is 300 meters, and the resolution of FOV(Filed of View) can reach 0.1 ° (H) x

0.05 ° (V).

Product Structure

The structure of EM4 LiDAR is illustrated in Figure 1.

Figure 1 Product Structure of EM4 LiDAR

## Page 10

EM4 User Manual 9

FOV Distribution

EM4 LiDAR’s FOV are listed in Table 1.

Table 1 EM4 FOV

Specifications Horizontal

FOV

Vertical FOV

25° FOV -60° \~ +60° -12.5° \~ +12.5°

Figure 2 EM4-B0 LiDAR FOV

Specifications

Table 2 Parameter specifications

Sensor

Measurement

Range1 300m @10% NIST1， 100klux Accuracy2 （Typical） ±5 cm@1σ Horizontal FOV 120°（-60° \~ +60°）

Horizontal Angle

Resolution

\~0.1° 1 The ranging capability is based on a 10% NIST diffuse reflector as the target, and the test results may be affected by environmental factors, including but not limited to environmental temperature, light intensity, etc; 2 The ranging accuracy is based on a 90% NIST diffuse reflector as the target, and the test results may be affected by environmental factors, including but not limited to environmental temperature, target object distance, etc;

## Page 11

EM4 User Manual 10 Vertical FOV 25°（-12.5°\~+12.5°）

Vertical Angle

Resolution

\~0.05°

Time Synchronization Mode

EM4 currently supports gPTP (IEEE802.1AS protocol) synchronization mode. If users have special requirements, please contact RoboSense.

2.5.1 gPTP synchronization principle

GPTP (General Precise Time Protocol, IEEE802.1AS protocol) is a derivative protocol of PTP in Time Sensitive Networking. The synchronization mechanism adopts the Peer Delay Mechanism, which is consistent with the PTP protocol, and also uses 3．The power consumption test results of the product may be affected by external factors, including but not limited to environmental temperature, distance from the target object, and reflection intensity of the target object; 4．The operating temperature of the product may be affected by external environmental factors, including but not limited to lighting conditions, airflow changes, and other factors;

Output

PPS 6,240,000 pts/s (single return mode) Ethernet Output 1000Base-T1

Communication

Protocols UDP

Data Package 3D spatial coordinates, reflection intensity, timestamps, etc

Mechanical and Electrical Specifications

Supply V oltage 12V (9V\~16VDC) Dimension(L\* W\*H) Depth 150mm \* Width 119mm \* Height 45mm (B prototype)

Power

Consumption 16W（Typical） Operating Temperature3 -40℃ \~ +85℃ Weight <1000g storage temperature -40℃ \~ +105℃

Time

Synchronization gPTP Protection

Level IP67/IP6K9K Frame 10 Hz Blind Zone 1m

## Page 12

EM4 User Manual 11 Ethernet L2 layer communication. Unlike PTP, gPTP requires the use of hardware timestamp, which means hardware timestamp, so the requirements for switc hes and Master clocks are more stringent and must meet the IEEE802.1AS protocol.

2.5.2 gPTP wiring method

To use gPTP synchronization method, the following preparations need to be made: 1) GPTP Master timing host (plug and play, no additional configuration required); 2) Ethernet switch; 3) Devices that support gPTP protocol for waiting to be taught.

Prompt explanation

1. The Master timing device is a third -party device and is not included in RoboSense shipments. Users need to purchase it themselves; 2) The RoboSense product, as a Slave device, only obtains the time sent by the Master and does not judge the accuracy of the Master clock source. If there is a sudden change in the time when analyzing the LiDAR point cloud, please check if the time provided by the Master is accurate; 3) After the synchronization of the LiDAR, the Master disconnects, and the time in the point cloud data packet will be superimposed according to the internal clock of the LiDAR. The LiDAR will only be reset after it is powered off and restarted.

## Page 13

EM4 User Manual 12

Product Installation

LiDAR Wiring and Interface Instructions

3.1.1 Interface and definition of onboard Ethernet harness

EM4 uses one automotive Ethernet and power supply two in one connector, and the matching wiring harness is shown in Figure 3.

Figure 3 Vehicle Ethernet power harness

The definitions of EM4 vehicle Ethernet power harness connectors and pins are shown in Table 3

Table 3 Definition of Ethernet power harness interface for onboard vehicles

A side Definition B side

J1 (TE 2387380-1)

1 VBat

J3 (Molex 43025-0600)

2 Wakeup

3 /

4 GND

5 CANFD\_H

## Page 14

EM4 User Manual 13

6 CANFD\_L

7 1000BASE-T1 N J2

(Amphenol NTHCF011A10S) 8 1000BASE-T1 P

3.1.2 Interface Box

Figure 4 Interface Box

The EM4 interface box has a power indicator light and various interfaces, as shown in Figure 4, which can be connected to power input and RJ45 network port.

Table 4 Definition of Interface Box

Interface Interface Name Function Description

J1 Power Wake-up Signal Provide power to the radar and output wake -up signals J2 Network 1000BASE-T1 vehicle Ethernet interface J3 DC Power connector External power input J4 Switch Wake up signal control switch, when the switch is pressed, the wake-up signal is turned on J5 RJ45 1000BASE-TX Industrial Ethernet

3.1.3 Power interface

The EM4 interface box power supply uses a standard DC 5.5-2.1 interface.

## Page 15

EM4 User Manual 14 When the power input is normal, the green indicator light on the power box remains on. When the green indicator light goes out, please check if the power input is normal. If the power input is normal, the interface box may be damaged. Please contact RoboSense.

3.1.4 RJ45 Ethernet port

The interface box only supports Gigabit Ethernet, and when using the interface box, the network interface uses a standard RJ45 interface.

Quick Connection

The EM4 network parameters can be configured, and the factory default uses a fixed IP and port number mode. Please refer to Table 5 for details.

Table 5 Factory default network configuration table

equipment IP address MSOP package slogan DIFOP packet slogan EM4 192.168.1.200 6699 7788 PC 192.168.1.102 When users use the product, they need to set the computer's IP to be on the same network segment as the product, such as 192.168.1. x (x values range from 1 to 254), with a subnet mask of 255.255. 255.0. Unknown product network configuration information, please connect the product and use Wireshark to capture the product output packet for analysis. Configure the IP and connection method as follows. 1) Connect the LiDAR The connection method is shown in Figure 5. a) The laser radar is connected to the interface box through a vehicle mounted Ethernet power harness; b) The PC and interface box are connected using Gigabit Industrial Ethernet through RJ45 network port connectors; c) After power on, under normal working conditions, the green indicator light of the interface box of the laser radar will remain on, and the location details of the indicator light are shown in Figure 5.

## Page 16

EM4 User Manual 15

Figure 5 Schematic diagram of interface box connection

1. Capture pa ckets through Wireshark, parse ARP packets for local IP configuration a) As mentioned above, after the laser radar is connected to the PC, start Wireshark (a third -party network analysis tool), select the correct network port, and start capturing packets; b) Enter "ARP" in the search box of Wireshark to search for mutual addressing messages between the LiDAR and PC, as shown in Figure 6;

Figure 6 Analyzing ARP Messages

c) As shown in Figure 6, the word SutengIn in the Source column indicates the information source of the LiDAR, and prompts 192.168.1.200 as the Source IP, which is the LiDAR IP. Then request access to 192.168.1.102, which is the PC IP. If the local IP is not the requested IP, the local IP of the PC needs to be configured as 192.168.1.102. For details, please refer to step 3); If it can be accessed normally, proceed to step 4). 3) Configure the local IP of the PC a) In the control panel, enter the "Network and Sharing Center" through "Network and Internet", click on the corresponding Ethernet connectio n in the "View Active Networks" content, enter the corresponding "Ethernet Status", and

Power Supply

Host Computer

Switch

## Page 17

EM4 User Manual 16 click on the "Properties" settings; b) Double click on Internet Protocol version 4 (TCP/IPv4) to enter IP information settings and configure using a static IP address; c) Set the local IP address to 192.168.1.102 and subnet mask to 255.255.255.0. Click "Confirm" to complete the static IP setting for the PC. 4) Connection completed

Prompt explanation

1. The time synchronization module (gPTP) is not a factory standard product. If you need to use related functions, please purchase them yourself. 2) The above configuration of local static IP is only for Windows system operation as an example. For other operating systems, please refer to the actual situation. 3) EM4 adopts a static ARP list, which only sends ARP packets after the radar is powered on and before it is connected to the upper computer. If the upper computer is replaced after normal communication between the radar and the upper computer, the radar needs to be powered on again to communicate with the new upper computer.

## Page 18

EM4 User Manual 17

Product usage

Product Coordinate System

The vehicle coordinate system is shown in Figure 7.

Figure 7 Schematic diagram of vehicle coordinates

The coordinate system of the product is shown in Figure 8.

Figure 8 Schematic diagram of LiDAR coordinates

RSView Usage

In terms of data visualization for EM4, free tools such as Wireshark and tcpdump can be used to capture raw data, while RSView can help users visualize raw data more conveniently Optical Center/

Coordinate Origin

## Page 19

EM4 User Manual 18

4.2.1 Software Functions

RSView provides real -time visualization of EM4 data. RSView can also replay data saved in. pcap file format, but currently does not support. pcap format files. RSView displays the distance measurement value obtained by EM4 as a point. It can support multiple custom colors to display data, such as reflection intensity, time, distance, horizontal angle, and laser beam number. The displayed data can be exported and saved in. csv format. RSView includes the following features: 1) Real time display of data through Ethernet; 2) Save real-time data records as PCAP files; 3) Replay from the recorded PCAP file; 4) Different types of visualization modes, such as distance, time, horizontal angle, etc; 5) Display point data in a table; 6) Export point cloud data to CSV format file; 7) Measuring distance tools; 8) Display multiple consecutive frames of playback data simultaneously; 9) Show or hide individual wiring harnesses (channels) in EM4; 10) Crop display.

4.2.2 Installing RSView

RSView supports running on Windows 64 bit, Ubuntu 18.04 and above operating systems. Download link for the latest version of RSView software installation package: [http://www.robosense.cn/resources](http://www.robosense.cn/resources) The decompression path of the software should not contain Chinese characters.

The software does not need to be installed and can be used normally by running the

executable file after decompression.

4.2.3 Using RSView

## Page 20

EM4 User Manual 19 After opening RSview, in the software interface, the software user guide can be opened by pressing the F1 button, or by clicking on the RS LiDAR User Guide option in the software menu bar.

Communication Protocol

The communication between EM4 and the computer uses Ethernet medium and UDP protocol. There are two types of output packets: MSOP packet and DIFOP packet. The fixed length of all MSOP protocol packets mentioned in the document is 1084 bytes, and the fixed length of DIFOP protocol packets is 1310 bytes. The network parameters of EM4 can be configured by contacting the technical support department. By default, the fixed IP and fixed destination port number mode is used. The communication between EM4 and the computer adopts Ethernet medium and UDP protocol. The communication protocol between EM4 and the computer is mainly divided into two categories, as shown in Table 6 for details.

Table 6 List of Product Agreements

(Protocol/Package)

Name

Abbreviation Function Type Package

size

Sending

interval

Main data Stream Output

Protocol MSOP Scan data output UDP 1084 bytes 24,000 times/s

Device Information

Output Protocol DIFOP

Product

information output UDP 1310 bytes 10 times/s

Prompt explanation

1. The main data stream output protocol MSOP encapsulates the distance, angle, reflection intensity, and other information scanned by the LiDAR into packets for output; 2) The product information output protocol DIFOP outputs various configuration information of the current state of the LiDAR.

4.3.1 Main data Stream Output Protocol（MSOP）

I/O type: Product output, computer parsing. The default port number at the factory is 6699.

## Page 21

EM4 User Manual 20 The basic structure is shown in the figure below:

Figure 9 MSOP Packet Data Packet Definition Schematic Diagram

4.3.1.1 Frame Header

The frame header consists of 32 bytes, used to identify the starting position of the data, packet count, reserved for UDP communication, and to store the timestamp. For detailed definitions, see Table 7.

Table 7 Frame Header

Content Offset(b yte) Byte Instruction

## Page 22

EM4 User Manual 21 pkt\_head 0 4 header：55aa5aa5 PL assignment, transparent transmission between R and

A cores

Pkt\_cnt 4 2 Packet cnt：loop packet counter Single Wave:1~~2400 Double Wave:1~~4800 There are 1200 column, each column wave pack 2 msop FOV:26(pitch)\*120(yaw) Protocal version 6 2 UDP protocol version return\_mode 8 1 4:Strongest Wave 5:Last Wave 6:Nearest Wave time\_mode 9 1 Time synchronization method: 0x00: Internal time 0x02: PTP 0x03: gPTP timestamp 10 10

Timestamp

Byte0~~5: s Byte6~~9: us frame\_sync

20 1

Frame synchronization

0x00:Not synchronized 0x01:Synchronized lidar\_health 21 1 column\_num 22 2 Column Number:0\~1199 yaw\_angle 24 2 yaw angle: factor:0.01 deg pack mode

26 1

PackMode

0x01: without compress 0x03: with compress if the length of the package is over than 1368, split the over byte to next package bit7\~4 indicates split package number 0: no split 1: 1st pack 2: 2nd pack surface id

27 1

Surface

0x01:A 0x02:B 0x03:C 0x04:D frame rate 28 1 0:10Hz 1:20Hz reserved 29 1 lidar\_type 30 1 Default:0x70

## Page 23

EM4 User Manual 22 main\_temp 31 1 fpga temperature:factor:1, offset:-80, Unit:°C

4.3.1.2 Data Block

The data block interval is the measurement value section of the sensor in the

MSOP packet, totaling 1040 bytes. It consists of 260 data blocks, each with a length of

4 bytes. In single echo mode, the EM4 has 260 point data echo data in each MSOP,

corresponding to 260 data points. The resolution of the EM4 is 5201200, so in single echo mode, a total of 5201200/260=2400 packets are needed to transmit a complete frame of image data over Ethernet. The detailed definition of each point data can be found in Table 8: Table8 Packet definition of point data n point data (4 Bytes) content offset(byte) byte instruction radius 0 2 In polar coordinate system, the radial point distance value has a distance resolution of 5mm intensity 2 1 range:0\~255 point\_attribute 3 1 point attribute 0x01:normal point 0x02:noise point

4.3.1.3 Data Block Interval

The frame tail length is 12 bytes and is reserved.

4.3.2 Device Information Output Protocol（DIFOP）

I/O type: Product output, computer parsing. The default port number at the factory is 6699. DIFOP is a "Output-only" protocol designed to periodically send information such as device serial number (S/N), firmware version, upper computer driver comp atibility, network configuration, calibration info, motor operation configuration, operational status, and fault diagnosis information to the user. Users can read DIFOP to interpret detailed information about various parameters of the current device in use. The DIFOP of EM4 is divided into 2 parts, where DIFOP1 has a transmission cycle of 20ms and

## Page 24

EM4 User Manual 23 DIFOP2 has a transmission cycle of 2 seconds. The basic structure of the data packet is shown in Table 9,10.

Table 9 DIFOP1 Data Sheet

Difop1 Name Data

Offset Length Type Range Description

Header StatusHdr 0 4 XNbytes 0xa5ff005a A5 FF 00 5A

Version

BootPN 4 4 XNbytes PSPN 8 4 XNbytes ALPN 12 4 XNbytes PL0PN 16 4 XNbytes sub pl PL1PN 20 4 XNbytes main pl SWVersion 24 3 XNbytes HWVersion 27 2 XNbytes Default:B0

SerialNumber

IntSN 29 6 XNbytes 0x0000000

00000 0xFE89

CustomerS

N 35 16 XNbytes 0x2109100 0

WorkInformation

WorkMode 51 1 XByte 0x0a 0x01: Init 0x02: Wait\_Normal 0x03: Pre\_Reset 0x04: Post\_Reset 0x05: Standby 0x06: Pre\_Sleep 0x07: Post\_Sleep 0x08: Fault 0x0A: Normal others：Reserved FrameRate 52 1 XByte 0x0A 0x0A:10Hz 0x14: 20Hz

## Page 25

EM4 User Manual 24 WaveMode 53 1 XByte 0x04 0x00:NearestFarthestWa ve 0x04:StrongestWave 0x05:FarthestWave 0x06:NearestWave 0x0A:Hist 0x0B:Gray ROIMode 54 1 XByte

Calibration

Mode 55 1 XByte 0x00: Normal mode 0x01: Factory mode

TotalRunnin

gTime 56 4 XNbytes

IgnitionRun

ningTime 60 2 XNbytes

IgnitionCou

nter 62 2 XNbytes Lidar\_Heate r\_Status 64 1 XNbyte Lidar\_Heate r\_State\_Ma chine\_Statu s

65 1 XNbyte

WindowBlo

ckageStatus 66 1 XNbyte

WindowBlo

ckageLevel 67 18 XNbytes Res1 85 4 XNbytes

TimeSyncInfoma

tion

TimesyncM

ode 89 1 XByte 0x03 0x00: internal Src timer 0x01: PPS timer 0x02: E2E L2 timer 0x03: gPTP timer 0x04: p2p L4 timer

TimesyncSt

atus 90 1 XByte 0x00 0x00: failed 0x01: Success 0x02: Timeout TimeStamp 91 10 XNbytes 0x0000000 002083a66d 47b 0-5 bytes: Second 6-9 bytes: MicroSecond

## Page 26

EM4 User Manual 25

NetParameter

PhyMasterS

laveMode 101 1 XByte 0x00 0x00: auto-negotiation 0x01: master SrcIP 102 4 IP 192.168.1.2

00 Default:C0 A8 01 C8

NetMask 106 4 IP 255.255.25

5.0 Default:FF FF FF 00

MacAddress 110 6 MAC

08 48 57 00

FB B1 Default:08 48 57 00 FB B1 MsopDstIp 116 4 IP 192.168.1.1 02 Default:C0 A8 01 66

MsopSrcPor

t 120 2 UnShort

6699 Default:1A 2B

MsopDstPor

t 122 2 UnShort

6699 Default:1A 2B

Difop1DstIp 124 4 IP 192.168.1.1 02 Default:C0 A8 01 66 Difop1SrcP ort 128 2 UnShort

7788 Default:1E 6C

Difop1DstP ort 130 2 UnShort

7788 Default:1E 6C

Difop2DstIp 132 4 IP 192.168.1.1 02 Default:C0 A8 01 66 Difop2SrcP ort 136 2 UnShort

7766 Default:1E 56

Difop2DstP ort 138 2 UnShort

7766 Default:1E 56

DoIPDstIp 140 4 IP 192.168.1.1 02 Default:C0 A8 01 66

DoIPSrcPor

t 144 2 UnShort

13400 Default:34 58

DoIPDstPor

t 146 2 UnShort

0 Default:00 00

LogicalEcu

Address 148 2 XNbytes 0x0001 Default: 00 01

LogicalFunc

Address 150 2 XNbytes 0xE400 Default: E4 00

LogicalTest

erAddress 152 2 XNbytes 0x0E00 Default: 0E 00

## Page 27

EM4 User Manual 26 NetAddr 154 2 XNbytes 0x00 Default: 00 Voltage & Temp Voltage\&Te mp 156 60 XNbytes

Fault

IntPowerSu

pplyFault 216 3 XNbytes 0x000000 0:No error 1:Fault

IntTempFau

lt 219 3 XNbytes 0x000000 0:No error 1:Fault

IntSoftware

Fault 222 3 XNbytes 0x000000 0:No error 1:Fault

Performanc

eFault 225 4 XNbytes 0x0000000 00000 0:No error 1:Fault

LidarFuncti

onFault 229 1 XNbytes

ExtPowerSu

pplyFault 230 1 XNbytes CommFault 231 2 XNbytes

FaultStatus

FaultLevel 233 1 XNbytes 0x00 FaultID 234 2 XNbytes FaultValue 236 4 XNbytes 0x00 0x00: No fault 0x01: FL1 0x02: FL2 0x03: FL3 DTCList 240 4 XNbytes E2E DataLength 244 2 UnShort 256 01 00 Counter 246 2 XNbytes 00 00\~FF FF DataId 248 4 XNbytes 0x00000e5c 00 00 0E 5C Crc32 252 4 XNbytes

## Page 28

EM4 User Manual 27

Table 10 DIFOP2 Data Sheet

Difop2 Name Data Offset Length Type Range Description Header InfoHdr 0 4 XNbyte s 0xa5ff00ae A5 FF 00 AE Reserved Res0 4 63 XNbyte s

AngleInformation

SurfaceCnt 67 1 XByte 0x04 there are 4 surface:A B C D

VcselPixelC

nt 68 1 XByte 0x14 1 vcsel:20 pixel VcselCnt 69 1 XByte 0x1A 1 column:26 vcsel

VcselYawOf

fset 70 26 XNbyte s factor:0.01

1 vcsel:20 pixel

1 column:520 pixel: 26

vcsel PixelPitch\[1 ~~520] 96 1040 XNbyte s channel 1~~520 pitch: factor 0.01 deg

SurfacePitch

Offset 1136 8 XNbyte s byte0\~1: Surface A Pitch

Offset

byte2\~3: Surface B Pitch

Offset

byte4\~5: Surface C Pitch

Offset

byte6\~7: Surface D Pitch

Offset

RollOffset 1144 2 XByte factor:0.01 Res1 1146 4 XNbyte s 0x00000000 E2E DataLength 1150 2 UnShor t Counter 1152 2 XNbyte s 00 00\~FF FF DataId 1154 4 XNbyte s 0x00005aa5 00 00 5A A5 Crc32 1158 4 XNbyte s

## Page 29

EM4 User Manual 28

Fault diagnosis

This chapter lists some common problems encountered during the use of the

product and corresponding troubleshooting methods. Please refer to Table 11 for details.

Table 11 Common Troubleshooting Methods

Fault phenomenon resolvent

The red/green indicator light on the interface box is not on/flashing

Check if the connection wire between the interface box

and the power end is loose; Check if the wiring harness is damaged.

The product keeps restarting during

startup

Check if the input pow er connection and polarity are

normal;

Check whether the voltage and current of the input

power supply meet the requirements (under the condition of 12V voltage input, the input current is ≥ 2A); Wireshark can receive data, but

RSView does not display point clouds

Turn off the computer firewall and run RSView to pass

through the firewall;

Confirm that the IP configuration of the computer

matches the destination address set for the product;

Confirm that the Sensor Network Configuration

setting in RSView is correct;

Confirm that the RSView installation directory or

configuration file storage directory does not contain any Chinese characters;

Confirm that the received packet in Wireshark is of

MSOP type.

Frequent data loss of products

Confirm whether there are a large number of other

network packets or network conflicts in the network;

Confirm whether there are other network products in

the network that are sending large amounts of data in broadcast mode, causing sensor data blockage;

Confirm whether the performance and interface

performance of the computer meet the requirements;

Remove all other network products and connect

directly to the computer to confirm if there is any packet loss.

## Page 30

EM4 User Manual 29

Unable to synchronize gPTP time

Confirm whether the radar firmware matches the

required synchronization mode; In gPTP time synchronization mode:

Confirm whether the gPTP Master synchronization

protocol complies with the current gPTP protocol; Confirm if gPTP Master is working properly.

The product has no data output after

passing through the router

Turn off the DHCP fun ction of the router or set the

sensor's IP address to the correct IP address inside the router.

Prompt explanation

If the above troubleshooting fails to solve the problem, please contact RoboSense.

## Page 31

EM4 User Manual 30

Product maintenance

Transportation and Logistics

Important

Improper transportation can lead to product damage! 1) Products should be packaged with shockproof and moisture -proof packaging materials to avoid damage during transportation. Suggest using the original packaging; 2) During transportation, be careful and hand le with care to avoid dangerous behaviors such as collision and falling; 3) Every time the goods are received during transportation, a detailed inspection of the delivered goods list and whether there is any damage (including products and packaging) must be carried out; 4) If there is any transportation damage, please refuse to receive the goods and contact RoboSense promptly.

Storage

Important

1. Please store the product indoors at room temperature and in a dry environment; 2) Please handle with care to prevent the pr oduct from being bumped, dropped, etc; 3) The product should be stored in a safe environment, avoiding corrosion, mechanical impact, and exposure to environments beyond the protection level; 4) Please regularly check the status of all components and packaging, w ith a recommended inspection cycle of 3 months.

Product Cleaning

In order to accurately perceive the surrounding environment, RS LiDAR needs to

## Page 32

EM4 User Manual 31 keep the annular protective cover clean.

6.3.1 Precautions

Please read this section carefully and completely before cl eaning the RS LiDAR, otherwise improper operation may damage the product. When using a LiDAR in harsh environments, it is necessary to promptly clean the surface dirt to keep the LiDAR clean, otherwise it will affect the normal use of the LiDAR.

6.3.2 Required Materials

1. Clean and dust-free cloth; 2) Neutral solutions with moderate temperature (such as soapy water, distilled water, 99% concentration ethanol, etc.).

6.3.3 Cleaning methods

1. If the surface of the LiDAR only adheres to some dust/dirt: a) Firstly, u se a clean and dust -free cloth to dip a small amount of neutral solution; b) Next, gently wipe and clean the surface of the LiDAR; c) Finally, dry it with a dry and clean dust-free cloth. 2) If the surface of the LiDAR is stained with lumps of foreign matter such as mud: d) Firstly, clean water should be sprayed onto the surface of the dirty area of the LiDAR to remove mud and other foreign objects (note: do not directly wipe off the mud with a dust -free cloth, as this may scratch the surface, especially th e protective cover surface); e) Next, spray warm soapy water on the dirty area, as the lubricating effect of soapy water can accelerate the detachment of foreign objects. Gently wipe the surface of the laser radar with a fiber cloth again, but be careful n ot to scratch the surface;

## Page 33

EM4 User Manual 32 f) Finally, clean the soap residue on the surface of the LiDAR with clean water (if there is still residue on the surface, it can be cleaned again with 99% ethanol), and dry it with a dry, dust-free cloth.

## Page 34

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

EM4 User Manual 33

After sales

If the fault diagnosis section 5 fails to solve the problem, please contact RoboSense in a timely manner. Official website: [https://www.robosense.cn/contact](https://www.robosense.cn/contact)

Prompt explanation

1. Please send back the produc t after receiving confirmation from RoboSense after -sales service; 2) The product can only be sent back in its original packaging or equivalent soft cushioned moisture-proof packaging.

## Page 35

EM4 User Manual 34 ROS\&ROS2 Package Rslidar\_sdk is a driver SDK for the ROS platform. Please contact RoboSense for assistance if needed.

## Page 36

EM4 User Manual 35

Definition of TE connector pins

Definition of TE connector pins

Pin Number Definition Connector model

1 VBat

TE 2387351-1

2 Wakeup

3 /

4 GND

5 CANFD\_H

6 CANFD\_L

D1 1000BASE-T1 N D2 1000BASE-T1 P

## Page 37

## Source Notes

* Review date: 2026-06-04.
* Local source file: `RS-EM4_UserGuide_v1.1_EN.pdf`.
* Product link: [https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar](https://openelab.io/products/robosense-em4-thousand-beam-long-range-digital-lidar)
* Content basis: local PDF text extraction with page markers preserved.
* Omitted content: manufacturer contact emails, phone numbers, addresses, working hours, and support contact blocks.
