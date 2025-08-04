
### **Linux မှာ Secure File Deletion လုပ်နည်း** 

Linux မှာ file ကို ပုံမှန် `rm` command နဲ့ဖျက်လိုက်တာနဲ့ တကယ်က data တွေ disk ပေါ်မှာ ကျန်နေနိုင်ပါတယ်။  
Disk မှာ overwrite မဖြစ်တဲ့အတွက် recovery tool တွေနဲ့ undelete ပြန်လုပ်လို့ရနိုင်ပါတယ်။  
**Secure delete** ဆိုတာက file ကို အချင်းချင်း overwrite လုပ်ပြီး ပြန်မရအောင်ဖျက်တာပါ။

---

## **1️⃣ Secure Deletion Tools**

Linux မှာ secure file deletion လုပ်ဖို့ အောက်ပါ methods တွေကို အသုံးပြုနိုင်ပါတယ်။

1. `shred` - File ကို အကြိမ်ကြိမ် overwrite ပြုလုပ်ပြီး ဖျက်ပေးတာ
    
2. `srm` (secure rm) - GNU `rm` နဲ့တူပေမယ့် overwrite လုပ်ပြီး ဖျက်ပေးတာ
    
3. `wipe` - Disk blocks တွေကို အကြိမ်ကြိမ် overwrite လုပ်တာ
    
4. `dd` - Zero overwrite, random data overwrite နဲ့ shred လုပ်နိုင်တာ
    

---

## **2️⃣ `shred` ကိုအသုံးပြုခြင်း** 

```bash
shred -u -z -n 5 secret.txt
```

🔹 **အကြောင်းအရာ**  
✔️ `-u` → ဖျက်ပြီး filename ကိုပါ ဖျက်ပေးမယ်  
✔️ `-z` → အဆုံးမှာ zero data overwrite လုပ်မယ်  
✔️ `-n 5` → ၅ ကြိမ် overwrite လုပ်မယ် (default က 3)

---

## **3️⃣ `srm` (Secure RM) ကိုအသုံးပြုခြင်း** 

(srm ကိုအသုံးပြုဖို့ **secure-delete** package ကို install လိုအပ်ပါတယ်။)

```bash
sudo apt install secure-delete   # Debian/Ubuntu
sudo pacman -S secure-delete     # Arch Linux
sudo yum install secure-delete   # RHEL/Fedora
```

**Example:**

```bash
srm -v secret.txt
```

🔹 **Option**  
✔️ `-v` → Verbose mode (ဖျက်တာကို ပြသမယ်)  
✔️ `-r` → Folder တွေပါဖျက်နိုင်မယ်

---

## **4️⃣ `wipe` ကိုအသုံးပြုခြင်း** 

```bash
sudo apt install wipe  # Debian-based OS
```

**Example:**

```bash
wipe -rf secret-folder/
```

🔹 `-r` → Recursive (folder အတွင်းပါဖျက်မယ်)  
🔹 `-f` → Force delete

---

## **5️⃣ `dd` နဲ့ Overwrite လုပ်ပြီး ဖျက်ခြင်း** 

```bash
dd if=/dev/urandom of=secret.txt bs=1M count=1
rm secret.txt
```

🔹 `if=/dev/urandom` → Random data ဖြည့်မယ်  
🔹 `bs=1M count=1` → 1MB အရွယ် file တစ်ခုကို overwrite လုပ်မယ်

**Partition တစ်ခုလုံး secure wipe လုပ်ချင်ရင်:**

```bash
dd if=/dev/zero of=/dev/sdX bs=1M
```

(⚠️ **သတိ**: `sdX` ကို မိမိ disk partition အစား သေချာစစ်ပါ။)

---

## **မှတ်ချက်**

🔹 **Single file** ဖျက်ချင်ရင် `shred` / `srm` ကိုသုံး  
🔹 **Whole folder** ဖျက်ချင်ရင် `wipe`  
🔹 **Partition တစ်ခုလုံး** secure erase လုပ်ချင်ရင် `dd`

---

### **ဘယ် CLI ကို ပိုသုံးသင့်လဲ?**


|**Tool**|**အသုံးပြုမှု**|**သင့်လျှော်မှု**|
|---|---|---|
|`shred`|**Single file** secure delete|အများဆုံးသုံး, user-friendly|
|`srm`|`rm` နဲ့တူပေမယ့် secure delete|နည်းပညာပိုင်းနားလည်ရင် သုံးမယ်|
|`wipe`|**Folder/partition** secure delete|Hard drive မထိခိုက်ပဲ အသုံးပြုနိုင်|
|`dd`|**Whole drive/partition wipe**|အန္တရာယ်များ, သတိထားသုံးရမယ်|

---

### **Harddisk ကို ထိခိုက်နိုင်လား?**

🔹 **SSD** ➜ **အန္တရာယ်ရှိနိုင်** (overwrite လုပ်ခြင်းက wear-leveling ကို ထိခိုက်နိုင်)  
🔹 **HDD** ➜ **ပိုမိုဘေးကင်း** (magnetic platter တွေ overwrite ဖြစ်တာမို့ ထိခိုက်မှုနည်း)

💡 **SSD သမားများအတွက် အကောင်းဆုံးနည်း**  
👉 **ATA Secure Erase** သုံးပါ

```bash
sudo hdparm --security-erase NULL /dev/sdX
```

(⚠️ **`/dev/sdX` ကို သင့် drive letter နဲ့ ပြောင်းပြီး သေချာစစ်ဆေးပါ**)

💡 **HDD သမားများအတွက်**  
✔️ **`shred` / `wipe` သုံးရုံနဲ့ လုံလောက်**  
✔️ **Whole disk wipe လိုချင်ရင် `dd`** သုံးလို့ရပေမယ့် `wipe` ပိုသင့်တော်

---

✅ **File-level secure delete** ➜ `shred` / `srm`  
✅ **Folder/partition-level wipe** ➜ `wipe`  
✅ **Whole disk erase** ➜ **SSD**: `hdparm`, **HDD**: `dd`

**SSD မှာ `shred`, `dd` တွေ သုံးတာထက် `secure erase` ပိုသင့်တော်ပါတယ်**။  
**HDD မှာတော့ `shred` / `wipe` ကို သုံးလို့ OK ပါ** 

---

### **SSD မှာ Secure Erase လုပ်နည်း (ATA Secure Erase)**

SSD မှာ **`shred`, `wipe`, `dd`** တို့လို **overwrite-based method** တွေကို မသုံးသင့်ပါ။  
SSD ဟာ **wear-leveling** နည်းပညာသုံးတာကြောင့် **ATA Secure Erase** လုပ်မှ အမှန်တကယ် data ပြန်ရမလာနိုင်တဲ့အတိုင်း erase ဖြစ်နိုင်ပါတယ်။

---

## **1️⃣ SSD ကို Secure Erase လုပ်ဖို့ အသုံးပြုသင့်သော Command**

✅ `hdparm`  
✅ `nvme format` (NVMe SSD များအတွက်)

---

## **2️⃣ SSD Secure Erase**

### **(A) SATA SSD အတွက် `hdparm` ဖြင့် Secure Erase**

🔹 **`hdparm` ကို Install လုပ်ပါ**

```bash
sudo apt install hdparm  # Debian/Ubuntu
sudo yum install hdparm  # Fedora
sudo pacman -S hdparm    # Arch Linux
```

🔹 **Drive Status Check**

```bash
sudo hdparm -I /dev/sdX
```

✔️ `sdX` ကို သင့် SSD partition နာမည်နဲ့ ပြောင်းပါ (`lsblk` နဲ့ စစ်လို့ရ)  
✔️ **"not frozen"** ဖြစ်မှ erase လုပ်လို့ရမယ်။  
✔️ **"frozen" ဖြစ်နေရင်** suspend mode သွားပြီး ပြန်ဖွင့်ပါ။

```bash
sudo systemctl suspend
```

ပြီးရင် **Power Button နဲ့ ပြန်ဖွင့်ပါ**။

🔹 **Secure Erase Enable**

```bash
sudo hdparm --user-master u --security-set-pass NULL /dev/sdX
```

🔹 **Erase လုပ်ရန် (⚠️ သတိ! SSD ထဲက Data အားလုံး ပျက်သွားမည်)**

```bash
sudo hdparm --security-erase NULL /dev/sdX
```

✔️ လုပ်ပြီးရင် `hdparm -I /dev/sdX` နဲ့ စစ်ကြည့်ပါ။

---

### **(B) NVMe SSD အတွက် `nvme format` ဖြင့် Secure Erase**

🔹 **`nvme-cli` ကို Install လုပ်ပါ**

```bash
sudo apt install nvme-cli  # Debian/Ubuntu
sudo yum install nvme-cli  # Fedora
sudo pacman -S nvme-cli    # Arch Linux
```

🔹 **NVMe SSD တွေအတွက် Secure Erase Command**

```bash
sudo nvme format /dev/nvme0n1
```

✔️ **Data အားလုံး ပျက်မယ်**  
✔️ **NVMe drive ကို format ပြုလုပ်သွားမယ်**  
✔️ **လိုချင်ရင် -s 1 option ထပ်ထည့်နိုင်**

```bash
sudo nvme format -s 1 /dev/nvme0n1
```

✔️ `nvme list` နဲ့ drive ကို စစ်နိုင်ပါတယ်။

---

## **3️⃣ SSD ကို ဘယ် Secure Erase Command သုံးသင့်လဲ**

|**SSD Type**|**Method**|**Commands**|
|---|---|---|
|SATA SSD|**ATA Secure Erase**|`hdparm --security-erase NULL /dev/sdX`|
|NVMe SSD|**NVMe Format Secure Erase**|`nvme format /dev/nvme0n1`|

**SSD တွေမှာ `shred` / `dd` မသုံးပါနဲ့!**  
**ATA Secure Erase / NVMe Format သည် 100% Secure ဖြစ်ပါတယ်** 

---

