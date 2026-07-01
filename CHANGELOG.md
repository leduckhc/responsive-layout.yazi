# Changelog

All notable changes to this project are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.1] - 2026-07-01

### Added

- Animated demo GIF in the README (wide ⇄ narrow).
- `CONTRIBUTING.md` with dev setup, testing checklist, and gotchas.

### Changed

- README polished: hero demo, feature list, options table, and "how it works".

## [1.0.0] - 2026-07-01

### Added

- Width-aware manager layout that switches on every terminal resize.
- **Wide mode** (`≥ wide_min` columns): the default three panes
  (parent │ current │ preview), honoring Yazi's runtime `rt.mgr.ratio`.
- **Narrow mode** (`< wide_min` columns): `current` and `preview` stacked
  vertically with a configurable horizontal divider between them.
- Configuration via `setup{}`: `wide_min`, `split`, and `divider`.
- Compatibility with [`toggle-pane.yazi`](https://github.com/yazi-rs/plugins/tree/main/toggle-pane.yazi)
  in wide mode (reads the runtime ratio instead of hardcoding it).

[1.0.1]: https://github.com/leduckhc/responsive-layout.yazi/releases/tag/v1.0.1
[1.0.0]: https://github.com/leduckhc/responsive-layout.yazi/releases/tag/v1.0.0
