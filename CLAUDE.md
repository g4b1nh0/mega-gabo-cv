# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this project is

An interactive resume ("Mega CV") built as a retro Mega Man X-style 2D platformer. The player fights through 5 bosses, each representing a real job/career stage of Gabriel Marín (2013–2026). Defeating a boss unlocks the skills acquired during that role; finishing all stages shows a summary screen with links to GitHub/LinkedIn.

## Commands

There is no build step, package manager, linter, or test suite. The entire game is one self-contained file.

- **Run locally**: open `index.html` directly in a browser (double-click, or `start index.html` on Windows). No server, no `npm install`.
- There is nothing to build, lint, or test — verify changes by opening the file in a browser and playing through the affected stage.

## Architecture

Everything lives in a single file: `index.html` (~1700 lines — HTML shell, inline `<style>`, inline `<script>`). There are no other source files besides `README.md`.

### Data-driven stages

`STAGES` (around line 171) is an array of 5 objects, one per career stage, each with:
- `title` — text shown at the top describing the role/period
- `boss` — `{ name, hp, color, w, h }`
- `env` — background/floor/accent colors
- `player` — weapon name/colors for that stage
- `unlock` — `{ title, items }` skills revealed after defeating the boss
- `init` — extra fields merged into `currentBoss` on load beyond `boss`/`x` (starting `w`/`h`/`startY`/`y` and the boss's own state-machine fields, e.g. `chargeState`/`actionTimer`)
- `behavior` — `{ update, draw, particleColor }`: direct references to that stage's `update<Boss>`/`draw<Boss>` functions (declared further down the file — safe due to function-declaration hoisting) plus the single hex color used for both hit-sparks and the defeat explosion

Adding a stage means adding one object here with its own `init`/`behavior`, plus writing the `update<Boss>`/`draw<Boss>`/`shoot<Weapon>` functions it references — no other file needs to change.

### Per-boss functions

Each boss has its own trio of hand-written functions, all following the same naming convention (`draw<Boss>`, `update<Boss>`, `shoot<Weapon>`):

| Stage | Boss (draw/update fn suffix) |
|---|---|
| 0 | `BlizzardBuffalo` |
| 1 | `QueuedOrdersDragoon` |
| 2 | `StormEagle` |
| 3 | `Vile` |
| 4 | `SigmaMMX2` |

Boss AI is a simple timer/state-machine pattern (`actionState`/`chargeState` + `actionTimer`/`chargeTimer` counters that trigger attacks and reset).

### Game state machine

`gameState` is one of `INTRO → PLAYING → VICTORY → END`, driven from `update()`. `loadStage(idx)` resets `player`, `projectiles`, `bossProjectiles`, `particles`, and constructs `currentBoss` from `{ ...stage.boss, x: 650, ...stage.init }` — no per-index branching.

### Main loop

`loop()` calls `update()` then `draw()` via `requestAnimationFrame`. Physics is basic gravity + AABB collision (no libraries). Both `update()` and `draw()` dispatch per-stage boss logic through `STAGES[currentStageIdx].behavior.update()` / `.draw(ctx, currentBoss)` — a single lookup instead of a per-index `if/else` chain. The hit-spark and defeat-explosion colors both read `STAGES[currentStageIdx].behavior.particleColor`.

The `currentStageIdx >= STAGES.length` fallback branches in `update()`/`draw()` (plain sine-bob motion / colored rectangle) are dead code in practice — `loadStage()` always routes to `gameState = 'END'` once `idx >= STAGES.length` — but are kept for defensive symmetry with the original behavior.

### Controls

- Desktop: `KeyA`/`KeyD` (or `ArrowLeft`/`ArrowRight`) move, `KeyJ` (or `ArrowUp`) jump, `KeyW`/`Space` shoot, `Enter` advance (physical key codes, not layout-aware). Arrow keys are normalized to their `KeyA`/`KeyD`/`KeyJ` equivalents in the keydown/keyup listeners rather than duplicated through the rest of the game logic.
- Mobile: on-screen D-pad/buttons (`#mobile-controls`) shown via the `@media (max-width: 850px)` breakpoint; these buttons just set the same `keys[...]` flags read by `update()`.

## Content notes

- Text and comments are a mix of English and Spanish (`lang="es"` on `<html>`).
- Boss designs are original pixel-art code inspired by (not copied from) classic Mega Man X bosses — see the disclaimer in `README.md` before adding new bosses that reference Capcom IP too closely.
