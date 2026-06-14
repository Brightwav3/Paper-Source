# Changelog

All notable changes to this project are documented here.
The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

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
