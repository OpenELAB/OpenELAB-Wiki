---
description: >-
  Understand model-specific navigation options, map and task data, all
  documented API operations and telemetry, with a standalone offline point-cloud
  example.
---

# Unitree industrial navigation: maps, routes, APIs and offline data

{% hint style="info" %}
**Shared software guide: Unitree industrial navigation.** This optional solution is available only for selected models/configurations; this page owns no robot SKU or retail entitlement. Use the [manufacturer/model directory](https://wiki.openelab.io/robotics/unitree), [SDK2 state guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development), [ROS2 integration guide](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration) and [G1 model guide](https://wiki.openelab.io/robotics/unitree/unitree-g1-standard-edu-development-guide) for their separate subjects. The first result here is an original offline point-cloud decoder, with no robot connection.
{% endhint %}

Unitree's navigation service separates localization maps, grid maps, topological routes, inspection tasks, command requests and asynchronous status. A successful HTTP response does not mean the robot arrived, a drawn route does not prove obstacle detection, and a software stop is not an independent physical emergency stop. This guide covers all 22 English navigation articles with source-specific model and revision limits. [Navigation overview](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service)

## Product overview <a href="#product-overview" id="product-overview"></a>

The web platform supports mapping/import, localization, route design, pose/topological navigation and task execution. The developer interface uses HTTP for operations and separate WebSocket streams for frequent status and important results; an SDK2 service interface is also documented. Inspection-specific payload actions, recognition and image capture need user development or a separate complete inspection solution. Navigation alone does not supply them. [Development scope](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_Secondary_Development_Guide)

The overview’s explicit compatibility table lists **B2, B2W, G1-EDU, A2 PRO and A2-W PRO as currently supported**, and **As2-EDU as extended support**, which it defines as not yet supported. Its upgrade precaution further limits B2/B2-W to serial numbers **after 365 with the standard LiDAR**; earlier units use an older navigation generation without this web console and with different protocols. The same chapter says installing industrial navigation disables the app navigation function, G1 lacks charging/gait-switch functions and A2 has only its default agile mode. These conditions must be resolved before selecting a procedure. [Overview §§1.6–1.7](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service)

There are four integration patterns: coordinate/pose navigation using a PCD map; navigation through a saved topological road network; temporary vertex/edge trajectories supplied by an external planner; and an inspection-task workflow with timed or externally triggered dwell. The web inspection chapter explicitly calls its basic inspection feature demonstrative and not recommended as a complete industrial inspection system. Preserve that restriction alongside the overview's industrial positioning. [Development advice](https://support.unitree.com/home/en/navigation/secondary_development_advises_and_guide), [Inspection](https://support.unitree.com/home/en/navigation/inspection)

## Applications <a href="#applications" id="applications"></a>

* **Inspection-platform integration:** use accepted command, current localization/control state and critical task result as separate stages; an external application owns payload actions and task policy.
* **Map and route preparation:** validate point-cloud quality, traversable-space assumptions and graph connectivity before considering live routes.
* **Offline log/visualization tools:** inspect exported telemetry, point clouds, topology files and scheduler history without sending commands.
* **Large/multi-map planning:** qualify overlap and paired switching points; visual alignment of layers is insufficient to establish coordinate correspondence.

The articles identify tunnels, RTK fusion, visual fusion, guided tours and group dance as optional or restricted solutions. They are not general capabilities of every Unitree robot. The English articles do not establish support for H2/H2-X, G1+, H1/H1-2, R1, Go1/A1/AlienGo/Laikago or arbitrary wheeled variants. A general SDK2 implementation does not fill those model gaps.

## Specifications <a href="#specifications" id="specifications"></a>

### Model, option and performance boundaries <a href="#model-option-and-performance-boundaries" id="model-option-and-performance-boundaries"></a>

| Source specification      | Published scope                                        | Qualification                                                                                     |
| ------------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| Mapping range per capture | B2/B2-W 100–200 m; G1 100 m; A2/A2-W 50 m              | Source-specific ranges, not a guarantee for every scene                                           |
| Map/task scale            | Maximum PCD range 1000 m; up to 30 map sheets per task | Large areas may require scanners and map switching                                                |
| Localization claims       | Relocalization ±3 cm; RTK fusion ±2 cm                 | Manufacturer-reported, optional equipment and scene conditions apply                              |
| Arrival / route deviation | Wheeled ≤8/20 cm; legged ≤5/5 cm                       | Reported specifications, not measured here or universal stopping margins                          |
| Navigation speeds         | Overview: legged 0.1–1 m/s, wheeled 0.1–2 m/s          | Edge chapter starts at 0.2 m/s; zero edge speed means model default, not stopped                  |
| Terrain                   | Overview ramps ≤30°, stairs ≤45°                       | G1 excluded; topology chapter further restricts model/gait/obstacles; no live terrain recipe here |
| Tunnel option             | B2, XT32 LiDAR and specially processed scanner map     | Standard RS5515 mapping is not an equivalent tunnel setup; wheeled robots discouraged             |
| Outdoor RTK option        | B2/B2-W and A2/A2-W                                    | Requires module, initialization signal, mapping origin/coordinate transform and delivered support |
| Guided tour / group dance | Optional G1-EDU indoor solution                        | Separate project/service prerequisites, not a generic navigation feature                          |

[Overview compatibility/performance table](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service), [topology restrictions](https://support.unitree.com/home/en/navigation/single_topology). The overview's “currently supported”/“extended” model presentation and other sections differ in scope; individual G1/A2 functions are documented but that does not prove every delivered version supports the full platform. Obtain the actual model/option/version matrix.

The overview excludes G1 from narrow tunnels, ramps/stairs and charging. Its charging table names B2/B2-W/A2 for QR/direct docking, while an older topology note limits automatic charging parameters to B2/B2-W and a newer subsection describes A2 QR docking with A2-W accuracy caution. These are unresolved revision/model differences, not permission to transfer docking procedures. Door/elevator/charging-room integrations are marked internal or advanced in parts of the sources. [Overview](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service), [docking details and notes](https://support.unitree.com/home/en/navigation/single_topology)

Group dance assumes substantial motion-control development, a separately selected G1-EDU navigation/group-control solution and project cooperation. The described stage is indoors, feature-rich, within 40×40 m and with at most one symmetry axis; high-dynamic localization up to 30 rad/s is not permission to execute such motion. Digital stage/trajectory editing, preview, group/music synchronization, monitoring and emergency management belong to that optional system. Guided tours add character/point/title/content/list/task management and AI voice interaction, requiring public-network connectivity and purchased AI services. These optional modules have no complete implementation manual in the 22-article set. [Overview notes](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Network/service roles <a href="#networkservice-roles" id="networkservice-roles"></a>

| Interface                      | Documented address/role           | Boundary                                                                                                    |
| ------------------------------ | --------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Navigation web console         | PC2, commonly port 8088           | AP/LAN/version-dependent entry addresses differ; use actual configuration                                   |
| Development operation endpoint | HTTP POST to PC2 `:18081/operate` | Commands can initialize, move, stop, change posture or start tasks; not a passive probe                     |
| Frequent status WebSocket      | PC2 `:18082`                      | `rt/slam_info`, optional `rt/rtk_status`; not a command channel                                             |
| Critical-event WebSocket       | PC2 `:18083`                      | `rt/slam_key_info`, task results and integration requests                                                   |
| Deployment tools               | PC2 `:18088`                      | Authenticated file/log/protocol tools; source says PC2 login credentials, no default password provided here |
| B2 cloud stream                | `:18082/mapping/cloud_registered` | Documented B2 visualization payload; LiDAR's `.124.20` is a different device address                        |

[Network connection](https://support.unitree.com/home/en/navigation/network_connection), [basic protocol](https://support.unitree.com/home/en/navigation/basic_description), [deployment tools](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_tool). These are source addresses, not discovered devices or public endpoints. The articles commonly use PC2 `192.168.123.162`; the web chapter also lists `.12.1`, `.123.161`, bare `.123.162` and port variations. LAN Wi-Fi obtains an address from the router; the development article discusses routing to internal PC2. Do not apply one example address to every version or change system routes as a first check.

The network article describes app Bluetooth binding, Wi-Fi versus AP configuration and account-unbinding through support. AP/production Multi-Band configurations have different purposes; the latter is a custom complete-inspection deployment. The internal 192.168.123 subnet is described without DHCP, reserving `.161`–`.165`; a qualified later setup must avoid address collisions. The article's generic Linux/Mac routing syntax needs host-specific verification, not blind execution. None is needed for the offline example.

Preserve approved PC account settings and credentials; the overview warns that a forgotten changed account may require factory reset with data loss. RTK fusion additionally requires the optional dual-antenna RTK/5G equipment, differential service account and data SIM. These prerequisites are separate from ordinary Wi-Fi reachability and are not supplied by the navigation API. [Overview precautions/options](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service)

Actual robot power, battery/charger/pinout, mounting, boot posture, payload clearance and emergency-stop instructions belong to the exact model manual. This shared guide supplies no energizing or motion sequence. The web joystick is A2/B2-specific, lower priority than the physical remote and able to change posture/move; it is not a replacement emergency stop. Its front/rear video display shows one selected stream, not complete surroundings. Software emergency stop offers limited protection; the source calls for an optional physical stop solution in industrial settings. [Other web functions](https://support.unitree.com/home/en/navigation/description_of_other_Web_functions)

### Mapping and environment constraints <a href="#mapping-and-environment-constraints" id="mapping-and-environment-constraints"></a>

Mapping requires usable LiDAR/IMU data and sufficient spatial features. The articles warn about blind areas behind the body/payload, incomplete one-direction scans, reflective water, fine wires/mesh, low objects and a 10–20 cm LiDAR blind spot. B2 reverse motion may lack obstacle sensing; the upside-down G1 MID360 has low/underfoot coverage gaps. These limitations must remain beside obstacle-mode selection. A source suggestion to disable avoidance in difficult terrain is not a safe general recovery procedure. [Single topology](https://support.unitree.com/home/en/navigation/single_topology)

For ordinary small scenes the map chapter discusses robot mapping; industrial/larger scenes call for scanners and larger RTK-enabled scans. Review final maps for layering, ghosts, warping and loop-closure errors; the live preview is not final quality. Tunnel mode lacks loop closure; multi-floor stairwell mapping has a separate loop-closure setting. A charging room needs a comprehensive scanner map with its door open. RTK maps require the recorded global-to-local origin/transform; visual/LiDAR fusion requires its optional module and usable lighting, not darkness or abrupt light changes. [Localization map building](https://support.unitree.com/home/en/navigation/Localization_Map_Building), [positioning modes](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Map, grid, topology and task data are different <a href="#map-grid-topology-and-task-data-are-different" id="map-grid-topology-and-task-data-are-different"></a>

| Data layer              | Purpose / key settings                                                                                                    | Acceptance boundary                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Localization PCD        | Name, indoor/outdoor/tunnel category, loop closure; advanced downsampling/XY/Z/IMU/RTK settings                           | Map quality and correct coordinate frame; advanced changes need matching guidance                               |
| Relocalization settings | Debug toggles, optional RTK, tunnel tolerance/segmentation, matching tolerance                                            | Settings apply only to corresponding map/mode; do not enable debugging or loosen tolerance to conceal a bad map |
| Occupancy grid          | PCD binding; downsampling, pixels/m resolution, opacity, passability/obstacle thresholds, inflation pixels, vertical crop | Only affects navigation when the relevant grid avoidance mode is selected                                       |
| Single topology         | One PCD; nodes, edges, attributes and graph connectivity                                                                  | Isolated nodes, missing endpoints or an off-road-network robot can prevent navigation                           |
| Composite topology      | At least two single topologies; paired switch nodes and cross-map edges                                                   | Same physical pose, different per-map coordinates; sufficient map overlap needed                                |
| Inspection task         | Saved route configuration, ordered points, dwell/trigger behavior, return/charge thresholds, loops and timers             | Not a complete payload inspection system; charging points excluded from inspection list                         |

[Mapping](https://support.unitree.com/home/en/navigation/Localization_Map_Building), [grid](https://support.unitree.com/home/en/navigation/Grid_Map), [single topology](https://support.unitree.com/home/en/navigation/single_topology), [composite](https://support.unitree.com/home/en/navigation/Composite_Topology), [inspection](https://support.unitree.com/home/en/navigation/inspection). Grid editing uses white for traversable, black for obstacle and eraser for unknown; undo/reset/save have distinct effects. Changing only display opacity or hiding the point cloud does not change localization quality.

Topology nodes carry position in meters, optional orientation in the UI's degrees, arrival accuracy, rotatability, map-switching and optional functional attributes. Edges carry endpoints, cost/weight, direction, rotatability, gait, obstacle mode and speed. Width/height/trajectory settings are internal or unsupported in the relevant chapter. Humanoids support a smaller attribute subset. Intermediate waypoints do not necessarily stop or execute target orientation; the final point can do so. A newly created edge's speed zero invokes a default and must not be interpreted as a stop.

The source uses different avoidance descriptions: pose mode 3 is described as ignoring intervening obstacles, whereas the topology edge “Off” text says minimal detection remains. Neither is a generally safe fallback, and both need exact service/model qualification. [Obstacle-mode context](https://support.unitree.com/home/en/navigation/single_topology)

Temporary-route `rpy` values are **radians**, unlike the UI orientation table. Map switching requires corresponding physical pose/orientation and paired switch points, not arbitrary lines between visually overlaid layers. The source suggests approximately 30 m overlap radius/60 m diameter in open scenes, with context-specific reductions indoors; three-way switching at one position is unsupported. Visual layer translation/rotation is not a surveyed transform. [Single/composite topology articles](https://support.unitree.com/home/en/navigation/Composite_Topology)

A composite topology cannot be nested into another composite, and the source says existing composites cannot be extended with additional single layers. Node numbers are reset during composition. The composite and single-layer maps then exist independently: edits in either are not propagated to the other. Finish composite editing before binding application node IDs, and version the maps rather than assuming live inheritance. [Composite topology restrictions](https://support.unitree.com/home/en/navigation/Composite_Topology)

The source’s gait subsection ends with an incomplete arrival-accuracy sentence. No missing tolerance or gait-setting instruction is supplied here. [Incomplete source context](https://support.unitree.com/home/en/navigation/single_topology)

Docking subsections discuss reflector-assisted alignment, direct positioning and A2 QR/marker alignment. The described marker is 36h11, 0.12 m black size, with orientation/mounting and `marker_id`, `marker_size`, `T_Dock_in_Aruco`/lateral-calibration fields. Reflector geometry, charging-room doors and alignment transforms are configuration-specific. The same sources disagree on model availability. No plate installation, charging-power wiring, transform recipe or autonomous docking test is authorized by this guide. Elevator integration requires external floor/door status feedback and a multi-map/floor convention, and is marked internal; the web console alone cannot sense or control an elevator. [Docking/elevator source subsections](https://support.unitree.com/home/en/navigation/single_topology)

### Command envelope and completion <a href="#command-envelope-and-completion" id="command-envelope-and-completion"></a>

The documented HTTP envelope has integer `api_id`, request identifier `id` (int64 in the source), and a function-specific `data` object. Responses use `succeed`, `errorCode`, `info`, `data`. Some source examples have comments, trailing commas or shorthand placeholders and are **not valid copy-ready JSON**. Treat exact spelling and types as a versioned contract, then validate actual JSON before a future qualified integration. JavaScript clients must preserve large integer IDs without silently losing precision.

The service is documented as SDK2 **`slam_operate` version `1.0.0.1`**, with JSON through `std_msgs::msg::dds_::String_` topics `rt/slam_info`, `rt/slam_key_info`, `rt/rtk_status`. That portal description does not prove a matching native SLAM client implementation in a particular SDK2 release. The canonical SDK2/ROS2 guides cover message/transport foundations; the navigation service and installed image remain separate qualifications. [Basic description](https://support.unitree.com/home/en/navigation/basic_description), [SDK2 guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development)

For repository reproducibility, the shared SDK2 C++ source baseline is commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`. Its [pinned official README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md) establishes the inspected SDK repository generation; it does not establish a matching navigation-server binary, native SLAM client or delivered firmware/service pairing. The closed/optional navigation solution remains governed by the article-specific service contract and actual unit entitlement.

### Complete command/API index <a href="#complete-commandapi-index" id="complete-commandapi-index"></a>

All rows are **source descriptions for inspection**, not instructions to send requests. An empty `data` object can still trigger movement or terminate localization. The common response envelope above applies unless additional result data is named.

| API ID             | Function and principal data fields                                                                                                                   | Prerequisite / material boundary                                                                                                         |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| 1004               | Initialize: `x,y,z,q_x,q_y,q_z,q_w,address`                                                                                                          | Stationary, appropriate posture/map, normalized quaternion; absolute PCD directory with trailing slash                                   |
| 1004 (`type=auto`) | Arbitrary auto-localization; `address`, optional clipping/resolution fields `cut_height_h/l,tar_leaf_size,src_leaf_size,min_level_res`               | Same ID with different mode; feature-rich small maps preferred; reported success still needs physical pose verification                  |
| 1005               | Charging-point historical auto-initialization, empty data                                                                                            | Uses last charging-point information and topology context; not safe arbitrary-position initialization                                    |
| 1105               | Topological node navigation: `version,topoAddress,nodeId`                                                                                            | Localization and road-network proximity; returns segmented `track`/`edgelist`, not arrival proof                                         |
| 1106               | Pose navigation: `targetPose`, `mode`, optional `meta`, `gridMap`, `speed`, `gait`, `adjustYaw`                                                      | Localization; quaternion and mode-specific grid; source recommends target within 10 m, not a guaranteed safe distance                    |
| 1104               | Sort from current localization: `version,topoAddress,taskQueue`                                                                                      | B2-labelled, localized/on graph; returns `sortResult`                                                                                    |
| 1107               | Sort from first supplied point: same principal fields                                                                                                | Heading says localization not required, but copied note says required; conflict unresolved                                               |
| 1103               | Recharge: `version,topoAddress,closestCharing,nodeId`                                                                                                | B2-series-labelled and localization; exact misspelling `closestCharing`; true nearest-selection overrides nodeId                         |
| 1108               | Temporary vertex/edge route: `vertices,edges`                                                                                                        | B2-labelled, localized; connected non-loop chain, current point named 1, sequential targets; directed/non-turnable attributes prohibited |
| 1109               | Replan topology: `version,topoAddress,nodeId`                                                                                                        | Active localization and suitable replanning edge; a graph with no alternative route can fail                                             |
| 1201 / 1202        | Pause / resume, empty data                                                                                                                           | Pause retains localization and task state; resume can move                                                                               |
| 1901               | Terminate navigation/control/localization, empty data                                                                                                | Different from pause, a motion-only stop or inspection cancellation                                                                      |
| 1903 / 1904 / 1905 | B2 damping / balanced stand / stop motion                                                                                                            | Motion service decoupled from navigation; no stable-hold or emergency-stop equivalence                                                   |
| 1906 / 1907 / 1908 | B2 stand / crouch / velocity `vx,vy,vyaw`                                                                                                            | Source velocity bounds ±0.6 m/s, ±0.4 m/s, ±0.8 rad/s; continuous-send semantics are not a qualified watchdog guarantee                  |
| 1944 / 1945 / 1946 | B2 agile / classic AI / gait switch `gait`                                                                                                           | Mode prerequisites apply; gait 0–4 has a separate enumeration from route gait                                                            |
| 1938 / 1939 / 1940 | A2 damping / balanced stand / stop motion                                                                                                            | Decoupled motion authority; not G1 motion APIs                                                                                           |
| 1941 / 1942 / 1943 | A2 stand / crouch / velocity `vx,vy,vyaw`                                                                                                            | Source x/y limits ±0.8/±0.5 m/s; yaw range ±2.0 is mislabelled m/s in the source and needs correction/qualification                      |
| 1702               | Start inspection: `startTaskInspectionFileName`, nested task `id`                                                                                    | Starts a saved task; nested ID differs from outer request ID                                                                             |
| 1701               | External continue trigger: boolean `continue`                                                                                                        | True advances a waiting inspection; not telemetry acknowledgement                                                                        |
| 1703               | Cancel inspection: `cancelTaskFlag`                                                                                                                  | Boolean table/example versus string comment conflict; cancel/completion terminates a task, pause alone does not                          |
| 1704               | Inspection recharge: `returnChargeFlag`                                                                                                              | Inspection-specific state change; model/dock limitations still apply                                                                     |
| 1909               | External door status: `type,typeId,state`                                                                                                            | Special integration feedback; must come from verified external state, not invented acknowledgement                                       |
| 1936               | Query localization: empty data, returns `isRelocation`                                                                                               | Source discourages relying on it instead of continuous localization data/freshness                                                       |
| 1501               | Generate grid: `pcd_file,pcd_name,resolution,std_limit,obstacle_limit,downsample_leaf_size,dilation_radius,cut_max_height,cut_min_height,saved_pics` | Primarily internal/not recommended; use web-exported grids when applicable                                                               |
| 1947               | B2 leg-odometry reset, empty data                                                                                                                    | Source recommends periodic reset for long uninterrupted operation; navigation handles it automatically; not a harmless read request      |

[Detailed interfaces, all subsections 3.2.1–3.2.6](https://support.unitree.com/home/en/navigation/detailed_description_of_interfaces). B2 movement/gait commands and A2 commands are not interchangeable, and the source says humanoid motion commands are unavailable through this category. It recommends over 10 Hz for continuous velocity messages but does not establish end-to-end stop latency, communications-failure safety or a power-off contract. Do not generate a live heartbeat loop from these descriptions.

### Route enums, fields and inspection configuration <a href="#route-enums-fields-and-inspection-configuration" id="route-enums-fields-and-inspection-configuration"></a>

| Structure              | Exact source information                                                                                                               | Integration consequence                                                                                                                              |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pose `mode`            | 0 cloud avoidance, 1 obstacle stop, 3 disabled, 4 grid                                                                                 | Not the same numeric map as edge `obs`                                                                                                               |
| Edge `meta.obs`        | 0 stop, 1 cloud, 2 trajectory/internal, 3 disabled, 4 grid                                                                             | Mode 4 requires a valid `gridMap`; do not send an enum from the other context                                                                        |
| Route `gait`           | 0 normal forward, 1 normal backward, 2 agile forward, 3 agile backward                                                                 | Distinct from B2 API 1946 `gait` 0 locked stand/1 blind/2 stepping/3 visual/4 planar                                                                 |
| Temporary vertices     | `pos`, `rpy`, `meta.type/typeId/chargingType`, `pcd`, `acc`, `turnable`                                                                | `acc` source range 0.05–0.2; special types include normal 0, map switch 6, direct charging 7; internal types are not enabled by knowing their number |
| Temporary edges        | `v` endpoint pair, `weight`, `meta.gait/v/w/h/ob/obs/dir/gridMap`                                                                      | `meta.v` is speed; outer `v` is endpoints; obstacle bounds array order is front-left/rear-left/rear-right/front-right                                |
| Temporary restrictions | At least two points, n−1 continuous edges, no rings, degree ≤2, no directed or non-turnable attributes                                 | Presence of those fields in an example is not permission to use prohibited values                                                                    |
| Route task             | `version,topoMultiple,tasks,globalWait,autoReturn,chargePercent,chargeBackPercent,inspectionSequence,arrivalAction,executionNum,timer` | Task tuples carry point/unused/initialization flags; dwell minimum 1 s; −1 disables low-battery return; charging points are not inspection points    |
| Task control           | `sequence`/`auto`; `wait`/`externTrigger`; execution count up to 99, 100 means continuous                                              | Automated order/continuous execution are active behavior; `initNode` is high-risk and `testMode` internal                                            |
| Timers                 | byDate date/time or byWeek time+weekday, unique ID, created timestamp and active flag                                                  | Weekday 0=Sunday; source allows only one active trigger; example is an array although a table calls it object                                        |

The web inspection page inconsistently describes a charging point as the first list item while another note/API chapter prohibits charging points in the inspection list. The API's sample `topoMultiple` path has inconsistent directory spelling/case, and `byDate` prose conflicts with the web chapter's one-time date schedule. Do not repair these discrepancies by guessing a production configuration. Validate the actual installed service's schema and exported task before any scheduled action. [Inspection article](https://support.unitree.com/home/en/navigation/inspection), [API inspection configuration](https://support.unitree.com/home/en/navigation/detailed_description_of_interfaces)

### Telemetry and error semantics <a href="#telemetry-and-error-semantics" id="telemetry-and-error-semantics"></a>

| Report                      | Source frequency / content                                                                         | Reader checks                                                                                                      |
| --------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| `robot_data`                | 0.5 Hz; motor temperature/error, battery current mA/voltage mV/percentage/temperature, CPU metrics | B2/A2 schemas differ; A2 has secondary battery and CPU frequency fields, unsupported mode fields may be −1         |
| `pos_info` / `mapping_info` | About 5 Hz; `currentPose`, `pcdName`, `address`                                                    | Match map and x,y,z plus quaternion x,y,z,w; require fresh continuing data                                         |
| `ctrl_info`                 | 1 Hz; target, arrival flag, distance, start/target poses, state machine, `obsInfo`, progress       | Navigation state, obstacle duration and progress are not equivalent to a result acknowledgement                    |
| `task_result`               | Critical-event stream                                                                              | Target node and `is_arrived` with error/result context; handle independently of frequent telemetry                 |
| `control_request`           | Critical door request                                                                              | Type/ID/state require an external integration response; UI alone cannot satisfy it                                 |
| `collision`                 | 10 Hz                                                                                              | Nearby-obstacle reporting can occur while stationary; do not infer a task failed solely from one proximity message |
| RTK                         | 10 Hz; signal, lat/lon/height, heading, solution and satellite count                               | `pos_type` 0/16/34/50 identifies none/single/float/fixed; signal true alone is not fixed-quality pose              |
| `joystick_info`             | 15 Hz; button booleans and lx/ly/rx/ry in −1..1                                                    | Reported button state is not authorization to replay commands                                                      |
| `inspection_data`           | Every 2 s; queue, scheduler, task, node progress and times                                         | Example `isTaskRunning` is the string `"false"`, which is truthy in some languages; preserve/validate actual type  |

All standard reports include source `sec`/`nanosec` and error/context fields where specified. Validate first sample, advancing time, local receive freshness, finite values and schema before display or decisions. Maintain independent freshness for high-rate pose and low-rate health; reconnect does not make cached state current. No `robot_data` humanoid schema is established by the B2/A2 examples. [Broadcast schemas](https://support.unitree.com/home/en/navigation/basic_description)

Error families in the source are indexed here for diagnosis: 0 normal; 1–16 communication/JSON/file/control/door/charge/map-switch/interruption/data errors; 100–109 underlying state, parsing, map/load/save/relocalization timeouts, invalid quaternion, unavailable service and sparse dock cloud; 200–221 topology/parsing/sort/charge/trajectory/connectivity/attribute/replanning/reflector errors (221 pending); 301–303 controller parameter/path/segment errors; 420–423 collision/range warnings; 501–510 missing sensors, parsing, drift, parameter/point/map/timeouts and mapping range; 701–702 task or task-file absence. Key graph cases are 207 duplicate, 208 self-loop, 209 isolated node, 210 missing endpoint, 213 off road network and 219 missing `gripMap` spelling in the source. Some topic assignments differ between the error table and report example (e.g. 421); retain the raw report and actual service version rather than assuming a universally consistent table. [Complete original error table](https://support.unitree.com/home/en/navigation/basic_description)

### Navigation error-code lookup <a href="#navigation-error-code-lookup" id="navigation-error-code-lookup"></a>

This compact lookup paraphrases every entry in the article's error table. Preserve the raw code and report channel: table classifications and live-report examples are not perfectly consistent.

| Codes   | Meaning in the reviewed source                                                                                                                                                                                                                                                                                                                                                              |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0–8     | 0 normal; 1 LiDAR unreachable; 2 command JSON parse failure; 3 motion command failed; 4 current pose unavailable; 5 door-open failure; 6 door-close failure; 7 recharge failure; 8 map-switch failure                                                                                                                                                                                       |
| 9–16    | 9 planned graph-result size invalid; 10 file write failed; 11 missing/invalid directory; 12 path outside allowed directories; 13 controller exception; 14 external/passive interruption, including remote intervention; 15 user interruption/new task/stop; 16 unacceptable input data                                                                                                      |
| 100–109 | 100 underlying state invalid; 101 input JSON invalid; 102 map save timeout; 103 map load timeout; 104 initialization timeout or match score out of tolerance; 105 mapping cancellation failed; 106 JSON file load failed; 107 initial position/quaternion invalid; 108 SLAM service unavailable; 109 dock-neighborhood cloud too sparse (source criterion: fewer than 3000 points in 3×3 m) |
| 200–206 | 200 command JSON invalid; 201 topology load failed; 202 navigation/task slicing failed; 203 point ordering failed; 204 missing/invalid charging point; 205 arbitrary trajectory creation failed; 206 tunnel route has no turnable node                                                                                                                                                      |
| 207–213 | 207 duplicate graph element; 208 self-loop; 209 isolated node; 210 edge references missing node; 211 graph planning failed; 212 topology task slicing failed; 213 current pose too far from the road network                                                                                                                                                                                |
| 214–221 | 214 target map missing; 215 target outside road network; 216 invalid attributes; 217 edge does not allow replanning; 218 already at target; 219 missing valid `gripMap` field (source spelling); 220 missing/incorrect reflector detections; 221 reserved/pending                                                                                                                           |
| 301–303 | 301 parameter-file load failed; 302 route start/end absent; 303 empty road-segment attributes                                                                                                                                                                                                                                                                                               |
| 420–423 | 420 very close/high collision risk; 421 nearby obstacle; 422 collision risk at current speed; 423 collision-detection range rejected                                                                                                                                                                                                                                                        |
| 501–510 | 501 IMU/LiDAR data missing; 502 JSON parse failed; 503 localization drift; 504 parameter load failed; 505 insufficient cloud points; 506 map save failed; 507 map load failed; 508 sensor-data wait timeout; 509 pose-match score too low; 510 mapping extent exceeded                                                                                                                      |
| 701–702 | 701 no matching/running task; 702 task file missing from the specified folder                                                                                                                                                                                                                                                                                                               |

[Original error table and topic assignments](https://support.unitree.com/home/en/navigation/basic_description). A code lookup is a diagnostic aid, not an instruction to retry a motion command, bypass a map constraint or weaken detection.

### Grid coordinates and processing tools <a href="#grid-coordinates-and-processing-tools" id="grid-coordinates-and-processing-tools"></a>

The grid conversion formula uses **Res in meters/pixel**: `xp=(X−X0)/Res`, `yp=H−(Y−Y0)/Res`, with inverse `X=X0+xp×Res`, `Y=Y0+(H−yp)×Res`. Pixel coordinates need integer handling and image bounds; yaw changes sign between the described coordinate systems. The UI/API generation parameter calls resolution **pixels/meter**, the reciprocal quantity. Keep them separate and verify exported metadata before conversion. [Grid API/formulas](https://support.unitree.com/home/en/navigation/detailed_description_of_interfaces)

Tool functions have different effects: imports/processors write maps, file/log downloads read saved records, protocol tests can send movement commands, and status reporting is observational. `GlobalMap.bin` is the active map filename in each PCD directory; the source permits a downloaded copy to be renamed `.pcd`, not arbitrary binary conversion. Topology `data.json` files live under `topoSingle` or `topoMultiple`. No dedicated map-transfer API is documented. [Map downloads](https://support.unitree.com/home/en/navigation/download_map_files_and_topology_map_files)

Logs are described under `/home/unitree/graph_pid_ws/bin/logs/` with `slam_server`, `graph`, `controller`, `slam_wrapper` subdirectories, and localization records under `graph_pid_ws/record`. Select time-correlated files around the anomaly; retain service start time, map/task revision and raw status/error sequence. These are documented on-robot paths, not private prerequisites for this guide. [Log download](https://support.unitree.com/home/en/navigation/download_log)

Map import discusses narrow-scene localization downsampling around 0.05, typical 0.1–0.2 and larger-scene visualization downsampling up to 0.8; these are source-specific processing choices, not a general tuning guarantee. The legacy standalone grid editor is deprecated in favor of console editing. LAS conversion needs colored LAS data for a platform archive; archives over 200 MB need a separate placement workflow. Feature enhancement discusses curvature 0.005–0.025 and smoothness 10–50, iterative review and generally sending original maps over 2 GB for support. **LAS conversion and feature enhancement are explicitly prohibited during localization/navigation because of CPU load.** Enhanced maps require Unitree review before use according to that article. [Import](https://support.unitree.com/home/en/navigation/import_map), [deprecated grid editor](https://support.unitree.com/home/en/navigation/grid_map_edition), [LAS tool](https://support.unitree.com/home/en/navigation/las_file_conversion_tool), [enhancement tool](https://support.unitree.com/home/en/navigation/feature_enhancement)

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: decode and reject synthetic cloud payloads offline <a href="#first-result-decode-and-reject-synthetic-cloud-payloads-offline" id="first-result-decode-and-reject-synthetic-cloud-payloads-offline"></a>

Prerequisite: Python 3 standard library only. Copy this complete original example into `navigation_cloud_check.py`, then run `python3 navigation_cloud_check.py`. No private cache, service, credential, SDK or network connection is used.

The source describes Base64 containing little-endian unsigned 16-bit x/y/z offsets, six bytes per point, in millimeters relative to bounding-box minima. The maximum offset is 65.535 m per axis. This example uses **invented test points**, not captured robot telemetry, and adds strict payload/bounds checks to the documented decoding principle. [B2 cloud payload specification](https://support.unitree.com/home/en/navigation/basic_description)

1. Open the linked B2 cloud specification in a browser and locate the six-byte little-endian quantization description; no service connection is needed.
2. Save the complete code below in a new local `navigation_cloud_check.py` file. The fixture is synthetic and already included.
3. Run `python3 navigation_cloud_check.py` from that file’s folder.
4. Confirm one accepted point and six specific rejection lines, then the PASS line. A successful check establishes only this offline decoder exercise.

```python
import base64
import math
import struct
from copy import deepcopy

def decode_cloud(c):
    if c.get("header", {}).get("frame_id") != "map":
        raise ValueError("frame")
    bounds = []
    for axis in "xyz":
        lo, hi = c[axis + "min"], c[axis + "max"]
        if (type(lo) not in (int, float) or type(hi) not in (int, float)
                or not math.isfinite(lo) or not math.isfinite(hi)
                or hi < lo or hi - lo > 65.535):
            raise ValueError("bounds")
        bounds.append((lo, hi))
    try:
        raw = base64.b64decode(c["data"], validate=True)
    except (ValueError, TypeError) as exc:
        raise ValueError("base64") from exc
    if not raw or len(raw) % 6:
        raise ValueError("length")
    points = []
    for offsets in struct.iter_unpack("<HHH", raw):
        point = tuple(bounds[i][0] + q / 1000 for i, q in enumerate(offsets))
        if any(point[i] > bounds[i][1] + 1e-9 for i in range(3)):
            raise ValueError("point outside bounds")
        points.append(point)
    return points

sample = {"header": {"frame_id": "map"}, "is_dense": True,
          "xmin": 1.0, "xmax": 2.0, "ymin": 2.0, "ymax": 3.0,
          "zmin": 3.0, "zmax": 4.0,
          "data": base64.b64encode(struct.pack("<HHH", 100, 200, 300)).decode()}
assert decode_cloud(sample) == [(1.1, 2.2, 3.3)]
print("accept: one synthetic point (1.1, 2.2, 3.3) m")
cases = [("wrong frame", {"header": {"frame_id": "base"}}, "frame"),
         ("nonfinite bounds", {"xmin": float("nan")}, "bounds"),
         ("quantization span", {"xmax": 100.0}, "bounds"),
         ("invalid base64", {"data": "***"}, "base64"),
         ("partial point", {"data": base64.b64encode(b"12").decode()}, "length"),
         ("outside bounds", {"xmax": 1.05}, "point outside bounds")]
for label, edits, expected in cases:
    c = deepcopy(sample)
    c.update(edits)
    try:
        decode_cloud(c)
    except ValueError as exc:
        assert str(exc) == expected, (label, str(exc))
        print("reject: " + label)
    else:
        raise AssertionError(label)
print("PASS: 7 offline cloud cases; no robot connection")
```

**Expected result:** one decoded point, six named rejections and the PASS line. This validates a narrow payload shape, not point-cloud provenance, localization quality, obstacle coverage, live freshness, frame transforms or safety. For an exported stream, retain the original payload and metadata, impose application-specific size/count limits, verify receipt time and map identity, and reject malformed records rather than truncating trailing bytes. Empty clouds need an explicit no-data policy; this miniature rejects them.

For a read-only protocol orientation, open the [basic description](https://support.unitree.com/home/en/navigation/basic_description) and [interface index](https://support.unitree.com/home/en/navigation/detailed_description_of_interfaces) in a browser. Locate ports 18081/18082/18083, `task_result`, API 1201, API 1901 and both obstacle-mode enums. **Expected record:** `commands / frequent status / critical results are separate; pause retains localization; terminate closes it; accepted request is not arrival`. No HTTP/WebSocket service needs to be contacted.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**The HTTP response succeeds but the robot has not arrived.** Treat the response as command feedback and inspect fresh pose/control plus the critical result stream. Preserve request/task/target identity. Do not automatically resend a movement or charging request after a timeout; it may have been accepted.

**Localization appears shifted or inconsistent.** Compare map identity/frame, pose quaternion and freshness, then final map quality, bidirectional coverage, scene features and mode-specific sensors. Do not hide a ghosted map by relaxing tolerance. Auto-localization success requires checking actual pose, not only a success flag.

**Navigation cannot start from a drawn point.** Check graph endpoints/isolated nodes, correct `topoAddress`, map identity and on-network proximity. The single-topology article cites approximately 0.5 m as a configurable proximity condition. That is a graph precondition, not a universal accuracy guarantee.

**Grid edits have no effect.** Check that the correct PCD/grid is bound and the request/edge actually selects grid avoidance. Confirm pixels/meter versus meters/pixel and row-axis/yaw convention before plotting coordinates.

**The protocol testing page says Connected.** It can prepare and send active requests. Connected is not proof of a safe command, fresh state or model support. Its status-reporting tab is a different function; the offline first result does not use the tool. [Protocol test](https://support.unitree.com/home/en/navigation/protocol_test)

**Task cancellation, pause or docking behaves differently.** Record service version and raw reports, distinguish inspection from navigation state, and resolve schema/model discrepancies before retrying. A scheduled task can still exist while movement is paused. Charging and elevator/door integration need exact model/options and external state, not another robot's defaults.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

### Complete 22-article functional index <a href="#complete-22-article-functional-index" id="complete-22-article-functional-index"></a>

| Source article / update date                                                                                                                           | Functional coverage and boundary                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [1. Overview of SLAM Navigation Service](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service) · 2026-09-16                        | Optional solution, complete modules/performance/options, current versus future model table, B2 serial/LiDAR upgrade restriction, app conflict, G1/A2 limits, RTK/tunnel/visual modes and group-dance/tour prerequisites.                  |
| [2. Navigation Platform(Web version) Instructions](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_web) · 2026-07-27                  | High-level map→route→inspection console workflow; no physical first-result sequence.                                                                                                                                                      |
| [2.1 Network Connection](https://support.unitree.com/home/en/navigation/network_connection) · 2026-07-27                                               | App binding, Wi-Fi/AP/LAN/Multi-Band, actual address/version differences and web layout; no guessed credentials or route changes.                                                                                                         |
| [2.2 Localization Map Building](https://support.unitree.com/home/en/navigation/Localization_Map_Building) · 2026-07-27                                 | Map category/loop closure/advanced parameters, mapping/save/view/thumbnail, relocalization settings, map-quality review, external import/RTK transforms and tunnel requirements.                                                          |
| [2.3 Grid Map](https://support.unitree.com/home/en/navigation/Grid_Map) · 2026-08-19                                                                   | PCD binding, generation parameters/units, brush/eraser/undo/reset, display versus saved map and required avoidance selection.                                                                                                             |
| [2.4 Single Topology](https://support.unitree.com/home/en/navigation/single_topology) · 2026-09-24                                                     | Node/edge properties/units, functional nodes, docking/markers, narrow regions, paired switching, internal elevator integration, waypoint/target difference, sensing/gait/environment limits, initialization and route editing/navigation. |
| [2.5 Composite Topology](https://support.unitree.com/home/en/navigation/Composite_Topology) · 2026-07-27                                               | At least two maps, no nesting/extension, node renumbering, independent edits, visual translation/rotation, paired physical switch poses and sufficient overlap.                                                                           |
| [2.6 Inspection](https://support.unitree.com/home/en/navigation/inspection) · 2026-08-05                                                               | Demonstration limitation; topology/task creation, point/order/properties, dwell versus trigger, thresholds/return, controls and one-time/weekly schedules; charging-list conflict retained.                                               |
| [2.7 Description of other Web functions](https://support.unitree.com/home/en/navigation/description_of_other_Web_functions) · 2026-09-03               | A2/B2 virtual joystick authority/posture/movement, software versus physical emergency stop, front/rear single-camera display.                                                                                                             |
| [2.8 Fast Inspection Guide](https://support.unitree.com/home/en/navigation/fast_inspection_guide) · 2026-08-05                                         | Map→single topology→inspection creation/save/initialize/start workflow; 20–30min demo estimate not commissioning guarantee.                                                                                                               |
| [3. Secondary Development Instructions](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_Secondary_Development_Guide) · 2026-07-27     | Service versus user inspection platform and prerequisite map/optional topology/tasks.                                                                                                                                                     |
| [3.1 Basic Description](https://support.unitree.com/home/en/navigation/basic_description) · 2026-07-27                                                 | HTTP/WS/SDK2 roles and addresses, JSON envelopes/service version/topics, quantized B2 cloud payload, complete telemetry families/units and full error-family index.                                                                       |
| [3.2 Detailed Description of Interfaces](https://support.unitree.com/home/en/navigation/detailed_description_of_interfaces) · 2026-07-27               | All35 distinct API IDs and36 operation variants, prerequisites, request fields, return envelope/path/sort data, route enums, task schemas, grid-coordinate conversions and contradictions.                                                |
| [3.3 Secondary Development Advises & Guide](https://support.unitree.com/home/en/navigation/secondary_development_advises_and_guide) · 2026-07-27       | Pose, saved topology, task-trigger and dynamic-route patterns, required localization shutdown after work/long sitting, separate group dance solution.                                                                                     |
| [4. Implementation Tools Guide](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_tool) · 2026-07-27                                    | Authenticated18088 deployment tools; maps/logs/protocol operations have distinct read/write authority.                                                                                                                                    |
| [4.1 Import Map](https://support.unitree.com/home/en/navigation/import_map) · 2026-07-27                                                               | External PCD import/downsampling and platform-directory options; no live map writes.                                                                                                                                                      |
| [4.2 Download Log](https://support.unitree.com/home/en/navigation/download_log) · 2026-07-27                                                           | Four log subsystems, record directory and service-start timestamps; time-correlated exported evidence.                                                                                                                                    |
| [4.3 Download Map Files & Topology Map Files](https://support.unitree.com/home/en/navigation/download_map_files_and_topology_map_files) · 2026-07-27   | PCD GlobalMap.bin and topoSingle/topoMultiple data.json exports; no dedicated transfer API.                                                                                                                                               |
| [4.4 Protocol Test](https://support.unitree.com/home/en/navigation/protocol_test) · 2026-07-27                                                         | API selection/template/send/log filtering versus continuous status subpage; Connected is not motion readiness.                                                                                                                            |
| [4.5 Grid Map Edition](https://support.unitree.com/home/en/navigation/grid_map_edition) · 2026-07-27                                                   | Deprecated standalone single-map grid editor, brush/obstacle/unknown meaning; console replacement.                                                                                                                                        |
| [4.6 LAS File Conversion Tool](https://support.unitree.com/home/en/navigation/las_file_conversion_tool) · 2026-07-27                                   | Colored LAS platform archive, CPU prohibition during navigation/localization and200MB manual-placement condition.                                                                                                                         |
| [4.7 Down Sample & Map Features Enhancement in Pipeline Tunnel Scene](https://support.unitree.com/home/en/navigation/feature_enhancement) · 2026-07-27 | Downsampling/enhancement, curvature/smoothness tuning, >2GB support path, dense-feature/sparse-plane review, Unitree approval and CPU prohibition.                                                                                        |

Selected original figures: [map→route→task workflow](https://doc-cdn.unitree.com/static/2026/7/21/fd23380f03e94bdfb11bec5de160740a_1776x250.png), [web navigation interface](https://doc-cdn.unitree.com/static/2026/7/9/1e8cdec667874f9f8da3060b76accbc2_1996x1078.png), [temporary-route concept](https://doc-cdn.unitree.com/static/2026/7/8/3f3e06245abe4030b02581604098ba8c_1778x626.png). Every indexed article retains its own original screenshot/resource context. These links do not establish every figure was visually verified or that a pictured version matches the installed console.

The web chapter's fast workflow covers mapping→single topology→inspection, including creation/save/initialization and task actions. Its 20–30 minute demonstration estimate is not a deployment or commissioning guarantee. Tools and API coverage above preserve the source's export/log/map/format resources without copying entire articles or uploading proprietary runtime packages. No applicable open-source navigation-server release or delivered firmware matrix was established; SDK2/ROS2 support must remain scoped to their separate canonical guides.

### Original figure and media link index <a href="#original-figure-and-media-link-index" id="original-figure-and-media-link-index"></a>

These are links to the original article resources, not newly measured results or reproduced manuals. All linked media retain their source context.

<details>

<summary>1. Overview of SLAM Navigation Service — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/21/fd23380f03e94bdfb11bec5de160740a_1776x250.png)

</details>

<details>

<summary>2.1 Network Connection — 7 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/f21fc01febd3463cb7cd4eb3f75ed095_2400x1080.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/40285a30bc184aa6b755a4662320557b_2400x1080.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/2/9/31004196c087479cbdc10d8591def316_2400x1080.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/eb556246cc2044e19c4bec9ca5bb7d7f_2400x1080.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/2/9/cc89ca6ca0544731a52c7c1747cbcdb9_2560x1600.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/7/6/c2b3d57be59742529e58ca0946253f51_2540x656.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/7/9/1e8cdec667874f9f8da3060b76accbc2_1996x1078.png)

</details>

<details>

<summary>2.2 Localization Map Building — 16 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/9/7047517409554de08572aa3fd377f91d_3024x1638.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/9/aeb09da2ff4a4710b637a6114b3ba9a6_3026x1640.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/7/9/fe2add9d0ce941938a44c075a122b83c_2992x1628.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/7/9/587479455d0f422097393b5bcc1d602c_3028x1640.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/7/9/0b1cced44c5e4e8db92e30d0893d83fa_3026x1640.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/7/9/5d20cb026b7c41da9e8fde40f73545c7_3022x1648.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/7/9/8f27bd1970cb438f9f7b42362653ba4d_3024x1650.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/7/9/073574972b874c2c8b85259f031e9766_3020x1646.png) · [Resource 9](https://doc-cdn.unitree.com/static/2026/7/9/aef3bb614d0e4e99a73d33f503a04948_3020x1650.png) · [Resource 10](https://doc-cdn.unitree.com/static/2026/7/9/f65fb05ef5a04b30b8ab64c6b7f291a9_3024x1638.png) · [Resource 11](https://doc-cdn.unitree.com/static/2026/7/9/01e4848ef8e14e988b42f674cb232118_3022x1634.png) · [Resource 12](https://doc-cdn.unitree.com/static/2026/7/9/4fc112370a12467f9d7b73777cdfe840_3024x1640.png) · [Resource 13](https://doc-cdn.unitree.com/static/2026/7/9/7f5283210d07413e81d0eb93ef6f7e8c_3024x1638.png) · [Resource 14](https://doc-cdn.unitree.com/static/2026/2/9/75017b0bff0b4318967277628067c78f_1279x1706.png) · [Resource 15](https://doc-cdn.unitree.com/static/2026/2/9/823a3ee16d004fcfbd1f356a0fa64e93_1279x1706.png) · [Resource 16](https://doc-cdn.unitree.com/static/2026/2/9/26871186b89b4591b3a4576a19b65643_1280x2759.png)

</details>

<details>

<summary>2.3 Grid Map — 10 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/9/d8d55877125c4a0ab54a8502ce2f0bc6_3022x1640.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/9/a638fc41fc594b23aa053800745fff4e_3024x1640.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/7/9/55d43dd560c643e2ad8417c56703b30e_3020x1638.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/7/9/f6f9ed8a2eb64607a37db3fafa125eb5_2066x1056.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/7/9/63a81badc0734bbe99c2d813f6c179cb_3024x1638.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/7/9/d712674a43d04ef7a6cc79adc41e06c9_3024x1640.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/7/9/1cd907396f0a40589b8588dccd3d8818_3024x1636.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/7/9/8bf6cb893907476eb3a7f6eedd382279_3024x1640.png) · [Resource 9](https://doc-cdn.unitree.com/static/2026/7/9/4b8cd0ee96954573a0de096bbb9c3263_3024x1636.png) · [Resource 10](https://doc-cdn.unitree.com/static/2026/7/9/4b192f0dd17140fd94ca8bd993253266_3022x1642.png)

</details>

<details>

<summary>2.4 Single Topology — 45 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/67ed0f023627495bb0a727c43b4b89d6_930x119.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/e755e1c8c55c47169cece1e156bc0c7d_692x653.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/7/9/f1c7317556274796a89f9eca66f18180_1074x992.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/7/7/39798ac7982740cd87be9200ac80060c_631x607.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/9/2/7ef15ed726c54c45a8f710eead3dc5c1_858x906.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/9/2/65597838454f42d9b147150615b58fa8_1614x984.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/2/9/bf1a586978b84f6d8530a99b9c5c432b_1012x331.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/2/9/f99802ef152b45cb8f3840d70da4285a_1231x244.png) · [Resource 9](https://doc-cdn.unitree.com/static/2026/7/22/3d6f5e78762247019cbcafe3cf4b04df_1500x890.png) · [Resource 10](https://doc-cdn.unitree.com/static/2026/7/22/9468760bce91466684eff3114a0020b8_1198x806.png) · [Resource 11](https://doc-cdn.unitree.com/static/2026/7/22/72eed816cb794442ac14f2cc19c3d7b2_1238x1154.png) · [Resource 12](https://doc-cdn.unitree.com/static/2026/7/22/857140acc7644e3293140ba475dd5a8a_1598x554.png) · [Resource 13](https://doc-cdn.unitree.com/static/2026/7/9/9f58fdec7aee4d0f8da1151d3b95241e_3024x1636.png) · [Resource 14](https://doc-cdn.unitree.com/static/2026/7/9/6f1d7cc026774479bb9b5b3512f2576a_3010x1642.png) · [Resource 15](https://doc-cdn.unitree.com/static/2026/7/9/e18ce3788c6d4773b1b1769c4387c4dc_3008x1640.png) · [Resource 16](https://doc-cdn.unitree.com/static/2026/7/9/353a7e25ef6d4d12abbce00d7bb4e4d0_3014x1638.png) · [Resource 17](https://doc-cdn.unitree.com/static/2026/7/9/a46f7fcc44fa4a3e8b859fc6549fd949_3014x1638.png) · [Resource 18](https://doc-cdn.unitree.com/static/2026/7/9/3a20c070ea9c467695226373df355315_78x618.png) · [Resource 19](https://doc-cdn.unitree.com/static/2026/7/9/07c418c50fc441e882b7c8556eca601d_3010x1638.png) · [Resource 20](https://doc-cdn.unitree.com/static/2026/7/9/d8e0bd1793024edf9a5319ebff7bbd45_3010x1636.png) · [Resource 21](https://doc-cdn.unitree.com/static/2026/7/9/00b3aecb7d0548488c7074d91f997e2a_3012x1636.png) · [Resource 22](https://doc-cdn.unitree.com/static/2026/7/9/343ef0bf1b2341d88fa52bf8003e0046_3010x1636.png) · [Resource 23](https://doc-cdn.unitree.com/static/2026/7/9/9e44b39482624cfc9976fa49cbcecd0a_610x52.png) · [Resource 24](https://doc-cdn.unitree.com/static/2026/7/9/7b032dc12b9c41c88bc5295661d4fb85_3046x1650.png) · [Resource 25](https://doc-cdn.unitree.com/static/2026/7/9/9dd5a4c556e047f1a07a84e0e49474a2_3046x1652.png) · [Resource 26](https://doc-cdn.unitree.com/static/2026/7/7/77807794f98e46a6809d53a3fe8ac225_64x54.png) · [Resource 27](https://doc-cdn.unitree.com/static/2026/7/7/17ae969f30bf4486ba03f812dbbc1609_52x44.png) · [Resource 28](https://doc-cdn.unitree.com/static/2026/7/9/21e219ce6df34d23b1e104bf339ab944_3046x1650.png) · [Resource 29](https://doc-cdn.unitree.com/static/2026/7/9/8018d379c72c491490abb9c5ce2eeb4a_3046x1650.png) · [Resource 30](https://doc-cdn.unitree.com/static/2026/7/9/242962596be8498b9357b14cc1aa7ad1_3048x1650.png) · [Resource 31](https://doc-cdn.unitree.com/static/2026/7/9/623a9ea407424afe8af696a45d9dbcfd_3046x1646.png) · [Resource 32](https://doc-cdn.unitree.com/static/2026/7/9/8c39c844e43c489599757a46e54554f2_3046x1646.png) · [Resource 33](https://doc-cdn.unitree.com/static/2026/7/9/3644272a887843bcbd197e21e43a91b1_3048x1644.png) · [Resource 34](https://doc-cdn.unitree.com/static/2026/7/9/d097b8b7447849f88e5524c5074ee6c8_3046x1646.png) · [Resource 35](https://doc-cdn.unitree.com/static/2026/7/9/988d3b3a11b947e4b523095174caa9a2_3046x1648.png) · [Resource 36](https://doc-cdn.unitree.com/static/2026/7/9/7dd5958053c745e887995bf0a31d43a3_3048x1642.png) · [Resource 37](https://doc-cdn.unitree.com/static/2026/7/9/aaf70c4a509b4f4e80687b4d74b777b3_3048x1650.png) · [Resource 38](https://doc-cdn.unitree.com/static/2026/7/9/57df431a97b54f728f8e35ce88492edd_3046x1644.png) · [Resource 39](https://doc-cdn.unitree.com/static/2026/7/9/7273777b157d440d9308a97a53620b81_3042x1646.png) · [Resource 40](https://doc-cdn.unitree.com/static/2026/7/9/60a6e799228c4e6e97fe97a03bd6e88c_3046x1650.png) · [Resource 41](https://doc-cdn.unitree.com/static/2026/7/9/ffee8c0ad9a0483787997c1fc6d4686c_3046x1650.png) · [Resource 42](https://doc-cdn.unitree.com/static/2026/7/9/7bfcc9e9044c4a00b25350eba99cf144_3042x1646.png) · [Resource 43](https://doc-cdn.unitree.com/static/2026/7/9/fd46e0d6b7c1425f8e856931588487d1_3048x1644.png) · [Resource 44](https://doc-cdn.unitree.com/static/2026/7/9/c7d806a292024ee6ad849afa8dbe18ca_3018x1636.png) · [Resource 45](https://doc-cdn.unitree.com/static/2026/7/9/b7220f6c91a64fb39b7bfb67abcc38e4_3046x1644.png)

</details>

<details>

<summary>2.5 Composite Topology — 18 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/9/c27bab062a0046be839430851584cb0b_3046x1648.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/9/6c7ee4317bfc4ceb89ba199ab17ca5fa_3046x1648.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/7/9/ed8ff0ed7277422f89d179230dcdcd6b_3054x1646.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/7/9/c1551eb023d849618a0b043b26a6e0c7_3050x1646.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/7/9/036f4d8ca6dd430f8ad080fe40e13c56_3046x1646.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/7/9/7285558c527544d78ef7944b79282d48_3050x1646.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/7/9/55dc198db4bf46b6addcc79295ace019_890x232.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/7/9/fcac2971d79447cab0cfaf9773cb9bf1_618x54.png) · [Resource 9](https://doc-cdn.unitree.com/static/2026/2/9/411b498148b842538ddb686a98ee2175_222x167.png) · [Resource 10](https://doc-cdn.unitree.com/static/2026/7/9/931e8b3d4644427f914ae20e7fd20f41_3044x1646.png) · [Resource 11](https://doc-cdn.unitree.com/static/2026/7/9/06a34725099c4a639f4caca0d7f27c75_3044x1642.png) · [Resource 12](https://doc-cdn.unitree.com/static/2026/7/9/62f192ba8ac348c7969dfa9bdb22c423_616x52.png) · [Resource 13](https://doc-cdn.unitree.com/static/2026/2/9/5078b239d32a4d5cad7e9802399f160e_372x365.png) · [Resource 14](https://doc-cdn.unitree.com/static/2026/7/9/8e69d069668b4b1682e0b94c1232078f_3050x1648.png) · [Resource 15](https://doc-cdn.unitree.com/static/2026/7/9/bc566ba51b4545a28498e29ab1f26e80_3046x1648.png) · [Resource 16](https://doc-cdn.unitree.com/static/2026/7/9/964c374867574c91810eb9ab906715a2_3046x1648.png) · [Resource 17](https://doc-cdn.unitree.com/static/2026/7/9/653c1195ca8744a49961e5cae428c805_3022x1644.png) · [Resource 18](https://doc-cdn.unitree.com/static/2026/7/9/e144f0d41b954fa8966cabafcc590e3a_3016x1640.png)

</details>

<details>

<summary>2.6 Inspection — 13 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/9/18c4e7f042254246b96ee7b86e1051d3_3050x1650.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/9/96382ff079f947c18e64cb868125f935_3046x1646.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/7/9/a771539820514c5d86ee77d8887057d0_3048x1648.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/8/5/d8024e2c2da84e42a444fefdc4650e95_3056x1656.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/8/5/ebaf9f48bfa746af9b1220ee1120b2e3_3056x1656.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/8/5/533227b0f3cf48db96c90a3f56861f41_3056x1656.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/7/9/b87a6692651f4c758bb50f37b8c3d5fb_866x660.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/7/9/5d81d9765de94a3380b0c99737d00fde_616x56.png) · [Resource 9](https://doc-cdn.unitree.com/static/2026/7/9/e2b22e22159e4e3ba252dc2740f2b388_3056x1656.png) · [Resource 10](https://doc-cdn.unitree.com/static/2026/7/9/817db7767ed448db8dbae9d0e56eaddb_3044x1648.png) · [Resource 11](https://doc-cdn.unitree.com/static/2026/7/9/732956a52f9f4c67adf3a20ffc4f480d_3020x1632.png) · [Resource 12](https://doc-cdn.unitree.com/static/2026/7/9/3dcf672ab19a4827b26875d22ac92101_3022x1634.png) · [Resource 13](https://doc-cdn.unitree.com/static/2026/7/9/44117a533cd6403cba5fdf5d5ff86487_3020x1632.png)

</details>

<details>

<summary>2.7 Description of other Web functions — 7 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/8/6/0be5ea277861441aa1ef4c51694d7ac7_100x100.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/8/5/d620155a87a542bda7d81d0a4e8bf261_3056x1656.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/8/5/98862f7db2dd4889aa1a28bd757c1557_3056x1656.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/e833b3f89fa14821ba48399d7c344a50_144x164.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/9/2/c8e0003eac9e43d1995bbec70c64bb85_3056x1656.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/9/2/479695ad86094260a7e70d5423a0a4ff_3056x1656.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/9/2/99206c9f83ef49fb8cbf94a766b1fb6a_3056x1656.png)

</details>

<details>

<summary>2.8 Fast Inspection Guide — 21 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/9/e5809ea13aad4a50ae223e9705e2a997_3024x1638.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/9/eb3d8d094b4e43aa87884490e4e139cd_3026x1640.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/7/9/800dde6a4e0340c6955ab454da1c93ac_3026x1640.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/7/9/9ce61d8e57c84baab419094ebe26733a_3024x1636.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/7/9/7a053ec8f86047e9bf8b47c8906168bf_3024x1638.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/7/9/e5651e73390042a09a8f6cbae9df7e00_3022x1634.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/7/9/967bc917c06548768d0475deac757555_3024x1638.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/7/9/365beacf592245c0b62d4bdca1f42dbc_410x238.png) · [Resource 9](https://doc-cdn.unitree.com/static/2026/7/9/affa35e67efd43b58cd4fa26063c6c23_3024x1636.png) · [Resource 10](https://doc-cdn.unitree.com/static/2026/7/9/fba9926f52bf4237921233672318a118_3008x1640.png) · [Resource 11](https://doc-cdn.unitree.com/static/2026/7/9/1d96447ab66a4e7dab686bebaf59db65_3012x1638.png) · [Resource 12](https://doc-cdn.unitree.com/static/2026/7/9/c9703f8fdf794e38bd996548c5d413b9_3010x1638.png) · [Resource 13](https://doc-cdn.unitree.com/static/2026/7/9/1c129476618942648e39aaaa69c31ded_3046x1652.png) · [Resource 14](https://doc-cdn.unitree.com/static/2026/7/9/84d10e27b56f458c9313d1b636bf56eb_3046x1646.png) · [Resource 15](https://doc-cdn.unitree.com/static/2026/7/9/9b04477f3b87498e9c6f245bb73d264b_3056x1656.png) · [Resource 16](https://doc-cdn.unitree.com/static/2026/7/9/297d810424de49a3a8b2715c3ee31f5c_610x354.png) · [Resource 17](https://doc-cdn.unitree.com/static/2026/7/9/6fa402e023924f9db119e1c641da3019_3050x1650.png) · [Resource 18](https://doc-cdn.unitree.com/static/2026/7/9/81b1e9b62ede41c89c06b9a71186e505_3048x1648.png) · [Resource 19](https://doc-cdn.unitree.com/static/2026/8/5/ebaf9f48bfa746af9b1220ee1120b2e3_3056x1656.png) · [Resource 20](https://doc-cdn.unitree.com/static/2026/8/5/533227b0f3cf48db96c90a3f56861f41_3056x1656.png) · [Resource 21](https://doc-cdn.unitree.com/static/2026/7/9/e2b22e22159e4e3ba252dc2740f2b388_3056x1656.png)

</details>

<details>

<summary>3.2 Detailed Description of Interfaces — 2 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/94beb67ea2984f928599d08dd3b1c7ca_269x163.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/8/3f3e06245abe4030b02581604098ba8c_1778x626.png)

</details>

<details>

<summary>3.3 Secondary Development Advises &#x26; Guide — 2 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/7/8/2cfef5658f43437fb13b433d91053b3d_1386x762.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/7/8/7c02c72748e54cb89e1cb28f10246636_1784x612.png)

</details>

<details>

<summary>4. Implementation Tools Guide — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/8602822d23cd4dafaca0180f43c0359a_1851x1052.png)

</details>

<details>

<summary>4.1 Import Map — 8 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/bf031ef247fb4370bf4c3fd7e8febfb7_1851x1053.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/f2dc611a29e44939a2237a05402684e8_1851x1052.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/2/9/0e10b33361234bfb8c424ec85bbaafd3_1851x1052.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/e0fc486066654dcd8c2b3543b07b7a22_1851x1087.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/2/9/2da6f65aca344ec1a6a9a0e8b2137532_1851x1087.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/2/9/1238ff439a1841598bf5a2028b938684_1851x1087.png) · [Resource 7](https://doc-cdn.unitree.com/static/2026/2/9/cd228249668543e5a60005aa25f3e875_1851x1087.png) · [Resource 8](https://doc-cdn.unitree.com/static/2026/2/9/f1e41a1644324fa4ab8cacf127f988fa_1851x1087.png)

</details>

<details>

<summary>4.2 Download Log — 2 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/f42cd79a991e4dc590393e87e7a11eab_1851x1053.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/673d678b079e4d46bfdf4e5f68240280_1851x1053.png)

</details>

<details>

<summary>4.3 Download Map Files &#x26; Topology Map Files — 6 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/b146e880db38422c9d3a8c6b35f70f43_1851x1053.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/5bb6753b6607421882aa7a0fb0effbf5_1851x1053.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/2/9/e354816a3bf34755ae9d17b05a86e4af_1851x1053.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/4df90dc098c84b5caf02e51b4662ed78_1851x1053.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/2/9/b62b4125fe49403893b339dec74ef0b0_1850x1134.png) · [Resource 6](https://doc-cdn.unitree.com/static/2026/2/9/30f77be1af584f68a0791e24bc3b55ab_1851x1053.png)

</details>

<details>

<summary>4.4 Protocol Test — 4 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/64418c45b33c46e792d6585d649cb1eb_1851x1053.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/625e0e3b113e43cead6a41f6599b4286_1851x1053.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/2/9/d76f88e0424f4573bd02dd6dfc23b2b0_1851x1053.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/d19a63c089d944f4a204e0b1a4aaa867_1851x1053.png)

</details>

<details>

<summary>4.5 Grid Map Edition — 4 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/032f5e11f2ab4aca9f7c032254717130_1850x1087.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/54a634a5f8ce42ba9def1371a97d3805_1851x1087.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/2/9/6abd670f8fa546978bb11988e1428937_1851x1084.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/df659bb70edd40be96531e4b1f8f3335_1850x1084.png)

</details>

<details>

<summary>4.6 LAS File Conversion Tool — 2 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/bb8b2de4499046dba493ea6b2d854eba_1848x1053.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/01b753d2f6104f3da6ee45dc9a134be8_1851x1053.png)

</details>

<details>

<summary>4.7 Down Sample &#x26; Map Features Enhancement in Pipeline Tunnel Scene — 5 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2026/2/9/3f5d7b548e0f410b8e7c65869f61afa6_1851x1087.png) · [Resource 2](https://doc-cdn.unitree.com/static/2026/2/9/7acc6a5ba6764358bbfbf5d2f2d67d7e_1850x1087.png) · [Resource 3](https://doc-cdn.unitree.com/static/2026/2/9/b80af89c26a74da5995aa1340a367482_1851x1137.png) · [Resource 4](https://doc-cdn.unitree.com/static/2026/2/9/ca536292310d46cc9b2a5b15539e6443_1851x1137.png) · [Resource 5](https://doc-cdn.unitree.com/static/2026/2/9/f2d8ebd10edf4330bf80d8588217b98d_1851x1137.png)

</details>

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **2026-11-24** against all 22 actual English navigation article bodies, whose update dates are preserved in the index. Service version `1.0.0.1` is a documented API service version, not a confirmed robot firmware. Source/model/type/unit conflicts are retained rather than silently normalized.

**Validation:** the original seven-case point-cloud example was executed offline. No robot/service requests, authentication changes, vendor installs/builds/imports, ROS/DDS, simulator/hardware motion, charging, map writes, scheduling or firmware work were performed. Source-bounded draft: API descriptions and synthetic decoding are usable for offline engineering; installed-service compatibility, physical operation and optional solutions remain unqualified.

**Related documentation:** [Unitree model and development directory](./).
