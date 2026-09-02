# UV Printing Principle Knowledge

## 1. Core Principle
UV printing is a digital inkjet printing process in which UV-curable ink droplets are deposited onto a substrate and then polymerized by ultraviolet light.

The process can be understood as:

```text
Image Data
  ↓
RIP / Rasterization
  ↓
Halftone / Drop Generation
  ↓
Printhead Jetting
  ↓
Droplet Flight
  ↓
Impact / Wetting / Spreading
  ↓
UV Exposure
  ↓
Polymerization
  ↓
Cured Ink Film
```

## 2. Inkjet Deposition

Most desktop UV printers use Drop-on-Demand inkjet technology. The printhead selectively ejects droplets from individual nozzles according to image data.

Key variables:
- Nozzle count
- Nozzle pitch
- Drop volume
- Jetting frequency
- Drop velocity
- Drop placement accuracy
- Variable-drop capability
- Printhead temperature

## 3. Droplet Formation

For a piezoelectric printhead, an electrical waveform deforms a piezoelectric actuator and creates pressure waves in the ink chamber.

```text
Electrical Waveform
        ↓
Piezo Actuation
        ↓
Pressure Wave
        ↓
Meniscus Deformation
        ↓
Droplet Ejection
```

Research should distinguish the printhead's physical capability from the printer's configured operating point.

## 4. Droplet Flight

After ejection, droplet behavior depends on:
- Initial velocity
- Drop volume
- Viscosity
- Surface tension
- Air resistance
- Printhead-to-substrate distance
- Temperature

Satellite droplets or unstable trajectories can reduce image quality and increase nozzle contamination.

## 5. Impact and Wetting

The deposited droplet interacts with the substrate before and during curing.

Important variables:
- Surface energy
- Contact angle
- Roughness
- Porosity
- Coating
- Ink surface tension
- Ink viscosity

A droplet that jets correctly can still produce poor print quality if wetting and spreading are poorly controlled.

## 6. Curing

UV exposure converts the deposited liquid ink into a cross-linked polymer network. Curing must be coordinated with deposition and motion.

Important parameters:
- UV wavelength
- Irradiance
- Exposure time
- UV dose
- Ink thickness
- Pigment loading
- Photoinitiator system

## 7. Image Formation

UV printers normally use halftoning rather than placing one physical droplet for every image pixel.

```text
Continuous-tone Image
        ↓
Rasterization
        ↓
Halftone Pattern
        ↓
Drop Placement
        ↓
Physical Dot Pattern
```

Therefore, nominal DPI should not be treated as equivalent to visual resolution.

## 8. Pass Strategy

Multi-pass printing can improve uniformity by distributing droplets across multiple carriage passes, but normally reduces throughput.

Trade-off:

```text
More Passes
   ↓
Better Dot Distribution / Fewer Artifacts
   ↓
Higher Print Time
```

## 9. Multi-layer Printing

White ink, color ink, varnish, and texture may be printed in different layer sequences.

Typical conceptual structures include:
- Color only
- White → Color
- Color → White
- White → Color → Varnish
- Multiple texture layers

Layer order depends on substrate, desired appearance, transparency, and product architecture.

## 10. Research Indicators

When analyzing a UV printer, investigate:
- Printhead model
- Number of channels
- Drop volume
- Native nozzle resolution
- Maximum firing frequency
- Pass modes
- Carriage architecture
- Printhead-to-substrate distance
- UV wavelength
- Ink type
- White / varnish architecture

Do not infer image quality directly from advertised DPI or print speed.