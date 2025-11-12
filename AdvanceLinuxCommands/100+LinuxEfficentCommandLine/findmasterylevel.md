
---

##  Step-by-Step — `find` Mastery Plan 

###  **Level 1 – Basic Filters**

အဓိကသုံးတဲ့ “test” options တွေပါ —

```bash
find . -type f -name "*.txt"       # .txt ဖိုင်တွေရှာ
find /etc -type d -name "nginx*"   # directory တွေရှာ
find ~/Downloads -size +50M        # 50MB ကျော်ဖိုင်ရှာ
find / -mtime -1                   # မနေ့တုန်းကပြင်ထားတဲ့ ဖိုင်ရှာ
find / -user kyaw                  # Kyaw ရဲ့ဖိုင်တွေရှာ
```

**Tests** ဆိုတာ — ဖိုင်တစ်ခုစီကို စစ်မယ့် “စစ်ခြင်း” တွေပါ။
###  **Level 2 – Logic control**


```bash
find . \( -name "*.mp4" -o -name "*.mkv" \)
find . -type f -a -name "*.conf"
find . ! -name "*.bak"
```


- `-o` → OR
- `-a` → AND
- `!` → NOT

Tip ==> parentheses တွေသုံးတဲ့အခါ `\(` `\)` လို့ escape လုပ်ဖို့မမေ့ပါနဲ့   ................. ။

###  **Level 3 – Action Options**

==> Example 

```bash
find . -type f -name "*.bak" -delete              # ဖျက်
find . -type f -name "*.jpg" -exec ls -lh {} \;   # စာရင်းပြ
find . -type f -exec file {} \;                   # file type စစ်
find . -type f -exec cp -t ~/Backup {} +          # copy စုပေး
```

==>  `-exec` နဲ့ `-delete` တို့က “**Action options**” ဖြစ်ပြီး test result ပေါ်မှာ လုပ်ဆောင်မှု လုပ်တာပါ။


###  **Level 4 – Optimizing with `+`**

`-exec` နောက်မှာ `+` သုံးတာက performance booster ပါ။

```bash
# ဥပမာ: ဖိုင် 100 ခုကို cp တစ်ကြိမ်နဲ့ပဲလုပ်တယ်
find . -name "*.png" -exec cp -t ~/Images {} +
```

=> Efficiency နဲ့ ပြောရရင် `+` က command run တစ်ကြိမ်နဲ့ ဖိုင်အများကြီး process လုပ်သွားတယ်။


###  **Level 5 – Mixing find + xargs (super combo)**

`xargs` နဲ့ပေါင်းသုံးရင် super smart ဖြစ်ပါတယ် 

```bash
find . -type f -name "*.log" | xargs rm
find . -type f -print0 | xargs -0 cp -t ~/Backup
```

 `-print0` နဲ့ `xargs -0` သုံးတာက spaces ပါတဲ့ filename တွေကိုလည်း လုံးဝအဆင်ပြေပါတယ်။



###  **Level 6 – Real-World Smart Tricks**

|Goal|Command|
|---|---|
|Hidden files only|`find . -type f -name ".*"`|
|Empty directories|`find . -type d -empty`|
|7 days old files|`find . -mtime +7`|
|Find symlinks|`find . -type l`|
|Search case-insensitive|`find . -iname "*.jpg"`|
|Combine with grep|`find . -type f -exec grep -i "keyword" {} \;`|


###  **Level 7 – Custom command composition (smart automation)**

Example ==>  `.mp4` ဖိုင်တွေကို 100MB ထက်ကျော်ရင် backup 

```bash
find ~/Videos -type f -name "*.mp4" -size +100M -exec cp -t ~/Backup {} +
```

ဒါဆိုရင် `find` ကို script automation ထဲမှာထည့်လို့လည်း ရပါတယ်။


```bash
man find
info find
```

သို့မဟုတ် cheat sheet:

```bash
find . -type f -name "*.sh" -printf "%p\t%k KB\n"
```

(ဖိုင်နဲ့အရွယ်အစားတစ်ပြိုင်တည်းပြသတယ်)

---
