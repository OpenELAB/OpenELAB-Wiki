# FEETECH SMS Servo - Memory Table Analysis

> FEETECH SMS Servo - Memory Table Analysis

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Servo Communication Protocol** <a href="#block-341d4c79856d8175aadfeac7e1bb6550" id="block-341d4c79856d8175aadfeac7e1bb6550"></a>

The servo uses the FT-SCS custom protocol. The default serial port configuration at the factory is as follows: the baud rate of the SMS servo is 115200 by default, and it uses RS485 bus communication.

The configurable baud rate range is 38400 to 1 Mbps. The default communication address (station number) is 1.

## **2. Servo Memory Table Definition** <a href="#block-341d4c79856d8059a88fd2714a6f4157" id="block-341d4c79856d8059a88fd2714a6f4157"></a>

If the function address uses two bytes of data, the low byte is stored at the lower address, and the high byte is stored at the higher address.

### **2.1 Version Information** <a href="#block-341d4c79856d81b1ad28f83b28641531" id="block-341d4c79856d81b1ad28f83b28641531"></a>

| Address (DEC) | Address (HEX) | Function Name                 | Number of Bytes | Initial Value | Access | Value Range | Unit | Description                                 |
| ------------- | ------------- | ----------------------------- | --------------- | ------------- | ------ | ----------- | ---- | ------------------------------------------- |
| 0             | 0x00          | Firmware Major Version Number | 1               | -             | RO     |             |      |                                             |
| 1             | 0x01          | Firmware Minor Version Number | 1               | -             | RO     |             |      |                                             |
| 2             | 0x02          | END                           | 1               | 0             | RO     |             |      | 0 indicates little-endian storage structure |
| 3             | 0x03          | Servo Major Version Number    | 1               | -             | RO     |             |      |                                             |
| 4             | 0x04          | Servo Minor Version Number    | 1               | -             | RO     |             |      |                                             |

### **2.2 EPROM Configuration** <a href="#block-341d4c79856d80ee856cd44caf3f0543" id="block-341d4c79856d80ee856cd44caf3f0543"></a>

| Address (DEC) | Address (HEX) | Function Name                               | Number of Bytes | Initial Value | Access | Value Range | Unit          | Description                                                                                                                                                                       |
| ------------- | ------------- | ------------------------------------------- | --------------- | ------------- | ------ | ----------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 5             | 0x05          | Servo ID                                    | 1               | 1             | RW     | 0 \~ 253    | No.           | Unique Master ID on the Bus                                                                                                                                                       |
| 6             | 0x06          | Baud Rate                                   | 1               | 0             | RW     | 0 \~ 7      |               | 0–7 respectively represent the following baud rates: 1000000 (0), 500000 (1), 250000 (2), 128000 (3), 115200 (4), 76800 (5), 57600 (6), 38400 (7).                                |
| 7             | 0x07          | Response Return Delay                       | 1               | 0             | RW     | 0/50 \~ 253 | 2us           | The maximum configurable return delay is 254 × 2 = 508 μs. 0 indicates the minimum return delay. If the setting is below 50, it defaults to 50 (100 μs).                          |
| 8             | 0x08          | Response Status Level                       | 1               | 1             | RW     | 0 \~ 1      |               | 0: No response packet is returned for any instruction except read instructions and PING instructions. 1: A response packet is returned for all instructions.                      |
| 9             | 0x09          | Minimum Angle Limit                         | 2               | 0             | RW     | 0 \~ 4094   | 0.087 degrees | This value is 0 when multi-turn absolute position control is used.                                                                                                                |
| 11            | 0x0B          | Maximum Angle Limit                         | 2               | 4095          | RW     | 1 \~ 4095   | 0.087 degrees | This value is 0 when multi-turn absolute position control is used.                                                                                                                |
| 13            | 0x0D          | Maximum Temperature Limit                   | 1               | 70            | RW     | 0 \~ 100    | °C            |                                                                                                                                                                                   |
| 14            | 0x0E          | Maximum Input Voltage                       | 1               | -             | RW     | 0 \~ 254    | 0.1V          |                                                                                                                                                                                   |
| 15            | 0x0F          | Minimum Input Voltage                       | 1               | 40            | RW     | 0 \~ 254    | 0.1V          |                                                                                                                                                                                   |
| 16            | 0x10          | Maximum Torque                              | 2               | 1000          | RW     | 0 \~ 1000   | 0.1%          | Torque limit is assigned to address 48 at power-on.                                                                                                                               |
| 18            | 0x12          | Phase                                       | 1               | -             | RW     | 0 \~ 254    |               | Special function byte. Do not modify unless specifically required.                                                                                                                |
| 19            | 0x13          | Unload Condition                            | 1               | -             | RW     | 0 \~ 254    |               | Setting the corresponding bit to 1 enables the respective protection, and setting it to 0 disables the respective protection.                                                     |
| 20            | 0x14          | LED Alarm Condition                         | 1               | -             | RW     | 0 \~ 254    |               | Setting the corresponding bit to 1 enables the flashing alarm, and setting it to 0 disables the flashing alarm.                                                                   |
| 21            | 0x15          | Position Loop Proportional Gain (Kp)        | 1               | -             | RW     | 0 \~ 254    |               | Proportional gain for motor control (1/4)                                                                                                                                         |
| 22            | 0x16          | Position Loop Derivative Gain (Kd)          | 1               | -             | RW     | 0 \~ 254    |               | Derivative gain for motor control (1/8)                                                                                                                                           |
| 23            | 0x17          | Position Loop Integral Gain (Ki)            | 1               | 0             | RW     | 0 \~ 254    |               | Integral gain for motor control                                                                                                                                                   |
| 24            | 0x18          | Minimum Starting Force                      | 1               | -             | RW     | 0 \~ 254    | 0.1%          | Set the minimum starting torque of the servo                                                                                                                                      |
| 25            | 0x19          | Integral Limit Value                        | 1               | 0             | RW     | 0 \~ 254    |               | Maximum integral value = Integral limit value × 4. 0 disables the integral limit function. This setting takes effect in position mode 0 and mode 4.                               |
| 26            | 0x1A          | Positive Dead Zone                          | 1               | 1             | RW     | 0 \~ 16     | 0.087 degrees | The minimum unit is one minimum resolvable angle.                                                                                                                                 |
| 27            | 0x1B          | Negative Dead Zone                          | 1               | 1             | RW     | 0 \~ 16     | 0.087 degrees | The minimum unit is one minimum resolvable angle.                                                                                                                                 |
| 28            | 0x1C          | Protection Current                          | 2               | 511           | RW     | 0 \~ 2047   | 6.5mA         | The maximum configurable current is 500 × 6.5 mA = 3250 mA.                                                                                                                       |
| 30            | 0x1E          | Angular Resolution                          | 1               | 1             | RW     | 1 \~ 128    |               | Amplification Factor of the Sensor’s Minimum Resolvable Angle                                                                                                                     |
| 31            | 0x1F          | Position Offset                             | 2               | 0             | RW     | 0 \~ 8191   | 0.087 degrees | 0 to 2047 represent 0 to 2047; 2048 to 4095 represent 0 to -2047; 4096 to 6143 represent 2048 to 4095; 6144 to 8191 represent -2048 to -4095.                                     |
| 33            | 0x21          | Operating Mode                              | 1               | 0             | RW     | 0 \~ 2      |               | 0: Position servo mode; 1: Constant speed mode; 2: PWM open-loop speed control mode; 3: Step mode                                                                                 |
| 34            | 0x22          | Holding Torque                              | 1               | 20            | RW     | 0 \~ 254    | 1%            | The torque output after entering overload protection. For example, a setting of 20 means 20% of the maximum torque.                                                               |
| 35            | 0x23          | Protection Time                             | 1               | 200           | RW     | 0 \~ 254    | 10ms          | The duration for which the current load output exceeds the overload torque is timed. For example, a setting of 200 means 2 seconds. The maximum configurable time is 2.5 seconds. |
| 36            | 0x24          | Overload Torque                             | 1               | 80            | RW     | 0 \~ 254    | 1%            | The maximum torque threshold that starts the overload protection timing. For example, a setting of 80 means 80% of the maximum torque.                                            |
| 37            | 0x25          | Velocity Closed-Loop Proportional Gain (Kp) | 1               | -             | RW     | 0 \~ 254    |               | Velocity loop proportional gain in constant speed mode (Mode 1)                                                                                                                   |
| 38            | 0x26          | Overcurrent Protection Time                 | 1               | 200           | RW     | 0 \~ 254    | 10ms          | The maximum configurable time is 254 × 10 ms = 2540 ms.                                                                                                                           |
| 39            | 0x27          | Velocity Closed-Loop Integral Gain (Ki)     | 1               | -             | RW     | 0 \~ 254    |               | Velocity loop integral gain in constant speed mode (Mode 1)                                                                                                                       |

### **2.3 SRAM Control** <a href="#block-341d4c79856d80a88783fc09f471ae47" id="block-341d4c79856d80a88783fc09f471ae47"></a>

| Address (DEC) | Address (HEX) | Function Name       | Number of Bytes | Initial Value                                     | Access | Value Range     | Unit               | Description                                                                                                                                                                                                                                                                                                                                                                  |
| ------------- | ------------- | ------------------- | --------------- | ------------------------------------------------- | ------ | --------------- | ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 40            | 0x28          | Torque Switch       | 1               | 0                                                 | RW     | 0 \~ 2          | -                  | Write 0: Disable torque output; write 1: Enable torque output; write 128: Calibrate any current position to 2048.                                                                                                                                                                                                                                                            |
| 41            | 0x29          | Acceleration        | 1               | 0                                                 | RW     | 0 \~ 254        | 8.7°/s²            | Servo acceleration/deceleration. 0 indicates maximum acceleration.                                                                                                                                                                                                                                                                                                           |
| 42            | 0x2A          | Target Position     | 2               | 0                                                 | RW     | -32767 \~ 32767 | 0.087 degrees      | Absolute position control mode. The maximum value corresponds to the maximum effective angle. Bit 15 is the direction bit.                                                                                                                                                                                                                                                   |
| 44            | 0x2C          | PWM Open-Loop Speed | 2               | 1000                                              | RW     | 0\~1000         | 0.1%               | Effective in PWM open-loop speed control mode. Bit 10 is the direction bit.                                                                                                                                                                                                                                                                                                  |
| 46            | 0x2E          | Operating Speed     | 2               | Default maximum speed of the servo at the factory | RW     | -32767 \~ 32767 | 0.732RPM/0.0146RPM | Sets the maximum operating speed of the motor. Bit 15 is the direction bit. A speed value of 0 defaults to the maximum speed, while a setting of 0 via the phase configuration means stop. The speed unit can be configured via the phase setting, offering two options: 0.732 RPM or 0.0146 RPM. When the speed unit is set to 0.0146 RPM, its precision remains 0.732 RPM. |
| 48            | 0x30          | Torque Limit        | 2               | Maximum torque (16). Default value: 1000.         | RW     | 0 \~ 1000       | 0.1%               | The user can programmatically modify this value to control the stall torque output.                                                                                                                                                                                                                                                                                          |
| 50\~54        | 0x32\~0x36    | Undefined           | 1               | -                                                 | -      | -               | -                  | -                                                                                                                                                                                                                                                                                                                                                                            |
| 55            | 0x37          | Lock Flag           | 1               | 1                                                 | RW     | 0 \~ 1          | -                  | Write 0 to disable the write lock. Values written to EPROM addresses are saved after power-off. Write 1 to enable the write lock. Values written to EPROM addresses are not saved after power-off.                                                                                                                                                                           |

### 2.4 **SRAM Feedback** <a href="#block-341d4c79856d806b9fbcf1c0e7126b5b" id="block-341d4c79856d806b9fbcf1c0e7126b5b"></a>

| Address (DEC) | Address (HEX) | Function Name           | Number of Bytes | Initial Value | Access | Value Range     | Unit               | Description                                                                                                                                                                                                               |
| ------------- | ------------- | ----------------------- | --------------- | ------------- | ------ | --------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 56            | 0x38          | Current Position        | 2               | -             | RO     | 0 \~ 2          | 0.087 degrees      | Feedback of the servo’s current absolute position. Bit 15 is the direction bit. In step mode (Mode 3), the step difference between the current position and the target position is returned. Bit 15 is the direction bit. |
| 58            | 0x3A          | Current Speed           | 2               | -             | RO     | 0 \~ 254        | 0.732RPM/0.0146RPM | Feedback of the current motor speed. The speed unit is configured via the phase setting. Bit 15 is the direction bit.                                                                                                     |
| 60            | 0x3C          | Current Load            | 2               | -             | RO     | -32767 \~ 32767 | 0.1%               | The current voltage duty cycle controlling the motor drive output. Bit 10 is the direction bit.                                                                                                                           |
| 62            | 0x3E          | Current Voltage         | 1               | -             | RO     | 0\~1000         | 0.1V               | Current Servo Operating Voltage                                                                                                                                                                                           |
| 63            | 0x3F          | Current Temperature     | 1               | -             | RO     | -32767 \~ 32767 | °C                 | Current Internal Operating Temperature of the Servo                                                                                                                                                                       |
| 64            | 0x40          | Asynchronous Write Flag | 1               | 0             | RO     | 0 \~ 1000       | -                  | Flag bit when using asynchronous write commands                                                                                                                                                                           |
| 65            | 0x41          | Servo Status            | 1               | 0             | RO     | -               | -                  | When the corresponding bit is set to 1, it indicates that the respective error has occurred.                                                                                                                              |
| 66            | 0x42          | Movement Flag           | 1               | 0             | RO     | 0 \~ 1          | -                  | The flag is 1 when the servo is moving, and 0 when the servo has reached the target and stopped. The flag remains 0 when the target position is not updated.                                                              |
| 67            | 0x43          | Target Position         | 2               | 0             | RO     | -               | 0.087 degrees      | Current Target Position                                                                                                                                                                                                   |
| 69            | 0x45          | Current Current         | 2               | -             | RO     | -               | 6.5mA              | Feedback of the current motor phase current                                                                                                                                                                               |
| 71            | 0x47          | Undefined               | 2               | -             | RO     | -               | -                  |                                                                                                                                                                                                                           |

### 3.5 **Factory Parameters** <a href="#block-341d4c79856d803eafede2e22c178693" id="block-341d4c79856d803eafede2e22c178693"></a>

| Address (DEC) | Address (HEX) | Function Name            | Number of Bytes | Initial Value | Access | Value Range | Unit | Description                                                                                                                                                                    |
| ------------- | ------------- | ------------------------ | --------------- | ------------- | ------ | ----------- | ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 80            | 0x50          | Movement Speed Threshold | 1               | -             | RO     | -           | -    |                                                                                                                                                                                |
| 81            | 0x51          | DTs(ms)                  | 1               | -             | RO     | -           | -    |                                                                                                                                                                                |
| 82            | 0x52          | Speed Unit Factor        | 1               | -             | RO     | -           | -    |                                                                                                                                                                                |
| 83            | 0x53          | Hts(ns)                  | 1               | -             | RO     | -           | -    | 20.83 ns. Valid for SMS servo firmware version 2.54 or higher. For other versions, keep it at 0.                                                                               |
| 84            | 0x54          | Maximum Speed Limit      | 1               | -             | RO     | -           | -    | Unit: 0.732 rpm                                                                                                                                                                |
| 85            | 0x55          | Acceleration Limit       | 1               | -             | RO     | -           | -    |                                                                                                                                                                                |
| 86            | 0x56          | Acceleration Multiplier  | 1               | -             | RO     | -           | -    | When the acceleration is 0, the acceleration multiplier takes effect. If both the acceleration and the acceleration multiplier are 0, the servo responds at the fastest speed. |

## **3. Special Byte Description** <a href="#block-341d4c79856d811ca207efca1a136132" id="block-341d4c79856d811ca207efca1a136132"></a>

### 3.1 **Servo Phase** <a href="#block-343d4c79856d80ac9e9cf645be2ab3b1" id="block-343d4c79856d80ac9e9cf645be2ab3b1"></a>

**Bit Count / Bit Weight Description**

* Bit 0 (1): Driver direction phase. (0) forward, (1) reverse.
* BIT1 (2): Bridge mode — 0 = brushless, 1 = brushed (restart)
* BIT2 (4): Speed unit — 0 = 0.732 RPM, 1 = 0.0146 RPM
* BIT3 (8): Speed mode — 0 = speed 0 = stop, 1 = speed 0 = max
* BIT4 (16): Angle feedback — 0 = single-turn, 1 = full angle
* BIT5 (32): Voltage sampling — 0 = 1.5K low, 1 = 1K high
* BIT6 (64): PWM frequency — 0 = 24 kHz, 1 = 16 kHz
* BIT7 (128): Position feedback direction — 0 = forward, 1 = reverse

💡

**Note:** If multiple bits are set simultaneously, the servo phase value is the sum of the individual bit values.

**For example:** if the original phase value is 0 and the servo is set to run in reverse, the phase value becomes 128 + 1 = 129.

### 3.2 **Servo Status** <a href="#block-343d4c79856d8060a3d4c314aa7d1283" id="block-343d4c79856d8060a3d4c314aa7d1283"></a>

**Servo status: 0 indicates normal, 1 indicates abnormal.**

**Bit Count / Bit Weight Description**

* BIT0 (1): Voltage status
* BIT1 (2): Magnetic encoder status
* BIT2 (4): Temperature status
* BIT3 (8): Current status
* BIT4 (16): Reserved
* BIT5 (32): Load status
* BIT6 (64): Reserved
* BIT7 (128): Reserved

💡

**Note:** Multiple statuses can be combined. The servo status value is the sum of the bit values of all active statuses.

**Example:** Overvoltage/undervoltage (1) + Overheating (4) = 5.

### 3.3 **Unload Condition** <a href="#block-343d4c79856d801ab042e704e123dc62" id="block-343d4c79856d801ab042e704e123dc62"></a>

**Unload condition — 0 = disabled, 1 = enabled**

**Bit Count / Bit Weight Description**

* BIT0 (1): Voltage protection
* BIT1 (2): Magnetic encoder protection
* BIT2 (4): Over-temperature protection
* BIT3 (8): Overcurrent protection
* BIT4 (16): Reserved
* BIT5 (32): Load overload
* BIT6 (64): Reserved
* BIT7 (128): Reserved

💡

**Note**: Multiple protection conditions can be combined. The unload condition value is the sum of the bit values of all enabled protections.

**Example:** Voltage protection (1) + Over-temperature protection (4) = 5.

### 3.4 **LED Alarm Condition** <a href="#block-343d4c79856d8017ab87da9943b9f871" id="block-343d4c79856d8017ab87da9943b9f871"></a>

**LED alarm condition — 0 = disabled, 1 = enabled**

**Bit Count / Bit Weight Description**

* BIT0 (1): Voltage alarm
* BIT1 (2): Magnetic encoder alarm
* BIT2 (4): Over-temperature alarm
* BIT3 (8): Overcurrent alarm
* BIT4 (16): Reserved
* BIT5 (32): Load overload alarm
* BIT6 (64): Reserved
* BIT7 (128): Reserved

💡

**Note**: Multiple alarm conditions can be combined. The LED alarm condition value is the sum of the bit values of all enabled alarms.

**Example:** Voltage alarm (1) + Over-temperature alarm (4) = 5.
