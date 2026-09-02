# Navigation Systems Knowledge Base

## Purpose

Evaluate navigation technologies used in robot vacuums — LiDAR SLAM, vSLAM, dToF, and hybrid approaches. Covers mapping speed, accuracy, reliability in different environments, and manufacturing cost implications.

---

# LiDAR SLAM (Laser Distance Sensor)

## Principle

360° rotating laser turret emits infrared pulses and measures time-of-flight to build a 2D point cloud of the room. SLAM algorithm uses the point cloud for simultaneous localization and mapping.

## Typical Specs

| Metric | Entry | Mid | High-End |
|---|---|---|---|
| Scan Rate | 5–6 Hz | 6–8 Hz | 8–10 Hz |
| Range | 8–10 m | 10–12 m | 12–16 m |
| Angular Resolution | 0.5–1.0° | 0.3–0.5° | 0.15–0.3° |
| Mapping Speed | 2–4 min/100m² | 1–3 min/100m² | <1 min/100m² |

## Advantages

- Works in complete darkness (active illumination)
- Fast initial mapping — 360° scan in one rotation
- High accuracy for wall-following and room perimeter
- Mature technology, well-understood
- Low compute requirements (2D point cloud)

## Disadvantages

- Mechanical turret — moving parts, wear/failure point
- Turret adds height (~3–5cm) to robot profile
- Cannot detect transparent obstacles (glass doors/windows)
- Limited furniture detail (2D only — sees legs as circles)
- Dust/debris can foul turret bearing over time

## Typical Implementations

- Roborock: Custom LDS turret on all Qrevo and S-series
- Ecovacs: dToF LiDAR (solid-state) on X series
- Dreame: Custom LDS with modulated laser
- Xiaomi: Off-the-shelf SLAMTEC RPLIDAR on budget models

---

# vSLAM (Visual SLAM)

## Principle

Monocular or binocular camera captures visual features (edges, corners, textures). SLAM algorithm tracks features frame-to-frame to estimate pose and build a sparse/dense map.

## Typical Specs

| Metric | Monocular vSLAM | Stereo vSLAM | RGB-D vSLAM |
|---|---|---|---|
| Depth Accuracy | Low (scale ambiguity) | Medium | High |
| Light Dependency | High | High | Medium (active IR) |
| Compute Requirement | Medium | High | High |
| Cost | Low | Medium | High |

## Advantages

- No mechanical turret — lower profile robot (can go under furniture)
- Rich visual information — furniture type, room type recognition
- Potential for object-level mapping (chair, table, sofa)
- Camera can serve dual-purpose (obstacle avoidance + mapping)

## Disadvantages

- Requires ambient light (fails in dark rooms unless IR illuminator)
- Higher compute requirements (ISP + neural network)
- Feature-poor environments (plain walls, uniform floors) cause drift
- Privacy concerns (camera in home)

## Typical Implementations

- iRobot: vSLAM on Roomba j9/combo — ceiling-facing camera
- Dyson: 360° panoramic camera + vSLAM (discontinued)
- Budget robots: Downward-facing optical flow (not true vSLAM)

---

# dToF (Direct Time-of-Flight)

## Principle

Infrared laser array emits modulated light pulses; SPAD (Single Photon Avalanche Diode) sensor array measures return time for each pixel. Produces a 3D depth map at video frame rates.

## Advantages

- Solid-state (no moving parts)
- 3D depth information (not just 2D slices)
- Works in dark (active IR illumination)
- Small form factor (can be embedded in bumper)
- High refresh rate (15–30 fps)

## Disadvantages

- Higher cost than mechanical LDS
- Range typically shorter than LDS (6–8m vs 12–16m)
- Sunlight interference (IR from sun saturates SPAD array)
- Manufacturing calibration complexity

## Typical Implementations

- Ecovacs: dToF on X2/X5 series — solid-state front-facing
- Roborock: ReactiveAI 2.0 (dToF + RGB camera)
- Dreame: 3D structured light (near-infrared speckle pattern)

---

# Hybrid Navigation

## Principle

Combines multiple sensors — typically LDS + camera + dToF — fusing data for robust navigation in all conditions.

## Advantages

- Best of all worlds — LDS speed + visual detail + 3D obstacle
- Graceful degradation (if one sensor fails, others compensate)
- Premium positioning (table-stakes for flagship tier)

## Disadvantages

- Highest BOM cost (3+ sensors)
- Complex sensor fusion software
- Calibration requirements between coordinate frames

## Typical Implementations

- Roborock S8 MaxV Ultra: LDS + RGB + dToF + IR structured light
- Dreame X40 Ultra: LDS + RGB + 3D structured light
- Ecovacs X5 Pro: dToF LiDAR + RGB + AI camera

---

# Evaluation Matrix

| Technology | Accuracy | Speed | Dark Performance | Reliability (no moving parts) | BOM Cost | Best For |
|---|---|---|---|---|---|---|
| **Mechanical LDS** | High | Fast | Excellent | Medium (turret wear) | Low-Medium | Mid-range, dark homes |
| **Monocular vSLAM** | Medium | Medium | Poor | High | Low | Budget, well-lit homes |
| **Stereo vSLAM** | High | Slow | Medium (IR) | High | Medium-High | Premium visual mapping |
| **dToF** | High | Fast | Good | Very High | Medium-High | Premium solid-state |
| **Hybrid (LDS+RGB+dToF)** | Very High | Fast | Excellent | Medium | High | Flagship |

---

# Industry Trends (2024–2026)

- **Solid-state replacing mechanical LDS**: dToF and solid-state LiDAR gradually replacing spinning turrets in premium segment
- **RGB camera as standard on mid-range+**: Obstacle avoidance + visual mapping + video call features
- **AI-based semantic mapping**: Identifying furniture types, room types, and dirt patterns
- **Multi-floor memory with auto-recognition**: Saved maps for different floors, auto-detection of which floor
- **Navigation compute moving to NPU**: On-device inference for real-time obstacle classification
