
### 1. **`while` Loop**
`while` loop သည် condition တစ်ခု true ဖြစ်နေစဉ် loop ကို ဆက်လက်လုပ်ဆောင်ပါသည်။

#### **Syntax**:
```bash
while [condition]
do
    # command(s)
done
```

#### **Example**:
```bash
#!/bin/bash

counter=1
while [ $counter -le 5 ]
do
    echo "Loop iteration: $counter"
    ((counter++))  # increment counter by 1
done
```

**Explanation**:  
- `counter=1` ဆိုတာ counter variable ကို 1 ထားပေးခြင်း။
- `while [ $counter -le 5 ]` သည် counter သည် 5 ထက်တန်ဖိုးမပိုရန် loop ကို ဆက်လက်လုပ်ဆောင်ပေးမှာဖြစ်သည်။
- `((counter++))` သည် counter ကို တစ်ခုချင်းပြောင်းလဲထားသည်။
- loop ပြီးရင် "Loop iteration: 1" ကနေ "Loop iteration: 5" အထိ print ပါလိမ့်မယ်။

### 2. **`until` Loop**
`until` loop သည် condition တစ်ခု false ဖြစ်နေစဉ် loop ကို ဆက်လက်လုပ်ဆောင်ပါသည်။

#### **Syntax**:
```bash
until [condition]
do
    # command(s)
done
```

#### **Example**:
```bash
#!/bin/bash

counter=1
until [ $counter -gt 5 ]
do
    echo "Loop iteration: $counter"
    ((counter++))  # increment counter by 1
done
```

**Explanation**:  
- `until [ $counter -gt 5 ]` သည် counter variable သည် 5 ထက်ကြီးမားတဲ့ condition ဖြစ်သောအထိ loop ကို ဆက်လက်လုပ်ဆောင်ပါလိမ့်မယ်။
- `((counter++))` က counter ကို တစ်ခုချင်းပေါင်းထည့်သည်။
- loop က "Loop iteration: 1" ကနေ "Loop iteration: 5" အထိ print ပြုလုပ်ပါလိမ့်မယ်။

### Summary:
- **`while` loop**: condition true ဖြစ်နေစဉ် loop ကို ဆက်လက်လုပ်ဆောင်သည်။
- **`until` loop**: condition false ဖြစ်နေစဉ် loop ကို ဆက်လက်လုပ်ဆောင်သည်။

---

### 1. **`break` Statement**
`break` statement သည် loop ကို ရပ်တန့်စေပါသည်။ Loop ကို condition တစ်ခုကြောင့် ရပ်တန့်လိုတဲ့အခါ `break` ကိုအသုံးပြုပါတယ်။

#### **Example** (with `while` loop):
```bash
#!/bin/bash

counter=1
while [ $counter -le 10 ]
do
    if [ $counter -eq 5 ]; then
        echo "Reached counter 5, breaking the loop!"
        break  # Breaks the loop when counter reaches 5
    fi
    echo "Counter is: $counter"
    ((counter++))
done
```

**Explanation**:
- `if [ $counter -eq 5 ]` ဆိုတာ counter အတိအကျ 5 သွားတဲ့အချိန်မှာ `break` statement ကို ဖော်ပြထားပါတယ်။ ထိုအချိန်မှာ loop ပိတ်ပါလိမ့်မယ်။
- Output: `Counter is: 1`, `Counter is: 2`, `Counter is: 3`, `Counter is: 4`, "Reached counter 5, breaking the loop!"

### 2. **`continue` Statement**
`continue` statement သည် loop ကို ရပ်တန့်စေခြင်းမရှိဘဲ အဆိုပါ iteration ကို skip လုပ်ပြီး အခြား iteration ကို ဆက်လက်လုပ်ဆောင်ပါသည်။

#### **Example** (with `while` loop):
```bash
#!/bin/bash

counter=1
while [ $counter -le 10 ]
do
    if [ $counter -eq 5 ]; then
        echo "Skipping counter 5"
        ((counter++))
        continue  # Skips the rest of the loop when counter is 5
    fi
    echo "Counter is: $counter"
    ((counter++))
done
```

**Explanation**:
- `if [ $counter -eq 5 ]` ဆိုတာ counter 5 ဖြစ်တဲ့အချိန်မှာ `continue` ကို အသုံးပြုပါတယ်။ ဒီအချိန်မှာ counter 5 ကို skip လုပ်ပြီး loop တစ်ခါကို ပျက်ကွက်နေစေပါမယ်။
- Output: `Counter is: 1`, `Counter is: 2`, `Counter is: 3`, `Counter is: 4`, "Skipping counter 5", `Counter is: 6`, ...

### **`break` and `continue` in `until` Loop**
`break` နဲ့ `continue` သည် `until` loop မှာလည်း အတိအကျအလုပ်လုပ်ပါတယ်။

#### **Example** (with `until` loop and `break`):
```bash
#!/bin/bash

counter=1
until [ $counter -gt 5 ]
do
    if [ $counter -eq 3 ]; then
        echo "Counter reached 3, breaking the loop!"
        break  # Breaks the loop when counter reaches 3
    fi
    echo "Counter is: $counter"
    ((counter++))
done
```

#### **Example** (with `until` loop and `continue`):
```bash
#!/bin/bash

counter=1
until [ $counter -gt 5 ]
do
    if [ $counter -eq 3 ]; then
        echo "Skipping counter 3"
        ((counter++))
        continue  # Skips the rest of the loop when counter is 3
    fi
    echo "Counter is: $counter"
    ((counter++))
done
```

### **Summary**:
- **`break`**: Loop ကိုအမြဲတမ်းရပ်တန့်လိုက်ပါသည်။
- **`continue`**: loop ကို skip လုပ်ပြီး အခြား iteration ကို ဆက်လက်လုပ်ဆောင်ပါသည်။
  
ဒီ `break` နဲ့ `continue` တွေဟာ loop တွေမှာ flow control ကို သုံးဖို့ အလွန်အသုံးဝင်တဲ့ method တွေဖြစ်ပါတယ်။

---
