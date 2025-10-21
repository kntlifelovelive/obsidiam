
---

##  **`echo` Command – How to Print Line of Text or String in Linux (15 Examples)**

###  **Usage**

```bash
echo [OPTION] [STRING]
```

==> **`echo`** ဆိုတာက string (စာသား) သို့မဟုတ် variable တန်ဖိုးကို terminal ပေါ်ထုတ်ပြဖို့ အသုံးပြုတဲ့ command ဖြစ်ပါတယ်။


##  **Basic Examples**

###  **Example 1 – Print Simple Text**

```bash
echo Hello World
```

==> Output => `Hello World`


### **Example 2 – Print Text with Quotes**

```bash
echo "Hello Linux World"
```

==> Double quotes သုံးတာက spaces ပါတဲ့ စာသားကို တစ်စုအနေနဲ့ ပြဖို့ဖြစ်တယ်။



###  **Example 3 – Print Blank Line**

```bash
echo ""
```

==> Blank line တစ်ကြောင်း ထုတ်ပေးတယ်။


###  **Example 4 – Print Variables**

```bash
name="Kyaw"
echo "My name is $name"
```

==> Output => `My name is Kyaw`


###  **Example 5 – Use Escape Characters**

```bash
echo -e "Line1\nLine2\nLine3"
```

==> `-e` option နဲ့ **newline (\n)**, **tab (\t)** စတဲ့ escape characters ကို အသုံးပြုနိုင်တယ်။  
Output 

```
Line1
Line2
Line3
```


###  **Example 6 – Disable Newline at End**

```bash
echo -n "Printing without newline"
```

==> Normally `echo` ပြီးရင် newline တစ်ကြောင်း အလိုအလျောက်ထုတ်တယ်။  `-n` သုံးရင် newline မထုတ်ပါ။



###  **Example 7 – Print Tab-separated Text**

```bash
echo -e "Name\tAge\tJob"
```

==>  Output 

```
Name    Age     Job
```


###  **Example 8 – Combine Text and Command Output**

```bash
echo "Today is $(date)"
```

==> Command substitution နဲ့ command output ကို text ထဲမှာထည့်နိုင်တယ်။  Output ==> `Today is Sun Oct 12 13:15:00 2025`


###  **Example 9 – Print Environment Variable**

```bash
echo $HOME
```

==> `/home/username` ဆိုတဲ့ home directory path ပြမယ်။


###  **Example 10 – Redirect Output to File**

```bash
echo "Log Created on $(date)" > log.txt
```

==> Output ကို file ထဲသို့ သိမ်းတယ်။  
==> **`> `** ဆိုတာ overwrite / create file အသစ်။  
==> **`>>`** ဆိုတာ append.


###  **Example 11 – Append Data to Existing File**

```bash
echo "New entry added" >> log.txt
```

==> `log.txt` ထဲကို အကြောင်းအရာ အသစ် ထပ်ထည့်တယ်။


###  **Example 12 – Use Color in Output**

```bash
echo -e "\e[31mThis is Red Text\e[0m"
```

==> **`\e[31m`** → Red color  
==> **`\e[0m`** → Reset color

Basic Color Codes

|Color|Code|
|---|---|
|Red|`\e[31m`|
|Green|`\e[32m`|
|Yellow|`\e[33m`|
|Blue|`\e[34m`|
|Magenta|`\e[35m`|
|Cyan|`\e[36m`|


###  **Example 13 – Combine Multiple Lines**

```bash
echo -e "System Info:\nHostname: $(hostname)\nUser: $(whoami)"
```

==> System info ကို multi-line ပုံစံနဲ့ ပြတယ်။


###  **Example 14 – Print from Script**

```bash
#!/bin/bash
echo "Backup process started..."
```

➡️ Script ထဲမှာ user ကို message ပြဖို့ အသုံးများတယ်။

---

### 🔹 **Example 15 – Use Echo for Debugging**

```bash
echo "Value of x is $x"
```

==> Script ထဲမှာ variable values စစ်ဖို့ အသုံးများတယ်။


##  **Option Summary Table**

|Option|Description|
|---|---|
|`-e`|Enable escape sequences like `\n`, `\t`, etc.|
|`-n`|No newline at the end|
|`> file`|Redirect output to file (overwrite)|
|`>> file`|Append output to file|

##  **Real-world Use Cases**

- Print messages in shell scripts
- Show variable values or debug info
- Create formatted logs with timestamps
- Display system info dynamically

---

