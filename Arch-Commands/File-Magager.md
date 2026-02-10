
---

##  File Manager (Default -Dolphin)

###  **Thunar** (Xfce)

-  ပေါ့ပါး၊ မြန်
    
- GTK based → Hyprland နဲ့ သဘောကျတယ်
    

```bash
sudo pacman -S thunar thunar-archive-plugin thunar-media-tags-plugin
```

---

### **Nautilus (GNOME Files)**

- Ubuntu မှာသုံးတဲ့ file manager
    
- Yaru icon နဲ့ အရမ်းလိုက်
    

```bash
sudo pacman -S nautilus
```

---

### **PCManFM**

- LXQt / LXDE file manager
    
- Simple + lightweight
    

```bash
sudo pacman -S pcmanfm
```

---

### **Ranger** (Terminal)

- Keyboard driven 💻
    
- CLI ကြိုက်ရင် အရမ်းမိုက်
    

```bash
sudo pacman -S ranger
```

---

###  **Nemo** (Cinnamon)

- Nautilus နဲ့ ဆင်တယ်
    
- Feature စုံ
    

```bash
sudo pacman -S nemo
```

- **Hyprland beginner / daily use အတွက်**  
- `Thunar` သို့ `Nautilus` ကို အကြံပြုပါတယ်

---

##  Ubuntu  **Yaru Icon Theme**

Arch repo ထဲမှာရှိပါတယ် 

```bash
sudo pacman -S yaru-icon-theme yaru-gtk-theme
```

### Icon apply 

- GTK app (Thunar, Nautilus) 
    

```bash
sudo pacman -S nwg-look
nwg-look
```

- Icon Theme → **Yaru**  
 - GTK Theme → **Yaru**

---

## Google Font (Todo / Roboto / Noto 

### Google Fonts  Arch repo

```bash
sudo pacman -S ttf-roboto ttf-noto-sans ttf-noto-serif
```

 Font refresh

```bash
fc-cache -fv
```

Hyprland config / GTK / app well done. 

---

## `yay` (AUR helper) 

###  git မရှိသေးရင်

```bash
sudo pacman -S git base-devel
```

###  yay install

```bash
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

###  yay 

```bash
yay -S google-chrome visual-studio-code-bin
```

---

-  File manager → **Thunar / Nautilus**
    
-  Ubuntu look → **Yaru icon + gtk**
    
- Font → **Roboto / Noto (Google Fonts)**
    
-  AUR → **yay**
    

