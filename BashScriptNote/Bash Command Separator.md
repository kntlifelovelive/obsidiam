 `name=$(uname); echo "Hello, $name"` ဆိုတာ Semicolon ထည့်ရေးထားလို့  Command separator နဲ့ ထည့်ရေးတာလို့ ခေါ်ပါတယ်။ 

---

### Command Separator 
- `;` (semicolon) ကို **command separator** လို့ခေါ်တယ်။  
- Command separator (`;`) ကိုသုံးလိုက်ပြီဆိုရင် **တစ်ကြောင်းထဲမှာ command နှစ်ခု (သို့မဟုတ် ပိုများလည်းရ) ကို ခွဲရေးနိုင်တယ်**။  

**Example:**  
```bash
echo "First command"; echo "Second command"
```
📌 Output:
```
First command
Second command
```

---

### မတူညီတဲ့ Command Separator မျိုးစုံ  
**1️⃣ `;` (semicolon) → ချိတ်တွဲသုံးနိုင်ပေမယ့် အားလုံးကို တပြိုင်နက် အလုပ်လုပ်စေတယ်**  
```bash
echo "Hello"; ls
```
*(ls ကို run တဲ့အခါ echo command က အလုပ်ဖြစ်သွားပြီးသားဖြစ်မယ်။)*  

**2️⃣ `&&` (AND) → အရင် command အောင်မြင်မှ နောက် command ကို run**  
```bash
mkdir mydir && cd mydir && touch file.txt
```
*(`mkdir mydir` အောင်မြင်မှ `cd mydir` ပြုလုပ်မယ်။ `cd mydir` အောင်မြင်မှ `touch file.txt` run မယ်။)*  

**3️⃣ `||` (OR) → အရင် command မအောင်မြင်ရင် နောက် command ကို run**  
```bash
cd non_existing_dir || echo "Directory not found!"
```
*(Folder မရှိဘူးဆိုရင် `"Directory not found!"` ကို ပြမယ်။)*  

---

### Conclusion  
- `name=$(uname); echo "Hello, $name"` ဆိုတာ **နှစ်ကြောင်းတစ်ကြောင်းပေါင်းရေးထားတာ**  
- `;` (semicolon) ကိုသုံးပြီး commands တစ်ကြောင်းထဲမှာ ခွဲရေးနိုင်တယ်  
- `&&` / `||` စတာတွေကိုလည်း Command Control အနေနဲ့ အသုံးပြုလို့ရတယ်  

---



Bash မှာ commands တွေကို အပြန်အလှန်ဆက်သွယ်ဖို့အတွက် **command separators** တွေကို အသုံးပြုနိုင်ပါတယ်။ ဒီ separator တွေက command တစ်ခုကို အလုပ်လုပ်ပြီးရင် နောက်ထပ် command တစ်ခုကို အလုပ်လုပ်ဖို့ ညွှန်ကြားပေးပါတယ်။

### 1. **Semicolon (`;`)**
   - **Function**: `;` ကို သုံးတဲ့အခါမှာ ပထမ command အလုပ်လုပ်ပြီးသွားရင် နောက်ထပ် command ကို အလုပ်လုပ်ဖို့ ညွှန်ကြားပေးပါတယ်။ ပထမ command အလုပ်မအောင်မြင်ဘူးဆိုရင်တောင် နောက်ထပ် command ကို ဆက်လက်လုပ်ဆောင်ပါမယ်။
   - **Example**:
     ```bash
     echo "Hello"; echo "World"
     ```
     **Output**:
     ```
     Hello
     World
     ```

   ဒီမှာ `echo "Hello"` ကို အရင်လုပ်ပြီးတော့ `echo "World"` ကို နောက်ပြီးလုပ်ပါမယ်။

---

### 2. **AND Operator (`&&`)**
   - **Function**: `&&` ကို သုံးတဲ့အခါမှာ ပထမ command အလုပ်အောင်မြင်ရင်သာ နောက်ထပ် command ကို အလုပ်လုပ်ဖို့ ညွှန်ကြားပေးပါတယ်။ ပထမ command အလုပ်မအောင်မြင်ရင် နောက်ထပ် command ကို မလုပ်ပါဘူး။
   - **Example**:
     ```bash
     mkdir mydir && cd mydir
     ```
     **Explanation**:
     - ပထမ `mkdir mydir` က directory တစ်ခုဖန်တီးပါမယ်။ အဲ့ဒီ command အလုပ်အောင်မြင်ရင် `cd mydir` ကို အလုပ်လုပ်ပါမယ်။
     - အကယ်၍ `mkdir mydir` က error တစ်ခုခုဖြစ်ခဲ့ရင် (ဥပမာ ရှိပြီးသား directory ဖြစ်နေတယ်ဆိုရင်) `cd mydir` ကို မလုပ်ပါဘူး။

---

### 3. **OR Operator (`||`)**
   - **Function**: `||` ကို သုံးတဲ့အခါမှာ ပထမ command အလုပ်မအောင်မြင်ခဲ့ရင်သာ နောက်ထပ် command ကို အလုပ်လုပ်ဖို့ ညွှန်ကြားပေးပါတယ်။ ပထမ command အလုပ်အောင်မြင်ခဲ့ရင် နောက်ထပ် command ကို မလုပ်ပါဘူး။
   - **Example**:
     ```bash
     rm myfile || echo "File not found"
     ```
     **Explanation**:
     - ပထမ `rm myfile` က file တစ်ခုကို ဖျက်ဖို့ ကြိုးစားပါမယ်။ အဲ့ဒီ command အလုပ်မအောင်မြင်ခဲ့ရင် (file မရှိဘူးဆိုရင်) `echo "File not found"` ကို အလုပ်လုပ်ပါမယ်။
     - အကယ်၍ `rm myfile` က အလုပ်အောင်မြင်ခဲ့ရင် `echo "File not found"` ကို မလုပ်ပါဘူး။

---

### 4. **Ampersand (`&`)**
   - **Function**: `&` ကို သုံးတဲ့အခါမှာ ပထမ command ကို background မှာ အလုပ်လုပ်ဖို့ ညွှန်ကြားပေးပါတယ်။ ပထမ command ကို background မှာ အလုပ်လုပ်စေပြီးတော့ နောက်ထပ် command ကို အလုပ်လုပ်ဖို့ ဆက်လက်ပေးပါတယ်။
   - **Example**:
     ```bash
     sleep 5 & echo "Sleeping in background"
     ```
     **Explanation**:
     - `sleep 5` ကို background မှာ အလုပ်လုပ်စေပြီးတော့ `echo "Sleeping in background"` ကို အလုပ်လုပ်ပါမယ်။
     - `sleep 5` က 5 စက္ကန့် စောင့်မှာဖြစ်ပေမယ့် ဒီ command က background မှာ အလုပ်လုပ်နေတဲ့အတွက် `echo` command ကို စောင့်စရာမလိုဘဲ အလုပ်လုပ်ပါမယ်။

---

### 5. **Pipe (`|`)**
   - **Function**: `|` ကို သုံးတဲ့အခါမှာ ပထမ command ရဲ့ output ကို နောက်ထပ် command ရဲ့ input အဖြစ် ပေးပါတယ်။
   - **Example**:
     ```bash
     ls -l | grep "txt"
     ```
     **Explanation**:
     - `ls -l` က directory ထဲက file တွေကို list ထုတ်ပေးပါမယ်။ အဲ့ဒီ output ကို `grep "txt"` ကို ပေးပြီး `.txt` ဖြစ်တဲ့ file တွေကို filter လုပ်ပါမယ်။

---

### 6. **Command Grouping (`()`, `{}`)**
   - **Function**: Command တွေကို group လုပ်ဖို့အတွက် parentheses `()` နဲ့ braces `{}` ကို သုံးနိုင်ပါတယ်။
     - `()` က subshell ထဲမှာ command တွေကို အလုပ်လုပ်ဖို့ အသုံးပြုပါတယ်။
     - `{}` က current shell ထဲမှာ command တွေကို အလုပ်လုပ်ဖို့ အသုံးပြုပါတယ်။
   - **Example**:
     ```bash
     (echo "This is a subshell") && echo "Back to main shell"
     ```
     **Explanation**:
     - `echo "This is a subshell"` က subshell ထဲမှာ အလုပ်လုပ်ပါမယ်။ အဲ့ဒီ command အလုပ်လုပ်ပြီးသွားရင် `echo "Back to main shell"` ကို main shell မှာ အလုပ်လုပ်ပါမယ်။

---

### 7. **Newline (`\n`)**
   - **Function**: Newline character (`\n`) က command တစ်ခုကို အဆုံးသတ်ပြီး နောက်ထပ် command ကို စတင်ဖို့ အသုံးပြုပါတယ်။ ဒါက အများဆုံးသုံးတဲ့ command separator ဖြစ်ပါတယ်။
   - **Example**:
     ```bash
     echo "Hello"
     echo "World"
     ```
     **Output**:
     ```
     Hello
     World
     ```

---

### 8. **Backslash (`\`)**
   - **Function**: `\` ကို သုံးတဲ့အခါမှာ command တစ်ခုကို multi-line ဖြစ်အောင် ခွဲခြားဖို့ အသုံးပြုပါတယ်။
   - **Example**:
     ```bash
     echo "This is a very long command" \
          "that spans multiple lines"
     ```
     **Output**:
     ```
     This is a very long command that spans multiple lines
     ```

---

### Summary Table:

| Separator | Function                                                    | Example                                            |                                                 |             |     |                        |
| --------- | ----------------------------------------------------------- | -------------------------------------------------- | ----------------------------------------------- | ----------- | --- | ---------------------- |
| `;`       | Commands run sequentially, regardless of success or failure | `echo "Hello"; echo "World"`                       |                                                 |             |     |                        |
| `&&`      | Run next command only if the previous one succeeds          | `mkdir mydir && cd mydir`                          |                                                 |             |     |                        |
| `         |                                                             | `                                                  | Run next command only if the previous one fails | `rm myfile  |     | echo "File not found"` |
| `&`       | Run command in the background                               | `sleep 5 & echo "Sleeping in background"`          |                                                 |             |     |                        |
| `         | `                                                           | Pipe the output of one command as input to another | `ls -l                                          | grep "txt"` |     |                        |
| `()`      | Run commands in a subshell                                  | `(echo "Subshell") && echo "Main shell"`           |                                                 |             |     |                        |
| `{}`      | Run commands in the current shell                           | `{ echo "Current shell"; }`                        |                                                 |             |     |                        |
| `\n`      | Separate commands by newlines                               | `echo "Hello"\necho "World"`                       |                                                 |             |     |                        |
| `\`       | Continue a command on the next line                         | `echo "Hello" \`<br>`"World"`                      |                                                 |             |     |                        |

---
