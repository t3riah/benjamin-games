# Verification: No 13th Floor Games rebuild (staging only)

Date: Nov 2-3, 2026. Nothing was pushed to GitHub and the live site was not changed. Live `~/workspace/games-site/` files still carry their Nov 1 timestamps.

## What was checked
- All four HTML files parse cleanly (Python HTML parser).
- Extracted JS from battleship.html, arrows.html, and gumdrops.html passes `node --check`. index.html has no script block.
- Hub links: index.html links only to battleship.html, arrows.html, and gumdrops.html. Each game page links back only to index.html (plus an empty `data:,` favicon in Battleship and Gumdrops, which is not a page link).
- No mentions of Buttons, Simon, Minesweeper, Arcade, or Candy Crush anywhere in staging HTML, after one fix: a Battleship code comment that said "same recipe as Buttons" was reworded to "Sound (tiny WebAudio)" and JS re-checked.
- No external URLs in any staging HTML file: system fonts only, no external fonts, scripts, assets, or audio files.
- Shared shell present on all pages: cream `#FFF9EC`, ink `#22201A`, 16px cards, shared top bar with "Back to all games" on game pages, footer "Saved on your device only. No accounts, no ads."
- Saved-progress keys unchanged: Battleship `benjaminBattleshipStatsV1`, Arrows `monroes_arrows_progress_v1`.
- CNAME unchanged: `games.no13thfloor.org`.

## Battleship
- New Smart engine (`aiSmartPick`): probability-density scoring over every legal placement consistent with hits/misses, checkerboard parity in hunt mode, line continuation in target mode, only unshot squares scored, so no repeated shots.
- Simulation (worker, using the extracted AI functions): single centre hit, all 30 Smart picks adjacent; two hits in a line (44, 45), all 100 picks were the line extensions 43 and 46; 200 full games with no repeated shot in any game; Smart averaged 45.0 shots to sink the fleet vs 95.7 for random.
- Easy stays random, Normal stays simpler hunt/target. Placement, Confirm fire, sonar, stats/badges, and rules unchanged. Hit/miss pulse shortened 0.55s to 0.35s with distinct hit/sunk vs miss rings.

## Monroe's Arrows
- Level data byte-identical before/after (SHA-256): classic `cbcedd9ee7190eab5ddd9ac36d5713b69b250f755864b19e7be1710109c0d26c`, Advanced `b605cbd28c8f4d4ed819150e1c516990ec94189e3ff6ad216c01575718609079`. 24 classic + 24 Advanced = 48 levels, no reorder or renumber.
- Kid rules kept: no timers, lives, penalties, or locks; all 48 levels open; Hint/Undo/Restart behavior untouched.
- Feel only: 0.45s eased slides (was flat 0.25s), original Web Audio tones with a mute toggle, stronger blocked-path red highlight, board tiles fill their cells.

## Gabriella's Gumdrops
- Shell only. Diff against pre-edit copy showed changes limited to shell CSS/markup, button/chip sizing, and three code comments reworded away from "Candy Crush". Match, cascade, special, scoring, and level code unchanged. 5 levels and specials intact, including 195ms swaps and per-distance falls.

## Unresolved / honest limits
- No live browser render was done, so mobile overflow is established from CSS structure (max-width containers, flex-wrap, board at 100% width), not a device screenshot. A visual phone check at publish time is still worthwhile.
- Grid/board cells themselves are exempt from the 52px rule by geometry: a 10x10 Battleship grid and a 7-8 wide Arrows board cannot use 52px cells on a 360px phone without sideways scrolling. All buttons and controls meet 52px.
- Arrows mute setting is memory-only and resets on reload; no second localStorage key was added, to avoid changing the progress schema. Persistent mute is an easy follow-up if wanted.
- Arrows sounds and Battleship/Gumdrops feel were code-verified, not aurally or visually play-tested in a live browser.

---

# Verification: Threshold update (Nov 8, 2026)

## What was checked
- All six HTML files parse cleanly (Python HTML parser). Extracted JS from
  quantum.html and fluid.html passes `node --check`. The three original game
  files are byte-unchanged from the Nov 3 live versions (sizes verified
  against the repo tree before pushing).
- Hub links: index.html links to quantum.html, fluid.html, battleship.html,
  arrows.html, gumdrops.html, and out to https://mazes.no13thfloor.org/.
  Each new game page links back only to index.html.
- No external URLs in quantum.html or fluid.html (no CDN, no fonts, no
  assets). Hub external URLs are only the Monromi link and the
  YouTube-nocookie embed of the Graph Gazer fluid-simulation Short.
- Monromi's Mazes was NOT replaced: the Gemini "Upgraded Game 1" code is a
  skeleton (a gold dot and a timer), far less than the live game at
  mazes.no13thfloor.org, so the hub links to the live game instead.
- The video was identified before embedding: "You've Seen This Your Whole
  Life (Real Fluid Simulation) #shorts" by Graph Gazer. It is a fluid-sim
  Short, not an overview of all three games' physics; the hub labels it
  honestly as a real fluid simulation.

## Quantum Conduit playtest (headless, local)
- Start overlay, 60s countdown, particles emitted and travelled to the
  right wall in both modes. Detector toggle switched arcs to bands, and
  Space toggled it too. Score rose on target hits (10 in wave mode after
  6s, 90 after 9s collapsed, 150 at the end). End overlay showed score
  and best; best score 150 was stored in localStorage.
  Tone toggle switched 432Hz to 528Hz and stored the choice.

## Fluid Matrix playtest (headless, local)
- Fixed wave path per round with a travelling flow head. Nodes dragged
  onto the path lit when the head passed; off-path nodes stayed dark
  (verified: a node left off-path did not light on its own). All five lit
  ends the round with "Flow stabilized"; timeout ends it with the lit
  count. Flow rate HUD tracked lit nodes.

## Honest limits
- Playtests were headless with scripted input, not a human on a phone.
  Touch dragging on a real phone still wants Louie's check.
- The two new games were built from Gemini's skeleton code, extended into
  playable 60-second rounds; the detector timing and node dragging are new
  mechanics, not Gemini's verbatim code.

## Nov 8, 2026: new Battleship + Gumdrops, mobile pass (headless, local)
- Battleship replaced with Louie's new 8x8 click-to-strike version (4 ships,
  12 cells). Verified at 390px: 64 cells render, no horizontal overflow,
  clicking all cells wins (Hits 12/12, "Sector Cleared!", no alert dialog),
  Re-Calibrate resets to Targeting Phase 0/12. Tailwind inlined, no CDN.
  Grid cells 34px on phones (geometry-bound, same exemption as the old
  board), 48px on desktop. Victory alert() removed; further clicks after a
  win are ignored. Old 10x10 placement version and its stats key are gone.
- Gumdrops replaced with Louie's new catcher version (basket + falling
  drops). Verified at 390px: canvas 324px wide, no overflow; a forced catch
  scored +10 and best score persisted in `gumdropsBestV1`; tap moves the
  basket. Tailwind inlined, no CDN. Canvas scales down on narrow phones.
  Old match-3 version and its progress are gone.
- Quantum: particle radius 3.5 to 4.5, target zone 34 to 40px tall for phone
  visibility. Re-verified: scores after 12s (20, then 120 on re-run).
- Fluid: node radius 15 to 17, grab tolerance 26 to 30px. Re-verified: node
  dragged onto the path lit (flow 20%); off-path node stayed dark.
- Hub, Arrows, Battleship (old), Gumdrops (old) mobile sweep at 390px
  before the replacements: no overflow anywhere; header buttons on the
  games were already 44px+ except Monromi's (fixed in its own repo).
