# No 13th Floor Games: Brand DNA

## Hub name
No 13th Floor Games. The hub at games.no13thfloor.org features the three
original games plus the Threshold tiers: Monromi's Mazes (external link),
The Quantum Conduit, and Fluid Matrix, plus one suggested-viewing video.

## Voice
Plain, direct, playful. Short sentences. No ads talk, no accounts talk
beyond the footer promise. Monroe's Arrows stays a calm puzzle: no timers,
no lives, no penalties. The new Threshold games (Quantum, Fluid) do use a
60-second round timer, which is part of those games, not of the hub.

## Shared tokens (Threshold Architecture, Nov 8, 2026 — supersedes the Nov 2 cream shell for the hub and new games)
- Background: void `#020205`
- Panels: obsidian `#0A0A16`
- Structural gold `#F59E0B`, neon cyan `#38BDF8`, harmonic violet `#A855F7`
- Minimum touch target: 52px
- Fonts: system fonts only, so pages work offline. No external fonts, scripts, or assets on the game pages. The hub page itself links out to Monromi's Mazes and embeds one YouTube-nocookie video; those are the only external URLs on the hub.
- Layout: mobile-first, single column, content centered, no horizontal overflow.

The three original games keep their own pages byte-unchanged, including
their own internal themes. Only the hub shell changed around them.

## Shared top bar
Every game page carries the same top bar: game name on the left, and a "Back to all games" link to `index.html` on the right. The hub page carries the hub name and a one-line welcome, no back link needed.

## Shared button style
- Minimum height 52px, padding 14px 20px
- Rounded corners, bold text
- Filled with the game's accent color, with readable contrast
- Clear visible focus outline for keyboard play

## Shared footer
Every page ends with exactly this line:

> Saved on your device only. No accounts, no ads.

## One accent per game
- Monromi's Mazes: gold `#F59E0B`
- The Quantum Conduit: violet `#A855F7`
- Fluid Matrix: cyan `#38BDF8`
- Benjamin's Battleship: navy `#1E3A5F` (page unchanged; hub button steel blue `#60A5FA` for contrast on void)
- Monroe's Arrows: green `#2E7D32` with gold `#D9A441` highlights
- Gabriella's Gumdrops: pink/candy `#E75480`

## Shared tone preference
Quantum and Fluid share a harmonic tone toggle (432Hz / 528Hz) stored in
`no13thToneV1`. It only changes the pitch of the score blip.

## Shared top bar
Every game page carries the same top bar: hub name "No 13th Floor Games" on the left, and a "Back to all games" link to `index.html` on the right. The hub page carries the hub name and a one-line welcome, no back link needed.

## Shared button style
- Minimum height 52px, padding 14px 20px
- Rounded corners, bold text
- Filled with the game's accent color, with readable contrast
- Clear visible focus outline for keyboard play

## Shared footer
Every page ends with exactly this line:

> Saved on your device only. No accounts, no ads.

## One accent per game
- Benjamin's Battleship: navy `#1E3A5F`
- Monroe's Arrows: green `#2E7D32` with gold `#D9A441` highlights
- Gabriella's Gumdrops: pink/candy `#E75480`

Each game's own theme stays intact. The brand shell (cream background, top bar, button shape, footer) is shared. The board, pieces, colors inside the game, and sound style stay that game's own.

## Saved progress
Keep each game's existing localStorage keys so existing progress survives the rebuild:
- Battleship: `benjaminBattleshipStatsV1`
- Monroe's Arrows: `monroes_arrows_progress_v1`
- Gabriella's Gumdrops: no localStorage key in the staged file; do not invent one that changes behavior.
- The Quantum Conduit: best score `quantumConduitBestV1`
- Fluid Matrix: no progress key; tone preference shared with Quantum in `no13thToneV1`

## Legal line
Borrow mechanics and feel as closely as helpful, using only original code, art, and synthesized sounds. Do not lift proprietary assets, audio, code, or trademarks from Candy Crush, the Battleship board game brand, or the original Arrows app. Generic mechanics are fine: match-3 swapping, naval grid combat, sliding arrows off a board. Do not name Candy Crush in the games or the hub.
