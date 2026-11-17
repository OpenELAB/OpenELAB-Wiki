# XGRIDS PortalCam Premium Kit 3D Spatial Camera Engineering Guide

**Product link:** [XGRIDS PortalCam Premium Kit Handheld 3D Spatial Camera LiDAR+3DGS on OpenELAB](https://openelab.io/products/xgrids-portalcam-premium-kit-3d-spatial-camera)

## XGRIDS PortalCam Premium Kit 3D Spatial Camera Engineering Guide

The XGRIDS PortalCam Premium Kit is a handheld 3D spatial camera package for creating photorealistic, interactive 3D environments from real spaces. The hardware combines LiDAR, a four-camera array, multi-SLAM processing, and 3D Gaussian Splatting (3DGS). The Premium Kit adds a Premium LCC license, a second battery, and an extra one-year virtual warranty extension compared with the Standard Kit listing.

This guide is written for engineers, application developers, AR/VR teams, digital-twin builders, real-estate visualization teams, film/virtual-production teams, and technical buyers evaluating the Premium Kit as a complete capture-to-model workflow.

### Quick Summary

* **Product type:** handheld spatial camera / LiDAR + camera capture system for 3DGS reconstruction.
* **Premium Kit difference:** includes 2 PortalCam batteries, LCC Premium License Activation Card, and PortalCam Warranty Extension for 1 year, virtual, based on the OpenELAB listing.
* **Best fit:** teams that expect repeated capture sessions, more frequent LCC processing, and professional project delivery where extra runtime and licensing matter.
* **Capture method:** walk through the target space while PortalCam records LiDAR and image data; monitor and manage data with LCC Scan.
* **Processing method:** use LCC Studio on Windows to generate, preview, edit, export, and publish LCC/3DGS models.
* **Developer angle:** XGRIDS provides an official LCC Unity SDK and developer portal for LCC application workflows.

### Premium Kit vs Standard Kit

| Item                                                                                      | Premium Kit                                   | Engineering Impact                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------- | --------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PortalCam body                                                                            | 1 unit                                        | Same core capture device and spatial-camera platform.                                                                                                                                    |
| Batteries                                                                                 | 2 PortalCam batteries                         | Better for multi-room, multi-property, and field capture days; allows one battery to charge while one is in use.                                                                         |
| License                                                                                   | LCC Premium License Activation Card           | Better fit for professional LCC workflows than the Standard Kit's Basic license. Verify exact Premium-license features with XGRIDS/OpenELAB before purchasing for a specific deployment. |
| Warranty                                                                                  | PortalCam Warranty Extension, 1 year, virtual | Useful for teams treating PortalCam as production equipment.                                                                                                                             |
| Tripod, charger, protective cover, case, cleaning cloth, quick start guide, warranty card | Included                                      | Enough to begin controlled capture and transport workflows.                                                                                                                              |

### What PortalCam Is

PortalCam is a spatial capture device that reproduces real spaces as interactive 3D environments rather than only flat panoramas or conventional mesh scans. XGRIDS describes PortalCam as using 3D Gaussian Splatting, LiDAR depth sensing, dual fisheye cameras, dual front cameras, and multi-SLAM algorithms to build photorealistic scenes that users can walk through, edit, and share.

For engineering teams, the key is to treat PortalCam as a complete system: device firmware, mobile control app, desktop reconstruction, optional online sharing, export workflows, and SDK integration. The Premium Kit is especially relevant when the camera will be used repeatedly by a team rather than as a one-off demo device.

### Key Technical Specifications

| Item                  | Specification                                       | Engineering Note                                                                     |
| --------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Weight                | 870 g without tripod                                | Comfortable for handheld walking scans; still plan routes for large spaces.          |
| Dimensions            | 130 x 90 x 77 mm                                    | Compact body for indoor capture, stairs, and mobile field work.                      |
| Material              | Aerospace-grade aluminum alloy                      | Rigid body helps maintain sensor alignment during movement.                          |
| Internal storage      | 512 GB                                              | Back up and offload raw scans after every site visit.                                |
| Connectivity          | USB 3.0, Wi-Fi 6 at 2.4/5 GHz, Bluetooth 5.2, GPS   | Supports transfer, app control, device connection, and spatial metadata workflows.   |
| Battery               | Removable Li-ion, 23.04 Wh                          | Premium Kit includes two batteries for longer capture sessions.                      |
| Runtime               | About 60 minutes continuous scan per battery        | With two batteries, plan capture/charging rotation for longer field jobs.            |
| Charging              | About 70 min from 0-90%; about 90 min from 0-100%   | Useful for scheduling capture breaks and recharge cycles.                            |
| Operating temperature | -20 deg C to 45 deg C                               | Watch battery behavior, condensation, and exposure when moving between environments. |
| LiDAR                 | Class 1, 940 nm, 0.1-30 m range, 856,000 points/sec | Provides structural depth and scale for the 3DGS workflow.                           |
| Camera array          | 4 cameras: 2 fisheye + 2 front                      | Wide coverage plus detail capture for photorealistic reconstruction.                 |
| Camera resolution     | 4000 x 3000 px, 1/2 inch CMOS                       | Capture quality depends on lighting, motion, reflectivity, and occlusion.            |
| Field of view         | Fisheye: 200 deg x 200 deg; front: 100 deg x 85 deg | Wide field of view helps coverage but does not replace good path planning.           |
| Power input           | USB-C PD, 45 W                                      | Use a suitable USB-C PD charger and verified cables.                                 |

### Hardware and Data Pipeline

PortalCam fuses LiDAR geometry with camera imagery. The LiDAR sensor provides measurable spatial structure; fisheye cameras capture broad surroundings; front cameras preserve forward-facing visual detail. XGRIDS' multi-SLAM and 3DGS pipeline then converts capture data into an interactive spatial model through LCC Studio.

Because PortalCam is a multi-sensor spatial system, quality depends on capture discipline. Avoid sudden rotations, very fast walking, dark transitions, strong glare, moving crowds, reflective surfaces, and long featureless paths. For large sites, plan loop closures and overlapping routes.

### Capture-to-Model Workflow

1. **Prepare the site.** Open doors, stabilize lighting, reduce moving objects, and plan the walking route.
2. **Connect with LCC Scan.** Use the mobile app to connect to PortalCam, view feed, adjust settings, name projects, and manage scan data.
3. **Capture smoothly.** Walk at a steady pace with overlap around doorways, stairs, corners, and room transitions.
4. **Review capture quality.** XGRIDS release notes for LCC Scan mention offline preview and model-quality estimates after scanning.
5. **Transfer data.** Move scan data to the processing workstation through the supported USB or transfer workflow.
6. **Process in LCC Studio.** Generate the 3DGS model, preview quality, crop, annotate, edit viewpoints, and publish or export.
7. **Integrate.** Use LCC links, LCC Unity SDK, or supported exports such as .lcc/.lcc2, .ply, 3D Tiles, or USDZ when available in your software version.

### Software and Resource Links

| Resource                           | Use It For                                                                      | Link                                                                                                                                   |
| ---------------------------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| OpenELAB Premium Kit page          | Purchase, SKU XGRIDS-10618, kit contents, and OpenELAB support                  | [OpenELAB PortalCam Premium Kit](https://openelab.io/products/xgrids-portalcam-premium-kit-3d-spatial-camera)                          |
| Related OpenELAB Standard Kit wiki | Compare the Standard Kit engineering notes                                      | [PortalCam Standard Kit Engineering Guide](https://wiki.openelab.io/cameras/xgrids-portalcam-standard-kit-3d-camera-engineering-guide) |
| XGRIDS PortalCam official page     | Manufacturer overview, applications, workflow, and sample-data entry point      | [XGRIDS PortalCam](https://www.xgrids.com/portalcam)                                                                                   |
| XGRIDS download center             | Firmware, LCC Studio, LCC Scan, user manuals, and release notes                 | [XGRIDS downloads](https://www.xgrids.com/support/download)                                                                            |
| PortalCam downloads                | PortalCam firmware and PortalCam-specific files                                 | [PortalCam downloads](https://www.xgrids.com/support/download?page=PortalCam)                                                          |
| LCC Studio downloads               | Windows desktop reconstruction, editing, export, and publishing                 | [LCC Studio downloads](https://www.xgrids.com/support/download?page=LCCStudio)                                                         |
| LCC Scan downloads                 | Mobile app for device connection, live feed, settings, and scan-data management | [LCC Scan downloads](https://www.xgrids.com/support/download?page=LCCScan)                                                             |
| XGRIDS Docs/FAQ                    | Manufacturer FAQs, software notes, and support articles                         | [XGRIDS Docs/FAQ](https://www.xgrids.com/support/docs-faq)                                                                             |
| Lixel CyberColor                   | Background on the LCC/3DGS processing platform                                  | [Lixel CyberColor](https://www.xgrids.com/lixel-cyber-color)                                                                           |
| XGRIDS developer portal            | SDK tutorials, release notes, and developer entry point                         | [XGRIDS developer portal](https://developer.xgrids.com/)                                                                               |
| LCC Unity SDK                      | Unity integration for LCC assets                                                | [xgrids/LCC-Unity-SDK on GitHub](https://github.com/xgrids/LCC-Unity-SDK)                                                              |

### Current Software Notes

* **PortalCam firmware:** XGRIDS' public version API listed PortalCam firmware version 3.2.2 during this review. Check the PortalCam download page and app-side OTA before upgrading.
* **LCC Studio:** XGRIDS' public version API listed LCC Studio for Windows version 1.9.1 during this review. XGRIDS release notes mention .lcc2 export/publishing, preview tools, scene snapshots, height filtering, asset location, exposure optimization, and large-scene improvements.
* **LCC Scan:** XGRIDS' public version API listed LCC Scan Android version 1.1.2 and iOS version 1.1.1 during this review.
* **Mobile requirements:** XGRIDS notes Android 12 or higher with Snapdragon 765G, Dimensity 8000-MAX, or equivalent performance; iOS 13 or higher.
* **GPU guidance:** XGRIDS FAQ says LCC Studio currently works with a single GPU and recommends NVIDIA RTX GPUs with at least 12 GB VRAM, with 24 GB+ recommended for complex projects.

### Output and Integration Options

The native workflow is centered on LCC Studio and LCC/LCC2 content. The OpenELAB listing mentions .ply and .lcc output. XGRIDS release notes mention 3D Tiles export for Cesium rendering and USDZ export with environment data. For application development, begin with the official LCC Unity SDK and XGRIDS developer portal.

For browser-based Gaussian-splat review, engineers can inspect [SuperSplat](https://superspl.at/editor) and the [SuperSplat GitHub repository](https://github.com/playcanvas/supersplat). SuperSplat is not a PortalCam-specific official tool, but it is useful for understanding 3DGS editing, inspection, and review workflows.

### Engineering Setup Checklist

* Confirm kit contents on arrival: PortalCam body, 2 batteries, tripod, battery charger/cable, protective cover, LCC Premium license card, warranty extension, quick start guide, warranty card, cleaning cloth, and protective case.
* Install the latest compatible PortalCam firmware from XGRIDS.
* Install LCC Scan on a supported Android or iOS device.
* Install LCC Studio on a Windows workstation with NVIDIA RTX GPU and enough VRAM for scene size.
* Activate and document the LCC Premium license terms for the project team.
* Prepare battery rotation, USB-C PD charging, high-speed transfer, and storage backup for raw data.
* Create a site-specific scan route plan before capture.
* Run a short test scan and process it before committing to a production scan.
* Record firmware, app, LCC Studio, and SDK versions in the project notes.

### Best Practices for Premium Kit Field Use

* **Battery rotation:** Use the second battery to avoid capture interruption; label batteries and log charge cycles for field teams.
* **Lighting:** Use stable lighting and avoid flicker, strong backlight, and abrupt exposure changes.
* **Movement:** Walk smoothly, avoid rapid rotations, and pause at doorways, corners, and key viewpoints.
* **Overlap:** Add route overlap and loop closures in repeated corridors, stairs, and large rooms.
* **Dynamic objects:** Minimize moving people, vehicles, screens, and reflective moving surfaces.
* **Scale-critical work:** Validate model measurements against known references before engineering decisions.
* **Project handoff:** Save raw capture data, LCC project files, export files, version numbers, and share links together.

### Project References and Application Ideas

* **Real-estate capture team:** XGRIDS positions PortalCam for a 3,000 sq ft / 280 square meter multi-story property in about 15 minutes at walking speed. The Premium Kit's second battery is useful for back-to-back property scans.
* **Film and virtual-production scouting:** Use PortalCam to capture real locations for remote review, camera blocking, LED wall reference, green-screen context, and production planning.
* **Unity training or showroom app:** Start from the [official LCC Unity SDK](https://github.com/xgrids/LCC-Unity-SDK) to create an interactive room-scale viewer, training simulation, product showroom, or museum/archive application.
* **Browser-based 3DGS review:** Use [SuperSplat](https://superspl.at/editor) and [SuperSplat on GitHub](https://github.com/playcanvas/supersplat) as ecosystem references for splat viewing and editing concepts.
* **Digital-twin web visualization:** If your LCC Studio version exports supported 3D Tiles data, review the [Cesium data formats documentation](https://cesium.com/learn/data-formats/) for web-scale spatial streaming patterns.
* **Inspection and documentation archive:** Capture construction progress, facility layouts, showroom installations, or event environments for later visual inspection and stakeholder review.

### Known Limitations and Things to Verify

* **Premium license details:** The OpenELAB listing states that the kit includes an LCC Premium License Activation Card, but exact feature boundaries should be confirmed with OpenELAB or XGRIDS for your deployment.
* **Technical drawings/CAD:** I did not find public mechanical drawings or CAD files for PortalCam during this review. Ask OpenELAB or XGRIDS if mounting geometry or enclosure CAD is required.
* **Point-cloud SDK access:** XGRIDS FAQ indicates current SDK access does not provide raw point-cloud coordinates; it focuses on Gaussian splat data access.
* **Single-GPU processing:** XGRIDS FAQ says LCC Studio currently uses a single GPU. Multi-GPU workstations may require manual GPU management.
* **Survey-grade work:** PortalCam is primarily a spatial-content and 3DGS capture system. Validate against control measurements for measurement-critical surveying.
* **Version compatibility:** Firmware, LCC Scan, LCC Studio, SDKs, and export formats evolve quickly. Check release notes before production use.

### FAQ

#### What is the XGRIDS PortalCam Premium Kit used for?

It is used to capture real spaces as photorealistic, interactive 3D environments for real estate, film pre-visualization, AR/VR, digital-twin previews, spatial archives, training, and immersive content creation.

#### How is the Premium Kit different from the Standard Kit?

The Premium Kit includes the same core PortalCam platform but adds a second battery, an LCC Premium License Activation Card, and a one-year virtual warranty extension according to the OpenELAB product listing.

#### Is PortalCam a LiDAR camera or a 3D Gaussian Splatting camera?

It is both in workflow terms. LiDAR and cameras capture spatial data, and XGRIDS' LCC/3DGS software pipeline turns the scan into interactive spatial models.

#### What software do I need?

Use LCC Scan for device connection and capture management. Use LCC Studio on Windows for reconstruction, preview, editing, publishing, and export.

#### Can I use Premium Kit data in Unity?

Yes. XGRIDS provides an official LCC Unity SDK. Check the SDK version, LCC Studio version, and license terms before building a production Unity application.

#### Can I export point clouds from the SDK?

XGRIDS FAQ indicates that current SDK access is for Gaussian splat coordinates and does not provide raw point-cloud coordinates. Confirm the latest capability with XGRIDS support if raw point clouds are required.

#### Does LCC Studio support multiple GPUs?

XGRIDS FAQ says LCC Studio currently supports single-GPU processing and recommends NVIDIA RTX GPUs with at least 12 GB VRAM, with 24 GB+ recommended for complex projects.

#### Where can I download firmware, manuals, LCC Scan, and LCC Studio?

Use the XGRIDS download center and product-specific download pages linked above. Always check release notes before installing or upgrading.

#### Is the Premium Kit suitable for survey-grade measurement?

PortalCam is primarily a spatial-content and 3DGS capture system. For measurement-critical surveying, validate against control measurements and manufacturer guidance.

### Source Notes

* Product details and Premium Kit contents: [OpenELAB PortalCam Premium Kit product page](https://openelab.io/products/xgrids-portalcam-premium-kit-3d-spatial-camera)
* Manufacturer overview and workflow claims: [XGRIDS PortalCam official page](https://www.xgrids.com/portalcam)
* Downloads, versions, manuals, and release notes: [XGRIDS download center](https://www.xgrids.com/support/download)
* Software and SDK ecosystem: [XGRIDS developer portal](https://developer.xgrids.com/), [LCC Unity SDK](https://github.com/xgrids/LCC-Unity-SDK), [Lixel CyberColor](https://www.xgrids.com/lixel-cyber-color)

**Review date:** 2026-05-25. Specifications, kit contents, software versions, license features, and SDK capabilities can change; verify against OpenELAB and XGRIDS release notes before production deployment.
