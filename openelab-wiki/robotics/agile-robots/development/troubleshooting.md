# Agile Robots training 6: fault isolation and evidence

{% hint style="info" %}
First result: a reproducible, redacted fault record. Keep stop functions and limits effective while diagnosing the problem.
{% endhint %}

## Preserve the state

Stop the operation and secure the area/load according to the delivered procedure. Record timestamp, arm/cabinet serials, model, software/configuration versions, mode, tool/load, exact error text/code and last deliberate action. Do not automatically clear a collision/error and resume a task while investigating.

## Diagnose by symptom

| Symptom                           | Ordered checks                                                                                                                                             |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UI cannot reach controller        | Correct port A, cable/link, actual address/subnet, unique PC address and route/VPN conflict; physical pendant and PC UI use different documented endpoints |
| UI online, arm supply reads 0 V   | Cabinet/UI power and switched arm 48 V are separate; inspect Startup state and required on-site procedure before Power On or enabling                      |
| Brake/servo remains disabled      | Inspect emergency/protective stop, enabling device, operating mode, controller indicators and error log; no bypass jumpers                                 |
| Drift or unexpected guiding force | Stop; verify model, mounting/gravity direction, tool mass/CoM/inertia, TCP and qualified calibration                                                       |
| Free Drive overspeed              | Retain limits, slow/stop the operation and review the load/configuration and prescribed thresholds                                                         |
| Abnormal joint noise              | Stop the activity; record affected joint, state, loading and available existing audio/video; do not reproduce unsafe motion for a recording                |
| Peripheral does not respond       | Isolate the electrical circuit; verify device model, power/reference, NPN/PNP common groups, protocol/port and actual map before any output write          |

Sources: [EN\_6\_Quick\_Troubleshooting.pptx, slides 3–6](../source-library/); [CB-FS-3.2T Controller User Manual V1.0.1.pdf, PDF pp. 26–27](../source-library/); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 121–124, 153, 190–191](../source-library/).

## Export evidence

1. Open **System Settings → System Log** and record the current levels/status. The log's Follow view tracks current events; do not interpret the absence of one displayed message as absence of stored history.
2. Use **Export** and choose a controlled local/USB destination. Confirm successful export and preserve the original.
3. Include the version/configuration record, exact failing operation and whether it occurred at idle, enabling or motion. Remove credentials, customer programs and unnecessary personal/site information from copies shared for support.
4. Prepare the fault report for the normal support process. This wiki does not send it or change the robot.

**Expected result:** an inspectable log bundle and a bounded problem description, with limits/stop functions unchanged. Sources: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 121–124](../source-library/); [EN\_6\_Quick\_Troubleshooting.pptx, slides 3–6](../source-library/).

## Correct a legacy training suggestion

The training's free-drive overspeed slide suggests removing the thresholds. V3.3 confirms that zeroed values remove free-drive speed thresholds. That is a configuration change, not fault recovery; this guide does not recommend it. Likewise, a factory jumper diagram is not permission to short an application safety circuit. Resolve the risk-assessed configuration with the responsible safety operator and manufacturer. See [SCU/JMU configuration review](safety-configuration.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                               | Coverage |
| ----------------------------------------------------------------------------------------------------- | -------- |
| [Agile Robots training 6 — Troubleshooting](../source-library/complete-en-6-quick-troubleshooting.md) | 8 slides |

### Evidence-led fault isolation

The eight slides organize power, communications and operational observations. Start from the actual fault text/code, mode, enable/stop state, model/software and recent changes. Inspect accessible cable/connector condition and the correct network/pendant path using the delivered manual; internal electrical checks and work on energized equipment need qualified service personnel.

The source's reset/brake clicks and network LEDs are observations, not acceptance tests. The .75 ping example checks only one network route. Preserve active controller, pendant and host settings before changing an address or restarting. For a noise report, record the affected joint, operating conditions and a safely obtained recording rather than repeatedly reproducing a dangerous condition.

The source proposes setting speed limits to zero for a free-drive overspeed problem. That statement is retained in the complete reader and explicitly excluded from the general recovery workflow. Investigate tool/gravity configuration, actual motion and the approved limits; involve the responsible safety person for a proposed configuration change. Do not bypass protective circuits or clear recurring faults without determining the cause.

Keep before/after evidence for the approved repair or recovery and repeat the affected acceptance checks. A reboot, cleared message or audible brake release does not establish that the underlying installation is safe.

### Source chapter map

| Source section               | Full detail                                                                 |
| ---------------------------- | --------------------------------------------------------------------------- |
| Update Training              | [Slide 1](../source-library/complete-en-6-quick-troubleshooting.md#slide-1) |
| Quick Troubleshooting        | [Slide 2](../source-library/complete-en-6-quick-troubleshooting.md#slide-2) |
| Quick Troubleshooting (2)    | [Slide 3](../source-library/complete-en-6-quick-troubleshooting.md#slide-3) |
| Quick Troubleshooting (3)    | [Slide 4](../source-library/complete-en-6-quick-troubleshooting.md#slide-4) |
| Quick Troubleshooting (4)    | [Slide 5](../source-library/complete-en-6-quick-troubleshooting.md#slide-5) |
| Quick Troubleshooting (5)    | [Slide 6](../source-library/complete-en-6-quick-troubleshooting.md#slide-6) |
| Exercise - Advanced Training | [Slide 7](../source-library/complete-en-6-quick-troubleshooting.md#slide-7) |
| Slide 8                      | [Slide 8](../source-library/complete-en-6-quick-troubleshooting.md#slide-8) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
