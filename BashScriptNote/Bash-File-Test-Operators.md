
#### **Bash File Test Operators (`-b`, `-f`, `-c`, `-x`, etc.)**  

Bash မှာ **file type checking** နဲ့ **permission checking** တွေအတွက် **test operators** တွေကို `[` ... `]` (or `test` command) နဲ့ သုံးနိုင်ပါတယ်။  

---

### **1. File Type Checking Operators**  
| Operator | Description | Example |
|----------|------------|---------|
| `-b file` | Block special file (e.g., HDD, USB) ဖြစ်မဖြစ် | `[ -b /dev/sda1 ] && echo "Block device"` |
| `-c file` | Character special file (e.g., Keyboard, Mouse) | `[ -c /dev/tty0 ] && echo "Character device"` |
| `-d file` | Directory ဖြစ်မဖြစ် | `[ -d /home/kyaw ] && echo "Directory exists"` |
| `-f file` | Regular file ဖြစ်မဖြစ် | `[ -f myfile.txt ] && echo "Regular file"` |
| `-L file` | Symbolic link ဖြစ်မဖြစ် | `[ -L mylink ] && echo "Symbolic link"` |
| `-p file` | Named pipe (FIFO) file ဖြစ်မဖြစ် | `[ -p /tmp/mypipe ] && echo "Pipe exists"` |
| `-S file` | Socket file ဖြစ်မဖြစ် | `[ -S /var/run/docker.sock ] && echo "Socket exists"` |

🔹 **Example Usage:**  
```bash
if [ -f /etc/passwd ]; then
    echo "passwd file exists."
fi
```

---

### **2. File Permission Checking Operators**  
| Operator | Description | Example |
|----------|------------|---------|
| `-r file` | Read permission ရှိ/မရှိ | `[ -r myfile.txt ] && echo "Readable"` |
| `-w file` | Write permission ရှိ/မရှိ | `[ -w myfile.txt ] && echo "Writable"` |
| `-x file` | Execute permission ရှိ/မရှိ | `[ -x script.sh ] && echo "Executable"` |

🔹 **Example Usage:**  
```bash
if [ -x myscript.sh ]; then
    ./myscript.sh
else
    echo "No execute permission"
fi
```

---

### **3. File Comparison Operators**  
| Operator | Description | Example |
|----------|------------|---------|
| `file1 -nt file2` | `file1` သည် `file2` ထက် အသစ် (newer) ဖြစ်သည်။ | `[ file1 -nt file2 ] && echo "file1 is newer"` |
| `file1 -ot file2` | `file1` သည် `file2` ထက် အို (older) ဖြစ်သည်။ | `[ file1 -ot file2 ] && echo "file1 is older"` |

🔹 **Example Usage:**  
```bash
if [ file1 -nt file2 ]; then
    echo "file1 is newer than file2"
fi
```

---

### **4. Logical Operators (`-a`, `-o`, `!`)**  
| Operator | Description | Example |
|----------|------------|---------|
| `-a` | AND (condition နှစ်ခုစလုံးမှန်ရမယ်) | `[ -f file.txt -a -r file.txt ] && echo "File exists & readable"` |
| `-o` | OR (condition တစ်ခုခုမှန်ရုံပါပဲ) | `[ -f file1 -o -f file2 ] && echo "At least one file exists"` |
| `!` | NOT (condition ကို invert လုပ်ခြင်း) | `[ ! -f file.txt ] && echo "File does not exist"` |

🔹 **Example Usage:**  
```bash
if [ -f myfile.txt -a -r myfile.txt ]; then
    echo "File is readable."
fi
```

---

### **5. Integer Comparison Operators**  
| Operator | Description | Example |
|----------|------------|---------|
| `n1 -eq n2` | `n1` == `n2` (equal) | `[ 5 -eq 5 ] && echo "Equal"` |
| `n1 -ne n2` | `n1` != `n2` (not equal) | `[ 5 -ne 3 ] && echo "Not Equal"` |
| `n1 -gt n2` | `n1` > `n2` (greater than) | `[ 10 -gt 5 ] && echo "Greater"` |
| `n1 -lt n2` | `n1` < `n2` (less than) | `[ 3 -lt 8 ] && echo "Lesser"` |
| `n1 -ge n2` | `n1` >= `n2` (greater or equal) | `[ 10 -ge 10 ] && echo "Greater or Equal"` |
| `n1 -le n2` | `n1` <= `n2` (less or equal) | `[ 2 -le 5 ] && echo "Less or Equal"` |

🔹 **Example Usage:**  
```bash
a=5
b=10
if [ $a -lt $b ]; then
    echo "$a is less than $b"
fi
```

---

## **Summary**  
✅ **File Type Checking** (`-b`, `-c`, `-d`, `-f`, `-L`, `-p`, `-S`)  
✅ **File Permission Checking** (`-r`, `-w`, `-x`)  
✅ **File Comparison** (`-nt`, `-ot`)  
✅ **Logical Operators** (`-a`, `-o`, `!`)  
✅ **Integer Comparison** (`-eq`, `-ne`, `-gt`, `-lt`, `-ge`, `-le`)  

ဒီ table တွေနဲ့ example တွေက **Bash scripting** လုပ်တဲ့အခါ file checking, permission checking, logic operation တွေအတွက် အသုံးဝင်လိမ့်မယ််။

---

### **Appendix: Common Features in Bash Shell**  

Bash shell တွင် အသုံးများသော common feature များကို **Table** နဲ့ **Examples** များပါဝင်အောင် ဖော်ပြပေးလိုက်ပါတယ်။  

---

### **1. Variables (အမြဲပြောင်းလဲနိုင်သောတန်ဖိုးများ)**  
| Feature | Description | Example |
|---------|------------|---------|
| **User Variables** | အသုံးပြုသူသတ်မှတ်သော variable | `name="Kyaw"` |
| **Environment Variables** | System-level variable | `echo $HOME` |
| **Command Substitution** | Command output ကို variable တစ်ခုထဲသိမ်းခြင်း | `today=$(date +"%Y-%m-%d")` |

**Example:**  
```bash
name="Kyaw"
echo "Hello, $name!"
```

---

### **2. Command Substitution (Command output ကို variable ထဲသိမ်းခြင်း)**  
| Syntax | Description | Example |
|--------|------------|---------|
| `` `command` `` | Command result ကို variable ထဲသိမ်းနိုင် | `current_time=\`date\`` |
| `$(command)` | Command result ကို variable ထဲသိမ်းနိုင် | `current_time=$(date)` |

**Example:**  
```bash
now=$(date +"%H:%M:%S")
echo "Current time is $now"
```

---

### **3. Conditional Statements (if, elif, else)**  
| Feature | Description | Example |
|---------|------------|---------|
| **if statement** | Condition တစ်ခုဖြင့် စစ်ဆေးခြင်း | `if [ -f file.txt ]; then echo "File exists"; fi` |
| **if-else statement** | Condition နှစ်ခုစစ်ဆေးခြင်း | `if [ $x -gt 10 ]; then echo "Big"; else echo "Small"; fi` |
| **elif statement** | Condition များစွာစစ်ဆေးခြင်း | `if [ $x -eq 1 ]; then ... elif [ $x -eq 2 ]; then ... fi` |

**Example:**  
```bash
read -p "Enter a number: " num
if [ $num -gt 10 ]; then
    echo "Greater than 10"
elif [ $num -eq 10 ]; then
    echo "Equal to 10"
else
    echo "Less than 10"
fi
```

---

### **4. Loops (Looping Statements)**  
| Feature | Description | Example |
|---------|------------|---------|
| **For Loop** | List ထဲက item များအားလုံးကို iterate | `for i in {1..5}; do echo $i; done` |
| **While Loop** | Condition တစ်ခုရှိသည်အထိ loop လည်ခြင်း | `while [ $x -lt 5 ]; do echo $x; ((x++)); done` |

**Example:**  
```bash
for i in {1..5}
do
    echo "Number: $i"
done
```

---

### **5. Functions (တန်ဖိုးပြန်ပေးသော သို့မဟုတ် မပြန်ပေးသော Function များ)**  
| Feature | Description | Example |
|---------|------------|---------|
| **Function Declaration** | Function တစ်ခုရေးသားခြင်း | `function say_hello() { echo "Hello"; }` |
| **Function Call** | Function ကိုခေါ်သုံးခြင်း | `say_hello` |

**Example:**  
```bash
function greet() {
    echo "Hello, $1!"
}
greet "Kyaw"
```

---

### **6. Arithmetic Operations (ဂဏန်း တွက်ခြင်း)**  
| Operator | Description | Example |
|----------|------------|---------|
| `+` | Addition | `echo $((5 + 3))` |
| `-` | Subtraction | `echo $((5 - 3))` |
| `*` | Multiplication | `echo $((5 * 3))` |
| `/` | Division | `echo $((10 / 2))` |
| `%` | Modulus | `echo $((10 % 3))` |

**Example:**  
```bash
a=5
b=3
sum=$((a + b))
echo "Sum: $sum"
```

---

### **7. String Manipulation (စာကြောင်းနှင့်ပတ်သက်သောလုပ်ဆောင်မှုများ)**  
| Feature | Description | Example |
|---------|------------|---------|
| **String Length** | စာကြောင်း အရှည်တွက်ခြင်း | `echo ${#string}` |
| **Substring Extraction** | စာကြောင်းအစိတ်အပိုင်းရယူခြင်း | `echo ${string:2:3}` |
| **Replace Substring** | စာလုံးအစားထိုးခြင်း | `echo ${string/old/new}` |

**Example:**  
```bash
text="Hello Bash"
echo "Length: ${#text}"
echo "Substring: ${text:0:5}"
```

---

### **8. File & Directory Operations (ဖိုင်နှင့် ဒါရိုက်ထရီ ပတ်သက်သော commands)**  
| Command | Description | Example |
|---------|------------|---------|
| `touch file` | Empty file တစ်ခုဖန်တီးခြင်း | `touch myfile.txt` |
| `mkdir dir` | Directory တစ်ခုဖန်တီးခြင်း | `mkdir mydir` |
| `rm file` | File ဖျက်ခြင်း | `rm myfile.txt` |
| `rmdir dir` | Empty directory ဖျက်ခြင်း | `rmdir mydir` |

**Example:**  
```bash
mkdir my_folder
cd my_folder
touch newfile.txt
ls
```

---

### **9. Process Management (Process တွေကို ထိန်းချုပ်ခြင်း)**  
| Command | Description | Example |
|---------|------------|---------|
| `ps` | Running process များပြခြင်း | `ps aux` |
| `kill PID` | Process ကို kill ခြင်း | `kill 1234` |
| `jobs` | Background jobs ကြည့်ခြင်း | `jobs` |
| `fg %job_id` | Background job ကို foreground ပြန်ခေါ် | `fg %1` |

**Example:**  
```bash
sleep 30 &
jobs
kill %1
```

---

### **10. Background & Foreground Execution (Background & Foreground များထိန်းချုပ်ခြင်း)**  
| Command | Description | Example |
|---------|------------|---------|
| `command &` | Background မှာ command chạyခြင်း | `ping google.com &` |
| `fg` | Background job ကို foreground ပြန်ခေါ်ခြင်း | `fg %1` |

**Example:**  
```bash
sleep 60 &
echo "Process is running in the background..."
jobs
```

---

### **11. Input/Output Redirection (File input/output ထိန်းချုပ်ခြင်း)**  
| Operator | Description | Example |
|----------|------------|---------|
| `>` | Output to file (overwrite) | `echo "Hello" > file.txt` |
| `>>` | Output to file (append) | `echo "World" >> file.txt` |
| `<` | Input from file | `wc -l < file.txt` |


---

**Example:**  
```bash
echo "Bash Scripting" > myfile.txt
cat myfile.txt
```

---

ဒီ table တွေနဲ့ example တွေက Bash Shell မှာ အထွေထွေ အသုံးများတဲ့ feature တွေပဲဖြစ်ပါတယ်။ Bash shell ကိုပိုမိုတိုးတက်စွာ အသုံးပြုနိုင်ဖို့ အဲ့ဒီ concept တွေကို နားလည်ဖို့ လိုပါတယ်။ 

---

