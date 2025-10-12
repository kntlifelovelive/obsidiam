
---

##  **`mv` Command – Move or Rename Files and Directories**

🔹 **Usage:** `mv [options] source destination`  
🔹 **Full meaning:** _Move_  
🔹 **Purpose:**  
- ==> Linux မှာ file (သို့) directory တစ်ခုကို  တခြားနေရာသို့ **ရွှေ့ခြင်း (move)**  သို့မဟုတ်  
- ==> **နာမည်ပြောင်းခြင်း (rename)** လုပ်ဖို့ အသုံးပြုပါတယ်။

##  **Basic Syntax**

```bash
mv [OPTION] SOURCE DESTINATION
```


##  **Common Options**

|Option|Description|
|---|---|
|`-i`|Confirm before overwrite (interactive mode)|
|`-f`|Force move without asking|
|`-n`|Do not overwrite existing files|
|`-v`|Show what is being moved (verbose mode)|


##  **9 Practical Examples of `mv` Command**


### 1 Move a file to another directory

```bash
mv file.txt /home/user/Documents/
```

==> `file.txt` ကို `Documents` folder ထဲသို့ ရွှေ့တယ်။

### 2 Rename a file

```bash
mv oldname.txt newname.txt
```

==> File name ကို **oldname.txt → newname.txt** ပြောင်းလိုက်တယ်။


### 3. Move multiple files to a directory

```bash
mv file1.txt file2.txt /home/user/Desktop/
```

==> File နှစ်ခုလုံးကို Desktop သို့ ရွှေ့တယ်။

### 4. Move a directory

```bash
mv Project1 /home/user/Projects/
```

==> `Project1` directory ကို `/home/user/Projects/` ထဲသို့ ရွှေ့တယ်။


### 5. Rename a directory

```bash
mv OldFolder NewFolder
```

==> Folder name ကို ပြောင်းလိုက်တယ်။


### 6. Move and overwrite without asking (force)

```bash
mv -f file.txt /home/user/
```

==> လက်ရှိ file ကိုမမေးဘဲ overwrite လုပ်တယ်။


### 7. Move but ask before overwrite (interactive)

```bash
mv -i file.txt /home/user/
```

==> Overwrite လုပ်မလား မေးပြီးမှ move တယ်။

### 8. Move and display progress (verbose)

```bash
mv -v *.txt /home/user/Documents/
```

==> Move လုပ်သမျှ file တွေကို message ပြပေးတယ်။

### 9. Combine move with wildcard

```bash
mv *.jpg Pictures/
```

==> `.jpg` file အားလုံးကို `Pictures` directory ထဲသို့ ရွှေ့တယ်။

##  **Quick Summary Table**

|Command|Description|
|---|---|
|`mv file.txt /dir/`|Move file to another directory|
|`mv old.txt new.txt`|Rename a file|
|`mv Folder1 Folder2`|Rename/move directories|
|`mv -i file /dir/`|Confirm before overwrite|
|`mv -f file /dir/`|Force move without asking|
|`mv -v file /dir/`|Verbose output|
|`mv *.jpg Pictures/`|Move all JPG files|
|`mv file1 file2 dir/`|Move multiple files|
|`mv Project /Backup/`|Move a directory to another place|


**Extra Tip (Brace Expansion + mv)** [Advance Usage](AdvanceLinuxCommands/100+LinuxEfficentCommandLine/mvadvance.md)

```bash
mv {file1.txt,file2.txt} /home/user/Downloads/
```

==> Brace expansion နဲ့ files များစွာ တပြိုင်နက်ရွှေ့နိုင်တယ်။

