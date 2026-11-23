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

# ATOMIC GPS Base

{% hint style="info" %}
[**View M5Stack ATOMIC GPS Base M5-A134 GNSS Module with microSD on OpenELAB**](https://openelab.io/products/atomic-gps-base)

**Store SKU / option:** `M5-A134`. Match the purchased model and revision to the official reference below.
{% endhint %}

### ATOMIC GPS Base

***

### Product Link

{% embed url="https://openelab.io/products/atomic-gps-base" %}

### Description <a href="#description" id="description"></a>

**Atomic GPS Base** is a GPS positioning module specifically designed for the ATOM series main controller. It incorporates the M8030-KT positioning navigation chip and is equipped with built-in FLASH memory. The module also includes a button cell battery that supports power-off retention of user configurations.The module finds applications in various scenarios, such as geographic coordinate viewing, bus stop announcements, vehicle and marine navigation, and trajectory tracking. It provides accurate positioning information that can be utilized in these applications.

Atomic GPS Base outputs data in the NMEA-0183 protocol, which is a common standard for GPS data communication. It supports multiple satellite systems, including GPS, GLONASS, GALILEO, BDS, SBAS, and QZSS. With a 72-channel search capability, it can accurately acquire and track satellite signals for precise positioning.

Furthermore, the Atomic GPS Base includes a MicroSD card slot located below the GPS module. This slot allows people to read GPS or other file data from a MicroSD card. For example, you can export GPS data in a specific format to view movement trajectories in map software. The module can also function as a regular card reader, enabling file reading and writing operations.

Regarding the UART parameter settings, the recommended settings for communication with the Atomic GPS Base are as follows:

UART Parameter Settings:

* Baud Rate (9600bps)
* Start Bit (1 bit)
* Stop Bit (1 bit)
* Parity Bit (None)

### Features <a href="#features" id="features"></a>

* Applicable to Atom Lite/Atom Matrix/AtomS3/AtomS3 Lite
* High signal acquisition sensitivity
* Support single system positioning of BDS / GPS / GLONASS / Galileo / SBAS / QZSS multiple satellite navigation systems
* Built in self elastic TF (microSD) card slot
* Low power

### Applications <a href="#applications" id="applications"></a>

* Vehicle and ship positioning and navigation
* Track record
* File reading and writing

### Specification <a href="#specification" id="specification"></a>

| Resources            | Parameters                                                                                                                                               |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Frequency accuracy   | GPS L1, GLONASS L1, BDS B1, GALILEO E1, SBAS L1, QZSS L1                                                                                                 |
| Accuracy             | Horizontal: 2m, Speed: 0.1m/s, Time: 1us                                                                                                                 |
| Channels             | 72 search channel                                                                                                                                        |
| Update frequency     | 1-10Hz                                                                                                                                                   |
| Maximum speed        | 515m/s                                                                                                                                                   |
| Maximum acceleration | < 4g                                                                                                                                                     |
| Sensitivity          | Trace: - 167dbm, capture: - 160dBm, cold start: - 148dbm, hot start: - 156dbm                                                                            |
| Start time           | Cold start: 26 seconds, warm start: 25 seconds, hot start: 1 second                                                                                      |
| Baud rate            | 9600bps                                                                                                                                                  |
| Output protocol      | NMEA-0183                                                                                                                                                |
| NMEA sentence        | RMC, VTG, GGA, GSA, GSV, GLL                                                                                                                             |
| Indicator light      | TX: the power on blue light flashes, indicating that there is data output, PPS:3D Blink after positioning, and it will not light if it is not positioned |
| Working temperature  | -40°C - 85°C                                                                                                                                             |
| Product Size         | 64\*18\*18mm                                                                                                                                             |
| Package Size         | 136\*92\*20mm                                                                                                                                            |
| Product Weight       | 14.4g                                                                                                                                                    |
| Package Weight       | 18.1g                                                                                                                                                    |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20GPS%20Base/img-c6106d8c-5518-4355-a565-69c615bef0c8.webp" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20GPS%20Base/pinMap-cc197554-37b7-43e1-8a1a-ea407a46be66.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20GPS%20Base/img-8659b3fd-a080-4f80-8e09-20fee5e18c45.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (399).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Atomic GPS Base](https://docs.m5stack.com/en/atom/Atomic_GPS_Base) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A134`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                         |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/atomic/atomic_gps_base)         |
| Example source: M5AtomS3     | [Read example source: m5atoms3](https://github.com/m5stack/M5AtomS3/tree/main/examples/AtomicBase/AtomicGPS/GPS) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
