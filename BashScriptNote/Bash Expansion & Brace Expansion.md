

#### Shell Expansion & Brace Expansion

**Shell Expansion** နဲ့ **Brace Expansion** က **Bash Shell** မှာ Command ကို run လုပ်တဲ့အခါ သက်ဆိုင်တဲ့ **Dynamic Text Replacement** နဲ့ **Pattern Matching** တွေကို လုပ်ပေးတဲ့ နည်းလမ်းတွေပါရှင့်။ 

---

## **1. Shell Expansion**
Shell Expansion က **Command Execution** မတိုင်ခင် **Bash Shell** က Text တွေကို **Expand** လုပ်ပြီး နောက်ဆုံးအဖြေကို ပြင်ဆင်ပေးတဲ့ process တစ်ခုပေါ့။ 

### **Shell Expansion မျိုးစုံ**
| Expansion Type      | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| **Pathname Expansion** | Wildcards (e.g., `*`, `?`) သုံးပြီး file name patterns ကို match လုပ်ခြင်း။   |
| **Tilde Expansion**    | `~` သင်္ကေတကို Home Directory သို့ Expand လုပ်ခြင်း။                       |
| **Arithmetic Expansion** | `$((expression))` ကို Evaluate လုပ်ပြီး ရလဒ်ကို ထုတ်ပေးခြင်း။              |
| **Command Substitution** | `$(command)` ကို run လုပ်ပြီး Output ကိုထုတ်ပေးခြင်း။                      |
| **Variable Expansion**  | `$VAR` သို့မဟုတ် `${VAR}` ကို Variable Value နဲ့ အစားထိုးခြင်း။              |

---

### **Shell Expansion Examples**

#### **1. Pathname Expansion**
```bash
echo *.txt
# Current directory ထဲက .txt file အားလုံးကို List ပြမယ်။
```

#### **2. Tilde Expansion**
```bash
echo ~
# Output: /home/username (သင့် Home Directory)
```

#### **3. Arithmetic Expansion**
```bash
echo $((5 + 10))
# Output: 15
```

#### **4. Command Substitution**
```bash
echo "Today's date: $(date)"
# Output: Today's date: <current date>
```

#### **5. Variable Expansion**
```bash
name="Kyaw"
echo "Hello, $name!"
# Output: Hello, Kyaw!
```

---

## **2. Brace Expansion**
Brace Expansion က Text ကို Patterns များစွာ ဖြစ်အောင် **Generate** လုပ်ပေးတယ်။ **Lists** သို့မဟုတ် **Sequences** တွေကို တိုတောင်းစွာရေးဖို့ အသုံးဝင်ပါတယ်။

### **Brace Expansion Syntax**
```bash
{item1,item2,...}
{start..end[..step]}
```

---

### **Brace Expansion Examples**

#### **1. Simple List Expansion**
```bash
echo {apple,banana,cherry}
# Output: apple banana cherry
```

#### **2. Number Sequence**
```bash
echo {1..5}
# Output: 1 2 3 4 5
```

#### **3. Number Sequence with Step**
```bash
echo {1..10..2}
# Output: 1 3 5 7 9
```

#### **4. Alphabet Sequence**
```bash
echo {a..f}
# Output: a b c d e f
```

#### **5. Combining Brace Expansion**
```bash
echo file{1..3}.txt
# Output: file1.txt file2.txt file3.txt
```

---

### **Shell Expansion နှင့် Brace Expansion အသုံးဝင်ပုံ**
1. **Automation**: ဖိုင်ပေါင်းများစွာကို သာမန် Loop မသုံးဘဲ Auto Generate လုပ်နိုင်သည်။  
   ```bash
   touch {file1,file2,file3}.txt
   ```

2. **Pattern Matching**: Shell Expansion နဲ့ Wildcard သုံးပြီး Files ကို Filter ရယူနိုင်သည်။  
   ```bash
   ls *.log
   ```

3. **Dynamic Commands**: Command Substitution နဲ့ Variable Expansion သုံးပြီး Scripts တွေ dynamic ဖြစ်စေသည်။  
   ```bash
   mkdir $(date +"%Y-%m-%d")
   ```

---

# **${\color{red}Note}$**

- ### *Shell Parameter and Variable Expansion*

```bash
love="i love you"
"$love"
$PATH, $HOME
```


---

### **Shell Parameter and Variable Expansion**
- **Parameter Expansion**: Shell ထဲမှာ သတ်မှတ်ထားတဲ့ variables (e.g., `$love`, `$PATH`, `$HOME`) တွေရဲ့ value ကို access လုပ်ဖို့ အသုံးပြုတဲ့ process တစ်ခုပေါ့။
- **Variable Expansion**: Shell variable ကို `$(...)` သို့မဟုတ် `${...}` နဲ့ call လုပ်ပြီး **value ကို expand** လုပ်တာကို ဆိုလိုပါတယ်။

---

### **ဥပမာ**

```bash
love="i love you"
echo "$love"
```

#### **Process:**
1. **Variable Definition**: `love="i love you"` မှာ `love` ဆိုတဲ့ variable ကို `"i love you"` string နဲ့ သတ်မှတ်တယ်။
2. **Variable Expansion**: `$love` ကို Shell က **"i love you"** နဲ့ အစားထိုးပြီး Output ထုတ်ပေးတယ်။

---

### **Parameter and Variable Expansion နဲ့ သက်ဆိုင်တဲ့ သင်္ကေတများ**

| Syntax          | Description                                     |
|------------------|-------------------------------------------------|
| `$VAR`          | Variable Value ကို Read လုပ်တယ်။                |
| `${VAR}`        | Variable Value ကို Read လုပ်တယ် (ကာကွယ်မှုများအတွက်။) |
| `${VAR:-default}`| Variable မရှိရင် `default` value ထည့်တယ်။        |
| `${#VAR}`       | Variable Value ရဲ့ Length (Length of String)။     |
| `${VAR%pattern}`| Value ရဲ့ နောက်ဆုံးမှာ pattern ကို ဖျက်ပစ်တယ်။    |

---

### **သုံးပုံသုံးနည်းများ**

#### **1. Variable Expansion**
```bash
name="Kyaw"
echo "Hello, $name"
# Output: Hello, Kyaw
```

#### **2. Default Value (Using `:-`)**
```bash
echo "${greeting:-Hello}"
# Output: Hello (greeting မရှိလို့ default value ထုတ်တယ်)
```

#### **3. String Length**
```bash
str="Hello World"
echo "${#str}"
# Output: 11
```

#### **4. Remove Substring (Using `%`)**
```bash
file="document.txt"
echo "${file%.txt}"
# Output: document (.txt ကို ဖျက်လိုက်တယ်)
```

---

### **နောက်ထပ် အသုံးဝင်မှု**
1. **Dynamic Text Replacement**
2. **Default Values**
3. **String Manipulation**: Length, Substring, Replacement
4. **Script Debugging**: Variables မဖြစ်နိုင်တဲ့အခြေအနေတွေကို handle လုပ်တာ

---

