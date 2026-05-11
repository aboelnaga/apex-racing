# APEX

A polished top-down 2D racing game built with Phaser 3. Procedurally-generated tracks, drift physics, three AI opponents with distinct personalities, three random themes, and a full art pass using Kenney CC0 sprites.

**Play it:** https://aboelnaga.github.io/apex-racing/

## Features

### Gameplay

- **Procedural tracks** — every race generates a unique closed-loop course via convex-hull → push-apart → radial perturbation → Catmull-Rom smoothing.
- **Drift physics** — separate forward and lateral velocity components; lateral grip drops at high speed so corners actually slide.
- **3 AI opponents with personalities** — AGGRO (fastest, late on the brakes), BLITZ (baseline), CRUISE (slower top speed, more cautious through corners).
- **Difficulty also picks race length**:
  - **EASY** — 1 lap, gentle AI
  - **NORMAL** — 2 laps, balanced
  - **HARD** — 3 laps, full-speed AI
- **Boost pads** — multi-chevron strips on the straights. Pick one up for +32% top speed for 1.8s and a forward kick.
- **Oil spots** — heavy iridescent puddles on tight corners. Lateral grip drops to 18%, easy to spin out.
- **Car-vs-car collisions** — elastic separation with velocity damping. Heavy impacts visibly darken (damage) the involved cars.
- **Off-track penalty** — speed-capped at 180, with audible grass noise and a dust trail behind your wheels.

### Themes (random per race)

- **Forest** — green grass, red/white curbs, tree clusters, woodland critters (rabbit, pig, monkey, panda), drifting autumn leaves
- **Desert** — sand-tan ground with subtle dune ridges, terracotta curbs, scattered rocks, blown sand
- **Lake** — deep blue water with ripples + sun glints, white curbs, palm trees, twinkling sparkles

### Visual polish

- Kenney sprite assets everywhere — cars, oil splat, arrow chevrons, skidmarks, trees, rocks, tribunes, race barriers, tire stacks, traffic cones, particle effects, animals
- Track furniture placed contextually — tribunes on long straights, tire stacks at corner apexes, cones along inside curbs in tight sections, race barriers at start/finish
- Layered road halo for a sharp asphalt silhouette against the surrounding terrain
- Skid marks dropped behind sliding rear wheels, fade over ~2s
- Off-track wheel dust using Kenney's dirt particle
- Collision flash (Kenney spark + light burst) when the player bonks an opponent
- Boost particle explosion combining sparks + smoke puff
- Camera lookahead at speed, smooth follow with lerp
- Theme-specific ambience particles drifting across the world

### UI / UX

- **Card-style menu** matching the end-screen modal — chevron flair around the **APEX** title, racing accent stripe, animated track preview that regenerates every 6 seconds, color-coded difficulty pills (green / orange / red), theme variety preview row, and a vertical-gradient background with drifting speed lines.
- **In-game HUD**:
  - Stats panel top-left — LAP, POS, TIME, LAST, BEST
  - **Speedometer panel top-right** — half-circle gauge with rotating needle, tick marks, colored fill (green → yellow → red), and big numeric speed underneath
  - Controls strip bottom-left for at-a-glance key reminders
  - Mini-map bottom-right with player direction triangle, AI dots, and boost pad indicators
- **End screen** with proper modal panel — "YOU WIN!" with confetti or "YOU LOSE" with a shake, stats summary, full 4-car ranking, and **RACE AGAIN / NEW TRACK / MENU** buttons that work at any camera position.

### Audio (all synthesized — no audio files)

- Continuous engine: sub-octave triangle + sawtooth one octave up, through an aggressive low-pass; frequency and gain track speed.
- Skid loop — high-passed noise, gain follows lateral velocity while on-track.
- Grass loop — low-passed noise when off-track.
- Crowd cheering — band-passed noise with a slow LFO swell, gain ramps up near tribunes. Surges briefly on each lap completion.
- Countdown beeps (3-2-1-GO!), lap ding, win fanfare, lose horn, boost sweep, collision bonk — all synthesized via Web Audio.

## Controls

| Key | Action |
|-----|--------|
| WASD / Arrow keys | Drive |
| P | Pause |
| M | Mute |
| R | New random track |
| Space | Restart same track |
| Esc | Back to menu |
| Enter | Start race (from menu) |

## Tech stack

- **Phaser 3.80** (loaded from CDN, no build step)
- **Web Audio API** for every sound
- Plain HTML + JavaScript — single `index.html`, no bundler
- Kenney CC0 sprite assets under `assets/`

## Running locally

```sh
# from the repo root
python3 -m http.server 8000
# then open http://localhost:8000/
```

Most browsers restrict local-file image loading over `file://`, so a one-line static server is the most reliable way to play locally.

## Credits

Sprites from [Kenney.nl](https://kenney.nl) (all CC0):

- [Racing Pack](https://kenney.nl/assets/racing-pack) — cars, oil, arrow chevrons, skidmarks, trees, rocks, tribunes, barriers, tires, cones
- [Particle Pack](https://kenney.nl/assets/particle-pack) — boost sparks, smoke, dirt, light flash
- [Animal Pack](https://kenney.nl/assets/animal-pack) — rabbit, pig, monkey, panda

Built on [Phaser 3](https://phaser.io) (MIT). All audio synthesized in-browser via the Web Audio API.

## License

MIT — do whatever you want with it.

---

Built by [@aboelnaga](https://github.com/aboelnaga).
