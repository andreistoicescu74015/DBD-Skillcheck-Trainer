# DBD Skill Check Trainer

A lightweight, browser-based trainer for the **skill check** timing minigame from *Dead by Daylight* — the spinning dial where you tap a key the instant the needle crosses the white zone to land a **Great**.

Everything lives in a **single self-contained HTML file**: no install, no build step, no dependencies, no network. Open it in a browser and start training. Your settings and stats save automatically.

> **Disclaimer** — This is an unofficial, fan-made practice tool. It is **not** affiliated with, endorsed by, or connected to Behaviour Interactive or *Dead by Daylight*. All sounds are **synthesized in the browser** (Web Audio API) — they are **not** the game's audio files. Zone sizes and timings are *calibrated approximations* based on community/wiki values, meant for building muscle memory rather than being a frame-accurate simulation.

## Quick start

1. Open `skillcheck-trainer.html` in any modern browser (Chrome, Edge, Firefox).
2. Press **Enter** to start.
3. Press **Space** when the red line sweeps into the white zone — land it in the small, bright **Great** band at the front of the zone for a perfect hit.
4. Click the ⚙ button (top-right) to open the menu and tweak perks, zone size/position, appearance, audio, and controls.

> Tip: rename the file to `index.html` and enable GitHub Pages to play it straight from a URL.

## Controls

| Action            | Default   | Notes        |
| ----------------- | --------- | ------------ |
| Start / Stop      | **Enter** | Rebindable   |
| Hit skill check   | **Space** | Rebindable   |

Both actions can be rebound to any key **or mouse button**, including **M4 / M5** side buttons — handy for matching whatever you use in-game.

## Features

**Gameplay**
- Continuous practice loop so you can grind timing, with an optional gap between checks.
- Authentic **Great / Good** zones: a bright **Great** band (perfect hit) at the leading edge of a wider **Good** band.
- Random zone position on the dial (set by clock position), or pin it to a single spot.

**Perk & ability simulation** (toggle in the menu)
- **Unnerving Presence** — shrinks the Good zone (−60%) for a brutally tight window.
- **This Is Not Happening (Injured)** — grows *only* the Great zone (+30%).
- **Hyperfocus** — speeds up the dial per stacked Great (+4% / stack, up to 6); a miss resets the stacks.
- **Doctor · Madness** — skill checks can spin in **reverse** and appear at random spots on the screen.
- **Hex: Huntress Lullaby** — removes the warning "appear" sound, so you react purely on sight.

**Tunable baseline**
- Rotation time, Great-zone size, Good-zone size.
- Doctor spawn area: how far from centre random skill checks can appear.

**Live performance tracking**
- Recent **form**: rolling % Great and average error in milliseconds.
- Running tallies: checks, greats, goods, misses, and best streak.
- An **early/late meter** that visualises your timing bias — recent hits show taller and brighter, with a marker for your average offset.
- Optional **±ms readout** in the centre of the dial after each hit.

**Appearance**
- Adjustable dial size, ring (block) thickness, and needle thickness.
- High-contrast mode (green Great vs. white Good).

**Quality of life**
- Synthesized audio with distinct appear / good / great / fail cues.
- Profile auto-saves to the browser; **Export / Import** as JSON to move it between machines.
- Fullscreen mode.

## How it works

- A single static HTML file: vanilla JavaScript with the **Canvas 2D** API for rendering and the **Web Audio API** for sound.
- ~400 lines, zero dependencies, no build tooling.
- State persists via `localStorage` — settings and stats save on every change and after every hit.

## Tips

- Keep high-contrast **off** to mirror the real game; turn it **on** when you want to clearly see where Great ends.
- Watch the early/late meter: if the average marker sits to the left you're hitting **early** (react slightly later), and vice-versa.
- Train with **Unnerving Presence** on to tighten the window — the real game then feels generous.

## License

No license chosen yet. Until one is added, all rights are reserved by the author. If you'd like others to reuse it, consider adding an [MIT](https://choosealicense.com/licenses/mit/) license.
