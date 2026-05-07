# dotfiles

Personal configs and global CLI tools that I want available on any machine I work from.

## Layout

```
bazecor/              # Dygma Raise keyboard layer exports (Layer0-2.json)
```

## Install on a new machine

```bash
git clone https://github.com/aaronmeza/dotfiles.git ~/personal/dotfiles
```

Make sure `~/bin` is on `PATH` (`echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc`) when you start adding tools that symlink into it.

## What's here

Currently just keyboard layouts. Personal CLI tools moved to [redwoods/scripts/](https://github.com/aaronmeza/redwoods/tree/main/scripts) - e.g. `bmad-update-all` now lives under `redwoods/scripts/bmad-update-all/`.

## What's NOT here

Secrets. API tokens and per-service credentials live outside the repo (a permissioned `<secrets-dir>/<service>.env` layout). This repo is public.

## Future additions

Common dotfiles inhabitants worth adding when the need shows up:

- **Shell** - `.zshrc`, `.zprofile`, `.aliases`, `.functions`, `.exports`
- **Git** - `.gitconfig` (user.name, signing key, aliases), `.gitignore_global` (`.DS_Store`, `node_modules/`, IDE folders), `.gitattributes`
- **Editor** - VS Code `settings.json` + `keybindings.json`, `.vimrc` / `.config/nvim/`
- **Terminal** - `.config/wezterm/`, `.config/alacritty/`, `.config/starship.toml` (prompt), `.tmux.conf`
- **macOS** - `Brewfile` for `brew bundle install`, a `macos.sh` script that runs `defaults write ...` for personal preferences (Finder, Dock, key repeat rate, screenshot location)
- **Window mgmt** - `.config/aerospace/`, `.config/karabiner/`, `.hammerspoon/`
- **SSH** - `~/.ssh/config` (Host blocks, ProxyJump, IdentityFile paths). Public keys yes, private keys never.
- **Direnv** - `.envrc` templates per project family
- **Version managers** - `.tool-versions` (asdf), default `.nvmrc`
- **Claude Code** - `~/.claude/CLAUDE.md` (global instructions), shared skills, hook scripts. Project-specific stays in each project.

Pick an install strategy when the surface grows: simple `ln -sf` is fine for a handful of files; `stow`, `chezmoi`, or `yadm` are worth it once the layout gets nested or per-machine differences matter.
