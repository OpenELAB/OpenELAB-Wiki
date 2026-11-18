# Seeed Studio reComputer Industrial R2245-12 Engineering Guide

[Product at OpenELAB](https://openelab.io/products/seeed-studio-recomputer-r2245-26tops)

### Product, applications and specification scope

**100077451, reComputer Industrial R2245-12** is a Raspberry Pi **CM5** industrial edge-AI/NVR configuration with **Hailo-8 acceleration advertised at 26 TOPS**. Use it for camera analytics and industrial data integration. It is not a CM4 R1000 gateway or a Jetson.

| Item                  | Engineering reference                                                |
| --------------------- | -------------------------------------------------------------------- |
| Host processor        | CM5, quad-core Cortex-A76                                            |
| Accelerator           | Hailo-8 M.2; model deployment requires compatible compiled artifacts |
| System storage/RAM    | Verify the ordered configuration and the installed module            |
| Industrial interfaces | RS485, RS232, CAN FD and isolated DI/DO                              |
| Expansion             | NVMe and supported cellular/LoRa options                             |
| Cooling               | Fanless enclosure; maintain the documented installation clearance    |

The official R22xx page contains conflicting copied CPU/Ethernet/PoE descriptions in some sections. Its CM5 specification and detailed per-port map should be checked against the received unit; **do not energize an assumed PoE port from a generic summary**. Confirm PSE versus PD behavior and power budget before attaching cameras.

### Getting started: OS and accelerator enumeration

1. Check the exact nameplate, supply requirements, boot switch and storage before powering the unit.
2. Boot the delivered model-specific image. Keep a backup before replacement.
3. Record OS, storage and interfaces using `cat /etc/os-release`, `lsblk`, `ip -br link` and `lspci -nn`.
4. Use Seeed's supported Hailo driver/runtime installation. When installed, run:

```bash
hailortcli fw-control identify
```

5. Run the manufacturer's matching Hailo example before adding multiple camera streams.

**Checkpoint:** the accelerator identifies successfully and a supported example produces detections. Measure your own throughput rather than treating 26 TOPS as an NVR channel-count guarantee.

### Technical resources and integration

Use the assembly guide for module access and the hardware guide's **pinouts and installation diagrams**. Observe the DI/DO electrical limits and isolated-interface reference grounds. Hailo runtime, firmware and compiled **HEF** model compatibility must be kept together.

### FAQs and recovery

**No display or eMMC while flashing?** Follow the R22xx boot-switch/USB procedure and its FAQ; do not substitute a CM4 recovery sequence.

**Can any ONNX model run directly?** It needs the supported Hailo conversion/compilation workflow.

**Camera link but no video?** Check stream URL/authentication, network routing, codec and power budget independently.

**Can I install a generic OS?** Confirm Seeed's current driver and OS support, especially Hailo and industrial interfaces, before replacing the supplied image.

### Sources and validation

* [R22xx manufacturer hardware and interface guide](https://wiki.seeedstudio.com/recomputer_industrial_r22xx_getting_start/)
* [R22xx assembly and expansion](https://wiki.seeedstudio.com/recomputer_industrial_r22xx_assembly_guide/)
* [R22xx system configuration](https://wiki.seeedstudio.com/recomputer_industrial_r22xx_configure_system/)
* [Known OS and flashing questions](https://wiki.seeedstudio.com/recomputer_industrial_r2x_faq/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
