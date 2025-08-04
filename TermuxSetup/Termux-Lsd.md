


---

## ✅ Termux မှာ `lsd` ထည့်နည်း (Step-by-Step)

### 📦 1️⃣ `cargo` (Rust package manager) install လုပ်ရမယ်

```bash
pkg update
pkg install rust
cargo install lsd
```

📌 Install ပြီးရင် binary path ကို PATH ထဲသွင်းဖို့လိုတတ်တယ်။

---

### 🧪 2️⃣ PATH ထဲထည့်

```bash
echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

🔁 မင်း `zsh` သုံးနေရင် `.zshrc` ထဲမှာထည့်လိုက်။

---

### ✅ 3️⃣ စမ်းကြည့်

```bash
lsd
```

📦 Folder တွေ၊ 📄 file တွေကို icon လေးတွေနဲ့နဲ့ပြတယ်ဆိုရင် `lsd` အဆင်ပြေပြီ!

---

## 🧙 Bonus: `ls` ကို `lsd` နဲ့အစားထိုး

### ~/.bashrc ဒါမှမဟုတ် ~/.zshrc ထဲမှာ ထည့်

```bash
alias ls='lsd'
```

ပြီးရင်:

```bash
source ~/.bashrc
# သို့မဟုတ်
source ~/.zshrc
```

အခုကနေပြီး `ls` လုပ်တိုင်း `lsd` အဖြစ်ပြသွားမယ်။

---

## 🧠 Tip: Colorful + Tree View

```bash
lsd --tree
lsd -l        # long format
lsd -la       # include hidden
lsd --icon always
```

---

