# Agile Robots training 3: coordinates, payload and tools

{% hint style="info" %}
Scope: supplied Diana/Thor training and Industrial pendant V3.3. First result: an audited frame/tool/load record. Calibration and payload identification require supervised motion and are not run here.
{% endhint %}

## Separate the frames and units

Base, flange, tool center point (TCP) and workpiece frames have different origins and transformations. The default tool may coincide with the flange; that is not the position of an installed gripper's finger tip. Workpiece one-point definition changes origin while retaining base orientation; three-point methods define origin, positive X and XY-plane direction. Use right-handed frames and record transform direction.

C/C++ and external Python APIs use meters/radians/seconds; pendant Lua uses millimeters/degrees/milliseconds. API Cartesian orientation is an axis-angle/rotation-vector convention unless a function explicitly converts it; do not insert Euler/RPY angles by visual similarity. Sources: [EN\_3\_Definition\_Coordinate\_Systems \_and\_Connection\_Endeffector.pptx, slides 4–17](../source-library.md); [Industrial Lua Programming Manual\_V3.3.0\_EN\_20260117.pdf, PDF p. 4](../source-library.md); [Industrial API Manual (Python Edition) \_V3.3.0\_EN\_20260205.pdf, PDF p. 9](../source-library.md).

## Inspect before calibrating

1. Open **System Settings → Coordinate** and inspect the existing tool/workpiece definitions without applying changes. Record names, offsets, orientation convention and units.
2. Inventory tool, adapter, cable and workpiece mass; obtain measured/manufacturer center of mass and the six inertia components in the correct frame. Tool payload is not just the handled object.
3. Compare the selected installation/gravity direction and application geometry with the mechanical drawings. Keep ordinary tool parameters and separately configured safety tool envelopes coherent.
4. Record a versioned frame/load table and obtain review before any recalibration or motion.

**Expected result:** a traceable frame and payload record with no guessed transform, inertia or powered tool setting. Source: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 154–160](../source-library.md); [EN\_3\_Definition\_Coordinate\_Systems \_and\_Connection\_Endeffector.pptx, slides 4–13](../source-library.md).

## Calibration methods and motion boundaries

The four-point **Position Definition** method returns the TCP to one fixed point from four different poses and calculates position offset. **Direction Definition** uses origin, X-direction and an XY-plane point to establish orientation. Buttons such as **Move to Point** command movement. Payload Identification also executes a trajectory; default waypoints can collide with an attached tool or fixture. Review the entire path, load and stopping envelope before a trained operator conducts that separate procedure. A successful numerical calculation is not independent proof of calibration accuracy.

Workpiece one-point and three-point methods are defined in the source training. Do not change a frame already referenced by an active project/safety zone without controlled revalidation. Sources: [EN\_3\_Definition\_Coordinate\_Systems \_and\_Connection\_Endeffector.pptx, slides 6–17](../source-library.md); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 154–160](../source-library.md).

## Tool and gripper integration

Training slides 19–23 show an example **3F15G/quick changer/Compute Box** arrangement, with separate 24 V power, configurable NPN/PNP I/O and a Compute Box browser interface. It is not a general Agile Hand, Franka Hand or all-grippers installation. The example IP `192.168.1.1` belongs to that peripheral example; it is not the robot controller's UI address. A saved peripheral program may automatically resume on its next power-on.

Use the actual robot flange drawing: Thor 20 has six M6 tool holes, while the training's generic four-screw quick-changer example is not its universal mounting instruction. Diana 3 and Thor tool M8 eight-pin connectors have different pin assignments. A repeated RS485 polarity-description typo in Thor tables remains unresolved; obtain the confirmed wiring before connection.

## Troubleshooting

Incorrect guidance forces/drift: stop and inspect load, inertia, gravity and TCP configuration. Offset motion: verify transform direction and units before recalibration. Gripper not recognized: inspect its separate power/communication/auto-start behavior with motion disabled; do not toggle unknown outputs. See [Agile Hand](../agile-hand.md) and the [separate Franka Hand guide](../../franka/franka-hand.md).

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
