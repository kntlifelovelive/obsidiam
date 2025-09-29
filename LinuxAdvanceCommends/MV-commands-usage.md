
## How to Use “mv” Command in Linux

---

| **No.** | **Command**                                    | **Description**                                                                                           | **Example**                                                                                                                                                  |
|---------|------------------------------------------------|-----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1       | `mv <source> <destination>`                    | ဖိုင်ကို ရွှေ့ရန်။                                                                                        | `mv file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာရွှေ့ပါ)                                                                  |
| 2       | `mv <source1> <source2> ... <destination>`      | များသောဖိုင်များကို ရွှေ့ရန်။                                                                            | `mv file1.txt file2.txt /home/user/Documents/` <br> (file1.txt နှင့် file2.txt ကို /home/user/Documents/ မှာရွှေ့ပါ)                                      |
| 3       | `mv <source> <destination>`                   | ဖိုင်/ဒိုက်ရက်တိုးရီကို အမည်ပြောင်းရန်                                                                        | `mv file1.txt newfile.txt` <br> (file1.txt ကို newfile.txt အဖြစ် အမည်ပြောင်းပါ)                                                                              |
| 4       | `mv -i <source> <destination>`                 | ဖိုင်ကို ရွှေ့တဲ့အခါ overwrite လုပ်မလားဟု စစ်ပြီး သိရှိရန် (interactive mode)                             | `mv -i file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာ overwrite လုပ်မလားဟု စစ်ပါ)                                         |
| 5       | `mv -f <source> <destination>`                 | ဖိုင်ကို overwrite လုပ်သည့်အခါ confirmation မပေးဘဲ forced အနေနဲ့ overwrite လုပ်ရန်                     | `mv -f file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာ overwrite လုပ်ပါ)                                                      |
| 6       | `mv -u <source> <destination>`                 | ဖိုင်အသစ်များကိုသာ ရွှေ့ရန် (source file သည် destination ထဲမှာ မရှိရင်သာ ရွှေ့ပါ)                      | `mv -u file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာ ရှိသည့်ဖိုင်များကို ထည့်ခြင်းမလုပ်ပဲ အသစ်ရောက်သော file တွေကိုသာ ရွှေ့ပါ) |
| 7       | `mv -v <source> <destination>`                 | ဖိုင် ရွှေ့မှုအား visual အနေဖြင့် ပြသရန် (verbose mode)                                                  | `mv -v file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာ visual အနေဖြင့် ပြသပေးပါ)                                        |
| 8       | `mv --backup=<mode> <source> <destination>`    | ဖိုင်ကို overwrite လုပ်ချိန်တွင် backup ဖိုင်အဖြစ် သိမ်းထားရန်                                              | `mv --backup=numbered file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာ backup ဖိုင်အဖြစ် သိမ်းပါ)                         |
| 9       | `mv -n <source> <destination>`                 | ဖိုင်ကို overwrite မလုပ်ပဲ ရွှေ့ပေးရန် (no clobber)                                                        | `mv -n file1.txt /home/user/Documents/` <br> (file1.txt ကို /home/user/Documents/ မှာ overwrite မလုပ်ပဲ ရွှေ့ပါ)                                            |

### **အဓိကပါဝင်သော options**
- `-i` : အမည်ပြောင်းပြီး overwrite လုပ်မလားဆိုတာ confirm မေးပါ။
- `-f` : ဤ option သည် overwrite ကို forced လုပ်ပါ။
- `-u` : source ဖိုင်၏ timestamp ဟာ destination ရှိသော file ထက် အသစ်ရင်သာ overwrite လုပ်ပါ။
- `-v` : ဖိုင်ကို overwrite လုပ်ခြင်း၊ ရွှေ့ခြင်းအား ပြသပါ။
- `-n` : မည်သည့်ဖိုင်ကို overwrite မလုပ်ပဲ ရွှေ့ပါ။

---

### **1. ဖိုင်ကို ရွှေ့ခြင်း**

ဖိုင်တစ်ခုကို တစ်နေရာမှ တခြားနေရာသို့ ရွှေ့ခြင်း။

```bash
mv file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` ဖိုလ်ဒါထဲတွင် ရွှေ့ပါ။

### **2. အမည်ပြောင်းခြင်း**

ဖိုင်တစ်ခု၏ အမည်ကို ပြောင်းခြင်း။

```bash
mv oldname.txt newname.txt
```
> **ဖော်ပြချက်**: `oldname.txt` ကို `newname.txt` အဖြစ် အမည်ပြောင်းပါ။

### **3. များသောဖိုင်များကို ရွှေ့ခြင်း**

အမျိုးမျိုးသော ဖိုင်များကို တစ်ပြိုင်နက်မှာ ရွှေ့ခြင်း။

```bash
mv file1.txt file2.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` နှင့် `file2.txt` ကို `/home/user/Documents/` မှာ ရွှေ့ပါ။

### **4. `-i` option (interactive mode) အသုံးပြုခြင်း**

ဖိုင်ကို overwrite လုပ်မလားဟု သိရှိရန် ဖတ်ခြင်း။

```bash
mv -i file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` ရွှေ့ရာတွင် overwrite လုပ်မလား ဆိုတာ confirm လုပ်မည်။

### **5. `-f` option (force mode) အသုံးပြုခြင်း**

Overwrite ပြုလုပ်ရန် confirmation မေးမီ အလိုအလျောက် အားလုံးကို force လုပ်ခြင်း။

```bash
mv -f file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` မှာ မေးမြန်းခြင်းမရှိပဲ overwrite လုပ်မည်။

### **6. `-u` option (update) အသုံးပြုခြင်း**

Source ဖိုင်၏ timestamp သည် destination ရှိသော file ထက် အသစ်ဖြစ်လျှင်သာ overwrite လုပ်ခြင်း။

```bash
mv -u file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` မှာ overwrite လုပ်မည်၊ သို့သော် timestamp အသစ်များသာ overwrite လုပ်ပါ။

### **7. `-v` option (verbose mode) အသုံးပြုခြင်း**

ရွှေ့လိုက်တဲ့ ဖိုင်များကို visual အနေနဲ့ ပြသခြင်း။

```bash
mv -v file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` ရွှေ့ရာတွင် process ကို ပြသပါ။

### **8. `--backup` option အသုံးပြုခြင်း**

ဖိုင်ကို overwrite လုပ်ပါက backup ဖိုင်အဖြစ် သိမ်းပါ။

```bash
mv --backup=numbered file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` မှာ overwrite လုပ်ပြီး၊ ပြီးနောက်မှာ backup ဖိုင်အဖြစ် သိမ်းမည်။

### **9. `-n` option (no clobber) အသုံးပြုခြင်း**

ဖိုင်ကို overwrite မလုပ်ပဲ ရွှေ့ပါ။

```bash
mv -n file1.txt /home/user/Documents/
```
> **ဖော်ပြချက်**: `file1.txt` ကို `/home/user/Documents/` မှာ overwrite မလုပ်ပဲ ရွှေ့ပါ။

### **အခြားနမူနာများ**

- **ဖိုင်များကို ဖိုလ်ဒါသစ်သို့ ရွှေ့ခြင်း**:

```bash
mv file1.txt file2.txt /home/user/new_folder/
```
> **ဖော်ပြချက်**: `file1.txt` နှင့် `file2.txt` ကို `/home/user/new_folder/` ဖိုလ်ဒါသစ်ထဲတွင် ရွှေ့ပါ။

- **အခြားသော ဖိုင်များကို တစ်ခုချင်းစီ အမည်ပြောင်းခြင်း**:

```bash
mv file1.txt /home/user/old_file.txt
mv file2.txt /home/user/new_file.txt
```
> **ဖော်ပြချက်**: `file1.txt` နှင့် `file2.txt` ကို 각각 အမည်ပြောင်းခြင်းဖြင့် `/home/user/` သို့ ရွှေ့ပါ။

