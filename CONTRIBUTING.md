# Contributing

First off, thanks for taking the time to contribute!

This project is a **beginner-friendly Neovim starter config**. Contributions that keep it simple, well-documented, and accessible to newcomers are always welcome.

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before participating.

## How to contribute

### Report a bug

Open a [bug report](https://github.com/Mvzundert/nvim-starter/issues/new?assignees=&labels=&template=bug_report.md).

Include:
- Your Neovim version (`nvim --version | head -1`)
- Operating system
- Steps to reproduce
- What you expected vs what happened

If the error is from a plugin (not the config itself), report it to the plugin author instead.

### Suggest a feature

Open a [feature request](https://github.com/Mvzundert/nvim-starter/issues/new?assignees=&labels=&template=feature_request.md).

Check [existing issues](https://github.com/Mvzundert/nvim-starter/issues) and [discussions](https://github.com/Mvzundert/nvim-starter/discussions) first — someone may have already suggested it.

### Improve documentation

Typos, unclear explanations, or missing docs for common setups are all great fixes. See any `*.md` file in the repo.

### Improve the config

Found a better default? A smarter keybinding? A plugin that's more stable or beginner-friendly than the current one? Open a pull request.

## Development setup

```bash
# Clone the repo
git clone https://github.com/Mvzundert/nvim-starter.git
cd nvim-starter

# Test your changes without touching your real config
nvim -u init.lua somefile.py
```

You can also symlink the file to test day-to-day:

```bash
ln -sf "$(pwd)/init.lua" ~/.config/nvim/init.lua
```

## Pull request guidelines

- **Keep it focused.** One change per PR. A starter config should stay lean.
- **Stay single-file.** The whole point is a single `init.lua` with comments.
- **Stay beginner-friendly.** New features must be clearly commented. Assume the reader has never used Neovim.
- **Minimize plugins.** Every new plugin adds maintenance cost and startup time. Ask yourself: *is this essential for a beginner?* If yes, prefer a stable, well-maintained option.
- **Test your changes.** Run `nvim -u init.lua` and verify the feature works and nothing breaks.
- **Preserve the existing style.** Indentation, comment style, and keybinding conventions should match.

## Commit style

Write commit messages in the imperative mood:

```
Add guess-indent.nvim for auto-indent detection
Fix which-key timeout description
Update LSP server list in docs
```

## First-time contributors

If this is your first PR ever, welcome! Feel free to tag `@Mvzundert` for help. Check issues labelled [good first issue](https://github.com/Mvzundert/nvim-starter/labels/good%20first%20issue) if you're looking for a place to start.

## Need help?

See [SUPPORT.md](SUPPORT.md) or start a [GitHub Discussion](https://github.com/Mvzundert/nvim-starter/discussions).
