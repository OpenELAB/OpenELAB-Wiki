# FEETECH Modbus-RTU Protocol

> FEETECH Modbus-RTU Servo Communication Protocol

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Protocol Overview** <a href="#block-346d4c79856d8178998aec2f9ae44649" id="block-346d4c79856d8178998aec2f9ae44649"></a>

The Modbus-RTU communication protocol (national standard GB/T 19582-2008) is used for communication. It supports one master controlling multiple slaves. Up to 247 slave addresses can be configured via the built-in host computer software (0 is the broadcast address, 1-247 are unicast addresses). The master can be a microcontroller, PLC, PC, or similar device.

## **2. Communication Parameters** <a href="#block-346d4c79856d80359f2bda25576b00e0" id="block-346d4c79856d80359f2bda25576b00e0"></a>

The factory default serial port configuration is as follows: baud rate defaults to 115200 bps, data bits: 8, parity: none, stop bits: 1. The configurable baud rate range is 4800 to 256000 bps. The default communication address (station number) of the driver is 1.

## **3. Modbus-RTU Frame Format** <a href="#block-346d4c79856d80068bfdd17e200d8113" id="block-346d4c79856d80068bfdd17e200d8113"></a>

This driver supports Modbus function codes 0x03 (read holding registers), 0x06 (write single register), and 0x10 (write multiple registers), as well as the exception code 0x83. The supported exception codes are 0x01 (invalid function code) and 0x02 (invalid data address).

### **3.1 Read Holding Registers (0x03)** <a href="#block-346d4c79856d8059b50fc95e23747220" id="block-346d4c79856d8059b50fc95e23747220"></a>

**Transmitted by master:**

| BIT     | 1             | 2    | 3                          | 4                         | 5                          | 6                         | 7             | 8            |
| ------- | ------------- | ---- | -------------------------- | ------------------------- | -------------------------- | ------------------------- | ------------- | ------------ |
| Content | Slave Address | 0x03 | Register Address High Byte | Register Address Low Byte | Read Data Length High Byte | Read Data Length Low Byte | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1–247)
* Byte 2 – 0x03: Read register function code
* Bytes 3–4: Start address of read registers
* Bytes 5–6: Read data length
* Bytes 7–8: CRC16 checksum of bytes 1–6

**Slave normal response:**

| BIT     | 1             | 2    | 3                              | 4、5             | 6、7             |   | n-1、n           | n+1           | n+2          |
| ------- | ------------- | ---- | ------------------------------ | --------------- | --------------- | - | --------------- | ------------- | ------------ |
| Content | Slave Address | 0x03 | Total Number of Register Bytes | Register Data 1 | Register Data 2 | … | Register Data m | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247)
* Byte 2 – 0x03: Read register function code
* Byte 3: Total number of register bytes from byte 4 to byte n (inclusive)
* Bytes 4 to n: Data of m registers read, where m = (n-3)/2, with byte n-1 as the high byte and byte n as the low byte
* Bytes n+1 & n+2: CRC16 checksum of bytes 1 to n

**Slave exception response:**

| BIT     | 1             | 2    | 3    | 4             | 5            |
| ------- | ------------- | ---- | ---- | ------------- | ------------ |
| Content | Slave Address | 0x83 | 0x02 | CRC High Byte | CRC Low Byte |

### **3.2 Write Single Register (0x06)** <a href="#block-346d4c79856d8039ae1ad469a9fd6994" id="block-346d4c79856d8039ae1ad469a9fd6994"></a>

**Transmitted by master:**

| BIT     | 1             | 2    | 3                          | 4                         | 5                       | 6                      | 7             | 8            |
| ------- | ------------- | ---- | -------------------------- | ------------------------- | ----------------------- | ---------------------- | ------------- | ------------ |
| Content | Slave Address | 0x06 | Register Address High Byte | Register Address Low Byte | Register Data High Byte | Register Data Low Byte | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247)
* Byte 2 – 0x06: Write single register function code
* Bytes 3 & 4: Address of the register to be written
* Bytes 5 & 6: Data to be written to the register
* Bytes 7 & 8: CRC16 checksum of bytes 1 to 6

**Slave normal response:**

| BIT     | 1             | 2    | 3                          | 4                         | 5                       | 6                      | 7             | 8            |
| ------- | ------------- | ---- | -------------------------- | ------------------------- | ----------------------- | ---------------------- | ------------- | ------------ |
| Content | Slave Address | 0x06 | Register Address High Byte | Register Address Low Byte | Register Data High Byte | Register Data Low Byte | CRC High Byte | CRC Low Byte |

**Slave exception response:**

| BIT     | 1             | 2    | 3              | 4             | 5            |
| ------- | ------------- | ---- | -------------- | ------------- | ------------ |
| Content | Slave Address | 0x86 | Exception code | CRC High Byte | CRC Low Byte |

💡

Exception code: 0x02 indicates an invalid address in the master request, and 0x03 indicates invalid data in the request.

### **3.3 Write Multiple Registers (0x10)** <a href="#block-346d4c79856d809abcceeec9d02f5f13" id="block-346d4c79856d809abcceeec9d02f5f13"></a>

**Transmitted by master:**

| BIT     | 1             | 2    | 3                          | 4                         | 5                         | 6                        | 7                              | 8、9             | 10、11           |   | n-1、n           | n+1           | n+2          |
| ------- | ------------- | ---- | -------------------------- | ------------------------- | ------------------------- | ------------------------ | ------------------------------ | --------------- | --------------- | - | --------------- | ------------- | ------------ |
| Content | Slave Address | 0x10 | Register Address High Byte | Register Address Low Byte | Register Length High Byte | Register Length Low Byte | Total number of register bytes | Register Data 1 | Register Data 2 | … | Register Data m | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247)
* Byte 2 – 0x10: Write multiple registers function code
* Bytes 3 & 4: Address of the register to be written (Byte 3 = high byte, Byte 4 = low byte)
* Bytes 5 & 6: Number of registers to write (m)
* Byte 7: Total number of bytes from Byte 8 to Byte n (inclusive)
* Bytes 8 to n: Data of the m registers to be written, where m = (n-7)/2, with Byte n-1 as the high byte and Byte n as the low byte
* Bytes n+1 & n+2: CRC16 checksum of bytes 1 to n

**Slave normal response:**

| BIT     | 1             | 2    | 3                          | 4                         | 5                         | 6                        | 7             | 8            |
| ------- | ------------- | ---- | -------------------------- | ------------------------- | ------------------------- | ------------------------ | ------------- | ------------ |
| Content | Slave Address | 0x10 | Register Address High Byte | Register Address Low Byte | Register Length High Byte | Register Length Low Byte | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247)
* Byte 2 – 0x10: Write multiple registers function code
* Bytes 3 & 4: Address of the registers written
* Bytes 5 & 6: Length of the registers written (number of registers)
* Bytes 7 & 8: CRC16 checksum of bytes 1 to 6

**Slave exception response:**

| BIT     | 1             | 2    | 3              | 4             | 5            |
| ------- | ------------- | ---- | -------------- | ------------- | ------------ |
| Content | Slave Address | 0x90 | Exception code | CRC High Byte | CRC Low Byte |

💡

Exception code: 0x02 indicates an invalid address in the master request, and 0x03 indicates invalid data in the request.

### **3.4 Query Slave Device ID (0x11)** <a href="#block-346d4c79856d80639084c699115f71d6" id="block-346d4c79856d80639084c699115f71d6"></a>

**Transmitted by master:**

| BIT     | 1             | 2    | 3             | 4            |
| ------- | ------------- | ---- | ------------- | ------------ |
| Content | Slave Address | 0x11 | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247). When only one slave device is connected on the bus, broadcast address 0 is allowed for query.
* Byte 2 – 0x11: Function code
* Bytes 3 & 4: CRC16 checksum of bytes 1 to 2

**Slave normal response:**

| BIT     | 1             | 2    | 3 | 4             | 5                     | 6                    | 7             | 8            |
| ------- | ------------- | ---- | - | ------------- | --------------------- | -------------------- | ------------- | ------------ |
| Content | Slave Address | 0x17 | 3 | Slave Address | Status code High Byte | Status code Low Byte | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247). When only one slave device is connected on the bus, broadcast address 0 is allowed for query.
* Byte 2 – 0x11: Function code
* Bytes 3 & 4: CRC16 checksum of bytes 1 to 2

**Slave exception response:**

* Byte 1 – Slave address: Slave address code (1 to 247)
* Byte 2 – 0x11: Function code
* Byte 3: Number of valid bytes returned
* Byte 4: Slave address code (1 to 247)
* Bytes 6 & 7: Status code
* Bytes 8 & 9: CRC16 checksum of bytes 1 to 6

### **3.5 Restart Slave Device (0x41)** <a href="#block-346d4c79856d80a29ad6dedda8f027d0" id="block-346d4c79856d80a29ad6dedda8f027d0"></a>

**Transmitted by master:**

| BIT     | 1             | 2    | 3             | 4            |
| ------- | ------------- | ---- | ------------- | ------------ |
| Content | Slave Address | 0x41 | CRC High Byte | CRC Low Byte |

* Byte 1 – Slave address: Slave address code (1 to 247). Using 0 as the broadcast address restarts all slave devices on the bus.
* Byte 2 – 0x41: Function code
* Bytes 3 & 4: CRC16 checksum of bytes 1 to 2
