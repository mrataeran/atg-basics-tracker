# ATG Basics Tracker

A single-file, offline-friendly web app for running the ATG Basics routine.

**Live:** https://mrataeran.github.io/atg-basics-tracker/

## What it does

- Three workout days: Lower Body (Mon), Upper Body (Wed), Spine (Fri)
- Per-set logging of weight and reps, with completion checkmarks
- Tempo prescriptions expanded into plain English (e.g. 41X1)
- Built-in rest timer (60s / 90s / 2m) that auto-starts when a set is checked
- Per-exercise scratch notes
- Session history: press Finish to archive a workout and reset the checkmarks
- Video slot per exercise, with an HLS (.m3u8) capable player via hls.js
- A YouTube search link per exercise as a fallback tutorial

## Privacy / data

Everything lives in your browser's localStorage under the key `atgb.v1`.
Nothing is uploaded, and no accounts or servers are involved.
No third-party video content is bundled in this repository.

## Adding your own video links

Open an exercise, tap **+ Add video link**, and paste a URL (`.m3u8`, `.mp4`, or any direct video link).
Links are keyed by exercise name and are stored only on that device.

To load many at once, tap the gear icon and paste a JSON map, then press **Import / merge**:

```json
{
  "ATG Row": "https://example.com/atg-row.m3u8",
  "Pancake": "https://example.com/pancake.mp4"
}
```

The gear menu also exports your full dataset as JSON so you can move it between devices.

## Install on a phone

Open the live URL, then use Share -> Add to Home Screen (iOS) or the install prompt (Android).
It runs full screen like a native app.

## Editing the routine

All exercise data is in the `DAYS` array near the top of the script block in `index.html`.
