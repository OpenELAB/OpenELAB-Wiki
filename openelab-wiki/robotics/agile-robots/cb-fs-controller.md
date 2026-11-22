# CB-FS-3.2T: power, networks and I/O

{% hint style="info" %}
**Model:** CB-FS-3.2T · **Scope:** V1.0.1; variant must match the arm

No separate exact OpenELAB product/SKU match was verified. This is a manufacturer-document reference; no substitute store URL or SKU is asserted.
{% endhint %}

## Product overview

This is the controller for a matched robot system, not an interchangeable general power supply. Confirm the full cabinet suffix, arm/serial pairing, installed I/O options and software configuration. A cabinet or pendant rating does not transfer to the complete robot/workcell.

## Applications

Arm power/control, teach-pendant operation, external application communications and a configured stop chain. Safety interfaces require qualified design and validation; ordinary I/O does not become safety rated through a software mapping.

## Specifications

| Parameter                           | Value and scope                                                                                |
| ----------------------------------- | ---------------------------------------------------------------------------------------------- |
| Variants / robot mapping            | 0.3KW: Diana 3; 0.6KW: Diana 7, Thor 7, Thor 7 Pro, Thor 12; 1KW: Thor 20                      |
| Mains                               | 110–240 V AC, 50/60 Hz                                                                         |
| Dimensions / mass                   | 483 × 377 × 192 mm / 16 kg                                                                     |
| Controller protection / temperature | IP20 / 0–50 °C                                                                                 |
| General I/O                         | Standard 16 DI / 16 DO / 2 AI / 2 AO; 32/48 digital options are separate fitted configurations |
| Pendant                             | TP3.1: 12.1-inch 1280 × 800 display, 1.75 kg, IP65 pendant rating                              |

Source: [CB-FS-3.2T Controller User Manual V1.0.1.pdf, PDF pp. 19–20](source-library.md). Respect the nameplate and delivered regional mains/earthing instructions. Arm average/instantaneous power figures are not a substitute for the cabinet's input specification.

## Hardware and connections

Four Ethernet ports: A for API/PC soft pendant and the Diana FCI manual route; D for application TCP/IP or Modbus TCP; B/C are reserved/unsupported in this manual. The DB9 serial connector combines RS232/RS485 signals; DB15 external encoder supplies 5 V and supports two encoder channels. Use the exact front-panel and connector-view drawings, not a generic DB9 or Ethernet cable assumption.

Dual-channel emergency/protective stop interfaces, eight safety-input groups and eight safety-output groups; PNP safety signals. These are distinct from ordinary configurable I/O. The supplied SCU/JMU configuration tool specifically covers this CB-FS family.

Source: [CB-FS-3.2T Controller User Manual V1.0.1.pdf, PDF pp. 22–41](source-library.md). Disconnect mains and follow the prescribed isolation/discharge procedure before cable work. Only authorized service personnel may open the cabinet. The commissioning guide does not include internal high-voltage work or safety bypass links.

The DI/DO common-terminal connections select PNP/NPN behavior in groups. External I/O power, ordinary controller outputs, tool power and safety power are separate electrical budgets. Use the exact manual's table and load limits before wiring; never connect two supplies together because both are labeled 24 V.

## Software and development resources

Use the delivered pendant and Industrial API package for the exact cabinet/model. Factory PC UI/API network is `192.168.10.75`; a physical pendant normally connects through the dedicated pendant network at `192.168.1.75:6050`. The PC soft-pendant UI uses `192.168.10.75:6050`. Those addresses are source defaults; actual delivered configuration wins. See [interface and network selection](development/interfaces-network.md).

## Getting started

1. Verify the matched arm/cabinet serials, full model suffix, supply, protective earth, cable locking, ventilation clearance and qualified stop/enabling-device acceptance with power isolated.
2. Connect the approved pendant/arm cables and the controller's documented mains supply. Do not hot-plug or interchange controllers simply because connectors fit.
3. Have the responsible operator follow [startup](development/system-startup.md) with the workspace clear and no motion command. On CB-style switched arm supplies, UI availability may precede arm 48 V power and brake release; these are different states.
4. Inspect **Startup**, **About**, mode and error/status information. For PC access, connect to port A and configure a unique same-subnet address, not the controller's own address.
5. Record the controller/arm/software versions and I/O option. Leave Start, brake release, motion and ordinary output toggles inactive for this first connection check.

**Expected result:** the intended controller and arm appear in the UI with traceable software/status information. Network reachability does not prove safe I/O operation or authorize automatic motion.

## Troubleshooting and FAQs

**UI connects but the application device does not:** check A versus D, IP routing, the protocol role and configured bus endpoint. Do not treat all four Ethernet sockets as a generic switch.

**Unexpected I/O polarity or voltage:** isolate the circuit and inspect the exact common-group and external/internal supply arrangement with a qualified technician. Do not test by toggling an actuator output.

**Robot remains disabled:** preserve mode, stop/enabling state and errors; resolve the cause. Never bridge safety terminals or use an unrelated cabinet's wiring example.

## Downloads and technical documents

[CB-FS-3.2T Controller User Manual V1.0.1.pdf and exact connector drawings](source-library.md) · [Networks and interface mapping](development/interfaces-network.md) · [Safety configuration scope](development/safety-configuration.md) · [Backup/update planning](development/backup-updates.md)

## References and validation

[CB-FS-3.2T Controller User Manual V1.0.1.pdf, PDF pp. 19–20; PDF pp. 22–41](source-library.md); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 190–191](source-library.md). Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
