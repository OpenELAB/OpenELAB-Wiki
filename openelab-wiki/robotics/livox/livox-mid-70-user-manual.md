---
description: >-
  Connect MID-70 and Converter 2.0 with distinct power/sync limits, capture a
  circular-FOV cloud and use the verified first-generation Livox SDK/ROS1
  workflow.
---

# LIVOX MID-70 User Manual

{% hint style="info" %}
[**View Livox MID-70 Wide-Angle 3D LiDAR for Mobile Robotics on OpenELAB**](https://openelab.io/products/livox-mid-70-compact-lidar3d?variant=45564605268166)

**Model / option:** Default Title · **SKU:** `Livox-MID-70`
{% endhint %}

## Product overview

**Livox MID-70 is a 70.4° circular-FOV Ethernet LiDAR, not a 360° surround sensor.** It uses the **first-generation Livox SDK/ROS driver**, not the MID-360S SDK2 configuration. This guide covers `Livox-MID-70`, whose store package lists the sensor and a one-to-three cable harness. Confirm the actual harness termination and obtain any required matched converter/power supply before use. [Exact package](https://openelab.io/products/livox-mid-70-compact-lidar3d), [MID-70 manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

The manufacturer manual describes the MID-70 with **Livox Converter 2.0** and a conversion cable. The converter's external supply range is not the bare sensor's range, and its PPS connector is not the same electrical interface as the sensor-side differential sync pair. Keeping those boundaries explicit avoids two common wiring errors.

### Product Profile <a href="#block-390d4c79856d804dab71cb6d43c8d06e" id="block-390d4c79856d804dab71cb6d43c8d06e"></a>

MID-70 is the first-generation Livox SDK/Viewer sensor with a circular 70.4° field, not a 360° MID-360-family scanner. Its optional Converter 2.0 changes the external supply and cable interfaces, not the sensor's own 10–15 V input limit. The reference below separates the optical sensor, bracket, conversion cable and converter so their dimensions, power pins and protection ratings are not mixed.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Introduction <a href="#block-390d4c79856d80dbba94dbde32aaaaad" id="block-390d4c79856d80dbba94dbde32aaaaad"></a>

MID-70 supplies short-to-long-range depth for AGVs/AMRs, service and delivery robots, industrial mobile platforms and perception research. Its published 260 m maximum requires an 80%-reflectivity target under the specified conditions; dark-target range is 90 m at 10% reflectivity. A circular 70.4° field is wider than MID-40's cone but is not an all-around obstacle envelope.

The intrinsic blind zone remains 0.05 m, and the 0.05–0.2 m output is reference-only without guaranteed precision. **Tilting the mount can change platform coverage; it does not eliminate the sensor's blind zone**, contrary to the old wiki's unqualified wording. Preserve the source's IP67 sensor scope: the included conversion cable and mounting bracket do not automatically share that rating. Remove the optical shipping film before first use.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Product Characteristics <a href="#block-390d4c79856d805fbd76c8a1229f2cff" id="block-390d4c79856d805fbd76c8a1229f2cff"></a>

The Livox Mid-70 has a high coverage ratio due to its unique non-repetitive scanning technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surroundings.

Figure 1.2.1 displays the typical point cloud patterns of the Livox Mid-70 over an extended period.

Figure 1.2.1 Point cloud patterns of the Livox Mid-70 accumulated over an extended period

Figure 1.2.2 displays the FOV coverage of Mid-70 compared with traditional mechanical LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is 0.2 seconds, the FOV coverage of the Livox Mid-70 is similar to a 32-line LiDAR sensor. As the integration time increases, however, the FOV coverage of the Livox Mid-70 increases significantly. After 1.5 seconds, the FOV coverage approaches 86%, in that stationary integration example; it is not an instantaneous uniform scan or a guarantee for moving objects. In this way, more details in the FOV can be revealed.

Figure 1.2.2 The FOV coverage of the Mid-70 and non-Livox LiDAR sensors using common mechanical scanning methods. The 16-line non-Livox LiDAR sensor has a vertical FOV of 30°, the 32-line non-Livox LiDAR sensor is 41°, and the 64-line non-Livox LiDAR sensor is 27°.💡

The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams. The FOV coverage (C) can be calculated with the following formula:

C = (area illuminated by laser beams / total field-of-view area) × 100%.

Refer to the official Livox website for more information about how the FOV coverage is calculated.

Table 1.2.1 Point cloud specifications

| Laser Wavelength             | 905 nm                                                                      |
| ---------------------------- | --------------------------------------------------------------------------- |
| Laser Safety                 | Class 1 (IEC 60825-1:2014) (Safe for eyes)                                  |
| Detection Range (@ 100 klx)  | 90 m @ 10% reflectivity; 130 m @ 20% reflectivity; 260 m @ 80% reflectivity |
| Close Proximity Blind Zone   | 0.05 m                                                                      |
| FOV                          | 70.4° (circular)                                                            |
| Distance Random Error        | 1σ (@ 20 m) ≤ 2 cm 1σ (@ 0.2–1 m) ≤ 3 cm                                    |
| Angular Random Error         | 1σ < 0.1°                                                                   |
| Beam Divergence              | 0.28° (Vertical) × 0.03° (Horizontal)                                       |
| Point Rate                   | 100,000 points/s (first or strongest return) 200,000 points/s (dual return) |
| False Alarm Ratio (@100 klx) | < 0.01%                                                                     |

💡

**Note:**

* Close Proximity Blind Zone: Target objects within 0.05 to 0.2 m from the Mid-70 can be detected and point cloud data can be recorded. However, since the detection precision cannot be guaranteed, the data should be taken as a reference only.
* Tested in an environment at a temperature of 25°C (77°F) with a target object that has a reflectivity of 30% and is 20 meters away from the Livox Mid-70. The actual environment may differ from the testing environment. The figure listed is for reference only.
* Tested in an environment at a temperature of 25°C (77°F) with a target object that has a reflectivity of 30% and is within the range of 0.2 to 1 meters from the Livox Mid-70. The actual environment may differ from the testing environment. The figure listed is for reference only.
* The performance may decrease in extreme environments such as those with foggy weather, that cause strong vibration, or where the temperature is -20°C (-4°F) or 65°C (149°F).

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e5baec3e-23f7-4c75-ba9b-103c70157f0f/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Product Characteristics" height="164.9979674796748" width="724.8125">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bac588c4-ae01-4813-b7a4-760bf05765e4/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Product Characteristics" height="437.3325652395988" width="656.9750366210938">

### Overview <a href="#block-390d4c79856d80a7a761f6163c79c8f9" id="block-390d4c79856d80a7a761f6163c79c8f9"></a>

**Livox Mid-70**

1. **Optical Window**

The laser passes through the optical window and scans objects in the FOV.

2. **M3 Mounting Holes**

Make sure to use the correct screws when mounting.

3. **Locating Hole**

The locating hole makes it easy for users to find the correct location to mount a fixed support for the Mid-70. Refer to the Dimensions section for more information.

4. **M12 Aviation Connector**

Used with the conversion cable, the M12 aviation connector connects to the Livox Converter 2.0 to carry out a quick performance test of the Mid-70. If users wish to improve the waterproof and dustproof protection of their system, they can replace the conversion cable with a cable of their own. Refer to the Cables section for more information.

5. **Conversion Cable**

The Livox Mid-70 includes a conversion cable. To connect the Livox Mid-70 to the Livox Converter 2.0, users can use this cable or a cable of their own. Refer to the Cables section for more information.

**Livox Converter 2.0**

1. **LiDAR Connector Port**
2. A JAE MX34012NF1 type connector port is used to connect to the Mid-70. The mating connector is JAE MX34012SF1 LiDAR.
3. **Power Port**
4. Connects to an external power supply.The overview specifies Converter 2.0 input as 9–30 V; its power-cable table instead says 10–30 V. Use 12 V as the shared commissioning baseline. This does not change the bare MID-70 10–15 V limit. The connector type is MOLEX 1053313-1102. The mating connector is MOLEX 105307-1202.
5. **Ethernet Port**
6. An RJ45 type Ethernet connector is used to connect to Ethernet cables.
7. **Sync Port**
8. The 3-pin sync port supports 3.3 V LVTTL sync signal input. Refer to Table 2.2.2 for more information. The mating connector of the sync port connector is Famfull 9.510AO-003-1RO. JST GHR-03 V-S is also compatible.

The connector names above are transcribed identifiers from the manufacturer manual. Match the actual connector drawing and mating face rather than inferring pin order from a part-name substring.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e2478ffb-2ca6-4408-bf3d-83d032dcf37a/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Overview" height="260.25880555270015" width="724.8250122070312">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/77355b65-f41a-4c6f-aaae-ea6efdc1666a/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Overview" height="233.81048387096774" width="724.8125">

## Applications

Use MID-70 for forward or oblique 3D perception, mapping and mobile-robot scene collection. Its non-repetitive scan progressively fills the circular field; longer stationary accumulation improves coverage but mixes acquisition times on a moving platform. Choose the integration window together with expected motion and downstream compensation.

A practical first project is a stationary planar-target capture at a measured distance, followed by repeatable short mobile passes. Compare point position, wall thickness and timing before adding localization. A circular 70.4° field is a cone around the optical axis, not 70.4° vertical by 360° horizontal. Range falls toward the FOV boundary; the long-range center specification is not a guarantee at the edge. [Manual FOV/product-characteristics sections](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

## Specifications

| Parameter                | MID-70 value / condition                                                |
| ------------------------ | ----------------------------------------------------------------------- |
| Laser                    | 905 nm; Class 1 under IEC60825-1:2014, intact product                   |
| Circular FOV             | 70.4°                                                                   |
| Range at 100 klx         | 90 m@10%,130 m@20%,260 m@80% reflectivity                               |
| Near blind zone          | 0.05 m;0.05–0.2 m output is reference-only without guaranteed precision |
| Distance random error,1σ | ≤2 cm at 20 m;≤3 cm at 0.2–1 m, manufacturer 25 °C/30% target tests     |
| Angular random error,1σ  | <0.1°                                                                   |
| Point rate               | 100,000 points/s first/strongest;200,000 dual-return                    |
| Interface                | 100 Mbps Ethernet/UDP                                                   |
| Timing                   | PTP v 2, external PPS, GPS(PPS+UTC via SDK)                             |
| Sensor supply            | 10–15 V DC,12 V recommended                                             |
| Average power            | 8 W; do not size the supply from this alone                             |
| Body / mass              | 97 × 64 × 62.7 mm; about 580 g with cable in the manual                 |
| Temperature              | −20 to 65 °C ambient;−20 to 80 °C shell                                 |
| Ingress                  | IP67 sensor; included cables/bracket are not the same protection scope  |

[Official specifications](https://www.livoxtech.com/mid-70/specs), [manual appendix](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf). No MID-70 integrated IMU output is established by these sources; do not infer one from an Avia or MID-360-family driver option.

**Power discrepancy to retain:** the manual's summary lists 35 W peak, but its detailed cold-start section describes up to 40 W during −20 to 0 °C self-heating for at least 3 minutes. Use the detailed cold-start demand when selecting an approved supply and confirm the actual unit/startup behavior; do not average the figures or use an 8 W-only adapter. Converter 2.0 is listed 9–30 V in the appendix while its power-cable table states 10–30 V; the recommended 12 V commissioning path lies within both. **Never apply 30 V to the MID-70 itself.** [Manual pp 9,12,23](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### MID-70 specifications <a href="#block-390d4c79856d80958ef4c9db72849f0c" id="block-390d4c79856d80958ef4c9db72849f0c"></a>

| Livox Mid -70                        |                                                                                  |
| ------------------------------------ | -------------------------------------------------------------------------------- |
| Operating Temperature Range          | -20° to 65°C (-4° to 149° F)                                                     |
| Operating Temperature Range of Shell | -20° to 80°C (-4° to 176° F)                                                     |
| Laser Wavelength                     | 905 nm                                                                           |
| Laser Safety                         | Class 1 (IEC 60825-1:2014) (safe for eyes)                                       |
| Detection Range (@ 100 klx)          | 90 m @ 10% reflectivity 130 m @ 20% reflectivity 260 m @ 80% reflectivity        |
| FOV                                  | 70.4° (circular)                                                                 |
| Distance Random Error                | 1σ (@ 20 m) ≤ 2 cm 1σ (@ 0.2-1 m) ≤ 3 cm                                         |
| Angular Random Error                 | 1σ < 0.1°                                                                        |
| Beam Divergence                      | 0.28° (Vertical) × 0.03° (Horizontal)                                            |
| Point Rate                           | 100,000 points/s (first or strongest return) 200,000 points/s (dual return)      |
| Data Latency                         | ≤ 2 ms                                                                           |
| Data Synchronization                 | IEEE 1588-2008 (PTP v2), PPS (Pulse Per Second), GPS (PPS+UTC)                   |
| False Alarm Ratio (@ 100 klx)        | < 0.01%                                                                          |
| IP Rating                            | IP67                                                                             |
| Power                                | 8 W average; 35 W summary peak; detailed cold-start section specifies up to 40 W |
| Power Supply Voltage Range           | Livox Mid-70: 10-15 V DC Livox Converter 2.0: 9-30 V DC                          |
| Dimensions                           | 97×64×62.7 mm                                                                    |
| Weight                               | Approx. 580 g                                                                    |

| Livox Mid -70 Mounting Bracket |               |
| ------------------------------ | ------------- |
| Dimensions                     | 100x97x5.7 mm |
| Weight                         | Approx.76 g   |
| Livox Converter 2.0            |               |
| Dimensions                     | 74x52x23 mm   |
| Weight                         | 88 g          |

The summary's 35 W peak is not silently selected over the detailed 40 W self-heating case. Shell operation up to 80 °C is distinct from ambient operation/storage up to 65 °C. Detection ranges and precision retain their target/illumination conditions.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

## Hardware and connections

### Two different connector-numbering systems

MID-70 uses a 12-pin M12 A-code shielded male sensor connector; the manual names Finecables MA12MAHD12STXXXB14 and its mating female MA12FAHD12STXXXB14. The conversion cable also has a rectangular **LiDAR/converter connector** with a different pin numbering order. Read the sensor-side M12 face on p 7 and the explicit cross-table on p 8; do not equate similarly numbered pins at both ends.

| M12 sensor pin | Function                                                        |
| -------------- | --------------------------------------------------------------- |
| 1,9            | Power +,10–15 V                                                 |
| 2,3            | Supply ground                                                   |
| 4,5            | Ethernet TX+, TX−                                               |
| 6,7            | Ethernet RX+, RX−                                               |
| 8,10           | Ground/shield-related returns in the reference conversion table |
| 11             | Sync −,RS485\_B PPS input                                       |
| 12             | Sync +,RS485\_A PPS input                                       |

[Original face/cross-table](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf). This differential PPS input must not be confused with a general RS485 command bus or the MID-360S 3.3 V GPS input. Converter 2.0's separate three-pin sync port is **pin 1 GND, pin 2=3.3 V LVTTL PPS, pin 3 reserved**. Use the correct interface and common reference; leave it unconnected for initial capture. The power-cable pins are 1 positive/2 ground on its own connector, not the M12 table. [Manual pp 8–9](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

The included store harness may be a splitter rather than the manual's converter cable. Verify its exact labels/continuity with power off and use only the approved 10–15 V sensor path. A physically fitting 12-pin M12 cable is not sufficient evidence of electrical compatibility. The first-run recipe below uses the documented matched converter/conversion assembly.

### Mounting and optical protection

Remove the optical shipping film before operation. Do not place glass or a transparent cover inside the defined FOV. Use the dimensioned body/bracket drawings: bottom M3 holes are 5 mm deep; the opposite mounting features have their own limits. Do not let a selected screw bottom out or use the sensor as a payload support. The optional bracket provides M6 mounting positions and a central 1/4-20 UNC feature; those are bracket features, not permission to thread a larger screw into the sensor. [Manual pp 9–11 and appendices](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Data, states and time

Point fields include coordinates, reflectivity, tags and timestamps. MID-70 tags include return number and confidence/noise categories; do not apply a MID-360S tag mask without checking the different format. First/strongest and dual-return output have different rates; dual returns are alternative echoes, not a doubled frame rate.

Normal, Standby and Power Saving are target modes; Initializing/Error are observed states. A connected device in Standby need not emit points. PPS resets relative timing at 1 Hz with 20–200 ms High; GPS timing adds UTC through the SDK, not a GPS serial input on an invented wire. PTP here uses UDP/IPv4. Verify the selected mode and timestamps before fusion. [Manual Usage section](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Connectors <a href="#block-390d4c79856d809c84e9cd7901e5a607" id="block-390d4c79856d809c84e9cd7901e5a607"></a>

Converter 2.0 presents four distinct ports: the rectangular 12-contact LiDAR connector, external power, three-contact synchronization input and conventional RJ45 data. The sensor itself uses a shielded 12-contact A-coded M12. The same pin number in those two connector systems can describe different signals; use the cross-table and the correct sensor/mating face below.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### M12 Aviation Connector <a href="#block-390d4c79856d80de9e23d54cc60033f2" id="block-390d4c79856d80de9e23d54cc60033f2"></a>

The Mid-70 uses the high-reliability M12 aviation connector (male). It is a M12 12P A-code fully shielded male connector that meets the IEC61076-2-101 standard. The connector type is Finecables MA12MAHD12STXXXB14 and its mating connector is Finecables MA12FAHD12STXXXB14, both of which meet the IP rating of IP67. When the M12 aviation connector is used with the conversion cable, users can connect the Mid-70 to the Livox Connector 2.0 for connecting power and transmitting control signals and data. If users wish to improve the waterproof and dustproof protection of their system, they can replace the conversion cable with a cable of their own.

**Conversion Cable**

To connect the Mid-70 to the Livox Converter 2.0, users can use this cable or a cable of their own.

Figure 2.1.1 Conversion Cable

Below is more information on the Livox Mid-70 M12 aviation connector and the aviation and converter connector cable.

Table 2.1.1 Conversion Cable description

| **LiDAR Connector Pin** | **M12 Aviation Connector Pin** | **Signal**   | **Type** | **Description**            | **Color**           |
| ----------------------- | ------------------------------ | ------------ | -------- | -------------------------- | ------------------- |
| 1                       | 1                              | Power+       | Power    | DC10V-15 V                 | Blue/white          |
| 7                       | 9                              | Power+       | Power    | DC10V-15 V                 | Blue                |
| 2                       | 2                              | Ground       | Power    | Ground                     | Silver bare wire    |
| 8                       | 3                              | Ground       | Power    | Ground                     | Silver bare wire    |
| 3                       | 4                              | Ethernet-TX+ | Output   | 100BASE-TX, TX+            | Orange/white        |
| 4                       | 5                              | Ethernet-TX- | Output   | 100BASE-TX, TX-            | Orange              |
| 9                       | 6                              | Ethernet-RX+ | Input    | 100BASE-TX, RX+            | Green/white         |
| 10                      | 7                              | Ethernet-RX- | Input    | 100BASE-TX, RX-            | Green               |
| 5                       | 8                              | Ground       | Power    | Ground                     | Silver braided wire |
| 11                      | 10                             | Ground       | Power    | Ground                     | Silver braided wire |
| 12                      | 11                             | Sync-        | Input    | RS485\_B, Pulse Per Second | Grey                |
| 6                       | 12                             | Sync+        | Input    | RS485\_A, Pulse Per Second | Grey/white          |

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d5165d30-9b31-4fba-ba71-f19ad7bd15e7/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from M12 Aviation Connector" height="255.23342226089972" width="603.9874877929688">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3d6a8546-b868-4beb-bf75-dbfee343c35d/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from M12 Aviation Connector" height="175.81053206980158" width="724.7875366210938">

### Power Cable and Sync Cable <a href="#block-390d4c79856d80e893ccdcd3baabc1c4" id="block-390d4c79856d80e893ccdcd3baabc1c4"></a>

The Mid-70 cables package includes a power cable and sync cable.

**Power Cable**

Power CableConnect "A" to the power port of the Livox Converter 2.0 and connect "B" to an external DC power supply. The connector type of this power cable is MOLEX 105307-1202.

Figure 2.2.1 Power cable

Table 2.2.1 Power cable description

| **Pin** | **Signal** | **Type** | **Description**         | **Color** |
| ------- | ---------- | -------- | ----------------------- | --------- |
| 1       | Power+     | Power    | DC 10 - 30 V (max 30 V) | Red       |
| 2       | Ground     | Power    | Ground                  | Black     |

**Sync Cable**

Connect "A" into the sync port of the Livox Converter 2.0 and connect "B" to the sync signal. The sync cable has a 3-pin connector. The connector type is Famfull 9.510A0-003-1R0, which is compatible with JST GHR03V-S type connectors. Refer to the Data Synchronization section for more information.

Figure 2.2.2 Sync cable

Table 2.2.2 Sync cable description

| **Pin** | **Signal** | **Type** | **Description**               | **Color** |
| ------- | ---------- | -------- | ----------------------------- | --------- |
| 1       | Ground     | Power    | Ground                        | Black     |
| 2       | Sync+      | Input    | 3.3 V LVTTL, Pulse Per Second | Blue      |
| 3       | Reserved   | Reserved | Undefined                     | White     |

Power-lead pin 1 is positive and pin 2 is ground. On the separate three-contact synchronization lead, pin 1 is ground, pin 2 is **3.3 V LVTTL PPS**, and pin 3 is reserved. Never transfer the power lead's pin-1 polarity to the sync lead.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e1f0dbe8-304c-4352-baa4-20254757b16d/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Power Cable and Sync Cable" height="127.84851362335014" width="724.7750244140625">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fd1a9c6d-c889-49f4-b65d-f2a52685a9ff/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Power Cable and Sync Cable" height="125.9613991803664" width="724.7625122070312">

### Ethernet Port <a href="#block-390d4c79856d803d9d61d622507e8404" id="block-390d4c79856d803d9d61d622507e8404"></a>

The Livox Converter 2.0 supports a 100BASE-TX standard RJ45 Ethernet port. The Mid-70 uses two twisted pairs to send and receive data.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Mounting the Livox Mid-70 <a href="#block-390d4c79856d8044855ff61da7076df3" id="block-390d4c79856d8044855ff61da7076df3"></a>

Mount the sensor from the specified bottom face and keep its full circular optical envelope clear. The optional bracket, sensor body and converter have different hole patterns and masses. A CAD envelope checks interference; the measured final translation/rotation establishes the robot-frame transform. Do not use the optical housing as a support for other payloads.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Effective Field of View (FOV) Range <a href="#block-390d4c79856d80ad97a1dd44edce55f1" id="block-390d4c79856d80ad97a1dd44edce55f1"></a>

As shown below, the Mid-70 has a circular FOV of 70.4°. When mounting a Livox LiDAR sensor, make sure that the FOV is not blocked by any objects. Go to [www.livoxtech.com/mid-70](http://www.livoxtech.com/mid-70) to download the 3D models of the Mid-70 and its FOV.

Note that the effective detection range of the Livox Mid-70 varies based on where the object is within the FOV. The closer to the edge of the FOV, the shorter the effective detection range is. The closer to the center of the FOV, the farther the effective detection range. Refer to the diagrams below:

Figure 3.1.2 Effective FOV of the Mid-70

As shown above, when an object with a reflectivity of 10% is placed in the center of the FOV, the object can be detected as far as 90 m. However, as the object moves towards the edge of the FOV, the distance at which it can be detected shortens accordingly. Pay attention to the effective detection range when the Mid-70 is in use.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e2df122e-97d2-461f-97a1-0d2f78e12d50/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Effective Field of View (FOV) Range" height="228.38730853391687" width="724.8125">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/95ea8bf4-026e-4e87-bf5c-b60edb0ba4f4/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Effective Field of View (FOV) Range" height="231.55935448577682" width="724.8125">

### Mounting Notice <a href="#block-390d4c79856d80928b25c61125c2a084" id="block-390d4c79856d80928b25c61125c2a084"></a>

Read and understand the following warnings before mounting the Mid-70.

1. Before use, remove the screen protector from the optical window.
2. Significant dust and stains on the optical window will affect the performance of the Mid-70 sensor. Follow the instructions in the Maintenance section to clean the optical window using compressed air, isopropyl alcohol, or a lens cloth.
3. When mounting the Mid-70, the field of view must not be blocked by an object, including glass. Refer to Figure 3.1.1.
4. There are no restrictions on which direction the Mid-70 can be installed. The top or bottom surface can be used to mount the Mid-70. It is recommended that the surface is parallel to the ground when mounting.
5. The Mid-70 cannot bear any extra payload. Otherwise, the reliability of the product cannot be guaranteed.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Dimensions <a href="#block-390d4c79856d806dafeece2b40cf8518" id="block-390d4c79856d806dafeece2b40cf8518"></a>

**Mounting the Mid-70 without Mounting Bracket**

The bottom surface of the Mid-70 has four M3 mounting holes with a depth of 5 mm. Refer to the dimensions and the mounting holes in the diagrams below to mount or embed the Mid-70 to or in an appropriate place on the target base.

Figure 3.2.1 The Mid-70 Dimensions (refer to Appendix 1)

Table 3.2.1 The Mid-70 Weight & Dimensions

| Weight (with cable) | Approx. 580 g |
| ------------------- | ------------- |
| Dimensions          | 97×64×62.7 mm |

**Mounting the Mid-70 with Mounting Bracket**

It is recommended to first attach the Mid-70 to the mounting bracket using the M3 mounting hole and then mount the Mid-70 using the M6 mounting hole on the mounting bracket. There is one 1/4 inch mounting hole available on the center of the mounting bracket to help mount the Mid-70 based on your requirements.

Table 3.2.2 The Mounting Bracket Weight & Dimensions

| **Weight** | **Approx. 76 g** |
| ---------- | ---------------- |
| Dimensions | 100×97×5.7 mm    |

**Livox Converter 2.0**

Refer to the dimensions below to mount the Livox Converter 2.0.

Table 3.2.3 Livox Converter 2.0 Weight & Dimensions

| **Weight** | **Approx. 88 g** |
| ---------- | ---------------- |
| Dimensions | 74×52×23 mm      |

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e36a4a1e-addd-497f-bcf4-f6209a8cbb2a/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Dimensions" height="205.10989899486663" width="724.8375244140625">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/944aaadc-db37-4934-be8b-3c9ed79c6426/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Dimensions" height="259.27373889970295" width="724.8250122070312">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/89d91a32-05e0-4d8c-8d8f-f839303ce68d/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Dimensions" height="314.64684107313593" width="724.8250122070312">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f72185ad-d6d1-47f3-93b0-7ca35845b226/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Dimensions" height="203.57486186562147" width="724.8250122070312">

### External Power Supply <a href="#block-390d4c79856d802e8875d1b266414711" id="block-390d4c79856d802e8875d1b266414711"></a>

The bare MID-70 requires **10–15 V DC**, with **12 V recommended**. Keep that voltage at the sensor through cable drop and transients. Converter 2.0 has a broader external supply: the manual's power-cable table says **10–30 V**, while its overview/appendix says **9–30 V**. Use 12 V as the common commissioning point and preserve the discrepancy when designing another input level; neither converter range authorizes high voltage at the bare sensor.

The specification summary lists **8 W average / 35 W peak**, but the detailed cold-start section says that at **−20 to 0 °C**, self-heating lasts **at least three minutes** and may reach **40 W**. Size the approved supply/cable against that detailed demand. A warm 8 W observation would not establish cold-start capability. Do not power the sensor from an Ethernet PoE port.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/be34d4d3-b64f-4430-becb-55c6b7590d16/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from External Power Supply" height="295.9845257234727" width="724.8125">

### Coordinates <a href="#block-390d4c79856d80fcae4fda426fdc70f7" id="block-390d4c79856d80fcae4fda426fdc70f7"></a>

The Cartesian coordinates O-XYZ of Mid-70 is defined as below:

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c4a887fb-78fd-41e5-9bf0-d22d9284a74e/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Coordinates" height="206.6480188269785" width="724.7875366210938">

## Software and development resources

Use **Livox SDK**, whose actual device enumeration includes `kDeviceTypeLidarMid70=6`. Do not use a generic README phrase such as“all Livox products”to choose SDK2. The reviewed first-generation `livox_ros_driver` v2.6.0 is a ROS1 package; its documented targets include Ubuntu 18.04/ROS Melodic and older environments. This guide does not claim a native MID-70 ROS2 Driver2 launch. [SDK definition](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_def.h), [ROS README](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/README.md).

| Tool                     | Exact role                                                                                |
| ------------------------ | ----------------------------------------------------------------------------------------- |
| Livox Viewer             | First-generation GUI, device status, return/mode/network selection and LVX capture/replay |
| Livox SDK                | C/C++11 API, sensor discovery/communication and acquisition samples                       |
| `livox_ros_driver`       | ROS1 PointCloud2/custom messages, LVX-to-rosbag and timestamp support                     |
| Viewer download baseline | Windows 0.11.0, Ubuntu 16.04 package 0.10.0 listed by official MID-70 center              |
| Firmware                 | MID70-specific 10.10.0001 listed 2023-04-10; not a prerequisite to first capture          |

[Official MID-70 download inventory](https://www.livoxtech.com/mid-70/downloads). Keep software/firmware version records. Reproducing the documented older ROS environment is different from asserting support on a newer distribution.

### Usage <a href="#block-390d4c79856d80318204c08fc21f2178" id="block-390d4c79856d80318204c08fc21f2178"></a>

MID-70 communication has separate control/status and point-cloud roles. Select Cartesian or spherical output and the intended return mode deliberately, preserving the raw tag and timestamp. Normal, Standby and Power Saving are explicit sensor modes; configuring a receiver or merely detecting broadcasts does not put a sensor into Normal sampling. The first-generation SDK/protocol is the applicable API family.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Output Data <a href="#block-390d4c79856d807ab4a8ee096e963267" id="block-390d4c79856d807ab4a8ee096e963267"></a>

The output information of the Mid-70 sensors includes point cloud data, which have timestamp, status codes, target reflectivity, coordinates, and tag information.

**Point Cloud Data**

A point cloud is the collection of the points where the surface of an object was detected in the FOV of the LiDAR sensor. Each point contains the following information.

Target reflectivity: 0 to 255. 0 to 150 corresponds to the reflectivity within the range of 0 to 100% in the Lambertian reflection model. 151 to 255 corresponds to the reflectivity of target objects with retroflection properties. When the target is less than 2 m from the Mid-70, it may result in a large reflectivity error. The data should be taken as a reference only.

Coordinates: can be expressed as Cartesian coordinates (x, y, z) and Spherical coordinates (r, θ, φ). The relationship between Cartesian and Spherical coordinates is shown in the figure below. When there is no object within the detection range or the object is placed outside the detection range, the coordinates of the point cloud will be expressed as (0, 0, 0) in Cartesian coordinates and as (0, θ, φ) in Spherical coordinates.

Figure 5.2.1.1 Relationship between Cartesian coordinates and Spherical coordinates

Tags: Indicates the return type of the laser and if the point detected is a noise. The format of the tag is as shown below:

| **bit7**                                                                                                                | **bit6** | **bit5**                                                           | **bit4** | **bit3**                                                                                                                    | **bit2** | **bit1**                                                                                                                                                                     | **bit0** |
| ----------------------------------------------------------------------------------------------------------------------- | -------- | ------------------------------------------------------------------ | -------- | --------------------------------------------------------------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| Point property based on nearby waveform distortion: 00: Normal 01: Nearby waveform distortion 10: Reserved 11: Reserved |          | Return number: 00: return 0 01: return 1 10: return 2 11: Reserved |          | Point property based on intensity: 00: Normal 01: Noise that does not meet intensity expectations 10: Reserved 11: Reserved |          | Point property based on spatial position: 00: Normal 01: High confidence level of the noise 10: Moderate confidence level of the noise 11: Low confidence level of the noise |          |

Each tag is composed of one byte. In this byte, bit7, and bit6 are Group 1, bit5 and bit4 are Group 2, bit3 and bit2 are Group 3 while bit1 and bit0 are Group 4.

Group 1 indicates if the sampling point is a noise based on the nearby waveform distortion. Due to the optical system characteristics of the machine, nearby return signal will be distorted by the stray light inside the system, leading to unreliable depth calculation results (especially when the return signal energy is small). "01" indicates that nearby return signal is distorted; "00" indicates that waveform is normal.

Group 2 indicates the return sequence of the sampling point. Featuring a coaxial optical path, the Mid-70 itself will generate a laser return even if there is no detectable object around. This return is recorded as return 0. After that, if there is any object within the detectable range, the first laser that returns to the Mid-70 is recorded as return 1, and then return 2, and so on. If the object is too close to the Mid-70, such as 1.5 m away, the first effective return will be merged into return 0, and be recorded as return 0.

Group 3 indicates if the sampling point is a noise based on the intensity of the return. Normally, the intensity of the returns of the noises generated due to the interference of atmosphere particles such as dust, rain, fog, and snow is quite low. Therefore, the noises are divided into two categories based on the intensity of the return received. "00" stands for normal point cloud; "01" stands for low intensity of the return, indicating that the samples have a high possibility of being noises such as dust, rain, and fog. The lower the confidence level of the sample is, the lower the possibility that it is a noise.

Group 4 indicates if the sampling point is a noise based on its spatial position. Normally, when the Mid-70 sensors detect two objects in close proximity of each other, there will be some thread-like noises between the two objects. The noises are divided into three categories. The lower the confidence level of the noise is, the lower the possibility that it is noise.

**Timestamp**

There are three ways to synchronize data with the Mid-70: IEEE 1588-2008, Pulse Per Second (PPS), and GPS (PPS+UTC).

IEEE 1588-2008: IEEE 1588-2008 is the Precision Time Protocol (PTP) enabling precise synchronization of clocks in measurement and control systems by Ethernet. Livox LiDAR sensors, as the ordinary clock in the PTP, only supports UDP/IPV4 for PTP. Livox LiDAR sensors support the following message events: Sync, Follow\_up, Delay\_req, and Delay\_resp.

PPS: PPS uses the sync cable for data synchronization. Refer to the Cables section for more information. The synchronization logic is shown in the figure below. The pulse interval in PPS is 1s (t0 = 1000 ms) while the continuous time of high-level voltage is from 20 ms to 200 ms (20 ms < t1 < 200 ms). The rising edge of PPS resets the timestamp to zero, so the timestamp of the point cloud data indicates the duration between the point cloud sampling and the PPS rising edge.

Figure 5.2.2.1 Pulse Per Second

GPS: GPS is a way to synchronize the data using the sync cable and UTC time. The PPS port logic is the same as the PPS synchronization mentioned above. Users are able to send the UTC time of each pulse to the Mid-70 via SDK communication protocol. Refer to the SDK Communication Protocols section for more information about commands. The logic of the UTC Time and PPS signal command are shown below. The timestamp of the point cloud data stands for the UTC sampling time of the point cloud once GPS synchronization is in use.

Figure 5.2.2.2 UTC Time Commands

**Status Codes**

The status codes display the current working status of the Mid-70 sensors. By checking the status codes, users can see the temperature status, voltage status, motor status, dust warning, service life warning, and PPS signal status. Status codes can be viewed in Livox Viewer or the Livox SDK. Refer to the Livox Viewer User Manual for more information about how to check status codes.

| **Status**           | **Description**                                                                                                                                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Temperature status   | Indicates if there is any temperature abnormality. Temperature status includes normal, warning, and error.                                                                                                                   |
| Voltage status       | Indicates if there is any internal voltage abnormality. Voltage status includes normal, warning, and error.                                                                                                                  |
| Motor status         | Indicates if there is any internal motor abnormality. Motor status includes normal, warning, and error.                                                                                                                      |
| Dust warning         | Indicates if a significant amount of dust is detected on the optical window or if the optical window is covered by objects.                                                                                                  |
| Service life warning | Indicates if the LiDAR sensor is nearing the end of its service life. The LiDAR sensor can still work for a short period once this warning appears. It is recommended to replace the LiDAR sensor once this warning appears. |
| PPS signal status    | Indicates whether the PPS sync signal is working normally.                                                                                                                                                                   |

For engineering use, keep the raw one-byte tag with each return. The four paired-bit groups are **7–6 near-waveform distortion, 5–4 return order, 3–2 intensity-related noise and 1–0 spatial-noise classification**. A zero-range return remains invalid even after coordinate transformation; it must not become a physical obstacle at the sensor origin. PPS-relative time is not absolute UTC until the SDK-supplied UTC association is established.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/de1e206e-ee81-4f85-ae28-2329bc1f4491/b83bdd63-76fc-4836-93a8-2b75dfdf7391/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Output Data" height="320" width="968.2051282051282">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/694d7a3a-d121-4b2a-9d1e-e5a05e72fa31/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Output Data" height="187.00940792139386" width="600.9625244140625">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0c0fc6d5-b654-40d4-81f2-d13b3763ae89/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Output Data" height="222.61949741768694" width="482.9875183105469">

### Working States & Working Modes <a href="#block-390d4c79856d8036a36aee8205543f1e" id="block-390d4c79856d8036a36aee8205543f1e"></a>

The working states of the Mid-70 includes initializing, normal, standby, power saving, and error.

| **Working states** | **Description**                                                                                                                                |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Initializing       | The LiDAR sensor is powering on.                                                                                                               |
| Normal             | The LiDAR sensor is powered on and working normally.                                                                                           |
| Standby            | The LiDAR sensor is powered on, but the laser beams are not active.                                                                            |
| Power saving       | All components are powered off apart from the communication module.                                                                            |
| Error              | The LiDAR sensor will enter error status when an error is detected and all the components are powered off apart from the communication module. |

Figure 5.2.1 Relationship between the different working states

The Mid-70 also has three working modes: Normal, Standby, and Power Saving. These modes can be set in Livox Viewer and the Livox SDK.

Figure 5.3.2 Relationship between the different working modes available in Livox Viewer

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d6abd848-3948-44b7-a554-982a988989a3/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Working States &#x26; Working Modes" height="323.7069865979646" width="458.9875183105469">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/06d1c734-d343-49e6-b139-48cc152aa8a4/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Working States &#x26; Working Modes" height="272.3217079276469" width="653.9625244140625">

### Livox Viewer <a href="#block-390d4c79856d80c498cacec089472de7" id="block-390d4c79856d80c498cacec089472de7"></a>

Livox Viewer is a computer software designed for Livox LiDAR sensors and Livox Hub. Users can check realtime point cloud data of all the Livox LiDAR sensors connected to a computer, and also record the point cloud data to view offline or for future application. The simple interface makes it easy to use.

Visit [www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer. Livox Viewer supports Windows® 7/8/10 (64 bit) and Ubuntu™ 16.04 (64 bit).

💡

**Note:**

* The historical v1.2 manual treats host firewall filtering as a possible cause of failed discovery. Keep the host firewall enabled and use scoped Livox Viewer/application rules for discovery broadcasts and the configured UDP streams on the isolated sensor interface. Inspect that adapter with Wireshark before changing rules; a blanket firewall shutdown is not a setup prerequisite. Verify the graphics driver separately if Viewer fails to launch or crashes.

For Windows users: unzip the Livox Viewer file and click to open the .exe file named "Livox Viewer."

For Ubuntu users: unzip the Livox Viewer file and click to open the "./livox\_viewer.sh" file under the root directory.

For more information, download the Livox Viewer User Manual from the official website [www.livoxtech.com](http://www.livoxtech.com/).

Use the first-generation Viewer/LVX workflow for this model. Device Manager identifies the actual broadcast code; inspect diagnostics before Normal sampling, record a short LVX and reopen it to verify the saved scan. Viewer2/SDK2 instructions for a MID-360 are not a drop-in MID-70 firmware path.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Software Development Kit (SDK) <a href="#block-390d4c79856d805590c2fa5f3c1fbeb9" id="block-390d4c79856d805590c2fa5f3c1fbeb9"></a>

Besides using Livox Viewer to check real-time point cloud data, users can also use the SDK to apply the point cloud acquired from Livox LiDAR sensors to different scenarios.

**SDK Communication Protocol**

With the SDK Communication Protocol, users can learn how to customize the Livox LiDAR sensors. The SDK Communication Protocol includes the following data roles:

Control Command Data: Configuration and query of LiDAR parameters and status information.

Point Cloud Data: Point cloud data generated by LiDAR.

All data is stored in little-endian format.

Visit [http://www.livoxtech.com/sdk](http://www.livoxtech.com/sdk) to learn more information about SDK communication protocol, Livox SDK API reference.

The pinned first-generation Livox SDK and `livox_ros_driver` targets in this guide are the executable development path. The old generic Windows/Linux/macOS/ROS summary is not a claim that every contemporary OS/ROS2 distribution was built or tested.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### First-generation SDK callbacks, driver settings and LVX replay

For MID-70, the applicable native sequence is **`Init()` → register broadcast/state callbacks → `Start()` → connect the selected broadcast code with `AddLidarToConnect` → register `SetDataCallback` for its handle**. The data callback receives `LivoxEthPacket*` and `data_num`; inspect its declared data type before interpreting point payloads. `QueryDeviceInformation` and state/error callbacks provide identity/health separately from point arrival. `LidarStartSampling`, `LidarStopSampling`, coordinate, return and network setters are asynchronous operations: evaluate both the immediate SDK status and the eventual command response. Finish with `Uninit()` after acquisition has stopped. Do not replace these first-generation APIs with similarly named SDK2 callbacks. [Pinned first-generation API declarations](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_sdk.h).

| Direct-LiDAR ROS1 configuration              | MID-70 consequence                                                                                                                         |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `broadcast_code`, `enable_connect`           | Select the actual 15-character broadcast code and explicitly permit connection; another example sensor's serial is not a wildcard          |
| `return_mode`                                | 0 first, 1 strongest, 2 dual; preserve matching packet/tag/time interpretation                                                             |
| `coordinate`                                 | 0 Cartesian, 1 spherical; a subscriber must match the selected output format                                                               |
| `imu_rate`                                   | The generic parameter is not MID-70 IMU support; the README states MID-series do not support that IMU push setting                         |
| `extrinsic_parameter_source`                 | 0 disables automatic compensation, 1 enables use of saved calibration; avoid applying another host transform twice                         |
| `publish_freq`, `multi_topic`, `xfer_format` | Grouping frequency, shared versus per-sensor topics and PointCloud2/CustomMsg/XYZI format are host choices, distinct from laser point rate |

Use `launch/livox_lidar_config.json` for direct connections. The Hub JSON is a different topology with shared Hub-level connection/coordinate controls; it is not required by Converter 2.0, which is not a Livox Hub. Rich CustomMsg carries first-point `timebase` and each point's `offset_time`, XYZ, reflectivity, tag and line. XYZI drops that richer timing/tag structure. [Driver settings and formats](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/README.md).

The driver's optional `timesync_config` is a **GPS UTC delivery path** based on `LidarSetUtcSyncTime`: the GPS NMEA serial/USB device connects to the **host**, while its correctly leveled PPS connects to the sensor's documented sync input. Set `enable_timesync`, actual `device_name`, `comm_device_type:0`, baud index and parity index. Index **2** selects **9600 baud**, parity index **0** is 8-bit/no parity, and GPRMC/GNRMC output should be **1 Hz**. This configuration does not make MID-70 accept an invented GPS serial wire or convert an Ethernet network into a PTP master.

For a retained **LVX v1.0/v1.1** capture, the first-generation driver's `lvx_to_rosbag.launch` takes an absolute `lvx_file_path` and writes a same-named bag alongside the source on successful conversion. Preserve the original LVX, verify converted topic types/counts and point-time fields, then compare a stationary scene before integrating a mapping package. Conversion is not evidence of SDK2/model compatibility, and no conversion or acquisition was executed here. [Time sync and LVX conversion contracts](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/README.md).

### MID-70 first-generation wire protocol

**Livox SDK Communication Protocol V1.3.0 (26 October 2020)** explicitly includes MID-70. Its frame and sample versions are different from SDK2: command version **1**, sample version **5**. Both use little-endian numeric fields. Device discovery is broadcast from sensor UDP **65000** to host **55000**; a handshake to 65000 supplies the selected host destination ports, and subsequent **1 Hz heartbeats** maintain the connection. After a heartbeat timeout the device broadcasts again. Merely hearing discovery is not a completed handshake or active sampling. [Official first-generation protocol](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol).

| Sample prefix         | Offset / bytes | Interpretation                                                                                     |
| --------------------- | -------------- | -------------------------------------------------------------------------------------------------- |
| `version`             | 0 / 1          | 5 for this protocol revision                                                                       |
| `slot_id`, `LiDAR_id` | 1 / 1; 2 / 1   | Direct connection normally slot 1, ID 1; configured slot applies where supported, not a beam count |
| Reserved              | 3 / 1          | Preserve                                                                                           |
| Status                | 4 / 4, u32     | Bit map below                                                                                      |
| Timestamp / data type | 8 / 1; 9 / 1   | Select time format and record layout before decoding                                               |
| Timestamp bytes       | 10 / 8         | Nanoseconds or GPS calendar/hour-offset representation                                             |
| Data                  | 18 onward      | MID-70 types 2–5 below                                                                             |

| MID-70 data type            | Payload record fields and relative offsets                                                                             | Record count / interpretation                                              |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| 2 extended Cartesian single | XYZ int32 at 0/4/8, reflectivity/tag u8 at 12/13                                                                       | 14 bytes × 96; XYZ mm; 100000 points/s                                     |
| 3 extended spherical single | depth u32 at 0, theta/phi u16 at 4/6, reflectivity/tag at 8/9                                                          | 10 bytes × 96; depth mm, angles 0.01°                                      |
| 4 Cartesian dual            | First 14-byte echo at 0; second at 14, XYZ 14/18/22 and reflectivity/tag 26/27                                         | 28 bytes × 48 **pairs**; 200000 returns/s, not twice the firing-event rate |
| 5 spherical dual            | theta/phi u16 at 0/2; first depth u32 at 4 and reflectivity/tag 8/9; second depth u32 at 10 and reflectivity/tag 14/15 | 16 bytes × 48 pairs; shared angles, separate ranges/tags                   |

Types 0/1 are older Mid-40 layouts without these tag fields; type 6 IMU and 7/8 triple-return formats are **not MID-70 outputs** in this protocol's supported-device table. For spherical data, theta is zenith \[0°,180°] and phi azimuth \[0°,360°], each encoded at 0.01°. Convert distance mm to metres before Cartesian projection. The existing MID-70 tag table above is the exact-model interpretation; the generic wiki tag table reserves bits that this model manual describes more specifically. Do not replace the model table with another sensor's tag mask. [Data types and supported-device matrix](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol#33-point-cloudimu-data-data_type), [pinned packed definitions](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_def.h).

| Timestamp type | Format and meaning                                                                                                         |
| -------------- | -------------------------------------------------------------------------------------------------------------------------- |
| 0              | uint64 ns since boot; not UTC                                                                                              |
| 1              | uint64 ns, PTP source                                                                                                      |
| 2              | Reserved; do not interpret as SDK2 GPS                                                                                     |
| 3              | GPS: year/month/day/hour bytes followed by uint32 microseconds within that hour; the driver maps year byte to 2000 + value |
| 4              | int64 ns relative to PPS rising edge; PPS alone does not provide a UTC date                                                |

The first timestamp belongs to the first firing event. The pinned ROS1 product table uses **10000 ns per MID-70 firing event**; for dual records, both echoes share the event time. It constructs per-return offsets using `(return_index / echo_count) × point_interval`. Do not derive a 5 µs separation between the two echoes just because dual-return throughput is 200000 returns/s. PTP has higher synchronization priority than GPS, then PPS in the generic protocol; loss of the highest-priority source can retain its timestamp type while setting a synchronization fault, so inspect status as well as the type byte. The generic protocol's electrical PPS examples include RS485 for other products; **MID-70 wiring follows this guide's exact manual and connector limits**, not those generic diagrams. [Timestamp specification](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol), [actual MID-70 timing table and conversion](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/livox_ros_driver/livox_ros_driver/lds.h), [per-point offsets](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/livox_ros_driver/livox_ros_driver/lddc.cpp).

### MID-70 command, configuration and status map

Command framing is `0xAA` at 0, version 1 at 1, length u16 at 2 (maximum 1400), command type u8 at 4 (0 request/1 ACK/2 unsolicited message), sequence u16 at 5, header CRC16 at 7, and data at 9. Data starts with **command set u8 and command ID u8**, then function data; a final CRC32 occupies the packet's last four bytes. This is **not SDK2's 24-byte header or 32-bit command sequence**. The pinned SDK computes reflected MCRF4XX-style CRC16 with seed `0x4C49` and seeded CRC32 with `0x564F580A`; use its actual CRC implementation rather than SDK2's CCITT-FALSE/default-CRC recipe. [Wire definition](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol#2-control-command), [SDK packing/checking](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/src/comm/sdk_protocol.cpp).

The following offsets are relative to **frame data byte 0**, including set/ID at 0/1. Ordinary ACKs place result at 2: 0 success, 1 failure; mode changes also allow 2 Switching. Never equate a transport-success return with a successful device ACK.

| Set / ID         | Purpose                    | Relevant data / response                                                                                                          |
| ---------------- | -------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `00/00`          | Broadcast message          | Broadcast-code\[16] at 2, device type at 18; MID-70 type 6                                                                        |
| `00/01`          | Handshake                  | Host IPv4\[4] at 2, data port u16 at 6, command port u16 at 8, generic IMU port at 10; the latter does not add MID-70 IMU support |
| `00/02`          | Identity query             | ACK result at 2, firmware\[4] at 3                                                                                                |
| `00/03`          | Heartbeat                  | ACK result at 2, state at 3, feature at 4, progress/status u32 at 5                                                               |
| `00/04`          | Sampling                   | u8 at 2: 0 stop, 1 start                                                                                                          |
| `00/05`          | Coordinates                | u8 at 2: 0 Cartesian, 1 spherical; RAM-only, resets to Cartesian on reboot                                                        |
| `00/06`          | Disconnect                 | No extra request data                                                                                                             |
| `00/07`          | Abnormal-status message    | u32 status at 2; device can push it at 10 Hz during error                                                                         |
| `00/08`          | Static/dynamic IP          | Mode at 2: 0 dynamic, 1 static; IPv4/mask/gateway at 3/7/11 for supported MID-70 firmware                                         |
| `00/09`          | IP query                   | ACK result/mode at 2/3; IP/mask/gateway at 4/8/12                                                                                 |
| `00/0A`          | Reboot                     | u16 delay at 2; interrupts connection                                                                                             |
| `00/0B`          | Persistent parameter write | TLVs at 2: key u16, length u16, bytes; ACK result/error key/error code at 2/3/5                                                   |
| `00/0C`          | Parameter read             | count u8 at 2, u16 key list at 3; ACK result/error key/error code at 2/3/5 and TLVs at 6                                          |
| `01/00`          | LiDAR target mode          | u8 at 2: Normal 1, Power Saving 2, Standby 3                                                                                      |
| `01/01`          | Store extrinsics           | float32 roll/pitch/yaw degrees at 2/6/10; int32 XYZ mm at 14/18/22                                                                |
| `01/02`          | Read extrinsics            | ACK result at 2; angles at 3/7/11, XYZ at 15/19/23                                                                                |
| `01/06`, `01/07` | Set/get returns            | 0 first, 1 strongest, 2 dual for MID-70; setter input at 2, getter result/mode at 2/3; return selection is saved in flash         |
| `01/0A`          | UTC synchronization        | year since 2000/month/day/hour at 2–5, uint32 microseconds within hour at 6                                                       |

The generic LiDAR set's IDs 03 rain/fog suppression, 04/05 fan and 08/09 IMU frequency have other supported-device lists in V1.3.0; they are not established MID-70 functions. Generic triple return 3 and Avia scan-pattern parameter likewise do not extend MID-70. Set `02` is the **Hub** command set and does not describe Converter 2.0, which does not supply Hub slot-power or extrinsic-processing functions. [Complete official command/support tables](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol).

Persistent key **3** is MID-70 slot ID 1–9 from firmware **10.03.0000** onward. Key 1 high sensitivity is Tele/Avia-only, and key 2 repetitive/non-repetitive switching is Avia-only in this reference. Parameter errors 0–7 mean no error, unsupported key, execution failure, non-writable key, bad value, bad value length, insufficient read capacity and count mismatch. The slot setting persists across restart; host coordinate format does not. Read before writing and retain old values. [Configuration-parameter table](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol#4-configuration-parameters).

| Status bits | Field and interpretation                                                                                                                            |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1–0         | Temperature: 0 normal, 1 high/low, 2 extreme                                                                                                        |
| 3–2         | Internal voltage: 0 normal, 1 high, 2 extreme                                                                                                       |
| 5–4         | Motor: 0 normal, 1 warning, 2 unable to work                                                                                                        |
| 7–6         | Optical window: 0 clear, 1 dirty/blocked                                                                                                            |
| 8 / 9       | Firmware abnormal / PPS valid                                                                                                                       |
| 10 / 11     | Service-life warning / generic fan status; do not infer a MID-70 controllable fan from this generic bit                                             |
| 12          | Self-heating flag: **wiki says 0 on/1 off, SDK comment says 0 normal/1 on**; retain the raw bit until firmware-specific interpretation is confirmed |
| 13          | PTP signal detected                                                                                                                                 |
| 16–14       | 0 no sync, 1 PTP, 2 GPS, 3 PPS, 4 highest-priority source abnormal                                                                                  |
| 29–17       | Reserved                                                                                                                                            |
| 31–30       | 0 normal, 1 warning, 2 error/shutdown                                                                                                               |

Heartbeat state is separate: 0 Initializing, 1 Normal, 2 Power Saving, 3 Standby, 4 Error. Its final u32 is initialization progress only in Initializing, otherwise status. Preserve state, the full raw status word and time type together; an error bit or missing synchronization should not be “fixed” by changing coordinate scaling. [Status specification](https://github.com/Livox-SDK/Livox-SDK/wiki/Livox-SDK-Communication-Protocol#35-status-code), [pinned status bit-field declarations](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_def.h).

## Getting started

### Documented static-IP first result

1. Check actual sensor/harness/converter labels, secure the sensor and connect with all sources off. On the documented Converter 2.0 path, use an approved 12 V input with cold-start capability; confirm the converter output is within 10–15 V at the sensor.
2. Set the dedicated host Ethernet adapter to `192.168.1.50/24`. Factory MID-70 IP is `192.168.1.1XX`, using the serial number's last two digits. Verify the received configuration before assuming that default.
3. Connect converter RJ45 to the host's data interface and apply the approved power. Leave synchronization disconnected/insulated. Keep only the intended sensor on this commissioning link.
4. Extract and run the first-generation Livox Viewer package for its documented host platform. Select the observed broadcast code; MID-70 uses its serial with an extra `1`. Record firmware/status and choose Normal mode if needed.
5. Observe an updating circular-sector cloud, record a short LVX and replay it. Compare one fixed target's position and the scene orientation. Then change first/strongest to dual-return only as a controlled comparison, recording each setting.

**Expected result:** the identified MID-70 reaches Normal, delivers current points and produces a replayable recording. A 0.05 m target is not a precision acceptance fixture. [Manual Getting Started/Usage](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

For a deliberate DHCP setup, switch the sensor to dynamic addressing using Viewer/SDK first, then connect the converter and host to LAN ports on a DHCP-capable router. Do not attach a factory-static sensor to a random router and assume its target network changed. Record the assigned address and discovery identity before returning to direct-link operation.

### Build the first-generation C/C++SDK

Prerequisites: a documented supported Linux environment, C++11 compiler and CMake ≥3.0. Use a fresh folder; the SDK's sample connects all discovered devices by default, so keep the bench LAN limited to the intended sensor or use its documented broadcast-code whitelist.

```bash
mkdir -p ~/mid70_dev
cd ~/mid70_dev
git clone https://github.com/Livox-SDK/Livox-SDK.git
cd Livox-SDK
git checkout 9306596a2bf15c1343bc023b497465ed0a32909d
mkdir -p build
cd build
cmake ..
make -j2
sudo make install
./sample/lidar/lidar_sample
```

**Expected result:** the sample discovers the intended MID-70 and reports acquisition according to its sample logging. Stop the application before reopening Viewer. An installed library alone is not a data checkpoint. [SDK build/sample instructions](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/README.md).

### ROS1 publication and original continuity monitor

For the source-documented **Ubuntu 18.04/ROS Melodic** baseline with SDK installed:

```bash
mkdir -p ~/mid70_ros
cd ~/mid70_ros
git clone https://github.com/Livox-SDK/livox_ros_driver.git ws/src
cd ws/src
git checkout 3d240d5666129e1a3052e78ee8487a04b08fdda3
source /opt/ros/melodic/setup.bash
cd ~/mid70_ros/ws
catkin_make
source devel/setup.bash
roslaunch livox_ros_driver livox_lidar_rviz.launch bd_list:=ACTUAL_BROADCAST_CODE
```

Replace `ACTUAL_BROADCAST_CODE` with the observed 15-character code, not an IP address. The reviewed launch defaults to PointCloud2,`livox_frame` and 10 Hz host publication; that publication interval is not the sensor's 100,000 points/s or ≤2 ms latency. [Actual launch](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/livox_ros_driver/launch/livox_lidar_rviz.launch).

In a second sourced terminal, run this original read-only Python 3 monitor (`rospy`/`sensor_msgs` must be available in that interpreter). It reports frame/message continuity for 10 seconds without commanding the LiDAR:

```python
import time
import rospy
from sensor_msgs.msg import PointCloud2

frames = 0
previous_stamp = None
backwards = 0

def inspect(message):
    global frames, previous_stamp, backwards
    stamp = message.header.stamp.to_nsec()
    if previous_stamp is not None and stamp < previous_stamp:
        backwards += 1
    previous_stamp = stamp
    frames += 1
    if frames == 1 or frames % 10 == 0:
        print("frames", frames, "points", message.width * message.height,
              "frame", message.header.frame_id, "backwards", backwards)

rospy.init_node("mid70_cloud_continuity", anonymous=True)
subscription = rospy.Subscriber("/livox/lidar", PointCloud2, inspect, queue_size=1)
end = time.monotonic() + 10.0
while not rospy.is_shutdown() and time.monotonic() < end:
    time.sleep(0.05)
subscription.unregister()
if frames == 0:
    raise SystemExit("No PointCloud2; check topic, launch and transfer format")
```

**Expected result:** rising frame count, nonzero point counts and an intentional sensor frame. Backward timestamps require investigation; their absence does not prove external synchronization. On a ROS Melodic installation whose Python bindings are Python 2-only, use the matching interpreter/bindings or the standard `rostopic hz /livox/lidar` checkpoint instead; do not claim Python 3 availability from the ROS name alone.

### Manual commissioning reference <a href="#block-390d4c79856d800bba3fd882308d1418" id="block-390d4c79856d800bba3fd882308d1418"></a>

Use the factory-static path on a stationary bench first: the sensor, intact conversion cable, Converter 2.0, matching regulated supply, Ethernet host and first-generation Livox Viewer are the actual components. Leave optional synchronization disconnected until ordinary cloud acquisition and state diagnostics are coherent. The default sensor identity and supply boundaries below apply to MID-70, not an SDK2 MID-360 configuration.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Connection <a href="#block-390d4c79856d80e5abfffadeb2324268" id="block-390d4c79856d80e5abfffadeb2324268"></a>

Factory-static MID-70 uses `192.168.1.1XX`, with `XX` from the final two serial digits; subnet mask is `255.255.255.0` and the documented gateway is `192.168.1.1`. For the first direct connection, use a unique host `192.168.1.50/24` on the dedicated wired adapter.

**Static network procedure**

1. Inspect the actual host adapter name/address. On Linux, `ip -br link` and `ip -br address` are read-only inventory commands.
2. In Windows adapter IPv4 Properties, enter `192.168.1.50` and mask `255.255.255.0`; on a supported Linux desktop use the adapter's IPv4 Manual settings for the same test address. Avoid conflicts with another interface or sensor.
3. With power removed, connect the sensor to its conversion cable and Converter 2.0, the converter RJ45 to the host, and the converter to the matched 12 V commissioning supply. Optional PPS remains disconnected.
4. Open first-generation Livox Viewer, identify MID-70 by serial/broadcast code and inspect its working state before selecting Normal sampling. The broadcast code is the sensor serial followed by `1` in this model's reference.
5. Record a static cloud, state/status and network settings. For multiple sensors, assign unique addresses and use an appropriate switch; the manual recommends Gigabit switching for more than six sensors.

**Deliberate DHCP transition**

1. Establish and save a working static configuration first. In Viewer select the actual MID-70 and change its IP mode to dynamic; changing a router does not change a factory-static sensor's mode.
2. Reconfigure the host for automatic IPv4/DHCP, and connect both host and converter to LAN ports on a DHCP-capable network. Reconnect/power the unit according to the manual, then discover it by serial/broadcast code and record the assigned address.
3. If it is absent, inspect DHCP/ARP traffic and the selected adapter before resetting the sensor. A direct host-only cable generally supplies no DHCP server.

This resolves the old exported instructions' confusing router/direct-cable ordering. Do not copy the historical Ubuntu 16.04 `ifconfig enp4s0` example onto an unidentified modern adapter.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19cf8c6c-3472-4348-a2f2-c9eb79197874/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Connection" height="311.02232336380627" width="724.8250122070312">

&#x20;

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/de8f3eef-bd26-44ff-9ce6-3fcb5658f2aa/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Connection" height="221.5999962678282" width="724.7999877929688">

### Dual Return Mode <a href="#block-390d4c79856d80718b19e46ca5e8ded8" id="block-390d4c79856d80718b19e46ca5e8ded8"></a>

The Mid-70 can be set to Dual Return mode using Livox Viewer or the Livox SDK. The Mid-70 can generate a point cloud of up to two returns in Dual Return mode, which has a point rate of 200,000 points per second.

To set the return mode, run Livox Viewer after the Mid-70 is connected.

Click the desired device under Device Manager. Click to select the return mode.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Original MID-70 identity query without a sampling request

This C++11 example uses an **already built first-generation SDK at the pinned revision**. It connects only the explicitly supplied MID-70 broadcast code, queries firmware and prints state/status. It performs a handshake and heartbeats, but sends no Sampling, return-mode, IP, calibration, reboot or firmware request. Close Viewer/other SDK clients first so they do not compete for the connection. The sensor's pre-existing physical operating state still matters; the program does not promise to stop an already operating sensor.

Save as `mid70_query.cpp`:

```cpp
#include "livox_sdk.h"
#include <atomic>
#include <chrono>
#include <cstdio>
#include <cstring>
#include <string>
#include <thread>

static std::string selected;
static std::atomic<bool> requested{false};
static std::atomic<bool> received{false};

static void firmware(livox_status status, uint8_t handle,
                     DeviceInformationResponse* reply, void*) {
  if (status != kStatusSuccess || reply == nullptr) {
    std::printf("firmware query handle=%u transport=%d no valid reply\n",
                unsigned(handle), int(status));
    return;
  }
  std::printf("firmware result=%u version=%u.%u.%u.%u\n",
              unsigned(reply->ret_code), unsigned(reply->firmware_version[0]),
              unsigned(reply->firmware_version[1]), unsigned(reply->firmware_version[2]),
              unsigned(reply->firmware_version[3]));
  received = reply->ret_code == 0;
}

static void state(const DeviceInfo* info, DeviceEvent event) {
  if (!info || info->type != kDeviceTypeLidarMid70 ||
      std::strncmp(info->broadcast_code, selected.c_str(), kBroadcastCodeSize) != 0)
    return;
  std::printf("event=%d handle=%u state=%d raw_status_or_progress=0x%08x\n",
              int(event), unsigned(info->handle), int(info->state),
              unsigned(info->status.progress));
  if (event == kEventConnect && !requested.exchange(true)) {
    livox_status status = QueryDeviceInformation(info->handle, firmware, nullptr);
    std::printf("query submission=%d\n", int(status));
  }
}

static void broadcast(const BroadcastDeviceInfo* info) {
  if (!info || info->dev_type != kDeviceTypeLidarMid70 ||
      std::strncmp(info->broadcast_code, selected.c_str(), kBroadcastCodeSize) != 0)
    return;
  uint8_t handle = 0;
  livox_status status = AddLidarToConnect(info->broadcast_code, &handle);
  std::printf("selected broadcast connection=%d handle=%u\n", int(status), unsigned(handle));
}

int main(int argc, char** argv) {
  if (argc != 2 || std::strlen(argv[1]) == 0 || std::strlen(argv[1]) >= kBroadcastCodeSize) {
    std::fprintf(stderr, "Usage: mid70_query ACTUAL_BROADCAST_CODE\n");
    return 2;
  }
  selected = argv[1];
  if (!Init()) return 3;
  SetBroadcastCallback(broadcast);
  SetDeviceStateUpdateCallback(state);
  if (!Start()) { Uninit(); return 4; }
  std::this_thread::sleep_for(std::chrono::seconds(10));
  Uninit();
  return received ? 0 : 5;
}
```

1. In the documented Linux SDK environment, set `MID70_SDK_ROOT` to the actual pinned checkout already built by the preceding procedure. Confirm its `build/sdk_core/liblivox_sdk_static.a` exists. Use the device's observed broadcast code, not a code copied from an example screenshot.
2. Compile this original program and run it on the isolated, already commissioned sensor network:

```bash
c++ -std=c++11 mid70_query.cpp \
  -I"$MID70_SDK_ROOT/sdk_core/include" \
  "$MID70_SDK_ROOT/build/sdk_core/liblivox_sdk_static.a" \
  -pthread -o mid70_query
./mid70_query ACTUAL_BROADCAST_CODE
```

3. Check both `query submission` and the later `firmware result`. Read a progress value as progress only while state is Initializing; otherwise use the status bit table. Save identity and status before considering any configuration change.

**Expected result:** connection/query submission reports success and a later device reply gives result 0 plus its actual four-byte firmware version. No matching broadcast produces exit 5 after the finite observation period. A missing callback, timeout or nonzero result is a failure checkpoint, not an invitation to reset the IP. No output shown above is claimed as a hardware observation. The source has been reviewed against the actual API; SDK linking/execution and hardware tests are not run. [Exact SDK callbacks/query types](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_sdk.h).

For subsequent **read-only configuration inspection** in a model-matched application, use `LidarGetPointCloudReturnMode`, `LidarGetExtrinsicParameter` and `LidarGetSlotNum`, each with its declared response type and both transport/device error checks. Record return mode, roll/pitch/yaw degrees, XYZ mm and persistent slot 1–9. Do not replace these getters with similarly named setters. Before requesting samples, install `SetDataCallback` for the correct handle: its pointer becomes invalid after return, each handle can receive on its own thread, and blocking disk/SLAM work belongs in an application-owned queue. [Return/extrinsic/slot getters and callback lifetime](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_sdk.h).

## Troubleshooting and FAQs

| Symptom                              | Checks and supported recovery                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Repeated cold boot                   | Detailed 40 W self-heating demand, supply/cable drop at sensor, temperature and converter rating; never exceed 15 V at bare sensor |
| No discovery                         | Correct static `.50/24`, actual sensor IP, broadcast filtering, matched converter and only one owner application                   |
| Discovered but no cloud              | Normal versus Standby/Power Saving/Error, correct first-generation software, broadcast-code whitelist and supply                   |
| Wrong point/return interpretation    | Actual return mode and MID-70 tag layout; do not use an S-model tag filter                                                         |
| No ROS2 launch                       | This source-backed baseline is SDK1/ROS1; select a separately verified bridge/integration, not a renamed SDK2 config               |
| Timing resembles repeated seconds    | PPS-relative versus GPS absolute/PTP time and lock; verify the expected time base before fusion                                    |
| Sparse scene or missing near objects | Accumulation window, FOV edge, target reflectivity and reference-only 5–20 cm zone                                                 |
| Dust warning / streaks               | Inspect the optical window and remove loose particles before lens cleaning as documented                                           |

Preserve LVX/configuration/logs before recovery, close competing clients and restart after correcting the network/supply. Use only MID70 firmware and its release notes for a deliberate update; do not flash MID-360 family files. The body IP67 rating does not waterproof the converter or exposed cable branches. [Maintenance/troubleshooting/manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Storage, Transportation, and Maintenance <a href="#block-390d4c79856d803bb0bde9ad0a9710db" id="block-390d4c79856d803bb0bde9ad0a9710db"></a>

These procedures protect the MID-70 optical window, connectors and stored calibration state. Storage limits differ from shell operating limits, and a dirty optical window can cause dust warnings or sparse returns without any packet-format failure. Keep a pre-service capture and inspect the physical sensor before replacing decoder software.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Storage <a href="#block-390d4c79856d801287d2d9c932e65773" id="block-390d4c79856d801287d2d9c932e65773"></a>

The storage temperature range for the Mid-70 is from -20° to 65 °C (-4° to 149° F). Keep Mid-70 sensors in a dry and dust-free environment.

* Make sure Mid-70 sensors are not exposed to environments containing poisonous or corrosive gases or materials.
* DO NOT drop Mid-70 sensors and be careful when placing a LiDAR sensor in storage or taking it out of storage.
* If a Mid-70 sensor is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Transportation <a href="#block-390d4c79856d80169b0eceb18c5d591b" id="block-390d4c79856d80169b0eceb18c5d591b"></a>

Before transportation, place Mid-70 sensors in a suitable box for transportation and make sure it is secure. Make sure to place foam inside the transportation box and that the box is clean and dry.

DO NOT drop Mid-70 sensors and always be careful when carrying a LiDAR sensor.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Maintenance <a href="#block-390d4c79856d80ba83bbe37aa4d2bb9e" id="block-390d4c79856d80ba83bbe37aa4d2bb9e"></a>

In normal conditions, the only maintenance required for the Mid-70 is to clean the optical window of the LiDAR sensor. Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor. Make sure to regularly clean the optical window to prevent this from happening.

First, check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. Use compressed or canned air: DO NOT wipe a dusty optical window, as it will only cause more damage. Dust the optical window with compressed or canned air before wiping the optical window. Note that if the optical window has no visible stains afterward, it is not necessary to wipe also.
2. Wipe the stains: DO NOT wipe using a dry lens tissue, as it will scratch the surface of the optical window. Use the lens tissue provided with isopropyl alcohol. Wipe slowly to remove the dirt instead of redistributing it on the surface of the optical window. If the optical window is still dirty, a mild soap solution can be used to gently wash the window. Repeat Step 2 to remove any remaining soap residue.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Troubleshooting <a href="#block-390d4c79856d80b2a8b7c04d042c3ce5" id="block-390d4c79856d80b2a8b7c04d042c3ce5"></a>

The table below shows you how to troubleshoot and resolve common issues with Mid-70 sensors. If the issue persists, contact Livox.

| **Issue**                                                          | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Cannot detect the LiDAR sensor                                     | • Make sure that all cables are correctly wired. • Make sure the voltage and power supply is suitable. The voltage should be between 10 and 15 V. If a Livox Converter 2.0 is in use, the supported voltage range of the external power source is from 9 to 30 V. • Make sure that the LiDAR sensor is not connected to other software. • Make sure the LAN is selected. • Check whether host security software filters discovery broadcasts or the configured UDP stream. Use scoped Livox Viewer/application rules on the isolated sensor interface rather than disabling the firewall or removing security software. Confirm packet output with Wireshark. |
| Cannot connect to the detected LiDAR sensor/ Cannot start sampling | • Make sure that all cables are correctly wired. • Make sure the voltage and power supply is suitable. The voltage should be between 10 and 15 V. If a Livox Converter 2.0 is in use, the supported voltage range of the external power source is from 9 to 30 V. If the issue persists, reboot the LiDAR sensor and restart the software.                                                                                                                                                                                                                                                                                                                    |
| No data received                                                   | Confirm the packet outputs for all connected devices using another application (e.g., Wireshark).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

Keep troubleshooting scoped: correct power/state/network faults, close competing acquisition clients and read actual status before considering model-matched firmware recovery. No blanket host-firewall disable, calibration write or enclosure disassembly is required for first capture.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### After-Sales Information <a href="#block-390d4c79856d80388524df748aeea091" id="block-390d4c79856d80388524df748aeea091"></a>

For a MID-70 service case, preserve the serial, first-generation Viewer/SDK version, supply arrangement (bare sensor or Converter 2.0), working-state/status codes and a short LVX or packet capture. The [Livox service and warranty information](http://www.livoxtech.com/support) defines the applicable process; a sensor datasheet is not a system warranty. Do not disassemble the optical enclosure to investigate a dust or motor-status warning.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

## Downloads and technical documents

| Resource                                                                                                                                           | Exact scope                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| [MID-70 manual v1.2](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf) | 25-page source; pin mapping, converter boundaries, cold-start, states, dual returns, time and drawings |
| [MID-70 downloads](https://www.livoxtech.com/mid-70/downloads)                                                                                     | Viewer, firmware/release notes, CAD and point-cloud explanatory files                                  |
| [First-generation SDK](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/README.md)                             | Device Type 6 and C/C++samples                                                                         |
| [First-generation ROS driver](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/README.md)               | Documented ROS1 build/launch, LVX conversion and timing                                                |

The original M12/converter cross-table and separate LVTTL sync drawing were visually inspected. The manufacturer document/drawings are linked, and existing file-based figures remain below.

### Appendix <a href="#block-390d4c79856d809aacc5c987a519c77d" id="block-390d4c79856d809aacc5c987a519c77d"></a>

The original reference contains three different dimensioned assemblies. Appendix 1 describes the MID-70 body, Appendix 2 the optional mounting bracket and Appendix 3 Converter 2.0. The native/source drawings are retained at their respective topics; dimensions and thread sizes must stay with the correct assembly.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

### Appendix 1 <a href="#block-390d4c79856d803e95a1f77a280f22d8" id="block-390d4c79856d803e95a1f77a280f22d8"></a>

The MID-70 body envelope is **97 × 64 × 62.7 mm**, approximately **580 g**. Its bottom M3 mounting features are separate from the bracket's M6 and 1/4-inch attachment options. Use the retained toleranced sensor drawing for hole positions, engagement and optical clearance before fabricating a mount.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/813fb335-c84d-455b-bc1b-bd7443983da8/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Appendix 1" height="616.029210175956" width="724.8250122070312">

### Appendix 2 <a href="#block-390d4c79856d80dbb9fadd95d9ed028c" id="block-390d4c79856d80dbb9fadd95d9ed028c"></a>

The optional mounting bracket has a **100 × 97 × 5.7 mm** envelope and approximately **76 g** mass. It attaches to the sensor with M3 hardware; the bracket's M6 or central 1/4-inch installation features belong to the bracket itself. Select screws using the actual bracket thickness and sensor engagement limit.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1df0fb45-e2b4-426e-ba66-d482a3ecdb94/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Appendix 2" height="777.6780107671565" width="511.9875183105469">

### Appendix 3 <a href="#block-390d4c79856d8006b813c26f54ecbaa6" id="block-390d4c79856d8006b813c26f54ecbaa6"></a>

Converter 2.0 has a **74 × 52 × 23 mm** envelope and approximately **88 g** mass. Allow clearance for all four ports and cable strain relief. Its **9–30 V overview/appendix input range** differs from the **10–30 V power-cable table**; 12 V is the shared baseline, while the bare LiDAR remains limited to 10–15 V.

[Model-specific source](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf).

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19bed60c-a591-4372-bfbf-6c180360df85/image/w=1920,quality=90,fit=scale-down" alt="Retained manufacturer illustration from Appendix 3" height="264.03611555783556" width="724.8250122070312">

## References and validation

Reviewed **24 November 2026**: exact MID-70 store package, official v1.2 manual/specifications/downloads and actual SDK1/ROS1 sources. Supply/peak discrepancies are preserved with a 12 V commissioning baseline instead of applying a converter rating to the sensor.

**SDK/ROS compilation, Viewer execution, firmware upgrade,10-second monitor execution, power/sync measurements and physical point-cloud tests: not run.** The monitor is original; syntax checks do not establish interpreter or hardware availability.

* [MID-70 official User Manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Mid-70/new/Livox%20Mid-70%20User%20Manual_EN_v1.2.pdf) — v1.2,2021.02; 25 pages read.
* [MID-70 official specification conditions](https://www.livoxtech.com/mid-70/specs) — current 24 Nov 2026.
* [MID-70 Viewer/firmware/CAD inventory](https://www.livoxtech.com/mid-70/downloads) — current 24 Nov 2026.
* [First-generation Livox SDK build and samples](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/README.md) — commit 9306596a2bf15c1343bc023b497465ed0a32909d.
* [MID-70 device Type 6 and data fields](https://github.com/Livox-SDK/Livox-SDK/blob/9306596a2bf15c1343bc023b497465ed0a32909d/sdk_core/include/livox_def.h) — commit 9306596a2bf15c1343bc023b497465ed0a32909d.
* [First-generation Livox ROS driver documented targets](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/README.md) — commit 3d240d5666129e1a3052e78ee8487a04b08fdda3.
* [ROS1 broadcast selector/PointCloud2 launch](https://github.com/Livox-SDK/livox_ros_driver/blob/3d240d5666129e1a3052e78ee8487a04b08fdda3/livox_ros_driver/launch/livox_lidar_rviz.launch) — commit 3d240d5666129e1a3052e78ee8487a04b08fdda3.
* [Exact MID-70 sensor/splitter package](https://openelab.io/products/livox-mid-70-compact-lidar3d) — 23 Nov catalog; public page read 24 Nov 2026.

### Additional established references

* [www.livoxtech.com/mid-70](http://www.livoxtech.com/mid-70)
* [www.livoxtech.com](http://www.livoxtech.com/)
* [http://www.livoxtech.com/sdk](http://www.livoxtech.com/sdk)
* [www.livoxtech.com/support](http://www.livoxtech.com/support)
