# Agile Robots development and training: choose the correct route

{% hint style="info" %}
**Platform scope:** Diana/Thor Industrial V3.3, delivered controller and exact feature configuration. Franka FR3, Agile Hand and humanoid SDKs have separate requirements.
{% endhint %}

## Training sequence

| Guide                                                         | First result / boundary                                           |
| ------------------------------------------------------------- | ----------------------------------------------------------------- |
| [1. Startup and first connection](system-startup.md)          | Matched system, controller-specific mains and UI identity         |
| [2. Pendant orientation](teach-pendant.md)                    | Modes, projects, variables and read-only status/log review        |
| [3. Coordinates, payload and tools](coordinates-tools.md)     | TCP/workpiece definitions, inertia and model-specific tool wiring |
| [4. Interfaces and programming routes](interfaces-network.md) | A/D networks, SDK versus embedded scripts and peripheral protocol |
| [5. Backup and software updates](backup-updates.md)           | Verified export before a model-specific controlled migration      |
| [6. Fault isolation](troubleshooting.md)                      | Logs and ordered checks while preserving stop functions/limits    |

## Development and specialist workflows

| Workflow                                         | Scope                                                                            |
| ------------------------------------------------ | -------------------------------------------------------------------------------- |
| [Industrial C/C++ and Python](industrial-api.md) | External host; versioned SDK, model joint count, SI units and state-only example |
| [Pendant Python](pendant-python.md)              | Context-based embedded script; finite log-only check                             |
| [Pendant Lua](pendant-lua.md)                    | mm/ms/degrees; finite log/delay check                                            |
| [Diana FS FCI](diana-fci.md)                     | Specific V3.3 FS configurations; exact client pairing required                   |
| [CB-FS SCU/JMU](safety-configuration.md)         | Scope/version and configuration/verification/signature review                    |
| [Arc welding](arc-welding.md)                    | Supported welder, Modbus role and no-arc/motion boundaries                       |

## Keep platform and units explicit

Diana uses seven Industrial API joint entries; Thor uses six. TCP poses remain six components. External C/C++/Python and pendant Lua use different units and entry points. An interface named FCI does not establish identical network, dynamics, gripper support or version selection across vendors.

For Franka Research 3 use the [existing Franka development series](../../franka/development/). For [Agile Hand](../agile-hand.md) and [H10-W](../h10-w.md)/[H20](../h20.md), the available brochures establish specifications but leave power, delivered SDK and whole-system commissioning requirements to exact integration documents. They do not inherit the industrial arm API by association.

## Acceptance and source versions

Record robot/controller serials, model, software/firmware/configurations, tool/load, calibration/frames, stop acceptance and the expected result before experiments. Preserve the difference between source-reviewed examples and executed tests. Manufacturer manuals and training can contain old links, generic wiring and outdated examples; the [source/revision notes](../source-library/) identify the differences that affect this series.

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                                                      | Coverage      |
| -------------------------------------------------------------------------------------------------------------------------------------------- | ------------- |
| [Industrial C/C++ API manual V3.3.0](../source-library/complete-industrial-api-manual-c-c-edition-v3-3-0-en-20260605/)                       | 190 PDF pages |
| [Industrial Python API manual V3.3.0](../source-library/complete-industrial-api-manual-python-edition-v3-3-0-en-20260205/)                   | 165 PDF pages |
| [Industrial Lua programming manual V3.3.0](../source-library/complete-industrial-lua-programming-manual-v3-3-0-en-20260117/)                 | 192 PDF pages |
| [Industrial teaching pendant manual V3.3.0](../source-library/complete-industrial-teaching-pendant-software-user-manual-v3-3-0-en-20260204/) | 286 PDF pages |
| [Safety configuration manual V3.3.0](../source-library/complete-safety-function-configuration-software-user-manual-v3-3-0-en-20260204.md)    | 53 PDF pages  |
| [Diana 7 FCI guide V1.3](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md)                               | 17 PDF pages  |
| [Arc welding function manual V3.3.0](../source-library/complete-arc-welding-function-manual-v3-3-0-en-20260204.md)                           | 26 PDF pages  |

### Select one delivered programming contract

The complete external C/C++, external Python, pendant Lua, pendant UI, Diana FCI, safety-configuration and welding references remain distinct. They differ in execution context, permissions, units, joint/pose representation, side effects and hardware support. The shared V3.3 label does not merge them into one interchangeable API.

Record hardware/controller/force-sensor options, software/SDK/package revisions, host prerequisites, tool/payload and coordinate frames before choosing a route. Start with the route's smallest documented state/log result. Keep activation, motion, process outputs, firmware, calibration and safety changes under the corresponding complete application procedure.

The six full training decks supplement the manuals with screenshots and examples. Their historical addresses, updater package, generic supply text and simplified examples are retained with source notes; they do not override exact-model documentation. No SDK compilation, robot motion, welding or hardware safety test is claimed.
