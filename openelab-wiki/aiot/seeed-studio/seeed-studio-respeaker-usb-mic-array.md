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

# Seeed Studio ReSpeaker USB Mic Array

{% hint style="info" %}
[**View Seeed Studio ReSpeaker USB Mic Array on OpenELAB**](https://openelab.io/products/respeaker-usb-mic-array)

**Store SKU / option:** `Seeed-107990193`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio ReSpeaker USB Mic Array

***

### Product Link

{% embed url="https://openelab.io/products/respeaker-usb-mic-array" %}

### Introduction

The ReSpeaker USB Mic Array is an advanced, compact, and highly sensitive microphone array designed for voice and sound applications. Developed by Seeed Studio, this device is equipped with multiple microphones arranged in an array, providing superior audio capture and processing capabilities. It connects easily via USB, making it an ideal solution for various applications such as voice recognition, conference systems, smart speakers, and other voice-based projects. The ReSpeaker USB Mic Array is designed to enhance the performance of voice-related tasks with its built-in audio processing features, including beamforming, noise reduction, and echo cancellation.

### Features

* Plug & Play (No driver required), compatible with Windows 10/8/7, Mac, Linux and Android that support OTG.
* Voice Pick-up device, Far-field voice pick-up up to 5m and supports 360° pick-up pattern
* Acoustic algorithms implemented:
* DOA(Direction of Arrival),
* AEC(Automatic Echo Cancellation),
* AGC(Automatic Gain Control),
* NS(Noise Suppression)
* Built-in audio jack, which allows for plugging in headphones or speakers (speaker not included)

### Specifications

* **Microphones**: 4 high-performance digital MEMS microphones
* **Audio Processing**:
  * Beamforming
  * Noise Reduction
  * Echo Cancellation
  * Voice Activity Detection (VAD)
* **Interface**: USB 2.0 (Type-A)
* **Sample Rate**: 16 kHz / 48 kHz
* **Audio Output**: 16-bit
* **Power Supply**: Powered via USB (5V)
* **Operating Voltage**: 5V
* **Operating Temperature**: -20°C to +70°C

### Pinout

The ReSpeaker USB Mic Array connects via USB and does not require a traditional pinout for usage. However, if needed for advanced projects, the board may offer additional breakout pins for further development and customization, including access to I2S, I2C, and UART interfaces.

### Dimensions

* **Board Size**: 70 mm (diameter)
* **Thickness**: 8 mm
* **Weight**: 30 grams

### How to Use

1. **Connecting the Device**:
   * Plug the ReSpeaker USB Mic Array into a USB port on your computer or development board.
   * The device is powered through the USB connection, so no additional power supply is needed.
2. **Setting Up the Environment**:
   * For most operating systems (Windows, macOS, Linux), the ReSpeaker USB Mic Array is recognized automatically without the need for additional drivers.
   * If using with a development environment like Python, ensure that relevant libraries for audio capture and processing are installed (e.g., `pyaudio`, `sounddevice`).
3. **Programming and Usage**:
   * Utilize audio processing libraries in your chosen programming language to capture and process sound.
   * Implement voice recognition, beamforming, noise reduction, and echo cancellation features in your projects by utilizing the built-in functionalities of the mic array.
4. **Testing and Calibration**:
   * Test the microphone array by recording audio and adjusting the settings for optimal performance in your specific environment.
   * Use available software tools to calibrate the array for the best noise reduction and voice detection results.
5. **Integrating into Projects**:
   * Incorporate the ReSpeaker USB Mic Array into larger projects such as smart home systems, voice-activated assistants, or conference systems.
   * Utilize the advanced audio features to enhance the performance of your applications.

### FAQ

<details>

<summary><strong>Do I need to install drivers to use the ReSpeaker USB Mic Array?</strong></summary>

For most operating systems (Windows, macOS, Linux), the device is recognized automatically without needing additional drivers.

</details>

<details>

<summary><strong>Can the ReSpeaker USB Mic Array be used with a Raspberry Pi?</strong></summary>

Yes, it can be used with a Raspberry Pi. It connects via USB and is compatible with Linux-based systems, including Raspbian.

</details>

<details>

<summary><strong>How many microphones are included in the ReSpeaker USB Mic Array?</strong></summary>

The array includes 4 digital MEMS microphones, which work together to capture high-quality audio.

</details>

<details>

<summary><strong>What is beamforming, and how does it work in the ReSpeaker USB Mic Array?</strong></summary>

Beamforming is a signal processing technique that focuses on sound from a particular direction while suppressing noise from other directions, improving the clarity and accuracy of voice capture.

</details>

<details>

<summary><strong>Is the ReSpeaker USB Mic Array suitable for voice recognition projects?</strong></summary>

Yes, it is designed for voice recognition applications, offering features like beamforming, noise reduction, and echo cancellation to enhance voice recognition performance.

</details>

## Official documentation and development resources

Use [reSpeaker USB 4-Mic Array XVF3000 v2.0](https://wiki.seeedstudio.com/ReSpeaker_Mic_Array_v2.0/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need     | Model-specific reference                                                                                           |
| -------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Electrical schematic | [Read electrical schematic](https://files.seeedstudio.com/products/107990053/ReSpeakerMicArrayv2.0.1Schematic.zip) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
