# Minimal Dotfiles

A lightweight, dependency-free dotfiles setup compatible with **bash** and **zsh**.

No chezmoi, no plugin managers, just simple symlinks.

This is meant as a lighter-weight version of [lmnotran/dotfiles](https://github.com/lmnotran/dotfiles_minimal)

## What's Included

```
shell/
├── profile    # Login shell config (PATH, env vars) - POSIX compatible
├── bashrc     # Bash interactive config
├── zshrc      # Zsh interactive config
└── aliases    # Shared aliases (bash + zsh)
git/
└── gitconfig  # Git configuration
```

## Setup

```bash
git clone https://github.com/lmnotran/dotfiles_minimal.git ~/repos/dotfiles_minimal
cd ~/repos/dotfiles_minimal
./script/bootstrap
```

The bootstrap script:
- Creates symlinks from `~/.bashrc`, `~/.zshrc`, etc. to this repo
- Backs up existing files to `*.backup` if they exist
- Is idempotent (safe to run multiple times)

## Devcontainer Setup

To automatically apply dotfiles when opening any VS Code devcontainer, add to your VS Code `settings.json`:

```json
{
  "dotfiles.repository": "lmnotran/dotfiles_minimal",
  "dotfiles.targetPath": "~/repos/dotfiles_minimal",
  "dotfiles.installCommand": "script/bootstrap"
}
```

## Local Customizations

For machine-specific config that shouldn't be committed:
- `~/.bashrc.local` — sourced at end of `.bashrc`
- `~/.zshrc.local` — sourced at end of `.zshrc`

## Features

- **POSIX-compatible profile** — works with sh, bash, dash, zsh
- **No external dependencies** — no plugin managers or package installs required
- **Git integration** — simple prompt with branch display (zsh), common aliases
- **Auto-detects tools** — uses nvim/vim/vi, eza/ls, Homebrew if available
- **VS Code aware** — uses `code --wait` as editor when running in VS Code terminal
