
## Bash script in Variable and Special Variable 

* * *

## **1\. Variables**

Variable တွေက Data (string, number, array, etc.) တွေကို သိမ်းဆည်းဖို့ အသုံးပြုတာပါ။ Bash မှာ Variable တစ်ခုကို `=` ကို သုံးပြီး သတ်မှတ်နိုင်တယ်။

**Syntax:**

```bash
VARIABLE_NAME=value
```

**Example:**

```bash
#!/bin/bash

name="Kyaw"
age=25

echo "My name is $name and I am $age years old."
```

**Output:**

```
My name is Kyaw and I am 25 years old.
```

* * *

## **2\. Variable Types (Variable အမျိုးအစားများ)**

Bash မှာ Variable တွေကို Data Type မသတ်မှတ်ပေးပဲ String အနေနဲ့ သိမ်းမယ်။ ဒါပေမယ့် **`declare`** command ကိုသုံးပြီး Variable တွေကို အမျိုးအစား သတ်မှတ်နိုင်ပါတယ်။

| **Type** | **Syntax** | **Description** |
| --- | --- | --- |
| Normal Variable | `var=value` | Default variable |
| Readonly Variable | `declare -r var=value` | Variable ကို Lock လုပ်ပြီး ပြောင်းလဲလို့မရ |
| Integer Variable | `declare -i var=10` | Number တွေအတွက် သီးခြားသတ်မှတ်နိုင် |
| Array Variable | `declare -a var=(1 2 3 4)` | Array format နဲ့ သတ်မှတ်နိုင် |

**Example:**

```bash
#!/bin/bash

declare -r myvar="Cannot Change"
declare -i mynumber=100

echo "$myvar"
echo "Number: $mynumber"

# myvar="New Value"  # Error: Read-only variable
```

* * *

## **3\. Special Variables**

Bash မှာ Built-in Special Variables တွေ ရှိပြီး, Shell Script ရဲ့ Execution & Arguments တွေနဲ့ပတ်သက်ပြီး အလုပ်လုပ်ပေးတယ်။

| **Variable** | **Description** |
| --- | --- |
| `$0` | Script Name (File Name) |
| `$1, $2, $3...` | Script Arguments (Command-line arguments) |
| `$#` | Number of arguments passed |
| `$@` | All arguments as list |
| `"$*"` | All arguments as a single string |
| `$?` | Last command execution status (0 = Success, 1+ = Error) |
| `$$` | Current Script Process ID (PID) |
| `$!` | Last background process ID |

### **Example 1: Script Name & Arguments**

```bash
#!/bin/bash

echo "Script Name: $0"
echo "First Argument: $1"
echo "Second Argument: $2"
echo "Total Arguments: $#"
echo "All Arguments: $@"
```

Run:

```bash
bash script.sh Kyaw 25
```

Output:

```
Script Name: script.sh
First Argument: Kyaw
Second Argument: 25
Total Arguments: 2
All Arguments: Kyaw 25
```

* * *

### **Example 2: Exit Status (`$?`)**

```bash
#!/bin/bash

ls /etc/passwd
echo "Exit Status: $?"  # Success -> 0

ls /fake/path
echo "Exit Status: $?"  # Error -> 2 (or other non-zero value)

```

### **Example 3: Process ID (`$$` & `$!`)**

```bash
#!/bin/bash

echo "Current Script PID: $$"

sleep 5 &
echo "Last Background Process PID: $!"
```

### **Example 4: Looping Through Arguments (`$@` vs `$*`)**

```bash
#!/bin/bash

echo "Using \$@"
for arg in "$@"; do
  echo "$arg"
done

echo "Using \$*"
for arg in "$*"; do
  echo "$arg"
done
```

Run:

```bash
bash script.sh Hello World Bash
```

Output:

```
Using $@
Hello
World
Bash

Using $*
Hello World Bash
```

**Note:**

- `$@` = Separate arguments
- `$*` = Single string

ဒါက `Bash Variable` နဲ့ `Special Variable` အသုံးပြုပုံတွေပါ။

### **Special Variables Table**

| Variable | Description |
| --- | --- |
| $0  | Script ကိုယ်တိုင်ရဲ့ နာမည် (path နဲ့အတူ) |
| $1, $2, $3, ... | Command-line arguments တွေ (အစဉ်လိုက်) |
| $#  | Command-line arguments တွေရဲ့ စုစုပေါင်း ဦးရေ |
| $\* | Command-line arguments အားလုံးကို တစ်ခုတည်းသော string အဖြစ် |
| $@  | Command-line arguments အားလုံးကို သီးခြားသီးခြား arguments အဖြစ် |
| $?  | နောက်ဆုံး execute လုပ်ခဲ့တဲ့ command ရဲ့ exit status |
| $$  | လက်ရှိ process ရဲ့ Process ID (PID) |
| $!  | နောက်ဆုံး background process လုပ်ခဲ့တဲ့ command ရဲ့ PID |
| $UID | လက်ရှိ user ရဲ့ user ID |
| $USER | လက်ရှိ user ရဲ့ username |
| $HOME | လက်ရှိ user ရဲ့ home directory |
| $PWD | လက်ရှိ working directory |
| $SHELL | လက်ရှိ user ကသုံးနေတဲ့ shell |

## Note:

- Positional Parameters: $0, $1, $2, ... တွေကို positional parameters လို့ခေါ်ပါတယ်။
- Special Parameters: $\*, $@ တွေကို special parameters လို့ခေါ်ပါတယ်။
- Shell Variables: $UID, $USER, $HOME, $PWD, $SHELL တွေကို shell variables လို့ခေါ်ပါတယ်။
- Process ID: PID ဟာ ഓരိုးရိုး process တစ်ခုချင်းစီကို သီးခြားခွဲခြား သတ်မှတ်ပေးတဲ့ number တစ်ခုပါ။
- Exit Status: Exit status ဟာ command တစ်ခု execute ပြီးနောက် အောင်မြင်စွာ ပြီးစီးခဲ့လား၊ မပြီးစီးခဲ့လားဆိုတာကို ပြောပြပေးပါတယ်။ 0 ဆိုတာ အောင်မြင်တယ်လို့ ဆိုလိုပါတယ်။

### Example Script in Bash for Linux.

```bash
#!/bin/bash

echo "This script is called: $0"
echo "You are user: $USER"
echo "Your home directory is: $HOME"

# Command-line arguments တွေကို ပြသခြင်း
for i in "$@"; do
  echo "Argument $i"
done


```


# **Bash Variables**

---

### **1. Special Bash Variables**  
Bash မှာ built-in ဖြစ်ပြီး system-level အချက်အလက်တွေကို ဆောင်ထားတဲ့ variable တွေပါ။ 

| Variable    | ဖော်ပြချက်                                                                                     |
|-------------|---------------------------------------------------------------------------------------------|
| `$0`        | Script ရဲ့ အမည်ကို ပြသည်။                                                                 |
| `$1, $2...` | Command-line arguments တွေကို လိုက်စဉ် access ပြုသည်။                                     |
| `$#`        | Command-line arguments ရဲ့ **အရေအတွက်** ကို ပြသည်။                                          |
| `$@`        | Command-line arguments အားလုံးကို ပြသည်။                                                   |
| `$?`        | နောက်ဆုံး run ခဲ့တဲ့ command ရဲ့ **exit status** ကို ပြသည် (0=Success, 1=Error)။          |
| `$$`        | Script ရဲ့ process ID (PID) ကို ပြသည်။                                                    |
| `$!`        | နောက်ဆုံး run ခဲ့တဲ့ background process ရဲ့ PID ကို ပြသည်။                                |

**ဥပမာ**  
```bash
echo "Script Name: $0"
echo "First Argument: $1"
echo "Number of Arguments: $#"
echo "All Arguments: $@"
```

---

### **2. String Variables**  
String variables က text သာလှမ်းထားသည့် variable မျိုးဖြစ်ပါတယ်။

**String Variable Creation**
```bash
name="Kyaw"
greeting="Hello, $name!"
echo $greeting
```

**String Concatenation**  
```bash
part1="Hello"
part2="World"
full="$part1 $part2"
echo $full
```

---

### **3. Integer Variables**  
Integer variables က ဂဏန်းများသာ သိမ်းဆည်းနိုင်တဲ့ variable မျိုးဖြစ်ပါတယ်။

**Integer Variable Creation**
```bash
num1=10
num2=20
sum=$((num1 + num2))  # Arithmetic operation
echo "Sum: $sum"
```

**Arithmetic Operations in Bash**
| Operator | ဖော်ပြချက်           |
|----------|-------------------|
| `+`      | ထပ်ပေါင်းခြင်း      |
| `-`      | လျော့နုတ်ခြင်း       |
| `*`      | မြှောက်ခြင်း        |
| `/`      | Division (integer) |
| `%`      | Remainder         |

---

### **4. Constant Variables**  
Constant variables က တစ်ခါသတ်မှတ်ပြီးပြီဆိုရင် ပြန်ပြောင်းလဲလို့မရအောင် ပြုလုပ်ထားတဲ့ variables ဖြစ်ပါတယ်။

**Constant Variable Creation**
```bash
readonly PI=3.14159
echo "Pi: $PI"

# Try changing the value (Error will occur)
# PI=3.14
```

---

### **5. Array Variables**  
Array variables ကတစ်ခုထက်ပိုတဲ့ value တွေကို index အလိုက် သိမ်းဆည်းဖို့ အသုံးပြုပါတယ်။

#### **Array Creation**
```bash
fruits=("Apple" "Banana" "Cherry")
```

#### **Accessing Elements**
```bash
echo "First Fruit: ${fruits[0]}"
```

#### **Adding/Modifying Elements**
```bash
fruits[1]="Blueberry"  # Replace "Banana" with "Blueberry"
fruits+=("Dragonfruit")  # Add new element
```

#### **Iterating Through Array**
```bash
for fruit in "${fruits[@]}"; do
    echo $fruit
done
```

#### **Array Length**
```bash
echo "Number of Fruits: ${#fruits[@]}"
```

---

**Summary**  
| Variable Type        | ဖော်ပြချက်                                                                 |
|----------------------|------------------------------------------------------------------------|
| Special Variables    | Script, Command-line arguments, Process ID, Exit status စတာတွေကို သိမ်းဆည်းပေးတယ်။|
| String Variables     | Text value တွေကို သိမ်းဆည်းဖို့ အသုံးပြုတယ်။                                   |
| Integer Variables    | ဂဏန်းတွေကို သိမ်းဆည်းပြီး Arithmetic တွေလုပ်ဖို့ အသုံးပြုတယ်။                   |
| Constant Variables   | တန်ဖိုးအပြောင်းအလဲမပြုနိုင်တဲ့ Variable မျိုး။                                     |
| Array Variables      | တန်ဖိုးစုံတွေကို index အလိုက် သိမ်းဆည်းဖို့ အသုံးပြုတယ်။                        |


---  

### **1. Extra Special Variables**  
အခြားအသုံးဝင်နိုင်တဲ့ `Bash Special Variables` တွေဖြည့်ပေးလိုက်မယ်။  

| Variable | Description |
|----------|------------|
| `$IFS` | Internal Field Separator (default: space, tab, newline) |
| `$OLDPWD` | Previous working directory (last used `cd` location) |
| `$RANDOM` | Generates a random number (0 - 32767) |
| `$SECONDS` | Time (in seconds) since script started running |
| `$LINENO` | Current line number in the script |
| `$HOSTNAME` | System hostname |
| `$OSTYPE` | OS type (e.g., linux-gnu) |
| `$PPID` | Parent Process ID (PID of the script's parent) |

#### **Example Usage**
```bash
#!/bin/bash
echo "Random Number: $RANDOM"
echo "Script has been running for $SECONDS seconds."
echo "Current Line Number: $LINENO"
echo "Previous Directory: $OLDPWD"
```

---

### **2. String Manipulation with Variables**  
Bash မှာ String Variable တွေကို Modify လုပ်နိုင်တဲ့ နည်းလမ်းတွေဖြည့်ပေးမယ်။  

| Expression | Description |
|------------|-------------|
| `${#var}` | String length |
| `${var:position}` | Substring (starting from position) |
| `${var:pos:length}` | Substring (specific length) |
| `${var#pattern}` | Remove shortest match (prefix) |
| `${var##pattern}` | Remove longest match (prefix) |
| `${var%pattern}` | Remove shortest match (suffix) |
| `${var%%pattern}` | Remove longest match (suffix) |
| `${var/old/new}` | Replace first match |
| `${var//old/new}` | Replace all matches |

#### **Example**
```bash
#!/bin/bash

str="Hello Bash Scripting"
echo "Length: ${#str}"
echo "Substring: ${str:6:4}"  # Bash
echo "Remove Prefix: ${str#Hello }"  # Bash Scripting
echo "Replace: ${str/Bash/Linux}"
```

---

### **3. Advanced Arithmetic Operations**  
`expr`, `let`, `(( ))`, `[ ]` နဲ့ `bc` ကိုအသုံးပြု၍ Math Operations တွေ ပြုလုပ်နိုင်တယ်။  

```bash
#!/bin/bash
num1=10
num2=3

# Using expr
sum=$(expr $num1 + $num2)
echo "Sum: $sum"

# Using let
let mul=num1*num2
echo "Multiplication: $mul"

# Using (( ))
div=$((num1 / num2))
echo "Division: $div"

# Using bc for floating point math
float_div=$(echo "scale=2; $num1 / $num2" | bc)
echo "Float Division: $float_div"
```

---

### **4. Using Associative Arrays (Bash 4.0+)**  
Normal array တွေက Index-based ဖြစ်တယ်။ Associative Array တွေက Key-Value format ဖြစ်တယ်။  

```bash
#!/bin/bash

declare -A person
person[name]="Kyaw"
person[age]=25
person[country]="Myanmar"

echo "Name: ${person[name]}"
echo "Age: ${person[age]}"
echo "Country: ${person[country]}"
```

---

## **1. Additional Special Variables**
မင်းရဲ့ note မှာပါတဲ့ `$0`, `$1`, `$#`, `$@`, `$*`, `$?`, `$$`, `$!` တွေထပ်ပြီး **မပါတာတွေ**ကို ဖြည့်ပေးမယ်။  

| Variable | Description |
|----------|------------|
| `$UID` | Current User ID (System User ID) |
| `$EUID` | Effective User ID (Superuser = 0) |
| `$GROUPS` | Group IDs of the current user |
| `$PWD` | Present Working Directory |
| `$OLDPWD` | Previous Directory |
| `$HOME` | Home Directory |
| `$SHELL` | Current Shell Path |
| `$HOSTNAME` | Hostname of the System |
| `$RANDOM` | Generates a random number (0 - 32767) |
| `$SECONDS` | Time (in seconds) since script started running |
| `$LINENO` | Current script line number |
| `$PPID` | Parent Process ID |
| `$OSTYPE` | OS type (e.g., `linux-gnu`) |

---

## **2. Variable Scope (Local vs Global)**
မင်းရဲ့ note မှာ **Variable Scope** အကြောင်း မပါတာမို့ ထပ်ဖြည့်ပေးလိုက်မယ်။  

| Scope | Command | Description |
|-------|---------|-------------|
| **Global** | `var=value` | Default Variable (accessible in script and subshells) |
| **Local** | `local var=value` | Limited to current function |

**Example:**
```bash
#!/bin/bash

global_var="I am global"

my_function() {
  local local_var="I am local"
  echo "Inside function: $local_var"
}

echo "Outside function: $global_var"
my_function
# echo "Outside function: $local_var"  # Error: Undefined variable
```

---

## **3. String Manipulation**
### **3.1 String Length**
```bash
str="Hello Bash"
echo "Length: ${#str}"
```

### **3.2 Substring Extraction**
```bash
echo "Substring: ${str:6:4}"  # Output: Bash
```

### **3.3 Replace Part of a String**
```bash
echo "Replaced: ${str/Bash/Linux}"  # Output: Hello Linux
```

### **3.4 Remove Substring**
```bash
filename="document.txt"
echo "Without extension: ${filename%.txt}"  # Output: document
```

---

## **4. Arithmetic Operations**
Bash မှာ Math Operations တွေကို `expr`, `let`, `(( ))`, `[ ]`, `bc` နဲ့လုပ်နိုင်တယ်။  
```bash
num1=10
num2=3

# Basic Arithmetic
sum=$((num1 + num2))
sub=$((num1 - num2))
mul=$((num1 * num2))
div=$((num1 / num2))
mod=$((num1 % num2))

echo "Sum: $sum, Sub: $sub, Mul: $mul, Div: $div, Mod: $mod"
```

---

## **5. Arrays (Indexed & Associative)**
### **5.1 Indexed Array**
```bash
arr=("Apple" "Banana" "Cherry")
echo "First Item: ${arr[0]}"
echo "All Items: ${arr[@]}"
echo "Array Length: ${#arr[@]}"
```

### **5.2 Associative Array (Bash 4.0+)**
```bash
declare -A person
person[name]="Kyaw"
person[age]=25
person[city]="Yangon"

echo "Name: ${person[name]}"
echo "Age: ${person[age]}"
echo "City: ${person[city]}"
```

---

