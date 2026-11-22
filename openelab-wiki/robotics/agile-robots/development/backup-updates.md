# Agile Robots training 5: backup and software updates

{% hint style="info" %}
First result: verified backup artifacts and an exact update plan. A project export, configuration backup and software upgrade are separate operations.
{% endhint %}

## Inventory before changing software

Record robot/controller serials, model, firmware, Industrial software, pendant, mechanical/algorithm/control-box/safety configurations and installed feature options. Keep the actual tool/load, frames, I/O mapping, safety signature and project records together. The 14 October 2025 deck demonstrates a V3.2 updater; it is not a current download or a universal V3.3 migration package.

## Export a backup

1. Stop tasks and secure tools/workpieces through the accepted on-site procedure. Do not export an actively edited/running project as if it were a final snapshot.
2. Use the pendant's **Export Project** function. Choose the intended project and export scope deliberately; preserve program files, variables, waypoints, frames and I/O mapping as applicable. Export to a controlled local folder or the correctly identified USB device.
3. Verify the success message, filenames, sizes and expected exported contents. Retain the original and a separately stored copy. Record a checksum on the host; do not test restore on the live production cell merely to validate a download.
4. Back up the controller/configuration package using the exact supplied maintenance/updater procedure. Do not assume that a project export contains firmware, model dynamics or the safety configuration/signature.

**Expected result:** readable, identified backup artifacts with export scope, version/serial record and a retention location. No firmware or configuration is changed by this checkpoint. Sources: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 209–215, 229–235](../source-library/); [EN\_5\_Data\_backup\_and\_software\_updates.pptx, slides 4–8](../source-library/).

## Prepare an update as a separate controlled change

Obtain the manufacturer-approved package for the exact model, controller and starting software, its release notes/checksums, required configuration migration, rollback/recovery method and post-update acceptance plan. Distinguish the pendant UI package from lower-level robot service, joint firmware and SCU/JMU changes. The supplied V3.3 UI manual has separate logged-out and logged-in upgrade routes; follow the route supported by the delivered system.

The Diana FCI V1.3 document explicitly requires fresh model/configuration files for a V3.2-or-earlier to V3.3 migration rather than retaining the old configuration. That potentially destructive migration needs a complete backup, model-specific approved files and qualified revalidation. It is not a reason to run the old deck's updater or uncheck retention blindly. Sources: [How to Use FCI on Diana7（English version）V1.3-20260209.pdf, PDF pp. 11–12](../source-library/); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 198–201](../source-library/).

## Verify after an authorized update

Compare displayed versions and model/serial/configuration identities to the approved plan. Review gravity, TCP, payload, tool envelope, I/O mappings, stop behavior and safety signature. Record the prescribed safety/operational acceptance before normal tasks resume. A UI “update OK” message alone does not establish correct dynamics, calibrated frames or safe motion.

## Troubleshooting

Package/model mismatch: stop before transfer. Missing configuration: retain the old system and obtain the exact package. Failed update: preserve updater/system logs and use the supported recovery procedure; avoid repeated power cycling or restoring another robot's configuration. See [fault reporting](troubleshooting.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                             | Coverage  |
| ------------------------------------------------------------------------------------------------------------------- | --------- |
| [Agile Robots training 5 — Backup and Updates](../source-library/complete-en-5-data-backup-and-software-updates.md) | 10 slides |

### Backups before software changes

The ten slides retain network setup, individual project export to PC/USB, FactoryUpdater connection, model selection, configuration/engineering backup, configuration-file selection and pendant upgrade. A project export and a controller configuration backup serve different recovery purposes; keep both with the delivered hardware/software identity and verify that the saved files are readable.

The training's `FactoryUpdater_v2.6_industry-v3.2.0` name is a historical example. Do not select it merely because the current documentation series is V3.3. Match the actual controller/model and approved target package. Mechanical, control-box, algorithm and safety configuration files are model-specific; a software configuration file is required only when explicitly specified by the release instructions.

The shown network is 192.168.10.0/24 with controller .75. Choose an approved unused ordinary host address, excluding the controller, network and broadcast addresses; the slide's 0–255 wording is overbroad. Keep a recoverable route and site-approved VPN/network policy. A ping response is a transport observation, not proof of model identity or updater compatibility.

Record the existing version, backups, target and recovery plan before an authorized update. Afterward verify installed versions, restored projects/configuration and the required safety/application acceptance. No firmware, pendant or configuration update was executed during this documentation work.

### Source chapter map

| Source section                       | Full detail                                                                              |
| ------------------------------------ | ---------------------------------------------------------------------------------------- |
| Update Training                      | [Slide 1](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-1)   |
| Data backup and software updates     | [Slide 2](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-2)   |
| Data backup and software updates (2) | [Slide 3](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-3)   |
| Data backup and software updates (3) | [Slide 4](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-4)   |
| Data backup and software updates (4) | [Slide 5](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-5)   |
| Data backup and software updates (5) | [Slide 6](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-6)   |
| Data backup and software updates (6) | [Slide 7](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-7)   |
| Data backup and software updates (7) | [Slide 8](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-8)   |
| Data backup and software updates (8) | [Slide 9](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-9)   |
| Slide 10                             | [Slide 10](../source-library/complete-en-5-data-backup-and-software-updates.md#slide-10) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
