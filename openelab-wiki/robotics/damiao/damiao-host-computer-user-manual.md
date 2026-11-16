# DAMIAO Host Computer User Manual

> **DAMIAO Integrated Motor Module Host Computer User Manual**

[**DAMIAO Motor**DAMIAO Motor - The ultimate choice for high-precision and high-stability robot joint motors. Power your projects with reliable performance.github.com](https://github.com/dmBots/dmBot)

## **Host Computer Download Link** <a href="#block-33bd4c79856d818a9253e97747ea45c3" id="block-33bd4c79856d818a9253e97747ea45c3"></a>

[https://gitee.com/kit-miao/dm-tools/tree/d53bdbf58dcf32a5ffed02411c53f66320b36bf9/USB转CAN/上位机](https://gitee.com/kit-miao/dm-tools/tree/d53bdbf58dcf32a5ffed02411c53f66320b36bf9/USB%E8%BD%ACCAN/%E4%B8%8A%E4%BD%8D%E6%9C%BA)

## **1. Motor wiring diagram** <a href="#block-342d4c79856d806ba3ccefe906570e2f" id="block-342d4c79856d806ba3ccefe906570e2f"></a>

### **1.1 Main wiring diagram** <a href="#block-342d4c79856d80fea58be7f89bdb07c1" id="block-342d4c79856d80fea58be7f89bdb07c1"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f0477e99-400f-4e3c-95a2-05b692417594/image/w=1920,quality=90,fit=scale-down" alt="image" height="559.8540034280118" width="737.5625">

### **1.2 USB-to-CAN module wiring diagram** <a href="#block-342d4c79856d8015a90dd650d5aec7ee" id="block-342d4c79856d8015a90dd650d5aec7ee"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dc24b1ef-084e-4313-924f-347c56ae6c8e/image/w=1920,quality=90,fit=scale-down" alt="image" height="398.86204722496007" width="629.9874877929688">

### **1.3 Power adapter board wiring diagram** <a href="#block-342d4c79856d80528b90f948c2914f1b" id="block-342d4c79856d80528b90f948c2914f1b"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b4f24767-f384-4700-bd4f-a6d3d03ead01/image/w=1920,quality=90,fit=scale-down" alt="image" height="521.1329746198294" width="737.5750122070312">

## **2. Connecting devices** <a href="#block-33bd4c79856d80bdb42ed8ba947ca46d" id="block-33bd4c79856d80bdb42ed8ba947ca46d"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9eaac05e-99ce-4dc3-917b-b0b51c7fde77/1/w=1920,quality=90,fit=scale-down" alt="image" height="267.115652039555" width="423.71875">

Connect the motor's serial port, CAN port, and power interface. Open the debugging assistant software on the computer, select the corresponding serial port device, and open the serial port.

When power is supplied to the motor at this time, the serial port will print the following information. Control Mode: Indicates the current drive mode. Different modes use different command formats.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/61042533-3036-4e9d-b34f-a06347b26825/3/w=1920,quality=90,fit=scale-down" alt="image" height="268.9944203347799" width="423.71875">

## **3. Read firmware version** <a href="#block-33bd4c79856d80ab8a77f8d38d3870bb" id="block-33bd4c79856d80ab8a77f8d38d3870bb"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cd806601-3c48-440d-85b9-c81c424d1a0e/image/w=1920,quality=90,fit=scale-down" alt="image" height="252.84002353556482" width="222.984375">

## **4. Calibration** <a href="#block-33bd4c79856d800ba8e3f47e1ba62ded" id="block-33bd4c79856d800ba8e3f47e1ba62ded"></a>

### 4.1 Motor-side encoder <a href="#block-33bd4c79856d80fb97b5f1b086e7cb88" id="block-33bd4c79856d80fb97b5f1b086e7cb88"></a>

The calibration process primarily corrects sensor installation errors. During this process, the motor will rotate in both directions for one rotor cycle. Please ensure the motor can rotate freely, ideally running under no-load conditions; otherwise, calibration may fail.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4e8fed93-582e-4f2a-9fb9-9e20a4a71c8c/image/w=1920,quality=90,fit=scale-down" alt="image" height="119.92125984251969" width="237.96875">

Sensor Calibration: Click "Calibrate." The motor will rotate first, and after rotation, it will return the pole pair number to the debugging assistant. Simultaneously, the motor will rotate in both directions to calibrate the sensor data. Please ensure the motor is securely fixed to prevent accidents.

After parameter identification is completed, the motor will automatically perform sensor calibration and display the motor's sensor waveform diagram

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8e4ff45d-f35f-4f9e-9199-f1f4a75a9d46/2/w=1920,quality=90,fit=scale-down" alt="image" height="277.6246527777778" width="395.3515625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8ac0660c-4682-498f-a6a5-bb5847147569/5/w=1920,quality=90,fit=scale-down" alt="image" height="211.04390554298644" width="341.2734375">

1. After calibration is complete, the calibration values will be automatically uploaded.
2. Once calibration is complete, a screenshot showing the calibration results will automatically pop up.
3. Special attention should be paid to the value of "Compensation Data," and it is recommended that it not exceed ±300. If it exceeds 300, there may be several reasons:
4. Error in identifying pole logarithms;
5. Excessive motor resistance causes jamming;
6. The sensor was not installed correctly;

💡

\[Note] The maximum value of the red curve should not significantly exceed that of the blue curve; otherwise, the test will fail, and you will need to recalibrating.

### 4.2 Output shaft encoder calibration <a href="#block-33bd4c79856d805ca32af19aa91ba05b" id="block-33bd4c79856d805ca32af19aa91ba05b"></a>

Dual-encoder motors require output shaft encoder calibration to improve output shaft encoder accuracy. During this process, the motor will rotate in the forward direction; please ensure the motor can rotate freely and is running under no-load conditions. Otherwise, excessive calibration errors may occur. The motor has already undergone output shaft encoder calibration at the factory, and this calibration is written into the motor. Under normal circumstances, it can be used directly without further output shaft encoder calibration. The following provides the operating steps for output shaft encoder calibration. In abnormal situations such as when the motor driver board is replaced or the output position changes, output shaft encoder calibration should be performed before operation.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/20c77913-d703-47be-aec9-4c274353c34a/1/w=1920,quality=90,fit=scale-down" alt="image" height="316.305934382793" width="500.84375">

Click the slider next to the calibration button until it displays "Output Shaft Encoder", then click calibrate.

The motor starts rotating and uploads the raw data waveform from the encoder.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/65362500-7b12-473b-99ee-f29fa30e0091/image/w=1920,quality=90,fit=scale-down" alt="image" height="320.8827827946768" width="500.84375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dd1f3fe7-4516-40d8-ae28-520b4d166ec6/image/w=1920,quality=90,fit=scale-down" alt="image" height="398.0106144514768" width="500.859375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/26252942-c8f2-4805-8edf-a8ab43dfb2e1/image/w=1920,quality=90,fit=scale-down" alt="image" height="309.96078187251" width="500.859375">

After calibration is complete, the calibration values will be automatically uploaded and displayed.

## **5. Parameter calibration** <a href="#block-33bd4c79856d8034bb89fd4ab1a34c18" id="block-33bd4c79856d8034bb89fd4ab1a34c18"></a>

Parameter identification mainly involves determining key parameters of the motor such as phase resistance, phase inductance, and magnetic flux linkage.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fa3a413a-1e30-4096-b6c6-f0402727db6c/image/w=1920,quality=90,fit=scale-down" alt="image" height="663.6341248764822" width="1047.734375">

Click the "Parameter Settings" tab, then click the "Parameter Calibration" button to start the identification process. During this process, the motor will rotate. It is recommended to keep the motor unloaded and securely fixed.

Once the identification is complete, the results will be uploaded automatically.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6fcd9562-ca8b-4167-9373-883eca4ff62b/image/w=1920,quality=90,fit=scale-down" alt="image" height="256.82065651633525" width="337.7749938964844">

💡

The above parameters cannot contain negative values. If a negative value is found, please confirm the motor status before recalibrating.

## **6. Read/Write Parameters** <a href="#block-33bd4c79856d8001889fc78dabd997b9" id="block-33bd4c79856d8001889fc78dabd997b9"></a>

### **6.1 Read Parameters** <a href="#block-33dd4c79856d80b38f70d075590601ea" id="block-33dd4c79856d80b38f70d075590601ea"></a>

To read parameters, under the "Parameter Settings" tab, click the "Read Parameters" button. The driver will then upload the parameters it stores and uses to the debugging assistant.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/599752b2-96f7-4bad-bff7-95402716ad64/image/w=1920,quality=90,fit=scale-down" alt="image" height="624.4458740900819" width="1047.734375">

#### 6.1.1 Motor Parameters <a href="#block-33bd4c79856d809ab465e3ac52fb1a72" id="block-33bd4c79856d809ab465e3ac52fb1a72"></a>

The parameters in this section are automatically identified by the driver. (If the driver board is replaced, parameter calibration is required once, and these parameters will be automatically saved to the driver).

| Parameter Name                              | Description                                                                                                                                                                                                                                 |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Npp（Number of pole pairs）                   | The number of pole pairs of the motor, which can be automatically determined through calibration.                                                                                                                                           |
| Gr (Gear Ratio)                             | The Gear Ratio of a motor primarily affects the motor's output speed and position, indirectly influencing the motor's torque feedback information. It can be set as a floating-point number.                                                |
| Acc/Dec (Acceleration/Deceleration)         | Used in non-MIT mode to limit the acceleration/deceleration of the driver.                                                                                                                                                                  |
| UV (Undervoltage)                           | If the power supply voltage falls below the set value, the driver will stop operating. T**he power supply voltage must not be lower than 15V**.                                                                                             |
| OV (Overvoltage)                            | Sets the upper voltage limit for the driver's operation. When the motor is powered on, the power supply voltage is sampled. If the sampled voltage exceeds this value, the driver will stop working and will only run once upon power-on.   |
| OT (Over-temperature)                       | The motor coil temperature protection value should be set according to usage requirements, but is recommended not to exceed 100℃. Upon over-temperature detection, the driver will deactivate, enter a disabled state, and report an error. |
| OC (Overcurrent)                            | Used to limit the maximum phase current of the motor, as a percentage.                                                                                                                                                                      |
| Spd Limit (Speed Limit)                     | Used only in speed mode to limit the maximum operating speed of the motor before deceleration, measured in rad/d/s.                                                                                                                         |
| fbw(Velocity Loop Filter Bandwidth)         | Speed filter bandwidth (**unit: Hz**)                                                                                                                                                                                                       |
| Ki\_speed(Velocity loop boost coefficient)  | Velocity loop auxiliary control parameter, with recommended adjustable range of 200–800.                                                                                                                                                    |
| Ki\_current(Current loop boost coefficient) | Current loop auxiliary control parameter, **do not recommend modification**.                                                                                                                                                                |

#### 6.1.2 Communication Parameters <a href="#block-33bd4c79856d800cbc7fdafc02268095" id="block-33bd4c79856d800cbc7fdafc02268095"></a>

| Parameter Name | Description                                                                                                                                                                                    |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CAN ID         | The frame ID number (hexadecimal) of the CAN command received by the driver;                                                                                                                   |
| Master ID      | The frame ID number used for driver feedback information, in hexadecimal                                                                                                                       |
| CAN Timeout    | CAN communication timeout setting, 32-bit integer, indicating the number of count cycles after which no CAN command is detected before motor protection is initiated. One count cycle is 50µs. |
| CAN baud rate  | Configure the CAN baud rate, **supporting 125Kbps–5Mbps.**                                                                                                                                     |

#### **6.1.3 Control amplitude** Parameters <a href="#block-33cd4c79856d80b9b0dfc07f0898ec4c" id="block-33cd4c79856d80b9b0dfc07f0898ec4c"></a>

| Parameter Name   | Description                                                                                                                                                             |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PMAX             | In MIT mode, it serves as the mapping value for commands received by the motor; in other modes, it serves as the mapping value for feedback information from the motor. |
| VMAX             | Same as the PMAX parameter.                                                                                                                                             |
| TMAX             | Same as the PMAX parameter.                                                                                                                                             |
| KT\_OUT          | The torque coefficient of the motor. If the motor parameter identification is accurate, set it to 0.                                                                    |
| Gear coefficient | Gear torque transmission coefficient, less than or equal to 1.0.                                                                                                        |
| Damping factor   | Current loop to velocity loop control bandwidth ratio **(not used).**                                                                                                   |

#### **6.1.4 Control setting parameters** <a href="#block-33cd4c79856d80d8a62fc0d22ace57d9" id="block-33cd4c79856d80d8a62fc0d22ace57d9"></a>

| Parameter Name                  | Description                                                                                                |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Control Mode                    | The control modes include MIT mode, position-velocity mode, velocity mode, and force-position hybrid mode. |
| Current bandwidth               | Set the gain coefficient of the current loop; the default value is 1000.                                   |
| velocity KP/KI & position KP/KI | Parameters of the velocity loop and position loop.                                                         |

### **6.2 Write Parameters** <a href="#block-33bd4c79856d8011aaf9ec2a34a86767" id="block-33bd4c79856d8011aaf9ec2a34a86767"></a>

Check drive parameters, control amplitude, control settings, and other parameters. Modify any parameters that need to be changed. Finally, click "Write Parameters" to save the modified parameters to the driver.

Clicking the "Write Parameters" button will automatically reset the chip. Therefore, when using "Write Parameters", please ensure that the motor is in the "disabled" state to prevent safety accidents.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f4bf46f3-a60b-4347-bc89-b17f012b53f5/image/w=1920,quality=90,fit=scale-down" alt="image" height="191.0610794221512" width="753.5875244140625">

💡

**Note：**

1. Do not modify the number of pole pairs or the reduction ratio parameters.
2. After clicking "Write Parameters", the driver will automatically perform a software restart; no external power reset is required.
3. The "Temporary Storage" button only takes effect for controller parameters and will be lost after power-off.

## 7. Debug <a href="#block-33dd4c79856d809a9c62f94a9c3b0654" id="block-33dd4c79856d809a9c62f94a9c3b0654"></a>

This function can only be operated when connected to the CAN interface. It can only debug a single motor. Before operation, connect the CAN cable to the driver board. Before debugging, confirm the wiring sequence and the current control mode, and select the corresponding sub-tab on the debugging page according to the different modes.

### **7.1 Selection and confirmation of the control mode** <a href="#block-33dd4c79856d80b4ace9e6d0b5e8ddde" id="block-33dd4c79856d80b4ace9e6d0b5e8ddde"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/12d82e59-bb6d-4005-9ff1-0077dfe466fb/image/w=1920,quality=90,fit=scale-down" alt="image" height="477.6426923076923" width="753.5625">

Click "Parameter Settings" in the debugging assistant, then click "Control Mode" in the control settings. You can select among four modes: MIT mode, position-velocity mode, velocity mode, and force-position hybrid mode. Then click "Write Parameters" to set the control mode.

1. When modifying the control mode, a prompt window will pop up: "Write Parameters Successful!".
2. Since the "Write Parameters" function automatically resets, there is no need to power cycle the driver for the changes to take effect.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/30cde6f1-70c7-4a25-a9a9-034cd1fdf009/image/w=1920,quality=90,fit=scale-down" alt="image" height="472.4247018423285" width="753.5750122070312">

### **7.2 MIT Mode** <a href="#block-33dd4c79856d8022b3b1c7b9b7dcd40e" id="block-33dd4c79856d8022b3b1c7b9b7dcd40e"></a>

1. Refer to "Selection and Confirmation of the Control Mode". Select the current mode as MIT mode, confirm the current control mode, and then select the corresponding MIT sub-tab on the debugging page.
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/948ff0e2-fa96-4e8a-8ee3-051d38542a23/image/w=1920,quality=90,fit=scale-down" alt="image" height="475.16059883004925" width="753.5750122070312">
3. Ensure the CAN ID is correct (it can be obtained through serial port print information or the parameter settings page, and can also be read or set using the read/set buttons on the debug page).
4.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8e2d4bba-d3f7-4500-becb-6ea0bdefa4b8/image/w=1920,quality=90,fit=scale-down" alt="image" height="141.11189824365053" width="753.5375366210938">

#### **7.2.1 Speed control** <a href="#block-33dd4c79856d801d92d7efd2ebc7ca1a" id="block-33dd4c79856d801d92d7efd2ebc7ca1a"></a>

1. Click the "Enable" button in the motor mode section. At this time, the green LED on the driver lights up, indicating that the motor is enabled.
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/51396d48-33bc-4ccc-844a-e8f2aa10b10d/image/w=1920,quality=90,fit=scale-down" alt="image" height="182.18614333832335" width="753.5625">
3. Apply a speed command to make the motor run at the given speed.
4. For example: set the speed command to 5 rad/s, set KD to 0.2 N·s/rad, set all other parameters to 0, check the "Periodic Send" box, then click the "Update" button and the "Send" button in sequence. The parameter curve graph can be viewed on the debugging interface.
5.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bd5b15e8-c0ab-43a1-9aa3-70ac94893ba0/image/w=1920,quality=90,fit=scale-down" alt="image" height="475.91160386305586" width="753.5750122070312">
6. 💡
7. Note: **Secure the motor.**
8. According to debugging requirements, it is necessary to modify control parameters and observe the debugging changes. Modify the parameters directly in the original interface, keep the "Periodic Send" box checked, and click the "Update" button to perform debugging.
9.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/83ab1db6-8db0-47ce-8d8c-b83adc0a95c9/image/w=1920,quality=90,fit=scale-down" alt="image" height="136.55951704545453" width="258.9921875">
10. The debugging assistant interface displays the current motor and driver temperature as well as the motor operating status in real time. This information can also be viewed via the feedback frame. The feedback frame format and status types are as follows.
11. When exiting debugging, click the "Stop" and "Disable" buttons in sequence. The red LED on the driver lights up, indicating that the motor mode has been exited.
12.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/24f3b88a-b18b-4dd3-b69b-58d3abf173c7/image/w=1920,quality=90,fit=scale-down" alt="image" height="475.54579940197743" width="753.5750122070312">

#### **7.2.2 Position control** <a href="#block-33dd4c79856d80b89ad6ddb0fda47e38" id="block-33dd4c79856d80b89ad6ddb0fda47e38"></a>

1. Click the "Enable" button in the motor mode section. At this time, the green LED on the driver lights up, indicating that the motor is enabled.
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/82824bbf-b05e-4840-9677-b0270cdc66a1/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.58727650975402" width="753.5375366210938">
3. Apply a position command to make the motor rotate to the specified position.
4. At this time, pay attention to the initial position of the motor. When assigning a value to the "Position" parameter in the control parameters section, avoid a large deviation from the initial position to prevent motor impact.
5.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3d490efe-6082-473c-bdd3-06f0b848df3c/image/w=1920,quality=90,fit=scale-down" alt="image" height="179.42262195405505" width="753.5750122070312">
6. You can click "Save Zero Position" in the control command bar to set the current motor position as the zero point, which facilitates the setting of the "Position" parameter.
7. For example, set the parameters: position command to 3.14 rad, KP to 0.5N/rad, KD to 0.1N·s/rad, set all other parameters to 0, check the "Periodic Send" box, then click the "Update" button and the "Send" button in sequence. The parameter curve graph can be viewed on the debugging interface.
8.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1f75c26f-bfb5-47d5-985f-213255a4ee17/image/w=1920,quality=90,fit=scale-down" alt="image" height="535.099254436928" width="753.5750122070312">
9. 💡
10. Note: **Secure the motor.**
11. According to debugging requirements, it is necessary to modify control parameters and observe the debugging changes. Modify the parameters directly in the original interface, keep the "Periodic Send" box checked, and click the "Update" button to perform debugging.
12. The debugging assistant interface displays the current motor and driver temperature as well as the motor operating status in real time. This information can also be viewed via the feedback frame. The feedback frame format and status types are as follows.
13. When exiting debugging, click the "Stop" and "Disable" buttons in sequence. The red LED on the driver lights up, indicating that the motor mode has been exited.

#### **7.2.3 MIT torque control** <a href="#block-33dd4c79856d80239c60c29aacb84b02" id="block-33dd4c79856d80239c60c29aacb84b02"></a>

1. Follow the same first step as in speed control and position control to enable the motor.
2. Apply a torque command to debug the motor.
3. For example, set the torque command to 1 N·m, set all other parameters to 0, check the "Periodic Send" box, then click the "Update" button and the "Send" button in sequence. The parameter curve graph can be viewed on the debugging interface.
4.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/19d27469-e6be-4499-8a2a-ff524041097d/image/w=1920,quality=90,fit=scale-down" alt="image" height="530.8290978994748" width="753.5625">
5. When exiting debugging, click the "Stop" and "Disable" buttons in sequence. The red LED on the driver lights up, indicating that the motor mode has been exited.

### **7.3 Position-velocity mode** <a href="#block-33dd4c79856d80ec9fcadf28af709509" id="block-33dd4c79856d80ec9fcadf28af709509"></a>

1. To debug the position-velocity mode, you need to switch the motor mode to position-velocity mode on the parameter page, then click "Write Parameters" for the change to take effect. On the debugging page, select the corresponding "Position" sub-tab.
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/33baa140-4890-4880-a8a4-53f604bc2578/image/w=1920,quality=90,fit=scale-down" alt="image" height="181.9744103551794" width="753.5750122070312">
3. Ensure the CAN ID is correct (it can be obtained through serial port print information or the parameter settings page, and can also be read or set using the read/set buttons on the debug page).
4.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/87a78df4-ec36-45cc-b735-4bdb9f7b0ec7/image/w=1920,quality=90,fit=scale-down" alt="image" height="172.91206169487168" width="753.5375366210938">
5. Click the "Enable" button in the motor mode section. At this time, the green LED on the driver lights up, indicating that the motor is enabled.
6.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/33b641a3-fc52-4f64-8a6f-780eb2ae6004/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.97406539916992" width="753.5750122070312">
7. Set the parameters, and the motor will run to the specified position at the set speed.
8.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/76e4ce86-bc88-4a47-9f4f-f064579000ff/image/w=1920,quality=90,fit=scale-down" alt="image" height="198.44856118689452" width="753.5375366210938">
9. 💡
10. Before setting the parameters, pay attention to the initial position of the motor and use it as a reference to configure the parameters.
11. Set the parameters: position to 10 rad, velocity to 5 rad/s. Check the "Periodic Send" box, then click the "Update" button and the "Send" button in sequence. The parameter curve graph can be viewed on the debugging interface.
12.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fb27a0dc-cb8d-4ddc-802b-52b9b03aabda/image/w=1920,quality=90,fit=scale-down" alt="image" height="479.124853440273" width="753.5750122070312">
13. 💡
14. Note: **Secure the motor.**
15. When exiting debugging, click the "Stop" and "Disable" buttons in sequence. The red LED on the driver lights up, indicating that the motor mode has been exited.

### **7.4 Velocity mode** <a href="#block-33dd4c79856d800ebaede4ab8a2f570d" id="block-33dd4c79856d800ebaede4ab8a2f570d"></a>

1. Refer to "Selection and Confirmation of the Control Mode". Select the current mode as velocity mode, confirm the current control mode, and then select the corresponding "Velocity" sub-tab on the debugging page.
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e84ff4e0-69b2-4047-b8a6-de683267671a/image/w=1920,quality=90,fit=scale-down" alt="image" height="186.42496262616956" width="753.5375366210938">
3. Ensure the CAN ID is correct (it can be obtained through serial port print information or the parameter settings page, and can also be read or set using the read/set buttons on the debug page).
4.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/073eb679-c0e4-46cd-ab29-22aa7e667d0b/image/w=1920,quality=90,fit=scale-down" alt="image" height="174.261328125" width="753.5625">
5. Click the "Enable" button in the motor mode section. At this time, the green LED on the driver lights up, indicating that the motor is enabled.
6.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2bd99a84-391d-43fb-982a-5ab9c3882fce/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.97406539916992" width="753.5750122070312">
7. Set the parameters, and the motor will run at the set speed.
8. For example, set the parameter: velocity to 20 rad/s. Check the "Periodic Send" box, then click the "Update" button and the "Send" button in sequence. The parameter curve graph can be viewed on the debugging interface.
9.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fe2b2b70-d930-4d73-a633-32eb80d9a048/image/w=1920,quality=90,fit=scale-down" alt="image" height="462.00407206752436" width="753.5875244140625">
10.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/82359292-154b-455f-acec-0943c75d430f/cf318b3d-62e8-4278-b0c2-1c71ab5c267a/w=1920,quality=90,fit=scale-down" alt="image" height="472.13593368716806" width="753.5750122070312">
11. 💡
12. Note: **Secure the motor.**
13. When exiting debugging, click the "Stop" and "Disable" buttons in sequence. The red LED on the driver lights up, indicating that the motor mode has been exited.

### 7.5 Force-Position Hybrid Control Mode <a href="#block-345d4c79856d80f28558ddafce5b84e9" id="block-345d4c79856d80f28558ddafce5b84e9"></a>

1. To debug the force-position hybrid control mode, you need to switch the motor mode to PVT mode on the parameter page, then click "Write Parameters" for the change to take effect. After that, select the corresponding "Position" sub-tab on the debugging page.
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/668eb6d6-b39e-40c6-b92d-489976ea1380/image/w=1920,quality=90,fit=scale-down" alt="image" height="187.93170361930942" width="753.5875244140625">
3. Ensure that the CAN ID is correct. It can be obtained via the serial port printing information or the parameter settings page, and can also be read or set using the read/set buttons on the debugging page.
4.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/df7e9244-6055-4371-a02f-0b23503f9b33/image/w=1920,quality=90,fit=scale-down" alt="image" height="183.65998892171345" width="753.5625">
5. Click the "Enable" button in the motor mode section. The green LED on the driver will then light up, indicating that the motor is enabled.
6.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dedc4423-45a6-401d-977d-777d5fbea9f6/image/w=1920,quality=90,fit=scale-down" alt="image" height="200.72239258175804" width="753.5499877929688">
7. Set the parameters, and the motor will run to the specified position at the set speed.
8. Before setting the parameters, pay attention to the initial position of the motor and use it as a reference for parameter configuration.
9.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/430e6b4c-9b91-423d-b751-a416b51b4f74/image/w=1920,quality=90,fit=scale-down" alt="image" height="223.44700139570978" width="753.5750122070312">
10. For example, set the parameters as follows: position to 10 rad, speed to 5 rad/s, and current to 20%. Then check the "Periodic Send" box, and click the "Update" button followed by the "Send" button. You can then view the parameter curve changes on the debugging interface.
11.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/58320f60-a3e8-4b15-b540-594dc81d9d05/image/w=1920,quality=90,fit=scale-down" alt="image" height="529.4347521659655" width="753.5750122070312">
12.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6bcafcdd-292d-4189-a00e-f59bd3bd4fb8/image/w=1920,quality=90,fit=scale-down" alt="image" height="477.6426923076923" width="753.5625">

💡

Note: **Secure the motor.**

6. When exiting debugging, first ensure that the motor has stopped, then click the "Stop" button followed by the "Disable" button. The red LED on the driver will light up, indicating that the motor has exited the motor mode.
7.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/247ab652-e7b0-4f33-aa50-64ed5587ad08/image/w=1920,quality=90,fit=scale-down" alt="image" height="554.2078654883688" width="753.5875244140625">

## 8. Firmware Version Check and Upgrade <a href="#block-33ed4c79856d80eab970c5101eed2120" id="block-33ed4c79856d80eab970c5101eed2120"></a>

### **8.1 View version** <a href="#block-33ed4c79856d80ee9940d1fc39cd0199" id="block-33ed4c79856d80ee9940d1fc39cd0199"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9d57ec3d-f0c7-4b2a-9f6b-e165d47cbdfd/image/w=1920,quality=90,fit=scale-down" alt="image" height="215.59248046875" width="223.9921875">

Connect the serial port, CAN port, and power interface of the motor. Choose the appropriate serial port device, open the port, and click 'Read Version' to check the driver's current software version.

💡

**When upgrading the firmware, please read the current version first. Unless otherwise specified, select the firmware whose version number starts with '72' (the first two digits) for upgrade; otherwise, unknown issues may occur, causing unnecessary trouble.**

### **8.2 Serial Port Firmware Upgrade** <a href="#block-33ed4c79856d80e0be71efe5c572e10d" id="block-33ed4c79856d80e0be71efe5c572e10d"></a>

When new firmware adds new features or an upgraded version fixes bugs, users can upgrade via the serial port to resolve issues and use new features. Before use, connect the serial port, then click "Firmware Selection" and select the corresponding firmware. After clicking "Open", the firmware name will be displayed in the firmware name field. Once confirmed, click the firmware upgrade button and wait for the upgrade progress bar to complete. You can also monitor whether the upgrade is completed via the serial port interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/42f650d3-3b4f-46c1-a598-32d2c2017b0e/image/w=1920,quality=90,fit=scale-down" alt="image" height="476.106010210396" width="753.5625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1dd4755c-55f2-4f00-a54a-13a74bb7a2e4/image/w=1920,quality=90,fit=scale-down" alt="image" height="474.47315583405674" width="753.5750122070312">

### **8.3 CAN firmware upgrade** <a href="#block-33ed4c79856d80e2921af2b77c0e015f" id="block-33ed4c79856d80e2921af2b77c0e015f"></a>

Bootloader version 3.2.0.5 and above supports firmware upgrade via CAN, using the baud rate configured on the driver board. Currently, only USB-to-CAN adapters are supported for upgrades. Before use, connect the CAN interface and ensure normal CAN communication. Then, in the USB Mode section, switch from UART to CAN, and enter the motor ID to be upgraded in the left box. If the bus does not exist, a corresponding prompt will appear, as shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5a5d3607-4eff-4452-ac54-531d3c71385e/image/w=1920,quality=90,fit=scale-down" alt="image" height="477.80855263157895" width="753.5750122070312">

💡

**If the connection is successful, no prompt will appear.**&#x20;

Then click "Firmware Selection" and select the corresponding firmware. After clicking "Open", the firmware name will be displayed in the firmware name field. Once confirmed, click the firmware upgrade button and wait for the upgrade progress bar to complete. You can also monitor whether the upgrade is completed via the serial port interface.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/decdf312-3826-48bc-8c06-36c6a14def66/image/w=1920,quality=90,fit=scale-down" alt="image" height="477.88031832298134" width="753.5625">

After the upgrade is completed, a corresponding prompt will appear on the serial port interface.
