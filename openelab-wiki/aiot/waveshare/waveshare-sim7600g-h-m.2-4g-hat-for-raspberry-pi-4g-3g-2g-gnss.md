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

# Waveshare SIM7600G-H M.2 4G HAT for Raspberry Pi 4G/3G/2G GNSS

{% hint style="info" %}
[**View Waveshare SIM7600G-H M.2 4G HAT for Raspberry Pi 4G/3G/2G GNSS on OpenELAB**](https://openelab.io/products/sim7600g-h-hat)

**Store SKU / option:** `Waveshare-21707`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare SIM7600G-H M.2 4G HAT for Raspberry Pi 4G/3G/2G GNSS

***

### Product Link

{% embed url="https://openelab.io/products/sim7600g-h-hat" %}

### Introduction

Prohibited by the module manufacturer SIMCOM, we're not allowed to ship this product or to provide any tech support, to the following countries/regions: Iran, North Korea, Cuba, Sudan, and Syrian. SIM7600G-H M.2 4G HAT For Raspberry Pi, LTE CAT4 High Speed, Global Coverage Multi-Band, 4G/3G/2G Compatible, GNSS

<figure><img src="../../.gitbook/assets/image (456).png" alt=""><figcaption></figcaption></figure>

### Features

* Supports dial-up, phone call, SMS, TCP, UDP, MQTT, HTTP(S), FTP(S), and so on.
* GNSS positioning: GPS, Beidou, Glonass, Galileo, QZSS, LBS base station.
* USB 3.1 port (USB 2.0 compatible) for connecting to PC, Raspberry Pi, or Jetson Nano host board to enable high speed 4G communication.
* Onboard UART, PWR, and RST control pin, built-in voltage level translator, enabled via DIP switch, for use with hosts like Raspberry Pi or Arduino.
* Onboard USB-C connector, enabled via switch, for connecting standalone power supply for the module, allows more loads, stable amd flexible power supply.
* Onboard power supply on/off switch, reset button and LED indicator, easy to turn on/off the module or monitor the operating status.
* Reserved 4x SMA to IPEX antenna interfaces, with pre-soldered 2x connectors for easily using antennas, allows changing the SMA antenna position.
* Onboard audio jack and audio decoder, allows audio operation like making phone call.
* High efficiency power supply circuit, up to 3A output current.

### Specifications

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM8202G-M2-5G-HAT-B-details-intro.jpg&#x26;width=800" alt=""><figcaption></figcaption></figure>

| Number | Name                     | Description                                                                                                                                                                                                                                                               |
| ------ | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ①      | Raspberry Pi GPIO Header | Easily connect to Raspberry Pi                                                                                                                                                                                                                                            |
| ②      | Switch                   | Enable the corresponding pin                                                                                                                                                                                                                                              |
| ③      | M.2 Interface            | Compatible with RM500U-CN/RM500Q-CN/RM500Q-GL/RM50XQ-AE and other series of 5G modules                                                                                                                                                                                    |
| ④      | SIM Card Holder          | Onboard two SIM card slots, dual card single standby. The default SIM1 card slot works, SIM2 is on the back, requires module support and must be switched through AT commands                                                                                             |
| ⑤      | USB 3.1 Connector        | Backward compatible with USB 2.0, can be used to connect to PC/Raspberry Pi/Jetson Nano, etc.                                                                                                                                                                             |
| ⑥      | USB Type-C Connector     | 5V 3A input; stable and flexible power supply                                                                                                                                                                                                                             |
| ⑦      | Audio Port               | SIM82XX series support audio function, RM50XX series do not support this audio function                                                                                                                                                                                   |
| ⑧      | Antenna Connector        | Onboard four-way antenna, strong signal                                                                                                                                                                                                                                   |
| ⑨      | Reset Switch             | One-key reset                                                                                                                                                                                                                                                             |
| ⑩      | Power Switch             | <p>To facilitate the power supply mode of the control module:</p><p>——If set to USB, the module will provide power through the "⑤.USB3.1 interface";<br>——If set to EXT PWR, the module will provide power through the "⑥.USB Type-C interface" external power supply</p> |
| ⑪      | Cooling Fan              | Cool down the Raspberry Pi and 5G module at the same time                                                                                                                                                                                                                 |
| ⑫      | Indicator                | Check the module running status anytime, anywhere                                                                                                                                                                                                                         |

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM8202G-M2-5G-HAT-B-details-intro02.jpg&#x26;width=800" alt=""><figcaption></figcaption></figure>

| Number | Name                  | Description                                                                                                                                                                                                                       |
| ------ | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ⑬      | Cooling Fan           | Simultaneously cooling Raspberry Pi and 5G modules                                                                                                                                                                                |
| ⑭      | SIM Card Slot 2       | Switchable via AT command (module is required)                                                                                                                                                                                    |
| ⑮      | Module Setting Switch | <p>Switch A to ON for SIM7600X/A7906X/IM7906X/SIM7912X series 4G M.2 module;<br>Switch B to ON, for SIM8202X/SIM8200EA/SIM8262X series 5G M.2 module;<br>Switch C to ON, for RM50X/RM520N-GL/EM06X series 5G/LTE-A M.2 module</p> |
| ⑯      | USB Interface Pad     | USB 2.0 interface pad                                                                                                                                                                                                             |
| ⑰      | NAU8810X Audio Chip   | For SIMN7600X/SIM8XXX series module, does support RM5XX and EM06XX series module                                                                                                                                                  |
| ⑱      | Fan Header            | 5V power supply for cooling fan                                                                                                                                                                                                   |

### Pinout

After connecting to Raspberry Pi, these pins (TX, RX, D4 and D6) can be connected or not through the DIP switch:

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=M.2-TO-4G-5G-HAT-Pin-defined.jpg&#x26;width=800" alt=""><figcaption></figcaption></figure>

**4G/5G modules function testing**

| Category | 4G/5G Module  | Network Communication | GNSS Positioning | <p>Voice calls through<br>Earphone Port</p> | Dual SIMs   | UART Interface | External Power Supply?    |
| -------- | ------------- | --------------------- | ---------------- | ------------------------------------------- | ----------- | -------------- | ------------------------- |
| 5G       | SIM8202G-M2   | 5G/4G/3G              | Support          | Support                                     | Support     | Support        | Optional, but recommended |
| 5G       | SIM8200EA-M2  | 5G/4G/3G              | Support          | Support                                     | Support     | Support        | Optional, but recommended |
| 5G       | RM500U-CN     | 5G/4G/3G              | NOT Support      | NOT Support                                 | Support     | Support        | Recommended               |
| 5G       | RM500Q-GL     | 5G/4G/3G              | Support          | NOT Support                                 | Support     | NOT Support    | Recommended               |
| 5G       | RM500Q-AE     | 5G/4G/3G              | Support          | NOT Support                                 | NOT Support | NOT Support    | Recommended               |
| 5G       | RM502Q-AE     | 5G/4G/3G              | Support          | NOT Support                                 | NOT Support | NOT Support    | Recommended               |
| LTE-A    | EM06-E        | LTE-A/4G/3G           | NOT Support      | NOT Support                                 | NOT Support | NOT Support    | Optional                  |
| LTE-A    | A7906E        | LTE-A/4G/3G           | NOT Support      | NOT Support                                 | NOT Support | NOT Support    | Optional                  |
| 4G       | SIM7600G-H-M2 | 4G/3G/2G              | Support          | Support                                     | NOT Support | Support        | Optional                  |

**4G/5G Module Compatibility**

If you need to use the M.2 TO 4G/5G HAT for other 4G/5G modules, you can refer to the M.2 connection diagram below, check whether there is any pin conflict, and then connect to test:<br>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=M.2-Compatibility.jpg&#x26;width=800" alt=""><figcaption></figcaption></figure>

### How to Use

### Dail-up

\[Note]: You must use a SIM card with GPRS networking function enabled and not out of service.

**NDIS Dail-up**

* At present, when using Windows 10 operating system, you can connect to 4G DONGLE module (equipped with 4G card of China Mobile/Telecom/Unicom). After installing the driver, most computers will automatically connect to the Internet.<br>
* If WINdows cannot access the Internet, you need to manually start NDIS dialing, open SIM7600 AT port, and send the command:<br>

```
AT$QCRMCALL=1,1+enter
```

\
At this point, the NDIS dialing takes effect, and the computer can connect to the network; if the dialing command returns an error, send the following command to set the NDIS dialing mode and then dial again:

<figure><img src="https://www.waveshare.com/w/upload/1/16/SIM820_dial.png" alt=""><figcaption></figcaption></figure>

```
AT+CUSBPIDSWITCH=9001,1,1
```

#### RNDIS Dial-Up Internet

In addition, dial-up Internet access using RNDIS is also possible:<br>

* After the device installed SIM card and antenna, connect the USB port to computer, then connect the power supply.
* Refer to the above to install the USB driver
* Open the serial port assistant, find the serial port number corresponding to the AT serial port, and send the AT command to check whether it is registered on the network:

```
AT+CPSI?  
```

* If you have successfully registered on the network, then send the AT command to enable USB dial-up Internet access:

```
AT+CUSBPIDSWITCH=9011,1,1
```

* If the transmission is successful, the DTU will return OK and reboot automatically.
* And then you can find that there are some unrecognized devices in the Device Manager on the computer, such as RNDIS (with exclamation mark).

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RNDIS_Dial-up01.png&#x26;width=600" alt=""><figcaption></figcaption></figure>

* Right-click the 'RNDIS', search "Update Divers" and select "Let me pick from a list of available drivers on my computer", then select "Network adapters" from the device list.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RNDIS_Dial-up02.png&#x26;width=600" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RNDIS_Dial-up03.png&#x26;width=600" alt=""><figcaption></figcaption></figure>

* Select "Microsoft" in the manufacturer list of the Network adapters window, and then select "Remote NDIS Compatible Device" in the list on the right, which is the remote NDIS compatible device.

<figure><img src="https://www.waveshare.com/w/upload/8/83/RNDIS_Dial-up04.png" alt=""><figcaption></figcaption></figure>

Click 'Next' and wait for the installation to finish, the RNDIS Kitl device will be installed successfully. And then you can see that the PC can access the Internet via DTU.

#### PPP dial-up

If the NDIS or RNDIS dial-up cannot access the Internet, you can also use PPP dial-up. The operation steps are as follows：<br>

* Network and Internet Settings -> Set up a new connection -> Connect to the Internet -> Dial up (D) -> Dial a phone number (D): \*99# (others are empty by default) -> Connection -> Register -> Connected to the Internet
*

```
<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600X_ppp_dial_%281%29.png&#x26;width=120" alt=""><figcaption></figcaption></figure>
```

*

```
<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600X_ppp_dial_%283%29.png&#x26;width=120" alt=""><figcaption></figcaption></figure>
```

*

```
<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600X_ppp_dial_%284%29.png&#x26;width=120" alt=""><figcaption></figcaption></figure>
```

*

```
<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600X_ppp_dial_%285%29.png&#x26;width=120" alt=""><figcaption></figcaption></figure>
```

*

```
<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600X_ppp_dial_%286%29.png&#x26;width=120" alt=""><figcaption></figcaption></figure>
```

### GPS Test

#### GNSS control instance

* Plug in the GPS antenna, and place the receiver tag face down in the open air, (Note that rainy weather cannot be tested) you need to wait about 1 minute before receiving the location signal.<br>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600G-H-M2-GPS.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* Detailed test instructions and screenshots are as follows:

```
AT+CGPS=1               // Open GPS
AT+CGPSINFO             // Prints GPS information to the serial port
AT+CGPS=0               // Turn off GPS
```

<br>

<figure><img src="https://www.waveshare.com/w/upload/4/47/SIM7600E-H_4G_DTU_GNSS.png" alt=""><figcaption></figcaption></figure>

### TCP/IP Internet data

GPRS debugging requires a SIM card with the GPRS networking function enabled.\
The following example takes accessing a mobile SIM card as an example.<br>

1. Correctly install the mobile phone card (the GPRS networking function must be enabled), the GSM antenna, and connect the USB cable to the computer;<br>
2. Press the PWR key to start the module and wait for more than ten seconds;<br>
3. Observe whether the indicator light is normal, the PWR indicator is always on, and the NET indicator is flashing;

#### Set up a local computer virtual server

The virtual server defines the mapping relationship between the WAN service port and the LAN network server. All accesses to the WAN service port will be relocated to the LAN network server specified by the IP address. (Please refer to your router's corresponding manufacturer's manual)

1. Use a browser to log in to the router management interface (please refer to your router manual for the specific address)
2. Set the port number: 2317 (it does not conflict with the existing port number. In this example, it is set to 2317)
3. Set the intranet IP of the computer (the IP obtained by the computer in the local area network can be run CMD on the local machine, enter the command line prompt, enter ipconfig to check the IPv4 address, the intranet IP of the computer in this example is 192.168.1.168), as shown in the following figure :

<figure><img src="https://www.waveshare.com/w/upload/2/26/Sim7600CE-18.jpg" alt=""><figcaption></figcaption></figure>

#### Configure GPRS

```
AT+CGDCONT=1,"IP","CMNET"     //Set APN
AT+CSQ       //Query the network signal quality. The first parameter is that the network signal quality is up to 31. The larger the value, the stronger the network signal.
AT+CREG?         //Query the network registration status, where the second parameter is 1, indicating that the registration has been successful.
AT+CIPMODE=1        //Set TCP/IP mode
AT+CSOCKSETPN=1          //select TCP/IP application mode
AT+CIPMODE=0          //select TCP/IP application mode
AT+NETOPEN         //startup mode 
AT+CIPOPEN=0,"TCP","113.81.233.65",2317         //Set TCP, IP and port number, establish TCP/IP connection 
AT+CIPSEND=0,9，         //To specify to send 9 characters of data, return to > to start sending 9 characters of content
AT+CIPCLOSE=0，         //close the TCP connection
AT+NETCLOSE，         //close the network
```

The operation is shown in the following figure:\
<br>

<figure><img src="https://www.waveshare.com/w/upload/f/f8/Ip-Gprs.png" alt=""><figcaption></figcaption></figure>

### Call Phone

* Refer to the "Hardware Configuration" chapter to connect the LTE antenna, SIM card (the phone function must be enabled), and the headset cable with microphone, and the module is turned on.
* Common commands for making calls:

| AT+CNUM              | Check the phone number (not all SIM cards support this command)                       | <p>+CNUM<br>OK</p> |
| -------------------- | ------------------------------------------------------------------------------------- | ------------------ |
| AT+CSDVC             | <p>AT+CSDVC=1: switch to headphone output<br>AT+CSDVC=3: switch to speaker output</p> | OK                 |
| AT+CLVL=?            | Query volume range                                                                    | OK                 |
| AT+CLVL=2            | set volume to 2                                                                       | OK                 |
| ATD\<phone\_number>; | ATD10086; Dial Mobile customer service phone number 10086                             | OK                 |
| AT+CHUP              | set volume to 2                                                                       | OK                 |
| AT+CLIP=1            | Set up caller ID                                                                      | OK                 |
| ATA                  | Answering the Phone                                                                   | OK                 |

* The detailed operation screenshots are as follows:

\
\[Note]When using the SSCOM serial port assistant to send and receive AT commands, you must click "carriage return and line feed".

<figure><img src="https://www.waveshare.com/w/upload/2/2c/Gprs2.png" alt=""><figcaption></figcaption></figure>

### Voice output mode and volume adjustment

```
AT+CSDVC=1 		//switch to headphones 
AT+CSDVC =3 	        //switch to speaker
AT+CLVL =?		//Query the volume range, return +CLVL: (0-5) //Indicates that the volume is adjustable from 0 to 5
AT+CLVL=2     	        //Set the volume to 2, return OK
```

### Answer the phone

```
Incoming call serial port display: RING
Send "ATA"      //Answer the phone
Send "AT+CHUP"  //Hang up
```

### Audio parameter debugging

```
AT+CACDBFN=?
+CACDBFN: (Handset_cal.acdb,Handset_tianmai.acdb)	// It is recommended to consider setting this set of parameters 
OK
```

A.In the initialization stage of the module startup, before making a call, add the following

```
AT^PWRCTL=0,1,3	// Mainly improve TDD noise effect 
OK
```

B. The module is in the process of establishing a voice call

```
VOICE CALL:BEGIN  	// Establish module call to improve call    effect
AT+CECM=1      		//suppress echo
OK
AT+CECH=0x500 	// improve the volume on the mobile phone  
OK
```

See "SIM7X00\_Audio\_Application\_Note" document for details.

### Send English SMS

1\. Correctly install the SIM card and LTE antenna, connect the module's USB interface to the computer with a USB cable, and turn on the module;\
2\. Observe whether the indicator light is normal, the PWR indicator is always on, and the NET indicator is flashing;\
3\. Set the local SMS center: AT + CSCA = " + 8613800755500" + Enter, return OK.<br>

Note: China Mobile's SMS service center number is +861380xxxx500, where xxxx is the long-distance telephone area code where you are located. The SMS center may be different from place to place. For details, you can query Baidu or call China Mobile Unicom customer service. This SMS center is Shenzhen (0755);<br>

4\. AT+CMGF=1: Set the SMS mode to TEXT;\
5\. AT+CMGS="phone number"\<Enter>, set the recipient's phone number, and then return: ">", send the content that you need, such as "Send massage test!", You don’t need to “Enter” at the end. After editing the text message, send 1A to send information in hexadecimal format (1A is the key value of "CTRL+Z", which is used to tell the module to perform the sending operation, or 1B or "ESC" to cancel the operation). After successfully sending, the module returns + CMGS: 15 confirm that the transmission was successful. As shown below.<br>

<figure><img src="https://www.waveshare.com/w/upload/3/3e/Send_English_Messages.png" alt=""><figcaption></figcaption></figure>

### Receive English SMS

1. Send a message on the phone: "This is a receive test for SIM7600X!" to the test module.
2. When receiving the information, the serial port will break and report the information, "SM", 20, which means there are 20 pieces of information in the SM, and the message just sent is the 20th piece of information.
3. Read information: AT+CMGR=20 to read the 20th information (AT+CMGL="ALL" to read all information).
4. Delete information: AT+CMGD=20, as shown below.
5. Convert the displayed information to text through a code converter.

<figure><img src="https://www.waveshare.com/w/upload/6/6d/Receive_English_Messages.png" alt=""><figcaption></figcaption></figure>

### User Guides of Raspberry Pi

#### Raspberry Pi Internet Operation

If you are using Raspberry Pi 4B, Raspberry Pi 3B+ or CM4-IO-BASE-A/B baseboard, you can use the used the customized USB adapter.if it is used for other embedded mainboards or PCs, it can be connected through the matching double-head usb3.0 data cable; as shown in the following figure:\
\
For specific operations related to Raspberry Pi dial-up Internet access, please refer to the following links:

<figure><img src="https://www.waveshare.com/w/upload/4/49/SIM7600G-H-M2_4G_HAT-1.png" alt=""><figcaption></figcaption></figure>

* [Raspberry Pi RNDIS dial-up Internet](https://www.waveshare.com/wiki/Raspberry_Pi_networked_via_RNDIS)- (the easiest way to operate)
* [Raspberry Pi PPP dial-up](https://www.waveshare.com/wiki/Raspberry_Pi_PPP_dial-up)- (the operation is relatively simple)
* [Raspberry Pi NDIS dial-up Internet access](https://www.waveshare.com/wiki/Raspberry_Pi_networked_via_NDIS)

#### Raspberry Pi Minicom Sends AT Command to Debug

1\. Connect the module to Raspberry Pi.\
2\. Install minicom, minicom is a serial debugging tool for the Linux platform.<br>

```
sudo apt-get install minicom
```

3\. USB and UART serial AT command debugging.<br>

* Execute minicom -D /dev/ttyUSB2. (default baud rate is 115200)<br>

```
 sudo minicom -D /dev/ttyUSB2
```

* Enter the following AT command in the minicom to open the UART. (the default baud rate is 115200).<br>

```
AT+CCUART=1
```

* Switch on all the A silkscreen corresponding to SIM76XX, use minicom to select the corresponding serial port, Raspberry Pi 5/3B/2B/zero, the user serial port device number is ttyAMA0, and the baud rate is 115200 by default.<br>

```
 sudo minicom -D /dev/ttyS0 -b 115200
```

\
4\. Taking the AT synchronization test as an example, send relevant commands, as shown in the following figure:\
\
\* minicom can enter the setting mode by pressing Ctrl+A, then Z, and exit by selecting X. If the sending command does not display, please send the command ATE=1 + Enter -> open the echo.

<figure><img src="https://www.waveshare.com/w/upload/b/ba/SIM7600G-H-M2_4G_HAT-2.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/4/42/SIM7600X-A.png" alt=""><figcaption></figcaption></figure>

#### Program sample

1\. After inserting the module and connecting it to the Raspberry Pi;\
2\. Download the sample program to the /home/pi/ path;

```
wget https://files.waveshare.com/upload/5/5c/SIM7600G-H-4G-HAT-B-Demo.zip
sudo apt-get install p7zip-full
7z x SIM7600G-H-4G-HAT-B-Demo.zip 
```

3\. Go to the corresponding instance directory, compile and run the program, the relevant instructions are as follows (take the PhoneCall.py program as an example):<br>

```
cd SIM7600G-H-4G-HAT-B-Demo/Raspberry/python/PhoneCall/ //Enter the folder where PhoneCall.py is located
sudo apt-get install python3-pip
sudo pip3 install pyserial 
```

sudo pip3 install RPi.GPIO

```
sudo python PhoneCall.py //Run the program
```

<br>

**AT Command**

<br>

<figure><img src="https://www.waveshare.com/w/upload/7/75/Sim7600g.png" alt=""><figcaption></figcaption></figure>

**Phone Call Demo**

<figure><img src="https://www.waveshare.com/w/upload/f/f9/Phonecall.png" alt=""><figcaption></figcaption></figure>

**Receive & Send SMS**\
Note: The sample program is to send English text messages. If you have sent Chinese text messages, you need to use the following commands to change to English format:

<figure><img src="https://www.waveshare.com/w/upload/4/40/Receive_%26_Send_SMS.png" alt=""><figcaption></figcaption></figure>

```
AT+CSMP=17,167,0,240
```

**GPS Demo**

<figure><img src="https://www.waveshare.com/w/upload/7/78/Gps-demo.png" alt=""><figcaption></figcaption></figure>

**TCP Network Communication Demo**

<figure><img src="https://www.waveshare.com/w/upload/c/c0/Tcp-network.png" alt=""><figcaption></figcaption></figure>

**FTP Upload & Download Demo**<br>

<figure><img src="https://www.waveshare.com/w/upload/4/49/Upload-download.png" alt=""><figcaption></figcaption></figure>

### Jetson Nano Demo

#### Hardware Connection

Jetson Nano has an onboard USB interface, SIM7600X 4G HAT(B) is connected to the USB interface of Jetson Nano through Micro USB.<br>

<figure><img src="https://www.waveshare.com/w/upload/e/e6/Jetson-hardware-connection.png" alt=""><figcaption></figcaption></figure>

#### Jetson Nano minicom Serial Port Debugging

1\. Connect the SIM7600X 4G HAT(B) to the Jetson Nano and turn it on after three seconds\
2\. Use [Template:SERIAL to log in to the Jetson Nano terminal](https://www.waveshare.com/wiki/Template:SERIAL_to_log_in_to_the_Jetson_Nano_terminal), install minicom, and enter:<br>

```
sudo apt-get install minicom
```

3\. Run minicom for debugging, and enter in the terminal

```
sudo minicom -D /dev/ttyUSB2 -b 115200
```

4\. Send AT command to test, exit minicom and press Ctrl+A, then X, and finally press ENTER\
More demos to be continued...

<figure><img src="https://www.waveshare.com/w/upload/0/0b/Jetson_nano_demo.png" alt=""><figcaption></figcaption></figure>

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion17"><strong>After using RNDIS dialing, what should I do if there is no drive device symbol?</strong></a></summary>

The RNDIS mode COM port can be loaded with the following drivers：\
[SIM7600X Driver](https://files.waveshare.com/upload/4/48/SIM7600_Windows_USB_driver_V1.02.zip)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion16"><strong>When compiling the BCM2835 library, Makefile:327:recipe for target 'aclocal.m4' failed?</strong></a></summary>

[![Bcm2835.png](https://www.waveshare.com/w/upload/4/4e/Bcm2835.png)](https://www.waveshare.com/wiki/File:Bcm2835.png)<br>

Execute: autoreconf -vfi, and then recompile, as shown in the following figure:\
[![Autoreconf.png](https://www.waveshare.com/w/upload/e/e5/Autoreconf.png)](https://www.waveshare.com/wiki/File:Autoreconf.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion15"><strong>When executing the chmod 777 sim7600_4G_hat_init command, an error is reported: "chmod: cannot access 'sim7600_4G_hat_init': No such file or directory", what should I do?</strong></a></summary>

[![Chmod.png](https://www.waveshare.com/w/upload/4/4f/Chmod.png)](https://www.waveshare.com/wiki/File:Chmod.png)<br>

Answer:Please confirm that there is a sim7600\_4G\_hat\_init file in the current path<br>

[![Chmod2.png](https://www.waveshare.com/w/upload/3/31/Chmod2.png)](https://www.waveshare.com/wiki/File:Chmod2.png)\
The general operation is: download the sample program, after decompression, rename the c folder under the Raspberry folder to SIM7600X, then copy the entire SIM7600X folder to the Raspberry Pi /home/pi directory, and enter the command line to /home/pi /SIM7600X directory, and then execute the chmod 777 sim7600\_4G\_hat\_init command. "

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion14"><strong>What should I do if I can't receive GPS signal and location information?</strong></a></summary>

Answer: Plug in the GPS antenna to the GNSS antenna base, and place the receiver label face down in an open outdoor (note that it cannot be tested in rainy weather). It takes about 1 minute to receive the positioning signal after power-on;

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion13"><strong>What do the positioning information obtained by SIM7600X through AT+CGPSINFO represent?</strong></a></summary>

From left to right are ①Latitude, ②Longitude, ③Date, ④Time, ⑤Elevation, ⑥Speed ​​and ⑦Angle.<br>

[![SIM7600 GNSS FAQ (1234567).png](https://www.waveshare.com/w/upload/c/ce/SIM7600_GNSS_FAQ_\(1234567\).png)](https://www.waveshare.com/wiki/File:SIM7600_GNSS_FAQ_\(1234567\).png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion12"><strong>What should I do if the SIM7600X module NDIS dialing fails and the driver cannot be installed?</strong></a></summary>

Make sure that your system kernel is above 5.4. Do not use sudo update to upgrade the Raspberry Pi to the latest version, otherwise the kernel version will be upgraded to a version higher than the current firmware and will not be recognized.

It is recommended to use the more convenient RNDIS dial\
You can burn the latest Raspberry Pi Raspbian system and reconfigure the RNDIS dial-up\
Or use the image that has been configured with the driver, RNDIS dial-up and boot up and start raspbian system image (the driver has been installed)

* Can burn the latest Raspberry Pi Raspbian system, reconfigure NDIS dial

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion11"><strong>NDIS dial-up of SIM7600X module fails and the driver cannot be installed, what should I do?</strong></a></summary>

* Make sure your system kernel is above 5.4. Do not use sudo update to upgrade the Raspberry Pi to the latest version. This will upgrade the kernel version to a version higher than the current firmware and it will not be recognized.
* It is recommended to use the more convenient [RNDIS dial](https://www.waveshare.com/wiki/SIM820X_RNDIS_Dial-Up)
* Can burn the latest Raspberry Pi Raspbian system, reconfigure NDIS dial

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion10"><strong>What are the antenna parameters for SIM7600CE 4G HAT?</strong></a></summary>

* Frequency: 700m 800m 900m 1710-1920M 2010-2100M 2300-2400M 2500-2690M-5800MHZ
* Gain: 9dbi ± 0.7dbi

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion9"><strong>How much power consumption when SIM7600CE 4G HAT loads 4g and gps at the same time?</strong></a></summary>

Turn on at the same time, average value: 110\~170mA

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion8"><strong>What is the working current when networking?</strong></a></summary>

Using USB 5V power supply, after successful networking, the current is generally in the range of 50\~300mA, with an average of about 150mA (for reference only, it depends on the network environment and the working status of the network.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion7"><strong>How many short messages can be stored in SIM7600CE 4G HAT?</strong></a></summary>

If the short message is stored in the SIM card, usually 50 is the upper limit. You can use the command: AT+CPMS? Make a query

<br>

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion6"><strong>SIM7600 firmware upgrade failed, and the prompt is as shown in the figure below, what should I do?</strong></a></summary>

[![SIM7600X-FAQ (6).png](https://www.waveshare.com/w/upload/8/89/SIM7600X-FAQ_\(6\).png)](https://www.waveshare.com/wiki/File:SIM7600X-FAQ_\(6\).png)\
1\. Pay attention to check the device manager, the new device will be prompted during the upgrade process, and there will be no device driver during the first upgrade;\
2\. Pay attention to the USB cable. The speed of the USB cable is higher during the upgrade process. You need to choose a better quality USB cable to avoid poor contact.\
3\. You need to run the upgrade tool with administrator privileges (SIM7500\_SIM7600\_QDL V1.41 only for Update)\
4\. Uninstall and reinstall the upgrade tool (SIM7500\_SIM7600\_QDL V1.41 only for Update)\
5\. For more operation details, please refer to this video: [https://www.waveshare.net/wiki/SIM7600-Firmware-upgrade-Video](https://www.waveshare.net/wiki/SIM7600-Firmware-upgrade-Video)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion5"><strong>Why is my dial-up internet speed very slow here?</strong></a></summary>

* Generally, the default configuration of SIM7600 is to automatically select the network standard, and it is likely to choose 2G Internet access; if you need to force the use of 4G mode, you need to enter the following AT command configuration:<br>

```
AT+CNMP=38 //Fixed 4G LTE, if there is no local 4G coverage, you may not be able to register to the network
```

[![SIM7600X-FAQ (4).png](https://www.waveshare.com/w/upload/8/80/SIM7600X-FAQ_\(4\).png)](https://www.waveshare.com/wiki/File:SIM7600X-FAQ_\(4\).png)

* If 4G has been fixed, the speed is still not ideal, it may be a frequency band problem;

```
AT+CNBP? //Back up the current frequency band (the returned frequency band information can be copied to notepad, etc.)
```

```
AT+CNBP=0x0002000000400183,0x000001E000000000,0x0000000000000021 //After returning OK, measure the speed
```

```
AT+CNBP=0x0002000004400180,0x000001E000000000,0x000000000000003F //If the speed does not improve, try this
```

[![SIM7600 band speed.png](https://www.waveshare.com/w/upload/d/d0/SIM7600_band_speed.png)](https://www.waveshare.com/wiki/File:SIM7600_band_speed.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion4"><strong>What should you do if you are registered to the network, dial up successfully and get an IP, but you cannot access the Internet and cannot ping through?</strong></a></summary>

It may be that the APN has not been obtained. Generally, the APN can be obtained automatically. In some areas (IoT card), it needs to be obtained manually. For example, it can be set by the following instructions:

```
AT+CGDCONT=1,"IP","CMNET" //CMNET is the apn of China Mobile, which is different for different operators
```

[![SIM7600X apn.png](https://www.waveshare.com/w/upload/a/ad/SIM7600X_apn.png)](https://www.waveshare.com/wiki/File:SIM7600X_apn.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion3"><strong>When sending AT+CPIN?, it returns ERROR</strong></a></summary>

This problem is generally caused by poor contact between the SIM card and the SIM card socket of the module.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion2"><strong>The NET light does not flash after the SIM7600X is turned on, what should I do if the network is abnormal?</strong></a></summary>

In this case, it may be that you have not successfully connected to the network, you can follow the steps below to troubleshoot:\
1\. First check the hardware connection:

* Check if the MAIN antenna is well connected;<br>
* Whether the connected SIM card can call and surf the Internet normally on mobile phones and other devices:<br>
* If the Raspberry Pi is connected, whether the module enters airplane mode;<br>

2\. After confirming that there is no problem with the hardware, the software can use these instructions:<br>

* Check whether the sim card is in good contact: AT+CPIN?<br>
* Check if the network mode setting is correct: AT+CNMP?<br>
* Check the signal quality of the current environment: AT+CSQ<br>
* Check the operator's access situation: AT+COPS?<br>
* Check the connection status: AT+CPSI?<br>
* Check whether it is successfully registered to the network: AT+CGREG?<br>

[![SIM7600X network check.png](https://www.waveshare.com/w/upload/d/df/SIM7600X_network_check.png)](https://www.waveshare.com/wiki/File:SIM7600X_network_check.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT#accordion1"><strong>Type of SIM card?</strong></a></summary>

Support SIM standard (Standard) card, as shown in the figure below, if it is Micro or Nano card, you need to add a card sleeve.\
[![SIM card size.png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM_card_size.png\&width=400)](https://www.waveshare.com/wiki/File:SIM_card_size.png)

</details>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/SIM7600G-H-M2_4G_HAT) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
