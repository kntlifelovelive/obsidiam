
## **How to Use the Gzip Command in Linux (13 Practical Examples)**

---

## `gzip` ဆိုတာဘာလဲ

`gzip` (GNU zip) က **Linux file compression tool** တစ်ခုပဲဖြစ်ပြီး  
==> File size ကို ချုံ့ဖို့ (compress)  
==> Disk space ချွေတာဖို့  
==> File transfer လုပ်ရာမှာ ပိုမြန်အောင်လုပ်ဖို့ သုံးကြတာပါ။  
Compression ဖြစ်သွားရင် `.gz` extension ပါတယ်။
### **Basic Syntax**

```bash
gzip [OPTION] [FILE...]
```


##  **13 Useful Examples**

### **Example 1 – Compress a Single File**

```bash
gzip file.txt
```

➡ `file.txt` ကို compress လုပ်ပြီး `file.txt.gz` အဖြစ်သိမ်းမယ်။  
➡ Original file ကို delete လုပ်ပြီး `.gz` version သာကျန်မယ်။


### **Example 2 – Decompress a File**

```bash
gunzip file.txt.gz
```

➡ `.gz` file ကို ပြန်ဖွင့် (decompress) မယ်။  
➡ Output = `file.txt`


### **Example 3 – Compress Multiple Files**

```bash
gzip file1.txt file2.txt file3.txt
```

➡ တစ်ခါတည်းနဲ့ file ၃ ခုလုံးကို `.gz` format ဖြစ်အောင် compress လုပ်မယ်။


### **Example 4 – Keep Original File While Compressing**

```bash
gzip -k file.txt
```

➡ `-k` option က original file ကို delete မလုပ်ဘဲ `.gz` version သီးသန့် ထပ်ထားပေးမယ်။


### **Example 5 – Compress Entire Directory Recursively**

```bash
gzip -r myfolder/
```

➡ `myfolder` ထဲက file အားလုံးကို recursive (အတွင်းထိ) compress လုပ်မယ်။


### **Example 6 – Decompress Entire Directory Recursively**

```bash
gunzip -r myfolder/
```

➡ Folder တစ်ခုလုံးကို `.gz` files များအနေနဲ့ decompress လုပ်မယ်။


### **Example 7 – Set Compression Level**

```bash
gzip -9 bigfile.iso
```

➡ `-1` ဆိုရင် fastest (သေးနဲ့မြန်)  
➡ `-9` ဆိုရင် slowest but best compression (အများဆုံးချုံ့ပေးတယ်)  
➡ Default level က `-6` ဖြစ်တယ်။


### **Example 8 – Test Integrity of a Compressed File**

```bash
gzip -t file.txt.gz
```

➡ `.gz` file က corrupted ဖြစ်လား စစ်မယ်။  
➡ Output မထွက်ရင် OK ဖြစ်တယ်။


### **Example 9 – Display Compression Ratio**

```bash
gzip -l file.txt.gz
```

➡ Original size, compressed size, compression ratio တွေ ပြပေးမယ်။


### **Example 10 – Compress Output of a Command**

```bash
ls -l /etc | gzip > etc_list.gz
```

➡ `ls -l /etc` result ကို gzip နဲ့ compress လုပ်ပြီး `etc_list.gz` ထဲသိမ်းမယ်။


### **Example 11 – View Contents of Compressed File Without Extracting**

```bash
zcat file.txt.gz
```

➡ `zcat` က decompress temporarily လုပ်ပြီး terminal မှာ contents ပြပေးတယ်။


### **Example 12 – Combine Multiple Files into One and Compress**

```bash
tar -cvf backup.tar /home/kyaw && gzip backup.tar
```

➡ ပထမဆုံး `tar` နဲ့ folder ကို archive လုပ်ပြီး  
➡ နောက်မှာ `gzip` နဲ့ compress လုပ်မယ်။  
==> Output → `backup.tar.gz`


### **Example 13 – Extract a `.tar.gz` File**

```bash
tar -xzvf backup.tar.gz
```

➡ `.tar.gz` file ကို extract လုပ်ဖို့ ဒီ command သုံးနိုင်တယ်။


### **Option Summary Table**

|Option|Description|
|:--|:--|
|`-k`|Keep original file|
|`-r`|Compress recursively|
|`-1` to `-9`|Compression level|
|`-t`|Test compressed file|
|`-l`|Show compression ratio|
|`-v`|Verbose (show progress)|


## **Quick Note**

- `gzip` = compress
- `gunzip` = decompress
- `.gz` files တွေက mostly text files / logs တွေအတွက် အသုံးများတယ်
- Backup scripts & automation မှာလည်း `gzip` သုံးလေ့ရှိတယ်။

---

