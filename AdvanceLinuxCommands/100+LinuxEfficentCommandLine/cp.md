
---

##  **`cp` Command – Copy Files and Directories**

🔹 **Usage:** `cp [options] source destination`  
🔹 **Full meaning:** _Copy_  
🔹 **Purpose**  ==> `Linu`x မှာ **file** (သို့) **directory** တစ်ခုကို တခြားနေရာသို့ ကူးယူဖို့ အသုံးပြုပါတယ်။


## **Basic Syntax**

```bash
cp [OPTION] SOURCE DESTINATION
```


##  **Common Options**

|Option|Description|
|---|---|
|`-i`|Confirm before overwrite (interactive)|
|`-r` or `-R`|Copy directories recursively|
|`-v`|Show what’s being copied (verbose)|
|`-u`|Copy only when source is newer|
|`-p`|Preserve file attributes (mode, ownership, timestamps)|
|`-n`|Don’t overwrite existing files|


##  **14 Practical Examples of `cp` Command**


### 1. Copy a file to another directory

```bash
cp file.txt /home/user/Documents/
```

==> `file.txt` ကို Documents ထဲသို့ ကူးထည့်တယ်။

### 2. Copy a file and rename it

```bash
cp file.txt backup.txt
```

==> `file.txt` ကို `backup.txt` နာမည်နဲ့ copy လုပ်တယ်။


### 3. Copy multiple files to one directory

```bash
cp file1.txt file2.txt /home/user/Desktop/
```

==> File နှစ်ခုလုံးကို Desktop ထဲသို့ ကူးတယ်။

### 4. Copy a directory (recursively)

```bash
cp -r Project /home/user/Backup/
```

==> Directory `Project` အတွင်းပါသော file အားလုံးပါအောင် copy လုပ်တယ်။


### 5. Copy directory and show progress (verbose)

```bash
cp -rv Project /home/user/Backup/
```

==> Copy လုပ်နေတဲ့ files တွေကို ပြပေးတယ်။

### 6. Copy with confirmation before overwrite

```bash
cp -i file.txt /home/user/
```

==> File overwrite ဖြစ်မဖြစ် မေးပြီးမှ copy လုပ်တယ်။


### 7. Copy without overwriting existing files

```bash
cp -n file.txt /home/user/
```

==> ရှိပြီးသား file ကို မထပ်ရေးဘူး။


### 8. Preserve file attributes

```bash
cp -p file.txt /home/user/
```

==> Original file ရဲ့ permissions, owner, timestamps တွေ ထားရှိတယ်။


### 9. Copy newer files only (update)

```bash
cp -u file.txt /home/user/
```

==> Destination ထဲက file ထက် source ကအသစ်ဖြစ်ရင်ပဲ overwrite လုပ်တယ်။


### 10. Copy all `.txt` files using wildcard

```bash
cp *.txt /home/user/Documents/
```

==> `.txt` file အားလုံးကို Documents ထဲသို့ copy လုပ်တယ်။



### 11. Copy hidden files (dotfiles)

```bash
cp -r .* /home/user/Backup/
```

==> Hidden files (like `.bashrc`, `.zshrc`) ကိုပါ copy လုပ်တယ်။



### 12. Copy using brace expansion

```bash
cp {file1.txt,file2.txt,file3.txt} /home/user/Desktop/
```

==> Brace expansion နဲ့ file အများအပြား တပြိုင်နက် copy လုပ်တယ်။

### 13. Copy with directory structure preserved

```bash
cp --parents src/file.txt /home/user/Backup/
```

==> Directory structure အပြည့်နဲ့ copy လုပ်တယ်။


### 14. Copy and rename a directory

```bash
cp -r MyFolder NewFolder
```

==> Folder တစ်ခုကို `NewFolder` အနေနဲ့ copy လုပ်တယ်။


##  **Quick Summary Table**

|Command|Description|
|---|---|
|`cp file.txt /dir/`|Copy file to directory|
|`cp file1 file2 /dir/`|Copy multiple files|
|`cp -r Folder /dir/`|Copy entire directory|
|`cp -v file /dir/`|Show progress|
|`cp -i file /dir/`|Ask before overwrite|
|`cp -n file /dir/`|Skip existing files|
|`cp -p file /dir/`|Preserve attributes|
|`cp -u file /dir/`|Copy only newer files|
|`cp *.txt /dir/`|Copy all text files|
|`cp -r .* /dir/`|Copy hidden files|


 **Extra Tip**

```bash
alias cp='cp -i'
```

==> ဒီလို alias လုပ်ထားရင် copy တိုင်း မေးပြီးမှ overwrite လုပ်မယ်။

---

##  **Advanced `cp` Command Examples (15-19)**


### 15. **How to Create a Hard Link File Instead of Copying**

==> Hard link ဆိုတာက file တစ်ခုနဲ့ တူတဲ့ data block ကို pointer တစ်ခုနဲ့ ချိတ်လိုက်တာပါ။  အဲ့ဒါကြောင့် original file ကိုဖျက်သော်လည်း data က မပျက်ပါ။

```bash
ln file.txt hardlink.txt
```

==> ဒီကောင်က `file.txt` ကို `hardlink.txt` အနေနဲ့ **hard link** တစ်ခုဖန်တီးတယ်။

 **Note**

-` Hard link` ကို **`ln`** command နဲ့ပဲလုပ်တယ် (cp မဟုတ်)
- Hard link များက **same filesystem** ထဲမှာပဲ လုပ်လို့ရတယ်။

### 16. **How to Create a Soft Link (Symbolic Link) Instead of Copying**

==> `Soft link` (symbolic link) ဆိုတာ Original file ကို ညွှန်ပြနေတဲ့ shortcut လိုမျိုးပါ။  Original file ပျက်ရင် link ကလည်း invalid ဖြစ်သွားတယ်။

```bash
ln -s /home/user/file.txt link_to_file.txt
```

==> ဒီကောင်က `/home/user/file.txt` ကို `link_to_file.txt` အနေနဲ့ **symbolic link** ဖန်တီးတယ်။

 **Note**

- `-s` option = symbolic link
- File system မတူလည်း link လုပ်နိုင်တယ်။


### 17. **How to Preserve the File Attributes While Copying**

==> File attributes ဆိုတာမှာ  
- ==> `Permissions (rwx)`  
- ==> `Owner`  
- ==> `Group ` 
- ==> `Timestamps` (modified, created time)  စတဲ့ info တွေပါဝင်တယ်။

```bash
cp -p file.txt /home/user/Backup/
```

==> `-p` option သုံးတာနဲ့ file attributes တွေ ထားရှိတယ်။
**Tip** `-a` (archive) option သုံးရင် အထက်ပါအကုန်ပါမယ်။

```bash
cp -a file.txt /home/user/Backup/
```


### 18. **How to Perform Copy Operation Recursively**

==> Directory အပြည့်အဝ (subdirectories ပါ) copy လုပ်ချင်ရင် **recursive** option သုံးတယ်။

```bash
cp -r Project /home/user/Backup/
```

==> `Project` directory ထဲက files, subfolders အကုန် copy လုပ်တယ်။

**Shortcut version**

```bash
cp -a Project /home/user/Backup/
```

`-a` = `-r` + `-p` + extra preservation  
=> So, “recursive copy with attributes preserved”


### 19. **How to Copy Multiple Directories**

=> Directory အများအပြားကို တစ်ပြိုင်တည်း copy လုပ်ချင်ရင် —

```bash
cp -r Dir1 Dir2 /home/user/Backup/
```

==> `Dir1` နဲ့ `Dir2` နှစ်ခုလုံးကို `/home/user/Backup/` ထဲသို့ copy လုပ်တယ်။

 **With brace expansion:**

```bash
cp -r {Dir1,Dir2,Dir3} /home/user/Backup/
```

==> အနည်းဆုံး 3 directories ကို တပြိုင်နက် copy လုပ်နိုင်တယ်။


## **Quick Summary Table**

|No|Command|Description|
|---|---|---|
|10|`ln file.txt hardlink.txt`|Create hard link|
|11|`ln -s file.txt softlink.txt`|Create soft (symbolic) link|
|12|`cp -p file.txt /dir/`|Preserve attributes|
|13|`cp -r Folder /dir/`|Copy directory recursively|
|14|`cp -r {Dir1,Dir2} /dir/`|Copy multiple directories|


 **Extra Tip (Best Practice)**

```bash
cp -av source/ destination/
```

==> `-a` → archive  
==> `-v` → verbose  
==> ဒါက “Full safe copy” command ဖြစ်တယ် — attributes ထိန်းပြီး progress ပြတယ်။

---
