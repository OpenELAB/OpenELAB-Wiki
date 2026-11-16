# LIVOX AVIA User Manual

> **LIVOX AVIA User Manual**

{% embed url="https://openelab.io/products/livox-avia-compact-lidar-sensor3d" %}

## **Product Overview** <a href="#block-798e263f6173409eb5a51d0d80c8e877" id="block-798e263f6173409eb5a51d0d80c8e877"></a>

### **Introduction** <a href="#block-6f15ba913bf64ea4984cfdd988e38500" id="block-6f15ba913bf64ea4984cfdd988e38500"></a>

The Livox Avia features long range, high accuracy, wide field of view, light weight, and high reliability, making it widely used in applications such as surveying and mapping, V2X (Vehicle-to-Everything), robotics, and more.

**Long Range**: Compared to the Livox Horizon, the Avia significantly improves ranging performance for low-reflectivity objects (e.g., rebar, concrete, rock, soil, etc.), with an increase of up to 70%.

**Light Weight**: The Avia is compact and lightweight, weighing 498 g, making it suitable for UAV surveying and mapping as well as small robotic applications.

**Triple Echo**: For surveying and mapping, the firmware supports up to three returns, better accommodating forestry mapping requirements.

**Switchable Scanning Mode**: Supports both traditional non-repetitive scanning and repetitive scanning modes. Non-repetitive scanning improves static scanning performance and vertical surface scanning during aerial mapping; repetitive scanning improves point cloud density uniformity.

**Built-in IMU Module**: The Avia features a built-in BMI088 inertial measurement unit, with a push frequency of 200 Hz.

**User-Friendly Livox Viewer Software**: Livox Viewer is an operation software that enables real-time display, recording, playback, and parsing of 3D point clouds, and also supports advanced functions such as product configuration and extrinsic parameter adjustment. Its clean interface makes it easy for users to get started.

**Open-Source Livox SDK**: Users can develop advanced algorithms based on the open-source Livox SDK, effectively improving development efficiency. The Livox SDK supports multiple development environments including Windows, Linux, Mac OS, and ROS.

💡

**Note:**

* At an ambient temperature of 25°C, with 100 klx solar irradiance and a Lambertian target reflectivity above 80% (reflectivity of concrete or pavement is 15–30%, while white gypsum walls have a reflectivity of 90–99%), the maximum detection range is measured at 320 m.
* Before use, please remove the protective film from the Avia window to avoid affecting its performance.

## **Product Features** <a href="#block-8560a474186746a982eac8931687e892" id="block-8560a474186746a982eac8931687e892"></a>

The Avia utilizes Livox’s proprietary scanning technology and offers two scanning point cloud patterns: non-repetitive scanning pattern and repetitive scanning pattern. Users can choose the appropriate scanning pattern based on their specific requirements. For the non-repetitive scanning pattern, the Avia ensures a denser point cloud distribution in the central area and a sparser distribution at the edges across different integration times. The FOV of the non-repetitive scanning point cloud pattern is 77.2° vertically and 70.4° horizontally. With a 0.1 s integration time, the point cloud density within a 10° radius circle at the center of the FOV is comparable to that of a typical 32-line mechanical spinning LiDAR. With a 0.2 s integration time, the point cloud density within a 10° radius circle at the center of the FOV is comparable to that of a typical 64-line mechanical spinning LiDAR, while the density in other areas is comparable to that of a typical 32-line mechanical spinning LiDAR. As the integration time increases, the point cloud density and coverage across the entire FOV gradually improve, allowing more details within the field of view to be captured.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5ab7ca31-7174-4e48-9ca3-22b620ee4fa8/image/w=1920,quality=90,fit=scale-down" alt="image" height="199.66855788934427" width="634.3636474609375">

The figure below (Figure 1.2.2) presents a comparison of the Avia’s FOV coverage at different integration times with several common multi-line mechanical spinning LiDARs currently available on the market. It can be observed from the figure that when the integration time is 0.3 s, the Avia’s FOV coverage is approximately 70%, which is slightly better than that of a typical 64-line mechanical spinning LiDAR. As the integration time continues to increase to around 0.8 s, the FOV coverage will approach 100%, meaning that nearly the entire field of view will be covered.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4e9dd988-544d-4da1-ac0f-8dba131bb85a/image/w=1920,quality=90,fit=scale-down" alt="image" height="345.2380952380953" width="634.375">

The repetition period of the Avia’s repetitive scanning pattern is approximately 0.1 s. The horizontal FOV of the repetitive scanning pattern is the same as that of the non-repetitive scanning pattern, both at 70.4°. The vertical FOV ranges from a minimum of 4.5° to a maximum of 6.8°, and its vertical angular resolution is slightly better than that of a traditional 32-line LiDAR.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/219fcd54-d908-4441-b900-bf1434acb052/image/w=1920,quality=90,fit=scale-down" alt="image" height="419.59123496762254" width="634.375">

> The area within the field of view illuminated by the laser is related to the measurement performance of the LiDAR. To characterize this metric, the proportion of the field of view that is detected by the laser can be quantitatively expressed as the field of view coverage ©. It is calculated as follows:C=TotalareailluminatedbylaserbeamsTotalareainFOV∗100%C=TotalareainFOVTotalareailluminatedbylaserbeams​∗100%
>
> Visit the Livox website for more information on field of view coverage.

## **Table 1.2.1 Point Cloud Specifications** <a href="#block-124789faea4b4bdbbb68f95e2050aec8" id="block-124789faea4b4bdbbb68f95e2050aec8"></a>

| **Parameter**                | **Value**                                              |
| ---------------------------- | ------------------------------------------------------ |
| Laser Wavelength             | 905 nm                                                 |
| Eye Safety Level             | Class 1 (IEC 60825-1:2014) Eye Safe                    |
| Range (@ 100 klx)            | 190 m @ 10% reflectivity                               |
|                              | 230 m @ 20% reflectivity                               |
|                              | 320 m @ 80% reflectivity                               |
| Range (@ 0 klx)              | 190 m @ 10% reflectivity                               |
|                              | 260 m @ 20% reflectivity                               |
|                              | 450 m @ 80% reflectivity                               |
| FOV                          | Non-repetitive scanning: 70.4° (H) × 77.2° (V)         |
|                              | Repetitive scanning: 70.4° (H) × 4.5° (V)              |
| Range Random Error           | 1σ (@ 20 m) < 2 cm                                     |
| Angular Random Error         | 1σ < 0.05°                                             |
| Beam Divergence              | 0.03° (H) × 0.28° (V)                                  |
| Data Rate                    | 240,000 pts/s (configurable first or strongest return) |
|                              | 480,000 pts/s (dual return)                            |
|                              | 720,000 pts/s (triple return)                          |
| False Alarm Rate (@ 100 klx) | < 0.0003%                                              |

💡

**Note:**

* Near-Field Blind Zone: When the target is less than 1 m from the Livox Avia, the Avia cannot measure it. When the target is within 1–3 m, the point cloud image may exhibit varying degrees of distortion.
* Test conditions: ambient temperature 25°C, target distance 20 m, reflectivity 80%. Under these conditions, the Avia’s range accuracy is 2 cm. Actual performance may vary depending on test conditions; please refer to actual measurement results.

### **Component Description** <a href="#block-b953b30a3b7847e9ba68d3f87e1f3e56" id="block-b953b30a3b7847e9ba68d3f87e1f3e56"></a>

**Livox Avia**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dd372559-f695-46c1-9142-3022b2ea9bef/image/w=1920,quality=90,fit=scale-down" alt="image" height="214.4999964498567" width="737.5499877929688">

1. Window
2. Laser beams are emitted through the window to scan objects within the FOV.
3. Aviation Power and Ethernet Cable
4. Users can quickly connect to the Livox Avia via the aviation power and Ethernet cable along with the power adapter socket 2.0. For the pin assignments of the aviation power and Ethernet cable, please refer to the “Interface Definition” section.
5. Mounting Holes
6. The Avia can be secured in place using M3 screws through these mounting holes.
7. Alignment Holes
8. When designing a mounting bracket, these alignment holes can be used to improve the installation accuracy of the Avia. For detailed dimensions, please refer to the “Installation Dimensions” section.

**Power Adapter Socket 2.0**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/adf2e118-103f-4621-9744-fa8cfe8a8285/image/w=1920,quality=90,fit=scale-down" alt="image" height="206.28444510858176" width="737.5375366210938">

1. LiDAR Connector Interface
2. Connects to the LiDAR connector. The connector model used is JAE MX34012NF1, and the corresponding LiDAR connector model is JAE MX34012SF1.
3. Power Interface
4. Connects to an external power supply. The operating voltage of the power adapter socket 2.0 is 9–30 V. Therefore, when connecting the Avia to an external power supply via the power adapter socket 2.0, the external power supply output voltage can be 9–30 V. The connector model used is MOLEX 105313-1102, and the corresponding wire-to-board connector model is MOLEX 105307-1202.
5. Ethernet Interface
6. Connects to an Ethernet cable. Uses a standard RJ45 Ethernet interface.
7. Sync Signal Interface
8. Connects to a sync signal cable. The sync signal interface of the power adapter socket 2.0 supports 3.3 V LVTTL level synchronization, with a 3-pin internal core. For the signal pinout, please refer to Table 2.2.2. If a custom cable is required, the corresponding wire-to-board connector is Famfull 9.510A0-003-1R0, which is compatible with JST GHR-03V-S.

## **Interface Definition** <a href="#block-b5e7ac25bf6f46528559d6ea848aa0ac" id="block-b5e7ac25bf6f46528559d6ea848aa0ac"></a>

### **M12 Aviation Connector** <a href="#block-833c03f3b2d048b8ad4eabc1fca935e5" id="block-833c03f3b2d048b8ad4eabc1fca935e5"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/01b5b1c7-1e8c-4de1-99c8-6d9271daf564/image/w=1920,quality=90,fit=scale-down" alt="image" height="261.82316450639206" width="737.5750122070312">

The Livox Avia uses a high-reliability M12 aviation plug (male connector). This plug is an M12 12P A-CODE fully shielded male connector compliant with the IEC61076-2-101 standard, model Finecables MA12MAHD12STXXXB14, and meets IP67 protection requirements. Users can not only connect to the Avia via the aviation power and Ethernet cable along with the power adapter socket 2.0 to achieve power connection, control signal transmission, and data transfer, but can also replace the aviation power cable with other cables according to their own needs, thereby improving the system’s environmental protection (e.g., dustproof and waterproof capabilities).

**Conversion Cable**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c4d97969-5297-44da-ab51-628eda9da13c/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.7536349489829" width="737.5875244140625">

The aviation power and Ethernet cable is an optional accessory for the Livox Avia, with a cable length of 1.5 m. Users can connect the Livox Avia via the aviation power and Ethernet cable along with the power adapter socket 2.0.

The pin assignments and definitions for the Livox Avia M12 aviation connector and the aviation power and Ethernet cable are as follows:

Table 2.1.1 Aviation Power and Ethernet Cable Pin Assignment Table

| **LiDAR M12 Aviation Connector Pin** | **Connector Pin (Male/Female)** | **Signal**   | **Attribute** | **Description**            | **Wire Color**   |
| ------------------------------------ | ------------------------------- | ------------ | ------------- | -------------------------- | ---------------- |
| 1                                    | 1                               | POWER+       | Power         | DC 10 V – 15 V             | Blue/White       |
| 2                                    | 2                               | Ground       | Power         | Ground                     | Silver Bare Wire |
| 3                                    | 4                               | Ethernet-TX+ | Output        | 100BASE-TX, TX+            | Orange/White     |
| 4                                    | 5                               | Ethernet-TX- | Output        | 100BASE-TX, TX-            | Orange           |
| 5                                    | 8                               | Ground       | Power         | Ground                     | Silver Braid     |
| 6                                    | 12                              | Sync+        | Input         | RS485\_A, pulse per second | Gray/White       |
| 7                                    | 9                               | POWER+       | Power         | DC 10 V – 15 V             | Blue             |
| 8                                    | 3                               | Ground       | Power         | Ground                     | Silver Bare Wire |
| 9                                    | 6                               | Ethernet-RX+ | Input         | 100BASE-TX, RX+            | Green/White      |
| 10                                   | 7                               | Ethernet-RX- | Input         | 100BASE-TX, RX-            | Green            |
| 11                                   | 10                              | Ground       | Power         | Ground                     | Silver Braid     |
| 12                                   | 11                              | Sync-        | Input         | RS485\_B, pulse per second | Gray             |

**SYNC Signal Description**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2a13e594-2764-42bb-994d-8a38065330f0/image/w=1920,quality=90,fit=scale-down" alt="image" height="237.03055396218903" width="737.5875244140625">

## **Power Cable and Sync Signal Cable Interface** <a href="#block-59d966b4ed5a4e258028ab244d591abb" id="block-59d966b4ed5a4e258028ab244d591abb"></a>

The Livox Avia cable kit includes a power cable and a sync signal cable. The pin assignments are as follows:

### **Power Cable** <a href="#block-ef95bcda28824634905981a12e6999a5" id="block-ef95bcda28824634905981a12e6999a5"></a>

End A connects to the power interface of the power adapter socket 2.0, and End B can be connected to an external DC regulated power supply by the user. The power cable uses connector model MOLEX 105307-1202.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/62fa295a-325f-4a13-abdd-3dc1fd7ad069/image/w=1920,quality=90,fit=scale-down" alt="image" height="176.87350119904076" width="737.5625">

Table 2.2.1 Power Cable Pin Assignment

| **Pin** | **Signal** | **Type** | **Description**      | **Color** |
| ------- | ---------- | -------- | -------------------- | --------- |
| 1       | Power+     | Power    | DC 9–30 V (30 V max) | Red       |
| 2       | Ground     | Power    | Ground               | Black     |

### **Sync Signal Cable** <a href="#block-f2b303d5064e4fe3811f7b17a41cdd3a" id="block-f2b303d5064e4fe3811f7b17a41cdd3a"></a>

End A connects to the sync signal interface of the power adapter socket 2.0, and End B can be connected to an external sync signal by the user. The sync signal cable uses a 3-pin connector. The corresponding wire-to-board connector model is Famfull 9.510A0-003-1R0, which is compatible with JST GHR-03V-S. Refer to the Sync Signal section for more information.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f5acb95b-18a5-4319-9236-5649c1ad60db/image/w=1920,quality=90,fit=scale-down" alt="image" height="122.99775496389893" width="565.953125">

Table 2.2.2 Sync Signal Cable Pin Assignment

| **Pin** | **Signal** | **Type** | **Description**                     | **Color** |
| ------- | ---------- | -------- | ----------------------------------- | --------- |
| 1       | Ground     | Power    | Ground                              | Black     |
| 2       | Sync+      | Input    | 3.3 V LVTTL level, pulse per second | Blue      |
| 3       | Reserved   | Reserved | Undefined signal                    | White     |

## **Ethernet Interface** <a href="#block-a27b0f5a7c2e44708a8ed60c36c3b954" id="block-a27b0f5a7c2e44708a8ed60c36c3b954"></a>

For ease of debugging, the Avia’s power adapter socket 2.0 directly supports a standard RJ45 Ethernet interface compliant with the 100BASE-TX standard. The Avia uses two twisted pairs for transmitting and receiving data.

## **Installation** <a href="#block-fb4729fd53144210a48ec1c473cfcdf9" id="block-fb4729fd53144210a48ec1c473cfcdf9"></a>

### **Effective Field of View (FOV) Range** <a href="#block-fc7eb5fc9bd64aa49655e1fc3e7c983d" id="block-fc7eb5fc9bd64aa49655e1fc3e7c983d"></a>

The Livox Avia has a FOV of 70.4° horizontally and 77.2° vertically, as shown in the figure below. When installing, please pay attention to the effective FOV range to avoid obstruction.

You can download the 3D model of the Avia and its FOV at [www.livoxtech.com/avia](http://www.livoxtech.com/avia).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/441fac01-750c-41a5-acd6-aa5a54bf1acb/image/w=1920,quality=90,fit=scale-down" alt="image" height="259.50832903826677" width="737.5499877929688">

Please note that the effective range of the Livox Avia varies across different areas of the FOV. The effective range becomes shorter toward the edges of the FOV, and approaches its maximum value toward the center of the FOV. Refer to the figure below for details:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c0c2e701-7cd7-4c0c-936c-cd62858ed315/image/w=1920,quality=90,fit=scale-down" alt="image" height="234.00722351499846" width="634.3409423828125">

## **Installation Precautions** <a href="#block-625437c0719d44b3b7e7d37d5a1cd6ad" id="block-625437c0719d44b3b7e7d37d5a1cd6ad"></a>

Before installing the Livox Avia, please read the following precautions:

1. Remove the protective film from the window glass before use.
2. Heavy dust or dirt on the window glass will affect the performance of the LiDAR. It is recommended to clean it using an air blower, alcohol, or an optical cleaning cloth as described in the maintenance section of this document. Perform the cleaning before installation.
3. When installing the LiDAR, do not block its FOV (as shown in Figure 3.1.1). Even installing transparent glass in front of the window can affect the LiDAR’s performance.
4. There is no restriction on the mounting orientation of the LiDAR; it can be mounted using its top, bottom, left, or right surfaces. During installation, it is recommended to keep the mounting surface parallel to the ground.
5. The LiDAR mounting structure only guarantees its own reliability. No additional load should be applied to the LiDAR body.

## **Installation Dimensions** <a href="#block-575e238c8a0d4cecb0d0299ae94ef9a1" id="block-575e238c8a0d4cecb0d0299ae94ef9a1"></a>

Install the Livox Avia in the appropriate position according to the dimensions below. M3 screws can be used for mounting. The top and bottom surfaces of the Avia are symmetrical about the optical axis, and the left and right surfaces are also symmetrical about the optical axis, so the Avia can be mounted using any surface.

The Livox Avia can also be mounted to the appropriate position using a mounting adapter plate (sold separately).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/51742fc4-f999-432e-bd02-97cfcb5d27b0/image/w=1920,quality=90,fit=scale-down" alt="image" height="267.17837879606776" width="737.5875244140625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/567bba6c-f0a1-4fd3-a12d-4e2d0b85e74e/image/w=1920,quality=90,fit=scale-down" alt="image" height="293.5593585622443" width="737.5625">

## **Power Adapter Socket 2.0** <a href="#block-5c2a3fe5e4cf472fb86cfcfda0a0ef68" id="block-5c2a3fe5e4cf472fb86cfcfda0a0ef68"></a>

If you need to use the Livox power adapter socket 2.0, install it in the appropriate position according to the dimensions of the power adapter socket and the mounting hole locations shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/76520c94-b947-4fbf-97c2-9b5e46e4082e/image/w=1920,quality=90,fit=scale-down" alt="image" height="292.23351567120045" width="737.5625">

Table 3.3.1 Power Adapter Socket 2.0 Weight and Dimensions

| **Weight** | **Approx. 88 g** |
| ---------- | ---------------- |
| Dimensions | 74 × 52 × 23 mm  |

## **Preparation** <a href="#block-ba7bcf6bf44549e282d33321fac4201f" id="block-ba7bcf6bf44549e282d33321fac4201f"></a>

### **Designing an External Power Supply** <a href="#block-f2b019e7c4d342d886652c4822153544" id="block-f2b019e7c4d342d886652c4822153544"></a>

The operating voltage of the Livox Avia is 10–15 V, with 12 V recommended. When extending the cable, please consider increasing the output voltage of the external power supply to compensate for the additional voltage drop caused by the cable extension, but the maximum voltage must not exceed 15 V. At low temperatures, the minimum operating voltage should be increased accordingly. Please note that voltage fluctuations above 15 V on the cable caused by certain reasons (e.g., interference, sudden power-off of other devices connected in parallel to the same power supply, etc.) may cause the device to malfunction or even be damaged.

Under normal conditions, the power consumption of the Livox Avia is 9 W. At low temperatures, such as -20°C to -10°C, the Avia will automatically enter a self-heating mode for no less than 3 minutes based on its own status. During self-heating mode, the maximum power consumption of the Avia can reach up to 31 W. Depending on the ambient temperature, the power consumption of the Avia varies, as shown in the figure below. Please design the power supply reasonably based on the actual operating power of the Avia.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/67c5a138-35f5-4c85-83d8-adc5857b3964/image/w=1920,quality=90,fit=scale-down" alt="image" height="260.13339189114254" width="737.5875244140625">

## **Connecting** <a href="#block-9c1ea4db46b849faa0e27b3a70ed8a8b" id="block-9c1ea4db46b849faa0e27b3a70ed8a8b"></a>

The M12 aviation connector of the Livox Avia provides external power and transmits data. For the specific pin assignments of this connector, please refer to the Interface Definition section. For temporary testing or use of the Livox Avia, it is recommended to use the Livox power adapter socket 2.0 along with the aviation power and Ethernet cable. The Livox power adapter socket 2.0 integrates the LiDAR connector interface, sync signal interface, power interface, and Ethernet interface.

The Livox Avia communicates via the UDP network protocol and supports two IP modes: Dynamic IP address mode and Static IP address mode. All Livox Avia units are factory-configured with Static IP enabled by default, with an IP address of 192.168.1.1XX (where XX is the last two digits of the serial number), a subnet mask of 255.255.255.0, and a default gateway of 192.168.1.1. On first use, the device can be connected directly to a computer without a router. The connection method differs depending on the IP address mode:

1. Static IP (factory default, can be connected directly to a computer);
2. Dynamic IP (uses DHCP to assign an address. The device must be switched to Dynamic IP mode using Livox Viewer or the SDK, and then connected via a router).

### **Static IP:** <a href="#block-f3c32d25cca24b14811006f5054053c4" id="block-f3c32d25cca24b14811006f5054053c4"></a>

Before connecting, set the computer’s IP to a static IP. The configuration method is as follows:

**Windows® System**

a. In the Control Panel, go to Network and Sharing Center.

b. Click “Ethernet” to open the Ethernet status window, then click the “Properties” button to enter Ethernet properties.

c. Double-click “Internet Protocol Version 4 (TCP/IPv4)”.

d. Set the IP address to 192.168.1.50, and the subnet mask to 255.255.255.0, then click “OK” to complete the static IP settings for the computer.

**Ubuntu™ 16.04 System**

1. The IP address can be configured in the terminal using the `ifconfig` command. Example code is as follows:
2. \~$ sudo ifconfig enp4s0 192.168.1.50 (replace `enp4s0` with the actual network interface name of your machine)
3. After the computer’s static IP address has been set, please connect as shown in the figure.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f1050abd-55c3-46ad-b46f-3360c4c4ba41/image/w=1920,quality=90,fit=scale-down" alt="image" height="350.01094685628743" width="737.5625">

a. Connect the Livox Avia to the aviation power and Ethernet cable, then plug the LiDAR connector on the aviation power and Ethernet cable into the LiDAR connector interface of the power adapter socket 2.0.

b. Use an Ethernet cable to connect the power adapter socket 2.0 to your PC.

c. Connect the external power supply through the power interface of the power adapter socket 2.0.

💡

**Note:**

* If you need to connect multiple Livox Avia units in Static IP mode to the PC simultaneously, set each Livox Avia to a different IP address and connect them via a network switch.
* After connecting as shown in Figure 4.2.1, run Livox Viewer on the computer, select the device for which you want to change the static IP address, and click to enter the device parameter settings interface to set the static IP address for that Livox Avia.
* If connecting more than 6 Livox Avia units, please use a Gigabit switch; otherwise, data loss or connection failures may occur.

## **Dynamic IP:** <a href="#block-260587e6f63541a496318e83f3accb7d" id="block-260587e6f63541a496318e83f3accb7d"></a>

1. First, connect the Livox Avia, the power adapter socket 2.0, the external power supply, and the computer as shown in Figure 4.2.1.
2. Run Livox Viewer on the computer, and in the device parameter settings interface, set the IP address of the LiDAR on the local network to Dynamic IP.
3. After the settings are completed, disconnect all connections to the Livox Avia. Note that the Dynamic IP settings will take effect after a reboot.
4. Then, set the computer to Dynamic IP mode. The configuration method is as follows:

Windows System

a. In the Control Panel, go to Network and Sharing Center.

b. Click “Ethernet” to open the Ethernet status window, then click the “Properties” button to enter Ethernet properties.

c. Double-click “Internet Protocol Version 4 (TCP/IPv4)”.

d. Select “Obtain an IP address automatically” and “Obtain DNS server address automatically”, then click “OK” to complete the dynamic IP settings for the computer.

**Ubuntu 16.04 System**

a. Open the Ubuntu network connection editor.

b. In the network connection editor, proceed as follows: edit the connection name, then select “Automatic (DHCP)” in the “Method” option, and finally click “Save”.

1. After the dynamic IP settings for both the Livox Avia and the computer have been completed, please connect as shown in the figure.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6f492b15-3ec8-4c38-8b18-0db1a8fe9760/image/w=1920,quality=90,fit=scale-down" alt="image" height="419.14524405877904" width="737.5750122070312">

a. Connect the Livox Avia to the aviation power and Ethernet cable, then plug the LiDAR connector on the aviation power and Ethernet cable into the LiDAR connector interface of the power adapter socket 2.0.

b. Use an Ethernet cable to connect both the power adapter socket 2.0 and your PC to the LAN ports of a router.

c. Connect the external power supply through the power interface of the power adapter socket 2.0.

💡

* If you need to connect more than 6 Livox Avia units simultaneously, please use a Gigabit router. Note that all Livox Avia units and the PC should be connected to LAN ports.
* The broadcast code of each LiDAR can be viewed via the device manager in Livox Viewer or through the SDK. The broadcast code of the Livox Avia is the serial number with an additional character “1” appended at the end.

## **Usage** <a href="#block-7fc311f6978143bb89b7fc65a3235da9" id="block-7fc311f6978143bb89b7fc65a3235da9"></a>

### **Coordinate System** <a href="#block-39ed428df5f44f6a91c5184ff9e8f13a" id="block-39ed428df5f44f6a91c5184ff9e8f13a"></a>

The Livox Avia has a built-in IMU. The definitions of the point cloud coordinate system O-XYZ and the IMU coordinate system O’-X’Y’Z’ are shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8ecbeb5d-3a8d-4cd5-8935-3ffb050510d0/image/w=1920,quality=90,fit=scale-down" alt="image" height="241.43642485913614" width="737.5750122070312">

The coordinates of the IMU origin O’ in the point cloud coordinate system O-XYZ are ((-41.65, -23.26, 28.40)) (unit: mm).

### **Output Data** <a href="#block-e3d93ec85c044c7692454bac499a35aa" id="block-e3d93ec85c044c7692454bac499a35aa"></a>

The output data of the Livox Avia includes point cloud data and IMU data. Both the point cloud data and IMU data contain timestamp information and status indicator code information, while the point cloud data additionally includes target reflectivity, coordinate information, and flag information.

### **Point Cloud Data** <a href="#block-3576fc8eb9374737a15628359270c777" id="block-3576fc8eb9374737a15628359270c777"></a>

Point cloud data is the total set of all points detected by the LiDAR on the surface of objects within the field of view. Each point cloud contains the following information:

* **Target Reflectivity**: Expressed as a value from 0 to 255. Values 0 to 150 correspond to reflectivity between 0% and 100% for diffuse scattering objects; values 151 to 255 correspond to total reflection objects.
* **Coordinate Information**: The coordinate information of the Livox Avia can be represented as Cartesian coordinates ((x, y, z)) or spherical coordinates `(r, Θ, Φ)`. The relationship between Cartesian coordinates and spherical coordinates is shown in the figure below. If no object is detected ahead or the detected object is beyond the range (e.g., 600 m), the point cloud output is ((0, 0, 0)) in Cartesian coordinates, and (0, Θ, Φ) in spherical coordinates.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/929e70ac-009c-4022-94d1-e3836aa08568/image/w=1920,quality=90,fit=scale-down" alt="image" height="296.6111559139785" width="737.5625">

**Tag**: Primarily indicates multi-echo information and noise information. The format of the tag information is as follows:

| bit7     | bit6 | bit5                                                               | bit4 | bit3                                                                                                                                 | bit2 | bit1                                                                                                                                                             | bit0 |
| -------- | ---- | ------------------------------------------------------------------ | ---- | ------------------------------------------------------------------------------------------------------------------------------------ | ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| Reserved |      | Return number: 00: return 0 01: return 1 10: return 2 11: return 3 |      | Point property based on intensity: 00: Normal 01: High confidence level of noise 10: Moderate confidence level of noise 11: Reserved |      | Point property based on spatial position: 00: Normal 01: High confidence level of noise 10: Moderate confidence level of noise 11: Low confidence level of noise |      |
|          |      |                                                                    |      |                                                                                                                                      |      |                                                                                                                                                                  |      |
|          |      |                                                                    |      |                                                                                                                                      |      |                                                                                                                                                                  |      |
|          |      |                                                                    |      |                                                                                                                                      |      |                                                                                                                                                                  |      |
|          |      |                                                                    |      |                                                                                                                                      |      |                                                                                                                                                                  |      |

Each tag is 1 byte in length. In this byte, bit7 and bit6 form the first group, bit5 and bit4 form the second group, bit3 and bit2 form the third group, and bit1 and bit0 form the fourth group.

The second group indicates the echo order of the sampled point. Since the Livox Avia uses a coaxial optical path, even when there is no external object to be measured, its internal optical system generates an echo, which is recorded as the 0th echo. Subsequently, if there is a detectable object in the laser emission direction, the first laser echo returning to the system is recorded as the 1st echo, followed by the 2nd echo, and so on. If the detected object is too close (e.g., 1.5 m), the 1st echo will be merged into the 0th echo, and this echo is recorded as the 0th echo.

The third group determines whether the sampled point is noise based on the echo energy intensity. Typically, noise points caused by interference such as dust, rain, fog, or snow have very low echo energy. Currently, noise confidence levels are classified into three grades based on echo energy intensity: 01 indicates very weak echo energy, indicating a high probability that such sampled points are noise (e.g., dust points); 10 indicates medium echo energy, indicating a medium probability that such sampled points are noise (e.g., rain and fog noise). The lower the noise confidence, the lower the probability that the point is noise.

The fourth group determines whether the sampled point is noise based on its spatial position. For example, when the LiDAR measures two objects at very close distances, filamentous noise may occur between the two objects. Currently, noise confidence is classified into three grades. The lower the noise confidence, the lower the probability that the point is noise.

💡

**Note**: The intensity-based point attribute and spatial-based point attribute functions are not yet available for the Livox Avia. If you have any requirements, please contact Livox.

## **Timestamp** <a href="#block-ff89e5a67b564ba79093c22cb0534937" id="block-ff89e5a67b564ba79093c22cb0534937"></a>

The point cloud data and IMU data of the Livox Avia contain timestamp information. The Livox Avia supports three synchronization methods: IEEE 1588-2008 synchronization, pulse synchronization (PPS), and GPS synchronization (PPS+UTC).

**IEEE 1588-2008**: IEEE 1588-2008 refers to the “Precision Time Protocol,” which enables precise clock synchronization for measurement and system control via Ethernet. The Livox LiDAR, as an ordinary clock in PTP, supports only UDP/IPv4. The Livox LiDAR supports the following message formats: Sync, Follow\_up, Delay\_req, and Delay\_resp.

**PPS**: Pulse synchronization is achieved via the sync signal cable. Refer to the Interface Definition section for more information. The synchronization logic is shown in the figure below. The pulse period of the pulse synchronization is ( t0 = 1000 , \text{ms} ), and the high level duration is ( t1 = (20 , \text{ms} < t1 < 200 , \text{ms}) ). When the rising edge of the pulse synchronization arrives, the timestamp in the point cloud is reset to zero. Therefore, the timestamp in the point cloud data represents the interval between the point cloud data sampling and the previous pulse synchronization rising edge.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/514f39b0-b14a-4788-9d50-9d1844ec0e9f/image/w=1920,quality=90,fit=scale-down" alt="image" height="151.15309718100892" width="565.984375">

**GPS Synchronization**: GPS synchronization is achieved via the sync signal cable and UTC time. The PPS interface logic is consistent with the PPS synchronization method described above. Users can send the UTC time of each pulse to the Avia via the SDK communication protocol. The logic of the UTC time command is shown in the figure below. When GPS synchronization is used, the timestamp in the point cloud data represents the UTC time of the point cloud sampling. For specific communication commands, please refer to the relevant sections of the SDK communication protocol.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ec066c26-09fb-425a-96d6-a7c102904e7e/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.80873226950354" width="565.984375">

## **Status Indication** <a href="#block-6699817462d54b4e98dff0c58a036723" id="block-6699817462d54b4e98dff0c58a036723"></a>

The point cloud data and IMU data of the Livox Avia contain status indicator code information. The status indicator code displays the current operating status of the Livox Avia. Through the status indicator code, users can check the temperature status, voltage status, motor status, remaining service life warning, and pulse synchronization signal status. Users can view the status indicator code in Livox Viewer or via the SDK. Refer to the Device Management Window section of the Livox Viewer User Manual for instructions on how to view the status indicator code.

| **Status**                          | **Description**                                                                                                                                                                            |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Temperature Status                  | Indicates whether there is a temperature anomaly. Temperature status includes: Normal, Warning, and Error.                                                                                 |
| Voltage Status                      | Indicates whether there is an internal voltage anomaly. Voltage status includes: Normal, Warning, and Error.                                                                               |
| Motor Status                        | Indicates whether there is an internal motor anomaly. Motor status includes: Normal, Warning, and Error.                                                                                   |
| Contamination Warning               | Indicates whether heavy dust or object obstruction is detected on the window.                                                                                                              |
| Remaining Service Life Warning      | Indicates whether the LiDAR is approaching the end of its service life. When this warning appears, the LiDAR can still be used for a period of time; please replace it in a timely manner. |
| Pulse Synchronization Signal Status | Indicates whether the pulse synchronization signal is properly connected.                                                                                                                  |

## **Operating Status and Operating Modes** <a href="#block-d49638ac8bc541c38aa8a17371adbbbe" id="block-d49638ac8bc541c38aa8a17371adbbbe"></a>

The operating status of the Livox Avia includes Initialization Status, Normal Operating Status, Standby Status, Low-Power Status, and Error Status.

| **Operating Status**    | **Description**                                                                                                            |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Initialization Status   | The LiDAR is booting up.                                                                                                   |
| Normal Operating Status | The LiDAR has started up and is operating normally.                                                                        |
| Standby Status          | The LiDAR has started up, but the laser beam has not yet been emitted.                                                     |
| Low-Power Status        | All parts except the communication module have stopped working.                                                            |
| Error Status            | After a fault is detected, the LiDAR will enter Error Status. All parts except the communication module will be shut down. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dc45caf4-10ad-40a9-b2ef-92cb3abc2a3f/image/w=1920,quality=90,fit=scale-down" alt="image" height="258.3689911706998" width="565.96875">

The Livox Avia has three operating modes: Normal Operating Mode, Standby Mode, and Low-Power Mode. Users can switch between different operating modes via Livox Viewer or the SDK.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/da0971ff-e2ee-47db-badc-dbfcbd66c0ca/image/w=1920,quality=90,fit=scale-down" alt="image" height="204.40248786407767" width="565.953125">

## **Multi-echo Mode** <a href="#block-8505ea32754d4c0d9b3cd5144d422ea9" id="block-8505ea32754d4c0d9b3cd5144d422ea9"></a>

The Livox Avia supports multi-echo mode, which can be configured via Livox Viewer or the SDK. When multi-echo mode is enabled, Livox will output up to three echoes per point.

The Livox Avia outputs 240,000 points per second by default. When dual-echo mode is enabled, the output rate increases to 480,000 points per second; when triple-echo mode is enabled, the output rate increases to 720,000 points per second. To quickly configure the echo mode using Livox Viewer, follow these steps:

After properly connecting the Avia, select the device you wish to configure, then enter the device parameter settings interface to change the echo mode.

## **IMU Sensor Information** <a href="#block-31b0da5ac2f147729a107bac7b7c26ab" id="block-31b0da5ac2f147729a107bac7b7c26ab"></a>

The Avia features a built-in IMU sensor that provides attitude data for the Avia.

Users can set the IMU data push frequency via Livox Viewer or the SDK. The configuration method is similar to that of the multi-echo mode.

## **Troubleshooting** <a href="#block-309e014240494501a1e2b6bdf2c29ed3" id="block-309e014240494501a1e2b6bdf2c29ed3"></a>

If you encounter any issues during use, please refer to the table below for solutions. If the problem persists, please contact Livox or an authorized Livox dealer.

| **Problem**                                                                                  | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Livox LiDAR cannot be detected                                                               | • Confirm that all cables are properly connected. • Confirm that the voltage is correct. The operating voltage of the Livox Avia LiDAR is 10–15 V. When connected via the Livox power adapter socket 2.0, an external power supply of 9–30 V is supported. • Confirm that the Livox LiDAR is not connected to other software. • Confirm that the PC and the device are on the same local network. • Confirm that no antivirus software or other programs that block Ethernet broadcasts are installed.After the above checks are completed, if the device still cannot be detected, please close all firewalls and restart Livox Viewer, then search for the LiDAR on the local network again.Use a network packet analysis tool (e.g., Wireshark) to analyze UDP packets. |
| Livox LiDAR is detected but connection cannot be established / or sampling cannot be started | • Confirm that all cables are properly connected. • Confirm that the voltage is correct. The operating voltage of the Livox Avia LiDAR is 10–15 V. When connected via the Livox power adapter socket 2.0, an external power supply of 9–30 V is supported.If the problem persists, please restart the LiDAR and the Livox Viewer software.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| No data                                                                                      | Use a network packet analysis tool (e.g., Wireshark) to analyze the output data.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

## After-Sales Information <a href="#block-dedab47d7a2b4a6684ce77fcccc5f9b0" id="block-dedab47d7a2b4a6684ce77fcccc5f9b0"></a>

Visit [www.livoxtech.com/support](http://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox LiDAR sensors.

## Appendix <a href="#block-7e0e93de88d049039f9c2fd7b9e80a16" id="block-7e0e93de88d049039f9c2fd7b9e80a16"></a>

### Appendix 1 <a href="#block-553b58fdb2d744faad76c92e83bcc636" id="block-553b58fdb2d744faad76c92e83bcc636"></a>

Livox Avia Dimensions (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9f6fd650-1a31-448a-a0d1-510220bb3590/image/w=1920,quality=90,fit=scale-down" alt="image" height="229.35759839650146" width="565.96875">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6e80af90-0920-4219-bf2d-9441b84fa818/image/w=1920,quality=90,fit=scale-down" alt="image" height="192.62230662983424" width="565.984375">

## Appendix 2 <a href="#block-2833918e162c462a8bbaf72c4e457e72" id="block-2833918e162c462a8bbaf72c4e457e72"></a>

Livox Converter 2.0 Dimensions (Unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3001bdf3-1327-4662-8beb-ab2939d97a1d/image/w=1920,quality=90,fit=scale-down" alt="image" height="201.62002314814814" width="565.984375">

## **Specifications** <a href="#block-3d4b20849ac94a1e9ea4dfb3ba4173d9" id="block-3d4b20849ac94a1e9ea4dfb3ba4173d9"></a>

| **Specification**            | **Parameter**                                                                                                  |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Laser Wavelength             | 905 nm                                                                                                         |
| Eye Safety Level             | Class 1 (IEC 60825-1:2014) Eye Safe                                                                            |
| Range (@ 100 klx)            | 190 m @ 10% reflectivity 230 m @ 20% reflectivity 320 m @ 80% reflectivity                                     |
| Range (@ 0 klx)              | 190 m @ 10% reflectivity 260 m @ 20% reflectivity 450 m @ 80% reflectivity                                     |
| FOV                          | Non-repetitive scanning: 70.4° (H) × 77.2° (V)Repetitive scanning: 70.4° (H) × 4.5° (V)                        |
| Range Random Error           | 1σ (@ 20 m) < 2 cm                                                                                             |
| Angular Random Error         | 1σ < 0.05°                                                                                                     |
| Beam Divergence              | 0.03° (H) × 0.28° (V)                                                                                          |
| Point Cloud Output           | 240,000 pts/s (configurable first or strongest return)480,000 pts/s (dual return)720,000 pts/s (triple return) |
| Data Latency                 | ≤ 2 ms                                                                                                         |
| Data Synchronization Methods | IEEE 1588-2008 (PTPv2), PPS (Pulse Per Second), GPS (PPS+UTC)                                                  |
| False Alarm Rate (@ 100 klx) | < 0.0003%                                                                                                      |
| Protection Level             | IP67                                                                                                           |
| IMU                          | Built-in IMU model: BMI088                                                                                     |
| Operating Temperature        | -20°C to 65°C                                                                                                  |
| Storage Temperature          | -40°C to 85°C                                                                                                  |
| Protection Rating            | IP67                                                                                                           |
| Power Consumption            | Repetitive scanning mode: 9 W (16 W at startup)Non-repetitive scanning mode: 8 W (16 W at startup)             |
| Supply Voltage Range         | Livox Avia: 10–15 VDC (12 V DC power supply > 31 W recommended)Power adapter socket 2.0: 9–30 VDC              |
| Noise                        | < 45 dBA at 40 cm (omnidirectional)                                                                            |
| Dimensions                   | 91 × 61.2 × 64.8 mm                                                                                            |
| Weight                       | Approx. 498 g (excluding cables) Power Adapter Socket 2.0                                                      |
| Supply Voltage Range         | 9–30 V DC                                                                                                      |
| Dimensions                   | 74 × 52 × 23 mm                                                                                                |
| Weight                       | 88 g                                                                                                           |
