
  
##  **How to Create and Extract Tar Archive Files in Linux (21 Practical Examples)**  



`tar` ဆိုတာက **tape archive** ဆိုတဲ့ abbreviation ပါ။  Linux မှာ file တွေ folder တွေကို **တစ်ဖိုင်တည်းအဖြစ် compress / backup** လုပ်ဖို့ အသုံးများပါတယ်။

##  **Command Usage**

**tar** – create, view, extract, or manage archive files  
**Syntax**

```bash
tar [OPTIONS] [ARCHIVE_FILE.tar] [FILES or DIRECTORIES]
```


##  **Examples**

#### **Example 1 – Create a Tar Archive File**

```bash
tar -cvf backup.tar file1.txt file2.txt
```

➡ `-c` = create  
➡ `-v` = verbose (show progress)  
➡ `-f` = specify filename  
==> output → `backup.tar`

### **Example 2 – Create a Tar Archive from a Directory**

```bash
tar -cvf project.tar /home/user/project/
```

➡ `/home/user/project` directory ကို `project.tar` ထဲမှာ archive လုပ်မယ်။


### **Example 3 – Extract a Tar Archive**

```bash
tar -xvf backup.tar
```

➡ `-x` = extract  
➡ `-v` = show extracting files  
➡ `-f` = file name



### **Example 4 – Extract to a Specific Directory**

```bash
tar -xvf backup.tar -C /tmp
```

➡ `/tmp` folder ထဲကို extract လုပ်မယ်။


### **Example 5 – View Contents Without Extracting**

```bash
tar -tvf backup.tar
```

➡ tar file ထဲမှာ ပါတဲ့ file list ကိုသာ ကြည့်နိုင်တယ်။


### **Example 6 – Create a Compressed Tar Archive (gzip)**

```bash
tar -czvf backup.tar.gz /home/user/docs/
```

➡ `-z` = compress with gzip  
==> output → `backup.tar.gz`



### **Example 7 – Extract a `.tar.gz` File**

```bash
tar -xzvf backup.tar.gz
```



### **Example 8 – Create a `.tar.bz2` Archive (bzip2 compression)**

```bash
tar -cjvf backup.tar.bz2 /home/user/files/
```

➡ `-j` = use bzip2 compression


### **Example 9 – Extract `.tar.bz2` Archive**

```bash
tar -xjvf backup.tar.bz2
```

---

### **Example 10 – Create an `.xz` Compressed Archive**

```bash
tar -cJvf backup.tar.xz /var/log/
```

➡ `-J` = use xz compression (smallest size)


### **Example 11 – Extract `.tar.xz` File**

```bash
tar -xJvf backup.tar.xz
```


### **Example 12 – Add Files to Existing Archive**

```bash
tar -rvf backup.tar newfile.txt
```

➡ `-r` = append to existing archive


### **Example 13 – Update Files in Archive**

```bash
tar -uvf backup.tar file.txt
```

➡ only newer files will replace old ones inside archive


### **Example 14 – Exclude Specific Files**

```bash
tar -cvf backup.tar --exclude='*.log' /home/user/
```



### **Example 15 – Create Archive with Absolute Paths**

```bash
tar -cvpf fullpath.tar /etc /var/log
```

➡ `-p` = preserve permissions  
➡ `-f` = file name


### **Example 16 – Extract Archive While Preserving Permissions**

```bash
tar -xvpf fullpath.tar
```


### **Example 17 – Create a Tar File from a List**

```bash
tar -cvf backup.tar -T filelist.txt
```

➡ filelist.txt ထဲက file list ကိုပဲ backup လုပ်မယ်။


### **Example 18 – Split Large Tar File**

```bash
tar -cvzf - /home/user | split -b 500M - backup_part.tar.gz.
```

➡ 500MB size ဖြင့် တစ်ပိုင်းချင်းစီ ခွဲမယ်။


### **Example 19 – Combine Split Parts Back**

```bash
cat backup_part.tar.gz.* > full_backup.tar.gz
```



### **Example 20 – Verify Contents of Archive**

```bash
tar -tvf backup.tar > list.txt
diff list.txt <(tar -tvf backup.tar)
```

➡ Compare file list for verification.



### **Example 21 – Extract Specific File from Archive**

```bash
tar -xvf backup.tar file2.txt
```

➡ file2.txt ကိုပဲ extract လုပ်မယ်။


##  **Quick Option Summary**

|Option|Meaning|
|---|---|
|-c|Create archive|
|-x|Extract archive|
|-t|List contents|
|-v|Verbose (show files)|
|-f|Filename (must be last before file name)|
|-z|Use gzip compression|
|-j|Use bzip2 compression|
|-J|Use xz compression|
|-C|Extract to specific dir|


## **summary note**

`tar` command က Linux system တွေမှာ  ==> Backup  ==> Transfer  ==> Compression  ==> Restore  
လုပ်ရာမှာ မရှိမဖြစ်ပါဝင်တဲ့ tool တစ်ခုပဲဖြစ်တယ်။

