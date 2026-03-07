# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

A single-file browser Snake game (`index.html`). No build tools, no dependencies, no package manager.

## Running

Open `index.html` directly in a browser (double-click or `start index.html` on Windows).

## Architecture

Everything lives in `index.html`:

- **Canvas rendering** — 400×400px grid, 20px cells, drawn each tick via `draw()`
- **Game loop** — `setInterval(tick, 150ms)`, started on first arrow key press
- **State** — `snake` (array of `{x,y}`), `dir`/`nextDir` (current/queued direction), `food`, `score`
- **Input** — single `keydown` listener; queues direction in `nextDir` to avoid mid-tick reversals
- **Lifecycle** — `init()` resets state; `start()` begins the interval; `gameOver()` clears it and prompts restart
