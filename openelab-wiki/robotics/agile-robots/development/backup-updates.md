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

**Expected result:** readable, identified backup artifacts with export scope, version/serial record and a retention location. No firmware or configuration is changed by this checkpoint. Sources: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 209–215, 229–235](../source-library.md); [EN\_5\_Data\_backup\_and\_software\_updates.pptx, slides 4–8](../source-library.md).

## Prepare an update as a separate controlled change

Obtain the manufacturer-approved package for the exact model, controller and starting software, its release notes/checksums, required configuration migration, rollback/recovery method and post-update acceptance plan. Distinguish the pendant UI package from lower-level robot service, joint firmware and SCU/JMU changes. The supplied V3.3 UI manual has separate logged-out and logged-in upgrade routes; follow the route supported by the delivered system.

The Diana FCI V1.3 document explicitly requires fresh model/configuration files for a V3.2-or-earlier to V3.3 migration rather than retaining the old configuration. That potentially destructive migration needs a complete backup, model-specific approved files and qualified revalidation. It is not a reason to run the old deck's updater or uncheck retention blindly. Sources: [How to Use FCI on Diana7（English version）V1.3-20260209.pdf, PDF pp. 11–12](../source-library.md); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 198–201](../source-library.md).

## Verify after an authorized update

Compare displayed versions and model/serial/configuration identities to the approved plan. Review gravity, TCP, payload, tool envelope, I/O mappings, stop behavior and safety signature. Record the prescribed safety/operational acceptance before normal tasks resume. A UI “update OK” message alone does not establish correct dynamics, calibrated frames or safe motion.

## Troubleshooting

Package/model mismatch: stop before transfer. Missing configuration: retain the old system and obtain the exact package. Failed update: preserve updater/system logs and use the supported recovery procedure; avoid repeated power cycling or restoring another robot's configuration. See [fault reporting](troubleshooting.md).

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
