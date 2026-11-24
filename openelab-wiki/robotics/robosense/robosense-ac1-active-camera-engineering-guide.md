---
description: >-
  Connect AC1 USB3 LiDAR/RGB/IMU streams, preserve factory calibration, resolve
  published specification differences and build the exact AC1 ROS2 Humble
  driver.
---

# RoboSense AC1 Active Camera Engineering Guide

{% hint style="info" %}
[**View RoboSense AC1 Active Camera LiDAR Depth Camera for Robotics on OpenELAB**](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale?variant=44647049920710)

**Model / option:** Default Title · **SKU:** `RS-AC1`
{% endhint %}

## Product overview

### Overview <a href="#overview" id="overview"></a>

**RoboSense AC1 combines solid-state LiDAR, an RGB rolling-shutter camera and a six-axis IMU over USB3.2 Gen 1, with separate DC power.** The assigned `RS-AC1` is the AC1 package, not AC2, an Ethernet RoboSense scanner or a generic UVC-only webcam. Use AC Viewer or the exact `start_ac1.launch.py` driver target to obtain all three streams. [Current AC1 product](https://www.robosense.ai/en/IncrementalComponents/AC1), [driver](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/README.md).

AC1 documentation has material revision differences. The current product page, generic Active Camera wiki table and April 2025 AC1 PDF disagree on depth FOV, range, image dimensions and body thickness. This guide keeps those source profiles explicit and uses the delivered unit's reported stream dimensions/calibration for development.

### Product And Variant Information <a href="#product-and-variant-information" id="product-and-variant-information"></a>

The exact sold option is `RS-AC1`; its package is the AC1 sensor with DC power lead and USB 3 data path. AC2 has a different launch and is not this model. The April 2025 AC1 manual, current AC1 product page and generic Active Camera wiki have different range/FOV/image-size profiles; the specification comparison keeps their revisions separate instead of merging them into a fictional single configuration.

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

## Applications

### Build a synchronized sensing input before adding autonomy

AC1 can support mobile-robot scene collection, image/cloud projection, LiDAR-visual-inertial odometry and calibrated hand-eye research. Begin with a fixed sensor and stationary scene, then confirm stream continuity and factory calibration before moving a platform. A colored point cloud is useful for checking registration; it is not proof of correct metric extrinsics or temporal compensation.

The wide RGB field extends beyond the depth field. A visible object may have no LiDAR point because it lies outside the depth envelope or between angular samples. Rolling-shutter RGB also has within-frame timing effects. Use the actual camera model/distortion and capture timestamps, rather than drawing a single bounding box over an assumed coextensive depth image. [AC1 manual](<../../.gitbook/assets/AC1 User Guide.pdf>), [calibration wiki](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools/calibration.html).

### Project References And Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

* Mobile robot obstacle detection using depth + RGB image streams.
* RGB-D perception datasets for indoor robotics.
* Visual-inertial experiments using AC1 RGB, depth, and IMU output.
* Object detection plus depth filtering for manipulation or navigation.
* USB sensor capture validation before ROS/ROS 2 integration.

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

## Specifications <a href="#specifications" id="specifications"></a>

### Stable integration parameters

| Parameter                       | Documented AC1 value / scope                               |
| ------------------------------- | ---------------------------------------------------------- |
| Laser / sensing                 | 940 nm, Class 1, ToF solid-state depth                     |
| Point output / depth frame rate | About 173,333 points/s /10 Hz                              |
| RGB                             | Rolling shutter; NV12/RGB24; 30 Hz;144° × 78° FOV          |
| IMU                             | 6-axis;±16 g accelerometer;±2000°/s gyro;200 Hz adjustable |
| Blind zone                      | 0.1 m at 90% reflectivity                                  |
| Data / power                    | USB3.2 Gen 1 / separate DC; standard adapter 12 V 2 A      |
| Typical consumption             | 12.6 W, environment dependent                              |
| Protection                      | IP54 sensor; not immersion protection                      |
| Temperature                     | −20 to +60 °C operating;−20 to +70 °C storage              |
| Weight                          | 400 g±10%                                                  |

[Model-specific manual](<../../.gitbook/assets/AC1 User Guide.pdf>), [current technical table](https://robosense-wiki-en.readthedocs.io/en/latest/product/sensor.html). The 12 V 2 A adapter is a documented commissioning baseline, not evidence of a broad allowable DC-input range. Do not apply another LiDAR's 9–32 V rating.

### Revision-sensitive values

| Source profile                       | Depth / ranging                                                                 | RGB / body                                            |
| ------------------------------------ | ------------------------------------------------------------------------------- | ----------------------------------------------------- |
| AC1 manual v1.0,2025-04-11           | 120° × 60°; table 20 m at 10%;±3 cm indoor/±5 cm outdoor 1σ under stated tests  | 1920 × 800; 95 × 42.6 × 80 mm                         |
| Current AC1 product page             | 120° × 60°;70 m longest range,40 m at 10% dark target;1 cm 1σ close-range claim | 144° × 78° RGB field                                  |
| Generic Active Camera technical wiki | 120° × 90°;40 m at 10%;±1 cm 0–5 m,±3 cm beyond 5 m                             | 1920 × 1080; 95 × 80 × 40 mm, length × height × width |

[AC1 PDF](<../../.gitbook/assets/AC1 User Guide.pdf>), [AC1 product](https://www.robosense.ai/en/IncrementalComponents/AC1), [generic wiki](https://robosense-wiki-en.readthedocs.io/en/latest/product/sensor.html). The old PDF also has inconsistent range wording in a footnote and stray E1R running headers; its substantive AC1 connector/USB sections are model identified. Do not silently “upgrade” a received unit's geometry or range from a newer webpage. Record hardware/firmware, read the actual image width/height and factory calibration, and obtain a serial-matched specification for acceptance testing.

## Hardware and connections

### Power and USB connection <a href="#wiring-and-interface" id="wiring-and-interface"></a>

Use the matched 12 V 2 A adapter, DC lead and USB3 data cable. The manual's DC drawing defines **pin 1 VIN, pin 2 GND** and depicts the locked connector; the following page mentions 5.5/2.5 and 5.5/2.1 mm DC interfaces. Verify the supplied cable/adapter fit and polarity against that drawing rather than forcing a similar barrel plug. The connector drawing was visually inspected. Connect with the supply off, secure threaded locks without loading the cable, and keep the optical envelopes unobstructed. [Manual installation, pp 11–12](<../../.gitbook/assets/AC1 User Guide.pdf>).

Plug directly into a host USB3 or better port with a data-rated cable. Avoid a hub in the first-result path. A USB-C shape or charge-only cable does not establish SuperSpeed connectivity. On Linux,`lsusb -t` reports the negotiated topology/speed; USB2 fallback can affect combined image/cloud transport. The sensor has separate DC power; do not assume the USB port powers the complete unit. [Current driver hardware instructions](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/README.md).

### Calibration frames and units

The technical wiki defines AC's reference as the LiDAR frame. Camera origin is **(4.3,0,−26.9) mm**, IMU origin **(−10.6,−9.9,15.5) mm** in that reference. These are nominal platform geometry, not a replacement for factory per-device intrinsics/extrinsics. Use calibration from the actual sensor and verify transform direction before converting mm to m. A shared `rslidar` header string alone does not prove optical-axis conventions or a correct robot transform. [Coordinate drawing](https://robosense-wiki-en.readthedocs.io/en/latest/product/sensor.html#coordinate-systems).

Mount so neither housing/bracket nor a cover clips RGB or depth FOV. Measure AC-to-robot translation and rotation after final assembly. Do not wipe loose grit across the optical window or impose load on the cover. IP54 does not justify immersion or prolonged heavy rain.

### Manufacturer drawings and retained diagrams

![RoboSense AC1 product image](<../../.gitbook/assets/robosense ac1 product.jpg>)

_Manufacturer drawings retained from this guide. Use the stated model/revision and the original manual when interpreting connector views and dimensions._

### Hardware Architecture <a href="#hardware-architecture" id="hardware-architecture"></a>

AC1's three outputs have different sampling and exposure properties: the LiDAR provides 10 Hz depth/points, rolling-shutter RGB is 30 Hz, and the six-axis IMU defaults to 200 Hz in the reviewed driver. USB carries these data streams while the matching 12 V/2 A adapter powers the sensor separately. A visible RGB image therefore proves neither a depth stream nor valid IMU timing.

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

## Software and development resources

### Exact driver and documented host target <a href="#software-and-setup-workflow" id="software-and-setup-workflow"></a>

The reviewed current `robosense_ac_driver` supports both AC1 and AC2, but their launches differ. Use **Ubuntu 22.04/ROS2 Humble** as the documented precompiled ROS baseline; Ubuntu 20.04/ROS Noetic is a separate supported ROS1 path. The broad wiki platform list does not establish a tested native build on every OS. The repository requires its pinned `rs_driver` submodule; its current commit is `56a73b58c5eda9527a0a6cd99d2203b64387d1f6`. [Driver README](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/README.md).

| AC1 output                        | ROS2 type / intended use                                                                  |
| --------------------------------- | ----------------------------------------------------------------------------------------- |
| `/rs_lidar/points`                | `sensor_msgs/msg/PointCloud2`, cloud                                                      |
| `/rs_camera/color/image_raw`      | `sensor_msgs/msg/Image`, raw color                                                        |
| `/rs_camera/rect/color/image_raw` | Rectified image when enabled                                                              |
| `/rs_imu`                         | `sensor_msgs/msg/Imu`, motion data                                                        |
| `/rs_lidar/set_laser_control`     | `std_srvs/srv/SetBool`, AC1-specific laser control; not needed for a passive stream check |

The actual AC1 launch defaults to USB, images 30 Hz, IMU 200 Hz, device calibration enabled, zero-copy disabled and LiDAR-clock use disabled. Keep those defaults for a first checkpoint; record a deliberate change before comparing timestamp domains. Advanced zero-copy is scoped by the project to ROS2 Humble/FastDDS and needs middleware settings; do not enable it to mask a basic USB fault. [Actual AC1 launch](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/src/modules/ac_driver/launch/start_ac1.launch.py).

### AC Studio tools and algorithm boundaries

| Official component              | What to establish before use                                                                               |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| AC Viewer                       | Live display, recording, replay; documented Windows 10 x64/Ubuntu 20.04 x64,8 GB minimum/16 GB recommended |
| Collection / Monitoring         | Configured db3 or MCAP recording; CPU/memory/I/O, frame rate and header-versus-host time monitoring        |
| Camera/LiDAR/IMU calibration    | Factory calibration first; optional target-based recalibration with retained originals                     |
| Point/cloud visual fusion       | IMU compensation and image/cloud projection; check calibration and image geometry                          |
| Localization                    | ESKF IMU+wheel fusion and map-based cloud localization; requires actual wheel/map inputs                   |
| SLAM                            | AC-adapted FAST-LIVO-family LiDAR/vision/IMU odometry; separate algorithm build and dataset requirements   |
| 3D Gaussian splatting           | Rendering from prior SLAM poses; not an independent source of metric pose                                  |
| PromptDA depth                  | Dense inference from sparse cloud +image; inferred pixels are not new laser measurements                   |
| YOLOv8 /Mask2Former /PP-LiteSeg | Detection/segmentation; platform/model dependencies and licenses remain project-specific                   |

[Official tools](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools.html), [algorithm chapters](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms.html). The reviewed platform matrices differ: 3D GS and dense depth do not mark every board supported. Follow the exact algorithm repository rather than infer universal support from the sensor driver.

### Communication Protocol <a href="#communication-protocol" id="communication-protocol"></a>

The older AC1 manual names `cloud_point_t` for point-level XYZ/reflectivity/time and `depth_frame_t` for frame dimensions, data format and timestamp. Those C structures describe that manual/SDK generation, not a version-independent USB wire protocol. For the pinned ROS2 driver, consume the published `sensor_msgs` types listed above and inspect actual width/height, byte layout and header clock before projecting pixels into a cloud. Do not reuse the Ethernet MSOP/DIFOP parser of another RoboSense LiDAR.

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

### AC1 launch parameters and calibration precedence

The AC1 launch's `ms_node` parameters are defined in the launch file, rather than all being declared launch arguments. `start_rviz_node` is a declared argument; do not assume that appending `name:=value` changes every internal node parameter. Inspect or copy the actual AC1 launch when making a controlled configuration.

| AC1 node parameter                                                   | Reviewed default / meaning                                                                                                |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `device_interface`, `usb_box_interface`                              | `usb`, `x3m`; the shared driver also has GMSL/AC2 code, which does not establish a GMSL port on this AC1                  |
| `serial_number`, `topic_prefix`                                      | Empty defaults; identify a serial and disambiguate prefixes before using multiple devices                                 |
| `image_input_fps`, `imu_input_fps`                                   | 30 / 200 Hz input requests, not measured host delivery rates                                                              |
| `enable_jpeg`, `enable_rectify`, `jpeg_quality`                      | false / false / 70; JPEG quality matters only when that encoding path is enabled                                          |
| `enable_angle_and_device_calib_info_from_device`                     | true requests device calibration; retain the original calibration with the recording                                      |
| `enable_device_calib_info_from_device_pripority`                     | true gives device calibration priority; preserve this exact source spelling in configuration                              |
| `angle_calib_basic_dir_path`, `device_calib_file_path`               | Empty overrides use package configuration locations; a path alone does not establish that a host calibration has priority |
| `enable_use_lidar_clock`, `timestamp_compensate_s`                   | false / 0.0 s; clock selection and an added offset are independent of physical synchronization                            |
| `enable_use_dense_points`, `enable_use_first_point_ts`               | false / false; invalid-point layout and cloud stamping affect downstream consumers                                        |
| `enable_pointcloud_send`, `enable_ac1_image_send`, `enable_imu_send` | All true; verify all three streams independently                                                                          |
| `ac1_crop_top/bottom/left/right`                                     | All 0 pixels; image cropping changes geometry used by projection and algorithms                                           |
| Frame IDs / logging                                                  | Point, AC1 image and IMU frames default to `rslidar`; log level 2 is info, file truncation enabled                        |

[Exact AC1 launch](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/src/modules/ac_driver/launch/start_ac1.launch.py). Parameters explicitly labeled AC2 denoise/debloom/frame filters in that shared file are **not an AC1 tuning recipe**. Zero-copy remains off for the initial journal; enable it only with the documented Humble/FastDDS/message infrastructure used by the downstream module.

### Recording and monitoring: configuration and expected outputs

The manufacturer collection tool at commit **9578c33ed4f2c40788b93ac60110faaef210fbd2** uses `DEFAULT_CONFIG/conf/collect.yaml`. Set each `recordsensorconfig.record_sensors[]` entry's `enable_topic`, `topic_name` and `record_file_name`; distinguish the README's generic disabled default from the shipped enabled multi-device preset discussed below. Optional per-topic timeout checks default to **300 ms warning / 500 ms error**. Match these thresholds to the actual cloud/image/IMU rates rather than reuse one timeout as a sensor-health guarantee.

In `recorddataconfig`, choose time segmentation (`RS_RECORD_SEGMENT_BY_TIME`) or the source's exact no-segment identifier **`RS_RECROD_SEGMENT_NO_SEG`**. Segment times are milliseconds; inner segmentation defaults to **30,000 ms**. ROS2 storage is `sqlite3` for db3 or `mcap`, with `serialization_format:cdr`. If compression is enabled, ROS2 uses zstd and the MCAP path requires file-level compression (`compression_mode:file` in the shipped YAML). The save root must end in **`RDCS_ROOT/`**; free-space monitoring is enabled with **32 GB** minimum by default. Set an actual writable mounted volume, task name and capture interval, then verify that the bag can be reopened. The README requires rebuilding after changing the installed configuration. [Pinned collection configuration/build/launch](https://github.com/RoboSense-Robotics/robosense_collect/blob/9578c33ed4f2c40788b93ac60110faaef210fbd2/README.md).

Monitoring at commit **1d7a7dfd4b10db5a7a7946a305ee0a78da589b28** publishes resource and rate diagnostics to `/diagnostics` by default. `ros2_process_manager.refresh_interval_ms` defaults to **6000 ms**. Each monitor has `enable`, `exec_interval_ms` and optional `publish_topic_name`; frequency-topic entries use `name` plus `min_freq`, while timestamp entries use `name` plus `max_difference_ms`. A time-offset alarm compares a message header with host time, so it is meaningful only after deliberately choosing the clock domain.

Use the launch's `config_file`, `node_name`, `enable_self_recording` and `self_recording_dir` arguments to select an explicit config and an optional recorder. A recorded monitor bag containing `metadata.yaml` is the input to `ros2 run rs_monitor parser.py BAG_DIRECTORY`; the parser generates HTML statistics/plots, with optional `--split_duration=1h` for long sessions. A process exit can raise the monitor's cumulative CPU figure because it includes child-process times; RSS is its memory measure and I/O counters exclude cached bytes. [Pinned monitoring configuration and report arguments](https://github.com/RoboSense-Robotics/robosense_monitor/blob/1d7a7dfd4b10db5a7a7946a305ee0a78da589b28/README.md).

For an original acceptance check, record the already-established stationary three-stream session and its diagnostics, reopen the recording, and compare topic counts, header time progression and dimensions with the live journal. Keep an untouched recording and configuration before changing compression, crop, clock or middleware settings. These instructions describe source-supported behavior; collection/monitor execution has not been performed here.

### Five calibration workflows: required observations and outputs

AC1 ships with camera intrinsics and sensor-to-sensor calibration. Preserve those originals; recalibration is a separate experiment after the basic stream checkpoint. The manufacturer calibration repository at **74d0f67d6b60cc1c0080fa51e528535d529428e6** uses `config/calibration.yaml`, saves results in `config/calibration_result.yaml`, and defines its AprilTag board in `config/AprilTag_41h12_65-77.yaml`. The recommended target is **60 × 60 cm**; editing its physical scale requires matching configuration changes.

| Workflow          | Observations / procedure                                                                                                                                                                                           | Output and useful check                                                                                                        |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Camera intrinsics | In the calibration RViz panel: **Open** configuration → **Start Driver** → **Camera Int**. Collect six orientations at each of center/left/right/top/bottom positions, following `/camera/image_indicate` guidance | Intrinsics/distortion and automatic detection on `/camera/image_detecte`; inspect reprojection, not merely a completion dialog |
| Camera–LiDAR      | Target in both fields, preferably 0.8–1.0 m away, about 45° tilt and suspended from background; keep AC1 stable, choose **Camera-Lidar**                                                                           | Relative extrinsics; inspect projection on a held-out target position                                                          |
| Camera–IMU        | Choose **Camera-IMU**; first keep still 10 s until bias calibration completes, then rotate through different axes, pausing 3–5 s between rotations while retaining target visibility                               | Sensor extrinsics from varied motion; a completely stationary sequence cannot provide the needed rotational excitation         |
| AC1–wheel base    | Two previously recorded sets: straight travel and constant-axis rotation; replay into the separate configured straight/circle cloud topics                                                                         | Quaternion/rotation only. Measure translation separately and enter it in the calibration file                                  |
| AC1–robot arm     | Joint set of LiDAR data and end-effector poses with varied translations/rotations and stationary observations                                                                                                      | Translation plus quaternion between sensor and end-effector; check frame direction before use                                  |

The calibration README's camera input is **`/rs_camera/rgb`**, whereas the current driver above publishes **`/rs_camera/color/image_raw`**. Align the actual configuration/remapping and message types before starting; the differing names are not evidence that the current driver automatically supplies both. The source reports expected calibration errors within **1 pixel / 0.3° / 1°** for intrinsic/camera–LiDAR/camera–IMU respectively; these are manufacturer expectations, not results achieved here. The overview wiki's generic stationary camera–IMU advice does not replace the pinned procedure's bias-hold followed by multi-axis excitation. [Calibration method, exact UI and sample datasets](https://github.com/RoboSense-Robotics/robosense_ac_calibration/blob/74d0f67d6b60cc1c0080fa51e528535d529428e6/README.md).

The separate extrinsic tool at **4f19955a2951590268fa39d19e8599b9ec780ac6** documents a straight run of at least **5 m at ≤1 m/s** and rotation through at least **45°** on level ground for its wheeled dataset. Those are controlled offline dataset requirements, not instructions to move an uncommissioned platform. `lidar_to_base_calib_config.yaml` names `straight_lidar_topic`, `circle_lidar_topic`, frame count, existing LiDAR calibration and NDT registration files; set actual motion direction flags rather than infer them from a name. Arm datasets call for translation changes ≥20 cm, rotation changes ≥20° about the axes and ≥4 s stationary after each motion. `lidar_to_arm_calib_config.yaml` additionally names the end-effector pose topic and stable-data threshold. Run these only with independently validated platform/arm control and a suitable collected dataset. [Extrinsic input/output requirements, config files and nodes](https://github.com/RoboSense-Robotics/robosense_calibration_extrinsic/blob/4f19955a2951590268fa39d19e8599b9ec780ac6/README.md).

### Algorithm settings, platform limits and data products

The AC Studio algorithm pages describe separate applications. They do not turn the USB driver into an odometry, navigation or learned-depth system without their required inputs and calibration.

| Module                            | Required inputs and settings                                                                                                              | Output / limitation                                                                                               |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `msf_localization`                | IMU + wheel speed; optional point-cloud localization. Initialize `x_init/y_init/z_init/roll_init/pitch_init/yaw_init` in `loc_param.yaml` | Relative ESKF pose, or global pose when map localization is fused                                                 |
| `lidar_localization`              | Cloud + fusion-localization estimate, PCD map selected by `map_path`, `init_position` and `init_euler`                                    | Map-relative pose using PCL/Ceres; an absent or wrong map/initial pose is not fixed by a sensor calibration write |
| RS-FAST-LIVO                      | LiDAR, IMU and image topics; `img_enable`/`lidar_enable`, actual calibration and `delta_time` in `RS_META.yaml`                           | Tightly coupled pose plus optional colored PCD; verify camera–LiDAR timing before tuning residual thresholds      |
| 3DGS preprocessing/training       | SLAM poses, images and scene conversion to the expected dataset directory                                                                 | Trained/rendered scene; it inherits SLAM pose error and is not a new independent trajectory measurement           |
| YOLOv8 / PP-LiteSeg / Mask2Former | Image stream and the matching platform model/runtime                                                                                      | Object classes/locations or semantic masks; learned inference must be evaluated on intended scenes                |
| PromptDA                          | Corresponding image and sparse cloud, correct calibration/geometry, matching model/runtime                                                | Image-resolution dense depth; synthesized depth is not additional measured laser returns                          |

The localization README describes zero initial position and identity orientation, but the shipped configuration has an example nonzero position as detailed below; set the actual map pose rather than assume global convergence. The current public localization README still includes an internal GitLab clone example; use the public repository linked by the wiki and the pinned reference here, without implying access to that internal server. [Localization inputs and initial-state configuration](https://github.com/RoboSense-Robotics/robosense_localization/blob/1baec33cb1c84edc7dfb8499e675bacbfe0b5f85/README.md).

For RS-FAST-LIVO, `point_filter_num` 3–4 favors speed and 1–2 a denser map. The README suggests `filter_size_surf` **0.05–0.15 indoors / 0.3–0.5 outdoors** and `filter_size_map` **0.15–0.3 / 0.4–0.5**, with `outlier_threshold` **50–250 for darker / 500–1000 for brighter scenes**. These are tuning starting points in that algorithm's units, not verified AC1 accuracy specifications. Its `img_point_cov` and `laser_point_cov` are different measurement-error weights; preserve a baseline dataset before changing them. `pcd_save_en` saves RGB-colored points when images are enabled and intensity-colored points otherwise. The source pins the older non-templated Sophus revision **a621ff** and releases its algorithm under **GPLv2**. [Pinned SLAM parameters/build/license](https://github.com/RoboSense-Robotics/robosense_ac_slam/blob/379872639b734e3370acbdb44467d5b4b173c4c8/README.md).

The perception repository documents **Noetic/Humble**; x86 requires an NVIDIA GPU plus CUDA/TensorRT (**8.5.2.2 recommended**), while ARM adaptations name **RKNN 2.3.0**, **JetPack 6.2** and **RDK X5 OS 3.1.1**. Model downloads and `perception_msgs` are additional dependencies. Its ROS2 launch names are `start_yolov8.py`, `start_ppseg.py` and `start_promptda.py`; a Mask2Former demonstration on the wiki does not imply that `start_ppseg.py` launches Mask2Former. [Pinned perception build/runtime/launch reference](https://github.com/RoboSense-Robotics/robosense_ac_perception/blob/d90ea2d4803b45b1720cdc5c4a6c98a7ee595a02/README.md).

The wiki marks 3DGS on **general x86 and AGX Orin**, not ROCK5B+, OrangePi 5 Ultra, Orin Nano Super or RDK X5. PromptDA large/small are marked on the first five listed platforms, but not RDK X5. Its download sizes are **1360 M / 100 M**; Mask2Former/PP-LiteSeg are **216 M / 49 M** in the wiki, without treating those figures as parameter counts. Use model/runtime-specific evidence before deploying on an unmarked board. [3DGS platform table](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/3d.html), [depth-model table](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/depth_estimation.html), [segmentation table](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/semantic_segmentation.html).

The 3DGS wrapper documents preprocessing → training → SIBR visualization; its viewer example uses a **1920 × 1080** render size. The wrapper's MIT license does not relicense bundled Gaussian Splatting/model dependencies: review each selected component before reuse. [Pinned wrapper and preprocessing reference](https://github.com/RoboSense-Robotics/robosense_ac_3dgs/blob/68f5a8785b4a11a00434ee655584a1365a48f3b5/README.md). No algorithm build, model execution, mapping or accuracy benchmark was run for this guide.

### Firmware upgrade sequence and reproducible algorithm resources

The official R\&D Viewer procedure is separate from AC Viewer recording. First record the current version, preserve calibration/captures and obtain an **AC1-matched** package and compatible R\&D Viewer. The download page reviewed here lists firmware **v0.0.5, 25 April 2025**; that is the page's listed release, not proof that it is the newest firmware for every current AC1. Its Ubuntu/Windows R\&D tools have their own driver-install instructions.

The source upgrade sequence is **USB connection → Version readback → select application-layer OTA image → OTA → success and automatic reboot → select system-layer OTA image → OTA → success and reboot → Version readback**. Keep power and USB uninterrupted through both flash/reboot stages. The prerequisite prose names `application/system` files while the action steps use `_ota_` names; use the actual model-matched supplied package manifest rather than rename an arbitrary file to fit the prose. The Linux download page also contains a malformed `sudo u+x` installation line; inspect the delivered permission script and the current driver permission procedure above instead of executing that typo. If version readback or the first stage fails, retain the actual error and contact manufacturer support rather than repeatedly flash another product's file. [Official download/version listing](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/download.html), [two-stage OTA UI sequence](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/upgrade.html). No firmware flash was performed.

Useful original datasets include [camera intrinsic calibration](https://cdn.robosense.cn/AC_wiki/camera_intrinsics_calib.zip), [camera–LiDAR calibration](https://cdn.robosense.cn/AC_wiki/camera_lidar_calib.zip), [camera–IMU calibration](https://cdn.robosense.cn/AC_wiki/camera_imu_calib.zip), [wheel-platform calibration](https://cdn.robosense.cn/AC_wiki/calibration_extrinsic.zip) and [sensor-to-arm calibration](https://cdn.robosense.cn/AC_wiki/sensor_to_arm_calib.zip). These are manufacturer-linked training/reproduction inputs; they are not this physical sensor's serial-matched factory calibration.

The 3DGS preprocessing path expects extracted images, `utm_V_opt_Cam_pose_W.txt`, `rgb_map.pcd` and `calibration.yaml` under a selected dataset directory. Its image parser takes bag path, image-output path, pose file and sample rate; `slam2gsdata.py --data_dir` then builds the scene. Optional depth preparation adds `filter_depths` with explicit `DEPTH_ROOT`, `SCENE_ROOT` and `CALIBRATION_PATH`, followed by `add_depth_to_gsdata.py` and a depth-validity check. That preprocessing README uses a **ROS1/catkin/rosbag** depth-parser path and `/rs_camera/rgb`; it is not a verified direct Humble/db3 consumer for the newer image topic. Resolve that interface/version conversion before training. [Pinned preprocessing input/output contract](https://github.com/RoboSense-Robotics/robosense_ac_3dgs/blob/68f5a8785b4a11a00434ee655584a1365a48f3b5/preprocess/README.md).

### Actual tool presets, topic adapters and reproducible sample data

The repository configurations expose integration details that the overview chapters omit:

| Pinned component / file                              | Concrete preset and adaptation                                                                                                                                                                                                                                                                                                                                               |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Collection `conf/collect.yaml`                       | Its shipped preset **enables** cloud, IMU, `/device_calib_info`, diagnostics, compressed image/camera-info topics and shared AC2 left/right topics. The README's generic `enable_topic:false` default is not this preset. For the first AC1 raw-image launch, select actual published topics; JPEG/rectified/AC2 topics will not appear just because a recorder enables them |
| Monitoring `config/config.yaml`                      | Resource/frequency checks every **1000 ms**, timestamp checks every **2000 ms**; stock topic thresholds concern diagnostics/parameter events/rosout, so add the actual sensor topics deliberately                                                                                                                                                                            |
| Calibration `config/calibration.yaml`                | Replace its `xxxx/` output/board/result paths, confirm `image_topic` and actual target scale; its `Pinhole`, **8 distortion coefficients** are the tool preset, not a reason to discard the sensor's known factory model                                                                                                                                                     |
| Wheel/arm extrinsic configs                          | Replace author-specific `/home/sti/...` calibration, registration and output paths. Wheel `cloud_size:10` and direction flags are example values; arm stable/accepted observation thresholds are configuration, not seconds unless the implementation says so                                                                                                                |
| Localization `lidar_localization/config/config.yaml` | The README describes a zero default, but the shipped example uses **`init_position:[2,4,0]`**, map `/map/new_map.pcd`, zero Euler angles and input cloud threshold **1000**. Set the actual map/pose before running; do not use an example pose as a localization result                                                                                                     |
| SLAM `config/RS_META.yaml`                           | Cloud/IMU topics match this driver, image is `/rs_camera/rgb` and needs adaptation. Actual image correction is nested **`rs.img_filter.delta_time`** in seconds; the README's short `delta_time` name is conceptual, not a root YAML key to invent                                                                                                                           |

The collection preset uses lowercase compression strings **`message` / `file`**; the README renders these as uppercase descriptive labels. Use the actual configuration schema/spelling and file-level mode for MCAP. Neither recording a nonexistent topic nor generating a monitor report validates a missing image stream. [Collection preset](https://github.com/RoboSense-Robotics/robosense_collect/blob/9578c33ed4f2c40788b93ac60110faaef210fbd2/conf/collect.yaml), [monitor preset](https://github.com/RoboSense-Robotics/robosense_monitor/blob/1d7a7dfd4b10db5a7a7946a305ee0a78da589b28/config/config.yaml), [calibration preset](https://github.com/RoboSense-Robotics/robosense_ac_calibration/blob/74d0f67d6b60cc1c0080fa51e528535d529428e6/config/calibration.yaml), [localization example](https://github.com/RoboSense-Robotics/robosense_localization/blob/1baec33cb1c84edc7dfb8499e675bacbfe0b5f85/lidar_localization/config/config.yaml), [actual SLAM nesting](https://github.com/RoboSense-Robotics/robosense_ac_slam/blob/379872639b734e3370acbdb44467d5b4b173c4c8/config/RS_META.yaml).

For image/cloud coloring, **`robosense_ac_postprocess`** commit **702a578f3f76f2fe78a20c07b843fc0603b1bed3** has an exact **`start_ac1.py`**, separate from AC2. Build/source the current driver and its `robosense_msgs` first, then build the postprocessor. The AC1 preset takes `/rs_camera/color/image_raw`, `/rs_lidar/points`, `/rs_imu` and online `/device_calib_info`; **`USE_ONLINE_CALIB_TOPIC:true`** gives the device-calibration topic priority over the offline file. Contrary to a generic “motion compensated” description, the shipped **`MOTION_CORRECT:false`** leaves that path disabled; IMU-linear and odometry-velocity compensation are also false. `FRAME_TAIL:true` selects the target time when compensation is enabled, and `NUM_DRIFT:100` is the bias-observation count. Inspect the chosen calibration/clock/rectification/crop before expecting correct color registration. [Postprocessor build and exact AC1 launch](https://github.com/RoboSense-Robotics/robosense_ac_postprocess/blob/702a578f3f76f2fe78a20c07b843fc0603b1bed3/README.md), [AC1 input/output/configuration](https://github.com/RoboSense-Robotics/robosense_ac_postprocess/blob/702a578f3f76f2fe78a20c07b843fc0603b1bed3/config/usr_config_ac1.yaml).

The pinned perception preset still uses **`/rs_camera/rgb`** for its image input. YOLOv8 defaults to **640 × 640**, NMS threshold **0.45** and box-confidence threshold **0.5**; PP-LiteSeg input is **1792 × 1024**; PromptDA input is **952 × 420**, with separate image/cloud inputs and platform-specific model files. These are inference configuration sizes/thresholds, not AC1 sensor resolution/range claims. The selected `.trt`, `.rknn` or `.bin` must match the deployed platform/runtime; changing its suffix does not convert a model. Do not treat `clip_min/clip_max` or an undocumented threshold's unit as a new physical range specification. [Actual perception configuration](https://github.com/RoboSense-Robotics/robosense_ac_perception/blob/d90ea2d4803b45b1720cdc5c4a6c98a7ee595a02/modules/config/usr_config.yaml).

| Manufacturer demo                                                                                                                      | Correct application/resource                              |
| -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| [Nezha data](https://cdn.robosense.cn/AC_wiki/nezha.tar.gz)                                                                            | ColorLidar image/cloud fusion                             |
| [Mobile wheeled vehicle](https://cdn.robosense.cn/AC_wiki/localization_demo.zip)                                                       | Fusion/map localization                                   |
| [Climbing Spot](https://cdn.robosense.cn/AC_wiki/zuopaotai.zip), [European architecture](https://cdn.robosense.cn/AC_wiki/shuichi.zip) | AC-adapted FAST-LIVO; the latter is also the 3DGS example |
| [Library dense-depth data](https://cdn.robosense.cn/AC_wiki/dense_depth_net_demo.zip)                                                  | PromptDA large/small depth examples                       |
| [Foreground detection](https://cdn.robosense.cn/AC_wiki/target_detection_radxa.tar.gz)                                                 | YOLOv8 obstacle detection                                 |
| [Open-road segmentation](https://cdn.robosense.cn/AC_wiki/split_network_demo.zip)                                                      | Mask2Former/PP-LiteSeg comparison                         |

The [detection chapter](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/object_detection.html) and [segmentation chapter](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/semantic_segmentation.html) provide their current Foreground/open-road sample links and the shared perception repository. Retain those exact resources when selecting a model; an illustration of Mask2Former is not a claim that the PP-LiteSeg launch selects it. All demo data belong to their source owners and require their applicable licenses. These repositories/configurations were read; their algorithms/models were not built or executed here.

## Getting started

### First result with AC Viewer

1. Record the AC1 label and kit contents. On a stationary mount, connect the matched DC and USB3 cables with power off; then energize the approved adapter. Keep platform drives disabled.
2. On a documented Viewer host, confirm device recognition. On Linux run `lsusb` and `lsusb -t` and record the enumerated USB mode before changing permissions.
3. Start the official AC Viewer 1.0.11 platform package. Select the AC1, inspect firmware/serial and display cloud, RGB and IMU streams. Record actual image width/height and capture mode.
4. Record a short stationary sequence and replay it. Inspect the overlap of a diffuse plane/target in cloud and image, noting that RGB extends beyond the depth field.

**Expected result:** the actual AC1 appears with live multimodal streams and a replayable recording. The observed image dimensions resolve the current stream configuration; they do not settle every conflicting public specification. [Viewer guide](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/ac_viewer.html).

### Build the current ROS2 driver

Use a new Ubuntu 22.04/Humble workspace with colcon and the repository's platform dependencies. The optional GPUJPEG/Rockchip multimedia paths require their own dependencies; the first launch below leaves JPEG and rectification disabled.

```bash
mkdir -p ~/ac1_dev
cd ~/ac1_dev
git clone https://github.com/RoboSense-Robotics/robosense_ac_driver.git
cd robosense_ac_driver
git checkout a4071099133327d5c0be3be22b29c5e1cc686699
git submodule update --init --recursive
source /opt/ros/humble/setup.bash
colcon build
```

If USB access is denied, read the repository's permission script before installing it. It creates udev rules for AC1/AC2 identifiers with MODE 0666 and restarts/reloads device services; this changes local USB access for all users. On the dedicated development host, after reviewing that scope:

```bash
cd ~/ac1_dev/robosense_ac_driver
sudo bash src/modules/ac_driver/scripts/AC_usb_permission.sh --install
```

Reconnect as instructed by the repository, then:

```bash
source /opt/ros/humble/setup.bash
source ~/ac1_dev/robosense_ac_driver/install/setup.bash
ros2 launch ac_driver start_ac1.launch.py start_rviz_node:=true
```

**Expected result:** the AC1 launch publishes `/rs_lidar/points`, the color image and `/rs_imu`. Use `ros2 topic list -t` and verify actual types before adding an algorithm. The AC2 USB/GMSL launch is not a substitute.

### Original ten-second stream journal

In a second sourced terminal, run this original Python 3/rclpy program. It records counts, actual image dimensions and backward header timestamps without commanding the sensor:

```python
import collections
import time
import rclpy
from rclpy.node import Node
from rclpy.qos import qos_profile_sensor_data
from sensor_msgs.msg import Image, Imu, PointCloud2

rclpy.init()
node = Node("ac1_stream_journal")
counts = collections.Counter()
backwards = collections.Counter()
last = {}

def receive(name, message):
    stamp = message.header.stamp.sec * 10**9 + message.header.stamp.nanosec
    if name in last and stamp < last[name]:
        backwards[name] += 1
    last[name] = stamp
    counts[name] += 1
    if counts[name] == 1:
        print(name, "frame", message.header.frame_id)
        if isinstance(message, Image):
            print("image", message.width, message.height, message.encoding)

subscriptions = []
for name, message_type, topic in [
    ("cloud", PointCloud2, "/rs_lidar/points"),
    ("rgb", Image, "/rs_camera/color/image_raw"),
    ("imu", Imu, "/rs_imu")]:
    subscriptions.append(node.create_subscription(
        message_type, topic, lambda m, n=name: receive(n, m), qos_profile_sensor_data))
end = time.monotonic() + 10
while rclpy.ok() and time.monotonic() < end:
    rclpy.spin_once(node, timeout_sec=0.1)
print("counts", dict(counts), "backward stamps", dict(backwards))
node.destroy_node()
rclpy.shutdown()
if any(counts[name] == 0 for name in ("cloud", "rgb", "imu")):
    raise SystemExit("Missing stream; inspect USB, launch enables and topic types")
```

**Expected result:** all three counts increase and image dimensions are printed. A low count or timestamp reversal is a useful diagnostic; the absence of reversals does not prove cross-stream synchronization or valid UTC. Preserve the journal with firmware/launch/calibration records.

### Engineering Setup Checklist <a href="#engineering-setup-checklist" id="engineering-setup-checklist"></a>

| Check          | Expected result                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------- |
| Power adapter  | 12 V 2 A adapter connected                                                                        |
| USB link       | USB 3.0 / USB 3.2 Gen1 host connection                                                            |
| AC Viewer      | Opens without path/encoding issue                                                                 |
| Point cloud    | Real-time depth/point cloud visible                                                               |
| RGB image      | Image stream visible at expected resolution                                                       |
| IMU            | 6-axis data visible or recordable                                                                 |
| Revision check | Confirm AC1 manual/product naming because the source PDF includes an early `E1R User Guide` label |

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

## Troubleshooting and FAQs

### Calibration and firmware recovery <a href="#troubleshooting" id="troubleshooting"></a>

Start with the factory camera intrinsics, camera-to-LiDAR and camera-to-IMU calibration. For optional recalibration, save the originals and use the official target/tool instructions. Keep a target inside both camera and LiDAR fields for camera/cloud calibration. Mobile-platform angular calibration needs recorded straight motion and fixed-axis rotation; translation is measured separately. Robotic-arm hand-eye calibration requires controlled multi-direction motion and end-effector poses; exclude it from first stationary commissioning. [Calibration chapters](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools/calibration.html).

The official firmware chapter lists v0.0.5 (2025-04-25) and a separate **R\&D Viewer**. Its documented order is version check, matching application image, automatic reboot, matching system image, automatic reboot, then version verification. Maintain power throughout. The page contains typographical command/wording errors; use the reviewed package's actual instructions and manufacturer guidance rather than running the malformed `sudo u+x` line. A firmware downgrade/update is not a fix for an unverified USB cable. [Download](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/download.html), [upgrade](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/upgrade.html).

| Symptom                          | Useful checks                                                                                            |
| -------------------------------- | -------------------------------------------------------------------------------------------------------- |
| No USB device                    | Separate DC power, data-rated USB3 cable, direct port,`lsusb`; do not use a charge-only lead             |
| Device present, permission error | Exact VID/PID and reviewed udev rule; replug after setup                                                 |
| Cloud only /missing image        | Actual AC1 launch enables, USB3 topology, CPU/I/O pressure, topic type and competing client              |
| Image/cloud misalignment         | Factory calibration identity, raw versus rectified image, actual resolution and transform direction      |
| Wrong timestamps                 | `enable_use_lidar_clock`, host time domain, compensation and per-stream capture fields                   |
| Unexpected dimensions/range      | Public revision conflict; record hardware/firmware/configuration and obtain serial-matched specification |

**Does the generic wiki's 90° depth FOV apply to this AC1?** It conflicts with both AC1-specific sources'60°. Use the actual delivered calibration and AC1 documentation; do not silently transfer the generic figure.

**Can IP54 tolerate immersion?** No. Protect the complete power/USB connection from water and check the installation's environmental envelope. Clean optics gently after removing loose particles. Store dry and protected. [Official FAQ](https://robosense-wiki-en.readthedocs.io/en/latest/FAQ/FAQ.html).

### Best Practices And Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

* Use the manual values as integration baselines, but confirm final firmware and hardware revision before production design.
* Range and precision depend on target reflectivity, distance, ambient light, and environmental conditions.
* Use USB 3.0-quality cabling and a stable power source for repeatable data capture.
* Do not reuse RSView/Ethernet workflows from RoboSense Fairy or EM4; AC1 uses AC Viewer and USB.
* Confirm camera/IMU extrinsic calibration workflow from the official RoboSense AC Studio or documentation before sensor fusion.

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

### FAQ <a href="#faq" id="faq"></a>

**Which viewer and interface apply?** AC Viewer with USB 3 plus separate DC power; RSView's Ethernet configuration is a different product path.

**Why can the displayed image size differ from the PDF?** AC1 documentation revisions disagree. Read the device's actual profile and calibration, preserve its firmware version and use the matching source profile in acceptance criteria.

**What does a successful stream check establish?** Continuous cloud, image and IMU messages with recorded timestamp domains. It does not validate optional SLAM, inference, body tracking, extrinsic recalibration or a firmware update.

[Model-specific source](<../../.gitbook/assets/AC1 User Guide.pdf>).

## Downloads and technical documents

### Resources <a href="#resources" id="resources"></a>

| Resource                                                                                                                            | Use                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| [AC1 User Guide v1.0](<../../.gitbook/assets/AC1 User Guide.pdf>)                                                                   | Model-specific USB/DC drawing, FOV envelope, legacy specifications and data structures    |
| [Current AC technical wiki](https://robosense-wiki-en.readthedocs.io/en/latest/)                                                    | Drivers, Viewer, collection/monitoring, calibration, algorithm chapters, firmware and FAQ |
| [Current driver](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/README.md) | Pinned AC1/AC2 launches, USB permissions, topics and service                              |
| [AC Viewer Linux 1.0.11](https://cdn.robosense.cn/ACViewer%20Release/AcViewer_Linux_x86_64_release_1.0.11.deb)                      | Ubuntu 20.04 x64 GUI                                                                      |
| [AC Viewer Windows 1.0.11](https://cdn.robosense.cn/ACViewer%20Release/AcViewer_Win_x86_64_release_1.0.11.exe)                      | Windows 10 x64 GUI                                                                        |
| [Calibration toolkit](https://github.com/RoboSense-Robotics/robosense_ac_calibration)                                               | Optional target-based intrinsics/extrinsics                                               |
| [Robot extrinsic toolkit](https://github.com/RoboSense-Robotics/robosense_calibration_extrinsic)                                    | Wheeled platform/arm-specific motion datasets                                             |
| [Firmware/R\&D Viewer resources](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/download.html)               | Exact model/version support workflow                                                      |

The native diagrams/attachments remain below. Manufacturer image rights are retained; the explanatory workflow and stream-journal code are original.

## References and validation

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed 24 November 2026: AC1-specific manual and current product page, technical-wiki sensor/Viewer/driver/tool/calibration/algorithm/firmware/FAQ chapters, and actual current AC1 launch/permission source. Conflicting generic/legacy specifications are preserved with source scope; no unsupported broad DC range is inferred.

**Driver compilation, udev installation, Viewer/ROS execution, stream-journal execution, calibration, motion/physical tests and firmware update: not run.** Syntax checking is local validation of examples only.

* [AC1 manufacturer User Guide](<../../.gitbook/assets/AC1 User Guide.pdf>) — v1.0 2025-04-11; model-specific body read; stray E1R headers noted.
* [Current AC1 model-specific product specifications](https://www.robosense.ai/en/IncrementalComponents/AC1) — 24 Nov 2026.
* [Generic Active Camera specifications/coordinate table](https://robosense-wiki-en.readthedocs.io/en/latest/product/sensor.html) — 24 Nov 2026; conflicts explicitly bounded.
* [Current AC1/AC2 ROS driver](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/README.md) — commit a4071099133327d5c0be3be22b29c5e1cc686699.
* [AC1 actual launch defaults](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/src/modules/ac_driver/launch/start_ac1.launch.py) — commit a4071099133327d5c0be3be22b29c5e1cc686699.
* [AC USB udev rule scope](https://github.com/RoboSense-Robotics/robosense_ac_driver/blob/a4071099133327d5c0be3be22b29c5e1cc686699/src/modules/ac_driver/scripts/AC_usb_permission.sh) — commit a4071099133327d5c0be3be22b29c5e1cc686699.
* [Exact RS-AC1 store package](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale) — 23 Nov catalog and live 24 Nov public page.
* [AC1 technical wiki viewer](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/ac_viewer.html) — current 24 Nov 2026.
* [AC1 technical wiki driver](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/driver.html) — current 24 Nov 2026.
* [AC1 technical wiki hardware](https://robosense-wiki-en.readthedocs.io/en/latest/product/hardware.html) — current 24 Nov 2026.
* [AC1 technical wiki tools](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools.html) — current 24 Nov 2026.
* [AC1 technical wiki algorithms](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms.html) — current 24 Nov 2026.
* [AC1 technical wiki fw-download](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/download.html) — current 24 Nov 2026.
* [AC1 technical wiki fw-upgrade](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware/upgrade.html) — current 24 Nov 2026.
* [AC1 technical wiki faq](https://robosense-wiki-en.readthedocs.io/en/latest/FAQ/FAQ.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-visual\_fusion](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/visual_fusion.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-localization](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/localization.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-calibration](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools/calibration.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-collection](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools/collection.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-monitoring](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools/monitoring.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-object\_detection](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/object_detection.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-ac\_studio](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/ac_studio.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-slam](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/slam.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-3 d](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/3d.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-firmware](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/firmware.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-semantic\_segmentation](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/semantic_segmentation.html) — current 24 Nov 2026.
* [AC1 technical wiki extra-depth\_estimation](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/algorithms/depth_estimation.html) — current 24 Nov 2026.

### Supporting resource links

* [resources](https://www.robosense.ai/en/resources)
