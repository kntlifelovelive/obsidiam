
ဒီ Pattern 6 ကို User Input လက်ခံအောင် Python နဲ့ ပြောင်းပေးမယ်။  
ပြီးတော့ Bash Script ထဲမှာလည်း User Input နဲ့ ပြောင်းလို့ရအောင် Python ကိုခေါ်သုံးမယ်။  

---

### **Python Code (User Input ထည့်နိုင်တဲ့ Version)**  
```python
n = int(input("Enter the number of rows/columns: "))  
k = 1  

for x in range(1, n + 1):  
    for y in range(1, n + 1):  
        print("{:2d} ".format(k), end="")  
        k += 1  
    print()
```
#### **Output Example (User Input = 4)**
```
Enter the number of rows/columns: 4
 1  2  3  4  
 5  6  7  8  
 9 10 11 12  
13 14 15 16  
```

---

### **Bash Script (User Input နဲ့ Python ကိုခေါ်သုံးနိုင်အောင် ပြောင်း)**  
```bash
#!/bin/bash

read -p "Enter the number of rows/columns: " n
python3 - <<EOF
n = $n
k = 1

for x in range(1, n + 1):
    for y in range(1, n + 1):
        print("{:2d} ".format(k), end="")
        k += 1
    print()
EOF
```
#### **Bash Script ကို Run မယ်**
```bash
chmod +x pattern.sh  
./pattern.sh  
```
#### **Output Example (User Input = 3)**
```
Enter the number of rows/columns: 3
 1  2  3  
 4  5  6  
 7  8  9  
```

ဒီလိုနဲ့ **Python** နဲ့ **Bash Script** နှစ်မျိုးစလုံးမှာ User Input လက်ခံပြီး Pattern 6 ကို ရှင်းပြပေးလိုက်ပြီနော်!

---

Bash ထဲမှာ Python Code အလုပ်လုပ်တာက **Here Document (<<EOF ... EOF)** နဲ့ Python Interpreter (`python3 -`) ကို သုံးထားလို့ပါ။  
ဒီလိုလုပ်မယ်ဆိုရင် **Python Code ကို Bash Script ထဲမှာ Inline Script အနေနဲ့ ခေါ်သုံးနိုင်မယ်**။  

---

## **Step-by-Step ရှင်းပြချက်**  

### **1. Bash ထဲမှာ User Input လက်ခံတာ**  
```bash
read -p "Enter the number of rows/columns: " n
```
- `read -p` ကိုသုံးပြီး User Input ကို `$n` ထဲမှာ သိမ်းထားတယ်။  
- User က `5` လို့ထည့်မယ်ဆိုရင် `$n = 5` ဖြစ်မယ်။  

---

### **2. Bash က Python ကို Run ပေးတာ**  
```bash
python3 - <<EOF
    Python Code
EOF
```
- `python3 -` က Bash မှာ Python Interpreter ကို ခေါ်သုံးတဲ့ Command  
- `<<EOF ... EOF` ကို **Here Document** လို့ခေါ်ပြီး Python Code ကို Bash ထဲမှာ Embed (ထည့်သုံး) ခြင်းဖြစ်တယ်။  
- `EOF` ဆိုတာက **End of File Marker** တစ်ခု၊ ဒီအကြားက Code တွေကို Python Script အနေနဲ့ Run ပေးမယ်။  

---

### **3. Bash Variable (`$n`) ကို Python ထဲ ထည့်ပေးတာ**  
```python
n = $n
```
- Python မှာ Variable Assigning သည် `n = 5` ဆိုတဲ့ Format ကိုလိုချင်တယ်။  
- Bash မှာ `$n` ဆိုတာက **Bash Variable** ဖြစ်တာမို့ **Python မှာ Read လို့မရနိုင်ဘူး**။  
- ဒါကြောင့် `$n` ကို **Bash Variable -> Python Variable** ပြောင်းဖို့ `EOF` ထဲမှာ Direct Assign လုပ်တာ။  

---

## **Python မှာ ဘာဖြစ်သွားလဲ?**  
### **Bash Input (User က 4 ထည့်တယ်)**  
```bash
Enter the number of rows/columns: 4
```
### **Python Interpreter ထဲ Run ဖြစ်တဲ့ Code**  
```python
n = 4  # Bash မှာ ရလာတဲ့ Input ကို Python ထဲမှာ Assign
k = 1

for x in range(1, n + 1):
    for y in range(1, n + 1):
        print("{:2d} ".format(k), end="")
        k += 1
    print()
```
- `n = 4` ဖြစ်သွားတာကြောင့် Python Code က `4x4` Pattern ထွက်လာမယ်။  

---

## **အကျဉ်းချုပ်**  
✔ **Bash Variable** (`$n`) ကို Python ထဲမှာ Assign လုပ်မယ်။  
✔ `python3 - <<EOF ... EOF` ကို သုံးပြီး **Python Code ကို Bash ထဲ Embed & Run** လုပ်မယ်။  
✔ **Python Interpreter** က Bash Variable ကို ချက်ချင်း Assign လုပ်မယ်။  

ဒါကြောင့် **Bash ထဲမှာ Python Code ကို အလုပ်လုပ်စေဖို့ `<<EOF ... EOF` နဲ့ Python Interpreter ကို သုံးလိုက်တာ** ပါ။  

---

