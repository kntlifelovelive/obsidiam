

---


####  History Command 

```bash
history
```

==> `history` ရိုက်လိုက်ရင် အရင်အသုံးပြုခဲ့တဲ့ command တွေကို line number နဲ့ပြပေးတယ်။


####  Special Expansion (!!, !ls, !num …)

Bash မှာ အရင် history ကို ချက်ချင်းခေါ်ထုတ်သုံးချင်ရင် **history expansion** သုံးပါတယ်။

|Syntax|အလုပ်လုပ်ပုံ|Example|Result|
|---|---|---|---|
|`!!`|နောက်ဆုံး run ခဲ့တဲ့ command ကို run|`!!`|အရင် command ကို ထပ်ပြီး run|
|`!ls`|ls နဲ့စတဲ့ နောက်ဆုံး command ကို run|`!ls`|`ls -l /home` စသဖြင့်|
|`!num`|history number တိတိနဲ့ run|`!105`|history 105 command ကို run|
|`!-n`|နောက်ဆုံးမှ n ကွာတဲ့ command run|`!-2`|နောက်ဆုံးကနေ 2 ကြာတဲ့ command|
|`!string:p`|run မလုပ်ဘဲ command ပြပေး|`!ls:p`|`ls -la` ကို ပြပေးတယ်|
|`!$`|နောက်ဆုံး command ရဲ့ last argument|`cat !$`|အရင် command နဲ့သုံးခဲ့တဲ့ file ကို သုံး|
|`!*`|နောက်ဆုံး command ရဲ့ arguments အကုန်|`echo !*`|argument အကုန်ထပ်သုံး|
|`^old^new`|နောက်ဆုံး command ထဲက string ကိုပြောင်းပြီး run|`^foo^bar`|foo → bar ပြောင်းပြီး run|


####  Example

```bash
$ ls -l /home/user/docs
# အခု နောက်ဆုံး command

$ !!
# အပေါ်က ls -l /home/user/docs ကို ထပ် execute

$ !ls
# ls နဲ့စတဲ့နောက်ဆုံး command → ls -l /home/user/docs

$ !105
# history number 105 မှာရှိတဲ့ command ကို run

$ echo hello world
$ echo !$
# Output => echo world

$ cp file1.txt file2.txt
$ mv !$ backup/
# mv file2.txt backup/  ← နောက်ဆုံး argument သုံးသွားတယ်
```

####  History Cheat Sheet

|Command|Description|
|---|---|
|`history`|history list ပြ|
|`!!`|နောက်ဆုံး command run|
|`!string`|string နဲ့စတဲ့ နောက်ဆုံး command run|
|`!num`|history number နဲ့ run|
|`!-n`|နောက်ဆုံးမှ n ကွာတဲ့ command run|
|`!$`|နောက်ဆုံး command ရဲ့ last argument|
|`!*`|နောက်ဆုံး command ရဲ့ arguments အကုန်|
|`!string:p`|run မလုပ်ဘဲ ပြပေး|
|`^old^new`|နောက်ဆုံး command ထဲက text ကိုပြောင်းပြီး run|


###  Note

- တခါတလေ အရေးကြီး command တွေ (e.g. `rm -rf`) ကို !! နဲ့ run လိုက်ရင် အန္တရာယ်ရှိနိုင်တယ်။ **အမြဲ double check** လုပ်ပါ။
  
#####  Linux Command Line Cheatsheet (Basic Command Note)

|Command|Usage|Example|Note|
|---|---|---|---|
|**echo**|Text/variable ကို print|`echo "Hello"`|variable ထည့်လို့ရ (`echo $USER`)|
|**date**|Date/Time ပြ|`date +"%Y-%m-%d %H:%M:%S"`|custom format ပြနိုင်|
|**whoami**|Current user ပြ|`whoami`|`sudo whoami` = root|
|**ls**|File list|`ls -la`|`-l` long, `-a` hidden, `-lh` human readable|
|**history reuse**|နောက်ဆုံး command ပြန် run|`!!`, `!ls`|အလွန် အဆင်ပြေ|
|**Shortcuts**|Cursor move/edit|`Ctrl+A`, `Ctrl+E`, `Ctrl+U`, `Ctrl+K`|bash/zsh မှာ အလွန် အသုံးဝင်|


|Command|Usage|Example|Note|
|---|---|---|---|
|**pwd**|Current directory path|`pwd`|eg: `/home/kyaw`|
|**cd**|Directory change|`cd /etc`, `cd ~`, `cd -`, `cd ..`|`~` home, `..` parent|
|**ls (advanced)**|File listing|`ls -lh`, `ls -t`, `ls -R`|size, time, recursive|
|**cat**|Show file content|`cat file.txt`|small files အတွက်|
|**less**|Scrollable file viewer|`less /etc/passwd`|`q` quit, `/search`|
|**file**|Check file type|`file /bin/ls`|binary/text မသိချင်ရင် အသုံးဝင်|


|Command|Usage|Example|Note|
|---|---|---|---|
|**touch**|Empty file create / update modified time|`touch notes.txt`|multiple files `touch a b c`|
|**mkdir**|Directory create|`mkdir -p proj/linux/lesson3`|`-p` nested create|
|**cp**|Copy file/folder|`cp f1 f2`, `cp -r dir dir_backup`|`-r` recursive|
|**mv**|Move/Rename|`mv old.txt new.txt`|folder move/rename နှစ်မျိုးလုံး|
|**rm**|Remove file/folder|`rm file`, `rm -r dir`|⚠ danger – permanent|
|**rmdir**|Remove empty dir only|`rmdir emptydir`|non-empty → error|


|Command|Usage|Example|Note|
|---|---|---|---|
|**head**|Show first N lines|`head -n 5 file.txt`|default = 10|
|**tail**|Show last N lines|`tail -n 20 file.txt`|`-f` for realtime log|
|**wc**|Count lines/words/chars|`wc -l file.txt`|-l line, -w words|
|**sort**|Sort file content|`sort file`, `sort -r file`, `sort -n nums.txt`|text/numeric|
|**uniq**|Remove duplicates|`sort file|uniq -c`|
|**grep**|Search text in file|`grep root /etc/passwd`, `grep -i text file`|`-r` recursive search|


---
