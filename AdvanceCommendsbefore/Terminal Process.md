

### **Terminal ကနေ Nautilus လို Background Process ဖွင့်ပြီး ပြန်ထွက်လိုရတဲ့ CLI**

---

#### **1. Background Mode နဲ့ Run ပြီး Terminal ကနေ တိုက်ရိုက် ထွက်ချင်ရင်**  
**`nohup`** နဲ့ **`&`** ကို အသုံးပြုပါ။  

```bash
nohup nautilus . & disown
```

---

### **Explanation**  
1. **`nohup`** ➡ Terminal က **ထွက်သွားရင်** ပဲ process ကို ဆက်လက် run ဖြစ်စေတယ်။  
2. **`&`** ➡ Command ကို background mode မှာ run လုပ်တယ်။  
3. **`disown`** ➡ Background process ကို Terminal ကို **detach** (ဖြုတ်ပစ်) လုပ်တယ်။  
   - နောက်မှ Terminal က ထွက်သွားရင် process မရပ်ဘူး။

---

### **Step-by-Step Summary**  
1. **Command ကို Background မှာ Run နဲ့ Detach လုပ်ပါ**  
   ```bash
   nohup nautilus . & disown
   ```

2. **Terminal ကနေ ထွက်လိုရင်**  
   ```bash
   exit
   ```

---

### **Results**  
- Nautilus က Terminal ကနေ independent ဖြစ်သွားပြီး **background** မှာ ဆက်လက်လုပ်နေမယ်။  
- Terminal ကနေ **exit** ဖြင့် ထွက်သွားလို့ရတယ်။

---

### **Short Note**  
```bash
nohup nautilus . & disown && exit

```
➡ **Background Process** ဆက်လုပ်ပြီး Terminal ကနေ **ထွက်နိုင်** သွားမယ်။

---
