
---

# `stat` Command – Detailed Notes

##  `stat` ဆိုတာဘာလဲ

`stat` command က  
- **file / directory တစ်ခုရဲ့ metadata (အတွင်းအချက်အလက်)** ကို ပြပေးတဲ့ command ပါ။

**metadata ဆိုတာ**

- file size
    
- permission
    
- owner / group
    
- inode number
    
- access / modify / change time  
    တွေကို ပြတာပါ။
    

-  `ls -l` ထက် **ပိုပြီးအသေးစိတ်** ပြပေးနိုင်တယ်။

---

##  Basic Usage

```bash
stat filename
```

 ဥပမာ

```bash
stat test.txt
```

 directory ကိုလည်း ရတယ်

```bash
stat /etc
```

---

## `stat` Output ကိုဖတ်နည်း

- output 

```text
File: test.txt
Size: 1024        Blocks: 8      IO Block: 4096 regular file
Device: 259,2     Inode: 131234  Links: 1
Access: (0644/-rw-r--r--)  Uid: (1000/kyaw)  Gid: (1000/kyaw)
Access: 2026-02-01 10:15:20.000000000 +0630
Modify: 2026-02-01 09:50:10.000000000 +0630
Change: 2026-02-01 09:50:10.000000000 +0630
 Birth: 2026-01-31 22:30:00.000000000 +0630
```

---

###  1. File

```text
File: test.txt
```

-  file / directory နာမည်

---

###  2. Size

```text
Size: 1024
```

file size (bytes)  
1024 bytes = 1KB

---

###  3. Blocks / IO Block

```text
Blocks: 8   IO Block: 4096
```

- **Blocks** → disk ပေါ်မှာ သုံးထားတဲ့ block အရေအတွက်
    
- **IO Block** → filesystem ရဲ့ block size
    

==> small file ဖြစ်ပေမဲ့ block size ကြောင့် disk ပေါ်မှာ ပိုယူနိုင်တယ်

---

###  4. File Type

```text
regular file
```

အမျိုးအစားများ 

- `regular file` → ပုံမှန် file
    
- `directory` → folder
    
- `symbolic link`
    
- `character device`
    
- `block device`
    
- `socket`
    
- `fifo`
    

---

###  5. Device

```text
Device: 259,2
```

==> file ရှိတဲ့ disk / partition ID  
(အများအားဖြင့် debug မှာပဲ အသုံးများ)

---

###  6. Inode  

```text
Inode: 131234
```

==> file ကို Linux filesystem မှာ ကိုယ်စားပြုတဲ့ unique number  
file name မဟုတ်ဘူး 
file data + metadata ကို inode က ထိန်းထားတယ်

- inode ပြည့်သွားရင် disk space မကုန်ပေမဲ့ file မဖန်တီးနိုင်ဘူး

---

###  7. Links

```text
Links: 1
```

==>  hard link အရေအတွက်  
1 ထက်များရင် file တစ်ခုကို နာမည်များစွာနဲ့ ချိတ်ထားတာ

---

###  8. Permission

```text
Access: (0644/-rw-r--r--)
```

**0644** = numeric permission  
**-rw-r--r--** = readable format

|Owner|Group|Others|
|---|---|---|
|rw-|r--|r--|

---

###  9. UID / GID

```text
Uid: (1000/kyaw)
Gid: (1000/kyaw)
```

 file owner & group

---

###  10. Time Stamps

```text
Access:
Modify:
Change:
Birth:
```

|Time|Meaning|
|---|---|
|Access (atime)|file ကို **ဖတ်ခဲ့တဲ့အချိန်**|
|Modify (mtime)|file content **ပြင်တဲ့အချိန်**|
|Change (ctime)|permission / owner **ပြောင်းတဲ့အချိန်**|
|Birth|file **စတင်ဖန်တီးတဲ့အချိန်**|


---

##  Useful Options

###  Human readable format

```bash
stat -h file
```

- ==>  size ကို KB / MB နဲ့ ပြ

---

### Filesystem info

```bash
stat -f file
```

filesystem details

- type (ext4, btrfs)
    
- block size
    
- inode count
    

---

###  Custom format  (Advanced)

```bash
stat -c "%n %s %y" file
```

|Format|Meaning|
|---|---|
|%n|file name|
|%s|size|
|%y|modify time|
|%a|permission (numeric)|
|%U|owner|
|%G|group|

 scripting မှာ အရမ်းသုံး

---

##  Practical Use Cases

###  File changed recently?

```bash
stat file | grep Modify
```

---

###  Permission check

```bash
stat -c "%a %n" *
```

---

###  Security / Incident check

- unauthorized file change?
    
- timestamp manipulation?
    
- inode mismatch?
    

---

##  `ls -l` vs `stat`

|ls -l|stat|
|---|---|
|basic|very detailed|
|no inode|inode info|
|simple view|forensic level|

---

##  Summary 

- `stat` = file metadata inspector
    
- filesystem, permission, inode, timestamps တွေကို **တစ်ခါတည်း** မြင်ရ
    
- sysadmin / security / debugging အတွက် must-know command
    

---
