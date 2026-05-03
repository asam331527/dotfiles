# Maintenance Guide

## Quick Reference

### Making Changes

Edit config files directly in `~/dotfiles` (they are symlinked to your home directory):

```zsh
cd ~/dotfiles
# edit .zshrc or starship.toml
source ~/.zshrc   # test the change
```

### Committing and Pushing

```zsh
cd ~/dotfiles
git add -A
git commit -m "Describe the change"
git push
```

### New Machine Setup

```zsh
brew install starship
git clone https://github.com/asam331527/dotfiles.git ~/dotfiles
ln -sf ~/dotfiles/.zshrc ~/.zshrc
ln -sf ~/dotfiles/starship.toml ~/.config/starship.toml
source ~/.zshrc
```

Or use the one-liner from README.md.

### Common Commands

| Task | Command |
|---|---|
| Check repo status | `cd ~/dotfiles && git status` |
| View recent commits | `cd ~/dotfiles && git log --oneline` |
| Pull remote changes | `cd ~/dotfiles && git pull` |
| Verify symlinks | `ls -la ~/.zshrc ~/.config/starship.toml` |
| Edit shell config | `cd ~/dotfiles && $EDITOR .zshrc` |
| Edit prompt config | `cd ~/dotfiles && $EDITOR starship.toml` |

### Files Managed by This Repo

| File | Live Location | Purpose |
|---|---|---|
| `.zshrc` | `~/.zshrc` | Shell initialization |
| `starship.toml` | `~/.config/starship.toml` | Prompt configuration |
| `README.md` | — | Setup and quick start documentation |
| `starship-setup.md` | — | Detailed prompt documentation |
| `REMOTE_SETUP.md` | — | Remote hosting guide |

### Never Edit Live Configs Directly

Because `~/.zshrc` and `~/.config/starship.toml` are symlinks, editing them edits the repo files directly. Either edit in `~/dotfiles` or edit the live paths — both update the same file. Always commit after making changes.

### Backup

Before major changes, commit first so you can revert:

```zsh
cd ~/dotfiles
git add -A && git commit -m "Checkpoint before changes"
# make edits...
# if broken: git checkout -- . && source ~/.zshrc
```

## Support

- Starship docs: https://starship.rs/config/
- This repo: https://github.com/asam331527/dotfiles
