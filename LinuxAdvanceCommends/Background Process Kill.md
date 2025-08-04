
---

1. **Background Process Kill** - ပေါ်ပြီဆိုတာနဲ့ kill လုပ်တာကို အဓိကပြထားတယ်
2. **Terminate Background Processes** - Background မှာ run နေသမျှကို ပိတ်သတ်ခြင်း
3. **Kill Multiple Processes** - Process အများကြီးကို တစ်ချိန်တည်းပစ်သတ်ခြင်း
4. **Bulk Process Termination** - Process အုပ်စုကို တစ်ချိန်တည်းပစ်ခြင်း
5. **Batch Kill Processes** - Process တွေကို အစုလိုက်ပိတ်သတ်ခြင်း
6. **Mass Process Kill** - Process အများကြီးကို တစ်ပြိုင်တည်းပိတ်သတ်ခြင်း
7. **Kill All Matching Processes** - Name နဲ့ကိုက်ညီသမျှအားလုံးကို ပိတ်သတ်ခြင်း

---


### **pgrep Command  ?**

`pgrep` ဆိုတာက **process ID (PID)** ကို ရှာဖွေရာမှာ အသုံးပြုတဲ့ command တစ်ခုပဲဖြစ်ပါတယ်။  
Process အမည် (name)၊ pattern၊ သတ်မှတ်ထားသော option များကို အသုံးပြုပြီး ရှာဖွေနိုင်ပါတယ်။

---

##  **Syntax**

```bash
pgrep [options] pattern
```

---

## 🗂 **အသုံးများသော Options များ**

|Option|အဓိပ္ပါယ်|
|---|---|
|`-f`|Full command line ကို ရှာဖွေပါသည်|
|`-l`|PID နှင့် process name ကို တွဲပြီးပြသည်|
|`-x`|အတိအကျ process name ကို ပေးထားမှပြသည်|
|`-c`|အစီရင်ခံချက်အနေဖြင့် ပေါင်းအရေအတွက်ကိုပြသည်|
|`-n`|နောက်ဆုံးစ (newest) process ကို ပြသည်|
|`-o`|အဟောင်းဆုံး (oldest) process ကို ပြသည်|
|`-d`|PID များအကြား separator ကို သတ်မှတ်သည်|

---

##  **Usage Examples**

###  **1. ပုံမှန် Process ID ရှာဖွေခြင်း**

```bash
pgrep mpv
```

**Output:**

```
12345
```

 **Output :** `mpv` ဆိုတဲ့ process ရဲ့ PID ကို ပြတာပါ။

---

###  **2. Process Name နဲ့ PID တွဲပြီး ပြခြင်း (-l)**

```bash
pgrep -l mpv
```

**Output:**

```
12345 mpv
```

 **Output :** PID နံပါတ်နဲ့ Process Name ကို အတူတကွ ပြပါတယ်။

---

### **3. Process Name တိတိကျကျ ပြခြင်း (-x)**

```bash
pgrep -x mpv
```

 **Output :** `mpv` ဆိုတဲ့ အမည်နဲ့ တိတိကျကျ ပြတာပါ။

---

###  **4. Command Line အပြည့်အစုံ ပြခြင်း (-f)**

```bash
pgrep -fl mpv
```

**Output:**

```
12345 /usr/bin/mpv --no-video --audio-display=no song.mp3
```

  Command line arguments အပြည့်အစုံနဲ့ process name ကို ပြပေးတယ်။

---

### **5. နောက်ဆုံးစ (Newest) Process ကို ပြခြင်း (-n)**

```bash
pgrep -n mpv
```

  `mpv` process တွေထဲက နောက်ဆုံးစထားတဲ့ PID ကိုပြတယ်။

---

###  **6. အဟောင်းဆုံး (Oldest) Process ကို ပြခြင်း (-o)**

```bash
pgrep -o mpv
```

 **Output** `mpv` process တွေထဲက အဟောင်းဆုံး PID ကို ပြတယ်။

---

###  **7. Process အရေအတွက်ကို စာရင်းပြခြင်း (-c)**

```bash
pgrep -c mpv
```

**Output:**

```
2
```

 **Output** `mpv` process ရဲ့ စုစုပေါင်း အရေအတွက်ကို ပြတယ်။

---

###  **8. PID များအကြား Separator သတ်မှတ်ခြင်း (-d)**

```bash
pgrep -d, mpv
```

**Output:**

```
12345,23456
```

 **Output :** PID များကို comma (`,`) နဲ့ ခွဲပြပါတယ်။

---

## **Real-World Usage Example**

1. **`mpv` Process ရှာပြီး kill လုပ်ခြင်း**
    
    ```bash
    kill $(pgrep mpv)
    ```
    
    **အဓိပ္ပါယ်:** `pgrep` နဲ့ `mpv` ရဲ့ PID ကို ရှာပြီး kill command နဲ့ ပိတ်ပစ်တာပါ။
    
2. **Full Command Line နဲ့ Process ရှာဖွေခြင်း**
    
    ```bash
    pgrep -fl "mpv --no-video"
    ```
    
     **အဓိပ္ပါယ်:** `mpv --no-video` အပြည့်အစုံနဲ့ run နေတဲ့ process ကို ရှာတယ်။
    

---

##  **Tips**

- `pgrep` နဲ့ တူတဲ့ command တစ်ခုက `pidof` ပါ။
    
    ```bash
    pidof mpv
    ```
    
     **အဓိပ္ပါယ်:** `mpv` ရဲ့ PID ကို ရှာတယ်။

---

#### `pkill` command ကတော့ **process တွေကို အမည်နဲ့တည်းဟုတ်မှန်းစစ်ပြီး ပိတ်ပစ်ဖျက်သိမ်း**တာလေးပါ။  

---

##  **pkill Command Syntax**

```bash
pkill [options] pattern
```

---

## **Options အကျဉ်းချုပ်**

|Option|အဓိပ္ပါယ်|
|---|---|
|`-f`|Full command line ကို ရှာဖွေပြီး ပစ်သည်|
|`-9`|Force kill (SIGKILL) နဲ့ ပစ်သည်|
|`-u`|သတ်မှတ်ထားသော user အတွက်ပစ်သည်|
|`-x`|အတိအကျ process name ကိုပစ်သည်|
|`-c`|စာရင်းပြသည် (Dry run)|
|`-n`|နောက်ဆုံးစထားသော (newest) process ကိုပစ်သည်|
|`-o`|အဟောင်းဆုံး (oldest) process ကိုပစ်သည်|
|`-P`|Parent process ID (PPID) ကိုသတ်မှတ်၍ပစ်သည်|

---

## **Basic Usage**

###  **1. Process Name နဲ့ပစ်ခြင်း (အခြေခံ)**

```bash
pkill mpv
```

 **အဓိပ္ပါယ်:** `mpv` process ကို အမည်နဲ့ တည်းဟုတ်မှန်းစစ်ပြီး ပစ်သတ်တယ်။

---

###  **2. Force Kill (SIGKILL) နဲ့ ပစ်ခြင်း (-9)**

```bash
pkill -9 mpv
```

 **အဓိပ္ပါယ်:** `mpv` process ကို **အရေးပေါ်ပစ်ခြင်း**ဖြစ်ပြီး ရပ်တန့်ဖို့ အချိန်မပေးဘဲ တိုက်ရိုက်ပစ်တယ်။

---

### **3. Full Command Line ကို တိတိကျကျ စစ်ပြီး ပစ်ခြင်း (-f)**

```bash
pkill -f "mpv --no-video"
```

**အဓိပ္ပါယ်:** `mpv --no-video` ဆိုတဲ့ Command Line အပြည့်အစုံကို ရှာပြီး ပစ်တယ်။

---

###  **4. အတိအကျ Process Name ကိုပစ်ခြင်း (-x)**

```bash
pkill -x mpv
```

**အဓိပ္ပါယ်:** Process name ဟာ `mpv` တည်းဟုတ်မှန်းစစ်ပြီး ပစ်တယ်။

---

### **5. နောက်ဆုံးစထားသော Process ကိုပစ်ခြင်း (-n)**

```bash
pkill -n mpv
```

**အဓိပ္ပါယ်:** `mpv` process တွေထဲမှာ နောက်ဆုံးစထားတဲ့ process ကိုပစ်တယ်။

---

###  **6. အဟောင်းဆုံး Process ကိုပစ်ခြင်း (-o)**

```bash
pkill -o mpv
```

 **အဓိပ္ပါယ်:** `mpv` process တွေထဲမှာ အဟောင်းဆုံးက ပထမဆုံးစတဲ့ process ကိုပစ်တယ်။

---

###  **7. သတ်မှတ်ထားသော User အတွက်ပစ်ခြင်း (-u)**

```bash
pkill -u user_name mpv
```

**အဓိပ္ပါယ်:** User သတ်မှတ်ချက်နဲ့ လုပ်နေတဲ့ `mpv` process ကိုပစ်တယ်။

---

#  **Real-World Examples**


### **mpv ကို Force Kill နဲ့ ပစ်ခြင်း**

```bash
pkill -9 mpv
```

 **အရေးပေါ်ပစ်ပြီး အသံရပ်ပယ်ရန် အသုံးဝင်တယ်။**

---

### **Full Command Line နဲ့ ရှာပြီးပစ်ခြင်း**

```bash
pkill -f "/usr/bin/mpv --no-video"
```

**အပြည့်အစုံ Command Line နဲ့ လုပ်နေတဲ့ process ကိုပစ်တယ်။**

---

###  **Process ပေါင်းများစွာကို တစ်ချိန်တည်း ပစ်ခြင်း**

```bash
pkill -9 -f "mpv.*audio"
```

 **Command Line မှာ `audio` ပါတဲ့ mpv process တွေကို အားလုံးပစ်တယ်။**

---

##  **Tips**

- **Process ပေါ်မပေါ် စစ်ချင်ရင်**
    
    ```bash
    pgrep -fl mpv
    ```
    
- **အတိအကျ ရှင်းရှင်းလင်းလင်း စစ်ချင်ရင်**
    
    ```bash
    ps aux | grep mpv
    ```
    

---

##  **pkill နဲ့ kill ရဲ့ ကွာခြားချက်**

- `kill` ကိုသုံးရင် PID ကို သိရပါမယ်။
- `pkill` က Process Name ကို အသုံးပြုပြီး ပစ်တယ်။
- `pkill` ကပိုလွယ်ကူပြီး pattern ကိုလည်း အသုံးပြုနိုင်တယ်။

---

  
### `pidof` command ကို အသုံးပြုတာက **Process ID (PID)** ကို ရှာဖို့ပါပဲ။

---

###  **Syntax**

```bash
pidof [process_name]
```

---

###  **Example**

```bash
pidof mpv
```


####  Commands Substitution ရေးနည်း

```bash 
kill $(pidof mpv)
```



 **Output :**  
`mpv` ဆိုတဲ့ process ရဲ့ **PID** (Process ID) ကို ပြပေးမှာပါ။

---

###  **Output Example**

```bash
1234 5678
```

အပေါ်က Output က `mpv` process တွေရှိတဲ့ **PID နံပါတ်တွေ** ပါ။  
တစ်ခါတည်း Process များစွာရှိရင် အစဉ်လိုက် ပြပေးပါတယ်။

---

###  **PID ကို အသုံးပြုပြီး Kill လုပ်ခြင်း**

PID ကို ရလာတဲ့အခါမှာ အောက်ပါအတိုင်း ပစ်သတ်နိုင်ပါတယ်။

```bash
kill 1234
```

သို့မဟုတ်

```bash
kill -9 1234 5678
```

**-9** ကတော့ **force kill** လုပ်တာပါ။

---

###  **`pidof` နဲ့ `pgrep` ကွာခြားချက်**

|Command|Description|
|---|---|
|`pidof`|Process name နဲ့ ကိုက်ညီတဲ့ **PID အားလုံးကို တစ်ကြိမ်တည်းပြသည်**|
|`pgrep`|Process name နဲ့ ကိုက်ညီတဲ့ **PID အားလုံးကို တစ်ကြိမ်တည်းပြသည်** (အနည်းငယ်ပိုခေတ်မီ)|

---

