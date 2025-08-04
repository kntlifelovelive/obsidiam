


---


## 📘 **Termux မှာ Nerd Font ထည့်ဖို့ အတွက် Note (Quick Guide)**

---

### ✅ **အဓိကအကြောင်းအရာ**

> Nerd Font မရှိရင် icon တွေ မမြင်ရဘူး။ ဖန်တီးမှု UI တွေလည်း မလှ။ Font မွန်မှ UI ပိုလှတယ်။

---

### 🪛 **Installation Steps**

#### 📁 1. `.termux` folder ဖန်တီး

```bash
mkdir -p ~/.termux
```

#### 🔤 2. Nerd Font Download လုပ်ပြီး ထည့်

```bash
cd ~/.termux
curl -LO https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/JetBrainsMono.zip
unzip JetBrainsMono.zip 'JetBrainsMonoNerdFont-Regular.ttf'
mv JetBrainsMonoNerdFont-Regular.ttf font.ttf
rm JetBrainsMono.zip
```

📝 အရေးကြီး → ဖိုင်နာမည်ကို `font.ttf` လို့ပေးရမယ်။

---

#### 🔁 3. Settings ပြန် Load

```bash
termux-reload-settings
```

➡️ Termux App ကို **ပိတ်ပြီး ပြန်ဖွင့်**ပါ။

---

#### 🧪 4. Icons စမ်းကြည့်

```bash
echo 'Icons Test:      契 '
```

📌 ပေါ်လာတာနဲ့ Nerd Font success ဖြစ်တာပါ။

---

### 🔎 **ထပ်သိထားသင့်တဲ့အချက်များ**

|အချက်|ဖော်ပြချက်|
|---|---|
|Font file path|`~/.termux/font.ttf` (ဖိုင်နာမည်အတိအကျ)|
|Font format|`.ttf` only|
|Reload method|`termux-reload-settings`|
|Nerd Font UI|p10k, nvim-tree, lualine, exa, starship|
|Fallback|Termux:Styling app (manual လုပ်တာက ပိုကောင်း)|

---

### 🧠 Useful Tip

- Nerd Font တွေကို [https://www.nerdfonts.com/font-downloads](https://www.nerdfonts.com/font-downloads) မှာရနိုင်တယ်။
- JetBrainsMono, Hack, FiraCode တွေက Dev အတွက် မိုက်တဲ့ Nerd Fonts ဖြစ်တယ်။

---

## 📝 Summary

```bash
# Nerd Font Quick Install
mkdir -p ~/.termux
cd ~/.termux
curl -LO https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/JetBrainsMono.zip
unzip JetBrainsMono.zip 'JetBrainsMonoNerdFont-Regular.ttf'
mv JetBrainsMonoNerdFont-Regular.ttf font.ttf
rm JetBrainsMono.zip
termux-reload-settings
```

---

