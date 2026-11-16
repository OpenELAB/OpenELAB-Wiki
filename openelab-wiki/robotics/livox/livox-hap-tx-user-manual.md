# LIVOX HAP (TX) User Manual

> LIVOX HAP(TX) User Manual

{% embed url="https://openelab.io/products/livox-hap-automotive-grade-lidar3d?variant=45564452995270" %}

## **Product Profile** <a href="#block-38fd4c79856d80e6adb7e256a2405d29" id="block-38fd4c79856d80e6adb7e256a2405d29"></a>

### **Introduction** <a href="#block-38fd4c79856d80508712f4ada4101995" id="block-38fd4c79856d80508712f4ada4101995"></a>

Livox HAP features a long detection range, high precision, wide field-of-view (FOV), and high reliability. It can be used for multiple applications, including autonomous driving, robots, automated guided vehicles, and unmanned aircraft. Livox HAP has two models, which are HAP (T1) and HAP (TX). This document is intended for HAP (TX).

**High FOV Coverage:** The HAP (TX) utilizes Livox's unique non-repetitive scanning technology and multi-laser and multi-APD DL-Pack technology, which can quickly detect every detail inside the FOV.

**Wide FOV:** The HAP (TX) has a rectangular FOV of 120° horizontally and 25° vertically. The HAP (TX) scans horizontally from top to bottom, increasing its compatibility with algorithms used to process common point cloud data.

**High Reliability:** The HAP (TX) offers enhanced reliability as the cutting-edge design works normally without rotating internal electronic devices such as the transmitter and receiver.

**Environmental Adaptation:** Even under 100 kilolux conditions, the HAP (TX) boasts a low noise rate below 0.01%. The HAP (TX) can effectively reduce interference from other LiDAR sensors thanks to the innovative de-noising algorithms built into the unit.

**User-Friendly Livox Viewer 2:** Livox Viewer 2 is software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

**Open Source Livox SDK:** A software development kit (SDK) is provided to help develop customizable applications using the data acquired from the point cloud data. Livox SDK supports Windows/Linux/Mac OS/ROS.

💡

**Note:**

* The HAP (TX) has a detection range of up to 200 m, which can be reached when the target object reflects 35% of light or more. For reference, grey concrete walls and roads have a reflectivity range from 15 to 30%, while white plaster walls have a reflectivity range from 90 to 99% in an environment with a temperature of 25° C (77° F).
* Before using for the first time remove the screen protector from the optical window.

### **Product Characteristics** <a href="#block-38fd4c79856d801d9006dff5159e7804" id="block-38fd4c79856d801d9006dff5159e7804"></a>

The HAP (TX) utilizes Livox's unique non-repetitive scanning technology and multi-laser and multi-APD DL-Pack technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surroundings.

Figure 1.2.1 displays the point cloud allocation of the HAP (TX) inside the FOV within 0.1s. In the center of the FOV, the scanning density is denser, with the average spacing of lines being 0.2° (most line spacing is from 0.1 to 0.3°), which is much denser than traditional 64-line LiDAR sensors. The two areas on both sides have a lower scanning density and average spacing lines of 0.3° (most line spacing is between 0.2 to 0.5°), rivaling traditional 64-line LiDAR sensors within 0.1 seconds.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/870aeedd-5859-482a-b0f4-03737146c0c8/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.1 Point Cloud Allocation of the HAP (TX) within 0.1s (coordinates units: °)" height="188.59751762058426" width="558.9874877929688">

Figure 1.2.1 Point Cloud Allocation of the HAP (TX) within 0.1s (coordinates units: °)

Figure 1.2.2 displays the point cloud patterns of the HAP (TX) with respect to different integration time.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/08215e07-695f-45bd-a9c1-68b603e2c97f/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.2 Point cloud patterns of the HAP (TX) accumulated over different integration time" height="97.92332398588609" width="724.7999877929688">

Figure 1.2.2 Point cloud patterns of the HAP (TX) accumulated over different integration time

Figure 1.2.3 displays the FOV coverage of the HAP (TX) over different integration time, compared with other non-Livox LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is less than 0.1 second, the FOV coverage of the HAP (TX) is close to 80%, better than a 64-line LiDAR sensor. As the integration time increases to 0.5 seconds, the FOV coverage approaches 99%, so almost all areas are illuminated by laser beams.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/44989520-6f6d-414b-a715-ad8dd54ce7d6/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.3 The FOV coverage of the HAP (TX) over different integration times compared with non-Livox LiDAR sensors using traditional mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°." height="300.0827145134051" width="371.9875183105469">

Figure 1.2.3 The FOV coverage of the HAP (TX) over different integration times compared with non-Livox LiDAR sensors using traditional mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.💡

The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams. The FOV coverage (C) can be calculated with the following formula:

C=TotalareailluminatedbylaserbeamsTotalareainFOV∗100%C=TotalareainFOVTotalareailluminatedbylaserbeams​∗100%

Refer to the official Livox website for more information about how the FOV coverage is calculated.

Table 1.2.1 Point cloud specifications

| Laser Wavelength              | 905 nm                                     |
| ----------------------------- | ------------------------------------------ |
| Laser Safety                  | Class 1 (IEC 60825-1:2014) (Safe for eyes) |
| Detection Range (@100 klx)    | 150 m @ 10% reflectivity                   |
| Close Proximity Blind Zone    | 0.5 m                                      |
| FOV                           | 120° (horizontal) × 25° (vertical)         |
| Distance Random Error (1σ)    | < 2 cm @ 20 m (80% reflectivity)           |
| Distance System Error         | < ± 3 cm @ 20 m                            |
| Angular Random Error (1σ)     | < 0.1°                                     |
| Beam Divergence               | 0.03° (horizontal) × 0.28° (vertical)      |
| Point Rate                    | 452,000 points/s                           |
| Frame Rate                    | 10 Hz                                      |
| False Alarm Ratio (@ 100 klx) | 0.01%                                      |

💡

**Note:**

* HAP (TX) cannot precisely detect objects which are less than 0.5 m away. In this situation, the HAP (TX) will output warning message for blocking, and the serial number of the HAP (TX) displayed on Livox Viewer 2 will change color to warn users. If used at the time, check the SDK for more information about the warning. The point cloud may distort to a varying extent when the target object is within the range of 0.5 to 2 m.
* The HAP (TX) has a detection accuracy of 2 cm when tested at a temperature of 25° C (77° F) with a target object that is 20 m away and has a reflectivity of 80%. The actual environment may differ from the testing environment. The figure listed is for reference only.
* The performance of the HAP (TX) may decrease in extreme environments, such as those where the temperature is -40° C (-40° F) or 85° C (185° F) or those that cause high vibration.

### Overview <a href="#block-38fd4c79856d80f7a798e232b5a1009f" id="block-38fd4c79856d80f7a798e232b5a1009f"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7727665b-a83a-45ea-a5ef-cb3359fd7dfd/image/w=1920,quality=90,fit=scale-down" alt="image" height="191.41790088670984" width="331.38751220703125">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5c97d708-f80e-47ce-9b77-061fcbb4d431/0cef8573-c293-4ab0-97a8-4499c885b0e5/w=1920,quality=90,fit=scale-down" alt="image" height="320" width="487.14285714285717">

1. **Optical Window**
2. The laser passes through the optical window and scans objects in the FOV.
3. **Locating Hole 1**
4. The locating hole makes it easy for users to find the correct place to mount a fixed support for the HAP (TX). Refer to the Dimensions section for more information.
5. **M6 Mounting Through-Hole (Φ6.5) × 4**
6. Users can mount the HAP (TX) to an appropriate place using M6 screws.
7. **M12 Aviation Connector**
8. The M12 aviation connector can be connected to the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) for quick testing and debugging. Users can also customize cables according to the pinout reference table to improve the waterproof and dustproof protection of the HAP (TX). Refer to the Connectors section for more information on the M12 aviation connector.
9. **M3 Mounting Hole × 4**
10. Users can mount the HAP (TX) to an appropriate place with M3 screws.
11. **Locating Hole 2**
12. The locating hole makes it easy for users to find the correct place to mount a fixed support for the HAP (TX). Refer to the Dimensions section for more information.
13. **Waterproof Breathable Valve**
14. The waterproof breathable valve can help balance the pressure difference between the inside and outside of the HAP (TX).

💡

Visit the DJl official store to purchase the Livox Aviation Connector 1-to-3 Splitter Cable. The Livox Aviation Connector 1-to-3 Splitter Cable can only be used for testing and debugging. It is recommended to customize the cable and connectors for other scenarios that require high reliability.

## **Connectors** <a href="#block-38fd4c79856d801fbab5c6890226a777" id="block-38fd4c79856d801fbab5c6890226a777"></a>

### **M12 Aviation Connector** <a href="#block-38fd4c79856d8012b224eef96604c053" id="block-38fd4c79856d8012b224eef96604c053"></a>

The HAP (TX) uses the high-reliability M12 aviation connector (male). The M12 12P A-code fully shielded male connector meets the IEC 61076-2-101 standard. The connector type is Finecables, and the port number is MA12MAHD12STXXXB14. The corresponding female connector type is Finecables, and the port number is MA12FAHD12STXXXB14. Both connectors have an IP rating of IP67. Users can connect the HAP (TX) with the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) for transmission of power, control signal, and data. Users can also replace the cable with other cables to improve the dustproof and waterproof protection of the HAP (TX).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0ab8a0c8-683b-4997-840a-cd55d1a61f04/image/w=1920,quality=90,fit=scale-down" alt="image" height="326.46052431217487" width="724.8250122070312">

### **Livox Aviation Connector 1-to-3 Splitter Cable** <a href="#block-38fd4c79856d805884c8d3eb41cc210f" id="block-38fd4c79856d805884c8d3eb41cc210f"></a>

Users can connect the HAP (TX) with the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately). The Livox Aviation Connector 1-to-3 Splitter Cable has an M12 aviation connector (female) on one end, and the other end is split into the power, network, and function cables.

The M12 aviation connector (female) connects to the M12 aviation connector (male) on the HAP (TX). The power cable connects to external DC power supply. The network cable has an RJ-45 network connector which connects to the RJ-45 connector on a computer for data transmission during testing. The function cable does not need to be used as it has no electrical current when using with the HAP (TX).

See below for more information on the HAP (TX) M12 aviation connector (male) and the Livox Aviation Connector 1-to-3 Splitter Cable.

| **M12 Aviation Connector Pin** | **Signal**   | **Type** | **Description** | **Color**        | **Function**                                                                                           |
| ------------------------------ | ------------ | -------- | --------------- | ---------------- | ------------------------------------------------------------------------------------------------------ |
| 1                              | Power+       | Power    | DC VCC          | Red (positive)   | Power cable (Connects to DC power)                                                                     |
| 9                              | Power+       | Power    | DC VCC          |                  |                                                                                                        |
| 2                              | Ground       | Power    | Ground          | Black (negative) |                                                                                                        |
| 3                              | Ground       | Power    | Ground          |                  |                                                                                                        |
| 4                              | Ethernet-TX+ | Output   | Ethernet-TX+    | Orange/white     | Ethernet cable (Connects to computer or router)                                                        |
| 5                              | Ethernet-TX- | Output   | Ethernet-TX-    | Orange           |                                                                                                        |
| 6                              | Ethernet-RX+ | Input    | Ethernet-RX+    | Green/white      |                                                                                                        |
| 7                              | Ethernet-RX- | Input    | Ethernet-RX-    | Green            |                                                                                                        |
| 8                              | N/A          | N/A      | N/A             | Purple/white     | Function cable (Not in use. DO NOT connect with other power or signal cables to avoid short circuits.) |
| 10                             | N/A          | N/A      | N/A             | Gray/white       |                                                                                                        |
| 11                             | N/A          | N/A      | N/A             | Gray             |                                                                                                        |
| 12                             | N/A          | N/A      | N/A             | Purple           |                                                                                                        |
| 2&3                            | Ground       | Ground   | Ground          | Black            |                                                                                                        |

## **Mounting the HAP (TX)** <a href="#block-38fd4c79856d8079ad81c17d07dde235" id="block-38fd4c79856d8079ad81c17d07dde235"></a>

### **Effective FOV Range** <a href="#block-390d4c79856d80e099b8c5f45d2fb585" id="block-390d4c79856d80e099b8c5f45d2fb585"></a>

As shown below, the HAP (TX) has a FOV of 120° horizontally and 25° vertically. When mounting the sensor, make sure that the FOV is not blocked by any objects. Visit [www.livoxtech.com/hap](http://www.livoxtech.com/hap) to download the 3D model of the HAP (TX) and its FOV.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f18f8ee5-f072-460f-977c-a76a0ddaccea/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.1.1 Effective FOV of the HAP (TX)" height="248.99871007582718" width="724.8250122070312">

Figure 3.1.1 Effective FOV of the HAP (TX)

Note that the HAP (TX) effective detection range varies based on where the object is within the FOV. The closer to the edge of the FOV, the shorter the effective detection range is. The closer to the center of the FOV, the farther the effective detection range. Refer to the diagrams below: Pay attention to the effective detection range when in use.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f0cfc876-7f03-47f3-9b6b-31fa0f12b671/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.1.2 Effective Detection Range inside FOV of the HAP (TX)" height="327.48689778645837" width="724.8125">

Figure 3.1.2 Effective Detection Range inside FOV of the HAP (TX)

As shown above, when an object with a reflectivity of 10% is placed near the border of the vertical FOV, the object can be detected as far as 125m.

### Mounting Notice <a href="#block-38fd4c79856d800fbee7d6d03ed8a580" id="block-38fd4c79856d800fbee7d6d03ed8a580"></a>

Read and understand the following warnings before mounting the HAP (TX):

1. Before use, remove the screen protector from the optical window.
2. Significant dust and stains on the optical window will affect the performance of the LiDAR sensor. Follow the instructions in the Maintenance section to clean the optical window using compressed air, isopropyl alcohol, or a lens cloth. Mount the HAP (TX) after cleaning it.
3. When mounting the HAP (TX), the field of view must not be blocked by an object, including glass. Refer to Figure 3.1.1.
4. When mounting the HAP (TX), allow a space of at least 10mm around the device to prevent poor airflow affecting heat dissipation, and make sure the waterproof breathable valve is not blocked.
5. The HAP (TX) cannot bear any extra payload. Otherwise, the reliability of the product cannot be guaranteed.

### **Dimensions** <a href="#block-38fd4c79856d80dbab68ea43820c5664" id="block-38fd4c79856d80dbab68ea43820c5664"></a>

The bottom surface of the HAP (TX) has four M3 mounting holes with a depth of 5mm, and four M6 mounting through-holes (Φ6.5). Refer to the below illustrations for HAP (TX) dimensions and locations for the mounting holes, and mount the HAP (TX) in an appropriate place.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1fdbd8ee-a365-4696-8370-061b7707c30b/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.2.1 HAP (TX) Dimensions (refer to Appendix 1)" height="378.0592537415904" width="724.8250122070312">

Figure 3.2.1 HAP (TX) Dimensions (refer to Appendix 1)

Table 3.2.1 HAP (TX) Weight and Dimensions

| **Weight** | **Approx. 1120 g**  |
| ---------- | ------------------- |
| Dimensions | 105 × 131.6 × 65 mm |

## **Getting Started** <a href="#block-38fd4c79856d80e38c38c0ffaa7bc51b" id="block-38fd4c79856d80e38c38c0ffaa7bc51b"></a>

### **External Power Supply** <a href="#block-38fd4c79856d802bbb73e111da78ea86" id="block-38fd4c79856d802bbb73e111da78ea86"></a>

The working voltage range of the HAP (TX) is from 9 to 18 V, the recommended working voltage is 12 V. The minimum working voltage should be increased in a low-temperature environment. When the HAP (TX) is connected to an external power source directly through the M12 aviation connector, make sure the output voltage range of the external power source is within the operating voltage range of the HAP (TX). When an extension cable is required, make sure to increase the output voltage of the external power source due to the extra voltage reduction. Make sure the maximum voltage does not exceed 18 V. Note that the power cable may generate voltage fluctuation where the voltage exceeds 18 V in some scenarios, such as if the power cable is interfered with or other devices connected to another power source in the parallel circuit suddenly power off. In such scenarios, the HAP (TX) may not work normally or even be damaged.

The HAP (TX) has a working power of 10 W when working normally at a temperature of 25°C. The working power varies depending on each sensor, but the maximum working power does not exceed 12 W. In low-temperature or high-temperature environments, the startup power of HAP (TX) may reach 40 W. In an environment where the temperature is below 0°C, the HAP (TX) will enter self-heating mode automatically. The lower the temperature, the greater the power.

Additionally, the HAP (TX) supports the window-heating mode, which can be used for defrosting and defogging the window. Users can choose to turn on or off the window-heating mode based on their needs. In window-heating mode, the working power may increase by 10 W. The working power of the HAP (TX) varies at different temperatures. Make sure the power supply is suitable based on the peak power of the HAP (TX). The value is for reference only. In normal conditions, the peak power varies depending on each sensor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1b10b56e-ea1b-4efc-9975-c75fe128abe2/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.1.1 The working power of the HAP (TX) at different temperatures" height="263.8842834039783" width="724.8250122070312">

Figure 4.1.1 The working power of the HAP (TX) at different temperatures

### **Connection** <a href="#block-38fd4c79856d80999b42ceb9e7f751f3" id="block-38fd4c79856d80999b42ceb9e7f751f3"></a>

The M12 aviation connector of HAP (TX) supports transmission of power and data. Refer to the Connectors section for more information about the connector. It is recommended to use the Livox Aviation Connector 1-to-3 Splitter Cable (sold separately) when testing or using the HAP (TX) temporarily. The Livox Aviation Connector 1-to-3 Splitter Cable contains the M12 aviation connector (male), power cable (bare wires), function cable (with insulation) and network cable (with RJ-45 connector).

The HAP (TX) transfers data using the User Datagram Protocol (UDP). All HAP (TX) are set to static IP address mode by default with an IP address of 192.168.1.100. The default subnet masks of HAP (TX) are 255.255.255.0 and their default gateways are 192.168.1.1. Directly connect the HAP (TX) to a computer.

1. Before connecting, set the IP address of the computer to static IP address mode. Set the IP address of the computer to the same network subnet as the IP address of HAP (TX). Follow the steps to set the IP address of your computer to static IP address:

* **Windows system**

1. Click to enter the Network and Sharing Center under Control Panel.
2. Click the network you are using and click "Properties".
3. Double click "Internet Protocol Version 4 (TCP/IPv4)".
4. Set the static IP address of the computer to 192.168.1.XX (make sure the IP address is different from the connected LiDAR sensor), such as 192.168.1.50 and that the subnet mask is set at 255.255.255.0. Click "OK" to complete.

* **Ubuntu-18.04 system**

The IP address of the computer can be configured by using the ifconfig command at the terminal. The configuration code is as below:

Copy

```javascript
~$ sudo ifconfig enp4s0 192.168.1.50
```

(replace "enp4s0" with the network port name of the computer)

2. Connect the HAP (TX) as shown below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fc50d38f-03c5-4ad4-bc2a-43a3ef731c63/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.2.1 Connecting the HAP (TX)" height="176.78658834317835" width="724.8250122070312">

Figure 4.2.1 Connecting the HAP (TX)

1. Connect the M12 aviation connector (female) on Livox Aviation Connector 1-to-3 Splitter Cable with the M12 aviation connector (male) on HAP (TX). The lock nut of the M12 aviation connector (female) should be tightened with a wrench to ensure a secure connection with the end face of the M12 aviation connector (male) lock nut. Make sure there is no gap between them.
2. Connect the RJ-45 network connector on the Livox Aviation Connector 1-to-3 Splitter Cable to the computer.
3. Connect the power cable on the Livox Aviation Connector 1-to-3 Splitter Cable to the external power source. Pay attention to the input voltage range and polarity.

💡

**Note:**

* The function cable does not need to be used as it has no electrical current when using with the HAP (TX).
* When multiple HAP (TX) LiDAR sensors are connected to one computer in static IP address mode, make sure all sensors connected have different static IP addresses. Refer to Livox HAP User Manual for more information on how to set the IP address for each LiDAR sensor.
* If more than six HAP (TX) LiDAR sensors are required, use a gigabit router or a switch.
* The broadcast number for each LiDAR sensor can be viewed in the Device Manager of Livox Viewer 2 or the Livox SDK. For the HAP (TX), the broadcast number will be its serial number ending in an additional "1".
* Launch Livox Viewer 2 after the HAP (TX) is connected. Click the device with the static IP address that should be altered. Click to open the settings page and set the static IP address of the HAP (TX).

## **Usage** <a href="#block-38fd4c79856d80a7929bf7600b06cfcb" id="block-38fd4c79856d80a7929bf7600b06cfcb"></a>

### **Coordinates** <a href="#block-38fd4c79856d801f9594d8dffb9a86c8" id="block-38fd4c79856d801f9594d8dffb9a86c8"></a>

The coordinates of the HAP (TX) are defined as shown below.

**Positioning Coordinates O'- X'Y'Z':** Point O' is the intersection point between the bottom surface and the locating hole 1. The Z' axis is the normal vector perpendicular to the bottom surface, and the X' axis is the normal vector perpendicular to the optical window surface.

**Point Cloud Coordinates O- XYZ:** Point O is the center of the optical window surface, and its coordinates directions are the same with that of the Positioning Coordinates.

The position and pose relation of the point cloud coordinate system relative to the positioning coordinate system is: (X, Y, Z, Roll, Pitch, Yaw) -> (8mm, 0 mm, 23 mm, 0°, 0°, 0°).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/55173abe-9957-4307-b034-f595a3ef42a5/image/w=1920,quality=90,fit=scale-down" alt="Figure 5.1.1 HAP (TX) Coordinates" height="318.2799209119033" width="400.9750061035156">

Figure 5.1.1 HAP (TX) Coordinates

### **Output Data** <a href="#block-38fd4c79856d8035bd99fe2c96264f6c" id="block-38fd4c79856d8035bd99fe2c96264f6c"></a>

The output information of HAP (TX) LiDAR sensors includes:

* Point Cloud Data (including timestamp)
* Control Command ACK
* Information Push

**Point Cloud Data**

A point cloud is the collection of the points where the surface of an object was detected in the FOV of the LiDAR sensor. Each point contains the following information.

Target reflectivity: 0 to 150 corresponds to the reflectivity within the range of 0 to 100% in the Lambertian reflection model. 151 to 255 corresponds to the reflectivity of target objects with retroflection properties.

Coordinates: Can be expressed as Cartesian coordinates (x, y, z). When there is no object within the detection range or the object is placed beyond the detection range, the coordinates of the point cloud will be expressed as (0, 0, 0) in Cartesian coordinates.

Tags: Indicates the return type of the laser and if the point detected is a noise. The format of the tag is as shown below:

| **bit7** | **bit6** | **Bit5**                                                           | **Bit4** | **Bit3**                                                                                                                   | **Bit2** | **Bit1**                                                                                                                                                         | **Bit0** |
| -------- | -------- | ------------------------------------------------------------------ | -------- | -------------------------------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Reserved |          | Return Number: 00: Return 0 01: Return 1 10: Return 2 11: Reserved |          | Point property based on intensity: 00: Normal 01: Noise that does not meet intensity expectation 10: Reserved 11: Reserved |          | Point property based on spatial position: 00: Normal 01: High confidence level of noise 10: Moderate confidence level of noise 11: Low confidence level of noise |          |

Each tag is composed of one byte. In this byte, bit7 and bit6 are Group 1, bit5 and bit4 are Group 2, bit3 and bit2 are Group 3 while bit1 and bit0 are Group 4.

Group 2 indicates the return sequence of the sampling point. Featuring a coaxial optical path, the HAP (TX) LiDAR sensor will generate a laser return even if there is no detectable object around. The return is recorded as return 0. After that, if there is any object within the detectable range, the first laser that returns to the HAP (TX) is recorded as return 1, and then return 2, and so on. If the object is too close to the HAP (TX), such as 1.5 m away, the first effective return will be merged into return 0, and be recorded as return 0.

Group 3 indicates if the sampling point is noise based on the intensity of the return. Normally, the intensity of the returns of the noises generated due to the interference of atmospheric particles such as dust, rain, fog, and snow is relatively low. Therefore, sampling points are divided into two categories based on the intensity of the return received: "00" represents a normal return; "01" represents a low-intensity return, indicating that the sampling points have a high possibility of being noise such as dust, rain and fog. It is recommended that users use the sampling points whose return intensity is "00".

Group 4 indicates if the sampling point is noise based on its spatial position. Normally, when the HAP (TX) LiDAR sensors detect two objects in close proximity of each other, there will be some thread-like noise between the two objects.

**Timestamp**

The HAP (TX) only supports the Generic Precision Time Protocol (gPTP) based on IEEE 802.1AS standard, where the domain controller works as the master, and the HAP (TX) as the slave:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8ed88ddc-9331-41cb-930c-71a03f44a41f/image/w=1920,quality=90,fit=scale-down" alt="image" height="423.1227736074713" width="378.9875183105469">

Calculate the transmission delay by following the steps above:

link\_delay = \[(t4 - t1) - (t3 - t2)] / 2

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2174c2b1-7d0f-4b13-80bc-b16e1bf05186/image/w=1920,quality=90,fit=scale-down" alt="image" height="361.32907459347746" width="456.9750061035156">

Calculate offset with sync and follow\_up:

offset = (t2' - t1') - link\_delay

The AUTOSAR standard Specification of Time Synchronization over Ethernet includes the special requirements for IEEE 802.1AS in automotive applications, such as:

* No support of Announce messages.
* No support for Best Master Clock Algorithm (BCMA).
* Master does not send delay\_req message.

As the time synchronization method of HAP (TX) integrates AUTOSAR gPTP, HAP (TX) follows above requirements.

**Control Command ACK**

Master sends control commands to the HAP (TX). HAP (TX) sends ACK messages once receiving the control command. Refer to the Control Command section in the SDK Communication Protocols for specific information.

**Information Push**

In normal conditions, the HAP (TX) pushes status information at 1Hz (such as the status of the LiDAR sensor, error code, flash status); In abnormal conditions, the HAP (TX) keeps pushing status information at 100Hz for 100ms for users to quickly recognize the error and take action.

The HAP (TX) will automatically push log data once anything abnormal happens. Users need to save these log data and provide them to Livox Support for analysis. Contact Livox Support for detailed definitions of the messages indicating abnormal situations.

### **Livox Viewer 2** <a href="#block-38fd4c79856d806591f4e66794f686e7" id="block-38fd4c79856d806591f4e66794f686e7"></a>

Livox Viewer 2 is software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

Visit [www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer 2. Livox Viewer 2 supports Windows® 10 (64 bit) and Ubuntu™ 18.04 (64 bit). Follow the steps below to use the Livox Viewer 2.

For Windows users, Livox Viewer 2 may fail to detect LiDAR sensors if Windows Firewall is turned on. In this situation, go to the Control Panel to turn off Windows Firewall and restart Livox Viewer 2.

For Windows users: Unzip the Livox Viewer 2 file and click to open the .exe file named "Livox Viewer 2".

Ubuntu users: unzip the Livox Viewer 2 file and click to open the "./livox\_viewer\_2.sh" file under the root directory.

For more information, download the Livox Viewer 2 User Manual from the official website [www.livox.com](http://www.livox.com/).

### **Software Development Kit (SDK)** <a href="#block-38fd4c79856d80dabf4ed603ac6638aa" id="block-38fd4c79856d80dabf4ed603ac6638aa"></a>

Besides using Livox Viewer 2 to check real-time point cloud data, users can also use the SDK to apply the point cloud acquired from Livox LiDAR sensors to different scenarios.

**SDK Communication Protocol**

With the SDK Communication Protocol, users can learn how to customize the Livox LiDAR sensors. The SDK Communication Protocol encompasses the following three types of data:

* Control Command Data
* Point Cloud Data
* Log Data

All data is stored in little-endian format.

Visit [http://www.livoxtech.com/sdk](http://www.livoxtech.com/sdk) for more information about SDK communication protocol and Livox SDK API reference.

## **Storage, Transportation, and Maintenance** <a href="#block-38fd4c79856d80aabd94ffe0adecc66b" id="block-38fd4c79856d80aabd94ffe0adecc66b"></a>

### **Storage** <a href="#block-38fd4c79856d80a5b18fc11bf805100c" id="block-38fd4c79856d80a5b18fc11bf805100c"></a>

The storage temperature range for the HAP (TX) LiDAR is from -40° to 95° C (-40° to 203° F). Keep HAP (TX) LiDAR sensors in a dry and dust-free environment.

* Make sure the HAP (TX) LiDAR is not exposed to environments containing poisonous or corrosive gases or materials.
* DO NOT drop the HAP (TX) LiDAR and be careful when placing in or taking out of storage.
* If a HAP (TX) LiDAR sensor is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

### **Transportation** <a href="#block-38fd4c79856d80bfa7d0fe6d4c18882b" id="block-38fd4c79856d80bfa7d0fe6d4c18882b"></a>

* Before transportation, place HAP (TX) LiDAR sensors in a suitable box and make sure it is secure.
* Make sure to place foam inside the transportation box and that the box is clean and dry.
* DO NOT drop the HAP (TX) and be careful when carrying it.

### **Maintenance** <a href="#block-38fd4c79856d80469553c8370acc6ccf" id="block-38fd4c79856d80469553c8370acc6ccf"></a>

In normal conditions, the only maintenance required for the HAP (TX) is to clean the optical window of the LiDAR sensor. Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor.

First, check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. Use compressed or canned air:

DO NOT wipe a dusty optical window as it will only cause more damage. Clean the optical window with compressed or canned air before wiping the optical window.

💡

**Note:**

Note that if the optical window has no visible stains afterward, it is unnecessary to wipe it.

2. Wipe the stains:

DO NOT wipe using a dry lens tissue, as it will scratch the surface of the optical window. Use a lens tissue and dampen with isopropyl alcohol.

If the optical window is still dirty, a mild soap solution can be used to gently wash the window. Repeat Step 2 to remove any remaining soap residue.

## **Troubleshooting** <a href="#block-38fd4c79856d80bb9274cc6989513a51" id="block-38fd4c79856d80bb9274cc6989513a51"></a>

The table below shows you how to troubleshoot and resolve common issues with HAP (TX) LiDAR sensors. If the issue persists, contact Livox.

| **Issue**                                                          | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cannot detect the LiDAR sensor                                     | • Make sure that all cables are correctly wired. • Make sure the voltage is suitable. The working voltage range for HAP (TX) is between 9 to 18 V. Make sure the voltage of the external power source is within the allowable range and the positive and negative ends of the power cable are connected correctly. • Make sure that the LiDAR sensor is not connected to other software. • Make sure that the LiDAR sensor and the host PC is connected to the same LAN. • Make sure no security software is installed that would block Ethernet broadcasts. If the issue persists, turn off all firewalls, restart the Livox Viewer 2 and try again. Confirm the UDP packets of all connected devices using another application (e.g., Wireshark). |
| Cannot connect to the detected LiDAR sensor/ Cannot start sampling | • Make sure that all cables are correctly wired. • Make sure the voltage is suitable. The working voltage range for HAP (TX) is from 9 to 18 V. Make sure the voltage of the external power source is within the allowable range and the positive and negative ends of the power cable are connected correctly. If the issue persists, reboot the LiDAR sensor and restart the Livox Viewer 2.                                                                                                                                                                                                                                                                                                                                                      |
| No data received                                                   | Confirm the UDP packets of all connected devices using another application (e.g., Wireshark).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

## **After-Sales Information** <a href="#block-38fd4c79856d8050a657c7a42f897288" id="block-38fd4c79856d8050a657c7a42f897288"></a>

Visit [www.livoxtech.com/support](http://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox LiDAR sensors.

## Appendix <a href="#block-38fd4c79856d80f4aae1c70ffc8e43e3" id="block-38fd4c79856d80f4aae1c70ffc8e43e3"></a>

### HAP (TX) Dimensions <a href="#block-38fd4c79856d8095b05fca053359860a" id="block-38fd4c79856d8095b05fca053359860a"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0f00d9a2-4ef2-4e22-b4d8-70bc0cb38b55/image/w=1920,quality=90,fit=scale-down" alt="image" height="994.3225258587341" width="724.8250122070312">

## Specifications <a href="#block-38fd4c79856d8030b080db77b7cffba6" id="block-38fd4c79856d8030b080db77b7cffba6"></a>

| Model                         | HAP (TX)                                                                                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Laser Wavelength              | 905 nm                                                                                                                                      |
| Laser Safety¹                 | Class 1 (IEC 60825-1:2014) (safe for eyes)                                                                                                  |
| Detection Range (@100 klx)²   | 150 m @ 10% reflectivity                                                                                                                    |
| FOV                           | 120° (horizontal) × 25° (vertical)                                                                                                          |
| Distance Random Error (1σ)³   | < 2 cm @ 20 m (80% reflectivity)                                                                                                            |
| Distance System Error         | < ±3 cm @ 20 m                                                                                                                              |
| Angular Random Error (1σ)     | < 0.1°                                                                                                                                      |
| Beam Divergence               | 0.03° (horizontal) × 0.28° (vertical)                                                                                                       |
| Point Rate                    | 452,000 points/s                                                                                                                            |
| Data Port                     | 100BASE-TX Ethernet                                                                                                                         |
| Data Synchronization          | gPTP                                                                                                                                        |
| False Alarm Ratio (@100 klx)⁴ | 0.01%                                                                                                                                       |
| Operation Temperature Range   | -40°C to 85°C (-40° to 185°F)                                                                                                               |
| Storage Temperature Range     | -40°C to 95°C (-40° to 203°F)                                                                                                               |
| IP Rating                     | IP67                                                                                                                                        |
| Power⁵                        | Rated power 12 W                                                                                                                            |
|                               | Startup power 26 W                                                                                                                          |
|                               | Low temperature heating power 40 W                                                                                                          |
| Power Supply Voltage Range⁶   | 9-18 V DC For versions that support 9-32 V DC power supply voltage, please contact Livox or submit a request via www.livoxtech.com/contact. |
| Noise                         | < 45 dB(A) (40 cm omnidirectional)                                                                                                          |
| Dimensions                    | 105 × 131.6 × 65 mm                                                                                                                         |
| Weight                        | Approx. 1120 g                                                                                                                              |

① The divergence of the embedded laser is approximately 25.2° (horizontal) × 8° (vertical), which was measured at full width at half maximum. The maximum power of the embedded laser may exceed 65W. In order to avoid being injured by the laser, DO NOT disassemble HAP (TX). ② HAP (TX) cannot precisely detect objects which are less than 0.5m away. ③ Tested in an environment at a temperature of 25°C (77°F). The actual environment may differ from the testing environment. The figure listed is for reference only. The point cloud may distort to a varying extent when the target object is within the range of 0.5 to 2 m. ④ The false alarm ratio of the noise created by the stray light in a test environment of 100 klx at a temperature of 25°C (77°F). ⑤ The rated power and startup power are tested in an environment at a temperature of 25°C (77°F). In low-temperature environments, HAP (TX) will first enter self-heating mode, and its power may reach a maximum amount of 40W. Make sure the power supply is suitable based on the peak power value of HAP (TX). ⑥ Make sure the output voltage of the power supply is within this range at all times.
