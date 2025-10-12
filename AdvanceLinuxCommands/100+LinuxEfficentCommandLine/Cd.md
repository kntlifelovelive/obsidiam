
---

##  **`cd` Command – Change Directory**

🔹 **Usage:** `cd` stands for **change directory**  
🔹 **Purpose:** Directory (folder) တစ်ခုကနေ တစ်ခုသို့ **သွားဖို့/ပြောင်းဖို့** အသုံးပြုတာပါ။


###  **Basic Syntax**

```bash
cd [directory_path]
```

==> `directory_path` ဆိုတာက သွားချင်တဲ့ ဖိုလ်ဒါလမ်းကြောင်း ဖြစ်ပါတယ်။


##  **15 Practical Examples of `cd` command**

### 1.Go to a directory

```bash
cd /home/kyaw/Documents
```

==> `/home/kyaw/Documents` ကိုသွားမယ်။



### 2 Go to your home directory

```bash
cd ~
```

==> user ရဲ့ home folder ကို ပြန်သွားတယ်။



### 3. Go to parent directory (one level up)

```bash
cd ..
```

==> လက်ရှိ directory ထဲကနေ **တစ်လှမ်းအပေါ် folder** ကိုသွားတယ်။



### 4. Go two levels up

```bash
cd ../..
```

==> လှမ်းနှစ်လှမ်းအထိ အပေါ် directory ကို သွားတယ်။



### 5.Go to root directory

```bash
cd /
```

==> Linux filesystem ရဲ့ **root (အမြင့်ဆုံး)** directory သွားတယ်။

### 7.Go to previous directory

```bash
cd -
```

==> အရင်သွားခဲ့တဲ့ directory ကို ပြန်သွားတယ်။



### 7.Change directory using absolute path

```bash
cd /usr/local/bin
```

==> Full path အသုံးပြုပြီး သွားတယ်။


### 8.Change directory using relative path

```bash
cd Documents/Projects
```

==> လက်ရှိ folder ထဲက `Documents/Projects` ကို သွားတယ်။


### 9.Go to another user’s home directory (if permission allowed)

```bash
cd /home/otheruser
```



### 10.Combine with `ls` to verify

```bash
cd /etc && ls
```

==> `/etc` သွားပြီး ဖိုင်တွေကို တစ်ခါတည်း ပြတယ်။


### 11.Use tab auto-completion

```bash
cd Doc[TAB]
```

==> Directory name ကို အလိုအလျောက် ဖြည့်ပေးတယ်။



### 12.Change directory name with spaces

```bash
cd "My Documents"
# or
cd My\ Documents
```

==> Space ပါတဲ့ folder နာမည်ကို သွားချင်တဲ့အခါ ။



### 13.Use `pwd` to confirm after `cd`

```bash
cd /var/log
pwd
```

==> ပြောင်းပြီးနောက် path ကို verify လုပ်။



### 14. Go inside hidden folder

```bash
cd .config
```

==>  “.” နဲ့ စတဲ့ hidden folder ကို သွားတယ်။



### 15 Combine with shortcuts

```bash
cd ~/Downloads
cd ~/Desktop
```

==> Home directory အောက်က shortcut path ။


##  **Note Summary**

|Command|Meaning|
|---|---|
|`cd`|Change directory|
|`cd ..`|Go one folder up|
|`cd -`|Go to previous folder|
|`cd ~`|Go to home folder|
|`cd /`|Go to root folder|

---

