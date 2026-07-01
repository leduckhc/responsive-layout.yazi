# Contributing to responsive-layout.yazi

Thanks for wanting to make this plugin even better! Whether it's a bug report, feature request, or code contribution, we'd love to hear from you.

## Issues & Bug Reports

Found a problem? Let's squash it. Please open an [issue](https://github.com/leduckhc/responsive-layout.yazi/issues) and include:

- **Your setup**: Yazi version, terminal width when it happens, any other plugins you're using
- **What you expected**: How it should behave
- **What actually happened**: The bug or surprising behavior
- **Steps to reproduce**: The minimal sequence to trigger it

## Feature Requests

Have an idea? Open a [discussion](https://github.com/leduckhc/responsive-layout.yazi/discussions) or [issue](https://github.com/leduckhc/responsive-layout.yazi/issues) labeled `enhancement`.

Some ideas that fit this plugin's scope:
- New divider glyphs or styling modes
- Threshold presets (e.g., "laptop", "ssh", "phone")
- Better integration with other layout-modifying plugins

Ideas that are out of scope:
- Colorization or themeing (let Yazi's theme handle that)
- Keybindings for manual layout switching (that's what `toggle-pane.yazi` does)
- Multi-pane or grid layouts (separate project)

## Code Contributions

### Setup

1. Fork and clone the repo:
   ```sh
   git clone git@github.com:YOUR_USERNAME/responsive-layout.yazi.git
   cd responsive-layout.yazi
   ```

2. Copy `main.lua` to your local Yazi plugins:
   ```sh
   cp main.lua ~/.config/yazi/plugins/responsive-layout.yazi/
   ```

3. Edit `~/.config/yazi/init.lua` to require it locally (for dev):
   ```lua
   require("responsive-layout"):setup { wide_min = 90 }
   ```

4. Restart Yazi (`ya quit && yazi`) or reload with `:reset` in command mode.

### Development Workflow

- **Testing**: Resize your terminal at different widths. Test with `toggle-pane.yazi` installed to ensure ratio mutations are honored.
- **Syntax check**: `luac -p main.lua` (or use your editor's Lua linter).
- **Code style**: Keep it concise; 100 lines is the sweet spot for maintainability.

### Submitting Changes

1. Create a feature branch:
   ```sh
   git checkout -b feature/your-idea
   ```

2. Make your changes. Update `CHANGELOG.md` if it's user-facing.

3. Commit with a clear message:
   ```sh
   git commit -m "feat: add preset thresholds for common terminal sizes"
   ```

4. Push and open a [pull request](https://github.com/leduckhc/responsive-layout.yazi/pulls).

### PR Guidelines

- Keep PRs focused on a single concern (one feature or one bugfix per PR).
- Include a clear description of *why* the change is needed.
- If it changes behavior, update the `README.md` options table or examples.
- All Lua code should be syntactically valid (`luac -p main.lua`).

## License

By contributing, you agree that your code will be licensed under the [MIT License](LICENSE).

## Questions?

- 🐛 Bug or problem? [Open an issue.](https://github.com/leduckhc/responsive-layout.yazi/issues)
- 💡 Idea or discussion? [Start a discussion.](https://github.com/leduckhc/responsive-layout.yazi/discussions)
- 📧 Anything else? Reach out on GitHub.

---

Thank you for making this plugin better! 🪟
