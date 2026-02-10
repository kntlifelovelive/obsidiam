

# Arch Linux Hyprland Project



---

## 1. System Update (first)

```bash
sudo pacman -Syu
```

---

## 2. Hyprland & Wayland Base

```bash
sudo pacman -S hyprland wayland xdg-desktop-portal-hyprland
```

Optional tools

```bash
sudo pacman -S hyprpaper hyprlock hypridle
```

---

## 3. Terminal & Shell

```bash
sudo pacman -S kitty alacritty foot
sudo pacman -S zsh starship
```

---

## 4. Neovim (Editor)

```bash
sudo pacman -S neovim
```

Extra (LazyVim / LSP အတွက် အသုံးများ)

```bash
sudo pacman -S nodejs npm python python-pip ripgrep fd
```

---

## 5. Clipboard (Copy / Paste)

### Text & Image copy

```bash
sudo pacman -S wl-clipboard
```

အသုံးပြုနည်း

```bash
echo "hello" | wl-copy
wl-paste
```

---

## 6. Audio (Sound / Copy Audio)

### PipeWire stack

```bash
sudo pacman -S pipewire pipewire-audio pipewire-pulse pipewire-alsa wireplumber
```

### Audio control

```bash
sudo pacman -S pavucontrol pamixer
```

### Audio record (copy audio)

```bash
sudo pacman -S pipewire-jack
```

Example

```bash
pw-record test.wav
```

---

## 7. Screenshot / Screen Record

### Screenshot

```bash
sudo pacman -S grim slurp swappy
```

Example

```bash
grim -g "$(slurp)" shot.png
```

### Screen record

```bash
sudo pacman -S wf-recorder
```

---

## 8. Waybar (Status Bar)

```bash
sudo pacman -S waybar
```

Extra modules

```bash
sudo pacman -S playerctl network-manager-applet blueman
```

---

## 9. App Launcher

```bash
sudo pacman -S rofi wofi
```

---

## 10. File Manager

```bash
sudo pacman -S thunar ranger nemo
```

Extras

```bash
sudo pacman -S gvfs tumbler
```

---

## 11. Notification

```bash
sudo pacman -S swaync
```

---

## 12. Fonts (Nerd Font + Google Noto)

```bash
sudo pacman -S ttf-jetbrains-mono-nerd ttf-firacode-nerd
```

### Google Noto Fonts (Myanmar + Unicode)

```bash
sudo pacman -S noto-fonts noto-fonts-cjk noto-fonts-emoji noto-fonts-extra
```

Myanmar font အတွက်  🇲🇲

---

## 13. Bluetooth / Network

```bash
sudo pacman -S bluez bluez-utils networkmanager
```

---

## 14. Useful CLI Tools

```bash
sudo pacman -S htop btop neofetch fastfetch unzip zip
```

---

## 15. AUR Helper (yay)

```bash
sudo pacman -S --needed base-devel git
cd /opt
sudo git clone https://aur.archlinux.org/yay.git
sudo chown -R $USER:users yay
cd yay
makepkg -si
```

---

## 16. AUR Popular Packages

```bash
yay -S google-chrome visual-studio-code-bin discord
```


---

# Preset Collections

## A. Minimal Hyprland Setup (Lightweight)

```bash
sudo pacman -S hyprland wayland xdg-desktop-portal-hyprland \
kitty wl-clipboard pipewire pipewire-pulse wireplumber \
waybar grim slurp swaync ttf-jetbrains-mono-nerd
```

---

## B. Developer Setup (Neovim + Web/Python)

```bash
sudo pacman -S neovim nodejs npm python python-pip ripgrep fd \
git lazygit docker docker-compose
```

Optional LSP tools

```bash
npm install -g vscode-langservers-extracted
pip install pynvim black isort
```

---

## C. Rice / Customize Setup (UI & Style)

```bash
sudo pacman -S rofi wofi hyprpaper hyprlock hypridle \
qt5-wayland qt6-wayland nwg-look
```

Theme tools

```bash
sudo pacman -S papirus-icon-theme lxappearance
```

---

## D. Media / Audio / Video

```bash
sudo pacman -S pavucontrol pamixer playerctl wf-recorder ffmpeg
```

---

## E. Daily CLI Power Tools

```bash
sudo pacman -S zsh starship tmux btop fastfetch
```

---

## F. Optional Apps (AUR)

```bash
yay -S google-chrome visual-studio-code-bin obsidian
```

---
