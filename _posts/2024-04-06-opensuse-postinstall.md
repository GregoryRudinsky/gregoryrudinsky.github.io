---
title: openSUSE Tumbleweed
date: 2024-04-06 00:55:00 +0500 # date-time-offset est
categories: [documentation, opensuse]
tags: [setup, zsh, distrohopping, linux]
---
# OpenSUSE Tumbleweed Post Install TODO

> WIP - Trust but verify. 


## Repositories and Updates

Add Community Repositories - Entire `packman` Repository 
- https://en.opensuse.org/Additional_package_repositories
- https://en.opensuse.org/Portal:Tumbleweed

```zsh
zypper ar -cfp 90 http://ftp.gwdg.de/pub/linux/misc/packman/suse/\
openSUSE_Tumbleweed/ packman

zypper dup --from packman --allow-vendor-change
```

   

### Update
```zsh
sudo zypper dup
```

```zsh
sudo zypper ref && sudo zypper update
```

### [Install  - Codecs](https://en.opensuse.org/SDB:Installing_codecs_from_Packman_repositories) `OPI`
```zsh
sudo zypper install opi

sudo zypper in opi && opi codecs
```

### Install `flatpak` `flathub repo` `flatseal`

```zsh
sudo zypper install flatpak

flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

flatpak install flathub com.github.tchx84.Flatseal
```

- OpenSUSE [flatpak](https://flatpak.org/setup/openSUSE) instructions
   

## System Tunables

### Change Host name

```zsh
sudo hostnamectl set-hostname opensuse
```
- Restart Terminal and enter `hostname`

### Disable GRUB Delay
-  Yast → Boot Loader → Bootloader Options → Set timeout to 0 → OK

   

## KDE 

### Change KDE Task Switcher

- System Settings → Window Management → Task Switcher → Select large icons (without selected window) → Apply

### Enable KDE `Dark Mode`
- System Settings → Appearance & Style → Colors & Themes

### Krunner Customization
- To increase size of `krunner`, add the following lines to `~/.config/krunnerrc`. 
	- If data is present, overwrite it.
	- [https://unix.stackexchange.com/questions/638795/change-krunner-size-and-position-in-kde-plasma-5](https://unix.stackexchange.com/questions/638795/change-krunner-size-and-position-in-kde-plasma-5) 

```
[General]
FreeFloating=true
font=Noto Sans,12,-1,5,50,0,0,0,0,0

[PlasmaRunnerManager]
migrated=false
```

   

## `git` `zsh` `OHMYZSH`

### Install `git`

```zsh
sudo zypper install git
```

### Install `zsh`

```zsh
sudo zypper install zsh
```

## Install `OHMYZSH`

```zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### Install Nerd Fonts
  - https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#meslo-nerd-font-patched-for-powerlevel10k
  - Download and install the 4 Nerd Fonts...
  - `Restart/Logout` 

### Theme 
- [Powerlevel10k] (https://github.com/romkatv/powerlevel10k)
  - [Manual Install](https://github.com/romkatv/powerlevel10k?tab=readme-ov-file#manual)	
  - Clone Repo

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

  - Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`
    - Restart Terminal
    - `p10k configure` to manully run config

`OHMYZSH` Docs
- https://github.com/ohmyzsh/ohmyzsh/wiki
- https://github.com/ohmyzsh/ohmyzsh/wiki/Themes


 
## Networkish

### Tailscale
https://tailscale.com/kb/1047/install-opensuse-tumbleweed

To view LAN:
`sudo tailscale up --accept-routes --operator=$USER`

### KTailctl - GUI Tailscale Manager

```zsh
flatpak install flathub org.fkoehler.KTailctl
```
- Flathub 
	- https://flathub.org/apps/org.fkoehler.KTailctl
- Github
	- https://github.com/f-koehler/KTailctl

   

## APPs

```zsh
flatpak install flathub md.obsidian.Obsidian

flatpak install flathub org.videolan.VLC

flatpak install flathub net.mullvad.MullvadBrowser

flatpak install flathub com.bitwarden.desktop

flatpak install flathub md.obsidian.Obsidian

flatpak install flathub com.brave.Browser

flatpak install flathub io.github.shiftey.Desktop
```

Visual Studio Code

- https://code.visualstudio.com/docs/setup/linux#_opensuse-and-slebased-distributions
## Backup .dot files
1. Backup `Konsole` dot files
2. 

---


## Zypper Syntax

```zsh
sudo zypper install package-name
```

```zsh
sudo zypper update
```

```zsh
zypper search package-name
```

```zsh
sudo zypper remove package-name
```

   

### TODO
> create script to install APPs


---

##### References

Things to do after installing OpenSuse
- [https://averagelinuxuser.com/after-installing-opensuse/](https://averagelinuxuser.com/after-installing-opensuse/)

LinuxCast
- [https://youtu.be/KW7hzWehuDo](https://youtu.be/KW7hzWehuDo)

PragmaticLinux
- [https://www.pragmaticlinux.com/2021/06/5-things-to-do-after-installing-opensuse-tumbleweed/](https://www.pragmaticlinux.com/2021/06/5-things-to-do-after-installing-opensuse-tumbleweed/)
