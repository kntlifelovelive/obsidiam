

---

## 📦 `.deb` Package ဆိုတာ ဘာလဲ?

`.deb` ဆိုတာက Debian/Ubuntu Linux distributions အတွက် installer package ပါ။ `.exe` files (Windows) နဲ့တူတယ်။ ဒီမှာတော့ မင်းရေးထားတဲ့ `TrashCan.sh` script ကို `.deb` package တစ်ခုအဖြစ် ပေးချင်တာပေါ့။

---

# ✅ Full Step-by-Step to Build `.deb` for TrashCan

---

## 🧱 Step 1: Folder Structure လုပ်မယ်

```bash
mkdir -p ~/trashcan-pkg/trashcan_1.0/usr/local/bin
mkdir -p ~/trashcan-pkg/trashcan_1.0/DEBIAN
```

### 📂 Structure ရလာမှာ:

```
~/trashcan-pkg/trashcan_1.0/
├── DEBIAN
└── usr
    └── local
        └── bin
```

---

## 📝 Step 2: Script ကို ထည့်

```bash
cp TrashCan.sh ~/trashcan-pkg/trashcan_1.0/usr/local/bin/trashcan
chmod +x ~/trashcan-pkg/trashcan_1.0/usr/local/bin/trashcan
```

➡️ ဒီထဲမှာ `TrashCan.sh` ဟာ `trashcan` လို့အမည်ပြောင်းသွားပါတယ်။ System command မျိုးတော့ `.sh` မလိုအပ်တော့ပါဘူး။

---

## 📄 Step 3: Control File ရေး

```bash
subl ~/trashcan-pkg/trashcan_1.0/DEBIAN/control
```

ထဲမှာ ဒီလိုရေးပါ (Copy & Paste)

```deb
Package: trashcan
Version: 1.0
Section: utils
Priority: optional
Architecture: all
Depends: bash, trash-cli, figlet, lolcat
Maintainer: bubu <your@email.com>
Description: A colorful CLI Trash Manager script
```

✔️ `Depends:` ထဲက packages (bash, trash-cli, etc.) မရှိရင် install မလုပ်ဘူး။

➡️ `Ctrl + O` → Save, `Ctrl + X` → Quit

---

## 🏗️ Step 4: `.deb` Package တည်ဆောက်

```bash
cd ~/trashcan-pkg
dpkg-deb --build trashcan_1.0
```

➡️ အလုပ်ဖြစ်လျှင် ဒီလို output တွေ့ရမယ်:

```
dpkg-deb: building package 'trashcan' in 'trashcan_1.0.deb'.
```

---

## 📥 Step 5: `.deb` install လုပ်

```bash
sudo dpkg -i trashcan_1.0.deb
```

➡️ အဆင်ပြေခဲ့ရင် terminal ထဲကနေ:

```bash
trashcan
```

လို့ရိုက်လိုက်တာနဲ့ မင်းရဲ့ script က လွင့်နေမှာပါ😍

---

## 📌 မမေ့သင့်တဲ့ Notes

|ဖိုင်နာမည်|ရည်ရွယ်ချက်|
|---|---|
|`control`|Package metadata|
|`/usr/local/bin/trashcan`|System command path|
|`.deb`|Installer file|

---

