NASA Space Apps Challenge 2026 · The Earth Information Jukebox

> **Note:** this is the *lite* single-file build. The full application — holographic 3D globe with 1800 stars, live satellite fleet, video input, auto tour, session recording, louder audio and Live Earth public real-time checks — is `index.html` in this repository.

# MSB NASA EARTH VIEW

Hear the Earth. Pick a scene or load a NASA Earth image or video, and the colours, brightness and motion become live sound: cool blues sound low and deep, warm reds sound high and bright.

Load NASA image or video · Volume louder (1.15× master) — works even on dark images

Choose a scene and press Play.

**Colour → Pitch**

Cool = low · Warm = high

**Brightness → Volume**

Dark = soft · Bright = loud (boosted)

**Motion → Rhythm**

Change triggers percussion

## How it works

- Each frame is scanned for average colour, brightness, where the light sits left to right, and frame-to-frame change.
- Warmth sets the note on a pentatonic scale, brightness sets loudness and filter opening, position sets stereo pan, and motion triggers drum pulses.
- Sound is synthesized live with the Web Audio API. No recorded tracks.
- Still images are swept by a moving scan line, so the picture is heard from left to right over 14 seconds.
- **Full app adds:** 1800 twinkling stars, 7 orbiting satellites (ISS, Himawari-9, GOES-18, NOAA-20, Terra, Aqua, GPM) with trails; a Live Earth panel that fetches open disasters from NASA EONET (public, no key) and links to NASA Climate vital signs for global warming / CO₂ / sea level; a **Scientific Lab** shown as one merged page (7.1 Air Quality, 7.2 Climate Lab, 7.3 Water & Ice, 7.4 Hazards, 7.5 Satellite comparison with a public-data graph); and a **20-language** interface pill (Arabic and Urdu switch to right-to-left).

## Data and disclosures

The four built-in scenes (sea surface, aerosols, night lights, lightning) are procedurally generated demo visuals, not NASA data. To hear real data, download frames or animations from the NASA Earth Information Center or the NASA Scientific Visualization Studio and load them above — or use `index.html` to load NASA GIBS imagery directly. NASA media are credited to NASA. Live disaster data in `index.html` comes from NASA EONET (public API, no key). Your files stay in your browser and are not uploaded. Team MSB Creative Studios. Super Intelligence tools were used to help write and debug code and documentation; mapping logic and creative direction are by the team. Sonification approach inspired by NASA’s data sonification work.

**Full instructions:** see `README.md` → *Live Earth science — public real-time checks*, *Scientific Lab — five datasets, one page* and *Languages — 20, with right-to-left support*, then open `index.html` to hear it.
