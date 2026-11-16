# FEETECH Servo Host Computer User Manual

> FEETECH Servo Host Computer User Manual

[**FEETECH Motor**High-precision, stable robotic servos by FEETECH. Cost-effective and trusted by popular open-source projects. Perfect for your next robotics build.feetechrc.com](https://www.feetechrc.com/software.html)

## 1. Hardware Electrical Connection Diagram <a href="#block-36ed4c79856d809fa76fc0b34d112992" id="block-36ed4c79856d809fa76fc0b34d112992"></a>

### 1.1 Main Connection Diagram <a href="#block-36ed4c79856d80f084b4dfc419886495" id="block-36ed4c79856d80f084b4dfc419886495"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5ac879f2-3e1e-4e62-95df-fdb74ba52b27/image/w=1920,quality=90,fit=scale-down" alt="image" height="736.0510239556291" width="621.9874877929688">

### 1.2 Adapter board <a href="#block-36ed4c79856d8039b5f5caf104c54bcd" id="block-36ed4c79856d8039b5f5caf104c54bcd"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/53359be6-cf34-4570-b697-b809c6724ae3/image/w=1920,quality=90,fit=scale-down" alt="image" height="595.784377980566" width="626.9874877929688">

### 1.3 Servo <a href="#block-36ed4c79856d80aa9b73fec68ee3f372" id="block-36ed4c79856d80aa9b73fec68ee3f372"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3cef9eec-8a61-4202-ab54-92e6c95b1a6a/image/w=1920,quality=90,fit=scale-down" alt="image" height="575.0636202313513" width="616.9750366210938">

### 1.4 Connection Steps: <a href="#block-36ed4c79856d80a79b5df4fd6e7ea5eb" id="block-36ed4c79856d80a79b5df4fd6e7ea5eb"></a>

1. Connect the URT-1 converter to the computer via a USB cable.
2. Use a dedicated connection cable to connect the servo to the corresponding port on the converter.
3. Ensure that the servo is powered properly (refer to the product specifications for the voltage range).

## **2. Motor Parameter Configuration** <a href="#block-f334816b61ba4002b50e8d2808b543e5" id="block-f334816b61ba4002b50e8d2808b543e5"></a>

| **Parameter Name** | **Configuration Parameter**             |
| ------------------ | --------------------------------------- |
| Communication Mode | TTL Communication / RS485 Communication |
| Baud Rate          | 1M (Default)                            |

## **3. Software Interface Introduction** <a href="#block-22a3b0d737544ea6aa0a6d9950c806cb" id="block-22a3b0d737544ea6aa0a6d9950c806cb"></a>

### **3.1 Communication Settings** <a href="#block-86c3ee10381b4504bbed751e10d540fe" id="block-86c3ee10381b4504bbed751e10d540fe"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/24fcceef-1aa5-4630-bb89-10028e34716f/image/w=1920,quality=90,fit=scale-down" alt="image" height="573.3844007939878" width="737.5750122070312">

The communication settings area is used to configure the physical connection parameters between the host computer and the servo.

| **Parameter** | **Description**                                          | **Setting Recommendation**                                                        |
| ------------- | -------------------------------------------------------- | --------------------------------------------------------------------------------- |
| Port Number   | Select the COM port corresponding to the URT-1 converter | Please confirm the actual port number in Device Manager                           |
| Baud Rate     | Serial communication speed                               | Must match the baud rate set inside the servo                                     |
| Parity Bit    | Communication parity check method                        | Default is NONE                                                                   |
| Timeout       | Communication waiting timeout period (unit: ms)          | Default value is 25; can be adjusted appropriately based on communication quality |

**Operation Steps:**

1. Confirm that the URT-1 converter is properly connected to the computer’s USB port.
2. Select the corresponding COM port from the “Port Number” drop-down menu.
3. Select the baud rate that matches the servo from the “Baud Rate” drop-down menu.
4. Keep the parity bit at the default NONE setting.
5. Keep the timeout parameter at the default value of 25.

💡

**Note:** Incorrect communication parameter settings will result in the inability to connect to the servo. If a connection failure occurs, first verify that the port number and baud rate settings are correct.

### **3.2 Servo Search** <a href="#block-a6bc217fd8ab4580a5d12fd36fefec44" id="block-a6bc217fd8ab4580a5d12fd36fefec44"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ecd7407e-6d73-4394-9b73-b83370a878f5/image/w=1920,quality=90,fit=scale-down" alt="image" height="573.3844007939878" width="737.5750122070312">

After completing the communication settings, scan the servo devices connected to the bus.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3affe6f9-9c19-47ed-bf59-7bcebbd47c17/image/w=1920,quality=90,fit=scale-down" alt="image" height="425.4395611906705" width="202.9875030517578">

**Operation Steps:**

1. Confirm that the servo is properly powered.
2. Click the “Search” button.
3. The software will automatically scan all online servos on the bus.
4. After the scan is complete, the detected servos will be displayed in the device list.

💡

**Note:** If no servos are found after clicking Search, please check the following:

* Whether the servo power supply is normal
* Whether the communication cable connection is secure
* Whether the port number and baud rate settings are correct

### **3.3 Servo Operation** <a href="#block-4175dc55b9d040e590e51028c2d26eef" id="block-4175dc55b9d040e590e51028c2d26eef"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b326f949-5567-4eee-88ee-54698c0f40f3/image/w=1920,quality=90,fit=scale-down" alt="image" height="567.5539660113791" width="730.0750122070312">

The Servo Operation area provides three write modes and torque output control.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a255b0a6-7658-4e28-b835-fffd930a3101/image/w=1920,quality=90,fit=scale-down" alt="image" height="256.41030840545534" width="477.9875183105469">

#### **3.3.1 Write Mode** <a href="#block-3c6879c71592432a92a8b2d66bba268a" id="block-3c6879c71592432a92a8b2d66bba268a"></a>

| **Mode**           | **Description**                                                       | **Application Scenario**                      |
| ------------------ | --------------------------------------------------------------------- | --------------------------------------------- |
| Normal Write       | Single write command, waits for servo response confirmation           | Single servo control, parameter configuration |
| Synchronous Write  | Sends the same command to multiple servos simultaneously              | Synchronized multi-servo motion               |
| Asynchronous Write | Continuously sends commands without waiting for response confirmation | Continuous motion control                     |

#### **3.3.2 Torque Output** <a href="#block-799ebf7829fb47308a6a07e42d228ee3" id="block-799ebf7829fb47308a6a07e42d228ee3"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4b44a442-8ac0-4172-8e8b-9def36b579ca/image/w=1920,quality=90,fit=scale-down" alt="image" height="256.41030840545534" width="477.9875183105469">

The “Torque Enable” switch is used to control the servo torque enable state:

* ON: The servo outputs torque and responds to control commands.
* OFF: The servo releases torque, and the output shaft can rotate freely.

**Safety Note:** During debugging or installation, it is recommended to turn off the torque output first, and then turn it on after parameter configuration is complete, to avoid injury caused by unexpected motion.

### **3.4 Servo Feedback** <a href="#block-6a7d7f5f47c94da9880b40ae6b9e1a39" id="block-6a7d7f5f47c94da9880b40ae6b9e1a39"></a>

The Servo Feedback area displays the real-time operating status parameters of the currently selected servo.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e17b5390-5d9e-405c-8bfc-58047bb942c7/d8e715a5-5f0f-4157-9266-2de68b965c31/w=1920,quality=90,fit=scale-down" alt="image" height="244.42035222457628" width="337.9875183105469">

| **Parameter** | **Unit**                                  | **Description**                                                                                                          | **Normal Range**                                   |
| ------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------- |
| Voltage       | V                                         | Current supply voltage of the servo                                                                                      | Refer to servo specifications (typical value: 12V) |
| Current       | mA                                        | Current operating current of the servo                                                                                   | Negative value indicates current direction         |
| Temperature   | ℃                                         | Internal temperature of the servo                                                                                        | Normal range: 0-80℃                                |
| Movement      | -                                         | Servo movement status indicator                                                                                          | 0 = stationary, non-zero = moving                  |
| Status        | -                                         | Communication connection status                                                                                          | Normal / Abnormal                                  |
| Torque        | -                                         | Current output torque value of the servo. A negative value indicates direction (e.g., reverse rotation or braking state) | depending on load and current limit                |
| Speed         | RPM (revolutions per minute) or steps/sec | Current rotation speed of the servo. Positive/negative values indicate direction                                         | Depends on servo model and settings                |
| Position      | Steps                                     | Current actual position feedback value of the servo                                                                      | 0-4095 (corresponding to 0-360°)                   |
| Target        | Steps                                     | Target position setpoint of the servo                                                                                    | 0-4095 (corresponding to 0-360°)                   |

### **3.5 Auto Tuning** <a href="#block-4e8d892b810742478cb43068d3fece74" id="block-4e8d892b810742478cb43068d3fece74"></a>

The Auto Tuning function is used to make the servo automatically reciprocate along a preset trajectory, facilitating servo performance verification and durability testing.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/050d1a2c-3cc5-4157-bc01-bc66a6362b44/image/w=1920,quality=90,fit=scale-down" alt="image" height="145.40911084823026" width="507.9624938964844">

#### **3.5.1 Parameter Settings** <a href="#block-2cef776f418f47c58e9d3e5609850831" id="block-2cef776f418f47c58e9d3e5609850831"></a>

| **Parameter** | **Unit** | **Description**                                | **Setting Range**             |
| ------------- | -------- | ---------------------------------------------- | ----------------------------- |
| Start         | Steps    | Starting position for auto tuning              | 0-4095                        |
| Delay (Scan)  | ms       | Dwell time at each position point              | Recommended ≥ 1000            |
| Steps         | -        | Number of step movements in a single direction | Set according to travel range |
| Step Size     | Steps    | Angle step size per movement                   | 1-4095                        |

#### **3.5.2 Operation Steps** <a href="#block-5073ea5a308847319375d5083f422fbf" id="block-5073ea5a308847319375d5083f422fbf"></a>

**Operation Steps:**

1. Set the starting position value in the “Start” input box.
2. Set the “Delay (Scan)” time (unit: ms).
3. Set the “Steps” — number of step movements.
4. Set the “Step Size” — step value for each step movement.
5. Confirm that the servo torque output is enabled.
6. Click “Start” to begin auto tuning.

#### **3.5.3 Motion Logic** <a href="#block-5d917b54bab940a1add1a8b739452d57" id="block-5d917b54bab940a1add1a8b739452d57"></a>

The servo will perform auto tuning according to the following motion logic:

1. Start from the starting position.
2. Gradually increase the position by the “Step Size” value.
3. After reaching each position point, dwell for the “Delay (Scan)” time.
4. Repeat the above steps until the “Steps” number of step movements is completed.
5. Automatically return to the starting position.
6. Repeat the above process cyclically.**Note:** Before performing auto tuning, ensure there are no obstacles within the servo’s motion range to avoid damage to the servo or mechanical structure caused by collision.

## **4. Upgrade Interface** <a href="#block-a32eafed367c42cd8a724d506d5a021f" id="block-a32eafed367c42cd8a724d506d5a021f"></a>

The Upgrade interface is used for firmware updates of the connected servo.

### **4.1 Communication Test** <a href="#block-fe6bf88f0771406babc636d0cb178099" id="block-fe6bf88f0771406babc636d0cb178099"></a>

This section tests the communication status between the host computer and the servo.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c1bcca9a-542c-4ee1-9df5-87e3ef8337c3/image/w=1920,quality=90,fit=scale-down" alt="image" height="681.8933279562317" width="730.0750122070312">

| **Parameter** | **Description**                                      |
| ------------- | ---------------------------------------------------- |
| Servo ID      | The ID of the servo being tested                     |
| Response      | Response delay time in microseconds (µs)             |
| Timeout       | Communication timeout value (0 indicates no timeout) |
| Speed         | Measured communication speed (kb/s)                  |

**Buttons:**

Test – Initiates the communication test.

Clear – Clears the current test results.

### **4.2 Command Test** <a href="#block-878d11e3cf4c470fbd05c65e357fdc2e" id="block-878d11e3cf4c470fbd05c65e357fdc2e"></a>

This section allows manual sending of commands to the servo.

| **Parameter** | **Description**                                   |
| ------------- | ------------------------------------------------- |
| cmd           | Command code (e.g., 01: PING for connection test) |
| format        | Address format (e.g., ID)                         |

**Data:**

* Tx (Transmit) – Data to be sent to the servo (e.g., ReadMe)
* Rx (Receive) – Data received from the servo (e.g., Send)

### **4.3 Firmware Update** <a href="#block-60f0d18e40124b23bfd46d31ee9d5233" id="block-60f0d18e40124b23bfd46d31ee9d5233"></a>

This section is used to update the servo firmware.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/95c567a4-f859-4277-acca-34974cd34a96/image/w=1920,quality=90,fit=scale-down" alt="image" height="257.7606660810929" width="730.0499877929688">

| **Parameter** | **Description**                                    |
| ------------- | -------------------------------------------------- |
| Model         | Servo model number and chip type \[HLS3955]        |
| Version       | Current firmware version → Target firmware version |
| File          | Firmware file name (.bin)                          |
| Upload        | Timestamp of the selected firmware file            |

Progress Bar: Displays the firmware update progress (0% – 100%).

**Note:** Ensure stable power and communication during firmware update. Do not disconnect or power off during the process.

## **5. Frequently Asked Questions and Troubleshooting** <a href="#block-19102c9d8a60445bb8ed21bb5229e5a9" id="block-19102c9d8a60445bb8ed21bb5229e5a9"></a>

| **Symptom**                        | **Possible Cause**          | **Solution**                                                              |
| ---------------------------------- | --------------------------- | ------------------------------------------------------------------------- |
| Click Search but no servo found    | Incorrect port number       | Check the COM port corresponding to the URT-1 converter in Device Manager |
| Click Search but no servo found    | Baud rate mismatch          | Verify that the servo baud rate matches the software setting              |
| Click Search but no servo found    | Servo not powered           | Check the servo power connection                                          |
| Servo does not respond to commands | Torque output not enabled   | Click to enable “Torque Output”                                           |
| Feedback status shows abnormality  | Communication interference  | Check communication cables, lower baud rate and retry                     |
| Servo motion abnormal              | Improper parameter settings | Check whether Start, Steps, and Step Size parameters are reasonable       |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4aaa1a9d-9c43-4353-bcc6-47d3eb3d9ba8/image/w=1920,quality=90,fit=scale-down" alt="image" height="567.5539660113791" width="730.0750122070312">

<br>
