# LIVOX MID-70 User Manual

> LIVOX MID-70 User Manual

{% embed url="https://openelab.io/products/livox-mid-70-compact-lidar3d" %}

## **Product Profile** <a href="#block-390d4c79856d804dab71cb6d43c8d06e" id="block-390d4c79856d804dab71cb6d43c8d06e"></a>

### **Introduction** <a href="#block-390d4c79856d80dbba94dbde32aaaaad" id="block-390d4c79856d80dbba94dbde32aaaaad"></a>

The Livox Mid-70 is a high-performance LiDAR sensor that can be used for multiple applications including autonomous driving, industrial robots, indoor and outdoor service robots, or any robots used in special applications. Specifically, the Mid-70 can be used with automated guided vehicles (AGV), autonomous mobile robots (AMR), automated trucks, medical logistics robots, cleaning robots, terminal delivery robots, and intelligent security robots. The Livox Mid-70 can detect objects as close as 0.05 meters away, and has a detection range of up to 260 meters.

**Wide FOV:** Compared with Mid-40, the Mid-70 has a larger circular field of view (FOV) of 70.4°, increasing its ability to detect both near and distant objects.

**Small Blind Zone:** The blind zone of the Mid-70 is 5 cm, and the detection precision from 0.2 to 1m is 3cm. Users can adjust the Mid-70 angle to completely eliminate the blind zone. It is recommended to embed the Mid-70 in an automotive device before adjusting the angle.

**Non-Repetitive Scanning Technology:** Livox's unique non-repetitive scanning technology ensures a high-density point cloud, and can precisely detect every detail inside the FOV.

**High Reliability:** The Mid-70 offers enhanced reliability as the cutting-edge optoelectronic system design works normally without rotating internal electronic devices such as a transmitter and receiver. The Mid-70 has undergone rigorous reliability testing required by the automotive industry. In addition, the Mid-70 has achieved an IP67 waterproof and dustproof rating under GB 4208-2008 and IEC 60529 standards. Note the included cables and mounting bracket do not meet the same standards.

**User-Friendly Livox Viewer:** Livox Viewer is a software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos, and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer. The simple interface makes Livox Viewer easy to use.

**Open Source Livox SDK:** a software development kit (SDK) is provided to help develop customizable applications using the data acquired from the point cloud data. Livox SDK supports Windows/Linux/Mac OS/ROS.

💡

**Note:**

* The Mid-70 has a detection range of up to 260m, which can be reached when the target object reflects 80% or more of light. For reference, grey concrete walls and roads have a reflectivity range from 15% to 30%, while white plaster walls have a reflectivity range from 90% to 99% in an environment with a temperature of 25° C (77° F).
* Before using for the first time, remove the screen protector from the optical window.

### **Product Characteristics** <a href="#block-390d4c79856d805fbd76c8a1229f2cff" id="block-390d4c79856d805fbd76c8a1229f2cff"></a>

The Livox Mid-70 has a high coverage ratio due to its unique non-repetitive scanning technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surroundings.

Figure 1.2.1 displays the typical point cloud patterns of the Livox Mid-70 over an extended period.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e5baec3e-23f7-4c75-ba9b-103c70157f0f/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.1 Point cloud patterns of the Livox Mid-70 accumulated over an extended period" height="164.9979674796748" width="724.8125">

Figure 1.2.1 Point cloud patterns of the Livox Mid-70 accumulated over an extended period

Figure 1.2.2 displays the FOV coverage of Mid-70 compared with traditional mechanical LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is 0.2 seconds, the FOV coverage of the Livox Mid-70 is similar to a 32-line LiDAR sensor. As the integration time increases, however, the FOV coverage of the Livox Mid-70 increases significantly. After 1.5 seconds, the FOV coverage approaches 86%, so almost all areas would be illuminated by laser beams. In this way, more details in the FOV can be revealed.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bac588c4-ae01-4813-b7a4-760bf05765e4/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.2 The FOV coverage of the Mid-70 and non-Livox LiDAR sensors using common mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°." height="437.3325652395988" width="656.9750366210938">

Figure 1.2.2 The FOV coverage of the Mid-70 and non-Livox LiDAR sensors using common mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.💡

The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams. The FOV coverage (C) can be calculated with the following formula:

C=TotalareailluminatedbylaserbeamsTotalareainFOV∗100%C=TotalareainFOVTotalareailluminatedbylaserbeams​∗100%

Refer to the official Livox website for more information about how the FOV coverage is calculated.

Table 1.2.1 Point cloud specifications

| Laser Wavelength             | 905 nm                                                                      |
| ---------------------------- | --------------------------------------------------------------------------- |
| Laser Safety                 | Class 1 (IEC 60825-1:2014) (Safe for eyes)                                  |
| Detection Range (@ 100 klx)  | 90 m @ 10% reflectivity; 130 m @ 20% reflectivity; 260 m @ 80% reflectivity |
| Close Proximity Blind Zone   | 0.05 m                                                                      |
| FOV                          | 70.4° (circular)                                                            |
| Distance Random Error        | 1σ (@ 20 m) ≤ 2 cm 1σ (@ 0.2–1 m) ≤ 3 cm                                    |
| Angular Random Error         | 1σ < 0.1°                                                                   |
| Beam Divergence              | 0.28° (Vertical) × 0.03° (Horizontal)                                       |
| Point Rate                   | 100,000 points/s (first or strongest return) 200,000 points/s (dual return) |
| False Alarm Ratio (@100 klx) | < 0.01%                                                                     |

💡

**Note:**

* Close Proximity Blind Zone: Target objects within 0.05 to 0.2 m from the Mid-70 can be detected and point cloud data can be recorded. However, since the detection precision cannot be guaranteed, the data should be taken as a reference only.
* Tested in an environment at a temperature of 25°C (77°F) with a target object that has a reflectivity of 30% and is 20 meters away from the Livox Mid-70. The actual environment may differ from the testing environment. The figure listed is for reference only.
* Tested in an environment at a temperature of 25°C (77°F) with a target object that has a reflectivity of 30% and is within the range of 0.2 to 1 meters from the Livox Mid-70. The actual environment may differ from the testing environment. The figure listed is for reference only.
* The performance may decrease in extreme environments such as those with foggy weather, that cause strong vibration, or where the temperature is -20°C (-4°F) or 65°C (149°F).

### Overview <a href="#block-390d4c79856d80a7a761f6163c79c8f9" id="block-390d4c79856d80a7a761f6163c79c8f9"></a>

**Livox Mid-70**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e2478ffb-2ca6-4408-bf3d-83d032dcf37a/image/w=1920,quality=90,fit=scale-down" alt="image" height="260.25880555270015" width="724.8250122070312">

1. **Optical Window**

The laser passes through the optical window and scans objects in the FOV.

2. **M3 Mounting Holes**

Make sure to use the correct screws when mounting.

3. **Locating Hole**

The locating hole makes it easy for users to find the correct location to mount a fixed support for the Mid-70. Refer to the Dimensions section for more information.

4. **M12 Aviation Connector**

Used with the conversion cable, the M12 aviation connector connects to the Livox Converter 2.0 to implement a quick performance test of the Mid-70.

Used with the conversion cable, the M12 aviation connector connects to the Livox Converter 2.0 to carry out a quick performance test of the Mid-70. If users wish to improve the waterproof and dustproof protection of their system, they can replace the conversion cable with a cable of their own. Refer to the Cables section for more information.

5. **Conversion Cable**

The Livox Mid-70 includes a conversion cable. To connect the Livox Mid-70 to the Livox Converter 2.0, users can use this cable or a cable of their own. Refer to the Cables section for more information.

**Livox Converter 2.0**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/77355b65-f41a-4c6f-aaae-ea6efdc1666a/image/w=1920,quality=90,fit=scale-down" alt="image" height="233.81048387096774" width="724.8125">

1. **LiDAR Connector Port**
2. A JAE MX34012NF1 type connector port is used to connect to the Mid-70. The mating connector is JAE MX34012SF1 LiDAR.
3. **Power Port**
4. Connects to an external power supply.When the Mid-70 is connected to the Livox Convertor 2.0, users can use a power supply of 9 to 30 V. The connector type is MOLEX 1053313-1102. The mating connector is MOLEX 105307-1202.
5. **Ethernet Port**
6. An RJ45 type Ethernet connector is used to connect to Ethernet cables.
7. **Sync Port**
8. The 3-pin sync port supports 3.3V LVTTL sync signal input. Refer to Table 2.2.2 for more information. The mating connector of the sync port connector is Famfull 9.510AO-003-1RO. JST GHR-03V-S is also compatible.

## **Connectors** <a href="#block-390d4c79856d809c84e9cd7901e5a607" id="block-390d4c79856d809c84e9cd7901e5a607"></a>

### **M12 Aviation Connector** <a href="#block-390d4c79856d80de9e23d54cc60033f2" id="block-390d4c79856d80de9e23d54cc60033f2"></a>

The Mid-70 uses the high-reliability M12 aviation connector (male). It is a M12 12P A-code fully shielded male connector that meets the IEC61076-2-101 standard. The connector type is Finecables MA12MAHD12STXXXB14 and its mating connector is Finecables MA12FAHD12STXXXB14, both of which meet the IP rating of IP67. When the M12 aviation connector is used with the conversion cable, users can connect the Mid-70 to the Livox Connector 2.0 for connecting power and transmitting control signals and data. If users wish to improve the waterproof and dustproof protection of their system, they can replace the conversion cable with a cable of their own.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d5165d30-9b31-4fba-ba71-f19ad7bd15e7/image/w=1920,quality=90,fit=scale-down" alt="image" height="255.23342226089972" width="603.9874877929688">

**Conversion Cable**

To connect the Mid-70 to the Livox Converter 2.0, users can use this cable or a cable of their own.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3d6a8546-b868-4beb-bf75-dbfee343c35d/image/w=1920,quality=90,fit=scale-down" alt="Figure 2.1.1 Conversion Cable" height="175.81053206980158" width="724.7875366210938">

Figure 2.1.1 Conversion Cable

Below is more information on the Livox Mid-70 M12 aviation connector and the aviation and converter connector cable.

Table 2.1.1 Conversion Cable description

| **LiDAR Connector Pin** | **M12 Aviation Connector Pin** | **Signal**   | **Type** | **Description**            | **Color**           |
| ----------------------- | ------------------------------ | ------------ | -------- | -------------------------- | ------------------- |
| 1                       | 1                              | Power+       | Power    | DC10V-15V                  | Blue/white          |
| 7                       | 9                              | Power+       | Power    | DC10V-15V                  | Blue                |
| 2                       | 2                              | Ground       | Power    | Ground                     | Silver bare wire    |
| 8                       | 3                              | Ground       | Power    | Ground                     | Silver bare wire    |
| 3                       | 4                              | Ethernet-TX+ | Output   | 100BASE-TX, TX+            | Orange/white        |
| 4                       | 5                              | Ethernet-TX- | Output   | 100BASE-TX, TX-            | Orange              |
| 9                       | 6                              | Ethernet-RX+ | Input    | 100BASE-TX, RX+            | Green/white         |
| 10                      | 7                              | Ethernet-RX- | Input    | 100BASE-TX, RX-            | Green               |
| 5                       | 8                              | Ground       | Power    | Ground                     | Silver braided wire |
| 11                      | 10                             | Ground       | Power    | Ground                     | Silver braided wire |
| 12                      | 11                             | Sync-        | Input    | RS485\_B, Pulse Per Second | Grey                |
| 6                       | 12                             | Sync+        | Input    | RS485\_A, Pulse Per Second | Grey/white          |

### **Power Cable and Sync Cable** <a href="#block-390d4c79856d80e893ccdcd3baabc1c4" id="block-390d4c79856d80e893ccdcd3baabc1c4"></a>

The Mid-70 cables package includes a power cable and sync cable.

**Power Cable**

Power CableConnect "A" to the power port of the Livox Converter 2.0 and connect "B" to an external DC power supply. The connector type of this power cable is MOLEX 105307-1202.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e1f0dbe8-304c-4352-baa4-20254757b16d/image/w=1920,quality=90,fit=scale-down" alt="Figure 2.2.1 Power cable" height="127.84851362335014" width="724.7750244140625">

Figure 2.2.1 Power cable

Table 2.2.1 Power cable description

| **Pin** | **Signal** | **Type** | **Description**         | **Color** |
| ------- | ---------- | -------- | ----------------------- | --------- |
| 1       | Power+     | Power    | DC 10 - 30 V (max 30 V) | Red       |
| 2       | Ground     | Power    | Ground                  | Black     |

**Sync Cable**

Connect "A" into the sync port of the Livox Converter 2.0 and connect "B" to the sync signal. The sync cable has a 3-pin connector. The connector type is Famfull 9.510A0-003-1R0, which is compatible with JST GHR03V-S type connectors. Refer to the Data Synchronization section for more information.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fd1a9c6d-c889-49f4-b65d-f2a52685a9ff/image/w=1920,quality=90,fit=scale-down" alt="Figure 2.2.2 Sync cable" height="125.9613991803664" width="724.7625122070312">

Figure 2.2.2 Sync cable

Table 2.2.2 Sync cable description

| **Pin** | **Signal** | **Type** | **Description**               | **Color** |
| ------- | ---------- | -------- | ----------------------------- | --------- |
| 1       | Ground     | Power    | Ground                        | Black     |
| 2       | Sync+      | Input    | 3.3 V LVTTL, Pulse Per Second | Blue      |
| 3       | Reserved   | Reserved | Undefined                     | White     |

### **Ethernet Port** <a href="#block-390d4c79856d803d9d61d622507e8404" id="block-390d4c79856d803d9d61d622507e8404"></a>

The Livox Converter 2.0 supports a 100BASE-TX standard RJ45 Ethernet port. The Mid-70 uses two twisted pairs to send and receive data.

## **Mounting the Livox Mid-70** <a href="#block-390d4c79856d8044855ff61da7076df3" id="block-390d4c79856d8044855ff61da7076df3"></a>

### **Effective Field of View (FOV) Range** <a href="#block-390d4c79856d80ad97a1dd44edce55f1" id="block-390d4c79856d80ad97a1dd44edce55f1"></a>

As shown below, the Mid-70 has a circular FOV of 70.4°. When mounting a Livox LiDAR sensor, make sure that the FOV is not blocked by any objects. Go to [www.livoxtech.com/mid-70](http://www.livoxtech.com/mid-70) to download the 3D models of the Mid-70 and its FOV.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e2df122e-97d2-461f-97a1-0d2f78e12d50/image/w=1920,quality=90,fit=scale-down" alt="image" height="228.38730853391687" width="724.8125">

Note that the effective detection range of the Livox Mid-70 varies based on where the object is within the FOV. The closer to the edge of the FOV, the shorter the effective detection range is. The closer to the center of the FOV, the farther the effective detection range. Refer to the diagrams below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/95ea8bf4-026e-4e87-bf5c-b60edb0ba4f4/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.1.2 Effective FOV of the Mid-70" height="231.55935448577682" width="724.8125">

Figure 3.1.2 Effective FOV of the Mid-70

As shown above, when an object with a reflectivity of 10% is placed in the center of the FOV, the object can be detected as far as 90m. However, as the object moves towards the edge of the FOV, the distance at which it can be detected shortens accordingly. Pay attention to the effective detection range when the Mid-70 is in use.

### **Mounting Notice** <a href="#block-390d4c79856d80928b25c61125c2a084" id="block-390d4c79856d80928b25c61125c2a084"></a>

Read and understand the following warnings before mounting the Mid-70.

1. Before use, remove the screen protector from the optical window.
2. Significant dust and stains on the optical window will affect the performance of the Mid-70 sensor. Follow the instructions in the Maintenance section to clean the optical window using compressed air, isopropyl alcohol, or a lens cloth.
3. When mounting the Mid-70, the field of view must not be blocked by an object, including glass. Refer to Figure 3.1.1.
4. There are no restrictions on which direction the Mid-70 can be installed. The top or bottom surface can be used to mount the Mid-70. It is recommended that the surface is parallel to the ground when mounting.
5. The Mid-70 cannot bear any extra payload. Otherwise, the reliability of the product cannot be guaranteed.

### **Dimensions** <a href="#block-390d4c79856d806dafeece2b40cf8518" id="block-390d4c79856d806dafeece2b40cf8518"></a>

**Mounting the Mid-70 without Mounting Bracket**

The bottom surface of the Mid-70 has four M3 mounting holes with a depth of 5mm. Refer to the dimensions and the mounting holes in the diagrams below to mount or embed the Mid-70 to or in an appropriate place on the target base.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e36a4a1e-addd-497f-bcf4-f6209a8cbb2a/image/w=1920,quality=90,fit=scale-down" alt="image" height="205.10989899486663" width="724.8375244140625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/944aaadc-db37-4934-be8b-3c9ed79c6426/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.2.1 The Mid-70 Dimensions (refer to Appendix 1)" height="259.27373889970295" width="724.8250122070312">

Figure 3.2.1 The Mid-70 Dimensions (refer to Appendix 1)

Table 3.2.1 The Mid-70 Weight & Dimensions

| Weight (with cable) | Approx. 580 g |
| ------------------- | ------------- |
| Dimensions          | 97×64×62.7 mm |

**Mounting the Mid-70 with Mounting Bracket**

It is recommended to first attach the Mid-70 to the mounting bracket using the M3 mounting hole and then mount the Mid-70 using the M6 mounting hole on the mounting bracket. There is one 1/4 inch mounting hole available on the center of the mounting bracket to help mount the Mid-70 based on your requirements.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/89d91a32-05e0-4d8c-8d8f-f839303ce68d/image/w=1920,quality=90,fit=scale-down" alt="image" height="314.64684107313593" width="724.8250122070312">

Table 3.2.2 The Mounting Bracket Weight & Dimensions

| **Weight** | **Approx. 76 g** |
| ---------- | ---------------- |
| Dimensions | 100×97×5.7 mm    |

**Livox Converter 2.0**

Refer to the dimensions below to mount the Livox Converter 2.0.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f72185ad-d6d1-47f3-93b0-7ca35845b226/image/w=1920,quality=90,fit=scale-down" alt="image" height="203.57486186562147" width="724.8250122070312">

Table 3.2.3 Livox Converter 2.0 Weight & Dimensions

| **Weight** | **Approx. 88 g** |
| ---------- | ---------------- |
| Dimensions | 74×52×23 mm      |

## **Getting Started** <a href="#block-390d4c79856d800bba3fd882308d1418" id="block-390d4c79856d800bba3fd882308d1418"></a>

### **External Power Supply** <a href="#block-390d4c79856d802e8875d1b266414711" id="block-390d4c79856d802e8875d1b266414711"></a>

The working voltage range of the Mid-70 is from 10 to 15 V, with a recommended working voltage of 12 V. The minimum working voltage should be increased in a low-temperature environment. When the Mid-70 is connected to an external power source directly, make sure the output voltage range of the external power source is within the working voltage range of the Mid-70. When an extension cable is required, make sure to increase the output voltage of the external power source due to the extra voltage reduction. Make sure the maximum voltage does not exceed 15 V. Note that the power cable may generate voltage fluctuation where the voltage exceeds 15 V in some scenarios such as if the power cable is interfered with or other devices connected to another power source in the parallel circuit suddenly power off. In such scenarios, the Mid-70 may not work normally or even be damaged.

Normally, the working power of the Mid-70 is 8 W. In an environment where the temperature is from -20° to 0° C (-4° to 32° F), the Mid-70 will first enter self-heating mode automatically, which lasts at least three minutes. In self heating mode, the working power of the Mid-70 may reach up to 40 W. The working power of the Mid-70 varies at different temperature. Below shows the relationship between the temperature of the environment and the working power of the Mid-70. Make sure the power supply is suitable based on the peak power of the Livox Mid-70. The value is for reference only. In normal conditions, the peak power varies depending on each sensor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/be34d4d3-b64f-4430-becb-55c6b7590d16/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.1.1 The working power of the Mid-70 at varying temperatures" height="295.9845257234727" width="724.8125">

Figure 4.1.1 The working power of the Mid-70 at varying temperatures

### **Connection** <a href="#block-390d4c79856d80e5abfffadeb2324268" id="block-390d4c79856d80e5abfffadeb2324268"></a>

The Mid-70 uses M12 aviation connector for power supply as well as control signal and data transmission. Refer to the Cables section for more information about the connector. The Livox Converter 2.0 integrates a LiDAR port, a sync port, a power port, and an Ethernet port. For temporary use or to ensure optimal performance, it is recommended to always use a Livox Converter 2.0 and a conversion cable.

The Mid-70 uses an Ethernet cable for data transmission and supports user datagram protocol (UDP). Both static and dynamic IP address configurations are supported. All Mid-70 sensors are set to static IP address mode by default with an IP address of 192.168.1.1XX (XX stands for the last two digits on the serial number of the Mid-70 sensor). The default subnet masks of the Mid-70 sensors are all 255.255.255.0, and their default gateways are 192.168.1.1. Directly connect the Mid-70 to the computer when using for the first time.

The static and dynamic IP addresses are connected in different ways. 1. The static IP address is connected by default and in this mode, the Mid-70 can be connected to a computer directly. 2. To connect to the dynamic IP address, make sure the Mid-70 is switched to dynamic IP mode by using Livox Viewer or the Livox SDK. In dynamic address mode, the addresses are assigned to the Mid-70 using dynamic host configuration protocol (DHCP).

**Static IP address:**

1. Follow the steps to set the IP address of your computer to static IP address:

**Windows system**

1. Click to enter the Network and Sharing Center under Control Panel.
2. Click the network you are using and click "Properties".
3. Double click "Internet Protocol Version 4 (TCP/IPv4)".
4. Set the static IP address of the computer to 192.168.1.50 and the subnet mask to 255.255.255.0. Click "OK" to complete.

**Ubuntu-16.04 system**

The IP address of the computer can be configured by using ifconfig command at the terminal. The configuration code is as below:

Copy

```javascript
~$ sudo ifconfig enp4s0 192.168.1.50 
```

(replace "enp4s0" with the network port name of the computer)

2. Connect the Mid-70, Livox Converter 2.0, external power source, and computer by following Figure 4.2.1.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19cf8c6c-3472-4348-a2f2-c9eb79197874/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.2.1 Connecting using static IP address" height="311.02232336380627" width="724.8250122070312">

Figure 4.2.1 Connecting using static IP address

1. Connect the Mid-70 to the 1.5m aviation connector and converter connector cable. Next, connect the 1.5m cable to the Livox Converter 2.0.
2. Connect the computer and the Livox Converter 2.0 to the router using Ethernet cables. Make sure both the Livox Converter 2.0 and the computer are connected to the LAN port on the router.
3. Connect the Livox Converter 2.0 to an external power source.

💡

**Note:**

* If necessary, use the sync cable to connect with the sync port of Livox Converter 2.0 and sync source.
* If multiple Mid-70 sensors are set to static IP addresses, make sure all the Mid-70 sensors have different IP addresses and use a switchboard to connect them to the computer.
* If more than six Mid-70 sensors are required, use a kilomega router or switchboard.
* The broadcast number for each LiDAR sensor can be viewed in the Device Manager of Livox Viewer or the Livox SDK. For the Mid-70, the broadcast number will be its serial number ending in an additional "1".
* Launch Livox Viewer after the Mid-70 is connected. Click the device with the static IP address that should be altered. Click to open the settings page and set the static IP address of the Mid-70.

**Dynamic IP address:**

1. Follow Figure 4.2.1 to connect the Mid-70, conversion cable, Livox Converter 2.0, external power source, and computer.
2. Run Livox Viewer, click to open the settings page, and set the IP address of the Mid-70 to dynamic IP address.
3. Disconnect the Mid-70, conversion cable, Livox Converter 2.0, external power source, and computer.
4. Follow the steps to set the IP address of your computer to dynamic IP address:

**Windows system**

1. Click to enter the Network and Sharing Center under Control Panel.
2. Click the network you are using and click "Properties".
3. Double click "Internet Protocol Version 4 (TCP/IPv4)".
4. Select "Obtain an IP address automatically" and "Obtain DNS server address automatically", then click "OK" to complete.

**Ubuntu-16.04 system**

1. Click to open "Network".
2. Click "IPv4", and then click "Automatic (DHCP)". Click "Apply" to complete.
3. Connect the Mid-70, conversion cable, Livox Converter 2.0, router, computer, and external power supply by following Figure 4.2.2.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/de8f3eef-bd26-44ff-9ce6-3fcb5658f2aa/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.2.2 Connecting using dynamic IP address" height="221.5999962678282" width="724.7999877929688">

Figure 4.2.2 Connecting using dynamic IP address

1. Connect the Mid-70 to the 1.5m aviation connector and converter connector cable. Next, connect the 1.5m cable to the Livox Converter 2.0.
2. Connect the computer and the Livox Converter 2.0 using an Ethernet cable.
3. Connect the Livox Converter 2.0 to an external power source.

💡

* If necessary, use the sync cable to connect with the sync port of Livox Converter 2.0 and sync source.
* If more than six Mid-70 sensors are required, use a kilomega router or switchboard.
* The broadcast number for each LiDAR sensor can be viewed in the Device Manager of Livox Viewer or the Livox SDK. For the Mid-70, the broadcast number will be its serial number ending in an additional "1".

## **Usage** <a href="#block-390d4c79856d80318204c08fc21f2178" id="block-390d4c79856d80318204c08fc21f2178"></a>

### **Coordinates** <a href="#block-390d4c79856d80fcae4fda426fdc70f7" id="block-390d4c79856d80fcae4fda426fdc70f7"></a>

The Cartesian coordinates O-XYZ of Mid-70 is defined as below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c4a887fb-78fd-41e5-9bf0-d22d9284a74e/image/w=1920,quality=90,fit=scale-down" alt="image" height="206.6480188269785" width="724.7875366210938">

### **Output Data** <a href="#block-390d4c79856d807ab4a8ee096e963267" id="block-390d4c79856d807ab4a8ee096e963267"></a>

The output information of the Mid-70 sensors includes point cloud data, which have timestamp, status codes, target reflectivity, coordinates, and tag information.

**Point Cloud Data**

A point cloud is the collection of the points where the surface of an object was detected in the FOV of the LiDAR sensor. Each point contains the following information.

Target reflectivity: 0 to 255. 0 to 150 corresponds to the reflectivity within the range of 0 to 100% in the Lambertian reflection model. 151 to 255 corresponds to the reflectivity of target objects with retroflection properties. When the target is less than 2m from the Mid-70, it may result in a large reflectivity error. The data should be taken as a reference only.

Coordinates: can be expressed as Cartesian coordinates (x, y, z) and Spherical coordinates (r, θ, φ). The relationship between Cartesian and Spherical coordinates is shown in the figure below. When there is no object within the detection range or the object is placed outside the detection range, the coordinates of the point cloud will be expressed as (0, 0, 0) in Cartesian coordinates and as (0, θ, φ) in Spherical coordinates.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/de1e206e-ee81-4f85-ae28-2329bc1f4491/b83bdd63-76fc-4836-93a8-2b75dfdf7391/w=1920,quality=90,fit=scale-down" alt="Figure 5.2.1.1 Relationship between Cartesian coordinates and Spherical coordinates" height="320" width="968.2051282051282">

Figure 5.2.1.1 Relationship between Cartesian coordinates and Spherical coordinates

Tags: Indicates the return type of the laser and if the point detected is a noise. The format of the tag is as shown below:

| **bit7**                                                                                                                | **bit6** | **bit5**                                                           | **bit4** | **bit3**                                                                                                                    | **bit2** | **bit1**                                                                                                                                                                     | **bit0** |
| ----------------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Point property based on nearby waveform distortion: 00: Normal 01: Nearby waveform distortion 10: Reserved 11: Reserved |          | Return number: 00: return 0 01: return 1 10: return 2 11: Reserved |          | Point property based on intensity: 00: Normal 01: Noise that does not meet intensity expectations 10: Reserved 11: Reserved |          | Point property based on spatial position: 00: Normal 01: High confidence level of the noise 10: Moderate confidence level of the noise 11: Low confidence level of the noise |          |

Each tag is composed of one byte. In this byte, bit7, and bit6 are Group 1, bit5 and bit4 are Group 2, bit3 and bit2 are Group 3 while bit1 and bit0 are Group 4.

Group 1 indicates if the sampling point is a noise based on the nearby waveform distortion. Due to the optical system characteristics of the machine, nearby return signal will be distorted by the stray light inside the system, leading to unreliable depth calculation results (especially when the return signal energy is small). "01" indicates that nearby return signal is distorted; "00" indicates that waveform is normal.

Group 2 indicates the return sequence of the sampling point. Featuring a coaxial optical path, the Mid-70 itself will generate a laser return even if there is no detectable object around. This return is recorded as return 0. After that, if there is any object within the detectable range, the first laser that returns to the Mid-70 is recorded as return 1, and then return 2, and so on. If the object is too close to the Mid-70, such as 1.5 m away, the first effective return will be merged into return 0, and be recorded as return 0.

Group 3 indicates if the sampling point is a noise based on the intensity of the return. Normally, the intensity of the returns of the noises generated due to the interference of atmosphere particles such as dust, rain, fog, and snow is quite low. Therefore, the noises are divided into two categories based on the intensity of the return received. "00" stands for normal point cloud; "01" stands for low intensity of the return, indicating that the samples have a high possibility of being noises such as dust, rain, and fog. The lower the confidence level of the sample is, the lower the possibility that it is a noise.

Group 4 indicates if the sampling point is a noise based on its spatial position. Normally, when the Mid-70 sensors detect two objects in close proximity of each other, there will be some thread-like noises between the two objects. The noises are divided into three categories. The lower the confidence level of the noise is, the lower the possibility that it is noise.

**Timestamp**

There are three ways to synchronize data with the Mid-70: IEEE 1588-2008, Pulse Per Second (PPS), and GPS (PPS+UTC).

IEEE 1588-2008: IEEE 1588-2008 is the Precision Time Protocol (PTP) enabling precise synchronization of clocks in measurement and control systems by Ethernet. Livox LiDAR sensors, as the ordinary clock in the PTP, only supports UDP/IPV4 for PTP. Livox LiDAR sensors support the following message events: Sync, Follow\_up, Delay\_req, and Delay\_resp.

PPS: PPS uses the sync cable for data synchronization. Refer to the Cables section for more information. The synchronization logic is shown in the figure below. The pulse interval in PPS is 1s (t0 = 1000 ms) while the continuous time of high-level voltage is from 20 ms to 200 ms (20 ms < t1 < 200 ms). The rising edge of PPS resets the timestamp to zero, so the timestamp of the point cloud data indicates the duration between the point cloud sampling and the PPS rising edge.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/694d7a3a-d121-4b2a-9d1e-e5a05e72fa31/image/w=1920,quality=90,fit=scale-down" alt="Figure 5.2.2.1 Pulse Per Second" height="187.00940792139386" width="600.9625244140625">

Figure 5.2.2.1 Pulse Per Second

GPS: GPS is a way to synchronize the data using the sync cable and UTC time. The PPS port logic is the same as the PPS synchronization mentioned above. Users are able to send the UTC time of each pulse to the Mid-70 via SDK communication protocol. Refer to the SDK Communication Protocols section for more information about commands. The logic of the UTC Time and PPS signal command are shown below. The timestamp of the point cloud data stands for the UTC sampling time of the point cloud once GPS synchronization is in use.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0c0fc6d5-b654-40d4-81f2-d13b3763ae89/image/w=1920,quality=90,fit=scale-down" alt="Figure 5.2.2.2 UTC Time Commands" height="222.61949741768694" width="482.9875183105469">

Figure 5.2.2.2 UTC Time Commands

**Status Codes**

The status codes display the current working status of the Mid-70 sensors. By checking the status codes, users can see the temperature status, voltage status, motor status, dust warning, service life warning, and PPS signal status. Status codes can be viewed in Livox Viewer or the Livox SDK. Refer to the Livox Viewer User Manual for more information about how to check status codes.

| **Status**           | **Description**                                                                                                                                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Temperature status   | Indicates if there is any temperature abnormality. Temperature status includes normal, warning, and error.                                                                                                                   |
| Voltage status       | Indicates if there is any internal voltage abnormality. Voltage status includes normal, warning, and error.                                                                                                                  |
| Motor status         | Indicates if there is any internal motor abnormality. Motor status includes normal, warning, and error.                                                                                                                      |
| Dust warning         | Indicates if a significant amount of dust is detected on the optical window or if the optical window is covered by objects.                                                                                                  |
| Service life warning | Indicates if the LiDAR sensor is nearing the end of its service life. The LiDAR sensor can still work for a short period once this warning appears. It is recommended to replace the LiDAR sensor once this warning appears. |
| PPS signal status    | Indicates whether the PPS sync signal is working normally.                                                                                                                                                                   |

### **Working States & Working Modes** <a href="#block-390d4c79856d8036a36aee8205543f1e" id="block-390d4c79856d8036a36aee8205543f1e"></a>

The working states of the Mid-70 includes initializing, normal, standby, power saving, and error.

| **Working states** | **Description**                                                                                                                                |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Initializing       | The LiDAR sensor is powering on.                                                                                                               |
| Normal             | The LiDAR sensor is powered on and working normally.                                                                                           |
| Standby            | The LiDAR sensor is powered on, but the laser beams are not active.                                                                            |
| Power saving       | All components are powered off apart from the communication module.                                                                            |
| Error              | The LiDAR sensor will enter error status when an error is detected and all the components are powered off apart from the communication module. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d6abd848-3948-44b7-a554-982a988989a3/image/w=1920,quality=90,fit=scale-down" alt="Figure 5.2.1 Relationship between the different working states" height="323.7069865979646" width="458.9875183105469">

Figure 5.2.1 Relationship between the different working states

The Mid-70 also has three working modes: Normal, Standby, and Power Saving. These modes can be set in Livox Viewer and the Livox SDK.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/06d1c734-d343-49e6-b139-48cc152aa8a4/image/w=1920,quality=90,fit=scale-down" alt="Figure 5.3.2 Relationship between the different working modes available in Livox Viewer" height="272.3217079276469" width="653.9625244140625">

Figure 5.3.2 Relationship between the different working modes available in Livox Viewer

### **Dual Return Mode** <a href="#block-390d4c79856d80718b19e46ca5e8ded8" id="block-390d4c79856d80718b19e46ca5e8ded8"></a>

The Mid-70 can be set to Dual Return mode using Livox Viewer or the Livox SDK. The Mid-70 can generate a point cloud of up to two returns in Dual Return mode, which has a point rate of 200,000 points per second.

To set the return mode, run Livox Viewer after the Mid-70 is connected.

Click the desired device under Device Manager. Click to select the return mode.

### **Livox Viewer** <a href="#block-390d4c79856d80c498cacec089472de7" id="block-390d4c79856d80c498cacec089472de7"></a>

Livox Viewer is a computer software designed for Livox LiDAR sensors and Livox Hub. Users can check realtime point cloud data of all the Livox LiDAR sensors connected to a computer, and also record the point cloud data to view offline or for future application. The simple interface makes it easy to use.

Visit [www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer. Livox Viewer supports Windows® 7/8/10 (64 bit) and Ubuntu™ 16.04 (64 bit).

💡

**Note:**

* Turn off firewalls on your computer before using Livox Viewer. Otherwise, Livox Viewer may not be able to detect the Livox LiDAR sensors. Make sure the graphics driver is correctly installed. Otherwise, Livox Viewer may not launch or may crash.

For Windows users: unzip the Livox Viewer file and click to open the .exe file named "Livox Viewer."

For Ubuntu users: unzip the Livox Viewer file and click to open the "./livox\_viewer.sh" file under the root directory.

For more information, download the Livox Viewer User Manual from the official website [www.livoxtech.com](http://www.livoxtech.com/).

### **Software Development Kit (SDK)** <a href="#block-390d4c79856d805590c2fa5f3c1fbeb9" id="block-390d4c79856d805590c2fa5f3c1fbeb9"></a>

Besides using Livox Viewer to check real-time point cloud data, users can also use the SDK to apply the point cloud acquired from Livox LiDAR sensors to different scenarios.

**SDK Communication Protocol**

With the SDK Communication Protocol, users can learn how to customize the Livox LiDAR sensors. The SDK Communication Protocol encompasses the following three types of data:

Control Command Data: Configuration and query of LiDAR parameters and status information.

Point Cloud Data: Point cloud data generated by LiDAR.

All data is stored in little-endian format.

Visit [http://www.livoxtech.com/sdk](http://www.livoxtech.com/sdk) to learn more information about SDK communication protocol, Livox SDK API reference.

## **Storage, Transportation, and Maintenance** <a href="#block-390d4c79856d803bb0bde9ad0a9710db" id="block-390d4c79856d803bb0bde9ad0a9710db"></a>

### **Storage** <a href="#block-390d4c79856d801287d2d9c932e65773" id="block-390d4c79856d801287d2d9c932e65773"></a>

The storage temperature range for the Mid-70 is from -20° to 65° C (-4° to 149° F). Keep Mid-70 sensors in a dry and dust-free environment.

* Make sure Mid-70 sensors are not exposed to environments containing poisonous or corrosive gases or materials.
* DO NOT drop Mid-70 sensors and be careful when placing a LiDAR sensor in storage or taking it out of storage.
* If a Mid-70 sensor is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

### **Transportation** <a href="#block-390d4c79856d80169b0eceb18c5d591b" id="block-390d4c79856d80169b0eceb18c5d591b"></a>

Before transportation, place Mid-70 sensors in a suitable box for transportation and make sure it is secure. Make sure to place foam inside the transportation box and that the box is clean and dry.

DO NOT drop Mid-70 sensors and always be careful when carrying a LiDAR sensor.

### **Maintenance** <a href="#block-390d4c79856d80ba83bbe37aa4d2bb9e" id="block-390d4c79856d80ba83bbe37aa4d2bb9e"></a>

In normal conditions, the only maintenance required for the Mid-70 is to clean the optical window of the LiDAR sensor. Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor. Make sure to regularly clean the optical window to prevent this from happening.

First, check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. Use compressed or canned air: DO NOT wipe a dusty optical window, as it will only cause more damage. Dust the optical window with compressed or canned air before wiping the optical window. Note that if the optical window has no visible stains afterward, it is not necessary to wipe also.
2. Wipe the stains: DO NOT wipe using a dry lens tissue, as it will scratch the surface of the optical window. Use the lens tissue provided with isopropyl alcohol. Wipe slowly to remove the dirt instead of redistributing it on the surface of the optical window. If the optical window is still dirty, a mild soap solution can be used to gently wash the window. Repeat Step 2 to remove any remaining soap residue.

## **Troubleshooting** <a href="#block-390d4c79856d80b2a8b7c04d042c3ce5" id="block-390d4c79856d80b2a8b7c04d042c3ce5"></a>

The table below shows you how to troubleshoot and resolve common issues with Mid-70 sensors. If the issue persists, contact Livox.

| **Issue**                                                          | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cannot detect the LiDAR sensor                                     | • Make sure that all cables are correctly wired. • Make sure the voltage and power supply is suitable. The voltage should be between 10 and 15 V. If a Livox Converter 2.0 is in use, the supported voltage range of the external power source is from 9 to 30 V. • Make sure that the LiDAR sensor is not connected to other software. • Make sure the LAN is selected. • Make sure no security software is installed that would block Ethernet broadcasts. If the issue persists, try to turn off all firewalls and search again. Confirm the packet outputs for all connected devices using another application (e.g., Wireshark). |
| Cannot connect to the detected LiDAR sensor/ Cannot start sampling | • Make sure that all cables are correctly wired. • Make sure the voltage and power supply is suitable. The voltage should be between 10 and 15 V. If a Livox Converter 2.0 is in use, the supported voltage range of the external power source is from 9 to 30 V. If the issue persists, reboot the LiDAR sensor and restart the software.                                                                                                                                                                                                                                                                                            |
| No data received                                                   | Confirm the packet outputs for all connected devices using another application (e.g., Wireshark).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

## **After-Sales Information** <a href="#block-390d4c79856d80388524df748aeea091" id="block-390d4c79856d80388524df748aeea091"></a>

Visit [www.livoxtech.com/support](http://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox LiDAR sensors.

## Appendix <a href="#block-390d4c79856d809aacc5c987a519c77d" id="block-390d4c79856d809aacc5c987a519c77d"></a>

### **Appendix 1** <a href="#block-390d4c79856d803e95a1f77a280f22d8" id="block-390d4c79856d803e95a1f77a280f22d8"></a>

Livox Mid-70 Dimensions (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/813fb335-c84d-455b-bc1b-bd7443983da8/image/w=1920,quality=90,fit=scale-down" alt="image" height="616.029210175956" width="724.8250122070312">

### **Appendix 2** <a href="#block-390d4c79856d80dbb9fadd95d9ed028c" id="block-390d4c79856d80dbb9fadd95d9ed028c"></a>

Livox Mid-70 Mounting Bracket Dimensions (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1df0fb45-e2b4-426e-ba66-d482a3ecdb94/image/w=1920,quality=90,fit=scale-down" alt="image" height="777.6780107671565" width="511.9875183105469">

### Appendix 3 <a href="#block-390d4c79856d8006b813c26f54ecbaa6" id="block-390d4c79856d8006b813c26f54ecbaa6"></a>

Livox Converter 2.0 Dimensions (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19bed60c-a591-4372-bfbf-6c180360df85/image/w=1920,quality=90,fit=scale-down" alt="image" height="264.03611555783556" width="724.8250122070312">

## Specifications <a href="#block-390d4c79856d80958ef4c9db72849f0c" id="block-390d4c79856d80958ef4c9db72849f0c"></a>

| Livox Mid -70                        |                                                                             |
| ------------------------------------ | --------------------------------------------------------------------------- |
| Operating Temperature Range          | -20° to 65° C (-4° to 149° F)                                               |
| Operating Temperature Range of Shell | -20° to 80° C (-4° to 176° F)                                               |
| Laser Wavelength                     | 905 nm                                                                      |
| Laser Safety                         | Class 1 (IEC 60825-1:2014) (safe for eyes)                                  |
| Detection Range (@ 100 klx)          | 90 m @ 10% reflectivity 130 m @ 20% reflectivity 260 m @ 80% reflectivity   |
| FOV                                  | 70.4° (circular)                                                            |
| Distance Random Error                | 1σ (@ 20m) ≤ 2cm 1σ (@ 0.2-1m) ≤ 3cm                                        |
| Angular Random Error                 | 1σ < 0.1°                                                                   |
| Beam Divergence                      | 0.28° (Vertical) × 0.03° (Horizontal)                                       |
| Point Rate                           | 100,000 points/s (first or strongest return) 200,000 points/s (dual return) |
| Data Latency                         | ≤ 2 ms                                                                      |
| Data Synchronization                 | IEEE 1588-2008 (PTP v2), PPS (Pulse Per Second), GPS (PPS+UTC)              |
| False Alarm Ratio (@ 100 klx)        | < 0.01%                                                                     |
| IP Rating                            | IP67                                                                        |
| Power                                | 8 W (average) 35 W (peak)                                                   |
| Power Supply Voltage Range           | Livox Mid-70: 10-15 V DC Livox Converter 2.0: 9-30 V DC                     |
| Dimensions                           | 97×64×62.7 mm                                                               |
| Weight                               | Approx. 580 g                                                               |

| Livox Mid -70 Mounting Bracket |               |
| ------------------------------ | ------------- |
| Dimensions                     | 100x97x5.7 mm |
| Weight                         | Approx.76 g   |
| Livox Converter 2.0            |               |
| Dimensions                     | 74x52x23 mm   |
| Weight                         | 88 g          |
