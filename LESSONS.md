# Lessons learned

A running record of what worked and what didn't while building this site, kept per
project, grouped into dated batches, and weighted by how much each lesson cost to learn.
Add a new batch after each stretch of work, and keep the weights honest.

## How lessons are weighed

Every batch gets two scores from 1 to 5. They are my estimates from the session, not
measurements.

- **Complexity (C):** how tangled the request was: ambiguity, how many requirements
  interacted, new design versus a tweak, how often the direction changed.
- **Effort (E):** how much it cost: iterations, rework, research, testing.

**Weight = round(C × E ÷ 5)**, from 1 to 5. A lesson starts with its batch's weight.
Each time the same lesson comes up again in a later batch it gains **+1** (shown as ↻, capped
at 5), because a mistake made twice was worth more to learn than the first time suggested.
Lessons are listed heaviest first.

## Project: Exponents

Static pages with React and Babel from a CDN: `index.html` (exponent field),
`uparrow.html` (Knuth arrows), `numberline.html` (big and small numbers).

### Batches

| Batch | Date (UTC) | PRs | What happened | C | E | Weight |
|---|---|---|---|---|---|---|
| 1 | 2026-10-27, 04:11–05:10 | #1, #2 | Rebuilt the exponent visualiser as an infinitely zoomable canvas, added the up-arrow page, the first TODO, and links between pages. | 5 | 5 | 5 |
| 2 | 2026-10-27, 05:10–10:02 | #3, #4, #5 | Extended the ruler, removed the stepper row, built the first number line, added wiki points once the full list was supplied. | 3 | 3 | 2 |
| 3 | 2026-10-27, 10:19–10:40 | #6, #7 | One page switch for all pages; rebuilt the number line as a guided journey after the first version took many clicks and led nowhere. | 4 | 4 | 3 |
| 4 | 2026-10-27, 10:40–11:11 | #8, #9 | Slowed the early pace, added real-world scale, a to-scale sliding line, and sourced definitions after research. | 5 | 5 | 5 |
| 5 | 2026-10-27, 11:11 onward | #10 | Bottom-right settings, hidden-egg regional names, a small-numbers journey, hidden sources on basic numbers, this file. | 4 | 3 | 2 |

### Lessons, heaviest first

**Weight 5**

- **Check facts before writing them, and compute what can be computed.** (Batch 4 ↻ 5)
  Several things written from memory were wrong or partly right: the googol's date, the
  Milky Way's mass, Kilofaxul's size (10^10^377.5, not 379). A short script caught the last
  one. *Apply:* source first, write second; recompute any number you can.
- **Say what you could not verify.** (Batch 4)
  Page fetches were blocked, so sources came from search results, and some entries (Ballium's
  number, BIG FOOT, Bird's number) exist only on the wiki. The cards say so. *Apply:* mark
  wiki-only or search-only claims on the page itself, and tell the user which settings would
  let you check properly.
- **Test in a real browser, against local copies of the libraries.** (Batch 1 ↻ 5)
  Headless Chromium at desktop and phone width found a settings button off the phone header,
  stacked labels, a menu behind a canvas, and Babel rewriting `**` into `Math.pow`, which
  breaks BigInt. *Apply:* screenshot every change at both widths, and measure rather than
  assert (the Next button's position was measured across cards).
- **Make the animation a timeline of named phases.** (Batch 1)
  Copy, then solidify, then settle (and the reverse going down); ease the camera in log space
  so a 10⁶ change in zoom still looks smooth. Draw only what is visible so 10¹⁵ cells cost
  the same as 8.
- **A scale that squeezes the interesting part needs a second scale.** (Batch 4)
  A pure super-log puts every named number from a million to a centillion in one corner. The
  fix was four scales stitched end to end, a zoom that follows the current card, an
  evenly-spaced option, and honest labels for numbers that can only be placed by order.
- **Keep the control people press repeatedly in a fixed spot.** (Batch 3 ↻ 4, ↻ 5)
  The Next button jumped as card height changed. Fixed-height control row above variable
  content solved it, and held across 79 and then 35 cards.

**Weight 3 to 4**

- **When the purpose changes, rewrite rather than patch.** (Batch 3 ↻ 4, weight 4)
  The first number line stepped through 17 points one at a time. The journey rebuild (a
  next-number link on every card, chapters, skip buttons, autoplay) worked because it started
  from what the page is for.
- **State your reading of an ambiguous request before building.** (Batch 3 ↻ 4, weight 4)
  "The link at the bottom", "toggle in the upper right" and "journey line" each had more than
  one reading. Say which one you chose in a line.
- **Separate content from rendering.** (Batch 3, weight 3)
  One ordered list plus maps for definitions, sources and sizes made 79, and then 123, cards
  manageable, and let a new mode reuse everything.

**Weight 1 to 2**

- **Design modes as views over one list.** (Batch 5, 2)
  The small-numbers mode reuses the whole engine: a number's place on the line comes from its
  reciprocal, and a `buildList` step filters by settings. No forked code.
- **Keep rarely used and playful content behind settings, with sensible defaults.** (Batch 5, 2)
  Regional names (lakh, crore, Japanese) and the small-numbers journey are off by default;
  credits and the wiki footer live in the settings panel, out of the way.
- **Use the text layer of a file before reading its pixels.** (Batch 2, 2)
  A scanned page was unreadable as an image but `pdftotext` read it; a `.webarchive` is a plist
  with the HTML inside. Check what is in a file before asking for a better scan.
- **Consolidate duplicate navigation early.** (Batch 2, 2)
  Three overlapping ways to switch pages were built and two removed. One switch in a fixed
  spot was enough.
- **Computed text beats hand-written text that depends on a neighbour.** (Batch 5, 2)
  "×1,000 from the previous card" went wrong once optional cards could appear between. Jump
  text is now computed from the cards actually shown.

## Cross-project (carry these to other work)

| Lesson | First seen | Seen again | Weight |
|---|---|---|---|
| Verify facts and numbers before writing them; compute what you can. | Batch 4 | Batch 5 (checked the SI prefixes and examples first) | 5 |
| Test in a real browser at desktop and phone width, with the page's libraries available locally. | Batch 1 | Batches 2–5 | 5 |
| Say plainly what you could not check, on the page and to the person. | Batch 4 | Batch 5 | 5 |
| Fixed place for the repeated action; variable content below it. | Batch 3 | Batches 4, 5 | 5 |
| State your reading of an ambiguous request before building it. | Batch 3 | Batch 4 | 4 |
| Rewrite when the purpose changes; patch when it doesn't. | Batch 3 | Batch 4 | 4 |
| One branch per piece of work, from a freshly fetched `main`; never reuse a merged branch. | Batch 2 | Batch 3 | 3 |
| Keep model names out of commit messages and PRs. Batch 1's first PRs broke this. | Batch 1 | Batches 2–5 (followed) | 3 |
| Merge notifications after a merge are only confirmations. No action needed. | Batch 2 | Batches 3–5 | 1 |

## Adding to this file

1. Add a row to the project's batch table: dates, PRs, what happened, C, E, and the weight
   from the formula above.
2. Add each new lesson under the right weight, with the batch number and a one-line
   *Apply:* where it helps.
3. If a lesson from an earlier batch came up again, add ↻ and raise its weight by one (max 5).
4. Move a lesson to the cross-project table once it has shown up in two batches or two projects.
