---
description: >-
  Wire the SV1-25 5 V USB interface, distinguish fisheye and rectified frames,
  use actual V1/V2 capture APIs and diagnose archive-versus-portal mismatches.
---

# Unitree SV1-25: USB stereo capture, calibration and exact SDK interfaces

{% hint style="info" %}
[**OpenELAB product — Unitree SV1-25 Mini RGB Global Shutter USB Binocular Camera**](https://openelab.io/products/unitree-sv1-25-mini-rgb-global-shutter-usb-binocular-camera) — SKU **`Unitree-SV1-25`**, observed Default Title variant **`44687632629958`**. This guide covers the exact SV1-25 camera, not every robot-mounted Unitree camera or a Go1 camera package.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

SV1-25 is a USB2.0 color global-shutter stereo camera with a 25 mm lens-center baseline and very wide fisheye optics. The manufacturer supplies two development packages: a C++/OpenCV-based stack with rectification and stereo-processing interfaces, and a lighter Linux-oriented interface for capture or independent development. The camera does not by itself establish a calibrated depth accuracy, a robot network address, or a ready-to-use ROS depth pipeline. [Official SV1-25 product](https://www.unitree.com/sv1-25/), [model-specific developer overview](https://support.unitree.com/home/en/SV1-25_develop/about_SV1-25).

The sensor specification is **1280 × 800 pixels**, while supported transported binocular frames are **1856 × 800** and **928 × 400**. These are different quantities. Do not expect two transported 1280 × 800 images merely by doubling the chip specification. Similarly, the advertised **220° optical field** is not the field of a rectified perspective output, whose example configuration requests 90°.

![Unitree SV1-25 original mechanical drawing](https://doc-cdn.unitree.com/static/2024/7/24/361235eda18143ffa28246594564a941_2578x1726.png)

_Original Unitree drawing from the model-specific developer overview; dimensions in mm. Viewed directly to check the mounting-hole and body annotations._

## Applications <a href="#applications" id="applications"></a>

Use SV1-25 for wide-view stereo capture, visual perception research and rectification/stereo algorithm evaluation where a short baseline and low-power USB interface fit the platform. Global shutter avoids rolling-shutter line skew but does not eliminate exposure blur, insufficient texture, calibration error or asynchronous integration with other sensors. The 25 mm baseline makes depth uncertainty strongly dependent on focal model, disparity, distance and calibration; no verified depth-error curve or maximum useful depth was supplied by the examined sources.

Start with raw binocular capture, confirm which half is which, and then load the camera's own intrinsics/extrinsics before rectification. Evaluate perspective output field and valid pixels separately from the fisheye marketing angle. A generic Unitree camera repository for Go1 is not evidence that the same calibration, firmware, robot IP or mount transform applies to this exact camera.

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                    | Exact model source                                                                                                   |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| Image sensor                 | 1280 H × 800 V, approximately 1 MP; 1/4-inch optical format (4.5 mm)                                                 |
| Shutter / lens               | Color global shutter; fixed focus                                                                                    |
| Advertised field             | V/H/D each 220° at respective Y = 1.35/1.80/2.29 mm; fisheye source definition                                       |
| Baseline                     | 25 mm between lens center lines                                                                                      |
| Interface                    | USB2.0                                                                                                               |
| Video modes                  | 1856 × 800 at 30 fps; 928 × 400 at 30 or 60 fps                                                                      |
| Advertised formats           | MJPEG / “YUV2” in product table; downloadable V2 header explicitly marks `PIX_FMT_YUYV` unsupported                  |
| Power                        | 5 V / 200 mA manufacturer requirement, approximately 1 W arithmetic nominal                                          |
| Filter                       | T = 50% at 650 ±10 nm, not a camera frame-frequency specification                                                    |
| Operating temperature        | −10 to +60 °C                                                                                                        |
| Kit in manufacturer overview | One camera; one 1 m USB-A to GH1.25 four-pin cable; confirm retail packing separately                                |
| Drawing                      | 51 mm width, 25.5 mm body dimension; approximately 16.7 mm overall depth; hole spacing 46 × 17 mm with Ø2.5 callouts |

[Official technical specifications / mechanical figure](https://support.unitree.com/home/en/SV1-25_develop/about_SV1-25). A Ø2.5 hole is not proof of an M2.5 threaded insert or a tightening torque. No IP rating, storage range, shock/vibration qualification, absolute USB power transient, or hardware trigger/synchronization input is established by these sources.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### USB pin functions and mechanical scope <a href="#usb-pin-functions-and-mechanical-scope" id="usb-pin-functions-and-mechanical-scope"></a>

The official interface figure labels the four contacts, in its displayed top-to-bottom order, **5V, D+, D−, GND**. It does not supply numbered mating-face pins; preserve the original view when making a harness specification. Use the supplied USB-A/GH1.25 cable and verify the actual connector orientation. The overview's “GH1.24” prose conflicts with its GH1.25 bill of materials; do not derive a substitute connector from that typo. [Original interface and connection chapter](https://support.unitree.com/home/en/SV1-25_develop/about_SV1-25).

![Unitree SV1-25 original USB connector diagram](https://doc-cdn.unitree.com/static/2024/7/24/c62372ca97dc445c9e2579204c9fb57a_1702x826.png)

**This four-pin connection is 5 V USB data. L1's four-pin connection is 12 V/3.3 V UART; L2's serial branch is data-only UART. Similar pitch does not establish compatibility.** Preserve USB differential-pair integrity and the matched cable. Power off before changing wiring. Secure the body without obscuring either fisheye lens or loading the cable connector; protect the exposed optics and board appropriate to the installation because no waterproof assembly rating was established.

### Images, timestamps and calibration <a href="#images-timestamps-and-calibration" id="images-timestamps-and-calibration"></a>

The V1 raw example takes the **first half as right** and the **second half as left**, then displays a reordered left-right image. This is an example's transport interpretation, not permission to label halves without a known asymmetric scene and a matching camera revision. `getStereoFrame(left,right,timestamp)` avoids manual half swapping when its implementation is applicable. Cropping or rescaling requires matching calibration. [Actual V1 archive](https://oss-global-cdn.unitree.com/static/146bebcfbf334d0691cfeaf51c90d66c.zip), `examples/example_getRawFrame.cc` and `include/StereoCameraCommon.hpp`.

V1 uses `std::chrono::microseconds` for frame timestamps; its `TimeFrame` comment describes time since the Unix epoch. This source convention does not prove exposure-midpoint hardware timestamps or external clock synchronization. Record timestamp origin and acquisition/processing latency before fusion. The V2 frame API provides pointer/index/bytes-used outputs; no timestamp argument is present. A buffer index is not a clock. Neither source establishes a complete SV1-25 camera-to-robot transform or an authoritative optical-frame axis convention; use the delivered calibration/assembly definition rather than a robot camera mount from another model.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Two actual packages and prerequisite boundary <a href="#two-actual-packages-and-prerequisite-boundary" id="two-actual-packages-and-prerequisite-boundary"></a>

Both packages are linked by the [SV1-25 quick-start article](https://support.unitree.com/home/en/SV1-25_develop/quick_start), not inferred from a similarly named repository:

| Package              | Resource / source identity                                                                                                                | Scope                                                                                                                   |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| V1 C++ stack         | [Official archive `146bebcfbf334d0691cfeaf51c90d66c.zip`](https://oss-global-cdn.unitree.com/static/146bebcfbf334d0691cfeaf51c90d66c.zip) | `UnitreeCameraSDK.hpp`, `StereoCameraCommon.hpp`, CMake and raw/rectified/depth/calibration examples                    |
| V2 lightweight stack | [Official archive `bcc76a427afe421bb6f48918cdbff349.zip`](https://oss-global-cdn.unitree.com/static/bcc76a427afe421bb6f48918cdbff349.zip) | `user/include/unitree_mkp.h`, `camera_api.h`, `user/src/example_getRawFrame.cc`; actual downloadable interface controls |

V1's README/CMake identifies OpenCV 4 or later and OpenGL/GLUT/X11 for relevant viewer/point-cloud examples, C++11, pthread and architecture-specific prebuilt libraries. V2 removes those large image-processing dependencies, but still links vendor camera/systemlog/V4L2 extension libraries and `udev`; it is not an entirely dependency-free source build. Its public header includes C++ facilities despite C linkage for several functions. Do not promise that a plain C compiler or an arbitrary OS/CPU can use it. Confirm the archive's supplied architecture, host ABI, Linux device/udev access and licensing before selecting a target. The V1 archive contains an MPL-2.0 license and per-file notices; that does not establish blanket permission for every binary or a different package.

### V1 API and processing lifecycle <a href="#v1-api-and-processing-lifecycle" id="v1-api-and-processing-lifecycle"></a>

| Functional group                  | Actual names / behavior                                                                                                                                                                        |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Construction / status             | `StereoCamera()` or device-node/config constructors, derived `UnitreeCamera`; `isOpened()` must be checked                                                                                     |
| Logging / identity                | `setLogLevel`, `getLogLevel`, `getDeviceNode`, position/serial getters and setters; robot-position example numbers are metadata, not proof of physical mounting                                |
| Format                            | `setRawFrameSize`, `getRawFrameSize`, `setRawFrameRate`, `getRawFrameRate`; two supported raw sizes; 30 or 60 fps as mode permits                                                              |
| Capture                           | `startCapture(bool udpFlag=false, bool shmFlag=false)`, `stopCapture`; plain capture does not require enabling network forwarding/shared memory                                                |
| Raw / stereo                      | `getRawFrame(cv::Mat&, microseconds&)`; `getStereoFrame(left,right,time)` returns false when unavailable; preserve ownership/copy requirements before reusing buffers                          |
| Rectification                     | `setRectFrameSize`; `getRectStereoFrame` overloads with perspective left/right and optional longitude-latitude/perspective output and timestamp; actual name differs from one portal prototype |
| Calibration                       | `getCalibParams`, `setCalibParams`, `loadCalibParams`, `saveCalibParams`; parameter array is intrinsic, distortion, xi, rotation, translation, kfe; left/right flag must match lens            |
| Configuration                     | `loadConfig` before capture; `saveConfig` writes a host file; retain the active config next to recorded data                                                                                   |
| Stereo computation                | `startStereoCompute` after capture; `getDepthFrame` / `getPointCloud`; stop computation before capture shutdown                                                                                |
| Output forms                      | `cv::Vec3f` XYZ or `PCLType` XYZ plus BGR byte color; a colorized depth display is not automatically a metric depth map                                                                        |
| Firmware / persistent calibration | `checkFirmwareVersion`, `updateFirmware`, `updateCalibParams2Flash`; exact image/revision/recovery must be established before any update; exclude these from first capture                     |

The sample `stereo_camera_config.yaml` uses combined `FrameSize:[928,400]`, rectified size `[464,400]`, `hFov:90`, `FrameRate:30`, `Transmode:-1`, and `Depthmode:1`. Transmission modes 0/1/2/3 select raw-right/raw-stereo/rectified-right/rectified-stereo. Its old `IpLastSegment:15` and robot-subnet examples are application settings, **not a USB camera's factory IP**. The actual header evolves that configuration toward a full IP address; match the archive's implementation instead of inventing a network dependency for capture. An OpenGL example is a different prerequisite set from a headless raw-buffer application.

### V2 API and exact mismatch corrections <a href="#v2-api-and-exact-mismatch-corrections" id="v2-api-and-exact-mismatch-corrections"></a>

Independent development uses `UnitreeOpenCamKey()` then an application-owned capture path, finishing with `UnitreeCloseCamKey()`. The portal explicitly separates this from rapid-development mode. These are vendor camera-mode controls, not website authentication. Rapid mode uses the following lifecycle; all documented calls use 0 for success, other values for failure:

| Phase               | Actual header contract                                                                                                             |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Environment         | `UnitreeInitSdkEnv()` / `UnitreeDeInitSdkEnv()`                                                                                    |
| Camera              | `UnitreeInitCamera(int CamId)` / `UnitreeDeInitCamera(int CamId)`; actual `/dev/videoX` mapping required                           |
| Capabilities        | `PrintCamCapabilities(int CamId)`; inspect before assuming format support                                                          |
| Parameters          | `UnitreeSetCamParam(int, ut_cam_param*)` / `UnitreeGetCamParam(int, ut_cam_param*)`; fields **`high`**, **`width`**, **`pix`**     |
| Buffers             | `UnitreeGetCamerbuffer(int,unsigned)` recommends 4; `UnitreeReleaseCamerBuffer(int)` pairs with it; spelling/case are significant  |
| Stream              | `UnitreeStreamStart(int)` / `UnitreeStreamStop(int)`                                                                               |
| One frame           | `UnitreeGetOneFrame(int,void**,unsigned*,unsigned*)`; pointer, buffer index, and bytes used are outputs                            |
| Release             | **`UnitreeReleaseOneFrame(int,unsigned)`**; exactly two arguments in the archive, not the portal table's three                     |
| Convenience capture | **`UnitreeGetAndReleaseframe(int)`** in the actual header; the portal sample's `UnitreeGetReleaseframe` is a mismatched identifier |

Use `ut_cam_param`, not the portal table's `ut_cam_ctx` spelling. `PIX_FMT_MJPEG` is the supported first path; the header comments **`PIX_FMT_YUYV` unsupported**, despite the product table advertising “YUV2.” Do not quietly resolve this by assuming untested firmware supports it.

The V2 vendor example declares an uninitialized `void **Framebuf` and passes it to `UnitreeGetOneFrame`; correct application code needs storage such as `void *frame=nullptr` and passes **`&frame`**. Check every return code before dereferencing. Pair every successful frame acquisition with release, stop streaming, then free buffers, camera and environment. Do not copy its unchecked file writes, omitted stream-stop or interactive pauses into an unattended service. A blocking library acquisition has no verified timeout argument; a host loop deadline cannot guarantee return from it.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Conditional first image <a href="#conditional-first-image" id="conditional-first-image"></a>

1. Confirm SV1-25 identity, actual cable orientation and 5 V USB path. Secure both optics unobstructed. Connect to a supported host USB port; inspect the actual video-node identity and permissions. Another webcam can make `/dev/video0` the wrong device.
2. Select **one** actual package and confirm its supplied libraries match the host. For the least processing, V2 MJPEG avoids the V1 OpenGL/rectification dependency set. Independent mode and rapid mode are separate choices; do not call both lifecycles together.
3. Read capabilities, request **928 × 400 MJPEG** and read back the accepted parameters. A successful request does not prove that the negotiated width/height are what was requested. Use 1856 × 800/30 fps only after the supported mode is confirmed.
4. Obtain a single binocular frame, record the accepted mode and byte length, release the frame and stop/close through the corresponding lifecycle. Check a known asymmetric scene to label halves before rectification. Keep initial capture independent of firmware update, flash calibration, network forwarding or stereo depth computation.

**Expected result:** a decodable MJPEG binocular image from the identified SV1-25 at an actually accepted mode. No depth accuracy or hardware-synchronized timestamp is established by that result. See the [model-specific SDK article and archives](https://support.unitree.com/home/en/SV1-25_develop/quick_start). No acquisition was performed for this guide.

### Original rapid-mode one-frame reference <a href="#original-rapid-mode-one-frame-reference" id="original-rapid-mode-one-frame-reference"></a>

This original C++ reference matches the downloaded V2 header. It is **source-reviewed, not compiled or hardware-tested**. Build/link through that archive's actual CMake environment after the compatibility checks above. The opaque `UnitreeGetOneFrame` can block; this is one attempted acquisition, not a guaranteed timed shutdown. Supply the identified video-node number as its only argument. It prints metadata without writing images:

```cpp
#include "unitree_mkp.h"
#include <cstdio>
#include <cstdlib>

int main(int argc, char** argv) {
  if (argc != 2) return 2;
  char* end = nullptr;
  long n = std::strtol(argv[1], &end, 10);
  if (!end || end == argv[1] || *end || n < 0 || n > 255) return 2;
  const int id = static_cast<int>(n);
  bool env=false, cam=false, buffers=false, stream=false, held=false;
  unsigned index=0, used=0;
  void* frame=nullptr;
  int result=1;
  ut_cam_param requested{};
  ut_cam_param actual{};
  requested.width=928; requested.high=400; requested.pix=PIX_FMT_MJPEG;
  do {
    if (UnitreeInitSdkEnv()!=0) break;
    env=true;
    if (UnitreeInitCamera(id)!=0) break;
    cam=true;
    if (PrintCamCapabilities(id)!=0) break;
    if (UnitreeSetCamParam(id,&requested)!=0) break;
    if (UnitreeGetCamParam(id,&actual)!=0) break;
    if (actual.width!=928 || actual.high!=400 || actual.pix!=PIX_FMT_MJPEG) break;
    if (UnitreeGetCamerbuffer(id,4)!=0) break;
    buffers=true;
    if (UnitreeStreamStart(id)!=0) break;
    stream=true;
    if (UnitreeGetOneFrame(id,&frame,&index,&used)!=0) break;
    held=true;
    if (!frame || !used) break;
    std::printf("node %d accepted %ux%u frame-buffer %u bytes %u\n",
                id,actual.width,actual.high,index,used);
    result=0;
  } while (false);
  if (held && UnitreeReleaseOneFrame(id,index)!=0) result=1;
  if (stream && UnitreeStreamStop(id)!=0) result=1;
  if (buffers && UnitreeReleaseCamerBuffer(id)!=0) result=1;
  if (cam && UnitreeDeInitCamera(id)!=0) result=1;
  if (env && UnitreeDeInitSdkEnv()!=0) result=1;
  return result;
}
```

The API's zero return is the only frame-acquisition success condition used here. On a partial initialization failure, the public header does not define every internal resource state; obtain vendor guidance if a failed initialization leaves the device busy. A metadata print is not JPEG decode validation. Only a deliberate subsequent decoder/image check proves image usability.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Symptom                               | Model-specific diagnosis                                                                                                                                                |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wrong or missing video node           | Inspect the actual USB/video-device association, 5 V path, supplied cable, kernel/udev permissions and other active users; do not choose a node solely by numeric order |
| Library fails to load/link            | Match architecture/ABI and vendor library set; V1 raw capture and OpenGL/depth examples have different dependencies                                                     |
| Portal example will not compile       | Check `ut_cam_param`, `UnitreeGetAndReleaseframe`, two-argument `UnitreeReleaseOneFrame`, `high` field and C++ compilation against the actual archive                   |
| Crash obtaining frame                 | Use a valid output-pointer address (`void* p` then `&p`), check return, nonnull pointer and byte count; do not pass an uninitialized `void**`                           |
| YUYV fails                            | V2 header marks it unsupported; use MJPEG and inspect actual capabilities instead of relying on the product's YUV2 claim                                                |
| Requested mode differs                | Read back accepted parameters; only 1856 × 800 and 928 × 400 are documented combined sizes                                                                              |
| Left/right reversed or depth unusable | Confirm transport-half order on an asymmetric scene and exact per-lens calibration; raw capture success is not stereo correctness                                       |
| Rectification cuts off scene          | Perspective rectification/FOV differs from 220° fisheye optics; match rectified size, intrinsics and valid region                                                       |
| Apparent timing misalignment          | V1 microseconds are not proof of hardware exposure time; V2 buffer index lacks timestamp; external synchronization unverified                                           |
| Device remains busy after exit        | Release acquired frames, stop stream, free buffers and deinitialize in reverse lifecycle; investigate failed/blocked calls rather than removing devices blindly         |

**Firmware / calibration recovery:** the V1 class exposes update and flash-calibration methods, but exact SV1-25 firmware binaries, compatibility matrix, update safety/recovery steps and rollback were not established. Preserve original calibration files and hardware identity; a generic camera SDK's firmware method is not a complete approved update procedure. No public ROS topic/frame/rate contract or robot-specific hand-eye transform was verified for this package.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                             | Use / verification scope                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| [Official product page](https://www.unitree.com/sv1-25/)                                                                             | Model identity and advertised sensor/mode specifications                                        |
| [Developer overview](https://support.unitree.com/home/en/SV1-25_develop/about_SV1-25)                                                | BOM, mechanical drawing, FOV figure, interface figure and USB connection                        |
| [Developer quick start](https://support.unitree.com/home/en/SV1-25_develop/quick_start)                                              | V1/V2 functional groups, flow diagrams and archive links; mismatches documented above           |
| [V1 archive](https://oss-global-cdn.unitree.com/static/146bebcfbf334d0691cfeaf51c90d66c.zip)                                         | Actual C++ headers/config/CMake/raw, rectification and calibration examples inspected           |
| [V2 archive](https://oss-global-cdn.unitree.com/static/bcc76a427afe421bb6f48918cdbff349.zip)                                         | Actual headers/CMake/raw example inspected; use exact declared prototypes                       |
| [Original software architecture figure](https://doc-cdn.unitree.com/static/2024/7/24/2815acf6534545d58d65d195c36691c8_1634x1204.png) | Manufacturer component relationship, not a guarantee that all processing runs inside the camera |
| [Original V2 lifecycle figure](https://doc-cdn.unitree.com/static/2024/7/24/ff6d948ca32545c4bda66c20b8d27a89_714x2843.png)           | High-level sequence; use corrected actual signatures and explicit cleanup above                 |

A separate downloadable exact-model operating PDF, complete electrical schematic, calibrated depth-accuracy report, CAD solid and verified firmware recovery package were not found in the inspected resources. The original mechanical/interface drawings provide useful dimensional/pin-function evidence without establishing those missing deliverables.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026: exact observed catalog SKU/variant, actual manufacturer page, **both complete SV1-25 developer articles** and both actual downloadable SDK archives' relevant headers, build descriptions/configuration and examples. Original connector/mount figures were visually checked. Portal text was read from actual accessible official article assets; no claim is made that unrelated portal chapters were read. Source identities, archive/file hashes and the article-section crosswalk accompany this draft privately; raw bundles and transcripts are not part of the public guide.

**No vendor library was imported, installed, compiled or executed. No USB capture, ROS, firmware, calibration write, hardware or robot test occurred.** The original example has exact-header source review only; runtime readiness remains conditional on matched hardware, host libraries and mode negotiation. Remaining gaps are measured depth performance, exposure-clock synchronization, actual delivered calibration/firmware/ABI compatibility, and a verified recovery method. Separate product JSON requests returned 429; retail identity is from the observed complete catalog, not a stock guarantee.

### Complete official article coverage <a href="#complete-official-article-coverage" id="complete-official-article-coverage"></a>

Each row records substantive functional coverage, not a claim that a link alone was reviewed. Full source heading/line ranges and hashes are retained with the draft. Empty category nodes are explicitly distinguished from technical content.

| Actual official article                                                         | Source sections read                                                                                                                                            | Original engineering coverage / boundary                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [about SV1-25](https://support.unitree.com/home/en/SV1-25_develop/about_SV1-25) | Product profile; Bill Of Material; technical specifications; Field of view angle signal:; Hardware interface description; Connection debugging                  | Separate chip resolution from combined transported sizes, fisheye220° optics from rectified FOV, and 25 mm baseline from an unprovided depth-accuracy guarantee. BOM is camera plus1 m USB/GH1.25 cable. Original drawing gives body/hole dimensions, not screw torque. Interface figure labels5V,D+,D−,GND in its own view; GH1.24 prose is not a substitute connector specification.                                                                                                          |
| [quick start](https://support.unitree.com/home/en/SV1-25_develop/quick_start)   | SDK introduction; Version 1; Software service interface; Version 2; Independent development mode; Rapid development mode; Use of the examples; Call the process | V1 provides capture/rectification/stereo interfaces with external image/GUI dependencies; V2 provides mutually exclusive independent mode or rapid capture lifecycle. Use actual header signatures, supported MJPEG, accepted-mode readback, valid output-pointer storage, paired frame releases and reverse cleanup. Portal ut\_cam\_ctx, GetReleaseframe and three-argument ReleaseOneFrame disagree with actual archive. Neither stack proves hardware exposure timing or firmware recovery. |

**Related documentation:** [Unitree model and development directory](./).
