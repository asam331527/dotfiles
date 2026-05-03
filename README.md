# Dotfiles

This repository contains the shell and prompt configuration for a developer-friendly macOS terminal setup.

## What's Included

| File | Purpose |
|---|---|
| `.zshrc` | Shell configuration: Starship prompt, color-coded `ls`, aliases |
| `starship.toml` | Minimal Starship prompt with full directory path and git status |
| `starship-setup.md` | Detailed documentation for the Starship prompt |
| `REMOTE_SETUP.md` | Guide for syncing this repo to a remote server |

## Requirements

- macOS with zsh (default on macOS)
- [Homebrew](https://brew.sh/) installed
- Git

## Installation

### Step 1: Install Starship

```zsh
brew install starship
```

### Step 2: Clone this repository

```zsh
git clone https://github.com/asam331527/dotfiles.git ~/dotfiles
```

### Step 3: Back up existing configs (optional but recommended)

```zsh
mv ~/.zshrc ~/.zshrc.bak.$(date +%Y%m%d) 2>/dev/null
mv ~/.config/starship.toml ~/.config/starship.toml.bak.$(date +%Y%m%d) 2>/dev/null
```

### Step 4: Symlink the configuration files

Using symlinks ensures any edits in `~/dotfiles` are immediately active in your shell.

```zsh
ln -sf ~/dotfiles/.zshrc ~/.zshrc
ln -sf ~/dotfiles/starship.toml ~/.config/starship.toml
```

### Step 5: Reload your shell

```zsh
source ~/.zshrc
```

### Step 6: Verify the installation

Navigate to a directory and check that the full path appears:

```zsh
cd /tmp
# Prompt should show: /tmp ❯
```

Enter a git repository and confirm branch/status display:

```zsh
cd ~/dotfiles
# Prompt should show: ~/dotfiles on  main ❯
```

Test color-coded file listing:

```zsh
ls -la
# Directories should appear in a different color than files
```

### Why symlinks?

- Edit once in `~/dotfiles` and changes are live immediately
- `git diff` shows actual configuration changes
- `git push` syncs everything without extra copy steps

### Quick Install (One-Liner)

If you already have Homebrew and Git installed:

```zsh
brew install starship && \
git clone https://github.com/asam331527/dotfiles.git ~/dotfiles && \
mkdir -p ~/.config && \
ln -sf ~/dotfiles/.zshrc ~/.zshrc && \
ln -sf ~/dotfiles/starship.toml ~/.config/starship.toml && \
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
