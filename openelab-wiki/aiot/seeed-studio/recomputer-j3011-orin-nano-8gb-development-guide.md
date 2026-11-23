---
description: >-
  Develop with original reComputer J3011 Orin Nano 8GB: J401 power and headers,
  JetPack image matching, camera capture, memory-aware software setup and
  recovery.
---

# Seeed Studio reComputer J3011 Orin Nano 8GB Engineering Guide

{% hint style="info" %}
[**View Seeed Studio reComputer J3011 on OpenELAB**](https://openelab.io/products/seeed-studio-recomputer-j3011-edge)

**Model:** original reComputer J3011 · **SKU:** `Seeed-110110147` · **Configuration:** Jetson Orin Nano 8GB, original J401 carrier,128GB NVMe
{% endhint %}

reComputer J3011 is an original J30/40-series edge computer. This guide covers its own power, pinout, software image and recovery path, then demonstrates Linux/peripheral communication without assuming that a similarly named Super or Robotics board is interchangeable.

[Seeed Studio wiki directory](./). Manufacturer illustrations retain their original attribution.

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The original J3011 is a six-core Orin Nano 8GB system on the J401 carrier. It has no NVDLA engine and no dedicated hardware video encoder: its advertised 40 TOPS does not imply the encoding resources of an Orin NX. The newer Super J3011 and similarly named Mini/Industrial systems have different carrier and thermal scopes. [Original model table](https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/), [release-specific flash and thermal notes](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/).

Inspect the module, carrier revision, delivered supply and fitted Wi-Fi module when unpacking. The documented 128GB NVMe is the OS drive; the module's RAM size is not storage capacity. Save the installed L4T release before upgrading.

## Applications

The J3011 is useful for compact computer vision, supported CSI/USB acquisition and memory-conscious local inference. Allocate the8GB RAM across desktop, model, frame buffers and middleware; a model that fits a16GB NX may fail here. Prefer hardware-decoded input and avoid sizing multi-stream encoding from an NX example.

Treat decode/encode maxima and TOPS as selection figures rather than promised frame rates. Start with one sensor and one small pipeline, record temperature and power mode, then add middleware or additional streams.

## Specifications

| Item                     | Original J3011                                                                           |
| ------------------------ | ---------------------------------------------------------------------------------------- |
| Module                   | Orin Nano 8GB; six Cortex-A78AE cores up to1.5GHz;1024 Ampere CUDA cores,32 Tensor Cores |
| RAM                      | 8GB 128-bit LPDDR5,68GB/s module bandwidth                                               |
| AI / accelerator         | Up to40 TOPS in the original configuration; no NVDLA / PVA engine                        |
| Video                    | Hardware decode;1080p30 encode uses1–2 CPU cores in the manufacturer comparison          |
| Storage                  | 128GB M.2 Key M NVMe2280 system SSD                                                      |
| Network                  | One RJ45,10/100/1000Mb/s;Key E wireless expansion                                        |
| USB                      | Four USB3.2 Type-A,10Gb/s via hub;one USB2.0 Type-C device/recovery                      |
| Display / camera         | One HDMI2.1;two15-pin two-lane CSI connectors                                            |
| Headers                  | J10:40-pin GPIO/I2C/SPI/UART/I2S;J15:12-pin service;J16:logic CAN                        |
| Supply                   | 9–19V DC barrel input;finished-system12V/5A adapter configuration                        |
| Mechanical / environment | 130×120×58.5mm;−10 to+60°C stated system range;retain active cooling                     |

Sources: [original J30/40 specification table](https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/), [original carrier connectors](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/), [exact OpenELAB listing](https://openelab.io/products/seeed-studio-recomputer-j3011-edge). The download named J301x datasheet currently serves a PDF whose cover and module table are J4011/J4012; use it for explicitly shared carrier connectors only, not Nano compute specifications.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Power and basic connections

The original J401 carrier accepts **9–19V DC** at its 5.5/2.5mm barrel input. Use the supplied/approved **12V, 5A** adapter for these original systems, and check the package before relying on an included supply. The carrier-only datasheet describes a package without an adapter; the finished-system listing identifies the ordered bundle. USB-C J1 is a **device/recovery data port**, not the main power input. Attach HDMI, keyboard and one Ethernet connection while unpowered, then apply barrel power. [Original J401 hardware guide](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/), [J401 connector datasheet](https://files.seeedstudio.com/products/NVIDIA/reComputer-J401x-datasheet.pdf).

Keep the heatsink/fan in place. The carrier's approximate overvoltage shutoff threshold of 22.5V is a protection response, not a usable input rating. Do not copy the Super carrier's 19V NX adapter policy or a Robotics XT30 wiring scheme onto this box.

### J10 physical pins and J15 service header

These are **physical header pins**, not Linux GPIO line offsets. Locate the pin-1 mark on the official J401 drawing; a Raspberry Pi-like connector shape does not make every alternate function identical.

| Interface            | J10 physical positions                                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Supply / return      | 3.3V on 1/17; 5V on 2/4; GND on 6/9/14/20/25/30/34/39                                                                     |
| I2C1                 | SDA3, SCL5                                                                                                                |
| I2C0                 | SDA27, SCL28; check attached system devices before probing                                                                |
| UART1                | TX8, RX10; RTS11, CTS36 when pinmux enables them                                                                          |
| SPI0                 | MOSI19, MISO21, SCK23, CS0 24, CS1 26                                                                                     |
| SPI1                 | SCK13, CS1 16, CS0 18, MISO22, MOSI37                                                                                     |
| I2S0                 | Clock12, frame35, data-in38, data-out40                                                                                   |
| Selected GPIO labels | Physical7 GPIO09, 15 GPIO12, 29 GPIO01, 31 GPIO11, 32 GPIO07, 33 GPIO13; verify actual pinmux and availability before use |

Source: [J401 datasheet, J10 table](https://files.seeedstudio.com/products/NVIDIA/reComputer-J401x-datasheet.pdf). The web interface table incorrectly leaves physical17 looking like a GPIO row; the connector datasheet identifies it as the **3.3V rail**, not a general output.

For UART, use an adapter with compatible logic levels; cross TX8 to adapter RX and RX10 to adapter TX, and connect GND6. Do not connect RS232 voltage levels directly to a TTL UART. The separate **J15 12-pin service header** is numbered 1 PWR BTN, 2 GND, 3 FC REC, 4 GND, 5 SYS RET, 6 GND, 7 AUTO ON, 8 DIS, 9 UART TXD, 10 UART RXD, 11 LED+, 12 LED−. This is not the Super's 12-pin numbering. Use only FC REC3/GND4 for the original carrier recovery procedure. [J401 flashing guide](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/#enter-force-recovery-mode).

### CAN is logic level, with no onboard differential transceiver

J16 is **1 TX, 2 RX, 3 GND, 4 3.3V**. Connect TX to a suitable transceiver's TXD input and RX to its RXD output; connect its logic ground and compatible 3.3V supply. Only the transceiver's CANH/CANL go onto the differential bus. A 5V transceiver's logic output must not be assumed compatible. Use termination at the two bus ends, not at every connector. [J401 datasheet p.20](https://files.seeedstudio.com/products/NVIDIA/reComputer-J401x-datasheet.pdf), [CAN usage](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/#can).

### Storage, cameras and service parts

J18 accepts a **2280 NVMe** drive, not SATA merely because an M.2 card fits. J20 Key E is the wireless-module position; connect matching antennas. The two 15-pin CSI ports need correctly oriented ribbons and a supported sensor/BSP combination. Connect cameras and expansion modules only while unpowered. The J13 fan is **5V PWM**, with ground, 5V, tachometer and PWM; do not replace it with an arbitrary 12V fan.

The RTC supports one **3V non-rechargeable CR1220** holder or the documented two-pin backup route. Charging is disabled in the reference circuit; do not populate two backup sources at once. The PoE header is a provision for an appropriate optional power module, not proof the finished computer accepts or supplies PoE. [J401 connector datasheet](https://files.seeedstudio.com/products/NVIDIA/reComputer-J401x-datasheet.pdf).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The original-system page describes JetPack5.1.3; Seeed's current flash page also contains5.1.1/5.1.2,6.0/6.1/6.2 and7.2 tabs. Use the row matching **Orin Nano 8GB on original J401**, not a generic Orin download. Jetson NX requires5.1 or later and Nano requires5.1.1 or later. Seeed specifically recommends5.1.3 for affected Hynix-DRAM modules. [Image and DRAM notes](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/).

The newer image tabs do not turn the original Nano box into the separately sold Super system. Use only profiles supplied for the exact original carrier/image, retain its cooling, and compare the actual nvpmodel output before changing modes.

Use Jetson/aarch64 CUDA/TensorRT/PyTorch builds compatible with the installed L4T version. Desktop x86 wheels, arbitrary ROS distributions and an unrelated camera overlay can break an otherwise bootable image. Keep the BSP/kernel, container tag, model artifact and sensor driver together. The original procedures below use Linux tools and supported interfaces; they have not been run on a target system.

## Getting started

### 1. Boot before installing project software

1. Prepare the complete J3011,approved12V/5A supply,HDMI display,keyboard and Ethernet. Leave external GPIO and CAN disconnected.
2. Connect peripherals, apply power and finish the Ubuntu user/locale setup. Use wired networking first.
3. Run on the **Jetson**:

```bash
cat /etc/nv_tegra_release
uname -m
free -h
lsblk -o NAME,SIZE,TYPE,MOUNTPOINTS
findmnt /
ip -br address
sudo nvpmodel -q
tegrastats --interval 1000
```

Stop statistics with Ctrl+C. **Expected result:** aarch64 Linux,L4T release,about8GB nominal module memory (usable RAM is lower),mounted system storage and a stable power/temperature record. A reported power mode is a configuration, not measured input watts. [NVIDIA tegrastats](https://docs.nvidia.com/jetson/archives/r36.4.3/DeveloperGuide/AT/JetsonLinuxDevelopmentTools/TegrastatsUtility.html).

### 2. Run an original bounded serial echo check

This test uses UART1 through a **compatible logic-level USB-to-UART adapter**. Confirm pinmux and the actual `/dev/ttyTHS1` mapping from the installed image before running. Power off to connect J10TX8→adapterRX,RX10→adapterTX and GND6→GND. Set the host terminal to115200,8N1,no flow control. Install `python3-serial` on the Jetson. Save as `uart_checkpoint.py`:

```python
import sys, time
import serial

port = sys.argv[1]
with serial.Serial(port, 115200, timeout=0.25) as link:
    link.reset_input_buffer()
    link.write(b"J3011_UART_READY\n")
    until = time.monotonic() + 15
    while time.monotonic() < until:
        data = link.read(128)
        if data:
            print("rx_hex=" + data.hex())
            link.write(b"echo:" + data)
```

```bash
sudo apt install python3-serial
python3 uart_checkpoint.py /dev/ttyTHS1
```

From the host, send `bench-J3011`. **Expected result:** the host first receives `J3011_UART_READY`;the Jetson prints received bytes in hexadecimal and returns them with `echo:` for15seconds. Use a real adapter with compatible levels; do not plug RS232 or the power rail into these pins. If permission is denied, inspect the port's group and add the account appropriately, then log in again. No response requires pinmux,device mapping,TX/RX and serial ownership checks before an OS reflash. [J401 UART procedure](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/#uart).

### 3. Acquire one camera stream

For a supported CSI sensor, shut down, disconnect power, fit the correctly oriented15-pin ribbon and apply its BSP/device-tree configuration. For a USB camera,use a Type-A host socket. Install `v4l-utils`,inspect `v4l2-ctl --list-devices`,then use the sensor's documented capture route. On a compatible JetPack image with Argus support:

```bash
command -v nvgstcapture-1.0
nvgstcapture-1.0 --sensor-id=0
```

Expected result is changing live imagery for the selected sensor. UVC cameras use V4L2 rather than an assumed Argus sensor ID;inspect `v4l2-ctl -d /dev/video0 --list-formats-ext` before selecting a format. Do not force a1920×1080 mode that the actual sensor does not list. [J30/40 camera scope](https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/),[NVIDIA accelerated multimedia reference](https://docs.nvidia.com/jetson/archives/r36.4.3/DeveloperGuide/SD/Multimedia/AcceleratedGstreamer.html).

### Peripheral tests after the first result

| Path                | Concrete test and interpretation                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| USB                 | Compare `lsusb -t` before/after a known device. The four Type-A connectors share an upstream connection; the datasheet gives **2.1A total per upper/lower pair**, not 2.1A independently on every socket. Use a powered hub for a verified high-load peripheral if needed.                                                                                                                                                  |
| NVMe                | Run `lsblk -o NAME,SIZE,TYPE,MOUNTPOINTS` and `findmnt /`; confirm the expected disk before a file test. Do not run a raw-device `dd` write on `/dev/sda` or the system NVMe.                                                                                                                                                                                                                                               |
| Ethernet / wireless | Inspect actual interface names with `ip -br link`; use `ethtool INTERFACE`. For a bench peer running `iperf3 -s`, use `iperf3 -c PEER_IP -t 10`. Inspect `nmcli device status` and pair Bluetooth through `bluetoothctl`; identify the fitted wireless module before installing a driver.                                                                                                                                   |
| I2C                 | On a disconnected bench, attach a known compatible sensor to SDA3/SCL5/GND6 and its documented supply. Use `i2cdetect -l` first; bus7 is the vendor's example, not a universal assignment. Probe only the known peripheral bus. A sensor needing a 5V supply must still have compatible I2C pull-ups.                                                                                                                       |
| UART                | Use compatible TX/RX/GND wiring above and 115200, 8N1, no flow control. Open the observed UART node and host adapter in serial terminals; send distinct short strings in both directions before a device protocol.                                                                                                                                                                                                          |
| GPIO                | Use `sudo /opt/nvidia/jetson-io/jetson-io.py` for the intended alternate function, save/reboot, then inspect `gpioinfo`. Match SoC line names to the actual chip/offset. With libgpiod1, use `gpioset --mode=signal CHIP LINE=VALUE` to hold until interrupted; with libgpiod2 use `gpioset -c CHIP LINE=VALUE`. Release only after disconnecting the test load. These are syntax patterns, not electrical pin assignments. |
| Fan / RTC           | Keep `nvfancontrol` active and inspect actual hwmon names instead of copying `hwmon3`. For a correctly fitted RTC battery, read `sudo hwclock -r`, disconnect networking, power-cycle normally and compare; NTP can hide a failed retention test.                                                                                                                                                                           |

The [J401 interface guide](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/) supplies the peripheral context. Its CAN-FD comment mentions 5Mb/s while the command sets 2Mb/s; this guide uses an explicit 2Mb/s bench data phase below. Its single-`#` frame remains a Classic CAN frame even on an FD-enabled interface.

### CAN bench send and receive

After adding the external transceiver, connect a second compatible bench node with H↔H, L↔L, reference ground and 120Ω at each end. Leave actuators disconnected. On the Jetson:

```bash
sudo apt install can-utils
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 500000
sudo ip link set can0 up
ip -details -statistics link show can0
candump -n 1 can0
```

Send one known frame from the peer while the last command waits. **Expected result:** one received ID and payload, with no increasing bus-off/error counters. For the reverse direction, run `cansend can0 321#10203040` and observe the peer. To test FD, first bring the interface down and configure **both** nodes for `bitrate 500000 dbitrate 2000000 fd on`; send an actual FD frame such as `cansend can0 321##1102030405060708090`. Here `##1` selects an FD frame with bitrate switching; all transceivers must support the data rate. Stop the interfaces after the bench test. [Seeed CAN section](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/#can), [NVIDIA CAN driver reference](https://docs.nvidia.com/jetson/archives/r36.4.3/DeveloperGuide/HR/ControllerAreaNetworkCan.html).

### Recovery: select the original carrier image

Back up the system and application before flashing. Use a physical x86 Ubuntu host supported by the selected JetPack release, a USB-C **data** cable, main DC supply and the matching original J401 image from [Seeed's version tabs](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/). Do not select Super, Robotics or Industrial firmware.

1. With power removed, identify J15 from the carrier diagram and connect **FC REC3 to GND4**.
2. Connect the carrier's USB2.0 Type-C device port to the host, then apply main power. Check `lsusb` on the host for **0955:7523**. Remove the jumper after recovery is established, as in the vendor procedure.
3. Choose the **Orin Nano 8GB** row and exact JetPack version; compare the archive's `sha256sum` with that row. Keep the filename and hash with the project.
4. Extract using `sudo tar xpf YOUR_EXACT_ARCHIVE.tar.gz` and enter its extracted mass-flash directory. Run:

```bash
sudo ./tools/kernel_flash/l4t_initrd_flash.sh --flash-only \
  --massflash 1 --network usb0 --showlogs
```

5. Wait for a successful flash log, power off, ensure FC REC is no longer grounded, attach HDMI and boot normally. Complete account setup and repeat the baseline and first application check.

The vendor also documents older raw BSP workflows. Do not mix one release's board configuration, QSPI XML and another release's root filesystem. The JetPack5.1.2 tab requires its stated BCT patch; a supported prebuilt mass-flash archive avoids constructing that historical image manually. Source-listed SharePoint images may require a browser session; this review did not download or flash the multi-gigabyte archives.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                               | Ordered check                                                                                                                                               |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power but no desktop                  | Main supply/barrel→fan and PWR→HDMI input/cable→boot logs through documented debug route;do not assume a display fault is storage failure.                  |
| Application dies when loading a model | Inspect `free -h`,`tegrastats` and kernel OOM logs;reduce batch/frame buffers;check architecture and dependency versions before changing the power profile. |
| CAN sees no external frames           | External transceiver→logic voltage→H/L/reference→two end resistors→bitrate→error counters. The J16 pins are not CANH/CANL.                                  |
| UART permission/busy error            | Inspect device ownership and console services;close competing serial tools;verify the actual UART node and pinmux.                                          |
| I2C example gives no ACK              | Correct bus from `i2cdetect -l`→supply/pull-up levels→SDA/SCL/ground→known sensor address. Bus7 and0x19 are examples,not built-in devices.                  |
| New kernel loses Wi-Fi                | Match driver and headers to the exact installed image;Seeed's6.0-specific repair is not a generic command for every kernel.                                 |
| Flash host sees no APX                | Check J15REC3/GND4 before power-on,correct USB-C data port and cable;require the model-specific USB ID before flash.                                        |
| Can I use the Super NX power mode?    | This Nano is a different module and original carrier;only use modes provided for its exact image and thermal configuration.                                 |

## Downloads and technical documents <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

| Resource                                                                                                                                                               | Use and access note                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [Original J30/40 setup](https://wiki.seeedstudio.com/reComputer_J30_40_with_Jetson_getting_start/)                                                                     | Exact system comparison and two-CSI/single-Ethernet scope                                     |
| [J401 peripheral guide](https://wiki.seeedstudio.com/J401_carrierboard_Hardware_Interfaces_Usage/)                                                                     | Storage,wireless,RTC,fan,GPIO,UART,I2C and CAN                                                |
| [Release-specific flash images and hashes](https://wiki.seeedstudio.com/reComputer_J4012_Flash_Jetpack/)                                                               | Select original carrier and **Orin Nano 8GB** row;archives not downloaded during review       |
| [J401x connector datasheet](https://files.seeedstudio.com/products/NVIDIA/reComputer-J401x-datasheet.pdf)                                                              | Downloaded/read;J10/J15/J16 and power tables;cover describes NX carrier package               |
| [J301x-named PDF](https://files.seeedstudio.com/products/NVIDIA/reComputer-J301x-datasheet.pdf)                                                                        | Observed to return the same NX-labelled PDF;not authoritative for Nano compute specifications |
| [J401 schematic v1.0](https://files.seeedstudio.com/wiki/J401/reComputer_J401_SCH_V1.0.pdf)                                                                            | Downloaded/read electrical reference                                                          |
| [J4012 STEP](https://files.seeedstudio.com/wiki/reComputer-J4012/reComputer-J4012.stp)                                                                                 | Manufacturer-listed shared enclosure/mechanical reference;confirm physical carrier revision   |
| [Official Jetson examples](https://github.com/Seeed-Projects/jetson-examples) / [beginner projects](https://github.com/Seeed-Projects/reComputer-Jetson-for-Beginners) | Separate examples;review release/platform requirements before installing                      |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026** using the exact store/catalog identity,the live J30/40,J401 interface and flash pages,and downloaded carrier datasheet/schematic. The J16 CAN table was visually checked. The J301x-named download's NX cover mismatch is disclosed rather than treated as Nano module evidence.

**Source review only: compilation,package installation,firmware flashing and physical hardware tests were not run.** UART output and camera/CAN results above are expected checkpoints,not observed logs. Record carrier/module revision,L4T,image hash,supply,peripherals and actual outputs when reproducing. Manufacturer downloads retain their original notices;the short application procedure and bounded serial example here are original.

### Related retained references

* [Manufacturer model comparison](https://www.seeed.cc/product/recomputer-classic-jetson)
* [Official flashing-selector source](https://github.com/Seeed-Studio/wiki-documents/blob/docusaurus-version/sites/en/docs/Edge/NVIDIA_Jetson/Flash_Jetpack.mdx)
