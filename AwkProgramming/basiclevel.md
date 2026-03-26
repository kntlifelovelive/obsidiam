
---

# 1 `awk '{print}' user.txt`

ဒီ command structure ကို အရင်ကြည့်ရအောင်။

```bash
awk 'PROGRAM' file
```

Example

```bash
awk '{print}' user.txt
```

|Part|Name|Meaning|
|---|---|---|
|awk|command|AWK interpreter|
|`' '`|program quotes|awk program|
|`{print}`|action block|line ကို print|
|user.txt|input file|awk process file|

---

# 2 `{}` braces ဆိုတာဘာလဲ

- => **AWK** မှာ ` { action } or { print }` ကို **Action Block** လို့ခေါ်တယ်။ 

```awk
{ action }  or { print }
```

ဒါက `{print}` ဆိုရင် `line` တစ်ကြောင်းဖတ်တိုင်း `print Output` ထုတ်ပေးတယ်ဆိုတဲ့ `meaning` ဖြစ်ပါတယ်။  

- --> ဒီ `Brace -> {}` က **bash brace expansion မဟုတ်ပါဘူး** 
- `Bash brace expansion ` ကတော့ ဒီလို `{1..5}`  ရေးပါတယ်။ 

```bash
echo {1..5}
```

- *Bash Brace Expansion* မှာ `echo {1..5}` ဆိုရင် `Output` ကတော့ `1 2 3 4 5`  ဖြစ်ပါတယ် ။ 

```
1 2 3 4 5
```

- ==> အဲ့ဒါကို `{1..5}` **shell feature**  လို့လည်း ခေါ်ပါတယ်။

**AWK**  မှာ   `Curly brace {}`  တွန့် ကွင်းကို  `action block` လို့ခေါ်ပါတယ်။ `Action block` ဖြစ်တယ်။



---

# 3 `$1 $2` ဆိုတာဘာလဲ

**AWK** မှာ `$1` ကို `Field variable` လို့ခေါ်ပါတယ် ။ 

- Example

```bash
awk '{print $1}' users.txt
```


```
{ print $1 } > Field variable
```

Meaning 

```
column 1  
```

ဒီ `Field varrable` ဟာ `column` အဖြစ်နဲ့ `Output` ထုတ်ပေးပါတယ်။ 

- Example file

```
kyaw 21 yangon
aung 30 mandalay
```

AWK က line ကို

```
kyaw   21   yangon
$1     $2   $3
```

လို split လုပ်တယ်။

---

# 4 Important AWK built-in variables

AWK မှာ built-in variables အများကြီးရှိတယ်။

|Variable|Meaning|
|---|---|
|`$0`|whole line|
|`$1`|column 1|
|`$2`|column 2|
|`$NF`|last column|
|`NR`|line number|
|`NF`|field count|

Example

```bash
awk '{print NR,$0}' users.txt
```

Output

```
1 kyaw 21 yangon
2 aung 30 mandalay
```

---

# 5 `$0` ဆိုတာ

Example

```bash
awk '{print $0}' users.txt
```

Meaning

```
whole line
```

---

# 6 `$NF` ဆိုတာ

Example

```bash
awk '{print $NF}' users.txt
```

Meaning

```
last column
```

Example

```
kyaw 21 yangon
```

Result

```
yangon
```

---

# 7 `NR` variable

Example

```bash
awk '{print NR,$1}' users.txt
```

Output

```
1 kyaw
2 aung
```

Meaning

```
NR = line number
```

---

# 8 `NF` variable

Example

```bash
awk '{print NF}' users.txt
```

Output

```
3
3
```

Meaning

```
fields count
```

---

# 9 Pattern + Action structure

AWK syntax

```
pattern { action }
```

Example

```bash
awk '$2>25 {print $1}'
```

Meaning

```
column2 > 25 ဖြစ်ရင် name print
```

---

# 10 AWK execution flow

AWK internally ဒီလို run တယ်

```
read line
↓
split fields
↓
check pattern
↓
run action
↓
next line
```

---

# 11  Field separator (FS)

default separator

```
space
```

Example

```
kyaw 21 yangon
```

split

```
$1 kyaw
$2 21
$3 yangon
```

CSV example

```bash
awk -F, '{print $1}'
```

---

# 12 Quick visualization

line

```
kyaw 21 yangon
```

AWK internal view

```
$0 = kyaw 21 yangon
$1 = kyaw
$2 = 21
$3 = yangon
NF = 3
```

---

# 13 Full example

```bash
awk '{print NR,$1,$NF}' users.txt
```

Output

```
1 kyaw yangon
2 aung mandalay
```

Meaning

```
line number
first column
last column
```

---

#  AWK terminology summary

|Syntax|Name|Meaning|
|---|---|---|
|`{}`|action block|commands|
|`$1`|field variable|column 1|
|`$0`|record variable|whole line|
|`NR`|built-in variable|line number|
|`NF`|built-in variable|field count|
|`FS`|field separator|column split|
|`pattern`|condition|filter|

---

 **important concept**

AWK data model

```
file
 ↓
record (line)
 ↓
fields (columns)
```

---

💬 ကိုရေ  
မင်း AWK ကို **deep level** နားလည်ချင်ရင် နောက် step က

1️⃣ **AWK internal variables (20 important variables)**  
2️⃣ **AWK record vs field system deep explanation**  
3️⃣ **AWK pattern matching engine**  
4️⃣ **AWK arrays (most powerful feature)**

ဒီ 4 ခုကို သိရင် **awk ကို 80% mastery** ရသွားတယ်။

လိုချင်ရင် ငါ **AWK internal architecture (awk engine ဘယ်လို run တယ်)** ကို diagram နဲ့ရှင်းပြပေးမယ်။ 😎