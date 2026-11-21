---
description: >-
  ATOM-W capstone project tutorial: source-mapped objectives, required
  edition/hardware, reproducible offline prototype, and validation gates.
---

# Application 8.1 — ATOM-W Exhibition Guide

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard verified; Education SKU not verified) · **Edition scope:** Standard for interaction/navigation; **Education/verified optional gripper** for manipulation
{% endhint %}

[ATOM-W curriculum index](../) · [Chapter 8 — system integration](./) · [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html)

### Product overview

**Application 8.1: Humanoid Robot Exhibition Guide.** The course asks students to combine (1) exhibition scenario analysis, (2) human perception, (3) voice explanation and Q\&A, (4) motion-based interaction and (5) a guided-tour workflow. For ATOM-W, use the **wheeled base and head sensors**, not a biped walking controller. A basic guided explanation can be prototyped with **Standard Version**, subject to actual software/accessory availability.

The first result is an **offline scripted tour**, not autonomous operation among visitors.

### Applications

* Supervised campus exhibition wayfinding between fixed stations.
* Non-biometric person-presence detection and kiosk-style spoken explanations.
* Operator-reviewed tours combining interactive questions and safe station transitions.

### Specifications

| Subsystem                | Requirement / evidence                                                              |
| ------------------------ | ----------------------------------------------------------------------------------- |
| Locomotion               | ATOM-W wheeled chassis, model-specific navigation maps and approved speed limits    |
| Human perception         | Listed head depth/binocular sensors; detection model is external and must be tested |
| Explanation              | Listed microphone/speakers; ASR/TTS and exhibit content pipeline are external       |
| Navigation commissioning | ATOM-W V1.0 user guide describes **Map Lab**, Topo Map and path properties          |
| Model simulation         | ROS 2 `atom\_gazebo` W-P3; not evidence of safe real public navigation              |
| Visitor safety           | A human supervisor and exclusion zone are required until validated on site          |

The ATOM-W manual describes a default Map Lab path speed and recommends lowering it in the mapping workflow; use the **actual validated controller/site limits**, not a generic path speed copied from another edition.

### Hardware and connections

1. Identify available cameras, microphone, speakers, mobile base and operator controls; Standard does not require dexterous hands for a speaking guide.
2. Keep an operator able to stop the chassis and prevent arm interactions with visitors.
3. Create a mock exhibition route with clearly numbered, empty stations away from crowds. **Do not** start with an occupied museum/campus corridor.
4. Verify ATOM-W manual's navigation map/charging procedures and avoid changing PC1 software.
5. Record route map version and all approved stop/station coordinates in the **actual map frame**.

### Software and development resources

* [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) — AMR Map Lab and topology/path setup.
* [ROS 2 Atom W-P3 Gazebo](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md) — safe simulated visualization.
* [Chapter 2 perception](../atom-w-chapter-2-perception-systems.md) and [Chapter 6 voice interaction](../atom-w-chapter-6-human-robot-interaction.md) — perception and transcript-to-response components.
* [Chapter 8 integration](./) — action gateway and system test cases.

### Getting started

#### Task 1 — Design station content and safe interaction states

For each station, write title, short accessible explanation, two allowed questions, permission for any person data, audio language and required user/operator confirmation. Use states: `idle → announce → await\_answer → request\_station\_change → operator\_approval → next\_station`.

#### Task 2 — First working result: offline route script

```python
STATIONS = {
    "entrance": "Welcome to the laboratory.",
    "robotics": "This area shows robot perception and manipulation.",
    "exit": "Thank you for visiting.",
}
TOUR = ["entrance", "robotics", "exit"]

def describe(station):
    return STATIONS.get(station, "Unknown station; stop the tour.")

assert [describe(s) for s in TOUR][-1] == "Thank you for visiting."
assert "Unknown station" in describe("staff_only")
print("\n".join(f"{s}: {describe(s)}" for s in TOUR))
```

**Expected result:** all three simulated station descriptions print; an unauthorized station is rejected. This exercise intentionally has **no motor, ASR, TTS, mapping or camera dependency**.

#### Task 3 — Validate optional navigation in a controlled environment

After the operator and ATOM-W manual checks: create and inspect an approved indoor map in the manufacturer's mapping tool; in **Topo Map**, create legal route edges (the manual describes **Create Path → Double-way Line Path**) and configure **Path Properties** with site-validated speed/conditions. Confirm saved paths match the intended map. Start with static explanation without chassis motion, then a **single supervised empty-route segment** only after independent movement-stop tests.

#### Task 4 — Add live perception and speech incrementally

Subscribe to a verified RGB/depth stream, produce a person-presence signal (not identity), and use verified ASR/TTS if installed. Ensure a lost person signal, uncertain transcript, map error or unexpected obstacle leads to **pause and request operator** rather than blind navigation. Log real intervention and completion counts.

### Troubleshooting and FAQs

**The route map doesn't match the actual space:** review the AMR map download/alignment, route frame and environment change before moving. Do not infer correct paths from a Gazebo screenshot.

**A visitor request is unrecognized:** provide a bounded default response and offer help; never send unknown utterances to chassis motion.

**Do hands have to be installed?** No. A speaking/observing exhibition guide can be scoped without manipulation; hands are required only if the design adds physical object handling.

### Downloads and technical documents

* [ATOM-W physical guide and Map Lab](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html).
* [Official ATOM W-P3 simulation](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).
* [OpenELAB product editions](https://openelab.io/products/dobot-atom-w-wheeled-humanoid).

**Student deliverable:** tour requirement sheet, station content, offline route state machine test, map/site plan and a **supervised** demonstration report if hardware tests are authorized.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0 (2026-09-15), Chapter 8 application outline, user-provided document.
* [OpenELAB ATOM-W product listing, Standard and Education configurations](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [ATOM-W User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), DOBOT-authored manual mirrored online.
* [ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official DOBOT Atom ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), W-P3 model.

**Source review:** completed for draft planning. **Software execution:** not run. **Physical robot tests:** not run. No detection, localization, grasp success rate or autonomy performance is claimed here. All live movement requires site-specific physical validation and supervision.
