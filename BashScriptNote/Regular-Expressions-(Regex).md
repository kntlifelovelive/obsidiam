
### Regular Expressions (Regex) 

**Regular Expressions (Regex)** ဆိုတာက **Text Pattern Matching** လုပ်ဖို့ အသုံးပြုတဲ့ နည်းစနစ်ပါ။ အဓိကအားဖြင့် Text Data တွေကို **ရှာဖွေရေး (Search)**၊ **တင်စားခြင်း (Sort)**၊ **ပြောင်းလဲခြင်း (Replace)** စတာတွေ လုပ်ဖို့ အသုံးဝင်ပါတယ်။

Bash Shell မှာ Regular Expressions ကို `grep`၊ `sed`၊ `awk` နဲ့အတူ `[[ ... =~ ... ]]` သို့မဟုတ် **Linux Utilities** တွေနဲ့ အသုံးပြုနိုင်ပါတယ်။

---

## **Regular Expression Syntax**
**Regular Expression Operators** တွေကို သုံးပြီး **Pattern** တွေ ဖန်တီးတယ်။ အဓိက Operators တွေကို အောက်မှာ ဖော်ပြထားပါတယ်။

---

### **Basic Regular Expression Operators**

| Operator | Description                       | Example     | Matches                             |     |
| -------- | --------------------------------- | ----------- | ----------------------------------- | --- |
| `.`      | Any single character              | `c.t`       | cat, cut, c3t                       |     |
| `*`      | 0 or more of the preceding char   | `ab*`       | a, ab, abb, abbb                    |     |
| `+`      | 1 or more of the preceding char   | `ab+`       | ab, abb, abbb                       |     |
| `?`      | 0 or 1 of the preceding char      | `ab?`       | a, ab                               |     |
| `^`      | Start of a line                   | `^Hello`    | Matches lines starting with "Hello" |     |
| `$`      | End of a line                     | `world$`    | Matches lines ending with "world"   |     |
| `[ ]`    | Any one character in brackets     | `[abc]`     | a, b, c                             |     |
| `[^ ]`   | Any one character not in brackets | `[^abc]`    | d, e, f (not a, b, c)               |     |
| \|       | Logical OR                        | `cat` `dog` | `cat or dog`                        |     |
| `()`     | Grouping                          | `(ab)+`     | ab, abab, ababab                    |     |
| `{n}`    | Exactly n repetitions             | `a{3}`      | aaa                                 |     |
| `{n,}`   | n or more repetitions             | `a{3,}`     | aaa, aaaa, aaaaa                    |     |
| `{n,m}`  | Between n and m repetitions       | `a{2,4}`    | aa, aaa, aaaa                       |     |
| `\`      | Escape special characters         | `\.`        | Matches literal `.`                 |     |

---

### **Examples of Regular Expressions**

#### **1. Match a Word**
```bash
echo "hello world" | grep "world"
# Output: world
```

#### **2. Match a Pattern with Wildcards**
```bash
echo "cat cut cot" | grep "c.t"
# Output: cat cut cot
```

#### **3. Start and End of Line**
```bash
echo -e "apple\nbanana\ncherry" | grep "^a"
# Output: apple
```

#### **4. Repeating Characters**
```bash
echo "aa ab aaa aaaa" | grep "a{3}"
# Output: aaa aaaa
```

#### **5. Logical OR**
```bash
echo "cat dog mouse" | grep "cat|dog"
# Output: cat dog
```

#### **6. Negating Characters**
```bash
echo "apple orange pear" | grep "[^aeiou]"
# Output: All words with non-vowel starting letters
```

---

### **Extended Regular Expressions (ERE)**
Bash Shell မှာ `grep -E` သို့မဟုတ် `egrep` ကို အသုံးပြုရင် **Extended Regular Expressions (ERE)** အသုံးပြုနိုင်ပါတယ်။  
ERE မှာ `+`၊ `{}`၊ `()` စတဲ့ **Advanced Operators** တွေကို အလွယ်တကူ အသုံးပြုနိုင်ပါတယ်။

---

### **Regular Expression Practical Uses**

#### **1. Validate Email**
```bash
email="test@example.com"
if [[ $email =~ ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$ ]]; then
    echo "Valid email"
else
    echo "Invalid email"
fi
```

#### **2. Extract Numbers**
```bash
echo "Order123 is confirmed" | grep -o "[0-9]+"
# Output: 123
```

#### **3. Replace Text with `sed`**
```bash
echo "Hello world" | sed 's/world/Regex/'
# Output: Hello Regex
```

#### **4. Count Specific Words**
```bash
echo "apple orange apple banana" | grep -o "apple" | wc -l
# Output: 2
```

---

Regular Expressions က Shell Scripting နဲ့ Text Processing မှာ အရမ်းအသုံးဝင်တဲ့ Tools တစ်ခုပါ။

---


