# Language Servers (LSP)

## What is LSP?

The Language Server Protocol is what powers go-to-definition, auto-completion,
hover documentation, and red-underlined errors in Neovim. Each programming
language has its own server. You install them once, and Neovim talks to them
automatically.

## How to install a server

1. Open a file of the language you want support for (e.g., `nvim main.py`)
2. Press `<Space>cm` to open **Mason**
3. Press `2` to view language servers, then `/` to search
4. Press `i` on the server you want
5. Press `q` to close Mason and reopen your file

The server attaches automatically when you open a file of that language.

## Recommended servers per language

| Language | Server | Search in Mason |
|---|---|---|
| Python | pyright | `/pyright` |
| Rust | rust-analyzer | `/rust-analyzer` |
| Go | gopls | `/gopls` |
| JavaScript / TypeScript | ts_ls (typescript-language-server) | `/typescript` |
| Lua | lua-language-server | `/lua-language-server` |
| Bash | bash-language-server | `/bash-language-server` |
| Ruby | ruby-lsp | `/ruby-lsp` |
| PHP | intelephense | `/intelephense` |
| C / C++ | clangd | `/clangd` |
| HTML / CSS | vscode-langservers-extracted | `/vscode-lang` |
| JSON | vscode-json-language-server | `/json-language` |
| YAML | yaml-language-server | `/yaml-language` |
| Docker | dockerls | `/dockerls` |
| Markdown | marksman | `/marksman` |

Install as many as you want. Mason handles downloads and updates.

## Verifying an LSP is working

See [Verifying LSP works](verify.md).
