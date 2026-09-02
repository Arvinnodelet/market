# UV Printer Printhead Knowledge

## 1. Role
The printhead is the core print-engine component responsible for converting ink into controlled droplets.

A useful analysis separates:
- Printhead physical capability
- Ink compatibility
- Drive waveform
- Printer operating parameters
- Resulting print quality

## 2. Common Architecture

Desktop UV systems commonly use piezoelectric Drop-on-Demand printheads.

Important characteristics:
- Nozzle count
- Nozzle pitch
- Channel count
- Native resolution
- Drop volume
- Variable-drop capability
- Jetting frequency
- Ink viscosity range
- Surface tension range
- Operating temperature

## 3. Waveform

The electrical waveform strongly influences droplet formation.

```text
Drive Voltage / Waveform
        ↓
Piezo Actuator
        ↓
Pressure Wave
        ↓
Meniscus Motion
        ↓
Droplet
```

The same printhead can behave differently with different ink formulations and waveforms.

## 4. Resolution

Distinguish:
- Native nozzle density
- Carriage-direction addressability
- Effective image resolution
- Multi-pass resolution

High nominal DPI does not automatically mean higher visible detail.

## 5. Drop Size

Smaller droplets can improve fine detail and tonal control, but may reduce deposited mass per firing and increase sensitivity to environmental and jetting conditions.

Variable-drop printheads can combine small and large drops to balance detail and coverage.

## 6. Printhead-to-Substrate Distance

Distance affects:
- Drop placement
- Satellite formation
- Dot size
- Image sharpness
- Tolerance to substrate height variation

A larger gap generally increases flight distance and can make placement more sensitive.

## 7. Ink Compatibility

Research should check whether the printhead is designed for:
- UV-curable ink
- Specific viscosity range
- Specific surface tension range
- Specific particle size
- Specific curing chemistry

Printhead compatibility should not be inferred merely because the ink is marketed as UV ink.

## 8. Nozzle Health

Key failure modes:
- Clogged nozzle
- Deflected nozzle
- Missing nozzle
- Satellite droplets
- Uneven drop volume

Typical countermeasures:
- Purging
- Wiping
- Capping
- Cleaning cycles
- Nozzle compensation
- Ink circulation

## 9. Evaluation Framework

When comparing printheads, evaluate:

| Dimension | Questions |
|---|---|
| Image quality | What drop sizes and placement accuracy are achievable? |
| Speed | What firing frequency and nozzle count are available? |
| Reliability | How sensitive is the head to clogging and contamination? |
| Ink compatibility | What viscosity, surface tension and chemistry are supported? |
| Cost | What is the replacement cost and service availability? |
| Integration | How difficult are electronics, waveform and mechanical integration? |

## 10. Research Evidence

Prefer:
1. Printhead manufacturer datasheets
2. Ink compatibility documentation
3. Printer service manuals
4. Teardown / repair evidence
5. Manufacturer product specifications

If the printer manufacturer does not disclose the printhead model, record it as Unknown rather than identifying it from appearance alone.