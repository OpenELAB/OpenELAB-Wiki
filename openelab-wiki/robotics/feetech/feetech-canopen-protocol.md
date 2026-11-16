# FEETECH CANopen Protocol

> FEETECH CANopen Protocol

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## 1. **CANopen Network Communication** <a href="#block-345d4c79856d80048c7bd26b3cd40225" id="block-345d4c79856d80048c7bd26b3cd40225"></a>

CANopen is a network transmission application layer protocol based on the CAN bus, following a master-slave communication architecture. Master and slave nodes read/write dictionary content data and exchange other information via Process Data Objects (PDO) and Service Data Objects (SDO). The CiA 301 (DS301) protocol standard defines the basic communication framework of CANopen, while CiA 402 (DS402) defines the specific implementation and standards for drives and motion control. Through this set of standard specifications, motion devices and control devices from different manufacturers can be more easily integrated and used together.

## **2. CIA301** <a href="#block-345d4c79856d80df95e8c340d078f9a6" id="block-345d4c79856d80df95e8c340d078f9a6"></a>

### 2.1 **Communication Identifier** <a href="#block-345d4c79856d80b193cbcfb1d0f9ed67" id="block-345d4c79856d80b193cbcfb1d0f9ed67"></a>

CANopen defines the 11-bit CAN 2.0A ID as: COB-ID = Function code (bits 10–7) + Node address (bits 6–0).

**COB-ID Composition Format**

| 10bit \~ 7bit | 6bit \~ 0bit |
| ------------- | ------------ |
| Function Code | NodeID       |

**COB-ID Allocation Table**

| Communication Object | Function Code | Node ID | COB-ID      |
| -------------------- | ------------- | ------- | ----------- |
| NTM                  | 0000b         | 0       | 0h          |
| SYNC                 | 0001b         | 0       | 80h         |
| EMCY                 | 0001b         | 1 - 127 | 80h+NodeID  |
| TPDO1                | 0011b         | 1 - 127 | 180h+NodeID |
| TPDO2                | 0101b         | 1 - 127 | 280h+NodeID |
| TPDO3                | 0111b         | 1 - 127 | 380h+NodeID |
| TPDO4                | 1001b         | 1 - 127 | 480h+NodeID |
| RPDO1                | 0100b         | 1 - 127 | 200h+NodeID |
| RPDO2                | 0110b         | 1 - 127 | 300h+NodeID |
| RPDO3                | 1000b         | 1 - 127 | 400h+NodeID |
| RPDO4                | 1010b         | 1 - 127 | 500h+NodeID |
| TSDO                 | 1011b         | 1 - 127 | 580h+NodeID |
| RSDO                 | 1100b         | 1 - 127 | 600h+NodeID |
| HeartBeat            | 0100b         | 1 - 127 | 700h+NodeID |
| boot up              | 0100b         | 1 - 127 | 700h+NodeID |

### 2.2 **Network Management (NMT)** <a href="#block-346d4c79856d8020b0f6f04e32160d29" id="block-346d4c79856d8020b0f6f04e32160d29"></a>

NMT (Network Management System) initializes, starts, and stops network nodes. It follows a master-slave architecture and supports only a single NMT master.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ab187346-f931-4481-923d-2b9acf19d519/image/w=1920,quality=90,fit=scale-down" alt="image" height="335.68575842738727" width="418.0874938964844">

**The following NMT commands are defined:**

| NMT Command Code | Description                           | Allowed Communication Objects                                                                          |
| ---------------- | ------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| 0x01             | Node state changes to operational     | SDO, NMT, EMCY, Heartbeat                                                                              |
| 0x02             | Node state changes to stopped         | EMCY, NMT, Heartbeat                                                                                   |
| 0x80             | Node state changes to pre-operational | SDO、PDO、NMT、SYNC、EMECY、Heartbeat                                                                       |
| 0x81             | Reset Node                            | Upon reset, the node enters the Initialization state                                                   |
| 0x82             | Reset Communication                   | Reset communication: Only communication parameters are reset. The node enters the Initialization state |

**The following NMT status codes are defined:**

| NMT Status Code | Description           |
| --------------- | --------------------- |
| 0x00            | Boot-up State         |
| 0x04            | Stopped State         |
| 0x05            | Operational State     |
| 0x7f            | Pre-operational State |

**NMT Message**

| COB-ID | Bit0        | Bit1   |
| ------ | ----------- | ------ |
| 000h   | NMT Command | NodeID |

💡

**Note**: Node ID = 1–127. 0 = broadcast command.

### 2.3 **Service Data Object (SDO)** <a href="#block-346d4c79856d80eb9370c55ca1461992" id="block-346d4c79856d80eb9370c55ca1461992"></a>

SDO is mainly used for parameter configuration of slave nodes by the CANopen master. Service confirmation is the most significant feature of SDO, generating an acknowledgment for each message to ensure data transmission accuracy. In a CANopen system, typically the CANopen slave node acts as the SDO server, and the CANopen master node acts as the client (referred to as CS communication). The SDO client can access the object dictionary on the SDO server via index and subindex. This allows the CANopen master to access parameters of any object dictionary entry on the slave node. Additionally, SDO can transmit data of any length (when the data length exceeds 4 bytes, it is split into multiple messages for transmission).

**SDO Write Operation Format**

| Operation | COB-ID      | Bit0 | Bit1\&Bit2 | Bit3     | Bit4\~Bit7     |
| --------- | ----------- | ---- | ---------- | -------- | -------------- |
| Send      | 600h+NodeID | 23h  | Index      | Subindex | Data (4 bytes) |
| Send      | 600h+NodeID | 27h  | Index      | Subindex | Data (3 bytes) |
| Send      | 600h+NodeID | 2Bh  | Index      | Subindex | Data (2 bytes) |
| Send      | 600h+NodeID | 2Fh  | Index      | Subindex | Data (1 bytes) |
| return    | 580h+NodeID | 60h  | Index      | Subindex | Zero Padding   |
| return    | 580h+NodeID | 80h  | Index      | Subindex | Abort Code     |

**SDO Read Operation Format**

| Operation | COB-ID      | Bit0 | Bit1\&Bit2 | Bit3     | Bit4\~Bit7     |
| --------- | ----------- | ---- | ---------- | -------- | -------------- |
| Send      | 600h+NodeID | 40h  | Index      | Subindex | Zero Padding   |
| return    | 580h+NodeID | 43h  | Index      | Subindex | Data (4 bytes) |
| return    | 580h+NodeID | 47h  | Index      | Subindex | Data (3 bytes) |
| return    | 580h+NodeID | 4Bh  | Index      | Subindex | Data (2 bytes) |
| return    | 580h+NodeID | 4Fh  | Index      | Subindex | Data (1 bytes) |
| return    | 580h+NodeID | 80h  | Index      | Subindex | Abort Code     |

**SDO Abort Code**

| Abort Code  | Description                                    |
| ----------- | ---------------------------------------------- |
| 05 04 00 01 | Invalid or unknown SDO command specifier       |
| 06 01 00 01 | Attempt to read a write-only object            |
| 06 01 00 02 | Attempt to write a read-only object            |
| 06 02 00 00 | Object does not exist in the object dictionary |
| 06 04 00 41 | Object cannot be mapped to PDO                 |
| 06 07 00 12 | Data type mismatch                             |
| 06 09 00 11 | Subindex does not exist                        |
| 06 09 00 30 | Parameter value out of range                   |
| 08 00 00 24 | No data available                              |

### 2.4 Process Data Object (PDO) <a href="#block-346d4c79856d8020ba24e421d2e66afc" id="block-346d4c79856d8020ba24e421d2e66afc"></a>

PDO belongs to process data and is used for unidirectional transmission of real-time data. It does not require acknowledgment CAN messages from receiving nodes to confirm reception, following the producer-consumer model. From the perspective of a slave node, PDOs can be divided into RPDO and TPDO. The final transmission method is determined by both the communication parameters and the mapping parameters.

**RPDO/TPDO mapping object address definition:**

| Bit31\~Bit16 | Bit15\~Bit8 | Bit7\~Bit0 |
| ------------ | ----------- | ---------- |
| Index        | Subindex    | Bit Length |

**PDO object list:**

| Name  | COB-ID      | Communication Object | Mapped Object |
| ----- | ----------- | -------------------- | ------------- |
| RPDO1 | 200h+NodeID | 1400h                | 1600h         |
| RPDO2 | 300h+NodeID | 1401h                | 1601h         |
| RPDO3 | 400h+NodeID | 1402h                | 1602h         |
| RPDO4 | 500h+NodeID | 1403h                | 1603h         |
| TPDO1 | 180h+NodeID | 1800h                | 1A00h         |
| TPDO2 | 280h+NodeID | 1801h                | 1A01h         |
| TPDO3 | 380h+NodeID | 1802h                | 1A02h         |
| TPDO4 | 480h+NodeID | 1803h                | 1A03h         |

**PDO Communication Parameters:** The COB-ID, status bits, transmission type, inhibit time, and event timer related to the PDO can all be configured through the corresponding communication object dictionary.

**PDO Mapping Parameters:** The actual data content of the PDO can be set by configuring the mapping object dictionary corresponding to the PDO.

### 2.5 **Sync Object (SYNC)** <a href="#block-346d4c79856d805e8373f1365dc0fc5b" id="block-346d4c79856d805e8373f1365dc0fc5b"></a>

SYNC object: A mechanism for synchronizing transmission/reception among multiple nodes. Mainly used for synchronous PDO transmission. Configurable via object dictionary: 1005h (SYNC COB-ID), 1006h (Cycle Period), 1007h (Sync Window Length).

| COB-ID | Data |
| ------ | ---- |
| 80h    | None |

### 2.6 **Emergency Object (EMCY)** <a href="#block-346d4c79856d8062bb46dfc6f463b357" id="block-346d4c79856d8062bb46dfc6f463b357"></a>

EMCY: Triggered by internal device errors. Sends error code to NMT master. Diagnostic message, does not affect communication. CAN-ID: stored at index 1014h, typically 080h + NodeID. Data length: 8 bytes.

Upon node fault, update the error register and pre-defined error field. Emergency message content shall adhere to the following specifications:

| COB-ID     | Bit0\&Bit1 | Bit2           | Bit3     | Bit4\~Bit7      |
| ---------- | ---------- | -------------- | -------- | --------------- |
| 80h+NodeID | Error Code | Error Register | Reserved | Auxiliary bytes |

**Error Code:**&#x45;rror code Latest value in pre-defined error field (1003h). See object dictionary for details.

**Error Register:**&#x45;rror register Value in error register (1001h). See object dictionary for details.

**Auxiliary bytes:**&#x41;uxiliary bytes Manufacturer-specific values.

### 2.7 **Special Message** <a href="#block-346d4c79856d80c98992e3d9e73d3715" id="block-346d4c79856d80c98992e3d9e73d3715"></a>

#### 2.7.1 **Boot-up Message** <a href="#block-346d4c79856d80f0b18dd68b7db6dde7" id="block-346d4c79856d80f0b18dd68b7db6dde7"></a>

First power-on message

| COB-ID      | Bit0 |
| ----------- | ---- |
| 700h+NodeID | 00h  |

#### 2.7.2 **Heartbeat Message** <a href="#block-346d4c79856d80758aa7ee9fd1b5e42f" id="block-346d4c79856d80758aa7ee9fd1b5e42f"></a>

**Parameter/Cycle Setting:** The heartbeat period (in milliseconds) is configured via object dictionary index 0x1017. A value of 0 disables the heartbeat function.

**Timeout Mechanism:** The master node defines a timeout threshold for each slave node. If a heartbeat is not received before the timeout expires, the slave node is considered offline, and an error is triggered.

| COB-ID      | Bit0              |
| ----------- | ----------------- |
| 700h+NodeID | Operational State |

## 3 **CIA402** <a href="#block-346d4c79856d809b80eeede7281dadb7" id="block-346d4c79856d809b80eeede7281dadb7"></a>

### 3.1 **State Machine** <a href="#block-346d4c79856d8084b067ef72d820be53" id="block-346d4c79856d8084b067ef72d820be53"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/abc7869a-f02f-4309-a347-7cd9fd4c176d/image/w=1920,quality=90,fit=scale-down" alt="image" height="452.54896373834566" width="418.07501220703125">

### 3.2 **Control Word** <a href="#block-346d4c79856d802f9ba8c598b7f35a1b" id="block-346d4c79856d802f9ba8c598b7f35a1b"></a>

| BIT    | Content | Description             | Note          |
| ------ | ------- | ----------------------- | ------------- |
| 0      | so      | Switch on               | **1 = valid** |
| 1      | ev      | Enable voltage          | Fixed to 1    |
| 2      | qs      | quick stop              | 0 = valid     |
| 3      | eo      | Enable operation        | 1 = valid     |
| 4\~6   | oms     | Operation mode specific | -             |
| 7      | fr      | Fault reset             | 1 = valid     |
| 8      | h       | Halt                    | -             |
| 9      | h       | Operation mode specific | -             |
| 10     | r       | Reserved                | -             |
| 11\~15 | r       | Manufacturer-Specific   | -             |

### 3.3 **Status Word** <a href="#block-346d4c79856d80509a74ed19f345d12a" id="block-346d4c79856d80509a74ed19f345d12a"></a>

| BIT    | Name | Description           | Note       |
| ------ | ---- | --------------------- | ---------- |
| 0      | rtso | Ready                 | Fixed to 1 |
| 1      | so   | Start                 | Fixed to 1 |
| 2      | oe   | Enable operation      | 1 = valid  |
| 3      | f    | Fault                 | 1 = valid  |
| 4      | ve   | Enable voltage        | Fixed to 1 |
| 5      | qs   | Quick stop            | 0 = valid  |
| 6      | sod  | swd                   | Fixed to 1 |
| 7      | w    | Warning               | 1 = valid  |
| 8      | ms   | Manufacturer-specific | -          |
| 9      | rm   | Remote                | Fixed to 1 |
| 10     | tr   | Target reached        | -          |
| 11     | ite  | Limit                 | -          |
| 12\~13 | oms  | Special definition    | -          |
| 14\~15 | ms   | Manufacturer-specific | -          |
