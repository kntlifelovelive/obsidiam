
---

##  Step-by-Step — `find` Mastery Plan 

###  **Level 1 – Basic Filters**

အဓိကသုံးတဲ့ “test” options တွေပါ —

```bash
find . -type f -name "*.txt"       # .txt ဖိုင်တွေရှာ
find /etc -type d -name "nginx*"   # directory တွေရှာ
find ~/Downloads -size +50M        # 50MB ကျော်ဖိုင်ရှာ
find / -mtime -1                   # မနေ့တုန်းကပြင်ထားတဲ့ ဖိုင်ရှာ
find / -user kyaw                  # Kyaw ရဲ့ဖိုင်တွေရှာ
```

**Tests** ဆိုတာ — ဖိုင်တစ်ခုစီကို စစ်မယ့် “စစ်ခြင်း” တွေပါ။
###  **Level 2 – Logic control**


```bash
find . \( -name "*.mp4" -o -name "*.mkv" \)
find . -type f -a -name "*.conf"
find . ! -name "*.bak"
```


- `-o` → OR
- `-a` → AND
- `!` → NOT

Tip ==> parentheses တွေသုံးတဲ့အခါ `\(` `\)` လို့ escape လုပ်ဖို့မမေ့ပါနဲ့   ................. ။

###  **Level 3 – Action Options**

==> Example 

```bash
find . -type f -name "*.bak" -delete              # ဖျက်
find . -type f -name "*.jpg" -exec ls -lh {} \;   # စာရင်းပြ
find . -type f -exec file {} \;                   # file type စစ်
find . -type f -exec cp -t ~/Backup {} +          # copy စုပေး
```

==>  `-exec` နဲ့ `-delete` တို့က “**Action options**” ဖြစ်ပြီး test result ပေါ်မှာ လုပ်ဆောင်မှု လုပ်တာပါ။


###  **Level 4 – Optimizing with `+`**

`-exec` နောက်မှာ `+` သုံးတာက performance booster ပါ။

```bash
# ဥပမာ: ဖိုင် 100 ခုကို cp တစ်ကြိမ်နဲ့ပဲလုပ်တယ်
find . -name "*.png" -exec cp -t ~/Images {} +
```

=> Efficiency နဲ့ ပြောရရင် `+` က command run တစ်ကြိမ်နဲ့ ဖိုင်အများကြီး process လုပ်သွားတယ်။


###  **Level 5 – Mixing find + xargs (super combo)**

`xargs` နဲ့ပေါင်းသုံးရင် super smart ဖြစ်ပါတယ် 

```bash
find . -type f -name "*.log" | xargs rm
find . -type f -print0 | xargs -0 cp -t ~/Backup
```

 `-print0` နဲ့ `xargs -0` သုံးတာက spaces ပါတဲ့ filename တွေကိုလည်း လုံးဝအဆင်ပြေပါတယ်။



###  **Level 6 – Real-World Smart Tricks**

|Goal|Command|
|---|---|
|Hidden files only|`find . -type f -name ".*"`|
|Empty directories|`find . -type d -empty`|
|7 days old files|`find . -mtime +7`|
|Find symlinks|`find . -type l`|
|Search case-insensitive|`find . -iname "*.jpg"`|
|Combine with grep|`find . -type f -exec grep -i "keyword" {} \;`|


###  **Level 7 – Custom command composition (smart automation)**

Example ==>  `.mp4` ဖိုင်တွေကို 100MB ထက်ကျော်ရင် backup 

```bash
find ~/Videos -type f -name "*.mp4" -size +100M -exec cp -t ~/Backup {} +
```

ဒါဆိုရင် `find` ကို script automation ထဲမှာထည့်လို့လည်း ရပါတယ်။


```bash
man find
info find
```

သို့မဟုတ် cheat sheet:

```bash
find . -type f -name "*.sh" -printf "%p\t%k KB\n"
```

(ဖိုင်နဲ့အရွယ်အစားတစ်ပြိုင်တည်းပြသတယ်)

---
---


# level.8 find combination 


---

#  1️⃣ Command

```bash
find . -type f -iname "*.mp4" -size +1G -print0 | xargs -0 du -ch

#output 

1.1G	./Videos/video_2026-01-28_21-32-07.mp4
1.1G	total
```

- Same Result 

```bash 

find . -type f -iname "*.mp4" -size +1G -exec du -ch  {} + 

#output 

1.1G	./Videos/video_2026-01-28_21-32-07.mp4
1.1G	total

```
##  Purpose

1GB ထက်ကြီးတဲ့ mp4 file တွေရဲ့ **disk usage size** ကိုကြည့်ချင်တဲ့အခါ သုံးတယ်။

##  Breakdown

- `find .` → current directory ထဲရှာမယ်
    
- `-type f` → file only
    
- `-iname "*.mp4"` → case insensitive match
    
- `-size +1G` → bigger than 1GB
    
- `-print0` → null separator output
    

Pipe →

- `xargs -0` → null separated input read
    
- `du -ch`
    
    - `-c` → total line ထုတ်ပေးမယ်
        
    - `-h` → human readable (MB, GB)
        

##  Result

File size တစ်ခုချင်းစီ + total size ပြမယ်။

---

#  2️⃣ Command

```bash
find . -type f -iname "*.mp4" -size +1G -print0 | xargs -0 ls -lh
```

```bash 

find . -type f -iname "*.mp4" -size +1G -exec ls -lh {} +


```


##  Purpose

1GB ထက်ကြီးတဲ့ mp4 file တွေရဲ့ **file detail info** ကြည့်ချင်တဲ့အခါ။

##  Difference from #1

ဒီမှာ `du` မဟုတ်ဘူး → `ls -lh`

- `ls -l` → permission, owner, date
    
- `-h` → human readable size
    

## Result

File size + permission + modified date ပြမယ်။

---

# 3️⃣ Command

```bash
find . -type f -iname "*.mp4" -size +1G -exec ls -lh {} +

# output 

-rw-r--r-- 1 archibubu archibubu 1.1G Jan 28 21:32 ./Videos/video_2026-01-28_21-32-07.mp4
```

- same Result 

```bash 

 find . -type f -iname "*.mp4" -size +1G -print0 | xargs -0 ls -lh 
 
 # output 
 
-rw-r--r-- 1 archibubu archibubu 1.1G Jan 28 21:32 ./Videos/video_2026-01-28_21-32-07.mp4

```
##  Purpose

Command #2 နဲ့တူတယ် —  
ဒါပေမယ့် `xargs` မသုံးဘူး။

##  Important Parts

- `-exec` → find ထဲမှာတန်း command run
    
- `{}` → found file name
    
- `+` → multiple files at once (faster)
    

###  Difference

|Method|Tool|
|---|---|
|#1|xargs + du|
|#2|xargs + ls|
|#3|find -exec|

---

#  Key Concept

### `du` vs `ls`

|Command|Meaning|
|---|---|
|`du`|disk usage (actual disk space used)|
|`ls`|file metadata info|

Sometimes `du` size ≠ `ls` size  
(Especially sparse files)

---

### Size Units in find

|Unit|Meaning|
|---|---|
|c|bytes|
|k|kilobytes|
|M|megabytes|
|G|gigabytes|

- Meaning:

- `+1G` → bigger than 1GB
    
- `1G` → exactly 1GB
    
- `-1G` → smaller than 1GB
    


---

#  When to Use What?

✔ Total size လိုချင် → `du -ch`  
✔ Detail info ကြည့်ချင် → `ls -lh`  
✔ Simpler syntax → `-exec`  
✔ Safer with spaces → `-print0 | xargs -0`

---


- file big size  format နဲ့  ရှာဖွေ
```bash 
find . -type f -iname "*.mp4" -size +1G -exec ls -lh {} +

## output 
 
find . -type f -iname "*.mp4" -size +1G -exec ls -lh {} + 
-rw-r--r-- 1 archibubu archibubu 1.1G Jan 28 21:32 ./Videos/video_2026-01-28_21-32-07.mp4

```

### Or 

```bash 

 find . -type f -iname "*.mp4" -size +1G -print0 | xargs -0 ls -lh 
 
 ## output 
 
-rw-r--r-- 1 archibubu archibubu 1.1G Jan 28 21:32 ./Videos/video_2026-01-28_21-32-07.mp4 
```

##### file format, size, path location 

```bash

 find . -type f -iname "*.mp4" -size +1G -print0 | xargs -0 du -ch 
1.1G	./Videos/video_2026-01-28_21-32-07.mp4
1.1G	total 
```



-----
-----
## Find and rsync mestry commands 


```bash 

sudo find ~/usb/ -type f -iname "Three*.mp4" -exec rsync -av --progress {} ~/Videos/ \;  
```



---
---
---
---

#  Find Command Practical Table Note

|#|Title|Source Path|Find Options|Action Command|Description|
|---|---|---|---|---|---|
|1|Delete .bak Files|`.`|`-type f -name "*.bak"`|`-delete`|Current directory အောက်ရှိ `.bak` files ဖျက်မယ်|
|2|List .jpg Files (Detail)|`.`|`-type f -name "*.jpg"`|`-exec ls -lh {} \;`|`.jpg` files ကို size + permission နဲ့ စာရင်းပြမယ်|
|3|Check File Type|`.`|`-type f`|`-exec file {} \;`|File type (text, binary, image, etc.) စစ်မယ်|
|4|Copy Files to Backup|`.`|`-type f`|`-exec cp -t ~/Backup {} +`|Found files အားလုံးကို `~/Backup` ထဲ copy စုပေးမယ်|

---

# Breakdown Structure

General Pattern 

```bash
find <source_path> <condition_options> <action>
```

---

# Important Differences

## 🔹 `{}` vs `{}` +

| Syntax    | Meaning                               |
| --------- | ------------------------------------- |
| `{}` `\;` | File တစ်ခုချင်းစီ command run         |
| `{}` `+`  | File များစုပြီး command run (faster ) |

Example:

```bash
-exec cp -t ~/Backup {} +
```

-  Efficient version  
- Large file count မှာ fast

---

#  Visual Structure Diagram

```text
find .                ← source path
-type f               ← condition (files only)
-name "*.jpg"         ← filter
-exec ls -lh {} \;    ← action
```

---

#  Extended Professional Table (Advanced Practice)

|Title|Example|Purpose|
|---|---|---|
|Delete Old Logs|`find /var/log -type f -mtime +30 -delete`|30 days old log delete|
|Large Files List|`find . -type f -size +1G -exec ls -lh {} +`|1GB+ files show|
|Empty Files Remove|`find . -type f -empty -delete`|Empty files clean|
|Permission Fix|`find . -type f -perm 777 -exec chmod 644 {} +`|Unsafe permission fix|

---

#  Practice Tasks For You

1️⃣ `.tmp` files list only  
2️⃣ 10MB ထက်ကြီးတဲ့ files list  
3️⃣ Empty directories delete  
4️⃣ `.log` files copy to backup

---

---

# FIND COMMAND MASTERY CHEAT SHEET

##  Basic Structure

```bash
find <path> <conditions> <action>
```

---

##  Core Options Table

|Category|Option|Example|Meaning|
|---|---|---|---|
|Path|`.`|`find .`|Current directory|
|File Type|`-type f`|`find . -type f`|Files only|
|Directory Type|`-type d`|`find . -type d`|Directories only|
|Name Match|`-name "*.txt"`|Case sensitive|File name filter|
|Case Ignore|`-iname "*.jpg"`|Case insensitive|Ignore case|
|Size Filter|`-size +100M`|`+` bigger / `-` smaller|File size filter|
|Time Modified|`-mtime -2`|Last 2 days|Date filter|
|Empty|`-empty`|`find . -empty`|Empty file/dir|
|Permission|`-perm 777`|Exact permission|Permission filter|
|User|`-user kyaw`|Owner filter|By user|
|Group|`-group staff`|Group filter|By group|

---

##  Action Options Table

|Action|Example|Purpose|
|---|---|---|
|Delete|`-delete`|Remove files|
|Exec (single)|`-exec cmd {} \;`|Run per file|
|Exec (batch)|`-exec cmd {} +`|Run grouped (fast)|
|Print|`-print`|Show result|
|Print0|`-print0`|Null separated output|
|OK|`-ok rm {} \;`|Ask before run|

---

##  Logical Operators

|Operator|Example|Meaning|
|---|---|---|
|AND (default)|`-type f -name "*.txt"`|Both true|
|OR|`-name "*.jpg" -o -name "*.png"`|Either true|
|NOT|`! -name "*.log"`|Exclude|

---

##  Advanced Examples Table

|Scenario|Command|
|---|---|
|Delete old logs|`find /var/log -type f -mtime +30 -delete`|
|Find big files|`find . -type f -size +1G -exec ls -lh {} +`|
|Remove empty dirs|`find . -type d -empty -delete`|
|Fix 777 perms|`find . -type f -perm 777 -exec chmod 644 {} +`|
|Only today modified|`find . -mtime 0`|

---

#  FIND vs XARGS DEEP COMPARISON

---

##  Basic Concept

`find -exec` → find runs command directly  
`find | xargs` → pipe output to another command

---

##  Comparison Table

| Feature             | find -exec      | find + xargs    |
| ------------------- | --------------- | --------------- |
| Syntax simplicity   | Easy            | Medium          |
| Performance         | Slower (`\;`)   | Faster          |
| Batch support       | `{}` `+`        | Native batching |
| Null safety         | Needs `-print0` | Use `-0`        |
| Parallel support    | X               | `xargs -P`      |
| Control flexibility | Limited         | More flexible   |

---

##  Execution Difference

### 🔹 Slow Version

```bash
find . -type f -exec rm {} \;
```

-  One process per file 

---

### 🔹 Faster Version

```bash
find . -type f -exec rm {} +
```

-  Grouped execution 

---

### 🔹 xargs Fastest Version

```bash
find . -type f -print0 | xargs -0 rm
```

- Very efficient 

---

##  Parallel Execution (xargs Superpower )

```bash
find . -type f -print0 | xargs -0 -P 4 rm
```

`-P 4` → 4 parallel processes

-  Huge performance gain on SSD / large datasets

---

##  Performance Hierarchy

|Speed Rank|Method|
|---|---|
|🥉|`-exec {} \;`|
|🥈|`-exec {} +`|
|🥇|`xargs`|
|👑|`xargs -P` (parallel)|

---

#  Real World Usage Guide

|Situation|Recommended|
|---|---|
|Small file count|`-exec`|
|Large file count|`xargs`|
|Space in filename|`-print0 + -0`|
|Multi-core system|`xargs -P`|
|Safer interactive|`-ok`|

---

#  Pro Tip Summary

✔ Always use `-print0` with xargs  
✔ Prefer `{}` `+` instead of `\;`  
✔ Use `xargs -P` for heavy operations  
✔ Test with `echo` before destructive command

Example safe test:

```bash
find . -type f -print0 | xargs -0 echo
```

---

