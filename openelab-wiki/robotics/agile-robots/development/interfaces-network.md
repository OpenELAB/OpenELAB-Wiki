# Agile Robots training 4: interfaces and programming routes

{% hint style="info" %}
Choose the actual controller, software interface and power domain before developing. First result: a verified connection/endpoint map; no peripheral outputs are toggled.
{% endhint %}

## Network and controller map

| Interface                  | Documented purpose                                                               |
| -------------------------- | -------------------------------------------------------------------------------- |
| Ethernet A                 | PC soft pendant and Industrial API; Diana FCI manual also specifies A            |
| Ethernet D                 | Application TCP/IP and Modbus TCP                                                |
| Ethernet B/C               | Reserved/unsupported in supplied controller manuals                              |
| Physical pendant           | Dedicated connector; remote endpoint normally 192.168.1.75:6050                  |
| PC soft pendant            | Normally 192.168.10.75:6050 on the controller network                            |
| Diana FCI                  | Factory 192.168.10.75, TCP 1337; real-time UDP is separate                       |
| Ordinary versus safety I/O | Different interfaces and validation; ordinary network data is not the stop chain |

Sources: [CB-FS-3.2T Controller User Manual V1.0.1.pdf, PDF pp. 23–27](../source-library/); [RCB2.1.1T-0.3KW Controller User Manual V1.2 EN.pdf, PDF pp. 30–33](../source-library/); [Industrial Teaching Pendant Software User Manual\_V3.3.0\_EN\_20260204.pdf, PDF pp. 190–191](../source-library/); [How to Use FCI on Diana7（English version）V1.3-20260209.pdf, PDF pp. 4, 13–15](../source-library/). Actual delivery settings take precedence.

## Pick the programming layer

| Route                                            | Scope                                                                                    |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------- |
| [Industrial C/C++ and Python](industrial-api.md) | External host, DianaApi, SI units and model-specific joint count                         |
| [Pendant Python scripting](pendant-python.md)    | Runs inside the pendant project with a supplied context, distinct from external DianaApi |
| [Pendant Lua](pendant-lua.md)                    | Robot command interface inside project; mm/ms/degrees                                    |
| [Diana FCI adaptation](diana-fci.md)             | Specific FS configurations; real-time control requires a verified matched client         |
| [Franka development](../../franka/development/)  | Separate FR3 controller/network/System Image/library matrix                              |

## First result: document the endpoints

1. Record exact cabinet model, software/configuration, intended host and interface role. Use [the verified UI route](system-startup.md) first.
2. On the isolated PC-controller subnet, choose a unique host address such as `192.168.10.136/24` only if unused. Inspect the OS route and controller address; do not assign .75 to the PC or assume the old subnet is unchanged.
3. Inspect the pendant network settings/status without applying remote changes. The manual says changing remote network configuration restarts the cabinet. A successful ping only checks reachability.
4. List application-device endpoint, protocol master/slave role, timing, timeout and expected read-only result. For ordinary I/O record common-group NPN/PNP selection and separate supply/load budgets before wiring.
5. For serial, tool RS485, Modbus or Profinet obtain the actual device protocol/register map and licensed/fitted options. Do not infer Profinet support solely from an Ethernet socket or a bus function's presence in the Lua manual.

**Expected result:** an interface map with no shared address, mismatched connector or unresolved supply assumption. Subsequent API/state inspection is covered separately; peripheral actuation requires its own accepted procedure.

## Tool electrical differences

Diana 3 tool power is pin 3/GND pin 1; the documented Thor 7/12/20 arrangement is power pin 7/GND pin 8. Both are M8 eight-pin female connectors in these manuals, so physical similarity is insufficient. The Thor RS485A description conflict blocks its wiring until confirmed. Diana 7, Thor 3 and Thor 7 Pro must not inherit those ports without delivery evidence. See [tool integration](coordinates-tools.md).

## Troubleshooting

Wrong port/role: compare A/D and master/slave configuration. Disconnects: retain logs and version pairing, inspect routing/firewall rules on the isolated interface without disabling broad host protection. Device input mismatch: isolate and check signal/common/reference before writing outputs. Never use an output-connected actuator as the first network test.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                               | Coverage  |
| --------------------------------------------------------------------------------------------------------------------- | --------- |
| [Agile Robots training 4 — Interfaces and Programming](../source-library/complete-en-4-interfaces-and-programming.md) | 29 slides |

### Programming contexts and side effects

The twenty-nine slides retain soft-pendant environment setup, script creation/error checks, system calls, robot-control examples and serial/TCP/UDP communication. The source's Ubuntu/Qt and Windows runtime examples describe its delivered pendant package; they are not a verified compatibility claim for an arbitrary current OS or SDK release.

Pendant Python receives the runtime's `context`; the external Industrial Python API uses its own delivered module and network initialization. Do not mix their imports, signatures, return conventions or units. The examples include logging and variable reads, but also variable writes, subprogram control, enable/stop paths, motion, impedance, force mode, payload changes and output writes. Classify a call by its effect, not by whether it is called an example.

Use a log-only first result in an isolated new script, then a documented read-only state query with the correct joint count. Preserve source example formatting issues—smart quotes, indentation and inconsistent variables—in the complete reference, while checking a working script against the installed API definition. The example IP addresses, serial devices and ports need an actual delivery-specific mapping.

Communication examples additionally need timeouts, framing, partial-read/write handling and deliberate resource cleanup. Opening a socket or receiving bytes does not prove that an application message was accepted or that an actuator action completed. A stop or returned motion status is not a safety-rated protective function.

### Source chapter map

| Source section                                        | Full detail                                                                      |
| ----------------------------------------------------- | -------------------------------------------------------------------------------- |
| Advanced Training                                     | [Slide 1](../source-library/complete-en-4-interfaces-and-programming.md#slide-1) |
| Interfaces and Programming                            | [Slide 2](../source-library/complete-en-4-interfaces-and-programming.md#slide-2) |
| 1. Environment Setup and Preparation                  | [Slide 3](../source-library/complete-en-4-interfaces-and-programming.md#slide-3) |
| 1. Environment Setup and Preparation (2)              | [Slide 4](../source-library/complete-en-4-interfaces-and-programming.md#slide-4) |
| 1. Environment Setup and Preparation (3)              | [Slide 5](../source-library/complete-en-4-interfaces-and-programming.md#slide-5) |
| 2. API Usage Examples in Python                       | [Slide 6](../source-library/complete-en-4-interfaces-and-programming.md#slide-6) |
| 2.1 System Call Function Description and Examples     | [Slide 7](../source-library/complete-en-4-interfaces-and-programming.md#slide-7) |
| 2.1 System Call Function Description and Examples (2) | [Slide 8](../source-library/complete-en-4-interfaces-and-programming.md#slide-8) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
