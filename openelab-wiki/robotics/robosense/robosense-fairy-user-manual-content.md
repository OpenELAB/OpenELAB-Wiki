# RoboSense Fairy User Manual Content

Product link: [https://openelab.io/products/robosense-fairy-mid-range-lidar](https://openelab.io/products/robosense-fairy-mid-range-lidar)

![RoboSense Fairy User Manual Content product image](<../../.gitbook/assets/robosense fairy product (1).jpg>)RoboSense Fairy User Manual Content product image

This page is a local-file-based OpenELAB wiki copy of `Fairy_EN_48TX_V1.0.pdf`. The content below follows the extracted PDF page order as closely as possible. Contact/support blocks, emails, phone numbers, addresses, and working hours were omitted from the wiki copy.

Source note: RS-LiDAR-Fairy User Guide, manual version 1.0, revision dated 2026-02-01.

## Manual Content

## Page 1

RS-LiDAR-Fairy User Guide 0 Version 1.0

## Page 2

Fairy User Guide

1

Change Description

Version Revision Date Description

1.0 2026/02/01 Initial release

## Page 3

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

Fairy User Guide

2

Reading Prompt

Warning: The usage process should be strictly followed, otherwise it may lead to potential dangerous situations such as minor injuries or property damage. Important: The usage process should be observed, otherwise it may cause potential harmful situations such as product damage. Note: The usage process should be valued sufficiently to achieve maximum value of the product efficiently and smoothly. Please click the following link to download the latest product manual, RSview and other resources: [https://www.robosense.ai/en/resources](https://www.robosense.ai/en/resources) Manufacturer: Suteng Innovation Technology Co., Ltd. (RoboSense). Website: [https://www.robosense.ai/en](https://www.robosense.ai/en) District, 1213 Liuxian Avenue, Taoyuan Street, Nanshan District, Shenzhen,

China

Symbolic Instructions

Resource Download

More Information

## Page 4

Fairy User Guide

3

Contents

Change Description ....................................................................................................... 1 Reading Prompt ............................................................................................................. 2 Contents ......................................................................................................................... 3 1 Safety Notices .........................................................................................................6 1.1 Legal Statement ................................................................................................ 6 1.2 User Guidelines ................................................................................................ 6 1.3 Illegal Operation ............................................................................................... 6 1.4 Requirements for Operating Personnel .............................................................7 1.5 Work Safety and Special Hazards .....................................................................7 2 Product Description ................................................................................................ 9 2.1 Product Overview ............................................................................................. 9 2.2 Product Structure .............................................................................................. 9 2.3 FOV Distribution ............................................................................................ 10 2.4 Specifications ..................................................................................................11 2.5 Product Principle ............................................................................................ 12 2.5.1 Coordinate Mapping ............................................................................. 12 2.5.2 Reflectivity Interpretation .....................................................................12 2.5.3 Return Modes ........................................................................................12 2.5.4 Phase Locking .......................................................................................13 2.5.5 Time Synchronization Method ............................................................. 14 3 Product Installation ...............................................................................................18 3.1 Accessory Description .................................................................................... 18 3.2 Mechanical Installation ...................................................................................18 3.3 Interface Description ...................................................................................... 20 3.3.1 Aviation Plug Interface and Definitions ............................................... 21 3.3.2 Interface Cable (Optional) .................................................................... 22 3.3.3 Power Interface .....................................................................................22 3.3.4 RJ45 Ethernet Interface ........................................................................ 23 The Fairy network interface complies with the EIA / TIA-568B standard. .. 23 3.3.5 Synchronization Interface .....................................................................23 3.4 Quick Connection ........................................................................................... 23 4 Product Usage .......................................................................................................26 4.1 Product Coordinate System ............................................................................ 26 4.2 Web UI Usage .................................................................................................26

## Page 5

Fairy User Guide

4 4.2.1 Web UI Functions ................................................................................. 26 4.2.2 Accessing the Web UI Interface ............................................................26 4.2.3 Using the Web UI Interface .................................................................. 27 4.3 RSView Usage ................................................................................................ 27 4.3.1 Software Functions ............................................................................... 27 4.3.2 Installing RSView .................................................................................28 4.4 Communication Protocols .............................................................................. 28 4.4.1 MSOP and DIFOP Data Protocol ......................................................... 28

4.4.2 Main Data Stream Output Protocol (MSOP) ........................................29

4.4.3 Device Info Output Protocol (DIFOP) ................................................. 32 4.4.4 IMU Data Stream Output Protocol ....................................................... 35 5 Product Maintenance ............................................................................................ 37 5.1 Transportation and Logistics ...........................................................................37 5.2 Storage ............................................................................................................ 37 5.3 Product Cleaning ............................................................................................ 37 5.3.1 Precautions ............................................................................................38 5.3.2 Required Materials ................................................................................38 5.3.3 Cleaning Method .................................................................................. 38 6 Fault Diagnosis ..................................................................................................... 40 7 After-sales Service ................................................................................................42 Appendix A Web UI Operation ............................................................................43 A.1 Product Information .......................................................................................43 A.2 Product Parameter Setting ............................................................................. 43 A.2.1 General Setting ................................................................................ 44 A.2.2 Performance Setting .........................................................................46 A.2.3 Angle Pulse Setting ..........................................................................47 A.3 Product Diagnostics/Operational Status ........................................................ 48 A.4 Product Firmware Upgrade ............................................................................49 Appendix B R0S\&ROS2 Package ....................................................................... 51 Appendix C DIFOP Data Definitions .................................................................. 52 C.1 Ethernet（ETH） .......................................................................................... 52 C.2 Mainboard Firmware Version (TOP\_FRM) ...................................................52 C.3 Baseboard Firmware Version (BOT\_FRM) ................................................... 52 C.4 APP Firmware Version (SOF\_FRM) ............................................................. 53 C.5 Motor Firmware Version (MOT\_FRM) .........................................................53 C.6 Product Serial Number（SN） ......................................................................53 C.7 Time Sync Mode Setting（TIME\_SYNC\_INFO） ...................................... 54

## Page 6

Fairy User Guide

5 C.8 Time（UTC\_TIME） ....................................................................................54 C.9 Real-time Motor Speed（REALTIME\_ROTATION\_SPEED） .................. 54 C.10 Vertical Angle calibration（COR\_VERT\_ANG） ..................................... 54 C.11 Horizontal Angle Calibration（COR\_HOR\_ANG） ..................................55 C.12 Mainboard Input Voltage（MAINBOARD\_VOLTAGE） .........................56 C.13 Device Input Voltage (MACHINE\_VOLTAGE) ......................................... 57 C.14 Baseboard 12V Voltage (BOTTOMBOARD\_VOLTAGE（12V）) .......... 57 C.15 IMU Calibration Data（IMU\_CALIB\_DATA） ........................................ 57 Appendix D Structural Drawings ......................................................................... 59 Appendix E Per-channel transmission delay table ...............................................61

## Page 7

Fairy User Guide

6

1 Safety Notices

1.1 Legal Statement

Unless otherwise stated, all rights (including copyrights, trademarks, patents, trade secrets, and other related rights) in RoboSense's products, technologies, software, programs, data, and other information (including text, icons, photographs, audio, video, graphics, color combinations, layout design, etc.) are owned by RoboSense and its licensors.

No one may use any content contained in this manual in any unauthorized manner

without the prior written consent of RoboSense. The word "RoboSense" and other logos and product and service names are owned by RoboSense. If you need to use them for any advertising or displaying purposes, you must obtain prior written authorization from RoboSense.

1.2 User Guidelines

Please use this product in accordance with the following requirements: 1) Please strictly abide by relevant national laser safety laws and regulations; 2) Please read this product manual in detail before using the product; 3) Please use this product only in the relevant field of application; 4) Please avoid using this product in environments that are explosive, highly corrosive, or beyond the IP protection level of the equipment.

1.3 Illegal Operation

Please use this product in accordance with the regulations, otherwise it may cause product damage, property loss, and personal injury. Users are responsible for risk arising from unauthorized operations. 1) Do not disassemble or modify this product (including accompanying accessories);

## Page 8

Fairy User Guide

7 2) Non-specified power supply and accompanying accessories are prohibited; 3) Please avoid abnormal operations such as dropping, colliding, burning, etc.; 4) If you notice any damage to the appearance of the device (arc protection cover), please immediately stop using it; 5) If you notice any abnormal operation of the product, please immediately stop using it and contact RoboSense in a timely manner.

1.4 Requirements for Operating Personnel

The use of this product requires certain basic professional knowledge and other

related requirements for operating personnel. Unreasonable operations performed by personnel without basic knowledge or training do not constitute a fault of RoboSense and may cause damage to equipment and personal property. 1) Please read the product manual in detail before using the device; 2) Prohibit illegal operations; 3) Before working, personnel must undergo training and obtain relevant construction qualifications; 4) Have some basic knowledge of computer data connection, electrical, and so on.

1.5 Work Safety and Special Hazards

To avoid risks of accidents, damage to sensor or violating of your product warranty, please read and follow the instructions in this manual carefully before operating the product. 1) Laser Safety: This product meets the following standards for laser products: IEC 60825-1:2014; 2) High Temperature Warning: Please pay attention to the overheating sign on the LiDAR surface to avoid a hot LiDAR surface that may lead to sensor

## Page 9

Fairy User Guide

8 failure or undesirable consequences; 3) Retain Instructions: The safety and operating instructions should be retained for future reference; 4) Heed Warnings: All warnings on the product and in the operating instructions should be adhered to; 5) Servicing: Except for what’s described in this manual, the sensor has no field serviceable parts. For servicing, please contact RoboSense sales or the authorized distributors.

## Page 10

Fairy User Guide

9

2 Product Description

2.1 Product Overview

Fairy is a high-precision, high-definition, medium-to-long-range digital LiDAR designed by RoboSense. It is primarily used in applications such as robot environment perception, autonomous vehicle environment perception, drone mapping, and smart cities. Fairy adopts RoboSense innovative chip-based transceiver design and a fully digital architecture, achieving an industry-leading accuracy of 0.5 cm. With a wide 360° × 32° field of view (FOV) and a maximum detection range of 150 meters, it delivers exceptional performance for advanced sensing applications.

2.2 Product Structure

The structure diagram of Fairy is shown in Figure 1 .

Figure 1 Product Structure Description

## Page 11

Fairy User Guide

10 It mainly includes the following components: 1) Protective Cover

Both the emitted laser and returned laser need to pass through the specially

designed arc-shaped protective cover. Therefore, any obstruction within the laser's field of view (FOV) is strictly prohibited. 2) Aviation Connector The LiDAR body is connected to the interface cable via an aviation connector, enabling power supply and data transmission functionalities. 3) M4 Screw Mounting Holes Used to secure the LiDAR to the mounting bracket, it is fastened with M4 screws. For detailed dimensions, refer to the structural drawings in Appendix D. 4) Mounting Holes

Used to support and fix the position and orientation between the LiDAR and the

bracket, and to enhance installation efficiency and accuracy. For detailed dimensions, refer to the structural drawings in Appendix D.

2.3 FOV Distribution

Fairy's FOV has a horizontal angular range of 0 to 360 degrees and a vertical angular range of -15.84° \~ +15.84° degrees, with the vertical angular resolution of approximately 0.67° degrees. The 48 lasers are defined as 48 channels, and their corresponding relationship with the real vertical angles is shown in Figure 2 .

Figure 2 Fairy FOV Illustration

## Page 12

Fairy User Guide

11 Fairy's design architecture and scanning sequence result in approximately 6ms of point cloud unavailability per second, meaning one out of every 10 frames of point cloud data has a gap of about 30°. The starting angle of this gap can be configured in firmware, allowing users to set it to a position with minimal impact based on actual needs. Refer to Appendix A.2.2 for detailed specifications.

2.4 Specifications1

Table 1 Fairy Specifications

Specifications

Number of Channels 48 Horizontal Field of View (FOV) 0\~360° Laser Safety Level Class1 Eye-Safey Vertical Field of View (FOV) -15.84° \~ +15.84° Measurement Range2 150m (80m @10% NIST)

Horizontal Angular

Resolution 0.25° Blind Zone ≤0.2m Vertical Angular Resolution 0.67° Rotation Speed 600 rpm Precision (Typical)3 0.5 cm (1 σ)

Number of Output Points

\~690,000 pts/s (Single Return Mode), \~1,380,000 pts/s (Dual Return Mode) Frame Rate 10 Hz

Ethernet Transmission

Bandwidth ＜19Mbps

Output Data Protocol UDP Packets Over Ethernet

Lidar Data Packet

Content Spatial coordinates, Reflectivity, Timestamp, etc. Operating Voltage 9 V - 32 V Product Life4 17520 h

Product Power

Consumption5 <10 W Dimensions Diameter 75 mm × Height 70 mm Weight <350g (LiDAR Body) Operating Temperature6 - 40℃ \~ + 60℃ Time Synchronization GPS & gPTP & PTP Storage Temperature - 40℃ \~ + 85℃ Product Model Fairy Protection Level IP67 / IP6K9K 1 The following data applies only to mass-produced products. Any samples, prototypes, or other non-mass-produced versions may not be applicable to these specification data. If you have any questions, please contact Robosense; 2 The ranging capability is based on a 10% NIST diffuse reflectance target; test results may be affected by environmental factors, including but not limited to ambient temperature and light intensity; 3 Measurement Precision is based on a 50% NIST diffuse reflection target, and the test results are affected by environmental factors, including ambient temperature and target distance. The accuracy value applies to most channels, but variations may exist between certain channels； 4 The specified Product life refers to operation under room temperature conditions (25 ℃), running 16 hours per day, 365 days per year, for three years; 5 Device Power Consumption test results are influenced by external environmental factors, including ambient temperature, target distance, and target reflectivity. 6 Device Operating Temperature may be affected by external environmental factors, including lighting conditions and airflow variations.

## Page 13

Fairy User Guide

12

2.5 Product Principle

2.5.1 Coordinate Mapping

As the LiDAR data packet contains only horizontal rotation angles and distance

parameters, to present a three-dimensional point cloud, the polar coordinates (angle and distance) are transformed into Cartesian coordinates (x, y, z) according to the following equations: ?= ????( ?) ???( ?) + R ???( ?); ? = ????( ?) ???( ?) + R ???( ?); ?= ????( ?) + Z; where r is the measured distance, ω is the laser's vertical angle, α is the laser's horizontal rotation angle, R is the plane radius from the optical center to the origin, Z is the height from the optical center to the origin, and x, y, z are the coordinates projected onto the Cartesian X, Y, Z axes.

2.5.2 Reflectivity Interpretation

Fairy LiDAR provides reflectivity information to characterize the reflectance of

measured objects. In Fairy data, the calibrated reflectivity range is from 1 to 255. (This range represents the RoboSense's proprietary reflectivity measurement scale.)

2.5.3 Return Modes

2.5.3.1 Return Modes Principle

Fairy supports multiple return modes, including Strongest Return, Last Return, First Return, and Dual Return modes. In the Dual Return mode, detailed information of the target object is displayed, and the data volume is twice that of the Single Return mode. Fairy analyzes multiple return values received and outputs the strongest, last, first return or dual return value based on user selection, or outputs dual return values. In the Strongest Return mode, only the strongest reflected return value is output; in the Last Return mode, only the last detected return in the time domain is output.

## Page 14

Fairy User Guide

13

Figure 3 Dual Return Detection

Note: In Dual Return mode, when the laser hits multiple targets, and the distance between the targets is longer than 1 meter, the LiDAR can detect two returns, as shown in Figure 3 .

2.5.3.2 Return Mode Flags

The default setting for Fairy at the factory is Strongest Return mode. Users need to change this setting, they can configure it in the product echo mode parameters on the Web interface. In DIFOP, the 300th byte is the flag bit for the return mode. For details, refer to Table 2.

Table 2 Return Mode and Flag Bit Reference Table

DIFOP Offset Flag Return Mode

300 0x00 Strongest Return 0x01 First Return 0x02 Last Return 0x03 Dual Return

2.5.4 Phase Locking

Fairy's phase locking function allows the device to emit lasers at specific angles when the sensor reaches a whole second.

Figure 4 illustrates Fairy's setup with different phase angles. The red arrows

indicate that at the whole second, the sensor rotates to 0°, 135°, and 270° to emit lasers. Refer to Figure 12 for the coordinate system details.

## Page 15

Fairy User Guide

14

Figure 4 Fairy Phase Lock Setting Illustration

The "Phase Lock" parameter setting is available in the Web interface under Setting > Phase Lock Setting. It allows users to set the locked phase angle, which should be an integer ranging from 0 to 360 For more details, refer to Web UI of Appendix A.

2.5.5 Time Synchronization Method

Fairy supports three time synchronization methods: GPS, PTP (IEEE 1588 V2 protocol), and gPTP (IEEE 802.1 AS protocol). Users can configure these settings through the Web interface. For more details, refer to Web UI of Appendix A.

2.5.5.1 GPS Time Synchronization Principle

The GPS module continuously sends GPRMC data and PPS synchronization

pulse signals to the product. The PPS synchronization pulse length should be between

20 to 200 ms, with GPRMC data transmission required to start after 10 ms from the

falling edge of the PPS pulse and complete between 300 to 500 ms before the rising edge of the next PPS pulse. The timing diagram is shown in Figure 5 .

Figure 5 GPS Time Synchronization Timing Diagram

## Page 16

Fairy User Guide

15 Note: To ensure timing synchronization accuracy, it is recommended to set the PPS pulse width between 20-200 ms. GPRMC completion time should be between 10 ms after the PPS falling edge and 300-500 ms before the next PPS rising.

2.5.5.2 GPS Time Synchronization Usage

The GPS interface of Fairy LiDAR adopts the RS232 electrical level protocol. Refer to Table 3 for the pin definition.

Table 3 Product Time Synchronization Pin Definitions

Communication

Receiving Pin Definition

GPS\_GPRMC GPS\_PPS RS232 Receives serial data with RS232 electrical level standard output from the GPS module

Receives positive synchronization pulse

signal output from the GPS module, with a voltage requirement of 3.0 \~ 15.0 V The external GPS module needs to set the output serial port baud rate to 9600 bps,

8 data bits, no parity bit, and 1 stop bit. Fairy only reads GPRMC-formatted data sent

by the GPS module. The standard format is as follows: $ GPRMC,<1>,<2>,<3>,<4>,<5>,<6>,<7>,<8>,<9>,<10>,<11>,<12> \* hh <1> UTC time <2> Positioning status: A = valid positioning, V = invalid positioning <3> Latitude <4> Latitude hemisphere N (Northern Hemisphere) or S (Southern Hemisphere) <5> Longitude <6> Longitude hemisphere E (Eastern Longitude) or W (Western Longitude) <7> Ground speed <8> Ground course <9> UTC date <10> Magnetic declination <11> Magnetic declination direction: E (East) or W (West) <12> Mode indication (A = Autonomous positioning, D = Differential, E = Estimated, N = Data invalid) \*hh at the end represents the XOR sum of characters from $ to \*

## Page 17

Fairy User Guide

16 Note: 1) The GPS interface on Fairy's aviation cable utilizes an SM2.54 terminal connector, with the pin configuration detailed in Figure 8; 2) The interval for sending 1 PPS pulse should be controlled within 1s ± 200 us; 3) GPRMC message's status field must be 'A' (Valid) for time synchronization to be permitted. 4) Fairy is compatible with most GPRMC message formats from GPS modules available in the market. If any compatibility issues are found during use, please contact RoboSense.

2.5.5.3 PTP Synchronization Principle

PTP (Precision Time Protocol, IEEE 1588V2 protocol) is a time synchronization protocol used for high-precision time synchronization between devices. It can also be used for frequency synchronization between devices. Compared to various existing time synchronization mechanisms, PTP offers the following advantages: 1) Compared to NTP (Network Time Protocol), PTP can meet higher precision time synchronization requirements. NTP generally achieves sub-millisecond level time synchronization accuracy, while PTP can reach sub-microsecond level accuracy; 2) Compared to GPS (Global Positioning System), PTP has lower construction and maintenance costs.

2.5.5.4 gPTP Synchronization Principle

gPTP (general Precise Time Protocol, IEEE 802.1AS protocol) is a derivative protocol of PTP in Time-Sensitive Networking (TSN). The synchronization mechanism uses the same P2P peer delay mechanism as the PTP protocol and adopts Ethernet L2 layer communication. Unlike PTP, gPTP requires the use of hardware-based timestamps, i.e., hardware timestamps, so the requirements for switches and master clocks are more stringent, complying with the IEEE 802.1AS protocol.

2.5.5.5 PTP/gPTP Wiring Method

To use PTP/gPTP synchronization, the following preparations are required. Refer to section 3.4 of the product manual for connection details:

## Page 18

Fairy User Guide

17 1) Select PTP/gPTP mode in the Web interface. See Appendix A of the product manual for details; 2) PTP Master/gPTP Master time source (plug and play, no additional configuration required); 3) Ethernet switch; 4) Devices that support PTP/gPTP protocols and need time synchronization. Note: 1) The PTP Master device is a third-party device and is not included in the RoboSense shipment. The user needs to purchase it separately; 2) RoboSense products, as Slave devices, only receive time from the Master and do not judge the accuracy of the Master's clock source. If there are sudden changes in the time when parsing LiDAR point cloud data, please check if the time provided by the Master is accurate; 3) After LiDAR synchronization, when the Master is disconnected, the time in the point cloud data packet will be accumulated based on the LiDAR's internal clock. The time will be reset when the LiDAR is powered off and restarted.

## Page 19

Fairy User Guide

18

3 Product Installation

3.1 Accessory Description

The standard accessories included with Fairy are listed in Table 4 for reference.

Table 4 Standard Accessory List

No. Accessory Name Specification Quantity

1 LiDAR Fairy 1

2 Screw Pack M4\*6 3

3 Screw Pack (Optional) M4\*10 3

4 Aviation Connector Cable (Optional) 1.5m 1

5 Power Adapter (Optional) DC12 V × 3.34 A / 40 W 1

6 Power Cable (Optional) 1.2 m 1

7 Ethernet Cable (Optional) 1.5 m 1

8 Product Packing List and Shipment Inspection

Report / 1 Note: For specific requirements, refer to the commercial agreement.

3.2 Mechanical Installation

The structural installation diagram of the LiDAR is shown in Figure 6 .

Figure 6 LiDAR Structure Installation Diagram

1. Screw Specifications: a) GB / T70.1, M4 × 6, hexagon socket head cap screw, strength grade A2-70. 2) Mounting and Positioning Method:

## Page 20

Fairy User Guide

19 a) The bracket and LiDAR positioning are as shown in the diagram; it is recommended to use the LiDAR's bottom locating posts for positioning; b) The bottom bracket should feature small raised pads near the 3 mounting holes to mate with the LiDAR, with an overall flatness requirement of ≤0.15 m; c) Use 3 M4 screws to install on the base, 3.5\~4.5 mm out of the installation surface. Recommended tightening torque is 15 ±1 kgf.cm; d) Use 2 Φ 3 positioning pins on the base for installation alignment, not exceeding a height of 3 mm; e) When installing the LiDAR, if both the top and bottom of the LiDAR have contact surfaces, ensure the distance between the surfaces is greater than the height of the LiDAR to avoid compressing it; f) Since the LiDAR requires wiring for external communication, insufficient wiring space or too small a bend radius may affect cable lifespan and signal quality. Wiring installation requirements are as follows: i. When routing the LiDAR cables, avoid excessive tension and ensure sufficient slack; ii. Cable diameter: 6 ±0.2 mm; minimum bend radius: 5×cable diameter.

Figure 7 Illustration of the Positioning Pins and Screws on the Bottom of the LiDAR

1. Bracket Stiffness and Strength Requirements:

The fixed bracket needs to have good rigidity for securely mounting the LiDAR

and maintaining the LiDAR in a stable state under various conditions. Design requirements include:

## Page 21

Fairy User Guide

20 a) It is recommended that the LiDAR mounting bracket maintain a certain rigidity, with specific thresholds determined by the customer's perception algorithm; b) The bracket will endure significant loads under random vibration and mechanical shock conditions. Strength must be verified based on actual operating conditions: Mechanical shock condition: Maximum stress < 2/3 of tensile strength. Random vibration condition: 1σ RMS stress < 1/5 of tensile strength. 4) Bracket Heat Dissipation Requirements: Fairy will experience temperature rise during operation, which may be exacerbated by external heat sources, ambient temperature, and solar radiation.

RoboSense can provide thermal simulation evaluation and optimization

recommendations based on specific design schemes. General thermal management guidelines include: a) The ambient temperature around the LiDAR must be maintained within the operating range (-40°C to +60°C); b) The bracket material is recommended to be made of aluminum alloy or galvanized steel plate with a thermal conductivity greater than 50 W/m·K. Some heat dissipation fins should be added to the bracket, with reasonable spacing, height, and direction of the fins to increase the heat dissipation area.

The direction should align with the air convection direction for more

effective heat dissipation; c) Ensure that the LiDAR base or top cover is not covered with non-metallic materials to avoid affecting the overall heat dissipation, leading to excessive temperature rise of the LiDAR; d) If necessary, add thermal interface materials between the LiDAR and bracket to enhance heat transfer efficiency.

3.3 Interface Description

## Page 22

Fairy User Guide

21

3.3.1 Aviation Plug Interface and Definitions

The cable aviation plug on the Fairy LiDAR side is shown in Figure 8 .

Figure 8 Aviation Plug Interface Pin Numbers

The specific pin definitions of the aviation plug interface on the LiDAR side are

shown in Table 5.

Table 5 Aviation Plug Interface Pin Definitions

Pin No. Spec Signal

1 26AWG 2P(RX+)

2 26AWG 2N(RX-)

3 26AWG 1P(TX+)

4 26AWG 1N(TX-)

5 26AWG GND

6 26AWG VIN

7 26AWG VIN

8 26AWG GND

9 30AWG GPS\_PPS

10 30AWG SYNC\_OUT1

11 30AWG GPS\_GPRMC

## Page 23

Fairy User Guide

22

3.3.2 Interface Cable (Optional)

The optional accessory cable for Fairy is a one-to-three wire harness. Among them: Terminal B serves as the power supply connector. Terminal C serves as the network connector, outputting 100Base-TX Ethernet. Terminal D also functions as a GPS time synchronization connector. The details of the connection cable are shown in the Figure 9 below:

Figure 9 Interface Cable

For detailed specifications of the interfaces on the Interface Cable, refer to Table 6 .

Table 6 Interface Cable specifications

A End No. Wire Spec Wire Definition A End Color B End No. C End No. D End No. D End

Color

1 26AWG 2P(RX+) Orange-white \ 1 \ \\

2 26AWG 2N(RX-) Orange \ 2 \ \\

3 26AWG 1P(TX+) Green-white \ 3 \ \\

4 26AWG 1N(TX-) Green 6 \ \\

5 26AWG GND Black 2 \ \ \\

6 26AWG VIN Red 1 \ \ \\

7 26AWG VIN Red 1 \ \ \\

8 26AWG GND Black 2 \ 4 Black

9 30AWG GPS\_PPS Purple \ \ 3 Purple

10 30AWG SYNC\_OUT1 Blue \ \ 2 Blue

11 30AWG GPS\_GPRMC Yellow \ \ 1 Yellow

Table 6 Interface Cable Interface Specifications

3.3.3 Power Interface

The Fairy power interface uses a standard DC 5.5–2.1 connector. If the LiDAR motor does not rotate after connecting power, the cable harness may be damaged. Please contact RoboSense.

## Page 24

Fairy User Guide

23 Important Note: 1) Grounding method: The LiDAR uses a shared ground design between the enclosure and the internal circuit board. 2) Installation environment recommendation: If the equipment enclosure in the installation environment is floating (ungrounded), it is recommended to electrically isolate the LiDAR enclosure from the equipment enclosure using non-metallic insulating components or other methods to ensure proper operation and prevent potential interference.

3.3.4 RJ45 Ethernet Interface

The Fairy network interface complies with the EIA / TIA-568B standard.

3.3.5 Synchronization Interface

Fairy synchronization interface definition: GPS REC is the GPS GPRMC input; GPS PULSE is the GPS PPS input. Important Note: 1) When connecting Fairy ground to an external system, the negative terminal (“ground”) of the external power supply and the GPS system ground must share a non-isolated common ground.

3.4 Quick Connection

The Fairy network parameters can be configured, and the default factory setting uses fixed IP and port number mode, as shown in Table 7.

Table 7 Default Factory Network Configuration Table

Device IP Address MSOP Package Port Number DIFOP Package Port Number

Fairy 192.168.1.200 6699 7788Computer 192.168.1.102 When using the product, the user needs to set the computer's IP address to be in the same subnet as the product, for example, 192.168.1.x (where x can be any value between 1 and 254), and the subnet mask is 255.255.255.0. For unknown product network configuration information, please connect the product and use Wireshark to

## Page 25

Fairy User Guide

24 capture the output package of the product for analysis. The IP configuration and connection methods are as follows: 1) Connecting the LiDAR The connection method is shown in Figure 10 . a) Connect the LiDAR's aviation plug to the cable assembly (1-to-3 wire harness); b) PC connects to the cable assembly via RJ45 Ethernet port. c) The LiDAR operates normally after power-on.

Figure 10 LiDAR Connection

1. Through the ".pcap" packets captured by Wireshark software, get the Local IP of Computer by analyzing " arp" packets a) Perform the following steps after the LiDAR and PC are connected:Start Wireshark (a third-party network analysis tool) and select the correct network interface to begin capturing packet; b) Use the search box in Wireshark and enter "arp" to search for the mutual addressing packets between the LiDAR and PC, as shown in Figure 11 ;

## Page 26

Fairy User Guide

25

Figure 11 Analyzing ARP Packets

c) In Figure 11 , the "SutengIn" in the Source column indicates the source information of the LiDAR, indicating that the Source IP is 192.168.1.200, which is the LiDAR's IP. The request is accessing 192.168.1.102, which is the PC's IP. If the local IP is not the requested access IP, then configure the PC's local IP as 192.168.1.102 as shown in step 3. If the access is successful, proceed to step 4. 3) Configuring the PC's Local IP a) In the Control Panel, go to "Network and Internet" and then "Network and Sharing Center." In the "View your active networks" section, click on the corresponding Ethernet connection to enter the corresponding "Ethernet Status," and then click on "Properties"; b) Double-click "Internet Protocol Version 4 (TCP/IPv4)" to enter the IP information settings and use a static IP for configuration; c) Set the local IP address to 192.168.1.102, subnet mask to 255.255.255.0, and click "OK" to complete the PC's static IP setting. 4) Connection Completed. Note: 2) The time synchronization module (PTP & gPTP, GPS time synchronization module) is not included as a standard product. If you need to use these features, please purchase them separately and follow the connection method shown in Figure 10; 3) The configuration of the local static IP provided above is only an example for Windows operating systems. For other operating systems, please refer to the actual instructions.

## Page 27

Fairy User Guide

26

4 Product Usage

4.1 Product Coordinate System

The coordinates and rotation direction of the product are shown in Figure 12 .

Figure 12 LiDAR Coordinate and Rotation Direction Illustration

Note:

The origin of the coordinates for the LiDAR is defined at the center of the LiDAR

base.

4.2 Web UI Usage

4.2.1 Web UI Functions

Fairy supports parameter settings, viewing of operational information/status, and firmware upgrades through the Web UI interface. The Fairy web address changes according to the Device IP. The default Device IP is 192.168.1.200. If you have changed the Device IP, the web address will be the newly set IP.

4.2.2 Accessing the Web UI Interface

Once the product is connected and correctly configured as required, use a

## Page 28

Fairy User Guide

27 computer browser to access the product's IP address (default Device IP: 192.168.1.200) to enter the Fairy web homepage. The default page is the "Device" tab.

4.2.3 Using the Web UI Interface

For detailed instructions on using the Web UI interface, please refer to Web UI of Appendix A.

4.3 RSView Usage

For data visualization with Fairy, you can use free tools such as Wireshark and tcp-dump to obtain raw data. RSView can provide a more convenient way to visualize the raw data.

4.3.1 Software Functions

RSView enables real-time visualization of Fairy's data. It can also replay data saved in ".pcap" file format, but does not support ".pcapng" files at the moment. In RSView, the distance measurement values obtained by Fairy are displayed as points. It supports various custom colors to display data, such as reflection intensity, time, distance, horizontal angle, and laser beam index. The displayed data can be exported and saved in ".csv" format, and RSView version 3.1.3 and later versions support exporting data in ".las" format. RSView includes the following features: 1) Real-time display of data via Ethernet; 2) Save real-time data as PCAP files; 3) Replay data from recorded PCAP files; 4) Various visualization modes, such as distance, time, horizontal angle, etc; 5) Display point data in tabular format; 6) Export point cloud data as CSV files; 7) Distance measurement tool;

## Page 29

Fairy User Guide

28 8) Display multiple frames of replayed data simultaneously; 9) Show or hide individual laser beams from Fairy; 10) Cropping display.

4.3.2 Installing RSView

RSView can be run on Windows 64-bit and Ubuntu 18.04 or higher operating systems. You can download the latest version of RSView software compressed package from the Robosense official website ( [https://www.robosense.ai/en](https://www.robosense.ai/en) ). After downloading, make sure the extraction path does not contain Chinese characters. The software does not require installation; simply run the executable file after extraction to use it.

4.4 Communication Protocols

Fairy communicates with a computer via Ethernet using UDP (User Datagram Protocol). The communication protocols between Fairy and the computer fall into two categories, as described in Table 8.

Table 8 Protocol Overview

Protocol Name Abbreviation Function Type Packet Size Send Interval

Main data Stream

Output Protocol MSOP Point cloud data UDP 1248 bytes Approx. 555.55 us

Device Information

Output Protocol DIFOP LiDAR

information output UDP 1248 bytes Approx. 1 s Note: 1) Section 4.4 of the product manual describes and defines the payload (1248 bytes) of the protocols; 2) The Main Data Stream Output Protocol (MSOP) encapsulates the laser scanning data, including distance, angle, and reflection intensity, into packets for output; 3) The Device Information Output Protocol (DIFOP) outputs various configuration information about the current state of Fairy.

4.4.1 MSOP and DIFOP Data Protocol

## Page 30

Fairy User Guide

29

Figure 13 LiDAR Data Structure Diagram

4.4.2 Main Data Stream Output Protocol (MSOP)

Main Data Stream Output Protocol: Main data Stream Output Protocol, abbreviated as MSOP. I/O Type: Product output, computer parsing. The default factory port number is 6699.

4.4.2.1 Header

The frame header (Header) is 42 bytes in total and is used to identify the start position of the data. For details on the data structure, refer to Table 9.

Table 9 MSOP Header Data Table

Information Offset

Length

（byte）

Description

Total Length

(byte) pkt\_head 0 4 0x55AA055A 42 REV0 4 8 / pktcnt 12 4 Packet transmission cycle count: 0-65535 REV 16 4 / timestamp 20 10 Timestamp, first 6 bytes indicate seconds, last 4 bytes indicate microseconds REV 30 1 / lidar\_type 31 1 0x0A：Fairy lidar\_model 32 1 0x02:48 beams

## Page 31

Fairy User Guide

30

Information Offset

Length

（byte）

Description

Total Length

(byte) REV 33 9 / Note:

The defined timestamp is used to record the system time with a resolution of

1 μs.

4.4.2.2 Data Block

As shown in Table 10, Data block is the part of sensor measurement value in MSOP package, with a total of 1184 bytes. It consists of eight Data Blocks, each of which is 148 bytes long. Data block in the space of 148 bytes includes: a sign of 2 bytes, indicated by 0xffee; Azimuth of 2 bytes, indicating the horizontal rotation Angle information, each Angle information corresponds to 48 channel data.

Table 10 Data Block Definition

Information Offset

Length

（byte）

Description

Total

Length(byte) Data\_ide 0 2 0xffee 148 Azimuth 2 2 In polar coordinates: Horizontal angle, resolution 0.01. Data 1

4 2 Distance Measurement (Take the lower

15 bits, with the highest bit reserved)

6 1 Reflectivity

Data 2 7 3 Same as Data 1 Data 3 10 3 Same as Data 1 ... ... ... ... Data 47 142 3 Same as Data 1 Data 48 145 3 Same as Data 1 1) Channel Data Definition Channel data is 3 bytes, with the high two bytes used to represent distance information and the low one byte used to represent reflectivity information, as shown in Table 11 .

## Page 32

Fairy User Guide

31

Table 11 Channel Data

Channel Data（3 bytes）

2 bytes Distance 1 byte Reflectivity

Distance Measurement (Take the lower 15 bits, with the highest bit reserved) Reflectance Intensity Data Note: Distance is 2 bytes，resolution is 0.5 cm.

Figure 14 MSOP Packet Illustration

Red Box: Header ID; Green Box: LiDAR Type and LiDAR Model; Blue Box: Data Block Flag; Black Box: Azimuth Value for Channel data 1; Yellow Box: Distance Value for Channel data 1; Orange Box: Reflectivity Value for Channel data 1. Distance Value Calculation in Data Packet: a) The hexadecimal distance values in the data packet: 0x04, 0xEE; b) Combine the data into 16 bits as a 16-bit unsigned integer, represented as: 0x04EE; c) Convert the distance value to a decimal number: 1262; then calculate based on the distance resolution; d) Result: 1262 × 0.5 cm = 631cm = 6.31 m. Angle Value Calculation in Data Packet:

## Page 33

Fairy User Guide

32 a) The hexadecimal angle values in the data packet: 0x79, 0x46; b) Combine the data into 16 bits as a 16-bit unsigned integer, represented as: 0x7946; c) Convert to a decimal number: 31046, then divide the decimal result by 100; d) Result: 31046° / 100 = 310.46°. Reflectivity Value Calculation in Data Packet: a) The hexadecimal reflectivity value in the data packet: 0x04; b) Convert to a decimal number: 4; c) The resulting reflectivity value is 4. 2) Angle Value Definition: In each Block, the angle value output by Fairy is the angle at which the first channel laser range finding occurs. This angle value is derived from the angle encoder, where the zero position of the angle encoder is the zero point of the angle. The resolution for horizontal rotation angle values is 0.01°.

4.4.2.3 Tail

Frame Tail (Tail) consists of two parts: a fixed-length 6-byte Tail and 16-byte reserved.

4.4.3 Device Info Output Protocol (DIFOP)

Device Info Output Protocol, abbreviated as DIFOP, is used for product output and computer reading. I/O Type: Product output, computer read. The default port number is 7788. DIFOP is an "output-only" protocol used to periodically send information such as product serial number (S/N), firmware version, computer driver compatibility information, configuration information, angle information, running status, fault diagnosis, etc., to users. Users can read DIFOP to interpret specific information about the currently used product.

## Page 34

Fairy User Guide

33 A complete DIFOP packet has a data format structure of synchronization header, data area, and tail. Every packet has 1248 bytes totally. The basic structure of the data packet is shown in Table 12.

Table 12 Data Format Structure of DIFOP Packet

Information Offset Length

（byte） Description DIFOP Header 0 8 0xA5 0xFF 0x00 0x5A 0x11 0x11 0x55 0x55 Reserved 8 2 Ethernet Source IP Address 10 4 Appendix C.1

Ethernet Destination IP

Address 14 4 LiDAR MAC Address 18 6 MSOP Port 24 2 Reserved 26 2 DIFOP Port 28 2 Reserved 30 2 FOV start angle 32 2 Range 0-359, precision 0.01° FOV end angle 34 2 Range 0-359, precision 0.01° Reserved 36 2 Phase lock angle 38 2 Range 0-360, precision 1°

Mainboard Firmware

Version 40 5 Appendix C.2

Baseboard Firmware

Version 45 5 Appendix C.3 APP Firmware Version 50 5 Appendix C.4 Motor Firmware Version 55 5 Appendix C.5 Reserved 60 25

PTP Param Config

85 2 PTP domain number

87 1 Responds to peer delay request messages

88 1 No leap second offset

89 1 Timeout for loss of sync messages (s)

90 1 Offset threshold from unlock to lock (ms)

91 1 Offset threshold from lock to unlock (ms)

Reserved 92 196

GPRMC baud rate in GPS

synchronization mode 288 1 Baud value: 0x00:1200 0x01:2400 0x02:4800 0x03:9600（default） 0x04:14400 0x05:19200 0x06:38400 0x07:43000 0x08:57600 0x09:76800 0x0A:115200 0x0B:128000 0x0C:230400 0x0D:256000

## Page 35

Fairy User Guide

34

Information Offset Length

（byte） Description 0x0E:460800 0x0F:921600 0x10:1382400" Reserved 289 3 Product Serial Number 292 6 Appendix C.6 Reserved 298 2 Return Mode 300 1 Time Sync Mode Setting 301 1 Appendix C.7Time Sync Status 302 1 Time 303 10 Appendix C.8

Angle Pulse Config

313 1 Angle pulse mode: 0 = mode2, 1 = mode1

(+25%)

314 1 Angle pulse enable: 0 = off, 1 = on

315 4 Angle pulse width (ns) — value × 10 equals

the configured width in ns

319 2 Angle pulse start angle — value × 0.01 equals

the configured angle

321 2 Angle pulse step size — value × 0.01 equals

the configured angle Reserved 323 5 Performance Config 328 2 Frame start blanking angle offset: 0–360° Reserved 330 27 GPS Status 357 1 bit0 (PPS lock flag): locked = 1, unlocked = 0 bit1 (GPRMC lock flag): locked = 1, unlocked = 0 bit2 (UTC lock flag): locked = 1, unlocked = 0 bit3 (GPRMC input status): input present = 1, no input = 0 bit4 (PPS input status): input present = 1, no input = 0 bit5–bit7: reserved

IMU config info

358 1 IMU enable control: 0 = off, 1 = on

359 2 IMU UDP port number

361 1 IMU message output frequency: 0 = 25 Hz, 1

\= 50 Hz, 2 = 100 Hz, 3 = 200 Hz

362 1

IMU accelerometer range:

0 = ±2 g

1 = ±4 g

2 = ±8 g

3 = ±16 g

363 1

IMU gyroscope range:

0 = ±250 dps

1 = ±500 dps

2 = ±1000 dps

3 = ±2000 dps

Reserved 364 7 Real-time Phase 371 2 Unit: degree Real-time motor speed 373 2 Appendix C.9 Reserved 375 93

## Page 36

Fairy User Guide

35

Information Offset Length

（byte） Description Vertical Angle calibration 468 288 Appendix C.10 Horizontal Angle calibration 756 288 Appendix 11

Mainboard Total Input

Voltage 1044 2 Appendix 12 Reserved 1046 20 Device Input Voltage 1066 2 Appendix C.15 Baseboard 12V Voltage 1068 2 Appendix C.15 Reserved 1070 22 IMU Calibration Data 1092 28 Appendix C.155 Reserved 1120 126 Reserved Frame Tail 1246 2 0x0F 0xF0 Note: 1) The Header (DIFOP Identification Header) consists of the bytes 0xA5, 0xFF, 0x00, 0x5A, 0x11, 0x11, 0x55, 0x55, and can be used as a check sequence for the packet; 2) The Tail contains the bytes 0x0F, 0xF0; 3) The definition and usage of each item's registers can be found in detail in Appendix C of the product manual. The corresponding relationship is specified in the Remarks column of Table 13.

4.4.4 IMU Data Stream Output Protocol

I/O Type: Product output, computer read. The default port number is 6688. The IMU output is the attitude information of IMU in the product, which can be used to adjust the external parameters of the customer’s products. The data format structure of a complete IMU packet is frame header, data area, and frame tail. Each packet contains 51 bytes. The basic structure of the packet is shown in Table 13.

Table 13 IMU Data Format Structure

No. Information Offset Length （byte） Description Remark

1 IMU header 0 4 0xAA 0x55 0x5A 0x05

2 Time 4 10

UTC time format. The first 6 bytes are second timestamps, and the last 4 bytes are microsecond timestamps.

3 AccelX 14 4 X-axis acceleration value, floating-point

number, unit: m/s².

4 AccelY 18 4 Y-axis acceleration value, floating-point

number, unit: m/s².

5 AccelZ 22 4 Z-axis acceleration value, floating-point

number, unit: m/s².

6 GyroX 26 4 X-axis angular velocity value, floating-point

## Page 37

Fairy User Guide

36 No. Information Offset Length （byte） Description Remark number, unit: rad/s

7 GyroY 30 4 Y-axis angular velocity value, floating-point

number, unit: rad/s

8 GyroZ 34 4 Z-axis angular velocity value, floating-point

number, unit: rad/s

9 Internal

Temperature 38 4 IMU internal temperature, signed, resolution

0.01 degrees.

10 ODR 42 1 Data Output Frequency

0:25Hz 1:50Hz 2:100Hz 3:200Hz 4:1000Hz

11 AccelFsr 43 1 Range of the Accelerometer

0: +/- 2g 1: +/- 4g 2: +/- 8g 3: +/- 16g

12 GyroFsr 44 1 Range of the Gyroscope

0: +/- 250 dps 1: +/- 500 dps 2: +/- 1000 dps 3: +/- 2000 dps

13 Package

Counter 45 4 The value is u32, starting with 1.

14 Frame Tail 49 2 0xF0 0x0F

## Page 38

Fairy User Guide

37

5 Product Maintenance

5.1 Transportation and Logistics

Important

Improper transportation can cause product damage! 1) The product should be packaged with shockproof and moisture-proof materials to avoid damage during transportation. It is recommended to use the original packaging; 2) Handle with care during transportation to avoid impact or dropping; 3) When receiving the goods, carefully check the delivery list for any damages (including the product and packaging); 4) If there is any transportation damage, refuse to accept the delivery and contact RoboSense promptly.

5.2 Storage

Important

Improper storage may cause product damage! 1) Store the product in an indoor environment with normal temperature and dry conditions; 2) Handle the product gently to avoid impact or dropping; 3) The product should be stored in a safe environment to avoid corrosion, mechanical impact, or exposure to environments exceeding the protection level; 4) Regularly inspect the condition of all components and packaging, and it is recommended to check every three months.

5.3 Product Cleaning

To ensure accurate perception of the surrounding environment, keep the Fairy's

## Page 39

Fairy User Guide

38 circular protective cover clean.

5.3.1 Precautions

Before cleaning the Fairy, carefully read and understand the content of this section. Improper cleaning may damage the product. When using the LiDAR in harsh environmental conditions, clean the surface regularly to keep the LiDAR clean. Otherwise, it may affect the normal operation of the LiDAR.

5.3.2 Required Materials

1. Clean and dust-free cloth; 2) Neutral solution at moderate temperature (such as soapy water, distilled water, 99% concentration of ethanol, etc.).

5.3.3 Cleaning Method

1. If the LiDAR surface is only covered with some dust: a) Use a clean and dust-free cloth, dip it in a small amount of neutral solution; b) Gently wipe the LiDAR surface; c) Dry it with a clean and dry dust-free cloth. 2) If the LiDAR surface is covered with mud or other solid foreign objects: a) First, spray clean water on the dirty part of the LiDAR surface to remove the mud or foreign objects (Note: Do not directly wipe off the mud with a dust-free cloth, as it may scratch the surface, especially the protective cover); b) Then spray warm soapy water on the dirty part. The lubricating effect of the soapy water helps to remove the foreign objects. Gently wipe the LiDAR surface with a fiber cloth, but be careful not to scratch the surface;

## Page 40

Fairy User Guide

39 c) Finally, rinse off the residual soap on the LiDAR surface with clean water (if there is still residue, clean it again with 99% ethanol) and dry it with a clean and dry dust-free cloth.

## Page 41

Fairy User Guide

40

6 Fault Diagnosis

This chapter lists some common problems encountered during the use of the

product and their corresponding troubleshooting methods. For details, refer to Table 14.

Table 14 Common Fault Troubleshooting Methods

Fault Phenomenon Solution

The Product Motor Does

Not Rotate

Check whether the connector cable on the aviation plug

power/product side is loose or if the wiring harness is damaged.

The Product Keeps

Restarting During Startup

Check the input power connection and polarity;

Check if the voltage and current of the input power meet the

requirements (when 12V voltage is applied, the input current should be ≥ 2A);

Check if the installation plane of the product is level or if the

screws on the bottom of the LiDAR are tightened too tightly.

The Product Internally

Rotates, But There is No

Data

Check if the LiDAR emits light normally; Check if the network connection is normal; Confirm if the computer-side network configuration is correct; Use other software (such as Wireshark) to check if the data is received;

Disable the firewall and other security software that may block

the network; Check if the power supply is normal; Try restarting the product.

Wireshark Can Receive

Data, But RSView Does Not

Display Point Cloud

Close the computer's firewall and run RSView through the firewall; Confirm that the computer's IP configuration matches the destination address set in the product;

Confirm that the Sensor Network Configuration in RSView is

set correctly;

Confirm that the installation directory or configuration file

storage directory of RSView does not contain any Chinese characters;

Confirm that the data packets received by Wireshark are of the

MSOP type.

## Page 42

Fairy User Guide

41

Table 14 (Continuation)

Fault Phenomenon Solution

The Product Has Frequent Data

Loss

Confirm if there is a large number of other network packets

or network conflicts in the network;

Confirm if there are other network products sending a large

amount of data in broadcast mode, causing sensor data blocking; Confirm if the computer's performance and interface performance meet the requirements;

Remove all other network products and directly connect to

the computer to confirm if data loss occurs.

Unable to Synchronize

GPS/PTP/gPTP Time

Confirm if the synchronization mode has been switched to

the correct mode on the web page; Under the GPS time synchronization mode: Confirm if the GPS module's baud rate is 9600 bps, 8 data bits, no parity bit, and 1 stop bit; Confirm if the GPS module outputs 3.3V TTL or RS232 level; Confirm if the 1PPS pulse is continuous and the wiring is correct;

Confirm if the NMEA message format of GPRMC is

correct;

Confirm if the GPS module and interface box share the

same ground; Confirm if the GPS module receives a valid fix; Confirm if the GPS module is validly positioned (outdoors); Under the PTP / gPTP time synchronization mode: Confirm if the PTP / gPTP Master synchronization protocol complies with the current PTP / gPTP protocol; Confirm if the PTP / gPTP Master is working properly.

No Data Output After Passing

Through the Router

Close the DHCP function of the router or set the IP address

of the sensor to the correct IP address internally in the router.

ROS Driver Displays a Fixed

Blank Area Rotating When

Showing Point Cloud

This phenomenon is normal. It occurs because the ROS driver splits the data into fixed packages for frame display.

The blank part of the data will be displayed in the next

frame.

RSView software outputs point

clouds as a single ray For Windows 10 systems, set RSView to run in Windows 7 compatibility mode to resolve the issue. Note: If the above troubleshooting steps fail to resolve the issue, please contact RoboSense for further assistance.

## Page 43

> Contact/support details from this page were omitted from the OpenELAB wiki copy.

42

7 After-sales Service

If the solutions provided in Chapter 6 of the troubleshooting guide do not solve the problem, please promptly contact RoboSense. Official Website: [https://www.robosense.cn/en/contact](https://www.robosense.cn/en/contact) Additional Information: 1) Please wait for a confirmation response from RoboSense after-sales service before sending the product back; 2) When sending the product back, please use the original packaging or an equivalent cushioned and moisture-resistant packaging.

## Page 44

43

Appendix A Web UI Operation

A.1 Product Information The LiDAR Web UI defaults to the product information page, as shown in Figure 15:

Figure 15 Web Page Information

1. Top Board Firmware Version indicates the mainboard firmware version; 2) Bottom Board Firmware Version indicates the baseboard firmware version; 3) Software Version indicates the version of software; 4) Motor Firmware Version indicates the motor firmware version; 5) S/N indicates the serial number of the product; 6) Mac Address Indicates address of the Mac; 7) Model is the product name. A.2 Product Parameter Setting

## Page 45

44 A.2.1 General Setting The "General Setting" bar at the end of the web page is the basic parameter setting page of LiDAR, where you can change the Settings of Device IP, port number, echo mode, speed and Angle trigger. The schematic diagram and function description are shown in Figure 16:

Figure 16 Web Side LiDAR Setting Information

1. Supports unicast (default)/broadcast mode. Set the Destination IP to

255.255.255.255 for broadcast mode, with the factory default being

192.168.1.102; 2) The data port of MSOP and DIFOP can be changed. The value ranges from

## Page 46

45

1025 to 65535;

1. The web can select the Strongest return(default)/Last return/first return and dual return modes from the Return Mode drop-down list; 4) The web can select GPS, PTP-E2E, PTP-P2P, PTP-GPTP, and PTP-E2E L2 from the “Time Synchronization Source” drop-down list to determine the time synchronization mode; 5) The time synchronization domain of PTP can be changed. The value ranges from 0 to 127; 6) Drop down “Respond To PeerDelayRequest” to select OFF (default) and ON to determine whether the LiDAR acts as the slave to respond to peer delay request requests from other nodes; 7) Drop down "No Leap Second" to select OFF (default) and ON to determine whether to respond to the leap second deviation setting of the announce packet; 8) Change the timeout period (5s by default) for the device to exit the time synchronization state due to the loss of the time master message. The value ranges from 1 to 255 seconds; 9) Change the offset threshold (default: 1ms) of the device that switches from the non-synchronous state to the synchronous state. The value ranges from 1 to 255 ms; 10) Change the offset threshold (default: 20ms) between the master and the device that switches from the synchronous state to the non-synchronous state. The value ranges from 1 to 255 ms; 11) Drop down "Operation Mode" to select two working modes: Standby/High Performance (default). When the Standby mode is selected, the lidar motor and transmitter stop working; 12) The Phase lock Angle of the device can be changed. The value ranges from

0 to 360 Degree;

1. Drop down "GPS Baud Rate" to select GPS Baud rate, which can be 9600

## Page 47

46 (default), 14400, 19200, 38400, 43200, 57600, 76800, and 115200; 14) Drop down “Imu Ctrl” to select OFF and ON (default) to determine whether to enable the control interface for the IMU function; 15) Change the communication port of the IMU. The value ranges from 1025 to 65535; 16) Drop down “Imu Output” Rate and select 25Hz/50Hz/100Hz/200Hz (default) to change the IMU output data update frequency; 17) Drop down "Accel Range" and select \[-2g,2g]/\[-4g,4g] (default) /\[-8g,8g]/\[-16g,16g] to change the maximum acceleration range of the IMU accelerometer; 18) Drop down "Gyro Range" and select \[-250,250]dps/\[-500,500]dps (default) /\[-1000,1000]dps/\[-2000,2000]dps to change the range of the IMU gyroscope; 19) To confirm whether the” Restore Default” function is enabled, select OFF and ON from the Restore Default drop-down list. A.2.2 Performance Setting The "Performance Setting" bar at the end of the web page is the LiDAR advanced parameter setting page, where the LiDAR reflectivity performance, drag point and rain and fog filtering and other advanced functions can be set. The schematic diagram and function description are shown in Figure 17:

## Page 48

47

Figure 17 Advanced Function Setting

1. Drop down "Reflectivity Enhancement" to select OFF (default) and ON to determine whether the reflectivity enhancement function is enabled; 2) Drop down "Trail Filter Level" and select 1/2/3/4 (default)/5/6/7 to confirm the trailing filter level; 3) The Frame Start Angle of the device can be changed. The value ranges from

0 to 360 Degree.

A.2.3 Angle Pulse Setting The column "Angle Pulse Setting" on the webpage is the setting page of LiDAR Angle pulse trigger, where the LiDAR Angle trigger signal can be set. The schematic diagram and function description are shown in Figure 18:

Figure 18 Angle Pulse Setting

1. Trigger Mode: There are two starting Angle modes. Mode 1 increases the initial pulse width by 25%; Mode 2 does not increase the initial pulse width (default). 2) Group: This column indicates the SYNC OUT group. Fairy includes SYNC OUT1; 3) Pulse Trigger Switch: Enable or disable the Trigger function. When ON is selected for Pulse Trigger Switch, the editable state is enabled, and the editable state is gray when the Pulse trigger switch is disabled; 4) Pulse Start Angle: The corresponding start Angle can be set. The input value must be an integer; 5) Pulse Width: The corresponding pulse width can be set; 6) Pulse Step: The step can be set. The input value must be a floating point

## Page 49

48 number with one decimal place reserved. Note: 1) The IP address of the Device and Destination IP address must be on the same network segment; otherwise, the connection may fail; 2) The MSOP and DIFOP values range from 1025 to 65535, and the MSOP port and DIFOP port cannot be the same port; 3) After the change is complete, click "Save" to save it. If a‘successful’ message is displayed, the setting takes effect. A.3 Product Diagnostics/Operational Status On this page, the operating status of LiDAR can be viewed in real time, including voltage, current, real-time speed, running time, temperature and other information, as shown in Figure 19:

Figure 19 Web Running Status or Fault Diagnosis

1. View Machine Temperature to obtain the current product operating temperature; 2) View the RPM to obtain the current real-time rotational speed information; 3) View the Phase to obtain the current rotation phase of the product; 4) Laser Status has two states: "On" (default) and "Off". When the user sets the Standby mode, "Off" is used; 5) View the Time Sync Mode to obtain the time synchronization mode of the LIDAR; 6) View Time Sync Data to obtain time synchronization data of LiDAR; 7) View PPP Status to obtain the PPS status;

## Page 50

49 8) View GPRMC Status to obtain GPRMC status; 9) View Time Sync Status to obtain the current time synchronization status. Lock indicates that the time is locked successfully. Unlock indicates that the time is not synchronized successfully; 10) View Startup Times to obtain the total startup times of the current product, which is added up once after each power off and restart; 11) View Elapsed time to obtain the total running time and the accumulated working time of the product under each temperature. Note: 1) The refresh rate of this page is 5 second; 2) If the voltage/current box turns red, check whether the product is in Standby mode. If not, check whether the product works properly. A.4 Product Firmware Upgrade Click on the webpage "System", this page can upgrade the firmware of the product App, baseboard and mainboard, as follows: 1) Please contact RoboSense to get the firmware upgrade. When the firmware to be upgraded is ready, click "Select File", as shown in Figure 20.

Figure 20 Step1 Click Select File

1. Select the folder corresponding to the firmware to be upgraded, select the firmware to be upgraded, and click "Open" (no Chinese characters appear in the path), as shown in Figure 21.

## Page 51

50

Figure 21 Select the File in the Path where the Upgrade Package is Stored

1. At this time, the file name of the firmware to be upgraded will be displayed on the web interface. Select the corresponding upgrade button to upgrade the corresponding firmware, as shown in Figure 22.

Figure 22 The Page is Displayed After the Upgrade File is Selected

Note: 1) The upgrade package should be in .zip format. The web-based upgrade interface only supports uploading .zip files for one-click upgrade; 2) The upgrade package name must meet the following requirements. Otherwise, an error message may be displayed; 3) Main board upgrade file: sequence logic must be suffix ".bin"; 4) Base board upgrade file: sequence logic necessary suffix ".bit"; 5) Web App upgrade file: sequence logic necessary suffix ".hs\_fs.

## Page 52

51 Appendix B R0S\&ROS2 Package rslidar\_sdk is the driver SDK for ROS platform. Please download it from RoboSense homepage on github or contact RoboSense to obtain it. 1) rslidar\_sdk relies on rs\_driver, which is the basic driver of RoboSense. Download rs\_driver from github; 2) If ROS2 is used,rslidar\_sdk also relies on rslidar\_msg, which is the msg definition file, which can be downloaded from github; 3) The driver SDK download package contains rich usage guidelines. Please read the README file and doc folder in the file before using the driver SDK. Note: 1) SDK 2) rs\_driver 3) msg

## Page 53

52

Appendix C DIFOP Data Definitions

This appendix supplements the definitions of each item in the DIFOP protocol

outlined in Section 4.4.3, facilitating user understanding for product use and development. For calculations, big-endian mode is used, and "Value" represents the decimal number derived from the corresponding offset bytes. C.1 Ethernet（ETH）

Table 15 Ethernet

Register of Ethernet（30 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 byte 6 byte 7 byte 8 Fun. LIDAR\_IP DEST\_PC\_IP No. byte 9 byte 10 byte 11 byte 12 byte 13 byte 14 byte 15 byte 16 Fun. MAC\_ADDR MSOP No. byte 17 byte 18 byte 19 byte 20 byte 21 byte 22 Fun. Reserved DIFOP Reserved Register Description: 1) LIDAR\_IP is the source IP address of the LiDAR, occupying 4 bytes; 2) DEST\_PC\_IP is the destination PC's IP address, occupying 4 bytes; 3) MAC\_ADDR is the MAC address of the LiDAR; 4) MSOP and DIFOP each occupy 2 bytes, and the source and destination port numbers are required to be identical. C.2 Mainboard Firmware Version (TOP\_FRM)

Table 16 Mainboard Firmware Version

Mainboard Firmware Version（5 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 Fun. TOP\_FRM Register Description: 1) This register is used to read the mainboard firmware version number; 2) For example, if byte 1 = 0x00, byte 2 = 0x10, byte 3 = 0x04, byte 4 = 0x0c, and byte 5 = 0x00, then the firmware version number is: 00 10 04 0c 00. C.3 Baseboard Firmware Version (BOT\_FRM)

## Page 54

53

Table 17 Baseboard Firmware Version

Baseboard Firmware Version（5 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 Fun. BOT\_FRM Register Description: 1) This register is used to read the baseboard firmware version number; 2) For example, if byte 1 = 0x00, byte 2 = 0x24, byte 3 = 0x12, byte 4 = 0x13, and byte 5 = 0x12, then the firmware version number is: 00 24 12 13 12. C.4 APP Firmware Version (SOF\_FRM)

Table 18 APP Firmware Version

APP Firmware Version（5 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 Fun. SOF\_FRM Register Description: 1) This register is used to read the APP firmware version number; 2) For example, if byte 1 = 0x00, byte 2 = 0x24, byte 3 = 0x12, byte 4 = 0x13, and byte 5 = 0x12, then the firmware version number is: 00 24 12 13 12. C.5 Motor Firmware Version (MOT\_FRM)

Table 19 Motor Firmware Version

Motor Firmware Version（5 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 Fun. MOT\_FRM Register Description: 1) This register is used to read the motor firmware version number; 2) For example, if byte 1 = 0x00, byte 2 = 0x24, byte 3 = 0x12, byte 4 = 0x12, and byte 5 = 0x25, then the firmware version number is: 00 24 12 12 25. C.6 Product Serial Number（SN）

Table 20 Product Serial Number

SN（6 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 byte 6 Fun. SN Register Description:

## Page 55

54 1) This register is used for the device serial number; 2) Similar to a MAC address, it consists of 6 bytes, representing the product serial number in hexadecimal. C.7 Time Sync Mode Setting（TIME\_SYNC\_INFO）

Table 21 Time Sync Information

Time Sync Information (2 bytes) No. byte 1 byte 2 Fun. Time\_Sync\_Mode Time\_Sync\_State Register Description: 1) This register is used to read time synchronization information; 2) Byte 1 is the time synchronization mode status bit, defined as follows: 0x00: GPS; 0x01: E2E-L4; 0x02: P2P; 0x03: gPTP; 0x04: E2E-L2; 3) Byte 2 is the time synchronization success status bit, defined as follows: 0x00: Not synchronized; 0x01: Synchronized successfully. C.8 Time（UTC\_TIME）

Table 22 Register of Time

Register of Time（10 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 byte 6 byte 7 byte 8 byte 9 byte10 Fun. sec us Register Description: 1) This register is used to read time information; 2) The range of the microsecond (us) value: 0 \~ 999,999. C.9 Real-time Motor Speed（REALTIME\_ROTATION\_SPEED）

Table 23 Real-time Motor Speed

Real-time Motor Speed No. byte 1 byte 2 Fun. REALTIME\_ROTATION\_SPEED Register Description: 1) This register is used to read the real-time speed information of the motor; 2) The value is 2 bytes in hexadecimal format; 3) For example, byte1=0x01, byte2=0x28, the actual motor speed converted to decimal is 600. C.10 Vertical Angle calibration（COR\_VERT\_ANG）

## Page 56

55

Table 24 Vertical Angle Calibration Register

Vertical Angle Calibration Register（288bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 byte 6 byte 7 byte 8 byte 9 Fun. Channel 1 Vertical Angle Channel 2 Vertical Angle Channel 3 Vertical Angle No. byte 10 byte 11 byte 12 byte 13 byte 14 byte 15 byte 16 byte 17 byte 18 Fun. Channel 4 Vertical Angle Channel 5 Vertical Angle Channel 6 Vertical Angle No. byte 19 byte 20 byte 21 byte 22 byte 23 byte 24 byte 25 byte 26 byte 27 Fun. Channel 7 Vertical Angle Channel 8 Vertical Angle Channel 9 Vertical Angle No. byte 28 byte 29 byte 30 byte 31 byte 32 byte 33 byte 34 byte 35 byte 36 Fun. Channel 10 Vertical Angle Channel 11 Vertical Angle Channel 12 Vertical Angle No. byte 37 byte 38 byte 39 byte 40 byte 41 byte 42 byte 43 byte 44 byte 45 Fun. Channel 13 Vertical Angle Channel 14 Vertical Angle Channel 15 Vertical Angle No. byte 46 byte 47 byte 48 byte 49 byte 50 byte 51 byte 52 byte 53 byte 54 Fun. Channel 16 Vertical Angle Channel 17 Vertical Angle Channel 18 Vertical Angle No. byte 55 byte 56 byte 57 byte 58 byte 59 byte 60 byte 61 byte 62 byte 63 Fun. Channel 19 Vertical Angle Channel 20 Vertical Angle Channel 21 Vertical Angle No. … … … Fun. … No. byte 262 byte 263 byte 264 byte265 byte 266 byte 267 byte 268 byte 269 byte 270 Fun. Channel 88 Vertical Angle Channel 89 Vertical Angle Channel 90 Vertical Angle No. byte 271 byte 272 byte 273 byte 274 byte 275 byte 276 byte 277 byte 278 byte 279 Fun. Channel 91 Vertical Angle Channel 92 Vertical Angle Channel 93 Vertical Angle No. byte 280 byte 281 byte 282 byte 283 byte 284 byte 285 byte 286 byte 287 byte 288 Fun. Channel 94 Vertical Angle Channel 95 Vertical Angle Channel 96 Vertical Angle Register Description: 1) The Angle value is divided into positive and negative, and the vertical Angle of each channel is composed of 3 bytes, where the first byte represents positive and negative, and the second and third byte jointly constitute the Angle value; 2) If the first byte attribute is 0x00, the vertical Angle of the channel is positive; if the attribute is 0x01, the vertical Angle of the channel is negative; 3) The angular resolution is 0.01°; 4) For example, the value of the channel 5 register is byte 1=0x00, which is positive. byte 2=0x01 and byte 3=0x71 are converted to decimal 369. The vertical Angle of channel 5 is 3.69°. C.11 Horizontal Angle Calibration（COR\_HOR\_ANG）

Table 25 Horizontal Angle Calibration Register

## Page 57

56 Horizontal Angle Calibration Register（288bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 byte 6 byte 7 byte 8 byte 9 Fun. Channel 1 Horizontal Angle Channel 2 Horizontal Angle Channel 3 Horizontal Angle No. byte 10 byte 11 byte 12 byte 13 byte 14 byte 15 byte 16 byte 17 byte 18 Fun. Channel 4 Horizontal Angle Channel 5 Horizontal Angle Channel 6 Horizontal Angle No. byte 19 byte 20 byte 21 byte 22 byte 23 byte 24 byte 25 byte 26 byte 27 Fun. Channel 7 Horizontal Angle Channel 8 Horizontal Angle Channel 9 Horizontal Angle No. byte 28 byte 29 byte 30 byte 31 byte 32 byte 33 byte 34 byte 35 byte 36 Fun. Channel 10 Horizontal Angle Channel 11 Horizontal Angle Channel 12 Horizontal Angle No. byte 37 byte 38 byte 39 byte 40 byte 41 byte 42 byte 43 byte 44 byte 45 Fun. Channel 13 Horizontal Angle Channel 14 Horizontal Angle Channel 15 Horizontal Angle No. byte 46 byte 47 byte 48 byte 49 byte 50 byte 51 byte 52 byte 53 byte 54 Fun. Channel 16 Horizontal Angle Channel 17 Horizontal Angle Channel 18 Horizontal Angle No. byte 55 byte 56 byte 57 byte 58 byte 59 byte 60 byte 61 byte 62 byte 63 Fun. Channel 19 Horizontal Angle Channel 20 Horizontal Angle Channel 21 Horizontal Angle No. … … … Fun. … No. byte 262 byte 263 byte 264 byte 265 byte 266 byte 267 byte 268 byte 269 byte 270 Fun. Channel 88 Horizontal Angle Channel 89 Horizontal Angle Channel 90 Horizontal Angle No. byte 271 byte 272 byte 273 byte 274 byte 275 byte 276 byte 277 byte 278 byte 279 Fun. Channel 91 Horizontal Angle Channel 92 Horizontal Angle Channel 93 Horizontal Angle No. byte 280 byte 281 byte 282 byte 283 byte 284 byte 285 byte 286 byte 287 byte 288 Fun. Channel 94 Horizontal Angle Channel 95 Horizontal Angle Channel 96 Horizontal Angle Register Description: 5) The Angle value is divided into positive and negative, and the horizontal offset Angle of each channel is composed of 3 bytes, where the first byte represents positive and negative, and the second and third byte jointly constitute the Angle value; 6) If the first byte attribute is 0x00, the channel horizontal offset Angle is positive, and if the attribute is 0x01, the channel horizontal offset Angle is negative; 7) The angular resolution is 0.01°; 8) For example, the value of the channel 5 register is byte 1=0x01, which is negative. byte 2=0x00 and byte 3=0xae are converted to decimal 174. The horizontal offset Angle of channel 5 is -1.74°. C.12 Mainboard Input Voltage（MAINBOARD\_VOLTAGE）

## Page 58

57

Table 26 Mainboard Input Voltage

Mainboard Input Voltage

No. byte 1 byte 2 Fun. Mainboard Voltage Register Description: 1) This register is used to read the mainboard input voltage of the device; 2) Unit: V. The voltage value consists of 2 bytes. The calculation formula is: Mainboard Voltage = Value / 100. C.13 Device Input Voltage (MACHINE\_VOLTAGE)

Table 27 Device Input Voltage

Device Input Voltage

No. byte 1 byte 2 Fun. Machine Voltage Register Description: 1) This register is used to read the overall input voltage of the device; 2) Unit: V. The voltage value consists of 2 bytes. Formula: the Machine Voltage = Value / 100. C.14 Baseboard 12V Voltage (BOTTOMBOARD\_VOLTAGE （12V）)

Table 28 Baseboard 12V Voltage

Baseboard 12V Voltage No. byte 1 byte 2 Fun. Bottomboard Voltage（12V） Register Description: 1) This register is used to read the device's backplane 12V voltage; 2) Unit: V. The voltage value consists of 2 bytes. Formula: Bottomboard Voltage (12 v) = Value / 100. C.15 IMU Calibration Data（IMU\_CALIB\_DATA）

Table 29 IMU Data

IMU Calibration Data（28 bytes） No. byte 1 byte 2 byte 3 byte 4 byte 5 byte 6 byte 7 byte 8 Fun. q\_x q\_y

## Page 59

58 No. byte 9 byte 10 byte11 byte 12 byte 13 byte 14 byte 15 byte 16 Fun. q\_z q\_w No. byte 17 byte 18 byte19 byte 20 byte 21 byte 22 byte 23 byte 24 Fun. x y No. byte 25 byte 26 byte27 byte 28 Fun. z Register Description: 1) This register is used to obtain IMU calibration data relative to the LiDAR coordinate system; 2) The calibration data includes attitude estimation and position offset, in 32-bit float format (IEEE754 compliant); 3) For example, the current bytes for x (byte 17\~byte 20) are 3b 8b 43 96. The calculation method is as follows: a) First, combine the 4 bytes into a 32-bit binary number: 00111011

10001011 01000011 10010110;

b) Separate the sign bit, exponent field, and mantissa field. The sign bit is bit 31 (0), the exponent field is bits 23~~30 (01110111), and the mantissa field is bits 0~~22 (00010110100001110010110); c) Calculate the values of each field according to IEEE 754: Sign field: 0 (positive number); Exponent field: 01110111 (decimal 119), actual exponent = 119 - 127 = -8. Mantissa field:

00010110100001110010110 (represents fractional part). Adding the

implied leading 1, the mantissa becomes 1.00010110100001110010110 (decimal 1.088); d) Calculate the floating-point number using the formula:

## Page 60

59

Appendix D Structural Drawings

## Page 61

60

## Page 62

61 Appendix E Per-channel transmission delay table

Table 30 Per-channel transmission delay table

Channel

index

Transmission

delay（ns）

Channel

index

Transmission

delay（ns） 00-07 0 24-31 28160 08-15 5280 32-39 42240 16-23 14080 40-47 51040

## Page 63

62

## Source Notes

* Review date: 2026-06-04.
* Local source file: `Fairy_EN_48TX_V1.0.pdf`.
* Product link: [https://openelab.io/products/robosense-fairy-mid-range-lidar.](https://openelab.io/products/robosense-fairy-mid-range-lidar.)
* Content basis: local PDF text extraction with page markers preserved.
* Omitted content: manufacturer contact emails, phone numbers, addresses, working hours, and support contact blocks.
