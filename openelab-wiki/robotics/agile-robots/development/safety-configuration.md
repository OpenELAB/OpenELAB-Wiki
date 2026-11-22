# CB-FS safety configuration: scope, review and acceptance

{% hint style="info" %}
Scope: Safety Function Configuration Software V3.3 for supported CB-FS-3.2T systems. First result: inspect versions and the existing safety record. No safety parameter is changed by this tutorial.
{% endhint %}

## Confirm applicability

The supplied manual covers CB-FS-3.2T-0.3KW with Diana 3, -0.6KW with Diana 7/Thor 7/Thor 7 Pro/Thor 12, and -1KW with Thor 20. It requires supported SCU and JMU hardware/firmware. It does not establish compatibility with the RCB Thor 3 controller, a Franka Watchman configuration or a humanoid stop system.

The manual requires the robot to be powered off during safety-parameter configuration. Have qualified personnel establish the precise arm/controller maintenance power state and procedure for the delivered system; an available network/UI is not evidence that motion is safely disabled. Source: [Safety Function Configuration Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 3–4](../source-library/).

## Inspect the record first

1. Complete the model/controller/serial inventory and obtain the approved application risk assessment and existing safety acceptance record.
2. In **About**, inspect SCU/JMU versions. Record the current safety configuration identity, relevant tool/workpiece frames, load and installation/gravity direction.
3. Review, without unlocking or applying, the active safety-function set, speed/position limits, virtual walls, tool envelope, safety I/O, safe positions and operating modes against the approved design.
4. Preserve an existing approved safety export/signature and a backup through the delivery-specific process. Do not load a generic configuration to see whether an alarm disappears.

**Expected result:** a versioned, model-specific safety review record and a list of differences for qualified resolution. No configured limit, stop path, signature or device state has been altered. Sources: [Safety Function Configuration Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 3–10, 22–46](../source-library/).

## Understand a controlled configuration change

The SCU workflow is **Unlock → Modify → Apply → verify displayed/backend data → confirm → Signature → Save Device → automatic lock**. JMU uses its documented verification/save flow without the SCU signature step. Apply, verification and persistent Save Device are distinct. A signature acknowledges a reviewed configuration; it does not prove an independent physical stop test passed.

Only authorized qualified personnel should conduct that process, with the arm in the prescribed de-energized state, exact approved parameters and a documented acceptance plan. Protect assigned credentials; do not copy a training screenshot's default account/password into a public commissioning checklist. Source: [Safety Function Configuration Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 7–20](../source-library/); [EN\_2\_How\_to\_use\_teach\_pendant.pptx, slides 39–41](../source-library/).

## Model and tool consistency

Ordinary tool coordinates, mass/CoM/inertia and safety geometry must describe the same installed equipment. A wrist tool change can affect stopping, reachable geometry and load even when no program line changes. Safety I/O and ordinary DI/DO mappings are different interfaces. Do not set every speed, collision or power threshold to a permissive value as a workaround.

## Troubleshooting and acceptance

Unsupported SCU/JMU version: obtain the matched manufacturer upgrade plan; do not improvise firmware replacement. Data mismatch after Apply: stop the change and resolve it before signing/saving. Missing prior signature/export: treat the record as incomplete. After an authorized change, perform and record all required functional/safety tests before operation; none were performed for this wiki.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                                                   | Coverage     |
| ----------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| [Safety configuration manual V3.3.0](../source-library/complete-safety-function-configuration-software-user-manual-v3-3-0-en-20260204.md) | 53 PDF pages |

### Full safety-configuration lifecycle

The complete manual retains SCU/JMU version information, safety interfaces, all parameter pages and the configuration/verification workflow. Keep the controller, safety hardware/firmware, arm, tool, mounting and software identity together. A screenshot of accepted values is not evidence that another installation has the same safety configuration.

The source covers such areas as tool/workpiece definitions, load/gravity, momentum/power, collision, velocity/position limits, virtual walls, tool envelope/pose, safety I/O, points and operating modes. Preserve coordinate frames, units, active mode and the actual tool/workpiece geometry for each item. A normal I/O signal or host-side condition is not a replacement for the relevant safety-rated circuit/function.

The training distinguishes loading/viewing a page, backend verification, configuration editing, applying, confirmation/signing and saving. These are separate actions. Retain the approved configuration, identity/checksum evidence and a recovery copy, then perform the complete required restart and functional validation. An apply/save message alone does not establish correct safety behavior.

Treat a limit change, calibration change, tool geometry change or proposed bypass as a safety-system modification. Resolve the underlying issue and obtain the responsible safety review and acceptance for the actual installation. This reference does not recommend disabling limits to clear an overspeed condition.

### Source chapter map

| Source section                              | Full detail                                                                                                             |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 1. Overview                                 | [PDF 3](../source-library/complete-safety-function-configuration-software-user-manual-v3-3-0-en-20260204.md#pdf-page-3) |
| 2. Teach Pendant Safety Function Parameters | [PDF 3](../source-library/complete-safety-function-configuration-software-user-manual-v3-3-0-en-20260204.md#pdf-page-3) |
| 3. Safety Function Configuration            | [PDF 7](../source-library/complete-safety-function-configuration-software-user-manual-v3-3-0-en-20260204.md#pdf-page-7) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
