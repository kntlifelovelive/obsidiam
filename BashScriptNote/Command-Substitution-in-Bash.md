
**Command Substitution** ဆိုတာက Shell ထဲမှာ Command တစ်ခုရဲ့ **Output ကို Variable တစ်ခုအနေနဲ့သိမ်းခြင်း** သို့မဟုတ် **အသုံးပြုနေတဲ့ Command ထဲကို Output ထည့်ခြင်း** လုပ်ပေးတဲ့ နည်းလမ်းတစ်ခုပါ။ 

---

## **Command Substitution Syntax**
Command Substitution ကို Shell မှာ syntax နှစ်မျိုးနဲ့ အသုံးပြုနိုင်ပါတယ်။

1. **$(command)** (modern style)
2. **`command`** (backtick style, legacy)

**Recommended**: `$(command)` ဟာ ယခင်စတိုင်ဖြစ်တဲ့ Backtick (`command`) ထက် အသုံးပြုရလွယ်ကူပြီး error handling ပိုကောင်းတယ်။

---

## **Command Substitution ရဲ့ လုပ်ဆောင်မှု**
1. **Command ကို Run လုပ်တယ်**။
2. **Output ကို Return ပြန်တယ်**။
3. **Output ကို Variable ထဲသို့ သိုလှောင်နိုင်တယ်** သို့မဟုတ် **Command ထဲမှာ Direct ပြန်သုံးနိုင်တယ်**။

---

## **Examples of Command Substitution**

#### **1. Simple Command Substitution**
```bash
date=$(date)
echo "Today is: $date"
# Output: Today is: <current date>
```

#### **2. Nested Command**
```bash
files=$(ls | wc -l)
echo "Number of files: $files"
# Output: Number of files: <file count>
```

#### **3. Using in a Command**
```bash
echo "This script is running on: $(uname -s)"
# Output: This script is running on: Linux
```

---

## **Command Substitution vs Variable Expansion**
| Feature                | Command Substitution                  | Variable Expansion          |
|-------------------------|---------------------------------------|-----------------------------|
| **Purpose**            | Command Output ကို သုံးတယ်           | Variable Value ကို သုံးတယ်     |
| **Syntax**             | `$(command)` or ``command``          | `$VAR` or `${VAR}`          |
| **Example**            | `$(date)` for current date           | `$HOME` for home directory |

---

## **Multiple Usages**
1. **Dynamic File Creation**
```bash
filename="backup_$(date +%Y-%m-%d).tar.gz"
echo $filename
# Output: backup_<current-date>.tar.gz
```

2. **Loop ထဲမှာ အသုံးပြုခြင်း**
```bash
for file in $(ls *.txt); do
    echo "Processing $file"
done
# Output: .txt files list processing
```

3. **Math Operations**
```bash
result=$(expr 5 + 10)
echo $result
# Output: 15
```

---

Command Substitution က **Automation** တွေမှာ အထောက်အကူဖြစ်လို့ ပိုမိုလုပ်ဆောင်နိုင်တဲ့ Script တွေ ရေးဖို့ပါ။