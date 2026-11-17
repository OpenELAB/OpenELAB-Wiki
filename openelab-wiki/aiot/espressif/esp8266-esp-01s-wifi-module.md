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

# ESP8266 ESP-01S WiFi module

### ESP8266 ESP-01S WiFi module

***

### Product Link

{% embed url="https://openelab.io/products/esp8266-esp01s-wifimodule?_pos=1&_sid=04c01dd06&_ss=r" %}

### Introduction

ESP8266 series module is a series of low-power UART-WiFi chip modules based on Loxin ESP8266EX developed by Shenzhen Ansinko Technology Co., Ltd, which can be conveniently used for secondary development and access to cloud services to achieve mobile phone 3/4G global anytime-anywhere control and accelerate product prototyping.

The module's core processor, ESP8266, integrates the industry-leading Tensilica L106 ultra-low-power 32-bit micro MCU with 16-bit lite mode in a smaller package with 80 MHz and 160 MHz main frequency support, RTOS support, integrated Wi-Fi MAC/ BB/RF/PA/LNA, and on-board antenna. It supports standard IEEE802.11 b/g/n protocols and complete TCP/IP stack. Users can use the module to add networking capabilities to existing devices or build standalone network controllers.

The ESP8266 is a high-performance wireless SoC that offers maximum utility at minimum cost, providing unlimited possibilities for embedding Wi-Fi functionality into other systems.

### Features

* 802.11 b/g/n&#x20;
* Built-in Tensilica L106 ultra-low-power 32-bit micro MCU, 80 MHz and 160 MHz, RTOS support
* Built-in 10 bit high precision ADC
* Built-in TCP/IP stack&#x20;
* Built-in TR switch, balun, LNA, power amplifier and matching network
* Built-in PLL, regulator and power management components, +18 dBm output power in 802.11b mode
* A-MPDU, A-MSDU aggregation and 0.4 s guard interval&#x20;
* Wi-Fi @ 2.4 GHz with WPA/WPA2 security mode support&#x20;
* Support AT local upgrade and cloud OTA upgrade&#x20;
* Supports STA/AP/STA+AP operating modes Support&#x20;
* Smart Config function (including Android and IOS devices)&#x20;
* HSPI, UART, I2C, I2S, IR Remote Control, PWM, GPIO&#x20;
* Deep sleep hold current of 20 uA, shutdown current less than 5 uA&#x20;
* Wake up, connect and pass packets within 2 ms&#x20;
* Standby power consumption less than 1.0 mW (DTIM3)&#x20;
* Operating temperature range: see specifications for details

### Pinout

<figure><img src="../../.gitbook/assets/image (703).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (705).png" alt=""><figcaption></figcaption></figure>

### How to Use

Connect the WIFI module to the computer with USB-TTL, install the driver, install the serial port debugging assistant and network debugging assistant, and use the Wildfire multifunctional debugging assistant for this process.

#### 1. WIFI module as a client(pass-through)

1. Serial debugging assistant to set the serial port parameters, see Figure 1 below
2. AT: test AT development mode start
3. AT+GMR ：View the firmware version information
4. AT+CWMODE=1: set WIFI application mode 1Station mode 2 AP mode 3 AP cum Station mode, AP means as access point, station means as client station
5. AT+RST: Reboot
6. AT+CWLAP: list the available access points
7. AT+CWJAP="TP-LINK\_6FFA", "123456789": join access point
8. AT+CIFSR ：Get local IP address
9. PC connects to the router, the network debugging assistant uses the IP address of the computer to create a server, the IP settings are shown in Figure 2 below;
10. AT+CIPSTART="TCP", "192.168.101.110",8080 ：Establish TCP connection with the server.
11. AT+CIPMODE=1: set up transmitting mode (that is, you can send all the time, otherwise you have to set up the number of bytes to be sent with AT+CIPSEND=4; as a server mode, you can't use the transmitting mode)
12. AT+CIPSEND: start the pass-through, serial debugging assistant sends data, network debugging assistant sends data.
13. Receive data format: serial tuning: +IPD,n:xxxxxxxxxxxx Received data Length is n bytes, xxxxxx is data; network tuning: \[Tcp client 192.168.1.108 2872] 123, TCP mode, client IP address, port number, 123 is data;
14. End pass-through: there is a programme to enter 3 + signs to exit pass-through, I didn't implement it, I directly power off the module, after a few minutes it can be reset;

#### 2. WIFI module as client (single connection)

1. AT+CWMODE=1 ：Set WIFI application mode 1Station mode 2 AP mode 3 AP cum Station mode, AP means as access point, station means as client station
2. AT+RST: Reboot
3. AT+CWJAP="TP-LINK\_6FFA", "123456789": join access point
4. PC connects to the router, the network debugging assistant uses the IP address of the computer to create a server, IP settings see Figure 2 above;
5. AT+CIPSTART="TCP", "192.168.101.110",8080 ：Establish TCP connection with the server.
6. AT+CIPSEND=4 ：Send four bytes of data, input the four bytes to be sent, no need to enter.
7. If the number of bytes sent exceeds the set length n of the command, it will respond busy and send the first n bytes of the data, and respond SEND OK when finished. The nettune can be sent over arbitrarily.

#### 3. WIFI module as server

1. AT+CWMODE=2 ：Set WIFI application mode 1 Station mode 2 AP mode 3 AP cum Station mode, AP means as access point, station means as client station
2. AT+RST: Reboot
3. AT+CWSAP="ESP\_664843", "123456789", "11,3,4,0", "CWSAP="ESP\_664843", "123456789", "123456789", "123456789", "123456789",11,3,4,0".
4. AT+CWSAP="ESP\_664843", "123456789",11,3 : modify access point name, password and 3 is encryption mode. 11 is channel number, need to reboot after modify, not used, not look into.
5. AT+CIPMUX=1:Start multiple connections.
6. AT+CIPSERVER=1:set up server, default port 333, tried it, can't change it.
7. AT+CIPSTO=300: set server timeout time 0\~28800, unit is s, over time will kick client off.
8. AT+CIFSR :Get local IP address for setting network assistant, there are two kinds of display: AP mode, AP and Station mode.
9. First of all, PC should be connected to the WIFI module hotspot, PC network debugging assistant as a client connected to the AP, setup see Figure 3 below.
10. AT+CWLIF: view the accessed devices.
11. AT+CIPSEND=4: (command report error, serial can not be sent, network can be sent)
12. Receive data: serial tuning can receive data from net tuning assistant, net tuning assistant can't receive serial tuning data.

### FAQ

<details>

<summary>Where can I download the PCB package for ESP8266 series modules?</summary>

[Download](https://docs.ai-thinker.com/_media/esp8266.zip)

</details>

<details>

<summary>How is the ESP8266 series module backplane pcb designed and what rules are followed?</summary>

[Reference to Ensign ESP Series Module PCB Design and Antenna Placement Design Reference](https://docs.ai-thinker.com/_media/esp8266/docs/antenna_design_reference_v1.1.pdf)

</details>

<details>

<summary>ESP8266 series usual development tools summary:</summary>

[Click on me to jump](https://docs.ai-thinker.com/tools)

</details>

<details>

<summary>common problems:</summary>

[ESP8266 Module Frequently Asked Questions](https://app.gitbook.com/u/yy9uvfxZYvM5dFCNVN2WjnNLCP53)

</details>

<details>

<summary>Summary of certificates of accreditation regarding Ensynco modules:</summary>

[ESP8266 Series Module Certificate](https://docs.ai-thinker.com/esp8266/certificate)

</details>

<details>

<summary>Windows platform C programming SDK secondary development environment construction</summary>

[Click on me to jump](https://blog.csdn.net/xh870189248/article/details/77985541)

</details>

<details>

<summary>Linux platform C programming SDK secondary development environment build;</summary>

[Click on me to jump](https://xuhong.blog.csdn.net/article/details/104736261)

</details>

<details>

<summary>ESP8266 series module recommended package:</summary>

[Click on me to jump](https://docs.ai-thinker.com/_media/esp8266.zip)

</details>
