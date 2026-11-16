# FEETECH HLS Servo – Memory Table Analysis

> FEETECH HLS Servo – Memory Table Analysis

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Servo Communication Protocol** <a href="#block-340d4c79856d81398120d765ac93af78" id="block-340d4c79856d81398120d765ac93af78"></a>

The servo uses the FT-SCS custom protocol. The factory default serial configuration is as follows: baud rate 1 Mbps, 8 data bits, no parity, and 1 stop bit.

The baud rate is configurable from 38,400 to 1 Mbps. The default communication address (station ID) is 1.

## **2. Servo Memory Table Definition** <a href="#block-344d4c79856d80afacb7f29d0a33924c" id="block-344d4c79856d80afacb7f29d0a33924c"></a>

If the function address uses two bytes of data, the low byte is stored at the lower address, and the high byte is stored at the higher address.

### **2.1 Version Information** <a href="#block-344d4c79856d80cc871ae77351a4d48b" id="block-344d4c79856d80cc871ae77351a4d48b"></a>

| Address (DEC) | Address (HEX) | Function Name                 | Number of Bytes | Initial Value | Access | Value Range | Unit | Description                                 |
| ------------- | ------------- | ----------------------------- | --------------- | ------------- | ------ | ----------- | ---- | ------------------------------------------- |
| 0             | 0x00          | Firmware Major Version Number | 1               | 3             | RO     |             |      |                                             |
| 1             | 0x01          | Firmware Minor Version Number | 1               | –             | RO     | 40–59       |      |                                             |
| 2             | 0x02          | END                           | 1               | 0             | RO     |             |      | 0 indicates little-endian storage structure |
| 3             | 0x03          | Servo Major Version Number    | 1               | 10            | RO     |             |      |                                             |
| 4             | 0x04          | Servo Minor Version Number    | 1               | –             | RO     |             |      |                                             |

### **2.2 EPROM Configuration** <a href="#block-344d4c79856d80569f5cf8eba2b42ed4" id="block-344d4c79856d80569f5cf8eba2b42ed4"></a>

| Address (DEC) | Address (HEX) | Function Name                        | Number of Bytes | Initial Value | Access | Value Range   | Unit          | Description                                                                                                     |
| ------------- | ------------- | ------------------------------------ | --------------- | ------------- | ------ | ------------- | ------------- | --------------------------------------------------------------------------------------------------------------- |
| 5             | 0x05          | Servo ID (Main ID)                   | 1               | 1             | RW     | 0 \~ 253      | No.           | Unique master ID on the bus (primary identifier)                                                                |
| 6             | 0x06          | Baud Rate                            | 1               | 0             | RW     | 0 \~ 7        |               | 0–7 correspond to: 1000000 (0), 500000 (1), 250000 (2), 128000 (3), 115200 (4), 76800 (5), 57600 (6), 38400 (7) |
| 7             | 0x07          | Sub ID                               | 1               | 0             | RW     | 0 \~ 253      | No.           | Secondary ID (used only for write instructions)                                                                 |
| 8             | 0x08          | Response Status Level                | 1               | 1             | RW     | 0 \~ 1        |               | 0: No response except READ and PING; 1: Respond to all instructions                                             |
| 9             | 0x09          | Minimum Angle Limit                  | 2               | 0             | RW     | 0 \~ 4094     | 0.087 degrees | 0 when multi-turn absolute position control is used                                                             |
| 11            | 0x0B          | Maximum Angle Limit                  | 2               | 4095          | RW     | 1 \~ 4095     | 0.087 degrees | 0 when multi-turn absolute position control is used                                                             |
| 13            | 0x0D          | Maximum Temperature Limit            | 1               | 70            | RW     | 0 \~ 100      | °C            |                                                                                                                 |
| 14            | 0x0E          | Maximum Input Voltage                | 1               | -             | RW     | 0 \~ 254      | 0.1V          |                                                                                                                 |
| 15            | 0x0F          | Minimum Input Voltage                | 1               | 40            | RW     | 0 \~ 254      | 0.1V          |                                                                                                                 |
| 16            | 0x10          | Maximum Torque                       | 2               | 980           | RW     | 0 \~ 1000     | 0.1%          | Assigned to address 48 (Torque Limit) at power-on                                                               |
| 18            | 0x12          | Phase                                | 1               | -             | RW     | 0 \~ 254      |               | Special function byte, do not modify unless required                                                            |
| 19            | 0x13          | Unload Condition                     | 1               | -             | RW     | 0 \~ 254      |               | Bit=1 enables protection; Bit=0 disables protection                                                             |
| 20            | 0x14          | LED Alarm Condition                  | 1               | -             | RW     | 0 \~ 254      |               | Bit=1 enables alarm flashing; Bit=0 disables                                                                    |
| 21            | 0x15          | Position Loop Proportional Gain (Kp) | 1               | -             | RW     | 0 \~ 254      |               | Assigned to address 50 at power-on                                                                              |
| 22            | 0x16          | Position Loop Derivative Gain (Kd)   | 1               | -             | RW     | 0 \~ 254      |               | Assigned to address 51 at power-on                                                                              |
| 23            | 0x17          | Position Loop Integral Gain (Ki)     | 1               | 0             | RW     | 0 \~ 254      |               | Assigned to address 52 at power-on                                                                              |
| 24            | 0x18          | Minimum Starting Torque              | 1               | -             | RW     | 0 \~ 254      | 0.1%          | Minimum startup torque of the servo                                                                             |
| 25            | 0x19          | Integral Limit Value                 | 1               | 0             | RW     | 0 \~ 254      |               | Max integral = value × 4; 0 disables; valid in mode 0 and 4                                                     |
| 26            | 0x1A          | Positive Dead Zone                   | 1               | 1             | RW     | 0 \~ 16       | 0.087 degrees | Minimum unit = minimum resolvable angle                                                                         |
| 27            | 0x1B          | Negative Dead Zone                   | 1               | 1             | RW     | 0 \~ 16       | 0.087 degrees | Minimum unit = minimum resolvable angle                                                                         |
| 28            | 0x1C          | Protection Current                   | 2               | -             | RW     | 0 \~ 2047     | 6.5mA         | Assigned to address 44 (Target Current) at power-on                                                             |
| 30            | 0x1E          | Angular Resolution                   | 1               | 1             | RW     | 1 \~ 128      |               | Amplification factor of sensor resolution                                                                       |
| 31            | 0x1F          | Position Offset                      | 2               | 0             | RW     | -4095 \~ 4095 | 0.087 degrees | Bit15 indicates direction                                                                                       |
| 33            | 0x21          | Operating Mode                       | 1               | 0             | RW     | 0 \~ 3        |               | 0: Position mode; 1: Constant speed mode; 2: Constant current mode; 3: PWM open-loop mode                       |
| 34            | 0x22          | Current Loop Proportional Gain (Kp)  | 1               | -             | RW     |               |               |                                                                                                                 |
| 35            | 0x23          | Current Loop Integral Gain (Ki)      | 1               | -             | RW     |               |               |                                                                                                                 |
| 36            | 0x24          | Undefined                            | 1               | -             | RW     | -             | -             | -                                                                                                               |
| 37            | 0x25          | Velocity Loop Proportional Gain (Kp) | 1               | -             | RW     | 0 \~ 254      |               | Used in constant speed mode (Mode 1)                                                                            |
| 38            | 0x26          | Overcurrent Protection Time          | 1               | 200           | RW     | 0 \~ 254      | 10ms          |                                                                                                                 |
| 39            | 0x27          | Velocity Loop Integral Gain (Ki)     | 1               | -             | RW     | 0 \~ 254      |               | Used in constant speed mode (Mode 1)                                                                            |

### **2.3 SRAM Control** <a href="#block-344d4c79856d80c0a9abc48333c59b08" id="block-344d4c79856d80c0a9abc48333c59b08"></a>

| Address (DEC) | Address (HEX) | Function Name   | Number of Bytes | Initial Value           | Access | Value Range     | Unit          | Description                                                              |
| ------------- | ------------- | --------------- | --------------- | ----------------------- | ------ | --------------- | ------------- | ------------------------------------------------------------------------ |
| 40            | 0x28          | Torque Switch   | 1               | 0                       | RW     | 0 \~ 2          |               | 0: Disable torque; 1: Enable torque; 2: Damping mode                     |
| 41            | 0x29          | Acceleration    | 1               | 0                       | RW     | 0 \~ 254        | 8.7°/s²       | 0 indicates maximum acceleration                                         |
| 42            | 0x2A          | Target Position | 2               | 0                       | RW     | -32767 \~ 32767 | 0.087 degrees | Bit15 is direction bit                                                   |
| 44            | 0x2C          | Target Current  | 2               | Protection Current (28) | RW     | -2047 \~ 2047   | 6.5mA         | Bit15 is direction (mode 2); PWM mode uses -1000\~1000 (Bit10 direction) |
| 46            | 0x2E          | Operating Speed | 2               | Max factory speed       | RW     | -32767 \~ 32767 | 0.732 RPM     | 0 = stop; Bit15 direction                                                |
| 48            | 0x30          | Torque Limit    | 2               | Maximum Torque (16)     | RW     | 0 \~ 1000       | 0.1%          | Stall torque control                                                     |
| 50            | 0x32          | Kp              | 1               | From EPROM (21)         | RW     | 0 \~ 254        |               | Position loop proportional gain (1/8)                                    |
| 51            | 0x33          | Kd              | 1               | From EPROM (22)         | RW     | 0 \~ 254        |               | Position loop derivative gain (1/4)                                      |
| 52            | 0x34          | Ki              | 1               | From EPROM (23)         | RW     | 0 \~ 254        |               | Position loop integral gain                                              |
| 53            | 0x35          | Undefined       | 1               | -                       | RW     | -               | -             |                                                                          |
| 54            | 0x36          | Undefined       | 1               | -                       | RW     | -               | -             |                                                                          |
| 55            | 0x37          | Lock Flag       | 1               | 1                       | RW     | 0 \~ 1          |               | 0: Disable lock (saved after power-off); 1: Enable lock                  |

### 2.4 **SRAM Feedback** <a href="#block-344d4c79856d80a1bc6ed7646bec098b" id="block-344d4c79856d80a1bc6ed7646bec098b"></a>

| Address (DEC) | Address (HEX) | Function Name       | Number of Bytes | Initial Value | Access | Value Range | Unit          | Description                        |
| ------------- | ------------- | ------------------- | --------------- | ------------- | ------ | ----------- | ------------- | ---------------------------------- |
| 56            | 0x38          | Present Position    | 2               | -             | R      | -           | 0.087 degrees | Bit15 is direction                 |
| 58            | 0x3A          | Present Speed       | 2               | -             | R      | -           | 0.732 RPM     | Bit15 is direction                 |
| 60            | 0x3C          | Present Load        | 2               | -             | R      | -           | 0.1%          | PWM duty cycle, Bit10 direction    |
| 62            | 0x3E          | Present Voltage     | 1               | -             | R      | -           | 0.1V          |                                    |
| 63            | 0x3F          | Present Temperature | 1               | -             | R      | -           | °C            |                                    |
| 64            | 0x40          | Async Write Flag    | 1               | 0             | R      | -           |               | Used in async write                |
| 65            | 0x41          | Servo Status        | 1               | 0             | R      | -           |               | Bit flags indicate errors          |
| 66            | 0x42          | Moving Flag         | 1               | 0             | R      | -           |               | BIT0: moving; BIT1: reached target |
| 67            | 0x43          | Target Position     | 2               | -             | R      | -           | 0.087 degrees |                                    |
| 69            | 0x45          | Present Current     | 2               | -             | R      | -           | 6.5mA         | Phase current                      |
| 71            | 0x47          | Undefined           | 2               | -             | R      | -           | -             |                                    |
| 73            | 0x49          | Current Offset      | 2               | -             | R      | -           | -             | Zero offset                        |

### **2.5 Factory Parameters** <a href="#block-344d4c79856d80919ee9e2502e66e031" id="block-344d4c79856d80919ee9e2502e66e031"></a>

| Address (DEC) | Address (HEX) | Function Name           | Number of Bytes | Initial Value | Access | Value Range | Unit | Description                                                                      |
| ------------- | ------------- | ----------------------- | --------------- | ------------- | ------ | ----------- | ---- | -------------------------------------------------------------------------------- |
| 77            | 0x4D          | vFk(\*10)               | 1               | –             | R      | –           | –    | Internal factory parameter (scaled ×10), used for velocity/feedback compensation |
| 78            | 0x4E          | vKgI                    | 1               | –             | R      | –           | –    | Internal velocity loop integral-related gain parameter                           |
| 79            | 0x4F          | pFk(\*10)               | 1               | –             | R      | –           | –    | Internal position-related factory parameter (scaled ×10)                         |
| 80            | 0x50          | Motion Speed Threshold  | 1               | –             | R      | –           | –    | Threshold for determining whether the servo is in motion                         |
| 81            | 0x51          | DTs (ms)                | 1               | –             | R      | –           | ms   | Control cycle timing parameter                                                   |
| 82            | 0x52          | eFk(\*10)               | 1               | –             | R      | –           | –    | Error/estimation compensation factor (scaled ×10)                                |
| 83            | 0x53          | Vk (ms)                 | 1               | –             | R      | –           | ms   | Internal timing constant for velocity control                                    |
| 84            | 0x54          | Maximum Speed Limit     | 1               | –             | R      | –           | –    | Factory-defined maximum allowable speed                                          |
| 85            | 0x55          | Acceleration Limit      | 1               | –             | R      | –           | –    | Factory-defined maximum acceleration limit                                       |
| 86            | 0x56          | Acceleration Multiplier | 1               | –             | R      | –           | –    | Scaling factor for acceleration behavior                                         |

## **3. Special Byte Description** <a href="#block-344d4c79856d803c9c71fa720644a5b5" id="block-344d4c79856d803c9c71fa720644a5b5"></a>

### **3.1 Servo Phase** <a href="#block-344d4c79856d800a945df92b57403ae9" id="block-344d4c79856d800a945df92b57403ae9"></a>

**Bit number / bit weight: description**

* BIT0 (1): servo phase (firmware version <= 3.41), magnetic encoder support (0: AS5600, 1: MT6701, firmware version >= 3.44)
* BIT1 (2): current feedback direction phase; (0) forward, (1) reverse
* BIT2 (4): driver bridge direction phase; (0) forward, (1) reverse
* BIT3 (8): speed direction phase (firmware version <= 3.41)
* BIT4 (16): angle feedback mode; (0) single-turn angle feedback, (1) multi-turn angle feedback
* BIT5 (32): driver bridge configuration, (0) independent H-bridge, (1) integrated H-bridge
* BIT6 (64): PWM frequency, (0) 24kHz, (1) 16kHz
* BIT7 (128): position feedback direction phase, (0) forward, (1) reverse

💡

**Note**: If multiple bits are set simultaneously, the servo phase value equals the sum of all bit values.

**For example**: if the original phase value is 0, and reverse operation is required, the phase value is 128 + 4 + 2 = 134.

### **3.2 Servo Status** <a href="#block-344d4c79856d8081a41bd2e26dae8679" id="block-344d4c79856d8081a41bd2e26dae8679"></a>

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

**Note:** If multiple statuses occur simultaneously, the servo status value equals the sum of all bit values.

**For example:** voltage over/under-voltage and servo overheat, then the servo status value is 4 + 1 = 5.

### **3.3 Unload Condition** <a href="#block-344d4c79856d80b88988fb0b63bc995e" id="block-344d4c79856d80b88988fb0b63bc995e"></a>

**Unload condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage protection
* BIT1 (2): magnetic encoder protection
* BIT2 (4): overheat protection
* BIT3 (8): overcurrent protection
* BIT4 (16): ----
* BIT5 (32): ----
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:** If multiple bits are set, the unload condition value equals the sum of all bit values.

**For example:** voltage protection and overheat protection enabled at the same time, then the unload condition value is 4 + 1 = 5.

### **3.4 LED Alarm Condition** <a href="#block-344d4c79856d8078b25aeadf288e58e4" id="block-344d4c79856d8078b25aeadf288e58e4"></a>

**Alarm condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): voltage alarm
* BIT1 (2): magnetic encoder alarm
* BIT2 (4): overheat alarm
* BIT3 (8): overcurrent alarm
* BIT4 (16): ----
* BIT5 (32): ----
* BIT6 (64): ----
* BIT7 (128): ----

💡

**Note:** If multiple bits are set simultaneously, the alarm condition value equals the sum of all bit values.

**For example:** voltage alarm and overheat alarm enabled at the same time, then the unload condition value is 4 + 1 = 5.
