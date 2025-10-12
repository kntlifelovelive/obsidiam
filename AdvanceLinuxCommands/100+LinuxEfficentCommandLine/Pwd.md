
---
#  **Command:** `pwd`

### **Usage**
 ==> `pwd` = **Print Working Directory**
###  **Full Meaning**
`"Print working directory"`  ဆိုတာပါ။   Linux terminal မှာ မင်းရဲ့ _လက်ရှိ location (path)_ ကို ပြသဖို့ သုံးပါတယ်။
###  **Description**

`pwd` command က မင်းအခု terminal မှာ ရှိနေတဲ့ directory (path) ကိုပြပေးတယ်။  
ဥပမာ — မင်းက `/home/kyaw/Documents` ထဲမှာ ရှိနေတယ်ဆိုရင်  
`pwd` လုပ်လိုက်တာနဲ့

```bash
/home/kyaw/Documents
```

ဆိုပြီး ပြပေးမယ်။

###  **Syntax**

```bash
pwd [OPTION]
```

### **Common Options**

|Option|Description|
|---|---|
|`-L`|Show **logical path** (including symlinks)|
|`-P`|Show **physical path** (real path, follow symlinks)|
|`--help`|Show help message|
|`--version`|Show version info|


###  **Examples (15 Total)**

|No|Command|Description|
|---|---|---|
|1|`pwd`|Show current working directory path|
|2|`pwd -L`|Show logical path (default behavior)|
|3|`pwd -P`|Show physical path (resolve symbolic links)|
|4|`cd /etc && pwd`|Change to `/etc` directory, then print current path|
|5|`cd ~ && pwd`|Go to home directory and show path|
|6|`cd /var/log && pwd`|Move to `/var/log` and print its full path|
|7|`echo "Current path: $(pwd)"`|Combine with `echo` to print path inside a sentence|
|8|`pwd > current_path.txt`|Save the current directory path to a file|
|9|`cat current_path.txt`|Check the path saved by previous command|
|10|`pwd && ls`|Print path and list files in it|
|11|`cd .. && pwd`|Move one directory up and show new path|
|12|`alias whereami='pwd'`|Create alias “whereami” for `pwd`|
|13|`cd / && pwd`|Move to root directory and show it|
|14|`cd /tmp && pwd -P`|Show resolved real path of `/tmp`|
|15|`echo $PWD`|Environment variable method (same as `pwd`)|


## **Pro Tip**

🔸 **`pwd`** command ကို အသုံးများတဲ့ script တွေအတွက်  
တကယ်အသုံးဝင်တယ် — especially backup scripts, automation scripts တွေမှာ current path သိဖို့လိုတယ်။

*Example*

```bash
#!/bin/bash
echo "You are in: $(pwd)"
```

###  **Summary Table**

|Command|Usage Summary|
|---|---|
|`pwd`|Show current working directory|
|`pwd -L`|Show logical path|
|`pwd -P`|Show physical path (resolve symlink)|
|`echo $PWD`|Environment variable showing current path|
|`pwd > file.txt`|Save current path to a file|


**Note**  
`pwd` က Linux CLI မှာ _သိထားသင့်တဲ့ basic command တစ်ခု_ ဖြစ်ပြီး  
မင်းဘယ် directory ထဲမှာရှိတယ်ဆိုတာသိဖို့အတွက် မရှိမဖြစ်လိုအပ်ပါတယ်

---
