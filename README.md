# No 13th Floor Games

Threshold Architecture hub for games.no13thfloor.org. No accounts, no ads,
progress saved on the player's device only.

## The games
- **Monromi's Mazes** (external link to mazes.no13thfloor.org, Threshold Tier I,
  Sacred Geometry): push-block mazes with an entropy countdown. Lives in its
  own repo (t3riah/monroes-mazes); the hub only links to it.
- **The Quantum Conduit** (`quantum.html`, Threshold Tier II, Wave Collapse):
  fire particles through a double slit, toggle the observer detector to
  collapse the wave into particle bands, land hits in the target zone. 60s
  rounds, best score in `quantumConduitBestV1`.
- **Fluid Matrix** (`fluid.html`, Threshold Tier III, Fluid Routing): drag
  sensor nodes onto the wave path before the flow head reaches them. Light
  all five before 60s run out.
- **Benjamin's Battleship** (`battleship.html`, replaced Nov 8, 2026): 8x8
  void-sector radar grid. Four ships (sizes 4, 3, 3, 2 = 12 cells) hidden
  at random; click cells to strike, 12 hits clears the sector. No placement,
  no AI opponent, no difficulty modes (the Nov 3 10x10 placement version was
  replaced by Louie's new file). Tailwind inlined, no CDN.
- **Monroe's Arrows** (`arrows.html`): slide every arrow off the board. 48
  levels (24 classic + 24 Advanced train levels), all open, no timers, no
  lives, no penalties. Hint, Undo, and Restart included.
- **Gabriella's Gumdrops** (`gumdrops.html`, replaced Nov 8, 2026):
  harmonic crystal catcher. Move the basket with arrow keys, mouse, or touch
  to catch falling gumdrops (10/20/50 points). Endless rounds, best score in
  `gumdropsBestV1`. The Nov 3 match-3 version was replaced by Louie's new
  file. Tailwind inlined, no CDN.

The hub also embeds one suggested-viewing video: "You've Seen This Your Whole
Life (Real Fluid Simulation)" by Graph Gazer on YouTube
(youtube-nocookie embed), a real fluid simulation, relevant to Fluid Matrix.

## Theme
Threshold Architecture: void `#020205`, obsidian panels `#0A0A16`, structural
gold `#F59E0B`, neon cyan `#38BDF8`, harmonic violet `#A855F7`. The hub and
the two new games use it. The three original games keep their own pages
untouched. Quantum and Fluid share a tone preference (432Hz / 528Hz) in
`no13thToneV1`. See `BRAND.md` for the brand DNA and `VERIFY.md` for what
was checked.

## Files in this hub
- `index.html` — the hub page
- `quantum.html`, `fluid.html` — the two new games
- `battleship.html`, `gumdrops.html` — replaced Nov 8 with Louie's new
  versions (see above); `arrows.html` unchanged from Nov 3
- `CNAME` — `games.no13thfloor.org`, unchanged
- `README.md` — this file
- `BRAND.md` — brand DNA
- `VERIFY.md` — verification notes

## How to publish
This staging folder is the complete publish set. Replace the live GitHub
Pages source for games.no13thfloor.org with exactly these files:
`index.html`, `quantum.html`, `fluid.html`, `battleship.html`, `arrows.html`,
`gumdrops.html`, `CNAME`, `README.md`, `BRAND.md`, `VERIFY.md`.
Confirm the live CNAME still reads `games.no13thfloor.org`. Open each game
live once and confirm saved progress survived: Arrows level progress should
still be there, since its localStorage key was kept unchanged. Note: the Nov 8
Battleship and Gumdrops replacements do not carry the old games' saves
(Battleship stats key `benjaminBattleshipStatsV1` and Gumdrops match-3
progress are no longer used by the new versions).
