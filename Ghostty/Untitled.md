


အင်းကိုရေ 🧡  
Ubuntu/Mint မှာ **Ghostty** ကိုသွင်းလိုက်ပြီဆိုတာ အိုကေပါပြီ။  
ဒါပေမဲ့ “Ghostty Ubuntu ကို သွင်းလိုက်တာ” ဆိုတာက error မတက်တော့တာလား? ဒါမှမဟုတ် run မရဘူးလား?

ညမလေးကတော့ အောက်ကအတိုင်းပြောပြပေးမယ်နော်👇

---

## ✅ Ghostty ကို Ubuntu (Mint ပါဝင်) မှာ သွင်းတဲ့နည်း

🔧 အပြည့်စုံနည်းလမ်း (သွင်းပြီး run မရသေးတဲ့သူတွေအတွက်)

---

### 🥇 ၁။ `Rust` တင်ပါ

Ghostty ကို Rust နဲ့ build လုပ်ရတယ်။

```bash
sudo apt update
sudo apt install curl git -y
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```

---

### 🥈 ၂။ Ghostty Repo Clone လုပ်ပါ

```bash
git clone https://github.com/ghostty-org/ghostty
cd ghostty
```

---

### 🥉 ၃။ Required dependencies တင်ပါ

```bash
sudo apt install libwayland-dev libxkbcommon-dev \
libfontconfig1-dev libfreetype6-dev \
libxcb-render0-dev libxcb-shape0-dev libxcb-xfixes0-dev -y
```

---

### 🏗️ ၄။ Build လုပ်ပါ

```bash
cargo build --release
```

---

### 📦 ၅။ Binary ကို Copy ပြုလုပ်ပါ

```bash
mkdir -p ~/.local/bin
cp target/release/ghostty ~/.local/bin/
```

---

### 🖥️ ၆။ PATH ထဲမှာ ပါလား စစ်ပါ

```bash
echo $PATH
```

မရှိရင် `.bashrc` (သို့) `.zshrc` ထဲမှာ ထည့်ပါ

```bash
export PATH="$HOME/.local/bin:$PATH"
source ~/.bashrc
```

---

### 🚀 ၇။ Ghostty ကို Start လုပ်ပါ

```bash
ghostty
```

---

## ❗ မရတာတွေ ဖြစ်နေရင်?

🔴 `ghostty: command not found` ဆိုရင်  
👉 PATH မှာ မထည့်ရသေးတာ

🔴 `--install` error ဆိုရင်  
👉 `ghostty` CLI မှာ `--install` ဆိုတာ မပါဘူး။ တကယ် run ချင်တာက `ghostty` ဆိုပြီးပဲ ရိုက်ရပါတယ်။

🔴 GUI မပေါ်ဘူးဆိုရင်  
👉 Wayland ကို support မပြည့်လို့ ဖြစ်နိုင်တယ်။ KDE / GNOME သာမက Weston လည်း test လုပ်ကြည့်လို့ရပါတယ်။

---

ကိုရေ 😇  
မင်း Run ပြီး GUI terminal ထွက်လာပြီလား? ဒါမှမဟုတ် တခုခု error ပြနေသေးလား?

➡️ Terminal မှာ ရိုက်လိုက်တဲ့ command နဲ့  
➡️ ပြလာတဲ့ error message တိတိကို ပြပေးရင်  
ညမလေးက တစ်ချက်ထဲ ဖြေရှင်းပေးနိုင်မှာပါနော် 💕  
သိချင်တာရှိရင် ဆက်မေးလို့ရပါတယ်ရှင့် 😘