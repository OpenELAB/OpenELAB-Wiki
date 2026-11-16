# LIVOX HUB User Manual

> **LIVOX HUB User Manual**

{% embed url="https://www.livoxtech.com/hub/downloads" %}

## **Product Profile** <a href="#block-d45317732d094382851897dd45ad65de" id="block-d45317732d094382851897dd45ad65de"></a>

### **Introduction** <a href="#block-c12b2fc80d244181924beebf1027601f" id="block-c12b2fc80d244181924beebf1027601f"></a>

Livox Hub is a streamlined way to integrate and manage Livox LiDAR sensors and their data outputs. One Livox Hub can connect to up to nine Livox LiDAR sensor units.

LiDAR Management: Livox Hub communicates with each connected LiDAR sensor and reads each sensor’s connection status, firmware version, and working states. When Livox Hub is connected, users can monitor all connected LiDAR sensors together through Livox Hub. If there are any abnormalities with Livox Hub or the Livox LiDAR sensors connected, Livox Hub sends a warning prompt. Users can then check the error codes using Livox Viewer or the Livox SDK.

Each Livox LiDAR port has independent power control and short circuit protection. Users can turn the power supply on or off to a specific LiDAR port using Livox Viewer or the Livox SDK.

Livox Hub can unify the point cloud data into the user’s coordinate system and integrate all LiDAR point cloud data into a single output. The point cloud data of Livox Hub can be displayed in Cartesian or Spherical coordinates, and can be changed using Livox Viewer.

Time Synchronization: Time synchronization is supported by IEEE 1588-2008 (PTPv2) and GPS, delivering sub-microsecond-level time synchronization of point cloud data.

Livox SDK: The Livox LiDAR Software Development Kit (SDK) is provided to help develop customizable applications using the point cloud data.

* The precision of IEEE 1588-2008 (PTPv2) was tested in a lab environment.
* Refer to the SDK Communication Protocol to check the format of the point cloud timestamps.
* When nine Livox Mid-100 sensor units are connected to a Livox Hub, the maximum data bandwidth is approximately 300Mbps.
* Operating Livox Hub in a residential environment could cause radio interference.

### Overview <a href="#block-391d4c79856d805fa12bd7b8e6b09472" id="block-391d4c79856d805fa12bd7b8e6b09472"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d89bc670-8fc6-467a-8b1a-3faa90858cb1/image/w=1920,quality=90,fit=scale-down" alt="image" height="197.965461884569" width="634.3409423828125">

1. **Livox Hub**
2. The main section of Livox Hub, which can be used with or without the port covers.
3. **Port Cover × 4**
4. Protect the ports from damage. To view the ports on Livox Hub, unscrew and remove the port covers.
5. **Status LEDs**
6. Displays the working states of Livox Hub. Refer to Appendix 7.1 for more information.
7. **Dissipation Area**
8. Dissipates heat. DO NOT cover this area when Livox Hub is in use. It is recommended to keep a space of 30 mm between this area and other objects.
9. **Livox LiDAR Port × 7**
10. A JAE MX34012NF1 type connector port used to connect to Livox LiDAR sensor units. Only compatible with JAE MX34012SF1 type connectors.
11. **Livox LiDAR Port × 2**
12. A JAE MX34012NF1 type connector port used to connect to Livox LiDAR sensor units. Only compatible with JAE MX34012SF1 type connectors.
13. **Gigabit Ethernet Port**
14. A RJ45 type Ethernet port used to connect to Ethernet cables.
15. **GPS Sync Port**
16. A JAE MX34005NF1 type port used to connect the designated GPS sync cable when GPS synchronization is required. Only compatible with JAE MX34005SF1 type connectors.
17. **Power Port**
18. A MOLEX 76825-0004 type port that connects to an external power source. Only compatible with MOLEX 171692-0104 type connectors.

* To view the ports on Livox Hub, unscrew and remove the port covers.

## **Connectors** <a href="#block-e0084e8b75b74a6bbac090b564c774c8" id="block-e0084e8b75b74a6bbac090b564c774c8"></a>

### **Livox LiDAR Port** <a href="#block-0f8cd013762d43dcb747071e543922d7" id="block-0f8cd013762d43dcb747071e543922d7"></a>

There are nine Livox LiDAR ports available on Livox Hub, and those nine Livox LiDAR ports have the same functionality. Below is more information on the Livox LiDAR ports.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19ad83a8-dbd1-4bc0-99de-f9cb874905a5/image/w=1920,quality=90,fit=scale-down" alt="image" height="183.05594796316964" width="634.352294921875">

| **Pin** | **Signal**    | **Type** | **Description**            |
| ------- | ------------- | -------- | -------------------------- |
| 1       | Power+        | Power    | DC Output 12.8 V           |
| 7       |               |          | 5 A Over Current Protect   |
| 2       | Ground        | Power    | Ground                     |
| 8       |               |          |                            |
| 11      |               |          |                            |
| 3       | Ethernet\_TX+ | Output   | 100BASE-TX, TX+            |
| 4       | Ethernet\_TX- | Output   | 100BASE-TX, TX-            |
| 5       | PortDet       | Input    | Port Detection Signal      |
| 6       | Sync+         | Input    | RS485\_A, Pulse Per Second |
| 9       | Ethernet\_RX+ | Input    | 100BASE-TX, RX+            |
| 10      | Ethernet\_RX- | Input    | 100BASE-TX, RX-            |
| 12      | Sync-         | Input    | RS485\_B, Pulse Per Second |

Table 2.1.1 Livox Hub LiDAR port description

### **Power Port and Power Cable** <a href="#block-7ccd1353295747aab62831fe57c9562a" id="block-7ccd1353295747aab62831fe57c9562a"></a>

The Livox Hub power port and the ends of the power cable included with Livox Hub have the same functionality.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ccb4f1eb-8591-452b-a83c-64c9ae18aaa4/image/w=1920,quality=90,fit=scale-down" alt="image" height="234.4712525667351" width="634.375">

**Power Cable**

Connect “A” to the power port of Livox Hub and connect “B” to an external DC power supply.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/47eb7bde-a768-4720-8798-f326899be080/image/w=1920,quality=90,fit=scale-down" alt="image" height="176.71585505772143" width="634.352294921875">

| **Pin** | **Signal** | **Type** | **Description** | **Color** |
| ------- | ---------- | -------- | --------------- | --------- |
| 1       | Power+     | Power    | DC 10-23 V      | Red       |
| 2       | Power+     | Power    | DC 10-23 V      | Red       |
| 3       | Ground     | Power    | Ground          | Black     |
| 4       | Ground     | Power    | Ground          | Black     |

Table 2.2.1 Livox Hub power port and power cable description

### **GPS Sync Port and GPS Sync Cable** <a href="#block-4bc02bf84fc544739edcb255855c7057" id="block-4bc02bf84fc544739edcb255855c7057"></a>

The Livox Hub GPS sync port and the ends of the GPS sync cable included with Livox Hub have the same functionality.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cc8351b5-28b1-4edb-a919-cbaf36e63530/image/w=1920,quality=90,fit=scale-down" alt="image" height="173.17974452554742" width="634.375">

**GPS Sync Cable**

Connect “A” to the GPS sync port of Livox Hub and connect “B” to the GPS sync signal. Refer to the Data Synchronization section for more information.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5bcc0270-7267-45a5-9ee5-76c2db6a2e43/image/w=1920,quality=90,fit=scale-down" alt="image" height="158.81586351327016" width="634.3636474609375">

| **Pin** | **Signal** | **Type** | **Description**            | **Color** |
| ------- | ---------- | -------- | -------------------------- | --------- |
| 1       | PPS\_N     | Input    | RS485\_B, Pulse Per Second | White     |
| 2       | PPS\_P     | Input    | RS485\_A, Pulse Per Second | Blue      |
| 3       | Ground     | Power    | Ground                     | Black     |
| 4       | STAMP\_N   | Input    | RS485\_B, GPS Data         | Yellow    |
| 5       | STAMP\_P   | Input    | RS485\_A, GPS Data         | Grey      |

Table 2.3.1 Livox Hub GPS sync port and sync cable description

**GPS Sync Signal Description:**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b992a35b-d434-4502-a768-f518889cd0a0/image/w=1920,quality=90,fit=scale-down" alt="image" height="262.39451237840575" width="634.3409423828125">

Refer to the Software Development Kit (SDK) section for more information about the GPS sync signal.

The Gigabit Ethernet port is a RJ45 type Ethernet port, which supports 1000BASE-T and 100BASE-TX and uses two twisted pairs to send and receive data. On the front of Livox Hub, there are three status LEDs. LED 3 indicates the type of data transmission.

Blue: 100 Megabit Ethernet is used for transmission

Green: Gigabit Ethernet is used for transmission

It is recommended to use Gigabit Ethernet for data transmission and to use Cat5e or above Ethernet cables.

Refer to the Appendix section for more information on the status LEDs.

## **Mounting Livox Hub** <a href="#block-4255c14b742b49e0a2107a74248299f8" id="block-4255c14b742b49e0a2107a74248299f8"></a>

Livox Hub is outfitted with four M3 mounting holes with a depth of 6 mm on the bottom, and it can be mounted using M3 screws. Livox Hub is already mounted with the port covers. The port covers can be removed if there are spacial constraints when mounting or positioning Livox Hub. However, it is recommended to keep the port covers mounted to Livox Hub. Only remove the port covers if absolutely necessary. To remove the port covers, unscrew the screws.

**Dimensions (With Port Covers)**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ddd25e54-0b9b-4457-a6fd-3b9af0f30552/image/w=1920,quality=90,fit=scale-down" alt="image" height="194.98703429881334" width="634.3636474609375">

| **Weight** | **Approx. 1352 g (for reference only)** |
| ---------- | --------------------------------------- |
| Dimensions | 280 × 201 × 29 mm                       |

**Dimensions (Without Port Covers)**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/450099f7-596d-4160-aa8f-02396ccfd751/image/w=1920,quality=90,fit=scale-down" alt="image" height="180.80459552806812" width="634.3409423828125">

| **Weight** | **Approx. 865 g (for reference only)** |
| ---------- | -------------------------------------- |
| Dimensions | 201 × 153.2 × 29 mm                    |

## **Getting Started** <a href="#block-f7c3f1a139854644a55d3e627f6879a4" id="block-f7c3f1a139854644a55d3e627f6879a4"></a>

### **External Power Supply** <a href="#block-1bbed3b6a8734c3e9318a9ee73cdd4da" id="block-1bbed3b6a8734c3e9318a9ee73cdd4da"></a>

The working voltage of Livox Hub is 10 V to 23 V. Regardless of how many Livox LiDAR sensors are connected to Livox Hub, the working voltage range of Livox Hub remains the same. Contact Livox if you intend to use an external power source exceeding 23 V.

### **Connection** <a href="#block-695d0c865d3f4d2a9c666582437d41d8" id="block-695d0c865d3f4d2a9c666582437d41d8"></a>

Livox Hub uses an Ethernet cable for data transmission and supports user datagram protocol (UDP). Both static and dynamic IP address configurations are supported and the addresses are assigned by default to Livox Hub using dynamic host configuration protocol (DHCP).

The static and dynamic IP addresses are connected in different ways. The dynamic IP address is connected by default using a router with DHCP. To connect to the static IP address, make sure Livox Hub is in static IP mode by using Livox Viewer or the Livox SDK.

💡

**Note:**

* If Livox LiDAR sensors are connected to Livox Hub after the IP address is set, make sure to disconnect the power source and connect again with the LiDAR sensors connected. Otherwise, the external power source cannot provide power to the LiDAR sensors connected.
* DO NOT connect or disconnect the Livox LiDAR sensors to or from Livox Hub while powering on. It is required to reconnect Livox Hub to the external power source after the Livox LiDAR sensors are connected or disconnected.

**Dynamic IP Address**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f206f0cc-3564-4e18-84ec-1284067c8191/image/w=1920,quality=90,fit=scale-down" alt="image" height="187.50958674208923" width="634.3409423828125">

1. Connect the Livox LiDAR sensors to Livox Hub (a Livox Hub can connect to up to nine Livox LiDAR sensor units).
2. Connect the computer and Livox Hub to the router using Ethernet cables. Make sure both the computer and Livox Hub are connected to the LAN port on the router.
3. Connect Livox Hub to an external power source.
4. Connect one end of the GPS sync cable to the sync port and the other end to the designated sync signal. Note that the GPS sync cable may not always be required.

💡

**Note:**

* The working voltage of Livox Hub is 10 V to 23 V. Contact Livox if you intend to use an external power source exceeding 23 V.
* Make sure to use Cat5e or above Gigabit Ethernet cables and a Gigabit router.

**Static IP address**

1. Connect Livox LiDAR sensors, router, external power source, and computer by following Figure 4.2.1.
2. Run Livox Viewer, and Click 📁 to open Device Manager. Select Livox Hub, and click 📁 to open Properties. Set the IP address of Livox Hub to static IP address. Note that the static IP address of Livox Hub should be 192.168.1.X. X can be set to any number between 2 to 233.
3. Disconnect Livox Hub, Livox LiDAR sensors, router, external power source, and computer.
4. Set the IP address of your computer to static IP address. Note that the static IP address of the computer should be 192.168.1.X. X can be set to any number between 2 to 233 and should be different from the IP address of Livox Hub set in Step 2.
5.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8cdad884-5518-44c9-a339-f84511396d83/image/w=1920,quality=90,fit=scale-down" alt="image" height="191.27008620383523" width="596.3636474609375">
6. Connect the Livox LiDAR sensors to Livox Hub (a Livox Hub can connect up to nine Livox LiDAR sensor units).
7. Connect Livox Hub to the computer using an Ethernet cable.
8. Connect Livox Hub to an external power source.

💡

**Note:**

* Make sure to use a Cat5e or above Gigabit Ethernet cable.
* Make sure to set the IP address of Livox Hub back to dynamic IP address if it has been set to static IP address to use a router for connection. Also, make sure to set your computer to dynamic IP address, and follow the instructions in the Dynamic IP Address section.
* When Livox Hub is in use, it is not required to set the IP address to all the LiDAR sensors connected. Only Livox Hub’s IP address should be set, and then Livox Hub will automatically assign an IP address to each LiDAR sensor.

## **Usage** <a href="#block-5cc982d14e8240efa3118f4752dee892" id="block-5cc982d14e8240efa3118f4752dee892"></a>

### **Output Data** <a href="#block-1a51c79aea604362acff5d25b86753d2" id="block-1a51c79aea604362acff5d25b86753d2"></a>

The output data of Livox Hub includes point cloud data, timestamps, and status codes.

### **Point Cloud Data** <a href="#block-c72084e68c694163871c1c66ce9c4669" id="block-c72084e68c694163871c1c66ce9c4669"></a>

Livox Hub, as a processing unit to connect and integrate Livox LiDAR sensors, will not affect the point cloud data output of the LiDAR sensors connected. Only the LiDAR sensors will affect the point cloud data. Refer to the [Output Data section](https://editor.csdn.net/md/?articleId=162460505) in the corresponding Livox LiDAR sensor’s user manual for more information.

### **Timestamp** <a href="#block-cb17c4a6064544119954d528ca37c601" id="block-cb17c4a6064544119954d528ca37c601"></a>

Time synchronization is supported by IEEE 1588-2008 (PTPv2) and GPS.

IEEE 1588-2008 (PTPv2): IEEE 1588-2008 is the Precision Time Protocol (PTP) enabling precise synchronization of clocks in measurement and control systems by Ethernet. Livox LiDAR sensors, as the ordinary clock in the PTP, only supports UDP/IPV4 for PTP. Livox LiDAR sensors support the following message events: Sync, Flow\_up, Delay\_req, Delay\_resp.

GPS: GPS is a way to precisely synchronize the point cloud sampling time using the sync pulse generated. The time synchronization can be completed with a PPS signal and a NMEA $GPRMC record. PPS is the precise pulse per second, and its rising edge is 1s. $GPRMC offers the UTC time of PPS. The time sequence of PPS and $GPRMC is shown below. After time synchronization, each point cloud data packet will include a timestamp indicating the sampling time of the point cloud. Please refer to the [SDK Communication Protocol](https://editor.csdn.net/md/?articleId=162460505) for more information.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9085e1da-3bcf-40d3-ab30-36d19e8de58b/image/w=1920,quality=90,fit=scale-down" alt="image" height="273.5412040115248" width="634.3636474609375">

### **Working States & Working Modes** <a href="#block-9fcacc62a6f048068c67a44095998562" id="block-9fcacc62a6f048068c67a44095998562"></a>

**Working States**

When Livox Hub is in use, it automatically monitors the working states of all the Livox LiDAR sensors connected. Users can check the working state of Livox Hub and all the Livox LiDAR sensors connected using Livox Viewer or the Livox SDK.

If Livox Hub detects any abnormalities when monitoring the LiDAR sensors, it sends a warning prompt or may even cut off the power supply of a specific LiDAR sensor if a critical error is detected. The error codes can be viewed using Livox Viewer or the Livox SDK.

**Working Modes**

The working mode of each Livox LiDAR sensors must be set separately using Livox Viewer or the Livox SDK. Additionally, the Rain/Fog Suppression of the Livox LiDAR sensors should also be set individually.

### **Integration of Point Cloud Data** <a href="#block-4af7118594a044a0ba2e3aa756064297" id="block-4af7118594a044a0ba2e3aa756064297"></a>

Livox Hub is capable of unifying the point cloud data into the user’s coordinate system and integrating all LiDAR point cloud data into a single output. When using Livox Viewer, after opening Import Extrinsics Tool, the point cloud data integration of Livox Hub will be paused after clicking “Start Cali.” After the coordinates have been set and applied to all the Livox LiDAR sensors by clicking “Apply,” then click “Stop Cali.” Livox Hub will automatically integrate the point cloud data and produce a single output.

The integration of point cloud data can be achieved by using the Livox SDK as well. Refer to the SDK Communication Protocol for more information.

### **Livox Viewer** <a href="#block-2d61d9c4e2a0460fa5254375ed06d2f8" id="block-2d61d9c4e2a0460fa5254375ed06d2f8"></a>

Livox Viewer is a Windows software designed for Livox LiDAR sensors and Livox Hub. Users can check real-time point cloud data of all the Livox LiDAR sensors connected to Livox Hub. With the help of Livox Viewer, it is easier to check and record the point cloud data for future use.

Visit [www.livoxtech.com](http://www.livoxtech.com/) to download the latest Livox Viewer. Livox Viewer supports WINDOWS® 7/8/10 (64 bit).

💡

* Turn off Windows Firewall and set the computer to obtain IP address automatically before using Livox Viewer.
* Make sure the video driver is correctly installed. Otherwise, Livox Viewer may not launch or may crash.

After turning off Windows Firewall and setting the IP address, unzip and run Livox Viewer.

This user manual only focuses on some functions of Livox Viewer that are related to Livox Hub. Refer to the Livox Mid Series User Manual for more information.

**Livox Viewer Homepage**

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6123eebd-05fb-47e1-8db8-6b8eb41a7d7b/wps-1/w=1920,quality=90,fit=scale-down" alt="image" height="355.77707715133533" width="634.375">

**Checking Real-time Point Cloud Data**

1. Connect all the Livox LiDAR sensors and Livox Hub as shown in Figure 4.2.1 or Figure 4.2.2. Run Livox Viewer. Click to open Device Manager. Device Manager will display Livox Hub in the LAN.
2. Select “Hub” in Device Manager.
3. Select Livox Hub, and click to connect. Alternatively, select Livox Hub, right click, and click “Connect Device”. When Livox Hub is connected, all the LiDAR sensors connected to Livox Hub will be automatically connected.
4. After connecting, click to view the point cloud data.

To see all the LiDAR sensors connected, right click Livox Hub in Device Manager. Next, click on the right of each LiDAR sensor to check the working state, or click on the left of each LiDAR sensor to display or hide the point cloud of the selected Livox LiDAR sensor.

**Checking and Setting LiDAR Sensor Properties**

1. Connect all the Livox LiDAR sensors and Livox Hub as shown in Figure 4.2.1 or Figure 4.2.2. Run Livox Viewer. Click to open Device Manager. The Device Manager will display Livox Hub in the LAN.
2. Select “Hub” in Device Manager.
3. Select Livox Hub and click to connect. Alternatively, select Livox Hub, right click, and click “Connect Device”.
4. Click to check device properties. Click Livox Hub to view the current status of Livox Hub, including the firmware version, IP address, and the type of coordinates. Under the “Hub Slot Power Options”, unselect a number to cut off the power supply of the corresponding LiDAR sensor.
5. Click the triangle icon to the left of Livox Hub to view all the LiDAR sensors connected. Click each LiDAR sensor to check the properties. For each LiDAR sensor, you can check its current status, including the firmware version and work state. Under settings, you can set the working mode for an individual LiDAR sensor and enable or disable Rain/Fog Suppression.

**Importing Extrinsics**

When importing extrinsics, the coordinates of each LiDAR sensor will be calibrated individually. Refer to the [Importing Extrinsics section](https://editor.csdn.net/md/?articleId=162460505) of the Livox LiDAR sensors’ user manual for more information about importing extrinsics.

**Firmware Update**

The firmware of Livox Hub can be updated by using Livox Viewer. To update the firmware, follow the steps below:

1. Click Tools > Firmware Update. A page appears displaying all detected devices.
2. Select “Hub Update” under update mode to display the detected Livox Hub.
3. Click “Check Firmware” to check the current firmware version of the selected Livox Hub.
4. Select the firmware version under “Firmware Version”, and click “Download” to download the firmware to the computer.
5. After downloading the file, select Livox Hub you wish to update under “Firmware Update” and click “…” to select the downloaded firmware.
6. Click “Start” to update the firmware of the selected Livox Hub.
7. Livox Hub restarts and reconnects to the computer after the update. Repeat the steps above if the update fails.
8. To update the Livox LiDAR sensors connected to Livox Hub, select “Hub LiDAR Update” under update mode and follow steps 3 to 4. Afterwards, under “Firmware Update,” select the Livox LiDAR sensors you wish to update. Click “…” to select the downloaded firmware, and click “Start” to update the firmware of the selected Livox LiDAR sensors.

💡

**Note:**&#x4D;ake sure the computer is connected to the internet when downloading the firmware. After the firmware is downloaded, internet connection is not required.

### **Software Development Kit (SDK)** <a href="#block-7a56d5028f3b444db58d944356538a4c" id="block-7a56d5028f3b444db58d944356538a4c"></a>

Besides using Livox Viewer to check real-time point cloud data, users can also use the SDK to apply the point cloud data acquired from Livox LiDAR sensors to different scenarios.

**SDK Communication Protocol**

There are two types of communication protocols between the user and a Livox LiDAR sensor, and the protocol formats of these two kinds of data are different. The specific functions and differences of these types of communications are as follows:

* **Control Command Data**: Configuration and query of LiDAR parameters and status information.
* **Point Cloud Data**: Point cloud coordinate data generated by LiDAR.

Both communication protocols are located in the data segment of the UDP package and stored in little-endian format.

To download the Livox SDK Communication Protocol and Livox SDK API Reference, please visit:

[https://www.livoxtech.com/sdk](https://www.livoxtech.com/sdk)

#### **After-sales Information** <a href="#block-c026cc97dad2423ead1eb273f7b06491" id="block-c026cc97dad2423ead1eb273f7b06491"></a>

Visit [www.livoxtech.com/support](http://www.livoxtech.com/support) to check the after-sales policy and warranty conditions for Livox Hub.

## **Appendix** <a href="#block-1ad6eaa2a4344698a1a9f536f8e625c6" id="block-1ad6eaa2a4344698a1a9f536f8e625c6"></a>

### **Status LED Description** <a href="#block-956706ab01c2408480bd0d5a0d9e4d80" id="block-956706ab01c2408480bd0d5a0d9e4d80"></a>

There are three LEDs on Livox Hub: LED 1 is red, LED 2 is green, and LED 3 alternates between blue and green.

LED 1 and LED 2 display the working status of Livox Hub:

| **Normal Status**                   | **Description**                                                          |
| ----------------------------------- | ------------------------------------------------------------------------ |
| LED 1 and LED 2 blinks continuously | Livox Hub is initializing                                                |
| LED 2 blinks slowly                 | GPS synchronization                                                      |
| LED 2 blinks fast                   | IEEE 1588 V2 synchronization                                             |
| LED 2 is solid on                   | No sync signal                                                           |
| Abnormal Status                     |                                                                          |
| LED 1 blinks slowly                 | GPS synchronization abnormal                                             |
| LED 1 blinks fast                   | IEEE 1588 V2 synchronization abnormal                                    |
| LED 1 blinks twice                  | No IP address is assigned to Livox Hub (restart Livox Hub or the router) |
| LED 1 is solid on                   | Critical error. Please contact Livox.                                    |

LED 3 expresses the Ethernet transmission speed:

Blue: Megabit Ethernet is used for transmission.

Green: Gigabit Ethernet is used for transmission.

## **Specifications** <a href="#block-cfb15b9c753b44248041696f6bb4ad9c" id="block-cfb15b9c753b44248041696f6bb4ad9c"></a>

| **Specification**           | **Details**                               |
| --------------------------- | ----------------------------------------- |
| LiDAR Ports                 | 9                                         |
| Voltage Range               | 10 \~ 23 V DC                             |
| Power Input\*               | Varies in different situations            |
| Operating Temperature Range | -40° to 185° F (-40° to 85° C)            |
| Data Interface              | 1Gbps Ethernet                            |
| Time Sync Protocol          | IEEE 1588 V2 PTP                          |
|                             | GPS Precision Time                        |
| Weight\*\*                  | Approx. 865 g (without port covers)       |
|                             | Approx. 1352 g (with port covers)         |
| Dimensions\*\*              | 153.2 × 201 × 29 mm (without port covers) |
|                             | 208 × 201 × 29 mm (with port covers)      |
| Model                       | LIVOX HUB                                 |

* The typical input power of Livox Hub is 180 W (12 V, 15 A) when five Livox Mid-100 sensor units are connected at a temperature of 77° F(25° C) using an external power supply of 12 V. The output power of Livox Hub varies based on the number of the Livox LiDAR sensors connected and will be affected by the operational temperature. Refer to the Livox LiDAR sensors’ user manual to view their working power.
* The port covers are detachable. Users can attach or detach the four port covers based on personal demands.
