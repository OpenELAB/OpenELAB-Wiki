# Training 3: Franka World, organizations and software

{% hint style="info" %}
**Scope:** account/robot association and software planning. Supplied screenshots are from October 2025. The current public guide describes Franka World 2.0; use its organization terminology and current role permissions.
{% endhint %}

## Separate personal account, organization and robot

[Franka World](https://franka.world/) manages organizations, members and robot software. Your personal login can belong to multiple organizations with different roles. The robot's **local** Administrator and Safety Operator are separate robot-side identities. The supplied slides' “Account” screens are a historical interface reference.

Sources: [Franka World training, 22 October 2025, slides 3–7](../source-library.md); [current Franka World user guide](https://download.franka.de/franka-world-manual/), Parts 1–3.

## First association review

1. Use your assigned personal World account and accept the invitation to the existing lab/company organization when applicable. Select the intended organization before looking for robots.
2. Check your organization role and ask the responsible administrator for the access needed for the actual task. Do not create a second organization to work around missing membership.
3. Locate the robot and verify its Control serial number and organization assignment against the physical system. Check the installed System Image in the robot's local Dashboard.
4. Inspect available compatible System Version strategy and Software Packages without applying changes. Record required FCI/app features and the intended library/ROS versions.
5. On a first-start or offline robot, follow the matching robot manual's synchronization path. The 5.10 manual describes downloading a synchronization file through the robot-provided World link; its prerequisites include membership in the robot's assigned account/organization.

**Expected result:** the correct organization and robot are identified, permissions are appropriate and the proposed software configuration is recorded. No update, ownership transfer, membership change or robot operation is required for this review.

## Online and offline update planning

The current World guide distinguishes selecting software in the cloud from actually synchronizing/installing it on an online or offline robot. A selection saved in World does not prove the robot has finished updating. Compare desired and installed versions and retain the completion evidence from the robot UI.

Before applying software, verify the Arm/Control compatibility matrix and dependent libfranka, ROS, tool, app and research-workspace versions. Back up the required configuration and project data, plan controlled downtime, keep power stable and follow the installed manual. Do not downgrade as a troubleshooting shortcut: the 5.10 operating manual warns that a downgrade can cause a factory reset.

## Accounts and data boundaries

Use assigned organization roles for membership/robot actions. Inviting users, transferring robots, changing software or deleting an organization are separate administrative decisions. Keep authentication tokens and recovery information out of research datasets and screenshots. Notification preferences in the old slides are not a substitute for robot ownership/permission verification.

## Troubleshooting

**The robot is missing:** first check selected organization, invitation/membership state, role and serial/assignment. Do not register a duplicate robot or factory-reset it merely to make it appear.

**World and Desk show different versions:** distinguish desired software, downloaded changes, applied changes and completed restart. Follow the installed-version synchronization instructions and collect exact status/logs.

**Offline sync fails:** verify the robot-provided link/file, intended organization, software compatibility and file integrity. Use the current guide and the robot's matching operating manual rather than copying an old screenshot's button sequence.

## Sources and validation

[Franka World training, 22 October 2025, slides 3–7](../source-library.md); [System Startup training, 21 October 2025, slides 6–8](../source-library.md); [Franka World 2.0 user guide](https://download.franka.de/franka-world-manual/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §§3 and 8. Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**. No account, organization, license, update or robot state was changed during this documentation task.
