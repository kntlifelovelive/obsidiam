
---

##  **`rm` Command – How to Remove Files and Directories in Linux (15 Examples)[RmAdvance](rmAdvance)**

###  **Usage**

```bash
rm [OPTION] FILE_OR_DIRECTORY
```

==> **`rm`** ဆိုတာက "remove"  Linux မှာ file တွေ၊ directory တွေကို ဖျက်ဖို့သုံးတဲ့ **powerful command** ဖြစ်ပါတယ်။ 
- => ဖျက်လိုက်တာကို **trash bin** မရှိပါ → အမြဲတမ်းပျက်သွားပါတယ်။


## **Basic Usage Examples**

###  **Example 1 – Remove a Single File**

```bash
rm file1.txt
```

==> `file1.txt` ကို ဖျက်တယ်။  အဲဒီ file မရှိရင် → error ပြမယ်။


### **Example 2 – Remove Multiple Files**

```bash
rm file1.txt file2.txt file3.txt
```

==> Files အများအပြားကို တပြိုင်နက် ဖျက်နိုင်တယ်။



###  **Example 3 – Remove Without Confirmation**

```bash
rm -f file.txt
```

==>  `-f` (force) သုံးရင် confirmation မလိုဘဲ ဖျက်တယ်။  Missing file ဖြစ်နေသော်လည်း error မပေးပါ။

###  **Example 4 – Remove with Confirmation**

```bash
rm -i file.txt
```

==> `-i` သုံးရင် တစ်ခုချင်း confirm မေးမယ်။

```
rm: remove regular file 'file.txt'? y
```


### **Example 5 – Remove All Files in a Folder**

```bash
rm *
```

==> လက်ရှိ directory ထဲက file အကုန်ဖျက်မယ်။  
(subfolders မဖျက်ပါ)
==> Dangerous — သတိထားသုံးပါ။

##  **Directory Removal Examples**

### **Example 6 – Remove Empty Directory**

```bash
rm -d emptydir
```

==> `rmdir` လိုပဲ empty directories ဖျက်နိုင်တယ်။


### **Example 7 – Remove Directory Recursively**

```bash
rm -r myfolder
```

==>  Folder အတွင်း file နဲ့ subfolder အကုန်ဖျက်မယ်။  (recursive removal)

- => အသုံးအများဆုံးပဲ။ သို့သော် `Dangerous`

###  **Example 8 – Remove Directory Recursively and Forcefully**

```bash
rm -rf myfolder
```

==>  **Comfirm မေးခြင်းမရှိဘဲ ဖျက်သွားမယ်။**  ==> Folder + Subfolders + Files အကုန်လုံး ဖျက်တယ်။
- => `သတိ `ဒီ command က system ကိုပင် ဖျက်နိုင်တယ်။


### **Example 9 – Remove All Files with Specific Extension**

```bash
rm *.log
```

==>  `.log` extension ပါတဲ့ file အကုန် ဖျက်တယ်။


### **Example 10 – Remove Files Interactively**

```bash
rm -i *.txt
```

==> `.txt` file တစ်ခုချင်း confirm မေးပြီးဖျက်တယ်။


###  **Example 11 – Remove Directory Using Wildcard**

```bash
rm -r testdir*
```

==> ` “testdir” `နဲ့စတဲ့ directories အကုန်ဖျက်တယ်။


###  **Example 12 – Remove Hidden Files**

```bash
rm -rf .*
```

==> ` Hidden files` (starting with `.`) ဖျက်မယ်။
- => `.bashrc`, `.config` စတဲ့ system files မဖျက်ဖို့ သတိထားပါ။

###  **Example 13 – Remove Files Listed in a Text File**

```bash
rm $(cat list.txt)
```

==> `list.txt` ထဲမှာပါတဲ့ file names အတိုင်း ဖျက်တယ်။
- => Example `list.txt`

```
a.txt
b.txt
c.txt
```


###  **Example 14 – Remove All Files Except One**

```bash
rm !(keep.txt)
```

==>  **Extended glob** သုံးပြီး keep.txt ကို မဖျက်ဘဲ  
အခြား files အကုန်ဖျက်တယ်။ သုံးဖို့အတွက် `shopt -s extglob` enable လုပ်ထားရမယ်။


###  **Example 15 – Combine with `find` Command**

```bash
find . -name "*.tmp" -type f -delete
```

==>  `.tmp` extension ပါတဲ့ file အကုန် recursive ဖျက်တယ်။  `find` နဲ့ပေါင်းသုံးလို့ precise & safe ဖြစ်တယ်။


##  **Option Summary Table**

|Option|Description|
|---|---|
|`-f`|Force remove (no confirm, no error)|
|`-i`|Interactive confirm before delete|
|`-r`|Recursive remove directories|
|`-rf`|Recursive + Force (dangerous)|
|`-d`|Remove empty directories only|
|`*`|Wildcard (all files)|


#  **Warning Zone**

- ==> **` Never run this as root`**

```bash
rm -rf /
```

==>  System files အကုန်ပျက်ပြီး OS boot မဖြစ်တော့ပါ

##  **Best Practices**

1. Always run with `-i` if you’re not 100% sure.
2. Double-check path before pressing Enter.
3. Use `ls` or `tree` command to verify what you’re deleting.
4. For safe deletion, consider using `trash-cli` (move to recycle bin).

---