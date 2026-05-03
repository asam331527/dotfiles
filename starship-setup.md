# Starship Prompt Configuration

## Overview
This document describes the Starship prompt setup for macOS (zsh), including current directory display, git status, and a minimal prompt character.

## Installation

```zsh
brew install starship
```

## Shell Integration

Add to `~/.zshrc`:

```zsh
eval "$(starship init zsh)"
```

## Configuration File Location

```
~/.config/starship.toml
```

## Full Configuration

```toml
format = "$directory$git_branch$git_status$character"

[directory]
truncation_length = 3
home_symbol = "~"
style = "bold cyan"

[git_branch]
style = "bold yellow"

[git_status]
style = "bold red"
conflicted = "!"
ahead = "⇡${count}"
behind = "⇣${count}"
diverged = "⇡${ahead_count}⇣${behind_count}"
untracked = "?${count}"
stashed = "$"
modified = "!${count}"
staged = "+${count}"
renamed = "»${count}"
deleted = "✘${count}"

[character]
success_symbol = "[❯](bold green)"
error_symbol = "[❯](bold red)"
```

## Module Reference

| Module | Shows | When |
|---|---|---|
| `$directory` | Current path (truncated to last 3 segments, `~` for home) | Always |
| `$git_branch` | ` main` | Inside a git repository |
| `$git_status` | `[!1]`, `[+2]`, `[?3]`, etc. | When repo has uncommitted changes |
| `$character` | `❯` (green on success, red on error) | Always |

## Git Status Symbols

- `!N` — N modified files
- `+N` — N staged files
- `?N` — N untracked files
- `»N` — N renamed files
- `✘N` — N deleted files
- `$` — Stashed changes
- `⇡N` — N commits ahead of remote
- `⇣N` — N commits behind remote
- `⇡N⇣M` — Diverged (N ahead, M behind)

## Reloading Configuration

After editing `~/.config/starship.toml`:

```zsh
source ~/.zshrc
```

Or open a new terminal window/tab.

## Backup Instructions

### Manual Backup
```zsh
# Create a dated backup
cp ~/.config/starship.toml ~/.config/starship.toml.bak.$(date +%Y%m%d)

# Or copy to a backup directory
mkdir -p ~/backups/starship
cp ~/.config/starship.toml ~/backups/starship/starship.toml.$(date +%Y%m%d_%H%M%S)
```

### Restore from Backup
```zsh
cp ~/backups/starship/starship.toml.YYYYMMDD_HHMMSS ~/.config/starship.toml
source ~/.zshrc
```

### Version Control (Recommended)
Track your dotfiles in a Git repository:
```zsh
git init ~/dotfiles
cp ~/.config/starship.toml ~/dotfiles/
cd ~/dotfiles
git add starship.toml
git commit -m "Backup starship config"
```

### Symlink for Easy Sync
```zsh
# Store the canonical version in your dotfiles repo
ln -sf ~/dotfiles/starship.toml ~/.config/starship.toml
```

## Related Files

- `~/.zshrc` — Shell initialization (contains `eval "$(starship init zsh)"`)
- `~/.config/starship.toml` — Main Starship configuration

## Official Documentation

https://starship.rs/config/
