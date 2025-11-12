
---

##  `find` command ထဲက syntax term 

### 1 **`-exec` → Action ( option)**

`find` မှာရှိတဲ့ option တွေကို **test** (စစ်ဆေးမှု) နဲ့ **action** (လုပ်ဆောင်မှု) လို့ခွဲတယ်။  
`-exec` ကတော့ _Action option_ တစ်ခုဖြစ်ပြီး “တွေ့တဲ့ ဖိုင်တိုင်းအပေါ်မှာ command တစ်ခုပြုလုပ်ပါ” ဆိုတဲ့အဓိပ္ပါယ်ရှိတယ်။

- Example

```bash
find . -type f -exec rm {} \;
```

ဆိုတာက “တွေ့တဲ့ ဖိုင်တိုင်းကို `rm` command နဲ့ဖျက်ပါ” ဆိုတဲ့ _Action_ ပဲ။

---

### 2 **`{}` → Placeholder ( or Substitution token)**

ဒီ `{}` ဆိုတာက _placeholder_ လို့ခေါ်တယ်။  
`find` ကတွေ့တဲ့ ဖိုင် path ကို ဒီနေရာမှာ အစားထိုးပေးတယ်။  


### 3  **`\;` နဲ့ `+` → Command terminators (အဆုံးသတ်ညွှန်ကြားချက်)**

`-exec` ကို သုံးတဲ့အခါ အဆုံးသတ်ဖို့ `\;` ဒါမှမဟုတ် `+` တစ်ခုခုဖြစ်ရမယ်။

🔹 `\;` → _run command once per file_  
(ဖိုင်တစ်ခုချင်းစီအတွက် command တစ်ကြိမ်စီလုပ်တယ်)

```bash
find . -type f -exec echo {} \;
```

🔹 `+` → _run command once for many files_  
(ဖိုင်တွေကိုစုပြီး command တစ်ခုပေါ်သွားတယ် — performance ပိုကောင်းတယ်)

```bash
find . -type f -exec cp -t ~/Videos {} +
```

==> နာမည်အနေနဲ့ “**aggregate terminator**” လို့ခေါ်ကြတတ်တယ်။


### 4  **`\(` နဲ့ `\)` → Grouping operators**

`find` မှာ logic expression တွေကို **grouping** လုပ်ဖို့သုံးတာပါ။  
Shell မှာ parentheses ကို `find` မထိခိုက်အောင် `\` နဲ့ escape လုပ်ရတယ်။

==> 

```bash
find . \( -name "*.mp3" -o -name "*.mp4" \)
```

ဆိုတာက `(A OR B)` ဆိုတဲ့ logic grouping ပဲ။  
နာမည်အနေနဲ့ “**Expression grouping operators**” လို့ခေါ်ကြတယ်။



###  အားလုံးပေါင်းထားတဲ့ structure ကတော့

```bash
find [path] [tests] [operators] [actions]
```

==> Example 

```bash
find ~/Downloads/Telegram\ Desktop/ -type f \( -name "*blood" -o -name "*.mp4" \) -exec cp -t ~/Videos/bloodriver {} +

or 

find ~/Download/Telegram\ Desktop/ -type f \( -name "*blood" -o -name "*river" -name "*.mp4" \) -exec cp -t ~/Videos/bloodriver { } + 

```

Details ခွဲကြည့်ရင် —

|Part|Function|နာမည်ခေါ်ခြင်း|
|---|---|---|
|`find`|Command|Utility name|
|`~/Downloads/Telegram Desktop/`|Search path|Path argument|
|`-type f`|Test|File-type test|
|`\( ... \)`|Grouping|Expression grouping|
|`-name`|Test|Name test|
|`-o`|Operator|Logical OR operator|
|`-exec`|Action|Execution action|
|`{}`|Placeholder|Substitution token|
|`+`|Terminator|Aggregate terminator|

---
