
---

## ✅ Step by Step ➤ `.deb` Package ဖန်တီးနည်း

### 🧱 Step 1 – Folder Structure Ready လုပ်မယ်

```bash
mkdir -p ~/debbuild/ramcleaner/DEBIAN
mkdir -p ~/debbuild/ramcleaner/usr/local/bin
mkdir -p ~/debbuild/ramcleaner/usr/share/applications
mkdir -p ~/debbuild/ramcleaner/usr/share/icons/hicolor/64x64/apps
```

---

### 📜 Step 2 – Script ကို ထည့်မယ်

```bash
cp ~/scripts/ram_cleaner.sh ~/debbuild/ramcleaner/usr/local/bin/ram_cleaner
chmod +x ~/debbuild/ramcleaner/usr/local/bin/ram_cleaner
```

> `ram_cleaner.sh` ကို package ထဲမှာ `ram_cleaner` လို့ rename လုပ်လိုက်တယ်။

---

### 🎨 Step 3 – Icon ထည့်မယ်

Icon `.png` တစ်ခု (ဥပမာ `ramclean.png`) ကို

```bash
cp ~/Pictures/icons/ramclean.png ~/debbuild/ramcleaner/usr/share/icons/hicolor/64x64/apps/ramclean.png
```

> Size: 64x64 လို့ standard ဖြစ်အောင်လုပ်ဖို့အရေးကြီးပါတယ်။

---

### 🖥️ Step 4 – `.desktop` Shortcut ဖန်တီးမယ်

```bash
nano ~/debbuild/ramcleaner/usr/share/applications/ramclean.desktop
```

ထဲမှာ👇

```ini
[DesktopEntry]
Version=1.0
Type=Application
Name=🧠 RAM Cleaner
Comment=Clean your RAM easily!
Exec=ram_cleaner
Icon=ramclean
Terminal=true
Categories=Utility;
```

---

### 🧾 Step 5 – `control` file ထည့်မယ်

```bash
nano ~/debbuild/ramcleaner/DEBIAN/control
```

ထဲမှာ👇

```
Package: ramcleaner
Version: 1.0
Section: utils
Priority: optional
Architecture: all
Maintainer: Kyaw Nyein Thant <kyaw@example.com>
Description: RAM Cleaner tool using shell script with a colorful interface
```

---

### 📦 Step 6 – `.deb` file ထုတ်မယ်

```bash
cd ~/debbuild
dpkg-deb --build ramcleaner
```

ပြီးရင် ➤ `ramcleaner.deb` ဆိုတဲ့ file လုပ်ထွက်လာပါပြီ။

---

### 🧪 Step 7 – Install လုပ်ကြမယ်

```bash
sudo dpkg -i ramcleaner.deb
```

တင်ပြီးတာနဲ့ `Application Menu` မှာ “🧠 RAM Cleaner” လို့ရှာလို့ရမယ်။  
ဖိလိုက်တာနဲ့ ➤ Terminal GUI Interface ပေါ်လာမယ် 💥

---

## 🎯 Summary

|Item|Path|
|---|---|
|Script|`/usr/local/bin/ram_cleaner`|
|Icon|`/usr/share/icons/hicolor/64x64/apps/ramclean.png`|
|Desktop Entry|`/usr/share/applications/ramclean.desktop`|
|Installed via|`dpkg -i ramcleaner.deb`|

---

### 💡 Bonus Tip – Icon မထပ်ခါတလဲလဲချင်ရင်

`/usr/share/icons/hicolor/64x64/apps/ramclean.png` မှာ overwrite လုပ်ဖို့ပဲ လိုပါတယ်။ Desktop entry မှာ icon name ကို `.png` မပါတဲ့ အမည်ပေးရင် GNOME ထဲက default theme path ထဲက image ရှာမှာပါ။

---
