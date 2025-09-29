
# <span style="background-color: lightgreen; color: black; padding: 2px 5px; border-radius: 5px;">Bash Function Details format</span>


Bash script မှာ `function` သုံးပြီး ပြုလုပ်နိုင်တဲ့ လုပ်ဆောင်ချက်တွေကို မဖြစ်မနေ သိထားသင့်ပါတယ်။ `function` သည် code ကို ပြန်သုံးနိုင်ဖို့အတွက် သင့်လျှော်ပြီး၊ script တွေအတွက် modular ဖြစ်စေတဲ့အတွက် maintenance လွယ်ကူပါတယ်။

---

# **Bash Function Basic**
Bash function ကို ရေးဖို့နည်း (၂) မျိုးရှိပါတယ်။  

### **Syntax 1 – function keyword အသုံးပြုခြင်း**
```bash
function my_function {
    echo "Hello from function!"
}
```
### **Syntax 2 – Parentheses အသုံးပြုခြင်း**
```bash
my_function() {
    echo "Hello from function!"
}
```
> **မှတ်ချက်**: Function ကို run မလုပ်ခင် သတ်မှတ်ထားဖို့လိုတယ်။ Function ကို run ခေါ်ရန် `create function name` ကို call လုပ်  အသုံးပြုရသည်။

---

## **Example 1 – Basic Function**
```bash
#!/bin/bash

greet() {
    echo "မင်္ဂလာပါ! ကိုရေ Bash Function သင်ကြားမှု 😃"
}

# Function ကို ခေါ်သုံးခြင်း
greet

```
🔹 ဒီမှာ `greet` ဆိုတဲ့ function ကို သတ်မှတ်ပြီး၊ အဲ့ function ကို script ထဲမှာ ပြန်ခေါ်သုံးထားတာပါ။

---

## **Example 2 – Function and Parameter (Arguments)**
```bash
#!/bin/bash

add_numbers() {
    sum=$(( $1 + $2 ))
    echo "အထွေထွေ ပေါင်းလိုက်ရင်: $sum"
}

add_numbers 5 10
add_numbers 20 30
```
🔹 `add_numbers` ဆိုတဲ့ function ကို ဖန်တီးပြီး၊ Parameter (Arguments) ၂ ခု `$1` `$2` ထည့်နိုင်ပါတယ်။  
🔹 `add_numbers 5 10` ဆိုပြီး function ကို parameter ၂ ခုနဲ့ call လုပ်လိုက်တာပါ။

---

## **Example 3 – Return Value (Exit Status)**
```bash
#!/bin/bash

check_even() {
    if (( $1 % 2 == 0 )); then
        return 0
    else
        return 1
    fi
}

check_even 8
if [ $? -eq 0 ]; then
    echo "Even Number"
else
    echo "Odd Number"
fi
```
🔹 `return` ကို သုံးပြီး Function မှာ Exit Status ပြန်ထုတ်နိုင်တယ်။  
🔹 `$?` ကို သုံးပြီး function return value ကို စစ်ဆေးနိုင်တယ်။  
🔹 0 ဆိုရင် Success, 1 ဆိုရင် Failure လို့ ယူနိုင်တယ်။

---

## **Example 4 – Function and Looping**


```bash

#!/bin/bash

countdown() {
    for ((i=$1; i>=0; i--)); do
        echo "$i..."
        sleep 1
    done
    echo "Time's up! ⏰ \a"
}

countdown 5


```


🔹 `countdown` ဆိုတဲ့ function ကို ဖန်တီးပြီး Looping ပတ်မယ်။
🔹 `sleep 1` သုံးပြီး တစ်စက္ကန့်စီ time out  မယ်။  
🔹 `countdown 5` လို့ ခေါ်လိုက်ရင် 5 ကနေ 0 ထိ တစ်ခုချင်းဆင်းမယ်။

---

## **Example 5 – Function တွေကို Recursive ခေါ်သုံးခြင်း**
```bash

#!/bin/bash

factorial() {
    if [ $1 -le 1 ]; then
        echo 1
    else
        prev=$(factorial $(( $1 - 1 )))
        echo $(( $1 * prev ))
    fi
}

result=$(factorial 5)
echo "Factorial of 5 is $result"


```

🔹 Function မှာ Function ကို ပြန်ခေါ်နိုင်တယ်။ (Recursive Function)  
🔹 `factorial 5` လို့ run လိုက်ရင် `5! = 5x4x3x2x1 = 120` ကို တွက်ပေးမယ်။

---

### **🔹 Summary**
- Function ကို `function name {}` နဲ့ သတ်မှတ်နိုင်တယ်။
- Function ကို ခေါ်သုံးတဲ့အခါ `name` ကို ခေါ်နိုင်တယ်။
- Arguments (Parameters) တွေကို `$1`, `$2`, ... နဲ့ ထည့်နိုင်တယ်။
- `return` ကို သုံးပြီး Exit Status (0/1) ပြန်ပေးနိုင်တယ်။
- Recursive Function သုံးလို့ရတယ်။

Function တွေကို မှန်မှန်သုံးနိုင်ရင် Bash Script တွေက ပိုပြီး Clean, Maintainable ဖြစ်စေမယ်။ 

---
Bash function တွေကို `function name {}` နဲ့ သတ်မှတ်နိုင်သလို `function name () {}` ဆိုပြီးလည်း သတ်မှတ်နိုင်တယ်။   
ဒီနည်းက *POSIX-compliant* မဟုတ်ပေမယ့် Bash, Zsh, Ksh မှာ အလုပ်လုပ်နိုင်တယ်။  

---

### **More Examples for Bash Functions**

### **Example . 1**

- **Function အတွင်းမှာ Variable သတ်မှတ်ခြင်း**  

```bash

#!/bin/bash

greet() {
    name="ကိုကျော်"
    echo "မင်္ဂလာပါ $name! 😊"
}

greet


```

🔹 Function အတွင်း `name` ဆိုတဲ့ variable ကို သတ်မှတ်ပြီး echo နဲ့ output ပြထားတာ။  
🔹 `greet` function ကို ခေါ်လိုက်ရင် `မင်္ဂလာပါ ကိုကျော်! 😊` လို့ ပြမယ်။

---

## **Example. 2** 
- **Function တွေထဲက Global Variable ပြောင်းလဲခြင်း**
- 
```bash

#!/bin/bash

count=0

increment() {
    count=$((count + 1))
}

echo "Count Before: $count"
increment
echo "Count After: $count"


```

🔹 Function မှာ `count` ကို ပြောင်းလဲလိုက်တာ။  
🔹 Function အပြင်မှာ `count` ကို access လုပ်လို့ရတယ်။  

---

## **Example.3**
-  **Function တွေကို Chaining လုပ်ခြင်း**
  
```bash

#!/bin/bash

first() {
    echo "This is the first function!"
    second
}

second() {
    echo "Now inside the second function!"
}

first


```

🔹 `first` function ထဲက `second` function ကို ခေါ်လိုက်တာ။  
🔹 Output:
```
This is the first function!
Now inside the second function!
```

---

## **Example.4**
- **Function Return Value ကို Variable ထဲမှာ သိမ်းခြင်း**

```bash

#!/bin/bash

get_date() {
    echo "$(date '+%Y-%m-%d')"
}

today=$(get_date)
echo "Today is: $today"


```

🔹 `get_date` function က `date` command ကို run ပြီး output ပြန်ပေးတယ်။  
🔹 Function return value ကို variable `today` ထဲမှာ သိမ်းနိုင်တယ်။  

---

## **Example.5** 
-  **Function ကို Command Line Argument နဲ့ သုံးခြင်း**
-  
```bash

#!/bin/bash

greet_user() {
    echo "မင်္ဂလာပါ, $1!"
}

greet_user "ကိုကျော်"
greet_user "ကိုကို"

```

🔹 `$1` ကို argument အနေနဲ့ ရယူတယ်။  
🔹 Function ကို argument (name) နဲ့ ခေါ်နိုင်တယ်။  

---

## **Example.6 
- **Function Return Exit Status**
- 
```bash

#!/bin/bash

check_file() {
    if [ -f "$1" ]; then
        return 0
    else
        return 1
    fi
}

check_file "/etc/passwd"
if [ $? -eq 0 ]; then
    echo "File exists!"
else
    echo "File not found!"
fi


```

🔹 Function က `$1` parameter ထဲမှာ File path ရယူတယ်။  
🔹 File ရှိမရှိ စစ်ပြီး `return 0` (Success) / `return 1` (Failure) ပြန်ပေးမယ်။  
🔹 `$?` ကို သုံးပြီး Function Return Status ကို စစ်နိုင်တယ်။  

---

## **Example.7**
-  **Function ကို Array Parameter နဲ့ သုံးခြင်း**

  
```bash

#!/bin/bash

print_array() {
    for item in "$@"; do
        echo "Item: $item"
    done
}

arr=("apple" "banana" "cherry")
print_array "${arr[@]}"


```

🔹 `"$@"` သည် function arguments array ကို ကိုယ်စားပြုတယ်။  
🔹 Array ကို function မှာ parameter အနေနဲ့ pass လုပ်နိုင်တယ်။  

---

## **Example.8**
- **Function Recursion (Recursive Function)**  
```bash

#!/bin/bash

countdown() {
    if [ $1 -le 0 ]; then
        echo -e "Time's up!\a"
    else
        echo "$1..."
        sleep 1
        countdown $(( $1 - 1 ))
    fi
}

countdown 5


```


🔹 Function ကို အလိုအလျှောက် ပြန်ခေါ်ပြီး Countdown ပြုလုပ်ပေးမယ်။  
🔹 `countdown 5` ကို Run လိုက်ရင် `5... 4... 3... 2... 1... Time's up!` ဆိုပြီး ပြမယ်။  

---

# **Summary**
✅ Function ကို `function name() {}` နဲ့ သတ်မှတ်နိုင်တယ်။  
✅ Function ထဲမှာ Variable တွေ သတ်မှတ်ပြီး ပြောင်းလဲနိုင်တယ်။  
✅ Function ကို Argument နဲ့ ခေါ်နိုင်တယ် (`$1`, `$2`, ...).  
✅ Function တွေကို Chaining & Recursion လုပ်နိုင်တယ်။  
✅ Function Return Value ကို Variable ထဲ သိမ်းလို့ရတယ်။  
✅ Function Return Exit Status ကို `$?` နဲ့ စစ်နိုင်တယ်။  
✅ Function တွေကို Array, Loop, Conditional Statements တွေနဲ့ ပေါင်းပြီး အသုံးချနိုင်တယ်။  

---


### **🔹 Advanced Bash Function Techniques**

### **Example.9 - Default Parameter Values**
Sometimes, a function might need a default value if no argument is provided.

```bash
#!/bin/bash

greet() {
    name=${1:-"သူငယ်ချင်း"}
    echo "မင်္ဂလာပါ, $name!"
}

greet "ကိုကျော်"
greet
```
🔹 `$1:-"DefaultValue"` သည် `$1` မရှိရင် `"DefaultValue"` ကို အသုံးပြုစေတယ်။  
🔹 `greet` ကို argument မထည့်ပဲ ခေါ်လိုက်ရင် `"သူငယ်ချင်း"` ဆိုပြီး output ပြမယ်။  

---

### **Example.10 - Local Variables in Functions**
By default, variables in Bash are global. But you can use `local` to make them function-specific.

```bash
#!/bin/bash

calculate() {
    local num=5
    echo "Number inside function: $num"
}

calculate
echo "Number outside function: $num"
```
🔹 `local num=5` သည် `num` variable ကို function အတွင်းမှာသာ အသုံးပြုနိုင်အောင် ကာကွယ်တယ်။  
🔹 Function အပြင်မှာ `num` ကို print လုပ်လိုက်ရင် မထွက်ပါဘူး။  

---

### **Example.11 - Function With Named Parameters**
Instead of `$1`, `$2`, we can use named parameters for clarity.

```bash
#!/bin/bash

send_message() {
    local recipient="$1"
    local message="$2"
    echo "📩 Sending message to $recipient: \"$message\""
}

send_message "ကိုကျော်" "မင်္ဂလာပါ! 😊"
```
🔹 `local recipient="$1"` နဲ့ parameter ကို assign လုပ်ထားတာ။  
🔹 `$1`, `$2` တွေထက် သေချာတဲ့ နာမည် သုံးထားလို့ ဖတ်ရလွယ်တယ်။  

---

### **Example.12 - Function With Named Flags (Using getopts)**
For more complex functions, we can use flags like `-n` for name.

```bash
#!/bin/bash

while getopts "n:a:" opt; do
    case "$opt" in
        n) name="$OPTARG" ;;
        a) age="$OPTARG" ;;
    esac
done

echo "👤 Name: $name, Age: $age"
```
🔹 `-n ကိုအမည်၊ -a ကိုအသက်` ဆိုပြီး flag နဲ့ value ခေါ်ထည့်နိုင်တယ်။  
🔹 Example run: `bash script.sh -n "ကိုကျော်" -a 25`  

---

### **Example.13 - Error Handling in Functions**
If an error happens inside a function, you can exit or handle it gracefully.

```bash
#!/bin/bash

check_file() {
    if [ ! -f "$1" ]; then
        echo "❌ Error: File '$1' not found!"
        return 1
    fi
    echo "✔ File '$1' exists."
}

check_file "/etc/passwd"
check_file "/invalid/file/path"
```
🔹 `return 1` ကိုသုံးပြီး error ဖြစ်ခဲ့ရင် function ကို ချက်ချင်းပြန်ထွက်စေတယ်။  
🔹 Output မှာ ❌ Error တော့ပြမယ်၊ ❌ မရှိရင် file ရှိတယ်ဆိုပြီး ပြမယ်။  

---

## **🔹 Summary of Additional Concepts**
✅ Default Parameter Values (`${1:-"Default"}`)  
✅ Local Variables (`local var=value`)  
✅ Named Parameters (`param1="$1" param2="$2"`)  
✅ Using Flags with `getopts` (`-n -a`)  
✅ Error Handling with `return 1`  

ဒီလို techniques တွေသုံးမယ်ဆိုရင် Bash function တွေ ပိုပြီး advanced ဖြစ်လာပါမည်။ 

---
