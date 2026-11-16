# Orbbec Gemini 305 User Manual

## Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting

{% embed url="https://openelab.io/products/orbbec-gemini-305-range-stereo-vision-camera" %}

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-1.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-2.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-3.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-4.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-5.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-6.jpg?v=1781599183)

### Gemini 305

### 0 Glossary

Terms Descriptions ASIC Application-specific Integrated Circuit Baseline The distance between the optical centers of the two cameras used for depth calculation D2C Depth to Color maps each pixel on a depth map to the corresponding color image according to the intrinsic and extrinsic parameters of the depth camera and color camera Depth Depth video streams are similar to color video streams except each pixel has a value representing the distance away from the sensor instead of color information Depth Camera Includes depth imaging module and external interface, of which the former is generally composed of an infrared projector, infrared camera, and depth computing processor FOV Field of View describes the angular extent of a given scene that is captured by a camera, which can be measured in the horizontal, vertical, and diagonal I2C Refers to a simple bi-directional two-wire synchronous serial bus developed by Philips IR Light in the infrared spectrum, which ranges from 700 nm and above IR Camera A camera capable of seeing light in the IR spectrum ISP Image signal processor, which is used for image post-processing PCBA PCBA (Printed Circuit Board Assembly) refers to a fully assembled printed circuit board (PCB) that includes all the electronic components mounted and soldered onto it. Point Cloud A discrete set of data points in space RGB Camera A camera that captures color images and video. ROI Region of Interest (ROI) in image processing refers to a specific area selected from the entire image SOM A System on Module (SoM) provides various core components of an embedded processing system on a single printed circuit board, including the processor core, communication interfaces, and memory modules. A typical example of this is the NVIDIA Jetson series products

SBC A Single Board Computer (SBC) is a microcomputer where all the logic circuits, timing circuits, internal memory, and external interfaces are integrated onto a single printed circuit board. A typical example is the Raspberry Pi SoC System on Chip, an integrated circuit (IC) that integrates all components of a computing system UVC USB Video Class (UVC) is a protocol standard defined for USB video capture devices and has become one of the USB.org standards TBD To Be Determined. Information will be provided in a later revision.

### 1 Product Brief

The Orbbec Gemini 305 is a RGB stereo vision camera specifically designed to meet the demand for high accuracy and stability in close-range applications. Equipped with Orbbec’s latest MX6800 ASIC, it outputs depth data directly with low latency, significantly lowering the computational burden on the host system. The camera also integrates multi-camera synchronization functionality, which greatly enhancing the precision and stability of synchronization. It offers a variety of pre-defined depth presets, enabling one‑click switching between "depth + color" and "dual‑color" combinations. These various depth presets cater to the perception requirements of diverse applications, such as visual guidance of robotic arm visual guidance and vision foundation model (VFM) data collection. For connectivity, the camera employs a reliable USB Type-C interface with screw locking for bothpower and data transmission, combining plug-and-play ease with reliable physical connection. When used with a certified cable and the interface screw securely fastened, the system achieves an IP54, effectively protecting against dust and water splashes.

* Ultra-close Depth Imaging: 4cm @ 848 x 530 & 256 disparity search range
* Wide Color FOV: H 94° x V 68°
* Depth to Color Aligned FOV: H 88° × V 65° @ 20cm
* High Depth Accuracy: ≤ 1% ( 1280 x 800 @ 50cm)
* 1 Mega-pixel Color Stream at High Frame Rate: 1280 x 800 @ 60fps
* Low-Latency Direct Depth Output Down to 60 ms
* Support Dual Color Streams (Left & Right) with Consistent ISP Imaging Results
* Multi-Camera Sync in Two Methods: Hardware-Sync for High Accuracy &

Software-Sync for High Flexibility

* IP54 when the interface is properly connected

### 2 Product Specifications

Parameter Gemini 305 Use Environment Indoor & Outdoor Technology Stereo Vision Baseline 18mm Operating Range\[1] \[2] 4 – 100cm Ideal Range 7 – 50cm Spatial Precision ≤ 1% (1280 x 800 @ 50cm & 90% x 90% ROI) Depth Resolution @ Frame Rate Up to 1280 x 800 @ 30fps 848 x 530 @ 60fps Depth FOV H 88° x V 65° ± 3° (1280 x 800 @ 20cm) Depth Filter IR-Cut Sensor Type Stereo Color: Global Shutter Color Resolution @ Frame Rate Up to 1280 x 800 @ 60fps Color FOV H 94° x V 68° ± 3° Depth Processing Orbbec MX6800 ASIC Data Connection USB 3.0 (recommended) & USB 2.0 Interface USB Type- C EMC ESD：Class A Contact discharge: ± 8kV, Air discharge: ± 15kV RE：≥6 dB Max Average Power Consumption ≤2.0W Power Supply DC 5V & ≥700mA Operating Environment -10 - 45°C @ 128 disparity search range -10 - 40°C @ 256 disparity search range Operating Backside Case Temperature -10℃ - 60℃ Storage Environment Short Term: -20℃ - 70℃, 5%\~90% RH (non-condensing) Long Term: 0℃ - 60℃, 5%\~90% RH (non-condensing)

Protection IP54 (only when the Type-C interface is properly connected and the screws are tightened) Dimensions(W x H x D) 42 x 42 x 23mm Weight 68g Installation Bottom:1x 1/4-20 UNC, 2x M3 Back :2x M3 Lifespan 5 Years: Default Operating Mode & Operating Environment

Notes: \[1] The depth performance of each 3D camera is validated at the production line before shipping to customers. The metrics reflect the depth performance under typical conditions. External impact factors over 3D cameras’ whole lifespan may have significant impacts on their depth performance. \[2] 4cm @ 848 x 530, with the max disparity search range of 256 pixels enabled.

### 3 Product Information

#### 3.1 Product Pictures

Table 3-1-1 Product pictures for Gemini 305 Front View

Rear View

Top View

Bottom View

Left View

Right View

Left Side View at 45°

Right Side View at 45°

#### 3.2 Product Drawings

**3.2.1 Product Drawings**

Table 3-2-1 Product drawings for Gemini 305 Name Gemini 305 Front View

Rear View

Top View

Bottom View

Side View

**3.2.2 Product Dimensions & Weight**

Table 3-2-2 Product dimensions & weight for Gemini 305 Name Gemini 305 Width/mm 42 Height/mm 42 Depth/mm 23 Net Weight/g 68

#### 3.3 Product Interfaces

Table 3-3-1 Product interfaces Name Gemini 305 Gemini 305 USB Type-C

Interface Pin Map

Table 3-3-2 USB Type-C Interface Definition Pin Name Definition Pin Name Definition A1 GND Ground B1 GND Ground A2 TX1+ High-speed Differential Signaling#1, TX, Positive B2 TX2+ High-speed Differential Signaling#2, TX, Positive A3 TX1- High-speed Differential Signaling#1 TX Negative B3 TX2- High-speed Differential Signaling#2 TX Negative A4 VBUS Power B4 VBUS Power A5 CC1 Port configuration B5 CC2 Power configuration A6 D+ USB2.0 Differential Signaling#1, Positive B6 D+ USB2.0 Differential Signaling#2, Positive A7 D- USB2.0 Differential Signaling#1, Negative B7 D- USB2.0 Differential Signaling#2, Negative A8 SBU Sideband use, 1.8V(Default), 3.3V, 5V; SYNC\_IN (Default) or SYNC\_OUT B8 SBU Sideband use, 1.8V(Default), 3.3V, 5V; SYNC\_IN (Default) or SYNC\_OUT A9 VBUS Power B9 VBUS Power A10 RX2- High-speed Differential Signaling#2 RX Negative B10 RX1- High-speed Differential Signaling#1 RX Positive A11 RX2+ High-speed Differential Signaling#2 RX Positive B11 RX1+ High-speed Differential Signaling#1 RX Negative A12 GND Ground B12 GND Ground

#### 3.4 Product Components

**3.4.1 Overview of Product Components**

Table 3-4-1 Overview of product components for Gemini 305 Gemini 305

**3.4.2 RGB Module**

Table 3-4-2 RGB module specifications Parameters Gemini 305 Filter Type IR-Cut Active Pixels 1280 x 800 Sensor Aspect Ratio 16:10 Focus Type Fixed Shutter Type Global Shutter Horizontal FOV 94° Vertical FOV 68° Diagonal FOV 104° FOV Tolerance ± 3.0° Distortion <1.5%

### 4 Functional Specifications

#### 4.1 Vendor Identifier (VID) and Product Identifier (PID)

Table 4-1-1 VID & PID table Name Gemini 305 Model G40351-191 PID 0x0840 VID 0x2BC5

#### 4.2 Platform and System Requirements

Table 4-2-1 Gemini 305 Recommended Platforms and Systems Architecture x86/x64 ARM OS Windows 10/11 Ubuntu 22.04 / 24.04 Ubuntu 22.04 / 24.04 and above USB USB 3.0 USB 3.0 USB 3.0 CPU Quad-core, 2.9GHz Quad-core, 2.9GHz Quad-core, A57 Reference model Intel i5 / Intel i7 Intel i5 / Intel i7 NVIDIA Jetson Orin Nano / NVIDIA Jetson Orin NX / NVIDIA Jetson AGX Orin / NVIDIA Jetson Thor RAM 8GB RAM and above 4GB RAM and above 4GB RAM and above

#### 4.3 Camera system Framework

Figure 4-3-1 Gemini 305 System Block Diagram

#### 4.4 Image Data Stream

Gemini 305 provides high-quality, multi-resolution depth data, as well as high- definition color data. The camera outputs depth data in Y16 format., and the color data in MJPEG / YUYV format. The SDK supports a comprehensive set of data conversions among MJPEG / YUYV / RGB8 / BGR8 / RGBA8 / BGRA8 / Y16 / Y8 formats. The camera outputs IR image data in Y8 format. Gemini 305 offers two image data stream combinations: "Depth + Color" and "Dual Color." The output combination is determined by the device's preset configuration: selecting the "Dual Color" preset outputs dual color streams, while any other preset outputs the "Depth + Color" data stream. Users can switch the data stream output with one click by changing the depth preset.

**4.4.1 “Depth + Color” Combinations**

Table 4-4-1 “Depth + Color” Output data streams (USB3.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Depth Y16 16:10 1280 x 800 5, 10, 15, 30 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60 IR Y8 16:10 1280 x 800 5, 10, 15, 30 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60 Color YUYV/Y8/Y16/ MJPEG/RGB8 /BGR8/BGRA 8/RGBA8 16:10 1280 x 800 5, 10, 15, 30, 60 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30, 60 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60

Table 4-4-2 “Depth + Color” Output data streams (USB2.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Depth Y16 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30

IR Y8 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30 Color YUYV/Y8/Y16/ MJPEG/RGB8 /BGR8/BGRA 8/RGBA8 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30

**4.4.2 “Dual Color” Combinations**

Table 4-4-3 “Dual Color” Output data streams (USB3.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Color Left YUYV/Y8/Y16/ MJPEG/RGB8/ BGR8/BGRA8/ RGBA8 16:10 1280 x 800 5, 10, 15, 30, 60 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30, 60 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60 Color Right YUYV/Y8/Y16/ RGBA8/RGB8/ BGR8/BGRA8/ 16:10 1280 x 800 5, 10, 15, 30, 60 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30, 60 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60

Table 4-4-3 “Dual Color” Output data streams (USB3.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Color Left YUYV/Y8/Y16/ MJPEG/RGB8/ BGR8/BGRA8/ RGBA8 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30 Color Right YUYV/Y8/Y16/ RGBA8/RGB8/ BGR8/BGRA8/ 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30

#### 4.5 Hardware Decimation

The Gemini 305 supports configurable hardware decimation for proportional image scaling. This process performs pixel merging and aggregation at the hardware level, reducing the image resolution in both X and Y dimensions while preserving the original aspect ratio. The camera directly outputs the resulting lower-resolution image stream. By utilizing hardware decimation, the Gemini 305 significantly reduces data transmission bandwidth and power consumption while maintaining the depth accuracy inherent to its full sensor resolution. Table 4-5-1 Gemini 305 Hardware Decimation Resolution Before Decimation Decimation Factor Resolution After Decimation 1280 x 800 2 640 x 400 3 424 x 266 4 320 x 200

1280 x 720 2 640 x 360 3 424 x 240 4 320 x 180 848 x 480 2 424 x 240 640 x 480 2 320 x 240

#### 4.6 Depth to Color Alignment

Depth to Color, a pixel-by-pixel geometric transformation of a depth image, results in the spatial alignment of a depth image with its corresponding color image through the D2C transformation, allowing us to locate any pixel of a color image by its image coordinates in the depth image after D2C by the same image coordinates. The depth information of the color pixel can be located in the depth image after D2C by using the same image coordinates. We generate a depth image of the same size as the target color image after D2C, and the image content is the depth data in the color camera coordinate system. In other words, a depth image is reconstructed that is "taken" using the origin and size of the color camera, where each pixel matches the coordinates of the corresponding pixel of the color camera. Table 4-6-1 Gemini 305 Depth to Color Alignment by software Depth Image before D2C Color Image Depth Image After D2C Aspect Ratio 1280 x 800 / 1280 x 720 / 848 x 530 / 848 x 480 / 640 x 480 1280 x 800 1280 x 800 16:10 848 x 530 848 x 530 1280 x 800 / 1280 x 720 / 848 x 530 / 848 x 480 / 640 x 480 1280 x 720 1280 x 720 16:9 848 x 480 848 x 480 1280 x 800 / 1280 x 720 / 848 x 530 / 848 x 480 / 640 x 480 640 x 480 640 x 480 4:3

Table 4-6-2 Gemini 305 Depth to Color Alignment by hardware Depth Image before D2C Color Image Depth Image After D2C Aspect Ratio 848 x 530 / 848 x 480 / 640 x 480 1280 x 800 1280 x 800 16:10 848 x 530 848 x 530 848 x 530 / 848 x 480 / 640 x 480 1280 x 720 1280 x 720 16:9 848 x 480 848 x 480 848 x 530 / 848 x 480 / 640 x 480 640 x 480 640 x 480 4:3

#### 4.7 Field of View

**4.7.1 Definition of Depth Field of View**

The image below shows the depth field of view (FOV). For a better understanding, we illustrate the angles that the depth and IR cameras "see".

Figure 4-7-1 Depth Field of View to Depth Map illustration Depth FOV at any depth (Z) can be calculated using the following equation:

Table 4-7-1 Depth FOV calculation formulas Calculation Formulas Definitions fx cxwidth Z B fx cx −−+      −=− 1arctanarctanFOVHDepth

1. cx = X-direction image coordinates of the principle point of the depth image 2. fx= Depth camera focal length in pixels of x- axis 3. cy= Y-direction image coordinates of the principle point of the depth image 4. fy= Depth camera focal length in pixels of y-axis 5. width= Depth image width 6. Height=Depth image height 7. Depth active H-FOV =RGB Left / Right H-FOV fx cxwidth fx cx −−+=− 1arctanarctanFoVH ActiveDepth

)tan(\*2 B FOVH ActiveDepth Z −=

fy -cyheight- fy c 1arctanyarctanFOV-VDepth +     =

> Note:

1. Depth intrinsics, including cx, cy, fx, fy, width and height, are obtained through SDK APIs, and these parameters may vary across different units 2. At different depth values, the depth FOV is non-constant. The farther the depth, the greater the depth FOV.

**4.7.2 Typical Depth Intrinsics**

Table 4-7-2 Typical Depth Intrinsics of Gemini 305 Baseline/mm Resolution Width x Height cx/pixel cy /pixel fx & fy/pixel Width/pixel Height/pixel 1280 800 640 400 620.0 & 620.0 1280 720 640 360 620.0 & 620.0 848 530 424 265 410.7 & 410.7 848 480 424 240 410.7 & 410.7 640 480 320 240 372.0 & 372.0

**4.7.3 Overview of Stream FOV**

Table 4-7-3 Stream FOV for Gemini 305 FOV Aspect Ratio Resolutions Gemini 305 Depth FOV Before D2C @ 20cm 16:10 1280 x 800 / 848 x 530 H 88° V 65° 16:9 1280 x 720 / 848 x 480 H 88° V 60° 4:3 640 x 480 H 77° V 65° IR 16:10 1280 x 800 / 848 x 530 H 91° V 65° 16:9 1280 x 720 / 848 x 480 H 91° V 60° 4:3 640 x 480 H 81° V 65° Color 16:10 1280 x 800 / 848 x 530 H 94° V 68° 16:9 1280 x 720 / 848 x 480 H 94° V 62° 4:3 640 x 480 H 82° V 68° Depth FOV After D2C @ 20cm 16:10 1280 x 800 / 848 x 530 H 88° V 65° 16:9 1280 x 720 / 848 x 480 H 88° V 60° 4:3 640 x 480 H 77° V 65°

**4.7.4 FOV Illustrations**

Table 4-6-4 Gemini 305 Depth FOV Aspect ratio Depth FOV Before D2C Depth FOV After D2C 16:10

16:9

4:3

#### 4.8 Minimum-Z Depth

The Minimum-Z Depth is the minimum distance from the depth camera to the scene. Table 4-8-1 Minimum-Z Depth for Gemini 305 Disparity search range H / V-FOV: 88° / 65° H / V-FOV: 88° / 60° H / V-FOV: 77° / 65° 1280 x 800 848 x 530 1280 x 720 848 x 480 640 x 480 256 50mm 40mm 50mm 40mm 40mm 128 90mm 60mm 90mm 60mm 55mm 64 180mm 120mm 180mm 120mm 110mm

> Note:

1. The larger the disparity search range, the closer the minimum working distance becomes, and the higher the power consumption. Conversely, the smaller the disparity search range, the farther the minimum working distance extends, the lower the camera's power consumption, and the higher the ambient temperature it can withstand. 2. The disparity search range of 256 is only supported in the ”Close-Range” presets.
2.  #### 4.9 Coordinate System

    For the Gemini 305 3D camera, the plane where the 1/4 screw hole is located is defined as the bottom side, the glass cover surface is the front side and the area of the Type- C port is the left side. The positive X-axis of the coordinate system points to the right, the positive Y-axis points downwards, and the positive Z-axis points forwards. The origin of the depth image coordinate system and the origin of the color image coordinate system is at the optical center of the left RGB module. The direction of the coordinate systems is the same: the positive X-axis points to the right, the positive Y- axis points downward, and the positive Z-axis points forward. The depth camera coordinate system origin is the default origin of the 3D camera, with coordinates (0,0,0). The reference positions of the depth origin and color origin in the 3D camera coordinate system are shown in the chart below:

    Table 4-9-1 Gemini 305 Coordinate System Position Reference Coordinate System Origin in the 3D camera coordinate system X mm Y mm Z(mm) Depth 0 0 0 Color 0 0 0

    Table 4-9-2 Gemini 305 Coordinate System Schematic Gemini 305 Depth

    RGB

#### 4.10 Depth Start Point Reference

```
The depth start point, or ground zero reference can be described as a reference point or plane with depth = 0. For the Gemini 305 3D camera, the distance of the depth zero point to the front cover glass of the camera is listed below for both before and after the D2C alignment. Table 4-10-1 Camera Depth Start Point Illustrations Camera Gemini 305 Before the D2C alignment (Z’) 3.95 mm After the D2C alignment (Z’) 3.95 mm Depth Start Point
```

#### 4.11 Streaming Mode

```
Gemini 305 provides flexible acquisition options for IR, Depth, and RGB image data. The most commonly used mode is the streaming mode. In this mode, users configure a target frame rate, resolution, and image format for IR, Depth, and RGB respectively, and then enable the corresponding streams in sequence. The camera acquires and outputs image data according to the configured target frame rate, resolution, and image format. Depending on the current camera configuration, users can select an appropriate frame rate for the application from the following predefined frame rate options: 5 fps, 10 fps, 15 fps, 30 fps, and 60 fps.
```

#### 4.12 Triggering Mode

```
The Gemini 305 supports two image acquisition modes: a fixed frame rate mode and a free-run triggering mode. In free-run triggering mode, the camera passively waits for an external trigger signal (e.g., a software command via USB) to capture each frame. Upon receiving a valid trigger, it completes a single acquisition and immediately resumes waiting for the next trigger. There is no fixed time constraint between consecutive triggers, allowing the interval to be arbitrarily set to achieve virtually any acquisition frequency. To ensure proper operation in this mode, the IR, Depth, and RGB sensors must be configured to a common fixed frame rate (e.g., 5, 10, 15, 30, or 60 fps). This setting determines the minimum allowable time between two triggers and thus the maximum effective triggering frequency. As summarized in Table 4-12-1, the camera will only respond to trigger signals that fall within this permissible range. Consequently, any trigger frequency within the valid range can be passively supported. Table 4-12-1 Table of Supported Trigger Configurations
```

3\. #### 4.13 Multi-Camera Synchronization

```
For a multi-camera use case, one camera can be initialized as primary, and the rest configured as secondary. Alternatively, an external signal generator can also be used as the primary trigger with all cameras set to secondary mode. When applying an external sync pulse, the HW SYNC input requires a 100-microsecond positive pulse at the nominal camera frame rate, e.g. 33.33 ms for a 30 Hz frame rate. Inputs are high impedance, 1.8V CMOS voltage levels. However, it is important to make sure to use a high-resolution signal generator. The frequency of the signal generator needs to exactly match the sensor frame rate. For example, if the sensor is set up as 30 FPS, the Set The Camera’s Fixed Frame Rate(fps) Supportable Passive Trigger Interval (ms) Supportable Passive Trigger Frequency (Hz) 60 ≥ 33.4 0 - 30 30 ≥ 66.7 0 - 15 15 ≥ 133.4 0 - 7.5 10 ≥200 0 – 5 5 ≥ 400 0 – 2.5

real frame rate may be 30.015 FPS. You may need to use an oscilloscope to measure the real frame rate and configure the signal generator to the same frequency. For this reason, it may be better to just use one additional camera as the primary sync signal generator. Advantages of multi-camera setup：
```

*   Increase camera coverage in a given space and fill in the occlusions where a

    single camera may have blind spots
*   Capture multiple images of the same scene and scan objects from different

    angles
*   Increase the effective frame rate to higher than 30 FPS when the cameras are

    running at 30 fps. Multi-camera frame synchronization in star topology is supported, including depth image synchronization and RGB image synchronization (typical time difference ≤ 5ms across synchronized multiple cameras, when auto exposure off), using the multi- camera synchronization function. Table 4-13-1 Topologies schematic diagram Star Topology

#### 4.14 Camera Functions

```
**4.14.1 Depth Camera Functions**

Gemini 305 expose the following Depth image settings. Table 4-14-1 Depth camera control Control Description Settings Default Setting Auto Exposure Priority When enabled, exposure is prioritized, allowing the frame rate to be reduced. Disabled, Enabled Enabled Auto Exposure Enables or disables automatic exposure control for the depth camera. Disabled, Enabled Enabled AE Max Exposure(us) Maximum correction value for AE exposure that limits the corresponding frame rate. 1 - 199000 30458(30fps) Mean Intensity Set Point Mean Intensity Set Point for Gemini 0 - 255 60 AE ROI AE ROI allows the user to specify a rectangular region. AE then performs exposure control based on the brightness of this region, enabling the target object to achieve a appropriate brightness. T:0 - 799, B:0 -799 L:0 - 1279, R:0 -1279 (Resolution:1280 x 800) T:0, B:799 L:0, R:1279 (Resolution:1280 x 800) Manual Exposure(1) (us) Sets the fixed exposure time when depth auto exposure is disabled. 1 - 199000 10000 Gain(Gain 1.0=16) Adjusts the gain applied to the depth image when auto exposure is disabled. 16 -248 16
```

4\.

```
> Note: (1) Not supported in Auto Exposure Mode

Definitions: T = Top, L = Left, B = Bottom, R = Right

**4.14.2 Color Camera Functions**

Gemini 305 expose the following Color image settings. Table 4-14-2 Color camera control Control Description Settings Default setting Auto Exposure Priority When enabled, exposure is prioritized, allowing the frame rate to be reduced. Disabled, Enabled Enabled Auto Exposure Enables or disables automatic exposure adjustment. Disabled, Enabled Enabled

AE Max Exposure (100us) Maximum correction value for AE exposure that limits the corresponding frame rate. 1999 303(30fps) AE ROI AE ROI allows the user to specify a rectangular region. AE then performs exposure control based on the brightness of this region, enabling the target object to achieve a appropriate brightness. T:0 - 779, B:0 -779 L:0 - 1279, R:0 -1279 (Resolution:1280 x 800) T:0, B:779 L:0, R:1279 (Resolution:1280 x 800) Manual Exposure(1) (100us) Sets the absolute exposure time when auto-exposure is disabled. 1 - 1999 156 Gain Sets the amount of gain applied to the frame if auto-exposure is disabled. 16 – 128 16 Brightness Sets the amount of brightness applied when auto-exposure is enabled. -64 – 64 0 Auto White Balance Enables or disables the AWB algorithm Disabled, Enabled Enabled White Balance/ K Sets the white balance when AWB is disabled 2800 – 6500 4600 Sharpness Sets the amount of sharpening adjustment applied to the frame 0 – 100 50 Gamma Adjusts gamma correction applied to image frames. Lower gamma values make the scene appear brighter. 100 - 500 300 Saturation Sets the amount of saturation adjustment applied to the frame 0 - 100 64 Contrast Sets the amount of contrast based on the brightness of the scene 0 - 100 50 Hue Sets the amount of hue adjustment applied to the frame -180 – 180 0 Backlight Compensation Sets a weighting amount based on brightness to the frame Disabled, Enabled Disabled Powerline Frequency Specified based on the local power line frequency for flicker avoidance Auto, 50, 60, Disabled Auto

> Note: (1) Not supported in Auto Exposure Mode

Definitions: T = Top, L = Left, B = Bottom, R = Right
```

### 5 Performance

#### 5.1 Depth Performance

```
**5.1.1 Depth Quality Assessment**

Calculation of Depth Accuracy (Z-accuracy): Depth accuracy (Z-accuracy) measures the per-pixel depth accuracy relative to the GT in a single frame depth image, excluding errors due to camera placement. GT is obtained by measuring the distance from depth origin to the reference target. Depth accuracy can be calculated using the following formula: Depth\_accuracy\_Signed = Median (CP\_Length – GT + PP\_Dist) where CP\_Length represents the actual length between the depth origin and a fitted plane along the GT measuring direction, and PP\_Dist denotes the per-pixel distance of the point cloud to the fitted plane. Calculation of Spatial Precision: The spatial precision is calculated as the percentage of the root mean square error (RMS Error) between each valid pixel and the optimal fitting plane compared to the true value (GT). Calculation of Temporal Precision: The temporal precision measures the variation in depth values over time within a ROI. The quality of a depth image can be assessed based on its temporal consistency, high-quality depth images should exhibit smooth and stable over time. This method is defined as the STD of depth values across a specific number of frames (for example, 30). The quantification of temporal noise is carried out on a per-pixel basis, followed by calculating the STD of each pixel over a specified time. Depth Fill Rate Calculation: The fill rate is used to calculate the proportion of valid pixels to total pixels within the target area (ROI region), primarily used to measure the completeness of depth.
```

5\. **5.1.2 Typical depth performance**

```
Typical depth performance for Gemini 305 is shown in the table below: Table 5-1-1 Typical Depth Performance for Gemini 305 Depth Performance Gemini 305 Depth Accuracy ≤±1.8% (1280 x 800 @ 50cm & 90% x 90% ROI) Spatial Precision ≤ 1% (1280 x 800 @ 50cm & 90% x 90% ROI) Temporal Precision ≤ 0.5% (1280 x 800 @ 50cm & 90% x 90% ROI) Fill Rate ≥99.5% (1280 x 800 @ 50cm & 90% x 90% ROI)

> Note:

1. The actual working range and accuracy may vary with the ambient illumination and the objects being measured. 2. The test object is a reflectivity > 80% plane, and the reference range is 81% FOV (81% FOV is the remaining center 81% of the depth map area after cropping 5% from the top, bottom, left and right of the depth map) or 64% FOV (64% = 80% x 80% and of a similar definition).
2. The depth performance of each 3D camera is validated at the production line before shipping to customers. The metrics reflect the depth performance under typical conditions. External impact factors over 3D cameras’ whole lifespan may have significant impacts on their depth performance. 4. Depth evaluation for the Gemini 305 passive RGB stereo vision requires textured or feature-rich objects.
```

#### 5.2 Electrical Performance

```
**5.2.1 Power Supply**

The Gemini 305 requires Type-C power and it is important to ensure that the power output is standard and that the maximum current of the Type-C power port is 0.7A or higher.

**5.2.2 Power Consumption**

Power consumption varies depending on the selected working mode. Table 5-1-1 Gemini 305 typical configuration & tested power consumption Reference Name Gemini 305 Typical configuration Max disparity search range: 128 Depth: 1280 x 800 @ 30 fps Y16 IR Left & IR Right: 1280 x 800 @ 30 fps Y8 RGB: 1280 x 800 @ 30 fps YUYV AE: On Hardware Noise Removal: on Average power consumption 1.57 W

Table 5-1-2 Gemini 305 Max Power Configuration & tested power consumption Reference Name Gemini 305 Max Power Configuration Max disparity search range: 256 Depth: 1280 x 800 @ 30 fps Y16 IR Left & IR Right: 1280 x 800 @ 30 fps Y8 RGB: 1280 x 800 @ 30 fps YUYV AE: On Hardware Noise Removal: on Average power consumption 1.88 W \*Note: The data in the above table are laboratory measurements and are for design reference only.

**5.2.3 Storage and Powered Conditions**

Table 5-1-3 Gemini 305 Storage and Powered Conditions Condition Description Min Max Unit Storage (Ambient), Not Powered Long term storage -10 60 ℃ Short exposure represents temporary max limits acceptable for transportation conditions -20 70 ℃

Humidity Temperature / RH: 40℃ / 90% Ambient, Powered The camera ambient temperature when powered \[1] -10 45 ℃ Backside Case Temperature, Powered The maximum temperature of the backside case occurs when the camera is operated in an ambient temperature of 45°C 0 60 ℃ Notes: \[1] For the Gemini 305, the allowable operating temperature range varies depending on the disparity search mode setting: when the disparity search mode is set to 128, the operating temperature range is -10 °C to 45 °C; when the disparity search mode is set to 256, the operating temperature range is -10 °C to 40 °C. \[2] If users require operation over a wider temperature range, additional thermal management measures need to be evaluated.
```

**5.2.4 ESD Performance**

Table 5-2-3 Gemini 305 ESD Performance Conditions Powered-On Powered-Off Certification Standards Contact Discharge ± 8KV Class A ± 8KV Class A EN 61000-6-2 Air Discharge ± 15KV Class A ± 15KV Class A

#### 5.3 Physical Performance

**5.3.1 Ingress Protection**

Table 5-1 Gemini 305 Ingress Protection Information IP Rating Protection Ability Conditions Reference Standard IP54 ① Prevents solid objects from entering the camera. ② Cannot completely prevent dust from entering the inside of the camera, but the dust that does enter does not affect normal operation. When the Type-C receptacle is mated with a cable rated for IP54 protection and the connector is fully seated. The unmated receptacle is not ingress- protected. Do not operate or unplug under wet conditions. IEC 60529:2013

6. Firmware

#### 6.1 Firmware Update & Cautions

Gemini 305 supports update the firmware via online or location, you can upgrade or downgrade as needed. Please note the following considerations: 1. You can update the firmware in any operating mode or preset; 2. All data streams must be closed when update the firmware; 3. During the firmware update, please ensure that the power supply and cable connections are stable; 4. The camera will automatically reboot after the firmware update is completed. You can also re-plug the cable after completion and reboot it manually.

#### 6.2 How to Update Firmware

The simplest way to update the firmware is through the Orbbec Viewer tool, which supports both manual updates and online updates. For detailed instructions, please refer to the documentation: TBC

#### 6.3 Recovery

Ensure the stability of cable during the update process to avoid any failure. If the update process fails, disconnect the cable, re-connect it, and update the firmware again. If re-burning is unsuccessful, the product may be damaged. Orbbec assumes no liability for any damages or losses resulting from the use of this product.

7. SDK Orbbec SDK is a flexible and modular platform for easy camera setup and runs on multiple platforms with a rich set of APIs. It supports camera access, device setup and configuration, data stream reading, processing, and viewing, RGB-D registration, and frame synchronization. Its functions include:

* Access and control of camera devices
* Control of frame synchronization and alignment
* Acquisition of point cloud data
* Orbbec Viewer for camera testing and evaluation

Please visit Orbbec SDK for the latest SDK.

#### 7.1 Temperature Sensor and Recording

The temperature of camera core components can be obtained, including ASIC temperature, ISP temperature and RGB sensor temperature, through API commands.

8. Use Guidance

#### 8.1 Packing List

Table 8-1-1 Gemini 305 Package List Packaging Type Packaging List Gemini 305 Notes Bulk Camera

Minimum batch packaging quantity: 200pcs Box Camera

Minimum batch packaging quantity: 30pcs 1x USB-C to USB-A cable (1m) 1x Quick Start Guide

#### 8.2 Initialization and Operation

* Connect Gemini 305 via the USB cable to the host PC
* Download Orbbec SDK from Orbbec SDK
* Use Orbbec Viewer to validate that images can be streamed from all sensors

with the following settings: o Depth stream: 1280 x 800(default configuration) o Color stream: 1280 x 800(default configuration) The detailed quick start guide refers to the documentation: TBC If for any reason that the camera is not responding or not being detected, please unplug the cable from the camera and replug the cable into the host PC for resetting the camera state.

9. Regulatory Compliance These products are certified as follows:

#### 9.1 EMC Regulatory Compliance

CE-Declaration FCC part 15 Declaration of Conformity

#### 9.2 Environment Regulatory Compliance

RoHS 2.0, REACH, WEEE, TSCA, TPCH, 94/62/EC RoHS REACH WEEE

TSCA TPCH 94/62/EC

PASS PASS

10. System Integration Guide Use outside of the specified conditions could cause the device to fail and/or function incorrectly. These conditions are applicable for the environment immediately around the device under all operational conditions. When used with an external enclosure, active temperature control and/or other cooling solutions are recommended to ensure the device is maintained within these ranges.

#### 10.1 Installation Recommendations

1. When using external housing around the camera for dust proofing, use foam inserts or rubber gaskets between the front of the camera and the external housing. 2. Avoid external forces applied to the camera chassis during installation process. 3. Disassembling chassis will void the warranty. 4. For the detailed installation reference solution, please refer to Document: TBC

#### 10.2 Heat Dissipation

1. Avoid direct heat source around the camera. 2. Maximizing the space inside the external housing may help lower operating temperature.

#### 10.3 Cable Design Guide

1. It is recommended to use the included USB Type-C cable. If a longer cable is required, use a USB-IF-certified cable that supports both power and data. A cable length of 3.0 m or less is recommended.
2. For the detailed cable design guide reference solution, please refer to Document: TBC
3. Cautions 1. Follow the instructions carefully when operating the camera. Improper handling may lead to damage to the internal components. 2. Do not drop the camera or expose the camera to mechanical stress. 3. Do not attempt to modify the camera as such modifications may cause permanent damage or performance degradation. 4. The temperature of the camera may rise during long periods of use. 5. Do not touch the lens. Fingerprints on the lens may affect image quality. 6. Keep the product beyond the reach of children or animals to avoid accidents. 7. If the computer does not recognize the camera, verify that the cable meets the power and data transfer requirements, then replug it into the USB port to reconnect. Safety and Handling Instructions: ●Avoid powering on the product if any external damage was observed. ●Do not attempt to open any portion of this product. There are no user serviceable parts. ●To maintain compliance and safety standards, do not modify or service the product. Unauthorized modifications or servicing could result in emissions surpassing the Class 1 safety level. ●Only update the camera firmware with official releases that match the specific module SKU and revision to ensure proper functionality and safety.

### Appendix A: Gemini 305 2D Mechanical Diagram

### Development Resources

* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK ROS 1 wrapper](https://github.com/orbbec/OrbbecSDK_ROS1)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
* [Official Gemini 305 documentation](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation)
* [Gemini 305 firmware releases](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305)
* [Gemini 305 CAD files](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Download%20CAD%20Files%20of%20Gemini%20305)
* [Official Gemini 305 datasheet](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)
