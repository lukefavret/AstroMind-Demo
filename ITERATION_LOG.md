# AstroMind-Demo Iteration Log

This log tracks all meaningful iterations, features, and fixes to make case-study writing easy. Add a new entry at the top for each change.

Format (template):
- Date: YYYY-MM-DD
- Title: Short, action-oriented summary
- Description: 1–3 sentences capturing intent, what changed, and why
- Files touched: Backticked list of key files
- Notes (optional): Decisions, tradeoffs, follow-ups

---

## 2025-10-05 — Restore multi-note editor functionality
- Description: Hardened editor instantiation to read note data from the scene store and keep open editors synchronized after scene rebuilds so multiple notes can open concurrently without blank panels.
- Files touched: `index.html`
- Notes: Refreshes per-editor content unless the field is actively being edited.

## 2025-10-05 — Require names before create (shapes & notes)
- Description: Enforced non-empty names when creating shapes and notes to prevent accidental clutter. Prefills sequential defaults ("Shape N" / "Note N"), auto-focuses/selects the name, blocks save on empty, and Cancel discards the new item. Note creation is deferred until Save.
- Files touched: `index.html`
- Notes: Delete is hidden for brand-new shapes until they exist; inline validation styling on name fields.

## 2025-10-05 — Fix delete behaviors
- Description: Made the note editor’s delete button remove only the selected note (with confirmation). Restored object deletion via a new "Delete Object" button in the shape edit panel, with its own confirmation.

## 2025-10-05 — Note editor handles & hover affordance
- Description: Restyled the note editor resize handles into classic right-angle triangles and added hover/focus feedback to the "+ New Note" button for clearer interactivity cues.
- Files touched: `index.html`

## 2025-10-05 — Shape editor button layout + close affordance
- Description: Updated the object edit panel with a top-right close icon, renamed the footer button to “Cancel,” and aligned the trash-can delete button on the left for visual consistency with the note editor.
- Files touched: `index.html`

## 2025-10-05 — Close notes when parent object deleted
- Description: When an object is removed, any open note editor tied to it now closes (or clears state), and pending note openings are cancelled.
- Files touched: `index.html`

## 2025-10-05 — Modal overlay z-index + delete confirm
- Description: Ensured the confirmation modal overlays the shape edit panel and that clicking “Yes, Delete” reliably triggers the fade-out and removal.
- Files touched: `index.html`

## 2025-10-05 — Fix delete behaviors
- Description: Made the note editor’s delete button remove only the selected note (with confirmation). Restored object deletion via a new "Delete Object" button in the shape edit panel, with its own confirmation.
- Files touched: `index.html`
- Notes: Modal message now adapts to note vs object deletion.

## 2025-10-05 — Add PR template with checklist
- Description: Added a PR template enforcing iteration log updates, smoke checks, and preservation of the single-file analog sci-fi aesthetic.
- Files touched: `.github/pull_request_template.md`, `.github/copilot-instructions.md`

## 2025-10-05 — Tab focus: quick, smooth lock-on
- Description: Reworked Tab cycle tween to be timestamp-based with an ease-in/out curve, shortened duration, interruptible cycling, and momentum reset for a snappy yet comfortable focus.
- Files touched: `index.html`
- Notes: Keeps ~10 units standoff; made configurable.

## 2025-10-05 — Add settings system (single-file friendly)
- Description: Introduced an editable JSON settings block plus localStorage overrides and a small runtime API for tweaks. Wired cycle, movement, and other params to settings.
- Files touched: `index.html`
- Notes: API: `AstroMind.settings`, `AstroMind.set(...)`, `AstroMind.resetSettings()`.

## 2025-10-05 — Expand settings coverage
- Description: Exposed controls, CRT post-processing, UI auto-hide, connector toggle, and decal sizing/opacity. Added applySettings for live updates.
- Files touched: `index.html`
- Notes: `retroPass` promoted to global for runtime uniform updates; settings JSON kept comment-free for strict parsing.
