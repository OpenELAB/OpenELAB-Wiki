# Orbbec Gemini 2 XL User Manual

### Orbbec Gemini 2 XL Long range with high quality depth data output

{% embed url="https://openelab.io/products/orbbec-gemini-2-xl-long-range" %}

![Official Orbbec Gemini 2 XL Long range with high quality depth data output product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-2XL-1.jpg?v=1781599250)

![Official Orbbec Gemini 2 XL Long range with high quality depth data output product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-2XL-2.jpg?v=1781599250)

![Official Orbbec Gemini 2 XL Long range with high quality depth data output product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-2XL-3.jpg?v=1781599250)

![Official Orbbec Gemini 2 XL Long range with high quality depth data output product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-2XL-4.jpg?v=1781599251)

![Official Orbbec Gemini 2 XL Long range with high quality depth data output product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-2XL-5.jpg?v=1781599250)

![Official Orbbec Gemini 2 XL Long range with high quality depth data output product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-2XL-6.jpg?v=1781599250)

### Gemini 2 XL

Product Overview The Orbbec Gemini 2 XL marks Orbbec’s debut in long-range 3D cameras suitable for outdoor use. The camera is designed with a depth Field of View (FoV) of up to 101° diagonally, and advanced depth processing for conquering complex and demanding application scenarios. Gemini 2 XL is easy to set up and operate with the Orbbec SDK, and the camera delivers extremely accurate and reliable data in various lighting conditions from pitch black to outdoor.

### 1 Product Brief

Product Features

* Global shutter for RGB and

IR cameras

* Wide Field of View at 91° Horizontal

and 66° Vertical

* High quality depth data output

from 0.4m to 20m

* USB 2.0 Type-C & Gigabit Ethernet

data connectivity

* Internal IMU
* Multi-camera synchronization

Parameter Specifications Model G30056-66 /G30056-86 (PoE) VID/PID 0x2BC5/0x0671 Technology Infrared Enhanced Stereo Shutter Type IR: Global Shutter; Color: Global Shutter Wavelength 850nm Mode Resolution FoV FPS Range Format Unbinned Dense Default 1280 x 800 H 91° V 66° 5, 10 0.4m - 20m Optimal Range: 0.40m – 10m Y16/RVL 640 x 400 5, 10 Unbinned Sparse Default 1280 x 800 5, 10 0.4m - 20m Optimal Range: 0.40m – 10m640 x 400 5, 10 Binned Sparse Default 640 x 400 5, 10, 15, 20 Optimal Range: 0.4m – 5.0m RGB\* 1280 x 800 H 94° V 68° 5, 10, 15, 20 RGB888/ MJPEG 1280 x 720 5, 10, 15, 20 800 x 600 5, 10, 15, 20 640 x 400 5, 10, 15, 20 RGB888/ YUYV/ MJPEG640 x 360 5, 10, 15, 20 Depth Accuracy: ≤ 2% (1280 x 800 @ 4m & 81% ROI). The test object has a reflectivity > 80% plane, and the reference range is 81% FoV (81% FoV is the remaining center 81% of the depth map area after cropping 5% of the top and bottom of the depth map). The root mean square of the distance sequence from all valid points in the area to the best-fit point of the fitted plane is calculated. Depending on the application environment, the camera can provide depth measurement data of more than 60m (with a depth unit set to 1mm), and the actual accuracy varies with distance and the object being measured. \* Acquisition of RGB images at 15/20fps is supported only in Binned Sparse Default mode. Parameter Specifications Baseline 100mm IMU 6 DoF; Frequency range: 50-2,000Hz. Data format: float Mirror Mode Supported, non-mirror by default Processing OBox Computing Module Data Connection USB 2.0 USB Type-C/Gigabit Ethernet Operating Modes Unbinned Dense Default: High accuracy and High-density depth data. Unbinned Sparse Default: Balanced depth accuracy and power consumption. Binned Sparse Default: Low power mode, supports 20fps. Power Input DC: 12V/2A PoE+: 802.3at (30W Max) Power Consumption DC: Average < 6W (Peak 12W) PoE: Average < 7W (Peak 14W) Operating Environment 0°C - 40°C, < 90%RH (non-condensing), Indoor/Outdoor Supported Functions D2C, Multi-Camera Sync Dimensions (&#x57;_&#x48;_&#x44;) Camera: 124mm x 29mm x 26mm OBox: 130mm x 22.5mm x 71mm Weight Camera: 152g OBox: 279g Certifications Class 1, RoHS, FCC, CE, Reach Installation Camera: 1 x ¼-20UNC, 2 x M4 OBox: 4 x M3



### 2 Product Specifications

Product Picture

### 3 Product Information

#### 3.1 Product Images

Gemini 2 VL Front View Gemini 2 VL Rear View OBox Top View OBox Bottom View OBox Rear View

Product Information (continued from previous page):

#### 3.3 Product Interfaces

The hardware interfaces of Gemini 2 VL camera and OBox are shown in the figure below. Gemini 2 VL USB2.0 Type-C

#### 3.4 Connection Type

Supported Connection Type Data Transmission 3 Ethernet with PoE \ Ethernet 4 DC USB Type-C USB Type-C 6 DC Ethernet without PoE Ethernet Gemini 2 VL 8-Pin Multi-Camera Synchronization Port OBox Hardware Interfaces

#### 3.2 Product Components

Gemini 2 VL Components

### 4 Software Development Kit (SDK)

Orbbec SDK is a flexible and modular platform for easy camera setup and runs on Linux/Windows with a rich set of APIs. It supports camera access, device setup and configuration, data stream reading, processing, viewing, RGB-D registration and frame synchronization. The functions include:

* Access and control of camera devices.
* Control of frame synchronization and alignment..
* Acquisition of point cloud data.
* Orbbec Viewer for camera testing.

Please check https://www.orbbec.com/developers/orbbec-sdk/ for the latest SDK. Packing List

* Orbbec Gemini 2 XL device (Gemini 2 VL + OBox)
* 12V/2A Power Supply
* USB Type-C T o Type-A Cable (T o Host)
* USB Type-C T o Type-C Cable (Camera to OBox)
* Tripod

### 5 Camera Setup and Operation

The temperature of camera core components – including laser temperature, IR sensor temperature and IMU sensor temperature – can be obtained through API commands. Initialization and Operation

* Connect Gemini 2 XL to the host PC via the USB cable.
* Check both indicators on the camera and validate that

all cameras are enumerated correctly in Windows device manager.

* Download the Orbbec SDK from
* Validate that the cable can stream reliably on all sensors

in the Orbbec Viewer, with the following settings:

* If the camera is not responding or not being detected for

some reason, please unplug all cables from the camera and replug to the host PC to reset the camera state.

* Depth work mode: Unbinned Sparse Default
* Depth camera:1280 x 800@10FPS Y16
* Depth units:1.0
* RGB Camera: 1280 x 800@10FPS MJPEG
* IR Camera:1280 x 800@10FPS Y8
* IMU enabled

Temperature sensor and recording

Use outside of the specified conditions could cause the device to fail and/or function incorrectly. These conditions are applicable for the environment immediately around the device under all operational conditions. When used with an external enclosure, active temperature control and/or other cooling solutions are recommended to ensure the device is maintained within these ranges.

#### 6.1 Installation Recommendations

1. When using an external housing around the camera for dust proofing, use foam inserts or rubber gaskets between the front of the camera and the external housing. 2. Avoid the application of external forces to the camera chassis during the installation process. 3. Disassembling the chassis and mounting brackets will void the warranty.

#### 6.3 Cable Design Guide

There are two types of USB cables for Gemini 2 XL (TYPE-C to TYPE-C cable and TYPE-A to TYPE-C cable). The TYPE-C to TYPE-C cable serves as the connection cable between the Gemini 2 VL and the OBox, with one end connecting to the Gemini 2 VL, and the other end connecting to the Device port (labeled: to Device) of the OBox. The TYPE-A to TYPE-C cable is used as the connection cable between Gemini 2 XL and host computer, one end of which is connected to the Host port (labeled: to Host) interface on OBox, and the other end is connected to the host computer. The two cables are for signal data transmission, not for power supply. Considering the influence of signal quality, the two cables should not exceed 2 meters in a single connection path and should pass the USB eye diagram and EMC test.

### 6 Installation Guide

#### 6.2 Heat Dissipation

1. Avoid any direct heat sources around the camera. 2. Maximizing the space inside the external housing may help lower operating temperature.

Gemini 2 VL Front View

### 7 Product Drawings

Gemini 2 VL Top View Gemini 2 VL Side View Gemini 2 VL Bottom View Gemini 2 VL Rear View OBox Top View OBox Rear View OBox Side View OBox Bottom View

### 8 Multi-Camera

Synchronization Using an 8-pin connector and matching cable, a multi-camera and multi-sensor network can be designed. (Please follow the instructions in the SDK). Gemini 2 XL Multi-camera synchronization Pin sequence diagram

* Increase camera coverage in the given space and fill in the

occlusions where a single camera may have blind spots.

* Capture multiple images of the same scene and scan

objects from different angles.

* Increase the effective frame rate to greater than 30

frames per second (FPS). Each depth camera device is equipped with a synchronization interface that enables multiple camera sychronizations. The use of multiple depth camera devices allows for a wider range of needs, including: Pin Definitions Description Pin\_1 VCC The default is 1.8V. When 3.3V or 5V drive voltage is provided on the VCC interface, the I/O level setting can be adjusted to 3.3V or 5V as required Pin\_2 GPIO\_OUT Synchronization drive signal: Active high. The high-level interval coincides with the IR exposure time. T ypical application is to drive external fill light. Pin\_3 VSYNC\_OUT Synchronous trigger signal: Active high. The high level provides the triggering signal for the secondary devices. Pin\_4 TIMER\_SYNC\_OUT Pulse signal source, reset hardware timestamp of secondary devices. Pin\_5 RESET\_IN Hardware reset signal: Triggers the camera to power down and automatically power up and reset. Detect the input signal: 20Hz / 50% duty cycle / more than 5 consecutive cycles, that is, judged as normal input signal, other signals filtered out; allowed fluctuations for frequency ± 1Hz, duty cycle ± 2%. Pin\_6 VSYNC\_IN Synchronous trigger signal: Active high. Generated for the triggering/sync signal by the primary device, with a duration of 1ms. Pin\_7 TIMER\_SYNC\_IN Hardware timestamp reset signal input, hardware timestamp clearing Pin\_8 GND Ground Synchronization Interfaces of Gemini 2 XL Camera Multi-camera and multi-sensor synchronization in different configurations can be designed with the optional Orbbec Multi-Camera Sync Hub Dev and Multi-Camera Sync Hub Pro accessories.

### 9 Safety and

Handling 1. Follow the camera operation instructions. Improper operation may cause damage to internal components. 2. Do not drop or subject the camera to external force. 3. Do not attempt to modify the camera as modifications may cause permanent damage or inaccuracies. 4. The camera temperature may increase during long periods of continuous usage. 5. Do not touch the lens. Fingerprints on the lens may affect image quality. 6. Keep the product beyond the reach of children or animals to avoid accidents. 7. If the camera is not recognized by the computer, check if the cable meets the power/data transfer requirements and reinsert the USB for reconnection. 8. This product uses a Class 1 laser. Looking at the laser for more than 20s is not recommended. PIN 8 PIN 1

Depth Field of View (Depth FOV) at any distance (Z) can be calculated using the following equation: Definitions: 1. cx = X-direction image coordinates of the main point of the depth image 2. fx = Depth camera focal length 3. width = Depth image width 4. H-FoV = IR H-FoV

> Note:

1. cx, fx, and width parameters are obtained through the SDK depth intrinsic for the relevant camera parameters, and each depth camera parameters are not the same. 2. At different distances, the depth FoV is different. The farther the distance, the greater the depth FoV. 10. Field of View Illustration The image below shows the depth camera field-of-view, or the angles that the sensors “see”. This diagram shows the IR camera.

Term Definition D2C Depth to Color function maps each pixel on a depth map to the corresponding color image according to the intrinsic and extrinsic parameters of depth camera and color camera. Depth Depth video streams are like color video streams except each pixel has a value representing the distance away from the sensor instead of color information. Depth Camera Includes the external interface and the depth imaging module, which is generally composed of the infrared projector, the infrared camera, and the depth computing processor. FOV Field of View (FoV) describes the angular extent of a given scene that is captured by a camera, which can be measured in horizontal, vertical, or diagonal. I2C I2C bus refers to a kind of simple bidirectional two-wire synchronous serial bus developed by Philips. It can be used for transferring information among devices connected to the bus with two wires. IR Camera Infrared camera. IR Flood IR floodlights are used to illuminate the environment. ISP Image signal processor, which is used for image post-processing. MIPI Mobile Industry Processor Interface (MIPI) is an open standard and specification formulated by the MIPI Alliance for mobile application processors. PCBA Circuit board that includes the depth computing processor, memory, and other electronic devices. Point Cloud A point cloud is a discrete set of data points in space. SoC System on Chip, an integrated circuit (IC) that integrates all components of a computing system. TBD To Be Determined. In the context of this document, information will be available in a later revision.

### 11 Glossary of Terms

your sales representative to obtain the latest Orbbec 3D product specifications. Orbbec is not responsible for any users infringing on third party copyright or other rights in use of Orbbec products. In addition, Orbbec does not assume any liability for damages or any losses resulting from the use of this product. All information provided here is subject to change without notice.

### Development Resources

* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK ROS 1 wrapper](https://github.com/orbbec/OrbbecSDK_ROS1)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
* [Official Gemini 2 XL datasheet](https://orbbec.com/wp-content/uploads/2023/12/ORBBEC_Datasheet_Gemini-2-XL.pdf)
