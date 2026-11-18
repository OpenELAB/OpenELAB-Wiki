# Seeed Studio SenseCAP ONE S700-A and S500 V2 Engineering Guide

[Seeed-101991050](https://openelab.io/products/seeed-studio-sensecap-s700) · [Seeed-101991021](https://openelab.io/products/seeed-studio-sensecap-s500-v2)

### Product and scope

The wired SenseCAP ONE weather-sensor family supports environmental monitoring and fieldbus integration. This page distinguishes **S700-A 101991050** from **S500 V2 101991021**; it does not cover the LoRaWAN S2120.

### Hardware and technical documents

| Item             | Reference                                                                          |
| ---------------- | ---------------------------------------------------------------------------------- |
| S500 V2 channels | Temperature, humidity, pressure, wind speed and direction                          |
| S700-A channels  | Adds light intensity and radar rainfall intensity to the five weather measurements |
| Data             | RS485 Modbus RTU / SDI-12; select the model's supported configuration              |
| S700-A supply    | 12–24V; separate 24V heating input where used                                      |
| Protection       | S700-A: IP66                                                                       |
| Connector        | M12 eight-pin; pin assignment and cable colors must follow the current diagram     |

The manufacturer's current setup page identifies V2 by SKU and base design. V2 removes the older RS232/RS422 interfaces. Use the exact model's current catalogue for measurement ranges, accuracy, mounting dimensions and orientation; the older S700 does not establish radar-rain behavior.

### Getting started

1. Check the sensor label, ordered cable and model-specific power requirements. Leave the heater disconnected for the first data test.
2. Connect USB-C to a computer for configuration and use the manufacturer configuration tool.
3. Record interface, baud rate, address and firmware. Wire only the documented power/data conductors of the M12 cable.
4. With an appropriate RS485 interface, issue the official manual's read command for a known measurement.
5. Compare a plausible ambient temperature/humidity reading and save the raw response plus decoded units before outdoor installation.

**Expected checkpoint:** stable model identification and repeatable measurement reads. Complete mounting/orientation checks before relying on wind direction or rain readings.

### Development software and recovery

Use the official SenseCAP ONE configuration-tool release and the model's **Modbus register map / SDI-12 commands**. Record tool and firmware versions. Firmware updates must use Seeed's V1/V2 mapping and recovery procedure; preserve configuration first.

### FAQs

**Why does an older wiring diagram disagree?** V1 and V2 have different interfaces. Select by the printed ordering code.

**Can data and heater use the same leads?** Follow the separate heating-power circuit; never infer it from wire color alone.

**No Modbus response?** Check A/B polarity, reference ground, address, serial settings, termination and the model's register map.

### Sources and validation

* [Current installation, V2 mapping and wiring](https://wiki.seeedstudio.com/Getting_Started_with_SenseCAP_ONE_Compact_Weather_Sensor/)
* [S700-A specifications](https://sensecap.org/product/sensecap-s700-a-7-in-1-compact-weather-station-radar-rain/)
* [Firmware/tool resources](https://wiki.seeedstudio.com/firmware_update/)
* [Current weather catalogue](https://files.seeedstudio.com/products/SenseCAP/SenseCAP_ONE/SenseCAP_Weather_Sensor_Catalogue.pdf)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
