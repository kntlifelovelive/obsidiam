
---

##  **`cat` Command – How to Print or View Contents of Files in Linux (13 Examples)**

###  **Usage**

```bash
cat [OPTION] [FILE]
```

==> **`cat`** ဆိုတာက `“concatenate”` ဆိုတဲ့ စကားလုံးရဲ့ အတိုကောက်ပါ။  
==> အဓိပ္ပါယ်ကတော့ – **ဖိုင်အကြောင်းအရာကို ဖတ်ကြည့်တာ၊ ပြတာ၊ ပေါင်းတာ** ဖြစ်ပါတယ်။


##  **Basic Examples**

###  **Example 1 – Display a File Content**

```bash
cat file1.txt
```

==>Terminal ပေါ်မှာ `file1.txt` ရဲ့ အကြောင်းအရာကို တန်းပြတယ်။


###  **Example 2 – Display Multiple Files Together**

```bash
cat file1.txt file2.txt
```

==> `file1.txt` နဲ့ `file2.txt` ရဲ့ content တွေကို  တစ်ပြိုင်တည်း terminal ပေါ်ပြတယ်။


###  **Example 3 – Create a New File with `cat`**

```bash
cat > newfile.txt
```

==> Enter ပြီးရင် ရေးချင်တာ ရိုက်လို့ရတယ်။  ပြီးရင် **Ctrl + D** (End of File) နှိပ်လိုက်တာနဲ့ file ဖန်တီးပြီးသွားမယ်။

###  **Example 4 – Append Data to an Existing File**

```bash
cat >> existingfile.txt
```

==> ရှိပြီးသား file ထဲကို **နောက်ထပ်စာသား append** လုပ်ဖို့သုံးတယ်။  ပြီးရင် Ctrl + D နဲ့ ပြီးတယ်။



### 🔹 **Example 5 – Combine Multiple Files into One**

```bash
cat file1.txt file2.txt > combined.txt
```

==> `file1` နဲ့ `file2` ရဲ့ content တွေကို  ပေါင်းပြီး `combined.txt` ထဲမှာ သိမ်းတယ်။


###  **Example 6 – View File with Line Numbers**

```bash
cat -n file1.txt
```

==> File ထဲက စာကြောင်းတိုင်းကို line number နဲ့အတူပြတယ်။


### 🔹 **Example 7 – Squeeze Blank Lines**

```bash
cat -s file1.txt
```

==> File ထဲမှာ blank line များများရှိရင်  တစ်ကြောင်းအနေနဲ့သာ ပြပေးတယ်။


###  **Example 8 – Display End of Lines with `$`**

```bash
cat -E file1.txt
```

==> Line တစ်ကြောင်းစီရဲ့ နောက်မှာ `$` ပြပြီး  Line break များကို ရှင်းရှင်းလင်းလင်းမြင်နိုင်တယ်။


###  **Example 9 – Display Non-printable Characters**

```bash
cat -v file1.txt
```

==> Tab, newline, control characters စတဲ့  non-printable symbols တွေကို ဖော်ပြတယ်။


### 🔹 **Example 10 – View Large File with `less` or `more`**

```bash
cat file.txt | less
```

==> File ကြီးကြီးဖတ်ချင်ရင် `less` နဲ့တွဲသုံးတာအဆင်ပြေတယ်။  (scroll လုပ်လို့ရ)


###  **Example 11 – Redirect Output to Another Command**

```bash
cat file.txt | grep "keyword"
```

==> File ထဲက “keyword” ပါတဲ့ စာကြောင်းတွေကို  `grep` နဲ့ ရှာဖွေဖော်ပြတယ်။


###  **Example 12 – Display Contents in Reverse Order**

```bash
tac file1.txt
```

==> `cat` ကို ဗြောင်းပြန်လှည့်သုံးတာက `tac` အကြောင်းအရာတွေကို **နောက်ဆုံးကနေ ပထမအစပိုင်းအထိ ပြတယ်။**


###  **Example 13 – Display Multiple Files and Create Log**

```bash
cat *.log > all_logs.txt
```

==> Directory ထဲက `.log` files အကုန်ယူပြီး  `all_logs.txt` ထဲမှာ merge လုပ်ပေးတယ်။


##  **Option Summary Table**

|Option|Description|
|---|---|
|`cat file`|Display file contents|
|`cat > file`|Create new file|
|`cat >> file`|Append text to existing file|
|`cat file1 file2 > newfile`|Merge multiple files|
|`cat -n`|Show line numbers|
|`cat -s`|Remove repeated blank lines|
|`cat -E`|Show `$` at end of line|
|`tac file`|Display file in reverse|


## **Real-life Tips**

- `cat /etc/os-release` → OS info ကိုဖတ်နိုင်တယ်
- `cat /proc/cpuinfo` → CPU information ကြည့်နိုင်တယ်
- `cat file | grep error` → Logs ထဲမှာ error များရှာဖို့ အသုံးများတယ်


---
