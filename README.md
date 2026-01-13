# HomGar Home Assistant Integration

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

Home Assistant integration for HomGar / RainPoint / Diivoo devices.

This project is forked from Remboooo/homgarapi and adapted for Home Assistant usage.

---

## ⚠️ Important Notice (HomGar Weather Stations)

This fork extends the original integration to properly support **HomGar weather stations with RF sub-devices**, including:

- Weather hub (modelCode **257**)
- Embedded weather station (modelCode **85**)
- Multiple indoor RF sensors (modelCode **86**)

These devices expose **hierarchical data structures** that were not fully handled in the original implementation.

---

## ✨ What’s New in This Fork

### ✅ Proper HomGar Weather Station Support

HomGar weather setups consist of:
- **One hub (modelCode 257)** – gateway only, no sensor data
- **One embedded weather station (modelCode 85)** – temperature, humidity, pressure
- **Multiple indoor sensors (modelCode 86)** – temperature & humidity only

This fork introduces:
- Clear separation between **hub** and **sensor roles**
- Correct parsing of `D01` payloads
- No duplicate entities
- Stable unique IDs

### 🧠 Correct Data Mapping

| Model | Role | Sensors |
|-----|-----|--------|
| 257 | Weather Hub | Connectivity only |
| 85 | Weather Station | Temperature, Humidity, Pressure |
| 86 | Indoor Sensor | Temperature, Humidity |

Pressure values are correctly parsed from payloads such as:
