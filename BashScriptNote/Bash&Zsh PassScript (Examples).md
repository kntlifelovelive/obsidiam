
`Username` နဲ့ `Password` စစ်တဲ့ **Bash** script ကို အောက်မှာ လေး examples ဖြင့် ဖော်ပြပါမယ်။

### 1. **Simple Username and Password Validation**  
ဒီ script မှာ user က username နဲ့ password ကိုရိုက်ထည့်ပြီး၊ သူ့ကိုသတ်မှတ်ထားတဲ့ username နဲ့ password နဲ့ တူရင် access ပေးပြီး၊ မတူရင် error message ပေးပါမယ်။

#### **Example**:
```bash
#!/bin/bash

# Define correct username and password
correct_username="admin"
correct_password="password123"

# Ask for username
echo -n "Enter username: "
read username

# Ask for password
echo -n "Enter password: "
read -s password  # -s option hides the password input

# Validate the username and password
if [ "$username" == "$correct_username" ] && [ "$password" == "$correct_password" ]; then
    echo -e "\nLogin successful!"
else
    echo -e "\nLogin failed! Incorrect username or password."
fi
```

**Explanation**:
- `read -s password`: password ကို မမြင်နိုင်ဘဲရိုက်ထည့်နိုင်အောင် `-s` option ကို သုံးထားပါသည်။
- တူလားမတူလား စစ်ပြီး result ပေးပါတယ်။

### 2. **Username and Password Validation with a Loop (Retry Limit)**  
ဒီ script မှာ username နဲ့ password မမှန်ရင် loop ဖြင့် အသစ်ထပ်ထည့်စရာပေးပြီး, အသေးစိတ် error message နဲ့ ထပ်မံသတိပေးပါတယ်။

#### **Example**:
```bash
#!/bin/bash

# Define correct username and password
correct_username="admin"
correct_password="password123"

# Set the maximum number of attempts
max_attempts=3
attempt=1

# Loop for username and password verification
while [ $attempt -le $max_attempts ]
do
    echo -n "Enter username: "
    read username

    echo -n "Enter password: "
    read -s password

    if [ "$username" == "$correct_username" ] && [ "$password" == "$correct_password" ]; then
        echo -e "\nLogin successful!"
        break
    else
        echo -e "\nIncorrect username or password. Attempt $attempt of $max_attempts."
    fi

    ((attempt++))  # Increment the attempt counter
done

if [ $attempt -gt $max_attempts ]; then
    echo "Maximum attempts reached. Access denied."
fi
```

**Explanation**:
- `max_attempts` ဆိုတာ ထပ်လုပ်ရမယ့်အခါများအတွက် limit တစ်ခုဖြစ်ပါသည်။
- တချို့သောလူသားများအတွက် password ကို မမှန်ရင် max attempts မရောက်မီ ထပ်လုပ်ရမယ်။

### 3. **Username and Password from a File**  
ဒီ script မှာ password နှင့် username ကို file မှာထားပြီး စစ်ဆေးပါတယ်။ ယူထားတဲ့ file အတိုင်း username နဲ့ password ကို verify လုပ်ပေးပါမယ်။

#### **Example**:
```bash
#!/bin/bash

# Define the file containing valid credentials
credentials_file="credentials.txt"

# Read username and password from file
correct_username=$(awk 'NR==1 {print $1}' $credentials_file)
correct_password=$(awk 'NR==1 {print $2}' $credentials_file)

# Ask for username
echo -n "Enter username: "
read username

# Ask for password
echo -n "Enter password: "
read -s password

# Validate the username and password
if [ "$username" == "$correct_username" ] && [ "$password" == "$correct_password" ]; then
    echo -e "\nLogin successful!"
else
    echo -e "\nLogin failed! Incorrect username or password."
fi
```

**Explanation**:
- `credentials.txt` file ထဲမှာ `username password` တွေအတူတူရှိသင့်ပါတယ် (example: `admin password123`)။
- `awk` က `credentials.txt` file ထဲကနေ username နဲ့ password ကို ခွဲထုတ်ပေးပါတယ်။

### 4. **Case Insensitive Username and Password Check**  
ဒီ script မှာ username နဲ့ password ကို case-insensitive ရေးစစ်ပါမယ်။

#### **Example**:
```bash
#!/bin/bash

# Define correct username and password
correct_username="Admin"
correct_password="Password123"

# Ask for username
echo -n "Enter username: "
read username

# Ask for password
echo -n "Enter password: "
read -s password

# Validate the username and password (case insensitive)
if [ "${username,,}" == "${correct_username,,}" ] && [ "${password,,}" == "${correct_password,,}" ]; then
    echo -e "\nLogin successful!"
else
    echo -e "\nLogin failed! Incorrect username or password."
fi
```

**Explanation**:
- `${username,,}` သည် username ကို lowercase သို့ ပြောင်းခြင်းဖြစ်ပြီး၊ case insensitive comparison ကို စစ်ဆေးနိုင်သည်။
- password ကိုလည်း တူညီသောနည်းဖြင့် compare လုပ်ပါသည်။

### Summary:
- **Simple username/password check**: User တင်သည့် credentials ကို တိုက်ရိုက်စစ်ထုတ်ပါ။
- **Retry limit with a loop**: Multiple attempts ကို handle လုပ်ပါ။
- **Username/password from a file**: file ထဲမှ credentials ကိုသုံးပါ။
- **Case insensitive check**: username/password ကို case-insensitive အဖြစ် check ပြုလုပ်ပါ။ 

---

---

## **❌ အမှား**
```zsh
if [ "$UserName" == "$correctUserName" ] && [ "$UserPass" == "$correctUserPass" ]; then
```
### **ဘာလို့ မှားလဲ?**
1. `[ ... ]` သည် **POSIX-compliant test command** ဖြစ်ပြီး `==` သုံးလို့မရဘူး။  
   - `==` ဟာ **`[[ ... ]]` ထဲမှာပဲ သုံးလို့ရ**။  
   - **ဖြေရှင်းနည်း** → `=` သုံးရမယ်။  

2. **AND condition (`&&`) ကို မှားသုံးထားတာ**  
   - `[ ... ] && [ ... ]` ဆိုတဲ့ format ကိုသုံးရမယ်။  
   - တစ်ခုပဲ bracket ထဲမှာ သုံးရင် အလုပ်မလုပ်ဘူး။  

---

## ✅ **အမှန်**
### **နည်း (1) - `[ ... ]` သုံးချင်ရင်**  
```zsh
if [ "$UserName" = "$correctUserName" ] && [ "$UserPass" = "$correctUserPass" ]; then
```
🔹 `[ ... ]` သုံးတဲ့အခါ `=` သာ သုံးရမယ်။  
🔹 `&&` ကို bracket နှစ်ခုလုံးမှာ သုံးရမယ်။  

---

### **နည်း (2) - `[[ ... ]]` သုံးရင်**  
```zsh
if [[ "$UserName" == "$correctUserName" && "$UserPass" == "$correctUserPass" ]]; then
```
🔹 `[[ ... ]]` သုံးလျှင် `==` ကို သုံးလို့ရတယ်။  
🔹 `&&` ကို တစ်ခုပဲ bracket ထဲမှာပဲ သုံးလို့ရတယ်။  
💡 **Zsh, Bash မှာ `[[ ... ]]` သုံးရင် ပိုကောင်းတယ်။**

---

### **🔥 Full Script (မှန်ကန်သော)**  
```zsh
#!/bin/zsh 

correctUserName="admin"
correctUserPass="123"

# simple method userinput read :

# read "UserName?Enter your username: " 
# read -s "UserPass?Enter your Password: " 

# Multiple method userinput read :
read  "UserName?Enter your username: " ; read -s "UserPass?Enter your Password: "
# read -s ==> option is hidden password: 

# if [[ "$UserName" == "$correctUserName" && "$UserPass" == "$correctUserPass" ]]; then
#     echo "\nLogin successful!"
# else
#     echo "\nLogin failed! Incorrect username or password."
# fi


if [ "$UserName" = "$correctUserName" ] && [ "$UserPass" = "$correctUserPass" ]; then
  echo "\nLogin successful"
else
  echo "\nnLogin failed "
fi 

```

---

