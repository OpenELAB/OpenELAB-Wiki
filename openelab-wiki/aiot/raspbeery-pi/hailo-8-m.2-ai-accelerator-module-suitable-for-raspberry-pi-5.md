---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Hailo-8 M.2 AI Accelerator Module Suitable for Raspberry Pi 5

### Hailo-8 M.2 AI Accelerator Module Suitable for Raspberry Pi 5

***

### Product Link

{% embed url="https://openelab.io/products/hailo-8-m-2-ai-accelerator-module" %}

### Introduction

Hailo-8/8L chip with 26/13Tops computing power.

### Feature

* Neural network inference accelerator with 13/26 trillion operations per second (TOPS) built on Hailo-8/8L chips.
* PCIE M.2 HAT+ for connecting the AI module to the Raspberry Pi 5.
* Support installing with hardware kit.
* Stackable GPIO pin header.

### Hardware Connection

Pay attention to the cable orientation, as shown below:<br>

<figure><img src="https://www.waveshare.com/w/upload/0/0e/Hailo-8-details-7.jpg" alt=""><figcaption></figcaption></figure>

### Working with Raspberry Pi

#### Update

```
#1: update the software
sudo apt update && sudo apt full-upgrade
sudo rpi-eeprom-update

#Configure CLI (Not required for 2024 or later version systems)  
sudo raspi-config
#Advanced Options -> Bootloader Version, select Latest. Then, click Finish or press ESC key to exit raspi-config 

#2: Update firmware
sudo rpi-eeprom-update -a
```

#### Identify Device

1: Enable the PCIE interface:

```
Connect the hardware, and the latest system system will detect the hardware, connect the hardware will automatically enable the PCIE interface
If not, you can execute: add "dtparam=pciex1" in /boot/firmware/config.txt 
```

2: Enable PCIE Gen3, add the following content in /boot/firmware/config.txt (Gne3 mode must be enabled):

```
dtparam=pciex1_gen=3
```

3: Reset the PI5 after modification, and then the device will be identified. (You can not reboot first and then reboot when the library is installed.)

#### Test Demo

rpicam-apps runs camera demo with Hailo AI Neural Network Accelerator.

Preparation:

```
1: Raspberry Pi 5 and Hailo-8 Acce A kit
2: Install 64-bit Raspberry Pi OS Bookworm
3: Install Raspberry Pi camera (for testing, use  to connect the CAM1 interface.)
```

1: Install and use the required dependencies for AI Kit:

```
sudo apt install hailo-all
```

2: Reboot the device:

```
sudo reboot
```

3: Check whether the driver is normal:

```
hailortcli fw-control identify

Or execute "dmesg | grep -i hailo" to check the log 

```

4: Check the camera:

```
rpicam-hello -t 10s
Please ensure the camera is in normal operation 
```

5: Clone rpicam-apps:

```
git clone --depth 1  ~/rpicam-apps
```

6: Test:

```
Object test
rpicam-hello -t 0 --post-process-file ~/rpicam-apps/assets/hailo_yolov6_inference.json --lores-width 640 --lores-height 640
Yolov8 model
rpicam-hello -t 0 --post-process-file ~/rpicam-apps/assets/hailo_yolov8_inference.json --lores-width 640 --lores-height 640
YoloX model
rpicam-hello -t 0 --post-process-file ~/rpicam-apps/assets/hailo_yolox_inference.json --lores-width 640 --lores-height 640
Yolov5 human and facial models
rpicam-hello -t 0 --post-process-file ~/rpicam-apps/assets/hailo_yolov5_personface.json --lores-width 640 --lores-height 640

Image segmentation
rpicam-hello -t 0 --post-process-file ~/rpicam-apps/assets/hailo_yolov5_segmentation.json --lores-width 640 --lores-height 640 --framerate 20
```

```
Posture estimation
rpicam-hello -t 0 --post-process-file ~/rpicam-apps/assets/hailo_yolov8_pose.json --lores-width 640 --lores-height 640
```

For more details, you can refer to [GitHub](https://github.com/hailo-ai/hailo-rpi5-examples), [Hailo official website](https://hailo.ai/developer-zone/).
