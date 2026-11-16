# FEETECH SCSCL Servo – Memory Table Analysis

> **Magnetic Encoder SCSCL Servo**

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Servo Communication Protocol** <a href="#block-345d4c79856d8102a9e2ed43f4a560ee" id="block-345d4c79856d8102a9e2ed43f4a560ee"></a>

The servo uses the FT-SCS custom protocol. The factory default baud rate is 1 Mbps or 500 kbps, using TTL single-wire bus communication, with 8 data bits, no parity, and 1 stop bit.

The baud rate is configurable from 38,400 to 1 Mbps (or 500 kbps). The default communication address (station ID) is 1.

## **2. Servo Memory Table Definition** <a href="#block-345d4c79856d80e189aad6f5c53fb5a6" id="block-345d4c79856d80e189aad6f5c53fb5a6"></a>

If the function address uses two bytes of data, the low byte is stored at the lower address, and the high byte is stored at the higher address.

### **2.1 Version Information** <a href="#block-345d4c79856d80948aecd475445bd95f" id="block-345d4c79856d80948aecd475445bd95f"></a>

| Address (DEC) | Address (HEX) | Function Name                 | Number of Bytes | Initial Value | Access | Value Range | Unit | Description                              |
| ------------- | ------------- | ----------------------------- | --------------- | ------------- | ------ | ----------- | ---- | ---------------------------------------- |
| 0             | 0x00          | Firmware Major Version Number | 1               | –             | RO     |             |      |                                          |
| 1             | 0x01          | Firmware Minor Version Number | 1               | –             | RO     |             |      |                                          |
| 2             | 0x02          | END                           | 1               | 1             | RO     |             |      | 1 indicates big-endian storage structure |
| 3             | 0x03          | Servo Major Version Number    | 1               | –             | RO     |             |      |                                          |
| 4             | 0x04          | Servo Minor Version Number    | 1               | –             | RO     |             |      |                                          |

### **2.2 EPROM Configuration** <a href="#block-345d4c79856d804ab2d4c01d1dc4bee7" id="block-345d4c79856d804ab2d4c01d1dc4bee7"></a>

| Address (DEC) | Address (HEX) | Function Name                        | Number of Bytes | Initial Value | Access | Value Range | Unit  | Description                                                                                                                |
| ------------- | ------------- | ------------------------------------ | --------------- | ------------- | ------ | ----------- | ----- | -------------------------------------------------------------------------------------------------------------------------- |
| 5             | 0x05          | Servo ID                             | 1               | 1             | RW     | 0 \~ 253    | No.   | Unique master ID on the bus                                                                                                |
| 6             | 0x06          | Baud Rate                            | 1               | 0             | RW     | 0 \~ 7      |       | 0–7 correspond to: 1000000 (0), 500000 (1), 250000 (2), 128000 (3), 115200 (4), 76800 (5), 57600 (6), 38400 (7)            |
| 7             | 0x07          | Undefined                            | 1               | –             | RW     | –           |       |                                                                                                                            |
| 8             | 0x08          | Response Status Level                | 1               | 1             | RW     | 0 \~ 1      |       | 0: No response for instructions except READ and PING; 1: Respond to all instructions                                       |
| 9             | 0x09          | Minimum Angle Limit                  | 2               | 20            | RW     | 0 \~ 1023   | Step  | Minimum operating angle limit; must be less than maximum angle limit; when minimum = maximum = 0, motor mode is enabled    |
| 11            | 0x0B          | Maximum Angle Limit                  | 2               | 1003          | RW     | 1 \~ 1023   | Step  | Maximum operating angle limit; must be greater than minimum angle limit; when minimum = maximum = 0, motor mode is enabled |
| 13            | 0x0D          | Maximum Temperature Limit            | 1               | 70            | RW     | 0 \~ 100    | °C    |                                                                                                                            |
| 14            | 0x0E          | Maximum Input Voltage                | 1               | –             | RW     | 0 \~ 254    | 0.1 V | Maximum input voltage = minimum input voltage = 0 disables voltage feedback                                                |
| 15            | 0x0F          | Minimum Input Voltage                | 1               | 40            | RW     | 0 \~ 254    | 0.1 V | Maximum input voltage = minimum input voltage = 0 disables voltage feedback                                                |
| 16            | 0x10          | Maximum Torque                       | 2               | 1000          | RW     | 0 \~ 1000   | 0.1 % | Assigned to address 48 (Torque Limit) at power-on                                                                          |
| 18            | 0x12          | Phase                                | 1               | –             | RW     | 0 \~ 254    |       | Special function byte, do not modify unless required                                                                       |
| 19            | 0x13          | Unload Condition                     | 1               | –             | RW     | 0 \~ 254    |       | Bit=1 enables corresponding protection; Bit=0 disables                                                                     |
| 20            | 0x14          | LED Alarm Condition                  | 1               | –             | RW     | 0 \~ 254    |       | Bit=1 enables alarm flashing; Bit=0 disables                                                                               |
| 21            | 0x15          | Position Loop Proportional Gain (Kp) | 1               | –             | RW     | 0 \~ 254    |       | Controls motor proportional gain                                                                                           |
| 22            | 0x16          | Position Loop Derivative Gain (Kd)   | 1               | –             | RW     | 0 \~ 254    |       | Controls motor derivative gain                                                                                             |
| 23            | 0x17          | Undefined                            | 1               | –             | RW     | –           | –     |                                                                                                                            |
| 24            | 0x18          | Minimum Starting Torque              | 1               | –             | RW     | 0 \~ 254    | 0.1 % | Sets minimum startup torque                                                                                                |
| 25            | 0x19          | Undefined                            | 1               | –             | RW     | –           | –     |                                                                                                                            |
| 26            | 0x1A          | Positive Dead Zone                   | 1               | 1             | RW     | 0 \~ 16     | Step  | Minimum unit is one minimum resolvable angle                                                                               |
| 27            | 0x1B          | Negative Dead Zone                   | 1               | 1             | RW     | 0 \~ 16     | Step  | Minimum unit is one minimum resolvable angle                                                                               |
| 28 \~ 36      | 0x1C \~ 0x24  | Undefined                            | 1               | –             | RW     | –           | –     |                                                                                                                            |
| 37            | 0x25          | Holding Torque                       | 1               | 20            | RW     | 0 \~ 254    | 1 %   | Output torque after entering overload protection (e.g., 20 = 20%)                                                          |
| 38            | 0x26          | Protection Time                      | 1               | 200           | RW     | 0 \~ 254    | 10 ms | Time duration when overload condition is maintained (e.g., 200 = 2 s, max 2.5 s)                                           |
| 39            | 0x24          | Overload Torque Threshold            | 1               | 80            | RW     | 0 \~ 254    | 1 %   | Threshold that triggers overload protection timing (e.g., 80 = 80% max torque)                                             |

### **2.3 SRAM Control** <a href="#block-345d4c79856d80879a0cf09bed0a1300" id="block-345d4c79856d80879a0cf09bed0a1300"></a>

| Address (DEC) | Address (HEX) | Function Name   | Number of Bytes | Initial Value             | Access | Value Range               | Unit         | Description                                                                                                                                                                        |
| ------------- | ------------- | --------------- | --------------- | ------------------------- | ------ | ------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 40            | 0x28          | Torque Switch   | 1               | 0                         | RW     | 0 \~ 2                    |              | 0: Disable torque / free state; 1: Enable torque; 2: Damping mode                                                                                                                  |
| 41            | 0x29          | Undefined       | 1               | –                         | RW     | –                         | –            |                                                                                                                                                                                    |
| 42            | 0x2A          | Target Position | 2               | 0                         | RW     | 0 \~ 1023                 | Step         | Each step corresponds to the minimum resolvable angle; absolute position control mode, maximum corresponds to the maximum valid angle                                              |
| 44            | 0x2C          | Operating Time  | 2               | 0                         | RW     | 0 \~ 9999 / -1000 \~ 1000 | 1 ms / 0.1 % | Motion time from current position to target position; when operating speed is 0, this parameter takes effect; in motor mode, it sets PWM duty cycle output; Bit10 is direction bit |
| 46            | 0x2E          | Operating Speed | 2               | Default factory max speed | RW     | 0 \~ 1000                 | Step/s       | Number of steps per second                                                                                                                                                         |
| 48            | 0x30          | Lock Flag       | 1               | 1                         | RW     | 0 \~ 1                    |              | 0: Disable write lock (EPROM values saved after power-off); 1: Enable write lock (EPROM values not saved after power-off)                                                          |
| 49 \~ 56      | 0x32 \~ 0x36  | Undefined       | 1               | –                         | RW     | –                         | –            |                                                                                                                                                                                    |

### 2.4 **SRAM Feedback** <a href="#block-345d4c79856d8021991bd94d51472685" id="block-345d4c79856d8021991bd94d51472685"></a>

| Address (DEC) | Address (HEX) | Function Name       | Number of Bytes | Initial Value | Access | Value Range | Unit   | Description                                                                                                                                                               |
| ------------- | ------------- | ------------------- | --------------- | ------------- | ------ | ----------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 56            | 0x38          | Present Position    | 2               | –             | R      | –           | Step   | Feedback of current position in steps; each step corresponds to the minimum angle resolution; in absolute position mode, maximum value corresponds to maximum valid angle |
| 58            | 0x3A          | Present Speed       | 2               | –             | R      | –           | Step/s | Feedback of current motor speed; number of steps per second                                                                                                               |
| 60            | 0x3C          | Present Load        | 2               | –             | R      | –           | 0.1 %  | PWM duty cycle driving the motor; Bit10 is direction bit                                                                                                                  |
| 62            | 0x3E          | Present Voltage     | 1               | –             | R      | –           | 0.1 V  | Current operating voltage                                                                                                                                                 |
| 63            | 0x3F          | Present Temperature | 1               | –             | R      | –           | °C     | Internal temperature of the servo                                                                                                                                         |
| 64            | 0x40          | Async Write Flag    | 1               | 0             | R      | –           | –      | Flag used during asynchronous write operations                                                                                                                            |
| 65            | 0x41          | Servo Status        | 1               | 0             | R      | –           | –      | Bit=1 indicates corresponding error                                                                                                                                       |
| 66            | 0x42          | Moving Flag         | 1               | 0             | R      | –           | –      | 1: moving; 0: stopped at target or no target update                                                                                                                       |

### **2.5 Factory Parameters** <a href="#block-345d4c79856d80cb8109c819fb1e2d57" id="block-345d4c79856d80cb8109c819fb1e2d57"></a>

| Address (DEC) | Address (HEX) | Function Name              | Number of Bytes | Initial Value | Access | Value Range | Unit | Description |
| ------------- | ------------- | -------------------------- | --------------- | ------------- | ------ | ----------- | ---- | ----------- |
| 78            | 0x4E          | Maximum PWM Mode Step      | 1               | 20            | R      | –           | –    |             |
| 79            | 0x50          | Motion Speed Threshold ×50 | 1               | 1             | R      | –           | –    |             |
| 80            | 0x51          | DTs (ms)                   | 1               | 20            | R      | –           | –    |             |
| 81            | 0x52          | Minimum Speed Limit ×50    | 1               | 1             | R      | –           | –    |             |
| 82            | 0x53          | Maximum Speed Limit ×50    | 1               | –             | R      | –           | –    |             |
| 83            | 0x54          | Acceleration               | 1               | 20            | R      | –           | –    |             |

## **3. Special Byte Description** <a href="#block-345d4c79856d805dbab1c265b8f523e7" id="block-345d4c79856d805dbab1c265b8f523e7"></a>

### **3.1 Servo Phase** <a href="#block-345d4c79856d80e0b1ded31a1ca1e567" id="block-345d4c79856d80e0b1ded31a1ca1e567"></a>

**Bit number / bit weight: description**

* BIT0 (1): driver direction phase; (0) forward, (1) reverse
* BIT1 (2): ----
* BIT2 (4): ----
* BIT3 (8): speed mode; (0) speed = 0 means stop, (1) speed = 0 means maximum speed
* BIT4 (16): ----
* BIT5 (32): PWM phase; (0) in-phase, (1) inverted phase
* BIT6 (64): voltage mode; (0) 1.5K low-voltage sampling, (1) 1K high-voltage sampling
* BIT7 (128): ----

💡

**Note:**&#x49;f multiple bits are set simultaneously, the servo phase value equals the sum of all bit values.

### **3.2 Servo Status** <a href="#block-345d4c79856d80108c9ae38e4cd79028" id="block-345d4c79856d80108c9ae38e4cd79028"></a>

**Servo status: 0 indicates normal, 1 indicates abnormal**

**Bit number / bit weight: description**

* BIT0 (1): voltage status
* BIT1 (2): ----
* BIT2 (4): temperature status
* BIT3 (8): ----
* BIT4 (16): ----
* BIT5 (32): load status
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:**&#x49;f multiple statuses occur simultaneously, the servo status value equals the sum of all bit values.

**For example:**&#x76;oltage over/under-voltage and servo overheat, then the servo status value is 4 + 1 = 5.

### **3.3 Unload Condition** <a href="#block-345d4c79856d80ce97d3e17a8fed19b8" id="block-345d4c79856d80ce97d3e17a8fed19b8"></a>

**Unload condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage protection
* BIT1 (2): ----
* BIT2 (4): overheat protection
* BIT3 (8): ----
* BIT4 (16): ----
* BIT5 (32): load overload
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:**&#x49;f multiple bits are set, the unload condition value equals the sum of all bit values.

**For example:**&#x76;oltage protection and overheat protection enabled at the same time, then the unload condition value is 4 + 1 = 5.

### **3.4 LED Alarm Condition** <a href="#block-345d4c79856d80bb8204c6e9bfaa76c3" id="block-345d4c79856d80bb8204c6e9bfaa76c3"></a>

**LED alarm condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage alarm
* BIT1 (2): ----
* BIT2 (4): overheat alarm
* BIT3 (8): ----
* BIT4 (16): ----
* BIT5 (32): load overload alarm
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:** If multiple bits are set simultaneously, the LED alarm condition value equals the sum of all bit values.

**For example:** voltage alarm and overheat alarm enabled at the same time, then the alarm condition value is 4 + 1 = 5.
