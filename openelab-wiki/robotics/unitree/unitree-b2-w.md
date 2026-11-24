---
description: >-
  Review the distinct B2-W wheel-leg map, English manual revisions, charging and
  stop boundaries, SDK2 control hazards and an offline wheel-aware state
  checkpoint.
---

# Unitree B2-W: wheel mapping, operating limits and first state checks

{% hint style="info" %}
**Manufacturer model reference: Unitree B2-W.** No exact B2-W OpenELAB listing or SKU was verified in the observed catalog. **SKU:** unverified · **Store URL:** unverified. This is a separate wheel-legged model reference, not additional coverage claimed by the listed [B2](unitree-b2.md). [Official Unitree B2-W product page](https://www.unitree.com/b2-w/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree B2-W combines twelve leg joints with four wheel joints in a wheel-legged industrial platform. The wheels change its state map, commands, contact geometry, stopping behavior and maintenance requirements. This guide uses the B2-W User Manual V1.1 and B2-W Remote Control Manual V1.0, together with B2-W-specific SDK2 examples. B2 battery instructions and B2 remote mode tables are not silently substituted for B2-W documentation. [B2-W manufacturer description](https://www.unitree.com/b2-w/), [B2-W joint constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2w/low_level/unitree_legged_const.py)

The source supports a GO-family state interface, but not a validated firmware range or a complete stop/charging specification for a delivered unit. The first result below is a wheel-aware offline mock, with no robot, SDK, ROS or DDS activation. The [B2](unitree-b2.md), [B2-Ex](unitree-b2-ex.md) and [B1](unitree-b1.md) references retain their own scopes.

### Portal evidence added without changing model identity <a href="#portal-evidence-added-without-changing-model-identity" id="portal-evidence-added-without-changing-model-identity"></a>

This edition preserves the published manuals, model identity and offline example, and adds the actual saved 35-article B2 developer corpus. The source index below distinguishes direct model material, related wheel/legged content, copied interface descriptions and optional modules. A source-specific service/API version is not a universal robot firmware range.

## Applications <a href="#applications" id="applications"></a>

B2-W's manufacturer describes wheel-leg travel over industrial terrain, stairs and uneven surfaces, and inspection payload integration. Its quoted range targets do not establish the endurance of a particular sensor payload, slope, tire condition or mission. Select and validate rolling versus stepping operation against the actual controller, traction and site conditions before route planning.

A useful initial development task is identifying the four wheel-state slots separately from leg angles. Another is recording the delivered computers, perception stack and interface module against the order. Neither task requires releasing control mode or issuing a wheel-speed command. Standard B2-W has no B2-Ex certification implication. [B2-W product functions and conditions](https://www.unitree.com/b2-w/)

### Development and deployment boundaries <a href="#development-and-deployment-boundaries" id="development-and-deployment-boundaries"></a>

Treat state observation, media capture, map editing and movement as separate capabilities with separate ownership. A research navigation example or a working offline parser does not establish an industrial autonomous mission, certified stop, payload retention or environmental clearance. Optional computers, radios, cameras and docks require their exact model/edition and power/network budgets. The first result remains the original offline program below.

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                  | B2-W source value and conditions                                                                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Standing / prone size      | Approximately 1098 × 550 × 758 mm / 950 × 550 × 450 mm, length × width × height.                                                                                                                 |
| Mass                       | Approximately 85 kg including battery. Do not use B2's 60 kg handling assumption.                                                                                                                |
| Payload                    | Product page: standing 120 kg, walking >40 kg. Payload position, restraint and configured mode remain per-unit engineering inputs.                                                               |
| Battery description        | Product page: >2 kWh, 58 V; User Manual V1.1 describes up to 45000 mAh. No B2-W-specific rated/maximum cell-voltage or charger-output table was established here.                                |
| Endurance                  | Approximately 30 km unloaded and maximum 25 km with 40 kg load. The product-page footnote qualifies the loaded-range/speed figures as special configurations; real speed limits apply.           |
| Travel speed               | Advertised maximum 15 km/h, configuration-limited in practice. This is not a commissioning or first-check speed.                                                                                 |
| Wheels                     | Product page: diameter 225 mm, maximum wheel angular speed 50 rad/s, maximum wheel torque 40 N·m. The two maxima are not a simultaneous continuous-duty rating or a tire-pressure specification. |
| Terrain capability         | Product page: continuous 20–25 cm stairs, 40 cm forward step capability and >45° slope. Manual operating guidance is materially more restrictive; see below.                                     |
| Body environment / ingress | −20 to +55 °C; IP67 advertised. Do not operate in lightning/tornado conditions; dry mating surfaces and the correct installed battery matter. No independent test report was read.               |
| Compute                    | Product page: Core i5 platform computer, Core i7 user-development computer; optional i7/Orin NX arrangements up to three devices, configuration-dependent.                                       |
| Expansion                  | User Manual lists Ethernet ×4, USB 3.0 ×4, 12 V ×4, 5 V ×1, 24 V ×4 and BAT ×1. Connector assignment, direction and allowed current require the exact interface module specification.            |

Sources: [official parameter table and footnotes](https://www.unitree.com/b2-w/), [B2-W User Manual V1.1, source images 6–12 and 20–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html).

### Keep the operating envelope separate <a href="#keep-the-operating-envelope-separate" id="keep-the-operating-envelope-separate"></a>

User Manual V1.1 directs ordinary operation on open, flat ground with steps **below 20 cm** and slopes **below 20°**, unlike the product-page maximum demonstrations. Its precautions state obstacle crossing ≤20 cm and say not to cross obstacles higher than 25 cm. They also warn about lateral drift near/above 45° and instability when turning on steep slopes. None of these passages validates a route at the product-page maxima. Use the delivered firmware's approved mode-specific envelope and reduce speed for uneven ground. [User Manual, source images 12 and 20–21](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

The manual requires at least 3 m separation from obstacles/crowds/water in its operating-environment section. For stand-up recovery, its earlier safety text says a 2 m diameter, later precautions say a 3 m diameter, while the separate remote manual states a **3 m radius**. These are conflicting published clearances, not a single consistent specification. Recovery is excluded from this first-result workflow; confirm a definitive procedure, and do not shrink a radius requirement to a diameter. [User Manual, images 5, 12 and 20](https://marketing.unitree.com/article/en/B2-W/User_Manual.html), [Remote Manual, images 8–9 and 13–14](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Wheels, body, perception and interface identification <a href="#wheels-body-perception-and-interface-identification" id="wheels-body-perception-and-interface-identification"></a>

Use the original B2-W parts/wheel illustrations in [User Manual images 6–7](https://marketing.unitree.com/article/en/B2-W/User_Manual.html), and the [B2-W interface-module drawing, source image 9](https://doc-cdn.unitree.com/static/2025/7/29/e974f27f40ee4032a099788d712bd8dc_2482x3509.png). The drawing has wheel-motor/leg-bus labels and an emergency-stop label, but it is not a verified mating pinout or proof of stop coverage in every controller mode. Do not wire a homemade stop circuit from OCR text, expose internal RS-485 wiring or connect a load to BAT without the delivered electrical drawing.

Before a later commissioning session identify the tire assemblies, body/pack/charger labels, remote R3 or R1 revision, computer allocation and accessory interface module. Check tires for wear/damage and loose wheel components, plus cameras/LiDAR, cooling, fasteners and battery latch. The sources do not give a verified tire pressure, wheel-fastener torque or permitted rail-mount moment; obtain those before mechanically altering the platform. [User Manual, images 7, 9 and 22–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

### Power and charging boundary <a href="#power-and-charging-boundary" id="power-and-charging-boundary"></a>

B2-W's own user manual describes removing the switched-off battery for plug-in charging, matching the delivered charger's AC nameplate, connecting AC first and then the battery, and cooling a hot pack to room temperature before charging. The documented AC input example is 100–240 V, 50/60 Hz. This does **not** establish the charger's DC output or an interchangeable B2 battery/charger model. The separate B2 Battery Manual is not applied here as a B2-W electrical specification. [B2-W User Manual, image 10](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

The user manual requires correct keyed battery orientation and a fully latched installation; never force a pack into place. It describes a prone, horizontal startup posture with the belly support on flat ground, legs retracted and no limb trapped by the body. The power-button sequence is a short press then a hold over three seconds, followed by roughly two minutes before automatic standing. This is documented context for a commissioned operator, not an action to perform for the offline check. Automatic standing and wheeled contact create movement hazards even without an application command. [User Manual, images 13–14](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

### Remote, stop behavior and upkeep <a href="#remote-stop-behavior-and-upkeep" id="remote-stop-behavior-and-upkeep"></a>

B2-W's Remote Manual V1.0 covers R3 and older R1 hardware, with a December 2024 upgrade notice. R3's table lists 780 mAh, 5 V/700 mA and about 5 h; R1 lists 2500 mAh, 5 V/2 A and about 4.5 h. Both state >100 m only in open conditions. R3 charging guidance recommends a 5 V/2 A USB adapter; the documented R1/R3 full-charge LED indications differ, so use the correct hardware section. [Remote Manual, images 2–7 and 10–12](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)

For the delivered official controller, the B2-W table identifies L2 held + B clicked as damping, L2 held + A clicked as lock-standing/lying, Y as General Mode and L2/R2 held + START clicked as Special Mode. It also lists recovery and a special-configuration rotating-jump action. These mode/action entries differ from B2 Remote V2.1 and are **not** setup tests. The [original B2-W command table, image 8](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html) is the versioned source; verify actual firmware before relying on any button mapping.

The user manual says high-level API and remote commands can both act on the robot, and remote commands cease to work during low-level development. Damping/lying controls are not proof of an independent wheel brake or safety-rated stop. User shutdown guidance first brings the robot to a stable lying state, then uses the battery button; abrupt power loss while standing can collapse it. A failed remote requires a unit-specific recovery plan, not an improvised lifting/power-off maneuver. [User Manual, images 4 and 18–20](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

The app workflow uses Unitree Explore with a Unitree-supplied enterprise account, Bluetooth-assisted binding, and AP or Wi-Fi connection. R3 link indication is the right DL light; older R1 guidance describes the left transmission indicators. A link light is not proof that the correct control mode or independent stop is armed. Store the machine dry/cool, inspect tires and cooling, and clean only with power off and soft materials. The user manual says retain the installed pack during body cleaning, but remove it for long storage; do not treat that as permission to wet the loose pack. Joint calibration is not a routine troubleshooting step. [User Manual, images 15–17 and 19–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

### B2-W hardware applicability <a href="#b2-w-hardware-applicability" id="b2-w-hardware-applicability"></a>

The B2 hardware article includes a specifically labelled B2-W tire section, but most numbered power/pin tables describe B2. Use the existing B2-W manuals and matched delivered harness for electrical integration; the B2 shared10 A rails and numbered connector view must not be silently promoted to B2-W limits. The tire pressure entry“2.4” omits its unit, so no bar/psi target is inferred. [About B2](https://support.unitree.com/home/en/B2_developer/About%20B2).

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Exact source map, not a universal firmware pairing <a href="#exact-source-map-not-a-universal-firmware-pairing" id="exact-source-map-not-a-universal-firmware-pairing"></a>

The reviewed C++ SDK2 commit is `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; Python SDK2 is `814556d15970dd2ecf1c9984e845ca02ab07e206`. C++ sources report project 2.0.0, vendor Ubuntu 20.04/GCC 9.4.0 prebuild for aarch64/x86\_64 and C++17. Python setup declares package 1.0.1, Python ≥3.8 and CycloneDDS ==0.10.2 plus NumPy/OpenCV. These identify source/environment baselines, not the robot's image. [C++ baseline](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [Python requirements](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py)

B2-W-specific sources use `unitree_go` low state/command on DDS `rt/lowstate` / `rt/lowcmd`. Twenty slots are transport capacity. The Python constants define this exact map:

| Group                           | DDS indices in the inspected B2-W example                     |
| ------------------------------- | ------------------------------------------------------------- |
| Front right hip/thigh/calf      | 0, 1, 2                                                       |
| Front left hip/thigh/calf       | 3, 4, 5                                                       |
| Rear right hip/thigh/calf       | 6, 7, 8                                                       |
| Rear left hip/thigh/calf        | 9, 10, 11                                                     |
| Front right / front left wheels | 12 / 13                                                       |
| Rear right / rear left wheels   | 14 / 15                                                       |
| Remaining GO slots              | 16–19; no active B2-W actuator assignment is established here |

Source: [pinned B2-W `unitree_legged_const.py`](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2w/low_level/unitree_legged_const.py). This is the example's contract; it is not a joint-sign/zero/calibration certificate for a particular machine.

The [C++ B2-W stand example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2w/b2w_stand_example.cpp) releases the motion mode, creates a low-command publisher and later commands wheel slots 12–15 at positive and negative angular velocities. It initializes 0x01 motor mode; the inspected B2 legged example uses 0x0A. The Python counterpart also requests StandDown/ReleaseMode during initialization. None is a passive “read sensor” program, despite sensor-printing text. Do not reuse their gains, sentinels, mode byte, CRC assumptions or wheel commands for a first check.

The [B2-W sport client example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2w/b2w_sport_client.cpp) uses the B2 `SportClient` (`sport`, API 1.0.0.1). Move/StopMove/SwitchGait/RecoveryStand are control requests; its movement-duration comments do not prove a hardware stopping guarantee. Confirm firmware, gait/rolling mode, wheel sign, traction, braking and one command owner before any later control work.

See the shared [SDK2 state guide](unitree-sdk2-state-development.md) and [ROS 2 integration guide](unitree-ros2-integration.md) for environment-specific details. A future subscriber must use the matched GO type, actual dedicated Ethernet interface and confirmed robot domain (0 in the reviewed examples). Keep simulation on a separately matched domain/interface, such as domain 1/lo. No interface activation, build or simulator is needed below.

### Applicability of B2-family context <a href="#applicability-of-b2-family-context" id="applicability-of-b2-family-context"></a>

The following B2-family service descriptions provide context. The dedicated B2-W subsection and original B2-W manuals/source example control wheel-specific claims; no legged gait, supply rail, recovery result or navigation installation is transferred without exact support evidence.

### Portal descriptions and the pinned implementation <a href="#portal-descriptions-and-the-pinned-implementation" id="portal-descriptions-and-the-pinned-implementation"></a>

The source audit uses C++ SDK2 `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`, not a moving branch. At this pin, initialize the factory with domain and network-interface arguments only: `Init(domain, interface)`. The A2/As2 portal signature includes a third shared-memory argument, and the B2 article mentions it in prose despite its two-argument signature. That additional argument is not in the pinned header. Likewise, the portal's `GetServerApiVersion` reference return differs from the actual by-value `std::string`; `GetApiVersion` is a separate client-side version query. Do not construct a compile recipe by mixing those revisions. [pinned factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp); [pinned client](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/client/client.hpp).

The subscriber paragraph mistakenly mentions a send channel. The real subscriber creates a receive channel, associates a callback and can use a bounded queue; copy required values before callback storage is reused. A positive queue length can absorb work but cannot make stale data fresh or prevent overload indefinitely. `GetLastDataAvailableTime` describes local receipt timing, not device sensor time. Domain numbers, NIC selection and multicast configuration are transport choices, not authentication or isolation. [pinned subscriber](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp).

A successful RPC return only reports that request's result. It does not certify safe posture, fresh state or exclusive motor ownership. The documented common errors distinguish client-side request/API-registration/timeout/correlation/response-validation/lease failures (3102–3107) from server-side internal/unsupported/parameter/rejection/lease failures (3202–3207). Specifically, 3103 means the API is not registered locally, 3106 means invalid response data, and 3203 separately means the server has not implemented the API. Keep the service name, API version, request identity and error together. Do not repeatedly replay a timed-out movement request: the robot may have acted before the reply was lost. Publisher, mode release, service switch, calibration, docking and navigation requests remain active operations. No such operation is part of the first check in this page.

### B2 services, message direction and frames <a href="#b2-services-message-direction-and-frames" id="b2-services-message-direction-and-frames"></a>

B2 uses DDS publish/subscribe for continuous state and RPC for requests. Basic service collects motor, IMU, BMS and remote data and also accepts low-level commands; the architecture distinguishes normal sport, AI sport, multimedia, network and SLAM services. Bluetooth provisions App/network binding; WebRTC carries remote media/control, while MQTT/HTTP support cloud binding, fault and upgrade functions. Cloud connection and external remote control require the documented authorization; a LAN participant does not need or imply cloud commissioning. [SDK Concepts](https://support.unitree.com/home/en/B2_developer/SDK%20Concepts); [Architecture Description](https://support.unitree.com/home/en/B2_developer/Architecture%20Description); [Robot Dog Application](https://support.unitree.com/home/en/B2_developer/Robot%20Dog%20Application); [Basic Service](https://support.unitree.com/home/en/B2_developer/Basic%20Service).

The basic-interface article reverses publish/subscribe wording and alternates `rt/lowState` capitalization. The actual pinned B2 example uses GO-family `LowState_` received from lowercase `rt/lowstate` and `LowCmd_` published to `rt/lowcmd`; printing state does not require command publication. Its leg sequence is FR,FL,RR,RL, each hip/thigh/calf,12 active leg motors. Generic array capacity is not active motor count. IMU quaternion order is w,x,y,z; position/velocity and joint units require the selected source frame. [Basic Service Interface](https://support.unitree.com/home/en/B2_developer/Basic%20Service%20Interface); [pinned GO state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/LowState_.hpp).

The AI-motion frame is x forward, y left, z up. Its topic is `rt/sportmodestate`; odometry is separately documented on `rt/odommodestate` and `rt/lf/odommodestate`. The odometry article explicitly specifies500/20 Hz, metre/metre-per-second positions/velocities, radian Euler angles and wxyz quaternion. These are article-specific declared rates, not rates inferred from `lf`, device measurements or a guarantee after the associated service is stopped. Sport body-frame velocity and odometry-frame position targets must not be interchanged. [AI Motion Service](https://support.unitree.com/home/en/B2_developer/AI_Motion_Service); [AI Motion Interface](https://support.unitree.com/home/en/B2_developer/AI%20Motion%20Interface); [Odometer Service Interface](https://support.unitree.com/home/en/B2_developer/Odometer%20Service%20Interface).

### B2 control ownership and stateful requests <a href="#b2-control-ownership-and-stateful-requests" id="b2-control-ownership-and-stateful-requests"></a>

`RobotStateClient` separates service-list observation from `ServiceSwitch` and report-frequency changes. The portal uses input switch1=on/0=off but returned status0=on/1=off; do not conflate them. Protected services can reject switching (5202), and 5201 denotes a switch execution error. `MotionSwitcherClient::CheckMode` reports form0 standard/form1 wheels and the current mode name; `SelectMode`, `ReleaseMode` and persistent `SetSilent` change ownership/startup behavior. Silence is not a physical stop, and releasing the controller is not an observation-only diagnostic. [RobotStateClient Interface](https://support.unitree.com/home/en/B2_developer/RobotStateClient%20Interface); [Motion Switcher Service Interface](https://support.unitree.com/home/en/B2_developer/Motion%20Switcher%20Service%20Interface).

The legged AI interface distinguishes `Damp`, `BalanceStand`, `StopMove`, `StandUp`, `StandDown` and `RecoveryStand`: damping changes joint behavior, balance stand unlocks movement, stop resets much motion state, and recovery may roll the body. These are not interchangeable stop certificates. `Move` is body velocity; `MoveToPos` is an odometry-frame pose; `TrajectoryFollow` accepts a time/pose/velocity path; `Euler` requests attitude. Gait controls include `SwitchGait`, `SpeedLevel`, `ContinuousGait`, `VisionWalk`, `FreeWalk`, `ClassicWalk` and `FastWalk`. Continuous gait can keep stepping at zero requested translation. `SwitchMoveMode` changes response persistence; its documented one-second behavior is not a universal watchdog. `HandStand` and `AutoRecoverySet` may trigger violent motion and need the source's3 m clear radius, independent supervision and matched firmware. The remote chapter separately specifies2 m radius for recovery; retain those action-specific differences. [AI Motion Interface](https://support.unitree.com/home/en/B2_developer/AI%20Motion%20Interface); [Remote\_control](https://support.unitree.com/home/en/B2_developer/Remote_control); [pinned B2 client](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/b2/sport/sport_client.hpp).

The portal's low-level stand and wheel examples disable existing control and start recurrent publishers. Their initial delay before sampling angles is not proof of fresh/valid state; default zeros must not be accepted as measured initial posture. The AI example also stands and translates automatically. The remote-reader chapter demonstrates joystick values and button edges, but is distinct from a stand example. Helloworld publisher/subscriber examples exercise generic DDS; they do not commission robot control. [DDS Communication](https://support.unitree.com/home/en/B2_developer/DDS%20Communication); [AI Motion Control](https://support.unitree.com/home/en/B2_developer/AI%20Motion%20Control); [Standup On Basic Motion Control](https://support.unitree.com/home/en/B2_developer/Basic%20Motion%20Control%20Standup); [Get Remote Control Status](https://support.unitree.com/home/en/B2_developer/Get%20Remote%20Control%20Status); [Wheeled Motion Example](https://support.unitree.com/home/en/B2_developer/Wheeled%20Motion%20Example).

### Multimedia, network and SLAM are separate services <a href="#multimedia-network-and-slam-are-separate-services" id="multimedia-network-and-slam-are-separate-services"></a>

B2 front/back JPEG requests use `FrontVideoClient` and `BackVideoClient::GetImageSample` into a byte vector. Video transport is encoded H264, not raw RGB; the article gives multicast230.1.1.1 on ports1720/1721 for front/back,1280×720 at 15 Hz, and RTSP alternatives. Decode/queue load and camera selection belong to the receiving application. OpenCV requires a GStreamer-enabled build for the shown pipelines. No viewer, stream join or package build was run here. [Multimedia Service](https://support.unitree.com/home/en/B2_developer/Multimedia%20Service); [Multimedia Service Interface](https://support.unitree.com/home/en/B2_developer/Multimedia%20Service%20Interface); [front JPEG declaration](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/b2/front_video/front_video_client.hpp).

App binding, AP hotspot configuration and STA configuration are active network changes. The B2 network article says AP and STA are mutually exclusive and persist across restart, despite an introductory “three connections” wording that lists only two. Record the actual configured mode rather than enabling a hotspot to debug a subscriber. [Network Service](https://support.unitree.com/home/en/B2_developer/Network%20Service); [App Binding](https://support.unitree.com/home/en/B2_developer/App%20Binding).

The historical B2 SLAM interface requires PC2 at 192.168.123.162 and its 3D LiDAR at 192.168.124.20, with a matched service installation. The example requests `Slam Nav`≥1.1.2.1; that is a service-specific minimum, not a whole-robot firmware range. `rt/qt_command` handles mapping 3/4, relocation 6/7, navigation 8–11, pause 14? **The actual table is pause 13, resume 14, return 15 and close 99**; use that table, not guessed consecutive codes. Node/edge add topics are separate, query results have separate topics, and command notices correlate sequence and result. Adding topology information replaces existing data, so the complete intended set must be supplied together; it is not an append operation. No command payload is sent by this guide. [SLAM Service](https://support.unitree.com/home/en/B2_developer/SLAM%20Service); [SLAM\&Navigation Interface](https://support.unitree.com/home/en/B2_developer/SLAM%26Navigation%20Interface); [SLAM Example](https://support.unitree.com/home/en/B2_developer/SLAM%20Example).

Mapping needs valid odometry/IMU and point clouds; relocation requires a saved map and initial pose. Navigation depends on that localization and an approved topology. The source example recommends≤100×100 m, feature-rich stable scenes, no multifloor construction, slow mapping, a return to the starting pose, and no simultaneous App/SDK SLAM control. Reflective/transparent surfaces and feature-poor corridors can degrade localization. Edge avoidance flags0 stop/1 avoid/3 replan and navigation recovery are planning policies, not collision-clearance guarantees. [SLAM\&Navigation Interface](https://support.unitree.com/home/en/B2_developer/SLAM%26Navigation%20Interface); [SLAM Example](https://support.unitree.com/home/en/B2_developer/SLAM%20Example).

### B2-W-specific portal contract <a href="#b2-w-specific-portal-contract" id="b2-w-specific-portal-contract"></a>

The dedicated wheel interface uses the B2 `SportClient` but defines a **different gait enumeration**:0 idle,1 limb. It describes idle as faster wheel travel with lower crossing ability and limb as slower travel with better crossing capability. Its documented body-velocity request bounds are vx−0.8..1.2 m/s,vy±0.4 m/s,vyaw±0.75 rad/s, and the article explicitly says inputs are not filtered. Those source bounds are not recommendations to execute or a guarantee across firmware. They must not be replaced by legged B2 gait values0–4. [Wheeled Motion Interface](https://support.unitree.com/home/en/B2_developer/Wheeled%20Motion%20Interface).

The wheel article says `StopMove` is equivalent to zero requested velocity, `Damp` can let the robot settle under gravity, and recovery returns to damping before a later stand request. These behaviors differ materially from holding position or a certified emergency stop. Its 25-second RPC timeout is reply waiting time, not a wheel braking deadline. The low-level wheel example commands12 leg joints and four wheels, disables `wheeled_sport`, runs nominally every 2 ms and drives wheels forward/backward. It is an active whole-robot program, not a read-only startup check. [Wheeled Motion Interface](https://support.unitree.com/home/en/B2_developer/Wheeled%20Motion%20Interface); [Wheeled Motion Example](https://support.unitree.com/home/en/B2_developer/Wheeled%20Motion%20Example).

The remote article distinguishes general/special mode and notes that crawling/squatting is temporarily disabled in its latest described version. Do not promise a special configuration's rotating-jump function on every delivered B2-W. The tire row gives8.5 inches and pressure“2.4” without a unit; no inflation pressure in bar/psi is inferred. Match the tire label/manual before service. [Remote\_control](https://support.unitree.com/home/en/B2_developer/Remote_control); [B2-W tire subsection](https://support.unitree.com/home/en/B2_developer/About%20B2).

## Getting started <a href="#getting-started" id="getting-started"></a>

### Offline first result: preserve wheel slots separately <a href="#offline-first-result-preserve-wheel-slots-separately" id="offline-first-result-preserve-wheel-slots-separately"></a>

1. Record the exact B2-W and remote/pack/charger revisions. Stop if only a B2 or B2-Ex commissioning document is available.
2. Keep power/data connections unused. Copy this original standard-library Python 3 code, which inspects synthetic dictionaries only.
3. Run locally and compare its explicit wheel map with the pinned constants above. Do not interpret synthetic zeros as observed robot position or velocity.

```python
import math

WHEELS = {"FR": 12, "FL": 13, "RR": 14, "RL": 15}
def inspect_b2w(samples):
    previous = None
    changes = 0
    for sample in samples:
        motors = sample["motor_state"]
        if len(motors) != 20:
            raise ValueError("GO transport has 20 slots, not 16")
        for index in range(16):
            if not all(math.isfinite(float(motors[index][f])) for f in ("q", "dq")):
                raise ValueError("Non-finite leg/wheel state")
        tick = int(sample["tick"])
        changes += previous is not None and tick != previous
        previous = tick
    if changes < 1:
        raise ValueError("No observed tick transition")
    return {"model": "B2-W", "transport_slots": 20, "leg_slots": 12,
            "wheel_slots": WHEELS, "data_origin": "original mock"}

mock_motors = [{"q": 0.0, "dq": 0.0} for _ in range(20)]
print(inspect_b2w([{"tick": 1, "motor_state": mock_motors},
                   {"tick": 2, "motor_state": mock_motors}]))
```

**Expected result:** B2-W, 20 transport slots, 12 leg slots and FR/FL/RR/RL wheel indices 12/13/14/15. A 16-slot array, repeated tick or nonfinite wheel sample must fail. Only original mock parsing is verified; DDS compatibility, wheel direction, calibration and stop behavior are not.

For a later precommissioned subscriber-only session, capture `rt/lowstate` with the exact GO binding, show leg and wheel slots separately, require observed tick changes and finite samples, preserve firmware/domain/interface/source identity and close the reader on timeout or uncertainty. Do not call StandDown, ReleaseMode, SwitchGait or a stand demo to “enable” the read. No live activation command is given while firmware, charging and independent stop evidence remain unresolved.

### Why portal examples are not the first check <a href="#why-portal-examples-are-not-the-first-check" id="why-portal-examples-are-not-the-first-check"></a>

The source installation/build, high-level stand/lie-down, mode-release, network-route, SLAM and calibration routines are described for audit context only. Keep the existing complete original offline example as the first result; it uses synthetic data and makes no robot connection. Its pass verifies only the stated local checks. A later subscriber session needs an already approved state publisher, exact type/topic/model/firmware, independent stop/retention arrangements and an isolated network plan. No first check here activates DDS, opens a vendor SDK, changes a service or moves hardware.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Why does a leg-only decoder miss part of B2-W?** Its twelve-leg-slot loop omits wheels 12–15, while the GO record still has twenty slots. Use the map from the B2-W constants; do not reduce the serialized record to sixteen fields or label slots 16–19 as wheels.

**Can a B2 stand program test the wheels?** No. The B2-W example deliberately issues wheel velocity commands and releases control mode. The B2 and B2-W example motor modes also differ. A state-only check needs a subscriber with no action client/publisher.

**Why does the product page say 45°/40 cm but the manual restrict operation?** Maximum demonstrated capability and operator instructions describe different conditions. Use the current delivered operating envelope, not a product headline. This guide does not validate a route, jump or incline.

**Can the remote always stop a custom program?** The manual explicitly excludes remote control during low-level development. Link indication and damping buttons are not an independently validated wheel-braking system. Resolve stop behavior before hardware use.

**Can the B2 battery manual supply the missing B2-W charging values?** Not without explicit pack/charger compatibility evidence. The B2-W user manual supports its own removal/charging sequence, but no matched B2-W DC-output/current table was verified here. Read the delivered labels and obtain the matching accessory manual.

**App cannot bind or data does not arrive.** Separate account/Bluetooth/AP or Wi-Fi setup from SDK DDS. Confirm enterprise account, matching remote ID, correct app permissions and network path. For DDS check model type, exact interface/domain and source identity without changing controller modes. Do not treat a factory calibration action as network recovery.

### Interpreting portal fault and connection evidence <a href="#interpreting-portal-fault-and-connection-evidence" id="interpreting-portal-fault-and-connection-evidence"></a>

System faults (source+bitmask), rejected behavior and App/connectivity faults are distinct. The fault article places body communication flags in low-state `bit_flag`, leg motor faults in `reserve[0]`, and motor communication frequency in `reserve[1]`; these meanings are B2/bridge-specific. Wheel motors12–15 have a distinct fault-bit table, with FR,FL,RR,RL order. Do not decode an HG motor's reserved words using this GO-era table. Preserve source code, raw word, timestamp and selected schema. Some protective faults require manufacturer-directed recovery; restarting is not a universal first diagnostic. [FAULTS](https://support.unitree.com/home/en/B2_developer/FAULTS); [Fault Service Interface](https://support.unitree.com/home/en/B2_developer/Fault%20Service%20Interface).

The B2 quick-start's Ubuntu20.04 external-PC recipe says the built-in PC is not supported for that development path; this is different from later A2 onboard development. It reserves161–165 on the 123 subnet. A successful compile, ping or green binary icon does not validate motor control, service ownership or firmware. Use the existing original offline checkpoint first. [Quick Start](https://support.unitree.com/home/en/B2_developer/Quick%20Start); [Debugging specification](https://support.unitree.com/home/en/B2_developer/Debugging%20specification).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                    | Scope                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Official B2-W page](https://www.unitree.com/b2-w/)                                                                                                                         | Dedicated wheel-legged specification table and configuration footnotes.                                                                                                                                             |
| [English B2-W User Manual](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)                                                                                  | V1.1, revision 29 July 2025; 23 images. Safety, parts/tire figure, functions/interfaces, charging, preparation/startup/app/remote, shutdown/packing, fault handling, precautions, maintenance and revision history. |
| [English B2-W Remote Control Manual](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)                                                                     | V1.0, 18 April 2025; 14 images. R3/R1 hardware, calibration/feedback, charging/binding, operation/command tables, clearances and revision history.                                                                  |
| [Exact wheel constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2w/low_level/unitree_legged_const.py) | Model-specific leg/wheel index evidence; read as text only.                                                                                                                                                         |
| [Wheel-command example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2w/b2w_stand_example.cpp)                    | Control-path audit resource, not first-result execution.                                                                                                                                                            |

No B2-W exact store SKU, dedicated pack electrical manual, tire-pressure/fastener specification, mating connector/current-rating table, complete independent stop design or firmware bounds were established. B2-Ex certifications and B2 charger values are not transferred.

### Manual chapter index <a href="#manual-chapter-index" id="manual-chapter-index"></a>

Page ranges below are source-image numbers, not guessed printed-page offsets. Each link opens the original model-specific manual.

| Manual / source images                                                                        | Engineering content                                                                         |
| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [B2-W-user images 1](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)          | Cover / identity; interpreted in Product overview.                                          |
| [B2-W-user images 2](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)          | Contents; interpreted in Downloads and technical documents.                                 |
| [B2-W-user images 3–4](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Disclaimer / intended-use and service boundaries; interpreted in References and validation. |
| [B2-W-user images 4–5](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Safety instructions; interpreted in Hardware and connections.                               |
| [B2-W-user images 6–7](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Introduction and parts; interpreted in Product overview.                                    |
| [B2-W-user images 7–8](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Function highlights; interpreted in Applications.                                           |
| [B2-W-user images 9](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)          | Interface drawing; interpreted in Hardware and connections.                                 |
| [B2-W-user images 10–11](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Battery/remote charging; interpreted in Hardware and connections.                           |
| [B2-W-user images 12–13](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Environment/unpacking/preflight; interpreted in Hardware and connections.                   |
| [B2-W-user images 14](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)         | Startup and automatic standing; interpreted in Hardware and connections.                    |
| [B2-W-user images 15–16](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Enterprise app binding / networking; interpreted in Software and development resources.     |
| [B2-W-user images 17](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)         | Remote operation; interpreted in Hardware and connections.                                  |
| [B2-W-user images 18](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)         | Shutdown / packing; interpreted in Hardware and connections.                                |
| [B2-W-user images 19–20](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Abnormalities and calibration limits; interpreted in Troubleshooting and FAQs.              |
| [B2-W-user images 20–21](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Operating precautions; interpreted in Specifications.                                       |
| [B2-W-user images 22–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Cleaning/storage/inspection/pack maintenance; interpreted in Hardware and connections.      |
| [B2-W-remote images 1](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)     | Cover / controller revision; interpreted in Product overview.                               |
| [B2-W-remote images 2–3](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | Upgrade notice / R3 hardware and specification; interpreted in Hardware and connections.    |
| [B2-W-remote images 3–4](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | R3 joystick fitting / calibration / power; interpreted in Hardware and connections.         |
| [B2-W-remote images 5](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)     | R3 feedback controls; interpreted in Downloads and technical documents.                     |
| [B2-W-remote images 6–7](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | R3 charging and binding; interpreted in Hardware and connections.                           |
| [B2-W-remote images 8–9](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | R3 command table / clearances; interpreted in Hardware and connections.                     |
| [B2-W-remote images 10](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)    | R1 hardware and specifications; interpreted in Hardware and connections.                    |
| [B2-W-remote images 11](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)    | R1 calibration/power/charging; interpreted in Hardware and connections.                     |
| [B2-W-remote images 12](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)    | R1 binding and operation; interpreted in Hardware and connections.                          |
| [B2-W-remote images 13–14](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html) | R1 commands / clearances / revision history; interpreted in Hardware and connections.       |

### Original numbered interface figures <a href="#original-numbered-interface-figures" id="original-numbered-interface-figures"></a>

These manufacturer figures were visually inspected. Retain the source view and exact model/module applicability; no unverified wire-side mirroring or cross-model harness approval is implied.

* [b2-a2-2plus2](https://doc-cdn.unitree.com/static/2024/3/4/0953a73aeca14d93a69bc34ff3885ec4_1167x1084.png) — original source drawing, not a newly authored pinout.
* [b2-a2-8plus2](https://doc-cdn.unitree.com/static/2024/3/4/cf6393326af44931b544e444fcc5365e_1167x1084.png) — original source drawing, not a newly authored pinout.

### Actual portal source index and applicability <a href="#actual-portal-source-index-and-applicability" id="actual-portal-source-index-and-applicability"></a>

The following actual saved articles were reviewed as text/structured tables, with code blocks statically scanned and source hashes retained. Linked videos, binaries, CAD/mesh geometry and firmware were not executed or implicitly read. Empty landing pages supply no hidden instructions.

| Source article                                                                                                                | Functional coverage                                                                                                                  | Model applicability                                                                                   |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| [About B2](https://support.unitree.com/home/en/B2_developer/About%20B2)                                                       | Model/edition tables, interfaces, frames, conditioned performance and accessory distinctions; discrepancies remain visible.          | Wheel-specific subsection or interface; other B2 details remain scoped.                               |
| [Remote\_control](https://support.unitree.com/home/en/B2_developer/Remote_control)                                            | Controller-specific posture/ownership, active-action keys, pairing and environment/battery limits; no cross-controller key transfer. | Wheel-specific subsection or interface; other B2 details remain scoped.                               |
| [SDK Concepts](https://support.unitree.com/home/en/B2_developer/SDK%20Concepts)                                               | DDS state versus RPC request roles; generic middleware capabilities do not establish model entitlement.                              | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Architecture Description](https://support.unitree.com/home/en/B2_developer/Architecture%20Description)                       | Onboard/App/cloud roles and version/edition conditions, including remote-control authorization.                                      | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Robot Dog Application](https://support.unitree.com/home/en/B2_developer/Robot%20Dog%20Application)                           | Development/service category index; child articles supply actual contracts, not the landing page.                                    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Basic Service](https://support.unitree.com/home/en/B2_developer/Basic%20Service)                                             | Low command/state directions, motor index/model scope, IMU/BMS/board fields, CRC and owner hazards.                                  | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [AI Motion Service](https://support.unitree.com/home/en/B2_developer/AI_Motion_Service)                                       | State machine, body/odometry frames, active posture/gait/velocity requests, version limits and stop distinctions.                    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [DDS Service](https://support.unitree.com/home/en/B2_developer/DDS%20Service)                                                 | DDS state versus RPC request roles; generic middleware capabilities do not establish model entitlement.                              | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Multimedia Service](https://support.unitree.com/home/en/B2_developer/Multimedia%20Service)                                   | JPEG requests versus encoded video streaming, camera/profile differences and receiver/dependency conditions.                         | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Network Service](https://support.unitree.com/home/en/B2_developer/Network%20Service)                                         | Service/index content retained with exact source scope and explicit active-operation/firmware limits.                                | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [SLAM Service](https://support.unitree.com/home/en/B2_developer/SLAM%20Service)                                               | Map/localization/navigation ownership, exact environment/service bounds, request/result topics and active/file-overwrite hazards.    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [FAULTS](https://support.unitree.com/home/en/B2_developer/FAULTS)                                                             | Source-specific error namespaces and recovery limits; raw words kept with timing/model, no blind reset.                              | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Application development](https://support.unitree.com/home/en/B2_developer/Application%20development)                         | Development/service category index; child articles supply actual contracts, not the landing page.                                    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Obtain SDK](https://support.unitree.com/home/en/B2_developer/Obtain%20SDK)                                                   | Public SDK/model/CAD listings; linked binaries, geometry and firmware are not implicitly tested.                                     | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Quick Start](https://support.unitree.com/home/en/B2_developer/Quick%20Start)                                                 | Operating preparation, automatic startup/motion, App activation and shutdown; kept separate from offline first result.               | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [App Binding](https://support.unitree.com/home/en/B2_developer/App%20Binding)                                                 | Service/index content retained with exact source scope and explicit active-operation/firmware limits.                                | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Software Interface Services](https://support.unitree.com/home/en/B2_developer/Software%20Interface%20Services)               | DDS state versus RPC request roles; generic middleware capabilities do not establish model entitlement.                              | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [DDS Service Interface](https://support.unitree.com/home/en/B2_developer/DDS%20Service%20Interface)                           | Factory/channel/RPC declarations and examples, corrected against the pinned headers; queue/freshness and direction distinguished.    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [RobotStateClient Interface](https://support.unitree.com/home/en/B2_developer/RobotStateClient%20Interface)                   | Service-list observation versus switching/report changes and protected-service errors.                                               | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Motion Switcher Service Interface](https://support.unitree.com/home/en/B2_developer/Motion%20Switcher%20Service%20Interface) | Observed form/mode versus mode release, selection and persistent startup changes.                                                    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Basic Service Interface](https://support.unitree.com/home/en/B2_developer/Basic%20Service%20Interface)                       | Low command/state directions, motor index/model scope, IMU/BMS/board fields, CRC and owner hazards.                                  | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [AI Motion Interface](https://support.unitree.com/home/en/B2_developer/AI%20Motion%20Interface)                               | State machine, body/odometry frames, active posture/gait/velocity requests, version limits and stop distinctions.                    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Wheeled Motion Interface](https://support.unitree.com/home/en/B2_developer/Wheeled%20Motion%20Interface)                     | Wheel-specific gait/service contract or active whole-body wheel example; not a passive first check.                                  | Wheel-specific subsection or interface; other B2 details remain scoped.                               |
| [Multimedia Service Interface](https://support.unitree.com/home/en/B2_developer/Multimedia%20Service%20Interface)             | JPEG requests versus encoded video streaming, camera/profile differences and receiver/dependency conditions.                         | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Fault Service Interface](https://support.unitree.com/home/en/B2_developer/Fault%20Service%20Interface)                       | Source-specific error namespaces and recovery limits; raw words kept with timing/model, no blind reset.                              | Wheel-specific subsection or interface; other B2 details remain scoped.                               |
| [SLAM\&Navigation Interface](https://support.unitree.com/home/en/B2_developer/SLAM%26Navigation%20Interface)                  | Map/localization/navigation ownership, exact environment/service bounds, request/result topics and active/file-overwrite hazards.    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Odometer Service Interface](https://support.unitree.com/home/en/B2_developer/Odometer%20Service%20Interface)                 | Explicit declared rates, coordinate systems and wxyz/metre/radian units; no measured-rate guarantee.                                 | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Case reference](https://support.unitree.com/home/en/B2_developer/Case%20reference)                                           | Service/index content retained with exact source scope and explicit active-operation/firmware limits.                                | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [DDS Communication](https://support.unitree.com/home/en/B2_developer/DDS%20Communication)                                     | Factory/channel/RPC declarations and examples, corrected against the pinned headers; queue/freshness and direction distinguished.    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [AI Motion Control](https://support.unitree.com/home/en/B2_developer/AI%20Motion%20Control)                                   | Active publisher/control-ownership example, automatic movement and initial-state hazards; never the first check.                     | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Wheeled Motion Example](https://support.unitree.com/home/en/B2_developer/Wheeled%20Motion%20Example)                         | Wheel-specific gait/service contract or active whole-body wheel example; not a passive first check.                                  | Wheel-specific subsection or interface; other B2 details remain scoped.                               |
| [Standup On Basic Motion Control](https://support.unitree.com/home/en/B2_developer/Basic%20Motion%20Control%20Standup)        | Low command/state directions, motor index/model scope, IMU/BMS/board fields, CRC and owner hazards.                                  | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Get Remote Control Status](https://support.unitree.com/home/en/B2_developer/Get%20Remote%20Control%20Status)                 | Controller-specific posture/ownership, active-action keys, pairing and environment/battery limits; no cross-controller key transfer. | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [SLAM Example](https://support.unitree.com/home/en/B2_developer/SLAM%20Example)                                               | Map/localization/navigation ownership, exact environment/service bounds, request/result topics and active/file-overwrite hazards.    | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |
| [Debugging specification](https://support.unitree.com/home/en/B2_developer/Debugging%20specification)                         | Model-specific physical/network access and address selection; connectivity is not hardware-control readiness.                        | B2 family context only; wheel applicability requires matched service/hardware; no automatic transfer. |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026. Complete OCR sequences for the 23-image B2-W User Manual V1.1 and 14-image Remote Manual V1.0 were read; the remote command/clearance image was visually checked. User Manual image 3 corresponds to printed page 2; citations above consistently identify source-image sequence pages. The original interface drawing is linked for inspection rather than converted into a guessed pinout.

**Validation:** original inline Python exercised with synthetic good/bad capacities, repeated ticks and invalid leg/wheel values; source hashes and manual page/chapter coverage checked. **Not run:** Unitree imports/examples, SDK install/build, ROS/DDS/network discovery, simulator, hardware, wheel motion, calibration or flashing. Root SDK2 licenses are BSD-3-Clause; manual/figure and third-party rights remain separate. Hardware readiness stays draft. The applicable saved B2 portal corpus is now reviewed below; linked assets and exact wheel applicability remain separately bounded.

**Related documentation:** [Unitree model and development directory](./).

### Portal-expansion validation boundary <a href="#portal-expansion-validation-boundary" id="portal-expansion-validation-boundary"></a>

Expanded 24 November2026 from the actual saved published Markdown and exact cached manufacturer portal records. Existing nine-section anchors, all original executable code fences, source figures, manual image/chapter coverage and product identities were preserved. Applicable prose/tables and full resource/section inventories were reviewed; vendor source/example blocks were statically inspected, not compiled or executed. The source ledger distinguishes direct applicability, copied documentation, related-only wheel material, empty articles and linked-only assets. No claim is made that every external link/video/archive or all628 portal articles was read.

Only original offline examples/fixtures and static preservation/source checks were run. No vendor SDK import, install/build, ROS/DDS/multicast activation, hardware, motion, calibration, charging, reboot, route edit or flashing occurred. Exact delivered firmware, independent stop and revision-specific electrical/support gaps remain visible. This is an author replacement candidate for independent review; the parent remains the sole CMS writer.

**Related documentation:** [Unitree model and development directory](./).
