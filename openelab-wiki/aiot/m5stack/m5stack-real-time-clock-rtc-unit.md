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

# M5Stack Real Time Clock (RTC) Unit

### M5Stack Real Time Clock (RTC) Unit

***

### Product Link

{% embed url="https://openelab.io/products/real-time-clock-rtc-unit" %}

### Description <a href="#description" id="description"></a>

**UNIT RTC** is a programmable real-time clock module, integrated HYM8563 low-power CMOS real-time clock/calendar chip, using I2C communication interface, full-coverage case can effectively protect the circuit, making its operation more stable. Applicable to a variety of embedded devices, instruments and instruments as a system clock.

### Role of RTC <a href="#role-of-rtc" id="role-of-rtc"></a>

Most MCUs are built-in timers, which usually start working automatically when the hardware is powered on, and reset when the hardware is powered off. The built-in timer can handle some simple timing tasks, but if we want to implement data timestamp recording, clock, alarm clock and other time-span functions, a system power-independent clock RTC is the best choice.

### Features <a href="#product-features" id="product-features"></a>

* Support second/minute/hour/day/month/year. time data reading and writing
* 32.768kHz high-precision clock crystal, greatly reducing the time error
* Low power consumption, coin battery can work continuously for years
* With century mark
* I2C communication interface

### Applications <a href="#applications" id="applications"></a>

* Clock, alarm clock
* Power down time synchronization

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications          | Parameters                             |
| ----------------------- | -------------------------------------- |
| Clock chip              | HYM8563                                |
| Crystal Frequency       | 32.768kHz                              |
| Communication interface | I2C, addr: 0x51, bus max speed 400Kbps |
| Power supply voltage    | 5V DC                                  |
| Net weight              | 4.1g                                   |
| Gross Weight            | 8.3g                                   |
| Product Dimensions      | 48 \* 24 \* 8mm                        |
| Package Size            | 136 \* 92 \* 13mm                      |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/rtc_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/rtc_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/rtc_06.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/rtc_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

* **Datasheet**
  * [HYM8563](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/rtc/HYM8563_Datasheet_V2.2_cn.pdf)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Unit-RTC - with M5Series](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Series/Unit_RTC_M5Series.ino)
* [M5Unit-RTC III with M5Atom](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Atom/Unit_RTC_M5Atom.ino)
* [M5Unit-RTC III with M5Core](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Core/Unit_RTC_M5Core.ino)
* [M5Unit-RTC III with M5Core2](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Core2/Unit_RTC_M5Core2.ino)
* [M5Unit-RTC III with M5StickC](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5StickC/Unit_RTC_M5StickC.ino)
* [M5Unit-RTC III with M5StickCPlus](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5StickCPlus/Unit_RTC_M5StickCPlus.ino)

#### UIFlow Example <a href="#uiflow-example" id="uiflow-example"></a>

* Clock Example

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow01_v1_10_2.webp" alt=""><figcaption></figcaption></figure>

* Timer Example

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow02.webp" alt=""><figcaption></figcaption></figure>

* Alarm Example

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow03_v1_10_2.webp" alt=""><figcaption></figcaption></figure>

### UIFlow <a href="#uiflow" id="uiflow"></a>

* Set RTC(year(0 - 99), month, date, weekday(1 - 7), hour, minute, second)
  * weekday
    * 1: Sunday
    * 2: Monday
    * 3: Tuesday
    * 4: Wednesday
    * 5: Thursday
    * 6: Friday
    * 7: Saturday

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow04.webp)

* Get RTC\
  Get list of RTCData. ex. (22, 7, 23, 6, 13, 0, 0)\
  **notice**: Before UIFlow v1.10.1
  * year(0 - 99)
  * month(1 - 12)
  * date(0 - 31)
  * weekday(1:Sunday - 7:Saturday)
  * hour(0 - 23)
  * minute(0 - 59)
  * second(0 - 59)

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow05.webp)

* Get RTC\
  Get RTCData.\
  **notice:** After UIFlow v1.10.2
  * year(0 - 99)
  * month(1 - 12)
  * date(0 - 31)
  * weekday(1:Sunday - 7:Saturday)
  * hour(0 - 23)
  * minute(0 - 59)
  * second(0 - 59)

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow17_v1_10_2.webp)

* Set alarm (date, hour, minute)\
  Set the alarm date and time.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow06.webp)

* Check alarm flag\
  Returns True at the specified date and time.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow07.webp)

* Turn off alarm\
  Turn off alarm and reset alarm flag.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow08.webp)

* Disable alarm

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow09.webp)

* Set timer value(count, unit)\
  Set timer in minutes or seconds.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow10.webp)

* Get timer value\
  Get current timer count.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow11.webp)

* Check timer flag\
  Returns True at the specified date and time.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow12.webp)

* Turn off timer\
  Reset timer flag. but timer count don't stop.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow13.webp)

* Disable timer. Reset timer flag and count stop .

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow14.webp)

* Pause timer.\
  Pause timer count.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow15.webp)

* Resume timer.\
  Resume after pause is executed.

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rtc/unit_rtc_uiflow16.webp)
