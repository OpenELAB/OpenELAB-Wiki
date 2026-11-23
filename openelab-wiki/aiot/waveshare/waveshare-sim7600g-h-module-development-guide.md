---
description: >-
  Identify and power the SIM7600G-H standard FPC module, query SIM/network
  status over USB, configure a matched data path and interpret GNSS coordinates.
---

# Waveshare SIM7600G-H 4G Module Engineering Guide

{% hint style="info" %}
[**View Waveshare SIM7600G-H 4G Communication Module 4G/3G/2G GNSS Positioning on OpenELAB**](https://openelab.io/products/waveshare-sim7600x-4g-module?variant=45546619535558)

**Model / option:** Standard version + FPC Antenna · **SKU:** `Waveshare-23992`
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The **Waveshare SIM7600G-H 4G Module, SKU Waveshare-23992**, is the compact castellated USB/UART cellular board, sold here as the **standard version with FPC LTE antenna and unsoldered headers**. It combines LTE Cat-4 connectivity and GNSS in a roughly 39 × 42mm board. It is not the larger Raspberry Pi HAT even though the shared download archive contains HAT-oriented example names.

The store's other assembly option adds soldered headers/SMA antenna hardware; it does not change this assigned SKU into a different regional modem. A GNSS antenna is **not included** in this option. Verify the module's `SIM7600G-H` shield marking and antenna connector labels before setup. [Exact-board manufacturer guide](https://www.waveshare.com/wiki/SIM7600X_4G_Module), [manufacturer product and connection reference](https://www.waveshare.com/product/sim7600g-h-4g-module.htm).

## Applications

Use this board for a Linux cellular uplink, remote sensor telemetry, a GNSS-enabled logger, or an MCU that sends AT commands over UART. Start with modem identity and SIM/network status over USB; add data transport and location only after those checks pass.

The G-H model's band coverage is broad, but a matching LTE band does not establish operator approval, roaming entitlement, APN settings or local 2G/3G service. Confirm those with the intended operator. Voice and SMS availability also depend on the service plan and modem firmware. The board has no conventional analog handset audio jack; voice work requires its documented USB-audio path or appropriate development, not merely an AT dial command.

## Specifications

| Parameter                       | SIM7600G-H board value / condition                                       |
| ------------------------------- | ------------------------------------------------------------------------ |
| Cellular class                  | LTE Cat-4; theoretical 150Mbps downlink / 50Mbps uplink                  |
| LTE-FDD                         | B1/B2/B3/B4/B5/B7/B8/B12/B13/B18/B19/B20/B25/B26/B28/B66                 |
| LTE-TDD                         | B34/B38/B39/B40/B41                                                      |
| UMTS/HSPA+                      | B1/B2/B4/B5/B6/B8/B19                                                    |
| GSM/EDGE                        | 850/900/1800/1900MHz                                                     |
| GNSS constellations             | GPS, BeiDou, GLONASS, Galileo, QZSS                                      |
| USB/VBUS supply                 | 5V                                                                       |
| VIN supply                      | 5–26V, board input only                                                  |
| BAT supply                      | Single-cell 3.7V lithium input; not the VIN terminal                     |
| UART I/O reference              | 3.3V with VIO unconnected; documented VIO configuration for 3.8–5V hosts |
| SIM                             | Nano SIM; 1.8V/3V card support                                           |
| Board dimensions                | 38.8 × 42.0mm                                                            |
| Operating / storage temperature | −30–80°C / −45–90°C, manufacturer board reference                        |

Sources: [model specification table](https://www.waveshare.com/wiki/SIM7600X_4G_Module), [manufacturer electrical and pin table](https://www.waveshare.com/product/sim7600g-h-4g-module.htm). Network data rates are modem maxima, not measured application throughput. The onboard regulator's high-current capability is not a guaranteed USB-port supply budget: size the supply, wiring and thermal design for cellular transmit bursts.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Power domains, antenna and SIM

Insert/remove the SIM and attach antennas with power removed. Seat the FPC antenna on **MAIN** and route its cable without pulling sideways on the IPEX connector. AUX is the diversity path and **GNSS** is a separate positioning-antenna connector. Never substitute an LTE antenna for the correct GNSS antenna.

| Board marking       | Function                                            | Connection rule                                                                     |
| ------------------- | --------------------------------------------------- | ----------------------------------------------------------------------------------- |
| VIN / GND           | 5–26V board input                                   | Use only the labeled input pair, with adequate current/thermal margin               |
| VBUS / GND          | USB 5V rail                                         | Not a 26V input                                                                     |
| BAT / GND           | 3.7V battery input                                  | Respect polarity and battery protection; not a charger instruction                  |
| TXD                 | Modem UART transmit                                 | Connect to host RX                                                                  |
| RXD                 | Modem UART receive                                  | Connect to host TX                                                                  |
| VIO                 | Level-translator reference                          | Leave unconnected for a 3.3V host; use documented 5V reference for a 5V MCU         |
| RST / PWK           | Reset / power-key control                           | Use exact schematic polarity/timing before driving; not required for USB first test |
| CTS / RTS           | UART flow control                                   | These are not the RST reset signal                                                  |
| FLT / DTR / RI      | Flight-mode / sleep-wake / incoming-event functions | Follow module/board logic reference before connecting                               |
| DP / DN             | USB data pair                                       | Preserve USB signal routing; do not wire to UART pins                               |
| VSIM / SC / SD / SR | SIM electrical signals                              | Do not apply external GPIO/power casually                                           |
| 3V3                 | Regulated board output                              | Do not treat as an unrestricted host supply                                         |

The [downloaded board schematic](https://files.waveshare.com/upload/8/89/SIM7600X_4G_Module.pdf) distinguishes **RST** from **RTS**; a duplicated “RTS” label in one product-table reset row is a documentation typo, not two reset pins. Use the schematic's header nets and actual silkscreen, not an inferred row number.

For Raspberry Pi UART: board TXD → Pi RX, board RXD → Pi TX, common GND, VIO left unconnected. Supply through the documented VIN/USB path. Disable the Linux serial login shell while enabling hardware UART in `raspi-config`; prefer the OS's stable `/dev/serial0` mapping after confirming the selected pins. A Pi UART is 3.3V logic. For a 5V UNO, the manufacturer's example uses digital pins 2/3 with a suitable software-serial library and **VIO referenced to 5V**; that logic selection does not power the modem from a GPIO.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

| Host / transport       | Supported starting point                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------- |
| Windows USB            | SIMCom USB driver, then the enumerated AT command port in Device Manager                    |
| Raspberry Pi/Linux USB | Kernel USB-serial drivers and modem composite ports; confirm actual AT port before using it |
| MCU UART               | 115200 baud example, crossed TX/RX, common ground and correct VIO                           |
| Data networking        | RNDIS, NDIS or PPP; firmware/USB composition and host driver must agree                     |
| GNSS                   | AT control and NMEA data, with a separate correct GNSS antenna                              |

The [SIMCom AT manual V3.00](https://files.waveshare.com/upload/a/af/SIM7500_SIM7600_Series_AT_Command_Manual_V3.00.pdf) is the command reference. Record `AT+CGMM` and `AT+CGMR` before making changes. Do not flash SIM7600E/CE firmware onto the G-H simply because a download name says SIM7600X.

For Arduino, the [official demo archive](https://files.waveshare.com/upload/2/29/SIM7600X-4G-HAT-Demo.7z) contains phone-call, SMS, GNSS, TCP and FTP examples. Review their host pin definitions and power controls against this compact board before reusing them. A demo for a HAT may assume GPIO power-key wiring absent from a USB-connected module.

## Getting started

### USB identity and registration check

1. Prepare the exact G-H module, active Nano SIM with the intended service, MAIN LTE antenna, a USB data cable and a stable host supply. Fit SIM/antenna while unpowered; leave external UART/battery/VIN disconnected for this first USB check.
2. Connect USB. On Windows install the official driver only if the composite devices are unrecognized, then select the **AT** port. On Linux list ports and inspect kernel messages:

```bash
ls -l /dev/serial/by-id/
ls /dev/ttyUSB*
```

3. Open the AT port at **115200**, 8 data bits, no parity, one stop bit. `/dev/ttyUSB2` is the vendor's example, not a universal device name. Send `AT` terminated with carriage return and expect `OK` before proceeding.
4. Use the following original diagnostic client to capture bounded, read-only queries. Install `pyserial` in a virtual environment, save as `modem_check.py`, then pass the actual AT port:

```bash
python3 -m venv modem-env
. modem-env/bin/activate
python -m pip install pyserial
python modem_check.py /dev/ttyUSB2
```

```python
import sys
import time
import serial

commands = ["AT", "AT+CGMM", "AT+CGMR", "AT+CPIN?", "AT+CSQ",
            "AT+COPS?", "AT+CPSI?", "AT+CGREG?", "AT+CGDCONT?"]
with serial.Serial(sys.argv[1], 115200, timeout=0.2) as modem:
    modem.reset_input_buffer()
    for command in commands:
        print("\n>", command)
        modem.write((command + "\r").encode("ascii"))
        modem.flush()
        deadline = time.monotonic() + 8
        terminal = False
        while time.monotonic() < deadline:
            line = modem.readline().decode("ascii", errors="replace").strip()
            if not line:
                continue
            print(line)
            if line in ("OK", "ERROR") or line.startswith(("+CME ERROR", "+CMS ERROR")):
                terminal = True
                break
        if not terminal:
            print("Timeout: verify the AT port and exclusive serial access")
            break
```

**Expected result:** `AT` returns `OK`, the model is G-H, firmware is readable, SIM reports `READY` and network queries show the current operator/system state. Registration or data access may take longer and depends on coverage; `OK` only proves the command was understood. No SIM serial/IMEI is queried by this example, and the script does not change APN, band masks or USB composition.

### Establishing an IP data path

Confirm SIM readiness, usable signal, network registration and the operator's APN first. Query `AT+CGDCONT?`; if a context must be changed, use the operator-supplied APN in `AT+CGDCONT=1,"IP","YOUR_OPERATOR_APN"`. Preserve the previous setting. An IoT SIM can need a different APN from a consumer SIM.

For Linux RNDIS, the [exact manufacturer procedure](https://www.waveshare.com/wiki/Raspberry_Pi_networked_via_RNDIS) uses `AT+CUSBPIDSWITCH=9011,1,1`, which **changes USB composition and restarts the modem**. Close the client, wait for re-enumeration and identify the new USB network interface with `ip -brief link`. Use the host's existing NetworkManager/DHCP service; on an image with `dhclient` the documented fallback is `sudo dhclient -v usb0`, substituting the actual interface. Do not start a second DHCP client over a manager-owned interface.

Check the assigned address, route and DNS separately:

```bash
ip -brief address
ip route
getent hosts example.com
```

The same vendor procedure lists `AT+CUSBPIDSWITCH=9001,1,1` as a return to its default composition. Record this recovery before switching. On Windows the [RNDIS guide](https://www.waveshare.com/wiki/SIM7600X_RNDIS_Dial-Up_on_Windows_10) explains choosing Microsoft's Remote NDIS Compatible Device when the new adapter is unrecognized. Do not combine an NDIS `AT$QCRMCALL=1,1` session and a different RNDIS/PPP recipe without understanding which interface owns the data path.

### Obtaining GNSS data and interpreting coordinates

Fit the correct GNSS antenna to GNSS, position it with a clear sky view and start positioning with `AT+CGPS=1`; poll `AT+CGPSINFO` at a modest rate. Empty coordinate fields mean no fix yet. An open-air cold-start reference is not a guaranteed indoor fix time. Finish the experiment with `AT+CGPS=0` if position updates are no longer needed. Command syntax and firmware support: [SIMCom AT manual](https://files.waveshare.com/upload/a/af/SIM7500_SIM7600_Series_AT_Command_Manual_V3.00.pdf).

GNSS latitude/longitude use degrees and minutes, not an ordinary decimal degree string. This original conversion routine accepts the raw numeric field and hemisphere; the values shown are illustrative, not a captured location:

```python
def decimal_degrees(raw, hemisphere):
    if not raw or hemisphere not in {"N", "S", "E", "W"}:
        raise ValueError("No valid fix or hemisphere")
    value = float(raw)
    degrees = int(value // 100)
    minutes = value - 100 * degrees
    if not 0 <= minutes < 60:
        raise ValueError("Invalid minutes")
    limit = 90 if hemisphere in {"N", "S"} else 180
    result = degrees + minutes / 60
    if result > limit:
        raise ValueError("Coordinate out of range")
    return -result if hemisphere in {"S", "W"} else result

print(decimal_degrees("5130.0000", "N"))  # expected 51.5
```

### SMS, TCP and FTP extension path

After registration/data checks, choose the manual's text/PDU SMS, TCP socket or FTP chapter and one official matching example. Record recipient/server, context, encoding and expected acknowledgement before transmission. Successful IP acquisition does not prove application login, TLS certificate handling or message delivery. Phone/SMS examples incur operator activity and should use a deliberate test destination; they are not part of the read-only first check.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                              | Ordered checks / supported recovery                                                                                                               |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| No USB ports or repeated disconnects | Check data cable, supply sag during transmit bursts, connector seating and host USB logs; disconnect extra power paths while isolating the issue  |
| AT timeout                           | Check AT versus NMEA/diagnostic port, CR terminator, correct baud and whether ModemManager/another terminal owns the port                         |
| `AT+CPIN?` error                     | Power down, reseat the Nano SIM, confirm contact orientation and SIM service in a known-good device                                               |
| SIM ready, no network                | MAIN antenna, service/bands, `AT+CFUN?`, operator status, signal and system query; preserve existing configuration before changing a network mode |
| Registered but no Internet           | APN/context, chosen USB composition, driver, DHCP address, route, DNS and operator policy, in that order                                          |
| UART fails but USB works             | Cross TX/RX, verify common ground, VIO selection and Linux console ownership; never drive 5V into a Pi UART                                       |
| No GNSS fix                          | Separate GNSS antenna, sky view, GNSS enabled state and sufficient acquisition time; empty fields are not zero coordinates                        |
| Apparent location offset             | Convert degrees/minutes and hemisphere correctly before comparing map coordinates; map coordinate systems can also differ                         |
| Reset pin ambiguous                  | Use the schematic RST net; RTS is UART flow control                                                                                               |
| Firmware update fails                | Exact G-H firmware, stable cable/power and update-port driver; preserve factory version and obtain the matched package before retrying            |

Avoid copying fixed LTE-only mode or band-mask settings from a generic FAQ. They can remove all usable coverage at the deployment location. Likewise a forced default route is not a substitute for diagnosing DHCP/route ownership.

## Downloads and technical documents

The board schematic was downloaded and visually inspected, including translator, power domains, SIM and antenna paths. The AT manual was downloaded as a separate command reference. Tools and archives listed below are manufacturer distributions; listing them is not an execution test.

| Resource                                                                                                              | Purpose and exact scope                                              |
| --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| [Board schematic](https://files.waveshare.com/upload/8/89/SIM7600X_4G_Module.pdf)                                     | Exact compact board, downloaded and visually reviewed                |
| [AT command manual V3.00](https://files.waveshare.com/upload/a/af/SIM7500_SIM7600_Series_AT_Command_Manual_V3.00.pdf) | Identity, network, SMS, GNSS, socket and file commands               |
| [Example archive](https://files.waveshare.com/upload/2/29/SIM7600X-4G-HAT-Demo.7z)                                    | Official shared host examples; adapt HAT power/pins carefully        |
| [Windows USB driver](https://files.waveshare.com/upload/2/24/SIMCOM_Windows_USB_Drivers_V1.0.2.zip)                   | Official V1.0.2 driver listing                                       |
| [Board 3D archive](https://www.waveshare.com/w/upload/a/aa/Sim7600x_4g_module.rar)                                    | Manufacturer-listed mechanical archive, not extracted in this review |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026**: exact G-H/standard-FPC SKU mapping, board wiki, manufacturer connection/pin reference, downloaded schematic and AT manual, and host-specific RNDIS procedures. The diagnostic client, coordinate conversion and commissioning sequence are original additions.

**Compilation, driver installation, modem commands, operator registration, IP traffic and GNSS hardware tests: not run.** Expected responses describe the intended checkpoint rather than a measured result.

* [SIM7600G-H compact board wiki](https://www.waveshare.com/wiki/SIM7600X_4G_Module) — snapshot 23 Nov 2026; reviewed 24 Nov.
* [Waveshare board schematic](https://files.waveshare.com/upload/8/89/SIM7600X_4G_Module.pdf) — undated manufacturer PDF, downloaded 24 Nov 2026.
* [SIMCom SIM7500/SIM7600 AT command reference](https://files.waveshare.com/upload/a/af/SIM7500_SIM7600_Series_AT_Command_Manual_V3.00.pdf) — V3.00.
* [Exact module power and UART reference](https://www.waveshare.com/product/sim7600g-h-4g-module.htm) — manufacturer page reviewed via web 24 Nov 2026.

### Retained source links <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

* [Exact standard SKU](https://dd.waveshare.net/shop/SIM7600G-H-4G-Module.htm)
