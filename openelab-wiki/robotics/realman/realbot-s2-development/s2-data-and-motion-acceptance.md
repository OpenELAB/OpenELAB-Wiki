# S2 tutorial: data acceptance and motion boundaries

{% hint style="info" %}
**Scope:** validate delivered recordings and plan staged S2 acceptance using V1.3. This page contains no executable non-zero motion command. A project-approved control appendix and on-site safety checks are prerequisites to motion.
{% endhint %}

## Validate a closed recording

Use a project-exported MCAP file after the recorder confirms closure. Do not move/compress a live recording or infer internal START/STOP/upload service formats from the ROS graph.

{% code collapsedlinecount="10" %}
```bash
ros2 bag info "/path/to/closed-recording.mcap"
```
{% endcode %}

Replace the path with an actual closed exported file. Confirm an MCAP storage reader is installed in the delivered host environment. Check readable metadata, plausible duration, nonzero per-topic counts, every task-required topic, expected count/rate relationship and continuous timestamps. Inspect sample content and camera decoding; counts alone cannot establish valid data.

Preserve task ID, robot version, hardware profile, scene and checksum. Keep the original until backup/upload verification completes. Treat local recording, upload completion and cloud parsing as separate results. Obtain the delivery's recorder contract, state machine, topic allowlist, quotas and error codes before implementing recording control. Source: [S2 interface V1.3, PDF pp. 53–57 \[S2\_API\]](../realman-source-library/).

**Expected result:** a readable closed artifact with the required topics and verified sample content, plus a traceable acceptance record. No recording or upload has been performed by this documentation task.

## Separate chassis ratings from control limits

The S2 user manual's travel-speed range is a product specification. V1.3's `/cmd_vel` table defines a different **input contract**: `linear.x/y` in m/s and `angular.z` in rad/s, with other Twist components zero. The table permits individual linear components up to ±0.8 m/s and angular.z up to ±1.2 rad/s, but these are not first-test values or simultaneously achievable full-body velocities. Direction follows the documented body frame: +X forward, +Y left, +Z up and positive yaw counterclockwise viewed from above.

The interface recommends 20 Hz publication and declares a 1.0 s command timeout. The timeout begins the zero-target stop process; it does not guarantee a physical stop within one second. Manual channels have higher priority and a 0.5 s hold after takeover ends. Do not compete by increasing publication rate. Source: [S2 interface V1.3, PDF pp. 38–43 \[S2\_API\]](../realman-source-library/).

## Collision and emergency-stop recovery

`/chassis/collision` is event-triggered and does not publish a periodic false-clear state. Receiving true must latch a client-side hold and stop all nonzero command sources. A subsequent command can clear the driver's internal collision-stop flag, so even a zero command is part of a controlled recovery sequence rather than evidence that the hazard has disappeared.

Have on-site personnel inspect people/obstacles, structure, payload, cables and floor. Verify current motor status and diagnostics; ensure teleoperation/keyboard sources are stopped. Follow the delivery's recovery authorization before zero-stream checks, clearing the client latch or a new bounded movement. Never automatically replay pre-collision, pre-emergency-stop or pre-disconnection targets. Software stop, timeout, collision response and physical emergency stop are distinct. Source: [S2 interface V1.3, PDF pp. 38–42, 58–60 \[S2\_API\]](../realman-source-library/).

## Plan the first authorized movement

Before any nonzero command, complete training, rigid/secure installation and the target machine's direction/limit/stop/authority checks. Use two trained people: one issues commands, the other remains at the hardware emergency stop; both stay outside the motion/pinch envelope. Prepare the matching stop command in a separate terminal and verify safe behavior on process exit, lost feedback and control-source takeover. Allow clearance in both intended and opposite directions.

V1.3 initial-direction ceilings are deliberately small and apply one degree of freedom at a time: chassis ≤0.05 m/s or ≤0.05 rad/s for ≤0.5 s; arm first checks use one joint, `v=1`, ≤500 millidegrees (0.5°) change while all other targets equal freshly read current joint positions. These are **ceilings for a controlled verification**, not a general safe-motion guarantee. Head/body checks require the exact joint mapping and limits from the S2 delivery. Stop and check feedback after every step; do not test multiple subsystems together initially.

For `/robot/command`, device 0/1 route left/right arms, 2 body and 3 head. Body/head require the matching nested `payload.device`; arm joint arrays contain seven absolute targets. Integer command units are **millidegrees**, as shown by `round(rad × 180 / π × 1000)`, despite the translation's “milliradians” wording. A zero target means absolute zero, not hold-current-position. Validate the complete V1.3 §8.3 schema, response semantics, finite values, ranges and matched source before any control implementation.

If direction, displacement, speed or joint mapping differs from expectation, stop immediately. Do not reverse signs or increase amplitude to trial-and-error the mapping. Following a collision, tip, impact, unusual noise or damage, keep the system stopped until mechanical/electrical/safety inspection is complete. Source: [S2 interface V1.3, PDF pp. 24–35, 48–50, 58–60 \[S2\_API\]](../realman-source-library/).

## Regression and issue evidence

After software changes, repeat version/SDK, publisher/type/QoS, units, freshness, optional-interface behavior and safe-failure checks before restoring control. Capture expected versus observed behavior, command/response IDs, time zone, target topic contract and redacted diagnostics. Do not log credentials, full business payloads or signed URLs. Customer applications must be independently disableable and recoverable without modifying robot base services.

## Sources and validation

[S2 Interface V1.3 \[S2\_API\]](../realman-source-library/), §§8–17. Reviewed 22 November 2026. MCAP parsing, stop tests, motion and hardware validation: **not run**. This guide records source requirements and staged acceptance boundaries, not a completed commissioning certificate.

## Complete interface contract and acceptance details

[RealBot2.0 / S2 interface manual V1.3 — all 70 PDF pages](../realman-source-library/complete-s2-interface-manual.md). For the full interface map, see the [S2 development guide](./).

### QoS, readiness and camera/recording acceptance

Readiness includes an expected endpoint, matching installed type, compatible QoS, data within an agreed timeout, valid content, continuous timestamps where applicable, and the required operating authority. Query the chassis lifecycle state read-only; do not automatically configure/activate production nodes, restart core services or change parameters as a discovery step.

Arm high-frequency topics use SensorDataQoS (Keep Last 5, Best Effort, Volatile) and a documented nominal 5 ms / 200 Hz publication interval. Those figures are not a hard real-time guarantee. Measure received rate and gaps and keep callbacks light. For cameras, record topic/type, encoding, calibration/resolution, rate, timestamp and a decoded sample. An encoded H.26x payload needs a matching decoder before a pixel-processing path such as `cv_bridge`.

For a data session, save the robot/profile/scene/SDK versions, exact interface definitions, source/read timestamps, QoS, frame IDs, units, named channel order and a bounded recording. Check that the MCAP opens, contains the intended channels, spans the intended interval, has valid sample content and can be decoded. A file on disk or an upload-complete indication alone does not establish an acceptable training dataset. Recording, upload and remote-operation control APIs remain project-specific unless explicitly delivered.

### Command, collision and recovery boundaries

The JSON routing uses left arm `device=0`, right arm `device=1`, waist `device=2` and head `device=3`. The waist/head contract repeats the device in the payload; the arm payload does not require that extra field. Exact schemas, all fields, response classifications and source examples are retained in full in the source reader. Preserve the difference between a completed ROS service exchange, a parsed business response and observed completion in the correct state source.

The chassis gives manual/teleoperation channels higher priority than `/cmd_vel`; a client must yield rather than raise its rate to compete. The source recommends continuous 20 Hz client publication and describes a 1.0 s command-expiry condition, but expiry is not a guaranteed 1.0 s physical stopping time or a specified braking distance. The client must deliberately stop its own non-zero target generation on task end or failure.

Latch collision events in the client. The source states that a new velocity message can clear an internal collision-stop flag, including a zero message; this does not establish that the physical hazard has been removed. There is no `false` collision message to wait for. Recovery requires an on-site inspection, valid diagnostics and continuously updated motor state, stopped competing sources and an explicitly authorized recovery sequence. Do not replay a cached pre-stop target after a collision, physical emergency stop or network restoration. The complete stopping, low-speed direction-verification and recovery procedures remain in the cited V1.3 pages; this entry remains a read-only first-result guide.
