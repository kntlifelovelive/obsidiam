
---

#  **`clear` Command – Clear the Terminal Screen**

-   **Usage:** `clear`  
-    **Full form meaning:** _Clear terminal display_  
-     **Purpose:** Terminal screen ပေါ်က previous output တွေကို **ရှင်းလင်းပြီး blank screen** လုပ်ပေးတယ်။

### **4 Practical Examples of `clear` Command**
### 1.**Basic clear command**

```bash
clear
```

==>  Terminal screen ထဲက အကုန်လုံးကို ဖျက်ပြီး blank ဖြစ်သွားတယ်။  
(ကောင်ထဲက history မဖျက်ပါ — scroll up လုပ်ရင် မျက်နှာဖုံးထဲမှာနေရာအရင် command တွေကရှိနေတတ်တယ်။)


### 2. **Using keyboard shortcut**

==>  **Shortcut:**

```
Ctrl + L
```

==> `clear` command နဲ့တူညီတဲ့ function — **quickly clean screen** လုပ်တယ်။


### 3. **Use `reset` command**

```bash
reset
```

==> ဒီဟာက `clear`  stronger —  screen ကိုပဲ မရှင်းဘဲ **terminal settings ကိုပါ reset** လုပ်ပေးတယ်။  
တခါတလေ encoding error, color mess ဖြစ်တဲ့အခါ ဒီဟာ အသုံးဝင်တယ်။

### 4. **Combine with other commands**

```bash
ls; clear
```

==> ပထမမှာ `ls` နဲ့ directory contents ပြပြီး  
နောက်ထပ် **တန်းရှင်းချင်ရင် `clear`** သုံးတယ်။


```bash
clear && echo "Screen cleared successfully!"
```

==> Screen ရှင်းပြီး confirm message ပြတယ်။

---

##  **Quick Summary Table**

|Command|Description|Shortcut|
|---|---|---|
|`clear`|Clear terminal screen|None|
|`Ctrl + L`|Shortcut to clear screen|✅|
|`reset`|Clear screen + reset terminal settings|⚙️|
|`ls; clear`|Combine with other commands|🧩|

---

###  **Extra Tip**

တခါတလေ script ထဲမှာ command မသိအောင် clean ဖို့လိုရင်

```bash
clear > /dev/null 2>&1
```

==> Output မပေါ်အောင် clean silently လုပ်ပေးတယ်။

---