
---

##  Compression & Archiving


### 1 Archiving vs Compression

|Type|Purpose|Example|
|---|---|---|
|**Archiving**|Files တစ်ခုချင်းစီကို _အစုလိုက်ဖိုင်တစ်ခု_ အဖြစ်စုထားတယ်။|`tar`|
|**Compression**|File size ကို _သေးသွားအောင်_ ပြုလုပ်တယ်။|`gzip`, `bzip2`, `xz`, `zip`|


### 2 `tar` – Tape Archive Tool

**Purpose:** Files များစွာကို Archive (စုထား) လုပ်ဖို့ အသုံးပြုတယ်။

**Syntax:**

```bash
tar [options] [archive.tar] [files...]
```



####  Common Options

|Option|Description|
|---|---|
|`-c`|create new archive|
|`-x`|extract files|
|`-t`|list archive contents|
|`-v`|verbose (show progress)|
|`-f`|specify filename|
|`-z`|use gzip compression|
|`-j`|use bzip2 compression|
|`-J`|use xz compression|


####  Examples

**1. Create an archive:**

```bash
tar -cvf backup.tar Documents/
```

➡ `Documents/` folder ကို `backup.tar` အနေနဲ့ စုတယ်။

**2. Extract archive:**

```bash
tar -xvf backup.tar
```

➡ tar file ထဲက files တွေကို ပြန်ဖွင့်တယ်။

**3. View archive contents only:**

```bash
tar -tvf backup.tar
```


###  Compressed Archives

**gzip + tar (most common):**

```bash
tar -czvf backup.tar.gz Documents/
```

**bzip2 compression:**

```bash
tar -cjvf backup.tar.bz2 Documents/
```

**xz compression (best ratio):**

```bash
tar -cJvf backup.tar.xz Documents/
```

**Extract compressed tar:**

```bash
tar -xzvf backup.tar.gz     # gzip
tar -xjvf backup.tar.bz2    # bzip2
tar -xJvf backup.tar.xz     # xz
```

 **Diagram:**

```
Documents/ → [tar] → backup.tar → [gzip] → backup.tar.gz
```



### 3  `gzip` – Compress Individual Files

Single file only (not folder).

**Example:**

```bash
gzip report.txt
```

➡ file ကို compress လုပ်ပြီး `report.txt.gz` ဖြစ်မယ်။  
original file ကို ဖျက်ပြီး gzip file ပဲကျန်မယ်။

**Decompress:**

```bash
gunzip report.txt.gz
```

**Keep original file:**

```bash
gzip -c report.txt > report.txt.gz
```



###  `bzip2` – Better Compression than gzip

 bzip2 က gzip ထက် သေးသွားတယ် (slower though).

**Example:**

```bash
bzip2 myfile.txt
bunzip2 myfile.txt.bz2
```



###  `xz` – Ultra Compression (Best Ratio)

 Modern tool (used in distros like Arch Linux).  
**Example:**

```bash
xz data.img
unxz data.img.xz
```



### 6 `zip` & `unzip` – Cross-Platform (Windows Compatible)

 ZIP format က cross-platform ဖြစ်လို့ Windows/macOS/Linux အကုန်သုံးလို့ရတယ်။

**Example:**

```bash
zip -r project.zip project_folder/
```

➡ Folder အကုန်ကို zip file အနေနဲ့ ပြုလုပ်တယ်။

**Extract:**

```bash
unzip project.zip
```

**List files without extracting:**

```bash
unzip -l project.zip
```


### 7 Combine Commands

**Example – Backup & compress logs:**

```bash
tar -czvf logs_$(date +%F).tar.gz /var/log/
```

➡ အခုနေ့ရက်နဲ့ backup filename ဖြစ်မယ်။

**Example – Archive + checksum:**

```bash
tar -czf backup.tar.gz /home/kyaw/ && sha256sum backup.tar.gz > backup.sha256
```


 **Diagram (Concept):**

```
/home/kyaw/ → tar → backup.tar → gzip → backup.tar.gz → sha256sum
```

####  Summary Table

|Command|Description|Example|
|---|---|---|
|`tar -cvf`|create archive|`tar -cvf files.tar /dir`|
|`tar -xvf`|extract archive|`tar -xvf files.tar`|
|`tar -czvf`|create gzip archive|`tar -czvf backup.tar.gz dir/`|
|`gzip`|compress file|`gzip file.txt`|
|`gunzip`|decompress file|`gunzip file.txt.gz`|
|`bzip2`|high-ratio compress|`bzip2 file.txt`|
|`xz`|ultra compress|`xz file.txt`|
|`zip`|zip folder|`zip -r archive.zip folder/`|
|`unzip`|unzip files|`unzip archive.zip`|

### Homework (Backup Lab Challenge )

1. `/etc` ထဲက config files ကို tar.gz နဲ့ backup လုပ်ပါ။ 

```bash
  sudo tar -czvf etc_backup.tar.gz /etc
```

2. `/var/log` ထဲက log files ကို xz နဲ့ compress လုပ်ပါ။
3. `unzip`, `tar -tvf`, `gunzip` တို့နဲ့ ဖိုင်တွေကို စမ်းဖွင့်ပါ။
4. Bonus  – `find` command နဲ့ `.log` files တွေရှာပြီး တစ်ခုပဲ tar.gz ထဲထည့်ပါ။

```bash
  find /var/log -name "*.log" | tar -czvf logs.tar.gz -T -
```

5. Advanced
- Backup script တစ်ခုရေးပြီး `/home/kyaw/Documents/` ကို အလိုအလျောက် tar.gz backup လုပ်ပါ။  filename မှာ `$(date +%F_%H-%M)` ထည့်ပါ။


---



