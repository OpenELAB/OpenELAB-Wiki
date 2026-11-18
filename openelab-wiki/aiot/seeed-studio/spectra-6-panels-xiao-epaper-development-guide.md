# Seeed Studio Spectra 6 Panels and XIAO ePaper Kit Development Guide

### Product boundaries and applications

These products support low-refresh color signage, information boards and photo displays. **A bare panel requires a compatible driver board and host.** It is not a complete reTerminal E1002/E1004.

| OpenELAB / Seeed code | Scope                                                                                |
| --------------------- | ------------------------------------------------------------------------------------ |
| 100064541             | 7.3-inch Spectra 6 panel, 800 × 480 pixels                                           |
| 100088646             | 13.3-inch Spectra 6 panel, 1200 × 1600 pixels                                        |
| E25102101             | XIAO 7.3-inch ePaper DIY kit; verify fitted driver-board revision and supplied parts |

Spectra 6 provides six-color ePaper. Panel resolution, FPC connection, waveform and driver selection matter independently. The current selection matrix identifies **EE02 for the 13.3-inch panel** and **EE04 support for compatible 7.3-inch panels**; inspect the delivered kit before using those instructions.

### Hardware documents and software

Use each panel page's **datasheet and dimensional drawing**, plus the fitted board's **schematic/PCB/CAD**. Do not connect a panel by pin count alone or hot-plug an FPC. Follow the controller's power and panel-connector instructions.

**Seeed\_GFX2** and the official board-specific firmware collection provide development paths. Select the exact board and **Spectra 6** panel; a monochrome 7.5-inch example is not a substitute. Retain the example's required library/toolchain versions.

### First display test

1. With power disconnected, fit the panel to the correct connector, confirm contact orientation and set documented jumpers.
2. Connect the driver board through USB. Install its supported Arduino setup.
3. Open the graphics-library example for the **actual board + panel combination** and upload its HelloWorld/color test.
4. Wait for the full refresh to finish before resetting or powering down.
5. Verify text orientation, resolution and all expected colors. Save the configuration and a reference photograph.

**Checkpoint:** a complete, repeatable refresh with correct geometry. Add networking or image conversion after this baseline succeeds.

### FAQs and recovery

**A picture remains with power off?** Image persistence is normal for ePaper.

**Blank or corrupted colors?** Recheck panel identity, FPC seating, driver/waveform and supply.

**Can it display video?** Design for the panel's documented refresh cycle; this is not an LCD.

**Can a reTerminal binary be flashed onto a bare-panel kit?** Use the exact controller target. Similar panel size does not imply the same MCU wiring.

**Factory restoration?** Select the fitted board and panel in the official firmware collection, preserving any application configuration first.

### Sources and validation

* [7.3-inch panel product and technical downloads](https://www.seeedstudio.com/7-3inch-Six-Color-eInk-ePaper-Display-with-800x480-Pixels-p-6567.html)
* [13.3-inch panel product and technical downloads](https://www.seeedstudio.com/13-3inch-Six-Color-eInk-ePaper-Display-with-1200x1600-Pixels-p-6569.html)
* [Current ePaper board/panel selection matrix](https://wiki.seeedstudio.com/seeed_epaper_displays/)
* [EE04 setup, schematic, PCB and CAD links](https://wiki.seeedstudio.com/epaper_ee04/)
* [Official graphics library](https://github.com/Seeed-Studio/Seeed_GFX2)
* [Board-specific firmware and hardware collection](https://github.com/Seeed-Projects/OSHW-reTerminal-Series-E-D)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
