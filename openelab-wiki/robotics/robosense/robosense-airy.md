---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Robosense Airy

{% hint style="info" %}
[**View RoboSense Airy 96 on OpenELAB**](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar)

**Covered model:** RoboSense Airy 96 · **SKUs:** `RS-Airy96-kit`, `RS-Airy96` · Confirm the exact kit/variant when selecting the product option.
{% endhint %}

## Robosense Airy

***

## Product Link

{% embed url="https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar" %}

## Description

Airy is a new type of short-range 3D LiDAR specifically designed by RoboSense to eliminate blind spots. It is primarily used in applications such as robot environment perception, autonomous vehicle environment perception, drone mapping, and smart cities.

Airy adopts RoboSense's innovative signal processing technology, allowing for a minimum detection distance as close as 10 centimeters. With its hemispherical, ultra-wide field-of-view design, it can effectively detect various extremely close-range obstacles over a large area.

## Specifications

<table data-header-hidden><thead><tr><th width="187" valign="top"></th><th width="187"></th><th></th><th></th></tr></thead><tbody><tr><td valign="top">Specifications</td><td></td><td></td><td></td></tr><tr><td valign="top">Number of Channels</td><td>96</td><td>Horizontal Field of View (FOV)</td><td>0~360°</td></tr><tr><td valign="top">Laser Wavelength</td><td>940 nm</td><td>Vertical Field of View (FOV)</td><td>0° ~ 90°</td></tr><tr><td valign="top">Laser Safety Level</td><td>Class1Eye-Safey</td><td><p>Horizontal Angular</p><p>Resolution</p></td><td><img src="file:///C:/Users/Administrator/AppData/Local/Temp/ksohtml20760/wps1.png" alt="">0.4</td></tr><tr><td valign="top">Measurement Range2</td><td>60m (30m @10% NIST)</td><td>Vertical Angular Resolution</td><td>0.947°</td></tr><tr><td valign="top">Blind Zone</td><td>0. 1 m</td><td><p>Accuracy</p><p>(Typical)3</p></td><td>1.5 cm (1 σ)</td></tr><tr><td valign="top">Rotation Speed</td><td>600</td><td>Frame Rate</td><td>10 Hz</td></tr><tr><td valign="top">Number of Output Points</td><td>856,320 pts/s(Single Return Mode), 1,712,640 pts/s(Dual Return Mode)</td><td></td><td></td></tr><tr><td valign="top">Ethernet Transmission Rate</td><td>100 MBps</td><td></td><td></td></tr><tr><td valign="top">Output Data Protocol</td><td>UDP Packets Over Ethernet</td><td></td><td></td></tr><tr><td valign="top">Lidar Data Packet Content</td><td>Distance, Reflectivity, Timestamp, etc.</td><td></td><td></td></tr><tr><td valign="top">Operating Voltage</td><td>9 V - 32 V</td><td>Dimensions</td><td>Diameter 60 mm × Height 63 mm</td></tr><tr><td valign="top">Product Power Consumption4</td><td>8 W(Typical)</td><td><p>Operating</p><p>Temperature5</p></td><td>- 40℃ ~ + 60℃</td></tr><tr><td valign="top">Weight</td><td>230g ± 20g (LiDAR Body)</td><td><p>Storage</p><p>Temperature</p></td><td>- 40℃ ~ + 85℃</td></tr><tr><td valign="top">Time Synchronization</td><td>GPS ，PTP &#x26; gPTP</td><td>Protection Level</td><td>IP67 / IP6K9K</td></tr></tbody></table>

## Mechanical Installation

<div align="center"><figure><img src="../../.gitbook/assets/image (345).png" alt=""><figcaption></figcaption></figure></div>

Screw Specifications:

* GB / T70.1, M3 × 8, hex socket cap head, strength grade 10.9, with anti-loosening;

Installation Requirements:

* The flatness of the installation surface should be better than 0.2 mm.
* Use 3 M3 screws to install on the base, extending 4 – 5 mm from the\
  installation surface. Recommended tightening torque is 13 ±1 kgf.cm.
* Use 2 Φ 4 positioning pins on the base for installation alignment, not\
  exceeding a height of 4 mm.
* When installing the LiDAR, if both the top and bottom of the LiDAR have\
  contact surfaces, ensure the distance between the surfaces is greater than the\
  height of the LiDAR to avoid compressing it.
* When routing the LiDAR cables, do not make them overly tight (leave an\
  installation margin of more than 2 cm) to ensure a degree of slack in the\
  cables.

<figure><img src="../../.gitbook/assets/image (346).png" alt=""><figcaption></figcaption></figure>

Bracket Stiffness and Strength Requirements:

* The fixed bracket needs to have good rigidity for securely mounting the LiDAR and maintaining the LiDAR in a stable state under various conditions. Therefore, the first-order modal frequency of the LiDAR and its fixed bracket should be at least greater than 50 Hz.
* The LiDAR will undergo various random vibrations and mechanical shocks during use. Under these conditions, the bracket needs to withstand significant loads, so it also requires sufficient strength. The bracket material is recommended to be aluminum alloy (thickness above 4 mm) or galvanized steel plate (thickness above 2 mm). Strengthening ribs should be added in various directions to improve its rigidity and strength as much as possible. It is advisable to avoid designing structures with sharp angles, corners less than 0.3 mm, or notches, which may cause stress concentration. The bracket strength needs to be verified through simulation.

Heat Dissipation Requirements:

* The bracket material is recommended to be made of aluminum alloy or galvanized steel plate with a thermal conductivity greater than 50 W/m·K. Some heat dissipation fins should be added to the bracket, with reasonable spacing, height, and direction of the fins to increase the heat dissipation area. The direction should align with the air convection direction for more effective heat dissipation.
* Ensure that the LiDAR base or top cover is not covered with non-metallic materials to avoid affecting the overall heat dissipation, leading to excessive temperature rise ofthe LiDAR.
* If you cannot ensure proper heat dissipation, please communicate with our Field Application Engineer (FAE) in advance to determine a suitable cooling solution and prevent the LiDAR from overheating, which could affect the product's performance or lifespan.

## Interface Description

#### Aviation Plug Interface and Definitions

<figure><img src="../../.gitbook/assets/image (348).png" alt=""><figcaption></figcaption></figure>

Aviation Plug Interface Pin Definitions:

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">Pin No.</td><td valign="top">Spec</td><td valign="top">Signal</td></tr><tr><td valign="top">1</td><td valign="top">26AWG</td><td valign="top">2P(RX+)</td></tr><tr><td valign="top">2</td><td valign="top">26AWG</td><td valign="top">2N(RX-)</td></tr><tr><td valign="top">3</td><td valign="top">26AWG</td><td valign="top">1P(TX+)</td></tr><tr><td valign="top">4</td><td valign="top">26AWG</td><td valign="top">1N(TX-)</td></tr><tr><td valign="top">5</td><td valign="top">24AWG</td><td valign="top">GND</td></tr><tr><td valign="top">6</td><td valign="top">26AWG</td><td valign="top">VIN</td></tr><tr><td valign="top">7</td><td valign="top">24AWG</td><td valign="top">VIN</td></tr><tr><td valign="top">8</td><td valign="top">26AWG</td><td valign="top">GND</td></tr><tr><td valign="top">9</td><td valign="top">30AWG</td><td valign="top">PPS</td></tr><tr><td valign="top">10</td><td valign="top">30AWG</td><td valign="top">SYNC_OUT1</td></tr><tr><td valign="top">11</td><td valign="top">30AWG</td><td valign="top">GPS</td></tr></tbody></table>

#### InterfaceCable(Optional)

<figure><img src="../../.gitbook/assets/image (349).png" alt=""><figcaption></figcaption></figure>

Interface cable Interface Specifications:

<table data-header-hidden><thead><tr><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th><th valign="top"></th></tr></thead><tbody><tr><td valign="top">A End No.</td><td valign="top">Wire Spec</td><td valign="top">Wire Definition</td><td valign="top">A End Color</td><td valign="top"><p>B End</p><p>No.</p></td><td valign="top"><p>C End</p><p>No.</p></td><td valign="top"><p>D End</p><p>No.</p></td><td valign="top"><p>D End</p><p>Color</p></td></tr><tr><td valign="top">1</td><td valign="top">26AWG</td><td valign="top">2P(RX+)</td><td valign="top">Orange-white 1</td><td valign="top">\</td><td valign="top">1</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">2</td><td valign="top">26AWG</td><td valign="top">2N(RX-)</td><td valign="top">Orange 2</td><td valign="top">\</td><td valign="top">2</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">3</td><td valign="top">26AWG</td><td valign="top">1P(TX+)</td><td valign="top">Green-white 3</td><td valign="top">\</td><td valign="top">3</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">4</td><td valign="top">26AWG</td><td valign="top">1N(TX-)</td><td valign="top">Green</td><td valign="top">\</td><td valign="top">6</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">5</td><td valign="top">26AWG</td><td valign="top">GND</td><td valign="top">Black 2</td><td valign="top">2</td><td valign="top">\</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">6</td><td valign="top">26AWG</td><td valign="top">VIN</td><td valign="top">Yellow 1</td><td valign="top">1</td><td valign="top">\</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">7</td><td valign="top">26AWG</td><td valign="top">VIN</td><td valign="top">Red 1</td><td valign="top">1</td><td valign="top">\</td><td valign="top">-</td><td valign="top">\</td></tr><tr><td valign="top">8</td><td valign="top">26AWG</td><td valign="top">GND</td><td valign="top">White 2</td><td valign="top">2</td><td valign="top">\</td><td valign="top">4</td><td valign="top">Orange</td></tr><tr><td valign="top">9</td><td valign="top">30AWG</td><td valign="top">PPS</td><td valign="top">Purple 3</td><td valign="top">\</td><td valign="top">\</td><td valign="top">3</td><td valign="top">Black</td></tr><tr><td valign="top">10</td><td valign="top">30AWG</td><td valign="top">SYNC_OUT1</td><td valign="top">Blue 2</td><td valign="top">\</td><td valign="top">\</td><td valign="top">2</td><td valign="top">Red</td></tr><tr><td valign="top">11</td><td valign="top">30AWG</td><td valign="top">GPS</td><td valign="top">Brown 1</td><td valign="top">\</td><td valign="top">\</td><td valign="top">1</td><td valign="top">Brown</td></tr></tbody></table>

## Storage

{% hint style="info" %}
Important

* Store the product in an indoor environment with normal temperature and dry conditions;
* Handle the product gently to avoid impact or dropping;
* The product should be stored in a safe environment to avoid corrosion, mechanical impact, or exposure to environments exceeding the protection level;
* Regularly inspect the condition of all components and packaging, and it is recommended to check every three months.
{% endhint %}

## Structural Drawing

<div align="left"><figure><img src="../../.gitbook/assets/image (341).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (343).png" alt=""><figcaption></figcaption></figure> <figure><img src="../../.gitbook/assets/image (344).png" alt=""><figcaption></figcaption></figure></div>

## Getting started: verify a live point cloud

1. Identify the exact Airy sensor and cable/kit configuration, then consult the [RoboSense Airy official manual](https://robosense-robotics.github.io/product-manual/en/Airy/) for model-specific power, connector and Ethernet requirements. Do not infer a wiring diagram from photographs.
2. With power disconnected, secure the sensor and connect the manufacturer-specified supply and Ethernet interface. Match the computer network and LiDAR network settings to the manual before connecting a driver.
3. Use RoboSense's documented visualization or the officially supported [rsLiDAR SDK](https://github.com/RoboSense-LiDAR/rsLiDAR_sdk) with its [rs\_driver](https://github.com/RoboSense-LiDAR/rs_driver) dependency. Select the configuration for this exact Airy model; check the SDK README for your installed version and ROS/ROS 2 target.
4. Confirm the sensor is discovered and a continuous point cloud updates when a stationary target is present. Record model/revision, firmware, host IP, driver commit and reported status before starting SLAM or obstacle-avoidance integration.

**Expected result:** a live point cloud from the Airy sensor, with coherent timestamps and orientation. **If it fails:** diagnose power/link LEDs, IP/subnet, the configured model and data ports, and firewall/network filtering in that order. Software execution and hardware testing have **not** been performed for this update.

_Primary reference:_ [_RoboSense Airy product manual, including the ROS/ROS 2 SDK appendix_](https://robosense-robotics.github.io/product-manual/en/Airy/)_._

## Documents

{% file src="../../.gitbook/assets/Airy User Guide.pdf" %}

{% file src="../../.gitbook/assets/Airy Lite User Guide.pdf" %}

{% file src="../../.gitbook/assets/Airy_Certification.zip" %}

## 3D Model

{% file src="../../.gitbook/assets/Robosesne Airy 3D model.zip" %}
