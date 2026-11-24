---
description: >-
  Wire GO-M8010-6 correctly, understand rotor-side control and firmware limits,
  and decode an original synthetic reply before any motor SDK or bench work.
---

# Unitree GO-M8010-6 Motor User Manual

> **Verified OpenELAB motor listing:** [**Unitree GO-M8010-6 High Torque FOC Four-legged Robot Joint Micro Micromotor**](https://openelab.io/products/unitree-go-m8010-6-high-torque-foc-four-legged-robot-joint-micro-micromotor), motor option **SKU `Unitree-4FOCMotor`**. The listing also offers accessory-only variants; they are not additional motor models or whole robots.

## Product overview <a href="#product-overview" id="product-overview"></a>

### Unitree GO-M8010-6 Motor User Manual <a href="#block-35fd4c79856d81f8a45fe95f859c1c64" id="block-35fd4c79856d81f8a45fe95f859c1c64"></a>

GO-M8010-6 is an integrated brushless joint motor with planetary reduction, FOC driver and position sensing. This is the existing motor manual, retaining its published identity, stable anchors and image references. It is a component guide: `MotorType.GO_M8010_6` in the actuator SDK does not mean a Go1/Go2 robot is exposed through this serial interface. The full model N6014B-12.6 belongs to IM6014 and must not identify this motor. [About M8010](https://doc-cdn.unitree.com/8/1484/en/8_1484_en) [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en)

### Motor Overview <a href="#block-35fd4c79856d8029b9ffd1d1b7fa6b82" id="block-35fd4c79856d8029b9ffd1d1b7fa6b82"></a>

The integrated driver handles current commutation and a hybrid torque/position/velocity law; the host remains responsible for targets, timing and system limits. The encoder's tracked rotor angle and a geared output angle are different quantities. Sources in this page are the manufacturer's product table, all **21 actual English motor-space articles**, and the actuator SDK pinned below, read on 24 November 2026. Linked binaries were not inspected or executed.

## Applications <a href="#applications" id="applications"></a>

Suitable designs include compact legged joints and research mechanisms whose peak torque, bus power and mechanical attachment fit this exact motor. A listing's phrase “four-legged robot joint” is not a guarantee of interchangeability with another Unitree joint or an assembled robot. The motor has no application-level trajectory planner or independent safety controller established by these sources.

The best first software result is an offline protocol check. The supplied vendor C++, Python and multi-channel programs are **actuation examples**, including velocity targets and damping. Seeing position and temperature printed by one of them does not make it a passive monitor. [Run C++ Example](https://doc-cdn.unitree.com/8/105/en/8_105_en) [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en) [4-channel USB to 485 module](https://doc-cdn.unitree.com/8/465/en/8_465_en)

## Specifications <a href="#specifications" id="specifications"></a>

| Item                  | GO-M8010-6 value / qualification                                                   |
| --------------------- | ---------------------------------------------------------------------------------- |
| Weight; outline       | 530 g; 96.5 × 92.5 × 42.3 mm                                                       |
| Operating supply      | 12–30 V DC; 24 V recommended                                                       |
| Peak output torque    | 23.7 Nm, not continuous torque                                                     |
| Maximum speed         | 30 rad/s at 24 V                                                                   |
| Current headline      | 40 A maximum phase current in About; not a continuous supply budget                |
| Reduction ratio       | 6.33                                                                               |
| Rotor encoder         | 15-bit single-turn absolute; tracked turn count is not retained through power loss |
| Operating temperature | −5 to 40°C in the product specification                                            |
| Communication         | RS485, 4 Mbps, 8N1, half-duplex                                                    |
| Addresses             | 0–14 individually; 15 broadcast, no reply                                          |
| Native frames         | 17-byte command FE EE; 16-byte reply FD EE                                         |

The [manufacturer GO motor page](https://www.unitree.com/go1/motor) and [About M8010](https://doc-cdn.unitree.com/8/1484/en/8_1484_en) establish this component's ratings. Absolute-limit/protection figures such as 60 V or a 45 V overvoltage threshold are not permission to operate above 30 V. Likewise, serialized torque range is not a continuous or safe physical rating.

The documented demo supply is at least 24 V/5 A, using at least 18 AWG cable shorter than 1 m. That is a particular bench reference, not a validated multi-motor supply design. Provide load, acceleration, simultaneous-current and cable-drop margin. Braking can return energy: a conventional switching supply may be damaged even when the drive protects itself. Use a correctly protected regenerative-capable power system and smooth trajectories after commissioning. [About M8010](https://doc-cdn.unitree.com/8/1484/en/8_1484_en) [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Motor Wiring Connection <a href="#block-35fd4c79856d808181cbfc108bf0271b" id="block-35fd4c79856d808181cbfc108bf0271b"></a>

GO motor wiring combines a power path and a differential data path. Use the exact motor connector view and matching harness for both.

### Motor wiring and accessories <a href="#motor-wiring-and-accessories" id="motor-wiring-and-accessories"></a>

Use the official XT30PB-M(2+2) orientation, not an IM6014 pin list or the mating plug's mirrored view. In the shown motor drawing A is upper left, B lower left, with power − and + in their illustrated positions. Both A/B and power polarity must be checked on the actual harness. Controller/USB adapter ground must share the motor's power-negative reference. Power off before wiring or hot-plugging: the source specifically warns that hot-plugging can damage a 10 Ω bus resistor. A/B are not power contacts. [About M8010](https://doc-cdn.unitree.com/8/1484/en/8_1484_en) [Line connection](https://doc-cdn.unitree.com/8/102/en/8_102_en)

![Official GO-M8010-6 motor connector drawing; use the illustrated view](https://oss-global-cdn.unitree.com/static/58cd91efd85548c3b9ceb94db23dca57_1257x867.jpg)

![Retained legacy GO motor wiring illustration; current wiring qualification is in the surrounding text](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cbabd8e0-7aba-4286-9806-7143f7cb1aaf/image/w=1920,quality=90,fit=scale-down)

The accessory board's GH1.25 three-pin header is shown with power negative, 485 A and 485 B from top to bottom **in that drawing**. Use its exact view and labels; no generic GH connector pin order follows from the connector name. Accessory kits supply wiring/adapter parts, not another motor. Kit contents and connector footprints are documented separately; confirm the purchased option and bill of materials. The download page supplies an Altium integrated library for XT30 PB/PW(2+2), GH1.25 3Pin and the TTL-to-485 module; the archive itself was not reviewed. [Accessory kit](https://doc-cdn.unitree.com/8/1498/en/8_1498_en) [Connector Footprint](https://doc-cdn.unitree.com/8/1503/en/8_1503_en) [DownloadPage](https://doc-cdn.unitree.com/8/1483/en/8_1483_en)

### RS485 topology and host modules <a href="#rs485-topology-and-host-modules" id="rs485-topology-and-host-modules"></a>

Daisy-chain A-to-A, B-to-B and common reference, keep IDs unique and use the configured 4 Mbps everywhere. The FAQ says no internal termination: it calls for external 120 Ω termination at both physical ends. Verify any supplied harness or adapter termination before adding duplicates. The maximum of 15 addressed motors is an ID capacity, not a demonstrated 15-motor real-time performance guarantee. Budget aggregate traffic and far-end supply drop. [Line connection](https://doc-cdn.unitree.com/8/102/en/8_102_en) [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en)

The four-channel USB module offers independent RS485 ports; the example uses four host threads and three motors per channel. Its tutorial specifies Ubuntu ≥20.04, GCC ≥9.3 and CMake ≥3.11, with optional external PREEMPT\_RT advice. Conflicting introductory 115200-baud and line-page 10-Mbps claims do not establish an actual verified high-speed performance rating. The supplied blocking program initializes gains/targets and commands motion, creates per-channel threads, loops over send/receive work and performs cleanup. Its timing and printed status are software observations; `Ctrl-C` and cleanup are not an independently verified stop. Driver identity, actual port naming and bus wiring are prerequisites, while unrelated driver download sites are not proof of support. [4-channel USB to 485 module](https://doc-cdn.unitree.com/8/465/en/8_465_en) [Line connection](https://doc-cdn.unitree.com/8/102/en/8_102_en)

The TTL-to-485 module exposes RO, active-low RE, DE and DI and needs correct half-duplex direction timing and shared ground. An MCU UART cannot drive RS485 A/B directly. This transceiver is not the TTL single-bus servo adapter. Its timing and size drawings are the primary hardware references. [TTL to 485 module](https://doc-cdn.unitree.com/8/1489/en/8_1489_en)

### GO-specific CAN bridge <a href="#go-specific-can-bridge" id="go-specific-can-bridge"></a>

The GO module uses extended 29-bit CAN identifiers, with the upper two bits carrying the module ID (0–3, default 3); CAN is 1 Mbps or 500 kbps with DIP 4 on. Its UART maintenance interface is 115200 8N1. The module's 80 V power tolerance does not enlarge GO's 12–30 V operating limit; signal pins remain limited to 5 V. `AT+D` rotates all connected motors; `AT+T`, `AT+R` and `AT+P` are diagnostic/reset/boot operations, not passive first checks. [CAN to 485 module](https://doc-cdn.unitree.com/8/472/en/8_472_en)

Bridge commands separate parameter state from control: function 11 stores gains per motor ID, function 12 reads parameters, function 10 controls with feedback, and function 13 uses the bridge's last transaction/cache. Gains are volatile and must be handled after power loss; parameter and target frames are not an atomic transaction. A cached reply must not be presented as a new physical sample. The documented communication-error temperature sentinel is −128. The quoted 3500 Hz at 500 kbps and 6000 Hz at 1 Mbps are conditional source claims, not validated sustained multi-motor rates. This GO-specific bridge description does not qualify IM6014, A1, B1-16 or servo firmware.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Introduction to FOC <a href="#block-35fd4c79856d802e8781fda0176ae8d0" id="block-35fd4c79856d802e8781fda0176ae8d0"></a>

The FOC explanation below separates the drive’s current commutation from the host’s application targets and limits.

### FOC, encoders and rotor-side control <a href="#foc-encoders-and-rotor-side-control" id="foc-encoders-and-rotor-side-control"></a>

FOC regulates the magnetic-field-oriented current components using rotor angle. It improves commutation and torque behavior but does not provide collision avoidance or a complete robot controller.

![Retained FOC illustration from the published manual](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/581508cb-33fd-450a-8865-cec4ed53c3cc/image/w=1920,quality=90,fit=scale-down)

#### Motor Hardware and Encoder Overview <a href="#block-35fd4c79856d80fdbd71c97c3a5acc09" id="block-35fd4c79856d80fdbd71c97c3a5acc09"></a>

The 15-bit absolute rotor encoder resolves one mechanical rotor turn. The controller tracks additional turns while powered; after power loss, the application must not assume its old multi-turn coordinate remains valid. Output position reconstructed from the rotor and 6.33 ratio is not an independent output encoder measurement. [Overview](https://doc-cdn.unitree.com/8/100/en/8_100_en) [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en)

#### Hybrid Control of the Motor <a href="#block-35fd4c79856d80d69be5ef6f078daa4c" id="block-35fd4c79856d80d69be5ef6f078daa4c"></a>

Hybrid control combines feedforward torque with position and velocity feedback. Keep the rotor and output coordinate conventions explicit.

#### Motor control <a href="#block-360d4c79856d807c81d1fa85ae072cff" id="block-360d4c79856d807c81d1fa85ae072cff"></a>

The drive combines feedforward torque with proportional position and velocity feedback:

`tau = tau_ff + kp * (q_des - q) + kd * (dq_des - dq)`.

`kp` has units Nm/rad and `kd` has units Nm/(rad/s). Position control uses nonzero position gain and damping; speed control sets position gain to zero and uses velocity gain; damping sets a zero desired speed with velocity gain; pure torque sets both gains to zero. Zero feedforward and zero gains remove the commanded torque contribution while the drive can remain enabled. That is neither an independent power disconnect nor a guarantee that a gravity-loaded linkage will hold position. Feedforward plus feedback creates hybrid control. These are combinations of fields within FOC, not necessarily distinct packet mode numbers.

A gear ratio `r` relates rotor and ideal output quantities as `q_out=q_rot/r`, `dq_out=dq_rot/r`, and `tau_out≈tau_rot*r`; friction and losses make torque conversion an estimate. Equivalent output position and velocity gains scale by `r²`. Always identify which side an API uses before applying a ratio. A source integer's representable range describes serialization, not a safe mechanical command envelope.

#### Position mode <a href="#block-360d4c79856d804ea965f0a814a75899" id="block-360d4c79856d804ea965f0a814a75899"></a>

Position control needs the initial desired coordinate to match a validated current coordinate before gains are introduced in a later approved bench process; a distant target produces a step.

#### Velocity mode <a href="#block-360d4c79856d805b99c6def5c3a68bd2" id="block-360d4c79856d805b99c6def5c3a68bd2"></a>

Speed control uses damping/velocity gain and a desired rotor speed; a target quoted at the output needs multiplication by 6.33.

#### Damping mode <a href="#block-360d4c79856d8039ab7fdf3bf2ed584e" id="block-360d4c79856d8039ab7fdf3bf2ed584e"></a>

Damping resists velocity but does not hold a fixed position under sustained external torque.

#### Torque mode <a href="#block-360d4c79856d80b7af7ec4777e8c350f" id="block-360d4c79856d80b7af7ec4777e8c350f"></a>

Pure torque can accelerate an unloaded rotor to high speed; it is not a fixed-speed test.

#### Zero-torque mode <a href="#block-360d4c79856d80f0a539f44d54830e36" id="block-360d4c79856d80f0a539f44d54830e36"></a>

Zero-torque FOC remains an enabled drive state. Do not test it by putting a hand on an energized shaft.

#### Force-position hybrid mode <a href="#block-360d4c79856d80488880f44ad3446673" id="block-360d4c79856d80488880f44ad3446673"></a>

Hybrid control adds torque feedforward to spring/damper feedback. `kw` is older naming for velocity gain; current public API names it `kd`. Numeric source examples contain different position/speed targets in prose and code, so no unreviewed demo target is reproduced here. [Control Mode](https://doc-cdn.unitree.com/8/106/en/8_106_en) [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en)

### Pinned actuator SDK: setup contract and API <a href="#pinned-actuator-sdk-setup-contract-and-api" id="pinned-actuator-sdk-setup-contract-and-api"></a>

The read source is [unitree\_actuator\_sdk at 5b79a42d81cd69adac1367db79efdb972a898fd1](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md), not robot SDK2 or a ROS package. README supports GO-M8010-6, A1 motor and B1 motor categories. GCC ≥5.4 is stated for x86 and ≥7.5 for ARM. The actual [CMakeLists.txt](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/CMakeLists.txt) requires CMake ≥3.1 and C++14 and links prebuilt Arm64 for `aarch64`, otherwise Linux64. That `else` branch is not evidence that every other processor or operating system works. Its bundled pybind11 builds a Python extension; Python ABI, architecture and shared-library compatibility must match the delivered environment. This source pin does not declare a universal minimum Python version.

Build-only reference for a later reviewed local checkout, **not performed here**:

```sh
cmake -S /path/to/reviewed/unitree_actuator_sdk -B /path/to/local/build
cmake --build /path/to/local/build
```

CMake builds active motor examples and `changeID` as well as the extension. Building is separate from running; this page gives no command to run those programs. The portal Quick Start also mentions dependencies and compilation, but source prerequisites, binary ABI and the physical adapter all need independent confirmation. [Quick Start](https://doc-cdn.unitree.com/8/159/en/8_159_en) [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en)

#### C++ example trial run <a href="#block-360d4c79856d80b1aca2c594414142f7" id="block-360d4c79856d80b1aca2c594414142f7"></a>

The public C++ command uses `motorType`, `id`, `mode`, `tau`, `dq`, `q`, `kp` and `kd`. The current fields are not interchangeable with older `T/W/Pos` names. Both command and data need the exact model selector. `queryMotorMode` and `queryGearRatio` are declared APIs; their implementation is linked in a prebuilt library. `MotorData.correct` begins false; a receive path must inspect transaction success and validated data before logging values. A printed struct after a failed transfer can be stale or uninitialized. The SerialPort declaration defaults to a 16-byte receive length, 4 Mbps and 20000 µs timeout; these defaults are not the A1/B1 wire contract. [Command/data declarations](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/unitreeMotor.h) [SerialPort declaration](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/serialPort/SerialPort.h)

![Retained illustration of the older C++ example; it is an actuation example, not an offline instruction](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/35927fab-3d01-45fe-80b1-abeca4c2b3d4/7c6b70da-b3c2-4887-ab38-de9c475c74f1/w=1920,quality=90,fit=scale-down)

The pinned C++ example sets FOC with nonzero damping and a rotor speed of `−6.28 × ratio`, then repeatedly calls `sendRecv`. The Python article also commands velocity. Their 200 µs delays do not establish a measured 5 kHz closed-loop update rate. The STM32 reference uses F103C8T6 with PA9 TX, PA10 RX and PA11 DE through a suitable 4-Mbps transceiver. Some embedded demonstrations select open-loop mode 5; that actuates. A Python table's calibration value 10 conflicts with the three-bit mode field and other mode-2 documentation; do not truncate arbitrary integers into mode bits. [Pinned C++ example](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/example/example_goM8010_6_motor.cpp) [Run C++ Example](https://doc-cdn.unitree.com/8/105/en/8_105_en) [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en) [Run STM32 example](https://doc-cdn.unitree.com/8/785/en/8_785_en)

#### Porting to other host computer platforms <a href="#block-4098c4d677e84f718aecdd9b8fb1c5d1" id="block-4098c4d677e84f718aecdd9b8fb1c5d1"></a>

A host-platform port must preserve the GO message contract, serial timing and data-validity checks. A common API name does not establish another motor’s compatibility.

#### Communication configuration <a href="#block-360d4c79856d8092bf4efd4e118bd26c" id="block-360d4c79856d8092bf4efd4e118bd26c"></a>

Confirm the GO bus rate, address and host ownership before interpreting a transaction; the packet layout is a separate requirement.

#### Motor motion control command format <a href="#block-360d4c79856d8015952bd3393fe8cf5f" id="block-360d4c79856d8015952bd3393fe8cf5f"></a>

The GO command and reply layouts below define field offsets and checksum coverage. Their representable ranges do not establish safe physical targets.

### Wire format and firmware boundary <a href="#wire-format-and-firmware-boundary" id="wire-format-and-firmware-boundary"></a>

Host commands are **17 bytes** with FE EE; replies are **16 bytes** with FD EE, little-endian. Byte 2 carries ID in bits 0–3 and mode in 4–6. The current portal assigns bit 7 to timeout protection, while the pinned packed header still names it reserved (`none`). No minimum compatible firmware is established here; do not inherit IM6014's one-second timeout or silently activate the new bit. The source's usual modes are 0 stop, 1 FOC and 2 calibration; calibration and factory/boot modes are state-changing. [Communication Protocol](https://doc-cdn.unitree.com/8/107/en/8_107_en) [Pinned packed GO header](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_GO-M8010-6.h)

| Field                  | Command offsets; conversion               | Reply offsets; conversion                                                            |
| ---------------------- | ----------------------------------------- | ------------------------------------------------------------------------------------ |
| Torque                 | 3–4; raw = Nm × 256                       | 3–4; Nm = raw/256                                                                    |
| Speed                  | 5–6; raw = rad/s ÷ 2π × 256               | 5–6; rad/s = raw/256 × 2π                                                            |
| Position               | 7–10; raw = rad ÷ 2π × 32768              | 7–10; rad = raw/32768 × 2π                                                           |
| Position/velocity gain | 11–12 / 13–14; raw = physical gain × 1280 | Not those fields in feedback                                                         |
| Temperature            | Not present                               | Signed byte 11                                                                       |
| Error/force            | Not present                               | Word 12–13: low 3 bits error, next 12 bits force raw; force physical unit unverified |
| CRC16                  | Bytes 15–16 over first 15                 | Bytes 14–15 over first 14                                                            |

CRC16 uses reflected polynomial 0x8408, seed zero and no final xor, stored little-endian. The pinned CRC helper takes a caller-provided seed; the protocol supplies the zero seed. The raw torque envelope can encode about ±128 Nm at the rotor, while the portal recommends a much smaller rotor range and the actual output peak is 23.7 Nm. None of those are a safe generic target. [Communication Protocol](https://doc-cdn.unitree.com/8/107/en/8_107_en) [Pinned CRC helper](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/crc/crc_ccitt.h)

### Configuration, assistant and release control <a href="#configuration-assistant-and-release-control" id="configuration-assistant-and-release-control"></a>

Keep serial-device identification separate from changes to motor configuration. The topics below distinguish tools, ID operations, firmware selection and mode restoration.

#### Motor configuration <a href="#block-360d4c79856d8036bafbf73ab46f2f2e" id="block-360d4c79856d8036bafbf73ab46f2f2e"></a>

Configuration work changes mode, identity or firmware and requires a matched stopped-state procedure. Identifying the host serial device is a separate preliminary task.

#### Check the serial port name <a href="#block-360d4c79856d80f686b8e12a1ee01e84" id="block-360d4c79856d80f686b8e12a1ee01e84"></a>

Identify the adapter and actual serial port using the host's normal device inventory. The retained screenshot is a historical example, not a fixed device name.

![Retained serial device screenshot from the existing motor manual](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6ada59e1-d955-40c0-929f-05effb3fd6d3/image/w=1920,quality=90,fit=scale-down)

#### Obtain the Motor Toolbox <a href="#block-360d4c79856d80d2a0c1ccd8ed6361a3" id="block-360d4c79856d80d2a0c1ccd8ed6361a3"></a>

Linux MotorTools includes `swboot`, `swmotor`, `changeid` and `unisp`. They change mode, ID or firmware; they are not read-only development prerequisites. The older page's `changed` spelling was not a verified tool name. Do not execute an old command screenshot as a recovery recipe.

![Retained MotorTools illustration; tool execution is outside this guide checkpoint](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3aeed34b-0960-4d1d-9916-50cbe57bc97c/image/w=1920,quality=90,fit=scale-down)

#### Check the motor ID <a href="#block-360d4c79856d80e28644f74a6d050801" id="block-360d4c79856d80e28644f74a6d050801"></a>

Query ID in the Windows assistant enters factory mode; its own instructions require Enable Auto Boot and Restore Motor Mode afterward. The query is therefore not a harmless passive receive. The GUI's Start Debugging can transmit immediately; its Query Version UI does not prove the shared transmit loop is stopped. FT232H/FT4232H adapters are the specifically discussed driver family, not every USB serial device.

![Retained ID-query screenshot; querying can switch motor mode](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c03f3b13-5f0c-4eae-af75-00db029dd958/image/w=1920,quality=90,fit=scale-down)

#### Change the motor ID <a href="#block-360d4c79856d800a98bedd62cfab2f69" id="block-360d4c79856d800a98bedd62cfab2f69"></a>

Change IDs one motor at a time while the mechanism is safely stopped and supported. Never put duplicate IDs on a shared line.

![Retained ID-change screenshot; state-changing configuration only](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e02c6f63-14f5-4940-90ba-d4e9733a0556/image/w=1920,quality=90,fit=scale-down)

#### Motor firmware upgrade <a href="#block-360d4c79856d808a9459daa239e916b0" id="block-360d4c79856d808a9459daa239e916b0"></a>

The current download table lists **E\_GO-M8010-6\_DRV\_v1.4.5\_HW2.bin**, version **v1.4.5**, dated **2025-10-30**, with a fix for excessive bus communication frequency reducing the current-loop rate. The ZIP is listed only; neither its contents nor a delivered motor's HW2 match has been validated. An old `GoM80106_v1.0.bin` example is not the current compatible file selection.

![Retained firmware-tool screenshot; firmware and hardware matching must be confirmed separately](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/78f748b2-4471-47a6-9337-5e35b4ae1c8f/image/w=1920,quality=90,fit=scale-down)

#### Switch back to motor mode <a href="#block-360d4c79856d80ebac85f71c44212958" id="block-360d4c79856d80ebac85f71c44212958"></a>

Factory mode can persist through reboot. Restore motor mode and auto-boot only through the matched manufacturer's documented procedure, with no competing port owner and an independent stop plan. Failed upgrades or mode recovery belong to manufacturer support after recording the exact firmware, hardware and fault state. [FW Upgrade\&ID Config](https://doc-cdn.unitree.com/8/103/en/8_103_en) [Motor Debugging Assistant](https://doc-cdn.unitree.com/8/158/en/8_158_en) [DownloadPage](https://doc-cdn.unitree.com/8/1483/en/8_1483_en)

A later live integration needs the delivered model, drive and hardware revision, firmware identifier, adapter, operating system, serial device, bus rate and ID recorded together. Assign one process exclusive ownership of the serial bus; close the assistant, other terminal tools and any robot controller before a qualified bench session. Each active status poll can transmit a control/state transaction. None of these motors provides a DDS subscriber-only first result. A successful frame CRC is not proof of model identity, firmware compatibility, safe mounting or fresh physical measurement.

For an eventual receive log, preserve immutable frame bytes with model provenance, monotonic receipt time, local frame counter and the exact parser revision. Reject mismatched IDs, length, header, CRC and invalid SDK results. Measure arrival age separately from changes in position: a stationary motor can have valid fresh feedback. On loss or stale feedback, stop the application under a separately engineered stop procedure; closing a port or attempting a final zero command cannot guarantee delivery over a broken link.

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Save the complete original Python block below as a local file.
2. Run that file with an existing Python 3 interpreter; no package installation is needed.
3. Compare the printed OFFLINE PASS result and preserve all unverified metadata flags.

### Product Usage Precautions <a href="#block-35fd4c79856d80ce9859f93437d7fae0" id="block-35fd4c79856d80ce9859f93437d7fae0"></a>

The first exercise below stays offline. A later powered session still requires the model, wiring, load support and independent stop conditions described in this guide.

### First result: original offline feedback exercise <a href="#first-result-original-offline-feedback-exercise" id="first-result-original-offline-feedback-exercise"></a>

Use an existing Python 3 interpreter with this complete standard-library block. It constructs a synthetic **reply**, not a command, checks its 16-byte form and CRC, and converts one rotor torque value. It imports no SDK and has no serial or network access. Expected output is `GO-M8010-6 OFFLINE PASS 16 bytes` and `rotor_torque=1.000 Nm output_estimate=6.330 Nm`.

```python
"""Original offline GO-M8010-6 feedback exercise; no serial/device access."""
import math
import struct

def crc16(data):
    value = 0
    for byte in data:
        value ^= byte
        for _ in range(8):
            value = (value >> 1) ^ (0x8408 if value & 1 else 0)
    return value

def decode(frame, expected_id=0):
    frame = bytes(frame)
    if len(frame) != 16 or frame[:2] != b'\xfd\xee':
        raise ValueError('Expected a 16-byte GO feedback frame')
    if crc16(frame[:14]) != int.from_bytes(frame[14:], 'little'):
        raise ValueError('CRC mismatch')
    motor_id, mode = frame[2] & 15, (frame[2] >> 4) & 7
    if motor_id != expected_id or motor_id == 15:
        raise ValueError('Unexpected or broadcast ID')
    torque, speed, position, temperature, flags = struct.unpack_from('<hhibH', frame, 3)
    ratio = 6.33
    return dict(model='GO-M8010-6', mode=mode, error=flags & 7,
                rotor_torque=torque / 256,
                output_torque_estimate=torque / 256 * ratio,
                output_position_from_rotor=position / 32768 * math.tau / ratio,
                output_speed_from_rotor=speed / 256 * math.tau / ratio,
                temperature=temperature, force_raw=(flags >> 3) & 4095,
                data_origin='synthetic offline frame')

if __name__ == '__main__':
    payload = b'\xfd\xee\x00' + struct.pack('<hhibH', 256, 0, 0, 25, 0)
    frame = payload + crc16(payload).to_bytes(2, 'little')
    result = decode(frame)
    print(result['model'], 'OFFLINE PASS', len(frame), 'bytes')
    print('rotor_torque=%.3f Nm output_estimate=%.3f Nm' %
          (result['rotor_torque'], result['output_torque_estimate']))
```

The “output estimate” is ideal gearing, not a measured calibrated output torque. A CRC-valid frame does not identify which hardware/firmware produced it. This example creates its own provenance and does not claim to read a motor. It does not count distinct physical samples, certify timeout behavior or infer a force unit.

### Later bench gate <a href="#later-bench-gate" id="later-bench-gate"></a>

Confirm the exact motor and hardware revision, firmware/protocol pair, fixed mounting, load support, 12–30 V power design, braking-energy handling, correct cable orientation, adapter/baud/ID and single bus owner. Establish a manufacturer-approved stopped-state polling method before any FOC gain, speed target or calibration. Querying feedback on this request/reply bus still needs a transmit transaction; a whole-robot DDS subscriber does not substitute for that procedure. None of the vendor demos was run for this guide.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### Link and host problems <a href="#link-and-host-problems" id="link-and-host-problems"></a>

Start with model, firmware, port identity, power and de-energized wiring records. Verify A/B, shared ground, 4 Mbps and ID before blaming an SDK. A permission-denied exception is a host access problem, not a failed motor. Arrange the appropriate serial-device group/permissions for the intended operator; do not make all devices world-writable or run a motion demo as administrator merely to diagnose a port. Stop any other process holding that port. For build/import failures, check the exact compiler, CPU architecture, Python ABI and prebuilt library match. [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en) [Motor Debugging Assistant](https://doc-cdn.unitree.com/8/158/en/8_158_en)

The historical `pos` jump of 1608 is a raw-coordinate troubleshooting clue discussed in the FAQ, not a radian angle or proof of gearbox backlash. Keep raw and converted values with reboot/turn-count context. Power loss invalidates assumptions about retained multi-turn position. If communication works but the motor does not move, inspect the validated error, actual mode and target interpretation; do not increase gains simply to force motion.

### Indicators and faults <a href="#indicators-and-faults" id="indicators-and-faults"></a>

The current FAQ describes slow blink about once per second for motor mode, rapid triple blink for factory/bootloader, fixed 200-ms fast blink for an error in motor mode, and off for a power problem. A steadily lit lamp is not a defined “healthy control” state in that FAQ. Use the actual error field and model firmware, not an LED alone.

| Error value | Current portal meaning | Pinned-header caveat                                                             |
| ----------- | ---------------------- | -------------------------------------------------------------------------------- |
| 0           | Normal                 | Agreement                                                                        |
| 1           | Overtemperature        | FAQ says about 80°C; older header comment says 90°C; actual threshold unresolved |
| 2           | Overcurrent            | Investigate load/drive, do not repeatedly clear                                  |
| 3           | Overvoltage            | Check supply and regenerative energy                                             |
| 4           | Encoder error          | Exact hardware inspection/support required                                       |
| 5           | Undervoltage           | Pinned source reserves 5–7                                                       |
| 6           | Winding overheat       | Pinned source reserves 5–7                                                       |
| 7           | Uncalibrated           | Pinned source reserves 5–7; do not infer a calibration command                   |

This three-bit error enum is not the IM6014/servo bitmask. Preserve unknown values for an unmatched firmware; do not reinterpret a pinned struct as the newest portal schema without evidence. Zero error does not qualify safe actuation. [Communication Protocol](https://doc-cdn.unitree.com/8/107/en/8_107_en) [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en) [Pinned error definitions](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_GO-M8010-6.h)

### Mode, firmware and multi-motor recovery <a href="#mode-firmware-and-multi-motor-recovery" id="mode-firmware-and-multi-motor-recovery"></a>

Factory/boot mode is separate from normal FOC mode. A raw mode >7 truncates in the three-bit field; reserved 7 enters factory mode. Never use an arbitrary integer from a conflicting table. Stop all traffic before manufacturer-directed ID/firmware work, do one motor at a time, preserve power and cable continuity, and record the exact approved recovery path. Normal operation may require auto-boot restoration after a query. A failed transfer is not permission to flash any download with a similar name.

For multi-motor faults, check supply sag, cable drop, external end termination and per-ID traffic scheduling. The four-channel example's host threads and last reply cache do not prove synchronized timestamps. Chatter, whining and overcurrent can indicate excessive gain, target steps, load or supply trouble; source tuning numbers are conditional examples rather than universal safe defaults. [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en) [4-channel USB to 485 module](https://doc-cdn.unitree.com/8/465/en/8_465_en)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

Use the actual [motor Download Page](https://doc-cdn.unitree.com/8/1483/en/8_1483_en) for direct upstream resources. It lists the [English manual dated 2024-05-15](https://oss-global-cdn.unitree.com/static/33c284af73014b2184b18dffe0b5be4c.pdf), Chinese manual, GO STM32 HAL example, four-channel multi-motor example, GO STP, A1 STEP, the HW2/v1.4.5 firmware ZIP, FTDI driver, CAD footprint library and hardware links. These files were **listed only**, not opened, installed, built or flashed. The third-party real-time-kernel article is also listed-only.

The read source contracts are pinned: [SDK README](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md), [public command/data API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/unitreeMotor.h), [serial API](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/serialPort/SerialPort.h), [packed GO protocol](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/unitreeMotor/include/motor_msg_GO-M8010-6.h), [CRC helper](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/include/crc/crc_ccitt.h), [build configuration](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/CMakeLists.txt) and [BSD 3-Clause license](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/LICENSE). Source licensing does not transfer the same terms to manuals, photos, firmware, prebuilt libraries or bundled third-party components. The original inline example is separate from upstream vendor code.

The [GO portal overview](https://doc-cdn.unitree.com/8/100/en/8_100_en), [protocol](https://doc-cdn.unitree.com/8/107/en/8_107_en), [configuration](https://doc-cdn.unitree.com/8/103/en/8_103_en) and [assistant](https://doc-cdn.unitree.com/8/158/en/8_158_en) are primary instructions with the qualifications explained above.

### Direct upstream resource links (listed only) <a href="#direct-upstream-resource-links-listed-only" id="direct-upstream-resource-links-listed-only"></a>

These resource targets are preserved from the read articles. None of the following file contents was opened or executed; a link is not a compatible-package recommendation.

* [GO-M8010-6 3D model STP](https://unitree-firmware.oss-cn-hangzhou.aliyuncs.com/tool/GO-M8010-6%E7%94%B5%E6%9C%BA3D%E6%A8%A1%E5%9E%8B.stp) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [GoM\_ComDemo\_STM32\_HAL.zip](https://oss-global-cdn.unitree.com/static/7af2438fd70548879b80a0068ef159b3.zip) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [DownloadPage resource](https://oss-global-cdn.unitree.com/static/2360943378c640709c419cbfe39a8223.zip) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [Download driver ZIP](https://oss-global-cdn.unitree.com/static/29919b2689364f27b0fbd874d52ac487.zip) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [Download PDF](https://oss-global-cdn.unitree.com/static/33c284af73014b2184b18dffe0b5be4c.pdf) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [block\_comm\_test example project](https://oss-global-cdn.unitree.com/static/982515d647c04ffd99ed48d67311517e.zip) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [DownloadPage resource](https://oss-global-cdn.unitree.com/static/af10a41124704a27ae333c1a5a2b575c.zip) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [Download PDF](https://oss-global-cdn.unitree.com/static/ba47968cb8b54cc0a602d672e51d15c3.pdf) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).
* [A1\_motor.STEP](https://unitree-firmware.oss-cn-hangzhou.aliyuncs.com/tool/A1_motor.STEP) — [listing chapter](https://doc-cdn.unitree.com/8/1483/en/8_1483_en).

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The OpenELAB catalog confirms the exact motor option and SKU; accessory options `Unitree-FOCAccessory`, `Unitree-FOCAccessory2`, `Unitree-CAN485`, `Unitree-UART485` and `Unitree-XT30(2+2)` are supporting wiring/adapter variants, not motor SKUs. No live stock, delivery or test claim is made. The [manufacturer product page](https://www.unitree.com/go1/motor), all 21 cached portal motor-space articles and pinned source files cited above were actually read. Interface and accessory drawings were visually inspected; the eight legacy image references and all 25 explicit anchors remain attached to their relevant topics.

This update preserves published page ID `95b3cc1ad3fb568fc035d33f060838587dd06e88`, slug and URL. It corrects the old IM6014 model mix-up, 16/17-byte transmit inconsistency, torque offsets and unqualified old mode/firmware/temperature claims, while retaining useful FOC, encoder, hybrid-control, wiring, configuration and porting explanations. Validation is static and original synthetic Python only. No vendor SDK, serial port, DDS, ROS, motor, firmware updater or hardware was executed. Unknown delivered firmware behavior, force units, thermal thresholds and adapter performance remain explicit gaps. Readiness: **draft for independent review**.

### Read source catalog <a href="#read-source-catalog" id="read-source-catalog"></a>

| Actual read primary chapter                                                  | Treatment on this page                                                                                                       |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [About M8010](https://doc-cdn.unitree.com/8/1484/en/8_1484_en)               | Identity, power/curves/dimensions/connector, modes and source boundaries                                                     |
| [Overview](https://doc-cdn.unitree.com/8/100/en/8_100_en)                    | Basic motor concepts, FOC, tracked rotor position and hybrid model                                                           |
| [Line connection](https://doc-cdn.unitree.com/8/102/en/8_102_en)             | RS485 4M8N1, wiring, ground and termination/module limits                                                                    |
| [4-channel USB to 485 module](https://doc-cdn.unitree.com/8/465/en/8_465_en) | Four-port hardware, environment, active thread/loop/cleanup example, port/driver/rate conflicts and troubleshooting          |
| [CAN to 485 module](https://doc-cdn.unitree.com/8/472/en/8_472_en)           | Extended CAN IDs, rates/DIP/AT, volatile gain functions/control/cache/error sentinel and throughput qualifications           |
| [TTL to 485 module](https://doc-cdn.unitree.com/8/1489/en/8_1489_en)         | TTL transceiver pins/direction/timing/dimensions; actual figures as primary reference                                        |
| [Accessory kit](https://doc-cdn.unitree.com/8/1498/en/8_1498_en)             | Exact accessory header view and kit versus motor distinction                                                                 |
| [Connector Footprint](https://doc-cdn.unitree.com/8/1503/en/8_1503_en)       | Footprint library scope, actual download table, archive not opened                                                           |
| [Development Guide](https://doc-cdn.unitree.com/8/104/en/8_104_en)           | Brief development introduction; no hidden technical chapter assumed                                                          |
| [Get SDK](https://doc-cdn.unitree.com/8/156/en/8_156_en)                     | Support categories, rotor command and rate table versus whole robot                                                          |
| [Quick Start](https://doc-cdn.unitree.com/8/159/en/8_159_en)                 | Dependencies, build-only reference and active-use qualification                                                              |
| [Control Mode](https://doc-cdn.unitree.com/8/106/en/8_106_en)                | Position, speed, damping, torque, zero-torque and hybrid fields; all original anchors retained                               |
| [Communication Protocol](https://doc-cdn.unitree.com/8/107/en/8_107_en)      | All command/reply offsets/scales, raw-versus-physical limits, CRC/mode and version conflict                                  |
| [Case Reference](https://doc-cdn.unitree.com/8/160/en/8_160_en)              | Brief case-reference introduction, child routines covered separately                                                         |
| [Run C++ Example](https://doc-cdn.unitree.com/8/105/en/8_105_en)             | C++ source parsed, FOC velocity and delay hazard explained                                                                   |
| [Run Python Example](https://doc-cdn.unitree.com/8/157/en/8_157_en)          | Python wrapper/model selector, actuation and calibration-table conflict                                                      |
| [Run STM32 example](https://doc-cdn.unitree.com/8/785/en/8_785_en)           | F103/PA9/PA10/PA11/4M transceiver, active open-loop demo and wiring                                                          |
| [FW Upgrade\&ID Config](https://doc-cdn.unitree.com/8/103/en/8_103_en)       | Port/device, tool names, query/change ID, firmware and mode recovery; old anchors/media preserved                            |
| [Motor Debugging Assistant](https://doc-cdn.unitree.com/8/158/en/8_158_en)   | GUI immediate traffic, query state change, version/ID/firmware and restoration distinction                                   |
| [FAQ](https://doc-cdn.unitree.com/8/162/en/8_162_en)                         | All17FAQ topics grouped across link/permission/position/thermal/driver/power/gains/modes/LED/build/recovery/topology text    |
| [DownloadPage](https://doc-cdn.unitree.com/8/1483/en/8_1483_en)              | Manuals, SDK/tools, examples, CAD, HW2release, drivers/thirdparty/hardware links and footprints with read/listed distinction |

**Related documentation:** [Unitree model and development directory](./).
