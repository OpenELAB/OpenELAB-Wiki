# Seeed Studio reComputer R1024 R1025 and R1126 Engineering Guide

{% hint style="info" %}
[**View reComputer R1024-10 on OpenELAB**](https://openelab.io/products/seeed-studio-recomputer-r1024-10) · SKU `Seeed-113991294`

[**View reComputer R1126-10 on OpenELAB**](https://openelab.io/products/seeed-studio-recomputer-r1126-10-iot-gateway-controller-4gb-ram-64gb-emmc) · SKU `Seeed-100040889`

**Also covered:** reComputer R1025-10 · SKU `Seeed-113991274`. Its **openelab.io** product page has not been verified; do not substitute an unconfirmed link. Follow only the exact model's I/O, OS image and electrical documentation.
{% endhint %}

## Model selection and applications

These **Raspberry Pi CM4** gateways target building-management integration, fieldbus data collection and edge services.

| Model / ordering code | RAM / eMMC | Field-interface distinction                             |
| --------------------- | ---------- | ------------------------------------------------------- |
| R1024-10 / 113991294  | 4GB / 16GB | R1000 hardware; three RS485 channels                    |
| R1025-10 / 113991274  | 4GB / 32GB | R1000 hardware; three RS485 channels                    |
| R1126-10 / 100040889  | 4GB / 64GB | R1100 hardware; two RS485, two RS232, two DI and two DO |

The manufacturer's October 2026 update explicitly maps R1125-10 to R1126-10. A storage refresh does not make R1000 and R1100 connector layouts interchangeable.

## Hardware and technical documents

Both families provide Linux computing and dual Ethernet. Optional cellular/LoRa, PoE, UPS and AI modules depend on the actual configuration. Check the model-specific manual for power input, isolation, terminal pinout, mounting dimensions and fitted expansion modules.

**RS232, RS485 and digital I/O are different electrical interfaces.** Do not use an R1100 terminal diagram to wire an R1000. PoE operation requires the appropriate supported hardware; an Ethernet socket alone is not evidence that it is fitted.

## Getting started: inspect before connecting a fieldbus

1. Boot the supplied image using the model's documented supply. Connect one Ethernet port to an isolated bench network.
2. Log in with the delivered setup instructions; change initial credentials when applicable.
3. Record the platform and interfaces:

```bash
cat /etc/os-release
uname -a
lsblk
ip -br addr
ls /dev/tty*
```

4. Follow the family's official serial-port configuration and RS485/Modbus tutorial. Start with a known bench device and a documented **read-only register**.
5. Match baud rate, parity, stop bits, slave address and termination. Log one decoded reading together with the raw request/response.

**Checkpoint:** a stable OS boot and repeatable communication on the correct port. Confirm polarity and reference grounding before connecting a site bus.

## Software, recovery and FAQs

Linux applications can use the documented serial interfaces, Node-RED or a suitable protocol library. Protocol support still requires a matching driver/application and device register map.

**Need to reflash?** Use the **R1000 or R1100** OS guide matching the carrier, and back up configuration first.

**Missing wireless or AI device?** Check that the optional module is physically supplied and supported.

**No serial response?** Verify physical interface type, device mapping, direction control, settings and register addressing before changing the OS.

## Sources and validation

* [R1000 setup, flashing and fieldbus tutorial index](https://wiki.seeedstudio.com/recomputer_r1000_intro/)
* [R1100 hardware, electrical limits and dimensions](https://wiki.seeedstudio.com/recomputer_r1100_intro/)
* [Manufacturer model comparison](https://www.seeed.cc/product/recomputer-r1000-series-raspberry-pi-iot-gateway-controller-cm4-powered-ai-capable)
* [October 2026 memory/storage revision mapping](https://www.seeedstudio.com/blog/2026/10/23/upgraded-memory-and-storage-for-seeed-raspberry-pi-based-products/)
* [R1100 OS recovery](https://wiki.seeedstudio.com/recomputer_r1100_flash_os/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.

## Official documentation and development resources

Use [reComputer R1000 Walk Through](https://wiki.seeedstudio.com/recomputer_r1000_intro/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
