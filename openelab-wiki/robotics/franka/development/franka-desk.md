# Training 2: Desk, Settings and Watchman

{% hint style="info" %}
**Scope:** interface orientation and a non-motion configuration review. The supplied Desk deck is dated 22 October 2025. Screens, roles and menu placement depend on the installed System Image.
{% endhint %}

## Understand the interface before operating

Franka UI contains **Desk** for tasks/apps, **Settings** for robot configuration and **Watchman** for safety functions. Reach it using [the X5 first-connection procedure](system-startup.md). Local robot credentials and roles are separate from cloud Franka World membership.

The training slides' old product-manual page references do not identify the current chapter numbers. Use the controller's own manual and [manufacturer portal](https://franka.de/documents); the 5.10 operating manual describes these areas in §6 and safety configuration in later dedicated chapters.

## Read-only orientation checklist

1. Sign in using the role assigned for this task. Confirm the robot identity in the System menu and the System Image in **Settings → Dashboard**.
2. In **Desk**, locate Tasks, Apps, Groups, timeline and the status/sidebar areas. Inspect an existing task without starting or modifying it.
3. Review the System menu. **Reboot**, **Shut Down**, **Activate FCI** and rescue functions change system state; locating them does not mean executing them.
4. In **Settings → End Effector**, check the displayed tool profile and compare it with the physical tool and recorded load data. An unloaded bare arm, Franka Hand and Robotiq tool need different configurations.
5. Review local Users and Network settings using the available permissions. Do not change the robot network while relying on it for the session.
6. Open Watchman in viewing mode to identify the current safety configuration and responsible operator. A trained, authorized safety operator must evaluate changes and revalidate the complete application.

**Expected result:** a documented identity/version/tool/role review and a clear map of where controls are located, with no task execution or safety-setting change. Sources: [Franka Desk training, 22 October 2025, slides 3–15, 20](../source-library/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §§6–7.

## Guiding, Pilot and end-effector controls

Slides 7–10 introduce Guiding Mode, Pilot Mode, tool controls and robot status. Those are **motion-related operations**. Before any later practical exercise, verify the mode, the external enabling device, cleared motion/pinch envelope, tool mass/inertia and the exact installed-version operating procedure. Do not infer a safe state from a single LED color or dashboard value.

Hand power can be gated by SEEPO and may home when restored. A gripper button can cause an opening/closing or a loaded object release; keep it out of the first interface walkthrough. See [Hand-specific instructions](../franka-hand.md).

## Settings that require their own acceptance

| Area             | Review boundary                                                                                    |
| ---------------- | -------------------------------------------------------------------------------------------------- |
| Calibration      | Use exact arm procedure and qualified personnel; do not calibrate simply to remove a warning       |
| Modbus TCP       | Obtain the installed-version register map, roles and command semantics before integration          |
| Software updates | Back up required configuration/logs, check compatibility and schedule downtime before Apply        |
| Safety/Watchman  | Authorized safety personnel and validation of the complete installation                            |
| Logs             | Capture version, time zone, symptoms and relevant files while protecting credentials/personal data |

## Troubleshooting

**A control is unavailable:** check local role, operation mode and installed features before assuming a software fault. A cloud organization role does not grant a local safety role.

**A copied task behaves differently:** stop and compare tools, mass/inertia, frames, installation orientation and app/software versions. A matching task name is insufficient evidence of compatibility.

**Which manual does the “Safety” slide cite?** Slide 20 repeats an older log-download chapter reference. Use the actual Safety/Watchman section for the installed release, not that slide's page number.

## Sources and validation

[Franka Desk training, 22 October 2025, slides 3–20](../source-library/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §§6–8 and safety chapters; [Franka Hand R50010/1.2/EN, PDF pp. 21–24](../source-library/). Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                               | Coverage  |
| --------------------------------------------------------------------- | --------- |
| [Franka training 2 — Franka Desk](../source-library/complete-desk.md) | 21 slides |

### Desk, Settings and Watchman coverage

All twenty-one slides are retained: UI/login, Desk menu, user switching, guiding/Pilot, end-effector controls, robot state, Watchman and each Settings area. Distinguish a displayed status from an action that activates FCI, calibrates torque, changes network/user settings, powers the tool or modifies safety configuration.

Use Settings/Dashboard to identify the delivered image and hardware information; review active end-effector data and the intended access role. Guiding and Pilot controls can move the robot or fingers. A selected UI mode, default speed or successful login does not validate the working envelope or the tool configuration.

The source reserves Watchman editing to the Safety Operator. Treat changing safety geometry or thresholds as a controlled configuration change with subsequent validation. The older combined-product-manual page numbers in the slides do not map directly to the supplied Arm v2.1 hardware manual. In particular, slide 20 repeats a log-download reference for Safety; use the actual semantic Safety/Watchman chapter in the matching operating manual.

For support, retain the image/version, active role, configuration and system logs before restarting or updating. The complete source reader preserves the original screenshots and links rather than silently rewriting their historical UI labels.

### Source chapter map

| Source section          | Full detail                                             |
| ----------------------- | ------------------------------------------------------- |
| Slide 1                 | [Slide 1](../source-library/complete-desk.md#slide-1)   |
| Basic Training          | [Slide 2](../source-library/complete-desk.md#slide-2)   |
| Franka Desk             | [Slide 3](../source-library/complete-desk.md#slide-3)   |
| Franka Desk (2)         | [Slide 4](../source-library/complete-desk.md#slide-4)   |
| Franka Desk (3)         | [Slide 5](../source-library/complete-desk.md#slide-5)   |
| Franka Desk (4)         | [Slide 6](../source-library/complete-desk.md#slide-6)   |
| Franka Desk (5)         | [Slide 7](../source-library/complete-desk.md#slide-7)   |
| Franka Desk (6)         | [Slide 8](../source-library/complete-desk.md#slide-8)   |
| Franka Desk (7)         | [Slide 9](../source-library/complete-desk.md#slide-9)   |
| Franka Desk (8)         | [Slide 10](../source-library/complete-desk.md#slide-10) |
| Franka Desk (9)         | [Slide 11](../source-library/complete-desk.md#slide-11) |
| Franka Desk (10)        | [Slide 12](../source-library/complete-desk.md#slide-12) |
| Franka Desk (11)        | [Slide 13](../source-library/complete-desk.md#slide-13) |
| Franka Desk (12)        | [Slide 14](../source-library/complete-desk.md#slide-14) |
| Franka Desk (13)        | [Slide 15](../source-library/complete-desk.md#slide-15) |
| Franka Desk (14)        | [Slide 16](../source-library/complete-desk.md#slide-16) |
| Franka Desk (15)        | [Slide 17](../source-library/complete-desk.md#slide-17) |
| Franka Desk (16)        | [Slide 18](../source-library/complete-desk.md#slide-18) |
| Franka Desk (17)        | [Slide 19](../source-library/complete-desk.md#slide-19) |
| Franka Desk (18)        | [Slide 20](../source-library/complete-desk.md#slide-20) |
| Diagnostics And Testing | [Slide 21](../source-library/complete-desk.md#slide-21) |
