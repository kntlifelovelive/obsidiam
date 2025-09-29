
# Escape Characters-in-Bash

**Escape Characters** ဆိုတာက special characters တွေကို **Bash** မှာ သက်မှတ်ထားတဲ့ အဓိပ္ပာယ်တွေနဲ့ အသုံးပြုနိုင်ဖို့ **\ (backslash)** သုံးပြီး အထူးသတ်မှတ်ချက်ပေးထားတာတွေ ဖြစ်ပါတယ်။ အဓိကအားဖြင့် **text formatting** ၊ **special characters** သုံးဖို့ အသုံးဝင်ပါတယ်။


---

### **Escape Characters မျိုးစုံနှင့် သုံးပုံသုံးနည်း**

| Escape Character | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `\n`             | **Newline**: အသစ်တန်းထွက်ရေးခြင်း။                                      |
| `\t`             | **Tab**: တစ်ခါ tab ဝင်ရေးခြင်း။                                          |
| `\\`             | **Backslash**: Backslash ကို ထွက်အောင်ရေးခြင်း။                          |
| `\'`             | **Single Quote**: Single quote `'` ကို ထွက်အောင်ရေးခြင်း။               |
| `\"`             | **Double Quote**: Double quote `"` ကို ထွက်အောင်ရေးခြင်း။               |
| `\a`             | **Alert**: Bell sound (သံကြိုးတီးသံဖြစ်စေတယ်၊ Terminal ပေါ်မှာ သိမ်းမှတ်ဖြစ်နိုင်)။|
| `\b`             | **Backspace**: Backspace effect (ဂဏန်းတွေရှေ့ဆုံးကိုဖျက်ပစ်တယ်)။         |
| `\r`             | **Carriage Return**: လက်ရှိတန်းရဲ့ အစကိုပြန်သွားစေတယ်။                   |

---

### **ဥပမာများ**

#### **1. Newline (`\n`)**
```bash
echo -e "Hello\nWorld"
# Output:
# Hello
# World
```

#### **2. Tab (`\t`)**
```bash
echo -e "Hello\tWorld"
# Output:
# Hello    World
```

#### **3. Backslash (`\\`)**
```bash
echo -e "This is a backslash: \\"
# Output:
# This is a backslash: \
```

#### **4. Single Quote (`\'`)**
```bash
echo -e 'I\'m learning Bash!'
# Output:
# I'm learning Bash!
```

#### **5. Double Quote (`\"`)**
```bash
echo -e "She said, \"Hello!\""
# Output:
# She said, "Hello!"
```

#### **6. Alert (`\a`)**
```bash
echo -e "\a"
# Output:
# (Terminal will produce a beep sound if supported)
```

#### **7. Carriage Return (`\r`)**
```bash
echo -e "12345\rABC"
# Output:
# ABC45
```

---

### **Escape Characters သုံးနည်းများ**
1. **`echo` Command နဲ့ `-e` Option**
   - Escape characters တွေထွက်အောင် **-e** flag ကို သုံးရမယ်။
   ```bash
   echo -e "Line 1\nLine 2"
   ```

2. **String Variables**
   - Escape characters ကို string variables တွေထဲမှာသုံးလို့ရတယ်။
   ```bash
   msg="Hello\nWorld"
   echo -e $msg
   ```

3. **Special Scripts (e.g., Formatting Logs, Alerts)**
   - Log file တွေမှာ စာလုံးတွေကို ပြင်ဆင်ရေးသားဖို့ အသုံးဝင်တယ်။

---

### **အသုံးဝင်ပုံ**
- **Text Formatting**: Newline, Tabs, etc.
- **Special Symbols** ထွက်အောင်ရေးဖို့: `\`, `'`, `"`, etc.
- **Script Logs**: Logs တွေကို ပိုမိုရှင်းလင်းအောင် ပြင်ဆင်ရေးသားခြင်း။
- **Debugging**: Alerts သုံးပြီး error tracking ရှာဖွေခြင်း။
--- 