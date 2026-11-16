# Orbbec Gemini 335 User Manual

## Orbbec Gemini 335 Stereo Vision Camera with Infrared Imaging

{% embed url="https://openelab.io/products/orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging" %}

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

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/28061441/5eecdaf48460cde5343a9d26a4f189fa2b08dc854bdf65fd2999d97d18fa6898a3842879b4ac8c2065a117e96928706494b137e9330ab0a52a198b6839c1d489104829e8254049202141f1f34e89e26505b26dbebc8fda3ba8af4430009de0b1-1024x731.png)

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

[![Group 10.jpg](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/group-10.jpg)](https://doc.orbbec.com/uploads/images/gallery/2025-12/group-10.jpg)

* The Gemini 330 series integrates Orbbec’s latest sensor technology into the camera. For detailed information, please refer to the [Orbbec Gemini 330 series Datasheet](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\)).

#### **6. Typical Scene Captures using Gemini 330 Series Cameras**

* \*\*Outdoor performance -\*\*Gemini 335/336

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174701/image001-7.png) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174705/image003-7.png) |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |

* **Outdoor performance - Gemini 335L/336L/335Lg/335Le**

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174739/image005-6.png) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174743/image007-5.png) |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |

* **Indoor performance - Gemini 335/336**

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180048/731E5D9D-029B-4550-8964-94D023884644.png) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180040/F4B07029-8606-41a0-B4C7-DC5BEB73334E.png) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |

* **Indoor performance - Gemini 335L/336L/335Lg/335Le**

| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180753/22EE797E-7B89-4611-9E26-091D4FB5E54B.png) | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180746/BF83A51D-7C77-49bd-AE78-5EC63F5F41C3.png) |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20150036/Gemini335lgdocs202410221.png)             | ![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20150047/Gemini335lgdocs202410222.png)             |

* **Tiny objects recognition @ 2m**. The tiny cubic of 3cm x 3cm (the smallest cubic on the right side of the RGB figure below) is clearly visible in point cloud.

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/17131154/1.png)

### Gemini 330 Series Quickstart Guide (USB)

#### **1. What's in The Box for Orbbec Gemini\*\*\*\*335/336?**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20062836/quick-start-1.png)

#### **2. What's in The Box for Orbbec Gemini 335L/336L?**

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20062841/quick-start-2.png)

#### **3. Connect the Orbbec Camera**

* **For** **Orbbec Gemini 335/336**

① Assemble the tripod head with the tripod, and then secure the camera onto the assembled tripod, as illustrated in Step 1 below.

② Use the USB-C to USB-A cable to connect the camera’s Type-C port, as shown in Step 2 below.

③ Connect the USB-A connector to the host using the same USB-C to USB-A cable, as shown in Step 3 below.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20063804/image014.png)

* **For** **Orbbec Gemini 335L/336L**

① Assemble the tripod head with the tripod, and then secure the camera onto the assembled tripod, as illustrated in Step 1 below.

② Use the USB-C to USB-A cable to connect the camera’s Type-C port, as shown in Step 2 below.

③ Connect the USB-A connector to the host using the same USB-C to USB-A cable, as shown in Step 3 below.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20063815/image016-1024x420.png)

#### **4. Get Orbbec Viewer**

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20063843/quick-start-5-1024x187.png)

#### **5. Launch Orbbec Viewer**

1. After starting the Orbbec Viewer, please make sure that the tool recognizes the 3D camera, as indicated by the following image.

Remark:If the camera is not recognized, please check to ensure that the camera and the host are properly connected. You can try disconnecting and then reconnecting the USB cable. If it still isn’t recognized, consider replacing the USB cable or verifying whether the host computer’s power supply meets the required specifications.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064018/image026-1024x548.png)

1. Toggle the ‘**Depth’** button at the top of the tool to start and preview the depth stream.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064029/image028-1024x548.png)

1. Toggle the ‘**Color**‘ button at the top of the tool to start and preview the color stream. The color stream and depth stream will be displayed side by side.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064038/image030-1024x549.png)

1. Toggle the ‘**IR Left’** and **‘IR Right’** buttons at the top of the tool to strat and preview the IR stream.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064049/image032-1024x549.png)

1. Toggle the ‘**IMU’** button at the top of the tool to start and preview the IMU stream.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064058/image034-1024x550.png)

1. Toggle the![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064224/image036.png) button on the top of each window to show the metadata information.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064250/image038-1024x548.png)

1. Toggle the ‘**PointCloud‘** button at the top of the tool to start and preview the 3D point cloud

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064259/image040-1024x549.png)

1. Toggle the **‘Display’** button under the **‘Image View’** menu on the left to start and preview the D2C (depth to color registration) stream. The 3D point cloud and the D2C stream will be displayed side by side.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064310/image042-1024x549.png)

1. The above are relevant operations for Orbbec Viewer version 1.9.4. There may be slight differences in updated versions. For detailed instructions, please refer to the Orbbec Viewer tutorial video below.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064316/image044.png)

[https://www.youtube.com/@Orbbec3d](https://www.youtube.com/@Orbbec3d)

#### **6.** ![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064318/image046.png)**Caution**

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

````
```cpp
#include <iostream>
#include "utils.hpp"
#include "libobsensor/ObSensor.hpp"
#include "libobsensor/hpp/Error.hpp"
```
````

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

````
```cpp
catch(ob::Error &e) {
    std::cerr << "Error: " << e.getMessage() << std::endl;
    return -2;
}
```
````

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

### Stereo 3D Camera

#### **1. Introduction**

A stereo 3D camera is a type of camera equipped with two or more lenses, each with its own image sensor or film frame. This configuration allows the camera to capture images from slightly different angles, simulating the human binocular vision. The primary purpose of a stereo 3D camera is to provide depth perception and create 3D images. The Gemini 330 series 3D cameras combine active and passive stereo vision technologies for seamless operation in both indoor and outdoor conditions.

**Working Principle:**

* **Stereoscopic Vision**: By capturing two images from different perspectives, a stereo 3D camera can calculate the distance to objects in the scene. This process involves measuring the disparity between the two images and using it to triangulate the depth.
* **Image Processing**: Advanced algorithms are used to analyze the images captured by the two lenses. These algorithms match corresponding points in both images to compute depth information, generating a 3D representation of the scene.

For the Orbbec Gemini 330 series cameras, the implementation of the working principle is completed on the Orbbec’s latest custom ASIC.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085557/image001-1.png)

Figure 1. Gemini 335 Stereo 3D Camera

#### **2. Baseline**

The baseline is the distance between the two cameras in a stereo setup, namely, the distance between two IR cameras as shown in Figure 1. A longer baseline increases depth accuracy but also increases the size of the setup. Proper baseline selection is crucial for balancing depth resolution and device compactness.

#### **3. Field of View(FOV)**

The FOV of a 3D camera determines the angular extent of the observable world that can be captured. A larger FOV allows the camera to capture more area but may reduce the resolution.

For the depth is calculated from the left and right images, the FOV of the depth camera is determined by the FOV of the left or right cameras, the measured distance and the baseline. The closer the distance, the smaller the FOV; the further the distance, the closer the FOV of the depth camera is to the FOV of the left or right camera.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085602/image003-1.png)

Figure 2. Depth FOV and IR FOV

Depth Field of View (Depth FOV) at any depth (Z) can be calculated using the following equation:

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085607/image005-1.png)

Definitions:

* cx: X-direction image coordinates of the principle point of the depth image.
* fx: Depth camera focal length.
* width: Depth image width.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085613/image007-1.png)

Figure 3. Gemini 335 Depth FOV for Aspect Ratio = 16:10

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085619/image009-1.png)

Figure 4. Gemini 335 Depth FOV for Aspect Ratio = 16:9

#### **4. Blind Spots**

Blind spots in 3D cameras are areas where the camera cannot capture depth information accurately. These are usually found at the edges of the FOV or the closest distance between the camera and the object. When the object is not visible in either the left or right image, accurate depth information cannot be obtained. The depth camera uses the left camera as the main camera, and the depth blind spots are the green and gray areas shown in the figure below.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085624/image011-1.png)

Figure 5. Depth blind spots

#### **5. Depth Dark Borders**

Depth black edges, or dark borders, in stereo 3D cameras refer to areas in the depth map where depth information is either missing or incorrect. These edges often appear at the boundaries of objects where there is a significant depth discontinuity.

**Cause of Depth Dark Borders**:

* **Baseline**: Stereo 3D cameras work by capturing two images from slightly different perspectives and then calculating the disparity (difference) between these images to estimate depth. These occur when objects seen in one image are not visible in the another due to FOV and baseline limitations, as shown in the green blind spots above.
* **Occlusions**: These occur when parts of one image are not visible in the other due to obstruction by an object. This leads to missing depth information, often resulting in black edges in the depth map.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085631/image013-1.png)

Figure 6. Depth Dark Borders

#### **6. Depth Error**

The errors of stereo 3D cameras are primarily influenced by disparity errors, which are related to the reflectivity of the measured object, image signal-to-noise ratio, algorithm errors, and other factors.

Depth is consequently derived from this equation:

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085635/image015-1.png)

By differentiating the disparity, we can derive the depth error as follows:

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085639/image017-1.png)

It can be seen that the depth error of binocular vision increases parabolically (proportional to the square of the distance) as the distance increases.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085643/image019-1.png)

Figure 7. Depth error(mm) as the distance(mm) increases

### Depth from HDR Imaging

#### **1. Introduction**

For image sensors, the primary challenge lies in capturing both dimly lit indoor scenes and brightly illuminated outdoor settings in the same high-quality image, such as photographing a person standing by the window indoors. Typical image sensors generally adjust exposure or gain to ensure quality imaging in low-light or high-illumination conditions. Robots face various challenges in this regard, such as autonomous mobile robots (AMR) that must operate precisely in environments where sunlight and shadow coexist; robotic vacuum cleaners working near windows face issues with (bright and dark areas in the same view)areas overly bright from sunlight and objects too dark from backlighting. In scenarios where dark and bright areas coexist, using long exposure could result in over-exposure of the bright area, while short exposure might fail to capture details in the darker area. The ORBBEC Gemini 330 Series stereo vision 3D cameras also encounter a similar challenge because their 3D images are calculated from a pair of high-quality, left and right images.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030607/image001.png)

Figure 1. The scene near the windows. Bright and black areas in the same view.

High Dynamic Range (HDR) imaging in computer vision and cinematography is a set of techniques aiming at handling enormously wide exposure range (i.e., images with greater contrast between light and dark) compared to traditional digital imaging technologies, by merging multiple frames. For 3D depth cameras, higher dynamic range means higher depth fill-rate and higher accuracy, significantly enhancing a robot’s obstacle avoidance capabilities. This paper introduces fundamental concepts related to HDR functionality and introduces how HDR is utilized in the ORBBEC Gemini 330 Series cameras.

#### **2. Sensor Settings**

**2.1 Exposure and Gain**

Exposure and gain are two main parameters in photography and imaging technologies that directly affect the quality and clarity of images.

The ORBBEC Gemini 330 series cameras individually control the exposure for visible RGB light and infrared pairs. For Orbbec depth or IR cameras, exposure is measured in microseconds (µs). It ranges from 1 µs to approximately 166 ms. Longer exposure times can enhance image brightness and signal-to-noise ratio (SNR) in low-light environments, thereby improving image clarity, and vice versa. Indoor scenes generally benefit from longer exposure times, while outdoor scenes require much shorter ones.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030622/image003-1024x291.png)

Figure 2. Effect of modifying camera exposure. The larger the exposure, the brighter the images.

Gain adjustment does not affect the amount of light collected by the sensor but amplifies the existing electrical signal. Increasing gain can enhance image brightness in low-light conditions, but also increase noise and reduce image quality. Furthermore, using shorter exposure times combined with higher gain settings can effectively minimize effects such as motion blur caused by rapid movement.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030639/image005-1024x387.png)

Figure 3. Effect of modifying camera gain. The larger the gain, the brighter the images.

**2.2 Over & Under Exposure**

When signals are converted into digital frames, they undergo quantization based on the effective dynamic range of the sensor and the available bit depth. Values falling below the minimum threshold or exceeding the maximum threshold are truncated. This can result in areas of overexposure or underexposure. Overexposed regions are typically displayed as predominantly white, while underexposed areas appear almost black. This issue is prominent in stereo cameras. Figure 6 illustrates the effect of overexposure and underexposure by presenting two bad cases:

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030647/image007-1024x290.png)

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030655/image009-1024x273.png)

Figure 4. Two bad cases of underexposure (top) and overexposure (bottom): left – infrared image, right – depth image.

As described in the commonly used Linear-Signal-Model, light signal undergoes quantization and gets converted into digital frames, while underexposure or overexposure may happen during this process. For a _k_-bit imaging sensor, normally, gray values are expected to range from 0 to 2^k^-1, despite the following unexpected pixels:

* almost black ones, when target surfaces are black, or too far away, etc.
* nearly saturated ones with high-reflective surfaces, etc.

In both cases, rich features on which reliable stereoscopic matching relies are missing, so that the depth result may not be available or may have erroneous values over such areas.

In order to solve the problem of underexposure or overexposure, common methods include: adjusting the camera’s manual exposure, controlling the camera’s automatic exposure configuration, using an HDR camera, or using image enhancement technology to restore the image etc. Image enhancement technology will not be discussed in this paper.

**2.3 Manual Exposure**

Manual exposure is an exposure mode supported by the Gemini 330 series cameras, allowing users to adjust the exposure time and gain to modify image brightness. This method does not automatically adjust based on changes in ambient lighting. It allows users to execute precise exposure control. For instance, to photograph fast-moving objects, one can set a shorter exposure time to prevent motion blur.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030704/image011-1024x290.png)

Figure 5. Same scene captured with short exposure (left) vs longer exposure (right)

You can also set up in the Orbbec viewer under the IR Left/IR Right/Depth control panel. The user needs to turn auto-exposure off before manual adjustment.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030708/image013.png)

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

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030716/image015-1024x284.png)

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030724/image017-1024x286.png)

Figure 7. Effect of auto-exposure indoors(top) and outdoors(bottom): left – infrared image, right – depth image.

By default, Gemini 330 series cameras are configured in auto-exposure mode. Under this mode, the camera will automatically adjust exposure and gain values until the average image intensity reaches a certain preset value. Auto exposure can also be turned on/off in the Orbbec viewer.

Auto exposure criteria can be set up as well, in case the preset average intensity value is not proper for the use case. If the IR images are too dark or too bright, the user can manually change the Mean Intensity Set Point, which can be set under the IR Left/IR Right/Depth control panel.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030728/image019.png)

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

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26032821/%E6%90%9C%E7%8B%97%E9%AB%98%E9%80%9F%E6%B5%8F%E8%A7%88%E5%99%A8%E6%88%AA%E5%9B%BE20240426112616.png)

where \mathscr{W}is the weighting function. In Orbbec’s HDR implementation, only two consecutive frames are chosen, thus equal to 2. And \ mathscr {W}is a simple non-zero check function. So the former can be rewritten as

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26032818/%E6%90%9C%E7%8B%97%E9%AB%98%E9%80%9F%E6%B5%8F%E8%A7%88%E5%99%A8%E6%88%AA%E5%9B%BE20240426112546.png)

To be noted, the aforementioned merging process is implemented in Orbbec-SDK, which can be simply customized.

**3.2 Orbbec Viewer Settings**

To enhance the camera functionality with High Dynamic Range (HDR) capabilities, we have implemented new HDR control features on compatible devices. In the Orbbec Viewer software, users must activate the depth or infrared streams to ensure optimal performance of the HDR function. To accommodate the HDR processing, which involves merging consecutive frames, we have adjusted the device configuration to double the standard frame rate to 60 FPS while maintaining an effective output of 30 FPS due to the HDR synthesis process. Each HDR output is created by merging frames with alternating "high exposure + low exposure" and "low exposure + high exposure" settings. This process introduces a minimal latency of two frames, but the frame rate is still 60FPS.

Users are advised to manually adjust the exposure and gain settings for both high and low exposure frames within the depth control settings to optimize HDR performance. Additionally, for precise monitoring of the camera’s functionality, the HDR-Merge feature can be disabled. This allows for an accurate assessment of the camera’s operational characteristics under varied environmental conditions.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033406/%E6%90%9C%E7%8B%97%E9%AB%98%E9%80%9F%E6%B5%8F%E8%A7%88%E5%99%A8%E6%88%AA%E5%9B%BE20240426113351.png)

Figure 9. Configuring the hardware for HDR in Orbbec Viewer

The camera will initiate streaming, alternating between the two predetermined exposure settings. By opening the metadata panel and pausing the stream, users can access additional details. It is important to note that per-frame metadata provides critical information and is essential for HDR images.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033649/%E6%90%9C%E7%8B%97%E9%AB%98%E9%80%9F%E6%B5%8F%E8%A7%88%E5%99%A8%E6%88%AA%E5%9B%BE20240426113521-1024x444.png)

Figure 10. Examining frame metadata of an HDR stream

The relevant metadata items are:

* **Hdr Sequence Name**– name of the HDR sequence
* **Hdr Sequence Size**– length of the HDR sequence
* **Hdr Sequence Index**– step number inside the HDR sequence of the current frame (zero-based)
* **Exposure**– exposure that was used for the current frame
* **Gain**– gain that was used for the current frame

In order to generate a synthesized depth HDR stream, the HDR Merge post-processing switch needs to be enabled:

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033118/image029.png)

Figure 11. Enabling Depth HDR Merge under post-processing

After activating the HDR Merge feature, the standard depth stream is replaced by an artificially generated HDR depth stream. This modification eliminates flickering in the depth stream; however, flickering in the infrared image stream persists. Since the merging of infrared image frames is a common image processing operation, this functionality has not been incorporated into the OrbbecSDK.

In addition to HDR depth fusion, the SDK provides a simple way of splitting the flickering stream into two individual sequence components by identifying its ID. This can be done using the Sequence ID Filter switch.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033123/image031.png)

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

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033132/image033-1024x315.png)

Figure 13. Depth effect in automatic exposure mode: left – depth image, right –infrared image.

On the other hand, when we turn on the HDR and HDR Merge functions, the depth fill rate in the high-reflection panel area is higher, and the depth value is more accurate.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033144/image035-1024x964.png)

Figure 14. HDR stream in mixed high& low reflection scene: high exposure frame (top), low exposure frame (middle), merged depth (bottom)

One main concern about HDR is its impact on depth accuracy. One example showing the influence is as follows. Pieces of highly reflective panels were stuck to a flat wall about 1043mm away from a Gemini 335 camera, as shown in the upper-left RGB image. The panels are too reflective to form reliable speckles; thus, no valid depth can be estimated in some regions, especially in "High Accuracy" or "Hand" presets, where only reliable estimations remain. The lower left depth image depicts a depth image captured in the "Hand" preset and with Auto Exposure checked.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033657/%E6%90%9C%E7%8B%97%E9%AB%98%E9%80%9F%E6%B5%8F%E8%A7%88%E5%99%A8%E6%88%AA%E5%9B%BE20240426113627-1024x571.png)

Figure 15. Pieces of a highly reflective panel were stuck tightly to a flat wall to test the accuracy.

As a comparison, a depth frame with HDR is also captured in the same scenario, showing higher depth fill-rate (as shown in the lower right of Figure 13) but no decreased accuracy, as shown in Figure 14. Black and red lines are depth values at the same row, with only different HDR settings. The red line with HDR appears to be more accurate.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26033213/image045.png)

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

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07083901/image001.png)

Figure 1: Spectral Curve of Wide-pass Bandpass Filter

b. Short-Pass: This filter allows light shorter than the selected wavelength to pass through while blocking light longer than that wavelength. Common examples include visible light pass filters, as shown in Figure 2.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07083906/image003.png)

Figure 2: Spectral Curve of Visible Light Pass Filter

c. Long-Pass: This filter allows light of wavelengths longer than the selected value to pass through while blocking light of wavelengths shorter than the selected value. Typical examples are IR Pass filters with visible light cut-off, as shown in Figure 3.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07083911/image005.png)

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

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07095556/202406071-1024x289.png)

Figure 4: Infrared and depth images without an IR pass filter

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07095548/202406072-1024x290.png)

Figure 5: Infrared and depth images with an IR pass filter

**5.2 Enhancing Speckle Signal-to-Noise Ratio (SNR)**

The signal-to-noise ratio (SNR) of laser speckles in stereo vision 3D cameras has a great impact on imaging quality. Ambient light introduces background noise to laser speckles, resulting in poor SNR or even overshadowing of speckle brightness. Adding an IR pass filter to eliminate visible light effectively improves the speckle SNR, especially in low-texture scenes, thereby enhancing imaging quality. Figures 6 and 7 show a comparison of before and after adding the IR pass filter. By adding a filter, By adding a filter, the depth performance of the light tube and the cart has significantly improved.

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07095540/202406073-1024x289.png)

Figure 6: Infrared and depth images without an IR pass filter

![Official Orbbec figure from Optical Filters for Stereo Vision 3D Cameras](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07095532/202406074-1024x289.png)

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

![Official Orbbec figure from Depth Quality Metrics](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26045853/image-Depth-quality-metrics1.png)

Figure 1: Reference plane for depth quality assessment.

**2.1 Depth Accuracy**

Depth Accuracy refers to the degree to which the measured depth values correspond to the true distances between objects and the capturing device. High accuracy implies that the depth measurements closely match the GT, minimizing errors in distance estimation. As previously mentioned, a reference plane placed at a known distance from the sensor is recommended in order to simplify the GT of depth data for evaluation, and the distance between the plane and the sensor can be precisely determined using common measuring tools such as laser distance meter or tape measure.

Table 4: Depth accuracy (Signed)

| **Item**           | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Category**       | Depth accuracy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **Purpose/Goal**   | Measure the accuracy of depth images within a specified ROI relative to the GT.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **Target**         | Reference plane\Wall                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Analyzed Image** | Depth image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **ROI**            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Description**    | <p>This metric measures the per-pixel depth accuracy relative to the GT in a single frame depth image, excluding errors due to camera placement. GT is obtained by measuring the distance from the depth origin to the reference target. Depth accuracy can be calculated using the following formula:<br><br>Depth_accuracy_Signed = Median(CP_Length – GT + PP_Dist)<br>where CP_Dist represents the actual length between the depth origin and a fitted plane along the GT measuring direction, and PP_Dist denotes the per-pixel distance of the point cloud to the fitted plane.</p>                    |
| **Pseudo-Code**    | <p>INPUT: Depth_Image, GT<br><br>REMOVE all zeros in Depth_Image<br>COMPUTE Point_Cloud (X,Y,Z matrix) from Depth_Image<br>COMPUTE Fitted_Plane to Point_Cloud<br>REMOVE outliers: all Z values that below percentile 0.5% and above percentile 99.5%<br>COMPUTE the actual length between the depth origin and the Fitted_Plane along the GT vector as CP_Dist<br>COMPUTE distance of all points to the Fitted_Plane as PP_Dist<br>COMPUTE Depth_Error = CP_Dist – GT + PP_Dist<br>COMPUTE Median_Value = 50% percentile value of Depth_Error<br>OUPUT: Depth_accuracy_Signed = 100 * Median_Value / GT</p> |
| **Output Value**   | Depth\_accuracy\_signed                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| **Output Units**   | \[%]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

**2.2 Spatial Precision**

While accuracy concerns the systematic deviation from the true depth, spatial precision relates to the consistency of depth measurements. Spatial precision indicates the noise level of depth data across a planar target. A high spatial precision depth data exhibits low variance in depth values for identical or similar surfaces within the same scene. To assess spatial precision, one can perform measurements of a reference plane at known or controlled locations, calculate the RMS error of the depth values obtained, and compare them against desired precision thresholds or specifications.

RMS error can be expressed in units of distance or disparity, but considering the coupling between depth and noise, it can be normalized by the distance between the camera and the planar target and represented in percentage (%) units.

Table 2 : Spatial Precision

| **Item**       | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Category       | spatial precision                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Purpose/Goal   | Measure the noise level of depth values relative to the best-fit plane.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Target         | Reference plane\Wall                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Analyzed Image | Depth Image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ROI            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                                                                                                                                              |
| Description    | Calculate the RMS of the distance from each valid pixel to the best-fit plane, normalized by the distance from the optical center to the plane, with the RMS Error output expressed as a percentage.                                                                                                                                                                                                                                                                                               |
| Pseudo-Code    | <p>INPUT: Depth_Image<br><br>REMOVE all zeros in Depth_Image<br>COMPUTE Point_Cloud (X,Y,Z matrix) from Depth_Image<br>COMPUTE Fitted_Plane to Point_Cloud<br>REMOVE outliers: all Z values that below percentile 0.5% and above percentile 99.5%<br>COMPUTE distance between the depth origin and the Fitted_Plane as CP_Dist<br>COMPUTE distance of all points to the Fitted_Plane as PP_Dist<br>COMPUTE RMSE = RootMeanSquare of PP_Dist<br>OUPUT: Spatial_precision = 100 * RMSE / CP_Dist</p> |
| Output Value   | Spatial\_precision                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Output Units   | \[%]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

**2.3 Temporal Precision**

Temporal Precision measures the variation in depth values over time within an ROI. The quality of a depth image can be assessed based on its temporal consistency; high-quality depth images should exhibit smooth and stable depth over time. This method is defined as the STD of depth values across a specific number of frames (for example, 30). The quantification of temporal noise is carried out on a per-pixel basis, followed by calculating the STD of each pixel over a specified time.

Table 3: Temporal Precision

| **Item**           | **Description**                                                                                                                                                                                                                                                                                                                                                                |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Category**       | Depth temporal noise                                                                                                                                                                                                                                                                                                                                                           |
| **Purpose/Goal**   | Measure the extent of variation in depth values per pixel over time.                                                                                                                                                                                                                                                                                                           |
| **Target**         | wall                                                                                                                                                                                                                                                                                                                                                                           |
| **Analyzed Image** | N sequential depth images                                                                                                                                                                                                                                                                                                                                                      |
| **ROI**            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                          |
| **Description**    | Per-pixel temporal noise is defined by measuring the STD of depth values for each pixel across N consecutive frames, resulting in a STD matrix. Temporal Noise is defined as the median of the STD matrix as a percentage of the target distance Z. This metric excludes NaN and zero depth data.                                                                              |
| **Pseudo-Code**    | <p>INPUT: N images of Depth_Image, GT<br><br>LOOP for each of N Depth_Image to create Depth_Tensor<br>ASSIGN Depth_Tensor = (Depth_Image,N) //dimension is (width,height,N)<br>REMOVE all zeros from Depth_Tensor<br>COMPUTE STD_Matrix = STD of Depth_Tensor(width,height,all)<br>COMPUTE Median_STD = 50% percentile value of STD_Matrix<br>Output: 100 * Median_STD / Z</p> |
| **Output Value**   | The median value of the STD matrix, divided by distance to wall                                                                                                                                                                                                                                                                                                                |
| **Output Units**   | \[%]                                                                                                                                                                                                                                                                                                                                                                           |

**2.4 Fill Rate**

A high-quality depth image should cover the entire field of view uniformly, without missing regions. Fill Rate measures the proportion of non-zero pixels in a depth image, representing the depth coverage. High fill rate indicates that most scene points have been successfully captured.

Table 5: Fill Rate

| **Item**           | **Description**                                                                                                                                                                                                                                                 |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Category**       | Fill rate                                                                                                                                                                                                                                                       |
| **Purpose/Goal**   | Measure the proportion of valid depth values within a specified ROI.                                                                                                                                                                                            |
| **Target**         | Reference plane\Wall                                                                                                                                                                                                                                            |
| **Analyzed Image** | Depth image                                                                                                                                                                                                                                                     |
| **ROI**            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                           |
| **Description**    | Calculate the ratio of pixels with valid depth values to all pixels within a specified ROI.                                                                                                                                                                     |
| **Pseudo-Code**    | <p>INPUT: Depth_Image<br><br>COMPUTE Total_Num = size(Depth_Image)<br>ASSIGN Valid_Image = Depth_Image<br>REMOVE all zeros from Valid_Image<br>COMPUTE Valid_Num = size(Valid_Image)<br>COMPUTE Fill_Rate = 100 * Valid_Num / Total_Num<br>Output Fill_Rate</p> |
| **Output Value**   | The proportion of valid pixels within the specified ROI.                                                                                                                                                                                                        |
| **Output Units**   | \[%]                                                                                                                                                                                                                                                            |

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

| **Metadata**       | **Definition**                              | **Range**                                                                                                                        |
| ------------------ | ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| timestamp          | exposure end timestamp                      | /                                                                                                                                |
| sensor timestamp   | Exposure center timestamp-1/2 exposure time | /                                                                                                                                |
| frame number       | current frame number                        | /                                                                                                                                |
| auto exposure      | content of AE state                         | <p>[0,1]<br>0 for off, 1 for on</p>                                                                                              |
| exposure           | content of exposure time                    | 1\~19900                                                                                                                         |
| gain               | content of exposure digital gain            | 16\~248                                                                                                                          |
| ae roi left        | ROI AE start pixel X-axis                   | 0\~1278                                                                                                                          |
| ae roi top         | ROI AE start pixel Y-axis                   | 0\~798                                                                                                                           |
| ae roi right       | ROI AE end pixel X-axis                     | 1\~1279                                                                                                                          |
| ae roi bottom      | ROI AE end pixel Y-axis                     | 1\~799                                                                                                                           |
| exposure priority  | Content of AE exposure priority state       | \[0,1]                                                                                                                           |
| hdr sequence name  | User-defined content                        | User-defined content                                                                                                             |
| hdr sequence size  | HDR frame total number                      | <p>[0,2]<br>0 for off, 2 for on</p>                                                                                              |
| hdr sequence index | HDR frame sequence                          | <p>[0,1]<br>0 for the first frame, 1 for the second frame</p>                                                                    |
| laser power        | laser optical power                         | \[0,60,120,240,300,360]                                                                                                          |
| laser power mode   | content of laser switch on or off           | <p>[0,1]<br>0 for off, 1 for on</p>                                                                                              |
| emitter mode       | Reserved                                    | <p>[0,1,2,3]<br>0 – all emitters disabled.<br>1 – laser enabled.<br>2 – auto laser enabled (opt).<br>3 – LED enabled (opt).*</p> |
| Gpio Input Data    | Reserved                                    | Reserved                                                                                                                         |

Table 2: RGB metadata definition

| **Metadata**           | **Definition**                                                                             | **Range**                            |
| ---------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------ |
| timestamp              | <p>335: exposure start timestamp<br>335L: exposure end timestamp</p>                       | /                                    |
| sensor timestamp       | <p>335: Exposure center timestamp<br>335L: Exposure center timestamp-1/2 exposure time</p> | /                                    |
| frame number           | current frame number                                                                       | /                                    |
| auto exposure          | content of AE state                                                                        | \[0,1]                               |
| exposure               | content of exposure time(us)                                                               | \[1,10000]                           |
| gain                   | content of exposure digital gain                                                           | \[0,128]                             |
| auto white balance     | content of AWB state                                                                       | 0 or 1                               |
| white balance          | current AWB color temperature                                                              | \[2800,6500]                         |
| brightness             | current brightness                                                                         | \[-64,64]                            |
| contrast               | contrast                                                                                   | \[0,100]                             |
| saturation             | saturation                                                                                 | \[0,100]                             |
| sharpness              | sharpness                                                                                  | \[0,100]                             |
| backlight compensation | state of backlight compensation enable                                                     | <p>[0,1]<br>0 for off, 1 for on</p>  |
| hue                    | hue                                                                                        | \[-180,180]                          |
| Gamma                  | Gamma                                                                                      | \[100,500]                           |
| power line frequency   | anti-flicker state                                                                         | \[50,60, disable, auto]              |
| low light compensation | state of low light compensation enable                                                     | <p>[0,1]<br>0 for off, 1 for on</p>  |
| manual white balance   | current AWB color temperature set manually                                                 | \[2800,6500]                         |
| actual frame rate      | frame rate set                                                                             | \[5,10,15,30,60]                     |
| ae roi left            | ROI AE start pixel X-axis                                                                  | <p>335 [0,1918]<br>335L [0,1278]</p> |
| ae roi top             | ROI AE start pixel Y-axis                                                                  | <p>335 [0,1078]<br>335L [0,798]</p>  |
| ae roi right           | ROI AE end pixel X-axis                                                                    | <p>335 [1,1919]<br>335L [1,1279]</p> |
| ae roi bottom          | ROI AE end pixel Y-axis                                                                    | <p>335 [1,1079]<br>335L [1,799]</p>  |

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

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26075126/image1234ty.png)

1. Unit: The Default unit is millimeters.

#### **3. Gemini 330 Series System Coordinate**

Gemini 330 series coordinate system reference picture is shown below.

Picture 2: Coordinate system schematic diagram

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22090512/docs20240722-1024x468.png)

The relative position relationship of the coordinate systems' origins is as follows.

Table 1: Relative position of coordinate systems for Gemini 335/336

| **Relative position**                 | **X(mm)** | **Y(mm)** | **Z(mm)** |
| ------------------------------------- | --------- | --------- | --------- |
| Origin of the Depth coordinate system | 0         | 0         | 0         |
| Origin of the Color coordinate system | 14.00     | 0         | 2.02      |
| Origin of the IMU coordinate system   | -0.246    | -0.065    | -16.948   |

Table 2: Relative position of coordinate systems for Gemini 335L/336L

| **Relative position**                 | **X(mm)** | **Y(mm)** | **Z(mm)** |
| ------------------------------------- | --------- | --------- | --------- |
| Origin of the Depth coordinate system | 0         | 0         | 0         |
| Origin of the Color coordinate system | 23.75     | 0         | 0         |
| Origin of the IMU coordinate system   | 7.866     | 1.068     | -14.248   |

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

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104142/image001.png)

2. Click "Next", and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104147/image003.png)

3. Click "I Agree", and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104152/image005.png)

4. Click "Next" again:

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104157/image007.png)

5. Click "Install" and wait for the installation to complete.

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104202/image009.png)

6. After the installation, the files in the Orbbec SDK installation directory are as follows:

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104208/image011.png)

The Orbbec Viewer can be accessed via the desktop shortcut.

#### **2. Linux /Arm64 Installation Guidance**

**2.1 Install via .deb Package**

.deb package download link:[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

OrbbecSDK\_vx.x.x\_amd64.deb is the installation package for Linux x64, and OrbbecSDK\_vx.x.x\_arm64.deb is the installation package for Arm64.

1. On the Linux x64 (Ubuntu) platform, install using the following command:

sudo dpkg -i OrbbecSDK\_v1.x.x\_amd64.deb # Based on the actual version

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104213/image013.png)

2. Check the entire package path of the Orbbec SDK using `dpkg -L orbbecsdk`, while the header files and library files of the Orbbec SDK will be installed in the `/usr/local` path.

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104218/image015.png)

3. Enter `OrbbecViewer` to run the Orbbec Viewer.

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104223/image017.png)

**2.2 Install via Debian Apt Repository**

1. In the terminal, enter the following command to obtain and add the public key used for verification:

wget -O – [http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec\_sdk/pub\_key.pub](http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk/pub_key.pub) | sudo apt-key add –

* Check if the public key was added successfully by entering:apt-key list

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104228/image019.png)

If there is a problem with the host not resolving, try the following command to restart the system DNS resolution service and retry the first command:

```
sudo systemctl restart systemd-resolved
```

2. In the terminal, enter the following command to add the apt source update address:

`echo "deb [http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk](http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk) stable main" | sudo tee /etc/apt/sources.list.d/orbbec-orbbecsdk.list`

3. The following command can be used to query the Orbbec SDK:

`sudo apt update`\
`sudo apt search orbbecsdk`

![Official Orbbec figure from Install Orbbec SDK](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/05/31104231/image021.png)

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-07/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-07/image.png)

#### **4. OS Support**

_**Windows OS**_ – Metadata extraction is supported by Microsoft starting with Windows 10. Check the Windows installation guide for details.

**Other OS –** We use libuvc/libusb as the default backend, which does not require any operation to enable metadata support.

#### **5. Devices Support**

Currently, only the Orbbec Gemini 300 series supports those APIs.

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/image.png)

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/cc1image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/cc1image.png)[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/oL5image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/oL5image.png)

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/ZT6image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/ZT6image.png)

At close range, depth values are more similar. When capturing flat surfaces, false positives may cause lateral depth loss.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/9v4image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/9v4image.png)

**\*\*4.4 FalsePositiveFilter::\*\*TextureSparsityFilter**

\*\*Function:\*\*Filters out erroneous depth in low-texture scenes. \*\*Typical scenarios:\*\*outdoor white walls, non-overexposed sky, etc. \*\*Rule:\*\*Within the depth map ROI, noise regions that satisfy both of the following conditions will be filtered out:

\[if !supportLists]l \[endif]Average depth value of noise region < fptsfMaxNoiseLevel

\[if !supportLists]l \[endif]Pixel area of noise cluster < fptsfMaxSpeckleSize

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/h6himage.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/h6himage.png)

**\*\*4.5 FalsePositiveFilter::\*\*PatternAmbiguityFilter**

\*\*Function:\*\*Filters out erroneous depth in repetitive texture scenes. \*\*Typical scenarios:\*\*fences, building windows, etc. **Rule:** Within the depth map ROI, noise regions that satisfy ALL of the following conditions will be filtered out:

\[if !supportLists]l \[endif]Average depth value of noise region < fppafMaxNoiseLevel

\[if !supportLists]l \[endif]Pixel area of noise cluster < fppafMaxSpeckleSize

\[if !supportLists]l \[endif]Noise cluster width < image width × fppafMaxWidthRatio

\[if !supportLists]l \[endif]Noise cluster height < image height × fppafMaxHeightRatio

\[if !supportLists]l \[endif]Noise Tolerance feature > fppafTolerance

\[if !supportLists]l \[endif]Noise Score feature > fppafScore

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/WC9image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/WC9image.png)

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

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/GWhimage.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/GWhimage.png)[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/jvHimage.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/jvHimage.png)

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

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/03/10115937/DOC202504107.png)

Successful Update: The updated presets will then be displayed in the optional depth preset list.

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/03/10115930/DOC202504108.png)

2. The Optional Depth Preset supports a maximum of three presets at a time. Each update will overwrite the previous optional depth presets.
3. Error Handling:

* If a duplicate preset is imported, a prompt will indicate that a duplicate configuration exists, and only one instance will be applied.

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/03/10115455/DOC202504105.png)

* If the firmware version is unsupported or the imported preset does not match the device, the following error message will appear: "Error! The preset data doesn’t match the device! Please select again."

![Official Orbbec figure from Optional Depth Preset Update (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/03/10115448/DOC202504106.png)

**3.2 How to Update Presets via SDK**

Refer to the sample code:

[GitHub Sample Link](https://github.com/orbbec/OrbbecSDK_v2/blob/main/examples/2.device.optional_depth_presets_update/device.optional_depth_presets_update.cpp)

### Update Firmware (Gemini 330 Series)

#### **1. Device Firmware Mode Introduction**

The Gemini 330 series cameras have two modes. The first is normal mode, where the camera operates normally. The second is recovery mode, where the camera cannot function but can only perform a firmware update. By default, the device will enter normal mode. It will only enter recovery mode when it is unable to enter normal mode.

**1.1 How to Identify the Device Mode**

**1.1.1 Windows System**

In normal mode, the device manager displays the device as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110142/image001-8.png)

In normal mode, the device is displayed as follows when connected to Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110147/image003-8-1024x239.png)

In recovery mode, the device manager displays the device as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110152/image005-7.png)

In recovery mode, the device is displayed as follows when connected to Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110157/image007-6.png)

**1.1.2 Ubuntu System**

In normal mode, the device information is displayed as follows when using the `**lsusb**` command:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110202/image009-6.png)

In normal mode, the device is displayed as follows when connected to the Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110208/image011.gif)

In recovery mode, the device information is displayed as follows when using the `**lsusb**` command:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110213/image013.gif)

In recovery mode, the device is displayed as follows when connected to the Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110219/image015.gif)

**1.2 Notes**

* Ensure the device has a stable power supply and stable communication during the update process.
* The camera firmware includes ISP firmware. ISP firmware will not be updated in recovery mode; it needs to be updated again after entering normal mode.
* If any failure occurs during the update process, you can repeat the update until it is successful.

#### **2. Update Firmware**

**2.1 Online Update via Orbbec Viewer**

1. Open Orbbec Viewer. If firmware updates are available, a notification will appear in the top right corner of the screen, indicating that new firmware is available for update.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110225/image017.gif)

2. Click the notification in the red box as shown above, and the following dialog box will appear.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110231/image019.gif)

3. Select "New Firmware Upgrade".

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110236/image021.gif)

4. Click "Upgrade," and the following dialog box will appear.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110242/image023.gif)

5. Click "Yes."

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110249/image025.gif)

6. Reboot the device.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110256/image027.gif)

7. Confirm the firmware version number after the update.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110302/image029.gif)

**Notes:**

If the update process fails, you can repeat the update until it is successful.

**2.2 Offline Update via Orbbec Viewer**

The difference between offline and online updates is as follows: With online updates, the firmware is automatically downloaded from the server (downloaded to the "output/firmwareFile" directory in Orbbec Viewer), and then the device is updated. However, with offline updates, you manually select the firmware path and then proceed with the update. The interface is as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110308/image031.gif)

After clicking "Upgrade," the subsequent update steps are the same as the online update.

**2.3 Code Sample**

1. The firmware update reference for Orbbec SDK V1.x.x version is available in the sample at the following link:

[https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade](https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade)

2. The firmware update reference for Orbbec SDK V2.x.x version is available in the sample at the following link:

[https://github.com/orbbec/OrbbecSDK\_v2/tree/main/examples/2.device.firmware\_update](https://github.com/orbbec/OrbbecSDK_v2/tree/main/examples/2.device.firmware_update)

#### **3. Handle Update Exception**

If there is a power failure or the USB cable is unplugged during the online update process, the device may enter Recovery mode. In this case, you will need to perform an offline update using the firmware downloaded online. The path to the online firmware download is in the "output/firmwareFile" directory of Orbbec Viewer, for example, on the Windows platform, as shown in the following figure.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110315/image033.gif)

If the device enters Recovery mode but there is no firmware available, please download the firmware from the product’s firmware download page first. Then, follow the offline update method to perform the update.

**Notes: (Very Important)**

In Recovery mode, ISP firmware update is not supported. You need to enter Normal mode and perform the firmware update again to ensure ISP firmware matches the current system. (In Recovery mode, firmware needs to be updated twice.)

#### **4. Update Orbbec Viewer**

If there is a new version of Orbbec Viewer available for update, when opening Orbbec Viewer, there will be a prompt in the top right corner: "A new version of the tool can be updated." Click on this prompt, and it will link to the download directory of Orbbec Viewer on GitHub. Please download the corresponding platform’s Orbbec Viewer.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110320/image035.gif)

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

### Reference Design - Mounting (Gemini 330 Series)

#### **1. Overview**

This document provides the optimal reference mounting design solution for the camera, assisting customers in swiftly implementing it during the product deployment process.

#### **2. Mounting Reference Solution for Gemini 335/336**

**2.1 Product Components**

| Gemini 335                                                                                                                                                                 | Gemini 336                                                                                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115611/202411031.png) | ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115615/202411032.png) |

**2.2 Product Drawing for Gemini 335**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115807/202411033.png)

**2.3 Product Drawing for Gemini 336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115813/202411034.png)

**2.4 Product Interfaces for Gemini 335/336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115820/202411035.png)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the left of the camera,the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port On the right side of the camera, rotate the Sync Port cover to see the Sync Port.

**2.5 Mounting and Fixing Method for Gemini 335/336:**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 5mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120111/202411036.png)

Option B\*\*:\*\*Fix the 3D camera using two M3 thread holes on the rear side,the hole depth is 3.0mm and commended is 0.4Nm

Option C: Fix the 3D Camera using the shape or edges of the metal housing

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120116/202411037.png)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, the FOV viewing angle cannot be blocked;

#### **3. Mounting Reference Solution for Gemini 335L/336L**

**3.1 Product Components**

| Gemini 335L                                                                                                                                                                | Gemini 336L                                                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120428/202411038.png) | ![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120432/202411039.png) |

**3.2 Product Drawing for Gemini 335L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120438/2024110310.png)

**3.3 Product Drawing for Gemini 336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120443/2024110311.png)

**3.4 Procuct Interface for Gemini 335L/336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120450/2024110312.png)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the bottom of the camera,the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. a length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. a length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port at the top side of the camera, remove the Sync Port protective cover to see the Sync Port.

**3.5 Mounting and Fixing Method for Gemini 335L/336L**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 8mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120454/2024110313.png)

Option B\*\*:\*\*Fix the 3D camera using two M4 thread holes on the rear side,the hole depth is 3.0mm and commended is 0.4Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120500/2024110314.png)

Option C: Fix the 3D Camera using the shape or edges of the metal housing

Illustration for 3D camera mounting

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120505/2024110315.png)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, it cannot block the FOV perspective;

#### **4. System Design Requirements**

1. Sealing Requirements

* Use foam padding or silicone seals between the 3D camera and the customer’s device to prevent dust.

2. Lens Requirements

* No additional lenses or covers can be added to the front of the 3D camera.

3. Cooling Requirements

* Connect the 3D camera to external metal components using thermal conductive materials to expand the cooling area. It is recommended to incorporate active cooling with fans.
* The 3D cameras must not be heated by other heat sources.

4. Before customer tooling, please provide structural drawings related to the 3D camera for orbbec’s ME review.

-The next step

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

### Development Resources

* [Official Gemini 330 Series documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)
* [Gemini 330 Series USB datasheet](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\))
* [Gemini 335 CAD files](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))
* [Gemini 330 Series firmware releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))
* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
