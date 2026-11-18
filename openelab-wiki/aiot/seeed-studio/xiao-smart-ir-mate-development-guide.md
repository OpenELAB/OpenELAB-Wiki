# Seeed Studio XIAO Smart IR Mate Development Guide

[Product at OpenELAB](https://openelab.io/products/seeed-studio-xiao-smart-ir-mate)

### Product and hardware

**109990586** is an ESPHome-based infrared bridge built around the **XIAO ESP32-C3**. It adds Wi-Fi control to appliances that accept compatible infrared remote commands; it does not convert an RF-only remote into an IR device.

| Function                 | Hardware / XIAO label |
| ------------------------ | --------------------- |
| Power                    | USB-C, 5V             |
| IR transmit              | Three emitters, D1    |
| IR receive               | D2                    |
| Touch / vibration        | D3 / D4               |
| Status LED / reset input | D5 / D0               |

The hardware ZIP contains the design resources; use its electrical pin mapping when editing ESPHome YAML. XIAO board labels and chip GPIO numbers should not be interchanged by guesswork.

### Getting started with factory firmware

1. Power the unit using USB-C. An unconfigured unit indicates provisioning with a blinking white LED.
2. Join the **XIAO IR Mate** / **Seeed\_ir** hotspot identified by the official guide. The documented provisioning password is `12345678`.
3. Open the captive portal, or `http://192.168.4.1`, and enter a **2.4GHz** Wi-Fi network.
4. In Home Assistant, add the discovered ESPHome integration. If discovery fails, add the device by its local IP.
5. Use one command slot to learn a harmless command from your original remote, then replay it and observe the appliance.

**Checkpoint:** the unit appears online in Home Assistant and the learned command changes the intended appliance. Confirm repeatability before attaching automations.

### Development and recovery

Factory firmware offers ten learned command slots. For richer air-conditioner state control, use an ESPHome climate implementation for the actual protocol, starting from Seeed's project source. A complete AC state packet is different from a universal on/off code.

Record the ESPHome version and source commit before building. Save learned-code/configuration data before replacing firmware. Restore the factory build through the official project or Seeed's gadget flashing route; custom firmware can change provisioning and button behavior.

### FAQs

**No hotspot?** A configured device normally rejoins its saved network. Check power, network availability and the documented reset procedure.

**Learning fails?** Check the original remote battery, aim at the receiver and reduce sunlight or other IR interference.

**Home Assistant reports offline?** Check the Wi-Fi lease and local network reachability before reflashing.

**Does successful transmission prove appliance state?** Usually it proves that a command was sent. Without feedback, confirm the appliance's actual state before building dependent automation.

### Sources and validation

* [Official setup, pin map and recovery](https://wiki.seeedstudio.com/XIAO_IR_Mate_Smart_IR_Remote/)
* [Hardware design archive](https://files.seeedstudio.com/wiki/XIAO_IR_MATE/XIAO_IR_REMOTE_hardware.zip)
* [Official ESPHome project](https://github.com/Seeed-Studio/xiao-esphome-projects/tree/main/projects/xiao_smart_ir_mate)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
