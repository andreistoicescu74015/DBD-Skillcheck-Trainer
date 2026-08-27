# DBD Skill Check Trainer

A browser trainer for the skill check from *Dead by Daylight*: the dial with the sweeping needle, where you tap a key as the needle crosses the white zone and try to land the small bright band at its front for a Great.

The whole thing is one HTML file. No install, no build step, no dependencies, no network calls. Open it in a browser and start training. Settings, stats and your run history save themselves.

Play it here: [andreistoicescu74015.github.io/DBD-Skillcheck-Trainer](https://andreistoicescu74015.github.io/DBD-Skillcheck-Trainer/)

> Disclaimer. This is an unofficial fan-made practice tool. Behaviour Interactive is not involved with it and has not endorsed it. Every sound is synthesized in the browser with the Web Audio API, so none of the game's audio files are used here. Zone sizes and timings follow the community wiki values and are meant for building muscle memory, not for frame-accurate simulation.

## Quick start

1. Open the live version, or download `index.html` and open it in any modern browser.
2. Press Enter to start.
3. Press Space as the red needle enters the white zone. The bright band at the front of that zone is the Great.
4. Open the panel with the gear button at the top right, or with Escape, to change anything below.

## Controls

| Action          | Default | Notes                                        |
| --------------- | ------- | -------------------------------------------- |
| Start / stop    | Enter   | Rebindable                                   |
| Hit skill check | Space   | Rebindable                                   |
| Open / close panel | Escape | Fixed                                       |

Both actions take any key, mouse button or controller button, side buttons M4 and M5 included, so you can match what you use in game. On a touch screen there is no keyboard, so one tap starts the run and every tap after that is a hit.

A controller is invisible to the browser until you press a button on it, so press one before you hit Rebind. Button names are the standard layout, Xbox first and PlayStation second: on Windows every XInput device reports the same id, so a DualSense through Steam cannot be told from an Xbox pad.

A pad has no input events, only a buffer the page reads, so a press reads about 5 to 8ms later than a key and about twice as loose. That is the browser polling the device, not you, and the game has the same latency, so the number is shown rather than subtracted. It is why runs hit with a pad are saved and compared apart from runs hit with a key.

## What it simulates

Five actions come as presets, with the wiki's tier III values for rotation time, Great size and Good size:

| Action           | Rotation | Great | Good |
| ---------------- | -------- | ----- | ---- |
| Repair           | 1100ms   | 3%    | 10%  |
| Heal             | 1200ms   | 3%    | 12%  |
| Decisive Strike  | 1100ms   | 7%    | 0%   |
| Overcharge       | 1000ms   | 5%    | 0%   |
| Snap Out of It   | 1200ms   | 12%   | 0%   |

Overcharge is the difficult check, so it also stands in for Oppression. Rotation time, Great size, Good size, where on the dial the zone can appear and the pause between checks are all sliders, so any value the presets do not cover is a drag away.

Nine perks and abilities can be toggled on top of that baseline. Only the part that changes the check itself is simulated: trigger odds, bonus progression, status effects and repair speed are left out.

| Toggle                | Effect here                                                                    |
| --------------------- | ------------------------------------------------------------------------------ |
| Unnerving Presence    | Good band shrinks by 60%, Great untouched                                       |
| This Is Not Happening | Great band grows by 30%, Good untouched                                         |
| Hyperfocus            | +4% dial speed per token, six tokens, a Great banks one and anything else spends them all |
| Coulrophobia          | +50% dial speed, healing checks                                                 |
| Stake Out             | One token every 15 seconds, four at most; a Good spends one and counts as a Great |
| Doctor, Madness       | The sweep can run backwards and the dial appears anywhere in the spawn area      |
| Hex: Huntress Lullaby | No warning sound when a check appears, so you react on sight                     |
| Merciless Storm       | No Great zone at all, and the chain never pauses between checks                  |
| No Quarter            | The same chained check, on a self-heal instead of a generator                     |

When a combination cannot happen in a match, for instance Coulrophobia on a repair check, the panel says so instead of quietly simulating it.

## Training tools

Runs come in lengths of 20, 50 or 100 checks, or Free if you just want to grind. A finished run opens a card with the split between great, good and miss, your average error, whether you drifted between the first and second half, your best streak, and how it compares with your last run set up the same way.

Those cards are kept. The History section holds the last 60 runs as a bar per run, with the ones matching your current baseline and perks picked out in green, so a Repair run is never compared against a Snap Out of It run.

Adaptive difficulty tightens the whole success zone after three greats in a row and widens it after anything else. Leave it on and it settles at the tightest window you can hold, which is a harder target than any fixed preset.

While a run is going you get: a rolling percentage over the last 60 checks with your spread and whether you lean early or late, an early/late meter with the Great window drawn on it and a marker for your average offset, an arc on the dial showing how far your press landed from the middle of the zone, and the error in milliseconds in the middle of the dial.

## Appearance and sound

Dial radius, zone thickness, needle thickness and needle length are all adjustable, which is how you match the size the game draws on your monitor. High-contrast mode paints the Great band green against a white Good band. The FPS counter is optional.

Audio is synthesized: a cue when the check appears, and distinct good, great and fail sounds. A check that ran out sounds duller than a mistimed press, so you can tell them apart without looking. Release the volume slider to hear a Great at that level.

## How it works

One static HTML file: vanilla JavaScript, the Canvas 2D API for the dial and the meters, the Web Audio API for sound. Around 630 lines of script, no dependencies, no build tooling.

The profile lives in `localStorage` and covers settings, lifetime stats and run history. Export writes all three to a JSON file and Import reads one back, which is how you move a profile between machines. Reset settings restores the defaults and leaves your stats and history alone.

## Tips

Leave high-contrast off to mirror the game, and turn it on when you want to see exactly where Great ends.

Watch the marker on the early/late meter. Sitting left of centre means you are hitting early, so react a little later.

Train with Unnerving Presence on, or with adaptive difficulty, and the real game feels generous afterwards.

## License

MIT, see [`LICENSE`](LICENSE). Copyright 2026 Andrei Stoicescu.
