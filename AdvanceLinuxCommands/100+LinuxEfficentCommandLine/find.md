
## **Topic – How to Search Files and Directories in Linux (20 Practical Examples)**

`find` ဆိုတာက Directory structure တစ်ခုလုံးအတွင်းမှာ   File name, type, size, permission, owner, modified time စသဖြင့်  
criteria မျိုးစုံနဲ့ file/directory တွေကို ရှာဖို့သုံးတဲ့ command ဖြစ်ပါတယ်။


##  **Command Usage**

 **find** – search for files and directories  
**Syntax**

```bash
find [path] [options] [expression]
```


##  **Examples**

### **Example 1 – Find Files by Name**

```bash
find /home -name file.txt
```

➡ `/home` directory ထဲမှာ **file.txt** နာမည်ရှိတဲ့ file ကို ရှာမယ်။

### **Example 2 – Find Files by Name (Case-Insensitive)**

```bash
find /home -iname file.txt
```

➡ `-iname` ဆိုတာ case-insensitive ဖြစ်တယ်။  
`File.txt`, `FILE.TXT` လည်း ဖော်ပြပေးမယ်။


### **Example 3 – Find All Files with Specific Extension**

```bash
find /home/user -name "*.sh"
```

➡ `.sh` extension (shell script files) တွေကို ရှာမယ်။


### **Example 4 – Find All Directories**

```bash
find /etc -type d
```

➡ Directory (`-type d`) များကိုသာ ရှာမယ်။


### **Example 5 – Find All Regular Files**

```bash
find /var/log -type f
```

➡ File များကိုသာ ပြမယ်။ (`-type f`)

### **Example 6 – Find Empty Files**

```bash
find /tmp -type f -empty
```

➡ size 0 ဖြစ်တဲ့ file များကိုရှာမယ်။


### **Example 7 – Find Empty Directories**

```bash
find /tmp -type d -empty
```

➡ ဖိုင်မပါတဲ့ directory များကိုရှာမယ်။


### **Example 8 – Find Files Modified in Last 7 Days**

```bash
find /home -type f -mtime -7
```

➡ နောက်ဆုံးပြင်ဆင်ခဲ့တာ 7 ရက်အတွင်းရှိ files များ။


### **Example 9 – Find Files Modified More Than 30 Days Ago**

```bash
find /var/log -type f -mtime +30
```

➡ 30 ရက်ထက် ပိုကြာပြီးပြီသော files များ။


### **Example 10 – Find Files Accessed in Last 24 Hours**

```bash
find /home -atime -1
```

➡ နောက်ဆုံး access လုပ်ခဲ့တာ တစ်နေ့အတွင်းဖြစ်တဲ့ files များ။


### **Example 11 – Find Files Larger Than 100MB**

```bash
find / -type f -size +100M
```

➡ Size 100MB ထက်ကြီးတဲ့ files များ။


### **Example 12 – Find Files Smaller Than 10KB**

```bash
find /home -type f -size -10k
```

➡ Size 10KB ထက်ငယ်တဲ့ files များ။


### **Example 13 – Find Files by Permission**

```bash
find /usr -type f -perm 644
```

➡ Permission 644 (rw-r--r--) ဖြစ်တဲ့ files များ။


### **Example 14 – Find Files Owned by Specific User**

```bash
find /home -user kyaw
```

➡ User `kyaw` ရဲ့ ဖိုင်များကို ရှာမယ်။


### **Example 15 – Find Files and Execute Command**

```bash
find /home -name "*.log" -exec rm {} \;
```

➡ `.log` files တွေကို ရှာပြီး delete လုပ်မယ်။  
(⚠️ သတိထားသုံးပါ)


### **Example 16 – Find Files with Specific Group**

```bash
find /var/www -group www-data
```

➡ `www-data` group ရဲ့ file များ။



### **Example 17 – Find Files Modified in Last 1 Hour**

```bash
find /tmp -mmin -60
```

➡ နောက်ဆုံးပြင်ခဲ့တာ ၁နာရီအတွင်းဖြစ်တဲ့ files များ။


### **Example 18 – Find Hidden Files**

```bash
find /home/kyaw -type f -name ".*"
```

➡ Hidden files (`.` နဲ့စတဲ့) များကိုရှာမယ်။


### **Example 19 – Find and Print Only Filenames (No Path)**

```bash
find /etc -type f -printf "%f\n"
```

➡ File name သာပြမယ်၊ full path မပါဘူး။


### **Example 20 – Combine Multiple Conditions**

```bash
find /home -type f \( -name "*.sh" -o -name "*.py" \)
```

➡ `.sh` OR `.py` extension များရှိတဲ့ files များကို ရှာမယ်။


##  **Quick Reference Table**

|Option|Meaning|
|---|---|
|`-name`|Match exact name|
|`-iname`|Case-insensitive name match|
|`-type f/d`|File / Directory|
|`-empty`|Empty file or dir|
|`-mtime / -atime / -mmin`|Modified / Accessed / Minutes|
|`-size`|File size filter|
|`-user / -group`|Owner / Group|
|`-exec`|Run command on results|


##  **Summary**

- `find` က directory structure ကြီးတွေထဲမှာ လှည့်ရှာဖို့အတွက် အမြဲသုံးကြတဲ့ command 
- Name, size, date, owner, permission အစရှိသဖြင့် filter နည်းစုံရှိတယ်။
- တစ်ခါတည်းနဲ့ action လုပ်ဖို့ (`-exec`) လည်း အသုံးဝင်တယ်။


---
