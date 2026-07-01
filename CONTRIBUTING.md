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
4. Open yazi and resize your terminal to test both wide and narrow modes.

## Testing

- **Wide mode** (≥ 90 cols): parent + current + preview side by side
- **Narrow mode** (< 90 cols): current (top) + preview (bottom) stacked vertically
- Verify the divider renders correctly (horizontal line between panes)
- Test with `toggle-pane` plugin: `T` to hide/show preview, `Ctrl-t` to maximize

## Gotchas

- The plugin reads `rt.mgr.ratio` at layout time, so it respects runtime changes from `toggle-pane`
- Custom components need `_id` field or Yazi silently skips them
- Use `ui.Bar` and `ui.Line` carefully — test both redraw and error logs (`~/.local/state/yazi/yazi.log`)

## Code style

- Lua 5.4+ (Yazi's embedded runtime)
- Comment complex logic
- Keep component classes simple and stateless where possible

## Reporting issues

Include:
- Terminal width / height
- Yazi version (`yazi --version`)
- Exact steps to reproduce
- Screenshot or GIF if relevant
