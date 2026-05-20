# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `jumpy-cat.html` directly in any modern browser — no build step, server, or dependencies needed.

```powershell
Start-Process "jumpy-cat.html"
```

## Architecture

Everything lives in `jumpy-cat.html` (one file). The script section is structured top-to-bottom:

1. **Canvas setup** — 480×640 canvas, scaled responsively via `canvas.style.width/height`
2. **State machine** — `state` variable: `'start'` → `'playing'` → `'dead'`
3. **`cat` object** — physics (`vy`, `g`, `jf`), hitbox getters (`hLeft/hRight/hTop/hBottom`), `draw(bob)`, `update()`, `reset()`
4. **Pipes** — `pipes[]` array; `makePipe()` spawns every 90 frames; `updatePipes()` moves, scores, and collision-checks; `drawPipes()` renders
5. **`clouds[]` + `drawBg()`** — parallax clouds, gradient sky, ground strip
6. **UI helpers** — `roundRect()`, `drawScore()`, `drawStartScreen()`, `drawGameOver()`
7. **Input handlers** — `keydown` (Space/ArrowUp), `click`, `touchstart` all call `handleInput()`
8. **`loop()`** — `requestAnimationFrame` loop; updates then draws each frame

## Key constants

| Constant | Value | Notes |
|---|---|---|
| `GAP` | 168 | Pipe opening height in px |
| `PW` | 65 | Pipe width |
| `GROUND` | 80 | Ground strip height |
| `pipeSpeed` | 2.8 → 5.5 | Increases +0.25 every 5 points |
| `cat.jf` | -9.2 | Jump force (negative = up) |
| `cat.g` | 0.45 | Gravity applied each frame |

## Hitbox

`cat.hLeft/hRight/hTop/hBottom` are intentionally inset from the drawn sprite to give the player a forgiveness margin. Do not widen them to match the visual bounds.

## Persistence

High score is stored in `localStorage` under key `'jcBest'`.
