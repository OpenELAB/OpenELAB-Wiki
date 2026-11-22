# RCB2.1.1T-0.3KW: power, networks and I/O

{% hint style="info" %}
**Model:** RCB2.1.1T-0.3KW · **Scope:** V1.2, Version B; Thor 3 controller route

No separate exact OpenELAB product/SKU match was verified. This is a manufacturer-document reference; no substitute store URL or SKU is asserted.
{% endhint %}

## Product overview

This is the controller for a matched robot system, not an interchangeable general power supply. Confirm the full cabinet suffix, arm/serial pairing, installed I/O options and software configuration. A cabinet or pendant rating does not transfer to the complete robot/workcell.

## Applications

Arm power/control, teach-pendant operation, external application communications and a configured stop chain. Safety interfaces require qualified design and validation; ordinary I/O does not become safety rated through a software mapping.

## Specifications

| Parameter         | Value and scope                                                             |
| ----------------- | --------------------------------------------------------------------------- |
| Robot route       | Thor 3 in supplied/current series brochures                                 |
| Mains             | 200–240 V AC, 50/60 Hz; not CB-FS 110–240 V                                 |
| Dimensions / mass | 563 × 414 × 192 mm / 20 kg                                                  |
| Temperature       | 0–50 °C                                                                     |
| General I/O       | Standard 16 DI / 16 DO / 2 AI / 2 AO; optional 32/48 digital configurations |
| Pendant           | TP3.1: 12.1-inch 1280 × 800, 1.75 kg, IP65 pendant rating                   |

Source: [RCB2.1.1T-0.3KW Controller User Manual V1.2 EN.pdf, PDF p. 15](source-library/). Respect the nameplate and delivered regional mains/earthing instructions. Arm average/instantaneous power figures are not a substitute for the cabinet's input specification.

## Hardware and connections

Ethernet interface X19 provides A for API/soft pendant, D for TCP/IP/Modbus TCP and reserved B/C. Its physical connector names and safety wiring differ from the CB-FS cabinet. A pendant IP setting is not the same as an application-bus port.

The safety interface is the model-specific DB25 female connector X20, with paired emergency-stop, safety-door and enabling paths. Do not apply the CB-FS PNP safety-terminal map or SCU/JMU software workflow to this cabinet.

Source: [RCB2.1.1T-0.3KW Controller User Manual V1.2 EN.pdf, PDF pp. 18–37](source-library/). Disconnect mains and follow the prescribed isolation/discharge procedure before cable work. Only authorized service personnel may open the cabinet. The commissioning guide does not include internal high-voltage work or safety bypass links.

The DI/DO common-terminal connections select PNP/NPN behavior in groups. External I/O power, ordinary controller outputs, tool power and safety power are separate electrical budgets. Use the exact manual's table and load limits before wiring; never connect two supplies together because both are labeled 24 V.

## Software and development resources

Use the delivered pendant and Industrial API package for the exact cabinet/model. Factory PC UI/API network is `192.168.10.75`; a physical pendant normally connects through the dedicated pendant network at `192.168.1.75:6050`. The PC soft-pendant UI uses `192.168.10.75:6050`. Those addresses are source defaults; actual delivered configuration wins. See [interface and network selection](development/interfaces-network.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                             | Coverage     |
| ------------------------------------------------------------------------------------------------------------------- | ------------ |
| [RCB2.1.1T-0.3KW controller manual V1.2](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md) | 46 PDF pages |

### Complete controller interface and lifecycle reference

The full manual retains enclosure/mounting and environmental data, mains and protective-earth requirements, controller/arm/pendant connections, every network/general-I/O/safety-interface drawing, the power/startup sequence and the service/transport/disposal information. Select the exact controller label and revision before a cable, supply or configuration file.

Keep mains input, protective earth, arm load power, peripheral/tool supply, normal I/O references and protective circuits separate in the wiring plan. Verify connector view, current rating, supply source and NPN/PNP role for each peripheral. A host network adapter or a standard DO cannot provide a substitute safety circuit. Keep factory jumper diagrams attached to their delivered configuration and the validated installation design.

Allow the specified clearances, cooling and cable bend/strain requirements. Record the delivered software and connected arm/pendant, inspect accessible connections with the required isolation and retain configuration/fault evidence before changes. A network link, reset click or UI login is not a completed electrical or safety-function acceptance.

The inspection and maintenance tables distinguish visual checks, functional checks, cleaning and authorized internal service. Preserve their intervals and conditions from the original pages; do not replace a specified maintenance procedure with an informal reboot. Configuration, mechanical, electrical or peripheral changes need the affected acceptance repeated.

### Source chapter map

| Source section              | Full detail                                                                                     |
| --------------------------- | ----------------------------------------------------------------------------------------------- |
| 1. SAFETY                   | [PDF 5](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-5)   |
| 1.1. SAFETY REGULATIONS     | [PDF 5](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-5)   |
| 1.2. SAFETY SIGNS           | [PDF 7](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-7)   |
| 1.3. PERSONNEL REQUIREMENTS | [PDF 8](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-8)   |
| 1.4. PRECAUTIONS            | [PDF 8](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-8)   |
| 1.5. EMERGENCY STOP         | [PDF 11](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-11) |
| 2. SAFETY FUNCTIONS         | [PDF 12](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-12) |
| 2.1. SAFETY LIMITS          | [PDF 12](source-library/complete-rcb2-1-1t-0-3kw-controller-user-manual-v1-2-en.md#pdf-page-12) |

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

[RCB2.1.1T-0.3KW Controller User Manual V1.2 EN.pdf and exact connector drawings](source-library/) · [Networks and interface mapping](development/interfaces-network.md) · [Safety configuration scope](development/safety-configuration.md) · [Backup/update planning](development/backup-updates.md)

## References and validation

[RCB2.1.1T-0.3KW Controller User Manual V1.2 EN.pdf, PDF p. 15; PDF pp. 18–37](source-library/); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 190–191](source-library/). Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
