# Waveshare SIM7600G-H 4G Module Engineering Guide

{% hint style="info" %}
[**View Waveshare SIM7600G-H 4G Module on OpenELAB**](https://openelab.io/products/waveshare-sim7600x-4g-module)

**Product model/family:** Waveshare SIM7600G-H 4G Module · **OpenELAB SKU:** `Waveshare-23992`
{% endhint %}

[Waveshare-23992](https://openelab.io/products/waveshare-sim7600x-4g-module)

## Product and scope

**23992** is the **SIM7600G-H 4G Module, standard/FPC-antenna** configuration. It is not the SIM7600 HAT, M.2 module or Jetson carrier kit; those carrier power and pinout instructions differ.

## Hardware and technical documents

| Item                   | Reference                                                             |
| ---------------------- | --------------------------------------------------------------------- |
| Modem                  | SIMCom SIM7600G-H, LTE Cat4 with supported fallback bands             |
| Host paths             | USB and UART                                                          |
| Positioning            | GNSS supported by the modem                                           |
| Mechanical integration | Castellated module/carrier with region-specific antenna configuration |
| SIM                    | Use supported SIM type and an operator-compatible service             |

The **SIM7600X 4G Module** wiki supplies the module-board **schematic, pinout, dimensions, AT manual and host demos**. Check VIN/VBAT and VIO separately. The manufacturer describes different 3.3V/5V host wiring; a raw modem's supply is not interchangeable with every carrier's USB input.

## Getting started

1. With power off, install the SIM and attach the correct cellular/GNSS antennas.
2. Use the exact module-board USB/power diagram for the first connection.
3. Install its supported host driver and identify the AT command port.
4. Send **AT**, then query modem identity, SIM readiness and network registration with the AT manual.
5. Set the operator APN and test one small data connection before adding GNSS or low-power control.

**Expected checkpoint:** an OK response, recognized SIM and network registration on a supported band/service.

## Development software and recovery

Use the module-specific Raspberry Pi/Jetson/MCU demos and SIM7600 AT-command reference. Record modem firmware and host-driver versions. Preserve APN/configuration before updates, and use the model's supported reset/recovery sequence.

## FAQs

**No AT response?** Verify modem startup, supply under load, USB port or UART pins/levels.

**SIM works but registration fails?** Check service, band coverage, antenna, APN and operator restrictions.

**Can the HAT pinout be reused?** Use this module's diagram; the carrier is different.

## Sources and validation

* [Exact standard SKU](https://dd.waveshare.net/shop/SIM7600G-H-4G-Module.htm)
* [Manufacturer module hardware](https://www.waveshare.com/product/sim7600g-h-4g-module.htm)
* [Correct module wiki and downloads](https://www.waveshare.com/wiki/SIM7600X_4G_Module)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
