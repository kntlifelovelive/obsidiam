
# `seq` command 

`seq` command ကို Linux CLI မှာ **sequence of numbers** တွေထုတ်ဖို့သုံးပါတယ်။  
Format ပုံစံကတော့  
```bash
seq [OPTION]... FIRST [INCREMENT] LAST
```
- **FIRST** → စကန့်ထုတ်မယ့် နံပါတ်  
- **INCREMENT** → တိုးမယ့်တန်ဖိုး (default `1`)  
- **LAST** → နောက်ဆုံး နံပါတ်  

---

## 1️⃣ Basic Usage  
```bash
seq 5
```
👉 **Output:**  
```
1
2
3
4
5
```
🔹 Default အနေနဲ့ `seq` က **1 မှစပြီး 1 တိုးပြီးသွားမယ်**။  

---

## 2️⃣ First & Last Number ထည့်ခြင်း  
```bash
seq 3 8
```
👉 **Output:**  
```
3
4
5
6
7
8
```
🔹 `3` မှစပြီး `8` ထိ **1 တိုးပြီး** ရိုက်ထုတ်မယ်။  

---

## 3️⃣ Increment တစ်ခုစီ သတ်မှတ်ခြင်း  
```bash
seq 2 2 10
```
👉 **Output:**  
```
2
4
6
8
10
```
🔹 `2` မှစပြီး **2 တိုး** သွားမယ်။  

---

## 4️⃣ Backward Sequence (Descending Order)  
```bash
seq 10 -2 2
```
👉 **Output:**  
```
10
8
6
4
2
```
🔹 Negative Increment (`-2`) သုံးလို့ `10 → 2` ထိ နောက်ပြန်သွားမယ်။  

---

## 5️⃣ Number Formatting  
- **Zero Padding (Leading Zeros)**  
```bash
seq -w 1 5
```
👉 **Output:**  
```
01
02
03
04
05
```
🔹 `-w` (equal width) သုံးလို့ **zero padding** လုပ်မယ်။  

- **Floating Point Numbers**  
```bash
seq -f "%.2f" 1 0.5 3
```
👉 **Output:**  
```
1.00
1.50
2.00
2.50
3.00
```
🔹 `-f "%.2f"` ဆိုတာ **floating point 2 decimal places** ထည့်တာ။  

---

## 6️⃣ Output ကို Single Line နဲ့ Print  
```bash
seq -s ", " 1 5
```
👉 **Output:**  
```
1, 2, 3, 4, 5
```
🔹 `-s` (separator) သုံးပြီး **comma-separated output** လုပ်နိုင်တယ်။  

---

## 7️⃣ Loop တစ်ခုနဲ့ပေါင်းသုံးခြင်း  
```bash
for i in $(seq 1 5); do
    echo "Number: $i"
done
```
👉 **Output:**  
```
Number: 1
Number: 2
Number: 3
Number: 4
Number: 5
```
🔹 `seq` ကို loop ထဲထည့်ပြီး **bash script** တွေမှာသုံးလို့ရတယ်။  

---

### ✅ Summary
- `seq 5` → **1 → 5**  
- `seq 3 8` → **3 → 8**  
- `seq 2 2 10` → **2 တိုးပြီး**  
- `seq 10 -2 2` → **နောက်ပြန် 2 လျော့ပြီး**  
- `seq -w 1 5` → **Zero Padding**  
- `seq -f "%.2f" 1 0.5 3` → **Floating Point**  
- `seq -s ", " 1 5` → **Comma-Separated Output**  
- `for i in $(seq 1 5); do echo "Number: $i"; done` → **Loop Usage**  

Linux CLI မှာ `seq` ကို **number list generate** လုပ်ဖို့ အရမ်းအသုံးဝင်ပါတယ်။😊

---

### **`seq` Command Options with Examples**  

`seq` မှာ အသုံးများတဲ့ **options** တွေကို **Table** နဲ့ ပြထားပေးပါမယ်။  
တစ်ခုချင်းစီအတွက် **Example** တွေလည်း ပါပါတယ်။  

---

### **1️⃣ `seq` Command Options Table**  

| **Option** | **Description** | **Example** | **Output** |
|------------|---------------|-------------|------------|
| `-w` | Zero-padding (Equal Width) | `seq -w 1 5` | `01 02 03 04 05` |
| `-f` | Format numbers (Floating point, String) | `seq -f "%.2f" 1 0.5 3` | `1.00 1.50 2.00 2.50 3.00` |
| `-s` | Custom separator | `seq -s ", " 1 5` | `1, 2, 3, 4, 5` |
| `--help` | Show help menu | `seq --help` | `seq [OPTION]... FIRST [INCREMENT] LAST` |
| `--version` | Show version info | `seq --version` | `seq (GNU coreutils) 8.30` |

---

### **2️⃣ `seq` Options with Details & Examples**

#### **1. `-w` → Zero-Padding (Equal Width)**
```bash
seq -w 1 10
```
👉 **Output:**
```
01
02
03
04
05
06
07
08
09
10
```
🔹 `-w` သုံးလိုက်တဲ့အခါ **number width တူအောင် zero-padding** ထည့်မယ်။

---

#### **2. `-f` → Format (Floating Point, String)**
```bash
seq -f "%.2f" 1 0.5 3
```
👉 **Output:**
```
1.00
1.50
2.00
2.50
3.00
```
🔹 `-f "%.2f"` ဆိုတာ **floating-point format (2 decimal places)** သုံးတာ။

---

#### **3. `-s` → Custom Separator**
```bash
seq -s ", " 1 5
```
👉 **Output:**
```
1, 2, 3, 4, 5
```
🔹 `-s` (separator) သုံးပြီး **comma-separated output** ပြုလုပ်နိုင်တယ်။

---

#### **4. `--help` → Help Menu**
```bash
seq --help
```
👉 **Output (Part of Help Menu):**
```
Usage: seq [OPTION]... FIRST [INCREMENT] LAST
  -f, --format=FORMAT  use printf style floating-point format
  -s, --separator=STRING  use STRING to separate numbers
  -w, --equal-width    equalize width by padding with leading zeroes
```
🔹 **All available options** တွေကို ပြသပေးမယ်။

---

#### **5. `--version` → Show Version**
```bash
seq --version
```
👉 **Output:**
```
seq (GNU coreutils) 8.30
```
🔹 `seq` command ရဲ့ **version info** ကို ပြမယ်။  

---

### **✅ Summary**
- **`-w`** → **Zero-padding (01, 02, 03...)**  
- **`-f`** → **Floating point format (1.00, 1.50...)**  
- **`-s`** → **Separator (1, 2, 3...)**  
- **`--help`** → **Help menu**  
- **`--version`** → **Show version**  

 **`seq` ကို CLI scripting, looping, formatting, and number generation အတွက် အသုံးများတယ်။**

---

