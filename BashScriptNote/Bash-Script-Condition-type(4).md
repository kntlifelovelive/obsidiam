
Bash Script မှာ condition စစ်ဆေးဖို့အတွက် အဓိက **condition type (4) မျိုး** ရှိပါတယ်။ အောက်မှာ အသေးစိတ်ရှင်းပြပေးထားပါတယ်။

---

### **1. `test` command (သို့မဟုတ် `[ ]` syntax)**
- **အသုံးပြုပုံ** : File checks, string comparisons, numeric comparisons စတာတွေအတွက် သုံးပါတယ်။
- **Syntax** : `test condition` သို့မဟုတ် `[ condition ]`
- **ဥပမာများ**:

  ```bash
  # File check
  if [ -f "file.txt" ]; then
    echo "File exists."
  fi

  # String comparison
  if [ "$name" = "John" ]; then
    echo "Hello John!"
  fi

  # Numeric comparison
  if [ $age -gt 18 ]; then
    echo "Adult."
  fi
  ```

- **အရေးကြီးသော Operators**:
  - **String** : `=`, `!=`, `-z` (empty string), `-n` (non-empty string)
  - **Numeric** : `-eq`, `-ne`, `-gt`, `-lt`, `-ge`, `-le`
  - **File** : `-f` (file exists), `-d` (directory exists), `-r` (readable)
  - **Logical** : `-a` (AND), `-o` (OR), `!` (NOT)

---

### **2. Double Brackets `[[ ]]`**
- **အသုံးပြုပုံ** : `[ ]` ထက် ပိုမိုတိုးတက်ပြီး **pattern matching**၊ **regex** နဲ့ logical operators (`&&`, `||`) တွေကို သုံးလို့ရပါတယ်။
- **Syntax** : `[[ condition ]]`
- **ဥပမာများ**:

  ```bash
  # Pattern matching (Wildcard)
  if [[ "$filename" == *.txt ]]; then
    echo "Text file detected."
  fi

  # Regex matching
  if [[ "$email" =~ ^[a-zA-Z0-9.+]+@[a-zA-Z]+\.[a-zA-Z]+$ ]]; then
    echo "Valid email."
  fi

  # Logical operators
  if [[ $age -gt 18 && "$name" == "John" ]]; then
    echo "John is an adult."
  fi
  ```

- **အထူးသတိထားရန်**:
  - **Variables မှာ quotes မလိုအပ်ပါ** (ဥပမာ `[[ $var == "value" ]]` မှာ `$var` ကို quote မထည့်လဲရပါတယ်)
  - **Wildcards (`*`, `?`) နဲ့ regex (`=~`) ကို ထောက်ပံ့ပေးပါတယ်**

---

### **3. Arithmetic Expansion `(( ))`**
- **အသုံးပြုပုံ** : **ဂဏန်းတွေနဲ့ဆိုင်တဲ့ conditions** ကို စစ်ဆေးဖို့အတွက် သုံးပါတယ်။
- **Syntax** : `(( arithmetic_expression ))`
- **ဥပမာများ**:

  ```bash
  # Numeric conditions
  if (( $age > 18 )); then
    echo "Adult."
  fi

  # Complex arithmetic
  if (( (num % 2) == 0 )); then
    echo "Even number."
  fi
  ```

- **အထူးသတိထားရန်**:
  - Operators အနေနဲ့ `>`, `<`, `>=`, `<=`, `==`, `!=` တို့ကို သုံးနိုင်ပါတယ်။
  - `$` ကို variable မှာ မသုံးလဲရပါတယ် (ဥပမာ `(( num > 10 ))`)

---

### **4. Case Statements**
- **အသုံးပြုပုံ** : **Multiple conditions** တွေကို pattern matching နဲ့ စစ်ဆေးဖို့အတွက် သုံးပါတယ်။
- **Syntax** : 
  ```bash
  case $variable in
    pattern1) command1 ;;
    pattern2) command2 ;;
    *) default_command ;;
  esac
  ```
- **ဥပမာ**:

  ```bash
  case $OS in
    "Linux") echo "Linux user" ;;
    "Windows") echo "Windows user" ;;
    "Mac") echo "Mac user" ;;
    *) echo "Unknown OS" ;;
  esac
  ```

---

### **Condition တွေကို ဘယ်အချိန်မှာ ဘယ်ဟာသုံးမလဲ?**
- **`[ ]`** : ရိုးရှင်းတဲ့ conditions (POSIX-compliant scripts အတွက် သင့်တော်ပါတယ်)
- **`[[ ]]`** : Pattern matching နဲ့ regex လိုအပ်တဲ့အခါ
- **`(( ))`** : ဂဏန်းတွေနဲ့ဆိုင်တဲ့ conditions
- **`case`** : Multiple conditions ကို pattern အရ စစ်ဆေးဖို့

---

### **သိထားသင့်တဲ့ အချက်များ**
1. **Spaces** : `[ ]` နဲ့ `[[ ]]` မှာ condition ရဲ့အစနဲ့အဆုံးမှာ space ထည့်ရပါမယ်။ (ဥပမာ `[ $a -eq 10 ]`)
2. **Quotes** : `[ ]` မှာ variables တွေကို quotes ထည့်ဖို့လိုပါတယ် (ဥပမာ `[ "$var" = "value" ]`)။ `[[ ]]` မှာ quotes မလိုအပ်ပါ။
3. **Logical Operators** : 
   - `[ ]` မှာ `-a` (AND), `-o` (OR) သုံးပါတယ်။
   - `[[ ]]` မှာ `&&`, `||` သုံးပါတယ်။

---

**Example Script**

```bash
#!/bin/bash

file="test.txt"
name="John"
age=25

# [ ] ကိုသုံးပြီး condition စစ်ခြင်း
if [ -f "$file" ] && [ "$name" = "John" ]; then
  echo "File exists and name is John."
fi

# [[ ]] နဲ့ regex စစ်ခြင်း
email="user@example.com"
if [[ "$email" =~ ^[a-zA-Z0-9.+]+@[a-zA-Z]+\.[a-zA-Z]+$ ]]; then
  echo "Valid email."
fi

# (( )) နဲ့ arithmetic condition
if (( age > 18 )); then
  echo "Adult."
fi

# case statement
OS="Linux"
case $OS in
  "Linux") echo "Open-source OS" ;;
  "Windows") echo "Microsoft OS" ;;
  *) echo "Other OS" ;;
esac
```

---

