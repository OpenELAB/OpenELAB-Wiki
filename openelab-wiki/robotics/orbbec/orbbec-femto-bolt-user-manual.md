---
description: >-
  Choose Femto Bolt ToF modes, power the USB camera correctly, capture depth
  with Orbbec SDK and plan K4A migration, recording and synchronization.
---

# Orbbec Femto Bolt: ToF depth capture and K4A migration

{% hint style="info" %}
[**Orbbec Femto Bolt ToF Depth Camera on OpenELAB**](https://openelab.io/products/orbbec-femto-bolt-tof-camera)

**Model:** Femto Bolt · **SKU:** `ORBBEC-Femto-Bolt` · **Option:** USB ToF camera with 4K RGB; not Femto Mega, Mega I or an Azure Kinect DK.
{% endhint %}

Femto Bolt provides time-of-flight depth, color and IMU streams over USB. Choose its depth field of view and power arrangement together: high-resolution modes and 4K color are not interchangeable with a restricted USB-powered configuration. This guide establishes one depth stream, then explains recording, calibration and K4A migration boundaries.

## Product overview

The 850 nm indirect time-of-flight (iToF) sensor measures phase-shifted active illumination. It offers narrow and wide depth modes; wider coverage changes resolution, useful distance and exposure timing. Depth processing involves the host, unlike Femto Mega's onboard Jetson processing. The color camera uses rolling shutter. [Femto Bolt datasheet v1.0](https://www.orbbec.com/wp-content/uploads/2023/08/ORBBEC_Datasheet_Femto-Bolt-3.pdf), [current hardware specifications](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications)

The [Femto Mega guide](orbbec-femto-mega-user-manual.md) covers a different powered network camera. The K4A API wrapper is a software migration route, not a statement that Bolt has identical optics, hardware, firmware, connectors or all Azure Kinect behavior.

## Applications

* Indoor volumetric capture and interaction research using wide-FOV depth.
* Narrow-FOV geometry capture where the selected mode's distance and error conditions fit the task.
* RGB-D/IMU recording for offline processing and calibration experiments.
* Adapting an existing K4A application with explicit checks for depth modes, images, timestamps, calibration and separate body-tracking dependencies.

Multipath from corners or reflective surfaces can bias ToF depth even when the image looks continuous. Low return, occlusion, ambient infrared and ambiguous phase can invalidate measurements. Test the actual environment and preserve invalid pixels; spatial smoothing is not independent geometric evidence. [ToF principles and invalidations](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Depth%20Camera%20\(Femto%20Bolt\))

## Specifications

The depth modes below follow the [current official hardware page](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications). Range/error conditions are 850 nm, 15–95% target reflectivity, specified ambient infrared and no multipath; they are not guaranteed for arbitrary materials.

| Depth mode                 | Resolution  | Field of illumination | Listed frame rates                   | Operating range |
| -------------------------- | ----------- | --------------------- | ------------------------------------ | --------------- |
| NFOV unbinned              | 640 × 576   | 75° × 65°             | 5/15/25/30 fps                       | 0.5–3.86 m      |
| NFOV 2 × 2 software binned | 320 × 288   | 75° × 65°             | 5/15/25/30 fps                       | 0.5–5.46 m      |
| WFOV 2 × 2 binned          | 512 × 512   | 120° × 120°           | 5/15/25/30 fps                       | 0.25–2.88 m     |
| WFOV unbinned              | 1024 × 1024 | 120° × 120°           | 5/15/25 fps on current hardware page | 0.25–2.21 m     |
| Passive IR                 | 1024 × 1024 | Not a depth mode      | 5/15/25/30 fps                       | No depth range  |

The older v1.0 PDF lists 30 fps for WFOV unbinned, while the current hardware page stops at 25 fps. **Use an actually enumerated profile; this guide starts in NFOV at 30 fps and does not promise WFOV 1024 × 1024 at 30 fps.**

| Parameter                               | Femto Bolt                                                                                                             |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Depth typical systematic / random error | <11 mm + 0.1% of distance / standard deviation ≤17 mm, under the stated test conditions                                |
| Color                                   | Up to 3840 × 2160 MJPEG, 30 fps; 16:9 FOV 80° × 51°; rolling shutter                                                   |
| IMU                                     | ICM-40608 according to current hardware page; six-axis data, 50–2000 Hz supported range                                |
| Host connection                         | USB 3.2 Gen 1 Type-C                                                                                                   |
| Required supply provision               | Official supplied 12 V/2 A DC adapter, or correctly negotiated 5 V/3 A USB-C source for supported USB-powered profiles |
| Peak power, current hardware page       | 8.7 W with external DC + USB data; 7.7 W with USB power/data                                                           |
| Ambient / humidity                      | 10–25 °C / 8–90% RH, noncondensing                                                                                     |
| Current hardware-page dimensions / mass | 115.30 × 64.95 × 40.26 mm / 348 g                                                                                      |
| Legacy PDF nominal size / mass          | 115 × 40 × 65 mm in its axis order / 335 g; use actual mechanical revision for bracket design                          |

The legacy PDF and current hardware page differ in dimension ordering, mass and some mode limits. Keep those revisions visible. The complete set of mode/exposure tables is linked above; NFOV and binned WFOV have 12.8 ms acquisition cycles, versus 20.3 ms for unbinned WFOV in the hardware timing table.

## Hardware and connections

![Official Orbbec Femto Bolt rear connections and power indicator](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033336/image011-1-e1701920252294.png)

Official Orbbec hardware-reference diagram: 1 power LED, 2 synchronization cable, 3 supplied-adapter power lead, 4 USB-C data cable. The sync cable is optional for this single-camera procedure.

### Supplied DC power is the baseline setup

Use the original matching **12 V/2 A adapter** and power lead plus a separate USB 3 data cable. The public hardware page specifies a 5.5 mm outer/2.1 mm inner barrel connector, but connector size alone does not establish polarity or adapter compatibility. Retain the supplied adapter rather than choosing a substitute from diameter alone. [Datasheet power scope](https://www.orbbec.com/wp-content/uploads/2023/08/ORBBEC_Datasheet_Femto-Bolt-3.pdf#page=3), [DC connector drawing](https://raw.githubusercontent.com/orbbec/OrbbecHardware/main/Femto%20Bolt/04_connector%20specification/041-DC_Female.pdf)

The older hardware page mentions ≥1.5 A cable capability, while the numerical supply specification is **USB-C 5 V/3 A**. Use the stricter supply requirement for USB-only evaluation. The legacy USB-powered mode footnote restricts depth/IR to **640 × 576 and below** and color to **1920 × 1080 and below**; use external DC for full-feature evaluation rather than assuming a USB-C plug authorizes all modes. Two ordinary USB-A host ports are not a substitute for the correct supply.

Connect directly before adding extenders. A flashing amber power indicator means insufficient power; flashing white indicates no valid USB 3 data connection; solid white indicates normal powered operation. Remove protective optical film and leave ventilation/thermal channels open. [Setup and indicators](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)

### Synchronization connector: retain the source's viewing convention

The public sources use conflicting pin-number conventions:

| Signal                | Legacy datasheet v1.0 rear-view numbering | Current multi-device article numbering |
| --------------------- | ----------------------------------------- | -------------------------------------- |
| GND                   | 1                                         | 8                                      |
| TIMER/TIME\_SYNC\_IN  | 2                                         | 7                                      |
| VSYNC\_IN             | 3                                         | 6                                      |
| RESET\_IN             | 4                                         | 5                                      |
| TIMER/TIME\_SYNC\_OUT | 5                                         | 4                                      |
| VSYNC\_OUT            | 6                                         | 3                                      |
| GPIO\_OUT             | 7                                         | 2                                      |
| SYNC\_VCC             | 8                                         | 1                                      |

This reversal can result from connector/view conventions, but the reviewed text does not establish an unambiguous wiring crosswalk for the physical unit. **Do not make a custom sync harness from this table.** Use an exact-model assembled accessory and confirm the connector drawing/pin-1 datum before external wiring. The logic reference defaults to **1.8 V**, with supported 3.3/5 V reference arrangements; it is not a 12 V input. The multi-device article describes rising-edge triggers longer than 1 ms at exact supported rates. Single-camera capture requires no sync cable. [Legacy p.8](https://www.orbbec.com/wp-content/uploads/2023/08/ORBBEC_Datasheet_Femto-Bolt-3.pdf#page=8), [multi-camera article](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Synchronize%20Multiple%20Femto%20Bolt%20Devices)

For multiple ToF cameras, coordinate exposure timing as well as frame timestamps to reduce optical interference. The documented stagger guidance uses at least **160 μs** between exposure starts; use the exact mode/exposure conditions and the supported sync utility instead of treating that number as a universal trigger period.

## Software and development resources

Use [**Orbbec SDK v2.10.6**](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6) with matching Viewer. The pinned support table lists Femto Bolt minimum firmware **1.1.2**, recommended **1.1.3**. Keep SDK extension/depth-engine files with the executable as the package requires; these are material dependencies, not optional images. On Linux, OpenGL context/driver setup affects host depth-engine initialization. [Support matrix](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/README.md#14-supported-devices), [known issues](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Known%20Issues%20and%20Troubleshooting%20for%20Femto%20Bolt)

### K4A migration and body tracking

For a new application use the native SDK path below. For an existing K4A application use the [official wrapper `v2-main` branch](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/tree/v2-main), whose device table explicitly includes Bolt. Keep one consistent set of headers, libraries, dependencies and calibration APIs. A legacy SDK v1 wrapper build is a different deployment. Recheck image format/stride, timestamps, distortion and depth-to-color transforms rather than replacing a library and assuming identical results.

Microsoft Body Tracking is a separate package/model/runtime with separate license and GPU/driver conditions; Orbbec SDK availability does not include it. Validate skeleton software only after the sensor stream works. The wrapper and third-party depth engine also have their own notices; source availability does not relicense bundled components. [Migration guide](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Access%20AKDK%20Application%20Software%20with%20Femto%20Bolt)

### Calibration, recording and playback

Read calibration from each device. Apply the SDK's supported transformations between depth, RGB and IMU frames; optical X is right, Y down, Z forward, while a robot/world transform is an additional calibration. Keep device and host timestamp domains distinct.

The K4A recorder stores Matroska `.mkv` tracks for color/depth/IR/IMU and calibration attachments. Track index is not fixed: inspect track tags/UIDs before extracting depth. Generic video decoding can rescale or reinterpret a 16-bit depth track, so use the playback API when preserving metric data. Record a short clip, reopen it and compare metadata, frame count and calibration before building an unattended recorder. [Recording format](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Wrapper%20Recording%20File%20Format%20\(Femto%20Bolt\)), [calibration API guide](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Use%20Azure%20Kinect%20Calibration%20Functions)

## Getting started

### First narrow-FOV depth stream

1. Put Bolt on a stable mount facing a diffuse matte target about **1 m** away. Remove optical protective film, keep the thermal channel open and leave synchronization disconnected.
2. Connect the supplied matching DC adapter and the USB 3 data cable directly to the host. Wait for boot to settle. Check solid white power status rather than proceeding through an amber underpower indication.
3. Install the host-architecture SDK v2.10.6 package and matching Viewer. Confirm **Femto Bolt**, serial and firmware; compare the installed version against the exact support table before deciding whether an update is needed.
4. Open Viewer and choose **NFOV unbinned**, **640 × 576 Y16**, **30 fps**, depth alone. Select the actual enumerated mode/profile if the UI labels differ by release.
5. Inspect the target and frame timestamps. Add 1080p color at an advertised profile only after depth is stable. Do not begin with all streams at maximum bandwidth.
6. Stop streams cleanly, save the profile/firmware/scale and close Viewer before custom code. For an existing K4A deployment, the official K4A Viewer path is **Open Device → Start** after the matched wrapper installation.

**Expected result:** Viewer identifies Bolt and shows a stable narrow-FOV depth plane with plausible metre-scale distance. This is the stream check; it does not prove ToF accuracy, successful body tracking or multi-camera synchronization. [Official setup](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)

### Original example: measure a central patch in millimetres

After Viewer works, close it so that one application owns the camera. This example targets **Orbbec SDK v2.10.6**, one connected camera and **Y16 depth only**. It requests an explicit profile, samples the central 10% × 10% patch, excludes invalid zero samples and reports the median every ten received frames. It deliberately does not turn one center pixel into an obstacle-clearance decision. The SDK's depth scale converts stored values to millimetres; timestamps are device microseconds. [API headers and release](https://github.com/orbbec/OrbbecSDK_v2/tree/v2.10.6/include/libobsensor/hpp)

Save this as `roi_depth.cpp`:

```cpp
#include <libobsensor/ObSensor.hpp>
#include <algorithm>
#include <cstdint>
#include <cstring>
#include <iostream>
#include <memory>
#include <stdexcept>
#include <string>
#include <vector>

int main(int argc, char **argv) {
    try {
        if(argc != 5) {
            std::cerr << "Usage: roi_depth WIDTH HEIGHT FPS usb|net\n";
            return 2;
        }
        const int width = std::stoi(argv[1]);
        const int height = std::stoi(argv[2]);
        const int fps = std::stoi(argv[3]);
        const bool network = std::string(argv[4]) == "net";
        if(width < 10 || height < 10 || fps <= 0 ||
           (!network && std::string(argv[4]) != "usb")) return 2;
        ob::Context context;
        context.enableNetDeviceEnumeration(network);
        auto devices = context.queryDeviceList();
        if(devices->getCount() != 1) {
            std::cerr << "Connect exactly one supported camera on this test host.\n";
            return 3;
        }
        auto device = devices->getDevice(0);
        auto info = device->getDeviceInfo();
        std::cout << info->getName() << " serial=" << info->getSerialNumber()
                  << " firmware=" << info->getFirmwareVersion() << '\n';
        ob::Pipeline pipeline(device);
        auto profiles = pipeline.getStreamProfileList(OB_SENSOR_DEPTH);
        auto profile = profiles->getVideoStreamProfile(width, height, OB_FORMAT_Y16, fps);
        auto config = std::make_shared<ob::Config>();
        config->enableStream(profile);
        pipeline.start(config);
        int received = 0;
        for(int attempt = 0; attempt < 120 && received < 60; ++attempt) {
            auto frames = pipeline.waitForFrameset(1000);
            if(!frames) continue;
            auto depth = frames->getDepthFrame();
            if(!depth || depth->getDataSize() < static_cast<uint32_t>(width * height * 2)) continue;
            ++received;
            const auto *bytes = static_cast<const uint8_t *>(depth->getData());
            std::vector<uint16_t> valid;
            const int x0 = width * 45 / 100, x1 = width * 55 / 100;
            const int y0 = height * 45 / 100, y1 = height * 55 / 100;
            for(int y = y0; y < y1; ++y) for(int x = x0; x < x1; ++x) {
                uint16_t value;
                std::memcpy(&value, bytes + 2 * (y * width + x), sizeof value);
                if(value != 0) valid.push_back(value);
            }
            if(received % 10) continue;
            std::cout << "frame=" << depth->getIndex()
                      << " timestamp_us=" << depth->getTimeStampUs()
                      << " valid_roi=" << valid.size() << '/' << (x1-x0)*(y1-y0);
            if(valid.empty()) std::cout << " median_mm=invalid\n";
            else {
                auto middle = valid.begin() + valid.size()/2;
                std::nth_element(valid.begin(), middle, valid.end());
                std::cout << " median_mm=" << *middle * depth->getValueScale() << '\n';
            }
        }
        pipeline.stop();
        if(received < 60) { std::cerr << "Insufficient depth frames\n"; return 4; }
        return 0;
    } catch(const ob::Error &e) {
        std::cerr << "SDK: " << e.getMessage() << '\n';
        return 1;
    } catch(const std::exception &e) {
        std::cerr << e.what() << '\n';
        return 2;
    }
}
```

Use an extracted Linux v2.10.6 SDK package matching the host architecture; `SDK_ROOT` below is the **absolute directory you extracted**, containing `include` and `lib`. Save this `CMakeLists.txt` beside the source:

```cmake
cmake_minimum_required(VERSION 3.10)
project(roi_depth LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 11)
find_package(OrbbecSDK REQUIRED)
add_executable(roi_depth roi_depth.cpp)
target_link_libraries(roi_depth PRIVATE ob::OrbbecSDK)
```

```bash
export SDK_ROOT=/absolute/path/to/extracted/OrbbecSDK
cmake -S . -B build -DOrbbecSDK_DIR="$SDK_ROOT/lib"
cmake --build build --config Release
# Keep the SDK extensions alongside the executable when supplied in the package.
cp -R "$SDK_ROOT/lib/extensions" build/
LD_LIBRARY_PATH="$SDK_ROOT/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}" ./build/roi_depth 640 576 30 usb
```

The package layout and imported CMake target follow the [v2.10.6 development guide](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/docs/tutorial/installation_and_development_guide.md). If an archive places its CMake config elsewhere, point `OrbbecSDK_DIR` at the directory actually containing that config. Do not mix headers and libraries from different SDK releases.

**Expected result:** the process prints six measurement records and exits successfully after receiving 60 depth frames. Each record includes a frame index, `timestamp_us`, valid sample count and `median_mm`; a diffuse target at about 1 m should give a plausible distance near its measured plane position. Those are expected results, not recorded measurements. An unsupported-profile error means enumerate/select a profile the device actually advertises; do not substitute a color format or interpret compressed depth bytes as Y16. Return code 3 means camera selection was ambiguous; 4 means too few frames arrived. A full invalid patch is reported explicitly rather than treated as zero metres.

## Troubleshooting and FAQs

| Symptom                                      | Ordered checks and recovery                                                                                                         |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Amber power indication                       | Restore supplied adapter/cable, check connection and avoid host-only USB-A power assumptions                                        |
| White flashing/no USB 3                      | Check cable and port negotiation, direct connection and other device owners; test a known-good USB 3 cable                          |
| Color works but depth fails on Linux         | Check matched SDK extension/depth-engine files, graphics driver/OpenGL availability and context ownership before changing firmware  |
| Headless capture fails                       | Consult the release's depth-engine/OpenGL requirements; a camera enumerating does not establish a working headless graphics context |
| Depth bends near corners/reflective surfaces | Suspect multipath or mixed pixels, change scene/angle and compare raw depth; filtering cannot establish true geometry               |
| Timestamps change after controls             | Set exposure/control properties outside the capture loop and allow settling; distinguish device capture time from host arrival      |
| Another application cannot open device       | Close Viewer/Camera apps and release the device; one application owns the stream path                                               |
| Firmware operation interrupted               | Maintain stable DC/USB, use the exact Bolt image and official Viewer recovery path; reopen and read back version after reboot       |

**Can I use a normal USB-C connection for every mode?** No. Supply negotiation and the USB-powered profile limits matter. Use the supplied external DC baseline for full-feature commissioning.

**Can I copy Azure Kinect sync wiring?** No. Bolt uses an 8-pin interface, and even the Orbbec sources reverse numbering conventions. Resolve the physical connector view before a custom harness.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                        | Purpose                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| [Bolt datasheet v1.0 PDF](https://www.orbbec.com/wp-content/uploads/2023/08/ORBBEC_Datasheet_Femto-Bolt-3.pdf)                                                                                                                                  | Power, acquisition, physical interfaces and legacy sync-view reference                         |
| [Current hardware/mode reference](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications)                                                                                          | Current dimensions, operating modes, indicators and thermal conditions                         |
| [2D mechanical PDF](https://raw.githubusercontent.com/orbbec/OrbbecHardware/main/Femto%20Bolt/01_2D%20PDF/Femto%20Bolt.pdf) / [3D STEP](https://raw.githubusercontent.com/orbbec/OrbbecHardware/main/Femto%20Bolt/02_3D%20STP/Femto%20bolt.stp) | Official CAD resources, verify revision before bracket tooling                                 |
| [Sync connector drawing](https://raw.githubusercontent.com/orbbec/OrbbecHardware/main/Femto%20Bolt/04_connector%20specification/042-Sync_Female.pdf)                                                                                            | Physical connector specification; does not by itself resolve competing functional numbering    |
| [Firmware](https://github.com/orbbec/OrbbecFirmware/releases/tag/Femto-Bolt-Firmware) / [update procedure](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Update%20Femto%20Bolt%20Firmware)                         | Exact-model firmware, supported recovery and version readback                                  |
| [SDK v2.10.6](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6) / [K4A wrapper](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/tree/v2-main)                                                                                        | Native and compatibility development paths                                                     |
| [Official Bolt document center](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation)                                                                                                                                     | Full setup, theory, transforms, recording/playback, IMU, migration and synchronization readers |

### Extended official documentation

These official readers retain the detailed model/concept/sample paths. Use the model and release boundaries above before adapting an advanced example.

| Official reader                                                                                                                                                                                                                                  | Relevant guide section             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [Orbbec GMSL Cameras Supported Hosts and System Requirements](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20&%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements) | Software and development resources |
| [Find and Open Femto Bolt Devices](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Find%20and%20Open%20Femto%20Bolt%20Devices)                                                                                        | Software and development resources |
| [About Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/About%20Femto%20Bolt)                                                                                                                              | Product overview                   |
| [Orbbec Femto Bolt Documentation](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation)                                                                                                                                    | Software and development resources |
| [Femto Bolt Data Recording](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Data%20Recording)                                                                                                          | Software and development resources |
| [K4A Viewer for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt)                                                                                                        | Software and development resources |
| [Orbbec SDK and K4A Wrapper Download (Femto Bolt)](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20K4A%20Wrapper%20Download%20\(Femto%20Bolt\))                                                  | Downloads and technical documents  |
| [Orbbec SDK and Orbbec SDK K4A Wrapper (Femto Bolt)](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20Orbbec%20SDK%20K4A%20Wrapper%20\(Femto%20Bolt\))                                            | Software and development resources |
| [Update Femto Bolt Firmware](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Update%20Femto%20Bolt%20Firmware)                                                                                                        | Troubleshooting and FAQs           |
| [Image Transformation with Azure Kinect DK](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Image%20Transformation%20with%20Azure%20Kinect%20DK)                                                                      | Software and development resources |
| [Record Multi-Device Synchronized Data with Femto Bolt Recorder](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Record%20Multi-Device%20Synchronized%20Data%20with%20Femto%20Bolt%20Recorder)                        | Hardware and connections           |
| [Femto Bolt 3D Camera SDK System Requirements](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%203D%20Camera%20SDK%20System%20Requirements)                                                              | Software and development resources |
| [Use Azure Kinect Calibration Functions](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Use%20Azure%20Kinect%20Calibration%20Functions)                                                                              | Software and development resources |
| [Get IMU Data from Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Get%20IMU%20Data%20from%20Femto%20Bolt)                                                                                                | Software and development resources |
| [Femto Bolt Comparison with Azure Kinect DK](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Comparison%20with%20Azure%20Kinect%20DK)                                                                  | Software and development resources |
| [Coordinate Systems (iToF Camera)](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Coordinate%20Systems%20\(iToF%20Camera\))                                                                                          | Hardware and connections           |
| [Generate Your First Femto Bolt Application](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Generate%20Your%20First%20Femto%20Bolt%20Application)                                                                    | Getting started                    |
| [K4A Wrapper Recording File Format (Femto Bolt)](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Wrapper%20Recording%20File%20Format%20\(Femto%20Bolt\))                                                        | Software and development resources |
| [Set up Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)                                                                                                                          | Getting started                    |
| [Access AKDK Application Software with Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Access%20AKDK%20Application%20Software%20with%20Femto%20Bolt)                                                      | Software and development resources |
| [K4A Viewer for Femto Bolt Recorder](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt%20Recorder)                                                                                    | Software and development resources |
| [Depth Camera (Femto Bolt)](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Depth%20Camera%20\(Femto%20Bolt\))                                                                                                        | Software and development resources |
| [Get Image Data from Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Get%20Image%20Data%20from%20Femto%20Bolt)                                                                                            | Software and development resources |
| [Azure Kinect Playback API](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Azure%20Kinect%20Playback%20API)                                                                                                          | Software and development resources |
| [Set up Cameras for External Synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)                                                                                   | Hardware and connections           |
| [Femto Bolt Device Synchronization](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Device%20Synchronization)                                                                                          | Hardware and connections           |
| [Femto Bolt Hardware Specifications](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications)                                                                                        | Hardware and connections           |
| [Synchronize Multiple Femto Bolt Devices](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Synchronize%20Multiple%20Femto%20Bolt%20Devices)                                                                            | Hardware and connections           |
| [Regulatory Compliance and Certificates (Femto Bolt)](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Regulatory%20Compliance%20and%20Certificates%20\(Femto%20Bolt\))                                                | Downloads and technical documents  |
| [Known Issues and Troubleshooting for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Known%20Issues%20and%20Troubleshooting%20for%20Femto%20Bolt)                                                        | Troubleshooting and FAQs           |
| [Using Orbbec SDK K4A Wrapper](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Using%20Orbbec%20SDK%20K4A%20Wrapper)                                                                                                  | Software and development resources |

## References and validation

Reviewed **24 November 2026**, using the current official hardware/setup articles, model datasheet v1.0, public connector/CAD repository and SDK v2.10.6 headers/support matrix. Source differences in mass, dimensions, mode rate and synchronization numbering are explicitly retained; unverified high-rate or custom sync commissioning is not included. No public full hardware schematic was found.

The original procedure/code is source reviewed. **SDK execution, camera tests, firmware updates and body-tracking tests were not run.** Official illustrations/files retain their owners' rights; SDK/wrapper and bundled-component licenses are separate.

### Reviewed engineering reference chapters

The following chapters preserve the existing wiki’s detailed engineering reference: specifications, calibration and coordinate concepts, metadata, filter behavior, source examples, installation procedures, troubleshooting and manufacturer illustrations. They complement the current commissioning guide above. Revision notes beside affected chapters separate historical SDK or host examples from the model-specific power, firmware and first-result path. No historical command, example output or photograph is a claimed test on this unit.

#### Orbbec Femto Bolt 4K RGB + ToF Depth Camera for AI & Robotics <a href="#orbbec-femto-bolt-4k-rgb--tof-depth-camera-for-ai-and-robotics" id="orbbec-femto-bolt-4k-rgb--tof-depth-camera-for-ai-and-robotics"></a>

[https://openelab.io/products/orbbec-femto-bolt-tof-camera](https://openelab.io/products/orbbec-femto-bolt-tof-camera)

#### About Femto Bolt <a href="#about-femto-bolt" id="about-femto-bolt"></a>

_Reviewed source:_ [_About Femto Bolt_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/About%20Femto%20Bolt)_. Manufacturer figures and source examples retain their original attribution and rights._

![Official Orbbec Femto Bolt figure from About Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/01060404/e7c9c2844d7c908fa6a25a2f96150152.png)

Femto Bolt is an advanced iToF 3D camera jointly developed by Orbbec and Microsoft. The depth camera uses Microsoft’s latest advanced ToF sensing technology and has a working mode and performance that is completely consistent with the Microsoft AKDK depth camera.

The Femto Bolt 3D camera integrates multiple sensing methods including multi-mode depth camera, color video camera and inertial sensor, and can simultaneously realize data transmission and power supply to the camera through a single USB Type-C connection. At the same time, Microsoft recommends using Femto Bolt as an alternative to Azure Kinect DK. For details, please refer to:

[https://techcommunity.microsoft.com/t5/mixed-reality-blog/microsoft-s-azure-kinect-developer-kit-technology-transfers-to/ba-p/3899122](https://techcommunity.microsoft.com/t5/mixed-reality-blog/microsoft-s-azure-kinect-developer-kit-technology-transfers-to/ba-p/3899122)

The Femto Bolt development environment consists of several SDKs:

* Orbbec SDK K4A Wrapper or Orbbec SDK for accessing the device.
* Human Skeleton Tracking SDK for tracking 3D human bodies.

In addition, Cognitive Vision services can be used with the device RGB camera. The system architecture diagram using Orbbec SDK K4A Wrapper is as follows:

![Official Orbbec Femto Bolt figure from About Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/01060358/dd0e36792765553fa0cdcdbd798d38f5.png)

The system architecture diagram using Orbbec SDK directly is as follows:

![Official Orbbec Femto Bolt figure from About Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/01060355/ac22c1d766497ee47c75175da2a36ae4.png)

Note: Using only Orbbec SDK without Orbbec SDK K4A Wrapper cannot use AKDK’s skeleton tracking algorithm.

#### 1. Orbbec SDK and Orbbec SDK K4A Wrapper <a href="#id-1.-orbbec-sdk-and-orbbec-sdk-k4a-wrapper" id="id-1.-orbbec-sdk-and-orbbec-sdk-k4a-wrapper"></a>

Orbbec Femto Bolt is a reliable alternative product to Microsoft Azure Kinect DK. We provide two SDKs for this product: Orbbec SDK and Orbbec SDK K4A Wrapper.Since Orbbec cannot provide upgrades and maintenance of the original AKDK development tools, from a long-term perspective, we recommend that you try and use Orbbec SDK that Orbbec has been maintaining and updating as soon as possible. Using Orbbec SDK with Femto Bolt will give you richer and more powerful features.To help users who have developed applications using K4A get started with Orbbec Femto Bolt more quickly, and achieve seamless replacement of Microsoft AKDK. On top of Orbbec SDK, we encapsulated Orbbec SDK K4A Wrapper that is maximally compatible with K4A API. Using this Wrapper, users basically don’t need to modify their application code.Orbbec SDK and Orbbec SDK K4A Wrapper provide access to complete Femto Bolt hardware sensor and device configuration.For more information on Orbbec SDK and Orbbec SDK K4A Wrapper, please refer to [Using Orbbec SDK K4A Wrapper](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Using%20Orbbec%20SDK%20K4A%20Wrapper)

**1.1 Orbbec SDK Features**

Orbbec SDK is the native SDK for Orbbec Femto Bolt and can use all the features of Femto Bolt:

* Depth camera access, resolution and frame rate control (including passive IR mode)
* RGB camera access, resolution, frame rate and image effect control (e.g. exposure, white balance, mirroring)
* IMU (gyroscope and accelerometer) access, sampling rate and range control
* Hardware synchronization of depth and color cameras and software synchronization (match by frame timestamp to achieve software synchronization) on the SDK side, configurable inter-camera delay
* External device synchronization control, configurable inter-device delay offset
* Free Run mode enables different frame rate configurations for depth and color cameras
* Access camera frame metadata for handling image resolution, timestamps, etc.
* Access to device calibration data
* Utility filters such as color image format conversion, point cloud data generation
* Depth data stream output aligned to color (i.e. D2C, output depth coordinate system and image resolution consistent with RGB)
* Complete setting information acquisition (device name, firmware version, SN, device temperature, etc.)
* Data recording function supports data compression
* Native C/C++ API and Python, ROS1, ROS2, Android wrappers

In addition, Orbbec SDK also supports almost all Orbbec’s mainstream cameras.

**1.2 Orbbec SDK K4A Wrapper Features**

Orbbec SDK and Orbbec SDK K4A Wrapper provide the following features that can run on Femto Bolt once installed:

* Depth camera access and mode control (passive IR mode, wide field-of-view and narrow field-of-view depth modes)
* RGB camera access and control (e.g. exposure and white balance)
* Motion sensor (gyroscope and accelerometer) access
* Synchronized depth and RGB camera streams with configurable inter-camera delay
* External device synchronization control with configurable inter-device delay offset
* Access camera frame metadata for handling image resolution, timestamps, etc.
* Access device calibration data

**1.3 Femto Bolt SDK Tools**

Orbbec SDK K4A Wrapper provides the following tools:

* Viewer tool that can be used to monitor device data streams and configure different modes
* Sensor recording tool and playback reader API using Matroska container format

#### 2. Human Skeleton Tracking SDK <a href="#id-2.-human-skeleton-tracking-sdk" id="id-2.-human-skeleton-tracking-sdk"></a>

The human skeleton tracking algorithm SDK uses Microsoft’s human skeleton tracking algorithm, namely: Azure Kinect Body Tracking SDK.To use the human skeleton tracking algorithm on Femto Bolt hardware, please refer to:Azure Kinect Body Tracking Features

**2.1 Access AKDK Applications with Femto Bolt**

Femto Bolt supports accessing Azure Kinect Body Tracking SDK to obtain human body tracking features and effects completely consistent with using AKDK:

* Provides human image segmentation
* Skeletons of partial or full bodies within the FOV range
* Provides unique identification for each human body
* Can track human bodies in real time

**2.2 Azure Kinect Body Tracking Tools**

After accessing Azure Kinect Body Tracking SDK with Femto Bolt, the following functions can be supported using the viewer tool in this SDK:

* The body tracker provides a viewer tool to see how it tracks 3D human bodies.

#### 3. Femto Bolt Hardware Requirements <a href="#id-3.-femto-bolt-hardware-requirements" id="id-3.-femto-bolt-hardware-requirements"></a>

Femto Bolt is a high performance iToF 3D camera jointly developed by Orbbec and Microsoft. The camera uses the same depth module as Azure Kinect DK, continuing the same depth modes and performance. For details, please refer to Hardware Specifications.

#### 4. Next Steps <a href="#id-4.-next-steps" id="id-4.-next-steps"></a>

Now that you have a preliminary understanding of Femto Bolt, please go in depth into its various functions and make corresponding settings! Quick Start: [Hardware Specifications](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications),[Set up Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)

#### Femto Bolt Hardware Specifications <a href="#femto-bolt-hardware-specifications" id="femto-bolt-hardware-specifications"></a>

_Reviewed source:_ [_Femto Bolt Hardware Specifications_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications)_. Manufacturer figures and source examples retain their original attribution and rights._

This document details the specifications and some design details of the ORBBEC® Femto Bolt 3D camera product for developers’ understanding and use.

![Official Orbbec Femto Bolt figure from Femto Bolt Hardware Specifications](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033308/image001-scaled.jpg)

#### 1. Terminology <a href="#id-1.-terminology" id="id-1.-terminology"></a>

The following abbreviation terms are used throughout.

* NFOV (Narrow Field of View depth mode)
* WFOV (Wide Field of View depth mode)
* FOV (Field of View)
* FPS (Frames per Second)
* IMU (Inertial Measurement Unit)
* FoI (Field of Interest)

#### 2. Product Dimensions and Weight <a href="#id-2.-product-dimensions-and-weight" id="id-2.-product-dimensions-and-weight"></a>

The Femto Bolt device dimensions and weight are:

* Dimensions: 115.30 × 64.95 × 40.26 mm
* Weight: 348g

For more information, please refer to the github [https://github.com/orbbec/OrbbecHardware](https://github.com/orbbec/OrbbecHardware)

![Official Orbbec Femto Bolt figure from Femto Bolt Hardware Specifications](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033212/image003-1.png)

#### 3. Operating Environment <a href="#id-3.-operating-environment" id="id-3.-operating-environment"></a>

Femto Bolt is intended for use by developers and commercial deployments operating under these environmental conditions:

* Temperature: 10-25°C
* Humidity: 8-90% (non-condensing) relative humidity

Note: Operation outside these conditions may result in device failure and/or abnormal operation. These environment conditions pertain to the ambient environment immediately surrounding the device while in operation under all use cases. If used with an external enclosure, effective temperature control and/or other heat dissipation solutions are recommended to maintain operating conditions within these ranges. A thermal channel is designed between the front face and rear cannister of the device. Do not obstruct this thermal channel when using the device.

#### 4. Depth Camera Supported Operating Modes <a href="#id-4.-depth-camera-supported-operating-modes" id="id-4.-depth-camera-supported-operating-modes"></a>

Femto Bolt integrates a 1 megapixel Time-of-Flight (ToF) depth camera. The depth camera supports the following modes as described:

| Mode                 | Resolution | FoI       | FPS        | Operating range\* | Exposure time |
| -------------------- | ---------- | --------- | ---------- | ----------------- | ------------- |
| NFOV unbinned        | 640×576    | 75°x65°   | 5、15、25、30 | 0.5 – 3.86 m      | 12.8 ms       |
| NFOV 2×2 binned (SW) | 320×288    | 75°x65°   | 5、15、25、30 | 0.5 – 5.46 m      | 12.8 ms       |
| WFOV 2×2 binned      | 512×512    | 120°x120° | 5、15、25、30 | 0.25 – 2.88 m     | 12.8 ms       |
| WFOV unbinned        | 1024×1024  | 120°x120° | 5、15、25    | 0.25 – 2.21 m     | 20.3 ms       |
| Passive IR           | 1024×1024  | N/A       | 5、15、25、30 | N/A               | 1.6 ms        |

\*850nm at 15% to 95% reflectivity, 2.2 μW/cm2/nm, standard deviation of random error ≤ 17 mm, typical system error < 11 mm + 0.1% of distance (no multi-path interference). Depth can be provided beyond the indicated operating range depending on object reflectivity.

#### 5. Color Camera Supported Operating Modes <a href="#id-5.-color-camera-supported-operating-modes" id="id-5.-color-camera-supported-operating-modes"></a>

The native operating modes are listed below:

| RGB Camera Resolution (HxV) | Aspect Ratio | Format Options  | Frame Rates (FPS) | Nominal FOV (HxV)(post-processed) |
| --------------------------- | ------------ | --------------- | ----------------- | --------------------------------- |
| 3840×2160                   | 16:9         | MJPEG           | 5、15、25、30        | 80°x51°                           |
| 2560×1440                   | 16:9         | MJPEG           | 5、15、25、30        | 80°x51°                           |
| 1920×1080                   | 16:9         | MJPEG           | 5、15、25、30        | 80°x51°                           |
| 1280×720                    | 16:9         | MJPEG/YUY2/NV12 | 5、15、25、30        | 80°x51°                           |
| 1280×960                    | 4:3          | MJPEG           | 5、15、25、30        | 65°x51°                           |

Note: The SDK can provide color images in BGRA pixel format. This is not a natively supported mode by the device and will result in increased CPU load. The host CPU is used to convert from the MJPEG images received from the device.

#### 6. Depth Sensor Raw Timing <a href="#id-6.-depth-sensor-raw-timing" id="id-6.-depth-sensor-raw-timing"></a>

| Depth Mode                                    | IR Pulses | Pulse Width | Idle Periods | Idle Time | Exposure Time |
| --------------------------------------------- | --------- | ----------- | ------------ | --------- | ------------- |
| NFOV Unbinned NFOV 2×2 Binned WFOV 2×2 Binned | 9         | 125 us      | 8            | 1450 us   | 12.8 ms       |
| WFOV Unbinned                                 | 9         | 125 us      | 8            | 2390 us   | 20.3 ms       |

#### 7. Camera Fields of View <a href="#id-7.-camera-fields-of-view" id="id-7.-camera-fields-of-view"></a>

The image below shows the depth and RGB camera fields of view (what the sensors see). The 16:9 mode RGB camera is shown below.

![Official Orbbec Femto Bolt figure from Femto Bolt Hardware Specifications](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033321/image005.jpg)

This depicts the camera fields of view at a distance of 2000 mm straight ahead.

![Official Orbbec Femto Bolt figure from Femto Bolt Hardware Specifications](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033326/image007-1-e1701920140190.png)

Note: For depth in NFOV mode, RGB camera pixel overlap is better in 4:3 mode than 16:9 mode.

#### 8. Inertial Measurement Unit (IMU) <a href="#id-8.-inertial-measurement-unit-imu" id="id-8.-inertial-measurement-unit-imu"></a>

The embedded Inertial Measurement Unit (IMU) is ICM-40608, containing accelerometer and gyroscope. 6-axis accelerometer & 6-axis gyroscope, data format is float, frequency range is 50-2000Hz.

#### 9. Indicator Lights <a href="#id-9.-indicator-lights" id="id-9.-indicator-lights"></a>

An indicator light on the front of the device signals the working status of the device, on by default and can be manually switched off.

A status LED on the back of the device indicates:

| When the light is | It means                                                 |
| ----------------- | -------------------------------------------------------- |
| Solid white       | Device is on and working properly.                       |
| Flashing white    | Device is on but doesn’t have a USB 3.0 data connection. |
| Flashing amber    | Device doesn’t have enough power to operate.             |

#### 10. Powering the Device <a href="#id-10.-powering-the-device" id="id-10.-powering-the-device"></a>

{% hint style="info" %}
The baseline hardware path uses the supplied DC adapter plus USB data. USB enumeration does not establish sufficient operating power. Retained alternative power arrangements require the model’s exact power specification.
{% endhint %}

The device can be powered in two ways:

1. Using the supplied power adapter. The power connector has an outer diameter of 5.5mm and an inner diameter of 2.1mm.
2. Power and data transfer via a Type-C to Type-C cable.

Note: The supplied power cable is a USB Type-A to barrel jack. Use this cable along with the supplied wall adapter. Two standard USB Type-A ports do not provide sufficient power for this device.

The USB cable is very important, a quality cable is recommended and functionality should be validated before remote deployment of the unit.

Tips for a good Type-C to Type-C cable:

* USB certified cable – must support power and data transfer
* Passive cables should be less than 1.5m length, use active for longer
* Cable needs to support at least 1.5A current, otherwise external power required
* Test cable:
  * Connect device to host PC with cable
  * Verify all devices appear correctly in Windows Device Manager. Depth and RGB cameras should appear as shown in example below.

![Official Orbbec Femto Bolt figure from Femto Bolt Hardware Specifications](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033330/image009-1.png)

* Verify cable reliably streams all sensor data in K4A Viewer with these settings:
  * Depth camera: NFOV unbinned
  * RGB camera: 2160p

#### 11. What Do the Indicator Lights Mean? <a href="#id-11.-what-do-the-indicator-lights-mean" id="id-11.-what-do-the-indicator-lights-mean"></a>

The power indicator is an LED on the back of Femto Bolt. This LED changes color based on the state of the device.

![Official Orbbec Femto Bolt figure from Femto Bolt Hardware Specifications](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07033336/image011-1-e1701920252294.png)

This diagram labels:

1. Power indicator LED
2. Multi-camera sync cable (does not affect power indicator state)
3. Power cable (for power adapter)
4. USB-C data cable (to PC)

Ensure cables are connected as shown. Then see the table below for the meaning of the power indicator LED states.

#### 12. Power Consumption <a href="#id-12.-power-consumption" id="id-12.-power-consumption"></a>

{% hint style="info" %}
The baseline hardware path uses the supplied DC adapter plus USB data. USB enumeration does not establish sufficient operating power. Retained alternative power arrangements require the model’s exact power specification.
{% endhint %}

Femto Bolt peak power consumption is 8.7W with DC power + Type-C data transfer; 7.7W with Type-C power + Type-C data transfer. Power consumption is use case dependent.

#### 13. Calibration <a href="#id-13.-calibration" id="id-13.-calibration"></a>

Femto Bolt devices are calibrated at the factory. Calibration parameters for the visual sensors and inertial sensors can be programmatically queried via the Sensor SDK.

#### 14. Next Steps <a href="#id-14.-next-steps" id="id-14.-next-steps"></a>

[Set up Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)

#### Femto Bolt 3D Camera SDK System Requirements <a href="#femto-bolt-3d-camera-sdk-system-requirements" id="femto-bolt-3d-camera-sdk-system-requirements"></a>

_Reviewed source:_ [_Femto Bolt 3D Camera SDK System Requirements_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%203D%20Camera%20SDK%20System%20Requirements)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

This document details the system requirements to install the SDK and successfully deploy Femto Bolt.

#### 1. Supported Operating Systems and Architectures <a href="#id-1.-supported-operating-systems-and-architectures" id="id-1.-supported-operating-systems-and-architectures"></a>

* Windows 10 April 2018 release (version 1803, OS build 17134) (x64) or later
* Linux Ubuntu 18.04 (x64) with GPU drivers that support OpenGL v4.4 or later
* Orbbec SDK and Orbbec SDK K4A Wrapper for native C/C++ Windows applications using Windows API (Win32)
* Orbbec SDK and Orbbec SDK K4A Wrapper are currently not supported for UWP applications. S-Mode on Windows 10 does not support Femto Bolt

#### 2. Development Environment Requirements <a href="#id-2.-development-environment-requirements" id="id-2.-development-environment-requirements"></a>

To contribute to the Sensor SDK, visit [Github](https://github.com/orbbec) .

#### 3. Minimum Host PC Hardware Requirements <a href="#id-3.-minimum-host-pc-hardware-requirements" id="id-3.-minimum-host-pc-hardware-requirements"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

The hardware requirements for the host PC depend on the application/algorithms/sensor frame rates/resolutions run on the host. The minimum Sensor SDK configuration recommended for Windows is:

* 7th Generation Intel® CoreTM i3 Processor (Dual-Core 2.4 GHz with HD620 or faster GPU)
* 4 GB Memory
* Dedicated USB3 port
* Graphics driver supporting OpenGL 4.4 or DirectX 11.0

Lower end or older CPUs may also work depending on the specific use case.

Additionally, performance varies based on Windows/Linux OS and graphics drivers used.

#### 4. Host PC Hardware Requirements for Body Tracking <a href="#id-4.-host-pc-hardware-requirements-for-body-tracking" id="id-4.-host-pc-hardware-requirements-for-body-tracking"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

The requirements for a body tracking host PC are higher than for a general host PC. The minimum body tracking SDK configuration recommended for Windows is:

* 7th Generation Intel® CoreTM i5 Processor (Quad-Core 2.4 GHz or faster)
* 4 GB Memory
* NVIDIA GEFORCE GTX 1050 or equivalent
* Dedicated USB3 port

The minimum recommended assumes K4A\_DEPTH\_MODE\_NFOV\_UNBINNED depth mode at 30fps tracking 5 people. Lower end or older CPU and NVIDIA GPUs may also work depending on the specific use case.

#### 5. USB3 <a href="#id-5.-usb3" id="id-5.-usb3"></a>

Some known USB host controller compatibility issues can be found on Troubleshooting.

#### 6. Next Steps <a href="#id-6.-next-steps" id="id-6.-next-steps"></a>

* [About Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/About%20Femto%20Bolt)
* [Set up Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)
* [Known Issues and Troubleshooting for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Known%20Issues%20and%20Troubleshooting%20for%20Femto%20Bolt)

#### Set up Femto Bolt <a href="#set-up-femto-bolt" id="set-up-femto-bolt"></a>

_Reviewed source:_ [_Set up Femto Bolt_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The baseline hardware path uses the supplied DC adapter plus USB data. USB enumeration does not establish sufficient operating power. Retained alternative power arrangements require the model’s exact power specification.
{% endhint %}

This quickstart provides guidance on how to set up your Femto Bolt, including how to test 3D camera stream visualization and use associated capabilities.

#### 1. System Requirements <a href="#id-1.-system-requirements" id="id-1.-system-requirements"></a>

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

Review the [Hardware Specifications ](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications)to verify your host computer configuration meets all minimum requirements for Femto Bolt.

#### 2. Set up Hardware <a href="#id-2.-set-up-hardware" id="id-2.-set-up-hardware"></a>

Note: Make sure to remove the protective film from the camera prior to use.

1. Insert the power connector into the power jack on the back of the device. Connect the USB power adapter to the other end of the cable, then plug the adapter into a power outlet.
2. Connect one end of the USB data cable to the device and the other end to a USB 3.0 port on your PC.

Note: For best results, connect cables directly to the device and computer. Avoid extenders or additional adapters in connections.

3. Verify the power indicator LED (next to the USB cable) is solid white.

It takes a few seconds for the device to power on. The device is ready for use when the streaming LED indicator on the front goes out.

For details on the power indicator LED, see [Hardware Specifications](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications).

![Official Orbbec Femto Bolt figure from Set up Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/04083713/20231204-scaled.jpg)

#### 3. Download the SDK <a href="#id-3.-download-the-sdk" id="id-3.-download-the-sdk"></a>

1. Go to the [Orbbec SDK and K4A Wrapper](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20Orbbec%20SDK%20K4A%20Wrapper%20\(Femto%20Bolt\)) download link.
2. Install the SDK on your PC.

#### 4. Update Firmware <a href="#id-4.-update-firmware" id="id-4.-update-firmware"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

The latest firmware version is required for the SDK to function properly. To check and update the firmware version, follow the steps in [Update Femto Bolt Firmware](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Update%20Femto%20Bolt%20Firmware).

#### 5. Verify Device Streams Data <a href="#id-5.-verify-device-streams-data" id="id-5.-verify-device-streams-data"></a>

1. Launch the [K4A Viewer Tool](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt), either from the command line or by double clicking.
2. In the Femto Bolt Viewer, select “Open Device” > “Start”.![Official Orbbec Femto Bolt figure from Set up Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/04083718/202312041-e1701679272579.png)
3. Verify the tool visualizes each sensor stream:

*
  * Depth camera
  * Color camera
  * Infrared camera
  * IMU

![Official Orbbec Femto Bolt figure from Set up Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/04083723/202312042.png)

Femto Bolt setup is now complete. You can now start developing applications.

If you encounter any issues, check out [Femto Bolt Troubleshooting](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Known%20Issues%20and%20Troubleshooting%20for%20Femto%20Bolt).

#### 6. Next Steps <a href="#id-6.-next-steps-1" id="id-6.-next-steps-1"></a>

With your Femto Bolt up and running, you can also learn how to: [Record data to file](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Data%20Recording)

#### Orbbec SDK and Orbbec SDK K4A Wrapper (Femto Bolt) <a href="#orbbec-sdk-and-orbbec-sdk-k4a-wrapper-femto-bolt" id="orbbec-sdk-and-orbbec-sdk-k4a-wrapper-femto-bolt"></a>

_Reviewed source:_ [_Orbbec SDK and Orbbec SDK K4A Wrapper (Femto Bolt)_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20Orbbec%20SDK%20K4A%20Wrapper%20\(Femto%20Bolt\))_. Manufacturer figures and source examples retain their original attribution and rights._

Orbbec Femto Bolt is a reliable alternative product to Microsoft Azure Kinect DK. We provide two SDKs for this product: Orbbec SDK and Orbbec SDK K4A Wrapper.

Since Orbbec cannot provide upgrades and maintenance of the original AKDK development tools, from a long-term perspective, we recommend you try and use Orbbec SDK which Orbbec has been maintaining and updating as soon as possible. Using Orbbec SDK with Femto Bolt will provide you with richer and more powerful features.

To help users who have developed applications using K4A get started with Orbbec Femto Bolt more quickly and achieve seamless replacement of Microsoft AKDK, we encapsulated Orbbec SDK K4A Wrapper on top of Orbbec SDK with maximum compatibility with K4A API. Using this Wrapper, the user’s application does not need to be modified.

For more details about Orbbec SDK, please click ([https://github.com/orbbec/OrbbecSDK](https://github.com/orbbec/OrbbecSDK)). If you encounter any issues using this product or need more information, please contact our technical support team at any time.

This document mainly summarizes Orbbec SDK K4A Wrapper and its features and tools.

#### 1. Features <a href="#id-1.-features" id="id-1.-features"></a>

Orbbec SDK K4A Wrapper provides cross-platform low-level access to Femto Bolt device configuration and hardware sensor streams, including:

* Depth camera access and mode control (passive IR mode, wide and narrow field-of-view depth modes)
* RGB camera access and control (e.g. exposure and white balance)
* Motion sensors (gyroscope and accelerometer) access.
* Synchronized depth and RGB camera streams with configurable inter-camera delay.
* External device synchronization control with configurable inter-device delay offset.
* Access to camera frame metadata for handling image resolution, timestamps, etc.
* Access to device calibration data.

#### 2. Tools <a href="#id-2.-tools" id="id-2.-tools"></a>

* K4aviewer tool for getting data streams, configuring depth modes, setting color parameters, live preview of 2D and 3D images.
* k4arecorder tool for recording using Matroska container format. Recorded files can be played back with K4aviewer.

#### 3. Sensor SDK <a href="#id-3.-sensor-sdk" id="id-3.-sensor-sdk"></a>

* Open source code for Orbbec SDK K4A Wrapper is available on GitHub.
* See Sensor SDK API Documentation for detailed usage information.

#### 4. Next Steps <a href="#id-4.-next-steps-1" id="id-4.-next-steps-1"></a>

Now that you know about Orbbec SDK K4A Wrapper, you can also:

* [Download Orbbec SDK and K4A Wrapper](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20K4A%20Wrapper%20Download%20\(Femto%20Bolt\))
* [Find and Open Device](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Find%20and%20Open%20Femto%20Bolt%20Devices)

#### K4A Viewer for Femto Bolt <a href="#k4a-viewer-for-femto-bolt" id="k4a-viewer-for-femto-bolt"></a>

_Reviewed source:_ [_K4A Viewer for Femto Bolt_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt)_. Manufacturer figures and source examples retain their original attribution and rights._

The Femto Bolt Viewer (found in the tools install directory as k4aviewer.exe) can visualize all device data streams. For example, the path is _C:\Program Files\Orbbec-SDK-K4A-Wrapper-vX.Y.Z\tools\k4aviewer.exe_ , where X.Y.Z is the installed SDK version.

The viewer can be used to:

* Verify sensors are working properly.
* Aid device positioning.
* Experiment with different camera settings.
* Read device configurations.
* Play recordings made with the Recorder.

#### 1. Using the Viewer <a href="#id-1.-using-the-viewer" id="id-1.-using-the-viewer"></a>

The viewer can capture live data from the sensors or play back recorded files.

**1.1 Launching the Application**

Run _k4aviewer.exe_ to start the application.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021915/image002-3.gif)

**1.2 Using the Viewer with Live Data**

1. In the “Open Device” section, select the device “Serial Number (Device S/N)” to open it. If the device is not listed, select “Refresh Devices”.
2. Click the “Open Device” button.
3. Select “Start” to begin streaming data with default settings.

**1.3 Using the Viewer with Recorded Data**

In the “Open Recording” section, navigate to and select the recorded file.

#### 2. Checking Device Firmware Version <a href="#id-2.-checking-device-firmware-version" id="id-2.-checking-device-firmware-version"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

As shown below, the device firmware versions can be accessed in the configuration window.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021918/image004.jpg)

For example, in this case the depth camera ISP is running FW 1.0.6.

#### 3. Depth Camera <a href="#id-3.-depth-camera" id="id-3.-depth-camera"></a>

The depth camera viewer will display two windows:

* One named “Active IR” showing a grayscale image of the IR brightness.
* Another named “Depth” representing the depth data in different colors.

Hovering over a pixel in the depth window shows the value from the depth sensor, as below.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021922/image006-3.gif)

#### 4. RGB Camera <a href="#id-4.-rgb-camera" id="id-4.-rgb-camera"></a>

The image below shows the color camera view.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021926/image008-3.gif)

The RGB camera settings can be controlled via the configuration window during streaming.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021930/image010-2.gif)

#### 5. Inertial Measurement Unit (IMU) <a href="#id-5.-inertial-measurement-unit-imu" id="id-5.-inertial-measurement-unit-imu"></a>

The IMU window contains two components: the accelerometer and gyroscope.

The top portion is the accelerometer, showing linear acceleration in m/s^2. This includes gravity, so the Z-axis may show around -9.8 m/s^2 if placed flat on a table.

The bottom portion is the gyroscope, showing rotational motion in radians/second.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021933/image012-3.gif)

#### 6. Point Cloud Visualization <a href="#id-6.-point-cloud-visualization" id="id-6.-point-cloud-visualization"></a>

The depth visualized in 3D allows moving through the image using the directional keys.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021936/image014-3.gif)

#### 7. Sync Control <a href="#id-7.-sync-control" id="id-7.-sync-control"></a>

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

When configuring multi-device sync, the viewer can set a device to standalone (default), master, or subordinate modes. Select “Refresh” when changing configurations or inserting/removing sync cables.

![Official Orbbec Femto Bolt figure from K4A Viewer for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07021940/image016-3.gif)

#### 8. Next Steps <a href="#id-8.-next-steps" id="id-8.-next-steps"></a>

[Synchronize Multiple Devices](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Synchronize%20Multiple%20Femto%20Bolt%20Devices)

#### Femto Bolt Data Recording <a href="#femto-bolt-data-recording" id="femto-bolt-data-recording"></a>

_Reviewed source:_ [_Femto Bolt Data Recording_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Data%20Recording)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

This quickstart provides information on how to use the K4A recorder tool to record the data streams emitted from the Sensor SDK to a file.

#### 1. Prerequisites <a href="#id-1.-prerequisites" id="id-1.-prerequisites"></a>

* Femto Bolt is connected to the host computer and powered on properly.
* You have completed [Set up Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt).

#### 2. Create Recording <a href="#id-2.-create-recording" id="id-2.-create-recording"></a>

{% hint style="info" %}
Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

1. Open a command prompt, providing the path to k4arecorder.exe, located in the k4arecorder tool install location. For example:

> F:\OrbbecSDK\_K4A\_Wrapper\_v1.8.1\_20231011\_win\_x64\_release\bin\k4arecorder.exe

2. Record for 5 seconds:

> k4arecorder.exe -l 5 output.mkv

3. By default, the recorder captures content with NFOV unbinned depth mode, 1080p RGB @ 30 fps (including IMU data). See [K4A Recorder for Femto Bolt ](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt%20Recorder), a full overview and tips on recording options.

#### 3. Play Recording <a href="#id-3.-play-recording" id="id-3.-play-recording"></a>

{% hint style="info" %}
Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

You can play back the recording using the [K4A Viewer tool](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt).

1. Launch k4aviewer.exe
2. Expand the “Open Recording” tab and open your recording.

#### 4. Next Steps <a href="#id-4.-next-steps-2" id="id-4.-next-steps-2"></a>

You now know how to record sensor streams to file, next you can generate your first application.

#### Generate Your First Femto Bolt Application <a href="#generate-your-first-femto-bolt-application" id="generate-your-first-femto-bolt-application"></a>

_Reviewed source:_ [_Generate Your First Femto Bolt Application_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Generate%20Your%20First%20Femto%20Bolt%20Application)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

Want to get started with your Femto Bolt? This quickstart guide will help you get your device powered on and running successfully!

This document will introduce the following functions:

* [k4a\_device\_get\_installed\_count()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#ga4a94d1a30b614cd9c1a42e7a9aa79b13)
* [k4a\_device\_open()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#gae9972f1c1a771813e3f6c7e75fefd96a)
* [k4a\_device\_get\_serialnum()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#gad9f91d0ff216404332b25752ab9b3721)
* [k4a\_device\_start\_cameras()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#gadcba304c93173494cc3f065623bf62ae)
* [k4a\_device\_stop\_cameras()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#ga5dc4ae0635c75c85fd73011f0796375d)
* [k4a\_device\_close()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#ga22e23c55a90f8e07d1c8a3fb7b3db6af)

#### 1. Prerequisites <a href="#id-1.-prerequisites-1" id="id-1.-prerequisites-1"></a>

1. You have completed [Set up Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Set%20up%20Femto%20Bolt).
2. The SDK is installed from [Download Orbbec SDK and K4A Wrapper](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20K4A%20Wrapper%20Download%20\(Femto%20Bolt\)).

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
#include <k4a/k4a.h>
```

#### 2. Header Files <a href="#id-2.-header-files" id="id-2.-header-files"></a>

Just one header file is needed, k4a.h. Make sure your chosen compiler is set up to use the SDK libraries and include folder. The k4a.lib and k4a.dll files will also need to be linked.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
uint32_t count = k4a_device_get_installed_count();
```

#### 3. Find Femto Bolt Device <a href="#id-3.-find-femto-bolt-device" id="id-3.-find-femto-bolt-device"></a>

Multiple Femto Bolt devices can be connected to a computer. First, we’ll use the [k4a\_device\_get\_installed\_count()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#ga4a94d1a30b614cd9c1a42e7a9aa79b13) function to determine if any devices are connected, or how many there are. This function should work right away without any additional setup.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
uint32_t count = k4a_device_get_installed_count();
```

Once a device is found to be connected to the computer, it can be opened with [k4a\_device\_open()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#gae9972f1c1a771813e3f6c7e75fefd96a). The index of the device to open can be provided, or just K4A\_DEVICE\_DEFAULT for the first device.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
k4a_device_open(K4A_DEVICE_DEFAULT, &device);
```

As with most things in the Azure Kinect library, when you open something, you should also close it when finished! Make sure to call [k4a\_device\_close()](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___functions.html#ga22e23c55a90f8e07d1c8a3fb7b3db6af) when closing.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
k4a_device_close(device);
```

After opening the device, we can test it is working properly. Let’s read the device serial number!

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Get the size of the serial number
size_t serial_size = 0;
k4a_device_get_serialnum(device, NULL, &serial_size);

// Allocate memory for the serial, then acquire it
char *serial = (char*)(malloc(serial_size));
k4a_device_get_serialnum(device, serial, &serial_size);
printf("Opened device: %s\n", serial);
free(serial);
```

#### 4. Start Cameras <a href="#id-4.-start-cameras" id="id-4.-start-cameras"></a>

After opening the device, the cameras need to be configured using a [k4a\_device\_configuration\_t](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___structures.html#gaa3764c9309d6fae0a927be1327965633) object. There are many different options available in the camera configuration. Choose settings most appropriate for your scenario.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Configure a stream of 3840x2160 BRGA color data at 15 frames per second
k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
config.camera_fps       = K4A_FRAMES_PER_SECOND_15;
config.color_format     = K4A_IMAGE_FORMAT_COLOR_BGRA32;
config.color_resolution = K4A_COLOR_RESOLUTION_2160P;

// Start the camera with the given configuration
k4a_device_start_cameras(device, &config);

// ...Camera capture and application specific code would go here...

// Shut down the camera when finished with application logic
k4a_device_stop_cameras(device);
```

#### 5. Error Handling <a href="#id-5.-error-handling" id="id-5.-error-handling"></a>

For brevity, error handling will not be shown in all examples. But error handling is always important! Many functions return a regular success/failure type [k4a\_result\_t](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___enumerations.html#ga4b419a99aa2220b076a4520dc2afd1e5), or more specific variables with extra details like [k4a\_wait\_result\_t](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___enumerations.html#ga44c7c0c1cfba7c879e9e2da1a869e4ee). Check the documentation for each function or IntelliSense to see expected error messages the function can return!

We can check function results with the [K4A\_SUCCEEDED](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___macros.html#ga8e5b48150bc243c6052793bd830c2fcd) and [K4A\_FAILED](https://orbbec.github.io/docs/OrbbecSDK_K4A_Wrapper/main/group___macros.html#ga8e5b48150bc243c6052793bd830c2fcd) macros. So in addition to opening the Femto Bolt device, we can also protect function calls like:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Open the first plugged in Kinect device
k4a_device_t device = NULL;
if ( K4A_FAILED( k4a_device_open(K4A_DEVICE_DEFAULT, &device) ) )
{
  printf("Failed to open k4a device!\n");
  return;
}
```

#### 6. Full Source <a href="#id-6.-full-source" id="id-6.-full-source"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
#pragma comment(lib, "k4a.lib")
#include <k4a/k4a.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{
  uint32_t count = k4a_device_get_installed_count();
  if (count == 0)
  {
    printf("No k4a devices attached!\n");
    return 1;
  }

  // Open the first plugged in Kinect device
  k4a_device_t device = NULL;
  if (K4A_FAILED(k4a_device_open(K4A_DEVICE_DEFAULT, &device))) 
  {
    printf("Failed to open k4a device!\n");
    return 1;
  }

  // Get the size of the serial number 
  size_t serial_size = 0;
  k4a_device_get_serialnum(device, NULL, &serial_size);

  // Allocate memory for the serial, then acquire it
  char *serial = (char*)(malloc(serial_size));
  k4a_device_get_serialnum(device, serial, &serial_size);

  printf("Opened device: %s\n", serial);
  free(serial);

  // Configure a stream of 3840x2160 BRGA color data at 15 frames per second
  k4a_device_configuration_t config = K4A_DEVICE_CONFIG_INIT_DISABLE_ALL;
  config.camera_fps = K4A_FRAMES_PER_SECOND_15; 
  config.color_format = K4A_IMAGE_FORMAT_COLOR_BGRA32;
  config.color_resolution = K4A_COLOR_RESOLUTION_2160P;

  // Start the camera with the given configuration
  if (K4A_FAILED(k4a_device_start_cameras(device, &config)))
  {
    printf("Failed to start cameras!\n");
    k4a_device_close(device);
    return 1;
  }

  // Camera capture and application specific code would go here

  // Shut down the camera when finished with application logic 
  k4a_device_stop_cameras(device);
  k4a_device_close(device);

  return 0;
}
```

#### 7. Next Steps <a href="#id-7.-next-steps" id="id-7.-next-steps"></a>

You have learned how to use the Sensor SDK to find and open your Femto Bolt device.

Next see [Find and Open Device ](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Find%20and%20Open%20Femto%20Bolt%20Devices)to continue developing your application.

#### Access AKDK Application Software with Femto Bolt <a href="#access-akdk-application-software-with-femto-bolt" id="access-akdk-application-software-with-femto-bolt"></a>

_Reviewed source:_ [_Access AKDK Application Software with Femto Bolt_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Access%20AKDK%20Application%20Software%20with%20Femto%20Bolt)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

#### 1. Overview <a href="#id-1.-overview" id="id-1.-overview"></a>

Orbbec SDK K4A Wrapper is designed and encapsulated based on Orbbec SDK, converting Orbbec SDK to Azure Kinect Sensor SDK interfaces. It mainly implements data stream reception, color parameter setting, D2C and point cloud functions, recording and playback, consistent APIs with Azure Kinect Sensor SDK, allowing users to quickly switch to Orbbec Femto Bolt and Orbbec Femto Mega cameras without modifying the application code.

Orbbec SDK K4A Wrapper open source link: [https://github.com/orbbec/OrbbecSDK-K4A-Wrapper](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper)

The implementation principle of Orbbec SDK K4A Wrapper is as follows:

The characteristics of Orbbec SDK K4A Wrapper are as follows:

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062757/image000-e1701758018713.png)

* Maintain the original interfaces of Azure Kinect Sensor SDK unchanged.
* Modify the implementation (impl) of Azure Kinect Sensor SDK C API, call Orbbec SDK internally to get video frames and control Femto Bolt and Femto Mega cameras.
* Coordinate transformation, D2C, C2D, point cloud reuse Azure Kinect Sensor SDK.

Orbbec SDK K4A Wrapper currently supports the following cameras:

**Orbbec Femto Bolt:** Win10 x86/x64, Ubuntu18.04 x64, Ubuntu20.04 x64

**Orbbec Femto Mega:** Win10 x86/x64, Ubuntu20.04 x64

#### 2. Switching AKDK Applications to Orbbec SDK K4A Wrapper <a href="#id-2.-switching-akdk-applications-to-orbbec-sdk-k4a-wrapper" id="id-2.-switching-akdk-applications-to-orbbec-sdk-k4a-wrapper"></a>

This chapter mainly shows how to implement code project switching and adaptation to Femto Bolt cameras by replacing Azure Kinect Sensor SDK library files and header files with Orbbec SDK K4A Wrapper under the user application code project.

For compiled application executables, you can also directly switch by replacing the libk4a library file linked by the application executable with Orbbec SDK K4A Wrapper.

**2.1 Windows Platform Application**

**2.1.1 Environment Configuration: Modify Registry**

Due to the Windows system mechanism, for UVC protocol devices, if you need to get timestamp and other metadata information, you need to register in the registry first. You can execute the obsensor\_metadata\_win10.ps1 script to complete automatic registration according to the obsensor\_metadata\_win10.md document guide.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062801/image001.png)

**2.1.2 Replace Header Files**

Orbbec SDK K4A Wrapper is developed based on Azure Kinect Sensor SDK V1.4.1 version. The header files directly use the original K4A library header files. If the user project originally used Azure Kinect Sensor SDK V1.4.1 version, this step can be ignored.

* Find the header files in Orbbec SDK K4A Wrapper

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062809/image003.png)

* Replace the corresponding header files in Azure Kinect Sensor SDK

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062818/image005.png)

**2.1.3 Replace Library Files**

**Compile**

* First copy the k4a.lib and k4arecord.lib library files from the Orbbec SDK K4A Wrapper to the corresponding path of the Azure Kinect Sensor SDK.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07064736/202312071.png)

* Replace the corresponding k4a.lib and k4arecord.lib library files in the Azure Kinect Sensor SDK.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07064758/202312072.png)

* Then, copy the dll file from Orbbec SDK K4A Wrapper to the corresponding path in Azure Kinect Sensor SDK.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07064825/202312073.png)

* Replace the corresponding dll in Azure Kinect Sensor SDK.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07064841/202312074.png)

**Run**

* Find k4a.dll, k4arecord.dll, OrbbecSDK.dll, depthengine\_2\_0.dll library files in Orbbec SDK K4A Wrapper

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062842/image011.png)

Copy the above library files to the original executable application path of Azure Kinect Sensor SDK, and replace the original k4a.dll, k4arecord.dll, depthengine\_2\_0.dll library files to run the application program.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062852/image013.png)

**2.2 Linux Platform Application**

**2.2.1 Environment Configuration: Install udev rules Configuration**

By default, Linux systems require root permissions for direct access to USB devices, which can be solved through the rules configuration file. Orbbec SDK K4A Wrapper provides a 99-obsensor-libusb.rules configuration file and install\_udev\_rules.sh installation script to complete the installation by executing the install\_udev\_rules.sh script.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062901/image015.png)

Execution method:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
sudo chmod +x ./install.sh # Make sure the installation script is executable
sudo ./install.sh # Execute the script with sudo
```

**2.2.2 Replace Header Files**

_Orbbec SDK K4A Wrapper is developed based on Azure Kinect Sensor SDK V1.4.1 version. The header files directly use the original K4A library header files. If the user project originally used Azure Kinect Sensor SDK V1.4.1 version, this step can be ignored._

Find the original header files of Orbbec SDK K4A Wrapper and replace the corresponding header files under Azure Kinect Sensor SDK.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062908/image017.png)

**2.2.3 Replace Library Files**

* Find the library files in Orbbec SDK K4A Wrapper, including: libdepthengine, libk4a, libk4arecord, libOrbbecSDK.so.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062918/image019.png)

* Copy the above library files to the /usr/lib/x86\_64-linux-gnu directory to replace the Azure Kinect Sensor SDK libraries to compile and use the application program with Orbbec SDK K4A Wrapper.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062927/image021.png)

**Note:**

On Linux platforms, the depth engine library requires OpenGL. If the application layer also uses OpenGL and makes cross-thread calls to OpenGL instances, context conflicts may occur, causing problems during depth engine initialization and inability to start the depth data stream properly.

If the application layer uses OpenGL rendering, the application layer needs to switch the Context under OpenGL: [(https://www.khronos.org/opengl/wiki/OpenGL\_and\_multithreading)](https://www.khronos.org/opengl/wiki/OpenGL_and_multithreading)

The following is our solution using the glfw library:

1. Call glfwMakeContextCurrent(NULL) before starting the stream.
2. Then start the stream.
3. After the stream is finished, glfwMakeContextCurrent(currentContext).

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// See GitHub source: tools/k4aviewer/k4adevicedockcontrol.cpp
GLFWwindow *currentContext = glfwGetCurrentContext(); // store the current context
glfwMakeContextCurrent(NULL); // make current context to NULL

StartCameras(); // will initialize the DepthEngine

glfwMakeContextCurrent(currentContext); // restore the current context
```

#### 3. AKDK User Skeleton Algorithm Adaptation <a href="#id-3.-akdk-user-skeleton-algorithm-adaptation" id="id-3.-akdk-user-skeleton-algorithm-adaptation"></a>

The following uses the Azure Kinect Body Tracking SDK Sample as an example to describe how to obtain skeleton data by using Orbbec Femto Bolt camera data after replacing Azure Kinect Sensor SDK through Azure Kinect Body Tracking SDK (hereinafter referred to as K4ABT). (Users can switch by directly replacing the library files without recompiling)

**3.1 Windows Platform**

**3.1.1 Skeleton Installation Package Download and Installation**

Complete the installation according to Microsoft’s installation documentation: [https://learn.microsoft.com/en-us/azure/kinect-dk/body-sdk-setup](https://learn.microsoft.com/en-us/azure/kinect-dk/body-sdk-setup)

Download Azure Kinect Body Tracking SDK 1.1.2.msi, then execute the file to complete the installation.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062937/image023.png)

**3.1.2 Demonstrate Skeleton Algorithm Effects**

Complete the environment configuration (metadata registration) according to Chapter 2, then replace the following libraries of Azure kinect Sensor SDK in the installation directory with Orbbec SDK K4A Wrapper libraries (k4a.dll, OrbbecSDK.dll, k4arecord.dll, depthengine\_2\_0.dll), then run simple\_3d\_viewer.exe with administrator rights.

The effect of the skeleton algorithm is as follows:

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062948/image025.png)

**3.1.3 Skeleton Algorithm Secondary Development (Sample Compilation)**

1.Download Azure Kinect Samples

URL: [https://github.com/microsoft/Azure-Kinect-Samples](https://github.com/microsoft/Azure-Kinect-Samples)

Clone code:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
git clone https://github.com/microsoft/Azure-Kinect-Samples.git
```

2\. Open Microsoft skeleton sample with Visual Studio

Microsoft skeleton sample only supports opening with visual studio. Use VS2019 to open the following projects.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05062957/image027.png)

3\. Use the Orbbec SDK K4A Wrapper header and library files to replace the Azure Kinect Sensor SDK header and library files (dll, OrbbecSDK.dll, k4arecord.dll, depthengine\_2\_0.dll).

* Replace header files

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05063007/image029.png)

* Replace library files

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05090318/image.png)

4.Compile & Run

* The simple\_3d\_viewer.exe example relies on the following 2 libraries, which are copied from the installation package to the bin directory where the compiled application is generated.

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05063015/image031.png)

* Copy the dependent libraries to the running directory:

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05063026/image033.png)

* Compilation running interface:

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05063037/image035.png)

**3.2 Running Kinect Skeleton Algorithm on Linux**

The historical wrapper procedure below uses the Ubuntu 18.04 Microsoft package feed. These retained commands describe that source environment; they are not an installation recommendation for an arbitrary current host. Match the wrapper, Sensor SDK, Body Tracking SDK, GPU driver and host release before using a package command.

**3.2.1 Install Azure Kinect Sensor SDK**

Refer to the Linux installation instructions section of Microsoft’s installation documentation to complete the installation. Document link:

[Azure Kinect Sensor SDK download | Microsoft Learn](https://learn.microsoft.com/en-us/azure/kinect-dk/sensor-sdk-download)

Installation instructions:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
curl -sSL -O https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb 
sudo apt-get update
sudo apt-get install libk4a1.4-dev
sudo apt-get install k4a-tools
```

**3.2.2 Install Azure Kinect Body Tracking SDK**

Refer to the Linux installation instructions section of Microsoft’s installation documentation to complete the installation. Document link:

[Azure Kinect Body Tracking SDK download | Microsoft Learn](https://learn.microsoft.com/en-us/azure/kinect-dk/body-sdk-download)

The following instructions were executed during installation of Azure Kinect Sensor SDK and do not need to be repeated:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
curl -sSL -O https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update
```

Install libk4abt:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
sudo apt install libk4abt1.1-dev
```

**3.2.3 Use Orbbec SDK K4A Wrapper to Replace Azure Kinect Sensor SDK Library**

Complete the environment configuration (udev rules script installation) according to Chapter 2, then replace the Azure Kinect Sensor SDK library files with the library files in the Orbbec SDK K4A Wrapper package (libk4a.so, libOrbbecSDK.so, depthengine2). After replacing and connecting the Orbbec camera, enter the simple\_3d\_viewer command in the terminal to see the following running effect:

![Official Orbbec Femto Bolt figure from Access AKDK Application Software with Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05063046/image037.png)

#### 4. Differences between Orbbec SDK K4A Wrapper and Azure Kinect Sensor SDK <a href="#id-4.-differences-between-orbbec-sdk-k4a-wrapper-and-azure-kinect-sensor-sdk" id="id-4.-differences-between-orbbec-sdk-k4a-wrapper-and-azure-kinect-sensor-sdk"></a>

**4.1 Functional Points with Differences**

| No. | Function Point | Orbbec SDK K4A Wrapper                                                                                                                                                                                                                                                                                                                                                          | Azure Kinect Sensor SDK                                                                                                                                                                                                                                                                                                                                                         | Impact on Application                                                   |
| --- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| 1   | Recording      | c++ typedef struct \_k4a\_record\_configuration\_t { /\*\* \* The timestamp offset of the start of the recording. All recorded timestamps are offset by this value such that \* the recording starts at timestamp 0. This value can be used to synchronize timestamps between 2 recording files. \*/ uint64\_t start\_timestamp\_offset\_usec; } k4a\_record\_configuration\_t; | c++ typedef struct \_k4a\_record\_configuration\_t { /\*\* \* The timestamp offset of the start of the recording. All recorded timestamps are offset by this value such that \* the recording starts at timestamp 0. This value can be used to synchronize timestamps between 2 recording files. \*/ uint32\_t start\_timestamp\_offset\_usec; } k4a\_record\_configuration\_t; | Need to replace and recompile the header file of Orbbec SDK K4a Wrapper |

**4.2 Unimplemented Interfaces in Orbbec SDK K4A Wrapper (return empty value or exception state)**

| No. | Azure Kinect Sensor SDK Interface Meaning                                                                                                                                                        | Impact of Differences                                                                                                 |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- |
| 1   | c++ k4a\_result\_t k4a\_set\_allocator(k4a\_memory\_allocate\_cb\_t allocate, k4a\_memory\_destroy\_cb\_t free) Pass in external user-defined memory manager for SDK internal memory application | User cannot use their custom memory manager for SDK internal use. Basic functioning of SDK itself is barely affected. |
| 2   | c++ void k4a\_capture\_set\_temperature\_c(k4a\_capture\_t capture\_handle, float temperature\_c) Set temperature information for capture                                                        | User cannot modify this value, impacting storage of custom values                                                     |
| 3   | c++ float k4a\_capture\_get\_temperature\_c(k4a\_capture\_t capture\_handle) Get temperature information for capture                                                                             | User cannot get this value, impacting algorithms or applications that rely on this value                              |
| 4   | c++ void k4a\_image\_set\_exposure\_usec(k4a\_image\_t image\_handle, uint64\_t exposure\_usec) Set exposure value for image                                                                     | User cannot modify this value, impacting storage of custom values                                                     |
| 5   | c++ void k4a\_image\_set\_white\_balance(k4a\_image\_t image\_handle, uint32\_t white\_balance) Set white balance value for image                                                                | User cannot modify this value, impacting storage of custom values                                                     |
| 6   | c++ void k4a\_image\_set\_iso\_speed(k4a\_image\_t image\_handle, uint32\_t iso\_speed) Set ISO speed for image                                                                                  | User cannot modify this value, impacting storage of custom values                                                     |
| 7   | c++ uint64\_t k4a\_image\_get\_exposure\_usec(k4a\_image\_t image\_handle) Get exposure value for image                                                                                          | User cannot get this value, impacting algorithms or applications that rely on this value                              |
| 8   | c++ uint32\_t k4a\_image\_get\_white\_balance(k4a\_image\_t image\_handle) Get white balance value for image                                                                                     | User cannot get this value, impacting algorithms or applications that rely on this value                              |
| 9   | c++ uint32\_t k4a\_image\_get\_iso\_speed(k4a\_image\_t image\_handle) Read ISO speed for image                                                                                                  | User cannot get this value, impacting algorithms or applications that rely on this value                              |
| 10  | c++ k4a\_result\_t k4a\_device\_get\_sync\_jack(k4a\_device\_t device\_handle, bool \*sync\_in\_jack\_connected, bool \*sync\_out\_jack\_connected) Get sync cable connection status for device  | User application cannot rely on this interface to determine multi-camera sync cable linkage status                    |

#### Depth Camera (Femto Bolt) <a href="#depth-camera-femto-bolt" id="depth-camera-femto-bolt"></a>

_Reviewed source:_ [_Depth Camera (Femto Bolt)_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Depth%20Camera%20\(Femto%20Bolt\))_. Manufacturer figures and source examples retain their original attribution and rights._

This page describes how to use the depth camera in Femto Bolt. The depth camera is the second of two cameras. As described in earlier sections, the other camera is the RGB camera.

#### 1. Working Principle <a href="#id-1.-working-principle" id="id-1.-working-principle"></a>

The Femto Bolt depth camera uses amplitude modulated continuous wave (AMCW) time-of-flight (ToF) principles. The camera projects modulated light in the near infrared (NIR) spectrum into the scene. It then records an indirect measurement of the time it takes for the light to travel from the camera to the scene and back.

Processing these measurements can produce a depth frame. A depth frame consists of Z-coordinates in millimeters corresponding to each pixel in the image.

Along with the depth frame, we also get what are known as Active IR readings. The pixel values in the Active IR correspond to the amount of light returned from the scene. This image looks similar to a conventional IR image. The image below shows a sample depth frame (left) and its corresponding Active IR image (right).

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105156/image002-1.gif)

#### 2. Key Capabilities <a href="#id-2.-key-capabilities" id="id-2.-key-capabilities"></a>

Key capabilities of the depth camera include:

* 1 megapixel ToF imaging chip with advanced pixel techniques for higher modulation frequency and depth accuracy.
* Two NIR laser diodes for near and wide field-of-view (FoV) depth modes.
* World’s smallest 3.5μm x 3.5μm ToF pixels.
* Auto pixel gain selection enables larger dynamic range, allowing sharp capture of both near and far objects.
* Global shutter helps improve daylight capture performance.
* Multi-phase depth computation method enables reliable accuracy even with chip, laser, and power variations.
* Low system error and random error.

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105159/image004-1.gif)

The depth camera streams the raw modulated IR images to the PC host. On the PC, GPU accelerated depth engine software converts the raw signal into depth frames. The depth camera supports several modes. The narrow field-of-view (FoV) mode works well for scenes with a small X, Y extent but a large Z extent. For scenes with a large X, Y extent but small Z extent, the wide FoV mode is more appropriate.

The depth camera supports a 2×2 binned mode which can extend the Z range compared to the unbinned modes. The tradeoff for binning is reduced image resolution. All modes can run at frame rates up to 30 frames/second (fps), except for the 1 megapixel (MP) mode which has a maximum frame rate of 15 fps. The depth camera also provides a Passive IR mode. In this mode, the illuminators on the camera are not activated and only ambient light can be observed.

#### 3. Camera Performance <a href="#id-3.-camera-performance" id="id-3.-camera-performance"></a>

The performance of the camera is measured by the system error and random error.

**3.1 System Error**

The system error is defined as the difference between the measured depth after denoising and the true (ground truth) depth. We calculate a temporal mean over many frames of a static scene to remove as much depth noise as possible. More specifically, the system error is defined as:![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105202/image006-1.gif)

Where d\_t is the measured depth at time t, N is the number of frames used in the averaging process, and d\_gt is the ground truth depth.

The system error specification for the depth camera does not include multi-path interference (MPI). MPI occurs when a sensor pixel integrates light reflected from multiple objects. Using a higher modulation frequency, as well as depth invalidations described shortly, can partially mitigate MPI in the depth camera.

**3.2 Random Error**

Suppose we capture 100 images of the same object without moving the camera. Across these 100 images, the object depth varies slightly in each image. This variation is caused by speckle noise. Speckle occurs because the number of photons striking the sensor fluctuates randomly for some reason. We define this random error in a static scene as the standard deviation of depth over time according to:![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105206/image008-1.gif)

Where N is the number of depth measurements, d\_t is the depth measurement at time t, and d is the mean computed over all depth measurements d\_t.

#### 4. Invalidations <a href="#id-4.-invalidations" id="id-4.-invalidations"></a>

In some cases, the depth camera may be unable to provide correct values for some pixels. In these cases, the depth pixel is invalidated. Invalid pixels are indicated by a depth value of 0. Reasons the depth engine cannot produce a correct value include:

* Outside active IR illumination mask
* IR signal saturation
* Low IR signal strength
* Filtering anomalies
* Multi-path interference

**4.1 Illumination Mask**

Pixels outside the active IR illumination mask will be invalidated. We do not recommend using the signal from such pixels to compute depth. The image below shows an example of pixel invalidations from being outside the illumination mask. Invalid pixels include the black pixels outside the circle in the wide FoV mode (left) and the hexagon in the narrow FoV mode (right).

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105209/image010.jpg)

**4.2 Signal Strength**

Pixels with a saturated IR signal will be invalidated. Phase information is lost when a pixel saturates. The image below shows an example of pixel invalidations from IR signal saturation. Notice the arrows pointing to example pixels in the depth image and IR image.

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105212/image012-1.gif)

Pixels can also be invalidated if the IR signal strength is too low to produce valid depth. The image below shows an example of pixel invalidations from low IR signal strength. Again notice the arrows pointing to example pixels in the depth image and IR image.

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105215/image014-1.gif)

**4.3 Ambiguous Depth**

Pixels can also be invalidated if they receive signals from multiple objects in the scene. This commonly occurs around corners. Due to scene geometry, IR light emitted from the camera reflects off one wall onto another. This reflected light leads to ambiguous measured pixel depths. Filters in the depth algorithm detect these ambiguous signals and invalidate the pixels.

The image below shows an example of multi-path detection causing pixel invalidations. You can also observe how the same surface area invalidated in one camera view (top row) reappears in the other camera view (bottom row). This demonstrates surfaces invalidated in one perspective may be visible in another.

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105219/image016-1.gif)

**4.4 Multi-Path Mixing**

Another common case of multi-path is when a pixel contains a mix of signals from foreground and background (e.g. around object edges). More invalidated pixels around edges may be noticeable in fast motion scenes. This is due to the exposure interval of the raw depth capture.

![Official Orbbec Femto Bolt figure from Depth Camera (Femto Bolt)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05105223/image018-1.gif)

#### 5. Next Steps <a href="#id-5.-next-steps" id="id-5.-next-steps"></a>

[Coordinate Systems](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Coordinate%20Systems%20\(iToF%20Camera\))

#### Coordinate Systems (iToF Camera) <a href="#coordinate-systems-itof-camera" id="coordinate-systems-itof-camera"></a>

_Reviewed source:_ [_Coordinate Systems (iToF Camera)_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Coordinate%20Systems%20\(iToF%20Camera\))_. Manufacturer figures and source examples retain their original attribution and rights._

This document describes conventions for 2D and 3D coordinate systems. Each sensor device has an associated independent coordinate system.

#### 1. 2D Coordinate Systems <a href="#id-1.-2d-coordinate-systems" id="id-1.-2d-coordinate-systems"></a>

The depth camera and color camera have independent associated 2D coordinate systems. The \[x, y] coordinates are in units of pixels, where x ranges from 0 to width-1, and y ranges from 0 to height-1. The width and height depend on the chosen operating mode for the depth and color cameras. The pixel coordinate \[0,0] corresponds to the top-left pixel in the image. Pixel coordinates can be decimal values representing subpixel coordinates.

The 2D coordinate systems are centered at 0, meaning the subpixel coordinate \[0.0, 0.0] denotes the center, \[0.5,0.5] denotes the bottom-right corner of a pixel, as shown below.

![Official Orbbec Femto Bolt figure from Coordinate Systems (iToF Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05121800/202312051.png)

#### 2. 3D Coordinate Systems <a href="#id-2.-3d-coordinate-systems" id="id-2.-3d-coordinate-systems"></a>

Each camera, accelerometer, and gyroscope has an associated independent 3D coordinate space system.

Points in the 3D coordinate systems are represented as \[X, Y, Z] metric coordinate triplets in millimeters.

**2.1 Depth and Color Cameras**

The origin \[0,0,0] is located at the camera focal point. The positive X-axis points right, positive Y-axis points down, and positive Z-axis points forward.

The depth camera is tilted down 6 degrees towards the color camera, as shown below.

The depth camera uses two illuminators. The illuminator used in Narrow Field of View (NFOV) mode aligns with the depth camera use case and thus does not tilt. The illuminator used in Wide Field of View (WFOV) mode tilts an additional 1.3 degrees down relative to the depth camera.

![Official Orbbec Femto Bolt figure from Coordinate Systems (iToF Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05121756/202312052.jpeg)

**2.2 Gyroscope and Accelerometer**

The origin \[0,0,0] of the gyroscope is the same as the origin of the depth camera. The origin of the accelerometer aligns with its physical location. The coordinate system of the accelerometer and gyroscope follow the right-hand rule. The positive X-axis points backwards, positive Y-axis points left, and positive Z-axis points down, as shown below.

![Official Orbbec Femto Bolt figure from Coordinate Systems (iToF Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/05121752/202312053-1024x681.png)

#### 3. Next Steps <a href="#id-3.-next-steps" id="id-3.-next-steps"></a>

[Orbbec SDK and Orbbec SDK K4A Wrapper](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Orbbec%20SDK%20and%20Orbbec%20SDK%20K4A%20Wrapper%20\(Femto%20Bolt\))

#### Update Femto Bolt Firmware <a href="#update-femto-bolt-firmware" id="update-femto-bolt-firmware"></a>

_Reviewed source:_ [_Update Femto Bolt Firmware_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Update%20Femto%20Bolt%20Firmware)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

This document provides guidance on how to update the device firmware on the Femto Bolt.

#### 1. Prepare for Firmware Update <a href="#id-1.-prepare-for-firmware-update" id="id-1.-prepare-for-firmware-update"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

1\. Download the latest version of Orbbec Viewer and [latest firmware](https://github.com/orbbec/OrbbecFirmware/releases/tag/Femto-Bolt-Firmware)

2\. Ensure the device is properly connected to the computer.

Note: Keep the USB port and power connected during firmware update. Disconnecting during the update can corrupt the firmware.

#### 2. Update Device Firmware <a href="#id-2.-update-device-firmware" id="id-2.-update-device-firmware"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

1\. Launch Orbbec Viewer

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094459/image002-2.gif)

2\. Open “More”

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094504/image004-2.gif)

3\. Open Recovery Mode

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094509/image006-2.gif)

4\. Select the corresponding firmware, e.g. FemtoBolt\_v1.0.6\_20230919151820\_905dfc4

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094514/image008-2.gif) ![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094518/image010-1.gif)

5\. Start the upgrade

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094523/image012-2.gif)

6\. Wait for the upgrade to complete

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094528/image014-2.gif)

#### 3. Verify Device Firmware Upgrade <a href="#id-3.-verify-device-firmware-upgrade" id="id-3.-verify-device-firmware-upgrade"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

1\. Launch Orbbec Viewer

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094532/image016-2.gif)

2\. Open “More”

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094537/image018-2.gif)

3\. Check Device Information

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094541/image020-1.gif)

4\. View the Firmware version information

![Official Orbbec Femto Bolt figure from Update Femto Bolt Firmware](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/06094546/image022-1.gif)

#### 4. Troubleshooting <a href="#id-4.-troubleshooting" id="id-4.-troubleshooting"></a>

Firmware updates can fail for several reasons. If the firmware update fails, try the following to resolve:

1\. Retry the firmware update operation

2\. Check the device is connected properly

3\. Verify the firmware file is correct

#### Synchronize Multiple Femto Bolt Devices <a href="#synchronize-multiple-femto-bolt-devices" id="synchronize-multiple-femto-bolt-devices"></a>

_Reviewed source:_ [_Synchronize Multiple Femto Bolt Devices_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Synchronize%20Multiple%20Femto%20Bolt%20Devices)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

Each Femto Bolt device has an 8-pin GPIO sync port that can be used to interconnect multiple devices. Once connected, the devices can be coordinated via software to trigger captures at synchronized times.

This document covers how to connect and synchronize multiple devices.

#### 1. Benefits of Using Multiple Femto Bolt Devices <a href="#id-1.-benefits-of-using-multiple-femto-bolt-devices" id="id-1.-benefits-of-using-multiple-femto-bolt-devices"></a>

There are several reasons to use multiple Femto Bolt devices, including:

* Filling occlusion zones. Although the Femto Bolt data transform generates a single image, the two cameras (depth and RGB) are actually spaced a small distance apart. This offset allows for occlusion. Occlusion refers to situations where a foreground object blocks part of the background scene from one of the cameras on the device. In the generated color image, the foreground object appears to cast a shadow over the background object.

For example, in the image below, the left camera can see the gray pixel “P2”. But the white foreground object blocks the IR view from the right camera. The right camera cannot acquire data for “P2”. Adding synchronized devices can provide data for the occlusion.

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062541/image001-1.png)

* Scanning 3D objects.
* Increasing valid frame rate to 30 frames per second (fps) or higher.
* Capturing multiple 4K color images of the same scene with exposures aligned within 100 microseconds (us).
* Increasing spatial coverage of the cameras.

#### 2. Planning Multi-Device Configuration <a href="#id-2.-planning-multi-device-configuration" id="id-2.-planning-multi-device-configuration"></a>

Be sure to review the Hardware Specifications and Depth Camera sections before beginning.

#### 3. Selecting a Device Configuration <a href="#id-3.-selecting-a-device-configuration" id="id-3.-selecting-a-device-configuration"></a>

Device configurations can be accomplished using either:

* Star configuration – One master device synced with up to eight subordinate devices.

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062547/image003-3-1024x424.png)

* Daisy chain configuration – One master device synced with up to eight subordinate devices.

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062553/image005-1-1024x245.png)

**3.1 Introduction to camera synchronous interface and synchronous wire (Multi-camera Sync Cable)**

The camera uses 8-pin GPIO ports to realize synchronization. The specific interfaces are described in the following table:

| Pin | Definition       | Function                                                                                                                                                                                                                                                                                                                                                            |
| --- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | SYNC\_VCC        | ● Input & continuous level signal ● I/O level setting signal: the I/O level of the 8-pin synchronous interface is set to 1.8V by default; If the level voltage of 3.3V or 5V is provided on the SYNC\_VCC interface, the I/O level setting can be adjusted to 3.3V or 5V to improve the transmission stability and transmission distance of the synchronous signal. |
| 2   | GPIO\_OUT        | ● Output & pulse signal ● Synchronous driving signal: IR exposure synchronous signal; Typical application is to drive external supplementary light                                                                                                                                                                                                                  |
| 3   | VSYNC\_OUT       | ● Output & pulse signal ● Synchronous trigger signal: used to trigger the synchronous acquisition of data by the subsequent equipment                                                                                                                                                                                                                               |
| 4   | TIMER\_SYNC\_OUT | ● Output & pulse signal ● Hardware timestamp reset signal: used to reset the hardware timestamp of the subsequent device                                                                                                                                                                                                                                            |
| 5   | RESET\_IN        | ● Input & pulse signal ● Camera hard reset signal: trigger the camera to power down first, and automatically power on to reset                                                                                                                                                                                                                                      |
| 6   | VSYNC\_IN        | ● Input & pulse signal ● Synchronous trigger signal: the synchronous acquisition trigger signal sent by the pre-sequence device                                                                                                                                                                                                                                     |
| 7   | TIMER\_SYNC\_IN  | ● Input & pulse signal ● Hardware timestamp reset signal: the hardware timestamp reset instruction sent by the pre-sequence device                                                                                                                                                                                                                                  |
| 8   | GND              | ● Input/Output & continuous level signal ● Grounding signal: reference of synchronous signal                                                                                                                                                                                                                                                                        |

Multi-camera Sync Cable introduction, as shown in the following figure, the professional version of the Multi-camera Sync Cable, the left Connector 8-pin interface is connected to the camera terminal, the right RJ45 interface is connected to the network Cable terminal.

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062559/image007-2-1024x352.png)

Diagram of synchronized cable connection on camera side

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062605/image009-2-e1701930726657-1024x551.png)

**3.2 Using External Trigger**

In both configurations, the master device provides the trigger signal to subordinates. But you can use a custom external source as the sync trigger instead. For example, this option can enable syncing captures with other equipment. The external trigger source connects to the VSYNC\_IN port on devices whether in star or daisy chain configurations.

The external trigger source must operate the same as the master device. It must provide a sync signal with:

* Rising edge trigger
* High pulse width: >1ms
* Trigger level: 1.8V/3.3V/5V
* Frequency support: exactly 30FPS, 25FPS, 15FPS and 5FPS (the frequency of the master camera’s VSYNC\_IN signal)

The trigger source must use a Multi-camera Sync Cable to relay the signal to the sync signal input port on subordinates.

Multi-camera synchronization of Primary connected to the Multi-camera Sync hub Pro diagram

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062611/image011-2-1024x431.png)

Multi-camera synchronization of Secondary connected to the Multi-camera Sync hub Pro diagram

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062617/image013-1-1024x428.png)

#### 4. Planning Camera Settings and Software Configurations <a href="#id-4.-planning-camera-settings-and-software-configurations" id="id-4.-planning-camera-settings-and-software-configurations"></a>

See Orbbec SDK and Orbbec SDK K4A Wrapper for info on setting up the software to control cameras and use image data.

This section discusses factors that affect synchronized devices together rather than individual devices. The software should account for these factors.

**4.1 Exposure Considerations**

To precisely align device exposure timing, we recommend using manual exposure. With auto exposure, each color camera may dynamically change the actual exposure value. Since the exposure duration affects timing, such changes impact sync effectiveness.

Avoid repeating the same exposure settings in image capture loops unless necessary. Call the API just once if possible.

**4.2 Avoiding Interference Between Depth Cameras**

If multiple depth cameras image overlapping fields of view, each must image using its own associated laser. To prevent interference between lasers, the camera captures should be offset from each other by 160us or more.

For each depth camera capture, the laser fires 9 times, active for just 125us each time. The laser then idles for 1450us or 2390us depending on mode. This behavior means the offset calculation starts from 125us.

In addition, the difference between the camera clock and device firmware clock increases the minimum offset to 160us. To calculate a more precise offset based on your configuration, note the depth mode used and reference the Depth Sensor Raw Timing table. Using the data in this table, the minimum offset (exposure time for each camera) can be computed as:

Where:

* Infrared pulse = Number of laser pulses per exposure, which is 9
* Pulse width = Duration laser is active per pulse
* Idle cycle = Number of idle periods per exposure, which is 8
* Idle time = Duration of each idle period

With a 160us offset, up to 9 additional depth cameras can be configured so that when one laser fires, the others remain idle.

In software, use depth\_delay\_off\_color\_usec or subordinate\_delay\_off\_master\_usec to ensure each infrared laser fires within its corresponding 160us window, or has a different field of view.

**Note:** The actual pulse width is 125us but we state 160us to provide some margin. As an example with NFOV UNBINNED, after each 125us pulse there is a 1450us idle. Adding those up – (9 x 125) + (8 x 1450) – gives the exposure time of 12.8ms. The trick to interleaving exposure across two devices is to have the first pulse of the second camera land in the first idle period of the first camera. The delay between the first and second camera can be as little as 125us (the pulse width) but we recommend a margin, so we state 160us. Given 160us, up to 10 cameras could interleave exposure times.

#### 5. Preparing Devices and Other Hardware <a href="#id-5.-preparing-devices-and-other-hardware" id="id-5.-preparing-devices-and-other-hardware"></a>

In addition to configuring multiple Femto Bolt devices, other hosts and hardware may be needed to support the configuration you intend to build. Use the info in this section to ensure all devices and hardware are ready before starting setup.

**5.1 Femto Bolt Devices**

For each Femto Bolt device to be synced:

* Ensure the latest firmware is installed on the device. See Update Femto Bolt Firmware for details on updating firmware.
* Note the serial number of each device. This will be needed later during setup.

**5.2 Host PCs**

It is typical to connect multiple Femto Bolts to dedicated host PCs individually, with dedicated host controllers depending on how the devices are used and the amount of data transferred over USB connections.

Ensure Orbbec SDK or Orbbec SDK K4A Wrapper is installed on the hosts. See Download Orbbec SDK and K4A Wrapper for details on installing the SDK.

**5.3 Linux Machines: USB Memory on Ubuntu**

By default, Linux-based hosts allocate just 16MB kernel memory for USB transfers per controller to handle USB transfers. This is often sufficient for a single Femto Bolt device. But more memory per controller is needed to support multiple devices. To increase the memory:

1. Edit /etc/default/grub.
2.  Find the line:

    ```
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    ```
3.  Change it to:

    ```
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.usbfs_memory_mb=128"
    ```
4. Run sudo update-grub.
5. Reboot the machine.

**Note:** These commands set the USB memory to 128MB. This example is 8X the default setting. Much larger values can be set as appropriate for the solution.

**5.4 Cables**

To interconnect devices and connect to hosts, Multi-camera Sync Cables, network cables, and a sync hub must be used. Network cable lengths should be less than 10m.

The number of cables needed depends on the number of devices and the specific device configuration. Sync cables and hub are not included with Femto Bolt cameras. Sync cables, hub, and network cables must be purchased separately.

#### 6. Connecting Devices in Star Configuration <a href="#id-6.-connecting-devices-in-star-configuration" id="id-6.-connecting-devices-in-star-configuration"></a>

1. Connect each Femto Bolt device to power.
2. Connect each device to its own host computer.
3. Choose one device to be the master and connect its sync cable.
4. Connect the other end of that sync cable to a T568B to T568B network cable, with the network cable going into the Primary In port on the professional star sync hub.
5. To connect another device, attach its sync cable to the Femto Bolt sync port and connect it via network cable to the other sync cable end, with the network cable going into the first subordinate port on the hub: Secondary Cam 1. The second subordinate connects to Secondary Cam 2, and so on.
6. Repeat for all devices.

#### 7. Connecting Devices in Daisy Chain Configuration <a href="#id-7.-connecting-devices-in-daisy-chain-configuration" id="id-7.-connecting-devices-in-daisy-chain-configuration"></a>

1. Connect each Femto Bolt device to power.
2. Connect each device to its own host computer.
3. Choose one device to be the master and connect its sync cable.
4. Connect the other end of that sync cable to the Primary In port on the daisy chain sync hub.
5. To connect another device, attach its sync cable to the Femto Bolt sync port and connect the other end to the first subordinate port on the hub: Secondary Cam 1. The second subordinate connects to Secondary Cam 2, and so on.
6. Repeat for all devices.

**Note:** The daisy chain connection provides a developer version of sync hub and cables not supporting network cable connections like the professional star version hub. See the Multi-Camera Sync Hub Specs for details.

#### 8. Verifying Devices Are Connected and Communicating <a href="#id-8.-verifying-devices-are-connected-and-communicating" id="id-8.-verifying-devices-are-connected-and-communicating"></a>

To verify devices are connected properly, use the K4A Viewer. Repeat this process as needed to test each subordinate device paired with the master.

**Important:** During testing, you must know the serial number of each Femto Bolt.

1. Open two instances of the K4A Viewer.
2. Under “Open Device”, select the serial number of the subordinate device to test.

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062620/image015-1.png)

3.Under External Sync options, select Sub.

![Official Orbbec Femto Bolt figure from Synchronize Multiple Femto Bolt Devices](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07062623/image017-1.png)

4.Select Start.

**Note:** Since this is a subordinate device, the K4A Viewer will not show images after starting the device. Images are not displayed until the subordinate receives the sync signal from the master.

5. After starting the subordinate, use the other instance of the K4A Viewer to open the master device.
6. Under External Sync options, select Master.
7. Select Start.

Once the Femto Bolt master starts, both instances of the K4A Viewer should display images.

**Note:** In K4A Viewer, Master corresponds to Primary master, and Sub corresponds to Secondary subordinate.

#### 9. Calibrating Synchronized Multi-Device Setups <a href="#id-9.-calibrating-synchronized-multi-device-setups" id="id-9.-calibrating-synchronized-multi-device-setups"></a>

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

Once devices are verified communicating, they can be calibrated to generate images in a unified domain.

Within a single device, the depth and RGB cameras are factory calibrated to work together. But when using multiple devices together, they must be calibrated to determine how to transform images from the camera domain they were captured in to the camera domain used for processing the images.

Several options exist for cross calibrating devices. A GitHub green screen code sample using OpenCV methods is provided here. The readme with this code example provides more details and guidance on calibrating devices.

See Calibration Functions for more on calibration.

#### 10. Next Steps <a href="#id-10.-next-steps" id="id-10.-next-steps"></a>

After setting up synchronized devices, you can also learn about:

* [K4A Recorder](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt%20Recorder)

#### Record Multi-Device Synchronized Data with Femto Bolt Recorder <a href="#record-multi-device-synchronized-data-with-femto-bolt-recorder" id="record-multi-device-synchronized-data-with-femto-bolt-recorder"></a>

_Reviewed source:_ [_Record Multi-Device Synchronized Data with Femto Bolt Recorder_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Record%20Multi-Device%20Synchronized%20Data%20with%20Femto%20Bolt%20Recorder)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.

Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

This document covers how to record data from multiple primary-secondary synchronized devices.

#### 1. Prerequisites <a href="#id-1.-prerequisites-2" id="id-1.-prerequisites-2"></a>

* [Synchronize Multiple Devices](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Synchronize%20Multiple%20Femto%20Bolt%20Devices)

#### 2. External Sync Constraints <a href="#id-2.-external-sync-constraints" id="id-2.-external-sync-constraints"></a>

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

First, connect the master and subordinate devices according to the product multi-device sync documentation.

* All master and subordinate devices must use the same camera configuration (fps and resolution).
* All master and subordinate devices must run the same device firmware ([Update Device Firmware](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Update%20Femto%20Bolt%20Firmware)).
* It is recommended to start all subordinate devices first, then the master device.
* The same exposure values should be set on all devices.
* The “Subordinate Delay Off Master” is set per subordinate device relative to the master.

#### 3. Recording with Each Device on Separate Host PC <a href="#id-3.-recording-with-each-device-on-separate-host-pc" id="id-3.-recording-with-each-device-on-separate-host-pc"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.

Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

In the following example, each device has its own dedicated host PC. We recommend dedicating devices to PCs to avoid USB bandwidth and CPU/GPU usage issues.

**3.1 Subordinate-1**

1. Set up recorder on first unit

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
k4arecorder.exe --external-sync sub -e -8 -r 5 -l 10 sub1.mkv
```

2. Device starts waiting

Console:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
Device serial number: 000011590212
Device version: Rel; C: 1.5.78; D: 1.5.60[6109.6109]; A: 1.5.13
Device started
[subordinate mode] Waiting for signal from master
```

**3.2 Subordinate-2**

1. Set up recorder on second unit

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
k4arecorder.exe --external-sync sub -e -8 -r 5 -l 10 sub2.mkv
```

2. Device starts waiting

Console:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
Device serial number: 000011590212
Device version: Rel; C: 1.5.78; D: 1.5.60[6109.6109]; A: 1.5.13
Device started
[subordinate mode] Waiting for signal from master
```

**3.3 Master**

1. Start recording on master device

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
>k4arecorder.exe --external-sync master -e -8 -r 5 -l 10 master.mkv
```

2. Wait for recording to complete

#### 4. Recording with Multiple Devices Connected to Single Host PC <a href="#id-4.-recording-with-multiple-devices-connected-to-single-host-pc" id="id-4.-recording-with-multiple-devices-connected-to-single-host-pc"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.

Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

Multiple Femto Bolts can be connected to a single host PC. However, this may require high USB bandwidth and host compute requirements. To reduce demands:

* Connect each device to its own USB host controller
* Use a powerful GPU that can handle the depth engine for each device
* Only record required sensors and use lower frame rates
* Always start subordinate devices first, master device last

**4.1 Subordinate-1**

1. Start recorder on subordinate device

\>k4arecorder.exe --device 1 --external-sync subordinate --imu OFF -e -8 -r 5 -l 5 output-2.mkv

2. Device enters waiting state

**4.2 Master**

1. Start master device

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
>k4arecorder.exe --device 0 --external-sync master --imu OFF -e -8 -r 5 -l 5 output-1.mkv
```

2. Wait for recording to complete

#### 5. Playing Back Recordings <a href="#id-5.-playing-back-recordings" id="id-5.-playing-back-recordings"></a>

{% hint style="info" %}
Retained `-e -8` recorder examples use older exposure syntax. The [reviewed K4A v2-main parser](https://github.com/orbbec/OrbbecSDK-K4A-Wrapper/blob/c469e24e63958d0aa62e3a0cb44b0cfb3095e721/tools/k4arecorder/main.cpp) instead accepts `-e` in 100–409500 microseconds; `sub` and `subordinate` are both accepted. Match the installed binary; inspect `--help` before adapting exposure. Typographic long dashes in command flags are normalized to ASCII below.
{% endhint %}

Use [K4A Viewer for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt) to play back recordings.

#### 6. Tips <a href="#id-6.-tips" id="id-6.-tips"></a>

* Record with manual exposure on synchronized cameras. RGB camera auto exposure can affect timing sync.
* Restarting a subordinate device will lose sync.
* Some [Hardware Specifications](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Femto%20Bolt%20Hardware%20Specifications)have max 15 fps support. We recommend not mixing modes/frame rates between devices.
* Connecting multiple units to a single PC can easily saturate USB bandwidth, consider dedicating host PCs per device. Also be mindful of CPU/GPU compute.
* Disable IMU if not needed to improve reliability.

See [Known Issues and Troubleshooting for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Known%20Issues%20and%20Troubleshooting%20for%20Femto%20Bolt)for any issues.

#### 7. Also See <a href="#id-7.-also-see" id="id-7.-also-see"></a>

* [Synchronize Multiple Devices](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Synchronize%20Multiple%20Femto%20Bolt%20Devices)
* [K4A Recorder for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt%20Recorder)and other info.
* [K4A Viewer for Femto Bolt](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/K4A%20Viewer%20for%20Femto%20Bolt)or configure RGB camera attributes not available via recorder.
* Update Device Firmware.

#### Known Issues and Troubleshooting for Femto Bolt <a href="#known-issues-and-troubleshooting-for-femto-bolt" id="known-issues-and-troubleshooting-for-femto-bolt"></a>

_Reviewed source:_ [_Known Issues and Troubleshooting for Femto Bolt_](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation/Known%20Issues%20and%20Troubleshooting%20for%20Femto%20Bolt)_. Manufacturer figures and source examples retain their original attribution and rights._

This page contains known issues that may be encountered when using Orbbec SDK K4A Wrapper with Femto Bolt, along with troubleshooting tips.

#### 1. Known Issues <a href="#id-1.-known-issues" id="id-1.-known-issues"></a>

On Linux platforms, the depth engine library requires OpenGL. If the application layer also uses OpenGL and makes cross-thread calls to OpenGL instances, context conflicts may occur, causing issues during depth engine initialization and inability to start the depth data stream properly.

If the application layer uses OpenGL rendering, the application layer needs to switch the Context under OpenGL: (https://www.khronos.org/opengl/wiki/OpenGL\_and\_multithreading)

Below is our solution using the glfw library:

1. Call glfwMakeContextCurrent(NULL) before starting the stream.
2. Then start the stream.
3.  After the stream is finished, call glfwMakeContextCurrent(currentContext).

    ```
    // github： file: tools/k4aviewer/k4adevicedockcontrol.cpp
    GLFWwindow *currentContext = glfwGetCurrentContext(); // store the current context
    glfwMakeContextCurrent(NULL);  // make current context to NULL

    StartCameras(); //  will initialize the DepthEngine

    glfwMakeContextCurrent(currentContext); // restore the current context
    ```

See GitHub Issues for other related issues.

#### 2. Collecting Logs <a href="#id-2.-collecting-logs" id="id-2.-collecting-logs"></a>

Orbbec SDK K4A Wrapper logs are output by the underlying Orbbec SDK, by default to the Log directory under the application working directory. Logs are output in a cyclical overwrite manner to a fixed 4 files, with a default maximum of 100MB per file. It is recommended to package log files when reporting issues.

#### 3. Device Not Listed in Device Manager <a href="#id-3.-device-not-listed-in-device-manager" id="id-3.-device-not-listed-in-device-manager"></a>

* Check the indicator light on the back – if blinking orange, power is insufficient. Try powering with the power adapter again. If it blinks white at that point, the USB connection is abnormal.
* Verify the power cable is connected and a USB3 port is being used for data transfer.
* Try a different USB3 port for the data connection (ports near the motherboard are recommended, e.g. rear USB ports on a PC).
* Inspect cable condition – damaged or poor quality cables can cause unreliable listings (device “blinking” in device manager).
* If connected to a laptop running on battery, the port power may be restricted.
* Restart the host computer.
* If the issue persists, there may be a compatibility problem.

#### 4. K4A Viewer Cannot Open Camera <a href="#id-4.-k4a-viewer-cannot-open-camera" id="id-4.-k4a-viewer-cannot-open-camera"></a>

* First check the device appears in Windows Device Manager.

![Official Orbbec Femto Bolt figure from Known Issues and Troubleshooting for Femto Bolt](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2023/12/07061139/20231207.png)

* Verify no other applications are using the device (e.g. Windows Camera app). Only one application can access the device at a time.
* Check log files for error messages.
* Open the Windows Camera app to verify it works properly.
* Power cycle the device, wait for streaming LED to go out, then retry using the device.
* Restart the host computer.
* Ensure latest graphics drivers are installed on the computer.
* If using your own SDK build, try the official release version if possible to resolve the issue.

#### 5. Device Firmware Update Issues <a href="#id-5.-device-firmware-update-issues" id="id-5.-device-firmware-update-issues"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

* If the reported version number after update is incorrect, closing and reopening the device may be needed.
* If the device firmware update process was interrupted, repowering the device before retrying the update.

#### 6. Image Quality Issues <a href="#id-6.-image-quality-issues" id="id-6.-image-quality-issues"></a>

* Launch the K4A Viewer to inspect device positioning for interference, sensor occlusion, or lens dirt.
* If the issue occurs in a specific mode, try different operating modes to narrow down the investigation.
* To work with the team on image quality issues:
  * Grab a paused snapshot from the K4A Viewer and screenshot
  * Record with the K4A Recorder, e.g. k4arecorder.exe -l 5 -r 5 output.mkv

#### 7. Inconsistent or Unexpected Device Timestamps <a href="#id-7.-inconsistent-or-unexpected-device-timestamps" id="id-7.-inconsistent-or-unexpected-device-timestamps"></a>

Calling _k4a\_device\_set\_color\_control_ can temporarily trigger timing changes in the device that may take a few captures to stabilize. Avoid calling the API in image capture loops to avoid resetting internal timing calculations per new image. Call it instead before starting cameras or when values need to change within image capture loops. Specifically avoid _k4a\_device\_set\_color\_control(K4A\_COLOR\_CONTROL\_AUTO\_EXPOSURE\_PRIORITY)_.

#### 8. Using Body Tracking SDK with Unreal <a href="#id-8.-using-body-tracking-sdk-with-unreal" id="id-8.-using-body-tracking-sdk-with-unreal"></a>

To use the Body Tracking SDK with Unreal, ensure \tools is added to the PATH environment variable, and _dnn\_model\_2\_0.onnx_ + _cudnn64\_7.dll_ are copied to _Program Files/Epic Games/UE\_4.23/Engine/Binaries/Win64_.

#### 9. Using Femto Bolt on Headless Linux Systems <a href="#id-9.-using-femto-bolt-on-headless-linux-systems" id="id-9.-using-femto-bolt-on-headless-linux-systems"></a>

The Femto Bolt depth engine uses OpenGL on Linux. OpenGL requires a window instance, which needs a monitor connected to the system. The workaround is:

1. Enable auto-login for the user account planned for use. See this for instructions on enabling auto-login.
2. Power down the system, disconnect the display, then power on the system. Auto-login will force creation of an x-server session.
3. Connect via ssh and set the DISPLAY environment variable _export DISPLAY=:0_
4. Launch the Femto Bolt application.

The xtrlock utility can be used to immediately lock the screen after auto-login. Add the following command to launch the application or systemd service: _bash -c “xtrlock -b”_

#### 10. Missing C# Documentation <a href="#id-10.-missing-c-documentation" id="id-10.-missing-c-documentation"></a>

Sensor SDK C++ documentation is located [here](https://microsoft.github.io/Azure-Kinect-Sensor-SDK/master/namespace_microsoft_1_1_azure_1_1_kinect_1_1_sensor.html).

Body Tracking SDK C++ documentation is located [here](https://microsoft.github.io/Azure-Kinect-Body-Tracking/release/1.x.x/namespace_microsoft_1_1_azure_1_1_kinect_1_1_body_tracking.html).

#### Development Resources <a href="#development-resources" id="development-resources"></a>

* [Official Femto Bolt documentation](https://doc.orbbec.com/documentation/Orbbec%20Femto%20Bolt%20Documentation)
* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
* [Femto Bolt CAD files](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Femto_Bolt.zip)
