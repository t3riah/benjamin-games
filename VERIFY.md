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
