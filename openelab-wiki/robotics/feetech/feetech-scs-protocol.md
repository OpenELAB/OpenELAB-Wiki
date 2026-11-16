# FEETECH SCS Protocol

> FT SCS Servo Communication Protocol

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Communication Protocol Overview** <a href="#block-345d4c79856d81acbc29e14ce365e007" id="block-345d4c79856d81acbc29e14ce365e007"></a>

The communication level adopts TTL level compatible with high-speed communication and RS485 mode with strong anti-interference capability. Communication is based on asynchronous full-duplex transmission, and both transmission and reception signals are processed asynchronously.

The controller and servo communicate using a request–response mechanism, where the controller sends instruction frames and the servo returns response frames.

A multi-servo bus network is supported, where each servo is assigned a unique ID within the network. The control instructions sent by the controller include the ID information. Only the servo whose ID matches the instruction will fully receive it and return a response.

The communication method is asynchronous serial communication. Each data frame consists of 1 start bit, 8 data bits, and 1 stop bit, with no parity bit, totaling 10 bits.

For memory table parameters that use two-byte values, the byte order depends on the servo type: potentiometer-type servos use big-endian format (high byte first, low byte second), while magnetic encoder-type servos use little-endian format (low byte first, high byte second). Since each servo model may have slight functional differences, please refer to the specific model’s memory map for actual implementation and control.

## **2. Instruction Frame** <a href="#block-345d4c79856d80028b51d213d70dae7d" id="block-345d4c79856d80028b51d213d70dae7d"></a>

| Header    | ID | Length | Instruction | Parameters              | Checksum  |
| --------- | -- | ------ | ----------- | ----------------------- | --------- |
| 0xFF 0xFF | ID | Length | Instruction | Parameter1 … ParameterN | Check Sum |

* **Header:** two consecutive 0xFF indicate a valid packet
* **ID:** servo ID, range 0–253 (0x00–0xFD)
* **Broadcast ID:** 254 (0xFE). When used, all servos receive the instruction. Except PING, no response is returned. Broadcast PING is not allowed in multi-servo bus
* **Length:** equals N + 2 (N = parameter bytes)
* **Instruction:** operation code (see Section 1.3)
* **Parameters:** control data; max 2 bytes per memory value, byte order depends on servo model
* **Checksum:** Check Sum = \~ (ID + Length + Instruction + Parameter1 + … + ParameterN) If sum exceeds 255, only the lowest byte is used. “\~” means bitwise NOT

## 3. Response Frame <a href="#block-345d4c79856d80238e61c53c6da04ffc" id="block-345d4c79856d80238e61c53c6da04ffc"></a>

| Header    | ID | Length | Error | Parameters              | Checksum  |
| --------- | -- | ------ | ----- | ----------------------- | --------- |
| 0xFF 0xFF | ID | Length | ERROR | Parameter1 … ParameterN | Check Sum |

The response frame contains the servo status in the ERROR byte. If the servo is operating normally, ERROR = 0. Otherwise, error status is indicated (see memory map for details).

## **4 Instruction Types** <a href="#block-345d4c79856d805190def2d2661c8aa7" id="block-345d4c79856d805190def2d2661c8aa7"></a>

| Instruction          | Function                                   | Value | Parameter Length |
| -------------------- | ------------------------------------------ | ----- | ---------------- |
| PING                 | Query status                               | 0x01  | 0                |
| READ DATA            | Read memory data                           | 0x02  | 2                |
| WRITE DATA           | Write memory data                          | 0x03  | ≥2               |
| REG WRITE            | Buffered write (non-executed until ACTION) | 0x04  | ≥4               |
| ACTION               | Execute REG WRITE                          | 0x05  | 0                |
| SYNC READ            | Read multiple servos                       | 0x82  | ≥3               |
| SYNC WRITE           | Write multiple servos                      | 0x83  | ≥2               |
| RESET                | Reset status (revolution reset)            | 0x0A  | 0                |
| Position Calibration | Position re-calibration                    | 0x0B  | 0                |
| Parameter Restore    | Restore parameters                         | 0x06  | 0                |
| Parameter Backup     | Save parameters                            | 0x09  | 0                |
| Reboot               | Restart servo                              | 0x08  | 0                |

### **4.1 PING** <a href="#block-345d4c79856d807e9330d5994f8e9349" id="block-345d4c79856d807e9330d5994f8e9349"></a>

**Function:** Query servo working status

**Length:** 0x02

**Instruction:** 0x01

**Parameters:** None

PING can use broadcast ID. Servos will still return response frames.

**Example 1: Read the operating status of the servo with ID 1.**

Instruction frame: FF FF 01 02 01 FB (sent in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 02 **Instruction:** 01 **Checksum:** FB

Response frame: FF FF 01 02 00 FC (displayed in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 02 **Status:** 00 **Checksum:** FC

### **4.2 READ DATA** <a href="#block-345d4c79856d801f8779c6cfbbed8e1f" id="block-345d4c79856d801f8779c6cfbbed8e1f"></a>

**Function:** Read data from memory table

**Length:** 0x04

**Instruction:** 0x02

**Parameter1:** Start address

**Parameter2:** Data length

**Example 2: Read the current position of servo ID 1 (low byte first, high byte second). The position parameter memory address is 0x38, with 2 consecutive bytes.**

Instruction frame: FF FF 01 04 02 38 02 BE (sent in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 04 **Instruction:** 02 **Parameters:** 38 02 (current position address, data length) **Checksum:** BE

Response frame: FF FF 01 04 00 18 05 DD (displayed in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 04 **Instruction:** 00 **Parameters:** 18 05 **Checksum:** DD

The two bytes read are interpreted in little-endian format: low byte L 0x18, high byte H 0x05. Combining them forms the 16-bit value 0x0518, which equals 1304 in decimal, representing the current position.

### 4.3 WRITE DATA Instruction <a href="#block-345d4c79856d80bba45cea34c99274c7" id="block-345d4c79856d80bba45cea34c99274c7"></a>

**Function:** Write data into the servo memory control table

**Length:** N + 2 (N is parameter length)

**Instruction:** 0x03

**Parameter 1:** Starting address of the write region

**Parameter 2:** First data byte to write

**Parameter 3:** Second data byte to write

…

**Parameter N:** Nth data byte，N=n+1

**Example 3: Use broadcast ID (0xFE) to set the ID of any servo to 1. The memory address for ID is 5.**

Instruction frame: FF FF FE 04 03 05 01 F4 (sent in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 04 **Instruction:** 03 **Parameters:** 05 01 (ID address, new ID value) **Checksum:** F4

Because a broadcast ID is used, no response is returned. In addition, the EPROM memory table has a protection lock switch; it must be disabled (set to 0) before modifying the ID, otherwise the ID will not be saved after power-off. Please refer to the specific servo manual for details.

**Example 4: Control servo ID 1 to rotate to position 2048 at a speed of 1000 steps per second. The starting address of the target position in the memory table is 0x2A, so 6 consecutive bytes are written starting from 0x2A.**

Position data: 0x0800 (2048) Reserved data: 0x0000 (0) Speed data: 0x03E8 (1000)

Instruction frame: FF FF 01 09 03 2A 00 08 00 00 E8 03 D5 (sent in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 09 **Instruction:** 03 **Parameters:** 2A (start address) 00 08 (position) 00 00 (reserved) E8 03 (speed) **Checksum:** D5

Response frame: FF FF 01 02 00 FC (displayed in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 02 **Status:** 00 **Checksum:** FC

The returned status is 0, indicating the servo correctly received the instruction without errors and has started execution. Since the instruction uses a non-broadcast ID (0xFE is broadcast; here ID is specific), the servo returns a status packet after receiving the command.

### 4.4 Asynchronous Write Instruction REG WRITE <a href="#block-345d4c79856d802184f3ecc77173bc7a" id="block-345d4c79856d802184f3ecc77173bc7a"></a>

REG WRITE is similar to WRITE DATA, but the execution timing is different. When a REG WRITE frame is received, the data is stored in a buffer, and an asynchronous write flag register is set to 1. The stored command is executed only after receiving an ACTION instruction.

**Length:** N + 2

**Instruction:** 0x04

**Parameter 1:** Starting address of write area

**Parameter 2:** First data byte

**Parameter 3:** Second data byte

…

**Parameter N:** Nth data byte

**Example 5: Control servos ID 1 to ID 10 to rotate to position 2048 at speed 1000 per second.**

ID 1: Asynchronous write instruction frame: FF FF 01 09 04 2A 00 08 00 00 E8 03 D4 ID 1: Response frame: FF FF 01 02 00 FC

ID 2: Asynchronous write instruction frame: FF FF 02 09 04 2A 00 08 00 00 E8 03 D3 ID 2: Response frame: FF FF 02 02 00 FB

ID 3: Asynchronous write instruction frame: FF FF 03 09 04 2A 00 08 00 00 E8 03 D2 ID 3: Response frame: FF FF 03 02 00 FA

ID 4: Asynchronous write instruction frame: FF FF 04 09 04 2A 00 08 00 00 E8 03 D1 ID 4: Response frame: FF FF 04 02 00 F9

ID 5: Asynchronous write instruction frame: FF FF 05 09 04 2A 00 08 00 00 E8 03 D0 ID 5: Response frame: FF FF 05 02 00 F8

ID 6: Asynchronous write instruction frame: FF FF 06 09 04 2A 00 08 00 00 E8 03 CF ID 6: Response frame: FF FF 06 02 00 F7

ID 7: Asynchronous write instruction frame: FF FF 07 09 04 2A 00 08 00 00 E8 03 CE ID 7: Response frame: FF FF 07 02 00 F6

ID 8: Asynchronous write instruction frame: FF FF 08 09 04 2A 00 08 00 00 E8 03 CD ID 8: Response frame: FF FF 08 02 00 F5

ID 9: Asynchronous write instruction frame: FF FF 09 09 04 2A 00 08 00 00 E8 03 CC ID 9: Response frame: FF FF 09 02 00 F4

ID 10: Asynchronous write instruction frame: FF FF 0A 09 04 2A 00 08 00 00 E8 03 CB ID 10: Response frame: FF FF 0A 02 00 F3

### 4.5 Execute Asynchronous Write Instruction ACTION <a href="#block-345d4c79856d80de853bf3f5fa3262da" id="block-345d4c79856d80de853bf3f5fa3262da"></a>

**Function:** Trigger the REG WRITE instruction

**Length:** 0x02

**Instruction:** 0x05

**Parameters:** None

1. The ACTION instruction is very useful when controlling multiple servos simultaneously.
2. When controlling multiple servos, using the ACTION instruction allows the first and the last servo to execute their respective actions simultaneously, with no delay in between.
3. When sending the ACTION instruction to multiple servos, the broadcast ID (0xFE) must be used. Therefore, no response frame will be returned when this instruction is sent.

**Example 6: After sending asynchronous write instructions to control servos ID1 to ID10 to rotate to position 2048 at a speed of 1000 per second, the asynchronous write command needs to be executed.**

**Instruction frame:** FF FF FE 02 05 FA

**Response frame:** None

### 4.6 Synchronous Write Instruction SYNC WRITE <a href="#block-345d4c79856d8058a602c2c7a43a1fe6" id="block-345d4c79856d8058a602c2c7a43a1fe6"></a>

**Function:** Used to control multiple servos simultaneously.

**ID:** 0xFE

**Length:** (L + 1) × n + 4 (L: data length sent to each servo, n: number of servos)

**Instruction:** 0x83

**Parameter 1:** Starting address for writing data

**Parameter 2:** Length of data to be written (L)

**Parameter 3:** ID of the 1st servo

**Parameter 4:** 1st data byte for the 1st servo

**Parameter 5:** 2nd data byte for the 1st servo

…

**Parameter L+3:** L-th data byte for the 1st servo

**Parameter L+4:** ID of the 2nd servo

**Parameter L+5:** 1st data byte for the 2nd servo

**Parameter L+6:** 2nd data byte for the 2nd servo

…

**Parameter 2L+4:** L-th data byte for the 2nd servo

… Compared with the REG WRITE + ACTION instruction, SYNC WRITE provides higher real-time performance. A single SYNC WRITE instruction can modify the control table contents of multiple servos at once, whereas REG WRITE + ACTION performs this in steps. However, when using SYNC WRITE, the data length and the starting address must be identical for all servos.

**Example 7: Write position 0x0800, time 0x0000, and speed 0x03E8 to servos ID1–ID4 at starting address 0x2A (low byte first, high byte second).**

Instruction frame: FF FF FE 20 83 2A 06 01 00 08 00 00 E8 03 02 00 08 00 00 E8 03 03 00 08 00 00 E8 03 04 00 08 00 00 E8 03 58 (sent in hexadecimal format)

**Header:** FF FF **ID:** FE **Effective data length:** 20 **Instruction:** 83 **Parameters:** 2A 06 (start address, data length) 01 00 08 00 00 E8 03 (instruction for servo ID1) 02 00 08 00 00 E8 03 (instruction for servo ID2) 03 00 08 00 00 E8 03 (instruction for servo ID3) 04 00 08 00 00 E8 03 (instruction for servo ID4) **Checksum:** 58

### 4.7 Synchronous Read Instruction SYNC READ <a href="#block-345d4c79856d80c7a2d7f5b291956663" id="block-345d4c79856d80c7a2d7f5b291956663"></a>

**Function:** Used to query multiple servos simultaneously.

**ID:** 0xFE

**Length:** n + 4 (n is the number of servos)

**Instruction:** 0x82

**Parameter 1:** Starting address of the data to read

**Parameter 2:** Length of data to read

**Parameter 3:** ID of the 1st servo

**Parameter 4:** ID of the 2nd servo

…

**Parameter N:** ID of the n-th servo, where N = n + 2

A single SYNC READ instruction can query the control table contents of multiple servos at once. The instruction specifies the IDs of the servos to be queried, and the servos return response frames in the same order as the IDs in the instruction. When using SYNC READ, all queried data must have the same starting address and data length (this instruction is supported only by some serial bus servos).

**Example 8: Query the current position, current speed, current load, current voltage, and current temperature of servos ID1 and ID2 (starting address 0x38, total 8 bytes, low byte first, high byte second).**

**Instruction frame:** FF FF FE 06 82 38 08 01 02 36

**Header:** FF FF **ID:** FE **Length:** 06 **Instruction:** 82 **Parameters:** 38 08 (data start address, data length) 01 02 (ID01, ID02) **Checksum:** 36

**Response frames:**

**Servo ID01:** FF FF 01 0A 00 00 08 00 00 00 00 79 1E 55 **Servo ID02:** FF FF 02 0A 00 FF 07 00 00 00 00 77 23 53

The response frames can be decoded according to the READ DATA instruction format.

### 4.8 Reset Instruction (RESET) <a href="#block-345d4c79856d8038a3dee7e7244b0666" id="block-345d4c79856d8038a3dee7e7244b0666"></a>

**Function:** Reset the servo status (reset the servo revolution count)

**Length:** 0x02

**Instruction:** 0x0A

**Parameters:** None

**Example 9: Reset the servo with ID = 01**

**Instruction frame:** FF FF 01 02 0A F2 (sent in hexadecimal format) **Response Frame:** FF FF 01 02 00 FC (displayed in hexadecimal format)

### 4.9 Position Calibration Instruction <a href="#block-345d4c79856d80e2b2e1ecef2821a2d3" id="block-345d4c79856d80e2b2e1ecef2821a2d3"></a>

**Function:** Recalibrate the current position to a specified value

**Length:** 0x02 or 0x04

**Instruction:** 0x0B

**Parameters:** None or specified value

**Note: If no parameter is provided, the current position will be calibrated to the middle position.This instruction is only supported by certain servo models. Refer to the table below for supported models.**

**Example 10: Calibrate current position to the middle position**

**Instruction frame:** FF FF 01 02 0B F1 (sent in hexadecimal format) **Response Frame:** FF FF 01 02 00 FC (displayed in hexadecimal format)

**Example 11: Calibrate current position to 1024**

**Instruction frame:** FF FF 01 04 0B 00 04 EB (sent in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 04 **Instruction:** 0B **Set Value:** 00 04 (1024) **Checksum:** EB

**Response Frame:** FF FF 01 02 00 FC (displayed in hexadecimal format)

**Header:** FF FF **ID:** 01 **Length:** 02 **Status:** 00 **Checksum:** FC

| Servo Model | Firmware Version | Effective Condition | Remarks                                                                                                             |
| ----------- | ---------------- | ------------------- | ------------------------------------------------------------------------------------------------------------------- |
| SMS Servo   | ≤ 2.54           | None                | Supports midpoint calibration by writing 128 to torque switch                                                       |
| STS Servo   | ≥ 3.10           | None                | Supports both parameter and non-parameter instructions; supports midpoint calibration via torque switch (write 128) |
| HLS Servo   | ≥ 3.43           | None                | Supports both parameter and non-parameter instructions; does NOT support midpoint calibration via torque switch     |

### 4.10 Parameter Restore Instruction <a href="#block-345d4c79856d8064b47cee49a884c7b5" id="block-345d4c79856d8064b47cee49a884c7b5"></a>

**Function:** Restore all servo parameters except the ID

**Length:** 0x02

**Instruction:** 0x06

**Parameters:** None

**Example 11: Restore servo parameters**

Copy

```c
Instruction frame: FF FF 01 02 06 F6  (sent in hexadecimal format)
Response Frame: FF FF 01 02 00 FC  (displayed in hexadecimal format)
```

💡

**Note: Before restoring parameters, the EPROM protection must be unlocked.**

### 4.11 Parameter Backup Instruction <a href="#block-345d4c79856d8074bb4cfc10480a2edb" id="block-345d4c79856d8074bb4cfc10480a2edb"></a>

**Function:** Backup parameters (used for parameter restore instruction)

**Length:** 0x02

**Instruction:** 0x09

**Parameters:** None

**Example 12: Backup servo parameters**

Copy

```c
Instruction frame: FF FF 01 02 09 F3  (sent in hexadecimal format)
Response Frame: FF FF 01 02 00 FC  (displayed in hexadecimal format)
```

💡

**Note:Before backing up parameters, the EPROM protection must be unlocked.**

### 4.12 Reboot Instruction <a href="#block-345d4c79856d80998853e70f8dd412e2" id="block-345d4c79856d80998853e70f8dd412e2"></a>

**Function:** Reboot the servo

**Length:** 0x02

**Instruction:** 0x08

**Parameters:** None

**Example 13: Reboot servo**

Copy

```c
Instruction frame: FF FF 01 02 08 F4  (sent in hexadecimal format)
Response Frame: None  (reboot time is approximately 800 ms)
```

💡

**Note: Before rebooting the servo, the torque must be turned off.**

<br>
