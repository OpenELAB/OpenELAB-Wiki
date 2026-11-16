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

# M.2 HAT for Raspberry Pi 5

### M.2 HAT for Raspberry Pi 5

***

### Produtc Link

{% embed url="https://openelab.io/products/m-2-hat-for-raspberry-pi-5" %}

### Introduction

The AI module is a 13 tera-operations per second (TOPS) neural network inference accelerator built around the Hailo-8L chip. The module uses the M.2 2242 form factor, and comes pre-installed in the M.2 HAT+, to which it connects through an M key edge connector. The M.2 HAT+ communicates between the AI module’s M.2 interface and the Raspberry Pi 5’s PCIe 2.0 interface.

When the host Raspberry Pi 5 is running an up-to-date Raspberry Pi OS image, it automatically detects the Hailo module and makes the NPU available for AI computing tasks. The built-in spam-apps camera applications in Raspberry Pi OS natively support the AI module, automatically using the NPU to run compatible post-processing tasks.

### Features

* Single-lane PCIe 2.0 interface (500 MB/s peak transfer rate)
* Supports devices that use the M.2 M key edge connector
* Supports devices with the 2230 or 2242 form factor
* Supplies up to 3A to connected M.2 devices
* Power and activity LEDs
* Conforms to the [Raspberry Pi HAT+ specification](https://datasheets.raspberrypi.com/hat/hat-plus-specification.pdf)
* Includes:
  * ribbon cable
  * 16mm GPIO stacking header
  * 4 threaded spacers
  * 8 screws
  * 1 knurled double-flanged drive attachment screw to secure and support the M.2 peripheral

### Specifications

Contains a neural network inference accelerator capable of 13 tera-operations per second (TOPS)

Fully integrated into Raspberry Pi’s camera software stack

Thermal pad pre-fitted between module and HAT+ spreads heat across components, improving performance

Conforms to Raspberry Pi HAT+ specification

Supplied with 16mm stacking header, spacers, and screws to enable fitting on Raspberry Pi 5 with Raspberry Pi Active Cooler in place

### Pinout

<figure><img src="../../.gitbook/assets/image (883).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (882).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### Install <a href="#m2-hat-plus-installation" id="m2-hat-plus-installation"></a>

To use the Raspberry Pi M.2 HAT+, you will need:

* a Raspberry Pi 5

Each M.2 HAT+ comes with a ribbon cable, GPIO stacking header, and mounting hardware. Complete the following instructions to install your M.2 HAT+:

1.  First, ensure that your Raspberry Pi runs the latest software. Run the following command to update:

    ```
    $ sudo apt update && sudo apt full-upgrade
    ```
2.  Next, [ensure that your Raspberry Pi firmware is up-to-date](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#update-the-bootloader-configuration). Run the following command to see what firmware you’re running:

    ```
    $ sudo rpi-eeprom-update
    ```

    If you see December 6, 2023 or a later date, proceed to the next step. If you see a date earlier than December 6, 2023, run the following command to open the Raspberry Pi Configuration CLI:

    ```
    $ sudo raspi-config
    ```

    Under `Advanced Options` > `Bootloader Version`, choose `Latest`. Then, exit `raspi-config` with `Finish` or the **Escape** key.

    Run the following command to update your firmware to the latest version:

    ```
    $ sudo rpi-eeprom-update -a
    ```

    Then, reboot with `sudo reboot`.
3. Disconnect the Raspberry Pi from power before beginning installation.
4.  The M.2 HAT+ is compatible with the Raspberry Pi 5 Active Cooler. If you have an Active Cooler, install it before installing the M.2 HAT+.



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-01.png?hash=8ec5865c09d8cf67c0fbb593304755f4" alt=""><figcaption></figcaption></figure>
5.  Install the spacers using four of the provided screws. Firmly press the GPIO stacking header on top of the Raspberry Pi GPIO pins; orientation does not matter as long as all pins fit into place. Disconnect the ribbon cable from the M.2 HAT+, and insert the other end into the PCIe port of your Raspberry Pi. Lift the ribbon cable holder from both sides, then insert the cable with the copper contact points facing inward, towards the USB ports. With the ribbon cable fully and evenly inserted into the PCIe port, push the cable holder down from both sides to secure the ribbon cable firmly in place.



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-02.png?hash=c59aa98734a3334cde67ebc8387f27ee" alt=""><figcaption></figcaption></figure>
6.  Set the M.2 HAT+ on top of the spacers, and use the four remaining screws to secure it in place.



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-03.png?hash=86ee6cde9d89679b56452add4d0a53ef" alt=""><figcaption></figcaption></figure>
7.  Insert the ribbon cable into the slot on the M.2 HAT+. Lift the ribbon cable holder from both sides, then insert the cable with the copper contact points facing up. With the ribbon cable fully and evenly inserted into the port, push the cable holder down from both sides to secure the ribbon cable firmly in place.



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-04.png?hash=0c2e813a36e988f85e317067de8c151b" alt=""><figcaption></figcaption></figure>
8.  Remove the drive attachment screw by turning the screw counter-clockwise. Insert your M.2 SSD into the M.2 key edge connector, sliding the drive into the slot at a slight upward angle. Do not force the drive into the slot: it should slide in gently.



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-05.png?hash=761bdd2e056ec948078c68c78eb127d2" alt=""><figcaption></figcaption></figure>
9.  Push the notch on the drive attachment screw into the slot at the end of your M.2 drive. Push the drive flat against the M.2 HAT+, and insert the SSD attachment screw by turning the screw clockwise until the SSD feels secure. Do not over-tighten the screw.



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-06.png?hash=c69a935c08589cff0531c1fa82644310" alt=""><figcaption></figcaption></figure>
10. Congratulations, you have successfully installed the M.2 HAT+. Connect your Raspberry Pi to power; Raspberry Pi OS will automatically detect the M.2 HAT+. If you use Raspberry Pi Desktop, you should see an icon representing the drive on your desktop. If you don’t use a desktop, you can find the drive at `/dev/nvme0n1`. To make your drive automatically available for file access, consider [configuring automatic mounting](https://www.raspberrypi.com/documentation/computers/configuration.html#automatically-mount-a-storage-device).



    <figure><img src="https://www.raspberrypi.com/documentation/accessories/images/m2-hat-plus-installation-07.png?hash=59ace8c3c7a33e8435e6e5b2484e8c6d" alt=""><figcaption></figcaption></figure>

| Warning | Always disconnect your Raspberry Pi from power before connecting or disconnecting a device from the M.2 slot. |
| ------- | ------------------------------------------------------------------------------------------------------------- |

#### Boot from NVMe

To boot from an NVMe drive attached to the M.2 HAT+, complete the following steps:

1. [Format your NVMe drive using Raspberry Pi Imager](https://www.raspberrypi.com/documentation/computers/getting-started.html#raspberry-pi-imager). You can do this from your Raspberry Pi if you already have an SD card with a Raspberry Pi OS image.
2. Boot your Raspberry Pi into Raspberry Pi OS using an SD card or USB drive to alter the boot order in the persistent on-board EEPROM configuration.
3. In a terminal on your Raspberry Pi, run `sudo raspi-config` to open the Raspberry Pi Configuration CLI.
4. Under `Advanced Options` > `Boot Order`, choose `NVMe/USB boot`. Then, exit `raspi-config` with `Finish` or the **Escape** key.
5. Reboot your Raspberry Pi with `sudo reboot`.

For more information, see [NVMe boot](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#nvme-ssd-boot).

#### Enable PCIe Gen 3

<table data-header-hidden><thead><tr><th width="163"></th><th></th></tr></thead><tbody><tr><td>Warning</td><td>The Raspberry Pi 5 is not certified for Gen 3.0 speeds. PCIe Gen 3.0 connections may be unstable.</td></tr></tbody></table>

To enable PCIe Gen 3 speeds, follow the instructions at [enable PCIe Gen 3.0](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#pcie-gen-3-0).
