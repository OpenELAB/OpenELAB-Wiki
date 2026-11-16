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

# XIAO MG24 Sense

Seeed Studio XIAO MG24 Sense Silicon Labs EFR32MG24 BLE 5.3

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-mg24-sense-silicon-labs-efr32mg24" %}

### Description

Seeed Studio XIAO MG24 is a mini development board based on Silicon Labs' MG24. XIAO MG24 is based on ARM Cortex-M33 core, 32-bit RISC architecture with a maximum clock speed of 78MHz, supporting DSP instructions and FPU floating-point operations, possessing powerful computing power, and built-in AL/ML hardware accelerator MVP, which can efficiently process AI/machine learning algorithms. Secondly, it has excellent RF performance, with a transmission power of up to+19.5 dBm and a reception sensitivity as low as -105.4 dBm. It supports multiple IoT and wireless transmission protocols such as Matter, Thread, Zigbee, Bluetooth LE 5.3,Bluetooth mesh etc.

### Features

* **Powerful CPU**:ARM Cortex-M33 core, with a maximum clock speed of 78MHz, supporting DSP instructions and FPU floating-point operations, 32-bit RISC architecture.
* **Ultra-Low Power**:RX current 4.6mA/TX current 5mA (0dBm), multiple low-power sleep modes
* **Powerful AI**:Built in AI/ML hardware accelerator MVP, capable of efficiently processing AI/machine learning algorithms.
* **Multi style wireless transmission**:Integrated 2.4GHz multi protocol wireless transceiver, supporting multiple IoT protocols such as Matter, OpenThread, Zigbee, Bluetooth LE 5.3, Bluetooth mesh, etc.
* **Better RF Performance**:Excellent RF performance, with a transmission power of up to+19.5 dBm and a reception sensitivity as low as -105.4 dBm (250kbps DSSS)
* **Powerful security**:Powerful security features of Secure Vault, including secure boot, encryption, random number generation, tamper proof, secure debugging, etc.
* **Ultra-small size**:21 x 17.8mm.
* **Rich on-chip resources**:Maximum 1536KB Flash and 256KB RAM, with ample storage space.
* **Rich interfaces**:Integrated with 12 bit 1Msps ADC, temperature sensor, analog comparator, DCDC and other rich peripherals, and up to 22 Pin, 2 USART, 2 low-power UART, 1 IIC and other interfaces.

### Specification

| Item                                | Seeed Studio XIAO MG24                                                                                                                    | Seeed Studio XIAO MG24 Sense                                                                                                              |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Processor                           | <p>Silicon Labs EFR32MG24<br>ARM Cortex-M33 @ 78MHz</p>                                                                                   |                                                                                                                                           |
| Wireless                            | <p>Complete 2.4GHz Wi-Fi subsystem<br>BLE: Bluetooth 5.3, Bluetooth mesh</p>                                                              |                                                                                                                                           |
| Built-in Sensors                    | -                                                                                                                                         | <p>6-Axis IMU(LSM6DS3TR-C)<br>Analog Microphone(MSM381ACT001)</p>                                                                         |
| Memory                              | 256kB RAM & 1538KB + 4MB Flash                                                                                                            | 256kB RAM & 1538KB + 4MB Flash                                                                                                            |
| Interface                           | <p>2x UART, 1x IIC, 2x SPI, 18x Analog, 18x Digital, ALL PWM, 1x User LED, 1x Charge LED<br>1x Reset button,</p>                          | <p>2x UART, 1x IIC, 2x SPI, 18x Analog, 18x Digital, ALL PWM, 1x User LED, 1x Charge LED<br>1x Reset button,</p>                          |
| Dimensions                          | 21 x 17.8mm                                                                                                                               | 21 x 17.8mm                                                                                                                               |
| Power                               | <p>Input voltage (Type-C): 5V@14mA<br>Input voltage (BAT): 3.7V@7mA</p>                                                                   |                                                                                                                                           |
| Charging battery current: **200mA** | Charging battery current: **200mA**                                                                                                       |                                                                                                                                           |
| Low Power Consumption Model         | <p>Normal: <strong>3.7V/6.71 mA</strong><br>Sleep Mode: <strong>3.7V/1.91mA</strong><br>Deep Sleep Mode: <strong>3.7V/1.95μA</strong></p> | <p>Normal: <strong>3.7V/6.71 mA</strong><br>Sleep Mode: <strong>3.7V/1.91mA</strong><br>Deep Sleep Mode: <strong>3.7V/1.95μA</strong></p> |
| Working Temperature                 | -20°C \~ 70°C                                                                                                                             |                                                                                                                                           |

### Hardware[​](https://wiki.seeedstudio.com/xiao_mg24_getting_started/#hardware-overview) <a href="#hardware-overview" id="hardware-overview"></a>

| XIAO MG24 Sense indication diagram                                                                         |
| ---------------------------------------------------------------------------------------------------------- |
| <p><img src="https://files.seeedstudio.com/wiki/XIAO_MG24/Getting_Start/mg24sense_pinlist.png" alt=""></p> |
| XIAO MG24 indication diagram                                                                               |
| <p><img src="https://files.seeedstudio.com/wiki/XIAO_MG24/Getting_Start/mg24_pinlist.png" alt=""></p>      |
| XIAO MG24/ XIAO MG24(Sense) Pin List                                                                       |
| <p><img src="https://files.seeedstudio.com/wiki/XIAO_MG24/Getting_Start/modifyMG24.png" alt=""></p>        |
|                                                                                                            |

**tip:**

The difference between the two development boards is that MG24 Sense has a microphone sensor and a six axis acceleration sensor, while MG24 does not have one.

* 5V - This is 5v out from the USB port. You can also use this as a voltage input but you must have some sort of diode (schottky, signal, power) between your external power source and this pin with anode to battery, cathode to 5V pin.
* 3V3 - This is the regulated output from the onboard regulator.
* GND - Power/data/signal ground

### Battery Usage[​](https://wiki.seeedstudio.com/xiao_mg24_getting_started/#battery-usage) <a href="#battery-usage" id="battery-usage"></a>

The XIAO MG24 has a built-in power management chip that allows the XIAO MG24 to be powered independently by using a battery or to charge the battery through the XIAO MG24's USB port.

If you want to connect the battery for XIAO, we recommend you to purchase qualified rechargeable 3.7V lithium battery. When soldering the battery, please be careful to distinguish between the positive and negative terminals. The negative terminal of the power supply should be the side closest to the USB port, and the positive terminal of the power supply is the side away from the USB port.

<div align="center"><img src="https://files.seeedstudio.com/wiki/XIAO_MG24/Getting_Start/4444.png" alt="pir" width="800"></div>

**caution:**

Please be careful not to short-circuit the positive and negative terminals and burn the battery and equipment when soldering.

**Instructions on the use of batteries:**

1. Please use qualified batteries that meet the specifications.
2. XIAO can be connected to your computer device via data cable while using the battery, rest assured that XIAO has a built-in circuit protection chip, which is safe.
3. The XIAO MG24 will not have any LED on when it is battery powered (unless you have written a specific program), please do not judge whether the XIAO MG24 is working or not by the condition of the LED, please judge it reasonably by your program.
4. Sorry, we currently have no way to help you check the remaining battery level through software (because there are no more chip pins available), you need to charge the battery regularly or use a multimeter to check the battery level.

At the same time, we designed a red indicator light for battery charging, through the indicator light display to inform the user of the current state of the battery in the charge.

1. When XIAO MG24 is not connected to the battery, the red light comes on when the Type-C cable is connected and goes off after 30 seconds.
2. The red light flashes when the battery is connected and the Type-C cable is connected for charging.
3. When connecting Type-C to charge the battery fully, the red light turns off.
