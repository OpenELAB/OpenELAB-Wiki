# RealSense D435 D435i D455f and D405 Engineering Guide

### Product family and model boundaries

This guide covers **D435, D435i, D455f and D405 USB depth cameras**. They share a software ecosystem, but differ in optics, useful distance, motion sensing and filtering. Select the camera according to the working distance and scene, not merely the shared D400 name.

| Model | Distinguishing scope                                             |
| ----- | ---------------------------------------------------------------- |
| D435  | Wide-field stereo-depth camera; no integrated IMU                |
| D435i | D435-family depth with integrated IMU                            |
| D455f | Longer-baseline D455-family camera with IR-pass filter and IMU   |
| D405  | Close-range stereo camera for near-field inspection/manipulation |

The manufacturer datasheet documents depth/RGB stream modes, FOV, operating limits and model-specific geometry. D435-family depth supports up to **1280 × 720** and up to **90 FPS**, but available combinations vary by mode. Treat those maxima separately; do not assume every resolution supports every frame rate.

### Technical documents and development software

Use the current **D400 datasheet** and mechanical drawings for your exact camera when designing brackets or assessing minimum distance. D435i's IMU and D455f's filter are not features of the plain D435. An IR-pass filter can help in some illumination conditions; it does not eliminate all depth failures on reflective or transparent surfaces.

The official **librealsense SDK** provides RealSense Viewer, C/C++ APIs, examples and Python bindings. Select a release whose compatibility table covers the camera, firmware and host OS. Keep those versions together rather than updating firmware independently of the application.

### Getting started: depth first, application second

1. Install the SDK for the host OS using its supported installation path.
2. Connect one camera directly to a suitable USB 3 host port with a known-good data cable. Avoid an unpowered hub for the first test.
3. Open **RealSense Viewer**, verify model/serial/firmware, and enable a supported depth stream.
4. Place a textured, matte target inside the selected model's documented working range. Confirm a stable depth image.
5. Enable RGB if applicable; on D435i/D455f separately verify motion streams. Save a short recording and its stream configuration.

**Checkpoint:** repeatable streaming with an identified USB mode and the expected streams. Viewer success does not yet establish calibrated hand-eye transforms, time synchronization or robot perception accuracy.

### Application integration

Start from an SDK example matching the programming language. Query device capabilities rather than hard-coding another model's streams. For robotics, define the optical coordinate frame, depth units, camera intrinsics and any color/depth alignment deliberately. Preserve original calibration metadata with recordings.

### FAQs

**Camera appears only as USB 2?** Check cable, port and hubs; reduce the stream configuration while diagnosing bandwidth.

**Depth is missing near an object?** Compare distance against the exact model's minimum range; D405 serves a different near-field role from D455f.

**IMU not found on D435?** Use a model that actually contains an IMU.

**Depth/color are shifted?** Apply the SDK's calibrated alignment correctly; raw streams come from different viewpoints.

**Recovery?** Follow the SDK's supported firmware update/recovery flow and compatibility table. Save application configuration and recordings before changes.

### Sources and validation

* [Manufacturer model comparison](https://www.realsenseai.com/compare-depth-cameras/)
* [D400-family datasheet, March 2026](https://www.realsenseai.com/wp-content/uploads/2026/03/RealSense-D400-Series-Datasheet-Mar-2026.pdf)
* [Official SDK and examples](https://github.com/realsenseai/librealsense)
* [SDK releases and firmware compatibility](https://github.com/realsenseai/librealsense/releases)
* [Manufacturer datasheet and drawing downloads](https://www.realsenseai.com/product-datasheets/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
