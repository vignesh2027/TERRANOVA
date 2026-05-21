# TERRANOVA

**See Earth. Watch Space. Track Everything.**

A premium real-time Earth intelligence dashboard combining Google Maps and NASA APIs in a single HTML file — no build step, no frameworks, no dependencies beyond the API scripts.

**Live →** [vignesh2027.github.io/TERRANOVA](https://vignesh2027.github.io/TERRANOVA/)

---

## What it does

TERRANOVA opens with a 22-second cinematic Three.js Earth — realistic textures, atmospheric glow, starfield, smooth orbital camera — then fades into a full-screen live dashboard.

### Google Maps layer
- Custom dark cartographic style (navy land, blue highways, dark ocean, warm white labels)
- Street View, satellite, terrain, and hybrid modes
- Places autocomplete search bar
- Click any point on Earth → coordinates, country, local time, UTC offset, NASA EPIC imagery of that region
- Measure distance between any two points
- Earthquake density heatmap toggle
- Day/Night terminator overlay

### NASA data panels

| Panel | API | What it shows |
|---|---|---|
| **APOD** | `/planetary/apod` | Daily astronomy photo with date picker and full-resolution modal |
| **Asteroid Radar** | `/neo/rest/v1/feed` | Animated canvas radar — every near-Earth object passing today, sized by diameter, red if hazardous |
| **EPIC Earth** | `epic.gsfc.nasa.gov` | Full-disc Earth photos from the DSCOVR satellite, cycling every 5 s |
| **EONET Events** | `eonet.gsfc.nasa.gov/api/v3` | All active wildfires, storms, earthquakes, volcanoes, floods plotted as map markers |

### Live refresh
- EONET events — every 5 minutes
- Asteroid feed — every 30 minutes
- APOD — daily at midnight UTC
- All responses cached in `localStorage`; stale cache served if an API call fails

---

## Stack

- **Three.js r134** — cinematic intro Earth globe
- **Google Maps JavaScript API** — maps, geocoding, places autocomplete, heatmap, geometry
- **NASA Open APIs** — APOD, NeoWs, EPIC, EONET (all free)
- Zero npm, zero build, zero frameworks — plain HTML + CSS + JS in one file

---

## Setup

1. Clone or download `index.html`
2. Open it in a browser served over HTTP (required for the Google Maps key domain check)

The file ships with working API keys for immediate use. To use your own:

- **NASA key** — [api.nasa.gov](https://api.nasa.gov) (free, instant)
- **Google Maps key** — [console.cloud.google.com](https://console.cloud.google.com) — enable Maps JavaScript API, Places API, Geocoding API, Visualization library

Paste your NASA key in the ⚙ settings panel inside the app. To swap the Maps key, edit the `GM_KEY` variable at the top of the `<script>` block.

### GitHub Pages

The repo is configured to serve from `main /`. Any push to `main` updates the live site automatically.

If the Google Maps tiles are blank on Pages, add `vignesh2027.github.io` to the allowed referrers for your Maps API key in Google Cloud Console.

---

## Features at a glance

```
22s cinematic Three.js Earth intro
├── Realistic day texture + specular + normal maps
├── Cloud layer (separate mesh, slightly faster rotation)
├── Atmospheric glow (inner + outer sphere, additive)
├── 9,000-point starfield
└── 7-keyframe eased camera path with city callouts

Full-screen Google Maps
├── Custom dark style (24 style rules)
├── EONET natural event markers (SVG icons per category)
├── Filter chips — toggle event types, badges update live
├── Collapsible left sidebar (events list) + right panel (space data)
├── Measure tool — click two points, see km/mi
├── Heatmap — earthquake density via Maps visualization library
├── Day/Night terminator circle overlay
└── Click-to-fly on any event in the sidebar

Right panel
├── APOD — image, title, date picker, fullscreen explanation modal
└── NeoWs radar — canvas, rotating sweep, glowing dots, hover details

Status bar — API health indicators, live coordinate display
Settings panel — swap NASA key without editing code
```

---

## Screenshots

> Map view with active events, asteroid radar, and EPIC Earth panel

*(Open [the live site](https://vignesh2027.github.io/TERRANOVA/) to see it in action)*

---

## License

MIT
