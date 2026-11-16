# LIVOX Mid-360 User Manual

> LIVOX Mid-360 User Manual

{% embed url="https://www.livoxtech.com/mid-360/downloads" %}

## **Product Profile** <a href="#block-394d4c79856d80399822de9521edd12e" id="block-394d4c79856d80399822de9521edd12e"></a>

### **Introduction** <a href="#block-382d4c79856d808db406fd556f1e4be9" id="block-382d4c79856d808db406fd556f1e4be9"></a>

Livox Mid-360 is a high-performance LiDAR sensor that can be used for multiple applications including automated guided vehicles, robotics, smart cities, and other fields, and supports the realization of mapping, positioning, recognition, obstacle avoidance, and other functions. Livox Mid-360 can detect objects as close as 0.1 meters away, and it has a detection range of up to 100 meters. **Compact Design:** The Mid-360 features a compact design with a size resembling a tennis ball and a weight of only 265 g, which makes it more suitable for realization of mapping and obstacle avoidance on small-scale robots.

**Wide FOV:** The FOV of Mid-360 is 360° horizontally and 59° at maximum vertically. The wide FOV enables Mid-360 to detect objects around more efficiently.

**High Angular Precision:** With an advanced opto-mechanical system design, the Mid-360 has an increased detection range and higher point cloud density and coverage. In addition, the Mid-360 has the non-repetitive scanning technology which can capture more details.

**High Reliability:** The Mid-360 offers enhanced reliability as the design works normally without rotating internal electronic devices such as the transmitter and receiver. In addition, the Mid-360 has achieved an IP67 waterproof and dustproof rating (excluding accessories such as the cables). It has an operation temperature range of -20° to 55° C (-4° to 131° F). It also meets the testing requirements for random vibration in section 4.1.2.4 of GB/T 28046.3-2011 (mainland China) and ISO 16750-3:2007 (outside mainland China).

**Built-in IMU Module:** The Mid-360 is embedded with a 3-axis accelerometer and a 3-axis gyroscope. Users turn on or turn off the information push through Livox Viewer 2 or Livox SDK 2. The Mid-360 pushes information at 200Hz.

**User-Friendly Livox Viewer 2:** Livox Viewer 2 is a software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos, and analyzes 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

**Open Source Livox SDK 2:** A software development kit (SDK) is provided to help develop customizable applications using the data acquired from the point cloud data. Livox SDK 2 supports Windows/Linux/Mac OS/ROS. Visit [https://github.com/Livox-SDK/Livox-SDK2](https://github.com/Livox-SDK/Livox-SDK2) to learn more.

**Livox ROS Driver 2:** Livox provides open source drivers for ROS1 and ROS2. Visit [https://github.com/Livox-SDK/livox\_ros\_driver2](https://github.com/Livox-SDK/livox_ros_driver2) to learn more.

### **Product Characteristics** <a href="#block-382d4c79856d800b85cad4ca160a7dbf" id="block-382d4c79856d800b85cad4ca160a7dbf"></a>

Livox Mid-360 adopts a smart and reliable optical design, equipped with non-repetitive scanning technology.

**Non-Repetitive Scanning Technology**

Livox Mid-360 has a high coverage ratio due to its non-repetitive scanning technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surrounding area.

The figure below displays the point cloud patterns of Livox Mid-360 over different integration times (0.1 s, 0.2 s, 0.5 s and 1 s), using the non-repetitive scanning technology.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/15b7e2d9-160d-4913-b2d1-74050ef19de1/image/w=1920,quality=90,fit=scale-down" alt="Point cloud patterns of Livox Mid-360 accumulated over different integration times." height="174.2737331931306" width="724.7999877929688">

Point cloud patterns of Livox Mid-360 accumulated over different integration times.

The figure below displays the FOV coverage of Livox Mid-360 using the non-repetitive scanning technology, compared with traditional mechanical LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is 0.1 seconds, the FOV coverage of Livox Mid-360 is similar to a 32-line mechanical LiDAR sensor. As the integration time increases to 0.5 seconds, the FOV coverage of Livox Mid-360 approaches 70%, which is higher than that of a 64-line mechanical LiDAR sensor, most of the areas will be illuminated by laser beams.

![The FOV coverage of Livox Mid-360 and non-Livox LiDAR sensors using common mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1470803b-cba8-4de0-b6ca-151bfbaa7e41/image/w=1920,quality=90,fit=scale-down)

The FOV coverage of Livox Mid-360 and non-Livox LiDAR sensors using common mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.💡

The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams. The FOV coverage (C) can be calculated with the following formula:

C=TotalareailluminatedbylaserbeamsTotalareainFOV∗100%C=TotalareainFOVTotalareailluminatedbylaserbeams​∗100%

Refer to the official Livox website for more information about how the FOV coverage is calculated.

The figure below shows the average angular gap change curve of the point cloud over different integration times using the non-repetitive scanning technology. Users can select the integration time according to the size and distance of the target object.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/996cae2a-58ce-45ea-9753-371ed7a9cae4/image/w=1920,quality=90,fit=scale-down" alt="Point cloud average angular gap of Livox Mid-360 over different integration times." height="342.6691772885284" width="724.8125">

Point cloud average angular gap of Livox Mid-360 over different integration times.

### **Overview** <a href="#block-382d4c79856d80fcbdadd8702245b295" id="block-382d4c79856d80fcbdadd8702245b295"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/44dc4a23-7b90-417b-b451-03f06f6c4f65/image/w=1920,quality=90,fit=scale-down" alt="image" height="259.8707349053745" width="679.9625244140625">

1. **Optical Window**

The laser beam passes through the optical window and scans objects in the FOV.

2. **M12 Aviation Connector**

The M12 aviation connector can be connected to the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) for quick testing and debugging. Users can use customized cables according to the connector pinout table to improve the waterproof and dustproof protection ability of the LiDAR sensor. Refer to the Connectors section for more information on the M12 aviation connector.

3. **Locating Hole**

The locating hole makes it easy for users to find the correct place to mount a fixed support for the Mid-360. Refer to the Dimensions section for more information.

4. **M3 Mounting Holes**

Mount Livox Mid-360 to an appropriate location using the M3 screws and the mounting holes.

💡

**Note:**

Visit the DJI official store to purchase the Livox Aviation Connector 1-to-3 Splitter Cable. The Livox Aviation Connector 1-to-3 Splitter Cable can only be used for testing and debugging. It is recommended to customize the cable and connectors for other scenarios that require high reliability.

## Connectors <a href="#block-382d4c79856d80c48e30c3fee55fc359" id="block-382d4c79856d80c48e30c3fee55fc359"></a>

### **M12 Aviation Connector** <a href="#block-382d4c79856d807c805cc540159a1b26" id="block-382d4c79856d807c805cc540159a1b26"></a>

The Mid-360 uses a high-reliability M12 A-Code aviation connector (male). The M12 12P A-code fully shielded male connector meets the IEC 61076-2-101 standard. The recommended female connector type is Finecables, port number MA12FAHD12STXXXB14. Both connectors have an IP rating of IP67. Users can connect Livox Mid-360 with the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) for transmission of power, control signal, and data. Users can also replace the cable with other cables to improve the dustproof and waterproof protection of the LiDAR sensor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/af1ac5b6-c39f-40b4-bc44-ca10d176833e/image/w=1920,quality=90,fit=scale-down" alt="image" height="181.07425551140446" width="418.9750061035156">

**Livox Aviation Connector 1-to-3 Splitter Cable**

Users can connect Livox Mid-360 with the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately). The Livox Aviation Connector 1-to-3 Splitter Cable has an M12 aviation connector (female) on one end, and the other is split into the power, Ethernet, and function cables. The cable length is 1.5 meters.

The M12 aviation connector (female) connects to the M12 aviation connector (male) on Livox Mid-360. The power cable connects to an external DC power supply. The Ethernet cable has an RJ-45 network connector which connects to the RJ-45 connector on a computer for data transmission during testing. If users need GPS time synchronization (not required), connect the function cable (pin 8 and 10) to the corresponding synchronization source, with the GPS serial port configured as: baud rate 9600, 8 data bits, no parity. Visit Livox Wiki for more information about time synchronization: [https://livox-wiki-en.readthedocs.io](https://livox-wiki-en.readthedocs.io/).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cd19c6a8-40b7-4c78-9d87-6eed77f1c83b/image/w=1920,quality=90,fit=scale-down" alt="image" height="198.56193997567158" width="724.7999877929688">

See below for more information on the Mid-360 M12 aviation connector (male) and the Livox Aviation Connector 1-to-3 Splitter Cable.

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
| 11                                            | LVTTL\_OUT   | Output 3.3V LVTTL | Reserved output IO | Gray             |                |
| 12                                            | LVTTL\_OUT   | Output 3.3V LVTTL | Reserved output IO | Purple           |                |
| 2 & 3                                         | Ground       | Ground            | Ground             | Black            |                |

## Mounting Livox Mid-360 <a href="#block-382d4c79856d8062a913ea4c514424e4" id="block-382d4c79856d8062a913ea4c514424e4"></a>

### Effective FOV Range <a href="#block-382d4c79856d805b809fdf3d541b1d2e" id="block-382d4c79856d805b809fdf3d541b1d2e"></a>

The FOV of Livox Mid-360 is 360° horizontally and 59° at maximum vertically. When mounting the sensor, make sure that the FOV is not blocked by any objects. Visit [www.livoxtech.com/mid-360](http://www.livoxtech.com/mid-360) to download the 3D model of the Mid-360 and its FOV.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b05a2f9c-f92d-4311-bce1-b1e6f5d038ce/image/w=1920,quality=90,fit=scale-down" alt="Effective FOV of the Mid-360" height="194.78666251046317" width="501.9875183105469">

Effective FOV of the Mid-360

Note that the effective detection range of Livox Mid-360 varies based on where the object is within the FOV. For the vertical FOV, the closer to the upper edge, the shorter the effective detection range is; the closer to the lower edge, the longer the effective detection range is. Refer to the diagram below. Pay attention to the effective detection range when in use.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f8b3f735-c80f-4f4c-b0be-237efc210ba6/image/w=1920,quality=90,fit=scale-down" alt="Effective Detection Range inside FOV of the Mid-360" height="218.89912561716767" width="574.9750366210938">

Effective Detection Range inside FOV of the Mid-360

As shown above,when an object with a reflectivity of 10% is placed near the lowest border of the vertical FOV, the object can be detected as far as 40 m. The closer to the upper part of the vertical FOV,the shorter the effective detection range.

💡

**Note:**

Overlapping with other Lidar FOVs should be avoided. If the laser beams are pointed right at each other, irreversible damage may be caused to the Mid-360.

### Mounting Notice <a href="#block-382d4c79856d80f5afb7d4dc93f388ec" id="block-382d4c79856d80f5afb7d4dc93f388ec"></a>

Read and understand the following warnings before mounting the Mid-360.

1. Dust and stains on the optical window will negatively affect the performance of the LiDAR sensor. Follow the instructions in the Maintenance section to clean the optical window using compressed air, isopropyl alcohol, or a lens cloth. Mount the Mid-360 after cleaning it.
2. When mounting the Mid-360, the FOV must not be blocked by an object, including glass.
3. There is no orientation requirement when mounting the Mid-360. Use the bottom surface for mounting. If mounting the Mid-360 upside down, allow a space of no less than 0.5m between the mounting surface and the ground. Contact Livox if you have special installation needs.
4. The Mid-360 cannot bear any extra payload. Otherwise, the reliability of the product cannot be guaranteed.
5. When mounting the Mid-360, allow a space of at least 10mm around the device to prevent poor airflow which can affect heat dissipation.
6. It is recommended to mount the Mid-360 on a flat metal surface. The metal base plate should have a thickness of no less than 3mm and an area of no less than 10000mm² on the metal plate should be exposed to the air for heat dissipation.

### **Dimensions** <a href="#block-382d4c79856d804f8c07cf6f05e9e398" id="block-382d4c79856d804f8c07cf6f05e9e398"></a>

The bottom surface of the Mid-360 has four M3 mounting holes with a depth of 5mm. Refer to the dimensions and the mounting holes in the diagrams below to mount or embed the Mid-360 to or in an appropriate place on the target base.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/76ef7ede-5fc2-4410-b8f0-a05658e55885/image/w=1920,quality=90,fit=scale-down" alt="Mid-360 Dimensions (refer to Appendix 1)" height="299.048513986014" width="724.8125">

Mid-360 Dimensions (refer to Appendix 1)

Livox Mid-360 Weight and Dimensions

| **Weight** | Approx. 265 g                            |
| ---------- | ---------------------------------------- |
| Dimensions | 65 (width) × 65 (depth) × 60 (height) mm |

## **Getting Started** <a href="#block-382d4c79856d80338e29eda49912d74a" id="block-382d4c79856d80338e29eda49912d74a"></a>

### **External Power Supply** <a href="#block-382d4c79856d80f0908af0a85853d07f" id="block-382d4c79856d80f0908af0a85853d07f"></a>

The working voltage range of Livox Mid-360 is from 9 V to 27 V, the recommended working voltage is 12 V. The minimum working voltage should be increased in a low-temperature environment. When the Mid-360 is connected to an external power source directly using the M12 aviation connector, make sure the output voltage range of the external power source is within the operating voltage range of the Mid-360. When an extension cable is required, make sure to increase the output voltage of the external power source due to the extra voltage reduction. Make sure the maximum voltage does not exceed 27 V. Note that the power cable may generate voltage fluctuation where the voltage exceeds 27 V in some scenarios, such as if the power cable is interfered with or other devices connected to another power source in the parallel circuit suddenly power off. In such scenarios, the Mid-360 may not work normally or even be damaged.

The Mid-360 has a working power of 6.5 W when working normally. When in an environment where the temperature is less than 35°C (95°F), the startup power is 18 W (which lasts for about 8 seconds); when in an environment where the temperature is higher than 35°C (95°F), the startup power is 9 W (which lasts for about 8 seconds). When in an environment where the temperature is -20° to 0°C (-4° to 32°F), Livox Mid-360 will first enter self-heating mode automatically. In self-heating mode, the working power of the Mid-360 can reach 14 W, which lasts at most 10 minutes. The working power of the Mid-360 varies at different temperatures. Make sure the power supply is suitable based on the working voltage range and the startup peak power of Livox Mid-360. The value is for reference only. In normal conditions, the startup peak power varies depending on each sensor.

### **Connection** <a href="#block-382d4c79856d80c1bce1f07e23cd172b" id="block-382d4c79856d80c1bce1f07e23cd172b"></a>

Livox Mid-360 uses a M12 aviation connector for power supply as well as data transmission. Refer to the Connectors section for more information about the connector. It is recommended to use the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) when testing or using the Mid-360 temporarily. The Livox Aviation Connector 1-to-3 Splitter Cable contains the M12 aviation connector (female), power cable (bare wires), function cable (wires with insulation), and Ethernet cable (with RJ-45 connector).

Livox Mid-360 transfers data using the User Datagram Protocol (UDP). It supports the static IP address configuration. All Livox Mid-360 LiDAR sensors are set to static IP address mode by default with an IP address of 192.168.1.1XX (XX stands for the last two digits of the Livox Mid-360 LiDAR sensor's serial number). The default subnet masks of the Livox Mid-360 LiDAR sensors are all 255.255.255.0 and their default gateways are 192.168.1.1. Directly connect the Mid-360 to a computer when using for the first time.

1. Before connecting, set the IP address of the computer to static IP address mode. Follow the steps to set the IP address of the computer to a static IP address:

**Windows system**

1. Click to enter the Network and Sharing Center under Control Panel.
2. Select the network you are using and then click Properties.
3. Double click Internet Protocol Version 4 (TCP/IPv4).
4. Set the static IP address of the computer to 192.168.1.50,the subnet mask is set at 255.255.255.0.Click OK to complete.

**Ubuntu-18.04 system**

The IP address of the computer can be configured by using the ifconfig command at the terminal. The configuration code is as below:

\~$ sudo ifconfig enp4s0 192.168.1.50 (replace "enp4s0" with the network port name of the computer)

2. Connect the Mid-360 as shown below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e2c852a6-c3af-46bf-9781-6e7ae6aa70f2/image/w=1920,quality=90,fit=scale-down" alt="Connecting using the static IP address" height="130.58609683183874" width="612.9750366210938">

Connecting using the static IP address

1. Connect the M12 aviation connector (female) on the Livox Aviation Connector 1-to-3 Splitter Cable with the M12 aviation connector (male) on Livox Mid-360. The lock nut of the M12 aviation connector (female) should be tightened with a wrench to ensure there is a secure connection with the M12 aviation connector (male). Make sure there is no gap between them.
2. Connect the RJ-45 network connector on the Livox Aviation Connector 1-to-3 Splitter Cable to the computer.
3. If GPS time synchronization is required, connect the function cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the corresponding synchronization source.
4. Connect the power cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the external power source. Pay attention to the input voltage range and polarity.

💡

**Note:**

* When connecting the power cable and the function cable, pay attention to their respective voltage ranges and polarities. DO NOT connect any PoE device to the RJ-45 network connector. Incorrect connection can lead to irreversible damage to the LiDAR.
* Connect the function cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the corresponding synchronization source if needed.
* When multiple Mid-360 LiDAR sensors are connected to one computer in static IP address mode, make sure all sensors connected have different static IP addresses, and they are connected to the computer using a switch.
* If more than three Mid-360 LiDAR sensors are required, use a gigabit router or switch.
* The broadcast number for each LiDAR sensor can be viewed using the QR code sticker on the back of the LiDAR sensor or in the Device Manager of Livox Viewer 2.
* Launch Livox Viewer 2 on the computer after the Mid-360 is connected. Click the device with the static IP address that should be altered. Click to open the settings page and set the static IP address of the Mid-360.

## **Usage** <a href="#block-387d4c79856d80259332e2eb7d7c9dad" id="block-387d4c79856d80259332e2eb7d7c9dad"></a>

### **Coordinates** <a href="#block-387d4c79856d80e3ad28cf496640103e" id="block-387d4c79856d80e3ad28cf496640103e"></a>

The Cartesian coordinates O-XYZ of Mid-360 is defined as below: Point O is the origin, and O-XYZ is the point cloud coordinates of Mid-360.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a3fa7af2-57e9-4217-97bd-c3decd9c6072/image/w=1920,quality=90,fit=scale-down" alt="Mid-360 Coordinates" height="215.6080438418705" width="540.9625244140625">

Mid-360 Coordinates

### **Output Data** <a href="#block-387d4c79856d805e9419f5440c90137f" id="block-387d4c79856d805e9419f5440c90137f"></a>

The output information of Mid-360 LiDAR sensors includes: Information Push, Point Cloud Data and IMU Data.

For detailed output information formats, refer to the communication protocol section of Livox Wiki: https://livox-wiki-en.readthedocs.io

**Information Push**

After power-on, Livox Mid-360 periodically pushes LiDAR sensor information to the set IP address (the broadcast address by default), including device information, user configuration and current status. Below is part of the pushed information.

| **Type**           | **Content**                       | **Description**                                                                                                                                      |
| ------------------ | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Device Information | Serial Number                     | The only identification number for Livox Mid-360.                                                                                                    |
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

**Point Cloud Data**

Normally, Livox Mid-360 starts to output point cloud data after power-on. The point cloud data includes **target reflectivity, coordinates, tags, and timestamp.**

A point cloud is the collection of the points where the surface of an object was detected in the FOV of the LiDAR sensor. Each point contains the following information.

**Target reflectivity:** expressed by a number from 0 to 255. 0 to 150 corresponds to the reflectivity within the range of 0 to 100% in the Lambertian reflection model. 151 to 255 corresponds to the reflectivity of target objects with retroflection properties. When the target is less than 2m from the Mid-360, it may result in a large reflectivity error. The data should only be used to distinguish whether the target is total reflective or diffuse reflective.

**Coordinates:** The coordinates of Livox Mid-360 can be expressed in Cartesian coordinates (x, y, z) or in Spherical coordinates (r, θ, φ). The relation between the two coordinate systems are as shown below. When there is no object within the detection range or the object is placed beyond the detection range (such as further than 100m), the coordinates of the point cloud will be expressed as (0, 0, 0) in Cartesian coordinates, and as (0, θ, φ) in Spherical coordinates.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1f506c4d-74c2-46f8-a931-6c1fe5136f61/image/w=1920,quality=90,fit=scale-down" alt="image" height="240.2563422353644" width="439.9875183105469">

**Tags:** Indicates additional information about the detected points. Point cloud tags are 8-bit unsigned integers, which are divided into several groups. Each group indicates one property of the detected point, including rain, fog, dust, and dragging noise between objects, etc. The confidence level indicates the credibility of the detected points. "0" stands for normal point cloud data (high confidence level); low confidence level indicates that the detected point is highly affected by the corresponding type of noise, and as a result the detection result has low credibility. Filter the point cloud based on the tag information.

The format of the tag is as shown below:

| **Bit\[7-6]** | **Bit\[5-4]**                                                                                                                             | **Bit\[3-2]**                                                                                                                                                                       | **Bit\[1-0]**                                                                                                                                                       |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Reserved      | Detected points property: Other 0: High confidence level (normal points) 1: Moderate confidence level 2: Low confidence level 3: Reserved | Detected points property: Atmospheric particles like rain, fog, and dust. 0: High confidence level (normal points) 1: Moderate confidence level 2: Low confidence level 3: Reserved | Detected points property: Dragging noise between objects. 0: High confidence level (normal points) 1: Moderate confidence level 2: Low confidence level 3: Reserved |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |
|               |                                                                                                                                           |                                                                                                                                                                                     |                                                                                                                                                                     |

**Timestamp**

There are two ways to synchronize data with the Mid-360: IEEE 1588-2008 and GPS. Timestamps are displayed in format of 64-bit integers, and the unit is ns. Visit Livox Wiki for more detailed information about time synchronization: https://livox-wiki-en.readthedocs.io.

IEEE 1588-2008: IEEE 1588-2008 is the Precision Time Protocol (PTP) enabling precise synchronization of clocks in measurement and control systems by Ethernet. Livox LiDAR sensors, as the ordinary clock in the PTP, only supports UDP/IPV4 for PTP. Livox LiDAR sensors support the following message events: Sync, Follow\_up, Delay\_req, and Delay\_resp. GPS: GPS is a way to synchronize the data using the PPS signal and GPS message events. PPS port logic is the same as the PPS synchronization mentioned above. GPS messages (GPRMC) are sent to the corresponding pins through the serial port (see the Connectors section in this user manual). The pulse interval in PPS signal is 1 s (t0=1000 ms) while the continuous time of high-level voltage is t1 (t1 > 1 us). Besides sending GPS messages through serial port, users can also send the timestamp information of each pulse to Livox Mid-360 in network packets. For specific communication commands, refer to the communication protocol section.

**IMU Data**

The LiDAR sensor is integrated with a IMU chip (with a 3-axis accelerometer and a 3-axis gyroscope). By default, Livox Mid-360 starts to push IMU data at a frequency of 200 Hz after power-on, which can be enabled or disabled using the host computer. The IMU data contains the 3-axis acceleration and 3-axis angular velocity, the directions of which are the same with that of the point cloud coordinates. The position of the IMU chip in the point cloud coordinates is x = 11.0 mm, y = 23.29 mm, z = -44.12 mm. Refer to the communication protocol section for specific communication protocol and data formats.

Refer to the communication protocol section for specific communication protocol and data formats.

### **Working States and Working Modes** <a href="#block-387d4c79856d80328babed56cfb1c5ca" id="block-387d4c79856d80328babed56cfb1c5ca"></a>

The working state of Livox Mid-360 refer to the current working state of the LiDAR sensor, while the working mode refers to the target working mode selected by the user.

**Working States Descriptions**

The working states of Livox Mid-360 include idle, ready, and sampling, etc. Refer to table below for details.

| **Working States** | **Description**                                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------ |
| Sampling           | The LiDAR sensor is powered on and working normally (emitting laser beams).                                        |
| Idle               | All components are powered off apart from the communication module. The lowest power consumption is in this state. |
| Error              | The LiDAR sensor will enter error status when an error is detected.                                                |
| Self-check         | The LiDAR sensor is conducting the power-on self-check.                                                            |
| Motor Startup      | The motor of the LiDAR sensor is starting.                                                                         |
| Upgrading          | The LiDAR sensor is updating the firmware.                                                                         |
| Ready              | The LiDAR sensor is powered on and ready to emit laser beams.                                                      |

**Working Modes Descriptions**

The working modes refer to the target working modes selected by the user. Livox Mid-360 has three working modes: idle, ready, and sampling. Users can select different working modes using Livox Viewer 2 or Livox SDK 2.

### **Livox Viewer 2** <a href="#block-387d4c79856d8073a39ce05e498d42a1" id="block-387d4c79856d8073a39ce05e498d42a1"></a>

Livox Viewer 2 is software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos, and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

Visit [www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer 2. It supports Windows® 10 (64 bit) and Ubuntu™ 18.04 (64 bit). Follow the steps below to use Livox Viewer 2.

💡

For Windows users, Livox Viewer 2 may fail to detect LiDAR sensors if Windows Firewall is turned on. In this situation, go to the Control Panel to turn off Windows Firewall and restart Livox Viewer 2.

**Windows Users:** unzip the downloaded file and click to open the .exe file named "Livox Viewer 2".

**Ubuntu Users**: unzip the downloaded file, and run the command "/livox\_viewer\_2.sh" file in the root directory of the unzipped folder.

For more information, download the Livox Viewer 2 User Manual from the official website: [https://www.livoxtech.com](https://www.livoxtech.com/).

### **Software Development Kit (SDK)** <a href="#block-387d4c79856d8001b29be1f70aad43fb" id="block-387d4c79856d8001b29be1f70aad43fb"></a>

**Livox SDK 2**

Besides using Livox Viewer 2 to check real-time point cloud data, users can also use the Livox SDK 2 to apply the point cloud acquired from Livox LiDAR sensors to different scenarios, such as:

* Configure the LiDAR Sensor: configure the parameters of the LiDAR sensor and check the status.
* Get Point Cloud Data: get the point cloud coordinates from the LiDAR sensor.
* Firmware Update: conduct firmware update of the LiDAR sensor.

Visit [https://github.com/Livox-SDK/Livox-SDK2](https://github.com/Livox-SDK/Livox-SDK2) to see more detailed information about Livox SDK 2 API documentation. **SDK Communication Protocol**

Both Livox Viewer 2 and Livox SDK 2 communicate with LiDAR sensors using the SDK communication protocol. Users can also develop their own software based on the SDK communication protocol to realize communication with and controlling the LiDAR sensor, and collecting the point cloud coordinates.

Visit [https://livox-wiki-en.readthedocs.io](https://livox-wiki-en.readthedocs.io/) to learn more information about SDK communication protocol.

## Storage, Transportation, and Maintenance <a href="#block-387d4c79856d80859863dcd937f0f8a2" id="block-387d4c79856d80859863dcd937f0f8a2"></a>

### **Storage** <a href="#block-387d4c79856d80e3886ecb10cccc98b0" id="block-387d4c79856d80e3886ecb10cccc98b0"></a>

The storage temperature for the Mid-360 is from -40° to 70° C (-40° to 158° F). Keep Mid-360 LiDAR sensors in a dry and dust-free environment.

* Make sure the Mid-360 LiDAR sensor is not exposed to environments containing poisonous or corrosive gases or materials.
* DO NOT drop the Mid-360 LiDAR sensor and be careful when placing it in storage or taking it out of storage.
* If a Mid-360 LiDAR sensor is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

### **Transportation** <a href="#block-387d4c79856d8092bbccf32ddf4af603" id="block-387d4c79856d8092bbccf32ddf4af603"></a>

* Before transportation, place Mid-360 LiDAR sensor in a suitable box and make sure it is secure.
* Make sure to place foam inside the transportation box and that the box is clean and dry.
* Always handle with care during transportation. Protect it from any impact, bumps, and never drop it to the ground.

### **Maintenance** <a href="#block-387d4c79856d80748ecbcec448e71314" id="block-387d4c79856d80748ecbcec448e71314"></a>

With full consideration for the requirements of reliability and stability during design, Livox Mid-360 features advanced optical, mechanical, and electrical performance. In normal conditions, the only maintenance required for the Mid-360 is to clean the optical window of the LiDAR sensor. Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor. Make sure to regularly clean the optical window to prevent this from happening.

Check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. Use compressed or canned air:

DO NOT directly wipe a dusty optical window as it will only cause more damage. Clean the optical window with compressed or canned air before wiping the optical window.

💡

If the optical window has no visible stains afterwards, it is unnecessary to wipe it.

2. Wipe the stains:

It is recommended to use a clean and dry lens tissue to gently wipe the optical window. If the optical window is still dirty, use the lens tissue provided with a small amount of isopropyl alcohol and wipe slowly to remove the dirt.

## **Troubleshooting** <a href="#block-387d4c79856d8012acebc3df545f6bd1" id="block-387d4c79856d8012acebc3df545f6bd1"></a>

The table below shows you how to troubleshoot and resolve common issues with Mid-360 LiDAR sensors. If the issue persists, contact Livox.

| **Issue**                                                           | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cannot detect the LiDAR sensor                                      | • Make sure that all cables are correctly wired. • Make sure the voltage of the power supply is suitable. The voltage should be between 9 V and 27 V. If connected with the Livox Aviation Connector 1-to-3 Splitter Cable, the voltage range of the supported external power source is from 9 V to 27 V. • Make sure that the LiDAR sensor is not connected to other software. • Make sure that the LiDAR sensor and the host computer is connected to the same LAN. • Make sure no security software is installed that would block Ethernet broadcasts. If the issue persists, turn off all firewalls, restart the Livox Viewer 2 and try again. Confirm the packet outputs of all connected devices using another application (e.g., Wireshark). |
| Cannot connect to the detected LiDAR sensor / Cannot start sampling | • Make sure that all cables are correctly wired. • Make sure the voltage is correct. The working voltage range for Livox Mid-360 is from 9 V to 27 V. If connected with the Livox Aviation Connector 1-to-3 Splitter Cable, the voltage range of the supported external power source is from 9 V to 27 V. If the issue persists, reboot the LiDAR sensor and restart the Livox Viewer 2.                                                                                                                                                                                                                                                                                                                                                            |
| No data received                                                    | Confirm the packet outputs for all connected devices using another application (e.g., Wireshark).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

## **After-Sales Information** <a href="#block-387d4c79856d80b0aca0f63f51dc2bf9" id="block-387d4c79856d80b0aca0f63f51dc2bf9"></a>

Visit [www.livoxtech.com/support](http://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox LiDAR sensors.

## Appendix <a href="#block-387d4c79856d80439d08c10d925fd372" id="block-387d4c79856d80439d08c10d925fd372"></a>

### Livox Mid-360 Dimensions <a href="#block-387d4c79856d80fcbccdd94cd757a59b" id="block-387d4c79856d80fcbccdd94cd757a59b"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1f7c2f15-f957-437f-9111-108550c987d6/image/w=1920,quality=90,fit=scale-down" alt="image" height="502.90014684287814" width="665">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ed129ead-9cd0-4f67-ab97-0f9cc8924005/image/w=1920,quality=90,fit=scale-down" alt="image" height="325.7193917139179" width="561.9874877929688">

## Specifications <a href="#block-387d4c79856d804b9b36f68cfa788bb9" id="block-387d4c79856d804b9b36f68cfa788bb9"></a>

| **Livox Mid-360**                |                                                 |
| -------------------------------- | ----------------------------------------------- |
| Model                            | MID-360                                         |
| Laser Wavelength                 | 905 nm                                          |
| Laser Safety\[1]                 | Class 1 (IEC 60825-1:2014) (safe for eyes)      |
| Detection Range (@ 100 klx)      | 40 m @ 10% reflectivity 70 m @ 80% reflectivity |
| Close Proximity Blind Zone\[2]   | 0.1 m                                           |
| FOV                              | Horizontal: 360°, Vertical: -7° \~ 52°          |
| Distance Random Error (1σ)\[3]   | ≤ 2 cm (@10 m)\[4] ≤ 3 cm (@0.2 m)\[5]          |
| Angular Random Error (1σ)        | ≤ 0.15°                                         |
| Point Rate                       | 200,000 points/s                                |
| Frame Rate                       | 10 Hz (typical value)                           |
| Data Port                        | 100 BASE-TX Ethernet                            |
| Data Synchronization             | IEEE 1588-2008 (PTP v2), GPS                    |
| Anti-Interference Function       | Available                                       |
| False Alarm Ratio (@100 klx)\[6] | < 0.01%                                         |
| IMU                              | Built-in IMU Model: ICM40609                    |
| Operating Temperature            | -20° to 55° C (-4° to 131° F)\[7]               |
| Storage Temperature              | -40° to 70° C (-40° to 158° F)                  |
| IP Rating                        | IP67                                            |
| Power\[8]                        | 6.5 W (environment temperature 25° C (77° F))   |
| Power Supply Voltage Range       | 9-27 V DC                                       |
| Dimensions                       | 65 (width) × 65 (depth) × 60 (height) mm        |
| Weight                           | Approx. 265 g                                   |

\[1] The divergence of the embedded laser is 25.2° (horizontal) × 8° (vertical), which was measured at full width at half maximum. The maximum power of the embedded laser may exceed 70 W. In order to avoid being injured by the laser, DO NOT disassemble Livox Mid-360. \[2] Target objects within 0.1 to 0.2 m from Mid-360 can be detected and point cloud data can be recorded. However, since the detection precision cannot be guaranteed, the data should be taken as a reference only. \[3] To detect objects having different reflectivities within the detection range, the accuracy of point cloud data of very few positions might decrease slightly. \[4] Tested in an environment at a temperature of 25° C (77° F) with a target object that has a reflectivity of 80% and is 10 meters away from Livox Mid-360. \[5] Tested in an environment at a temperature of 25° C (77° F) with a target object that has a reflectivity of 80% and is 0.2 meters away from Livox Mid-360. For target objects within 0.1 to 1 m away from the Mid-360, if they have a low reflectivity or are thin and tiny, the detection effect cannot be guaranteed. These objects include but are not limited to black foam and the surface of water or objects that have been polished, have a matte finish, thin lines, etc. \[6] The false alarm ratio of the noise created by the stray light in a test environment of 100 kx at a temperature of 25°C (77°F). \[7] The performance of Livox Mid-360 might slightly decrease in high-temperature or low-temperature environments, or environments with strong vibrations or heavy fog, etc. Besides, operating at a high temperature for an extended period of time may negatively affect performance and may lead to permanent damage to the product. It is recommended to apply extra heat dissipation measures. A high temperature will trigger the high-temperature protection mechanism, and Livox Mid-360 will issue a high-temperature warning. Livox Mid-360 will stop operating automatically if the temperature is too high. When the Livox Mid-360 logo faces the user, make sure the temperature of the following locations does not exceed 75°C (167°F): a. The center of the bottom of Livox Mid-360. b. The highest point of the sloped surface in the left heatsink center groove. \[8] When the ambient temperature is from -20°C (-4°F) to 0°C (32°F), Livox Mid-360 will automatically enter self-heating mode, where the peak power may reach 14 W. Make sure to design the power supply reasonably to ensure the LiDAR sensor works normally.

<br>
