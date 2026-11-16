---
description: >-
  English, searchable instructions from DOBOT's bilingual Mini Vacuum Source
  shipping list, specifications, and user guide.
---

# DOBOT Mini Vacuum Source User Guide

## DOBOT Mini Vacuum Pump Box for Robot End Effectors

{% embed url="https://openelab.io/products/dobot-mini-vacuum-pump-box" %}

[Official manual PDF](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260706/%E8%BF%B7%E4%BD%A0%E6%B0%94%E6%B3%B5%E7%9B%92_%E5%8F%91%E8%B4%A7%E6%B8%85%E5%8D%95_%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E_20260630-CN%26EN.pdf)

## Supplied Components

The manufacturer's shipping list shows one mini vacuum source, one connection cable, and one 4 mm air tube.

![Official shipping-list drawings of the mini vacuum source, connection cable, and air tube](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKENUR8PrqGATMEanEZNI%2Fmini-pump-shipping-items.png?alt=media)

## Specifications

| Parameter                            | Official value    |
| ------------------------------------ | ----------------- |
| Dimensions (length × width × height) | 163 × 143 × 53 mm |
| Weight                               | 800 g             |
| Negative pressure (suction)          | −70 kPa           |
| Positive pressure (blowing)          | 110 kPa           |
| Air-tube connector size              | 4 mm              |
| Control method                       | I/O               |
| Rated voltage                        | 24 V DC ±10%      |
| Rated current                        | 0.8 A             |
| Peak current                         | 1.2 A             |
| Operating noise                      | 65 dB             |
| Protection rating                    | IP20              |

## Controls and Connections

The front panel has a power switch, a Manual/Auto selector, Pressure and Vacuum controls, an air port, and an I/O interface.

![Official front-panel drawing showing the power, Manual/Auto, Pressure, Vacuum, air, and I/O controls](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FufBkZe1G3a4Oqp8hwbbZ%2Fmini-pump-control-panel.png?alt=media)

* **Manual/Auto:** In Auto mode, control the pump through I/O. In Manual mode, use the front-panel buttons.
* **Pressure/Vacuum:** The indicator LEDs show the active mode. Press a button once to enable that function and again to stop it. Only one mode can be active at a time; pressing Vacuum while Pressure is active switches directly to Vacuum.

### I/O Signals

| Terminal | Function                            | Signal specification                                                |
| -------- | ----------------------------------- | ------------------------------------------------------------------- |
| 24V      | Positive supply                     | 24 V DC ±10%; rated current 0.8 A                                   |
| GND      | Supply return                       | Connect to the negative supply terminal.                            |
| Pressure | Blowing / positive-pressure control | High (24 V DC ±10%): pump runs; low (−0.3 to 0.8 V DC): pump stops. |
| Vacuum   | Suction / negative-pressure control | High (24 V DC ±10%): pump runs; low (−0.3 to 0.8 V DC): pump stops. |

**Wiring caution:** The source leaflet inconsistently describes the GND terminal in English. Check the physical terminal labels and confirm the supply wiring with DOBOT before energizing the unit.

## Installation with MG400

The official installation example shows an MG400 robot. Its steps do not establish compatibility or wiring for other robots.

1. Connect the pump's 4-pin cable to the MG400.
2. Connect the pump's air tube to the air port on the MG400 base.
3. Connect the air tube at the MG400 tool end to the suction cup.

![Official MG400 base connection diagram for the mini vacuum source](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKNwvpoKHVGlxdb2pbM1D%2Fmini-pump-mg400-wiring.png?alt=media)

![Official MG400 end-effector air-tube and suction-cup connection diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDxBuc5jC23kSyUk59AjW%2Fmini-pump-suction-cup.png?alt=media)

**Placement note:** When a suction cup is holding an object under vacuum, briefly enable Pressure to release the negative pressure more quickly before setting the object down.
