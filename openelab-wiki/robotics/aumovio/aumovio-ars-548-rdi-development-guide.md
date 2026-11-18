# AUMOVIO ARS 548 RDI Radar Engineering Guide

{% hint style="info" %}
[**View AUMOVIO ARS 548 RDI Radar Engineering Guide on OpenELAB**](https://openelab.io/products/aumovio-ars-548-rdi-radar)

**Model:** AUMOVIO ARS 548 RDI Radar Engineering Guide · **OpenELAB SKU:** `Aumovio-ARS-548-RDI`
{% endhint %}

[Aumovio-ARS-548-RDI](https://openelab.io/products/aumovio-ars-548-rdi-radar)

## Product and scope

**ARS 548 RDI** is a 77GHz radar for industrial distance, velocity and angular detection. It requires the correct power cable and **BroadR-Reach Ethernet** interface. A normal RJ45 Ethernet port is not the sensor's physical interface.

## Hardware and technical documents

| Item           | Reference                                                                     |
| -------------- | ----------------------------------------------------------------------------- |
| Measurements   | Distance, relative velocity, azimuth and elevation                            |
| Data interface | 100Mbps BroadR-Reach Ethernet                                                 |
| Connections    | Six-pin main connector and two-pin Ethernet connector in the cited data sheet |
| Housing        | 137 × 90 × 39mm; connector envelope up to 65.5mm                              |
| Mass           | 526g in the cited data sheet                                                  |
| Applications   | Industrial area monitoring and object-detection research                      |

Use the manufacturer's **ARS 548 RDI data sheet and mechanical drawing**. Verify the delivered sensor revision, power specification, mating cable, pinout and suitable media converter before applying power. Extended detection ranges depend on configuration and target conditions.

## Getting started

1. Inventory the sensor, mating harness, compatible BroadR-Reach converter and correctly rated supply.
2. Mount the radar using the documented points and preserve its sensing region.
3. Connect the physical link according to the manufacturer integration package.
4. Configure the host network and receiver using the exact RDI communication specification.
5. Capture a short stream and verify sensor identity/status before interpreting detections near a static target.

**Expected checkpoint:** a stable physical/data link and valid decoded status/detections under the supplied RDI specification.

## Development software and recovery

The public product/data-sheet pages do **not by themselves supply a complete SDK or packet specification**. Obtain the matching RDI communication documentation/approved tools from the manufacturer or supplied kit before writing a parser. Do not substitute an unrelated ARS radar's CAN protocol. Record sensor firmware and decoder version.

## FAQs

**Can it plug directly into a laptop?** A compatible BroadR-Reach conversion path and correct wiring are needed.

**Can a generic ARS408 driver be used?** Do not assume protocol compatibility.

**Is it a complete collision-safety system?** System-level performance and required safety functions require separate validation.

## Sources and validation

* [Manufacturer product and interface](https://engineering-solutions.aumovio.com/components/ars-548-rdi/)
* [Official data sheet and dimensions](https://engineering-solutions.aumovio.com/wp-content/uploads/2025/10/FS_ARS-548-RDI_EN.pdf)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
