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

# M5Stack COM.LTE Module

{% hint style="info" %}
[**View M5Stack COM.LTE Module on OpenELAB**](https://openelab.io/products/com-lte-module)

**Store SKU / option:** `M5-M031-A`. Match the purchased model and revision to the official reference below.
{% endhint %}

## M5Stack COM.LTE Module

***

### Product Link

{% embed url="https://openelab.io/products/com-lte-module" %}

### Description <a href="#description" id="description"></a>

**COM.LTE(4G)** is a stackable multifunctional LTE communication module, built-in LTE communication module SIM7600G, supports LTE-TDD/LTE-FDD/WCDMA and GSM frequency bands, supports LTE.CAT4 (downlink speed is 150Mbps), supports voice calls SMS with SMS.

It has stable performance, small appearance, high cost performance, and can realize the transmission of SMS and data information with low power consumption. The module has a DC power input and can provide 5V-12V power supply through an external power supply.

In order to facilitate the user to configure the pin, the DIP switch is used to set the pin. The onboard microphone and 3.5mm headphone jack support the insertion of headphone with microphone. This module is especially suitable for scenarios that require high-speed network connections, such as video calls, drone data transmission, industrial Internet of Things, etc.

### Notice <a href="#notice" id="notice"></a>

When used with the **FIRE** main control, due to the PSRAM pin conflict, please switch the DIP switch pins of the module base to TX(0/13), RX(5/15), and the device can use USB/ External DC is used for power supply.When used with **Core2** series main control, due to the different order of the base pin array, COM.X base pins TX(16), RX(17) correspond to the actual pins TX(14), RX of the Core2 main control (13) The equipment needs to use external DC for power supply.

### Features <a href="#features" id="features"></a>

* Stackable design
* Support voice calls, SMS text messages, cellular data transmission
* Independent external power supply
* Built-in microphone
* AT command control
* SIM card type: MicroSIM
* Status signal: two LED indicators
* External antenna: SMA antenna
* Serial communication: UART 115200bps
* Frequency band:
  * LTE-TDD B34/B38/B39/B40/B41
  * LTE\_FDD B1/B2/B3/B4/B5/B7/B8/B12/B13/ B18/B19/B20/B25/B26/B28/B66
  * WCDMA B1/B2/B4/B5/B6/B8/B19
  * GSM/GPRS/EDGE 850/900/1800/1900MHz
* Data transmission speed:
* LTE Cat4
  * UL:50Mbps
  * DL:150Mbps
* HSPA+
  * UL:5.76Mbps
  * DL:42Mbps
* WCDMA
  * UL/DL:384Kbps
* EDGE/GPRS
  * UL/DL:236.8Kbps
* Protol
  * TCP/IP/IPV4/IPV6/ Multi-PDP/FTP/FTPS/HTTP/ HTTPS/DNS
  * TLS
  * RNDIS/ECM
  * FOTA

### Certification <a href="#certification" id="certification"></a>

• CE/RCM/FCC/IC

• PTCRB/GCF

• AT\&T/Verizon

• RoHS/REACH

### Applications <a href="#applications" id="applications"></a>

* Remote meter reading system
* Automatic Web Spider SMS-notifier
* Wireless communication
* M2M industrial
* Vehicle-mounted
* Video

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                   | Parameter                                                  |
| --------------------------- | ---------------------------------------------------------- |
| Frequency band              | LTE-FDD/LTE-TDD/WCDMA/GSM                                  |
| Network protocol            | TTCP/IP/IPV4/IPV6/ Multi-PDP/FTP/FTPS/HTTP/ HTTPS/DNS etc. |
| Communication               | UART 115200bps                                             |
| DC interface specifications | 5.5mm                                                      |
| Net weight                  | 55g                                                        |
| Gross weight                | 90g                                                        |
| Product Size                | 54.2\*54.2\*13.2mm                                         |
| Package Size                | 165\*60\*36mm                                              |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Stack | TX(GPIO0/13/17) | RX(GPIO5/15/16) | 5V  | GND |
| ------- | --------------- | --------------- | --- | --- |
| COM.LTE | RX              | TX              | VIN | GND |

According to the different needs of different hosts, the DIP switch fluctuates to the corresponding pin.

| M5Stack HOST | CORES3  | CORE2   | CORE    |
| ------------ | ------- | ------- | ------- |
| RXD          | 17/0/7  | 14/0/19 | 17/0/13 |
| TXD          | 18/1/13 | 13/33/2 | 16/5/15 |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/comx_lte/comx_lte_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet**
  * [SIM7600G datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/SIM7600-H%20Series_SPEC_20200528.pdf)
* **Application**
  * [SIM7100\_SIM7500\_SIM7600\_SIM7800 Series\_USB AUDIO\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7500_SIM7600_SIM7800%20Series_USB%20AUDIO_Application%20Note_V2.00.pdf)
  * [SIM7100\_SIM7600 Series\_TTS\_Application Note\_V2.0.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7600%20Series_TTS_Application%20Note_V2.0.pdf)
  * [SIM7500\_SIM7600 Series\_FOTA\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600%20Series_FOTA_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600 Series\_FTP(S)\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600%20Series_FTP\(S\)_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600 Series\_GNSS\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600%20Series_GNSS_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600 Series\_Jamming Detection\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600%20Series_Jamming%20Detection_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600 Series\_SAT\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600%20Series_SAT_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600\_SIM7800 Series\_ECALL\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600_SIM7800%20Series_ECALL_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600\_SIM7800 Series\_MQTT\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600_SIM7800%20Series_MQTT_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600\_SIM7800 Series\_SMS\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600_SIM7800%20Series_SMS_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600\_SIM7800 Series\_SSL\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600_SIM7800%20Series_SSL_Application%20Note_V2.00.pdf)
  * [SIM7500\_SIM7600\_SIM7800 Series\_TCPIP\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600_SIM7800%20Series_TCPIP_Application%20Note_V2.00.pdf)
  * [SIM7600 Series\_HSIC\_LAN\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7600%20Series_HSIC_LAN_Application%20Note_V2.00.pdf)
  * [SIM7600\_AYLA\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7600_AYLA_V2.00.pdf)
  * [SIM7600\_Alibaba\_MQTT\_COAPV2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7600_Alibaba_MQTT_COAPV2.00.pdf)
  * [SIM7100\_SIM7500\_SIM7600 Series\_GPIO\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7500_SIM7600%20Series_GPIO_Application%20Note_V2.00.pdf)
  * [SIM7100\_SIM7500\_SIM7600 Series\_LBS\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7500_SIM7600%20Series_LBS_Application%20Note_V2.00.pdf)
  * [SIM7100\_SIM7500\_SIM7600 Series\_Sleep Mode\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7500_SIM7600%20Series_Sleep%20Mode_Application%20Note_V2.00.pdf)
  * [SIM7100\_SIM7500\_SIM7600 Series\_UART\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7500_SIM7600%20Series_UART_Application%20Note_V2.00.pdf)
  * [SIM7100\_SIM7500\_SIM7600 Series\_UIM HOT SWAP\_Application Note\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7100_SIM7500_SIM7600%20Series_UIM%20HOT%20SWAP_Application%20Note_V2.00.pdf)
* **AT Command**
  * [SIM7500\_SIM7600 Series\_AT Command Manual\_V2.00.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7500_SIM7600%20Series_AT%20Command%20Manual_V2.00.pdf)
* **Certificate**
  * [SIM7600E-PCIE\_Deutsche Telekom\_Certificate\_2020.pdf.pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/sim7600x/SIM7600E-PCIE_Deutsche%20Telekom_Certificate_2020.pdf.pdf)

### Compatible <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (964).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module COMX LTE](https://docs.m5stack.com/en/module/Module_COMX_LTE) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M031-A`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                 |
| ---------------------------- | -------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/module/module_comx_lte) |
| Example source: M5Stack      | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Modules/COM_LTE)  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
