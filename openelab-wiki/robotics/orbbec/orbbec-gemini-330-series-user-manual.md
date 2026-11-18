# Orbbec Gemini 330 Series User Manual

{% hint style="info" %}
[**View Orbbec Gemini 330 camera family on OpenELAB**](https://openelab.io/products/orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging)

**Model/family:** Orbbec Gemini 330 camera family · **OpenELAB SKUs:** `ORBBEC-Gemini-336L`, `ORBBEC-Gemini-335L`, `ORBBEC-Gemini-336`, `ORBBEC-Gemini-335Le` · Check the exact variant and documented differences before using shared instructions.
{% endhint %}

## Orbbec Gemini 335 Stereo Vision Camera with Infrared Imaging

{% embed url="https://openelab.io/products/orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging" %}

## Orbbec Gemini 335L Stereo Vision Camera with Infrared Imaging

{% embed url="https://openelab.io/products/orbbec-gemini-335l-stereo-camera" %}

## Orbbec Gemini 336 IR-Pass Stereo Depth Camera with Anti-Glare Infrared Imaging

{% embed url="https://openelab.io/products/orbbec-gemini-336-stereo-vision-camera-with-infrared-imaging" %}

## Orbbec Gemini 336L Stereo Vision Camera with Infrared Imaging

{% embed url="https://openelab.io/products/orbbec-gemini-336l-stereo-camera" %}

## Orbbec Gemini 335Lg Stereo Vision 3D Camera IP65 GMSL2/FAKRA

{% embed url="https://openelab.io/products/orbbec-gemini-335lg-stereo-vision-3d-camera-ip65-gmsl2-fakra" %}

## Orbbec Gemini 335Le Stereo Vision Camera with Infrared Imaging

{% embed url="https://openelab.io/products/orbbec-gemini-335le-stereo-vision" %}

### About Orbbec Gemini 330 Series

#### **1. Series Introduction**

The Orbbec Gemini 330 series stereo vision 3D cameras integrate Orbbec’s latest proprietary depth engine ASIC MX6800, combining active and passive stereo vision technologies for seamless operation in both indoor and outdoor conditions. By performing depth image generation and spatial alignment of depth images to color images internally, cameras in the Gemini 330 series achieve minimal data latency and significantly reduce reliance on the computing power of host computers. These cameras are preset with multiple operating modes, making them adaptable and efficient for various application scenarios. A flexible and comprehensive frame synchronization mechanism simplifies and enhances the scalability of multi-camera operations.

The Gemini 330 series continues expanding its product offerings through modular design to meet diverse application needs. This flexibility allows for options such as compact short baseline, high-precision long baseline, hardware interface suitable for specific scenarios, robust protective enclosure, and depth filter reducing glare, etc. Current models include:\
● flagship and foundational Gemini 335 and Gemini 335L\
● IR-enhanced Gemini 336 and Gemini 336L\
● GMSL2/FAKRA-powered Gemini 335Lg\
● Gigabit Ethernet with PoE-powered Gemini 335Le

Each camera in the Orbbec Gemini 330 series includes the following components:\
● Orbbec’s latest proprietary depth engine ASIC MX6800\
● Stereo IR Module\
● Laser Diode Module (LDM)\
● RGB Module\
● Laser Ranging Module (LRM)\
● IMU Module\
● Orbbec SDK\
● Wrappers (e.g., ROS1 / ROS2 / Python)

Gemini 335Lg contains an extra serializer board module to transmit GMSL2 data.

Orbbec Gemini 330 series cameras are available on [Orbbec online store](https://store.orbbec.com/), which also offers a wide selection of multi-camera synchronization accessories.

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/bqyIU1Xa4iu68Pi0xqG0/assets/da2267c66aaae872f6ae.webp)

#### **2. Orbbec SDK**

The Orbbec SDK provides low-level sensor access to Gemini 330 series cameras hardware sensors and device configuration. For more details on the Orbbec SDK, please refer to [Orbbec SDK architecture](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Orbbec%20SDK%20Architecture).

#### **3. Orbbec SDK Features**

The Orbbec SDK offers the following features, ready to use on the Gemini 330 series cameras upon installation:

* Depth camera access and mode control
* HDR support for depth
* Depth post-processing (e.g. decimation filter, spatial filter, disparity to depth)
* RGB camera access and control (e.g., exposure and white balance)
* Synchronized depth and RGB camera streams with configurable inter-camera latency
* External device synchronization control with configurable inter-device latency offsets
* Motion sensor (gyroscope and accelerometer) access
* Point cloud access and control
* Camera frame metadata access for image resolution, timestamps, etc.
* Device calibration data access

#### **4. Camera Tools**

Orbbec provides the following tools:

* Orbbec Viewer tool, used for monitoring device data streams and configuring different modes,
* Orbbec Quality Assessment Tool, used for assessing camera depth quality.

For detailed instructions on using the Orbbec Viewer, please refer to [Explore camera functions in Orbbec Viewer.](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Explore%20Camera%20Function%20in%20Orbbec%20Viewer)

#### **5. Gemini 330 Series Hardware Requirements**

* Gemini 330 series specifications

[![Group 10.jpg](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/HwNyZth5b289fRLHtxgX/assets/9bdbdbac0eec2ac54ff2.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-12/group-10.jpg)

* The Gemini 330 series integrates Orbbec’s latest sensor technology into the camera. For detailed information, please refer to the [Orbbec Gemini 330 series Datasheet](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\)).

#### **6. Typical Scene Captures using Gemini 330 Series Cameras**

* \*\*Outdoor performance -\*\*Gemini 335/336

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/iRVyy2y5sa4ojixks8pS/assets/8aee70d48996f6988b3a.webp) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rJRMqHeVRlX9A45Ycco2/assets/3c21af0c692d12729823.webp) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

* **Outdoor performance - Gemini 335L/336L/335Lg/335Le**

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/DnEaOj6YGas0slZis5MD/assets/3b845f0c69a7e409d5c1.webp) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/eyGkaSm5OXSPITBll0FQ/assets/2fbe7abe0f012e737a72.webp) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

* **Indoor performance - Gemini 335/336**

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oW4m06hU3cr1CZgrkdgf/assets/9c023e794e5af1055636.webp) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/vSVTxPpDS2jN6AoErgHj/assets/4de00059b9151d8e807e.webp) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

* **Indoor performance - Gemini 335L/336L/335Lg/335Le**

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/XQrPsk7Rwh0crEubV07j/assets/2149bcb85c44548e599a.webp) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/g61QDiEJiZLZFZ3Jmvnm/assets/0f999758fc052506c0b2.webp) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/1NOpDaNlrfSnQyNGKzvR/assets/46b3c254d7ac9e2eaec7.webp) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Po2Q7mvqi6yCSN0JzDNC/assets/21fe138482198461fc2b.webp) |

* **Tiny objects recognition @ 2m**. The tiny cubic of 3cm x 3cm (the smallest cubic on the right side of the RGB figure below) is clearly visible in point cloud.

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jG61pynLfG7LUuc84fE8/assets/de3aad12c69ccc1164dc.webp)

### Gemini 330 Series Datasheet (Overall)

| **Interface** | **Product**              | **Datasheet**                                                                                                                                                                               | **Version** | **Release Date** |
| ------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ---------------- |
| USB           | Gemini 335/336/335L/336L | [Gemini 330 Series Datasheet for USB Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/04/22062452/Gemini-330-series-Datasheet-V1.6.pdf)                            | V1.6        | 2025-04-10       |
| GMSL          | Gemini 335Lg/338Lg       | [Gemini 330 Series Datasheet for GMSL Devices](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Series%20GMSL%20Datasheet-V1.2.pdf)                         | V1.2        | 2026-08-10       |
| Ethernet      | Gemini 335Le/338Le       | [Gemini 330 Series Datasheet for Ethernet Devices](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf) | V1.0        | 2026-08-10       |

### Camera Interface Selection Guide

Coming soon

### Gemini 330 Series Quickstart Guide (Overall)

| **Interface** | **Product**              | **Quickstart Guide**                                                                                                                                                                           |
| ------------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB           | Gemini 335/336/335L/336L | [Gemini 330 Series Quickstart Guide (USB)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))           |
| GMSL          | Gemini 335Lg             | [Gemini 330 Series Quickstart Guide (GMSL)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(GMSL\))         |
| Ethernet      | Gemini 335Le             | [Gemini 330 Series Quickstart Guide (Ethernet)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Ethernet\)) |

### Gemini 330 Series Quickstart Guide (USB)

#### **1. What's in The Box for Orbbec Gemini\*\*\*\*335/336?**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7d9Z0jhBPHp35jXJ1tlC/assets/706f8f2c31e786855743.webp)

#### **2. What's in The Box for Orbbec Gemini 335L/336L?**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8MBn2nPrxgGnIr6Pnse6/assets/c6da0112ab3ded1155f3.webp)

#### **3. Connect the Orbbec Camera**

* **For** **Orbbec Gemini 335/336**

① Assemble the tripod head with the tripod, and then secure the camera onto the assembled tripod, as illustrated in Step 1 below.

② Use the USB-C to USB-A cable to connect the camera’s Type-C port, as shown in Step 2 below.

③ Connect the USB-A connector to the host using the same USB-C to USB-A cable, as shown in Step 3 below.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/bom1TVTpT7SRhNpHa8pc/assets/3455ffc0ab614c367559.webp)

* **For** **Orbbec Gemini 335L/336L**

① Assemble the tripod head with the tripod, and then secure the camera onto the assembled tripod, as illustrated in Step 1 below.

② Use the USB-C to USB-A cable to connect the camera’s Type-C port, as shown in Step 2 below.

③ Connect the USB-A connector to the host using the same USB-C to USB-A cable, as shown in Step 3 below.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/395UoRCpT2qePG9i7gHs/assets/958b83d8c334b1ff311a.webp)

#### **4. Get Orbbec Viewer**

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/OiVk7UTyqnjO8xjVgaed/assets/47407f5e9ff14d37bdc1.webp)

#### **5. Launch Orbbec Viewer**

1. After starting the Orbbec Viewer, please make sure that the tool recognizes the 3D camera, as indicated by the following image.

Remark:If the camera is not recognized, please check to ensure that the camera and the host are properly connected. You can try disconnecting and then reconnecting the USB cable. If it still isn’t recognized, consider replacing the USB cable or verifying whether the host computer’s power supply meets the required specifications.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zNsgeJtS5i7lpOlo6dfc/assets/8f5e5c1b26053f90be1c.webp)

1. Toggle the ‘**Depth’** button at the top of the tool to start and preview the depth stream.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/HFvzAtZE1R6bRYkqyDB3/assets/f073ca3f645bc8c4f400.webp)

1. Toggle the ‘**Color**‘ button at the top of the tool to start and preview the color stream. The color stream and depth stream will be displayed side by side.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AHvrGxmNuKMbnBfjxHWA/assets/d9850739c0cd1996d773.webp)

1. Toggle the ‘**IR Left’** and **‘IR Right’** buttons at the top of the tool to strat and preview the IR stream.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Cnkru8wHIjPTNeMU1BCK/assets/b435f7f6992b1af403d5.webp)

1. Toggle the ‘**IMU’** button at the top of the tool to start and preview the IMU stream.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/0F3uqr0hp1YZAXJKBJ95/assets/5fb5a2f22b9529205cd3.webp)

1. Toggle the![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/REbeSxqOY3UwD5Wc6buc/assets/9065d80891795244d335.webp) button on the top of each window to show the metadata information.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5VjRZP6oq4Go5ob0AZ80/assets/7156eb03675ed6353e7f.webp)

1. Toggle the ‘**PointCloud‘** button at the top of the tool to start and preview the 3D point cloud

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/mvRpBBoAVRHsNdp6Cmog/assets/d23396696f7b97e63f22.webp)

1. Toggle the **‘Display’** button under the **‘Image View’** menu on the left to start and preview the D2C (depth to color registration) stream. The 3D point cloud and the D2C stream will be displayed side by side.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/RPJw8KKsczquDSmpxr2m/assets/318831d2f614080d6efd.webp)

1. The above are relevant operations for Orbbec Viewer version 1.9.4. There may be slight differences in updated versions. For detailed instructions, please refer to the Orbbec Viewer tutorial video below.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jTdFeLI7zYdkHxoK15oz/assets/de97abe23d68541795a9.webp)

[https://www.youtube.com/@Orbbec3d](https://www.youtube.com/@Orbbec3d)

#### **6.** ![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/cnHDrkVdK529EAiqvUrj/assets/3c79754847a03d90e16e.webp)**Caution**

1. Follow the instructions carefully when operating the camera. Improper handling may lead to damage to the internal components.
2. Do not drop the camera or expose the camera to mechanical stress.
3. Do not attempt to modify the camera as such modifications may cause permanent damage or performance degradation.
4. The temperature of the camera may rise during long periods of use.
5. Do not touch the lens. Fingerprints on the lens may affect image quality.
6. Keep the product beyond the reach of children or animals to avoid accidents.

7.If the computer does not recognize the camera, verify that the cable meets the power and data transfer requirements, then replug it into the USB port to reconnect.

8. This product is classified as a Class 1 Laser Product under the international standard EN/IEC 60825-1, Edition 3 (2014).

Using controls, adjustments, or procedures other than those specified herein may result in hazardous radiation exposure.

Safety and Handling Instructions:

●Avoid powering on the product if any external damage was observed.

●Do not attempt to open any portion of this product. There are no user serviceable parts.

●Be cautious of invisible laser radiation. Avoid direct exposure to the beam.

●To maintain compliance and safety standards, do not modify or service the product. Unauthorized modifications or servicing could result in emissions surpassing the Class 1 safety level.

●Only update the camera firmware with official releases that match the specific module SKU and revision to ensure proper functionality and safety.

### Gemini 330 Series Quickstart Guide (GMSL)

#### **Important Notice**

Dear Developer,\
To better support you in integrating and developing with the Gemini 335Lg camera, we have created a brand-new, more comprehensive GitHub repository. The details are as follows:\
New Repository URL: [https://github.com/orbbec/MIPI\_Camera\_Platform\_Driver](https://github.com/orbbec/MIPI_Camera_Platform_Driver)

The new repository contains:

* More complete official documentation
* The latest binary files
* Driver adaptation source code
* Rich development examples

Thank you for your support!

#### **1. Preparation**

**1.1 Hardware Requirements**

* Gemini 335Lg boxed camera
* NVIDIA Jetson AGX Orin DevKit and compatible power supply
* GMSL camera deserializer board (example model: FG96\_8CH\_GMSL(EVK)) and compatible power supply

Supported Camera and Platform Information

Table 1-1

| **Camera Model** | **Hardware Platform**   | **Manufacturer** | **Software Version** | **GMSL Adapter Board** |
| ---------------- | ----------------------- | ---------------- | -------------------- | ---------------------- |
| Gemini 335Lg     | Jetson AGX Orin Dev Kit | NVIDIA           | JetPack 6.0/6.2      | FG96-8CH-V2(Max9296)   |

**1.2 Software Resources**

* Precompiled driver file
* OrbbecViewer software(supports version OrbbecViewer\_v2.0.7-rc and above)

#### **2. Unboxing and Installation**

**2.1 Cut or tear the transparent sealing tape on both sides of the box.**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/w9grgxuX3uwVfAVqQnjb/assets/a4619407397ff9a05e67.gif)

Fig. 2-1

**2.2 Remove the Gemini 335Lg camera, FAKRA-Z cable, tripod, tripod head, and Quick Start Guide**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UITrNlZWLDfNjNW30JhF/assets/a4c86e6d5fb71f94a4d3.webp)

Fig. 2-2

**2.3 Remove the white protective film from the camera glass cover**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/PEYqPHOcpRgQYuG4RmUe/assets/8dc8ac50c875eb8d464b.gif)

Fig. 2-3

**2.4 Assemble the tripod and tripod head, then mount the Gemini 335Lg camera**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/DpAc1eJVeMPcCdZNlpKj/assets/2f6723ea749a8b72a460.webp)

Fig. 2-4

**2.5 Open the top sync port cover of the Gemini 335Lg camera, switch the USB/MIPI toggle on the right to M mode, then close the cover**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JmrE7WapmA0UcU9aKAgN/assets/4890e3421d4d400a8905.gif)

Fig. 2-5

#### **3. Connecting Devices and Powering On**

**3.1 Open the right FAKRA port cover on the camera, and connect the camera to the GMSL camera deserializer board using the FAKRA-Z to FAKRA-Z cable**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3hrGRFUEsVrGj6VAbsXI/assets/c0c70909dce32a7056a7.gif)

Fig. 3-1

**3.2 Install the GMSL camera deserializer board and Jetson AGX Orin DevKit together**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/v2g2mtdHsTh90QU4wKkb/assets/c9393a3066cd48cd49d5.gif)

Fig. 3-2

**3.3 Connect the appropriate power supply**

Connecting adapter power supply for Jetson AGX Orin DevKit and GMSL camera deserializer board

Note: Example GMSL board uses 12V 3A power

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/4JLmpao4o8ovGfBz42j8/assets/40ebe6f2d4cd8c4305fd.webp)

Fig. 3-3

**3.4 Connect a monitor, keyboard, and mouse to the Jetson AGX Orin DevKit, then power on both the Jetson AGX Orin DevKit and the GMSL camera deserializer board**

#### **4. Loading the Precompiled Driver File**

**4.1 Check JetPack Version**

Run the following in the terminal:

dpkg -l | grep nvidia-l4t-core

From the output, check the corresponding JetPack version using [NVIDIA’s JetPack-L4T mapping table](https://developer.nvidia.com/embedded/jetpack-archive)

(Example: Output nvidia-l4t-core version 36.4.3 corresponds to JetPack 6.2)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/BlGbL3c3YnvjkSlufPWY/assets/3f41c247fe136fb71c97.gif)

Fig. 4-1

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8POqxLd1Ql5SyabMCVf1/assets/486583363dd09f74a113.gif)

Fig. 4-2

**4.2 Obtain the Precompiled Driver**

Download gmsl-driver-jetson-vx.x.x(JPx.x).zip from the GitHub repository and place it in the \~/Downloads directory

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/efe84yVFw9t7YEA7kiu0/assets/8192160b0887ed74db14.gif)

Fig. 4-3

**4.3 Extract and Install**

For GMSL camera deserializer board FG96\_8CH\_GMSL(EVK), use the copy\_to\_target\_agx\_orin\_fg96.sh script

Run the following in the terminal:

```
cd ~/Downloads/
unzip MIPI_Camera_Platform_Driver.zip
cd gmsl-driver-jetson-v1.2.03(JP6.2)/
chmod +x copy_to_target_agx_orin_fg96.sh
sh copy_to_target_agx_orin_fg96.sh
reboot
```

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/mSLlP3KiwyYzTXBFo8r7/assets/343a4379d4907b94680e.gif)

Fig. 4-4

#### **5. Getting Started**

**5.1 Check Driver Version**

Ensure the driver version matches the precompiled driver file version

Run the following in the terminal:

```
cat /sys/module/g300/version
```

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/sctkD9dAKzmOcx8L68yL/assets/93b3931f74ac55c80bd5.gif)

Fig. 5-1

**5.2 List Video Nodes**

Run the following in the terminal:

```
ls /dev/video*
```

Note: One Gemini 335Lg camera will generate 8 video nodes:

* video0 – Depth stream
* video1 – Depth metadata
* video2 – Color stream
* video3 – Color metadata
* video4 – Left IR stream
* video5 – Left IR metadata
* video6 – Right IR stream
* video7 – Right IR metadata

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/PYqkh9wEFnCwiFByMpqT/assets/41c399c7e802c9922870.gif)

Fig. 5-2

**5.3 Obtain OrbbecViewer Software**

Download the latest OrbbecViewer from OrbbecSDK\_v2 Releases (e.g., OrbbecViewer\_v2.4.8\_xxx.zip) and place it in \~/Downloads.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zleoovG6N8RnjQNTRbvF/assets/c98bed2023c60829598f.gif)Fig. 5-3

**5.4 Extract and Run**

Run the following in the terminal:

```
cd ~/Downloads/
unzip OrbbecViewer_v2.4.8_202507031357_a1355db_linux_aarch64.zip
cd OrbbecViewer_v2.4.8_202507031357_a1355db_linux_aarch64/
sudo ./OrbbecViewer
```

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3vCTHTW4GD0xrYBKRMSc/assets/730abeddd693d34a455b.gif)

Fig. 5-4

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/YjuS68Pa0BzOOwHqrBJV/assets/f3f8d15309746cabcba5.gif)

Fig. 5-5

**5.5 Preview Images**

In the device management area, enable the following streams to preview corresponding images:

* Color stream
* Depth stream
* Left IR stream
* Right IR stream
* IMU stream

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/GudJIZdfFVAwM54TOVJX/assets/af4bfebbd353aeb3ea69.gif)

Fig. 5-6

### Gemini 330 Series Quickstart Guide (Ethernet)

#### **1. What's in The Box for Gemini 335Le?**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UEJrs1GAUVukATFSXpBw/assets/31c550a5efc6bef49377.webp) ![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JrsJ2PVUPEKX1oXlU2Ug/assets/973148de52e4ca501e03.webp)

#### **2. Connect the Orbbec Camera**

**A. Connect the camera using PoE (Power over Ethernet) for power supply.**

1. Secure the camera onto the tripod, as illustrated in Step 1 below.
2. If a PoE switch is available, the camera can be powered via the same Ethernet (M12) data cable for data transfer.
3. Remove the camera’s M12 interface protective cover and connect the Data cable to the M12 interface on the camera.Use an appropriate mounting tool to achieve the specified torque: [M12 torque wrench](https://us.rs-online.com/catalogsearch/result/?q=M12+torque+wrench+set+AF+13)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/cplb8HbyZ4WEloP3Kzx0/assets/6bc7cc456fc18e07c331.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/G5Cimage.png)
4. Plug the RJ45 end of the data cable into the PoE Switch.
5. Connect the host to the PoE switch using a standard RJ45 Ethernet cable (the port used for\
   the PC connection does not need to be PoE capable).

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rgyEpPepxesC8XdW2RsG/assets/ff87233c4c0ac5dac801.webp)

| **Configuration**                                  | **Hardware Requirement** - **In the product retail package**                                                                                           | **Hardware Requirement** - **To be provided by the user**                                                                                                                                                                       |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| \*\*PoE-powered,\*\***Host with Ethernet Port**    | <p>- Gemini 335Le camera<br>- Gemini 335Le data cable (2m)</p>                                                                                         | <p>- PoE switch or PoE injector (IEEE 802.3af/at compliant), reference product:<br><a href="https://www.digikey.com/en/products/detail/microchip-technology/PD-3501G-AC-US/3992860">PD-3501G/AC-US Microchip Technology</a></p> |
| \*\*PoE-powered,\*\***Host without Ethernet Port** | In addition to the ‘PoE-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user. |                                                                                                                                                                                                                                 |

**B. Connect the camera using a DC power supply.**

1. Secure the camera onto the tripod, as illustrated in Step 1 below.
2. Remove the camera’s M12 interface protective cover and connect the Data cable to the M12 interface on the camera.
3. Remove the camera’s M8 interface protective cover and connect the Power cable to the M8 interface on the camera. Use an appropriate mounting tool to achieve the specified torque: [M8 torque wrench](https://us.rs-online.com/catalogsearch/result/?q=M8+torque+wrench)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kMfJXsGb93ZGsNK4OMMQ/assets/52200f90c9a6d64ffbc7.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/M21image.png)
4. Use the red-labeled "POWER IN 9- 24V" pin and the black-labeled "POWER GND" pin to connect a 9- 24V DC power source.
5. Plug the RJ45 end of the data cable into the host or the network gateway to which the host is connected.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AdVTqPMmYTQxKW5cEFQp/assets/fea3338e4751a60ace34.webp)

| **Configuration**                                 | **Hardware Requirement** - **In the product retail package**                                                                                          | **Hardware Requirement** - **To be provided by the user**                                                                                                                                                                                      |
| ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| \*\*DC-powered,\*\***Host with Ethernet Port**    | <p>- Gemini 335Le camera<br>- Gemini 335Le data cable (2m)<br>- Gemini 335Le power cable (2m)</p>                                                     | <p>- DC power supply (output: 9-24V, current: ≥1A)<br>- If a power extension cord is required, make sure the current and voltage received by the camera’s original power cord harness meet the power supply requirements in its datasheet.</p> |
| \*\*DC-powered,\*\***Host without Ethernet Port** | In addition to the ‘DC-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user. |                                                                                                                                                                                                                                                |

#### **3. Get Orbbec Viewer**

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/MSeOcIEQAUa8sqSC8rfT/assets/dbbff0fcc59b5613e935.webp)

#### **4. Environment Preparation Instructions**

For detailed network environment configuration instructions, please refer to https://www.orbbec.com/docs/gemini-335le-quick-start/

#### **5. Launch Orbbec Viewer**

For detailed instructions, please refer to the Orbbec Viewer tutorial video below .

[https://www.youtube.com/@Orbbec3d](https://www.youtube.com/@Orbbec3d)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7FAnJd5zLjNKSz7B0rW9/assets/8b60cff1a21de9dca5fa.webp)

#### **6. Network Environment Configuration on the Host**

**A. Linux Platform**

**1. Environment Preparation**

1.1 Linux x86\_64 /Arm64 Ubuntu 20.04+;

1.2 Connect directly using either the Ethernet port on the host/switch or through a USB-to-Ethernet adapter.

**2. Environment Configuration**

The default IP address for the Gemini 335Le device is 192.168.1.10. The device can be directly connected to the host or via a network switch. Please adjust the host’s local network interface to be on the same network segment as the Gemini 335Le device for proper recognition. Once the sub-net is adjusted, you can access the Gemini 335Le network device using the Orbbec Viewer tool or SDK.

Modify the local network segment to match the same sub-net as the Gemini 335Le device.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/WIEP5ni5oh46AE1wMvsv/assets/d3387b0a010cfd1e7be4.webp)

**3. Recommend Configuration**

(1) If, after configuring the network environment as described in section "2.2", the Orbbec Viewer tool fails to recognize the Gemini 335Le network device, you should check whether the Wi-Fi connection is enabled. If Wi-Fi is enabled, it needs to be turned off first. Then, re-enable the local network connection or power cycle the network device, and it should be recognized.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/vDCnCG1NUGHgpZ83qe5J/assets/d8d28909344c760fefdd.webp)

(2) Due to differences in system networks and power management across platforms, packet loss may occur to varying degrees during the process of stream capture on the host machine, which can result in the frame rate not meeting expectations. Therefore, before using the Gemini 335Le device on different platforms, it is essential to configure and verify the platform and system settings to avoid issues like frame loss.

**Computer Power Configuration:**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/e0jMYOPwrpgru3OwIRWZ/assets/289af370062809195b3c.webp)

**Computer Network Card Configuration:**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/hqwBnd2UFb4WxRMMOVcJ/assets/bd4184bab895a45a6390.webp)

**Firewall Configuration:**

The firewall on Ubuntu is disabled by default. Ubuntu uses Uncomplicated Firewall (UFW) as the default firewall management tool, and UFW is disabled by default. If it is enabled, the user needs to manually configure it to be turned off. Before using Orbbec Viewer, make sure that the firewall is disabled.

**4. Start Orbbec Viewer for Experiencing**

Once the environment and configurations are properly set up as described in the previous sections, you can start experiencing the Gemini 335Le by launching the provided Orbbec Viewer tool for Linux/Arm platforms, as shown in the image below:

Open the Orbbec Viewer tool, select the Gemini 335Le network device you want to open, and click Open:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8p7rclyBR6vEBTPsTRNM/assets/16a6bee95cfe075f0463.webp)

Once the device is successfully loaded, the detailed functionality window will appear, allowing you to start the experience:![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/VjyItA9rqg7hUZqM9qel/assets/bf1e9059a76a04141615.webp)

**B. Windows Platform**

**1. Environment Preparation**

1.1 Windows 10 or above platforms, x64 operating system, 8/16GB or above memory;

1.2 Connect directly using either the Ethernet port on the host/switch or through a USB-to-Ethernet adapter.

**2. Network Configuration**

The default IP address for the G335Le device is 192.168.1.10. The device can be directly connected to the host or via a network switch. Please adjust the host’s local network interface to be on the same network segment as the G335Le device for proper recognition. Once the host is in the same network segment, the G335Le device can be accessed using either the Orbbec Viewer tool or the SDK.

Modify the IP address to be in the same network segment:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ws3y1QG10pCEBwZtqrCJ/assets/bdb0cffbb34906ba78dd.webp)

**3. Recommend Configuration**

Due to differences in system networks and power management across platforms, packet loss may occur to varying degrees during the process of stream capture on the host machine, which can result in the frame rate not meeting expectations. Therefore, before using the G335Le device on different platforms, it is essential to configure and verify the platform and system settings to avoid issues like frame loss.

1. Computer power configuration:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/MQUtUcr2Tn2ZmNRT8lOW/assets/1060fe22c4f6e1123d64.webp)

(2) Computer network card configuration:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/FZa27DjiXfwx6eXWYhJ3/assets/17690f41d28f80f3e320.webp)

(3) Computer firewall configuration:

To allow Orbbec Viewer to communicate through Windows Defender Firewall, follow the path below: Control Panel\System and Security\Windows Defender Firewall

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Wd6N2ee17BqdGjYdui3Y/assets/3df48dc51e713e9441d3.webp) ![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/4IbnYoeLf8ExsoZ7BOgk/assets/5d7ffca0dc826e8827e1.webp)

**4. Start Orbbec Viewer for Experiencing**

Once the environment and configurations are properly set up as described in the previous sections, you can start experiencing the G335Le by launching the provided Orbbec Viewer tool on Windows platforms, as shown in the image below:

Open the Orbbec Viewer tool, select the G335Le network device you want to open, and click Open:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IWGVvnsxvw5ezEcZkB1v/assets/258b344e6651e1bcf3ed.webp)

Once the device is successfully loaded, the detailed functionality window will appear, allowing you to start the experience:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/6CM8A6geMm37IFmvoo1b/assets/42f20186157dde694fa8.webp)

### Gemini 335Lg Recommended FAKRA Connector & Cable Specifications

This documentation illustrates the recommended FAKRA connector and cable specifications for Gemini 335Lg.

#### **1. FAKRA Connector Introduction**

FAKRA (Fachkreis Automobil, a German standard) connectors are SMB based automotive-grade connectors that can operate up to 6 GHz. These connectors are embedded within a plastic housing with a locking feature that has an audible clicking noise which lets you know a connection has been made. They are available in 14 different mechanical layouts, which are color coded for easy identification and mis-matching prevention.

Orbbec Gemini 335Lg is equipped with FAKRA-Z connector.

![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/FTAHN985y35dE0B4cIhO/assets/54ad23af05f8da613463.webp)

Figure 1-1 Different FAKRA Connectors

#### **2. Recommended Cable**

The Gemini 335Lg camera utilizes ADI’s GMSL2 technology, a cost-effective, simple, and scalable SerDes solution. Fakra cables, which connect the Serializer and Deserializer, have a significant impact on the performance of the GMSL2 channel. Different cables have various characteristics and are suited for different applications.

For example, lightweight and flexible cables with a small bending radius usually have thinner wire cores, which require less copper and are relatively low-cost. However, their insertion loss and return loss characteristics are not the best, making them suitable for short-distance applications where the equipment is not fixed and may require frequent bending. On the other hand, cables with thicker wire cores have better insertion and return loss characteristics, making them ideal for long-distance transmission and fixed installations where the equipment doesn’t need to be moved. However, the thicker wire cores also come with higher costs. Regardless of the cable type chosen, it must meet ADI’s GMSL2 channel specifications.

The serializer chip used in Gemini 335Lg camera is the MAX9295D, which supports both coaxial and twisted-pair transmission. Since the module also utilizes POC (Power over Coax) technology, the external Fakra connection cable must be coaxial. Below is a table listing the key parameters for selecting Fakra cables, based on ADI’s GMSL2 technical documentation.

Table 2-1 Cable specifications

| **Category**                                  | **Recommend Spec.**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | **Notes**                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cable type                                    | Coaxial cable                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | ![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3JTi6v5XJ9nDka8xQrE5/assets/2fefae1c474cc315757d.webp)                                                                                                                                                                                                                                  |
| Transmission frequency range                  | 0 \~ 6GHz                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Characteristic impedance                      | 50Ω ± 2Ω                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Reconmended                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Rated current                                 | ≥ 1A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Typical POC voltage: 12V; Ripple: ≤ ±10%                                                                                                                                                                                                                                                                                                                                                                                                              |
| DC resistance                                 | ＜ 0.1Ω/m                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Insulation withstanding voltage               | ≥ 500V AC                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Insulation resistance                         | ≥ 100MΩ                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Contact resistance                            | ≤ 5mΩ (Initial)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Cable length                                  | <p>The maximum length of commonly used cables<br>are listed as follows:<br>RG174: ≤5m<br>Dacar 302/RG58: ≤15m</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | According to [ADI’s MAX9295D datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/max9295d.pdf), "Cables with an attenuation of 1.1dB/m can support up to a maximum length of 15m (3.2mmφ, 6Gbps, 105℃)." Detailed information is in page 1.                                                                                                                                                                                |
| Bend radius                                   | <p>RG174: Static 3x cable OD; Dynamic 10x cable OD<br>Dacar 302:<br>Static 5x cable OD; Dynamic 15x cable OD</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | OD: Out Diameter                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Insertion loss (IL)                           | −17dB MAX @ 3GHz (6Gbps / 187.5Mbps)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Information is according to "[GMSL2 Channel Specification User GuideRev 1](https://www.analog.com/media/en/technical-documentation/user-guides/gmsl2-channel-specification-user-guide.pdf)". Detailed information is in page 16.                                                                                                                                                                                                                      |
| Return loss (RL)                              | ![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/fM54CzGNvwIu9ZxHj7M1/assets/331b875783ad23aa9e89.webp)                                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Tensile strength                              | ≥ 110N                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Ingress protection                            | IP67 (recommended)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Ambient temperature                           | -40 \~ 105℃                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Recommended cable and connector manufacturers | Cable: Amphenol RF, Belden wire & cable, TE Connectivity, HUBER + SUHNER, Lenoi, etc. Connector: Rosenberger, Molex, TE Connectivity, Amphenol RF, etc.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Recommended cables                            | <p>Allied Vision, Inc. <a href="https://www.wdlsystems.com/allied-vision-18424">https://www.wdlsystems.com/allied-vision-18424</a><br><a href="https://www.digikey.com.au/en/products/detail/allied-vision-inc/CABLE-FPD-LINK-III-GMSL2-5M-COAX/22195452">https://www.digikey.com.au/en/products/detail/allied-vision-inc/CABLE-FPD-LINK-III-GMSL2-5M-COAX/22195452</a><br>Amphenol RF: <a href="https://www.mouser.com/ProductDetail/Amphenol-RF/095FJZFJZSHM500?qs=zW32dvEIR3sjRLgtRmvHeA%3D%3D">https://www.mouser.com/ProductDetail/Amphenol-RF/095FJZFJZSHM500?qs=zW32dvEIR3sjRLgtRmvHeA%3D%3D</a></p> | <p><a href="https://www.mouser.com/datasheet/2/18/2/Amphenol_RF_FAKRA_Cable_Assemblies_Cutsheet-3440413.pdf">https://www.mouser.com/datasheet/2/18/2/</a> <a href="https://www.mouser.com/datasheet/2/18/2/Amphenol_RF_FAKRA_Cable_Assemblies_Cutsheet-3440413.pdf">Amphenol_RF_FAKRA_Cable_Assemblies_</a><br><a href="https://www.mouser.com/datasheet/2/18/2/Amphenol_RF_FAKRA_Cable_Assemblies_Cutsheet-3440413.pdf">Cutsheet-3440413.pdf</a></p> |

#### **3. Orbbec Default Cable Drawings**

**i. Orbbec Box-packed Gemini 335Lg Default Cable Drawing**

![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/DBIhjzh6sQvtj7bIcgJK/assets/9db81cc26b14b1f2fdef.webp)

**ii. Orbbec Gemini 335Lg FAKRA Connector Drawing**

![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/r50x1LH8pUHVw90kKyAC/assets/a4100ab38a4e79b2499c.webp)

### Gemini 335Lg Hardware Synchronization

The Gemini 335Lg is designed to be compatible with complex multi-device sync scenarios. There are two methods that users can choose to HW sync multiple Gemini 335Lg and other devices. One is through the GMSL2 / FAKRA link without using sync cable; the other one is through the 8-pin AUX connector with sync cable, which is usually used in USB connections. But Gemini 335Lg can also sync via 8-pin port, as the GPIO map and the sync trigger signal is connected to the same PCBA component inside Gemini 335Lg.

Figure 1 Sync schematic

![Official Orbbec figure from Gemini 335Lg Hardware Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/KWeNMSo2gTwsgnEn0tr3/assets/86d50fbcdd9640ccd95d.webp)

Gemini 335Lg supports HW sync via GMSL2 or 8-pin cable, but the signal requirement is the same. Sync trigger signal is active in rising edge. The default pulse level is 3.3V and pulse width is required to be ≥ 1ms. Detailed signal requirements can be found in [Set up cameras for external synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization).

Figure 2 Trigger signal reference waveform

![Official Orbbec figure from Gemini 335Lg Hardware Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nyfZSGZEELH1U4OE6oRK/assets/533507f45142764d8c6b.webp)

**\*\*Method 1:\*\*Multi-device sync via GMSL2 / FAKRA**

Gemini 335Lg is compatible with the NVIDIA ecosystem, such as AGX Orin developer kit & AGX Xavier developer kit. To achieve accurate synchronization, the host should be able to output a stable and high-accuracy trigger signal. After the trigger signal is output to the supported deserializer MAX9296A or another compatible one, the deserializer and serializer can transmit the signal to the MCU by GPIO map via coax cable. The GPIO used is usually MFP10 or MFP7. Taking CTI’s deserializer board JCB002 as an example, the board can generate PWM signal, the signal is transmitted to the camera side.

![Official Orbbec figure from Gemini 335Lg Hardware Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/h22vGjFFvDpY7jkqIi3C/assets/b4988f81cdd4d3522607.webp)

Users can check the synchronization performance in the Orbbec viewer. If JCB002 is the target deserializer board, users should set the camera #1 and camera #2 as "Secondary-synced" in Orbbec viewer, then use the provided script to generate PWM signal from JCB002. In this case, both cameras are used as slave cameras, with the host as the master, to achieve precise multi-device synchronization. When configured properly and without external interference, the synchronization accuracy can reach 1ms.

Under the current technological solutions, Gemini 335Lg only supports multi-machine synchronization as a slave and does not support being a master. Only supports multi-device synchronization when the master is the host.

**\*\*Method2:\*\*Multi-device sync via 8-pin port**

When using 8-pin port for multi-device synchronization, in order to ensure the quality of the synchronization signal, it is necessary to use it together with a multi-device sync hub. Pin 3 of the sync interface is the trigger signal output pin, Pin 6 is the trigger signal input pin, and Pin 8 is the ground pin. Star synchronization & string synchronization are both supported. For detailed connection methods and precautions, please refer to the document " [Set up cameras for external synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)."

### Build Your First Camera Application

#### **Introduction**

Getting started with the Orbbec SDK? This quickstart will get you up and running with the device!

The following functions are covered:

* queryDeviceList()
* deviceCount()
* getDevice()
* getDeviceInfo()
* firmwareVersion()
* serialNumber()
* connectionType()
* getSensorList()
* getSensor()

#### **1. Prerequisites**

* Set up the Orbbec device
* Download and install the Orbbec SDK through [https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

#### **2. Headers**

Include the primary header file for the Orbbec SDK to access its features:

```cpp
#include <iostream>
#include "utils.hpp"
#include "libobsensor/ObSensor.hpp"
#include "libobsensor/hpp/Error.hpp"
```

#### **3. Find an Orbbec Device**

First, we need to check how many Orbbec devices are connected to your computer. Use the `queryDeviceList()` function to retrieve the connected devices.

```
// Create a Context.
ob::Context ctx;

// Query the list of connected devices
auto devList = ctx.queryDeviceList();
if (devList->deviceCount() == 0) {
    std::cerr << "Device not found!" << std::endl;
    return -1;
}
```

If a device is detected, you can proceed to access its information and sensors.

#### **4. Access Device Information**

Once you have a device list, open the first device and retrieve some basic information such as the device name and firmware version.

```
auto dev = devList->getDevice(0);
auto devInfo = dev->getDeviceInfo();
std::cout << "Device name: " << devInfo->name() << std::endl;
std::cout << "Firmware version: " << devInfo->firmwareVersion() << std::endl;

// By getting the serial number of the device
auto sn = devInfo->serialNumber();
std::cout << "Serial number: " << sn << std::endl;

// By getting the connection type of the device
auto connectType = devInfo->connectionType();
std::cout << "ConnectionType: " << connectType << std::endl;
```

#### **5. List Sensors**

Next, explore the sensors available on the device by fetching the sensor list and printing each sensor type.

```
   // Get the list of supported sensors
    std::cout << "Sensor types: " << std::endl;
    auto sensorList = dev->getSensorList();
    for(uint32_t i = 0; i < sensorList->count(); i++) {
        auto sensor = sensorList->getSensor(i);
        switch(sensor->type()) {
        case OB_SENSOR_COLOR:
            std::cout << "\tColor sensor" << std::endl;
            break;
        case OB_SENSOR_DEPTH:
            std::cout << "\tDepth sensor" << std::endl;
            break;
        case OB_SENSOR_IR:
            std::cout << "\tIR sensor" << std::endl;
            break;
        case OB_SENSOR_IR_LEFT:
            std::cout << "\tIR Left sensor" << std::endl;
            break;
        case OB_SENSOR_IR_RIGHT:
            std::cout << "\tIR Right sensor" << std::endl;
            break;
        case OB_SENSOR_GYRO:
            std::cout << "\tGyro sensor" << std::endl;
            break;
        case OB_SENSOR_ACCEL:
            std::cout << "\tAccel sensor" << std::endl;
            break;
        default:
            break;
        }
    }
```

#### **6. Error Handling**

It’s important to include error handling in your applications. The Orbbec SDK provides detailed exceptions that can be caught to understand what went wrong during execution.

```cpp
catch(ob::Error &e) {
    std::cerr << "Error: " << e.getMessage() << std::endl;
    return -2;
}
```

#### **7. Full Source**

```
#include <iostream>
#include "utils.hpp"
#include "libobsensor/ObSensor.hpp"
#include "libobsensor/hpp/Error.hpp"

#define ESC 27

int main(int argc, char **argv) try {
    // Print the sdk version number, the sdk version number is divided into major version number, minor version number and revision number
    std::cout << "SDK version: " << ob::Version::getMajor() << "." << ob::Version::getMinor() << "." << ob::Version::getPatch() << std::endl;
    // Print sdk stage version
    std::cout << "SDK stage version: " << ob::Version::getStageVersion() << std::endl;

    // Create a Context.
    ob::Context ctx;

    // Query the list of connected devices
    auto devList = ctx.queryDeviceList();

    // Get the number of connected devices
    if(devList->deviceCount() == 0) {
        std::cerr << "Device not found!" << std::endl;
        return -1;
    }

    // Create a device, 0 means the index of the first device
    auto dev = devList->getDevice(0);

    // Get device information
    auto devInfo = dev->getDeviceInfo();

    // Get the name of the device
    std::cout << "Device name: " << devInfo->name() << std::endl;

    // Get the pid, vid, uid of the device
    std::cout << "Device pid: " << devInfo->pid() << " vid: " << devInfo->vid() << " uid: " << devInfo->uid() << std::endl;

    // By getting the firmware version number of the device
    auto fwVer = devInfo->firmwareVersion();
    std::cout << "Firmware version: " << fwVer << std::endl;

    // By getting the serial number of the device
    auto sn = devInfo->serialNumber();
    std::cout << "Serial number: " << sn << std::endl;

    // By getting the connection type of the device
    auto connectType = devInfo->connectionType();
    std::cout << "ConnectionType: " << connectType << std::endl;

    // Get the list of supported sensors
    std::cout << "Sensor types: " << std::endl;
    auto sensorList = dev->getSensorList();
    for(uint32_t i = 0; i < sensorList->count(); i++) {
        auto sensor = sensorList->getSensor(i);
        switch(sensor->type()) {
        case OB_SENSOR_COLOR:
            std::cout << "\tColor sensor" << std::endl;
            break;
        case OB_SENSOR_DEPTH:
            std::cout << "\tDepth sensor" << std::endl;
            break;
        case OB_SENSOR_IR:
            std::cout << "\tIR sensor" << std::endl;
            break;
        case OB_SENSOR_IR_LEFT:
            std::cout << "\tIR Left sensor" << std::endl;
            break;
        case OB_SENSOR_IR_RIGHT:
            std::cout << "\tIR Right sensor" << std::endl;
            break;
        case OB_SENSOR_GYRO:
            std::cout << "\tGyro sensor" << std::endl;
            break;
        case OB_SENSOR_ACCEL:
            std::cout << "\tAccel sensor" << std::endl;
            break;
        default:
            break;
        }
    }

    std::cout << "Press ESC to exit! " << std::endl;

    while(true) {

        // Get the value of the pressed key, if it is the esc key, exit the program
        int key = getch();
        if(key == ESC)
            break;
    }

    return 0;
}
catch(ob::Error &e) {
    std::cerr << "function:" << e.getName() << "\nargs:" << e.getArgs() << "\nmessage:" << e.getMessage() << "\ntype:" << e.getExceptionType() << std::endl;
    exit(EXIT_FAILURE);
}
```

#### **8. Next Steps**

* Learn more about configuring and using individual sensors with the Orbbec SDK.
* Explore advanced features and settings available in the Orbbec SDK documentation.
* Begin integrating Orbbec Device capabilities into your larger projects and applications.

### Build Your First Camera Streaming Application

#### **Introduction**

This quickstart guide will walk you through the process of setting up a multi-sensor streaming application using the Orbbec SDK. This application will utilize various sensors and stream their data simultaneously.

The document refers to the C++ sample MultiStream.

#### **1. Prerequisites**

* Set up the Orbbec device.
* Download and install the Orbbec SDK through [https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

#### **2. Headers**

First, include all the necessary headers for your application:

```
#include "window.hpp"
#include "libobsensor/hpp/Pipeline.hpp"
#include "libobsensor/hpp/Error.hpp"
#include <mutex>
#include <thread>
```

#### **3. Initialize the Pipeline**

The pipeline manages streams and configurations for different sensors:

```
// Create a pipeline with default device
ob::Pipeline pipe;
// Configure which streams to enable or disable for the Pipeline by creating a Config
std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();
```

#### **4. Configure Streams**

Configure which streams to enable based on the sensors available on the device:

```
auto device     = pipe.getDevice();
auto sensorList = device->getSensorList();
for(int i = 0; i < sensorList->count(); i++) {
    auto sensorType = sensorList->type(i);
    if(sensorType == OB_SENSOR_GYRO || sensorType == OB_SENSOR_ACCEL) {
        continue;
    }
    auto profiles = pipe.getStreamProfileList(sensorType);
    auto profile  = profiles->getProfile(OB_PROFILE_DEFAULT);
    config->enableStream(profile);
}
```

#### **5. Start the Main Pipeline**

Start the main pipeline with the configured streams:

```
// Start the pipeline with config
std::mutex                                        frameMutex;
std::map<OBFrameType, std::shared_ptr<ob::Frame>> frameMap;
pipe.start(config, [&](std::shared_ptr<ob::FrameSet> frameset) {
    auto count = frameset->frameCount();
    for(int i = 0; i < count; i++) {
        auto                         frame = frameset->getFrame(i);
        std::unique_lock<std::mutex> lk(frameMutex);
        frameMap[frame->type()] = frame;
    }
});
```

#### **6. Handle IMU Data Separately**

Due to the high frame rate of IMU sensors, it is beneficial to handle their data in a separate pipeline:

```
auto                                              dev         = pipe.getDevice();
auto                                              imuPipeline = std::make_shared<ob::Pipeline>(dev);
std::mutex                                        imuFrameMutex;
std::map<OBFrameType, std::shared_ptr<ob::Frame>> imuFrameMap;
try {
    auto                        accelProfiles = imuPipeline->getStreamProfileList(OB_SENSOR_ACCEL);
    auto                        gyroProfiles  = imuPipeline->getStreamProfileList(OB_SENSOR_GYRO);
    auto                        accelProfile  = accelProfiles->getProfile(OB_PROFILE_DEFAULT);
    auto                        gyroProfile   = gyroProfiles->getProfile(OB_PROFILE_DEFAULT);
    std::shared_ptr<ob::Config> imuConfig     = std::make_shared<ob::Config>();
    imuConfig->enableStream(accelProfile);
    imuConfig->enableStream(gyroProfile);
    imuPipeline->start(imuConfig, [&](std::shared_ptr<ob::FrameSet> frameset) {
        auto count = frameset->frameCount();
        for(int i = 0; i < count; i++) {
            auto                         frame = frameset->getFrame(i);
            std::unique_lock<std::mutex> lk(imuFrameMutex);
            imuFrameMap[frame->type()] = frame;
        }
    });
}
catch(...) {
    std::cout << "IMU sensor not found!" << std::endl;
    imuPipeline.reset();
}
```

#### **7. Render Frames**

Create a window for rendering the collected frames:

```
Window app("MultiStream", 1280, 720, RENDER_GRID);
while(app) {
    std::vector<std::shared_ptr<ob::Frame>> framesForRender;
    {
        std::unique_lock<std::mutex> lock(frameMutex);
        for(auto &frame: frameMap) {
            framesForRender.push_back(frame.second);
        }
    }
    {
        std::unique_lock<std::mutex> lock(imuFrameMutex);
        for(auto &frame: imuFrameMap) {
            framesForRender.push_back(frame.second);
        }
    }
    app.addToRender(framesForRender);
}
```

#### **8. Stop the Pipeline**

Properly stop the pipelines when the application is closing to ensure all resources are freed:

```
pipe.stop();
if(imuPipeline) {
    imuPipeline->stop();
}
```

#### **9. Full Source**

This is a brief overview of the complete application, which integrates all components discussed:

```
#include "window.hpp"

#include "libobsensor/hpp/Pipeline.hpp"
#include "libobsensor/hpp/Error.hpp"
#include <mutex>
#include <thread>

int main(int argc, char **argv) try {
    // Create a pipeline with default device
    ob::Pipeline pipe;

    // Configure which streams to enable or disable for the Pipeline by creating a Config
    std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();

    // enumerate and config all sensors
    auto device     = pipe.getDevice();
    auto sensorList = device->getSensorList();
    for(int i = 0; i < sensorList->count(); i++) {
        auto sensorType = sensorList->type(i);
        if(sensorType == OB_SENSOR_GYRO || sensorType == OB_SENSOR_ACCEL) {
            continue;
        }
        auto profiles = pipe.getStreamProfileList(sensorType);
        auto profile  = profiles->getProfile(OB_PROFILE_DEFAULT);
        config->enableStream(profile);
    }

    // Start the pipeline with config
    std::mutex                                        frameMutex;
    std::map<OBFrameType, std::shared_ptr<ob::Frame>> frameMap;
    pipe.start(config, [&](std::shared_ptr<ob::FrameSet> frameset) {
        auto count = frameset->frameCount();
        for(int i = 0; i < count; i++) {
            auto                         frame = frameset->getFrame(i);
            std::unique_lock<std::mutex> lk(frameMutex);
            frameMap[frame->type()] = frame;
        }
    });

    // The IMU frame rate is much faster than the video, so it is advisable to use a separate pipeline to obtain IMU data.
    auto                                              dev         = pipe.getDevice();
    auto                                              imuPipeline = std::make_shared<ob::Pipeline>(dev);
    std::mutex                                        imuFrameMutex;
    std::map<OBFrameType, std::shared_ptr<ob::Frame>> imuFrameMap;
    try {
        auto                        accelProfiles = imuPipeline->getStreamProfileList(OB_SENSOR_ACCEL);
        auto                        gyroProfiles  = imuPipeline->getStreamProfileList(OB_SENSOR_GYRO);
        auto                        accelProfile  = accelProfiles->getProfile(OB_PROFILE_DEFAULT);
        auto                        gyroProfile   = gyroProfiles->getProfile(OB_PROFILE_DEFAULT);
        std::shared_ptr<ob::Config> imuConfig     = std::make_shared<ob::Config>();
        imuConfig->enableStream(accelProfile);
        imuConfig->enableStream(gyroProfile);
        imuPipeline->start(imuConfig, [&](std::shared_ptr<ob::FrameSet> frameset) {
            auto count = frameset->frameCount();
            for(int i = 0; i < count; i++) {
                auto                         frame = frameset->getFrame(i);
                std::unique_lock<std::mutex> lk(imuFrameMutex);
                imuFrameMap[frame->type()] = frame;
            }
        });
    }
    catch(...) {
        std::cout << "IMU sensor not found!" << std::endl;
        imuPipeline.reset();
    }

    // Create a window for rendering and set the resolution of the window
    Window app("MultiStream", 1280, 720, RENDER_GRID);
    while(app) {
        std::vector<std::shared_ptr<ob::Frame>> framesForRender;
        {
            std::unique_lock<std::mutex> lock(frameMutex);
            for(auto &frame: frameMap) {
                framesForRender.push_back(frame.second);
            }
        }
        {
            std::unique_lock<std::mutex> lock(imuFrameMutex);
            for(auto &frame: imuFrameMap) {
                framesForRender.push_back(frame.second);
            }
        }
        app.addToRender(framesForRender);
    }

    // Stop the Pipeline, no frame data will be generated
    pipe.stop();
    if(imuPipeline) {
        imuPipeline->stop();
    }
    return 0;
}
catch(ob::Error &e) {
    std::cerr << "function:" << e.getName() << "\nargs:" << e.getArgs() << "\nmessage:" << e.getMessage() << "\ntype:" << e.getExceptionType() << std::endl;
    exit(EXIT_FAILURE);
}
```

#### **10. Next Steps**

* Learn more about configuring and using individual sensors with the Orbbec SDK.
* Explore advanced features and settings available in the Orbbec SDK documentation.
* Begin integrating Orbbec Device capabilities into your larger projects and applications.

### Explore Camera Functions in Orbbec Viewer (Gemini 330 Series)

[Explore Camera Functions in Orbbec Viewer (Gemini 330 Series).pdf](https://doc.orbbec.com/attachments/7)

### Stereo 3D Camera

#### **1. Introduction**

A stereo 3D camera is a type of camera equipped with two or more lenses, each with its own image sensor or film frame. This configuration allows the camera to capture images from slightly different angles, simulating the human binocular vision. The primary purpose of a stereo 3D camera is to provide depth perception and create 3D images. The Gemini 330 series 3D cameras combine active and passive stereo vision technologies for seamless operation in both indoor and outdoor conditions.

**Working Principle:**

* **Stereoscopic Vision**: By capturing two images from different perspectives, a stereo 3D camera can calculate the distance to objects in the scene. This process involves measuring the disparity between the two images and using it to triangulate the depth.
* **Image Processing**: Advanced algorithms are used to analyze the images captured by the two lenses. These algorithms match corresponding points in both images to compute depth information, generating a 3D representation of the scene.

For the Orbbec Gemini 330 series cameras, the implementation of the working principle is completed on the Orbbec’s latest custom ASIC.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5dyblUcwfNZ9V63En9LP/assets/7aa068b4ed9a2333415c.webp)

Figure 1. Gemini 335 Stereo 3D Camera

#### **2. Baseline**

The baseline is the distance between the two cameras in a stereo setup, namely, the distance between two IR cameras as shown in Figure 1. A longer baseline increases depth accuracy but also increases the size of the setup. Proper baseline selection is crucial for balancing depth resolution and device compactness.

#### **3. Field of View(FOV)**

The FOV of a 3D camera determines the angular extent of the observable world that can be captured. A larger FOV allows the camera to capture more area but may reduce the resolution.

For the depth is calculated from the left and right images, the FOV of the depth camera is determined by the FOV of the left or right cameras, the measured distance and the baseline. The closer the distance, the smaller the FOV; the further the distance, the closer the FOV of the depth camera is to the FOV of the left or right camera.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/9eEuwDPZJ7n70UksMPuW/assets/785e845a11cffee6f2fe.webp)

Figure 2. Depth FOV and IR FOV

Depth Field of View (Depth FOV) at any depth (Z) can be calculated using the following equation:

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/w1P6zzkstDG7x70LaXHA/assets/d2074ab7395e28ea1056.webp)

Definitions:

* cx: X-direction image coordinates of the principle point of the depth image.
* fx: Depth camera focal length.
* width: Depth image width.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/r1mrhiS4vyQKJyccU0QV/assets/649a60c6b2f58148a242.webp)

Figure 3. Gemini 335 Depth FOV for Aspect Ratio = 16:10

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/FJQ3yRc5FWQeLVeLVhoC/assets/3e040f12572e4e47cba7.webp)

Figure 4. Gemini 335 Depth FOV for Aspect Ratio = 16:9

#### **4. Blind Spots**

Blind spots in 3D cameras are areas where the camera cannot capture depth information accurately. These are usually found at the edges of the FOV or the closest distance between the camera and the object. When the object is not visible in either the left or right image, accurate depth information cannot be obtained. The depth camera uses the left camera as the main camera, and the depth blind spots are the green and gray areas shown in the figure below.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/C4xg8VKhY9H5u2Mc3c2Z/assets/c227de91c4bd0aa8fe2b.webp)

Figure 5. Depth blind spots

#### **5. Depth Dark Borders**

Depth black edges, or dark borders, in stereo 3D cameras refer to areas in the depth map where depth information is either missing or incorrect. These edges often appear at the boundaries of objects where there is a significant depth discontinuity.

**Cause of Depth Dark Borders**:

* **Baseline**: Stereo 3D cameras work by capturing two images from slightly different perspectives and then calculating the disparity (difference) between these images to estimate depth. These occur when objects seen in one image are not visible in the another due to FOV and baseline limitations, as shown in the green blind spots above.
* **Occlusions**: These occur when parts of one image are not visible in the other due to obstruction by an object. This leads to missing depth information, often resulting in black edges in the depth map.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oHOnyGpE6T6541SmqGGR/assets/ff6fc2f3aff25332c19b.webp)

Figure 6. Depth Dark Borders

#### **6. Depth Error**

The errors of stereo 3D cameras are primarily influenced by disparity errors, which are related to the reflectivity of the measured object, image signal-to-noise ratio, algorithm errors, and other factors.

Depth is consequently derived from this equation:

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jkYrybEim00tzwmydvTe/assets/bd701412bf48445018ee.webp)

By differentiating the disparity, we can derive the depth error as follows:

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/XJ5EXEGhqp4NC0YW8ugY/assets/3f7712b7542be62a6ba4.webp)

It can be seen that the depth error of binocular vision increases parabolically (proportional to the square of the distance) as the distance increases.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Eq2wTZ6UH8qvbKUdQ0ia/assets/55f3482e1c7429063d8b.webp)

Figure 7. Depth error(mm) as the distance(mm) increases

### Depth from HDR Imaging

#### **1. Introduction**

For image sensors, the primary challenge lies in capturing both dimly lit indoor scenes and brightly illuminated outdoor settings in the same high-quality image, such as photographing a person standing by the window indoors. Typical image sensors generally adjust exposure or gain to ensure quality imaging in low-light or high-illumination conditions. Robots face various challenges in this regard, such as autonomous mobile robots (AMR) that must operate precisely in environments where sunlight and shadow coexist; robotic vacuum cleaners working near windows face issues with (bright and dark areas in the same view)areas overly bright from sunlight and objects too dark from backlighting. In scenarios where dark and bright areas coexist, using long exposure could result in over-exposure of the bright area, while short exposure might fail to capture details in the darker area. The ORBBEC Gemini 330 Series stereo vision 3D cameras also encounter a similar challenge because their 3D images are calculated from a pair of high-quality, left and right images.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/RJJKiAfUxBSUa8KhV3bt/assets/da40a74a09e1f437b7df.webp)

Figure 1. The scene near the windows. Bright and black areas in the same view.

High Dynamic Range (HDR) imaging in computer vision and cinematography is a set of techniques aiming at handling enormously wide exposure range (i.e., images with greater contrast between light and dark) compared to traditional digital imaging technologies, by merging multiple frames. For 3D depth cameras, higher dynamic range means higher depth fill-rate and higher accuracy, significantly enhancing a robot’s obstacle avoidance capabilities. This paper introduces fundamental concepts related to HDR functionality and introduces how HDR is utilized in the ORBBEC Gemini 330 Series cameras.

#### **2. Sensor Settings**

**2.1 Exposure and Gain**

Exposure and gain are two main parameters in photography and imaging technologies that directly affect the quality and clarity of images.

The ORBBEC Gemini 330 series cameras individually control the exposure for visible RGB light and infrared pairs. For Orbbec depth or IR cameras, exposure is measured in microseconds (µs). It ranges from 1 µs to approximately 166 ms. Longer exposure times can enhance image brightness and signal-to-noise ratio (SNR) in low-light environments, thereby improving image clarity, and vice versa. Indoor scenes generally benefit from longer exposure times, while outdoor scenes require much shorter ones.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/WmXktC5WXeEG2MA3hIdI/assets/f3e24f1e2edd1e98b47c.webp)

Figure 2. Effect of modifying camera exposure. The larger the exposure, the brighter the images.

Gain adjustment does not affect the amount of light collected by the sensor but amplifies the existing electrical signal. Increasing gain can enhance image brightness in low-light conditions, but also increase noise and reduce image quality. Furthermore, using shorter exposure times combined with higher gain settings can effectively minimize effects such as motion blur caused by rapid movement.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/DjUt5VCCq2SL2rVCYcHE/assets/d2907a8459de7dc13d79.webp)

Figure 3. Effect of modifying camera gain. The larger the gain, the brighter the images.

**2.2 Over & Under Exposure**

When signals are converted into digital frames, they undergo quantization based on the effective dynamic range of the sensor and the available bit depth. Values falling below the minimum threshold or exceeding the maximum threshold are truncated. This can result in areas of overexposure or underexposure. Overexposed regions are typically displayed as predominantly white, while underexposed areas appear almost black. This issue is prominent in stereo cameras. Figure 6 illustrates the effect of overexposure and underexposure by presenting two bad cases:

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/30RCLQEPUxDsXT58eidG/assets/77f8615e6edb27f29ebd.webp)

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/j6UbBHlyS8cpprfF6B78/assets/48b8e2ee560f56b98d4e.webp)

Figure 4. Two bad cases of underexposure (top) and overexposure (bottom): left – infrared image, right – depth image.

As described in the commonly used Linear-Signal-Model, light signal undergoes quantization and gets converted into digital frames, while underexposure or overexposure may happen during this process. For a _k_-bit imaging sensor, normally, gray values are expected to range from 0 to 2k-1, despite the following unexpected pixels:

* almost black ones, when target surfaces are black, or too far away, etc.
* nearly saturated ones with high-reflective surfaces, etc.

In both cases, rich features on which reliable stereoscopic matching relies are missing, so that the depth result may not be available or may have erroneous values over such areas.

In order to solve the problem of underexposure or overexposure, common methods include: adjusting the camera’s manual exposure, controlling the camera’s automatic exposure configuration, using an HDR camera, or using image enhancement technology to restore the image etc. Image enhancement technology will not be discussed in this paper.

**2.3 Manual Exposure**

Manual exposure is an exposure mode supported by the Gemini 330 series cameras, allowing users to adjust the exposure time and gain to modify image brightness. This method does not automatically adjust based on changes in ambient lighting. It allows users to execute precise exposure control. For instance, to photograph fast-moving objects, one can set a shorter exposure time to prevent motion blur.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/j12ZfkWFoC6iUOff8QpS/assets/de03cc632e5c4bec19b2.webp)

Figure 5. Same scene captured with short exposure (left) vs longer exposure (right)

You can also set up in the Orbbec viewer under the IR Left/IR Right/Depth control panel. The user needs to turn auto-exposure off before manual adjustment.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/CMh8Q190tBW8XaC8uvze/assets/f5b140bbb401359d3e05.webp)

Figure 6. Disabling auto-exposure and adjusting exposure and gain in Orbbec Viewer

Similarly, you can refer to the following code to set exposure and gain.

```
// Create a pipeline with default device
ob::Pipeline pipe;
// Get the device from the pipeline
auto device = pipe.getDevice();
// set ir exposure value to 3000
device->setIntProperty(OB_PROP_IR_EXPOSURE_INT, 3000);
// set ir gain value to 16
device->setIntProperty(OB_PROP_IR_GAIN_INT, 16);
```

**2.4 Automatic Exposure**

The goal of auto-exposure is to achieve an appreciate brightness level, or so-called target brightness level in different lighting conditions and scenes, so that the videos or images captured are neither too dark nor too bright. For example, robots need to work indoors and outdoors, and the camera is usually set to automatic exposure mode.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rboDEt0ReURwpl2CcI35/assets/c01250a9eee579be1165.webp)

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/o1Bv3QOEMB4ZjTqqQqKw/assets/04e5269a6e9a16c6d1a3.webp)

Figure 7. Effect of auto-exposure indoors(top) and outdoors(bottom): left – infrared image, right – depth image.

By default, Gemini 330 series cameras are configured in auto-exposure mode. Under this mode, the camera will automatically adjust exposure and gain values until the average image intensity reaches a certain preset value. Auto exposure can also be turned on/off in the Orbbec viewer.

Auto exposure criteria can be set up as well, in case the preset average intensity value is not proper for the use case. If the IR images are too dark or too bright, the user can manually change the Mean Intensity Set Point, which can be set under the IR Left/IR Right/Depth control panel.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/KRz7U47YaRmSqVLbTNiD/assets/3b0b752e7edc7bd6da84.webp)

Figure 8. Enabling auto-exposure and adjusting the Mean Intensity Set Point in Orbbec Viewer

Similarly, you can refer to the following code to set auto-exposure.

```
// Create a pipeline with default device
ob::Pipeline pipe;
// Get the device from the pipeline
auto device = pipe.getDevice();
// Enable IR sensor auto exposue
device->setBoolProperty(OB_PROP_IR_AUTO_EXPOSURE_BOOL, true);
// set the IR sensor mean intensity set point value to 60
device->setIntProperty(OB_PROP_IR_BRIGHTNESS_INT, 60);
```

However, automatic exposure cannot handle certain extreme scenarios, such as half-bright and half-dark in the view. In this case, you may consider using HDR as described in Section 3.

**2.5 Exposure Limitation**

Naturally, the maximum exposure time of a camera is constrained by its frame rate, as indicated in Table 1. In automatic exposure mode, the maximum exposure time is less than the Max exposure time based on frame rate. In manual exposure mode, there is no such limitation for user input, but if it exceeds the limitation for the current frame rate, the active frame rate will be reduced accordingly. For example, if the camera’s frame rate is set to 30fps and the manual exposure time is set to 30,000us, yet some indoor scenes still appear too dark, the exposure time can be extended to 60,000us. This adjustment will cause the camera’s output frame rate to drop to 15fps.

| **Framerate (fps)** | **Max Exposure Time (us)** |
| ------------------- | -------------------------- |
| 60                  | 16,000                     |
| 30                  | 32,000                     |
| 15                  | 65,000                     |
| 6                   | 166,000                    |

Table 1. Max exposure per frame rate

#### **3. High Dynamic Range**

High Dynamic Range (HDR) imaging allows imaging systems to capture images in extremely dark and bright scenes alike. To overcome the limitations of traditional dynamic range, this technology typically involves capturing multiple images at different exposure levels and combining them into a single HDR image. Given the limitations of the Gimini 330 hardware (MX6800) , it is impossible/difficult to synthesize multi-exposure color and depth images on the ASIC inside the camera. We propose a software solution running on the host CPU to implement this feature. It utilizes data from two consecutive frames and directly synthesizes these two depth images, thereby enhancing the dynamic range of 16-bit depth images.

This feature requires firmware v1.2.01+ and SDK v1.9.0+.

**3.1 Methodology**

As described before, HDR works with given exposure and gain values, which was left to the user to set according to a specific application scenario. So the main task here lies in merging outputs from different exposure and gain settings.

For a given set of depth images with n frames, let d\_i (i=0, \ldots, n-1)be the i-th depth value at any pixel, and the merged depth value could be represented via the following

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/S0Iiyfx74AJJA1651BKk/assets/aa4c8dfd418f831d9042.webp)

where \mathscr{W}is the weighting function. In Orbbec’s HDR implementation, only two consecutive frames are chosen, thus equal to 2. And \ mathscr {W}is a simple non-zero check function. So the former can be rewritten as

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/fPfXT2P7zBN3Yg48Ilj5/assets/00af2116e913c9e6bb16.webp)

To be noted, the aforementioned merging process is implemented in Orbbec-SDK, which can be simply customized.

**3.2 Orbbec Viewer Settings**

To enhance the camera functionality with High Dynamic Range (HDR) capabilities, we have implemented new HDR control features on compatible devices. In the Orbbec Viewer software, users must activate the depth or infrared streams to ensure optimal performance of the HDR function. To accommodate the HDR processing, which involves merging consecutive frames, we have adjusted the device configuration to double the standard frame rate to 60 FPS while maintaining an effective output of 30 FPS due to the HDR synthesis process. Each HDR output is created by merging frames with alternating "high exposure + low exposure" and "low exposure + high exposure" settings. This process introduces a minimal latency of two frames, but the frame rate is still 60FPS.

Users are advised to manually adjust the exposure and gain settings for both high and low exposure frames within the depth control settings to optimize HDR performance. Additionally, for precise monitoring of the camera’s functionality, the HDR-Merge feature can be disabled. This allows for an accurate assessment of the camera’s operational characteristics under varied environmental conditions.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/MmLhJ6HML0eiHLNSANnw/assets/a8eb05a55ebcc2d0c572.webp)

Figure 9. Configuring the hardware for HDR in Orbbec Viewer

The camera will initiate streaming, alternating between the two predetermined exposure settings. By opening the metadata panel and pausing the stream, users can access additional details. It is important to note that per-frame metadata provides critical information and is essential for HDR images.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jw45WcDi35vq8EN5c6Fr/assets/7c47e554d03c5d5a5492.webp)

Figure 10. Examining frame metadata of an HDR stream

The relevant metadata items are:

* **Hdr Sequence Name**– name of the HDR sequence
* **Hdr Sequence Size**– length of the HDR sequence
* **Hdr Sequence Index**– step number inside the HDR sequence of the current frame (zero-based)
* **Exposure**– exposure that was used for the current frame
* **Gain**– gain that was used for the current frame

In order to generate a synthesized depth HDR stream, the HDR Merge post-processing switch needs to be enabled:

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8i0qEYGIsGUe3maU5iTk/assets/ba2a5f035c495e624a85.webp)

Figure 11. Enabling Depth HDR Merge under post-processing

After activating the HDR Merge feature, the standard depth stream is replaced by an artificially generated HDR depth stream. This modification eliminates flickering in the depth stream; however, flickering in the infrared image stream persists. Since the merging of infrared image frames is a common image processing operation, this functionality has not been incorporated into the OrbbecSDK.

In addition to HDR depth fusion, the SDK provides a simple way of splitting the flickering stream into two individual sequence components by identifying its ID. This can be done using the Sequence ID Filter switch.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oNr5NNUvaOVBtplsk06p/assets/66f8cc101fb5e5f7ce63.webp)

Figure 12. Filtering the stream by sequence ID

**3.3 Code Examples**

To activate HDR functionality, set different exposures or gains, and use the built-in HDR Merge post-processing algorithm, refer to the following code example:

```
#include "window.hpp"

#include "libobsensor/hpp/Pipeline.hpp"
#include "libobsensor/hpp/Error.hpp"

int main(int argc, char **argv) try {
// Create a pipeline with default device
ob::Pipeline pipe;

// Get the device from the pipeline
auto device = pipe.getDevice();

// Check if the device supports HDR merge
if(!device->isPropertySupported(OB_STRUCT_DEPTH_HDR_CONFIG, OB_PERMISSION_READ_WRITE)) {
std::cerr << "Current default device does not support HDR merge" << std::endl;
return -1;
}

// Configure which streams to enable or disable for the Pipeline by creating a Config
std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();

// Get all stream profiles of the depth camera, including stream resolution, frame rate, and frame format
auto depthProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH);
auto depthProfile  = depthProfiles->getProfile(OB_PROFILE_DEFAULT);
config->enableStream(depthProfile);

// Create HdrMerge post processor to merge depth frames betweens different hdr sequence ids.
// The HdrMerge also supports processing of infrared frames.
ob::HdrMerge hdrMerge;

// configure and enable Hdr stream
OBHdrConfig obHdrConfig;
obHdrConfig.enable     = true;  // enable HDR merge
obHdrConfig.exposure_1 = 7500;
obHdrConfig.gain_1     = 24;
obHdrConfig.exposure_2 = 100;
obHdrConfig.gain_2     = 16;
device->setStructuredData(OB_STRUCT_DEPTH_HDR_CONFIG, &obHdrConfig, sizeof(OBHdrConfig));

// Start the pipeline with config
pipe.start(config);

// Create a window for rendering and set the resolution of the window
bool   resizeWindows = true;
Window app("HDR-Merge", 1280, 720);
bool   mergeRequired = true;

std::cout << "Press 'M' to toggle HDR merge." << std::endl;
while(app) {
auto key = app.waitKey(10);
if(key == 'M' || key == 'm') {
mergeRequired = !mergeRequired;
if(mergeRequired) {
std::cout << "HDR merge enabled." << std::endl;
}
else {
std::cout << "HDR merge disabled." << std::endl;
}
}

auto frameSet = pipe.waitForFrames(100);
if(frameSet == nullptr) {
continue;
}

auto depthFrame = frameSet->depthFrame();
if(depthFrame == nullptr) {
continue;
}

if(mergeRequired) {
// Using HdrMerge post processor to merge depth frames
auto mergedDepthFrame = hdrMerge.process(depthFrame);
if(mergedDepthFrame == nullptr) {
continue;
}

// add merged depth frame to render queue
app.addToRender(mergedDepthFrame);
}
else {
// add original depth frame to render queue
app.addToRender(depthFrame);
}
}

// Stop the Pipeline, no frame data will be generated
pipe.stop();

// close hdr merge
obHdrConfig.enable = false;
device->setStructuredData(OB_STRUCT_DEPTH_HDR_CONFIG, &obHdrConfig, sizeof(OBHdrConfig));

return 0;
}
catch(ob::Error &e) {
std::cerr << "function:" << e.getName() << "\nargs:" << e.getArgs() << "\nmessage:" << e.getMessage() << "\ntype:" << e.getExceptionType() << std::endl;
exit(EXIT_FAILURE);
}
```

**3.4 Results**

The built-in HDR function of the Gemini 330 series cameras improves the depth fill rate.

In the following depth capturing scenario, which covers a high-reflection panel and a low-reflection bracket, the Gemini 330 series camera is set to automatic exposure. It is very obvious that in the high-reflection surface area, most of the pixels cannot get valid depth data.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7TvDeAd3kerNkSRbsLML/assets/b6100d5eb5406a23e388.webp)

Figure 13. Depth effect in automatic exposure mode: left – depth image, right –infrared image.

On the other hand, when we turn on the HDR and HDR Merge functions, the depth fill rate in the high-reflection panel area is higher, and the depth value is more accurate.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/VYzrDf4QUX0WZVXCZkDy/assets/76ca7f74418d70ecc4ff.webp)

Figure 14. HDR stream in mixed high& low reflection scene: high exposure frame (top), low exposure frame (middle), merged depth (bottom)

One main concern about HDR is its impact on depth accuracy. One example showing the influence is as follows. Pieces of highly reflective panels were stuck to a flat wall about 1043mm away from a Gemini 335 camera, as shown in the upper-left RGB image. The panels are too reflective to form reliable speckles; thus, no valid depth can be estimated in some regions, especially in "High Accuracy" or "Hand" presets, where only reliable estimations remain. The lower left depth image depicts a depth image captured in the "Hand" preset and with Auto Exposure checked.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3zg2acY2P0uFtqwhnUmD/assets/c0cebadad3cc538ab037.webp)

Figure 15. Pieces of a highly reflective panel were stuck tightly to a flat wall to test the accuracy.

As a comparison, a depth frame with HDR is also captured in the same scenario, showing higher depth fill-rate (as shown in the lower right of Figure 13) but no decreased accuracy, as shown in Figure 14. Black and red lines are depth values at the same row, with only different HDR settings. The red line with HDR appears to be more accurate.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/tWlinCgciuVj8IVFdJAU/assets/f10e88b983d3b7d8a0af.webp)

Figure 16. Section profile of depth image captured in the same scenario as in Figure 13.

#### **4. Summary**

Gemini 330 series cameras provide high-quality depth imaging. It's built-in automatic exposure mode can meet user needs in most scenarios, both indoor and outdoor. For autonomous mobile robots equipped with these cameras, the automatic exposure generally provides sufficient adaptability to handle varying lighting conditions effectively. Since the auto-exposure algorithm is implemented in the firmware, it does not consume resources from the host equipment and simplifies user operation.

Manual exposure is typically used in scenarios requiring precise exposure control, such as factory robotic arms pan-picking, where it is only necessary to enhance the imaging quality of the workpieces.

HDR in depth sensor is designed to address some challenges that neither automatic nor manual exposure can solve. It significantly improves the fill rate in tough working environments with complicated illumination or reflection situations, and also improves the depth accuracy in these areas. It reduces the risk of two common and serious errors in computer vision systems: "missed detection" and "false detection". In some use cases, these errors can even be fatal.

As every technology people developed, it of course has its own limitations, such as frame delay and CPU usage due to extra calculation on the host; experience required to determine proper high and low exposure times; motion artifacts for high-speed moving objects.

In scenes with rapid camera movement, adjusting the mean intensity of the auto-exposure can improve image stability. If needed, enabling HDR and HDR merge can enhance detail capture at the cost of a higher frame rate. For applications requiring precise depth data, activate HDR but avoid merging depth frames, using both high and low exposure frames to meet specific algorithmic needs. This setup ensures detailed and accurate depth information under varying lighting conditions.

#### **5. References**

* HDR imaging with OpenCV – [https://docs.opencv.org/3.4/d2/df0/tutorial\_py\_hdr.html](https://docs.opencv.org/3.4/d2/df0/tutorial_py_hdr.html)
* High dynamic range – [https://en.wikipedia.org/wiki/High\_dynamic\_range](https://en.wikipedia.org/wiki/High_dynamic_range)

### Optical Filters for Stereo Vision 3D Cameras

In this document, we discuss the use of optical filters in stereo vision 3D cameras. More specifically, we are going to first investigate the optical characteristics of different filter types and then optimize the 3D camera performance under challenging lighting conditions with properly selected optical filters, where significantly improved imaging quality can be observed in test images.

#### **1. Introduction**

The performance of stereo vision 3D cameras is directly related to the quality of the input stereo image pairs. Therefore, in certain scenarios, it’s beneficial to use additional optical components to enhance the imaging quality of the stereo camera, thereby improving the performance of the depth perception. In this document, we focus primarily on optical filters, which can avoid critical imaging issues if applied appropriately and are generally available at affordable cost.

#### **2. What is an Optical Filter?**

An optical filter is an optical component designed to selectively transmit or block specific wavelengths of light. They are typically made of specific materials or coated with films to achieve desired optical properties, used to control the propagation of light in optical systems. For stereo vision 3D cameras, placing filters of specific wavelength bands on top of the cover glass can help selectively transmit or block light within certain wavelength ranges, thereby significantly enhancing imaging quality.

#### **3. Types of Optical Filters**

**3.1 Neutral Density Filter**

These filters are designed to reduce the intensity of incident light. This filtering action is non-selective, meaning it reduces the intensity of light for all wavelengths equally, thereby decreasing the transmitted light intensity without affecting the spectral distribution of the light. In photography, they are commonly used to prevent saturation in high dynamic range images. While in laser applications, they are typically used for controlling laser power.

**3.2 Broadband Filter**

These filters selectively transmit a certain wavelength band of light while blocking other wavelengths. They are further classified into short-pass, band-pass, and long-pass filters, each allowing specific wavelength ranges to pass through while attenuating others. Different bandpass filters are chosen based on the desired transmittance characteristic over the spectra of interest. The following diagram illustrates the spectral distribution curves of different types of bandpass filters.

a. Band-pass filter: This filter selects a specific wavelength band to pass through while attenuating wavelengths outside the passband. The spectral curve is depicted in Figure 1.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5zVY3jLwf7GC5bw8sNd2/assets/273677815f9b4451e314.webp)

Figure 1: Spectral Curve of Wide-pass Bandpass Filter

b. Short-Pass: This filter allows light shorter than the selected wavelength to pass through while blocking light longer than that wavelength. Common examples include visible light pass filters, as shown in Figure 2.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7rWYI0swhkewsgZhsSmv/assets/02338e2930e60396aad5.webp)

Figure 2: Spectral Curve of Visible Light Pass Filter

c. Long-Pass: This filter allows light of wavelengths longer than the selected value to pass through while blocking light of wavelengths shorter than the selected value. Typical examples are IR Pass filters with visible light cut-off, as shown in Figure 3.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UuFT7OrX8Hi8cowABjGr/assets/2e82da72bd8100b0e8cc.webp)

Figure 3: Spectral Curve of IR Pass Filter

**3.3 Band-Stop Filter**

This filter blocks only a specific wavelength band of light and is essentially the opposite of a bandpass filter. It is commonly used to eliminate light of a particular wavelength and plays an important role in scientific applications such as fluorescence microscopy imaging.

**3.4 Polarizing Filter**

This type of filters is used to adjust the polarization state of incident light. Common types of polarized light include linearly polarized light, circularly polarized light, and elliptically polarized light. It is used in applications such as laser polarization imaging, liquid crystal displays, and sunglasses.

#### **4. Challenges of Stereo Vision 3D Cameras**

**4.1 Sensitivity to Ambient Light**

Stereo vision usually captures image pairs with ambient light in the environment. However, differences in light intensity and incident light angles between the left and right cameras can lead to significant differences in brightness between the left and right images of a stereo pair, resulting in a sharp decline in algorithmic matching effectiveness.

**4.2 Poor Performance in Monotonous and Textureless Scenes**

Stereo vision relies on visual features for image matching. Therefore, scenes lacking visual features, such as the sky or white walls, can pose matching difficulties, leading to significant matching failures or even errors. Adding laser speckle projection can enhance features in low-texture scenes, but in certain situations, ambient light can reduce the contrast of laser speckles or even obscure their grayscale information.

#### **5. Using Filters**

**5.1 Filtering out Ambient Light**

The majority of ambient light in indoor scenes consists of visible light, with its spectrum concentrated in the 400 nm- 600 nm range. For stereo vision 3D cameras, areas with high brightness or highly reflective objects can result in incorrect depth calculations due to excessive ambient light. Adding an IR pass filter effectively suppresses overexposed areas caused by ambient light, ensuring the accuracy of depth calculation. Figures 4 and 5 show a comparison of before and after adding the IR pass filter. By adding a filter, the depth performance of the ground has significantly improved.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/fQT9iqaT2J7d7BWIlBuh/assets/931e8ce5845d9189fa9a.webp)

Figure 4: Infrared and depth images without an IR pass filter

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/wqIa7KiaOU7ByqB4Fe8N/assets/90d9b20b6786f64e6cef.webp)

Figure 5: Infrared and depth images with an IR pass filter

**5.2 Enhancing Speckle Signal-to-Noise Ratio (SNR)**

The signal-to-noise ratio (SNR) of laser speckles in stereo vision 3D cameras has a great impact on imaging quality. Ambient light introduces background noise to laser speckles, resulting in poor SNR or even overshadowing of speckle brightness. Adding an IR pass filter to eliminate visible light effectively improves the speckle SNR, especially in low-texture scenes, thereby enhancing imaging quality. Figures 6 and 7 show a comparison of before and after adding the IR pass filter. By adding a filter, By adding a filter, the depth performance of the light tube and the cart has significantly improved.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/y4yNcRZlkmZ463qfYakm/assets/9191a0d8655001294ba9.webp)

Figure 6: Infrared and depth images without an IR pass filter

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/iyJ7RL2agJVvttzQZlrr/assets/b1a444345be6fad1b4a8.webp)

Figure 7: Infrared and depth images with an IR pass filter

### Depth Quality Metrics

#### **1. Terminology**

The table below lists terms and acronyms that appear in this document.

Table 1: Terms and acronyms

| **Term** | **Description**     |
| -------- | ------------------- |
| ROI      | Region of Interest  |
| FOV      | Field of View       |
| GT       | Ground Truth        |
| RMS      | Root of Mean Square |
| STD      | Standard Deviation  |

#### **2. Quality Metrics**

Assessing depth quality involves quantifying various aspects of the depth data and comparing them against desired performance criteria or ground truth measurements. Some common metrics for quantitative depth quality assessment include:

* **Depth accuracy** assesses the absolute error by calculating the median deviation from depth data.
* **Spatial Precision** assesses spatial noise by calculating the root mean squared error of the depth data.
* **Temporal Precision** assesses the uniformity of depth values over time.
* **Fill Rate** assesses the percentage of valid depth pixels across an image.

Quantitative metrics demand a thorough understanding and diligent assessment of the depth data quality. Establishing a controlled and comprehensive testing environment is important for accurately assessing the capabilities and limitations of depth sensors, as well as for determining their suitability for specific applications or scenarios. For the sake of maintaining consistency in depth quality assessment, it is advisable to utilize a high-reflectivity, flat surface characterized by uniform diffuse reflection attributes, thereby avoiding intricate, uncontrolled real-world scenarios. This refers to a planar reference target, placed at a known distance from the capturing device, serving as an essential benchmark for the evaluation. If such conditions are lacking, a flat wall surface or whiteboard may also serve as an appropriate test target. Each metric may be computed over any desired ROI within the camera’s FOV.

![Official Orbbec figure from Depth Quality Metrics](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/sj7Jtj1bXdJiD3awZe0f/assets/af067c0a07c6f347b676.webp)

Figure 1: Reference plane for depth quality assessment.

**2.1 Depth Accuracy**

Depth Accuracy refers to the degree to which the measured depth values correspond to the true distances between objects and the capturing device. High accuracy implies that the depth measurements closely match the GT, minimizing errors in distance estimation. As previously mentioned, a reference plane placed at a known distance from the sensor is recommended in order to simplify the GT of depth data for evaluation, and the distance between the plane and the sensor can be precisely determined using common measuring tools such as laser distance meter or tape measure.

Table 4: Depth accuracy (Signed)

| **Item**           | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Category**       | Depth accuracy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Purpose/Goal**   | Measure the accuracy of depth images within a specified ROI relative to the GT.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **Target**         | Reference plane\Wall                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **Analyzed Image** | Depth image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **ROI**            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **Description**    | <p>This metric measures the per-pixel depth accuracy relative to the GT in a single frame depth image, excluding errors due to camera placement. GT is obtained by measuring the distance from the depth origin to the reference target. Depth accuracy can be calculated using the following formula: Depth_accuracy_Signed = Median(CP_Length – GT + PP_Dist)<br>where CP_Dist represents the actual length between the depth origin and a fitted plane along the GT measuring direction, and PP_Dist denotes the per-pixel distance of the point cloud to the fitted plane.</p>                    |
| **Pseudo-Code**    | <p>INPUT: Depth_Image, GT REMOVE all zeros in Depth_Image<br>COMPUTE Point_Cloud (X,Y,Z matrix) from Depth_Image<br>COMPUTE Fitted_Plane to Point_Cloud<br>REMOVE outliers: all Z values that below percentile 0.5% and above percentile 99.5%<br>COMPUTE the actual length between the depth origin and the Fitted_Plane along the GT vector as CP_Dist<br>COMPUTE distance of all points to the Fitted_Plane as PP_Dist<br>COMPUTE Depth_Error = CP_Dist – GT + PP_Dist<br>COMPUTE Median_Value = 50% percentile value of Depth_Error<br>OUPUT: Depth_accuracy_Signed = 100 * Median_Value / GT</p> |
| **Output Value**   | Depth\_accuracy\_signed                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **Output Units**   | \[%]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

**2.2 Spatial Precision**

While accuracy concerns the systematic deviation from the true depth, spatial precision relates to the consistency of depth measurements. Spatial precision indicates the noise level of depth data across a planar target. A high spatial precision depth data exhibits low variance in depth values for identical or similar surfaces within the same scene. To assess spatial precision, one can perform measurements of a reference plane at known or controlled locations, calculate the RMS error of the depth values obtained, and compare them against desired precision thresholds or specifications.

RMS error can be expressed in units of distance or disparity, but considering the coupling between depth and noise, it can be normalized by the distance between the camera and the planar target and represented in percentage (%) units.

Table 2 : Spatial Precision

| **Item**       | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Category       | spatial precision                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Purpose/Goal   | Measure the noise level of depth values relative to the best-fit plane.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Target         | Reference plane\Wall                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Analyzed Image | Depth Image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ROI            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                                                                                                                                       |
| Description    | Calculate the RMS of the distance from each valid pixel to the best-fit plane, normalized by the distance from the optical center to the plane, with the RMS Error output expressed as a percentage.                                                                                                                                                                                                                                                                                        |
| Pseudo-Code    | <p>INPUT: Depth_Image REMOVE all zeros in Depth_Image<br>COMPUTE Point_Cloud (X,Y,Z matrix) from Depth_Image<br>COMPUTE Fitted_Plane to Point_Cloud<br>REMOVE outliers: all Z values that below percentile 0.5% and above percentile 99.5%<br>COMPUTE distance between the depth origin and the Fitted_Plane as CP_Dist<br>COMPUTE distance of all points to the Fitted_Plane as PP_Dist<br>COMPUTE RMSE = RootMeanSquare of PP_Dist<br>OUPUT: Spatial_precision = 100 * RMSE / CP_Dist</p> |
| Output Value   | Spatial\_precision                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Output Units   | \[%]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |

**2.3 Temporal Precision**

Temporal Precision measures the variation in depth values over time within an ROI. The quality of a depth image can be assessed based on its temporal consistency; high-quality depth images should exhibit smooth and stable depth over time. This method is defined as the STD of depth values across a specific number of frames (for example, 30). The quantification of temporal noise is carried out on a per-pixel basis, followed by calculating the STD of each pixel over a specified time.

Table 3: Temporal Precision

| **Item**           | **Description**                                                                                                                                                                                                                                                                                                                                                         |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Category**       | Depth temporal noise                                                                                                                                                                                                                                                                                                                                                    |
| **Purpose/Goal**   | Measure the extent of variation in depth values per pixel over time.                                                                                                                                                                                                                                                                                                    |
| **Target**         | wall                                                                                                                                                                                                                                                                                                                                                                    |
| **Analyzed Image** | N sequential depth images                                                                                                                                                                                                                                                                                                                                               |
| **ROI**            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                   |
| **Description**    | Per-pixel temporal noise is defined by measuring the STD of depth values for each pixel across N consecutive frames, resulting in a STD matrix. Temporal Noise is defined as the median of the STD matrix as a percentage of the target distance Z. This metric excludes NaN and zero depth data.                                                                       |
| **Pseudo-Code**    | <p>INPUT: N images of Depth_Image, GT LOOP for each of N Depth_Image to create Depth_Tensor<br>ASSIGN Depth_Tensor = (Depth_Image,N) //dimension is (width,height,N)<br>REMOVE all zeros from Depth_Tensor<br>COMPUTE STD_Matrix = STD of Depth_Tensor(width,height,all)<br>COMPUTE Median_STD = 50% percentile value of STD_Matrix<br>Output: 100 * Median_STD / Z</p> |
| **Output Value**   | The median value of the STD matrix, divided by distance to wall                                                                                                                                                                                                                                                                                                         |
| **Output Units**   | \[%]                                                                                                                                                                                                                                                                                                                                                                    |

**2.4 Fill Rate**

A high-quality depth image should cover the entire field of view uniformly, without missing regions. Fill Rate measures the proportion of non-zero pixels in a depth image, representing the depth coverage. High fill rate indicates that most scene points have been successfully captured.

Table 5: Fill Rate

| **Item**           | **Description**                                                                                                                                                                                                                                          |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Category**       | Fill rate                                                                                                                                                                                                                                                |
| **Purpose/Goal**   | Measure the proportion of valid depth values within a specified ROI.                                                                                                                                                                                     |
| **Target**         | Reference plane\Wall                                                                                                                                                                                                                                     |
| **Analyzed Image** | Depth image                                                                                                                                                                                                                                              |
| **ROI**            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                    |
| **Description**    | Calculate the ratio of pixels with valid depth values to all pixels within a specified ROI.                                                                                                                                                              |
| **Pseudo-Code**    | <p>INPUT: Depth_Image COMPUTE Total_Num = size(Depth_Image)<br>ASSIGN Valid_Image = Depth_Image<br>REMOVE all zeros from Valid_Image<br>COMPUTE Valid_Num = size(Valid_Image)<br>COMPUTE Fill_Rate = 100 * Valid_Num / Total_Num<br>Output Fill_Rate</p> |
| **Output Value**   | The proportion of valid pixels within the specified ROI.                                                                                                                                                                                                 |
| **Output Units**   | \[%]                                                                                                                                                                                                                                                     |

### Metadata

#### **1. Brief Introduction**

Metadata refers to data that provides information about other data. It acts like a descriptive label that helps to identify, manage, and use the actual data more effectively. Metadata can include a variety of details depending on the context:

* **Descriptive Metadata**: This includes information like titles, authors, and keywords which help in discovering and identifying data. For example, the metadata of a book might include its title, author, publisher, and ISBN.
* **Structural Metadata**: This indicates how a dataset is organized or how complex objects are put together. For instance, in a database, structural metadata would describe the tables, columns, relationships, and other structures used to organize data.
* **Administrative Metadata**: This provides information to help manage a resource, like when and how it was created, file type, and access permissions. It might also include technical data necessary for managing digital resources, such as file types or compression methods.
* **Reference Metadata**: It provides information about the contents and quality of statistical data. This type is common in data-centric fields like statistics and data analysis, providing details on data sources, accuracy, and timeliness.

#### **2. Metadata of MIPI**

In the context of MIPI, metadata can involve various types of information depending on the application. For example, in camera interfaces like MIPI CSI-2, metadata may include details about camera module parameters, resolution settings, frame rates, color spaces, white balance settings, sharpness, and chrominance. These details are crucial for properly configuring and utilizing the camera module.

Additionally, metadata might also pertain to control information related to data transmission, synchronization, error detection, and correction. This metadata is essential for ensuring the integrity and accuracy of data, especially in environments characterized by high-speed and low-power transmission.

On a broader scale, MIPI metadata may also involve system-level information, such as the connections between devices, data transmission rates, and power consumption budgets. This information aids in system-level design and optimization to ensure optimal performance and power efficiency of the entire system.

The specific definitions and implementations of metadata in the MIPI standards can vary based on different applications and requirements, and the information included in the metadata may differ among various device manufacturers.

#### **3. Gemini 330 Series Metadata Definition**

Orbbec 3D cameras typically include components such as 2 IR modules, LDM, laser ranging module, and a color camera. Both the IR module and the color camera transmit data to the mainboard using the MIPI protocol, thus carrying metadata. Users can utilize the Orbbec SDK to parse this metadata and view it directly within the Orbbec Viewer to see the current data stream’s metadata information.

Taking the Gemini 335 as an example, the supported metadata includes the following content:

Table 1: Depth/IR metadata

| **Metadata**       | **Definition**                              | **Range**                                                                                                                     |
| ------------------ | ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| timestamp          | exposure end timestamp                      | /                                                                                                                             |
| sensor timestamp   | Exposure center timestamp-1/2 exposure time | /                                                                                                                             |
| frame number       | current frame number                        | /                                                                                                                             |
| auto exposure      | content of AE state                         | \[0,1] 0 for off, 1 for on                                                                                                    |
| exposure           | content of exposure time                    | 1\~19900                                                                                                                      |
| gain               | content of exposure digital gain            | 16\~248                                                                                                                       |
| ae roi left        | ROI AE start pixel X-axis                   | 0\~1278                                                                                                                       |
| ae roi top         | ROI AE start pixel Y-axis                   | 0\~798                                                                                                                        |
| ae roi right       | ROI AE end pixel X-axis                     | 1\~1279                                                                                                                       |
| ae roi bottom      | ROI AE end pixel Y-axis                     | 1\~799                                                                                                                        |
| exposure priority  | Content of AE exposure priority state       | \[0,1]                                                                                                                        |
| hdr sequence name  | User-defined content                        | User-defined content                                                                                                          |
| hdr sequence size  | HDR frame total number                      | \[0,2] 0 for off, 2 for on                                                                                                    |
| hdr sequence index | HDR frame sequence                          | \[0,1] 0 for the first frame, 1 for the second frame                                                                          |
| laser power        | laser optical power                         | \[0,60,120,240,300,360]                                                                                                       |
| laser power mode   | content of laser switch on or off           | \[0,1] 0 for off, 1 for on                                                                                                    |
| emitter mode       | Reserved                                    | <p>[0,1,2,3] 0 – all emitters disabled.<br>1 – laser enabled.<br>2 – auto laser enabled (opt).<br>3 – LED enabled (opt).*</p> |
| Gpio Input Data    | Reserved                                    | Reserved                                                                                                                      |

Table 2: RGB metadata definition

| **Metadata**           | **Definition**                                                                   | **Range**                            |
| ---------------------- | -------------------------------------------------------------------------------- | ------------------------------------ |
| timestamp              | 335: exposure start timestamp 335L: exposure end timestamp                       | /                                    |
| sensor timestamp       | 335: Exposure center timestamp 335L: Exposure center timestamp-1/2 exposure time | /                                    |
| frame number           | current frame number                                                             | /                                    |
| auto exposure          | content of AE state                                                              | \[0,1]                               |
| exposure               | content of exposure time(us)                                                     | \[1,10000]                           |
| gain                   | content of exposure digital gain                                                 | \[0,128]                             |
| auto white balance     | content of AWB state                                                             | 0 or 1                               |
| white balance          | current AWB color temperature                                                    | \[2800,6500]                         |
| brightness             | current brightness                                                               | \[-64,64]                            |
| contrast               | contrast                                                                         | \[0,100]                             |
| saturation             | saturation                                                                       | \[0,100]                             |
| sharpness              | sharpness                                                                        | \[0,100]                             |
| backlight compensation | state of backlight compensation enable                                           | <p>[0,1]<br>0 for off, 1 for on</p>  |
| hue                    | hue                                                                              | \[-180,180]                          |
| Gamma                  | Gamma                                                                            | \[100,500]                           |
| power line frequency   | anti-flicker state                                                               | \[50,60, disable, auto]              |
| low light compensation | state of low light compensation enable                                           | \[0,1] 0 for off, 1 for on           |
| manual white balance   | current AWB color temperature set manually                                       | \[2800,6500]                         |
| actual frame rate      | frame rate set                                                                   | \[5,10,15,30,60]                     |
| ae roi left            | ROI AE start pixel X-axis                                                        | <p>335 [0,1918]<br>335L [0,1278]</p> |
| ae roi top             | ROI AE start pixel Y-axis                                                        | <p>335 [0,1078]<br>335L [0,798]</p>  |
| ae roi right           | ROI AE end pixel X-axis                                                          | <p>335 [1,1919]<br>335L [1,1279]</p> |
| ae roi bottom          | ROI AE end pixel Y-axis                                                          | <p>335 [1,1079]<br>335L [1,799]</p>  |

When using Orbbec 3D cameras on user platforms, metadata can be utilized to assess frame information, enabling advanced functions such as data correction, frame loss verification, and HDR (High Dynamic Range) fusion. This allows for enhanced accuracy and functionality in applications where precise imaging and data integrity are critical.

### Coordinate Systems (Stereo Vision 3D Camera)

#### **1. Brief Introduction**

Gemini 330 series 3D camera usually contains depth camera, color camera, and IMU. Those sensors collect information and output it as streams.

In order to characterize the positional relationship better, the Orbbec Gemini 330 series define 3D camera coordinate system. The coordinate system of a 3D camera typically contains the Depth coordinate system & the Color coordinate system & the IMU coordinate system.

#### **2. System Coordinate**

Every coordinate usually consists of three components:

1. Origin: The Depth coordinate system’s origin is located at the optical center of the Left IR camera lens. The color coordinate system’s origin is located at the optical center of the Color camera lens. The IMU coordinate system’s origin is located at the physical center of the IMU.
2. Category: meeting the definition of right-hand coordinate system. The positive direction of the X-axis is to the right. The positive direction of the Y-axis is down. The positive direction of the Z-axis is forward. The X, Y, and Z axes are red, green, and blue, respectively.

Picture 1: Right-hand coordinate system

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/94OqClDe76mhRCuQKQq4/assets/e7eae98014be6f213115.webp)

1. Unit: The Default unit is millimeters.

#### **3. Gemini 330 Series System Coordinate**

Gemini 330 series coordinate system reference picture is shown below.

Picture 2: Coordinate system schematic diagram

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3OZxyKX3ulYM28xW50NG/assets/5ffc5616db06fc590f36.webp)

The relative position relationship of the coordinate systems' origins is as follows.

Table 1: Relative position of coordinate systems for Gemini 335/336

\*\*Relative position\*\*\*\*X(mm)\*\*\*\*Y(mm)\*\*\*\*Z(mm)\*\*Origin of the Depth coordinate system000Origin of the Color coordinate system14.0002.02Origin of the IMU coordinate system-0.246-0.065-16.948Table 2: Relative position of coordinate systems for Gemini 335L/336L

\*\*Relative position\*\*\*\*X(mm)\*\*\*\*Y(mm)\*\*\*\*Z(mm)\*\*Origin of the Depth coordinate system000Origin of the Color coordinate system23.7500Origin of the IMU coordinate system7.8661.068-14.248

### Orbbec SDK Supported Features

#### **1. Introduction**

Orbbec SDK is a cross-platform (Windows, Android, Linux) software development package for 3D sensor cameras such as Orbbec optical structured light, Binocular, and iToF. It provides device parameter configuration, data stream reading, and stream processing.

#### **2. Core Features**

* Depth camera access and related parameter settings
* RGB camera access and related parameter settings (such as exposure and white balance)
* Sensor access and related parameter settings (e.g. gyroscope and accelerometer)
* Frame synchronization and alignment control
* Point cloud data
* Filtering and other algorithm capabilities
* Support for multiple operating systems and Wrapper.

#### **3. Features Matrix**

Please refer to this [Features matrix](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/25125938/Features-matrix.xlsx)

### Install Orbbec SDK

This document describes how to install the Orbbec SDK via installation packages on both Windows and Linux.

#### **1. Windows Installation Guidance**

Download the installer "OrbbecSDK\_vx.x.x\_win64.exe" from [https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

The installation process is as follows:

1. Double-click the .exe file, and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Pmg5MrETb3OeXLOxayz8/assets/5e15862c63e72cdcd39e.webp)

2. Click "Next", and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Lb5GJVNgixm5gPRFo1Yu/assets/28459d7422c73257fc95.webp)

3. Click "I Agree", and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/BXBmBshmIBJJJPJAsK8H/assets/77b3896ccd0a91da4f7d.webp)

4. Click "Next" again:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/veqi5voFWcFy8NDSET5D/assets/c2ccdbf6bb36816d1dbc.webp)

5. Click "Install" and wait for the installation to complete.

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/v6FskLHgVtBVDfw5SnDn/assets/811604151023bc3113f5.webp)

6. After the installation, the files in the Orbbec SDK installation directory are as follows:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UCqjvQSlZxgo61JvAsgT/assets/2fcc0e2592524b4e97dd.webp)

The Orbbec Viewer can be accessed via the desktop shortcut.

#### **2. Linux /Arm64 Installation Guidance**

**2.1 Install via .deb Package**

.deb package download link:[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

OrbbecSDK\_vx.x.x\_amd64.deb is the installation package for Linux x64, and OrbbecSDK\_vx.x.x\_arm64.deb is the installation package for Arm64.

1. On the Linux x64 (Ubuntu) platform, install using the following command:

sudo dpkg -i OrbbecSDK\_v1.x.x\_amd64.deb # Based on the actual version

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/hQgKXcghyp17vQ65JVeB/assets/9babfeda7c4b2e9e0f2d.webp)

2. Check the entire package path of the Orbbec SDK using `dpkg -L orbbecsdk`, while the header files and library files of the Orbbec SDK will be installed in the `/usr/local` path.

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/mut1HCTffETYDNCcyQV9/assets/2aa91af2b869c17736c7.webp)

3. Enter `OrbbecViewer` to run the Orbbec Viewer.

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/goXZCI328ASousl3W8g9/assets/0bdd921db96872a286ed.webp)

**2.2 Install via Debian Apt Repository**

1. In the terminal, enter the following command to obtain and add the public key used for verification:

wget -O – [http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec\_sdk/pub\_key.pub](http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk/pub_key.pub) | sudo apt-key add –

* Check if the public key was added successfully by entering:apt-key list

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/CRLBiAUJVa4UETFpivXl/assets/b6c1b996f287f5cc4468.webp)

If there is a problem with the host not resolving, try the following command to restart the system DNS resolution service and retry the first command:

```
sudo systemctl restart systemd-resolved
```

2. In the terminal, enter the following command to add the apt source update address:

`echo "deb [http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk](http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk) stable main" | sudo tee /etc/apt/sources.list.d/orbbec-orbbecsdk.list`

3. The following command can be used to query the Orbbec SDK:

`sudo apt update`\
`sudo apt search orbbecsdk`

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JTFBR4mHj8H1JTEehe5W/assets/934ed1c086933f55fda9.webp)

4. Check the installation directory of the Orbbec SDK through `dpkg -L orbbecsdk`, and by entering the `OrbbecViewer` Command, you can run the Orbbec Viewer.

### Programming fundamentals

#### **1. Get the First Orbbec Device**

```
ob::Context ctx;
auto devList = ctx.queryDeviceList();
auto dev = devList->getDevice(0);
```

#### **2. Start Streaming with Default Configuration**

```
ob::Pipeline pipe;  // create pipe with default device
pipe.start(nullptr);  // start with defualt configuratio
```

#### **3. Start Streaming Infrared Image**

For TOF or Single-Camera structured light devices:

```
ob::Pipeline pipe;
std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();
auto irProfiles = pipe.getStreamProfileList(OB_SENSOR_IR);
auto irProfile = irProfiles->getProfile(OB_PROFILE_DEFAULT);
config->enableStream(irProfile);
pipe.start(config);
```

For Dual-Camera structured light devices:

```
ob::Pipeline pipe;
std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();

auto irLeftProfiles = pipe.getStreamProfileList(OB_SENSOR_IR_LEFT);
auto irLeftProfile = irLeftProfiles->getProfile(OB_PROFILE_DEFAULT);
config->enableStream(irLeftProfile);

auto irRightProfiles = pipe.getStreamProfileList(OB_SENSOR_IR_RIGHT);
auto irRightProfile = irRightProfiles->getProfile(OB_PROFILE_DEFAULT);
config->enableStream(irRightProfile);

pipe.start(config);
```

#### **4. Wait for a Coherent Set of Frames**

```
ob::Pipeline pipe;
pipe.start(nullptr);
auto frameSet = pipe.waitForFrames(100);
auto depthFrame = frameSet->depthFrame();
```

#### **5. Do Processing on a Background-Thread**

```
std::mutex frameQueueMtx;
std::queue<std::shared_ptr<ob::Frame>> frameQueue;
auto precessThread = std::thread([&](){
    std::shared_ptr<ob::Frame> depthFrame;
    while(true{
      {
        std::lock_guard<std::mutex> lk(frameQueueMtx);
        if(frameQueue.empty()){
          std::this_thread::sleep_for(std::chrono::milliseconds(10));
          continue;
        }
        depthFrame = frameQueue.front();
        frameQueue.pop();
      }
      auto depthFrameData = depthFrame->data();
      // do some thing to process depth frame data;
    }
})
ob::Pipeline pipe;
pipe.start(nullptr);
while(true){ 
  auto frameSet = pipe.waitForFrames(100);
  auto depthFrame = frameSet->depthFrame();

  if(depthFrame){
    std::lock_guard<std::mutex> lk(frameQueueMtx);
    frameQueue.push(depthFrame)
  }
}
```

#### **6. Get Depth-to-Color Extrinsics**

```
ob::Pipeline pipe;
auto depthProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH);
auto depthProfile = depthProfiles->getProfile(OB_PROFILE_DEFAULT);
auto colorProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH);
auto colorProfile = depthProfiles->getProfile(OB_PROFILE_DEFAULT);

auto extrinsics = depthProfile->getExtrinsicTo(colorProfile);
```

#### **7. Get Video Stream Intrinsics**

From pipeline:

```
ob::Pipeline pipe;
pipe.start(nullptr);
// get camera intrinsic and extrinsic parameters form pipeline and set to point cloud filter
auto cameraParam = pipeline.getCameraParam();
```

From Frame/StreamProfile (Gemini 300 series only):

```
ob::Pipeline pipe;
pipe.start(nullptr);

auto frameSet = pipe.waitForFrames(100);
auto frame = frameSet->depthFrame();
auto streamProfile = frame->getStreamProfile();
auto videoStreamProfile = streamProfile->as<ob::VideoStreamProfile>();

auto intrinsic = videoStreamProfile->getIntrinsic();
```

#### **8. Get Depth Units**

```
ob::Pipeline pipe;
pipe.start(nullptr);

auto frameSet = pipe.waitForFrames(100);
auto depthFrame = frameSet->depthFrame();

auto uint = depthFrame->getValueScale();
```

#### **9. Controll the Laser**

```
ob::Pipeline pipe;
auto dev = pipe->getDevice();

// Laser control (for Gemini 300 series)
dev->setIntProperty(OB_PROP_LASER_CONTROL_INT, 1); // 0: off, 1: on, 2: auto

// Turn on/off laser (for other series)
dev->setBoolProperty(OB_PROP_LASER_BOOL, true);

// Laser energy level control
dev->setIntProperty(OB_PROP_LASER_ENERGY_LEVEL_INT, 2);
```

### What is a Filter

#### **1.1 What is a Filter?**

A Filter is a post-processing module provided by OrbbecSDK v2 for processing raw frames from the sensor. Common use cases include:

• Removing noise and holes from depth maps

• Spatial and temporal smoothing of depth maps

• Downsampling images to reduce resolution, data size, and improve downstream processing performance

• Software-based alignment of depth and color streams

• Converting frame pixel formats

• Generating point cloud data

**⚠ Note:Filters are not limited to Depth streams. Some Filters also support Color or IR streams. Always check the applicable stream type for each Filter.**

#### **1.2 Two Ways to Use Filters**

| **Method**                  | **Description**                                                                                                                                                           | **Use Case**                                 |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **Create Filter Directly**  | Explicitly specify which Filter to use and configure its parameters                                                                                                       | Fine-grained control, custom scenarios       |
| **Recommended Filter List** | Obtained from a specific Sensor. The SDK returns a recommended Filter combination based on the Sensor's stream type. Can only process frames of the matching stream type. | Quick integration, general-purpose scenarios |

\*\*✅ Tip:\*\*Not sure which method your device supports, or which one to choose? **Start with the Recommended Filter List to get up and running quickly**. Switch to "Create Filter Directly" when you need custom configuration.

#### **1.3 Complete Filter Quick Reference**

| **Filter Name**         | **Applicable Stream** | **Description**                                                                                 | **Type**             |
| ----------------------- | --------------------- | ----------------------------------------------------------------------------------------------- | -------------------- |
| PointCloudFilter        | Depth / Depth+Color   | Converts depth frames to XYZ point clouds, or depth+color frames to RGBD point clouds (XYZ+RGB) | Transformation       |
| Align                   | Depth + Color         | Software-based spatial alignment between depth and color streams                                | Transformation       |
| FormatConvertFilter     | Color / IR            | Pixel format conversion (e.g., MJPG→RGB, YUYV→BGR, etc.)                                        | Transformation       |
| DisparityTransform      | Depth                 | Bidirectional conversion between depth and disparity maps                                       | Transformation       |
| SequenceIdFilter        | Depth / IR            | Filters frames by sequence ID, used with HDR                                                    | Flow Control         |
| DecimationFilter        | Depth / IR / Color    | Downsamples the image to reduce resolution                                                      | Sampling / Threshold |
| ThresholdFilter         | Depth                 | Zeroes out depth values outside the specified range                                             | Sampling / Threshold |
| NoiseRemovalFilter      | Depth                 | Removes noise from depth maps (basic)                                                           | Noise Reduction      |
| **FalsePositiveFilter** | **Depth**             | **Removes various types of noise from depth maps (advanced)**                                   | **Noise Reduction**  |
| SpatialAdvancedFilter   | Depth                 | Edge-preserving spatial smoothing, high quality                                                 | Spatial Smoothing    |
| SpatialFastFilter       | Depth                 | Fast spatial smoothing, low CPU usage                                                           | Spatial Smoothing    |
| SpatialModerateFilter   | Depth                 | Balanced spatial smoothing between speed and quality                                            | Spatial Smoothing    |
| HoleFillingFilter       | Depth                 | Fills holes in depth maps                                                                       | Spatial Smoothing    |
| TemporalFilter          | Depth                 | Temporal smoothing by fusing adjacent frame data                                                | Temporal Smoothing   |

\*\*Note:\*\*NoiseRemovalFilter is called automatically inside the SDK. You can only enable/disable it or adjust its parameters. It cannot be created independently. All other Filters are public types - create them directly with no activation code required.

#### **1.4 Two Frame Processing Modes**

**Synchronous Processing (recommended, suitable for most scenarios)**

_auto outFrame = filter->process(inFrame);_

_if(outFrame) {_

_// Use the processed frame_

_}_

**Asynchronous Processing (suitable for high frame rate or pipeline scenarios)**

_// Set the callback, triggered automatically when processing completes_

_filter->setCallBack(\[]\(std::shared\_ptr_[_ob::Frame_](ob::Frame) _outFrame) {_

_if(outFrame) {_

_// Use the processed frame_

_}_

_});_

_// Push the frame into the Filter's processing queue_

_filter->pushFrame(inFrame);_

**⚠ Note:**`process()` may return `nullptr` in some cases. Always check the return value before using it.

### Detailed Filter Reference

####

**1. Transformation**

**1.1 PointCloudFilter**

\*\*Applicable Stream:\*\*Depth (for XYZ point cloud); Depth + Color (for RGBD point cloud, requires Depth and Color to be aligned (D2C) first, otherwise color mapping will be incorrect)

\*\*Function:\*\*Converts depth frames to XYZ point clouds (OB\_FORMAT\_POINT), or aligned depth+color frames to RGBD point clouds (OB\_FORMAT\_RGB\_POINT, each point contains XYZ coordinates and RGB color)

| **Parameter** | **Type** | **Range**                                  | **Default**       | **Description**                                                              |
| ------------- | -------- | ------------------------------------------ | ----------------- | ---------------------------------------------------------------------------- |
| pointFormat   | OBFormat | OB\_FORMAT\_POINT / OB\_FORMAT\_RGB\_POINT | OB\_FORMAT\_POINT | Point cloud format                                                           |
| decimate      | int      | 1 \~ 8                                     | 1                 | Point cloud decimation factor. Values > 1 downsample the output point cloud. |

**Example 1: XYZ Point Cloud**

_auto pointCloudFilter = std::make\_shared_[_ob::PointCloudFilter_](ob::PointCloudFilter)_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_POINT);_

_pointCloudFilter->setCoordinateDataScaled(1.0f);_

_// Can pass a standalone Depth frame or a FrameSet containing a Depth frame_

_auto pointCloudFrame = pointCloudFilter->process(depthFrame);_

_if(pointCloudFrame) {_

_auto points = pointCloudFrame->as_[_ob::PointsFrame_](ob::PointsFrame)_();_

_// Use point cloud data ..._

_}_

**Example 2: RGBD Point Cloud**

To generate an RGBD point cloud, the depth and color frames must be spatially aligned before being passed to PointCloudFilter. There are two alignment methods: prefer hardware D2C (better performance); if the resolution does not support hardware D2C, use the software Align Filter.

**Method 1: Hardware D2C Alignment (recommended, use when resolution supports it)**

_auto pointCloudFilter = std::make\_shared_[_ob::PointCloudFilter_](ob::PointCloudFilter)_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_RGB\_POINT);_

_// Enable hardware D2C in Config. The FrameSet output by Pipeline is already aligned_

_std::shared\_ptr_[_ob::Config_](ob::Config) _config = std::make\_shared_[_ob::Config_](ob::Config)_();_

_config->enableVideoStream(OB\_STREAM\_DEPTH);_

_config->enableVideoStream(OB\_STREAM\_COLOR);_

_config->setAlignMode(ALIGN\_D2C\_HW\_MODE);_

_pipe.start(config);_

_auto frameSet = pipe.waitForFrameset(100);_

_auto rgbdPointCloudFrame = pointCloudFilter->process(frameSet);_

_if(rgbdPointCloudFrame) {_

_auto points = rgbdPointCloudFrame->as_[_ob::PointsFrame_](ob::PointsFrame)_();_

_// Each point contains XYZ coordinates and RGB color ..._

_}_

**Method 2: Software Align Filter (use when the resolution does not support hardware D2C)**

_auto pointCloudFilter = std::make\_shared_[_ob::PointCloudFilter_](ob::PointCloudFilter)_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_RGB\_POINT);_

_auto alignFilter = std::make\_shared_[_ob::Align_](ob::Align)_(OB\_STREAM\_COLOR);_

_// frameSet comes from Pipeline (must enable both Depth and Color streams)_

_auto frameSet = pipe.waitForFrameset(100);_

_auto alignedFrameSet = alignFilter->process(frameSet); // FrameSet after software alignment_

_auto rgbdPointCloudFrame = pointCloudFilter->process(alignedFrameSet);_

_if(rgbdPointCloudFrame) {_

_auto points = rgbdPointCloudFrame->as_[_ob::PointsFrame_](ob::PointsFrame)_();_

_// Each point contains XYZ coordinates and RGB color ..._

_}_

**1.2 Align**

\*\*Applicable Stream:\*\*Depth + Color. \*\*Function:\*\*Performs software-based spatial alignment between two streams, eliminating parallax offset between depth and color images. Unlike hardware D2C alignment, the Align Filter runs on the CPU, requires no hardware support, and offers more flexibility — but with higher platform resource consumption. If your device supports hardware D2C alignment, prefer it for better performance.

| **Parameter** | **Type**     | **Description**                                                                                                                |
| ------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| AlignType     | OBStreamType | Alignment target stream type: OB\_STREAM\_COLOR (depth aligned to color, D2C), OB\_STREAM\_DEPTH (color aligned to depth, C2D) |

_// Specify the alignment target when creating (depth aligned to color)_

_auto alignFilter = std::make\_shared_[_ob::Align_](ob::Align)_(OB\_STREAM\_COLOR);_

_// Ensure both Depth and Color frames exist in the FrameSet_

_auto depthFrame = frameSet->getFrame(OB\_FRAME\_DEPTH);_

_auto colorFrame = frameSet->getFrame(OB\_FRAME\_COLOR);_

_if(!depthFrame || !colorFrame) {_

_// Depth or Color frame missing, cannot perform alignment_

_continue;_

_}_

_// Process the FrameSet_

_auto alignedFrameSet = alignFilter->process(frameSet);_

_if(alignedFrameSet) {_

_auto alignedDepth = alignedFrameSet->as_[_ob::FrameSet_](ob::FrameSet)_()->getFrame(OB\_FRAME\_DEPTH);_

_}_

**1.3 FormatConvertFilter**

\*\*Applicable Stream:\*\*Color (YUYV/MJPG/NV12/NV21 to RGB/BGR, etc.); IR (Y16 to RGB, etc.). \*\*Function:\*\*Converts a frame's pixel format from one type to another. Commonly used to convert the camera's raw output format into a format directly usable by OpenCV.

| **Enum Value**         | **Description** |
| ---------------------- | --------------- |
| FORMAT\_YUYV\_TO\_RGB  | YUYV → RGB      |
| FORMAT\_MJPG\_TO\_RGB  | MJPG → RGB      |
| FORMAT\_MJPG\_TO\_BGR  | MJPG → BGR      |
| FORMAT\_MJPG\_TO\_NV21 | MJPG → NV21     |
| FORMAT\_MJPG\_TO\_NV12 | MJPG → NV12     |
| FORMAT\_NV12\_TO\_RGB  | NV12 → RGB      |
| FORMAT\_NV21\_TO\_RGB  | NV21 → RGB      |
| FORMAT\_RGB\_TO\_BGR   | RGB → BGR       |
| FORMAT\_Y16\_TO\_RGB   | Y16 (IR) → RGB  |

_auto formatConvertFilter = std::make\_shared_[_ob::FormatConvertFilter_](ob::FormatConvertFilter)_();_

_formatConvertFilter->setFormatConvertType(FORMAT\_MJPG\_TO\_RGB);_

_auto rgbFrame = formatConvertFilter->process(colorFrame);_

_if(rgbFrame) {_

_// rgbFrame is now in RGB format, directly usable for OpenCV display_

_}_

**1.4 DisparityTransform**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Converts disparity maps to depth maps. The camera outputs depth data by default. This filter is only needed when you have switched to disparity-format data and need to convert it back to depth format.

**⚠ Note:**(1) Depth filters like ThresholdFilter only work on Depth data (in mm). (2) If the input is in Disparity format, it must first be converted via DisparityTransform, otherwise the filtering result will be invalid.

_auto disparityTransform = std::make\_shared_[_ob::DisparityTransform_](ob::DisparityTransform)_();_

_auto depthFrame = disparityTransform->process(disparityFrame);_

**2. Flow Control**

**2.1 SequenceIdFilter**

**Applicable Stream:** Depth / IR. \*\*Function:\*\*Filters frames from a FrameSet by the specified sequence ID. Used with HDR. Only takes effect when the HDR Merge Filter is disabled. selectSequenceId(0) passes all frames through; selectSequenceId(1) only keeps frames with sequence ID 1.

| **Parameter** | **Type** | **Range** | **Default** | **Description**                                           |
| ------------- | -------- | --------- | ----------- | --------------------------------------------------------- |
| sequenceid    | int      | -1 \~ 1   | 0           | Frame sequence ID to retain. 0 passes all frames through. |

_auto seqFilter = std::make\_shared_[_ob::SequenceIdFilter_](ob::SequenceIdFilter)_();_

_seqFilter->selectSequenceId(1); // Only keep frames with sequence ID 1_

_auto filteredFrame = seqFilter->process(frameSet);_

**3. Sampling / Threshold**

**3.1 DecimationFilter**

\*\*Applicable Stream:\*\*Depth / IR / Color. \*\*Function:\*\*Downsamples the image by a specified factor, reducing resolution and lowering computational load for downstream processing. However, higher sampling rates result in more detail loss.

| **Parameter** | **Type** | **Range** | **Default** | **Description**                                                                    |
| ------------- | -------- | --------- | ----------- | ---------------------------------------------------------------------------------- |
| decimate      | uint8    | 1 \~ 8    | 2           | Downsampling factor. For example, 2 reduces the resolution to 1/2 of the original. |

auto decimationFilter = std::make\_shared[ob::DecimationFilter](ob::DecimationFilter)();

// Query the supported scale range

auto scaleRange = decimationFilter->getScaleRange();

std::cout << "scale range: " << (int)scaleRange.min << " \~ "

<< (int)scaleRange.max << std::endl;

decimationFilter->setScaleValue(2); // Reduce resolution to 1/2 of original

auto outFrame = decimationFilter->process(depthFrame);

\*\*⚠ Note:\*\*The frame resolution changes after downsampling. Subsequent Filters or algorithms must adapt to the new resolution.

Depth effect before and after 1/2 downsampling:

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ovmIv8Iz7JgvXD8JIoxl/assets/11ef93a0a36ea25b8125.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/image.png)

**3.2 ThresholdFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Zeroes out pixels whose depth values fall outside the specified range \[min, max] (in mm). Used to filter out invalid depth values that are too close or too far. Only effective on Depth data (mm), not on Disparity data.

| **Parameter** | **Type** | **Range**  | **Default** | **Description**                |
| ------------- | -------- | ---------- | ----------- | ------------------------------ |
| min           | uint32   | 0 \~ 16000 | 0           | Minimum valid depth value (mm) |
| max           | uint32   | 0 \~ 16000 | 16000       | Maximum valid depth value (mm) |

_auto thresholdFilter = std::make\_shared_[_ob::ThresholdFilter_](ob::ThresholdFilter)_();_

_// Query the supported range_

_auto minRange = thresholdFilter->getMinRange();_

_auto maxRange = thresholdFilter->getMaxRange();_

_// Only keep depth values in the 300mm\~3000mm range_

_thresholdFilter->setValueRange(300, 3000);_

_auto outFrame = thresholdFilter->process(depthFrame);_

**4. Noise Reduction**

**4.1 NoiseRemovalFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Applies clustering to the depth map to identify and filter out noisy regions. As a basic noise reduction filter that runs inside the SDK, it is enabled by default on most devices and does not need to be created manually. Use the "Recommended Filter List" to toggle its state and adjust parameters.

| **Parameter** | **Type** | **Range**  | **Default** | **Description**                                                                                                                                       |
| ------------- | -------- | ---------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| min\_diff     | uint16   | 1 \~ 51200 | 256         | Depth spatial filtering range. Larger values weaken the denoising effect (retaining more detail); smaller values strengthen denoising.                |
| max\_size     | uint16   | 1 \~ 1000  | 80          | Maximum pixel area of noise clusters. Larger values make denoising more aggressive (filtering larger noise clusters), but may reduce depth fill rate. |

Depth effect before and after enabling NoiseRemovalFilter:

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/LUvPQ9LrJ5sqLK83iztX/assets/a84a7598a3a69c8ae458.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/cc1image.png)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qnPQwMYfhV9DVkVor84M/assets/1cfa1d91b1de4138e9c7.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/oL5image.png)

**4.2 FalsePositiveFilter**

\*\*Applicable Stream:\*\*Depth. **Function:** Filters out erroneous depth values (ghost noise) from the depth map. This filter functionally supersedes NoiseRemovalFilter and consumes more platform resources. It is recommended to disable NoiseRemovalFilter when enabling FalsePositiveFilter.

Because this filter has too many parameters to pass individually when creating it directly, it only supports enable/disable via filter->enable(bool). No additional parameter configuration is needed. **It is strongly recommended to use the "Recommended Filter List" approach.**

_auto fpFilter = std::make\_shared_[_ob::FalsePositiveFilter_](ob::FalsePositiveFilter)_();_

_// Enable the filter_

_fpFilter->enable(true);_

_auto outFrame = fpFilter->process(depthFrame);_

This filter consists of three sub-filters, each targeting noise in a specific scenario. Since the filtering process may misclassify and remove valid depth data, each sub-filter exposes ROI parameters to precisely control the filter's region of influence, avoiding damage to valid depth. Adjust the ROI range as needed.

**4.3 FalsePositiveFilter::EdgeBleedFilter**

\*\*Function:\*\*Filters out laterally extended erroneous depth at object edges. \*\*Typical scenarios:\*\*semi-outdoor window edges, overexposed outdoor sky, etc. \*\*Rule:\*\*Within the depth map ROI, when more than fpebfMinBleedLength consecutive pixels have identical depth values in the horizontal direction, the region is classified as edge bleed noise and filtered out. For example, setting fpebfMinBleedLength = 40 triggers filtering when more than 40 consecutive pixels have the same depth value.

| **Parameter**           | **Type** | **Range**  | **Default** | **Description**                                                                                                                                 |
| ----------------------- | -------- | ---------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| fpEdgeBleedFilterEnable | bool     | 0 \~ 1     | 0           | Edge bleed filter toggle                                                                                                                        |
| fpebfROIMinXRatio       | float    | 0.0 \~ 1.0 | 0.0         | ROI left boundary (proportion of image width, 0.0 = left edge)                                                                                  |
| fpebfROIMaxXRatio       | float    | 0.0 \~ 1.0 | 1.0         | ROI right boundary (proportion of image width, 1.0 = right edge)                                                                                |
| fpebfROIMinYRatio       | float    | 0.0 \~ 1.0 | 0.0         | ROI top boundary (proportion of image height, 0.0 = top edge)                                                                                   |
| fpebfROIMaxYRatio       | float    | 0.0 \~ 1.0 | 0.6         | ROI bottom boundary (proportion of image height, 1.0 = bottom edge)                                                                             |
| fpebfMinBleedLength     | int      | 1 \~ 256   | 40          | Minimum consecutive bleed length (pixels). Filtering is triggered when the number of consecutive identical-depth pixels exceeds this threshold. |

Depth effect before and after enabling EdgeBleedFilter (laterally extended noise has been filtered):

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/h67d2BEqwytUZpRerFTZ/assets/44c54a2a9c78b34db24d.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/ZT6image.png)

At close range, depth values are more similar. When capturing flat surfaces, false positives may cause lateral depth loss.

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/axKvhPrKyT9ODQbgXek9/assets/5b048624b966bcd309df.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/9v4image.png)

**\*\*4.4 FalsePositiveFilter::\*\*TextureSparsityFilter**

\*\*Function:\*\*Filters out erroneous depth in low-texture scenes. \*\*Typical scenarios:\*\*outdoor white walls, non-overexposed sky, etc. \*\*Rule:\*\*Within the depth map ROI, noise regions that satisfy both of the following conditions will be filtered out:

l Average depth value of noise region < fptsfMaxNoiseLevel

l Pixel area of noise cluster < fptsfMaxSpeckleSize

| **Parameter**                 | **Type** | **Range**  | **Default** | **Description**                                                                            |
| ----------------------------- | -------- | ---------- | ----------- | ------------------------------------------------------------------------------------------ |
| fpTextureSparsityFilterEnable | bool     | 0 \~ 1     | 0           | Low-texture filter toggle                                                                  |
| fptsfROIMinXRatio             | float    | 0.0 \~ 1.0 | 0.0         | ROI left boundary (proportion of image width, 0.0 = left edge)                             |
| fptsfROIMaxXRatio             | float    | 0.0 \~ 1.0 | 1.0         | ROI right boundary (proportion of image width, 1.0 = right edge)                           |
| fptsfROIMinYRatio             | float    | 0.0 \~ 1.0 | 0.0         | ROI top boundary (proportion of image height, 0.0 = top edge)                              |
| fptsfROIMaxYRatio             | float    | 0.0 \~ 1.0 | 0.45        | ROI bottom boundary (proportion of image height, 1.0 = bottom edge)                        |
| fptsfMaxNoiseLevel            | int      | 1 \~ 65535 | 6000        | Maximum noise depth value (mm). Only removes noise with depth values below this threshold. |
| fptsfMaxSpeckleSize           | int      | 1 \~ 65535 | 1300        | Maximum pixel area of noise clusters. Only removes clusters smaller than this value.       |

Depth effect before and after enabling TextureSparsityFilter (noise in the sky has been filtered):

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/OuDgJle9FDaiTWdo5ICs/assets/3028b3ea1c9d8813daf9.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/h6himage.png)

**\*\*4.5 FalsePositiveFilter::\*\*PatternAmbiguityFilter**

\*\*Function:\*\*Filters out erroneous depth in repetitive texture scenes. \*\*Typical scenarios:\*\*fences, building windows, etc. \*\*Rule:\*\*Within the depth map ROI, noise regions that satisfy ALL of the following conditions will be filtered out:

l Average depth value of noise region < fppafMaxNoiseLevel

l Pixel area of noise cluster < fppafMaxSpeckleSize

l Noise cluster width < image width × fppafMaxWidthRatio

l Noise cluster height < image height × fppafMaxHeightRatio

l Noise Tolerance feature > fppafTolerance

l Noise Score feature > fppafScore

| **Parameter**                  | **Type** | **Range**  | **Default** | **Description**                                                                            |
| ------------------------------ | -------- | ---------- | ----------- | ------------------------------------------------------------------------------------------ |
| fpPatternAmbiguityFilterEnable | bool     | 0 \~ 1     | 0           | Repetitive texture filter toggle                                                           |
| fppafROIMinXRatio              | float    | 0.0 \~ 1.0 | 0.0         | ROI left boundary (proportion of image width, 0.0 = left edge)                             |
| fppafROIMaxXRatio              | float    | 0.0 \~ 1.0 | 0.99        | ROI right boundary (proportion of image width, 1.0 = right edge)                           |
| fppafROIMinYRatio              | float    | 0.0 \~ 1.0 | 0.0         | ROI top boundary (proportion of image height, 0.0 = top edge)                              |
| fppafROIMaxYRatio              | float    | 0.0 \~ 1.0 | 0.9         | ROI bottom boundary (proportion of image height, 1.0 = bottom edge)                        |
| fppafMaxNoiseLevel             | int      | 1 \~ 65535 | 6000        | Maximum noise depth value (mm). Only removes noise with depth values below this threshold. |
| fppafMaxSpeckleSize            | int      | 1 \~ 65535 | 4000        | Maximum pixel area of noise clusters. Only removes clusters smaller than this value.       |
| fppafMaxWidthRatio             | float    | 0.0 \~ 1.0 | 0.3         | Maximum noise cluster width as a proportion of image width                                 |
| fppafMaxHeightRatio            | float    | 0.0 \~ 1.0 | 0.3         | Maximum noise cluster height as a proportion of image height                               |
| fppafTolerance                 | float    | 0.0 \~ 1.0 | 0.15        | Noise tolerance feature threshold. Only removes noise when Tolerance > this value.         |
| fppafScore                     | int      | 1 \~ 65535 | 50          | Noise score threshold. Only removes noise when Score > this value.                         |

Depth effect before and after enabling PatternAmbiguityFilter (noise on building facades from repetitive textures has been filtered)

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EK28EpO3tWprMSlw1qkv/assets/f962017bd982652165ef.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/WC9image.png)

**4.6 FalsePositiveFilter Tuning Guide:**

| **Parameter**       | **Sub-Filter**         | **Adjustment Direction for Noise Suppression** |
| ------------------- | ---------------------- | ---------------------------------------------- |
| fpebfMinBleedLength | EdgeBleedFilter        | ↓ Decrease for more aggressive filtering       |
| fptsfMaxNoiseLevel  | TextureSparsityFilter  | ↑ Increase to cover farther noise              |
| fptsfMaxSpeckleSize | TextureSparsityFilter  | ↑ Increase to filter larger noise clusters     |
| fppafMaxNoiseLevel  | PatternAmbiguityFilter | ↑ Increase to cover farther noise              |
| fppafMaxSpeckleSize | PatternAmbiguityFilter | ↑ Increase to filter larger noise clusters     |
| fppafMaxWidthRatio  | PatternAmbiguityFilter | ↑ Increase to filter wider noise clusters      |
| fppafMaxHeightRatio | PatternAmbiguityFilter | ↑ Increase to filter taller noise clusters     |
| fppafTolerance      | PatternAmbiguityFilter | ↓ Decrease for more aggressive filtering       |
| fppafScore          | PatternAmbiguityFilter | ↓ Decrease for more aggressive filtering       |

**5. Spatial Smoothing**

**5.1 SpatialAdvancedFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Edge-preserving spatial smoothing. Controls smoothing strength and edge preservation through alpha and disp\_diff parameters. Smooths depth values in flat areas while preserving object edges. This is the recommended choice for depth map spatial smoothing, but also has the highest resource usage.

| **Parameter** | **Type** | **Range**  | **Default** | **Description**                                                                                      |
| ------------- | -------- | ---------- | ----------- | ---------------------------------------------------------------------------------------------------- |
| alpha         | float    | 0.1 \~ 1   | 0.5         | Current pixel weight. Larger values reduce smoothing (preserving original values). Step size: 0.01.  |
| disp\_diff    | uint16   | 1 \~ 10000 | 160         | Depth gradient threshold. Pixels exceeding this value are excluded from smoothing (edge protection). |
| radius        | uint16   | 0 \~ 8     | 1           | Smoothing radius. Affects the smoothing range.                                                       |
| magnitude     | int      | 1 \~ 5     | 1           | Number of iterations. More iterations produce stronger smoothing.                                    |

_auto spatialFilter = std::make\_shared_[_ob::SpatialAdvancedFilter_](ob::SpatialAdvancedFilter)_();_

_// Get current parameters (including defaults)_

_auto params = spatialFilter->getFilterParams();_

_// Modify parameters as needed_

_params.alpha = 0.5f;_

_params.disp\_diff = 160;_

_params.radius = 2;_

_params.magnitude = 1;_

_spatialFilter->setFilterParams(params);_

_auto outFrame = spatialFilter->process(depthFrame);_

**5.2 SpatialFastFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Fast spatial filtering based on an enhanced median smoothing algorithm. Low CPU usage, suitable for performance-sensitive scenarios.

| **Parameter** | **Type** | **Range** | **Default** | **Description**                                                                                         |
| ------------- | -------- | --------- | ----------- | ------------------------------------------------------------------------------------------------------- |
| radius        | uint8    | 3 \~ 5    | 3           | Smoothing radius. Larger values increase the smoothing range. Step size: 2, so valid values are 3 or 5. |

_auto spatialFastFilter = std::make\_shared_[_ob::SpatialFastFilter_](ob::SpatialFastFilter)_();_

_// Get current parameters (including defaults)_

_auto params = spatialFastFilter->getFilterParams();_

_// Modify parameters as needed_

_params.radius = 2;_

_spatialFastFilter->setFilterParams(params);_

_auto outFrame = spatialFastFilter->process(depthFrame);_

**5.3 SpatialModerateFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Based on an optimized mean smoothing algorithm, balancing processing speed and smoothing quality.

| **Parameter** | **Type** | **Range**  | **Default** | **Description**                                                                                      |
| ------------- | -------- | ---------- | ----------- | ---------------------------------------------------------------------------------------------------- |
| magnitude     | uint8    | 1 \~ 3     | 1           | Number of iterations. More iterations produce stronger smoothing.                                    |
| radius        | uint8    | 3 \~ 7     | 5           | Smoothing radius. Step size: 2, so valid values are 3, 5, or 7.                                      |
| disp\_diff    | uint16   | 1 \~ 10000 | 160         | Depth gradient threshold. Pixels exceeding this value are excluded from smoothing (edge protection). |

_auto spatialModFilter = std::make\_shared_[_ob::SpatialModerateFilter_](ob::SpatialModerateFilter)_();_

_// Get current parameters (including defaults)_

_auto params = spatialModFilter->getFilterParams();_

_// Modify parameters as needed_

_params.magnitude = 2;_

_params.radius = 2;_

_params.disp\_diff = 64;_

_spatialModFilter->setFilterParams(params);_

_auto outFrame = spatialModFilter->process(depthFrame);_

**5.4 HoleFillingFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Fills zero-valued hole pixels in the depth map. The fill value source depends on the selected mode.

| **Parameter**           | **Type**                                                           | **Range** | **Default** | **Description**             |
| ----------------------- | ------------------------------------------------------------------ | --------- | ----------- | --------------------------- |
| hole\_filling\_mode     | OBHoleFillingMode                                                  | 0 \~ 2    | 0 (TOP)     | Fill mode (see table below) |
| **Enum Value**          | **Description**                                                    |           |             |                             |
| OB\_HOLE\_FILL\_TOP     | Fill with the nearest valid depth value directly above the hole    |           |             |                             |
| OB\_HOLE\_FILL\_NEAREST | Fill with the nearest valid depth value from the surrounding area  |           |             |                             |
| OB\_HOLE\_FILL\_FAREST  | Fill with the farthest valid depth value from the surrounding area |           |             |                             |

_auto holeFillingFilter = std::make\_shared_[_ob::HoleFillingFilter_](ob::HoleFillingFilter)_();_

_holeFillingFilter->setFilterMode(OB\_HOLE\_FILL\_TOP);_

_auto outFrame = holeFillingFilter->process(depthFrame);_

This filter fills all holes, which may introduce false data and is generally not recommended. However, in special scenarios where complete depth is required, you can enable it with the recommended OB\_HOLE\_FILL\_FAREST mode.

Depth effect before and after enabling HoleFillingFilter (zero-depth regions have been filled):

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/SX96BYOW15aAGpSz62da/assets/0fb0c868178ec0dc5b2f.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/GWhimage.png)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/9eZCifSB3PugxThZdGqF/assets/274893fb8da7c4bf6a47.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/jvHimage.png)

**6. Temporal Smoothing**

**6.1 TemporalFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Fuses depth data from the current frame with historical frames for temporal smoothing, effectively suppressing inter-frame jitter noise.

| **Parameter** | **Type** | **Range** | **Default** | **Description**                                                                                                                                            |
| ------------- | -------- | --------- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| diff\_scale   | float    | 0.1 \~ 1  | 0.1         | Allowed depth change ratio threshold. Pixels exceeding this ratio are excluded from fusion. Step size: 0.01.                                               |
| weight        | float    | 0.1 \~ 1  | 0.4         | Fusion weight for the current frame. Larger values favor the original data (weaker smoothing), smaller values produce stronger smoothing. Step size: 0.01. |

_auto temporalFilter = std::make\_shared_[_ob::TemporalFilter_](ob::TemporalFilter)_();_

_// Query the allowed parameter range_

_auto diffScaleRange = temporalFilter->getDiffScaleRange();_

_auto weightRange = temporalFilter->getWeightRange();_

_// Set parameters as needed (within the allowed range)_

_temporalFilter->setDiffScale(0.1f); // Range: \[diffScaleRange.min, diffScaleRange.max]_

_temporalFilter->setWeight(0.4f); // Range: \[weightRange.min, weightRange.max]_

_auto outFrame = temporalFilter->process(depthFrame);_

_// Note: process() may return nullptr when there is insufficient historical data in the first few frames_

_if(outFrame) {_

_// Use the processed frame_

_}_

### Recommended Filter List

**1. Quick Start**

_#include \<libobsensor/ObSensor.hpp>_

_ob::Pipeline pipe;_

_auto device = pipe.getDevice();_

_// Step 1: Get the target Sensor (using depth stream as an example)_

_auto sensor = device->getSensor(OB\_SENSOR\_DEPTH);_

_// Step 2: Get the Recommended Filter List_

_auto filters = sensor->createRecommendedFilters();_

_// Step 3: Check if there are recommended Filters_

_if(filters.empty()) {_

_std::cout << "This Sensor does not support recommended post-processing. Use the raw frames directly." << std::endl;_

_return 0;_

_}_

_// Step 4: View the initial enabled state of each Filter_

_for(auto \&filter : filters) {_

_std::cout << filter->getName()_

_<< " : " << (filter->isEnabled() ? "enabled" : "disabled")_

_<< std::endl;_

_}_

_// Step 5: Start the data stream_

_std::shared\_ptr_[_ob::Config_](ob::Config) _config = std::make\_shared_[_ob::Config_](ob::Config)_();_

_config->enableVideoStream(OB\_STREAM\_DEPTH);_

_pipe.start(config);_

_while(true) {_

_auto frameSet = pipe.waitForFrameset(100);_

_if(!frameSet) continue;_

_auto depthFrame = frameSet->getFrame(OB\_FRAME\_DEPTH);_

_if(!depthFrame) continue;_

_// Step 6: Apply enabled Filters in sequence_

_std::shared\_ptr_[_ob::Frame_](ob::Frame) _outFrame = depthFrame;_

_for(auto \&filter : filters) {_

_if(filter->isEnabled()) {_

_auto result = filter->process(outFrame);_

_if(result) outFrame = result;_

_}_

_}_

_// outFrame is the processed depth frame_

_}_

⚠ Note: The Recommended Filter List is bound to the stream type of the Sensor it was obtained from. It can only process frames of that type. For example, the list obtained from a depth Sensor can only process depth frames. Passing in other frame types will cause processing failures or return `nullptr`.

**2. Viewing and Adjusting the Recommended List**

**Step 1: View the Recommended Filter List**

_auto filters = sensor->createRecommendedFilters();_

_std::cout << "Recommended Filter List (" << filters.size() << " filters):" << std::endl;_

_for(auto \&filter : filters) {_

_std::cout << " - " << filter->getName()_

_<< " \[" << (filter->isEnabled() ? "enabled" : "disabled") << "]"_

_<< std::endl;_

_}_

**Step 2: View a Filter's Configurable Parameters**

Once you have identified the target Filter, use getConfigSchemaVec() to see which parameters it supports, along with their ranges and default values:

| **Field** | **Description**                           |
| --------- | ----------------------------------------- |
| name      | Parameter name                            |
| type      | Parameter type ("int" / "float" / "bool") |
| min       | Minimum value                             |
| max       | Maximum value                             |
| step      | Step size                                 |
| def       | Default                                   |
| desc      | Description                               |

_// Using TemporalFilter as an example, view its configurable parameters_

_for(auto \&filter : filters) {_

_if(filter->getName() == "TemporalFilter") {_

_for(auto \&item : filter->getConfigSchemaVec()) {_

_std::cout << " " << item.name_

_<< " type=" << item.type_

_<< " range=\[" << item.min << ", " << item.max << "]"_

_<< " step=" << item.step_

_<< " default=" << item.def_

_<< std::endl;_

_}_

_break;_

_}_

_}_

**Step 3: Read Current Parameter Values**

getConfigSchemaVec() returns the static parameter definitions (range, default value), while getConfigValue() returns the actual runtime value currently in effect.

_for(auto \&filter : filters) {_

_if(filter->getName() == "TemporalFilter") {_

_double diffScale = filter->getConfigValue("diff\_scale");_

_double weight = filter->getConfigValue("weight");_

_std::cout << "diff\_scale=" << diffScale_

_<< " weight=" << weight << std::endl;_

_break;_

_}_

_}_

**Step 4: Modify Parameters**

**Method 1: Generic Approach (recommended) — suitable for runtime dynamic adjustment without needing to know the Filter's concrete type:**

_for(auto \&filter : filters) {_

_if(filter->getName() == "TemporalFilter") {_

_filter->setConfigValue("diff\_scale", 0.1);_

_filter->setConfigValue("weight", 0.4);_

_break;_

_}_

_}_

**Method 2: Strongly-Typed Approach — use is() to check the type, as() to cast to the subclass, and call the specific API. IDEs provide autocompletion for this approach.**

_for(auto \&filter : filters) {_

_if(filter->is_[_ob::TemporalFilter_](ob::TemporalFilter)_()) {_

_auto temporalFilter = filter->as_[_ob::TemporalFilter_](ob::TemporalFilter)_();_

_temporalFilter->setDiffScale(0.1f);_

_temporalFilter->setWeight(0.4f);_

_}_

_}_

**Step 5: Enable / Disable a Filter**

_for(auto \&filter : filters) {_

_if(filter->getName() == "TemporalFilter") {_

_filter->enable(false); // Temporarily disable temporal filtering_

_}_

_}_

**Important Notes**

• The default parameter values for each Filter in the recommended list are the SDK's optimal configuration for the currently connected device. Using them directly typically yields good results.

• To restore default values, simply call sensor->createRecommendedFilters() again. The parameters will be reset to the device defaults.

**3. Different Sensors Return Different Lists**

⚠ Note: The Recommended Filter List is bound to the stream type of the Sensor it was obtained from. Filters in the list can only process frames of the matching stream type. Ensure the frame type passed to the Filter matches the Sensor's stream type. See the notes in Section 3.1 for details.

Different Sensor stream types return different Filter lists: the depth Sensor returns depth-specific Filters, and the color Sensor returns color-specific Filters.

_// Depth stream recommended Filters_

_auto depthSensor = device->getSensor(OB\_SENSOR\_DEPTH);_

_auto depthFilters = depthSensor->createRecommendedFilters();_

_// Color stream recommended Filters_

_auto colorSensor = device->getSensor(OB\_SENSOR\_COLOR);_

_auto colorFilters = colorSensor->createRecommendedFilters();_

Different device models may also return different list contents. Always look up Filters by name using filter->getName(), and never hardcode index positions.

/_/ Correct approach: look up by name_

_for(auto \&filter : filters) {_

_if(filter->getName() == "ThresholdFilter") { /_ ... _/ }_

_}_

_// Wrong approach: hardcoded index (order may differ across devices)_

_// auto thresholdFilter = filters\[2]; // Do NOT do this_

If the recommended list is empty, the Sensor's data stream does not support recommended post-processing. Use the raw frames directly.

**4. Comparison and Recommendations**

|                         | **Create Filter Directly**                                        | **Recommended Filter List**                                            |
| ----------------------- | ----------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Ease of Use             | Requires understanding of each Filter's purpose and parameters    | No detail knowledge needed, works out of the box                       |
| Parameter Configuration | Manual setup, fully controllable                                  | Device-optimal defaults, fine-tune as needed                           |
| Device Compatibility    | Must verify whether the current device supports the target Filter | SDK automatically returns only Filters supported by the current device |
| Filter Selection        | Fully independent selection                                       | Determined by SDK based on device model                                |
| Default Parameters      | Must set appropriate values manually                              | Already the optimal configuration for the current device               |
| Typical Scenarios       | Product customization, algorithm tuning                           | Quick integration, general-purpose demos                               |

**Recommendations**

• If you are a first-time user or just want to see results quickly, use the Recommended Filter List. It takes only a few lines of code to get started.

• If you need to select a specific Filter combination or have precise parameter requirements, use Create Filter Directly.

• The two approaches can be combined: first use the recommended list to learn which Filters your device supports, then create them directly for fine-grained parameter tuning.

### Optional Depth Preset Update (Gemini 330 Series)

#### **1. Purpose**

The Gemini 330 has been updated to support depth preset updates. Since the camera has limited storage for built-in Presets, we provide three optional depth preset updates. Users can download the appropriate Preset from the [Depth Preset Release](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Preset%20Release%20\(Gemini%20330%20Series\)) page provided by Orbbec based on their specific application scenarios and update it to the camera for better depth performance in corresponding scenarios.

#### **2. Scope**

Applies to all Gemini 330 products with firmware version 1.4.60 or later, and requires SDK version 2.3.x or later.

#### **3. How to Update Presets**

**3.1 How to Update Presets via Orbbec Viewer**

1. After connecting the camera to Orbbec Viewer, click on Device Control, then click the Update button under Optional Depth Preset. Select the preset file you wish to update.

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/1M8eEXDMfF7YIDccrEVS/assets/b30fad7108301ed37aeb.webp)

Successful Update: The updated presets will then be displayed in the optional depth preset list.

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/GeX4RAzWaG0a4BaWiPz1/assets/4a01f0585872a06bf821.webp)

2. The Optional Depth Preset supports a maximum of three presets at a time. Each update will overwrite the previous optional depth presets.
3. Error Handling:

* If a duplicate preset is imported, a prompt will indicate that a duplicate configuration exists, and only one instance will be applied.

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zgucgPyE8CYEZCTcO3gh/assets/ee6d19de8a466008f330.webp)

* If the firmware version is unsupported or the imported preset does not match the device, the following error message will appear: "Error! The preset data doesn’t match the device! Please select again."

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ZAftJo52G4Bh10uy7Bwo/assets/4945d7ebd3cc65d61185.webp)

**3.2 How to Update Presets via SDK**

Refer to the sample code: [GitHub Sample Link](https://github.com/orbbec/OrbbecSDK_v2/blob/main/examples/2.device.optional_depth_presets_update/device.optional_depth_presets_update.cpp)

### Update Firmware (Gemini 330 Series)

#### **1. Device Firmware Mode Introduction**

The Gemini 330 series cameras have two modes. The first is normal mode, where the camera operates normally. The second is recovery mode, where the camera cannot function but can only perform a firmware update. By default, the device will enter normal mode. It will only enter recovery mode when it is unable to enter normal mode.

**1.1 How to Identify the Device Mode**

**1.1.1 Windows System**

In normal mode, the device manager displays the device as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/l3oHN8iYCsmrJwY5eSxo/assets/34fd863689aa1af67dba.webp)

In normal mode, the device is displayed as follows when connected to Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/gHOxfTVuqRdYYykvBaeG/assets/6ed2d98c1e666ce1eaec.webp)

In recovery mode, the device manager displays the device as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kRhUBUFUv1DKMfUPlzz0/assets/65b82000fedb230dc128.webp)

In recovery mode, the device is displayed as follows when connected to Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/QRlYkcgkNlN8sJnHT6pv/assets/30991058c4e39c9a9756.webp)

**1.1.2 Ubuntu System**

In normal mode, the device information is displayed as follows when using the `**lsusb**` command:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/r1y69BOWHwd4VRabvQXL/assets/6de4cfe9a9dd30481e0a.webp)

In normal mode, the device is displayed as follows when connected to the Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/s1mLkUJhxbAUntGHGJvX/assets/c843871ebfb35126b774.gif)

In recovery mode, the device information is displayed as follows when using the `**lsusb**` command:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/SDred2i07fZzPE8Xu4DL/assets/142846ffdcf6b4a8f981.gif)

In recovery mode, the device is displayed as follows when connected to the Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7ld4ArWD3qv1QIeyDYhJ/assets/3a33e8140d2ab77538f0.gif)

**1.2 Notes**

* Ensure the device has a stable power supply and stable communication during the update process.
* The camera firmware includes ISP firmware. ISP firmware will not be updated in recovery mode; it needs to be updated again after entering normal mode.
* If any failure occurs during the update process, you can repeat the update until it is successful.

#### **2. Update Firmware**

**2.1 Online Update via Orbbec Viewer**

1. Open Orbbec Viewer. If firmware updates are available, a notification will appear in the top right corner of the screen, indicating that new firmware is available for update.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ym8Np944ihzmg1FWrzmi/assets/b0732cc01bec4292b191.gif)

2. Click the notification in the red box as shown above, and the following dialog box will appear.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/i0lxCWwvlT8KOnccOUFi/assets/d26b259954a012271cc0.gif)

3. Select "New Firmware Upgrade".

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/uYS5fzK2yXGta7snCkkl/assets/e000b5a73dbbd673710c.gif)

4. Click "Upgrade," and the following dialog box will appear.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ehwG36aZr8kT6jX9i3Ar/assets/6ea432c798f62de8edd0.gif)

5. Click "Yes."

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/6JyuSJuyNEypLmNmGUko/assets/d9f1d04a769799a4ebd9.gif)

6. Reboot the device.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/HbCGZjdIGENnI5UWAEPj/assets/aabcaeb0286802fa0db2.gif)

7. Confirm the firmware version number after the update.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/H4PzqfgaCo9jqx6Gi2go/assets/aa81b9070f5c066e7c10.gif)

**Notes:**

If the update process fails, you can repeat the update until it is successful.

**2.2 Offline Update via Orbbec Viewer**

The difference between offline and online updates is as follows: With online updates, the firmware is automatically downloaded from the server (downloaded to the "output/firmwareFile" directory in Orbbec Viewer), and then the device is updated. However, with offline updates, you manually select the firmware path and then proceed with the update. The interface is as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/WoPkNwzTj8GDAmuiunx2/assets/067fc37f8cc08ccbed88.gif)

After clicking "Upgrade," the subsequent update steps are the same as the online update.

**2.3 Code Sample**

1. The firmware update reference for Orbbec SDK V1.x.x version is available in the sample at the following link: [https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade](https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade)2. The firmware update reference for Orbbec SDK V2.x.x version is available in the sample at the following link: [https://github.com/orbbec/OrbbecSDK\_v2/tree/main/examples/2.device.firmware\_update](https://github.com/orbbec/OrbbecSDK_v2/tree/main/examples/2.device.firmware_update)

#### **3. Handle Update Exception**

If there is a power failure or the USB cable is unplugged during the online update process, the device may enter Recovery mode. In this case, you will need to perform an offline update using the firmware downloaded online. The path to the online firmware download is in the "output/firmwareFile" directory of Orbbec Viewer, for example, on the Windows platform, as shown in the following figure.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/6vfdWFpC9904eU2mxvvp/assets/5072435cdcd691142459.gif)

If the device enters Recovery mode but there is no firmware available, please download the firmware from the product’s firmware download page first. Then, follow the offline update method to perform the update.

**Notes: (Very Important)**

In Recovery mode, ISP firmware update is not supported. You need to enter Normal mode and perform the firmware update again to ensure ISP firmware matches the current system. (In Recovery mode, firmware needs to be updated twice.)

#### **4. Update Orbbec Viewer**

If there is a new version of Orbbec Viewer available for update, when opening Orbbec Viewer, there will be a prompt in the top right corner: "A new version of the tool can be updated." Click on this prompt, and it will link to the download directory of Orbbec Viewer on GitHub. Please download the corresponding platform’s Orbbec Viewer.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nQpTKlOhqKsxQXGhrz8D/assets/170acd9ee68d647fee12.gif)

**Notes:**

Each firmware has a corresponding minimum version number of supported Orbbec Viewer. If the current Orbbec Viewer version is too low, you need to update Orbbec Viewer first to detect the prompt for the latest firmware update.

### Gemini 330 Series Supported Hosts and System Requirements (USB)

#### **1. Recommended Host Platforms**

**Recommended configuration for hosts in x86/x64 architecture:**

* Operating systems: Windows 10/11, Ubuntu 18.04/20.04/22.04
* Data Interface: USB 3.0 / USB 2.0
* Processor: Quad-core, 2.9GHz and above
* RAM: 8GB and above

**Recommended configuration for ARM-based hosts**

* Operating systems: Ubuntu 18.04/20.04/22.04
* Data Interface: USB 3.0 or USB 2.0
* Processors: Quad-core Cortex-A72 and above
* RAM: 4GB and above

#### **2. System Requirements**

| **Operating system** | **Requirement**                                                                              | **Description**                                                                                                           |
| -------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Windows 10/11        | – Windows 10 April 2018 (version 1803, operating system build 17134) release (x64) or higher | The generation of the VS project depends on the installed VS version and cmake version, and supports VS2015/VS2017/VS2019 |
| Linux Ubuntu         | 18.04/20.04/22.04                                                                            | Support GCC 7.5                                                                                                           |
| Ubuntu Arm           | 18.04/20.04/22.04                                                                            | Support GCC 7.5                                                                                                           |

#### **3. Tested PC Host Platforms**

| **Platform**  | **System** |                  |                  |                  |            |
| ------------- | ---------- | ---------------- | ---------------- | ---------------- | ---------- |
| **Win10**     | **Win11**  | **Ubuntu 18.04** | **Ubuntu 20.04** | **Ubuntu 22.04** |            |
| **Intel NUC** | PASS       | PASS             | Not tested       | PASS             | Not tested |
| **x64 PC**    | PASS       | PASS             | PASS             | PASS             | PASS       |

#### **4. Tested ARM Host Platforms**

| **ARM Platform**         | **Software Version**                                                                                                          | **Test Result** |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------- | --------------- |
| NVIDIA Jetson Orin Nano  | Last Tested on JetPack5.1.1-b56                                                                                               | PASS            |
| NVIDIA Jetson Orin NX    | Last Tested on JetPack5.1.1-b56                                                                                               | PASS            |
| NVIDIA Jetson AGX Orin   | Last Tested on JetPack6.0                                                                                                     | PASS            |
| NVIDIA Jetson Nano       | Last Tested on JetPack4.6.1-b110                                                                                              | PASS            |
| NVIDIA Jetson AGX Xavier | Last Tested on JetPack5.0.2-b231                                                                                              | PASS            |
| NVIDIA Jetson Xavier NX  | Last Tested on JetPack4.6.1-b110                                                                                              | PASS            |
| Qualcomm RB5             | Last Tested on Qualcomm\_Linux.SPF.5.4.219                                                                                    | PASS            |
| Raspberry Pi 4B          | Last Tested on Ubuntu 20.04                                                                                                   | PASS            |
| Raspberry Pi 5           | Last Tested on [Debian](https://www.raspberrypi.com/news/bookworm-the-new-version-of-raspberry-pi-os/)GNU/Linux 12 (bookworm) | PASS            |

### Gemini 330 Series Supported Hosts and System Requirements (GMSL)

The GMSL Series cameras are the latest GMSL2 stereo camera launched by Orbbec. To preview variable data streams and apply them in business development, the camera should be connected to a host that supports GMSL2 to MIPI CSI-2 deserialization functionality, such as the NVIDIA Jetson ecosystem equipped with a GMSL camera board. The Gemini 335Lg has been officially adapted by Orbbec and ecosystem partners, ensuring its compatibility with a wide range of host solutions, such as developer kit, turnkey system, and modular stacks.

For the convenience of users in quick testing and development, Orbbec provides precompiled GMSL drivers for the NVIDIA Jetson AGX Orin developer kit solution in the official Github repository. For compatibility with other solutions such as turnkey system and modular stacks, you can contact our partners for support.

Three types of solutions are supported: developer kit, turnkey system, and modular stacks.

| **Category**                                                     | **Supported Hardware**                 | **Hardware Platform**   |                            |                         |                     |                         |
| ---------------------------------------------------------------- | -------------------------------------- | ----------------------- | -------------------------- | ----------------------- | ------------------- | ----------------------- |
| **Developer Kit + GMSL2 Camera Broad**                           | NVIDIA Jetson AGX Orin Developer Kit   | +                       | FG96-8CH-V2                | NVIDIA Jetson AGX Orin™ |                     |                         |
| **Turnkey System**                                               | ADVANTECH MIC-733-AO                   | NVIDIA Jetson AGX Orin™ |                            |                         |                     |                         |
| Connect Tech Inc. Anvil Embedded System                          | NVIDIA Jetson AGX Orin™                |                         |                            |                         |                     |                         |
| Axiomtek AIE510-ONX                                              | NVIDIA Jetson Orin™ NX                 |                         |                            |                         |                     |                         |
| Seeed Studio reComputer Robotics J5012/J5011 with GMSL Extension | NVIDIA Jetson AGX Orin™                |                         |                            |                         |                     |                         |
| Seeed Studio reComputer Robotics J4012 with GMSL Extension       | NVIDIA Jetson Orin™ NX                 |                         |                            |                         |                     |                         |
| Seeed Studio reComputer Robotics J3011 with GMSL Extension       | NVIDIA Jetson Orin™ Nano Super         |                         |                            |                         |                     |                         |
| ADVANTECH MIC-742-AT                                             | NVIDIA®Jetson Thor™                    |                         |                            |                         |                     |                         |
| **Modular Stacks (Carrier Board + SOM + GMSL Camera Board)**     | Connect Tech Inc. Forge Carrier AGX201 | +                       | NVIDIA Jetson AGX Orin SOM | +                       | Connect Tech JCB002 | NVIDIA Jetson AGX Orin™ |
| Connect Tech Inc. Rogue Carrier AGX202                           | NVIDIA Jetson AGX Orin SOM             | Connect Tech JCB002     | NVIDIA Jetson AGX Orin™    |                         |                     |                         |
| Connect Tech Inc. Rogue-RX Carrier AGX203                        | NVIDIA Jetson AGX Orin SOM             | Connect Tech JCB002     | NVIDIA Jetson AGX Orin™    |                         |                     |                         |
| Seeed Studio reComputer Mini J501                                | NVIDIA Jetson AGX Orin SOM             | GMSL Board              | NVIDIA Jetson AGX Orin™    |                         |                     |                         |
| AVerMedia D331                                                   | NVIDIA Jetson Thor SOM                 | AVerMedia GMSL Board    | NVIDIA Jetson Thor™        |                         |                     |                         |

Driver version support status:

| Driver version   | Cameras Supported                                  | Precompiled Driver                                                           |
| ---------------- | -------------------------------------------------- | ---------------------------------------------------------------------------- |
| Basic Version    | Gemini 335Lg,Gemini 338Lg                          | [Orbbec repositories](https://github.com/orbbec/MIPI_Camera_Platform_Driver) |
| V1.2.10 or above | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg             |                                                                              |
| V1.2.12 or above | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g |                                                                              |

#### **1. Developer Kit Solution**

**1.1 NVIDIA Jetson AGX Orin Developer Kit**

The NVIDIA Jetson AGX Orin developer kit comes with a computing power of 275TOPS, 64GB of RAM, and a 120-pin 16-lane MIPI connector. To connect the Gemini 335Lg to this developer kit, a compatible GMSL camera board is required. Please refer to the below information:| **Components** | - 1 x [NVIDIA Jetson AGX Orin Developer Kit](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/)& Compatible Power Supply\
\- 1 x GMSL Series camera EVK (including 1 x GMSL2 camera GMSL Series camera, 1 x GMSL camera board, 1 x power conversion cable)\
\- 1 x Compatible Power Supply for GMSL Camera Board\
\- It is also possible to connect additional Gemini 335Lg cameras. | | --- | --- | | **Connection Diagram** | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/XVcQwybFXj6LK3iiaUbx/assets/9134296b741a323ba559.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-11/image.png) | | **Hardware Platform** | NVIDIA Jetson AGX Orin™ | | **JetPack Version** | 6.0/6.2/7.2 | | **Maximum Number of\*\*\*\*GMSL Series cameras**\
**Supported** | 8 | | **Precompiled Driver** | [Orbbec repositories](https://github.com/orbbec/MIPI_Camera_Platform_Driver) |

#### **2. Turnkey Systems Solution**

**2.1 ADVANTECH Turnkey System**

The GMSL series cameras have been adapted to the MIC-742-AT standalone Turnkey system launched by advanced intelligent device manufacturer Advantech Technology Co., Ltd., which is a fanless ultra compact AI Inference System system based on NVIDIA®Jetson Thor™. Unlike the development kit, the standalone machine comes with a deserter board that supports direct integration with GMSL cameras. For detailed information, please consult Advantech. The specific adaptation of this scheme is shown in the table below:

| **Components**                                      | <p>- 1 x <a href="https://www.advantech.com/en/products/965e4edb-fb98-429e-89ed-9a0a8435a7be/mic-742%E2%80%8B/mod_79762a8d-c514-4c3f-b391-7f56a995b758">MIC-742-AT</a> &#x26; Compatible Power Supply<br>- 1 x - 8 x GMSL Series cameras<br>- 1 x - 8 x Power Conversion Cables</p> |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Connection Diagram**                              | ![Official Orbbec figure from Gemini 330 Series Supported Hosts and System Requirements (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/VvnPPq6XzsrOw987SJIJ/assets/38428efa71a835fc4703.webp)                                                               |
| **Hardware Platform**                               | NVIDIA®Jetson Thor™                                                                                                                                                                                                                                                                 |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                  |
| **Maximum Number of GMSL Series cameras Supported** | 8                                                                                                                                                                                                                                                                                   |
| **Driver Support**                                  | Please contact [Advantech](https://www.advantech.com/en-us)                                                                                                                                                                                                                         |

**2.2 ADVANTECH Turnkey System**

The Gemini 335Lg is also compatible with the ADVANTECH MIC-733-AO turnkey system, a fanless ultra-compact edge AI system for AMR & robotics. Unlike the developer kit, the turnkey system comes with a built-in GMSL camera board, which allows direct GMSL camera connection. In the MIC-733 series, there is a dedicated SKU that supports Gemini 335Lg out of the box, while other models in the MIC-733 series require manual driver installation. For more information, please contact Advantech. The compatibility details are as follows:

| **Components**                                      | <p>- 1 x <a href="https://www.advantech.com/en-us/products/9140b94e-bcfa-4aa4-8df2-1145026ad613/mic-733/mod_09861425-4950-46ab-ad39-1b5522881218">MIC-733-AO</a> &#x26; Compatible Power Supply<br>- 1 x - 4 x GMSL Series cameras<br>- 1 x - 4 x Power Conversion Cables</p> |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Connection Diagram**                              | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/CzVXIJonqtz0HHg4IWiE/assets/97ef96c2f6abc7a02d0e.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-10/image.png)                                                                         |
| **Hardware Platform**                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                       |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                            |
| **Maximum Number of GMSL Series cameras Supported** | 4                                                                                                                                                                                                                                                                             |
| **Driver Support**                                  | Please contact [Advantech](https://www.advantech.com/en-us)                                                                                                                                                                                                                   |

**2.3 Connect Tech Inc. Turnkey System**

Connect Tech Anvil Embedded System comes ready to withstand even the most compute-intensive AI applications with its power-efficient and feature-rich design. It supports up to eight GMSL2 camera inputs, and provides native support for Gemini 335Lg. This joint solution can significantly reduce your overall application development time. The compatibility details are as follows:

| **Components**                                      | <p>- 1 x <a href="https://connecttech.com/product/anvil-embedded-system-with-nvidia-jetson-agx-orin/">Anvil Embedded System</a>&#x26; Compatible Power Supply<br>- 1 x - 8 x GMSL Series cameras<br>- 1 x - 8 x Power Conversion Cables</p> |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Compatible Device Image**                         | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JM82GgBKBJuSrhfGZfDP/assets/65f4abadd6c2e9b4315a.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-10/pklimage.png)                                    |
| **Hardware Platform**                               | NVIDIA Jetson AGX Orin™ & AGX Orin™ Industrial                                                                                                                                                                                              |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                          |
| **Maximum Number of GMSL Series cameras Supported** | 8                                                                                                                                                                                                                                           |
| **Driver Support**                                  | Please contact [Connect Tech Inc.](https://connecttech.com/)                                                                                                                                                                                |

**2.4 Axiomtek Turnkey System**

Powered by the NVIDIA Jetson Orin NX 16GB module, the AIE510-ONX is a compact, rugged embedded system engineered for edge AI applications. Specifically, the AIE510-ONX-GMSL integrates 4 Fakra-Z connector for GMSL2 connection, ensuring seamless compatibility with Gemini 335Lg. The whole solution is ideal for high-precision robotics and autonomous mobile robot (AMR) deployments. The compatibility details are as follows:

| **Components**                                      | <p>- 1 x <a href="https://us.axiomtek.com/Default.aspx?MenuId=Products&#x26;FunctionId=ProductView&#x26;ItemId=27341&#x26;C=AIE510-ONX&#x26;upcat=350">AIE510-ONX</a> &#x26; Compatible Power Supply<br>- 1 x - 4 x GMSL Series cameras<br>- 1 x - 4 x Power Conversion Cables</p> |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Compatible Device Image**                         | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/OVYuAWgiJYRB9l8SkTsA/assets/f2ca3973ac26d594a459.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-10/UCZimage.png)                                                                           |
| **Hardware Platform**                               | NVIDIA Jetson Orin™ NX                                                                                                                                                                                                                                                             |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                 |
| **Maximum Number of GMSL Series cameras Supported** | 4                                                                                                                                                                                                                                                                                  |
| **Driver Support**                                  | Please contact [Axiomtek](https://www.axiomtek.com/)                                                                                                                                                                                                                               |

**2.5 Seed Studio Turnkey System**

Seeed Studio delivers the industry's most comprehensive range of turnkey edge AI systems supporting Gemini 335Lg. Spanning the full NVIDIA Jetson Orin portfolio—from the high-performance AGX Orin to the compact Orin Nano Super—the reComputer series provides flexible deployment options tailored to diverse performance requirements and form factor constraints. Each platform features native GMSL2 connectivity through dedicated extension boards, enabling seamless multi-camera integration for robotics and autonomous mobile robot(AMR) applications.

Supported Platforms:

**2.5.1 NVIDIA Jetson AGX Orin™ Platform**

| **Components**                                      | <p>- 1 x <a href="https://www.seeedstudio.com/reComputer-Robotics-J5011-with-GMSL-extension-board-p-6681.html">reComputer Robotics J5011 with GMSL</a>/<a href="https://www.seeedstudio.com/reComputer-Robotics-J5012-with-GMSL-extension-board-p-6682.html">reComputer Robotics J5012 with GMSL</a> &#x26; Compatible Power Supply<br>- 1 x - 8 x GMSL Series cameras<br>- 1 x - 8 x Power Conversion Cables</p> |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Compatible Device Image**                         | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yPN1PXY3LUoBnzQl4h3H/assets/02e72c1f90481dd7c93e.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/image.png)                                                                                                                                                                                                             |
| **Hardware Platform**                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                                                                                                                                                           |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                                                                                                                                                |
| **Maximum Number of GMSL Series cameras Supported** | 8                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **Driver Support**                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                                                                                                                                                                                                       |

**2.5.2 NVIDIA Jetson Orin™ NX Platform**

| **Components**                                      | <p>- 1 x <a href="https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html">reComputer Robotics J4012 with GMSL Extension</a> &#x26; Compatible Power Supply<br>- 1 x - 4 x GMSL Series cameras<br>- 1 x - 4 x Power Conversion Cables</p> |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Compatible Device Image**                         | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7lLoxwpVVR7e4iRkPt9e/assets/8f0abcd812d37c4c1cbc.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/vG1image.png)                                                                      |
| **Hardware Platform**                               | NVIDIA Jetson Orin™ NX                                                                                                                                                                                                                                                        |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                            |
| **Maximum Number of GMSL Series cameras Supported** | 4                                                                                                                                                                                                                                                                             |
| **Driver Support**                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                                                                   |

**2.5.3 NVIDIA Jetson Orin™ Nano Super Platform**

| **Components**                                      | <p>- 1 x <a href="https://www.seeedstudio.com/reComputer-Robotics-J3011-with-GMSL-extension-board-p-6538.html">reComputer Robotics J3011 with GMSL Extension</a> &#x26; Compatible Power Supply<br>- 1 x - 4 x GMSL Series cameras<br>- 1 x - 4 x Power Conversion Cables</p> |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Compatible Device Image**                         | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/lUbkb3rSFY9cmrEGdGXc/assets/d410a29d06de80f0f185.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/JW6image.png)                                                                      |
| **Hardware Platform**                               | NVIDIA Jetson Orin™ Nano Super                                                                                                                                                                                                                                                |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                            |
| **Maximum Number of GMSL Series cameras Supported** | 4                                                                                                                                                                                                                                                                             |
| **Driver Support**                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                                                                   |

#### **3. Modular Stacks**

The NVIDIA Jetson modules are essentially system on Modules (SOMs) that require compatible carrier boards for operation. A NVIDIA Jetson developer kit is essentially a combination of a SOM and a carrier board. Orbbec provides adaptation solutions for such cases, with the following details:

**3.1 Connect Tech Inc Modular Stacks Solution**

| **Components**                                      | <p>- 1x NVIDIA Jetson AGX Orin SOM &#x26; Compatible Power Supply<br>- 1x Carrier Board<br>- 1x - 8x GMSL Series cameras<br>- 1x GMSL Camera Board &#x26; Compatible Power Supply<br>- 1x - 8x Power Conversion Cables</p>                                                                                                                                                                                                  |
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Supported GMSL Camera Board**                     | [Connect Tech JCB002](https://connecttech.com/product/xavier-gmsl-camera-platform/)                                                                                                                                                                                                                                                                                                                                         |
| **Supported Carrier Board**                         | <p>- <a href="https://connecttech.com/product/forge-carrier-for-nvidia-jetson-agx-orin/">Connect Tech Inc. Forge Carrier AGX201</a><br>- <a href="https://connecttech.com/product/rogue-carrier-for-nvidia-jetson-agx-orin/">Connect Tech Inc. Rogue Carrier AGX202</a><br>- <a href="https://connecttech.com/product/rogue-rx-carrier-board-for-nvidia-jetson-agx-orin/">Connect Tech Inc. Rogue-RX Carrier AGX203</a></p> |
| **Connection Diagram**                              | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/a06gGuAQtBL3tjno0evF/assets/7f69d1a0f66e89e23d9f.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-10/3iVimage.png)                                                                                                                                                                                                                    |
| **Hardware Platform**                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                                                                                                                                                                     |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                                                                                                                                                          |
| **Maximum Number of GMSL Series cameras Supported** | 8                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **Driver Support**                                  | Please contact [Connect Tech Inc.](https://connecttech.com/)                                                                                                                                                                                                                                                                                                                                                                |

**3.2 Seeed Studio Modular Stacks Solution**

| **Components**                                      | <p>- 1x NVIDIA Jetson AGX Orin SOM &#x26; Compatible Power Supply<br>- 1x Carrier Board<br>- 1x - 8x GMSL Series cameras<br>- 1x GMSL Camera Board &#x26; Compatible Power Supply<br>- 1x - 8x Power Conversion Cables</p> |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Supported GMSL Camera Board**                     | - [reComputer Mini J501 Carrier Board for Jetson AGX Orin™ with GMSL Extension](https://www.seeedstudio.com/reComputer-Mini-J501-Carrier-Board-for-Jetson-AGX-Orin-p-6606.html)                                            |
| **Supported Carrier Board**                         |                                                                                                                                                                                                                            |
| **Connection Diagram**                              | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zbjsQB39fGQ2DxNNj7Bf/assets/8d11a436d8044b84e64e.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/j90image.png)                   |
| **Hardware Platform**                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                    |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                         |
| **Maximum Number of GMSL Series cameras Supported** | 8                                                                                                                                                                                                                          |
| **Driver Support**                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                |

**3.3 AVerMedia Modular Stacks Solution**

| **Components**                                      | <p>- 1x NVIDIA Jetson Thor SOM &#x26; Compatible Power Supply<br>- 1x Carrier Board<br>- 1x - 8x GMSL Series cameras<br>- 1x GMSL Camera Board &#x26; Compatible Power Supply<br>- 1x - 8x Power Conversion Cables</p> |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Supported GMSL Camera Board**                     | - [GMSL Board](https://professional.avermedia.com/product-detail/GMSL-Board)                                                                                                                                           |
| **Supported Carrier Board**                         | - [AVerMedia D331](https://professional.avermedia.com/product-detail/D331)                                                                                                                                             |
| **Connection Diagram**                              | [![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/S2ndwUAWGX51NSuc15il/assets/337a161ae4e8293bc569.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/Jmwimage.png)               |
| **Hardware Platform**                               | NVIDIA Jetson Thor™                                                                                                                                                                                                    |
| **Verify camera models**                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                     |
| **Maximum Number of GMSL Series cameras Supported** | 8                                                                                                                                                                                                                      |
| **Driver Support**                                  | Please contact [AVerMedia](https://professional.avermedia.com/)                                                                                                                                                        |

### Reference Design - Mounting (Gemini 330 Series)

#### **1. Overview**

This document provides the optimal reference mounting design solution for the camera, assisting customers in swiftly implementing it during the product deployment process.

#### **2. Mounting Reference Solution for Gemini 335/336**

**2.1 Product Components**

| Gemini 335                                                                                                                                                                                           | Gemini 336                                                                                                                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kX8Z2XtNFR6oJcDefkgn/assets/e0ff30687b421fa169a2.webp) | ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oC6Yu6fdFyQqsCkK5TE8/assets/9689e5f465e1745d4987.webp) |

**2.2 Product Drawing for Gemini 335**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/POt38CnGMw1SPM8TjOmO/assets/69dec62e40205e9c31a9.webp)

**2.3 Product Drawing for Gemini 336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7Fm4NIPtyh9KJRR7UqIK/assets/0078e07fa5e71c70dd09.webp)

**2.4 Product Interfaces for Gemini 335/336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EAudRIAr3nVVGxM5Huok/assets/ffd8c769cb1b8957cbca.webp)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the left of the camera,the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port On the right side of the camera, rotate the Sync Port cover to see the Sync Port.

**2.5 Mounting and Fixing Method for Gemini 335/336:**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 5mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EQNIkv5F7DMc11r2TIFO/assets/78d35886673757cbbd53.webp)

Option B\*\*:\*\*Fix the 3D camera using two M3 thread holes on the rear side,the hole depth is 3.0mm and commended is 0.4Nm

Option C: Fix the 3D Camera using the shape or edges of the metal housing

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kpAIKbtxct8gKv7RCFcU/assets/82a8e185499c9f91c1ce.webp)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, the FOV viewing angle cannot be blocked;

#### **3. Mounting Reference Solution for Gemini 335L/336L**

**3.1 Product Components**

| Gemini 335L                                                                                                                                                                                          | Gemini 336L                                                                                                                                                                                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/eQttTPsHUSTzzVMKg9FJ/assets/45a22d6f0657c8faad1f.webp) | ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IcHs3Fsfcxp219HV2OtH/assets/9891dabfe4091cc73fba.webp) |

**3.2 Product Drawing for Gemini 335L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yuTyaeJu2tgace0gEr5A/assets/f3d9e4e31f24bad06274.webp)

**3.3 Product Drawing for Gemini 336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jXlTlDyuN1XVC1jaQyHJ/assets/7fcbd9d0555158e4bb3d.webp)

**3.4 Procuct Interface for Gemini 335L/336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/toR5m59vm9kPDfDSxzt6/assets/c7b15528e6c5eb8c7c9e.webp)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the bottom of the camera,the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. a length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. a length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port at the top side of the camera, remove the Sync Port protective cover to see the Sync Port.

**3.5 Mounting and Fixing Method for Gemini 335L/336L**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 8mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qHU8RuPa7GiPfxbthtIs/assets/38fd813299e17e6bf6bc.webp)

Option B\*\*:\*\*Fix the 3D camera using two M4 thread holes on the rear side,the hole depth is 3.0mm and commended is 0.4Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/xbiv3YSXvnzp9J2rUYv9/assets/2d0998911b101b8ee40b.webp)

Option C: Fix the 3D Camera using the shape or edges of the metal housing

Illustration for 3D camera mounting

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qSoJ7oDnNFClhwkUpTEX/assets/c15c8dc7c14c5473794a.webp)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, it cannot block the FOV perspective;

#### **4. System Design Requirements**

1. Sealing Requirements - Use foam padding or silicone seals between the 3D camera and the customer’s device to prevent dust.
2. Lens Requirements - No additional lenses or covers can be added to the front of the 3D camera.
3. Cooling Requirements - Connect the 3D camera to external metal components using thermal conductive materials to expand the cooling area. It is recommended to incorporate active cooling with fans.

* The 3D cameras must not be heated by other heat sources.

4. Before customer tooling, please provide structural drawings related to the 3D camera for orbbec’s ME review.

-The next step

### Reference Design - Thermal (Gemini 330 Series)

#### **1. Overview**

This document provides the optimal reference thermal design solution for the camera, assisting customers in quickly implementing effective cooling strategies during product development and deployment.

#### **2. Thermal Reference Solution for Gemini 335/336**

1. Active Cooling: It is recommended to use fans for active cooling.\
   Operating temperature ranges: - LDM module: < 70°C (The overall laser energy is reduced by 50% at 70 °C and the laser is completely shut down at 73 °C to prevent potential overheating of the laser device, while still maintaining adequate performance for most use cases.)

* IR module: < 68°C
* RGB module: < 68°C
* CPU: < 85°C

2. Passive cooling: - Apply graphite thermal pads on the side. It is recommended to use graphite thermal pads with specifications of 500W or higher.

![Official Orbbec figure from Reference Design - Thermal (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/xkmFt7nhW5X4FF9zhHf4/assets/4860a048a021459f0945.webp)

*
  * It is recommended to create ventilation holes on the outer casing to enhance cooling. The most effective directions for creating holes are vertically (top and bottom). If holes cannot be placed on the top, consider placing them horizontally (left and right) and on the bottom for improved airflow.

![Official Orbbec figure from Reference Design - Thermal (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/FDJoOEQbjk3F9Qg8gnAK/assets/39d2b954ae789d28ccc4.webp)

–

#### **3. Thermal Reference Solution for Gemini 335L/336L**

1. Active Cooling: It is recommended to use fans for active cooling.\
   Operating temperature ranges: - LDM module: < 70°C (The overall laser energy is reduced by 50% at 70 °C and the laser is completely shut down at 73 °C to prevent potential overheating of the laser device, while still maintaining adequate performance for most use cases.)

* IR module: < 68°C
* RGB module: < 68°C
* CPU: < 85°C

2. Passive cooling:

a. Apply graphite thermal pads on the side. It is recommended to use graphite thermal pads with specifications of 500W or higher.

![Official Orbbec figure from Reference Design - Thermal (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/9r2LuFUVSjpVnE9B4aRy/assets/d962845a7f540a61f13c.webp)

b. It is recommended to create ventilation holes on the casing to enhance cooling. The most effective directions for these holes are vertically (top and bottom). If holes cannot be placed on the top, consider placing them horizontally (left and right) and on the bottom for improved airflow.

#### **4. System Design Requirements**

1. Sealing Requirements - Use foam padding or silicone seals between the 3D camera and the customer’s device to prevent dust.
2. Lens Requirements - No additional lenses or covers can be added to the front of the 3D camera.
3. Cooling Requirements - Connect the 3D camera to external metal components using thermal conductive materials to expand the cooling area. It is recommended to incorporate active cooling with fans.

* The 3D cameras must not be heated by other heat sources.

4. Before customer tooling, please provide structural drawings related to the 3D camera for orbbec’s ME review.

### Reference Design - Power Delivery (Gemini 330 Series)

**I. Power Capability and Bandwidth Requirements of USB Ports:**\
Both Gemini 335 and Gemini 335L require the USB ports on the customer’s motherboard to support a data bandwidth of USB 3.0 (5Gbps), and the power supply capability of the USB ports should support 5V/1.5A or higher.

**II. Solutions for Insufficient Power Supply Capability of USB Ports:**\
If the customer’s motherboard USB 3.0 port can only support up to 0.9A, there are two solutions available:

#### **1. Solution A**

Without hardware modifications, it is necessary to adjust the laser power level. For Gemini 335, the laser power level needs to be adjusted from 6 (default value) to 4, and press the Refresh button to refresh the laser power level, ensuring that the peak current of Gemini 335 does not exceed 0.9A, as shown in Figure 1.

Gemini 335L, adjust the laser power level from 6 (default value) to 5, and press the Refresh button to refresh the laser power level, ensuring that the peak current of Gemini 335L does not exceed 0.9A, as shown in Figure 2.

![Official Orbbec figure from Reference Design - Power Delivery (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UAcMal7BqcugDebxgseM/assets/e540c32eedce6cab875f.webp)

Figure 1. Adjust the laser power level for Gemini 335

![Official Orbbec figure from Reference Design - Power Delivery (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JBc00Dt34NOQofmyINLV/assets/bc7e4c2783f656c26b72.webp)

Figure 2. Adjust the laser power level for Gemini 335L

Note:\
Decreased laser energy levels in Gemini 335/335L may reduce the depth quality in certain scenarios. To address this issue, customers need adapt the configuration according to the unique requirements of their particular application.

1. Gemimi 335/335L is capable to work in both active and passive modes, thus reduction of laser energy level has no effect on the depth effect of outdoors performance where the passive mode dominates. But it reduces the depth integrity and depth accuracy for some indoor scenes, such as low-reverse non-textured scenes or long-distance non-textured objects.
2. Energy level reduction affects moving objects in indoor dark light environment. It takes longer exposure time to obtain better depth quality after energy level reduction, resulting in the motion blur.

#### **2. Solution B**

If reducing intensity of the laser power is undesirable, an additional switching board can be used, powered by an external adapter providing 5V/1.5A. The 5V/1.5A power supply is routed through the DC-IN interface to the USB Power Switch SY6874DBC chip’s power input on the adapter board. The VBUS signal from the motherboard’s USB port only controls the SY6874DBC’s EN enable pin, thereby managing the 5V power delivery to the USB A Female port. The power is then delivered to the Gemini 335 or Gemini 335L through a USB 3.0 cable, fulfilling the power requirements for the Gemini series, as illustrated in Figure 3.

![Official Orbbec figure from Reference Design - Power Delivery (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5ZqtHDvYgBA8fOlP31WW/assets/5e97a6a1c33f848250e5.webp)

Figure 3. Using an additional switching board to power Gemini series

### Reference Design - Cable (USB) (Gemini 330 Series)

We provide standard 1m length USB3.0 wire. If the length cannot meet the requirements, customers can make their own wires according to the following wire requirements or find a third-party supplier to provide wires that meet the specification requirements. The following are some basic requirements of USB3.0 wire:

1. Signal line structure: in addition to the original power line and data line (D +, D-) of USB2.0, USB3.0 wire also adds four additional high-speed data channels to form a pair of SuperSpeed differential pairs (RX1 +/RX1-and TX +/TX-),Supports full duplex data transmission up to 5 Gbps.
2. Materials and quality:

Conductor material should use high quality copper wire, such as oxygen-free copper, to ensure low resistance and signal transmission clarity.

Insulating materials should meet certain dielectric constant and dielectric loss to reduce signal attenuation and delay. Usually, materials with low dielectric constant (DK) are selected.

The shielding layer must be tight enough to reduce electromagnetic interference (EMI) and signal crosstalk, which usually includes one or two layers of metal foil shielding layer plus ground braided layer.

Wire color: the standard of USB3.0 wire requires that the internal SuperSpeed difference should be blue to distinguish the outer skin of the wire, which is a unique identification of usb3.0.

1. Length limit:

The USB3.0 standard does not have a clear limit on the length of wires, but considering the influence of signal attenuation and noise, the length of cables recommend in practical engineering applications is usually less than 3 meters, which may affect the data transmission rate and stability.

1. Interface compatibility:

The USB plugs at both ends of the wire shall conform to the USB 3.0 interface standard to ensure physical compatibility with the USB 3.0 device, and shall also be downcompatible with the USB 2.0 device.

1. Electrical performance:

The wire shall undergo strict electrical performance tests, including signal integrity and consistency tests, to verify whether it meets various indicators required by USB3.0 specifications, such as signal eye diagrams, radiation, static electricity, etc.

Attachment USB cable reference design drawing

![Official Orbbec figure from Reference Design - Cable (USB) (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ffCzSbjG5C8LysX49RLE/assets/631c7998d172a5a56f0b.webp)

### Reference Design for Ethernet Device

| **Interface** | **Product**  | **Reference Design**                                                                 | **Version** | **Release Date** | **Remark** |
| ------------- | ------------ | ------------------------------------------------------------------------------------ | ----------- | ---------------- | ---------- |
| Ethernet      | Gemini 335Le | [Gemini 335Le ME Design Guideline \_V1.2.pdf](https://doc.orbbec.com/attachments/28) | V1.2        | 2026-04-19       |            |

### Troubleshooting

#### **1. Camera Not Working or Detected**

**Q1: The camera is connected, but when I launch the Orbbec Viewer tool on Ubuntu system, it doesn’t detect the device.**

Add sudo permissions when you launch the Orbbec Viewer tool.

**Q2: The camera is connected, Orbbec Viewer tool cannot detect the camera device after a period of use, but the camera device can be detected in the system terminal with "lsusb" command.**

Disconnect the camera USB port and reconnect it.

**Q3: Camera is connected to the USB3.0 port, but it is incorrectly identified as USB2.0.**

First, you can check whether the USB cable and the host port are USB3.0 compliant and make sure the USB connector is fully plugged in;

Then, disconnect the camera USB port and reconnect it smoothly.

**Q4: Orbbec Viewer tool doesn’t detect the device after you restart the host.**

Maybe you restrat the host straightly without closing the data streams. If you want to restart the host, please close all the data streams first.

**Q5: When you run the Orbbec Viewer tool on a brand-new Ubuntu 22.04 system, the camera doesn’t work.**

First, you should grant permissions to the installation file in the Orbbec Viewer directory. To do this, you could enter the path of the script file and then execute the command "sudo chmod 777 install.sh";

Second, proceed to execute command "sudo ./install.sh";

Lastly, run Orbbec Viewer with the command "sudo ./OrbbecViewer".

**Q6: How to get the log of hardware level?**

Here are three ways to get the log.

1. Turn on the "heartbeat" switch in Orbbec Viewer;
2. By API,device->setBoolProperty(OB\_PROP\_HEARTBEAT\_BOOL, true);
3. By configuration file, config the "DefaultHeartBeat" as 1. The file is located at ./SDK/Config

**Q7: When the camera is connected to the USB2.0 port, the camera identification may take a long time.**

We recommend using the USB3.0 port and the corresponding USB cable;

If you use the USB2.0 port or USB2.0 cable, camera identification takes about 20 seconds.

#### **2. Function**

**Q1: The display resolution in metadata is half of the set resolution or less.**

Switching off the decimation filter can solve this issue. You can find it in: Depth => Advanced Control => Decimation Filter.

**Q2: Failed to switch to another depth preset when any data stream is started.**

If you want to switch to another depth preset, please close all the data streams first.

**Q3: When depth, IR left, IR right and RGB are streaming at the same time, there may be some frame loss. This problem may exist on some hosts.**

High-end hosts are essential for simultaneously streaming depth, IR left, IR right and RGB data due to rapid memory access required for high-throughput data transmission via USB connection. If low-end hosts are deployed or hosts are heavily loaded, start with fewer than four data streams to ensure more reliable data transmission.

We recommend the following configuration to you:

Ubuntu 20.04/22.04 i7-7700 CPU@3.60GHz x64 8GB, or above.

**Q4: Set another IR resolution when depth data stream is started, it may cause some data streams error with a low probability.**

If you want to set another resolution, please close all the data streams first.

**Q5: In "Orbbec Viewer-Device Control-Preset-Factory Calib" mode, there are many resolutions of depth and IR data stream cannot be started.**

The "factory calib" only supports specific resolution. It is an internal production mode and is therefore not recommended for general use.

**Q6: Point cloud may not be built accurately if you mirror, flip or rotate the depth/color data stream in the previous step, it will also lead to align mode error.**

Mirror, flip, or rotate is seen as illegal operation for pointcloud preview. Please restore to original state and try again.

**Q7: Start the depth and IR stream immediately when you switch to another depth preset, it may fail with a low probability.**

The tool will reload some parameters when you switch to another depth preset, we advise waiting 3 seconds before starting the data stream.

**Q8: In linux, if you press "Ctrl+C" on the terminal to exit the Orbbec Viewer, it may fail to start the depth and IR stream when you restart Orbbec Viewer immediately.**

It takes time for the Viewer to exit, we advise waiting for 3 seconds before restarting it.

**Q9: In linux, if you connect two or more cameras on one low-end host, it may fail to start all the cameras and all the data stream.**

You can try to increase the system buffer size to solve this problem.

Try to execute "sudo sh -c ‘echo 128> /sys/module/usbcore/parameters/usbfs\_memory\_mb".

**Q10: Color data stream cannot be started after updating the firmware.**

The RGB firmware update was unsuccessful; please try updating it again.

**Gemini 335 buyers:** Use the dedicated [Orbbec Gemini 335 User Manual](https://wiki.openelab.io/orbbec/orbbec-gemini-335-user-manual) as the primary product manual. This series manual remains the shared development reference for Gemini 330 Series cameras.

### Frame Metadata

Frame metadata is a set of parameters (or attributes) that provide a snapshot of the sensor configuration and/or system state present during the frame’s generation. The attributes are recalculated and updated on a per-frame basis. Orbbec SDK supports querying a set of predefined attributes as part of the frame data available to the end-user.

#### **1. API**

`Orbbec SDK` introduces two functions into its public API to query metadata:

C:

```
/**
 * @brief check if the frame contains the specified metadata
 *
 * @param[in] frame frame object
 * @param[in] type metadata type, refer to @ref ob_frame_metadata_type
 * @param[out] error Log error messages
 */
bool ob_frame_has_metadata(ob_frame *frame, ob_frame_metadata_type type, ob_error **error);

/**
 * @brief Get the metadata value of the frame
 *
 * @param[in] frame frame object
 * @param[in] type  metadata type, refer to @ref ob_frame_metadata_type
 * @param[out] error Log error messages
 * @return int64_t return the metadata value of the frame
 */
int64_t ob_frame_get_metadata_value(ob_frame *frame, ob_frame_metadata_type type, ob_error **error);
```

C++:

```
// Member functions of class ob::Frame

/**
* @brief Check if the frame object has metadata of a given type.
*
* @param type The metadata type. refer to @ref OBFrameMetadataType
* @return bool The result.
*/
bool hasMetadata(OBFrameMetadataType type);

/**
* @brief Get the metadata value
*
* @param type The metadata type. refer to @ref OBFrameMetadataType
* @return int64_t The metadata value.
*/
int64_t getMetadataValue(OBFrameMetadataType type);
```

#### **2. Example**

The envisaged mode of querying metadata attribute is `check-then-query`

```
const char *metaDataTypes[] = { "TIMESTAMP", "SENSOR_TIMESTAMP","FRAME_NUMBER",
                                "AUTO_EXPOSURE", "EXPOSURE", "GAIN",
                                "AUTO_WHITE_BALANCE", "WHITE_BALANCE", "BRIGHTNESS",
                                "CONTRAST", "SATURATION", "SHARPNESS",
                                "BACKLIGHT_COMPENSATION", "HUE", "GAMMA",
                                "POWER_LINE_FREQUENCY", "LOW_LIGHT_COMPENSATION", "MANUAL_WHITE_BALANCE",
                                "ACTUAL_FRAME_RATE", "FRAME_RATE",  "AE_ROI_LEFT",
                                "AE_ROI_TOP",  "AE_ROI_RIGHT", "AE_ROI_BOTTOM",
                                "EXPOSURE_PRIORITY", "HDR_SEQUENCE_NAME", "HDR_SEQUENCE_SIZE",
                                "HDR_SEQUENCE_INDEX", "LASER_POWER", "LASER_POWER_MODE",
                                "EMITTER_MODE", "GPIO_INPUT_DATA" };
ob::Pipeline pipe;
pipe.start(nullptr);

auto frameSet = pipe.waitForFrames(100);
auto colorFrame = frameSet->ColorFrame();
for(int metaDataType = 0; metaDataType < OB_FRAME_METADATA_TYPE_COUNT; metaDataType++) {
     // Check if it is supported metaDataType for current frame
    if(colorFrame->hasMetadata((OBFrameMetadataType)metaDataType)) {
       // Get the value of the metadata
       auto value = colorFrame->getMetadataValue((OBFrameMetadataType)metaDataType)
       std::cout << metaDataTypes[metaDataType] << ": " << value << std::endl;
    }
    else {
        std::cout << metaDataTypes[metaDataType] << ": " << "unsupported" << std::endl;
    }
}
```

#### **3. Display Frame Metadata in OrbbecViewer**

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qVODavWnrIiDkhMwVVwN/assets/176f77b12d9091d447e4.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-07/image.png)

#### **4. OS Support**

_**Windows OS**_ – Metadata extraction is supported by Microsoft starting with Windows 10. Check the Windows installation guide for details.

**Other OS –** We use libuvc/libusb as the default backend, which does not require any operation to enable metadata support.

#### **5. Devices Support**

Currently, only the Orbbec Gemini 300 series supports those APIs.

### Creating Filters Directly

**1. Quick Start**

Using ThresholdFilter as an example, complete post-processing in 3 steps:

_#include \<libobsensor/ObSensor.hpp>_

_// Step 1: Create the Filter_

_auto thresholdFilter = std::make\_shared_[_ob::ThresholdFilter_](ob::ThresholdFilter)_();_

_// Step 2: Set parameters (keep depth values between 300mm and 3000mm)_

_thresholdFilter->setValueRange(300, 3000);_

_// Step 3: Process the frame (depthFrame comes from a FrameSet obtained via Pipeline)_

_auto outFrame = thresholdFilter->process(depthFrame);_

_if(outFrame) {_

_auto processedDepth = outFrame->as_[_ob::DepthFrame_](ob::DepthFrame)_();_

_// Use processedDepth ..._

_}_

**2. Chaining Multiple Filters**

Multiple Filters can be chained together, passing the output of one Filter as the input to the next.

**Chain Order (Depth Stream)**

_Format Conversion (FormatConvertFilter)_

_→ Downsampling (DecimationFilter)_

_→ Sequence Filtering (SequenceIdFilter)_

_→ Threshold Filtering (ThresholdFilter)_

_→ Noise Reduction (EdgeNoiseRemovalFilter/FalsePositiveFilter/_

_MgcNoiseRemovalFilter/LutNoiseRemovalFilter)_

_→ Spatial Smoothing (SpatialAdvancedFilter/SpatialFastFilter/_

_SpatialModerateFilter)_

_→ Temporal Smoothing (TemporalFilter)_

_→ Hole Filling (HoleFillingFilter)_

_→ Software Alignment (Align)_

_→ Point Cloud (PointCloudFilter)_

\*\*⚠ Note:\*\*A slash (/) indicates optional alternatives within the same stage. Choose based on your device model and scenario requirements. Keep the relative order of Filters unchanged; reordering may produce unexpected results.

**Code Example (threshold filtering → noise reduction → spatial smoothing → software alignment → point cloud):**

_auto thresholdFilter = std::make\_shared_[_ob::ThresholdFilter_](ob::ThresholdFilter)_();_

_thresholdFilter->setValueRange(300, 3000);_

_thresholdFilter->enable(true);_

_auto edgeFilter = std::make\_shared_[_ob::EdgeNoiseRemovalFilter_](ob::EdgeNoiseRemovalFilter)_();_

_edgeFilter->enable(true);_

_auto spatialFilter = std::make\_shared_[_ob::SpatialAdvancedFilter_](ob::SpatialAdvancedFilter)_();_

_spatialFilter->enable(true);_

_auto alignFilter = std::make\_shared_[_ob::Align_](ob::Align)_(OB\_STREAM\_COLOR);_

_alignFilter->enable(true);_

_auto pointCloudFilter = std::make\_shared_[_ob::PointCloudFilter_](ob::PointCloudFilter)_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_RGB\_POINT);_

_pointCloudFilter->enable(true);_

_// Frame processing should be done in a separate thread. Do not call it directly in the frame acquisition or callback thread._

_if(!frameSet) return;_

_auto depthFrame = frameSet->getFrame(OB\_FRAME\_DEPTH);_

_auto colorFrame = frameSet->getFrame(OB\_FRAME\_COLOR);_

_if(!depthFrame || !colorFrame) return;_

_std::shared\_ptr_[_ob::Frame_](ob::Frame) _outFrame = frameSet;_

_for(auto \&filter : std::vector\<std::shared\_ptr_[_ob::Filter_](ob::Filter)_>{_

_thresholdFilter, edgeFilter, spatialFilter,_

_alignFilter, pointCloudFilter}) {_

_if(outFrame) {_

_outFrame = filter->process(outFrame);_

_}_

_}_

_// outFrame is the point cloud frame after the full processing chain_

**3. Other Common Interfaces**

_// Disable the Filter_

_filter->enable(false);_

_// Enable the Filter_

_filter->enable(true);_

_// Query whether the Filter is currently enabled_

_bool enabled = filter->isEnabled();_

### Set up Cameras for External Synchronization

#### **1. Connection Preparation**

**1.1 Multi-camera Sync Hub Pro and Cable**

Table 1-1: Summary of Multi-Camera Synchronization Hub Pro and Cable

| **Description**                                                                                                                                                                                                                                     | **Qty** | **Purchase Link**                                                                                   | **Remarks Description**                                                                                                                                                                    | **Example**                                                      |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- |
| 3D Camera                                                                                                                                                                                                                                           | N       | Corresponding links for each product                                                                | _N_\*≥ 2\*                                                                                                                                                                                 | _Gemini 335 :2_                                                  |
| Multi-Camera Sync Hub Pro ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/v52QcB4F3pBDShAJlUjM/assets/2029a89610b62e812794.webp)                          | 1       | [Purchase Link](https://store.orbbec.com/products/sync-hub-pro)                                     | _1 hub supports 1 primary and up to 8 Secondary cameras_                                                                                                                                   | _Quantity: 1_                                                    |
| Multi-camera Sync Adapter for Gemini\&Astra series ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/E6g6bB52jLsLVuhgpnVz/assets/b26649f198cc3c1b0454.webp) | N       | [Purchase Link](https://store.orbbec.com/products/sync-adaptor-for-astra-2-and-gemini-2-330-series) | _SH1.0-8P synchronous patch cord_                                                                                                                                                          | _Quantity: 2_                                                    |
| Multi-camera Sync Adapter for Femto series ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ECBHoYQNBg8Mmrx1GWu0/assets/18c3462f0a578d0f5a1b.webp)         | N       | [Purchase Link](https://store.orbbec.com/products/sync-adaptor-for-femto-mega-and-femto-bolt)       | _SH1.2-8P synchronous patch cord_                                                                                                                                                          | N/A                                                              |
| _Network cable_ ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3m40XdzNXilX6ALTDd7U/assets/3b16ff93e30566e74988.webp)                                    | N       |                                                                                                     | _To be provided by the user:_ Network cable standard T568B To T568B,Cate5e and above specifications, network cable length can be confirmed according To the actual scene, recommended <10m | _Quantity: 2_                                                    |
| _multi-camera synchronization hub Type-C power cable_                                                                                                                                                                                               | 1       |                                                                                                     | _To be provided by the user_                                                                                                                                                               | _Quantity: 1_                                                    |
| _For camera power supply and data transmission USB3.0 Hub_                                                                                                                                                                                          | 1       |                                                                                                     | _To be provided by the user_                                                                                                                                                               | _Quantity: 0;2+ USB ports of computers can meet the requirement_ |

**1.2 Multi-camera Sync Dev Hub and Cable**

Table 1-2 Summary of Multi-Camera Synchronization Hub and Cable

| **Description**                                                                                                                                                                                                                                       | **Qty** | **Purchase Link**                                                                                          | **Remarks Description**                                  | **Example**     |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------- | --------------- |
| 3D Camera                                                                                                                                                                                                                                             | N       | Corresponding links for each product                                                                       | _N_\*≥ 2\*                                               | _Gemini 335L:4_ |
| Multi-Camera Sync Hub Dev (Star/Daisy-Chain) ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ACwtKmrtVQr0wEQSPuk7/assets/bdea94ef8ca83dfc9eeb.webp)         | 1       | [Purchase Link](https://store.orbbec.com/products/sync-hub-dev-star)                                       | _1 hub supports 1 primary and up to 4 secondary cameras_ | _1_             |
| Multi-Camera Sync Cable Dev for Gemini\&Astra series ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/48jYj04UkKzhppeRZZaC/assets/b51a24d0676c780a93ac.webp) | N       | [Purchase Link](https://store.orbbec.com/products/sync-cable-8-pin-1m-for-astra-2-and-gemini-2-330-series) | _SH1.0-8P synchronous cable_                             | _4_             |
| Multi-Camera Sync Cable Dev for Femto series ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Bd7QiVr195vsNAQ7KqFd/assets/a6c0bbe34766161547fc.webp)         | N       | [Purchase Link](https://store.orbbec.com/products/sync-cable-8-pin-1m-for-femto-mega-and-femto-bolt)       | _SH1.2-8P synchronous cable_                             | N/A             |
| _multi-camera synchronization hub Type-C power cable \* 1_                                                                                                                                                                                            | 1       |                                                                                                            | _To be provided by the user_                             | _1_             |
| _USB3.0 Hu&#x62;_&#x32;\*                                                                                                                                                                                                                             | 1       |                                                                                                            | _To be provided by the user_                             | _1_             |

* 1 Type-C power cable, power supply requirements: 5V
* 2 for USB Hub with external power supply, the output current needs to meet the specification requirements of the product. The above recommendations are the relevant USB Hub used in our actual test for reference. The required specification is a Hub with an external power supply, and the output requirement is 5V 2.4A.

**1.3 Camera Power Supply Requirements**

1. After purchasing the camera, you can choose to power it either via USB 3.0 or PoE (Power over Ethernet), based on the specific camera model. (The camera must support PoE functionality.)
2. When using a USB 3.0 Hub for power, verify whether the upstream device’s output current meets the product’s requirements according to the camera’s specifications. Typically, a computer’s USB 3.0 port outputs 900mA/4.5W. If this does not meet the product’s specifications, ensure the use of an external USB Hub with sufficient output current as per the product’s requirements. Please refer to Appendix 1 for detailed information.

For reference, we have tested the following USB Hubs for practical use:

Table 1-3 Reference Description of Camera Power Supply and Connection Cable

| **USB Hub Model** | **Specifications**         | **Purchase Reference Link** |
| ----------------- | -------------------------- | --------------------------- |
| USB3.0 Hub        | USB3.0 hub, output 5V 2.4A | **USB Hub purchase link**   |

3. Typically, to ensure adequate power supply for some cameras, the camera is factory-equipped with a Type-C to Type-C cable. When synchronizing multiple cameras, you will need to purchase Type-C to Type-A cables. Orbbec can provide official 1m/2m Type-A to Type-C cables. For longer cables, please refer to the document [reference design\&best practice-cable](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Cable%20\(USB\)%20\(Gemini%20330%20Series\)).

**1.4 Platform Configuration**

When running multi-camera synchronization, the host computer may need to simultaneously read and process data from multiple cameras. Therefore, we recommend using a sufficiently powerful host computer platform to ensure smooth operation of the multi-camera synchronization function. The following platform configurations have been tested previously and can support the normal operation, provided as a reference:

Table 1-4 Platform Configuration Description

| **Platform**                          | **X64**                                      | **ARM 64**      |             |
| ------------------------------------- | -------------------------------------------- | --------------- | ----------- |
| Hardware device                       | PC                                           | Orin Nano       |             |
| System                                | Windows 10                                   | Ubuntu20.04     | Ubuntu20.04 |
| CPU                                   | Intel i7-10750H                              | Intel i7-10750H | 6-core A78  |
| RAM                                   | 16GB                                         | 16GB            | 8G          |
| Typical number of supported secondary | Please refer to Appendix I for more details. |                 |             |

\*Linux Computer: USB Buffer Configuration on Ubuntu: By default, Linux-based hosts allocate only 16 MB of kernel memory for USB controller operations. This allocation may be insufficient for handling high-resolution images or multiple streams and devices. To support multiple devices, the USB controller requires more memory. Follow these steps to increase the memory allocation:

1. Edit.
2. Locate the following line:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`

(Or other contents within the quotes, depending on your system) Replace it with:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.usbfs_memory_mb=128"`

Note: This command sets the USB memory to 128 MB. This example configuration is eight times the default value. Adjust the value accordingly based on your specific requirements.

1. Run.
2. Restart your computer.

These steps will adjust the USB memory allocation to enhance performance, particularly when dealing with multiple devices or high data throughput scenarios.

#### **2. Device Connection Operation Instructions**

Below, we will illustrate an example of star connection using Gemini 335 in conjunction with the developer version of the hub.

**2.1 Detailed Camera Connection Steps**

Table 2-1 Detailed operation steps for camera connection

| **Operation steps** | **Overview of operating steps**                      | **Detailed description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | **Notes and Schematic Diagram**                                                                                                                                                                 |
| ------------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1                   | Preparation for connection                           | <p>You will need to prepare the following items: – 2x Gemini 335 cameras<br>– 2x synchronization cables<br>– 2x Type-A to Type-C cables<br>– 1x multi-camera synchronization hub<br>– 1x Type-C interface synchronization hub power cable</p>                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                 |
| 2                   | Connect the cables at the camera end.                | <p>Connect the USB cables and multi-camera synchronization cables as shown in the diagram. <img src="https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/xK8VRauYa867nKuusQ1k/assets/14720cd2925836f5db1c.webp" alt="Official Orbbec figure from Set up Cameras for External Synchronization"><br>Note: When connecting at the camera end, ensure the red line on the synchronization cable aligns with the rotational position of the synchronization port plug.<br>Follow the host’s connection method to sequentially connect the secondary cameras (Secondary Cam 1/2/3/4) to the hub.</p>                                                                | ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/p7oxMXCv0KWmTZvMJqKS/assets/a9eaff277030b41ebfa5.gif) |
| 3                   | Connect the cables at the hub end                    | <p>1. Connect the host’s synchronization cable to the "Primary In" port of the multi-camera synchronization hub. 2. Connect the secondary cameras’ synchronization cables to the "Secondary: Cam" ports of the multi-camera synchronization hub. If there are multiple secondary cameras, connect them sequentially to Secondary Cam 1/2/3/4 ports on the hub.<br>3. Connect a 5V power supply to the Type-C port or DC port of the hub.<br>[Note] For synchronization involving more than 4 secondary cameras, a synchronization extender is required. For detailed connection instructions, please refer to the datasheet of the multi-camera synchronization hub.</p> | ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rigsvBLHEjrsHyZ1WOL6/assets/c92e21183b672c29bfb3.gif) |
| 4                   | Connect the cameras to the host computer or USB hub. | Connect the cameras to the USB 3.0 ports on the host computer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | The USB hub must be USB 3.0 and independently powered. If connecting directly to the host computer, ensure that the USB output current is ≥1.5 A.                                               |

**2.2 Complete Schematic Diagram of Camera Connections**

![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/hhGuSM24u55EmyRnjxHQ/assets/0143ec82eaa51c0a042e.webp)

Figure 2-1 Schematic diagram of complete camera connection

Number Name Description:

| NO. | Description                        | No. | Description        |
| --- | ---------------------------------- | --- | ------------------ |
| ①   | 3D camera                          | ⑤   | power supply cable |
| ②   | multi-camera synchronization Hub   | ⑥   | USB Hub            |
| ③   | multi-camera synchronization cable | ⑦   | Host               |
| ④   | USB data Cable                     |     |                    |

See Appendix I for details of the connection instructions for the professional version.

#### **3. Camera Configuration**

**3.1 Use the Orbbec Viewer to Configure and Verify that Synchronization Takes Effect**

* Get Orbbec Viewer:[Download Orbbec Viewer.](https://github.com/orbbec/OrbbecSDK/releases)
* Gemini 330 series synchronization effective confirmation method:

After connecting the camera according to the 2.1, open the Orbbec Viewer and perform the following configurations:

1. Primary configuration, as shown in Figure 3-1:

① The primary synchronization configuration mode is configured as Software Triggering

② Make sure the trigger out enable is available

③ Set the primary single trigger acquisition frame number, can be set to any value

④ Click on "Write" button to save the settings.

⑤Confirm synchronization configuration was saved successfully.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/eZrYntQLMWFAcZeS8CUd/assets/4d8c4d209ca854355815.gif) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Figure 3-1-1 Gemini 335 Synchronization Validation Primary Configuration

2. Configuration of the secondary device, as shown in Figure 3-2:

① Set the secondary synchronization configuration mode to Hardware Triggering.

② Make sure the trigger out enable is available if using daisy-chain topology, and this is not required for star topology.

③ Set the number of frames for single-trigger data collection on the secondary device, which can be configured to any value.

⑤Confirm synchronization configuration was saved successfully.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oNerZCBwDQ2IZPnXO2gM/assets/f21eaf12548ef575cbc3.gif) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Figure 3-1-2 Gemini 335 Synchronization Validation Secondary Configuration

3. Toggle the depth and color buttons for the Primary and Secondary. The depth stream for both devices does not display, but the color stream is functioning correctly, as shown in Figure 3-3:

① Toggle the depth and color buttons for the Primary.

② Toggle the depth and color buttons for the Secondary.

③ Neither the Primary nor the Secondary outputs depth stream; only the color stream is outputted.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nfG2bYUVhgHxDVSeFf6Z/assets/ed3260805dd85fcbb4a7.gif) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Figure 3-1-3 Gemini 335 Synchronization Validation Secondary Configuration

4. Synchronization verification process as shown in Figure 3-4:

① Click the "Trigger Once" button on the Primary. Both the Primary and Secondary should capture stream normally, indicating that camera synchronization is functioning (hardware connection OK). If synchronization is not working, the Secondary device will not capture the specified number of frames after triggering from the Primary.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AWHydHQkxIoG4gRbKPMa/assets/0fbbdeae7c4955ecfcd6.gif) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Figure 3-1-4 Gemini 335 synchronization validation

* Confirmation of Astra 2 synchronization effectiveness is detailed in Appendix III.
* Confirmation of Femto Mega/Bolt synchronization effectiveness is detailed in Appendix IV.
* The synchronization verification method for Gemini 2 series is the same as for Gemini 330 series, with the only difference being that Gemini 2 series supports RGB triggering.

**3.2 Use the SDK to Run a Multi-camera Synchronization Example**

**3.2.1 Initial Configuration for Multi-Camera Synchronization**

SDK Acquisition: [Download Orbbec SDK](https://github.com/orbbec/OrbbecSDK/releases)

In the SDK program folder:\OrbbecSDK\_C\_C++\_v1.10.8\_20240604\_d1671a341\_win\_x64\_release\OrbbecSDK\_v1.10.8\Example\bin\
Find the configuration file "MultiDeviceSyncConfig.json", and configure it as shown in the following figure. After configuration, save the settings. (The following is a reference setting for the Gemini 330 series)

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/0M7wDgKkqGe8zxlEs69w/assets/20067c4575e8b4186f64.gif) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Figure 3-2-1 Gemini 335 multi-camera synchronization example configuration

\*Detailed configuration parameter explanations and the configuration parameters for different cameras are available in Appendix V.

**3.2.2 Running multi-camera synchronization Example**

1. Navigate to the directory where the SDK is installed on your system.

`\OrbbecSDK_C_C++_v1.10.8_20240604_d1671a341_win_x64_release\OrbbecSDK_v1.10.8\Example\bin`

1. Find the executable file named "MultiDeviceSync" in the
2. Run the "MultiDeviceSync" application by double-clicking on it or using the command line to execute it.
3. When prompted, choose the option related to multi-camera synchronization. Typically, you would enter "0" (or follow the specific instructions provided in the application’s interface).
4. Follow any additional prompts or instructions displayed by the application to set up and verify the synchronization between multiple devices.

This should initiate the example application and demonstrate how to synchronize multiple devices as per the capabilities of the Orbbec SDK version.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kzybZei3H1VQjUaDhBZQ/assets/27ca78cf19ff185456b6.gif) |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

Figure 3-2-2 Example Operation Diagram of Gemini 335 multi-camera Synchronization

1. Successful streaming and preview of multi-camera effects are shown in Figure 3-2-2 below.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/D8OHZpFxmW8fukBbCjct/assets/d276f32ed47da9aa396b.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Figure 3-2-3 Preview of multi-camera synchronous open streaming of Gemini 335

7. Checking the effect of multi-camera synchronization

① According to the designated device numbers as follows: Device#0 (Primary) and Device#1 (Secondary), locate the timestamps (Sensor timestamp for Gemini 335; Frame timestamp for Gemini 335L) that are closest to each other. These timestamps represent the synchronized timestamps between the two devices. The figure below illustrates that the depth synchronization timestamp between the Primary and Secondary devices shows a difference of 0 to 1ms, and the color synchronization timestamp also shows a difference of 0 to 1ms.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AmU9XiZ0C5ZA9lpN1sB7/assets/66af48cf2c235e34cdbd.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Figure 3-2-4 Gemini 335 multi-camera synchronization open-stream synchronization timestamp Log

**3.3 Key Log**

Table 3-3-1 Key Logs

| **Journal**           | **Significance**                      |
| --------------------- | ------------------------------------- |
| Device#0, color frame | RGB camera data stream for device 0   |
| Device#0, depth frame | Depth camera data stream for device 0 |
| Device#1, color frame | RGB camera data stream for device 1   |
| Device#1, depth frame | Depth camera data stream for device 1 |

Note: When analyzing data, confirm based on the timestamps of different devices.

Table 3-3-2 Key Words

| **Key word**     | **Meaning**                                                                                                                                                                                                                                                                                                                                                                |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Device#X         | X represents the device number. Device#0 and Device#1 are simply used to distinguish between different devices and are not related to the device IDs in the configuration file.                                                                                                                                                                                            |
| color frame      | Color stream                                                                                                                                                                                                                                                                                                                                                               |
| depth frame      | Depth stream                                                                                                                                                                                                                                                                                                                                                               |
| Frame timestamp  | Frame timestamp is critical for analyzing multi-camera synchronization. Frames from the same batch of data across different devices have closely aligned timestamps. Conversely, frames with similar timestamps generally depict similar content. This can be verified by capturing dynamic objects and judging the similarity of scene content based on object positions. |
| system timestamp | The system timestamp recorded after receiving a complete UVC data frame.                                                                                                                                                                                                                                                                                                   |

#### **4. Caution**

1. After starting the device, press ‘ESC’ in the image preview window to stop the data stream and exit the program. Abnormal program termination may cause incomplete shutdown of the device, leading to continuous triggering of the secondary device (restarting the device can resolve this).
2. The same device can only be accessed by one application at a time. Opening the same device with multiple applications simultaneously may cause anomalies. Please use with caution.
3. Using AE (Auto Exposure) may result in synchronization delays due to significant environmental differences between cameras. It is recommended to use the SDK to call exposure control interfaces and set fixed exposures to mitigate this issue.
4. For Linux computers, such as Ubuntu, the default kernel allocates only 16 MB of memory for USB controllers to handle USB transfers. This amount may be insufficient for high-resolution images or multiple streams and devices. To support multiple devices, the USB controller must have more memory allocated. Follow these steps to increase the allocated memory: 1. Edit.
5. Locate the following line:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`

(or other contents within quotes, depending on your system) and replace it with:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.usbfs_memory_mb=128"`

Note: This command sets USB memory to 128 MB. This example sets it to 8 times the default value. Adjust as needed.

1. Run .
2. Restart your computer.

#### **5. Code Development**

Users can refer to the example source code and interface documentation provided in the SDK package directory to develop their code according to actual business requirements.

Key code:

```
// Update the configuration items of the configuration file, and keep the original configuration for other items

Autocor config = device-> Get multi devices yncconfig ();

 

CurConfig. syncMode = config->syncConfig.syncMode;

curConfig.depthDelayUs         = config->syncConfig.depthDelayUs;

CurConfig. colorDelayUs = config->syncConfig.colorDelayUs;

CurConfig. trigger2ImageDelayUs = config->syncConfig.trigger2ImageDelayUs;

Curconfig. triggero-utenable = config-> syncconfig. triggero-utenable;

CurConfig. triggerOutDelayUs = config->syncConfig.triggerOutDelayUs;

CurConfig. framesPerTrigger = config->syncConfig.framesPerTrigger;

 

Device->setMultiDeviceSyncConfig(curConfig);

 

The enum names for different synchronization modes in the SDK: 

/**

* @ brief    The sync mode of the device

*/

Typedef enum {

 

/**

* @brief free run mode

* @ brief This device is not syncing with other devices

* @ brief "Color" and "Depth" can be set to different frame rates

*/

OB_MULTI_DEVICE_SYNC_MODE_FREE_RUN = 1 << 0,

 

/**

* @brief standalone mode

* @ brief This device is not syncing with other devices

* @ brief "Color" and "Depth" should be set to the same frame rate, "Color" and "Depth" will be synchronized

*/

OB_MULTI_DEVICE_SYNC_MODE_STANDALONE = 1 << 1,

 

/**

* @brief primary mode

* @ brief   This device is the primary device in a multi-camera system, which by default outputs trigger signals via the VSYNC_OUT pin on the synchronization port.

* @ brief The color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs.

*/

OB_MULTI_DEVICE_SYNC_MODE_PRIMARY = 1 << 2,

 

/**

* @brief secondary  mode

* @ brief This device is the secondary device in a multi-camera system, which receives trigger signals via the VSYNC_IN pin on the synchronization port. By default, it outputs trigger signals via the VSYNC_OUT pin on the synchronization port.

* @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs.

* @ brief After starting the stream, the device waits for trigger signals to begin capturing images and stops capturing images when the trigger signal stops.

*

* @ attention The frequency of trigger signals should match the frame rate set in the stream profile configured during stream startup.

*/

OB_MULTI_DEVICE_SYNC_MODE_SECONDARY = 1 << 3,

 

/**

* @brief secondary synced mode

* @ brief This device is the secondary device in a multi-camera system, which receives trigger signals via the VSYNC_IN pin on the synchronization port. By default, it outputs trigger signals via the VSYNC_OUT pin on the synchronization port.

* @ brief  Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs.

* @ brief After starting the stream, the device immediately begins capturing images and adjusts capture timing upon receiving trigger signals to synchronize with the primary device. The device continues capturing images even if trigger signals stop.

*

* @ attention The frequency of trigger signals should match the frame rate set in the stream profile configured during stream startup.

*/

OB_MULTI_DEVICE_SYNC_MODE_SECONDARY_SYNCED = 1 << 4,

 

/**

* @brief software triggering mode

* @ brief This device starts image capture upon receiving a capture command and by default outputs trigger signals via the VSYNC_OUT pin.

Capture commands can be sent from the host using @ref ob_device_trigger_capture.

The number of images captured per shot can be set using @ref framesPerTriggerForTriggeringMode

* @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs.

* @ brief The frequency at which the user calls @ref ob_device_trigger_capture to send capture commands multiplied by the number of frames per trigger should be less than the frame rate set in the stream configuration file at startup.

*/

OB_MULTI_DEVICE_SYNC_MODE_SOFTWARE_TRIGGERING = 1 << 5,

 

/**

* @brief hardware triggering mode

* @ brief This device starts image capture upon receiving a trigger signal via the VSYNC_IN pin on the synchronization port and by default outputs trigger signals via the VSYNC_OUT pin. The number of images captured per shot can be set using @ref framesPerTriggerForTriggeringMode.

* @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs.

*

* @ attention The frequency at which trigger signals are received multiplied by the number of frames per trigger should be less than the frame rate set in the stream configuration file at startup.

* @ attention  In hardware triggering mode or software triggering mode, the trigger signals input via the VSYNC_IN pin on the synchronization port should be output by other devices via the VSYNC_OUT pin.

* @ attention Due to potential differences in signal input requirements among different device models, do not use trigger signals output from different device models as input trigger signals.

*/

OB_MULTI_DEVICE_SYNC_MODE_HARDWARE_TRIGGERING = 1 << 6,

 

} ob_multi_device_sync_mode,

OBMultiDeviceSyncMode;
```

#### **6. Subsidiary Function**

**6.1 Use Orbbec Viewer to View Device SN**

When connecting multiple devices, follow these steps to view the SN (serial number) and connection method of the selected camera:

1. Select the corresponding device from the options in the top left corner as shown in Step ① of the following figure.
2. Then, click according to Step ② in the figure to view the SN and connection method of the selected camera.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/aMIS2svgiOVybPbEDqIU/assets/843aac581c89bdf72632.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Figure 6-1 diagram of the device SN viewed by the Orbbec Viewer

**6.2 View Multi-camera Synchronization Configuration in Orbbec Viewer**

① After connecting the devices, open the Orbbec Viewer tool. If multiple devices are connected, you need to select the devices. If only one device is connected, no selection is required as the device will be recognized automatically.

② Click on "Device Control" and expand "Synchronization Configuration" to display relevant parameters such as mode, color delay, depth delay, trigger output switch, signal output delay, and other information.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ZV6oChG0NkefeyLGPgG1/assets/a42e92d68126e144de96.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Figure 6-2 Schematic diagram of the equipment viewed by the Orbbec Viewer

#### **7. Appendix**

**7.1 Appendix I: Typical Number of Supported Secondary**

Appendix Table 1-1: Supported number of secondary and power requirements

| **Product**       | **Typical number of supported secondary** | **Maxunim of supported secondary**                                                                                                                                         | **Power supply request**                |
| ----------------- | ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| Femto Mega        | 1-4 units                                 | 8 units                                                                                                                                                                    | Use the camera’s built-in power supply. |
| Femto Bolt        | 1-4 units                                 | 1-4 units                                                                                                                                                                  | Use the camera’s built-in power supply. |
| Gemini 2          | 1-4 units                                 | Theoretical support for infinite expansion is contingent upon the performance of the host computer and bandwidth limitations. In practical tests, we have used four units. | Power supply:5V ; Current: ≥1.5A        |
| Gemini 2 L        | 1-4 units                                 | Power supply:5V ; Current: ≥2.0A                                                                                                                                           |                                         |
| Gemini 2 XL       | 1-4 units                                 | Power supply:5V ; Current: ≥2.0A                                                                                                                                           |                                         |
| Gemini 330 series | 1-4 units                                 | Power supply:5V ; Current: ≥1.5A                                                                                                                                           |                                         |
| Astra 2           | 1-4 units                                 | 7 units                                                                                                                                                                    | Power supply:5V ; Current: ≥1.5A        |
| Gemini 215        | 1-4 units                                 | 1-4 units                                                                                                                                                                  | Power supply:5V ; Current: ≥1.5.A       |

\*\*The maximum number of supported peripherals depends on the performance of the host computer and bandwidth limitations. When connecting multiple cameras to a single USB 3.0 hub, the primary consideration is the bandwidth limitation of the host system. It’s also important to verify whether the host computer’s USB ports are connected through internal USB hubs or if they have multiple independent controllers. If bandwidth issues cause streaming problems, reducing resolution or frame rate can be chosen as a solution.

**7.2 Appendix II: Detailed Operation Steps for Multi-camera Sync Hub Pro Connection**

Appendix Table 2-1 Detailed Operation Procedure Description of Camera Connection for Multi-camera Sync Hub Pro (The following takes 2 Gemini330 series cameras as an example to illustrate)

| **Operation steps** | **Overview of operating steps**                    | **Detailed description**                                                                                                                                                                                                                                                                                                                                     | **Notes and Schematic Diagram**                                                                                                                                                                  |
| ------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1                   | Connection preparation                             | You need to prepare 2x Gemini 330 series cameras, 2x Multi-camera Sync Adapter , 2x network cables, and a Multi-camera Sync Hub Pro.                                                                                                                                                                                                                         | Note: 1. Specifications of network cable: T568B-T568B,Cate5e and above; 2, Network cable length <10m                                                                                             |
| 2                   | Camera end connection                              | Connect the camera end to the Multi-camera Sync Adapter, USB cable and network cable as shown on the right.                                                                                                                                                                                                                                                  | ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/QdKBCSCRrUdoi2dfMMUX/assets/6e287e6b893c2c6be101.webp) |
| 3                   | Primary device hub-end connection                  | <p>① Connect one end of the network cable to the "Primary In" interface of the hub ② Connect the other end of the network cable to the synchronous adapter RJ45 interface of the Primary device.<br>③ Use the Type-C power cable to connect the Type-C 5V In of the synchronization hub and supply 5V power to it</p>                                        | ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zIZGq4qFaYqXXBCRUZT8/assets/447d4d6bebed06f13033.webp) |
| 4                   | secondary device hub-end connection                | <p>① Connect one end of the network cable to the "Secondary Cam1" interface of the synchronization hub ② Connect the other end of the network cable to the synchronous adapter RJ45 interface of secondary 1 device.<br>Note: If there are multiple cameras distributed, connect Secondary cam2/3/4 at one time according to the above Operation steps….</p> | ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/4pp96cUogeAf7JupVPsB/assets/08e3cd7f485663e9c3a4.webp) |
| 5                   | Connect the camera to the host computer or USB Hub | Camera and USB Hub need to be connected to USB3.0 interface                                                                                                                                                                                                                                                                                                  | The USB Hub needs to be USB3.0 with independent power supply; If directly connected to the host computer, pleaseensure that the USB output current is ≥ 2.0 A.                                   |

**7.3 Appendix III: Astra 2 Synchronization Confirmation Method**

1. After connecting the camera as described in section 2.1, open OrbbecViewer for the following configurations:
2. Configure the synchronization mode and parameters between the primary and the secondary according to Figure 3-1:

① Set the primary device sync mode to "Primary"

② Click ‘Write’

③ Select the secondary device, and set the sync mode to "Secondary-synced"

④ Set the secondary’s Trigger2Image delay \[1] is ≥4000

⑤ Click ‘Write’

Note: \[1] For star topology connection, set the secondary’s Trigger2Image delay between secondary 1 and the Prinary to be ≥4000 microseconds. If there are multiple secondary cameras, delays between secondary also need to be ≥4000 microseconds. For daisy-chain topology connection, set the secondary’s signal output delay to -1; this applies to all secondary.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/CzOeUedM5ICA1JFgQn4B/assets/f8aa43db47d5f24b7af2.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Appendix Table 3-1: Astra 2 Synchronization Confirmation Host/secondary Configuration Diagram

1. Configure the depth frame rate for the host and the secondary as shown in Figure 3-2:

① Set the Primary depth frame rate to 30fps.

② Set the secondary depth frame rate to 15fps.

③ Toggle the depth and color buttons on the primary device, Ensure normal depth and color streams from primary device.

④ Toggle the depth and color buttons on the secondary device, Confirm normal color stream from the secondary, with no depth imaging as expected.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/0qPWOhvbLFWPJ2HrrgUj/assets/767f6787071ea5192f80.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Appendix Table 3-2: Astra 2 Synchronization Confirmation Diagram

⑤ Set the secondary depth frame rate to 30fps to confirm synchronization is effective with normal data output (refer to Figure 3-3).

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/RR7P938EJkRTlX8UlKQY/assets/36d97e6cfccf9e85ea3b.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Appendix Table 3-3: Astra 2 Synchronization Confirmation Diagram

\[Note] Ineffective synchronization is indicated when the primary operates at 30fps for depth, and the secondary at 15fps for depth. When depth imaging is enabled on both devices, the secondary should display depth imaging correctly under these conditions.

**7.4 Appendix IV: Confirmation Method for Femto Mega/Bolt Synchronization Effectiveness**

1. Open OrbbecViewer and configure Femto Mega/Bolt as follows:
2. Configure the synchronization mode and parameters between the primary and the secondary cameras, as shown in Figure 3-1:

① Set the primary camera mode to: Primary

② Click ‘Write’

③ Select the secondary camera, and set the mode to: Secondary

④ Configure the secondarydepth delay: ≥125us, recommended 160us

⑤ Click ‘Write’

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IOm5MIvuVJLyDLW1Qli2/assets/1a843430253f54ae8170.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Appendix Table 4-1: Femto Mega/Bolt Synchronization Confirmation Host/Slave Configuration Diagram

2. Verification Method for Synchronization:

① Toggle the depth and color buttons on the secondary device. Neither depth nor color data streams are output from the secondary device.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yXxag0nbaGmMReQH8LOo/assets/9d704fbbeba1ee39dde2.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Appendix Table 4-2: Femto Mega/Bolt Synchronization Effectiveness Verification Diagram

② After enabling depth and color on the primary device, observe normal depth and color imaging on the secondary device to confirm synchronization is effective.

| ![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/YMNZhrq2JP5OMn7WyOpX/assets/9d32abcdb6bb0951114b.webp) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

Appendix Table 4-3: Femto Mega/Bolt Synchronization Effectiveness Verification Diagram

\[Note] Ineffective synchronization is indicated if the secondary camera does not produce images when the primary is enabled, or if the secondary produces images without the primary being enabled.

**7.5 Appendix V: Synchronous Configuration Details**

**7.5.1 Profile Description**

```
{

"version": "1.0.0",

"configTime": "2023/01/01",

"devices": [

{

"sn": "AY3A131007M", // 1. Configure Primary SN, case-sensitive.

"syncConfig": {

"syncMode": "OB_MULTI_DEVICE_SYNC_MODE_PRIMARY",  // 2. The sync mode is Configured to the PRIMARY mode.

"depthDelayUs": 0, // 3. Configure depth trigger delay, unit: microseconds

"colorDelayUs": 0, // 4. Configure color trigger delay, unit: microseconds

"trigger2ImageDelayUs": 0, // 5. Configure trigger image delay, unit: microseconds

"triggerOutEnable": true, // 6. Configure trigger signal output enable.

"triggerOutDelayUs": 0 // 7. Configure trigger signal output delay, unit: microsecond

"framesPerTrigger": 1 // 8. Configure the number of frames captured by each trigger in the trigger mode

}

},

{

"sn": "AY3JB20003C", // 9. Configure secondary SN,case-sensitive.

"syncConfig": {

"syncMode": "OB_MULTI_DEVICE_SYNC_MODE_SECONDARY_SYNCED",  // 10. All configurations are set to OB_MULTI_DEVICE_SYNC_MODE_SECONDARY_SYNCED except for Femto series,The Femto series is configured to OB_MULTI_DEVICE_SYNC_MODE_SECONDARY

"depthDelayUs": 0, // 11.Configure depth trigger delay, unit: microseconds

"colorDelayUs": 0, // 12. Configure color trigger delay, unit: microseconds

"trigger2ImageDelayUs": 0, // 13. Configure the trigger image delay, unit: microseconds

"triggerOutEnable": true, // 14. Configure trigger output enable,

"triggerOutDelayUs": 0 // 15. Configure the trigger signal output delay, unit: microseconds

"framesPerTrigger": 1 // 16. Configure the number of frames captured by each trigger in the trigger mode

}

}

]

}
```

① JSON files do not support comments, please do not copy the above comments.

The user can add configuration in the configuration file according to the actual number of devices used.

③ The camera SN number can be found on the camera housing, or it can be viewed on the device information page after connecting the device through the Orbbec Viewer tool.

④ When the primary mode is set, triggerOutEnable is forcibly set to true, and triggerOutDelayUs is forcibly set to 0.

**7.5.2 Multi-camera Synchronization Mode Definition Description**

| **Pattern Name**    | **Setting effect description**                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Free Run            | -Support different frame rate settings The synchronization interface does not support external output of synchronization-related signals                                                                                                                                                                                                                                                                                                                                  |
| Standalone(default) | <p>● Same as Primary by default ● Built-in RGBD frame synchronization<br>● Synchronous interface does not output signals to the outside by default</p>                                                                                                                                                                                                                                                                                                                    |
| Primary             | ● Set as primary camera ● Synchronous interface output signal to external device                                                                                                                                                                                                                                                                                                                                                                                          |
| Secondary           | ● Set as secondary (passive synchronization; When there is a hardware continuous trigger signal input from the outside and the continuous trigger signal matches the currently set frame rate, the image is collected according to the external trigger signal; When there is no external trigger signal, the flow is stopped) ● Synchronous interface output signal to external device                                                                                   |
| Secondary-synced    | ● Set to secondary synchronization (passive synchronization; When there is a hardware continuous trigger signal input from the outside and the continuous trigger signal matches the currently set frame rate, the image is collected according to the external trigger signal; When there is no external trigger signal, the image is collected according to the internal trigger signal at the set frame rate) ● Synchronous interface output signal to external device |
| Hardware Triggering | ● Set as hardware trigger (passive trigger; When there is a hardware trigger signal input from the outside and the trigger signal time interval is not less than the current upper limit, the image is collected according to the external trigger signal; When there is no external trigger signal, the image is not collected) ● Synchronous interface output signal to external device                                                                                 |
| Software Triggering | ● Set as software trigger (passive trigger; When there is a trigger command input from the host computer and the trigger command time interval is not less than the current upper limit, the image is collected according to the trigger command; When there is no trigger command, the image is not collected) ● Synchronous interface output signal to external device                                                                                                  |

**7.5.3 List of Product Support Modes**

| **Product**       | **Free Run** | **Standalone** **(Default)** | **Primary** | **Secondary** | **Secondary-synced** | **Hardware Triggering** | **Software Triggering** |
| ----------------- | ------------ | ---------------------------- | ----------- | ------------- | -------------------- | ----------------------- | ----------------------- |
| Gemini 330 series | Support      | Support                      | Support     | N/A           | Support              | Support                 | Support                 |
| Gemini 2          | Support      | Support                      | Support     | N/A           | Support              | Support                 | Support                 |
| Gemini 2 L        | Support      | Support                      | Support     | N/A           | Support              | Support                 | Support                 |
| Gemini2 XL        | Support      | Support                      | Support     | N/A           | Support              | Support                 | Support                 |
| Astra 2           | Support      | Support                      | Support     | N/A           | Support              | N/A                     | N/A                     |
| Femto Mega        | Support      | Support                      | Support     | Support       | N/A                  | N/A                     | Support                 |
| Femto Bolt        | Support      | Support                      | Support     | Support       | N/A                  | N/A                     | N/A                     |
| Gemini 215        | Support      | Support                      | Support     | N/A           | Support              | N/A                     | N/A                     |

The camera delay setting uses the default configuration.

**7.5.4 Comparison List of Camera Delay Settings**

Product NameDepth Delay(us)

| **Product Name**         | **Primary**              | **Secondary**                   | **Remark**                     |                          |                          |                                 |                                                                                                         |                         |                                                                                                                                              |
| ------------------------ | ------------------------ | ------------------------------- | ------------------------------ | ------------------------ | ------------------------ | ------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Depth Delay** **(us)** | **Color Delay** **(us)** | **Tigger2Image Delay** **(us)** | **Trigger Out Delay** **(us)** | **Depth Delay** **(us)** | **Color Delay** **(us)** | **Tigger2Image Delay** **(us)** | **Trigger Out Delay** **(us)**                                                                          |                         |                                                                                                                                              |
| Gemini 330 series        | 0                        | 0                               | N/A                            | 0                        | 0                        | 0                               | N/A                                                                                                     | 0                       |                                                                                                                                              |
| Gemini 2                 | N/A                      | N/A                             | 0                              | N/A                      | N/A                      | N/A                             | 0                                                                                                       | N/A                     |                                                                                                                                              |
| Gemini 2 L               | N/A                      | N/A                             | 0                              | N/A                      | N/A                      | N/A                             | 0                                                                                                       | N/A                     |                                                                                                                                              |
| Gemini 2 XL              | N/A                      | N/A                             | 0                              | N/A                      | N/A                      | N/A                             | 0                                                                                                       | N/A                     |                                                                                                                                              |
| Astra 2                  | N/A                      | N/A                             | 0                              | -1                       | N/A                      | N/A                             | <p>Daisy-chain: 0 Star : Delay between secondary devices ≥ 4000 µs.<br>For example, 4000/8000, etc.</p> | Daisy-chain: -1; Star:0 | Trigger Out Delay :-1 represents the default exposure output time for the camera; 0 indicates that no external trigger signal is being sent. |
| Femto Mega               | 0                        | 0                               | N/A                            | N/A                      | 160/ 320…                | 0                               | N/A                                                                                                     | 0                       |                                                                                                                                              |
| Femto Bolt               | 0                        | 0                               | N/A                            | N/A                      | 160/ 320…                | 0                               | N/A                                                                                                     | 0                       |                                                                                                                                              |
| Gemini 215               | N/A                      | N/A                             | 0                              | N/A                      | N/A                      | N/A                             | 0                                                                                                       | N/A                     |                                                                                                                                              |

\*The above delay values are recommended default settings. Users may adjust these values to any amount greater than the default based on actual needs, allowing for synchronization with external devices by modifying the delay.

### Regulatory Compliance and Certificates

Orbbec Gemini 330 series 3D camera certification and regulatory compliance information are as follows.| **Type** | **Certification** | **Gemini 335 \&Gemini 336** | **Gemini 335L \&Gemini 336L** | **Gemini 335Lg** | **Gemini 335Le** | **Gemini 338Le** | | --- | --- | --- | --- | --- | --- | --- | | **Laser Safety** | Class 1 | [CLASS 1\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf) | | | | | | FDA Accession Number | 2420619-002 | | | | | | | **EMC** | CE | [CE\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26132900/SZ24040105C01_CE_VoC.pdf) | [CE\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133940/SZ24040102C01_CE_VoC.pdf) | [CE\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033449/SZ24080134C01_CE_VoC.pdf) | [CE\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084855/CE_Orbbec_Gemini-335Le.pdf) | [CE\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/29) | | FCC | [FCC\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26141705/FCC_Gemini-33x.pdf) | [FCC\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26141702/FCC_Gemini-33xL.pdf) | [FCC\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033447/SZ24080133_FCC-SDoC.pdf) | [FCC\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084853/FCC_Orbbec_Gemini-335Le.pdf) | [FCC\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/30) | | | KC | [KC\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/27054345/%EC%A0%81%ED%95%A9%EB%93%B1%EB%A1%9D%ED%95%84%EC%A6%9D_Orbbec-Inc._G40155-170_240522.pdf) | [KC\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/27054347/%EC%A0%81%ED%95%A9%EB%93%B1%EB%A1%9D%ED%95%84%EC%A6%9D_Orbbec-Inc._G40055-170_240522.pdf) | In certification | [KC\_Orbbec\_Gemini 335Le](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/KC_Orbbec_Gemini%C2%A0335Le.pdf) | [KC\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/31) | | | UKCA | [UKCA\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133050/SZ24040105C02_UKCA_VOC.pdf) | [UKCA\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133937/SZ24040102C02_UKCA_VOC.pdf) | [UKCA\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033502/SZ24080254C01_UKCA_VOC.pdf) | N/A | N/A | | | IC | [IC\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133200/SZ24040106C01_IC_VOC.pdf) | [IC\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133932/SZ24040103C01_IC_VOC.pdf) | [IC\_Orbbec Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/04121846/IC_Orbbec-Gemini-335Lg.pdf) | N/A | N/A | | | RCM | [RCM Report\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084039/RCM_Orbbec-Gemini-33x.pdf) | [RCM Report\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084034/RCM_Orbbec-Gemini-33xL.pdf) | N/A | N/A | N/A | | | **Environment** | REACH | [REACH\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133633/SZ24040099R02_Orbbec_Gemini-335_REACH.pdf) | [REACH\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26134328/SZ24040100R02_Orbbec_Gemini-335L_REACH.pdf) | [REACH\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033456/SZ24080135R02_Orbbec_G40055_REACH-241.pdf) | [REACH\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084850/REACH_Orbbec_Gemini-335Le.pdf) | [REACH\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/32) | | RoHS | [ROHS\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133342/SZ24040099R01_Orbbec_Gemini-335_ROHS.pdf) | [ROHS\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26134324/SZ24040100R01_Orbbec_Gemini-335L_ROHS.pdf) | [ROHS\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033453/SZ24080135R01_Orbbec_G40055_ROHS.pdf) | [ROHS\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084847/ROHS_Orbbec_Gemini-335Le.pdf) | [ROHS\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/33) | | | WEEE | [WEEE\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133600/SZ24040099R03_Orbbec_Gemini-335_WEEE.pdf) | [WEEE\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26134320/SZ24040100R03_Orbbec_Gemini-335L_WEEE.pdf) | [WEEE\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033500/SZ24080135R03_Orbbec_G40055_WEEE.pdf) | [WEEE\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084843/WEEE_Orbbec_Gemini-335Le.pdf) | [WEEE\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/34) | | | 94/62/EC | [Package directive\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032021/Package-directive_Orbbec-Gemini-33xx.pdf) | TBD | | | | | | TSCA | [TSCA\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032019/TSCA_Orbbec-Gemini-33xx.pdf) | [TSCA\_Orbbec Gemini 338Le](https://doc.orbbec.com/attachments/35) | | | | | | TPCH | [TPCH\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032017/TPCH_Orbbec-Gemini-33xx.pdf) | TBD | | | | |

### Download Tools

| **Version**                           | **Link**                                                                                     |
| ------------------------------------- | -------------------------------------------------------------------------------------------- |
| Orbbec SDK and Viewer (Closed-source) | [https://github.com/orbbec/OrbbecSDK/releases](https://github.com/orbbec/OrbbecSDK/releases) |
| Orbbec SDK and Viewer (Open-source)   | [Releases · orbbec/OrbbecSDK\_v2](https://github.com/orbbec/OrbbecSDK_v2/releases)           |

### Development Resources

* [Official Gemini 330 Series documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)
* [CAD files](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))
* [Firmware releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))
* [Depth preset releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Preset%20Release%20\(Gemini%20330%20Series\))
* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK ROS 1 wrapper](https://github.com/orbbec/OrbbecSDK_ROS1)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
