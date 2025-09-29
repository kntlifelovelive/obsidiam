
## **Linux Terminal Hotkeys** (မြန်မာလိုရှင်းပြချက်ပါ)

---

### **1. Bash Navigation (နာဗီဂိတ်ရှင်းပြချက်)**

#### **Ctrl + A** - Command line ရဲ့ အစကို ရောက်သွားရန်

**ဥပမာ:**

```bash
echo "Hello World!"
```

`Ctrl + A` ကို နှိပ်လိုက်တာနဲ့ Cursor က command line ရဲ့ အစကို ရောက်သွားပါလိမ့်မယ်။

---

#### **Ctrl + E** - Command line ရဲ့ အဆုံးကို ရောက်သွားရန်

**ဥပမာ:**

```bash
echo "Hello World!"
```

Cursor ကို command line ရဲ့ အဆုံးသို့ ရောက်သွားစေပါတယ်။

---

#### **Ctrl + F** - အရှေ့ Characters တစ်လုံးချင်းစီသို့ ရွှေ့ရန်

Cursor ကို အရှေ့ Characters တစ်လုံးစီသို့ ရွှေ့သွားစေပါတယ်။

---

#### **Ctrl + B** - အနောက် Characters တစ်လုံးချင်းစီသို့ ပြန်ရွှေ့ရန်

Cursor ကို အနောက် Characters တစ်လုံးစီသို့ ပြန်ရွှေ့ပါသည်။

---

#### **Ctrl + XX** - Cursor ရဲ့ တည်နေရာကို အစနှင့် လက်ရှိအနေအထားအကြား အပြောင်းအလဲပြုလုပ်ရန်

Command line ရဲ့ အစနှင့် လက်ရှိ Cursor တည်နေရာအကြား ပြောင်းလဲနိုင်ပါတယ်။

---

#### **Alt + F / Esc + F** - Word တစ်လုံးစီ အရှေ့သို့ ရွှေ့ရန်

**ဥပမာ:**

```bash
echo "Learning Linux terminal"
```

`Alt + F` ကို နှိပ်လိုက်ရင် Cursor က စကားလုံး (Word) တစ်လုံးအရှေ့သို့ ရွှေ့သွားပါလိမ့်မယ်။

---

#### **Alt + B / Esc + B** - Word တစ်လုံးစီ အနောက်သို့ ပြန်ရွှေ့ရန်

Cursor ကို စကားလုံး တစ်လုံးခြင်းပြန်ရွှေ့နိုင်ပါတယ်။

---

### **2. Bash Control/Process (Command ထိန်းချုပ်မှု)**

#### **Ctrl + L** - Screen ကို ဖြတ်ပစ်ရန်

**clear** command နှင့် အတူတူ ဖြစ်ပါတယ်။

```bash
clear
```

---

#### **Ctrl + S** - Output ကို ရပ်တန့်ထားရန်

**ဥပမာ:**

```bash
ping google.com
```

`Ctrl + S` ကို နှိပ်လိုက်ရင် Output ရပ်တန့်သွားပါတယ်။  
ပြန်စသွားရန် - `Ctrl + Q` ကို နှိပ်ပါ။

---

#### **Ctrl + Z** - Command ကို နောက်ခံ (background) ကို ရွှေ့ရန်

**ဥပမာ:**

```bash
ping google.com
```

`Ctrl + Z` ကို နှိပ်လိုက်ရင် Command ကို နောက်ခံသို့ ရွှေ့ပါမယ်။  
**Command ပြန်စရန်:**

```bash
fg %1
```

---

#### **Ctrl + C** - Command ကို ရပ်တန့်စေသည် (Terminate)

Command ကို သတ်မှတ်ချက်မဲ့ ပြီးဆုံးစေပါသည်။

---

#### **Ctrl + D** - Terminal ကို ပိတ်ရန်

လက်ရှိ Terminal session ကို ပိတ်ပါသည်။

---

### **3. Bash History (လွန်ခဲ့သော Commands များ)**

#### **Ctrl + R** - Command History ထဲက ပြန်ရှာရန်

Command တွေကို တစ်ချက်ချင်းပြန်ရှာနိုင်ပါတယ်။  
**ဥပမာ:**

```bash
(reverse-i-search)`ping': ping google.com
```

---

#### **Ctrl + P** - လွန်ခဲ့သော Command ကို ပြန်သွားရန်

**Ctrl + N** - နောက်တစ်ခု Command ကို ရွှေ့ရန်  
**!!** - နောက်ဆုံး Command ကို ထပ်စရန်  
**ဥပမာ:**

```bash
echo "Hello"
```

နောက်တစ်ခါ `!!` ရိုက်လိုက်ရင် `echo "Hello"` ပြန်ပြေးပါမယ်။

---

### **4. Bash Editing (Command တည်းဖြတ်ခြင်း)**

#### **Ctrl + U** - Cursor အစမှ Command အထိ ဖြတ်ပစ်ရန်

**ဥပမာ:**

```bash
echo "Hello World!"
```

`Ctrl + U` ကို နှိပ်လိုက်တာနဲ့ Command line အစအထိ ဖြတ်ပစ်ပါလိမ့်မယ်။

---

#### **Ctrl + K** - Cursor မှ နောက်ဆုံးထိ ဖြတ်ပစ်ရန်

Cursor ရဲ့ လက်ရှိနေရာမှ အဆုံးထိ ဖြတ်ပစ်ပါသည်။

---

#### **Ctrl + W** - Cursor မတိုင်မီ စကားလုံး (Word) တစ်လုံး ဖြတ်ပစ်ရန်

Cursor ရှေ့က စကားလုံး တစ်လုံးကို ဖြတ်ပစ်ပါသည်။

---

#### **Alt + D** - Cursor အနောက်မှ စကားလုံး တစ်လုံး ဖြတ်ပစ်ရန်

Cursor ရှေ့က စကားလုံး တစ်လုံးကို ဖြတ်ပစ်ပါသည်။

---

### **5. Bash Information (အချက်အလက် နှင့် အကူအညီ)**

#### **TAB** - Command အား Auto-complete ပြုလုပ်ရန်

**ဥပမာ:**

```bash
cd Doc
```

TAB ကို နှိပ်လိုက်ရင် - `cd Documents/` အဖြစ် ပြောင်းလဲပါမယ်။

---

#### **Alt + ?** - လက်ရှိလမ်းကြောင်းထဲရှိ ဖိုင်များ ပြရန်

Linux User အားလုံးကို ပြပါမယ်။

#### **Alt + .** - ယခင် Command ရဲ့ နောက်ဆုံး Argument ကို အသုံးပြုရန်

**ဥပမာ:**

```bash
mkdir newdir
```

နောက်တစ်ခါ:

```bash
cd Alt + .
```

ရလာမည့်အဖြစ်:

```bash
cd newdir
```

---

### **Pro Tips**

1. **Ctrl + R** နှင့် **Ctrl + O** ကို ပေါင်းစပ်ပြီး Command ရှာပြီး ချက်ချင်း အသုံးပြုနိုင်ပါတယ်။
2. **Ctrl + A** နှင့် **Ctrl + K** ကို တွဲသုံးပြီး Command ကို မြန်မြန်ပြန်ရိုက်နိုင်ပါတယ်။

---


**Linux Terminal Hotkeys** (with detailed examples)

### **1. Bash Navigation**

#### **Ctrl + A** - Move to the start of the command line

**Example:**

```
echo "Hello World!"
```

Press `Ctrl + A`, and the cursor will move to the beginning of the line.

#### **Ctrl + E** - Move to the end of the command line

Press `Ctrl + E`, and the cursor will move to the end of the line.

#### **Ctrl + F** - Move one character forward

Moves the cursor one character forward without deleting.

#### **Ctrl + B** - Move one character backward

Moves the cursor one character backward without deleting.

#### **Ctrl + XX** - Switch cursor position between start and current position

Quickly swap between the beginning of the line and the current cursor position.

#### **Alt + F / Esc + F** - Move one word forward

```
echo "Learning Linux terminal"
```

Press `Alt + F`, and the cursor will move word by word.

#### **Alt + B / Esc + B** - Move one word backward

Moves the cursor one word backward.

---

### **2. Bash Control/Process**

#### **Ctrl + L** - Clear the screen

Works like the `clear` command.

#### **Ctrl + S** - Stops the terminal output

For example:

```
ping google.com
```

Press `Ctrl + S` to pause the output. Press `Ctrl + Q` to resume.

#### **Ctrl + Z** - Suspend the current command

For example:

```
ping google.com
```

Press `Ctrl + Z`, and it will suspend the process. You can see it in the background using:

```
jobs
```

Resume the job using:

```
fg %1
```

#### **Ctrl + C** - Terminate the current command

Interrupts a running command, like stopping a ping.

#### **Ctrl + D** - Close the terminal

Ends the terminal session.

---

### **3. Bash History**

#### **Ctrl + R** - Reverse search through command history

Start typing, and it will auto-complete previous commands.

```
(reverse-i-search)`ping': ping google.com
```

#### **Ctrl + P** - Move to the previous command

#### **Ctrl + N** - Move to the next command

Same as using the up and down arrows.

#### **!!** - Repeat the last command

If your previous command was:

```
echo "Hello"
```

Typing `!!` will run it again.

#### **!x** - Run the last command starting with 'x'

```
!ec
```

It will find and run the last command that started with `ec`, like `echo "Hello"`.

---

### **4. Bash Editing**

#### **Ctrl + U** - Delete from the cursor to the beginning of the line

If you typed:

```
echo "Hello World!"
```

Pressing `Ctrl + U` will clear the whole line.

#### **Ctrl + K** - Delete from the cursor to the end of the line

If your cursor is in the middle, it will delete from the cursor to the end.

#### **Ctrl + W** - Delete the word before the cursor

```
echo "Hello World!"
```

If the cursor is after "World!", pressing `Ctrl + W` will remove "World!".

#### **Alt + D** - Delete the word after the cursor

If your cursor is before "World!", pressing `Alt + D` will delete "World!".

---

### **5. Bash Information**

#### **TAB** - Autocomplete commands and paths

For example:

```
cd Doc
```

Press `TAB`, and it will auto-complete to `cd Documents/` if it exists.

#### **Alt + ?** - Display files/folders in the current path

Displays a list of all available files and directories.

#### **Alt + .** - Reuse the last argument of the previous command

If you typed:

```
mkdir newdir
```

Then use:

```
cd Alt + .
```

It will expand to:

```
cd newdir
```

---

### **6. Bash Shortcuts Summary**

|Shortcut|Action|
|---|---|
|Ctrl + A|Move to the start of the command line|
|Ctrl + E|Move to the end of the command line|
|Ctrl + C|Terminate current command|
|Ctrl + Z|Suspend current command|
|Ctrl + L|Clear terminal screen|
|Ctrl + R|Reverse search through history|
|Alt + F|Move one word forward|
|Alt + B|Move one word backward|
|Ctrl + W|Delete the word before the cursor|
|Ctrl + K|Delete from the cursor to the end of the line|

#### **Pro Tip:**

You can combine shortcuts for more efficiency. For example:

- Use `Ctrl + R` to find a command and then press `Ctrl + O` to execute it directly.
- Combine `Ctrl + A`, `Ctrl + K`, and `Ctrl + Y` to quickly move to the start, cut, and paste a command.

---


