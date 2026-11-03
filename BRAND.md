# No 13th Floor Games: Brand DNA

## Hub name
No 13th Floor Games. The hub at games.no13thfloor.org features exactly three games and nothing else.

## Voice
Plain, direct, playful. Short sentences. No pressure, no timers pushed on players, no ads talk, no accounts talk beyond the footer promise. The one exception is normal Battleship play itself: hunting, missing, and sinking ships are part of that game, and that is fine.

## Shared tokens
- Background: cream `#FFF9EC`
- Text: deep ink `#22201A`
- Cards: white `#FFFFFF`, rounded 16px corners, soft shadow
- Minimum touch target: 52px
- Fonts: system fonts only, so pages work offline. No external fonts, scripts, or assets.
- Layout: mobile-first, single column, content centered, no horizontal overflow.

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

## Legal line
Borrow mechanics and feel as closely as helpful, using only original code, art, and synthesized sounds. Do not lift proprietary assets, audio, code, or trademarks from Candy Crush, the Battleship board game brand, or the original Arrows app. Generic mechanics are fine: match-3 swapping, naval grid combat, sliding arrows off a board. Do not name Candy Crush in the games or the hub.
