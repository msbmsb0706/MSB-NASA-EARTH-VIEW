# MSB NASA EARTH VIEW — The Earth Information Jukebox

> **Hear the Earth in real time.** A zero-dependency, single-file web application that turns NASA Earth
> science imagery into live soundscapes — and renders the planet as an interactive holographic 3D globe.

**NASA Space Apps Challenge 2026 · Mysore, India · Team MSB Creative Studios**

---

## Overview

**MSB NASA EARTH VIEW** is a browser-based, multi-sensory sonification engine built for the
*Earth Information Jukebox* challenge. NASA's Earth Information Center (EIC) and Scientific Visualization
Studio (SVS) produce extraordinary visualisations of our planet; relying on sight alone shuts out blind and
low-vision audiences and limits how anyone can perceive subtle climate trends.

This application scans Earth imagery in real time and converts **colour, brightness, spatial position and
motion** into an evolving musical performance. There are no recorded tracks: every note, filter sweep and
drum pulse is synthesised live in the browser with the Web Audio API.

Version 2.0 adds a hand-written WebGL globe — a dotted, holographic Earth with atmospheric glow, great-circle
data arcs and a scanning meridian — plus video input, session recording, auto tour, keyboard control and a
full accessibility layer.

---

## Quick start

1. Open **`index.html`** in any modern browser (Chrome, Edge, Firefox, Safari).
   No build step, no server, no dependencies, no network requests.
2. Pick one of the four Earth scenes, or load your own NASA frame (image **or** video).
3. Press **Start sonification** (or hit <kbd>Space</kbd>) and listen to the scan.

Optional local server (some Safari versions treat `file://` media more strictly):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

### Publish with GitHub Pages

1. Push this repository to GitHub.
2. **Settings → Pages → Source: Deploy from a branch → `main` / `root`**.
3. The application is served at `https://<user>.github.io/<repo>/` — no configuration needed.

---

## What's new in 2.0

| Area | Change |
| --- | --- |
| 3D | New hand-written WebGL renderer: dotted continents, textured data field, atmosphere, starfield, graticule, great-circle arcs, scanning meridian, orbit/zoom. |
| Merge | The standalone *Earth Jukebox* build (pentatonic motion→rhythm engine, stereo panning, image/video loading, ARIA narration) is fully merged into `index.html`. |
| Input | Image **and** video uploads (MP4/WebM/GIF/PNG/JPG/WebP), drag-and-drop anywhere on the page. |
| Audio | Reverb, feedback delay, stereo panning, transient percussion, FM bells, compressor; per-scene sound design. |
| UX | Auto tour, session recording, fullscreen, high-contrast mode, keyboard shortcuts, help dialog, URL-free deep state. |
| A11y | ARIA live announcements, labelled controls, reduced-motion support, keyboard access to every action. |
| Design | Daylight theme merged from the lite build, system-preference aware, remembered across visits. |
| Docs | This README, a changelog and an MIT licence. |

### Sound design (merged from the lite build)

The original *Earth Jukebox* lite engine has its own voice, and it is now selectable in the app:

| Voice | What it does |
| --- | --- |
| **Holographic** (default) | Scene-defined oscillators, hybrid kick + hat percussion, full reverb. |
| **Jukebox lite (original)** | Faithful port of the lite engine: detuned saw pad, triangle lead, 0.34 s delay with 0.38 feedback, and its 1800 Hz noise-crack drum with a 140 → 48 Hz body. |
| **Cinematic drone** | Slow glides, deep reverb and sparse soft percussion for long listening. |
| **Kinetic storm** | Square lead, short reverb and dense punch percussion, tuned for lightning data. |

Both engines share the same analysis and mapping, so switching voices never changes what the data means.
Alongside the voices there is a **scale menu** (scene default, the lite build's minor pentatonic, Lydian,
Dorian, natural minor, whole tone), plus independent **Percussion** and **Bells** mutes.
The pad now follows the harmonic degree under the melody, exactly as the lite build did.

See [`CHANGELOG.md`](CHANGELOG.md) for the full list.

---

## Key features

### Real-time sonification
- **Colour → pitch.** Warm reds, ambers and whites climb a scene-specific scale; cool blues and cyans sit low.
- **Brightness → volume and timbre.** Pixel luminance drives lead amplitude and opens the low-pass filter.
- **Position → stereo pan.** The scan position and the light distribution in the scanned column steer the stereo field.
- **Motion → rhythm.** Frame-to-frame change fires kicks and hats; sudden luminance spikes trigger pitched pulses and FM bells.
- **Four scales.** Lydian harmonic, Dorian atmospheric, pentatonic crystalline and minor kinetic — one per scene.
- **Live spectral analysis.** A 128-band analyser feeds the spectrum display.

### The 3D globe (WebGL 1, no libraries)
- 512 × 256 **embedded Natural Earth land mask** rasterised at build time (1.6 kB of packed bits) and sampled
  into a 5 200-point Fibonacci sphere → 1 591 land dots.
- Sphere rendered with a custom holographic shader: ocean hex grid, continent texture from the live data field,
  day/night shading, fresnel limb and a glowing scanning meridian.
- **Atmosphere** from a screen-space glow shader; **1 100-star** parallax field.
- **Great-circle arcs** between Chennai, Mysore, New York, London, São Paulo, Nairobi, Tokyo and Sydney with
  travelling light pulses.
- Arcball-style drag to orbit, pinch or <kbd>Ctrl</kbd>/<kbd>⌘</kbd> + scroll to zoom, auto-orbit toggle.
- Graceful degradation: if WebGL is unavailable the flat scanner takes over and every audio feature still works.

### Scenes and input
- **Global Sea Surface Currents & Temp** — Lydian harmonic, flowing current ribbons and warm Gulf Stream eddies.
- **GEOS Global Aerosols & Dust Plumes** — Dorian sweep, drifting dust plumes and streamers.
- **Earth at Night: Urban Luminance** — pentatonic bells, 780 city-light clusters sampled from the land mask.
- **ISS Lightning & Convective Storms** — minor kinetic pulse with random flash/branching-bolt events.
- **Custom imagery.** Load a NASA EIC/SVS JPG, PNG, WebP, GIF, MP4 or WebM. Images are swept west→east by the
  scan meridian (14 seconds per sweep at 1× speed); videos loop and drive the mapping every frame.
  Files never leave the device.

### Design and themes (merged from the lite build)
- **Daylight theme** using the lite build's palette (`#f4f7fb` paper, `#0b1730` ink, `#1d5fd1` accent),
  with every panel, card, control, dialog and meter restyled — the globe stage deliberately keeps its
  deep-space look in both themes, because it is a viewport rather than paper.
- **Follows your system preference** until you choose, then remembers your choice in `localStorage`.
- Theme resolved **before first paint** so there is no flash on load.
- High-contrast mode composes with both themes.
- Mobile polish from the lite build: 44 px touch targets and safe-area insets on the header.

### Performance and comfort
- Auto tour (12 s per scene), audio session recording to `.webm`, fullscreen, high-contrast theme.
- Reduced-motion support (`prefers-reduced-motion`) and adaptive device-pixel-ratio capping.
- Single request-free document: works offline, on `file://`, and inside locked-down school networks.

---

## Controls

| Action | Pointer / touch | Keyboard |
| --- | --- | --- |
| Start / pause sonification | **Start sonification** button | <kbd>Space</kbd> |
| Select scene | Scene cards | <kbd>1</kbd> <kbd>2</kbd> <kbd>3</kbd> <kbd>4</kbd> |
| 3D globe ↔ flat scan | **3D globe / Flat scan** switch | <kbd>V</kbd> |
| Orbit the globe | Drag | — |
| Zoom | Pinch, or <kbd>Ctrl</kbd>/<kbd>⌘</kbd> + scroll | — |
| Reset the scan | **↺ Reset** | <kbd>R</kbd> |
| Nudge the scan | — | <kbd>←</kbd> <kbd>→</kbd> |
| Master gain | Gain slider | <kbd>↑</kbd> <kbd>↓</kbd> |
| Sound design voice | **Voice** menu | <kbd>D</kbd> |
| Musical scale | **Scale** menu | <kbd>S</kbd> |
| Auto tour | **Auto tour** | <kbd>T</kbd> |
| Auto-orbit | **Auto-orbit** switch | <kbd>O</kbd> |
| Fullscreen | **⛶** | <kbd>F</kbd> |
| Daylight / dark theme | **☀ / ☾** | <kbd>L</kbd> |
| Help | **?** | <kbd>H</kbd> |
| Close dialogs | — | <kbd>Esc</kbd> |

---

## How the sonification mapping works

```
NASA frame / procedural scene
        │
        ▼
 512 × 256 data field  ──────────────► WebGL texture on the globe
        │                              (and the flat 2D scanner)
        ▼
 64 × 32 analysis pass, ~60 × per second
        │
        ├── average colour      → warmth 0…1 ──► scale degree ──► pitch
        ├── pixel luminance     → 0…1       ──► lead gain + low-pass cutoff
        ├── light distribution  → centroid  ──► stereo pan
        └── frame delta         → motion    ──► kick / hat / pulse / bell
```

Every scene uses a different oscillator mix, filter setting, reverb depth and scale, so each dataset has its
own acoustic signature:

| Scene | Scale | Lead | Texture |
| --- | --- | --- | --- |
| Sea surface | Lydian harmonic (C4–C6) | sine | deep pad, long reverb |
| Aerosols | Dorian atmospheric (D3–A5) | triangle | saw pad, feedback delay |
| Night lights | Pentatonic crystalline (C4–G6) | sine | FM bells, wide reverb |
| Lightning | Minor kinetic pulse (A2–E5) | triangle | noise percussion, short reverb |

---

## Architecture

Everything lives in **one HTML file** (≈148 kB) with three clearly separated layers:

```
index.html
├── <style>   design system, layout, high-contrast theme, reduced-motion rules
├── markup    header · stage · transport · jukebox rail · telemetry · help dialog
└── <script>  IIFE, ~2 600 lines
    ├── utilities + embedded land mask (base64, 512 × 256 packed bitmap)
    ├── scenes      procedural painters for the four datasets + custom media
    ├── analysis    64 × 32 downsample → warmth / luminance / motion / pan features
    ├── audio       Web Audio graph: pad + sub + lead + percussion → filters,
    │               pan, delay, convolution reverb, compressor, analyser, recorder tap;
    │               4 voices, 6 scale sets, lite-build percussion (noise crack + body)
    ├── renderers   · flat 2D canvas scanner
    │               · WebGL1 globe: 3 programs (earth / particles / atmosphere),
    │                 3 shaders compiled at runtime, 22 buffers
    └── interaction UI bindings, keyboard map, pointer orbit, tour, recording, loop
```

**Why no framework?** The submission must run offline, inside sandboxed judging environments, from a single
file. Vanilla ES2020 + WebGL1 keeps the payload tiny and removes every supply-chain and CDN dependency.

**Data flow.** The same 512 × 256 field canvas feeds the audio analysis, the flat scanner and the WebGL
texture, guaranteeing that what you see is exactly what you hear.

---

## Files in this repository

| File | Purpose |
| --- | --- |
| `index.html` | The full application — 3D globe, sonification engine, accessibility layer. |
| `MSB NASA EARTH VIEW – Earth Jukebox.html` | Lite single-file build: minimal, dependency-free flat-scan variant. Its synth voice, percussion, pentatonic mapping and narration are merged into `index.html` and selectable as **Jukebox lite (original)**. |
| `MSB NASA EARTH VIEW – Earth Jukebox.md` | Documentation for the lite build. |
| `MSB_NASA_EARTH_VIEW_Master_Guide.pdf` | Submission package: pitch script, deck outline, checklist. |
| `README.md` | This document. |
| `CHANGELOG.md` | Version history. |
| `LICENSE` | MIT licence. |

---

## Data and disclosures

- The four built-in scenes are **procedurally generated demo visuals inspired by** NASA EIC/SVS datasets
  (sea-surface currents and temperature, GEOS aerosols, night lights, ISS lightning). They are **not raw NASA
  data**. To hear real data, download frames or animations from the
  [NASA Earth Information Center](https://earth.gov/) or the
  [NASA Scientific Visualization Studio](https://svs.gsfc.nasa.gov/) and load them above.
- NASA media are credited to NASA. No NASA imagery is bundled with this repository; only a public-domain
  Natural Earth land mask (1:50 m, `world-atlas`) is embedded, as packed coastline bits.
- **Privacy.** There is no analytics, no telemetry and no network traffic. Uploaded images and videos are
  decoded locally and never uploaded; they are released as soon as you clear or replace them.
- **Super Intelligence disclosure.** Super Intelligence (LLM) tools assisted with code and documentation.
  Sonification mapping logic, creative direction and technical integration were designed and executed by
  MSB Creative Studios.

---

## Accessibility

- Every control is a real `<button>`, `<input>` or `<label>` with an accessible name, reachable by keyboard,
  with visible focus rings and a skip link.
- ARIA live regions announce scene changes, play state, loaded media, tour/recording state and a periodic
  qualitative description of the sound (warm/cool, bright/soft, busy/calm, current note).
- Audio starts only after an explicit user gesture, as required by browser autoplay policies.
- A daylight theme that follows `prefers-color-scheme` until you pick one, plus an independent
  high-contrast mode; both compose with `prefers-reduced-motion`, 44 px touch targets, safe-area insets
  and a screen-reader description of the visualisation.
- The sound itself is the accessible output: every visual variable has an audible counterpart.

---

## Browser support and performance

| Browser | Status |
| --- | --- |
| Chrome / Edge 100+ | Full support (WebGL + Web Audio + MediaRecorder) |
| Firefox 100+ | Full support (`audio/webm` recording) |
| Safari 15.4+ | Full support, some codecs (e.g. WebM playback) are OS-dependent |
| Older / headless | Flat-scan fallback, all audio features intact |

Rendering is capped at 2× device-pixel-ratio, the globe texture refreshes every other frame and the analysis
pass runs on a 64 × 32 buffer, so the application stays smooth on integrated graphics and phones.

---

## Roadmap

- Live API streaming from NASA GIBS / Worldview instead of uploads.
- Multi-stem export (pads, lead, percussion) and MIDI out for classroom composition.
- Sonification of additional NASA datasets: GRACE groundwater, ICESat-2 ice loss, precipitation.
- Configurable mapping curves and a "describe what you hear" tutorial for first-time users.
- WebMIDI controller support and spatial (HRTF) audio.

---

## Team and credits

**MSB Creative Studios** — Mysore, India · NASA Space Apps Challenge 2026 · *The Earth Information Jukebox*.
Sonification approach inspired by NASA's own data-sonification work.

Built with HTML5 Canvas, WebGL 1, the Web Audio API and vanilla ES2020 — no frameworks, no build tools,
no external requests.

---

## Licence

Distributed under the **MIT License** — see [`LICENSE`](LICENSE).

*Built with passion by MSB Creative Studios for the 2026 NASA Space Apps Challenge.*
