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

# Wi-Fi HaLow Board based on FGH100M-H

### Seeed Studio Wi-Fi HaLow Board based on the FGH100M-H module

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-wifi-halow-board" %}

### Description

This tutorial will guide you through setting up and using the Wio-WM6180 Wi-Fi HaLow Module with a XIAO ESP32S3 to build a Wi-Fi HaLow client. Wi-Fi HaLow (IEEE 802.11ah) is designed for long-range, low-power IoT applications, operating in the sub-1 GHz frequency band. We'll walk through the hardware setup, software configuration, and demonstrate how to establish Wi-Fi HaLow connectivity for your IoT projects.

#### Key Features[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#key-features) <a href="#key-features" id="key-features"></a>

* Long range Wi-Fi connectivity up to 1km line-of-sight
* Low power consumption ideal for IoT devices
* Sub-1 GHz operation for better penetration through walls and obstacles
* Compatible with XIAO ESP32S3 development board
* Easy to follow setup and configuration process &#x20;

### Hardware <a href="#hardware-overview" id="hardware-overview"></a>

The following table outlines the key specifications of the Wio-WM6180 Wi-Fi HaLow Module:

|   Characteristic  |     Value     | Unit |
| :---------------: | :-----------: | :--: |
| Operating Voltage |      3.3      |   V  |
| Operating Current |      TBD      |  mA  |
|   Wi-Fi Protocol  | IEEE 802.11ah |   -  |
|   Frequency Band  |   Sub-1 GHz   |   -  |
|       Range       |    Up to 1    |  km  |
|     Interface     |      SPI      |   -  |
|     Dimensions    |      TBD      |  mm  |

### What is Wi-Fi HaLow?[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#what-is-wi-fi-halow) <a href="#what-is-wi-fi-halow" id="what-is-wi-fi-halow"></a>

Wi-Fi HaLow is a wireless networking protocol based on the IEEE 802.11ah standard, specifically designed for Internet of Things (IoT) applications. Operating in the sub-1 GHz frequency band (typically 900 MHz), Wi-Fi HaLow offers several significant advantages over traditional Wi-Fi:

![](https://files.seeedstudio.com/wiki/wifi_halow/pic/Wi-Fi_HaLow_frequency_band_graphic.png)

1. **Extended Range**: Wi-Fi HaLow can achieve distances up to 1 kilometer in line-of-sight conditions, far exceeding the range of conventional Wi-Fi.
2. **Improved Penetration**: The lower frequency signals can better penetrate through walls and other obstacles, making it ideal for challenging environments.
3. **Low Power Consumption**: Designed with IoT devices in mind, Wi-Fi HaLow enables years of battery life for connected devices.
4. **Scalability**: Supports thousands of devices connected to a single access point, perfect for large-scale IoT deployments.
5. **Security**: Inherits the robust security features of the Wi-Fi family, including WPA3 encryption.

#### Why Wi-Fi HaLow Matters[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#why-wi-fi-halow-matters) <a href="#why-wi-fi-halow-matters" id="why-wi-fi-halow-matters"></a>

Wi-Fi HaLow addresses the growing needs of IoT applications that require long-range connectivity, low power consumption, and the ability to handle numerous devices simultaneously. It bridges the gap between traditional Wi-Fi and LPWAN technologies, offering:

* **Industrial IoT**: Enables reliable connectivity in factories, warehouses, and industrial settings.
* **Smart Agriculture**: Provides coverage across large agricultural areas for sensor networks.
* **Smart Cities**: Supports extensive networks of connected devices in urban environments.
* **Asset Tracking**: Allows for long-range tracking of valuable assets and equipment.

By combining the familiarity of Wi-Fi with the benefits of low-power, long-range connectivity, Wi-Fi HaLow is poised to play a crucial role in the expansion of IoT applications across various industries.

#### Wi-Fi HaLow System Architecture[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#wi-fi-halow-system-architecture) <a href="#wi-fi-halow-system-architecture" id="wi-fi-halow-system-architecture"></a>

A typical Wi-Fi HaLow network consists of several key components that work together to enable long-range, low-power IoT connectivity:

![](https://files.seeedstudio.com/wiki/wifi_halow/pic/wifi-halow-architecture.png)

1. **Access Point (AP)**: The central hub of the Wi-Fi HaLow network, responsible for managing connections and routing data between devices and the internet.
2. **Stations (STA)**: The client devices that connect to the Access Point. These can be sensors, actuators, or other IoT devices.
3. **Gateway**: Acts as a bridge between the Wi-Fi HaLow network and other networks (e.g., Ethernet or cellular).

### MM-IoT-SDK Framework[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#mm-iot-sdk-framework) <a href="#mm-iot-sdk-framework" id="mm-iot-sdk-framework"></a>

The WM6180 module utilizes [MorseMicro's MM-IoT-SDK](https://github.com/MorseMicro/mm-iot-esp32), which provides:

* **Multi-protocol Support**: Enables seamless integration with various IoT protocols
* **Low Power Management**: Optimized power consumption for battery-powered devices
* **Security Features**: Built-in encryption and authentication mechanisms
* **Easy Configuration**: Simplified API for network setup and management

The MM-IoT-SDK architecture consists of several layers:

1. **Hardware Abstraction Layer (HAL)**: Provides a unified interface for different hardware platforms
2. **Network Stack**: Implements the Wi-Fi HaLow protocol stack
3. **Application Layer**: Offers APIs for application development and device management

This framework allows developers to quickly implement Wi-Fi HaLow functionality while maintaining flexibility for custom applications.

### Building Example Firmware[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#building-example-firmware) <a href="#building-example-firmware" id="building-example-firmware"></a>

The mm-iot-esp32 repository includes several example applications that demonstrate different functionalities. Here's how to build and configure these examples:

#### Example Applications Location[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#example-applications-location) <a href="#example-applications-location" id="example-applications-location"></a>

All example applications can be found in the `examples` directory of the repository. Available examples include:

* `scan`: Wi-Fi scanning example
* `iperf`: iperf server example
* `sta_reboot`: Wi-Fi station reboot example
* `sta_connect`: Wi-Fi station connection example
* `web_camera_server`: Web camera server example
* And more...

#### Configure Network Credentials[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#configure-network-credentials) <a href="#configure-network-credentials" id="configure-network-credentials"></a>

Before building the firmware, you need to configure the network settings in the example's configuration file:

1. Navigate to your chosen example directory:

```
cd $MMIOT_ROOT/examples/example_name
```

2. Edit the configuration file:

```
# Open the configuration file
nano src/mm_app_loadconfig.c
```

3. In this file, you can modify:

* Country code (should be set to **US** as the product is currently only available for North America)
* Wi-Fi HaLow network credentials
* Other network-related parameters

**caution:**

Important Note About Country Code:

* The country code must be set to "US" as this product is currently only available for the North American market
* The product is not yet available for other regions due to regulatory requirements
* Using the product in regions other than North America may violate local regulations

#### Building Process[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#building-process) <a href="#building-process" id="building-process"></a>

After configuring the network settings, you can build the firmware using these commands:

```
idf.py set-target esp32s3
idf.py fullclean
idf.py build
```

**note:**

* The `idf.py set-target` command only needs to be run once for each example
* `idf.py fullclean` ensures a clean build by removing all previous build artifacts
* After successful build, the firmware binary will be located in the `build` directory

#### Build Output[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#build-output) <a href="#build-output" id="build-output"></a>

After a successful build, you should see output similar to this:

```
# Project build complete. To flash, run this command:
idf.py -p (PORT) flash
```

Below, we will demonstrate a few examples.

### Example 1. scan[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#example-1-scan) <a href="#example-1-scan" id="example-1-scan"></a>

This example demonstrates how to scan for available Wi-Fi HaLow networks in your vicinity. Follow these steps to build and run the scan example:

#### Step 1: Navigate to the Scan Example[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-1-navigate-to-the-scan-example) <a href="#step-1-navigate-to-the-scan-example" id="step-1-navigate-to-the-scan-example"></a>

```
cd ~/mm-iot-esp32/example/scan
```

#### Step 2: Configure Country Code[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-2-configure-country-code) <a href="#step-2-configure-country-code" id="step-2-configure-country-code"></a>

1. Open the configuration file:

```
nano main/src/mm_app_loadconfig.c
```

2. Locate and modify the country code line:

```
#define COUNTRY_CODE "US"  // Must use "US" as the product is only available for North America
```

#### Step 3: Hardware Setup[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-3-hardware-setup) <a href="#step-3-hardware-setup" id="step-3-hardware-setup"></a>

1. Connect the Wio-WM6180 Wi-Fi HaLow Module to your XIAO ESP32S3
2. Connect the XIAO ESP32S3 to your computer via USB

#### Step 4: Build and Flash[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-4-build-and-flash) <a href="#step-4-build-and-flash" id="step-4-build-and-flash"></a>

Execute the following commands in sequence:

```
idf.py set-target esp32s3
idf.py fullclean
idf.py build
idf.py flash monitor
```

#### Step 5: Monitor Results[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-5-monitor-results) <a href="#step-5-monitor-results" id="step-5-monitor-results"></a>

If everything is working correctly:

* The serial monitor will start automatically after flashing
* The program will begin scanning for Wi-Fi HaLow networks
* If any Wi-Fi HaLow gateways are in range, their information will be displayed in the serial monitor

Example output in the serial monitor:

![](https://files.seeedstudio.com/wiki/wifi_halow/pic/9.png)

**tip:**

* Make sure there are Wi-Fi HaLow gateways in your vicinity to detect networks
* The scanning process runs continuously, so you'll see periodic updates of available networks
* Press Ctrl+C to stop the monitor and exit the program

**note:**

If you don't see any networks:

* Verify that your Wi-Fi HaLow gateway is powered on and functioning
* Check that you're within range of the gateway
* Ensure the module is properly connected to your XIAO ESP32S3

### Example 2. iperf[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#example-2-iperf) <a href="#example-2-iperf" id="example-2-iperf"></a>

This example demonstrates how to test the network performance of your Wi-Fi HaLow connection using iPerf. Follow these steps to build and run the iPerf example:

#### Step 1: Navigate to the iPerf Example[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-1-navigate-to-the-iperf-example) <a href="#step-1-navigate-to-the-iperf-example" id="step-1-navigate-to-the-iperf-example"></a>

```
cd ~/mm-iot-esp32/example/iperf
```

#### Step 2: Configure Network Settings[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-2-configure-network-settings) <a href="#step-2-configure-network-settings" id="step-2-configure-network-settings"></a>

1. Open the configuration file:

```
nano main/src/mm_app_loadconfig.c
```

2. Modify the following parameters:

```
// Set country code (must be "US" for North America)
#define COUNTRY_CODE "US"

// Set your Wi-Fi HaLow network credentials
#define SSID             Your_HaLow_SSID           // Replace with your network name
#define SAE_PASSPHRASE   Your_Password             // Replace with your network password
```

#### Step 3: Hardware Setup[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-3-hardware-setup-1) <a href="#step-3-hardware-setup-1" id="step-3-hardware-setup-1"></a>

1. Connect the Wio-WM6180 Wi-Fi HaLow Module to your XIAO ESP32S3
2. Connect the XIAO ESP32S3 to your computer via USB

#### Step 4: Build and Flash[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-4-build-and-flash-1) <a href="#step-4-build-and-flash-1" id="step-4-build-and-flash-1"></a>

Execute the following commands in sequence:

```
idf.py set-target esp32s3
idf.py fullclean
idf.py build
idf.py flash monitor
```

#### Step 5: Run Performance Test[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-5-run-performance-test) <a href="#step-5-run-performance-test" id="step-5-run-performance-test"></a>

Once the program is running successfully, you'll see the iPerf service start up. Now you can run performance tests from your Wi-Fi HaLow gateway.

For IPv4 testing, execute this command on your gateway:

```
iperf -c <device_ip> -p <port> -i 1 -u -b 20M
```

For IPv6 testing, execute this command on your gateway:

```
iperf -c <device_ip>%wlan0 -p <port> -i 1 -V -u -b 20M
```

The parameters explained:

* `-c`: Run in client mode
* `-p`: Port number
* `-i`: Report interval (1 second)
* `-u`: Use UDP protocol
* `-b`: Target bandwidth (20 Mbps)
* `-V`: IPv6 mode (for IPv6 testing only)

![](https://files.seeedstudio.com/wiki/wifi_halow/pic/11.png)

**tip:**

* Make sure your device has successfully connected to the Wi-Fi HaLow network before running the performance test
* The device's IP address will be displayed in the serial monitor after connection
* You can adjust the bandwidth (-b parameter) based on your testing needs

**note:**

Common issues and solutions:

* If connection fails, verify your network credentials
* If iPerf service doesn't start, check your hardware connections
* If performance is poor, ensure you're within good range of the gateway

### Example 3. web\_camera\_server[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#example-3-web_camera_server) <a href="#example-3-web_camera_server" id="example-3-web_camera_server"></a>

This example demonstrates how to stream camera feed from XIAO ESP32S3 Sense over Wi-Fi HaLow network. Follow these steps to build and run the web camera server:

#### Step 1: Navigate to the Web Camera Example[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-1-navigate-to-the-web-camera-example) <a href="#step-1-navigate-to-the-web-camera-example" id="step-1-navigate-to-the-web-camera-example"></a>

```
cd ~/mm-iot-esp32/example/web_camera_serve
```

#### Step 2: Configure Network Settings[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-2-configure-network-settings-1) <a href="#step-2-configure-network-settings-1" id="step-2-configure-network-settings-1"></a>

1. Open the configuration file:

```
nano main/src/mm_app_loadconfig.c
```

2. Modify the Wi-Fi HaLow credentials:

```
// Set your Wi-Fi HaLow network credentials
#define SSID              Your_HaLow_SSID           // Replace with your network name
#define SAE_PASSPHRASE    Your_Password             // Replace with your network password
```

#### Step 3: Hardware Setup[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-3-hardware-setup-2) <a href="#step-3-hardware-setup-2" id="step-3-hardware-setup-2"></a>

1. Connect the Wio-WM6180 Wi-Fi HaLow Module to your XIAO ESP32S3 Sense
2. Ensure the camera module on your XIAO ESP32S3 Sense is properly connected
3. Connect the XIAO ESP32S3 Sense to your computer via USB

#### Step 4: Build and Flash[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-4-build-and-flash-2) <a href="#step-4-build-and-flash-2" id="step-4-build-and-flash-2"></a>

Execute the following commands in sequence:

```
idf.py set-target esp32s3
idf.py fullclean
idf.py build
idf.py flash monitor
```

#### Step 5: Access the Camera Feed[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#step-5-access-the-camera-feed) <a href="#step-5-access-the-camera-feed" id="step-5-access-the-camera-feed"></a>

Once the program is running successfully:

1. Note the IP address displayed in the serial monitor
2. Open a web browser on any device connected to the same network as your Wi-Fi HaLow gateway
3. Enter the IP address in your browser's address bar
4. You should now see the live camera feed from your XIAO ESP32S3 Sense

Example URL:

```
http://192.168.4.1
```

![](https://files.seeedstudio.com/wiki/wifi_halow/pic/14.png)

**tip:**

For the best streaming experience:

* Ensure good lighting conditions for better image quality
* Keep the XIAO ESP32S3 Sense within good range of the Wi-Fi HaLow gateway
* Use a modern web browser for optimal compatibility

**note:**

Troubleshooting:

* If you can't access the camera feed, verify that your device is on the same network as the Wi-Fi HaLow gateway
* If the image is not showing, check that the camera module is properly connected
* If the stream is laggy, try moving closer to the Wi-Fi HaLow gateway

### Resources[​](https://wiki.seeedstudio.com/getting_started_with_wifi_halow_module_for_xiao/#resources) <a href="#resources" id="resources"></a>

* **\[GITHUB]** [mm-iot-esp32 repository](https://github.com/Seeed-Studio/mm-iot-esp32.git)
* **\[GITHUB]** [mm-iot Document](https://github.com/Seeed-Studio/mm-iot-esp32/blob/main/documentation.html)
* **\[PDF]** [WI-FI\_HALOW\_FGH100M\_EXT01\_V30\_SCH\_20241107](https://files.seeedstudio.com/wiki/wifi_halow/res/WI-FI_HALOW_FGH100M_EXT01_V30_SCH_20241107.pdf)
* **\[KiCAD]** [WI-FI\_HALOW\_FGH100M\_EXT01\_V30 KiCAD PCB File](https://files.seeedstudio.com/wiki/wifi_halow/res/WI-FI_HALOW_FGH100M_EXT01_V30.kicad_pcb)
* **\[PDF]** [Quectel\_FGH100M-H\_Short-Range\_Module\_Specification\_V1.0.0](https://files.seeedstudio.com/wiki/wifi_halow/res/Quectel_FGH100M-H_Short-Range_Module_Specification_V1.0.0_Preliminary_20241018.pdf)
