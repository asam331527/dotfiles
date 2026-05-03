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

```zsh
# Clone the repo
git clone https://github.com/asam331527/dotfiles.git ~/dotfiles

# Install Starship
brew install starship

# Copy configuration files
cp ~/dotfiles/.zshrc ~/
cp ~/dotfiles/starship.toml ~/.config/

# Reload shell
source ~/.zshrc
```

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

After making local changes:

```zsh
cd ~/dotfiles
cp ~/.zshrc . && cp ~/.config/starship.toml .
git add -A
git commit -m "Update config"
git push
```

## Dependencies

- [Starship](https://starship.rs/) (`brew install starship`)
- zsh (default on macOS)

## License

Personal configuration — feel free to use as a starting point for your own dotfiles.
