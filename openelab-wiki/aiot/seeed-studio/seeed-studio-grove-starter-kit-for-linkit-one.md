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

# Seeed Studio Grove Starter Kit for LinkIt ONE

{% hint style="info" %}
[**View Seeed Studio Grove Starter Kit for LinkIt ONE on OpenELAB**](https://openelab.io/products/grove-starter-kit)

**Store SKU / option:** `Seeed-110060039`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio Grove Starter Kit for LinkIt ONE

***

### Product Link

{% embed url="https://openelab.io/products/grove-starter-kit" %}

### Features

* **Comprehensive Starter Kit**: Includes a wide variety of Grove modules, such as sensors, actuators, and display units, providing everything you need to start developing with the LinkIt ONE.
* **Plug-and-Play Design**: Grove modules use standardized connectors, allowing for quick and easy connections without the need for breadboards or soldering.
* **Compatibility**: Fully compatible with the LinkIt ONE development board, enabling seamless integration and operation.
* **Modular System**: The Grove system's modularity allows for easy expansion, letting you add more sensors and actuators as your project grows.
* **User-Friendly**: Designed with beginners in mind, the kit includes detailed documentation and examples to help you get started quickly.

### Specifications

* **Included Modules**:
  * Grove - Temperature & Humidity Sensor
  * Grove - Light Sensor
  * Grove - Sound Sensor
  * Grove - Button
  * Grove - Relay
  * Grove - Buzzer
  * Grove - 4-digit Display
  * Grove - Rotary Angle Sensor
  * Grove - Servo
* **Connector Type**: Grove 4-pin connectors for easy plug-and-play connections.
* **Power Supply**: Modules are powered through the LinkIt ONE board (5V/3.3V).
* **Compatibility**: Designed specifically for the LinkIt ONE development board but can also be used with other compatible Grove systems.
* **Operating Voltage**: 5V/3.3V, depending on the module.

### Pinout

The Seeed Studio Grove Starter Kit for LinkIt ONE follows the standardized Grove system pinout:

* **VCC**: Power supply pin (5V/3.3V depending on the module).
* **GND**: Ground.
* **SIG**: Signal pin, used for data transmission.
* **NC**: Not Connected (varies by module).

Each Grove module in the kit connects to the LinkIt ONE board using these standardized 4-pin connectors, which correspond to the pinout described above.

### Dimensions

* **Grove Modules**: Sizes vary depending on the module, typically ranging from 20x20 mm to 40x20 mm.
* **Packaging**: The entire kit is compactly packaged for easy storage and portability.

### How to Use

1. **Set Up the LinkIt ONE Board**:
   * Connect the LinkIt ONE board to your computer using a USB cable.
   * Install the necessary drivers and development environment (e.g., Arduino IDE with LinkIt ONE support).
2. **Connect Grove Modules**:
   * Select the desired Grove module from the kit.
   * Connect the module to the LinkIt ONE board using the appropriate Grove cable and port.
   * Each module should be plugged into the corresponding analog, digital, or I2C port on the LinkIt ONE board.
3. **Programming**:
   * Write or load a sample program that utilizes the connected Grove module.
   * Upload the code to the LinkIt ONE board and observe the module's behavior.
4. **Experiment and Prototype**:
   * Combine different modules to create more complex projects.
   * Use the provided examples and documentation to explore various functionalities and applications.
5. **Powering the Setup**:
   * The Grove modules are powered through the LinkIt ONE board, so no additional power supply is needed.

### FAQ

<details>

<summary><strong>Can I use the Grove Starter Kit with other development boards?</strong></summary>

While the kit is designed for the LinkIt ONE, Grove modules are compatible with other platforms that support the Grove system, such as Arduino or Raspberry Pi, using appropriate connectors or shields.

</details>

<details>

<summary><strong>How do I know which port to connect a module to?</strong></summary>

Each module comes with a detailed description in the documentation that specifies whether it should be connected to an analog, digital, or I2C port.

</details>

<details>

<summary><strong>Do I need to solder anything to use the Grove modules?</strong></summary>

No, the Grove system is designed for plug-and-play use, so no soldering is required.

</details>

<details>

<summary><strong>Where can I find sample codes for the Grove modules?</strong></summary>

Sample codes are available in the kit’s documentation and online through Seeed Studio’s website or the LinkIt ONE resources.

</details>

<details>

<summary><strong>What should I do if a module doesn’t work?</strong></summary>

Check the connections and ensure the correct port is used. If the issue persists, refer to the troubleshooting section in the documentation or contact Seeed Studio’s support.

</details>

## Official documentation and development resources

Use [Grove - Starter Kit for LinkIt ONE](https://wiki.seeedstudio.com/Grove-Starter_Kit_for_LinkIt_ONE/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
