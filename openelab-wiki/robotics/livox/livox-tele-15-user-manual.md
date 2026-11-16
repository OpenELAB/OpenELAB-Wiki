# LIVOX TELE-15 User Manual

> **LIVOX TELE-15 User Manual**

{% embed url="https://openelab.io/products/livox-tele-15-lidar-highaccuracy" %}

## **Product Overview** <a href="#block-deebe38e0fc14149bfd102f4d771dc32" id="block-deebe38e0fc14149bfd102f4d771dc32"></a>

### **Introduction** <a href="#block-80988bd2336c4bd2bd5a1a4f93c5f297" id="block-80988bd2336c4bd2bd5a1a4f93c5f297"></a>

The Livox Tele-15 (hereinafter referred to as “Tele-15”) features long range, high accuracy, and high reliability, making it widely applicable in fields such as high-speed autonomous driving, rail transportation, surveying and mapping, and security.

**High Field of View Coverage**: The Tele-15 utilizes Livox’s proprietary high-speed non-repetitive scanning technology and custom-designed multi-line encapsulated lasers, achieving point cloud FOV coverage five times that of the Mid-40 within the same time frame, enabling rapid capture of every detail within the field of view.

**Ultra-Long Range**: Through industry-leading optoelectronic design, the Tele-15 achieves an extremely high signal-to-noise ratio. Its built-in high-sensitivity functionality enables detection of objects with 10% reflectivity at distances up to 320 m under 100 klx illumination.

**High Stability and Reliability**: The Tele-15 employs an advanced system design that eliminates the need for rotating electronic components such as transmitting and receiving devices, significantly enhancing product reliability. The Tele-15 has undergone rigorous testing and meets IP67 dustproof and waterproof protection levels (excluding external connectors and cables) in accordance with GB 4208-2008 (domestic) / IEC 60529 (international) standards.

**Adaptive to Environment**: The Tele-15’s built-in noise tag information helps identify the noise type and confidence level of each point cloud. The Tele-15 can resist strong ambient light interference and filter out most noise caused by direct sunlight. At temperatures above 65°C, noise filtering performance may decrease. Even under 100 klx intense sunlight interference, the noise rate of the Tele-15 remains below 0.01%.

**Built-in IMU Module**: The Tele-15 features a built-in BMI088 inertial measurement unit with a push frequency of 200 Hz.

**User-Friendly Livox Viewer Software**: Livox Viewer is an operation software that enables real-time display, recording, playback, and parsing of 3D point clouds, and also supports advanced functions such as product configuration and extrinsic parameter adjustment. Its clean interface makes it easy for users to get started.

**Open-Source Livox SDK**: Users can develop advanced algorithms based on the open-source Livox SDK, effectively improving development efficiency. The Livox SDK supports multiple development environments including Windows, Linux, Mac OS, and ROS.

💡

**Note:**

* At an ambient temperature of 25°C and with a Lambertian target reflectivity above 50% (reflectivity of concrete or pavement is 15–30%), the default maximum detection range of the Tele-15 is 500 m. Additionally, the Tele-15 supports customized components that can extend the maximum range from 500 m to 1000 m. Users with such requirements, please visit https://www.livoxtech.com/contact for technical support.
* Before use, please remove the protective film from the Tele-15 window to avoid affecting its performance.

### **Product Features** <a href="#block-e1fab209706b4242b7d442f1be075832" id="block-e1fab209706b4242b7d442f1be075832"></a>

The Tele-15 utilizes Livox’s proprietary high-speed non-repetitive scanning technology and custom-designed multi-line encapsulated lasers, achieving point cloud FOV coverage five times that of the Mid-40 within the same time frame. As the integration time increases, the point cloud FOV coverage continues to grow, enabling detection of more details within the field of view.

Figure 1.2.1 illustrates the point cloud distribution of the Tele-15 with a 0.1 s scanning pattern. The Tele-15 achieves extremely high scanning density in the central region, comparable to that of a 300-line traditional LiDAR, while outperforming 100-line LiDAR scanning coverage in other areas. Within the Tele-15’s FOV, the comprehensive scanning performance at 0.1 s is equivalent to that of a typical mechanical spinning 128-line LiDAR.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/32d60b66-c1da-49aa-977b-f1f7ac940ce9/image/w=1920,quality=90,fit=scale-down" alt="image" height="354.9146475770925" width="634.375">

According to the Livox coordinate system definition, the azimuth angle ranges from 0° to 360°, where -10° to 0° corresponds to 350° to 360°.

Figure 1.2.3 presents the FOV coverage of the Tele-15 at different integration times, compared with several common multi-line mechanical spinning LiDARs currently available on the market. It can be observed from the figure that when the integration time is 0.1 s, the FOV coverage of the Tele-15 is approximately 99%, which is higher than that of a typical 128-line mechanical spinning LiDAR.

Figure 1.2.3 FOV coverage of the Tele-15 and several common multi-line mechanical spinning LiDARs currently on the market at different integration times. The vertical FOVs for the 128-line, 64-line, 32-line, and 16-line products are 40°, 27°, 41°, and 30°, respectively.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/73ffc880-bab2-420b-adb4-690928ef82a1/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.6363690180299" width="634.3636474609375">

> The area within the field of view illuminated by the laser is related to the measurement performance of the LiDAR. To characterize this metric, the proportion of the field of view that is detected by the laser can be quantitatively expressed as the field of view coverage ©. It is calculated as follows:C=AreailluminatedbythelaserbeamsTotalareawithinthefieldofview∗100%C=TotalareawithinthefieldofviewAreailluminatedbythelaserbeams​∗100%
>
> Visit the Livox website for more information on field of view coverage.

Table 1.2.1 Point Cloud Specifications

| **Parameter**                | **Value**                                                                                                     |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Laser Wavelength             | 905 nm                                                                                                        |
| Eye Safety Level             | Class 1 (IEC 60825-1:2014) Eye Safe                                                                           |
| Range (@ 100 klx)            | 320 m @ 10% reflectivity; 500 m @ 50% reflectivity                                                            |
| FOV                          | 14.5° (H) × 16.2° (V)                                                                                         |
| Range Accuracy (1σ)          | < 2 cm (5–70 m), < 4 cm (70–120 m) @ 10% reflectivity < 2 cm (5–220 m), < 4 cm (220–380 m) @ 80% reflectivity |
| Angular Accuracy (1σ)        | < 0.03°                                                                                                       |
| Beam Divergence              | 0.02° (H) × 0.12° (V)                                                                                         |
| Point Cloud Output           | 240,000 pts/s (configurable first or strongest return) 480,000 pts/s (dual return)                            |
| False Alarm Rate (@ 100 klx) | < 0.01%                                                                                                       |

💡

**Note:**

* Tested with a Lambertian target in an environment with a temperature of 25° C (77° F), under 100 kilolux conditions with high sensitivity function enabled. The actual environment may differ from the testing environment. The figure listed is for reference only. The performance may decrease in extreme environments such as those with foggy weather, that cause strong vibration, or where the temperature is -40° C (-40° F) or 85° C (185° F).
* The built-in high sensitivity function increases the detection range of Tele-15, especially of small objects with low reflectivity. The high sensitivity function is enabled by default and can be disabled via Livox Viewer or SDK. When the environment temperature exceeds 65° C (149° F), Tele-15 reduces the sensitivity to ensure measurement accuracy. Objects with a reflectivity of 50% can be detected at a range of up to 500 meters in an environment within a temperature range of -40° to 85° C (-40° to 185° F).
* Vicinity Blind Zone: Objects that are within 2.5 meters cannot be measured precisely. When the distance from an object is less than 0.3 meters, an occlusion warning is sent by error code. The point cloud data may be distorted to a varying extent when the target object is within a range of 2.5 to 5 meters. Contact Livox for support if you require to detect objects within this range.

### OverView <a href="#block-be54778b5a734b3095c536a0c9183bc7" id="block-be54778b5a734b3095c536a0c9183bc7"></a>

**Livox Tele-15**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/46d2b29d-62d1-4e9d-9af9-0bc1c9f24af3/image/w=1920,quality=90,fit=scale-down" alt="image" height="203.2680457746479" width="634.375">

1. M3 Mounting Holes
2. The Tele-15 can be secured in place using M3 screws through these mounting holes.
3. 1/4-inch Mounting Hole
4. Compatible with platforms featuring a 1/4-inch mounting interface, such as tripods.
5. Precision Alignment Hole 1
6. Precision Alignment Hole 2
7. Active Cooling Module
8. The active cooling module is removable. After removal, please ensure that the housing temperature of the Livox Tele-15 does not exceed 85°C during use. It is recommended to operate in ambient temperatures below 65°C and avoid direct sunlight.
9. Users may also design their own cooling solutions. If overheating occurs, the Tele-15 will enter an error state and stop working; it can be restored by restarting. The active cooling module is not designed for repeated removal and installation. Please confirm the usage scenario before removing it.
10. Window
11. Laser beams are emitted through the window to scan objects within the FOV.
12. Air Outlet
13. Cooling function. When installing, ensure that the space 10 mm around the air outlet is free from obstruction.
14. Active Cooling Module Retaining Screws (M2.5)
15. There are 6 screws used to secure the cooling module, size M2.5, color black. When removing the active cooling module, please take care to store the cooling module and screws properly for possible future reinstallation.
16. Fan (Air Inlet)
17. Cooling function. When installing, ensure that the space 10 mm around the air inlet is free from obstruction.
18. M12 Aviation Connector
19. Use this connector to connect the LiDAR to the power adapter socket. Users may also configure according to the pin assignment of this connector. For the pin assignments of the M12 aviation connector, please refer to the Interface Definition section. When connecting directly to an external DC power supply via the M12 aviation connector, ensure that the output voltage of the external power supply is within the operating voltage range of the Livox Tele-15.
20. Aviation Power and Ethernet Cable

**power adapter socket 2.0**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/84465efe-0ff0-4a33-9e4e-152efc4c3797/image/w=1920,quality=90,fit=scale-down" alt="image" height="203.51785714285717" width="634.375">

1. LiDAR Connector Interface
2. Connects to the LiDAR connector. The connector model used is JAE MX34012NF1, and the corresponding LiDAR connector model is JAE MX34012SF1.
3. Power Interface
4. Connects to an external power supply. The operating voltage of the power adapter socket 2.0 is 9–30 V. Therefore, when connecting the Tele-15 to an external power supply via the power adapter socket 2.0, the external power supply output voltage is 9–30 V. The connector model used is MOLEX 105313-1102, and the corresponding wire-to-board connector model is MOLEX 105307-1202.
5. Ethernet Interface
6. Connects to an Ethernet cable. Uses a standard RJ45 Ethernet interface.
7. Sync Signal Interface
8. Connects to a sync signal cable. The sync signal interface of the power adapter socket 2.0 supports 3.3 V LVTTL level synchronization, with a 3-pin internal core. For the signal pinout, please refer to Table 2.2.2. If a custom cable is required, the corresponding wire-to-board connector is Famfull 9.510A0-003-1R0, which is compatible with JST GHR-03V-S.

## Connectors <a href="#block-0cded403b36f4f9f8bc75cb44f5a463e" id="block-0cded403b36f4f9f8bc75cb44f5a463e"></a>

### **M12 Aviation Connector** <a href="#block-5c979b60d5c0411e8a7263bab0e2c92a" id="block-5c979b60d5c0411e8a7263bab0e2c92a"></a>

The Livox Tele-15 uses a high-reliability M12 aviation plug (male connector). This plug is an M12 12P A-CODE fully shielded male connector compliant with the IEC61076-2-101 standard and meets IP67 protection requirements. Users can not only connect to the power adapter socket 2.0 via the aviation power and Ethernet cable, but can also design custom cables according to their own needs to achieve power connection, control signal transmission, and data transfer, thereby improving the system’s protection capabilities. For the cable interfacing with the LiDAR, the user side should select a corresponding M12 12P A-CODE fully shielded aviation connector (female). Please refer to the next section for the pin definitions of the female connector.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/73768aa4-90fc-466f-a390-272222019728/image/w=1920,quality=90,fit=scale-down" alt="image" height="196.0093226788432" width="634.375">

**Conversion Cable**

Users can connect the Tele-15 via the aviation power and Ethernet cable along with the power adapter socket 2.0.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/246a4a0a-9e3e-46d6-9b19-7f8c4d3c0bb8/image/w=1920,quality=90,fit=scale-down" alt="image" height="188.79692832764505" width="634.375">

The pin assignments and definitions for the M12 12P A-CODE aviation connector of the aviation power and Ethernet cable and the LiDAR connector are as follows:

Table 2.1.1 Aviation Power and Ethernet Cable Pin Assignment Table

| **LiDAR Connector Pin** | **M12 Aviation Connector Pin** | **Signal**   | **I/O** | **Description**            | **Wire Color**   |
| ----------------------- | ------------------------------ | ------------ | ------- | -------------------------- | ---------------- |
| 1                       | 1                              | POWER+       | Power   | DC 10 V – 15 V             | Blue/White       |
| 7                       | 9                              | POWER+       | Power   | DC 10 V – 15 V             | Blue             |
| 2                       | 2                              | Ground       | Power   | Ground                     | Silver Bare Wire |
| 8                       | 3                              | Ground       | Power   | Ground                     | Silver Bare Wire |
| 3                       | 4                              | Ethernet-TX+ | Output  | 100BASE-TX, TX+            | Orange/White     |
| 4                       | 5                              | Ethernet-TX- | Output  | 100BASE-TX, TX-            | Orange           |
| 9                       | 6                              | Ethernet-RX+ | Input   | 100BASE-TX, RX+            | Green/White      |
| 10                      | 7                              | Ethernet-RX- | Input   | 100BASE-TX, RX-            | Green            |
| 5                       | 8                              | Ground       | Power   | Ground                     | Silver Braid     |
| 11                      | 10                             | Ground       | Power   | Ground                     | Silver Braid     |
| 12                      | 11                             | Sync-        | Input   | RS485\_B, Pulse Per Second | Gray             |
| 6                       | 12                             | Sync+        | Input   | RS485\_A, Pulse Per Second | Gray/White       |

**Sync Signal Description**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b1d3d71e-af8d-4f17-a7da-7cf3364a627a/image/w=1920,quality=90,fit=scale-down" alt="image" height="235.69047083361394" width="634.3409423828125">

* For detailed information about the sync signal, please refer to the SDK User Manual section.

### **Power Cable and Sync Signal Cable Interface** <a href="#block-e73fdc08310247179e6829c997b0d048" id="block-e73fdc08310247179e6829c997b0d048"></a>

The Livox Tele-15 cable kit includes two power cables and two sync signal cables. The pin assignments are as follows:

**Power Cable**

End A connects to the power interface of the power adapter socket 2.0, and End B can be connected to an external DC regulated power supply by the user. The power cable uses connector model MOLEX 105307-1202.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b54a08de-c1fc-4f5b-8f3e-ad8b65c27fd2/image/w=1920,quality=90,fit=scale-down" alt="image" height="122.57795988073671" width="634.3409423828125">

Table 2.2.1 Power Cable Pin Assignment

| **Pin** | **Signal** | **Type** | **Description**      | **Color** |
| ------- | ---------- | -------- | -------------------- | --------- |
| 1       | Power+     | Power    | DC 9–30 V (30 V max) | Red       |
| 2       | Ground     | Power    | Ground               | Black     |

**Sync Signal Cable**

End A connects to the sync signal interface of the power adapter socket 2.0, and End B can be connected to an external sync signal by the user. The sync signal cable uses a 3-pin connector. The corresponding wire-to-board connector model is Famfull 9.510A0-003-1R0, which is compatible with JST GHR-03V-S. Refer to the Sync Signal section for more information.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b562d9b0-bded-47b4-bdfb-f25112625493/image/w=1920,quality=90,fit=scale-down" alt="image" height="113.86217948717949" width="634.375">

Table 2.2.2 Sync Signal Cable Pin Assignment

| **Pin** | **Signal** | **Type** | **Description**                     | **Color** |
| ------- | ---------- | -------- | ----------------------------------- | --------- |
| 1       | Ground     | Power    | Ground                              | Black     |
| 2       | Sync+      | Input    | 3.3 V LVTTL level, pulse per second | Blue      |
| 3       | Reserved   | Reserved | Undefined signal                    | White     |

### **Ethernet Interface** <a href="#block-1f83b559a7bf48d9b17e35ba5912e1e0" id="block-1f83b559a7bf48d9b17e35ba5912e1e0"></a>

For ease of debugging, the Tele-15’s power adapter socket 2.0 directly supports a standard RJ45 Ethernet interface compliant with the 100BASE-TX standard. The Tele-15 uses two twisted pairs for transmitting and receiving data.

## Mounting the Livox Tele-15 <a href="#block-fc67f534035d4ce9a871878adfc20ecd" id="block-fc67f534035d4ce9a871878adfc20ecd"></a>

### **Effective Field of View (FOV) Range** <a href="#block-a61c7f2e08804e5f8575ef1aa161c433" id="block-a61c7f2e08804e5f8575ef1aa161c433"></a>

The Livox Tele-15 has a FOV of 14.5° horizontally and 16.2° vertically, as shown in the figure below. When installing, please pay attention to the effective FOV range to avoid obstruction. You can download the 3D model of the Tele-15 and its FOV at [www.livoxtech.com/tele-15](http://www.livoxtech.com/tele-15).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/54884f44-e634-41f1-937a-87b3f322f24c/image/w=1920,quality=90,fit=scale-down" alt="image" height="260.0978719948018" width="634.375">

### **Installation Precautions** <a href="#block-038e116e8dc7453fb3d15dee906bb2fe" id="block-038e116e8dc7453fb3d15dee906bb2fe"></a>

Before installing the Livox Tele-15, please read the following precautions:

1. Remove the protective film from the window glass before use.
2. Heavy dust or dirt on the window glass will affect the performance of the LiDAR. It is recommended to clean it using an air blower, alcohol, or an optical cleaning cloth as described in the maintenance section of this document. Perform the cleaning before installation.
3. When installing the LiDAR, do not block its FOV. Even installing transparent glass in front of the window can affect the LiDAR’s performance.
4. During installation, ensure sufficient clearance around the air inlet and outlet of the LiDAR; otherwise, the performance and lifespan of the LiDAR may be affected. The distance from the air inlet/outlet end face to any obstruction should be greater than 10 mm.
5. There is no restriction on the mounting orientation of the LiDAR; it can be mounted using either its top or bottom surface. During installation, it is recommended to keep the mounting surface parallel to the ground.
6. The LiDAR mounting structure only guarantees its own reliability. No additional load should be applied to the LiDAR body.
7. Mounting the LiDAR to a tripod using the 1/4-inch threaded hole is for static display purposes only and does not guarantee reliability under shock or vibration loads.

### **Removing the Active Cooling Module** <a href="#block-cfedf8919b32463d868fc04ce3e7789c" id="block-cfedf8919b32463d868fc04ce3e7789c"></a>

The active cooling module is located on top of the Livox Tele-15. Users can remove it and use the Livox Tele-15 standalone. After removing the cooling module, please design an appropriate cooling system; otherwise, the maximum operating temperature of the Livox Tele-15 may be reduced. The active cooling module is not designed for repeated removal and installation. Only remove it if you are certain that it will not be used again.

To remove the active cooling module:

* Place the Livox Tele-15 with the fan side facing up, and use a hex wrench to remove the 6 screws securing the active cooling module.
* After the screws are removed, the active cooling module can be detached. If you need to reinstall the active cooling module, ensure that the connector on the Tele-15 body aligns with the connector on the active cooling module, then secure it using the original 6 black M2.5 screws.

Please note that after removing the active cooling module, install the fan interface protective rubber plug (included in the packaging) into the connector between the cooling module and the Livox Tele-15 as shown in the figure, to protect the cooling module interface. At this point, please ensure that the housing temperature of the Livox Tele-15 does not exceed 85°C during use. It is recommended to operate in ambient temperatures below 65°C and avoid direct sunlight. Users may also design their own cooling solutions.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bbb3bb98-3f87-4754-8f30-66d5350a0cd8/image/w=1920,quality=90,fit=scale-down" alt="image" height="297.1885593220339" width="634.375">

### **Installation Dimensions** <a href="#block-ea8115897bc14f1c80f24600c26eb16f" id="block-ea8115897bc14f1c80f24600c26eb16f"></a>

**Installing the Livox Tele-15 (with Active Cooling Module)**

The dimensions of the active cooling module and its mounting hole locations are shown below. When installing with the active cooling module, please mount the Livox Tele-15 in the appropriate position according to the dimensions provided. In this configuration, M3 screws or the 1/4-inch threaded interface on the active cooling module can be used for mounting.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/54c0d6c8-8319-44ee-9332-5ac916316b51/image/w=1920,quality=90,fit=scale-down" alt="image" height="195.47365470852017" width="634.375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d0a8f0b0-f458-4ec9-ace7-2cd192823dba/image/w=1920,quality=90,fit=scale-down" alt="image" height="252.3576817558299" width="634.375">

Tele-15 Weight and Dimensions (with Active Cooling Module)

| **Weight** | **Approx. 1.8 kg (including the standard 1.3 m cable, weight approx. 160 g)** |
| ---------- | ----------------------------------------------------------------------------- |
| Dimensions | 112 × 94.2 × 122 mm                                                           |

**Installing the Livox Tele-15 (without Active Cooling Module)**

After removing the active cooling module, install the Livox Tele-15 in the appropriate position according to the device dimensions and mounting hole locations shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b57e74cf-2de9-489a-b5fa-755e577fc0f0/image/w=1920,quality=90,fit=scale-down" alt="image" height="207.00657894736844" width="634.375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/91ab7892-ca60-4543-bf2a-9c7936060496/image/w=1920,quality=90,fit=scale-down" alt="image" height="201.7922623292704" width="634.32958984375">

Tele-15 Weight and Dimensions (without Active Cooling Module)

| **Weight (with cable)** | **Approx. 1.7 kg**  |
| ----------------------- | ------------------- |
| Dimensions              | 112 × 82.4 × 122 mm |

**Power Adapter Socket 2.0**

If you need to use the Livox power adapter socket, install it in the appropriate position according to the dimensions of the power adapter socket and the mounting hole locations shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/927991f9-8253-4655-91b1-4fd10651e80f/image/w=1920,quality=90,fit=scale-down" alt="image" height="205.80058528428094" width="634.375">

Table 3.4.3 Livox Converter 2.0 Weight & Dimensions

| **Weight** | **Approx. 88 g** |
| ---------- | ---------------- |
| Dimensions | 74 × 52 × 23 mm  |

## **Preparation** <a href="#block-a7e27fabffcf4d08a39bca16bfcb2297" id="block-a7e27fabffcf4d08a39bca16bfcb2297"></a>

### **Designing an External Power Supply** <a href="#block-5278a9bd0b354b00b6df29a81faf7319" id="block-5278a9bd0b354b00b6df29a81faf7319"></a>

The Livox Tele-15 supports direct power supply from a DC power source with an output voltage of 10–15 V. When extending the cable, please consider increasing the output voltage of the external power supply to compensate for the additional voltage drop caused by the cable extension, but the maximum voltage must not exceed 15 V. At low temperatures, the minimum operating voltage should be increased accordingly. Please note that voltage fluctuations above 15 V on the cable caused by certain reasons (e.g., interference, sudden power-off of other devices connected in parallel to the same power supply, etc.) may cause the device to malfunction or even be damaged.

At an ambient temperature of 25°C, the power consumption of the Livox Tele-15 is 12 W. Depending on the ambient temperature, the power consumption of the Tele-15 varies, as shown in the figure below. Please design the power supply reasonably based on the actual operating power of the Tele-15.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/791e284a-1e46-48cb-bea9-d23412e14707/image/w=1920,quality=90,fit=scale-down" alt="image" height="255.30781036834924" width="634.375">

### **Connecting** <a href="#block-df440324296e4a468efa059a0d7210cf" id="block-df440324296e4a468efa059a0d7210cf"></a>

The connector of the Livox Tele-15 provides external power and transmits data. For the specific pin assignments of this connector, please refer to the Interface Definition section. When using the Livox Tele-15 LiDAR, it is recommended to use the Livox power adapter socket 2.0, which integrates the LiDAR connector interface, sync signal interface, power interface, and Ethernet interface.

The Livox Tele-15 supports two IP modes: Dynamic IP address mode and Static IP address mode. All Livox Tele-15 units are factory-configured with Static IP enabled by default, with an IP address of 192.168.1.1XX (where XX is the last two digits of the serial number), a subnet mask of 255.255.255.0, and a default gateway of 192.168.1.1. On first use, the device can be connected directly to a computer without a router. The connection method differs depending on the IP address mode:

1. Static IP (factory default, can be connected directly to a computer; the Tele-15 can be set to any static IP address in any subnet via Livox Viewer or the SDK).
2. Dynamic IP (uses DHCP to assign an address. The device must be switched to Dynamic IP mode using Livox Viewer or the SDK, and then connected via a router).

#### Static IP address: <a href="#block-fcc51229894b4f64b555229a52b7e585" id="block-fcc51229894b4f64b555229a52b7e585"></a>

1. Follow the steps to set the IP address of your computer to static IP address:

**Windows system**

a. Click to enter in the Network and Sharing Center under Control Panel.

b. Click the network you are using, and click “Properties”.

c. Double click “Internet Protocol Version 4 (TCP/IPv4)”.

d. Set the static IP address of the computer to 192.168.1.50 and the subnet mask to 255.255.255.0. Click “OK” to complete.

**Ubuntu-16.04 system**

The IP address of the computer can be configured by using the ifconfig command at the terminal. The configuration code is as below:

\~$ sudo ifconfig enp4s0 192.168.1.50 (replace “enp4s0” with the network port name of the computer)

2. Connect the Tele-15, Livox Converter 2.0, external power source, and computer by following Figure 4.2.1.
3.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5c5cb9bd-9b3d-4c98-a047-edf710fa9d10/image/w=1920,quality=90,fit=scale-down" alt="image" height="194.30610835444818" width="634.352294921875">

a. Connect the Tele-15 to the Livox Converter 2.0.

b. Connect the Livox Converter 2.0 to your computer using an Ethernet cable.

c. Connect the Livox Converter 2.0 to an external power source.

💡

**Note:**

* If you need to connect multiple Livox Tele-15 units in Static IP mode to the PC simultaneously, set each Livox Tele-15 to a different IP address and connect them via a network switch.
* After connecting as shown in Figure 4.2.1, run Livox Viewer on the computer, select the device for which you want to change the static IP address, and click **Enter Device Parameter Settings** to set the static IP address for that Livox Tele-15.
* If connecting more than 6 Livox Tele-15 units, please use a Gigabit switch; otherwise, data loss or connection failures may occur.

**Dynamic IP:**

1. First, connect the Livox Tele-15, the power adapter socket 2.0, the external power supply, and the computer as shown in Figure 4.2.1.
2. Run Livox Viewer on the computer, and in the **Device Parameter Settings** interface, set the IP address of the LiDAR on the local network to Dynamic IP.
3. After the settings are completed, disconnect all connections to the Livox Tele-15. Note that the Dynamic IP settings will take effect after a reboot.
4. Then, set the computer to Dynamic IP mode. The configuration method is as follows:

**Windows System**

a. In the Control Panel, go to Network and Sharing Center.

b. Click “Ethernet” to open the Ethernet status window, then click the “Properties” button to enter Ethernet properties.

c. Double-click “Internet Protocol Version 4 (TCP/IPv4)”.

e. Select “Obtain an IP address automatically” and “Obtain DNS server address automatically”, then click “OK” to complete the dynamic IP settings for the computer.

**Ubuntu 16.04 System**

a. Open the Ubuntu network connection editor.

b. In the network connection editor, proceed as follows: edit the connection name, then select “Automatic (DHCP)” in the “Method” option, and finally click “Save”.

5. After the dynamic IP settings for both the Livox Tele-15 and the computer have been completed, please connect as shown in the figure.
6.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/90b9b221-b201-458b-ab09-4ef930470882/image/w=1920,quality=90,fit=scale-down" alt="image" height="209.38521241830065" width="634.375">

a. Insert the LiDAR connector on the Livox Tele-15 into the LiDAR connector interface of the power adapter socket 2.0.

b. Use an Ethernet cable to connect both the power adapter socket 2.0 and your PC to the LAN ports of a router.

c. Connect the external power supply through the power interface of the power adapter socket 2.0.

💡

**Note:**

* If you need to connect more than 6 Livox Tele-15 units simultaneously, please use a Gigabit router. Note that all Livox Tele-15 units and the PC should be connected to LAN ports.
* The broadcast code of each LiDAR can be viewed via the device manager in Livox Viewer or through the SDK. The broadcast code of the Livox Tele-15 is the serial number with an additional character “1” appended at the end.

## **Usage** <a href="#block-e6dd77ea5e034bf1ae8f863cd24021cc" id="block-e6dd77ea5e034bf1ae8f863cd24021cc"></a>

### **Coordinate System** <a href="#block-f2fd5ac0eb064c6fa4412277577cff8f" id="block-f2fd5ac0eb064c6fa4412277577cff8f"></a>

The Livox Tele-15 has a built-in IMU. The definitions of the point cloud coordinate system O-XYZ and the IMU coordinate system O’-X’Y’Z’ are shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9fbaa52e-69a8-4199-938a-674acb9cbeb7/image/w=1920,quality=90,fit=scale-down" alt="image" height="213.07251908396947" width="634.375">

The coordinates of the IMU origin O’ in the point cloud coordinate system O-XYZ are (-84.7, 42.5, -35.3) (unit: mm).

### **Output Data** <a href="#block-1642ce2147bb4b329af974c96894e836" id="block-1642ce2147bb4b329af974c96894e836"></a>

The output data of the Livox Tele-15 includes point cloud data and IMU data. Both the point cloud data and IMU data contain timestamp information and status indicator code information, while the point cloud data additionally includes target reflectivity, coordinate information, and flag information.

### **Point Cloud Data** <a href="#block-b42e6ad2008b4d679e05f482c36b959f" id="block-b42e6ad2008b4d679e05f482c36b959f"></a>

Point cloud data is the total set of all points detected by the LiDAR on the surface of objects within the field of view. Each point cloud contains the following information:

* **Target Reflectivity**: Expressed as a value from 0 to 255. Values 0 to 150 correspond to reflectivity between 0% and 100% for diffuse scattering objects; values 151 to 255 correspond to total reflection objects.
* **Coordinates:** Can be expressed as Cartesian coordinates (x, y, z) and Spherical coordinates (r, θ, φ). The relationship between Cartesian and Spherical coordinates is shown in the figure below. When there is no object within the detective range or the object is placed outside the detective range, the coordinates of the point cloud will be expressed as (0, 0, 0) in Cartesian coordinates and as (0, θ, φ) in Spherical coordinates.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4cf25231-ae98-4c2f-bccf-6ccc30d8b42f/image/w=1920,quality=90,fit=scale-down" alt="image" height="249.98870209689082" width="634.375">

**Tag**: Primarily indicates multi-echo information and noise information. The format of the tag information is as follows:

| bit7     | bit6 | bit5                                                           | bit4 | bit3                                                                                                                                     | bit2 | bit1                                                                                                                                                                         | bit0 |
| -------- | ---- | -------------------------------------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| Reserved |      | Return number: 00:return 0 01:return 1 10:return 2 11:return 3 |      | Point property based on intensity: 00:Normal 01:High confidence level of the noise 10:Moderate confidence level of the noise 11:Reserved |      | Point property based on spatial position: 00: Normal 01: High confidence level of the noise 10: Moderate confidence level of the noise 11: Low confidence level of the noise |      |

Each tag is 1 byte in length. In this byte, bit7 and bit6 form the first group, bit5 and bit4 form the second group, bit3 and bit2 form the third group, and bit1 and bit0 form the fourth group.

The second group indicates the echo order of the sampled point. Since the Livox Tele-15 uses a coaxial optical path, even when there is no external object to be measured, its internal optical system generates an echo, which is recorded as the 0th echo. Subsequently, if there is a detectable object in the laser emission direction, the first laser echo returning to the system is recorded as the 1st echo, followed by the 2nd echo, and so on. If the detected object is too close (e.g., 1.5 m), the 1st echo will be merged into the 0th echo, and this echo is recorded as the 0th echo.

The third group determines whether the sampled point is noise based on the echo energy intensity. Typically, noise points caused by interference such as dust, rain, fog, or snow have very low echo energy. Currently, noise confidence levels are classified into three grades based on echo energy intensity: 01 indicates very weak echo energy, indicating a high probability that such sampled points are noise (e.g., dust points); 10 indicates medium echo energy, indicating a medium probability that such sampled points are noise (e.g., rain and fog noise). The lower the noise confidence, the lower the probability that the point is noise.

The fourth group determines whether the sampled point is noise based on its spatial position. For example, when the LiDAR measures two objects at very close distances, filamentous noise may occur between the two objects. Currently, noise confidence is classified into three grades. The lower the noise confidence, the lower the probability that the point is noise.

### **Timestamp** <a href="#block-85b9a2cf14a74014a4267e7c6b9a1d88" id="block-85b9a2cf14a74014a4267e7c6b9a1d88"></a>

The point cloud data and IMU data of the Livox Tele-15 contain timestamp information. The Livox Tele-15 supports three synchronization methods: IEEE 1588-2008 synchronization, PPS synchronization, and GPS synchronization. When multiple synchronization methods are connected simultaneously, the synchronization priority order is: IEEE 1588-2008 > GPS > PPS.

**IEEE 1588-2008**: IEEE 1588-2008 refers to the “Precision Time Protocol,” which enables precise time synchronization via Ethernet. The Livox LiDAR uses the UDP/IPv4 protocol in the synchronization network and operates in “two-step” synchronization mode. The supported message formats are: Sync, Follow\_up, Delay\_req, and Delay\_resp.

**PPS**: Pulse synchronization is achieved via the sync signal cable. Refer to the Interface Definition section for more information. The synchronization logic is shown in the figure below. The pulse period of the pulse synchronization is ( t0 ) (( t0 = 1000 , \text{ms} )), and the high level duration is ( t1 ) (( 20 , \text{ms} < t1 < 200 , \text{ms} )). When the rising edge of the pulse synchronization arrives, the timestamp in the point cloud is reset to zero. Therefore, the timestamp in the point cloud data represents the interval between the point cloud data sampling and the previous pulse synchronization rising edge.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f2c69561-e690-48ef-8e78-6857ba15a17b/image/w=1920,quality=90,fit=scale-down" alt="image" height="189.65850515463916" width="634.375">

**GPS**: The GPS module outputs the PPS signal and UTC time information, and transmits them to the Livox Tele-15 for synchronization. The PPS signal is input via the sync signal interface of the Livox Tele-15, while the UTC time information is transmitted to the Livox Tele-15 via the SDK. For specific communication commands, please refer to the relevant sections of the SDK communication protocol. The logic of the PPS signal and UTC time commands is shown in the figure below. When GPS synchronization is used, the timestamp in the point cloud data is in UTC format.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/36236c7a-0eb6-402f-b298-d82d48ba450a/image/w=1920,quality=90,fit=scale-down" alt="image" height="190.52901023890786" width="634.375">

### **Status Indication** <a href="#block-74184a4f458f49f4979027e7898b1886" id="block-74184a4f458f49f4979027e7898b1886"></a>

The point cloud data and IMU data of the Livox Tele-15 contain status indicator code information. The status indicator code displays the current operating status of the Livox Tele-15. Through the status indicator code, users can check the temperature status, voltage status, motor status, contamination warning, remaining service life warning, and pulse synchronization signal status. Users can view the status indicator code in Livox Viewer or via the SDK. Refer to the Device Management Window section of the Livox Viewer User Manual for instructions on how to view the status indicator code.

| **Status**                          | **Description**                                                                                                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Temperature Status                  | Indicates whether there is a temperature anomaly. Temperature status includes: Normal, Warning, and Error.                                                                                 |
| Voltage Status                      | Indicates whether there is an internal voltage anomaly. Voltage status includes: Normal, Warning, and Error.                                                                               |
| Motor Status                        | Indicates whether there is an internal motor anomaly. Motor status includes: Normal, Warning, and Error.                                                                                   |
| Contamination Warning               | Indicates whether heavy dust is detected on the window, whether an object is blocking the window, or whether there is an obstacle close to the LiDAR.                                      |
| Remaining Service Life Warning      | Indicates whether the LiDAR is approaching the end of its service life. When this warning appears, the LiDAR can still be used for a period of time; please replace it in a timely manner. |
| Pulse Synchronization Signal Status | Indicates whether the pulse synchronization signal is properly connected.                                                                                                                  |

### **Operating Status and Operating Modes** <a href="#block-a989680ea7214acea965733b70e10afa" id="block-a989680ea7214acea965733b70e10afa"></a>

The operating status of the Livox Tele-15 includes Initialization Status, Normal Operating Status, Standby Status, Low-Power Status, and Error Status.

| **Operating Status**    | **Description**                                                                                                            |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Initialization Status   | The LiDAR is booting up.                                                                                                   |
| Normal Operating Status | The LiDAR has started up and is operating normally.                                                                        |
| Standby Status          | The LiDAR has started up, but the laser beam has not yet been emitted.                                                     |
| Low-Power Status        | All parts except the communication module have stopped working.                                                            |
| Error Status            | After a fault is detected, the LiDAR will enter Error Status. All parts except the communication module will be shut down. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/50111f8f-5297-4d52-8b1a-f89eb9b7e7f6/image/w=1920,quality=90,fit=scale-down" alt="image" height="298.91965393862716" width="634.352294921875">

The Livox Tele-15 has three operating modes: Normal Operating Mode, Standby Mode, and Low-Power Mode. Users can switch between different operating modes via Livox Viewer or the SDK.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/df0ab88a-ae6b-40ae-bfb0-d9b1227e2fdd/image/w=1920,quality=90,fit=scale-down" alt="image" height="238.83726585089525" width="634.3409423828125">

### **Multi-echo Mode** <a href="#block-02c04608669345f9be6d1d5e19e9f09b" id="block-02c04608669345f9be6d1d5e19e9f09b"></a>

The Livox Tele-15 supports multi-echo mode, which can be configured via Livox Viewer or the SDK. When multi-echo mode is enabled, Livox will output up to two echoes per point.

The Livox Tele-15 outputs 240,000 points per second by default. When multi-echo mode is enabled, the output rate increases to 480,000 points per second. To quickly configure the echo mode using Livox Viewer, follow these steps:

After properly connecting the Tele-15, select the device you wish to configure, then enter the device parameter settings interface to change the echo mode.

### **IMU Sensor Information** <a href="#block-830680370d0940fa897788d7d253c815" id="block-830680370d0940fa897788d7d253c815"></a>

The Tele-15 features a built-in IMU sensor that provides attitude data for the Tele-15.

Users can set the IMU data push frequency via Livox Viewer or the SDK. The configuration method is similar to that of the multi-echo mode.

### **Software Development Kit (SDK)** <a href="#block-6501af3314074bf5ae96172120d2d888" id="block-6501af3314074bf5ae96172120d2d888"></a>

In addition to using Livox Viewer to view real-time point cloud data, users can also use the Software Development Kit (SDK), ROS toolkit, etc., to apply the point cloud data and IMU data acquired from the Livox LiDAR to various custom application scenarios.

**SDK Communication Protocol**

Interaction between the user and the Livox LiDAR can be carried out via the SDK communication protocol, which includes the following three types of data:

* **Control Command Data**: Configuration and query of LiDAR parameters and status information.
* **Point Cloud Data**: Point cloud coordinate data generated by the LiDAR.
* **IMU Data**: IMU data generated by the built-in IMU of the LiDAR.

All the above data are stored in little-endian format.

Visit http://www.livoxtech.com/sdk for more detailed information on the SDK communication protocol, Livox SDK API documentation, and ROS toolkit.

## **Troubleshooting** <a href="#block-39d19359db734b3b8cfa0227b15c5d35" id="block-39d19359db734b3b8cfa0227b15c5d35"></a>

If you encounter any issues during use, please refer to the table below for solutions. If the problem persists, please contact Livox or an authorized Livox dealer.

| **Problem**                                                                                  | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Livox LiDAR cannot be detected                                                               | - Confirm that all cables are properly connected.- Confirm that the voltage is correct. The operating voltage of the Livox Tele-15 LiDAR is 10–15 V. When connected via the Livox power adapter socket 2.0, an external power supply of 9–30 V is supported.- Confirm that the Livox LiDAR is not connected to other software.- Confirm that the PC and the device are on the same local network.- Confirm that no antivirus software or other programs that block Ethernet broadcasts are installed.After the above checks are completed, if the device still cannot be detected, please close all firewalls and restart Livox Viewer, then search for the LiDAR on the local network again.Use a network packet analysis tool (e.g., Wireshark) to analyze UDP packets. |
| Livox LiDAR is detected but connection cannot be established / or sampling cannot be started | - Confirm that all cables are properly connected.- Confirm that the voltage is correct. The operating voltage of the Livox Tele-15 LiDAR is 10–15 V. When connected via the Livox power adapter socket 2.0, an external power supply of 9–30 V is supported.If the problem persists, please restart the LiDAR and the Livox Viewer software.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| No data                                                                                      | Use a network packet analysis tool (e.g., Wireshark) to analyze the output data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

## Appendix <a href="#block-6374c630448d4aae9503268528a249c4" id="block-6374c630448d4aae9503268528a249c4"></a>

### Appendix 1 <a href="#block-b454faa2879343e29348bcccfa470874" id="block-b454faa2879343e29348bcccfa470874"></a>

Livox Tele-15 Dimensions with Self-Dissipation Module (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2fd05f12-d371-45fc-b8e3-8d61b50ad344/image/w=1920,quality=90,fit=scale-down" alt="image" height="303.4157477601654" width="634.375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ed3d51b2-5d64-4194-87aa-0123b3dadaed/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.3255603759942" width="634.375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ad444a9a-f2e5-4758-86e5-447a39d39ff9/image/w=1920,quality=90,fit=scale-down" alt="image" height="207.82589471726192" width="634.352294921875">

### Appendix 2 <a href="#block-51acc05d43734b1284ec9ee33a4596fe" id="block-51acc05d43734b1284ec9ee33a4596fe"></a>

Livox Tele-15 Dimensions without Self-Dissipation Module (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/292c93ac-1363-4b9a-836d-7fa8a94edbe4/image/w=1920,quality=90,fit=scale-down" alt="image" height="282.91606030273437" width="634.3409423828125">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dc07c6c7-9480-4f93-82ff-225855001bfb/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.01748081628114" width="634.352294921875">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dcd7554a-8e4c-449e-9636-2017b34a571a/image/w=1920,quality=90,fit=scale-down" alt="image" height="205.28265241438967" width="634.3636474609375">

### Appendix 3 <a href="#block-4bb36e2d899d4e519c346eeff0037bdf" id="block-4bb36e2d899d4e519c346eeff0037bdf"></a>

Livox Converter 2.0 Dimensions (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/095356cf-07d7-4861-acef-5ebadafab198/image/w=1920,quality=90,fit=scale-down" alt="image" height="253.14471984497314" width="634.3409423828125">

## **Specifications** <a href="#block-16190c9618464632882385802ee319f7" id="block-16190c9618464632882385802ee319f7"></a>

| **Parameter**                    | **Value**                                                                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Model                            | TELE-15                                                                                                      |
| Laser Wavelength                 | 905 nm                                                                                                       |
| Eye Safety Level(^1)             | Class 1 (IEC 60825-1:2014) Eye Safe                                                                          |
| Range (@ 100 klx)                | 320 m @ 10% reflectivity500 m @ 50% reflectivity                                                             |
| FOV                              | 14.5° (H) × 16.2° (V)                                                                                        |
| Range Accuracy (1σ)              | < 2 cm (5–70 m), < 4 cm (70–120 m) @ 10% reflectivity< 2 cm (5–220 m), < 4 cm (220–380 m) @ 80% reflectivity |
| Angular Accuracy (1σ)            | < 0.03°                                                                                                      |
| Beam Divergence                  | 0.02° (H) × 0.12° (V)                                                                                        |
| Point Cloud Output               | 240,000 pts/s (configurable first or strongest return)480,000 pts/s (dual return)                            |
| Data Latency                     | ≤ 2 ms                                                                                                       |
| Data Interface                   | 100 Mbps Ethernet Interface                                                                                  |
| Data Synchronization Methods     | IEEE 1588-2008, PPS, GPS                                                                                     |
| False Alarm Rate (@ 100 klx)(^2) | < 0.01%                                                                                                      |
| IMU                              | Built-in IMU model: BMI088                                                                                   |
| Operating Temperature            | -40°C to 85°C (with active cooling module)                                                                   |
| Storage Temperature              | -40°C to 90°C                                                                                                |
| Protection Level                 | IP67(^3)                                                                                                     |
| Power Consumption                | 12 W (typical), 36 W (startup)                                                                               |
| Supply Voltage Range             | Livox Tele-15: 10–15 V DC (12 V DC power supply > 36 W recommended)Power adapter socket 2.0: 9–30 V DC       |
| Noise                            | < 50 dB at 40 cm (omnidirectional, fan off)                                                                  |
| Dimensions                       | 112 × 94.2 × 122 mm (with active cooling module)112 × 82.4 × 122 mm (without active cooling module)          |
| Weight                           | Approx. 1.8 kg (with active cooling module)Approx. 1.7 kg (without active cooling module)                    |
| Power Adapter Socket 2.0         |                                                                                                              |
| Supply Voltage Range             | 9–30 V DC                                                                                                    |
| Dimensions                       | 74 × 52 × 23 mm                                                                                              |
| Weight                           | 88 g                                                                                                         |

1. The typical divergence angle of the built-in laser radiation in the LiDAR is 25.2° (H) × 8° (V) (FWHM). The maximum peak power of the laser may exceed 70 W. Do not disassemble the Livox Tele-15 to avoid danger.
2. The proportion of false alarm noise generated by ambient heat dissipation under 100 klx sunlight conditions at an ambient temperature of 25°C.
3. All cables for the Livox Tele-15 and the power adapter socket 2.0 are not covered by this protection level.
