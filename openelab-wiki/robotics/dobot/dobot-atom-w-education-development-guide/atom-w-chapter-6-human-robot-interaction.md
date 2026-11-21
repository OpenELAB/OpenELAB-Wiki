---
description: >-
  DOBOT ATOM-W education chapter with model-specific hardware scope, practical
  workflow, validation checkpoints and source links.
---

# Chapter 6 — ATOM-W Perception and Voice Interaction

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard Version verified; Education SKU pending) · **Versions:** Standard / Education · **Platform:** wheeled humanoid
{% endhint %}

[ATOM-W course index](./) · [ATOM-W physical-operation guide](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) · [Official ROS 2 package](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 6: Humanoid Robot Interaction Practice** translates **6.1 Robot Perception Practice** (vision, human/object recognition, tracking) and **6.2 Voice Interaction Practice** (acquisition, recognition, command interpretation, synthesis and response) into a supervised ATOM-W development sequence.

This chapter demonstrates **interaction software first, physical robot action only after separate validation**. The course's topics are learning objectives; they do not establish that a speech recognizer, speaker API, face identifier or person follower is preinstalled.

### Applications

* Human-presence detection, object recognition and privacy-conscious pose/gesture studies.
* Offline voice-command understanding with an explicit command whitelist.
* Speech/GUI response and interactive exhibition-guide prototypes.
* Testing timeout, ambiguous commands and operator interruptions.

### Specifications

| Module                   | ATOM-W hardware / software scope                                                                                                     |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Vision                   | Head depth + binocular camera on both editions; optional wrist depth only Education                                                  |
| Audio input/output       | Head/platform microphone and two speakers listed                                                                                     |
| High-level control       | C++ Atom SDK includes `gcontrol\_rpc\_client.h` for voice/device functions; current method names must be checked before code binding |
| Speech recognition & TTS | Not specified as ready-made executable software by supplied course outline                                                           |
| Physical motion          | All requested actions must pass an operator-approved motion gateway and stop checks                                                  |
| Human recognition        | Detection and pose are distinct from **identifying a particular person**; respect consent and retention                              |

### Hardware and connections

1. Inspect and obtain calibrated drivers for the camera actually installed. Keep the chassis parked while testing.
2. Check microphone permissions and speaker output without assuming a particular ALSA device number or ROS voice topic.
3. If testing person tracking, get permission from participants and avoid crowds, public-space biometric identification and unreviewed uploads.
4. Ensure the operator has immediate access to ATOM-W's actual physical emergency stop, and confirm its behavior per the V1.0 user guide.

### Software and development resources

* [ATOM-W SDK application guide V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) — model-specific interfaces.
* [DOBOT C++ SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) — `gcontrol\_rpc\_client.h` and other interface source.
* [DOBOT ROS 2 package](https://github.com/Dobot-Arm/dobot_atom_ros2) — states, simulation and examples.
* ASR/TTS, object recognition, detection and pose-estimation models must be sourced and versioned **separately**; the uploaded outline names technologies, not a reference model.

### Getting started

#### Task 1 — Establish perception output

Capture a **consented or synthetic** still frame with the installed camera's verified driver. Label a person/object bounding box and document image frame, confidence and timestamp. Success: at least one visual annotation with correct units and the model/driver version; no motor motion required.

#### Task 2 — First working result: an offline voice-to-action decision

Use a **text transcript fixture**, not real speech or a robot control function:

```python
ALLOW = {"hello": "greet", "tell me about this": "describe_exhibit"}
def interpret(text, operator_enabled):
    key = text.lower().strip()
    return ALLOW[key] if operator_enabled and key in ALLOW else "reject"

assert interpret("hello", True) == "greet"
assert interpret("move forward", True) == "reject"
assert interpret("hello", False) == "reject"
print("Offline command mapping passed")
```

**Expected result:** assertions pass; `hello` maps to a speaking/GUI action, unknown movement phrases are rejected, and an operator-disabled system rejects all. This does **not** prove ASR accuracy or TTS output.

#### Task 3 — Add real ASR/TTS in stages

1. Choose a versioned and properly licensed ASR model and record the microphone PCM format with known prompts.
2. Measure transcription confidence, latency and wrong-command cases.
3. Add a separate versioned TTS system; verify speaker volume and safe use.
4. Connect only **non-motion feedback** (screen/speaker) first.
5. After formal system review, integrate permitted robot actions via the same safeguarded command manager used in Chapter 8. No direct ASR → DDS motor command path.

#### Task 4 — Behavior and gesture evaluation

Test neutral posture versus wave, side-on posture, partial occlusion and lighting changes on a small labeled set. Compare precision, recall and processing delay, not anecdotal successes. If a person disappears from camera view, do not initiate pursuit or navigation by default.

### Troubleshooting and FAQs

**The microphone is silent:** inspect actual host/audio driver, permissions, hardware mute and recording sample format. A documented microphone does not identify an installed capture device by name.

**Voice recognition is inconsistent:** inspect noisy environment, language model, confidence threshold and command set; ambiguous input must map to reject rather than motion.

**Vision shows people but the robot cannot follow them:** detection does not provide collision-safe navigation or tracked identity; those are separate unvalidated modules.

### Downloads and technical documents

* [ATOM SDK `gcontrol\_rpc\_client.h` source location](https://github.com/Dobot-Arm/dobot_atom_sdk/tree/main/rpc).
* [ATOM SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [OpenELAB hardware/edition list](https://openelab.io/products/dobot-atom-w-wheeled-humanoid).

**Student deliverable:** labeled vision examples, speech phrase test matrix, command rejection logs and an offline Q\&A/feedback demonstration.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, Tutorial Guide V2.0 (2026-09-15), supplied source; chapter mapping as listed above.
* [OpenELAB, ATOM-W product/edition configuration](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT, ATOM-W Wheeled Humanoid Robot User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) (manufacturer document mirrored by a third party).
* [DOBOT, ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official Atom C++ SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) and [ROS 2 source](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** completed for documentation draft. **Software execution:** not run. **Hardware validation:** not run. Real ATOM-W trials require a confirmed firmware, installed edition and a supervised, manufacturer-compliant safety procedure.
