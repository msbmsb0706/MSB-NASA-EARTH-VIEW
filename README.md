# MSB NASA EARTH VIEW — The Earth Information Jukebox

> **Hear Earth imagery as it is scanned.** A zero-dependency, single-file web application that turns
> NASA satellite imagery into synthesized soundscapes and renders an interactive holographic 3D globe with live satellites and stars.

**NASA Space Apps Challenge 2026 · Team MSB Creative Studios**

`v3.8.0` · single file · zero dependencies · 20 languages · WebGL + Web Audio

**▶ Live app:** <https://msbmsb0706.github.io/MSB-NASA-EARTH-VIEW/> — served straight from `main` with GitHub Pages.

---

## Overview

**MSB NASA EARTH VIEW** is a browser-based, multi-sensory sonification engine built for the
*Earth Information Jukebox* challenge. NASA's Earth Information Center (EIC) and Scientific Visualization
Studio (SVS) produce extraordinary visualisations of our planet; relying on sight alone shuts out blind and
low-vision audiences and limits how anyone can perceive subtle climate trends.

This application scans Earth imagery in real time and converts **colour, brightness, spatial position and
motion** into an evolving musical performance. There are no recorded tracks: every note, filter sweep and
drum pulse is synthesised live in the browser with the Web Audio API.

Version 3.8 adds a fourth public-data panel — **live NOAA space weather**, **Earth's rotation and magnetic field**, **sunlight on every planet plus each planet's pull on Earth**, and **ISS passes over your own location** (fetched TLE, propagated in the browser, clickable, with a sky chart and calendar export). Version 3.7 added a hand-written WebGL globe with **1800 twinkling stars**, a **live satellite fleet** (ISS live via wheretheiss.at, Himawari-9, GOES-18, NOAA-20, Terra, Aqua, GPM), great-circle data arcs and a scanning meridian — plus video input, session recording, auto tour, keyboard control, a full accessibility layer, **boosted audio**, a **Live Earth** panel that checks public NASA data in real time, a **warming chart you can click to hear**, a **20-language NASA pill** `🌐 LANG`, and a **Scientific Lab** shown as one merged page: [7.1 Air Quality](#scientific-lab--five-datasets-one-page), 7.2 Climate Lab, 7.3 Water & Ice, 7.4 Hazards and **7.5 Satellite comparison** — a bar chart ranking ten operational free/public missions by spatial detail, update speed or openness, all charts visible at once, with CSV export and sonification for school/public/research.

---

## Quick start

1. Open **`index.html`** in any modern browser (Chrome, Edge, Firefox, Safari).
   No build step or dependencies. A network connection is needed for NASA imagery and live disaster checks; demos and local files work offline.
2. Press **Start near-real-time view + sound** to load the latest available Himawari infrared image and start listening. For the Americas choose GOES-East. Or choose a NASA layer and press **Load selected imagery**, then **Start sonification** (or <kbd>Space</kbd>).
3. You can also choose a simulated demo or load a local image or video.
4. Scroll to **Live Earth — climate · disasters · satellites** and press **Check live disasters** to fetch open events from NASA EONET (public API).
5. Keep scrolling to the **Scientific Lab** — all five blocks are on one page. Air quality and USGS earthquakes load
   themselves; press **🔄 Check air** / **📍 Use my location** to move the AQI to your city, click any chart to hear it,
   and try the **🔍 Spatial detail / ⏱️ Update speed / 🌍 Openness** switch in **7.5 Satellite comparison**.
6. Scroll to **8. Space weather, planets & satellites over you**: NOAA SWPC solar wind, Kp and Dst load themselves;
   press **📍 Use my location** and **🔭 Find ISS passes** to see passes over you in the next three days, then click a
   pass to draw it in the sky chart, save it as a calendar file, or hear it.
7. Change the interface language any time with the **`🌐 LANG`** pill in the header (20 languages, Arabic and Urdu flip
   the page to right-to-left).

### NASA imagery and dates

The app requests imagery via NASA's [GIBS WMS](https://nasa-gibs.github.io/gibs-api-docs/access-basics/) and uses its WMTS DescribeDomains service to check the selected layer's available times. **Follow latest available** looks back 14 days and chooses the latest available frame; it checks every 5 minutes while that same layer is active and reloads when a newer frame appears. Choose a date to turn following off; for a historical 30-minute layer, the last available frame on that UTC day is selected. The status displays the GIBS-listed frame time and retrieval time. GIBS availability does not guarantee complete global coverage.

Himawari and GOES-East infrared imagery has a nominal 10-minute cadence and covers only each satellite's viewing area. NASA's delivery can be delayed and the latest frame can be unavailable or incomplete; the app displays its UTC timestamp and approximate age. These are not continuous video and don't cover the whole world. VIIRS NOAA-20 and MODIS true-color layers are daily mosaics. IMERG's 30-minute layer is a precipitation **estimate**, not ground radar, and arrives with processing delay; the daily layer is an average. None is a live video feed. If NASA's availability or image request fails, the previous source stays active: check your connection, try another date or layer, or use [NASA Worldview](https://worldview.earthdata.nasa.gov/) or a local file. The GIBS service can snap WMS requests to a nearest time, so the app checks the advertised availability before requesting an image rather than assuming a date exists.

The actual displayed image pixels drive live Web Audio synthesis; this is an artistic image-to-sound mapping, not a calibrated reading of temperature, wind, or other measurements. With a still mosaic, changes in sound mainly come from scanning different image columns, not live changes on Earth. The NASA request is made directly from your browser and requires network access and a browser that permits cross-origin pixel reads.

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

## What's new

### v3.8.0 — space weather, planet sunlight and passes over you
| Area | Change |
| --- | --- |
| **8.1 Live magnetosphere** | Solar wind speed, IMF **Bz** and **Bt**, **Kp**, **Dst** and the **NOAA G-scale** from NOAA SWPC public JSON, refreshed every five minutes. A Kp chart shows the last two days plus the NOAA forecast and is clickable to hear the storm curve. An aurora estimate converts the current Kp into the oval's magnetic latitude and compares it with yours. |
| **8.2 Earth's rotation** | Live sidereal clock, spin speed at your latitude, orbital speed, magnetic latitude, dipole field strength and dip angle — plus the honest answer: the geomagnetic field comes from the core and does **not** steer the spin. Local solar elevation, direct sunlight, sunrise/sunset and day length are computed for your place. |
| **8.3 Planets** | Sunlight on all eight planets right now in **W/m²** and as a percentage of Earth's, from Keplerian elements evaluated for the minute. A second table computes each planet's **gravitational and tidal pull on Earth** and compares it with the Moon's, making the real scale of "planetary influence" visible. Every row is clickable and sonified. |
| **8.4 Passes over you** | Live ISS TLE from **api.wheretheiss.at**, propagated locally with a J2 model. Press *Use my location* → *Find ISS passes* for every pass above 10° in the next three days with maximum elevation, direction and a **visible** flag. Click a pass to draw its **polar sky chart**, **⬇ export an .ics calendar file**, or **🔊 hear the pass**. Any public two-line TLE can be pasted to track another satellite. |
| Honesty | The panel states that space weather does not measurably change Earth's rotation, that planetary tides are dominated by the Sun and Moon, and that local predictions are approximations, not navigation data. |

### v3.7.1 — documentation and help refresh
| Area | Change |
| --- | --- |
| Help | In-app help now explains **Live Earth**, the five **Scientific Lab** blocks and the **language pill** (including which languages switch to right-to-left). |
| Language | Arabic and Urdu now set `dir="rtl"` on the page, and a saved RTL language is restored before first paint of the labels. |
| Disclosures | The in-app *Data & disclosures* panel lists every Scientific Lab source: Open-Meteo (CAMS), USGS, NASA GISS, the Mauna Loa Keeling record and the curated satellite catalogue. |
| Footer | Shows the live app version (`v3.7.1`), read from the same constant as the diagnostics hook. |
| Docs | README, lite-build docs, CHANGELOG and the GitHub repository description/topics brought in line with the app. |

### v3.7.0 — satellite comparison
| Area | Change |
| --- | --- |
| Scientific Lab | New **7.5 Satellite comparison** — bar chart of ten operational **free/public** missions (Sentinel-2 A/B, Sentinel-1 A/C, Landsat 8/9, MODIS Terra/Aqua, VIIRS NOAA-20/21, Himawari-9 AHI, GOES-18 ABI, GPM IMERG, SMAP, GRACE-FO) with three toggleable metrics — **🔍 Spatial detail**, **⏱️ Update speed**, **🌍 Openness**. Bars are log-scaled, values sit in a right-hand column, bars are clickable (each plays its mission and announces the value). |
| Scientific Lab | **“Running now — operational & free”** list: status dot, native resolution, refresh time, a **PUBLIC** tag and a data-portal link per mission, plus a headline count (`10 of 10 running · 96 % open`). |
| Scientific Lab | **🔊 Sonify comparison** (ranking as rising tones), **⬇ CSV export** of the catalogue, GIBS link, and chart re-draw on theme / high-contrast switch. |
| Language | `中文` is labelled **`中文 (Mandarin)`**. All 20 languages kept. |

### v3.6.0 — merged Scientific Lab
| Area | Change |
| --- | --- |
| Scientific Lab | The four tab buttons are **gone**. Air Quality, Climate Lab, Water & Ice and Hazards are **stacked in one merged page** with numbered headings 7.1–7.4, so every chart and value is visible together on one scroll. Air quality and USGS quakes still auto-load. |
| Language | `اردو (Urdu)` shows 🇮🇳 (Urdu is an Indian language too) — the language itself is unchanged. |

### v3.5.0 — Scientific Lab and extra languages
| Area | Change |
| --- | --- |
| Scientific Lab | First release: 🌫️ Air Quality (Open-Meteo PM2.5 / PM10 / O₃ / NO₂ / CO, AQI badge, *Use my location*, sonify), 🌡️ Climate Lab (1880 → 2024 comparison, Keeling CO₂ curve, CSV), 🌊 Water & Ice (sea-level curve, GRACE + IMERG tips), ⚠️ Hazards (USGS earthquakes, M4.5+ count, sonify by magnitude). |
| Language | বাংলা, मराठी, ગુજરાતી, اردو, ਪੰਜਾਬੀ and 한국어 added — 20 languages. |

### v3.0 — globe, satellites, Live Earth
| Area | Change |
| --- | --- |
| 3D | Enhanced starfield: **1800 stars** (was 1100) with twinkle, warm/blue variants, brighter giants. New **live satellite fleet** — ISS, Himawari-9 (140.7°E GEO), GOES-18 (75.2°W GEO), NOAA-20 polar, Terra, Aqua, GPM-Core — each with colored trailing dots orbiting in real time. |
| Live Earth | New **Live Earth — climate · disasters · satellites** panel: global warming (+1.2 °C), CO₂/sea-level vital signs, active disaster count from **NASA EONET public API** (auto-checks on load + every 10 min), satellite legend and links to NASA Climate, EONET, Worldview. |
| Audio | **Louder master gain** — 1.15× (was 0.9×) with gentler compressor (−16 dB) so quiet/dark images are audible. |
| UI | Removed location-specific footer; now shows live data status `Live: EONET n events · GIBS timestamp`. Theme + high-contrast still supported. |

See [`CHANGELOG.md`](CHANGELOG.md) for the full list back to v1.0.

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

---

## Key features

### Real-time sonification
- **Colour → pitch.** Warm reds, ambers and whites climb a scene-specific scale; cool blues and cyans sit low.
- **Brightness → volume and timbre.** Pixel luminance drives lead amplitude and opens the low-pass filter.
- **Position → stereo pan.** The scan position and the light distribution in the scanned column steer the stereo field.
- **Motion → rhythm.** Frame-to-frame change fires kicks and hats; sudden luminance spikes trigger pitched pulses and FM bells.
- **Four scales.** Lydian harmonic, Dorian atmospheric, pentatonic crystalline and minor kinetic — one per scene.
- **Live spectral analysis.** A 128-band analyser feeds the spectrum display.

### The 3D globe — satellites & stars (WebGL 1, no libraries)
- 512 × 256 **embedded Natural Earth land mask** rasterised at build time (1.6 kB of packed bits) and sampled
  into a 5 200-point Fibonacci sphere → 1 591 land dots.
- Sphere rendered with a custom holographic shader: ocean hex grid, continent texture from the live data field,
  day/night shading, fresnel limb and a glowing scanning meridian.
- **Atmosphere** from a screen-space glow shader; **1800-star** twinkling field with warm/blue giants.
- **Live satellite fleet** with colored trails: ISS (LEO 51.6°), Himawari-9 GEO 140.7°E, GOES-18 GEO 75.2°W, NOAA-20, Terra, Aqua, GPM-Core — orbital periods scaled for visible motion, geostationary satellites fixed over equator with subtle drift.
- **Great-circle arcs** between Chennai, New York, London, São Paulo, Nairobi, Tokyo and Sydney with travelling light pulses.
- Arcball-style drag to orbit, pinch or <kbd>Ctrl</kbd>/<kbd>⌘</kbd> + scroll to zoom, auto-orbit toggle.
- Graceful degradation: if WebGL is unavailable the flat scanner takes over and every audio feature still works.

### Live Earth science — public real-time checks
- **Global warming indicator:** +1.2 °C since 1880 (NASA GISS) with link to `climate.nasa.gov/vital-signs/global-temperature` — sonified as rising pitch.
- **CO₂ & sea level:** 421 ppm CO₂, +21 cm sea level — links to NASA vital signs; daily GIBS true-color confirms ice/ocean color.
- **Active disasters:** Fetches **NASA EONET** `https://eonet.gsfc.nasa.gov/api/v3/events?status=open` — counts open wildfires, storms, volcanoes, floods; lists 8 most recent events with date/coordinates/source links. Auto-checks on load and every 10 min while visible. Also updates footer with `Live: EONET n events`.
- **Satellite legend** explains each colored dot on the globe.
- All checks run **directly from your browser to public NASA APIs** — no backend, no key, no account.

### Scientific Lab — five datasets, one page
Everything lives in **one merged panel** (section 7) — no tabs, no clicking to reveal content. Each block keeps
its own numbered heading, buttons and sonification.

| Block | Data | What you can do |
| --- | --- | --- |
| **7.1 🌫️ Air Quality** | Open-Meteo Air Quality API (CAMS): PM2.5, PM10, O₃, NO₂, CO | Live AQI with colour badge, *Use my location*, **🔊 Sonify AQI** (clean air = pure tone, polluted = noisy/detuned), raw pollutant badges, API docs link |
| **7.2 🌡️ Climate Lab** | NASA GISS surface temperature, Mauna Loa Keeling CO₂ | Compare any year 1880 → 2024 (+1.47 °C baseline), CO₂ curve canvas (*click to hear 315 → 421 ppm*), **⬇ CSV**, **🔊 Sonify warming** |
| **7.3 🌊 Water & Ice** | NASA sea-level altimetry, GRACE, GPM IMERG | +21 cm since 1993 with a clickable rise curve, **🔊 Sonify sea rise**, GRACE link and a Chennai-monsoon IMERG tip |
| **7.4 ⚠️ Hazards Live** | USGS earthquakes, last 24 h | Live quake count + M4.5+ count, eight most recent events with magnitude, depth, lat/lon and USGS links, **🔊 Sonify by magnitude** (magnitude → loudness, depth → pitch) |
| **7.5 🛰️ Satellite comparison** | Curated catalogue of operational free-data missions | Bar-chart ranking of ten public missions by **spatial detail**, **update speed** or **openness**; click a bar to hear that mission; *Running now — operational & free* list; **🔊 Sonify comparison**; **⬇ CSV** |

**7.5 in detail.** Ten missions are compared — Sentinel-2 A/B (10 m), Sentinel-1 A/C radar (10 m), Landsat 8/9
(30 m), MODIS Terra/Aqua (250 m), VIIRS NOAA-20/21 (375 m), Himawari-9 AHI (500 m), GOES-18 ABI (500 m),
GPM IMERG (2 km), SMAP (9 km) and GRACE-FO (300 km). Scores are log-scaled, so 10 m → 300 km is readable on one
chart; the best mission for the chosen metric is always the longest bar, and values are printed in a right-hand
column. The chart re-draws when you switch theme or high-contrast mode.

> The 7.5 catalogue is **not live telemetry**. It lists agency-confirmed operational missions whose data is free
> and public, with their published resolutions and refresh times; the panel says so on screen.

### Space weather, planets and satellites over you
A fourth public-data panel (section 8), stacked under the Scientific Lab:

| Block | Data | What you can do |
| --- | --- | --- |
| **8.1 🧲 Live magnetosphere** | NOAA SWPC: solar-wind speed, IMF Bz/Bt, planetary Kp, Kyoto Dst, NOAA R/S/G scales | Current conditions with colour-coded warnings, NOAA's 3-day storm watch, a clickable Kp history + forecast chart, **🔊 Hear conditions**, and an aurora-latitude estimate for your location |
| **8.2 🌍 Earth's rotation** | Computed in-browser: sidereal time, solar position, dipole magnetic model | Live spin direction, rotation period, speed at your latitude, orbital speed, magnetic latitude / field / dip angle, solar elevation, direct sunlight in W/m², sunrise, sunset and day length — with a clear explanation of why the magnetic field does **not** drive the spin |
| **8.3 🌞 Planets** | JPL Keplerian elements (Standish) + Newtonian gravity, evaluated now | Sunlight on every planet (W/m² and % of Earth), and every planet's gravitational and tidal pull on Earth relative to the Moon; click any row to hear it |
| **8.4 🛰️ Passes over you** | ISS TLE from api.wheretheiss.at (public, no key); orbit propagated with a J2 model | Passes above 10° for the next 3 days at your location, with elevation, compass direction and visibility; selectable polar **sky chart**, **.ics calendar export**, **pass sonification**, and a paste-a-TLE field for any other public satellite |

The panel is explicitly honest about limits: space weather disturbs radio, GPS, satellites and power grids but does
not measurably change Earth's rotation or axis; planetary tides are dominated by the Sun and Moon; pass times are
approximations and should be confirmed with NASA Spot the Station.

### Languages — 20, with right-to-left support
- The header’s **`🌐 LANG`** pill switches the main interface labels between **20 languages**:
  English, தமிழ் (Tamil), हिन्दी (Hindi), ಕನ್ನಡ (Kannada), తెలుగు (Telugu), മലയാളം (Malayalam), বাংলা (Bengali),
  मराठी (Marathi), ગુજરાતી (Gujarati), اردو (Urdu), ਪੰਜਾਬੀ (Punjabi), 한국어 (Korean), Español, Français, Deutsch,
  中文 (Mandarin), 日本語 (Japanese), العربية (Arabic), Português and Русский.
- **Arabic and Urdu switch the page to `dir="rtl"`**, and a saved RTL language is applied before the labels render.
- Your choice is stored in `localStorage` (`msb-lang`) and restored on the next visit.
- Scientific values, units and dataset labels deliberately stay in English so numbers are never misread.

### Scenes and input
- **Global Sea Surface Currents & Temp** — Lydian harmonic, flowing current ribbons and warm Gulf Stream eddies.
- **GEOS Global Aerosols & Dust Plumes** — Dorian sweep, drifting dust plumes and streamers.
- **Earth at Night: Urban Luminance** — pentatonic bells, 780 city-light clusters sampled from the land mask.
- **ISS Lightning & Convective Storms** — minor kinetic pulse with random flash/branching-bolt events.
- **NASA GIBS.** Explore 10-minute Himawari/GOES-East infrared, daily VIIRS/MODIS true-color mosaics and daily or 30-minute IMERG precipitation imagery by UTC date. Check availability, follow recent frames and refresh.
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
- Single document: demo scenes and local files work offline; NASA GIBS/EONET require network access.

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
| Master gain | Gain slider (louder now) | <kbd>↑</kbd> <kbd>↓</kbd> |
| Sound design voice | **Voice** menu | <kbd>D</kbd> |
| Musical scale | **Scale** menu | <kbd>S</kbd> |
| Auto tour | **Auto tour** | <kbd>T</kbd> |
| Auto-orbit | **Auto-orbit** switch | <kbd>O</kbd> |
| Check live disasters | **🔄 Check live disasters** | — |
| Language (20) | **🌐 LANG** pill | — |
| Check air quality / locate | **🔄 Check air**, **📍 Use my location** in 7.1 | — |
| Hear a chart | Click the CO₂, sea-level, warming or satellite bar chart | — |
| Satellite comparison metric | **🔍 Spatial detail** / **⏱️ Update speed** / **🌍 Openness** in 7.5 | — |
| Export data | **⬇ Download CSV** in 7.2 and 7.5 | — |
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
                │
                └── Live Earth disasters → motion density → denser rhythm
```

Every scene uses a different oscillator mix, filter setting, reverb depth and scale, so each dataset has its
own acoustic signature:

| Scene | Scale | Lead | Texture |
| --- | --- | --- | --- |
| Sea surface | Lydian harmonic (C4–C6) | sine | deep pad, long reverb |
| Aerosols | Dorian atmospheric (D3–A5) | triangle | saw pad, feedback delay |
| Night lights | Pentatonic crystalline (C4–G6) | sine | FM bells, wide reverb |
| Lightning | Minor kinetic pulse (A2–E5) | triangle | noise percussion, short reverb |

Public disaster data (EONET) supplements the audio: when many wildfires/storms are open, the “motion” character is denser — you hear it as busier percussion even on a still image.

---

## Architecture

Everything lives in **one HTML file** (≈340 kB, ≈6 900 lines) with three clearly separated layers:

```
index.html
├── <style>   design system, layout, high-contrast theme, reduced-motion rules, Live Earth cards
├── markup    header (incl. 🌐 LANG pill) · stage · transport · jukebox rail · telemetry ·
│             Live Earth panel · merged Scientific Lab 7.1–7.5 ·
│             space weather / planets / passes 8.1–8.4 · info-grid · help dialog
└── <script>  IIFE, ~4 300 lines (app) + a 10-line theme bootstrap in <head>
    ├── utilities + embedded land mask (base64, 512 × 256 packed bitmap)
    ├── scenes      procedural painters for the four datasets + custom media
    ├── analysis    64 × 32 downsample → warmth / luminance / motion / pan features
    ├── audio       Web Audio graph: pad + sub + lead + percussion → filters,
    │               pan, delay, convolution reverb, compressor (−16 dB), analyser, recorder tap;
    │               4 voices, 6 scale sets, lite-build percussion (noise crack + body); louder master 1.15×
    ├── renderers   · flat 2D canvas scanner
    │               · WebGL1 globe: 3 programs (earth / particles / atmosphere),
    │                 3 shaders compiled at runtime, 22 buffers + satellite/trail buffers
    │               · starfield (1800), satellite fleet, arcs, graticule, meridian
    ├── live-earth  EONET fetch (public, no key) → disaster counts + list; GIBS 5-min poll; ISS position
    ├── sci-lab     Open-Meteo air quality · GISS/Keeling climate + sea-level canvases ·
    │               USGS quakes · satellite comparison chart (log-scaled bars, 3 metrics,
    │               click-to-sonify, CSV) · all charts redraw on theme change
    ├── sky-lab     NOAA SWPC space weather · Kp chart · Earth rotation + dipole field ·
    │               planet sunlight & tidal pull · TLE parsing, J2 propagation, pass finding,
    │               polar sky chart, .ics export · all computed locally
    ├── i18n        20-language dictionary, localStorage persistence, RTL switch for ar/ur
    └── interaction UI bindings, keyboard map, pointer orbit, tour, recording, loop
```

**Why no framework?** The demo and local media can run offline from a single file. Vanilla ES2020 + WebGL1 keeps the payload tiny and removes every supply-chain and CDN dependency.

**Data flow.** The same 512 × 256 field canvas feeds the audio analysis, the flat scanner and the WebGL
texture, guaranteeing that what you see is exactly what you hear. Live checks add context without changing the pixel-to-sound math.

---

## Files in this repository

| File | Purpose |
| --- | --- |
| `index.html` | The full application — 3D globe, satellite fleet, live disaster checks, sonification engine, accessibility layer. |
| `MSB NASA EARTH VIEW – Earth Jukebox.html` | Lite single-file build: minimal, dependency-free flat-scan variant. Its synth voice, percussion, pentatonic mapping and narration are merged into `index.html` and selectable as **Jukebox lite (original)**. |
| `MSB NASA EARTH VIEW – Earth Jukebox.md` | Documentation for the lite build, with a pointer to the full app’s Live Earth and Scientific Lab features. |
| `README.md` | This document. |
| `CHANGELOG.md` | Version history. |
| `LICENSE` | MIT licence. |

---

## Data and disclosures

- The four built-in scenes are **procedurally generated demo visuals inspired by** NASA EIC/SVS datasets
  (sea-surface currents and temperature, GEOS aerosols, night lights, ISS lightning). They are **not raw NASA
  data**. For NASA pixels, use the GIBS option or download frames or animations from the
  [NASA Earth Information Center](https://earth.gov/) or the
  [NASA Scientific Visualization Studio](https://svs.gsfc.nasa.gov/) and load them above.
- We acknowledge the use of imagery provided by NASA's Global Imagery Browse Services (GIBS), part of NASA's Earth Science Data and Information System (ESDIS). Himawari imagery is from JMA; GOES imagery is from NOAA. No NASA imagery is bundled with this repository; only a public-domain
  Natural Earth land mask (1:50 m, `world-atlas`) is embedded, as packed coastline bits.
- **Live disasters** are from **NASA EONET** (`eonet.gsfc.nasa.gov`), a public API with no key required. The app fetches directly from your browser; no proxy or tracking.
- **Climate indicators** link to `climate.nasa.gov/vital-signs` — global temperature, CO₂, sea level, ice. Values shown are educational summaries; follow the links for the latest peer-reviewed datasets.
- **Scientific Lab sources.** Air quality and pollutants: **Open-Meteo Air Quality API** (CAMS), fetched directly from the browser. Earthquakes: **USGS** `all_day.geojson` summary feed. Climate curves: **NASA GISS** surface-temperature series and the **Mauna Loa Keeling** CO₂ record. Sea level/ice: NASA vital signs and GRACE. Satellite comparison (7.5): a **curated catalogue** of operational mission specifications compiled from NASA, ESA Copernicus, NOAA and JMA published product pages — a catalogue, not live telemetry, and not a measurement of what any satellite is doing right now. Every one of these APIs is public and keyless; nothing is proxied and nothing is stored.
- **Space weather, sky and passes (section 8).** Solar-wind speed, IMF Bz/Bt, Kp, Dst and the NOAA storm scale are fetched from **NOAA SWPC** public JSON endpoints (`services.swpc.noaa.gov`), which are CORS-open and keyless. The ISS two-line element set comes from **api.wheretheiss.at**. Planet positions, sunlight, gravitational and tidal pull, sidereal time, solar elevation, sunrise/sunset and satellite passes are **computed in the browser** from published Keplerian elements and a J2 orbit model — useful approximations, not official ephemerides, and not for navigation. The magnetic-field values use a simple tilted-dipole model, not the World Magnetic Model. Space weather does not measurably change Earth's rotation or axis; the geomagnetic field is a product of the core dynamo, not a driver of the spin.
- **A note on scale.** Air-quality AQI in 7.1 is derived from Open-Meteo PM2.5 with a simple linear approximation for demonstration; treat it as an indicator, not a regulatory AQI. CSV exports contain exactly the numbers shown on screen.
- **Privacy.** There is no analytics or telemetry. Loading NASA imagery sends a request to NASA GIBS; checking disasters sends a request to NASA EONET. Uploaded images and videos are decoded locally and never uploaded; they are released when cleared or replaced.
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
| Chrome / Edge 100+ | Full support (WebGL + Web Audio + MediaRecorder + EONET fetch) |
| Firefox 100+ | Full support (`audio/webm` recording) |
| Safari 15.4+ | Full support, some codecs (e.g. WebM playback) are OS-dependent |
| Older / headless | Flat-scan fallback, all audio features intact |

Rendering is capped at 2× device-pixel-ratio, the globe texture refreshes every other frame and the analysis
pass runs on a 64 × 32 buffer, so the application stays smooth on integrated graphics and phones. Star count increased to 1800 adds negligible cost (points).

---

## Roadmap

Done: merged Scientific Lab (3.6), satellite comparison graph (3.7), space weather + planet sunlight + local ISS
passes (3.8), 20-language pill with RTL support, Live Earth public checks, live ISS position.

Next:
- Add more NASA GIBS layers and time-series playback when source data are available.
- Extend the satellite comparison with a live “data availability now” column driven by GIBS DescribeDomains.
- Multi-stem export (pads, lead, percussion) and MIDI out for classroom composition.
- Sonification of additional NASA datasets: ICESat-2 ice loss, SMAP soil moisture, GRACE groundwater.
- Configurable mapping curves and a “describe what you hear” tutorial for first-time users.
- WebMIDI controller support and spatial (HRTF) audio.
- Translate the Scientific Lab strings, keeping numbers and units in English.

## Team and credits

**MSB Creative Studios** — NASA Space Apps Challenge 2026 · *The Earth Information Jukebox*.

Sonification approach inspired by NASA's own data-sonification work.

Built with HTML5 Canvas, WebGL 1, the Web Audio API and vanilla ES2020 — no frameworks, no build tools,
no external requests except direct public NASA APIs (GIBS, EONET).

---

## Licence

Distributed under the **MIT License** — see [`LICENSE`](LICENSE).

*Built with passion by MSB Creative Studios for the 2026 NASA Space Apps Challenge.*
