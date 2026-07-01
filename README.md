# responsive-layout.yazi

Make [Yazi](https://github.com/sxyazi/yazi)'s manager layout **responsive to terminal width**.

- **Wide** (≥ `wide_min` cols): the default 3 panes — parent │ current │ preview.
- **Narrow** (< `wide_min` cols): current (top) and preview (bottom) **stacked
  vertically**, with a horizontal divider between them — no cramped side-by-side
  columns.

Yazi re-runs the layout on every resize, so the switch happens live as you
resize your terminal.

## Installation

```sh
ya pkg add <your-namespace>/responsive-layout
```

Or drop `main.lua` into `~/.config/yazi/plugins/responsive-layout.yazi/`.

## Setup

Add to your `~/.config/yazi/init.lua`:

```lua
require("responsive-layout"):setup {
	wide_min = 90,  -- width (cols) at/above which all 3 panes show; below → vertical stack
	split    = 0.5, -- vertical split: fraction of height given to the top (current) pane
	divider  = "─", -- glyph used for the horizontal divider in stacked mode
}
```

All options are optional; the defaults above are used if omitted.

## Compatibility

- Reads the runtime ratio (`rt.mgr.ratio`) in wide mode, so it stays compatible
  with [`toggle-pane.yazi`](https://github.com/yazi-rs/plugins/tree/main/toggle-pane.yazi)
  (hide/maximize panes still works).
- It overrides `Tab:layout` and `Tab:build`. Other UI plugins that also override
  `Tab` (e.g. [`full-border.yazi`](https://github.com/yazi-rs/plugins/tree/main/full-border.yazi))
  can conflict — whichever `setup()` runs **last** wins, so order your `require(...):setup{}`
  calls accordingly.

## License

MIT. See [LICENSE](LICENSE).
