# Genmitsu PROVerXL 4030 V2: assembly, control and first dry run

{% hint style="info" %}
[**View Genmitsu PROVerXL 4030 V2: assembly, control and first dry run on OpenELAB**](https://openelab.io/products/proverxl-4030-v2-cnc-router)

**Product/option:** Genmitsu PROVerXL 4030 V2: assembly, control and first dry run · **Workbook SKU:** `101-60-XL4030V2-EB`
{% endhint %}

[101-60-XL4030V2-EB](https://openelab.io/products/proverxl-4030-v2-cnc-router)

## Product and scope

A desktop CNC router for controlled material-machining projects, fixture fabrication and prototyping. This page covers 101-60-XL4030V2-EB and the V2 resource set. Do not substitute original 4030 or extension-kit assembly dimensions.

## Hardware and technical documents

| Item                       | Reference                                               |
| -------------------------- | ------------------------------------------------------- |
| Model                      | PROVerXL 4030 V2                                        |
| Nominal XY work area       | 400 × 300 mm; usable travel depends on fixtures/tooling |
| Host interface             | USB serial CNC controller                               |
| Official control resources | UGS for Windows/macOS/Linux; Candle optional on Windows |

Use SainSmart's V2 resource page for the assembly manual, USB-stick files, controller software, probe and limit-switch instructions. Read the manual's electrical, enclosure and material restrictions before operation. Match spindle, controller and regional power supply labels. A motor's closed-loop behavior does not remove the need for workholding, limit checks and tool clearance.

## Getting started

1. Assemble the V2 using the supplied manual. Check fasteners, axis travel, cable routing, workholding and emergency-stop behavior.
2. Connect USB and identify the serial port. Install the official CH341 driver only if required by the host; open UGS or the documented Candle version with the controller's specified connection settings.
3. With the spindle disabled and the tool clear of the bed, jog each axis in small increments. Verify direction, units and the documented homing/limit sequence.
4. Set the work coordinate system and inspect a simple CAM toolpath. Confirm stock dimensions, tool length, safe height and travel limits.
5. Run a spindle-off air cut above the stock and observe the full path before attempting a shallow first cut with the appropriate tool and parameters.

**Expected checkpoint:** All axes move in the intended directions, the stop works, and an air-cut toolpath completes without exceeding the intended envelope.

## Development software and recovery

The normal workflow is CAD → CAM → controller-compatible G-code → sender. Use a postprocessor for the actual controller. Archive the original controller settings before adjustment. For alarms, record the exact GRBL error and consult SainSmart's linked code list; repeated unlocking can conceal a mechanical or limit problem.

## FAQs

**Why can the sender not connect?** Check the data cable, serial driver/port, connection parameters and whether another program owns the port.

**Can a 6060 extension use unchanged stock settings?** Update the mechanical setup, travel configuration and CAM envelope using the extension instructions.

**Is an SDK required?** No; start with the supported G-code sender workflow.

## Sources and validation

* [SainSmart V2 manuals, files, software and troubleshooting](https://docs.sainsmart.com/article/bhhdcyg7hk-prover-xl-4030-v2)
* [PROVerXL 4030 V2 user manual](https://genmitsu.s3.us-east-1.amazonaws.com/101-60-XL4030V2/PROVerXL_4030V2_User_Manual_v1.0-202306.pdf)
* [Universal Gcode Sender](https://winder.github.io/ugs_website/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
