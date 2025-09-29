
## **`sed` Commands တွေ**  
`sed` မှာ အသုံးဝင်တဲ့ command တွေ အများကြီးရှိပါတယ်။ အဓိက အသုံးပြုလေ့ရှိတဲ့ command တွေကို အောက်မှာ ရှင်းပြပေးပါတယ်။

---

### **1. Substitution Command (`s`)**  
စာသားတစ်ခုကို အခြားစာသားနဲ့ အစားထိုးဖို့အတွက်:  
```bash
sed 's/old_text/new_text/' file.txt
```
- `s`: Substitute command  
- Example:
  ```bash
  echo "Hello World" | sed 's/World/Everyone/'
  ```
  Output: `Hello Everyone`

---

### **2. Deletion Command (`d`)**  
ထည့်လိုင်းတွေကို ဖျက်ပစ်ဖို့:  
```bash
sed 'Nd' file.txt
```
- `N`: ဖျက်လိုတဲ့လိုင်းနံပါတ်  
- Example:
  ```bash
  sed '2d' file.txt
  ```
  ဒုတိယလိုင်းကို ဖျက်ပစ်မယ်။

---

### **3. Print Command (`p`)**  
သတ်မှတ်လိုင်းတွေကိုသာ output မှာ ပြချင်ရင်:  
```bash
sed -n 'Np' file.txt
```
- `-n`: Quiet mode (output ကို silence လုပ်မယ်)  
- `Np`: N-th line ကိုပဲ print လုပ်မယ်  
- Example:
  ```bash
  sed -n '3p' file.txt
  ```
  တတိယလိုင်းကိုပဲ ပြမယ်။

---

### **4. Append Command (`a`)**  
လိုင်းတစ်ခုရဲ့နောက်မှာ စာသားထည့်သွင်းဖို့:  
```bash
sed 'Na new_text' file.txt
```
- `N`: Target လိုင်းနံပါတ်  
- Example:
  ```bash
  sed '3a This is new text' file.txt
  ```
  တတိယလိုင်းနောက်မှာ `This is new text` ထည့်မယ်။

---

### **5. Insert Command (`i`)**  
လိုင်းတစ်ခုရဲ့မရှေ့မှာ စာသားထည့်သွင်းဖို့:  
```bash
sed 'Ni new_text' file.txt
```
- Example:
  ```bash
  sed '1i This is inserted text' file.txt
  ```
  ပထမလိုင်းရှေ့မှာ `This is inserted text` ထည့်မယ်။

---

### **6. Replace Specific Line (`c`)**  
လိုင်းတစ်ခုကို အခြားစာသားနဲ့ အစားထိုးဖို့:  
```bash
sed 'Nc new_text' file.txt
```
- Example:
  ```bash
  sed '2c Replaced text' file.txt
  ```
  ဒုတိယလိုင်းကို `Replaced text` နဲ့ အစားထိုးမယ်။

---

### **7. Write to a File (`w`)**  
အထွက်ကို သတ်မှတ်ဖိုင်ထဲသိမ်းဖို့:  
```bash
sed 'w output.txt' file.txt
```
- Example:
  ```bash
  sed -n '1,3p;w output.txt' file.txt
  ```
  ပထမမှ တတိယလိုင်းတွေကို `output.txt` ဖိုင်ထဲသိမ်းမယ်။

---

### **8. Multiple Commands (`-e`)**  
Command အများကြီးကို တပြိုင်တည်း ဆောင်ရွက်ဖို့:  
```bash
sed -e 'command1' -e 'command2' file.txt
```
- Example:
  ```bash
  sed -e 's/old/new/' -e '2d' file.txt
  ```
  စာသားကို အစားထိုးပြီး ဒုတိယလိုင်းကို ဖျက်မယ်။

---

### **9. In-Place Editing (`-i`)**  
Original file ကို တိုက်ရိုက်ပြင်မယ်:  
```bash
sed -i 's/old_text/new_text/' file.txt
```
- Example:
  ```bash
  sed -i 's/Linux/Ubuntu/' file.txt
  ```

---

### **10. Addressing Ranges**  
လိုင်းအပိုင်းအချို့ကို သီးသန့်ပြင်ချင်ရင်:  
- **By Line Numbers**  
  ```bash
  sed '1,3s/old/new/' file.txt
  ```
  ပထမမှ တတိယလိုင်းထိ အစားထိုးမယ်။

- **Using Patterns**  
  ```bash
  sed '/pattern1/,/pattern2/d' file.txt
  ```
  `pattern1` နှင့် `pattern2` ကြားရှိလိုင်းတွေကို ဖျက်မယ်။

---

### **11. Use with Regex**  
`sed` မှာ Regular Expressions (regex) ကို အသုံးပြုနိုင်ပါတယ်။  
```bash
sed 's/[0-9]/#/g' file.txt
```
- စာရွက်ထဲမှာ အားလုံးနဲ့တိုက်ဆိုင်တဲ့ အရေအတွက်တွေကို `#` နဲ့ အစားထိုးမယ်။

---

