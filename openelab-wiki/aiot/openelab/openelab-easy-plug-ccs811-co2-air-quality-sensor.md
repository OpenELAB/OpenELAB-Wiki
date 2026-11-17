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

# OpenELAB EASY PLUG CCS811 CO2 Air Quality Sensor

### OpenELAB EASY PLUG CCS811 CO2 Air Quality Sensor

***

### Product Link

{% embed url="https://openelab.io/products/ccs811-co2-air-quality-sensor" %}

### Introduction

EASY plug CCS811 CO2 air quality sensor can work with EASY plug control board V2.0, by connecting it to the I2C communication port with a cable.

This sensor adopts the CCS811 chip, a ultra-low consumption digital air sensor, which can detect a variety of volatile organic compounds (TVOC), including equivalent carbon dioxide (eCO2) and metal oxide (MOX). The detected range of carbon dioxide is 400\~29206 ppm, the range of organic compound (TVOC) is 0\~32768ppb.

### Specifications

* Working voltage: DC 5V
* Working current: 30mA
* Maximum power: 60mW
* eCO2 measurement range: 400-29206 ppm
* TVOC measurement range: 0 to 32768ppb
* Interface: I2C communication interface
* Environmental protection attributes: ROHS

### Pinout

<figure><img src="../../.gitbook/assets/image (454).png" alt=""><figcaption></figcaption></figure>

### Dimensions

* Size: 30\*20\*15mm
* Weight: 4g

### How to Use

#### Test Code

Note: 1.The corresponding library file must be placed in the library file folder where Arduino IDE is installed before uploading the code.

2\. When testing, arduino 1.8.7 version IDE test is required, other versions may not be compatible.

```
#include <CCS811.h>

/*
 * IIC address default 0x5A, the address becomes 0x5B if the ADDR_SEL is soldered.
 */
//CCS811 sensor(&Wire, /*IIC_ADDRESS=*/0x5A);
CCS811 sensor;

void setup(void)
{
    Serial.begin(115200);
    /*Wait for the chip to be initialized completely, and then exit*/
    while(sensor.begin() != 0){
        Serial.println("failed to init chip, please check if the chip connection is fine");
        delay(1000);
    }
    /**
     * @brief Set measurement cycle
     * @param cycle:in typedef enum{
     *                  eClosed,      //Idle (Measurements are disabled in this mode)
     *                  eCycle_1s,    //Constant power mode, IAQ measurement every second
     *                  eCycle_10s,   //Pulse heating mode IAQ measurement every 10 seconds
     *                  eCycle_60s,   //Low power pulse heating mode IAQ measurement every 60 seconds
     *                  eCycle_250ms  //Constant power mode, sensor measurement every 250ms
     *                  }eCycle_t;
     */
    sensor.setMeasCycle(sensor.eCycle_250ms);
}
void loop() {
  delay(1000);
    if(sensor.checkDataReady() == true){
        Serial.print("CO2: ");
        Serial.print(sensor.getCO2PPM());
        Serial.print("ppm, TVOC: ");
        Serial.print(sensor.getTVOCPPB());
        Serial.println("ppb");
        
    } else {
        Serial.println("Data is not ready!");
    }
    /*!
     * @brief Set baseline
     * @param get from getBaseline.ino
     */
    sensor.writeBaseLine(0x847B);
    //delay cannot be less than measurement cycle
    //delay(1000);
}
```

#### Test Result

Hook up according to the wiring diagram, upload the code, plug in power, open the serial monitor and set the baud rate to 115200. Then the corresponding data is shown. The data is incorrect at the beginning, wait a few minutes (up to 20 minutes) until it is stable

<figure><img src="https://wiki.keyestudio.com/images/thumb/0/05/%E5%9B%BE%E7%89%873.png/600px-%E5%9B%BE%E7%89%873.png" alt=""><figcaption></figcaption></figure>

When blowing to the sensor, the data obviously changes

<figure><img src="https://wiki.keyestudio.com/images/thumb/1/1e/%E5%9B%BE%E7%89%874.png/600px-%E5%9B%BE%E7%89%874.png" alt=""><figcaption></figcaption></figure>
