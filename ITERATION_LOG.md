# AstroMind-Demo Iteration Log

This log tracks all meaningful iterations, features, and fixes to make case-study writing easy. Add a new entry at the top for each change.

Format (template):
- Date: YYYY-MM-DD
- Title: Short, action-oriented summary
- Description: 1–3 sentences capturing intent, what changed, and why
- Files touched: Backticked list of key files
- Notes (optional): Decisions, tradeoffs, follow-ups

---

## 2025-10-05 — Add name prompt for creating shapes and notes
- Description: Implemented a modal prompt that requires users to enter a name before creating new shapes or notes. The prompt pre-fills with auto-numbered default names (Shape 1, Shape 2, Note 1, Note 2) that users can accept immediately or customize. Users can also cancel to abort creation, preventing accidental workspace clutter.
- Files touched: `index.html`
- Notes: Modal input supports Enter key for quick confirmation, auto-focuses and selects default text for easy editing. The naming system intelligently calculates the next available number by scanning existing shapes/notes. Accessibility preserved: typing in the modal disables camera navigation.

## 2025-10-05 — Fix delete behaviors
- Description: Made the note editor’s delete button remove only the selected note (with confirmation). Restored object deletion via a new "Delete Object" button in the shape edit panel, with its own confirmation.
- Files touched: `index.html`
- Notes: Modal message now adapts to note vs object deletion.

## 2025-10-05 — Modal overlay z-index + delete confirm

## 2025-10-05 — Close notes when parent object deleted
- Description: When an object is removed, any open note editor tied to it now closes (or clears state), and pending note openings are cancelled.
- Files touched: `index.html`

## 2025-10-05 — Add PR template with checklist

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
