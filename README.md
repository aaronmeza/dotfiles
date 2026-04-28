# dotfiles

Personal configs and global CLI tools that I want available on any machine I work from.

## Layout

```
bin/                  # executables symlinked into ~/bin
etc/                  # config files read by tools in bin/
bazecor/              # Dygma Raise keyboard layer exports (Layer0-2.json)
```

## Install on a new machine

```bash
git clone https://github.com/aaronmeza/dotfiles.git ~/personal/dotfiles
mkdir -p ~/bin
ln -sf ~/personal/dotfiles/bin/bmad-update-all ~/bin/bmad-update-all
```

Then make sure `~/bin` is on `PATH` (`echo 'export PATH="$HOME/bin:$PATH"' >> ~/.zshrc`).

## What's here

### `bin/bmad-update-all`

Runs `bmad-method@next` quick-update across every repo under `~/crown`, `~/personal`, `~/confelicity` that has a `_bmad/` directory.

```bash
bmad-update-all              # update in place
bmad-update-all --dry-run    # list installs + versions
bmad-update-all --commit     # update, branch, PR, squash-merge per repo
```

Skip list lives at `etc/bmad-update-all.skip` — one repo path per line, relative to `$HOME`. Override with `BMAD_UPDATE_SKIP_FILE=/path` if needed.

## What's NOT here

Secrets. API tokens and per-service credentials live in `~/.secrets/<service>.env` (perms `700/600`), not in this repo. This repo is public.

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
