---
description: >-
  Power and mount the compact Gemini 335, choose resolution-dependent near
  limits, start depth capture and sample a calibrated patch using Orbbec SDK
  v2.10.6.
---

# Orbbec Gemini 335: USB depth capture and SDK development

{% hint style="info" %}
[**Orbbec Gemini 335 Compact USB Stereo Depth Camera on OpenELAB**](https://openelab.io/products/orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging)

**Model:** Gemini 335 · **SKU:** `ORBBEC-Gemini-335` · **Option:** 50 mm-baseline USB camera; not 335L, 335Le or the IR-pass Gemini 336.
{% endhint %}

Gemini 335 is a compact USB RGB-D camera with onboard stereo depth processing, global-shutter infrared sensors, rolling-shutter color and a six-axis IMU. This guide establishes one powered USB 3 connection, demonstrates live depth and supplies an original numerical check using a pinned SDK release.

## Product overview

### Orbbec Gemini 335 Stereo Vision Camera with Infrared Imaging <a href="#orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging" id="orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging"></a>

Gemini 335 is the all-pass compact member of the 330 family. The 50 mm stereo baseline favors compact packaging and close scenes compared with the 95 mm long models. USB Type-C carries both power and data. It can expose depth, color, infrared and IMU streams; the host still needs adequate power, bandwidth and processing for simultaneous streams. [USB datasheet V1.8](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf)

Use the [330-series comparison](orbbec-gemini-330-series-user-manual.md) for 336, 335L, 336L and 335Le differences. Do not copy the Ethernet model's auxiliary pinout or the long model's near-limit table into a 335 installation.

## Applications

* Bench robotics and depth-algorithm development where a single USB connection is convenient.
* Short-range geometry and point-cloud experiments with a calibrated, textured scene.
* RGB-D capture and IMU logging, after checking spatial transforms and timestamp domains.
* Evaluating active versus passive stereo under controlled lighting and target materials.

The rolling-shutter color sensor can distort a fast-moving scene even when the depth infrared sensors use global shutter. Missing depth on glossy, dark or transparent surfaces must remain invalid in application logic; a hole-filled image is not independent evidence of an obstacle-free region.

## Specifications

Values are for **Gemini 335**, [USB datasheet V1.8, 13 October 2026, pp.11–12, 16 and 58–59](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf). Rates and minimum distance depend on the selected profile.

| Parameter                         | Gemini 335                                                                                          |
| --------------------------------- | --------------------------------------------------------------------------------------------------- |
| Depth technology / processor      | Active/passive stereo / MX6800 onboard processing                                                   |
| Baseline / projector              | 50 mm / 850 nm                                                                                      |
| Ideal range / broad working range | 0.26–3 m / 0.1–20 m+; broad range is scene-dependent and long-range claim assumes reflectivity >10% |
| Depth FOV                         | 90° × 65° ±3°, 1280 × 800 at 2 m                                                                    |
| Full-resolution depth             | 1280 × 800 at up to 30 fps                                                                          |
| Color                             | Rolling shutter; up to 1920 × 1080 at 30 fps; FOV 86° × 55° ±3° at 16:9                             |
| Spatial precision                 | ≤1.5% at 2 m, 1280 × 800, central 90% × 90% region                                                  |
| IMU                               | 6 DoF; 50/100/200/500/1000 Hz gyro and accelerometer                                                |
| Interface                         | USB 3.0/2.0 Type-C; 8-pin synchronization connector                                                 |
| Required host supply capability   | 5 V, ≥1.5 A                                                                                         |
| Power summary                     | Average <3 W; peak <6.5 W; typical laboratory configuration measured 2.3 W                          |
| Ambient                           | −10 to +45 °C at 15 fps; −10 to +40 °C for higher-rate 30/60 fps configurations; noncondensing      |
| Size / mass / protection          | 90 × 25 × 30 mm / 97 g / IP5X                                                                       |

### Select the near limit with the profile

| Depth resolution         | Documented minimum-Z |
| ------------------------ | -------------------- |
| 1280 × 800 or 1280 × 720 | 0.26 m               |
| 848 × 480                | 0.18 m               |
| 640 × 480                | 0.17 m               |
| 640 × 360                | 0.14 m               |
| 480 × 270                | 0.11 m               |
| 424 × 240                | 0.10 m               |

These values do not establish the same precision, fill rate or field coverage at every resolution. A first check around 1 m avoids confusing the blind region with a broken sensor. Precision is a spatial-noise metric, not a guarantee of absolute measurement bias. [Depth quality definitions](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)

## Hardware and connections

![Official Orbbec Gemini 335 and 336 side USB and covered sync connectors](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115820/202411035.png)

Official Orbbec mounting-reference illustration. The two sides of the same compact housing are shown; these are not the long-housing connector positions.

### USB supply and cable

Use a data-capable USB 3 cable and a port or powered hub rated to deliver **5 V/≥1.5 A**. A standard 900 mA host port may enumerate successfully and still fail during projector peaks. Test without extension cables, share neither a weak hub power budget nor one saturated controller with several cameras, and check USB negotiation with `lsusb -t` on Linux. [Power-delivery design reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Power%20Delivery%20\(Gemini%20330%20Series\))

When a host is limited to 900 mA, Orbbec documents reducing **335 laser power from level 6 to 4**, then using Refresh. This reduces infrared illumination and can affect indoor low-texture or moving-target results. It is a deliberate alternative configuration, not proof that a weak supply meets the full camera requirement. Do not inject external power into a USB cable or combine supply rails without a designed power path.

### Mounting and connector orientation

The Type-C connector is at one side; the covered sync port is on the opposite side. The camera has a 1/4-20 UNC bottom mount and two rear M3 holes. The mounting reference specifies **5 mm bottom hole depth**, **3 mm rear hole depth**, and **0.4 N·m rear torque**; choose screw length from the engaged depth after the bracket thickness. Do not obstruct the projector/IR/color windows or thermally insulate the whole housing. Check CAD V1.0 versus V2.0: the updated compact housing omits the front rubber feet. [Mounting reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Mounting%20\(Gemini%20330%20Series\)), [CAD revisions](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))

### Eight-pin synchronization interface

| Pin | Function         | Boundary                                                                    |
| --- | ---------------- | --------------------------------------------------------------------------- |
| 1   | VCC reference    | Default 1.8 V; external 1.75–5.25 V reference, ≥100 mA capability when used |
| 2   | GPIO\_OUT        | Output follows VCC                                                          |
| 3   | VSYNC\_OUT       | Output follows VCC                                                          |
| 4   | TIMER\_SYNC\_OUT | Output follows VCC                                                          |
| 5   | RESET\_IN        | Dedicated reset waveform; not a generic control pin                         |
| 6   | VSYNC\_IN        | Logic level follows VCC; VIH = 0.65 × VCC, VIL ≤0.7 V                       |
| 7   | TIMER\_SYNC\_IN  | Follow the separate timing specification                                    |
| 8   | GND              | Signal ground                                                               |

Use the exact connector drawing and its mating-face orientation in [datasheet pp.46–48](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf#page=46). **USB's 5 V power does not make sync pins 5 V by default.** Leave this connector capped for single-camera startup. For multiple cameras use the documented hub/cables, common signal reference, compatible roles and frame settings. USB and Ethernet models have different pin ordering and voltage domains.

## Software and development resources

The original example uses [**Orbbec SDK v2.10.6**](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6) and matching Viewer. Its model table lists **Gemini 335 minimum firmware 1.2.20**, recommended **1.8.10**. The 330-family release row for **1.8.17** supports 338Le/338Lg rather than this camera. Match the supported-product list before any firmware action. [Exact support matrix](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/README.md#14-supported-devices), [firmware table](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))

Use the release's Windows or Linux package for the actual host architecture. Linux device access uses the provided udev rules; Windows metadata registration and application permissions are separate from stream enumeration. The SDK source is MIT-licensed, with additional third-party component notices. ROS 1/2, Python, Unity and Android wrappers are separate integrations: choose their supported branch/version, not a name-matched arbitrary example.

### Depth units, alignment, presets and recording

Keep Y16 pixel values and the frame's `getValueScale()` together: multiplying them yields millimetres. Deprojection needs per-device intrinsics for the active profile. Depth/color alignment needs calibrated extrinsics and a supported alignment mode; resizing one image alone is not alignment. Optical axes are X right, Y down, Z forward. [Programming fundamentals](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Programming%20Fundamentals), [coordinate transforms](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Transform%20Coordinates)

Default preset is the baseline. Hand, High Accuracy, High Density and Medium Density target different fill/edge/noise tradeoffs; change one setting at a time and retain the preset name with recordings. Stop streams before preset changes and allow about 3 seconds before restarting. HDR requires matching exposure sequence/metadata and introduces a motion tradeoff. Decimation changes output resolution; spatial, temporal and hole-filling filters can change edges and latency. Inspect raw depth alongside processed depth before trusting an improvement. [Preset guide](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Presets%20for%20Orbbec%20Gemini%20330%20Series%203D%20Cameras), [filter guide](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Detailed%20Filter%20Reference)

The SDK provides separate examples for depth/color/IR, identity, IMU, hotplug, hardware/software alignment, point clouds, recording/playback and synchronization. Capture a short recording with timestamps before integrating into robot navigation; record host arrival time separately from capture time so dropped frames and transport jitter remain diagnosable. [Examples](https://github.com/orbbec/OrbbecSDK_v2/tree/v2.10.6/examples), [frame metadata](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Frame%20Metadata)

## Getting started

### Obtain one stable depth stream

1. Confirm **Gemini 335** on the camera label and prepare a diffuse target about 1 m away, one USB 3 cable and a 5 V/≥1.5 A-capable USB supply path. Leave sync disconnected.
2. Install the host-matched SDK v2.10.6/Viewer package. On Linux apply its udev rules and reconnect; inspect `lsusb` and `lsusb -t`. A USB 2 link requires cable/port diagnosis before expecting full USB 3 stream combinations.
3. Launch Viewer, select the camera and record model, serial and firmware. Keep one camera connected for the first test.
4. Select Default preset and auto exposure; enable **depth only, Y16, 1280 × 800 at 30 fps**. Inspect target distance, frame counter and metadata. Do not start every stream at its maximum simultaneously.
5. Move the target slowly, then hold it still; compare a few center and edge pixels. Add RGB at an advertised profile, then enable supported depth-to-color alignment if needed.
6. Stop streams before closing Viewer or changing preset/resolution. Save the profile, firmware, exposure and scale for comparison with application results.

**Expected result:** Viewer identifies Gemini 335 and shows a continuous depth plane with plausible distance; invalid borders and difficult materials remain invalid rather than being assumed correct. If full-resolution capture fails, restore a short USB 3 path and inspect power before changing firmware. [Official USB quickstart](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))

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
LD_LIBRARY_PATH="$SDK_ROOT/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}" ./build/roi_depth 1280 800 30 usb
```

The package layout and imported CMake target follow the [v2.10.6 development guide](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/docs/tutorial/installation_and_development_guide.md). If an archive places its CMake config elsewhere, point `OrbbecSDK_DIR` at the directory actually containing that config. Do not mix headers and libraries from different SDK releases.

**Expected result:** the process prints six measurement records and exits successfully after receiving 60 depth frames. Each record includes a frame index, `timestamp_us`, valid sample count and `median_mm`; a diffuse target at about 1 m should give a plausible distance near its measured plane position. Those are expected results, not recorded measurements. An unsupported-profile error means enumerate/select a profile the device actually advertises; do not substitute a color format or interpret compressed depth bytes as Y16. Return code 3 means camera selection was ambiguous; 4 means too few frames arrived. A full invalid patch is reported explicitly rather than treated as zero metres.

## Troubleshooting and FAQs

| Symptom                                   | Check and recovery                                                                                                                               |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Not detected                              | Inspect USB enumeration and cable data capability; apply release udev rules on Linux; close other camera applications; reconnect                 |
| Reports USB 2                             | Confirm SuperSpeed-capable host and cable, full insertion and no USB 2 hub/extension in the route                                                |
| Works until projector/extra streams start | Check 5 V peak supply and shared hub/controller load; depth alone first; use adequate powered USB before evaluating the lower-laser workaround   |
| Blank near object                         | Confirm selected profile's minimum-Z; back the target away and use a matte plane                                                                 |
| Metadata resolution differs               | Inspect decimation; processed dimensions can be lower than the sensor profile                                                                    |
| Misaligned point cloud                    | Restore default mirror/flip/rotation, use calibration and matching alignment profiles; account for rolling color shutter on moving scenes        |
| Restart/preset switch fails               | Stop all streams, wait about 3 seconds, then restart; avoid Factory Calib mode for general use                                                   |
| Color missing after firmware update       | Check supported model/image and completion of ISP update; follow the exact Viewer recovery instructions rather than cross-flashing another model |

**Is 335 interchangeable with Gemini 2 because the housings/CAD are related?** No. Their model-specific firmware and SDK minimums differ. The shared mechanical file does not establish electrical, optical or firmware equivalence.

**Can I call a zero depth reading “zero distance”?** No. Zero is an invalid sample. Record valid fraction and compare stable planar data; a median alone does not establish accuracy or maximum range. [Official troubleshooting](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Troubleshooting), [quality metrics](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                                                                             | Use                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| [USB datasheet V1.8 PDF](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf)                                                                                                                                                                                                                        | Model comparison, formats, minimum-Z, synchronization, supply, thermal and mounting data   |
| [CAD revision table](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))                                                                                                                                                                                         | Select the Gemini 2/Gemini 335 file matching front rubber feet present/absent              |
| [Firmware and changelog](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))                                                                                                                                                                                         | Choose the explicit Gemini 335 supported-model row                                         |
| [SDK v2.10.6 release](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6)                                                                                                                                                                                                                                                                   | Matching Viewer, host library and examples                                                 |
| [USB cable design](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Cable%20\(USB\)%20\(Gemini%20330%20Series\)) / [thermal reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Thermal%20\(Gemini%20330%20Series\)) | Cable/grounding and housing integration                                                    |
| [Multi-camera synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)                                                                                                                                                                                                      | Exact hub/cable topology and model-specific signal scope                                   |
| [Official 330-series documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)                                                                                                                                                                                                                             | Concepts, presets, HDR, filters, SDK examples, wrappers, regulatory resources and licenses |

Direct mechanical downloads: [compact housing CAD V1.0 with front rubber feet](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini2%26Gemini335_CAD_Files_V1.0.zip) and [CAD V2.0 without front rubber feet](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini2%26Gemini335_CAD_Files_V2.0.zip). Match the actual enclosure before bracket design.

### Extended official documentation

These official readers retain the detailed model/concept/sample paths. Use the model and release boundaries above before adapting an advanced example.

| Official reader                                                                                                                                                                                                                                  | Relevant guide section             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [Orbbec GMSL Cameras Supported Hosts and System Requirements](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20&%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements) | Software and development resources |
| [Orbbec SDK Supported Features](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Orbbec%20SDK%20Supported%20Features)                                                                                         | Software and development resources |
| [Transform Coordinates](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Transform%20Coordinates)                                                                                                             | Hardware and connections           |
| [C++ Sample Sync Align Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Sync%20Align%20Viewer)                                                                                         | Software and development resources |
| [ROS1 Tutorial Visualize Point Cloud](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS1%20Tutorial%20Visualize%20Point%20Cloud)                                                                           | Software and development resources |
| [Reference Design - Thermal (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Thermal%20\(Gemini%20330%20Series\))                                               | Hardware and connections           |
| [C Sample Double Infrared Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Double%20Infrared%20Viewer)                                                                                   | Software and development resources |
| [Build Your First Camera Streaming Application](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Build%20Your%20First%20Camera%20Streaming%20Application)                                                     | Getting started                    |
| [About Orbbec Gemini 330 Series](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/About%20Orbbec%20Gemini%20330%20Series)                                                                                     | Product overview                   |
| [C++ Sample Multi Device](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Multi%20Device)                                                                                                     | Software and development resources |
| [Programming fundamentals](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Programming%20fundamentals)                                                                                                       | Software and development resources |
| [Creating Filters Directly](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Creating%20Filters%20Directly)                                                                                                   | Software and development resources |
| [Stereo 3D Camera](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Stereo%203D%20Camera)                                                                                                                     | Software and development resources |
| [C Sample Align Filter Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Align%20Filter%20Viewer)                                                                                         | Software and development resources |
| [C++ Sample Multi Device Sync](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Multi%20Device%20Sync)                                                                                         | Software and development resources |
| [C++ Sample Post Processing](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Post%20Processing)                                                                                               | Software and development resources |
| [Reference Design - Power Delivery (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Power%20Delivery%20\(Gemini%20330%20Series\))                               | Hardware and connections           |
| [ROS1 Tutorial Depth & Color Alignment](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS1%20Tutorial%20Depth%20&%20Color%20Alignment)                                                                     | Software and development resources |
| [C Sample Depth Stream Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Depth%20Stream%20Viewer)                                                                                         | Software and development resources |
| [C++ Sample Playback](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Playback)                                                                                                               | Software and development resources |
| [Explore Camera Functions in Orbbec Viewer (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Explore%20Camera%20Functions%20in%20Orbbec%20Viewer%20\(Gemini%20330%20Series\))             | Software and development resources |
| [Depth from HDR Imaging](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20from%20HDR%20Imaging)                                                                                                       | Software and development resources |
| [Licenses for Orbbec SDK](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Licenses%20for%20Orbbec%20SDK)                                                                                                     | Downloads and technical documents  |
| [Depth Preset Release (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Preset%20Release%20\(Gemini%20330%20Series\))                                                             | Software and development resources |
| [C Sample Hello Orbbec](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Hello%20Orbbec)                                                                                                         | Software and development resources |
| [C++ Sample Point Cloud](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Point%20Cloud)                                                                                                       | Software and development resources |
| [What is a Filter](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/What%20is%20a%20Filter)                                                                                                                   | Software and development resources |
| [Install Orbbec SDK](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Install%20Orbbec%20SDK)                                                                                                                 | Software and development resources |
| [C Sample Hot Plugin](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Hot%20Plugin)                                                                                                             | Software and development resources |
| [Detailed Filter Reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Detailed%20Filter%20Reference)                                                                                                   | Software and development resources |
| [Camera Interface Selection Guide](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Camera%20Interface%20Selection%20Guide)                                                                                   | Hardware and connections           |
| [C Sample Color Stream Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Color%20Stream%20Viewer)                                                                                         | Software and development resources |
| [Build Your First Camera Application](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Build%20Your%20First%20Camera%20Application)                                                                           | Getting started                    |
| [Gemini 330 Series Supported Hosts and System Requirements (GMSL)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Supported%20Hosts%20and%20System%20Requirements%20\(GMSL\))       | Software and development resources |
| [C++ Sample Infrared Stream Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Infrared%20Stream%20Viewer)                                                                               | Software and development resources |
| [Warranties & Terms & Conditions](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Warranties%20&%20Terms%20&%20Conditions)                                                                                   | Downloads and technical documents  |
| [Metadata](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Metadata)                                                                                                                                         | Software and development resources |
| [C Sample HDR Merge](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20HDR%20Merge)                                                                                                               | Software and development resources |
| [ROS1 Wrapper User Manual](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS1%20Wrapper%20User%20Manual)                                                                                                   | Software and development resources |
| [Troubleshooting](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Troubleshooting)                                                                                                                           | Troubleshooting and FAQs           |
| [ROS2 Wrapper User Manual](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS2%20Wrapper%20User%20Manual)                                                                                                   | Software and development resources |
| [Gemini 335Lg Hardware Synchronization](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20335Lg%20Hardware%20Synchronization)                                                                         | Hardware and connections           |
| [C Sample Firmware Update](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Firmware%20Update)                                                                                                   | Troubleshooting and FAQs           |
| [Coordinate Systems (Stereo Vision 3D Camera)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Coordinate%20Systems%20\(Stereo%20Vision%203D%20Camera\))                                                     | Hardware and connections           |
| [Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20335Lg%20Recommended%20FAKRA%20Connector%20&%20Cable%20Specifications)             | Hardware and connections           |
| [Firmware Release (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))                                                                       | Downloads and technical documents  |
| [C++ Sample Save To Disk](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Save%20To%20Disk)                                                                                                   | Software and development resources |
| [C++ Sample HDR Merge](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20HDR%20Merge)                                                                                                           | Software and development resources |
| [C++ Sample Config Depth Work Mode](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Config%20Depth%20Work%20Mode)                                                                             | Software and development resources |
| [Orbbec Gemini 330 Series Documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)                                                                                                                    | Software and development resources |
| [Optical Filters for Stereo Vision 3D Cameras](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Optical%20Filters%20for%20Stereo%20Vision%203D%20Cameras)                                                     | Software and development resources |
| [C Sample Point Cloud](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Point%20Cloud)                                                                                                           | Software and development resources |
| [Optional Depth Preset Update (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Optional%20Depth%20Preset%20Update%20\(Gemini%20330%20Series\))                                           | Getting started                    |
| [ROS1 Tutorial Use Multiple Cameras](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS1%20Tutorial%20Use%20Multiple%20Cameras)                                                                             | Software and development resources |
| [ROS1 Tutorial Start Device Node](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS1%20Tutorial%20Start%20Device%20Node)                                                                                   | Software and development resources |
| [Gemini 330 Series Quickstart Guide (Overall)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Overall\))                                                     | Getting started                    |
| [Download Tools](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20Tools)                                                                                                                           | Downloads and technical documents  |
| [C++ Sample IMU Reader](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20IMU%20Reader)                                                                                                         | Software and development resources |
| [C++ Sample Depth Unit Control](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Depth%20Unit%20Control)                                                                                       | Software and development resources |
| [C++ Sample Color Stream Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Color%20Stream%20Viewer)                                                                                     | Software and development resources |
| [Reference Design - Cable (USB) (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Cable%20\(USB\)%20\(Gemini%20330%20Series\))                                   | Hardware and connections           |
| [C++ Sample Depth Stream Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Depth%20Stream%20Viewer)                                                                                     | Software and development resources |
| [Download CAD Files (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))                                                                 | Downloads and technical documents  |
| [Update Firmware (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Update%20Firmware%20\(Gemini%20330%20Series\))                                                                         | Troubleshooting and FAQs           |
| [Regulatory Compliance and Certificates (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Regulatory%20Compliance%20and%20Certificates%20\(Gemini%20330%20Series\))                       | Downloads and technical documents  |
| [Depth Presets for Orbbec Gemini 330 Series 3D Cameras](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Presets%20for%20Orbbec%20Gemini%20330%20Series%203D%20Cameras)                               | Software and development resources |
| [Set up Cameras for External Synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)                                                                                   | Hardware and connections           |
| [Reference Design - Mounting (Gemini 330 Series)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Mounting%20\(Gemini%20330%20Series\))                                             | Hardware and connections           |
| [C++ Sample Multi Stream](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Multi%20Stream)                                                                                                     | Software and development resources |
| [C++ Sample Firmware Update](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Firmware%20Update)                                                                                               | Troubleshooting and FAQs           |
| [C++ Sample Hello Orbbec](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Hello%20Orbbec)                                                                                                     | Software and development resources |
| [ROS2 Tutorial Use Multiple Cameras](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS2%20Tutorial%20Use%20Multiple%20Cameras)                                                                             | Software and development resources |
| [ROS2 Tutorial Visualize Point Cloud](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS2%20Tutorial%20Visualize%20Point%20Cloud)                                                                           | Software and development resources |
| [C Sample Post Processing](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Post%20Processing)                                                                                                   | Software and development resources |
| [Gemini 330 Series Datasheet (Overall)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\))                                                                     | Hardware and connections           |
| [Gemini 330 Series Quickstart Guide (Ethernet)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Ethernet\))                                                   | Getting started                    |
| [C++ Sample Align Filter Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Align%20Filter%20Viewer)                                                                                     | Software and development resources |
| [Gemini 330 Series Quickstart Guide (GMSL)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(GMSL\))                                                           | Getting started                    |
| [Programming Fundamentals](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Programming%20Fundamentals)                                                                                                       | Software and development resources |
| [C++ Sample Recorder](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Recorder)                                                                                                               | Software and development resources |
| [C++ Sample Device Control](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Device%20Control)                                                                                                 | Software and development resources |
| [C Sample Infrared Stream Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C%20Sample%20Infrared%20Stream%20Viewer)                                                                                   | Software and development resources |
| [Recommended Filter List](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Recommended%20Filter%20List)                                                                                                       | Software and development resources |
| [Frame Metadata](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Frame%20Metadata)                                                                                                                           | Software and development resources |
| [C++ Sample Double Infrared Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Double%20Infrared%20Viewer)                                                                               | Software and development resources |
| [Depth Quality Metrics](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)                                                                                                           | Software and development resources |
| [Gemini 330 Series Quickstart Guide (USB)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))                                                             | Getting started                    |
| [ROS2 Tutorial Start Device Node](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS2%20Tutorial%20Start%20Device%20Node)                                                                                   | Software and development resources |
| [C++ Sample Hot Plugin](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20Hot%20Plugin)                                                                                                         | Software and development resources |
| [Reference Design for Ethernet Device](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20for%20Ethernet%20Device)                                                                         | Software and development resources |
| [Gemini 330 Series Supported Hosts and System Requirements (USB)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Supported%20Hosts%20and%20System%20Requirements%20\(USB\))         | Software and development resources |
| [ROS2 Tutorial Depth & Color Alignment](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/ROS2%20Tutorial%20Depth%20&%20Color%20Alignment)                                                                     | Software and development resources |

## References and validation

Reviewed **24 November 2026** using the current official 330-series documentation, USB datasheet V1.8 and pinned SDK v2.10.6 support table/headers. Official illustrations, CAD and documentation remain Orbbec's material; SDK license and bundled third-party notices apply. No public full hardware schematic was found; the exact interface drawings and SDK APIs are the relevant public integration references.

The setup and original example were source reviewed. **SDK execution and hardware testing were not run.** Expected outputs above are acceptance criteria, not measured results.

### Reviewed engineering reference chapters

The following chapters preserve the existing wiki’s detailed engineering reference: specifications, calibration and coordinate concepts, metadata, filter behavior, source examples, installation procedures, troubleshooting and manufacturer illustrations. They complement the current commissioning guide above. Revision notes beside affected chapters separate historical SDK or host examples from the model-specific power, firmware and first-result path. No historical command, example output or photograph is a claimed test on this unit.

### Orbbec Gemini 335 Stereo Vision Camera with Infrared Imaging <a href="#reference-orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging" id="reference-orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging)

#### About Orbbec Gemini 330 Series <a href="#about-orbbec-gemini-330-series" id="about-orbbec-gemini-330-series"></a>

_Reviewed source:_ [_About Orbbec Gemini 330 Series_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/About%20Orbbec%20Gemini%20330%20Series)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Series Introduction <a href="#id-1.-series-introduction" id="id-1.-series-introduction"></a>

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

#### 2. Orbbec SDK <a href="#id-2.-orbbec-sdk" id="id-2.-orbbec-sdk"></a>

The Orbbec SDK provides low-level sensor access to Gemini 330 series cameras hardware sensors and device configuration. For more details on the Orbbec SDK, please refer to [Orbbec SDK architecture](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Orbbec%20SDK%20Architecture).

#### 3. Orbbec SDK Features <a href="#id-3.-orbbec-sdk-features" id="id-3.-orbbec-sdk-features"></a>

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

#### 4. Camera Tools <a href="#id-4.-camera-tools" id="id-4.-camera-tools"></a>

Orbbec provides the following tools:

* Orbbec Viewer tool, used for monitoring device data streams and configuring different modes,
* Orbbec Quality Assessment Tool, used for assessing camera depth quality.

For detailed instructions on using the Orbbec Viewer, please refer to [Explore camera functions in Orbbec Viewer.](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Explore%20Camera%20Function%20in%20Orbbec%20Viewer)

#### 5. Gemini 330 Series Hardware Requirements <a href="#id-5.-gemini-330-series-hardware-requirements" id="id-5.-gemini-330-series-hardware-requirements"></a>

* Gemini 330 series specifications

[![Group 10.jpg](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/group-10.jpg)](https://doc.orbbec.com/uploads/images/gallery/2025-12/group-10.jpg)

* The Gemini 330 series integrates Orbbec’s latest sensor technology into the camera. For detailed information, please refer to the [Orbbec Gemini 330 series Datasheet](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\)).

#### 6. Typical Scene Captures using Gemini 330 Series Cameras <a href="#id-6.-typical-scene-captures-using-gemini-330-series-cameras" id="id-6.-typical-scene-captures-using-gemini-330-series-cameras"></a>

* \*\*Outdoor performance -\*\*Gemini 335/336

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174701/image001-7.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174705/image003-7.png) |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |

* **Outdoor performance - Gemini 335L/336L/335Lg/335Le**

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174739/image005-6.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174743/image007-5.png) |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |

* **Indoor performance - Gemini 335/336**

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180048/731E5D9D-029B-4550-8964-94D023884644.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180040/F4B07029-8606-41a0-B4C7-DC5BEB73334E.png) |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |

* **Indoor performance - Gemini 335L/336L/335Lg/335Le**

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180753/22EE797E-7B89-4611-9E26-091D4FB5E54B.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180746/BF83A51D-7C77-49bd-AE78-5EC63F5F41C3.png) |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20150036/Gemini335lgdocs202410221.png)             | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20150047/Gemini335lgdocs202410222.png)             |

* **Tiny objects recognition @ 2m**. The tiny cubic of 3cm x 3cm (the smallest cubic on the right side of the RGB figure below) is clearly visible in point cloud.

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/17131154/1.png)

#### Gemini 330 Series Quickstart Guide (USB) <a href="#gemini-330-series-quickstart-guide-usb" id="gemini-330-series-quickstart-guide-usb"></a>

_Reviewed source:_ [_Gemini 330 Series Quickstart Guide (USB)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. What's in The Box for Orbbec Gemini\\\335/336? <a href="#id-1.-whats-in-the-box-for-orbbec-gemini-335-336" id="id-1.-whats-in-the-box-for-orbbec-gemini-335-336"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20062836/quick-start-1.png)

#### 2. What's in The Box for Orbbec Gemini 335L/336L? <a href="#id-2.-whats-in-the-box-for-orbbec-gemini-335l-336l" id="id-2.-whats-in-the-box-for-orbbec-gemini-335l-336l"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20062841/quick-start-2.png)

#### 3. Connect the Orbbec Camera <a href="#id-3.-connect-the-orbbec-camera" id="id-3.-connect-the-orbbec-camera"></a>

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

#### 4. Get Orbbec Viewer <a href="#id-4.-get-orbbec-viewer" id="id-4.-get-orbbec-viewer"></a>

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20063843/quick-start-5-1024x187.png)

#### 5. Launch Orbbec Viewer <a href="#id-5.-launch-orbbec-viewer" id="id-5.-launch-orbbec-viewer"></a>

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

#### 6. Caution <a href="#id-6.-caution" id="id-6.-caution"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20064318/image046.png)

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

#### Build Your First Camera Application <a href="#build-your-first-camera-application" id="build-your-first-camera-application"></a>

_Reviewed source:_ [_Build Your First Camera Application_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Build%20Your%20First%20Camera%20Application)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

#### Introduction <a href="#introduction" id="introduction"></a>

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

#### 1. Prerequisites <a href="#id-1.-prerequisites" id="id-1.-prerequisites"></a>

* Set up the Orbbec device
* Download and install the Orbbec SDK through [https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

#### 2. Headers <a href="#id-2.-headers" id="id-2.-headers"></a>

Include the primary header file for the Orbbec SDK to access its features:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```cpp
#include <iostream>
#include "utils.hpp"
#include "libobsensor/ObSensor.hpp"
#include "libobsensor/hpp/Error.hpp"
```

#### 3. Find an Orbbec Device <a href="#id-3.-find-an-orbbec-device" id="id-3.-find-an-orbbec-device"></a>

First, we need to check how many Orbbec devices are connected to your computer. Use the `queryDeviceList()` function to retrieve the connected devices.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 4. Access Device Information <a href="#id-4.-access-device-information" id="id-4.-access-device-information"></a>

Once you have a device list, open the first device and retrieve some basic information such as the device name and firmware version.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 5. List Sensors <a href="#id-5.-list-sensors" id="id-5.-list-sensors"></a>

Next, explore the sensors available on the device by fetching the sensor list and printing each sensor type.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 6. Error Handling <a href="#id-6.-error-handling" id="id-6.-error-handling"></a>

It’s important to include error handling in your applications. The Orbbec SDK provides detailed exceptions that can be caught to understand what went wrong during execution.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```cpp
catch(ob::Error &e) {
    std::cerr << "Error: " << e.getMessage() << std::endl;
    return -2;
}
```

#### 7. Full Source <a href="#id-7.-full-source" id="id-7.-full-source"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 8. Next Steps <a href="#id-8.-next-steps" id="id-8.-next-steps"></a>

* Learn more about configuring and using individual sensors with the Orbbec SDK.
* Explore advanced features and settings available in the Orbbec SDK documentation.
* Begin integrating Orbbec Device capabilities into your larger projects and applications.

#### Build Your First Camera Streaming Application <a href="#build-your-first-camera-streaming-application" id="build-your-first-camera-streaming-application"></a>

_Reviewed source:_ [_Build Your First Camera Streaming Application_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Build%20Your%20First%20Camera%20Streaming%20Application)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

#### Introduction <a href="#introduction-1" id="introduction-1"></a>

This quickstart guide will walk you through the process of setting up a multi-sensor streaming application using the Orbbec SDK. This application will utilize various sensors and stream their data simultaneously.

The document refers to the C++ sample MultiStream.

#### 1. Prerequisites <a href="#id-1.-prerequisites-1" id="id-1.-prerequisites-1"></a>

* Set up the Orbbec device.
* Download and install the Orbbec SDK through [https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

#### 2. Headers <a href="#id-2.-headers-1" id="id-2.-headers-1"></a>

First, include all the necessary headers for your application:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
#include "window.hpp"
#include "libobsensor/hpp/Pipeline.hpp"
#include "libobsensor/hpp/Error.hpp"
#include <mutex>
#include <thread>
```

#### 3. Initialize the Pipeline <a href="#id-3.-initialize-the-pipeline" id="id-3.-initialize-the-pipeline"></a>

The pipeline manages streams and configurations for different sensors:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Create a pipeline with default device
ob::Pipeline pipe;
// Configure which streams to enable or disable for the Pipeline by creating a Config
std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();
```

#### 4. Configure Streams <a href="#id-4.-configure-streams" id="id-4.-configure-streams"></a>

Configure which streams to enable based on the sensors available on the device:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 5. Start the Main Pipeline <a href="#id-5.-start-the-main-pipeline" id="id-5.-start-the-main-pipeline"></a>

Start the main pipeline with the configured streams:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 6. Handle IMU Data Separately <a href="#id-6.-handle-imu-data-separately" id="id-6.-handle-imu-data-separately"></a>

Due to the high frame rate of IMU sensors, it is beneficial to handle their data in a separate pipeline:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 7. Render Frames <a href="#id-7.-render-frames" id="id-7.-render-frames"></a>

Create a window for rendering the collected frames:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 8. Stop the Pipeline <a href="#id-8.-stop-the-pipeline" id="id-8.-stop-the-pipeline"></a>

Properly stop the pipelines when the application is closing to ensure all resources are freed:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
pipe.stop();
if(imuPipeline) {
    imuPipeline->stop();
}
```

#### 9. Full Source <a href="#id-9.-full-source" id="id-9.-full-source"></a>

This is a brief overview of the complete application, which integrates all components discussed:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 10. Next Steps <a href="#id-10.-next-steps" id="id-10.-next-steps"></a>

* Learn more about configuring and using individual sensors with the Orbbec SDK.
* Explore advanced features and settings available in the Orbbec SDK documentation.
* Begin integrating Orbbec Device capabilities into your larger projects and applications.

#### Stereo 3D Camera <a href="#stereo-3d-camera" id="stereo-3d-camera"></a>

_Reviewed source:_ [_Stereo 3D Camera_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Stereo%203D%20Camera)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Introduction <a href="#id-1.-introduction" id="id-1.-introduction"></a>

A stereo 3D camera is a type of camera equipped with two or more lenses, each with its own image sensor or film frame. This configuration allows the camera to capture images from slightly different angles, simulating the human binocular vision. The primary purpose of a stereo 3D camera is to provide depth perception and create 3D images. The Gemini 330 series 3D cameras combine active and passive stereo vision technologies for seamless operation in both indoor and outdoor conditions.

**Working Principle:**

* **Stereoscopic Vision**: By capturing two images from different perspectives, a stereo 3D camera can calculate the distance to objects in the scene. This process involves measuring the disparity between the two images and using it to triangulate the depth.
* **Image Processing**: Advanced algorithms are used to analyze the images captured by the two lenses. These algorithms match corresponding points in both images to compute depth information, generating a 3D representation of the scene.

For the Orbbec Gemini 330 series cameras, the implementation of the working principle is completed on the Orbbec’s latest custom ASIC.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085557/image001-1.png)

Figure 1. Gemini 335 Stereo 3D Camera

#### 2. Baseline <a href="#id-2.-baseline" id="id-2.-baseline"></a>

The baseline is the distance between the two cameras in a stereo setup, namely, the distance between two IR cameras as shown in Figure 1. A longer baseline increases depth accuracy but also increases the size of the setup. Proper baseline selection is crucial for balancing depth resolution and device compactness.

#### 3. Field of View(FOV) <a href="#id-3.-field-of-view-fov" id="id-3.-field-of-view-fov"></a>

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

#### 4. Blind Spots <a href="#id-4.-blind-spots" id="id-4.-blind-spots"></a>

Blind spots in 3D cameras are areas where the camera cannot capture depth information accurately. These are usually found at the edges of the FOV or the closest distance between the camera and the object. When the object is not visible in either the left or right image, accurate depth information cannot be obtained. The depth camera uses the left camera as the main camera, and the depth blind spots are the green and gray areas shown in the figure below.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085624/image011-1.png)

Figure 5. Depth blind spots

#### 5. Depth Dark Borders <a href="#id-5.-depth-dark-borders" id="id-5.-depth-dark-borders"></a>

Depth black edges, or dark borders, in stereo 3D cameras refer to areas in the depth map where depth information is either missing or incorrect. These edges often appear at the boundaries of objects where there is a significant depth discontinuity.

**Cause of Depth Dark Borders**:

* **Baseline**: Stereo 3D cameras work by capturing two images from slightly different perspectives and then calculating the disparity (difference) between these images to estimate depth. These occur when objects seen in one image are not visible in the another due to FOV and baseline limitations, as shown in the green blind spots above.
* **Occlusions**: These occur when parts of one image are not visible in the other due to obstruction by an object. This leads to missing depth information, often resulting in black edges in the depth map.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085631/image013-1.png)

Figure 6. Depth Dark Borders

#### 6. Depth Error <a href="#id-6.-depth-error" id="id-6.-depth-error"></a>

The errors of stereo 3D cameras are primarily influenced by disparity errors, which are related to the reflectivity of the measured object, image signal-to-noise ratio, algorithm errors, and other factors.

Depth is consequently derived from this equation:

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085635/image015-1.png)

By differentiating the disparity, we can derive the depth error as follows:

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085639/image017-1.png)

It can be seen that the depth error of binocular vision increases parabolically (proportional to the square of the distance) as the distance increases.

![Official Orbbec figure from Stereo 3D Camera](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/06/07085643/image019-1.png)

Figure 7. Depth error(mm) as the distance(mm) increases

#### Depth from HDR Imaging <a href="#depth-from-hdr-imaging" id="depth-from-hdr-imaging"></a>

_Reviewed source:_ [_Depth from HDR Imaging_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20from%20HDR%20Imaging)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Introduction <a href="#id-1.-introduction-1" id="id-1.-introduction-1"></a>

For image sensors, the primary challenge lies in capturing both dimly lit indoor scenes and brightly illuminated outdoor settings in the same high-quality image, such as photographing a person standing by the window indoors. Typical image sensors generally adjust exposure or gain to ensure quality imaging in low-light or high-illumination conditions. Robots face various challenges in this regard, such as autonomous mobile robots (AMR) that must operate precisely in environments where sunlight and shadow coexist; robotic vacuum cleaners working near windows face issues with (bright and dark areas in the same view)areas overly bright from sunlight and objects too dark from backlighting. In scenarios where dark and bright areas coexist, using long exposure could result in over-exposure of the bright area, while short exposure might fail to capture details in the darker area. The ORBBEC Gemini 330 Series stereo vision 3D cameras also encounter a similar challenge because their 3D images are calculated from a pair of high-quality, left and right images.

![Official Orbbec figure from Depth from HDR Imaging](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26030607/image001.png)

Figure 1. The scene near the windows. Bright and black areas in the same view.

High Dynamic Range (HDR) imaging in computer vision and cinematography is a set of techniques aiming at handling enormously wide exposure range (i.e., images with greater contrast between light and dark) compared to traditional digital imaging technologies, by merging multiple frames. For 3D depth cameras, higher dynamic range means higher depth fill-rate and higher accuracy, significantly enhancing a robot’s obstacle avoidance capabilities. This paper introduces fundamental concepts related to HDR functionality and introduces how HDR is utilized in the ORBBEC Gemini 330 Series cameras.

#### 2. Sensor Settings <a href="#id-2.-sensor-settings" id="id-2.-sensor-settings"></a>

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

| Framerate（fps） | Max Exposure Time (us) |
| -------------- | ---------------------- |
| 60             | 16,000                 |
| 30             | 32,000                 |
| 15             | 65,000                 |
| 6              | 166,000                |

Table 1. Max exposure per frame rate

#### 3. High Dynamic Range <a href="#id-3.-high-dynamic-range" id="id-3.-high-dynamic-range"></a>

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 4. Summary <a href="#id-4.-summary" id="id-4.-summary"></a>

Gemini 330 series cameras provide high-quality depth imaging. It's built-in automatic exposure mode can meet user needs in most scenarios, both indoor and outdoor. For autonomous mobile robots equipped with these cameras, the automatic exposure generally provides sufficient adaptability to handle varying lighting conditions effectively. Since the auto-exposure algorithm is implemented in the firmware, it does not consume resources from the host equipment and simplifies user operation.

Manual exposure is typically used in scenarios requiring precise exposure control, such as factory robotic arms pan-picking, where it is only necessary to enhance the imaging quality of the workpieces.

HDR in depth sensor is designed to address some challenges that neither automatic nor manual exposure can solve. It significantly improves the fill rate in tough working environments with complicated illumination or reflection situations, and also improves the depth accuracy in these areas. It reduces the risk of two common and serious errors in computer vision systems: "missed detection" and "false detection". In some use cases, these errors can even be fatal.

As every technology people developed, it of course has its own limitations, such as frame delay and CPU usage due to extra calculation on the host; experience required to determine proper high and low exposure times; motion artifacts for high-speed moving objects.

In scenes with rapid camera movement, adjusting the mean intensity of the auto-exposure can improve image stability. If needed, enabling HDR and HDR merge can enhance detail capture at the cost of a higher frame rate. For applications requiring precise depth data, activate HDR but avoid merging depth frames, using both high and low exposure frames to meet specific algorithmic needs. This setup ensures detailed and accurate depth information under varying lighting conditions.

#### 5. References <a href="#id-5.-references" id="id-5.-references"></a>

* HDR imaging with OpenCV – [https://docs.opencv.org/3.4/d2/df0/tutorial\_py\_hdr.html](https://docs.opencv.org/3.4/d2/df0/tutorial_py_hdr.html)
* High dynamic range – [https://en.wikipedia.org/wiki/High\_dynamic\_range](https://en.wikipedia.org/wiki/High_dynamic_range)

#### Optical Filters for Stereo Vision 3D Cameras <a href="#optical-filters-for-stereo-vision-3d-cameras" id="optical-filters-for-stereo-vision-3d-cameras"></a>

_Reviewed source:_ [_Optical Filters for Stereo Vision 3D Cameras_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Optical%20Filters%20for%20Stereo%20Vision%203D%20Cameras)_. Manufacturer figures and source examples retain their original attribution and rights._

In this document, we discuss the use of optical filters in stereo vision 3D cameras. More specifically, we are going to first investigate the optical characteristics of different filter types and then optimize the 3D camera performance under challenging lighting conditions with properly selected optical filters, where significantly improved imaging quality can be observed in test images.

#### 1. Introduction <a href="#id-1.-introduction-2" id="id-1.-introduction-2"></a>

The performance of stereo vision 3D cameras is directly related to the quality of the input stereo image pairs. Therefore, in certain scenarios, it’s beneficial to use additional optical components to enhance the imaging quality of the stereo camera, thereby improving the performance of the depth perception. In this document, we focus primarily on optical filters, which can avoid critical imaging issues if applied appropriately and are generally available at affordable cost.

#### 2. What is an Optical Filter? <a href="#id-2.-what-is-an-optical-filter" id="id-2.-what-is-an-optical-filter"></a>

An optical filter is an optical component designed to selectively transmit or block specific wavelengths of light. They are typically made of specific materials or coated with films to achieve desired optical properties, used to control the propagation of light in optical systems. For stereo vision 3D cameras, placing filters of specific wavelength bands on top of the cover glass can help selectively transmit or block light within certain wavelength ranges, thereby significantly enhancing imaging quality.

#### 3. Types of Optical Filters <a href="#id-3.-types-of-optical-filters" id="id-3.-types-of-optical-filters"></a>

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

#### 4. Challenges of Stereo Vision 3D Cameras <a href="#id-4.-challenges-of-stereo-vision-3d-cameras" id="id-4.-challenges-of-stereo-vision-3d-cameras"></a>

**4.1 Sensitivity to Ambient Light**

Stereo vision usually captures image pairs with ambient light in the environment. However, differences in light intensity and incident light angles between the left and right cameras can lead to significant differences in brightness between the left and right images of a stereo pair, resulting in a sharp decline in algorithmic matching effectiveness.

**4.2 Poor Performance in Monotonous and Textureless Scenes**

Stereo vision relies on visual features for image matching. Therefore, scenes lacking visual features, such as the sky or white walls, can pose matching difficulties, leading to significant matching failures or even errors. Adding laser speckle projection can enhance features in low-texture scenes, but in certain situations, ambient light can reduce the contrast of laser speckles or even obscure their grayscale information.

#### 5. Using Filters <a href="#id-5.-using-filters" id="id-5.-using-filters"></a>

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

#### Depth Quality Metrics <a href="#depth-quality-metrics" id="depth-quality-metrics"></a>

_Reviewed source:_ [_Depth Quality Metrics_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Use an independently measured reference plane and calibrated optical origin; exclude invalid zeros and record ROI, fit/outlier policy, distance and mode. Accuracy (bias), spatial plane residual and temporal noise are different quantities. The source pseudocode’s `CP_Length`/`CP_Dist` naming is normalized here to `CP_Dist`; fitted-plane residuals alone do not establish absolute accuracy.
{% endhint %}

#### 1. Terminology <a href="#id-1.-terminology" id="id-1.-terminology"></a>

The table below lists terms and acronyms that appear in this document.

Table 1: Terms and acronyms

| Term | Description         |
| ---- | ------------------- |
| ROI  | Region of Interest  |
| FOV  | Field of View       |
| GT   | Ground Truth        |
| RMS  | Root of Mean Square |
| STD  | Standard Deviation  |

#### 2. Quality Metrics <a href="#id-2.-quality-metrics" id="id-2.-quality-metrics"></a>

{% hint style="info" %}
Use an independently measured reference plane and calibrated optical origin; exclude invalid zeros and record ROI, fit/outlier policy, distance and mode. Accuracy (bias), spatial plane residual and temporal noise are different quantities. The source pseudocode’s `CP_Length`/`CP_Dist` naming is normalized here to `CP_Dist`; fitted-plane residuals alone do not establish absolute accuracy.
{% endhint %}

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

| Item           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Category       | Depth accuracy                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Purpose/Goal   | Measure the accuracy of depth images within a specified ROI relative to the GT.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Target         | Reference plane\Wall                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Analyzed Image | Depth image                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ROI            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Description    | This metric measures the per-pixel depth accuracy relative to the GT in a single frame depth image, excluding errors due to camera placement. GT is obtained by measuring the distance from the depth origin to the reference target. Depth accuracy can be calculated using the following formula: Depth\_accuracy\_Signed = Median(CP\_Dist – GT + PP\_Dist) where CP\_Dist represents the actual length between the depth origin and a fitted plane along the GT measuring direction, and PP\_Dist denotes the per-pixel distance of the point cloud to the fitted plane.              |
| Pseudo-Code    | INPUT: Depth\_Image, GT REMOVE all zeros in Depth\_Image COMPUTE Point\_Cloud (X,Y,Z matrix) from Depth\_Image COMPUTE Fitted\_Plane to Point\_Cloud REMOVE outliers: all Z values that below percentile 0.5% and above percentile 99.5% COMPUTE the actual length between the depth origin and the Fitted\_Plane along the GT vector as CP\_Dist COMPUTE distance of all points to the Fitted\_Plane as PP\_Dist COMPUTE Depth\_Error = CP\_Dist – GT + PP\_Dist COMPUTE Median\_Value = 50% percentile value of Depth\_Error OUPUT: Depth\_accuracy\_Signed = 100 \* Median\_Value / GT |
| Output Value   | Depth\_accuracy\_signed                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Output Units   | \[%]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

**2.2 Spatial Precision**

While accuracy concerns the systematic deviation from the true depth, spatial precision relates to the consistency of depth measurements. Spatial precision indicates the noise level of depth data across a planar target. A high spatial precision depth data exhibits low variance in depth values for identical or similar surfaces within the same scene. To assess spatial precision, one can perform measurements of a reference plane at known or controlled locations, calculate the RMS error of the depth values obtained, and compare them against desired precision thresholds or specifications.

RMS error can be expressed in units of distance or disparity, but considering the coupling between depth and noise, it can be normalized by the distance between the camera and the planar target and represented in percentage (%) units.

Table 2 : Spatial Precision

| Item           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Category       | spatial precision                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Purpose/Goal   | Measure the noise level of depth values relative to the best-fit plane.                                                                                                                                                                                                                                                                                                                                                                                                       |
| Target         | Reference plane\Wall                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Analyzed Image | Depth Image                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ROI            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                                                                                                                                         |
| Description    | Calculate the RMS of the distance from each valid pixel to the best-fit plane, normalized by the distance from the optical center to the plane, with the RMS Error output expressed as a percentage.                                                                                                                                                                                                                                                                          |
| Pseudo-Code    | INPUT: Depth\_Image REMOVE all zeros in Depth\_Image COMPUTE Point\_Cloud (X,Y,Z matrix) from Depth\_Image COMPUTE Fitted\_Plane to Point\_Cloud REMOVE outliers: all Z values that below percentile 0.5% and above percentile 99.5% COMPUTE distance between the depth origin and the Fitted\_Plane as CP\_Dist COMPUTE distance of all points to the Fitted\_Plane as PP\_Dist COMPUTE RMSE = RootMeanSquare of PP\_Dist OUPUT: Spatial\_precision = 100 \* RMSE / CP\_Dist |
| Output Value   | Spatial\_precision                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Output Units   | \[%]                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

**2.3 Temporal Precision**

Temporal Precision measures the variation in depth values over time within an ROI. The quality of a depth image can be assessed based on its temporal consistency; high-quality depth images should exhibit smooth and stable depth over time. This method is defined as the STD of depth values across a specific number of frames (for example, 30). The quantification of temporal noise is carried out on a per-pixel basis, followed by calculating the STD of each pixel over a specified time.

Table 3: Temporal Precision

| Item           | Description                                                                                                                                                                                                                                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Category       | Depth temporal noise                                                                                                                                                                                                                                                                                                                                          |
| Purpose/Goal   | Measure the extent of variation in depth values per pixel over time.                                                                                                                                                                                                                                                                                          |
| Target         | wall                                                                                                                                                                                                                                                                                                                                                          |
| Analyzed Image | N sequential depth images                                                                                                                                                                                                                                                                                                                                     |
| ROI            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                                                                                                                                         |
| Description    | Per-pixel temporal noise is defined by measuring the STD of depth values for each pixel across N consecutive frames, resulting in a STD matrix. Temporal Noise is defined as the median of the STD matrix as a percentage of the target distance Z. This metric excludes NaN and zero depth data.                                                             |
| Pseudo-Code    | INPUT: N images of Depth\_Image, GT LOOP for each of N Depth\_Image to create Depth\_Tensor ASSIGN Depth\_Tensor = (Depth\_Image,N) //dimension is (width,height,N) REMOVE all zeros from Depth\_Tensor COMPUTE STD\_Matrix = STD of Depth\_Tensor(width,height,all) COMPUTE Median\_STD = 50% percentile value of STD\_Matrix Output: 100 \* Median\_STD / Z |
| Output Value   | The median value of the STD matrix, divided by distance to wall                                                                                                                                                                                                                                                                                               |
| Output Units   | \[%]                                                                                                                                                                                                                                                                                                                                                          |

**2.4 Fill Rate**

A high-quality depth image should cover the entire field of view uniformly, without missing regions. Fill Rate measures the proportion of non-zero pixels in a depth image, representing the depth coverage. High fill rate indicates that most scene points have been successfully captured.

Table 5: Fill Rate

| Item           | Description                                                                                                                                                                                                                                     |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Category       | Fill rate                                                                                                                                                                                                                                       |
| Purpose/Goal   | Measure the proportion of valid depth values within a specified ROI.                                                                                                                                                                            |
| Target         | Reference plane\Wall                                                                                                                                                                                                                            |
| Analyzed Image | Depth image                                                                                                                                                                                                                                     |
| ROI            | For instance, an 81% ROI corresponds to 90% of the image width multiplied by 90% of the image height.                                                                                                                                           |
| Description    | Calculate the ratio of pixels with valid depth values to all pixels within a specified ROI.                                                                                                                                                     |
| Pseudo-Code    | INPUT: Depth\_Image COMPUTE Total\_Num = size(Depth\_Image) ASSIGN Valid\_Image = Depth\_Image REMOVE all zeros from Valid\_Image COMPUTE Valid\_Num = size(Valid\_Image) COMPUTE Fill\_Rate = 100 \* Valid\_Num / Total\_Num Output Fill\_Rate |
| Output Value   | The proportion of valid pixels within the specified ROI.                                                                                                                                                                                        |
| Output Units   | \[%]                                                                                                                                                                                                                                            |

#### Metadata <a href="#metadata" id="metadata"></a>

_Reviewed source:_ [_Metadata_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Metadata)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

#### 1. Brief Introduction <a href="#id-1.-brief-introduction" id="id-1.-brief-introduction"></a>

Metadata refers to data that provides information about other data. It acts like a descriptive label that helps to identify, manage, and use the actual data more effectively. Metadata can include a variety of details depending on the context:

* **Descriptive Metadata**: This includes information like titles, authors, and keywords which help in discovering and identifying data. For example, the metadata of a book might include its title, author, publisher, and ISBN.
* **Structural Metadata**: This indicates how a dataset is organized or how complex objects are put together. For instance, in a database, structural metadata would describe the tables, columns, relationships, and other structures used to organize data.
* **Administrative Metadata**: This provides information to help manage a resource, like when and how it was created, file type, and access permissions. It might also include technical data necessary for managing digital resources, such as file types or compression methods.
* **Reference Metadata**: It provides information about the contents and quality of statistical data. This type is common in data-centric fields like statistics and data analysis, providing details on data sources, accuracy, and timeliness.

#### 2. Metadata of MIPI <a href="#id-2.-metadata-of-mipi" id="id-2.-metadata-of-mipi"></a>

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

In the context of MIPI, metadata can involve various types of information depending on the application. For example, in camera interfaces like MIPI CSI-2, metadata may include details about camera module parameters, resolution settings, frame rates, color spaces, white balance settings, sharpness, and chrominance. These details are crucial for properly configuring and utilizing the camera module.

Additionally, metadata might also pertain to control information related to data transmission, synchronization, error detection, and correction. This metadata is essential for ensuring the integrity and accuracy of data, especially in environments characterized by high-speed and low-power transmission.

On a broader scale, MIPI metadata may also involve system-level information, such as the connections between devices, data transmission rates, and power consumption budgets. This information aids in system-level design and optimization to ensure optimal performance and power efficiency of the entire system.

The specific definitions and implementations of metadata in the MIPI standards can vary based on different applications and requirements, and the information included in the metadata may differ among various device manufacturers.

#### 3. Gemini 330 Series Metadata Definition <a href="#id-3.-gemini-330-series-metadata-definition" id="id-3.-gemini-330-series-metadata-definition"></a>

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

Orbbec 3D cameras typically include components such as 2 IR modules, LDM, laser ranging module, and a color camera. Both the IR module and the color camera transmit data to the mainboard using the MIPI protocol, thus carrying metadata. Users can utilize the Orbbec SDK to parse this metadata and view it directly within the Orbbec Viewer to see the current data stream’s metadata information.

Taking the Gemini 335 as an example, the supported metadata includes the following content:

Table 1: Depth/IR metadata

| Metadata           | Definition                                  | Range                                                                                                           |
| ------------------ | ------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| timestamp          | exposure end timestamp                      | /                                                                                                               |
| sensor timestamp   | Exposure center timestamp-1/2 exposure time | /                                                                                                               |
| frame number       | current frame number                        | /                                                                                                               |
| auto exposure      | content of AE state                         | \[0,1] 0 for off, 1 for on                                                                                      |
| exposure           | content of exposure time                    | 1\~19900                                                                                                        |
| gain               | content of exposure digital gain            | 16\~248                                                                                                         |
| ae roi left        | ROI AE start pixel X-axis                   | 0\~1278                                                                                                         |
| ae roi top         | ROI AE start pixel Y-axis                   | 0\~798                                                                                                          |
| ae roi right       | ROI AE end pixel X-axis                     | 1\~1279                                                                                                         |
| ae roi bottom      | ROI AE end pixel Y-axis                     | 1\~799                                                                                                          |
| exposure priority  | Content of AE exposure priority state       | \[0,1]                                                                                                          |
| hdr sequence name  | User-defined content                        | User-defined content                                                                                            |
| hdr sequence size  | HDR frame total number                      | \[0,2] 0 for off, 2 for on                                                                                      |
| hdr sequence index | HDR frame sequence                          | \[0,1] 0 for the first frame, 1 for the second frame                                                            |
| laser power        | laser optical power                         | \[0,60,120,240,300,360]                                                                                         |
| laser power mode   | content of laser switch on or off           | \[0,1] 0 for off, 1 for on                                                                                      |
| emitter mode       | Reserved                                    | \[0,1,2,3] 0 – all emitters disabled. 1 – laser enabled. 2 – auto laser enabled (opt). 3 – LED enabled (opt).\* |
| Gpio Input Data    | Reserved                                    | Reserved                                                                                                        |

Table 2: RGB metadata definition

| Metadata               | Definition                                                                       | Range                        |
| ---------------------- | -------------------------------------------------------------------------------- | ---------------------------- |
| timestamp              | 335: exposure start timestamp 335L: exposure end timestamp                       | /                            |
| sensor timestamp       | 335: Exposure center timestamp 335L: Exposure center timestamp-1/2 exposure time | /                            |
| frame number           | current frame number                                                             | /                            |
| auto exposure          | content of AE state                                                              | \[0,1]                       |
| exposure               | content of exposure time(us)                                                     | \[1,10000]                   |
| gain                   | content of exposure digital gain                                                 | \[0,128]                     |
| auto white balance     | content of AWB state                                                             | 0 or 1                       |
| white balance          | current AWB color temperature                                                    | \[2800,6500]                 |
| brightness             | current brightness                                                               | \[-64,64]                    |
| contrast               | contrast                                                                         | \[0,100]                     |
| saturation             | saturation                                                                       | \[0,100]                     |
| sharpness              | sharpness                                                                        | \[0,100]                     |
| backlight compensation | state of backlight compensation enable                                           | \[0,1] 0 for off, 1 for on   |
| hue                    | hue                                                                              | \[-180,180]                  |
| Gamma                  | Gamma                                                                            | \[100,500]                   |
| power line frequency   | anti-flicker state                                                               | \[50,60, disable, auto]      |
| low light compensation | state of low light compensation enable                                           | \[0,1] 0 for off, 1 for on   |
| manual white balance   | current AWB color temperature set manually                                       | \[2800,6500]                 |
| actual frame rate      | frame rate set                                                                   | \[5,10,15,30,60]             |
| ae roi left            | ROI AE start pixel X-axis                                                        | 335 \[0,1918] 335L \[0,1278] |
| ae roi top             | ROI AE start pixel Y-axis                                                        | 335 \[0,1078] 335L \[0,798]  |
| ae roi right           | ROI AE end pixel X-axis                                                          | 335 \[1,1919] 335L \[1,1279] |
| ae roi bottom          | ROI AE end pixel Y-axis                                                          | 335 \[1,1079] 335L \[1,799]  |

When using Orbbec 3D cameras on user platforms, metadata can be utilized to assess frame information, enabling advanced functions such as data correction, frame loss verification, and HDR (High Dynamic Range) fusion. This allows for enhanced accuracy and functionality in applications where precise imaging and data integrity are critical.

#### Coordinate Systems (Stereo Vision 3D Camera) <a href="#coordinate-systems-stereo-vision-3d-camera" id="coordinate-systems-stereo-vision-3d-camera"></a>

_Reviewed source:_ [_Coordinate Systems (Stereo Vision 3D Camera)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Coordinate%20Systems%20\(Stereo%20Vision%203D%20Camera\))_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Brief Introduction <a href="#id-1.-brief-introduction-1" id="id-1.-brief-introduction-1"></a>

Gemini 330 series 3D camera usually contains depth camera, color camera, and IMU. Those sensors collect information and output it as streams.

In order to characterize the positional relationship better, the Orbbec Gemini 330 series define 3D camera coordinate system. The coordinate system of a 3D camera typically contains the Depth coordinate system & the Color coordinate system & the IMU coordinate system.

#### 2. System Coordinate <a href="#id-2.-system-coordinate" id="id-2.-system-coordinate"></a>

Every coordinate usually consists of three components:

1. Origin: The Depth coordinate system’s origin is located at the optical center of the Left IR camera lens. The color coordinate system’s origin is located at the optical center of the Color camera lens. The IMU coordinate system’s origin is located at the physical center of the IMU.
2. Category: meeting the definition of right-hand coordinate system. The positive direction of the X-axis is to the right. The positive direction of the Y-axis is down. The positive direction of the Z-axis is forward. The X, Y, and Z axes are red, green, and blue, respectively.

Picture 1: Right-hand coordinate system

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26075126/image1234ty.png)

1. Unit: The Default unit is millimeters.

#### 3. Gemini 330 Series System Coordinate <a href="#id-3.-gemini-330-series-system-coordinate" id="id-3.-gemini-330-series-system-coordinate"></a>

Gemini 330 series coordinate system reference picture is shown below.

Picture 2: Coordinate system schematic diagram

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22090512/docs20240722-1024x468.png)

The relative position relationship of the coordinate systems' origins is as follows.

Table 1: Relative position of coordinate systems for Gemini 335/336

| Relative position                     | X(mm)  | Y(mm)  | Z(mm)   |
| ------------------------------------- | ------ | ------ | ------- |
| Origin of the Depth coordinate system | 0      | 0      | 0       |
| Origin of the Color coordinate system | 14.00  | 0      | 2.02    |
| Origin of the IMU coordinate system   | -0.246 | -0.065 | -16.948 |

Table 2: Relative position of coordinate systems for Gemini 335L/336L

| Relative position                     | X(mm) | Y(mm) | Z(mm)   |
| ------------------------------------- | ----- | ----- | ------- |
| Origin of the Depth coordinate system | 0     | 0     | 0       |
| Origin of the Color coordinate system | 23.75 | 0     | 0       |
| Origin of the IMU coordinate system   | 7.866 | 1.068 | -14.248 |

#### Orbbec SDK Supported Features <a href="#orbbec-sdk-supported-features" id="orbbec-sdk-supported-features"></a>

_Reviewed source:_ [_Orbbec SDK Supported Features_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Orbbec%20SDK%20Supported%20Features)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

The linked legacy feature workbook uses historical OS/package rows and still labels some Gemini 300 Python support as pending. It is not the v2.10.6 support/firmware matrix. Use the version-pinned core SDK table and each maintained wrapper’s own device list for current integration.
{% endhint %}

#### 1. Introduction <a href="#id-1.-introduction-3" id="id-1.-introduction-3"></a>

Orbbec SDK is a cross-platform (Windows, Android, Linux) software development package for 3D sensor cameras such as Orbbec optical structured light, Binocular, and iToF. It provides device parameter configuration, data stream reading, and stream processing.

#### 2. Core Features <a href="#id-2.-core-features" id="id-2.-core-features"></a>

* Depth camera access and related parameter settings
* RGB camera access and related parameter settings (such as exposure and white balance)
* Sensor access and related parameter settings (e.g. gyroscope and accelerometer)
* Frame synchronization and alignment control
* Point cloud data
* Filtering and other algorithm capabilities
* Support for multiple operating systems and Wrapper.

#### 3. Features Matrix <a href="#id-3.-features-matrix" id="id-3.-features-matrix"></a>

Please refer to this [Features matrix](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/25125938/Features-matrix.xlsx)

#### Install Orbbec SDK <a href="#install-orbbec-sdk" id="install-orbbec-sdk"></a>

_Reviewed source:_ [_Install Orbbec SDK_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Install%20Orbbec%20SDK)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

This document describes how to install the Orbbec SDK via installation packages on both Windows and Linux.

#### 1. Windows Installation Guidance <a href="#id-1.-windows-installation-guidance" id="id-1.-windows-installation-guidance"></a>

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

#### 2. Linux /Arm64 Installation Guidance <a href="#id-2.-linux-arm64-installation-guidance" id="id-2.-linux-arm64-installation-guidance"></a>

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### Programming fundamentals <a href="#programming-fundamentals" id="programming-fundamentals"></a>

_Reviewed source:_ [_Programming fundamentals_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Programming%20fundamentals)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

#### 1. Get the First Orbbec Device <a href="#id-1.-get-the-first-orbbec-device" id="id-1.-get-the-first-orbbec-device"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Context ctx;
auto devList = ctx.queryDeviceList();
auto dev = devList->getDevice(0);
```

#### 2. Start Streaming with Default Configuration <a href="#id-2.-start-streaming-with-default-configuration" id="id-2.-start-streaming-with-default-configuration"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;  // create pipe with default device
pipe.start(nullptr);  // start with defualt configuratio
```

#### 3. Start Streaming Infrared Image <a href="#id-3.-start-streaming-infrared-image" id="id-3.-start-streaming-infrared-image"></a>

For TOF or Single-Camera structured light devices:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;
std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();
auto irProfiles = pipe.getStreamProfileList(OB_SENSOR_IR);
auto irProfile = irProfiles->getProfile(OB_PROFILE_DEFAULT);
config->enableStream(irProfile);
pipe.start(config);
```

For Dual-Camera structured light devices:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 4. Wait for a Coherent Set of Frames <a href="#id-4.-wait-for-a-coherent-set-of-frames" id="id-4.-wait-for-a-coherent-set-of-frames"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;
pipe.start(nullptr);
auto frameSet = pipe.waitForFrames(100);
auto depthFrame = frameSet->depthFrame();
```

#### 5. Do Processing on a Background-Thread <a href="#id-5.-do-processing-on-a-background-thread" id="id-5.-do-processing-on-a-background-thread"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 6. Get Depth-to-Color Extrinsics <a href="#id-6.-get-depth-to-color-extrinsics" id="id-6.-get-depth-to-color-extrinsics"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;
auto depthProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH);
auto depthProfile = depthProfiles->getProfile(OB_PROFILE_DEFAULT);
auto colorProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH);
auto colorProfile = depthProfiles->getProfile(OB_PROFILE_DEFAULT);

auto extrinsics = depthProfile->getExtrinsicTo(colorProfile);
```

#### 7. Get Video Stream Intrinsics <a href="#id-7.-get-video-stream-intrinsics" id="id-7.-get-video-stream-intrinsics"></a>

From pipeline:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;
pipe.start(nullptr);
// get camera intrinsic and extrinsic parameters form pipeline and set to point cloud filter
auto cameraParam = pipeline.getCameraParam();
```

From Frame/StreamProfile (Gemini 300 series only):

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;
pipe.start(nullptr);

auto frameSet = pipe.waitForFrames(100);
auto frame = frameSet->depthFrame();
auto streamProfile = frame->getStreamProfile();
auto videoStreamProfile = streamProfile->as<ob::VideoStreamProfile>();

auto intrinsic = videoStreamProfile->getIntrinsic();
```

#### 8. Get Depth Units <a href="#id-8.-get-depth-units" id="id-8.-get-depth-units"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe;
pipe.start(nullptr);

auto frameSet = pipe.waitForFrames(100);
auto depthFrame = frameSet->depthFrame();

auto uint = depthFrame->getValueScale();
```

#### 9. Controll the Laser <a href="#id-9.-controll-the-laser" id="id-9.-controll-the-laser"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### Frame Metadata <a href="#frame-metadata" id="frame-metadata"></a>

_Reviewed source:_ [_Frame Metadata_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Frame%20Metadata)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

Frame metadata is a set of parameters (or attributes) that provide a snapshot of the sensor configuration and/or system state present during the frame’s generation. The attributes are recalculated and updated on a per-frame basis. Orbbec SDK supports querying a set of predefined attributes as part of the frame data available to the end-user.

#### 1. API <a href="#id-1.-api" id="id-1.-api"></a>

`Orbbec SDK` introduces two functions into its public API to query metadata:

C:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 2. Example <a href="#id-2.-example" id="id-2.-example"></a>

The envisaged mode of querying metadata attribute is `check-then-query`

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 3. Display Frame Metadata in Orbbec Viewer <a href="#id-3.-display-frame-metadata-in-orbbecviewer" id="id-3.-display-frame-metadata-in-orbbecviewer"></a>

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-07/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-07/image.png)

#### 4. OS Support <a href="#id-4.-os-support" id="id-4.-os-support"></a>

_**Windows OS**_ – Metadata extraction is supported by Microsoft starting with Windows 10. Check the Windows installation guide for details.

**Other OS –** We use libuvc/libusb as the default backend, which does not require any operation to enable metadata support.

#### 5. Devices Support <a href="#id-5.-devices-support" id="id-5.-devices-support"></a>

In this referenced API-generation document, the metadata APIs are scoped to the Orbbec Gemini 300 series. This is a version-specific scope statement, not a complete current SDK device list; query the exact camera/firmware capability before using a field.

#### What is a Filter <a href="#what-is-a-filter" id="what-is-a-filter"></a>

_Reviewed source:_ [_What is a Filter_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/What%20is%20a%20Filter)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1.1 What is a Filter? <a href="#id-1.1-what-is-a-filter" id="id-1.1-what-is-a-filter"></a>

A Filter is a post-processing module provided by OrbbecSDK v2 for processing raw frames from the sensor. Common use cases include:

• Removing noise and holes from depth maps

• Spatial and temporal smoothing of depth maps

• Downsampling images to reduce resolution, data size, and improve downstream processing performance

• Software-based alignment of depth and color streams

• Converting frame pixel formats

• Generating point cloud data

**⚠ Note:Filters are not limited to Depth streams. Some Filters also support Color or IR streams. Always check the applicable stream type for each Filter.**

#### 1.2 Two Ways to Use Filters <a href="#id-1.2-two-ways-to-use-filters" id="id-1.2-two-ways-to-use-filters"></a>

| Method                  | Description                                                                                                                                                               | Use Case                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| Create Filter Directly  | Explicitly specify which Filter to use and configure its parameters                                                                                                       | Fine-grained control, custom scenarios       |
| Recommended Filter List | Obtained from a specific Sensor. The SDK returns a recommended Filter combination based on the Sensor's stream type. Can only process frames of the matching stream type. | Quick integration, general-purpose scenarios |

\*\*✅ Tip:\*\*Not sure which method your device supports, or which one to choose? **Start with the Recommended Filter List to get up and running quickly**. Switch to "Create Filter Directly" when you need custom configuration.

#### 1.3 Complete Filter Quick Reference <a href="#id-1.3-complete-filter-quick-reference" id="id-1.3-complete-filter-quick-reference"></a>

| Filter Name           | Applicable Stream   | Description                                                                                     | Type                 |
| --------------------- | ------------------- | ----------------------------------------------------------------------------------------------- | -------------------- |
| PointCloudFilter      | Depth / Depth+Color | Converts depth frames to XYZ point clouds, or depth+color frames to RGBD point clouds (XYZ+RGB) | Transformation       |
| Align                 | Depth + Color       | Software-based spatial alignment between depth and color streams                                | Transformation       |
| FormatConvertFilter   | Color / IR          | Pixel format conversion (e.g., MJPG→RGB, YUYV→BGR, etc.)                                        | Transformation       |
| DisparityTransform    | Depth               | Bidirectional conversion between depth and disparity maps                                       | Transformation       |
| SequenceIdFilter      | Depth / IR          | Filters frames by sequence ID, used with HDR                                                    | Flow Control         |
| DecimationFilter      | Depth / IR / Color  | Downsamples the image to reduce resolution                                                      | Sampling / Threshold |
| ThresholdFilter       | Depth               | Zeroes out depth values outside the specified range                                             | Sampling / Threshold |
| NoiseRemovalFilter    | Depth               | Removes noise from depth maps (basic)                                                           | Noise Reduction      |
| FalsePositiveFilter   | Depth               | Removes various types of noise from depth maps (advanced)                                       | Noise Reduction      |
| SpatialAdvancedFilter | Depth               | Edge-preserving spatial smoothing, high quality                                                 | Spatial Smoothing    |
| SpatialFastFilter     | Depth               | Fast spatial smoothing, low CPU usage                                                           | Spatial Smoothing    |
| SpatialModerateFilter | Depth               | Balanced spatial smoothing between speed and quality                                            | Spatial Smoothing    |
| HoleFillingFilter     | Depth               | Fills holes in depth maps                                                                       | Spatial Smoothing    |
| TemporalFilter        | Depth               | Temporal smoothing by fusing adjacent frame data                                                | Temporal Smoothing   |

\*\*Note:\*\*NoiseRemovalFilter is called automatically inside the SDK. You can only enable/disable it or adjust its parameters. It cannot be created independently. All other Filters are public types - create them directly with no activation code required.

#### 1.4 Two Frame Processing Modes <a href="#id-1.4-two-frame-processing-modes" id="id-1.4-two-frame-processing-modes"></a>

**Synchronous Processing (recommended, suitable for most scenarios)**

_auto outFrame = filter->process(inFrame);_

_if(outFrame) {_

_// Use the processed frame_

_}_

**Asynchronous Processing (suitable for high frame rate or pipeline scenarios)**

_// Set the callback, triggered automatically when processing completes_

_filter->setCallBack(\[]\(std::shared\_ptr_`ob::Frame` _outFrame) {_

_if(outFrame) {_

_// Use the processed frame_

_}_

_});_

_// Push the frame into the Filter's processing queue_

_filter->pushFrame(inFrame);_

**⚠ Note:**`process()` may return `nullptr` in some cases. Always check the return value before using it.

#### Detailed Filter Reference <a href="#detailed-filter-reference" id="detailed-filter-reference"></a>

_Reviewed source:_ [_Detailed Filter Reference_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Detailed%20Filter%20Reference)_. Manufacturer figures and source examples retain their original attribution and rights._



**1. Transformation**

**1.1 PointCloudFilter**

\*\*Applicable Stream:\*\*Depth (for XYZ point cloud); Depth + Color (for RGBD point cloud, requires Depth and Color to be aligned (D2C) first, otherwise color mapping will be incorrect)

\*\*Function:\*\*Converts depth frames to XYZ point clouds (OB\_FORMAT\_POINT), or aligned depth+color frames to RGBD point clouds (OB\_FORMAT\_RGB\_POINT, each point contains XYZ coordinates and RGB color)

| Parameter   | Type     | Range                                      | Default           | Description                                                                  |
| ----------- | -------- | ------------------------------------------ | ----------------- | ---------------------------------------------------------------------------- |
| pointFormat | OBFormat | OB\_FORMAT\_POINT / OB\_FORMAT\_RGB\_POINT | OB\_FORMAT\_POINT | Point cloud format                                                           |
| decimate    | int      | 1 \~ 8                                     | 1                 | Point cloud decimation factor. Values > 1 downsample the output point cloud. |

**Example 1: XYZ Point Cloud**

_auto pointCloudFilter = std::make\_shared_`ob::PointCloudFilter`_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_POINT);_

_pointCloudFilter->setCoordinateDataScaled(1.0f);_

_// Can pass a standalone Depth frame or a FrameSet containing a Depth frame_

_auto pointCloudFrame = pointCloudFilter->process(depthFrame);_

_if(pointCloudFrame) {_

_auto points = pointCloudFrame->as_`ob::PointsFrame`_();_

_// Use point cloud data ..._

_}_

**Example 2: RGBD Point Cloud**

To generate an RGBD point cloud, the depth and color frames must be spatially aligned before being passed to PointCloudFilter. There are two alignment methods: prefer hardware D2C (better performance); if the resolution does not support hardware D2C, use the software Align Filter.

**Method 1: Hardware D2C Alignment (recommended, use when resolution supports it)**

_auto pointCloudFilter = std::make\_shared_`ob::PointCloudFilter`_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_RGB\_POINT);_

_// Enable hardware D2C in Config. The FrameSet output by Pipeline is already aligned_

_std::shared\_ptr_`ob::Config` _config = std::make\_shared_`ob::Config`_();_

_config->enableVideoStream(OB\_STREAM\_DEPTH);_

_config->enableVideoStream(OB\_STREAM\_COLOR);_

_config->setAlignMode(ALIGN\_D2C\_HW\_MODE);_

_pipe.start(config);_

_auto frameSet = pipe.waitForFrameset(100);_

_auto rgbdPointCloudFrame = pointCloudFilter->process(frameSet);_

_if(rgbdPointCloudFrame) {_

_auto points = rgbdPointCloudFrame->as_`ob::PointsFrame`_();_

_// Each point contains XYZ coordinates and RGB color ..._

_}_

**Method 2: Software Align Filter (use when the resolution does not support hardware D2C)**

_auto pointCloudFilter = std::make\_shared_`ob::PointCloudFilter`_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_RGB\_POINT);_

_auto alignFilter = std::make\_shared_`ob::Align`_(OB\_STREAM\_COLOR);_

_// frameSet comes from Pipeline (must enable both Depth and Color streams)_

_auto frameSet = pipe.waitForFrameset(100);_

_auto alignedFrameSet = alignFilter->process(frameSet); // FrameSet after software alignment_

_auto rgbdPointCloudFrame = pointCloudFilter->process(alignedFrameSet);_

_if(rgbdPointCloudFrame) {_

_auto points = rgbdPointCloudFrame->as_`ob::PointsFrame`_();_

_// Each point contains XYZ coordinates and RGB color ..._

_}_

**1.2 Align**

\*\*Applicable Stream:\*\*Depth + Color. \*\*Function:\*\*Performs software-based spatial alignment between two streams, eliminating parallax offset between depth and color images. Unlike hardware D2C alignment, the Align Filter runs on the CPU, requires no hardware support, and offers more flexibility — but with higher platform resource consumption. If your device supports hardware D2C alignment, prefer it for better performance.

| Parameter | Type         | Description                                                                                                                    |
| --------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| AlignType | OBStreamType | Alignment target stream type: OB\_STREAM\_COLOR (depth aligned to color, D2C), OB\_STREAM\_DEPTH (color aligned to depth, C2D) |

_// Specify the alignment target when creating (depth aligned to color)_

_auto alignFilter = std::make\_shared_`ob::Align`_(OB\_STREAM\_COLOR);_

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

_auto alignedDepth = alignedFrameSet->as_`ob::FrameSet`_()->getFrame(OB\_FRAME\_DEPTH);_

_}_

**1.3 FormatConvertFilter**

\*\*Applicable Stream:\*\*Color (YUYV/MJPG/NV12/NV21 to RGB/BGR, etc.); IR (Y16 to RGB, etc.). \*\*Function:\*\*Converts a frame's pixel format from one type to another. Commonly used to convert the camera's raw output format into a format directly usable by OpenCV.

| Enum Value             | Description    |
| ---------------------- | -------------- |
| FORMAT\_YUYV\_TO\_RGB  | YUYV → RGB     |
| FORMAT\_MJPG\_TO\_RGB  | MJPG → RGB     |
| FORMAT\_MJPG\_TO\_BGR  | MJPG → BGR     |
| FORMAT\_MJPG\_TO\_NV21 | MJPG → NV21    |
| FORMAT\_MJPG\_TO\_NV12 | MJPG → NV12    |
| FORMAT\_NV12\_TO\_RGB  | NV12 → RGB     |
| FORMAT\_NV21\_TO\_RGB  | NV21 → RGB     |
| FORMAT\_RGB\_TO\_BGR   | RGB → BGR      |
| FORMAT\_Y16\_TO\_RGB   | Y16 (IR) → RGB |

_auto formatConvertFilter = std::make\_shared_`ob::FormatConvertFilter`_();_

_formatConvertFilter->setFormatConvertType(FORMAT\_MJPG\_TO\_RGB);_

_auto rgbFrame = formatConvertFilter->process(colorFrame);_

_if(rgbFrame) {_

_// rgbFrame is now in RGB format, directly usable for OpenCV display_

_}_

**1.4 DisparityTransform**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Converts disparity maps to depth maps. The camera outputs depth data by default. This filter is only needed when you have switched to disparity-format data and need to convert it back to depth format.

**⚠ Note:**(1) Depth filters like ThresholdFilter only work on Depth data (in mm). (2) If the input is in Disparity format, it must first be converted via DisparityTransform, otherwise the filtering result will be invalid.

_auto disparityTransform = std::make\_shared_`ob::DisparityTransform`_();_

_auto depthFrame = disparityTransform->process(disparityFrame);_

**2. Flow Control**

**2.1 SequenceIdFilter**

**Applicable Stream:** Depth / IR. \*\*Function:\*\*Filters frames from a FrameSet by the specified sequence ID. Used with HDR. Only takes effect when the HDR Merge Filter is disabled. selectSequenceId(0) passes all frames through; selectSequenceId(1) only keeps frames with sequence ID 1.

| Parameter  | Type | Range   | Default | Description                                               |
| ---------- | ---- | ------- | ------- | --------------------------------------------------------- |
| sequenceid | int  | -1 \~ 1 | 0       | Frame sequence ID to retain. 0 passes all frames through. |

_auto seqFilter = std::make\_shared_`ob::SequenceIdFilter`_();_

_seqFilter->selectSequenceId(1); // Only keep frames with sequence ID 1_

_auto filteredFrame = seqFilter->process(frameSet);_

**3. Sampling / Threshold**

**3.1 DecimationFilter**

\*\*Applicable Stream:\*\*Depth / IR / Color. \*\*Function:\*\*Downsamples the image by a specified factor, reducing resolution and lowering computational load for downstream processing. However, higher sampling rates result in more detail loss.

| Parameter | Type  | Range  | Default | Description                                                                        |
| --------- | ----- | ------ | ------- | ---------------------------------------------------------------------------------- |
| decimate  | uint8 | 1 \~ 8 | 2       | Downsampling factor. For example, 2 reduces the resolution to 1/2 of the original. |

auto decimationFilter = std::make\_shared`ob::DecimationFilter`();

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

| Parameter | Type   | Range      | Default | Description                    |
| --------- | ------ | ---------- | ------- | ------------------------------ |
| min       | uint32 | 0 \~ 16000 | 0       | Minimum valid depth value (mm) |
| max       | uint32 | 0 \~ 16000 | 16000   | Maximum valid depth value (mm) |

_auto thresholdFilter = std::make\_shared_`ob::ThresholdFilter`_();_

_// Query the supported range_

_auto minRange = thresholdFilter->getMinRange();_

_auto maxRange = thresholdFilter->getMaxRange();_

_// Only keep depth values in the 300mm\~3000mm range_

_thresholdFilter->setValueRange(300, 3000);_

_auto outFrame = thresholdFilter->process(depthFrame);_

**4. Noise Reduction**

**4.1 NoiseRemovalFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Applies clustering to the depth map to identify and filter out noisy regions. As a basic noise reduction filter that runs inside the SDK, it is enabled by default on most devices and does not need to be created manually. Use the "Recommended Filter List" to toggle its state and adjust parameters.

| Parameter | Type   | Range      | Default | Description                                                                                                                                           |
| --------- | ------ | ---------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| min\_diff | uint16 | 1 \~ 51200 | 256     | Depth spatial filtering range. Larger values weaken the denoising effect (retaining more detail); smaller values strengthen denoising.                |
| max\_size | uint16 | 1 \~ 1000  | 80      | Maximum pixel area of noise clusters. Larger values make denoising more aggressive (filtering larger noise clusters), but may reduce depth fill rate. |

Depth effect before and after enabling NoiseRemovalFilter:

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/cc1image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/cc1image.png)[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/oL5image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/oL5image.png)

**4.2 FalsePositiveFilter**

\*\*Applicable Stream:\*\*Depth. **Function:** Filters out erroneous depth values (ghost noise) from the depth map. This filter functionally supersedes NoiseRemovalFilter and consumes more platform resources. It is recommended to disable NoiseRemovalFilter when enabling FalsePositiveFilter.

Because this filter has too many parameters to pass individually when creating it directly, it only supports enable/disable via filter->enable(bool). No additional parameter configuration is needed. **It is strongly recommended to use the "Recommended Filter List" approach.**

_auto fpFilter = std::make\_shared_`ob::FalsePositiveFilter`_();_

_// Enable the filter_

_fpFilter->enable(true);_

_auto outFrame = fpFilter->process(depthFrame);_

This filter consists of three sub-filters, each targeting noise in a specific scenario. Since the filtering process may misclassify and remove valid depth data, each sub-filter exposes ROI parameters to precisely control the filter's region of influence, avoiding damage to valid depth. Adjust the ROI range as needed.

**4.3 FalsePositiveFilter::EdgeBleedFilter**

\*\*Function:\*\*Filters out laterally extended erroneous depth at object edges. \*\*Typical scenarios:\*\*semi-outdoor window edges, overexposed outdoor sky, etc. \*\*Rule:\*\*Within the depth map ROI, when more than fpebfMinBleedLength consecutive pixels have identical depth values in the horizontal direction, the region is classified as edge bleed noise and filtered out. For example, setting fpebfMinBleedLength = 40 triggers filtering when more than 40 consecutive pixels have the same depth value.

| Parameter               | Type  | Range      | Default | Description                                                                                                                                     |
| ----------------------- | ----- | ---------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| fpEdgeBleedFilterEnable | bool  | 0 \~ 1     | 0       | Edge bleed filter toggle                                                                                                                        |
| fpebfROIMinXRatio       | float | 0.0 \~ 1.0 | 0.0     | ROI left boundary (proportion of image width, 0.0 = left edge )                                                                                 |
| fpebfROIMaxXRatio       | float | 0.0 \~ 1.0 | 1.0     | ROI right boundary (proportion of image width, 1.0 = right edge )                                                                               |
| fpebfROIMinYRatio       | float | 0.0 \~ 1.0 | 0.0     | ROI top boundary (proportion of image height, 0.0 = top edge )                                                                                  |
| fpebfROIMaxYRatio       | float | 0.0 \~ 1.0 | 0.6     | ROI bottom boundary (proportion of image height, 1.0 = bottom edge )                                                                            |
| fpebfMinBleedLength     | int   | 1 \~ 256   | 40      | Minimum consecutive bleed length (pixels). Filtering is triggered when the number of consecutive identical-depth pixels exceeds this threshold. |

Depth effect before and after enabling EdgeBleedFilter (laterally extended noise has been filtered):

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/ZT6image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/ZT6image.png)

At close range, depth values are more similar. When capturing flat surfaces, false positives may cause lateral depth loss.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/9v4image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/9v4image.png)

**\*\*4.4 FalsePositiveFilter::\*\*TextureSparsityFilter**

\*\*Function:\*\*Filters out erroneous depth in low-texture scenes. \*\*Typical scenarios:\*\*outdoor white walls, non-overexposed sky, etc. \*\*Rule:\*\*Within the depth map ROI, noise regions that satisfy both of the following conditions will be filtered out:

\[if !supportLists]l \[endif]Average depth value of noise region < fptsfMaxNoiseLevel

\[if !supportLists]l \[endif]Pixel area of noise cluster < fptsfMaxSpeckleSize

| Parameter                     | Type  | Range      | Default | Description                                                                                |
| ----------------------------- | ----- | ---------- | ------- | ------------------------------------------------------------------------------------------ |
| fpTextureSparsityFilterEnable | bool  | 0 \~ 1     | 0       | Low-texture filter toggle                                                                  |
| fptsfROIMinXRatio             | float | 0.0 \~ 1.0 | 0.0     | ROI left boundary (proportion of image width, 0.0 = left edge )                            |
| fptsfROIMaxXRatio             | float | 0.0 \~ 1.0 | 1.0     | ROI right boundary (proportion of image width, 1.0 = right edge )                          |
| fptsfROIMinYRatio             | float | 0.0 \~ 1.0 | 0.0     | ROI top boundary (proportion of image height, 0.0 = top edge )                             |
| fptsfROIMaxYRatio             | float | 0.0 \~ 1.0 | 0.45    | ROI bottom boundary (proportion of image height, 1.0 = bottom edge )                       |
| fptsfMaxNoiseLevel            | int   | 1 \~ 65535 | 6000    | Maximum noise depth value (mm). Only removes noise with depth values below this threshold. |
| fptsfMaxSpeckleSize           | int   | 1 \~ 65535 | 1300    | Maximum pixel area of noise clusters. Only removes clusters smaller than this value.       |

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

| Parameter                      | Type  | Range      | Default | Description                                                                                |
| ------------------------------ | ----- | ---------- | ------- | ------------------------------------------------------------------------------------------ |
| fpPatternAmbiguityFilterEnable | bool  | 0 \~ 1     | 0       | Repetitive texture filter toggle                                                           |
| fppafROIMinXRatio              | float | 0.0 \~ 1.0 | 0.0     | ROI left boundary (proportion of image width, 0.0 = left edge )                            |
| fppafROIMaxXRatio              | float | 0.0 \~ 1.0 | 0.99    | ROI right boundary (proportion of image width, 1.0 = right edge )                          |
| fppafROIMinYRatio              | float | 0.0 \~ 1.0 | 0.0     | ROI top boundary (proportion of image height, 0.0 = top edge )                             |
| fppafROIMaxYRatio              | float | 0.0 \~ 1.0 | 0.9     | ROI bottom boundary (proportion of image height, 1.0 = bottom edge )                       |
| fppafMaxNoiseLevel             | int   | 1 \~ 65535 | 6000    | Maximum noise depth value (mm). Only removes noise with depth values below this threshold. |
| fppafMaxSpeckleSize            | int   | 1 \~ 65535 | 4000    | Maximum pixel area of noise clusters. Only removes clusters smaller than this value.       |
| fppafMaxWidthRatio             | float | 0.0 \~ 1.0 | 0.3     | Maximum noise cluster width as a proportion of image width                                 |
| fppafMaxHeightRatio            | float | 0.0 \~ 1.0 | 0.3     | Maximum noise cluster height as a proportion of image height                               |
| fppafTolerance                 | float | 0.0 \~ 1.0 | 0.15    | Noise tolerance feature threshold. Only removes noise when Tolerance > this value.         |
| fppafScore                     | int   | 1 \~ 65535 | 50      | Noise score threshold. Only removes noise when Score > this value.                         |

Depth effect before and after enabling PatternAmbiguityFilter (noise on building facades from repetitive textures has been filtered)

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/WC9image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/WC9image.png)

**4.6 FalsePositiveFilter Tuning Guide:**

| Parameter           | Sub-Filter             | Adjustment Direction for Noise Suppression |
| ------------------- | ---------------------- | ------------------------------------------ |
| fpebfMinBleedLength | EdgeBleedFilter        | ↓ Decrease for more aggressive filtering   |
| fptsfMaxNoiseLevel  | TextureSparsityFilter  | ↑ Increase to cover farther noise          |
| fptsfMaxSpeckleSize | TextureSparsityFilter  | ↑ Increase to filter larger noise clusters |
| fppafMaxNoiseLevel  | PatternAmbiguityFilter | ↑ Increase to cover farther noise          |
| fppafMaxSpeckleSize | PatternAmbiguityFilter | ↑ Increase to filter larger noise clusters |
| fppafMaxWidthRatio  | PatternAmbiguityFilter | ↑ Increase to filter wider noise clusters  |
| fppafMaxHeightRatio | PatternAmbiguityFilter | ↑ Increase to filter taller noise clusters |
| fppafTolerance      | PatternAmbiguityFilter | ↓ Decrease for more aggressive filtering   |
| fppafScore          | PatternAmbiguityFilter | ↓ Decrease for more aggressive filtering   |

**5. Spatial Smoothing**

**5.1 SpatialAdvancedFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Edge-preserving spatial smoothing. Controls smoothing strength and edge preservation through alpha and disp\_diff parameters. Smooths depth values in flat areas while preserving object edges. This is the recommended choice for depth map spatial smoothing, but also has the highest resource usage.

| Parameter  | Type   | Range      | Default | Description                                                                                          |
| ---------- | ------ | ---------- | ------- | ---------------------------------------------------------------------------------------------------- |
| alpha      | float  | 0.1 \~ 1   | 0.5     | Current pixel weight. Larger values reduce smoothing (preserving original values). Step size: 0.01.  |
| disp\_diff | uint16 | 1 \~ 10000 | 160     | Depth gradient threshold. Pixels exceeding this value are excluded from smoothing (edge protection). |
| radius     | uint16 | 0 \~ 8     | 1       | Smoothing radius. Affects the smoothing range.                                                       |
| magnitude  | int    | 1 \~ 5     | 1       | Number of iterations. More iterations produce stronger smoothing.                                    |

_auto spatialFilter = std::make\_shared_`ob::SpatialAdvancedFilter`_();_

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

| Parameter | Type  | Range  | Default | Description                                                                                             |
| --------- | ----- | ------ | ------- | ------------------------------------------------------------------------------------------------------- |
| radius    | uint8 | 3 \~ 5 | 3       | Smoothing radius. Larger values increase the smoothing range. Step size: 2, so valid values are 3 or 5. |

_auto spatialFastFilter = std::make\_shared_`ob::SpatialFastFilter`_();_

_// Get current parameters (including defaults)_

_auto params = spatialFastFilter->getFilterParams();_

_// Modify parameters as needed_

_params.radius = 2;_

_spatialFastFilter->setFilterParams(params);_

_auto outFrame = spatialFastFilter->process(depthFrame);_

**5.3 SpatialModerateFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Based on an optimized mean smoothing algorithm, balancing processing speed and smoothing quality.

| Parameter  | Type   | Range      | Default | Description                                                                                          |
| ---------- | ------ | ---------- | ------- | ---------------------------------------------------------------------------------------------------- |
| magnitude  | uint8  | 1 \~ 3     | 1       | Number of iterations. More iterations produce stronger smoothing.                                    |
| radius     | uint8  | 3 \~ 7     | 5       | Smoothing radius. Step size: 2, so valid values are 3, 5, or 7.                                      |
| disp\_diff | uint16 | 1 \~ 10000 | 160     | Depth gradient threshold. Pixels exceeding this value are excluded from smoothing (edge protection). |

_auto spatialModFilter = std::make\_shared_`ob::SpatialModerateFilter`_();_

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

| Parameter               | Type                    | Type                                                               | Range                                                              | Default                                                            | Description                                                        |
| ----------------------- | ----------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| hole\_filling\_mode     | OBHoleFillingMode       | OBHoleFillingMode                                                  | 0 \~ 2                                                             | 0 (TOP)                                                            | Fill mode (see table below)                                        |
| Enum Value              | Enum Value              | Description                                                        | Description                                                        | Description                                                        | Description                                                        |
| OB\_HOLE\_FILL\_TOP     | OB\_HOLE\_FILL\_TOP     | Fill with the nearest valid depth value directly above the hole    | Fill with the nearest valid depth value directly above the hole    | Fill with the nearest valid depth value directly above the hole    | Fill with the nearest valid depth value directly above the hole    |
| OB\_HOLE\_FILL\_NEAREST | OB\_HOLE\_FILL\_NEAREST | Fill with the nearest valid depth value from the surrounding area  | Fill with the nearest valid depth value from the surrounding area  | Fill with the nearest valid depth value from the surrounding area  | Fill with the nearest valid depth value from the surrounding area  |
| OB\_HOLE\_FILL\_FAREST  | OB\_HOLE\_FILL\_FAREST  | Fill with the farthest valid depth value from the surrounding area | Fill with the farthest valid depth value from the surrounding area | Fill with the farthest valid depth value from the surrounding area | Fill with the farthest valid depth value from the surrounding area |

_auto holeFillingFilter = std::make\_shared_`ob::HoleFillingFilter`_();_

_holeFillingFilter->setFilterMode(OB\_HOLE\_FILL\_TOP);_

_auto outFrame = holeFillingFilter->process(depthFrame);_

This filter fills all holes, which may introduce false data and is generally not recommended. However, in special scenarios where complete depth is required, you can enable it with the recommended OB\_HOLE\_FILL\_FAREST mode.

Depth effect before and after enabling HoleFillingFilter (zero-depth regions have been filled):

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/GWhimage.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/GWhimage.png)[![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-08/scaled-1680-/jvHimage.png)](https://doc.orbbec.com/uploads/images/gallery/2026-08/jvHimage.png)

**6. Temporal Smoothing**

**6.1 TemporalFilter**

\*\*Applicable Stream:\*\*Depth. \*\*Function:\*\*Fuses depth data from the current frame with historical frames for temporal smoothing, effectively suppressing inter-frame jitter noise.

| Parameter   | Type  | Range    | Default | Description                                                                                                                                                |
| ----------- | ----- | -------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| diff\_scale | float | 0.1 \~ 1 | 0.1     | Allowed depth change ratio threshold. Pixels exceeding this ratio are excluded from fusion. Step size: 0.01.                                               |
| weight      | float | 0.1 \~ 1 | 0.4     | Fusion weight for the current frame. Larger values favor the original data (weaker smoothing), smaller values produce stronger smoothing. Step size: 0.01. |

_auto temporalFilter = std::make\_shared_`ob::TemporalFilter`_();_

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

#### Creating Filters Directly <a href="#creating-filters-directly" id="creating-filters-directly"></a>

_Reviewed source:_ [_Creating Filters Directly_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Creating%20Filters%20Directly)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

**1. Quick Start**

Using ThresholdFilter as an example, complete post-processing in 3 steps:

_#include \<libobsensor/ObSensor.hpp>_

_// Step 1: Create the Filter_

_auto thresholdFilter = std::make\_shared_`ob::ThresholdFilter`_();_

_// Step 2: Set parameters (keep depth values between 300mm and 3000mm)_

_thresholdFilter->setValueRange(300, 3000);_

_// Step 3: Process the frame (depthFrame comes from a FrameSet obtained via Pipeline)_

_auto outFrame = thresholdFilter->process(depthFrame);_

_if(outFrame) {_

_auto processedDepth = outFrame->as_`ob::DepthFrame`_();_

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

_auto thresholdFilter = std::make\_shared_`ob::ThresholdFilter`_();_

_thresholdFilter->setValueRange(300, 3000);_

_thresholdFilter->enable(true);_

_auto edgeFilter = std::make\_shared_`ob::EdgeNoiseRemovalFilter`_();_

_edgeFilter->enable(true);_

_auto spatialFilter = std::make\_shared_`ob::SpatialAdvancedFilter`_();_

_spatialFilter->enable(true);_

_auto alignFilter = std::make\_shared_`ob::Align`_(OB\_STREAM\_COLOR);_

_alignFilter->enable(true);_

_auto pointCloudFilter = std::make\_shared_`ob::PointCloudFilter`_();_

_pointCloudFilter->setCreatePointFormat(OB\_FORMAT\_RGB\_POINT);_

_pointCloudFilter->enable(true);_

_// Frame processing should be done in a separate thread. Do not call it directly in the frame acquisition or callback thread._

_if(!frameSet) return;_

_auto depthFrame = frameSet->getFrame(OB\_FRAME\_DEPTH);_

_auto colorFrame = frameSet->getFrame(OB\_FRAME\_COLOR);_

_if(!depthFrame || !colorFrame) return;_

_std::shared\_ptr_`ob::Frame` _outFrame = frameSet;_

_for(auto \&filter : std::vector\<std::shared\_ptr_`ob::Filter`_>{_

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

#### Recommended Filter List <a href="#recommended-filter-list" id="recommended-filter-list"></a>

_Reviewed source:_ [_Recommended Filter List_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Recommended%20Filter%20List)_. Manufacturer figures and source examples retain their original attribution and rights._

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

_std::shared\_ptr_`ob::Config` _config = std::make\_shared_`ob::Config`_();_

_config->enableVideoStream(OB\_STREAM\_DEPTH);_

_pipe.start(config);_

_while(true) {_

_auto frameSet = pipe.waitForFrameset(100);_

_if(!frameSet) continue;_

_auto depthFrame = frameSet->getFrame(OB\_FRAME\_DEPTH);_

_if(!depthFrame) continue;_

_// Step 6: Apply enabled Filters in sequence_

_std::shared\_ptr_`ob::Frame` _outFrame = depthFrame;_

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

| Field | Description                               |
| ----- | ----------------------------------------- |
| name  | Parameter name                            |
| type  | Parameter type ("int" / "float" / "bool") |
| min   | Minimum value                             |
| max   | Maximum value                             |
| step  | Step size                                 |
| def   | Default                                   |
| desc  | Description                               |

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

_if(filter->is_`ob::TemporalFilter`_()) {_

_auto temporalFilter = filter->as_`ob::TemporalFilter`_();_

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

| Unlabelled source column | Create Filter Directly                                            | Recommended Filter List                                                |
| ------------------------ | ----------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Ease of Use              | Requires understanding of each Filter's purpose and parameters    | No detail knowledge needed, works out of the box                       |
| Parameter Configuration  | Manual setup, fully controllable                                  | Device-optimal defaults, fine-tune as needed                           |
| Device Compatibility     | Must verify whether the current device supports the target Filter | SDK automatically returns only Filters supported by the current device |
| Filter Selection         | Fully independent selection                                       | Determined by SDK based on device model                                |
| Default Parameters       | Must set appropriate values manually                              | Already the optimal configuration for the current device               |
| Typical Scenarios        | Product customization, algorithm tuning                           | Quick integration, general-purpose demos                               |

**Recommendations**

• If you are a first-time user or just want to see results quickly, use the Recommended Filter List. It takes only a few lines of code to get started.

• If you need to select a specific Filter combination or have precise parameter requirements, use Create Filter Directly.

• The two approaches can be combined: first use the recommended list to learn which Filters your device supports, then create them directly for fine-grained parameter tuning.

#### Optional Depth Preset Update (Gemini 330 Series) <a href="#optional-depth-preset-update-gemini-330-series" id="optional-depth-preset-update-gemini-330-series"></a>

_Reviewed source:_ [_Optional Depth Preset Update (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Optional%20Depth%20Preset%20Update%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

#### 1. Purpose <a href="#id-1.-purpose" id="id-1.-purpose"></a>

The Gemini 330 has been updated to support depth preset updates. Since the camera has limited storage for built-in Presets, we provide three optional depth preset updates. Users can download the appropriate Preset from the [Depth Preset Release](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Preset%20Release%20\(Gemini%20330%20Series\)) page provided by Orbbec based on their specific application scenarios and update it to the camera for better depth performance in corresponding scenarios.

#### 2. Scope <a href="#id-2.-scope" id="id-2.-scope"></a>

Applies to all Gemini 330 products with firmware version 1.4.60 or later, and requires SDK version 2.3.x or later.

#### 3. How to Update Presets <a href="#id-3.-how-to-update-presets" id="id-3.-how-to-update-presets"></a>

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

#### Update Firmware (Gemini 330 Series) <a href="#update-firmware-gemini-330-series" id="update-firmware-gemini-330-series"></a>

_Reviewed source:_ [_Update Firmware (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Update%20Firmware%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

#### 1. Device Firmware Mode Introduction <a href="#id-1.-device-firmware-mode-introduction" id="id-1.-device-firmware-mode-introduction"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

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

#### 2. Update Firmware <a href="#id-2.-update-firmware" id="id-2.-update-firmware"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

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

If an update fails, preserve the error and first resolve power, connection and exact-image compatibility. Retry only through the model’s documented recovery workflow; do not repeatedly flash to diagnose an unidentified fault.

**2.2 Offline Update via Orbbec Viewer**

The difference between offline and online updates is as follows: With online updates, the firmware is automatically downloaded from the server (downloaded to the "output/firmwareFile" directory in Orbbec Viewer), and then the device is updated. However, with offline updates, you manually select the firmware path and then proceed with the update. The interface is as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110308/image031.gif)

After clicking "Upgrade," the subsequent update steps are the same as the online update.

**2.3 Code Sample**

1. The firmware update reference for Orbbec SDK V1.x.x version is available in the sample at the following link:

[https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade](https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade)

2. The firmware update reference for Orbbec SDK V2.x.x version is available in the sample at the following link:

[https://github.com/orbbec/OrbbecSDK\_v2/tree/main/examples/2.device.firmware\_update](https://github.com/orbbec/OrbbecSDK_v2/tree/main/examples/2.device.firmware_update)

#### 3. Handle Update Exception <a href="#id-3.-handle-update-exception" id="id-3.-handle-update-exception"></a>

If there is a power failure or the USB cable is unplugged during the online update process, the device may enter Recovery mode. In this case, you will need to perform an offline update using the firmware downloaded online. The path to the online firmware download is in the "output/firmwareFile" directory of Orbbec Viewer, for example, on the Windows platform, as shown in the following figure.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110315/image033.gif)

If the device enters Recovery mode but there is no firmware available, please download the firmware from the product’s firmware download page first. Then, follow the offline update method to perform the update.

**Notes: (Very Important)**

In Recovery mode, ISP firmware update is not supported. You need to enter Normal mode and perform the firmware update again to ensure ISP firmware matches the current system. (In Recovery mode, firmware needs to be updated twice.)

#### 4. Update Orbbec Viewer <a href="#id-4.-update-orbbec-viewer" id="id-4.-update-orbbec-viewer"></a>

If there is a new version of Orbbec Viewer available for update, when opening Orbbec Viewer, there will be a prompt in the top right corner: "A new version of the tool can be updated." Click on this prompt, and it will link to the download directory of Orbbec Viewer on GitHub. Please download the corresponding platform’s Orbbec Viewer.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/31110320/image035.gif)

**Notes:**

Each firmware has a corresponding minimum version number of supported Orbbec Viewer. If the current Orbbec Viewer version is too low, you need to update Orbbec Viewer first to detect the prompt for the latest firmware update.

#### Gemini 330 Series Supported Hosts and System Requirements (USB) <a href="#gemini-330-series-supported-hosts-and-system-requirements-usb" id="gemini-330-series-supported-hosts-and-system-requirements-usb"></a>

_Reviewed source:_ [_Gemini 330 Series Supported Hosts and System Requirements (USB)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Supported%20Hosts%20and%20System%20Requirements%20\(USB\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

#### 1. Recommended Host Platforms <a href="#id-1.-recommended-host-platforms" id="id-1.-recommended-host-platforms"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

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

#### 2. System Requirements <a href="#id-2.-system-requirements" id="id-2.-system-requirements"></a>

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

| Operating system | Requirement                                                                                  | Description                                                                                                               |
| ---------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Windows 10/11    | – Windows 10 April 2018 (version 1803, operating system build 17134) release (x64) or higher | The generation of the VS project depends on the installed VS version and cmake version, and supports VS2015/VS2017/VS2019 |
| Linux Ubuntu     | 18.04/20.04/22.04                                                                            | Support GCC 7.5                                                                                                           |
| Ubuntu Arm       | 18.04/20.04/22.04                                                                            | Support GCC 7.5                                                                                                           |

#### 3. Tested PC Host Platforms <a href="#id-3.-tested-pc-host-platforms" id="id-3.-tested-pc-host-platforms"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

| Platform  | System / Win10 | System / Win11 | System / Ubuntu 18.04 | System / Ubuntu 20.04 | System / Ubuntu 22.04 |
| --------- | -------------- | -------------- | --------------------- | --------------------- | --------------------- |
| Intel NUC | PASS           | PASS           | Not tested            | PASS                  | Not tested            |
| x64 PC    | PASS           | PASS           | PASS                  | PASS                  | PASS                  |

#### 4. Tested ARM Host Platforms <a href="#id-4.-tested-arm-host-platforms" id="id-4.-tested-arm-host-platforms"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

| ARM Platform             | Software Version                                                                                                               | Test Result |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------ | ----------- |
| NVIDIA Jetson Orin Nano  | Last Tested on JetPack5.1.1-b56                                                                                                | PASS        |
| NVIDIA Jetson Orin NX    | Last Tested on JetPack5.1.1-b56                                                                                                | PASS        |
| NVIDIA Jetson AGX Orin   | Last Tested on JetPack 6.0                                                                                                     | PASS        |
| NVIDIA Jetson Nano       | Last Tested on JetPack 4.6.1-b110                                                                                              | PASS        |
| NVIDIA Jetson AGX Xavier | Last Tested on JetPack 5.0.2-b231                                                                                              | PASS        |
| NVIDIA Jetson Xavier NX  | Last Tested on JetPack 4.6.1-b110                                                                                              | PASS        |
| Qualcomm RB5             | Last Tested on Qualcomm\_Linux.SPF. 5.4.219                                                                                    | PASS        |
| Raspberry Pi 4B          | Last Tested on Ubuntu 20.04                                                                                                    | PASS        |
| Raspberry Pi 5           | Last Tested on [Debian](https://www.raspberrypi.com/news/bookworm-the-new-version-of-raspberry-pi-os/) GNU/Linux 12 (bookworm) | PASS        |

#### Reference Design - Mounting (Gemini 330 Series) <a href="#reference-design-mounting-gemini-330-series" id="reference-design-mounting-gemini-330-series"></a>

_Reviewed source:_ [_Reference Design - Mounting (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Mounting%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Overview <a href="#id-1.-overview" id="id-1.-overview"></a>

This document provides the optimal reference mounting design solution for the camera, assisting customers in swiftly implementing it during the product deployment process.

#### 2. Mounting Reference Solution for Gemini 335/336 <a href="#id-2.-mounting-reference-solution-for-gemini-335-336" id="id-2.-mounting-reference-solution-for-gemini-335-336"></a>

**2.1 Product Components**

| Gemini 335                                                                                      | Gemini 336                                                                                      |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115611/202411031.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115615/202411032.png) |

**2.2 Product Drawing for Gemini 335**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115807/202411033.png)

**2.3 Product Drawing for Gemini 336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115813/202411034.png)

**2.4 Product Interfaces for Gemini 335/336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115820/202411035.png)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the left of the camera, the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port On the right side of the camera, rotate the Sync Port cover to see the Sync Port.

**2.5 Mounting and Fixing Method for Gemini 335/336:**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 5mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120111/202411036.png)

Option B\*\*:\*\*Fix the 3D camera using two M3 thread holes on the rear side, the hole depth is 3.0mm and commended is 0.4Nm

Option C: Fix the 3D Camera using the shape or edges of the metal housing

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120116/202411037.png)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, the FOV viewing angle cannot be blocked;

#### 3. Mounting Reference Solution for Gemini 335L/336L <a href="#id-3.-mounting-reference-solution-for-gemini-335l-336l" id="id-3.-mounting-reference-solution-for-gemini-335l-336l"></a>

**3.1 Product Components**

| Gemini 335L                                                                                     | Gemini 336L                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120428/202411038.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120432/202411039.png) |

**3.2 Product Drawing for Gemini 335L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120438/2024110310.png)

**3.3 Product Drawing for Gemini 336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120443/2024110311.png)

**3.4 Procuct Interface for Gemini 335L/336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120450/2024110312.png)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the bottom of the camera, the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. a length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. a length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port at the top side of the camera, remove the Sync Port protective cover to see the Sync Port.

**3.5 Mounting and Fixing Method for Gemini 335L/336L**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 8mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120454/2024110313.png)

Option B\*\*:\*\*Fix the 3D camera using two M4 thread holes on the rear side, the hole depth is 3.0mm and commended is 0.4Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120500/2024110314.png)

Option C: Fix the 3D Camera using the shape or edges of the metal housing

Illustration for 3D camera mounting

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120505/2024110315.png)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, it cannot block the FOV perspective;

#### 4. System Design Requirements <a href="#id-4.-system-design-requirements" id="id-4.-system-design-requirements"></a>

1. Sealing Requirements

* Use foam padding or silicone seals between the 3D camera and the customer’s device to prevent dust.

2. Lens Requirements

* No additional lenses or covers can be added to the front of the 3D camera.

3. Cooling Requirements

* Connect the 3D camera to external metal components using thermal conductive materials to expand the cooling area. It is recommended to incorporate active cooling with fans.
* The 3D cameras must not be heated by other heat sources.

4. Before customer tooling, please provide structural drawings related to the 3D camera for orbbec’s ME review.

-The next step

#### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

_Reviewed source:_ [_Troubleshooting_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Troubleshooting)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Camera Not Working or Detected <a href="#id-1.-camera-not-working-or-detected" id="id-1.-camera-not-working-or-detected"></a>

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

Lastly, run Orbbec Viewer with the command "sudo ./Orbbec Viewer".

**Q6: How to get the log of hardware level?**

Here are three ways to get the log.

1. Turn on the "heartbeat" switch in Orbbec Viewer;
2. By API, device->setBoolProperty(OB\_PROP\_HEARTBEAT\_BOOL, true);
3. By configuration file, config the "DefaultHeartBeat" as 1. The file is located at ./SDK/Config

**Q7: When the camera is connected to the USB2.0 port, the camera identification may take a long time.**

We recommend using the USB3.0 port and the corresponding USB cable;

If you use the USB2.0 port or USB2.0 cable, camera identification takes about 20 seconds.

#### 2. Function <a href="#id-2.-function" id="id-2.-function"></a>

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

#### Development Resources <a href="#development-resources" id="development-resources"></a>

* [Official Gemini 330 Series documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)
* [Gemini 330 Series USB datasheet](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\))
* [Gemini 335 CAD files](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))
* [Gemini 330 Series firmware releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))
* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
