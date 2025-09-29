

Linux မှာ `trash` ဆိုတာက GUI Desktop Environment (GNOME, KDE, etc) တွေရဲ့ "Recycle Bin" (Windows) / "Trash" (macOS) နဲ့တူတဲ့ system တစ်ခုပဲဖြစ်ပါတယ်။

CLI (Terminal) မှာ `trash` ကိုထိန်းချုပ်ဖို့ GUI ရဲ့ Trash folder ကိုသုံးဖို့မလွယ်တာကြောင့် `trash-cli` ဆိုတဲ့ command-line tool တစ်ခုပြုလုပ်ထားပါတယ်။

---

## 🧺 `trash-cli` ကိုသုံးတာ

### ✅ ၁။ Install လုပ်ဖို့

```bash
sudo apt install trash-cli
```

---

### 📦 ၂။ ဖိုင်တစ်ခုကို Trash ထဲကို Move လုပ်ဖို့

```bash
trash-put filename
```

ตัวอย่าง:

```bash
trash-put myfile.txt
```

---

### 📂 ၃။ Trash ထဲမှာရှိတဲ့ ဖိုင်တွေကို `ls` လိုမျိုးကြည့်ချင်တယ်ဆိုရင်

```bash
trash-list
```

---

### ❌ ၄။ Trash ထဲကဖိုင်တွေကို အကုန်လုံးဖျက်ချင်တယ် (empty trash)

```bash
trash-empty
```

👉 တချို့ဆိုရင် argument ပေးနိုင်တယ်။ (နောက်ဆုံး X ရက်အကြာကြာကိုပဲဖျက်မယ်)

```bash
trash-empty 7   # 7 ရက်ကျော်တဲ့အဖိုင်တွေကိုပဲဖျက်မယ်
```

---

### 🔙 ၅။ Trash ထဲကဖိုင်ကို ပြန်ယူချင်တယ်ဆိုရင်

```bash
trash-restore
```

ဒါကို run လုပ်ရင် ပြန်ယူချင်တဲ့ဖိုင်နာမည်နဲ့ နံပါတ်တွေပြမှာပါ။ ပြန်ယူချင်တဲ့နံပါတ်ကိုထည့်လိုက်ရင် ပြန်ယူနိုင်ပါတယ်။

---

### 🛑 Trash folder ကိုသိချင်တယ်ဆိုရင်

GNOME သုံးနေရင် Trash ထဲကဖိုင်တွေဟာ ဒီလမ်းကြောင်းထဲမှာပါ:

```bash
~/.local/share/Trash/files/
```

Metadata (ဖျက်တဲ့ရက်စွဲတွေ၊ original path) ဆိုတာကတော့:

```bash
~/.local/share/Trash/info/
```

---

## 📝 အကျဉ်းချုပ်

|လုပ်ဆောင်ချက်|Command|
|---|---|
|Move file to trash|`trash-put filename`|
|List trash contents|`trash-list`|
|Empty trash|`trash-empty`|
|Restore from trash|`trash-restore`|
|Trash folder path|`~/.local/share/Trash/`|

---
