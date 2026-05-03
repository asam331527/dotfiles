# Dotfiles Remote Setup Guide

## Current Repository State

The dotfiles repo is at `~/dotfiles` and contains:
- `.zshrc` — shell config with Starship init, color-coded `ls`, aliases
- `starship.toml` — minimal prompt with full directory path and git status
- `starship-setup.md` — documentation

Current branch: `main`
Commits:
- `78122f5` — Add zshrc with color-coded ls and full directory path in prompt
- `1e96e3e` — Add minimal Starship prompt config and documentation

## Prerequisites

Ensure your SSH key is set up with your chosen host:
```zsh
ls ~/.ssh/id_*.pub
# If none exist:
ssh-keygen -t ed25519 -C "your@email.com"
cat ~/.ssh/id_ed25519.pub
# Copy the output and add it to your git host's SSH keys settings
```

## Option 1: GitHub

### Method A: GitHub CLI (gh)
```zsh
brew install gh
gh auth login
gh repo create dotfiles --public --source=. --remote=origin --push
```

### Method B: Manual (web UI)
1. Go to https://github.com/new
2. Name it `dotfiles`
3. Choose Public or Private
4. Do NOT initialize with README (we have one locally)
5. Copy the SSH URL: `git@github.com:YOURNAME/dotfiles.git`
6. In `~/dotfiles`, run:
```zsh
git remote add origin git@github.com:YOURNAME/dotfiles.git
git branch -M main
git push -u origin main
```

## Option 2: GitLab

1. Go to https://gitlab.com/projects/new
2. Create blank project named `dotfiles`
3. Copy SSH URL: `git@gitlab.com:YOURNAME/dotfiles.git`
4. In `~/dotfiles`, run:
```zsh
git remote add origin git@gitlab.com:YOURNAME/dotfiles.git
git branch -M main
git push -u origin main
```

## Option 3: Self-Hosted / Other

Replace with your server details:
```zsh
git remote add origin ssh://user@your-server.com/path/to/repo.git
git branch -M main
git push -u origin main
```

## Verify the Push

```zsh
git remote -v
git log --oneline
```

## Syncing Changes Going Forward

After making local changes:
```zsh
cd ~/dotfiles
cp ~/.zshrc . && cp ~/.config/starship.toml .
git add -A
git commit -m "Describe your change"
git push
```

## Cloning on a New Machine

```zsh
git clone git@github.com:YOURNAME/dotfiles.git ~/dotfiles
cp ~/dotfiles/.zshrc ~/
cp ~/dotfiles/starship.toml ~/.config/
source ~/.zshrc
```
