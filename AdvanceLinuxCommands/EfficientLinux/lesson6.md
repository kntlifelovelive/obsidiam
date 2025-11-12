
---

## Lesson 6 – Redirection & Pipelines

_(Page 51–70, Efficient Linux at the Command Line)_

---

## 1 Input & Output Streams (Fundamentals)

Linux မှာ process တစ်ခုရဲ့ I/O (Input/Output) ကို ၃ မျိုးသတ်မှတ်ထားတယ်။

|Stream|Name|Description|
|---|---|---|
|`stdin`|Standard Input|Keyboard / Input source|
|`stdout`|Standard Output|Normal output to screen|
|`stderr`|Standard Error|Error messages output|

**Diagram (Concept):**

```
Keyboard → [ stdin → Command → stdout → Screen ]
                               ↳ stderr → Screen
```



## 2 Output Redirection (`>` , `>>`)

=> Command ရဲ့ output ကို file ထဲ redirect လုပ်နိုင်တယ်။

### `>` → overwrite existing file

```bash
echo "Hello Kyaw" > message.txt
```

➡ file မရှိရင် ဖန်တီးမယ်, ရှိရင် overwrite လုပ်မယ်။

### `>>` → append (ပေါင်းထည့်)

```bash
echo "Love Linux" >> message.txt
```

➡ file ရှိရင် အဆုံးမှာ ထပ်ရေးမယ်။

**Example:**

```bash
date > log.txt
ls >> log.txt
```

 Diagram:

```
[Command Output] →> log.txt
```

---

## 3 Input Redirection (`<`)

=> File ထဲက content ကို command input အနေနဲ့ အသုံးပြုမယ်။

**Example:**

```bash
sort < names.txt
```

➡ `names.txt` file ထဲက data ကို input အနေနဲ့ sort လုပ်တယ်။

**Another Example:**

```bash
wc -l < file.txt
```

➡ file ထဲက line count ကို တွက်မယ်။

---

## 3 Redirect Errors (`2>`, `2>>`)

-  Error messages ကိုပဲ separate file ထဲ redirect လုပ်ချင်တဲ့အခါ။

**Example:**

```bash
ls /root 2> errors.log
```

➡ Permission denied error ကို `errors.log` ထဲသိမ်းမယ်။

**Append mode:**

```bash
ls /notexist 2>> errors.log
```

**Both stdout & stderr together:**

```bash
command > all.log 2>&1
```

 Diagram:

```
stdout → all.log
stderr ↗ same file
```


## 5 Pipelines (`|`)

Commands တွေကို ချိတ်ပြီး _တcommand output ကို နောက် command input_ အနေနဲ့ပေးနိုင်တယ်။  
ဒါက Linux efficiency ရဲ့ အဓိက feature ဖြစ်တယ် 

**Basic Syntax:**

```bash
command1 | command2
```

 Diagram:

```
[Command1 output] → [Command2 input]
```


### Examples

**Example 1 – Filter list:**

```bash
ls -l | grep ".sh"
```

➡ `.sh` file တွေကိုပဲ ပြမယ်။

**Example 2 – Count number of lines:**

```bash
cat /etc/passwd | wc -l
```

➡ `/etc/passwd` file ထဲရှိ line အရေအတွက် ပြမယ်။

**Example 3 – Combine 3 commands:**

```bash
ps aux | grep bash | wc -l
```

➡ bash process ဘယ်နှစ်ခုရှိသလဲ တွက်မယ်။


## 6  Mixed Redirection + Pipeline

- stdout, stderr, stdin တွေကိုတစ်ပြိုင်တည်း manage လုပ်လို့ရတယ်။

**Example:**

```bash
find /etc -name "*.conf" 2> /dev/null | grep network
```

➡ Error တွေ (/etc permission denied) ကို ဖယ်ပြီး  
`network` ပါတဲ့ `.conf` files တွေကိုပဲပြမယ်။



## 7  `/dev/null` (the black hole)

**output / error မဖြစ်စေချင်တဲ့အခါ ဖျက်လိုက်တဲ့ file**  Linux ရဲ့ “trash can” လို့ပြောလို့ရတယ်။

**Examples:**

```bash
command > /dev/null        # output မပြ
command 2> /dev/null       # error မပြ
command &> /dev/null       # output + error နှစ်မျိုးလုံး မပြ
```



##  Lesson 6 – Summary Table

|Symbol|Description|Example|
|---|---|---|
|`>`|stdout → file (overwrite)|`ls > out.txt`|
|`>>`|stdout → file (append)|`echo hi >> file.txt`|
|`<`|file → stdin|`sort < names.txt`|
|`2>`|stderr → file|`ls /root 2> err.log`|
|`|`|stdout → stdin (pipe)|
|`&>`|stdout + stderr → file|`cmd &> output.txt`|
|`/dev/null`|discard output|`ls > /dev/null`|



## Homework (Practice Tasks)

1. `ls /root > output.txt 2> error.txt`  
   normal result & errors ကို separate files ထဲ save လုပ်ပါ။
2. `cat /etc/passwd | grep bash | wc -l`  
   → bash shell သုံးသူဘယ်နှစ်ယောက်ရှိသလဲ တွက်ပါ။

3. `find / -name "*.conf" 2> /dev/null | wc -l`  
   → system ထဲက `.conf` files များအရေအတွက် ကိုတွက်ပါ။

4. `echo "Kyaw loves Linux" > love.txt`  
   → ပြီးနောက် `"loves"` ကို `grep` နဲ့ filter လုပ်ပါ။

5. Bonus  – `dmesg | grep error | tee errors.log`  
   → system error logs ကို screen နဲ့ file နှစ်ဖက်လုံးသိမ်းပါ။




 **Pro Tip (diagram)**

```
cat file.txt ─┬─> grep "error" ─┬─> sort ─┬─> wc -l
               │                 │          │
           stdin              stdout     stdout
```

➡ data flow လုပ်ပုံကို ဒီလိုမြင်လို့ရတယ်။

---
