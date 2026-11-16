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

# Waveshare SIM7070G NB-IoT / Cat-M / GPRS / GNSS HAT for Raspberry Pi

### Waveshare SIM7070G NB-IoT / Cat-M / GPRS / GNSS HAT for Raspberry Pi

***

### Product Link

{% embed url="https://openelab.io/products/sim7070gnb-iotcat-mgprsgnsshat" %}

### Introduction

This is a telecommunication HAT for Raspberry Pi which supports global bands of NB-IoT, Cat-M, and GPRS, as well as GNSS positioning function. Due to its advantages such as small size, low delay, and wide coverage, it is the ideal choice for IoT applications such as intelligent instruments, asset tracking, remote monitoring, e-health, and so on.

Compared to SIM7080G, this module also supports GPRS (2G); compared to SIM7000C/E, it is more generic due to the global bands support.

### Features

* Standard Raspberry Pi 40PIN GPIO extension header, supports Raspberry Pi series boards<br>
* Supports communication protocols such as TCP/UDP/HTTP/HTTPS/TLS/DTLS/PING/LWM2M/COAP/MQTT<br>
* Supports GNSS positioning (GPS, BeiDou, GLONASS, Galileo)<br>
* Onboard USB interface, to test AT Commands, get GPS positioning data, and so on<br>
* Breakout UART control pins, to connect with host boards like Arduino/STM32<br>
* SIM card slot supports ONLY 1.8V SIM card (3V SIM card is not available)<br>
* 2x LED indicators, easy to monitor the working status<br>
* Baudrate: 300\~3686400 bps<br>
* Common baud rate auto-negotiation: 9600/19200/38400/57600/115200 bps<br>
* Comes with development resources and manual (examples for Raspberry Pi/Arduino/STM32)

### Specifications

| **NB-IOT/CAT-M/2G**                                                      |                                                                       |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| Band                                                                     | NB-IoT: B1/B2/B3/B4/B5/B8/B12/B13/B18/B19/B20/B25/B26/B28/B66/B71/B85 |
| Cat-M: B1/B2/B3/B4/B5/B8/B12/B13/B14/B18/B19/B20/B25/B26/B27/B28/B66/B85 |                                                                       |
| GSM/GPRS/EDGE: 850/900/1800/1900MHz                                      |                                                                       |
| Data rate                                                                | NB-IoT: 136Kbps(DL)/150Kbps(UL)                                       |
| Cat-M: 589Kbps(DL)/1119Kbps(UL)                                          |                                                                       |
| GPRS: 85.6Kbps(DL)/85.6Kbps(UL)                                          |                                                                       |
| EDGE: 236.8Kbps(DL)/236.8Kbps(UL)                                        |                                                                       |
| SIM card support                                                         | NB-IoT/Cat-M/2G card (1.8V SIM card ONLY)                             |
| Applicable region                                                        | global                                                                |
| **GNSS**                                                                 |                                                                       |
| Receiver type                                                            | 16-channel                                                            |
| C/A Code                                                                 |                                                                       |
| Band                                                                     | GPS L1: 1575.42 ± 1.023MHz                                            |
| GLONASS L1: 1598.0625 \~ 1605.375MHz                                     |                                                                       |
| BDS B1: 1559.052 \~ 1591.788MHz                                          |                                                                       |
| Galileo L1: 1575.42 ± 1.023MHz                                           |                                                                       |
| Data format                                                              | NMEA-0183                                                             |
| Antenna                                                                  | Active antenna                                                        |
| **OTHER**                                                                |                                                                       |
| Power supply                                                             | 5V                                                                    |
| Operating voltage                                                        | 5V / 3.3V (configured via 0Ω resistor)                                |
| Current consumption                                                      | about 41mA (idle mode)                                                |
| Operating temperature                                                    | -40°C \~ 85°C                                                         |
| Storage temperature                                                      | -45°C \~ 90°C                                                         |
| Dimensions                                                               | 30.50mm × 65.00mm                                                     |

### Pinout

<figure><img src="../../.gitbook/assets/image (457).png" alt=""><figcaption></figcaption></figure>

### Dimensions

Dimensions：30.50mm × 65.00mm

Weight: 0.148 kg

<figure><img src="../../.gitbook/assets/image (458).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### Use it with Raspberry Pi

Initialize IO and install software

The PWRKEY pin is connected to P7 (wiringPi number) of Raspberry Pi by jumper. To let the SIM7080G board work normally, you should firstly initialize the P7 pin. Download codes and run by the following commands.

```
sudo apt-get update
sudo pip install RPi.GPIO
sudo apt-get install python-serial
wget -P ~/Documents/ https://files.waveshare.com/upload/4/4a/SIM7080G_Cat_M_NB_IoT_HAT_Code.tar.gz
cd ~/Documents
tar -xzf SIM7080G_Cat_M_NB_IoT_HAT_Code.tar.gz
sh ~/Documents/SIM7080G_Cat_M_NB_IoT_HAT_Code/RaspberryPi/pi_gpio_init.sh
```

Enable UART and hardware connection.

Open raspi-config by following commands, and choose Interfacing Options -> Serial, close login shell and open the hardware serial port.

```
sudo rapsi-config
```

[![L76X GPS Module rpi serial.png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=L76X_GPS_Module_rpi_serial.png\&width=600)](https://www.waveshare.com/wiki/File:L76X_GPS_Module_rpi_serial.png)[![SIM7070G-Cat-M-NB-IoT-GPRS-HAT-003.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7070G-Cat-M-NB-IoT-GPRS-HAT-003.jpg\&width=600)](https://www.waveshare.com/wiki/File:SIM7070G-Cat-M-NB-IoT-GPRS-HAT-003.jpg)Python codes

The python codes is provided for MQTT function.

```
cd ~/Documents/SIM7080G_Cat_M_NB_IoT_HAT_Code/RaspberryPi/python/mqtt/
sudo python mqtt.py
```

[![SIM7070G-Cat-M-NB-IoT-GPRS-HAT-011.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7070G-Cat-M-NB-IoT-GPRS-HAT-011.jpg\&width=1200)](https://www.waveshare.com/wiki/File:SIM7070G-Cat-M-NB-IoT-GPRS-HAT-011.jpg)

#### Use it with STM32

The demo codes provided is based on Waveshare Open103C, it is use for TCP connecting.

[![SIM7070G-Cat-M-NB-IoT-GPRS-HAT-012.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7070G-Cat-M-NB-IoT-GPRS-HAT-012.jpg\&width=500)](https://www.waveshare.com/wiki/File:SIM7070G-Cat-M-NB-IoT-GPRS-HAT-012.jpg)[![SIM7070G-Cat-M-NB-IoT-GPRS-HAT-014.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7070G-Cat-M-NB-IoT-GPRS-HAT-014.jpg\&width=600)](https://www.waveshare.com/wiki/File:SIM7070G-Cat-M-NB-IoT-GPRS-HAT-014.jpg)

#### Use it with Arduino

The demo codes provide is based on Arduino UNO. The D10 (RX) and D11 (TX) is used for software serial.

[![SIM7070G-Cat-M-NB-IoT-GPRS-HAT-013.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7070G-Cat-M-NB-IoT-GPRS-HAT-013.jpg\&width=600)](https://www.waveshare.com/wiki/File:SIM7070G-Cat-M-NB-IoT-GPRS-HAT-013.jpg)[![SIM7080G Cat-M NB-IoT HAT 015.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7080G_Cat-M_NB-IoT_HAT_015.jpg\&width=600)](https://www.waveshare.com/wiki/File:SIM7080G_Cat-M_NB-IoT_HAT_015.jpg)

### FAQ



<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7070G_Cat-M/NB-IoT/GPRS_HAT#accordion3"><strong>Can SIM7070G use cellular network and GPS positioning at the same time?</strong></a></summary>

SIM7080X and SIM7070X series cannot connect to cellular networks and GPS positioning at the same time.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7070G_Cat-M/NB-IoT/GPRS_HAT#accordion1"><strong>SIM card type?</strong></a></summary>

Support 25mm X 15mm SIM standard card as shown in the picture below, if it is a Micro or Nano card you need to add a card holder.\
[![SIM7070G Cat-M-FAQ.jpg](https://www.waveshare.com/w/upload/8/81/SIM7070G_Cat-M-FAQ.jpg)](https://www.waveshare.com/wiki/File:SIM7070G_Cat-M-FAQ.jpg)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7070G_Cat-M/NB-IoT/GPRS_HAT#accordion4"><strong>Why is there no signal from SIM7070G?</strong></a></summary>



* Fixed NB-IOT or CAT-M Easier to get the signal:

```
AT+CMNB=2 //Fixed NB-IOT
AT+CMNB=1 //Fixed CAT-M
```

* Fixed LTE mode can register to the network faster:

```
AT+CNMP=38
```

Please refer to the following manual for specific instructions: [SIM7070\_SIM7080\_SIM7090\_Series\_AT\_Command\_Manual\_V1.03](https://www.waveshare.com/w/upload/0/02/SIM7070_SIM7080_SIM7090_Series_AT_Command_Manual_V1.03.pdf)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7070G_Cat-M/NB-IoT/GPRS_HAT#accordion2"><strong>Why didn't the module Raspberry Pi return when the minicom sent the AT command?</strong></a></summary>

SIM7070G may get stuck when it is first turned on, send AT commands several times until it returns OK.\
[![SIM7070G Cat-M-FAQ02.png](https://www.waveshare.com/w/upload/8/85/SIM7070G_Cat-M-FAQ02.png)](https://www.waveshare.com/wiki/File:SIM7070G_Cat-M-FAQ02.png)

</details>
