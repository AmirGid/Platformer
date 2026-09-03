# Slime Bash

A browser-based HTML5 canvas platformer. Move through a moonlit forest overlooking a city, fight off imps, and manage your life flask before you reach the flag.

## Running it

No build step — it's a static page. Either:

- Open `index.html` directly in a browser, or
- Serve the folder locally (recommended, avoids any `file://` quirks):

  ```bash
  python3 -m http.server 8000
  ```

  then visit `http://localhost:8000/index.html`.

## Controls

- **Arrow keys / A, D** — move left and right
- **Arrow Up** — jump
- **Space** — attack
- **X** — once you've defeated 6+ imps, ignite into the fire-elemental form
- **R** — restart after game over or a win

## Project structure

```
index.html       game code (HTML/CSS/JS, no build tools needed)
assets/          all sprite sheets and art, referenced by index.html
```

### Assets

| File(s) | Used for |
| --- | --- |
| `background.jpg` | Parallax backdrop |
| `player_*.png` | Base player (shadow-creature) animation states: walk, idle, jump, attack, hurt, death |
| `fire_*.png` | Fire-elemental "ignited" form, same animation states, unlocked at 6+ kills |
| `imp_*.png` | Enemy sprites |
| `rock.png` | Tiled platform/lava-rock art |
| `flask_0.png`–`flask_4.png` | Life flask HUD, indexed by hits remaining (0 = empty, 4 = full) |
| `torch_0.png`–`torch_5.png` | Imp-kill-count HUD torch, indexed by progressive ignition state |

## Notes

All art assets were extracted and cleaned (background removed, cropped, retina-scaled) from hand-drawn reference sprite sheets.
