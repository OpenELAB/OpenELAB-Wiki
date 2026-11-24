---
description: >-
  Match Gemini 305g power-over-coax, FAKRA cable, deserializer and JetPack
  driver before capturing close-range depth with the exact supported SDK and
  firmware.
---

# Orbbec Gemini 305g: GMSL2 wrist-camera integration

{% hint style="info" %}
[**Orbbec Gemini 305g GMSL2 Wrist Camera on OpenELAB**](https://openelab.io/products/orbbec-gemini-305g-wrist-camera)

**Model:** Gemini 305g · **SKU:** `ORBBEC-Gemini-305G` · **Option:** GMSL2/FAKRA wrist camera with USB evaluation interface; not the USB-only Gemini 305.
{% endhint %}

Gemini 305g is an 18 mm-baseline passive stereo camera for close-range robot perception, using global-shutter color sensors and onboard depth processing. Its production GMSL2 path requires a powered compatible deserializer and a matching Jetson/carrier driver; the Type-C port provides a separate initial evaluation path. This guide establishes depth before wrist motion or multi-camera integration.

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The 305g adds a GMSL2 serializer/FAKRA connection to the close-range stereo design. The [manufacturer product page](https://www.orbbec.com/gemini-305g/) and [official package listing](https://store.orbbec.com/products/gemini-305g) identify the FAKRA connection and supplied FAKRA-Z-to-FAKRA-Z cable. The rear mechanical drawing uses an SMB-family designation, so match the actual mating assembly rather than assuming another Gemini GMSL cable is mechanically identical.

The Type-C interface is documented for initial evaluation/configuration; it does not establish that a generic USB host is a GMSL receiver or that an open service-port setup meets IP65. The purchased camera does not include a Jetson, deserializer board, matched BSP or robot calibration. Compare [Gemini 305](orbbec-gemini-305-user-manual.md) for the lighter USB model and the [330-family guide](orbbec-gemini-330-series-user-manual.md) for different long-baseline models. [305g datasheet V1.1](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf)

## Applications

* Wrist-mounted observation of textured objects in the **7–50 cm** ideal working region, with cable retention and visible lighting appropriate to robot motion.
* Close-range object localization and grasp-planning research after depth scale and hand–eye calibration are independently verified.
* Embedded multi-camera systems using a documented GMSL2 deserializer/carrier/driver combination.
* Dual global-shutter color acquisition and depth/color evaluation with mode-specific stream combinations.

Stereo requires scene correspondence. Adequate light and texture matter even though the interface can carry a stable high-speed stream. Keep the arm disabled until the camera's transform, gripper occlusion, cable movement and perception failure behavior have been checked.

## Specifications

Hardware values below use [Gemini 305g Datasheet V1.1, pp.11–19 and 42–44](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf). Precision/range figures include configuration and target conditions.

| Parameter                         | Gemini 305g                                                                                                          |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Stereo / processing               | Passive global-shutter color stereo, 18 mm baseline / MX6800 onboard depth                                           |
| Working / ideal range             | 4–100 cm / 7–50 cm; 4 cm headline is tied to close-range disparity configuration                                     |
| Full-resolution depth             | 1280 × 800 at up to 30 fps                                                                                           |
| Higher-rate depth                 | 848 × 480 at up to 60 fps in summary; enumerate detailed transport/profile combinations                              |
| Color maximum                     | 1280 × 800 at up to 60 fps                                                                                           |
| Depth / color FOV                 | 88° × 65° ±3° at 20 cm, 1280 × 800 / 94° × 68° ±3°                                                                   |
| Spatial / temporal precision      | ≤1% / ≤0.5% at 50 cm, 1280 × 800, central 90% × 90% region, specified reflective textured plane                      |
| Accuracy / fill-rate test entries | ±1.8% / ≥99.5% at the same documented factory conditions; not a guarantee for every object                           |
| GMSL supply                       | **12 V DC, ≥0.5 A** capability through the compatible camera power-over-coax path                                    |
| USB evaluation supply             | **5 V DC, ≥0.7 A** capability                                                                                        |
| GMSL average / peak power         | ≤2.6 W / ≤3.2 W                                                                                                      |
| USB 3 average / peak power        | ≤2.1 W / ≤2.8 W                                                                                                      |
| Ambient                           | −10 to +45 °C at disparity search 128; −10 to +40 °C at search 256                                                   |
| Rear case / protection            | Up to 60 °C / IP65 only with correctly fitted GMSL2 connection, screws tightened and service-port sealing maintained |
| Size / mass                       | 42 × 42 × 40 mm / 116 g ±10 g                                                                                        |
| Mounting                          | Bottom 1/4-20 UNC and four M3 points; use exact drawing for other points and engagement                              |
| Model / USB evaluation VID:PID    | G40351-291 / `2bc5:0842`                                                                                             |

### Near limit is a resolution/disparity choice

| Disparity search range | 1280 × 800 / 1280 × 720 minimum-Z | 848 × 530 / 848 × 480 minimum-Z | 640 × 480 minimum-Z |
| ---------------------- | --------------------------------- | ------------------------------- | ------------------- |
| 64                     | 185 mm                            | 125 mm                          | 115 mm              |
| 128                    | 95 mm                             | 65 mm                           | 55 mm               |
| 256                    | 50 mm                             | 35 mm                           | 32 mm               |

This [V1.1 table, p.32](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf#page=32) describes geometric near limits, not guaranteed good measurements down to every listed millimetre. The specified ideal region remains a useful starting point. Wider disparity search increases processing/thermal demand. Start around 20–30 cm and verify texture/lighting before trying the closest configuration.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

![Official Orbbec Gemini 305g side view showing its USB evaluation interface and deeper housing](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/11/23121555/305g-EN.webp)

Official Orbbec exact-model illustration; use the linked V1.1 interface and mechanical drawings for connector and mounting details.

### GMSL2 is a complete powered host path

The production path is **camera → matching coax/FAKRA cable → compatible deserializer board → Jetson CSI interface → carrier-specific driver → SDK application**. It is not Ethernet, PoE, a USB cable adapter or a bare CSI ribbon connection. Use the supplied cable first; power off before mating the deserializer/camera. Provide the specified 12 V/≥0.5 A camera power domain through the supported board, plus the host/board's separate supply requirements. Do not inject a host's arbitrary 19/24 V supply onto camera coax.

The GMSL serializer multifunction-pin (MFP) table describes signals transported/configured through the SerDes design; these are **not numbered exposed pins on the coax plug**:

| Serializer MFP | Documented function                                                | Integration implication                                   |
| -------------- | ------------------------------------------------------------------ | --------------------------------------------------------- |
| MFP6           | SYNC\_IN, ≥1 ms active-high pulse in the serializer-to-camera path | Requires matching deserializer routing/configuration      |
| MFP7           | PPS input path                                                     | Timestamp-related feature; not a loose-wire connector pin |
| MFP8           | Camera power/restart control, low enables camera power             | Wrong routing can power-cycle the camera                  |
| MFP9           | SYNC\_OUT from camera to serializer                                | Requires supported multi-camera topology                  |
| MFP15 / MFP16  | I²C SDA / SCL                                                      | Mandatory deserializer/driver integration path            |

Use [V1.1 interface tables pp.15–17](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf#page=15) and the [official GMSL hardware design guide](https://github.com/orbbec/MIPI_Camera_Platform_Driver/blob/931a2d2414a0ac1afc959c6b125b2208c153d235/doc/GMSL%20Camera%20Board%20Hardware%20Design%20Guide.pdf). Do not apply a PLC signal directly to a conceptual MFP row. Detailed design needs the actual carrier/deserializer schematic and device-tree routing. The linked board-design PDF begins with a **335Lg-specific** camera chapter; its 335Lg power/pin details are not substituted for the 305g V1.1 camera tables. Its deserializer-board material is an integration reference.

### USB evaluation and sealing

For initial evaluation use USB 3 Type-C with 5 V/≥700 mA and the corresponding data cable, keeping GMSL power disconnected unless the exact hardware instructions permit simultaneous connections. USB SBU pins carry model-specific synchronization functions with 1.8 V default and configurable reference arrangements; a generic cable does not expose them as safe robot GPIO. Leave custom sync wiring out of the first test.

IP65 is conditional on the installed GMSL connector/fasteners and sealed service interfaces. The USB evaluation arrangement should not be assumed to retain that rating. For wrist mounting use the [2D drawing p.52](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf#page=52) and exact CAD; account for bracket thickness, connector clearance, bend radius and strain relief. Perform cable-motion checks with robot power/motion disabled before dynamic trials.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

### Match four separate versions

| Layer              | Verified requirement / selected scope                                                                                                 |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------- |
| Camera firmware    | SDK v2.10.6 table: 305g minimum/recommended **1.0.70** at release; later firmware **1.1.20** explicitly supports 305g with SDK 2.10.6 |
| Native camera SDK  | **Orbbec SDK v2.10.6**, correct Linux ARM64 or desktop package; v1 is not the 305g development target                                 |
| GMSL driver        | 305g support starts at **v1.2.12**; current reviewed driver README recommends **v1.2.21**                                             |
| Carrier/BSP/kernel | Must match the actual Jetson module, carrier, deserializer board and JetPack/kernel; a matching CPU name alone is insufficient        |

The [firmware release table](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305) names 1.1.20 for both 305 and 305g. [PCN 20261102001](https://www.orbbec.com/pcn/) records the factory update from 1.0.70 to 1.1.20. These newer records explain why a newly delivered unit can differ from the frozen [SDK v2.10.6 README](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/README.md#14-supported-devices).

### Supported GMSL reference combinations

The [reviewed driver commit](https://github.com/orbbec/MIPI_Camera_Platform_Driver/tree/931a2d2414a0ac1afc959c6b125b2208c153d235) explicitly lists Gemini 305G. Its guide identifies, among others:

| Reference combination                    | Deserializer module          | Software boundary                       |
| ---------------------------------------- | ---------------------------- | --------------------------------------- |
| AGX Orin developer kit + FG96\_8CH\_GMSL | MAX9296 / `obc_max9296.ko`   | Reference JetPack/BSP-specific package  |
| Orin NX developer kit + FG96\_2CH        | MAX9296 / `obc_max9296.ko`   | Separate carrier overlay/install script |
| AGX Orin + Leopard LI-JAG-ADP-GMSL2-8CH  | MAX96712 / `obc_max96712.ko` | Different CSI/overlay path              |

For the guide's **JetPack 6.2 example**, the kernel is **5.15.148-tegra**; its JetPack 6.0 example uses **5.15.136-tegra**. Do not mix their modules or DTBOs. JetPack 7.2 introduces a different kernel/OOT installation workflow. Commercial systems need the vendor's exact image/extension board; the [official supported-host matrix](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20%26%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements) does not certify an arbitrary carrier with the same SoM.

### Calibration, modes and transport restrictions

Keep the per-device intrinsics, optical datum, depth scale and camera-to-wrist transform. A stereo camera's factory depth/color calibration is not hand–eye calibration. Stop streams before changing acquisition mode or disparity search; the manual separates depth/color and dual-color combinations. Auto-exposure priority may lower delivered frame rate in dim light.

The driver README limits GMSL to its V4L2 path and YUYV color transport rather than MJPEG. Data nodes and metadata nodes are not interchangeable. Paired deserializer links share stream/bandwidth restrictions, and MAX96712 synchronized-secondary operation needs the expected trigger; do not enable that mode for an uncabled first test. Validate one camera/free-running stream before multiple cameras or external synchronization. [Driver limitations](https://github.com/orbbec/MIPI_Camera_Platform_Driver/blob/931a2d2414a0ac1afc959c6b125b2208c153d235/README.md)

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result through the documented USB evaluation interface

1. Keep the robot stationary and place a textured, visibly illuminated matte target **20–30 cm** from the camera. Confirm the label is **305g** and prepare the USB evaluation cable and 5 V/≥700 mA source.
2. With GMSL power disconnected, connect USB 3 directly. On Linux inspect `lsusb -d 2bc5:0842` and `lsusb -t`; apply release udev rules and reconnect if device access is denied.
3. Install/open **Orbbec Viewer v2.10.6** for the host architecture. Record model, serial and installed firmware; check it against the 305g support row, not the earlier USB 305-only firmware row.
4. Start the normal depth/color configuration with default disparity search and **1280 × 800 Y16 depth at 30 fps**, initially depth alone. Keep the target away from the geometric near limit.
5. Verify the target plane and add color at a supported profile. Stop streaming before changing disparity/mode; save a short clip and the exact settings.

**Expected result:** Viewer recognizes **Gemini 305g** over USB and displays coherent near-field depth on the textured target. This proves the USB evaluation path, not a working GMSL carrier/driver or an IP65 moving-arm installation. [V1.1 USB evaluation scope and initialization](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf)

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

### GMSL bring-up on the documented reference host

1. Choose one exact reference stack, for example **AGX Orin developer kit + FG96\_8CH\_GMSL + JetPack 6.2 / 5.15.148-tegra**, with a 305g-capable driver ≥1.2.12. Before installing anything, record the target system:

```bash
cat /etc/nv_tegra_release
uname -r
```

2. Obtain the matching precompiled package or follow the pinned [G300 build/package guide](https://github.com/orbbec/MIPI_Camera_Platform_Driver/blob/931a2d2414a0ac1afc959c6b125b2208c153d235/doc/Orbbec_G300_Series_GMSL_Camera_Driver_Quick_Start_Guide.md). Verify kernel/board/metadata-layout correspondence and preserve the vendor's original boot image/modules/DTBO and recovery path. Do not apply the developer-kit package to a commercial carrier solely because it uses AGX Orin.
3. For that exact AGX Orin/FG96 reference package, the guide's regular target script is **`sh copy_to_target_agx_orin_fg96.sh`**, run from its **`gmsl-driver-jetson`** package directory. The `nomtd` script is a different metadata layout, not a generic fallback. The documented JetPack 6 installation replaces boot/kernel components; follow it only after the exact match and recovery backup are established. Reboot after the matched installation.
4. Power down before connecting the camera's GMSL cable and board power; then boot the prepared host. Check the installed modules, logs and actual video-node names rather than assuming `/dev/video0` is depth:

```bash
lsmod | grep -E 'g300|obc_max9296|obc_max96712|obc_cam_sync'
dmesg | grep -iE 'g300|orbbec|max9296|max96712'
v4l2-ctl --list-devices
```

5. Identify the image node for the connected port from its driver/device listing. Replace the node below with the **observed image node**, inspect its formats and capture 30 buffers without changing firmware/calibration:

```bash
export CAMERA_NODE=/dev/videoX
v4l2-ctl -d "$CAMERA_NODE" --list-formats-ext
v4l2-ctl -d "$CAMERA_NODE" --stream-mmap --stream-count=30 --stream-to=305g-node.raw
wc -c 305g-node.raw
```

6. Close the raw capture and open the matched ARM64 Orbbec Viewer on the Jetson's graphical session. Confirm exact model/serial and select an enumerated free-running depth profile. Compare against the USB baseline before adding streams, metadata layouts or synchronization.

**Expected result:** the board-specific deserializer and `g300` modules load, an image node enumerates supported formats, the short capture writes a nonempty file, and Viewer identifies 305g and produces a coherent depth image. A nonempty raw file alone proves buffer transport, **not metric depth decoding or calibration**. Missing modules/nodes stop bring-up at the carrier/driver stage. [Pinned bring-up and verification guide](https://github.com/orbbec/MIPI_Camera_Platform_Driver/blob/931a2d2414a0ac1afc959c6b125b2208c153d235/doc/Orbbec_G300_Series_GMSL_Camera_Driver_Quick_Start_Guide.md)

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                    | Check in order                                                                                                                                                |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB evaluation works, GMSL fails           | Treat camera imaging and carrier integration separately: power-over-coax, deserializer, kernel/module match, device-tree overlay, CSI routing and camera port |
| No video nodes                             | Inspect loaded modules and deserializer probe logs; verify the board-specific overlay and actual reboot. Reflashing camera firmware is not the first remedy   |
| Module refuses to load                     | Compare running kernel/vermagic and BSP package; do not force-load an incompatible module                                                                     |
| Raw buffers arrive but depth is unusable   | Identify image versus metadata node and stream format, then use SDK decoding/calibration; YUYV bytes are not a Y16 depth array                                |
| Stream fails after switching cameras/modes | Check paired-link limits, metadata layout and secondary-sync trigger requirements; start one free-running camera/stream                                       |
| Close object invalid                       | Verify resolution/disparity near limit, visible illumination and texture; the 4 cm claim is not an all-mode guarantee                                         |
| Unstable while wrist moves                 | Inspect cable strain, retention, bend path and power; test stationary first, then controlled motion only with a verified hand–eye transform                   |
| Firmware recovery needed                   | Use the explicitly supported 305g firmware row, stable supported connection and Viewer workflow; do not install an earlier 305-only image                     |

**Does a listed Jetson model prove my carrier works?** No. Deserializer, carrier routing, device tree, BSP and kernel must match the documented combination.

**Can I use USB for the first check?** Yes, as the manufacturer documents for evaluation/configuration. It does not validate the production GMSL path or environmental sealing.

## Downloads and technical documents

| Resource                                                                                                                                                                                                                              | Scope                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| [305g datasheet V1.1 PDF](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec_Gemini%20305g%20Datasheet%20V1.1.pdf)                                                                                                       | Full model optics, stream combinations, USB/SerDes signals, coordinates, performance and mechanical drawings |
| [305g English 2D/3D CAD ZIP](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20305g%202D%263D\(English\).zip)                                                                                                         | Exact model mechanical integration; check connector and housing revision                                     |
| [Current product/package description](https://store.orbbec.com/products/gemini-305g)                                                                                                                                                  | Official camera + FAKRA-Z cable + quickstart package; host/deserializer supplied separately                  |
| [Firmware 1.1.20 binary](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini305_v1.1.20.bin) / [firmware table](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305) | Explicit 305/305g-supported release and minimum SDK                                                          |
| [SDK v2.10.6](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6)                                                                                                                                                            | Native Viewer, libraries and API examples                                                                    |
| [Pinned GMSL driver repository](https://github.com/orbbec/MIPI_Camera_Platform_Driver/tree/931a2d2414a0ac1afc959c6b125b2208c153d235)                                                                                                  | Model support, hardware design, precompiled packages, patches and verification tools                         |
| [Supported hosts](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20%26%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements)                                | Exact vendor combinations and driver-version boundaries                                                      |
| [305 document center](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation)                                                                                                                                              | 305 and 305g datasheets/resources; select the exact model                                                    |

### Extended official documentation

These official readers retain the detailed model/concept/sample paths. Use the model and release boundaries above before adapting an advanced example.

| Official reader                                                                                                                                                                                                                                  | Relevant guide section             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------- |
| [Orbbec GMSL Cameras Supported Hosts and System Requirements](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20&%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements) | Software and development resources |
| [Set up Cameras for External Synchronization](https://doc.orbbec.com/documentation/Camera%20Accessories/Set%20up%20Cameras%20for%20External%20Synchronization)                                                                                   | Hardware and connections           |
| [Firmware Release of Gemini 305](https://doc.orbbec.com/documentation/Gemini%20305%20Documentation/Firmware%20Release%20of%20Gemini%20305)                                                                                                       | Downloads and technical documents  |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026**. Camera scope is **305g V1.1**, native SDK **v2.10.6**, and the GMSL workflow is pinned to driver repository commit **931a2d2414a0ac1afc959c6b125b2208c153d235**. USB evaluation and the named reference GMSL stack are separate procedures. No claim is made that an unspecified commercial carrier or arbitrary JetPack release is compatible.

Original procedures/code are source reviewed. **SDK execution, GMSL installation, hardware capture, robot motion and firmware flashing were not run.** Official diagrams, CAD, firmware and SDK/driver components retain their original licenses and notices. The datasheet's ambiguous USB RX-polarity labels are not used to design a custom high-speed cable; use a qualified cable or exact vendor-reviewed interface design.

### Reviewed engineering reference chapters

The following chapters preserve the existing wiki’s detailed engineering reference: specifications, calibration and coordinate concepts, metadata, filter behavior, source examples, installation procedures, troubleshooting and manufacturer illustrations. They complement the current commissioning guide above. Revision notes beside affected chapters separate historical SDK or host examples from the model-specific power, firmware and first-result path. No historical command, example output or photograph is a claimed test on this unit.

[ORBBEC-Gemini-305G](https://openelab.io/products/orbbec-gemini-305g-wrist-camera)

### Product and scope <a href="#reference-product-and-scope" id="reference-product-and-scope"></a>

**Gemini 305g** is a close-range stereo RGB-D camera for robot wrists and manipulation. It adds a **GMSL2/FAKRA** path to the Gemini 305 design and also provides USB-C. GMSL host integration is separate from USB SDK installation.

### Hardware and technical documents <a href="#reference-hardware-and-technical-documents" id="reference-hardware-and-technical-documents"></a>

| Item             | Reference                                       |
| ---------------- | ----------------------------------------------- |
| Working range    | 4–100cm+; manufacturer ideal range 7–50cm       |
| Depth modes      | Up to 1280 × 800 at 30fps or 848 × 480 at 60fps |
| Color            | Up to 1280 × 800 at 60fps, global shutter       |
| Body             | 42 × 42 × 40mm; approximately 116g              |
| GMSL supply      | 12V, ≥500mA per manufacturer reference          |
| Protection / SDK | IP65 / Orbbec SDK v2                            |

Use the product's **mechanical drawing, mounting/thread details and GMSL system guide**. USB power follows its USB contract; do not apply GMSL's 12V to USB. Confirm deserializer, carrier and cable compatibility before integration.

### Getting started: retained reference <a href="#reference-getting-started" id="reference-getting-started"></a>

1. For initial evaluation, use the supported USB setup and **Orbbec SDK v2 / Viewer** to confirm camera identity and a depth image.
2. Place a matte target within the ideal near-field range and select a supported stream pair.
3. For GMSL deployment, select an explicitly supported host, deserializer and JetPack/driver combination.
4. Install the official MIPI/GMSL platform driver before expecting the camera to enumerate.
5. Then verify frame rate, timestamps and synchronization before hand-eye calibration.

**Expected checkpoint:** stable depth/color streaming on the selected interface with recorded firmware and SDK/driver versions.

### Development software and recovery <a href="#reference-development-software-and-recovery" id="reference-development-software-and-recovery"></a>

Use **OrbbecSDK\_v2**. GMSL additionally requires **MIPI\_Camera\_Platform\_Driver** and the exact carrier's device-tree/driver support. The official compatibility guide lists Gemini 305g support from driver **v1.2.12 or above** for its stated solutions; verify the current platform matrix. Follow model-specific firmware recovery instructions.

### FAQs <a href="#reference-faqs" id="reference-faqs"></a>

**A FAKRA connector fits but there is no image?** Verify serializer/deserializer and carrier-driver support.

**60fps at full depth resolution?** The published full 1280 × 800 depth mode is 30fps; 60fps uses the stated lower depth resolution.

**Grasping coordinates are wrong?** Validate intrinsics, stream alignment, optical frames and hand-eye transform.

### Sources and validation <a href="#reference-sources-and-validation" id="reference-sources-and-validation"></a>

* [Manufacturer model specifications/drawings](https://www.orbbec.com/gemini-305g/)
* [Power/interface comparison](https://store.orbbec.com/products/gemini-305g)
* [Official SDK](https://orbbec.github.io/OrbbecSDK_v2/)
* [GMSL driver and quick start](https://github.com/orbbec/MIPI_Camera_Platform_Driver)
* [Host/driver compatibility](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20%26%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
