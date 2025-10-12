

---

##  **`rmdir` Command – How to Remove Empty Directories in Linux (5 Examples)**

###  **Usage**

```bash
rmdir [OPTION] DIRECTORY
```

==> **rmdir** usage  
- => “Remove Directory” ဆိုတဲ့အဓိပ္ပါယ်ဖြစ်ပြီး  
- => **အတွင်းမှာ ဘာမှ မပါတဲ့ (empty)** directories ကိုပဲ ဖျက်နိုင်တယ်။


### **Example 1 – Remove a Single Empty Directory**

```bash
rmdir testdir
```

==> `testdir` ဆိုတဲ့ folder က **အတွင်းမှာ file မရှိရင်ပဲ** ဖျက်သွားမယ်။
- => Error: If it’s not empty →   “rmdir: failed to remove 'testdir': Directory not empty”

###  **Example 2 – Remove Multiple Empty Directories**

```bash
rmdir dir1 dir2 dir3
```

==> dir1, dir2, dir3 တို့က empty ဖြစ်ရင် အကုန်ဖျက်မယ်။  Empty မဟုတ်တဲ့ folder တစ်ခုရှိရင်တော့ error ပြမယ်။

### **Example 3 – Remove Nested Directories with `-p` Option**

```bash
rmdir -p project/src/test
```

==> ဒီကောင်က `project/src/test` → `test` directory ကို ဖျက်ပြီး  ၊ ပြီးရင် `src`၊ `project` တို့လည်း **empty ဖြစ်နေခဲ့ရင် ဆက်ဖျက်မယ်။**
- => Very useful when cleaning multiple empty subdirectories.


### **Example 4 – Remove Directory Using Wildcard**

```bash
rmdir testdir*
```

==>  ဒီဟာက `testdir1`, `testdir2`, `testdirA` စတဲ့   **testdir** နဲ့ စတဲ့ empty directories အကုန်ဖျက်မယ်။
- =>  Files ပါတဲ့ folder တွေကိုတော့ မဖျက်နိုင်ဘူး။


###  **Example 5 – Verify Empty Before Removing**

```bash
ls -l testdir
rmdir testdir
```

==> Directory ထဲမှာဘာမှ မရှိတာကို **ls** နဲ့ verify လုပ်ပြီးမှ **rmdir** သုံးတာ သုံးစွဲသူအတွက် ပိုလုံခြုံတယ်။
### **Pro Tip**

- Empty မဟုတ်တဲ့ folder ဖျက်ချင်ရင်တော့ `rmdir` မဖြစ်ပါ။

###  **Summary Table**

|Command|Description|
|---|---|
|`rmdir folder`|Remove one empty directory|
|`rmdir dir1 dir2`|Remove multiple empty directories|
|`rmdir -p path/to/folder`|Remove nested empty directories|
|`rmdir test*`|Remove all empty dirs starting with “test”|
|`rm -r folder`|Remove non-empty folder (next lesson)|


**Note**  
`rmdir` က safe command တစ်ခုပဲဖြစ်တယ်။  သုံးရတာ လွယ်ပြီး **system safe** ဖြစ်တယ်။

---