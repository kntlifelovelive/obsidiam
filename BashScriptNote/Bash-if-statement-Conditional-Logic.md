
Bash မှာ `if` statement ကို **Conditional Logic** အတွက် အသုံးပြုပါတယ်။ 

---

### **Basic Syntax**
```bash
if [ condition ]; then
    # code to run if condition is true
elif [ another_condition ]; then
    # code to run if another_condition is true
else
    # code to run if all conditions are false
fi
```

---

### **Condition Types**
Bash မှာ `if` statement နဲ့တွဲသုံးဖို့ **Conditions** အမျိုးမျိုးရှိပါတယ်။

#### 1. **File Tests**
- `-f file`: File ရှိမရှိ စစ်ခြင်း
- `-d dir`: Directory ရှိမရှိ စစ်ခြင်း
- `-r file`: ဖိုင်ကို ဖတ်လို့ရမရှိ စစ်ခြင်း
- `-w file`: ဖိုင်ကို ရေးလို့ရမရှိ စစ်ခြင်း

**ဥပမာ:**
```bash
if [ -f "test.txt" ]; then
    echo "test.txt exists!"
fi
```

#### 2. **String Comparisons**
- `"$str1" == "$str2"`: String တူမတူ စစ်ခြင်း
- `"$str1" != "$str2"`: String မတူမရှိ စစ်ခြင်း
- `-z "$str"`: String က empty ဖြစ်နေလား
- `-n "$str"`: String က empty မဖြစ်ဘူးလား

**ဥပမာ:**
```bash
name="John"
if [ "$name" == "John" ]; then
    echo "Hello John!"
fi
```

#### 3. **Numeric Comparisons**
- `$num1 -eq $num2`: Equal (`=`)
- `$num1 -ne $num2`: Not Equal (`!=`)
- `$num1 -gt $num2`: Greater Than (`>`)
- `$num1 -lt $num2`: Less Than (`<`)
- `$num1 -ge $num2`: Greater Than or Equal (`>=`)
- `$num1 -le $num2`: Less Than or Equal (`<=`)

**ဥပမာ:**
```bash
age=25
if [ $age -ge 18 ]; then
    echo "You are an adult."
fi
```

---

### **Logical Operators**
- `&&` (AND): အားလုံးမှန်မှ မှန်
- `||` (OR): တစ်ခုမှန်ရင် မှန်
- `!` (NOT): မှားရင် မှန်၊ မှန်ရင် မှား

**ဥပမာ:**
```bash
if [ $age -gt 18 ] && [ "$country" == "MM" ]; then
    echo "You are a Myanmar adult."
fi
```

---

### **Advanced Conditions with `[[ ]]`**
`[[ ]]` ကို အသုံးပြုရင် **Pattern Matching** နဲ့ **Regular Expressions** သုံးလို့ရပါတယ်။

**ဥပမာ:**
```bash
file="image.jpg"
if [[ "$file" == *.jpg ]]; then
    echo "This is a JPEG file."
fi
```

---

### **Command Exit Status**
Command တစ်ခု အောင်မြင်လားဆိုတာ စစ်လို့ရပါတယ်။
- `0`: Success
- `1` (or non-zero): Failure

**ဥပမာ:**
```bash
if grep "error" log.txt; then
    echo "Error found in log."
fi
```

---

### **Common Mistakes**
1. **Spaces**: `[ ]` အတွင်းမှာ Space လိုအပ်ပါတယ်။  
   ❌ `if[$a==$b]` → ✔️ `if [ $a == $b ]`
2. **Quotes**: Variable မှာ Space ပါနိုင်ရင် `"$var"` သုံးပါ။  
   ❌ `[ $name == John Doe ]` → ✔️ `[ "$name" == "John Doe" ]`
3. **Numeric vs String**: Numeric အတွက် `-eq`, String အတွက် `==` သုံးပါ။

---

### **Example Script**
```bash
#!/bin/bash

read -p "Enter your age: " age

if [ $age -lt 13 ]; then
    echo "You are a child."
elif [ $age -ge 13 ] && [ $age -lt 18 ]; then
    echo "You are a teenager."
else
    echo "You are an adult."
fi
```

---

### **အကျဉ်းချုပ်**
- `if` statement ကို **Conditional Logic** အတွက် အသုံးပြုပါ။
- Conditions မှာ **File Tests**, **String/Numeric Comparisons** စသဖြင့် အမျိုးမျိုးရှိပါတယ်။
- `&&`, `||`, `!` စတဲ့ **Logical Operators** တွေနဲ့ Condition တွေကို ပေါင်းစပ်နိုင်ပါတယ်။

ဒီအခြေခံတွေကို သိထားရင် Bash Scripting မှာ `if` statement ကို လွယ်လွယ်ကူကူ အသုံးပြုနိုင်ပါလိမ့်မယ်! 

---

