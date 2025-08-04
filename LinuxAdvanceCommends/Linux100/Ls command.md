


---

## 🧾 `ls` command – Basic usage

```bash
ls
```

> မည်သည့် option မသုံးဘဲရင် current directory ထဲက file တွေကို အတိုအထွာပဲပြတယ်။

---

## 📋 `ls` command options – Explained

|Option|Meaning|မြန်မာဖော်ပြချက်|
|---|---|---|
|`-l`|Long listing format|ပိုမိုအသေးစိတ်အချက်အလက် (permission, size, date, etc.) ပြတယ်|
|`-a`|Show all files including hidden ones (`.` files)|dot (.) နဲ့စတဲ့ hidden file တွေအပါအဝင်ပြတယ်|
|`-h`|Human-readable sizes|file size တွေကို MB, KB, GB ဆိုပြီးလွယ်လွယ်နဲ့ဖတ်လို့ရအောင်ပြတယ်|
|`-t`|Sort by modification time (newest first)|အသွင်ပြင်ပြီးဆုံးချိန်နဲ့အတိုင်း ရှေးနောက်စဥ်လိုက်ပြတယ်|
|`-r`|Reverse order|sorting order ကို ပြန်လှန်ပြတယ်|
|`-R`|Recursive|subdirectory ထဲက files တွေကိုပါ ပြတယ်|
|`-S`|Sort by file size|ဖိုင်အရွယ်အစားအကြီးဆုံးကနေသေးသွားအတိုင်းစီပြတယ်|
|`-1`|One entry per line|ဖိုင်တစ်ခုကို တစ်ကြောင်းပြတယ်|
|`-d`|List directory itself, not its contents|directory name ကိုပဲပြတယ်၊ ထဲက contents မပြတယ်|
|`-F`|Classify entries with symbols|file တွေဟာ directory (`/`), executable (`*`) စတဲ့ symbol နဲ့အတူ ပြတယ်|

---

## 🧪 Combo Examples – 

1. **Show all files in long format including hidden files**

```bash
ls -la
```

> hidden file တွေအပါအဝင် အသေးစိတ်ဖော်ပြတယ်

---

2. **Show human-readable sizes**

```bash
ls -lh
```

> file size ကို MB/KB format နဲ့ ပြတယ်

---

3. **Sort files by last modified time**

```bash
ls -lt
```

> အသစ်ဆုံးဖိုင်တွေကို အထက်မှာတင်ပြတယ်

---

4. **Show all files recursively**

```bash
ls -lR
```

> folder ထဲမှာရှိတဲ့ subfolder တွေအကုန်လုံးထဲက file တွေကိုပြတယ်

---

5. **Show only directories, not contents**

```bash
ls -ld */
```

> directory name တွေကိုပဲ ဖော်ပြတယ်

---

6. **Sort files by size in reverse order**

```bash
ls -lSr
```

> အသေးဆုံးဖိုင်ကအစ sorting လုပ်ပြတယ်

---

7. **List with symbols showing file type**

```bash
ls -F
```

> directory ကို `/`, executable ကို `*` နဲ့ ပြတယ်

---

## Pro Tip (သိထားသင့်တဲ့အချက်)

Option တွေကို ပေါင်းပြီးသုံးလို့ရပါတယ်။ ဥပမာ:

```bash
ls -alh
```

> hidden files တွေအပါအဝင် အသေးစိတ်ဖော်ပြပြီး size တွေကိုလည်း MB, KB စနစ်နဲ့ပြတယ်။

---

နောက်ထပ် `ls` option တွေသိချင်တယ်ဆိုရင်တော့ ဒီလို command နဲ့ကြည့်လို့ရပါတယ်👇

```bash
man ls
```

ဒါမှမဟုတ်:

```bash
ls --help
```

---
