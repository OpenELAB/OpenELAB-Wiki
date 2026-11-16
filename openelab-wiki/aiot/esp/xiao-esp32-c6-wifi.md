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

# XIAO ESP32-C6 WIFI

### Seeed Studio XIAO ESP32-C6 WIFI Dev Board

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-esp32c6" %}

### Introduction[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#introduction) <a href="#introduction" id="introduction"></a>

Seeed Studio XIAO ESP32C6 is powered by the highly-integrated [ESP32-C6 SoC](https://www.espressif.com/en/products/socs/esp32-c6), built on **two 32-bit RISC-V processors**, with a high-performance (HP) processor with **running up to 160 MHz**, and a low-power (LP) 32-bit RISC-V processor, which can be clocked up to 20 MHz. There are **512KB SRAM and 4 MB Flash on the chip**, allowing for more programming space, and binging more possibilities to the IoT control scenarios.

XIAO ESP32C6 is **Matter native thanks to its enhanced wireless connectivity**. The wireless stack supports **2.4 GHz WiFi 6, Bluetooth® 5.3, Zigbee, and Thread (802.15.4)**. As the first XIAO member compatible with Thread, it's a perfect fit for building Matter-compliant projects, thus achieving interoperability in smart-home.

### Features[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#features) <a href="#features" id="features"></a>

* **Enhanced Connectivity**: Integrates _**2.4**_ GHz Wi-Fi 6 (802.11ax), Bluetooth 5(LE), and IEEE 802.15.4 radio connectivity, allowing for the application of **Thread** and **Zigbee** protocols.
* **Matter Native**: Supports the building of Matter-compliant smart home projects, ensuring interoperability among different smart devices.
* **Security Encrypted on Chip**: Utilizes the ESP32-C6 to provide secure boot, encryption, and Trusted Execution Environment (TEE) features, enhancing the security of smart home projects.
* **Outstanding RF Performance**: Features an on-board antenna with up to _80m_ BLE/Wi-Fi range and offers an interface for connecting an external UFL antenna, ensuring reliable connectivity.
* **Leveraging Power Consumption**: Offers four working modes, including a deep sleep mode with consumption as low as _15_ μA, along with support for lithium battery charge management.
* **Dual RISC-V Processors**: Incorporates two 32-bit RISC-V processors, with the high-performance processor capable of running up to 160 MHz and the low-power processor up to _20 MHz_.
* **Classic XIAO Designs**: Maintains the thumb-size form factor of 21 x 17.8mm and single-sided mount design, ideal for space-limited projects like wearable devices.

### Specifications[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#specifications-comparison) <a href="#specifications-comparison" id="specifications-comparison"></a>

<figure><img src="../../.gitbook/assets/image (419).png" alt=""><figcaption></figcaption></figure>

### Hardware overview <a href="#hardware-overview" id="hardware-overview"></a>

<figure><img src="../../.gitbook/assets/image (418).png" alt=""><figcaption></figcaption></figure>

### Getting started[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#getting-started) <a href="#getting-started" id="getting-started"></a>

To enable you to get started with the XIAO ESP32C6 faster, please read the hardware and software preparation below to prepare the XIAO.

#### Hardware Preparation[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#hardware-preparation) <a href="#hardware-preparation" id="hardware-preparation"></a>

You need to prepare the following:

* 1 x [Seeed Studio XIAO ESP32C6](https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html)
* 1 x Computer
* 1 x USB Type-C cable

tip

Some USB cables can only supply power and cannot transfer data. If you don't have a USB cable or don't know if your USB cable can transmit data, you can check [Seeed USB Type-C support USB 3.1](https://www.seeedstudio.com/USB-3-1-Type-C-to-A-Cable-1-Meter-3-1A-p-4085.html).

**Solder header**[**​**](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#solder-header)

XIAO ESP32C6 is shipped without pin headers by default, you need to prepare your own pin headers and solder it to the corresponding pins of XIAO so that you can connect to the expansion board or sensor.

Due to the miniature size of XIAO ESP32C6, please be careful when soldering headers, do not stick different pins together, and do not stick solder to the shield or other components. Otherwise, it may cause XIAO to short circuit or not work properly, and the consequences caused by this will be borne by the user.

#### BootLoader Mode[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#bootloader-mode) <a href="#bootloader-mode" id="bootloader-mode"></a>

There are times when we use the wrong program to make XIAO appear to lose ports or not work properly. The specific performance is:

* Connected to computer, but no port number found for XIAO.
* The computer is connected and the port number appears, but the upload program fails.

When you encounter the above two situations, you can try to put XIAO into BootLoader mode, which can solve most of the problems of unrecognized devices and failed uploads. The specific method is:

* **Step 1**. Press and hold the BOOT button on the XIAO ESP32C6 without releasing it.
* **Step 2**. Keep the BOOT button pressed and then connect to the computer via the data cable. Release the BOOT button after connecting to the computer.
* **Step 3**. Upload the **Blink** program to check the operation of the XIAO ESP32C6.

#### Reset[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#reset) <a href="#reset" id="reset"></a>

When the program runs abnormally, you can press Reset once during power-up to let XIAO re-execute the uploaded program.

When you press and hold the BOOT key while powering up and then press the Reset key once, you can also enter BootLoader mode.

#### Software Preparation[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#software-preparation) <a href="#software-preparation" id="software-preparation"></a>

The recommended programming tool for the XIAO ESP32C6 is the Arduino IDE, so you need to complete the Arduino installation as part of the software preparation.

*   **Step 1.** Download and Install the stable version of Arduino IDE according to your operating system.

    [**Download Arduino IDE**](https://www.arduino.cc/en/software)
* **Step 2.** Launch the Arduino application.
* [**Step 3**](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#add-board)**.** Add the XIAO ESP32C6 on-board package to the Arduino IDE and click `OK`.
* **Step 4.** Close the Arduino IDE and reopen it.

**Add the XIAO-C6 Board**[**​**](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#add-board)

To install the XIAO ESP32C6 board, follow these steps:

```
https://espressif.github.io/arduino-esp32/package_esp32_index.json
```

1. Add the above board manager URL to the preferences of your Arduino IDE, which is taken from the [Installing - Arduino ESP32](https://docs.espressif.com/projects/arduino-esp32/en/latest/installing.html#installing-using-arduino-ide).

![](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32C6/img/boards_url.png)

2. Download the XIAO ESP32C6 board package.

![](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32C6/img/install_board.png)

3. Opt for `XIAO_ESP32C6` variant.

![](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32C6/img/select_xiao_c6.png)

Now enjoy coding ✨.

### Run your first Blink program[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#run-your-first-blink-program) <a href="#run-your-first-blink-program" id="run-your-first-blink-program"></a>

* **Step 1.** Launch the Arduino application.
* **Step 2.** Navigate to **File > Examples > 01.Basics > Blink**, open the program.

![](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/img/11.png)

* **Step 3.** Select the board model to **XIAO ESP32C6**, and select the correct port number to upload the program.

![](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32C6/img/upload_program.png)

Once the program is successfully uploaded, you will see the following output message and you can observe that the orange LED on the right side of the XIAO ESP32C6 is blinking.

| <img src="https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32C6/img/XIAOC6_flash_firmware.png" alt="" data-size="original"> | <img src="https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32C6/img/XIAOC6-blink.gif" alt="" data-size="original"> |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |

### Battery Usage[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#battery-usage) <a href="#battery-usage" id="battery-usage"></a>

The XIAO ESP32C6 series features a built-in power management chip, allowing it to be powered independently by a battery or to charge the battery through its USB port.

For connecting a battery to your XIAO, we recommend using a qualified rechargeable 3.7V lithium battery. When soldering the battery, carefully distinguish between the positive and negative terminals. The negative terminal should be on the side closest to the USB port, while the positive terminal should be on the side farthest from the USB port.

### Reading Battery Voltage[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#reading-battery-voltage) <a href="#reading-battery-voltage" id="reading-battery-voltage"></a>

To monitor the battery voltage on the XIAO ESP32C6, similar to the [XIAO ESP32C3](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#check-the-battery-voltage), you'll need to solder a 200k resistor in a 1:2 configuration. This setup reduces the voltage by half, allowing safe monitoring through the A0 analog port.

#### Sample Code[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#sample-code) <a href="#sample-code" id="sample-code"></a>

The code below initializes the ADC on the A0 port and averages 16 readings to calculate the battery voltage, adjusting for the 1:2 attenuation ratio of the voltage divider.

```
#include <Arduino.h>

void setup() {
  Serial.begin(115200);
  pinMode(A0, INPUT);         // Configure A0 as ADC input
}

void loop() {
  uint32_t Vbatt = 0;
  for(int i = 0; i < 16; i++) {
    Vbatt += analogReadMilliVolts(A0); // Read and accumulate ADC voltage
  }
  float Vbattf = 2 * Vbatt / 16 / 1000.0;     // Adjust for 1:2 divider and convert to volts
  Serial.println(Vbattf, 3);                  // Output voltage to 3 decimal places
  delay(1000);                                // Wait for 1 second
}
```

This code takes 16 measurements from the ADC, averages them, and then compensates for the voltage divider's 1:2 ratio to output the battery voltage in volts with three decimal places of precision.

### Deep sleep mode and wake-up[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#deep-sleep-mode-and-wake-up) <a href="#deep-sleep-mode-and-wake-up" id="deep-sleep-mode-and-wake-up"></a>

The XIAO ESP32C6 has a complete deep sleep mode and wake-up function. Here we will show two of the more common examples offered by the ESP.

#### Demo1: Deep Sleep with External Wake Up[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#demo1-deep-sleep-with-external-wake-up) <a href="#demo1-deep-sleep-with-external-wake-up" id="demo1-deep-sleep-with-external-wake-up"></a>

This code displays how to use deep sleep with an external trigger as a wake up source and how to store data in RTC memory to use it over reboots.

```
/*
Hardware Connections
======================
Push Button to GPIO 0 pulled down with a 10K Ohm
resistor

NOTE:
======
Bit mask of GPIO numbers which will cause wakeup. Only GPIOs
which have RTC functionality can be used in this bit map.
For different SoCs, the related GPIOs are:
- ESP32: 0, 2, 4, 12-15, 25-27, 32-39
- ESP32-S2: 0-21
- ESP32-S3: 0-21
- ESP32-C6: 0-7
- ESP32-H2: 7-14
*/

#define BUTTON_PIN_BITMASK (1ULL << GPIO_NUM_0) // GPIO 0 bitmask for ext1

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

  /*
  First we configure the wake up source
  We set our ESP32 to wake up for an external trigger.
  There are two types for ESP32, ext0 and ext1, ext0 
  don't support ESP32C6 so we use ext1.
  */

  //If you were to use ext1, you would use it like
  esp_sleep_enable_ext1_wakeup(BUTTON_PIN_BITMASK,ESP_EXT1_WAKEUP_ANY_HIGH);

  //Go to sleep now
  Serial.println("Going to sleep now");
  esp_deep_sleep_start();
  Serial.println("This will never be printed");
}

void loop(){
  //This is not going to be called
}
```

#### Demo2: Deep Sleep with Timer Wake Up[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#demo2-deep-sleep-with-timer-wake-up) <a href="#demo2-deep-sleep-with-timer-wake-up" id="demo2-deep-sleep-with-timer-wake-up"></a>

ESP32 offers a deep sleep mode for effective power saving as power is an important factor for IoT applications. In this mode CPUs, most of the RAM, and all the digital peripherals which are clocked from APB\_CLK are powered off. The only parts of the chip which can still be powered on are: RTC controller, RTC peripherals ,and RTC memories.

This code displays the most basic deep sleep with a timer to wake it up and how to store data in RTC memory to use it over reboots.

```
/*
Simple Deep Sleep with Timer Wake Up
=====================================
This code is under Public Domain License.

Author:
Pranav Cherukupalli <cherukupallip@gmail.com>
*/
#define uS_TO_S_FACTOR 1000000ULL  /* Conversion factor for micro seconds to seconds */
#define TIME_TO_SLEEP  5        /* Time ESP32 will go to sleep (in seconds) */
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

  /*
  First we configure the wake up source
  We set our ESP32 to wake up every 5 seconds
  */
  esp_sleep_enable_timer_wakeup(TIME_TO_SLEEP * uS_TO_S_FACTOR);
  Serial.println("Setup ESP32 to sleep for every " + String(TIME_TO_SLEEP) +
  " Seconds");

  /*
  Next we decide what all peripherals to shut down/keep on
  By default, ESP32 will automatically power down the peripherals
  not needed by the wakeup source, but if you want to be a poweruser
  this is for you. Read in detail at the API docs
  http://esp-idf.readthedocs.io/en/latest/api-reference/system/deep_sleep.html
  Left the line commented as an example of how to configure peripherals.
  The line below turns off all RTC peripherals in deep sleep.
  */
  //esp_deep_sleep_pd_config(ESP_PD_DOMAIN_RTC_PERIPH, ESP_PD_OPTION_OFF);
  //Serial.println("Configured all RTC Peripherals to be powered down in sleep");

  /*
  Now that we have setup a wake cause and if needed setup the
  peripherals state in deep sleep, we can now start going to
  deep sleep.
  In the case that no wake up sources were provided but deep
  sleep was started, it will sleep forever unless hardware
  reset occurs.
  */
  Serial.println("Going to sleep now");
  Serial.flush(); 
  esp_deep_sleep_start();
  Serial.println("This will never be printed");
}
void loop(){
  //This is not going to be called
}
```
