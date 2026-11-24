---
description: >-
  Integrate the Gemini 305 USB wrist camera with profile-dependent near limits,
  mounting and thermal constraints, firmware pairing and an original depth-patch
  example.
---

# Orbbec Gemini 305: close-range USB wrist-camera development

{% hint style="info" %}
[**Orbbec Gemini 305 Close-Range Wrist Camera on OpenELAB**](https://openelab.io/products/orbbec-gemini-305-range-stereo-vision-camera)

**Model:** Gemini 305 · **SKU:** `ORBBEC-Gemini-305` · **Option:** standalone USB camera, not a robot-arm bundle and not the GMSL2 Gemini 305g.
{% endhint %}

Gemini 305 is an 18 mm-baseline passive color stereo camera for close-range geometry. It needs visible texture and adequate lighting, and it computes depth onboard. This guide covers USB power, wrist mounting, profile-dependent near limits and a first depth measurement before the camera is used in a moving robot.

## Product overview

### Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting <a href="#orbbec-gemini-305-range-stereo-vision-camera-for-robotic-wrist-mounting" id="orbbec-gemini-305-range-stereo-vision-camera-for-robotic-wrist-mounting"></a>

The two global-shutter color sensors and MX6800 depth processor provide depth/color or dual-color acquisition through USB Type-C. Its **IR-cut** optical path is different from an active infrared projector camera. A plain untextured wall in darkness is therefore a poor first target, even if another Gemini camera can measure it. SDK stream names inherited from the camera family do not establish an infrared illuminator. [Gemini 305 datasheet V1.0, §§1–4](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)

This is the camera alone. The same SKU also occurs as a camera option under robot-arm listings in the catalog; those incidental bundle rows do not define this standalone package. Compare the [305g guide](orbbec-gemini-305g-development-guide.md) for FAKRA/GMSL2 and the [335 guide](orbbec-gemini-335-user-manual.md) for longer-range active/passive stereo.

## Applications

* Eye-in-hand perception of small objects about 7–50 cm from the camera, with controlled visible lighting and useful surface texture.
* Close-range point clouds and grasp-pose development after camera calibration and hand–eye calibration are validated separately.
* Dual-color acquisition for stereo-algorithm experiments, using the corresponding stream combination rather than assuming depth and both color streams are all available together.
* Static measurement trials before a robot is allowed to move based on the result.

The camera's small minimum range does not eliminate occlusion by a gripper or tool. Plan cable strain relief and a clear view throughout the joint range. Keep robot motion disabled while checking camera geometry; a plausible image is not a validated robot transform.

## Specifications

Values below are scoped to [Gemini 305 V1.0, 5 January 2026, pp.10–17 and 19–20](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf). Different profile settings change the near limit, frame rate and thermal budget.

| Parameter                                 | Gemini 305                                                                                        |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Stereo baseline                           | 18 mm                                                                                             |
| Sensing / optical filtering               | Passive global-shutter color stereo / IR-cut                                                      |
| Working / ideal range                     | 4–100 cm / 7–50 cm; the 4 cm claim requires 848 × 530 and disparity search range 256              |
| Spatial precision                         | ≤1% at 50 cm, 1280 × 800, central 90% × 90% region; not an absolute-error promise for every scene |
| Depth profiles, USB 3                     | 1280 × 800 or 1280 × 720 at 5/10/15/30 fps; 848 × 530, 848 × 480 or 640 × 480 up to 60 fps        |
| Color maximum                             | 1280 × 800 at up to 60 fps; global shutter                                                        |
| Depth / color FOV                         | 88° × 65° ±3° at 20 cm and 1280 × 800 / 94° × 68° ±3°                                             |
| Processor / host connection               | MX6800 onboard depth / USB 3 recommended; USB 2 with reduced combinations                         |
| Supply capability / maximum average power | 5 V at ≥700 mA / ≤2 W                                                                             |
| Operating ambient                         | −10 to +45 °C with disparity search 128; −10 to +40 °C with search 256                            |
| Powered rear case limit                   | Up to 60 °C; provide a heat path                                                                  |
| Dimensions / mass                         | 42 × 42 × 23 mm / 68 g                                                                            |
| Enclosure                                 | IP54 only with the specified sealed, fully seated Type-C mating cable and tightened screws        |
| Model / USB VID:PID                       | G40351-191 / `2bc5:0840`                                                                          |

The broad range is not achieved with the same settings as every full-resolution stream. Increasing disparity search to reach closer objects raises thermal demand. Use the actual enumerated profile and record disparity setting with each measurement.

## Hardware and connections

![Gemini 305 two-aperture close-range camera, existing OpenELAB product image](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-1.jpg?v=1781599183)

Existing OpenELAB product illustration of the exact USB Gemini 305.

### Power and Type-C data

Connect the supplied USB data cable directly to a host or powered USB 3 hub that can provide 5 V/≥700 mA. Use a short cable first and confirm SuperSpeed negotiation. Never feed 12 V into the USB connector; that is the GMSL2 power domain of the different 305g model. A charge-only cable can power the camera without providing a usable stream. [Interface and power sections](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf#page=14)

The datasheet exposes synchronization on Type-C **SBU A8/B8**, with **1.8 V default** and configurable 3.3/5 V reference levels. These are not normal user GPIO leads on an arbitrary Type-C cable. Do not wire SBU, CC or VBUS to a robot controller from connector position alone. Use a model-specific supported synchronization accessory or design reviewed against the full interface drawing; the single-camera procedure needs no SBU connection. The published Type-C table contains confusing RX signal polarity labels, so it is not used here to specify a custom high-speed cable. [Pin table p.15](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf#page=15)

### Mechanical integration

Use the exact [2D mechanical drawing p.44](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf#page=44) or [CAD V1.1](https://doc.orbbec.com/attachments/18). The mounting provisions are a bottom 1/4-20 UNC point, two bottom M3 points and two rear M3 points. Choose screw engagement from the drawing and actual bracket thickness; do not let a long screw bottom out against the camera. Keep both stereo apertures clear and avoid twisting the housing when tightening.

The published dimension drawing shows the optical datum, which is distinct from the bracket face. The depth zero plane is documented **3.95 mm behind the front glass**, before and after supported depth-to-color alignment. Use calibration, not a guessed front-face distance, when comparing against a reference plane. Route the wrist cable with a service loop, strain relief and clearance from pinch points. [Depth datum p.29](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf#page=29)

IP54 applies only with the specified properly mated connector. Do not unplug or operate an unsealed receptacle wet. Provide airflow or a conductive heat path to stay within the disparity-dependent ambient limit; an enclosing wrist cover changes that thermal environment.

## Software and development resources

Use [**Orbbec SDK v2.10.6**](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6) and matching Viewer. Its support table lists Gemini 305 minimum firmware **1.0.30** and recommends **1.0.70**; the newer official firmware page lists **1.1.20**, released 23 October 2026, paired with SDK **2.10.6** for 305/305g. This is a later firmware-page recommendation than the frozen SDK README; record the actual pair, and do not interpret the older README as a maximum version. [Pinned support matrix](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/README.md#14-supported-devices), [305 firmware releases](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305)

The manual recommends Windows 10/11 or Ubuntu 22.04/24.04, USB 3, and x64 or supported ARM hosts. Choose the actual architecture package; Jetson CPU support does not create a GMSL path for this USB model. The SDK provides C/C++ APIs; Python and ROS wrappers have their own branch/version requirements.

### Acquisition choices and calibrated geometry

The manual separates **Depth + Color** and **Dual Color** combinations. Choose the needed mode before starting streams. Start with default depth/color rather than changing exposure, disparity search and alignment simultaneously. Auto-exposure priority may lower delivered frame rate to maintain exposure; inspect timestamps and exposure metadata before treating a lower rate as USB failure. [Stream combinations pp.19–21 and controls pp.32–33](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)

Read per-device calibration and use the supported hardware/software alignment combinations. Deproject depth with the active profile's intrinsics and scale; image-size matching alone does not align streams. Optical axes are X right, Y down and Z forward. A zero depth sample is invalid. Filters can alter edges or retain temporal history, so keep raw data and processing settings for a measurement or hand–eye calibration record. Coordinate and transform SDK examples are available in the [shared official SDK examples](https://github.com/orbbec/OrbbecSDK_v2/tree/v2.10.6/examples).

## Getting started

### First passive-stereo result with the robot stationary

1. Secure the camera on a stable mount, keep robot motion disabled, and place a visibly textured matte target **20–30 cm** from the front. Use diffuse visible lighting; avoid a glossy plain object as the first test.
2. Connect its USB cable to a sufficient 5 V USB 3 source. On Linux check `lsusb -d 2bc5:0840` and `lsusb -t`; install the release's udev rules if access is denied, then reconnect.
3. Install matching SDK/Viewer for the host. Open Viewer, confirm **Gemini 305**, serial number and firmware. Record the firmware before considering any update.
4. Select the normal depth/color acquisition configuration and default disparity search. Start **1280 × 800 Y16 depth at 30 fps**, initially with color off. Enable auto exposure and allow it to settle on the textured target.
5. Check that depth changes when moving the target within the ideal range. Add color at an advertised profile and inspect alignment/calibration. Stop all streams before changing mode or search range.
6. Save a short recording or screenshot with profile, disparity, exposure, firmware and measured target distance. Only after this stationary check should hand–eye calibration and robot integration begin.

**Expected result:** Viewer identifies the USB 305 and shows coherent depth on the textured target, with plausible centimetre-scale distance. A uniform or dark region may remain invalid; improving visible texture/light is a model-specific diagnostic, not evidence that an infrared laser must be enabled. [Initialization p.40](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf#page=40)

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

**Expected result:** the process prints six measurement records and exits successfully after receiving 60 depth frames. Each record includes a frame index, `timestamp_us`, valid sample count and `median_mm`; a diffuse target at 20–30 cm should give a plausible distance near its measured plane position. Those are expected results, not recorded measurements. An unsupported-profile error means enumerate/select a profile the device actually advertises; do not substitute a color format or interpret compressed depth bytes as Y16. Return code 3 means camera selection was ambiguous; 4 means too few frames arrived. A full invalid patch is reported explicitly rather than treated as zero metres.

## Troubleshooting and FAQs

| Symptom                                   | Check and supported next action                                                                                                                           |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB device missing                        | Check cable data capability, VID:PID, port power and udev access; reconnect after closing other camera applications                                       |
| Connected at USB 2                        | Remove an extension/hub bottleneck and confirm SuperSpeed; USB 2 full-resolution combinations are reduced, so 30 fps is not a valid expectation there     |
| No depth on a white object                | Add visible texture or change target/light; this passive color stereo model does not gain texture from a 335-style infrared projector                     |
| Object vanishes near the lens             | Back away into 7–50 cm first; 4 cm requires 848 × 530 and disparity 256, with a lower ambient ceiling                                                     |
| Frame rate falls in dim light             | Inspect auto-exposure priority and exposure duration; improve illumination before forcing gain or changing USB settings                                   |
| Dual-color/depth combination unavailable  | Consult the separate stream-combination tables; do not assume every stream mode can run simultaneously                                                    |
| Depth offset versus ruler                 | Measure from the documented optical datum, inspect scale, alignment, lens obstruction and calibration; keep the camera and target rigid                   |
| Update interrupted or device unresponsive | Reconnect a stable power/data cable, use exact supported 305 firmware in Viewer, stop streams before update and check firmware after the automatic reboot |

**Does the camera report wrist pose?** No. It reports sensor data; the robot's kinematics, camera mounting transform and hand–eye calibration are separate inputs.

**Is IP54 guaranteed by any USB-C cable?** No. The manual conditions it on a matching sealed receptacle/cable connection and proper seating. The unmated port is not protected.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                             | Purpose                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| [Gemini 305 datasheet V1.0 PDF](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)                                                                                        | Complete optics, streams, timing, coordinate, performance, supply, integration and mechanical reference |
| [CAD V1.1 ZIP](https://doc.orbbec.com/attachments/18)                                                                                                                                                                                | Official model-specific 2D/3D files; the source page labels these for evaluation                        |
| [Firmware 1.1.20 binary](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini305_v1.1.20.bin) / [release table](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305) | Confirm the supported-product and SDK row before selecting the image                                    |
| [Firmware changelog PDF](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20305%20Series%20Firmware_changelog.pdf)                                                                                                    | Changes across the 305/305g firmware series                                                             |
| [SDK v2.10.6](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6)                                                                                                                                                           | Viewer, libraries and examples                                                                          |
| [305 document center](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation)                                                                                                                                             | Current datasheets, CAD, firmware, regulatory certificates and SDK resources                            |
| [Python](https://github.com/orbbec/pyorbbecsdk) / [ROS 2](https://github.com/orbbec/OrbbecSDK_ROS2) wrappers                                                                                                                         | Additional integration routes with their own version matrices                                           |

### Extended official documentation

These official readers retain the detailed model/concept/sample paths. Use the model and release boundaries above before adapting an advanced example.

| Official reader                                                                                                                                                                            | Relevant guide section             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [Firmware Release of Gemini 305](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305)                                                 | Downloads and technical documents  |
| [Regulatory Compliance and Certificates of Gemini 305](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Regulatory%20Compliance%20and%20Certificates%20of%20Gemini%20305) | Downloads and technical documents  |
| [Gemini 305 Documentation](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation)                                                                                              | Software and development resources |
| [Download CAD Files of Gemini 305](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Download%20CAD%20Files%20of%20Gemini%20305)                                           | Downloads and technical documents  |

## References and validation

Reviewed **24 November 2026**. Hardware scope is Gemini 305 datasheet V1.0; code API scope is Orbbec SDK v2.10.6. The manual's unfinished cross-references for detailed installation/cable tutorials are not treated as available documents; exact drawings, public SDK sources and explicit first-result steps are provided instead. No public full hardware schematic was found.

Original code and procedures were source reviewed. **SDK execution and hardware testing were not run.** All target distances and console results above are proposed acceptance checks, not bench observations. Official files and illustrations remain attributed to Orbbec and are not relicensed by this guide.

### Reviewed engineering reference chapters

The following chapters preserve the existing wiki’s detailed engineering reference: specifications, calibration and coordinate concepts, metadata, filter behavior, source examples, installation procedures, troubleshooting and manufacturer illustrations. They complement the current commissioning guide above. Revision notes beside affected chapters separate historical SDK or host examples from the model-specific power, firmware and first-result path. No historical command, example output or photograph is a claimed test on this unit.

### Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting <a href="#reference-orbbec-gemini-305-range-stereo-vision-camera-for-robotic-wrist-mounting" id="reference-orbbec-gemini-305-range-stereo-vision-camera-for-robotic-wrist-mounting"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

[Original store reference](https://openelab.io/products/orbbec-gemini-305-range-stereo-vision-camera)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-1.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-2.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-3.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-4.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-5.jpg?v=1781599183)

![Official Orbbec Gemini 305 Range Stereo Vision Camera for Robotic Wrist Mounting product figure](https://cdn.shopify.com/s/files/1/0621/0050/4774/files/ORBBEC-Gemini-305-6.jpg?v=1781599183)

#### Gemini 305 <a href="#gemini-305" id="gemini-305"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

This reference concerns the USB Gemini 305, not the deeper 305g GMSL camera. The V1.0 model document separates imaging modes, disparity-dependent near limits, power, temperature, installation and recovery; keep those conditions together when reproducing a wrist-camera setup.

#### 0 Glossary <a href="#id-0-glossary" id="id-0-glossary"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

Terms Descriptions ASIC Application-specific Integrated Circuit Baseline The distance between the optical centers of the two cameras used for depth calculation D2C Depth to Color maps each pixel on a depth map to the corresponding color image according to the intrinsic and extrinsic parameters of the depth camera and color camera Depth Depth video streams are similar to color video streams except each pixel has a value representing the distance away from the sensor instead of color information Depth Camera Includes depth imaging module and external interface, of which the former is generally composed of an infrared projector, infrared camera, and depth computing processor FOV Field of View describes the angular extent of a given scene that is captured by a camera, which can be measured in the horizontal, vertical, and diagonal I2C Refers to a simple bi-directional two-wire synchronous serial bus developed by Philips IR Light in the infrared spectrum, which ranges from 700 nm and above IR Camera A camera capable of seeing light in the IR spectrum ISP Image signal processor, which is used for image post-processing PCBA PCBA (Printed Circuit Board Assembly) refers to a fully assembled printed circuit board (PCB) that includes all the electronic components mounted and soldered onto it. Point Cloud A discrete set of data points in space RGB Camera A camera that captures color images and video. ROI Region of Interest (ROI) in image processing refers to a specific area selected from the entire image SOM A System on Module (SoM) provides various core components of an embedded processing system on a single printed circuit board, including the processor core, communication interfaces, and memory modules. A typical example of this is the NVIDIA Jetson series products

SBC A Single Board Computer (SBC) is a microcomputer where all the logic circuits, timing circuits, internal memory, and external interfaces are integrated onto a single printed circuit board. A typical example is the Raspberry Pi SoC System on Chip, an integrated circuit (IC) that integrates all components of a computing system UVC USB Video Class (UVC) is a protocol standard defined for USB video capture devices and has become one of the USB.org standards Not specified in the cited revision To Be Determined. Information will be provided in a later revision.

#### 1 Product Brief <a href="#id-1-product-brief" id="id-1-product-brief"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

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

#### 2 Product Specifications <a href="#id-2-product-specifications" id="id-2-product-specifications"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

Parameter Gemini 305 Use Environment Indoor & Outdoor Technology Stereo Vision Baseline 18mm Operating Range\[1] \[2] 4 – 100cm Ideal Range 7 – 50cm Spatial Precision ≤ 1% (1280 x 800 @ 50cm & 90% x 90% ROI) Depth Resolution @ Frame Rate Up to 1280 x 800 @ 30fps 848 x 530 @ 60fps Depth FOV H 88° x V 65° ± 3° (1280 x 800 @ 20cm) Depth Filter IR-Cut Sensor Type Stereo Color: Global Shutter Color Resolution @ Frame Rate Up to 1280 x 800 @ 60fps Color FOV H 94° x V 68° ± 3° Depth Processing Orbbec MX6800 ASIC Data Connection USB 3.0 (recommended) & USB 2.0 Interface USB Type- C EMC ESD：Class A Contact discharge: ± 8kV, Air discharge: ± 15kV RE：≥6 dB Max Average Power Consumption ≤2.0W Power Supply DC 5V & ≥700mA Operating Environment -10 - 45°C @ 128 disparity search range -10 - 40°C @ 256 disparity search range Operating Backside Case Temperature -10℃ - 60℃ Storage Environment Short Term: -20℃ - 70℃, 5%\~90% RH (non-condensing) Long Term: 0℃ - 60℃, 5%\~90% RH (non-condensing)

Protection IP54 (only when the Type-C interface is properly connected and the screws are tightened) Dimensions(W x H x D) 42 x 42 x 23mm Weight 68g Installation Bottom:1x 1/4-20 UNC, 2x M3 Back :2x M3 Lifespan 5 Years: Default Operating Mode & Operating Environment

Notes: \[1] The depth performance of each 3D camera is validated at the production line before shipping to customers. The metrics reflect the depth performance under typical conditions. External impact factors over 3D cameras’ whole lifespan may have significant impacts on their depth performance. \[2] 4cm @ 848 x 530, with the max disparity search range of 256 pixels enabled.

#### 3 Product Information <a href="#id-3-product-information" id="id-3-product-information"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 3.1 Product Pictures <a href="#id-3.1-product-pictures" id="id-3.1-product-pictures"></a>

Table 3-1-1 Product pictures for Gemini 305 Front View

Rear View

Top View

Bottom View

Left View

Right View

Left Side View at 45°

Right Side View at 45°

#### 3.2 Product Drawings <a href="#id-3.2-product-drawings" id="id-3.2-product-drawings"></a>

**3.2.1 Product Drawings**

Table 3-2-1 Product drawings for Gemini 305 Name Gemini 305 Front View

Rear View

Top View

Bottom View

Side View

**3.2.2 Product Dimensions & Weight**

Table 3-2-2 Product dimensions & weight for Gemini 305 Name Gemini 305 Width/mm 42 Height/mm 42 Depth/mm 23 Net Weight/g 68

#### 3.3 Product Interfaces <a href="#id-3.3-product-interfaces" id="id-3.3-product-interfaces"></a>

Table 3-3-1 Product interfaces Name Gemini 305 Gemini 305 USB Type-C

Interface Pin Map

Table 3-3-2 USB Type-C Interface Definition Pin Name Definition Pin Name Definition A1 GND Ground B1 GND Ground A2 TX1+ High-speed Differential Signaling#1, TX, Positive B2 TX2+ High-speed Differential Signaling#2, TX, Positive A3 TX1- High-speed Differential Signaling#1 TX Negative B3 TX2- High-speed Differential Signaling#2 TX Negative A4 VBUS Power B4 VBUS Power A5 CC1 Port configuration B5 CC2 Power configuration A6 D+ USB2.0 Differential Signaling#1, Positive B6 D+ USB2.0 Differential Signaling#2, Positive A7 D- USB2.0 Differential Signaling#1, Negative B7 D- USB2.0 Differential Signaling#2, Negative A8 SBU Sideband use, 1.8V(Default), 3.3V, 5V; SYNC\_IN (Default) or SYNC\_OUT B8 SBU Sideband use, 1.8V(Default), 3.3V, 5V; SYNC\_IN (Default) or SYNC\_OUT A9 VBUS Power B9 VBUS Power A10 RX2- High-speed Differential Signaling#2 RX Negative B10 RX1- High-speed Differential Signaling#1 RX Positive A11 RX2+ High-speed Differential Signaling#2 RX Positive B11 RX1+ High-speed Differential Signaling#1 RX Negative A12 GND Ground B12 GND Ground

#### 3.4 Product Components <a href="#id-3.4-product-components" id="id-3.4-product-components"></a>

**3.4.1 Overview of Product Components**

Table 3-4-1 Overview of product components for Gemini 305 Gemini 305

**3.4.2 RGB Module**

Table 3-4-2 RGB module specifications Parameters Gemini 305 Filter Type IR-Cut Active Pixels 1280 x 800 Sensor Aspect Ratio 16:10 Focus Type Fixed Shutter Type Global Shutter Horizontal FOV 94° Vertical FOV 68° Diagonal FOV 104° FOV Tolerance ± 3.0° Distortion <1.5%

#### 4 Functional Specifications <a href="#id-4-functional-specifications" id="id-4-functional-specifications"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 4.1 Vendor Identifier (VID) and Product Identifier (PID) <a href="#id-4.1-vendor-identifier-vid-and-product-identifier-pid" id="id-4.1-vendor-identifier-vid-and-product-identifier-pid"></a>

Table 4-1-1 VID & PID table Name Gemini 305 Model G40351-191 PID 0x0840 VID 0x2BC5

#### 4.2 Platform and System Requirements <a href="#id-4.2-platform-and-system-requirements" id="id-4.2-platform-and-system-requirements"></a>

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

Table 4-2-1 Gemini 305 Recommended Platforms and Systems Architecture x86/x64 ARM OS Windows 10/11 Ubuntu 22.04 / 24.04 Ubuntu 22.04 / 24.04 and above USB USB 3.0 USB 3.0 USB 3.0 CPU Quad-core, 2.9GHz Quad-core, 2.9GHz Quad-core, A57 Reference model Intel i5 / Intel i7 Intel i5 / Intel i7 NVIDIA Jetson Orin Nano / NVIDIA Jetson Orin NX / NVIDIA Jetson AGX Orin / NVIDIA Jetson Thor RAM 8GB RAM and above 4GB RAM and above 4GB RAM and above

#### 4.3 Camera system Framework <a href="#id-4.3-camera-system-framework" id="id-4.3-camera-system-framework"></a>

Figure 4-3-1 Gemini 305 System Block Diagram

#### 4.4 Image Data Stream <a href="#id-4.4-image-data-stream" id="id-4.4-image-data-stream"></a>

Gemini 305 provides high-quality, multi-resolution depth data, as well as high- definition color data. The camera outputs depth data in Y16 format., and the color data in MJPEG / YUYV format. The SDK supports a comprehensive set of data conversions among MJPEG / YUYV / RGB8 / BGR8 / RGBA8 / BGRA8 / Y16 / Y8 formats. The camera outputs IR image data in Y8 format. Gemini 305 offers two image data stream combinations: "Depth + Color" and "Dual Color." The output combination is determined by the device's preset configuration: selecting the "Dual Color" preset outputs dual color streams, while any other preset outputs the "Depth + Color" data stream. Users can switch the data stream output with one click by changing the depth preset.

**4.4.1 “Depth + Color” Combinations**

Table 4-4-1 “Depth + Color” Output data streams (USB3.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Depth Y16 16:10 1280 x 800 5, 10, 15, 30 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60 IR Y8 16:10 1280 x 800 5, 10, 15, 30 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60 Color YUYV/Y8/Y16/ MJPEG/RGB8 /BGR8/BGRA 8/RGBA8 16:10 1280 x 800 5, 10, 15, 30, 60 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30, 60 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60

Table 4-4-2 “Depth + Color” Output data streams (USB2.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Depth Y16 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30

IR Y8 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30 Color YUYV/Y8/Y16/ MJPEG/RGB8 /BGR8/BGRA 8/RGBA8 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30

**4.4.2 “Dual Color” Combinations**

Table 4-4-3 “Dual Color” Output data streams (USB3.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Color Left YUYV/Y8/Y16/ MJPEG/RGB8/ BGR8/BGRA8/ RGBA8 16:10 1280 x 800 5, 10, 15, 30, 60 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30, 60 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60 Color Right YUYV/Y8/Y16/ RGBA8/RGB8/ BGR8/BGRA8/ 16:10 1280 x 800 5, 10, 15, 30, 60 848 x 530 5, 10, 15, 30, 60 16:9 1280 x 720 5, 10, 15, 30, 60 848 x 480 5, 10, 15, 30, 60 4:3 640 x 480 5, 10, 15, 30, 60

Table 4-4-3 “Dual Color” Output data streams (USB3.0)-Gemini 305 Gemini 305 Data Format Aspect Ratio Resolution Frame Rate Color Left YUYV/Y8/Y16/ MJPEG/RGB8/ BGR8/BGRA8/ RGBA8 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30 Color Right YUYV/Y8/Y16/ RGBA8/RGB8/ BGR8/BGRA8/ 16:10 1280 x 800 5, 10 848 x 530 5, 10, 15 16:9 1280 x 720 5, 10 848 x 480 5, 10, 15 4:3 640 x 480 5, 10, 15, 30

#### 4.5 Hardware Decimation <a href="#id-4.5-hardware-decimation" id="id-4.5-hardware-decimation"></a>

The Gemini 305 supports configurable hardware decimation for proportional image scaling. This process performs pixel merging and aggregation at the hardware level, reducing the image resolution in both X and Y dimensions while preserving the original aspect ratio. The camera directly outputs the resulting lower-resolution image stream. By utilizing hardware decimation, the Gemini 305 significantly reduces data transmission bandwidth and power consumption while maintaining the depth accuracy inherent to its full sensor resolution. Table 4-5-1 Gemini 305 Hardware Decimation Resolution Before Decimation Decimation Factor Resolution After Decimation 1280 x 800 2 640 x 400 3 424 x 266 4 320 x 200

1280 x 720 2 640 x 360 3 424 x 240 4 320 x 180 848 x 480 2 424 x 240 640 x 480 2 320 x 240

#### 4.6 Depth to Color Alignment <a href="#id-4.6-depth-to-color-alignment" id="id-4.6-depth-to-color-alignment"></a>

Depth to Color, a pixel-by-pixel geometric transformation of a depth image, results in the spatial alignment of a depth image with its corresponding color image through the D2C transformation, allowing us to locate any pixel of a color image by its image coordinates in the depth image after D2C by the same image coordinates. The depth information of the color pixel can be located in the depth image after D2C by using the same image coordinates. We generate a depth image of the same size as the target color image after D2C, and the image content is the depth data in the color camera coordinate system. In other words, a depth image is reconstructed that is "taken" using the origin and size of the color camera, where each pixel matches the coordinates of the corresponding pixel of the color camera. Table 4-6-1 Gemini 305 Depth to Color Alignment by software Depth Image before D2C Color Image Depth Image After D2C Aspect Ratio 1280 x 800 / 1280 x 720 / 848 x 530 / 848 x 480 / 640 x 480 1280 x 800 1280 x 800 16:10 848 x 530 848 x 530 1280 x 800 / 1280 x 720 / 848 x 530 / 848 x 480 / 640 x 480 1280 x 720 1280 x 720 16:9 848 x 480 848 x 480 1280 x 800 / 1280 x 720 / 848 x 530 / 848 x 480 / 640 x 480 640 x 480 640 x 480 4:3

Table 4-6-2 Gemini 305 Depth to Color Alignment by hardware Depth Image before D2C Color Image Depth Image After D2C Aspect Ratio 848 x 530 / 848 x 480 / 640 x 480 1280 x 800 1280 x 800 16:10 848 x 530 848 x 530 848 x 530 / 848 x 480 / 640 x 480 1280 x 720 1280 x 720 16:9 848 x 480 848 x 480 848 x 530 / 848 x 480 / 640 x 480 640 x 480 640 x 480 4:3

#### 4.7 Field of View <a href="#id-4.7-field-of-view" id="id-4.7-field-of-view"></a>

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

#### 4.8 Minimum-Z Depth <a href="#id-4.8-minimum-z-depth" id="id-4.8-minimum-z-depth"></a>

The Minimum-Z Depth is the minimum distance from the depth camera to the scene. Table 4-8-1 Minimum-Z Depth for Gemini 305 Disparity search range H / V-FOV: 88° / 65° H / V-FOV: 88° / 60° H / V-FOV: 77° / 65° 1280 x 800 848 x 530 1280 x 720 848 x 480 640 x 480 256 50mm 40mm 50mm 40mm 40mm 128 90mm 60mm 90mm 60mm 55mm 64 180mm 120mm 180mm 120mm 110mm

> Note:

1. The larger the disparity search range, the closer the minimum working distance becomes, and the higher the power consumption. Conversely, the smaller the disparity search range, the farther the minimum working distance extends, the lower the camera's power consumption, and the higher the ambient temperature it can withstand. 2. The disparity search range of 256 is only supported in the ”Close-Range” presets.
2.  #### 4.9 Coordinate System <a href="#id-4.9-coordinate-system" id="id-4.9-coordinate-system"></a>

    For the Gemini 305 3D camera, the plane where the 1/4 screw hole is located is defined as the bottom side, the glass cover surface is the front side and the area of the Type- C port is the left side. The positive X-axis of the coordinate system points to the right, the positive Y-axis points downwards, and the positive Z-axis points forwards. The origin of the depth image coordinate system and the origin of the color image coordinate system is at the optical center of the left RGB module. The direction of the coordinate systems is the same: the positive X-axis points to the right, the positive Y- axis points downward, and the positive Z-axis points forward. The depth camera coordinate system origin is the default origin of the 3D camera, with coordinates (0,0,0). The reference positions of the depth origin and color origin in the 3D camera coordinate system are shown in the chart below:

    Table 4-9-1 Gemini 305 Coordinate System Position Reference Coordinate System Origin in the 3D camera coordinate system X mm Y mm Z(mm) Depth 0 0 0 Color 0 0 0

    Table 4-9-2 Gemini 305 Coordinate System Schematic Gemini 305 Depth

    RGB

#### 4.10 Depth Start Point Reference <a href="#id-4.10-depth-start-point-reference" id="id-4.10-depth-start-point-reference"></a>

The depth start point, or ground zero reference can be described as a reference point or plane with depth = 0. For the Gemini 305 3D camera, the distance of the depth zero point to the front cover glass of the camera is listed below for both before and after the D2C alignment. Table 4-10-1 Camera Depth Start Point Illustrations Camera Gemini 305 Before the D2C alignment (Z’) 3.95 mm After the D2C alignment (Z’) 3.95 mm Depth Start Point

#### 4.11 Streaming Mode <a href="#id-4.11-streaming-mode" id="id-4.11-streaming-mode"></a>

Gemini 305 provides flexible acquisition options for IR, Depth, and RGB image data. The most commonly used mode is the streaming mode. In this mode, users configure a target frame rate, resolution, and image format for IR, Depth, and RGB respectively, and then enable the corresponding streams in sequence. The camera acquires and outputs image data according to the configured target frame rate, resolution, and image format. Depending on the current camera configuration, users can select an appropriate frame rate for the application from the following predefined frame rate options: 5 fps, 10 fps, 15 fps, 30 fps, and 60 fps.

#### 4.12 Triggering Mode <a href="#id-4.12-triggering-mode" id="id-4.12-triggering-mode"></a>

{% hint style="info" %}
Match the exact camera, connector view and synchronization accessory before wiring. USB supply voltage is not the GPIO logic level. Retain source timing/units with recordings; first capture is free-running with optional sync disconnected.
{% endhint %}

The Gemini 305 supports two image acquisition modes: a fixed frame rate mode and a free-run triggering mode. In free-run triggering mode, the camera passively waits for an external trigger signal (e.g., a software command via USB) to capture each frame. Upon receiving a valid trigger, it completes a single acquisition and immediately resumes waiting for the next trigger. There is no fixed time constraint between consecutive triggers, allowing the interval to be arbitrarily set to achieve virtually any acquisition frequency. To ensure proper operation in this mode, the IR, Depth, and RGB sensors must be configured to a common fixed frame rate (e.g., 5, 10, 15, 30, or 60 fps). This setting determines the minimum allowable time between two triggers and thus the maximum effective triggering frequency. As summarized in Table 4-12-1, the camera will only respond to trigger signals that fall within this permissible range. Consequently, any trigger frequency within the valid range can be passively supported. Table 4-12-1 Table of Supported Trigger Configurations

3\. #### 4.13 Multi-Camera Synchronization

For a multi-camera use case, one camera can be initialized as primary, and the rest configured as secondary. Alternatively, an external signal generator can also be used as the primary trigger with all cameras set to secondary mode. When applying an external sync pulse, the HW SYNC input requires a 100-microsecond positive pulse at the nominal camera frame rate, e.g. 33.33 ms for a 30 Hz frame rate. Inputs are high impedance, 1.8V CMOS voltage levels. However, it is important to make sure to use a high-resolution signal generator. The frequency of the signal generator needs to exactly match the sensor frame rate. For example, if the sensor is set up as 30 FPS, the Set The Camera’s Fixed Frame Rate(fps) Supportable Passive Trigger Interval (ms) Supportable Passive Trigger Frequency (Hz) 60 ≥ 33.4 0 - 30 30 ≥ 66.7 0 - 15 15 ≥ 133.4 0 - 7.5 10 ≥200 0 – 5 5 ≥ 400 0 – 2.5

real frame rate may be 30.015 FPS. You may need to use an oscilloscope to measure the real frame rate and configure the signal generator to the same frequency. For this reason, it may be better to just use one additional camera as the primary sync signal generator. Advantages of multi-camera setup：

*   Increase camera coverage in a given space and fill in the occlusions where a

    single camera may have blind spots
*   Capture multiple images of the same scene and scan objects from different

    angles
*   Increase the effective frame rate to higher than 30 FPS when the cameras are

    running at 30 fps. Multi-camera frame synchronization in star topology is supported, including depth image synchronization and RGB image synchronization (typical time difference ≤ 5ms across synchronized multiple cameras, when auto exposure off), using the multi- camera synchronization function. Table 4-13-1 Topologies schematic diagram Star Topology

#### 4.14 Camera Functions <a href="#id-4.14-camera-functions" id="id-4.14-camera-functions"></a>

**4.14.1 Depth Camera Functions**

Gemini 305 expose the following Depth image settings. Table 4-14-1 Depth camera control Control Description Settings Default Setting Auto Exposure Priority When enabled, exposure is prioritized, allowing the frame rate to be reduced. Disabled, Enabled Enabled Auto Exposure Enables or disables automatic exposure control for the depth camera. Disabled, Enabled Enabled AE Max Exposure(us) Maximum correction value for AE exposure that limits the corresponding frame rate. 1 - 199000 30458(30fps) Mean Intensity Set Point Mean Intensity Set Point for Gemini 0 - 255 60 AE ROI AE ROI allows the user to specify a rectangular region. AE then performs exposure control based on the brightness of this region, enabling the target object to achieve a appropriate brightness. T:0 - 799, B:0 -799 L:0 - 1279, R:0 -1279 (Resolution:1280 x 800) T:0, B:799 L:0, R:1279 (Resolution:1280 x 800) Manual Exposure(1) (us) Sets the fixed exposure time when depth auto exposure is disabled. 1 - 199000 10000 Gain(Gain 1.0=16) Adjusts the gain applied to the depth image when auto exposure is disabled. 16 -248 16

4\.

> Note: (1) Not supported in Auto Exposure Mode

Definitions: T = Top, L = Left, B = Bottom, R = Right

**4.14.2 Color Camera Functions**

Gemini 305 expose the following Color image settings. Table 4-14-2 Color camera control Control Description Settings Default setting Auto Exposure Priority When enabled, exposure is prioritized, allowing the frame rate to be reduced. Disabled, Enabled Enabled Auto Exposure Enables or disables automatic exposure adjustment. Disabled, Enabled Enabled

AE Max Exposure (100us) Maximum correction value for AE exposure that limits the corresponding frame rate. 1999 303(30fps) AE ROI AE ROI allows the user to specify a rectangular region. AE then performs exposure control based on the brightness of this region, enabling the target object to achieve a appropriate brightness. T:0 - 779, B:0 -779 L:0 - 1279, R:0 -1279 (Resolution:1280 x 800) T:0, B:779 L:0, R:1279 (Resolution:1280 x 800) Manual Exposure(1) (100us) Sets the absolute exposure time when auto-exposure is disabled. 1 - 1999 156 Gain Sets the amount of gain applied to the frame if auto-exposure is disabled. 16 – 128 16 Brightness Sets the amount of brightness applied when auto-exposure is enabled. -64 – 64 0 Auto White Balance Enables or disables the AWB algorithm Disabled, Enabled Enabled White Balance/ K Sets the white balance when AWB is disabled 2800 – 6500 4600 Sharpness Sets the amount of sharpening adjustment applied to the frame 0 – 100 50 Gamma Adjusts gamma correction applied to image frames. Lower gamma values make the scene appear brighter. 100 - 500 300 Saturation Sets the amount of saturation adjustment applied to the frame 0 - 100 64 Contrast Sets the amount of contrast based on the brightness of the scene 0 - 100 50 Hue Sets the amount of hue adjustment applied to the frame -180 – 180 0 Backlight Compensation Sets a weighting amount based on brightness to the frame Disabled, Enabled Disabled Powerline Frequency Specified based on the local power line frequency for flicker avoidance Auto, 50, 60, Disabled Auto

> Note: (1) Not supported in Auto Exposure Mode

Definitions: T = Top, L = Left, B = Bottom, R = Right

#### 5 Performance <a href="#id-5-performance" id="id-5-performance"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 5.1 Depth Performance <a href="#id-5.1-depth-performance" id="id-5.1-depth-performance"></a>

**5.1.1 Depth Quality Assessment**

Calculation of Depth Accuracy (Z-accuracy): Depth accuracy (Z-accuracy) measures the per-pixel depth accuracy relative to the GT in a single frame depth image, excluding errors due to camera placement. GT is obtained by measuring the distance from depth origin to the reference target. Depth accuracy can be calculated using the following formula: Depth\_accuracy\_Signed = Median (CP\_Length – GT + PP\_Dist) where CP\_Length represents the actual length between the depth origin and a fitted plane along the GT measuring direction, and PP\_Dist denotes the per-pixel distance of the point cloud to the fitted plane. Calculation of Spatial Precision: The spatial precision is calculated as the percentage of the root mean square error (RMS Error) between each valid pixel and the optimal fitting plane compared to the true value (GT). Calculation of Temporal Precision: The temporal precision measures the variation in depth values over time within a ROI. The quality of a depth image can be assessed based on its temporal consistency, high-quality depth images should exhibit smooth and stable over time. This method is defined as the STD of depth values across a specific number of frames (for example, 30). The quantification of temporal noise is carried out on a per-pixel basis, followed by calculating the STD of each pixel over a specified time. Depth Fill Rate Calculation: The fill rate is used to calculate the proportion of valid pixels to total pixels within the target area (ROI region), primarily used to measure the completeness of depth.

5\. **5.1.2 Typical depth performance**

Typical depth performance for Gemini 305 is shown in the table below: Table 5-1-1 Typical Depth Performance for Gemini 305 Depth Performance Gemini 305 Depth Accuracy ≤±1.8% (1280 x 800 @ 50cm & 90% x 90% ROI) Spatial Precision ≤ 1% (1280 x 800 @ 50cm & 90% x 90% ROI) Temporal Precision ≤ 0.5% (1280 x 800 @ 50cm & 90% x 90% ROI) Fill Rate ≥99.5% (1280 x 800 @ 50cm & 90% x 90% ROI)

> Note:

1. The actual working range and accuracy may vary with the ambient illumination and the objects being measured. 2. The test object is a reflectivity > 80% plane, and the reference range is 81% FOV (81% FOV is the remaining center 81% of the depth map area after cropping 5% from the top, bottom, left and right of the depth map) or 64% FOV (64% = 80% x 80% and of a similar definition).
2. The depth performance of each 3D camera is validated at the production line before shipping to customers. The metrics reflect the depth performance under typical conditions. External impact factors over 3D cameras’ whole lifespan may have significant impacts on their depth performance. 4. Depth evaluation for the Gemini 305 passive RGB stereo vision requires textured or feature-rich objects.

#### 5.2 Electrical Performance <a href="#id-5.2-electrical-performance" id="id-5.2-electrical-performance"></a>

**5.2.1 Power Supply**

The Gemini 305 requires Type-C power and it is important to ensure that the power output is standard and that the maximum current of the Type-C power port is 0.7A or higher.

**5.2.2 Power Consumption**

Power consumption varies depending on the selected working mode. Table 5-1-1 Gemini 305 typical configuration & tested power consumption Reference Name Gemini 305 Typical configuration Max disparity search range: 128 Depth: 1280 x 800 @ 30 fps Y16 IR Left & IR Right: 1280 x 800 @ 30 fps Y8 RGB: 1280 x 800 @ 30 fps YUYV AE: On Hardware Noise Removal: on Average power consumption 1.57 W

Table 5-1-2 Gemini 305 Max Power Configuration & tested power consumption Reference Name Gemini 305 Max Power Configuration Max disparity search range: 256 Depth: 1280 x 800 @ 30 fps Y16 IR Left & IR Right: 1280 x 800 @ 30 fps Y8 RGB: 1280 x 800 @ 30 fps YUYV AE: On Hardware Noise Removal: on Average power consumption 1.88 W \*Note: The data in the above table are laboratory measurements and are for design reference only.

**5.2.3 Storage and Powered Conditions**

Table 5-1-3 Gemini 305 Storage and Powered Conditions Condition Description Min Max Unit Storage (Ambient), Not Powered Long term storage -10 60 ℃ Short exposure represents temporary max limits acceptable for transportation conditions -20 70 ℃

Humidity Temperature / RH: 40℃ / 90% Ambient, Powered The camera ambient temperature when powered \[1] -10 45 ℃ Backside Case Temperature, Powered The maximum temperature of the backside case occurs when the camera is operated in an ambient temperature of 45°C 0 60 ℃ Notes: \[1] For the Gemini 305, the allowable operating temperature range varies depending on the disparity search mode setting: when the disparity search mode is set to 128, the operating temperature range is -10 °C to 45 °C; when the disparity search mode is set to 256, the operating temperature range is -10 °C to 40 °C. \[2] If users require operation over a wider temperature range, additional thermal management measures need to be evaluated.

**5.2.4 ESD Performance**

Table 5-2-3 Gemini 305 ESD Performance Conditions Powered-On Powered-Off Certification Standards Contact Discharge ± 8KV Class A ± 8KV Class A EN 61000-6-2 Air Discharge ± 15KV Class A ± 15KV Class A

#### 5.3 Physical Performance <a href="#id-5.3-physical-performance" id="id-5.3-physical-performance"></a>

**5.3.1 Ingress Protection**

Table 5-1 Gemini 305 Ingress Protection Information IP Rating Protection Ability Conditions Reference Standard IP54 ① Prevents solid objects from entering the camera. ② Cannot completely prevent dust from entering the inside of the camera, but the dust that does enter does not affect normal operation. When the Type-C receptacle is mated with a cable rated for IP54 protection and the connector is fully seated. The unmated receptacle is not ingress- protected. Do not operate or unplug under wet conditions. IEC 60529:2013

6. Firmware

#### 6.1 Firmware Update & Cautions <a href="#id-6.1-firmware-update-and-cautions" id="id-6.1-firmware-update-and-cautions"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

Gemini 305 supports update the firmware via online or location, you can upgrade or downgrade as needed. Please note the following considerations: 1. You can update the firmware in any operating mode or preset; 2. All data streams must be closed when update the firmware; 3. During the firmware update, please ensure that the power supply and cable connections are stable; 4. The camera will automatically reboot after the firmware update is completed. You can also re-plug the cable after completion and reboot it manually.

#### 6.2 How to Update Firmware <a href="#id-6.2-how-to-update-firmware" id="id-6.2-how-to-update-firmware"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

The simplest way to update the firmware is through the Orbbec Viewer tool, which supports both manual updates and online updates. For detailed instructions, please refer to the documentation: TBC

#### 6.3 Recovery <a href="#id-6.3-recovery" id="id-6.3-recovery"></a>

Ensure the stability of cable during the update process to avoid any failure. If the update process fails, disconnect the cable, re-connect it, and update the firmware again. If re-burning is unsuccessful, the product may be damaged. Orbbec assumes no liability for any damages or losses resulting from the use of this product.

7. SDK Orbbec SDK is a flexible and modular platform for easy camera setup and runs on multiple platforms with a rich set of APIs. It supports camera access, device setup and configuration, data stream reading, processing, and viewing, RGB-D registration, and frame synchronization. Its functions include:

* Access and control of camera devices
* Control of frame synchronization and alignment
* Acquisition of point cloud data
* Orbbec Viewer for camera testing and evaluation

Please visit Orbbec SDK for the latest SDK.

#### 7.1 Temperature Sensor and Recording <a href="#id-7.1-temperature-sensor-and-recording" id="id-7.1-temperature-sensor-and-recording"></a>

The temperature of camera core components can be obtained, including ASIC temperature, ISP temperature and RGB sensor temperature, through API commands.

8. Use Guidance

#### 8.1 Packing List <a href="#id-8.1-packing-list" id="id-8.1-packing-list"></a>

Table 8-1-1 Gemini 305 Package List Packaging Type Packaging List Gemini 305 Notes Bulk Camera

Minimum batch packaging quantity: 200pcs Box Camera

Minimum batch packaging quantity: 30pcs 1x USB-C to USB-A cable (1m) 1x Quick Start Guide

#### 8.2 Initialization and Operation <a href="#id-8.2-initialization-and-operation" id="id-8.2-initialization-and-operation"></a>

* Connect Gemini 305 via the USB cable to the host PC
* Download Orbbec SDK from Orbbec SDK
* Use Orbbec Viewer to validate that images can be streamed from all sensors

with the following settings: o Depth stream: 1280 x 800(default configuration) o Color stream: 1280 x 800(default configuration) The detailed quick start guide refers to the documentation: TBC If for any reason that the camera is not responding or not being detected, please unplug the cable from the camera and replug the cable into the host PC for resetting the camera state.

9. Regulatory Compliance These products are certified as follows:

#### 9.1 EMC Regulatory Compliance <a href="#id-9.1-emc-regulatory-compliance" id="id-9.1-emc-regulatory-compliance"></a>

CE-Declaration FCC part 15 Declaration of Conformity

#### 9.2 Environment Regulatory Compliance <a href="#id-9.2-environment-regulatory-compliance" id="id-9.2-environment-regulatory-compliance"></a>

RoHS 2.0, REACH, WEEE, TSCA, TPCH, 94/62/EC RoHS REACH WEEE

TSCA TPCH 94/62/EC

PASS PASS

10. System Integration Guide Use outside of the specified conditions could cause the device to fail and/or function incorrectly. These conditions are applicable for the environment immediately around the device under all operational conditions. When used with an external enclosure, active temperature control and/or other cooling solutions are recommended to ensure the device is maintained within these ranges.

#### 10.1 Installation Recommendations <a href="#id-10.1-installation-recommendations" id="id-10.1-installation-recommendations"></a>

1. When using external housing around the camera for dust proofing, use foam inserts or rubber gaskets between the front of the camera and the external housing. 2. Avoid external forces applied to the camera chassis during installation process. 3. Disassembling chassis will void the warranty. 4. For the detailed installation reference solution, please refer to Document: TBC

#### 10.2 Heat Dissipation <a href="#id-10.2-heat-dissipation" id="id-10.2-heat-dissipation"></a>

1. Avoid direct heat source around the camera. 2. Maximizing the space inside the external housing may help lower operating temperature.

#### 10.3 Cable Design Guide <a href="#id-10.3-cable-design-guide" id="id-10.3-cable-design-guide"></a>

1. It is recommended to use the included USB Type-C cable. If a longer cable is required, use a USB-IF-certified cable that supports both power and data. A cable length of 3.0 m or less is recommended.
2. For the detailed cable design guide reference solution, please refer to Document: TBC
3. Cautions 1. Follow the instructions carefully when operating the camera. Improper handling may lead to damage to the internal components. 2. Do not drop the camera or expose the camera to mechanical stress. 3. Do not attempt to modify the camera as such modifications may cause permanent damage or performance degradation. 4. The temperature of the camera may rise during long periods of use. 5. Do not touch the lens. Fingerprints on the lens may affect image quality. 6. Keep the product beyond the reach of children or animals to avoid accidents. 7. If the computer does not recognize the camera, verify that the cable meets the power and data transfer requirements, then replug it into the USB port to reconnect. Safety and Handling Instructions: ●Avoid powering on the product if any external damage was observed. ●Do not attempt to open any portion of this product. There are no user serviceable parts. ●To maintain compliance and safety standards, do not modify or service the product. Unauthorized modifications or servicing could result in emissions surpassing the Class 1 safety level. ●Only update the camera firmware with official releases that match the specific module SKU and revision to ensure proper functionality and safety.

#### Appendix A: Gemini 305 2D Mechanical Diagram <a href="#appendix-a-gemini-305-2d-mechanical-diagram" id="appendix-a-gemini-305-2d-mechanical-diagram"></a>

_Reviewed source:_ [_Orbbec\_Gemini 305 Datasheet V1.0\_20260105.pdf_](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)_. Manufacturer figures and source examples retain their original attribution and rights._

The [manufacturer’s dimensioned drawing on datasheet page44](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf#page=44) shows the housing, 18 mm stereo baseline, mounting faces and connector clearances. Use the drawing’s maximum screw-insertion depths and exact mating stack; do not infer thread engagement from the outside 42 mm housing dimension. The linked drawing was visually inspected; it is not a reconstructed diagram.

#### Development Resources <a href="#development-resources" id="development-resources"></a>

* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK ROS 1 wrapper](https://github.com/orbbec/OrbbecSDK_ROS1)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
* [Official Gemini 305 documentation](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation)
* [Gemini 305 firmware releases](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305)
* [Gemini 305 CAD files](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Download%20CAD%20Files%20of%20Gemini%20305)
* [Official Gemini 305 datasheet](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305%20Datasheet%20V1.0_20260105.pdf)
