# Contributing

Thanks for your interest in **responsive-layout.yazi**! Contributions of all
sizes are welcome — bug reports, ideas, docs, and code.

## Getting started

1. **Fork & clone** this repo.
2. Symlink your working copy into Yazi's plugins dir so you can iterate live:
   ```sh
   ln -s "$(pwd)" ~/.config/yazi/plugins/responsive-layout.yazi
   ```
   (Move any existing install aside first.)
3. Enable it in `~/.config/yazi/init.lua`:
   ```lua
   require("responsive-layout"):setup { wide_min = 90 }
   ```
4. Launch `yazi` and resize your terminal across the `wide_min` threshold to see
   the layout switch.

## Development notes

- The whole plugin is a single `main.lua` that overrides `Tab:layout()` and
  `Tab:build()`. Keep it dependency-free and small.
- Custom UI components **must** carry an `_id` field, or Yazi silently fails to
  redraw the region (renders blank). Mirror the shape of the built-in `Rail` /
  `Marker` components: `_id`, `new`, `reflow`, `redraw`, and no-op `click` /
  `scroll` / `touch` / `drag`.
- In wide mode, read the layout from `rt.mgr.ratio` (support both the array form
  `{a,b,c}` and the struct form `.parent/.current/.preview`) so
  [`toggle-pane.yazi`](https://github.com/yazi-rs/plugins/tree/main/toggle-pane.yazi)
  stays compatible.
- For vertical splits, compute `ui.Rect` values directly — `Constraint.Fill`
  has produced blank panes in testing.

## Testing your change

There's no unit-test harness for a TUI layout plugin, so verify manually:

1. `luacheck main.lua` or at least `luac -p main.lua` for syntax.
2. Run `yazi` at a **wide** width (≥ `wide_min`): confirm 3 panes render.
3. Run at a **narrow** width (< `wide_min`): confirm current + preview stack with
   a divider and no stray vertical rail.
4. In wide mode, confirm `toggle-pane` (if installed) still hides/maximizes panes.
5. Check `~/.local/state/yazi/yazi.log` (run with `YAZI_LOG=debug yazi`) — there
   should be **no** redraw errors.

## Pull requests

- Keep PRs focused; one change per PR.
- Update `README.md` and `CHANGELOG.md` when behavior or options change.
- Describe how you tested (widths, terminal, Yazi version).

## Reporting bugs

Open an issue with:

- Yazi version (`yazi --version`) and OS/terminal.
- Your `setup { ... }` options.
- What you saw vs. what you expected (a screenshot helps).
- Any relevant lines from `~/.local/state/yazi/yazi.log`.

## License

By contributing, you agree that your contributions are licensed under the
[MIT License](LICENSE).
