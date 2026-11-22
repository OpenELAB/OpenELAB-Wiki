# Training 1: system startup and first connection

{% hint style="info" %}
**First result:** identify the system and reach the correct UI without commanding movement. The October 2025 Startup deck is supplemented by the installed-version operating manual. Qualified installation and stop verification precede power-on.
{% endhint %}

## Prerequisites

Use [the FR3 Arm guide](../fr3-arm.md) for hardware scope and the matching manual. Prepare a commissioned installation or a responsible integrator for first commissioning, the supplied stop/enabling devices, correct end effector, a browser computer and Ethernet cable. Leave the workspace and jaw travel clear. Read [System Startup training, 21 October 2025, slides 3–6](../source-library/).

## Connect to the UI network

1. Record the Arm and Control labels and their serial/hardware versions. Verify that the mounting/wiring/stop checklist is complete; do not power a loose arm on a bench.
2. Connect the computer to **X5 at the arm base**, enable DHCP and follow the approved power-on procedure. The default robot address is `192.168.0.1` and its DHCP client pool is `192.168.0.100–150`.
3. Open `https://robot.franka.de` in the browser. If DNS is unavailable, use the confirmed robot-network address. Do not use a guessed corporate-network address or assign the robot's address to the host.
4. For an already configured system, use the assigned local account. Inspect **Settings → Dashboard** and record the System Image. Read the controller-provided manual via the System menu.

Sources: [FR3 Arm v2.1 hardware manual R02210/1.2/EN, PDF pp. 40–43, 64–65](../source-library/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §3.1 and §6. The UI connection is distinct from the wired C2 link needed for FCI.

## First Start on a new system

Follow the matching operating manual's First Start sequence: language, network, Franka World association/synchronization, local Administrator and end-effector configuration. The 5.10 manual describes online and offline synchronization paths and requires the user to belong to the same World account/organization as the robot. Do not substitute another organization's account or create a duplicate organization merely because the robot is absent.

For the end effector, choose **None** only when no tool is mounted, the appropriate **Hand** profile for the actual Hand, or **User Defined** with verified mass/inertia for another tool. Incorrect tool data can cause unexpected guiding behavior. Keep the end effector unloaded because homing may happen when power is restored. Initial safety/Watchman configuration requires the responsible qualified personnel; a tutorial cannot pre-approve a universal safety scenario.

## Verify and record the first result

Save the Arm/Control identity, System Image, browser network and tool profile. Check reported faults and that the local account role matches the intended work. Keep brake-open, task, jog, FCI, calibration and recovery controls inactive during this baseline.

**Expected result:** the correct system's UI/status and configuration checklist are available. On a new robot, registration/configuration prerequisites are resolved before the installation is declared commissioned. No arm or mobile motion is used as a connectivity test.

## Troubleshooting and shutdown

**No UI:** inspect the physical X5 connection, DHCP lease, host routing and DNS/VPN/proxy interference. Resolve duplicate subnets before altering robot settings.

**World synchronization cannot complete:** verify correct organization membership and robot assignment, then use the installed version's online/offline workflow. Obtain support for unresolved assignment problems rather than factory-resetting the robot as a first action.

**A warning remains:** record the exact message, version and time. Follow the matching recovery procedure; do not clear safety faults to get past the checklist.

Shut down through the documented UI procedure and wait for the controller's confirmation before removing mains. TMR/Mobile soft shutdown is a separate, version-specific process and must use its delivered manual.

## Sources and validation

[System Startup training, 21 October 2025, slides 3–13](../source-library/); [FR3 Arm v2.1 hardware manual R02210/1.2/EN, PDF pp. 62–70](../source-library/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §§3, 6 and 8. Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                     | Coverage  |
| --------------------------------------------------------------------------- | --------- |
| [Franka training 1 — System Startup](../source-library/complete-startup.md) | 14 slides |

### Complete startup workflow and checkpoints

The fourteen slides cover equipment identification, data sheets, the X5 browser route, initial setup, World resources, software/licensing and the documentation/tutorial ecosystem. Their original hyperlinks are retained in the slide reader, including links to older manuals, Desk API/RIDE, FCI/ROS, Modbus and OPC UA resources.

Use the hardware labels and compatible manual set first. Then inspect the installed network and reach the UI on the intended local interface. The shown 192.168.0.1 / host-range example is a factory training profile, not an instruction to replace a working site network. A browser login confirms the UI route; it does not verify the Control-side real-time FCI path.

Record the Control identity, System Image, end-effector configuration and selected organization/licenses before planning an update. World synchronization changes software/license state and is separate from mounting, safety-peripheral and application acceptance. Follow the exact operating manual for the initial physical setup; the closing Diagnostics and Testing slide does not itself define a test procedure.

### Source chapter map

| Source section          | Full detail                                                |
| ----------------------- | ---------------------------------------------------------- |
| Slide 1                 | [Slide 1](../source-library/complete-startup.md#slide-1)   |
| Basic Training          | [Slide 2](../source-library/complete-startup.md#slide-2)   |
| System Startup          | [Slide 3](../source-library/complete-startup.md#slide-3)   |
| System Startup (2)      | [Slide 4](../source-library/complete-startup.md#slide-4)   |
| System Startup (3)      | [Slide 5](../source-library/complete-startup.md#slide-5)   |
| System Startup (4)      | [Slide 6](../source-library/complete-startup.md#slide-6)   |
| System Startup (5)      | [Slide 7](../source-library/complete-startup.md#slide-7)   |
| System Startup (6)      | [Slide 8](../source-library/complete-startup.md#slide-8)   |
| System Startup (7)      | [Slide 9](../source-library/complete-startup.md#slide-9)   |
| System Startup (8)      | [Slide 10](../source-library/complete-startup.md#slide-10) |
| System Startup (9)      | [Slide 11](../source-library/complete-startup.md#slide-11) |
| System Startup (10)     | [Slide 12](../source-library/complete-startup.md#slide-12) |
| System Startup (11)     | [Slide 13](../source-library/complete-startup.md#slide-13) |
| Diagnostics And Testing | [Slide 14](../source-library/complete-startup.md#slide-14) |
