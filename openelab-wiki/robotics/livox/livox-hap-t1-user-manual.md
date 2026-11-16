# LIVOX HAP(T1) User Manual

> LIVOX HAP (T1) User Manual

{% embed url="https://openelab.io/products/livox-hap-automotive-grade-lidar3d?variant=46043733622982" %}

## **Product Profile** <a href="#block-389d4c79856d8058b038d332cbd322ef" id="block-389d4c79856d8058b038d332cbd322ef"></a>

### **Introduction** <a href="#block-389d4c79856d80f38b1fe96a03b74d72" id="block-389d4c79856d80f38b1fe96a03b74d72"></a>

Livox HAP features a long detection range, high precision, wide field-of-view (FOV), and high reliability. It can be used for multiple applications, including autonomous driving, robots, automated guided vehicles, and unmanned aircraft. Livox HAP has two models, which are HAP (T1) and HAP (TX). This document is intended for HAP (T1).

**High FOV Coverage:** The HAP (T1) utilizes Livox's unique non-repetitive scanning technology and multi-laser and multi-APD DL-Pack technology, which can quickly detect every detail inside the FOV.

**Wide FOV:** The HAP (T1) has a rectangular FOV of 120° horizontally and 25° vertically. The HAP (T1) scans horizontally from top to bottom, increasing its compatibility with algorithms used to process common point cloud data.

**High Reliability:** The HAP (T1) offers enhanced reliability as the cutting-edge design works normally without rotating internal electronic devices such as the transmitter and receiver.

**Environmental Adaptation:** Even under 100 kilolux conditions, the HAP (T1) boasts a low noise rate below 0.01%. The HAP (T1) can effectively reduce interference from other LiDAR sensors thanks to the innovative de-noising algorithms built into the unit.

**User-Friendly Livox Viewer 2:** Livox Viewer 2 is software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

**Open Source Livox SDK:** A software development kit (SDK) is provided to help develop customizable applications using the data acquired from the point cloud data. Livox SDK supports Windows/Linux/Mac OS/ROS.

💡

**Note：**

* The HAP (T1) has a detection range of up to 200 m, which can be reached when the target object reflects 35% of light or more. For reference, grey concrete walls and roads have a reflectivity range from 15 to 30%, while white plaster walls have a reflectivity range from 90 to 99% in an environment with a temperature of 25° C (77° F).
* Before using for the first time remove the screen protector from the optical window.

### **Product Characteristics** <a href="#block-389d4c79856d80ec8e36d998926633db" id="block-389d4c79856d80ec8e36d998926633db"></a>

The HAP (T1) utilizes Livox's unique non-repetitive scanning technology and multi-laser and multi-APD DL-Pack technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surroundings.

Figure 1.2.1 displays the point cloud allocation of the HAP (T1) inside the FOV within 0.1s. In the center of the FOV, the scanning density is denser, with the average spacing of lines being 0.2° (most line spacing is from 0.1 to 0.3°), which is much denser than traditional 64-line LiDAR sensors. The two areas on both sides have a lower scanning density and average spacing lines of 0.3° (most line spacing is between 0.2 to 0.5°), rivaling traditional 64-line LiDAR sensors within 0.1 seconds.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c5d24fe2-c47c-4138-a940-482803f08665/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.1 Point Cloud Allocation of the HAP (T1) within 0.1s (coordinates units: °)" height="190.50892863240276" width="555.9750366210938">

Figure 1.2.1 Point Cloud Allocation of the HAP (T1) within 0.1s (coordinates units: °)

Figure 1.2.2 displays the point cloud patterns of the HAP (T1) with respect to different integration time.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b51ea4f6-c6db-4afb-835e-28135c57c1a8/image/w=1920,quality=90,fit=scale-down" alt="Figure 1.2.2 Point cloud patterns of the HAP (T1) accumulated over different integration time" height="97.14852855477857" width="724.8125">

Figure 1.2.2 Point cloud patterns of the HAP (T1) accumulated over different integration time

Figure 1.2.3 displays the FOV coverage of the HAP (T1) over different integration time, compared with other non-Livox LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is less than 0.1 second, the FOV coverage of the HAP (T1) is close to 80%, better than a 64-line LiDAR sensor. As the integration time increases to 0.5 seconds, the FOV coverage approaches 99%, so almost all areas are illuminated by laser beams.

![Figure 1.2.3 The FOV coverage of the HAP (T1) over different integration times compared with non-Livox LiDAR sensors using traditional mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0c62971c-1cfa-496d-a928-ea293bdfc0cf/image/w=1920,quality=90,fit=scale-down)

Figure 1.2.3 The FOV coverage of the HAP (T1) over different integration times compared with non-Livox LiDAR sensors using traditional mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.💡

&#x20;: The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams. The FOV coverage (C) can be calculated with the following formula:

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

* HAP (T1) cannot precisely detect objects which are less than 0.5 m away. In this situation, the HAP (T1) will output warning message for blocking, and the serial number of the HAP (T1) displayed on Livox Viewer 2 will change color to warn users. If used at the time, check the SDK for more information about the warning. The point cloud may distort to a varying extent when the target object is within the range of 0.5 to 2 m.
* The HAP (T1) has a detection accuracy of 2 cm when tested at a temperature of 25° C (77° F) with a target object that is 20 m away and has a reflectivity of 80%. The actual environment may differ from the testing environment. The figure listed is for reference only.
* The performance of the HAP (T1) may decrease in extreme environments, such as those where the temperature is -40° C (-40° F) or 85° C (185° F) or those that cause high vibration.

### Overview <a href="#block-389d4c79856d80809a71fe543915af56" id="block-389d4c79856d80809a71fe543915af56"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4c1fd535-ff25-4457-a836-4c7252992af2/image/w=1920,quality=90,fit=scale-down" alt="image" height="188.5761233276663" width="331.4125061035156">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7fe5b049-b5e0-448b-a69d-916bb8acd67e/image/w=1920,quality=90,fit=scale-down" alt="image" height="209.32501220703125" width="313.9875183105469">

1. **Optical Window**
2. The laser passes through the optical window and scans objects in the FOV.
3. **Locating Hole 1**
4. The locating hole makes it easy for users to find the correct place to mount a fixed support for the HAP (T1). Refer to the Dimensions section for more information.
5. **M6 Mounting Through-Hole (Φ6.5) × 4**
6. Users can mount the HAP (T1) to an appropriate place with M6 screws.
7. **Automotive Ethernet Connector (100BASE-T1)**
8. Use an Automotive Ethernet Cable (sold separately) to connect the HAP (T1) to a converter that converts 100BASE-T1 automotive Ethernet to standard 100BASE-TX Ethernet for quick testing and debugging of the HAP (T1). Users need to purchase a suitable converter separately. Users can use customized cables according to the pinout reference table to improve the waterproof and dustproof protection ability of the HAP(T1). Refer to the Connectors section for more information on the automotive Ethernet connector.
9. **Power Connector**
10. Connect to an external DC power supply using the power cable (sold separately). Users can use customized cables according to the pinout reference table to improve the waterproof and dustproof protection ability of the HAP (T1). Refer to the Connectors section for more information on the power connector.
11. **M3 Mounting Hole × 4**
12. Users can mount the HAP (T1) to an appropriate place with M3 screws.
13. **Locating Hole 2**
14. The locating hole makes it easy for users to find the correct place to mount a fixed support for the HAP (T1). Refer to the Dimensions section for more information.
15. **Waterproof Breathable Valve**
16. The waterproof breathable valve can help balance the pressure difference between the inside and outside of the HAP (T1).

💡

Visit the DJl official store to purchase the HAP (T1) wire pack. The wire pack contains a power cable and an automotive Ethernet cable. These cables are for testing and debugging only. It is recommended for users to customize cables and connectors of their own for scenarios that have high-reliability requirements.

## **Connectors** <a href="#block-389d4c79856d804c9548f46962a11d51" id="block-389d4c79856d804c9548f46962a11d51"></a>

### **Power Connector and Automotive Ethernet Connector** <a href="#block-38ad4c79856d8047b02fc58e091f7a69" id="block-38ad4c79856d8047b02fc58e091f7a69"></a>

The HAP (T1) includes a power connector and an automotive Ethernet connector. Users can connect the HAP (T1) with the power cable and the automotive Ethernet cable (both cables are sold separately) to realize transmission of power, control signals and data. Users can also customize cables of their own to improve the waterproof and dustproof protection of the HAP (T1).

**Power Connector and Automotive Ethernet Connector of HAP (T1)**

See below for more information on the power connector and the automotive Ethernet connector of HAP (T1).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4b032bea-e729-41c6-8531-166b5e720f6e/image/w=1920,quality=90,fit=scale-down" alt="image" height="160.5078433365772" width="270.9750061035156">

| **Pin** | **Signal** | **Type**     | **Description** | **Function**                                                                                               |
| ------- | ---------- | ------------ | --------------- | ---------------------------------------------------------------------------------------------------------- |
| 1       | Power+     | Power        | DC VCC          | Power Cable (connects to DC power supply)                                                                  |
| 4       | Ground     | Power        | Ground          |                                                                                                            |
| 7       | MDI+       | Input/Output | 100Base-T1      | Automotive Ethernet Cable (connects to automotive Ethernet devices)                                        |
| 8       | MDI-       | Input/Output | 100Base-T1      |                                                                                                            |
| 2       | N/A        | N/A          | N/A             | Function Cable (Not in use. DO NOT connect with other power cable or signal cable to avoid short circuit.) |
| 3       | N/A        | N/A          | N/A             |                                                                                                            |
| 5       | N/A        | N/A          | N/A             |                                                                                                            |
| 6       | N/A        | N/A          | N/A             |                                                                                                            |

**Power Cable**

Connect A to the power connector of HAP (T1), and the connector type for A is TE 1-967616-1. Connect B to an external DC power supply, and the connector type for B is XT30.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/46dcc57d-8421-4a34-beda-2ea37b651ce7/image/w=1920,quality=90,fit=scale-down" alt="image" height="91.92423230974633" width="724.75">

**Automotive Ethernet Cable**

Connect A to the automotive Ethernet connector of HAP (T1), and the connector type for A is TE 1802105-1. Connect B to the automotive Ethernet connector of an automotive Ethernet converter, and the connector type for B is MOLEX 347910040.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7c33197a-8c96-4040-904b-3ac2a32986e0/image/w=1920,quality=90,fit=scale-down" alt="image" height="92.6492723244008" width="724.7875366210938">

## **Mounting the HAP (T1)** <a href="#block-38ad4c79856d807c824bea03b8471661" id="block-38ad4c79856d807c824bea03b8471661"></a>

### **Effective FOV Range** <a href="#block-389d4c79856d80fb87b1ff11fcb6a018" id="block-389d4c79856d80fb87b1ff11fcb6a018"></a>

As shown below, the HAP (T1) has a FOV of 120° horizontally and 25° vertically. When mounting the sensor, make sure that the FOV is not blocked by any objects. Visit [www.livoxtech.com/hap](http://www.livoxtech.com/hap) to download the 3D model of the HAP (T1) and its FOV.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ec8711a7-6fd1-474e-9a3f-bd726bc95ade/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.1.1 Effective FOV of the HAP (T1)" height="267.80914779499403" width="724.8125">

Figure 3.1.1 Effective FOV of the HAP (T1)

Note that the HAP (T1) effective detection range varies based on where the object is within the FOV. The closer to the edge of the FOV, the shorter the effective detection range is. The closer to the center of the FOV, the farther the effective detection range. Refer to the diagrams below. Pay attention to the effective detection range when in use.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/33256feb-90f8-4c4c-b758-eafe6df9da9f/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.1.2 Effective Detection Range inside FOV of the HAP (T1)" height="352.4116353700415" width="724.8250122070312">

Figure 3.1.2 Effective Detection Range inside FOV of the HAP (T1)

As shown above, when an object with a reflectivity of 10% is placed near the border of the vertical FOV, the object can be detected as far as 125m.

### Mounting Notice <a href="#block-38ad4c79856d804c8253f4ec91454212" id="block-38ad4c79856d804c8253f4ec91454212"></a>

Read and understand the following warnings before mounting the HAP(T1):

1. Before use, remove the screen protector from the optical window.
2. Significant dust and stains on the optical window will affect the performance of the LiDAR sensor. Follow the instructions in the Maintenance section to clean the optical window using compressed air, isopropyl alcohol, or a lens cloth. Mount the HAP (T1) after cleaning it.
3. When mounting the HAP (T1), the field of view must not be blocked by an object, including glass. Refer to Figure 3.1.1.
4. When mounting the HAP (T1), allow a space of at least 10 mm around the device to prevent poor airflow affecting heat dissipation, and make sure the waterproof breathable valve is not blocked.
5. The HAP (T1) cannot bear any extra payload. Otherwise, the reliability of the product cannot be guaranteed.

### **Dimensions** <a href="#block-38ad4c79856d8014af50fb6f150d21cd" id="block-38ad4c79856d8014af50fb6f150d21cd"></a>

The bottom surface of the HAP (T1) has four M3 mounting holes with a depth of 5 mm, and four M6 mounting through-holes (Φ6.5). Refer to the below illustrations for HAP (T1) dimensions and locations for the mounting holes, and mount the HAP (T1) in an appropriate place.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e6d82e0a-52d5-46f1-bd1a-adc455e7658a/image/w=1920,quality=90,fit=scale-down" alt="Figure 3.2.1 HAP (T1) Dimensions (refer to Appendix 1)" height="405.6970989761092" width="724.8125">

Figure 3.2.1 HAP (T1) Dimensions (refer to Appendix 1)

Table 3.2.1 HAP (T1) Weight and Dimensions

| **Weight** | **Approx. 1120 g**  |
| ---------- | ------------------- |
| Dimensions | 105 × 131.6 × 65 mm |

## **Getting Started** <a href="#block-389d4c79856d802da265fb5f7302ec31" id="block-389d4c79856d802da265fb5f7302ec31"></a>

### **External Power Supply** <a href="#block-389d4c79856d80c38b80d9c405a820d4" id="block-389d4c79856d80c38b80d9c405a820d4"></a>

The working voltage range of the HAP (T1) is from 9 to 18V, the recommended working voltage is 12V. The minimum working voltage should be increased in a low-temperature environment. When the HAP (T1) is connected to an external power source directly through the M12 aviation connector, make sure the output voltage range of the external power source is within the operating voltage range of the HAP (T1). When an extension cable is required, make sure to increase the output voltage of the external power source due to the extra voltage reduction. Make sure the maximum voltage does not exceed 18V. Note that the power cable may generate voltage fluctuation where the voltage exceeds 18V in some scenarios, such as if the power cable is interfered with or other devices connected to another power source in the parallel circuit suddenly power off. In such scenarios, the HAP (T1) may not work normally or even be damaged.

The HAP (T1) has a working power of 10W when working normally at a temperature of 25°C. The working power varies depending on each sensor, but the maximum working power does not exceed 12W. In low-temperature or high-temperature environments, the startup power of HAP (T1) may reach 40W. In an environment where the temperature is below 0°C, the HAP (T1) will enter self-heating mode automatically. The lower the temperature, the greater the power. Additionally, the HAP (T1) supports the window-heating mode, which can be used for defrosting and defogging the window. Users can choose to turn on or off the window-heating mode based on their needs. In window-heating mode, the working power may increase by 10W. The working power of the HAP (T1) var ies at different temperatures. Make sure the power supply is suitable based on the peak power of the HAP (T1). The value is for reference only. In normal conditions, the peak power varies depending on each sensor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2b140635-579b-49dc-889a-2be5769828da/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.1.1 The working power of the HAP (T1) at different temperatures" height="269.76245995338974" width="724.8250122070312">

Figure 4.1.1 The working power of the HAP (T1) at different temperatures

### **Connection** <a href="#block-38ad4c79856d8061bec7f13cf554e7c9" id="block-38ad4c79856d8061bec7f13cf554e7c9"></a>

All HAP (T1) are set to static IP address mode by default with an IP address of 192.168.1.100. The default subnet masks of HAP (T1) are 255.255.255.0 and their default gateways are 192.168.1.1. To connect with a computer for testing and debugging, users need to purchase a converter that can convert from 100BASE-T1 automotive Ethernet to standard 100BASE-TX Ethernet, and the automotive Ethernet module of the converter needs to work in Master mode when connected to HAP (T1). Make sure the converter you purchase meets the specified requirements.

1. Before connecting, set the IP address of the computer to static IP address mode. Set the IP address of the computer to the same network subnet as the IP address of HAP (T1). Follow the steps to set the IP address of your computer to static IP address:

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

2. Connect HAP (T1) as shown below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a76b1c3d-e6ee-45fb-b3fd-01ab13d7d3e7/image/w=1920,quality=90,fit=scale-down" alt="Figure 4.2.1 Connecting the HAP (T1)" height="170.63467940750655" width="724.7750244140625">

Figure 4.2.1 Connecting the HAP (T1)

1. Connect one end of the automotive Ethernet cable to the automotive Ethernet connector of HAP (T1), and connect the other end to the automotive Ethernet connector of the converter.
2. Connect one end of the power cable to the power connector of HAP (T1), and connect the other end to an external power supply.
3. Connect the converter to an external power supply.
4. Connect the converter to the computer using an Ethernet cable.
5. Set the automotive Ethernet module of the converter to Master mode. For the specific setup method, refer to the usage instructions for the purchased converter.

💡

**Note:**

* When multiple HAP (T1) LiDAR sensors are connected to one computer in static IP address mode, make sure all sensors connected have different static IP addresses. Refer to Livox HAP User Manual for more information on how to set the IP address for each LiDAR sensor.
* If more than six HAP (T1) LiDAR sensors are required, use a gigabit router or an switch.
* The broadcast number for each LiDAR sensor can be viewed in the Device Manager of Livox Viewer 2 or the Livox SDK. For the HAP (T1), the broadcast number will be its serial number ending in an additional "1".
* Launch Livox Viewer 2 after the HAP (T1) is connected. Click the device with the static IP address that should be altered. Click to open the settings page and set the static IP address of the HAP (T1).

## **Usage** <a href="#block-38ad4c79856d808ebf50f57ea3d628dd" id="block-38ad4c79856d808ebf50f57ea3d628dd"></a>

### **Coordinates** <a href="#block-38ad4c79856d80debe35d2161797e5c1" id="block-38ad4c79856d80debe35d2161797e5c1"></a>

The coordinates of the HAP (T1) are defined as shown below.

**Positioning Coordinates O'- X'Y'Z':** Point O' is the intersection point between the bottom surface and the locating hole 1. The Z' axis is the normal vector perpendicular to the bottom surface, and the X' axis is the normal vector perpendicular to the optical window surface.

**Point Cloud Coordinates O- XYZ:** Point O is the center of the optical window surface, and its coordinates directions are the same with that of the Positioning Coordinates.

The position and pose relation of the point cloud coordinate system relative to the positioning coordinate system is: (X, Y, Z, Roll, Pitch, Yaw) >> (8mm, 0 mm, 23 mm, 0°, 0°, 0°)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/db8dd328-07e2-41fe-875f-32858e28a60e/image/w=1920,quality=90,fit=scale-down" alt="Figure 5.1.1 HAP (T1) Coordinates" height="296.0295039797292" width="395.9875183105469">

Figure 5.1.1 HAP (T1) Coordinates

### **Output Data** <a href="#block-38ad4c79856d8022afdedc49f0b6e848" id="block-38ad4c79856d8022afdedc49f0b6e848"></a>

The output information of HAP (T1) LiDAR sensors includes:

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

Group 2 indicates the return sequence of the sampling point. Featuring a coaxial optical path, the HAP (T1) LiDAR sensor will generate a laser return even if there is no detectable object around. The return is recorded as return 0. After that, if there is any object within the detectable range, the first laser that returns to the HAP (T1) is recorded as return 1, and then return 2, and so on. If the object is too close to the HAP (T1), such as 1.5 m away, the first effective return will be merged into return 0, and be recorded as return 0.

Group 3 indicates if the sampling point is noise based on the intensity of the return. Normally, the intensity of the returns of the noises generated due to the interference of atmospheric particles such as dust, rain, fog, and snow is relatively low. Therefore, sampling points are divided into two categories based on the intensity of the return received: "00" represents a normal return; "01" represents a low-intensity return, indicating that the sampling points have a high possibility of being noise such as dust, rain and fog. It is recommended that users use the sampling points whose return intensity is "00".

Group 4 indicates if the sampling point is noise based on its spatial position. Normally, when the HAP (T1) LiDAR sensors detect two objects in close proximity of each other, there will be some thread-like noise between the two objects.

**Timestamp**

The HAP (T1) only supports the Generic Precision Time Protocol (gPTP) based on IEEE 802.1AS standard, where the domain controller works as the master, and the HAP (T1) as the slave:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5d6cdeb8-15dc-4b8f-8b1f-518c1b7ab1e0/image/w=1920,quality=90,fit=scale-down" alt="image" height="420.1542105585256" width="356.9875183105469">

Calculate the transmission delay by following the steps above:

link\_delay = \[(t4 - t1) - (t3 - t2)] / 2

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ef243482-2b1a-4f6d-b8b6-9758822a69b5/image/w=1920,quality=90,fit=scale-down" alt="image" height="353.2596341340438" width="443.9875183105469">

Calculate offset with sync and follow\_up:

offset = (t2' - t1') - link\_delay

The AUTOSAR standard Specification of Time Synchronization over Ethernet includes the special requirements for IEEE 802.1AS in automotive applications, such as:

* No support of Announce messages.
* No support for Best Master Clock Algorithm (BCMA).
* Master does not send delay\_req message.

As the time synchronization method of HAP (T1) integrates AUTOSAR gPTP, HAP (T1) follows above requirements.

**Control Command ACK**

Master sends control commands to the HAP (T1). HAP (T1) sends ACK messages once receiving the control command. Refer to the Control Command section in the SDK Communication Protocols for specific information.

**Information Push**

In normal conditions, the HAP (T1) pushes status information at 1 Hz (such as the status of the LiDAR sensor, error code, flash status); In abnormal conditions, the HAP (T1) keeps pushing status information at 100Hz for 100 ms for users to quickly recognize the error and take action.

The HAP (T1) will automatically push log data once anything abnormal happens. Users need to save these log data and provide them to Livox Support for analysis. Contact Livox Support for detailed definitions of the messages indicating abnormal situations.

### **Livox Viewer 2** <a href="#block-38ed4c79856d80fca6cfff818c93e06d" id="block-38ed4c79856d80fca6cfff818c93e06d"></a>

Livox Viewer 2 is software specially designed for Livox LiDAR sensors. It displays and records real-time point cloud data, replays point cloud videos and analyzes the 3D point cloud data. Users can set product parameters and calibrate extrinsics using Livox Viewer 2. The simple interface makes it easy to use.

Visit [www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer 2. Livox Viewer 2 supports Windows® 10 (64 bit) and Ubuntu™ 18.04 (64 bit). Follow the steps below to use the Livox Viewer 2.

For Windows users, Livox Viewer 2 may fail to detect LiDAR sensors if Windows Firewall is turned on. In this situation, go to the Control Panel to turn off Windows Firewall and restart Livox Viewer 2.

For Windows users: Unzip the Livox Viewer 2 file and click to open the .exe file named "Livox Viewer 2".

Ubuntu users: unzip the Livox Viewer 2 file and click to open the "./livox\_viewer\_2.sh" file under the root directory.

For more information, download the Livox Viewer 2 User Manual from the official website [www.livox.com](http://www.livox.com/).

### **Software Development Kit (SDK)** <a href="#block-38ed4c79856d800ab365ff61f77c7f97" id="block-38ed4c79856d800ab365ff61f77c7f97"></a>

Besides using Livox Viewer 2 to check real-time point cloud data, users can also use the SDK to apply the point cloud acquired from Livox LiDAR sensors to different scenarios.

**SDK Communication Protocol**

With the SDK Communication Protocol, users can learn how to customize the Livox LiDAR sensors. The SDK Communication Protocol encompasses the following four types of data:

* Control Command Data
* Point Cloud Data
* Log Data

All data is stored in little-endian format.

Visit [http://www.livoxtech.com/sdk](http://www.livoxtech.com/sdk) for more information about SDK communication protocol and Livox SDK API reference.

## **Storage, Transportation, and Maintenance** <a href="#block-38ed4c79856d80dc8e75c38de73044f4" id="block-38ed4c79856d80dc8e75c38de73044f4"></a>

### **Storage** <a href="#block-38ed4c79856d8098a10ecf19e5b77d40" id="block-38ed4c79856d8098a10ecf19e5b77d40"></a>

The storage temperature range for the HAP (T1) LiDAR is from -40° to 95° C (-40° to 203° F). Keep HAP (T1) LiDAR sensors in a dry and dust-free environment.

* Make sure the HAP (T1) LiDAR is not exposed to environments containing poisonous or corrosive gases or materials.
* DO NOT drop the HAP (T1) LiDAR and be careful when placing in or taking out of storage.
* If a HAP (T1) LiDAR sensor is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

### **Transportation** <a href="#block-38ed4c79856d8002a5f4ca2e4858e025" id="block-38ed4c79856d8002a5f4ca2e4858e025"></a>

* Before transportation, place HAP (T1) LiDAR sensors in a suitable box and make sure it is secure.
* Make sure to place foam inside the transportation box and that the box is clean and dry.
* DO NOT drop the HAP (T1) and be careful when carrying it.

### **Maintenance** <a href="#block-38ed4c79856d8050bb71d5defb412543" id="block-38ed4c79856d8050bb71d5defb412543"></a>

In normal conditions, the only maintenance required for the HAP (T1) is to clean the optical window of the LiDAR sensor. Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor.

First, check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. Use compressed or canned air:

DO NOT wipe a dusty optical window as it will only cause more damage. Clean the optical window with compressed or canned air before wiping the optical window.

💡

Note that if the optical window has no visible stains afterward, it is unnecessary to wipe it.

2. Wipe the stains:

DO NOT wipe using a dry lens tissue, as it will scratch the surface of the optical window. Use a lens tissue and dampen with isopropyl alcohol.

If the optical window is still dirty, a mild soap solution can be used to gently wash the window. Repeat Step 2 to remove any remaining soap residue.

## **Troubleshooting** <a href="#block-38ed4c79856d80e79cccebce3c746bc5" id="block-38ed4c79856d80e79cccebce3c746bc5"></a>

The table below shows you how to troubleshoot and resolve common issues with HAP (T1) LiDAR sensors. If the issue persists, contact Livox.

| **Issue**                                                          | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cannot detect the LiDAR sensor                                     | • Make sure that all cables are correctly wired. • Make sure the voltage is suitable. The working voltage range for HAP (T1) is between 9 to 18 V. Make sure the voltage of the external power source is within the allowable range and the positive and negative ends of the power cable are connected correctly. • Make sure that the LiDAR sensor is not connected to other software. • Make sure that the LiDAR sensor and the host PC is connected to the same LAN. • Make sure no security software is installed that would block Ethernet broadcasts. If the issue persists, turn off all firewalls, restart the Livox Viewer 2 and try again. Confirm the UDP packets of all connected devices using another application (e.g., Wireshark). |
| Cannot connect to the detected LiDAR sensor/ Cannot start sampling | • Make sure that all cables are correctly wired. • Make sure the voltage is suitable. The working voltage range for HAP (T1) is from 9 to 18 V. Make sure the voltage of the external power source is within the allowable range and the positive and negative ends of the power cable are connected correctly. If the issue persists, reboot the LiDAR sensor and restart the Livox Viewer 2.                                                                                                                                                                                                                                                                                                                                                      |
| No data received                                                   | Confirm the UDP packets for all connected devices using another application (e.g., Wireshark)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

## **After-Sales Information** <a href="#block-38ed4c79856d80f097c2f3f5d367254e" id="block-38ed4c79856d80f097c2f3f5d367254e"></a>

Visit [www.livoxtech.com/support](http://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox LiDAR sensors.

## Appendix <a href="#block-38ed4c79856d809b8908dcfd265329e6" id="block-38ed4c79856d809b8908dcfd265329e6"></a>

### HAP (T1) Dimensions <a href="#block-38ed4c79856d80239d06c88e1a04fab0" id="block-38ed4c79856d80239d06c88e1a04fab0"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/426b8e42-3695-4b2f-8878-94a6c8405c57/image/w=1920,quality=90,fit=scale-down" alt="image" height="1087.7051473506806" width="724.8250122070312">

## Specifications <a href="#block-38ed4c79856d80359ff6e6e65c02d655" id="block-38ed4c79856d80359ff6e6e65c02d655"></a>

| Model                         | HAP (T1)                                   |
| ----------------------------- | ------------------------------------------ |
| Laser Wavelength              | 905 nm                                     |
| Laser Safety¹                 | Class 1 (IEC 60825-1:2014) (safe for eyes) |
| Detection Range (@100 klx)²   | 150 m @ 10% reflectivity                   |
| FOV                           | 120° (horizontal) × 25° (vertical)         |
| Distance Random Error (1σ)³   | < 2 cm @ 20 m (80% reflectivity)           |
| Distance System Error         | < ±3 cm @ 20 m                             |
| Angular Random Error (1σ)     | < 0.1°                                     |
| Beam Divergence               | 0.03° (horizontal) × 0.28° (vertical)      |
| Point Rate                    | 452,000 points/s                           |
| Data Port                     | 100BASE-T1 Automotive Ethernet             |
| Data Synchronization          | gPTP                                       |
| False Alarm Ratio (@100 klx)⁴ | < 0.01%                                    |
| Operation Temperature Range   | -40°C to 85°C (-40° to 185°F)              |
| Storage Temperature Range     | -40°C to 95°C (-40° to 203°F)              |
| IP Rating                     | IP67⁵                                      |
| Power⁶                        | Rated power 12 W                           |
|                               | Startup power 26 W                         |
|                               | Low temperature heating power 40 W         |
| Power Supply Voltage Range⁷   | 9-18 V DC                                  |
| Noise                         | < 45 dB(A) (40 cm omnidirectional)         |
| Dimensions                    | 105 × 131.6 × 65 mm                        |
| Weight                        | Approx. 1120 g                             |
| IMU                           | Not supported.                             |

① The divergence of the embedded laser is approximately 25.2° (horizontal) × 8° (vertical), which was measured at full width at half maximum. The maximum power of the embedded laser may exceed 65 W. In order to avoid being injured by the laser, DO NOT disassemble HAP (T1). ② HAP (T1) cannot precisely detect objects which are less than 0.5 m away. ③ Tested in an environment at a temperature of 25° C (77° F). The actual environment may differ from the testing environment. The figure listed is for reference only. The point cloud may distort to a varying extent when the target object is within the range of 0.5 to 2 m. ④ The false alarm ratio of the noise created by the stray light in a test environment of 100 klx at a temperature of 25° C (77° F). ⑤ HAP (T1) can achieve an IP rating of IP67 when connected with the power and automotive Ethernet cables. If not connected to the two cables, the IP rating for HAP (T1) is IP54. ⑥ The rated power and startup power are tested in an environment at a temperature of 25° C (77° F). In low-temperature environments, HAP (T1) will first enter self-heating mode, and its power may reach a maximum amount of 40 W. Make sure the power supply is suitable based on the peak power value of HAP (T1). ⑦ Make sure the output voltage of the power supply is within this range at all times.
