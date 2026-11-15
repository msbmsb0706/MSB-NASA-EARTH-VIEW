# Changelog

All notable changes to MSB NASA EARTH VIEW.

## [3.0.0] — 2026-11-15

### Added
- **Live satellite fleet** orbiting the 3D globe in real time: ISS (LEO 51.6°), Himawari-9 GEO 140.7°E, GOES-18 GEO 75.2°W, NOAA-20 polar, Terra, Aqua, GPM-Core — each with colored trails and pulse; geostationary satellites fixed over equator with drift.
- **Enhanced starfield:** 1800 twinkling stars (was 1100) with warm/blue giants and brighter parallax.
- **Live Earth — climate · disasters · satellites** panel: global warming +1.2 °C, CO₂/sea-level vital signs, active disaster count from **NASA EONET public API** (`eonet.gsfc.nasa.gov/api/v3/events`) with auto-check on load and every 10 min, plus 8-item event list with dates/coordinates/source links; footer shows `Live: EONET n events · GIBS timestamp`.

### Changed
- **Louder audio:** master gain 1.15× (was 0.9×), compressor −16 dB / 3.5 ratio for dark-image audibility.
- Footer and disclosures are now location-agnostic (removed Mysore-specific line); README and lite docs updated with public real-time check instructions.

## [2.5.0] — 2026-11-15

### Added
- A one-click near-real-time view and sonification, with Himawari Asia-Pacific and GOES-East Americas infrared layers at a nominal 10-minute cadence.
- Available frame timestamp, approximate age and five-minute checks for newer imagery. Satellite coverage and publication delays are disclosed.

## [2.4.0] — 2026-11-15

### Added
- NASA VIIRS NOAA-20 imagery and daily / 30-minute GPM IMERG precipitation visualizations with explanations, limitations, and links to NASA science sources.
- GIBS availability lookup chooses an advertised frame time and reports missing frames or connection errors instead of assuming a recent date is available.
- Clear pixel-analysis labels distinguish image color from physical temperature and precipitation measurements.

## [2.3.0] — 2026-11-15

### Added
- NASA GIBS daily MODIS Terra and Aqua true-color imagery with a UTC date selector, recent-date following, periodic refresh, and accessible loading/error status.
- The satellite image feeds the existing scanner, globe and real-time audio synthesis. Failed requests retain the previous source.
- Clear disclosures distinguish requested dates and daily satellite mosaics from live video and simulated demos.

## [2.2.0] — 2026-11-15

### Added
- **Daylight theme**, merged from the lite build's design (paper `#f4f7fb`, ink `#0b1730`, accent
  `#1d5fd1`). Every surface is covered: header, panels, dataset cards, metrics, sound-design selects,
  upload zone, transport, mapping bars, footer, dialogs and keycaps. The visualisation stage keeps its
  deep-space look in both themes on purpose.
- **Theme control** in the header (☀ / ☾) with the <kbd>L</kbd> shortcut. The app follows
  `prefers-color-scheme` until you choose, then remembers the choice in `localStorage`.
- Theme is resolved by a tiny inline bootstrap **before first paint**, so there is no flash of the
  wrong theme, and the `theme-color` meta tag follows the active theme.
- High-contrast mode now composes with the daylight theme (dark-on-white variant).
- Mobile polish carried over from the lite build: 44 px touch targets and `env(safe-area-inset-top)`
  on the sticky header.
- Light-theme variants for range sliders, selects, switches and keycaps.

### Changed
- `Audio.init` configures delay/reverb from the active sound-design record (see 2.1.0).

## [2.1.0] — 2026-11-15

### Added
- **Sound design panel** with four selectable synth voices:
  - *Holographic* (default) — the 2.0 engine.
  - *Jukebox lite (original)* — faithful port of the lite build's voice: detuned sawtooth pad,
    triangle lead, 0.34 s delay with 0.38 feedback and 0.3 wet, 1800 Hz noise-crack drum with a
    140 → 48 Hz sine body, reduced reverb, no bells.
  - *Cinematic drone* — slower glides, longer delay, deeper reverb, soft kick only.
  - *Kinetic storm* — square lead, short delay/reverb, dense punch percussion.
- **Scale sets**: scene default, minor pentatonic (the lite build's `[0,3,5,7,10]`), Lydian, Dorian,
  natural minor and whole tone, transposed over the active scene root.
- **Percussion** and **Bells** mute switches.
- Harmonic pad follower: the drone and sub now glide to the scale degree under the melody
  (lite-build behaviour) instead of sitting on a fixed root.
- Keyboard: <kbd>D</kbd> cycles voice, <kbd>S</kbd> cycles scale; both documented in the help dialog.

### Changed
- Still-image and scene sweeps now take 14 seconds at 1× scan speed (as documented in the lite build).
- Lead gain, pad level, delay feedback, delay wet and reverb mix are driven by the selected voice.
- Percussion gating uses the lite build's interval curve: `max(0.14, 0.9 − motion × 1.3)` seconds.

### Fixed
- `Audio.init` no longer hits a temporal-dead-zone error when the delay/reverb stages are configured
  from the sound-design record.

## [2.0.0] — 2026-11-15

Full rebuild of the application on top of the original jukebox prototype. The standalone
*Earth Jukebox* page and the jukebox dashboard have been merged into a single `index.html`.

### Added
- **Holographic 3D Earth** rendered with hand-written WebGL 1 (no libraries, no CDN):
  - 5 200-point Fibonacci sphere sampled against an embedded 512 × 256 Natural Earth land mask
    (1 591 visible land dots), 96 × 64 textured globe mesh.
  - Three runtime-compiled shader programs: globe (ocean hex grid, continent data texture,
    day/night shading, fresnel limb, scanning meridian glow), particles/lines, and an
    atmospheric screen-space halo.
  - 1 100-star parallax starfield, 15° graticule, great-circle data arcs between eight world
    hubs with travelling pulses, and an animated scan meridian.
  - Drag-to-orbit, pinch / ⌘-Ctrl-scroll zoom, auto-orbit, and a graceful 2D fallback when
    WebGL is unavailable.
- **Video input**: MP4/WebM files loop and drive the sonification frame by frame.
- **Flat scan mode** (canvas 2D) retained alongside the globe, with beam, graticule and
  analysis-window overlays.
- **Sound design layer**: convolution reverb from a generated impulse, feedback delay, stereo
  panner, sub-bass, vibrato lead, transient pulses, FM bells, noise hats and kick, all through
  a dynamics compressor.
- **Per-scene acoustic signatures**: Lydian / Dorian / pentatonic / minor scales, individual
  oscillator mixes, filter settings and effect depths.
- **Auto tour** (12 s per scene), **audio session recording** to `.webm` via MediaRecorder.
- **Keyboard control** for every action, plus a help dialog.
- **Accessibility layer**: ARIA live narration, skip link, labelled controls, focus styling,
  high-contrast mode, `prefers-reduced-motion` support, screen-reader stage description.
- **Telemetry HUD**: dominant frequency, note name, warmth, luminance, transient delta, stereo
  position, live spectrum, FPS and engine status pills.
- **Land mask pipeline**: Natural Earth 1:50m TopoJSON rasterised to a packed bitmap at build
  time (documented in the README architecture section).
- `LICENSE` (MIT) and `CHANGELOG.md`.

### Changed
- Unified data pipeline: one 512 × 256 field canvas drives audio analysis, the flat scanner and
  the WebGL texture, so audio and visuals can never disagree.
- Analysis now runs on a 64 × 32 downsample with smoothed features and a gamma-corrected
  luminance curve, giving a much wider musical dynamic range on dark scenes.
- Pitch mapping combines thermal warmth with the vertical light centroid.
- Layout rebuilt as a responsive two-column stage/rail dashboard with a full-width info section.
- Reduced-motion users start with auto-orbit off.

### Fixed
- Still images now produce audible rhythm (scan-line delta) instead of a static drone.
- Globe longitude mapping corrected so east appears to the right when viewed from outside.
- Model matrix corrected to a true orthonormal rotation (`rotX · rotY`).
- Reverb/delay switches are respected on first audio initialisation.
- Wheel zoom no longer traps page scrolling (requires ⌘/Ctrl or a pinch gesture).
- Uploaded media is revoked and released when clearing or switching scenes.

### Removed
- Pixel-by-pixel 960 × 540 drawing loop in favour of a 512 × 256 field plus GPU texture.

## [1.0.0] — 2026-11-14

- Initial sonification prototype: four procedural NASA-inspired scenes, real-time column scan,
  Web Audio synthesis, telemetry HUD and custom image loading.
- Lite single-file accessible build (*Earth Jukebox*) with pentatonic mapping and ARIA narration.
