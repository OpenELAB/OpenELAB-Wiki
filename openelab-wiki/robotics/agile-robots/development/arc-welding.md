# Arc welding V3.3: supported welders and dry-run boundaries

{% hint style="info" %}
Scope: supplied Arc Welding Function Manual V3.3.0. First result: review welder/protocol/configuration and a no-arc plan. No live arc, wire feed or robot path is tested here.
{% endhint %}

## Confirm the supported equipment

The manual uses **Modbus TCP**, robot as master and welder as slave. It lists Aotai NBC-350RL and NBC-400RP/500RP Plus; Megmeet entries are explicitly **not supported yet** in this revision. A selectable brand/model in a UI is not sufficient evidence of support. Verify the actual welder/firmware and supplier integration map. Sources: [Arc Welding Function Manual \_V3.3.0\_EN\_20260204.pdf, PDF pp. 3–6](../source-library/).

The illustrated `192.168.0.100:502`, request timeout 200, is an example configuration, not a universal welder address or a controller PC-network setting. Application communication uses the controller's documented route, ordinarily port D, and its own verified addressing. Keep welding power/control, work return, shielding-gas, fume/UV/fire protection, guarding and stop integration within the qualified welding-cell design.

## Review connection and process records

1. Keep welding energy inhibited through the accepted hardware/procedure, with the robot stopped and area controlled. Identify the torch, welder, tool load/TCP, fixture, I/O/Modbus map and stop interactions.
2. Inspect **System Settings → Bus & IO → Modbus TCP** and **Welding Process Settings**. Record master/slave role, actual slave endpoint, selected brand/model and associated IP without applying new settings.
3. Record process number, mode, units and accepted parameter recipe. UI input ranges, such as current, gas times and travel speed, are capability limits rather than an approved welding recipe.
4. Record the reconnect behavior: the manual describes reconnection after some logout/login scenarios. Do not rely solely on a red disconnected icon or software checkbox as energy isolation.

**Expected result:** a traceable supported-welder/protocol/configuration record and a reviewed dry-run plan, with no arc, gas, wire feed or robot movement. Source: [Arc Welding Function Manual \_V3.3.0\_EN\_20260204.pdf, PDF pp. 4–12](../source-library/).

## Dry run still involves motion

The manual's **Welding Disabled** state suppresses the welder's gas/arc output while a welding program can still move the robot through its weaving trajectory. This is not a stationary or safe-state guarantee. Before a supervised dry run, independently verify welding energy inhibition, tool/TCP/load, every path/transition, workholding, guards and the robot's risk-assessed motion envelope.

Wire-feed, gas and manual-control buttons can actuate equipment independently of an arm path. Do not use them for the first connectivity check. Source: [Arc Welding Function Manual \_V3.3.0\_EN\_20260204.pdf, PDF pp. 19–22](../source-library/).

## Programming and acceptance

The manual defines Lua welding commands and process/trajectory associations. Use the delivered V3.3 definitions, actual supported welder and approved recipe; do not invent a generic arc-on script or publish guessed current/voltage settings as an application recipe. After a qualified dry-run acceptance, live welding needs its own process, quality and safety validation.

## Troubleshooting

Connection green but wrong process: compare selected welder/model, associated slave IP and firmware/map. Arc feedback timeout: stop and isolate the process; inspect source-defined feedback, interlocks and parameters rather than extending retries blindly. Unexpected reconnection: keep the independent energy isolation effective and investigate the startup/login logic. See [fault records](troubleshooting.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                            | Coverage     |
| ------------------------------------------------------------------------------------------------------------------ | ------------ |
| [Arc welding function manual V3.3.0](../source-library/complete-arc-welding-function-manual-v3-3-0-en-20260204.md) | 26 PDF pages |

### Full process and equipment coverage

The complete manual retains the supported-welder information, connection/configuration screens, weld-process settings, instructions, parameters and examples. Keep the exact welder model/interface, controller/software, process configuration, I/O mapping and units together. An advertised family name is not proof that a particular welder firmware or option is supported.

Separate robot trajectory validation from arc-start/stop, wire-feed, gas and other process outputs. The arm can remain stationary while those outputs energize equipment. A pendant dry-run or simulation setting is not proof of electrical/process isolation; use the approved cell procedure and verify the actual peripheral state.

For an integration record, retain the torch/TCP and payload, workpiece frame, installed welder/interface, channel mapping, approved process values, start/end behavior, interlocks and fault-recovery responsibility. Test a trajectory and process only through the staged, attended and authorized acceptance procedure. Do not clear a welder error or replay an interrupted weld command merely because communications recover.

The source examples are available in full for engineering review. No arc, gas, wire-feed, motion or welding-safety test was run during this documentation update.

### Source chapter map

| Source section                        | Full detail                                                                                        |
| ------------------------------------- | -------------------------------------------------------------------------------------------------- |
| 1. Overview                           | [PDF 3](../source-library/complete-arc-welding-function-manual-v3-3-0-en-20260204.md#pdf-page-3)   |
| 2. Arc Welding Function Configuration | [PDF 3](../source-library/complete-arc-welding-function-manual-v3-3-0-en-20260204.md#pdf-page-3)   |
| 3. Arc Welding Commands               | [PDF 23](../source-library/complete-arc-welding-function-manual-v3-3-0-en-20260204.md#pdf-page-23) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
