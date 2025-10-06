# AstroMind-Demo
https://lukefavret.github.io/AstroMind-Demo/
This is a very WIP prototype, and a barebones ReadMe. 
A 3D Mind Mapping tool created due to alleviate difficulties in organizing information which can arise from various neurodivergences like ADHD, or "folks who think b etter in SPACE!"

## Highlights
- Spatial canvas with a procedural star field and soft CRT post‑processing
- Keyboard/mouse flight: WASD/QE to move, drag to look, Tab to cycle focus
- Create/edit/delete objects with on‑object labels (title + notes list)
- Multiple notes open at once as draggable/resizable panels, each with a “power‑off” close animation
- Per‑editor screen‑space connector lines that point back to the source object (toggleable)
- Sticky‑note decals appear on objects that have notes
- Names required on create with helpful defaults (Shape N / Note N); cancellable flow
- Randomized default shape when creating a new object for a playful start
- Everything saved to localStorage and restored on reload

## Quick start
Visit the repo's github pages page to check it out live:
https://lukefavret.github.io/AstroMind-Demo/
or:
1) Open `index.html` in a modern desktop browser.
2) Move around, create a few shapes, and add notes. Everything autosaves locally.

Optional: Deploy to GitHub Pages by serving this repo as a static site — no build step needed.

## Controls at a glance
- Move: W/A/S/D (strafe), Q/E (down/up)
- Look: click+drag
- Focus cycling: Tab jumps to the next object and eases the camera into place
- Interact: click an object’s “+ New Note” or a note title to open editors
- Editors: drag by header; resize with corner handles; close with the round power button

Tip: Navigation pauses while typing, so you won’t drift when you’re in an input field.

## Architecture (single‑file by design)
- One HTML file (`index.html`) contains HTML, CSS, and JS.
- Three.js is loaded via CDN; CSS2DRenderer is used for 2D labels.
- No bundlers, no external services. Ideal for GitHub Pages and quick sharing.
- Persistence: a Map of objectId → ObjectData is stored in `localStorage`.

Data shape (simplified):
- ObjectData: { name, shape, color, position, notes[], decal? }
- Note: { title, content }

## Settings and persistence
- Settings live inside `index.html` as an embedded JSON block and can be overridden via `localStorage`.
- A small runtime API is exposed for tweaks:
	- `AstroMind.settings` (read current)
	- `AstroMind.set(partial)` (persist overrides and apply)
	- `AstroMind.resetSettings()` (clear overrides)
- Examples of adjustable parameters: movement speed/damping, focus easing/duration, post‑processing toggles, connector visibility, decal sizing/opacity, and UI auto‑hide.

Tags: Spatial Computing, Personal Knowledge Management, HCI, Creative Technology, and Accessibility.
