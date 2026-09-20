# Blind

A wine blind-tasting deduction trainer. One self-contained `index.html` —
inline CSS, vanilla JS, no build step, no dependencies, no network calls.
Open it from `file://` and it works offline. Data lives in `localStorage`.

## The loop

1. Work through a CMS-style deductive grid: **Sight → Nose → Palate → Conclusion**.
   Every field is skippable, and a skipped field contributes exactly zero to
   scoring — no penalty, no bonus.
2. Commit **your own call** (grape + region + vintage range) from a browsable
   picker. The app's deduction is never shown on this screen.
3. The app then reveals its ranked top five, with the specific observations
   that pushed each candidate up, the ones that argue against it, and the one
   thing to check next time to separate #1 from #2.
4. Enter the bottle to score the session. Everything is logged to History.

## Sections

- **Taste** — the deductive grid and reveal.
- **Codex** — one page per grape, with regional expressions as tabs inside the
  grape (Chablis and Meursault live under Chardonnay, not as separate entries),
  hue swatches, labelled range bars, ageing notes, benchmark producers, and a
  Pitfalls panel of the wines it gets mistaken for. Plus a cross-cutting
  pitfalls page for the traps that aren't varietal at all.
- **History** — session log, accuracy trend, accuracy by grape, your most
  confused pairs, JSON export/import.
- **Practice** — the reverse drill: the app describes a wine, you name it.
  Weighted toward grapes you have historically missed. Includes a flashcard
  sub-mode showing only the diagnostic tells.

## Editing the wine data

`WINE_DB` sits near the top of the script, in clearly banner-commented blocks
(reds, then whites). Each entry is one grape with a `regions[]` array; regions
inherit the grape profile and override what differs. The shape is documented in
the comment above the first entry. `validateDB()` (Settings → "Run data
self-check", or the browser console on load) checks every marker id, hue, veto
expression, range and pitfall cross-reference.
