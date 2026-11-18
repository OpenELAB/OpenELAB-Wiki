# HeyGears UltraPrint PAT10 transparent resin: material workflow

{% hint style="info" %}
[**View HeyGears UltraPrint-Modeling PAT10 Transparent Resin on OpenELAB**](https://openelab.io/products/pat10-transparent-resin)

**Material:** UltraPrint-Modeling PAT10 transparent resin · **Top-200 workbook SKU:** `Hg-MA005001` · **Storefront SKU observed:** `MA002363A`. **SKU mapping remains unverified:** confirm the listed bottle/region variant before treating them as the same sale item.
{% endhint %}

[Hg-MA005001](https://openelab.de/products/heygears-ultraprint-modeling-pat10)

## Product and scope

PAT10 is a transparent modeling photopolymer for visual prototypes and clear functional-model development. This is a consumable material guide: reproducibility depends on the exact printer profile, geometry, wash and cure process, rather than a device SDK.

## Hardware and technical documents

| Item                  | Reference                                                                        |
| --------------------- | -------------------------------------------------------------------------------- |
| Material              | UltraPrint-Modeling PAT10                                                        |
| OpenELAB variant      | Hg-MA005001; confirm bottle label, quantity and expiry                           |
| Optical reference     | Manufacturer reports 88.5% transmittance and 5.4% haze under its test conditions |
| Printer compatibility | Select PAT10 only when supported by the exact printer/profile release            |

Obtain the current PAT10 technical data sheet and safety data sheet from HeyGears before lab use. A directly readable SDS was not located during this review; chemical handling, storage, disposal and exposure limits remain subject to that document. Do not treat the uncured resin or a transparent cured part as certified for skin, food or optical-instrument use.

## Getting started

1. Record bottle batch, expiry, storage history, printer and resin-profile version.
2. Use the exact printer's PAT10 material selection in Blueprint. Follow the material instructions for conditioning and mixing; avoid substituting exposure times from another resin.
3. Print a small coupon with representative walls, holes and the intended surface finish.
4. Wash, dry and post-cure according to the PAT10 process specified for the available equipment. Do not invent a generic curing time.
5. Measure the coupon after full post-processing; record haze, color, dimensions and any finish treatment before producing the final part.

**Expected checkpoint:** A labeled cured coupon and a recorded printer-to-post-processing recipe that can be repeated for the same batch.

## Development software and recovery

The development resources are the material TDS/SDS and the printer's Blueprint profile. Material certificates and downloadable recipes should be archived with the project. For cloudy parts, separate uncured residue, washing effects, cure state and surface roughness before changing the print settings.

## FAQs

**Does transparency guarantee lens-grade performance?** No. Test optical performance at the intended thickness, wavelength and surface finish.

**Can PAT10 use another resin's cure cycle?** Use the PAT10 recipe for the actual equipment; different formulations and printers require different processes.

## Sources and validation

* [PAT10 manufacturer product and material information](https://store.heygears.com/products/ultraprint-modeling-pat10-transparent-resin)
* [HeyGears Blueprint](https://www.heygears.com/SAP)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
