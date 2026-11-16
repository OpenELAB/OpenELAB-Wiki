# M5GO Battery Bottom2

### M5Stack M5GO Battery Bottom2

***

### Product Link

{% embed url="https://openelab.io/products/m5go-battery-bottom2" %}

### Description <a href="#description" id="description"></a>

**M5GO BOTTOM2** is an expansion base designed for M5Core2. It integrates an MPU6886 6 axis gyro/accelerometer,digital mic(SPM1423) and 500mAh LiPo battery. The base also includes 2 HY2.0-4P expansion ports capable of ADC/DAC/UART protocols and data input/output,which allows the use of units from the M5Stack range. On either side of the base beneath a diffuser are a total of 10 programmable RGB LEDs(SK6812),which can be used as a form of notification or for impressive lighting effects. Beneath the device are a set of pogo pins which can attach to a charging base (excluded) for charging. The pogo pin connector can also be used for I2C communication, therefore if the user wants to attach or modify the base to include I2C devices they are able to do so. On the bottom of the device are an array of Lego™ compatible holes which makes integration of your Lego™ projects a breeze.

### Features <a href="#features" id="features"></a>

* Compatible with M5Core2
* Digital microphone
* Programmable RGB LED
* 500mAh LiPo battery
* HY2.0-4P expansion ports
* Lego™ compatible
* Pogo Pin magnetic charging

### Specifications <a href="#specifications" id="specifications"></a>

| Resources            | Parameter     |
| -------------------- | ------------- |
| Mic                  | SPM1423       |
| LED                  | SK6812\*10    |
| IMU                  | MPU6886       |
| Net Weight           | 31g           |
| Gross Weight         | 45g           |
| Product Dimensions   | 54\*54\*8mm   |
| Packaging Dimensions | 192\*92\*20mm |

![](https://static-cdn.m5stack.com/resource/docs/products/base/m5go_bottom2/m5go_bottom2_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/base/m5go_bottom2/m5go_bottom2_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/base/m5go_bottom2/m5go_bottom2_06.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/BASE/EasyLoader_M5GO_BOTTOM2.exe)

**Description:**\
IMU data acquisition, microphone data acquisition Display spectrum, control LED blinking.

### Pin Mapping <a href="#pin-mapping" id="pin-mapping"></a>

**SK6812-LED Bar**

| ESP32 Chip | GPIO25 |
| ---------- | ------ |
| SK6812     | DATA   |

**SPM1423-Mic**

| ESP32 Chip | GPIO34 | GPIO0 |
| ---------- | ------ | ----- |
| SPM1423    | DAT    | CLK   |

**MPU6886 & Pogo Pin**

| ESP32 Chip | GPIO21 | GPIO22 |
| ---------- | ------ | ------ |
| MPU6886    | SDA    | SCL    |
| Pogo Pin   | SDA    | SCL    |

**HY2.0-4P-PortB(black)**

| ESP32 Chip | GPIO26      | GPIO36      |
| ---------- | ----------- | ----------- |
| PortB      | GPIO26(DAC) | GPIO36(ADC) |

**HY2.0-4P-PortC(blue)**

| ESP32 Chip | GPIO13       | GPIO14       |
| ---------- | ------------ | ------------ |
| PortC      | GPIO13(RXD2) | GPIO14(TXD2) |

**M5GO-BOTTOM2-BUS**

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/base/m5go_bottom2/m5go_bottom2_bus_01.webp" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/base/m5go_bottom2/m5go_bottom2_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

* [SPM1423](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/SPM1423HM4H-B_datasheet_en.pdf)
* [MPU6886](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/MPU-6886-000193%2Bv1.1_GHIC_en.pdf)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Click here to download the Arduino example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Base/M5GO_BOTTOM2)

### FAQ <a href="#faq" id="faq"></a>

<details>

<summary><strong>CoreMP135 which ttySTMx for RS485 PORT, UART PORT?</strong></summary>

UART PROT(PORT C): /dev/ttySTM0 RS485 PORT: /dev/ttySTM3

</details>

<details>

<summary><strong>Unitv2 How use NanoDetPlus models?</strong></summary>

1\. The current application environment of unitv2 does not support NanoDetPlus, only supports NanoDet\_old. The latest NanoDetPlus requires writing NCNN C++ inference code by yourself to use. 2.unitv2 supports custom deployment of ncnn models, but you need to write NCNN C++ programs by yourself. We provide the relevant SDK (https://github.com/m5stack/UnitV2Framework.git). Third: unitv2 runs on the Linux system, which means you can easily perform remote operations.

</details>

<details>

<summary><strong>Can use Atom Echo with Atomic SPK Base?</strong></summary>

Atom Echo some GPIO is used for I2S. so can't stack with other Atomic Base

</details>
