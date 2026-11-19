# MyActuator RMD-X6-P20 and RMD-X8-P20 Engineering Guide

{% hint style="info" %}
[**View RMD-X6-P20 on OpenELAB**](https://openelab.io/products/myactuator-rmd-x6-p20-actuator) · [**View RMD-X8-P20 on OpenELAB**](https://openelab.io/products/myactuator-rmd-x8-p20-actuator)

**Model/kit:** MyActuator RMD-X6-P20 and RMD-X8-P20 · **OpenELAB SKUs:** `MyActuator-RMD-X6-P20-60-E`, `MyActuator-RMD-X8-P20-120-E` · The variants may have different electrical, mechanical and firmware requirements.
{% endhint %}

[MyActuator-RMD-X6-P20-60-E](https://openelab.io/products/myactuator-rmd-x6-p20-actuator) · [MyActuator-RMD-X8-P20-120-E](https://openelab.io/products/myactuator-rmd-x8-p20-actuator)

For detailed X8-120 specifications and commissioning, see the [MyActuator RMD-X8-P20-120-E Development Guide](rmd-x8-p20-120-e-development-guide.md).

## Product and scope

This page covers **RMD-X6-P20-60-E** and **RMD-X8-P20-120-E** integrated planetary actuators. Match the full **E/C suffix, V4/V4.1 generation and firmware**; the older single-encoder V2 and other X6/X8 ratios use different limits.

## Hardware and technical documents

| Item          | Reference                                                       |
| ------------- | --------------------------------------------------------------- |
| X6 scope      | RMD-X6-P20-60-E; 60Nm is its peak-class designation             |
| X8 scope      | RMD-X8-P20-120-E; 120Nm is its peak-class designation           |
| Gearing       | P20 model family; use the exact manual's actual reduction value |
| Control paths | Model-specific CAN / EtherCAT configuration                     |
| Feedback      | Dual-encoder V4-family scope; verify the actual unit            |

The official Downloads-X page supplies **model-specific 2D/3D files, motor parameters and generation-specific manuals**. Use the exact files for nominal supply, continuous torque, current, speed and mounting. Peak torque is not continuous holding torque.

## Getting started

1. Secure one unloaded actuator to a suitable fixture and identify the exact label/firmware.
2. Wire the documented power and communication interfaces, with accessible isolation and conservative current limits.
3. Install the manufacturer's matching setup software and supported interface driver.
4. Read identity, position, temperature and error status before enabling motion.
5. Use the manual's low-speed, small-position test and verify stop behavior before loading the shaft.

**Expected checkpoint:** repeatable status reads and one controlled small motion without faults.

## Development software and recovery

The manufacturer currently lists **CAN motion protocol V4.4-260520**, **EtherCAT protocol V2.0-260425** and **X Series V4 manual-261029**. Select documents compatible with the fitted generation. Its separate **SDK** and **Setup Software** downloads are the software starting points. Preserve parameters and encoder calibration before updates.

## FAQs

**Can an X12 parameter file be imported?** Do not transfer model-specific gains, limits or scaling.

**CAN works but EtherCAT does not?** Check interface variant, master configuration and matching ESI/protocol.

**Status is valid but direction is wrong?** Stop and verify coordinate convention, gearing and encoder settings.

## Sources and validation

* [Exact models, CAD and manuals](https://www.myactuator.com/downloads-xseries)
* [Manufacturer SDK](https://www.myactuator.com/downloads-sdk)
* [Manufacturer setup software](https://www.myactuator.com/downloads-setupsoftware)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
