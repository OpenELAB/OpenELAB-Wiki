# HeyGears Reflex 2 Pro and Reflex RS Turbo: model-specific setup

[11030301147](https://openelab.io/products/heygears-ultracraft-reflex-2-pro) · [11030301140](https://openelab.de/products/heygears-ultracraft-reflex-turbo-3d)

### Product and scope

Two distinct MSLA resin printers for detailed prototypes, tooling models and small production runs. Select the exact printer in the slicer; an original Reflex profile is not a substitute. This page separates the confirmed model specifications and follows the manufacturer-managed print workflow.

### Hardware and technical documents

| Item                         | Reference                                                  |
| ---------------------------- | ---------------------------------------------------------- |
| Reflex 2 Pro build volume    | 230 × 144 × 350 mm                                         |
| Reflex 2 Pro optics          | 40 μm native XY pixel; 385+ nm; 10.7-inch Amber Screen Pro |
| Reflex RS Turbo build volume | 222 × 122 × 228 mm                                         |
| Reflex RS Turbo optics       | 29.7 μm native XY pixel; 405 nm                            |
| Connectivity                 | 2 Pro: USB, Wi-Fi, LAN; RS Turbo: USB, Wi-Fi               |

Use the exact model's quick-start instructions for shipping restraints, tank installation, leveling and resin handling. The manufacturer store page contains model specifications and included parts; external dimensions and mechanical tolerances must come from the current drawing/manual. A CAD package or public printer-control SDK was not confirmed. Check whether wash, cure and pulsing-release accessories are included or separate.

### Getting started

1. Record the printer model, firmware version, resin name/lot and installed tank/accessories. Remove transport restraints using the supplied quick-start guide.
2. Install HeyGears Blueprint from the official software page. Select the exact printer and a currently supported resin profile; review required accessory compatibility.
3. Complete the model's initialization and leveling workflow. Inspect the platform and tank before filling; follow the material SDS and ventilation requirements.
4. Prepare a small manufacturer-supported test model in Blueprint. Inspect orientation, supports and print preview before sending the job.
5. Wash and cure using the resin's specified process. Measure the cured test part and save the job/profile versions.

**Expected checkpoint:** A completed small print with no platform/tank errors, documented post-curing and a repeatable saved job.

### Development software and recovery

Blueprint is the supported preparation and job-management path. Do not infer exposure settings from the other printer's wavelength or pixel pitch. Export job diagnostics and record firmware/profile versions before troubleshooting. Resolve adhesion, tank condition and profile selection before tuning a material. Manufacturer accuracy and speed claims depend on the stated test conditions; validate your own part tolerances.

### FAQs

**Can the two printers share a sliced job?** Re-slice for the destination model and its supported material/accessory combination.

**Can I use arbitrary third-party resin?** Confirm current model, firmware and material-mode support with HeyGears; this guide does not establish universal compatibility.

**Why is my cured part distorted?** Check support placement, orientation, cleaning and curing recipe before changing printer calibration.

### Sources and validation

* [Reflex 2 Pro specifications](https://store.heygears.com/products/reflex-2-pro-3d-printer)
* [Reflex RS Turbo specifications](https://store.heygears.com/products/ultracraft-reflex-rs-turbo-3d-printer)
* [HeyGears software](https://www.heygears.com/SAP)
* [Reflex 2 documentation](https://wiki.heygears.com/en/Reflex2)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
