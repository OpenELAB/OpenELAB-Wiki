# Thor 7 Pro: force-controlled variant reference

{% hint style="info" %}
**Model:** Thor 7 Pro · **Scope:** Series brochure; exact Pro arm manual not supplied

No separate exact OpenELAB product/SKU match was verified. This is a manufacturer-document reference; no substitute store URL or SKU is asserted.

[Manufacturer product information](https://www.agile-robots.com/en/products/thor-series/)
{% endhint %}

## Product overview

Thor 7 Pro is the torque-sensing, force-controlled six-axis member of the Thor series. It shares the 7 kg/900 mm headline with Thor 7 but is a separate variant, with different mass, speed and interface coverage. Its own delivered mechanical/dynamic configuration is required.

## Applications

Force-sensitive assembly and manipulation where the delivered control option, tool and application have been validated. Manufacturer force-control relative accuracy is not an absolute-force calibration certificate or a safe-contact guarantee.

## Specifications

| Parameter                            | Value and scope                                      |
| ------------------------------------ | ---------------------------------------------------- |
| Axes / payload / reach               | 6 / 7 kg / 900 mm                                    |
| Arm mass                             | 38 kg                                                |
| Repeatability                        | ±0.03 mm, manufacturer series figure                 |
| Maximum TCP speed                    | 2.5 m/s                                              |
| Force-control relative accuracy      | 0.5 N manufacturer figure; conditions matter         |
| Protection / temperature             | IP54 / 0–50 °C                                       |
| Controller                           | CB-FS-3.2T-0.6KW                                     |
| Integrated tool electrical interface | Series brochure marks “–”; do not copy Thor 7 pinout |

Sources: [AR-ThorSeries-Productflyer-SCREEN-en.pdf, specification table, PDF pp. 4–5](source-library/); [current series brochure](https://www.agile-robots.com/media/files/New_website/Products/Thor_series/AR-ThorSeries-Productflyer-SCREEN-en-20260320.pdf), PDF p. 7; [manufacturer model description](https://www.agile-robots.com/en/products/thor-series/).

## Hardware and connections

The training mounting table lists four M8 base fasteners for Pro, but a Pro-specific mounting/load/torque drawing was not supplied. Use the exact delivered drawing before choosing fastener length, engagement or reaction-load design. The normal Thor 7 powered-flange table is not a Pro wiring authority. Use the matched [CB-FS controller](cb-fs-controller.md) and documented external tool arrangement.

## Software and development resources

Industrial API uses six joint entries for Thor. Obtain a Pro-specific model/algorithm/firmware package; do not substitute ordinary Thor 7 parameters to obtain force control. The supplied CB-FS safety manual explicitly lists Thor 7 Pro, but that does not validate a generic safety configuration. See [API selection](development/industrial-api.md) and [SCU/JMU review](development/safety-configuration.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                      | Coverage    |
| -------------------------------------------------------------------------------------------- | ----------- |
| [Thor series product flyer](source-library/complete-ar-thorseries-productflyer-screen-en.md) | 5 PDF pages |

### Force-controlled variant scope

The full Thor-series flyer retains every model column, parameter, drawing and feature claim. Keep the Pro row/column distinct from ordinary Thor 7. A shared payload class, silhouette or base fastener pattern does not establish the same torque sensing, force-control behavior, controller, tool wiring or SDK support.

Before powered integration obtain the delivered Thor 7 Pro operating manual, controller/force-sensing configuration, support matrix, tool/electrical interfaces and safety/recovery procedures. Record exact model labels, software/package versions, joint limits, payload and calibration. The ordinary Thor 7 manual can provide comparison context but is not a substitute for missing Pro-specific procedures. No unsupported force-control recipe is inferred from the brochure.

## Getting started

1. Keep the arm de-energized until the Pro nameplate, 0.6KW controller, mechanical drawings, tool-interface documents and delivered configuration are reconciled. 2(features and their licenses. Compare them with the Pro-specific software/BOM record rather than the ordinary Thor 7 label.
2. After the integrator's installation/safety acceptance, use [the UI identification workflow](development/system-startup.md) to record model, software and six-joint status without starting a task or Free Drive.
3. Stop if the delivered model package or tool connection is not explicit. Do not use force control or powered tooling as the first test.

**Expected result:** an identified Pro configuration and version/status baseline. Powered tool setup and force experiments remain blocked until their exact supporting documents are available.

## Troubleshooting and FAQs

**32 kg or 3.1 m/s appears in an example:** those are Thor 7 figures. Verify Pro's 38 kg/2.5 m/s scope and delivered model package.

**A hand-guiding demonstration drifts:** stop, verify the load/TCP/gravity configuration and the supplied Pro procedure. Do not alter collision thresholds or copy another robot's calibration.

## Downloads and technical documents

[Supplied/current Thor brochures, CB-FS manual and training references](source-library/) · [Ordinary Thor 7 guide for comparison](thor-7.md) · [Development workflows](development/)

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**. Pro-specific arm installation, powered-tool and force-control procedures were not established by the supplied ordinary Thor 7 manual; those operations are not presented as ready.
