# Photo Location Map Generator

A pair of browser-based tools for photographers to extract GPS data from photos and build Google Maps collections. Built for scouting shoot locations around Tokyo.

No server. No uploads. Everything runs locally in your browser.

---

## Tools

### `photo-to-map.html` — Batch Map Exporter
Drop a folder of photos, extract all GPS coordinates at once, and export a KML file for direct import into Google My Maps.

### `photoscout.jsx` — Single Photo Scout (React)
Drop individual photos to get GPS coordinates, a Google Maps link, and an AI-powered location scouting note via the Anthropic API. Includes film simulation presets (Kodak Portra, Fuji Velvia, Ilford HP5, Cinestill 800T).

---

## How It Works

Both tools read GPS data directly from the EXIF metadata embedded in JPEG files. The parsing is done entirely in the browser using the native `FileReader` and `ArrayBuffer` APIs — no libraries, no dependencies, no data leaves your machine.

The only external call is the AI analysis in `photoscout.jsx`, which sends the image to the Anthropic API to generate a scouting note.

---

## Usage

### Batch Exporter (`photo-to-map.html`)

1. Open the file in any modern browser
2. Drop a folder of photos or select multiple files
3. Photos with GPS data are marked green; without are marked red
4. Click **Download KML File**
5. Open [Google My Maps](https://mymaps.google.com)
6. Create a new map → **Import** → upload the KML file
7. All your pins appear, labeled with the photo filename

### Single Photo Scout (`photoscout.jsx`)

Requires a React environment and an [Anthropic API key](https://console.anthropic.com).

```bash
# Install dependencies
npm install react react-dom

# Add your Anthropic API key to your environment
ANTHROPIC_API_KEY=your_key_here
```

Drop a photo into the app to see:
- Exact GPS coordinates
- Direct link to Google Maps satellite view
- AI scouting note (best time of day, lighting tips, composition ideas)
- Film simulation preview

---

## GPS Requirements

Photos must have location data embedded at capture time.

**iPhone:** Settings → Privacy & Security → Location Services → Camera → *While Using*

**Android:** Camera app → Settings → Location tags → *On*

**DSLR / Mirrorless:** Most cameras require a GPS accessory or post-shoot geotagging via software like Lightroom or GPicSync.

---

## Tech

- Vanilla HTML/CSS/JS (batch exporter — zero dependencies)
- React + Tailwind (single photo scout)
- EXIF GPS parsing via raw `ArrayBuffer` / `DataView`
- KML generation for Google My Maps import
- Anthropic Claude API for AI location analysis

---

## Project

Built as part of the workflow for scouting portrait and editorial shoot locations in Tokyo.

---

## License

MIT
