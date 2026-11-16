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

# M5Stack Extend I/O

### M5Stack Extend I/O 2 Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-extend-io2-unit" %}

### Description <a href="#description" id="description"></a>

**EXT.IO2** is an `IO extended unit`, based on STM32F030 main controller, using I2C communication interface and providing 8 IO expansion. Each IO supports independent configuration of `digital I/O`, `ADC`, `SERVO control`, `RGB LED control` modes. Supports configuration of device I2C address, which means that users can mount multiple `EXT.IO2` UNITs on the same I2C BUS to extend more IO resources. Suitable for multiple digital/analog signal acquisition, with lighting/servo control applications.

### Features <a href="#features" id="features"></a>

* 8-channel input and output expansion.
  * Digital I/O
  * ADC input
  * SERVO control (PWM)
  * RGB LED control
* I2C communication interface:
  * Supports configuration of I2C address

### Applications <a href="#applications" id="applications"></a>

* IO Expansion
* Servo Control
* Multiple lighting control
* Multiple analog signal acquisition

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                | Parameters                                                |
| ----------------------------- | --------------------------------------------------------- |
| MCU                           | STM32F030                                                 |
| I2C Address                   | 0x45(default)                                             |
| Number of IO extensions       | 8                                                         |
| IO interface PIN spacing      | 2.54mm                                                    |
| IOSupport Mode                | Digital input/output, ADC, SERVO control, RGB LED control |
| IO Input/Output Level Support | 3.3V                                                      |
| Net Weight                    | 5g                                                        |
| Gross Weight                  | 13g                                                       |
| Product Size                  | 32\*24\*11mm                                              |
| Package Size                  | 93\*138mm                                                 |

### Pin Mapping <a href="#pin-mapping" id="pin-mapping"></a>

| M5Core(PORT A) | GPIO22 | GPIO21 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| EXT.IO2 Unit   | SCL    | SDA    | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/extio2/extio2_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/extio2/2024ab245eb708df4dcc36c00aee5b7.png" alt=""><figcaption></figcaption></figure>

### Communication protocols <a href="#communication-protocols" id="communication-protocols"></a>

MODE CONFIG

| REG  | DESC        | LEN    | R/W |
| ---- | ----------- | ------ | --- |
| 0x00 | MODE\_CH\_1 | 1 BYTE | R/W |
| 0x01 | MODE\_CH\_2 | 1 BYTE | R/W |
| 0x02 | MODE\_CH\_3 | 1 BYTE | R/W |
| 0x03 | MODE\_CH\_4 | 1 BYTE | R/W |
| 0x04 | MODE\_CH\_5 | 1 BYTE | R/W |
| 0x05 | MODE\_CH\_6 | 1 BYTE | R/W |
| 0x06 | MODE\_CH\_7 | 1 BYTE | R/W |
| 0x07 | MODE\_CH\_8 | 1 BYTE | R/W |

* Value:

```c
DIGITAL_INPUT_MODE=0 
DIGITAL_OUTPUT_MODE=1 
ADC_INPUT_MODE=2
SERVO_CTL_MODE=3 
RGB_LED_MODE=4
 
```

DIGITAL INPUT/OUTPUT

| REG  | DESC                       | LEN    | R/W |
| ---- | -------------------------- | ------ | --- |
| 0x10 | OUTPUT\_CTL\_REG\_CH\_1    | 1 BYTE | W   |
| 0x11 | OUTPUT\_CTL\_REG\_CH\_2    | 1 BYTE | W   |
| 0x12 | OUTPUT\_CTL\_REG\_CH\_3    | 1 BYTE | W   |
| 0x13 | OUTPUT\_CTL\_REG\_CH\_4    | 1 BYTE | W   |
| 0x14 | OUTPUT\_CTL\_REG\_CH\_5    | 1 BYTE | W   |
| 0x15 | OUTPUT\_CTL\_REG\_CH\_6    | 1 BYTE | W   |
| 0x16 | OUTPUT\_CTL\_REG\_CH\_7    | 1 BYTE | W   |
| 0x17 | OUTPUT\_CTL\_REG\_CH\_8    | 1 BYTE | W   |
| 0x20 | DIGITAL\_INPUT\_REG\_CH\_1 | 1 BYTE | R   |
| 0x21 | DIGITAL\_INPUT\_REG\_CH\_2 | 1 BYTE | R   |
| 0x22 | DIGITAL\_INPUT\_REG\_CH\_3 | 1 BYTE | R   |
| 0x23 | DIGITAL\_INPUT\_REG\_CH\_4 | 1 BYTE | R   |
| 0x24 | DIGITAL\_INPUT\_REG\_CH\_5 | 1 BYTE | R   |
| 0x25 | DIGITAL\_INPUT\_REG\_CH\_6 | 1 BYTE | R   |
| 0x26 | DIGITAL\_INPUT\_REG\_CH\_7 | 1 BYTE | R   |
| 0x27 | DIGITAL\_INPUT\_REG\_CH\_8 | 1 BYTE | R   |

* Value:

```c
HIGH:1 / LOW:0
 
```

8B ANALOG INPUT

| REG  | DESC                                            | LEN    | R/W |
| ---- | ----------------------------------------------- | ------ | --- |
| 0x30 | <p>ANALOG_INPUT_8B_REG_CH_1<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x31 | <p>ANALOG_INPUT_8B_REG_CH_2<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x32 | <p>ANALOG_INPUT_8B_REG_CH_3<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x33 | <p>ANALOG_INPUT_8B_REG_CH_4<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x34 | <p>ANALOG_INPUT_8B_REG_CH_5<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x35 | <p>ANALOG_INPUT_8B_REG_CH_6<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x36 | <p>ANALOG_INPUT_8B_REG_CH_7<br>Value: 0-255</p> | 1 BYTE | R   |
| 0x37 | <p>ANALOG_INPUT_8B_REG_CH_8<br>Value: 0-255</p> | 1 BYTE | R   |

12B ANALOG INPUT

| REG  | DESC                                              | LEN    | R/W |
| ---- | ------------------------------------------------- | ------ | --- |
| 0x40 | <p>ANALOG_INPUT_12B_REG_CH_1<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x42 | <p>ANALOG_INPUT_12B_REG_CH_2<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x44 | <p>ANALOG_INPUT_12B_REG_CH_3<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x46 | <p>ANALOG_INPUT_12B_REG_CH_4<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x48 | <p>ANALOG_INPUT_12B_REG_CH_5<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x4A | <p>ANALOG_INPUT_12B_REG_CH_6<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x4C | <p>ANALOG_INPUT_12B_REG_CH_7<br>Value: 0-4095</p> | 2 BYTE | R   |
| 0x4E | <p>ANALOG_INPUT_12B_REG_CH_8<br>Value: 0-4095</p> | 2 BYTE | R   |

SERVO ANGLE CTL

| REG  | DESC                                              | LEN    | R/W |
| ---- | ------------------------------------------------- | ------ | --- |
| 0x50 | <p>SERVO_ANGLE_8B_REG_CH_1<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x51 | <p>SERVO_ANGLE_8B_REG_CH_2<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x52 | <p>SERVO_ANGLE_8B_REG_CH_3<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x53 | <p>SERVO_ANGLE_8B_REG_CH_4<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x54 | <p>SERVO_ANGLE_8B_REG_CH_5<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x55 | <p>SERVO_ANGLE_8B_REG_CH_6<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x56 | <p>SERVO_ANGLE_8B_REG_CH_7<br>Value: 0-180deg</p> | 1 BYTE | R/W |
| 0x57 | <p>SERVO_ANGLE_8B_REG_CH_8<br>Value: 0-180deg</p> | 1 BYTE | R/W |

SERVO PULSE CTL

| REG  | DESC                                                 | LEN    | R/W |
| ---- | ---------------------------------------------------- | ------ | --- |
| 0x60 | <p>SERVO_PULSE_16B_REG_CH_1<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x62 | <p>SERVO_PULSE_16B_REG_CH_2<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x64 | <p>SERVO_PULSE_16B_REG_CH_3<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x66 | <p>SERVO_PULSE_16B_REG_CH_4<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x68 | <p>SERVO_PULSE_16B_REG_CH_5<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x6A | <p>SERVO_PULSE_16B_REG_CH_6<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x6C | <p>SERVO_PULSE_16B_REG_CH_7<br>Value: 500-2500us</p> | 2 BYTE | R/W |
| 0x6E | <p>SERVO_PULSE_16B_REG_CH_8<br>Value: 500-2500us</p> | 2 BYTE | R/W |

RGB LED CTL

| REG  | DESC                         | LEN    | R/W |
| ---- | ---------------------------- | ------ | --- |
| 0x70 | RGB\_24B\_REG\_CH\_1：RGB 888 | 3 BYTE | R/W |
| 0x73 | RGB\_24B\_REG\_CH\_2：RGB 888 | 3 BYTE | R/W |
| 0x76 | RGB\_24B\_REG\_CH\_3：RGB 888 | 3 BYTE | R/W |
| 0x79 | RGB\_24B\_REG\_CH\_4：RGB 888 | 3 BYTE | R/W |
| 0x7C | RGB\_24B\_REG\_CH\_5：RGB 888 | 3 BYTE | R/W |
| 0x7F | RGB\_24B\_REG\_CH\_6：RGB 888 | 3 BYTE | R/W |
| 0x82 | RGB\_24B\_REG\_CH\_7：RGB 888 | 3 BYTE | R/W |
| 0x85 | RGB\_24B\_REG\_CH\_8：RGB 888 | 3 BYTE | R/W |

Note: Do not write to the I2C address configuration register repeatedly at high frequency.

CONFIG

| REG  | DESC                                                                | LEN    | R/W |
| ---- | ------------------------------------------------------------------- | ------ | --- |
| 0xFE | FW VERSION                                                          | 1 BYTE | R   |
| 0xFF | I2C ADDR CONFIG (warn: Repeated writing may cause partition damage) | 1 BYTE | R/W |

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/extio2/3ad33fb83c15cac23cfb9ae5dccf684.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (387).png" alt=""><figcaption></figcaption></figure>
