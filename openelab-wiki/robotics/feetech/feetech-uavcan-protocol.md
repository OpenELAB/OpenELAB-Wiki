# FEETECH UAVCAN Protocol

> FEETECH UAVCAN Servo Communication Protocol

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. UAVCAN Protocol Overview** <a href="#block-346d4c79856d81689681e65b2f86988b" id="block-346d4c79856d81689681e65b2f86988b"></a>

UAVCAN is a lightweight protocol based on the CAN 2.0B communication protocol, with a transmission rate of up to 1 Mb/s. It provides a highly reliable communication method for aerospace and robotics applications via the CAN bus. UAVCAN is a decentralized peer-to-peer network in which each peer (node) has a unique digital identifier called NODE\_ID. UAVCAN nodes can communicate using any of the following communication methods:

1. Message broadcasting – The primary method of data exchange with publish/subscribe semantics.
2. Service invocation – A communication method for peer-to-peer request/response interactions.

UAVCAN can automatically split long data into multiple CAN frames using serialized message and service data structures, allowing nodes to exchange data structures of arbitrary size.

The protocol uses CAN 2.0B standard data frames for communication. The factory default CAN baud rate is 1 Mbps, with a configurable range of 10 kbps to 1 Mbps. The communication address (NODE\_ID), CAN baud rate, and node address can be configured via the host computer software.

## **2. UAVCAN Command** <a href="#block-346d4c79856d80b1acdae5f63287fd47" id="block-346d4c79856d80b1acdae5f63287fd47"></a>

**Information Frame Command:**

| **UAVCAN Command** | **UAVCAN Signature**    | **Description**                       |                         |
| ------------------ | ----------------------- | ------------------------------------- | ----------------------- |
| 341(0x0155)        | -                       | Node Status Command                   | Servo Heartbeat Command |
| 1020(0x03FC)       | -                       | Torque Switch Command                 |                         |
| 2011(0x07DB)       | -                       | Single Motor Position Control Command |                         |
| 2012(0x07DC)       | 56 D7 8A D5 6C 8A 65 3A | Multi-Motor Position Control Command  |                         |
| 2013(0x07DD)       | E4 81 9D 8E 5B 7B 80 65 | Data Feedback Command                 | Auto-Report Command     |
| 2014(0x07DE)       | -                       | Auto-Report Start/Stop Command        |                         |

**Service Frame Command:**

| **UAVCAN Command** | **UAVCAN Signature**    | **Description**                                              |
| ------------------ | ----------------------- | ------------------------------------------------------------ |
| 250(0xFA)          | 4F A9 E7 BE A3 6E B3 EC | Parameter Read Command — Big-endian byte order (MSB first).  |
| 251(0xFB)          | 8C E7 80 A1 F9 E4 C7 68 | Parameter Write Command — Big-endian byte order (MSB first). |
| 252(0xFC)          | -                       | Servo Restart Command                                        |

💡

**Note:** When transmitting data in multi-frame format, add the signature to the front of the data for CRC calculation.

### **2.1 Node Status Command** <a href="#block-346d4c79856d804d8e6ed1bb5ad2eab5" id="block-346d4c79856d804d8e6ed1bb5ad2eab5"></a>

|    | **CAN-ID**        | **DLC** | **Data**                                                                                    |
| -- | ----------------- | ------- | ------------------------------------------------------------------------------------------- |
| Rx | 18015500+NODE\_ID | 8       | Frame Counter (4 bytes), Fault Code (1 byte), Status Code (2 bytes), Frame Trailer (1 byte) |

**CAN-ID:** Default value is 0x18015564. The NODE\_ID (servo node ID) default value is 100, with a valid range of 1 to 127. It is used to identify the node status of different servos.

**Frame Counter (4 bytes):** Counter value ranging from 0 to (2³² - 1). The counter increments by one for each transmitted frame.

**Fault Code (1 byte):** Values are as follows:

* Fatal fault: 0xC0 – Magnetic encoder error, undervoltage
* Major fault: 0x40 – Overload, over-temperature
* Minor fault: 0x80 – Overvoltage
* No fault: 0x00Status Code (2 bytes): Refer to the servo status code.Frame Trailer (1 byte): C0 + Transfer\_ID. The Transfer\_ID ranges from 0 to 31 and automatically increments by one for each transmitted frame.

💡

**Note 1:**&#x54;he default auto-report frequency of the node status command is 1 Hz. The frequency can be modified via the FC software.

**Note 2:**&#x54;he NODE\_ID of each servo on the bus must be unique. It can be modified via the FC software.

### **2.2 Torque Switch Command** <a href="#block-346d4c79856d801f836cff0eaea376f3" id="block-346d4c79856d801f836cff0eaea376f3"></a>

|    | **CAN-ID** | **DLC** | **Data**                                                                |
| -- | ---------- | ------- | ----------------------------------------------------------------------- |
| Tx | 1003FC01   | 3       | Servo Channel (1 byte), Torque Command (1 byte), Frame Trailer (1 byte) |

**Servo Channel (1 byte):** Range 0 to 17

**Torque Command (1 byte):** 0 = torque off, 1 = torque on

**Frame Trailer (1 byte):** C0

💡

**Note:** The position command will automatically enable the servo torque. This command can be used to disable the servo torque, allowing the servo to enter a free state.

### **2.3 Single Motor Position Control Command** <a href="#block-346d4c79856d8065ab50cd85b96cdd65" id="block-346d4c79856d8065ab50cd85b96cdd65"></a>

|    | **CAN-ID** | **DLC** | **Data**                                                               |
| -- | ---------- | ------- | ---------------------------------------------------------------------- |
| Tx | 1007DB01   | 4       | Servo Channel (1 byte), Position Data (1 byte), Frame Trailer (1 byte) |

**Servo Channel (1 byte):** Range 0 to 17

**Position Data (2 bytes):** Range -8192 to 8191, corresponding to 360 degrees. 1 LSB = sensor accuracy. Little-endian format. Negative numbers are represented in two’s complement.

**Frame Trailer (1 byte):** C0

💡

**Note:** Default servo channel = 0. Modifiable via FC software.

### **2.4 Multi-Motor Position Control Command** <a href="#block-346d4c79856d80d3a7edd5dc8abd2c62" id="block-346d4c79856d80d3a7edd5dc8abd2c62"></a>

#### **2.4.1 Control fewer than 3 servos** <a href="#block-346d4c79856d803d9db0e67861e37a91" id="block-346d4c79856d803d9db0e67861e37a91"></a>

|    | **CAN-ID** | **DLC** | **Data**                                                                                                         |
| -- | ---------- | ------- | ---------------------------------------------------------------------------------------------------------------- |
| Tx | 1007DC01   | 7       | Channel 0 Position (2 bytes), Channel 1 Position (2 bytes), Channel 2 Position (2 bytes), Frame Trailer (1 byte) |

**Channel x Position (2 bytes):** x ranges from 0 to 2. Position range: -8192 to 8191, corresponding to 360 degrees. 1 LSB = sensor accuracy. Little-endian format. Negative numbers are represented in two’s complement.

**Frame Trailer (1 byte):** C0

💡

**Note:** The servo channel in the command can only be from 0 to 2.

#### **2.4.2 Control more than 3 servos** <a href="#block-346d4c79856d80088b9ce94e2f3bb174" id="block-346d4c79856d80088b9ce94e2f3bb174"></a>

|     | **CAN-ID** | **DLC** | **Data**                                                                                                                                         |
| --- | ---------- | ------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Tx1 | 1007DC01   | 8       | Checksum (2 bytes), channel 0 position (2 bytes), channel 1 position (2 bytes), channel 2 position (low byte), frame tail (1 byte)               |
| Tx2 | 1007DC01   | 8       | channel 2 position (high byte), channel 3 position (2 bytes), channel 4 position (2 bytes), channel 5 position (2 bytes), frame tail (1 byte)    |
| Tx3 | 1007DC01   | 8       | channel 6 position (2 bytes), channel 7 position (2 bytes), channel 8 position (2 bytes), channel 9 position (low byte), frame tail (1 byte)     |
| Tx4 | 1007DC01   | 8       | channel 9 position (high byte), channel 10 position (2 bytes), channel 11 position (2 bytes), channel 12 position (2 bytes), frame tail (1 byte) |
| Tx5 | 1007DC01   | 8       | channel 13 position (2 bytes), channel 14 position (2 bytes), channel 15 position (2 bytes), channel 16 position (low byte), frame tail (1 byte) |
| Tx6 | 1007DC01   | 4       | channel 16 position (high byte), channel 17 position (2 bytes), frame tail (1 byte)                                                              |

**Checksum (2 bytes):** Refer to the checksum section.

**Channel x Position (2 bytes):** x ranges from 0 to 17. Position range: -8192 to 8191, corresponding to 360 degrees. 1 LSB = sensor accuracy. Little-endian format. Negative numbers are represented in two’s complement.

**Frame Trailer (1 byte):**

* Tx1: 0x80 – Start frame, BIT5 = 0
* Tx2: 0x20 – Intermediate frame, BIT5 toggled relative to the previous frame
* Tx3: 0x00 – Intermediate frame, BIT5 toggled relative to the previous frame
* Tx4: 0x20 – Intermediate frame, BIT5 toggled relative to the previous frame
* Tx5: 0x00 – Intermediate frame, BIT5 toggled relative to the previous frame
* Tx6: 0x60 – End frame, BIT5 toggled relative to the previous frame

💡

**Note:** The above command can control up to 18 servos. In practical applications, the command can be adjusted (increased or decreased) according to the number of servo channels.

### **2.5 Auto-Report Data Feedback Command** <a href="#block-346d4c79856d8041a216e4674d2fb897" id="block-346d4c79856d8041a216e4674d2fb897"></a>

|     | **CAN-ID**        | **DLC** | **Data**                                                                                                                                                       |
| --- | ----------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Rx1 | 1807DD00+NODE\_ID | 8       | Checksum (2 bytes), servo channel (1 byte), target position (2 bytes), current position (2 bytes), frame tail (1 byte)                                         |
| Rx2 | 1807DD00+NODE\_ID | 8       | Servo voltage (2 bytes), servo current (2 bytes), servo PCB temperature (1 byte), servo motor temperature (1 byte), servo status (1 byte), frame tail (1 byte) |

CAN-ID: Default value is 0x1807DD64. The NODE\_ID (servo node ID) default value is 100, with a valid range of 1 to 127. It can be modified via the FC software and is used to identify node feedback data from different servos.

**Servo Channel (1 byte):** Range 0 to 17. The default servo channel is 0 and can be modified via the FC software.

**Target Position (2 bytes):** Range -8192 to 8191, corresponding to 360 degrees. 1 LSB = sensor accuracy. Little-endian format. Negative numbers are represented in two’s complement.

**Current Position (2 bytes):** Range -8192 to 8191, corresponding to 360 degrees. 1 LSB = sensor accuracy. Little-endian format. Negative numbers are represented in two’s complement.

**Servo Voltage (2 bytes):** 1 LSB = 0.1 V.

**Servo Current (2 bytes):** 1 LSB = accuracy of the current sampling circuit.

**Servo PCB Temperature (1 byte):** Temperature of the MOS on the servo PCB. 1 LSB = 1°C.

**Servo Motor Temperature (1 byte):** 1 LSB = 1°C. This data is invalid if the servo motor does not have a temperature sensor.

**Servo Status (1 byte):**

* Bit 0: 0 = normal, 1 = driver operating abnormal (e.g., magnetic encoder error). Automatically recovers when normal.
* Bit 1: 0 = normal, 1 = UAVCAN command error, CRC error, invalid command, or invalid frame. Automatically recovers upon receiving a valid command.
* Bit 2: 0 = normal, 1 = motor torque disabled.
* Bit 3: 0 = normal, 1 = motor stalled or overloaded. Automatically recovers when torque returns to normal.
* Bit 4: 0 = normal, 1 = driver MOS overheated. Automatically recovers when temperature returns to normal.
* Bit 5: 0 = abnormal, 1 = motor overheated. Automatically recovers when temperature returns to normal.
* Bit 6: 0 = normal, 1 = undervoltage or overvoltage. Automatically recovers when voltage returns to normal.

**Frame Trailer (1 byte):**

* Rx1: 0x80 + Transfer\_ID — Start frame, BIT5 = 0
* Rx2: 0x60 + Transfer\_ID — End frame, BIT5 toggled relative to the previous frame

Transfer\_ID ranges from 0 to 31. The Transfer\_ID is the same for both frame trailers above. After every two complete frames are received, the Transfer\_ID automatically increments by one.

💡

**Note 1:** The default auto-report frequency of the data feedback command is 10 Hz. The frequency can be modified via the FC software.

💡

**Note 2:** The NODE\_ID of each servo on the bus must be unique. Servo channels can be the same; the same channel generally refers to servos that perform the same action. Both the servo NODE\_ID and the servo channel can be modified via the FC software.

### **2.6 Auto-Report Start/Pause Command** <a href="#block-346d4c79856d808c819cf0d00bb1422a" id="block-346d4c79856d808c819cf0d00bb1422a"></a>

|    | **CAN-ID** | **DLC** | **Data**                                                                 |
| -- | ---------- | ------- | ------------------------------------------------------------------------ |
| Tx | 1007DE01   | 3       | Servo NODE\_ID (1 byte), Switch Command (1 byte), Frame Trailer (1 byte) |

**Servo NODE\_ID (1 byte):** Range 0 to 127. 0 indicates all servos.

**Torque Command (1 byte):** 0 = pause, 5 = start.

**Frame Trailer (1 byte):** C0

### **2.7 Parameter Write Command** <a href="#block-347d4c79856d80dab6bfdc699454f9ee" id="block-347d4c79856d80dab6bfdc699454f9ee"></a>

|    | **CAN-ID**             | **DLC** | **Data**                                                                                                                                  |
| -- | ---------------------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Tx | 10FB8081+(NODE\_ID<<8) | 4+L\*2  | Parameter Address (2 bytes), Parameter Length L (1 byte), Parameter Data 1 (2 bytes) … Parameter Data L (2 bytes), Frame Trailer (1 byte) |
| Rx | 10FB0180+NODE\_ID      | 2       | Write Status (1 byte), Frame Trailer (1 byte)                                                                                             |

CAN-ID:

* Tx: 0x10FB8081 + (NODE\_ID << 8). Default NODE\_ID is 100. Default CAN-ID is 0x10FBE481.
* Rx: 0x10FB0180 + NODE\_ID. Default NODE\_ID is 100. Default CAN-ID is 0x10FB01E4.

**Parameter Address (2 bytes):** Refer to the memory table address.

**Parameter Length L (1 byte):** Length of the parameter (L).

**Parameter Data 1 (2 bytes):** Refer to the memory table data.

**Parameter Data L (2 bytes):** Refer to the memory table data. L ≤ 2.

**Write Status (1 byte):** 0 = normal, 1 = invalid address, 2 = invalid parameter.

**Frame Trailer (1 byte):** C0

### **2.8 Parameter Read Command** <a href="#block-347d4c79856d80148caece8300d5d172" id="block-347d4c79856d80148caece8300d5d172"></a>

|    | **CAN-ID**             | **DLC** | **Data**                                                                                                                           |
| -- | ---------------------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Tx | 10FA8081+(NODE\_ID<<8) | 4       | Parameter Address (2 bytes), Parameter Length L (1 byte), Frame Trailer (1 byte)                                                   |
| Rx | 10FA0180+NODE\_ID      | 3+L\*2  | Read Status (1 byte), Parameter Length L (1 byte), Parameter Data 1 (2 bytes) … Parameter Data L (2 bytes), Frame Trailer (1 byte) |

CAN-ID:

* Tx: 0x10FA8081 + (NODE\_ID << 8). Default NODE\_ID is 100. Default CAN-ID is 0x10FAE481.
* Rx: 0x10FA0180 + NODE\_ID. Default NODE\_ID is 100. Default CAN-ID is 0x10FA01E4.

**Parameter Address (2 bytes):** Refer to the memory table address.

**Parameter Length L (1 byte):** Length of the parameter (L).

**Parameter Data (2 bytes):** Refer to the memory table data.

**Parameter Data L (2 bytes):** Refer to the memory table data. L ≤ 2.

**Write Status (1 byte):** 0 = normal, 1 = invalid address, 2 = invalid parameter.

**Frame Trailer (1 byte):** C0

## **3. UAVCAN Protocol CRC Check** <a href="#block-347d4c79856d80baacb9d44322584cb1" id="block-347d4c79856d80baacb9d44322584cb1"></a>

💡

**Note:** This section applies to the checksum calculation in multi-frame commands. It can be skipped for single-frame commands.

**The multi-frame data composition is as follows:**

| UAVCAN Data Frame 1 | UAVCAN Data Frame 2 | … | UAVCAN Data Frame N |
| ------------------- | ------------------- | - | ------------------- |
| Byte0 \~ Byte7      | Byte0 \~ Byte7      | … | Byte0 \~ ByteX      |

**UAVCAN Data Frame 1:** Byte 0 and Byte 1 are the CRC checksum (little-endian format). Bytes 2 to 6 are valid data. Byte 7 is the frame trailer.

**UAVCAN Data Frame 2:** Bytes 0 to 6 are valid data. Byte 7 is the frame trailer.

**UAVCAN Data Frame N:** Bytes 0 to (X-1) are valid data. Byte X is the frame trailer, where X < 8.

**The data composition for CRC calculation is as follows:**

| UAVCAN Signature    | UAVCAN Data Frame 1 | UAVCAN Data Frame 2 | … | UAVCAN Data Frame N |
| ------------------- | ------------------- | ------------------- | - | ------------------- |
| Signature (8 bytes) | Byte2 \~ Byte6      | Byte2 \~ Byte6      | … | Byte0 \~ Byte（X-1）  |

UAVCAN Signature: The signature varies for different commands. For detailed signature encoding, refer to the UAVCAN command documentation.

**UAVCAN Data Frame 1:** Bytes 2 to 6 (valid data) are included in the CRC calculation.

**UAVCAN Data Frame 2:** Bytes 0 to 6 (valid data) are included in the CRC calculation.

**UAVCAN Data Frame N:** Bytes 0 to (X-1) (valid data) are included in the CRC calculation.

**The CRC check algorithm is as follows:**

* CRC Format: CRC-16-CCITT-FALSE
* Initial value: 0xFFFF
* Polynomial: 0x1021
* Reflection: No
* XOR: 0

Copy

```c
#include <stdint.h>
#include <stddef.h>

#define CRC16_CCITT_FALSE_INIT 0xFFFF
#define CRC16_CCITT_FALSE_POLY 0x1021

static const uint16_t crc16_ccitt_false_table[256] = {
0x0000, 0x1021, 0x2042, 0x3063, 0x4084, 0x50A5, 0x60C6, 0x70E7,
0x8108, 0x9129, 0xA14A, 0xB16B, 0xC18C, 0xD1AD, 0xE1CE, 0xF1EF,
0x1231, 0x0210, 0x3273, 0x2252, 0x52B5, 0x4294, 0x72F7, 0x62D6,
0x9339, 0x8318, 0xB37B, 0xA35A, 0xD3BD, 0xC39C, 0xF3FF, 0xE3DE,
0x2462, 0x3443, 0x0420, 0x1401, 0x64E6, 0x74E7, 0x4484, 0x54A5,
0xA54A, 0xB56B, 0x8508, 0x9529, 0xE5CE, 0xF5EF, 0xC58C, 0xD5AD,
0x3653, 0x2672, 0x1611, 0x0630, 0x76D7, 0x66F6, 0x5695, 0x46B4,
0xB75B, 0xA77A, 0x9719, 0x8738, 0xF7DF, 0xE7FE, 0xD79D, 0xC7BC,
0x48C4, 0x58E5, 0x6886, 0x78A7, 0x0840, 0x1861, 0x2802, 0x3823,
0xC9CC, 0xD9ED, 0xE98E, 0xF9AF, 0x8948, 0x9969, 0xA90A, 0xB92B,
0x5AF5, 0x4AD4, 0x7AB7, 0x6A96, 0x1A71, 0x0A50, 0x3A33, 0x2A12,
0xDBFD, 0xCBDC, 0xFBBF, 0xEB9E, 0x9B79, 0x8B58, 0xBB3B, 0xAB1A,
0x6CA6, 0x7C87, 0x4CE4, 0x5CC5, 0x2C22, 0x3C03, 0x0C60, 0x1C41,
0xEDAE, 0xFD8F, 0xCDEC, 0xDDCD, 0xAD2A, 0xBD0B, 0x8D68, 0x9D49,
0x7E97, 0x6EB6, 0x5ED5, 0x4EF4, 0x3E13, 0x2E32, 0x1E51, 0x0E70,
0xFF9F, 0xEFBE, 0xDFDD, 0xCFFC, 0xBF1B, 0xAF3A, 0x9F59, 0x8F78,
0x9188, 0x81A9, 0xB1CA, 0xA1EB, 0xD10C, 0xC12D, 0xF14E, 0xE16F,
0x1080, 0x00A1, 0x30C2, 0x20E3, 0x5004, 0x4025, 0x7046, 0x6067,
0x83B9, 0x9398, 0xA3FB, 0xB3DA, 0xC33D, 0xD31C, 0xE37F, 0xF35E,
0x02B1, 0x1290, 0x22F3, 0x32D2, 0x4235, 0x5214, 0x6277, 0x7256,
0xB5EA, 0xA5CB, 0x95A8, 0x8589, 0xF56E, 0xE54F, 0xD52C, 0xC50D,
0x34E2, 0x24C3, 0x14A0, 0x0481, 0x7466, 0x6447, 0x5424, 0x4405,
0xA7DB, 0xB7FA, 0x8799, 0x97B8, 0xE75F, 0xF77E, 0xC71D, 0xD73C,
0x26D3, 0x36F2, 0x0691, 0x16B0, 0x6657, 0x7676, 0x4615, 0x5634,
0xD94C, 0xC96D, 0xF90E, 0xE92F, 0x99C8, 0x89E9, 0xB98A, 0xA9AB,
0x5844, 0x4865, 0x7806, 0x6827, 0x18C0, 0x08E1, 0x3882, 0x28A3,
0xCB7D, 0xDB5C, 0xEB3F, 0xFB1E, 0x8BF9, 0x9BD8, 0xABBB, 0xBB9A,
0x4A75, 0x5A54, 0x6A37, 0x7A16, 0x0AF1, 0x1AD0, 0x2AB3, 0x3A92,
0xFD2E, 0xED0F, 0xDD6C, 0xCD4D, 0xBDAA, 0xAD8B, 0x9DE8, 0x8DC9,
0x7C26, 0x6C07, 0x5C64, 0x4C45, 0x3CA2, 0x2C83, 0x1CE0, 0x0CC1,
0xEF1F, 0xFF3E, 0xCF5D, 0xDF7C, 0xAF9B, 0xBFBA, 0x8FD9, 0x9FF8,
0x6E17, 0x7E36, 0x4E55, 0x5E74, 0x2E93, 0x3EB2, 0x0ED1, 0x1EF0
};

uint16_t crc16_ccitt_false_update(uint16_t crc, const uint8_t *data, size_t len)
{
    for (size_t i = 0; i < len; i++) 
    {
        crc = (crc << 8) ^ crc16_ccitt_false_table[((crc >> 8) ^ data[i]) & 0xFF];
    }
    return crc;
}

uint16_t uavcan_compute_transfer_crc(const uint8_t *data_type_signature,
const uint8_t *payload,
size_t payload_len)
{
    uint16_t crc = CRC16_CCITT_FALSE_INIT;
    crc = crc16_ccitt_false_update(crc, data_type_signature, 8);
    crc = crc16_ccitt_false_update(crc, payload, payload_len);
    return crc;
}
```
