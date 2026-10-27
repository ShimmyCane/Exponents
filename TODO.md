# TODO

The site's purpose: help people *feel* large numbers. It started with binary,
then exponents (`index.html`), then Knuth up-arrows (`uparrow.html`). Each new
page should take the visitor one size further, so that someone coming back in
10 years still finds something that makes them say "wow".

New pages hang off the exponent page's **⚙ settings → Explore bigger** menu.

---

## 1. Big-number line (`numberline.html`): built, ideas for next

Built as a guided journey up the Googology Wiki's list (72 numbers, 7 chapters, from One to Hollom's
number): a next-number link on every card, chapter jumps, a draggable line, autoplay and deep links
(`numberline.html#googol`). The spec below is the original plan, kept for reference.

- [ ] Add more entries per chapter (the wiki list is far longer; see its "More..." sections).
- [ ] A real counting stretch at the start (count to 100, then by hundreds).
- [ ] Show the numbers' relative size visually (digit counts, then tower heights).

### Original plan

**Inspiration:** a YouTube video about big numbers that starts at the googol and
the googolplex and keeps going. _(add link here)_

### The idea

One horizontal line you keep scrolling to the right, forever. Where a normal
number line has a fixed scale, this one **changes its scale as you travel**:
each time the numbers get too big for the current scale, it hands off to a
coarser one. A small badge in the corner always says which scale you are on.

### Zones (scrolling left → right)

| # | Zone | Step between ticks | Notation shown | Scale |
|---|------|--------------------|----------------|-------|
| 1 | Counting | 1, 2, 3 … 100 | plain digits | linear |
| 2 | Hundreds | 100, 200 … 1,000 | plain digits | linear |
| 3 | Thousands | 1,000, 2,000 … 10,000 → by ×10 to 1,000,000 | plain digits with commas | switch to ×10 per tick (log) |
| 4 | The -illions | million → billion → trillion → … → decillion (×1,000 per tick) | name **and** digits (1,000,000,000) | log, one tick per name |
| 5 | Scientific notation | 10³³ … 10¹⁰⁰ | names start fading, `1 × 10³⁶` takes over around 10²¹–10³³ | log |
| 6 | Googol | 10¹⁰⁰ | big landmark card | log |
| 7 | Exponent of exponents | 10¹⁰⁰ → 10^(10¹⁰⁰) | now ticks are **digit counts**: "a number with 1,000 digits", "a number with a googol digits" | log-log |
| 8 | Googolplex and beyond | 10^10^100, googolplexian 10^10^10^100 | power towers | super-log (each tick = one more "10^", same ruler as `uparrow.html`) |
| 9 | Up-arrow land | 10↑↑10, 3↑↑↑3, … | Knuth arrows | count of arrows / tower height |
| 10 | Graham's number | g₁ = 3↑↑↑↑3, g₂ = 3↑^(g₁)3 … g₆₄ | layered arrows | "layers" |
| 11 | Beyond notation | TREE(3), SSCG(3), Busy Beaver, Rayo's number | descriptions, no digits | qualitative: "faster-growing function" |

Design notes:
- When the scale changes, briefly show the old ticks squeezing together
  (like the exponent page's "solidify" step), then the new tick labels fade in.
- Keep a small "you are here" readout: current number, its name if it has
  one, and how many digits it has.
- Landmark cards pop up on the line for real-world quantities (see the list below).
- Keyboard: → scrolls, Shift + → jumps to the next zone.
- Mobile: horizontal swipe; zones snap.
- Link landmarks to the other pages (e.g. 2⁴⁰ → exponent field, 3↑↑4 → up-arrow page).

### Numbers to put on the line

**Named numbers (short scale)**

| Name | Value |
|------|-------|
| hundred | 10² |
| thousand | 10³ |
| million | 10⁶ |
| billion | 10⁹ |
| trillion | 10¹² |
| quadrillion | 10¹⁵ |
| quintillion | 10¹⁸ |
| sextillion | 10²¹ |
| septillion | 10²⁴ |
| octillion | 10²⁷ |
| nonillion | 10³⁰ |
| decillion | 10³³ |
| undecillion … vigintillion | 10³⁶ … 10⁶³ |
| googol | 10¹⁰⁰ |
| centillion | 10³⁰³ |
| millinillion | 10³⁰⁰³ |
| googolplex | 10^(10¹⁰⁰) |
| googolplexian | 10^(10^(10¹⁰⁰)) |

**Real-world landmarks (approximate)**

| What | Roughly |
|------|---------|
| People on Earth | 8 × 10⁹ |
| Grains of sand on Earth's beaches | 7.5 × 10¹⁸ |
| Stars in the observable universe | 10²² – 10²⁴ |
| Avogadro's number (atoms in 12 g of carbon) | 6.022 × 10²³ |
| Atoms in a human body | 7 × 10²⁷ |
| Legal chess positions | ~4.8 × 10⁴⁴ |
| Atoms in the Earth | 1.3 × 10⁵⁰ |
| Eddington number (protons in the universe) | 1.57 × 10⁷⁹ |
| Atoms in the observable universe | ~10⁸⁰ |
| Shannon number (possible chess games) | ~10¹²⁰ |
| Planck volumes in the observable universe | ~10¹⁸⁵ |
| Largest known prime (2024): 2¹³⁶²⁷⁹⁸⁴¹ − 1 | 41,024,320 digits |

**Huge mathematical numbers**

| Name | Size / definition |
|------|-------------------|
| Skewes' number | ≈ e^e^e^79 ≈ 10^10^10^34 |
| Poincaré recurrence time (Page) | ≈ 10^10^10^10^10^1.1 years |
| 3↑↑4 | 10^3,638,334,640,024 |
| Moser's number | Steinhaus–Moser polygon notation |
| Graham's number | g₆₄ |
| TREE(3) | far beyond Graham's number |
| SSCG(3) | beyond TREE(3) |
| Busy Beaver BB(n) | BB(5) = 47,176,870 (proved 2024); BB(6) > 10↑↑15 |
| Loader's number | from a program for the calculus of constructions |
| Rayo's number | the biggest number nameable in a googol symbols of set theory |

---

## 2. Up-arrow page (`uparrow.html`) follow-ups

- [ ] Graham's number walkthrough: g₁ = 3↑↑↑↑3, then "the number of arrows is g₁" … g₆₄.
- [ ] Last digits of power towers: they stabilise (3↑↑n ends in …4,195,387 for big n),
      computable with repeated Euler-totient reduction. Very "wow", and they are real digits.
- [ ] Four arrows (hexation) with the same "beyond" handling.
- [ ] Animate the evaluation "collapse": fold the tower from the top, one level at a time.
- [ ] Conway chained arrows as a teaser for Graham's number.

## 3. Exponent page (`index.html`) ideas

- [ ] Negative exponents: divide below 1 by splitting the seed cell into fractions.
- [ ] Fractional exponents (√b as a half-step), with a continuous slider.
- [ ] "Compare" mode: two bases side by side on the same zoomable field.
- [ ] Share button (the URL already holds `?base=&exp=`).
- [ ] Link back to the binary page once it's on this site.
