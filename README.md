<h1 align="center">RIVER</h1>

[![River Video](screenshots/river_4.png)](https://youtu.be/MwnK6arB2Rc)

<p align="center">The ultimate River configuration (A Desktop Environment Like Experience)</p>

---

## Overview

[River](https://github.com/riverwm/river) is a dynamic tiling Wayland compositor with flexible runtime configuration.

- **Operating System** : `Archcraft`
- **Window Manager** : `River`
- **Status Bar** : `Waybar`
- **Launcher** : `Rofi` / `Wofi`
- **Session Manager** : `Rofi` / `Wofi`
- **Notifications** : `Mako`
- **Terminal** : `Foot`
- **File Manager** : `Thunar`
- **Text Editor** : `Geany`
- **Web Browser** : `Firefox`

## Installation
- **Get the files from** : [Ko-fi :coffee:](https://ko-fi.com/s/69957c0587) <sup>[**`Why Paid`**](https://github.com/adi1090x/adi1090x/blob/master/WHY.md)</sup>
- Extract The file **river.tar.gz** with : `tar -xzvf river.tar.gz`
- If you are using **`Archcraft`** (`Required: 2023 or later`) as your OS, You can just install the provided package with : `sudo pacman -U archcraft-river-3.0-3-any.pkg.tar.zst`
- If you want to install this setup on _Arch Linux_ or on any _other distro_, follow the points below :
  - Install the following programs on your computer: `river` `lua` `lua-posix` `wlr-randr` `swaybg` `swayidle` `swaylock` `wlroots` `wl-clipboard` `waybar` `wofi` `foot` `mako` `grim` `slurp` `wf-recorder` `light` `yad` `thunar` `geany` `mpv` `mpd` `mpc` `viewnior` `imagemagick` `xfce-polkit` `xorg-xwayland` `xdg-desktop-portal-wlr` `playerctl`
  - After installing programs above, Create river directory in **`~/.config`** : `mkdir -p ~/.config/river`
  - Copy Everything from _dotfiles_ to **`~/.config/river`** : `cp -r ./dotfiles/* ~/.config/river/` 
  - Logout and login to your amazingly configured River WM.

### Appearance

Install the following `theme`, `icon pack`, `cursors` and `fonts` for overall appearance.

- GTK Theme : [Arc-Dark gtk theme](https://github.com/horst3180/arc-theme)
- Icon Theme : [Arc icon theme](https://github.com/horst3180/arc-icon-theme)
- Cursor Theme : [Qogir cursor theme](https://www.gnome-look.org/p/1366182/)
- Fonts : [JetBrainsMono Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/JetBrainsMono.zip), [Iosevka Nerd Font](https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Iosevka.zip), [Icomoon Feather](https://github.com/archcraft-os/archcraft-packages/blob/main/archcraft-fonts/files/icon-fonts/Icomoon-Feather.ttf), [Archcraft](https://github.com/archcraft-os/archcraft-packages/blob/main/archcraft-fonts/files/icon-fonts/archcraft.ttf)

## Config Structure
```
~/.config
└── river             : River config directory
    ├── foot          : Terminal config
    ├── mako          : Notification daemon config
    │   └── icons     : Notification icons
    ├── rofi          : Rofi config files
    ├── scripts       : Various scripts for functionality
    ├── wallpapers    : Wallpapers
    ├── waybar        : Statusbar config
    ├── wofi          : Launcher, Powermenu config
    └── init          : River init file (main config)
```

> By default, **`wofi`** is used as app launcher.
>
> But, If you want to use **rofi** instead of **wofi**, First make sure you install the [wayland fork of rofi](https://github.com/lbonn/rofi). Edit the config file `~/.config/river/init` and uncomment rofi keybindings (and, comment the wofi stuff as well).

> By default, **`MPD`** is used on waybar for music.
>
> But, If you want to use **Spotify** instead of **MPD**, Edit the config file `~/.config/river/waybar/config` and uncomment the spotify module (and, comment the MPD module as well).

## Nvidia
If you're on `Archcraft` and install the provided package, There's nothing else you need to do in order to run it on Nvidia machine. The package's post_installation script does it all, And the compositor should work fine.

If you're running any other distribution and want to install this setup on your Nvidia machine, You need to do some tweaking. In this guide, I'm assuing you're using **Arch Linux**. Follow the steps below to make this wayland compositor work on Nvidia :

- Install **Nvidia Drivers** on your system. [NVIDIA](https://wiki.archlinux.org/title/NVIDIA) 
- Edit `/etc/mkinitcpio.conf` file and add **`nvidia`** kernel modules
```
MODULES="nvidia nvidia_modeset nvidia_uvm nvidia_drm"
```

- In the same file, Remove `kms` hook from hooks array if present.
- Rebuild your initrd file with : `sudo mkinitcpio -P linux`
- Edit `/etc/default/grub` file and add **`nvidia_drm.modeset=1`** kernel parameter for Nvidia
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia_drm.modeset=1 ..."
```

- Update your grub config file with : `sudo grub-mkconfig -o /boot/grub/grub.cfg`
- Reboot your Nvidia Machine and login to your wayland compositor, It should work now.

More Information: [NVIDIA#Installation](https://wiki.archlinux.org/title/NVIDIA#Installation), [NVIDIA#DRM_kernel_mode_setting](https://wiki.archlinux.org/title/NVIDIA#DRM_kernel_mode_setting)

## Keybindings

| Keys | Action |
| --- | --- |
| <kbd>super + Return</kbd> | Open terminal |
| <kbd>super + shift + Return</kbd> | Open floating terminal |
| <kbd>super + alt + Return</kbd> | Open terminal with selected geometry |
| <kbd>super + shift + F</kbd> | Open file manager |
| <kbd>super + shift + E</kbd> | Open text editor |
| <kbd>super + shift + W</kbd> | Open web browser|
| <kbd>super + D</kbd> | Run app launcher |
| <kbd>super + X</kbd> | Run powermenu |
| <kbd>super + N</kbd> | Open network manager |
| <kbd>super + P</kbd> | Run colorpicker |
| <kbd>super + C/Q</kbd> | Kill active window |
| <kbd>ctrl + alt + L</kbd> | Run lockscreen |
| <kbd>ctrl + alt + Space</kbd> | Dismiss all notifications |
| <kbd>ctrl + alt + Delete</kbd> | Exit RiverWM instantly |
| <kbd>super + 1,2..9</kbd> | Change workspace/tag from 1 to 9 |
| <kbd>super + shift + 1,2..9</kbd> | Move active container to repective workspace/tag |
| <kbd>super + Left</kbd> | Change focus to the next view |
| <kbd>super + Right</kbd> | Change focus to the previous view |
| <kbd>super + shift + Left</kbd> | Swap focused view with the next view |
| <kbd>super + shift + Right</kbd> | Swap focused view with the previous view |
| <kbd>super + J</kbd> | Change focus to the next output |
| <kbd>super + K</kbd> | Change focus to the previous output |
| <kbd>super + shift + J</kbd> | Send the focused view to next output |
| <kbd>super + shift + K</kbd> | Send the focused view to previous output |
| <kbd>super + E</kbd> | Bump the focused view to the top of the layout stack |
| <kbd>super + F</kbd> | Toggle fullscreen mode |
| <kbd>super + Space</kbd> | Toggle floating mode |
| <kbd>super + H</kbd> | Decrease the main_factor value of rivertile by 0.02 |
| <kbd>super + L</kbd> | Increase the main_factor value of rivertile by 0.02 |
| <kbd>super + shift + H</kbd> | Increment the main_count value of rivertile |
| <kbd>super + shift + L</kbd> | Decrement the main_count value of rivertile |
| <kbd>ctrl + alt + Left</kbd> | change layout orientation to left |
| <kbd>ctrl + alt + Down</kbd> | change layout orientation to down |
| <kbd>ctrl + alt + Up</kbd> | change layout orientation to up |
| <kbd>ctrl + alt + Right</kbd> | change layout orientation to right |
| <kbd>super + alt + Left</kbd> | move views (floating) to left side |
| <kbd>super + alt + Down</kbd> | move views (floating) towards Down |
| <kbd>super + alt + Up</kbd> | move views (floating) towards Up |
| <kbd>super + alt + Right</kbd> | move views (floating) to right side |
| <kbd>super + ctrl + Left</kbd> | resize views (floating) |
| <kbd>super + ctrl + Down</kbd> | resize views (floating) |
| <kbd>super + ctrl + Up</kbd> | resize views (floating) |
| <kbd>super + ctrl + Right</kbd> | resize views (floating) |
| <kbd>super + ctrl + alt + H</kbd> | snap views to screen edges |
| <kbd>super + ctrl + alt + J</kbd> | snap views to screen edges |
| <kbd>super + ctrl + alt + K</kbd> | snap views to screen edges |
| <kbd>super + ctrl + alt + L</kbd> | snap views to screen edges |

## Screenshots

| Screenshot 1 | Screenshot 2 |
| --- | --- |
|![river](screenshots/river_1.png)|![river](screenshots/river_2.png)|

| Screenshot 3 | Screenshot 4 |
| --- | --- |
|![river](screenshots/river_3.png)|![river](screenshots/river_4.png)|

---

### See Also

| [**`archcraft-sway`**](https://github.com/archcraft-os/archcraft-sway) | [**`archcraft-wayfire`**](https://github.com/archcraft-os/archcraft-wayfire) | [**`archcraft-hyprland`**](https://github.com/archcraft-os/archcraft-hyprland) | [**`archcraft-newm`**](https://github.com/archcraft-os/archcraft-newm) |
| --- | --- | --- | --- |
|[![Sway](https://raw.githubusercontent.com/archcraft-os/archcraft-sway/main/screenshots/sway_4.png)](https://github.com/archcraft-os/archcraft-sway)|[![Wayfire](https://raw.githubusercontent.com/archcraft-os/archcraft-wayfire/main/screenshots/wayfire_4.png)](https://github.com/archcraft-os/archcraft-wayfire)|[![Hyprland](https://raw.githubusercontent.com/archcraft-os/archcraft-hyprland/main/screenshots/dark/hypr_4.png)](https://github.com/archcraft-os/archcraft-hyprland)| [![Newm](https://raw.githubusercontent.com/archcraft-os/archcraft-newm/main/screenshots/solid/newm_5.png)](https://github.com/archcraft-os/archcraft-newm)|
