# Paper Source v1.5.0 — UX coverage expansion

**Date:** 2026-06-17
**Author:** Šimon Zelenka (Brightwav3)
**Status:** Approved — direction selected by maintainer

## Goal

Close the biggest UX gaps in the theme. The vault is a journal (*denik*) that
relies on Calendar, Dataview, pretty-properties, better-word-count and
Omnisearch every day, yet the theme styles none of them. Markdown coverage is
also incomplete (only 2 of ~13 callout types are colored, embeds/Mermaid/images
are unstyled), and the theme lacks the accessibility and print affordances
expected of a publicly shared Obsidian theme.

This release is **purely additive**: it introduces new `--cc-*` / plugin tokens
and selector blocks. No existing rule is changed, so the current look is
preserved at the default settings.

## Architecture

Everything derives from the existing token system:

- New colors are declared as `--cc-*` tokens (or the plugin's own
  `--color-*` variables) inside the existing `.theme-light` / `.theme-dark`
  blocks, so there is a single source of truth and the hue slider keeps working.
- Radii reuse `--radius-s/m/l`; accents reuse `--cc-coral` / `--cc-accent`;
  text uses `--text-normal/muted/faint`.
- Plugin selectors and CSS variables were verified against the installed
  plugins (calendar reads `--color-*` vars from its `main.js`; dataview,
  omnisearch, pretty-properties from their `styles.css`).

## Scope

### 1. Callouts — full type coverage
Add `--callout-*` RGB triplets (Obsidian's expected format) for every built-in
type currently falling back to the default: `info, todo, tip/hint,
success/check/done, question/help/faq, warning/caution/attention,
failure/fail/missing, danger/error, bug, example, abstract/summary/tldr,
important`. Tuned to the paper palette — muted in light, more saturated
(Monokai-leaning) in dark. Box structure is unchanged; only icon/stripe/title
tint colors are set.

### 2. Journaling plugins
- **Calendar:** map the plugin's own CSS variables
  (`--color-background-heading`, `--color-dot`, `--color-text-today`,
  `--color-text-weeknum`, `--color-arrow`, `--interactive-accent`, …) to the
  paper palette; "today" uses the accent, dots use the graph/accent color,
  hover uses `--background-modifier-hover`, radius from `--radius`.
- **Dataview:** inline fields (`.inline-field-key` / `.inline-field-value`) as
  subtle paper pills; `.dataview.table-view-table` inherits the existing
  zebra/header table styling; `.dataview-error-box` tinted as a danger surface.
- **pretty-properties:** `.banner-image` rounded to `--radius-m`;
  `.metadata-progress` / `.metadata-circle-progress` driven by the accent.
- **better-word-count:** status-bar count promoted from `--text-faint` to
  `--text-muted` for legibility.
- **Omnisearch:** `.omnisearch-modal` matched to the `.prompt` surface;
  `.omnisearch-result-highlight` / `.omnisearch-highlight` in `--cc-coral-soft`.

### 3. Markdown surfaces
- **Embeds / transclusions** (`.markdown-embed`): left accent stripe + subtle
  border so embedded notes are distinguishable from body text.
- **Mermaid:** remap node/edge/label colors to `--text-normal`, `--cc-coral`
  and border tokens so diagrams sit in the palette in both modes.
- **Images:** `border-radius: var(--radius-m)`; centered `figcaption` /
  alt-caption in `--text-faint`.

### 4. Publication quality
- `:focus-visible` — 2px accent outline on interactive elements for keyboard
  navigation / a11y.
- `@media (prefers-reduced-motion: reduce)` — disable transitions/animations.
- `@media print` — white background, black text, hide app chrome (ribbon,
  tabs, status bar), widen the measure for clean PDF export.
- Two new Style Settings toggles: **Image shadow** and **Highlight active
  line**.

## Out of scope
- No new fonts, no structural layout changes, no changes to existing rules.
- No bespoke styling for plugins not installed in the vault.

## Verification
- Brace-balance / syntax sanity check on `theme.css`.
- Manual confirmation in Obsidian (copy to vault) across light + dark, with
  the Calendar, Dataview and pretty-properties views open.

## Release
- Bump `manifest.json` and the README badge to `1.5.0`.
- Add a `## [1.5.0]` section to `CHANGELOG.md`.
- Copy `theme.css` + `manifest.json` into the vault's installed theme folder.
- Commit and push to `github.com/Brightwav3/Paper-Source` as Brightwav3.
