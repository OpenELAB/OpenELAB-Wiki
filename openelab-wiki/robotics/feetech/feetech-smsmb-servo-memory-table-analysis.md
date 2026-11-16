# FEETECH SMSMB Servo – Memory Table Analysis

> **Magnetic Encoder SMSMB Servo**

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Servo Communication Protocol** <a href="#block-345d4c79856d81d9a0e8eea92bc4c5b7" id="block-345d4c79856d81d9a0e8eea92bc4c5b7"></a>

The servo uses the MODBUS-RTU standard protocol. The factory default serial configuration is as follows: baud rate 115200, with 8 data bits, no parity, and 1 stop bit.

The baud rate is configurable from 9600 to 256 Kbps.

The default communication address (station ID) is 1.

## **2. Servo Memory Table Definition** <a href="#block-345d4c79856d8017b40dec1c7962f7e9" id="block-345d4c79856d8017b40dec1c7962f7e9"></a>

### **2.1 Version Information** <a href="#block-345d4c79856d80bba2f6cc760f6fdb44" id="block-345d4c79856d80bba2f6cc760f6fdb44"></a>

| Address (DEC) | Address (HEX) | Function Name           | Number of Bytes | Initial Value | Access | Value Range | Unit | Description |
| ------------- | ------------- | ----------------------- | --------------- | ------------- | ------ | ----------- | ---- | ----------- |
| 0             | 0x00          | Firmware Version Number | 2               | –             | RO     |             |      |             |
| 1             | 0x01          | Servo Version Number    | 2               | –             | RO     |             |      |             |
| 2             | 0x02          | Firmware Release Year   | 2               | –             | RO     |             |      |             |
| 3             | 0x03          | Firmware Release Month  | 2               | –             | RO     |             |      |             |

### **2.2 EPROM Configuration** <a href="#block-345d4c79856d80ee928bc78e85bba38c" id="block-345d4c79856d80ee928bc78e85bba38c"></a>

| Address (DEC) | Address (HEX) | Address (PLC) | Function Name                   | Number of Bytes | Initial Value | Access | Value Range   | Unit           | Description                                                                                                                      |
| ------------- | ------------- | ------------- | ------------------------------- | --------------- | ------------- | ------ | ------------- | -------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 10            | 0x0A          | 40011         | ID                              | 2               | 1             | RW     | 1 \~ 247      | No.            | Unique identification number on the bus; duplicate IDs are not allowed. Address 0 (0x00) is the broadcast ID                     |
| 11            | 0x0B          | 40012         | Baud Rate                       | 2               | 2             | RW     | 0 \~ 9        |                | 0–9 correspond to: 256000 (0), 128000 (1), 115200 (2), 57600 (3), 56000 (4), 38400 (5), 19200 (6), 14400 (7), 9600 (8), 4800 (9) |
| 12            | 0x0C          | 40013         | Response Delay                  | 2               | 500           | RW     | 0 \~ 500      | 1 µs           | 0 indicates minimum response delay; maximum is 500 µs                                                                            |
| 13            | 0x0D          | 40014         | Minimum Angle Limit             | 2               | 0             | RW     | 0 \~ 4095     | 0.0879 degrees | Minimum motion range limit; must be less than maximum angle limit; set to 0 in multi-turn absolute mode                          |
| 14            | 0x0E          | 40015         | Maximum Angle Limit             | 2               | 4095          | RW     | 0 \~ 4095     | 0.0879 degrees | Maximum motion range limit; must be greater than minimum angle limit; set to 0 in multi-turn absolute mode                       |
| 15            | 0x0F          | 40016         | Position Calibration            | 2               | 0             | RW     | -2047 \~ 2047 | 0.0879 degrees | Calibration range; writing 4 via fault reset (134) calculates and stores mid-position (2048)                                     |
| 16            | 0x10          | 40017         | Operating Mode                  | 2               | 0             | RW     | 0 \~ 4        |                | 0: Servo mode; 1: Constant speed mode; 2: Reserved; 3: Special mode (torque disabled at target); 4: Step mode                    |
| 17            | 0x11          | 40018         | Position Loop Proportional Gain | 2               | –             | RW     | 0 \~ 254      |                | Controls proportional gain of motor                                                                                              |
| 18            | 0x12          | 40019         | Position Loop Derivative Gain   | 2               | –             | RW     | 0 \~ 254      |                | Controls derivative gain of motor                                                                                                |
| 19            | 0x13          | 40020         | Position Loop Integral Gain     | 2               | 0             | RW     | 0 \~ 254      |                | Controls integral gain of motor                                                                                                  |
| 20            | 0x14          | 40021         | Speed Loop Proportional Gain    | 2               | –             | RW     | 0 \~ 254      |                | Speed loop proportional gain in constant speed mode (Mode 1)                                                                     |
| 21            | 0x15          | 40022         | Speed Loop Integral Gain        | 2               | –             | RW     | 0 \~ 254      |                | Speed loop integral gain in constant speed mode (Mode 1)                                                                         |

### **2.3 SRAM Control** <a href="#block-345d4c79856d8059b9ede42947e4fa68" id="block-345d4c79856d8059b9ede42947e4fa68"></a>

| Address (DEC) | Address (HEX) | Address (PLC) | Function Name   | Number of Bytes | Initial Value              | Access | Value Range     | Unit            | Description                                                                                                                                                                          |
| ------------- | ------------- | ------------- | --------------- | --------------- | -------------------------- | ------ | --------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 128           | 0x80          | 40129         | Target Position | 2               | 0                          | RW     | -32768 \~ 32767 | 0.0879 degrees  | Absolute position control mode; maximum value corresponds to maximum valid angle                                                                                                     |
| 129           | 0x81          | 40130         | Torque Switch   | 2               | 0                          | RW     | 0 \~ 1          |                 | 0: Disable torque output; 1: Enable torque output                                                                                                                                    |
| 130           | 0x82          | 40131         | Acceleration    | 2               | Default acceleration value | RW     | 0 \~ 65535      | 8.79 degrees/s² | If set to 0, maximum acceleration is used; initialized from “Acceleration Default Value (405)” at power-on                                                                           |
| 131           | 0x83          | 40132         | Operating Speed | 2               | Default speed value        | RW     | 0 \~ 65535      | 0.732 RPM       | Initialized from “Speed Default Value (406)” at power-on                                                                                                                             |
| 132           | 0x84          | 40133         | Torque Limit    | 2               | Default torque limit       | RW     | 0 \~ 1000       | 0.1 %           | Initial value is loaded from torque limit default (0x194); user can modify to control maximum output torque; also affects speed linearly (reducing torque reduces no-load max speed) |
| 133           | 0x85          | 40134         | Lock Flag       | 2               | 1                          | RW     | 0 \~ 1 / 128    |                 | 0: Disable EPROM write lock (values saved after power-off); 1: Enable write lock (values not saved after power-off); 128: Disable factory parameter write lock                       |
| 134           | 0x86          | 40135         | Fault Reset     | 2               | 0                          | RW     | 0 \~ 65535      |                 | Each bit resets corresponding fault when set to 1; after successful reset, the bit is cleared; see special byte definition for details                                               |

### 2.4 **SRAM Feedback** <a href="#block-345d4c79856d8034bdb8ea7fcba77176" id="block-345d4c79856d8034bdb8ea7fcba77176"></a>

| Address (DEC) | Address (HEX) | Address (PLC) | Function Name       | Number of Bytes | Initial Value | Access | Value Range | Unit           | Description                                                                                                    |
| ------------- | ------------- | ------------- | ------------------- | --------------- | ------------- | ------ | ----------- | -------------- | -------------------------------------------------------------------------------------------------------------- |
| 256           | 0x100         | 40257         | Servo Status        | 2               | 0             | RO     | –           |                | Bit=1 indicates corresponding error; see special byte definition                                               |
| 257           | 0x101         | 40258         | Present Position    | 2               | 0             | RO     | –           | 0.0879 degrees | Feedback of current position; absolute position control mode, maximum value corresponds to maximum valid angle |
| 258           | 0x102         | 40259         | Present Speed       | 2               | 0             | RO     | –           | 0.732 RPM      | Feedback of current motor speed                                                                                |
| 259           | 0x103         | 40260         | Output PWM          | 2               | 0             | RO     | –           | 0.1 %          | Current PWM duty cycle driving the motor                                                                       |
| 260           | 0x104         | 40261         | Present Voltage     | 2               | 0             | RO     | –           | 0.1 V          | Current operating voltage                                                                                      |
| 261           | 0x105         | 40262         | Present Temperature | 2               | 0             | RO     | –           | °C             | Internal servo temperature                                                                                     |
| 262           | 0x106         | 40263         | Moving Flag         | 2               | 0             | RO     | –           |                | 1: moving; 0: stopped at target                                                                                |
| 263           | 0x107         | 40264         | Present Current     | 2               | 0             | RO     | –           | 6.5 mA         | Maximum measurable current: 500 × 6.5 mA = 3250 mA                                                             |

### **2.5 Factory Parameters** <a href="#block-345d4c79856d8042bfd4c60d2c6fdc40" id="block-345d4c79856d8042bfd4c60d2c6fdc40"></a>

| Address (DEC) | Address (HEX) | Address (PLC) | Function Name               | Number of Bytes | Initial Value | Access  | Value Range                  | Unit            | Description                                                                                 |
| ------------- | ------------- | ------------- | --------------------------- | --------------- | ------------- | ------- | ---------------------------- | --------------- | ------------------------------------------------------------------------------------------- |
| 384           | 0x180         | 40385         | Motion Detection Threshold  | 2               | –             | Default | –                            |                 | Servo factory default parameter                                                             |
| 385           | 0x181         | 40386         | D Control Time              | 2               | –             | Default | –                            |                 | Servo factory default parameter                                                             |
| 386           | 0x182         | 40387         | Maximum Speed Limit         | 2               | –             | Default | 0 \~ 32767                   | 0.732 RPM       | Servo factory default parameter                                                             |
| 387           | 0x183         | 40388         | H-Bridge Dead Time          | 2               | –             | Default | –                            |                 | Servo factory default parameter                                                             |
| 388           | 0x184         | 40389         | Acceleration Limit          | 2               | –             | Default | 0 \~ 65535                   | 8.79 degrees/s² | Servo factory default parameter                                                             |
| 389           | 0x185         | 40390         | Startup Torque              | 2               | –             | Default | 0 \~ 1000                    | 0.1 %           | Minimum output startup torque; 1000 = 100% stall torque                                     |
| 390           | 0x186         | 40391         | Clockwise Dead Zone         | 2               | –             | Default | 0 \~ 32                      | 0.0879 degrees  |                                                                                             |
| 391           | 0x187         | 40392         | Counterclockwise Dead Zone  | 2               | –             | Default | 0 \~ 32                      | 0.0879 degrees  |                                                                                             |
| 392           | 0x188         | 40393         | Phase                       | 2               | –             | Default | 0 \~ 255                     |                 | Special function byte; should not be modified unless necessary; see special byte definition |
| 393           | 0x189         | 40394         | Protection Switch           | 2               | –             | Default | 0 \~ 255                     |                 | Bit=1 enables corresponding protection; Bit=0 disables; see special byte definition         |
| 394           | 0x18A         | 40395         | LED Alarm Condition         | 2               | –             | Default | 0 \~ 255                     |                 | Bit=1 enables LED alarm; Bit=0 disables; see special byte definition                        |
| 395           | 0x18B         | 40396         | Maximum Temperature Limit   | 2               | –             | Default | 0 \~ 100                     | °C              | Maximum operating temperature limit (e.g., 70°C)                                            |
| 396           | 0x18C         | 40397         | Maximum Input Voltage       | 2               | –             | Default | Minimum input voltage \~ 360 | 0.1 V           | e.g., 80 = 8.0 V                                                                            |
| 397           | 0x18D         | 40398         | Minimum Input Voltage       | 2               | –             | Default | 0 \~ Maximum input voltage   | 0.1 V           | e.g., 40 = 4.0 V                                                                            |
| 398           | 0x18E         | 40400         | Overload Current            | 2               | –             | Default | 0 \~ 511                     | 6.5 mA          | Servo overload protection current                                                           |
| 399           | 0x18F         | 40401         | Overcurrent Protection Time | 2               | –             | Default | 0 \~ 5000                    | 1 ms            | Maximum duration exceeding overload current                                                 |
| 400           | 0x190         | 40402         | Protection Torque           | 2               | –             | Default | 0 \~ 1000                    | 0.1 %           | Output torque during overload protection; e.g., 200 = 20%                                   |
| 401           | 0x191         | 40403         | Overload Torque Threshold   | 2               | –             | Default | 0 \~ 1000                    | 0.1 %           | Torque threshold to trigger overload protection                                             |
| 402           | 0x192         | 40404         | Overload Protection Time    | 2               | –             | Default | 0 \~ 5000                    | 1 ms            | Maximum time torque exceeds overload threshold                                              |
| 403           | 0x193         | 40405         | Angular Resolution          | 2               | 1             | Default | 1 \~ 128                     |                 | Amplification factor of minimum sensor resolution; affects control range                    |
| 404           | 0x194         | 40406         | Default Torque Limit        | 2               | 1000          | Default | 0 \~ 1000                    | 0.1 %           | Power-on default torque limit                                                               |
| 405           | 0x195         | 40407         | Default Acceleration        | 2               | –             | Default | 0 \~ 65535                   | 8.79 degrees/s² | Power-on default acceleration                                                               |
| 406           | 0x196         | 40408         | Default Speed               | 2               | –             | Default | 0 \~ 32767                   | 0.732 RPM       | Power-on default speed                                                                      |

## **3. Special Byte Description** <a href="#block-345d4c79856d80469d22eaf7ef7a5918" id="block-345d4c79856d80469d22eaf7ef7a5918"></a>

### **3.1 Servo Phase** <a href="#block-345d4c79856d8099808af1855d6070b2" id="block-345d4c79856d8099808af1855d6070b2"></a>

**Bit number / bit weight: description**

* BIT0 (1): driver direction phase; (0) forward, (1) reverse
* BIT1 (2): driver bridge mode; (0) brushless, (1) brushed, effective after reboot
* BIT2 (4): torque auto switch; (0) auto enable, (1) command enable, firmware >= 20.9
* BIT3 (8): status auto reset; (0) auto reset, (1) command reset, firmware >= 20.9
* BIT4 (16): angle feedback mode; (0) single-turn angle feedback, (1) full-range angle feedback
* BIT5 (32): ----
* BIT6 (64): PWM frequency; (0) 24 kHz, (1) 16 kHz
* BIT7 (128): position feedback direction phase; (0) forward, (1) reverse

💡

**Note:**&#x49;f multiple bits are set simultaneously, the servo phase value equals the sum of all bit values.

**For example:** If the original phase value is 0 and reverse operation is required, the phase value is 128 + 1 = 129.

### **3.2 Servo Status** <a href="#block-345d4c79856d80ab82d5cf1f364a605d" id="block-345d4c79856d80ab82d5cf1f364a605d"></a>

**Servo status: 0 indicates normal, 1 indicates abnormal**

**Bit number / bit weight: description**

* BIT0 (1): voltage status
* BIT1 (2): magnetic encoder status
* BIT2 (4): temperature status
* BIT3 (8): current status
* BIT4 (16): torque status: 0 indicates torque off, 1 indicates torque on
* BIT5 (32): load status

💡

**Note:**&#x49;f multiple statuses occur simultaneously, the servo status value equals the sum of all bit values.

**For example:**&#x76;oltage over/under-voltage and servo overheat, then the servo status value is 4 + 1 = 5.

### **3.3 Protection Switch** <a href="#block-345d4c79856d80c38408e69e1aa601c6" id="block-345d4c79856d80c38408e69e1aa601c6"></a>

**Unload condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage protection
* BIT1 (2): magnetic encoder protection
* BIT2 (4): overheat protection
* BIT3 (8): overcurrent protection
* BIT4 (16): ----
* BIT5 (32): load overload

💡

**Note:**&#x49;f multiple bits are set, the unload condition value equals the sum of all bit values.

**For example:**&#x76;oltage protection and overheat protection enabled at the same time, then the unload condition value is 4 + 1 = 5.

### **3.4 LED Alarm Condition** <a href="#block-345d4c79856d805e8131f5246c2798bb" id="block-345d4c79856d805e8131f5246c2798bb"></a>

**LED alarm condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage alarm
* BIT1 (2): magnetic encoder alarm
* BIT2 (4): overheat alarm
* BIT3 (8): overcurrent alarm
* BIT4 (16): ----
* BIT5 (32): load overload alarm

💡

**Note:**&#x49;f multiple bits are set simultaneously, the LED alarm condition value equals the sum of all bit values.

**For example:** voltage alarm and overheat alarm enabled at the same time, then the alarm condition value is 4 + 1 = 5.

### **3.5 Fault Reset** <a href="#block-345d4c79856d80439738caf8350c9888" id="block-345d4c79856d80439738caf8350c9888"></a>

**Fault reset: 0 invalid, 1 reset**

**Bit number / bit weight: description**

* BIT0 (1): reset overload fault; automatic reset enabled, reversing target position and disabling torque switch can also clear the fault
* BIT1 (2): reset overcurrent fault; automatic reset enabled, reversing target position and disabling torque switch can also clear the fault
* BIT2 (4): set midpoint; set current position to 2048 midpoint
* BIT3 (8): ----
* BIT4 (16): ----
* BIT5 (32): reset overvoltage/undervoltage; when voltage returns to normal, write 32 to reset status; automatic reset enabled when voltage is normal
* BIT6 (64): reset overheat status; when temperature returns to normal, write 64 to reset status; automatic reset enabled when temperature is normal
* BIT7 (128): reset magnetic encoder status; when encoder is connected normally, write 128 to reset status; automatic reset enabled when encoder is normal

💡

**Note:**&#x49;f multiple bits are set, the fault reset value equals the sum of all bit values.

**For example:** If overload fault reset and overcurrent fault reset are both triggered, the value is 1 + 2 = 3.
