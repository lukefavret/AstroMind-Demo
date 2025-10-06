# AstroMind Demo

AstroMind is a spatial “idea-verse” prototype that maps projects as celestial systems. Planets hold primary topics, moons and satellites break work into increasingly fine details, and shimmering trade routes highlight cross-cutting links. Everything is rendered in a retro analog-sci-fi aesthetic with CRT post-processing, a starfield skybox, and ambient synth hums.

## Highlights
- **Recursive solar hierarchy** – Create, edit, and delete Planets → Moons → Satellites with orbiting motion and automatic parent/child wiring.
- **Constellation relationships** – Draw persistent relationship lines between any two objects to represent lateral associations.
- **Analog sci-fi presentation** – Momentum flight controls, easing focus jumps, CRT scanlines, chromatic aberration, ambient hum, and retro UI flourishes.
- **Tethered editing panels** – Selecting an object opens a floating, distance-sensitive panel anchored to that body for renaming, describing, coloring, spawning children, and managing relationships.
- **Local-first persistence** – All entities and links are serialized to `localStorage` (with automatic migration from the legacy planet + notes format). Reloading restores the whole solar system instantly.

## Quick start
1. Clone or download the repo.
2. Open `index.html` in a modern desktop browser (Chrome, Edge, Firefox, or Safari).
3. Explore with the controls below, spawn new celestial ideas, and watch everything auto-save locally.

GitHub Pages friendly: the demo works as-is when the repo is served statically.

## Controls
- **Flight:** `W/A/S/D` strafing, `Q/E` vertical thrust, hold the left mouse button to steer (pointer lock with momentum-based damping).
- **Focus:** `Tab` cycles through all planets with a smooth dolly and reorientation.
- **Select:** Click any planet, moon, or satellite to focus it and open its panel.
- **Create:** Use `+ New Planet` or the `+ Moon / + Satellite` buttons inside the panel.
- **Relationships:** From a panel, choose “Link Object”, select a target, and optionally name the connection. Remove links from the panel list.

Tips:
- Panels fade when you drift too far; fly back or Tab-focus to refresh them.
- Hold `Shift` while flying to engage a speed boost.

## Data model & persistence
The scene is stored under the key `astroMind-scene-data` with the following structure:

```json
{
  "version": 2,
  "entities": {
    "<id>": {
      "id": "uuid",
      "type": "planet" | "moon" | "satellite",
      "name": "string",
      "description": "string",
      "color": "#rrggbb" | "hsl()",
      "size": number,
      "parentId": "uuid | null",
      "orbitRadius": number,
      "orbitSpeed": number,
      "orbitPhase": number,
      "position": { "x": number, "y": number, "z": number },
      "createdAt": epochMillis
    }
  },
  "relationships": {
    "<relationshipId>": { "id": "uuid", "from": "uuid", "to": "uuid", "label": "string", "color": "#rrggbb" }
  }
}
```

Legacy saves that contained planets with note lists are migrated automatically into a planet → “Legacy Notes” moon → satellite stack.

## Architecture notes
- The entire experience lives in `index.html` (HTML + CSS + JS) with CDN-hosted Three.js extras (`EffectComposer`, `FilmPass`, `RGBShiftShader`, `CSS2DRenderer`).
- Scene management is handled by modular classes inside the module script (`DataStore`, `SceneManager`, `PanelManager`, etc.) for clarity while staying bundle-free.
- Visual polish includes a shader-based skybox, procedural star points, CRT overlay, film grain, and chromatic aberration.
- Audio feedback uses the Web Audio API (no external assets) to synthesize hums, whooshes, and fades.

## Contributing
This is a prototype aimed at rapid experimentation. Keep changes self-contained inside `index.html`, prefer modular helper classes/functions, and document new subsystems with inline comments so future contributors can navigate the single-file architecture quickly.

