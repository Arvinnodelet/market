# UV Printer Sensors Knowledge

## 1. Role

Sensors provide position, material, ink-system, thermal, optical, and safety feedback required for stable printing.

```text
Sensors
  ├─ Position / Motion
  ├─ Ink System
  ├─ Temperature
  ├─ Printhead / Head Gap
  ├─ UV Curing
  ├─ Media / Substrate
  └─ Safety
```

## 2. Sensor Categories

| Category | Typical Sensor | Purpose | Research Questions |
|---|---|---|---|
| Position | Encoder | Measure carriage/feed position | Resolution? Linear or rotary? |
| Limit | Optical/mechanical switch | Homing / travel protection | Redundant protection? |
| Ink level | Float, capacitive, optical or pressure-based | Detect ink availability | Continuous or threshold? |
| Ink pressure | Pressure sensor | Maintain stable ink delivery | Closed-loop control? |
| Ink temperature | RTD / thermistor | Control viscosity | Heating/cooling range? |
| Printhead temperature | Thermistor / integrated sensor | Protect and stabilize head | Monitoring or active control? |
| UV temperature | Thermistor / thermal sensor | Protect LED/curing assembly | Derating / shutdown? |
| UV output | Optical monitoring where implemented | Detect curing degradation | Closed-loop or maintenance check? |
| Head height | Distance / position sensing | Maintain head-to-substrate gap | Automatic detection? |
| Media presence | Optical / mechanical | Detect substrate | Does printing interlock with detection? |
| Door / cover | Switch / Hall / optical | Safety interlock | What motion/UV functions are disabled? |
| Vacuum | Pressure sensor / switch | Verify table vacuum | Fault detection? |
| Waste ink | Float / optical / level sensor | Prevent overflow | Warning and shutdown thresholds? |

## 3. Motion Feedback

Encoder feedback is particularly important for print registration.

```text
Encoder Position
      ↓
Motion Controller
      ↓
Carriage / Media Position
      ↓
Printhead Firing Timing
```

For systems without full servo feedback, stepper motion may rely primarily on commanded position plus homing and calibration.

## 4. Ink-System Feedback

Monitor:

- Ink level
- Supply pressure
- Return pressure where applicable
- Ink temperature
- Filter condition if sensed
- White-ink circulation state where available
- Waste-ink level

The presence of a sensor does not imply closed-loop control; verify the control architecture.

## 5. Head / Media Distance

Head-to-substrate distance strongly affects droplet placement and collision risk.

Research:

- Fixed mechanical gap
- Manual height adjustment
- Automatic height sensing
- Collision detection
- Media thickness detection

## 6. UV Monitoring

Some systems monitor UV module temperature and/or optical output. Many desktop systems may instead use open-loop UV power control plus maintenance replacement criteria.

Do not assume closed-loop UV-dose control without evidence.

## 7. Safety Sensors

Potential interlocks include:

- Cover/door switch
- Emergency stop
- Over-temperature protection
- Carriage collision detection
- UV enclosure interlock
- Vacuum/media fault
- Ink starvation protection

## 8. Sensor Architecture

A useful analysis should distinguish:

```text
Sensor
 ↓
Signal Conditioning
 ↓
ADC / Digital Input / Encoder Interface
 ↓
MCU / Motion Controller
 ↓
Control Logic
 ↓
Actuator
```

## 9. Research Indicators

For each important sensor identify:

- Sensor type
- Measurement range
- Resolution / accuracy if disclosed
- Sampling rate where relevant
- Interface
- Calibration method
- Open-loop vs closed-loop use
- Fault threshold
- Redundancy
- Effect on product reliability

## 10. Research Rule

Do not infer sensor presence from a feature description alone. Distinguish physically observed sensors, documented sensors, inferred sensors, and software-only status indicators.
