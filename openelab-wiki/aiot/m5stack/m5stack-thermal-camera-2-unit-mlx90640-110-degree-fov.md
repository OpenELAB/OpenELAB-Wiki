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

# M5Stack Thermal Camera 2 Unit (MLX90640) -110 Degree FoV

## M5Stack Thermal Camera 2 Unit

***

### Product Link

{% embed url="https://openelab.io/products/thermal-camera-2-unit" %}

### Introduction

UNIT Thermal2 is a data processing MCU-equipped MLX90640 thermal imaging acquisition unit. It has 32x24 imaging pixels, a field of view of 110°x75°, and a temperature measurement range of -40°C to 300°C. The MCU uses ESP32, which is capable of high and low temperature alarms, average, maximum and minimum values reading, and data caching via data processing. The board integrates with a buzzer, RGB indicator, function and reset buttons, and communicates with the host computer through I2C. This product can be used together with the host computer or separately, and is applicable for temperature measurement and abnormal alarms.

<figure><img src="../../.gitbook/assets/image (478).png" alt=""><figcaption></figcaption></figure>

### Features

* MCU:ESP32-PICO-D4
* MLX90640 Infrared (IR) Sensor
* Reset buttom
* Passive buzzer
* Integrated programmable RGB LED
* GROVE I2C/HY2.0-4Pinterface
* Programming platform: Arduino/UIFlow

### Specifications

| Resources             | Parameters          |
| --------------------- | ------------------- |
| MCU                   | ESP32-PICO-D4       |
| SENSOR                | MLX90640            |
| POWER                 | 5V @ 0.5A           |
| Field of View         | 110°×75°            |
| Measurement Range     | -40°C \~ 300°C      |
| Resolution            | 32 x 24             |
| Refresh Rate          | 0.5Hz-64Hz          |
| Operating temperature | -10°C \~ 60°C       |
| Housing material      | Plastic ( PC )      |
| Product Size          | 48mm × 24mm ×8mm    |
| Package Size          | 136mm × 92mm × 13mm |
| Product Weight        | 4.9g                |
| Package Weight        | 10.7g               |

### Dimensions

<figure><img src="../../.gitbook/assets/image (477).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

* [Host code（Core）](https://github.com/m5stack/M5Unit-Thermal2-Internal-FW/blob/main/examples/FactoryTest/FactoryTest.ino)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/arduinoCase-%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20220923175447.jpg" alt=""><figcaption></figcaption></figure>

* [Thermal2 firmware](https://github.com/m5stack/M5Unit-Thermal2-Internal-FW)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [High Body Temperature Alert System](https://flow.m5stack.com/?examples=unit_thermal2_demo)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/uiflowCase-1663845747734.jpg" alt=""><figcaption></figcaption></figure>

### UIFlow Blocks <a href="#uiflow-blocks" id="uiflow-blocks"></a>

* Get button status

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-8c020bdf-3e79-48ba-9a65-eebfd2e63e7a.png" alt=""><figcaption></figcaption></figure>

* Get temperaturre alarm status

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-abdc4f37-90b4-4008-890b-ceb484b719d6.png" alt=""><figcaption></figcaption></figure>

* Get device info

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-3fbaf506-ed43-4715-93c5-3e6660c5f2ad.png" alt=""><figcaption></figcaption></figure>

* Get I2C address

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-d81a396f-d9d1-4b3a-86ef-718cc5ade374.png" alt=""><figcaption></figcaption></figure>

* Get function control

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-90e7700a-365f-4c63-9b86-c026f0e46f4e.png" alt=""><figcaption></figcaption></figure>

* Get refresh rate

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-ea6bcda2-ffa6-4db1-a775-97d202e998ed.png" alt=""><figcaption></figcaption></figure>

* Get noise filter

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-bde17481-8f1b-4d43-b543-7bd4f9b4943a.png" alt=""><figcaption></figcaption></figure>

* Get temperature monitor size

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-15bf3666-0724-4b47-a57f-11cf9b89d5e7.png" alt=""><figcaption></figcaption></figure>

* Get buzzer frequency value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-2ff28735-9c12-4db8-9b93-8f99c25dc9e5.png" alt=""><figcaption></figcaption></figure>

* Get buzzer duty cycle

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-d8988582-6a53-41a0-b2aa-a06b85ba4cde.png" alt=""><figcaption></figcaption></figure>

* Get lowest temperature or highest temperature threshold value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-dd4b3e9c-0b39-4b3a-b6a5-1213af9e6619.png" alt=""><figcaption></figcaption></figure>

* Get low temperature or high temperature buzzer frequency

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-b56d082b-eac1-41b9-af31-384cf76e26c6.png" alt=""><figcaption></figcaption></figure>

* Get low temperature or high temperature buzzer interval

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-969e485e-2323-4e6a-adc7-105830f17b96.png" alt=""><figcaption></figcaption></figure>

* Get low temperature or high temperature LED RGB colors

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-8c23faa2-739e-4866-83b2-27663b53e8d5.png" alt=""><figcaption></figcaption></figure>

* Get data refresh control

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-bd48c9ef-e22b-46b0-9417-fe61b106bf46.png" alt=""><figcaption></figcaption></figure>

* Get subpage information

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-748efb12-900c-4ee4-a397-f69d8bc0e540.png" alt=""><figcaption></figcaption></figure>

* Get ( median / average / differential / lowest / highest ) temperature value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-061504b6-0249-430a-aaa7-813a62c3a9d8.png" alt=""><figcaption></figcaption></figure>

* Get ( differential / lowest / highest ) position

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-dc770280-f42b-41be-a222-779457e00af0.png" alt=""><figcaption></figcaption></figure>

* Get temperature data buffer

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-d3122b29-4f27-43aa-a337-853bf337785c.png" alt=""><figcaption></figcaption></figure>

* Set control for buzzer, neopixel, auto-refresh

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-3c4c2bb9-2ba3-45ed-ba8f-887056967571.png" alt=""><figcaption></figcaption></figure>

* Set refresh rate

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-e66665b0-725c-43b1-918b-2af7f07f0b75.png" alt=""><figcaption></figcaption></figure>

* Set noise filter

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-1140af6d-f5f1-4c6c-ab41-9a4c5070638e.png" alt=""><figcaption></figcaption></figure>

* Set temperature monitor size

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-ed597803-056d-4e2f-809c-7dd0dfeb4d26.png" alt=""><figcaption></figcaption></figure>

* Set temperature alarm control

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-17472a62-fc19-484f-aa61-fc596a2cb03a.png" alt=""><figcaption></figcaption></figure>

* Set buzzer frequency

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-dbef2636-79ee-41e1-8dd3-42f94d51b31f.png" alt=""><figcaption></figcaption></figure>

* Set buzzer duty cycle

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-c073cc9d-e8a4-4c1e-85b0-051f5d305a1e.png" alt=""><figcaption></figcaption></figure>

* Set RGB LED colors

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-6b5f08ba-b23b-4250-ac48-56c5215d00cd.png" alt=""><figcaption></figcaption></figure>

* Set lowest temperature or highest temperature threshold value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-c2f68344-afe5-4d9b-9ef0-697bc6f2c0b0.png" alt=""><figcaption></figcaption></figure>

* Set lowest temperature or highest temperature buzzer frequency

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-a9bf568c-779a-4331-9911-5e981e8b3d21.png" alt=""><figcaption></figcaption></figure>

* Set lowest temperature or highest temperature buzzer interval

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/blockIntro-814a7933-89a3-4937-a17f-e558d19d20ab.png" alt=""><figcaption></figcaption></figure>

* Set lowest temperature or highest temperature LED color

### FAQ

<details>

<summary><strong>What development boards are compatible with the M5Stack Thermal Camera 2 Unit?</strong></summary>

The unit is compatible with M5Stack development boards and other microcontrollers that support I2C or UART interfaces.

</details>

<details>

<summary><strong>What is the maximum temperature that the Thermal Camera 2 Unit can measure?</strong></summary>

The unit can measure temperatures up to 300°C.

</details>

<details>

<summary><strong>How do I power the Thermal Camera 2 Unit?</strong></summary>

&#x20;The unit can be powered using a 3.3V or 5V power supply.

</details>

<details>

<summary><strong>Where can I find the software libraries for the Thermal Camera 2 Unit?</strong> </summary>

The software libraries can be downloaded from the M5Stack website or the official GitHub repository.

</details>

<details>

<summary><strong>Can the Thermal Camera 2 Unit provide real-time thermal imaging?</strong> </summary>

Yes, it provides real-time thermal imaging and temperature data.

</details>
