---
description: >-
  Compare Gemini 336, 335L, 336L and 335Le optics, power, pins and firmware,
  then acquire depth through USB or Ethernet with model-specific setup.
---

# Orbbec Gemini 330 series: USB and PoE camera integration

{% hint style="info" %}
[**Orbbec Gemini 336L on OpenELAB**](https://openelab.io/products/orbbec-gemini-336l-stereo-camera) — `ORBBEC-Gemini-336L`, IP65 long-baseline USB, IR-pass.

[**Orbbec Gemini 335L on OpenELAB**](https://openelab.io/products/orbbec-gemini-335l-stereo-camera) — `ORBBEC-Gemini-335L`, IP65 long-baseline USB, visible + near-IR pass.

[**Orbbec Gemini 336 on OpenELAB**](https://openelab.io/products/orbbec-gemini-336-stereo-vision-camera-with-infrared-imaging) — `ORBBEC-Gemini-336`, compact USB, IR-pass.

[**Orbbec Gemini 335Le on OpenELAB**](https://openelab.io/products/orbbec-gemini-335le-stereo-vision) — `ORBBEC-Gemini-335Le`, IP67 Gigabit Ethernet/PoE.
{% endhint %}

Gemini 330 is a stereo-camera family with materially different optics, housings and host interfaces. This guide compares the four listed options and provides separate USB and Ethernet first-result paths. Gemini 335 has its [own detailed USB guide](orbbec-gemini-335-user-manual.md); GMSL variants require a platform driver and are not substitutes for USB or Ethernet cameras.

## Product overview

### Choose optics and transport independently

The cameras calculate stereo depth onboard using the MX6800 processor. “L” models use a 95 mm baseline and global-shutter color; compact 335/336 use a 50 mm baseline and rolling-shutter color. Model 336/336L adds an infrared-pass cover over the depth optical path to suppress visible-light interference. That changes available scene texture as well as glare response; it is not a universal depth-quality upgrade. [USB datasheet V1.8](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf), [optical-filter guide](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Optical%20Filters%20for%20Stereo%20Vision%203D%20Cameras)

### Orbbec Gemini 335 Stereo Vision Camera with Infrared Imaging <a href="#orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging" id="orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging"></a>

The compact 335 is the all-pass comparison model. Follow its [dedicated guide](orbbec-gemini-335-user-manual.md) for the full commissioning procedure; do not infer that the 336 cover makes color sensing or all environmental limits identical.

### Orbbec Gemini 335L Stereo Vision Camera with Infrared Imaging <a href="#orbbec-gemini-335l-stereo-vision-camera-with-infrared-imaging" id="orbbec-gemini-335l-stereo-vision-camera-with-infrared-imaging"></a>

335L offers the longer baseline with visible + near-IR depth transmission and global-shutter color. Its host is USB 3, not a PoE switch.

### Orbbec Gemini 336 IR-Pass Stereo Depth Camera with Anti-Glare Infrared Imaging <a href="#orbbec-gemini-336-ir-pass-stereo-depth-camera-with-anti-glare-infrared-imaging" id="orbbec-gemini-336-ir-pass-stereo-depth-camera-with-anti-glare-infrared-imaging"></a>

336 keeps the compact 50 mm baseline and adds the IR-pass depth cover. It is IP5X, not IP65, and its color camera retains rolling-shutter behavior.

### Orbbec Gemini 336L Stereo Vision Camera with Infrared Imaging <a href="#orbbec-gemini-336l-stereo-vision-camera-with-infrared-imaging" id="orbbec-gemini-336l-stereo-vision-camera-with-infrared-imaging"></a>

336L combines the IR-pass depth cover, 95 mm baseline, global-shutter color and IP65 housing. Camera cable orientation and mounting holes follow the long housing, not the compact 336 drawing.

### Orbbec Gemini 335Lg Stereo Vision 3D Camera IP65 GMSL2/FAKRA <a href="#orbbec-gemini-335lg-stereo-vision-3d-camera-ip65-gmsl2-fakra" id="orbbec-gemini-335lg-stereo-vision-3d-camera-ip65-gmsl2-fakra"></a>

This legacy family reference is retained to distinguish the GMSL option: it needs a compatible deserializer, carrier, JetPack/kernel-specific driver and power-over-coax configuration. The [official GMSL quickstart](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(GMSL\)) and [GMSL platform requirements](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20%26%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements) are separate resources. None of the USB/PoE instructions below establishes GMSL compatibility.

### Orbbec Gemini 335Le Stereo Vision Camera with Infrared Imaging <a href="#orbbec-gemini-335le-stereo-vision-camera-with-infrared-imaging" id="orbbec-gemini-335le-stereo-vision-camera-with-infrared-imaging"></a>

335Le is the sealed Ethernet camera. It has an M12 X-coded data/PoE connector and **M8 A-coded** power/sync connector. It must not inherit the larger 435Le's auxiliary connector drawing. [Ethernet datasheet V1.0](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf)

## Applications

For textured indoor geometry and ordinary USB robotics, compare the compact and long-baseline models by near limit and color shutter. Choose 336/336L when suppressing visible-light interference is worth the change in depth texture response. Consider 335Le for a powered wired network and IP67 installation. Evaluate actual target materials and light: black or reflective objects and direct sunlight can defeat otherwise valid depth settings.

For robot fusion, keep per-device calibration and extrinsics. A family-wide FOV number is not a replacement for calibrated intrinsics at the selected resolution. Invalid depth and missing frames must remain identifiable in downstream obstacle or measurement logic.

## Specifications

The USB columns below use [USB datasheet V1.8, 13 October 2026, pp.11–12 and 16](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf). Ethernet uses [Ethernet datasheet V1.0, pp.9–10](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf). Dimensions are width × height × depth.

| Parameter                        | Gemini 336                 | Gemini 335L                | Gemini 336L          | Gemini 335Le                                               |
| -------------------------------- | -------------------------- | -------------------------- | -------------------- | ---------------------------------------------------------- |
| Sold SKU                         | `ORBBEC-Gemini-336`        | `ORBBEC-Gemini-335L`       | `ORBBEC-Gemini-336L` | `ORBBEC-Gemini-335Le`                                      |
| Interface                        | USB 3/2 Type-C             | USB 3/2 Type-C             | USB 3/2 Type-C       | Gigabit Ethernet, TCP/IP/RTSP                              |
| Baseline                         | 50 mm                      | 95 mm                      | 95 mm                | 95 mm                                                      |
| Depth optical path               | IR-pass                    | Visible + NIR-pass         | IR-pass              | Visible + NIR-pass                                         |
| Depth / color shutter            | Global / rolling           | Global / global            | Global / global      | Global / global                                            |
| Ideal working range              | 0.26–3 m                   | 0.25–6 m                   | 0.25–6 m             | 0.25–6 m                                                   |
| Broad advertised range           | 0.1–20 m+                  | 0.17–20 m+                 | 0.17–20 m+           | 0.25–20 m+                                                 |
| Depth maximum at full resolution | 1280 × 800, 30 fps         | 1280 × 800, 30 fps         | 1280 × 800, 30 fps   | 1280 × 800, 30 fps; multi-stream link budget still applies |
| Color maximum                    | 1920 × 1080, 30 fps        | 1280 × 800, 60 fps         | 1280 × 800, 60 fps   | 1280 × 800, 60 fps; enumerate actual combinations          |
| Depth FOV at 2 m                 | 90° × 65°, ±3°             | Same                       | Same                 | Same                                                       |
| Spatial precision                | ≤1.5% at 2 m               | ≤0.8% at 2 m; ≤1.6% at 4 m | Same as 335L         | Same as 335L                                               |
| Enclosure                        | IP5X                       | IP65                       | IP65                 | IP67                                                       |
| Dimensions                       | 90 × 25 × 30.7 mm          | 124 × 29 × 27 mm           | 124 × 29 × 27.7 mm   | 124 × 29 × 50 mm                                           |
| Mass                             | 99 g                       | 133 g                      | 135 g                | 220 g ±3 g                                                 |
| Supply provision                 | 5 V, ≥1.5 A USB capability | Same                       | Same                 | IEEE 802.3af PoE or 9–24 V DC, ≥1 A                        |
| Summary average / peak power     | <3 W / <6.5 W              | <3 W / <6 W                | Same as 335L         | PoE <5 W / <12 W; DC <4 W / <8.5 W                         |

Spatial-precision conditions are 1280 × 800, central 90% × 90% region at 2 m or 80% × 80% at 4 m. The 20 m+ claims depend on reflectivity >10% and scene conditions; they do not promise the listed precision at 20 m. All four have 850 nm projection and a six-axis IMU. [Exact conditions](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf#page=11), [Ethernet conditions](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf#page=9)

### Near limit and thermal conditions change with settings

| USB depth profile | Compact 335/336 minimum-Z | Long 335L/336L minimum-Z |
| ----------------- | ------------------------- | ------------------------ |
| 1280 × 800        | 0.26 m                    | 0.25 m                   |
| 848 × 480         | 0.18 m                    | 0.34 m                   |
| 640 × 480         | 0.17 m                    | 0.30 m                   |
| 424 × 240         | 0.10 m                    | 0.17 m                   |

These V1.8 values are profile-specific, not a promise that every preset reaches the closest limit. At 15 fps compact models support −10 to +45 °C ambient; at higher 30/60 fps configurations use −10 to +40 °C. Long USB models support −10 to +50 °C at 15/30 fps, reducing to +45 °C at 60 fps. For 335Le use −10 to +50 °C at 15 fps and +45 °C for higher-rate configurations. Conditions are noncondensing. [USB thermal and near-limit tables](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf), [Ethernet thermal table p.46](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf#page=46)

## Hardware and connections

![Official Orbbec long USB cameras: bottom Type-C and top sync port](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120450/2024110312.png)

Official Orbbec mounting-reference illustration for 335L/336L. The Ethernet 335Le uses different sealed connectors.

### USB 336, 335L and 336L

Use a USB 3 cable and a port/powered hub able to provide **5 V at ≥1.5 A**, not merely a port colored blue. A 900 mA USB port can enumerate the camera yet brown out during projector activity. The official 335L workaround lowers laser level from 6 to 5 on a 900 mA host, trading illumination for power; prefer an adequately powered host for initial characterization and do not generalize that workaround to 336L without confirming its firmware controls. [Power-delivery reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Power%20Delivery%20\(Gemini%20330%20Series\))

Compact cameras have Type-C on the side and the covered 8-pin sync port on the opposite side. Long USB cameras have Type-C on the bottom and sync on the top. Fit the proper cable/cover and strain relief; check cable-plug clearance before clamping the housing. Compact rear mounts are M3, long rear mounts M4; both have a 1/4-20 UNC bottom mount. The official mounting reference gives 3 mm rear thread depth and 0.4 N·m rear screw torque; bottom thread depth differs, 5 mm compact versus 8 mm long. Check engagement in the actual CAD revision, including the with/without-front-rubber-feet options. [Mounting reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Mounting%20\(Gemini%20330%20Series\))

### USB sync connector is a logic interface

| Pin | USB 330-series function | Electrical scope                                                     |
| --- | ----------------------- | -------------------------------------------------------------------- |
| 1   | VCC reference           | 1.75–5.25 V; default 1.8 V; external reference input ≥100 mA if used |
| 2   | GPIO\_OUT               | Output level follows reference VCC                                   |
| 3   | VSYNC\_OUT              | Output level follows reference VCC                                   |
| 4   | TIMER\_SYNC\_OUT        | Output level follows reference VCC                                   |
| 5   | RESET\_IN               | Special reset timing; not an ordinary GPIO input                     |
| 6   | VSYNC\_IN               | Input level follows reference VCC                                    |
| 7   | TIMER\_SYNC\_IN         | Refer to full electrical/timing table before use                     |
| 8   | GND                     | Signal ground                                                        |

Use the exact mating-face orientation in [V1.8 synchronization drawings pp.46–48](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf#page=46). The default is **1.8 V logic**, not 5 V by virtue of USB power. At pin 6 the table specifies VIH = 0.65 × VCC and VIL ≤0.7 V. Do not apply 24 V or use the Ethernet camera's pin numbering. Use a documented synchronization hub/cable if synchronization is needed; first-run capture below leaves this connector capped.

### Ethernet 335Le power and auxiliary connector

Connect the M12 X-coded cable to a compliant Gigabit PoE source; ordinary Ethernet alone does not power it. Alternatively wire the supplied M8 harness to **9–24 V DC, ≥1 A capacity**, red pin 1 positive, black pin 8 power ground, with power removed during wiring. Keep unused wires insulated. The auxiliary M8 connector is **male at the camera**, unlike the female X-coded Ethernet port. [Connector drawings pp.13–15](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf#page=13)

| M8 pin / harness color | 335Le signal           |
| ---------------------- | ---------------------- |
| 1 / red                | 9–24 V power input     |
| 2 / orange             | VSYNC reference supply |
| 3 / green              | VSYNC input            |
| 4 / blue               | VSYNC output           |
| 5 / brown              | Signal ground          |
| 6 / purple             | RS485B                 |
| 7 / yellow             | RS485A                 |
| 8 / black              | Power ground           |

The M8 table lists adjustable 3.3–24 V synchronization levels. However, the same Ethernet datasheet describes input pulses as ≥50 μs in its connector chapter, 100 μs in its general sync description and 1 ms in another table. **Custom external-trigger timing remains bounded until the applicable revision is clarified.** PoE free-running capture does not use these pins. RS-485 is differential signaling; no reviewed public command map was found for implementing a serial control client from these pins alone. [Timing descriptions pp.15 and 35–37](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf)

## Software and development resources

Use matching Viewer/libraries from [**Orbbec SDK v2.10.6**](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6) for the original example. Its support table lists USB 335/336/335L/336L minimum firmware **1.2.20**, recommended **1.8.10**; 335Le minimum **1.5.31**, recommended **1.8.10**. The newer **1.8.17** firmware row is explicitly for 338Le/338Lg; do not select it merely because its number is higher. [Release support matrix](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/README.md#14-supported-devices), [firmware release table](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))

### Presets, HDR, filtering and calibrated geometry

Start with Default preset and auto exposure. High Accuracy may discard uncertain pixels; High Density can fill more pixels at the cost of noise. Not all presets apply to IR-pass models: the current table lists High Accuracy for 336/336L but limits Hand, High Density and Medium Density to named all-pass models. Stop streams before changing preset and allow the documented settling delay before restarting. HDR merges exposures and needs matching sequence/metadata; it can introduce motion artifacts, so demonstrate a stable single-exposure stream first. [Preset guide](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Presets%20for%20Orbbec%20Gemini%20330%20Series%203D%20Cameras), [HDR sample](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/C++%20Sample%20HDR%20Merge)

Retrieve intrinsics/extrinsics from the device for the selected profiles. Use SDK alignment and deprojection rather than scaling depth pixels onto RGB by image-size ratios. The optical coordinate convention is X right, Y down, Z forward; distinguish depth-to-color transformation from the camera-to-robot mounting transform. Record device timestamps, host arrival timestamps, frame numbers, exposure and depth scale with recordings. [Coordinates](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Coordinate%20Systems%20\(Stereo%20Vision%203D%20Camera\)), [metadata](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Frame%20Metadata), [transform guide](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Transform%20Coordinates)

Inspect raw depth before enabling decimation, spatial, temporal, hole-filling or HDR filters. Their ordering affects geometry and latency; temporal history can make a moving object appear to persist. Use recorded scenes to compare valid fraction, plane bias and frame-to-frame variation with identical settings. [Detailed filters](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Detailed%20Filter%20Reference), [recommended filter ordering](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Recommended%20Filter%20List), [depth metrics](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Quality%20Metrics)

The C/C++ examples cover identity, separate streams, IMU, point clouds, recording/playback, hotplug, control, depth units and multi-camera synchronization. [ROS 2](https://github.com/orbbec/OrbbecSDK_ROS2), [ROS 1](https://github.com/orbbec/OrbbecSDK_ROS1) and [Python](https://github.com/orbbec/pyorbbecsdk) are separate wrapper projects; validate their branch/SDK/firmware matrix before using their launch files. A generic wrapper tutorial is not proof of support for a particular carrier or camera firmware.

## Getting started

### USB first result: 336, 335L or 336L

1. Check the exact model label, prepare one USB 3 camera, a short data cable, a powered 5 V/≥1.5 A-capable port and a diffuse plane around 1 m away. Leave sync disconnected.
2. Install the matching SDK/Viewer package for Windows x64 or the supported Linux host architecture. On Linux install the release's udev rules, reconnect the camera and confirm it in `lsusb`; `lsusb -t` should show the intended SuperSpeed connection.
3. Open Viewer, select the camera and record serial/firmware. Check it meets the model's SDK minimum. Do not upgrade firmware merely to cure a loose cable or a USB 2 connection.
4. Select Default preset; start **1280 × 800 Y16 depth at 30 fps**, auto exposure, with all other streams off. If the profile is unavailable, inspect the USB link and enumerated profiles first.
5. Move the target slowly, then hold it still. Inspect depth and frame metadata; add color only after the depth stream is stable. Stop streams before changing preset or resolution.

**Expected result:** the chosen model reports a continuous depth image at an advertised profile, with a plausible plane distance and stable frame arrival. Invalid black regions may remain at edges/reflective areas; no general scene is expected to have 100% valid pixels. [USB quickstart](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))

### Ethernet first result: 335Le only

1. Connect one 335Le through its M12-to-RJ45 cable to an IEEE 802.3af Gigabit PoE source; connect the host to the data side. Keep M8 signals disconnected.
2. In the host network settings choose a free camera-interface address such as **192.168.1.20/24**; the factory camera is **192.168.1.10**. Avoid a duplicate address or overlapping VPN route. Inspect `ip route get 192.168.1.10` on Linux before altering settings.
3. Open the network device in matching Viewer. Confirm model, serial, firmware and 1 Gbit/s link. Scope firewall application permission to this test network.
4. Start **1280 × 800 Y16 depth at 15 fps**, the preset guide's recommended Ethernet starting point, with other streams off. Add MJPEG color at an advertised profile only after checking frame gaps.
5. Stop streams and record the profile/IP/firmware combination. Assign a unique persistent address before adding a second factory-default camera.

**Expected result:** Viewer opens a **335Le**, displays depth and continues receiving complete frames. Finding a device in a scan is not sufficient if its data address is on a different subnet. [Ethernet quickstart](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Ethernet\))

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
LD_LIBRARY_PATH="$SDK_ROOT/lib${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}" ./build/roi_depth 1280 800 15 net
```

The package layout and imported CMake target follow the [v2.10.6 development guide](https://github.com/orbbec/OrbbecSDK_v2/blob/v2.10.6/docs/tutorial/installation_and_development_guide.md). If an archive places its CMake config elsewhere, point `OrbbecSDK_DIR` at the directory actually containing that config. Do not mix headers and libraries from different SDK releases.

**Expected result:** the process prints six measurement records and exits successfully after receiving 60 depth frames. Each record includes a frame index, `timestamp_us`, valid sample count and `median_mm`; a diffuse target at about 1 m should give a plausible distance near its measured plane position. Those are expected results, not recorded measurements. An unsupported-profile error means enumerate/select a profile the device actually advertises; do not substitute a color format or interpret compressed depth bytes as Y16. Return code 3 means camera selection was ambiguous; 4 means too few frames arrived. A full invalid patch is reported explicitly rather than treated as zero metres.

For USB 336/335L/336L run `./build/roi_depth 1280 800 30 usb` with the same library path setup. For 335Le use the `net` invocation shown above. The program tests exactly one enumerated camera and intentionally refuses ambiguous selection.

## Troubleshooting and FAQs

| Problem                             | Practical diagnostic sequence                                                                                                                                                                                           |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB camera appears but stream stops | Confirm USB 3 negotiation and sufficient 5 V supply; remove passive hubs/extensions; test depth alone; check host logs before reducing projector power                                                                  |
| Device missing on Linux             | Confirm `lsusb`, release udev rules and that another process does not own it; close Viewer before starting custom code; reconnect after applying access rules                                                           |
| Lower apparent resolution           | Check decimation and stream profile; post-processing can reduce image dimensions without changing the original sensor setting                                                                                           |
| Color/depth edges do not align      | Restore unmirrored/unrotated streams; use calibrated alignment at supported profiles; compact color is rolling shutter, which still introduces motion differences                                                       |
| Depth preset change fails           | Stop all streams first, change preset, wait about 3 seconds, then restart; avoid the production-only Factory Calib preset                                                                                               |
| Ethernet frame loss                 | Verify Gigabit link, power budget, route and host load; start depth alone at 15 fps; increase streams one at a time                                                                                                     |
| Multi-camera interference or gaps   | Separate power/bandwidth limitations from optical interference; use the exact supported synchronization topology and per-model electrical levels                                                                        |
| Firmware recovery needed            | Use exact-model firmware and supported Viewer recovery. The documented recovery-mode process may require a second normal-mode update to finish ISP firmware; verify the recovery instructions for the installed release |

**Is the 336L simply a faster 336?** No. It changes baseline, shutter, housing, near-limit/profile behavior and mounting. Its maximum color profile also differs.

**Can I connect USB sync directly to a 24 V PLC output?** No. The USB family's reference-driven logic interface is different from the Ethernet auxiliary interface. Use an appropriately designed interface and the exact electrical/timing specification.

**Can an IP65/IP67 camera be operated unsealed?** Connector protection depends on the proper mating cable and unused-port caps. An enclosure rating is not a substitute for installation instructions. [Troubleshooting](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Troubleshooting), [mounting and thermal references](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Thermal%20\(Gemini%20330%20Series\))

## Downloads and technical documents

| Resource                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Scope                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| [USB datasheet V1.8 PDF](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Compact/long USB optics, stream tables, pinout, thermal, power and mechanical drawings        |
| [Ethernet datasheet V1.0 PDF](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 335Le/338Le; use only the 335Le column for this SKU                                           |
| [Model-specific CAD downloads](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 335/336 with/without rubber feet; 335L, 336L and 335Le separate CAD revisions                 |
| [Firmware table and changelog](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Match the supported-model row and SDK minimum before downloading                              |
| [Depth preset releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Preset%20Release%20\(Gemini%20330%20Series\))                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Optional presets; check exact model/firmware instead of applying every family file            |
| [SDK v2.10.6 release](https://github.com/orbbec/OrbbecSDK_v2/releases/tag/v2.10.6)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Viewer, libraries and original vendor examples                                                |
| [Mounting](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Mounting%20\(Gemini%20330%20Series\)) / [thermal](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Thermal%20\(Gemini%20330%20Series\)) / [power](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Power%20Delivery%20\(Gemini%20330%20Series\)) / [USB cable](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Cable%20\(USB\)%20\(Gemini%20330%20Series\)) | Integration references; retain the model and revision context                                 |
| [Ethernet mechanical reference](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20for%20Ethernet%20Device)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 335Le-specific mechanical design guideline                                                    |
| [Official 330 documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Overview, theory, SDK concepts, samples, wrappers, compliance, licenses and reference designs |

### Direct model-specific CAD files

* [Gemini 336 CAD V2.0, without front rubber feet](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini336_CAD_Files_V2.0.zip)
* [Gemini 335L CAD V1.0](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini_335L_CAD_Files.zip)
* [Gemini 336L CAD V1.0](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini_336L_CAD_Files.zip)
* [Gemini 335Le CAD V1.1](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini_335Le_CAD_files_V1.1.zip)

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

Reviewed **24 November 2026** against the current official document center, USB datasheet V1.8, Ethernet datasheet V1.0 and SDK v2.10.6 source headers/support table. Linked official diagrams and design files belong to Orbbec; SDK code carries its own license and third-party notices. Public full hardware schematics and a complete RS-485 command map were not found in the reviewed resources.

Procedures and original code are source reviewed. **SDK execution and hardware testing were not run.** USB and free-running Ethernet startup are covered; custom Ethernet trigger timing is deliberately excluded because the datasheet gives inconsistent pulse requirements. The GMSL model reference is retained for navigation and is not a claim that a USB/Ethernet host can drive it.

### Reviewed engineering reference chapters

The following chapters preserve the existing wiki’s detailed engineering reference: specifications, calibration and coordinate concepts, metadata, filter behavior, source examples, installation procedures, troubleshooting and manufacturer illustrations. They complement the current commissioning guide above. Revision notes beside affected chapters separate historical SDK or host examples from the model-specific power, firmware and first-result path. No historical command, example output or photograph is a claimed test on this unit.

### Orbbec Gemini 335 Stereo Vision Camera with Infrared Imaging <a href="#reference-orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging" id="reference-orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-335-stereo-vision-camera-with-infrared-imaging)

### Orbbec Gemini 335L Stereo Vision Camera with Infrared Imaging <a href="#reference-orbbec-gemini-335l-stereo-vision-camera-with-infrared-imaging" id="reference-orbbec-gemini-335l-stereo-vision-camera-with-infrared-imaging"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-335l-stereo-camera)

### Orbbec Gemini 336 IR-Pass Stereo Depth Camera with Anti-Glare Infrared Imaging <a href="#reference-orbbec-gemini-336-ir-pass-stereo-depth-camera-with-anti-glare-infrared-imaging" id="reference-orbbec-gemini-336-ir-pass-stereo-depth-camera-with-anti-glare-infrared-imaging"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-336-stereo-vision-camera-with-infrared-imaging)

### Orbbec Gemini 336L Stereo Vision Camera with Infrared Imaging <a href="#reference-orbbec-gemini-336l-stereo-vision-camera-with-infrared-imaging" id="reference-orbbec-gemini-336l-stereo-vision-camera-with-infrared-imaging"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-336l-stereo-camera)

### Orbbec Gemini 335Lg Stereo Vision 3D Camera IP65 GMSL2/FAKRA <a href="#reference-orbbec-gemini-335lg-stereo-vision-3d-camera-ip65-gmsl2fakra" id="reference-orbbec-gemini-335lg-stereo-vision-3d-camera-ip65-gmsl2fakra"></a>

{% hint style="info" %}
This chapter concerns the GMSL/FAKRA variant and its stated reference host/driver. It is retained as an interface comparison; the assigned USB and PoE SKUs are not GMSL cameras. Match camera firmware, deserializer/carrier, JetPack/L4T and kernel module before using a driver command. A command from an older reference kernel is not portable to another Jetson image.
{% endhint %}

[Original store reference](https://openelab.io/products/orbbec-gemini-335lg-stereo-vision-3d-camera-ip65-gmsl2-fakra)

### Orbbec Gemini 335Le Stereo Vision Camera with Infrared Imaging <a href="#reference-orbbec-gemini-335le-stereo-vision-camera-with-infrared-imaging" id="reference-orbbec-gemini-335le-stereo-vision-camera-with-infrared-imaging"></a>

[Original store reference](https://openelab.io/products/orbbec-gemini-335le-stereo-vision)

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

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/bqyIU1Xa4iu68Pi0xqG0/assets/da2267c66aaae872f6ae.webp)

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

[![Group 10.jpg](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/HwNyZth5b289fRLHtxgX/assets/9bdbdbac0eec2ac54ff2.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-12/group-10.jpg)

* The Gemini 330 series integrates Orbbec’s latest sensor technology into the camera. For detailed information, please refer to the [Orbbec Gemini 330 series Datasheet](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\)).

#### 6. Typical Scene Captures using Gemini 330 Series Cameras <a href="#id-6.-typical-scene-captures-using-gemini-330-series-cameras" id="id-6.-typical-scene-captures-using-gemini-330-series-cameras"></a>

* \*\*Outdoor performance -\*\*Gemini 335/336

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174701/image001-7.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174705/image003-7.png) |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/iRVyy2y5sa4ojixks8pS/assets/8aee70d48996f6988b3a.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rJRMqHeVRlX9A45Ycco2/assets/3c21af0c692d12729823.webp)
* **Outdoor performance - Gemini 335L/336L/335Lg/335Le**

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174739/image005-6.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26174743/image007-5.png) |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/DnEaOj6YGas0slZis5MD/assets/3b845f0c69a7e409d5c1.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/eyGkaSm5OXSPITBll0FQ/assets/2fbe7abe0f012e737a72.webp)
* **Indoor performance - Gemini 335/336**

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180048/731E5D9D-029B-4550-8964-94D023884644.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180040/F4B07029-8606-41a0-B4C7-DC5BEB73334E.png) |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oW4m06hU3cr1CZgrkdgf/assets/9c023e794e5af1055636.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/vSVTxPpDS2jN6AoErgHj/assets/4de00059b9151d8e807e.webp)
* **Indoor performance - Gemini 335L/336L/335Lg/335Le**

| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180753/22EE797E-7B89-4611-9E26-091D4FB5E54B.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26180746/BF83A51D-7C77-49bd-AE78-5EC63F5F41C3.png) |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20150036/Gemini335lgdocs202410221.png)             | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/20150047/Gemini335lgdocs202410222.png)             |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/1NOpDaNlrfSnQyNGKzvR/assets/46b3c254d7ac9e2eaec7.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Po2Q7mvqi6yCSN0JzDNC/assets/21fe138482198461fc2b.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/XQrPsk7Rwh0crEubV07j/assets/2149bcb85c44548e599a.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/g61QDiEJiZLZFZ3Jmvnm/assets/0f999758fc052506c0b2.webp)
* **Tiny objects recognition @ 2m**. The tiny cubic of 3cm x 3cm (the smallest cubic on the right side of the RGB figure below) is clearly visible in point cloud.

![Official Orbbec figure from About Orbbec Gemini 330 Series](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jG61pynLfG7LUuc84fE8/assets/de3aad12c69ccc1164dc.webp)

#### Gemini 330 Series Datasheet (Overall) <a href="#gemini-330-series-datasheet-overall" id="gemini-330-series-datasheet-overall"></a>

_Reviewed source:_ [_Gemini 330 Series Datasheet (Overall)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Datasheet%20\(Overall\))_. Manufacturer figures and source examples retain their original attribution and rights._

| Interface | Product                  | Datasheet                                                                                                                                                                                   | Version | Release Date |
| --------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | ------------ |
| USB       | Gemini 335/336/335L/336L | [Gemini 330 Series Datasheet for USB Devices](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Gemini%20330%20series%20Datasheet-V1.8.pdf)                                          | V1.8    | 2026-10-13   |
| GMSL      | Gemini 335Lg/338Lg       | [Gemini 330 Series Datasheet for GMSL Devices](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Series%20GMSL%20Datasheet-V1.2.pdf)                         | V1.2    | 2026-08-10   |
| Ethernet  | Gemini 335Le/338Le       | [Gemini 330 Series Datasheet for Ethernet Devices](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/Orbbec%20Gemini%20330%20Serise%20Datasheet%20for%20Ethernet%20Devices_V1.0.pdf) | V1.0    | 2026-08-10   |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2025/04/22062452/Gemini-330-series-Datasheet-V1.6.pdf)

#### Camera Interface Selection Guide <a href="#camera-interface-selection-guide" id="camera-interface-selection-guide"></a>

_Reviewed source:_ [_Camera Interface Selection Guide_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Camera%20Interface%20Selection%20Guide)_. Manufacturer figures and source examples retain their original attribution and rights._

The manufacturer selector page does not provide a technical matrix. For this integration, distinguish three contracts: USB uses a powered host and Orbbec SDK; Ethernet uses Gigabit routing plus a documented PoE/DC power path; GMSL requires a compatible powered deserializer, carrier and exact platform driver. The specification and hardware tables above identify the covered USB/PoE models; a matching connector cannot substitute one transport for another.

#### Gemini 330 Series Quickstart Guide (Overall) <a href="#gemini-330-series-quickstart-guide-overall" id="gemini-330-series-quickstart-guide-overall"></a>

_Reviewed source:_ [_Gemini 330 Series Quickstart Guide (Overall)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Overall\))_. Manufacturer figures and source examples retain their original attribution and rights._

| Interface | Product                  | Quickstart Guide                                                                                                                                                                               |
| --------- | ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB       | Gemini 335/336/335L/336L | [Gemini 330 Series Quickstart Guide (USB)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))           |
| GMSL      | Gemini 335Lg             | [Gemini 330 Series Quickstart Guide (GMSL)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(GMSL\))         |
| Ethernet  | Gemini 335Le             | [Gemini 330 Series Quickstart Guide (Ethernet)](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Ethernet\)) |

#### Gemini 330 Series Quickstart Guide (USB) <a href="#gemini-330-series-quickstart-guide-usb" id="gemini-330-series-quickstart-guide-usb"></a>

_Reviewed source:_ [_Gemini 330 Series Quickstart Guide (USB)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(USB\))_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. What's in The Box for Orbbec Gemini\\\335/336? <a href="#id-1.-whats-in-the-box-for-orbbec-gemini-335-336" id="id-1.-whats-in-the-box-for-orbbec-gemini-335-336"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7d9Z0jhBPHp35jXJ1tlC/assets/706f8f2c31e786855743.webp)

#### 2. What's in The Box for Orbbec Gemini 335L/336L? <a href="#id-2.-whats-in-the-box-for-orbbec-gemini-335l-336l" id="id-2.-whats-in-the-box-for-orbbec-gemini-335l-336l"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/8MBn2nPrxgGnIr6Pnse6/assets/c6da0112ab3ded1155f3.webp)

#### 3. Connect the Orbbec Camera <a href="#id-3.-connect-the-orbbec-camera" id="id-3.-connect-the-orbbec-camera"></a>

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

#### 4. Get Orbbec Viewer <a href="#id-4.-get-orbbec-viewer" id="id-4.-get-orbbec-viewer"></a>

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/OiVk7UTyqnjO8xjVgaed/assets/47407f5e9ff14d37bdc1.webp)

#### 5. Launch Orbbec Viewer <a href="#id-5.-launch-orbbec-viewer" id="id-5.-launch-orbbec-viewer"></a>

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

#### 6. Caution <a href="#id-6.-caution" id="id-6.-caution"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (USB)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/cnHDrkVdK529EAiqvUrj/assets/3c79754847a03d90e16e.webp)

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

#### Gemini 330 Series Quickstart Guide (GMSL) <a href="#gemini-330-series-quickstart-guide-gmsl" id="gemini-330-series-quickstart-guide-gmsl"></a>

_Reviewed source:_ [_Gemini 330 Series Quickstart Guide (GMSL)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(GMSL\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
This chapter concerns the GMSL/FAKRA variant and its stated reference host/driver. It is retained as an interface comparison; the assigned USB and PoE SKUs are not GMSL cameras. Match camera firmware, deserializer/carrier, JetPack/L4T and kernel module before using a driver command. A command from an older reference kernel is not portable to another Jetson image.
{% endhint %}

#### Important Notice <a href="#important-notice" id="important-notice"></a>

Dear Developer,\
To better support you in integrating and developing with the Gemini 335Lg camera, we have created a brand-new, more comprehensive GitHub repository. The details are as follows:\
New Repository URL: [https://github.com/orbbec/MIPI\_Camera\_Platform\_Driver](https://github.com/orbbec/MIPI_Camera_Platform_Driver)

The new repository contains:

* More complete official documentation
* The latest binary files
* Driver adaptation source code
* Rich development examples

Thank you for your support!

#### 1. Preparation <a href="#id-1.-preparation" id="id-1.-preparation"></a>

**1.1 Hardware Requirements**

* Gemini 335Lg boxed camera
* NVIDIA Jetson AGX Orin DevKit and compatible power supply
* GMSL camera deserializer board (example model: FG96\_8CH\_GMSL(EVK)) and compatible power supply

Supported Camera and Platform Information

Table 1-1

| Camera Model | Hardware Platform       | Manufacturer | Software Version | GMSL Adapter Board   |
| ------------ | ----------------------- | ------------ | ---------------- | -------------------- |
| Gemini 335Lg | Jetson AGX Orin Dev Kit | NVIDIA       | JetPack 6.0/6.2  | FG96-8CH-V2(Max9296) |

**1.2 Software Resources**

* Precompiled driver file
* Orbbec Viewer software(supports version Orbbec Viewer\_v2.0.7-rc and above)

#### 2. Unboxing and Installation <a href="#id-2.-unboxing-and-installation" id="id-2.-unboxing-and-installation"></a>

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

#### 3. Connecting Devices and Powering On <a href="#id-3.-connecting-devices-and-powering-on" id="id-3.-connecting-devices-and-powering-on"></a>

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

#### 4. Loading the Precompiled Driver File <a href="#id-4.-loading-the-precompiled-driver-file" id="id-4.-loading-the-precompiled-driver-file"></a>

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### 5. Getting Started <a href="#id-5.-getting-started" id="id-5.-getting-started"></a>

**5.1 Check Driver Version**

Ensure the driver version matches the precompiled driver file version

Run the following in the terminal:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

```
cat /sys/module/g300/version
```

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/sctkD9dAKzmOcx8L68yL/assets/93b3931f74ac55c80bd5.gif)

Fig. 5-1

**5.2 List Video Nodes**

Run the following in the terminal:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

**5.3 Obtain Orbbec Viewer Software**

Download the latest Orbbec Viewer from OrbbecSDK\_v2 Releases (e.g., Orbbec Viewer\_v2.4.8\_xxx.zip) and place it in \~/Downloads.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (GMSL)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zleoovG6N8RnjQNTRbvF/assets/c98bed2023c60829598f.gif)Fig. 5-3

**5.4 Extract and Run**

Run the following in the terminal:

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

#### Gemini 330 Series Quickstart Guide (Ethernet) <a href="#gemini-330-series-quickstart-guide-ethernet" id="gemini-330-series-quickstart-guide-ethernet"></a>

_Reviewed source:_ [_Gemini 330 Series Quickstart Guide (Ethernet)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Quickstart%20Guide%20\(Ethernet\))_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. What's in The Box for Gemini 335Le? <a href="#id-1.-whats-in-the-box-for-gemini-335le" id="id-1.-whats-in-the-box-for-gemini-335le"></a>

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/UEJrs1GAUVukATFSXpBw/assets/31c550a5efc6bef49377.webp) ![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JrsJ2PVUPEKX1oXlU2Ug/assets/973148de52e4ca501e03.webp)

#### 2. Connect the Orbbec Camera <a href="#id-2.-connect-the-orbbec-camera" id="id-2.-connect-the-orbbec-camera"></a>

**A. Connect the camera using PoE (Power over Ethernet) for power supply.**

1. Secure the camera onto the tripod, as illustrated in Step 1 below.
2. If a PoE switch is available, the camera can be powered via the same Ethernet (M12) data cable for data transfer.
3. Remove the camera’s M12 interface protective cover and connect the Data cable to the M12 interface on the camera.Use an appropriate mounting tool to achieve the specified torque: [M12 torque wrench](https://us.rs-online.com/catalogsearch/result/?q=M12+torque+wrench+set+AF+13)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/cplb8HbyZ4WEloP3Kzx0/assets/6bc7cc456fc18e07c331.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/G5Cimage.png)
4. Plug the RJ45 end of the data cable into the PoE Switch.
5. Connect the host to the PoE switch using a standard RJ45 Ethernet cable (the port used for\
   the PC connection does not need to be PoE capable).

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rgyEpPepxesC8XdW2RsG/assets/ff87233c4c0ac5dac801.webp)

| Configuration                           | Hardware Requirement • In the product retail package                                                                                                   | Hardware Requirement • To be provided by the user                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PoE-powered, Host with Ethernet Port    | <p>• Gemini 335Le camera<br>• Gemini 335Le data cable (2m)</p>                                                                                         | <p>• PoE switch or PoE injector ( IEEE 802.3af/at compliant ), reference product: <a href="https://www.digikey.com/en/products/detail/microchip-technology/PD-3501G-AC-US/3992860">PD-3501G/AC-US Microchip Technology | Power Supplies – External/Internal (Off-Board) | DigiKey</a> <a href="https://www.omadanetworks.com/us/business-networking/omada-accessory-poe-adapter/poe150s/">POE150S | Omada PoE Injector | TP-Link</a> Note: depending on your selected PoE switch/PoE injector, a power cable for it may be required. Please ensure the selected cable complies with your regional power supply standards. • Gigabit Ethernet cable • &#x3C;10m, Cat5e or higher T568B-to-T568B or T568A-to-T568A standard compliant<br>• 10m+, Cat6 or higher T568B-to-T568B or T568A-to-T568A standard compliant</p> |
| PoE-powered, Host without Ethernet Port | In addition to the ‘PoE-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user. | In addition to the ‘PoE-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

**B. Connect the camera using a DC power supply.**

1. Secure the camera onto the tripod, as illustrated in Step 1 below.
2. Remove the camera’s M12 interface protective cover and connect the Data cable to the M12 interface on the camera.
3. Remove the camera’s M8 interface protective cover and connect the Power cable to the M8 interface on the camera. Use an appropriate mounting tool to achieve the specified torque: [M8 torque wrench](https://us.rs-online.com/catalogsearch/result/?q=M8+torque+wrench)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kMfJXsGb93ZGsNK4OMMQ/assets/52200f90c9a6d64ffbc7.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-04/M21image.png)
4. Use the red-labeled "POWER IN 9- 24V" pin and the black-labeled "POWER GND" pin to connect a 9- 24V DC power source.
5. Plug the RJ45 end of the data cable into the host or the network gateway to which the host is connected.

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AdVTqPMmYTQxKW5cEFQp/assets/fea3338e4751a60ace34.webp)

| Configuration                          | Hardware Requirement • In the product retail package                                                                                                  | Hardware Requirement • To be provided by the user                                                                                                                                                                                               |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DC-powered, Host with Ethernet Port    | <p>• Gemini 335Le camera<br>• Gemini 335Le data cable (2m)<br>• Gemini 335Le power cable (2m)</p>                                                     | <p>• DC power supply (output: 9-24V , current: ≥1A)<br>• If a power extension cord is required, make sure the current and voltage received by the camera’s original power cord harness meet the power supply requirements in its datasheet.</p> |
| DC-powered, Host without Ethernet Port | In addition to the ‘DC-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user. | In addition to the ‘DC-powered, Host with Ethernet port’ configuration, a USB-to-Gigabit Ethernet adapter is required and to be provided by the user.                                                                                           |

#### 3. Get Orbbec Viewer <a href="#id-3.-get-orbbec-viewer" id="id-3.-get-orbbec-viewer"></a>

Select and download the corresponding Orbbec Viewer based on your system and version.

[https://www.orbbec.com/developers/orbbec-sdk/](https://www.orbbec.com/developers/orbbec-sdk/)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/MSeOcIEQAUa8sqSC8rfT/assets/dbbff0fcc59b5613e935.webp)

#### 4. Environment Preparation Instructions <a href="#id-4.-environment-preparation-instructions" id="id-4.-environment-preparation-instructions"></a>

For detailed network environment configuration instructions, please refer to https://www.orbbec.com/docs/gemini-335le-quick-start/

#### 5. Launch Orbbec Viewer <a href="#id-5.-launch-orbbec-viewer-1" id="id-5.-launch-orbbec-viewer-1"></a>

For detailed instructions, please refer to the Orbbec Viewer tutorial video below .

[https://www.youtube.com/@Orbbec3d](https://www.youtube.com/@Orbbec3d)

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7FAnJd5zLjNKSz7B0rW9/assets/8b60cff1a21de9dca5fa.webp)

#### 6. Network Environment Configuration on the Host <a href="#id-6.-network-environment-configuration-on-the-host" id="id-6.-network-environment-configuration-on-the-host"></a>

{% hint style="info" %}
PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

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

The default IP address for the Gemini 335Le device is 192.168.1.10. The device can be directly connected to the host or via a network switch. Please adjust the host’s local network interface to be on the same network segment as the Gemini 335Le device for proper recognition. Once the host is in the same network segment, the Gemini 335Le device can be accessed using either the Orbbec Viewer tool or the SDK.

Modify the IP address to be in the same network segment:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ws3y1QG10pCEBwZtqrCJ/assets/bdb0cffbb34906ba78dd.webp)

**3. Recommend Configuration**

Due to differences in system networks and power management across platforms, packet loss may occur to varying degrees during the process of stream capture on the host machine, which can result in the frame rate not meeting expectations. Therefore, before using the Gemini 335Le device on different platforms, it is essential to configure and verify the platform and system settings to avoid issues like frame loss.

1. Computer power configuration:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/MQUtUcr2Tn2ZmNRT8lOW/assets/1060fe22c4f6e1123d64.webp)

(2) Computer network card configuration:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/FZa27DjiXfwx6eXWYhJ3/assets/17690f41d28f80f3e320.webp)

(3) Computer firewall configuration:

To allow Orbbec Viewer to communicate through Windows Defender Firewall, follow the path below: Control Panel\System and Security\Windows Defender Firewall

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Wd6N2ee17BqdGjYdui3Y/assets/3df48dc51e713e9441d3.webp) ![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/4IbnYoeLf8ExsoZ7BOgk/assets/5d7ffca0dc826e8827e1.webp)

**4. Start Orbbec Viewer for Experiencing**

Once the environment and configurations are properly set up as described in the previous sections, you can start experiencing the Gemini 335Le by launching the provided Orbbec Viewer tool on Windows platforms, as shown in the image below:

Open the Orbbec Viewer tool, select the Gemini 335Le network device you want to open, and click Open:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IWGVvnsxvw5ezEcZkB1v/assets/258b344e6651e1bcf3ed.webp)

Once the device is successfully loaded, the detailed functionality window will appear, allowing you to start the experience:

![Official Orbbec figure from Gemini 330 Series Quickstart Guide (Ethernet)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/6CM8A6geMm37IFmvoo1b/assets/42f20186157dde694fa8.webp)

#### Gemini 335Lg Recommended FAKRA Connector & Cable Specifications <a href="#gemini-335lg-recommended-fakra-connector-and-cable-specifications" id="gemini-335lg-recommended-fakra-connector-and-cable-specifications"></a>

_Reviewed source:_ [_Gemini 335Lg Recommended FAKRA Connector & Cable Specifications_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20335Lg%20Recommended%20FAKRA%20Connector%20&%20Cable%20Specifications)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
This chapter concerns the GMSL/FAKRA variant and its stated reference host/driver. It is retained as an interface comparison; the assigned USB and PoE SKUs are not GMSL cameras. Match camera firmware, deserializer/carrier, JetPack/L4T and kernel module before using a driver command. A command from an older reference kernel is not portable to another Jetson image.
{% endhint %}

This documentation illustrates the recommended FAKRA connector and cable specifications for Gemini 335Lg.

#### 1. FAKRA Connector Introduction <a href="#id-1.-fakra-connector-introduction" id="id-1.-fakra-connector-introduction"></a>

FAKRA (Fachkreis Automobil, a German standard) connectors are SMB based automotive-grade connectors that can operate up to 6 GHz. These connectors are embedded within a plastic housing with a locking feature that has an audible clicking noise which lets you know a connection has been made. They are available in 14 different mechanical layouts, which are color coded for easy identification and mis-matching prevention.

Orbbec Gemini 335Lg is equipped with FAKRA-Z connector.

![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/FTAHN985y35dE0B4cIhO/assets/54ad23af05f8da613463.webp)

Figure 1-1 Different FAKRA Connectors

#### 2. Recommended Cable <a href="#id-2.-recommended-cable" id="id-2.-recommended-cable"></a>

The Gemini 335Lg camera utilizes ADI’s GMSL2 technology, a cost-effective, simple, and scalable SerDes solution. Fakra cables, which connect the Serializer and Deserializer, have a significant impact on the performance of the GMSL2 channel. Different cables have various characteristics and are suited for different applications.

For example, lightweight and flexible cables with a small bending radius usually have thinner wire cores, which require less copper and are relatively low-cost. However, their insertion loss and return loss characteristics are not the best, making them suitable for short-distance applications where the equipment is not fixed and may require frequent bending. On the other hand, cables with thicker wire cores have better insertion and return loss characteristics, making them ideal for long-distance transmission and fixed installations where the equipment doesn’t need to be moved. However, the thicker wire cores also come with higher costs. Regardless of the cable type chosen, it must meet ADI’s GMSL2 channel specifications.

The serializer chip used in Gemini 335Lg camera is the MAX9295D, which supports both coaxial and twisted-pair transmission. Since the module also utilizes POC (Power over Coax) technology, the external Fakra connection cable must be coaxial. Below is a table listing the key parameters for selecting Fakra cables, based on ADI’s GMSL2 technical documentation.

Table 2-1 Cable specifications

| Category                                      | Recommend Spec.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Notes                                                                                                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cable type                                    | Coaxial cable                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/10/20025657/Gemini335lgdocs202410206.png)                                                                                                                                                                                                                                                                                                  |
| Transmission frequency range                  | 0 \~ 6GHz                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Characteristic impedance                      | 50Ω ± 2Ω                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Reconmended                                                                                                                                                                                                                                                                                                                                                                                                     |
| Rated current                                 | ≥ 1A                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Typical POC voltage: 12V；Ripple: ≤ ±10%                                                                                                                                                                                                                                                                                                                                                                         |
| DC resistance                                 | ＜ 0.1Ω/m                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Insulation withstanding voltage               | ≥ 500V AC                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Insulation resistance                         | ≥ 100MΩ                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Contact resistance                            | ≤ 5mΩ (Initial)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Cable length                                  | The maximum length of commonly used cables are listed as follows: RG174：≤5m Dacar 302/RG58：≤15m                                                                                                                                                                                                                                                                                                                                                                                                                                                               | According to [ADI’s MAX9295D datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/max9295d.pdf) , “Cables with an attenuation of 1.1dB/m can support up to a maximum length of 15m (3.2mmφ, 6Gbps, 105℃).” Detailed information is in page 1.                                                                                                                                         |
| Bend radius                                   | RG174: Static 3x cable OD；Dynamic 10x cable OD Dacar 302： Static 5x cable OD；Dynamic 15x cable OD                                                                                                                                                                                                                                                                                                                                                                                                                                                             | OD: Out Diameter                                                                                                                                                                                                                                                                                                                                                                                                |
| Insertion loss (IL)                           | −17dB MAX @ 3GHz (6Gbps / 187.5Mbps)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Information is according to “ [GMSL2 Channel Specification User GuideRev 1](https://www.analog.com/media/en/technical-documentation/user-guides/gmsl2-channel-specification-user-guide.pdf) “. Detailed information is in page 16.                                                                                                                                                                              |
| Return loss (RL)                              | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/10/20043416/Gemini335lgdocs202410207.png)                                                                                                                                                                                                                                                                                                                                                                                                                                                | Information is according to “ [GMSL2 Channel Specification User GuideRev 1](https://www.analog.com/media/en/technical-documentation/user-guides/gmsl2-channel-specification-user-guide.pdf) “. Detailed information is in page 16.                                                                                                                                                                              |
| Tensile strength                              | ≥ 110N                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Ingress protection                            | IP67 (recommended)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Ambient temperature                           | -40 \~ 105℃                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Recommended cable and connector manufacturers | Cable: Amphenol RF, Belden wire & cable, TE Connectivity, HUBER + SUHNER, Lenoi, etc. Connector: Rosenberger, Molex, TE Connectivity, Amphenol RF, etc.                                                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Recommended cables                            | Allied Vision, Inc. [https://www.wdlsystems.com/allied-vision-18424](https://www.wdlsystems.com/allied-vision-18424) [https://www.digikey.com.au/en/products/detail/allied-vision-inc/CABLE-FPD-LINK-III-GMSL2-5M-COAX/22195452](https://www.digikey.com.au/en/products/detail/allied-vision-inc/CABLE-FPD-LINK-III-GMSL2-5M-COAX/22195452) Amphenol RF: [https://www.mouser.com/ProductDetail/Amphenol-RF/095FJZFJZSHM500?qs=zW32dvEIR3sjRLgtRmvHeA%3D%3D](https://www.mouser.com/ProductDetail/Amphenol-RF/095FJZFJZSHM500?qs=zW32dvEIR3sjRLgtRmvHeA%3D%3D) | [https://www.mouser.com/datasheet/2/18/2/](https://www.mouser.com/datasheet/2/18/2/Amphenol_RF_FAKRA_Cable_Assemblies_Cutsheet-3440413.pdf) [Amphenol\_RF\_FAKRA\_Cable\_Assemblies\_](https://www.mouser.com/datasheet/2/18/2/Amphenol_RF_FAKRA_Cable_Assemblies_Cutsheet-3440413.pdf) [Cutsheet-3440413.pdf](https://www.mouser.com/datasheet/2/18/2/Amphenol_RF_FAKRA_Cable_Assemblies_Cutsheet-3440413.pdf) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3JTi6v5XJ9nDka8xQrE5/assets/2fefae1c474cc315757d.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/fM54CzGNvwIu9ZxHj7M1/assets/331b875783ad23aa9e89.webp)

#### 3. Orbbec Default Cable Drawings <a href="#id-3.-orbbec-default-cable-drawings" id="id-3.-orbbec-default-cable-drawings"></a>

**i. Orbbec Box-packed Gemini 335Lg Default Cable Drawing**

![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/DBIhjzh6sQvtj7bIcgJK/assets/9db81cc26b14b1f2fdef.webp)

**ii. Orbbec Gemini 335Lg FAKRA Connector Drawing**

![Official Orbbec figure from Gemini 335Lg Recommended FAKRA Connector & Cable Specifications](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/r50x1LH8pUHVw90kKyAC/assets/a4100ab38a4e79b2499c.webp)

#### Gemini 335Lg Hardware Synchronization <a href="#gemini-335lg-hardware-synchronization" id="gemini-335lg-hardware-synchronization"></a>

_Reviewed source:_ [_Gemini 335Lg Hardware Synchronization_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20335Lg%20Hardware%20Synchronization)_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
Match the exact camera, connector view and synchronization accessory before wiring. USB supply voltage is not the GPIO logic level. Retain source timing/units with recordings; first capture is free-running with optional sync disconnected.

This chapter concerns the GMSL/FAKRA variant and its stated reference host/driver. It is retained as an interface comparison; the assigned USB and PoE SKUs are not GMSL cameras. Match camera firmware, deserializer/carrier, JetPack/L4T and kernel module before using a driver command. A command from an older reference kernel is not portable to another Jetson image.
{% endhint %}

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

#### Explore Camera Functions in Orbbec Viewer (Gemini 330 Series) <a href="#explore-camera-functions-in-orbbec-viewer-gemini-330-series" id="explore-camera-functions-in-orbbec-viewer-gemini-330-series"></a>

_Reviewed source:_ [_Explore Camera Functions in Orbbec Viewer (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Explore%20Camera%20Functions%20in%20Orbbec%20Viewer%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

With one application owning the camera, open its device panel, select a supported depth profile and start depth alone. Inspect live frame rate, exposure and the log before adding color or filters. Save a short recording with its profile and metadata, then stop streams before changing work mode. [Viewer v2 control reference, 52 pages](https://doc.orbbec.com/attachments/7).

[Explore Camera Functions in Orbbec Viewer (Gemini 330 Series).pdf](https://doc.orbbec.com/attachments/7)

#### Stereo 3D Camera <a href="#stereo-3d-camera" id="stereo-3d-camera"></a>

_Reviewed source:_ [_Stereo 3D Camera_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Stereo%203D%20Camera)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Introduction <a href="#id-1.-introduction" id="id-1.-introduction"></a>

A stereo 3D camera is a type of camera equipped with two or more lenses, each with its own image sensor or film frame. This configuration allows the camera to capture images from slightly different angles, simulating the human binocular vision. The primary purpose of a stereo 3D camera is to provide depth perception and create 3D images. The Gemini 330 series 3D cameras combine active and passive stereo vision technologies for seamless operation in both indoor and outdoor conditions.

**Working Principle:**

* **Stereoscopic Vision**: By capturing two images from different perspectives, a stereo 3D camera can calculate the distance to objects in the scene. This process involves measuring the disparity between the two images and using it to triangulate the depth.
* **Image Processing**: Advanced algorithms are used to analyze the images captured by the two lenses. These algorithms match corresponding points in both images to compute depth information, generating a 3D representation of the scene.

For the Orbbec Gemini 330 series cameras, the implementation of the working principle is completed on the Orbbec’s latest custom ASIC.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5dyblUcwfNZ9V63En9LP/assets/7aa068b4ed9a2333415c.webp)

Figure 1. Gemini 335 Stereo 3D Camera

#### 2. Baseline <a href="#id-2.-baseline" id="id-2.-baseline"></a>

The baseline is the distance between the two cameras in a stereo setup, namely, the distance between two IR cameras as shown in Figure 1. A longer baseline increases depth accuracy but also increases the size of the setup. Proper baseline selection is crucial for balancing depth resolution and device compactness.

#### 3. Field of View(FOV) <a href="#id-3.-field-of-view-fov" id="id-3.-field-of-view-fov"></a>

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

#### 4. Blind Spots <a href="#id-4.-blind-spots" id="id-4.-blind-spots"></a>

Blind spots in 3D cameras are areas where the camera cannot capture depth information accurately. These are usually found at the edges of the FOV or the closest distance between the camera and the object. When the object is not visible in either the left or right image, accurate depth information cannot be obtained. The depth camera uses the left camera as the main camera, and the depth blind spots are the green and gray areas shown in the figure below.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/C4xg8VKhY9H5u2Mc3c2Z/assets/c227de91c4bd0aa8fe2b.webp)

Figure 5. Depth blind spots

#### 5. Depth Dark Borders <a href="#id-5.-depth-dark-borders" id="id-5.-depth-dark-borders"></a>

Depth black edges, or dark borders, in stereo 3D cameras refer to areas in the depth map where depth information is either missing or incorrect. These edges often appear at the boundaries of objects where there is a significant depth discontinuity.

**Cause of Depth Dark Borders**:

* **Baseline**: Stereo 3D cameras work by capturing two images from slightly different perspectives and then calculating the disparity (difference) between these images to estimate depth. These occur when objects seen in one image are not visible in the another due to FOV and baseline limitations, as shown in the green blind spots above.
* **Occlusions**: These occur when parts of one image are not visible in the other due to obstruction by an object. This leads to missing depth information, often resulting in black edges in the depth map.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oHOnyGpE6T6541SmqGGR/assets/ff6fc2f3aff25332c19b.webp)

Figure 6. Depth Dark Borders

#### 6. Depth Error <a href="#id-6.-depth-error" id="id-6.-depth-error"></a>

The errors of stereo 3D cameras are primarily influenced by disparity errors, which are related to the reflectivity of the measured object, image signal-to-noise ratio, algorithm errors, and other factors.

Depth is consequently derived from this equation:

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jkYrybEim00tzwmydvTe/assets/bd701412bf48445018ee.webp)

By differentiating the disparity, we can derive the depth error as follows:

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/XJ5EXEGhqp4NC0YW8ugY/assets/3f7712b7542be62a6ba4.webp)

It can be seen that the depth error of binocular vision increases parabolically (proportional to the square of the distance) as the distance increases.

![Official Orbbec figure from Stereo 3D Camera](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Eq2wTZ6UH8qvbKUdQ0ia/assets/55f3482e1c7429063d8b.webp)

Figure 7. Depth error(mm) as the distance(mm) increases

#### Depth from HDR Imaging <a href="#depth-from-hdr-imaging" id="depth-from-hdr-imaging"></a>

_Reviewed source:_ [_Depth from HDR Imaging_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20from%20HDR%20Imaging)_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Introduction <a href="#id-1.-introduction-1" id="id-1.-introduction-1"></a>

For image sensors, the primary challenge lies in capturing both dimly lit indoor scenes and brightly illuminated outdoor settings in the same high-quality image, such as photographing a person standing by the window indoors. Typical image sensors generally adjust exposure or gain to ensure quality imaging in low-light or high-illumination conditions. Robots face various challenges in this regard, such as autonomous mobile robots (AMR) that must operate precisely in environments where sunlight and shadow coexist; robotic vacuum cleaners working near windows face issues with (bright and dark areas in the same view)areas overly bright from sunlight and objects too dark from backlighting. In scenarios where dark and bright areas coexist, using long exposure could result in over-exposure of the bright area, while short exposure might fail to capture details in the darker area. The ORBBEC Gemini 330 Series stereo vision 3D cameras also encounter a similar challenge because their 3D images are calculated from a pair of high-quality, left and right images.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/RJJKiAfUxBSUa8KhV3bt/assets/da40a74a09e1f437b7df.webp)

Figure 1. The scene near the windows. Bright and black areas in the same view.

High Dynamic Range (HDR) imaging in computer vision and cinematography is a set of techniques aiming at handling enormously wide exposure range (i.e., images with greater contrast between light and dark) compared to traditional digital imaging technologies, by merging multiple frames. For 3D depth cameras, higher dynamic range means higher depth fill-rate and higher accuracy, significantly enhancing a robot’s obstacle avoidance capabilities. This paper introduces fundamental concepts related to HDR functionality and introduces how HDR is utilized in the ORBBEC Gemini 330 Series cameras.

#### 2. Sensor Settings <a href="#id-2.-sensor-settings" id="id-2.-sensor-settings"></a>

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

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rboDEt0ReURwpl2CcI35/assets/c01250a9eee579be1165.webp)

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/o1Bv3QOEMB4ZjTqqQqKw/assets/04e5269a6e9a16c6d1a3.webp)

Figure 7. Effect of auto-exposure indoors(top) and outdoors(bottom): left – infrared image, right – depth image.

By default, Gemini 330 series cameras are configured in auto-exposure mode. Under this mode, the camera will automatically adjust exposure and gain values until the average image intensity reaches a certain preset value. Auto exposure can also be turned on/off in the Orbbec viewer.

Auto exposure criteria can be set up as well, in case the preset average intensity value is not proper for the use case. If the IR images are too dark or too bright, the user can manually change the Mean Intensity Set Point, which can be set under the IR Left/IR Right/Depth control panel.

![Official Orbbec figure from Depth from HDR Imaging](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/KRz7U47YaRmSqVLbTNiD/assets/3b0b752e7edc7bd6da84.webp)

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

#### 4. Challenges of Stereo Vision 3D Cameras <a href="#id-4.-challenges-of-stereo-vision-3d-cameras" id="id-4.-challenges-of-stereo-vision-3d-cameras"></a>

**4.1 Sensitivity to Ambient Light**

Stereo vision usually captures image pairs with ambient light in the environment. However, differences in light intensity and incident light angles between the left and right cameras can lead to significant differences in brightness between the left and right images of a stereo pair, resulting in a sharp decline in algorithmic matching effectiveness.

**4.2 Poor Performance in Monotonous and Textureless Scenes**

Stereo vision relies on visual features for image matching. Therefore, scenes lacking visual features, such as the sky or white walls, can pose matching difficulties, leading to significant matching failures or even errors. Adding laser speckle projection can enhance features in low-texture scenes, but in certain situations, ambient light can reduce the contrast of laser speckles or even obscure their grayscale information.

#### 5. Using Filters <a href="#id-5.-using-filters" id="id-5.-using-filters"></a>

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

![Official Orbbec figure from Depth Quality Metrics](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/sj7Jtj1bXdJiD3awZe0f/assets/af067c0a07c6f347b676.webp)

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

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/94OqClDe76mhRCuQKQq4/assets/e7eae98014be6f213115.webp)

1. Unit: The Default unit is millimeters.

#### 3. Gemini 330 Series System Coordinate <a href="#id-3.-gemini-330-series-system-coordinate" id="id-3.-gemini-330-series-system-coordinate"></a>

Gemini 330 series coordinate system reference picture is shown below.

Picture 2: Coordinate system schematic diagram

![Official Orbbec figure from Coordinate Systems (Stereo Vision 3D Camera)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3OZxyKX3ulYM28xW50NG/assets/5ffc5616db06fc590f36.webp)

The relative position relationship of the coordinate systems' origins is as follows.

Table 1: Relative position of coordinate systems for Gemini 335/336

\*\*Relative position\*\*\*\*X(mm)\*\*\*\*Y(mm)\*\*\*\*Z(mm)\*\*Origin of the Depth coordinate system000Origin of the Color coordinate system14.0002.02Origin of the IMU coordinate system-0.246-0.065-16.948Table 2: Relative position of coordinate systems for Gemini 335L/336L

\*\*Relative position\*\*\*\*X(mm)\*\*\*\*Y(mm)\*\*\*\*Z(mm)\*\*Origin of the Depth coordinate system000Origin of the Color coordinate system23.7500Origin of the IMU coordinate system7.8661.068-14.248

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

#### 2. Linux /Arm64 Installation Guidance <a href="#id-2.-linux-arm64-installation-guidance" id="id-2.-linux-arm64-installation-guidance"></a>

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

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ovmIv8Iz7JgvXD8JIoxl/assets/11ef93a0a36ea25b8125.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/image.png)

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/LUvPQ9LrJ5sqLK83iztX/assets/a84a7598a3a69c8ae458.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/cc1image.png)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qnPQwMYfhV9DVkVor84M/assets/1cfa1d91b1de4138e9c7.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/oL5image.png)

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/h67d2BEqwytUZpRerFTZ/assets/44c54a2a9c78b34db24d.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/ZT6image.png)

At close range, depth values are more similar. When capturing flat surfaces, false positives may cause lateral depth loss.

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/axKvhPrKyT9ODQbgXek9/assets/5b048624b966bcd309df.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/9v4image.png)

**\*\*4.4 FalsePositiveFilter::\*\*TextureSparsityFilter**

\*\*Function:\*\*Filters out erroneous depth in low-texture scenes. \*\*Typical scenarios:\*\*outdoor white walls, non-overexposed sky, etc. \*\*Rule:\*\*Within the depth map ROI, noise regions that satisfy both of the following conditions will be filtered out:

l Average depth value of noise region < fptsfMaxNoiseLevel

l Pixel area of noise cluster < fptsfMaxSpeckleSize

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/OuDgJle9FDaiTWdo5ICs/assets/3028b3ea1c9d8813daf9.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/h6himage.png)

**\*\*4.5 FalsePositiveFilter::\*\*PatternAmbiguityFilter**

\*\*Function:\*\*Filters out erroneous depth in repetitive texture scenes. \*\*Typical scenarios:\*\*fences, building windows, etc. \*\*Rule:\*\*Within the depth map ROI, noise regions that satisfy ALL of the following conditions will be filtered out:

l Average depth value of noise region < fppafMaxNoiseLevel

l Pixel area of noise cluster < fppafMaxSpeckleSize

l Noise cluster width < image width × fppafMaxWidthRatio

l Noise cluster height < image height × fppafMaxHeightRatio

l Noise Tolerance feature > fppafTolerance

l Noise Score feature > fppafScore

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EK28EpO3tWprMSlw1qkv/assets/f962017bd982652165ef.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/WC9image.png)

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/SX96BYOW15aAGpSz62da/assets/0fb0c868178ec0dc5b2f.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/GWhimage.png)[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/9eZCifSB3PugxThZdGqF/assets/274893fb8da7c4bf6a47.webp)](https://doc.orbbec.com/uploads/images/gallery/2026-08/jvHimage.png)

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

#### 2. Update Firmware <a href="#id-2.-update-firmware" id="id-2.-update-firmware"></a>

{% hint style="info" %}
Read the camera identity and current firmware first, save settings, stop streams, and use only the exact model/hardware package. The older Viewer screenshots describe an update workflow, not permission to flash another model or repeat updates through an unresolved power/network fault. Use the release/firmware pairing in the core software section; restore power only at the updater’s documented checkpoint.
{% endhint %}

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

If an update fails, preserve the error and first resolve power, connection and exact-image compatibility. Retry only through the model’s documented recovery workflow; do not repeatedly flash to diagnose an unidentified fault.

**2.2 Offline Update via Orbbec Viewer**

The difference between offline and online updates is as follows: With online updates, the firmware is automatically downloaded from the server (downloaded to the "output/firmwareFile" directory in Orbbec Viewer), and then the device is updated. However, with offline updates, you manually select the firmware path and then proceed with the update. The interface is as follows:

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/WoPkNwzTj8GDAmuiunx2/assets/067fc37f8cc08ccbed88.gif)

After clicking "Upgrade," the subsequent update steps are the same as the online update.

**2.3 Code Sample**

1. The firmware update reference for Orbbec SDK V1.x.x version is available in the sample at the following link: [https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade](https://github.com/orbbec/OrbbecSDK/tree/main/examples/cpp/Sample-FirmwareUpgrade)2. The firmware update reference for Orbbec SDK V2.x.x version is available in the sample at the following link: [https://github.com/orbbec/OrbbecSDK\_v2/tree/main/examples/2.device.firmware\_update](https://github.com/orbbec/OrbbecSDK_v2/tree/main/examples/2.device.firmware_update)

#### 3. Handle Update Exception <a href="#id-3.-handle-update-exception" id="id-3.-handle-update-exception"></a>

If there is a power failure or the USB cable is unplugged during the online update process, the device may enter Recovery mode. In this case, you will need to perform an offline update using the firmware downloaded online. The path to the online firmware download is in the "output/firmwareFile" directory of Orbbec Viewer, for example, on the Windows platform, as shown in the following figure.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/6vfdWFpC9904eU2mxvvp/assets/5072435cdcd691142459.gif)

If the device enters Recovery mode but there is no firmware available, please download the firmware from the product’s firmware download page first. Then, follow the offline update method to perform the update.

**Notes: (Very Important)**

In Recovery mode, ISP firmware update is not supported. You need to enter Normal mode and perform the firmware update again to ensure ISP firmware matches the current system. (In Recovery mode, firmware needs to be updated twice.)

#### 4. Update Orbbec Viewer <a href="#id-4.-update-orbbec-viewer" id="id-4.-update-orbbec-viewer"></a>

If there is a new version of Orbbec Viewer available for update, when opening Orbbec Viewer, there will be a prompt in the top right corner: "A new version of the tool can be updated." Click on this prompt, and it will link to the download directory of Orbbec Viewer on GitHub. Please download the corresponding platform’s Orbbec Viewer.

![Official Orbbec figure from Update Firmware (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nQpTKlOhqKsxQXGhrz8D/assets/170acd9ee68d647fee12.gif)

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

#### Gemini 330 Series Supported Hosts and System Requirements (GMSL) <a href="#gemini-330-series-supported-hosts-and-system-requirements-gmsl" id="gemini-330-series-supported-hosts-and-system-requirements-gmsl"></a>

_Reviewed source:_ [_Gemini 330 Series Supported Hosts and System Requirements (GMSL)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Gemini%20330%20Series%20Supported%20Hosts%20and%20System%20Requirements%20\(GMSL\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The chapter retains its documented SDK/API generation. Older `deviceCount()`, `name()` and K4A examples are reference implementations, not a claim that they compile against Orbbec SDK v2.10.6. Use the original version-pinned first-result program above for that release. Package names, OS baselines, wrappers and firmware must be matched independently; no retained example or installer was executed in this review.

This chapter concerns the GMSL/FAKRA variant and its stated reference host/driver. It is retained as an interface comparison; the assigned USB and PoE SKUs are not GMSL cameras. Match camera firmware, deserializer/carrier, JetPack/L4T and kernel module before using a driver command. A command from an older reference kernel is not portable to another Jetson image.

PASS and Not tested entries below are the manufacturer’s results for its listed host/OS/SDK configuration, not tests performed for this guide. Recheck the current release platform matrix before applying an older host result to a new SDK or kernel.
{% endhint %}

The GMSL Series cameras are the latest GMSL2 stereo camera launched by Orbbec. To preview variable data streams and apply them in business development, the camera should be connected to a host that supports GMSL2 to MIPI CSI-2 deserialization functionality, such as the NVIDIA Jetson ecosystem equipped with a GMSL camera board. The Gemini 335Lg has been officially adapted by Orbbec and ecosystem partners, ensuring its compatibility with a wide range of host solutions, such as developer kit, turnkey system, and modular stacks.

For the convenience of users in quick testing and development, Orbbec provides precompiled GMSL drivers for the NVIDIA Jetson AGX Orin developer kit solution in the official Github repository. For compatibility with other solutions such as turnkey system and modular stacks, you can contact our partners for support.

Three types of solutions are supported: developer kit, turnkey system, and modular stacks.

| Category                                                                    | Supported Hardware                                               | Supported Hardware                                               | Supported Hardware                                               | Supported Hardware                                               | Supported Hardware                                               | Hardware Platform              |
| --------------------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------ |
| Developer Kit + GMSL2 Camera Broad                                          | NVIDIA Jetson AGX Orin Developer Kit                             | NVIDIA Jetson AGX Orin Developer Kit                             | NVIDIA Jetson AGX Orin Developer Kit                             | +                                                                | FG96-8CH-V2                                                      | NVIDIA Jetson AGX Orin™        |
| <p>Turnkey System<br><br></p>                                               | ADVANTECH MIC-733-AO                                             | ADVANTECH MIC-733-AO                                             | ADVANTECH MIC-733-AO                                             | ADVANTECH MIC-733-AO                                             | ADVANTECH MIC-733-AO                                             | NVIDIA Jetson AGX Orin™        |
| <p>Turnkey System<br><br></p>                                               | Connect Tech Inc. Anvil Embedded System                          | Connect Tech Inc. Anvil Embedded System                          | Connect Tech Inc. Anvil Embedded System                          | Connect Tech Inc. Anvil Embedded System                          | Connect Tech Inc. Anvil Embedded System                          | NVIDIA Jetson AGX Orin™        |
| <p>Turnkey System<br><br></p>                                               | Axiomtek AIE510-ONX                                              | Axiomtek AIE510-ONX                                              | Axiomtek AIE510-ONX                                              | Axiomtek AIE510-ONX                                              | Axiomtek AIE510-ONX                                              | NVIDIA Jetson Orin™ NX         |
| <p>Turnkey System<br><br></p>                                               | Seeed Studio reComputer Robotics J5012/J5011 with GMSL Extension | Seeed Studio reComputer Robotics J5012/J5011 with GMSL Extension | Seeed Studio reComputer Robotics J5012/J5011 with GMSL Extension | Seeed Studio reComputer Robotics J5012/J5011 with GMSL Extension | Seeed Studio reComputer Robotics J5012/J5011 with GMSL Extension | NVIDIA Jetson AGX Orin™        |
| <p>Turnkey System<br><br></p>                                               | Seeed Studio reComputer Robotics J4012 with GMSL Extension       | Seeed Studio reComputer Robotics J4012 with GMSL Extension       | Seeed Studio reComputer Robotics J4012 with GMSL Extension       | Seeed Studio reComputer Robotics J4012 with GMSL Extension       | Seeed Studio reComputer Robotics J4012 with GMSL Extension       | NVIDIA Jetson Orin™ NX         |
| <p>Turnkey System<br><br></p>                                               | Seeed Studio reComputer Robotics J3011 with GMSL Extension       | Seeed Studio reComputer Robotics J3011 with GMSL Extension       | Seeed Studio reComputer Robotics J3011 with GMSL Extension       | Seeed Studio reComputer Robotics J3011 with GMSL Extension       | Seeed Studio reComputer Robotics J3011 with GMSL Extension       | NVIDIA Jetson Orin™ Nano Super |
| <p>Turnkey System<br><br></p>                                               | ADVANTECH MIC-742-AT                                             | ADVANTECH MIC-742-AT                                             | ADVANTECH MIC-742-AT                                             | ADVANTECH MIC-742-AT                                             | ADVANTECH MIC-742-AT                                             | NVIDIA®Jetson Thor™            |
| <p>Modular Stacks (Carrier Board + SOM + GMSL Camera Board)<br><br><br></p> | Connect Tech Inc. Forge Carrier AGX201                           | +                                                                | NVIDIA Jetson AGX Orin SOM                                       | +                                                                | Connect Tech JCB002                                              | NVIDIA Jetson AGX Orin™        |
| <p>Modular Stacks (Carrier Board + SOM + GMSL Camera Board)<br><br><br></p> | Connect Tech Inc. Rogue Carrier AGX202                           | +                                                                | NVIDIA Jetson AGX Orin SOM                                       | +                                                                | Connect Tech JCB002                                              | NVIDIA Jetson AGX Orin™        |
| <p>Modular Stacks (Carrier Board + SOM + GMSL Camera Board)<br><br><br></p> | Connect Tech Inc. Rogue-RX Carrier AGX203                        | +                                                                | NVIDIA Jetson AGX Orin SOM                                       | +                                                                | Connect Tech JCB002                                              | NVIDIA Jetson AGX Orin™        |
| <p>Modular Stacks (Carrier Board + SOM + GMSL Camera Board)<br><br><br></p> | Seeed Studio reComputer Mini J501                                | +                                                                | NVIDIA Jetson AGX Orin SOM                                       | +                                                                | <p>GMSL Board<br></p>                                            | NVIDIA Jetson AGX Orin™        |
| <p>Modular Stacks (Carrier Board + SOM + GMSL Camera Board)<br><br><br></p> | AVerMedia D331                                                   | +                                                                | NVIDIA Jetson Thor SOM                                           | +                                                                | AVerMedia GMSL Board                                             | NVIDIA Jetson Thor™            |

Driver version support status:

| Driver version   | Cameras Supported                                  | <p>Precompiled Driver<br></p>                                                |
| ---------------- | -------------------------------------------------- | ---------------------------------------------------------------------------- |
| Basic Version    | Gemini 335Lg,Gemini 338Lg                          | [Orbbec repositories](https://github.com/orbbec/MIPI_Camera_Platform_Driver) |
| V1.2.10 or above | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg             | [Orbbec repositories](https://github.com/orbbec/MIPI_Camera_Platform_Driver) |
| V1.2.12 or above | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g | [Orbbec repositories](https://github.com/orbbec/MIPI_Camera_Platform_Driver) |

#### 1. Developer Kit Solution <a href="#id-1.-developer-kit-solution" id="id-1.-developer-kit-solution"></a>

**1.1 NVIDIA Jetson AGX Orin Developer Kit**

The NVIDIA Jetson AGX Orin developer kit comes with a computing power of 275TOPS, 64GB of RAM, and a 120-pin 16-lane MIPI connector. To connect the Gemini 335Lg to this developer kit, a compatible GMSL camera board is required. Please refer to the below information:

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                                                                                                                                                                                |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/jetson-orin/">NVIDIA Jetson AGX Orin Developer Kit</a> &#x26; Compatible Power Supply<br>• 1 x GMSL Series camera EVK (including 1 x GMSL2 camera GMSL Series camera, 1 x GMSL camera board, 1 x power conversion cable)<br>• 1 x Compatible Power Supply for GMSL Camera Board<br>• It is also possible to connect additional Gemini 335Lg cameras.</p> |
| Connection Diagram                              | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-11/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-11/image.png)                                                                                                                                                                                                                                                                                |
| Hardware Platform                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                                                                                                                                                                                      |
| JetPack Version                                 | 6.0/6.2/7.2                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Precompiled Driver                              | [O rbbec repositories](https://github.com/orbbec/MIPI_Camera_Platform_Driver)                                                                                                                                                                                                                                                                                                                                                                |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/XVcQwybFXj6LK3iiaUbx/assets/9134296b741a323ba559.webp)

#### 2. Turnkey Systems Solution <a href="#id-2.-turnkey-systems-solution" id="id-2.-turnkey-systems-solution"></a>

**2.1 ADVANTECH Turnkey System**

The GMSL series cameras have been adapted to the MIC-742-AT standalone Turnkey system launched by advanced intelligent device manufacturer Advantech Technology Co., Ltd., which is a fanless ultra compact AI Inference System system based on NVIDIA®Jetson Thor™. Unlike the development kit, the standalone machine comes with a deserter board that supports direct integration with GMSL cameras. For detailed information, please consult Advantech. The specific adaptation of this scheme is shown in the table below:

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://www.advantech.com/en/products/965e4edb-fb98-429e-89ed-9a0a8435a7be/mic-742%E2%80%8B/mod_79762a8d-c514-4c3f-b391-7f56a995b758">MIC-742-AT</a> &#x26; Compatible Power Supply<br>• 1 x - 8 x GMSL Series cameras<br>• 1 x - 8 x Power Conversion Cables</p>                                                |
| Connection Diagram                              | ![Official manufacturer figure](https://alidocs.dingtalk.com/core/api/resources/img/5eecdaf48460cde51f4478fe98e982d366dfbda7cd7ba53875b8339e1c4c248347618140e0f585628d68742cd653602a0524375348f90ffd7e15542712c204a96c07bc3dcf7bf14ecdf42f28da8666f7cdaeba37e570356e8c92666e01c74854?tmpCode=938a532d-a6c6-46e3-bfa8-9e41fe7a13c4) |
| Hardware Platform                               | NVIDIA®Jetson Thor™                                                                                                                                                                                                                                                                                                                |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                                                                 |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                                                                                                                                  |
| Driver Support                                  | Please contact [Advantech](https://www.advantech.com/en-us)                                                                                                                                                                                                                                                                        |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/VvnPPq6XzsrOw987SJIJ/assets/38428efa71a835fc4703.webp)

**2.2 ADVANTECH Turnkey System**

The Gemini 335Lg is also compatible with the ADVANTECH MIC-733-AO turnkey system, a fanless ultra-compact edge AI system for AMR & robotics. Unlike the developer kit, the turnkey system comes with a built-in GMSL camera board, which allows direct GMSL camera connection. In the MIC-733 series, there is a dedicated SKU that supports Gemini 335Lg out of the box, while other models in the MIC-733 series require manual driver installation. For more information, please contact Advantech. The compatibility details are as follows:

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                 |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://www.advantech.com/en-us/products/9140b94e-bcfa-4aa4-8df2-1145026ad613/mic-733/mod_09861425-4950-46ab-ad39-1b5522881218">MIC-733-AO</a> &#x26; Compatible Power Supply<br>• 1 x - 4 x GMSL Series cameras<br>• 1 x - 4 x Power Conversion Cables</p> |
| Connection Diagram                              | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-10/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2025-10/image.png)                                                                                                                 |
| Hardware Platform                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                       |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                            |
| Maximum Number of GMSL Series cameras Supported | 4                                                                                                                                                                                                                                                                             |
| Driver Support                                  | Please contact [Advantech](https://www.advantech.com/en-us)                                                                                                                                                                                                                   |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/CzVXIJonqtz0HHg4IWiE/assets/97ef96c2f6abc7a02d0e.webp)

**2.3 Connect Tech Inc. Turnkey System**

Connect Tech Anvil Embedded System comes ready to withstand even the most compute-intensive AI applications with its power-efficient and feature-rich design. It supports up to eight GMSL2 camera inputs, and provides native support for Gemini 335Lg. This joint solution can significantly reduce your overall application development time. The compatibility details are as follows:

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://connecttech.com/product/anvil-embedded-system-with-nvidia-jetson-agx-orin/">Anvil Embedded System</a> &#x26; Compatible Power Supply<br>• 1 x - 8 x GMSL Series cameras<br>• 1 x - 8 x Power Conversion Cables</p> |
| Compatible Device Image                         | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-10/scaled-1680-/pklimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-10/pklimage.png)                                                                          |
| Hardware Platform                               | NVIDIA Jetson AGX Orin™ & AGX Orin™ Industrial                                                                                                                                                                                               |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                           |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                                            |
| Driver Support                                  | Please contact [Connect Tech Inc.](https://connecttech.com/)                                                                                                                                                                                 |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/JM82GgBKBJuSrhfGZfDP/assets/65f4abadd6c2e9b4315a.webp)

**2.4 Axiomtek Turnkey System**

Powered by the NVIDIA Jetson Orin NX 16GB module, the AIE510-ONX is a compact, rugged embedded system engineered for edge AI applications. Specifically, the AIE510-ONX-GMSL integrates 4 Fakra-Z connector for GMSL2 connection, ensuring seamless compatibility with Gemini 335Lg. The whole solution is ideal for high-precision robotics and autonomous mobile robot (AMR) deployments. The compatibility details are as follows:

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                      |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://us.axiomtek.com/Default.aspx?MenuId=Products&#x26;FunctionId=ProductView&#x26;ItemId=27341&#x26;C=AIE510-ONX&#x26;upcat=350">AIE510-ONX</a> &#x26; Compatible Power Supply<br>• 1 x - 4 x GMSL Series cameras<br>• 1 x - 4 x Power Conversion Cables</p> |
| Compatible Device Image                         | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-10/scaled-1680-/UCZimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-10/UCZimage.png)                                                                                                                |
| Hardware Platform                               | NVIDIA Jetson Orin™ NX                                                                                                                                                                                                                                                             |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                 |
| Maximum Number of GMSL Series cameras Supported | 4                                                                                                                                                                                                                                                                                  |
| Driver Support                                  | Please contact [Axiomtek](https://www.axiomtek.com/)                                                                                                                                                                                                                               |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/OVYuAWgiJYRB9l8SkTsA/assets/f2ca3973ac26d594a459.webp)

**2.5 Seed Studio Turnkey System**

Seeed Studio delivers the industry's most comprehensive range of turnkey edge AI systems supporting Gemini 335Lg. Spanning the full NVIDIA Jetson Orin portfolio—from the high-performance AGX Orin to the compact Orin Nano Super—the reComputer series provides flexible deployment options tailored to diverse performance requirements and form factor constraints. Each platform features native GMSL2 connectivity through dedicated extension boards, enabling seamless multi-camera integration for robotics and autonomous mobile robot(AMR) applications.

Supported Platforms:

**2.5.1 NVIDIA Jetson AGX Orin™ Platform**

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                                                                                                                                                       |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://www.seeedstudio.com/reComputer-Robotics-J5011-with-GMSL-extension-board-p-6681.html">reComputer Robotics J5011 with GMSL</a> / <a href="https://www.seeedstudio.com/reComputer-Robotics-J5012-with-GMSL-extension-board-p-6682.html">reComputer Robotics J5012 with GMSL</a> &#x26; Compatible Power Supply<br>• 1 x - 8 x GMSL Series cameras<br>• 1 x - 8 x Power Conversion Cables</p> |
| Compatible Device Image                         | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-04/scaled-1680-/image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-04/image.png)                                                                                                                                                                                                                                                       |
| Hardware Platform                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                                                                                                                                                             |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                                                                                                                                                  |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Driver Support                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                                                                                                                                                                                                         |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yPN1PXY3LUoBnzQl4h3H/assets/02e72c1f90481dd7c93e.webp)

**2.5.2 NVIDIA Jetson Orin™ NX Platform**

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                 |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://www.seeedstudio.com/reComputer-Robotics-J4012-with-GMSL-extension-board-p-6537.html">reComputer Robotics J4012 with GMSL Extension</a> &#x26; Compatible Power Supply<br>• 1 x - 4 x GMSL Series cameras<br>• 1 x - 4 x Power Conversion Cables</p> |
| Compatible Device Image                         | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-04/scaled-1680-/vG1image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-04/vG1image.png)                                                                                                           |
| Hardware Platform                               | NVIDIA Jetson Orin™ NX                                                                                                                                                                                                                                                        |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                            |
| Maximum Number of GMSL Series cameras Supported | 4                                                                                                                                                                                                                                                                             |
| Driver Support                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                                                                   |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7lLoxwpVVR7e4iRkPt9e/assets/8f0abcd812d37c4c1cbc.webp)

**2.5.3 NVIDIA Jetson Orin™ Nano Super Platform**

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                 |
| ----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1 x <a href="https://www.seeedstudio.com/reComputer-Robotics-J3011-with-GMSL-extension-board-p-6538.html">reComputer Robotics J3011 with GMSL Extension</a> &#x26; Compatible Power Supply<br>• 1 x - 4 x GMSL Series cameras<br>• 1 x - 4 x Power Conversion Cables</p> |
| Compatible Device Image                         | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-04/scaled-1680-/JW6image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-04/JW6image.png)                                                                                                           |
| Hardware Platform                               | NVIDIA Jetson Orin™ Nano Super                                                                                                                                                                                                                                                |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                            |
| Maximum Number of GMSL Series cameras Supported | 4                                                                                                                                                                                                                                                                             |
| Driver Support                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                                                                   |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/lUbkb3rSFY9cmrEGdGXc/assets/d410a29d06de80f0f185.webp)

#### 3. Modular Stacks <a href="#id-3.-modular-stacks" id="id-3.-modular-stacks"></a>

The NVIDIA Jetson modules are essentially system on Modules (SOMs) that require compatible carrier boards for operation. A NVIDIA Jetson developer kit is essentially a combination of a SOM and a carrier board. Orbbec provides adaptation solutions for such cases, with the following details:

**3.1 Connect Tech Inc Modular Stacks Solution**

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1x NVIDIA Jetson AGX Orin SOM &#x26; Compatible Power Supply<br>• 1x Carrier Board<br>• 1x - 8x GMSL Series cameras<br>• 1x GMSL Camera Board &#x26; Compatible Power Supply<br>• 1x - 8x Power Conversion Cables</p>                                                                                                                                                                                                  |
| Supported GMSL Camera Board                     | [Connect Tech JCB002](https://connecttech.com/product/xavier-gmsl-camera-platform/)                                                                                                                                                                                                                                                                                                                                         |
| Supported Carrier Board                         | <p>• <a href="https://connecttech.com/product/forge-carrier-for-nvidia-jetson-agx-orin/">Connect Tech Inc. Forge Carrier AGX201</a><br>• <a href="https://connecttech.com/product/rogue-carrier-for-nvidia-jetson-agx-orin/">Connect Tech Inc. Rogue Carrier AGX202</a><br>• <a href="https://connecttech.com/product/rogue-rx-carrier-board-for-nvidia-jetson-agx-orin/">Connect Tech Inc. Rogue-RX Carrier AGX203</a></p> |
| Connection Diagram                              | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2025-10/scaled-1680-/3iVimage.png)](https://doc.orbbec.com/uploads/images/gallery/2025-10/3iVimage.png)                                                                                                                                                                                                                                                         |
| Hardware Platform                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                                                                                                                                                                                                                     |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                                                                                                                                                                                                                          |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Driver Support                                  | Please contact [Connect Tech Inc.](https://connecttech.com/)                                                                                                                                                                                                                                                                                                                                                                |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/a06gGuAQtBL3tjno0evF/assets/7f69d1a0f66e89e23d9f.webp)

**3.2 Seeed Studio Modular Stacks Solution**

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                              |
| ----------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1x NVIDIA Jetson AGX Orin SOM &#x26; Compatible Power Supply<br>• 1x Carrier Board<br>• 1x - 8x GMSL Series cameras<br>• 1x GMSL Camera Board &#x26; Compatible Power Supply<br>• 1x - 8x Power Conversion Cables</p> |
| Supported GMSL Camera Board                     | • [reComputer Mini J501 Carrier Board for Jetson AGX Orin™ with GMSL Extension](https://www.seeedstudio.com/reComputer-Mini-J501-Carrier-Board-for-Jetson-AGX-Orin-p-6606.html)                                            |
| Supported Carrier Board                         | • [reComputer Mini J501 Carrier Board for Jetson AGX Orin™ with GMSL Extension](https://www.seeedstudio.com/reComputer-Mini-J501-Carrier-Board-for-Jetson-AGX-Orin-p-6606.html)                                            |
| Connection Diagram                              | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-04/scaled-1680-/j90image.png)](https://doc.orbbec.com/uploads/images/gallery/2026-04/j90image.png)                                                        |
| Hardware Platform                               | NVIDIA Jetson AGX Orin™                                                                                                                                                                                                    |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                         |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                          |
| Driver Support                                  | Please contact [Seeed Studio](https://www.seeedstudio.com/)                                                                                                                                                                |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zbjsQB39fGQ2DxNNj7Bf/assets/8d11a436d8044b84e64e.webp)

**3.3 AVerMedia Modular Stacks Solution**

| Source field                                    | Manufacturer-documented value                                                                                                                                                                                          |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Components                                      | <p>• 1x NVIDIA Jetson Thor SOM &#x26; Compatible Power Supply<br>• 1x Carrier Board<br>• 1x - 8x GMSL Series cameras<br>• 1x GMSL Camera Board &#x26; Compatible Power Supply<br>• 1x - 8x Power Conversion Cables</p> |
| Supported GMSL Camera Board                     | • [GMSL Board](https://professional.avermedia.com/product-detail/GMSL-Board)                                                                                                                                           |
| Supported Carrier Board                         | • [AVerMedia D331](https://professional.avermedia.com/product-detail/D331)                                                                                                                                             |
| Connection Diagram                              | [![image.png](https://doc.orbbec.com/uploads/images/gallery/2026-04/scaled-1680-/Jmwimage.png)](https://doc.orbbec.com/uploads/images/gallery/2026-04/Jmwimage.png)                                                    |
| Hardware Platform                               | NVIDIA Jetson Thor™                                                                                                                                                                                                    |
| Verify camera models                            | Gemini 335Lg,Gemini 338Lg,Gemini 345Lg,Gemini 305g                                                                                                                                                                     |
| Maximum Number of GMSL Series cameras Supported | 8                                                                                                                                                                                                                      |
| Driver Support                                  | Please contact [AVerMedia](https://professional.avermedia.com/)                                                                                                                                                        |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/S2ndwUAWGX51NSuc15il/assets/337a161ae4e8293bc569.webp)

#### Reference Design - Mounting (Gemini 330 Series) <a href="#reference-design-mounting-gemini-330-series" id="reference-design-mounting-gemini-330-series"></a>

_Reviewed source:_ [_Reference Design - Mounting (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Mounting%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

#### 1. Overview <a href="#id-1.-overview" id="id-1.-overview"></a>

This document provides the optimal reference mounting design solution for the camera, assisting customers in swiftly implementing it during the product deployment process.

#### 2. Mounting Reference Solution for Gemini 335/336 <a href="#id-2.-mounting-reference-solution-for-gemini-335-336" id="id-2.-mounting-reference-solution-for-gemini-335-336"></a>

**2.1 Product Components**

| Gemini 335                                                                                      | Gemini 336                                                                                      |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115611/202411031.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03115615/202411032.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kX8Z2XtNFR6oJcDefkgn/assets/e0ff30687b421fa169a2.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oC6Yu6fdFyQqsCkK5TE8/assets/9689e5f465e1745d4987.webp)

**2.2 Product Drawing for Gemini 335**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/POt38CnGMw1SPM8TjOmO/assets/69dec62e40205e9c31a9.webp)

**2.3 Product Drawing for Gemini 336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/7Fm4NIPtyh9KJRR7UqIK/assets/0078e07fa5e71c70dd09.webp)

**2.4 Product Interfaces for Gemini 335/336**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EAudRIAr3nVVGxM5Huok/assets/ffd8c769cb1b8957cbca.webp)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the left of the camera, the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port On the right side of the camera, rotate the Sync Port cover to see the Sync Port.

**2.5 Mounting and Fixing Method for Gemini 335/336:**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 5mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/EQNIkv5F7DMc11r2TIFO/assets/78d35886673757cbbd53.webp)

Option B\*\*:\*\*Fix the 3D camera using two M3 thread holes on the rear side, the hole depth is 3.0mm and commended is 0.4Nm

Option C: Fix the 3D Camera using the shape or edges of the metal housing

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kpAIKbtxct8gKv7RCFcU/assets/82a8e185499c9f91c1ce.webp)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, the FOV viewing angle cannot be blocked;

#### 3. Mounting Reference Solution for Gemini 335L/336L <a href="#id-3.-mounting-reference-solution-for-gemini-335l-336l" id="id-3.-mounting-reference-solution-for-gemini-335l-336l"></a>

**3.1 Product Components**

| Gemini 335L                                                                                     | Gemini 336L                                                                                     |
| ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120428/202411038.png) | ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/03120432/202411039.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IcHs3Fsfcxp219HV2OtH/assets/9891dabfe4091cc73fba.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/eQttTPsHUSTzzVMKg9FJ/assets/45a22d6f0657c8faad1f.webp)

**3.2 Product Drawing for Gemini 335L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yuTyaeJu2tgace0gEr5A/assets/f3d9e4e31f24bad06274.webp)

**3.3 Product Drawing for Gemini 336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/jXlTlDyuN1XVC1jaQyHJ/assets/7fcbd9d0555158e4bb3d.webp)

**3.4 Procuct Interface for Gemini 335L/336L**

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/toR5m59vm9kPDfDSxzt6/assets/c7b15528e6c5eb8c7c9e.webp)

**-24 Pin USB Type-C interface**

1. The 24 Pin USB Type-C interface is at the bottom of the camera, the depth of Type-C Female is specified as 6.0±0.2mm. please pay attention to the dimension of Type-C Plug to avoid interference, and secures adequate contact during the insertion of the Type-C plug.
2. The metal exposed section’s length of Type-C Plug:
3. a length of 6.0± 0.2mm is suggested for Type-C plug with screw
4. a length of 6.2±0.2mm is recommended for Type-C plug without screw

**-8 Pin Sync Port :**

The 8 Pin sync port at the top side of the camera, remove the Sync Port protective cover to see the Sync Port.

**3.5 Mounting and Fixing Method for Gemini 335L/336L**

Option A: Fix the 3D camera using the 1/4-20 UNC thread hole, the hole depth is 8mm and commended torque is 4.0Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qHU8RuPa7GiPfxbthtIs/assets/38fd813299e17e6bf6bc.webp)

Option B\*\*:\*\*Fix the 3D camera using two M4 thread holes on the rear side, the hole depth is 3.0mm and commended is 0.4Nm

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/xbiv3YSXvnzp9J2rUYv9/assets/2d0998911b101b8ee40b.webp)

Option C: Fix the 3D Camera using the shape or edges of the metal housing

Illustration for 3D camera mounting

![Official Orbbec figure from Reference Design - Mounting (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qSoJ7oDnNFClhwkUpTEX/assets/c15c8dc7c14c5473794a.webp)

\[Note]]:

1. 1/4-20 UNC threaded hole or other areas on metal parts of module must be utilized for grounding purposes.
2. After the module is assembled to the whole machine, it cannot block the FOV perspective;

#### 4. System Design Requirements <a href="#id-4.-system-design-requirements" id="id-4.-system-design-requirements"></a>

1. Sealing Requirements - Use foam padding or silicone seals between the 3D camera and the customer’s device to prevent dust.
2. Lens Requirements - No additional lenses or covers can be added to the front of the 3D camera.
3. Cooling Requirements - Connect the 3D camera to external metal components using thermal conductive materials to expand the cooling area. It is recommended to incorporate active cooling with fans.

* The 3D cameras must not be heated by other heat sources.

4. Before customer tooling, please provide structural drawings related to the 3D camera for orbbec’s ME review.

-The next step

#### Reference Design - Thermal (Gemini 330 Series) <a href="#reference-design-thermal-gemini-330-series" id="reference-design-thermal-gemini-330-series"></a>

_Reviewed source:_ [_Reference Design - Thermal (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Thermal%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

{% hint style="info" %}
The thermal reference’s graphite-pad phrase “500W” lacks a dimensional conductivity unit. Do not interpret it as a cooling-power rating or silently supply a missing unit. Specify pad conductivity, thickness, contact resistance and actual case/module temperatures from component data before approving a thermal design.
{% endhint %}

#### 1. Overview <a href="#id-1.-overview-1" id="id-1.-overview-1"></a>

This document provides the optimal reference thermal design solution for the camera, assisting customers in quickly implementing effective cooling strategies during product development and deployment.

#### 2. Thermal Reference Solution for Gemini 335/336 <a href="#id-2.-thermal-reference-solution-for-gemini-335-336" id="id-2.-thermal-reference-solution-for-gemini-335-336"></a>

{% hint style="info" %}
The thermal reference’s graphite-pad phrase “500W” lacks a dimensional conductivity unit. Do not interpret it as a cooling-power rating or silently supply a missing unit. Specify pad conductivity, thickness, contact resistance and actual case/module temperatures from component data before approving a thermal design.
{% endhint %}

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

#### 3. Thermal Reference Solution for Gemini 335L/336L <a href="#id-3.-thermal-reference-solution-for-gemini-335l-336l" id="id-3.-thermal-reference-solution-for-gemini-335l-336l"></a>

{% hint style="info" %}
The thermal reference’s graphite-pad phrase “500W” lacks a dimensional conductivity unit. Do not interpret it as a cooling-power rating or silently supply a missing unit. Specify pad conductivity, thickness, contact resistance and actual case/module temperatures from component data before approving a thermal design.
{% endhint %}

1. Active Cooling: It is recommended to use fans for active cooling.\
   Operating temperature ranges: - LDM module: < 70°C (The overall laser energy is reduced by 50% at 70 °C and the laser is completely shut down at 73 °C to prevent potential overheating of the laser device, while still maintaining adequate performance for most use cases.)

* IR module: < 68°C
* RGB module: < 68°C
* CPU: < 85°C

2. Passive cooling:

a. Apply graphite thermal pads on the side. It is recommended to use graphite thermal pads with specifications of 500W or higher.

![Official Orbbec figure from Reference Design - Thermal (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/9r2LuFUVSjpVnE9B4aRy/assets/d962845a7f540a61f13c.webp)

b. It is recommended to create ventilation holes on the casing to enhance cooling. The most effective directions for these holes are vertically (top and bottom). If holes cannot be placed on the top, consider placing them horizontally (left and right) and on the bottom for improved airflow.

#### 4. System Design Requirements <a href="#id-4.-system-design-requirements-1" id="id-4.-system-design-requirements-1"></a>

1. Sealing Requirements - Use foam padding or silicone seals between the 3D camera and the customer’s device to prevent dust.
2. Lens Requirements - No additional lenses or covers can be added to the front of the 3D camera.
3. Cooling Requirements - Connect the 3D camera to external metal components using thermal conductive materials to expand the cooling area. It is recommended to incorporate active cooling with fans.

* The 3D cameras must not be heated by other heat sources.

4. Before customer tooling, please provide structural drawings related to the 3D camera for orbbec’s ME review.

#### Reference Design - Power Delivery (Gemini 330 Series) <a href="#reference-design-power-delivery-gemini-330-series" id="reference-design-power-delivery-gemini-330-series"></a>

_Reviewed source:_ [_Reference Design - Power Delivery (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Power%20Delivery%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

**I. Power Capability and Bandwidth Requirements of USB Ports:**\
Both Gemini 335 and Gemini 335L require the USB ports on the customer’s motherboard to support a data bandwidth of USB 3.0 (5Gbps), and the power supply capability of the USB ports should support 5V/1.5A or higher.

**II. Solutions for Insufficient Power Supply Capability of USB Ports:**\
If the customer’s motherboard USB 3.0 port can only support up to 0.9A, there are two solutions available:

#### 1. Solution A <a href="#id-1.-solution-a" id="id-1.-solution-a"></a>

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

#### 2. Solution B <a href="#id-2.-solution-b" id="id-2.-solution-b"></a>

If reducing intensity of the laser power is undesirable, an additional switching board can be used, powered by an external adapter providing 5V/1.5A. The 5V/1.5A power supply is routed through the DC-IN interface to the USB Power Switch SY6874DBC chip’s power input on the adapter board. The VBUS signal from the motherboard’s USB port only controls the SY6874DBC’s EN enable pin, thereby managing the 5V power delivery to the USB A Female port. The power is then delivered to the Gemini 335 or Gemini 335L through a USB 3.0 cable, fulfilling the power requirements for the Gemini series, as illustrated in Figure 3.

![Official Orbbec figure from Reference Design - Power Delivery (Gemini 330 Series)](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/5ZqtHDvYgBA8fOlP31WW/assets/5e97a6a1c33f848250e5.webp)

Figure 3. Using an additional switching board to power Gemini series

#### Reference Design - Cable (USB) (Gemini 330 Series) <a href="#reference-design-cable-usb-gemini-330-series" id="reference-design-cable-usb-gemini-330-series"></a>

_Reviewed source:_ [_Reference Design - Cable (USB) (Gemini 330 Series)_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20-%20Cable%20\(USB\)%20\(Gemini%20330%20Series\))_. Manufacturer figures and source examples retain their original attribution and rights._

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

#### Reference Design for Ethernet Device <a href="#reference-design-for-ethernet-device" id="reference-design-for-ethernet-device"></a>

_Reviewed source:_ [_Reference Design for Ethernet Device_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Reference%20Design%20for%20Ethernet%20Device)_. Manufacturer figures and source examples retain their original attribution and rights._

| Interface | Product      | Reference Design                                                                     | Version | Release Date | Remark      |
| --------- | ------------ | ------------------------------------------------------------------------------------ | ------- | ------------ | ----------- |
| Ethernet  | Gemini 335Le | [Gemini 335Le ME Design Guideline \_V1.2.pdf](https://doc.orbbec.com/attachments/28) | V1.2    | 2026-04-19   | <p><br></p> |

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

Lastly, run Orbbec Viewer with the command "sudo ./OrbbecViewer".

**Q6: How to get the log of hardware level?**

Here are three ways to get the log.

1. Turn on the "heartbeat" switch in Orbbec Viewer;
2. By API,device->setBoolProperty(OB\_PROP\_HEARTBEAT\_BOOL, true);
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

**Gemini 335 buyers:** Use the dedicated [Orbbec Gemini 335 User Manual](https://wiki.openelab.io/orbbec/orbbec-gemini-335-user-manual) as the primary product manual. This series manual remains the shared development reference for Gemini 330 Series cameras.

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

[![image.png](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/qVODavWnrIiDkhMwVVwN/assets/176f77b12d9091d447e4.webp)](https://doc.orbbec.com/uploads/images/gallery/2025-07/image.png)

#### 4. OS Support <a href="#id-4.-os-support" id="id-4.-os-support"></a>

_**Windows OS**_ – Metadata extraction is supported by Microsoft starting with Windows 10. Check the Windows installation guide for details.

**Other OS –** We use libuvc/libusb as the default backend, which does not require any operation to enable metadata support.

#### 5. Devices Support <a href="#id-5.-devices-support" id="id-5.-devices-support"></a>

In this referenced API-generation document, the metadata APIs are scoped to the Orbbec Gemini 300 series. This is a version-specific scope statement, not a complete current SDK device list; query the exact camera/firmware capability before using a field.

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/3m40XdzNXilX6ALTDd7U/assets/3b16ff93e30566e74988.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/E6g6bB52jLsLVuhgpnVz/assets/b26649f198cc3c1b0454.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ECBHoYQNBg8Mmrx1GWu0/assets/18c3462f0a578d0f5a1b.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/v52QcB4F3pBDShAJlUjM/assets/2029a89610b62e812794.webp)

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/48jYj04UkKzhppeRZZaC/assets/b51a24d0676c780a93ac.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ACwtKmrtVQr0wEQSPuk7/assets/bdea94ef8ca83dfc9eeb.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/Bd7QiVr195vsNAQ7KqFd/assets/a6c0bbe34766161547fc.webp)
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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/p7oxMXCv0KWmTZvMJqKS/assets/a9eaff277030b41ebfa5.gif)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/rigsvBLHEjrsHyZ1WOL6/assets/c92e21183b672c29bfb3.gif)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/xK8VRauYa867nKuusQ1k/assets/14720cd2925836f5db1c.webp)

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

#### 3. Camera Configuration <a href="#id-3.-camera-configuration" id="id-3.-camera-configuration"></a>

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

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013913/image027.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/eZrYntQLMWFAcZeS8CUd/assets/4d8c4d209ca854355815.gif)

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/oNerZCBwDQ2IZPnXO2gM/assets/f21eaf12548ef575cbc3.gif)

Figure 3-1-2 Gemini 335 Synchronization Validation Secondary Configuration

3. Toggle the depth and color buttons for the Primary and Secondary. The depth stream for both devices does not display, but the color stream is functioning correctly, as shown in Figure 3-3:

① Toggle the depth and color buttons for the Primary.

② Toggle the depth and color buttons for the Secondary.

③ Neither the Primary nor the Secondary outputs depth stream; only the color stream is outputted.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013930/image031.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/nfG2bYUVhgHxDVSeFf6Z/assets/ed3260805dd85fcbb4a7.gif)

Figure 3-1-3 Gemini 335 Synchronization Validation Secondary Configuration

4. Synchronization verification process as shown in Figure 3-4:

① Click the "Trigger Once" button on the Primary. Both the Primary and Secondary should capture stream normally, indicating that camera synchronization is functioning (hardware connection OK). If synchronization is not working, the Secondary device will not capture the specified number of frames after triggering from the Primary.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013939/image033.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AWHydHQkxIoG4gRbKPMa/assets/0fbbdeae7c4955ecfcd6.gif)

Figure 3-1-4 Gemini 335 synchronization validation

* Confirmation of Astra 2 synchronization effectiveness is detailed in Appendix III.
* Confirmation of Femto Mega/Bolt synchronization effectiveness is detailed in Appendix IV.
* The synchronization verification method for Gemini 2 series is the same as for Gemini 330 series, with the only difference being that Gemini 2 series supports RGB triggering.

**3.2 Use the SDK to Run a Multi-camera Synchronization Example**

**3.2.1 Initial Configuration for Multi-Camera Synchronization**

SDK Acquisition: [Download Orbbec SDK](https://github.com/orbbec/OrbbecSDK/releases)

In the SDK program folder:\OrbbecSDK\_C\_C++\_v1.10.8\_20240604\_d1671a341\_win\_x64\_release\OrbbecSDK\_v1.10.8\Example\bin\
Find the configuration file "MultiDeviceSyncConfig.json", and configure it as shown in the following figure. After configuration, save the settings. (The following is a reference setting for the Gemini 330 series)

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04013948/image035.gif) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/0M7wDgKkqGe8zxlEs69w/assets/20067c4575e8b4186f64.gif)

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/kzybZei3H1VQjUaDhBZQ/assets/27ca78cf19ff185456b6.gif)

Figure 3-2-2 Example Operation Diagram of Gemini 335 multi-camera Synchronization

1. Successful streaming and preview of multi-camera effects are shown in Figure 3-2-2 below.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020144/image038.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/D8OHZpFxmW8fukBbCjct/assets/d276f32ed47da9aa396b.webp)

Figure 3-2-3 Preview of multi-camera synchronous open streaming of Gemini 335

7. Checking the effect of multi-camera synchronization

① According to the designated device numbers as follows: Device#0 (Primary) and Device#1 (Secondary), locate the timestamps (Sensor timestamp for Gemini 335; Frame timestamp for Gemini 335L) that are closest to each other. These timestamps represent the synchronized timestamps between the two devices. The figure below illustrates that the depth synchronization timestamp between the Primary and Secondary devices shows a difference of 0 to 1ms, and the color synchronization timestamp also shows a difference of 0 to 1ms.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020154/image040.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/AmU9XiZ0C5ZA9lpN1sB7/assets/66af48cf2c235e34cdbd.webp)

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
4. For Linux computers, such as Ubuntu, the default kernel allocates only 16 MB of memory for USB controllers to handle USB transfers. This amount may be insufficient for high-resolution images or multiple streams and devices. To support multiple devices, the USB controller must have more memory allocated. Follow these steps to increase the allocated memory: 1. Edit.
5. Locate the following line:

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

#### 6. Subsidiary Function <a href="#id-6.-subsidiary-function" id="id-6.-subsidiary-function"></a>

**6.1 Use Orbbec Viewer to View Device SN**

When connecting multiple devices, follow these steps to view the SN (serial number) and connection method of the selected camera:

1. Select the corresponding device from the options in the top left corner as shown in Step ① of the following figure.
2. Then, click according to Step ② in the figure to view the SN and connection method of the selected camera.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020201/image042.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/aMIS2svgiOVybPbEDqIU/assets/843aac581c89bdf72632.webp)

Figure 6-1 diagram of the device SN viewed by the Orbbec Viewer

**6.2 View Multi-camera Synchronization Configuration in Orbbec Viewer**

① After connecting the devices, open the Orbbec Viewer tool. If multiple devices are connected, you need to select the devices. If only one device is connected, no selection is required as the device will be recognized automatically.

② Click on "Device Control" and expand "Synchronization Configuration" to display relevant parameters such as mode, color delay, depth delay, trigger output switch, signal output delay, and other information.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020207/image044.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/ZV6oChG0NkefeyLGPgG1/assets/a42e92d68126e144de96.webp)

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/4pp96cUogeAf7JupVPsB/assets/08e3cd7f485663e9c3a4.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/QdKBCSCRrUdoi2dfMMUX/assets/6e287e6b893c2c6be101.webp)
* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/zIZGq4qFaYqXXBCRUZT8/assets/447d4d6bebed06f13033.webp)

**7.3 Appendix III: Astra 2 Synchronization Confirmation Method**

1. After connecting the camera as described in section 2.1, open Orbbec Viewer for the following configurations:
2. Configure the synchronization mode and parameters between the primary and the secondary according to Figure 3-1:

① Set the primary device sync mode to "Primary"

② Click ‘Write’

③ Select the secondary device, and set the sync mode to "Secondary-synced"

④ Set the secondary’s Trigger2Image delay \[1] is ≥4000

⑤ Click ‘Write’

Note: \[1] For star topology connection, set the secondary’s Trigger2Image delay between secondary 1 and the Prinary to be ≥4000 microseconds. If there are multiple secondary cameras, delays between secondary also need to be ≥4000 microseconds. For daisy-chain topology connection, set the secondary’s signal output delay to -1; this applies to all secondary.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020233/image052.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/CzOeUedM5ICA1JFgQn4B/assets/f8aa43db47d5f24b7af2.webp)

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/0qPWOhvbLFWPJ2HrrgUj/assets/767f6787071ea5192f80.webp)

Appendix Table 3-2: Astra 2 Synchronization Confirmation Diagram

⑤ Set the secondary depth frame rate to 30fps to confirm synchronization is effective with normal data output (refer to Figure 3-3).

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020247/image056.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/RR7P938EJkRTlX8UlKQY/assets/36d97e6cfccf9e85ea3b.webp)

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

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/IOm5MIvuVJLyDLW1Qli2/assets/1a843430253f54ae8170.webp)

Appendix Table 4-1: Femto Mega/Bolt Synchronization Confirmation Host/Slave Configuration Diagram

2. Verification Method for Synchronization:

① Toggle the depth and color buttons on the secondary device. Neither depth nor color data streams are output from the secondary device.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020301/image060.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/yXxag0nbaGmMReQH8LOo/assets/9d704fbbeba1ee39dde2.webp)

Appendix Table 4-2: Femto Mega/Bolt Synchronization Effectiveness Verification Diagram

② After enabling depth and color on the primary device, observe normal depth and color imaging on the secondary device to confirm synchronization is effective.

| Manufacturer reference content                                                                 |
| ---------------------------------------------------------------------------------------------- |
| ![](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/09/04020309/image062.png) |

_Retained figure/download references from the existing version of this table:_

* [Original manufacturer resource](https://content.gitbook.com/content/tgOfPnscWebs1eh82EKq/blobs/YMNZhrq2JP5OMn7WyOpX/assets/9d32abcdb6bb0951114b.webp)

Appendix Table 4-3: Femto Mega/Bolt Synchronization Effectiveness Verification Diagram

\[Note] Ineffective synchronization is indicated if the secondary camera does not produce images when the primary is enabled, or if the secondary produces images without the primary being enabled.

**7.5 Appendix V: Synchronous Configuration Details**

**7.5.1 Profile Description**

_Retained chapter example or transcript; source/API revision applies. Not executed or compiled for this guide._

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

The retained regulatory matrix links the following exact-model documents. A download is a document reference, not a new certification conclusion. The matrix labels KC for 335Lg as in certification; UKCA/IC/RCM are marked not applicable for 335Le/338Le, and some packaging/TPCH entries are unspecified in that revision.

| Type           | Certification         | Gemini 335 \&Gemini 336                                                                                                                                                                         | Gemini 335L \&Gemini 336L                                                                                                                                                                        | Gemini 335Lg                                                                                                                                                    | Gemini 335Le                                                                                                                                                    | Gemini 338Le                                                                                                                                                    | Gemini 338Lg                                                                                                                                                    |
| -------------- | --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Laser Safety   | Class 1               | <p><a href="https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf">CLASS 1_Orbbec Gemini 33xx</a><br></p>                                 | <p><a href="https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf">CLASS 1_Orbbec Gemini 33xx</a><br></p>                                  | <p><a href="https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf">CLASS 1_Orbbec Gemini 33xx</a><br></p> | <p><a href="https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf">CLASS 1_Orbbec Gemini 33xx</a><br></p> | <p><a href="https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf">CLASS 1_Orbbec Gemini 33xx</a><br></p> | <p><a href="https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084045/Class1_Orbbec_Gemini-33xxx.pdf">CLASS 1_Orbbec Gemini 33xx</a><br></p> |
| Laser Safety   | FD A Accession Number | <p>2420619-002<br></p>                                                                                                                                                                          | <p>2420619-002<br></p>                                                                                                                                                                           | <p>2420619-002<br></p>                                                                                                                                          | <p>2420619-002<br></p>                                                                                                                                          | <p>2420619-002<br></p>                                                                                                                                          | <p>2420619-002<br></p>                                                                                                                                          |
| <p>EMC<br></p> | CE                    | [CE\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26132900/SZ24040105C01_CE_VoC.pdf)                                                                 | [CE\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133940/SZ24040102C01_CE_VoC.pdf)                                                                 | [CE\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033449/SZ24080134C01_CE_VoC.pdf)                               | [CE\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084855/CE_Orbbec_Gemini-335Le.pdf)                             | [CE\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/29)                                                                                               | [CE Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/SZ26060269C01_CE_VoC.pdf)                                                     |
| <p>EMC<br></p> | FCC                   | [FCC\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26141705/FCC_Gemini-33x.pdf)                                                                      | [FCC\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26141702/FCC_Gemini-33xL.pdf)                                                                     | [FCC\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033447/SZ24080133_FCC-SDoC.pdf)                               | [FCC\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084853/FCC_Orbbec_Gemini-335Le.pdf)                           | [FCC\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/30)                                                                                              | [FCC Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/FCC%20Orbbec%20Gemini%20338Lg.pdf)                                           |
| <p>EMC<br></p> | KC                    | [KC\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/27054345/%EC%A0%81%ED%95%A9%EB%93%B1%EB%A1%9D%ED%95%84%EC%A6%9D_Orbbec-Inc._G40155-170_240522.pdf) | [KC\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/27054347/%EC%A0%81%ED%95%A9%EB%93%B1%EB%A1%9D%ED%95%84%EC%A6%9D_Orbbec-Inc._G40055-170_240522.pdf) | In certification                                                                                                                                                | [KC\_Orbbec\_Gemini 335Le](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/KC_Orbbec_Gemini%C2%A0335Le.pdf)                                            | [KC\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/31)                                                                                               | [KC Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/KC%20Orbbec%20Gemini%20338Lg.pdf)                                             |
| <p>EMC<br></p> | UKCA                  | [UKCA\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133050/SZ24040105C02_UKCA_VOC.pdf)                                                             | [UKCA\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133937/SZ24040102C02_UKCA_VOC.pdf)                                                             | [UKCA\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033502/SZ24080254C01_UKCA_VOC.pdf)                           | N/A                                                                                                                                                             | N/A                                                                                                                                                             | N/A                                                                                                                                                             |
| <p>EMC<br></p> | IC                    | [IC\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133200/SZ24040106C01_IC_VOC.pdf)                                                                 | [IC\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133932/SZ24040103C01_IC_VOC.pdf)                                                                 | [IC\_Orbbec Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/04121846/IC_Orbbec-Gemini-335Lg.pdf)                              | N/A                                                                                                                                                             | N/A                                                                                                                                                             | [IC Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/IC%20Orbbec%20Gemini%20338Lg.pdf)                                             |
| <p>EMC<br></p> | RCM                   | [RCM Report\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084039/RCM_Orbbec-Gemini-33x.pdf)                                                                | [RCM Report\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084034/RCM_Orbbec-Gemini-33xL.pdf)                                                               | N/A                                                                                                                                                             | N/A                                                                                                                                                             | N/A                                                                                                                                                             | N/A                                                                                                                                                             |
| Environment    | REACH                 | [REACH\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133633/SZ24040099R02_Orbbec_Gemini-335_REACH.pdf)                                             | [REACH\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26134328/SZ24040100R02_Orbbec_Gemini-335L_REACH.pdf)                                            | [REACH\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033456/SZ24080135R02_Orbbec_G40055_REACH-241.pdf)           | [REACH\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084850/REACH_Orbbec_Gemini-335Le.pdf)                       | [REACH\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/32)                                                                                            | [REACH Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/REACH%20Orbbec%20Gemini%20338Lg.pdf)                                       |
| Environment    | RoHS                  | [ROHS\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133342/SZ24040099R01_Orbbec_Gemini-335_ROHS.pdf)                                               | [ROHS\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26134324/SZ24040100R01_Orbbec_Gemini-335L_ROHS.pdf)                                              | [ROHS\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033453/SZ24080135R01_Orbbec_G40055_ROHS.pdf)                 | [ROHS\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084847/ROHS_Orbbec_Gemini-335Le.pdf)                         | [ROHS\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/33)                                                                                             | [ROHS Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/ROHS%20Orbbec%20Gemini%20338Lg.pdf)                                         |
| Environment    | WEEE                  | [WEEE\_Orbbec\_Gemini 33x](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26133600/SZ24040099R03_Orbbec_Gemini-335_WEEE.pdf)                                               | [WEEE\_Orbbec\_Gemini 33xL](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/26134320/SZ24040100R03_Orbbec_Gemini-335L_WEEE.pdf)                                              | [WEEE\_Orbbec\_Gemini 335Lg](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/21033500/SZ24080135R03_Orbbec_G40055_WEEE.pdf)                 | [WEEE\_Orbbec\_Gemini 335Le](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/22084843/WEEE_Orbbec_Gemini-335Le.pdf)                         | [WEEE\_Orbbec\_Gemini 338Le](https://doc.orbbec.com/attachments/34)                                                                                             | [WEEE Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/WEEE%20Orbbec%20Gemini%20338Lg.pdf)                                         |
| Environment    | 94/62/EC              | [Package directive\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032021/Package-directive_Orbbec-Gemini-33xx.pdf)                                  | [Package directive\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032021/Package-directive_Orbbec-Gemini-33xx.pdf)                                   | [Package directive\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032021/Package-directive_Orbbec-Gemini-33xx.pdf)  | [Package directive\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032021/Package-directive_Orbbec-Gemini-33xx.pdf)  | Not specified in this source revision                                                                                                                           | Not specified in this source revision                                                                                                                           |
| Environment    | TSCA                  | [TSCA\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032019/TSCA_Orbbec-Gemini-33xx.pdf)                                                            | [TSCA\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032019/TSCA_Orbbec-Gemini-33xx.pdf)                                                             | [TSCA\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032019/TSCA_Orbbec-Gemini-33xx.pdf)                            | [TSCA\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032019/TSCA_Orbbec-Gemini-33xx.pdf)                            | [TSCA\_Orbbec Gemini 338Le](https://doc.orbbec.com/attachments/35)                                                                                              | [TSCA Orbbec Gemini 338Lg](https://orbbec-debian-repos-aws.s3.amazonaws.com/product/TSCA%20Orbbec%20Gemini%20338Lg.pdf)                                         |
| Environment    | TPCH                  | [TPCH\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032017/TPCH_Orbbec-Gemini-33xx.pdf)                                                            | [TPCH\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032017/TPCH_Orbbec-Gemini-33xx.pdf)                                                             | [TPCH\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032017/TPCH_Orbbec-Gemini-33xx.pdf)                            | [TPCH\_Orbbec Gemini 33xx](https://new-orbbec3d-s3.s3.amazonaws.com/wp-content/uploads/2024/04/15032017/TPCH_Orbbec-Gemini-33xx.pdf)                            | Not specified in this source revision                                                                                                                           | Not specified in this source revision                                                                                                                           |

The source lists Class 1 laser classification and FDA accession 2420619-002 for the family reference. Select the exact camera and market-specific declaration; do not treat a certificate for another family column as this model’s approval.

#### Download Tools <a href="#download-tools" id="download-tools"></a>

_Reviewed source:_ [_Download Tools_](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20Tools)_. Manufacturer figures and source examples retain their original attribution and rights._

| Version                               | Link                                                                                         |
| ------------------------------------- | -------------------------------------------------------------------------------------------- |
| Orbbec SDK and Viewer (Closed-source) | [https://github.com/orbbec/OrbbecSDK/releases](https://github.com/orbbec/OrbbecSDK/releases) |
| Orbbec SDK and Viewer (Open-source)   | [Releases · orbbec/OrbbecSDK\_v2](https://github.com/orbbec/OrbbecSDK_v2/releases)           |

#### Development Resources <a href="#development-resources" id="development-resources"></a>

* [Official Gemini 330 Series documentation](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation)
* [CAD files](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Download%20CAD%20Files%20\(Gemini%20330%20Series\))
* [Firmware releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Firmware%20Release%20\(Gemini%20330%20Series\))
* [Depth preset releases](https://doc.orbbec.com/documentation/Orbbec%20Gemini%20330%20Series%20Documentation/Depth%20Preset%20Release%20\(Gemini%20330%20Series\))
* [Orbbec SDK v2](https://github.com/orbbec/OrbbecSDK_v2)
* [Orbbec SDK v2 documentation](https://orbbec.github.io/OrbbecSDK_v2/)
* [Orbbec SDK ROS 2 wrapper](https://github.com/orbbec/OrbbecSDK_ROS2)
* [Orbbec SDK ROS 1 wrapper](https://github.com/orbbec/OrbbecSDK_ROS1)
* [Orbbec SDK Python wrapper](https://github.com/orbbec/pyorbbecsdk)
