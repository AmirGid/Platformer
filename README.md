# Demonic Flame

A browser-based HTML5 canvas platformer. Move through a moonlit forest overlooking a city, fight off imps, and manage your life flask as you push east through connected stages.

## Stages

Stages are linked metroidvania style: walk off an edge or drop down a shaft to reach the next area. Imps you've killed stay dead when you return.

```
 Moonlit Ridge = Ember Hollow = Ashen Woods = Cinder Cliffs
                      | shaft                     | shaft
 Smoldering Den = Molten Core /              The Chute
                  Frozen Spire                    | shaft
                                             Obsidian Gate (finish)
```

The route: Ember Hollow, down into the golem's room, beat it, climb the Frozen Spire back up into Ember Hollow, then east through Ashen Woods (needs the double jump) and Cinder Cliffs, down The Chute to the Obsidian Gate.

1. **Moonlit Ridge** (start): solid ground and scattered rock ledges. Exit east to Ember Hollow.
2. **Ember Hollow**: lava pits in the ground (falling in costs one flask hit and sends you back to the stage entrance), a high staircase route and more, faster imps. The last pit is a dark shaft instead of lava: drop into it to reach the Molten Core. Exit east to Ashen Woods.
3. **Molten Core**: a volcanic cavern arena with the **Magma Golem** boss (14 hits). It throws fireballs (swat them with your attack), leaps at you and sends ground shockwaves (jump them), and breathes fire. Below half health it speeds up and throws three fireballs at once. Beating it shatters the golem, flings out its still-pumping **heart** (grab it to grow your flask to 5 hits and fill it up), unlocks the **double jump** (press jump again in mid-air; once the frost settles a card with a looping demo shows how, and stays up until you've tried it) and a wave of frost turns the cavern into ice for good. In fire form you take no damage and touching the golem hurts it.
4. **Frozen Spire**: the frozen cavern becomes the bottom of a tall ice shaft. Climb about 40 ice ledges (you can jump up through them from below) past winged imps that hover over the ledges, fly between them and swoop at you when you get close. Jump up from the glowing summit to climb back out into Ember Hollow. Its west side opens into the Smoldering Den (the east side, E on the map, is not built yet).
5. **Ashen Woods**: grey forest east of Ember Hollow. Its last lava gap is too wide for one jump: you need the golem's double jump to reach Cinder Cliffs.
6. **Cinder Cliffs**: red-lit cliffs with winged imps; the last pit is a shaft down into The Chute.
7. **The Chute**: a narrow, tall shaft. Work your way down the ledges past winged imps; the pit at the bottom drops into the Obsidian Gate. Double-jump up out of the top to go back to Cinder Cliffs.
8. **Obsidian Gate** (finish): the last gauntlet of pits and fast imps. Reach the glowing gate at the far end to win.
9. **Smoldering Den**: an optional side cave west of the golem's room.

Stages are defined in the `STAGES` list in `index.html`; add another entry to add a stage.


## Sound

Background music and the start laugh are recorded files. All other sound effects are synthesized in the browser (Web Audio API), so they need no files: sword swings, imp deaths, getting hurt, lava, jumps and the icy double jump, fire form, stage changes, the golem's roar, fireballs, leap, ground slam, flame breath, stone-crack hits, death and explosion, the heart's splat and distance-based heartbeat, the frost wave, the ability chime, the winged imps' screech, game over and the victory fanfare.

The golem's roar and death can use recorded files instead: set their paths in `SFX_FILES` in `index.html` and they replace the synthesized versions once loaded.

Press **M** or tap the speaker button to mute; the choice is remembered on that device. Sound starts after the first tap or key press (browsers require a user gesture).
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
| `heart_*.png` | The golem's heart: beating, dripping, spinning, landing and bursting frames |
| `flyer_*.png` | Winged imp frames (hover, fly, dive; 4 each), cut from a sprite sheet; all face right |
| `rock.png` | Tiled platform/lava-rock art |
| `flask_0.png`–`flask_4.png` | Life flask HUD, indexed by hits remaining (0 = empty, 4 = full). After the heart, the taller 5-hit flask is built in code from `flask_0` and `flask_4` |
| `torch_0.png`–`torch_5.png` | Imp-kill-count HUD torch, indexed by progressive ignition state (score 0 already shows the first ember) |
| `bgmusic.mp3` | Background music, starts on load |
| `sfx_laugh.mp3` | Evil-laugh sound effect, played on pressing Start |

## Notes

All art assets were extracted and cleaned (background removed, cropped, retina-scaled) from hand-drawn reference sprite sheets.
