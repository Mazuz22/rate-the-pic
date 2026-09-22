# Rate the Pic

A single-elimination knockout for a year of photos, dressed as Windows 98.

Two photos at a time. Pick the one you like more; the other is out. 32 photos go in
over 31 matches and five rounds, and one comes out as Pic of the Year.

**Play it:** https://mazuz22.github.io/rate-the-pic/

## What's in here

Everything is one file. No build step, no dependencies, no framework — `index.html`
plus a folder of photos. The only external request is Anton from Google Fonts.

### The WordArt gallery

Titles are generated as SVG, not images. The engine composes:

- **14 gallery styles** — twelve gradient fills plus a horizontal rainbow and an
  outline-only face
- **9 text shapes** — arch up, arch down, wave, slant up, slant down, triangle,
  chevron, dome, plain
- **4 effects** — stacked 3D extrusion thrown down-and-left, a hard offset shadow,
  a soft grey ghost, and outline-only
- **Lean and stretch** — forward skew and vertical scaling, pivoted on the baseline,
  which is most of what made real WordArt look like WordArt

Every round of the tournament wears a different style, reshuffled on each run.

Boxes are measured, not guessed: letters on a curve are rotated, so the renderer lays
the art out, reads its bounding box and fits the `viewBox` to it. That is what stops
tall glyphs on a steep arc from being clipped.

### Layout

Built for a phone first. The match view never scrolls — the title and progress bar take
what they need and the two photos split whatever is left, so both are always on screen
at once. Photos keep their own aspect ratio and are letterboxed rather than cropped.

Progress is kept in IndexedDB, so a half-finished bracket survives a reload.
`prefers-reduced-motion` turns off every animation, including the SVG shimmer.
