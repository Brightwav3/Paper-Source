# Changelog

All notable changes to this project are documented here.
The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [1.5.1] - 2026-06-20

### Fixed
- Renamed `screenshot-light-dark.png` back to `screenshot.png` — the community
  theme dashboard couldn't find the file referenced by the listing after the
  earlier rename.
- Dropped `box-decoration-break` / `-webkit-box-decoration-break` from the
  `==highlight==` styling; only partially supported by Obsidian's bundled
  Chromium and flagged by CSS lint.

## [1.5.0] - 2026-06-17

### Added
- **Full callout coverage** — every built-in callout type (`info`, `todo`,
  `tip`, `success`, `question`, `warning`, `failure`, `danger`, `bug`,
  `example`, `abstract`, `important`, and their aliases) now has a
  palette-matched color instead of falling back to the default. Muted in light,
  Monokai-leaning in dark.
- **Journaling plugin styling** for the views used daily in the vault:
  - **Calendar** — its `--color-*` variables mapped to the paper palette;
    "today" in the accent, daily-note dots in the tan accent, palette hover and
    week numbers, rounded day cells.
  - **Dataview** — inline fields rendered as connected paper pills; error boxes
    styled as a danger surface (tables already inherit the header/zebra style).
  - **pretty-properties** — rounded banner image and progress bars (progress
    already follows the accent via `--accent-h/s/l`).
  - **better-word-count** — status-bar count promoted above the faint default.
  - **Omnisearch** — modal matched to the command-palette surface, matches
    highlighted in the accent.
- **Markdown surfaces** — embeds/transclusions get an accent stripe and border;
  images are rounded with centered captions; Mermaid diagrams pulled into the
  palette (nodes, edges, labels).
- **Accessibility & export**:
  - `:focus-visible` accent ring on interactive controls for keyboard
    navigation.
  - `prefers-reduced-motion` support that neutralizes the theme's transitions.
  - A `@media print` stylesheet — white page, hidden app chrome, full measure —
    for clean PDF export.
- Two new Style Settings toggles: **Image shadow** and **Highlight active line**.

## [1.4.0] - 2026-06-16

### Added
- **Style Settings panel** with live controls:
  - **Background tint hue** — a single slider that rotates the entire paper
    palette (backgrounds, text, headings) around the wheel while keeping
    lightness and saturation fixed, so the default green can become pink,
    purple, blue, and so on without losing the vibe. The tan accent is left
    untouched on purpose.
  - Layout & typography: corner radius, body font size, line height, and
    reading line width sliders, plus "Plain bold & italic" and "Left-aligned
    body text" toggles.
  - Per-mode graph colors (node, link, tagged node, unresolved node) for both
    light and dark.

### Changed
- The whole green surface palette is now derived from a single `--cc-base-hue`
  variable via `hsl()` instead of hard-coded hex values, in both light and dark
  modes. Default hue (132) reproduces the original look.
- Style Settings master variables are declared at `body` scope so the plugin's
  overrides always win.

## [1.3.0] - 2026-06-16

### Added
- **Style Settings support** — an "Accent hue" slider that rotates the accent
  color around the wheel while keeping saturation and lightness fixed, so the
  paper vibe is preserved. The whole accent family (backlinks, bold/italic,
  tags, selection, hovers) is now derived from a single `--cc-accent-hue`
  variable via `hsl()`.
- Callout styling aligned to the palette: rounded container, tinted titles,
  italic quote/cite.
- Syntax highlighting for code blocks in both the editor and reading view —
  full Monokai palette in dark mode, a muted paper palette in light mode.
- Properties / frontmatter panel styling.
- `==Highlight==` (mark) styling.
- Canvas: palette-matched node containers, focus accent, labels, and background
  dot pattern.
- Custom checkbox states (`-`, `>`, `<`, `?`, `!`, `*`).
- Table header background and zebra striping.
- Footnotes section and footnote popover styling.
- Search-result match highlighting in the accent color.
- Tooltip styling matched to the paper surface.

## [1.2.0] - 2026-06-14

### Added
- Graph view polish (light mode): slightly darker neutral links and node labels
  that use the normal text color instead of the washed-out default. Includes a
  direct override for the `extended-graph` plugin, which reads its node-label
  color from a probe element rather than `--graph-text`.
- Light-mode chrome contrast pass: darker ribbon icons, tab headers, file-tree
  rows, folder titles, file dots, and clickable icons so the UI reads clearly on
  the pale mint surface.

### Changed
- Synced the theme with the upstream Paper look from the Coding Agent theme,
  from which Paper Source is split out into its own standalone theme.

## [1.0.2] - 2026-06-12

### Fixed
- Removed all `!important` declarations; bold, italic, and the editor cursor are
  now styled via selector specificity and the `--caret-color` variable.
- Replaced the `text-decoration-color` underline on backlinks with a
  `border-bottom`, clearing the "partially supported" CSS lint warning.

### Changed
- Renamed `PaperSourceDark.png` to `screenshot.png` so the theme screenshot
  resolves during submission, and updated the README reference.

## [1.0.1] - 2026-06-12

### Added
- MIT license file.
- Expanded README with a color palette table, full feature list, and detailed
  installation instructions.

### Changed
- Aligned the `manifest.json` author name with the README and license, and set
  `authorUrl`.

## [1.0.0] - 2026-06-11

### Added
- Initial release.
