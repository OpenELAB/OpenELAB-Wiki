# Seeed Studio XIAO ESP32-C5 Development Guide

[Product at OpenELAB](https://openelab.io/products/seeed-studio-xiao-esp32-c5)

### Product, applications and hardware

**100010048** is the XIAO **ESP32-C5** for compact dual-band Wi-Fi devices and sensor prototypes. C3, C5, C6 and S3 boards have different processors, pin maps and firmware targets.

| Item          | ESP32-C5 board                 |
| ------------- | ------------------------------ |
| Processor     | 32-bit RISC-V, up to 240MHz    |
| Wireless      | 2.4/5GHz Wi-Fi 6; Bluetooth LE |
| Memory        | 8MB flash and 8MB PSRAM        |
| Size          | 21 × 17.8mm                    |
| Expansion     | I2C, SPI, UART and GPIO/ADC    |
| User controls | BOOT, reset and user LED       |

Consult the manufacturer's schematic and complete pin table before wiring. For example, **D4/D5 map to GPIO23/GPIO24**, and D10 is GPIO10. Board labels are not chip pin numbers. Keep GPIO within the board's documented logic limits.

### Getting started: offline LED test

1. Connect a USB-C data cable. Leave external hardware disconnected.
2. Install Arduino IDE and **Espressif ESP32 board package 3.3.5 or later**, as specified in the reviewed manufacturer guide.
3. Select **XIAO\_ESP32C5** and its enumerated port.
4. Upload this minimal sketch:

```cpp
void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
}
void loop() {
  digitalWrite(LED_BUILTIN, LOW);
  delay(1000);
  digitalWrite(LED_BUILTIN, HIGH);
  delay(1000);
}
```

**Expected result:** the user LED alternates once per second. This checks build, upload and execution without needing Wi-Fi credentials.

### Development and recovery

Use the official C5 board definition for PlatformIO, or a supported ESP-IDF/MicroPython build for this exact model. Record the board package and toolchain version; a generic ESP32 target is insufficient.

If the application prevents uploads, use the guide's BOOT/reset download-mode sequence, reselect the new port and retry the minimal sketch. Back up flash/configuration before erasing.

### FAQs

**No USB port?** Check cable, port, driver and boot mode.

**Can a 5GHz network be used?** C5 supports dual-band Wi-Fi; confirm the firmware's supported mode and router settings.

**Old XIAO code behaves differently?** Recheck pin mapping, target, PSRAM settings and dependencies before connecting external loads.

### Sources and validation

* [Manufacturer getting started, schematic and pinout links](https://wiki.seeedstudio.com/xiao_esp32c5_getting_started/)
* [Official board definition](https://github.com/Seeed-Studio/platform-seeedboards/blob/main/boards/seeed-xiao-esp32-c5.json)
* [MicroPython model build](https://micropython.org/download/SEEED_XIAO_ESP32C5/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
