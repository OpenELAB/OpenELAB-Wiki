# FEETECH STS Servo – Memory Table Analysis

> **Magnetic Encoder FEETECH STS Servo**

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Servo Communication Protocol** <a href="#block-344d4c79856d8111857acdef3eeb1047" id="block-344d4c79856d8111857acdef3eeb1047"></a>

The servo uses the FT-SCS custom protocol. The factory default serial configuration is as follows: baud rate 1 Mbps, using TTL single-wire bus communication, 8 data bits, no parity, and 1 stop bit.

The baud rate is configurable from 38,400 to 1 Mbps. The default communication address (station ID) is 1.

## **2. Servo Memory Table Definition** <a href="#block-344d4c79856d80a9bbeced4b05d99f9c" id="block-344d4c79856d80a9bbeced4b05d99f9c"></a>

If the function address uses two bytes of data, the low byte is stored at the lower address, and the high byte is stored at the higher address.

### **2.1 Version Information** <a href="#block-344d4c79856d802dbb0cd65336451a23" id="block-344d4c79856d802dbb0cd65336451a23"></a>

| Address (DEC) | Address (HEX) | Function Name                 | Number of Bytes | Initial Value | Access | Value Range | Unit | Description                                 |
| ------------- | ------------- | ----------------------------- | --------------- | ------------- | ------ | ----------- | ---- | ------------------------------------------- |
| 0             | 0x00          | Firmware Major Version Number | 1               | –             | RO     |             |      |                                             |
| 1             | 0x01          | Firmware Minor Version Number | 1               | –             | RO     |             |      |                                             |
| 2             | 0x02          | END                           | 1               | 0             | RO     |             |      | 0 indicates little-endian storage structure |
| 3             | 0x03          | Servo Major Version Number    | 1               | –             | RO     |             |      |                                             |
| 4             | 0x04          | Servo Minor Version Number    | 1               | –             | RO     |             |      |                                             |

### **2.2 EPROM Configuration** <a href="#block-344d4c79856d8041b5cae8aac95c8a2f" id="block-344d4c79856d8041b5cae8aac95c8a2f"></a>

| Address (DEC) | Address (HEX) | Function Name                        | Number of Bytes | Initial Value | Access | Value Range | Unit          | Description                                                                                                     |
| ------------- | ------------- | ------------------------------------ | --------------- | ------------- | ------ | ----------- | ------------- | --------------------------------------------------------------------------------------------------------------- |
| 5             | 0x05          | Servo ID                             | 1               | 1             | RW     | 0 \~ 253    | No.           | Unique master ID on the bus                                                                                     |
| 6             | 0x06          | Baud Rate                            | 1               | 0             | RW     | 0 \~ 7      |               | 0–7 correspond to: 1000000 (0), 500000 (1), 250000 (2), 128000 (3), 115200 (4), 76800 (5), 57600 (6), 38400 (7) |
| 7             | 0x07          | Reserved Address                     | 1               | –             | RW     | –           | –             |                                                                                                                 |
| 8             | 0x08          | Response Status Level                | 1               | 1             | RW     | 0 \~ 1      |               | 0: No response except READ and PING; 1: Respond to all instructions                                             |
| 9             | 0x09          | Minimum Angle Limit                  | 2               | 0             | RW     | 0 \~ 4094   | 0.087 degrees | 0 when multi-turn absolute position control is used                                                             |
| 11            | 0x0B          | Maximum Angle Limit                  | 2               | 4095          | RW     | 1 \~ 4095   | 0.087 degrees | 0 when multi-turn absolute position control is used                                                             |
| 13            | 0x0D          | Maximum Temperature Limit            | 1               | 70            | RW     | 0 \~ 100    | °C            |                                                                                                                 |
| 14            | 0x0E          | Maximum Input Voltage                | 1               | –             | RW     | 0 \~ 254    | 0.1 V         |                                                                                                                 |
| 15            | 0x0F          | Minimum Input Voltage                | 1               | 40            | RW     | 0 \~ 254    | 0.1 V         |                                                                                                                 |
| 16            | 0x10          | Maximum Torque                       | 2               | 1000          | RW     | 0 \~ 1000   | 0.1 %         | Assigned to address 48 (Torque Limit) at power-on                                                               |
| 18            | 0x12          | Phase                                | 1               | –             | RW     | 0 \~ 254    |               | Special function byte, do not modify unless required                                                            |
| 19            | 0x13          | Unload Condition                     | 1               | –             | RW     | 0 \~ 254    |               | Bit=1 enables corresponding protection; Bit=0 disables                                                          |
| 20            | 0x14          | LED Alarm Condition                  | 1               | –             | RW     | 0 \~ 254    |               | Bit=1 enables alarm flashing; Bit=0 disables                                                                    |
| 21            | 0x15          | Position Loop Proportional Gain (Kp) | 1               | –             | RW     | 0 \~ 254    |               | Proportional gain (scaled by 1/4)                                                                               |
| 22            | 0x16          | Position Loop Derivative Gain (Kd)   | 1               | –             | RW     | 0 \~ 254    |               | Derivative gain (scaled by 1/8)                                                                                 |
| 23            | 0x17          | Position Loop Integral Gain (Ki)     | 1               | 0             | RW     | 0 \~ 254    |               | Integral gain                                                                                                   |
| 24            | 0x18          | Minimum Starting Torque              | 1               | –             | RW     | 0 \~ 254    | 0.1 %         | Minimum startup torque                                                                                          |
| 25            | 0x19          | Integral Limit Value                 | 1               | 0             | RW     | 0 \~ 254    |               | Max integral = value × 4; 0 disables; valid in mode 0 and 4                                                     |
| 26            | 0x1A          | Positive Dead Zone                   | 1               | 1             | RW     | 0 \~ 16     | 0.087 degrees | Minimum unit equals minimum resolvable angle                                                                    |
| 27            | 0x1B          | Negative Dead Zone                   | 1               | 1             | RW     | 0 \~ 16     | 0.087 degrees | Minimum unit equals minimum resolvable angle                                                                    |
| 28            | 0x1C          | Protection Current                   | 2               | 511           | RW     | 0 \~ 2047   | 6.5 mA        | Max current = 500 × 6.5 mA = 3250 mA                                                                            |
| 30            | 0x1E          | Angular Resolution                   | 1               | 1             | RW     | 1 \~ 128    |               | Amplification factor of sensor resolution                                                                       |
| 31            | 0x1F          | Position Offset                      | 2               | 0             | RW     | 0 \~ 8191   | 0.087 degrees | Encoded offset: maps to -4095 \~ 4095 (see encoding rules)                                                      |
| 33            | 0x21          | Operating Mode                       | 1               | 0             | RW     | 0 \~ 3      |               | 0: Position mode; 1: Constant speed mode; 2: PWM open-loop mode; 3: Step mode                                   |
| 34            | 0x22          | Holding Torque                       | 1               | 20            | RW     | 0 \~ 254    | 1 %           | Output torque after overload protection (e.g., 20 = 20%)                                                        |
| 35            | 0x23          | Protection Time                      | 1               | 200           | RW     | 0 \~ 254    | 10 ms         | Duration exceeding overload torque (e.g., 200 = 2 s, max 2.5 s)                                                 |
| 36            | 0x24          | Overload Torque Threshold            | 1               | 80            | RW     | 0 \~ 254    | 1 %           | Threshold to trigger overload protection timing                                                                 |
| 37            | 0x25          | Velocity Loop Proportional Gain (Kp) | 1               | –             | RW     | 0 \~ 254    |               | Used in constant speed mode (Mode 1)                                                                            |
| 38            | 0x26          | Overcurrent Protection Time          | 1               | 200           | RW     | 0 \~ 254    | 10 ms         | Max = 254 × 10 ms = 2540 ms                                                                                     |
| 39            | 0x27          | Velocity Loop Integral Gain (Ki)     | 1               | –             | RW     | 0 \~ 254    |               | Used in constant speed mode (Mode 1)                                                                            |

### **2.3 SRAM Control** <a href="#block-344d4c79856d80d1a72ce5c378926447" id="block-344d4c79856d80d1a72ce5c378926447"></a>

| Address (DEC) | Address (HEX) | Function Name       | Number of Bytes | Initial Value                     | Access | Value Range     | Unit                   | Description                                                                                                                                                                  |
| ------------- | ------------- | ------------------- | --------------- | --------------------------------- | ------ | --------------- | ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 40            | 0x28          | Torque Switch       | 1               | 0                                 | RW     | 0 \~ 2          |                        | 0: Disable torque; 1: Enable torque; 2: Damping mode (torque limit at address 48 controls damping strength); 128: Calibrate current position to 2048                         |
| 41            | 0x29          | Acceleration        | 1               | 0                                 | RW     | 0 \~ 254        | 8.7 degrees/s²         | Acceleration/deceleration of servo; 0 indicates maximum acceleration                                                                                                         |
| 42            | 0x2A          | Target Position     | 2               | 0                                 | RW     | -32767 \~ 32767 | 0.087 degrees          | Absolute position control; max corresponds to max valid angle; Bit15 is direction bit                                                                                        |
| 44            | 0x2C          | PWM Open-loop Speed | 2               | 1000                              | RW     | 0 \~ 1000       | 0.1 %                  | Effective in PWM open-loop mode; Bit10 is direction bit                                                                                                                      |
| 46            | 0x2E          | Operating Speed     | 2               | Max factory speed                 | RW     | -32767 \~ 32767 | 0.732 RPM / 0.0146 RPM | Maximum motor speed; Bit15 is direction bit; 0 means max speed by default; can be set to stop via phase; unit selectable (0.732 or 0.0146 RPM), resolution remains 0.732 RPM |
| 48            | 0x30          | Torque Limit        | 2               | Maximum Torque (16), default 1000 | RW     | 0 \~ 1000       | 0.1 %                  | User-configurable stall torque output                                                                                                                                        |
| 50 \~ 54      | 0x32 \~ 0x36  | Undefined           | 1               | –                                 | RW     | –               | –                      |                                                                                                                                                                              |
| 55            | 0x37          | Lock Flag           | 1               | 1                                 | RW     | 0 \~ 1          |                        | 0: Disable write lock (EPROM values saved after power-off); 1: Enable write lock (EPROM values not saved after power-off)                                                    |

### 2.4 **SRAM Feedback** <a href="#block-344d4c79856d80ecbf04cc3095d6c500" id="block-344d4c79856d80ecbf04cc3095d6c500"></a>

| Address (DEC) | Address (HEX) | Function Name       | Number of Bytes | Initial Value | Access | Value Range | Unit                   | Description                                                                                                                                                        |
| ------------- | ------------- | ------------------- | --------------- | ------------- | ------ | ----------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 56            | 0x38          | Present Position    | 2               | –             | R      | –           | 0.087 degrees          | Feedback of current absolute position; Bit15 is direction; in Step mode (Mode 3), returns step difference between current and target position (Bit15 is direction) |
| 58            | 0x3A          | Present Speed       | 2               | –             | R      | –           | 0.732 RPM / 0.0146 RPM | Feedback of current motor speed; unit depends on phase setting; Bit15 is direction                                                                                 |
| 60            | 0x3C          | Present Load        | 2               | –             | R      | –           | 0.1 %                  | PWM duty cycle driving the motor; Bit10 is direction                                                                                                               |
| 62            | 0x3E          | Present Voltage     | 1               | –             | R      | –           | 0.1 V                  | Current operating voltage                                                                                                                                          |
| 63            | 0x3F          | Present Temperature | 1               | –             | R      | –           | °C                     | Internal temperature of the servo                                                                                                                                  |
| 64            | 0x40          | Async Write Flag    | 1               | 0             | R      | –           |                        | Flag used during asynchronous write operations                                                                                                                     |
| 65            | 0x41          | Servo Status        | 1               | 0             | R      | –           |                        | Bit flags; Bit=1 indicates corresponding error                                                                                                                     |
| 66            | 0x42          | Moving Flag         | 1               | 0             | R      | –           |                        | 1: moving; 0: stopped at target or no target update                                                                                                                |
| 67            | 0x43          | Target Position     | 2               | 0             | R      | –           | 0.087 degrees          | Current target position                                                                                                                                            |
| 69            | 0x45          | Present Current     | 2               | –             | R      | –           | 6.5 mA                 | Phase current feedback                                                                                                                                             |
| 71            | 0x47          | Undefined           | 2               | –             | R      | –           | –                      |                                                                                                                                                                    |

### **2.5 Factory Parameters** <a href="#block-344d4c79856d801e8147c3db3a30a052" id="block-344d4c79856d801e8147c3db3a30a052"></a>

| Address (DEC) | Address (HEX) | Function Name           | Number of Bytes | Initial Value | Access | Value Range | Unit      | Description                                                                                                           |
| ------------- | ------------- | ----------------------- | --------------- | ------------- | ------ | ----------- | --------- | --------------------------------------------------------------------------------------------------------------------- |
| 80            | 0x50          | Motion Speed Threshold  | 1               | –             | R      | –           | –         | Threshold for determining whether the servo is in motion                                                              |
| 81            | 0x51          | DTs (ms)                | 1               | –             | R      | –           | ms        | Internal control cycle timing parameter                                                                               |
| 82            | 0x52          | Velocity Scaling Factor | 1               | –             | R      | –           | –         | Scaling factor for velocity unit conversion                                                                           |
| 83            | 0x53          | Minimum Speed Limit     | 1               | –             | R      | –           | 0.732 RPM | Minimum allowable speed limit                                                                                         |
| 84            | 0x54          | Maximum Speed Limit     | 1               | –             | R      | –           | 0.732 RPM | Maximum allowable speed limit                                                                                         |
| 85            | 0x55          | Acceleration Limit      | 1               | –             | R      | –           | –         | Factory-defined maximum acceleration limit                                                                            |
| 86            | 0x56          | Acceleration Multiplier | 1               | –             | R      | –           | –         | Effective when acceleration = 0; if both multiplier and acceleration are 0, the servo achieves maximum response speed |

## **3. Special Byte Description** <a href="#block-344d4c79856d806b9645e3693286bf1b" id="block-344d4c79856d806b9645e3693286bf1b"></a>

### **3.1 Servo Phase** <a href="#block-344d4c79856d806ca676c762689f38a9" id="block-344d4c79856d806ca676c762689f38a9"></a>

**Bit number / bit weight: description**

* BIT0 (1): driver direction phase; (0) forward, (1) reverse
* BIT1 (2): driver bridge mode; (0) brushless, (1) brushed (effective after reboot)
* BIT2 (4): speed unit; (0) 0.732 RPM, (1) 0.0146 RPM
* BIT3 (8): speed mode; (0) speed = 0 means stop, (1) speed = 0 means maximum speed
* BIT4 (16): angle feedback mode; (0) single-turn angle feedback, (1) full-range angle feedback
* BIT5 (32): driver bridge configuration / voltage sampling; (0) independent H-bridge / 1K high-voltage sampling, (1) integrated H-bridge / 1.5K low-voltage sampling / no current feedback
* BIT6 (64): PWM frequency; (0) 24 kHz, (1) 16 kHz
* BIT7 (128): position feedback direction phase; (0) forward, (1) reverse

💡

**Note:**&#x49;f multiple bits are set simultaneously, the servo phase value equals the sum of all bit values.

**For example:** If the original phase value is 0 and reverse operation is required, the phase value is 128 + 1 = 129.

### **3.2 Servo Status** <a href="#block-344d4c79856d80b2a9a9d50c81cf06d7" id="block-344d4c79856d80b2a9a9d50c81cf06d7"></a>

**Servo status: 0 indicates normal, 1 indicates abnormal**

**Bit number / bit weight: description**

* BIT0 (1): voltage status
* BIT1 (2): magnetic encoder status
* BIT2 (4): temperature status
* BIT3 (8): current status
* BIT4 (16): ----
* BIT5 (32): load status
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:**&#x49;f multiple statuses occur simultaneously, the servo status value equals the sum of all bit values.

**For example:**&#x76;oltage over/under-voltage and servo overheat, then the servo status value is 4 + 1 = 5.

### **3.3 Unload Condition** <a href="#block-344d4c79856d809bb718fa2e2d1eb054" id="block-344d4c79856d809bb718fa2e2d1eb054"></a>

**Unload condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage protection
* BIT1 (2): magnetic encoder protection
* BIT2 (4): overheat protection
* BIT3 (8): overcurrent protection
* BIT4 (16): ----
* BIT5 (32): load overload protection
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:**&#x49;f multiple bits are set, the unload condition value equals the sum of all bit values.

**For example:**&#x76;oltage protection and overheat protection enabled at the same time, then the unload condition value is 4 + 1 = 5.

### **3.4 LED Alarm Condition** <a href="#block-344d4c79856d807e8efcd12f67c2124d" id="block-344d4c79856d807e8efcd12f67c2124d"></a>

**Alarm condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage alarm
* BIT1 (2): magnetic encoder alarm
* BIT2 (4): overheat alarm
* BIT3 (8): overcurrent alarm
* BIT4 (16): ----
* BIT5 (32): load overload alarm
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:** If multiple bits are set simultaneously, the alarm condition value equals the sum of all bit values.

**For example:** voltage alarm and overheat alarm enabled at the same time, then the alarm condition value is 4 + 1 = 5.
