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

# SenseCAP Card Tracker

{% hint style="info" %}
[**View Seeed Studio SenseCAP Card Tracker T1000-E for LoRaWAN (Not for Meshtastic) on OpenELAB**](https://openelab.io/products/seeed-studio-sensecap-card-t1000e)

**Store SKU / option:** `Seeed-114993591`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio SenseCAP Card Tracker T1000-E for LoRaWAN

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-sensecap-card-t1000e" %}

### Description

T1000-E for LoRaWAN comes with fully open-source firmware. To enhance the user experience, we provide demo firmware pre-installed on factory-produced devices. Users can explore the demo firmware for an initial experience and also develop your own custom firmware.

**T1000 Series Version Comparison**

<img src="https://media-cdn.seeedstudio.com/media/wysiwyg/upload/image2_20.png" alt="pir" width="800">

### Hardware <a href="#hardware-overview" id="hardware-overview"></a>

#### Diagram[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#diagram) <a href="#diagram" id="diagram"></a>

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/diagram.png" alt="pir" width="800">

#### Pin Descriptions[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#pin-descriptions) <a href="#pin-descriptions" id="pin-descriptions"></a>

| No. | Name  | Function                              | Description                                                        |
| --- | ----- | ------------------------------------- | ------------------------------------------------------------------ |
| 1   | P0.00 | XL1                                   | Connection for 32.768 kHz crystal                                  |
| 2   | P0.01 | XL2                                   | Connection for 32.768 kHz crystal                                  |
| 3   | P0.02 | <p>Digital I/O</p><p>Analog input</p> | Baterry level dectect                                              |
| 4   | P0.03 | <p>Digital I/O</p><p>Analog input</p> | Red LED IO                                                         |
| 5   | P0.04 | <p>Digital I/O</p><p>Analog input</p> | VCC voltage dectect                                                |
| 6   | P0.05 | <p>Digital I/O</p><p>Analog input</p> | Charger insert dectect,must be configured as no pullup or pulldown |
| 7   | P0.06 | Digital I/O                           | Key IO, must be configured as input\_pulldown                      |
| 8   | P0.07 | Digital I/O                           | LR1110 BUSY                                                        |
| 9   | P0.08 | Digital I/O                           | AG3335 VRTC EN                                                     |
| 10  | P0.09 | NFC input                             | NC                                                                 |
| 11  | P0.10 | NFC input                             | NC                                                                 |
| 12  | P0.11 | Digital I/O                           | SPI SCK                                                            |
| 13  | P0.12 | Digital I/O                           | SPI CS                                                             |
| 14  | P0.13 | Digital I/O                           | UART1 TX For AG3335                                                |
| 15  | P0.14 | Digital I/O                           | UART1 RX For AG3335                                                |
| 16  | P0.15 | Digital I/O                           | AG3335 RTC Interrupt                                               |
| 17  | P0.16 | Digital I/O                           | UART1 TX For debug                                                 |
| 18  | P0.17 | Digital I/O                           | UART1 RX For debug                                                 |
| 19  | P0.18 | Reset                                 | Reset                                                              |
| 20  | P0.19 | Digital I/O                           | QSPI Clock for FLASH                                               |
| 21  | P0.20 | Digital I/O                           | QSPI CS for FLASH                                                  |
| 22  | P0.21 | Digital I/O                           | QSPI IO0 for FLASH                                                 |
| 23  | P0.22 | Digital I/O                           | QSPI IO1 for FLASH                                                 |
| 24  | P0.23 | Digital I/O                           | QSPI IO2 for FLASH                                                 |
| 25  | P0.24 | Digital I/O                           | Green LED IO                                                       |
| 26  | P0.25 | Digital I/O                           | Buzzer PWM                                                         |
| 27  | P0.26 | Digital I/O                           | I2C SDA                                                            |
| 28  | P0.27 | Digital I/O                           | I2C SCL                                                            |
| 29  | P0.28 | <p>Digital I/O</p><p>Analog input</p> | NC                                                                 |
| 30  | P0.29 | <p>Digital I/O</p><p>Analog input</p> | Light Sensor ADC input                                             |
| 31  | P0.30 | <p>Digital I/O</p><p>Analog input</p> | NC                                                                 |
| 32  | P0.31 | <p>Digital I/O</p><p>Analog input</p> | Temperature Sensor ADC input                                       |
| 33  | P1.00 | Digital I/O                           | QSPI IO3 for FLASH                                                 |
| 34  | P1.01 | Digital I/O                           | LR1110 DIO9                                                        |
| 35  | P1.02 | Digital I/O                           | Accelerator Interrupt                                              |
| 36  | P1.03 | Digital I/O                           | Charger State                                                      |
| 37  | P1.04 | Digital I/O                           | Charger Done                                                       |
| 38  | P1.05 | Digital I/O                           | Buzzer Enable                                                      |
| 39  | P1.06 | Digital I/O                           | Sensor VCC Enable                                                  |
| 40  | P1.07 | Digital I/O                           | Accelerator Enable                                                 |
| 41  | P1.08 | Digital I/O                           | SPI MISO                                                           |
| 42  | P1.09 | Digital I/O                           | SPI MOSI                                                           |
| 43  | P1.10 | Digital I/O                           | LR1110 RESET                                                       |
| 44  | P1.11 | Digital I/O                           | AG3335 PWR EN                                                      |
| 45  | P1.12 | Digital I/O                           | AG3335 SLEEP Interrupt                                             |
| 46  | P1.13 | Digital I/O                           | Flash Enable                                                       |
| 47  | P1.14 | Digital I/O                           | AG3335 RESETB OUT                                                  |
| 48  | P1.15 | Digital I/O                           | AG3335 Reset                                                       |

### Demo Firmware <a href="#demo-firmware-overview" id="demo-firmware-overview"></a>

#### Positioning Description[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#positioning-description) <a href="#positioning-description" id="positioning-description"></a>

| **Location** | **Description**                                                                                                                                             |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GNSS         | <p>Upload longitude and latitude info.<br>(There is usually no GPS signal indoors, so it's recommended to test the device outdoors to get the location)</p> |
| Wi-Fi        | Upload the MAC address and RSSI info of the Wi-Fi AP.                                                                                                       |
| Bluetooth    | Upload the MAC address and RSSI info of the Bluetooth beacon.                                                                                               |

#### Button[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#button) <a href="#button" id="button"></a>

| **Button Action**        | **Description**                     |
| ------------------------ | ----------------------------------- |
| Long press for 3 seconds | Power on/off                        |
| Click button 3 times     | Switch on/off Bluetooth             |
| Double click             | Switch on/off SOS alart             |
| Click once               | Upload location/battery/sensor data |

#### LED[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#led) <a href="#led" id="led"></a>

<table><thead><tr><th valign="top">LED Status</th><th valign="top">Description</th><th></th></tr></thead><tbody><tr><td valign="top">Red LED</td><td valign="top">Solid</td><td>Charging</td></tr><tr><td valign="top">Flash</td><td valign="top">Abnormal charging</td><td></td></tr><tr><td valign="top">Green LED</td><td valign="top">Solid</td><td><p>Device in DFU mode.</p><p>Reboot the device to exit DFU mode(Press and hold the button, then release it immediately after connecting the charging cable)</p></td></tr><tr><td valign="top">On 500ms/Off 1s</td><td valign="top">Bluetooth on</td><td></td></tr><tr><td valign="top">Breath</td><td valign="top">Joining LoRaWAN network</td><td></td></tr><tr><td valign="top">Quick flash for 2s and then off</td><td valign="top">Joined the LoRaWAN network successfully</td><td></td></tr></tbody></table>

#### Sensor Function[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#sensor-function) <a href="#sensor-function" id="sensor-function"></a>

The SenseCAP T1000 Tracker is equipped with 3 sensors: Temperature sensor, Light sensor and 3-Axis Accelerometer. You can choose enable or disable these sensors:

note

When the sensors are turned on, the device will consume more power.

| **Sensor**           | **Description**                                                                                                                                                                                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Temperature          | <p>Onboard independent temperature sensor.</p><p>here may be some temperature measurement delay here, because it is separated from the shell.</p><p>Range: -20 to 60℃; Accuracy: ± 1℃(min 0.5℃, max 1℃); Resolution: 0.1℃</p>                                      |
| Light                | <p>The light sensor is not the actual lumen value monitored, but a percentage of the light from dark to amount. Mainly can be used for anti-demolition monitoring and some light sensitive monitoring.</p><p>Range: 0 to 100%, (0% is dark, 100% is brightest)</p> |
| 3-Axis Accelerometer | By setting the value of acceleration, motion event and shock event are triggered.                                                                                                                                                                                  |

#### Battery[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#battery) <a href="#battery" id="battery"></a>

Battery life depends on factors such as uplink interval, sensor usage, LoRa transmission distance, and operating temperature. Predicted battery life is based on a typical working environment (25°C) and serves as a reference. Actual battery life may vary.

**EU868(1C/SF12)**

| Upload Interval   | 1 minute | 5 minutes | 60 minutes | 1 day  |
| ----------------- | -------- | --------- | ---------- | ------ |
| Battery Life(day) | 2.46     | 11.72     | 84.68      | 184.86 |

**US915(1C/SF9)**

| Upload Interval   | 1 minute | 5 minutes | 60 minutes | 1 day  |
| ----------------- | -------- | --------- | ---------- | ------ |
| Battery Life(day) | 2.89     | 13.66     | 92.59      | 186.83 |

### Get Started[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#get-started) <a href="#get-started" id="get-started"></a>

Press the button for 3s to power on the device, a rising melody indicates that the device has been successfully powered on.

#### Connect via App[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#connect-via-app) <a href="#connect-via-app" id="connect-via-app"></a>

* **Step 1:** Download `SenseCraft` App

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Tracker/app_downlaod.png" alt="pir" width="500">

Login to the SenseCraft APP.

**tip:**

Select Server Location as `Global`.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/global-version.png" alt="pir" width="200">

* **Step 2:** Add Device

Click `Add Device` tab on the top right, then scan the QR code on the device label.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Tracker/config.png" alt="pir" width="800">

#### Configure the Device[​](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#configure-the-device) <a href="#configure-the-device" id="configure-the-device"></a>

* Navigate to `User` -> `Device Bluetooth Configuration` page.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/config-ppa.png" alt="pir" width="200">

* **Click the button 3 times** to enter the configuration mode. Device name: **T1000-E xxxx**(the last four digits of the MAC address).

**Quick Configuration**[**​**](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#quick-configuration)

For quick start with the `SenseCAP cloud`, you can select `Quick Configuration`.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/quick-config.png" alt="pir" width="800">

Configure the `Frequency Plan` according to your region, and set up the `Uplink Interval` you want.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/quick-1.png" alt="pir" width="200">

**Advanced Configuration**[**​**](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#advanced-configuration)

For advanced usage, please select `Advanced Configuration`.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/advan-config.png" alt="pir" width="800">

You can see the current device information, which includes the `device EUI`, `hardware/software version`, `battery`, etc.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/info-dev.png" alt="pir" width="250">

Navigate to `Settings` to set up the parameters.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/LoraWAN_Tracker/setting-page.png" alt="pir" width="600">

* **LoRa Setup**

<table><thead><tr><th></th><th valign="top">Parameters</th><th valign="top">Description</th></tr></thead><tbody><tr><td>Platform</td><td valign="top">SenseCAP for The Things Network（by default）</td><td valign="top"><p>A proprietary TTN server of SenseCAP. Out of the box when paired with a SenseCAP gateway.</p><p><a href="https://www.seeedstudio.com/LoRaWAN-Gateway-US915-p-4306.html">SenseCA Outdoor Gateway</a><br><a href="https://www.seeedstudio.com/SenseCAP-Multi-Platform-LoRaWAN-Indoor-Gateway-SX1302-US915-p-5472.html">SenseCA Indoor Gateway</a></p></td></tr><tr><td>SenseCAP for Helium</td><td valign="top"><p>A private Helium console of SenseCAP.</p><p>Out of the box with SenseCAP Mate App and Portal.</p></td><td valign="top"></td></tr><tr><td>Helium</td><td valign="top">Public Helium Server</td><td valign="top"></td></tr><tr><td>The Things Network</td><td valign="top">Public TTN Server</td><td valign="top"></td></tr><tr><td>Other Platform</td><td valign="top">Other LoRaWAN Network Server</td><td valign="top"></td></tr><tr><td>Frequency Plan</td><td valign="top">EU868/US915/AU915/KR920/IN865/AS923-1/AS923-2/AS923-3/AS923-4</td><td valign="top">EU868 by default</td></tr><tr><td>Packet Policy</td><td valign="top">1C</td><td valign="top">Enable by default</td></tr><tr><td>LoRaWAN ADR</td><td valign="top">Enable by default</td><td valign="top">Enable by default</td></tr><tr><td>Restore LoRa Configuration</td><td valign="top">Enable by default</td><td valign="top">Enable by default</td></tr></tbody></table>

* **General Setup**

<table><thead><tr><th></th><th valign="top">Parameters</th><th valign="top">Description</th></tr></thead><tbody><tr><td>3-axis accelerometer</td><td valign="top">Enable/Disable, disable by default</td><td valign="top">Upload the data of the 3-axis accelerometer</td></tr><tr><td>SOS Report Mode</td><td valign="top">Single(by default)</td><td valign="top">Upload data and report SOS event once.<br>Buzzer alarm for 3 seconds</td></tr><tr><td>Continuous</td><td valign="top">Upload data and report SOS event every minute, ends after 30 times.<br>Buzzer alarm for 30 seconds</td><td valign="top"></td></tr><tr><td>Uplink Interval(min)</td><td valign="top">1-10080min, 60min by default</td><td valign="top">Upload data at intervals.<br>The higher the frequency, the higher the power consumption</td></tr><tr><td>Geolocation Strategy</td><td valign="top">GNSS only(by default)</td><td valign="top">Uses only GPS satellite systems to determine the position</td></tr><tr><td>Wi-Fi only</td><td valign="top">Upload the MAC address and RSSI info of the Wi-Fi AP</td><td valign="top"></td></tr><tr><td>Bluetooth only</td><td valign="top">Upload the MAC address and RSSI info of the Bluetooth beacon</td><td valign="top"></td></tr><tr><td>GNSS + Wi-Fi</td><td valign="top">Uses GPS positioning first, if GPS fails, then uses Wi-Fi in one geolocation cycle</td><td valign="top"></td></tr><tr><td>Bluetooth + GNSS</td><td valign="top">Uses Bluetooth positioning first, if Bluetooth fails, then uses GNSS in one geolocation cycle</td><td valign="top"></td></tr><tr><td>Bluetooth + Wi-Fi</td><td valign="top">Uses Bluetooth positioning first, if Bluetooth fails, then uses Wi-Fi in one geolocation cycle</td><td valign="top"></td></tr><tr><td>Bluetooth + Wi-Fi + GNSS</td><td valign="top">Use Bluetooth, Wi-Fi and GNSS for positioning in turn (switch to the next type of positioning after one type of positioning fails)</td><td valign="top"></td></tr><tr><td>GNSS(GPS)</td><td valign="top">GNSS Max Scan Time(s)</td><td valign="top">10-120s, 30s by default</td></tr><tr><td>IBeacon Scan</td><td valign="top">Maximum number of BLE scans</td><td valign="top">3-5, 3 by default</td></tr><tr><td>Scan Timeout(s)</td><td valign="top">3-10s, 3s by default</td><td valign="top"></td></tr><tr><td>Group UUID(Hex)</td><td valign="top">Set UUID Filter, up to 16bytes.<br>Forexample, if set as '01 020304', it will filter beacons with thepattern'0102 03 04 xx xx xx ...'</td><td valign="top"></td></tr><tr><td>Wi-Fi Scan</td><td valign="top">Maximum number of Wi-Fi scans</td><td valign="top">3-5, 3 by default</td></tr></tbody></table>

#### Device Data View <a href="#device-data-view" id="device-data-view"></a>

**SenseCAP Mate App**[**​**](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#sensecap-mate-app)

Check the Location on the APP.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Tracker/data_view.png" alt="pir" width="800">

**SenseCAP Portal**[**​**](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#sensecap-portal)

The main function of the SenseCAP Portal is to manage SenseCAP devices and store data. It is built on Azure, a secure and reliable cloud service from Microsoft. Users can apply for an account and bind all devices to this account. The SenseCAP Portal provides a web portal and API. The web portal includes Dashboard, Device Management, Data Management, and Access Key Management. The API is open to users for further development.

* **Dashboard:** Including Device Overview, Announcement, Scene Data, and Data Chart, etc.
* **Device Management:** Manage SenseCAP devices.
* **Data Management:** Manage data, including Data Table and Graph section, providing methods to search for data.
* **Subaccount System:** Register subaccounts with different permissions.
* **Access Key Management:** Manage Access Key (to access API service), including Key Create, Key Update, and Key Check.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Tracker/portal_page.png" alt="pir" width="800">

**Device Data View**[**​**](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/#device-data-view-1)

Log in [SenseCAP Portal](http://sensecap.seeed.cc/)

If you have created an account through the APP, you can log in directly.

1\) Select register account, enter email information, and click "register", the registered email will be sent to the user's mailbox

2\) Open the "SenseCAP…"Email, click the jump link, fill in the relevant information, and complete the registration

3\) Return to the login interface and complete the login

Check [SenseCAP Portal User Guide](https://sensecap-docs.seeed.cc/quickstart.html) for more details.

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Tracker/portaldata1.png" alt="pir" width="800">

&#x20;

<img src="https://files.seeedstudio.com/wiki/SenseCAP/Tracker/map_view2.png" alt="pir" width="800">

## Official documentation and development resources

Use [Get Started with LoRaWAN Tracker](https://wiki.seeedstudio.com/get_started_with_lorawan_tracker/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                                             | Model-specific reference                                                                                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Official source: Seeed-Tracker-T1000-E-for-LoRaWAN-dev-board | [Read official source: seeed-tracker-t1000-e-for-lorawan-dev-board](https://github.com/Seeed-Studio/Seeed-Tracker-T1000-E-for-LoRaWAN-dev-board) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
