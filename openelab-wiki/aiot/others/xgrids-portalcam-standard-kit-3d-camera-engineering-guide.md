# XGRIDS PortalCam Standard Kit 3D Camera Engineering Guide

**Product link:** [XGRIDS PortalCam Standard Kit Handheld 3D Spatial Camera LiDAR+3DGS on OpenELAB](https://openelab.io/products/xgrids-portalcam-standard-kit-3d-camera)

## XGRIDS PortalCam Standard Kit 3D Camera Engineering Guide

The XGRIDS PortalCam Standard Kit is a handheld spatial camera for creating photorealistic 3D environments from real-world spaces. It combines LiDAR, a four-camera array, multi-SLAM processing, and 3D Gaussian Splatting (3DGS) workflows so engineers can capture rooms, buildings, sets, and outdoor areas as interactive 3D assets.

This page is for engineers, developers, robotics teams, digital-twin builders, real-estate visualization teams, film and virtual-production teams, and AR/VR creators who need a practical understanding of the device and its software pipeline.

### Quick Summary

* **Product type:** handheld 3D spatial camera / LiDAR + camera capture system for 3DGS reconstruction.
* **Best fit:** real-estate walkthroughs, immersive web/VR spaces, film location scouting, virtual production references, digital-twin previews, and spatial archives.
* **Capture method:** walk through the target space while PortalCam records LiDAR and image data; monitor and manage capture from LCC Scan.
* **Processing method:** use LCC Studio on a Windows workstation to generate, preview, edit, export, and publish LCC/3DGS models.
* **Developer angle:** XGRIDS provides an official LCC Unity SDK, and LCC Studio release notes mention exports such as .lcc2, 3D Tiles, USDZ with environment data, and model publishing workflows.

### What PortalCam Is

PortalCam is a spatial capture device designed to reproduce real spaces as interactive 3D environments instead of only flat panoramas or conventional mesh scans. XGRIDS describes PortalCam as using 3D Gaussian Splatting, LiDAR depth sensing, dual fisheye cameras, dual front cameras, and multi-SLAM algorithms to build photorealistic scenes that users can walk through, edit, and share.

For engineering teams, the important point is that PortalCam is a complete reality-capture pipeline: device firmware, mobile control app, local desktop processing, optional cloud/share workflows, and SDK integration. Treat it as a system, not a single sensor module.

### Key Technical Specifications

| Item                  | Specification                                       | Engineering Note                                                                          |
| --------------------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Weight                | 870 g without tripod                                | Light enough for handheld walking scans; plan operator path and fatigue for large spaces. |
| Dimensions            | 130 x 90 x 77 mm                                    | Compact body for indoor capture and mobile field work.                                    |
| Material              | Aerospace-grade aluminum alloy                      | Rigid body helps maintain sensor alignment during movement.                               |
| Storage               | 512 GB internal                                     | Back up raw capture data after every site visit.                                          |
| Connectivity          | USB 3.0, Wi-Fi 6 at 2.4/5 GHz, Bluetooth 5.2, GPS   | Used for data transfer, app control, device connection, and spatial metadata.             |
| Battery               | Removable Li-ion, 23.04 Wh                          | Carry spare batteries for multi-site capture days.                                        |
| Runtime               | About 60 minutes continuous scan                    | Keep each scan bounded and verify quality before leaving the site.                        |
| Charging              | About 70 min from 0-90%; about 90 min from 0-100%   | Use a charging rotation for field work.                                                   |
| Operating temperature | -20 deg C to 45 deg C                               | Watch battery behavior and condensation across indoor/outdoor work.                       |
| LiDAR                 | Class 1, 940 nm, 0.1-30 m range, 856,000 points/sec | Provides structure and measurable scale for the 3DGS pipeline.                            |
| Camera array          | 4 cameras: 2 fisheye + 2 front                      | Fisheye cameras cover the environment; front cameras preserve detail.                     |
| Camera resolution     | 4000 x 3000 px, 1/2 inch CMOS                       | Capture quality still depends on light, motion, reflectivity, and occlusion.              |
| Field of view         | Fisheye: 200 deg x 200 deg; front: 100 deg x 85 deg | Wide coverage reduces blind spots but does not remove the need for good path planning.    |
| Power input           | USB-C PD, 45 W                                      | Use a suitable USB-C PD charger and verified cables.                                      |

### Hardware Architecture

PortalCam combines geometric and visual sensing. LiDAR provides depth structure and scale. The fisheye cameras capture broad environmental coverage. The front cameras capture higher-detail visual texture in the walking direction. XGRIDS' multi-SLAM pipeline fuses these sources so LCC Studio can reconstruct a 3DGS model with spatial context.

Capture quality depends on scene planning. Avoid very fast walking, excessive rotation, dark corridors without lighting, mirrors, moving crowds, reflective surfaces, and long featureless walls without loop-closure opportunities. For large properties, plan overlapping paths and return points so the SLAM system has enough visual and geometric context.

### Capture-to-Model Workflow

1. **Prepare the scene.** Open doors, stabilize lighting, remove avoidable moving objects, and decide the walking path.
2. **Connect with LCC Scan.** Use the mobile app to connect to PortalCam, view camera feed, adjust settings, name projects, and manage scan data.
3. **Walk the scan path.** Move smoothly. Add overlap around entrances, stairs, corners, and room transitions.
4. **Check capture quality.** LCC Scan release notes mention offline model preview and quality estimates after scanning, so review before leaving the site.
5. **Transfer data.** Move raw scan data to the processing workstation using the supported USB or transfer workflow.
6. **Process in LCC Studio.** Generate a 3DGS model, preview raw point cloud or model quality, crop, annotate, edit viewpoints, and publish or export.
7. **Integrate or share.** Use LCC links for browser/VR sharing, LCC Unity SDK for Unity projects, or supported export formats for external visualization pipelines.

### Software and Resource Links

| Resource                       | Use It For                                                                  | Link                                                                                                    |
| ------------------------------ | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| OpenELAB product page          | Purchase, SKU, kit contents, and OpenELAB support                           | [OpenELAB PortalCam product page](https://openelab.io/products/xgrids-portalcam-standard-kit-3d-camera) |
| XGRIDS PortalCam official page | Manufacturer overview, applications, workflow, and sample-data entry points | [XGRIDS PortalCam](https://www.xgrids.com/portalcam)                                                    |
| XGRIDS download center         | Firmware, LCC Studio, LCC Scan, user manuals, and release notes             | [XGRIDS downloads](https://www.xgrids.com/support/download)                                             |
| PortalCam download page        | PortalCam firmware and PortalCam-specific files                             | [PortalCam downloads](https://www.xgrids.com/support/download?page=PortalCam)                           |
| LCC Studio download page       | Windows desktop reconstruction, editing, export, and publishing             | [LCC Studio downloads](https://www.xgrids.com/support/download?page=LCCStudio)                          |
| LCC Scan download page         | Mobile app for device connection, live feed, settings, and scan data        | [LCC Scan downloads](https://www.xgrids.com/support/download?page=LCCScan)                              |
| XGRIDS Docs/FAQ                | Manufacturer FAQs, software notes, and support articles                     | [XGRIDS Docs/FAQ](https://www.xgrids.com/support/docs-faq)                                              |
| Lixel CyberColor               | Background on the LCC/3DGS processing platform                              | [Lixel CyberColor](https://www.xgrids.com/lixel-cyber-color)                                            |
| Developer resources            | SDK and platform information                                                | [XGRIDS developer page](https://www.xgrids.com/developer)                                               |
| LCC Unity SDK                  | Unity integration for LCC assets                                            | [xgrids/LCC-Unity-SDK on GitHub](https://github.com/xgrids/LCC-Unity-SDK)                               |

### Current Software Notes

* **PortalCam firmware:** XGRIDS' download API listed PortalCam firmware version 3.2.2 during this review. Check the PortalCam download page before upgrading.
* **LCC Studio:** XGRIDS' download API listed LCC Studio for Windows version 1.9.1 during this review. Release notes mention .lcc2 export and publishing, preview tools, scene snapshots, height filtering, asset location, exposure optimization, and large-scene improvements.
* **LCC Scan:** XGRIDS' download API listed LCC Scan Android version 1.1.2 and iOS version 1.1.1 during this review.
* **Mobile requirements:** XGRIDS notes Android 12 or higher with Snapdragon 765G, Dimensity 8000-MAX, or equivalent performance; iOS 13 or higher.
* **GPU guidance:** XGRIDS FAQ says LCC Studio currently works with a single GPU and recommends NVIDIA RTX GPUs with at least 12 GB VRAM, with 24 GB+ recommended for complex projects.

### Output and Integration Options

The native XGRIDS workflow is centered on LCC Studio and LCC/LCC2 content. The OpenELAB product page also mentions .ply and .lcc output. XGRIDS release notes mention 3D Tiles export for Cesium rendering and USDZ export with environment data. For application development, the official LCC Unity SDK is the best starting point.

For browser-based Gaussian-splat review, engineers can inspect [SuperSplat](https://superspl.at/editor) and the [SuperSplat GitHub repository](https://github.com/playcanvas/supersplat). SuperSplat is not a PortalCam-specific official tool, but it is useful for understanding 3DGS editing and review workflows.

### Engineering Setup Checklist

* Install the latest compatible PortalCam firmware from XGRIDS.
* Install LCC Scan on a supported Android or iOS device.
* Install LCC Studio on a Windows workstation with an NVIDIA RTX GPU and enough VRAM.
* Prepare spare batteries, USB-C PD charging, high-speed transfer, and local storage for raw data.
* Create a scan route plan for large spaces, stairs, outdoor/indoor transitions, and repeated corridors.
* Run a short test scan at the site and process it before full production capture.
* Record firmware, app, and LCC Studio versions in project notes for reproducibility.

### Best Practices for High-Quality Captures

* **Lighting:** Use stable, even light; avoid flicker, strong backlight, and sudden exposure changes.
* **Movement:** Walk smoothly and avoid fast rotations; pause briefly at doorways and key viewpoints.
* **Overlap:** Include overlap between rooms and return to recognizable areas.
* **Dynamic objects:** Minimize moving people, vehicles, screens, and reflective moving surfaces.
* **Scale-critical work:** Validate dimensions against known measurements before relying on model measurements.
* **Outdoor work:** Watch for direct sunlight, glass, water, large repeated textures, and GPS/positioning conditions.

### Project References and Application Ideas

* **Real-estate digital walkthrough:** XGRIDS positions PortalCam for capturing a 3,000 sq ft / 280 square meter multi-story property in about 15 minutes at walking speed. Use this as a reference workflow for property documentation and facilities handover.
* **Film and virtual production scouting:** XGRIDS describes PortalCam for remote location management, pre-visualization, LED wall reference environments, and green-screen workflows.
* **Unity interactive viewer prototype:** Start from the [official LCC Unity SDK](https://github.com/xgrids/LCC-Unity-SDK) to build a room-scale viewer, training simulator, product showroom, or museum/archive experience.
* **Browser-based 3DGS review:** Use [SuperSplat](https://superspl.at/editor) and the [SuperSplat GitHub repository](https://github.com/playcanvas/supersplat) as engineering references for splat viewing and editing concepts.
* **Geospatial visualization:** For supported 3D Tiles exports, review the [Cesium data formats documentation](https://cesium.com/learn/data-formats/) for web-scale spatial streaming patterns.

### Known Limitations and Things to Verify

* **Technical drawings/CAD:** I did not find public mechanical drawings or CAD files for PortalCam during this review. Ask OpenELAB or XGRIDS support if your integration requires mounting geometry or enclosure drawings.
* **Point-cloud SDK access:** XGRIDS FAQ indicates the current SDK does not provide raw point-cloud coordinate access; it focuses on Gaussian splat data access.
* **GPU selection:** XGRIDS FAQ says LCC Studio currently uses a single GPU. Multi-GPU workstations may require manual GPU management.
* **Measurement accuracy:** PortalCam is primarily a spatial-content and 3DGS capture system. Validate with control measurements for survey-grade work.
* **Version compatibility:** Firmware, LCC Scan, LCC Studio, and export formats evolve quickly. Check release notes before production work.

### FAQ

#### What is the XGRIDS PortalCam Standard Kit used for?

It captures real spaces as photorealistic interactive 3D environments for real estate, film pre-visualization, VR/AR, digital-twin previews, content creation, and spatial archives.

#### Is PortalCam a LiDAR camera or a 3D Gaussian Splatting camera?

It is both in workflow terms: LiDAR and cameras capture the space, then XGRIDS' LCC/3DGS workflow produces interactive spatial models.

#### What software do I need?

Use LCC Scan for device connection and capture management. Use LCC Studio on Windows for reconstruction, preview, editing, publishing, and export.

#### Can I use PortalCam data in Unity?

Yes. XGRIDS provides an official LCC Unity SDK. Check SDK documentation and version compatibility before production integration.

#### Can I export point clouds from the SDK?

XGRIDS FAQ indicates that current SDK access is for Gaussian splat coordinates and does not provide raw point-cloud coordinates. Confirm the latest capability with XGRIDS support if raw point clouds are required.

#### Does LCC Studio support multiple GPUs?

XGRIDS FAQ says LCC Studio currently supports single-GPU processing and recommends NVIDIA RTX GPUs with at least 12 GB VRAM, with 24 GB+ recommended for complex projects.

#### Where can I download firmware, manuals, LCC Scan, and LCC Studio?

Use the XGRIDS download center and product-specific download pages linked above. Always check release notes before installing.

#### Is PortalCam suitable for survey-grade measurement?

PortalCam is primarily a spatial-content and 3DGS capture system. For measurement-critical surveying, validate against control measurements and manufacturer guidance.

### Source Notes

* Product details and kit information: [OpenELAB PortalCam product page](https://openelab.io/products/xgrids-portalcam-standard-kit-3d-camera)
* Manufacturer overview and workflow claims: [XGRIDS PortalCam official page](https://www.xgrids.com/portalcam)
* Downloads, versions, manuals, and release notes: [XGRIDS download center](https://www.xgrids.com/support/download)
* Software and SDK ecosystem: [XGRIDS developer page](https://www.xgrids.com/developer), [LCC Unity SDK](https://github.com/xgrids/LCC-Unity-SDK), [Lixel CyberColor](https://www.xgrids.com/lixel-cyber-color)

**Review date:** 2026-05-24. Specifications, software versions, and SDK capabilities can change; verify against XGRIDS release notes before production deployment.
