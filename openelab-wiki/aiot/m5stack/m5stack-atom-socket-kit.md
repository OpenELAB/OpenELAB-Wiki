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

# M5Stack ATOM Socket Kit

### M5Stack ATOM Socket Kit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-atom-socket-kit" %}

### Description <a href="#description" id="description"></a>

**ATOM Socket CN** is a smart power socket adapted to ATOM main control. Built-in HLW8032 high-precision energy metering IC, through the serial port communication can read the electrical parameters (line voltage, current, active power, apparent power and power factor) of the socket. The external jack adopts Chinese standard specifications, and the internal integrated single-circuit relay (AC-220V@10A) is used to control the power on and off of the socket. With the ATOM main control integrated with WiFi module, the power socket can be easily connected to the network for remote control And electric energy metering. The extra socket integrates HY2.0-4P interface, which can interact with external devices (relay signal input, key signal output).

### Features <a href="#product-features" id="product-features"></a>

* Single relay control socket power on and off (AC:220V@10A/DC:28V@10A)
* HLW8032 High Precision Energy Metering IC
* Support voltage and current detection power calculation, within 1000:1 dynamic range:
  * The measurement error of active power reaches 0.2%
  * The effective current measurement error reaches 0.5%
  * The effective voltage measurement error reaches 0.5%
* UART communication (baud: 4800)
* ∑-Δ ADC, high-precision energy metering core
* China standard jack
* HY2.0-4P external control interface

### Includes <a href="#includes" id="includes"></a>

* 1x ATOM Socket CN
* 1x ATOM LITE

### Application <a href="#application" id="application"></a>

* Metering socket
* Smart WIFI socket
* Smart home appliance control

### Specification <a href="#specification" id="specification"></a>

| Resources                                   | Parameter                |
| ------------------------------------------- | ------------------------ |
| HLW8032 serial port communication baud rate | 4800                     |
| Recommended load power                      | <=1000W                  |
| Relay parameters                            | AC:220V@10A / DC:28V@10A |
| Net weight                                  | 104g                     |
| Gross weight                                | 116.6g                   |
| Product size                                | 90\*42\*55mm             |
| Package size                                | 92\*62\*42mm             |

![](https://static-cdn.m5stack.com/resource/docs/products/atom/atom_socket_cn/atom_socket_cn_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/atom/atom_socket_cn/atom_socket_cn_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/atom/atom_socket_cn/atom_socket_cn_06.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a simple and fast program burner, which has a built-in product-related case program, which can be burned to the main control through simple steps to perform a series of functional verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/ATOM_BASE/EasyLoader_Atom_Socket.exe)

{% embed url="https://m5stack.oss-cn-shenzhen.aliyuncs.com/video/Product_example_video/AtomBase/ATOM_SOCKET_CN.mp4" %}

**Description:**\
Remotely control the ATOM Socket on and off the power supply, and monitor the power status

#### Pinout <a href="#pin-mapping" id="pin-mapping"></a>

| ATOM        | G22 | G23   |
| ----------- | --- | ----- |
| ATOM Socket | RX  | Relay |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/atom_socket/atom_socket_sch_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/atom_socket/atom_socket_sch_02.webp" alt=""><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

-**Datasheet** - [HLW8032](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/atombase/atom_socket/DS_HLW8032_CN.pdf)

### Learn <a href="#learn" id="learn"></a>

![Identifying Household Load Using QuickFeather and SensiML](https://hackster.imgix.net/uploads/attachments/1306046/_NCv03rfSd2.blob?auto=compress%2Cformat\&w=400\&h=300\&fit=min)

[Identifying Household Load Using QuickFeather and SensiML](https://www.hackster.io/naveenbskumar/identifying-household-load-using-quickfeather-and-sensiml-d3303b)

Non-intrusive energy consumption analysis for effective climate change mitigation using machine learning at the edge.

### Example <a href="#example" id="example"></a>

* [Arduino code example](https://github.com/m5stack/M5Atom/tree/master/examples/ATOM_BASE/ATOM_Socket)
