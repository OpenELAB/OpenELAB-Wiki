# LIVOX Mid-360S User Manual

> LIVOX Mid-360S User Manual

{% embed url="https://openelab.io/products/livox-mid360" %}

## 1 Product Profile <a href="#block-394d4c79856d8027b3aef6966f94a9c4" id="block-394d4c79856d8027b3aef6966f94a9c4"></a>

### **1.1 Overview** <a href="#block-380d4c79856d80a98899fa6c1eb5819d" id="block-380d4c79856d80a98899fa6c1eb5819d"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8c9a648d-e9a7-4b69-8151-1a382c5bee2b/image/w=1920,quality=90,fit=scale-down" alt="image" height="196.31165888280043" width="469.9875183105469">

**1. Optical Window**

The laser beam passes through the optical window and scans objects in the FOV.

**2. M12 Aviation Connector**

The M12 aviation connector can be connected to the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) for quick testing and debugging. Users can use customized cables according to the connector pinout table to improve the water-resistant and dustproof protection ability of the LiDAR sensor. Refer to the M12 Aviation Connector section for more information on the M12 aviation connector.

**3. Locating Hole**

The locating hole makes it easy for users to find the correct place to mount a fixed support for the product. Refer to the Dimensions section for more information.

**4. M3 Mounting Holes**

Mount the product to an appropriate location using the M3 screws and the mounting holes.

\[1] Visit the DJI official store to purchase the Livox Aviation Connector 1-to-3 Splitter Cable. The Livox Aviation Connector 1-to-3 Splitter Cable can only be used for testing and debugging. It is recommended to customize the cable and connectors for other scenarios that require high reliability.

### **1.2 Connector Definition** <a href="#block-381d4c79856d8045b360f0e1c291599c" id="block-381d4c79856d8045b360f0e1c291599c"></a>

#### **M12 Aviation Connector** <a href="#block-381d4c79856d80d2b7d3f4199735850e" id="block-381d4c79856d80d2b7d3f4199735850e"></a>

The product uses a high-reliability M12 A-Code aviation connector (male). The M12 12P A-code fully shielded male connector meets the IEC 61076-2-101 standard. The recommended female connector type is Finecables, part number MA12FAHD12STXXXB14. Both connectors have an IP rating of IP67. Users can connect the product with the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) for transmission of power, control signal, and data.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8fcc7963-fe6b-4091-b798-b1c1ba9cf396/image/w=1920,quality=90,fit=scale-down" alt="image" height="198.49988367061806" width="488.9875183105469">

You can also use other cables instead of the Livox Aviation Connector 1-to-3 Splitter Cable to improve overall protection (such as dust and water resistance). However, strictly observe the following guidelines:

* Shielded cables are recommended for communication and power supply connections. For cables subject to prolonged exposure or friction, apply protective measures (such as corrugated tubing) to prevent damage to the insulation.
* When routing cables, the bending radius must be at least 60mm.
* Secure the aviation connector to prevent vibration-induced loosening.

#### **Livox Aviation Connector 1-to-3 Splitter Cable** <a href="#block-381d4c79856d80a8b641c690fee5b4d2" id="block-381d4c79856d80a8b641c690fee5b4d2"></a>

Users can connect the product with the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately). The Livox Aviation Connector 1-to-3 Splitter Cable has a M12 aviation connector (female) on one end, and the other is split into the power, Ethernet, and function cables. The cable length is 1.5 meters. The M12 aviation connector (female) connects to the M12 aviation connector (male) on the product. The power cable connects to an external DC power supply. The Ethernet cable has a RJ-45 network connector which connects to the RJ-45 connector on a computer for data transmission during testing. If users need GPS time synchronization (not required), connect the function cable (pin 8 and 10) to the corresponding synchronization source, with the GPS serial port configured as: baud rate 9600, 8 data bits, no parity. Visit Livox Wiki for more information about time synchronization: [https://livox-wiki-cn.readthedocs.io](https://livox-wiki-cn.readthedocs.io/)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d78c17e8-2326-4d2a-95cb-e0557173ece8/image/w=1920,quality=90,fit=scale-down" alt="image" height="171.8978134666121" width="670.9874877929688">

See below for more information on the Livox Mid-360S M12 aviation connector (male) and the Livox Aviation Connector 1-to-3 Splitter Cable:

| **M12 Aviation Connector (male/female) Pins** | **Signal**   | **Type**          | **Description**    | **Color**        | **Function**   |
| --------------------------------------------- | ------------ | ----------------- | ------------------ | ---------------- | -------------- |
| 1                                             | Power+       | Power             | DC 9V-27V          | Red (positive)   | Power Cable    |
| 9                                             | Power+       | Power             | DC 9V-27V          |                  |                |
| 2                                             | Ground       | Power             | Ground             | Black (negative) |                |
| 3                                             | Ground       | Power             | Ground             |                  |                |
| 4                                             | Ethernet-TX+ | Output            | Ethernet-TX+       | Orange/white     | Ethernet cable |
| 5                                             | Ethernet-TX- | Output            | Ethernet-TX-       | Orange           |                |
| 6                                             | Ethernet-RX+ | Input             | Ethernet-RX+       | Green/white      |                |
| 7                                             | Ethernet-RX- | Input             | Ethernet-RX-       | Green            |                |
| 8                                             | LVTTL\_IN    | Input 3.3V LVTTL  | Pulse per second   | Purple/white     | Function cable |
| 10                                            | LVTTL\_IN    | Input 3.3V LVTTL  | GPS input          | Gray/white       |                |
| 11                                            | LVTTL\_OUT   | Output 3.3V LVTTL | Reserved output IO | Purple           |                |
| 12                                            | LVTTL\_OUT   | Output 3.3V LVTTL | Reserved output IO | Gray             |                |

## 2 Product Characteristics <a href="#block-381d4c79856d8044baf6fb1b5ac2e393" id="block-381d4c79856d8044baf6fb1b5ac2e393"></a>

### **2.1 Effective FOV Range** <a href="#block-381d4c79856d80debb0deab756d927d8" id="block-381d4c79856d80debb0deab756d927d8"></a>

The FOV of the product is 360° horizontally and 59° at maximum vertically. When mounting the sensor, make sure that the FOV is not blocked by any objects. Visit [https://www.livoxtech.com/mid-360s/downloads](https://www.livoxtech.com/mid-360s/downloads) to download the 3D model of the product and its FOV.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d819dd90-312e-40f9-8841-c0c003a78839/image/w=1920,quality=90,fit=scale-down" alt="image" height="205.3342917675545" width="724.8125">

Note that the effective detection range of the product varies based on where the object is within the FOV. For the vertical FOV, the closer to the upper edge, the shorter the effective detection range is; the closer to the lower edge, the longer the effective detection range is. Refer to the diagram below. Pay attention to the effective detection range when in use.

As shown below, when an object with a reflectivity of 10% is placed near the lowest border of the vertical FOV, the object can be detected as far as 40m. The closer to the upper part of the vertical FOV, the shorter the effective detection range.

💡

**Note:** Overlapping with other Lidar FOV should be avoided. If the laser beams are pointed right at each other, irreversible damage may be caused to the product.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f58f16f2-365c-4396-b293-e29caf58e455/image/w=1920,quality=90,fit=scale-down" alt="image" height="225.24742723547894" width="627.9625244140625">

### **2.2 Non-Repetitive Scanning Technology** <a href="#block-381d4c79856d807ea986f80c743baf66" id="block-381d4c79856d807ea986f80c743baf66"></a>

The product has a high coverage ratio due to its non-repetitive scanning technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surrounding area. The figure below displays the point cloud patterns of the product over different integration times (0.1 s, 0.2 s, 0.5 s and 1 s), using the non-repetitive scanning technology.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cc61bd71-023d-4254-aa18-397921630568/image/w=1920,quality=90,fit=scale-down" alt="image" height="139.54966452742124" width="724.8125">

The figure below displays the FOV coverage of the product using the non-repetitive scanning technology, compared with traditional mechanical LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is 0.1 seconds, the FOV coverage of the product is similar to a 32-line mechanical LiDAR sensor. As the integration time increases to 0.5 seconds, the FOV coverage of the product approaches 70%, which is higher than that of a 64-line mechanical LiDAR sensor, most of the areas will be illuminated by laser beams.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/282d3929-f3b2-4096-8345-7361949ead88/image/w=1920,quality=90,fit=scale-down" alt="image" height="398.96866084627084" width="530.9874877929688">

💡

The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams.

The FOV coverage (C) can be calculated with the following formula:

C=TotalareailluminatedbylaserbeamsTotalareainFOV∗100%C=TotalareainFOVTotalareailluminatedbylaserbeams​∗100%

Refer to the official Livox website for more information about how the FOV coverage is calculated.

The figure below shows the average angular gap change curve of the point cloud over different integration times using the non-repetitive scanning technology. Users can select the integration time according to the size and distance of the target object.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e7078069-b121-44f8-b214-e3e8fac2805d/image/w=1920,quality=90,fit=scale-down" alt="image" height="363.2732505980861" width="724.8125">

## 3 Usage <a href="#block-381d4c79856d80258b90e3b1a076a9a5" id="block-381d4c79856d80258b90e3b1a076a9a5"></a>

### **3.1 Mounting** <a href="#block-381d4c79856d80cba09feb0562a8cf50" id="block-381d4c79856d80cba09feb0562a8cf50"></a>

#### **Mounting Notice** <a href="#block-381d4c79856d80c68339e5e71fc7a4d3" id="block-381d4c79856d80c68339e5e71fc7a4d3"></a>

Read and understand the following warnings before mounting the product:

1. Dust and stains on the optical window will negatively affect the performance of the LiDAR sensor. Follow the instructions in the Maintenance section to clean the optical window using compressed air, isopropyl alcohol, or a lens cloth. Mount the product after cleaning it.
2. When mounting the product, the FOV must not be blocked by an object, including glass.
3. There is no orientation requirement when mounting the product. Use the bottom surface for mounting. If mounting the product upside down, allow a space of no less than 0.5m between the mounting surface and the ground. Contact Livox if you have special installation needs.
4. The product cannot bear any extra payload. Otherwise, the reliability of the product cannot be guaranteed.
5. When mounting the product, allow a space of at least 10mm around the device to prevent poor airflow which can affect heat dissipation.
6. It is recommended to mount the product on a flat metal surface. The metal base plate should have a thickness of no less than 3mm, and an area of no less than 10000mm^2 on the metal plate should be exposed to the air for heat dissipation.

#### **Dimensions** <a href="#block-381d4c79856d807fb4dbc1c127966b59" id="block-381d4c79856d807fb4dbc1c127966b59"></a>

The bottom surface of the product has four M3 mounting holes with a depth of 5mm. Refer to the dimensions and the mounting holes in the diagrams below to mount or embed the product to or in an appropriate place on the target base.

Unit: mm

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b861f05f-d82a-4c41-9f9d-e7ec6661a6b5/image/w=1920,quality=90,fit=scale-down" alt="image" height="298.7707814445828" width="724.8125">

### 3.2 External Power Supply <a href="#block-381d4c79856d804a994aff238cf94a49" id="block-381d4c79856d804a994aff238cf94a49"></a>

The working voltage range of the product is from 9 V to 27 V, the recommended working voltage is 12 V. The minimum working voltage should be increased in a low-temperature environment. When the product is connected to an external power source directly using the M12 aviation connector, make sure the output voltage range of the external power source is within the operating voltage range of the product. When an extension cable is required, make sure to increase the output voltage of the external power source due to the extra voltage reduction. Make sure the maximum voltage does not exceed 27 V.

The product has a working power of 6.5 W when working normally. The working power varies at different temperatures. Make sure the power supply is suitable based on the working voltage range and the startup peak power of the product.

* -20°C to 0°C : The product will enter self-heating mode automatically. In self-heating mode, the working power of the product can reach 14 W, which lasts at most 10 minutes.
* 0°C to 35°C : The startup power is 18 W (which lasts for about 8 seconds).
* above 35°C : The startup power is 9 W (which lasts for about 8 seconds).

💡

**Note:**

* Note that the power cable may generate voltage fluctuation where the voltage exceeds 27 V in some scenarios, such as if the power cable is interfered with or other devices connected to another power source in the parallel circuit suddenly power off. In such scenarios, the product may not work normally or even be damaged.
* The value is for reference only. In normal conditions, the start-up peak power varies depending on each sensor.

### 3.3 Connection <a href="#block-381d4c79856d8079b9b1c55bd1857462" id="block-381d4c79856d8079b9b1c55bd1857462"></a>

The product uses a M12 aviation connector for power supply as well as data transmission. Refer to the Connectors section for more information about the connector. It is recommended to use the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) when testing or using the product temporarily. The Livox Aviation Connector 1-to-3 Splitter Cable contains the M12 aviation connector (female), power cable (bare wires), function cable (wires with insulation), and Ethernet cable (with RJ-45 connector).

The product transfers data using the User Datagram Protocol (UDP). It supports the static IP address configuration. All the Livox Mid-360S LiDAR sensors are set to static IP address mode by default with an IP address of 192.168.1.1XX (XX stands for the last two digits of the Livox Mid-360S LiDAR sensor's serial number). The default subnet masks of the Livox Mid-360S LiDAR sensors are all 255.255.255.0 and their default gateways are 192.168.1.1. Directly connect the product to a computer when using for the first time.

1. Before connecting, set the IP address of the computer to static IP address mode. Follow the steps to set the IP address of the computer to a static IP address:

* **Windows system**

1. Click to enter the Network and Sharing Center under Control Panel.
2. Select the network you are using and then click Properties.
3. Double click Internet Protocol Version 4 (TCP/IPv4).
4. Set the static IP address of the computer to 192.168.1.50, the subnet mask is set at 255.255.255.0.Click OK to complete.

* **Ubuntu-18.04 system**

The IP address of the computer can be configured by using the ifconfig command at the terminal. The configuration code is as below:

Copy

```javascript
~$ sudo ifconfig enp4s0 192.168.1.50
```

(replace enp4s0 with the network port name of the computer)

2. Connect the product as shown below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/436ad206-ae7b-467e-83b8-f7105ba2a14b/image/w=1920,quality=90,fit=scale-down" alt="image" height="146.97333370948618" width="724.8250122070312">

1. Connect the M12 aviation connector (female) on the Livox Aviation Connector 1-to-3 Splitter Cable with the M12 aviation connector (male) on Livox Mid-360S.The lock nut of the M12 aviation connector (female) should be tightened with a wrench to ensure there is a secure connection with the M12 aviation connector (male). Make sure there is no gap between them.
2. Connect the RJ-45 network connector on the Livox Aviation Connector 1-to-3 Splitter Cable to the computer.
3. If GPS time synchronization is required, connect the function cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the corresponding synchronization source.
4. Connect the power cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the external power source. Pay attention to the input voltage range and polarity.

💡

**Note:**

* When connecting the power cable and the function cable, pay attention to their respective voltage ranges and polarities. DO NOT connect any PoE device to the RJ-45 network connector. Incorrect connection can lead to irreversible damage to the LiDAR.
* When inserting the Livox Aviation Connector 1-to-3 Splitter Cable, be sure to align the positioning key with the positioning slot inside the connector. Push the connector straight in slowly. Do not insert it at an angle or force it in, as this may bend the pins. To secure the connection, hand-tighten the metal nut first, then use a wrench to apply a torque of 1.5 to 2.0 N·m. Only turn the metal nut. DO NOT twist or apply torque to the cable.
* Connect the function cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the corresponding synchronization source if needed.
* When multiple Livox Mid-360S are connected to one computer in static IP address mode, make sure all sensors connected have different static IP addresses, and they are connected to the computer using a switch.
* If more than three Livox Mid-360S are required, use a gigabit router or switch.
* The broadcast number for each LiDAR sensor can be viewed using the QR code sticker on the back of the LiDAR sensor or in the Device Manager of Livox Viewer 2.
* Launch Livox Viewer 2 on the computer after Livox Mid-360S is connected. Click the device with the static IP address that should be altered. Click to open the settings page and set the static IP address of Livox Mid-360S.

### **3.4 Coordinates** <a href="#block-381d4c79856d80889a9ee6ec983f570d" id="block-381d4c79856d80889a9ee6ec983f570d"></a>

The Cartesian coordinates O-XYZ of the product is defined as below: Point O is the origin, and O-XYZ is the point cloud coordinates of the product.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/987b35e9-4d44-43a4-9eee-c65972a500f4/image/w=1920,quality=90,fit=scale-down" alt="image" height="280.13507228542016" width="724.8250122070312">

### 3.5 Output Data <a href="#block-381d4c79856d80819350effa301ad255" id="block-381d4c79856d80819350effa301ad255"></a>

The output information of LiDAR sensors includes: Information Push, Point Cloud Data and IMU Data. For detailed output information formats, refer to the communication protocol section of Livox Wiki: [https://livox-wiki-cn.readthedocs.io](https://livox-wiki-cn.readthedocs.io/)

#### **Information Push** <a href="#block-381d4c79856d807a94dbcc92b8155406" id="block-381d4c79856d807a94dbcc92b8155406"></a>

After power-on, the product periodically pushes LiDAR sensor information to the set IP address (the broadcast address by default), including device information, user configuration and current status. Below is part of the pushed information.

| **Type**           | **Content**                       | **Description**                                                                                                                                      |
| ------------------ | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Device Information | Serial Number                     | The only identification number for the product.                                                                                                      |
|                    | Firmware Version                  | Firmware Version                                                                                                                                     |
|                    | Hardware Version                  | Hardware Version                                                                                                                                     |
|                    | MAC Address                       | The MAC address of the network card.                                                                                                                 |
| User Configuration | LiDAR sensor IP address           | Configure the IP address, subnet mark and gateway for the LiDAR sensor.                                                                              |
|                    | Target Address                    | Configure the target address for pushing information and sending point cloud data.                                                                   |
|                    | Point Cloud Data Format           | Configure different coordinates.                                                                                                                     |
|                    | IMU Data                          | Configure the switch for pushing IMU data, which is enabled by default.                                                                              |
|                    | LiDAR Sensor Extrinsic Parameters | Configure the extrinsic parameters calibration information for the LiDAR sensor (the LiDAR sensor only stores and does not use this information).    |
|                    | Working Mode                      | The target working state. Users can change this setting. The default working mode is Sampling (i.e. starting to collect point cloud after power-on). |
|                    | FOV Configuration                 | If users do not need the full FOV of 360°, users can configure the LiDAR sensor to work in a certain range of FOV.                                   |
|                    | Detection Mode                    | Configure as Normal or Sensitive detection mode. The default detection mode is Normal. \[1]                                                          |
| Current Status     | The current working status.       | The current working status.                                                                                                                          |
|                    | Internal Temperature              | The current temperature of the crucial internal components of the LiDAR sensor.                                                                      |
|                    | Error Code                        | If the LiDAR sensor malfunctions, users can use the error code to confirm the reason and classify the error.                                         |

\[1] If the detection mode is configured as Sensitive detection mode, the ability for detecting low-reflectivity objects can be enhanced, achieving better detection effect for extremely dark or bright objects. Note that the noise rate may increase slightly in this mode.

#### **Point Cloud Data** <a href="#block-381d4c79856d80aa8875e834b7e3c0a1" id="block-381d4c79856d80aa8875e834b7e3c0a1"></a>

Normally, the product starts to output point cloud data after power-on. The point cloud data includes: **target reflectivity, coordinates, tags, and timestamp.**

A point cloud is the collection of the points where the surface of an object was detected in the FOV of the LiDAR sensor. Each point contains the following information.

* **Target reflectivity:** expressed by a number from 0 to 255. 0 to 150 corresponds to the reflectivity within the range of 0 to 100% in the Lambertian reflection model. 151 to 255 corresponds to the reflectivity of target objects with retroflection properties. When the target is less than 2 m from the product, it may result in a large reflectivity error. The data should only be used to distinguish whether the target is total reflective or diffuse reflective.
* **Coordinates:** The coordinates of the product can be expressed in Cartesian coordinates (x, y, z) or in Spherical coordinates (r, θ, φ). The relation between the two coordinate systems are as shown below. When there is no object within the detection range or the object is placed beyond the detection range (such as further than 100 m), the coordinates of the point cloud will be expressed as (0, 0, 0) in Cartesian coordinates, and as (0, θ, φ) in Spherical coordinates.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/67e9e2a9-2a1f-423c-a0ea-60ab08a96773/image/w=1920,quality=90,fit=scale-down" alt="image" height="336.3817211990238" width="624.9874877929688">

* **Tags:** Indicates additional information about the detected points. Point cloud tags are 8-bit unsigned integers, which are divided into several groups. Each group indicates one property of the detected point, including rain, fog, dust, and dragging noise between objects, etc. The confidence level indicates the credibility of the detected points. "0" stands for normal point cloud data (high confidence level); low confidence level indicates that the detected point is highly affected by the corresponding type of noise, and as a result the detection result has low credibility. Filter the point cloud based on the tag information.

The format of the tag is as shown below:

| **Bit\[7-6]** | **Bit\[5-4]**                                                                                                                             | **Bit\[3-2]**                                                                                                                                                                       | **Bit\[1-0]**                                                                                                                                                       |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reserved      | Detected points property: Other 0: High confidence level (normal points) 1: Moderate confidence level 2: Low confidence level 3: Reserved | Detected points property: Atmospheric particles like rain, fog, and dust. 0: High confidence level (normal points) 1: Moderate confidence level 2: Low confidence level 3: Reserved | Detected points property: Dragging noise between objects. 0: High confidence level (normal points) 1: Moderate confidence level 2: Low confidence level 3: Reserved |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |

* **Timestamp:** There are two ways to synchronize data with the Mid-360: IEEE 1588-2008 and GPS. Timestamps are displayed in format of 64-bit integers, and the unit is ns. Visit Livox Wiki for more detailed information about time synchronization: [https://livox-wiki-cn.readthedocs.io](https://livox-wiki-cn.readthedocs.io/)
* **IEEE 1588-2008:** IEEE 1588-2008 is the Precision Time Protocol (PTP) enabling precise synchronization of clocks in measurement and control systems by Ethernet. Livox LiDAR sensors, as the ordinary clock in the PTP, only supports UDP/IPV4 for PTP. Livox LiDAR sensors support the following message events: Sync, Follow\_up, Delay\_req, and Delay\_resp.
* **GPS:** GPS is a way to synchronize the data using the PPS signal and GPS message events. PPS port logic is the same as the PPS synchronization mentioned above. GPS messages (GPRMC) are sent to the corresponding pins through the serial port (see the Connectors section in this user manual). The pulse interval in PPS signal is t0 (t0=1000 ms) while the continuous time of high-level voltage is t1 (t1 > 1 us). Besides sending GPS messages through serial port, users can also send the timestamp information of each pulse to the product in network packets. For specific communication commands, refer to the communication protocol section.

#### **IMU Data** <a href="#block-381d4c79856d8008b88cd28c659fe6a6" id="block-381d4c79856d8008b88cd28c659fe6a6"></a>

The LiDAR sensor is integrated with an IMU chip (with a 3-axis accelerometer and a 3-axis gyroscope). By default, the product starts to push IMU data at a frequency of 200 Hz after power-on, which can be enabled or disabled using the host computer. The IMU data contains the 3-axis acceleration and 3-axis angular velocity, the directions of which are the same with that of the point cloud coordinates. The position of the IMU chip in the point cloud coordinates is x = 11.0mm, y = 23.29mm, z = -44.12mm.

Refer to the communication protocol section for specific communication protocol and data formats.

### **3.6 Working States and Working Modes** <a href="#block-381d4c79856d800f926ce94582a36211" id="block-381d4c79856d800f926ce94582a36211"></a>

The working state of the product refer to the current working state of the LiDAR sensor, while the working mode refers to the target working mode selected by the user.

#### **Working States** <a href="#block-381d4c79856d80b6bc94e03b5581b464" id="block-381d4c79856d80b6bc94e03b5581b464"></a>

| **Working States** | **Description**                                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------ |
| Sampling           | The LiDAR sensor is powered on and working normally (emitting laser beams).                                        |
| Idle               | All components are powered off apart from the communication module. The lowest power consumption is in this state. |
| Error              | The LiDAR sensor will enter error status when an error is detected.                                                |
| Self-check         | The LiDAR sensor is conducting the power-on self-check.                                                            |
| Startup            | The LiDAR sensor is starting.                                                                                      |
| Upgrading          | The LiDAR sensor is updating the firmware.                                                                         |
| Ready              | The LiDAR sensor is powered on and ready to emit laser beams.                                                      |

#### **Working Modes Descriptions** <a href="#block-381d4c79856d802b97c6c53bc9c25e7c" id="block-381d4c79856d802b97c6c53bc9c25e7c"></a>

The working modes refer to the target working modes selected by the user. The product has three working modes: idle, ready, and sampling. Users can select different working modes using Livox Viewer 2 or Livox SDK 2.

### **3.7 Livox Viewer 2** <a href="#block-381d4c79856d800b8544ed13473f1462" id="block-381d4c79856d800b8544ed13473f1462"></a>

Livox Viewer 2 is software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos, and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

Visit [http://www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer 2. Livox Viewer 2 supports Windows® 10 (64 bit) and Ubuntu™ 18.04 (64 bit). Follow the steps below to use Livox Viewer 2.

💡

**Note:**

For Windows users, Livox Viewer 2 may fail to detect LiDAR sensors if Windows Firewall is turned on. In this situation, go to the Control Panel to turn off Windows Firewall and restart Livox Viewer 2.

**Windows Users:** unzip the downloaded file and click to open the .exe file named "Livox Viewer 2".

**Ubuntu Users:** unzip the downloaded file, and run the command **. / livox\_viewer\_2. sh** file in the root directory of the unzipped folder.

For more information, download the Livox Viewer 2 User Manual from the official website: [http://www.livoxtech.com](http://www.livoxtech.com/).

### **3.8 Software Development Kit** <a href="#block-381d4c79856d80b58084e8e523cbe4e2" id="block-381d4c79856d80b58084e8e523cbe4e2"></a>

#### **Livox SDK 2** <a href="#block-381d4c79856d807f8bd3eb53bd4a6135" id="block-381d4c79856d807f8bd3eb53bd4a6135"></a>

Besides using Livox Viewer 2 to check real-time point cloud data, users can also use the Livox SDK 2 to apply the point cloud acquired from Livox LiDAR sensors to different scenarios, such as:

* Configure the LiDAR Sensor: configure the parameters of the LiDAR sensor and check the status.
* Get Point Cloud Data: get the point cloud coordinates from the LiDAR sensor.
* Firmware Update: conduct firmware update of the LiDAR sensor.

Visit [https://github.com/Livox-SDK/Livox-SDK2](https://github.com/Livox-SDK/Livox-SDK2) to see more detailed information about Livox SDK 2 API documentation.

#### **SDK Communication Protocol** <a href="#block-381d4c79856d806489afff723a3f129c" id="block-381d4c79856d806489afff723a3f129c"></a>

Both Livox Viewer 2 and Livox SDK 2 communicate with LiDAR sensors using the SDK communication protocol. Users can also develop their own software based on the SDK communication protocol to realize communication with and controlling the LiDAR sensor, and collecting the point cloud coordinates.

Visit [https://livox-wiki-cn.readthedocs.io](https://livox-wiki-cn.readthedocs.io/) to learn more information about SDK communication protocol.

## 4 Storage, Transportation, and Maintenance <a href="#block-381d4c79856d80a59058e2a5e48b6fe5" id="block-381d4c79856d80a59058e2a5e48b6fe5"></a>

### **4.1 Storage** <a href="#block-381d4c79856d80e98340fccaa61e5b40" id="block-381d4c79856d80e98340fccaa61e5b40"></a>

The storage temperature for the product is from -40° to 70° C (-40° to 158° F). Keep the product in a dry and dust-free environment.

💡

**Note:**

* Make sure the product is not exposed to environments containing poisonous or corrosive gases or materials.
* DO NOT drop the product and be careful when placing it in storage or taking it out of storage.
* If the product is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

### **4.2 Transportation** <a href="#block-381d4c79856d80ba8f36ef5a6ad19844" id="block-381d4c79856d80ba8f36ef5a6ad19844"></a>

* Before transportation, place the product in a suitable box and make sure it is secure.
* Make sure to place foam inside the transportation box and that the box is clean and dry.
* Always handle with care during transportation. Protect it from any impact, bumps, and never drop it to the ground.

### **4.3 Maintenance** <a href="#block-381d4c79856d8050abcbebfdfcaae6b0" id="block-381d4c79856d8050abcbebfdfcaae6b0"></a>

Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor. Make sure to regularly clean the optical window to prevent this from happening. Check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. **Use compressed or canned air:** Clean the optical window with compressed or canned air before wiping the optical window.

💡

**Note:**

* DO NOT directly wipe a dusty optical window as it will only cause more damage.

2. **Wipe the stains:** It is recommended to use a clean and dry lens tissue to gently wipe the optical window. If the optical window is still dirty, use the lens tissue provided with a small amount of isopropyl alcohol and wipe slowly to remove the dirt.

## 5 Appendix <a href="#block-381d4c79856d80baa013cc66b89db742" id="block-381d4c79856d80baa013cc66b89db742"></a>

### **5.1 Troubleshooting** <a href="#block-381d4c79856d80ee9c18ee883cb89ade" id="block-381d4c79856d80ee9c18ee883cb89ade"></a>

The table below shows you how to troubleshoot and resolve common issues with LiDAR sensors. If the issue persists, contact Livox.

1. Cannot detect the LiDAR sensor:

* Make sure that all cables are correctly wired.
* Make sure the voltage of the power supply is suitable. The voltage should be between 9 V and 27 V. If connected with the Livox Aviation Connector 1-to-3 Splitter Cable, the voltage range of the supported external power source is from 9 V to 27 V.
* Make sure that the LiDAR sensor is not connected to other software.
* Make sure that the LiDAR sensor and the host computer is connected to the same LAN.
* Make sure no security software is installed that would block Ethernet broadcasts.
* If the issue persists, turn off all firewalls, restart Livox Viewer 2 and try again.
* Confirm the packet outputs of all connected devices using another application (e.g., Wireshark).

2. Cannot connect to the detected LiDAR sensor/Cannot start sampling

* Make sure that all cables are correctly wired.
* Make sure the voltage is correct. The working voltage range for the product is from 9 V to 27 V. If connected with the Livox Aviation Connector 1-to-3 Splitter Cable, the voltage range of the supported external power source is from 9 V to 27 V.
* If the issue persists, reboot the LiDAR sensor and restart Livox Viewer 2.

3. No data received:

* Confirm the packet outputs for all connected devices using another application (e.g., Wireshark).

### **5.2 Specifications** <a href="#block-381d4c79856d8079b2ccc162db7faf3c" id="block-381d4c79856d8079b2ccc162db7faf3c"></a>

Visit the following website for specifications.

[https://www.livoxtech.com/mid-360s/specs](https://www.livoxtech.com/mid-360s/specs)

### 5.3 After-Sales Information <a href="#block-381d4c79856d80df8c48fec9bfe41757" id="block-381d4c79856d80df8c48fec9bfe41757"></a>

Visit [https://www.livoxtech.com/support](https://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox LiDAR sensors.
