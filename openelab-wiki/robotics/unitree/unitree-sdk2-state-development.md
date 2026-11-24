---
description: >-
  Prepare pinned Unitree SDK2 C++ and Python environments, select Go2 GO or
  G1/R1 HG state bindings, and inspect a bounded subscriber-only workflow with
  clear edition and control-ownership limits.
---

# Unitree SDK2 State Development: Go2, G1 and R1

{% hint style="info" %}
**Related host listings on OpenELAB — this is a supporting development guide, with no separately sold SKU:**

[**G1 EDU Plus U2**](https://openelab.io/products/unitree-g1-edu-plus-u2) · SKU `Unitree-G1edu-U2` · [**G1 EDU Standard U1**](https://openelab.io/products/unitree-g1-edu-standard-u1) · SKU `Unitree-G1edu-U1`.

[**Go2 Air**](https://openelab.io/products/unitree-go2-air) · robot option SKU `Unitree-Go2-Air` · [**Go2 Pro**](https://openelab.io/products/unitree-go2-pro-quadruped-robot) · SKU `Unitree-Go2-Pro`.

These are catalog identity references. AIR/PRO listings do not establish SDK2 access; the G1 U1/U2 links do not establish an identical joint configuration. Use the exact purchased-host guide and its delivered configuration before commissioning.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree SDK2 lets a host computer receive typed robot state through Data Distribution Service (DDS), and provides separate interfaces that request or publish robot actions. This guide starts with a bounded **subscriber-only** state reader: Go2 uses `unitree_go`, while G1 and the inspected R1 humanoid example use `unitree_hg`. It covers source selection, dependency preparation, original Python/C++ readers, and the boundary between observing a robot and taking control. [GO/HG binding notes](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/readme.md) [R1 source contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/r1/low_level/r1_low_level_example.py)

This is a shared SDK reference. It does not replace the G1, Go2 or R1 hardware guide, the separate [ROS2 state-development guide](unitree-ros2-integration.md), or a delivered robot's commissioning manual. The Unitree support portal was inaccessible during this review; this page makes no claim to have read its complete manuals or model inventory.

**Edition matters.** Unitree's G1 comparison marks secondary development “/” for G1 and “YES” for G1 EDU. The Go2 AIR/PRO/X/EDU comparison uses `○ / ○ / ◕ / ●` for secondary development; the partial X symbol's precise access level requires the manual. Do not substitute a retail Go2 AIR/PRO or base G1 merely because an SDK example names the family. R1 example code verifies an HG message contract, not entitlement or a retail U1–U6 configuration mapping. [Unitree G1 comparison](https://www.unitree.com/g1) [Unitree Go2 comparison](https://www.unitree.com/go2)

## Applications <a href="#applications" id="applications"></a>

* Confirm that a development-enabled robot exposes progressing IMU and joint-state messages before creating a controller.
* Log decoded state for diagnostics, timestamp inspection and later engineering analysis without adding a motor-command publisher.
* Reuse a small formatter in an isolated simulator, then compare message structures with the delivered robot's documented interface.
* Separate high-level locomotion requests, arm commands, whole-body control and independent hand services before selecting an implementation.

A successful state subscription establishes communication with a source of that DDS type. It does not identify the robot serial number, prove all sensors are calibrated, validate firmware compatibility, or establish that motion commands are permitted.

## Specifications <a href="#specifications" id="specifications"></a>

### Reviewed software snapshot <a href="#reviewed-software-snapshot" id="reviewed-software-snapshot"></a>

| Component              | Exact reviewed baseline                                                                     | Meaning and boundary                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| C++ SDK2               | Commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; CMake project version `2.0.0`            | Source snapshot; not a robot firmware revision                                                                                                     |
| Python SDK2            | Commit `814556d15970dd2ecf1c9984e845ca02ab07e206`; package `unitree_sdk2py` version `1.0.1` | Python interface package, not the legacy legged SDK Python wrapper                                                                                 |
| C++ vendor prebuild    | Ubuntu 20.04 LTS, GCC 9.4.0, `aarch64` or `x86_64`                                          | Architecture-matched prebuilt SDK library; other systems not validated here                                                                        |
| C++ project language   | C++17                                                                                       | Root CMake minimum is 3.5; README prerequisite is CMake ≥3.10; the recipes below require CMake ≥3.15 for their modern configuration/install syntax |
| Python runtime         | Python ≥3.8; `cyclonedds==0.10.2`; NumPy; OpenCV Python                                     | Actual `setup.py` requirements; Python ≥3.8 is a declared floor, not proof every newer interpreter works                                           |
| First reader transport | DDS `rt/lowstate`; real-robot examples use domain `0`                                       | Explicit robot-facing network interface required by this guide                                                                                     |
| Isolated simulation    | Domain `1`, interface `lo` in this guide                                                    | Matches MuJoCo's recommended separation; simulator must use the same domain/type                                                                   |
| Live firmware minimum  | Unresolved                                                                                  | Obtain the exact image/controller pairing for the delivered edition before a physical run                                                          |

Sources: [C++ SDK2 README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [C++ project contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt), [Python dependency contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py), [MuJoCo interface and configuration](https://github.com/unitreerobotics/unitree_mujoco/blob/1eb6642e3f3fdfb7fb13a9794fd6a2dd93ea0e7d/readme.md).

### Select the message type before writing a callback <a href="#select-the-message-type-before-writing-a-callback" id="select-the-message-type-before-writing-a-callback"></a>

| Robot scope                                                       | SDK2 state binding                                                                                | Important distinction                                                                                         |
| ----------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Go2; documented Go-family binding also names B2, B2w, Go2w and H1 | C++ `unitree_go::msg::dds_::LowState_`; Python `unitree_sdk2py.idl.unitree_go.msg.dds_.LowState_` | 20 message slots. Go2's body has 12 joint entries; capacity is not active-joint count                         |
| G1 and H1-2                                                       | C++ `unitree_hg::msg::dds_::LowState_`; Python `unitree_sdk2py.idl.unitree_hg.msg.dds_.LowState_` | 35 message slots; inspect the purchased configuration before labeling them                                    |
| Inspected R1 humanoid example                                     | Same HG state binding                                                                             | Example has 26 active joints distributed over DDS indices `0–13, 15–19, 22–26, 29–30`; not the first 26 slots |

The inspected G1 29-joint example flags waist roll/pitch as invalid on a 23-DoF or locked-waist configuration, and additional wrist pitch/yaw joints as invalid on a 23-DoF configuration. Do not reuse its gain arrays or joint loop for every G1 EDU option. The first reader below intentionally displays slot 0 only. [GO/HG binding notes](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/readme.md) [GO LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_LowState_.py) [HG LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_hg/msg/dds_/_LowState_.py) [G1 low-level source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/low_level/g1_low_level_example.py) [R1 source contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/r1/low_level/r1_low_level_example.py)

The GO state schema has `power_v`/`power_a`; the HG state schema does not. Both expose `tick`, `imu_state` and `motor_state`. A decoder banner saying Cyclone DDS IDL v0.11.0 describes generation tooling; the Python dependency remains `cyclonedds==0.10.2`. [GO LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_LowState_.py) [HG LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_hg/msg/dds_/_LowState_.py) [Python dependency contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

Use the exact host guide for power, battery handling, connector identification, suspension/support and physical stop controls. This software reference assigns no pinout, supply voltage or reset sequence to all Unitree robots.

Before a physical state check, record the robot model, edition, active-joint configuration, firmware/image revision, installed accessories, host OS/CPU, SDK commit, network interface and domain. Confirm that the purchased edition exposes the intended SDK interface. If those are unresolved, retain the offline result and stop before a live connection.

Use the documented robot Ethernet connection and the actual robot-facing interface name. `enp2s0` and `eth0` in upstream examples are examples, not identifiers guaranteed on your machine. A sensor bridge or USB Ethernet adapter can introduce another interface; automatic interface selection can therefore choose the wrong network. This guide requires an explicit interface argument. The SDK2 Python factory is a singleton and ignores subsequent reinitialization after success: use a new process when changing domain or interface. [Python channel implementation](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/core/channel.py)

DDS discovery and data reception require matching domain, message type, network reachability and the relevant multicast/network configuration. Do not switch controller modes or disable built-in services to fix a missing subscriber message. A receive-only application can still exchange discovery traffic; “subscriber-only” here means no application motion-command writer or RPC action client.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### C++ preparation and reader build <a href="#c-preparation-and-reader-build" id="c-preparation-and-reader-build"></a>

The following are **documented preparation commands, not commands executed during this review**. Use an approved development host matching the vendor baseline. Review local package changes first. Use CMake ≥3.15 for this recipe’s `-S`/`-B` and `--install` syntax; the vendor README’s SDK prerequisite is ≥3.10. Install the other dependencies listed in the pinned README:

```bash
sudo apt-get update
sudo apt-get install -y cmake g++ build-essential libyaml-cpp-dev libeigen3-dev libboost-all-dev libfmt-dev
git clone https://github.com/unitreerobotics/unitree_sdk2.git
cd unitree_sdk2
git checkout b7fec6020eb93d4c059a6edf19905e12a75a8d3d
cmake -S . -B build -DBUILD_EXAMPLES=OFF -DCMAKE_INSTALL_PREFIX=/opt/unitree_robotics
cmake --build build
sudo cmake --install build
```

`BUILD_EXAMPLES=OFF` avoids building the robot demos. The SDK root imports `lib/${CMAKE_SYSTEM_PROCESSOR}/libunitree_sdk2.a`; it does not build that core library from public C++ source. Match architecture and retain the SDK/third-party notices. The build prepares software; it does not verify a robot connection. [C++ project contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt) [C++ SDK2 README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md)

Create `read_state.cpp` and `CMakeLists.txt` together in a separate directory using the complete original code below. Configure that reader with the SDK prefix, then build its two explicit targets:

```cpp
// Original OpenELAB subscriber. Source reviewed; compilation/hardware NOT tested.
#include <unitree/robot/channel/channel_factory.hpp>
#include <unitree/robot/channel/channel_subscriber.hpp>
#ifdef OPENELAB_GO_STATE
#include <unitree/idl/go2/LowState_.hpp>
using State = unitree_go::msg::dds_::LowState_;
#else
#include <unitree/idl/hg/LowState_.hpp>
using State = unitree_hg::msg::dds_::LowState_;
#endif
#include <chrono>
#include <cmath>
#include <iostream>
#include <mutex>
#include <string>
#include <thread>
int main(int argc, char** argv) {
  if (argc != 3 || (std::string(argv[1]) != "0" && std::string(argv[1]) != "1")) {
    std::cerr << "Usage: read_state 0|1 interface\n"; return 2;
  }
  const int domain = std::stoi(argv[1]);
  const std::string nic = argv[2];
  if (nic.empty() || (domain == 1 && nic != "lo") || (domain == 0 && nic == "lo")) {
    std::cerr << "Check robot-facing interface; simulation requires 1 lo\n"; return 2;
  }
  using Clock = std::chrono::steady_clock;
  std::mutex mutex;
  unsigned count = 0;
  unsigned transitions = 0;
  unsigned tick = 0;
  float q = 0, dq = 0;
  auto progress = Clock::now();
  unitree::robot::ChannelFactory::Instance()->Init(domain, nic);
  unitree::robot::ChannelSubscriber<State> subscriber("rt/lowstate");
  subscriber.InitChannel([&](const void* raw) {
    const auto& state = *static_cast<const State*>(raw);
    const auto q_new = state.motor_state().at(0).q();
    const auto dq_new = state.motor_state().at(0).dq();
    if (!std::isfinite(q_new) || !std::isfinite(dq_new)) return;
    std::lock_guard<std::mutex> guard(mutex);
    if (count == 0 || tick != state.tick()) {
      progress = Clock::now();
      if (count != 0) ++transitions;
    }
    tick = state.tick(); q = q_new; dq = dq_new; ++count;
  }, 10);
  bool success = false;
  for (int second = 0; second < 10; ++second) {
    std::this_thread::sleep_for(std::chrono::seconds(1));
    std::lock_guard<std::mutex> guard(mutex);
    if (!count) continue;
    auto age = std::chrono::duration<double>(Clock::now() - progress).count();
    std::cout << "samples=" << count << " tick=" << tick << " q0_rad=" << q
              << " dq0_rad_s=" << dq << " progress_age_s=" << age << '\n';
    if (age > 2.0) { success = false; break; }
    success = transitions >= 1;
  }
  {
    std::lock_guard<std::mutex> guard(mutex);
    const auto final_age = std::chrono::duration<double>(Clock::now() - progress).count();
    success = success && transitions >= 1 && final_age <= 2.0;
  }
  subscriber.CloseChannel();
  {
    std::lock_guard<std::mutex> guard(mutex);
    const auto age = std::chrono::duration<double>(Clock::now() - progress).count();
    success = success && transitions >= 1 && age >= 0.0 && age <= 2.0;
  }
  if (!success) std::cerr << "No progressing state stream; check configuration\n";
  return success ? 0 : 1;
}
```

```cmake
cmake_minimum_required(VERSION 3.10)
project(openelab_state_reader LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
find_package(unitree_sdk2 REQUIRED)
add_executable(read_go_state read_state.cpp)
target_compile_definitions(read_go_state PRIVATE OPENELAB_GO_STATE)
target_link_libraries(read_go_state PRIVATE unitree_sdk2)
add_executable(read_hg_state read_state.cpp)
target_link_libraries(read_hg_state PRIVATE unitree_sdk2)
```

```bash
cmake -S . -B build -DCMAKE_PREFIX_PATH=/opt/unitree_robotics
cmake --build build --target read_go_state read_hg_state
```

`read_go_state` binds GO `LowState_`; `read_hg_state` binds HG `LowState_`. Both use `ChannelSubscriber::InitChannel(callback, 10)` and close the subscriber after the bounded observation. They create no command publisher or RPC client. This original C++ application was source reviewed only; compilation, linkage and runtime behavior remain untested. [C++ subscriber contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp) [C++ factory contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp) [Installed CMake target contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/cmake/unitree_sdk2Targets.cmake)

### Python preparation <a href="#python-preparation" id="python-preparation"></a>

Use a separate Python environment on the supported development host. On Ubuntu, provision `python3-venv` and `python3-pip` if they are not already available; these enable the isolated environment below. The two pinned SDK repositories have independent histories: choosing these commits makes the documentation reproducible, but does not prove that they match a delivered robot's firmware.

```bash
python3 -m venv unitree-state-env
. unitree-state-env/bin/activate
python3 -m pip install --upgrade pip
git clone https://github.com/unitreerobotics/unitree_sdk2_python.git
cd unitree_sdk2_python
git checkout 814556d15970dd2ecf1c9984e845ca02ab07e206
python3 -m pip install -e .
```

The source installation requests CycloneDDS 0.10.2, NumPy and OpenCV. If installation reports that CycloneDDS cannot be located, the upstream README gives this native-library fallback:

```bash
git clone https://github.com/eclipse-cyclonedds/cyclonedds -b releases/0.10.x
cmake -S cyclonedds -B cyclonedds/build -DCMAKE_INSTALL_PREFIX="$PWD/cyclonedds/install"
cmake --build cyclonedds/build --target install
export CYCLONEDDS_HOME="$PWD/cyclonedds/install"
```

Return to the pinned `unitree_sdk2_python` checkout and repeat `python3 -m pip install -e .` in the same shell. The upstream native branch is moving, not a fixed commit; record its resolved commit when commissioning. Do not silently upgrade the Python runtime dependency to 0.11 because a generated binding mentions 0.11. [Python SDK2 README](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/README.md) [Python dependency contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py)

### Receiving state versus requesting control <a href="#receiving-state-versus-requesting-control" id="receiving-state-versus-requesting-control"></a>

| Interface                                     | Intended role                             | What changes ownership or behavior                                                                        |
| --------------------------------------------- | ----------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| `ChannelSubscriber("rt/lowstate", LowState_)` | Receive state                             | No robot-command publisher or service action is needed                                                    |
| Go2 `SportClient`                             | Request built-in locomotion/actions       | Stand, movement, posture and other RPC methods act on the robot                                           |
| G1 `LocoClient`                               | G1 locomotion/FSM service                 | It uses service name `sport`, but a different API version and IDs from Go2                                |
| `MotionSwitcherClient.CheckMode()`            | Query active controller mode              | It is still an RPC exchange; not needed for the first subscriber                                          |
| `ReleaseMode()` / `SelectMode()`              | Change the active controller relationship | They are not passive connection checks or application cleanup                                             |
| `rt/lowcmd` writer                            | Whole-body low-level commands             | Requires correct controller ownership, fresh state, model mapping, command CRC and physical commissioning |
| G1 `rt/arm_sdk`                               | Dedicated arm-control path                | Separate command topic and blending/weight behavior; not interchangeable with `rt/lowcmd`                 |

Go2's sport API declares `1.0.0.1`; the inspected G1 locomotion API declares `1.0.0.0` and IDs in the 7000 range. A matching service name does not make their requests interchangeable. API version constants are not robot firmware requirements. [Go2 sport API](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/go2/sport/sport_api.hpp) [G1 locomotion API](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/g1/loco/g1_loco_api.hpp) [Motion switcher client](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/comm/motion_switcher/motion_switcher_client.py)

The G1 low-level example calls `CheckMode`/`ReleaseMode`, creates a `rt/lowcmd` publisher, waits for state to obtain `mode_machine`, then publishes CRC-bearing joint commands. The Go2 stand example calls `StandDown` as part of releasing control. The R1 low-level example also releases controller mode and publishes commands. These are actuation examples, even though they subscribe to state as part of their operation. Upstream loops do not establish a complete operational recovery procedure. A later control tutorial needs checked RPC results, one explicit command owner, state-age checks, exact joint limits and model-specific stop/recovery evidence. [G1 low-level source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/low_level/g1_low_level_example.py) [Go2 stand source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2/low_level/go2_stand_example.py) [R1 source contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/r1/low_level/r1_low_level_example.py)

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Copy the complete original Python formatter and reader below.
2. Prepare the pinned SDK environment and inspect the subscriber source.
3. Select the confirmed binding, domain and interface for the intended source.
4. Observe a bounded state stream and retain the result with its configuration.

### 1. Prepare the two reader files <a href="#id-1-prepare-the-two-reader-files" id="id-1-prepare-the-two-reader-files"></a>

Create `state_view.py` and `read_state.py` in the same directory from the complete code in step 2. All first-result code is included on this page; no downloadable example or private test file is required.

The author checked the original formatter, callback and bounded reader with standard-library mock samples, inert adapters, a fake clock and syntax inspection. First-message-only, repeated-tick and silent-stream cases were rejected; a late genuine tick transition was accepted, and expired progress was rejected. These are offline checks of the original application, not vendor SDK or robot tests.

### 2. Inspect the actual subscriber code <a href="#id-2-inspect-the-actual-subscriber-code" id="id-2-inspect-the-actual-subscriber-code"></a>

The reader is original OpenELAB code based on the inspected public channel contract. It requires a deliberate model/type selection, interface and domain; it stops after ten seconds. It prints the DDS tick, decoded slot count, slot-0 angle/velocity, sample count, observed tick-transition count and age since the tick last changed. Success requires at least one tick transition and fresh state metadata at completion; two identical samples cannot pass. Two seconds without tick progress is a diagnostic threshold in this example, not a manufacturer control watchdog specification. [Python channel implementation](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/core/channel.py)

Copy this formatter as `state_view.py`:

```python
"""Original OpenELAB state formatting. Standard library only; no robot connection."""
import math

def summarize_state(msg, family):
    capacity = {"go2": 20, "g1": 35, "r1": 35}[family]
    motors = msg.motor_state
    if len(motors) != capacity:
        raise ValueError("Unexpected state array capacity; check the message binding")
    q0, dq0 = float(motors[0].q), float(motors[0].dq)
    if not all(math.isfinite(x) for x in (q0, dq0)):
        raise ValueError("Non-finite joint state")
    return {"family": family, "tick": int(msg.tick), "slots": len(motors),
            "q0_rad": q0, "dq0_rad_s": dq0}


def progressing(snapshot, now):
    """Require observed change and current freshness; no manufacturer timing claim."""
    return (snapshot["error"] is None and snapshot["latest"] is not None
            and snapshot["transitions"] >= 1
            and snapshot["progress_at"] is not None
            and 0.0 <= now - snapshot["progress_at"] <= 2.0)
```

Copy this reader as `read_state.py` in the same directory:

```python
"""Original OpenELAB bounded subscriber. Source reviewed; SDK execution NOT tested."""
import argparse
import json
import threading
import time
from state_view import summarize_state, progressing

def main():
    parser = argparse.ArgumentParser()
    parser.add_argument("--robot", choices=("go2", "g1", "r1"), required=True)
    parser.add_argument("--interface", required=True)
    parser.add_argument("--domain", type=int, choices=(0, 1), required=True)
    args = parser.parse_args()
    if args.domain == 1 and args.interface != "lo":
        parser.error("This guide restricts simulation to domain 1 and loopback lo")
    if args.domain == 0 and args.interface == "lo":
        parser.error("A physical connection requires the verified robot-facing interface")

    # Deferred imports: importing this file alone does not initialize DDS.
    from unitree_sdk2py.core.channel import ChannelSubscriber, ChannelFactoryInitialize
    if args.robot == "go2":
        from unitree_sdk2py.idl.unitree_go.msg.dds_ import LowState_
    else:
        from unitree_sdk2py.idl.unitree_hg.msg.dds_ import LowState_
    ChannelFactoryInitialize(args.domain, args.interface)
    lock = threading.Lock()
    shared = {"latest": None, "count": 0, "transitions": 0, "progress_at": None, "error": None}

    def on_state(msg):
        try:
            view = summarize_state(msg, args.robot)
        except (ValueError, TypeError, AttributeError, IndexError) as exc:
            with lock:
                shared["error"] = str(exc)
            return
        with lock:
            old = shared["latest"]
            if old is None or old["tick"] != view["tick"]:
                shared["progress_at"] = time.monotonic()
                if old is not None:
                    shared["transitions"] += 1
            shared["latest"] = view
            shared["count"] += 1

    def snapshot_state():
        with lock:
            snapshot = dict(shared)
            snapshot["latest"] = dict(shared["latest"]) if shared["latest"] else None
            return snapshot

    sub = ChannelSubscriber("rt/lowstate", LowState_)
    sub.Init(on_state, 10)
    deadline = time.monotonic() + 10.0
    try:
        while time.monotonic() < deadline:
            time.sleep(1.0)
            snapshot = snapshot_state()
            if snapshot["error"]:
                raise RuntimeError(snapshot["error"])
            if snapshot["latest"] is not None:
                age = time.monotonic() - snapshot["progress_at"]
                print(json.dumps({**snapshot["latest"], "samples": snapshot["count"],
                                  "tick_transitions": snapshot["transitions"],
                                  "progress_age_s": round(age, 3)}))
                if age > 2.0:
                    raise RuntimeError("State tick stopped progressing; investigate the source")
        final_snapshot = snapshot_state()
        if not progressing(final_snapshot, time.monotonic()):
            raise RuntimeError("No progressing state stream; check binding/domain/interface/edition")
    finally:
        sub.Close()

if __name__ == "__main__":
    main()
```

The program creates a subscriber only. `sub.Close()` closes the application reader; it does not release a robot controller or command a stop. The formatter reports decoded fields and does not validate the message CRC, calibration or physical plausibility of every joint.

### 3. Choose a single source <a href="#id-3-choose-a-single-source" id="id-3-choose-a-single-source"></a>

For a previously commissioned, **SDK-enabled physical robot**, after the model/firmware/connection checks above, use the exact robot-facing interface in place of `ROBOT_INTERFACE`:

```bash
python3 read_state.py --robot go2 --interface ROBOT_INTERFACE --domain 0
python3 read_state.py --robot g1 --interface ROBOT_INTERFACE --domain 0
python3 read_state.py --robot r1 --interface ROBOT_INTERFACE --domain 0
```

Run only the line matching the connected model. These are future-use instructions; none was executed in this review. The R1 binding follows the reviewed R1 humanoid example and does not certify every R1 variant. A retail AIR/PRO or a base G1 is not made SDK-enabled by this command.

For an already prepared isolated simulator publishing the matching state type on loopback/domain 1:

```bash
python3 read_state.py --robot go2 --interface lo --domain 1
```

Use `--robot g1` or `--robot r1` only if that simulator actually publishes the corresponding model's HG state. This guide does not establish a new R1 simulator configuration. Starting a simulator or training policy is a separate workflow. MuJoCo's stock tests command torque and must not be used as passive state checks. [MuJoCo interface and configuration](https://github.com/unitreerobotics/unitree_mujoco/blob/1eb6642e3f3fdfb7fb13a9794fd6a2dd93ea0e7d/readme.md)

The equivalent C++ observation command is `./build/read_go_state 0 ROBOT_INTERFACE` for GO state, or `./build/read_hg_state 0 ROBOT_INTERFACE` for HG state. For an already matching isolated simulation use domain `1` and interface `lo`. The HG executable chooses a schema; it cannot distinguish G1 from R1 by itself.

### 4. Check the result and retain the record <a href="#id-4-check-the-result-and-retain-the-record" id="id-4-check-the-result-and-retain-the-record"></a>

**Expected result:** messages arrive, sample count increases, tick changes, angles/velocities are finite, and the reader exits after ten seconds only if a tick transition was observed and the final state metadata is fresh. Log values are measurements from the selected source; there is no universal expected angle or tick value. No example terminal output in this guide is presented as a measured robot result.

Keep the source identity, robot/edition, firmware, SDK commit, interface, domain and captured log together. A silent stream, repeated tick, wrong message capacity, exception or unconfirmed source means the checkpoint has not passed. Investigate those before any command-producing development. Ctrl-C stops this reader; it is not an emergency-stop procedure for a robot running another controller.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### No state arrives <a href="#no-state-arrives" id="no-state-arrives"></a>

Check edition/SDK entitlement and delivered firmware pairing first. Then check the physical Ethernet link, intended interface, address configuration from the exact host guide, DDS domain and selected GO/HG type. Confirm the same interface is used throughout the process. Start a new process after changing factory settings. Investigate discovery/multicast restrictions and competing simulators. Do not call `ReleaseMode()` to make a state reader work. [Python channel implementation](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/core/channel.py) [GO/HG binding notes](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/readme.md)

### G1 or R1 fails on a battery field <a href="#g1-or-r1-fails-on-a-battery-field" id="g1-or-r1-fails-on-a-battery-field"></a>

The HG low-state schema has no GO-style `power_v` or `power_a`. Subscribe using HG and inspect only documented fields. Battery services need their own exact-model evidence. [HG LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_hg/msg/dds_/_LowState_.py) [GO LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_LowState_.py)

### Why are there more state slots than robot joints? <a href="#why-are-there-more-state-slots-than-robot-joints" id="why-are-there-more-state-slots-than-robot-joints"></a>

Arrays reserve message capacity. G1 variants have different valid joints; R1's reviewed example maps 26 active joints noncontiguously into 35 slots. Use the exact mapping, not the array length, for labels or future commands. [G1 low-level source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/low_level/g1_low_level_example.py) [R1 source contract](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/r1/low_level/r1_low_level_example.py)

### Can the README's “Low-Level Status” command be used as the first check? <a href="#can-the-readmes-low-level-status-command-be-used-as-the-first-check" id="can-the-readmes-low-level-status-command-be-used-as-the-first-check"></a>

Do not rely on that heading alone. The Python README repeats `lowlevel_control.py` under both status and active torque control, and several listed paths differ from the pinned tree. Use the inspected subscriber-only reader here. Similarly, stand, ankle-swing, arm, gripper, calibration and torque-test examples can move hardware. [Python SDK2 README](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/README.md) [Go2 stand source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2/low_level/go2_stand_example.py) [G1 low-level source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/low_level/g1_low_level_example.py)

### Does a simulation result establish physical readiness? <a href="#does-a-simulation-result-establish-physical-readiness" id="does-a-simulation-result-establish-physical-readiness"></a>

No. MuJoCo retains `SportModeState` when the built-in controller is off, whereas its README says the physical robot does not. Simulator domain/interface settings can also differ from control examples. Use loopback and an explicitly matched separate domain, and retain separate simulation and physical results. The Isaac Lab manipulation repository explicitly labels its supplied weights for simulation testing. [MuJoCo interface and configuration](https://github.com/unitreerobotics/unitree_mujoco/blob/1eb6642e3f3fdfb7fb13a9794fd6a2dd93ea0e7d/readme.md) [Isaac Lab simulation scope](https://github.com/unitreerobotics/unitree_sim_isaaclab/blob/84a15e52b30953313f728b2157060d32b4f1fcbd/README.md)

### Can SDK2 replace the Go1 SDK or a standalone motor driver? <a href="#can-sdk2-replace-the-go1-sdk-or-a-standalone-motor-driver" id="can-sdk2-replace-the-go1-sdk-or-a-standalone-motor-driver"></a>

The current legacy legged SDK v3.8.6 README supports Go1; it is a different UDP API. The inspected older v3.3.1 README supports Aliengo/A1 and explicitly excludes Laikago/Go1. Standalone actuator SDK commands target motor rotor quantities and require motor-specific conversion; the whole-robot DDS joint command is a separate contract. Z1, Dex1 and D2 also have separate services or drivers. [Legacy Go1 SDK README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md) [Historical v3.3.1 README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/v3.3.1/README.md) [Actuator SDK units](https://github.com/unitreerobotics/unitree_actuator_sdk/blob/5b79a42d81cd69adac1367db79efdb972a898fd1/README.md)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                                                                    | Purpose and reviewed scope                                              |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Original Python formatter and bounded reader, included in Getting started                                                                                                                                                                                                                                                                                                   | GO/HG typed state observation; no command publisher/RPC client          |
| Original C++ reader and CMake project, included in Software and development resources                                                                                                                                                                                                                                                                                       | Two explicitly bound reader targets; build/runtime untested             |
| [C++ SDK2 README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md)                                                                                                                                                                                                                                                  | Vendor preparation and prebuild baseline at pinned commit               |
| [Python SDK2 README](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/README.md)                                                                                                                                                                                                                                        | Vendor Python setup and dependency fallback; example-path caveats above |
| [GO/HG binding notes](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/g1/readme.md)                                                                                                                                                                                                                            | Explicit GO/HG family split in G1 example README                        |
| [GO LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_LowState_.py) and [HG LowState definition](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_hg/msg/dds_/_LowState_.py) | Actual Python generated state definitions                               |
| [Go2 sport API](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/go2/sport/sport_api.hpp) and [G1 locomotion API](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/g1/loco/g1_loco_api.hpp)                                           | Distinct RPC API contracts; not first-check executables                 |
| [MuJoCo interface and configuration](https://github.com/unitreerobotics/unitree_mujoco/blob/1eb6642e3f3fdfb7fb13a9794fd6a2dd93ea0e7d/readme.md)                                                                                                                                                                                                                             | Low-level simulator behavior and domain/interface separation            |

Host drawings, wiring, firmware images and calibration procedures belong to the exact robot guide. The inaccessible support-portal pages are not represented here as successfully read resources or a complete document library. Hardware manuals collected separately in this project were not reviewed for this supporting SDK guide; their collection alone does not establish firmware compatibility.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed on 24 November 2026. C++ SDK2 snapshot: `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; Python snapshot: `814556d15970dd2ecf1c9984e845ca02ab07e206`. This page is an original explanation based on the pinned resources linked beside the relevant claims. SDK2 C++ and Python root licenses are BSD 3-Clause; preserve the applicable notices when redistributing vendor code. Third-party DDS components, model assets and other repositories have their own terms; a root SDK license is not a blanket license for all Unitree manuals or firmware. [C++ SDK license](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/LICENSE) [Python SDK license](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/LICENSE)

**Validation performed:** source inspection and original offline mock/AST checks retained in the private validation record. **Not performed:** vendor SDK execution/import, installation, C++ build, DDS/ROS runtime, simulator training, robot/hardware tests or firmware changes. Physical commissioning remains unresolved until exact edition/firmware/network and per-unit configuration are verified. No GitBook content was written during this batch.

**Related documentation:** [Unitree robot and development directory](./).
