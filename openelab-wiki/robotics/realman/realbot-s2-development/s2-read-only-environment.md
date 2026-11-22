# S2 tutorial: read-only environment and discovery

{% hint style="info" %}
**Target:** the delivered RealBot-S2 Ubuntu 22.04 / ROS 2 Humble image and matching interface SDK. Run on the robot through the authorized project account. The commands below inspect the system; they do not enable or move it.
{% endhint %}

## Prerequisites

Complete the [S2 hardware/network identity check](../realbot-s2-guide.md). Record the installed version, scene, profile and approved local DDS settings. Keep all customer motion sources inactive. Source: [S2 interface V1.3, PDF pp. 5–9, 61–66 \[S2\_API\]](../realman-source-library.md).

## Load the delivered environment

For an on-robot interactive CLI session, V1.3 §16.1 uses the following complete overlay order and the `ROS_LOCALHOST_ONLY=0` discovery setting. This differs from its long-running production-node baseline (`1`). Use it only if it matches the delivered local CLI instructions; do not edit robot startup files or apply the interactive setting to a production service.

{% code collapsedlinecount="10" %}
```bash
source /opt/ros/humble/setup.bash
source /rm_app/rm_robot_ws/install/setup.bash
source /rm_app/body_chassis/setup.bash
source /rm_app/rmos/install/setup.bash
export ROS_LOCALHOST_ONLY=0
export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
export FASTRTPS_DEFAULT_PROFILES_FILE=/rm_app/rm_robot_ws/script/fastdds.xml
cat /rm_app/rm_robot_ws/version.txt
echo "$ROS_DISTRO"
echo "$ROS_DOMAIN_ID"
echo "$RMW_IMPLEMENTATION"
ros2 pkg prefix rm_robot_interfaces
```
{% endcode %}

Do not invent a ROS domain value. If any setup file, DDS profile or message package is missing, stop and confirm the delivered image/SDK. A package prefix should resolve to the expected installed workspace; never copy a random dynamic library into `/rm_app` to bypass a mismatch.

## Discover and check one public topic

{% code collapsedlinecount="10" %}
```bash
timeout 15 ros2 node list --no-daemon --spin-time 5
timeout 15 ros2 topic list -t --no-daemon --spin-time 5
timeout 15 ros2 service list -t --no-daemon --spin-time 5
timeout 15 ros2 topic info /robot_slave/states --verbose --no-daemon --spin-time 5
timeout 15 ros2 topic echo /robot_slave/states --once --no-daemon --spin-time 5
```
{% endcode %}

`timeout` bounds an interactive query; it is not a robot stop mechanism. An exit caused by the time limit is a failed/unfinished observation, not a passing test. Confirm the aggregate message type is `std_msgs/msg/String`, that its publisher belongs to the expected delivery and that the content passes V1.3's schema.

Read chassis lifecycle state without changing it:

{% code collapsedlinecount="10" %}
```bash
ros2 lifecycle nodes
ros2 lifecycle get /chassis_driver_node
```
{% endcode %}

Startup handles configure/activate. Do not issue lifecycle transitions, parameter writes, fault-clear services or restarts as an ordinary client recovery procedure.

## Expected result and evidence

The installed version/profile is identified, Humble/Fast DDS and the delivered SDK resolve, and a public status topic has the expected type, publisher, QoS and valid content. Save a small redacted baseline with observation time, client version and topic information. Avoid full unmasked business payloads or credentials in logs.

## Troubleshooting

**No graph:** verify all overlays, domain, RMW, delivered Fast DDS profile, locality and scene. A ping reply does not establish ROS discovery.

**Type cannot be loaded:** inspect `rm_robot_interfaces` from the installed SDK. If the optional `ros2 interface` extension is unavailable, read the delivered `.msg` definition under that package's `share/rm_robot_interfaces/msg` directory. Do not guess fields from one payload.

**Topic exists but no valid data:** check publisher, driver readiness, optional hardware/scene and QoS before investigating the consumer. Do not restart the base system automatically.

## External hosts and deployment

External ROS access is a separately delivered capability. It needs the network/domain/DDS settings, matching SDK and firewall/security instructions. Long-running on-robot nodes should use V1.3 §2.3/§16.8's production baseline and the separate customer overlay; do not reuse this interactive example blindly.

## Sources and validation

[S2 interface V1.3, PDF pp. 5–9, 61–66 \[S2\_API\]](../realman-source-library.md). Reviewed 22 November 2026; commands were not executed on a robot. Continue with [state and sensor validation](s2-state-and-sensors.md).
