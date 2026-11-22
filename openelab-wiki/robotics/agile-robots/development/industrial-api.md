# Industrial API V3.3: C/C++ and Python state inspection

{% hint style="info" %}
Scope: manufacturer Industrial API, not pendant context scripting or FCI. First result: library/link and cached joint-state inspection without brake release, motion, output writes or automatic recovery.
{% endhint %}

## Obtain the exact SDK

Use the manufacturer's delivered native library, headers/Python wrapper and examples for the actual arm, host and Industrial software. The supplied manuals do not provide a verified public SDK download, source repository or redistribution license. Obtain these through the normal supplier channel, including release checksums/terms. No similarly named PyPI package, community ROS repository or AgileX UGV SDK is asserted as the official Industrial SDK.

The Python manual lists Ubuntu 18.04/20.04/22.04 x64 and Windows 10/11 x64, validated with Python 3.8.0. The C/C++ manual lists those x64 targets and Ubuntu 18.04 aarch64, with GCC 7.5.0/gcc-linaro-7.5.0 or MSVC 2017 as documented validation toolchains. These are the manual's tested-version claims, not proof of compatibility with an arbitrary current Python/OS/compiler. Sources: [Industrial API Manual (Python Edition) \_V3.3.0\_EN\_20260205.pdf, PDF p. 9](../source-library/); [Industrial API Manual (C\&C++ Edition) \_V3.3.0\_EN\_20260605.pdf, PDF p. 10](../source-library/).

## Units, dimensions and return values

| Item                            | Rule                                                                                                       |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Diana / Thor joint count        | JOINT\_NUM = 7 / 6; TCP pose remains six components                                                        |
| External C/C++ and Python units | m, rad, s, N, N·m, A; function-specific exceptions must be checked                                         |
| Pose convention                 | Axis-angle / rotation vector unless a particular function states otherwise; do not substitute Euler angles |
| Python init/read calls          | Boolean True success / False failure in the supplied wrapper                                               |
| C/C++ init/read calls           | Generally 0 success / -1 failure; use the exact declaration                                                |
| Pendant Lua                     | Separate API using mm, ms and degrees                                                                      |

The C/C++ June edition includes `initSrvV2` with a warning callback; do not infer that every binding or earlier wrapper exposes it. Retain callback objects/lifetimes and avoid blocking callback threads. Source: [Industrial API Manual (C\&C++ Edition) \_V3.3.0\_EN\_20260605.pdf, PDF pp. 10–15](../source-library/); [Industrial API Manual (Python Edition) \_V3.3.0\_EN\_20260205.pdf, PDF pp. 9–11, 26–28](../source-library/).

## State-only Python example

Prerequisites: commissioned robot, responsible operator, clear workspace, accepted stops and matched SDK, isolated wired controller port A, actual controller address and model joint count. Do not add brake release, error-recovery loops or motion calls to make the read succeed. Run from the delivered SDK environment where `DianaApi` and its native dependency are correctly installed.

Save this source-reviewed example as `read_state.py`; substitute the actual address and explicitly select seven joints for Diana or six for Thor:

{% code collapsedlinecount="10" %}
```python
import argparse
import DianaApi

parser = argparse.ArgumentParser()
parser.add_argument("--ip", required=True)
parser.add_argument("--joints", required=True, type=int, choices=(6, 7))
args = parser.parse_args()

if not DianaApi.initSrv((args.ip, 0, 0, 0, 0, 0)):
    raise RuntimeError("SDK initialization failed; inspect version/network errors")
try:
    if not DianaApi.getLinkState(args.ip):
        raise RuntimeError("Controller link is not normal")
    q = [0.0] * args.joints
    if not DianaApi.getJointPos(q, args.ip):
        raise RuntimeError("Joint-state read failed")
    print("Library version:", DianaApi.getLibraryVersion())
    print("Cached joint positions [rad]:", q)
finally:
    DianaApi.destroySrv(args.ip)
```
{% endcode %}

{% code collapsedlinecount="10" %}
```bash
python read_state.py --ip ACTUAL_CONTROLLER_ADDRESS --joints 7
```
{% endcode %}

For Thor, use `--joints 6`. The symbolic address is a placeholder for your verified endpoint, not a literal hostname. This example has been checked against the supplied signatures; it has not been connected to a robot or executed with the proprietary SDK.

**Expected result:** a normal link and library-version/joint-position result with the correct array size, without a motion command. Monitoring calls retrieve locally synchronized **cached** data after initialization; a successful getter or plausible zero values do not prove fresh live samples. Verify update timing/freshness with the delivery's state mechanism and compare to the pendant before recording data as current. Sources: [Industrial API Manual (Python Edition) \_V3.3.0\_EN\_20260205.pdf, PDF pp. 9–11, 26–28, 30–33](../source-library/).

## C/C++ implementation route

Use `DianaAPIDef.h`, `initSrvNetInfo` to initialize `srv_net_st`, set the actual server IP, then `initSrv` or the supported `initSrvV2`, check return codes, inspect `getJointPos` and release resources with `destroySrv`. Allocate `JOINT_NUM` from the actual model/build; do not hard-code seven for Thor or confuse a six-element TCP pose with a six-axis joint vector. Build flags/library names must come from the delivered SDK, so no unverified compiler/linker command is supplied. Sources: [Industrial API Manual (C\&C++ Edition) \_V3.3.0\_EN\_20260605.pdf, PDF pp. 10–15, 31–32](../source-library/).

## Troubleshooting

Import/load failure: match wrapper architecture, native library and Python runtime. Version mismatch: reconcile SDK/controller rather than upgrading blindly. Wrong/unchanging data: inspect model count, link and update freshness; retain errors and do not print uninitialized buffers as a result. An API read failure never calls for disabling collision detection or auto-resuming after a stop. See [fault evidence](troubleshooting.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                                    | Coverage      |
| -------------------------------------------------------------------------------------------------------------------------- | ------------- |
| [Industrial C/C++ API manual V3.3.0](../source-library/complete-industrial-api-manual-c-c-edition-v3-3-0-en-20260605/)     | 190 PDF pages |
| [Industrial Python API manual V3.3.0](../source-library/complete-industrial-api-manual-python-edition-v3-3-0-en-20260205/) | 165 PDF pages |

### Complete API contract selection

Both language manuals are retained in full, including every signature, parameter, array, return value, callback, example and appendix. Their complete function indexes link to original PDF pages. The C/C++ edition is dated 2026-06-05; the Python edition is dated 2026-02-05. Shared version labels do not prove that every later C/C++ function exists in the delivered Python package.

Before a client connects, record the exact SDK package/release, license, OS/architecture, controller software and robot model. Initialization and network settings must match that delivery. The external API is distinct from pendant Python and Lua; preserve each function's type, SI/unit convention, joint count and pose representation. A six-axis Thor and a seven-axis Diana do not share a universal joint vector.

| API area                  | Integration requirement                                                                                                 |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Initialization / lifetime | Check the actual initialization signature, connection result, error callback and cleanup contract                       |
| State / diagnosis         | Check return status before consuming arrays; retain sample time, joint order and raw error information                  |
| Kinematics / frames       | Preserve transforms, reference joints, pose convention and units; multiple inverse solutions need an explicit selection |
| Motion / servo / force    | Establish mode, authority, payload, limits, update timing, stop and stale-command behavior before use                   |
| I/O / communications      | Separate queries from writes and process-equipment actuation; confirm mapping, types and timeout behavior               |
| Persistent configuration  | Save/restore, calibration and parameter writes are changes to the robot configuration, not passive discovery            |

The first client result should remain a documented identity/state read with verified return values and no enable, reset, motion or output write. Preserve the difference between successful transport, API return status and actual device state. A built client, a returned zero code or a displayed pose is not evidence of an executed trajectory or a validated stop behavior.

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
