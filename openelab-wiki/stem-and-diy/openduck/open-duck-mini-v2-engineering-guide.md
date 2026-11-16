# Open Duck Mini v2 Engineering Guide

{% embed url="https://openelab.io/products/feetech-sts3215-c001-servo" %}

## Overview

Open Duck Mini is an open-source miniature bipedal droid inspired by the Disney BDX droid. The current revision, **Open Duck Mini v2**, stands about **42 cm tall** with its legs extended. The design, firmware, and trained walking policies are released under the **Apache-2.0** license, and the project is developed as a community hub with over 4,000 GitHub stars.

The v2 robot is driven by **14 Feetech STS3215-C001 serial bus servos** (7.4 V / 19 kg·cm, 345:1 — the variant named in the official BOM), five per leg plus four for the neck and head, controlled by a **Raspberry Pi Zero 2 W** running the onboard runtime. Walking policies are trained with reinforcement learning in MuJoCo, exported to ONNX, and executed in real time on the robot. The project also provides LeRobot data-collection scripts for imitation-learning workflows.

## Key Features

* 42 cm tall bipedal BDX-style droid
* 14 × Feetech STS3215-C001 smart serial servos (7.4 V, 19 kg·cm, 345:1) on a 1 Mbps TTL bus
* Raspberry Pi Zero 2 W embedded runtime executing ONNX policies
* Reinforcement learning stack (PPO / GAIL / behavioral cloning) with MuJoCo
* Placo walk engine with an inverse-kinematics Python API
* LeRobot experiment scripts for episode recording in HDF5
* OnShape public CAD, print and assembly guides, community mods
* Apache-2.0 licensed hardware and software

## Specifications

| Item             | Value                                                      |
| ---------------- | ---------------------------------------------------------- |
| Height           | \~42 cm (legs extended)                                    |
| Actuators        | 14 × Feetech STS3215-C001 (7.4 V, 19 kg·cm, 345:1)         |
| Servo bus        | TTL serial, 1 Mbps baud                                    |
| Legs             | 2 legs × 5 DOF (hip yaw, hip roll, hip pitch, knee, ankle) |
| Head / neck      | 4 DOF (neck pitch, head pitch, head yaw, head roll)        |
| Onboard computer | Raspberry Pi Zero 2 W                                      |
| Simulation       | MuJoCo (via MuJoCo Playground)                             |
| Policy format    | ONNX runtime                                               |
| Software license | Apache-2.0                                                 |
| Community        | Discord server linked from the GitHub repository           |

## Hardware Architecture

### Leg and Head Joints

Each leg carries five STS3215 servos arranged as hip yaw, hip roll, hip pitch, knee, and ankle. The neck and head add four more servos for expressive motion. All servos share a single TTL bus; the firmware uses 1 Mbps communication and the `pypot.feetech` Python interface.

| Joint             | Servo ID |
| ----------------- | -------- |
| right\_hip\_yaw   | 10       |
| right\_hip\_roll  | 11       |
| right\_hip\_pitch | 12       |
| right\_knee       | 13       |
| right\_ankle      | 14       |
| left\_hip\_yaw    | 20       |
| left\_hip\_roll   | 21       |
| left\_hip\_pitch  | 22       |
| left\_knee        | 23       |
| left\_ankle       | 24       |
| neck\_pitch       | 30       |
| head\_pitch       | 31       |
| head\_yaw         | 32       |
| head\_roll        | 33       |

![Wiring diagram](<../../.gitbook/assets/open duck mini v2 wiring diagram (7).png>)

### Servo Variants

The STS3215 family shares one bus protocol and the ID map above, but Feetech sells it in several electrical and gearing variants. The official Open Duck Mini v2 BOM specifies the **7.4 V / 19 kg·cm** part, sold as **STS3215-C001** (345:1).

| Variant      | Voltage / torque | Gear ratio | Where it appears                                         |
| ------------ | ---------------- | ---------- | -------------------------------------------------------- |
| STS3215-C001 | 7.4 V / 19 kg·cm | 345:1      | Official BOM; 2S pack                                    |
| STS3215-C018 | 12 V / 30 kg·cm  | 345:1      | Pre-assembled kits with a 3S pack; common torque upgrade |
| STS3215-C044 | 7.4 V            | 191:1      | Faster gearing, raised in the project issue tracker      |
| STS3215-C046 | 7.4 V            | 147:1      | Faster gearing, raised in the project issue tracker      |

{% hint style="warning" %}
Swapping servos does not change the wiring, IDs, or firmware interface, but it does change the achieved joint dynamics, so re-verify the gait and current limits after a swap. The project has not published a validated policy for the non-BOM variants.
{% endhint %}

### Printed Structure

The body, legs, and feet are 3D-printed. The feet combine a PLA shell with a TPU sole, and the trunk uses press-fit bearings and M3 heat-set inserts. The official OnShape document is the reference for the mechanical design, and the repository ships a print guide covering orientation and material choices.

## Assembly

{% stepper %}
{% step %}
## Configure the servos

Configure every servo first: assign the servo ID and set offsets with `docs/configure_motors.md` (firmware IDs must match the table above before assembly).
{% endstep %}

{% step %}
## Print the parts

Print all parts following `docs/print_guide.md`.
{% endstep %}

{% step %}
## Assemble the structure

Assemble the trunk, legs, and feet per `docs/assembly_guide.md`. Use blue threadlocker (Loctite 243) on metal-to-metal screws; never on plastic screws.
{% endstep %}

{% step %}
## Wire the robot

Wire the 14 servos to the bus per the wiring diagram above, then mount the Raspberry Pi Zero 2 W.
{% endstep %}

{% step %}
## Flash and test the runtime

Flash the embedded runtime and run a motor test before attaching the legs under load.
{% endstep %}
{% endstepper %}

## Unboxing And Quick Start

This section covers pre-assembled OpenDuckMini units. DIY builders should follow the Assembly section above instead; the software steps below apply to both.

### Bracket Assembly

{% stepper %}
{% step %}
## Assemble the display bracket

Assemble the display bracket first using M3x10 screws to fix the upper panel.
{% endstep %}

{% step %}
## Mount the duck

Lift the duck and align the raised part of the bracket with the screw slot under the duck's rear to place it steadily.

![Bracket assembly reference](<../../.gitbook/assets/unbox 02 (6).jpg>)

![Duck mounted on the bracket](<../../.gitbook/assets/unbox 03 (6).jpg>)
{% endstep %}
{% endstepper %}

### Battery Check

* To prevent over-discharge during shipping, the battery connector is intentionally disconnected. Open the back cover and reconnect it before first use.
* The duck uses a 3S LiPo battery with a low-voltage alarm connected to prevent over-discharge.
* Charge the battery when the total voltage drops below 11.1 V; a fully charged pack reads about 12.5 V.
* With a B3 charger, three red LEDs light up while charging, and three green LEDs when fully charged. Avoid overcharging or over-discharging to prevent battery damage.

![Battery connector reference](<../../.gitbook/assets/unbox 04 (6).jpg>)

![Battery and low-voltage alarm](<../../.gitbook/assets/unbox 05 (6).jpg>)

![Battery charging reference](<../../.gitbook/assets/unbox 06 (6).jpg>)

![Charger LED states](<../../.gitbook/assets/unbox 07 (6).jpg>)

### Run The Walking Demo

{% stepper %}
{% step %}
## Connect to the hotspot

Connect to the Wi-Fi hotspot named `openduckmini` hosted by the Raspberry Pi. The pre-configured Pi starts this hotspot automatically when no known network is available. If the hotspot is not visible, toggle Wi-Fi off and on to refresh the list.
{% endstep %}

{% step %}
## Open the web control page

Open the web control page in a browser at `http://192.168.12.1:5051/service`.
{% endstep %}

{% step %}
## Pair the controller

Pair the PS4-style controller by bringing it close to the duck's head and pressing the middle button; the controller's blue light confirms pairing.
{% endstep %}

{% step %}
## Start the walking demo

Click `Start` on the `duck_test` service in the web interface. The eye LEDs turn on about ten seconds after the program starts. Press the `X` button on the right side of the controller to exit pause mode, then use the left joystick to move the duck. The `□` button toggles the lights (Raspberry Pi 5 version).

![Web control interface](<../../.gitbook/assets/unbox 08 (6).jpg>)

![Controller pairing reference](<../../.gitbook/assets/unbox 09 (6).jpg>)

![Walking demo reference](<../../.gitbook/assets/unbox 10 (6).jpg>)
{% endstep %}

{% step %}
## Stop the process

Click `Stop` to terminate the process. The web interface can also reboot or shut down the Raspberry Pi.
{% endstep %}
{% endstepper %}

### Terminal Testing

In addition to the web interface, the robot can be exercised over SSH:

{% stepper %}
{% step %}
## Connect over SSH

Connect to the duck's hotspot, then SSH to the Raspberry Pi at `192.168.12.1` (username and password are both `raspios` in hotspot mode). Any SSH client works: PowerShell or MobaXterm on Windows, or a terminal on Linux/macOS.
{% endstep %}

{% step %}
## Locate the test scripts

The test scripts live in `~/open_duck_mini_ws/tools`:

```
check_antennas_with_ps4.py   check_ps4.py            turn_on.py
check_cam.py                 check_sounds.py         turn_straight.py
check_eyes.py                check_motors_pid.py     turn_off.py
check_motors.py              check_feet_contacts.py
check_motors_voltage.py
```
{% endstep %}

{% step %}
## Run the servo check

Run the servo check with `python check_motors.py`. It enables each servo at low torque one by one, reports the servo ID and current position (IDs 10–14 right leg, 20–24 left leg, 30–33 neck/head), then offers an optional small-movement test per motor:

```
Initializing hardware interface...
Successfully connected to hardware!
Turning on motors with low torque (one by one)...
✓ Low torque set successfully for motor 'left_hip_yaw' (ID: 20).
...
Attempting to read position from motor 'right_ankle' (ID: 14)...
✓ Motor 'right_ankle' (ID: 14) is responsive. Position: -0.000
--- Motor Movement Test ---
Press Enter to begin the movement test...
```
{% endstep %}

{% step %}
## Prepare for the walk test

For the walk test with pre-configured settings, pair the controller again by bringing it close to the duck's head and pressing the middle button.
{% endstep %}
{% endstepper %}

## Software Ecosystem

| Component                                | Purpose                                                                        | Link                                                                 |
| ---------------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| Open\_Duck\_Mini repository              | Design, firmware, policies, docs                                               | https://github.com/apirrone/Open\_Duck\_Mini                         |
| Open\_Duck\_Mini\_Runtime                | Onboard policy runtime for the Pi Zero 2 W                                     | https://github.com/apirrone/Open\_Duck\_Mini\_Runtime                |
| Open\_Duck\_Playground                   | MuJoCo Playground RL training                                                  | https://github.com/apirrone/Open\_Duck\_Playground                   |
| Open\_Duck\_reference\_motion\_generator | Reference motions for imitation learning                                       | https://github.com/apirrone/Open\_Duck\_reference\_motion\_generator |
| Rhoban BAM                               | Actuator identification tooling used by the project                            | https://github.com/Rhoban/bam                                        |
| LeRobot                                  | Imitation-learning framework; the repo provides HDF5 episode-recording scripts | https://github.com/huggingface/lerobot                               |

Trained walking policies are distributed as ONNX files in the repository root and can be executed with the Placo/MuJoCo scripts or on the real robot through the runtime.

## LeRobot Runtime Environment Setup

The Open Duck Mini repository includes LeRobot experiment scripts (`experiments/LeRobot/record_episodes_hdf5.py`) for recording demonstration episodes. To run them you need a working LeRobot environment. The steps below use official sources only.

{% stepper %}
{% step %}
## NVIDIA Graphics Drivers

* **Linux:** install the driver recommended by your distribution for your GPU model.
* **Windows:** download from the official NVIDIA driver page: https://www.nvidia.com/en-us/drivers/
{% endstep %}

{% step %}
## NVIDIA CUDA

* Verify driver compatibility against the official release notes: https://docs.nvidia.com/cuda/cuda-toolkit-release-notes/index.html
* Download the matching toolkit: https://developer.nvidia.com/cuda-downloads
{% endstep %}

{% step %}
## Anaconda Python Environment

Download from the official site: https://www.anaconda.com/download
{% endstep %}

{% step %}
## Clone LeRobot and install

```bash
git clone https://github.com/huggingface/lerobot.git
cd lerobot
conda create -y -n lerobot python=3.10
conda activate lerobot
pip install --no-binary=av -e ".[feetech]"
```

If the `av` package fails with `subprocess-exited-with-error`, install the FFmpeg development libraries first, then retry:

```bash
sudo apt-get install -y ffmpeg libavformat-dev libavcodec-dev libavdevice-dev \
libavutil-dev libavfilter-dev libswscale-dev libswresample-dev
pip install --no-binary=av -e ".[feetech]"
```
{% endstep %}

{% step %}
## Verify the environment

```bash
python lerobot/scripts/find_motors_bus_port.py
```

The script should run cleanly even with no motors connected; it only verifies that the environment and port-detection tooling work.
{% endstep %}
{% endstepper %}

## Best Practices And Limitations

* Configure servo IDs **before** assembly; reconfiguring IDs inside the assembled legs requires disassembly.
* The embedded runtime targets the Raspberry Pi Zero 2 W; heavy training workloads belong on a workstation with CUDA, not on the robot.
* The assembly guide is officially marked incomplete; cross-check mechanical details against the OnShape CAD.
* The `docs/prepare_robot.md` MuJoCo workflow is outdated per the maintainers; prefer MuJoCo Playground for new work.
* Walking policies are trained for flat indoor surfaces; re-train for other terrains rather than expecting zero-shot transfer.

## FAQ

<details>

<summary>Is the Open Duck Mini a commercial product?</summary>

No. It is a community open-source project. You source parts from the BOM, print the structure, and assemble it yourself.

</details>

<details>

<summary>Which servos does v2 use?</summary>

14 × Feetech STS3215-C001 serial bus servos (7.4 V, 19 kg·cm, 345:1) on a 1 Mbps TTL bus. The 12 V / 30 kg·cm STS3215-C018 is a common substitute, and it is the variant shipped in pre-assembled kits.

</details>

<details>

<summary>Can I use LeRobot with the Open Duck Mini?</summary>

The repository provides experimental episode-recording scripts for LeRobot. The main control path remains the project's ONNX policies and Placo walk engine.

</details>

<details>

<summary>Where is the bill of materials?</summary>

The official BOM is a Google Sheets document linked from the repository README; a Chinese Feishu version is also maintained.

</details>

## Resources

* GitHub repository: https://github.com/apirrone/Open\_Duck\_Mini
* OnShape CAD: https://cad.onshape.com/documents/64074dfcfa379b37d8a47762/w/3650ab4221e215a4f65eb7fe/e/0505c262d882183a25049d05
* BOM (Google Sheets): https://docs.google.com/spreadsheets/d/1gq4iWWHEJVgAA\_eemkTEsshXqrYlFxXAPwO515KpCJc/edit?usp=sharing
* Community build guide (Tnkr): https://tnkr.ai/explore/docs/open-duck-mini/open-duck-mini-v2#home
* Discord community: https://discord.gg/UtJZsgfQGe
* Servo, official BOM variant 7.4 V / 19 kg·cm (345:1) on the OpenELAB store: https://openelab.io/products/feetech-sts3215-c001-servo
* Servo, 12 V / 30 kg·cm (345:1) on the OpenELAB store: https://openelab.io/products/feetech-sts3215-c018-servo-12v
* Servo, 7.4 V (191:1) on the OpenELAB store: https://openelab.io/products/feetech-sts3215-c044-servo-7
* Servo, 7.4 V (147:1) on the OpenELAB store: https://openelab.io/products/feetech-sts3215-c046-servo

## Source Notes

* Reviewed: 2026-09-21, against the `v2` branch of `apirrone/Open_Duck_Mini` (Apache-2.0, \~4.1k stars).
* Servo family, joint IDs, and the 1 Mbps bus baud rate verified from `experiments/v2/configure_motors.py` and the runtime's `rustypot_position_hwi.py`. Neither the README nor the repository docs state the servo variant: the 7.4 V / 19 kg·cm BOM specification (retail model STS3215-C001, 345:1) is taken from the official BOM as quoted in the project issue tracker (issues #48 and #51), and the 12 V / 30 kg·cm STS3215-C018 is the variant used by pre-assembled kits and by community torque upgrades.
* Height and controller choice verified from the official README.
* The LeRobot setup commands follow the official LeRobot installation flow using official NVIDIA, CUDA, and Anaconda sources.
* LeRobot integration in the Open Duck Mini repository is experimental; treat the HDF5 recording scripts as a starting point.
* Unboxing and quick-start details follow the quick-start guide published for pre-assembled OpenDuckMini kits; hotspot name, web control URL, and default credentials apply to the pre-configured firmware and may differ on community-built units.
* No videos are included in the referenced quick-start material; all images from that guide are preserved in this page.
