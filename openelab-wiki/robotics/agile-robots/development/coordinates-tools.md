# Agile Robots training 3: coordinates, payload and tools

{% hint style="info" %}
Scope: supplied Diana/Thor training and Industrial pendant V3.3. First result: an audited frame/tool/load record. Calibration and payload identification require supervised motion and are not run here.
{% endhint %}

## Separate the frames and units

Base, flange, tool center point (TCP) and workpiece frames have different origins and transformations. The default tool may coincide with the flange; that is not the position of an installed gripper's finger tip. Workpiece one-point definition changes origin while retaining base orientation; three-point methods define origin, positive X and XY-plane direction. Use right-handed frames and record transform direction.

C/C++ and external Python APIs use meters/radians/seconds; pendant Lua uses millimeters/degrees/milliseconds. API Cartesian orientation is an axis-angle/rotation-vector convention unless a function explicitly converts it; do not insert Euler/RPY angles by visual similarity. Sources: [EN\_3\_Definition\_Coordinate\_Systems \_and\_Connection\_Endeffector.pptx, slides 4–17](../source-library/); [Industrial Lua Programming Manual\_V3.3.0\_EN\_20260117.pdf, PDF p. 4](../source-library/); [Industrial API Manual (Python Edition) \_V3.3.0\_EN\_20260205.pdf, PDF p. 9](../source-library/).

## Inspect before calibrating

1. Open **System Settings → Coordinate** and inspect the existing tool/workpiece definitions without applying changes. Record names, offsets, orientation convention and units.
2. Inventory tool, adapter, cable and workpiece mass; obtain measured/manufacturer center of mass and the six inertia components in the correct frame. Tool payload is not just the handled object.
3. Compare the selected installation/gravity direction and application geometry with the mechanical drawings. Keep ordinary tool parameters and separately configured safety tool envelopes coherent.
4. Record a versioned frame/load table and obtain review before any recalibration or motion.

**Expected result:** a traceable frame and payload record with no guessed transform, inertia or powered tool setting. Source: [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 154–160](../source-library/); [EN\_3\_Definition\_Coordinate\_Systems \_and\_Connection\_Endeffector.pptx, slides 4–13](../source-library/).

## Calibration methods and motion boundaries

The four-point **Position Definition** method returns the TCP to one fixed point from four different poses and calculates position offset. **Direction Definition** uses origin, X-direction and an XY-plane point to establish orientation. Buttons such as **Move to Point** command movement. Payload Identification also executes a trajectory; default waypoints can collide with an attached tool or fixture. Review the entire path, load and stopping envelope before a trained operator conducts that separate procedure. A successful numerical calculation is not independent proof of calibration accuracy.

Workpiece one-point and three-point methods are defined in the source training. Do not change a frame already referenced by an active project/safety zone without controlled revalidation. Sources: [EN\_3\_Definition\_Coordinate\_Systems \_and\_Connection\_Endeffector.pptx, slides 6–17](../source-library/); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 154–160](../source-library/).

## Tool and gripper integration

Training slides 19–23 show an example **3F15G/quick changer/Compute Box** arrangement, with separate 24 V power, configurable NPN/PNP I/O and a Compute Box browser interface. It is not a general Agile Hand, Franka Hand or all-grippers installation. The example IP `192.168.1.1` belongs to that peripheral example; it is not the robot controller's UI address. A saved peripheral program may automatically resume on its next power-on.

Use the actual robot flange drawing: Thor 20 has six M6 tool holes, while the training's generic four-screw quick-changer example is not its universal mounting instruction. Diana 3 and Thor tool M8 eight-pin connectors have different pin assignments. A repeated RS485 polarity-description typo in Thor tables remains unresolved; obtain the confirmed wiring before connection.

## Troubleshooting

Incorrect guidance forces/drift: stop and inspect load, inertia, gravity and TCP configuration. Offset motion: verify transform direction and units before recalibration. Gripper not recognized: inspect its separate power/communication/auto-start behavior with motion disabled; do not toggle unknown outputs. See [Agile Hand](../agile-hand.md) and the [separate Franka Hand guide](../../franka/franka-hand.md).

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                                                                | Coverage  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | --------- |
| [Agile Robots training 3 — Coordinates and End Effectors](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md) | 24 slides |

### TCP and workpiece methods

The twenty-four slides preserve tool selection, direct offset entry, four-position TCP calibration, direction definition, payload/inertia configuration, workpiece calibration and the gripper/Compute Box example. The original coordinate-frame animation from slides 7 and 9 is linked in the complete reader.

The TCP position procedure observes the same fixed point from four arm poses; direction definition separately establishes an origin, positive-X direction and XY plane. A computed position offset is not a verified orientation. The workpiece one-point method changes the origin while keeping the base orientation; three-point and extended three-point methods also establish axis directions. Record the actual transforms and validate their intended direction before executing a task.

Payload configuration includes mass, center of mass and the six independent inertia terms. Preserve their reference frame and units. Payload identification and “Move to Waypoint” execute motion; default identification poses may collide with an attached tool, so the actual swept path and fixtures must be reviewed first.

The gripper section shows a 3F15G component overview and a separate RG2-style software example. Those labels do not establish one interchangeable product. Verify the delivered gripper, quick changer, 24 V supply, NPN/PNP switches and I/O mapping. The shown Compute Box program can resume after power restoration; review and isolate that behavior before energizing the peripheral.

### Source chapter map

| Source section                        | Full detail                                                                                                      |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Advanced Training                     | [Slide 1](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-1)   |
| Advanced Training (2)                 | [Slide 2](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-2)   |
| Definition of Coordinate Systems      | [Slide 3](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-3)   |
| Slide 4                               | [Slide 4](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-4)   |
| Slide 5                               | [Slide 5](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-5)   |
| Definition of Coordinate Systems (2)  | [Slide 6](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-6)   |
| Definition of Coordinate Systems (3)  | [Slide 7](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-7)   |
| Slide 8                               | [Slide 8](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-8)   |
| Definition of Coordinate Systems (4)  | [Slide 9](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-9)   |
| Definition of Coordinate Systems (5)  | [Slide 10](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-10) |
| Definition of Coordinate Systems (6)  | [Slide 11](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-11) |
| Definition of Coordinate Systems (7)  | [Slide 12](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-12) |
| 2.2 Payload Identification            | [Slide 13](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-13) |
| Definition of Coordinate Systems (8)  | [Slide 14](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-14) |
| Definition of Coordinate Systems (9)  | [Slide 15](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-15) |
| Definition of Coordinate Systems (10) | [Slide 16](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-16) |
| Definition of Coordinate Systems (11) | [Slide 17](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-17) |
| Connection Endeffector (Gripper)      | [Slide 18](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-18) |
| Connection Endeffector (Gripper) (2)  | [Slide 19](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-19) |
| Connection Endeffector (Gripper) (3)  | [Slide 20](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-20) |
| Connection Endeffector (Gripper) (4)  | [Slide 21](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-21) |
| Connection Endeffector (Gripper) (5)  | [Slide 22](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-22) |
| Connection Endeffector (Gripper) (6)  | [Slide 23](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-23) |
| Slide 24                              | [Slide 24](../source-library/complete-en-3-definition-coordinate-systems-and-connection-endeffector.md#slide-24) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
