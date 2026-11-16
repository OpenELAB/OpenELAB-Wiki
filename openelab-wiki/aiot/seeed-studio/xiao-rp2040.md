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

# XIAO RP2040

### Seeed Studio XIAO RP2040 Supports Arduino

***

### Product Link

{% embed url="https://openelab.io/products/xiao-rp2040-supports-arduino" %}

### Description <a href="#description" id="description"></a>

The Seeed Studio XIAO RP2040 is as small as the Seeed Studio XIAO SAMD21 but it's more powerful. On one hand, it carries the powerful Dual-core RP2040 processor that can flexible clock running up to 133 MHz which is a low-power microcontrollers. On the Seeed Studio XIAO RP2040 there is also 264KB of SRAM, and 2MB of on-board Flash memory which can provide more program to save and run. On the other hand, this little board has good performance in processing but needs less power.\
All in all, it is designed in a tiny size as small as a thumb(21x17.8mm) and can be used for wearable devices and small projects.

There are 14 GPIO PINs on Seeed Studio XIAO RP2040, on which there are 11 digital pins, 4 analog pins, 11 PWM Pins,1 I2C interface, 1 UART interface, 1 SPI interface, 1 SWD Bonding pad interface.

Seeed Studio XIAO RP2040 is compatible to the Seeed Studio XIAO expansion board.

### Features <a href="#features" id="features"></a>

* Powerful MCU: Dual-core ARM Cortex M0+ processor, flexible clock running up to 133 MHz
* Rich on-chip resources: 264KB of SRAM, and 2MB of on-board Flash memory
* Flexible compatibility: Support Micropython/Arduino/CircuitPython
* Easy project operation: Breadboard-friendly & SMD design, no components on the back
* Small size: As small as a thumb(21x17.8mm) for wearable devices and small projects.
* Multiple interfaces: 11 digital pins, 4 analog pins, 11 PWM Pins,1 I2C interface, 1 UART interface, 1 SPI interface, 1 SWD Bonding pad interface.

### Specifications <a href="#specifications" id="specifications"></a>

| Item                                   | Value                                           |
| -------------------------------------- | ----------------------------------------------- |
| CPU                                    | Dual-core ARM Cortex M0+ processor up to 133MHz |
| Flash Memory                           | 2MB                                             |
| SRAM                                   | 264KB                                           |
| Digital I/O Pins                       | 11                                              |
| Analog I/O Pins                        | 4                                               |
| PWM Pins                               | 11                                              |
| I2C interface                          | 1                                               |
| SPI interface                          | 1                                               |
| UART interface                         | 1                                               |
| Power supply and downloading interface | Type-C                                          |
| Power                                  | 3.3V/5V DC                                      |
| Dimensions                             | 21×17.8×3.5mm                                   |

### Hardware <a href="#schematics" id="schematics"></a>

<img src="https://files.seeedstudio.com/wiki/XIAO-RP2040/img/xinpin.jpg" alt="pir" width="600">

For general I/O pins: Working voltage of MCU is 3.3V . Voltage input connected to general I/O pins may cause chip damage if it' higher than 3.3V .

For power supply pins: The built-in DC-DC converter circuit able to change 5V voltage into 3.3V allows to power the device with a 5V supply via VIN-PIN and 5V-PIN.

XIAO RP2040 currently only supports battery power supply and cannot connect to Type-C while a battery is connected, as it may pose a safety risk.

Please pay attention to use, do not lift the shield cover.

#### Enter Bootloader Mode <a href="#enter-bootloader-mode" id="enter-bootloader-mode"></a>

Sometimes the Seeed Studio XIAO RP2040 port may disappear when user programming process fails. we can solve this problem by the following operation:

* Long press the "B" button.
* Connect the Seeed Studio XIAO PR2040 to your computer.
* The computer will appear a disk driver.

At this point, the chip enters Bootloader mode and the burn port appears again. Because the RP2040 chip has two partitions, one is the Bootloader and the other is the user program. The product will burn a bootloader code in the system memory when it leaves the factory. We can switch modes by performing the above steps.

#### Reset <a href="#reset" id="reset"></a>

If you want to reset the Seeed Studio XIAO RP2040, perform the following steps:

* Connect the Seeed Studio XIAO RP2040 to your computer.
* Press the "R" pins **once**.

Please note: The behavior of the built-in programmable Single-colour LEDs (They are red, blue and green) are reversed to the one on an Arduino. On the Seeed Studio XIAO RP2040, the pin has to be pulled low to enable.

<img src="https://files.seeedstudio.com/wiki/XIAO-RP2040/img/xinfront.jpg" alt="pir" width="600">

### Schematics <a href="#schematics" id="schematics"></a>

<div align="center"><figure><img src="../../.gitbook/assets/image (351).png" alt=""><figcaption></figcaption></figure></div>
