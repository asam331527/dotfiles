# Dotfiles

This repository contains the shell and prompt configuration for a developer-friendly macOS terminal setup.

## What's Included

| File | Purpose |
|---|---|
| `.zshrc` | Shell configuration: Starship prompt, color-coded `ls`, aliases |
| `starship.toml` | Minimal Starship prompt with full directory path and git status |
| `starship-setup.md` | Detailed documentation for the Starship prompt |
| `REMOTE_SETUP.md` | Guide for syncing this repo to a remote server |

## Quick Start (New Machine)

Use symlinks so edits in the repo are live immediately without manual copying:

```zsh
# 1. Install Starship
brew install starship

# 2. Clone the repo
git clone https://github.com/asam331527/dotfiles.git ~/dotfiles

# 3. Back up existing configs (optional but safe)
mv ~/.zshrc ~/.zshrc.bak.$(date +%Y%m%d) 2>/dev/null
mv ~/.config/starship.toml ~/.config/starship.toml.bak.$(date +%Y%m%d) 2>/dev/null

# 4. Symlink the config files
ln -sf ~/dotfiles/.zshrc ~/.zshrc
ln -sf ~/dotfiles/starship.toml ~/.config/starship.toml

# 5. Reload shell
source ~/.zshrc
```

**Why symlinks?** Edit once in `~/dotfiles` and changes are live. `git diff` shows real changes, and `git push` syncs without extra `cp` steps.

## Prompt Features

- **Full directory path** — never truncated, `~` for home
- **Git branch** — ` main`
- **Git status** — `[!1]`, `[+2]`, `[?3]`, etc.
- **Minimal character** — `❯` (green on success, red on error)

## Aliases

| Alias | Command |
|---|---|
| `ls` | `ls -G` (color-coded) |
| `ll` | `ls -laG` (detailed + color-coded) |

## Git Status Symbols

- `!N` — N modified files
- `+N` — N staged files
- `?N` — N untracked files
- `»N` — N renamed files
- `✘N` — N deleted files
- `$` — Stashed changes
- `⇡N` — N commits ahead
- `⇣N` — N commits behind
- `⇡N⇣M` — Diverged

## Keeping in Sync

With symlinks, edit directly in `~/dotfiles` and commit:

```zsh
cd ~/dotfiles
# edit .zshrc or starship.toml
git diff
git add -A && git commit -m "Update config" && git push
```

## Dependencies

- [Starship](https://starship.rs/) (`brew install starship`)
- zsh (default on macOS)

## License

Personal configuration — feel free to use as a starting point for your own dotfiles.
