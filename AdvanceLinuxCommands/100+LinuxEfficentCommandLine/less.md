
  
## **How to Read Contents of Text Files Efficiently in Linux (6 Examples)**  

`less` command ကို file contents ကို scrollable way နဲ့ ဖတ်ချင်တဲ့အခါသုံးတာပါ။  
အထူးသဖြင့် log file, config file, source code file တွေကို ဖတ်တဲ့အခါမှာ **less** က ပိုလှပါတယ်။   mouse scroll, up/down arrow keys, PgUp/PgDn တို့သုံးလို့ရပါတယ်။


###  **Command Usage**

==> **less** → display file content one page at a time  
==> **Usage Syntax:**

```bash
less [OPTIONS] [FILENAME]
```



##  **Examples**

### **Example 1 – View a File with `less`**

```bash
less file.txt
```

➡ file.txt ထဲက content ကို page by page ဖတ်နိုင်မယ်။  
➡ **Press `q`** to quit the viewer.


### **Example 2 – View Multiple Files**

```bash
less file1.txt file2.txt
```

➡ file1.txt ပြီးရင် **n** နဲ့ နောက် file သွားနိုင်တယ်။  
➡ **p** နဲ့ ပြန်လာနိုင်တယ်။



### **Example 3 – View Command Output Using Pipe**

```bash
ls -l /etc | less
```

➡ `/etc` directory ထဲက list ကို page by page ကြည့်နိုင်တယ်။  
➡ အခုလို **| less** သုံးတာက အထူးအသုံးများတဲ့နည်းဖြစ်တယ်။


### **Example 4 – Search Text Inside the File**

```bash
less file.txt
```

➡ အတွင်းမှာ `/word` လို့ရိုက်ပြီး search လုပ်နိုင်တယ်။  
➡ `n` နဲ့ next result သွားနိုင်တယ်၊ `N` နဲ့ previous result သွားနိုင်တယ်။



### **Example 5 – Show Line Numbers**

```bash
less -N file.txt
```

➡ file ထဲက line number တွေပါပြပေးမယ်။



### **Example 6 – Start from a Specific Line Number**

```bash
less +50 file.txt
```

➡ file.txt ကို line 50 မှ စဖတ်မယ်။



##  **Useful Navigation Keys inside `less`**

|Key|Function|
|---|---|
|↑ / ↓|Scroll one line up/down|
|Space|Next page|
|b|Previous page|
|g|Go to first line|
|G|Go to last line|
|/word|Search for “word”|
|n|Next match|
|q|Quit|



##  **Summary**

- `less` က `cat` 보다 သုံးရတာအဆင်ပြေပြီး file ကြီးတွေ ဖတ်ဖို့ သင့်တော်တယ်။
- **`cat`** → quick view only
- **`less`** → scroll, search, navigate

---

