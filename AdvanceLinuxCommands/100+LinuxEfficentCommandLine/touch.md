
---

##  **`touch` Command – How to Create or Modify Files and Change Timestamps in Linux (8 Examples)**

###  **Usage**

```bash
touch [OPTION] FILE_NAME
```

==> **`touch`** ဆိုတာက  File အသစ်တစ်ခုဖန်တီးဖို့ သုံးတာပါ။  File ရှိပြီးသားဖြစ်ရင်တော့ **timestamp (modified time)** ကို update လုပ်ပေးတယ်။


##  **Basic Examples**

###  **Example 1 – Create a New Empty File**

```bash
touch file1.txt
```

==> `file1.txt` မရှိရင် အသစ်ဖန်တီးမယ်။  ရှိပြီးသားဆိုရင် modified date ကို update လုပ်မယ်။


###  **Example 2 – Create Multiple Files at Once**

```bash
touch file1 file2 file3
```

==> file1, file2, file3 တို့ကို တပြိုင်နက် ဖန်တီးတယ်။


###  **Example 3 – Update Timestamp of Existing File**

```bash
touch oldfile.txt
```

==> File ရှိပြီးသားဖြစ်ရင် `modified date` ကို **current time** နဲ့ update လုပ်တယ်။  (အဖွင့်အပိတ် မလိုပဲ refresh လုပ်သလိုပါ။)


###  **Example 4 – Set a Specific Timestamp**

```bash
touch -t 202510122030 file1.txt
```

==> `-t` option နဲ့ မိမိလိုချင်တဲ့ date/time ကို ပေးနိုင်တယ်။  
==> Format: `[[CC]YY]MMDDhhmm[.ss]`  
==> ဥပမာ - 2025/10/12 20:30 PM


###  **Example 5 – Change Access Time Only**

```bash
touch -a file1.txt
```

==> File ရဲ့ **Access Time (last read time)** ကိုပဲ update လုပ်မယ်။


###  **Example 6 – Change Modify Time Only**

```bash
touch -m file1.txt
```

==> File ရဲ့ **Modified Time (last write time)** ကိုပဲ update လုပ်မယ်။


###  **Example 7 – Use Another File’s Timestamp**

```bash
touch -r source.txt target.txt
```

==>. `target.txt` ရဲ့ timestamp ကို  
==> `source.txt` ရဲ့ timestamp နဲ့တူအောင် ပြောင်းတယ်။
==> Useful when syncing files or comparing changes.


###  **Example 8 – Create File in Another Directory**

```bash
touch /home/user/Documents/newfile.txt
```

==> ပေးထားတဲ့ path ထဲမှာ file တစ်ခုဖန်တီးတယ်။


##  **Option Summary Table**

|Option|Description|
|---|---|
|`-a`|Change access time only|
|`-m`|Change modify time only|
|`-r file`|Use another file’s timestamp|
|`-t`|Set specific date/time|
|_(no option)_|Create or update file timestamp|


##  **Real-world Usage Tips**

1. New file ဖန်တီးချင်ရင် → `touch new.txt`
2. Git repo မပြောင်းလှဲဘဲ time update ချင်ရင် → `touch -m file.py`
3. Backup script တွေမှာ အချိန်စစ်ဖို့အတွက် မရှိရင် `touch` နဲ့ ဖန်တီးထားနိုင်တယ်။
4. Logs ဖိုင်များတွင် auto timestamp သုံးဖို့အတွက် ပိုအဆင်ပြေတယ်။


##  Example: Combine with `ls -l` to Verify

```bash
touch demo.txt
ls -l demo.txt
```

==> “Modified” column မှာ time ပြောင်းသွားတာတွေ့မယ်။

---
