# FEETECH SHC Servo – Memory Table Analysis

> FEETECH SHC Servo – Memory Table Analysis

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/support.html)

## **1. Communication Protocol** <a href="#block-345d4c79856d81af9042c4ac4e985aa4" id="block-345d4c79856d81af9042c4ac4e985aa4"></a>

The servo uses the CANopen communication protocol. The factory default CAN baud rate is 125 kbps. The configurable baud rate range is 20 kbps to 1 Mbps. The default communication node ID is 1.

The SDO (Service Data Object) is used to access all entries in the object dictionary for parameter configuration of the servo.

The PDO (Process Data Object) is used for high-speed real-time control of the servo to enable servo operation.

The SYNC signal is used to synchronize and broadcast real-time status updates of all servos on the CAN bus.

RPDO1 is mapped by default to the control word and operation mode object, used for torque enable/disable and mode configuration.

RPDO2 is mapped by default to the target position object for position control.

RPDO3 is mapped by default to the target velocity object for velocity control.

RPDO4 is mapped by default to the rated current object for current-based servo control.

TPDO2 is mapped by default to the real-time position feedback object. Using the SYNC signal enables real-time position feedback from all servos on the bus.

TPDO1, TPDO3, and TPDO4 are disabled by default.

## **2. Object Dictionary** <a href="#block-345d4c79856d80b8916ac7813bfc4ce2" id="block-345d4c79856d80b8916ac7813bfc4ce2"></a>

The CANopen Object Dictionary (OD: Object Dictionary) is the core concept of the CANopen protocol. It is an ordered collection of objects that describes all parameters of a CANopen node, including the storage locations of communication data. Each object is addressed via an index and sub-index.

### 2.1 Communication Object Sub-Protocol Area <a href="#block-345d4c79856d807b9f63cfa9806f4418" id="block-345d4c79856d807b9f63cfa9806f4418"></a>

| Index | Sub Index | Object                        | Access | Type | Unit  | Default     | PDO Mapping | Description                                                                                                                                |
| ----- | --------- | ----------------------------- | ------ | ---- | ----- | ----------- | ----------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| 1000h | 00h       | Device Type                   | RO     | U32  | –     | 00020192h   | –           | CIA402 device standard value                                                                                                               |
| 1001h | 00h       | Error Register                | RO     | U8   | –     | 0           | TPDO        | See special byte bit parsing                                                                                                               |
| 1002h | 00h       | Servo Status                  | RO     | U32  | –     | 0           | TPDO        | Servo custom status, see special byte bit parsing                                                                                          |
| 1003h | 00h       | Pre-defined Error Field       | RW     | U8   | –     | 0           | –           | Number of error occurrences, writing 00h clears error history, writing non-zero returns SDO abort 0x06090030, see special byte bit parsing |
| 1003h | 01h       | Pre-defined Error Field-1     | RO     | U32  | –     | 0           | –           | No error, reading returns SDO abort 0x08000024                                                                                             |
| 1003h | 02h       | Pre-defined Error Field-2     | RO     | U32  | –     | 0           | –           | No error, reading returns SDO abort 0x08000024                                                                                             |
| 1003h | 03h       | Pre-defined Error Field-3     | RO     | U32  | –     | 0           | –           | No error, reading returns SDO abort 0x08000024                                                                                             |
| 1003h | 04h       | Pre-defined Error Field-4     | RO     | U32  | –     | 0           | –           | No error, reading returns SDO abort 0x08000024                                                                                             |
| 1003h | 05h       | Pre-defined Error Field-5     | RO     | U32  | –     | 0           | –           | No error, reading returns SDO abort 0x08000024                                                                                             |
| 1005h | 00h       | SYNC Message COB-ID           | RO     | U32  | –     | 00000080h   | –           | SYNC COB-ID not allowed to be modified                                                                                                     |
| 1008h | 00h       | Manufacturer Name             | RO     | str  | –     | –           | –           | 15-byte string                                                                                                                             |
| 1009h | 00h       | Hardware Model                | RO     | str  | –     | –           | –           | 15-byte string                                                                                                                             |
| 1010h | 00h       | Save Parameters               | RO     | U8   | –     | 1           | –           | Save parameter entry                                                                                                                       |
| 1010h | 01h       | Save All Parameters           | RW     | U32  | –     | –           | –           | "save" saves all parameters to EPROM                                                                                                       |
| 1011h | 00h       | Restore Parameters            | RO     | U8   | –     | 1           | –           | Restore parameter entry                                                                                                                    |
| 1011h | 01h       | Restore All Parameters        | RW     | U32  | –     | –           | –           | "load" restores all parameters to default                                                                                                  |
| 1014h | 00h       | EMCY Message COB-ID           | RO     | U32  | –     | 80h+NodeID  | –           | Emergency message COB-ID                                                                                                                   |
| 1017h | 00h       | Producer Heartbeat Time       | RW     | U16  | 100ms | 0           | –           | 0 means heartbeat disabled                                                                                                                 |
| 1018h | 00h       | Identity Object               | RO     | U8   | –     | 4           | –           | Identity object                                                                                                                            |
| 1018h | 01h       | Vendor ID                     | RO     | U32  | –     | –           | –           | Vendor ID                                                                                                                                  |
| 1018h | 02h       | Device Model                  | RO     | U32  | –     | –           | –           | Device model                                                                                                                               |
| 1018h | 03h       | Firmware Version              | RO     | U32  | –     | –           | –           | Firmware version                                                                                                                           |
| 1018h | 04h       | Serial Number                 | RO     | U32  | –     | –           | –           | Serial number                                                                                                                              |
| 1200h | 00h       | SDO Service Parameter         | RO     | U8   | –     | 2           | –           | SDO service parameter                                                                                                                      |
| 1200h | 01h       | TxSDO Object                  | RO     | U32  | –     | NodeID+600h | –           | Transmit SDO object                                                                                                                        |
| 1200h | 02h       | RxSDO Object                  | RO     | U32  | –     | NodeID+580h | –           | Receive SDO object                                                                                                                         |
| 1400h | 00h       | RPDO1 Communication Parameter | RO     | U8   | –     | 2           | –           | RPDO1 communication parameter                                                                                                              |
| 1400h | 01h       | RPDO1 Object                  | RO     | U32  | –     | NodeID+200h | –           | RPDO1 object                                                                                                                               |
| 1400h | 02h       | Transmission Type             | RO     | U8   | –     | FF          | –           | Servo updates data immediately after receiving RPDO                                                                                        |
| 1401h | 00h       | RPDO2 Communication Parameter | RO     | U8   | –     | 2           | –           | RPDO2 communication parameter                                                                                                              |
| 1401h | 01h       | RPDO2 Object                  | RO     | U32  | –     | NodeID+300h | –           | RPDO2 object                                                                                                                               |
| 1401h | 02h       | Transmission Type             | RO     | U8   | –     | FF          | –           | Servo updates data immediately after receiving RPDO                                                                                        |
| 1402h | 00h       | RPDO3 Communication Parameter | RO     | U8   | –     | 2           | –           | RPDO3 communication parameter                                                                                                              |
| 1402h | 01h       | RPDO3 Object                  | RO     | U32  | –     | NodeID+400h | –           | RPDO3 object                                                                                                                               |
| 1402h | 02h       | Transmission Type             | RO     | U8   | –     | FF          | –           | Servo updates data immediately after receiving RPDO                                                                                        |
| 1403h | 00h       | RPDO4 Communication Parameter | RO     | U8   | –     | 2           | –           | RPDO4 communication parameter                                                                                                              |
| 1403h | 01h       | RPDO4 Object                  | RO     | U32  | –     | NodeID+500h | –           | RPDO4 object                                                                                                                               |
| 1403h | 02h       | Transmission Type             | RO     | U8   | –     | FF          | –           | Servo updates data immediately after receiving RPDO                                                                                        |
| 1600h | 00h       | RPDO1 Mapping Parameter       | RW     | U8   | –     | 2           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1600h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x60400010  | –           | Mapped object address                                                                                                                      |
| 1600h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | 0x60600008  | –           | Mapped object address                                                                                                                      |
| 1600h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1600h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1601h | 00h       | RPDO2 Mapping Parameter       | RW     | U8   | –     | 1           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1601h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x607a0020  | –           | Mapped object address                                                                                                                      |
| 1601h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1601h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1601h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1602h | 00h       | RPDO3 Mapping Parameter       | RW     | U8   | –     | 1           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1602h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x60ff0020  | –           | Mapped object address                                                                                                                      |
| 1602h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1602h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1602h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1603h | 00h       | RPDO4 Mapping Parameter       | RW     | U8   | –     | 1           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1603h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x60750020  | –           | Mapped object address                                                                                                                      |
| 1603h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1603h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1603h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1800h | 00h       | TPDO1 Communication Parameter | RO     | U8   | –     | 2           | –           | TPDO1 communication parameter                                                                                                              |
| 1800h | 01h       | TPDO1 Object                  | RO     | U32  | –     | NodeID+180h | –           | TPDO1 object                                                                                                                               |
| 1800h | 02h       | Transmission Type             | RO     | U8   | –     | 1           | –           | Servo returns TPDO immediately after receiving SYNC                                                                                        |
| 1801h | 00h       | TPDO2 Communication Parameter | RO     | U8   | –     | 2           | –           | TPDO2 communication parameter                                                                                                              |
| 1801h | 01h       | TPDO2 Object                  | RO     | U32  | –     | NodeID+280h | –           | TPDO2 object                                                                                                                               |
| 1801h | 02h       | Transmission Type             | RO     | U8   | –     | 1           | –           | Servo returns TPDO immediately after receiving SYNC                                                                                        |
| 1802h | 00h       | TPDO3 Communication Parameter | RO     | U8   | –     | 2           | –           | TPDO3 communication parameter                                                                                                              |
| 1802h | 01h       | TPDO3 Object                  | RO     | U32  | –     | NodeID+380h | –           | TPDO3 object                                                                                                                               |
| 1802h | 02h       | Transmission Type             | RO     | U8   | –     | 1           | –           | Servo returns TPDO immediately after receiving SYNC                                                                                        |
| 1803h | 00h       | TPDO4 Communication Parameter | RO     | U8   | –     | 2           | –           | TPDO4 communication parameter                                                                                                              |
| 1803h | 01h       | TPDO4 Object                  | RO     | U32  | –     | NodeID+480h | –           | TPDO4 object                                                                                                                               |
| 1803h | 02h       | Transmission Type             | RO     | U8   | –     | 1           | –           | Servo returns TPDO immediately after receiving SYNC                                                                                        |
| 1A00h | 00h       | TPDO1 Mapping Parameter       | RW     | U8   | –     | 0           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1A00h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x60410010  | –           | Mapped object address                                                                                                                      |
| 1A00h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | 0x60610008  | –           | Mapped object address                                                                                                                      |
| 1A00h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | 0x603f0010  | –           | Mapped object address                                                                                                                      |
| 1A00h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A01h | 00h       | TPDO2 Mapping Parameter       | RW     | U8   | –     | 1           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1A01h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x60630020  | –           | Mapped object address                                                                                                                      |
| 1A01h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | 0x606c0020  | –           | Mapped object address                                                                                                                      |
| 1A01h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A01h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A02h | 00h       | TPDO3 Mapping Parameter       | RW     | U8   | –     | 0           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1A02h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | 0x60780010  | –           | Mapped object address                                                                                                                      |
| 1A02h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A02h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A02h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A03h | 00h       | TPDO4 Mapping Parameter       | RW     | U8   | –     | 0           | –           | Number of mapped objects, 0 disables mapping, range 0–4                                                                                    |
| 1A03h | 01h       | Mapped Object Address 1       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A03h | 02h       | Mapped Object Address 2       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A03h | 03h       | Mapped Object Address 3       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |
| 1A03h | 04h       | Mapped Object Address 4       | RW     | U32  | –     | –           | –           | Mapped object address                                                                                                                      |

### 2.2 Manufacturer-Specific Sub-protocol Area <a href="#block-345d4c79856d80eb9044e1f9fb752005" id="block-345d4c79856d80eb9044e1f9fb752005"></a>

| Index | Sub Index | Object                             | Access  | Type | Unit       | Default | PDO Mapping | Description                                                                                                                   |
| ----- | --------- | ---------------------------------- | ------- | ---- | ---------- | ------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 2000h | 00h       | Servo NodeId                       | RW      | S8   | –          | 1       | –           | Takes effect immediately                                                                                                      |
| 2001h | 00h       | Servo Baudrate                     | RW      | U8   | –          | 4       | –           | 0-8 represent baudrate: 10k(0), 20k(1), 50k(2), 100k(3), 125k(4), 250k(5), 500k(6), 800k(7), 1M(8), takes effect after reboot |
| 2002h | 00h       | Communication Timeout              | RW      | U8   | ms         | 50      | –           |                                                                                                                               |
| 2003h | 00h       | Default Mode                       | RW      | S8   | –          | 1       | –           | See special byte bit parsing                                                                                                  |
| 2004h | 00h       | Torque Limit                       | RW      | S16  | 0.02%      | 4800    | –           |                                                                                                                               |
| 2005h | 00h       | Startup Torque                     | RW      | S16  | 0.02%      | 0       | –           | Range: 0 \~ 255                                                                                                               |
| 2006h | 00h       | Position Deadband                  | RW      | U8   | 0.022deg   | 2       | –           | Minimum unit is smallest resolution angle                                                                                     |
| 2007h | 00h       | Min Angle Limit                    | RW      | S16  | 0.022deg   | 0       | –           | In multi-turn absolute mode this value is 0                                                                                   |
| 2008h | 00h       | Max Angle Limit                    | RW      | S16  | 0.022deg   | 0       | –           | In multi-turn absolute mode this value is 0                                                                                   |
| 2009h | 00h       | Position Offset                    | RW      | S16  | 0.022deg   | 0       | –           | Minimum unit is smallest resolution angle                                                                                     |
| 200Ah | 00h       | Servo Phase                        | RW      | U16  | –          | –       | –           | Do not modify without special requirement, see special byte bit parsing                                                       |
| 200Bh | 00h       | Protection Switch                  | RW      | U16  | –          | 7       | –           | Each bit 1 enables protection, 0 disables protection, see special byte bit parsing                                            |
| 200Ch | 00h       | LED Alarm Condition                | RW      | U16  | –          | 15      | –           | Each bit 1 enables LED alarm, 0 disables, see special byte bit parsing                                                        |
| 200Dh | 00h       | Max Temperature Limit              | RW      | U16  | °C         | 70      | –           | Maximum operating temperature limit, unit 1°C                                                                                 |
| 200Eh | 00h       | Min Input Voltage                  | RW      | U16  | 0.1V       | –       | –           | Example: 40 means 4.0V minimum operating voltage                                                                              |
| 200Fh | 00h       | Max Input Voltage                  | RW      | U16  | 0.1V       | –       | –           | Example: 260 means 26.0V maximum operating voltage                                                                            |
| 2010h | 00h       | Overload Current                   | RW      | U16  | 6.5mA      | –       | –           | Servo overload protection current                                                                                             |
| 2011h | 00h       | Overcurrent Protection Time        | RW      | U16  | 1ms        | 3000    | –           | Maximum allowed time over overload current                                                                                    |
| 2012h | 00h       | Protection Torque                  | RW      | U16  | –          | 0       | –           | Reserved                                                                                                                      |
| 2013h | 00h       | Overload Torque                    | RW      | U16  | –          | 0       | –           | Reserved                                                                                                                      |
| 2014h | 00h       | Overload Protection Time           | RW      | U16  | –          | 0       | –           | Reserved                                                                                                                      |
| 2015h | 00h       | Position Loop P Gain               | RW      | U16  | –          | 48      | –           | Position mode (Mode 1), proportional gain                                                                                     |
| 2016h | 00h       | Position Loop D Gain               | RW      | U16  | –          | 32      | –           | Position mode (Mode 1), derivative gain                                                                                       |
| 2017h | 00h       | Position Loop I Gain               | RW      | U16  | –          | 0       | –           | Position mode (Mode 1), integral gain                                                                                         |
| 2018h | 00h       | Position Loop Integral Limit       | RW      | U16  | –          | 0       | –           | Max integral limit, 0 means no limit                                                                                          |
| 2019h | 00h       | Velocity Loop P Gain               | RW      | U16  | –          | 100     | –           | Velocity mode (Mode 3), proportional gain                                                                                     |
| 201Ah | 00h       | Velocity Loop I Gain               | RW      | U16  | –          | 100     | –           | Velocity mode (Mode 3), integral gain                                                                                         |
| 201Bh | 00h       | Current Loop P Gain                | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 201Ch | 00h       | Current Loop I Gain                | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 201Dh | 00h       | Max Speed Limit                    | RW      | U16  | 0.183rpm   | –       | –           | Factory default parameter                                                                                                     |
| 201Eh | 00h       | Max Acceleration Limit             | RW      | U16  | 0.366rpm/s | –       | –           | Factory default parameter                                                                                                     |
| 201Fh | 00h       | Rated Current Limit                | RW      | U16  | 6.5mA      | –       | –           | Factory default parameter                                                                                                     |
| 2020h | 00h       | Max Torque Limit                   | RW      | S16  | –          | 5000    | –           | Do not modify without special requirement                                                                                     |
| 2021h | 00h       | H-Bridge Dead Time                 | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2022h | 00h       | Differential Control Time          | RW      | U16  | ms         | –       | –           | Factory default parameter                                                                                                     |
| 2023h | 00h       | Current Sampling Window Time       | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2024h | 00h       | Motion Detection Threshold         | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2025h | 00h       | Six-Step Commutation Threshold     | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2026h | 00h       | Velocity Derivative Time           | RW      | U16  | ms         | 20      | –           | Factory default parameter                                                                                                     |
| 2027h | 00h       | Position Filter Coefficient        | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2028h | 00h       | Velocity Filter Coefficient        | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2029h | 00h       | Bus Current Filter Coefficient     | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 202Ah | 00h       | Position Loop D Filter Coefficient | RW      | U16  | –          | –       | –           | Factory default parameter                                                                                                     |
| 202Bh | 00h       | Current Voltage                    | RO      | S16  | 0.1V       | ?       | TPDO        | Current servo operating voltage                                                                                               |
| 202Ch | 00h       | Current Temperature                | RO      | S16  | °C         | ?       | TPDO        | Current internal temperature                                                                                                  |
| 202Eh | 00h       | Magnetic Encoder Status Code       | RO      | U16  | –          | ?       | –           | Magnetic encoder status code                                                                                                  |
| 202Fh | 00h       | Encoder Error Count                | RO      | U16  | –          | ?       | –           | Magnetic encoder communication error count                                                                                    |
| 2031h | 00h       | Bus Current Offset                 | RO      | U16  | 6.5mA      | ?       | –           | Auto detected at power-on                                                                                                     |
| 2032h | 00h       | Servo Status Reset                 | RW      | U16  | 0          | 0       | RPDO        | Write 1 to corresponding bit to reset fault, bit clears after success, see special byte bit parsing                           |
| 2033h | 00h       | Servo Manufacturer                 | Default | U32  | –          | –       | –           | Factory default parameter                                                                                                     |
| 2034h | 00h       | Servo Model                        | Default | U32  | –          | –       | –           | Factory default parameter                                                                                                     |

### 2.3 Standard Device Sub-protocol Area <a href="#block-345d4c79856d80339026f457a52ae44b" id="block-345d4c79856d80339026f457a52ae44b"></a>

| Index | Sub Index | Object                     | Access | Type | Unit       | Default                       | PDO Mapping | Description                                                            |
| ----- | --------- | -------------------------- | ------ | ---- | ---------- | ----------------------------- | ----------- | ---------------------------------------------------------------------- |
| 603Fh | 00h       | Error Code                 | RO     | U16  | –          | 0                             | TPDO        | Refer to 1003h (Pre-defined Error Field), can be reset to 0 via 6040h  |
| 6040h | 00h       | Control Word               | RW     | U16  | –          | 0                             | RPDO        | 0: disable servo torque, 15: enable servo torque, 11: quick fault stop |
| 6041h | 00h       | Status Word                | RO     | U16  | –          | 0                             | TPDO        | See CANopen communication protocol                                     |
| 6060h | 00h       | Modes of Operation         | RW     | S8   | –          | default mode (2003)           | RPDO        | See special byte bit parsing                                           |
| 6061h | 00h       | Modes of Operation Display | RO     | S8   | –          | default mode (2003)           | TPDO        | See special byte bit parsing                                           |
| 6062h | 00h       | Target Position            | RO     | S32  | 0.022deg   | ?                             | TPDO        |                                                                        |
| 6063h | 00h       | Actual Position            | RO     | S32  | 0.022deg   | ?                             | TPDO        |                                                                        |
| 606Ch | 00h       | Actual Velocity            | RO     | S32  | –          | ?                             | TPDO        |                                                                        |
| 6072h | 00h       | Torque Limit               | RW     | U16  | 0.02%      | torque limit (2004)           | RPDO        |                                                                        |
| 6074h | 00h       | Current Torque             | RW     | S16  | 0.02%      | ?                             | TPDO        |                                                                        |
| 6075h | 00h       | Rated Current              | RW     | U32  | 6.5mA      | rated current limit (201F)    | RPDO        |                                                                        |
| 6078h | 00h       | Current Feedback           | RO     | S16  | 6.5mA      | ?                             | TPDO        |                                                                        |
| 607Ah | 00h       | Target Position            | RW     | S32  | 0.022deg   | –                             | RPDO        | Servo position control target position                                 |
| 6083h | 00h       | Profile Acceleration       | RW     | U32  | 0.366rpm/s | max acceleration limit (201E) | RPDO        | Acceleration and deceleration share this parameter                     |
| 6084h | 00h       | Profile Deceleration       | RW     | U32  | 0.366rpm/s | –                             | RPDO        | Invalid                                                                |
| 6085h | 00h       | Quick Stop Deceleration    | RW     | U32  | 0.366rpm/s | –                             | RPDO        | Used when control word is 11 for quick stop                            |
| 60FFh | 00h       | Target Velocity            | RW     | S32  | 0.183rpm   | max speed limit (201D)        | RPDO        |                                                                        |

## 3. Special Byte Description <a href="#block-345d4c79856d8027acbbec3d698e8e64" id="block-345d4c79856d8027acbbec3d698e8e64"></a>

### **3.1 Mode Definition** <a href="#block-345d4c79856d80d8a5e6d0a30bd50ac2" id="block-345d4c79856d80d8a5e6d0a30bd50ac2"></a>

| Value | Mode                   | Description                                                                         |
| ----- | ---------------------- | ----------------------------------------------------------------------------------- |
| 1     | Standard Position Mode | Target position, velocity, rated current control, acceleration/deceleration control |
| 3     | Standard Velocity Mode | Velocity, rated current control, acceleration/deceleration control                  |
| 12    | Motor Mode             | Rated current control (0.02%), used for servo testing                               |

### **3.2 Error Register Definition** <a href="#block-345d4c79856d80e6a4a2f8ef6a2d7968" id="block-345d4c79856d80e6a4a2f8ef6a2d7968"></a>

**Bit number / bit weight: 0 indicates normal, 1 indicates abnormal**

* BIT0 (1): ----
* BIT1 (2): servo overcurrent
* BIT2 (4): servo overvoltage / undervoltage
* BIT3 (8): servo overtemperature
* BIT4 (16): ----
* BIT5 (32): ----
* BIT6 (64): ----
* BIT7 (128): servo position sensor communication error

### **3.3 Predefined Error Field Definition** <a href="#block-345d4c79856d80d3a2f9fe2a341a8acc" id="block-345d4c79856d80d3a2f9fe2a341a8acc"></a>

| Additional Info | Error Code    |
| --------------- | ------------- |
| bit31 \~ bit16  | bit15 \~ bit0 |

| Error Code | Alarm Description         |
| ---------- | ------------------------- |
| 0000h      | error reset or no error   |
| 2300h      | motor overcurrent         |
| 2311h      | motor overload            |
| 3210h      | power supply overvoltage  |
| 3220h      | power supply undervoltage |
| 4210h      | overtemperature alarm     |
| 7306h      | encoder fault             |

### **3.4 Servo Phase** <a href="#block-345d4c79856d80358e38d20d487bfeaf" id="block-345d4c79856d80358e38d20d487bfeaf"></a>

**Bit number / bit weight: description**

* BIT0 (1): driver direction phase; (0) forward, (1) reverse
* BIT1 (2): position feedback direction phase; (0) forward, (1) reverse
* BIT2 (4): brushless / brushed; (0) brushless, (1) brushed, takes effect after reboot

### 3.5 Servo Status <a href="#block-345d4c79856d8011a57cee22b20f8fe4" id="block-345d4c79856d8011a57cee22b20f8fe4"></a>

**\*Servo status: 0 indicates normal, 1 indicates abnormal**

**Bit number / bit weight: description**

* BIT0 (1): driver direction phase; (0) forward, (1) reverse
* BIT1 (2): position feedback direction phase; (0) forward, (1) reverse
* BIT2 (4): brushless / brushed; (0) brushless, (1) brushed, takes effect after reboot

### **3.6 LED Alarm Condition** <a href="#block-345d4c79856d809c9d5fd58a4322133a" id="block-345d4c79856d809c9d5fd58a4322133a"></a>

**LED alarm condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): ----
* BIT1 (2): overcurrent alarm
* BIT2 (4): voltage alarm
* BIT3 (8): overtemperature alarm
* BIT4 (16): ----
* BIT5 (32): ----
* BIT6 (64): ----
* BIT7 (128): encoder alarm

### **3.7 Protection Switch** <a href="#block-345d4c79856d80fea381d003b144a65c" id="block-345d4c79856d80fea381d003b144a65c"></a>

**Unload condition: 0 indicates off, 1 indicates on**

**Bit number / bit weight: description**

* BIT0 (1): ----
* BIT1 (2): overcurrent alarm
* BIT2 (4): voltage alarm
* BIT3 (8): overtemperature alarm
* BIT4 (16): ----
* BIT5 (32): ----
* BIT6 (64): ----
* BIT7 (128): encoder alarm

### **3.8 Status Reset** <a href="#block-345d4c79856d80c49658f59bd30bd04d" id="block-345d4c79856d80c49658f59bd30bd04d"></a>

**Fault reset: 0 invalid, 1 indicates reset**

**Bit number / bit weight: description**

* BIT0 (1): ----
* BIT1 (2): reset overcurrent fault
* BIT2 (4): reset overvoltage / undervoltage; when voltage returns to normal, write 32 to reset this status
* BIT3 (8): reset overtemperature status; when temperature returns to normal, write 64 to reset this status
* BIT4 (16): ----
* BIT5 (32): ----
* BIT6 (64): ----
* BIT7 (128): reset magnetic encoder status; when encoder communication is normal, write 128 to reset this status
* BIT14 (16384): revolution reset; write 16384 to reset, current position returns to single-turn position
* BIT15 (32768): zero position setting; write 32768 to set current position as midpoint (8192)
