---
description: >-
  Connect the Gemini 435Le over Gigabit Ethernet, select supported depth
  profiles, inspect power and trigger limits, and measure a depth patch with SDK
  v2.10.6.
---

# Orbbec Gemini 435Le: PoE depth streaming and network setup

{% hint style="info" %}
[**Orbbec Gemini 435Le Industrial Ethernet Stereo Vision Camera on OpenELAB**](https://openelab.io/products/orbbec-gemini-435le-industrial-stereo-camera)

**Model:** Gemini 435Le · **SKU:** `ORBBEC-Gemini435Le` · **Option:** industrial Gigabit Ethernet camera, not Gemini 335Le or a USB camera.
{% endhint %}

Gemini 435Le is a 95 mm-baseline stereo depth camera with Gigabit Ethernet, PoE and global-shutter depth/color sensors. This guide takes one camera from a powered network connection to a depth image and an original numerical depth check. External synchronization is treated separately because the first datasheet contains contradictory trigger-interface details.

## Product overview

### Orbbec Gemini 435Le Industrial Ethernet Stereo Vision Camera <a href="#orbbec-gemini-435le-industrial-ethernet-stereo-vision-camera" id="orbbec-gemini-435le-industrial-ethernet-stereo-vision-camera"></a>

The camera computes depth onboard and exposes depth, two infrared views, color and an inertial measurement unit (IMU) through Orbbec SDK. The M12 X-coded connector carries Ethernet/PoE; the other connector carries external power and auxiliary signals. It is a powered camera endpoint: an ordinary laptop Ethernet port supplies data only. The 435Le's 1280 × 800 depth profile is limited to **10 fps**, unlike the 330-series Ethernet camera. [Datasheet V1.0, §§2–4](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)

For a smaller Ethernet model compare the [Gemini 330 family](orbbec-gemini-330-series-user-manual.md); for direct USB use see [Gemini 335](orbbec-gemini-335-user-manual.md). SDK support for one model does not establish identical connector wiring or stream profiles for another.

## Applications

* Robot perception over a wired network where onboard stereo processing reduces host depth-computation work.
* Measuring stable surfaces over a larger baseline, with a calibration and error budget appropriate to the chosen distance.
* Outdoor perception trials using natural texture as well as projected infrared texture. Sunlight, reflectivity and occlusion still affect valid depth.
* Combining depth and global-shutter color for moving scenes, after verifying timestamps and spatial alignment.

For collision avoidance, treat invalid or missing depth as unknown space. IP67 does not establish a safety-rated protective sensor, or reliable depth from glass, water, polished metal or every dark target.

## Specifications

These selection values are from [Gemini 435Le Datasheet V1.0, 9 May 2025, pp.11–12, 24 and 43](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf). Maximum range and spatial precision have different test conditions.

| Parameter                              | Gemini 435Le                                                                                                                            |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Stereo baseline / projector wavelength | 95 mm / 850 nm                                                                                                                          |
| Advertised working / ideal range       | 0.31–20 m+ / 0.31–10 m; long-range claim requires target reflectivity >10%; actual range depends on scene                               |
| Spatial precision                      | ≤0.4% at 2 m, 1280 × 800, central 90% × 90% region; ≤0.8% at 4 m, central 80% × 80% region                                              |
| Depth FOV                              | 90° horizontal × 65° vertical, ±3°, at 2 m and 1280 × 800                                                                               |
| Depth profiles                         | 1280 × 800: 5/10 fps; 640 × 400: 5/10/15/20 fps; Y16 or RVL                                                                             |
| Color                                  | Global shutter; 1280 × 800 and lower profiles, I420/MJPEG; actual multi-stream combinations depend on link bandwidth                    |
| IMU                                    | 6 DoF; 50/100/200/500/1000 Hz gyro and accelerometer                                                                                    |
| Data / enclosure                       | Gigabit Ethernet, TCP/IP and RTSP / IP67 with correctly fitted connectors and caps                                                      |
| Power                                  | IEEE 802.3af PoE, or 9–24 V DC supply rated ≥2 A at the camera                                                                          |
| Average / peak power limits            | DC <6.5 W / <11 W; PoE <8 W / <15 W, specification summary; individual hot-condition laboratory averages can exceed the summary average |
| Environment                            | −10 to +50 °C ambient, 5–90% RH, noncondensing; powered rear case ≤65 °C                                                                |
| Size / mass                            | 138.5 × 40.5 × 70.0 mm / 520 g                                                                                                          |
| Mounting                               | M4 holes on back, top and bottom; maximum insertion 6 mm, torque 0.4 N·m                                                                |

The advertised 0.31 m near limit is not universal: minimum-Z depends on resolution, preset and offset. Start at about 1 m with the default perception configuration; do not design a wrist mount around the closest number from another profile. HDR is marked for a later upgrade in this datasheet, so confirm actual firmware capability before relying on it. [Minimum-Z and feature scope, §§4.7 and 2](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)

## Hardware and connections

![Official Orbbec 435Le M12 X-coded to RJ45 data cable](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/yqrimage.png)

Official Orbbec illustration from the 435Le quickstart; use the camera cable with a compliant PoE source or separate supported DC supply.

### Choose one supported power path

For the first connection use an IEEE 802.3af-compatible Gigabit PoE injector/switch, the supplied M12 X-coded-to-RJ45 cable, and Cat5e-or-better host cable. Connect the injector's powered output to the camera cable and its data input to the host. A Gigabit USB Ethernet adapter can serve a host without Ethernet. Keep connector keys aligned and fit the appropriate seal/cap before environmental use. [Official quickstart](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Quick%20Start%20Guide%20for%20Gemini%20435Le)

For external DC, disconnect power before wiring the supplied harness: **red is 9–24 V input; black is power ground**. Use ≥2 A supply capacity, following datasheet pp.11/43; the quickstart's ≥1 A figure is lower and is not the commissioning value used here. Power capacity is not the camera's continuous current draw. Keep the Ethernet cable connected for data. Leave unused signal conductors separately insulated.

| Supplied auxiliary harness pin / color | Function in datasheet cable drawing |
| -------------------------------------- | ----------------------------------- |
| 1 / red                                | POWER IN, 9–24 V                    |
| 2 / orange                             | VSYNC VCC                           |
| 3 / green                              | VSYNC IN                            |
| 4 / blue                               | VSYNC OUT                           |
| 5 / brown                              | Signal ground                       |
| 6 / purple                             | RS485B                              |
| 7 / yellow                             | RS485A                              |
| 8 / black                              | Power ground                        |

Pin numbers are those of the manufacturer's mating-face drawing, not a left-to-right order along loose wires. Use the supplied cable rather than building from color alone. The [original cable drawing, p.54](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf#page=54) and [interface drawing, pp.15–16](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf#page=15) are the authority for orientation. RS-485 is a differential pair; these are not UART TX/RX pins. No serial command protocol is needed for the depth-stream procedure.

### Synchronization boundary

**Do not connect an external trigger from this guide alone.** V1.0 p.34 describes 3.3 V CMOS and a 100 μs pulse; p.35 describes a 3.3–24 V input and ≥1 ms pulse and labels the connector M8, while the interface chapter identifies M12 A-coded. The cable appendix repeats an M8 label. Obtain a corrected drawing/electrical specification for the unit's revision before custom trigger wiring. The pin table above identifies the harness; it does not resolve those electrical contradictions. PoE, Ethernet and free-running capture do not require these pins. [Conflicting source, pp.15–16, 34–35 and 54](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)

Provide a metal heat path without obstructing either optical window or the projector. Avoid an extra transparent cover unless its optical effects have been evaluated. Record camera serial number, firmware, SDK release and mounting transform with the installation.

## Software and development resources

Use the [Orbbec SDK v2.10.6 release](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6), including matching Viewer and host libraries. Its exact [support table](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/README.md#14-supported-devices) lists Gemini 435Le with minimum firmware **1.2.4**, recommended **1.3.19**. The doc-center firmware page still recommends 1.3.11; record the source/version pair instead of treating both recommendations as identical. First enumerate the camera and inspect its installed firmware; a firmware upgrade is not the first diagnostic action.

Windows 10+ x64 and supported Linux x64/ARM64 hosts have separate packages. Install the correct architecture. On Linux use the release's udev setup for USB access where applicable, and verify Ethernet routing separately. The SDK code is MIT-licensed; follow the notices for bundled libraries and extensions. [SDK platform and license information](https://github.com/orbbec/OrbbecSDK_v2/tree/v2.10.6)

### Coordinates, timestamps and processing

Depth optical coordinates use +X right, +Y down, +Z forward; depth values use the frame's scale, not an assumed fixed millimetre per count. Obtain per-device intrinsics and extrinsics through the SDK when deprojecting or aligning depth to color. Physical dimension drawings do not replace calibrated transforms. For this model the documented color-origin offset relative to depth is +23.75 mm X; IMU origin is +15.48 mm X and −55.60 mm Z. [Coordinate definition](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Coordinate%20system%20of%20Gemini%20435Le)

Device capture timestamps and host arrival timestamps answer different questions. Inspect frame metadata and sequence gaps when evaluating packet loss. Check clock synchronization before fusing separate cameras. Capture unmodified depth before trying alignment, decimation, spatial/temporal filtering or a point cloud; filtering can smooth edges, change resolution or retain old measurements. Preserve preset, scale, exposure and processing settings with every recorded result. [Metadata](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Metadata%20of%20Gemini%20435Le), [filter reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Detailed%20Filter%20Reference)

## Getting started

### First depth image over PoE

1. Prepare one camera, its matching cable, a compliant PoE source, a Gigabit host adapter and a diffuse target about 1 m away. Leave the auxiliary connector capped. Check the label says **435Le**.
2. Power the camera through the PoE source and verify Ethernet link. Put only this camera on the test segment to avoid duplicate factory addresses.
3. In the host network settings assign an unused address such as **192.168.1.20**, mask **255.255.255.0**, to the camera-facing interface. The documented factory camera address is **192.168.1.10**. Keep this isolated interface off a conflicting office/VPN subnet. On Linux inspect `ip -br address` and `ip route get 192.168.1.10` before changing anything.
4. Launch matching **Orbbec Viewer**, locate the network device, check model/serial/firmware and open it. Discovery across subnets does not prove that streaming is routable. Allow the application on the isolated camera interface if the firewall blocks it; do not turn off the whole host firewall as a routine setup step.
5. Start **depth only**, **640 × 400**, **Y16**, **10 fps**, with default exposure/preset. Inspect the target and metadata. Add color at an enumerated profile only after depth is stable.
6. Stop streams cleanly. Save the chosen profiles, device serial/firmware, host link speed and depth scale with a short recording or screenshot.

**Expected result:** Viewer identifies a Gemini 435Le and displays continuously changing depth with a stable target plane. A zero/blank patch is invalid measurement, not contact with the lens. Persistent frame gaps require network/power checks before adding more streams. [Quickstart](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Quick%20Start%20Guide%20for%20Gemini%20435Le), [IP configuration](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Camera%20IP%20Configuration%20Function%20Description)

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
LD_LIBRARY_PATH="$SDK_ROOT/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}" ./build/roi_depth 640 400 10 net
```

The package layout and imported CMake target follow the [v2.10.6 development guide](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/docs/tutorial/installation_and_development_guide.md). If an archive places its CMake config elsewhere, point `OrbbecSDK_DIR` at the directory actually containing that config. Do not mix headers and libraries from different SDK releases.

**Expected result:** the process prints six measurement records and exits successfully after receiving 60 depth frames. Each record includes a frame index, `timestamp_us`, valid sample count and `median_mm`; a diffuse target at about 1 m should give a plausible distance near its measured plane position. Those are expected results, not recorded measurements. An unsupported-profile error means enumerate/select a profile the device actually advertises; do not substitute a color format or interpret compressed depth bytes as Y16. Return code 3 means camera selection was ambiguous; 4 means too few frames arrived. A full invalid patch is reported explicitly rather than treated as zero metres.

## Troubleshooting and FAQs

| Symptom                           | Ordered checks and recovery                                                                                                                                                                                     |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| No link or no device              | Confirm PoE output port/cable and link LEDs; try one known-good cable and compliant injector; confirm factory address and host route; isolate overlapping Wi-Fi/VPN routes rather than changing camera firmware |
| Device discovered but cannot open | Put host and camera on the same subnet; the discovery function can see across subnets without providing a working data route                                                                                    |
| Address unknown                   | Read MAC from label; use Viewer's temporary/Force IP on the same local segment. It is temporary and reverts on reboot; verify connectivity before saving a persistent address                                   |
| DHCP camera disappears            | Check the DHCP lease; the documented request timeout is 45 seconds, then the camera falls back to its last persistent address                                                                                   |
| Low frame rate                    | Confirm 1 Gbit/s link, start depth alone, reduce resolution/streams, inspect host load and packet loss. The 1280 × 800 depth limit is 10 fps; color maximums do not raise it                                    |
| Depth looks smooth but wrong      | Restore unrotated, unmirrored streams; inspect scale, preset, exposure, confidence and near limit; compare raw depth with filtered output                                                                       |
| Firmware update interrupted       | Keep a stable wired power/link path; use the exact 435Le firmware and supported Viewer recovery workflow. Do not cross-flash a Gemini 330 image                                                                 |

**Can I use the auxiliary connector like a 24 V industrial trigger?** Not until the conflicting V1.0 interface descriptions are clarified for the physical unit. Use free-running Ethernet capture meanwhile.

**Does a valid center median prove the camera is accurate across its field?** No. Measure a known plane, retain the valid-pixel fraction and assess center/edge regions over time. Spatial precision, absolute bias, temporal noise and fill rate are distinct metrics. [Depth quality metrics](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)

## Downloads and technical documents

| Resource                                                                                                                                      | Purpose and scope                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [435Le datasheet V1.0 PDF](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf) | Full hardware, stream, performance, power and mechanical reference; trigger conflicts noted above         |
| [435Le CAD V1.1 ZIP](https://doc.orbbec.com/attachments/10)                                                                                   | Official mechanical CAD; check connector and housing revision against the actual unit                     |
| [435Le firmware releases](https://github.com/orbbec/OrbbecFirmware/releases/tag/Gemin435Le-Firmware)                                          | Model-specific image and changelog; the official tag spells “Gemin435Le”                                  |
| [SDK v2.10.6](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6)                                                                    | Viewer, C/C++ libraries and examples for the matching host                                                |
| [SDK examples](https://github.com/orbbec/OrbbecSDK_v2/tree/v2.10.6/examples)                                                                  | Depth/color/IR, metadata, IMU, point cloud, recording/playback, multi-device and synchronization examples |
| [ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2) / [Python wrapper](https://github.com/orbbec/pyorbbecsdk)                           | Separate integrations; check the wrapper's device and SDK version matrix before selecting a branch        |
| [435Le official document center](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation)                                | Overview, quickstart, IP settings, coordinates, metadata, firmware, compliance, host and tool resources   |

### Extended official documentation

These official readers retain the detailed model/concept/sample paths. Use the model and release boundaries above before adapting an advanced example.

| Official reader                                                                                                                                                                                                                                  | Relevant guide section             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [Metadata of Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Metadata%20of%20Gemini%20435Le)                                                                                                          | Software and development resources |
| [Orbbec GMSL Cameras Supported Hosts and System Requirements](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20&%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements) | Software and development resources |
| [Orbbec Gemini 435Le Documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation)                                                                                                                                | Software and development resources |
| [Regulatory Compliance and Certificates of Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Regulatory%20Compliance%20and%20Certificates%20of%20Gemini%20435Le)                                        | Downloads and technical documents  |
| [Gemini 435Le Supported Hosts and System Requirements](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Gemini%20435Le%20Supported%20Hosts%20and%20System%20Requirements)                                            | Software and development resources |
| [Firmware Release of Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Firmware%20Release%20of%20Gemini%20435Le)                                                                                        | Downloads and technical documents  |
| [Download Tools](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Download%20Tools)                                                                                                                                  | Downloads and technical documents  |
| [About Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/About%20Gemini%20435Le)                                                                                                                        | Product overview                   |
| [Download CAD Files of Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Download%20CAD%20Files%20of%20Gemini%20435Le)                                                                                  | Downloads and technical documents  |
| [Quick Start Guide for Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Quick%20Start%20Guide%20for%20Gemini%20435Le)                                                                                  | Getting started                    |
| [Set up Cameras for External Synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)                                                                                   | Hardware and connections           |
| [Coordinate system of Gemini 435Le](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Coordinate%20system%20of%20Gemini%20435Le)                                                                                      | Hardware and connections           |
| [Camera IP Configuration Function Description](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Camera%20IP%20Configuration%20Function%20Description)                                                                | Software and development resources |
| [Detailed Filter Reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Detailed%20Filter%20Reference)                                                                                                   | Software and development resources |
| [Orbbec Gemini 330 Series Documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)                                                                                                                    | Software and development resources |
| [Depth Quality Metrics](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)                                                                                                           | Software and development resources |

## References and validation

Source review: **24 November 2026**. Hardware values above are scoped to Orbbec 435Le datasheet V1.0; software example APIs are scoped to SDK v2.10.6. Official diagrams and downloads remain Orbbec's copyrighted material and are linked with attribution. Detailed source readers, firmware instructions and advanced examples remain reachable from the document center; no hardware design schematic was found in the reviewed public resources.

This guide's first-result procedures and code were source reviewed. **SDK application execution and hardware testing were not run.** External trigger commissioning remains excluded pending a corrected connector/pulse specification; the free-running PoE procedure does not use those signals.

### Reviewed engineering reference chapters

The following chapters preserve the existing wiki’s detailed engineering reference: specifications, calibration and coordinate concepts, metadata, filter behavior, source examples, installation procedures, troubleshooting and manufacturer illustrations. They complement the current commissioning guide above. Revision notes beside affected chapters separate historical SDK or host examples from the model-specific power, firmware and first-result path. No historical command, example output or photograph is a claimed test on this unit.

### Orbbec Gemini 435Le Industrial Ethernet Stereo Vision Camera <a href="#reference-orbbec-gemini-435le-industrial-ethernet-stereo-vision-camera" id="reference-orbbec-gemini-435le-industrial-ethernet-stereo-vision-camera"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-435le-industrial-stereo-camera)

#### About Gemini 435Le <a href="#about-gemini-435le" id="about-gemini-435le"></a>

_Reviewed source:_ [_About Gemini 435Le_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/About%20Gemini%20435Le)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Product Introduction <a href="#id-1.-product-introduction" id="id-1.-product-introduction"></a>

The Gemini 435Le is a high-performance industrial-grade binocular 3D camera launched by Orbbec. Utilizing a master-slave fusion stereo vision technique, it consistently delivers high-quality depth images in both indoor and outdoor scenarios, ensuring reliable operation for robots in complex and demanding environments.

Its core strengths are primarily reflected in three aspects:

* Long-Range, High-Precision Perception: Comprehensively optimized for depth performance, it provides low-noise, high-density, and high-integrity environmental depth data during movement. It particularly enhances depth effectiveness at long distances, aiding large equipment in stable navigation and precise obstacle avoidance within complex environments.
* Accurate Edge Restoration Capability: Accurately restores the contour edges of complex objects. It can effectively identify objects made of various materials such as plastic, wood, and metal, meeting the requirements of high-precision identification and measurement tasks.
* Flexible Multi-Scenario Adaptation: Features multiple built-in preset depth modes. Users can flexibly switch between them via software (e.g., AMR perception mode for obstacle avoidance, dimension measurement mode for identification). A single camera can handle multiple tasks, significantly reducing hardware costs and system integration complexity.

Furthermore, the Gemini 435Le boasts an IP67 protection rating, exhibits excellent electromagnetic interference resistance, and can operate in a wide temperature range from -10°C to 50°C, ensuring stable performance even under harsh industrial conditions.

Each product in the Orbbec Gemini 435Le includes the following essential components:

* Binocular IR Module
* Speckle Projector Module
* RGB Module
* Laser Range Finder Module
* IMU Module
* Proprietary Depth Engine ASIC Chip
* Vision Co-processor
* Orbbec SDK
* Wrappers (e.g., ROS1 / ROS2 / Python)

The Orbbec Gemini 435Le camera is available on [Orbbec online store](https://store.orbbec.com/), which also offers a wide selection of multi-camera synchronization accessories.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/image.png)

#### 2. Orbbec SDK <a href="#id-2.-orbbec-sdk" id="id-2.-orbbec-sdk"></a>

The Orbbec SDK supports access to the fundamental layers and enables configuration for the Gemini 435Le cameras. For more details on the Orbbec SDK, please refer to Orbbec SDK architecture.

#### 3. Orbbec SDK Features <a href="#id-3.-orbbec-sdk-features" id="id-3.-orbbec-sdk-features"></a>

The Orbbec SDK provides the following functions, which are operational on the Gemini 435Le camera once installed:

* Depth Camera Access and Mode Control
* Support for Depth Post-Processing (e.g., filtering, downsampling, disparity-to-depth conversion)
* RGB Camera Access and Control (e.g., exposure and white balance)
* Support for Outputting a Confidence Map and adjusting confidence filter parameters
* Support for Depth-to-Color Alignment
* Synchronized Depth and RGB Camera Streams, with configurable latency between cameras
* External Device Synchronization Control, with configurable delay offset between devices
* Motion Sensor Access (gyroscope and accelerometer)
* Point Cloud Access and Control
* Camera Frame Metadata Access for processing image resolution, timestamps, etc.
* Device Calibration Data Access

#### 4. Camera Tools <a href="#id-4.-camera-tools" id="id-4.-camera-tools"></a>

Orbbec provides the following tools:

* Orbbec Viewer tool, used for monitoring device data streams and configuring different modes;
* Orbbec Quality Assessment Tool, used for assessing camera depth quality.

For detailed instructions on using the Orbbec Viewer, please refer to[Explore camera functions in Orbbec Viewer](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Explore%20Camera%20Functions%20in%20Orbbec%20Viewer%20\(Gemini%20330%20Series\)).

#### Quick Start Guide for Gemini 435Le <a href="#quick-start-guide-for-gemini-435le" id="quick-start-guide-for-gemini-435le"></a>

_Reviewed source:_ [_Quick Start Guide for Gemini 435Le_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Quick%20Start%20Guide%20for%20Gemini%20435Le)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
For DC operation use the datasheet’s 9–24 V input and supply capacity of at least 2 A. The quickstart’s older ≥1 A entry is superseded here by that model-specific requirement. PoE and DC are alternative documented arrangements; peak power and cable drop still matter.
{% endhint %}

#### 1. WHAT'S IN THE BOX? <a href="#id-1.-whats-in-the-box" id="id-1.-whats-in-the-box"></a>

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/RYXimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/RYXimage.png)

Gemini 435Le 3D Camera

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/yqrimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/yqrimage.png) [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/Ffbimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/Ffbimage.png)

Data Cable Power Cable

#### 2. CONNECTING THE ORBBEC CAMERA <a href="#id-2.-connecting-the-orbbec-camera" id="id-2.-connecting-the-orbbec-camera"></a>

**2.1 Connecting the camera using PoE (Power over Ethernet) for power supply.**

1. Prepare a PoE switch or a PoE-capable power source to supply power to the camera via the Ethernet (M12) data cable.
2. Remove the protective cap from the camera's M12 port, and connect the M12 X-coded connector of the data cable to the M12 port on the camera.
3. Insert the RJ45 end of the data cable into the PoE switch.
4. Connect the host computer to the PoE switch using a standard RJ45 Ethernet cable (CAT 5E or higher). (For PC connection, a non-PoE port on the switch may be used.)

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/NGMimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/NGMimage.png)

| Configuration                           | Hardware Requirement • In the product retail package                                                                                                   | Hardware Requirement • To be provided by the user                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PoE-powered, Host with Ethernet Port    | <p>• Gemini 435Le camera<br>• Gemini 435Le data cable (2m)</p>                                                                                         | <p>• PoE switch or PoE injector (IEEE 802.3af/at compliant), reference product: <a href="https://www.digikey.com/en/products/detail/microchip-technology/PD-3501G-AC-US/3992860">PD-3501G/AC-US Microchip Technology | Power Supplies – External/Internal (Off-Board) | DigiKey</a> <a href="https://www.omadanetworks.com/us/business-networking/omada-accessory-poe-adapter/poe150s/">POE150S | Omada PoE Injector | TP-Link</a> Note: depending on your selected PoE switch/PoE injector, a power cable for it may be required. Please ensure the selected cable complies with your regional power supply standards. • Gigabit Ethernet cable • &#x3C;10m, Cat5e or higher T568B-to-T568B or T568A-to-T568A standard compliant<br>• 10m+, Cat6 or higher T568B-to-T568B or T568A-to-T568A standard compliant</p> |
| PoE-powered, Host without Ethernet Port | In addition to the ‘PoE-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user. | In addition to the ‘PoE-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

**2.2 Connecting the camera using a DC power supply.**

1. Remove the protective cap from the camera's M12 port and connect the M12 X‑coded connector of the data cable to the camera's M12 port.
2. Remove the protective cap from the camera's M12 port and connect the power cable to the camera's M12 port.
3. Connect a 9‑24 V DC power supply to the red "POWER IN 9‑24V" pin and the black "POWER GND" pin.
4. Insert the RJ45 end of the data cable into the host computer or into the gateway device to which the host is connected.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/382image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/382image.png)

| Configuration                          | Hardware Requirement • In the product retail package                                                                                                  | Hardware Requirement • To be provided by the user                                                                                                                                                                                                                                                                          |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DC-powered, Host with Ethernet Port    | <p>• Gemini 435Le camera<br>• Gemini 435Le data cable (2m)<br>• Gemini 435Le power cable (2m)</p>                                                     | <p>• DC power supply (output: 9–24 V; quickstart entry ≥1 A, superseded here by the exact datasheet’s ≥2 A supply requirement)<br>• If a power extension cord is required, make sure the current and voltage received by the camera’s original power cord harness meet the power supply requirements in its datasheet.</p> |
| DC-powered, Host without Ethernet Port | In addition to the ‘DC-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user. | In addition to the ‘DC-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user.                                                                                                                                                                      |

#### 3. GET ORBBEC VIEWER <a href="#id-3.-get-orbbec-viewer" id="id-3.-get-orbbec-viewer"></a>

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Quick Start Guide for Gemini 435Le](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/raHhoaBtNUidaSjRgW6R/image202503165.png)

#### 4. LAUNCHING ORBBEC VIEWER <a href="#id-4.-launching-orbbec-viewer" id="id-4.-launching-orbbec-viewer"></a>

For detailed instructions, please refer to the Orbbec Viewer tutorial video below.

[https://www.youtube.com/@Orbbec3d](https://www.youtube.com/@Orbbec3d) [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/0XAimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/0XAimage.png)

***

#### 5. Network Environment Configuration on the host <a href="#id-5.-network-environment-configuration-on-the-host" id="id-5.-network-environment-configuration-on-the-host"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

**5.1 Linux platform**

**5.11 Environment preparation**

1. Prepare a Linux x86\_64 / Arm64 platform with Ubuntu 20.04 or later.
2. To ensure stable operation and optimal performance of the camera, connect the camera to a Gigabit (1000 Mbps) Ethernet port. If connected to a Fast Ethernet (100 Mbps) port, insufficient network bandwidth may result in failure to achieve expected performance and unstable connectivity.

**5.12 Environment configuration**

1. The Gemini 435Le device has a default IP address of 192.168.1.10.
2. The camera must be connected to the host via direct connection or through a switch, andthe host must be in the same subnet for the device to be discovered and recognized.
3. Once recognized, the Gemini 435Le can be accessed and controlled using the Orbbec Viewer tool or the SDK.
4. For detailed network configuration instructions, please refer to the documentation: [Camera IP Configuration Function Description](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Camera%20IP%20Configuration%20Function%20Description)

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/NQaimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/NQaimage.png)

**5.13Recommended configuration**

(1) If, after configuring the network environment as described in section "2", the Orbbec Viewer tool fails to recognize the Gemini 435Le network device, you should check whether the Wi-Fi connection is enabled. If Wi-Fi is enabled, it needs to be turned off first. Then, re-enable the local network connection or power cycle the network device, and it should be recognized.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/wRtimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/wRtimage.png)

(2) Due to differences in system networks and power management across platforms, packet loss may occur to varying degrees during the process of stream capture on the host machine, which can result in the frame rate not meeting expectations. Therefore, before using the Gemini 435Le device on different platforms, it is essential to configure and verify the platform and system settings to avoid issues like frame loss.

**Computer power configuration:**

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/EMfimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/EMfimage.png)

**Computer network card configuration:**

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/zscimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/zscimage.png)

**Firewall Configuration:**

The firewall on Ubuntu is disabled by default. Ubuntu uses Uncomplicated Firewall (UFW) as the default firewall management tool, and UFW is disabled by default. If a firewall is enabled, allow the documented camera discovery and streaming traffic on the isolated camera interface. Do not disable protection on unrelated host interfaces; retain a network trace when discovery fails.

**5.1.4 Start Orbbec Viewer**

Once the environment and configurations are properly set up as described in the prevouse sections, you can start experiencing the Gemini 435Le by launching the provided Orbbec Viewer tool for Linux/Arm platforms, as shown in the image below:

Open the Orbbec Viewer tool, select the Gemini 435Le network device you want to open, and click Open:

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/Bitimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/Bitimage.png)

**5.2 Windows Platform**

**5.21 Environment Preparation**

1. Windows 10 or above platforms, x64 operating system, 8/16GB or above memory;
2. Connect directly using either the Ethernet port on the host/switch or through a USB-to-Ethernet adapter.

**5.22 Network Configuration**

1. The Gemini 435Le device has a default IP address of 192.168.1.10.
2. The camera must be connected to the host via direct connection or through a switch, andthe host must be in the same subnet for the device to be discovered and recognized.
3. Once recognized, the Gemini 435Le can be accessed and controlled using the Orbbec Viewer tool or the SDK.
4. For detailed network configuration instructions, please refer to the documentation: [Camera IP Configuration Function Description](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Camera%20IP%20Configuration%20Function%20Description)

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/dhEimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/dhEimage.png)

**5.23 Recommended configuration**

Due to differences in system networks and power management across platforms, packet loss may occur to varying degrees during the process of stream capture on the host machine, which can result in the frame rate not meeting expectations. Therefore, before using the Gemini 435Le device on different platforms, it is essential to configure and verify the platform and system settings to avoid issues like frame loss.

1. Computer power configuration: [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/01oimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/01oimage.png)

2.Computer network card configuration:

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/x7Himage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/x7Himage.png)

3. Computer firewall configuration:

To allow Orbbec Viewer to communicate throughWindows Defender Firewall, follow the path below: Control Panel\System and Security\Windows Defender Firewall

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/lZpimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/lZpimage.png) [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/LqZimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/LqZimage.png)

**5.24 Start Orbbec Viewer**

Once the environment and configurations are properly set up as described in the previous sections, you can start experiencing the Gemini 435Le by launching the provided Orbbec Viewer tool on Windows platforms, as shown in the image below:

Open the Orbbec Viewer tool, select the Gemini 435Le network device you want to open, and click Open:

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/xZ2image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/xZ2image.png)

Once the device is successfully loaded, the detailed functionality window will appear, allowing you to start the experience:

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/VIoimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/VIoimage.png)

#### Camera IP Configuration Function Description <a href="#camera-ip-configuration-function-description" id="camera-ip-configuration-function-description"></a>

_Reviewed source:_ [_Camera IP Configuration Function Description_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Camera%20IP%20Configuration%20Function%20Description)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. First-Time Use <a href="#id-1.-first-time-use" id="id-1.-first-time-use"></a>

When using the camera for the first time after receiving it, ensure the host and camera are on the same subnet for successful communication:

1. IP Address: 192.168.1.xxa. Configure the host and camera to be on the same subnet. The camera’s default IP is 192.168.1.10.b. Ensure there is no IP conflict between the host and the camera.
2. Subnet Mask (MASK):

* For local networks, the recommended subnet mask is 255.255.255.0.

3. Default Gateway: 192.168.1.xxa. It is recommended to set the gateway within the same subnet as the IP or leave it unconfigured.b. Ensure the gateway does not conflict with the host or camera IP.c.Do not set it to 0.0.0.0.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/t5qimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/t5qimage.png)

#### 2. Persistent IP Configuration <a href="#id-2.-persistent-ip-configuration" id="id-2.-persistent-ip-configuration"></a>

The camera supports manual configuration of Persistent IP, Subnet Mask, and Default Gateway through Orbbec Viewer or Orbbec SDK, ensuring stable operation in complex network environments.Persistent IP settings are retained after power-off.

**2.1 Method 1: Using Orbbec Viewer**

1. Launch Orbbec Viewer and locate the IP Configuration option.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/Vy6image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/Vy6image.png)

1. The configured parameters will take effect after the camera reconnects

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/Gljimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/Gljimage.png)

**2.2 Method 2: Using Orbbec SDK**

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
 // Create a context object for managing and querying device lists ob::Context ctx; // Query the device list in current context auto deviceList = ctx.queryDeviceList(); // Check if the device list is empty or has no devices if(!deviceList || deviceList->getCount() < 1) { // If no device found, output message and exit std::cout << "No device found! Please connect a supported device and retry this program." << std::endl; return; } // Get the first device from the device list auto device = deviceList->getDevice(0); // Check if device was successfully obtained if(!device) { // If failed to get device, output error message and exit std::cerr << "Failed to get the device." << std::endl; return; } // Define network IP configuration parameters OBNetIpConfig ipConfig = { 0, // dhcp off { 192, 168, 1, 26 }, // address { 255, 255, 255, 0 }, // mask { 192, 168, 1, 254 } // gateway }; // Configure the device's IP address settings device->setStructuredData(OB_STRUCT_DEVICE_IP_ADDR_CONFIG, (const uint8_t *)(&ipConfig), sizeof(ipConfig));
```

#### 3. DHCP Configuration <a href="#id-3.-dhcp-configuration" id="id-3.-dhcp-configuration"></a>

The camera supports enabling DHCP functionality through either Orbbec Viewer or Orbbec SDK, allowing for dynamic IP address assignment. This is particularly suitable for scenarios requiring flexible deployment or temporary debugging. When switching from DHCP to Persistent IP mode, the camera automatically loads the last configured: Persistent IP address, Subnet Mask (MASK) andDefault Gateway

**3.1 Method 1: Using Orbbec Viewer**

1. Launch Orbbec Viewer.
2. Locate and activate the DHCP switch in the network configuration interface.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/hw4image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/hw4image.png)

**3.2 Method 2: Using Orbbec SDK**

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
 // Create a context object for device management and querying ob::Context ctx; // Query device list in current context auto deviceList = ctx.queryDeviceList(); // Check if device list is empty or contains no devices if(!deviceList || deviceList->getCount() < 1) { // If no devices found, output message and exit std::cout << "No device found! Please connect a supported device and retry this program." << std::endl; return; } // Get first device from device list auto device = deviceList->getDevice(0); // Verify successful device acquisition OBNetIpConfig ipConfig = { 0 }; uint32_t ipConfigSize = 0; device->getStructuredData(OB_STRUCT_DEVICE_IP_ADDR_CONFIG, (uint8_t*)&ipConfig, &ipConfigSize); if(ipConfigSize != sizeof(OBNetIpConfig)) { std::cerr << "Failed to get the device ip config." << std::endl; return; } // Enable DHCP for automatic IP configuration ipConfig.dhcp = 1; // Configure device IP address settings device->setStructuredData(OB_STRUCT_DEVICE_IP_ADDR_CONFIG, (const uint8_t *)(&ipConfig), sizeof(ipConfig));
```

**3.3 DHCP Failure Management**

1. **DHCP Request Process:**

* The device broadcasts DHCP requests with a default timeout period of 45 seconds

2. **Fallback Mechanism:**

* If no response is received from the DHCP server within the timeout period
* OR if the DHCP assignment fails
* The device will automatically revert to thelast configured Persistent IP

#### 4. Special Function Description <a href="#id-4.-special-function-description" id="id-4.-special-function-description"></a>

**4.1 Cross-Subnet Device Discovery Function**

This camera supports the cross-subnet device discovery function. When the camera and the host are on different subnets, users can still scan and obtain device information through the Orbbec Viewer tool or Orbbec SDK.

Under the cross-subnet device discovery function, only device discovery is supported, and direct data communication is not possible. To establish normal communication, the camera and the host must be adjusted to the same subnet.

**4.2 Method 1: Using Orbbec Viewer**

Hover the mouse over the target device in the device list to obtain the current device information.

[![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/tCbimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/tCbimage.png)

**4.3 Method 2: Using Orbbec SDK**

Refer to the Orbbec SDK sample in the following link:

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

#### 5. Temporary IP Address <a href="#id-5.-temporary-ip-address" id="id-5.-temporary-ip-address"></a>

When the camera cannot be connected due to an unknown or misconfigured IP address, theTemporary IP Address (Force IP) can be used to forcibly assign a new IP address and quickly restore communication. This function is suitable for debugging, device recovery, or cross-network environment adaptation.

**Note:**

* The Temporary IP is only for short-term debugging. After the camera reboots, it will revert to the original Persistent IP or DHCP configuration.
* To permanently retain the assigned IP, manually switch toPersistent IP mode and save the settings.

**Prerequisites:**

1. The camera’s MAC address must be known (usually printed on the device label or original packaging).
2. The camera and the host must be directly connected via Ethernet or be on the same local network (avoiding router or firewall interference).

#### Explore Camera Functions in Orbbec Viewer (Gemini 330 Series) <a href="#explore-camera-functions-in-orbbec-viewer-gemini-330-series" id="explore-camera-functions-in-orbbec-viewer-gemini-330-series"></a>

_Reviewed source:_ [_Explore Camera Functions in Orbbec Viewer (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Explore%20Camera%20Functions%20in%20Orbbec%20Viewer%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

With one application owning the camera, open its device panel, select a supported depth profile and start depth alone. Inspect live frame rate, exposure and the log before adding color or filters. Save a short recording with its profile and metadata, then stop streams before changing work mode. [Viewer v2 control reference, 52 pages](https://doc.orbbec.com/attachments/7).

[Explore Camera Functions in Orbbec Viewer (Gemini 330 Series).pdf](https://doc.orbbec.com/attachments/7)

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

```
\`\`\`cpp #include <iostream> #include "utils.hpp" #include "libobsensor/ObSensor.hpp" #include "libobsensor/hpp/Error.hpp" \`\`\`
```

#### 3. Find an Orbbec Device <a href="#id-3.-find-an-orbbec-device" id="id-3.-find-an-orbbec-device"></a>

First, we need to check how many Orbbec devices are connected to your computer. Use the `queryDeviceList()` function to retrieve the connected devices.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Create a Context. ob::Context ctx; // Query the list of connected devices auto devList = ctx.queryDeviceList(); if (devList->deviceCount() == 0) { std::cerr << "Device not found!" << std::endl; return -1; }
```

If a device is detected, you can proceed to access its information and sensors.

#### 4. Access Device Information <a href="#id-4.-access-device-information" id="id-4.-access-device-information"></a>

Once you have a device list, open the first device and retrieve some basic information such as the device name and firmware version.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
auto dev = devList->getDevice(0); auto devInfo = dev->getDeviceInfo(); std::cout << "Device name: " << devInfo->name() << std::endl; std::cout << "Firmware version: " << devInfo->firmwareVersion() << std::endl; // By getting the serial number of the device auto sn = devInfo->serialNumber(); std::cout << "Serial number: " << sn << std::endl; // By getting the connection type of the device auto connectType = devInfo->connectionType(); std::cout << "ConnectionType: " << connectType << std::endl;
```

#### 5. List Sensors <a href="#id-5.-list-sensors" id="id-5.-list-sensors"></a>

Next, explore the sensors available on the device by fetching the sensor list and printing each sensor type.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
 // Get the list of supported sensors std::cout << "Sensor types: " << std::endl; auto sensorList = dev->getSensorList(); for(uint32_t i = 0; i < sensorList->count(); i++) { auto sensor = sensorList->getSensor(i); switch(sensor->type()) { case OB_SENSOR_COLOR: std::cout << "\tColor sensor" << std::endl; break; case OB_SENSOR_DEPTH: std::cout << "\tDepth sensor" << std::endl; break; case OB_SENSOR_IR: std::cout << "\tIR sensor" << std::endl; break; case OB_SENSOR_IR_LEFT: std::cout << "\tIR Left sensor" << std::endl; break; case OB_SENSOR_IR_RIGHT: std::cout << "\tIR Right sensor" << std::endl; break; case OB_SENSOR_GYRO: std::cout << "\tGyro sensor" << std::endl; break; case OB_SENSOR_ACCEL: std::cout << "\tAccel sensor" << std::endl; break; default: break; } }
```

#### 6. Error Handling <a href="#id-6.-error-handling" id="id-6.-error-handling"></a>

It’s important to include error handling in your applications. The Orbbec SDK provides detailed exceptions that can be caught to understand what went wrong during execution.

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
\`\`\`cpp catch(ob::Error &e) { std::cerr << "Error: " << e.getMessage() << std::endl; return -2; } \`\`\`
```

#### 7. Full Source <a href="#id-7.-full-source" id="id-7.-full-source"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
#include <iostream> #include "utils.hpp" #include "libobsensor/ObSensor.hpp" #include "libobsensor/hpp/Error.hpp" #define ESC 27 int main(int argc, char **argv) try { // Print the sdk version number, the sdk version number is divided into major version number, minor version number and revision number std::cout << "SDK version: " << ob::Version::getMajor() << "." << ob::Version::getMinor() << "." << ob::Version::getPatch() << std::endl; // Print sdk stage version std::cout << "SDK stage version: " << ob::Version::getStageVersion() << std::endl; // Create a Context. ob::Context ctx; // Query the list of connected devices auto devList = ctx.queryDeviceList(); // Get the number of connected devices if(devList->deviceCount() == 0) { std::cerr << "Device not found!" << std::endl; return -1; } // Create a device, 0 means the index of the first device auto dev = devList->getDevice(0); // Get device information auto devInfo = dev->getDeviceInfo(); // Get the name of the device std::cout << "Device name: " << devInfo->name() << std::endl; // Get the pid, vid, uid of the device std::cout << "Device pid: " << devInfo->pid() << " vid: " << devInfo->vid() << " uid: " << devInfo->uid() << std::endl; // By getting the firmware version number of the device auto fwVer = devInfo->firmwareVersion(); std::cout << "Firmware version: " << fwVer << std::endl; // By getting the serial number of the device auto sn = devInfo->serialNumber(); std::cout << "Serial number: " << sn << std::endl; // By getting the connection type of the device auto connectType = devInfo->connectionType(); std::cout << "ConnectionType: " << connectType << std::endl; // Get the list of supported sensors std::cout << "Sensor types: " << std::endl; auto sensorList = dev->getSensorList(); for(uint32_t i = 0; i < sensorList->count(); i++) { auto sensor = sensorList->getSensor(i); switch(sensor->type()) { case OB_SENSOR_COLOR: std::cout << "\tColor sensor" << std::endl; break; case OB_SENSOR_DEPTH: std::cout << "\tDepth sensor" << std::endl; break; case OB_SENSOR_IR: std::cout << "\tIR sensor" << std::endl; break; case OB_SENSOR_IR_LEFT: std::cout << "\tIR Left sensor" << std::endl; break; case OB_SENSOR_IR_RIGHT: std::cout << "\tIR Right sensor" << std::endl; break; case OB_SENSOR_GYRO: std::cout << "\tGyro sensor" << std::endl; break; case OB_SENSOR_ACCEL: std::cout << "\tAccel sensor" << std::endl; break; default: break; } } std::cout << "Press ESC to exit! " << std::endl; while(true) { // Get the value of the pressed key, if it is the esc key, exit the program int key = getch(); if(key == ESC) break; } return 0; } catch(ob::Error &e) { std::cerr << "function:" << e.getName() << "\nargs:" << e.getArgs() << "\nmessage:" << e.getMessage() << "\ntype:" << e.getExceptionType() << std::endl; exit(EXIT_FAILURE); }
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
#include "window.hpp" #include "libobsensor/hpp/Pipeline.hpp" #include "libobsensor/hpp/Error.hpp" #include <mutex> #include <thread>
```

#### 3. Initialize the Pipeline <a href="#id-3.-initialize-the-pipeline" id="id-3.-initialize-the-pipeline"></a>

The pipeline manages streams and configurations for different sensors:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Create a pipeline with default device ob::Pipeline pipe; // Configure which streams to enable or disable for the Pipeline by creating a Config std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>();
```

#### 4. Configure Streams <a href="#id-4.-configure-streams" id="id-4.-configure-streams"></a>

Configure which streams to enable based on the sensors available on the device:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
auto device = pipe.getDevice(); auto sensorList = device->getSensorList(); for(int i = 0; i < sensorList->count(); i++) { auto sensorType = sensorList->type(i); if(sensorType == OB_SENSOR_GYRO || sensorType == OB_SENSOR_ACCEL) { continue; } auto profiles = pipe.getStreamProfileList(sensorType); auto profile = profiles->getProfile(OB_PROFILE_DEFAULT); config->enableStream(profile); }
```

#### 5. Start the Main Pipeline <a href="#id-5.-start-the-main-pipeline" id="id-5.-start-the-main-pipeline"></a>

Start the main pipeline with the configured streams:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Start the pipeline with config std::mutex frameMutex; std::map<OBFrameType, std::shared_ptr<ob::Frame>> frameMap; pipe.start(config, [&](std::shared_ptr<ob::FrameSet> frameset) { auto count = frameset->frameCount(); for(int i = 0; i < count; i++) { auto frame = frameset->getFrame(i); std::unique_lock<std::mutex> lk(frameMutex); frameMap[frame->type()] = frame; } });
```

#### 6. Handle IMU Data Separately <a href="#id-6.-handle-imu-data-separately" id="id-6.-handle-imu-data-separately"></a>

Due to the high frame rate of IMU sensors, it is beneficial to handle their data in a separate pipeline:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
auto dev = pipe.getDevice(); auto imuPipeline = std::make_shared<ob::Pipeline>(dev); std::mutex imuFrameMutex; std::map<OBFrameType, std::shared_ptr<ob::Frame>> imuFrameMap; try { auto accelProfiles = imuPipeline->getStreamProfileList(OB_SENSOR_ACCEL); auto gyroProfiles = imuPipeline->getStreamProfileList(OB_SENSOR_GYRO); auto accelProfile = accelProfiles->getProfile(OB_PROFILE_DEFAULT); auto gyroProfile = gyroProfiles->getProfile(OB_PROFILE_DEFAULT); std::shared_ptr<ob::Config> imuConfig = std::make_shared<ob::Config>(); imuConfig->enableStream(accelProfile); imuConfig->enableStream(gyroProfile); imuPipeline->start(imuConfig, [&](std::shared_ptr<ob::FrameSet> frameset) { auto count = frameset->frameCount(); for(int i = 0; i < count; i++) { auto frame = frameset->getFrame(i); std::unique_lock<std::mutex> lk(imuFrameMutex); imuFrameMap[frame->type()] = frame; } }); } catch(...) { std::cout << "IMU sensor not found!" << std::endl; imuPipeline.reset(); }
```

#### 7. Render Frames <a href="#id-7.-render-frames" id="id-7.-render-frames"></a>

Create a window for rendering the collected frames:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
Window app("MultiStream", 1280, 720, RENDER_GRID); while(app) { std::vector<std::shared_ptr<ob::Frame>> framesForRender; { std::unique_lock<std::mutex> lock(frameMutex); for(auto &frame: frameMap) { framesForRender.push_back(frame.second); } } { std::unique_lock<std::mutex> lock(imuFrameMutex); for(auto &frame: imuFrameMap) { framesForRender.push_back(frame.second); } } app.addToRender(framesForRender); }
```

#### 8. Stop the Pipeline <a href="#id-8.-stop-the-pipeline" id="id-8.-stop-the-pipeline"></a>

Properly stop the pipelines when the application is closing to ensure all resources are freed:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
pipe.stop(); if(imuPipeline) { imuPipeline->stop(); }
```

#### 9. Full Source <a href="#id-9.-full-source" id="id-9.-full-source"></a>

This is a brief overview of the complete application, which integrates all components discussed:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
#include "window.hpp" #include "libobsensor/hpp/Pipeline.hpp" #include "libobsensor/hpp/Error.hpp" #include <mutex> #include <thread> int main(int argc, char **argv) try { // Create a pipeline with default device ob::Pipeline pipe; // Configure which streams to enable or disable for the Pipeline by creating a Config std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>(); // enumerate and config all sensors auto device = pipe.getDevice(); auto sensorList = device->getSensorList(); for(int i = 0; i < sensorList->count(); i++) { auto sensorType = sensorList->type(i); if(sensorType == OB_SENSOR_GYRO || sensorType == OB_SENSOR_ACCEL) { continue; } auto profiles = pipe.getStreamProfileList(sensorType); auto profile = profiles->getProfile(OB_PROFILE_DEFAULT); config->enableStream(profile); } // Start the pipeline with config std::mutex frameMutex; std::map<OBFrameType, std::shared_ptr<ob::Frame>> frameMap; pipe.start(config, [&](std::shared_ptr<ob::FrameSet> frameset) { auto count = frameset->frameCount(); for(int i = 0; i < count; i++) { auto frame = frameset->getFrame(i); std::unique_lock<std::mutex> lk(frameMutex); frameMap[frame->type()] = frame; } }); // The IMU frame rate is much faster than the video, so it is advisable to use a separate pipeline to obtain IMU data. auto dev = pipe.getDevice(); auto imuPipeline = std::make_shared<ob::Pipeline>(dev); std::mutex imuFrameMutex; std::map<OBFrameType, std::shared_ptr<ob::Frame>> imuFrameMap; try { auto accelProfiles = imuPipeline->getStreamProfileList(OB_SENSOR_ACCEL); auto gyroProfiles = imuPipeline->getStreamProfileList(OB_SENSOR_GYRO); auto accelProfile = accelProfiles->getProfile(OB_PROFILE_DEFAULT); auto gyroProfile = gyroProfiles->getProfile(OB_PROFILE_DEFAULT); std::shared_ptr<ob::Config> imuConfig = std::make_shared<ob::Config>(); imuConfig->enableStream(accelProfile); imuConfig->enableStream(gyroProfile); imuPipeline->start(imuConfig, [&](std::shared_ptr<ob::FrameSet> frameset) { auto count = frameset->frameCount(); for(int i = 0; i < count; i++) { auto frame = frameset->getFrame(i); std::unique_lock<std::mutex> lk(imuFrameMutex); imuFrameMap[frame->type()] = frame; } }); } catch(...) { std::cout << "IMU sensor not found!" << std::endl; imuPipeline.reset(); } // Create a window for rendering and set the resolution of the window Window app("MultiStream", 1280, 720, RENDER_GRID); while(app) { std::vector<std::shared_ptr<ob::Frame>> framesForRender; { std::unique_lock<std::mutex> lock(frameMutex); for(auto &frame: frameMap) { framesForRender.push_back(frame.second); } } { std::unique_lock<std::mutex> lock(imuFrameMutex); for(auto &frame: imuFrameMap) { framesForRender.push_back(frame.second); } } app.addToRender(framesForRender); } // Stop the Pipeline, no frame data will be generated pipe.stop(); if(imuPipeline) { imuPipeline->stop(); } return 0; } catch(ob::Error &e) { std::cerr << "function:" << e.getName() << "\nargs:" << e.getArgs() << "\nmessage:" << e.getMessage() << "\ntype:" << e.getExceptionType() << std::endl; exit(EXIT_FAILURE); }
```

#### 10. Next Steps <a href="#id-10.-next-steps" id="id-10.-next-steps"></a>

* Learn more about configuring and using individual sensors with the Orbbec SDK.
* Explore advanced features and settings available in the Orbbec SDK documentation.
* Begin integrating Orbbec Device capabilities into your larger projects and applications.

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

![Official Orbbec figure from Depth Quality Metrics](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/NmNSQhrQkuCoGDyBAoJx/image%20Depth%20quality%20metrics1.png)

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

#### Metadata of Gemini 435Le <a href="#metadata-of-gemini-435le" id="metadata-of-gemini-435le"></a>

_Reviewed source:_ [_Metadata of Gemini 435Le_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Metadata%20of%20Gemini%20435Le)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

#### 1. Brief Introduction <a href="#id-1.-brief-introduction" id="id-1.-brief-introduction"></a>

Metadata refers to data that provides information about other data. It acts like a descriptive label that helps to identify, manage, and use the actual data more effectively. Metadata can include a variety of details depending on the context:

* Descriptive Metadata: This includes information like titles, authors, and keywords which help in discovering and identifying data. For example, the metadata of a book might include its title, author, publisher, and ISBN.
* Structural Metadata: This indicates how a dataset is organized or how complex objects are put together. For instance, in a database, structural metadata would describe the tables, columns, relationships, and other structures used to organize data.
* Administrative Metadata: This provides information to help manage a resource, like when and how it was created, file type, and access permissions. It might also include technical data necessary for managing digital resources such as file types or compression methods.
* Reference Metadata: It provides information about the contents and quality of statistical data. This type is common in data-centric fields like statistics and data analysis, providing details on data sources, accuracy, and timeliness.

#### 2. metadata of MIPI <a href="#id-2.-metadata-of-mipi" id="id-2.-metadata-of-mipi"></a>

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

In the context of MIPI, metadata can involve various types of information depending on the application. For example, in camera interfaces like MIPI CSI-2, metadata may include details about camera module parameters, resolution settings, frame rates, color spaces, white balance settings, sharpness, and chrominance. These details are crucial for properly configuring and utilizing the camera module.

Additionally, metadata might also pertain to control information related to data transmission, synchronization, error detection, and correction. This metadata is essential for ensuring the integrity and accuracy of data, especially in environments characterized by high-speed and low-power transmission.

On a broader scale, MIPI metadata may also involve system-level information, such as the connections between devices, data transmission rates, and power consumption budgets. This information aids in system-level design and optimization to ensure optimal performance and power efficiency of the entire system.

The specific definitions and implementations of metadata in the MIPI standards can vary based on different applications and requirements, and the information included in the metadata may differ among various device manufacturers.

#### 3. Gemini 435Le metadata definition <a href="#id-3.-gemini-435le-metadata-definition" id="id-3.-gemini-435le-metadata-definition"></a>

{% hint style="info" %}
Field availability is device/firmware/transport specific. Keep device capture timestamps separate from host arrival time and retain metadata with the selected stream profile. A field in a common SDK enumeration is not proof that this camera produces it.
{% endhint %}

Orbbec 3D cameras typically include components such as 2 IR modules, LDM, laser ranging module, and a color camera. Both the IR module and the color camera transmit data to the mainboard using the MIPI protocol, thus carrying metadata. Users can utilize the Orbbec SDK to parse this metadata and view it directly within the Orbbec Viewer to see the current data stream's metadata information.

Gemini 435Le supported metadata includes the following content:

Table 3-1 Depth/IR metadata

| Metadata                  | Definition                                  | Range                      |
| ------------------------- | ------------------------------------------- | -------------------------- |
| Timestamp (Camera)        | exposure end timestamp                      | /                          |
| Sensor Timestamp (Camera) | Exposure center timestamp-1/2 exposure time | /                          |
| Device Timestamp (Camera) | =Timestamp                                  | /                          |
| Global Timestamp (Host)   | Transformed Device Timestamp                | /                          |
| System Timestamp (Host)   | Time of Arrival in SDK (Entire Frame)       | /                          |
| frame number              | current frame number                        | /                          |
| auto exposure             | content of AE state                         | \[0,1] 0 for off, 1 for on |
| exposure                  | content of exposure time                    | 1\~19900                   |
| gain                      | content of exposure digital gain            | 16\~248                    |
| ae roi left               | ROI AE start pixel X-axis                   | 0\~1278                    |
| ae roi top                | ROI AE start pixel Y-axis                   | 0\~798                     |
| ae roi right              | ROI AE end pixel X-axis                     | 1\~1279                    |
| ae roi bottom             | ROI AE end pixel Y-axis                     | 1\~799                     |
| exposure priority         | content of AE exposure priority state       | \[0,1]                     |
| laser power               | laser optical power                         | \[0,60,120,240,300,360]    |
| laser power mode          | content of laser switch on or off           | \[0,1] 0 for off, 1 for on |
| Gpio Input Data           | Reserved                                    | Reserved                   |

Table 4-2 RGB metadata definition

| Metadata                  | Definition                                  | Range                      |
| ------------------------- | ------------------------------------------- | -------------------------- |
| timestamp (Camera)        | exposure end timestamp                      | /                          |
| sensor timestamp (Camera) | Exposure center timestamp-1/2 exposure time | /                          |
| Device Timestamp (Camera) | =Timestamp                                  | /                          |
| Global Timestamp (Host)   | Transformed Device Timestamp                | /                          |
| System Timestamp (Host)   | Time of Arrival in SDK (Entire Frame)       | /                          |
| frame number              | current frame number                        | /                          |
| auto exposure             | content of AE state                         | \[0,1]                     |
| exposure                  | content of exposure time(us)                | \[1,10000]                 |
| gain                      | content of exposure digital gain            | \[0,128]                   |
| auto white balance        | content of AWB state                        | 0 or 1                     |
| white balance             | current AWB color temperature               | \[2800,6500]               |
| brightness                | current brightness                          | \[-64,64]                  |
| contrast                  | contrast                                    | \[0,100]                   |
| saturation                | saturation                                  | \[0,100]                   |
| sharpness                 | sharpness                                   | \[0,100]                   |
| backlight compensation    | state of backlight compensation enable      | \[0,1] 0 for off, 1 for on |
| hue                       | hue                                         | \[-180,180]                |
| Gamma                     | Gamma                                       | \[100,500]                 |
| power line frequency      | anti-flicker state                          | \[50,60,disable,auto]      |
| low light compensation    | state of low light compensation enable      | \[0,1] 0 for off, 1 for on |
| manual white balance      | current AWB color temperature set manually  | \[2800,6500]               |
| actual frame rate         | frame rate set                              | \[5,10,15,30,60]           |
| ae roi left               | ROI AE start pixel X-axis                   | \[0,1278]                  |
| ae roi top                | ROI AE start pixel Y-axis                   | \[0,798]                   |
| ae roi right              | ROI AE end pixel X-axis                     | \[1,1279]                  |
| ae roi bottom             | ROI AE end pixel Y-axis                     | \[1,799]                   |

When using Orbbec 3D cameras on user platforms, metadata can be utilized to assess frame information, enabling advanced functions such as data correction, frame loss verification, and HDR (High Dynamic Range) fusion. This allows for enhanced accuracy and functionality in applications where precise imaging and data integrity are critical.

#### Coordinate system of Gemini 435Le <a href="#coordinate-system-of-gemini-435le" id="coordinate-system-of-gemini-435le"></a>

_Reviewed source:_ [_Coordinate system of Gemini 435Le_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Coordinate%20system%20of%20Gemini%20435Le)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Brief Introduction <a href="#id-1.-brief-introduction-1" id="id-1.-brief-introduction-1"></a>

Gemini 435Le 3D camera usually contains depth camera and color camera and IMU. Those sensors collect information and output it as streams.

In order to characterize the positional relationship better, Orbbec Gemini 435Le define 3D camera coordinate system. The coordinate system of a 3D camera typically contains Depth coordinate system & Color coordinate system & IMU coordinate system.

#### 2. System Cooridnate <a href="#id-2.-system-cooridnate" id="id-2.-system-cooridnate"></a>

Every coordinates usually consists of three components:

1. origin: Depth coordinate system's origin locates at the optical center of the Left IR camera lens. Color coordinate system's origin locates at the optical center of the Color camera lens. IMU coordinate system's origin locates at the physical center of the IMU.
2. category: meeting the definition of right-hand coordinate system. The positive direction of the X-axis is to the right. The positive direction of the Y-axis is to the down. The positive direction of the Z-axis is to the forward.
3. unit: Default unit is millimeter.

#### 3. Gemini 435Le System Cooridnate <a href="#id-3.-gemini-435le-system-cooridnate" id="id-3.-gemini-435le-system-cooridnate"></a>

Gemini 435Le coordinate system reference picture is shown as below.

Picture 3-1 Coordinate system schematic diagram

| Coordinate system       | Gemini 435Le                                                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Depth coordinate system | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/MlBimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/MlBimage.png) |
| Color coordinate system | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/Buoimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/Buoimage.png) |
| IMU coordinate system   | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/LbBimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/LbBimage.png) |

The relative position relationship of the coordinate systems origin are as follows.

Table 3-1 Relative position of coordinate systems for Gemini 435Le

| Relative Position                 | X(mm) | Y(mm) | Z(mm)  |
| --------------------------------- | ----- | ----- | ------ |
| Origin of Depth coordinate system | 0     | 0     | 0      |
| Origin of Color coordinate system | 23.75 | 0     | 0      |
| Origin of IMU coordinate system   | 15.48 | 0     | -55.60 |

Table 4-8-3 Gemini 435Le Coordinate System Position Reference

| Camera       | Coordinate System                                                                                                                                                   | Position in the 3D camera coordinate system / X（mm）                                                                                                                 | Position in the 3D camera coordinate system / Y（mm）                                                                                                                 | Position in the 3D camera coordinate system / Z(mm)                                                                                                                 |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gemini 435Le | Mounting hole                                                                                                                                                       | 0                                                                                                                                                                   | 0                                                                                                                                                                   | 0                                                                                                                                                                   |
| Gemini 435Le | Depth                                                                                                                                                               | -81.41                                                                                                                                                              | -20.20                                                                                                                                                              | 36.01                                                                                                                                                               |
| Gemini 435Le | Color                                                                                                                                                               | -57.66                                                                                                                                                              | -20.20                                                                                                                                                              | 36.01                                                                                                                                                               |
| Gemini 435Le | IMU                                                                                                                                                                 | -65.93                                                                                                                                                              | -20.20                                                                                                                                                              | -19.59                                                                                                                                                              |
| Gemini 435Le | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/2dWimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/2dWimage.png) | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/2dWimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/2dWimage.png) | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/uZ7image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/uZ7image.png) | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-12/scaled-1680-/uZ7image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-12/uZ7image.png) |

#### Update Firmware (Gemini 330 Series) <a href="#update-firmware-gemini-330-series" id="update-firmware-gemini-330-series"></a>

_Reviewed source:_ [_Update Firmware (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Update%20Firmware%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.

This is an inherited Gemini 330 tool-workflow chapter. It does not identify a valid Gemini 435Le firmware image; use the separately linked 435Le firmware release resources.
{% endhint %}

#### 1. Device Firmware Mode Introduction <a href="#id-1.-device-firmware-mode-introduction" id="id-1.-device-firmware-mode-introduction"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

The Gemini 330 series cameras have two modes. The first is normal mode, where the camera operates normally. The second is recovery mode, where the camera cannot function but can only perform a firmware update. By default, the device will enter normal mode. It will only enter recovery mode when it is unable to enter normal mode.

**1.1 How to Identify the Device Mode**

**1.1.1 Windows System**

In normal mode, the device manager displays the device as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/cfNBwZyR4s6uka6XYh89/image001%208.png)

In normal mode, the device is displayed as follows when connected to Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8v2FruXPEStbLwr3hiWA/image003%208%201024x239.png)

In recovery mode, the device manager displays the device as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/l3pKjB5BcaGnBxZtSgny/image005%207.png)

In recovery mode, the device is displayed as follows when connected to Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/cN9Pk1CuUXour1v7xKH4/image007%206.png)

**1.1.2 Ubuntu System**

In normal mode, the device information is displayed as follows when using the `**lsusb**` command:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Q4gDzGWwjXlJCV100ffF/image009%206.png)

In normal mode, the device is displayed as follows when connected to the Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/xIqKx0MhfpNvuLKtFlIF/image011.gif)

In recovery mode, the device information is displayed as follows when using the `**lsusb**` command:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nFagSKDzJk7vGtWu03T6/image013.gif)

In recovery mode, the device is displayed as follows when connected to the Orbbec Viewer:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/08QjTmloqETH1VJQnrF6/image015.gif)

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

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oZmRxZenLOFNoNVp5ICM/image017.gif)

2. Click the notification in the red box as shown above, and the following dialog box will appear.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/2SDdHpFg66umd9hO9JxQ/image019.gif)

3. Select "New Firmware Upgrade".

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/q8qU0ALKeH86gslSurDO/image021.gif)

4. Click "Upgrade," and the following dialog box will appear.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yPz8WjkoHxkMaMqUe5ED/image023.gif)

5. Click "Yes."

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Yz1LMkEQAr6pJY5HNpnB/image025.gif)

6. Reboot the device.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/dhRUU2OtRWk1Ojdgwvkp/image027.gif)

7. Confirm the firmware version number after the update.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/tquC0xak20RYivIu3O6a/image029.gif)

**Notes:**

If an update fails, preserve the error and first resolve power, connection and exact-image compatibility. Retry only through the model’s documented recovery workflow; do not repeatedly flash to diagnose an unidentified fault.

**2.2 Offline Update via Orbbec Viewer**

The difference between offline and online updates is as follows: With online updates, the firmware is automatically downloaded from the server (downloaded to the "output/firmwareFile" directory in Orbbec Viewer), and then the device is updated. However, with offline updates, you manually select the firmware path and then proceed with the update. The interface is as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/17CSA335rXe5DM12hrIT/image031.gif)

After clicking "Upgrade," the subsequent update steps are the same as the online update.

**2.3 Code Sample**

1. The firmware update reference for Orbbec SDK V1.x.x version is available in the sample at the following link: [https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade](https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade)
2. The firmware update reference for Orbbec SDK V2.x.x version is available in the sample at the following link: [https://github.com/orbbec/OrbbecSDK\_v2/tree/main/examples/2.device.firmware\_update](https://github.com/orbbec/OrbbecSDK_v2/tree/main/examples/2.device.firmware_update)

#### 3. Handle Update Exception <a href="#id-3.-handle-update-exception" id="id-3.-handle-update-exception"></a>

If there is a power failure or the USB cable is unplugged during the online update process, the device may enter Recovery mode. In this case, you will need to perform an offline update using the firmware downloaded online. The path to the online firmware download is in the "output/firmwareFile" directory of Orbbec Viewer, for example, on the Windows platform, as shown in the following figure.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/GHCKvolsdiIpx5ggpO7o/image033.gif)

If the device enters Recovery mode but there is no firmware available, please download the firmware from the product’s firmware download page first. Then, follow the offline update method to perform the update.

**Notes: (Very Important)**

In Recovery mode, ISP firmware update is not supported. You need to enter Normal mode and perform the firmware update again to ensure ISP firmware matches the current system. (In Recovery mode, firmware needs to be updated twice.)

#### 4. Update Orbbec Viewer <a href="#id-4.-update-orbbec-viewer" id="id-4.-update-orbbec-viewer"></a>

If there is a new version of Orbbec Viewer available for update, when opening Orbbec Viewer, there will be a prompt in the top right corner: "A new version of the tool can be updated." Click on this prompt, and it will link to the download directory of Orbbec Viewer on GitHub. Please download the corresponding platform’s Orbbec Viewer.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/2SqhhIuv0z7nPZ4VGhJM/image035.gif)

**Notes:**

Each firmware has a corresponding minimum version number of supported Orbbec Viewer. If the current Orbbec Viewer version is too low, you need to update Orbbec Viewer first to detect the prompt for the latest firmware update.

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

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/uiB7kXH5L9TMqT7xjIdi/image001.png)

2. Click "Next", and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5v7FPxUHBO6ou5o0dOuQ/image003.png)

3. Click "I Agree", and the following dialog box will pop up:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8nDC5gPsen20Dn7nSRxp/image005.png)

4. Click "Next" again:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/c190FW6unfZlO7ykhCGJ/image007.png)

5. Click "Install" and wait for the installation to complete.

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/vaRlemBDGHWUEPCmgvEW/image009.png)

6. After the installation, the files in the Orbbec SDK installation directory are as follows:

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/2aUPNmFCw0aJNhvKby3G/image011.png)

The Orbbec Viewer can be accessed via the desktop shortcut.

#### 2. Linux /Arm64 Installation Guidance <a href="#id-2.-linux-arm64-installation-guidance" id="id-2.-linux-arm64-installation-guidance"></a>

**2.1 Install via .deb Package**

.deb package download link: [https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

OrbbecSDK\_vx.x.x\_amd64.deb is the installation package for Linux x64, and OrbbecSDK\_vx.x.x\_arm64.deb is the installation package for Arm64.

1. On the Linux x64 (Ubuntu) platform, install using the following command:

sudo dpkg -i OrbbecSDK\_v1.x.x\_amd64.deb # Based on the actual version

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/A8GwwLnIZze0NVpUD8WD/image013.png)

2. Check the entire package path of the Orbbec SDK using `dpkg -L orbbecsdk`, while the header files and library files of the Orbbec SDK will be installed in the `/usr/local` path.

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Sgj6hN7FblfijRp4fEGN/image015.png)

3. Enter `OrbbecViewer` to run the Orbbec Viewer.

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Dso4knaBJT4JaspWOebq/image017.png)

**2.2 Install via Debian Apt Repository**

1. In the terminal, enter the following command to obtain and add the public key used for verification:

wget -O – [http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec\_sdk/pub\_key.pub](http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk/pub_key.pub) | sudo apt-key add –

* Check if the public key was added successfully by entering:apt-key list

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/T3Q2wJr6HSO5dhZkeo0H/image019.png)

If there is a problem with the host not resolving, try the following command to restart the system DNS resolution service and retry the first command:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
sudo systemctl restart systemd-resolved
```

2. In the terminal, enter the following command to add the apt source update address:

`echo "deb [http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk](http://s3.amazonaws.com/orbbec-debian-repos-aws/repos/orbbec_sdk) stable main" | sudo tee /etc/apt/sources.list.d/orbbec-orbbecsdk.list`

3. The following command can be used to query the Orbbec SDK:

`sudo apt update``sudo apt search orbbecsdk`

![Official Orbbec figure from Install Orbbec SDK](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zJWqYgrof6chdcF60t5M/image021.png)

4. Check the installation directory of the Orbbec SDK through `dpkg -L orbbecsdk`, and by entering the `OrbbecViewer` Command, you can run the Orbbec Viewer.

#### Programming fundamentals <a href="#programming-fundamentals" id="programming-fundamentals"></a>

_Reviewed source:_ [_Programming fundamentals_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Programming%20fundamentals)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.
{% endhint %}

#### 1. Get the First Orbbec Device <a href="#id-1.-get-the-first-orbbec-device" id="id-1.-get-the-first-orbbec-device"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Context ctx; auto devList = ctx.queryDeviceList(); auto dev = devList->getDevice(0);
```

#### 2. Start Streaming with Default Configuration <a href="#id-2.-start-streaming-with-default-configuration" id="id-2.-start-streaming-with-default-configuration"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; // create pipe with default device pipe.start(nullptr); // start with defualt configuratio
```

#### 3. Start Streaming Infrared Image <a href="#id-3.-start-streaming-infrared-image" id="id-3.-start-streaming-infrared-image"></a>

For TOF or Single-Camera structured light devices:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>(); auto irProfiles = pipe.getStreamProfileList(OB_SENSOR_IR); auto irProfile = irProfiles->getProfile(OB_PROFILE_DEFAULT); config->enableStream(irProfile); pipe.start(config);
```

For Dual-Camera structured light devices:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; std::shared_ptr<ob::Config> config = std::make_shared<ob::Config>(); auto irLeftProfiles = pipe.getStreamProfileList(OB_SENSOR_IR_LEFT); auto irLeftProfile = irLeftProfiles->getProfile(OB_PROFILE_DEFAULT); config->enableStream(irLeftProfile); auto irRightProfiles = pipe.getStreamProfileList(OB_SENSOR_IR_RIGHT); auto irRightProfile = irRightProfiles->getProfile(OB_PROFILE_DEFAULT); config->enableStream(irRightProfile); pipe.start(config);
```

#### 4. Wait for a Coherent Set of Frames <a href="#id-4.-wait-for-a-coherent-set-of-frames" id="id-4.-wait-for-a-coherent-set-of-frames"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; pipe.start(nullptr); auto frameSet = pipe.waitForFrames(100); auto depthFrame = frameSet->depthFrame();
```

#### 5. Do Processing on a Background-Thread <a href="#id-5.-do-processing-on-a-background-thread" id="id-5.-do-processing-on-a-background-thread"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
std::mutex frameQueueMtx; std::queue<std::shared_ptr<ob::Frame>> frameQueue; auto precessThread = std::thread([&](){ std::shared_ptr<ob::Frame> depthFrame; while(true{ { std::lock_guard<std::mutex> lk(frameQueueMtx); if(frameQueue.empty()){ std::this_thread::sleep_for(std::chrono::milliseconds(10)); continue; } depthFrame = frameQueue.front(); frameQueue.pop(); } auto depthFrameData = depthFrame->data(); // do some thing to process depth frame data; } }) ob::Pipeline pipe; pipe.start(nullptr); while(true){ auto frameSet = pipe.waitForFrames(100); auto depthFrame = frameSet->depthFrame(); if(depthFrame){ std::lock_guard<std::mutex> lk(frameQueueMtx); frameQueue.push(depthFrame) } }
```

#### 6. Get Depth-to-Color Extrinsics <a href="#id-6.-get-depth-to-color-extrinsics" id="id-6.-get-depth-to-color-extrinsics"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; auto depthProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH); auto depthProfile = depthProfiles->getProfile(OB_PROFILE_DEFAULT); auto colorProfiles = pipe.getStreamProfileList(OB_SENSOR_DEPTH); auto colorProfile = depthProfiles->getProfile(OB_PROFILE_DEFAULT); auto extrinsics = depthProfile->getExtrinsicTo(colorProfile);
```

#### 7. Get Video Stream Intrinsics <a href="#id-7.-get-video-stream-intrinsics" id="id-7.-get-video-stream-intrinsics"></a>

From pipeline:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; pipe.start(nullptr); // get camera intrinsic and extrinsic parameters form pipeline and set to point cloud filter auto cameraParam = pipeline.getCameraParam();
```

From Frame/StreamProfile (Gemini 300 series only):

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; pipe.start(nullptr); auto frameSet = pipe.waitForFrames(100); auto frame = frameSet->depthFrame(); auto streamProfile = frame->getStreamProfile(); auto videoStreamProfile = streamProfile->as<ob::VideoStreamProfile>(); auto intrinsic = videoStreamProfile->getIntrinsic();
```

#### 8. Get Depth Units <a href="#id-8.-get-depth-units" id="id-8.-get-depth-units"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; pipe.start(nullptr); auto frameSet = pipe.waitForFrames(100); auto depthFrame = frameSet->depthFrame(); auto uint = depthFrame->getValueScale();
```

#### 9. Controll the Laser <a href="#id-9.-controll-the-laser" id="id-9.-controll-the-laser"></a>

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
ob::Pipeline pipe; auto dev = pipe->getDevice(); // Laser control (for Gemini 300 series) dev->setIntProperty(OB_PROP_LASER_CONTROL_INT, 1); // 0: off, 1: on, 2: auto // Turn on/off laser (for other series) dev->setBoolProperty(OB_PROP_LASER_BOOL, true); // Laser energy level control dev->setIntProperty(OB_PROP_LASER_ENERGY_LEVEL_INT, 2);
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
/** * @brief check if the frame contains the specified metadata * * @param[in] frame frame object * @param[in] type metadata type, refer to @ref ob_frame_metadata_type * @param[out] error Log error messages */ bool ob_frame_has_metadata(ob_frame *frame, ob_frame_metadata_type type, ob_error **error); /** * @brief Get the metadata value of the frame * * @param[in] frame frame object * @param[in] type metadata type, refer to @ref ob_frame_metadata_type * @param[out] error Log error messages * @return int64_t return the metadata value of the frame */ int64_t ob_frame_get_metadata_value(ob_frame *frame, ob_frame_metadata_type type, ob_error **error);
```

C++:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Member functions of class ob::Frame /** * @brief Check if the frame object has metadata of a given type. * * @param type The metadata type. refer to @ref OBFrameMetadataType * @return bool The result. */ bool hasMetadata(OBFrameMetadataType type); /** * @brief Get the metadata value * * @param type The metadata type. refer to @ref OBFrameMetadataType * @return int64_t The metadata value. */ int64_t getMetadataValue(OBFrameMetadataType type);
```

#### 2. Example <a href="#id-2.-example" id="id-2.-example"></a>

The envisaged mode of querying metadata attribute is `check-then-query`

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
const char *metaDataTypes[] = { "TIMESTAMP", "SENSOR_TIMESTAMP","FRAME_NUMBER", "AUTO_EXPOSURE", "EXPOSURE", "GAIN", "AUTO_WHITE_BALANCE", "WHITE_BALANCE", "BRIGHTNESS", "CONTRAST", "SATURATION", "SHARPNESS", "BACKLIGHT_COMPENSATION", "HUE", "GAMMA", "POWER_LINE_FREQUENCY", "LOW_LIGHT_COMPENSATION", "MANUAL_WHITE_BALANCE", "ACTUAL_FRAME_RATE", "FRAME_RATE", "AE_ROI_LEFT", "AE_ROI_TOP", "AE_ROI_RIGHT", "AE_ROI_BOTTOM", "EXPOSURE_PRIORITY", "HDR_SEQUENCE_NAME", "HDR_SEQUENCE_SIZE", "HDR_SEQUENCE_INDEX", "LASER_POWER", "LASER_POWER_MODE", "EMITTER_MODE", "GPIO_INPUT_DATA" }; ob::Pipeline pipe; pipe.start(nullptr); auto frameSet = pipe.waitForFrames(100); auto colorFrame = frameSet->ColorFrame(); for(int metaDataType = 0; metaDataType < OB_FRAME_METADATA_TYPE_COUNT; metaDataType++) { // Check if it is supported metaDataType for current frame if(colorFrame->hasMetadata((OBFrameMetadataType)metaDataType)) { // Get the value of the metadata auto value = colorFrame->getMetadataValue((OBFrameMetadataType)metaDataType) std::cout << metaDataTypes[metaDataType] << ": " << value << std::endl; } else { std::cout << metaDataTypes[metaDataType] << ": " << "unsupported" << std::endl; } }
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

#### Gemini 435Le Supported Hosts and System Requirements <a href="#gemini-435le-supported-hosts-and-system-requirements" id="gemini-435le-supported-hosts-and-system-requirements"></a>

_Reviewed source:_ [_Gemini 435Le Supported Hosts and System Requirements_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Gemini%20435Le%20Supported%20Hosts%20and%20System%20Requirements)_. Manufacturer figures and source examples retain their original attribution and rights._

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
* Data Interface: Gigabit Ethernet
* Processor: Quad-core, 2.9GHz and above
* RAM: 8GB and above

**Recommended configuration for ARM-based hosts**

* Operating systems: Ubuntu 18.04/20.04/22.04
* Data Interface: Gigabit Ethernet
* Processors: Quad-core Cortex-A57 and above
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

| ARM Platform             | Software Version                  | Test Result |
| ------------------------ | --------------------------------- | ----------- |
| NVIDIA Jetson Orin Nano  | Last Tested on JetPack5.1.1-b56   | PASS        |
| NVIDIA Jetson Orin NX    | Last Tested on JetPack5.1.1-b56   | PASS        |
| NVIDIA Jetson AGX Orin   | Last Tested on JetPack 6.0        | PASS        |
| NVIDIA Jetson Nano       | Last Tested on JetPack 4.6.1-b110 | PASS        |
| NVIDIA Jetson AGX Xavier | Last Tested on JetPack 5.0.2-b231 | PASS        |
| NVIDIA Jetson Xavier NX  | Last Tested on JetPack 4.6.1-b110 | PASS        |

#### Official Gemini 435Le Datasheet <a href="#official-gemini-435le-datasheet" id="official-gemini-435le-datasheet"></a>

_Reviewed source:_ [_Orbbec-Gemini-435Le-Datasheet-V1.pdf_](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

The following hardware chapters retain the Gemini 435Le V1.0 specification and its test conditions. The core guide names the 9–24 V/≥2 A DC requirement and unresolved trigger/connector discrepancies. [Full dated datasheet,including mechanical and cable drawings](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf).

#### 1 Product Brief <a href="#id-1-product-brief" id="id-1-product-brief"></a>

_Reviewed source:_ [_Orbbec-Gemini-435Le-Datasheet-V1.pdf_](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

The Gemini 435Le is the newest addition to Orbbec's 3D camera family. Building upon the exceptional depth-sensing capabilities of the Gemini 435L, it further expands the application boundaries for robotics. Designed with industrial-grade hardware and featuring high-reliability interfaces with IP67-rated protection, this product meets the demands of even the most challenging industrial environments. Its powerful 3D vision system delivers high-precision, real-time depth data for logistics robots and large outdoor robotic systems, ensuring stable and reliable operation in complex scenarios such as logistics sorting robotic arms, intelligent forklifts, and outdoor autonomous mobile robots (AMRs). The Gemini 435Le utilizes standard network communication protocols for rapid multi-platform deployment and offers the following key advantages:

* Active/Passive Stereo Vision: Adapts to dynamic environments with stable and reliable

depth perception

* High-Precision Depth Measurement: Achieves spatial relative accuracy better than

0.4% at 2m range

* Wide Field of View: 90° (H) × 65° (V) for broader coverage
* All-Environment Operation: IP67-rated for reliable indoor/outdoor performance
* Industrial-Grade Reliability: Complies with stringent industrial certification standards
* Long-Distance Stable Transmission: Supports PoE power delivery and 100m cable

transmission for flexible deployment

* Multi-Camera Synchronization: Enables hardware synchronization and RS485

communication for cluster operations

* Robust Industrial Connectivity: High-reliability interfaces ensure stable data

transmission

#### 2 Product Specifications <a href="#id-2-product-specifications" id="id-2-product-specifications"></a>

_Reviewed source:_ [_Orbbec-Gemini-435Le-Datasheet-V1.pdf_](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

Parameter Gemini 435Le Use Environment Indoor & Outdoor Technology Stereo Vision Baseline 95mm LDM Wavelength 850nm Working Range\[1] 0.31 -20m+ Ideal Range \[2]

#### 0.31 - 10m <a href="#id-0.31-10m" id="id-0.31-10m"></a>

Spatial Precision \[3] ≤ 0.4% (1280 x 800 @ 2 m & 90% x 90% ROI) ≤ 0.8% (1280 x 800 @ 4 m & 80% x 80% ROI) Depth Resolution @ Frame Rate Up to 1280 x 800 @ 10fps 640 x 400 @ 20fps Depth FOV 90° x 65° ± 3° @ 2m (1280 x 800) Depth Filter Visible + NIR-Pass Sensor Type IR: Global Shutter Color: Global Shutter RGB Resolution @ Frame Rate Up to 1280 x 800 @ 10fps MJPEG/I420 640 x 400 @ 20fps MJPEG/I420 RGB FOV Aspect ratio 16:10 94° x 68° ± 3° Aspect ratio 16:9 94° x 62° ± 3° Aspect ratio 4:3 82° x 66° ± 3° Depth confidence map Supported IMU 6 DoF; Gyroscope/Accelerometer Sample range: 50 - 1,000Hz Data Connection Gigabit Ethernet Network Protocol TCP/IP, RTSP Interface M12, 8-pin, X-coded connector for data transmission and POE M12, 8-pin, A-coded connector for DC Power in, Sync in/out and RS485 Power Supply POE: IEEE 802.3af DC: ≥2A @ 9V - 24V HDR Depth To be supported in subsequent software upgrades

ESD Class A Contact discharge: ±8kV, Air discharge: ±15kV RE ≥6 dB Power Consumption DC: Average < 6.5W (Peak < 11.0W) PoE: Average < 8.0W (Peak < 15W) Operating Environment -10℃ - 50℃ 5% \~ 90 % RH (non-condensing) Storage Environment Short Term: -20℃ - 70℃, 5%\~90% RH (non-condensing) Long Term: 0℃ - 60℃, 5%\~90% RH (non-condensing) Operating BacksideCase Temperature -10℃ - 65℃ Protection IP67 Supported Functions Hardware Spatial Alignment of Depth to Color Hardware Timestamps, Multi-camera Sync RS485 Dimensions 138.5mm x 40.5mm x 70.0mm Weight 520g Installation Back：4x M4, Max Torque: 0.4 N.m, Max Insertion Depth: 6mm Bottom：4x M4, Max Torque: 0.4 N.m, Max Insertion Depth: 6mm Top：4x M4, Max Torque: 0.4 N.m, Max Insertion Depth: 6mm \[1] Measure object reflectivity > 10%, up to 20m distance depth data. Theoretical maximum depth ranges up to 65 meters, but the actual accuracy varies with the distance and the object to be measured. \[2] The minimum operating distance may vary depending on different offset configurations and Preset configurations. For specific details, please refer to the detailed specifications in Table 4-7-1. \[3] The depth performance of each 3D camera is validated at the production line before shipping to customers. The metrics reflect the depth performance under typical conditions. External impact factors over 3D cameras’ whole lifespan may have significant impacts on their depth performance. For more detailed depth performance metrics, please refer to section 5.1.2.

#### 3 Product Information <a href="#id-3-product-information" id="id-3-product-information"></a>

_Reviewed source:_ [_Orbbec-Gemini-435Le-Datasheet-V1.pdf_](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 3.1 Product Pictures <a href="#id-3.1-product-pictures" id="id-3.1-product-pictures"></a>

Table 3-1-1 Product pictures for Gemini 435Le Front View Back View Top View Bottom View Left View Right View

#### 3.2 Product Dimensions & Weight & Drawings <a href="#id-3.2-product-dimensions-and-weight-and-drawings" id="id-3.2-product-dimensions-and-weight-and-drawings"></a>

**3.2.1 Product Dimensions & Weight for Gemini 435Le**

Table 3-2-1 Product dimensions & weight for Gemini 435Le Name Gemini 435Le Width/mm 138.5 Height/mm 40.5 Depth/mm 70 N.W/g 520

**3.2.2 Product Drawings for Gemini 435Le**

Table 3-2-2 Product drawings for Gemini 435Le Name Gemini 435Le Front View Top View Bottom View Left View Right View

#### 3.3 Product Interfaces <a href="#id-3.3-product-interfaces" id="id-3.3-product-interfaces"></a>

Table 3-3 Product interfaces for Gemini 435Le Interfaces DC power in & sync in/out & RS485 Data & PoE Connector M12 A-coded M12 X-coded Illustration

**3.3.1 Ethernet M12 connector, X-coded, Female**

The Ethernet interface provides configuration access to the camera and is also used for image data transmission. Table 3-3-1 M12 Connector PIN Definition M12 PIN Description PIN Layout 1 Bi-directional pair A+ 2 Bi-directional pair A- 3 Bi-directional pair B+ 4 Bi-directional pair B- 5 Bi-directional pair D+ 6 Bi-directional pair D- 7 Bi-directional pair C- 8 Bi-directional pair C+ Rear View M12 A-coded M12 X-coded

**3.3.2 Power M12 connector, A-coded, Male**

Beside the Ethernet interface for communication and data transmission, Gemini 435Le cameras is equipped with M12 connector providing I/O-interface and power input. Table 3-3-2 M12 Connector PIN Definition M8 PIN Description PIN Layout 1 POWER IN 9-24V 2 VSYNC VCC 3.3-24V 3 VSYNC IN 3.3-24V 4 VSYNC OUT 3.3-24V 5 SIGNAL GND 6 RS485B 7 RS485A 8 POWER GND

#### 3.4 Product Components <a href="#id-3.4-product-components" id="id-3.4-product-components"></a>

**3.4.1 Overview of Product Components for Gemini 435Le**

Table 3-4-1 Overview of product components for Gemini 435Le Name Gemini 435Le Overview

**3.4.3 Laser Diode Module**

The laser module (LDM) comprises an array of vertical cavity surface emitting lasers and other optic components. It enhances the depth camera system's ability to detect depth information by projecting static infrared patterns onto the scene, adding texture to low-texture scenes. The Gemini 435Le laser module is a Class 1 Laser Product under normal conditions. Table 3-4-3 LDM parameters LDM Gemini 435Le Type Infrared Component Vertical Cavity Surface Laser Emitter (VCSEL) + Optics Laser Controller Pulse Wavelength 850nm ± 6nm Laser Compliance\_ Class 1, IEC 60825-1:2007 Edition 2, IEC 60825-1:2014 Edition 3 FDA number: 2420619-000 Laser Power-down Temperature\_ 73℃ Horizontal FOV 101° Vertical FOV 72.5° FOV tolerance ±3.0°

> Note: \* LDM is considered Class 1 when integrated into Orbbec‘s 3D Cameras.

* LDM will power down while the NTC tested temperature is ≥73℃.

**3.4.4 Infrared Module**

Table 3-4-4 Infrared module parameters IR Module Gemini 435Le Filter Type Visible + NIR-pass Filter Active Pixels 1280 x 800 Sensor Aspect Ratio 16:10 Focus Type Fixed Shutter Type Global Shutter Horizontal FOV 94° Vertical FOV 68° Diagonal FOV 104° FOV tolerance ±3.0° Distortion <1.5%

**3.4.5 RGB Module**

Table 3-4-5 RGB module parameters RGB Module Gemini 435Le Filter Type IR-cut Active Pixels 1280 x 800 Sensor Aspect Ratio 16:10 Focus Type Fixed Shutter Type Global Shutter Horizontal FOV 94° Vertical FOV 68° Diagonal FOV 104° FOV tolerance ±3.0° Distortion <1.5%

**3.4.6 Laser Ranging Module**

The Gemini 435Le 3D cameras come equipped with a single-point laser ranging module (LRM). Essentially, it is a single-point dToF (direct time-of-flight) sensor that calculates relative distance by measuring the time it takes for light to travel from emission to reception. It is used for close-range ranging, helping the 3D camera to fill in blind spots at short distances and enhances the overall ranging performance of the depth camera. Table 3-4-6a LRM parameters Parameters Gemini 435Le Type Infrared Wavelength 940nm（typical value） Projector DFOV 19° Receiving DFOV 37° FOV tolerance ±2.0° Table 3-4-6b Gemini 435Le LRM Ranging Accuracy Reference Value Distance Value Unit LRM Accuracy 1mm — 100mm ±15 mm 100mm — 200mm ±10 mm 200 mm — 400mm ±5% N/A

Table 3-4-6c LRM Ranging FOV Name Gemini 435Le Rear View Side View

**3.4.7 Transmittance vs. Wavelength for Depth Camera**

Figure 3-4-7 Transmittance vs. Wavelength for Depth Camera

**3.4.8 IMU**

Table 3-4-8 Gemini 435Le IMU Specifications Timestamp Unit us (the same hardware clock is utilized for IMU, IR, RGB and Depth streams) Transmittance Protocol I2C X/Y/Z Axis The X, Y, and Z axis point right, downward, and forward relative to the camera front Gyroscope Format 3 x 16-bit Range ±17.45 rad/s (1000dps) Frequency (Hz) 50/100/200/500/1000 Accelerometer Format 3 x 16-bit Range ± 39.2m/s² (4g) Frequency (Hz) 50/100/200/500/1000 Temperature Format 1 x 16-bit Range -40 \~ 85℃ Frequency (Hz) Follows the gyroscope and accelerometer frequency

#### 4 Functional Specifications <a href="#id-4-functional-specifications" id="id-4-functional-specifications"></a>

_Reviewed source:_ [_Orbbec-Gemini-435Le-Datasheet-V1.pdf_](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 4.1 Vendor Identifier (VID) and Product Identifier (PID) <a href="#id-4.1-vendor-identifier-vid-and-product-identifier-pid" id="id-4.1-vendor-identifier-vid-and-product-identifier-pid"></a>

Table 4-1-1 VID & PID table Name Model VID PID Gemini 435Le G30056-370 0x2BC5 0x0815

#### 4.2 Platform and System Requirements <a href="#id-4.2-platform-and-system-requirements" id="id-4.2-platform-and-system-requirements"></a>

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

Gemini 435Le connect to the host computer using Ethernet, which is compatible with various platforms and system requirements. Table 4-2-1 Gemini 435Le Recommended Platforms and Systems Chip x86/x64 ARM OS Windows 10/11 Ubuntu 20.04 / 22.04 Ubuntu 20.04 / 22.04 Ethernet Gigabit Ethernet Gigabit Ethernet Gigabit Ethernet CPU Quad-core, 2.9GHz Quad-core, 2.9GHz Quad-core, A57 Reference model Intel i7 10700 Intel i7 10700 NVIDIA AGX Orin/Orin NX/Orin Nano Network adapters Intel ® Ethernet Controller (11) I219-LM Intel ® corporation Ethernet connection（14） I219-LM（rev 11） RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller（rev 15） RAM 8GB RAM and above 4GB RAM and above 8GB RAM and above

#### 4.3 Camera system Framework <a href="#id-4.3-camera-system-framework" id="id-4.3-camera-system-framework"></a>

Figure 4-3-1 Gemini 435Le System Framework Diagram

#### 4.4 Image Data Stream <a href="#id-4.4-image-data-stream" id="id-4.4-image-data-stream"></a>

The Gemini 435Le delivers high-quality, multi-resolution depth and IR streams alongside HD color video streams. The camera outputs depth data in Y16 or RVL format, color images in I420 or MJPEG format, and IR images in Y8 format. The software SDK additionally supports RGB/BGR/BGRA formats for color streams. Table 4-4-1 Output data streams (Gigabit Ethernet)-Gemini 435Le Gemini 435Le (Gigabit Ethernet) Data Format Aspect Ratio Resolution Frame Rate Depth Y16 16:10 1280 x 800 5,10 640 x 400 5,10,15,20 RVL 16:10 1280 x 800 5,10 640 x 400 5,10,15,20 IR Y8 16:10 1280 x 800 5,10,15,20 640 x 400 5,10,15,20 Color I420 16:10 1280 x 800 5,10,15,20 640 x 400 5,10,15,20 16:9 1280 x 720 5,10,15,20 640 x 360 5,10,15,20 4:3 800 x 600 5,10,15,20 MJPEG 16:10 1280 x 800 5,10,15,20 640 x 400 5,10,15,20 16:9 1280 x 720 5,10,15,20 640 x 360 5,10,15,20 4:3 800 x 600 5,10,15,20

> Note: A single data stream output can support all resolutions and frame rates. However, when

simultaneously outputting two, three, or four streams of depth and color stream, some combinations may not be supported due to the actual bandwidth limitations of camera’s Gigabit or Fast Ethernet and the performance of the host device.

#### 4.5 Field of View <a href="#id-4.5-field-of-view" id="id-4.5-field-of-view"></a>

**4.5.1 Definition of Depth Field of View**

The image below shows the depth camera field-of-view, or the angles that the sensors "see". We use the IR cameras for illustration. Figure 4-5-1 Depth Field of View to Depth Map illustration Depth Field of View (Depth FOV) at any depth (Z) can be calculated using the following equation: Table 4-5-1 Depth FOV calculation formulas Calculation formulas Definitions fx cxwidth Z B fx cx        1arctanarctanFOVHDepth 1. cx = X-direction image coordinates of the principle point of the depth image 2. fx= Depth camera focal length 3. cy= Y-direction image coordinates of the principle point of the depth image 4. fy=Depth camera focal length 5. width= Depth image width 6. Height=Depth image height 7. Depth active H-FOV =Left IR H-FOV fx cxwidth fx cx  1arctanarctanFoVH ActiveDepth )tan(\*2 B FOVH ActiveDepth Z  fy -cyheight- fy c 1arctanyarctanFOV-VDepth      

> Note:

1. cx, fx, and width parameters are obtained through the SDK Depth Intrinsic for the relevant camera parameters, and each depth camera parameters are not the same. 2. At different depth values, the depth FOV is different. The farther the depth, the greater the depth FOV.

**4.5.2 Typical Depth Intrinsics**

Table 4-5-2 Typical Depth Intrinsics of Gemini 435Le Baseline Resolution：Width x Height cx/pixel cy /pixel Fx & fy/pixel Width/pixel Height/pixel 95mm 1280 800 640 400 620.0 & 620.0 640 400 320 200 310.0 & 310.0

**4.5.3 Overview of Stream FOV**

Table 4-5-3 Stream FOV for Gemini 435Le FOV Image ratio Gemini 435Le Depth @ 2m 16:10 H 90° V 65° 4:3 H 81° V 65° IR 16:10 H 91° V 65° 4:3 H 81° V 65° RGB 16:10 H 94° V 68° 16:9 H 94° V 62° 4:3 H 82° V 68° D2C FOV @ 2m 16:10 H 90° V 65° 16:9 H 90° V 60° 4:3 H 81° V 65°

**4.5.4 FOV Illustrations for Gemini 435Le**

Table 4-5-4 Gemini 435Le Depth FOV Aspect ratio Depth FoV Before D2C Depth FOV After D2C 16:10 16:9 N/A 4:3

#### 4.6 Depth to Color Alignment <a href="#id-4.6-depth-to-color-alignment" id="id-4.6-depth-to-color-alignment"></a>

Depth to Color, a pixel-by-pixel geometric transformation of a depth image, results in the spatial alignment of a depth image with its corresponding color image through the D2C transformation, allowing us to locate any pixel of a color image by its image coordinates in the depth image after D2C by the same image coordinates. The depth information of the color pixel can be located in the depth image after D2C by using the same image coordinates. We generate a depth image of the same size as the target color image after D2C, and the image content is the depth data in the color camera coordinate system. In other words, a depth image is reconstructed that is "taken" using the origin and size of the color camera, where each pixel matches the coordinates of the corresponding pixel of the color camera. Table 4-6-1 Gemini 435Le Depth to Color Alignment by software Depth Image before D2C Color Image Depth Image After D2C Aspect Ratio 1280 x 800/640 x 400 1280 x 800 1280 x 800 16:10 640 x 400 640 x 400 1280 x 800/640 x 400 1280 x 720 1280 x 720 16:9 640 x 360 640 x 360 1280 x 800/640 x 400 640 x 480 640 x 480 4:3 Table 4-6-2 Gemini 435Le Depth to Color Alignment by hardware Pre-D2C Depth Image Color Image Post D2C Depth Image Aspect Ratio 1280 x 800/640 x 400 1280 x 800 1280 x 800 4:3 640 x 400 640 x 400 1280 x 800/640 x 400 1280 x 720 1280 x 720 16：10 640 x 360 640 x 360 1280 x 800/640 x 400 640 x 480 640 x 480 16：9

#### 4.7 Minimum-Z Depth <a href="#id-4.7-minimum-z-depth" id="id-4.7-minimum-z-depth"></a>

The minimum working distance of a depth camera refers to the closest detectable planar distance from the camera’s depth origin. This distance is determined by the disparity search range and image resolution. The Gemini 435Le adjusts its minimum working distance by configuring depth offset values. The achievable minimum distance may also vary across different Preset modes. The camera provides flexible configuration options to adapt to diverse application needs. Table 4-7-1 Minimum-Z Depth for Gemini 435Le Camera Gemini 435Le Perset Resolution offset Max（mm） Min（mm） Perception 1280 x 800 0 ∞ 310 32 1855 266 640 x 400 0 ∞ 155 32 928 133 Dimensioning 640 x 480 0 ∞ 310 64 928 233 128 463 187

#### 4.8 Coordinate System <a href="#id-4.8-coordinate-system" id="id-4.8-coordinate-system"></a>

The Gemini 435Le 3D camera defines its coordinate systems as follows: The label surface is the bottom, the glass cover is the front, and the RGB module's direction relative to the LDM module is left. The IMU coordinate origin aligns with the sensor's physical center behind the RGB module, with +X right, +Y down, and +Z forward. The depth image origin is at the left IR module's optical center, while the color image origin is at the RGB module's optical center, both sharing the same axis orientation. The depth camera origin (0,0,0) serves as the default reference point, with the world coordinate system recommended to use the rear left mounting hole center. Reference positions for all origins are provided in accompanying diagrams. Table 4-8-1 Gemini 435Le Coordinate System Position Reference Camera Coordinate System Position in the 3D camera coordinate system X（mm） Y（mm） Z(mm) Gemini 435Le Depth 0 0 0 Color 23.75 0 0 IMU 15.48 0 -55.60

> Note: If the alignment of the depth and color cameras is enabled, the origin of the depth coordinate

system will automatically switch to the origin of the color coordinate system, and the intrinsics will also change accordingly.

Table 4-8-2 Gemini 435Le Coordinate System Schematic Gemini 435Le IMU Depth RGB

The relative coordinate system relationship between the installation positions and Depth/Color/IMU of Gemini 435Le. Table 4-8-3 Gemini 435Le Coordinate System Position Reference Camera Coordinate System Position in the 3D camera coordinate system X（mm） Y（mm） Z(mm) Gemini 435Le Mounting hole 0 0 0 Depth -81.41 -20.20 36.01 Color -57.66 -20.20 36.01 IMU -65.93 -20.20 -19.59 Note：All reference points are at the centers of the components or positions.

#### 4.9 Camera Start Point Reference <a href="#id-4.9-camera-start-point-reference" id="id-4.9-camera-start-point-reference"></a>

The camera start point, or ground zero datum can be described as a start point or plane with depth = 0. For the Gemini 435Le 3D camera, the distance of the depth/RGB/LRM zero point relative to the front cover glass of the camera are listed in the table below. Table 4-9-1 Camera Start Point Illustrations Position Camera Start Point（Z'） Illustrations Depth 4.040mm RGB 4.040mm LRM 0mm

#### 4.10 Streaming Mode <a href="#id-4.10-streaming-mode" id="id-4.10-streaming-mode"></a>

The Gemini 435Le offers flexible methods for acquiring IR, Depth, and RGB image data, with the streaming mode being the most common approach. In this mode, users configure the target frame rate, resolution, and image format for each data type before sequentially activating the corresponding streams. The camera then captures and outputs image data according to these user-defined parameters. Users can select specific frame rates (5fps, 10fps, 15fps, or 20fps) from predefined options based on the camera's current depth mode and resolution configuration, then acquire image data at the chosen rate.

#### 4.11 Triggering Mode <a href="#id-4.11-triggering-mode" id="id-4.11-triggering-mode"></a>

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

The Gemini 435Le supports a free-running trigger mode with configurable frequency parameters. In this operational mode, the camera remains in standby state until receiving valid external trigger signals that meet configuration requirements. Each triggered acquisition cycle completes before the system resets for subsequent triggers. 1. Flexible Timing Control: 1) No fixed interval required between consecutive triggers. 2) Minimum requirement: Trigger interval > single acquisition cycle duration 2. Trigger Sources: 1) Software triggers via network commands (host-initiated). 2) Hardware triggers through M12 A-coded sync interface 3. Frame Rate Configuration: 1) Mandatory unified frame rate setting for all streams (IR/Depth/RGB). 2) Available frame rates: 5/10/15/20 fps (fixed). 3) Minimum trigger interval must be preconfigured 4. Frequency Limitations: 1) See Table 4-11-1 for correlations between(Fixed frame rates/Minimum trigger intervals/Maximum allowable trigger frequencies). 2) The camera only processes triggers within validated frequency ranges This passive acquisition architecture enables adaptive triggering at any frequency within operational constraints while ensuring system stability. Table 4-11-1 Table of Arbitrary Frame Rates Allowed to be Passively Triggered Set The Camera’s Fixed Frame Rate(fps) Supportable Passive Trigger Interval (ms) Supportable Passive Trigger Frequency (Hz) 20 ≥100 0 - 10 15 ≥ 133.4 0 - 7.5 10 ≥200 0 – 5 5 ≥ 400 0 – 2.5

#### 4.12 Multi-camera Synchronization <a href="#id-4.12-multi-camera-synchronization" id="id-4.12-multi-camera-synchronization"></a>

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

For a multi-camera use case, one camera can be initialized as primary, and the rest configured as secondary. Alternatively, an external signal generator can also be used as the primary trigger with all cameras set to secondary mode. When applying an external sync pulse, the HW SYNC input requires a 100-microsecond positive pulse at the nominal camera frame rate, e.g. 50 ms for a 20 Hz frame rate. Inputs are high impedance,3.3V CMOS voltage levels. However, it is important to make sure to use a high-resolution signal generator. The frequency of the signal generator needs to exactly match the sensor frame rate. For example, if the sensor is set up as 20 FPS, the real frame rate may be 20.015 FPS. You may need to use an oscilloscope to measure the real frame rate and configure the signal generator to the same frequency. For this reason, it may be better to just use one additional camera as the primary sync signal generator. Advantages of multi-camera setup： o Increase camera coverage in a given space and fill in the occlusions where a single camera may have blind spots o Capture multiple images of the same scene and scan objects from different angles o Increase the effective frame rate to greater than 30 FPS Using an 8-pin connector and matching cable, a multi-camera and multi-sensor network can be designed. (Please follow the instructions in the SDK). Multi-camera frame synchronization in two topologies is supported, including depth image synchronization and RGB image synchronization (time difference ≤ 5ms, when auto exposure off), using the multi-camera synchronization function. Table 4-12-1 Topologies schematic diagram Star Topology Daisy-chain Topology

Table 4-12-2 Synchronization Interfaces of Gemini 435Le M8 Connector Definitions Description Pin\_2 SIGNAL VCC When SYNC\_VCC is not connected to an external power source, VSYNC\_OUT defaults to a 3.3V logic level. To achieve different voltage domains for VSYNC\_OUT, a target voltage between 3.3V and 24V can be supplied to the SYNC\_VCC input. Pin\_3 VSYNC\_IN The synchronization trigger signal (from upstream devices) supports 3.3V to 24V level input, with rising-edge triggering and a minimum pulse duration of 1ms. Pin\_4 VSYNC\_OUT Synchronous trigger signal: Active high. The high level provides the triggering signal for the secondary devices. Pin\_5 SIGNAL GND Ground Table 4-12-3 Gemini 435Le Multi-camera Synchronization Pin Placement Multi-camera Sync interface Illustration Detailed operating instructions for multi-camera synchronization, please refer the document of Set up cameras for external synchronization PIN 2 to PIN5 of M8 connector are for multi-camera sync interface

#### 4.13 Camera Functions <a href="#id-4.13-camera-functions" id="id-4.13-camera-functions"></a>

**4.13.1 Depth Camera Functions**

Gemini 435Le expose the following Depth image settings. Table 4-13-1 Depth camera control Control Description Settings Default Setting Mirror Image mirror is an image processing technique that creates a symmetrical effect by flipping the image along a specific axis (usually vertical or horizontal). Disable, Enable Enable Flip Inverting images or data, such as flipping an image horizontally or vertically. Disable, Enable Enable Rotate Turning an image by a specific angle. 0°,90°,180°,270° 0° Laser Power Level 0,1,2,3,4,5,6 6 Laser Control Laser control on or off Laser On, Laser Off On Auto Exposure Auto Exposure Mode. When Auto Exposure is enabled, Exposure and Gain are set based on the environment condition. Disable, Enable Enable AE Max Exposure(us) AE Max Exposure 1 - 199000 60616 (15fps) Mean Intensity Set Point Mean Intensity Set Point for Gemini 0 - 255 60 AE ROI Perform Auto Exposure on a selected ROI T:0 - 799, B:0 -799 L:0 - 1279, R:0 -1279 (Resolution:1280 x 800) T:0, B:399 L:0, R:639 (Resolution: 640 x 400) Manual Exposure (1) (us) Sets the absolute exposure time when auto-exposure is disabled 1 - 199000 3000 Gain(Gain 1.0=16) Control sensor digital gain 16 -248 16 Depth Unit(millimeter) Depth Measurement Standard Units 0.001 - 10 1 Disparity to Depth Disable, Hardware, Software Disable, Hardware, Software Hardware Post Processing post-processing filters to enhance the quality of depth data and reduce noise levels Disable, Enable Enable

> Note: (1) Not supported in Auto Exposure Mode

Definitions: T = Top, L = Left, B = Bottom, R = Right

**4.13.2 Color Camera Functions**

Gemini 435Le expose the following Color image settings. Table 4-13-2 Color camera control Control Description Settings Default setting Mirror Image mirror is an image processing technique that creates a symmetrical effect by flipping the image along a specific axis (usually vertical or horizontal). Disable, Enable Disable Fli Inverting images or data, such as flipping an image horizontally or vertically. Disable, Enable Disable Rotat Turning an image by a specific angle. 0°, 90°, 180°, 270° 0° Auto Exposure Priority Disable, Enable Enable Auto Exposure Automatically sets the exposure time and gain for the frame Disable, Enable Enable AE Max Exposure (100us) Maximum correction value for AE exposure that limits the corresponding frame rate 1 - 1999 665(15fps) AE ROI Perform Auto Exposure on a selected ROI T:0 - 779, B:0 -779 L:0 - 1279, R:0 -1279 (Resolution: 1280 x 800） T:0, B:399 L:0, R:639 (Resolution: 640 x 400） Manual Exposure (1) (100us) Sets the absolute exposure time when auto-exposure is disabled 1 - 33333 156 Gain Sets the amount of gain applied to the frame if auto-exposure is disabled 0 – 128 16 Brightness Sets the amount of brightness applied when auto-exposure is enabled -64 – 64 0 Auto White Balance Enables or disables the AWB algorithm Disable, Enable Disable White Balance/ K Sets the white balance when AWB is disabled 2800 – 6500 4600 Sharpness Sets the amount of sharpening adjustment applied to the frame 0 – 100 50 Saturation Sets the amount of saturation adjustment applied to the frame 0 - 100 64 Contrast Sets the amount of contrast based on the brightness of the scene 0 - 100 50 Hue Sets the amount of hue adjustment 0 – 100 0

applied to the frame Powerline Frequency Specified based on the local power line frequency for flicker avoidance Auto, 50, 60, Disabled Auto

> Note: (1) Not supported in Auto Exposure Mode

Definitions: T = Top, L = Left, B = Bottom, R = Right

#### 5 Performance <a href="#id-5-performance" id="id-5-performance"></a>

_Reviewed source:_ [_Orbbec-Gemini-435Le-Datasheet-V1.pdf_](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/06/04011158/Orbbec-Gemini-435Le-Datasheet-V1.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 5.1 Depth Performance <a href="#id-5.1-depth-performance" id="id-5.1-depth-performance"></a>

**5.1.1 Depth Quality Assessment**

Calculation of Depth Accuracy (Z-accuracy): Depth accuracy (Z-accuracy) refers to the difference between the depth of effective pixels on a fitted plane and the true value plane, which can be either positive or negative. Calculation method: Use a flat plate parallel to the x-axis of the module, and measure the distance with a laser rangefinder or tape measure as the Ground Truth (GT) surface. Collect the depth map at the current distance, and obtain the difference between the effective pixels in the ROI area and the true values to create an error map. Use the median of the error map as the Z-accuracy of the current depth map. To avoid errors from single measurements, take N depth maps and calculate the average or the ratio of the average to the true values as the final Z-accuracy. Calculation of Spatial Precision: The spatial precision is calculated as the percentage of the root mean square error (RMS Error) between each valid pixel and the optimal fitting plane compared to the true value (GT). Calculation of Temporal Precision: The temporal precision measures the variation in depth values over time within a ROI. The quality of a depth image can be assessed based on its temporal consistency, high-quality depth images should exhibit smooth and stable over time. This method is defined as the STD of depth values across a specific number of frames (for example, 30). The quantification of temporal noise is carried out on a per-pixel basis, followed by calculating the STD of each pixel over a specified time. Depth Fill Rate Calculation: The fill rate is used to calculate the proportion of valid pixels to total pixels within the target area (ROI region), primarily used to measure the completeness of depth. Detailed calculation principle can be found in document “Depth Quality Metrics”.

**5.1.2 Typical depth performance for Gemini 435Le**

Typical depth performance for Gemini 435Le is shown in the table below: Table 5-1-1 Typical Depth Performance for Gemini 435Le Depth Performance Gemini 435Le Depth Accuracy ≤±1% (1280 x 800 @ 2 m & 90% x 90% ROI) ≤±2% (1280 x 800 @ 4 m & 80% x 80% ROI) Spatial Precision ≤ 0.4% (1280 x 800 @ 2 m & 90% x 90% ROI) ≤ 0.8% (1280 x 800 @ 4 m & 80% x 80% ROI) Temporal Precision ≤ 0.1% @2m (1280 x 800) Fill Rate ≥99.5% (1280 x 800 @ 2 m & 90% x 90% ROI)

> Note:

1. The actual working range and accuracy may vary with the ambient illumination and the objects being measured. 2. The test object is a reflectivity > 80% plane, and the reference range is 81% FOV (81% FOV is the remaining center 81% of the depth map area after cropping 5% from the top, bottom, left and right of the depth map) or 64% FOV (64% = 80% x 80% and of a similar definition). 3. The depth performance of each 3D camera is validated at the production line before shipping to customers. The metrics reflect the depth performance under typical conditions. External impact factors over 3D cameras’ whole lifespan may have significant impacts on their depth performance.
2. Spatial Precision performance reference vs. Distance

Typical Depth performance reference of spatial precision for Gemini 435Le Figure 5-1-1 Spatial Precision chart of Gemini 435Le

* Temporal Precision performance reference vs. Time

Typical Depth performance reference of temporal precision for Gemini 435Le Figure 5-1-2 Temporal Precision chart of Gemini 435Le

* Fill Rate performance reference vs. Distance:

Typical Depth performance reference of fill rate for Gemini 435Le Figure 5-1-3 Fill Rate chart of Gemini 435Le

* Depth Accuracy performance reference vs. Distance

Typical Depth performance reference of Depth Accuracy for Gemini 435Le Figure 5-1-4 Depth Accuracy of Gemini 435Le

#### 5.2 Electrical Performance <a href="#id-5.2-electrical-performance" id="id-5.2-electrical-performance"></a>

{% hint style="info" %}
For DC operation use the datasheet’s 9–24 V input and supply capacity of at least 2 A. The quickstart’s older ≥1 A entry is superseded here by that model-specific requirement. PoE and DC are alternative documented arrangements; peak power and cable drop still matter.
{% endhint %}

**5.2.1 Power Supply**

The Gemini 435Le camera can be PoE/DC powered with the following power requirements: Table 5-2-1 Gemini 435Le power supply requirements Power supply method Requirements PoE IEEE 802.3af DC ≥2A @ 9-24V

**5.2.2 Power Consumption**

Power consumption varies depending on the selected working mode. Table 5-2-2 Typical configuration & tested power consumption Reference Power supply PoE DC Power Typical configuration Laser power level: 5 D2C：On Operating temperature: 25°C Depth：1280 x 800 @ 10 fps RVL, AE On RGB: 1280 x 800 @ 10 fps MJPEG AE On IR × 2: 1280 x 800 @ 10 fps Y8 AE On IMU ODR (output data rate): 1000Hz Laser power level: 5 D2C：On Operating temperature: 25°C Depth：1280 x 800 @ 10 fps RVL, AE On RGB: 1280 x 800 @ 10 fps MJPEG AE On IR × 2: 1280 x 800 @ 10 fps Y8 AE On IMU ODR (output data rate): 1000Hz Average power consumption 7.57W 6.07W

Table 5-2-2 High-Temperature Max Power Configuration & Measured Power Consumption Reference Power supply PoE DC Power Max Power Configuration Laser power level: 6 D2C：On Operating temperature: 50°C Depth：1280 x 800 @ 10 fps RVL, AE On RGB: 1280 x 800 @ 10 fps MJPEG AE On IR × 2: 1280 x 800 @ 10 fps Y8 AE On IMU ODR (output data rate): 1000Hz Laser power level: 6 D2C：On Operating temperature: 50°C Depth：1280 x 800 @ 10 fps RVL, AE On RGB: 1280 x 800 @ 10 fps MJPEG AE On IR × 2: 1280 x 800 @ 10 fps Y8 AE On IMU ODR (output data rate): 1000Hz Average power consumption 8.08W 6.55W \*Note: The data in the above table are laboratory measurements and are for design reference only.

**5.2.3 Storage and Powered Conditions**

Table 5-2-3 Gemini 435Le Storage and Powered Conditions Condition Description Min Max Unit Storage (Ambient), Not Powered Long term storage 0 60 ℃ Short exposure represents temporary max limits acceptable for transportation conditions -20 60 ℃ Humidity Temperature / RH： 60℃ / 95% Ambient, Powered\[1] The camera ambient temperature when powered -10 50 ℃ LDM Protect Temperature The LDM temperature when powered N/A 73 ℃ Backside Case Temperature, Powered The maximum temperature of the backside case occurs when the camera is operated in an ambient temperature of 50°C -3 65 ℃ Notes: \[2] If users require operation over a wider temperature range, additional thermal management measures need to be

evaluated.

**5.2.4 ESD Performance**

Table 5-2-4 Gemini 435Le ESD Performance Conditions Powered-On Powered-Off Certification Standards Contact Discharge ±8KV Class A ±8KV Class A EN 61000-6-2 Air Discharge ±15KV Class A ±15KV Class A

#### 5.3 Physical Performance <a href="#id-5.3-physical-performance" id="id-5.3-physical-performance"></a>

**5.3.1 Ingress Protection**

The Gemini 435Le supports IP67 level of water and dust resistance and has been factory tested for air tightness. In order to achieve this protection, users should make sure that the M8 A-coded connector is covered with a waterproof cover when using PoE power and use IP67 or higher rated cables. Gemini 435Le Ingress Protection Information IP Rating Power supply Protection Ability Conditions IP67 PoE ①Completely prevents dust from entering the camera ②Completely prevents water up to 1m deep from entering the camera interior for 30 minutes. ①Use an IP67 cable and make sure the M12 X-coded connector is connected well ②Ensure that the M12 A-coded connector cover is in place. DC power ①Use network cables and power cables that meet IP67 requirements; ②Ensure that the M12 X-coded and M12 A-coded interfaces are locked at the same time.

1. Firmware

#### 6.1 Firmware Update & Cautions <a href="#id-6.1-firmware-update-and-cautions" id="id-6.1-firmware-update-and-cautions"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

Gemini 435Le supports update the firmware via online or location, you can upgrade or downgrade as needed. To get the firmware and changelog: Firmware Release Please note the following considerations: 1. You can update the firmware in any working mode or preset; 2. All data streams must be closed when update the firmware; 3. During the firmware update, please ensure that the power supply and data transmission cable connections are stable; 4. The camera will automatically restart after the firmware update is completed. You can also re-plug the cable after completion and restart it manually;

#### 6.2 How to Update Firmware <a href="#id-6.2-how-to-update-firmware" id="id-6.2-how-to-update-firmware"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

The simplest way to update the firmware is through the Orbbec Viewer tool, which supports both manual updates and online updates. For detailed instructions, please refer to the documentation: Update firmware

#### 6.3 Recovery <a href="#id-6.3-recovery" id="id-6.3-recovery"></a>

Ensure the stability of cable during the update process to avoid upgrade failure. If the update process fails, disconnect the cable, re-insert it, and burn the product again. If re-burning is unsuccessful, the product may be damaged. Orbbec assumes no liability for any damages or losses resulting from the use of this product.

1. SDK Orbbec SDK is a flexible and modular platform for easy camera setup and runs on multiple platforms with a rich set of APIs. It supports camera access, device setup and configuration, data stream reading, processing, and viewing, RGB-D registration, and frame synchronization. Its functions include: Access and control of camera devices
2. Control of frame synchronization and alignment
3. Acquisition of point cloud data
4. Orbbec Viewer for camera testing and evaluation

Please visit Orbbec SDK for the latest SDK.

#### 7.1 Temperature Sensor and Recording <a href="#id-7.1-temperature-sensor-and-recording" id="id-7.1-temperature-sensor-and-recording"></a>

The temperature of camera core components can be obtained, including laser temperature, IR sensor temperature, RGB sensor temperature, ASIC temperature and IMU sensor temperature, through API commands.

1. Use Guidance

#### 8.1 Packing List <a href="#id-8.1-packing-list" id="id-8.1-packing-list"></a>

Table 8-1-1 Gemini 435Le Package List Package Type Package List Gemini 435Le Notes Bulk Camera Minimum batch packaging quantity: 25pcs Box Camera Minimum batch packaging quantity: 20pcs 1x Data Cable(2m) 1x Power Cable(2m) 1x Quick Start Guide

#### 8.2 Initialization and Operation <a href="#id-8.2-initialization-and-operation" id="id-8.2-initialization-and-operation"></a>

* Connect Gemini 435Le via the Data cable to the host PC
* Download Orbbec SDK from Orbbec SDK
* Use Orbbec Viewer to validate that images can be streamed from all sensors with the

following settings: o Depth stream: 1280 x 800(AMR Perceptiom) o Color stream: 1280 x 800(AMR Perceptiom) o IMU enabled

* If for any reason that the camera is not responding or not being detected, please

unplug all cables from the camera and replug the cables for resetting the camera status.

1. Regulatory Compliance These products are certified as follows:

#### 9.1 Laser Safety certification <a href="#id-9.1-laser-safety-certification" id="id-9.1-laser-safety-certification"></a>

Class 1 Laser Product under the EN/IEC 60825-1:2014 U.S. FDA Accession Number: 2420619-000

#### 9.2 EMC Regulatory Compliance <a href="#id-9.2-emc-regulatory-compliance" id="id-9.2-emc-regulatory-compliance"></a>

CE-Declaration FCC part 15 Declaration of Conformity KC

#### 9.3 Environment Regulatory Compliance <a href="#id-9.3-environment-regulatory-compliance" id="id-9.3-environment-regulatory-compliance"></a>

RoHS REACH WEEE

1. System Integration Guide Use outside of the specified conditions could cause the device to fail and/or function incorrectly. These conditions are applicable for the environment immediately around the device under all operational conditions. When used with an external enclosure, active temperature control and/or other cooling solutions are recommended to ensure the device is maintained within these ranges.

#### 10.1 Installation Recommendations <a href="#id-10.1-installation-recommendations" id="id-10.1-installation-recommendations"></a>

1. When using external housing around the camera for dust proofing, use foam inserts or rubber gaskets between the front of the camera and the external housing. 2. Avoid external forces applied to the camera chassis during installation process. 3. Disassembling chassis will void the warranty.

#### 10.2 Heat Dissipation <a href="#id-10.2-heat-dissipation" id="id-10.2-heat-dissipation"></a>

1. Avoid direct heat source around the camera. 2. Maximizing the space inside the external housing may help lower operating temperature.

#### 10.3 Cable Design Guide <a href="#id-10.3-cable-design-guide" id="id-10.3-cable-design-guide"></a>

1. It is recommended to use the included data cable and power cable. If there is a need for longer cable, please select a T568B Ethernet cable that meets CAT6A standards.
2. Cautions 1. Follow the instructions carefully when operating the camera. Improper handling may lead to damage to the internal components. 2. Do not drop the camera or expose the camera to mechanical stress. 3. Do not attempt to modify the camera as such modifications may cause permanent damage or performance degradation. 4. The temperature of the camera may rise during long periods of use. 5. Do not touch the lens. Fingerprints on the lens may affect image quality. 6. Keep the product beyond the reach of children or animals to avoid accidents. 7. If the computer does not recognize the camera, verify that the cables meet the power and data transfer requirements, then replug them into the ports to reconnect. 8. This product is classified as a Class 1 Laser Product under the international standard EN/IEC 60825-1, Edition 3 (2014). Using controls, adjustments, or procedures other than those specified herein may result in hazardous radiation exposure. Safety and Handling Instructions: ●Avoid powering on the product if any external damage was observed. ●Do not attempt to open any portion of this product. There are no user serviceable parts. ●Be cautious of invisible laser radiation. Avoid direct exposure to the beam. ●To maintain compliance and safety standards, do not modify or service the product. Unauthorized modifications or servicing could result in emissions surpassing the Class 1 safety level. ●Only update the camera firmware with official releases that match the specific module SKU and revision to ensure proper functionality and safety.

Appendix A Gemini 435Le 2D Mechanical Diagram

Appendix B The cables reference design drawing Data cable: Power cable:

#### Set up Cameras for External Synchronization <a href="#set-up-cameras-for-external-synchronization" id="set-up-cameras-for-external-synchronization"></a>

_Reviewed source:_ [_Set up Cameras for External Synchronization_](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Connector numbering, electrical levels and pulse widths belong to the exact model, connector view and synchronization accessory. The core hardware section identifies the documented source conflicts. These retained timing/mode explanations are not approval to build a custom trigger harness: keep optional sync disconnected for the first result and resolve the exact revision/view before applying a signal. A hub output level must not be treated as the camera GPIO limit.
{% endhint %}

#### 1. Connection Preparation <a href="#id-1.-connection-preparation" id="id-1.-connection-preparation"></a>

**1.1 Multi-camera Sync Hub Pro and Cable**

Table 1-1: Summary of Multi-Camera Synchronization Hub Pro and Cable

| Description                                                                                                                                               | Qty | Purchase Link                                                                                       | Remarks Description                                                                                                                                                                      | Example                                                        |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| 3D Camera                                                                                                                                                 | N   | Corresponding links for each product                                                                | N ≥ 2                                                                                                                                                                                    | Gemini 335 :2                                                  |
| Multi-Camera Sync Hub Pro ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013812/image001-e1725414259621-300x123.png)           | 1   | [Purchase Link](https://store.orbbec.com/products/sync-hub-pro)                                     | 1 hub supports 1 primary and up to 8 Secondary cameras                                                                                                                                   | Quantity: 1                                                    |
| Multi-camera Sync Adapter for Gemini\&Astra series ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013817/image003-300x186.png) | N   | [Purchase Link](https://store.orbbec.com/products/sync-adaptor-for-astra-2-and-gemini-2-330-series) | SH1.0-8P synchronous patch cord                                                                                                                                                          | Quantity: 2                                                    |
| Multi-camera Sync Adapter for Femto series ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013821/image005.png)                 | N   | [Purchase Link](https://store.orbbec.com/products/sync-adaptor-for-femto-mega-and-femto-bolt)       | SH1.2-8P synchronous patch cord                                                                                                                                                          | N/A                                                            |
| Network cable ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013826/image007-e1725414360514.png)                               | N   |                                                                                                     | To be provided by the user: Network cable standard T568B To T568B,Cate5e and above specifications, network cable length can be confirmed according To the actual scene, recommended <10m | Quantity: 2                                                    |
| multi-camera synchronization hub Type-C power cable                                                                                                       | 1   |                                                                                                     | To be provided by the user                                                                                                                                                               | Quantity: 1                                                    |
| For camera power supply and data transmission USB3.0 Hub                                                                                                  | 1   |                                                                                                     | To be provided by the user                                                                                                                                                               | Quantity: 0;2+ USB ports of computers can meet the requirement |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/4AgYdWCkGxjLzA2IdAHp/image007%20e1725414360514.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/S6o59gubXW1jS7mmxOGG/image005.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/gcR40f9tmJfk7L8ZtdN6/image001%20e1725414259621%20300x123.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nuqSFVdIeeCdoHXZ4BI2/image003%20300x186.png)

**1.2 Multi-camera Sync Dev Hub and Cable**

Table 1-2 Summary of Multi-Camera Synchronization Hub and Cable

| Description                                                                                                                                                | Qty | Purchase Link                                                                                              | Remarks Description                                    | Example       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | --- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | ------------- |
| 3D Camera                                                                                                                                                  | N   | Corresponding links for each product                                                                       | N ≥ 2                                                  | Gemini 335L:4 |
| Multi-Camera Sync Hub Dev (Star/Daisy-Chain) ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013832/image009-e1725414523645.png) | 1   | [Purchase Link](https://store.orbbec.com/products/sync-hub-dev-star)                                       | 1 hub supports 1 primary and up to 4 secondary cameras | 1             |
| Multi-Camera Sync Cable Dev for Gemini\&Astra series ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013838/image011.png)        | N   | [Purchase Link](https://store.orbbec.com/products/sync-cable-8-pin-1m-for-astra-2-and-gemini-2-330-series) | SH1.0-8P synchronous cable                             | 4             |
| Multi-Camera Sync Cable Dev for Femto series ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013842/image013.png)                | N   | [Purchase Link](https://store.orbbec.com/products/sync-cable-8-pin-1m-for-femto-mega-and-femto-bolt)       | SH1.2-8P synchronous cable                             | N/A           |
| multi-camera synchronization hub Type-C power cable \* 1                                                                                                   | 1   |                                                                                                            | To be provided by the user                             | 1             |
| USB3.0 Hub\*2                                                                                                                                              | 1   |                                                                                                            | To be provided by the user                             | 1             |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/2mP9HdWOpyWhzR2N0EPT/image011.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Awbm7T2vHI1JYSF0L7vH/image013.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EM6w5iOfzXbp8RQQNNZF/image009%20e1725414523645.png)
* 1 Type-C power cable, power supply requirements: 5V
* 2 for USB Hub with external power supply, the output current needs to meet the specification requirements of the product. The above recommendations are the relevant USB Hub used in our actual test for reference. The required specification is a Hub with an external power supply, and the output requirement is 5V 2.4A.

**1.3 Camera Power Supply Requirements**

1. After purchasing the camera, you can choose to power it either via USB 3.0 or PoE (Power over Ethernet), based on the specific camera model. (The camera must support PoE functionality.)
2. When using a USB 3.0 Hub for power, verify whether the upstream device’s output current meets the product’s requirements according to the camera’s specifications. Typically, a computer’s USB 3.0 port outputs 900mA/4.5W. If this does not meet the product’s specifications, ensure the use of an external USB Hub with sufficient output current as per the product’s requirements. Please refer to Appendix 1 for detailed information.

For reference, we have tested the following USB Hubs for practical use:

Table 1-3 Reference Description of Camera Power Supply and Connection Cable

| USB Hub Model | Specifications             | Purchase Reference Link |
| ------------- | -------------------------- | ----------------------- |
| USB3.0 Hub    | USB3.0 hub, output 5V 2.4A | USB Hub purchase link   |

3. Typically, to ensure adequate power supply for some cameras, the camera is factory-equipped with a Type-C to Type-C cable. When synchronizing multiple cameras, you will need to purchase Type-C to Type-A cables. Orbbec can provide official 1m/2m Type-A to Type-C cables. For longer cables, please refer to the document [reference design\&best practice-cable](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Cable%20\(USB\)%20\(Gemini%20330%20Series\)).

**1.4 Platform Configuration**

When running multi-camera synchronization, the host computer may need to simultaneously read and process data from multiple cameras. Therefore, we recommend using a sufficiently powerful host computer platform to ensure smooth operation of the multi-camera synchronization function. The following platform configurations have been tested previously and can support the normal operation, provided as a reference:

Table 1-4 Platform Configuration Description

| Platform                              | X64                                          | X64                                          | ARM 64                                       |
| ------------------------------------- | -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| Hardware device                       | PC                                           | PC                                           | Orin Nano                                    |
| System                                | Windows 10                                   | Ubuntu20.04                                  | Ubuntu20.04                                  |
| CPU                                   | Intel i7-10750H                              | Intel i7-10750H                              | 6-core A78                                   |
| RAM                                   | 16GB                                         | 16GB                                         | 8G                                           |
| Typical number of supported secondary | Please refer to Appendix I for more details. | Please refer to Appendix I for more details. | Please refer to Appendix I for more details. |

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

#### 2. Device Connection Operation Instructions <a href="#id-2.-device-connection-operation-instructions" id="id-2.-device-connection-operation-instructions"></a>

Below, we will illustrate an example of star connection using Gemini 335 in conjunction with the developer version of the hub.

**2.1 Detailed Camera Connection Steps**

Table 2-1 Detailed operation steps for camera connection

| Operation steps | Overview of operating steps                          | Detailed description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Notes and Schematic Diagram                                                                                                                       |
| --------------- | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1               | Preparation for connection                           | You will need to prepare the following items: – 2x Gemini 335 cameras – 2x synchronization cables – 2x Type-A to Type-C cables – 1x multi-camera synchronization hub – 1x Type-C interface synchronization hub power cable                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                   |
| 2               | Connect the cables at the camera end.                | Connect the USB cables and multi-camera synchronization cables as shown in the diagram. ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013848/image015.png) Note: When connecting at the camera end, ensure the red line on the synchronization cable aligns with the rotational position of the synchronization port plug. Follow the host’s connection method to sequentially connect the secondary cameras (Secondary Cam 1/2/3/4) to the hub.                                                                                                                                                                                 | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013853/image021.gif)                                                    |
| 3               | Connect the cables at the hub end                    | 1. Connect the host’s synchronization cable to the “Primary In” port of the multi-camera synchronization hub. 2. Connect the secondary cameras’ synchronization cables to the “Secondary: Cam” ports of the multi-camera synchronization hub. If there are multiple secondary cameras, connect them sequentially to Secondary Cam 1/2/3/4 ports on the hub. 3. Connect a 5V power supply to the Type-C port or DC port of the hub. \[Note] For synchronization involving more than 4 secondary cameras, a synchronization extender is required. For detailed connection instructions, please refer to the datasheet of the multi-camera synchronization hub. | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013858/image023.gif)                                                    |
| 4               | Connect the cameras to the host computer or USB hub. | Connect the cameras to the USB 3.0 ports on the host computer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | The USB hub must be USB 3.0 and independently powered. If connecting directly to the host computer, ensure that the USB output current is ≥1.5 A. |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5rXUMRMUdZrHwDoy4SnF/image015.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Ai68rwHnHOUb7k5cNvA2/image023.gif)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/pFqsII8wwZi86KUE2kQ2/image021.gif)

**2.2 Complete Schematic Diagram of Camera Connections**

![Official Orbbec figure from Set up Cameras for External Synchronization](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/U9sD8slzsXbBQaTk9e4L/image025.jpg)

Figure 2-1 Schematic diagram of complete camera connection

Number Name Description:

| NO. | Description                        | No. | Description        |
| --- | ---------------------------------- | --- | ------------------ |
| ①   | 3D camera                          | ⑤   | power supply cable |
| ②   | multi-camera synchronization Hub   | ⑥   | USB Hub            |
| ③   | multi-camera synchronization cable | ⑦   | Host               |
| ④   | USB data Cable                     |     |                    |

See Appendix I for details of the connection instructions for the professional version.

#### 3. Camera Configuration <a href="#id-3.-camera-configuration" id="id-3.-camera-configuration"></a>

**3.1 Use the Orbbec Viewer to Configure and Verify that Synchronization Takes Effect**

* Get Orbbec Viewer: [Download Orbbec Viewer.](https://github.com/orbbec/OrbbecSDK/releases)
* Gemini 330 series synchronization effective confirmation method:

After connecting the camera according to the 2.1, open the Orbbec Viewer and perform the following configurations:

1. Primary configuration, as shown in Figure 3-1:

① The primary synchronization configuration mode is configured as Software Triggering

② Make sure the trigger out enable is available

③ Set the primary single trigger acquisition frame number, can be set to any value

④ Click on "Write" button to save the settings.

⑤Confirm synchronization configuration was saved successfully.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013913/image027.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/PkFNNMGV6w41TQYeCpcp/image027.gif)

Figure 3-1-1 Gemini 335 Synchronization Validation Primary Configuration

2. Configuration of the secondary device, as shown in Figure 3-2:

① Set the secondary synchronization configuration mode to Hardware Triggering.

② Make sure the trigger out enable is available if using daisy-chain topology, and this is not required for star topology.

③ Set the number of frames for single-trigger data collection on the secondary device, which can be configured to any value.

⑤Confirm synchronization configuration was saved successfully.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013921/image029.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UtBeHzgtCpCPSqTZrCb1/image029.gif)

Figure 3-1-2 Gemini 335 Synchronization Validation Secondary Configuration

3. Toggle the depth and color buttons for the Primary and Secondary. The depth stream for both devices does not display, but the color stream is functioning correctly, as shown in Figure 3-3:

① Toggle the depth and color buttons for the Primary.

② Toggle the depth and color buttons for the Secondary.

③ Neither the Primary nor the Secondary outputs depth stream; only the color stream is outputted.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013930/image031.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7VPyIAwegQ0x9DFe06vK/image031.gif)

Figure 3-1-3 Gemini 335 Synchronization Validation Secondary Configuration

4. Synchronization verification process as shown in Figure 3-4:

① Click the "Trigger Once" button on the Primary. Both the Primary and Secondary should capture stream normally, indicating that camera synchronization is functioning (hardware connection OK). If synchronization is not working, the Secondary device will not capture the specified number of frames after triggering from the Primary.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013939/image033.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zarq32Hj7AicBr5BF1Lg/image033.gif)

Figure 3-1-4 Gemini 335 synchronization validation

* Confirmation of Astra 2 synchronization effectiveness is detailed in Appendix III.
* Confirmation of Femto Mega/Bolt synchronization effectiveness is detailed in Appendix IV.
* The synchronization verification method for Gemini 2 series is the same as for Gemini 330 series, with the only difference being that Gemini 2 series supports RGB triggering.

**3.2 Use the SDK to Run a Multi-camera Synchronization Example**

**3.2.1 Initial Configuration for Multi-Camera Synchronization**

SDK Acquisition: [Download Orbbec SDK](https://github.com/orbbec/OrbbecSDK/releases)

In the SDK program folder:\OrbbecSDK\_C\_C++\_v1.10.8\_20240604\_d1671a341\_win\_x64\_release\OrbbecSDK\_v1.10.8\Example\binFind the configuration file "MultiDeviceSyncConfig.json", and configure it as shown in the following figure. After configuration, save the settings. (The following is a reference setting for the Gemini 330 series)

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013948/image035.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/NC1zfekcop5aM2nHSRNH/image035.gif)

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

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013956/image037.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/fZsxfzg6QaD0hChyLiuB/image037.gif)

Figure 3-2-2 Example Operation Diagram of Gemini 335 multi-camera Synchronization

1. Successful streaming and preview of multi-camera effects are shown in Figure 3-2-2 below.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020144/image038.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5PY6gQ5ZO2HD9YeJPUj5/image038.png)

Figure 3-2-3 Preview of multi-camera synchronous open streaming of Gemini 335

7. Checking the effect of multi-camera synchronization

① According to the designated device numbers as follows: Device#0 (Primary) and Device#1 (Secondary), locate the timestamps (Sensor timestamp for Gemini 335; Frame timestamp for Gemini 335L) that are closest to each other. These timestamps represent the synchronized timestamps between the two devices. The figure below illustrates that the depth synchronization timestamp between the Primary and Secondary devices shows a difference of 0 to 1ms, and the color synchronization timestamp also shows a difference of 0 to 1ms.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020154/image040.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ctL83ePtEJKvouaZonWY/image040.png)

Figure 3-2-4 Gemini 335 multi-camera synchronization open-stream synchronization timestamp Log

**3.3 Key Log**

Table 3-3-1 Key Logs

| Journal               | Significance                          |
| --------------------- | ------------------------------------- |
| Device#0, color frame | RGB camera data stream for device 0   |
| Device#0, depth frame | Depth camera data stream for device 0 |
| Device#1, color frame | RGB camera data stream for device 1   |
| Device#1, depth frame | Depth camera data stream for device 1 |

Note: When analyzing data, confirm based on the timestamps of different devices.

Table 3-3-2 Key Words

| Key word         | Meaning                                                                                                                                                                                                                                                                                                                                                                    |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Device#X         | X represents the device number. Device#0 and Device#1 are simply used to distinguish between different devices and are not related to the device IDs in the configuration file.                                                                                                                                                                                            |
| color frame      | Color stream                                                                                                                                                                                                                                                                                                                                                               |
| depth frame      | Depth stream                                                                                                                                                                                                                                                                                                                                                               |
| Frame timestamp  | Frame timestamp is critical for analyzing multi-camera synchronization. Frames from the same batch of data across different devices have closely aligned timestamps. Conversely, frames with similar timestamps generally depict similar content. This can be verified by capturing dynamic objects and judging the similarity of scene content based on object positions. |
| system timestamp | The system timestamp recorded after receiving a complete UVC data frame.                                                                                                                                                                                                                                                                                                   |

#### 4. Caution <a href="#id-4.-caution" id="id-4.-caution"></a>

1. After starting the device, press ‘ESC’ in the image preview window to stop the data stream and exit the program. Abnormal program termination may cause incomplete shutdown of the device, leading to continuous triggering of the secondary device (restarting the device can resolve this).
2. The same device can only be accessed by one application at a time. Opening the same device with multiple applications simultaneously may cause anomalies. Please use with caution.
3. Using AE (Auto Exposure) may result in synchronization delays due to significant environmental differences between cameras. It is recommended to use the SDK to call exposure control interfaces and set fixed exposures to mitigate this issue.
4. For Linux computers, such as Ubuntu, the default kernel allocates only 16 MB of memory for USB controllers to handle USB transfers. This amount may be insufficient for high-resolution images or multiple streams and devices. To support multiple devices, the USB controller must have more memory allocated. Follow these steps to increase the allocated memory:
5. Edit.
6. Locate the following line:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"`

(or other contents within quotes, depending on your system) and replace it with:

`GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbcore.usbfs_memory_mb=128"`

Note: This command sets USB memory to 128 MB. This example sets it to 8 times the default value. Adjust as needed.

1. Run .
2. Restart your computer.

#### 5. Code Development <a href="#id-5.-code-development" id="id-5.-code-development"></a>

Users can refer to the example source code and interface documentation provided in the SDK package directory to develop their code according to actual business requirements.

Key code:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
// Update the configuration items of the configuration file, and keep the original configuration for other items Autocor config = device-> Get multi devices yncconfig (); CurConfig. syncMode = config->syncConfig.syncMode; curConfig.depthDelayUs = config->syncConfig.depthDelayUs; CurConfig. colorDelayUs = config->syncConfig.colorDelayUs; CurConfig. trigger2ImageDelayUs = config->syncConfig.trigger2ImageDelayUs; Curconfig. triggero-utenable = config-> syncconfig. triggero-utenable; CurConfig. triggerOutDelayUs = config->syncConfig.triggerOutDelayUs; CurConfig. framesPerTrigger = config->syncConfig.framesPerTrigger; Device->setMultiDeviceSyncConfig(curConfig); The enum names for different synchronization modes in the SDK: /** * @ brief The sync mode of the device */ Typedef enum { /** * @brief free run mode * @ brief This device is not syncing with other devices * @ brief "Color" and "Depth" can be set to different frame rates */ OB_MULTI_DEVICE_SYNC_MODE_FREE_RUN = 1 << 0, /** * @brief standalone mode * @ brief This device is not syncing with other devices * @ brief "Color" and "Depth" should be set to the same frame rate, "Color" and "Depth" will be synchronized */ OB_MULTI_DEVICE_SYNC_MODE_STANDALONE = 1 << 1, /** * @brief primary mode * @ brief This device is the primary device in a multi-camera system, which by default outputs trigger signals via the VSYNC_OUT pin on the synchronization port. * @ brief The color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs. */ OB_MULTI_DEVICE_SYNC_MODE_PRIMARY = 1 << 2, /** * @brief secondary mode * @ brief This device is the secondary device in a multi-camera system, which receives trigger signals via the VSYNC_IN pin on the synchronization port. By default, it outputs trigger signals via the VSYNC_OUT pin on the synchronization port. * @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs. * @ brief After starting the stream, the device waits for trigger signals to begin capturing images and stops capturing images when the trigger signal stops. * * @ attention The frequency of trigger signals should match the frame rate set in the stream profile configured during stream startup. */ OB_MULTI_DEVICE_SYNC_MODE_SECONDARY = 1 << 3, /** * @brief secondary synced mode * @ brief This device is the secondary device in a multi-camera system, which receives trigger signals via the VSYNC_IN pin on the synchronization port. By default, it outputs trigger signals via the VSYNC_OUT pin on the synchronization port. * @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs. * @ brief After starting the stream, the device immediately begins capturing images and adjusts capture timing upon receiving trigger signals to synchronize with the primary device. The device continues capturing images even if trigger signals stop. * * @ attention The frequency of trigger signals should match the frame rate set in the stream profile configured during stream startup. */ OB_MULTI_DEVICE_SYNC_MODE_SECONDARY_SYNCED = 1 << 4, /** * @brief software triggering mode * @ brief This device starts image capture upon receiving a capture command and by default outputs trigger signals via the VSYNC_OUT pin. Capture commands can be sent from the host using @ref ob_device_trigger_capture. The number of images captured per shot can be set using @ref framesPerTriggerForTriggeringMode * @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs. * @ brief The frequency at which the user calls @ref ob_device_trigger_capture to send capture commands multiplied by the number of frames per trigger should be less than the frame rate set in the stream configuration file at startup. */ OB_MULTI_DEVICE_SYNC_MODE_SOFTWARE_TRIGGERING = 1 << 5, /** * @brief hardware triggering mode * @ brief This device starts image capture upon receiving a trigger signal via the VSYNC_IN pin on the synchronization port and by default outputs trigger signals via the VSYNC_OUT pin. The number of images captured per shot can be set using @ref framesPerTriggerForTriggeringMode. * @ brief Color and depth should be set to the same frame rate. Color and depth will synchronize, and adjustments can be made using @ref colorDelayUs, @ref depthDelayUs, or @ref trigger2ImageDelayUs. * * @ attention The frequency at which trigger signals are received multiplied by the number of frames per trigger should be less than the frame rate set in the stream configuration file at startup. * @ attention In hardware triggering mode or software triggering mode, the trigger signals input via the VSYNC_IN pin on the synchronization port should be output by other devices via the VSYNC_OUT pin. * @ attention Due to potential differences in signal input requirements among different device models, do not use trigger signals output from different device models as input trigger signals. */ OB_MULTI_DEVICE_SYNC_MODE_HARDWARE_TRIGGERING = 1 << 6, } ob_multi_device_sync_mode, OBMultiDeviceSyncMode;
```

#### 6. Subsidiary Function <a href="#id-6.-subsidiary-function" id="id-6.-subsidiary-function"></a>

**6.1 Use Orbbec Viewer to View Device SN**

When connecting multiple devices, follow these steps to view the SN (serial number) and connection method of the selected camera:

1. Select the corresponding device from the options in the top left corner as shown in Step ① of the following figure.
2. Then, click according to Step ② in the figure to view the SN and connection method of the selected camera.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020201/image042.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/S8viupzlBJMyj6CT59h7/image042.png)

Figure 6-1 diagram of the device SN viewed by the Orbbec Viewer

**6.2 View Multi-camera Synchronization Configuration in Orbbec Viewer**

① After connecting the devices, open the Orbbec Viewer tool. If multiple devices are connected, you need to select the devices. If only one device is connected, no selection is required as the device will be recognized automatically.

② Click on "Device Control" and expand "Synchronization Configuration" to display relevant parameters such as mode, color delay, depth delay, trigger output switch, signal output delay, and other information.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020207/image044.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ZTDS7hvR1Rij3s7DkuTb/image044.png)

Figure 6-2 Schematic diagram of the equipment viewed by the Orbbec Viewer

#### 7. Appendix <a href="#id-7.-appendix" id="id-7.-appendix"></a>

**7.1 Appendix I: Typical Number of Supported Secondary**

Appendix Table 1-1: Supported number of secondary and power requirements

| Product           | Typical number of supported secondary | Maxunim of supported secondary                                                                                                                                             | Power supply request                    |
| ----------------- | ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------- |
| Femto Mega        | 1-4 units                             | 8 units                                                                                                                                                                    | Use the camera’s built-in power supply. |
| Femto Bolt        | 1-4 units                             | 1-4 units                                                                                                                                                                  | Use the camera’s built-in power supply. |
| Gemini 2          | 1-4 units                             | Theoretical support for infinite expansion is contingent upon the performance of the host computer and bandwidth limitations. In practical tests, we have used four units. | Power supply:5V ; Current：≥1.5A         |
| Gemini 2 L        | 1-4 units                             | Theoretical support for infinite expansion is contingent upon the performance of the host computer and bandwidth limitations. In practical tests, we have used four units. | Power supply:5V ; Current：≥2.0A         |
| Gemini 2 XL       | 1-4 units                             | Theoretical support for infinite expansion is contingent upon the performance of the host computer and bandwidth limitations. In practical tests, we have used four units. | Power supply:5V ; Current：≥2.0A         |
| Gemini 330 series | 1-4 units                             | Theoretical support for infinite expansion is contingent upon the performance of the host computer and bandwidth limitations. In practical tests, we have used four units. | Power supply:5V ; Current：≥1.5A         |
| Astra 2           | 1-4 units                             | 7 units                                                                                                                                                                    | Power supply:5V ; Current：≥1.5A         |
| Gemini 215        | 1-4 units                             | 1-4 units                                                                                                                                                                  | Power supply:5V ; Current：≥1.5.A        |

\*\*The maximum number of supported peripherals depends on the performance of the host computer and bandwidth limitations. When connecting multiple cameras to a single USB 3.0 hub, the primary consideration is the bandwidth limitation of the host system. It’s also important to verify whether the host computer’s USB ports are connected through internal USB hubs or if they have multiple independent controllers. If bandwidth issues cause streaming problems, reducing resolution or frame rate can be chosen as a solution.

**7.2 Appendix II: Detailed Operation Steps for Multi-camera Sync Hub Pro Connection**

Appendix Table 2-1 Detailed Operation Procedure Description of Camera Connection for Multi-camera Sync Hub Pro (The following takes 2 Gemini330 series cameras as an example to illustrate)

| Operation steps | Overview of operating steps                        | Detailed description                                                                                                                                                                                                                                                                                                                               | Notes and Schematic Diagram                                                                                                                                    |
| --------------- | -------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1               | Connection preparation                             | You need to prepare 2x Gemini 330 series cameras, 2x Multi-camera Sync Adapter , 2x network cables, and a Multi-camera Sync Hub Pro.                                                                                                                                                                                                               | Note: 1. Specifications of network cable: T568B-T568B,Cate5e and above; 2、 Network cable length <10m                                                           |
| 2               | Camera end connection                              | Connect the camera end to the Multi-camera Sync Adapter, USB cable and network cable as shown on the right.                                                                                                                                                                                                                                        | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020213/image046.png)                                                                 |
| 3               | Primary device hub-end connection                  | ① Connect one end of the network cable to the “Primary In” interface of the hub ② Connect the other end of the network cable to the synchronous adapter RJ45 interface of the Primary device. ③ Use the Type-C power cable to connect the Type-C 5V In of the synchronization hub and supply 5V power to it                                        | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020219/image048.png)                                                                 |
| 4               | secondary device hub-end connection                | ① Connect one end of the network cable to the “Secondary Cam1” interface of the synchronization hub ② Connect the other end of the network cable to the synchronous adapter RJ45 interface of secondary 1 device. Note: If there are multiple cameras distributed, connect Secondary cam2/3/4 at one time according to the above Operation steps…. | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020226/image050.png)                                                                 |
| 5               | Connect the camera to the host computer or USB Hub | Camera and USB Hub need to be connected to USB3.0 interface                                                                                                                                                                                                                                                                                        | The USB Hub needs to be USB3.0 with independent power supply; If directly connected to the host computer, pleaseensure that the USB output current is ≥ 2.0 A. |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/07Chbt0b4dzLMnl1X2VK/image048.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kJQSIctXRA3R7Sv7plit/image050.png)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ycgRS3nxmRMihZgVv33R/image046.png)

**7.3 Appendix III: Astra 2 Synchronization Confirmation Method**

1. After connecting the camera as described in section 2.1, open OrbbecViewer for the following configurations:
2. Configure the synchronization mode and parameters between the primary and the secondary according to Figure 3-1:

① Set the primary device sync mode to "Primary"

② Click ‘Write’

③ Select the secondary device, and set the sync mode to "Secondary-synced"

④ Set the secondary’s Trigger2Image delay <sup>\[1]</sup> is ≥4000

⑤ Click ‘Write’

Note: \[1] For star topology connection, set the secondary’s Trigger2Image delay between secondary 1 and the Prinary to be ≥4000 microseconds. If there are multiple secondary cameras, delays between secondary also need to be ≥4000 microseconds. For daisy-chain topology connection, set the secondary’s signal output delay to -1; this applies to all secondary.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020233/image052.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/pBhCUvum3hVN6B4SQ3yy/image052.png)

Appendix Table 3-1: Astra 2 Synchronization Confirmation Host/secondary Configuration Diagram

1. Configure the depth frame rate for the host and the secondary as shown in Figure 3-2:

① Set the Primary depth frame rate to 30fps.

② Set the secondary depth frame rate to 15fps.

③ Toggle the depth and color buttons on the primary device, Ensure normal depth and color streams from primary device.

④ Toggle the depth and color buttons on the secondary device, Confirm normal color stream from the secondary, with no depth imaging as expected.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020240/image054.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/NbS4qPk6qPvoX9ToqEXX/image054.png)

Appendix Table 3-2: Astra 2 Synchronization Confirmation Diagram

⑤ Set the secondary depth frame rate to 30fps to confirm synchronization is effective with normal data output (refer to Figure 3-3).

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020247/image056.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/45NqtuSnzbC68xvzyDos/image056.png)

Appendix Table 3-3: Astra 2 Synchronization Confirmation Diagram

\[Note] Ineffective synchronization is indicated when the primary operates at 30fps for depth, and the secondary at 15fps for depth. When depth imaging is enabled on both devices, the secondary should display depth imaging correctly under these conditions.

**7.4 Appendix IV: Confirmation Method for Femto Mega/Bolt Synchronization Effectiveness**

1. Open Orbbec Viewer and configure Femto Mega/Bolt as follows:
2. Configure the synchronization mode and parameters between the primary and the secondary cameras, as shown in Figure 3-1:

① Set the primary camera mode to: Primary

② Click ‘Write’

③ Select the secondary camera, and set the mode to: Secondary

④ Configure the secondarydepth delay: ≥125us, recommended 160us

⑤ Click ‘Write’

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020253/image058.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/BAIFfdaQ2fYYybtZ2x2V/image058.png)

Appendix Table 4-1: Femto Mega/Bolt Synchronization Confirmation Host/Slave Configuration Diagram

2. Verification Method for Synchronization:

① Toggle the depth and color buttons on the secondary device. Neither depth nor color data streams are output from the secondary device.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020301/image060.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IKHRRXrV0eOUlfBPB4lm/image060.png)

Appendix Table 4-2: Femto Mega/Bolt Synchronization Effectiveness Verification Diagram

② After enabling depth and color on the primary device, observe normal depth and color imaging on the secondary device to confirm synchronization is effective.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020309/image062.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8j7rKY2BAlQdau7bTnG1/image062.png)

Appendix Table 4-3: Femto Mega/Bolt Synchronization Effectiveness Verification Diagram

\[Note] Ineffective synchronization is indicated if the secondary camera does not produce images when the primary is enabled, or if the secondary produces images without the primary being enabled.

**7.5 Appendix V: Synchronous Configuration Details**

**7.5.1 Profile Description**

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
{ "version": "1.0.0", "configTime": "2023/01/01", "devices": [ { "sn": "AY3A131007M", // 1. Configure Primary SN, case-sensitive. "syncConfig": { "syncMode": "OB_MULTI_DEVICE_SYNC_MODE_PRIMARY", // 2. The sync mode is Configured to the PRIMARY mode. "depthDelayUs": 0, // 3. Configure depth trigger delay, unit: microseconds "colorDelayUs": 0, // 4. Configure color trigger delay, unit: microseconds "trigger2ImageDelayUs": 0, // 5. Configure trigger image delay, unit: microseconds "triggerOutEnable": true, // 6. Configure trigger signal output enable. "triggerOutDelayUs": 0 // 7. Configure trigger signal output delay, unit: microsecond "framesPerTrigger": 1 // 8. Configure the number of frames captured by each trigger in the trigger mode } }, { "sn": "AY3JB20003C", // 9. Configure secondary SN,case-sensitive. "syncConfig": { "syncMode": "OB_MULTI_DEVICE_SYNC_MODE_SECONDARY_SYNCED", // 10. All configurations are set to OB_MULTI_DEVICE_SYNC_MODE_SECONDARY_SYNCED except for Femto series,The Femto series is configured to OB_MULTI_DEVICE_SYNC_MODE_SECONDARY "depthDelayUs": 0, // 11.Configure depth trigger delay, unit: microseconds "colorDelayUs": 0, // 12. Configure color trigger delay, unit: microseconds "trigger2ImageDelayUs": 0, // 13. Configure the trigger image delay, unit: microseconds "triggerOutEnable": true, // 14. Configure trigger output enable, "triggerOutDelayUs": 0 // 15. Configure the trigger signal output delay, unit: microseconds "framesPerTrigger": 1 // 16. Configure the number of frames captured by each trigger in the trigger mode } } ] }
```

① JSON files do not support comments, please do not copy the above comments.

The user can add configuration in the configuration file according to the actual number of devices used.

③ The camera SN number can be found on the camera housing, or it can be viewed on the device information page after connecting the device through the Orbbec Viewer tool.

④ When the primary mode is set, triggerOutEnable is forcibly set to true, and triggerOutDelayUs is forcibly set to 0.

**7.5.2 Multi-camera Synchronization Mode Definition Description**

| Pattern Name        | Setting effect description                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Free Run            | -Support different frame rate settings The synchronization interface does not support external output of synchronization-related signals                                                                                                                                                                                                                                                                                                                                  |
| Standalone(default) | ● Same as Primary by default ● Built-in RGBD frame synchronization ● Synchronous interface does not output signals to the outside by default                                                                                                                                                                                                                                                                                                                              |
| Primary             | ● Set as primary camera ● Synchronous interface output signal to external device                                                                                                                                                                                                                                                                                                                                                                                          |
| Secondary           | ● Set as secondary (passive synchronization; When there is a hardware continuous trigger signal input from the outside and the continuous trigger signal matches the currently set frame rate, the image is collected according to the external trigger signal; When there is no external trigger signal, the flow is stopped) ● Synchronous interface output signal to external device                                                                                   |
| Secondary-synced    | ● Set to secondary synchronization (passive synchronization; When there is a hardware continuous trigger signal input from the outside and the continuous trigger signal matches the currently set frame rate, the image is collected according to the external trigger signal; When there is no external trigger signal, the image is collected according to the internal trigger signal at the set frame rate) ● Synchronous interface output signal to external device |
| Hardware Triggering | ● Set as hardware trigger (passive trigger; When there is a hardware trigger signal input from the outside and the trigger signal time interval is not less than the current upper limit, the image is collected according to the external trigger signal; When there is no external trigger signal, the image is not collected) ● Synchronous interface output signal to external device                                                                                 |
| Software Triggering | ● Set as software trigger (passive trigger; When there is a trigger command input from the host computer and the trigger command time interval is not less than the current upper limit, the image is collected according to the trigger command; When there is no trigger command, the image is not collected) ● Synchronous interface output signal to external device                                                                                                  |

**7.5.3 List of Product Support Modes**

| Product           | Free Run | Standalone (Default) | Primary | Secondary | Secondary-synced | Hardware Triggering | Software Triggering |
| ----------------- | -------- | -------------------- | ------- | --------- | ---------------- | ------------------- | ------------------- |
| Gemini 330 series | Support  | Support              | Support | N/A       | Support          | Support             | Support             |
| Gemini 2          | Support  | Support              | Support | N/A       | Support          | Support             | Support             |
| Gemini 2 L        | Support  | Support              | Support | N/A       | Support          | Support             | Support             |
| Gemini2 XL        | Support  | Support              | Support | N/A       | Support          | Support             | Support             |
| Astra 2           | Support  | Support              | Support | N/A       | Support          | N/A                 | N/A                 |
| Femto Mega        | Support  | Support              | Support | Support   | N/A              | N/A                 | Support             |
| Femto Bolt        | Support  | Support              | Support | Support   | N/A              | N/A                 | N/A                 |
| Gemini 215        | Support  | Support              | Support | N/A       | Support          | N/A                 | N/A                 |

The camera delay setting uses the default configuration.

**7.5.4 Comparison List of Camera Delay Settings**

Product NameDepth Delay(us)

| Product Name      | Primary / Depth Delay (us) | Primary / Color Delay (us) | Primary / Tigger2Image Delay (us) | Primary / Trigger Out Delay (us) | Secondary / Depth Delay (us) | Secondary / Color Delay (us) | Secondary / Tigger2Image Delay (us)                                                           | Secondary / Trigger Out Delay (us) | Remark                                                                                                                                       |
| ----------------- | -------------------------- | -------------------------- | --------------------------------- | -------------------------------- | ---------------------------- | ---------------------------- | --------------------------------------------------------------------------------------------- | ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Gemini 330 series | 0                          | 0                          | N/A                               | 0                                | 0                            | 0                            | N/A                                                                                           | 0                                  |                                                                                                                                              |
| Gemini 2          | N/A                        | N/A                        | 0                                 | N/A                              | N/A                          | N/A                          | 0                                                                                             | N/A                                |                                                                                                                                              |
| Gemini 2 L        | N/A                        | N/A                        | 0                                 | N/A                              | N/A                          | N/A                          | 0                                                                                             | N/A                                |                                                                                                                                              |
| Gemini 2 XL       | N/A                        | N/A                        | 0                                 | N/A                              | N/A                          | N/A                          | 0                                                                                             | N/A                                |                                                                                                                                              |
| Astra 2           | N/A                        | N/A                        | 0                                 | -1                               | N/A                          | N/A                          | Daisy-chain: 0 Star : Delay between secondary devices ≥ 4000 µs. For example, 4000/8000, etc. | Daisy-chain: -1; Star:0            | Trigger Out Delay :-1 represents the default exposure output time for the camera; 0 indicates that no external trigger signal is being sent. |
| Femto Mega        | 0                          | 0                          | N/A                               | N/A                              | 160/ 320…                    | 0                            | N/A                                                                                           | 0                                  |                                                                                                                                              |
| Femto Bolt        | 0                          | 0                          | N/A                               | N/A                              | 160/ 320…                    | 0                            | N/A                                                                                           | 0                                  |                                                                                                                                              |
| Gemini 215        | N/A                        | N/A                        | 0                                 | N/A                              | N/A                          | N/A                          | 0                                                                                             | N/A                                |                                                                                                                                              |

\*The above delay values are recommended default settings. Users may adjust these values to any amount greater than the default based on actual needs, allowing for synchronization with external devices by modifying the delay.

#### Regulatory Compliance and Certificates <a href="#regulatory-compliance-and-certificates" id="regulatory-compliance-and-certificates"></a>

_Reviewed source:_ [_Regulatory Compliance and Certificates of Gemini 435Le_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Regulatory%20Compliance%20and%20Certificates%20of%20Gemini%20435Le)_. Manufacturer figures and source examples retain their original attribution and rights._

Orbbec Gemini 435Le 3D camera certification and regulatory compliance information are as follows.

| Type           | Certification | Gemini 435Le certificate document                                  |
| -------------- | ------------- | ------------------------------------------------------------------ |
| Laser Safety   | Class 1       | [Gemini 435Le\_Class 1.pdf](https://doc.orbbec.com/attachments/12) |
| <p>EMC<br></p> | CE            | [Gemini 435Le\_CE.pdf](https://doc.orbbec.com/attachments/11)      |
| <p>EMC<br></p> | FCC           | [Gemini 435Le\_FCC.pdf](https://doc.orbbec.com/attachments/13)     |
| <p>EMC<br></p> | KC            | [Gemini 435Le\_KC.pdf](https://doc.orbbec.com/attachments/14)      |
| Environment    | REACH         | [Gemini 435Le\_REACH.pdf](https://doc.orbbec.com/attachments/15)   |
| Environment    | RoHS          | [Gemini 435Le\_ROHS.pdf](https://doc.orbbec.com/attachments/16)    |
| Environment    | WEEE          | [Gemini 435Le\_WEEE.pdf](https://doc.orbbec.com/attachments/17)    |

The source’s certificate-column title names 335/336 in error; the linked files identify Gemini 435Le. This header follows those actual document names. Certification statements remain the manufacturer’s documents, not a new approval.

#### Development Resources <a href="#development-resources" id="development-resources"></a>

* [Official Gemini 435Le documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation)
* [CAD files](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Download%20CAD%20Files%20of%20Gemini%20435Le)
* [Firmware releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Firmware%20Release%20of%20Gemini%20435Le)
* [Download tools](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20435Le%20Documentation/Download%20Tools)
* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK ROS 1 wrapper](https://github.com/orbbec/OrbbecSDK_ROS1)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
