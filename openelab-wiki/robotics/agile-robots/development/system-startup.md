# Agile Robots training 1: startup and first connection

{% hint style="info" %}
Scope: matched Diana/Thor arm and controller, not Franka FR3 or a whole humanoid. First result: identify the commissioned system without commanding motion.
{% endhint %}

## Prepare the matched system

Match arm and controller serials, controller suffix, cable, pendant and tool against the delivery list. Mount on the correct foundation and use the model drawing: Thor 3 uses four M6 base screws, Diana 3/7 and Thor 7/12 use four M8, and Thor 20 uses six M10. Tool screws and base screws are different selections. Have the integrator verify grounding, stop/enabling-device functions, tool retention/load, mounting/gravity direction and the complete work envelope before power-on.

Use [CB-FS: 110–240 V AC](../cb-fs-controller.md) or [RCB: 200–240 V AC](../rcb-controller.md) according to the actual cabinet. The training slide's blanket 110–220 V statement and “30% ensures safe operation” are not universal mains or safety criteria. No arbitrary percentage establishes a safe commissioning speed. Source: [EN\_1\_System\_Startup.pptx, slides 3–4, 9](../source-library.md); exact arm/controller manuals in [the source library](../source-library.md).

## Choose the UI connection

| Route                  | Setting / scope                                                                                            |
| ---------------------- | ---------------------------------------------------------------------------------------------------------- |
| Physical TP3.1 pendant | Approved dedicated pendant connector; documented remote endpoint 192.168.1.75:6050                         |
| PC soft pendant        | Controller Ethernet A; factory endpoint 192.168.10.75:6050                                                 |
| PC adapter example     | 192.168.10.136 / 255.255.255.0, only if unused on the isolated controller subnet                           |
| Other network values   | Use the delivered configuration if changed; do not select .0, .255, .75 or an occupied address in that /24 |

The training's “0–255 except 75” address shorthand includes network/broadcast addresses; it is not a valid host-selection rule. Source: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 190–191](../source-library.md); [EN\_5\_Data\_backup\_and\_software\_updates.pptx, slide 3](../source-library.md).

## First UI result

1. Connect only the approved cables with power isolated; keep the workspace clear and the emergency stop accessible. Have the responsible operator perform the delivery-specific controller startup.
2. Let initialization finish. A temporary connection error during startup is not a reason to repeatedly reset or enable the robot. Observe status and logs.
3. Open the supplied pendant application and use the assigned account. Inspect **Startup** and **About**: model, serial/version information, joint count, tool, supply/status and any fault.
4. Distinguish cabinet/UI power, switched arm 48 V supply and brake release. In CB-style UI the Power On/Off and Start/Stop buttons control different states. Keep them inactive for this identification checkpoint unless a qualified commissioning step explicitly requires otherwise.
5. Record the exact system/software and reported status. Do not click Home, Free Drive, jog, run a project or toggle I/O as a connectivity test.

**Expected result:** the correct model/controller and current state are visible, without commanded motion. Successful login or ping does not validate the integrated safety chain. Source: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 11–13](../source-library.md); [EN\_1\_System\_Startup.pptx, slides 3–4, 17](../source-library.md).

## Troubleshooting and shutdown

For a PC connection failure, check port A, cable/link, unique host address/subnet and route/VPN interference. Use [the fault-isolation checklist](troubleshooting.md) before changing any robot configuration. The manual's three-position enabling switch and mode key have specific functions; releasing or fully squeezing the enabling device differs from deliberate middle-position enablement.

Use the installed UI's system-shutdown procedure after tasks stop and the load/workspace are secured. A forced power cut or generic packaging pose is not the default shutdown/recovery method. See [backup and update planning](backup-updates.md) before software changes.

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
