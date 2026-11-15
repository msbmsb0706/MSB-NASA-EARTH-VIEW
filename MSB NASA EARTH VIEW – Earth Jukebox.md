NASA Space Apps Challenge 2026 · The Earth Information Jukebox

> **Note:** this is the *lite* single-file build. The full application — holographic 3D globe, video input, auto tour and session recording — is `index.html` in this repository.

# MSB NASA EARTH VIEW

Hear the Earth. Pick a scene or load a NASA Earth image or video, and the colours, brightness and motion become live sound: cool blues sound low and deep, warm reds sound high and bright.

Load NASA image or video Volume

Choose a scene and press Play.

**Colour → Pitch**

Cool = low · Warm = high

**Brightness → Volume**

Dark = soft · Bright = loud

**Motion → Rhythm**

Change triggers percussion

## How it works

- Each frame is scanned for average colour, brightness, where the light sits left to right, and frame-to-frame change.
- Warmth sets the note on a pentatonic scale, brightness sets loudness and filter opening, position sets stereo pan, and motion triggers drum pulses.
- Sound is synthesized live with the Web Audio API. No recorded tracks.
- Still images are swept by a moving scan line, so the picture is heard from left to right over 14 seconds.

## Data and disclosures

The four built-in scenes (sea surface, aerosols, night lights, lightning) are procedurally generated demo visuals, not NASA data. To hear real data, download frames or animations from the NASA Earth Information Center or the NASA Scientific Visualization Studio and load them above. NASA media are credited to NASA. Your files stay in your browser and are not uploaded. Team MSB Creative Studios · Mysore local event. Super Intelligence tools were used to help write and debug code and documentation; mapping logic and creative direction are by the team. Sonification approach inspired by NASA’s data sonification work.