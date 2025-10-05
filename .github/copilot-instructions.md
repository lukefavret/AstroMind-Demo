# Copilot Instructions for AstroMind-Demo

## Acknowledgement
You must read and follow the guidance in `handover_instructions.md` before making any changes. Confirm this in your first response.

## Project Vision & Aesthetic
- AstroMind is a 3D spatial mind-mapping tool using an "Analog Sci‑Fi" aesthetic (retro‑futuristic, CRT, analog tech vibes).
- The core metaphor is a solar system: ideas are celestial bodies in a 3D space.
- The design is grounded in cognitive psychology (spatial memory, method of loci) and accessibility for neurodivergent users (ADHD, Autism).

## Architecture & Workflow
- Single-file static web app: All code and UI live in `index.html`. Do not split into multiple files.
- 3D engine: Three.js via CDN (no bundler, no external dependencies beyond necessary Three.js example scripts).
- Persistence: All data is stored in browser localStorage. No backend or server code.
- Deployment: Target is GitHub Pages.
- Edit/test: Edit `index.html`, open/reload in a browser to see changes.

## Iteration Log
- All feature additions, fixes, or noteworthy iterations MUST include a new entry in `ITERATION_LOG.md` at the repo root.
- Entry format:
	- Date: YYYY-MM-DD
	- Title: Short, action-oriented summary
	- Description: 1–3 sentences on intent, what changed, and why
	- Files touched: Backticked list of key files
	- Notes (optional): Decisions, tradeoffs, follow-ups
 - Always add new entries to the TOP of the file.

## Pull Requests
- Use the PR template at `.github/pull_request_template.md`.
- Ensure the checklist is completed, including the `ITERATION_LOG.md` entry and local smoke checks.

## Current Key Features (as implemented)
- 3D space scene with procedural star field sky.
- Camera: WASD/QE for movement, mouse-drag for rotation, Tab cycles focus, with simple momentum for smooth motion.
- Post-processing: CRT-style pass (RGB offset, vignette) and scanlines.
- UI: Frosty-glass panels, dark mode, minimal chrome that fits the analog/CRT vibe.
- Objects: Create/edit/delete objects (fade-out on delete) with on-object CSS2D UI showing title and notes list.
- Notes: Multiple notes per object; draggable/resizable main editor panel with CRT "power-off" close animation.
- Spatial linkage: Dynamic screen-space line connecting the open editor to its parent object.
- Sticky-note decals: When notes exist, a subtle sticky-note DecalGeometry is placed on the object and persisted.
- Persistence: All scene state is saved to localStorage and reloaded on startup.

## Planned/Optional Features (not yet implemented in code)
- AI assistance in the note editor (e.g., "Summarize" and "Brainstorm" via Gemini API). Treat this as planned; do not add networked backends. If implemented, it must be optional, keyed via local settings, and keep the single-file constraint.

## Critical Conventions
- Never break the single-file structure. All code must remain inside `index.html`.
- Preserve the Analog Sci‑Fi aesthetic: CRT feel, frosty-glass UI, subtle animations. Visual quality is a requirement, not a nice-to-have.
- Accessibility and spatial cognition first: disable navigation while typing; reduce visual clutter with distance-based UI hiding; keep interactions predictable.
- Minimal, targeted edits: Prefer the smallest diffs; avoid broad refactors unless explicitly requested.
- Comment non-obvious code: Especially spatial UI math, accessibility decisions, or aesthetic rationale.
- No external services/state: Only browser localStorage for persistence; no backend. Any AI calls must be clearly optional and isolated.

## References
- `handover_instructions.md`: Project vision, workflow, and feature list.
- `README.md`: High-level goals and intent.
- `.github/instructions/base.instructions.md`: General coding guidelines.

---
Update this file as the project evolves. Remove or revise sections as new patterns emerge.
