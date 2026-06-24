# Starter Neovim Config

A single-file, beginner-friendly Neovim setup with 8 plugins, sensible defaults,
and a curated set of keybindings to get productive quickly.

**What this gives you:**

| You get | Provided by |
|---|---|
| Dark colorscheme (tokyonight moon) | tokyonight.nvim |
| Keymap cheat sheet — press `<Space>` and wait | which-key.nvim |
| Fuzzy file finder, text search, terminal | snacks.nvim |
| Language server installer (GUI) | mason.nvim |
| Go-to-definition, hover docs, rename, diagnostics | nvim-lspconfig |
| Auto-completion while you type | blink.cmp |
| Git change markers in the gutter | gitsigns.nvim |

Everything is in one file. Read it, understand it, then tweak it.

---

## Prerequisites

- **Neovim >= 0.11** — required for the built-in `vim.pack.add()` plugin manager
- **Git** — needed to clone plugins on first launch
- **Nerd Font** (optional) — makes icons in which-key and gitsigns look right.
  [Download a Nerd Font](https://www.nerdfonts.com/) if you see missing glyphs.

Check your versions:

```bash
nvim --version | head -1
git --version
```

---

## Installation

### Option A: One-command install

```bash
curl -fsSL https://raw.githubusercontent.com/Mvzundert/nvim-starter/main/install.sh | bash
```

This backs up your existing `~/.config/nvim/init.lua` and copies the starter config into place.

### Option B: Manual

```bash
mkdir -p ~/.config/nvim
cp starter/init.lua ~/.config/nvim/init.lua
```

If you already have an `init.lua`, back it up first:

```bash
cp ~/.config/nvim/init.lua ~/.config/nvim/init.lua.bak
```

### Option C: Try without installing

```bash
nvim -u starter/init.lua somefile.py
```

Your real config stays untouched. Useful for testing before committing.

---

## First launch

Open Neovim on any file:

```bash
nvim hello.py
```

**What happens:**

1. **Plugins auto-install.** You'll see git clone output for ~30 seconds. This
   happens once. On subsequent launches Neovim starts instantly.
2. **tokyonight colorscheme applies.** Dark background, syntax highlighting.
3. **which-key is active.** Tap `<Space>` and wait half a second — a menu of
   available keybindings appears.

If plugins fail to install, check that `git` is available and you have a working
internet connection.

---

## Installing language servers

Language servers (LSPs) power go-to-definition, auto-completion, hover docs, and
diagnostics. They must be installed separately — one per language.

### Step-by-step

1. Open a file of the language you want support for (e.g. `nvim main.py`)
2. Press `<Space>cm` to open **Mason**
3. In the Mason window:
   - Press `2` to view language servers
   - Use `/` to search (e.g. `/pyright` for Python)
   - Press `i` on the server you want to install
4. Press `q` to close Mason
5. Reopen your file — the LSP attaches automatically

### Recommended servers per language

| Language | Server | Install in Mason |
|---|---|---|
| Python | pyright | `/pyright` → `i` |
| Rust | rust-analyzer | `/rust-analyzer` → `i` |
| Go | gopls | `/gopls` → `i` |
| JavaScript / TypeScript | ts_ls (typescript-language-server) | `/typescript` → `i` |
| Lua | lua-language-server | `/lua-language-server` → `i` |
| Bash | bash-language-server | `/bash-language-server` → `i` |
| Ruby | ruby-lsp | `/ruby-lsp` → `i` |
| PHP | intelephense | `/intelephense` → `i` |

You can install as many as you want. Mason handles the downloads.

---

## Verifying it works

Open a Python file (or any language you installed a server for):

```bash
nvim test.py
```

Run these checks:

| Check | How | What you should see |
|---|---|---|
| LSP is attached | `:LspInfo` | Server listed as attached |
| Completion works | Type `import os` then `os.` | Popup with os functions |
| Go-to-definition | Place cursor on a function call, press `gd` | Jumps to the definition |
| Hover docs | Place cursor on a symbol, press `K` | Floating documentation window |
| Diagnostics | Make a syntax error, wait 1 second | Red underline and gutter marker |

If `:LspInfo` shows "no client attached," make sure you installed the server in
Mason and restarted Neovim on the file.

---

## Keybindings

### Core (always active)

| Keys | Action |
|---|---|
| `jk` | Exit Insert mode (no reaching for `Esc`) |
| `<Space>` | Hold, then wait for which-key to show all keybindings |

### Fuzzy finder (`<Space> s...`)

| Keys | Action |
|---|---|
| `<Space>sf` | Search files by name |
| `<Space>sg` | Search files by content (grep) |

### Buffers (`<Space> b...`)

| Keys | Action |
|---|---|
| `<Space>bb` | Browse open buffers |

### File

| Keys | Action |
|---|---|
| `<Space>w` | Save current file |
| `<Space>q` | Close current buffer |

### Tools (`<Space> c...` / `<Space> t...`)

| Keys | Action |
|---|---|
| `<Space>cm` | Open Mason (install LSP servers) |
| `<Space>tt` | Toggle terminal |

### LSP (active when a language server is attached)

| Keys | Action |
|---|---|
| `gd` | Go to definition |
| `gr` | Find references |
| `K` | Hover documentation |
| `[d` / `]d` | Previous / next diagnostic |
| `<Space>rn` | Rename symbol |
| `<Space>ca` | Code actions (quick-fix menu) |

### Vim built-ins (always available)

| Keys | Action |
|---|---|
| `:q` | Quit |
| `:q!` | Force quit (discard changes) |
| `:w` | Save |
| `:wq` | Save and quit |
| `u` | Undo |
| `Ctrl-r` | Redo |

---

## Customizing

### Change the colorscheme

Set `vim.cmd.colorscheme('tokyonight')` near line 34 to any colorscheme. You can
also change the tokyonight variant:

```lua
-- Add this before colorscheme on line 34:
require('tokyonight').setup({ style = 'storm' })  -- or 'night', 'day', 'moon'
```

### Change indent size

On lines 44-45, change `2` to your preferred width:

```lua
vim.opt.shiftwidth = 4
vim.opt.tabstop = 4
```

### Add more LSP keybindings

Edit section 7 (line 97). Example — add a key to show type definition:

```lua
map('<leader>gt', vim.lsp.buf.type_definition, 'Goto Type Definition')
```

### Add plugins

Append to the `vim.pack.add()` list on line 21. Example — add a file tree:

```lua
{ src = 'https://github.com/nvim-tree/nvim-tree.lua', name = 'nvim-tree.lua' },
```

Then configure the plugin in a new section at the bottom of the file.

---

## Troubleshooting

### Plugins fail to install (git errors)

Check that `git` is installed and on your `PATH`:

```bash
git --version
```

If you're behind a corporate proxy, set `git config --global http.proxy http://proxy:port`.

### Clipboard doesn't sync with system

`unnamedplus` requires a clipboard provider. Install one:

- **Linux (X11):** `sudo apt install xclip` (or `xsel`)
- **Linux (Wayland):** `sudo apt install wl-clipboard`
- **macOS:** `pbcopy` is built-in. Should work out of the box.

### `jk` doesn't escape Insert mode

The timeout might be too fast. Try slowing your typing — press `j` then `k`
within 300ms. If it still fails, check that you haven't remapped `j` or `k`
elsewhere in your config.

### No syntax highlighting

Make sure `vim.opt.termguicolors = true` is set (line 42) and your terminal
supports 24-bit color (most modern terminals do).

### Error: "vim.pack.add is nil" or plugins don't load

You're running Neovim < 0.11. Update to the latest version, or use the AppImage:

```bash
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim.appimage
chmod +x nvim.appimage
./nvim.appimage
```

---

## Uninstalling

```bash
rm ~/.config/nvim/init.lua
```

If you had a backup, restore it:

```bash
cp ~/.config/nvim/init.lua.bak.XXXXXXXXXX ~/.config/nvim/init.lua
```

Plugins are cached in `~/.local/share/nvim/site/pack/`. Remove them if you want
a completely clean slate:

```bash
rm -rf ~/.local/share/nvim/site/pack/
```

---

## Next steps

1. **`vimtutor`** — 30-minute interactive tutorial (run `vimtutor` in your
   terminal, or `:Tutor` inside Neovim)
2. **`:help`** — the built-in manual (try `:help quickref` for a one-page
   cheatsheet)
3. **Read the config** — `starter/init.lua` is 179 lines, all commented. The
   best way to learn is to read and tweak it.
4. **Practice** — install a vim mode in your browser (Vimium, Tridactyl) to
   build muscle memory everywhere.
