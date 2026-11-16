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

# Waveshare ESP8266 for Raspberry Pi Pico Wifi Module TCP UDP

### Waveshare ESP8266 for Raspberry Pi Pico Wifi Module TCP UDP

***

### Product Link

{% embed url="https://openelab.io/products/esp8266forraspberrypipicowifimodule" %}

### Overview

The Pico-ESP8266 is a WiFi expansion module designed for Raspberry Pi Pico, which can be controlled via UART AT command, and supports TCP/UDP communication protocol. It is an easy solution to enable WiFi feature for Raspberry Pi Pico, suitable for sorts of IoT communication projects.

### Features

* Standard Raspberry Pi Pico header supports Raspberry Pi Pico series.
* UART communication, controlled via AT command, helps you get started quickly.
* Supports STA, AP, and STA+AP three WiFi operating modes, embedded LWIP protocol stack, supports TCP/UDP communication.
* Based on ESP8266 module, four-layers process, enhanced impedance matching, stronger signal, more stable connection.
* 2 x functional buttons, convenient for the user to update AT firmware through Raspberry Pi Pico.
* Comes with online development resources and manual (Raspberry Pi Pico C/C++ and MicroPython examples).

### Specification

* Communication interface: UART
* UART baud rate: 115200 bps
* WIFI standard: IEEE 802.11b/g/n
* Frequency range: 2400 \~ 2483.5MHz
* WIFI operating mode: WiFi STA, WiFi AP, WiFi STA+AP
* Antenna: PCB antenna
* Operating voltage: 3.3V
* Operating temperature: -40°C \~ 85°C
* Dimensions: 58 x 25mm

### Pinout

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-details-inter.jpg&#x26;width=600" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="https://www.waveshare.com/w/upload/0/0c/Pico_ESP8266_Spec02.jpg" alt=""><figcaption></figcaption></figure>

### Quick start

#### Hardware connection

1. Press and hold the BOOTSEL button of Pico, the pico will be recognized as a movable disk, copy the dev\_cdc\_ports.uf2 file from demo codes to the Pico, the Pico will automatically restart and work as the USB to serial adapter.
2. Connect the Pico\_EPS8266 board to Pico, then connect the Pico to PC by USB cable.
3. Open an SSCOM software, choose the correct COM port, and set the baud rate to 115200.
4. Test the module by AT command.

<figure><img src="https://www.waveshare.com/w/upload/e/ec/Pico-ESP8266-01.png" alt=""><figcaption></figcaption></figure>

#### AT commands

* 1\. AT:

```
AT
Response:
AT
OK
```

* 2\. AT+RST Restart device:

```
AT+RST
Response:
AT+RST
OK
```

* 3\. AT+GMR Check version:

```
AT+GMR
Response:
AT+GMR
AT version:1.2.0.0(Jul  1 2016 20:04:45)
SDK version:1.5.4.1(39cb9a32)
Ai-Thinker Technology Co. Ltd.
v1.5.4.1-a Nov 30 2017 15:54:29
OK
```

#### TCP Client

* 1\. Configure WiFi mode.

```
AT+CWMODE=3	//softAP+station mode
Response: :
OK
```

* 2\. Connect to the router.

```
AT+CWJAP="SSID","password"	//SSID and password of the router
Response: :
AT+CWJAP="SSID","password"
OK
```

If it succeeds in connecting the WIFI, it will respond and get an IP address.

```
WIFI CONNECTED
WIFI GOT IP
```

* 3\. Check the IP address of ESP8266.

```
AT+CIFSR
Response: :
+CIFSR:APIP,"192.168.4.1"
+CIFSR:APMAC,"1a:fe:34:a5:8d:c6"
+CIFSR:STAIP,"192.168.3.133"
+CIFSR:STAMAC,"18:fe:34:a5:8d:c6"

OK
```

* 4\. PC and ESP8266 are connected to the same router, use the network debugging tool on the PC end, and establish a TCP server.

For example, build a server on a PC with IP address 192.168.3.116 and port 8080.

* 5\. ESP8266 works as a TCP client and connects to the server.

```
AT+CIPSTART="TCP","192.168.3.116",8080		 //protocol, server IP and port
Response :
CONNECT
OK
```

* 6\. ESP8266 device ends data of a specified length to the server.

```
AT+CIPSEND=4                            //set date length which will be sent, such as 4 bytes	
>test                                   //enter the data, no CR
Response :
Recv 4 bytes
SEND OK
```

* 7\. The data is printed if ESP8266 receives data from the server.

```
+IPD,n:xxxxxxxxxx				//received n bytes, data=xxxxxxxxxxx
```

* 8\. Enable the transparent transmission mode, data can be directly transmitted

```
AT+CIPMODE=1
Response :
OK
```

* 9\. If the transparent transmission mode is enabled, data can be directly transmitted

```
AT+CIPSEND	

>	 //From now on, data received from UART will be	transmitted to	the server automatically.
```

* 10\. Exit sending data:

If +++ is detected in a single packet of data during transparent transmission, the system stops transparent transmission.<br>

\- If you use the keyboard to type +++, it may take too long and is not considered as three consecutive + s. You are advised to use a serial port tool to send +++ at a time and not carry invisible characters such as Spaces or newlines.\
\- Please send the next AT command AT least one second later

* 11\. Exit the transparent transmission mode.

```
AT+CIPMODE=0
Response :
OK
```

* 12\. Disconnect TCP.

```
AT+CIPCLOSE
Response :
CLOSED
```

```
OK
```

#### TCP Server

* 1\. Configure WiFi mode:

```
AT+CWMODE=3	//softAP+station mode
Response :
OK
```

* 2\. Connect to router:

```
AT+CWJAP="SSID","password"	//SSID and password of the router
Response :
OK
```

* 3\. Check the IP address of the ESP8266 device:

```
AT+CIFSR
Response :
+CIFSR:APIP,"192.168.4.1"
+CIFSR:APMAC,"1a:fe:34:a5:8d:c6"
+CIFSR:STAIP,"192.168.3.133"
+CIFSR:STAMAC,"18:fe:34:a5:8d:c6"
OK
```

* 4\. Enable multiple connection:

```
AT+CIPMUX=1
Response :
OK
```

Note: If "IPMODE must be 0" appears, it is necessary to disconnect ESP8266 and then enter the command. If not, press the button or power off to restart the module and then operate it again.

* 5\. Build TCP server

```
AT+CIPSERVER=1	 	 //	default	port	=	333
Response :
OK
```

* 6\. The PC and THE ESP8266 are connected to the same router. Use the network debugging tool on the PC to establish a TCP client and connect to the TCP server of the ESP8266.
* 7\. Send data:

```
//ID number of connection is	defaulted	to be 0.
AT+CIPSEND=0,4   //send 4	bytes to connection NO.0
>test            //enter the	data, no CR
Response :
Recv 4 bytes

SEND OK
```

* 8\. When the ESP8266 device receives data from the server, the following message is displayed:

```
+IPD,0,n:xxxxxxxxxx	 //received n bytes,	 data=xxxxxxxxxxx
```

* 9\. Disconnect TCP:

```
AT+CIPCLOSE
Response :
CLOSED
OK
```

#### UDP

UDP transmission does not distinguish between server and client and is established by the AT+CIPSTART command.

* 1\. Configure WiFi mode.

```
AT+CWMODE=3	//softAP+station mode
Response :
OK
```

* 2\. Connect to the router.

```
AT+CWJAP="SSID","password"	//SSID and password of router
Response :
AT+CWJAP="SSID","password"
OK
```

If the connection is normal, it may prompt you to connect to WIFI and obtain the IP address.

```
WIFI CONNECTED
WIFI GOT IP
```

* 3\. Example Query the IP address of the ESP8266.

```
AT+CIFSR
Response :
+CIFSR:APIP,"192.168.4.1"
+CIFSR:APMAC,"1a:fe:34:a5:8d:c6"
+CIFSR:STAIP,"192.168.3.133"
+CIFSR:STAMAC,"18:fe:34:a5:8d:c6"

OK
```

* 4\. The PC and the ESP8266 are connected to the same router. Use the network debugging tool on the PC to set up a TCP server.

For example, build a server on a PC with IP 192.168.3.116, and the port is set as 8080.

* 5\. Enable multiple connections.

```
AT+CIPMUX=1
Response :
OK
```

Note: If "IPMODE must be 0" appears, it is necessary to disconnect ESP8266 and then enter the command. If not, press the button or power off to restart the module and then operate it again.

* 6\. Create a UDP transport. For example, to assign a joined number of 4, the instruction is as follows：

```
AT+CIPSTART=4,"UDP","192.168.101.110",8080,1112,0
Response :
4, CONNECT	

OK
```

Note：\
About the command：<br>

* "192.168.101.110", 8080 is the remote IP and port transmitted, that is the UDP port built in step 4;
* 1112 is the local UDP port of ESP8266, it is configurable, or a random port
* 0 Indicates that after the current UDP transmission is established, the UDP remote device will not be changed by other devices. Even if other devices send data to ESP8266 UDP port 1112 through UDP protocol, the remote end of THE UDP transmission no. 4 of ESP8266 will not be replaced. If the command "AT+CIPSEND=4, X" is used to send data, the current PC will still receive the data.
* 7\. Send data

```
AT+CIPSEND=4,7	 //Send 7 bytes to transmission NO.4	
>UDPtest  // enter the data, no CR
Response :
Recv 7 bytes
SEND OK
```

Note：

• When sending data, if the number of bytes entered exceeds the set length（n）：\
\- The system prompts BUSY, sends the first N bytes of data, and responds SEND OK when the sending is complete.\
\- The data that exceeds the length is considered invalid and is not accepted.

* 8\. Receive data. When the ESP8266 device receives data from the server, the following information is displayed:

```
+IPD,4,n:xxxxxxxxxx		 //received n bytes,	data=xxxxxxxxxxx
```

* 9\. If the transparent transmission mode is enabled, data can be directly transmitted.

```
AT+CIPMODE=1
Response :
OK
```

* 10\. The ESP8266 device transmits data to the server through transmission

```
AT+CIPSEND	

>	 //From now on, data received from UART will be	transmitted to the server automatically.
```

* 11\. Exit sending data:

If +++ is detected in a single packet of data during transparent transmission, the system stops transparent transmission.

\- If you use the keyboard to type +++, it may take too long and is not considered as three consecutive + s. You are advised to use a serial port tool to send +++ at a time and not carry invisible characters such as Spaces or newlines.\
\- After that, send the next AT command AT least one second later.

* 12\. Exit the transparent transmission mode

```
AT+CIPMODE=0
Response :
OK
```

* 13\. Disconnect UDP transmission

```
AT+CIPCLOSE=4
Response :
4, CLOSED
OK
```

### MicroPython Example

Before Pico can run MicroPython programs, you need to download the MicroPython firmware, install the Thonny IDE, and configure the motherboard environment with the Rasberry Pi option.

#### TCP Client

* Open the TCP\&UDP test tool, create the server, and start the server.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-TCP-1.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* Open tcp\_client.py in Thonny IDE and change the SSID and password to the actual WiFi account and password. Change the values of ServerIP and Port in the program to the IP and Port of the actual TCP server.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-02.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* Click run program. After running, the program will connect to WiFi and send data to the server. The information sent by the server is displayed in the shell.

#### TCP Server

* Open the tcp\_server.py program in Thonny IDE and change SSID and password values to the actual WiFi account password.
* Click to run the program. After the program runs, it will connect to WiFi and start the server. The SHELL displays the STAIP address of ESP8266.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-05.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* Open the TCP\&UDP test tool, create a connection, set the type to TCP, and target IP to the STAIP address displayed in the shell, port 8080.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-06.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* Click the "connect" button to connect to the server. After a normal connection, the icon changes from a blue dot to a green triangle.

#### UDP

* Open the TCP\&UDP test tool, create a connection, and select UDP as the type, the destination IP address is the STAIP address displayed in the shell after running the program, the port is 1112, and the local port is 8087. Select Create and Connect.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-04.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* Open the tcp\_server.py program in Thonny IDE and change the SSID and password to the actual WiFi account and password. Set remote\_IP to the actual IP address of the computer

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pico-ESP8266-08.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* After the program runs, it will connect to WiFi and send data to UDP on the computer side. Enter a string in the send area and send it. ESP8266 receives the message and sends it back for display in the receiving area. The shell port will also display the received information.

#### C/C++ codes

* C/C++ is compiled in Raspberry PI. This step can be skipped if the Pico compilation environment has been configured for Raspberry PI. If the Pico compilation environment has not been configured, perform the following operations.

```
wget 
chmod +x pico_setup.sh
./pico_setup.sh
```

* Download the demo codes:

```
cd ~
wget  
unzip Pico-ESP8266.zip
cp -r Pico-ESP8266/c/pico-esp8266  pico
```

* Before compiling the program, you need to modify the program and change the values of SSID and password to the actual WiFi account password. Change the values of ServerIP and Port in the program to the IP and Port of the actual TCP server.
* Compiler:

```
cd pico/pico-esp8266/build
cmake ..
make
```

#### Download AT Firmware

* Hold the Pico's BOOTSEL button and power on. The computer will recognize a USB flash drive and copy the dev\_CDC\_ports.uf2 file from the sample program to the flash drive to download the program. The Pico will become a USB-to-serial device.
* Run the flash\_download\_tool software.

<figure><img src="https://www.waveshare.com/w/upload/5/5d/Pico-ESP8266-11.png" alt=""><figcaption></figcaption></figure>

* The factory default of the module is C1.5.4.1 AT firmware 32Mbit version. Select ai-thinker\_esp8266\_dout\_32mbit\_V1.5.4.1 -a\_20171130.bin and set the address to 0x0. Set SPI SPEED to 40MHz, SPI MODE to DOUT, and FLASH SIZE to 32Mb-C1.

<figure><img src="https://www.waveshare.com/w/upload/a/a0/Pico-ESP8266-12.png" alt=""><figcaption></figcaption></figure>

* Hold the IO0 button of the PICo-ESP8266 and then press the RESET button to enter download mode. Select the corresponding serial port and set the baud rate to 115200. Click START and wait for the download to complete.
* To set the AT firmware for nonOS\_AT\_BIN\_V1.7.4, follow the following figure.

<figure><img src="https://www.waveshare.com/w/upload/5/5a/Pico-ESP8266-013.png" alt=""><figcaption></figcaption></figure>

### Resource

#### Document

* [Schematic](https://files.waveshare.com/upload/7/74/Pico-ESP8266_Schematic.pdf)
* [ESP8266 AT Instruction Set](https://files.waveshare.com/upload/8/86/Esp8266_at_instruction_set_en.pdf)
* [ESP8266 AT Command example](https://files.waveshare.com/upload/1/15/Esp8266_at_command_examples_en.pdf)
* [More...](https://docs.ai-thinker.com/en/esp8266)

#### Examples

* [Demo codes](https://files.waveshare.com/upload/4/41/Pico-ESP8266.zip)

#### Software

* [Thonny Python IDE (Windows V3.3.3)](https://files.waveshare.com/upload/7/73/Thonny-3.3.3.zip)
* [TCP/UDP Debug software](https://files.waveshare.com/upload/8/8a/Tcpudpdbg.zip)
* [Flash Download tool](https://files.waveshare.com/upload/d/d2/Flash_download_tool_v3.8.5_1.zip)
* [AT firmware](https://files.waveshare.com/upload/3/37/Pico-ESP8266_AT%E5%9B%BA%E4%BB%B6.zip)
* [TCP232](https://www.waveshare.com/wiki/File:TCP232.7z)

### Pico Quick Start

#### Download Firmware

* MicroPython Firmware Download

Expand

* C\_Blink Firmware Download

Expand

### Video Tutorial

* Pico Tutorial I - Basic Introduction

Expand

* Pico Tutorial II - GPIO

Expand

* Pico Tutorial III - PWM

Expand

* Pico Tutorial IV - ADC

Expand

* Pico Tutorial V - UART

Expand

* Pico Tutorial VI - To be continued...

### Text Tutorial

#### Introduction

* [Raspberry Pi Pico](https://www.waveshare.com/wiki/Raspberry_Pi_Pico)

#### MicroPython Series

* [【MicroPython】 machine.Pin Function](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91_Machine.Pin_Functions)
* [【MicroPython】 machine.PWM Function](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91machine.PWM_Function)
* [【MicroPython】 machine.ADC Function](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91machine.ADC_Function)
* [【MicroPython】 machine.UART Function](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91machine.UART_Function)
* [【MicroPython】 machine.I2C Function](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91machine.I2C_Function)
* [【MicroPython】 machine.SPI Function](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91machine.SPI_Function)
* [【MicroPython】 rp2.StateMachine](https://www.waveshare.com/wiki/%E3%80%90MicroPython%E3%80%91PIO_Function)

#### C/C++ Series

* [【C/C++】 Windows Tutorial 1 - Environment Setting](https://www.waveshare.com/wiki/Pico_C/C%2B%2B_Windows_Tutorial_1)
* [【C/C++】 Windows Tutorial 2 - Create New Project](https://www.waveshare.com/wiki/Pico_C/C%2B%2B_Windows_Tutorial_2)

#### Arduino IDE Series

**Install Arduino IDE**

1.  Download the Arduino IDE installation package from [Arduino website](https://www.arduino.cc/).<br>

    <figure><img src="https://www.waveshare.com/w/upload/c/ce/RoArm-M1_Tutorial_II01.jpg" alt=""><figcaption></figcaption></figure>
2.  Just click on "JUST DOWNLOAD".<br>

    <figure><img src="https://www.waveshare.com/w/upload/1/13/Arduino_IDE_Pico.png" alt=""><figcaption></figcaption></figure>
3.  Click to install after downloading.<br>

    <figure><img src="https://www.waveshare.com/w/upload/9/9e/RoArm-M1_Tutorial_II02.gif" alt=""><figcaption></figcaption></figure>
4. Note: You will be prompted to install the driver during the installation process, we can click Install.

**Install Arduino-Pico Core on Arduino IDE**

1.  Open Arduino IDE, click the File on the left corner and choose "Preferences".<br>

    <figure><img src="https://www.waveshare.com/w/upload/9/9e/RoArm-M1_Tutorial04.jpg" alt=""><figcaption></figcaption></figure>
2.  Add the following link in "Additional boards manager URLs", then click OK.<br>

    ```
    https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
    ```

    \
    Note: If you already have the ESP32 board URL, you can separate the URLs with commas like this:

    ```
    https://dl.espressif.com/dl/package_esp32_index.json,https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
    ```

    <figure><img src="https://www.waveshare.com/w/upload/e/e2/RoArm-M1_Tutorial_II05.jpg" alt=""><figcaption></figcaption></figure>
3. Click on Tools -> Board -> Board Manager -> Search for pico, it shows installed since my computer has already installed it.

<figure><img src="https://www.waveshare.com/w/upload/5/5f/Pico_Get_Start_05.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/a/ad/Pico_Get_Start_06.png" alt=""><figcaption></figcaption></figure>

**Upload Demo At the First Time**

1.  Press and hold the BOOTSET button on the Pico board, connect the Pico to the USB port of the computer via the Micro USB cable, and release the button when the computer recognizes a removable hard drive (RPI-RP2).<br>

    <figure><img src="https://www.waveshare.com/w/upload/4/45/Pico_Get_Start.gif" alt=""><figcaption></figcaption></figure>
2. Download the demo, open the D1-LED.ino under arduino\PWM\D1-LED path.
3.  Click Tools -> Port, remember the existing COM, do not need to click this COM (different computers show different COM, remember the existing COM on your computer).<br>

    <figure><img src="https://www.waveshare.com/w/upload/2/24/UGV1_doenload02EN.png" alt=""><figcaption></figcaption></figure>
4.  Connect the driver board to the computer with a USB cable, then click Tools -> Ports, select uf2 Board for the first connection, and after the upload is complete, connecting again will result in an additional COM port.<br>

    <figure><img src="https://www.waveshare.com/w/upload/7/7a/UGV1_doenload03EN.png" alt=""><figcaption></figcaption></figure>
5.  Click Tools -> Board -> Raspberry Pi Pico/RP2040 -> Raspberry Pi Pico.<br>

    <figure><img src="https://www.waveshare.com/w/upload/9/91/Pico_Get_Start02.png" alt=""><figcaption></figcaption></figure>
6.  After setting, click the right arrow to upload.<br>

    * If you encounter problems during the period, you need to reinstall or replace the Arduino IDE version, uninstall the Arduino IDE clean, after uninstalling the software you need to manually delete all the contents of the folder C:\Users\\\[name]\AppData\Local\Arduino15 (you need to show the hidden files in order to see it) and then reinstall.

    <figure><img src="https://www.waveshare.com/w/upload/f/f3/Pico_Get_Start03.png" alt=""><figcaption></figcaption></figure>

#### Open Source Demo

* [MicroPython Demo (GitHub)](https://github.com/waveshareteam/Pico_MircoPython_Examples)
* [MicroPython Firmware/Blink Demo (C)](https://files.waveshare.com/upload/b/b2/Raspberry_Pi_Pico_Demo.zip)
* [Official Raspberry Pi C/C++ Demo](https://github.com/raspberrypi/pico-examples/)
* [Official Raspberry Pi MicroPython Demo](https://github.com/raspberrypi/pico-micropython-examples)
* [Arduino Official C/C++ Demo](https://github.com/earlephilhower/arduino-pico)
