# LIVOX Mid Series User Manual

> **LIVOX Mid Series User Manual**

{% embed url="https://openelab.io/products/livox-mid-40-lidar-compact" %}

## **Product profile** <a href="#block-389529777f354265a92fb280e7b73e75" id="block-389529777f354265a92fb280e7b73e75"></a>

### **Introduction** <a href="#block-dd67c9ee98d94ffcacd51f7155235b99" id="block-dd67c9ee98d94ffcacd51f7155235b99"></a>

The Livox Mid-40 and the Livox Mid-100 are high-performance LiDAR sensors that can be used for multiple applications including autonomous driving, robot navigation, dynamic path planning, and high-precision mapping.

Both the Livox Mid-40 and Livox Mid-100 have a detection range of up to 260 meters.

**Non-repetitive Scanning Technology:** The unique non-repetitive scanning technology owned by Livox ensures a high-density point cloud, and can precisely detect every detail inside the field of view (FOV).

**High Reliability:** The Livox Mid series has undergone high-temperature endurance tests, salt spray tests, and other rigorous reliability testing required by the automotive industry. In addition, the Livox Mid series has achieved an IP67 waterproof and dustproof rating under GB 4208-2008 and IEC 60529 standards.

**Environmental Adaptation:** The Livox Mid series maintains a consistent performance in a wide range of lighting conditions, from 100 kilolux to darker, low-visibility environments. Thanks to the innovative de-noising algorithms built into the unit, the Livox Mid series is able to effectively reduce the noise caused by atmospheric particles such as rain, fog, and dust, as well as interference from other LiDAR sensors.

**User-friendly Livox Viewer:** Livox Viewer is a Windows software specially designed for Livox LiDAR sensors. It displays real-time point clouds, and the simple interface makes it easy to use.

**Livox SDK:** A software development kit (SDK) is provided to help develop customizable applications using the data acquired from point clouds.

💡

**Note:**

* 260 m can be reached when the target object reflects 80% or more of light (e.g., grey concrete walls and roads have a reflectivity range from 15% to 30%, while white plaster walls have a reflectivity range from 90% to 99%) in an environment with a temperature of 77° F (25° C).
* The Livox Mid-40 and the Mid-100 have basically the same functionalities. The only difference between the Livox Mid-40 and Livox Mid-100 is that the Livox Mid-100 is a three-in-one version of the Livox Mid-40. The general descriptions in the user manual apply to both the Livox Mid-40 and Livox Mid-100.
* Remove the protective file on the optical window before first use.

### **Product Characteristics** <a href="#block-a258c14dedae4edd9c6499dfaa12d328" id="block-a258c14dedae4edd9c6499dfaa12d328"></a>

The Livox Mid-40 and Livox Mid-100 have a high coverage ratio due to their unique non-repetitive scanning technology. Over time, the coverage inside the FOV increases significantly and reveals more detailed information of the surroundings.

Figures 1.2.1 and 1.2.2 display the typical point cloud patterns of the Livox Mid-40 and Livox-100 over an extended period. The point cloud pattern of the Livox Mid-100 is composed of the point cloud patterns of three Livox Mid-40 LiDAR sensors.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c97f6acb-e246-4a56-b9b5-808b47ba4067/image/w=1920,quality=90,fit=scale-down" alt="image" height="158.18143764398036" width="634.352294921875">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/36b4ebca-b8b5-4b46-8cd7-18a34be2c001/image/w=1920,quality=90,fit=scale-down" alt="image" height="281.64640591966173" width="634.375">

Figure 1.2.3 displays the FOV coverage of Livox LiDAR sensors compared with other non-Livox LiDAR sensors that use common mechanical scanning methods. The diagram shows that when the integration time is less than 0.1 seconds, the FOV coverage of the Livox Mid-40 is similar to the 32-line LiDAR sensor. As the integration time increases, however, the FOV coverage of the Livox Mid-40 increases significantly while the 32-line LiDAR sensor remains the same. After 0.5 seconds, the FOV coverage of the Livox Mid-40 is the same as the 64-line LiDAR sensor. After 1.4 seconds, the FOV coverage would approach 100%, so almost all areas would be illuminated by laser beams. In this way, more details in the FOV can be revealed.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6008b178-ff62-40ec-93c9-1d0ed8604dad/image/w=1920,quality=90,fit=scale-down" alt="image" height="318.1176686217009" width="634.375">

💡

The performance of the scanning method is defined by the FOV coverage, which is calculated as the fraction of FOV illuminated by laser beams. The FOV coverage © can be calculated with the following formula:

C=TotalareailluminatedbylaserbeamsTotalareainFOV∗100%C=TotalareainFOVTotalareailluminatedbylaserbeams​∗100%

Refer to the official Livox website for more information about how the FOV coverage is calculated.

| **Laser Wavelength**         | **905 nm**                                                                          |
| ---------------------------- | ----------------------------------------------------------------------------------- |
| Laser Safety                 | Class 1 (IEC 60825-1:2014) eye safe                                                 |
| Detection Range (@100 klx)   | 90 m @ 10% reflectivity 130 m @ 20% reflectivity 260 m @ 80% reflectivity           |
| FOV                          | Livox Mid-40: 38.4° (circular) Livox Mid-100: 98.4° (Horizontal) × 38.4° (Vertical) |
| Range Precision (1σ @ 20 m)  | 2 cm                                                                                |
| Angular Accuracy             | < 0.1°                                                                              |
| Beam Divergence              | 0.28° (Vertical) × 0.03° (Horizontal)                                               |
| Point Rate                   | Livox Mid-40: 100,000 points/s Livox Mid-100: 300,000 points/s                      |
| False Alarm Ratio (@100 klx) | < 0.01%                                                                             |

Table 1.2.1 Point cloud specifications

💡

**Note:**

* The Livox Mid series cannot detect objects which are less than 1 m away. Contact Livox if you require LiDAR sensors that can detect objects within a range of 1 m.
* The range precision was tested in an environment at a temperature of 77° F (25° C) with a target object that had a reflectivity of 80% and was 20 m away from the Livox Mid series LiDAR sensors. The actual environment may differ from the testing environment. The figure listed is for reference only.

### **Overview** <a href="#block-48bc0d5fcb1e4581944659d5f4c705a6" id="block-48bc0d5fcb1e4581944659d5f4c705a6"></a>

**Livox Mid-40**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/98be4ec3-0984-4561-a997-26e612cf0c70/image/w=1920,quality=90,fit=scale-down" alt="image" height="458.1515231662326" width="634.3636474609375">

1. **Optical Window**
2. The laser passes through the optical window and scans objects in the FOV.
3. **Fan (Air Inlet)**
4. Only dissipates heat when the temperature of the LiDAR sensor is high. Make sure there are at least 10 millimeters between the fan (air inlet) and the nearest objects.
5. **Mounting Holes**
6. M3 mounting holes. Make sure to use the correct screws when mounting.
7. **LiDAR Connector**
8. Connects to the Livox Converter. The LiDAR Connector can be customized. Refer to the Cables section for more information.
9. **Air Outlet**
10. Dissipates heat. Make sure there are at least 10 millimeters between the air outlet and the nearest objects.

**Livox Mid-100**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ddfa2c9e-d9fd-4ee1-9124-9252d047187b/image/w=1920,quality=90,fit=scale-down" alt="image" height="186.9748791024154" width="634.32958984375">

1. **LiDAR Connector**
2. Connects to the Livox Converter. The LiDAR Connector can be customized. Refer to the Cables section for more information.
3. **Fan (Air Inlet)**
4. Only dissipates heat when the temperature of the LiDAR sensor is high. Make sure there are at least 10 millimeters between the fan (air inlet) and the nearest objects.
5. **M3 Mounting Holes**
6. M3 mounting holes. Make sure to use the correct screws when mounting.
7. **¼ Inch Mounting Hole**
8. Can be mounted on a tripod or other bases outfitted with a ¼ inch screw.
9. **Air Outlet**
10. Dissipates heat. Make sure there are at least 10 millimeters between the air outlet and the nearest objects.
11. **Optical Window**
12. The laser passes through the optical window and scans objects in the FOV.

**Livox Converter**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f6329ff7-8b5b-49e4-9a2c-0ff353ec3fd2/image/w=1920,quality=90,fit=scale-down" alt="image" height="188.95262113530583" width="634.3409423828125">

1. **LiDAR Connector Port**
2. A JAE MX34012NF1 type connector port used to connect to Livox Mid series LiDAR sensors.
3. Only compatible with JAE MX34012SF1 type LiDAR connectors.
4. **Power Port**
5. A MOLEX 105313-1102 type power port used to connect to an external power supply. Only compatible with MOLEX 105307-1202 (LiDAR) connectors.
6. **Ethernet Port**
7. An RJ45 type Ethernet connector used to connect to Ethernet cables.
8. **Sync Port**
9. A JST SM03B-GHS-TB type sync port used to connect to sync cables. Only compatible with JST GHR-03V-S type connectors.

## **Connectors** <a href="#block-ba26dbe0af79437b93c646d2de0cbff6" id="block-ba26dbe0af79437b93c646d2de0cbff6"></a>

### **LiDAR Connector** <a href="#block-2f621f01414e41fa81d672742665593a" id="block-2f621f01414e41fa81d672742665593a"></a>

Below is more information on the LiDAR connector and extensible power cables connector. Users can customize the connectors based on their needs for power supply, data transmission, and data synchronization.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/05fd071c-298d-43c3-ac8e-f051db95a93b/image/w=1920,quality=90,fit=scale-down" alt="image" height="176.20266384548611" width="634.32958984375">

| **Pin** | **Signal**    | **Type** | **Description**            |
| ------- | ------------- | -------- | -------------------------- |
| 1       | Power+        | Power    | DC 10-16 V (max 16 V)      |
| 2       | Ground        | Power    | Ground                     |
| 3       | Ethernet\_TX+ | Output   | 100BASE-TX, TX+            |
| 4       | Ethernet\_TX- | Output   | 100BASE-TX, TX-            |
| 5       | Ground        | Power    | Ground                     |
| 6       | Sync+         | Input    | RS485\_A, Pulse Per Second |
| 7       | Power+        | Power    | DC 10-16 V (max 16 V)      |
| 8       | Ground        | Power    | Ground                     |
| 9       | Ethernet\_RX+ | Input    | 100BASE-TX, RX+            |
| 10      | Ethernet\_RX- | Input    | 100BASE-TX, RX-            |
| 11      | Ground        | Power    | Ground                     |
| 12      | Sync-         | Input    | RS485\_B, Pulse Per Second |

Table 2.1.1 LiDAR and Extensible Cable Connector Description

**SYNC signal description**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/52ece874-ed87-405d-bc71-1e61f68437bd/image/w=1920,quality=90,fit=scale-down" alt="image" height="203.23544755954188" width="634.3409423828125">

Refer to the Software Development Kit (SDK) section for more information about the sync signal.

### **Power Cable and Sync Cable** <a href="#block-4b52b9e9716f419eaf7b4349ffdf9691" id="block-4b52b9e9716f419eaf7b4349ffdf9691"></a>

The Livox Mid series cables package includes a power cable and sync cable.

#### **Power Cable** <a href="#block-006230f0756f4e5790aa60e1b93625e3" id="block-006230f0756f4e5790aa60e1b93625e3"></a>

Connect “A” to the power port of the Livox Converter and connect “B” to an external DC power supply.

The connector type of this power cable is MOLEX105307-1202.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/701663c9-f0da-47fd-8c39-2e755182b856/image/w=1920,quality=90,fit=scale-down" alt="image" height="129.28229192228017" width="634.3636474609375">

| **Pin** | **Signal** | **Type** | **Description**       | **Color** |
| ------- | ---------- | -------- | --------------------- | --------- |
| 1       | Power+     | Power    | DC 10-16 V (max 16 V) | Red       |
| 2       | Ground     | Power    | Ground                | Black     |

Table 2.2.1 Power cable description

**Sync cable**

Connect “A” into the sync port of the Livox Converter and connect “B” to the sync signal. The connector type of this sync cable is GHR-03V-S. Refer to the Data Synchronization section for more information.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/64ed1dd4-cf3e-4e16-9b36-f5593229f193/image/w=1920,quality=90,fit=scale-down" alt="image" height="130.61303781244376" width="634.3409423828125">

| **Pin** | **Signal** | **Type** | **Description**            | **Color** |
| ------- | ---------- | -------- | -------------------------- | --------- |
| 1       | Ground     | Power    | Ground                     | Black     |
| 2       | Sync+      | Input    | RS485\_A, Pulse Per Second | Blue      |
| 3       | Sync-      | Input    | RS485\_B, Pulse Per Second | White     |

Table 2.2.2 Sync cable description

### **Ethernet Port** <a href="#block-18ec2546b8e04d2b8bf7ab1654871edb" id="block-18ec2546b8e04d2b8bf7ab1654871edb"></a>

The Livox Mid series LiDAR connector can be converted to an RJ45 Ethernet type port by using the Livox Converter. The Livox Mid series supports 100BASE-TX and uses two twisted pairs to send and receive data.

## **Mounting the Livox Mid Series** <a href="#block-5bcb12535c374058911a9e9bf344dfcf" id="block-5bcb12535c374058911a9e9bf344dfcf"></a>

### **Effective Field of View (FOV) Range** <a href="#block-de5e4db04e3644e3bad11f1db2dd50a9" id="block-de5e4db04e3644e3bad11f1db2dd50a9"></a>

The circular FOV of the Livox Mid-40 is 38.4°. The Livox Mid-100 is a three-in-one version of the Livox Mid-40. To ensure the performance of the Livox Mid-100, the FOV ranges of the three LiDAR sensors are overlapped. Consequently, the actual FOV of the Livox Mid-100 is 98.4°. When mounting a Livox Mid Series LiDAR sensor, make sure that the FOV is not blocked by any objects.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8bdfdf73-fb3b-402b-9a52-7f7739fd7739/image/w=1920,quality=90,fit=scale-down" alt="image" height="298.09466019417476" width="634.375">

### **Dimensions** <a href="#block-0663c474106f415dadfa78f616354c6e" id="block-0663c474106f415dadfa78f616354c6e"></a>

#### **Livox Mid-40 Dimensions** <a href="#block-ef57d8a5567e4896a3db0bc4cb860025" id="block-ef57d8a5567e4896a3db0bc4cb860025"></a>

Refer to the dimensions and the mounting holes in the figures below to mount or embed the Livox Mid-40 to or in an appropriate place on the target base. When the base is outfitted with ¼ inch mounting holes, it is recommended to first attach the Livox Mid-40 to the mounting bracket and then mount the Livox Mid-40 using the ¼ inch mounting hole on the mounting bracket. There are several M3 screw holes available on the sides of the mounting bracket to help mount the Livox Mid-40 based on the requirements.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5cc12ac4-8970-4fe2-b97a-d37de3a6e203/image/w=1920,quality=90,fit=scale-down" alt="image" height="221.42885289293653" width="634.3409423828125">

| **Weight (with cable)** | **760 g**       |
| ----------------------- | --------------- |
| Dimensions              | 88 × 76 × 69 mm |

Table 3-2-1 Livox Mid-40 Weight & Dimensions

**Livox Mid-40 Mounting Bracket**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4a70eb47-c393-4841-9f31-a503ebd9463e/image/w=1920,quality=90,fit=scale-down" alt="image" height="277.53409576416016" width="634.3636474609375">

| **Weight** | **101 g**       |
| ---------- | --------------- |
| Dimensions | 88 × 69 × 18 mm |

Table 3-2-2 Livox Mid-40 Mounting Bracket Weight & Dimensions

#### **Livox Mid-100 Dimensions** <a href="#block-fd5c7fdd65524e82aa3a4353881cc517" id="block-fd5c7fdd65524e82aa3a4353881cc517"></a>

The Livox Mid-100 is outfitted with four M3 mounting holes on the bottom, and can be mounted using the M3 screws. Additionally, a 1/4 inch mounting hole is also available on the center of the bottom. When mounting the Livox Mid-40 to a tripod or other target base outfitted with 1/4 inch mounting holes, users can use this hole. Refer to the dimensions and the mounting holes in the figures below to mount or embed the Livox Mid-100 to or in an appropriate place on the target base.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4bfdb1fd-9729-4d1a-9357-c9a9eb024238/image/w=1920,quality=90,fit=scale-down" alt="image" height="210.73775407176905" width="634.3636474609375">

| **Weight (with cable)** | **2200 g**        |
| ----------------------- | ----------------- |
| Dimensions              | 142 × 70 × 230 mm |

Table 3.2.3 Livox Mid-100 Weight & Dimensions

#### **Livox Converter** <a href="#block-4b7158a803cb40d8851dd4bfccf81e66" id="block-4b7158a803cb40d8851dd4bfccf81e66"></a>

Refer to the dimensions below to mount the Livox Converter.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/aff8c0de-abd7-4a53-966a-ffa9261e99e5/image/w=1920,quality=90,fit=scale-down" alt="image" height="179.40634864267676" width="634.32958984375">

| **Weight Dimensions** | **66 g**        |
| --------------------- | --------------- |
| Dimensions            | 52 × 58 × 25 mm |

Table 3.2.4 Livox Converter Weight & Dimensions

## **Getting Started** <a href="#block-101b453eb84f475c86f3d5eb269d5c12" id="block-101b453eb84f475c86f3d5eb269d5c12"></a>

### **External Power Supply** <a href="#block-2d01f74a2df84578b91fbd27821be263" id="block-2d01f74a2df84578b91fbd27821be263"></a>

The working voltage of the Livox Mid series is 10 V to 16 V. The working power of the Livox Mid-40 is 10 W, while the Livox Mid-100 is 30 W. After powering on, the Livox Mid series LiDAR sensors may reach peak power, which may last for short periods. The lower the temperature, the higher the peak power will be.

When powering on the Livox Mid-40 in an environment temperature of 4° F (-20° C), within the first 20 seconds the peak power can reach 40 W. When powering on the Livox Mid-100 in the same environment temperature, it may take 40 seconds to power on the three Livox Mid-40 LiDAR sensors, and the peak power can reach 67 W.

Make sure the power supply is suitable based on the peak power of the Livox Mid series LiDAR sensor. Refer to the figures below to see the relationship between the peak power and the environment temperature of the Livox Mid series. The value is for reference only. In normal conditions, the peak power is lower than in the figures below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f33c5e63-bda5-4d70-b105-32075aa02663/image/w=1920,quality=90,fit=scale-down" alt="image" height="294.3260746675379" width="634.3636474609375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19b4015e-a93a-4f62-9fb3-9fa961697e95/image/w=1920,quality=90,fit=scale-down" alt="image" height="326.8609153223402" width="634.352294921875">

💡

**Note:**

* The working temperature range for the Livox Mid series is from -4° to 149° F (-20° to 65° C). DO NOT use this product outside of that range.
* In real situations, the power voltage may fluctuate due to the influence of the working environment. Make sure that the power voltage is always within the range between 10 to 16 V even with the fluctuations.

### **Connection** <a href="#block-9e30cb267a2d4b2195b677c467f92a69" id="block-9e30cb267a2d4b2195b677c467f92a69"></a>

The Livox Mid series uses a compact and reliable electrical connector for power supply as well as control signal and data transmission. Refer to the Cables section for more information about the connector. The Livox Converter integrates a LiDAR port, a sync port, a power port, and an Ethernet port. To ensure optimal performance, it is recommended to always use a Livox Converter.

The Livox Mid series uses an Ethernet cable for data transmission and supports user datagram protocol (UDP). Both static and dynamic IP address configurations are supported and the addresses are assigned by default to the Livox Mid series LiDAR sensor using dynamic host configuration protocol (DHCP). The static and dynamic IP addresses are connected in different ways. The dynamic IP address is connected by default using a router with DHCP. To connect to the static IP address, make sure the Livox Mid series LiDAR is switched to static IP mode by using Livox Viewer or the SDK. The connections are the same for the Livox Mid-40 and Livox Mid-100.

The Livox Mid-40 is used in the example below.

#### **Dynamic IP address:** <a href="#block-38341628387e4a8bb363aca48b61efce" id="block-38341628387e4a8bb363aca48b61efce"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/58eec126-376b-4e96-87a4-c078ee2ab8ab/01534880-c5a9-4967-90ed-4b76c2c9e6f6/w=1920,quality=90,fit=scale-down" alt="image" height="203.8836545461259" width="634.352294921875">

1. Connect the Livox Mid-40 to the Livox Converter.
2. Connect the computer and the Livox Converter to the router using Ethernet cables. Make sure both the Livox Converter and the computer are connected to the LAN port on the router.
3. Connect the Livox Converter to an external power source.
4. Connect one end of the sync cable to the sync port and the other end to the designated sync signal. Note that the sync cable may not always be required.

💡

**Note:**

* When connecting multiple Livox Mid-40 LiDAR sensors, connect them to one router, and then connect the router to a computer.

#### **Static IP address:** <a href="#block-efbe2d741ce84041b915c78c91ac78f1" id="block-efbe2d741ce84041b915c78c91ac78f1"></a>

1. Connect the Livox Mid-40, Livox Converter, router, external power source, and computer by following Figure 4.2.1.
2. Run Livox Viewer, click 📂, and set the IP address of the Livox Mid-40 to static IP address. Note that the static IP address of a Livox Mid-40 should be 192.168.1.X. The X is related to the broadcast number of the LiDAR sensor. If the broadcast number ends with 1, X can be set to any number between 11 to 80. If the broadcast number ends with 2, X can be set to any number between 81 to 150. If the broadcast number ends with 3, X can be set to any number between 151 to 220.
3. Disconnect the Livox Mid-40, Livox Converter, router, external power source, and computer.
4. Set the IP address of your computer to static IP address. Note that the static IP address of your computer should be 192.168.1.X. X can be set to any number between 2 to 233 and should be different from the IP address of the Livox Mid series LiDAR sensor set in Step 2.
5.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8828f4aa-d8e9-4c8a-b2a1-3230833dfbbe/image/w=1920,quality=90,fit=scale-down" alt="image" height="164.2037383603378" width="596.3409423828125">
6. Connect the Livox Mid-40 to the Livox Converter.
7. Connect the Livox Converter to your computer using an Ethernet cable.
8. Connect the Livox Converter to an external power source.
9. 💡
10. **Note:**
11. Make sure to set the IP address of the Livox Mid series LiDAR sensor back to dynamic IP address if it has been set to static IP address to use a router for connection. Also make sure to set your computer to dynamic IP address, and follow the instructions in the Dynamic IP address section.
12. If multiple Livox Mid-40 LiDAR sensors are set to static IP addresses, make sure all the Livox Mid-40 LiDAR sensors have different IP addresses and use a switchboard to connect them to the computer.
13. A Livox Mid-100 is equal to three Livox Mid-40 LiDAR sensors. Therefore, you should set three different static IP addresses to one Livox Mid-100.
14. If more than 6 Livox Mid-40 LiDAR sensors are required, use a kilo mega switchboard or a kilo mega router.
15. The broadcast number for each LiDAR sensor can be viewed in the Device Manager of Livox Viewer or the SDK. For the Livox Mid-40, the broadcast number will be its serial number ending in an additional “1”. For the Livox Mid-100, the broadcast numbers of the three Livox Mid-40 LiDAR sensors will be the serial number ending in an additional “1”, “2”, or “3”.
16. In static IP address mode, the router is required only when you set the IP address of the LiDAR sensors.

## **Usage** <a href="#block-b64080b1cd30454aaa9b3be81c8151db" id="block-b64080b1cd30454aaa9b3be81c8151db"></a>

### **Coordinates** <a href="#block-7ba28554c9954943ad6e941f37b1cb47" id="block-7ba28554c9954943ad6e941f37b1cb47"></a>

Users can view the real-time point cloud data by using Livox Viewer and develop customizable applications using the Software Development Kit (SDK). Before learning about how to use Livox Viewer and the SDK, see the Cartesian and Spherical coordinates of the Livox Mid-40 and Livox Mid-100 below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/36139b56-aa54-44a4-9697-9a761af0244e/image/w=1920,quality=90,fit=scale-down" alt="image" height="245.1929083208666" width="634.352294921875">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8c56f254-5fef-43e2-9b7d-f3db6890940b/image/w=1920,quality=90,fit=scale-down" alt="image" height="225.15721915920057" width="634.375">

### **Output Data** <a href="#block-34ae9840745a48e0803662aaa52d81f9" id="block-34ae9840745a48e0803662aaa52d81f9"></a>

The output information of Livox Mid series LiDAR sensors includes point cloud data, timestamp, and status codes.

#### **Point Cloud Data** <a href="#block-d8119d72fc2542dbb09548dee20db6c8" id="block-d8119d72fc2542dbb09548dee20db6c8"></a>

A point cloud is the collection of the points where the surface of an object was detected in the FOV of the LiDAR sensor. Each point contains the following information.

* Target reflectivity: 0 to 255. 0 to 150 corresponds to the reflectivity within the range of 0 to 100% in the Lambertian reflection model. 151 to 255 corresponds to the reflectivity of target objects with retroreflection properties.
* Coordinates: Can be expressed as Cartesian coordinates (x, y, z) and Spherical coordinates (r, θ, φ). The relationship between Cartesian and Spherical coordinates is shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1bf777af-2c7e-4009-abd3-dcd0136e2032/image/w=1920,quality=90,fit=scale-down" alt="image" height="248.675" width="634.375">

#### **Timestamp** <a href="#block-5330bf1642dc4642a044d5b74876903d" id="block-5330bf1642dc4642a044d5b74876903d"></a>

There are two ways to synchronize data with the Livox Mid series: IEEE 1588-2008 and Pulse Per Second (PPS).

IEEE 1588-2008: IEEE 1588-2008 is the Precision Time Protocol (PTP) enabling precise synchronization of clocks in measurement and control systems by Ethernet. Livox LiDAR sensors, as the ordinary clock in the PTP, only supports UDP/IPV4 for PTP. Livox LiDAR sensors support the following message events: Sync, Flow\_up, Delay\_req, Delay\_resp.

PPS: PPS uses the sync cable for data synchronization. Refer to the Cables section for more information. The synchronization logic is shown in the figure below. The pulse interval in PPS is 1 s (t0 = 1 s) while the continuous time of high-level voltage is from 1 ms to 300 ms (1 ms < t1 < 300 ms). The rising edge of PPS will reset the timestamp to zero. So the timestamp of the point cloud data indicates the duration between the point cloud sampling and the PPS rising edge.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d53627db-fb41-4397-aed4-384571531b94/image/w=1920,quality=90,fit=scale-down" alt="image" height="187.83967391304347" width="634.375">

#### **Status Codes** <a href="#block-3d6f78e77dd647e6835d2c29a428538b" id="block-3d6f78e77dd647e6835d2c29a428538b"></a>

The status codes display the current working status of the Livox Mid series LiDAR sensors. By checking the status codes, users can see the temperature status, voltage status, motor status, dust warning, service life warning, and PPS signal status. Status codes can be viewed in Livox Viewer or in the SDK. Refer to the Livox Viewer section for more information about how to check status codes.

| **Status**           | **Description**                                                                                                                                                                                     |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Temperature status   | Indicates if there is any temperature abnormality. Temperature status includes: normal, warning, and error.                                                                                         |
| Voltage status       | Indicates if there is any internal voltage abnormality. Voltage status includes: normal, warning, and error.                                                                                        |
| Motor status         | Indicates if there is any internal motor abnormality. Motor status includes: normal, warning, and error.                                                                                            |
| Dust warning         | Indicates if a significant amount of dust is detected on the optical window, if the optical window is covered by objects, or if there is an object less than 0.3 meters away from the LiDAR sensor. |
| Service life warning | Indicates if the LiDAR sensor is nearing the end of its service life.                                                                                                                               |
| PPS signal status    | Indicates whether the PPS sync signal is working normally.                                                                                                                                          |

### **Working States & Working Modes** <a href="#block-29eed49035f34c09bccea4c02ce5cffe" id="block-29eed49035f34c09bccea4c02ce5cffe"></a>

The working states of the Livox Mid series includes initializing, normal, standby, power saving, and error.

| **Working states** | **Description**                                                                                                                                |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Initializing       | The LiDAR sensor is powering on.                                                                                                               |
| Normal             | The LiDAR sensor is powered on and working normally.                                                                                           |
| Standby            | The LiDAR sensor is powered on, but the laser beams are not active.                                                                            |
| Power saving       | All components are powered off apart from the communication module.                                                                            |
| Error              | The LiDAR sensor will enter error status when an error is detected and all the components are powered off apart from the communication module. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/181316ff-11a1-49b9-a1f1-53859df2d448/image/w=1920,quality=90,fit=scale-down" alt="image" height="335.08724926364033" width="634.3636474609375">

The Livox Mid series also has three working modes: Normal, Standby, and Power Saving. These modes can be set in Livox Viewer and SDK.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/768888d4-2feb-4624-b2d5-4bef7ab005e8/image/w=1920,quality=90,fit=scale-down" alt="image" height="232.75629496402877" width="634.375">

### **Rain/Fog Suppression** <a href="#block-f8f131809fe640ba9f068c2c3f0f949b" id="block-f8f131809fe640ba9f068c2c3f0f949b"></a>

When the Livox Mid series is used in adverse weather conditions, it may detect atmospheric particles such as rain, fog, or dust. Rain/Fog Suppression decreases the false detection rate of atmospheric particles in adverse weather conditions.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cc3011bd-4a43-4827-808c-e26b68e4c037/image/w=1920,quality=90,fit=scale-down" alt="image" height="261.28407563042845" width="634.352294921875">

Note that Rain/Fog Suppression only limits the false detection rate of rain, fog, and dust. Additionally, Rain/Fog Suppression may also decrease the Livox Mid series ability to detect some surfaces with low reflectivity, such as glass or power cables. Only enable Rain/Fog Suppression when absolutely required. Rain/Fog Suppression can be enabled in the SDK. Refer to the Livox SDK Communication Protocol for more information.

## **Storage, Transportation, and Maintenance** <a href="#block-c42fee5a45b346a7b8d8414029db1323" id="block-c42fee5a45b346a7b8d8414029db1323"></a>

### **Storage** <a href="#block-22b7ea09840b4af18f9284a353eb8b95" id="block-22b7ea09840b4af18f9284a353eb8b95"></a>

The storage temperature range for the Livox Mid series is from -40° to 185° F (-40° to 85° C). Keep Livox Mid series LiDAR sensors in a dry and dust-free environment.

Make sure Livox Mid series LiDAR sensors are not exposed to environments containing poisonous or corrosive gases or materials.

DO NOT drop Livox Mid Series LiDAR sensors and always be careful when placing a LiDAR sensor in storage or taking it out of storage.

If a Livox Mid series LiDAR sensor is not to be used for more than three months, regularly check the sensors and connectors for abnormalities.

### **Transportation** <a href="#block-1f486238c18e4ac2b4122fd1f9a839bf" id="block-1f486238c18e4ac2b4122fd1f9a839bf"></a>

Before transportation, place Livox Mid series LiDAR sensors in a suitable box for transportation and make sure it is secure.

Make sure to place foam inside the transportation box and that the box is clean and dry.

DO NOT drop Livox Mid series LiDAR sensors and always be careful when carrying a LiDAR sensor.

### **Maintenance** <a href="#block-d8112bd9a6f94a57be9c2f2d65f55de4" id="block-d8112bd9a6f94a57be9c2f2d65f55de4"></a>

In normal conditions, the only maintenance required for the Livox Mid series is to clean the LiDAR sensor’s optical window. Dust and stains on the optical window can negatively affect the performance of the LiDAR sensor. Make sure to regularly clean the optical window to prevent this from happening.

First, check the surface of the optical window to see if cleaning is necessary. If it is necessary to clean, follow the steps below:

1. Use compressed or canned air: DO NOT wipe a dusty optical window, as it will only cause more damage. Dust the optical window with compressed or canned air before wiping the optical window. If the optical window has no visible stains afterward, it is not necessary to wipe it also.
2. Wipe the stains: DO NOT wipe using a dry lens tissue, as it will scratch the surface of the optical window. Use the lens tissue provided with isopropyl alcohol. Wipe slowly to remove the dirt instead of redistributing it on the surface of the optical window.

If the optical window is still dirty, a mild soap solution can be used to gently wash the window. Repeat Step 2 to remove any remaining soap residue.

## **Troubleshooting** <a href="#block-e155700eeb5e4c0797a83f70f529d200" id="block-e155700eeb5e4c0797a83f70f529d200"></a>

The table below shows you how to troubleshoot and resolve common issues with Livox Mid series LiDAR sensors. If the issue persists, please contact Livox.

| **Issue**                                                          | **Resolution**                                                                                                                           |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Cannot detect the LiDAR sensor                                     | Make sure that all cables are correctly wired.                                                                                           |
|                                                                    | Make sure the voltage and power supply is suitable. The voltage should be between 10 and 16 V and the power supply should be above 60 W. |
|                                                                    | Make sure that the LiDAR sensor is not connected to other software.                                                                      |
|                                                                    | Make sure LAN is selected.                                                                                                               |
|                                                                    | Make sure no security software installed that would block Ethernet broadcasts.                                                           |
|                                                                    | If the issues persists, try to turn off all firewalls and search again.                                                                  |
|                                                                    | Make sure the packet output of all connected devices using another application (e.g., Wireshark).                                        |
| Cannot connect to the detected LiDAR sensor/ Cannot start sampling | Make sure that the power and Ethernet cables are correctly connected.                                                                    |
|                                                                    | Make sure the voltage and power supply is suitable. The voltage should be between 10 and 16 V and the power supply should be above 60 W. |
|                                                                    | If the issue persists, reboot the LiDAR sensor and restart the software.                                                                 |
| No data received                                                   | Make sure the packet output of all connected devices using another application (e.g., Wireshark).                                        |

## **Appendix** <a href="#block-52686105304a4e0787a0eefca56e269b" id="block-52686105304a4e0787a0eefca56e269b"></a>

### **Appendix 1** <a href="#block-f5bd71fc80ad4c1895c2eacc270a6d04" id="block-f5bd71fc80ad4c1895c2eacc270a6d04"></a>

Livox Mid-40 Dimensions (unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/90e3e353-23ef-4b12-bb10-9e48a7f0f075/image/w=1920,quality=90,fit=scale-down" alt="image" height="311.21222527472526" width="634.375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/98a84c13-8c0e-4db9-875f-be3d6468271c/image/w=1920,quality=90,fit=scale-down" alt="image" height="312.03275047508447" width="634.352294921875">

### **Appendix 2** <a href="#block-27aaa0a2eed24813a59211fa0fd0b29e" id="block-27aaa0a2eed24813a59211fa0fd0b29e"></a>

Livox Mid-40 Mounting Bracket Dimensions (unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c8dacd2f-2e1a-456c-8997-3730813d0850/image/w=1920,quality=90,fit=scale-down" alt="image" height="319.30648666454846" width="634.3636474609375">

### **Appendix 3** <a href="#block-eefeb8adfe004f909b0461225b99213a" id="block-eefeb8adfe004f909b0461225b99213a"></a>

Livox Mid-100 Dimensions (unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/deada2a0-c67c-4054-b1d2-b65a5e2d94eb/image/w=1920,quality=90,fit=scale-down" alt="image" height="247.90779341774427" width="634.352294921875">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2ebe66bd-8cb2-4e2a-af76-cf3e67d0a3d9/image/w=1920,quality=90,fit=scale-down" alt="image" height="287.40788755458516" width="634.375">

### **Appendix 4** <a href="#block-1d6d50a5df734ade8178ed59d33e3064" id="block-1d6d50a5df734ade8178ed59d33e3064"></a>

Livox Converter Dimensions (unit: mm)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/74870cd2-d7e2-40a4-b8ef-2d350a2a0ec9/image/w=1920,quality=90,fit=scale-down" alt="image" height="277.76008253375306" width="634.352294921875">

## **Specifications** <a href="#block-1695c87d019e44fda55a4feb83aa7bb8" id="block-1695c87d019e44fda55a4feb83aa7bb8"></a>

| **Livox Mid-40/ Livox Mid-100**   |                                                                                     |
| --------------------------------- | ----------------------------------------------------------------------------------- |
| **Operation Temperate Range**     | -4° to 149° F (-20° to 65° C)                                                       |
| **Laser Wavelength**              | 905 nm                                                                              |
| **Laser Safety**                  | Class 1 (IEC 60825-1:2014) eye safe                                                 |
| **Detection Range (@100 klx)**    | 90 m @ 10% reflectivity; 130 m @ 20% reflectivity; 260 m @ 80% reflectivity         |
| **FOV**                           | Livox Mid-40: 38.4° (circular) Livox Mid-100: 98.4° (Horizontal) × 38.4° (Vertical) |
| **Range Precision (1σ @ 20 m)**   | 2 cm                                                                                |
| **Angular Accuracy**              | < 0.1°                                                                              |
| **Beam Divergence**               | 0.28° (Vertical) × 0.03° (Horizontal)                                               |
| **Point Rate**                    | Livox Mid-40: 100,000 points/s; Livox Mid-100: 300,000 points/s                     |
| **Data Latency**                  | ≤ 2 ms                                                                              |
| **False Alarm Ratio (@100 klx)**  | < 0.01%                                                                             |
| **IP Rating**                     | IP67                                                                                |
| **Power**                         | Livox Mid-40: 10 W (Average) 40 W (Peak) Livox Mid-100: 30 W (Average) 67 W (Peak)  |
| **Power Supply Voltage Range**    | 10 \~ 16 V (DC Power supply only)                                                   |
| **Dimensions**                    | Livox Mid-40: 88×69×76 mm Livox Mid-100: 142×70×230 mm                              |
| **Weight**                        | Livox Mid-40: 760 g Livox Mid-100: 2200 g                                           |
| **Livox Mid-40 Mounting Bracket** |                                                                                     |
| **Dimensions**                    | 88×69×18 mm                                                                         |
| **Weight**                        | 101 g                                                                               |
| **Livox Converter**               |                                                                                     |
| **Dimensions**                    | 52×58×25 mm                                                                         |
| **Weight**                        | 66 g                                                                                |
