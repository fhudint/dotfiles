<div align="center">

# ✦ dotfiles ✦

*my little corner of the terminal — configs, tweaks, and quiet obsessions.*

![Fedora](https://img.shields.io/badge/Fedora-51A2DA?style=for-the-badge&logo=fedora&logoColor=white)
![Zsh](https://img.shields.io/badge/Zsh-F15A24?style=for-the-badge&logo=gnubash&logoColor=white)
![VS Code](https://img.shields.io/badge/VS_Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white)
![License](https://img.shields.io/badge/License-GPL--3.0-a6e3a1?style=for-the-badge)

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

## ◈ Boot: GRUB (Fedora only)

> 📝 A case study for **Fedora**, the distro I use. The paths, the
> `grub2-mkconfig` command and the stock `10_linux` script are Fedora-specific,
> so don't expect this to work as-is on other distros.

By default GRUB prints `Loading Linux ...` / `Loading initial ramdisk ...` for
every entry and lists every kernel flat. I wanted a clean top-level
**Fedora Linux** entry with the older kernels tucked into a submenu.

- **[boot/10_linux_quiet](boot/10_linux_quiet)**: a wrapper around the stock
  `/etc/grub.d/10_linux` that strips the `echo` lines from its output. The
  original script stays untouched, so package updates can't overwrite my change.

`/etc/default/grub` changes:

```sh
GRUB_DISTRIBUTOR="Fedora Linux"   # top-level entry title + submenu name
# GRUB_DISABLE_SUBMENU=true       # removed, so older kernels go into a submenu
```

Install (run as root, and keep the backups):

```bash
sudo cp /boot/grub2/grub.cfg /boot/grub2/grub.cfg.bak
sudo cp /etc/default/grub /etc/default/grub.bak

sudo install -m 755 boot/10_linux_quiet /etc/grub.d/10_linux_quiet
sudo chmod -x /etc/grub.d/10_linux        # avoid generating entries twice

sudo grub2-mkconfig -o /tmp/grub.cfg.new  # generate to a temp file first
grep -c "Loading" /tmp/grub.cfg.new       # should print 0
sudo cp /tmp/grub.cfg.new /boot/grub2/grub.cfg
```

Rollback: restore `grub.cfg.bak` and run `sudo chmod +x /etc/grub.d/10_linux`.

### Theme: bsol

The GRUB theme is [harishnkr/bsol](https://github.com/harishnkr/bsol), included
as a git submodule at `boot/grub-themes/bsol` (it is GPL-3.0 too, and linking
it keeps its own history and license intact).

```bash
# fetch the submodule (skip if you cloned with --recurse-submodules)
git submodule update --init

# install the theme
sudo mkdir -p /boot/grub2/themes
sudo cp -r boot/grub-themes/bsol/bsol /boot/grub2/themes/bsol
```

Then point GRUB at it in `/etc/default/grub` and regenerate the config as above:

```sh
GRUB_THEME="/boot/grub2/themes/bsol/theme.txt"
```

## ◈ Structure

```text
dotfiles/
├── boot/
│   ├── 10_linux_quiet
│   └── grub-themes/
│       └── bsol/          # git submodule (harishnkr/bsol)
├── LICENSE
└── README.md
```

The structure will expand as new configs land, e.g. `zsh/`, `git/`, `vscode/`.

## ◈ Installation

```bash
# 1. clone
git clone --recurse-submodules https://github.com/fhudint/dotfiles.git ~/Projects/dotfiles
cd ~/Projects/dotfiles

# 2. symlink the configs you need (example)
ln -sf ~/Projects/dotfiles/zsh/.zshrc ~/.zshrc
```

> ⚠️ Back up your existing configs before overwriting them with symlinks.

## ◈ Palette

Note the theme colors here, for example:

`#1e1e2e` `#cdd6f4` `#89b4fa` `#a6e3a1` `#f38ba8`

## ◈ License

Released under the [GNU General Public License v3.0](LICENSE).

---

<div align="center">

*made with ☕ and too many late nights*

</div>
