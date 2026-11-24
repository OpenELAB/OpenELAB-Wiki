---
description: >-
  Plan ARS 548 RDI radar-kit power and automotive Ethernet integration, collect
  read-only network evidence, and identify the exact connector and RDI documents
  needed before commissioning.
---

# AUMOVIO ARS 548 RDI Radar Engineering Guide

{% hint style="info" %}
[**View Aumovio ARS 548 RDI 77 GHz 4D Radar for Industrial Sensing on OpenELAB**](https://openelab.io/products/aumovio-ars-548-rdi-radar?variant=47197572661446)

**Model / option:** ARS-548-RDI Radar kit · **SKU:** `Aumovio-ARS-548-RDI`
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

**Aumovio ARS 548 RDI is an automotive-Ethernet radar providing distance, relative velocity, azimuth and elevation for industrial perception.** The assigned `Aumovio-ARS-548-RDI` option is the **radar kit**, whose store packing list includes radar, cable, converter and power supply. Radar-only, converter and cable options have separate SKUs and do not all contain a sensor. [Exact kit selection](https://openelab.io/products/aumovio-ars-548-rdi-radar).

Its physical link is **100 Mbit/s Broad R-Reach**, requiring a compatible automotive-Ethernet endpoint or media converter. A passive RJ45 lead does not provide physical-layer conversion. [Manufacturer interface description](https://engineering-solutions.aumovio.com/components/ars-548-rdi/). This guide provides a bounded integration workflow: do not energize loose wires or run a configuration sender until the delivered harness/converter instructions and applicable RDI protocol revision have been checked.

## Applications

Use the radar as a sensing input for collision-warning research, far-field area monitoring, target-motion analysis and height/clearance experiments. Aumovio describes applications on AGVs, industrial vehicles, cranes and infrastructure. A perception sensor alone does not establish a machine's stopping behavior; first collect stationary data with motion outputs disabled. [Manufacturer applications](https://engineering-solutions.aumovio.com/components/ars-548-rdi/).

### Define the observable result

Separate detections, clusters and tracked objects in the host pipeline. A single physical object can produce several detections, and a stationary radar can observe moving objects without robot odometry. Dynamic-platform compensation requires the appropriate delivered ego-motion inputs, sign conventions and configuration. Do not label raw reflection points as unique people or obstacles.

The manufacturer product page advertises customer-configurable extended range up to about 1500 m, while the linked short factsheet describes 300 m operation. Preserve those scopes: extended configuration is not a default guarantee for every target. An initial test should use nearby well-separated stationary and moving targets within the approved evaluation area, without using a road vehicle as the first test fixture.

## Specifications

### Sensor and kit boundaries <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

The values below are **listed by the exact OpenELAB product**, whose linked detailed manufacturer sheet could not be retrieved in this review. They are useful for procurement/integration planning, but terminal wiring and operating configuration must be checked against the delivered manufacturer documentation before powering. [Store specification table](https://openelab.io/products/aumovio-ars-548-rdi-radar).

| Parameter                              | Listed ARS 548 RDI value / scope                                                 |
| -------------------------------------- | -------------------------------------------------------------------------------- |
| Radar band / dimensions measured       | 76–77 GHz; distance, relative speed, azimuth, elevation                          |
| Nominal / optional extended distance   | About 300 m; customer configuration up to about 1500 m                           |
| Range resolution                       | 0.22 m; not minimum sensing distance                                             |
| Range accuracy                         | ±0.15 m point-target value, conditional on ego speed                             |
| Output azimuth / installation keep-out | ±50° OI/RDI; ±70° horizontal keep-out, different meanings                        |
| Elevation / vertical keep-out          | ±4° at 300 m, up to±14° below 100 m; ±20° keep-out                               |
| Relative velocity                      | −400 to +200 km/h; approaching has negative sign in the listed sheet             |
| Cycle timing                           | About 50 ms full field; about 70 ms rear /100 ms standstill                      |
| Antenna arrangement                    | 16 RX × 12 TX =192 virtual channels                                              |
| Sensor supply                          | 8.5–17 V DC, nominal 12 V; never direct 24 V                                     |
| Power / current                        | 18 W /1.5 A typical at 12 V; about 23 W maximum; about 3 A peak                  |
| Body / depth / mass                    | 137 × 90 × 39 mm;65.5 mm with connector;526 g excluding cables                   |
| Ambient / storage                      | −40 to +85 °C /−40 to +105 °C                                                    |
| Protection as listed                   | IPx 6 K/9 K water and IP 6 Kx dust; complete harness protection remains separate |

**Do not average or merge these into an unrestricted operating envelope.** The product-page 20 Hz statement is a nominal mode; the detailed cycle values are operating-state dependent. Range resolution, range accuracy and detection range are three different specifications. The installation keep-out envelope is larger than the reported measurement field. [Manufacturer overview](https://engineering-solutions.aumovio.com/components/ars-548-rdi/), [store detailed table](https://openelab.io/products/aumovio-ars-548-rdi-radar).

## Hardware and connections

### Keep three interfaces distinct

| Boundary           | Requirement before connection                                                              |
| ------------------ | ------------------------------------------------------------------------------------------ |
| DC source to radar | Exact harness polarity, wake/enable behavior, connector cavity view and supply rating      |
| Radar to converter | Correct Broad R-Reach/100BASE-T1 physical interface and master/slave arrangement           |
| Converter to host  | Conventional Ethernet port/configuration specified by the delivered converter              |
| Host software      | Actual RDI/object ICD version, addressing, multicast/VLAN requirements and decoder support |

The store lists a six-pin main and two-pin Ethernet connector, but those counts do not establish a safe cavity assignment. No pin-number table is invented here. Use the delivered approved cable assembly intact; verify its labels and documentation with power off. Do not wire from a photograph of an ARS 408 or apply an ARS 408 CAN pinout. [Exact kit description](https://openelab.io/products/aumovio-ars-548-rdi-radar), [Aumovio cable resources](https://engineering-solutions.aumovio.com/components/cables-and-accessories-for-radar-sensors/).

### Installation and frame definition

Provide a rigid bracket matched to the sensor's rear mounting features and keep the radome and specified angular clearance unobstructed. Record installation height, yaw, pitch and roll, and the transform into the host frame. Avoid assuming the shared table's ARS 540 automatic alignment feature applies to ARS 548 RDI. Use the delivered dimensional drawing and mounting constraints before drilling or choosing fastener engagement.

Keep converter supply requirements separate from the radar's 8.5–17 V sensor range. A kit adapter with a higher input rating does not increase the permitted radar-terminal voltage. The listed shutdown above 18 V is protection behavior, not a continuous supply rating. [Store integration notes](https://openelab.io/products/aumovio-ars-548-rdi-radar).

## Software and development resources

### Development software and recovery <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The public manufacturer page provides a product overview and linked factsheet; it does not expose a reviewed public software SDK, complete connector drawing or versioned RDI interface-control document. Those items are required for a verified decoder/setup recipe. Obtain the package matching the delivered serial, firmware and converter through the supplied support channel. [Official product/download entry](https://engineering-solutions.aumovio.com/components/ars-548-rdi/).

A community ROS package or packet definition can be a candidate for separate review, but a repository name containing “ARS 548” does not prove compatibility with this kit's firmware or authorize configuration writes. Do not send copied UDP control payloads, sensor-IP changes or ego-motion messages to obtain an initial display. Capture first and identify the applicable protocol before decoding.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Read-only first checkpoint with a documented, assembled kit

1. Confirm the received selection is the complete radar kit. Photograph labels and record sensor serial, converter model, supply output, cable part number and supplied documentation revision.
2. With all power off, compare the approved harness and converter instructions. Confirm sensor voltage/polarity, physical-interface compatibility, wake behavior and both connector views. If any is absent, stop at this wiring checkpoint; do not infer a pinout from the table above.
3. Once those delivered instructions are verified, connect the intact kit on an isolated evaluation network and energize only as documented. Record the converter link indicators and selected host interface. Keep machine actuation disabled.
4. On Linux, inspect the host before altering network settings:

```bash
ip -br link
ip -br address
ip route
```

Choose the actual dedicated Ethernet interface. In Wireshark, start capture on that interface without a display filter. Observe source/destination MAC, ARP, VLAN and UDP traffic, then save a short PCAPNG for diagnosis. This is observation, not an instruction to assign guessed radar addresses.

5. Export a packet inventory from the saved capture using installed Wireshark command-line tools:

```bash
tshark -r ars548-bench.pcapng -Y udp -T fields -E header=y -E separator=, -e frame.time_relative -e ip.src -e ip.dst -e udp.srcport -e udp.dstport -e udp.length
```

**Expected result:** when the documented kit is powered and its converter link is valid, the capture identifies actual Ethernet/UDP endpoints and packet lengths. If no UDP is visible, the result is a diagnostic failure, not permission to guess a configuration command. A UDP stream alone does not prove valid radar detections, clock synchronization or a supported decoder.

### Original offline traffic summary

Save the exported CSV as `ars548-udp.csv`. This original script summarizes the observed network without parsing an unverified proprietary payload or sending anything:

```python
import csv
from collections import Counter
from pathlib import Path
counts = Counter()
lengths = Counter()
with Path("ars548-udp.csv").open(newline="") as f:
    for row in csv.DictReader(f):
        endpoint = (row["ip.src"], row["ip.dst"],
                    row["udp.srcport"], row["udp.dstport"])
        counts[endpoint] += 1
        lengths[row["udp.length"]] += 1
for endpoint, count in counts.most_common():
    print("endpoint", endpoint, "packets", count)
print("UDP lengths including header", dict(lengths))
if not counts:
    raise SystemExit("No exported UDP; recheck capture interface and link")
```

**Expected result:** an endpoint/length inventory suitable for comparison with the delivered ICD. Next, validate a manufacturer-approved viewer/decoder against a known stationary scene, verify units/velocity sign/time and only then consider an application integration. Exact viewer commands are not supplied because the kit's software/ICD revision has not been established.

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                  | Check before changing configuration                                                                                          |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| No conventional Ethernet link            | Correct converter supply and physical-layer conversion; a passive cable cannot replace Broad R-Reach hardware                |
| Converter link, no UDP                   | Actual interface, VLAN/multicast handling, delivered endpoint settings, sensor wake/power and packet capture without filters |
| Packets but no objects                   | Correct RDI versus object-output parser and firmware/ICD match; do not use an ARS 408 CAN decoder                            |
| Range seems “wrong”                      | Nominal versus extended mode, target properties, detection versus tracked-object output and unit scaling                     |
| Apparent approaching-speed sign reversal | Radar radial velocity sign versus robot-frame convention; compare a controlled target                                        |
| Variable update rate                     | Operating state, nominal 50 ms versus other listed modes, packet assembly and host processing                                |
| Persistent restart                       | Sensor-side voltage/current and converter supply separately; do not connect a 24 V system directly                           |

**Is this a complete collision-avoidance system?** It supplies radar data; host processing, system response and stopping behavior require separate implementation and validation.

**Can I use the converter accessory alone?** It contains no radar. The assigned SKU is the complete kit, with separate accessory SKUs excluded from this guide's coverage.

Preserve captures and configuration records before a support-directed recovery. Use only the firmware and procedure matched to the delivered sensor. No reset, flash or factory-IP write is recommended from the currently readable public evidence.

## Downloads and technical documents

| Resource                                                                                                                     | Review status and purpose                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| [Aumovio ARS 548 RDI overview](https://engineering-solutions.aumovio.com/components/ars-548-rdi/)                            | Read: measurement method, applications, interface and extended-range scope |
| [Official linked factsheet](https://engineering-solutions.aumovio.com/wp-content/uploads/2025/10/FS_ARS-548-RDI_EN.pdf)      | Download blocked/timed out during this review; retain original URL         |
| [Aumovio cables/accessories](https://engineering-solutions.aumovio.com/components/cables-and-accessories-for-radar-sensors/) | Obtain model-matched harness/converter documentation                       |
| [Exact OpenELAB selection](https://openelab.io/products/aumovio-ars-548-rdi-radar)                                           | Kit versus radar-only/accessory scope and listed sensor specifications     |

Before electrical commissioning, obtain the **connector/polarity/wake drawing** and **converter configuration instructions**. Before decoded first result, obtain the **applicable versioned RDI/object ICD and supported viewer/SDK**. These are named integration prerequisites; the read-only host/capture steps above do not replace them.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed 24 November 2026: exact kit selection and cached catalog, live store page and readable manufacturer product page. The official linked detailed PDF was not successfully retrieved; its detailed numerical values above are expressly attributed to the store rather than represented as newly verified manufacturer facts.

**Physical setup, power measurements, live capture, offline script execution, decoder execution and firmware changes: not run.** The local traffic-summary example is original and syntax checked. This guide remains bounded pending the exact connector/converter instructions and versioned RDI/SDK evidence.

* [ARS 548 RDI official product page](https://engineering-solutions.aumovio.com/components/ars-548-rdi/) — current 24 Nov 2026.
* [Exact radar-kit store specifications/options](https://openelab.io/products/aumovio-ars-548-rdi-radar) — 23 Nov catalog plus live 24 Nov page.
* [ARS 548 RDI linked factsheet access attempt](https://engineering-solutions.aumovio.com/wp-content/uploads/2025/10/FS_ARS-548-RDI_EN.pdf) — retrieval blocked.
