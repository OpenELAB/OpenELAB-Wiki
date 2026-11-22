# Agile Robots training 2: pendant, modes and project review

{% hint style="info" %}
Scope: Industrial pendant V3.3. First result: a read-only UI and project inventory. Home, Free Drive, enabling, I/O writes and Run can cause motion or external actuation.
{% endhint %}

## Read the interface before operating

The pendant separates Startup, Manual Operation, Programming and System Settings. Startup displays model/pose, tool, joint temperatures, bus voltage/current and state; its Start/Stop controls concern brakes. In the switched-power cabinet route, arm Power On/Off is a separate operation. The displayed coordinate system, current tool and speed setting affect later manual commands. Source: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 5–8, 11–25](../source-library/); [EN\_2\_How\_to\_use\_teach\_pendant.pptx, slides 3–18](../source-library/).

## Orientation checklist

1. Complete [first connection](system-startup.md); retain motion/output controls inactive.
2. Inspect the **Manual Operation** pose and joint displays. Diana has seven joints; Thor has six. Check the selected Base/TCP/Workpiece frame and tool name against the installation record.
3. Inspect the current project tree and variable/waypoint tables. Record project name, version and referenced tool/workpiece frames. Do not open a different active project, delete instructions, overwrite waypoints or Run merely to explore the UI.
4. Inspect **System Settings → System Log**, status and **About**. Export a redacted log when diagnosing a fault. Clear display and clear fault are different actions.
5. Record coordinate/load, I/O and safety configuration identities for authorized review. Reading an ordinary I/O status is different from writing an output connected to a gripper, valve or machine.

**Expected result:** a model/version/project/frame/status record without motion, project replacement or output actuation. Sources: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 9–10, 121–124, 164–169](../source-library/); [EN\_2\_How\_to\_use\_teach\_pendant.pptx, slides 20–41](../source-library/).

## Functions with additional prerequisites

| Function                         | Why the initial checklist does not activate it                                                    |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| Jog / Home / saved-point Move    | Clear path, correct frame/units, mode, approved speed and on-site enabling procedure              |
| Free Drive / flange teach button | Verified load, center of mass, inertia, gravity and workspace; can cause drift/collision if wrong |
| Nullspace motion                 | Diana-specific redundant-joint function; do not transfer to six-axis Thor                         |
| Impedance modes                  | Return forces/torques depend on the chosen mode; do not treat as an unpowered arm                 |
| I/O toggles and scripts          | May actuate peripheral equipment even when the arm does not move                                  |
| Calibration / safety settings    | Qualified model-specific procedure, controlled change and acceptance record                       |

The training packaging-position and script examples are demonstrations, not safe destinations for a tool-equipped cell. Slide 27 has inconsistent variable spelling and a joint/pose example; it is not copied as runnable code. Use [the state-only API example](industrial-api.md) or [the no-motion Lua log example](pendant-lua.md) for a first programming result.

## Troubleshooting

An unexpected frame/tool or joint count blocks later motion. A blocked mode/stop state requires investigation, not repeated reset. If a log reports overspeed, retain the limits and inspect the operation and configuration. Use [fault isolation](troubleshooting.md) and [SCU/JMU review](safety-configuration.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                | Coverage  |
| ------------------------------------------------------------------------------------------------------ | --------- |
| [Agile Robots training 2 — Teach Pendant](../source-library/complete-en-2-how-to-use-teach-pendant.md) | 45 slides |

### Full pendant workflow

The forty-five slides cover startup/main screens, joint/TCP displays, base/tool/workpiece frames, Home, free-drive, Diana nullspace and impedance modes, speed/precision settings, I/O, program/logic/variable tools, system logs/status, maintenance and SCU configuration. The corresponding full V3.3 manual adds every screen, option and procedure.

Before jogging or teaching, verify the selected frame and the actual TCP/workpiece definitions. Nullspace teaching is a redundant Diana-arm workflow, not a six-axis Thor feature. Home, packaging, impedance, waypoint execution and gripper outputs are motion-capable operations. An I/O page can energize a peripheral even when the arm does not move; distinguish reading a DI from writing a DO.

Review joint-vector length against the actual robot. Slide 27's formatted program contains inconsistent identifiers and a six-element joint allocation, so it is retained as source evidence, not offered as a runnable Diana seven-axis example. The full reader keeps the exercise joint tables attached to their model labels; they are not generic startup targets.

SCU editing, joint zero calibration and impedance changes require their own authorization and acceptance within the installation. The source's example factory login is not a production credential policy. Use the actual fault/status/log evidence before a reset or configuration change.

### Source chapter map

| Source section                            | Full detail                                                                    |
| ----------------------------------------- | ------------------------------------------------------------------------------ |
| Basic Training                            | [Slide 1](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-1) |
| How to use Teach Pendant                  | [Slide 2](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-2) |
| Slide 3                                   | [Slide 3](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-3) |
| Slide 4                                   | [Slide 4](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-4) |
| How to use Teach Pendant (2)              | [Slide 5](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-5) |
| Manual Move - Robot Arm Position Display  | [Slide 6](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-6) |
| Manual Move - Coordinate system selection | [Slide 7](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-7) |
| Manual Move - Home                        | [Slide 8](../source-library/complete-en-2-how-to-use-teach-pendant.md#slide-8) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
