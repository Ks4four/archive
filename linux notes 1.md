# Linux Notes

> **Note**: These notes now serve only as a memento, with no practical purpose.

## Basic Setup

```sh
mkdir ~/src
mkdir ~/appimages
```

---

## Uninstall XFCE Components and Configure i3

Remove XFCE and install dependencies for a lightweight i3 setup.

```
sudo apt purge --autoremove thunar thunar*xfce4* xfconf xfdesktop4 xfwm4 mugshot
sudo apt install lxappearance feh dunst gnome-keyring policykit-1-gnome picom xclip
```

More details: [https://hrishikeshpathak.com/blog/install-and-configure-i3-window-manager-from-scratch/](https://hrishikeshpathak.com/blog/install-and-configure-i3-window-manager-from-scratch/)

---

## Terminal: Alacritty

Install and compile Alacritty from source.

```
sudo apt install cmake pkg-config libfreetype6-dev libfontconfig1-dev libxcb-xfixes0-dev libxkbcommon-dev python3
git clone https://github.com/alacritty/alacritty.git
cd alacritty
cargo build --release
sudo mv target/release/alacritty /opt
sudo ln -s /opt/alacritty /usr/local/bin/alacritty
```

---

## Web Browser: Floorp

### Linux Mint Installation

Download and extract Floorp.

```sh

tar xjf ./floorp-xx.xx.0.linux-x86_64.tar.bz2
sudo mv /home/ksfour/Downloads/floorp /opt
sudo ln -s /opt/floorp/floorp /usr/local/bin/floorp

```

### Desktop Integration

Create a desktop entry for Floorp.

```sh
nvim ~/.local/share/applications/floorp.desktop
```

```xml
[Desktop Entry]
Version=1.0
Name=Floorp
Comment=Browse the web
Exec=/path/to/floorp/bin %u
Icon=/path/to/floorp/icon.png
Terminal=false
Type=Application
Categories=Network;WebBrowser;
```

---

## Web Browser: Chromium

### Linux Mint Installation

```sh
sudo apt install chromium
```

---

## Desktop Environment

Switch to Regolith and install relevant packages.

`sudo apt install regolith-i3-control-center-gnome`

---

## Applications

### AppImageLauncher

Download from GitHub: [https://github.com/TheAssassin/AppImageLauncher](https://github.com/TheAssassin/AppImageLauncher)

### ANGRYsearch

Download from GitHub: [https://github.com/DoTheEvo/ANGRYsearch](https://github.com/DoTheEvo/ANGRYsearch)

---

## Personal Information Management (PIM)

### Obsidian

Use AppImage for both Linux Mint and Fedora: [https://obsidian.md/download](https://obsidian.md/download)

### Anki

Install from Anki's website: [https://apps.ankiweb.net/](https://apps.ankiweb.net/)

- **Linux Mint:** Install `mpv` to support audio playback.

- `sudo apt install mpv`
- **Fedora:** Install `zstd` to handle the tarball extraction.

- `sudo dnf install zstd`

#### Anki Plugins

```text
31746032 571150035 759844606 1771074083 1898790263 1928346827 2055492159
```

- Plugin `1431333984`: Changes the interface font if needed.

### Super Productivity

Download link: [https://super-productivity.com/download/](https://super-productivity.com/download/)

---

## Text Editors

### Neovim

<https://github.com/neovim/neovim/blob/master/INSTALL.md>

```sh
tar xzf ./nvim-linux64.tar.gz
sudo mv ./nvim-linux64 /opt
sudo ln -s /opt/nvim-linux64/bin/nvim /usr/local/bin/nvim
```

### xclip

```sh
sudo apt install xclip
```

---

## Music Player: cmus

`sudo apt install cmus`

---

## Password Management: KeepassXC

Add repository and install KeepassXC.

```
sudo add-apt-repository ppa:phoerious/keepassxc sudo apt update sudo apt install keepassxc
```

---

## Fonts

### Install and Manage Fonts

```
sudo apt install font-manager
```

### Set Default Font (Without Desktop Environment)

Edit font configuration file.

```
nvim /home/ksfour/.config/fontconfig/fonts.conf
```

```
<?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "urn:fontconfig:fonts.dtd"> <fontconfig>   <alias>     <family>serif</family>     <prefer><family>Sarasa UI SC</family></prefer>   </alias>   <alias>     <family>sans-serif</family>     <prefer><family>Sarasa UI SC</family></prefer>   </alias>   <alias>     <family>monospace</family>     <prefer><family>Sarasa Mono SC</family></prefer>   </alias> </fontconfig>
```

### Nerd Fonts (Symbols Only)

Download from GitHub: [https://github.com/ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts)

---

## eBook Management: Calibre

```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
```

---

## Keyboard Input: 雾凇拼音

Install Rime and configure with 雾凇拼音 (flypy schema).

```
cd ~/src && curl -fsSL https://raw.githubusercontent.com/rime/plum/master/rime-install | bash && sudo apt-get install ibus-rime && cd plum && bash rime-install iDvel/rime-ice:others/recipes/full && bash rime-install iDvel/rime-ice:others/recipes/config:schema=flypy ibus-daemon -r -d -x
```

### Espanso

Download link: [https://espanso.org/](https://espanso.org/)

---

## Theme Setup (Without Desktop Environment)

Add KDE environment variable to `.bash_profile`.

```
cd ~ nvim .bash_profile
```

`XDG_CURRENT_DESKTOP=KDE`

Reboot to apply changes.

---

## System Clock

Set the system clock to local time.

```
sudo timedatectl set-local-rtc 1
```

---

## Screen Saver Disable

Disable screen saver and DPMS.

```
xset s off xset -dpms
```

