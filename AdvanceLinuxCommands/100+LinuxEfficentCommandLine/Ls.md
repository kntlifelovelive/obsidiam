
---

##  `ls` Command 

**`ls`** ဆိုတာက ==> >  `ls` = **List directory contents**
 “list segments” or “list structure” (short for _list_)
 Linux မှာ _directory ထဲက file တွေ၊ folder တွေကို ပြရန်_ အသုံးပြုတဲ့ command ပါ။  
 Windows မှာ “dir” နဲ့တူတယ်။
Default အနေနဲ့ `ls` လုပ်ရင် → current directory ထဲက file & folder names တွေကို ပြပေးတယ်။

---

##  `ls` Command Examples (15 Examples with Explanations)

|No|Command|Description|
|---|---|---|
|1|`ls`|လက်ရှိ directory ထဲက file နဲ့ folder name တွေကို ပြတယ်။|
|2|`ls -l`|Long format ပြပေးတယ် — permissions, owner, size, date modified စတဲ့ detail info တွေပါပဲ။|
|3|`ls -a`|Hidden files (`.` နဲ့စတဲ့ file တွေ) အပါအဝင် ပြပေးတယ်။|
|4|`ls -lh`|File size ကို human readable format (KB, MB) နဲ့ ပြတယ်။|
|5|`ls -R`|Subdirectories အထိ recursively ပြတယ်။|
|6|`ls -lt`|Modification time အရ sort လုပ်ပြီး အစောဆုံးပြတယ် (latest first)။|
|7|`ls -ltr`|Modification time အရ sort လုပ်ပြီး အဟောင်းဆုံးကို အပေါ်မှာပြတယ်။|
|8|`ls -S`|File size အကြီးဆုံးအရ sort လုပ်ပြတယ်။|
|9|`ls -lS`|Long format + Sort by file size (big → small)။|
|10|`ls -d */`|Folder (directories) တွေကိုပဲ ပြချင်တဲ့အခါ။|
|11|`ls -1`|Single column format နဲ့ file တွေကို တန်းစီပြတယ်။ (scripts တွေမှာ often used)|
|12|`ls /etc`|`/etc` ဆိုတဲ့ directory ထဲက file တွေကို ပြတယ်။ (သတ်မှတ်ပေးနိုင်တယ်)|
|13|`ls -i`|File တွေရဲ့ inode number ကိုပါပြတယ်။|
|14|`ls --color=auto`|File type ပေါ်မူတည်ပြီး color နဲ့ highlight ပြတယ်။|
|15|`ls -lh *.txt`|`.txt` files တွေကိုပဲ human readable format နဲ့ပြတယ်။|

---

##  Extra Useful Combination

```bash
ls -lah
```

➡ Hidden files + Long format + Human readable  
သုံးရတဲ့ combination ဖြစ်တယ်။

*Example  Output*

```bash
drwxr-xr-x  2 user user 4.0K Oct 12 10:00 .
drwxr-xr-x 12 user user 4.0K Oct 12 09:50 ..
-rw-r--r--  1 user user  120 Oct 12 10:01 file.txt
-rw-r--r--  1 user user  512 Oct 11 18:00 .hiddenfile
```

---

##  Summary Table (Cheatsheet Style)

|Option|Meaning|
|---|---|
|`-l`|Long listing format|
|`-a`|Include hidden files|
|`-h`|Human readable file sizes|
|`-R`|Recursive listing|
|`-t`|Sort by modification time|
|`-r`|Reverse sort order|
|`-S`|Sort by file size|
|`--color=auto`|Colorized output|
|`-d */`|Show directories only|

---
