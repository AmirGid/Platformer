# Demonic Flame

A browser-based HTML5 canvas platformer. Move through a moonlit forest overlooking a city, fight off imps, and manage your life flask as you push east through connected stages.

## Stages

Stages are linked metroidvania style: walk off an edge or drop down a shaft to reach the next area. Imps you've killed stay dead when you return.

1. **Moonlit Ridge**: solid ground and scattered rock ledges. Exit east to Ember Hollow.
2. **Ember Hollow**: lava pits in the ground (falling in costs one flask hit and sends you back to the stage entrance), a high staircase route and more, faster imps. The last pit is a dark shaft instead of lava: drop into it to reach the Molten Core.
3. **Molten Core**: a volcanic cavern arena with the **Magma Golem** boss (14 hits). It throws fireballs (swat them with your attack), leaps at you and sends ground shockwaves (jump them), and breathes a short flame cone. Below half health it speeds up and throws three fireballs at once. Beating it shatters the golem, unlocks the **double jump** (press jump again in mid-air) and a wave of frost turns the cavern into ice. In fire form you take no damage and touching the golem hurts it.
4. **Frozen Spire**: the frozen cavern becomes the bottom of a tall ice shaft. Climb about 40 ice ledges (you can jump up through them from below) past winged imps that hover over the ledges, fly between them and swoop at you when you get close (they wind up first: that's your cue to swing). Reach the glowing summit ledge to win.

Stages are defined in the `STAGES` list in `index.html`; add another entry to add a stage.

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
- **X** — once you've defeated 4+ imps, ignite into the fire-elemental form for 15 seconds (moves much faster, and simply touching an enemy kills it instantly with no damage taken). When the timer runs out you revert to normal and the imp counter resets to 0.
- **R** — restart after game over or a win
- **Phones / tablets** — on-screen buttons appear automatically on touch screens

## Project structure

```
index.html       game code (HTML/CSS/JS, no build tools needed)
assets/          all sprite sheets, art, and audio referenced by index.html
```

### Assets

| File(s) | Used for |
| --- | --- |
| `background.jpg` | Parallax backdrop |
| `player_*.png` | Base player (shadow-creature) animation states: walk, idle, jump, attack, hurt, death |
| `fire_*.png` | Fire-elemental "ignited" form, same animation states, unlocked at 4+ kills |
| `imp_*.png` | Enemy sprites |
| `boss_*.png` | Magma Golem boss poses (walk, idle, roar, throw, jump, hover, slam, breath, smoke, plus the 4-frame death sequence die0–die3), cut from sprite sheets; all face right |
| `stage3_background.jpg` | Molten Core cavern backdrop |
| `stage4_background.jpg` | Frozen Spire ice-cave backdrop (tall, scrolls as you climb) |
| `ice_platform.png` | Ice ledge art for the Frozen Spire |
| `flyer_*.png` | Winged imp frames (hover, fly, dive; 4 each), cut from a sprite sheet; all face right |
| `rock.png` | Tiled platform/lava-rock art |
| `flask_0.png`–`flask_4.png` | Life flask HUD, indexed by hits remaining (0 = empty, 4 = full) |
| `torch_0.png`–`torch_5.png` | Imp-kill-count HUD torch, indexed by progressive ignition state (score 0 already shows the first ember) |
| `bgmusic.mp3` | Background music, starts on load |
| `sfx_laugh.mp3` | Evil-laugh sound effect, played on pressing Start |

## Notes

All art assets were extracted and cleaned (background removed, cropped, retina-scaled) from hand-drawn reference sprite sheets.
