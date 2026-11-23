---
description: >-
  Use the U172 ToF4M VL53L1X sensor with the correct wiring, library, model
  distinctions and distance checks.
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# M5Stack Time-of-Flight Distance Unit (VL53L1X)

{% hint style="info" %}
[**View M5Stack ToF4M distance sensor on OpenELAB**](https://openelab.io/products/time-of-flight-distance-unit)

**Model:** Unit ToF4M · **Manufacturer code:** `U172` · **OpenELAB SKU:** `M5-U172` · VL53L1CXV0FY/1 sensor.
{% endhint %}

## Product overview

This guide covers the **U172 ToF4M**, not the older U010 ToF. Both use I2C address `0x29`, so an address scan alone cannot distinguish them. The former page mixed the U172 listing with VL53L0X instructions; use the ToF4M library and the hardware label when selecting a driver. [ToF4M official guide](https://docs.m5stack.com/en/unit/Unit_ToF4M), [older U010 guide](https://docs.m5stack.com/en/unit/Unit_ToF).

## Applications

Use ToF4M for a distance display, proximity experiment or measured-position prototype. Check readings against a fixed target at known distances before adding them to a control loop. A nominal range specification does not establish a safety-rated obstacle detector.

## Specifications

| Item                  | U172 ToF4M                         |
| --------------------- | ---------------------------------- |
| Sensor                | VL53L1CXV0FY/1; VL53L1X family     |
| Manufacturer range    | 4–400 cm                           |
| Data interface        | I2C, address `0x29`                |
| Field of view         | 15–27°, according to configuration |
| Operating temperature | 0–40 °C                            |
| Module dimensions     | 32 × 24 × 8 mm                     |

Values are manufacturer-reported for [U172](https://docs.m5stack.com/en/unit/Unit_ToF4M). The 2 m range, VL53L0X driver and ±3% figure in the old U010 description do not describe U172.

## Hardware and connections

The ToF4M Grove connection is **black: GND; red: 5 V; yellow: SDA; white: SCL**. The connector's supply marking is not permission to apply 5 V logic to a host GPIO. Follow the exact host's Port A pinout and the [U172 schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/626/UNIT-ToF4M.pdf). Connect with power removed and initially use only one sensor; two devices sharing `0x29` need a supported addressing or bus-isolation arrangement.

## Software and development resources

Use [M5Unit-ToF4M](https://github.com/m5stack/M5Unit-ToF4M), the library linked by the U172 manufacturer guide. Its README lists **M5GFX, M5Unified and VL53L1X** dependencies and an MIT license. Retain the downloaded source revision and dependency versions. Do not substitute the old `ToF_VL53L0X` example just because an I2C scan finds `0x29`. [Library and dependencies](https://github.com/m5stack/M5Unit-ToF4M).

## Getting started

1. Read the sensor label and confirm U172/ToF4M. Prepare a compatible M5Stack host, Grove cable and USB data cable.
2. With power off, connect ToF4M to the host's documented I2C port. Check that the selected host's SDA/SCL pins match the example; Core, Core2, CoreS3 and Atom ports differ.
3. Download the [official library](https://github.com/m5stack/M5Unit-ToF4M), install its declared dependencies and inspect [examples/Continuous/Continuous.ino](https://github.com/m5stack/M5Unit-ToF4M/blob/main/examples/Continuous/Continuous.ino). Its header records Arduino M5Stack Board Manager **v2.0.7**. For a different host configuration, make the bus explicit as shown below; retain the actual package/library versions. Build before uploading.
4. Start with a stationary, matte target in range. Save the displayed distance and status at two known positions, along with units and the software revision. Keep invalid/out-of-range status separate from a numerical distance.

**Expected result:** the supported example initializes U172 and its distance changes consistently as the target moves. A successful scan is only a bus checkpoint. **Observed result:** not run; no physical device or compile result was available for this review. The [official Arduino/UIFlow resources](https://docs.m5stack.com/en/unit/Unit_ToF4M) provide the model's maintained examples.

### Arduino

**Explicit CoreS3 Port A bus.**

This OpenELAB adaptation targets **CoreS3 K128 Port A, SDA2/SCL1**, with M5Unified and Pololu's VL53L1X library. The official sample initializes `M5.Ex_I2C` but assigns the sensor to `Wire`; when porting it, ensure both operations refer to the same physical bus. The following version initializes `Wire` explicitly. It preserves the sample's 50 ms timing budget/period and checks measurement status. It has **not been compiled or run on hardware**. [CoreS3 pin map](https://docs.m5stack.com/en/core/CoreS3), [original sample](https://github.com/m5stack/M5Unit-ToF4M/blob/main/examples/Continuous/Continuous.ino), [VL53L1X API and units](https://github.com/pololu/vl53l1x-arduino).

```cpp
#include <M5Unified.h>
#include <Wire.h>
#include <VL53L1X.h>

VL53L1X distanceSensor;

void setup() {
  M5.begin();
  Serial.begin(115200);
  Wire.begin(2, 1, 400000);  // CoreS3 Port A only: SDA, SCL, Hz
  distanceSensor.setBus(&Wire);
  distanceSensor.setTimeout(500);
  if (!distanceSensor.init()) {
    Serial.println("U172 initialization failed; check model and Port A");
    while (true) { delay(1000); }
  }
  distanceSensor.setDistanceMode(VL53L1X::Long);
  distanceSensor.setMeasurementTimingBudget(50000);  // microseconds
  distanceSensor.startContinuous(50);               // milliseconds
}

void loop() {
  const uint16_t rangeMm = distanceSensor.read();
  if (distanceSensor.timeoutOccurred()) {
    Serial.println("No fresh range: timeout");
  } else if (distanceSensor.ranging_data.range_status != VL53L1X::RangeValid) {
    Serial.println("Range status invalid; do not use this sample");
  } else {
    Serial.printf("Range: %u mm\n", static_cast<unsigned>(rangeMm));
  }
}
```

Do not reuse pins 2/1 on another host without its pin map. Keep the serial connection at 115200 baud. A valid range remains a sensor reading, not a validated safety or motion-control signal.

## Troubleshooting and FAQs

**No I2C response:** check power, cable orientation, actual host pins and another device at the same address. Reconnect only with power removed.

**Address responds but driver initialization fails:** compare the hardware label and installed library. U010/VL53L0X and U172/VL53L1X share the address; their drivers are not interchangeable.

**Distance is implausible or intermittent:** first check range/status, target surface and ambient light; then compare a fixed target and the supplied example before changing timing parameters. Do not convert an invalid measurement into a zero-distance reading.

### UIFlow

Use the model-specific UIFlow resources in the [U172 guide](https://docs.m5stack.com/en/unit/Unit_ToF4M). Confirm the runtime generation and host; the retained U010 screenshots below do not establish a U172 configuration.

## Downloads and technical documents

| Resource                                                                                                          | Scope                                                                      |
| ----------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| [U172 official guide](https://docs.m5stack.com/en/unit/Unit_ToF4M)                                                | Specifications, pin map, drawings, datasheet, comparisons and UIFlow links |
| [Schematic PDF](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/626/UNIT-ToF4M.pdf)                              | Electrical connections for ToF4M                                           |
| [Official Arduino library](https://github.com/m5stack/M5Unit-ToF4M)                                               | Host examples and dependencies                                             |
| [Mechanical source files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U172_Unit_ToF4M/Structures) | U172 structure, as linked by M5Stack                                       |

## References and validation

Sources reviewed **23 November 2026**. Arduino compilation and hardware tests were **not run**. This correction resolves the U010/U172 documentation mismatch; it does not claim a measured range or tested host combination. Use the official resource links for the current revision and complete example source.

## Existing illustrations

The following illustrations are retained from the earlier **U010/VL53L0X** page. They are historical references, **not U172 wiring or UIFlow instructions**. Use the U172 links above for ToF4M.

<figure><img src="../../.gitbook/assets/image (543).png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/TOF/uiflowCase-1689302874150UIFLOW.png" alt=""><figcaption></figcaption></figure>
