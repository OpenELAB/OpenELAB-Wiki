---
description: >-
  Hardware, SDK setup, an offline Arduino quick-start, firmware recovery,
  troubleshooting and technical resources for StackChan K151.
---

# M5Stack StackChan K151 Development Guide

**Build a programmable desktop character with an ESP32-S3 controller, touch display, camera, audio, RGB lighting and two motorized axes.** This guide covers the **M5Stack StackChan K151**. It starts with an offline LED test, then points to motion, sensing and connected applications.

![M5Stack StackChan K151 desktop robot](../../.gitbook/assets/stackchan-k151-product.webp)

_Product photograph: M5Stack._ [_Original image_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/K151_stack_chan_main_pictures_01.webp)_._

[Buy StackChan at OpenELAB](https://openelab.io/products/m5stack-stackchan-open-source-ai-desktop-robot) · [M5Stack wiki hub](./) · [Manufacturer documentation](https://docs.m5stack.com/en/StackChan)

### Product overview and applications

StackChan combines a CoreS3 main controller with a robot body containing feedback servos, a battery, lighting and additional interfaces. Developers can combine facial animation, touch input, sound and physical movement in one device. The official Arduino board support package exposes the body peripherals alongside M5Unified's controller functions.

Useful development directions include a touch-operated desk assistant, an expressive notification terminal, an interactive classroom robot and a prototype interface for a connected service. These are project ideas; each requires its own application code and integration work.

The factory application offers a separate connected experience. An ESP32-S3 controller and microphone do not by themselves provide an offline large language model. Check the selected firmware's network, account and backend requirements before planning a voice assistant deployment. A self-contained Arduino application, including the LED example below, can run without an AI service.

**Model scope:** K151 is the robot. K151-R is a different package with remote-control accessories. Check the purchased package before following accessory-specific instructions. A generic CoreS3 replacement should not be assumed to have the original StackChan controller's factory provisioning.

Sources: [official BSP overview](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/README.md), [factory firmware project](https://github.com/m5stack/StackChan), [manufacturer model notes](https://docs.m5stack.com/en/StackChan).

### Key specifications

| Item              | Specification                                                                       |
| ----------------- | ----------------------------------------------------------------------------------- |
| Main controller   | CoreS3 with ESP32-S3, dual-core processor up to 240 MHz                             |
| Memory            | 16 MB flash; 8 MB PSRAM                                                             |
| Wireless          | 2.4 GHz Wi-Fi and Bluetooth Low Energy                                              |
| Display           | 2.0-inch, 320 × 240 capacitive touch display                                        |
| Camera            | GC0308, VGA 640 × 480                                                               |
| Audio             | Two microphones and a 1 W speaker                                                   |
| Main-unit sensors | Nine-axis inertial sensing; proximity and ambient-light sensing                     |
| Movement          | Two feedback servos; continuous horizontal rotation and nominal 90° vertical travel |
| Body interaction  | 12 RGB LEDs, three-zone top touch input, infrared transmitter/receiver and NFC      |
| Battery           | 550 mAh built-in battery                                                            |
| Connections       | Two USB-C interfaces for power/data; Grove expansion ports                          |
| Envelope and mass | 54 × 70.5 × 61.5 mm; 187.2 g                                                        |

Sources: [BSP overview](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/README.md), [CoreS3 specifications](https://docs.m5stack.com/en/core/CoreS3), [mechanical dimensions](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/Model_Size.pdf). Dimensions are the manufacturer's nominal product dimensions; use the drawing/CAD for enclosure design. Battery capacity is not a runtime guarantee.

### Hardware orientation and expansion

Use the **USB-C connector on the robot base** for the first programming session. Route the cable so it cannot catch when the head moves. Place the robot on a clear, stable surface; the factory application can move the head during startup. Keep fingers and cables clear of the moving joints.

The bottom RST button also enters download mode. Its location and the green indicator are shown in the manufacturer's animation:

![Manufacturer demonstration of StackChan download mode](../../.gitbook/assets/stackchan-download-mode.gif)

_Animation: M5Stack._ [_Original download-mode demonstration_](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/stackchan-download-mode-demo.gif)_._

For external modules, match the signal pins as well as the connector shape:

| Grove port | Black | Red | Yellow signal | White signal |
| ---------- | ----- | --- | ------------- | ------------ |
| A          | GND   | 5 V | G2            | G1           |
| B          | GND   | 5 V | G9            | G8           |
| C          | GND   | 5 V | G17           | G18          |

The red wire's supply voltage does not establish the allowable voltage on a GPIO signal. Check the controller and attached module's electrical requirements before connecting an external circuit. Internal peripherals already occupy other pins; use the manufacturer's pin map and schematics when extending the hardware.

Source: [StackChan interfaces and pin map](https://docs.m5stack.com/en/StackChan).

### Choose a software path

| Path                  | Use it for                                                         | Start here                                                                                                                                                                        |
| --------------------- | ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino C++           | Custom behavior and direct peripheral control                      | This guide and the [official Arduino setup](https://docs.m5stack.com/en/arduino/stackchan/program)                                                                                |
| UiFlow2 / MicroPython | Block-based exploration or Python scripting                        | [UiFlow2 setup](https://docs.m5stack.com/en/uiflow2/stackchan/program) and [StackChan Python API](https://uiflow-micropython.readthedocs.io/en/latest/controllers/stackchan.html) |
| Factory application   | Manufacturer demos, supported app functions and connected services | [Factory usage guide](https://docs.m5stack.com/en/StackChan) and [firmware download](https://burner.m5stack.com/device/stackchan)                                                 |

Uploading an Arduino sketch replaces the application currently running on the controller. Record the current firmware/package first if you plan to return to it. Configuration and account requirements depend on the application; consult that application's restoration instructions.

### Getting started: an offline RGB test

**Goal:** compile and upload a small C++ application, initialize the robot body and cycle its LEDs. This provides a first checkpoint before adding networking, audio or movement.

#### 1. Prepare the hardware and tools

You need a K151 robot, a computer, a USB-C **data** cable and Arduino IDE 2.x. No cloud account or Wi-Fi connection is required by this sketch. Charge/power the device before testing.

In Arduino IDE, add the following URL to **Preferences → Additional Boards Manager URLs**:

```
https://static-cdn.m5stack.com/resource/arduino/package_m5stack_index.json
```

In Boards Manager, install the **M5Stack** board package. The manufacturer's StackChan RGB guide specifies **3.2.2 or later**. Select **M5Stack → M5CoreS3** and the port belonging to the connected robot. Begin with that board preset's defaults; if uploading fails, follow the download-mode procedure below before changing unrelated options.

Sources: [official board-package installation](https://docs.m5stack.com/en/arduino/arduino_board), [StackChan board selection](https://docs.m5stack.com/en/arduino/stackchan/program), [RGB example requirements](https://docs.m5stack.com/en/arduino/stackchan/rgb).

#### 2. Install the board support library

Install **M5StackChan** through Library Manager and accept its dependencies: **M5Unified**, **IRremoteESP8266** and **M5Unit-NFC**. This draft's API checks use M5StackChan **1.1.1**, as declared in the source snapshot below. Record the actual versions installed when reproducing the example.

If that version is unavailable in Library Manager, the [pinned BSP source ZIP](https://github.com/m5stack/StackChan-BSP/archive/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0.zip) can be installed through **Sketch → Include Library → Add .ZIP Library**. Install the dependencies separately if prompted. Keep one installation of each library to avoid selecting an older duplicate.

Sources: [library metadata and dependencies](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/library.properties), [BSP public API](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/src/M5StackChan.h).

#### 3. Upload the example

Create a new sketch and paste the following code. It sends no movement commands and disables servo power immediately after initialization. **Initialization itself enables servo power temporarily**, so keep the mechanism unobstructed even for this LED test.

```cpp
#include <Arduino.h>
#include <M5StackChan.h>

// OpenELAB example using M5Stack's MIT-licensed StackChan BSP.
// API reference: M5StackChan 1.1.1, commit e2f3b02.

const uint8_t COLORS[3][3] = {
    {24, 0, 0},  // red
    {0, 24, 0},  // green
    {0, 0, 24}   // blue
};

void setup() {
    M5StackChan.begin();
    M5StackChan.setServoPowerEnabled(false);
    M5StackChan.showRgbColor(0, 0, 0);
}

void loop() {
    M5StackChan.update();

    static uint32_t previous = 0;
    static uint8_t color = 0;
    const uint32_t now = millis();

    if (now - previous >= 1000) {
        previous = now;
        M5StackChan.showRgbColor(
            COLORS[color][0], COLORS[color][1], COLORS[color][2]);
        color = (color + 1) % 3;
    }
    delay(5);
}
```

Click **Verify**, then **Upload**. If the device does not enter the bootloader automatically, use the recovery procedure in the next section and select the port again. After upload, reset/power-cycle the robot if the IDE leaves it in download mode.

#### 4. Check the result

The expected result is that all 12 body LEDs change together, cycling red → green → blue approximately once per second. This sketch does not draw a face, play sound or connect to Wi-Fi; a blank display is compatible with this particular test.

A successful test checks the application upload path and RGB control. It does not validate the camera, microphones, NFC, battery runtime or servo mechanics. Add those subsystems individually using the official examples so a failure has a clear starting point.

The source calls and initialization behavior were checked against [M5StackChan.h](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/src/M5StackChan.h) and [M5StackChan.cpp](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/src/M5StackChan.cpp). This example still requires compilation and physical-device validation before it can be described as tested.

### Firmware recovery and return to factory software

If no upload port appears, first try a known data cable and a direct computer USB connection. To enter download mode, connect through the base USB-C port and hold the bottom **RST** button until the green indicator appears. Release the button, recheck the port list and retry the upload. The manufacturer's animation above shows the physical operation.

To restore the manufacturer's application, open **M5Burner**, select the official **StackChan-UserDemo** entry for K151/K151-R, and follow its current flashing instructions. After a successful flash, restart the robot and complete the setup for that firmware. Avoid an indiscriminate full flash erase: retain configuration/calibration information unless the manufacturer specifically instructs you to erase it.

References: [download-mode instructions](https://docs.m5stack.com/en/arduino/stackchan/program), [official StackChan firmware entry](https://burner.m5stack.com/device/stackchan). M5Stack notes that its [public factory-project repository](https://github.com/m5stack/StackChan) may lag released firmware, so distinguish repository builds from the application distributed through M5Burner.

### Developing movement and other peripherals

For motion, read the [official servo guide](https://docs.m5stack.com/en/arduino/stackchan/servo) before enabling servo power. Its API uses **0.1° units**: a command value of 450 represents 45°. M5Stack recommends keeping vertical movement within **5–85°**; convert this to **50–850** when using that API. Mechanical travel limits are different from safe starting positions.

Begin with a small movement near the current position, a clear workspace and conservative speed. Do not copy an endpoint-sweeping example into an assembled or modified mechanism without checking its limits. Never force a powered joint by hand. Re-homing/calibration changes the coordinate reference; follow the official calibration procedure only when needed.

For the next development steps, use the BSP's [examples directory](https://github.com/m5stack/StackChan-BSP/tree/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/examples) for body peripherals and [M5Unified](https://github.com/m5stack/M5Unified) for controller functions. Keep one small, reproducible test per subsystem before combining movement, sound and networking into a larger application.

### Troubleshooting and FAQs

| Symptom or question                                        | Check and next action                                                                                                                                                                                                                                                        |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| No USB port appears                                        | Check power, use a data cable, connect directly to the computer, then enter download mode. Re-select the port after the bootloader enumerates.                                                                                                                               |
| `M5StackChan.h` is missing                                 | Install M5StackChan and its declared dependencies. Check for duplicate/old library folders and confirm the M5CoreS3 board selection.                                                                                                                                         |
| Upload succeeds but there is no face                       | The RGB test does not render a display interface. Check the LED sequence first; use the manufacturer's application for its animated interface.                                                                                                                               |
| LEDs remain off                                            | Confirm the new sketch starts after reset. Recheck the correct BSP/version and the body connection with power off. The BSP logs `IO expander init timeout` if body I/O initialization does not complete; inspect the initialization path before adding application features. |
| Servos do not move with this sketch                        | Servo power is intentionally disabled. Use the servo tutorial as a separate test and respect the vertical limits.                                                                                                                                                            |
| Factory app cannot join Wi-Fi                              | Use a 2.4 GHz network and check the app's Bluetooth/local-network permissions. Follow the factory pairing flow; the Arduino test does not implement pairing.                                                                                                                 |
| Is the factory AI experience available offline?            | Check the particular firmware's service requirements. The offline RGB example demonstrates local hardware control, not offline conversational AI.                                                                                                                            |
| Can another CoreS3 simply replace the supplied controller? | Physical compatibility does not establish factory-app provisioning compatibility. Check M5Stack's controller-replacement guidance first.                                                                                                                                     |
| What information helps reproduce a failure?                | Record K151/K151-R, board package and library versions, firmware name, USB port used, the smallest failing sketch, and actual compiler/serial output. Never include Wi-Fi passwords or service credentials.                                                                  |

References: [BSP initialization source](https://github.com/m5stack/StackChan-BSP/blob/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0/src/M5StackChan.cpp), [factory setup and FAQ](https://docs.m5stack.com/en/StackChan), [Arduino setup](https://docs.m5stack.com/en/arduino/stackchan/program).

### Drawings, software and technical resources

| Resource                                                                                                               | Engineering use                                                               |
| ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| [StackChan documentation](https://docs.m5stack.com/en/StackChan)                                                       | Product identity, interfaces, setup notes and manufacturer FAQ                |
| [CoreS3 reference](https://docs.m5stack.com/en/core/CoreS3)                                                            | Main-controller hardware, onboard devices and electrical references           |
| [CoreS3 schematic, PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/490/Sch_M5_CoreS3_v1.0.pdf)                   | Controller circuit reference; verify the revision against the actual hardware |
| [Adapter schematic, PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/SCH_Adapter.pdf)                        | Adapter circuitry                                                             |
| [Power schematic, PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/SCH_Power.pdf)                            | Body power circuitry                                                          |
| [Ring schematic, PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/SCH_Ring.pdf)                              | RGB/peripheral ring circuitry                                                 |
| [Touch schematic, PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/SCH_Touch.pdf)                            | Top touch-board circuitry                                                     |
| [Dimension drawing, PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1205/Model_Size.pdf)                         | Mechanical dimensions                                                         |
| [Official structural/CAD files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K151_StackChan/Structures) | Mechanical integration and enclosure work                                     |
| [Arduino BSP, pinned source](https://github.com/m5stack/StackChan-BSP/tree/e2f3b02dbe7f28e26a02adc72bef3aa2c545e4a0)   | Reproduce the API snapshot used for this draft                                |
| [Latest Arduino BSP](https://github.com/m5stack/StackChan-BSP)                                                         | Releases, issue tracking and current examples; upstream is MIT licensed       |
| [UiFlow2 StackChan API](https://uiflow-micropython.readthedocs.io/en/latest/controllers/stackchan.html)                | MicroPython peripheral programming                                            |
| [Factory application source](https://github.com/m5stack/StackChan)                                                     | Advanced application investigation; observe upstream release caveats          |
| [Official factory firmware](https://burner.m5stack.com/device/stackchan)                                               | Return to the manufacturer-distributed application                            |

**Documentation review:** 17 November 2026. **Validation status:** manufacturer documentation, drawings and SDK source reviewed; the example has not yet been compiled or run on physical hardware. This draft is ready for editorial review, with bench validation still pending.
