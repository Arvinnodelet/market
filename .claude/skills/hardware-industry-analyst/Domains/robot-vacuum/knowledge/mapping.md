# Mapping & Software Knowledge Base

## Purpose

Evaluate the software stack that converts sensor data into cleaning behavior — SLAM algorithms, map representation, room management, app UX, and smart home integration.

---

# Map Representation

## Map Types

| Type | Data | Storage | Best For |
|---|---|---|---|
| **2D Grid Map** | Occupancy grid (occupied/free/unknown) | Small (KB) | Budget, simple navigation |
| **2.5D Map** | Grid + height estimates | Medium (MB) | Mid-range, basic obstacle |
| **3D Point Cloud** | Full 3D coordinates + colors | Large (tens of MB) | Premium, semantic mapping |
| **Semantic Map** | Object-labeled 3D (chair, table, sofa, carpet) | Large | Flagship, smart home |

---

# SLAM Quality Assessment

| Metric | What to Assess | Entry | Mid | Premium |
|---|---|---|---|---|
| **Map Accuracy** | Wall deviation from actual | ±10–15 cm | ±5–10 cm | ±2–5 cm |
| **Loop Closure** | Returning to start position error | ±15–20 cm | ±5–10 cm | ±1–3 cm |
| **First Map Speed** | Time to map 100m² | 8–15 min | 3–8 min | 1–3 min |
| **Dynamic Environment** | Handles furniture moved mid-clean | Poor | Good | Excellent |
| **Dark Room Mapping** | Accuracy in 0 lux | Fail (vSLAM) / Good (LDS) | Good | Excellent |

---

# Room & Zone Management

## Features by Tier

| Feature | Budget (<$300) | Mid ($300–700) | Premium ($700+) |
|---|---|---|---|
| **Room Segmentation** | Manual only | Auto + manual | AI auto-segmentation |
| **Room Naming** | None or manual | Manual | AI recognition (kitchen/living/bedroom) |
| **Zone Cleaning** | None | Manual draw | Voice + app |
| **No-Go Zones** | None | Manual draw | AI-learned |
| **Pin & Go** | None | Yes | Yes |
| **Multi-Floor** | None | 2–3 floors | 5+ floors, auto-floor detection |

---

# Cleaning Algorithms

| Algorithm | Description | Best For |
|---|---|---|
| **Random Bounce** | Robot moves in straight lines, bounces off obstacles randomly | Legacy / ultra-budget |
| **Grid/Zigzag** | Systematic parallel lines | Standard cleaning |
| **Edge + Grid** | Perimeters first, then fill interior | Most robots |
| **Room-by-Room** | Complete one room before moving to next | Efficiency, battery life |
| **Deep Clean Zones** | User-defined areas with extra passes or max suction | High-traffic areas |
| **Auto-Adaptive** | Algorithm adjusts pattern based on room shape and detected dirt | Premium AI-driven |

---

# App & Smart Home Integration

## App Quality Assessment

| Dimension | What to Evaluate |
|---|---|
| **Map Interaction** | Pinch-to-zoom, rotate, 3D view, room tap to clean |
| **Scheduling** | Per-room schedules, time-of-day, day-of-week, vacation mode |
| **Real-Time Status** | Position, battery, cleaning time, area covered, water level |
| **Consumable Tracking** | Filter life, brush life, sensor cleaning reminders |
| **Remote Control** | Manual drive, video call, voice intercom, live camera view |
| **Firmware Updates** | OTA frequency, changelog quality, rollback capability |

## Smart Home Integration

| Ecosystem | Integration Depth | Examples |
|---|---|---|
| **Alexa** | Voice clean, pause, dock, room commands | Universal |
| **Google Home** | Voice clean, pause, dock | Universal |
| **Apple HomeKit** | Siri voice control | Select models (Roborock S8 MaxV) |
| **Xiaomi Mi Home** | Full native ecosystem | Xiaomi/Roborock/Dreame |
| **Matter** | Emerging standard | Limited adoption so far |

---

# Data Privacy & Security

| Aspect | What to Assess | Red Flags |
|---|---|---|
| **Camera Data** | On-device vs cloud processing | Cloud upload of home images |
| **Map Storage** | Local vs cloud | No local-only option |
| **Account Security** | 2FA, login methods | SMS-only verification |
| **Data Sharing** | Third-party data access | Unclear privacy policy |
| **Video Call** | End-to-end encryption | No encryption stated |

---

# Evaluation Matrix

| Software Dimension | Performance Impact | UX Impact | Development Complexity | Competitive Moat |
|---|---|---|---|---|
| **SLAM Algorithm** | 🔴 Critical | 🟡 Medium | Very High | 🔴 Strong moat |
| **Map Quality** | 🟠 High | 🟠 High | High | 🟠 Good moat |
| **AI Object Recognition** | 🟡 Medium | 🔴 Critical | Very High | 🔴 Strong moat |
| **App UX** | 🟢 None | 🔴 Critical | Medium | 🟡 Modest moat |
| **Smart Home Integration** | 🟢 None | 🟡 Medium | Low | 🟢 No moat |
| **OTA Updates** | 🟡 Medium | 🟡 Medium | Medium | 🟡 Modest moat |

---

# Industry Trends (2024–2026)

- **AI-based semantic mapping**: Object-level maps — "clean around the dining table" vs "clean the dining room"
- **Foundation models for home understanding**: Vision-language models identifying household objects
- **Matter protocol adoption**: Cross-platform smart home standard for robot vacuums
- **Privacy as premium differentiator**: On-device AI vs cloud-dependent; local map storage
- **Subscription models emerging**: iRobot Genius, advanced AI features with monthly fee
- **Open API for developers**: Roborock's HomeAssistant integration leads community ecosystem
