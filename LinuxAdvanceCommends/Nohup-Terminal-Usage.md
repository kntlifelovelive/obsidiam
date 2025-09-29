
`nohup` ဆိုတာ **"no hang up"** လို့ အဓိပ္ပါယ်ရတဲ့ Linux/Unix command ဖြစ်ပါတယ်။ ဒီ command ကိုအသုံးပြုရင် **terminal ကိုပိတ်သွားရင်**တောင် command line မှာ run လုပ်နေတဲ့ program သို့ process ဟာ ဆက်လက် run နေလိမ့်မယ်။

### `nohup` ရဲ့ အဓိပ္ပါယ်
Linux မှာ terminal ကိုပိတ်သွားတဲ့အခါ မကြာခဏ **parent process** ဟာ **child process** တွေကို ပိတ်လိုက်ပြီး လုပ်ဆောင်နေတဲ့ tasks တွေကို မပြီးဆုံးခင် ပိတ်သွားနိုင်ပါတယ်။  
`nohup` ဟာ **SIGHUP (Signal Hang Up)** ဆိုတဲ့ signal ကို **ignore** လုပ်လိုက်တာကြောင့် terminal ပိတ်သွားရင်တောင် process ဆက်လက်လုပ်ဆောင်နိုင်စေပါတယ်။

---

### `nohup` သုံးပုံသုံးနည်း

1. **ပုံမှန်အသုံးပြုနည်း**  
```bash
nohup command &
```
`&` သည် **background** မှာ run လုပ်ဆောင်စေတဲ့ operator ပါ။  
**ဥပမာ**  
```bash
nohup python3 script.py &
```

- ဒီမှာ `script.py` ဟာ terminal ပိတ်သွားလည်း **background** မှ run နေလိမ့်မယ်။

---

2. **Output ကို redirect လုပ်ချင်ရင်**  
ပုံမှန်အားဖြင့် `nohup` ဟာ output ကို `nohup.out` ဖိုင်ထဲသို့သိမ်းပြီး **current directory** မှာ ထည့်ပေးပါတယ်။  
Output ကို ထိန်းချင်ရင်:  
```bash
nohup command > output.log 2>&1 &
```

**ဥပမာ**  
```bash
nohup python3 script.py > output.log 2>&1 &
```
- ဒီအတွက် output အားလုံး (errors + standard output) ကို `output.log` ဖိုင်ထဲသိမ်းပါတယ်။

---

3. **Process ကိုကြည့်ခြင်း**  
Process ရဲ့ **PID (Process ID)** ကို `ps` command နဲ့ကြည့်နိုင်ပါတယ်။  
```bash
ps aux | grep command
```

---

4. **Example**  
ဘယ်လိုသုံးရမလဲ ဆိုတာပြန်ပြီးစဉ်ကြည့်ရင်:
```bash
nohup sleep 300 &
```
- ဒီမှာ `sleep 300` ဆိုတာ **300 စက္ကန့်** စောင့်နေတဲ့ command ဖြစ်ပါတယ်။
- `nohup` သုံးလိုက်တော့ terminal ပိတ်သွားလည်း **background** မှ run နေလိမ့်မယ်။

---

### အကျဉ်းချုပ်  
`nohup` ကို **background task** တွေ run လုပ်ပြီး terminal ပိတ်သွားလည်း **process ပျက်မသွားစေချင်တဲ့အခါ** သုံးပါတယ်။

🔹 **အကြောင်းအရာများ**  
- Command run မပြီးခင် terminal ပိတ်ရင်လည်း ဆက်လက်လုပ်ဆောင်စေမယ်။  
- Output ကို `nohup.out` မှာသိမ်းသွားတယ် (သို့မဟုတ် output ကို redirect လုပ်လို့ရတယ်)။  

**Example:**  
```bash
nohup your_command > log_file.log 2>&1 &
```  
***Output file** ထဲမှာ အလုပ်သွားတာကို ကြည့်နိုင်ပါတယ်။*

---

### `nohup` Command မှတ်ချက်  

`nohup` ဆိုတာ **no hang up** ကိုဆိုလိုပြီး terminal ပိတ်သွားလည်း **process ဆက် run နေစေတဲ့ command** ဖြစ်ပါတယ်။

---

### **အသုံးချနည်းများ**  
1. **ပုံမှန်အသုံးပြုနည်း**  
```bash
nohup command &
```
- **Example:**  
```bash
nohup python3 script.py &
```
**Terminal ပိတ်သွားလည်း `script.py` ဆက် run နေလိမ့်မယ်။**

---

2. **Output ကို redirect လုပ်ချင်ရင်**  
Output နှင့် Error ကို file မှာသိမ်းဆည်းဖို့:  
```bash
nohup command > output.log 2>&1 &
```
- **Example:**  
```bash
nohup python3 script.py > output.log 2>&1 &
```
**အကြောင်းအရာအားလုံးကို `output.log` ဖိုင်ထဲမှာ သိမ်းပေးတယ်။**

---

3. **Process ကိုကြည့်ခြင်း**  
Run ဖြစ်နေတဲ့ process တွေကိုကြည့်ဖို့ `ps` command သုံးပါ။  
```bash
ps aux | grep command
```

---

4. **လွယ်ကူတဲ့ ဥပမာ**  
```bash
nohup sleep 300 &
```
- `sleep 300` ဆိုတဲ့ command ကို background မှ run နေစေပြီး terminal ပိတ်သွားလည်း ဆက်လုပ်ဆောင်မယ်။

---

### **အကျဉ်းချုပ်**  
🔹 `nohup` သည် terminal ပိတ်သွားလည်း process ပျက်မသွားအောင် run ဆက်လုပ်ပေးတယ်။  
🔹 Output ကို `nohup.out` file ထဲသိမ်းတယ်၊ မလိုချင်ရင် file ကို redirect လုပ်လို့ရတယ်။  

---

### **အရေးကြီးသော Command မှတ်ချက်**  
```bash
nohup your_command > log_file.log 2>&1 &
```
- **Process ကို background မှ run**  
- **Output နှင့် Error** ကို `log_file.log` ထဲသိမ်းထားနိုင်တယ်။**