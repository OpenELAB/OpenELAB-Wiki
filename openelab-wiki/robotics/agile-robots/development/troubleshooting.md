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

Sources: [EN\_6\_Quick\_Troubleshooting.pptx, slides 3–6](../source-library.md); [CB-FS-3.2T Controller User Manual V1.0.1.pdf, PDF pp. 26–27](../source-library.md); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 121–124, 153, 190–191](../source-library.md).

## Export evidence

1. Open **System Settings → System Log** and record the current levels/status. The log's Follow view tracks current events; do not interpret the absence of one displayed message as absence of stored history.
2. Use **Export** and choose a controlled local/USB destination. Confirm successful export and preserve the original.
3. Include the version/configuration record, exact failing operation and whether it occurred at idle, enabling or motion. Remove credentials, customer programs and unnecessary personal/site information from copies shared for support.
4. Prepare the fault report for the normal support process. This wiki does not send it or change the robot.

**Expected result:** an inspectable log bundle and a bounded problem description, with limits/stop functions unchanged. Sources: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 121–124](../source-library.md); [EN\_6\_Quick\_Troubleshooting.pptx, slides 3–6](../source-library.md).

## Correct a legacy training suggestion

The training's free-drive overspeed slide suggests removing the thresholds. V3.3 confirms that zeroed values remove free-drive speed thresholds. That is a configuration change, not fault recovery; this guide does not recommend it. Likewise, a factory jumper diagram is not permission to short an application safety circuit. Resolve the risk-assessed configuration with the responsible safety operator and manufacturer. See [SCU/JMU configuration review](safety-configuration.md).

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
