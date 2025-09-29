
### **Bash ရဲ့ String Methods (String Manipulation)**
Bash မှာ String ကို (manipulate) လုပ်ဖို့ အတွက် method တွေအများကြီးရှိတယ်။ အောက်မှာ အသုံးများတဲ့ String manipulation techniques တွေကို example နဲ့ ရှင်းပြပေးမယ်။

---

## **1. String Length**
```bash
str="Hello World"
echo "Length: ${#str}"
```
🔹 **Output:** `Length: 11`

---

## **2. String Slicing (Substring)**
**Syntax:**  
```bash
${string:start:length}
```
**Example:**
```bash
str="Hello World"
echo "${str:0:5}"   # "Hello"
echo "${str:6:5}"   # "World"
```

---

## **3. String Replace (Substitution)**
**Single occurrence replace:**  
```bash
str="Hello World"
echo "${str/World/Bash}"
```
🔹 **Output:** `Hello Bash`

**All occurrences replace:**  
```bash
str="apple apple apple"
echo "${str//apple/orange}"
```
🔹 **Output:** `orange orange orange`

---

## **4. Remove Prefix & Suffix**
**Remove prefix (`#`):**
```bash
str="prefix_hello"
echo "${str#prefix_}"   # "hello"
```

**Remove suffix (`%`):**
```bash
str="hello_suffix"
echo "${str%suffix}"    # "hello_"
```

---

## **5. Convert to Uppercase & Lowercase**

###  **Bash & Zsh: Uppercase / Lowercase Conversion**

#### a. **Using `${}` String Substitution in Bash & Zsh**

**Uppercase Conversion**
```bash
str="hello"
echo "${str^^}"   # Uppercase: HELLO
```

**Lowercase Conversion**
```bash
str="HELLO"
echo "${str,,}"   # Lowercase: hello
```

- **`^^`**: Uppercase conversion (Bash & Not to Zsh)
- **`,,`**: Lowercase conversion (Bash & Not to  Zsh)

####  **Using `tr` Command in Bash & Zsh**

**Uppercase Conversion with `tr`**
```bash
echo "hello" | tr 'a-z' 'A-Z'   # Uppercase: HELLO
```

**Lowercase Conversion with `tr`**
```bash
echo "HELLO" | tr 'A-Z' 'a-z'   # Lowercase: hello
```

- `tr 'a-z' 'A-Z'` : Lowercase to Uppercase conversion
- `tr 'A-Z' 'a-z'` : Uppercase to Lowercase conversion

####  **Using `awk` Command in Bash & Zsh**

**Uppercase Conversion with `awk`**
```bash
echo "hello" | awk '{print toupper($0)}'  # Uppercase: HELLO
```

**Lowercase Conversion with `awk`**
```bash
echo "HELLO" | awk '{print tolower($0)}'  # Lowercase: hello
```

- **`toupper()`**: Converts to uppercase
- **`tolower()`**: Converts to lowercase

### **Summary**:  

| **Method** | **Uppercase** | **Lowercase** |
|------------|---------------|---------------|
| **Bash/Zsh `${}`** | `${str^^}` | `${str,,}` |
| **`tr` Command** | `tr 'a-z' 'A-Z'` | `tr 'A-Z' 'a-z'` |
| **`awk` Command** | `awk '{print toupper($0)}'` | `awk '{print tolower($0)}'` |

### **Note**:
- **Bash/Zsh `${}` Substitution**: This method works **directly** for variable manipulation and is **clean**.
- **`tr` Command**: This command is used for **character-by-character** transformation and is **easy** for a quick conversion.
- **`awk` Command**: `awk` is often used for **processing text** and is ideal for complex text transformations with the ability to work on specific fields.


---

## **6. Check if String Contains Substring**
```bash
str="Hello Bash"
if [[ "$str" == *"Bash"* ]]; then
    echo "Contains Bash"
else
    echo "Does not contain Bash"
fi
```
🔹 **Output:** `Contains Bash`

---

## **7. Concatenating Functions Inside `echo`**
Bash မှာ function return values ကို `echo` ထဲမှာ concatenate လုပ်ချင်ရင် `$(function_name)` သုံးရမယ်။  
**Example:**  
```bash
greet() {
    echo "Hello"
}

name="Kyaw"
echo "$(greet), $name!"
```
🔹 **Output:** `Hello, Kyaw!`

---
### **Bash String Methods Table**  

| **Method**            | **Syntax**                     | **Example**                         | **Output**                 | **Note**                                      |
|----------------------|-----------------------------|---------------------------------|-------------------------|-------------------------------------------|
| **String Length**    | `${#str}`                   | `str="Hello"`<br>`echo ${#str}` | `5`                     | String length ကိုတွက်နိုင်မယ် |
| **Substring**        | `${str:start:length}`        | `str="Hello World"`<br>`echo ${str:0:5}` | `Hello`                 | Substring ကိုထုတ်ယူနိုင်မယ် |
| **Replace (First Occurrence)** | `${str/old/new}` | `str="Hello World"`<br>`echo ${str/World/Bash}` | `Hello Bash` | First occurrence ကိုပဲ ပြောင်းမယ် |
| **Replace (All Occurrences)** | `${str//old/new}` | `str="apple apple"`<br>`echo ${str//apple/orange}` | `orange orange` | တစ်ခုလုံးကို ပြောင်းမယ် |
| **Remove Prefix**    | `${str#prefix_}`            | `str="prefix_text"`<br>`echo ${str#prefix_}` | `text`                  | Prefix ကိုဖယ်ရှားမယ် |
| **Remove Suffix**    | `${str%suffix}`             | `str="text_suffix"`<br>`echo ${str%suffix}` | `text_`                  | Suffix ကိုဖယ်ရှားမယ် |
| **Lowercase**        | `${str,,}`                  | `str="HELLO"`<br>`echo ${str,,}` | `hello`                  | Lowercase ပြောင်းမယ် |
| **Uppercase**        | `${str^^}`                  | `str="hello"`<br>`echo ${str^^}` | `HELLO`                  | Uppercase ပြောင်းမယ် |
| **Check Substring**  | `[[ $str == *sub* ]]`       | `str="Hello Bash"`<br>`if [[ "$str" == *"Bash"* ]]; then echo "Yes"; fi` | `Yes` | String ထဲမှာ ပါမပါ စစ်နိုင်မယ် |
| **Concatenate Function in Echo** | `$(func_name)` | `greet() { echo "Hi"; }`<br>`echo "$(greet), User!"` | `Hi, User!` | Function return value ကို String ထဲမှာ ချိတ်မယ် |

---

### **Zsh မှာ `read` Command Syntax & Usage**  

`read` command ကို **user input ကို variable ထဲသိမ်းဖို့** သုံးပါတယ်။  

---

### **📌 1. Basic Syntax**  
```zsh
read "variable_name?Prompt message: "
```
🔹 **`variable_name`** → Input ကို သိမ်းမယ့် variable  
🔹 **`Prompt message`** → User ကို ပြသမယ့် စာသား  

---

### **📌 2. Example Usage**  

```zsh
#!/bin/zsh

read "UserName?Enter Your Name: "
echo "Hello, $UserName!"
```
**🟢 Output:**  
```
Enter Your Name: Kyaw
Hello, Kyaw!
```

---

### **📌 3. Multiple Inputs**
User input ကို တစ်ချိန်တည်းမှာ Variables များစွာထဲ သိမ်းနိုင်ပါတယ်။  

```zsh
read "firstName?Enter First Name: " "lastName?Enter Last Name: "
echo "Your full name is $firstName $lastName."

# adding method discover 
# multiple input method for read:

read  "UserName?Enter your username: " ; read -s "UserPass?Enter your Password: "


```
**🟢 Output:**  
```
Enter First Name: Kyaw
Enter Last Name: Soe
Your full name is Kyaw Soe.
```

---

### **📌 4. Input ကို Default Value သတ်မှတ်ခြင်း**  
User က input မထည့်ရင် **default value** ပါလာစေချင်ရင် 👇  
```zsh
default_name="Guest"
read "UserName?Enter Your Name ($default_name): "
UserName=${UserName:-$default_name}
echo "Hello, $UserName!"
```
**🟢 Output (User didn't enter anything):**  
```
Enter Your Name (Guest): 
Hello, Guest!
```

---

### **📌 5. Input ကို Hidden (Password Input)**
```zsh
read -s "password?Enter Your Password: "
echo "Password Saved!"
```
**🔒 Password Input မှာ အကြည့်မပေါ်ဘူး။**  

---

### **📌 6. Time Limit (Auto-cancel after timeout)**
```zsh
read -t 5 "UserName?Enter Your Name (5s Timeout): "
echo "You entered: $UserName"
```
**⏳ 5 sec မှာ input မထည့်ရင် empty ဖြစ်သွားမယ်။**

---

### **📌 7. Confirmation Prompt**
```zsh
read "confirm?Are you sure? (y/n): "
if [[ $confirm == "y" ]]; then
  echo "Confirmed!"
else
  echo "Cancelled!"
fi
```

---

### **Bash vs Zsh Read Command Differences**  

Bash မှာသုံးလို့ရတဲ့ `read -p` ကို **Zsh မှာမသုံးနိုင်ပါဘူး**။  
ဒါကြောင့် **Zsh-specific syntax** ကိုသုံးဖို့လိုပါတယ်။  

---

### ✅ **Bash-Compatible Syntax**  
```bash
read -p "Enter Your Name: " UserName
echo "Hello, $UserName!"
```
📌 **Bash မှာ `-p` ကို prompt ပြဖို့သုံးတယ်။**  
📌 **Zsh မှာတော့ ဒီ syntax အလုပ်မလုပ်ပါဘူး။**

---

### ✅ **Zsh-Compatible Syntax**  
```zsh
read "UserName?Enter Your Name: "
echo "Hello, $UserName!"
```
📌 **Zsh မှာ `?` ကို prompt ပြဖို့သုံးရတယ်။**  
📌 **`read "variable_name?Prompt message: "` ဆိုတဲ့ format ကိုသုံးရမယ်။**  

---

### 🔥 **Key Differences**  
| Feature        | Bash (`read -p`) | Zsh (`read "var?Prompt"`) |
|--------------|----------------|------------------|
| Prompt Syntax | `read -p "Prompt: " var` | `read "var?Prompt: "` |
| Compatibility | Bash Only | Zsh Only |
| Works in Scripts? | ✅ Yes | ✅ Yes |

---

 **Conclusion**  
- Bash မှာ `read -p` သုံးရမယ်။  
- Zsh မှာ `read "variable?Prompt: "` သုံးရမယ်။  
- **Zsh မှာ `read -p` အလုပ်မလုပ်ဘူး**!  

---

