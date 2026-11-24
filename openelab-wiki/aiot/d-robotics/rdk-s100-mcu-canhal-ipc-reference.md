---
description: >-
  Understand MCU1 build and recovery, CANHAL routing, IPC DMA ownership and MCU
  peripheral APIs on the RDK S100 4.0.5 platform.
---

# RDK S100 MCU1, CANHAL and IPC development reference

{% hint style="info" %}
[**RDK S100 on OpenELAB**](https://openelab.io/products/d-robotics-rdk-s100-robotics?variant=45780626964678) — **`D-Robotics-31641`**.

[**RDK S100P on OpenELAB**](https://openelab.io/products/d-robotics-rdk-s100-robotics?variant=45780626997446) — **`D-Robotics-32030`**.

Supporting development reference; these links identify its host kits.

This page describes **S100-series MCU1, CANHAL and inter-core IPC**, not an additional product or a ready-made motion controller. Begin with the [S100/S100P hardware and image guide](rdk-s100-s100p-engineering-guide.md). The source lane is **RDK S100 4.0.5**; S600 channel allocation and SocketCAN configuration are separate.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

The S100 application CPU runs Linux, while the Cortex-R52+ MCU domain runs FreeRTOS. MCU0 starts the application CPU and MCU1 and manages power; MCU1 is the application-development target. A host process can reach selected MCU peripherals through IPC, but a Linux file descriptor, an MCU controller number and a physical connector channel are different identifiers. Keep that mapping explicit before connecting a CAN or other external bus. [MCU architecture](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100), [IPC ownership](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100).

The community package contains application/configuration code and delivered libraries. MCU0 compilation and McalCdd/Service/Platform implementation are commercial-edition material; public API documentation does not mean those implementations were inspected. Preserve the supplied MCU0 image. [Community/commercial division](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/code_release?v=4.0.5\&p=RDK+S100).

## Applications <a href="#applications" id="applications"></a>

| Development task                 | Suitable first checkpoint                                          | Keep separate                                                 |
| -------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------- |
| Linux-to-MCU telemetry           | Read version/alive state, then audit IPC configuration             | Firmware running versus a valid complete application protocol |
| CAN sensor/controller connection | Isolated bus, verified transceiver/termination and passive receive | Receipt versus actuator acknowledgement or motion completion  |
| Low-latency peripheral task      | Bounded FreeRTOS task, timer and measured queue/interrupt behavior | A nominal task priority versus an end-to-end deadline         |
| MCU Ethernet/EtherCAT research   | Link/state/PDO mapping with drive outputs disabled                 | Reaching OP state versus permission to energize a drive       |
| Crash diagnosis                  | Save matching ELF/map, log and ramdump before restart              | Recovery controls versus routine read-only inspection         |

No MCU/BPU hardware feature establishes a complete robot safety function. Put application freshness, bounded queues, fault propagation and a physical stop path into the system design rather than relying on an example's infinite receive loop.

## Specifications <a href="#specifications" id="specifications"></a>

### MCU software and resource boundaries <a href="#mcu-software-and-resource-boundaries" id="mcu-software-and-resource-boundaries"></a>

| Item                      | S100 documented scope                                                                                                                                             |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CPU/OS                    | Cortex-R52+; FreeRTOS kernel 10.0.1                                                                                                                               |
| Compiler                  | GCC Arm none-eabi 10.3-2021.10                                                                                                                                    |
| Build target              | Public package: `mcu/Build/FreeRtos_mcu1_community`; documentation also describes `FreeRtos_mcu1`. Select the delivered package's target, compiler and build mode |
| Console                   | UART4 shared debug console, 921600 baud, 8N1 by default                                                                                                           |
| UART instances            | UART4–6; UART4 is not a spare peripheral port                                                                                                                     |
| PWM                       | One IP with 12 independent channels; common interrupt per IP                                                                                                      |
| Timer                     | Six instances × four 32-bit channels                                                                                                                              |
| ADC                       | One unit; channels 0–13 and 15, no channel 14; documented measurement range 100–1700 mV                                                                           |
| CAN controller capability | Up to 10 controllers; connector exposure and firmware ownership are narrower                                                                                      |
| IPC                       | Instance ownership assigned to a core; matching channel pools/configuration required at both ends                                                                 |

These are chip/software capabilities, not a connector wiring map. The public `mcu-community.tar.gz` linked under the `RDKS100-V4.0.5_20260507` directory was inspected specifically for its build parser. It uses `FreeRtos_mcu1_community`, rather than the prose guide's shorter directory. Its parser recognizes `s100`/`s100p`, `gcc` and debug/release independently; `matrix`, `B` and `mcu1` form `lite-matrix-B-mcu1.yaml`. Thus the two documented placements of `gcc` versus `mcu1` resolve to the same YAML in **this downloaded package**, rather than proving two incompatible command syntaxes. `s100p` selects the S100 configuration directory while retaining its SoC selection. This is static source inspection, not a completed build or evidence about an uninspected future package. [Public package](https://archive.d-robotics.cc/downloads/os_images/rdk_s100/RDKS100-V4.0.5_20260507/RDK_MCU_SDK/board_support_package/mcu-community.tar.gz), [MCU guide](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100), [build structure](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/MCU_build_system?v=4.0.5\&p=RDK+S100), [UART](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_uart?v=4.0.5\&p=RDK+S100), [PWM](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_pwm?v=4.0.5\&p=RDK+S100), [timer](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_timer?v=4.0.5\&p=RDK+S100), [ADC](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_adc?v=4.0.5\&p=RDK+S100).

### MCU CAN limits and timing <a href="#mcu-can-limits-and-timing" id="mcu-can-limits-and-timing"></a>

The CAN guide describes 128 mailboxes/controller, different FIFO capacities for CAN0–3 and CAN4–9, and no TTCAN support. It states 8 Mbit/s capability but only laboratory verification up to 5 Mbit/s, subject to the transceiver. This is not an 8 Mbit/s guarantee for the supplied wiring. Nominal arbitration rate, FD data rate, sample point and transceiver-delay compensation are distinct settings. [CAN timing/capability](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

For a CAN bit clock, the nominal relation is `bit_rate = clock / (prescaler × total_TQ)`, with total time quanta including fixed synchronization, propagation and both phase segments. Some register encodings store a field minus one. The guide's 1 Mbit/s arbitration / 5 Mbit/s data illustration uses different sample points and timing values; do not transplant its register numbers to a different clock. Recalculate and inspect the generated controller configuration in `Can_PBcfg.c`.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Connector and power-domain rules <a href="#connector-and-power-domain-rules" id="connector-and-power-domain-rules"></a>

On the S100 carrier, J22 is the 16-pin MCU header and J23 the mixed-voltage 100-pin MCU expansion connector. J23 includes CAN5–9 **logic TX/RX**, not directly wired differential bus pairs. Use a compatible transceiver/interface board and its own documented connector orientation. Select 1.8 V versus 3.3 V for every signal using the exact carrier revision's pinlist. A 5 V supply pin does not make adjacent digital signals 5 V-tolerant. [Mainboard electrical reference](rdk-s100-s100p-engineering-guide.md#hardware-and-connections), [official carrier guide](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/01_rdk_s100/01_rdk_s100_kit?v=4.0.5\&p=RDK+S100).

Before any bus connection:

1. Disconnect DC power and determine the carrier/expansion-board revision.
2. Draw the complete path: Linux target → IPC instance/channel → MCU controller → connector pin → transceiver → peer.
3. Verify transceiver supply, standby/enable polarity, reference ground and bus termination. Install termination at the actual bus ends; do not enable every board's resistor by habit.
4. Keep external actuators de-energized. Confirm the peer's bitrate, standard/extended ID format and classic/FD mode before receiving.
5. Check boot-strapping/pull-state constraints and power sequencing so an external peripheral cannot backfeed or override a boot-sensitive MCU pin.

**Expected result:** an unambiguous mapping and powered-down harness that matches the actual hardware documentation. No new wiring was fabricated for this reference.

### Peripheral ownership before pinmux <a href="#peripheral-ownership-before-pinmux" id="peripheral-ownership-before-pinmux"></a>

MCU0 owns power-critical modules and selected instances. The public allocation table assigns I2C6/7 to MCU0 and I2C8/9 to MCU1; default IPC instance 8 participates in MCU1 boot, instance 7 in IpcBox, and other reserved services include time synchronization and OTA. Reusing an instance because its channel appears quiet can break boot or sleep. An IPC interrupt belongs to the instance's selected MCU core, not every core. [Allocation table](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100), [IPC use table](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100).

The Port subsystem sets pin function, input enable, Schmitt trigger, slew, pull and drive strength. The Port index, GPIO number and physical-header pin are separate. Linux `pinctrl` settings for a main-domain signal do not configure MCU-owned pins. For the S100 main header's I²C-expander GPIO, MCU Port configuration is irrelevant. [Port configuration](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_port/development_manual?v=4.0.5\&p=RDK+S100), [Port application](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_port/user_manual?v=4.0.5\&p=RDK+S100).

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Build, interrupt routing and release coherence <a href="#build-interrupt-routing-and-release-coherence" id="build-interrupt-routing-and-release-coherence"></a>

The SCons build uses `SConstruct`, module `SConscript` files, board YAML selection, GCC settings and a model-specific linker script. Keep all of these with the exact MCU package. The guide's SCons-version references differ between its architecture description and installation prerequisite; inspect the delivered build requirements instead of forcing an arbitrary host version. Debug artifacts include ELF/map and a binary under the configured S100 output directory. Keep those files with the device's actual firmware version for later stack/crash decoding. [Build system](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/MCU_build_system?v=4.0.5\&p=RDK+S100).

The current MCU1 entry path initializes core-specific interrupts, logging, IPC/power state and FreeRTOS tasks. Core1 participates in CAN data handling and stop/deep-sleep transitions. Removing apparently idle initialization or routing an interrupt to multiple owners can produce faults that resemble random packet loss. Give interrupt handlers bounded work and move blocking processing into tasks. [MCU1 core paths](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100), [FreeRTOS interrupt table](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/FreeRTOS_development?v=4.0.5\&p=RDK+S100).

### CANHAL configuration and API behavior <a href="#canhal-configuration-and-api-behavior" id="canhal-configuration-and-api-behavior"></a>

S100 Acore does not directly operate CAN through the documented S600 SocketCAN driver. CANHAL forwards through IPCF. Three configuration files determine the host route:

| File                | Meaning and fields to verify                                                                                    |
| ------------------- | --------------------------------------------------------------------------------------------------------------- |
| `nodes.json`        | Logical `target`, unique ID, `enable`, access `mode` (`R`, `W`, `RW`), clock source and `io_channel.channel_id` |
| `ipcf_channel.json` | ID-to-channel mapping; library path, instance, channel, buffer sizes, device path and receive timeout           |
| `channels.json`     | Location of the IPCF configuration; paths resolve from the application's working/configuration context          |

The S100 **Software Architecture allocation table** assigns the following routes. IPC instances 0 and 4 both carry CAN traffic; controller numbering does not imply one shared instance. [Authoritative allocation table](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

| S100 controller | IPC instance | IPC channel |
| --------------- | ------------ | ----------- |
| CAN5            | 0            | 4           |
| CAN6            | 0            | 6           |
| CAN7            | 4            | 7           |
| CAN8            | 4            | 2           |
| CAN9            | 0            | 3           |

The same chapter later contains sample JSON with contradictory instance fields. Treat that JSON as a configuration-format illustration, **not an authoritative allocation**: reconcile every route with the table and the matching installed MCU configuration before enabling traffic. A stale target name or sample instance must not replace that check. The simple S100 `bypass` example uses instance 0/channel 6; S600 examples have separate allocations. [Allocation and conflicting sample context](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

`canInit()` precedes traffic. Send/receive use the configured target plus frame/package metadata; receive is documented as nonblocking in the example. A negative `CAN_TRY_AGAIN` is a resource/retry condition, not a valid frame. Bound retry count/time and yield instead of busy-spinning forever. Preserve ID, payload length, frame flags, sequence/package count and both clock domains' timestamps; receipt of an IPC package is not proof every expected CAN frame arrived. Deinitialize when finished. [CANHAL example/control flow](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

| CANHAL error area                | Concrete diagnostic                                                                                 |
| -------------------------------- | --------------------------------------------------------------------------------------------------- |
| `-100` / `-101`                  | Invalid/missing config: JSON syntax, duplicate/empty target, current directory and all three files  |
| `-200`                           | Target absent or disabled; compare the exact string passed by the application                       |
| `-201…-206`                      | Channel ID/mode/initialization mismatch; resolve node → IPCF route                                  |
| `-301` / `-302`                  | HAL initialization/configuration: MCU1 state, plugin load, `/dev/ipcdrv`, matching instance/channel |
| `-303` and related device errors | Inspect the actual error enum/log and device state; do not call all negative receives “no CAN data” |
| `-400…-409`                      | Protocol/buffer/parameter/latency failures: retain the frame/package context and counters           |

Do not fix a configuration or firmware problem by simply suppressing logs. [Exact error categories and corrective checks](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

### Filtering and batching change observable latency <a href="#filtering-and-batching-change-observable-latency" id="filtering-and-batching-change-observable-latency"></a>

CAN standard IDs are 11 bits (`0…0x7FF`); extended IDs are 29 bits (`0…0x1FFFFFFF`). The documented filters support masked single ID, inclusive range and two-ID selection; standard/extended filters are separate and filters within a format are ORed. High mode bits in a filter word are not part of the received ID. Oversized IDs can be truncated by the driver configuration, so validate at the application boundary. [Filter encoding and ID limits](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

MCU-to-Acore batching trades interrupt/IPC overhead for waiting time. The guide's default merge count is 1 and timeout 1000 µs. A higher threshold waits until enough frames arrive or the timeout flushes a partial group. Measure tail latency and loss under sparse traffic as well as saturation; a faster bulk throughput result can conceal an unacceptable per-frame control delay. [Merge policy](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

### IPC and IpcBox contracts <a href="#ipc-and-ipcbox-contracts" id="ipc-and-ipcbox-contracts"></a>

`Ipc_MDMA_Init` uses an instance configuration after DMA initialization. Verify the remote core is ready, open the instance, then send/poll/close/deinitialize in a consistent ownership order. Matching control/data shared-memory addresses, channel IDs, pool count and buffer size are required on both endpoints. The default addresses in an example are not a free memory allocation for an application. [IPC configuration and APIs](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100).

`Ipc_MDMA_SendMsg(instance, channel, size, buffer, timeout)` is synchronous and returns status such as illegal parameter, not initialized, channel not open, timeout or no memory. Send buffers and size must obey the documented **16-byte alignment** constraints. Only two MDMA send channels exist; multi-task/core users need serialized ownership. The guide distinguishes polled send DMA from receive interrupts and requires compatible interrupt priorities. A function that returned success does not validate the application payload schema. [DMA restrictions](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100).

IpcBox exposes RunCmd/UART/I2C/SPI passthrough. Instance 7 and an agreed function/message format carry requests to the MCU; a host-side channel configuration must match its peer implementation. Limit command scope and validate request length, bus/device address, return status and timeout before dispatch. Do not expose the example's remote command execution to arbitrary network/model text. Use a known benign read first; separate transport acknowledgement from peripheral read success. [IpcBox functions](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100), [Acore IPC driver](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/linux_development/driver_development_super/driver_ipc?v=4.0.5\&p=RDK+S100).

### Other MCU modules: parameters and lifecycle <a href="#other-mcu-modules-parameters-and-lifecycle" id="other-mcu-modules-parameters-and-lifecycle"></a>

| Module             | API/data flow and material limit                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| UART               | Init → baud/format → synchronous or asynchronous TX/RX → status/bytes transferred → deinit. DMA buffers require 64-byte alignment; do not reuse them before completion. UART4 is the shared console. [UART](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_uart?v=4.0.5\&p=RDK+S100)                                                                                                                   |
| PWM                | Init → `Pwm_SetPeriodAndDuty` / `Pwm_SetDutyCycle` → inspect output/notifications → idle/deinit. Duty uses **0x0000…0x8000** in the documented API, not a literal 0…100 percentage; period granularity is the peripheral clock and the documented counter maximum is 4294967295. [PWM](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_pwm?v=4.0.5\&p=RDK+S100)                                         |
| SPI                | Configure channels/jobs/sequences, set internal/external buffers, transmit, inspect sequence/job status and read results. DMA length is 8-byte aligned, buffers 64-byte aligned and each channel transfer ≤4096 bytes. Slave operation over 9 MHz requires DMA in the guide. [SPI](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_spi?v=4.0.5\&p=RDK+S100)                                             |
| I2C                | Initialize the configured controller/clock, select address and transaction direction/length, execute and check completion/error. Check slave-address convention and shared ownership; a probe ACK does not establish sensor initialization. MCU0's I2C instances are not application spares. [I2C](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_i2c?v=4.0.5\&p=RDK+S100)                             |
| ADC                | Complete POST, initialize group/result buffer, start software conversion or configure the single permitted hardware/inject group, then check status/read/notification. Keep input within the documented 100–1700 mV measurement range; ambient shifts beyond ±20 °C require calibration. This is not a 3.3 V ADC rating. [ADC](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_adc?v=4.0.5\&p=RDK+S100) |
| ICU/GPIO interrupt | Configure Port first, choose rising/falling/both/level trigger, bind the matching group IRQ and clear/service status. A persistent level can retrigger until the condition clears. [ICU](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ICU?v=4.0.5\&p=RDK+S100)                                                                                                                                       |
| GPT timer          | Configure a supported instance/channel, duration/mode and notification; start, inspect elapsed/remaining and stop. The S100 has six × four channels, not S600's ten instances. [Timer](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_timer?v=4.0.5\&p=RDK+S100)                                                                                                                                       |
| Watchdog           | Instance-specific Wdg0/1/2 configuration, mode and trigger condition; design the servicing deadline and fault response before enabling. Feeding a watchdog in an unconditional high-priority loop can hide an application deadlock. [Watchdog](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_watchdog?v=4.0.5\&p=RDK+S100)                                                                            |
| LIN                | Init → frame request/status → sleep/wakeup where configured. An external LIN transceiver is required; logic TX/RX is not a LIN bus wire. Match checksum, ID and schedule to the peer. [LIN](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_lin?v=4.0.5\&p=RDK+S100)                                                                                                                                    |
| Ethernet           | Configure/activate controller, obtain a TX buffer, transmit and observe confirmation; receive via configured buffers/notifications. Described MCU MAC capability is up to 1 Gbit/s; configured RX buffer must include the frame/header/FCS size. [Ethernet](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_eth?v=4.0.5\&p=RDK+S100)                                                                    |
| EtherCAT           | SOEM-backed FreeRTOS flow: discover slaves → map PDOs → configure distributed clocks → verify states/working counter → periodic process-data exchange. `EtherCAT_SlaveInfo_Start` and SDO/PDO access can affect real equipment; inspect read-only state before OP/output writes. [EtherCAT](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ethercat?v=4.0.5\&p=RDK+S100)                               |

These summaries preserve module-specific choices and limits; complete enum/structure definitions remain in each linked API page and the matched SDK headers. A library's API description is not a claim that its proprietary low-level implementation was read.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Passive MCU health record <a href="#passive-mcu-health-record" id="passive-mcu-health-record"></a>

1. Complete normal S100 boot and record Linux/image and carrier revisions. Disconnect external drives and custom bus connections.
2. Enumerate the remoteproc paths actually provided by the image. Read `name`, `state`, `alive`, `mcu_version` and `sbl_version` where present; do not write `firmware` or `state` during this check.
3. Save MCU0/MCU1 logs and load data only from existing readable nodes. `alive` updates about once a second; a single sample is not a timing guarantee.
4. Compare a second health sample and retain the exact package/ELF identity before modifying a task or bus route.

```bash
ls -l /sys/class/remoteproc
ls -l /proc/remoteproc_mcu0 /proc/remoteproc_mcu1
```

**Expected result:** identified MCU domains and version/state information consistent with the image. The guide describes `cpuloads` task priority/stack/run counts, but retrieving it has an approximately one-second data-copy delay and is not a high-rate control-loop measurement. [Readback nodes and log paths](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100).

### Original offline CANHAL configuration audit <a href="#original-offline-canhal-configuration-audit" id="original-offline-canhal-configuration-audit"></a>

Save as `audit_s100_can_routes.py`. It reads **copies** of `nodes.json` and `ipcf_channel.json`; it opens no device, sends no CAN frame and executes no SDK code.

```python
import argparse
import json
from pathlib import Path

parser = argparse.ArgumentParser(description="Audit copied CANHAL IPCF routes")
parser.add_argument("nodes", type=Path)
parser.add_argument("channels", type=Path)
args = parser.parse_args()
nodes = json.loads(args.nodes.read_text(encoding="utf-8"))["nodes"]
channels = json.loads(args.channels.read_text(encoding="utf-8"))["channels"]
by_id = {}
for item in channels:
    key = item["id"]
    if key in by_id:
        raise ValueError(f"duplicate IPCF id {key}")
    by_id[key] = item["channel"]
seen = set()
for node in nodes:
    if not node.get("enable", False):
        continue
    target = node["target"]
    if not isinstance(target, str) or not target or target in seen:
        raise ValueError("empty or duplicate target")
    seen.add(target)
    if node["mode"] not in {"R", "W", "RW"}:
        raise ValueError(f"invalid access mode for {target}")
    route = node["io_channel"]
    if route["device_type"] != "ipcf":
        raise ValueError(f"{target} is not the S100 IPCF route under review")
    channel = by_id[route["channel_id"]]
    print(target, "-> instance", channel["instance"],
          "channel", channel["channel"], "device", channel["dev_path"])
```

Run `python3 audit_s100_can_routes.py copied_nodes.json copied_ipcf_channel.json`. **Expected result:** one line per enabled unique target with the actual instance/channel/device. Missing IDs, malformed JSON and invalid/duplicate targets fail visibly. The audit does not prove matching MCU firmware, buffer address, bitrate, GPIO or hardware support; compare the output with the MCU allocation before enabling a bus. [Configuration schema](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

### From build artifacts to a bounded MCU1 experiment <a href="#from-build-artifacts-to-a-bounded-mcu1-experiment" id="from-build-artifacts-to-a-bounded-mcu1-experiment"></a>

1. Obtain the matching public MCU1 package/toolchain and retain package hashes. Use the inspected public package's `FreeRtos_mcu1_community` directory; confirm the same parser/configuration before using the command below.
2. Select S100/MCU1/GCC and debug or release. Inspect its board YAML, linker map and reserved services before adding a task. Build on the documented host, outside this documentation task.
3. Retain the generated ELF/map/binary. Compare their target and memory layout with the selected image; do not rename a different platform's ELF to look compatible.
4. Before transferring/restarting firmware, de-energize external outputs and establish a recovery image/console. The documented host control point is `/sys/class/remoteproc/remoteproc_mcu0`: MCU0 mediates MCU1 startup using the selected `/lib/firmware` ELF.
5. After a controlled stop, **wait until the MCU reaches WFI/standby before starting again**. An early reload can overwrite still-running SRAM code. Check version/alive/log and the intended task result before reconnecting peripherals.

For the inspected public package, the source-supported S100 debug invocation is:

```bash
cd mcu-community/mcu/Build/FreeRtos_mcu1_community
python3 build_freertos.py lite matrix B s100 mcu1 gcc debug
```

For S100P the parser supports `s100p`; retain that option's generated target/artifacts and verify its supplied libraries rather than renaming an S100 output. The script can download/extract a compiler and invoke SCons, so reviewing it is not equivalent to running it. No build command was executed here.

**Expected result:** the correct MCU1 image reports its version and the new task's non-actuating result without disrupting MCU0/boot. This build/start sequence was source-reviewed only; no firmware replacement was performed. [Build/start/stop and WFI requirement](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### A receive call fails even with a quiet bus <a href="#a-receive-call-fails-even-with-a-quiet-bus" id="a-receive-call-fails-even-with-a-quiet-bus"></a>

Resolve the error layer in order: JSON/current directory → target/access mode → IPCF plugin/device → MCU1 readiness → instance/channel → transceiver/termination → bitrate/filter/frame format. `-CAN_TRY_AGAIN` needs a bounded retry strategy; a different negative code needs its actual enum meaning. Preserve logs before changing configuration. [CANHAL diagnosis](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100).

### Data arrives in bursts or control latency grows <a href="#data-arrives-in-bursts-or-control-latency-grows" id="data-arrives-in-bursts-or-control-latency-grows"></a>

Check merge threshold/timeout, queue depth, CPU load and receive scheduling. Separate CAN wire timestamps from MCU/SoC package timestamps and confirm synchronization before subtracting them. Reduce copying/handler work and measure maximum latency under contention; do not assume a faster mean receive rate proves a better deadline. [Batching](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100), [DMA/interrupt ownership](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100).

### MCU1 will not restart or a crash loses evidence <a href="#mcu1-will-not-restart-or-a-crash-loses-evidence" id="mcu1-will-not-restart-or-a-crash-loses-evidence"></a>

Save the matching ELF/map, `/proc` logs and crash registers before stopping/reloading. MCU0/MCU1 share the crash-info region; simultaneous faults can invalidate the saved data. MCU0 exception recovery restarts the system, whereas MCU1 exception handling and normal remoteproc stop/start are different flows. Follow the current WFI/standby sequence and do not disable context-saving to make a restart appear faster. [Ramdump](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ramdump?v=4.0.5\&p=RDK+S100), [current exception paths](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100).

### A new pin function breaks sleep or boot <a href="#a-new-pin-function-breaks-sleep-or-boot" id="a-new-pin-function-breaks-sleep-or-boot"></a>

Revert the last Port/configuration change, disconnect the new peripheral with power off, and compare pull/default levels and instance ownership. Restore only the matched image/MCU components. Do not replace MCU0 or alter boot-strapping pins as an exploratory fix. [Port](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_port/development_manual?v=4.0.5\&p=RDK+S100), [MCU ownership](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/basic_information?v=4.0.5\&p=RDK+S100), [carrier limits](https://d-robotics.github.io/rdk_s_doc/en/01_Quick_start/01_hardware_introduction/01_rdk_s100/01_rdk_s100_kit?v=4.0.5\&p=RDK+S100).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                     | Purpose                                                               |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| [S100/S100P canonical guide](rdk-s100-s100p-engineering-guide.md)                                                                                            | Model, power, revision and image preparation                          |
| [MCU source delivery directory](https://archive.d-robotics.cc/downloads/os_images/rdk_s100/RDKS100-V4.0.5_20260507/RDK_MCU_SDK/)                             | Matched public application package/firmware listing                   |
| [Community/commercial delivery description](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/code_release?v=4.0.5\&p=RDK+S100) | What is actually provided as source versus libraries/private material |
| [MCU build-system guide](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/MCU_build_system?v=4.0.5\&p=RDK+S100)                | YAML, toolchain settings, linker and output structure                 |
| [CAN/CANHAL API and examples](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_can?v=4.0.5\&p=RDK+S100)                    | Filters, bit timing, JSON, errors and MCU controller APIs             |
| [IPC/IpcBox API](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ipc?v=4.0.5\&p=RDK+S100)                                 | Shared-memory ownership, DMA restrictions and passthrough             |
| [MCU ramdump guide](https://d-robotics.github.io/rdk_s_doc/en/Advanced_development/mcu_development/mcu_ramdump?v=4.0.5\&p=RDK+S100)                          | Exception evidence and recovery limitations                           |
| [Official S100 downloads](https://d-robotics.github.io/rdk_s_doc/en/Quick_start/download?v=4.0.5\&p=RDK+S100)                                                | Compiler, pinlists, image and application-package links               |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

This reference summarizes the public S100 **4.0.5** MCU documentation reviewed on **24 November 2026**. Commercial/NDA implementation code and full archive contents were not claimed as read. Only the named public build-parser member was inspected from the downloaded community archive; the directory/argument-order difference is resolved for those exact bytes, and future packages require a fresh check. Passive health/configuration procedures do not depend on a custom firmware build.

Only original offline JSON examples and syntax checks may be exercised locally. **No SDK/vendor build, ROS stack, MCU firmware, CAN traffic, EtherCAT command or physical hardware test was run.** A source-reviewed API summary is not a measured real-time guarantee or proof that an application is safe to actuate.

**Related guides:** [D-Robotics boards, modules and peripherals](./).

* [D-Robotics RDK S100/S100P — hardware, image and BPU development](rdk-s100-s100p-engineering-guide.md)
* [D-Robotics RDK S100 Camera Expansion Board: MIPI/GMSL wiring and first video](rdk-s100-camera-expansion-board.md)
* [D-Robotics RDK S100 MCU Port Expansion Board: pinout, CANHAL and first readback](rdk-s100-mcu-port-expansion-board-reference.md)
* [RDK S100 Camera Expansion Board 12L: PoC, pinout and capture reference](rdk-s100-camera-expansion-board-12l-reference.md)
