# MSB NASA EARTH VIEW — The Earth Information Jukebox

**Hear the Earth.** This app turns NASA satellite pictures into live music, shows a 3D Earth with satellites
in orbit, and adds public real-time data you can read, click and listen to.

**NASA Space Apps Challenge 2026 · Team MSB Creative Studios**

**▶ Open the app:** <https://msbmsb0706.github.io/MSB-NASA-EARTH-VIEW/>

Current version **3.8.0** · works in a normal browser · no account, no installation, no tracking.

---

## What is this, in one minute?

NASA publishes huge amounts of information about our planet: clouds, oceans, air quality, wildfires,
earthquakes, sea level, the Sun's effect on Earth's magnetic field. Most of it can only be understood by
looking at pictures, charts or numbers. That leaves out people who are blind or have low vision, and it makes
fast patterns hard to notice for everyone.

This app turns those pictures and numbers into **sound**. A scan line moves across a satellite image, and the
colour, brightness and movement under the line become notes, volume, stereo position and rhythm. Nothing is
recorded: every sound is generated live in your browser.

You can also explore public live data with your ears and eyes:

- air quality where you live,
- wildfires, storms and earthquakes happening now,
- Earth's climate and sea-level records,
- the solar wind and geomagnetic storms hitting Earth right now,
- how much sunlight each planet is getting at this moment,
- and when the International Space Station passes over your own town.

Everything runs in the browser. Nothing you load is uploaded, and there are no ads or trackers.

---

## How to open it

**Easiest:** go to <https://msbmsb0706.github.io/MSB-NASA-EARTH-VIEW/>.

**Offline copy:** download `index.html` and double-click it. The demo scenes and your own photos and videos
work without internet. Live data needs a connection.

**On your own computer with a local web server** (only needed if your browser is strict about local files):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Use a recent Chrome, Edge, Firefox or Safari. Headphones are nice, but not required.

---

## Your first two minutes

1. When the page opens, press **▶ Start sonification**. Browsers only allow sound after a click, so nothing
   plays before that.
2. The scan line sweeps across the Earth picture. Listen: brighter areas get louder, warmer colours climb in
   pitch, and the left/right position of the light moves the sound across your ears.
3. Press **Start near-real-time view + sound** to load the newest Himawari infrared image of Asia and the
   Pacific (choose GOES-East for the Americas). It updates about every 10 minutes.
4. Press **1**, **2**, **3** or **4** to try the four built-in scenes: ocean currents, aerosols, city lights and
   lightning.
5. Scroll down to **6 Live Earth**, then **7 Scientific Lab**, then **8 Space weather, planets & satellites**.
   The last three are full of public live data — see what to click below.

There are no wrong buttons. Everything can be stopped, reset or replayed.

---

## What is on the screen

| Section | What it is | What you can do |
| --- | --- | --- |
| **1 · EIC dataset jukebox** | NASA satellite imagery (Himawari, GOES, VIIRS, MODIS, GPM rain) plus four demo scenes and your own photo/video | Pick a layer and a date, load it, or drop in any image or video. Sound follows whatever is on screen |
| **2 · Frame scanner & acoustic engine** | The big stage with the 3D globe or the flat scan | Play/pause, change scan speed and volume, turn reverb and auto-orbit on/off, drag to spin the globe |
| **3 · Sound design** | Four instrument characters and six musical scales | Change the mood without changing the data: holographic, jukebox lite, cinematic or kinetic |
| **4 · Live acoustic telemetry** | The current note, brightness, warmth, pan and motion | Watch what the scanner is "hearing" right now |
| **5 · Mapping monitor** | Bars showing how each visual quality is being turned into sound | Learn the translation from picture to music |
| **6 · Live Earth** | Global warming, CO₂ and sea level, NASA's open disasters, the live satellite fleet | Check live disasters, hear the warming curve, track the ISS |
| **7 · Scientific Lab** | 7.1 air quality · 7.2 climate · 7.3 water & ice · 7.4 earthquakes · 7.5 satellite comparison | Use your location for air quality, click any chart to hear it, download CSV data |
| **8 · Space weather, planets & satellites over you** | 8.1 solar wind and storms · 8.2 Earth's rotation · 8.3 sunlight on every planet · 8.4 ISS passes over you | Refresh space weather, hear the storm curve, click a planet, or find the next pass over your town |

At the top of the page you also get an **Auto tour**, a **Record** button (saves a video of what you hear),
a **🌐 LANG** menu with 20 languages, light/dark theme, high contrast, help and fullscreen.

---

## Five things to try

**1. Hear yesterday's satellite picture.** Choose *Himawari infrared*, leave **Follow latest available** on,
press **Load selected imagery**, then **Start sonification**. Sweeping from west to east, cloud tops sound
different from warm land and sea.

**2. Check the air where you live.** Go to **7.1 Air Quality**, press **📍 Use my location**, then
**🔊 Sonify AQI**. Clean air is a smooth tone; polluted air is harsher and noisier.

**3. Find the space station.** Go to **8.4 Satellites passing over your place**, press **📍 Use my location**,
then **🔭 Find ISS passes (3 days)**. Click a pass to see its arc across your sky, add it to your calendar, or
hear the pass rise and fall. A **VISIBLE** label means the sky will be dark and the station will be sunlit.

**4. Compare sunlight on the planets.** In **8.3**, see how much energy each planet receives right now. Mercury
gets about ten times Earth's sunlight; Neptune about a thousandth. Click any row to hear the difference.

**5. Ask the big question.** In **8.1** look at Kp (a 0–9 score of how disturbed Earth's magnetic field is) and
in **8.2** read Earth's rotation speed and direction. Then read the honest answer below.

---

## "Does the magnetic field change how Earth rotates?"

**No.** This is a common belief, so the app addresses it directly.

- Earth rotates **west to east**, once every **23 h 56 min 4 s**, and that has not changed because of the
  magnetic field. The spin is left over from the way the planet formed.
- The magnetic field is **produced by** the churning iron in Earth's outer core. It is a result of the planet's
  interior and its rotation, not a motor that drives it.
- Geomagnetic storms from the Sun can disturb radio, GPS, satellites and power grids, and paint the aurora.
  They cannot flip or measurably speed up the whole planet.
- Very small day-length changes (milliseconds) come from tides, the atmosphere, the oceans and the core.
  Tides alone make the day about **1.7 ms longer per century**.

The same honesty applies to the planets. In **8.3** you can see the numbers: the Moon's tidal pull on Earth is
the strongest, the Sun's is about half of that, and every planet is a tiny fraction of a percent. **Planetary
alignments do not measurably change Earth's rotation, tides or earthquakes.**

---

## What you hear, and why

The app reads the picture under the scan line and converts it like this:

| What the picture does | What you hear |
| --- | --- |
| Warm colours (reds, ambers) | Higher notes |
| Cool colours (blues, teals) | Lower, deeper notes |
| Bright areas | Louder, with a more open filter |
| Dark areas | Softer |
| Light on the left or right | Sound moves left or right |
| Rapid change between frames | Percussion and rhythm |

Each scene has its own instrument mix and scale, so the ocean, aerosols, city lights and lightning all sound
different. Public disaster data adds to the mood: when many wildfires and storms are open, the percussion gets
busier even on a still image.

Small "bumps" in the sound are not mistakes. They are real differences in the image — a cloud edge, a coastline,
a city, a patch of clean ocean.

---

## Live data: what is real, and what is a demo

| What you see | Where it comes from | How fresh |
| --- | --- | --- |
| Satellite imagery | NASA GIBS (NASA Earth data), with JMA for Himawari and NOAA for GOES | About 10 minutes for infrared, daily for true-colour mosaics |
| Open disasters | NASA EONET | Every 10 minutes while the page is open |
| Air quality and pollutants | Open-Meteo (CAMS) | Hourly model data |
| Climate and CO₂ records | NASA GISS and the Mauna Loa Keeling record | Published records, not a live feed |
| Sea level and ice | NASA vital signs and GRACE | Published records |
| Earthquakes | USGS | Last 24 hours, refreshed on demand |
| Solar wind, Kp, Dst, storm level | NOAA Space Weather Prediction Center | About every minute at NOAA; the app checks every 5 minutes |
| Planet positions and sunlight | Calculated in your browser from published orbital elements | Recalculated every minute |
| ISS position and passes | Public TLE from api.wheretheiss.at, orbit calculated in your browser | Fresh TLE, positions recalculated every second |
| Four demo scenes | Generated by the app for demonstration | Not NASA observations |

Everything above is public and free. No API key, no login, and no server in the middle: your browser talks to
the source directly.

**Limits worth knowing:**

- Satellite images are pictures, not measurements. The sound follows the colours, not the temperature.
- The air-quality number is an indicator, not an official regulatory AQI.
- The magnetic-field strength uses a simple dipole model, not the official World Magnetic Model.
- ISS pass times are calculated locally and can be **a minute or two off**. Check
  [NASA Spot the Station](https://spotthestation.nasa.gov/) before travelling. This is not navigation data.
- In **8.1**, the aurora estimate is just an estimate from Kp; clouds and local conditions decide what you
  actually see.

---

## Good questions, quick answers

**Do I need an account, a key or an installation?**
No. It is one HTML file. Open it and use it.

**Why is there no sound at first?**
Browsers block audio until you interact with the page. Press **Start sonification**.

**Does it work without internet?**
The four demo scenes, your own images and your own videos work offline. NASA imagery and live data need a
connection.

**Is my location or my photo uploaded anywhere?**
No. Geolocation is used only in your browser to calculate air quality and satellite passes. Images and videos
are processed locally and never leave your device.

**Can I use my own image or video?**
Yes. Drop a JPG, PNG, WebP, GIF, MP4 or WebM into the upload box in section 1. A video becomes a moving
soundscape.

**Can I save what I hear?**
Press **Record** to save a video of the performance, or use the CSV buttons in the Scientific Lab to download
the numbers.

**Why do the planets' numbers keep changing?**
Because they are calculated for the current moment. Mercury moves fastest and noticeably changes its distance
and sunlight over weeks; Earth's own distance to the Sun changes over the year.

**Why is the ISS not visible on a pass marked "daylight"?**
The station may pass overhead while your sky is bright. Only passes with a dark sky **and** a sunlit station
are marked **VISIBLE**.

**Is any of this official NASA output?**
The app uses public NASA data and imagery, and the team built the rest. It is an educational and artistic
project, not an official NASA product.

---

## Languages and accessibility

- The **🌐 LANG** menu switches the main labels between **20 languages**: English, தமிழ், हिन्दी, ಕನ್ನಡ, తెలుగు,
  മലയാളം, বাংলা, मराठी, ગુજરાતી, اردو, ਪੰਜਾਬੀ, 한국어, Español, Français, Deutsch, 中文, 日本語, العربية,
  Português and Русский. Arabic and Urdu switch the page to right-to-left.
- Numbers and units stay in English on purpose, so a value is never misread.
- Everything works by keyboard. Press **H** in the app for the full list.
- Screen-reader announcements describe the scene, the sound and every live update.
- There is a daylight theme, a high-contrast mode, reduced-motion support and large touch targets.

**Handy keys:** <kbd>Space</kbd> play/pause · <kbd>1</kbd>–<kbd>4</kbd> scenes · <kbd>V</kbd> globe/flat ·
<kbd>R</kbd> reset scan · <kbd>D</kbd> sound character · <kbd>S</kbd> scale · <kbd>T</kbd> auto tour ·
<kbd>O</kbd> auto-orbit · <kbd>L</kbd> theme · <kbd>F</kbd> fullscreen · <kbd>H</kbd> help.

---

## For teachers, students and science clubs

- **Sound-first lessons.** Let students describe what they hear, then reveal the image. It works well for
  cloud patterns, ocean currents and night lights.
- **Data literacy.** Use the Climate and Water & Ice charts, then download the CSV and ask what the numbers
  actually show.
- **Local investigations.** Compare air quality across neighbourhoods with **Use my location**, or compare
  your city's satellite image on a clear day and a monsoon day.
- **Space weather day.** Read Kp and Bz in **8.1**, then look at the aurora estimate and explain why Chennai
  and the Arctic see different skies.
- **Scale of the solar system.** Use **8.3** to compare sunlight on Mercury, Earth and Neptune, then compute
  the inverse-square law by hand and check the app.

Everything is free, public and safe for classroom use. No accounts and no data collection.

---

## If something is not working

| Problem | Try this |
| --- | --- |
| No sound | Press **Start sonification**; check the volume and the **Master gain** slider; try headphones |
| NASA image does not load | Check the connection, try another date or layer, or open NASA Worldview. The previous image stays active |
| Air quality or quakes say "failed" | These need internet. Try again, or open the source link in the same card |
| Space weather says "unavailable" | NOAA may be temporarily unreachable from your network. Press **Refresh now** or open swpc.noaa.gov |
| No ISS passes found | Use **📍 Use my location**, then **Find ISS passes**. Some days have no pass above 10°, and a stale TLE can shift times |
| "Use my location" does nothing | Allow location in your browser, or keep the default city shown in the panel |
| The page feels slow | Close other tabs; the flat scan mode uses less power than the 3D globe |

---

## Credits, data and licence

Built by **MSB Creative Studios** for the **NASA Space Apps Challenge 2026**, *Earth Information Jukebox*.

With thanks to the public data providers: **NASA** (GIBS, EONET, GISS, Earth Information Center, SVS),
**NOAA** (GOES, Space Weather Prediction Center), **JMA** (Himawari), **USGS** (earthquakes),
**ESA Copernicus**, **Open-Meteo/CAMS**, **api.wheretheiss.at** (ISS TLE) and the Mauna Loa CO₂ record.

The four built-in scenes are generated demo visuals inspired by NASA datasets, not raw observations. The app
requests imagery and live data directly from the providers; nothing is stored or resold. Only a public-domain
Natural Earth land mask is bundled inside the file.

Released under the **MIT licence** — see [`LICENSE`](LICENSE). Use it, remix it, teach with it.

---

## For developers (optional reading)

The whole application is a single file, `index.html` (about 340 kB), with no build step and no dependencies.

| File | What it is |
| --- | --- |
| `index.html` | The full app: WebGL globe, Web Audio engine, all live-data panels |
| `MSB NASA EARTH VIEW – Earth Jukebox.html` | A smaller flat-scan version; its sound is included in the full app as **Jukebox lite** |
| `MSB NASA EARTH VIEW – Earth Jukebox.md` | Notes for that smaller version |
| `CHANGELOG.md` | Version history |
| `LICENSE` | MIT licence |

Rough internals, for anyone extending it:

- **Rendering:** hand-written WebGL 1 globe (no Three.js), plus a 2D canvas flat scanner and starfield.
- **Audio:** Web Audio API, all synthesised — pads, lead, sub, percussion, convolution reverb, compressor,
  analyser and a recording tap.
- **Data:** direct browser `fetch` to CORS-open public APIs (NASA GIBS/EONET, NOAA SWPC, USGS, Open-Meteo,
  api.wheretheiss.at). No proxy, no secrets.
- **Astronomy:** Keplerian planet positions, a tilted-dipole field, solar position, TLE parsing and a
  J2 orbit propagator for passes. All calculated in the page.
- **Publishing:** push to GitHub and enable **Settings → Pages → Deploy from a branch → `main` / root**.

Browser support: current Chrome, Edge, Firefox and Safari. Older or headless browsers fall back to the flat
scanner while all sound features keep working.

Questions, ideas or classroom use: open an issue in this repository. We would love to hear what you made with
it.
