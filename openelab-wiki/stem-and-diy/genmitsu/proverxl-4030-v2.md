---
description: >-
  Set up PROVerXL 4030 V2 with model-matched wiring, GRBL status checks,
  coordinate/probe validation, supervised dry runs and complete resource
  navigation.
---

# Genmitsu PROVerXL 4030 V2: assembly, control and first dry run

{% hint style="info" %}
[**View Genmitsu PROVerXL 4030 V2 CNC Router on OpenELAB**](https://openelab.io/products/proverxl-4030-v2-cnc-router)

**Model:** PROVerXL 4030 V2 · **SKU:** `101-60-XL4030V2-EB` · **Scope:** stock 400 × 300mm platform and its matched control box; record spindle, board and extension revisions before using a procedure.
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The PROVerXL 4030 V2 is a desktop GRBL-compatible CNC router with closed-loop NEMA23 axis motors and ball-screw motion. Establish controller identity and save settings **before any motion, probing, firmware change or cutting**. This guide separates a non-moving USB checkpoint from later supervised dry runs, and distinguishes the V2 machine from the original PROVerXL 4030 and extension kits. [SainSmart V2 resource center](https://docs.sainsmart.com/article/bhhdcyg7hk-prover-xl-4030-v2)

[Genmitsu manufacturer directory](./) · [4040-PRO MAX guide](genmitsu-4040-pro-max-cnc-router-engineering-guide.md)

## Applications

Use the machine for supported wood/plastic machining, signs, fixture prototypes and controlled material-development trials. Choose tooling and CAM parameters for the actual material, spindle, workholding and extraction system. Closed-loop motors help the drive respond to position error; they do not establish tool clearance, clamp security, unattended operation or a process capability for every material.

Separate CAD geometry, CAM toolpath generation, G-code postprocessing and controller execution. A sender that displays a file is not proof that the code uses the right units, work offset, safe height or spindle control.

## Specifications

| Parameter                  | V1.1 June 2023 manual reference                                 | Practical qualification                                              |
| -------------------------- | --------------------------------------------------------------- | -------------------------------------------------------------------- |
| Nominal work envelope      | 400 × 300 × 110mm                                               | Available space is reduced by tooling, fixtures and accessories      |
| Overall dimensions         | 740 × 605 × 488mm                                               | Add bench space for cables, extraction and operator access           |
| Control compatibility      | GRBL 1.1h; 8-bit reference controller                           | Read actual `$I` build information before assuming firmware identity |
| Maximum speed              | 5,000mm/min                                                     | Not a recommended cutting feed                                       |
| Structure                  | Metal frame; hybrid spoilboard                                  | Check flatness and workholding for the intended job                  |
| Motion                     | X/Y 1204 ball screws; Z 12mm linear shaft and 1204 ball screw   | Confirm alignment and lubrication before adding load                 |
| Axis motors                | NEMA23, 76mm closed-loop; 2.2N·m reference                      | This is axis-motor data, not spindle cutting torque                  |
| Stepper drive reference    | WSD6056DN56                                                     | Match the received control/drive revision                            |
| Stock spindle reference    | Up to 400W, 10,000rpm; adjustable 0–48V DC                      | A different fitted router needs its own power/control instructions   |
| Supply references          | 48V/7A and 24V/8A                                               | Internal system/supply ratings; do not improvise mains or DC wiring  |
| Advertised motion accuracy | Circular ≤±0.05mm; rectangular ≤±0.02mm; repositioning ≤±0.05mm | Manufacturer figures, not measured part tolerances                   |
| Control software           | GRBL-compatible sender such as Candle or UGS                    | Use the correct port, baud and postprocessor                         |

Source: [manufacturer manual, cover V1.1 June 2023, printed p.3](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/PROVerXL_4030V2_User_Manual_v1.0-202306.pdf#page=5). The URL contains `v1.0`, but the visible cover says **V1.1**. Record the document itself, not only its filename.

The resource center now also links a different [GM-43V2 manual file](https://genmitsu.s3.dualstack.us-east-1.amazonaws.com/GM-43V2/GM-43V2-AJ_Manual%20260708.pdf) whose cover reads **V2.0 July 2027**, while its filename includes `20260708`. That date/revision inconsistency remains unresolved. The USB baseline here uses the readable V1.1 reference; confirm the manual for the received hardware before assembly or controller replacement.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Mechanical assembly and inspection

The V1.1 manual’s sequence is important: compare left/right Y-carriage positions before attaching the gantry; install the X and XZ assemblies, coupling and motor, then the drag-chain brackets/chains. Keep cable routing clear throughout travel. The manual also includes a separate 65mm spindle-mount replacement procedure; it is not evidence that a new router is electrically compatible. [Assembly, printed pp.8–16](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/PROVerXL_4030V2_User_Manual_v1.0-202306.pdf#page=10)

Check the supplied modules, coupler, chains/brackets, clamping kit, probe, USB cable, power cord, tools and hardware against the manual’s illustrated inventory. Use its fastener positions and drawings rather than replacing a screw from a photograph. The closed-loop encoder adjustment is described as factory-set; do not turn it to compensate for a loose coupling or mechanical bind.

Keep the frame square on a rigid level bench. Inspect ball-screw/rail movement, coupling security, cable strain relief and full machine clearance with power isolated. Clean and lubricate the documented motion components as required; a longer travel setting is not a mechanical extension.

### Controller, spindle and stop behavior

With all power disconnected, identify the marked X/Y/Z limit and motor connections from the exact wiring drawing. Match control-box mains selection, regional cord and spindle supply before energizing. The manual directs checking its voltage selector; do not assume universal automatic input selection. Keep enclosures intact and the emergency stop reachable. [Wiring, printed pp.20–23](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/PROVerXL_4030V2_User_Manual_v1.0-202306.pdf#page=22)

An emergency stop, a sender’s feed hold and software reset have different effects. GRBL feed hold decelerates axis motion but does **not** by itself disable spindle/coolant. Verify the actual machine’s stop behavior with the spindle disabled and the work area clear; software control must not be assumed to isolate an independently powered router. [GRBL real-time commands](https://github.com/gnea/grbl/wiki/Grbl-v1.1-Commands#grbl-v11-realtime-commands)

Operate in a suitable indoor workshop with eye protection, workholding and material-appropriate extraction/ventilation. Keep people clear of the moving mechanism and supervise operation. Disconnect power before tool changes, wiring or mechanical service; do not open mains supplies as a routine diagnostic.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

| Tool/resource          | Role and boundary                                                                                                                      |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| CH340/CH341 USB driver | Install the manufacturer-linked package only if the host needs it; identify the actual newly enumerated serial device                  |
| UGS                    | Windows/macOS/Linux GRBL sender; inspect connection and firmware settings before opening a job                                         |
| Candle/GRBLControl     | Optional Windows workflow; unpack the whole application archive, not a lone executable                                                 |
| CAD/CAM                | Generate geometry and controller-compatible toolpaths; confirm GRBL postprocessor, units, stock, clearance, feeds and spindle commands |
| Supplied USB content   | Manual, driver, sender and sample files; treat samples as files to inspect before running                                              |
| Offline controller     | Separate device with its own menu/probe behavior; do not transplant Candle-only macros                                                 |
| Wi-Fi-module updater   | A distinct firmware target, not a generic GRBL or axis-drive update                                                                    |

The [resource center](https://docs.sainsmart.com/article/bhhdcyg7hk-prover-xl-4030-v2) indexes UGS, Candle, probe/limit guides, firmware, extensions and Fusion 360, Carveco, Easel and Vectric learning paths. Commercial software can require an account/license. A device SDK is not needed for normal G-code operation; the controller protocol and sender are the relevant development interfaces.

## Getting started

### First result: identify the controller without moving an axis

Prerequisites: correct assembled machine/control box, spindle disabled, clear work area, known USB data cable, accessible stop, sender and the matching manual. This stage does not start a spindle or homing cycle.

1. Check the model, control-box/spindle labels, wiring, mains selector and fixture/axis clearance with power isolated. Record the board and manual revision.
2. Connect USB, identify the new serial port and open Candle or UGS. The V1.1 reference uses **115200 baud, 8N1**. Close other serial clients.
3. Record the GRBL banner. In the sender console, issue the following queries individually, preserving each response:

```
$I
$$
$G
$#
$N
?
```

4. Save the build identity, full settings, modal state, coordinate/probe values, startup blocks and current state. An alarm is information to investigate; do not automatically send `$X`, `$H`, a reset-to-defaults command or motion.
5. Compare the reported controller and configured travel with the actual stock/extended hardware. Keep the original settings export before any configuration change.

**Expected result:** a valid build/banner and coherent settings/status responses while the mechanism remains stationary. The documented meaning of these queries is in the [GRBL command reference](https://github.com/gnea/grbl/wiki/Grbl-v1.1-Commands). Querying settings is different from commands containing `=`, which may write configuration or start a jog.

### Progress to a supervised dry run

After checking directions, limits, stop behavior and travel clearance, use the sender’s smallest deliberate jog increment to verify each axis separately. State the units explicitly and begin away from mechanical stops. Perform the matched homing sequence only after the switches and direction are established.

Use a GRBL-compatible postprocessor and inspect the entire job preview, including rapid moves, stock dimensions, work offset, tool length, retract height and clamp positions. With the spindle physically disabled and the tool path clear above the stock/fixtures, perform a supervised air cut. Stop at any unexpected direction, travel or status. Only then prepare a shallow, material/tool-specific coupon; no universal feed/RPM recipe is supplied.

Record machine coordinates and work coordinates separately. Homing establishes a machine reference; ZeroXY/ZeroZ establishes a work reference. Setting work zero does not establish that a machine is homed, and a closed-loop motor does not correct an incorrect CAM origin.

### Probe only after checking the actual plate and input

The manual contains example probe values **14mm** and **20.17mm**, and explanatory text that does not exactly match the shown macro. These are examples, not measurements of your supplied plate. Measure the plate, verify the probe input changes when contacted, confirm the intended downward travel, feed, work-offset convention and clearance, and use the procedure for the actual sender/controller. Remove the probe and clip before spindle operation. [V1.1 probe pages 29–31](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/PROVerXL_4030V2_User_Manual_v1.0-202306.pdf#page=31)

Do not paste a generic `G92` thickness or long probe stroke as a first connection test. SainSmart explicitly says the 4030 resource page’s generic probe article applies to Candle and that its offline-controller section is not the applicable 4030 offline workflow; use the separately linked offline-controller guide.

### Extensions and firmware recovery

The resource page includes **6060 and 1313** extension manuals. Complete their mechanical conversion and matched travel configuration before regenerating the CAM envelope. A toolpath or settings file for one extension is not a baseline for the other.

The resource link labelled a firmware update resolves to the [4030 V2 Wi-Fi Module Firmware Update Guide](https://docs.sainsmart.com/article/m6nco76c23-genmitsu-4030-v-2-wi-fi-module-firmware-update-guide). It uses IAP\_Programmer and a specific reconnect timing window. Identify that exact module and package before following it; this is not permission to flash the GRBL control board or motor drivers with a similarly named file. Export configuration and keep the supported recovery route first.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                               | Ordered checks                                                                                                                          |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| No serial connection                  | Data cable, new port, required driver, 115200 setting and exclusive port ownership; compare with the supplied USB resources             |
| Banner differs from expected          | Record `$I` and board label; match the received revision instead of forcing a historical image                                          |
| Alarm/homing failure                  | Read exact code and switch state, inspect wiring/direction/clearance; do not repeatedly unlock into a fault                             |
| Axis binds or loses position          | Power-isolated alignment, coupler, screw/rail cleanliness and work load; do not change the factory encoder adjustment as a first remedy |
| Probe dives or gives a wrong Z        | Stop motion; check actual plate thickness, electrical contact, macro mode/units, travel and sender-specific procedure                   |
| Part size/origin wrong                | Separate CAM units, work offset, machine home, tool diameter and mechanical calibration before changing steps/mm                        |
| Sender pause leaves spindle running   | Feed hold controls motion; use the verified machine stop/isolation method for spindle hazards                                           |
| 6060/1313 job exceeds travel          | Reconcile actual extension, controller limits, CAM stock and origin; do not disable limits to make it run                               |
| Update file has “4030 V2” in its name | Identify Wi-Fi module versus controller target and the exact package before any flash                                                   |

Use the exact GRBL error and the [SainSmart troubleshooting resources](https://docs.sainsmart.com/article/bhhdcyg7hk-prover-xl-4030-v2#troubleshooting). Preserve logs/settings and inspect a small test rather than re-running a failed cutting job unchanged.

## Downloads and technical documents

### Manual chapter map

| Printed pages in V1.1 | Scope                                                                      |
| --------------------- | -------------------------------------------------------------------------- |
| 1–3                   | Setup resources, workshop restrictions and specifications                  |
| 4–7                   | Illustrated inventory and dimensions                                       |
| 8–16                  | Carriage alignment, gantry/XZ, motor/coupler, drag chains and mount option |
| 17–19                 | Lead-screw/eccentric/encoder notes and maintenance                         |
| 20–23                 | Supply selection, limit/motor wiring and spindle connection                |
| 24–26                 | Driver, port and Candle configuration                                      |
| 27–28                 | Sender interface, job loading, work-zero example and factory configuration |
| 29–31                 | Probe setup; verify actual thickness and macro before use                  |

[Open the complete manufacturer V1.1 PDF](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/PROVerXL_4030V2_User_Manual_v1.0-202306.pdf). The live resource page’s newer cover/date discrepancy is recorded above rather than silently treated as the received machine’s revision.

### Official resource-center index

The following model-specific resource links were observed in the [V2 directory](https://docs.sainsmart.com/article/bhhdcyg7hk-prover-xl-4030-v2). A listed archive, video or paid training resource is not claimed fully downloaded, watched or executed. Verify model scope before using a shared article.

| Resource                                                                                                                                                                                                           | Purpose / source section |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------ |
| [Download the USB Stick Content](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/Genmitsu_PROVerXL4030V2_SD_Card_Package-0505.zip)                                                                     | Assembly                 |
| [PROVerXL 4030 V2 User Manual](https://genmitsu.s3.dualstack.us-east-1.amazonaws.com/GM-43V2/GM-43V2-AJ_Manual%20260708.pdf)                                                                                       | Assembly                 |
| [Laser Fixed Focus Module Installation Guide](https://docs.sainsmart.com/article/o9gxeljd59-laser-installation-guide)                                                                                              | Assembly                 |
| [6060 Extension Kit Installation Guide](https://genmitsu.s3.us-east-1.amazonaws.com/101-63-XYS4030V2-6060/Genmitsu_4030V2_6060_Extension_Kit_User_Manual_V2.0.pdf)                                                 | Extension Kit            |
| [1313 Extension Kit Installation Guide](https://genmitsu.s3.us-east-1.amazonaws.com/101-63-XYS4030V2-1313/Genmitsu_4030V2_1313_Extension_Kit_User_Manual.pdf_V2.0.pdf)                                             | Extension Kit            |
| [CH341SER Driver Version 3.9 (For Windows)](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/CH341SER.zip)                                                                                              | Driver                   |
| [CH341SER Driver (For Windows)](https://genmitsu.s3.us-east-1.amazonaws.com/CH341SER/CH341SER_202205.ZIP)                                                                                                          | Driver                   |
| [CH341SER Driver (For Mac)](http://s3.amazonaws.com/s3.image.smart/download/101-60-280PRO/CH341SER_MAC.zip)                                                                                                        | Driver                   |
| [CH341 Installation Guide](https://genmitsu.s3.us-east-1.amazonaws.com/CH341SER/How_to_Install_CH340_Drivers.pdf)                                                                                                  | Driver                   |
| [Click here to download UGS](https://winder.github.io/ugs_website/download/)                                                                                                                                       | Control software         |
| [https://winder.github.io/ugs\_website](https://winder.github.io/ugs_website/)                                                                                                                                     | Control software         |
| [How to Install Candle/GRBLControl for Windows](https://docs.sainsmart.com/article/7c20d7zaw3-how-to-install-candle-grblcontrol-for-windows)                                                                       | Control software         |
| [GRBLControl/Candle 1.17 (For Windows)](http://s3.amazonaws.com/s3.image.smart/download/101-60-3018PROVER/Grblcontrol\(Candle_1.1.7%20\).zip)                                                                      | Control software         |
| [Sainsmart Genmitsu PROVerXL 4030 CNC Router Build, Test & Review](https://youtu.be/ZLiBigGxLGo?t=603)                                                                                                             | Machine Operation        |
| [Guide on How to Set Up & Use Candle for Multiple Operations](https://sainsmart.helpdocs.io/article/bj9o96wcbc-how-to-set-up-use-candle-for-multiple-operations)                                                   | Machine Operation        |
| [Offline Controller User Guide](https://sainsmart.helpdocs.io/article/js1mp2rh0n-genmitsu-prover-xl-4030-offline-controller-user-guide)                                                                            | Machine Operation        |
| [What is a Z-Probe & How to Use It](https://docs.sainsmart.com/article/yhgowhcb8x-what-is-a-z-probe-how-do-i-use-it)                                                                                               | Machine Operation        |
| [How to Use Limit Switches to Maintain Positional Accuracy Between CNC Operations](https://docs.sainsmart.com/article/bi9jhbfgjf-how-to-use-limit-switches-to-maintain-positional-accuracy-between-cnc-operations) | Machine Operation        |
| [CNC Bit Selection Buyers Guide](https://cdn.shopify.com/s/files/1/1978/9859/files/CNC_Buying_Guide_V1.3-202104.pdf?v=1617328766\&fbclid=IwAR2bibDTEYEiikvm3YVwNM1IItrrD6o5_o4NNVDjmULWdYT9_saRV5dfkow)            | Machine Operation        |
| [GRBL Error Code List & Meaning](https://docs.sainsmart.com/article/dm4jbd5jce-grbl-error-codes)                                                                                                                   | Troubleshooting          |
| [CNC Router Trouble Shooting](https://docs.sainsmart.com/article/vhoiliz03s-3018-pro-cnc-router-trouble-shooting)                                                                                                  | Troubleshooting          |
| [The Beginner’s Guide to Genmitsu CNC Upgrade & Accessories](https://docs.sainsmart.com/article/pfit3ebx6z-the-beginner-s-guide-to-genmitsu-cnc-upgrade-accessories-updated-june-2021)                             | CNC Upgrade Resources    |
| [How to Install & Use a DeWalt 611 Router with a 4030 CNC](https://docs.sainsmart.com/article/a3odmawhhd-how-to-install-use-a-de-walt-611-router-with-your-4030-cnc)                                               | CNC Upgrade Resources    |
| [Genmitsu 4030 to 6060 Expansion Guide](https://docs.sainsmart.com/article/op57h2ppg4-genmitsu-6060-prover-xl-expansion-guide)                                                                                     | CNC Upgrade Resources    |
| [PROVerXL 4030 V2 Firmware Update Guide](https://docs.sainsmart.com/article/m6nco76c23-genmitsu-4030-v-2-wi-fi-module-firmware-update-guide)                                                                       | CNC Upgrade Resources    |
| [Quick-Start Guide](https://sainsmart.helpdocs.io/article/j3nxnaoejh-fusion-360-quick-start-guide-for-3018-pro-prover-cnc-s)                                                                                       | Other CAD/CAM Software   |
| [Understanding Roughing & Finishing Passes](https://sainsmart.helpdocs.io/article/awrxnhbk59-fusion-360-guide-to-understanding-roughing-finishing-passes)                                                          | Other CAD/CAM Software   |
| [How to Use Carveco Maker with your Genmitsu CNC](https://docs.sainsmart.com/article/n2s80bz2j5-how-to-use-carveco-maker-with-your-sain-smart-prover-xl-prover-or-genmitsu-machine)                                | Other CAD/CAM Software   |
| [Training & Tutorial Videos](https://carveco.com/support/training/)                                                                                                                                                | Other CAD/CAM Software   |
| [Link to Purchas 12 month subscription](https://www.sainsmart.com/products/carveco-maker-12-month-subscription?_pos=2&_sid=810517027&_ss=r)                                                                        | Other CAD/CAM Software   |
| [Link to Website](https://easel.inventables.com/)                                                                                                                                                                  | Other CAD/CAM Software   |
| [Desktop version is available on SainSmart.com](https://www.sainsmart.com/products/vectric-vcarve-desktop)                                                                                                         | Other CAD/CAM Software   |
| [V-carve desktop training video](https://www.vectric.com/support/tutorials/vcarve-desktop)                                                                                                                         | Other CAD/CAM Software   |
| [\[User Story\] PROVerXL 4030 V2 CNC router Work with Vectric Aspire](https://hardwarepoint.net/2024/06/vectric-aspire/)                                                                                           | Other CAD/CAM Software   |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026**. The OpenELAB SKU was matched to its active global-store listing. The V2 resource center, V1.1 English manual, visible newer-manual cover/specification pages, relevant GRBL command semantics and the Wi-Fi update guide were read. Official electrical/assembly illustrations remain available in their page-indexed PDFs.

No physical controller connection, settings query, motion, probe, cut, firmware update or hardware test was performed. Software/hardware execution is **not run**. Expected results are reproduction checkpoints. The guide improves the original summary with controller-first identification, explicit version/target distinctions, complete resource navigation and model-specific troubleshooting; actual process capability requires a measured coupon on the assembled machine.
