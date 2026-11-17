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

# M5Stack LLM Module

### M5Stack LLM (large language model) Module (AX630C)

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**Module LLM** is an integrated offline Large Language Model (LLM) inference module designed for terminal devices that require efficient and intelligent interaction. Whether for smart homes, voice assistants, or industrial control, Module LLM provides a smooth and natural AI experience without relying on the cloud, ensuring privacy and stability. Integrated with the **StackFlow** framework and **Arduino/UiFlow** libraries, smart features can be easily implemented with just a few lines of code.\
Powered by the advanced **AX630C** SoC processor, it integrates a 3.2 TOPs high-efficiency NPU with native support for Transformer models, handling complex AI tasks with ease. Equipped with **4GB LPDDR4** memory (1GB available for user applications, 3GB dedicated to hardware acceleration) and **32GB eMMC** storage, it supports parallel loading and sequential inference of multiple models, ensuring smooth multitasking. The main chip's runtime power consumption of approximately 1.5W, making it highly efficient and suitable for long-term operation.\
It features a built-in microphone, speaker, TF storage card, **USB OTG**, and RGB status light, meeting diverse application needs with support for voice interaction and data transfer. The module offers flexible expansion: the onboard SD card slot supports cold/hot firmware upgrades, and the **UART** communication interface simplifies connection and debugging, ensuring continuous optimization and expansion of module functionality. The USB port supports master-slave auto-switching, serving as both a debugging port and allowing connection to additional USB devices like cameras. Users can purchase the LLM debugging kit to add a 100 Mbps Ethernet port and kernel serial port, using it as an SBC.\
The module is compatible with multiple models and comes pre-installed with the **Qwen2.5-0.5B** language model. It features **KWS** (wake word), **ASR** (speech recognition), **LLM** (large language model), and **TTS** (text-to-speech) functionalities, with support for standalone calls or **pipeline** automatic transfer for convenient development. Future support includes Qwen2.5-1.5B, Llama3.2-1B, and InternVL2-1B models, allowing hot model updates to keep up with community trends and accommodate various complex AI tasks. Vision recognition capabilities include support for CLIP, YoloWorld, and future updates for DepthAnything, SegmentAnything, and other advanced models to enhance intelligent recognition and analysis.\
Plug and play with **M5 hosts**, Module LLM offers an easy-to-use AI interaction experience. Users can quickly integrate it into existing smart devices without complex settings, enabling smart functionality and improving device intelligence. This product is suitable for offline voice assistants, text-to-speech conversion, smart home control, interactive robots, and more.

### Product Features <a href="#product-features" id="product-features"></a>

* Offline inference, 3.2T@INT8 precision computing power
* Integrated KWS (wake word), ASR (speech recognition), LLM (large language model), TTS (text-to-speech generation)
* Multi-model parallel processing
* Onboard 32GB eMMC storage and 4GB LPDDR4 memory
* Onboard microphone and speaker
* Serial communication
* SD card firmware upgrade
* Supports ADB debugging
* RGB indicator light
* Built-in Ubuntu system
* Supports OTG functionality
* Compatible with Arduino/UIFlow

### Applications <a href="#applications" id="applications"></a>

* Offline voice assistants
* Text-to-speech conversion
* Smart home control
* Interactive robots

### Specifications <a href="#specifications" id="specifications"></a>

<table><thead><tr><th width="215">Specification</th><th>Parameter</th></tr></thead><tbody><tr><td>Processor SoC</td><td>AX630C@Dual Cortex A53 1.2 GHz<br>MAX.12.8 TOPS @INT4 and 3.2 TOPS @INT8</td></tr><tr><td>Memory</td><td>4GB LPDDR4 (1GB system memory + 3GB dedicated for hardware acceleration)</td></tr><tr><td>Storage</td><td>32GB eMMC5.1</td></tr><tr><td>Communication</td><td>Serial communication default baud rate 115200@8N1 (adjustable)</td></tr><tr><td>Microphone</td><td>MSM421A</td></tr><tr><td>Audio Driver</td><td>AW8737</td></tr><tr><td>Speaker</td><td>8Ω@1W, Size:2014 cavity speaker</td></tr><tr><td>Built-in Units</td><td>KWS (wake word), ASR (speech recognition), LLM (large language model), TTS (text-to-speech)</td></tr><tr><td>RGB Light</td><td>3x RGB LED@2020 driven by LP5562 (status indication)</td></tr><tr><td>Power</td><td>Idle: 5V@0.5W, Full load: 5V@1.5W</td></tr><tr><td>Button</td><td>For entering download mode for firmware upgrade</td></tr><tr><td>Upgrade Port</td><td>SD card / Type-C port</td></tr><tr><td>Working Temp</td><td>0-40°C</td></tr><tr><td>Product Size</td><td>54*54*13mm</td></tr><tr><td>Packaging Size</td><td>133*95*16mm</td></tr><tr><td>Product Weight</td><td>17.4g</td></tr><tr><td>Packaging Weight</td><td>32.0g</td></tr></tbody></table>

![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/11.webp)![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/5.webp)![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/12.webp)![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/9.webp)![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/14.webp)![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/7.webp)

### Related Links <a href="#related-links" id="related-links"></a>

* [AX630C](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/AX630C.pdf)

### PinMap <a href="#pinmap" id="pinmap"></a>

| Module LLM   | RXD | TXD  |
| ------------ | --- | ---- |
| Core (Basic) | G16 | G17  |
| Core2        | G13 | G14  |
| CoreS3       | G18 | G17  |
| CoreMP135    | PH8 | PF11 |

LLM Module Pin SwitchingLLM Module has reserved soldering pads for pin switching. In cases of pin multiplexing conflicts, the PCB trace can be cut and reconnected to other sets of pins.

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/03.jpg" alt=""><figcaption></figcaption></figure>

Taking `CoreS3` as an example, the first column (left green box) is the TX pin for serial communication, where users can choose one out of four options as needed (from top to bottom, the pins are G18, G7, G14, and G10). The default is set to IO18. To switch to a different pin, cut the connection on the solder pad (at the red line) — it’s recommended to use a blade for this — and then connect to one of the three remaining pins below. The second column (right green box) is for RX pin selection, and, as with the TX pin, it also allows a choice of one out of four options.

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Indicator Light <a href="#indicator-light" id="indicator-light"></a>

* LLM Module working status indicator:
  * Red: Device is initializing
  * Green: Device initialized successfully
* LLM Module upgrade status indicator:
  * Blue flashing: Application package updating
  * Red:Application package update failed
  * Green: Application package updated successfully

Note on Model ReplacementThe LLM Module supports models in a proprietary format requiring special processing to function properly. Therefore, existing models on the market cannot be used directly.

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [LLM Module UIFlow2.0 Quick Start](https://docs.m5stack.com/en/guide/llm/llm/uiflow2)
* [LLM Module UIFlow2.0 API](https://uiflow-micropython.readthedocs.io/en/latest/module/llm.html)

#### Arduino <a href="#arduino" id="arduino"></a>

* [LLM Module Arduino Quick Start](https://docs.m5stack.com/en/guide/llm/llm/arduino)
* [LLM Module Arduino Library](https://github.com/m5stack/M5Module-LLM)
* [LLM Module Arduino Library API](https://docs.m5stack.com/en/guide/llm/llm/arduino_api)

#### Firmware Update <a href="#firmware-update" id="firmware-update"></a>

* [LLM Module Image Update](https://docs.m5stack.com/en/guide/llm/llm/image)
* [LLM Module ADB Tools](https://docs.m5stack.com/en/guide/llm/llm/adb)
* [LLM Module Factory firmware](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/linux/llm/AX630C_emmc_arm64_k419_ubuntu_rootfs_V2.0.0_P7_20240513101106_20241021175618_20241024_glibc_4_32.axp)

#### Development Resources <a href="#development-resources" id="development-resources"></a>

* [AX630C Databrief](https://en.axera-tech.com/Product/126.html)
* [LLM Module JSON API Documentation](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/protocol/M140/LLM_Module_API_v1.0.0_EN.pdf)
* [LLM Module AX630C API Docs](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/linux/llm/M5_LLM_AXERA_DOC_RELEASE.zip)
* [LLM Module AX620E MSP/Sample](https://github.com/AXERA-TECH/ax620e_bsp_sdk.git)
* [LLM Module Linux Kernel 4.19.125-head](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/linux/llm/linux-4.19.125-head.tar.gz)
* [AXERA LLM Example](https://github.com/AXERA-TECH/ax-llm)
* [AXERA CV Example](https://github.com/AXERA-TECH/ax-samples)

### AI Benchmark Comparison <a href="#ai-benchmark-comparison" id="ai-benchmark-comparison"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/Module%20LLM/Benchmark%E5%AF%B9%E6%AF%94.png" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (420).png" alt=""><figcaption></figcaption></figure>
