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

# M5Stack IoT Base

{% hint style="info" %}
[**View M5Stack IoT Base with CAT-M Module Communication Base on OpenELAB**](https://openelab.io/products/m5stack-iot-base)

**Store SKU / option:** `M5-M119`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack IoT Base with CAT-M Module

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-iot-base" %}

### Description <a href="#description" id="description"></a>

**IoT BASE Cat-M** is a functional base designed for IoT data transmission. The internal 'SIM7080G' module supports both 'CAT-M' and 'NB-IoT' modes with global coverage. This functional base includes I2C + UART + GPIO + RS485 + Battery-power ports, with rich expansion options. As well to support common industrial protocols such as Modbus. Suitable for remote control, remote monitoring, remote medical applications.

### Features <a href="#features" id="features"></a>

* Module Solution: SIM7080G
* Cat-M & NB-IoT modes with Global Coverage
* UART interface/ AT command control
* Global version/ multi-band support
* Card slot: MicroSIM
* Antenna: external `SMA` antenna
* Module certifications: Softbank/Telec/RoHS/REACH/JATE/Docomo/KDDI/RCM/CE(RED)/GCF
* Deutsche Telekom/FCC/PTCRB/AT\&T/Verizon/T-Mobile/US Cellular/IC
* IoT Base expansion ports:
  * 1x PWR485 (RS485 + DC12V INPUT)
  * 1x DC power jack
  * 1x I2C
  * 1x GPIO
  * 1x UART
  * 1x Battery Expansion Interface

### Applications <a href="#applications" id="applications"></a>

* Remote Control/Data Collection
* Data transmission

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                   | Parameters                                                                                                                                           |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Communication module             | SIM7080G, communication interface: UART baud 115200 8N1                                                                                              |
| Support CAT-M band               | B1/B2/B3/B4/B5/B8/B12/B13/B14/B18/B19/B20/B25/B26 /B27/B28/B66/B85                                                                                   |
| Support CAT-NB frequency band    | B1/B2/B3/B4/B5/B8/B12/B13/B18/B19/B20/B25/B26/B28 /B66/B71/B85                                                                                       |
| Cat-M uplink and downlink speed  | Uplink: 1119Kbps Downlink: 589Kbps                                                                                                                   |
| NB-IoT uplink and downlink speed | Uplink: 150Kbps Downlink: 136Kbps                                                                                                                    |
| RF Power Class                   | Class 5 (Typ. 21dbm)                                                                                                                                 |
| Card slot specifications         | MicroSIM                                                                                                                                             |
| Support protocol:                | TCP/UDP/HTTP/HTTPS/TLS/DTLS/PING/LWM2M/COAP/MQTT and other communication protocols                                                                   |
| Working current                  | 42mA (DC interface 12V input, when the device is connected to the network)                                                                           |
| Interface specifications         | <p>I2C/GPIO/UART(HY2.0-4P)<br>RS485(VH-3.96-4P)<br>DC interface (round hole DC-IN-TH_DC-0440-2.5A-2.0)<br>Lithium battery interface (VH-3.96-2P)</p> |
| Net weight (module)              | 29.4g                                                                                                                                                |
| Gross weight                     | 153.6g                                                                                                                                               |
| Product size                     | 80 \* 54 \* 33mm                                                                                                                                     |
| Packing size                     | 98 \* 106 \* 57mm                                                                                                                                    |

### PinMap <a href="#pinmap" id="pinmap"></a>

* SIM7080G

| M5Core   | G0 | G35 | G12 | 5V  | GND |
| -------- | -- | --- | --- | --- | --- |
| SIM7080G | RX | TX  | PWR | VCC | GND |

* RS485

| CORE  | G15 | G13 | 5V  | GND |
| ----- | --- | --- | --- | --- |
| RS485 | TX  | RX  | VIN | GND |

* HY2.0-4P

| M5Core   | G21 | G22 | 5V  | GND |
| -------- | --- | --- | --- | --- |
| I2C PORT | SDA | SCL | VCC | GND |

| M5Core    | G36 | G26 | 5V  | GND |
| --------- | --- | --- | --- | --- |
| GPIO PORT | ADC | DAC | VCC | GND |

| M5Core    | G17 | G16 | 5V  | GND |
| --------- | --- | --- | --- | --- |
| UART PORT | TX  | RX  | VCC | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/base/iot_base_catm/iot_base_catm_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [IoT Base CatM](https://docs.m5stack.com/en/base/IoT_Base_CatM) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M119`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                   | Model-specific reference                                                                                                             |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Example source: IoT\_BASE\_SIM7080 | [Read example source: iot\_base\_sim7080](https://github.com/m5stack/IoT_BASE_SIM7080/tree/master/examples/MQTT)                     |
| Example source: IoT\_BASE\_SIM7080 | [Read example source: iot\_base\_sim7080](https://github.com/m5stack/IoT_BASE_SIM7080/tree/master/examples/Modbus/ModBus-RTU/Master) |
| Example source: IoT\_BASE\_SIM7080 | [Read example source: iot\_base\_sim7080](https://github.com/m5stack/IoT_BASE_SIM7080/tree/master/examples/Modbus/ModBus-RTU/Slave)  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
