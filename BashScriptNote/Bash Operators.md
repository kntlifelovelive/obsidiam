
# Bash Operators Cheat Sheet

## 1. Arithmetic Operators (သင်္ချာဆိုင်ရာ Operator)
| Operator | Description |
|----------|-------------|
| `+`      | Addition (ပေါင်း) |
| `-`      | Subtraction (နုတ်) |
| `*`      | Multiplication (မြှောက်) |
| `/`      | Division (စား) |
| `%`      | Modulus (အကြွင်း) |
| `++`     | Increment (တစ်လုံးတိုး) |
| `--`     | Decrement (တစ်လုံးလျော့) |

## 2. Comparison Operators (Integer)
| Operator | Description |
|----------|-------------|
| `-eq`    | Equal (ညီ) |
| `-ne`    | Not equal (မညီ) |
| `-lt`    | Less than (ငယ်) |
| `-le`    | Less than or equal (ငယ်/ညီ) |
| `-gt`    | Greater than (ကြီး) |
| `-ge`    | Greater than or equal (ကြီး/ညီ) |

## 3. String Comparison Operators
| Operator | Description |
|----------|-------------|
| `=`      | Equal (string တူ) |
| `!=`     | Not equal (string မတူ) |
| `-z`     | String length is zero (string) |
| `-n`     | String length is non-zero (string) |
| `<`      | Alphabetically less than (alphabetically) |
| `>`      | Alphabetically greater than (alphabetically) |

## 4. Logical Operators 
| Operator | Description |
|----------|-------------|
| `&&`     | Logical AND (နှစ်ခုစလုံးမှန်) |
| `\|\|`     | Logical OR (တစ်ခုခုမှန်) |
| `!`      | Logical NOT (true ကို false ပြောင်း) |

## 5. File Test Operators 
| Operator | Description |
|----------|-------------|
| `-e`     | File exists (ဖိုင်ရှိ) |
| `-f`     | Regular file exists (ပုံမှန်ဖိုင်ရှိ) |
| `-d`     | Directory exists (directory ရှိ) |
| `-r`     | Read permission exists (ဖတ်ခွင့်ရှိ) |
| `-w`     | Write permission exists (ရေးခွင့်ရှိ) |
| `-x`     | Execute permission exists (လုပ်ဆောင်ခွင့်ရှိ) |

## 6. Assignment Operators 
| Operator | Description |
|----------|-------------|
| `=`      | Assign value (တန်ဖိုးပေး) |
| `+=`     | Add and assign (ပေါင်းပြီးပေး) |
| `-=`     | Subtract and assign (နုတ်ပြီးပေး) |
| `*=`     | Multiply and assign (မြှောက်ပြီးပေး) |
| `/=`     | Divide and assign (စားပြီးပေး) |

## 7. Bitwise Operators (Bit-level Operator)
| Operator | Description |
|----------|-------------|
| `&`      | Bitwise AND |
| `\|`      | Bitwise OR |
| `^`      | Bitwise XOR |
| `<<`     | Left shift |
| `>>`     | Right shift |

## 8. Redirection Operators (Output Redirection)
| Operator | Description |
|----------|-------------|
| `>`      | Redirect output to file (output ကိုဖိုင်ထဲထည့်) |
| `>>`     | Append output to file (output ကို ဖိုင်ထဲမှာ ပေါင်းထည့်) |
| `<`      | Redirect input from file (input ကိုဖိုင်ကထုတ်ယူ) |

## 9. Pipe Operator (Command chaining)
| Operator | Description |
|----------|-------------|
| `\|`      | Pipe output from one command to another (output ကို နောက်တစ်ခုထဲထည့်) |

## 10. Background and Job Control Operators
| Operator | Description |
|----------|-------------|
| `&`      | Run a command in the background |
| `;`      | Separate commands on the same line |
| `&&`     | Run next command if the previous one succeeded |
| `\|\|`     | Run next command if the previous one failed |

---

#  **1. Arithmetic Operators**  
 **Integer (whole numbers) တွေတွက်ပဲ အလုပ်လုပ်တယ်**  

 **Operators & Meaning**  
```bash
+   # Plus (ပေါင်း)
-   # Minus (နှုတ်)
*   # Multiply (မြှောက်)
/   # Divide (စား)
%   # Modulus (အကြွင်း)
**  # Exponentiation (မြှောက်ကိန်း)
```

 **Example.1**  
```bash
#!/bin/bash
a=10
b=3

echo "Addition: $((a + b))"   # 13
echo "Subtraction: $((a - b))" # 7
echo "Multiplication: $((a * b))" # 30
echo "Division: $((a / b))" # 3
echo "Modulus: $((a % b))" # 1
echo "Exponentiation: $((a ** b))" # 1000
```


- **Example: 2. Arithmetic Operators Example with `(( ))`**
```bash
#!/bin/bash

a=10
b=3

echo "Addition: $((a + b))"     # 13
echo "Subtraction: $((a - b))"  # 7
echo "Multiplication: $((a * b))" # 30
echo "Division: $((a / b))"    # 3
echo "Modulus: $((a % b))"     # 1
echo "Exponentiation: $((a ** b))" # 1000
```

---

- **Example: 3. Using `let` Command**
`let` ကိုလည်း Arithmetic Calculation တွေအတွက်သုံးနိုင်ပါတယ်။  
```bash
#!/bin/bash

let x=10
let y=4

let sum=x+y
let diff=x-y
let prod=x*y
let div=x/y
let mod=x%y

echo "Sum: $sum"      # 14
echo "Difference: $diff" # 6
echo "Product: $prod"   # 40
echo "Quotient: $div"   # 2
echo "Remainder: $mod"  # 2
```

---

- **Example: 4. Using `expr` Command**
`expr` က command line မှာ Math တိုင်းတာလို့ရပါတယ်။  
```bash
#!/bin/bash

a=15
b=4

sum=$(expr $a + $b)
diff=$(expr $a - $b)
prod=$(expr $a \* $b)  # '*' ကို '\' escape လုပ်ရမယ်
div=$(expr $a / $b)
mod=$(expr $a % $b)

echo "Sum: $sum"
echo "Difference: $diff"
echo "Product: $prod"
echo "Quotient: $div"
echo "Modulus: $mod"
```

---

- **Example: 5. Using `bc` Command (For Floating Point Calculation)**
Bash မှာ `(( ))`, `let`, `expr` တွေက integer calculation ပဲလုပ်နိုင်တယ်။  
Floating point တွက်ချင်ရင် `bc` (Basic Calculator) ကိုသုံးရမယ်။  

```bash
#!/bin/bash

a=5.5
b=2.2

sum=$(echo "$a + $b" | bc)
diff=$(echo "$a - $b" | bc)
prod=$(echo "$a * $b" | bc)
div=$(echo "scale=2; $a / $b" | bc) # scale=2 ဆိုတာ ဒဿမ ၂လုံးထိ ပြ

echo "Sum: $sum"
echo "Difference: $diff"
echo "Product: $prod"
echo "Division: $div"
```

---

- **Example: 6. Using `awk` for Advanced Calculation**
`awk` ကို floating point တွက်ချင်ရင်လည်း သုံးနိုင်တယ်။  
```bash
#!/bin/bash

a=5.5
b=2.2

awk "BEGIN {print $a + $b}"  # 7.7
awk "BEGIN {print $a - $b}"  # 3.3
awk "BEGIN {print $a * $b}"  # 12.1
awk "BEGIN {print $a / $b}"  # 2.5
```

---

## **Summary**
✅ `(( ))` → Basic integer math  
✅ `let` → Variable-based arithmetic  
✅ `expr` → Command-line math (Integer Only)  
✅ `bc` → Floating point math  
✅ `awk` → Advanced math operations  

Bash Arithmetic Operators Script  

```bash
#!/bin/bash

x=10
y=4

echo "Addition: $((x + y))"
echo "Subtraction: $((x - y))"
echo "Multiplication: $((x * y))"
echo "Division: $((x / y))"
echo "Modulus: $((x % y))"
echo "Exponentiation: $((x ** y))"
```


---

#  **2. Comparison Operators (နှိုင်းယှဉ်ခြင်း)**
 **Number တွေတွက်ပဲ အလုပ်လုပ်တယ်**  

**Operators & Meaning**  
```bash
-eq  # Equal ( == )
-ne  # Not Equal ( != )
-gt  # Greater than ( > )
-lt  # Less than ( < )
-ge  # Greater than or Equal ( >= )
-le  # Less than or Equal ( <= )
```

 **Example**  
```bash
#!/bin/bash
x=15
y=10

if [ $x -gt $y ]; then
    echo "$x is greater than $y"
fi
```
 **Result**: `15 is greater than 10`

---

#  **3. String Operators (စာသားတွေအတွက်)**
**Operators & Meaning**  
```bash
=   # Equal (တူ)
!=  # Not Equal (မတူ)
-z  # Is empty (string ကိုစစ်)
-n  # Is not empty (string ရှိ)
```

**Example**  
```bash
#!/bin/bash
str1="hello"
str2=""

if [ -z "$str2" ]; then
    echo "str2 is empty"
fi

if [ "$str1" != "$str2" ]; then
    echo "Strings are different"
fi
```
**Result**:  
```
str2 is empty  
Strings are different
```

---

#  **4. File Operators (ဖိုင်တွေ အတွက်)**
**Operators & Meaning**  
```bash
-f  # Is regular file (ဖိုင်လား)
-d  # Is directory (ဖိုင်Folderလား)
-e  # Exists (ရှိလား)
-r  # Readable (ဖတ်လို့ရလား)
-w  # Writable (ရေးလို့ရလား)
-x  # Executable (Run လို့ရလား)
```

 **Example**  
```bash
#!/bin/bash
file="/etc/passwd"

if [ -f "$file" ]; then
    echo "$file exists and is a regular file"
fi
```
 **Result**: `/etc/passwd exists and is a regular file`

---

#  **5. Logical Operators (AND, OR, NOT)**
 **Operators & Meaning**  
```bash
&&   # AND (နှစ်ခုစလုံးမှန်မှ TRUE)
||   # OR (တစ်ခုမှန်လျှင် TRUE)
!    # NOT (မမှန်)
```

 **Example**  
```bash
#!/bin/bash
age=25

if [ $age -gt 18 ] && [ $age -lt 30 ]; then
    echo "You are a young adult"
fi
```
 **Result**: `You are a young adult`

Bash script တွင် logical operator များကို condition များကို စစ်ဆေးရန် နှင့် control flow များကို ထိန်းချုပ်ရန် အသုံးပြုပါသည်။ အဓိက logical operator များမှာ အောက်ပါအတိုင်းဖြစ်ပါသည်။

#### 1. **AND Operator (`&&`)**
- AND operator သည် condition နှစ်ခုလုံး true ဖြစ်မှသာ true ပြန်ပေးပါသည်။
- Syntax:
  ```bash
  command1 && command2
  ```
- Example:
  ```bash
  if [ $a -eq 1 ] && [ $b -eq 2 ]; then
      echo "Both conditions are true"
  fi
  ```

####  2. **OR Operator (`||`)**
- OR operator သည် condition တစ်ခုခု true ဖြစ်ရင်ပင် true ပြန်ပေးပါသည်။
- Syntax:
  ```bash
  command1 || command2
  ```
- Example:
  ```bash
  if [ $a -eq 1 ] || [ $b -eq 2 ]; then
      echo "At least one condition is true"
  fi
  ```

#### 3. **NOT Operator (`!`)**
- NOT operator သည် condition ကို ပြောင်းပြန်လှန်ပေးပါသည်။ true ကို false အဖြစ်၊ false ကို true အဖြစ် ပြောင်းပေးပါသည်။
- Syntax:
  ```bash
  ! condition
  ```
- Example:
  ```bash
  if ! [ $a -eq 1 ]; then
      echo "a is not equal to 1"
  fi
  ```

#### 4. **Combining Logical Operators**
- Logical operator များကို ပေါင်းစပ်အသုံးပြုနိုင်ပါသည်။
- Example:
  ```bash
  if [ $a -eq 1 ] && [ $b -eq 2 ] || [ $c -eq 3 ]; then
      echo "Complex condition is true"
  fi
  ```

#### 5. **Double Brackets (`[[ ]])**
- Double brackets ကို အသုံးပြုပြီး logical operator များကို ပိုမိုရှင်းလင်းစွာ ရေးသားနိုင်ပါသည်။
- Example:
  ```bash
  if [[ $a -eq 1 && $b -eq 2 ]]; then
      echo "Both conditions are true"
  fi
  ```

### 6. **Single Brackets (`[ ]`)**
- Single brackets တွင် logical operator များကို `-a` (AND) နှင့် `-o` (OR) အဖြစ် အသုံးပြုနိုင်ပါသည်။
- Example:
  ```bash
  if [ $a -eq 1 -a $b -eq 2 ]; then
      echo "Both conditions are true"
  fi
  ```

#### 7. **Ternary Operator (Conditional Operator)**
- Bash တွင် ternary operator မရှိသော်လည်း အောက်ပါအတိုင်း အသုံးပြုနိုင်ပါသည်။
- Example:
  ```bash
  [ $a -eq 1 ] && echo "a is 1" || echo "a is not 1"
  ```

#### 8. **Case Statements**
- Case statements တွင် logical operator များကို အသုံးပြုနိုင်ပါသည်။
- Example:
  ```bash
  case $a in
      1|2) echo "a is 1 or 2" ;;
      *) echo "a is neither 1 nor 2" ;;
  esac
  ```

#### 9. **Arithmetic Comparison**
- Arithmetic comparison တွင် logical operator များကို အသုံးပြုနိုင်ပါသည်။
- Example:
  ```bash
  if (( a == 1 && b == 2 )); then
      echo "Both conditions are true"
  fi
  ```

#### 10. **Short-circuit Evaluation**
- Logical operator များသည် short-circuit evaluation ကို အသုံးပြုပါသည်။
- Example:
  ```bash
  [ $a -eq 1 ] && [ $b -eq 2 ] && echo "Both conditions are true"
  ```

ဤ logical operator များကို အသုံးပြုပြီး Bash script များတွင် condition များကို ထိရောက်စွာ စစ်ဆေးနိုင်ပါသည်။


---

**logical operator table**

| **Operator** | **အဓိပ္ပာယ်**                     | **Syntax**                     | **Example**                                   |
|--------------|----------------------------------|--------------------------------|-----------------------------------------------|
| `&&`         | AND (နှစ်ခုလုံး true ဖြစ်မှ true)   | `command1 && command2`         | `[ $a -eq 1 ] && [ $b -eq 2 ]`               |
| `\|\|`       | OR (တစ်ခုခု true ဖြစ်ရင် true)     | `command1 \|\| command2`       | `[ $a -eq 1 ] \|\| [ $b -eq 2 ]`             |
| `!`          | NOT (ပြောင်းပြန်လှန်ပေးသည်)       | `! condition`                  | `! [ $a -eq 1 ]`                             |
| `-a`         | AND (Single brackets တွင်)       | `[ condition1 -a condition2 ]` | `[ $a -eq 1 -a $b -eq 2 ]`                   |
| `-o`         | OR (Single brackets တွင်)        | `[ condition1 -o condition2 ]` | `[ $a -eq 1 -o $b -eq 2 ]`                   |
| `[[ && ]]`   | AND (Double brackets တွင်)       | `[[ condition1 && condition2 ]]` | `[[ $a -eq 1 && $b -eq 2 ]]`               |
| `[[ \|\| ]]` | OR (Double brackets တွင်)        | `[[ condition1 \|\| condition2 ]]` | `[[ $a -eq 1 \|\| $b -eq 2 ]]`             |
| `(( && ))`   | AND (Arithmetic comparison တွင်) | `(( a == 1 && b == 2 ))`       | `if (( a == 1 && b == 2 )); then ... fi`     |
| `(( \|\| ))` | OR (Arithmetic comparison တွင်)  | `(( a == 1 \|\| b == 2 ))`     | `if (( a == 1 \|\| b == 2 )); then ... fi`   |

#### Explaine:
1. **`&&`**  
   - နှစ်ခုလုံး true ဖြစ်မှ true ပြန်ပေးသည်။  
   - Example:  
     ```bash
     [ $a -eq 1 ] && [ $b -eq 2 ]
     ```

2. **`||`**  
   - တစ်ခုခု true ဖြစ်ရင် true ပြန်ပေးသည်။  
   - Example:  
     ```bash
     [ $a -eq 1 ] || [ $b -eq 2 ]
     ```

3. **`!`**  
   - Condition ကို ပြောင်းပြန်လှန်ပေးသည်။  
   - Example:  
     ```bash
     ! [ $a -eq 1 ]
     ```

4. **`-a`**  
   - Single brackets တွင် AND operator အဖြစ်အသုံးပြုသည်။  
   - Example:  
     ```bash
     [ $a -eq 1 -a $b -eq 2 ]
     ```

5. **`-o`**  
   - Single brackets တွင် OR operator အဖြစ်အသုံးပြုသည်။  
   - Example:  
     ```bash
     [ $a -eq 1 -o $b -eq 2 ]
     ```

6. **`[[ && ]]`**  
   - Double brackets တွင် AND operator အဖြစ်အသုံးပြုသည်။  
   - Example:  
     ```bash
     [[ $a -eq 1 && $b -eq 2 ]]
     ```

7. **`[[ || ]]`**  
   - Double brackets တွင် OR operator အဖြစ်အသုံးပြုသည်။  
   - Example:  
     ```bash
     [[ $a -eq 1 || $b -eq 2 ]]
     ```

8. **`(( && ))`**  
   - Arithmetic comparison တွင် AND operator အဖြစ်အသုံးပြုသည်။  
   - Example:  
     ```bash
     if (( a == 1 && b == 2 )); then ... fi
     ```

9. **`(( || ))`**  
   - Arithmetic comparison တွင် OR operator အဖြစ်အသုံးပြုသည်။  
   - Example:  
     ```bash
     if (( a == 1 || b == 2 )); then ... fi
     ```

**Logical operator end**

---


#  **6. Assignment Operators (သတ်မှတ်ခြင်း)**
**Operators & Meaning**  
```bash
=   # Assign (ပေးလိုက်သည်)
+=  # Increment (တိုး)
-=  # Decrement (လျှော့)
*=  # Multiply & Assign
/=  # Divide & Assign
%=  # Modulus & Assign
```

 **Example**  
```bash
#!/bin/bash
num=5
num=$((num + 3))  # num += 3 လည်းသုံးလို့ရတယ်

echo "New Value: $num"
```
**Result**: `New Value: 8`

---

#  **7. Bitwise Operators (Binary အတွက်)**
 **Operators & Meaning**  
```bash
&   # AND
|   # OR
^   # XOR
~   # Complement
<<  # Left Shift
>>  # Right Shift
```

 **Example**  
```bash
#!/bin/bash
a=5  # 0101 in binary
b=3  # 0011 in binary

echo "Bitwise AND: $((a & b))" # 1 (0001)
echo "Bitwise OR: $((a | b))"  # 7 (0111)
echo "Bitwise XOR: $((a ^ b))" # 6 (0110)
```

**Result**:
```
Bitwise AND: 1  
Bitwise OR: 7  
Bitwise XOR: 6  
```

---

# ** Summary**
| Operator Type | Operators |
|--------------|-----------|
| Arithmetic | `+ - * / % **` |
| Comparison | `-eq -ne -gt -lt -ge -le` |
| String | `= != -z -n` |
| File | `-f -d -e -r -w -x` |
| Logical | `&& || !` |
| Assignment | `= += -= *= /= %=` |
| Bitwise | `& \| ^ ~ << >>` |

---

### **Bash Operators - Summary Table with Descriptions** 

| **Operator Type**  | **Operators** | **Description** (အသုံးပြုပုံ) |
|--------------------|--------------|-------------------------------|
| **Arithmetic Operators** (ဂဏန်းတွက်ခြင်း) | `+` | **Addition** (ပေါင်းခြင်း) |
| | `-` | **Subtraction** (နှုတ်ခြင်း) |
| | `*` | **Multiplication** (မြှောက်ခြင်း) |
| | `/` | **Division** (စားခြင်း) |
| | `%` | **Modulus** (အကြွင်းကျန်တွက်ခြင်း) |
| | `**` | **Exponentiation** (မြှောက်ကိန်း) |
| **Comparison Operators** (နှိုင်းယှဉ်ခြင်း) | `-eq` | **Equal to** (တူခြင်း) |
| | `-ne` | **Not equal to** (မတူခြင်း) |
| | `-gt` | **Greater than** (ကြီးခြင်း) |
| | `-lt` | **Less than** (ငယ်ခြင်း) |
| | `-ge` | **Greater than or equal to** (ကြီး သို့မဟုတ် တူခြင်း) |
| | `-le` | **Less than or equal to** (ငယ် သို့မဟုတ် တူခြင်း) |
| **String Operators** (စာသားတွေအတွက်) | `=` | **Equal** (တူခြင်း) |
| | `!=` | **Not equal** (မတူခြင်း) |
| | `-z` | **Is empty?** (စာသားမရှိခြင်း) |
| | `-n` | **Is not empty?** (စာသားရှိခြင်း) |
| **File Operators** (ဖိုင်စစ်ခြင်း) | `-f` | **Is regular file?** (ဖိုင်လား?) |
| | `-d` | **Is directory?** (Folderလား?) |
| | `-e` | **Exists?** (ရှိလား?) |
| | `-r` | **Readable?** (ဖတ်လို့ရလား?) |
| | `-w` | **Writable?** (ရေးလို့ရလား?) |
| | `-x` | **Executable?** (Run လို့ရလား?) |
| **Logical Operators** (AND, OR, NOT) | `&&` | **Logical AND** (နှစ်ခုမှန်မှ TRUE) |
| | `\|\|` | **Logical OR** (တစ်ခုမှန်လျှင် TRUE) |
| | `!` | **Logical NOT** (မမှန်) |
| **Assignment Operators** (တန်ဖိုးသတ်မှတ်ခြင်း) | `=` | **Assign** (တန်ဖိုးသတ်မှတ်ခြင်း) |
| | `+=` | **Increment and assign** (တိုးပြီး သတ်မှတ်ခြင်း) |
| | `-=` | **Decrement and assign** (လျှော့ပြီး သတ်မှတ်ခြင်း) |
| | `*=` | **Multiply and assign** (မြှောက်ပြီး သတ်မှတ်ခြင်း) |
| | `/=` | **Divide and assign** (စားပြီး သတ်မှတ်ခြင်း) |
| | `%=` | **Modulus and assign** (အကြွင်းကျန်တွက်ပြီး သတ်မှတ်ခြင်း) |
| **Bitwise Operators** (Binary တွေအတွက်) | `&` | **Bitwise AND** (၂ ခုလုံး ၁ ဖြစ်မှ ၁) |
| | `\|` | **Bitwise OR** (တစ်ခုခု ၁ ဖြစ်လျှင် ၁) |
| | `^` | **Bitwise XOR** (၂ ခုတူရင် ၀, မတူရင် ၁) |
| | `~` | **Bitwise Complement** (၀ ကို ၁ ပြောင်း, ၁ ကို ၀ ပြောင်း) |
| | `<<` | **Left Shift** (ဘယ်ဘက်သို့ ချောင်းခြင်း) |
| | `>>` | **Right Shift** (ညာဘက်သို့ ချောင်းခြင်း) |

---

### **တစ်ခုပိုမိုသိထားသင့်တာ**  
- **Arithmetic Operators** ကို `$(())` ဖြင့် သုံးရမယ်  
- **Comparison Operators** ကို `[ ]` သို့မဟုတ် `[[ ]]` ဖြင့် သုံးရမယ်  
- **String Operators** ကို `[ ]` သို့မဟုတ် `[[ ]]` ဖြင့် သုံးလို့ရတယ်  
- **File Operators** ကို `[ ]` သုံးရမယ်  
- **Logical Operators** ကို `[ ]` သို့မဟုတ် `[[ ]]` ဖြင့် သုံးလို့ရတယ်။

---

### **ဖြည့်စွက်အကြောင်းအရာများ**

#### 1. **Command Substitution Operators (Command အထွက်ကို Variable အဖြစ်သိမ်းခြင်း)**
| Operator | Description |
|----------|-------------|
| `` ` ``  | Backticks ဖြင့် Command Substitution (အဟောင်း) |
| `$()`    | Modern Command Substitution (အသစ်၊ ပိုမိုရှင်းလင်း) |

**ဥပမာ:**
```bash
current_date=`date`    # Backticks နည်း
current_date=$(date)   # $() နည်း
```

---

#### 2. **Pattern Matching Operators (စာသားပုံစံကိုက်ညှိခြင်း)**
- `[[ ]]` အတွင်းတွင် `==` နှင့် `!=` ဖြင့် Wildcard (`*`, `?`) များကို အသုံးပြုနိုင်သည်။  

**ဥပမာ:**
```bash
if [[ "hello" == h* ]]; then
    echo "Starts with 'h'"
fi
```

---

#### 3. **Array Operators (ဒေတာအစုများအတွက်)**
| Operator | Description |
|----------|-------------|
| `${array[@]}` | Array အားလုံးကို ရည်ညွှန်း |
| `${#array[@]}` | Array ထဲရှိ အရေအတွက် |
| `${array[index]}` | Specific index ကို ရည်ညွှန်း |

**ဥပမာ:**
```bash
fruits=("apple" "banana" "cherry")
echo "Total fruits: ${#fruits[@]}"  # 3
echo "First fruit: ${fruits[0]}"    # apple
```

---

#### 4. **Process Substitution Operators (Command များကို File အဖြစ်အသုံးပြုခြင်း)**
| Operator | Description |
|----------|-------------|
| `<(` *command* `)` | Command output ကို File ကဲ့သို့ဖတ်ရန် |
| `>(` *command* `)` | Command input ကို File ကဲ့သို့ရေးရန် |

**ဥပမာ:**
```bash
diff <(ls dir1) <(ls dir2)   # dir1 နှင့် dir2 ဖိုင်စာရင်းကို နှိုင်းယှဉ်ခြင်း
```

---

#### 5. **Here Documents & Here Strings (Multi-line Input ပေးခြင်း)**
| Operator | Description |
|----------|-------------|
| `<<`     | Here Document (အသုံးပြုသူ input ကို command သို့ပို့) |
| `<<<`    | Here String (String တစ်ခုကို command သို့ပို့) |

**ဥပမာ:**
```bash
# Here Document
cat << EOF
Hello, this is a
multi-line text.
EOF

# Here String
grep "apple" <<< "apple banana cherry"
```

---

### **အပြည့်စုံဆုံး Operator ဇယား (ဖြည့်စွက်ချက်နှင့်အတူ)**

| **Operator Type**       | **Operators**                         | **Description**                                                                 |
|-------------------------|---------------------------------------|---------------------------------------------------------------------------------|
| **Command Substitution**| `` ` ``, `$()`                        | Command ရဲ့ output ကို variable အနေနဲ့ သိမ်းခြင်း                               |
| **Pattern Matching**    | `==`, `!=` (with `[[ ]]`)             | Wildcard (`*`, `?`) များဖြင့် စာသားပုံစံကိုက်ညှိခြင်း                             |
| **Array Operations**    | `${array[@]}`, `${#array[@]}`         | Array များကို စီမံခြင်း                                                         |
| **Process Substitution**| `<(` *command* `)`, `>(` *command* `)`| Command များကို File ကဲ့သို့အသုံးပြုခြင်း                                       |
| **Here Docs/Strings**   | `<<`, `<<<`                           | Multi-line input သို့မဟုတ် string input ကို command သို့တိုက်ရိုက်ပို့ခြင်း         |

---

### **အကြံပြုချက်**
- **ဥပမာများထပ်ထည့်ပါ**: အထက်ပါ operator အသစ်တိုင်းအတွက် ရှင်းလင်းသော script ဥပမာများ ထည့်ပေးပါ။
- **Best Practices**: Operator အသုံးပြုရာတွင် သတိထားရမည့် အချက်များ (ဥပမာ: `[[ ]]` ကို ဦးစားပေးသုံးရန်)။
- **Error Handling**: Operator များနှင့်အတူ `set -e` (error exit) နှင့် `set -o pipefail` တို့ကို မည်သို့သုံးမည်ကို ရှင်းပြပါမည်။

---

### **ဖြည့်စွက်ဥပမာများ**

#### 1. **Command Substitution Example**
```bash
# Using backticks
files=`ls`
echo "Files in directory: $files"

# Using $()
files=$(ls)
echo "Files in directory: $files"
```

#### 2. **Pattern Matching Example**
```bash
# Check if a string starts with 'h'
if [[ "hello" == h* ]]; then
    echo "String starts with 'h'"
fi
```

#### 3. **Array Operations Example**
```bash
# Declare an array
fruits=("apple" "banana" "cherry")

# Print all elements
echo "All fruits: ${fruits[@]}"

# Print the number of elements
echo "Number of fruits: ${#fruits[@]}"

# Access specific element
echo "First fruit: ${fruits[0]}"
```

#### 4. **Process Substitution Example**
```bash
# Compare the output of two commands
diff <(ls dir1) <(ls dir2)
```

#### 5. **Here Document & Here String Example**
```bash
# Here Document
cat << EOF
This is a multi-line
text using Here Document.
EOF

# Here String
grep "apple" <<< "apple banana cherry"
```

---

### **Best Practices**
- **`[[ ]]` ကို ဦးစားပေးသုံးပါ**: `[[ ]]` သည် `[ ]` ထက် ပိုမိုစွမ်းဆောင်နိုင်ပြီး ပိုမိုလုံခြုံသည်။
- **Error Handling**: Script တွင် `set -e` နှင့် `set -o pipefail` ကို အသုံးပြုပါ။
  ```bash
  set -e  # Exit immediately if a command exits with a non-zero status
  set -o pipefail  # Ensure that the script fails if any command in a pipeline fails
  ```

---

### **Error Handling Example**
```bash
#!/bin/bash
set -e
set -o pipefail

# Example command that might fail
ls /nonexistent_directory || echo "Directory not found, but script continues"
```

---

