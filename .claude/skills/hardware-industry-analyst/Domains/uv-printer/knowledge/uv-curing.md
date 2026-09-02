# UV Curing Knowledge

## 1. Principle
UV curing uses ultraviolet radiation to activate photoinitiators and convert reactive components in the ink into a solid polymer network.

```text
UV Light
  ↓
Photoinitiator Excitation
  ↓
Reactive Species
  ↓
Polymerization / Cross-linking
  ↓
Cured Film
```

## 2. Key Parameters

### Wavelength
The UV source spectrum must overlap the absorption characteristics of the photoinitiator system.

### Irradiance
Irradiance is instantaneous optical power per unit area, commonly expressed in W/cm².

### Dose
UV dose is accumulated energy per unit area, commonly expressed in J/cm².

Conceptually:

```text
Dose ≈ Irradiance × Exposure Time
```

Actual cure performance depends on spectral distribution and process conditions, so this relation should not be treated as a complete curing model.

## 3. Curing Geometry

Analyze:
- LED position relative to printhead
- Distance to substrate
- Exposure width
- Irradiation angle
- Carriage speed
- Number of passes
- Shadowing / shielding
- Cooling architecture

## 4. Cure Timing

Curing can occur immediately after deposition or through controlled exposure during subsequent motion.

The timing affects:
- Dot spreading
- Layer interaction
- Adhesion
- Surface gloss
- Texture
- Final mechanical properties

## 5. Under-Cure

Potential symptoms:
- Sticky or soft surface
- Poor scratch resistance
- Poor chemical resistance
- Odor
- Weak adhesion

Possible causes:
- Insufficient dose
- Incorrect wavelength
- Excessive print speed
- Excessive ink thickness
- Pigment absorption
- Photoinitiator mismatch

## 6. Over-Cure

Potential effects:
- Excessive brittleness
- Surface defects
- Gloss changes
- Color changes
- Excessive shrinkage
- Substrate damage

## 7. Pigment and Layer Effects

Dark or highly pigmented inks can reduce UV penetration. White ink can also alter optical absorption and scattering.

For multi-layer printing, evaluate curing through the complete printed stack rather than only a single ink layer.

## 8. Thermal Management

UV LEDs generate heat. Analyze:
- LED board design
- Heat sink
- Fan / liquid cooling
- Temperature monitoring
- Thermal isolation from printhead and substrate

Thermal behavior can affect LED lifetime, ink viscosity, substrate deformation and process stability.

## 9. Research Indicators

Look for:
- UV wavelength
- Irradiance
- Dose or energy density
- LED power
- Cooling method
- LED lifetime
- Curing distance
- Carriage speed
- Recommended ink thickness

If only LED electrical power is disclosed, do not equate it directly with optical irradiance at the substrate.