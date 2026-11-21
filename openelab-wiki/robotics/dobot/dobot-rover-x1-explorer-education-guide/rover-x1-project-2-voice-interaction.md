---
description: >-
  DOBOT Rover X1 Explorer educational project tutorial; source-backed draft with
  expected results and validation boundaries.
---

# Project 2 — ROVER X1 Voice Interaction and Motion Response

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **SKU:** DOBOT-1100000231 (Basic EDU default product selection; other variant SKUs require confirmation) · **Edition scope:** Basic / Smart / Max EDU; point-foot robot
{% endhint %}

[Return to Explorer education guide](./) · [Existing ROVER X1 manual (Air/Standard/Pro scope)](../dobot-rover-x1-user-manual.md)

### Product overview

**Project 2: Voice Interaction and Motion Response.** This tutorial develops the course's three tasks: ROS 2/voice-project planning; speech acquisition and interpretation; motion and voice feedback. The manufacturer SDK **documents audio DDS topics**, but it does **not**, by itself, establish a ready-made speech-recognition model, ROS 2 bridge or safe voice-to-motion controller.

### Applications

* Acquiring audio from the robot microphone for human–robot-interaction coursework.
* Mapping recognized keywords to a restricted robot-action vocabulary.
* Building an explicit acknowledgment and rejection mechanism before enabling physical movement.

### Specifications

| Interface                    | Documented value                                          |
| ---------------------------- | --------------------------------------------------------- |
| Voice capture topic          | rt/voice/state, VoiceState                                |
| Voice playback topic         | rt/voice/cmd, VoiceCmd                                    |
| Audio stream                 | 24 kHz, 16-bit, mono                                      |
| Connection                   | Wired Ethernet and CycloneDDS                             |
| Manufacturer examples        | low\_level/python/e8\_voice\_sub.py and e7\_voice\_pub.py |
| Speech recognition and ROS 2 | Separate engineering components to implement and verify   |

Source: [DOBOT Low-Level API, E7 and E8](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md).

### Hardware and connections

* Verify the robot's microphone/audio subsystem is present and functional on the actual delivered EDU unit. A separate external microphone requires its own interface documentation.
* Connect the development PC by **wired Ethernet** in 192.168.5.0/24; low-level audio topics are not established as available through the gRPC-only Wi-Fi route.
* Keep the robot at rest while developing speech processing. Do not allow a recognition result to bypass the operator, robot safety state or motion gateway.
* For file-mode playback, the audio file path refers to a file **on the robot host**, not automatically on the development PC.

### Software and development resources

Use [the Quad SDK README](https://github.com/Dobot-Team/dobot_quad_sdk) for the official Debian/CycloneDDS package and Python wheel installation. In the SDK root, the documented workflow includes:

```bash
sudo dpkg -i dist/dds-middleware-with-thirdparty*.deb
sudo apt-get install -y cyclonedds-dev
python3 -m pip install dist/dds_middleware_python-*.whl cyclonedds opencv-python
```

Configure a **copy** of cyclonedds.xml with the actual Ethernet interface in place of USER\_PORT\_INTERFACE and export CYCLONEDDS\_URI as the absolute file URI. The interface name, DDS domain and QoS must match the installed middleware. Confirm DDS discovery before running a subscriber; do not run the low-level motor-command publishing example.

### Getting started

#### Task 1 — First working result: acquire microphone data

From the SDK root, after DDS setup:

```bash
export CYCLONEDDS_HOME=/usr/local/
export CYCLONEDDS_URI=file://"$PWD"/cyclonedds.xml
cd low_level/python
python3 e8_voice_sub.py
```

The path in CYCLONEDDS\_URI must refer to your **edited, actual config file** before changing directory.

**Expected result:** the official subscriber receives VoiceState messages and reports nonzero payload sizes while audio is present. The source documents 24 kHz, 16-bit, mono data; record actual frame sizes, timing and device behavior. Stop the subscriber with Ctrl+C. If nothing arrives, check physical microphone, Ethernet, DDS interface/domain, topic and subscription permissions.

#### Task 2 — Recognize and interpret safely

Connect the captured PCM stream to a separately selected automatic speech-recognition (ASR) engine **only after** establishing sample rate, buffering, privacy handling and timestamp alignment. First test the action mapper with text rather than robot movement:

```python
ALLOWED = {
    "stand": "balance_stand",
    "lie down": "stand_down",
    "wave": "wave_hand",
}

def interpret(transcript: str):
    return ALLOWED.get(transcript.strip().lower(), "reject")

for heard in ["stand", "wave", "turn left", "unknown"]:
    print(heard, "->", interpret(heard))
```

**Expected result:** three explicitly allowed English phrases map to named SDK methods and all other phrases reject. This is a software-only parsing illustration, **not evidence that the microphone, ASR or robot actions have been integrated**. Extend it with confidence thresholds, confirmation, cooldown, explicit human enable and a stop/abort priority.

#### Task 3 — Add feedback and supervised motion

The official **e7\_voice\_pub.py** example illustrates playback via the **rt/voice/cmd** topic (documented file or streaming modes). The example's **streaming** option supports the documented 24 kHz / 16-bit / mono PCM requirements. Build a feedback state machine: idle → heard → interpreted → confirmation → permitted action → completed / rejected / fault. A voice command must go through the same central safety gate as manual/SDK commands. Keep movement disabled during the first integration tests.

### Troubleshooting and FAQs

**VoiceState topic is silent:** verify the robot's microphone, wired DDS discovery, reader QoS and that the example is running in the SDK's low\_level/python directory.

**Voice playback file not found:** check that the source WAV/FLAC/MP3 is at the intended location **on the robot host**. For streaming mode, verify the actual PCM encoding.

**Recognition triggers unintended motion:** remove the motor-action binding; start with a rejected-by-default phrase map and logging. An unclear or incomplete utterance must never become a movement command.

### Downloads and technical documents

* [DOBOT Low-Level API — Voice Playback and Capture](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md).
* [Manufacturer SDK and audio examples](https://github.com/Dobot-Team/dobot_quad_sdk).
* [Rover X1 education hub](./).

**Student deliverable:** time-stamped audio acquisition evidence, a small allowable-command test report, a flow diagram of the action arbiter, and—only after approval—a supervised voice-response demonstration. **Not supplied by the source course:** an ASR model, ROS 2 message bridge and validated motion authorization layer.

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_ V2.0, 2026-09-30, supplied course outline.
* [OpenELAB Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [Official DOBOT Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware testing:** not run. Outcomes and diagnostic checks below are expected behavior from the cited interfaces or explicit project acceptance criteria; they are not claimed test results. Use the delivered firmware and record the actual SDK commit before performing experiments.
