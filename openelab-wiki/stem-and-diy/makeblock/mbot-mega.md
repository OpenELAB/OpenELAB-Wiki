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

# mBot Mega

### mBot Mega

***

<figure><img src="../../.gitbook/assets/爆炸图 (1).png" alt=""><figcaption></figcaption></figure>

### Product Link

{% embed url="https://openelab.io/products/makeblock-mbot-mega-smart-remote-control-robot-car" %}

### Introduction

mBot Mega is a programmable robot with a metal structure. It offers gesture recognition, automatic line tracking, and obstacle avoidance features, and supports programming based on Hui Programming, Arduino IDE, and Raspberry Pi interfaces. mBot Mega is equipped with four Mecanum wheels. Compared to ordinary wheels, Mecanum wheels make mBot Mega more flexible and versatile in movement, making it a better choice for learning robot motion algorithms.

### Features

#### Programming Environment

● Arduino C Programming, Wise Programming Graphical Programming

#### 3 functions Function switching

● Long press function switching Press any of the collision sensors until the color of the RGB light changes.

&#x20;● Green: Gesture Recognition, Blue: Auto Line Patrol, Yellow: Auto Obstacle Avoidance

<figure><img src="../../.gitbook/assets/1.png" alt=""><figcaption></figcaption></figure>

#### Gesture Recognition (power-on default feature)

<figure><img src="../../.gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>

● Light colour: green

● Standby status: both RGB modules are dark green.

● When the obstacle avoidance sensor detects an obstacle, the RGB LED turns bright green.

● The three assembled IR obstacle avoidance sensors can detect three states at a distance of 3-10cm:

&#x20; Slide to the right: when the obstacle avoidance sensors 3 and 2 or sensors 2 and 1 detect signals in sequence, the robot moves to the right by about 10 cm. the RGB LED on the right side turns bright green when the robot moves, and returns to dark green when the robot stops.

&#x20; Slide to the left: when the obstacle avoidance sensors 1,2 or sensors 2,3 detect the signal in sequence, the robot moves to the left about 10cm. when the robot moves, the RGB LED on the left side turns bright green and returns to dark green when the robot stops.

&#x20; Push: When obstacle avoidance sensors 1 and 3 detect the signal at the same time for more than 0.2 seconds, it is judged to be a push gesture, and both the left and right RGB LEDs turn bright green, and the robot moves backward.

● When all sensors fail to detect the signal, mBot Mega stops moving and the RGB LEDs revert to dark green

#### Automated obstacle avoidance

<figure><img src="../../.gitbook/assets/2 (1).png" alt=""><figcaption></figcaption></figure>

● Light colour: yellow

● When no obstacle is detected, all LEDs light up dim yellow.

● When an obstacle is detected by any of the IR sensors, all LEDs light up bright yellow.

● After switching to the automatic obstacle avoidance mode, move according to the status of the three sensors:

&#x20; Forward: forward when none of the three sensors detect an obstacle

&#x20;Turn left : when obstacle avoidance sensor 1 detects an obstacle, it will rotate about 90 degrees clockwise at the scene.

&#x20; Turn right: when obstacle avoidance sensor 3 detects an obstacle, it rotates approximately 90 degrees counterclockwise on the spot.

&#x20; Turn Backward: When Obstacle Avoidance Sensor 2 detects an obstacle, it will move backward about 5cm.

#### Automatic line patrol

● Light colour: blue&#x20;

● When the wire patrol sensor does not detect black, the RGB light is low blue.&#x20;

● When the wire patrol sensor detects black, the RGB light on the corresponding side is high blue.&#x20;

● After switching to line patrol mode, if any line patrol sensor detects black, it will start to patrol; if both line patrol sensors cannot detect black, rotate in place for 5 seconds until black is detected and then start to patrol; if black is still not detected after 5 seconds, stop the movement and wait for black to be detected and then start to patrol again (wait for manually placing it on the black line).

### Specifications

#### TT motor:&#x20;

● Voltage use range: 2.4-6V&#x20;

● Rated no-load speed: 118±10%RPM&#x20;

● Rated load speed: 84±10%RPM (0.3kg.cm)

#### MegaPi Master Board:

<figure><img src="../../.gitbook/assets/3.png" alt=""><figcaption></figcaption></figure>

#### Specification Parameters

| Product Parameter             | **描述**          |
| ----------------------------- | --------------- |
| product code                  | 10050           |
| controller chip               | ATMEGA2560-16AU |
| Input Voltage/Current         | DC 6-12V 10A    |
| working voltage               | DC 5V           |
| General Purpose I/O Pin       | 43              |
| serial port                   | 3               |
| I2C interface                 | 1               |
| SPI interface                 | 1               |
| Analogue Input                | 15              |
| DC current rating per I/O pin | 20mA            |
| flash                         | 256KB           |
| RAM                           | 8KB             |
| EEPROM                        | 4KB             |
| main frequencies              | 16MHz           |
| Product Dimension             | 86mm×53mm       |

#### Infrared obstacle avoidance sensor

● Detectable range: light-coloured objects that can reflect infrared rays within the range of 20-120mm.

● Returns low (0) when an obstacle is detected, otherwise returns high.&#x20;

● Adjust the maximum triggering distance by rotating the potentiometer, decreasing when rotating clockwise and increasing when rotating anti-clockwise.

<div align="center"><figure><img src="../../.gitbook/assets/红外避障传感器.png" alt="" width="460"><figcaption></figcaption></figure></div>

#### Patrol Sensor

Detectable range: within 2-20mm, outputs a high level when light colours (surfaces that reflect infrared light) are detected, otherwise outputs a low level (0).

<figure><img src="../../.gitbook/assets/巡线传感器.png" alt=""><figcaption></figcaption></figure>

#### Crash sensor (limit switch)

● Outputs a low level when the key is pressed and a high level when the state is released.

<figure><img src="../../.gitbook/assets/碰撞传感器.png" alt=""><figcaption></figcaption></figure>

#### RGB light module

● 4 RGB LEDs can be controlled individually, refer to the following diagram for LED serial numbers

<figure><img src="../../.gitbook/assets/RGB灯模块.png" alt=""><figcaption></figcaption></figure>

### Assembly

#### Learning to use a screwdriver

&#x20;● The screwdriver has a Phillips screw and a hexagon socket head screw at each end, so you can use them interchangeably depending on the situation.

#### Structural assemblies

Mounting the left motor bracket

<figure><img src="../../.gitbook/assets/01_安装左电机支架.gif" alt=""><figcaption></figcaption></figure>

Mounting the right motor bracket

<figure><img src="../../.gitbook/assets/02_安装右电机支架.gif" alt=""><figcaption></figcaption></figure>

Installation of wire patrol sensors

<figure><img src="../../.gitbook/assets/03_安装巡线传感器.gif" alt=""><figcaption></figcaption></figure>

Attachment of motor bracket

<figure><img src="../../.gitbook/assets/04_连接电机支架.gif" alt=""><figcaption></figcaption></figure>

Installing the motor drive module

<figure><img src="../../.gitbook/assets/05_安装电机驱动模块.gif" alt=""><figcaption></figcaption></figure>

Mounting Megapi to the car

<figure><img src="../../.gitbook/assets/06_将Megapi安装到车身上.gif" alt=""><figcaption></figcaption></figure>

Installing the Battery

<figure><img src="../../.gitbook/assets/安装18650电池.gif" alt=""><figcaption></figcaption></figure>

Mounting the Infrared Obstacle Avoidance Sensor to the Upper Cover Plate

<figure><img src="../../.gitbook/assets/07_将红外避障传感器安装到上盖板.gif" alt=""><figcaption></figcaption></figure>

Mounting the body shell to the motor mount

<figure><img src="../../.gitbook/assets/08_将车身外壳安装到电机支架上.gif" alt=""><figcaption></figcaption></figure>

#### Connecting the electronic modules

Connect the motor

<figure><img src="../../.gitbook/assets/09_连接电机.jpg" alt=""><figcaption></figcaption></figure>

Connection sequence of the electronic modules

<figure><img src="../../.gitbook/assets/0.png" alt=""><figcaption></figcaption></figure>

Corresponding positions of electronic modules

<figure><img src="../../.gitbook/assets/QQ20241211-120513.png" alt=""><figcaption></figcaption></figure>

#### Mounting the top cover plate&#x20;

● 3pin connection method provides more freedom. Compatible with almost all 3pin electronic parts, such as sensors, light strips, etc.

<figure><img src="../../.gitbook/assets/12_连接MegaPi 所有电子模块和电机。.gif" alt=""><figcaption></figcaption></figure>

If the battery is low during use, the robot will not work properly (e.g. Bluetooth disconnection, underpowered motors, etc.).

### Dimensions

<figure><img src="../../.gitbook/assets/4.png" alt=""><figcaption></figcaption></figure>

### How to Use

Software Installation

Installing Wise Programming：

Wise Programming is a graphical programming software independently developed by Kid's Maker for the STEAM education field, with over 10 million users using it to create, learn and share. It not only allows users to create interesting stories, games, animations, etc. in the software, but also allows them to programme hardware such as Makeblock system, micro:bit, Arduino, etc. It supports switching code languages such as Python with one click. Wise Programming supports one-click switching of code languages such as Python and provides Python input mode, while incorporating cutting-edge technologies such as AI (Artificial Intelligence) and IoT (Internet of Things).

Versions：

● PC (need to download and install software)：

{% embed url="https://mblock.cc/pages/downloads?zhbanner" %}

● Web-side (no need to install software, you can program on the web page):

[https://ide.makeblock.com/](https://ide.makeblock.com/)

● Wise Programming Mobile allows you to enjoy programming on mobile devices. You can download the Wise Programming App by searching for ‘Wise Programming’ in major app shops.

#### Download and install mLink on your computer

In order to connect the hardware on the web side of Wise Programming, we need to install the Wise Programming Assistant (mLink).

Download mLink to your computer by visiting this website:

{% embed url="https://mblock.cc/pages/downloads" %}

<figure><img src="../../.gitbook/assets/5.png" alt=""><figcaption></figcaption></figure>

Add the mBot Mega from the device library

<figure><img src="../../.gitbook/assets/6.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/7.png" alt=""><figcaption></figcaption></figure>

Connect mBot Mega and update firmware. Connect the mBot Mega to your computer using the USB cable and click Connect to start connecting the device.

RGB control:

Use the data cable to connect MegaPi motherboard and computer, use the jumper cable to connect the RGB module to MegaPi motherboard, and open the Wise Programming Tool (desktop, web, and mobile are all available), click on Add, select mBot Mega in the Device Library, click on Connect and switch to Upload Mode.

Flashing: When the power is turned on, the RGB module produces the phenomenon of alternating light on and off.

<figure><img src="../../.gitbook/assets/16.png" alt=""><figcaption></figcaption></figure>

Light up one by one: switch on the power, the RGB lights on the RGB module light up one by one, and when all the lights are lit, all of them turn off.

<figure><img src="../../.gitbook/assets/17.png" alt=""><figcaption></figcaption></figure>

When the obstacle avoidance sensor detects an obstacle, the RGB light is on, otherwise the RGB light is off.

<figure><img src="../../.gitbook/assets/20.png" alt=""><figcaption></figcaption></figure>

When the wire patrol sensor detects a black wire, the RGB lamp lights up, otherwise the RGB lamp goes out.

<figure><img src="../../.gitbook/assets/21.png" alt=""><figcaption></figcaption></figure>

When the collision sensor detects an impact, the RGB light illuminates, otherwise the RGB light goes out.

<figure><img src="../../.gitbook/assets/22.png" alt=""><figcaption></figcaption></figure>

Breathing light

<figure><img src="../../.gitbook/assets/23.png" alt=""><figcaption></figcaption></figure>

running light

<figure><img src="../../.gitbook/assets/24.png" alt=""><figcaption></figcaption></figure>

running horse lamp

<figure><img src="../../.gitbook/assets/25.png" alt=""><figcaption></figcaption></figure>

One second forward, one second back, and the cycle is executed

<figure><img src="../../.gitbook/assets/31.png" alt=""><figcaption></figcaption></figure>

One second to the left, one second to the right. Cycle through.

<figure><img src="../../.gitbook/assets/30.png" alt=""><figcaption></figcaption></figure>

One second left panning, one second right panning

<figure><img src="../../.gitbook/assets/29.png" alt=""><figcaption></figcaption></figure>

4 - 45° movement

<figure><img src="../../.gitbook/assets/32.png" alt=""><figcaption></figcaption></figure>

Robot Dance

<figure><img src="../../.gitbook/assets/33.png" alt=""><figcaption></figcaption></figure>

Robot obstacle avoidance

<figure><img src="../../.gitbook/assets/34.png" alt=""><figcaption></figcaption></figure>

Robot patrols

<figure><img src="../../.gitbook/assets/35.png" alt=""><figcaption></figcaption></figure>

### FAQ

<details>

<summary>Will downloading mBlock 5 replace mBlock 3 now? </summary>

No, it will not replace mBlock 3, the two software will co-exist in your computer. You can use mBlock 3 and mBlock 5 at the same time!

</details>

<details>

<summary>Windows version download mBlock 5 after opening the interface blank what is the situation? </summary>

Your computer system graphics card version is too low, you need to upgrade the system graphics card driver, it is recommended to use the driver wizard.

</details>

<details>

<summary>Does the installation of Wise Programming for PC have any requirements on the CPU and RAM of the computer? </summary>

There is no specific requirement for CPU and memory. You can use Wise Programming as long as your computer has OSX or Win7 or above installed.

</details>

<details>

<summary>What is the best browser to use when using Wise Programming Online Editor? </summary>

Recommended to use chrome browser, the best experience. Available for download on the official website:[https://www.google.cn/chrome/](https://www.google.cn/chrome/)

</details>

<details>

<summary>When installing Wise Programming, the 360 pop-up window prompts ‘A program is trying to modify the key program DLL file’, how to solve it?</summary>

When this happens, select ‘Allow this operation’.

</details>

<details>

<summary>The first time I installed Wise Programming, it was intercepted by the computer butler, how to solve it?</summary>

When this happens, please select ‘Allow changes’.

</details>

<details>

<summary>When using 360 Software Manager to uninstall Hui Programming, the interception prompts a programme is modifying the system key settings, how to solve?</summary>

When this happens, select ‘Allow this operation’.

</details>
