# MSB NASA EARTH VIEW — The Earth Information Jukebox

> **Hear the Earth in Real Time.** A browser-based interactive web application and multi-sensory sonification engine that translates NASA Earth Information Center (EIC) and Scientific Visualization Studio (SVS) visual telemetry into live soundscapes.

---

## 🚀 Overview

**MSB NASA EARTH VIEW** is an accessible, zero-dependency web application built for the **NASA Space Apps Challenge 2026** (Mysore, India event). Tackling the *Earth Information Jukebox* challenge, our platform bridges a critical accessibility gap for blind and low-vision communities by transforming complex climate science and satellite telemetry into immersive, multi-sensory audio compositions.

Instead of relying solely on visual interpretation, users can select from built-in NASA datasets or upload custom frames to experience real-time pixel-to-frequency sonification.

---

## ✨ Key Features

- **Real-Time Pixel Sonification:** Scans video and image frames column-by-column, translating spatial coordinates, RGB thermal warmth (cool blues vs. warm ambers/reds), and pixel luminance into musical scale frequencies and volume dynamics.
- **Interactive EIC Dataset Jukebox:** Features four procedurally rendered NASA science modes:
  - *Global Sea Surface Currents & Temp* (Hydroshpere / Lydian Harmonic scale)
  - *GEOS Global Aerosols & Dust Plumes* (Atmosphere / Dorian sweep)
  - *Earth at Night: Urban Luminance* (Anthroposphere / Pentatonic crystalline arpeggios)
  - *ISS Lightning & Convective Storms* (Severe Weather / Minor kinetic pulse with transient flash detection)
- **Custom Frame Loader:** Upload any local NASA EIC or SVS JPG/PNG frame to instantly sonify its actual pixel properties in real time.
- **Live Acoustic Telemetry HUD:** High-contrast dark-space telemetry interface displaying dominant frequency in Hz, calculated note names, thermal warmth ratios, and a live frequency spectrum bar graph.
- **Accessibility & Web Audio API:** Zero external dependencies, full ARIA live support, responsive layout, and responsive mobile-friendly touch targets.

---

## 🛠️ Technology Stack

- **Frontend & Rendering:** HTML5 Canvas, Vanilla ES6 JavaScript
- **Audio Synthesis:** Web Audio API (`OscillatorNode`, `BiquadFilterNode`, `StereoPannerNode`, `GainNode`, `AnalyserNode`)
- **Styling:** Custom CSS with CSS variables, frosted glass HUD panels, and responsive grid layouts.

---

## 🏃 Quick Start & Local Execution

1. Clone or download this repository:
   ```bash
   git clone https://github.com/elayadesign/msb-nasa-earth-view.git
   ```
2. Open `index.html` directly in any modern browser (Chrome, Safari, Edge, Firefox).
3. Click **"▶ Play sound"** to engage the real-time Web Audio API synthesizer.

---

## 📋 Data & Disclosures

- **NASA Data Sources:** Built-in procedural simulation visuals represent NASA EIC and SVS dataset structures (Ocean currents, GEOS aerosols, Night lights, ISS lightning). Real data frames can be loaded via the custom file uploader.
- **Super Intelligence Disclosure:** LLM tools were utilized to assist with documentation structure and code debugging. Core sonification architecture, mapping logic, and creative direction were designed and executed by **MSB Creative Studios**.

---

## 📜 License

Distributed under the MIT License. See `LICENSE` for more information.

---
*Built with passion by MSB Creative Studios for the 2026 NASA Space Apps Challenge.*
