---
description: >-
  Understand Unitree D1-T two-arm and four-arm kits, D1 component
  specifications, power and connector limits, and an offline inventory check
  before integration.
---

# Unitree D1-T Teleoperation Kits: Edition and Development Guide

{% hint style="info" %}
**Unitree D1-T — unlisted manufacturer reference.** No exact OpenELAB product URL or SKU was found in the reviewed 67-product Unitree catalog. Unitree offers a Dual-Arm AI Teleoperation Kit (Standard Edition) and a Quad-Arm AI Teleoperation Kit (Full Edition). Confirm the kit edition and delivered bill of materials; the component specification table is labeled **D1**, not a standalone D1-T arm SKU. [Manufacturer D1-T page](https://www.unitree.com/D1-T/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

D1-T is Unitree's teleoperation kit for embodied-intelligence research and data acquisition. The manufacturer describes two-arm and four-arm editions and gives specifications for a six-axis D1 arm with one gripper. Keep the kit identity, individual arm identity and assigned control role as separate records. An edition name alone does not establish which arms are leaders or followers, which cameras are included, or how many power supplies ship. [Official kit and component descriptions](https://www.unitree.com/D1-T/)

This reference supports edition selection and an offline inventory/data-design checkpoint. An exact public D1-T protocol, SDK release, calibration procedure and wiring pinout were not established from accessible model-specific documents. Those gaps prevent a reproducible live-control recipe. Z1, D2, R1-7a and UniArmL1 software must not be assumed compatible because the manufacturer or joint count is similar.

## Applications <a href="#applications" id="applications"></a>

The published capabilities are position, velocity and force control through low-level and high-level interfaces, six-axis manipulation with gripper control, and expansion with external cameras or mobile robot chassis. These support planning teleoperation demonstrations, paired observations/actions for imitation learning, and camera/arm timestamp studies. The manufacturer does not provide a verified timing budget, dataset format, API signature or supported learning framework on this page. [D1-T features](https://www.unitree.com/D1-T/)

A useful development task is to design a session record that distinguishes arm axes from grippers, associates every physical arm with an asset ID and side/role, and stores calibration and software revisions separately. Before collecting demonstrations, an integrator must establish time synchronization, dropped-sample handling, command ownership and what happens when the teleoperation input disappears. The offline example below begins with the identity checks that can be completed without guessing those device behaviors.

## Specifications <a href="#specifications" id="specifications"></a>

These are the **D1 component-table values on the D1-T kit page**, not totals for a complete two- or four-arm system. [Manufacturer table](https://www.unitree.com/D1-T/)

| Parameter                    | Published D1 component value                                 | Integration meaning                                                   |
| ---------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------------- |
| Arm mass                     | About 2.37 kg                                                | Kit mass and mounting accessories not specified                       |
| Degrees of freedom           | 6 axes + 1 gripper                                           | Store six joint angles separately from gripper state                  |
| Payload                      | 500 g                                                        | Complete load envelope / center-of-gravity condition not supplied     |
| Reach without / with gripper | 550 / 670 mm                                                 | Preserve the end-effector condition in workspace comparisons          |
| Supply                       | 24 V, 2.5 A; maximum 5 A                                     | Per component-table context; not a whole-kit power budget             |
| Power                        | 60 W                                                         | No published kit-wide peak/continuous breakdown                       |
| Motor type                   | Bus servo                                                    | Does not identify a public command packet format                      |
| Connections                  | DC5.5–2.1 power; RJ45 communication; Type-C serial debugging | Connector shape does not prove pinout, Ethernet or USB power delivery |

The manufacturer [joint illustration](https://oss-global-cdn.unitree.com/static/ef65f92be2674b4996dbad757c8d24d5_1904x1802.png) labels **Joint0–Joint6**, covering the six-axis/gripper assembly. Its printed spans are Joint0 ±135°, Joint1 ±90°, Joint2 ±90°, Joint3 ±135°, Joint4 ±90°, Joint5 ±135° and Joint6 −40° to +20°. This is the figure’s numbering, not a verified SDK motor-ID or calibrated joint-order definition. Use it to orient the arm against a manufacturer-confirmed zero convention; a picture alone does not define calibrated encoder signs or software soft limits. Diagram © Unitree Robotics. The page does not state repeatability, encoder resolution, command frequency, torque limits, operating temperature or an ingress-protection rating. Do not import these from other arms or bus-servo products.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

Build a pre-power kit inventory with edition, arm count, arm labels/serials, grippers, bases, supply labels, cables, adapters and any separately supplied cameras or teleoperation controls. Record missing or optional items explicitly. The Standard/Full distinction establishes two/four arms, but the published page does not establish a universal included-component list or leader/follower wiring topology. [Kit editions and hardware description](https://www.unitree.com/D1-T/)

| Interface           | Verified role             | Confirmation needed before connection                                   |
| ------------------- | ------------------------- | ----------------------------------------------------------------------- |
| DC5.5–2.1           | Power supply connector    | Polarity, mating plug, protection, approved supply and kit distribution |
| RJ45                | Communication             | Electrical levels, pin assignments, actual transport and topology       |
| Type-C              | Serial-port debugging     | Driver, serial parameters, cable role and any power restrictions        |
| End effector / base | Arm and gripper are shown | Revision-specific mounting drawing, fasteners and tool-load conditions  |

**Do not plug the RJ45 connector into a network switch on the assumption that it is Ethernet.** The manufacturer only calls it communication. Likewise, a Type-C debug connector is not evidence that USB can power the arm. Obtain the exact D1-T harness diagram and kit power-distribution instructions before energizing. Allocate secure mounting, a supported rest posture and clearance for every arm and gripper; a four-arm arrangement introduces shared collision space that the edition label does not resolve.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

The D1-T product page promises high- and low-level interfaces but does not identify a downloadable model-specific SDK or firmware release. Consequently, this guide provides no invented host OS, baud rate, device IP, ROS driver, motor IDs or command API. Request the kit's actual delivery package, license, supported host/toolchain and manufacturer release notes, tied to its arm/controller revision. [Published interface claims](https://www.unitree.com/D1-T/)

The official [UniArmL1 repository](https://github.com/unitreerobotics/UniArmL1/blob/cae412dfd98342e4f33098350dc0821c91e91d8f/README.md) is a separate open-source six-degree-of-freedom arm and teleoperation project. Its README describes a hardware BOM, VR/keyboard/leader modes, data capture and a LeRobot integration path, under Apache 2.0. Those are UniArmL1 facts; the read source does not establish D1-T as the same hardware or promise that its scripts can control a D1-T kit. It is useful background for data-pipeline design, not a supported D1-T commissioning shortcut. [UniArmL1 license](https://github.com/unitreerobotics/UniArmL1/blob/cae412dfd98342e4f33098350dc0821c91e91d8f/LICENSE)

For an independent data pipeline, preserve at least session ID, physical arm identity, edition, assigned role, side, six measured joint angles with declared units, gripper state with declared units, command versus feedback distinction, monotonic timestamps, camera frame times, calibration IDs and software/firmware revisions. This is an integration recommendation, not an official D1-T schema. Never replay a recorded vector on hardware until the manufacturer-defined joint order, units and enable/stop ownership are known.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: validate a kit inventory offline <a href="#first-result-validate-a-kit-inventory-offline" id="first-result-validate-a-kit-inventory-offline"></a>

1. Confirm Standard or Full against the order/delivery documentation. Inventory the physical arms with power disconnected. Do not assign leader/follower roles from their position in a photograph.
2. Save this **original local planning record** as `kit.json`. Replace the asset labels with your recorded identifiers. It is neither a Unitree protocol nor a declaration of included components.

```json
{"edition":"standard","arms":[
  {"asset_id":"arm-A","axes":6,"grippers":1,"role":"unassigned"},
  {"asset_id":"arm-B","axes":6,"grippers":1,"role":"unassigned"}
]}
```

3. Save the following original standard-library program as `check_kit_record.py` and run `python3 check_kit_record.py kit.json`. No device, SDK or network access is involved.

```python
"""Original planning schema, not a Unitree packet format or bill of materials."""
import json
import sys


def check(record):
    expected = {"standard": 2, "full": 4}[record["edition"]]
    arms = record["arms"]
    if len(arms) != expected:
        raise ValueError("edition/arm-count mismatch")
    ids = [a["asset_id"] for a in arms]
    if any(not isinstance(v, str) or not v.strip() for v in ids) or len(set(ids)) != expected:
        raise ValueError("missing or duplicate asset identity")
    for arm in arms:
        if arm["axes"] != 6 or arm["grippers"] != 1:
            raise ValueError("record six arm axes separately from one gripper")
        if arm["role"] not in ("unassigned", "leader", "follower"):
            raise ValueError("unknown local role label")
    return {"edition": record["edition"], "arms": expected,
            "arm_axes": expected * 6, "grippers": expected,
            "commissioning": "requires kit BOM, protocol and wiring confirmation"}


if __name__ == "__main__":
    with open(sys.argv[1]) as stream:
        print(json.dumps(check(json.load(stream)), indent=2))
```

Expected checkpoint: `edition=standard`, `arms=2`, `arm_axes=12`, `grippers=2`, with commissioning still requiring documentation. For a Full-edition inventory use `edition=full` and four unique arm records; expected totals are 24 arm axes and four grippers. A duplicate asset ID, wrong arm count or conflated seven-axis record fails. These totals describe the planning record, not independently verified kit contents or synchronized control channels.

### Gate for a live first-status session <a href="#gate-for-a-live-first-status-session" id="gate-for-a-live-first-status-session"></a>

Ask Unitree or the supplying partner for the exact kit BOM, power/polarity and connector drawings, firmware/SDK pair, installation license, transport settings, calibration/zero references, ownership model, hardware stop method and remote-loss behavior. A qualified integrator can then define a non-motion state query, its expected identity/status fields and the supported way to exit. Keep the arms supported during any release of holding torque. Without that delivery evidence, this page intentionally stops at the offline result rather than presenting a plausible-looking live command.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Is D1-T another name for a single D1 arm?** The official page uses D1-T for teleoperation kits and D1 in its component table. Preserve both labels in the inventory and ask for delivered part numbers; do not replace one with the other. [Edition/table context](https://www.unitree.com/D1-T/)

**Does “six axes plus gripper” mean seven rotary arm joints?** No. Record six arm coordinates and the gripper separately. A seven-element learning vector could include the gripper, but its unit and range cannot be assumed to match joint radians.

**Can the Z1 SDK or UniArmL1 setup script be used?** No compatible D1-T release was established. Matching joint count is insufficient. Compare an explicit manufacturer model/revision support statement before installing or running any controller. Retain firmware and calibration records instead of experimenting with another model's binaries.

**No communication after connecting the RJ45 port.** Verify the correct wiring/transport document first. The page does not establish Ethernet, IP discovery or a baud rate. Avoid network scans, pin swaps or power injection as substitutes for a pinout.

**A demonstration has swapped arms or bad timing.** Check unique asset IDs, role/side metadata and calibration identifiers, then inspect command/feedback timestamps and camera times offline. Do not fix a dataset mismatch by reversing motor signs or replaying on the other arm. Once the device SDK is known, distinguish missing feedback from a measured zero.

**What is the supported recovery?** The accessible product material does not specify fault codes, remote-loss timing, reset or reflash procedures. Preserve the fault report, support the mechanism, isolate power only using the approved site procedure and obtain model-specific instructions. Repeated enable, reset or recalibration is not an established recovery method.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                               | Purpose / status                                                                  |
| ---------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [D1-T official product page](https://www.unitree.com/D1-T/)                                                            | Kit edition identity, D1 component specifications and interface claims            |
| [D1-T joint illustration](https://oss-global-cdn.unitree.com/static/ef65f92be2674b4996dbad757c8d24d5_1904x1802.png)    | Manufacturer arm/joint visual reference; not an electrical or calibration drawing |
| [Manufacturer demonstration](https://oss-global-cdn.unitree.com/static/f32e18cb87104902b7c713bbd9a0cf77.mp4)           | Observed video URL; not downloaded or analyzed as a commissioning procedure       |
| [UniArmL1 source](https://github.com/unitreerobotics/UniArmL1/blob/cae412dfd98342e4f33098350dc0821c91e91d8f/README.md) | Separately identified related project; D1-T compatibility unverified              |
| [Unitree contact](https://www.unitree.com/)                                                                            | Obtain exact delivery documentation through the manufacturer/supplier channel     |

No verified D1-T user manual, kit BOM, dimensioned mounting CAD, electrical pinout, public protocol/SDK, firmware image or model-specific ROS package was obtained. These are specific access/coverage gaps, not evidence that such resources do not exist.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The D1-T product HTML and its joint illustration were read/visually reviewed on 24 November 2026. The separate UniArmL1 README and license were read at commit `cae412dfd98342e4f33098350dc0821c91e91d8f` solely to resolve product identity and avoid an unsupported SDK substitution. All integration recommendations and the local record format above are original explanations.

Only the original offline inventory validator and invalid-input checks were executed. No vendor code, SDK installation/build, ROS, simulation, hardware or motion test was performed. No complete support-portal review is claimed. This page is a bounded manufacturer reference; live commissioning depends on the missing D1-T delivery documents and a verified stop/ownership procedure.

**Related documentation:** [Unitree model and development directory](./).
