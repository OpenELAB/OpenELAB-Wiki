---
description: >-
  Set up IR Mate learning/replay and exact C3 pins; inspect raw IR with original
  receive-only ESPHome and choose a supported climate protocol.
---

# Seeed Studio XIAO Smart IR Mate Development Guide

{% hint style="info" %}
[**View Seeed Studio XIAO Smart IR Mate on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-smart-ir-mate)

**Model:** XIAO Smart IR Mate · **SKU:** `Seeed-109990586` · **Controller:** XIAO ESP32-C3 · **Power:** USB-C5 V. This is an assembled IR appliance bridge, not a bare XIAO board.
{% endhint %}

## Product overview <a href="#product-and-hardware" id="product-and-hardware"></a>

IR Mate receives a remote-control waveform, stores it in a selected factory-firmware slot and transmits it on request. It also provides touch input, vibration feedback and a status light through ESPHome/Home Assistant. For a supported air-conditioner protocol, custom climate firmware can generate a complete state command instead of replaying one stored button waveform. [Manufacturer guide](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/).

## Applications

Retrofit an IR-controlled TV, fan or similar room appliance, or use an existing IR remote as a Home Assistant scene input. Keep the original remote for comparison and recovery. An IR transmission has no guaranteed appliance acknowledgement: an optimistic dashboard state can differ from the physical appliance after a missed command or manual operation.

Place the unit where its receiver/emitter paths are clear. The three-emitter arrangement provides broad coverage, but furniture, sunlight, range and receiver direction still affect results. Establish one reliable command at the intended position before adding automation or assuming room-wide coverage.

## Specifications

| Item                | Exact IR Mate scope                                                                 |
| ------------------- | ----------------------------------------------------------------------------------- |
| MCU                 | XIAO ESP32-C3                                                                       |
| Power               | 5 V through USB-C                                                                   |
| Radio               | 2.4 GHz Wi-Fi; BLE hardware available for custom development                        |
| IR hardware         | 3 emitters,1 receiver                                                               |
| Factory storage     | 10 learned-command slots                                                            |
| Local interaction   | Touch input, vibration motor, addressable status LED, reset/function button         |
| Mechanical size     | Store specification:65 mm diameter ×19 mm height                                    |
| Factory application | ESPHome-based learning/replay and Home Assistant discovery                          |
| Custom application  | Exact ESP32-C3 target and IR pin map; supported climate protocols depend on ESPHome |

[Exact product listing](https://openelab.io/products/seeed-studio-xiao-smart-ir-mate), [manufacturer hardware/features](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/), [factory project](https://github.com/Seeed-Studio/xiao-esphome-projects/tree/main/projects/xiao_smart_ir_mate). Ten slots is a factory application feature, not a universal hardware/protocol learning limit.

## Hardware and connections

### Actual GPIO mapping

| Function              | XIAO label / actual ESP32-C3 GPIO | Constraint                                                                                |
| --------------------- | --------------------------------- | ----------------------------------------------------------------------------------------- |
| IR transmitter        | D1 /GPIO3                         | Drives the board's transmitter circuit, not a directly attached LED                       |
| IR receiver           | D2 /GPIO4                         | Factory input is inverted                                                                 |
| Touch module          | D3 /GPIO5                         | External touch sensor output, not the C3's nonexistent native capacitive-touch peripheral |
| Vibration             | D4 /GPIO6                         | Use board motor driver; do not attach a motor directly to GPIO                            |
| Status light          | D5 /GPIO7                         | WS2812/GRB one-pixel addressable device in factory YAML, not a plain on/off LED           |
| Function/reset button | **D9 /GPIO9**                     | Active-low input and boot strap; distinguish from the MCU reset pin                       |

The manufacturer overview's reset-button “D0” wording conflicts with its actual [factory YAML](https://github.com/Seeed-Studio/xiao-esphome-projects/blob/main/projects/xiao_smart_ir_mate/xiao_smart_ir_mate.yaml), which uses **GPIO9 / D9**. Use the source-backed map above for firmware. The [hardware ZIP](https://files.seeedstudio.com/wiki/XIAO_IR_MATE/XIAO_IR_REMOTE_hardware.zip) contains the V30 KiCad schematic/PCB project for revision inspection. Do not transfer a bare C3 pin label to a different module without checking the board.

Use USB-C data for flashing and a stable5 V USB source for operation. GPIO remains a3.3 V domain; no appliance mains wiring is involved in this interface. Do not drive the internal transmitter/motor from external pins or infer an exposed expansion pinout from the enclosure.

## Software and development resources <a href="#development-and-recovery" id="development-and-recovery"></a>

The [factory project YAML](https://github.com/Seeed-Studio/xiao-esphome-projects/blob/main/projects/xiao_smart_ir_mate/xiao_smart_ir_mate.yaml) reviewed on24 November2026 declares project version**2.0**, board **`seeed_xiao_esp32c3`**, Arduino framework and the custom **`Flash_comp`** storage component from Seeed's repository. Preserve that component, storage behavior and pin map if reproducing the ten-slot application. Do not copy its demonstration/shared OTA password into your own deployment; create your own API/OTA credentials and keep them in ESPHome secrets.

| Path                        | Appropriate first use                                                          |
| --------------------------- | ------------------------------------------------------------------------------ |
| Factory firmware            | Provision, discover, learn one slot, verify appliance response                 |
| Custom receive-only ESPHome | Inspect real protocol/raw frames without transmitting                          |
| Climate firmware            | Select the exact supported appliance protocol/submodel and test state commands |
| IR-triggered scene          | Match a decoded command and verify a benign Home Assistant action              |

[ESPHome remote receiver](https://esphome.io/components/remote_receiver/), [transmitter](https://esphome.io/components/remote_transmitter/), [IR climate components](https://esphome.io/components/climate/climate_ir/). Pin the ESPHome release and factory/external-component commit together; a moving `main` branch and an old YAML example are not a tested compatibility matrix.

## Getting started <a href="#getting-started-with-factory-firmware" id="getting-started-with-factory-firmware"></a>

### Factory network and Home Assistant connection

1. Power the assembled device through USB-C. In the documented factory state, the white indicator blinks about1 Hz while waiting for a network.
2. Join the device's observed AP, named **XIAO IR Mate** or **Seeed\_ir** in the guide, using the documented initial password **12345678**. Open `http://192.168.4.1` if a captive portal does not appear.
3. Select your authorized **2.4 GHz** SSID and enter its password. After joining, the AP disappears and the indicator becomes steady.
4. On the same reachable LAN, open Home Assistant **Settings → Devices & Services** and accept ESPHome discovery. If not discovered, add the **ESPHome** integration using the actual device address/hostname.

**Expected result:** Home Assistant exposes the intended physical IR Mate with slot selection, Learn, Send and learned-status entities. Names vary by firmware: the wiki uses `signal_1` examples, while current YAML options are **Signal0–Signal9**. Inspect the actual entities instead of assuming a slot number from a screenshot. [Factory setup](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/), [current project source](https://github.com/Seeed-Studio/xiao-esphome-projects/tree/main/projects/xiao_smart_ir_mate).

### Learn one non-destructive command and verify persistence

1. Choose an unused slot and note its exact name. Select **Learn**; factory firmware activates vibration while awaiting input.
2. Aim the original remote at the receiver and press a suitable single command briefly. Verify vibration stops and **Is Learned Signal** becomes active for the selected slot.
3. Ensure the same slot is selected, aim the unit appropriately and press **Send** once. Observe the actual appliance, not only the Home Assistant log.
4. Change slots and return, then reboot normally and verify that the intended command remains stored. Keep a written slot-to-action map before using those slots in automation.

**Expected result:** the chosen appliance performs the expected single action after replay. An unlearned slot should not send a stored frame. Avoid using a power-toggle command as proof of absolute appliance state; repeat playback toggles it again. [Learning/send behavior](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/).

### What the factory implementation stores

Current source stores raw timing vectors in NVS through `Flash_comp`, with a selected-slot index and an `is_learning_mode` gate. Its receiver uses inverted GPIO4, **65500 µs idle segmentation** and **500000 clock resolution**. Its playback uses a **38 kHz carrier**. Those are implementation choices, not proof that every handset's carrier or long state frame is captured correctly. A raw demodulating receiver's duration capture does not measure carrier frequency. [Read factory implementation](https://github.com/Seeed-Studio/xiao-esphome-projects/blob/main/projects/xiao_smart_ir_mate/xiao_smart_ir_mate.yaml).

If short TV commands work but an AC state does not, inspect frame segmentation, repeats, payload length and appliance protocol before simply increasing transmit power. Factory learning can capture an incomplete long frame, and a carrier other than38 kHz may need a different transmit configuration.

### Original receive-only ESPHome diagnostic

This complete original configuration listens and reports button/touch state. It contains **no transmitter**, factory-reset automation or learned-slot writes. Flashing it replaces the factory application, so save the required learning/configuration records first. Put your own `wifi_ssid` and `wifi_password` in `secrets.yaml`, select the actual USB device and use ESPHome's supported build/install flow.

```yaml
esphome:
  name: openelab-ir-listener
esp32:
  board: seeed_xiao_esp32c3
  framework:
    type: arduino
logger:
  level: DEBUG
api:
ota:
  - platform: esphome
wifi:
  ssid: !secret wifi_ssid
  password: !secret wifi_password
remote_receiver:
  pin:
    number: GPIO4
    inverted: true
  dump: all
  idle: 25ms
binary_sensor:
  - platform: gpio
    name: "IR Mate touch diagnostic"
    pin:
      number: GPIO5
      mode: INPUT_PULLDOWN
  - platform: gpio
    name: "IR Mate function button diagnostic"
    pin:
      number: GPIO9
      mode: INPUT_PULLUP
      inverted: true
      ignore_strapping_warning: true
```

**Expected result:** pressing the original remote produces decoded/raw records in ESPHome logs; touch and function-button entities change independently. The25 ms idle is an **original diagnostic starting point**, not a claim to reproduce the factory segmentation. If a protocol splits incorrectly, compare the captured bursts and documented receiver options. Capture several presses, including held-key repeats, and compare before defining a transmit action. [Receiver configuration/decoders](https://esphome.io/components/remote_receiver/).

### Stateful air-conditioner control

Use a supported **climate protocol**, not merely the brand name. For a confirmed compatible Gree `yan` model, the following is an original **addition** to the listener baseline; remove receive dumping if it is too verbose. Other Gree submodels or brands require their own documented selection.

```yaml
remote_transmitter:
  id: ir_output
  pin: GPIO3
  carrier_duty_percent: 50%
climate:
  - platform: gree
    name: "Bench Gree controller"
    model: yan
    supports_cool: true
    supports_heat: false
```

Build and install with your selected supported ESPHome version. First verify an explicit OFF command, then a known benign mode/temperature on the actual appliance and compare its display/beep. Do not enable heating for an appliance that lacks it. The climate entity's target state remains optimistic unless a real feedback path/protocol supports synchronization; the current manufacturer Gree example does not automatically consume the handheld remote to synchronize its state. A separate temperature sensor needs a real entity and documented protocol support. [Supported IR climate options](https://esphome.io/components/climate/climate_ir/#gree), [manufacturer AC route](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/).

### Reuse a remote as a scene input or touch as a button

For a remote scene, retain receive-only diagnostics until a unique decoded command is repeatable, then bind the corresponding ESPHome `on_…` trigger to a test Home Assistant action. Distinguish the initial frame from held-key repeats to avoid repeatedly toggling a light. For touch, debounce/group the external GPIO5 sensor and keep the vibration pulse short. The factory source uses roughly100 ms confirmation vibration and500 ms for reset; touch processing/transmit timing is firmware-specific, so do not treat those durations as an electrical device rating. [Current factory scripts](https://github.com/Seeed-Studio/xiao-esphome-projects/blob/main/projects/xiao_smart_ir_mate/xiao_smart_ir_mate.yaml).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                         | Ordered checks / recovery                                                                                                                              |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| AP not found                                    | Confirm power and installed application; factory AP can disappear after successful provisioning. Custom firmware may have no fallback AP.              |
| Home Assistant cannot discover it               | Find its actual IP, verify ESPHome API and same reachable LAN, then add manually; discovery and network connectivity are separate.                     |
| Learned status on, appliance unchanged          | Confirm selected slot, receiver/emitter placement, carrier/protocol/repeats and actual appliance response. A log saying “Send” is not acknowledgement. |
| Long AC frame fails                             | Inspect raw segmentation and state protocol; use supported climate generation if appropriate rather than recording every temperature separately.       |
| Custom light does not respond to `digitalWrite` | Status LED is WS2812 onGPIO7 in current firmware, requiring an addressable-light driver.                                                               |
| Upload stalls                                   | Verify XIAO ESP32-C3 target and data cable; GPIO9 is a strap. Use the C3 BOOT/reset recovery procedure with external forcing removed.                  |
| Unexpected replay on touch                      | Factory touch schedules its selected-slot Send; custom listener above intentionally does not. Inspect actual firmware automation.                      |
| Need to restore factory features                | Use the official XIAO Gadget flasher, select IR Mate and preserve needed data before replacement.                                                      |

### Restart versus erase

The factory function button onGPIO9 reboots after a short press/release. Holding longer than**5 s** invokes the documented factory-reset path: **Wi-Fi credentials and all ten learned IR slots are cleared** in the current source before restart. A short reboot does not intentionally erase them. Treat the firmware action separately from the physical MCU reset and BOOT strap behavior. [Reset source](https://github.com/Seeed-Studio/xiao-esphome-projects/blob/main/projects/xiao_smart_ir_mate/xiao_smart_ir_mate.yaml), [official flasher](https://gadgets.seeed.cc/).

## Downloads and technical documents <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

| Resource                                                                                                                            | Exact scope                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| [Hardware ZIP](https://files.seeedstudio.com/wiki/XIAO_IR_MATE/XIAO_IR_REMOTE_hardware.zip)                                         | Downloaded V30 KiCad schematic/PCB/project; use for exact revision inspection |
| [Factory source directory](https://github.com/Seeed-Studio/xiao-esphome-projects/tree/main/projects/xiao_smart_ir_mate)             | README and version2.0 YAML, actual GPIO and persistence behavior              |
| [Factory YAML](https://github.com/Seeed-Studio/xiao-esphome-projects/blob/main/projects/xiao_smart_ir_mate/xiao_smart_ir_mate.yaml) | Inspect `Flash_comp` dependency and replace sample credentials                |
| [XIAO Gadget firmware flasher](https://gadgets.seeed.cc/)                                                                           | Select IR Mate for restoration/update                                         |
| [ESPHome IR receiver](https://esphome.io/components/remote_receiver/)                                                               | Capture/decoder/filter/timing options                                         |
| [ESPHome IR transmitter](https://esphome.io/components/remote_transmitter/)                                                         | Raw/protocol actions, carrier and repeats                                     |
| [ESPHome IR climate](https://esphome.io/components/climate/climate_ir/)                                                             | Protocol/model-specific state generation                                      |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November2026** against the [exact manufacturer guide](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/), current factory README/YAML and ESPHome references. Hardware ZIP access and contents were verified; the pin/protocol decisions above are traced to actual firmware rather than the wiki's inconsistent reset label. No whole manufacturer example was reproduced.

**Validation:** source reviewed. ESPHome validation/compilation, flashing, IR capture/transmission, Home Assistant integration and hardware tests were **not run**. Expected results are checkpoints for reproduction. Reconfirm received hardware/firmware revision before modifying the unit.
