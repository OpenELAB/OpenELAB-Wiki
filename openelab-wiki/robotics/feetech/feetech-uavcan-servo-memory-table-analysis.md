# FEETECH UAVCAN Servo – Memory Table Analysis

> **Magnetic Encoder UAVCAN Servo**

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Communication Protocol** <a href="#block-345d4c79856d81bf873dd72cf3ab06d9" id="block-345d4c79856d81bf873dd72cf3ab06d9"></a>

The servo uses the UAVCAN communication protocol. The factory default CAN baud rate is 1 Mbps. The configurable baud rate range is 20 Kbps to 1 Mbps. The communication address, CAN baud rate, and node ID can be configured via upper computer software.

## **2. UAVCAN Command Examples** <a href="#block-345d4c79856d8052ba26e85e4882d1ff" id="block-345d4c79856d8052ba26e85e4882d1ff"></a>

The following commands use CAN 2.0B standard. Default motor NODE\_ID is 100 (0x64).

**Single-motor position command:** 1807DB01 (Frame ID): 00 64 05 D5 (Data)

**Level:** 18

**Frame type:** 07DB (2011)

**Frame** **source ID:** 01

**Frame data:** 00 64 05 (channel 00, position data 0564)

**Frame tail:** D5

**Multi-motor position command:**

1807DC01 (Frame ID): 8E 82 64 05 00 00 00 97 (Data) 1807DC01 (Frame ID): 00 00 00 00 00 00 00 37 (Data) 1807DC01 (Frame ID): 00 00 00 00 00 00 00 17 (Data) 1807DC01 (Frame ID): 00 00 00 00 00 00 00 37 (Data) 1807DC01 (Frame ID): 00 00 00 00 00 00 00 17 (Data) 1807DC01 (Frame ID): 00 00 00 77 (Data)

**Level:** 18

**Frame type:** 07DC (2012)

**Frame source ID:** 01

**CRC check code:** 8E 82

**Frame data:** 64 05 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 (cmd\[0]=0564, cmd\[1]=0000, cmd\[2]=0000 … cmd\[17]=0000)

**Frame tail:** 97 / 37 / 17 / 37 / 17 / 77

**Automatic feedback reporting command:**

1807DD64 (Frame ID): A1 04 00 CC 0C CD 0C 80 (Data) 1807DD64 (Frame ID): 45 00 00 00 2A 00 00 60 (Data)

**Level:** 18

**Frame type:** 07DD (2013)

**Frame source ID:** 64

**CRC check code:** A1 04

**Frame data:**

00 CC 0C CD 0C 45 00 00 00 2A 00 00 (Servo\_ID: 00, POS\_CMD: 0CCC, POS\_SENSOR: 0CCD, VOLTAGE: 0045, CURRENT: 0000, PCB\_Temp: 2A, MOTOR\_Temp: 00, StatusInfo: 00)

**Frame tail:** 80 / 60

**Node status command:** 18015564 (Frame ID): 50 03 00 00 00 00 00 D0 (Data)

**Level:** 18

**Frame type:** 0155 (341)

**Frame source ID:** 64

**Frame data:** 50 03 00 00 00 00 00 (uptime\_sec: 00000350, health: 0, mode: 0, sub\_mode: 0, vendor\_specific\_status\_code: 0)

**Frame tail:** D0

**Torque control command:** 1803FC01 (Frame ID): 00 00 D6 (Data)

**Level:** 18

**Frame type:** 03FC (1020)

**Source ID:** 01

**Frame data:** 00 00 D6 , Motor channel (00), torque command (00, 00 means torque off)

**Frame tail:** D6

**Read hardware version command:**

**Request:** 18FAE481 (Frame ID): 00 00 02 C0 (Data)

**Response:** 18FA0164 (Frame ID): 00 02 4E 28 07 D1 C0 (Data)

**Request Frame Level:** 18

**Request Frame Type:** FA(250)

**Request Frame Source ID:** 01

**Request Frame Target ID:** 64

**Request Frame Data:** 00 01 02 C0 (Parameter Address: 0001, Parameter Length: 02)

**Request Frame Tail:** C0

**Response Frame Level:** 18

**Response Frame Type:** FA(250)

**Response Frame Source ID:** 64

**Response Frame Target ID:** 01

**Response Frame Data:** 00 02 4E 28 07 D1 (Read Status: 00, Parameter Length: 02, Parameter Data 0: 4E28, Parameter Data 1: 07D1)

**Response Frame Tail:** C0

## 3. Servo Memory Map Definition <a href="#block-345d4c79856d80e9b267e42fab2a3aad" id="block-345d4c79856d80e9b267e42fab2a3aad"></a>

💡

The register address uses a paged structure, where each page contains 64 registers. The register address is composed of page number and index. For example, page 1, index 2 corresponds to address 1×64+2=66. All registers in the table can be accessed via MODBUS-RTU and UAVCAN protocols.

### **3.1 Version Information** <a href="#block-345d4c79856d80fdaa25e89a4910d873" id="block-345d4c79856d80fdaa25e89a4910d873"></a>

**Storage: SRAM, Access: Read-only, Write condition: None**

| Page | Index | Function                   | Range | Default | Description       |
| ---- | ----- | -------------------------- | ----- | ------- | ----------------- |
| 0    | 0     | Product Model High Byte    |       | 20008   |                   |
| 0    | 1     | Product Model Low Byte     |       | 2001    |                   |
| 0    | 2     | Firmware Version High Byte |       | 2050    |                   |
| 0    | 3     | Firmware Version Low Byte  |       | 513xx   | xx = 00\~99       |
| 0    | 4     | Byte Order                 |       | 1       | Big-endian format |
| 0    | 5     | SN1                        |       | 0       |                   |
| 0    | 6     | SN2                        |       | 0       |                   |
| 0    | 7     | SN3                        |       | 0       |                   |
| 0    | 8     | SN4                        |       | 0       |                   |

### **3.2 Control Parameters** <a href="#block-345d4c79856d802992dec49cd8a93081" id="block-345d4c79856d802992dec49cd8a93081"></a>

**Storage: SRAM, Access: Read/Write, Write condition: None**

| Page | Index | Function                  | Range         | Default                   | Description                                                                     |
| ---- | ----- | ------------------------- | ------------- | ------------------------- | ------------------------------------------------------------------------------- |
| 1    | 0     | Reserved Address          |               | 0                         |                                                                                 |
| 1    | 1     | Reserved Address          |               | 0                         |                                                                                 |
| 1    | 2     | Target Position High Byte | 0\~65535      | 0                         | 1=0.02197°, -8192\~8192 (output shaft -180°\~180°)                              |
| 1    | 3     | Target Position Low Byte  | 0\~65535      | 0                         | 1=0.02197°, -8192\~8192 (output shaft -180°\~180°)                              |
| 1    | 4     | Motion Acceleration       | 0\~2000       | Default acceleration      | Output shaft acceleration, 1=2.1972°/s², 0 = maximum default                    |
| 1    | 5     | Motion Speed              | -600\~600     | Default speed             | Output shaft speed, 1=0.1831 rpm, 0 = stop                                      |
| 1    | 6     | Motion Current            | -625\~625     | Default current           | Operating supply current, 1=6.5 mA                                              |
| 1    | 7     | Torque Limit              | 0\~4800       | Default torque limit      | Default value is 4800                                                           |
| 1    | 8     | Status Reset              | 0\~65535      | 0                         | See “Status Reset” bit definition                                               |
| 1    | 9     | Torque Switch             | 0\~1          | 0                         | 0: torque off; 1: torque on; in servo mode 0 UAVCAN command auto enables torque |
| 1    | 10    | Write Lock Flag           | 0\~11         | 0                         | EEPROM parameter unlock flag, unlock value equals page number                   |
| 1    | 11    | Write Lock Password       | -32768\~32767 | 0                         |                                                                                 |
| 1    | 12    | CAN Function Enable Bits  | 0\~7          | Default CAN function bits | See “CAN Function Enable Bits”                                                  |

**Status Reset: 0 invalid, 1 reset corresponding fault**

**Bit / weight description:**

* BIT10 (1024): reset revolution count
* BIT15 (32768): zero calibration

💡

**Note:**&#x54;o reset a fault, set corresponding bit to 1, convert to value, and write it to status reset (1-8).

**For example:**&#x6F;verheat and overcurrent reset → binary “0000 0000 0000 1100” → hex 000C.

**CAN function enable bits: 0 invalid, 1 valid**

* BIT0: node status auto report enable
* BIT1: ----
* BIT2: feedback auto report enable

### **3.3 Status Parameters** <a href="#block-345d4c79856d80f5b5a1d7905589a5f2" id="block-345d4c79856d80f5b5a1d7905589a5f2"></a>

**Storage: SRAM, Access: Read-only, Write condition: None**

| Page | Index  | Function                   | Range         | Default | Description                                                              |
| ---- | ------ | -------------------------- | ------------- | ------- | ------------------------------------------------------------------------ |
| 2    | 0      | Reserved Address           |               | --      |                                                                          |
| 2    | 1      | Reserved Address           |               | --      |                                                                          |
| 2    | 2      | Current Position High Byte | 0\~65535      | --      | Same unit as target position                                             |
| 2    | 3      | Current Position Low Byte  | 0\~65535      | --      | Same unit as target position                                             |
| 2    | 4      | Single Turn Position       | -32768\~32767 | --      | 1=360/16384=0.02197°                                                     |
| 2    | 5      | Reserved Address           |               |         |                                                                          |
| 2    | 6      | Current Speed              | -32768\~32767 | --      | 1=0.1831 rpm                                                             |
| 2    | 7      | Reserved Address           |               | 0       |                                                                          |
| 2    | 8      | Bus Current                | -2048\~2047   | --      | Same unit as motion current                                              |
| 2    | 9      | Voltage                    | 0\~400        | --      | 1=0.1 V                                                                  |
| 2    | 10     | MOS Temperature            | 0\~100        | --      | 1=1°C                                                                    |
| 2    | 11     | Load                       | 0\~5000       | --      | PWM duty cycle, 1=0.02%                                                  |
| 2    | 12     | Servo Status               | 0\~65535      | --      | See servo status bit definition                                          |
| 2    | 13     | Reserved Address           |               | --      |                                                                          |
| 2    | 14     | Motor Temperature          | 0\~100        | --      | 1=1°C                                                                    |
| 2    | 15\~21 | Reserved Address           |               | --      |                                                                          |
| 2    | 22     | Input Pulse Width (us)     |               | --      | microseconds                                                             |
| 2    | 23     | Input Pulse Period (us)    |               | --      | microseconds                                                             |
| 2    | 24     | Encoder Status Code        |               | --      | BIT0\~1: normal/strong/weak field; BIT2: button pressed; BIT3: overspeed |
| 2    | 25     | Encoder Error Count        |               | --      | Encoder communication error count                                        |

**Servo Status: 0 indicates normal, 1 indicates abnormal**

**Bit number / weight: description**

* BIT0 (1): overvoltage, automatically recovers when voltage is normal
* BIT1 (2): undervoltage, automatically recovers when voltage is normal
* BIT2 (4): driver MOS over-temperature, automatically recovers when temperature is normal
* BIT3 (8): overcurrent, recovers when detected output torque is below safety torque
* BIT5 (64): magnetic encoder error, automatically recovers when encoder is normal
* BIT7 (128): torque state, 0 = torque OFF, 1 = torque ON
* BIT8 (256): motion state, 0 = stopped, 1 = moving
* BIT9 (512): target out of range, automatically recovers when valid target is received
* BIT12 (4096): target reached status, 0 = reached target
* BIT13 (8192): motor MOS over-temperature, automatically recovers when temperature is normal
* BIT14 (32768): damping state, 1 = entering damping mode

💡

**Note:** If multiple statuses occur simultaneously, the servo status value is the sum of all active bit values.

**For example:** torque ON + overvoltage ⇒ 128 + 1 = 129

### **3.4 Communication Parameters** <a href="#block-345d4c79856d80f7b46efaf2cfe351b9" id="block-345d4c79856d80f7b46efaf2cfe351b9"></a>

**Storage: EPROM, Permission: Read/Write, Write condition: torque switch = 0 && write lock flag = 3**

| Page | Index  | Function                   | Range    | Default | Description                                                                                                    |
| ---- | ------ | -------------------------- | -------- | ------- | -------------------------------------------------------------------------------------------------------------- |
| 3    | 0      | UART Master ID             | 1\~247   | 1       | Unique device ID on the bus; duplicate IDs are not allowed; 0 is broadcast ID                                  |
| 3    | 1      | Reserved address           | –        | 0       | –                                                                                                              |
| 3    | 2      | UART baud rate             | 2\~10    | 4       | 2-10 correspond to: 256000(2), 128000(3), 115200(4), 57600(5), 38400(6), 19200(7), 14400(8), 9600(9), 4800(10) |
| 3    | 3      | Reserved address           | –        | 0       | –                                                                                                              |
| 3    | 4      | Reserved address           | –        | 0       | –                                                                                                              |
| 3    | 5      | UART response delay        | 0\~1000  | 500     | Unit: ms                                                                                                       |
| 3    | 6      | Reserved address           | –        | 0       | –                                                                                                              |
| 3    | 7      | CAN communication timeout  | 0\~1000  | 100     | Unit: ms                                                                                                       |
| 3    | 8      | CAN baud rate              | 0\~9     | 8       | 0-9 correspond to: 10K(0), 20K(1), 50K(2), 100K(3), 125K(4), 250K(5), 500K(6), 800K(7), 1M(8), 83.3K(9)        |
| 3    | 9      | CAN driver node ID         | 1\~125   | 100     | Unique NODE-ID of servo                                                                                        |
| 3    | 10     | CAN controller node ID     | 1\~125   | 1       | Controller NODE-ID; must match controller ID or servo will not accept commands                                 |
| 3    | 11     | Reserved address           | 0        | 0       | –                                                                                                              |
| 3    | 12     | Active reporting frequency | 0\~32767 | 100     | Unit: ms; interval for feedback auto-report; 0 disables reporting                                              |
| 3    | 13\~17 | Reserved address           | 0        | –       | –                                                                                                              |
| 3    | 18     | CAN heartbeat frequency    | 0\~32767 | 1000    | Unit: ms; status auto-report interval; 0 disables reporting                                                    |
| 3    | 19     | Reserved address           | 0        | 0       | –                                                                                                              |
| 3    | 20     | CAN channel ID             | 0\~17    | 0       | UAVCAN position command channel ID                                                                             |

### 3.5 Configuration Parameters <a href="#block-345d4c79856d8069a53fc47b9ebb9f4f" id="block-345d4c79856d8069a53fc47b9ebb9f4f"></a>

**Storage: EPROM, Permission: Read/Write, Write condition: torque switch = 0 && write lock flag = 4**

| Page | Index | Function                     | Range         | Default | Description                                                                                                                                                                 |
| ---- | ----- | ---------------------------- | ------------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 4    | 0     | Operating mode               | 0\~5          | 0       | 0 servo mode, 1 constant speed mode, 2 constant current mode, 3 RCPWM servo mode (reboot required), 4 reserved, 5 motor mode, 6 RCPWM constant speed mode (reboot required) |
| 4    | 1     | Default running speed        | 0\~32767      | –       | Same unit as running speed                                                                                                                                                  |
| 4    | 2     | Default acceleration         | 0\~32767      | –       | Same unit as running acceleration; 0 = invalid                                                                                                                              |
| 4    | 3     | Default max current          | 0\~4095       | –       | Same unit as running current                                                                                                                                                |
| 4    | 4     | Default max torque           | 0\~4800       | 4800    | Same unit as output torque                                                                                                                                                  |
| 4    | 5     | Reserved                     | –             | 0       | –                                                                                                                                                                           |
| 4    | 6     | Reserved                     | –             | 0       | –                                                                                                                                                                           |
| 4    | 7     | Positive direction dead zone | 0\~128        | 2       | Same unit as target position                                                                                                                                                |
| 4    | 8     | Negative direction dead zone | 0\~128        | 2       | Same unit as target position                                                                                                                                                |
| 4    | 9     | Minimum angle limit          | -8192\~0      | 0       | Same unit as target position; min=max means no limit; invalid in RCPWM mode                                                                                                 |
| 4    | 10    | Maximum angle limit          | 0\~8191       | 0       | Same unit as target position; min=max means no limit; invalid in RCPWM mode                                                                                                 |
| 4    | 11    | Output shaft position offset | -32768\~32767 | 0       | Same unit as target position                                                                                                                                                |
| 4    | 12    | Reserved                     | –             | –       | –                                                                                                                                                                           |
| 4    | 13    | CAN function default switch  | 0\~7          | 5       | See CAN function bit definition                                                                                                                                             |
| 4    | 14    | Configuration phase          | 0\~32768      | 0       | Reserved                                                                                                                                                                    |

### 3.6 RCPWM Parameters <a href="#block-345d4c79856d80eeb36bf84044eb6c96" id="block-345d4c79856d80eeb36bf84044eb6c96"></a>

**Storage: EPROM, Permission: Read/Write, Write condition: torque switch = 0 && write lock flag = 4**

| Page | Index | Function                       | Range         | Default | Description                                                       |
| ---- | ----- | ------------------------------ | ------------- | ------- | ----------------------------------------------------------------- |
| 5    | 0     | Min input pulse width          | 500\~2500     | 500     | Unit: μs                                                          |
| 5    | 1     | Max input pulse width          | 500\~2500     | 2500    | Unit: μs                                                          |
| 5    | 2     | Positive direction pulse width | 0\~1000       | 1000    | Unit: μs                                                          |
| 5    | 3     | Negative direction pulse width | 0\~1000       | 1000    | Unit: μs                                                          |
| 5    | 4     | Signal min angle               | -8192\~0      | -8192   | Same unit as target position; PWM mapping; UAVCAN 0\~1000 mapping |
| 5    | 5     | Signal max angle               | 0\~8191       | 8191    | Same unit as target position                                      |
| 5    | 6     | Signal resolution              | 1\~16         | 2       | Unit: μs                                                          |
| 5    | 7     | Signal trim                    | -128\~128     | 0       | Unit: μs                                                          |
| 5    | 8     | Fail-safe protection           | 0\~2          | 0       | 0: no torque, 1: go to fail-safe position, 2: hold position       |
| 5    | 9     | Fail-safe position             | -32768\~32767 | 0       | Same unit as target position                                      |
| 5    | 10    | Signal dead zone               | 0\~128        | 50      | RCPWM dead zone in speed mode                                     |
| 5    | 11    | Reserved                       | –             | 0       | –                                                                 |
| 5    | 12    | Reserved                       | –             | 0       | –                                                                 |
| 5    | 13    | Signal modulation factor       | 0\~512        | 15      | Higher value = faster response when enabled                       |
| 5    | 14    | Signal phase                   | 0\~65535      | 0       | See signal phase bit definition                                   |

**Signal phase: 0 = OFF, 1 = ON**

**Bit number / bit weight: description**

* BIT0 (1): ----
* BIT1 (2): ----
* BIT2 (4): In RCPWM constant-speed mode, signal and direction phase, 0 = forward direction, 1 = reverse direction
* BIT3 (8): In RCPWM servo mode, signal and target position phase, 0 = forward direction, 1 = reverse direction
* BIT4 (16): RCPWM signal modulation function bit; effective when firmware version ≥ 2050.51303; 0 = disabled, 1 = enabled (after enabling, weighting is adjusted via the signal modulation coefficient parameter); for fast response applications this bit must be disabled

### **3.7 Protection Parameters** <a href="#block-345d4c79856d803baf1ae0d740fd3217" id="block-345d4c79856d803baf1ae0d740fd3217"></a>

**Storage: EPROM, Permission: Read/Write, Write condition: torque switch = 0 && write lock flag = 7**

| Page | Index  | Function                              | Range    | Default | Description                                                                                                                                     |
| ---- | ------ | ------------------------------------- | -------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 7    | 0      | Torque shutdown condition             | 0\~65535 | 7       | See “LED alarm / torque shutdown condition” bit definition                                                                                      |
| 7    | 1      | LED alarm condition                   | 0\~65535 | 12295   | See “LED alarm / torque shutdown condition” bit definition                                                                                      |
| 7    | 2      | MOS max temperature limit             | 0\~100   | 70      | 1 = 1°C                                                                                                                                         |
| 7    | 3      | MOS protection temperature difference | 0\~10    | 2       | 1 = 1°C; overheat recovery temperature = MOS max temperature limit − MOS protection difference                                                  |
| 7    | 4      | MOS overheat protection time          | 0\~32767 | 50      | unit: ms                                                                                                                                        |
| 7    | 5      | Minimum input voltage                 | 0\~400   | 80      | 1 = 0.1V                                                                                                                                        |
| 7    | 6      | Maximum input voltage                 | 0\~400   | 280     | 1 = 0.1V                                                                                                                                        |
| 7    | 7      | Protection voltage difference         | 0\~20    | 5       | undervoltage recovery voltage = minimum voltage + protection difference; overvoltage recovery voltage = maximum voltage − protection difference |
| 7    | 8      | Undervoltage protection time          | 0\~32767 | 100     | unit: ms                                                                                                                                        |
| 7    | 9      | Overvoltage protection time           | 0\~32767 | 1000    | unit: ms                                                                                                                                        |
| 7    | 10\~12 | Reserved                              | 0        | 0       |                                                                                                                                                 |
| 7    | 13     | Protection current                    | 0\~4095  | 1000    | same unit as operating current                                                                                                                  |
| 7    | 14     | Overcurrent protection time           | 0\~32767 | 1000    | unit: ms                                                                                                                                        |
| 7    | 15     | Safety torque                         | 0\~4095  | 0       | maximum torque output after entering overcurrent protection; exits protection when torque drops below this value                                |
| 7    | 16\~18 | Reserved                              |          |         |                                                                                                                                                 |
| 7    | 19     | Motor max temperature limit           | 0\~100   | 0       | 1 = 1°C; 0 disables temperature sensor input                                                                                                    |
| 7    | 20     | Motor temperature difference          | 0\~10    | 2       | 1 = 1°C; overheat recovery temperature = motor max temperature limit − motor protection difference                                              |
| 7    | 21     | Motor overheat protection time        | 0\~32768 | 50      | unit: ms                                                                                                                                        |

**LED alarm condition / torque shutdown condition: 0 = OFF, 1 = ON**

**Bit number / bit weight: description**

* BIT0 (1): overvoltage alarm / overvoltage protection
* BIT1 (2): undervoltage alarm / undervoltage protection
* BIT2 (4): MOS overheat alarm / MOS overheat protection, motor overheat alarm / motor overheat protection
* BIT3 (8): overcurrent alarm / overcurrent protection
* BIT6 (64): terminal magnetic encoder error alarm / protection

### 3.8 PID Parameters <a href="#block-345d4c79856d80d89b72d2301dae6524" id="block-345d4c79856d80d89b72d2301dae6524"></a>

**Storage: EPROM, Permission: Read/Write, Write condition: torque switch = 0 && write lock flag = 8**

| Page | Index | Function                     | Range   | Default | Description  |
| ---- | ----- | ---------------------------- | ------- | ------- | ------------ |
| 8    | 0     | Position loop P              | 0\~1000 | 48      |              |
| 8    | 1     | Position loop D              | 0\~1000 | 32      |              |
| 8    | 2     | Position loop I              | 0\~1000 | 0       |              |
| 8    | 3     | Position loop integral limit | 0\~5000 | 0       | 0 = no limit |
| 8    | 4     | Reserved                     |         | 0       |              |
| 8    | 5     | Speed loop P                 | 0\~1000 | 20      |              |
| 8    | 6     | Speed loop I                 | 0\~1000 | 20      |              |
| 8    | 7     | Reserved                     |         | 0       |              |
| 8    | 8     | Current loop P               | 0\~1000 | 0       | Reserved     |
| 8    | 9     | Current loop I               | 0\~1000 | 1       |              |

<br>
