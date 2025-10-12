
---


###  Lesson 5 – Text Processing Tools (Part 1)

#### 1 `cut` – Column & Field Extractor

==> Text file ထဲက column/field အတိအကျထုတ်ဖို့ သုံးတယ်  
CSV / log file / passwd file တို့ကို split ထုတ်ဖို့ အလွန်အဆင်ပြေတယ်

**Syntax:**

```bash
cut OPTION... [FILE]...
```

**Main Options:**

- `-f` → field number(s) (column number)
- `-d` → delimiter (separating character)
- `-c` → character position(s)


**Example 1 – Field by delimiter:**  
`/etc/passwd` file ထဲက colon-separated fields:

```bash
cut -d: -f1 /etc/passwd
```

➡ username field (field1) အကုန်ထုတ်မယ်

```bash
cut -d: -f1,3 /etc/passwd
```

➡ username (field1) နဲ့ UID (field3) ထုတ်မယ်


**Example 2 – Character positions:**

```bash
echo "KyawLinux" | cut -c1-4
```

➡ Output: `Kyaw` (character 1 to 4)


 **Diagram** (concept):

```
username:x:1000:1000:comment:/home/user:/bin/bash
| f1  |f2| f3 | f4 | ... | f7 |
```

`cut -d: -f1` → username  
`cut -d: -f7` → shell


**Homework**

1. `/etc/passwd` ထဲက username & home directory (field1 & field6) ကို cut နဲ့ထုတ်ပါ
2. `"LinuxIsGreat"` string ထဲက character 6 to 10 ကို cut -c နဲ့ထုတ်ပါ


### 2 `tr` – Translate / Delete Characters

==> String ထဲက character တွေကို translate (replace) / delete / squeeze လုပ်တယ်  
plain text stream များအတွက် အဆင်ပြေတယ်

**Syntax:**

```bash
tr [OPTION] SET1 [SET2]
```

**Main Functions:**

- Character replace
- Uppercase ↔ lowercase conversion
- Delete specific characters
- Squeeze repeated characters


**Example 1 – Lowercase to Uppercase:**

```bash
echo "hello world" | tr '[:lower:]' '[:upper:]'
```

➡ Output: `HELLO WORLD`


**Example 2 – Delete specific characters:**

```bash
echo "Kyaw123" | tr -d '0-9'
```

➡ Output: `Kyaw` (digits deleted)


**Example 3 – Replace characters:**

```bash
echo "apple" | tr 'ae' 'AE'
```

➡ Output: `ApplE`

---

**Example 4 – Squeeze repeated spaces:**

```bash
echo "Kyaw    loves    Linux" | tr -s ' '
```

➡ Output: `Kyaw loves Linux`


 **Diagram** (concept):

```
Input:  a a a b b   c
tr -s ' '
Output: a a a b b c (spaces squeezed)
```


**Homework**

1. `"HELLO WORLD"` string ကို tr သုံးပြီး small letter ပြောင်းပါ
2. `"Kya w Lin ux"` string ထဲက space တွေကို squeeze လုပ်ပါ
3. `"abc123xyz"` string ထဲက digits တွေကို delete လုပ်ပါ


### Lesson 5 Part 1 Summary

|Command|Function|Example|
|---|---|---|
|`cut -d: -f1 file`|delimiter-separated field extract|usernames|
|`cut -c1-5 file`|character positions extract|first 5 chars|
|`tr 'a-z' 'A-Z'`|convert lowercase → uppercase|HELLO|
|`tr -d '0-9'`|delete digits|abcxyz|
|`tr -s ' '`|squeeze spaces|single space|

---

## 🔹 `cut` Command — Full Explanation
 
==> `cut` က **line-based text** ကို “အပိုင်းခွဲပြီး”  
character position (`-c`)  
သို့မဟုတ် field delimiter (`-d` & `-f`) နဲ့ လိုအပ်တာပဲ select လုပ်ပေးတဲ့ tool ဖြစ်တယ်။
==> usage က CSV file, `/etc/passwd`, log files, tabular data တို့မှာ ပါတယ်။

---

###  Basic Syntax

```bash
cut OPTION... [FILE]...
```

|Option|Meaning|
|---|---|
|`-f`|Field number(s) to extract|
|`-d`|Field delimiter (default = TAB)|
|`-c`|Character positions|
|`--complement`|Select all except those fields|
|`--output-delimiter`|Custom output separator|


###  Example 1 – Field Extraction by Delimiter

==> **Sample file: `users.txt`**

```
kyaw:x:1000:1000:Kyaw Linux:/home/kyaw:/bin/bash
may:x:1001:1001:May Aye:/home/may:/bin/zsh
aung:x:1002:1002:Aung Win:/home/aung:/bin/bash
```

==> Field delimiter = `:`

**Example:**

```bash
cut -d: -f1 users.txt
```

➡ Output:

```
kyaw
may
aung
```

➡ (field1 = username)

**Extract Multiple Fields**

```bash
cut -d: -f1,6 users.txt
```

➡ Output:

```
kyaw:/home/kyaw
may:/home/may
aung:/home/aung
```

➡ username နဲ့ home directory တစ်ခုပြတယ်။

**Use Different Output Delimiter**

```bash
cut -d: -f1,7 --output-delimiter=" → " users.txt
```

➡ Output:

```
kyaw → /bin/bash
may → /bin/zsh
aung → /bin/bash
```


 **Diagram (concept):**

```
| username | x | UID | GID | fullname | home | shell |
 kyaw         :   x   :1000:1000:Kyaw Linux:/home/kyaw:/bin/bash
       ↑                              ↑
     -f1                            -f7
```


###  Example 2 – Extract Characters

**Example:**

```bash
echo "KyawLinux" | cut -c1-4
```

➡ Output: `Kyaw`

**Range Usage:**

```bash
echo "123456789" | cut -c3-7
```

➡ Output: `34567`

**Separate characters:**

```bash
echo "abcdefghij" | cut -c2,4,6,8
```

➡ Output: `bdfh`


###  Example 3 – Skip & Keep Selected Fields

**Example File:**

```
name,age,city,gender
Kyaw,25,Yangon,Male
May,21,Mandalay,Female
```

```bash
cut -d, -f2,3 people.csv
```

➡ Output:

```
age,city
25,Yangon
21,Mandalay
```

**Inverse (Skip Fields):**

```bash
cut -d, --complement -f2 people.csv
```

➡ Output:

```
name,city,gender
Kyaw,Yangon,Male
May,Mandalay,Female
```


###  Example 4 – Combine with Other Commands (Pipeline)

**Example 1 – Get current users’ shells**

```bash
cat /etc/passwd | cut -d: -f1,7
```

**Example 2 – Show only unique shells**

```bash
cat /etc/passwd | cut -d: -f7 | sort | uniq
```

➡ Output:

```
/bin/bash
/bin/zsh
/bin/false
```

**Example 3 – Get IP from ifconfig**

```bash
ifconfig eth0 | grep 'inet ' | cut -d' ' -f10
```

➡ Output: your IP address  
(_works depending on spacing in output_)

---

###  Example 5 – Extract Specific Range from File

**Example File (`text.txt`):**

```
Line1: Kyaw
Line2: May
Line3: Aung
Line4: Su
```

```bash
cut -c7- text.txt
```

➡ Output:

```
Kyaw
May
Aung
Su
```

(`-c7-` means from character 7 to end)

---

###  Example 6 – Using `cut` with `awk` or `grep`

```bash
grep bash /etc/passwd | cut -d: -f1
```

➡ bash shell သုံးသူများနဲ့ username ကိုပဲပြမယ်။

```bash
awk -F: '{print $1,$7}' /etc/passwd
```

➡ `awk` သုံးတာနဲ့တောင်တူရိုးရိုးပဲ — `cut` နဲ့တူတယ်။

---

###  Summary Table

|Option|Description|Example|
|---|---|---|
|`-d`|Specify delimiter|`-d:`|
|`-f`|Choose field(s)|`-f1,3`|
|`-c`|Character range|`-c1-5`|
|`--complement`|Exclude specified fields|`--complement -f2`|
|`--output-delimiter`|Change output separator|`--output-delimiter=" → "`|

---

### Homework (Challenge Mode)

1. `/etc/passwd` ထဲက username + UID + shell ကို colon-separated နဲ့ cut လုပ်ပါ။
2. CSV file (`name,age,city`) တစ်ခုဖန်တီးပြီး name + city ကိုသာထုတ်ပါ။
3. `cut -c` သုံးပြီး string `"HELLOLINUXWORLD"` ထဲက `"LINUX"` ပဲ extract လုပ်ပါ။
4. `ps aux | cut -c1-10` လုပ်ပြီး process list ရဲ့ first column အပိုင်းကိုသာပြပါ။
5. `cat /etc/passwd | cut -d: -f7 | sort | uniq -c` လုပ်ပြီး shell usage count ကိုစမ်းပါ။

---



