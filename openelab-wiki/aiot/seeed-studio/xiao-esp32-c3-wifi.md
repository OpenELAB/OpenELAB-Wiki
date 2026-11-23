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

# XIAO ESP32-C3 WIFI

{% hint style="info" %}
[**View Seeed Studio XIAO ESP32C3 RISC-V Wi-Fi BLE 5.0 Battery Charge Supported on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-esp32c3)

**Store SKU / option:** `Seeed-113991054`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio XIAO ESP32-C3 WIFI Dev Board

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-esp32c3" %}

### Introduction

**Seeed Studio XIAO ESP32C3** is an IoT mini development board based on the Espressif **ESP32-C3** WiFi/Bluetooth dual-mode chip. ESP32-C3 is a **32-bit RISC-V CPU**, which includes an **FPU** (Floating Point Unit) for **32-bit single-precision arithmetic** with powerful computing power. It has excellent radio frequency performance, supporting **IEEE 802.11 b/g/n WiFi**, and **Bluetooth 5 (LE)** protocols. This board comes included with an external antenna to increase the signal strength for your wireless applications. It also has a **small and exquisite form-factor** combined with a **single-sided surface-mountable design**. It is equipped with rich interfaces and has **11 digital I/O** that can be used as **PWM pins** and **3 analog I/O** that can be used as **ADC pins**. It supports four serial interfaces such as **UART, I2C and SPI**. There is also a small **reset button** and a **bootloader mode button** on the board. XIAO ESP32C3 is fully compatible with the [Grove Shield for Seeeduino XIAO](https://www.seeedstudio.com/Grove-Shield-for-Seeeduino-XIAO-p-4621.html) and [Seeeduino XIAO Expansion board](https://wiki.seeedstudio.com/Seeeduino-XIAO-Expansion-Board) except for the Seeeduino XIAO Expansion board, the SWD spring contacts on the board will not be compatible.

With regard to the features highlighted above, XIAO ESP32C3 is positioned as a **high-performance, low-power, cost-effective IoT mini development board**, suitable for **low-power IoT applications and wireless wearable applications**.

### Features

* **Powerful CPU:** ESP32-C3, 32­bit RISC­-V single­core processor that operates at up to 160 MHz
* **Complete Wi­Fi subsystem:** Complies with IEEE 802.11b/g/n protocol and supports Station mode, SoftAP mode, SoftAP + Station mode, and promiscuous mode
* **Bluetooth LE subsystem:** Supports features of Bluetooth 5 and Bluetooth mesh
* **Ultra-Low Power:** Deep sleep power consumption is about 43μA
* **Better RF performance:** External RF antenna included
* **Battery charging chip:** Supports lithium battery charge and discharge management
* **Rich on-chip resources:** 400KB of SRAM, and 4MB of on-board flash memory
* **Ultra small size:** As small as a thumb(21x17.8mm) XIAO series classic form-factor for wearable devices and small projects
* **Reliable security features:** Cryptographic hardware accelerators that support AES-128/256, Hash, RSA, HMAC, digital signature and secure boot
* **Rich interfaces:** 1xI2C, 1xSPI, 2xUART, 11xGPIO(PWM), 4xADC, 1xJTAG bonding pad interface
* Single-sided components, surface mounting design

### Specifications

<table><thead><tr><th>Item</th><th>Seeed Studio XIAO ESP32C3</th><th>Seeeduino XIAO</th><th width="159">Seeed XIAO RP2040</th><th>Seeed XIAO nRF52840</th><th>Seeed XIAO nRF52840 Sense</th></tr></thead><tbody><tr><td>Processor</td><td>ESP32-C3 32-bit RISC-V @160MHz</td><td>SAMD21 M0+@48MHz</td><td>RP2040 Dual-core M0+@133Mhz</td><td>nRF52840 M4F@64MHz</td><td>nRF52840 M4F@64MHz</td></tr><tr><td>Wireless Connectivity</td><td>WiFi and Bluetooth 5 (LE)</td><td>N/A</td><td>N/A</td><td>Bluetooth 5.0/BLE/NFC</td><td>Bluetooth 5.0/BLE/NFC</td></tr><tr><td>Memory</td><td>400KB SRAM, 4MB onboard Flash</td><td>32KB SRAM 256KB FLASH</td><td>264KB SRAM 2MB onboard Flash</td><td>256KB RAM, 1MB Flash 2MB onboard Flash</td><td>256KB RAM,1MB Flash 2MB onboard Flash</td></tr><tr><td>Built-in Sensors</td><td>N/A</td><td>N/A</td><td>N/A</td><td>N/A</td><td>6 DOF IMU (LSM6DS3TR-C), PDM Microphone</td></tr><tr><td>Interfaces</td><td>I2C/UART/SPI</td><td>I2C/UART/SPI</td><td>I2C/UART/SPI</td><td>I2C/UART/SPI</td><td>I2C/UART/SPI</td></tr><tr><td>PWM/Analog Pins</td><td>11/4</td><td>11/11</td><td>11/4</td><td>11/6</td><td>11/6</td></tr><tr><td>Onboard Buttons</td><td>Reset/ Boot Button</td><td>N/A</td><td>Reset/ Boot Button</td><td>Reset Button</td><td>Reset Button</td></tr><tr><td>Onboard LEDs</td><td>Charge LED</td><td>N/A</td><td>Full-color RGB/ 3-in-one LED</td><td>3-in-one LED/ Charge LED</td><td>3-in-one LED/ Charge LED</td></tr><tr><td>Battery Charge Chip</td><td>Built-in</td><td>N/A</td><td>N/A</td><td>BQ25101</td><td>BQ25101</td></tr><tr><td>Programming Languages</td><td>Arduino/ MicroPython</td><td>Arduino/ CircuitPython</td><td>Arduino/ MicroPython/ CircuitPython</td><td></td><td></td></tr></tbody></table>

### Pinout

<figure><img src="../../.gitbook/assets/image (931).png" alt=""><figcaption></figcaption></figure>

### Getting started[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#getting-started) <a href="#getting-started" id="getting-started"></a>

First, we are going to connect XIAO ESP32C3 to the computer, connect an LED to the board and upload a simple code from Arduino IDE to check whether the board is functioning well by blinking the connected LED.

#### Software setup[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#software-setup) <a href="#software-setup" id="software-setup"></a>

* **Step 1.** Download and Install the latest version of Arduino IDE according to your operating system

[![](https://files.seeedstudio.com/wiki/Seeeduino_Stalker_V3_1/images/Download_IDE.png)](https://www.arduino.cc/en/software)

* **Step 2.** Launch the Arduino application
* **Step 3.** Add ESP32 board package to your Arduino IDE

Navigate to **File > Preferences**, and fill **"Additional Boards Manager URLs"** with the url below: [_https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package\_esp32\_index.json_](https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json)

![](https://files.seeedstudio.com/wiki/XIAO_WiFi/add_board.png)

Navigate to **Tools > Board > Boards Manager...**, type the keyword "**esp32**" in the search box, select the latest version of **esp32**, and install it.

![](https://files.seeedstudio.com/wiki/XIAO_WiFi/add_esp32c3.png)

* **Step 4.** Select your board and port

**Board**

Navigate to **Tools > Board > ESP32 Arduino** and select "**XIAO\_ESP32C3**". The list of board is a little long and you need to roll to the buttom to reach it.

![](https://files.seeedstudio.com/wiki/Seeed-Studio-XIAO-ESP32/XIAO_ESP32_board.png)

**Port**

Navigate to **Tools > Port** and select the serial port name of the connected XIAO ESP32C3. This is likely to be COM3 or higher (**COM1** and **COM2** are usually reserved for hardware serial ports).

#### Hardware setup[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#hardware-setup) <a href="#hardware-setup" id="hardware-setup"></a>

You need to prepare the following:

* 1 x [Seeed Studio XIAO ESP32C3](https://www.seeedstudio.com/seeed-xiao-esp32c3-p-5431.html)
* 1 x Computer
* 1 x USB Type-C cable

tip

Some USB cables can only supply power and cannot transfer data. If you don't have a USB cable or don't know if your USB cable can transmit data, you can check [Seeed USB Type-C support USB 3.1](https://www.seeedstudio.com/USB-3-1-Type-C-to-A-Cable-1-Meter-3-1A-p-4085.html).

* **Step 1.** Connect XIAO ESP32C3 to your computer via a USB Type-C cable.

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/cable-connect.png" alt="" width="188">

* **Step 2.** Connect an LED to D10 pin as follows

![](https://files.seeedstudio.com/wiki/XIAO_WiFi/connect-led-2.png)

**Note:** Make sure to connect a resistor (about 150Ω) in series to limit the current through the LED and to prevent excess current that can burn out the LED

#### Blink the LED[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#blink-the-led) <a href="#blink-the-led" id="blink-the-led"></a>

* **Step 1.** Copy the below code to Arduino IDE

Make sure your `D10` is connected to an LED as shown in the diagram above.

```

// define led according to pin diagram in article
const int led = D10; // there is no LED_BUILTIN available for the XIAO ESP32C3.

void setup() {
  // initialize digital pin led as an output
  pinMode(led, OUTPUT);
}

void loop() {
  digitalWrite(led, HIGH);   // turn the LED on 
  delay(1000);               // wait for a second
  digitalWrite(led, LOW);    // turn the LED off
  delay(1000);               // wait for a second
}
```

* **Step 2.** Click the **Upload** button to upload the code to the board

![](https://files.seeedstudio.com/wiki/Seeeduino_GPRS/img/upload_image.png)

Once uploaded, you will see the connected LED blinking with a 1-second delay between each blink. This means the connection is successful and now you can explore more projects with XIAO ESP32C3!

### Battery Usage[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#battery-usage) <a href="#battery-usage" id="battery-usage"></a>

The XIAO ESP32C3 is capable of using a 3.7V lithium battery as the power supply input. You can refer to the following diagram for the wiring method.

<div align="center"><img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/battery_connect.png" alt="pir" width="600"></div>

**Instructions on the use of batteries:**

1. Please use qualified batteries that meet the specifications.
2. XIAO can be connected to your computer device via data cable while using the battery, rest assured that XIAO has a built-in circuit protection chip, which is safe.
3. The XIAO ESP32C3 will not have any LED on when it is battery powered (unless you have written a specific program), please do not judge whether the XIAO ESP32C3 is working or not by the condition of the LED, please judge it reasonably by your program.
4. Sorry, we currently have no way to help you check the remaining battery level through software (because there are no more chip pins available), you need to charge the battery regularly or use a multimeter to check the battery level.

#### Check the battery voltage[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#check-the-battery-voltage) <a href="#check-the-battery-voltage" id="check-the-battery-voltage"></a>

Due to the limitation of the number of pins in the ESP32C3, engineers had no extra pins to allocate to the battery for voltage measurement in order to ensure that the XIAO ESP32C3 has the same number of GPIOs as the other XIAO series available.

But if you prefer to use a separate pin for battery voltage measurement, you can refer to the genius operation of [msfujino](https://forum.seeedstudio.com/u/msfujino). We would also like to give a special thanks to [msfujino](https://forum.seeedstudio.com/u/msfujino) for all the experience and efforts shared for the XIAO ESP32C3.

The basic operating idea is: The battery voltage was divided by 1/2 with 200k and connected to the A0 port so that the voltage could be monitored.

<div align="center"><img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/3.png" alt="pir" width="300"></div>

The datasheet says nominally 2500mV full scale AD conversion, but there is a large variation from chip to chip, actually ±10%. My chip was 2700mV full scale.

Fortunately, the calibrated correction value for each chip is written in the fuse area, and by using the function `analogReadMilliVolts()`, I can read the corrected voltage value without doing anything special.

The result of AD conversion and the voltage measured by the multimeter agree well with each other with an error of about 5 mV, which is not a problem in practical use.

In addition, during communication in particular, spike-like errors occurred, which had to be averaged out 16 times to remove them.

The following is the procedure to test the battery voltage.

```
void setup() {
  Serial.begin(115200);
  pinMode(A0, INPUT);         // ADC
}

void loop() {
  uint32_t Vbatt = 0;
  for(int i = 0; i < 16; i++) {
    Vbatt = Vbatt + analogReadMilliVolts(A0); // ADC with correction   
  }
  float Vbattf = 2 * Vbatt / 16 / 1000.0;     // attenuation ratio 1/2, mV --> V
  Serial.println(Vbattf, 3);
  delay(1000);
}
```

### Deep sleep mode and wake-up[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#deep-sleep-mode-and-wake-up) <a href="#deep-sleep-mode-and-wake-up" id="deep-sleep-mode-and-wake-up"></a>

The XIAO ESP32C3 is designed to support deep sleep mode and wake-up functions. For the use of these two functions, we provide the following usage examples.

```
#define BUTTON_PIN_BITMASK 0x200000000 // 2^33 in hex

RTC_DATA_ATTR int bootCount = 0;

/*
Method to print the reason by which ESP32
has been awaken from sleep
*/
void print_wakeup_reason(){
  esp_sleep_wakeup_cause_t wakeup_reason;

  wakeup_reason = esp_sleep_get_wakeup_cause();

  switch(wakeup_reason)
  {
    case ESP_SLEEP_WAKEUP_EXT0 : Serial.println("Wakeup caused by external signal using RTC_IO"); break;
    case ESP_SLEEP_WAKEUP_EXT1 : Serial.println("Wakeup caused by external signal using RTC_CNTL"); break;
    case ESP_SLEEP_WAKEUP_TIMER : Serial.println("Wakeup caused by timer"); break;
    case ESP_SLEEP_WAKEUP_TOUCHPAD : Serial.println("Wakeup caused by touchpad"); break;
    case ESP_SLEEP_WAKEUP_ULP : Serial.println("Wakeup caused by ULP program"); break;
    default : Serial.printf("Wakeup was not caused by deep sleep: %d\n",wakeup_reason); break;
  }
}

void setup(){
  Serial.begin(115200);
  delay(1000); //Take some time to open up the Serial Monitor

  //Increment boot number and print it every reboot
  ++bootCount;
  Serial.println("Boot number: " + String(bootCount));

  //Print the wakeup reason for ESP32
  print_wakeup_reason();

  esp_deep_sleep_enable_gpio_wakeup(BIT(D1), ESP_GPIO_WAKEUP_GPIO_LOW);

  //Go to sleep now
  Serial.println("Going to sleep now");
  esp_deep_sleep_start();
  Serial.println("This will never be printed");
}

void loop(){
  //This is not going to be called
}
```

If you are quick enough to turn on the serial monitor before the XIAO goes into deep sleep, then you can see the message output as shown below. This means that the XIAO is now "asleep".

![](https://files.seeedstudio.com/wiki/XIAO_WiFi/15.png)

### FAQ[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#faq) <a href="#faq" id="faq"></a>

<details>

<summary>My Arduino IDE is stuck when uploading code to the board</summary>

You can first try to reset the board by clicking the **RESET BUTTON** once while the board is connected to your PC. If that does not work, hold the **BOOT BUTTON**, connect the board to your PC while holding the **BOOT** button, and then release it to enter **bootloader mode**.

</details>

<details>

<summary>My board is not showing up as a serial device on Arduino IDE​</summary>

Follow the same answer as for **Q1** above.

</details>

<details>

<summary>I want to reflash the bootloader with factory firmware​</summary>

You can simply connect the board to a PC via **USB Type-C** and reflash the bootloader with factory firmware by using **ESP RF Test Tool**.

* **Step 1.** Hold on the **BOOT BUTTON** and connect XIAO ESP32C3 to the PC to enter **bootloader mode**
* **Step 2.** After it is connected, release the BOOT BUTTON
* **Step 3.** Visit [this page](https://www.espressif.com/en/support/download/other-tools) and download **ESP RF Test Tool and Test Guide**

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-tool-download.png" alt="" data-size="original">

* **Step 4.** Extract the **.zip**, navigate to `ESP_RF_Test_EN\ESP_RF_Test_EN\EspRFTestTool_v2.8_Manual` and open **EspRFTestTool\_v2.8\_Manual.exe**

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-tool-open.png" alt="" data-size="original">

* **Step 5.** Select **ESP32C3** as the ChipType, your COM port, **115200** as the BaudRate and click **open**

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-2.png" alt="" data-size="original">

You will see the following output

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-5.png" alt="" data-size="original">

* **Step 6.** Select **Flash** and click **Select Bin**

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-6.jpg" alt="" data-size="original">

* **Step 7.** Download the [factory firmware of XIAO ESP32C3](https://files.seeedstudio.com/wiki/XIAO_WiFi/Resources/ESP32-C3_RFTest_108_2b9b157_20211014.bin) and select it.
* **Step 8.** Finally click **Load Bin**

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-8.png" alt="" data-size="original">

You will see the following output when flashing is successful

<img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/esp-flash-9.png" alt="" data-size="original">

</details>

## Official documentation and development resources

Use [Getting Started with Seeed Studio XIAO ESP32C3](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
