# MATEKSYS H743-SLIM V4 Flight Controller Engineering Guide

[Product at OpenELAB](https://openelab.io/products/matek-h743-slim-v4-drone-flight-controller)

### Identity and development scope

**MATEK-H743-SLIM-V4** is a flight-controller board for custom vehicles and autopilot development. The SLIM V4 has a different sensor and power configuration from WING, MINI, WLITE and older SLIM boards. Family firmware support does not make their wiring interchangeable.

The manufacturer currently labels this board EOL. Preserve the exact revision's wiring diagram and known-working firmware when maintaining an existing vehicle.

### Specifications and connections

| Item                | SLIM V4                                                 |
| ------------------- | ------------------------------------------------------- |
| MCU                 | STM32H743VIH6, 480MHz; 1MB RAM, 2MB flash               |
| Inertial sensors    | Two ICM42688P IMUs                                      |
| Barometer / OSD     | DPS368 / AT7456E                                        |
| Expansion           | Seven UARTs, two I2C buses, one CAN interface           |
| Outputs             | 13 PWM-capable outputs, including the LED pad           |
| Logging             | microSD socket                                          |
| Supply              | 6–36V input, corresponding to the documented 2–8S range |
| Regulated output    | 5V BEC, 2.5A continuous, 3A maximum                     |
| Current measurement | No built-in current sensor                              |
| USB                 | USB-C, USB 2.0                                          |

The official product page contains the board drawings and pin maps. Verify pad names against the physical PCB. Do not substitute WING-family sensor or servo-BEC values into a SLIM V4 design.

### Bench setup before installing a vehicle

1. Remove propellers and disconnect actuators or other hazardous loads. Photograph the board revision and current wiring.
2. Connect the controller to the computer with a USB data cable. Use the configuration software for the selected autopilot ecosystem.
3. Select the **MATEKH743** target documented by MATEKSYS for ArduPilot, Betaflight or INAV. Follow that project's installation and bootloader procedure; the applications and parameter sets are separate.
4. Confirm the controller connects, reports its firmware version and displays plausible attitude changes when the board is tilted.
5. Configure board orientation and calibrate sensors using the firmware's own workflow. Reboot and verify persistence before adding radio, GPS, CAN devices or motor outputs.

**Expected result:** reliable configuration access and correct attitude response on a stationary bench. This is not flight readiness.

### Software, diagnostics and recovery

Save a parameter export and the exact firmware version after the initial checks. Use the official firmware project's supported configuration tools; there is no universal Python SDK that replaces autopilot setup.

If USB does not enumerate, first change the cable/port and disconnect peripherals. For firmware recovery, use the board's documented boot/DFU procedure and the chosen project's flashing guide.

### FAQs

**Why does a family guide show different IMUs?** The family includes multiple revisions; SLIM V4's product-specific specification takes precedence.

**Can I calculate battery current immediately?** The board lacks an integrated current sensor. Install and calibrate a suitable external sensor.

**Can any PWM/DShot mix be used?** Timer-group constraints depend on firmware and output grouping. Check the selected firmware documentation before assigning outputs.

### Sources and validation

* [MATEKSYS H743-SLIM V4 specifications and wiring](https://www.mateksys.com/?portfolio=h743-slim-v4)
* [MATEKSYS firmware target references](https://www.mateksys.com/?p=5159)
* [ArduPilot Matek H743 family documentation](https://shop.ardupilot.org/sub/docs/common-matekh743-wing.html)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
