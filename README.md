<div align="center">

# ✦ dotfiles ✦

*my little corner of the terminal — configs, tweaks, and quiet obsessions.*

![Fedora](https://img.shields.io/badge/Fedora-51A2DA?style=for-the-badge&logo=fedora&logoColor=white)
![Zsh](https://img.shields.io/badge/Zsh-F15A24?style=for-the-badge&logo=gnubash&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-a6e3a1?style=for-the-badge)

</div>

---

## ◈ About

This repo is a collection of my personal *dotfiles*: the configuration files
that make a workspace feel like home. The goals are simple:

- **Reproducible**: set up a new machine by cloning, not starting from scratch.
- **Minimal**: only what I actually use, no bloat.
- **Consistent**: one theme and one vibe across every tool.

## ◈ Setup

| Component | Choice       |
| --------- | ------------ |
| OS        | Fedora Linux (KDE Plasma Edition) |
| Shell     | Zsh          |
| Editor    | VS Code      |
| Desktop   | KDE Plasma, via [caelestia-kde](https://github.com/ladybug-me/caelestia-kde) |

> This table will grow as the repo does (terminal, fonts, theme).

## ◈ Desktop: Fedora KDE

I run the **Fedora KDE Plasma Edition**, and my desktop setup is based on
[ladybug-me/caelestia-kde](https://github.com/ladybug-me/caelestia-kde).
Head over to that repo for the full details and install instructions.

## ◈ Structure

```text
dotfiles/
├── LICENSE
└── README.md
```

The structure will expand as new configs land, e.g. `zsh/`, `git/`, `vscode/`.

## ◈ Installation

```bash
# 1. clone
git clone https://github.com/fhudint/dotfiles.git ~/Projects/dotfiles
cd ~/Projects/dotfiles

# 2. symlink the configs you need (example)
ln -sf ~/Projects/dotfiles/zsh/.zshrc ~/.zshrc
```

> ⚠️ Back up your existing configs before overwriting them with symlinks.

## ◈ Palette

Note the theme colors here, for example:

`#1e1e2e` `#cdd6f4` `#89b4fa` `#a6e3a1` `#f38ba8`

## ◈ License

Released under the license in [LICENSE](LICENSE).

---

<div align="center">

*made with ☕ and too many late nights*

</div>
