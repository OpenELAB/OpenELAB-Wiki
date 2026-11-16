# FEETECH CAN2.0A to FTSCS1.0 Protocol

> FEETECH CAN2.0A to FTSCS1.0 Protocol

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Protocol Overview** <a href="#block-345d4c79856d81e49433fe18402eda01" id="block-345d4c79856d81e49433fe18402eda01"></a>

This protocol is based on the CAN2.0A standard data frame. It defines a set of custom communication commands that are converted into the FTSCS1.0 proprietary protocol, enabling FEETECH bus servos using custom protocols to work together with CAN bus devices.

Communication is carried out using the CAN2.0A standard data frame. The factory default CAN baud rate is 1 Mbps, with a configurable range from 100 kbps to 1 Mbps. The default CAN node ID is set to 1. Both the CAN baud rate and the communication node ID can be configured via CAN commands.

Since the FTSCS1.0 protocol is based on RS485/TTL communication, the CAN converter must follow a strict request–response communication mechanism; otherwise, data collisions may occur on the RS485/TTL bus.

This conversion protocol must be used with FEETECH dedicated converter modules (such as CAN2.0A to TTL single-bus modules) to achieve communication conversion functionality.

## **2. CAN2.0A Frame Format** <a href="#block-345d4c79856d8086807fe92fd342c593" id="block-345d4c79856d8086807fe92fd342c593"></a>

| CAN-ID        | DLC               | Data1 … DataN                   |
| ------------- | ----------------- | ------------------------------- |
| 11-bit CAN-ID | Data length (0–8) | Each data field is 1 byte, n<=8 |

**CAN-ID Structure:**

| CAN-ID | BIT10 … BIT6         | BIT5 … BIT0      |
| ------ | -------------------- | ---------------- |
|        | CAN instruction code | CAN node address |

* **BIT5 \~ BIT0:** CAN node address, range 0 \~ 63
* 0 = broadcast address
* 1–63 = unicast address
* **BIT10 \~ BIT6:** CAN instruction code, used to define the function of the CAN message

**CAN Instruction Codes:**

| Instruction Code | Function Description               | CAN-ID                   | Description                  |
| ---------------- | ---------------------------------- | ------------------------ | ---------------------------- |
| 0x01             | Memory table read instruction      | 0x080 + CAN node address |                              |
| 0x02             | Memory table write instruction     | 0x100 + CAN node address |                              |
| 0x03             | Position control instruction       | 0x180 + CAN node address |                              |
| 0x04             | Synchronous read instruction       | 0x200 + CAN node address |                              |
| 0x05             | Asynchronous control instruction   | 0x280 + CAN node address |                              |
| 0x06             | Asynchronous execution instruction | 0x300 + CAN node address |                              |
| 0x07             | Synchronous control instruction    | 0x380 + CAN node address |                              |
| 0x08             | Synchronous execution instruction  | 0x400 + CAN node address |                              |
| 0x09             | Servo response instruction         | 0x480 + CAN node address | Used for servo response data |
| 0x0A             | CAN configuration instruction      | 0x500 + CAN node address |                              |
| 0x0B             | Servo calibration instruction      | 0x580 + CAN node address |                              |

### 2.1 Memory Table Read Instruction (0x01) <a href="#block-345d4c79856d800396abfd52927710b9" id="block-345d4c79856d800396abfd52927710b9"></a>

The memory table read instruction is used to query data from the servo memory table. A maximum of 6 bytes can be read per request.

|          | CAN-ID              | DLC   | Data                                                                      |
| -------- | ------------------- | ----- | ------------------------------------------------------------------------- |
| Send     | 0x080 + CAN node ID | 3     | Servo ID (1 byte), Memory address (1 byte), Data length N (1 byte, N ≤ 6) |
| Response | 0x480 + CAN node ID | N + 2 | Servo ID (1 byte), Servo status (1 byte), Data1 (1 byte) … DataN (1 byte) |

### 2.2 Memory Table Write Instruction (0x02) <a href="#block-345d4c79856d803a9954f7f507c983ce" id="block-345d4c79856d803a9954f7f507c983ce"></a>

The memory table write instruction is used to write data into the servo memory table. A maximum of 6 bytes can be written per operation.

|          | CAN-ID              | DLC   | Data                                                                               |
| -------- | ------------------- | ----- | ---------------------------------------------------------------------------------- |
| Send     | 0x100 + CAN node ID | N + 2 | Servo ID (1 byte), Memory address (1 byte), Data1 (1 byte) … DataN (1 byte, N ≤ 6) |
| Response | 0x480 + CAN node ID | 2     | Servo ID (1 byte), Servo status (1 byte)                                           |

### 2.3 Position Control Instruction (0x03) <a href="#block-345d4c79856d80eea6c4cd308737de7f" id="block-345d4c79856d80eea6c4cd308737de7f"></a>

The position control instruction is used to control the servo position. The input command includes: Servo ID (1 byte), Position (2 bytes), Acceleration (1 byte), Speed (2 bytes), and Operating Current (2 bytes).

|          | CAN-ID              | DLC | Data                                                                                                                                  |
| -------- | ------------------- | --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Send     | 0x180 + CAN node ID | 8   | Servo ID (1 byte), Target position (2 bytes), Operating acceleration (1 byte), Operating speed (2 bytes), Operating current (2 bytes) |
| Response | 0x480 + CAN node ID | 2   | Servo ID (1 byte), Servo status (1 byte)                                                                                              |

### 2.4 Synchronous Read Instruction (0x04) <a href="#block-345d4c79856d80a0b87bf512732df0b5" id="block-345d4c79856d80a0b87bf512732df0b5"></a>

The synchronous read instruction can be used to read memory table data from up to 6 servos simultaneously.

|          | CAN-ID              | DLC   | Data                                                                                                   |
| -------- | ------------------- | ----- | ------------------------------------------------------------------------------------------------------ |
| Send     | 0x200 + CAN node ID | n + 2 | Memory address (1 byte), Data length N (1 byte, N ≤ 6), Servo ID1 (1 byte) … Servo IDn (1 byte, n ≤ 6) |
| Response | 0x480 + CAN node ID | N + 2 | Servo ID (1 byte), Servo status (1 byte), Data1 (1 byte) … DataN (1 byte)                              |

### 2.5 Asynchronous Control Instruction (0x05) <a href="#block-345d4c79856d80b4865fde441e391773" id="block-345d4c79856d80b4865fde441e391773"></a>

The asynchronous control instruction is used to control servo position in asynchronous mode. The input command includes: Servo ID (1 byte), Target position (2 bytes), Operating acceleration (1 byte), Operating speed (2 bytes), and Operating current (2 bytes).

|          | CAN-ID              | DLC | Data                                                                                                                                  |
| -------- | ------------------- | --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Send     | 0x280 + CAN node ID | 8   | Servo ID (1 byte), Target position (2 bytes), Operating acceleration (1 byte), Operating speed (2 bytes), Operating current (2 bytes) |
| Response | 0x480 + CAN node ID | 2   | Servo ID (1 byte), Servo status (1 byte)                                                                                              |

### 2.6 Asynchronous Execution Instruction (0x06) <a href="#block-345d4c79856d8060bc1ef0366ab956f3" id="block-345d4c79856d8060bc1ef0366ab956f3"></a>

The asynchronous execution instruction is used to execute buffered asynchronous control instructions.

|      | CAN-ID              | DLC | Data |
| ---- | ------------------- | --- | ---- |
| Send | 0x300 + CAN node ID | 0   | None |

### 2.7 Synchronous Control Instruction (0x07) <a href="#block-345d4c79856d80cb9dc1cfa5b1af76a4" id="block-345d4c79856d80cb9dc1cfa5b1af76a4"></a>

The synchronous control instruction is used for synchronized servo position control. The input command includes: Servo ID (1 byte), Target position (2 bytes), Operating acceleration (1 byte), Operating speed (2 bytes), and Operating current (2 bytes). The input commands are first buffered in the CAN converter, and after receiving the synchronous execution instruction, they are converted into servo synchronous control commands and output.

|      | CAN-ID              | DLC | Data                                                                                                                                  |
| ---- | ------------------- | --- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Send | 0x380 + CAN node ID | 8   | Servo ID (1 byte), Target position (2 bytes), Operating acceleration (1 byte), Operating speed (2 bytes), Operating current (2 bytes) |

### 2.8 Synchronous Execution Instruction (0x08) <a href="#block-345d4c79856d80c4bef5ee24fc0487b0" id="block-345d4c79856d80c4bef5ee24fc0487b0"></a>

After the CAN converter receives the synchronous execution command, it converts the cached synchronous control instructions into servo synchronous control instructions and outputs them.

**Execution Instruction:**

|      | CAN-ID              | DLC | Data |
| ---- | ------------------- | --- | ---- |
| Send | 0x400 + CAN node ID | 0   | None |

**Clear Instruction:**

|      | CAN-ID              | DLC | Data |
| ---- | ------------------- | --- | ---- |
| Send | 0x400 + CAN node ID | 1   | 0    |

**Query Instruction:**

|          | CAN-ID              | DLC | Data                                     |
| -------- | ------------------- | --- | ---------------------------------------- |
| Send     | 0x400 + CAN node ID | 1   | 1                                        |
| Response | 0x400 + CAN node ID | 1   | Number of buffered instructions (1 byte) |

### **2.9 CAN Configuration Command (0x0A)** <a href="#block-345d4c79856d801bab44db731d3178ee" id="block-345d4c79856d801bab44db731d3178ee"></a>

**CAN Configuration Command:**

|          | CAN-ID              | DLC | Data                                                                                                                                                                                                             |
| -------- | ------------------- | --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Send     | 0x500 + CAN node ID | 3   | CAN baud rate (1 byte), CAN node ID (1 byte), servo baud rate (1 byte)                                                                                                                                           |
| Response | 0x500 + CAN node ID | 8   | Baud rate (1 byte), CAN node ID (1 byte), servo baud rate (1 byte), reserved (1 byte), firmware version (1 byte), firmware release year (1 byte), firmware release month (1 byte), firmware release day (1 byte) |

**CAN node ID:** 1 \~ 63

**Servo baud rate:** 0 \~ 3, where 0 = 1M, 1 = 500k, 2 = 250k, 3 = 115200

**CAN baud rate:** 0 \~ 3, where 0 = 1M, 1 = 500k, 2 = 250k, 3 = 100k

**CAN Configuration Query Response:**

|          | CAN-ID              | DLC | Data                                                                                                                                                                                                             |
| -------- | ------------------- | --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Send     | 0x500 + CAN node ID | 0   | None                                                                                                                                                                                                             |
| Response | 0x500 + CAN node ID | 8   | Baud rate (1 byte), CAN node ID (1 byte), servo baud rate (1 byte), reserved (1 byte), firmware version (1 byte), firmware release year (1 byte), firmware release month (1 byte), firmware release day (1 byte) |

**Note: Configuration changes take effect after reboot.**

### 2.10 Servo Calibration Command (0x0B) <a href="#block-345d4c79856d8004a109c98d801478c1" id="block-345d4c79856d8004a109c98d801478c1"></a>

**Recalibrate current position to a specified value:**

|          | CAN-ID              | DLC | Data                                              |
| -------- | ------------------- | --- | ------------------------------------------------- |
| Send     | 0x580 + CAN node ID | 3   | Servo ID (1 byte), calibration position (2 bytes) |
| Response | 0x480 + CAN node ID | 2   | Servo ID (1 byte), servo status (1 byte)          |

**Recalibrate current position to center (mid-position):**

|          | CAN-ID              | DLC | Data                                     |
| -------- | ------------------- | --- | ---------------------------------------- |
| Send     | 0x580 + CAN node ID | 1   | Servo ID (1 byte)                        |
| Response | 0x480 + CAN node ID | 2   | Servo ID (1 byte), servo status (1 byte) |
