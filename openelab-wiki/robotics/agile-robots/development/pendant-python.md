# Pendant Python: context scripts and a no-motion first result

{% hint style="info" %}
Scope: Python scripts inside the supplied pendant project, not the external DianaApi host wrapper. First result: one finite log message in a controlled empty project.
{% endhint %}

## Separate the Python interfaces

Training examples such as `log(context, level, message)` run inside the pendant's embedded project environment. The external Industrial SDK uses `DianaApi.initSrv(...)` and separate host/native dependencies. Do not copy `context` calls into a standalone SDK script or replace a pendant function with a similar external API name.

The training's soft-pendant environment describes an Ubuntu/Qt 5.12.6 gcc\_64 package or a Windows x64 package with the VC++ 2017 runtime. These are supplied-package prerequisites, not proof that every modern host/package is interchangeable. Obtain the correct delivered UI bundle; no unverified download or installation command is asserted. Source: [EN\_4\_Interfaces\_and\_Programming.pptx, slides 3–9](../source-library.md).

## First finite log result

1. On a commissioned test system with no active production task, create an empty test project through the installed pendant's documented project-management flow. Save/export the current project first; changing the active project is a deliberate operational change.
2. Add a Python script instruction in that empty project. Use the scripting editor/environment supplied by that pendant version.
3. Enter only this source-grounded line:

{% code collapsedlinecount="10" %}
```python
log(context, 1, "Agile pendant Python: log-only check")
```
{% endcode %}

4. Inspect the entire project tree and any startup/background instructions. It must contain no move, Free Drive, brake, I/O, socket or peripheral command. Program execution can still change operational state, so have the responsible operator authorize this isolated test under the installed procedure.
5. Observe the log and stop the finite test normally. Preserve the log plus project/software identity; do not append a training motion example merely because logging works.

**Expected result:** the message appears once without an arm/peripheral actuation command. This is a proposed, source-reviewed check; it was **not run** during wiki authoring. Source: [EN\_4\_Interfaces\_and\_Programming.pptx, slides 4–9](../source-library.md); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 9–10, 121–124](../source-library.md).

## Common mistakes

Curly quotes, broken indentation and inconsistent variable names in slide text are not executable Python. Infinite background logging loops obscure termination/pause behavior and are unnecessary for a first result. A script that contains only reads can still be embedded in a project with motion elsewhere; inspect the entire project.

Use [external Industrial API state inspection](industrial-api.md) for host SDK work, [Lua](pendant-lua.md) for the separate Lua command interface, and [interface selection](interfaces-network.md) before adding external communications. The training's placeholder socket/serial examples do not establish a production device protocol.

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
