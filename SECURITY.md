# Security Policy

## Supported Versions

Only the latest commit on `main` is supported. There are no versioned releases.

| Branch | Supported          |
| ------ | ------------------ |
| main   | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security issue — for example, something in the install script
or config that could be exploited — please report it privately.

**Do not open a public issue.** Instead, send details to:

> Open a [private security advisory](https://github.com/Mvzundert/nvim-starter/security/advisories/new)
> on GitHub.

You can expect:
- An initial response within 72 hours
- A status update within 7 days
- Credit in the advisory once resolved (unless you prefer to remain anonymous)

## What counts as a vulnerability?

This is a Neovim configuration repo. Real vulnerabilities are unlikely, but
things worth reporting include:

- **install.sh** — anything that could cause unintended writes, deletions, or
  code execution beyond copying `init.lua` into `~/.config/nvim/`
- **init.lua** — malicious `vim.pack.add()` sources or `vim.cmd` calls that
  execute arbitrary shell commands
- **CI / GitHub Actions** — exposed secrets or exploitable workflows

## What is NOT a vulnerability?

- Plugin bugs — report those to the plugin author (e.g. folke/tokyonight.nvim,
  williamboman/mason.nvim, etc.)
- Missing language servers or LSP issues
- General crashes or misbehavior of Neovim itself

## A note on `curl | bash`

The README suggests `curl -fsSL <url>/install.sh | bash`. If you're
security-conscious, download the script first and inspect it:

```bash
curl -fsSL -o install.sh https://raw.githubusercontent.com/Mvzundert/nvim-starter/main/install.sh
less install.sh   # read it before running
bash install.sh
```
