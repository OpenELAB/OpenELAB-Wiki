---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Robosense E1R

### Robosense E1R

***

### Product Link

{% embed url="https://openelab.io/products/robosense-e1r-solid-state-lidar" %}

### Description

Product Structure:

<figure><img src="../../.gitbook/assets/image (994).png" alt=""><figcaption></figcaption></figure>

Optical Envelope FOV Definition:

The optical envelope of the E1R is shown in Figure 2. After all limits are accumulated, the optical envelope ofthe LiDAR cannot be blocked by exterior parts of the vehicle, such as LiDAR cover, roof panel, engine hood, and front bumper, which may block the field of view (FOV) of some parts.

<div><figure><img src="../../.gitbook/assets/image (995).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (996).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (997).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (998).png" alt=""><figcaption></figcaption></figure></div>

### Specifications

The E1R uses a flash scanning method to measure distances up to 30 meters. Each frame produces a high number of points, at a rate of 26,000 points. The horizontal range of the scan is 120° (-60.0° to +60.0°), while the vertical range is 90° (-45° to +45°).

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"><p>Ranging</p><p>principle</p></td><td valign="top">Time ofFlight</td><td valign="top">FOV(horizontal)</td><td valign="top">120°（-60.0°~+60.0°)</td></tr><tr><td valign="top">safety class</td><td valign="top">Class1 eye safe</td><td valign="top">FOV(vertical)</td><td valign="top">90°（-45°~+45°)</td></tr><tr><td valign="top"><p>Ranging</p><p>distance  1</p></td><td valign="top"><p>30m @10% NIS,</p><p>100klux direct sunlight</p></td><td valign="top"><p>Angular</p><p>resolution(horizontal)</p></td><td valign="top"><p> </p><p>average 0.625°2</p></td></tr><tr><td valign="top">Blind area</td><td valign="top">0.1 m</td><td valign="top"><p>Angular</p><p>resolution(vertical)</p></td><td valign="top"> </td></tr><tr><td valign="top"><p>Count of the</p><p>points</p></td><td valign="top">~260,000 points/second</td><td valign="top">Ranging Precision3</td><td valign="top">±5cm@1 sigma</td></tr><tr><td valign="top"><p>Time</p><p>Synchronizatio</p><p>n</p></td><td valign="top"><p>gPTP（IEEE-802.1AS）</p><p>PTP E2E L2（IEEE-</p><p>1588）</p></td><td valign="top"><p>Ethernet transmission</p><p>rate</p></td><td valign="top">1000Base-T1 Gigabit Ethernet</td></tr><tr><td valign="top">Frame rate</td><td valign="top">10 Hz</td><td valign="top">Operating Voltage</td><td valign="top">9V - 16V</td></tr><tr><td valign="top"><p>Power</p><p>Consumption4</p></td><td valign="top">&#x3C;10 W</td><td valign="top">Weight</td><td valign="top"><p>330 g±20 g (only</p><p>LiDAR)</p></td></tr><tr><td valign="top"><p>Operating</p><p>Temperature  5</p></td><td valign="top">- 40℃ ~ + 85℃</td><td valign="top">Storage Temperature:</td><td valign="top">- 40℃ ~ + 105℃</td></tr><tr><td valign="top"><p>Protection</p><p>Rating</p></td><td valign="top">IP67 / IP6K9K</td><td valign="top"> </td><td valign="top"></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Size</td><td valign="top">Name</td><td valign="top">length（mm）</td><td valign="top">width（mm）</td><td valign="top">height（mm）</td></tr><tr><td valign="top"><p> </p><p> </p><p>Size</p></td><td valign="top">Outer Contour</td><td valign="top">95</td><td valign="top">42.6</td><td valign="top">69.5</td></tr><tr><td valign="top"> </td><td valign="top"><p>Outer contour of main</p><p>body with connector and</p><p>installation position</p><p>contour</p></td><td valign="top"><p> </p><p> </p><p>95</p></td><td valign="top"><p> </p><p> </p><p>51.1</p></td><td valign="top"><p> </p><p> </p><p>87</p></td></tr></tbody></table>

### Product Installation Recommendations

#### Interface Description

E1R Platform Connector:

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Connector Scheme</td><td valign="top"><p>Connection</p><p>Type</p></td><td valign="top"><p> </p><p>Model</p></td><td valign="top"><p> </p><p>Picture</p></td><td valign="top"><p> </p><p>Function</p></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>TE Bow-mount Type</p><p>(Two-in-one plug,</p><p>6+2pin)</p></td><td valign="top"><p> </p><p>LiDAR End</p><p>Connector</p></td><td valign="top"><p> </p><p>TE</p><p>2397179-1</p></td><td valign="top"> <img src="../../.gitbook/assets/image (999).png" alt=""></td><td valign="top"><p>Power +</p><p>Gigabit</p><p>Ethernet</p></td></tr><tr><td valign="top"> </td><td valign="top"><p> </p><p>Wire harness</p><p>Connector</p></td><td valign="top"><p> </p><p>TE</p><p>2397144-1</p></td><td valign="top"> <img src="../../.gitbook/assets/image (1000).png" alt=""></td><td valign="top"><p>Power +</p><p>Gigabit</p><p>Ethernet</p></td></tr></tbody></table>

Connection Installation Requirements:

* The wire harness end connectors and wires, after being assembled with the LiDAR end connectors, must meet the waterproof grades of IP67 and IP6K-9K. The specific selection is the responsibility of the customer;
* It is recommended that at least 70mm of hand space be reserved for plugging and unplugging at the end of the wire harness connector and the surrounding environment.

Entire machine Wire Harness End Installation Requirements:

* The material of the Ethernet wire harness should use STP wires that meet 1000BASE-T1;
* It is recommended to use Dacra 686-3 (with a bending radius of 25 mm) or GGX9305 (with a bending radius of 12 mm), subject to the recommendation of the wiring harness supplier;
* The total length of the Ethernet wire harness is recommended to be less than 15m, and the number of connectors should not exceed 3 pairs (including wire pairs);
* Ethernet signal lines should be routed in the entire machine, and it is recommended to avoid moving sections and high-temperature areas;
* The power supply needs to take into account the wire length, wire diameter and impedance. The working voltage of the lidar on the power line should be maintained at 9V - 16V;
* It is recommended that the LiDAR wiring harnesses exposed to the outside be designed with waterproof rubber sleeves.

#### The Connection of Interface Box

Vehicle Ethernet Harness Interface and Definition:

<figure><img src="../../.gitbook/assets/image (1001).png" alt=""><figcaption></figcaption></figure>

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Wiring Description</td><td valign="top">TE Interface Box Structure Diagram</td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>Connecting to the LiDAR side</p></td><td valign="top"><div><figure><img src="../../.gitbook/assets/image (1002).png" alt=""><figcaption></figcaption></figure></div></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>Connecting to the power supply and host computer side</p></td><td valign="top"><div><figure><img src="../../.gitbook/assets/image (1003).png" alt=""><figcaption></figcaption></figure></div></td></tr></tbody></table>

Power Interface:

The E1R interface box uses standard DC 5.5-2.1 interfaces.

When the power supply is normal, the green indicator of the power supply box is steady on. When the green indicator is off, check whether the power input is normal. If the power input is normal, the interface box may be damaged. Contact RoboSense.

RJ45 network port

The E1R body supports only 1000BASE-T1 on-board Ethernet. When the interface box is used, the network interface uses the standard RJ45 interface. The interface box supports only Gigabit Ethernet.

#### LiDAR State Machine

When the wake- up pin inputs a high level of 9-16V, the LiDAR wakes up.

<figure><img src="../../.gitbook/assets/image (1004).png" alt=""><figcaption></figcaption></figure>

### LiDAR Usage

#### Coordinate System

<figure><img src="../../.gitbook/assets/image (1005).png" alt=""><figcaption></figcaption></figure>

#### RSView

In the detection of data from E1R, free tools such as Wireshark and tcp-dump can be used to obtain raw data. Meanwhile, RSView can assist users in visualizing raw data more conveniently.

Software Features:

RSView provides real-time visualization of any RoboSense LiDAR data. RSView can also review pre-recorded data stored in “pcap” (Packet Capture) files, but RSView still does not support playing “ .pcapng” files.

RSView displays distance measurements from a RoboSense LiDAR as point data.

It  supports  custom-colored  display  of  variables  such  as  intensity-of-return,  time, distance, azimuth, and laser ID. The data can be exported in ‘ .csv format ’. The RSView 4.3.11 or later version supports generating LAS format point cloud files.

Functionality and features ofRSView include:

* Visualize live streaming sensor data over Ethernet
* Record live sensor data to pcap files
* Visualize sensor data from a recorded pcap file
* Different types of visualization modes, such as distance, time, azimuth, etc
* Display point data in a spreadsheet
* Export point cloud data in CSV format
* Distance measurement tool
* Display multiple frames of data simultaneously (Trailing Frames)
* Crop views

Install RSView:

RSView supports running on Windows 64-bit, Ubuntu 18.04 or higher operating systems.   You    can    download    the   latest   installer   from   RoboSense   website ([http://www.robosense.ai/resource](http://www.robosense.ai/resource)). Launch the downloaded installer and follow the instructions to finish the installation. After installation is completed, a shortcut will be generated  on  the  desktop.  Make  sure  the  installation  path  only  contains  English characters.

Use RSView:

For details on using RSView for operation, please refer to the RS-LiDAR User Guide by pressing the F1 button, or clicking the Help option in menu bar.

#### Communication Protocol

The communication between E1R and the computer is through Ethernet, and uses UDP protocol. There are two types of output packets: MSOP packet and DIFOP packet.

All MSOP packets involved in this document are with fixed length of 1200 bytes, DIFOP packets  are  with  fixed  length  of 256  bytes.  E1R  network  parameters  are configurable, and the factory default IP and fixed client port number are set as listed in the Table:

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"></td><td valign="top">IP Address</td><td valign="top">MSOP Port Number</td><td valign="top">DIFOP Port Number</td></tr><tr><td valign="top">E1R</td><td valign="top">192.168.1.200</td><td valign="top">6699</td><td valign="top">7788</td></tr><tr><td valign="top">Computer</td><td valign="top">192.168.1.102</td><td valign="top">6699</td><td valign="top">7788</td></tr></tbody></table>

The default MAC address of the LiDAR is initially set at the factory, and the MAC address of each LiDAR is unique.

When using the LiDAR in unicast mode, you need to set the computer's IP to the same network segment as the LiDAR, for example,  192.168.1.x (the range of x is 1\~254),  and  the  subnet  mask  as  255.255.0.0.  If  you  don't  know  the  network configuration information ofthe LiDAR, please set the host computer subnet mask to 255.255.0.0 to connect to the LiDAR and use Wireshark to capture the LiDAR output packet for analysis.

The communication protocol between E1R and the computer is mainly divided into two categories. See the Table for the protocol list.

The main data stream output protocol (MSOP), encapsulates the distance, angle, reflectivity and other information measured by the LiDAR into a package and outputs it to the computer.

LiDAR  information   output  protocol   (DIFOP),  outputs  various   configuration information ofthe LiDAR currently in use to the computer.

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Protocol</td><td valign="top">Abbreviation</td><td valign="top">Function</td><td valign="top">Type</td><td valign="top">Packet size</td></tr><tr><td valign="top">Main Data Stream Output Protocol</td><td valign="top">MSOP</td><td valign="top">Output measured data</td><td valign="top">UDP</td><td valign="top">1200 Bytes</td></tr><tr><td valign="top">Device Information Output Protocol</td><td valign="top">DIFOP</td><td valign="top">Output device information</td><td valign="top">UDP</td><td valign="top">256 Bytes</td></tr></tbody></table>

Main Data Stream Output Protocol (MSOP):

Main data Stream Output Protocol is abbreviated as MSOP.

I/O type: LiDAR output, computer analysis.

Default port number: 6699.

The MSOP packets output three-dimensional measurement related data, including laser ranging value, return reflectivity value, vertical angle, horizontal angle and time stamp.The payload length of the MSOP packet is  1200 bytes, which consists  of a synchronization header of 32 bytes, a data packet of 1152 bytes (a total of 96 data blocks of 12 bytes), and a tail of 16 bytes.

<figure><img src="../../.gitbook/assets/image (1006).png" alt=""><figcaption></figcaption></figure>

Header:

The header is 32-bytes long, and is used for identification of the starting position of data, packet counting, UDP communication reservation, and time stamp storage.

<table data-header-hidden><thead><tr><th width="172" valign="top"></th><th></th><th></th><th></th><th></th></tr></thead><tbody><tr><td valign="top">Header(32Bytes)</td><td></td><td></td><td></td><td></td></tr><tr><td valign="top">Sync</td><td>PktCnt</td><td>Ver</td><td>ReturnMode</td><td>TimeMode</td></tr><tr><td valign="top">4 Bytes</td><td>2 Bytes</td><td>2 Bytes</td><td>1 Byte</td><td>1 Byte</td></tr><tr><td valign="top">Timestamp</td><td>FrameSync</td><td>Res0</td><td>LidarType</td><td>LidarTmp</td></tr><tr><td valign="top">10 Bytes</td><td>1 Byte</td><td>9 Bytes</td><td>1 Byte</td><td>1 Byte</td></tr></tbody></table>

Sync: can be used as a packet inspection sequence, and the identification header is 0x55, 0xaa, 0x5a, 0xa5.

PktCnt: Packets Sequence Number, packet counting in a circular counting manner, the count value of the first data packet of each frame is 0, the count value of the last data packet of each frame is the maximum value.

Ver: version number of the UDP communication protocol.

ReturnMode: return mode flag, 4 means strongest return, which is fixed.

TimeMode: Time synchronization mode:

* 0x00: currently using the LiDAR internal timing.
* 0x02: currently using PTP E2E time synchronization mode.
* 0x03: currently using gPTP time synchronization mode.

Timestamp: store timestamps. The defined timestamp is used to record the system.

time. The high 6 bytes are the second bits, and the low 4 bytes are the microsecond bits.

FrameSync: frame synchronization state（0x00:no      0x01:yes）

Res0: reserved bit

LidarType: the type of LiDAR, default is 0x62.

LidarTmp: LiDAR’s temperature, Temp = LidarTmp – 80

Data Packet:

The data packet in the MSOP packet stores the data measured by the LiDAR, it has a total of 1152 bytes consisting of 96 data blocks, each data block has 12 bytes

<table data-header-hidden><thead><tr><th valign="top"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td valign="top">Data block (12Bytes)</td><td></td><td></td><td></td></tr><tr><td valign="top">content</td><td>offset</td><td>byte</td><td>instruction</td></tr><tr><td valign="top"><p> </p><p> </p><p>TimeOffset</p></td><td><p> </p><p> </p><p>0</p></td><td><p> </p><p> </p><p>2</p></td><td>The time offset of all points in the block relative to the timestamp of the packet,  the time of this group of points equals to</td></tr></tbody></table>

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"></td><td valign="top"> </td><td valign="top"> </td><td valign="top">Timestamp + time_offset</td></tr><tr><td valign="top"><p> </p><p> </p><p>Radius</p></td><td valign="top"><p> </p><p> </p><p>2</p></td><td valign="top"><p> </p><p> </p><p>2</p></td><td valign="top"><p>In the polar coordinate system, the radial</p><p>distance value of the points, the distance</p><p>resolution is 5mm</p></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>DirVectorX</p></td><td valign="top"><p> </p><p> </p><p> </p><p>4</p></td><td valign="top"><p> </p><p> </p><p> </p><p>2</p></td><td valign="top"><p>Unit direction vector X axis component of channel 1, the value ranges from</p><p>-32768 to 32767, and divides by 2^15 to</p><p>float.</p></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>DirVectorY</p></td><td valign="top"><p> </p><p> </p><p> </p><p>6</p></td><td valign="top"><p> </p><p> </p><p> </p><p>2</p></td><td valign="top"><p>Unit direction vector Y axis component of channel 1, the value ranges from</p><p>-32768 to 32767, and divides by 2^15 to</p><p>float.</p></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>DirVectorZ</p></td><td valign="top"><p> </p><p> </p><p> </p><p>8</p></td><td valign="top"><p> </p><p> </p><p> </p><p>2</p></td><td valign="top"><p>Unit direction vector Z axis component of channel 1, the value ranges from</p><p>-32768 to 32767, and divides by 2^15 to</p><p>float.</p></td></tr><tr><td valign="top"><p> </p><p>Intensity</p></td><td valign="top"><p> </p><p>10</p></td><td valign="top"><p> </p><p>1</p></td><td valign="top"><p>Reflection intensity value of the channel</p><p>1 points, the value range is 0~255</p></td></tr><tr><td valign="top"><p> </p><p>PointAttribute</p></td><td valign="top"><p> </p><p>11</p></td><td valign="top"><p> </p><p>1</p></td><td valign="top"><p>Attribute of the channel 1 point, 1</p><p>indicates normal, 2 indicates noisy point,</p></td></tr></tbody></table>

{% hint style="info" %}
Related calculation specification:

Calculation of the radial distance: (Radius is 2-byte long, the unit is millimeter, and the resolution is 5mm.)

Get the hexadecimal number of the radius value of a charnel in the data packet: R1 is 0x03, R2 is 0xfc

0x03 is the high digit of the distance, converted to decimal is 3, 0xfc is the low digit of the distance, converted into decimal is 252.

Therefore: the radial distance of this channel=R1\*256+R2=3\*256+252=1020.

According to the resolution of the coordinates, it is converted to meters: 1020\*0.005=5.10m.

Therefore, the radial distance of this channel in the corresponding elevation and azimuth direction is 5.1 m.

Calculation of XYZ coordinates:

XYZ coordinates can be calculated from the following equations:

![](<../../.gitbook/assets/image (1007).png>)
{% endhint %}

Tail:

The frame tail contains parameters used by LiDAR E2E Profile4

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">content</td><td valign="top">offset</td><td valign="top">byte</td><td valign="top">instruction</td></tr><tr><td valign="top">Res1</td><td valign="top">1184</td><td valign="top">4</td><td valign="top">Reserved</td></tr><tr><td valign="top">DataLength</td><td valign="top">1188</td><td valign="top">2</td><td valign="top">04 B0</td></tr><tr><td valign="top">Counter</td><td valign="top">1190</td><td valign="top">2</td><td valign="top">00 00~FF FF</td></tr><tr><td valign="top">DataId</td><td valign="top">1192</td><td valign="top">4</td><td valign="top">00 00 0E 5C</td></tr><tr><td valign="top">Crc32</td><td valign="top">1196</td><td valign="top">4</td><td valign="top"></td></tr></tbody></table>

LiDAR Information Output Protocol is abbreviated as DIFOP:

I/O type: LiDAR output, computer read.

Default port number: 7788.

DIFOP is an "output-only" protocol to periodically send the LiDAR serial number (S/N), firmware version information, host computer driver compatibility information, network configuration information, calibration information, operating status, and fault diagnosis information to users. By reading DIFOP, users can learn specific information of various parameters ofthe LiDAR currently in use.

<table data-header-hidden><thead><tr><th valign="top"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td valign="top">DIFOP Packet(256Bytes)</td><td></td><td></td><td></td></tr><tr><td valign="top">content</td><td>offset</td><td>byte</td><td>instruction</td></tr><tr><td valign="top">DifopHeader</td><td>0</td><td>8</td><td>DIFOP recognition head</td></tr><tr><td valign="top">Res0</td><td>8</td><td>8</td><td>Reserved</td></tr><tr><td valign="top">SW Version</td><td>16</td><td>3</td><td>LIDAR SW version information</td></tr><tr><td valign="top">Res1</td><td>19</td><td>1</td><td>Reserved</td></tr><tr><td valign="top">SN</td><td>20</td><td>6</td><td>Serial number</td></tr><tr><td valign="top">Res2</td><td>26</td><td>18</td><td>Reserved</td></tr><tr><td valign="top">LocalIP</td><td>44</td><td>4</td><td>LIDAR IP source address</td></tr><tr><td valign="top">NetMask</td><td>48</td><td>4</td><td>Subnet mask</td></tr><tr><td valign="top">MacAddress</td><td>52</td><td>6</td><td>LIDAR IP local Mac address</td></tr><tr><td valign="top">MsopRemoteIp</td><td>58</td><td>4</td><td>Msop remote IP address</td></tr><tr><td valign="top">MsopLocalPort</td><td>62</td><td>2</td><td>Msop local port number</td></tr><tr><td valign="top">MsopRemotePort</td><td>64</td><td>2</td><td>Msop Remote port number</td></tr><tr><td valign="top">DifopRemoteIp</td><td>66</td><td>4</td><td>Difop Remote IP address</td></tr><tr><td valign="top">DifopLocalPort</td><td>70</td><td>2</td><td>Difop Local port number</td></tr><tr><td valign="top">DifopRemotePort</td><td>72</td><td>2</td><td>Difop Remote port number</td></tr><tr><td valign="top">Res3</td><td>74</td><td>25</td><td>Reserved</td></tr><tr><td valign="top">FrequecySetting</td><td>99</td><td>1</td><td>LIDAR frame rate setting</td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>ReturnMode</p></td><td><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>100</p></td><td><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>1</p></td><td><p>LIDAR echo information：</p><p>0x00: FarthestWave</p><p>0x04: StrongestWave (Default)</p><p>0x07: NearestWave</p><p>0x08: 2ndStrongestWave</p><p>0x09: StrongestFarthestWave</p><p>0x0A: NearestFarthestWave</p></td></tr></tbody></table>

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top"></td><td valign="top"> </td><td valign="top"> </td><td valign="top">0x0B: Strongest2ndStrongestWave</td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>TimesyncMode</p></td><td valign="top"><p> </p><p> </p><p> </p><p>101</p></td><td valign="top"><p> </p><p> </p><p> </p><p>1</p></td><td valign="top"><p>Time Synchronization Mode:</p><p>0x0: Internal</p><p>0x2: E2E L2</p><p>0x3: GPTP</p></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p>TimesyncStatus</p></td><td valign="top"><p> </p><p> </p><p> </p><p>102</p></td><td valign="top"><p> </p><p> </p><p> </p><p>1</p></td><td valign="top"><p>Time Syne Status: 0x00: failed</p><p>0x01: success</p><p>0x02: timeout</p></td></tr><tr><td valign="top"><p> </p><p> </p><p>TimeStatus</p></td><td valign="top"><p> </p><p> </p><p>103</p></td><td valign="top"><p> </p><p> </p><p>10</p></td><td valign="top"><p>Timestamp:</p><p>0-5bytes: Second</p><p>6-9bytes: MicroSecond</p></td></tr><tr><td valign="top"><p> </p><p> </p><p> </p><p> </p><p>PHYMode</p></td><td valign="top"><p> </p><p> </p><p> </p><p> </p><p>113</p></td><td valign="top"><p> </p><p> </p><p> </p><p> </p><p>1</p></td><td valign="top"><p>PHY Mode:</p><p>0x00: auto-negotiation 0x01: master</p><p>0x02: slave</p><p>other: same as 0x00</p></td></tr><tr><td valign="top">Res4</td><td valign="top">114</td><td valign="top">142</td><td valign="top">Reserved</td></tr></tbody></table>

### Storage

{% hint style="info" %}
Storage Inadequate can lead to equipment damage!

* Please store the equipment in an indoor environment with normal temperature and dryness;
* Handle the equipment carefully to avoid collisions, drops, and other dangerous behaviors;
* The products should be stored in a safe environment to prevent corrosion, mechanical impact, and exposure to environments above the protective level;
* Regularly check the status of all components and packaging. It is recommended to conduct inspections every 3 months.
{% endhint %}

### Documents

{% file src="../../.gitbook/assets/E1R User Guide.pdf" %}

{% file src="../../.gitbook/assets/E1_Certification.zip" %}

### 3D model

{% file src="../../.gitbook/assets/Robosense E1R 3D model.zip" %}
