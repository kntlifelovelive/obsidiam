

`touch test{10}.txt` ကို **Shell Expansion** နဲ့ **Braces `{}`** ဘယ်လိုအလုပ်လုပ်သလဲ ? ... ။

* * *

## 🔹🥰 **Shell Brace Expansion (Shell မှာ `{}` သုံးတဲ့နည်း)**

📌 **Linux Shell (Bash, Zsh) မှာ \`{}\`\` ကိုသုံးပြီး Multiple Files, Sequences, Lists ပြုလုပ်နိုင်ပါတယ်။**

📌 **File Name များစုစည်းဖန်တီးချင်ရင်** `{start..end}` ပုံစံနဲ့ သုံးရမယ်။

* * *

## **Multiple Files with Number Sequences**

📌 **10 ခုဖန်တီးချင်ရင်**

```bash
touch test{1..10}.txt
```

📌 **Output:**

```bash
test1.txt  test2.txt  test3.txt  test4.txt  test5.txt
test6.txt  test7.txt  test8.txt  test9.txt  test10.txt
```

📌 **Step Value (ထပ်လိုချင်တဲ့အခါ)**

```bash
touch test{1..10..2}.txt
```

📌 **Output:**

```bash
test1.txt  test3.txt  test5.txt  test7.txt  test9.txt
```

📌 **Leading Zeros (00, 01, 02 Format)**

```bash
touch test{01..10}.txt
```

📌 **Output:**

```bash
test01.txt  test02.txt  test03.txt  test04.txt ... test10.txt
```

* * *

## **Multiple File Types ဖန်တီးရန်**

📌 **Different Extensions**

```bash
touch file{1..3}.{txt,log,csv}
```

📌 **Output:**

```bash
file1.txt  file1.log  file1.csv
file2.txt  file2.log  file2.csv
file3.txt  file3.log  file3.csv
```

📌 **Different Prefix & Suffix**

```bash
touch {report,summary}_2024.txt
```

📌 **Output:**

```bash
report_2024.txt  summary_2024.txt
```

* * *

## **Parentheses `{}` နဲ့ Mistake မဖြစ်စေချင်ရင်**

📌 **Shell Expansion ဖြစ်မယ်**  
✅ `touch test{1..10}.txt`  
✅ `touch test{01..10}.txt`  
✅ `touch test{a..z}.txt`

📌 **Literal ဖြစ်မယ် (Variable Expansion )**  
❌ `touch test{10}.txt` **(Single Value မဖြစ်သင့်) → test{10}.txt**  
❌ `touch test{a}.txt` **(Literal များသာ)**

* * *

### **Summary**

✔️ `{}` ကို **List** / **Sequence** / **Multiple Extensions** ဖန်တီးဖို့ အသုံးပြုနိုင်  
✔️ `{start..end}` - Number Sequences  
✔️ `{word1,word2}` - Multiple Values  
✔️ `{start..end..step}` - Step Values  
✔️ `{name1,name2}_{date1,date2}.ext` - Combination

* * *

😃 **Bash Expansions** တွေကို **Shell Scripting** မှာ အသုံးများတဲ့ **techniques** များ ။

Bash Shell မှာ **Expansions** တွေက **Variable Handling**, **Pattern Matching**, **File Naming**, **Looping** တွေအတွက် အသုံးဝင်ပါတယ်။

* * *

## **1\. Brace Expansion `{}`**

📌 **Syntax:**

```bash
echo {start..end}
```

📌 **Example:**

```bash
echo {1..5}
```

📌 **Output:**

```bash
1 2 3 4 5
```

📌 **Step Value (Increment/Decrement)**

```bash
echo {1..10..2}    # 1, 3, 5, 7, 9
echo {10..1..-2}   # 10, 8, 6, 4, 2
```

📌 **Alphabet Sequences**

```bash
echo {a..z}
echo {A..Z}
```

📌 **Combine Words**

```bash
echo {home,user,root}/folder
```

📌 **Output:**

```bash
home/folder user/folder root/folder
```

* * *

## **2\. Tilde Expansion `~` (Home Directory)**

📌 **Current User Home Path**

```bash
echo ~
```

📌 **Other User's Home Path**

```bash
echo ~username
```

📌 **Path Combination**

```bash
echo ~/Documents
```

* * *

## **3\. Variable Expansion `$VAR`**

📌 **Environment Variables**

```bash
echo $USER    # Current User
echo $HOME    # Home Directory
echo $SHELL   # Default Shell
```

📌 **Default Value Assignments**

```bash
echo ${MYVAR:-"Default Value"}
```

👉 **If MYVAR is empty, print "Default Value"**

📌 **Substring Extraction**

```bash
STRING="Hello Bash"
echo ${STRING:6}   # "Bash"
echo ${STRING:0:5} # "Hello"
```

* * *

## Bash **substring** Syntax :

```bash
${string:start_index:length}
```

- `string` → ရယူချင်တဲ့ string variable ဖြစ်ပါတယ်။
- `start_index` → substring ကိုစယူချင်တဲ့ index number ဖြစ်ပါတယ် (0-based index ဖြစ်တယ်)။
- `length` → substring ရဲ့ အရှည် (optional ဖြစ်တယ်၊ default က `:`Start`:`End အထိ ဘယ်နှစ်လုံးရယူမလဲဆိုတာကို သတ်မှတ်ဖို့ဖြစ်ပါတယ်)။

### Example:

```bash
STRING="Hello Bash"
echo ${STRING:6}       # Output: "Bash"
echo ${STRING:0:5}     # Output: "Hello"
```

#### Detail:

1.  `${STRING:6}` → `start_index` က `6` ဖြစ်တဲ့အတွက် `STRING` က `"Hello Bash"` မှာ index 6 ကနေ စပြီး string ကို `"Bash"` ထုတ်ပြပါမယ်။
2.  `${STRING:0:5}` → `start_index` က `0` (string ရဲ့အစ) မှာ စပြီး 5 characters ကိုယူမယ်ဆိုတာပါ၊ ထုတ်တဲ့ result က `"Hello"` ဖြစ်ပါလိမ့်မယ်။

### အခြားသော Syntax:

- `${string:start_index}` → length မပေးလိုက်ရင် start_index ကနေ အဆုံးအထိ substring ကိုယူမယ်။
- `${string:-length}` → string ရဲ့ အဆုံးမှ length characters ကို ရယူနိုင်ပါတယ်။

```bash
STRING="Hello Bash"
echo ${STRING: -4}   # Output: "Bash"
```

**မှတ်ချက်**: Negative indexing တွေကိုအသုံးပြုလို့ရပါတယ်၊ `-1` မှာ string ရဲ့ နောက်ဆုံး character ကိုရယူပါမယ်! 🥰

## **4\. Command Substitution `$(command)`**

📌 **Basic Usage**

```bash
echo "Today is $(date)"
```

📌 **Store Command Output to Variable**

```bash
FILES=$(ls)
echo "Files: $FILES"
```

* * *

## **5\. Arithmetic Expansion `$((expression))`**

📌 **Basic Calculation**

```bash
echo $((5 + 3))
echo $((10 * 2))
echo $((100 / 5))
```

📌 **Using Variables in Calculation**

```bash
A=10
B=5
echo $((A + B))
```

* * *

## **6\. Globbing (Wildcard Expansion) `* ? []`**

📌 **Match All Files**

```bash
ls *.txt   # All .txt files
ls file?.txt  # file1.txt, file2.txt
ls file[1-3].txt # file1.txt, file2.txt, file3.txt
```

* * *

## 🔥 **7\. Process Substitution `<(command)`**

📌 **Compare Two Outputs**

```bash
diff <(ls dir1) <(ls dir2)
```

📌 **Sort Command Output**

```bash
sort <(ls)
```

* * *

## **8\. Parameter Expansion (String Manipulation)**

📌 **Remove Prefix & Suffix**

```bash
FILE="backup.tar.gz"
echo ${FILE%.gz}   # Remove .gz (Suffix)
echo ${FILE#backup.} # Remove backup. (Prefix)
```

📌 **Replace Substring**

```bash
TEXT="I like bash scripting"
echo ${TEXT/bash/zsh}  # "I like zsh scripting"
```

* * *

### **Summary**

✔️ **Brace Expansion** `{}` - Sequences & Combinations  
✔️ **Tilde Expansion** `~` - Home Directory  
✔️ **Variable Expansion** `$VAR` - Environment Variables  
✔️ **Command Substitution** `$(command)` - Run Commands Inside Commands  
✔️ **Arithmetic Expansion** `$(( ))` - Math Calculations  
✔️ **Globbing** `* ? []` - Filename Matching  
✔️ **Process Substitution** `<(command)` - Compare Outputs  
✔️ **Parameter Expansion** - String Manipulation

* * *

👉 **Bash Scripting နဲ့ Terminal မှာ အသုံးများတဲ့ Expansion တွေပါ။**

* * *

## **Bash Expansions Cheat Sheet (Table Format)**

| **Expansion Type** | **Syntax** | **Example** | **Output** |
| --- | --- | --- | --- |
| **Brace Expansion** | `{1..5}` | `echo {1..5}` | `1 2 3 4 5` |
|     | `{1..10..2}` | `echo {1..10..2}` | `1 3 5 7 9` |
|     | `{a..z}` | `echo {a..e}` | `a b c d e` |
|     | `{file1,file2}.txt` | `echo {file1,file2}.txt` | `file1.txt file2.txt` |
| **Tilde Expansion** | `~` | `echo ~` | `/home/kyaw` |
|     | `~user` | `echo ~root` | `/root` |
|     | `~/Documents` | `echo ~/Documents` | `/home/kyaw/Documents` |
| **Variable Expansion** | `$VAR` | `echo $USER` | `kyaw` |
|     | `${VAR:-default}` | `echo ${MYVAR:-"No Value"}` | `No Value` |
|     | `${VAR:offset:length}` | `STRING="Hello Bash"; echo ${STRING:6}` | `Bash` |
| **Command Substitution** | `$(command)` | `echo "Today is $(date)"` | `Today is Wed Jan 31 12:34:56` |
|     | `` `command` `` | ``echo "Files: `ls`"`` | `Files: file1 file2` |
| **Arithmetic Expansion** | `$((expression))` | `echo $((5 + 3))` | `8` |
|     | `$((VAR1 + VAR2))` | `A=10; B=5; echo $((A + B))` | `15` |
| **Globbing (Wildcard Expansion)** | `*` | `ls *.txt` | `file1.txt file2.txt` |
|     | `?` | `ls file?.txt` | `file1.txt file2.txt` |
|     | `[ ]` | `ls file[1-3].txt` | `file1.txt file2.txt file3.txt` |
| **Process Substitution** | `<(command)` | `diff <(ls dir1) <(ls dir2)` | Compare two directories |
| **Parameter Expansion (String Manipulation)** | `${VAR%pattern}` | `FILE="backup.tar.gz"; echo ${FILE%.gz}` | `backup.tar` |
|     | `${VAR#pattern}` | `FILE="backup.tar.gz"; echo ${FILE#backup.}` | `tar.gz` |
|     | `${VAR//old/new}` | `TEXT="I like bash"; echo ${TEXT/bash/zsh}` | `I like zsh` |

* * *

## **More Examples for Bash Expansions**

### ✅ **Brace Expansion `{}` (More Uses)**

🔹 **Multiple File Creation:**

```bash
touch {doc1,doc2,doc3}.txt
```

📌 Creates: `doc1.txt doc2.txt doc3.txt`

🔹 **Nested Expansion:**

```bash
echo {A,B}{1,2}
```

📌 Output: `A1 A2 B1 B2`

🔹 **Combining Brace Expansion with Variables:**

```bash
PREFIX="log"
touch ${PREFIX}{1..3}.txt
```

📌 Creates: `log1.txt log2.txt log3.txt`

* * *

### ✅ **Tilde Expansion `~` (More Uses)**

🔹 **Change Directory to Another User's Home**

```bash
cd ~root
```

🔹 **List Files in Another User's Home**

```bash
ls ~user/Documents
```

* * *

### ✅ **Variable Expansion `$VAR` (More Uses)**

🔹 **Using Default Values If Variable Is Empty**

```bash
echo ${USERNAME:-"Guest"}
```

📌 If `$USERNAME` is empty, it prints `"Guest"`.

🔹 **Extracting Substring**

```bash
TEXT="Linux is awesome"
echo ${TEXT:6:2}
```

📌 Output: `is`

🔹 **String Replacement**

```bash
FILE="backup_2024.tar.gz"
echo ${FILE/_2024/}
```

📌 Output: `backup.tar.gz`

* * *

### ✅ **Command Substitution `$(command)` (More Uses)**

🔹 **Get the System Uptime**

```bash
echo "System Uptime: $(uptime -p)"
```

🔹 **Save Command Output to Variable**

```bash
HOSTNAME=$(hostname)
echo "Current Host: $HOSTNAME"
```

* * *

### ✅ **Arithmetic Expansion `$((expression))` (More Uses)**

🔹 **Calculate Disk Space Usage**

```bash
TOTAL=$(( $(df --output=used / | tail -n1) / 1024 ))
echo "Used Space: ${TOTAL}MB"
```

🔹 **Convert Celsius to Fahrenheit**

```bash
CELSIUS=25
FAHRENHEIT=$(( (CELSIUS * 9/5) + 32 ))
echo "$CELSIUS°C = $FAHRENHEIT°F"
```

* * *

### ✅ **Globbing (Wildcard Expansion) (More Uses)**

🔹 **Find All Shell Scripts**

```bash
ls *.sh
```

🔹 **List Only Files Starting with 'log' and Ending in '.txt'**

```bash
ls log*.txt
```

🔹 **Find Files with Numbers**

```bash
ls file[0-9].txt
```

* * *

### ✅ **Process Substitution `<(command)` (More Uses)**

🔹 **Compare File Contents Without Creating Temp Files**

```bash
diff <(cat file1.txt) <(cat file2.txt)
```

🔹 **Sort Two Lists Together**

```bash
sort <(echo -e "banana\napple") <(echo -e "carrot\ndate")
```

* * *

### ✅ **Parameter Expansion (More Uses)**

🔹 **Remove Smallest Prefix Match**

```bash
TEXT="abcdefabcdef"
echo ${TEXT#a*c}
```

📌 Output: `defabcdef`

🔹 **Remove Largest Prefix Match**

```bash
echo ${TEXT##a*c}
```

📌 Output: `def`

🔹 **Remove Smallest Suffix Match**

```bash
echo ${TEXT%c*f}
```

📌 Output: `abcde`

🔹 **Remove Largest Suffix Match**

```bash
echo ${TEXT%%c*f}
```

📌 Output: `ab`

* * *

## **Conclusion**

👉 **Bash Expansions** တွေက **Linux Terminal** မှာ **Automation, String Processing, File Handling** တို့အတွက် အသုံးဝင်တဲ့ Techniques တွေပဲ။  
👉 **Table Cheat Sheet** ကို Note အနေနဲ့ **Print ထုတ်လို့ရနိုင်မယ်။**

* * *


