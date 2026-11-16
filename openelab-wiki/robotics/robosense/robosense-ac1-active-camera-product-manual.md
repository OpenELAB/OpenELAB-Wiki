# Robosense AC1 Active Camera Product Manual

Product link: [https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale)

## Engineering Guide

The Robosense AC1 is an active camera module that combines Time-of-Flight LiDAR depth sensing, an RGB camera, and a 6-axis IMU for robot perception. This OpenELAB wiki page is written from the AC1 user guide and focuses on practical engineering setup: DC power, screw-lock USB 3.2 Gen1 data connection, AC Viewer validation, depth/RGB/IMU output, coordinate checks, and maintenance. The source PDF contains an early `E1R User Guide` label on some pages, while the main content and OpenELAB listing identify the product as AC1; verify the final hardware revision before production use.

### Overview

AC1 is designed for intelligent robot vision, indoor and outdoor depth perception, navigation, obstacle detection, mapping, and machine perception workflows where one compact sensor must provide point cloud, RGB image, and IMU data to a host computer.

Unlike Ethernet RoboSense LiDAR products, AC1 does not use MSOP/DIFOP UDP packets for first bring-up. It connects to the host over USB 3.0 / USB 3.2 Gen1 and is validated with AC Viewer.

![AC1 product](<../../.gitbook/assets/ac1 product.jpg>)AC1 product

### Key Features

* Active camera sensor combining LiDAR, RGB camera, and IMU outputs
* Time-of-Flight LiDAR using 940 nm wavelength
* Class 1 eye-safe laser classification
* 120 deg horizontal and 60 deg vertical LiDAR field of view
* RGB camera with 144 deg horizontal and 78 deg vertical field of view
* 1920 x 800 RGB resolution, NV12 and RGB24 output formats
* 6-axis IMU output with adjustable 200 Hz data frequency
* USB 3.2 Gen1 data interface
* Screw-lock Type-C data cable and screw-lock DC power connection
* AC Viewer support for real-time point cloud and image display

### Specifications

| Item                      | Engineering value from AC1 user guide                                 |
| ------------------------- | --------------------------------------------------------------------- |
| Product                   | Robosense AC1 / Active Camera 1                                       |
| Sensor type               | Active camera with LiDAR, RGB camera, and IMU                         |
| Primary application       | Robot environment perception                                          |
| LiDAR ranging principle   | Time of Flight                                                        |
| LiDAR wavelength          | 940 nm                                                                |
| Laser safety              | Class 1 eye safe                                                      |
| LiDAR horizontal FOV      | 120 deg                                                               |
| LiDAR vertical FOV        | 60 deg                                                                |
| LiDAR angular resolution  | About 0.625 deg in the center FOV and about 0.7 deg near FOV edges    |
| Ranging distance          | 20 m at 10 percent NIST diffuse reflector, subject to test conditions |
| Blind area                | 0.1 m at 90 percent reflectance                                       |
| Ranging precision         | +/-3 cm at 1 sigma indoor; +/-5 cm at 1 sigma outdoor                 |
| Point output              | About 173,333 points/s                                                |
| LiDAR frame rate          | 10 Hz                                                                 |
| RGB shutter               | Rolling shutter                                                       |
| RGB horizontal FOV        | 144 deg                                                               |
| RGB vertical FOV          | 78 deg                                                                |
| RGB output formats        | NV12, RGB24                                                           |
| RGB frame rate            | 30 Hz                                                                 |
| RGB resolution            | 1920 x 800                                                            |
| IMU                       | 6-axis data output                                                    |
| Gyroscope range           | +/-2000 dps                                                           |
| Accelerometer range       | +/-16 g                                                               |
| IMU data frequency        | 200 Hz adjustable                                                     |
| Typical power consumption | 12.6 W                                                                |
| Operating temperature     | -20 C to +60 C                                                        |
| Storage temperature       | -20 C to +70 C                                                        |
| Protection rating         | IP54                                                                  |
| Weight                    | 400 g +/-10 percent                                                   |
| Data interface            | USB 3.2 Gen1                                                          |
| Power interface           | DC                                                                    |
| Outer size                | 95 mm x 42.6 mm x 80 mm                                               |

Range, precision, power consumption, and operating-temperature behavior can be affected by target reflectance, target distance, ambient light, ambient temperature, airflow, and other environment conditions.

### Hardware Architecture

The AC1 system has four main blocks:

| Block                  | Function                                                               |
| ---------------------- | ---------------------------------------------------------------------- |
| AC1 sensor             | Captures LiDAR depth, RGB image, and IMU data                          |
| DC power input         | Powers the sensor through a screw-lock DC cable                        |
| USB 3.2 Gen1 data link | Sends LiDAR, RGB, and IMU data to the host computer                    |
| Host computer          | Runs AC Viewer or custom software to display, record, and process data |

![AC1 product structure](<../../.gitbook/assets/ac1 product structure.png>)AC1 product structure

### Optical Field Of View

The AC1 LiDAR and RGB camera have different optical envelopes. Confirm the required overlap and mounting direction before using AC1 for perception calibration, obstacle detection, or sensor fusion.

![AC1 LiDAR FOV](<../../.gitbook/assets/ac1 lidar fov.jpg>)AC1 LiDAR FOV![AC1 camera FOV](<../../.gitbook/assets/ac1 camera fov.jpg>)AC1 camera FOV

### Mechanical Installation

Mount AC1 on a rigid, low-vibration bracket. Keep the optical windows clean and unobstructed, and leave enough space for the screw-lock Type-C data cable, screw-lock DC power cable, and cable bend radius.

Use the structural drawing below for envelope checks and mounting planning. Do not design final brackets only from listing text; use the final drawing, measured hardware, or manufacturer CAD when production tolerances matter.

![AC1 structural drawing](<../../.gitbook/assets/ac1 structural drawing.jpg>)AC1 structural drawing

### Wiring And Interface

The standard accessory set described in the user guide includes:

| Item                              | Description                  | Quantity |
| --------------------------------- | ---------------------------- | -------- |
| Active Camera AC1                 | Main sensor module           | 1        |
| Type-C data cable with screw lock | 1 m                          | 1        |
| DC power cord with screw lock     | 1 m                          | 1        |
| DC adapter                        | 12 V, 2 A                    | 1        |
| Product specification             | Printed or supplied document | 1        |

![AC1 interface definition](<../../.gitbook/assets/ac1 interface definition.jpg>)AC1 interface definition

#### Power Interface

AC1 uses a DC power input. The manual lists standard DC 5.5-2.5 and DC 5.5-2.1 interfaces.

| DC pin | Definition |
| ------ | ---------- |
| 1      | VIN        |
| 2      | GND        |

Check polarity before power-up. The listed adapter is 12 V / 2 A, while typical power consumption is 12.6 W; reserve margin for startup and cable losses.

#### Data Interface

AC1 data transmission uses USB 3.2 Gen1. For first bring-up, use a USB 3.0-capable host port and the screw-lock Type-C cable supplied with the product.

![AC1 physical connection](<../../.gitbook/assets/ac1 physical connection.jpg>)AC1 physical connection

### Software And Setup Workflow

AC Viewer is the primary viewer for AC1. It displays Active Camera data, including point clouds and images, in real time, and can be used to view, record, and store sensor data.

AC Viewer supports:

* Windows 64-bit
* Ubuntu 18.04 or later

Recommended first bring-up workflow:

1. Connect the DC power cable and verify the power source.
2. Connect AC1 to the host PC with the screw-lock USB Type-C data cable.
3. Use a USB 3.0 / USB 3.2 Gen1-capable port on the host.
4. Download AC Viewer from the RoboSense resources page.
5. Extract AC Viewer to a path that does not contain Chinese characters.
6. Run the executable directly after decompression.
7. Verify point cloud and image display before moving to custom software.
8. Record a short sample dataset for integration and regression testing.

PC configuration from the user guide:

| Item       | Minimum configuration                      | Recommended configuration                  |
| ---------- | ------------------------------------------ | ------------------------------------------ |
| CPU        | 7th generation Intel Core i3 or equivalent | Intel 11500 or higher, or Mac M2 or higher |
| GPU        | Integrated graphics                        | NVIDIA RTX 3060 or above                   |
| RAM        | 8 GB                                       | 16 GB or higher                            |
| Connection | USB 3.0                                    | USB 3.0                                    |

### Coordinate System And Calibration Notes

The AC1 coordinate system is defined in the user guide. Use this coordinate definition when aligning AC1 data to robot frames, camera frames, IMU frames, or external perception software.

![AC1 coordinate system](<../../.gitbook/assets/ac1 coordinate system.jpg>)AC1 coordinate system

The user guide points readers to RoboSense AC Studio / wiki material for obtaining AC1 camera and IMU external parameters. For production calibration, confirm the exact calibration workflow, firmware version, and output format with the manufacturer documentation used by your software stack.

### Communication Protocol

AC1 communicates with the host computer over USB 3.0 and outputs IMU, LiDAR, and image sensor data. The user guide describes the following data structures.

| Sensor      | Data structure   | Main fields                                                                                            |
| ----------- | ---------------- | ------------------------------------------------------------------------------------------------------ |
| LiDAR       | `cloud_point_t`  | `points.x`, `points.y`, `points.z`, `intensity`, timestamp information                                 |
| LiDAR frame | `depth_frame_t`  | depth data pointer, buffer byte count, point count, frame-related metadata                             |
| RGB camera  | `image_frame_t`  | width, height, frame format, line step, sequence, capture time, image data pointer, image buffer bytes |
| IMU         | `motion_frame_t` | accelerometer x/y/z, gyroscope x/y/z, temperature, timestamp                                           |

Example field notes from the user guide:

| Field                                | Type             | Description                      |
| ------------------------------------ | ---------------- | -------------------------------- |
| `points.x` / `points.y` / `points.z` | `float`          | 3D point cloud coordinates       |
| `intensity`                          | `uint8_t`        | Point cloud reflection intensity |
| `width` / `height`                   | `uint32_t`       | Image width and height in pixels |
| `frame_format`                       | `frame_format_t` | Image data format                |
| `capture_time`                       | `struct timeval` | Image data acquisition timestamp |
| `accel.x` / `accel.y` / `accel.z`    | `float`          | Acceleration values in m/s2      |
| `gyro.x` / `gyro.y` / `gyro.z`       | `float`          | Angular velocity values          |

### Engineering Setup Checklist

* Confirm that the project needs AC1's combined LiDAR, RGB, and IMU outputs rather than a LiDAR-only Ethernet product.
* Verify the exact product naming and manual revision because early PDF pages contain an E1R label.
* Use the supplied 12 V power adapter or an equivalent regulated source with adequate current margin.
* Use the screw-lock USB Type-C data cable and a real USB 3.0 / USB 3.2 Gen1 host port.
* Start with AC Viewer before debugging custom SDK code.
* Keep the AC Viewer extraction path free of Chinese characters.
* Confirm FOV overlap and mounting direction before sensor-fusion calibration.
* Record a known-good sample after first bring-up for future comparison.
* Keep the optical window clean and avoid direct wiping when mud or hard particles are present.

### Best Practices And Limitations

* Treat range, precision, and power values as condition-dependent engineering values.
* Do not copy setup assumptions from Ethernet LiDAR products such as EMX, EM4, Fairy, or Airy; AC1 uses USB and AC Viewer.
* Confirm final camera/IMU extrinsic parameters before deploying AC1 in a calibrated robot system.
* Avoid mounting AC1 where the optical envelope is blocked by robot covers, bumpers, cables, or brackets.
* Keep the product within the IP54 environmental expectation; do not treat it as an IP67 outdoor LiDAR.
* Do not use product-page dimensions alone for final mechanical design.
* No support email, phone number, address, working-hour text, or after-sales contact block is included in this wiki page.

### Cleaning And Maintenance

Keep the AC1 optical window clean to maintain sensing performance.

Recommended cleaning materials:

* Clean, dust-free cloth
* Neutral solution at moderate temperature, such as soap water or distilled water
* 99 percent alcohol if appropriate for residue cleaning

Cleaning guidance:

1. If only dust or small particles are present, apply a small amount of neutral solution to a clean dust-free cloth and wipe gently.
2. Dry the surface with a clean dust-free cloth.
3. If mud or blocky foreign objects are present, rinse or spray clean water first instead of wiping directly.
4. Use warm soap water to loosen remaining dirt, then gently wipe with a fiber cloth.
5. Rinse away soap residue and dry the surface.

### Troubleshooting

| Symptom                                      | Checks                                                                                                                     |
| -------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| AC Viewer does not show the device           | Confirm DC power, USB cable seating, screw locks, USB 3.0 host port, and operating-system support.                         |
| Point cloud or image display is unstable     | Use the supplied cable, avoid USB hubs during first bring-up, check host performance, and test another USB 3.0 port.       |
| AC Viewer does not start                     | Make sure the extraction path does not contain Chinese characters and that the OS version is supported.                    |
| RGB image appears but point cloud is missing | Confirm that the correct AC Viewer version is used and that the device is fully powered.                                   |
| IMU data is not useful for fusion            | Verify timestamp handling, coordinate frames, and camera/IMU external parameters from RoboSense AC Studio documentation.   |
| Range or precision is lower than expected    | Check target reflectance, ambient light, temperature, target distance, optical-window cleanliness, and mounting vibration. |
| Optical output is blocked                    | Recheck mounting location, cable routing, bracket shape, and the LiDAR/RGB FOV diagrams.                                   |

### Project References And Application Ideas

* Indoor AMR obstacle detection with RGB-assisted debugging
* Robot navigation perception with depth, RGB, and IMU streams
* Short-range 3D mapping and environment reconstruction
* Dataset capture for camera-depth calibration experiments
* Visual-inertial perception research using synchronized image and IMU data
* Quality-control or inspection rigs requiring compact depth and image capture

### Resources

| Resource                          | Link                                                                                                                                                | Notes                                                                        |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| OpenELAB product page             | [https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale)    | Product listing, variants, and purchasing context                            |
| RoboSense resources               | [https://www.robosense.ai/en/resources](https://www.robosense.ai/en/resources)                                                                      | AC Viewer and manufacturer download entry point referenced by the user guide |
| RoboSense AC Studio documentation | [https://robosense-wiki-en.readthedocs.io/en/latest/ac\_studio/tools.html](https://robosense-wiki-en.readthedocs.io/en/latest/ac_studio/tools.html) | External-parameter workflow referenced by the user guide                     |
| RoboSense documentation index     | [https://robosense-wiki-en.readthedocs.io/en/latest/](https://robosense-wiki-en.readthedocs.io/en/latest/)                                          | Viewer and tool documentation referenced by the user guide                   |

### FAQ

#### What is the Robosense AC1 used for?

AC1 is used for robot environment perception where LiDAR depth, RGB image, and IMU data are needed from one compact active camera sensor.

#### Is AC1 an Ethernet LiDAR?

No. AC1 uses USB 3.2 Gen1 / USB 3.0 data transmission. Use AC Viewer for first bring-up rather than RSView, MSOP, or DIFOP workflows.

#### What power supply should I use for AC1?

The standard accessory list includes a 12 V / 2 A DC adapter. The manual lists typical power consumption as 12.6 W, so keep current margin for startup and cable losses.

#### What host computer should I use?

Use at least a 7th generation Intel Core i3 or equivalent CPU, integrated graphics, 8 GB RAM, and USB 3.0. The recommended configuration is Intel 11500 or higher, or Mac M2 or higher, NVIDIA RTX 3060 or above, 16 GB RAM or higher, and USB 3.0.

#### What data does AC1 output?

The user guide describes LiDAR point cloud/depth data, RGB image data, and IMU motion data structures, including `cloud_point_t`, `depth_frame_t`, `image_frame_t`, and `motion_frame_t`.

#### Why does the PDF mention E1R?

The local PDF has early pages labeled `E1R User Guide`, but the main product description and OpenELAB listing refer to AC1 / Active Camera 1. Treat this as a source-title inconsistency and confirm the final document revision for production projects.

#### Does this page include contact or after-sales text from the manual?

No. Manufacturer contact emails, phone numbers, addresses, working hours, and direct after-sales blocks are intentionally omitted from this OpenELAB wiki page.

### Source Notes

* Review date: 2026-06-04.
* Primary source: local user-provided `AC1 .pdf`.
* Manual version noted in PDF: 1.0.
* Manual revision date noted in PDF: 2025-04-11.
* Product page: [https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale.](https://openelab.io/products/robosense-ac1-lidar-depth-camera-pre-sale.)
* Content style reference: existing OpenELAB Wiki page `robosense/robosense-emx`.
* Contact/support blocks, emails, phone numbers, addresses, and working hours were omitted.
