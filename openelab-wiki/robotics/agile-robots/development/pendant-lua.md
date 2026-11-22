# Industrial Lua V3.3: units, scripts and log-only check

{% hint style="info" %}
Scope: the pendant Script instruction and supplied Industrial Lua V3.3 manual. First result: a finite no-motion log/delay script, with no peripheral writes.
{% endhint %}

## Keep units and APIs distinct

The Lua robot interface is designed to match pendant units: **millimeters, milliseconds and degrees**. External Industrial C/C++ and Python use SI units. Thus `delay(1000)` is one second, and a Lua waypoint in degrees must not be copied as API radians. Check each function's declaration, parameter types and return semantics; a Lua pose is not automatically an RPY vector. Source: [Industrial Lua Programming Manual\_V3.3.0\_EN\_20260117.pdf, PDF pp. 4, 6–7](../source-library/).

## Prepare the script environment

Use the matching installed Industrial pendant. The robot command functions are provided inside its project/Script environment, not by a generic desktop Lua installation. New/active-project selection and Run are operational changes; back up the current project and conduct the test in an empty, reviewed project with the responsible operator.

## First finite result

1. Create a controlled empty test project using the installed pendant's project-management procedure. Confirm no startup, parallel or background motion/output instructions exist.
2. Add a Lua Script instruction/program and enter:

{% code collapsedlinecount="10" %}
```lua
log("Agile Lua log-only check: begin")
local ok = delay(1000)
log("delay returned", ok)
log("Agile Lua log-only check: end")
```
{% endcode %}

3. Review the complete tree, then have the responsible operator run the isolated test under the accepted operating procedure.
4. Observe the ordered messages, the approximately one-second requested delay and the returned success/failure value. Stop normally and retain the script/software/log record.

**Expected result:** finite log messages with no motion, brake, payload, calibration, safety or peripheral command. The delay is not a real-time timing benchmark. This example is source reviewed and was not executed here. Source: [Industrial Lua Programming Manual\_V3.3.0\_EN\_20260117.pdf, PDF pp. 6–7](../source-library/).

## Develop beyond the first check

The manual covers subprograms, parameters, waypoints, movement, I/O and external communication. Identify tool/workpiece frame names, actual joint count and returned error conditions before adding robot commands. A seven-joint example is not a six-axis Thor joint vector. Register-level Modbus/Profinet code additionally needs the actual fitted bus option and device map.

Avoid copying an infinite training loop as a first program or silently ignoring a false result. Pausing a program is not the same as a safety stop, and a logging script is not proof that a motion trajectory is safe. See [frames/payload](coordinates-tools.md) and [safety acceptance](safety-configuration.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                                      | Coverage      |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------- |
| [Industrial Lua programming manual V3.3.0](../source-library/complete-industrial-lua-programming-manual-v3-3-0-en-20260117/) | 192 PDF pages |

### Complete Lua function reference

The full 192-page manual retains the system-call, robot-control, communications and remaining function groups, every argument/return convention and each call example. Its chapter/function index is linked from the complete reference. Pendant Lua is not interchangeable with the external Industrial API or context-based pendant Python.

Preserve each Lua function's documented units, which can use millimetres, degrees and milliseconds in places where another interface uses metres, radians or seconds. Also preserve scalar versus vector types, the actual arm joint count, base/tool/workpiece convention, timeout meaning and program context. A numeric value copied without its API context can be wrong by a large factor.

Separate log/state reads from variable and output writes, task/program control, calibration, motion, force/impedance and persistent configuration. Check return conventions explicitly; truth-like values and numeric status codes are not interchangeable. Keep a bounded log-only first result and retain actual error evidence before adding application behavior.

For asynchronous or repeated operations, define resource lifetime, timeout, cancellation and the expected postcondition. A script ending or a stop function returning does not validate every attached device's state. The source examples are preserved as references; no Lua, SDK, arm or fieldbus execution was performed.

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
