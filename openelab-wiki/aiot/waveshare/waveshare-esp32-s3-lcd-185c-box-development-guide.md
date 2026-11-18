# Waveshare ESP32-S3 Touch LCD 1.85C BOX Engineering Guide

[Waveshare-30684](https://openelab.io/products/waveshare-esp32-s3-1-85-round-lcd)

### Product and scope

**30684 ESP32-S3-Touch-LCD-1.85C-BOX** combines a touch-display MCU board with a speaker enclosure and battery configuration. The manufacturer replaced V1 with **V2 from 30 January 2026**; identify the received revision before flashing.

### Hardware and technical documents

| Item            | Reference                                                |
| --------------- | -------------------------------------------------------- |
| Processor       | ESP32-S3, 2.4GHz Wi-Fi/BLE                               |
| UI              | 1.85-inch capacitive-touch display                       |
| BOX distinction | Speaker enclosure and 3.7V lithium-battery configuration |
| Revision        | Separate V1/V2 compatibility requirements                |
| Applications    | Voice-terminal, touch UI and portable display prototypes |

The official **version compatibility notes, schematic and pin map** govern display/audio initialization and power. Use the BOX enclosure/dimensional resources; bare-board photographs do not establish battery or speaker inclusion.

### Getting started

1. Identify V1/V2 and verify the battery/speaker connections against that revision.
2. Record the factory firmware and test it before erasing.
3. Install the documented Arduino/ESP-IDF environment and select the matching revision's basic UI example.
4. Upload, check display/touch response and then test audio at low volume.
5. Introduce network/voice services only after local input/output works.

**Expected checkpoint:** a responsive local UI and independently working audio path without resets under load.

### Development software and recovery

Keep the exact hardware revision, example commit and toolchain. Use the manufacturer-supported factory binary and flash layout for recovery. A generic ESP32-S3 image can omit power and audio initialization even if flashing succeeds.

### FAQs

**A V1 example compiles but fails?** Check V2 compatibility and changed peripheral definitions.

**Voice app cannot answer?** Separate microphone/speaker tests from network, credentials and backend requirements.

**Powered but USB absent?** Check data cable and documented download mode.

### Sources and validation

* [Current model and revision compatibility](https://docs.waveshare.com/ESP32-S3-Touch-LCD-1.85C)
* [Legacy model resource index](https://www.waveshare.com/wiki/ESP32-S3-Touch-LCD-1.85C)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
