# APEX

Top-down 2D racing game. A new random track every race, drift physics, three AI opponents with distinct personalities, boost pads, oil spots, and three visual themes.

**Play it:** https://aboelnaga.github.io/apex-racing/

## Features

- **Procedural tracks** — every race generates a unique closed-loop course (random points → convex hull → push apart → perturb → Catmull-Rom spline).
- **Drift physics** — forward and lateral velocity components decoupled; grip drops at high speed so corners actually slide.
- **3 AI opponents with personalities**
  - **AGGRO** — fastest top speed, harder corner throttle
  - **BLITZ** — baseline
  - **CRUISE** — slower top speed, more cautious in corners
- **Difficulty** — Easy / Normal / Hard, scales AI top speed and corner-handling.
- **Themes** — Forest / Desert / Lake, picked randomly per race. Theme swaps the surrounding terrain colour, track edge colour, and decoration sprites (trees / cacti / palms).
- **Boost pads** — yellow chevron-striped strips on the straights. Hit one for +32% top speed for 1.8s and a forward kick.
- **Oil spots** — dark iridescent puddles in the corners. Lateral grip drops to 18% — your steering won't save you.
- **Car-vs-car collisions** — soft elastic push when cars converge; light bonk sound on player contact.
- **Synthesised audio** — no audio files, everything via Web Audio API. Continuous engine drone (dual-oscillator with low-pass filter), tire skid noise on hard cornering, grass rumble off-track, countdown beeps, lap ding, win fanfare, lose horn, boost whoosh, collision bonk.
- **Polished UI** — start menu with animated track preview, 3-2-1-GO countdown, live mini-map with all four cars and boost-pad markers, end screen with full ranking, win/lose animations, confetti on victory.
- **Lap timer** — current lap, last lap, best lap.

## Controls

| Key | Action |
|---|---|
| ↑ / W | Accelerate |
| ↓ / S | Brake / reverse |
| ← → / A D | Steer |
| P | Pause |
| R | New random track |
| Space | Restart current race |
| Esc | Back to menu |
| M | Mute |
| Enter | Start (from menu) |

## How to play

1. Pick a difficulty on the start menu.
2. Hit **START**.
3. Race 2 laps. Beat the three AI opponents. Finish 1st of 4 to win.
4. Hit yellow boost pads on the straights for top speed.
5. Avoid oil spots in the corners — they'll send you sliding wide.

## Tech

Single self-contained `index.html`. No build step, no dependencies, no framework.

- HTML5 `<canvas>` 2D rendering
- Vanilla JavaScript (~2,000 lines)
- Web Audio API for all sound (no audio assets)
- Procedural track generation, drift physics, and AI all hand-rolled

## Run locally

Either:

- Double-click `index.html` (works in any modern browser via `file://`).
- Or serve statically:
  ```sh
  python3 -m http.server 8000
  # then open http://localhost:8000
  ```

## Deploy

Hosted on GitHub Pages — pushing to `main` auto-redeploys. No CI configuration required.
