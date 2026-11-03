# No 13th Floor Games

A three-game hub for games.no13thfloor.org. Nothing else. No accounts, no ads, progress saved on the player's device only.

## The three games
- **Benjamin's Battleship** (`battleship.html`): 10x10 naval grid combat. Place five ships, fire with Confirm, use two sonar pings per battle. Easy is random, Normal is simpler hunt/target, Smart is a probability-density hunt/target engine.
- **Monroe's Arrows** (`arrows.html`): slide every arrow off the board. 48 levels (24 classic + 24 Advanced train levels), all open, no timers, no lives, no penalties. Hint, Undo, and Restart included.
- **Gabriella's Gumdrops** (`gumdrops.html`): match-3 swapping across 5 levels, with striped gumdrops and sugar bombs.

See `BRAND.md` for the shared brand DNA (cream background, system fonts only, shared top bar, button style, and footer) and `VERIFY.md` for what was checked in this rebuild.

## Files in this hub
- `index.html` — the hub page, linking only to the three games
- `battleship.html`
- `arrows.html`
- `gumdrops.html`
- `CNAME` — `games.no13thfloor.org`, unchanged
- `README.md` — this file
- `BRAND.md` — brand DNA
- `VERIFY.md` — verification notes

## How to publish
This staging folder is the complete publish set. Do not publish anything else from the old hub.

1. Review the three games and the hub in staging first, ideally on a phone.
2. Replace the live GitHub Pages source for games.no13thfloor.org with exactly these files: `index.html`, `battleship.html`, `arrows.html`, `gumdrops.html`, `CNAME`, `README.md`, `BRAND.md`, `VERIFY.md`.
3. Confirm the live CNAME still reads `games.no13thfloor.org` and that the old games (Buttons, Simon, Minesweeper, Arcade, and any others) are no longer present or linked.
4. Open each game live once and confirm saved progress survived: Battleship stats and Arrows level progress should still be there, since their localStorage keys were kept unchanged.

Publishing is a separate step from this staging rebuild. Nothing in staging has been pushed or made live by building it.
