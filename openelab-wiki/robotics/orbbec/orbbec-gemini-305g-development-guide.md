# Orbbec Gemini 305g Engineering Guide

[ORBBEC-Gemini-305G](https://openelab.io/products/orbbec-gemini-305g-wrist-camera)

### Product and scope

**Gemini 305g** is a close-range stereo RGB-D camera for robot wrists and manipulation. It adds a **GMSL2/FAKRA** path to the Gemini 305 design and also provides USB-C. GMSL host integration is separate from USB SDK installation.

### Hardware and technical documents

| Item             | Reference                                       |
| ---------------- | ----------------------------------------------- |
| Working range    | 4–100cm+; manufacturer ideal range 7–50cm       |
| Depth modes      | Up to 1280 × 800 at 30fps or 848 × 480 at 60fps |
| Color            | Up to 1280 × 800 at 60fps, global shutter       |
| Body             | 42 × 42 × 40mm; approximately 116g              |
| GMSL supply      | 12V, ≥500mA per manufacturer reference          |
| Protection / SDK | IP65 / Orbbec SDK v2                            |

Use the product's **mechanical drawing, mounting/thread details and GMSL system guide**. USB power follows its USB contract; do not apply GMSL's 12V to USB. Confirm deserializer, carrier and cable compatibility before integration.

### Getting started

1. For initial evaluation, use the supported USB setup and **Orbbec SDK v2 / Viewer** to confirm camera identity and a depth image.
2. Place a matte target within the ideal near-field range and select a supported stream pair.
3. For GMSL deployment, select an explicitly supported host, deserializer and JetPack/driver combination.
4. Install the official MIPI/GMSL platform driver before expecting the camera to enumerate.
5. Then verify frame rate, timestamps and synchronization before hand-eye calibration.

**Expected checkpoint:** stable depth/color streaming on the selected interface with recorded firmware and SDK/driver versions.

### Development software and recovery

Use **OrbbecSDK\_v2**. GMSL additionally requires **MIPI\_Camera\_Platform\_Driver** and the exact carrier's device-tree/driver support. The official compatibility guide lists Gemini 305g support from driver **v1.2.12 or above** for its stated solutions; verify the current platform matrix. Follow model-specific firmware recovery instructions.

### FAQs

**A FAKRA connector fits but there is no image?** Verify serializer/deserializer and carrier-driver support.

**60fps at full depth resolution?** The published full 1280 × 800 depth mode is 30fps; 60fps uses the stated lower depth resolution.

**Grasping coordinates are wrong?** Validate intrinsics, stream alignment, optical frames and hand-eye transform.

### Sources and validation

* [Manufacturer model specifications/drawings](https://www.orbbec.com/gemini-305g/)
* [Power/interface comparison](https://store.orbbec.com/products/gemini-305g)
* [Official SDK](https://orbbec.github.io/OrbbecSDK_v2/)
* [GMSL driver and quick start](https://github.com/orbbec/MIPI_Camera_Platform_Driver)
* [Host/driver compatibility](https://doc.orbbec.com/documentation/GMSL%20Camera%20Platform%20Compatibility%20%26%20Multi-Camera%20Sync/Orbbec%20GMSL%20Cameras%20Supported%20Hosts%20and%20System%20Requirements)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
