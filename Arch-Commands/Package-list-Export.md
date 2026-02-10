
---

## 🔹 Step (1)  – package list export

Arch မှာ package ကို အဓိက ၃ မျိုး ခွဲထားလို့ရတယ်  
- Official repo (pacman)  
- AUR (yay)  
- Optional – all 

---

###  1. Official repo packages (pacman)

```bash
pacman -Qqen > pkglist-pacman.txt
```

-  Explanation

- `-Q` = query installed
    
- `-q` = name only
    
- `-e` = explicitly installed (system auto deps မပါ)
    
- `-n` = official repo only
    

==> Hyprland, waybar, kitty, pipewire … အကုန်ပါမယ်

---

### 2. AUR packages (yay)

(discord, obsidian, google-chrome စတာတွေ)

```bash
pacman -Qqem > pkglist-aur.txt
```

==> Explanation

- `-m` = foreign packages (AUR)
    

==> discord / obsidian / spotify / brave-bin စတာတွေ ဒီထဲပါမယ်

---

###  3. (Optional) pacman + AUR ကို တစ်ခုထဲ

```bash
pacman -Qqe > pkglist-all.txt
```

 ဒီနည်းက system dependency တွေလည်း ပါနိုင်လို့  
**အကြံပြုတာက (1)+(2) ခွဲထားတာပါ**

---

## 🔹 Step (2) – list file ကို နောက်စက်ဆီ ယူသွားမယ်

နည်းအမျိုးမျိုးရပါတယ် 

- USB
- GitHub / GitLab
    
- scp
    

ဥပမာ (scp) –

```bash
scp pkglist-*.txt user@newpc:/home/user/
```

---

##  Step (3) – နောက်စက်မှာ restore လုပ်မယ်

####  (A) Arch clean install ပြီးပြီးချင်း

####  pacman packages ပြန်တင်

```bash
sudo pacman -S --needed - < pkglist-pacman.txt
```

 `--needed` → already installed package မထပ်တင်ဘူး

---

####  yay install (မရှိသေးရင်)

```bash
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

---

####  AUR packages (discord, obsidian) ပြန်တင်

```bash
yay -S --needed - < pkglist-aur.txt
```

==>  ဒီအဆင့်မှာ

- discord
    
- obsidian
    
- chrome
    
- hyprland plugins  
    အားလုံး auto ပြန်တင်သွားမယ်
    

---

## 🔹 Step (4) – confirm လုပ်ချင်ရင်

```bash
pacman -Q | wc -l
```

```bash
yay -Qm
```


---

##  Summary 

|အလုပ်|Command|
|---|---|
|pacman list|`pacman -Qqen`|
|AUR list|`pacman -Qqem`|
|pacman restore|`sudo pacman -S --needed - < file`|
|AUR restore|`yay -S --needed - < file`|

---
