# Banana Pi BPI-R4 Pro 8X: image selection and first network setup

[BPI-R4P-8X](https://openelab.io/products/banana-pi-bpi-r4-pro)

### Product and scope

The BPI-R4P-8X is the 8 GB BPI-R4 Pro router platform for network development, edge gateways and high-speed routing experiments. R4, R4 Pro 8X and R4 Pro 4E are separate image targets. Optional wireless modules and cellular hardware must be identified independently.

### Hardware and technical documents

| Item              | Reference                                                                      |
| ----------------- | ------------------------------------------------------------------------------ |
| SoC               | MediaTek MT7988A / Filogic 880                                                 |
| Memory variant    | 8 GB DDR4 for BPI-R4P-8X                                                       |
| Storage reference | 8 GB eMMC and 256 MB SPI NAND in the Pro documentation; confirm board revision |
| Image example     | BpiRouterOS v1.6.0 provides a dedicated BPI-R4-Pro 8X image, separate from 4E  |

Use the official Pro documentation for the port map, power input, boot selection, schematics and mechanical files. The board is not an ordinary Raspberry Pi GPIO replacement. Confirm the exact copper/SFP port arrangement and fitted wireless modules from the 8X revision's labels; do not infer included Wi-Fi hardware from a Wi-Fi 7 headline.

### Getting started

1. Record board revision, memory, fitted modules and power-supply specification. Keep console/recovery instructions and a configuration backup available.
2. Choose the official image explicitly labeled BPI-R4-Pro 8X. Verify its download integrity and write it to the documented removable boot medium, checking the destination device carefully.
3. Set boot selection using the board manual and boot with a wired PC on the designated LAN interface. Start isolated from the production network.
4. Identify the management address from the image's instructions. Set credentials and confirm the LAN/WAN assignments before connecting an uplink.
5. Check link negotiation and connectivity one port at a time, then back up configuration before adding VLANs, multi-WAN or wireless packages.

**Expected checkpoint:** A repeatable wired login, correctly identified interfaces and a saved configuration for the exact 8X image.

### Development software and recovery

The official image release notes and board documentation define boot/recovery behavior. Avoid immediately overwriting eMMC or NAND; preserve a known-working removable boot path. For upgrades, follow the exact image release's method and model-specific filenames rather than another OpenWrt device's procedure. Keep a serial boot log when diagnosing failure to start.

### FAQs

**Can I flash the 4E image to an 8X?** No; the official release explicitly separates those targets.

**Why is Wi-Fi absent?** Confirm an appropriate wireless module is fitted and supported by the image before investigating radio settings.

**Why did an interface change after an upgrade?** Compare image configuration and port mapping before reusing older network settings.

### Sources and validation

* [Banana Pi R4 Pro hardware documentation](https://docs.banana-pi.org/en/BPI-R4_Pro/BananaPi_BPI-R4_Pro)
* [Official BpiRouterOS v1.6.0 release](https://forum.banana-pi.org/t/bpirouteros-v1-6-0-official-version-released/28490)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
