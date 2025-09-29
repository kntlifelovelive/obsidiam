
# <span style="color: lightgreen;">Bash Array Details</span>



Bash Script တွင် Array များကို အသုံးပြုနည်းကို အဆင့်ဆင့်ရှင်းပြပေးပါမယ်။

### 1. **Array အမျိုးအစားများ**
- **Indexed Array** - Normal Array (index number)
- **Associative Array** - Key-Value pairs (Bash 4.0+ တွင်သာ ပံ့ပိုး)

---

### 2. **Array ဖန်တီးခြင်း**

#### a. Indexed Array
```bash
# နည်းလမ်း ၁ - တန်ဖိုးများတစ်ခါတည်းထည့်
fruits=("Apple" "Banana" "Orange")

# နည်းလမ်း ၂ - အညွှန်းဖြင့် တစ်ခုချင်းသတ်မှတ်
fruits[0]="Apple"
fruits[1]="Banana"
fruits[2]="Orange"

# နည်းလမ်း ၃ - စာကြောင်းမှဖတ်ပြီးထည့်
read -a fruits <<< "Apple Banana Orange"
```

#### b. Associative Array (Bash 4.0+)
```bash
declare -A user  # ကြေငြာရန် လိုအပ်
user=(
  [name]="John"
  [age]=30
  [email]="john@example.com"
)
```

---

### 3. **Array တန်ဖိုးများကို ဖတ်ခြင်း**

#### a. တစ်ခုချင်းဖတ်ရန်
```bash
echo "First fruit: ${fruits[0]}"  # Apple
echo "All fruits: ${fruits[@]}"   # Apple Banana Orange
```

#### b. Index အားလုံးကိုဖတ်ရန်
```bash
echo "Indexes: ${!fruits[@]}"     # 0 1 2
```

#### c. Array အရှည်
```bash
echo "Total fruits: ${#fruits[@]}"  # 3
```

---

### 4. **Array ကို Update လုပ်ခြင်း**

#### a. တန်ဖိုးထပ်ထည့်ခြင်း
```bash
fruits+=("Mango")            # အဆုံးတွင် ထည့်ခြင်း
fruits[3]="Grapes"           # အညွှန်းဖြင့် ထည့်ခြင်း
```

#### b. တန်ဖိုးဖျက်ခြင်း
```bash
unset fruits[1]              # Banana ကိုဖျက် (Index 1 ပျယ်)
```

---

### 5. **Array ကို Loop ပတ်ခြင်း**

#### a. တန်ဖိုးများဖြင့် Loop
```bash
for fruit in "${fruits[@]}"; do
  echo "Fruit: $fruit"
done
```

#### b. Index များဖြင့် Loop
```bash
for index in "${!fruits[@]}"; do
  echo "Index $index: ${fruits[$index]}"
done
```

---

### 6. **Associative Array နမူနာ**
```bash
declare -A user
user[name]="Alice"
user[age]=25
user[email]="alice@example.com"

# Key များဖြင့် Loop
for key in "${!user[@]}"; do
  echo "$key: ${user[$key]}"
done
```

---

### 7. **အထူးနည်းလမ်းများ**

#### a. Array Slice
```bash
echo "${fruits[@]:1:2}"  # Index 1 မှစပြီး 2 ခု (Banana Orange)
```

#### b. Array ကို Copy ကူးခြင်း
```bash
copy_fruits=("${fruits[@]}")
```

#### c. Command Output ကို Array အဖြစ်သိမ်းခြင်း
```bash
files=( *.txt )  # လက်ရှိအောက်ရှိ .txt ဖိုင်များ
```

---

### 8. **အမှားများနှင့် သတိပြုရန်**
- **Space ပါသော String များ** - ကိုးကားမှုမပါလျှင် အမှားဖြစ်နိုင်  
  ```bash
  names=("John Doe" "Alice Smith")  # မှန်း
  names=(John Doe Alice Smith)      # 4 elements ဖြစ်သွား
  ```
- **Associative Array များကို မကြေငြာဘဲသုံးခြင်း**  
  `declare -A` ဖြင့်ကြေငြာရန် လိုအပ်

---

### 9. **နမူနာ Script**
```bash
#!/bin/bash

# Indexed Array
colors=("Red" "Green" "Blue")
colors+=("Yellow")

echo "First color: ${colors[0]}"
echo "All colors: ${colors[@]}"

# Loop through colors
for color in "${colors[@]}"; do
  echo "Color: $color"
done

# Associative Array
declare -A person
person[name]="Bob"
person[age]=35

echo "Name: ${person[name]}"
echo "Age: ${person[age]}"
```

---

Array များသည် Bash Scripting တွင် Data များကို စနစ်တကျ စီမံရာတွင် အလွန်အသုံးဝင်ပါသည်။ လက်တွေ့တွင် ကိုယ်တိုင်စမ်းသပ်ရင်း ကျွမ်းကျင်အောင် လေ့ကျင့်ပါ။

---
Bash script တွင် array ဆိုသည်မှာ variable တစ်ခုထက်ပိုသော value များကို သိမ်းဆည်းရန် အသုံးပြုသော data structure တစ်ခုဖြစ်သည်။ Array များကို index များဖြင့် ခွဲခြားသတ်မှတ်ထားပြီး၊ index များသည် 0 မှစတင်သည်။ Bash script တွင် array များကို အောက်ပါအတိုင်း သတ်မှတ်နိုင်သည်။

### 1. Array ကို သတ်မှတ်ခြင်း
Bash script တွင် array ကို အောက်ပါအတိုင်း သတ်မှတ်နိုင်သည်။

```bash
my_array=("value1" "value2" "value3")
```

သို့မဟုတ်

```bash
my_array[0]="value1"
my_array[1]="value2"
my_array[2]="value3"
```

### 2. Array ထဲမှ value များကို ဖတ်ခြင်း
Array ထဲမှ value များကို ဖတ်ရန် `${array_name[index]}` ကို အသုံးပြုနိုင်သည်။

```bash
echo ${my_array[0]}  # value1 ကို ထုတ်ပေးမည်
echo ${my_array[1]}  # value2 ကို ထုတ်ပေးမည်
echo ${my_array[2]}  # value3 ကို ထုတ်ပေးမည်
```

### 3. Array ထဲမှ value အားလုံးကို ဖတ်ခြင်း
Array ထဲမှ value အားလုံးကို ဖတ်ရန် `${array_name[@]}` သို့မဟုတ် `${array_name[*]}` ကို အသုံးပြုနိုင်သည်။

```bash
echo ${my_array[@]}  # value1 value2 value3 ကို ထုတ်ပေးမည်
```

### 4. Array ထဲမှ value များ၏ အရေအတွက်ကို ရယူခြင်း
Array ထဲမှ value များ၏ အရေအတွက်ကို `${#array_name[@]}` ဖြင့် ရယူနိုင်သည်။

```bash
echo ${#my_array[@]}  # 3 ကို ထုတ်ပေးမည်
```

### 5. Array ထဲမှ value များကို loop ဖြင့် ဖတ်ခြင်း
Array ထဲမှ value များကို loop ဖြင့် ဖတ်ရန် `for` loop ကို အသုံးပြုနိုင်သည်။

```bash
for value in "${my_array[@]}"
do
  echo $value
done
```

### 6. Array ထဲမှ value များကို ပြင်ဆင်ခြင်း
Array ထဲမှ value များကို ပြင်ဆင်ရန် index ကို အသုံးပြုနိုင်သည်။

```bash
my_array[1]="new_value2"
echo ${my_array[1]}  # new_value2 ကို ထုတ်ပေးမည်
```

### 7. Array ထဲမှ value များကို ဖျက်ခြင်း
Array ထဲမှ value များကို `unset` command ဖြင့် ဖျက်နိုင်သည်။

```bash
unset my_array[1]
echo ${my_array[@]}  # value1 value3 ကို ထုတ်ပေးမည်
```

### 8. Array ထဲမှ value များကို ပေါင်းထည့်ခြင်း
Array ထဲမှ value များကို ပေါင်းထည့်ရန် `+=` operator ကို အသုံးပြုနိုင်သည်။

```bash
my_array+=("value4")
echo ${my_array[@]}  # value1 value2 value3 value4 ကို ထုတ်ပေးမည်
```

### 9. Associative Array (Key-Value Pair)
Bash 4.0 နှင့် အထက်တွင် associative array ကို အသုံးပြုနိုင်သည်။ Associative array သည် key-value pair များကို သိမ်းဆည်းရန် အသုံးပြုသည်။

```bash
declare -A my_assoc_array
my_assoc_array["key1"]="value1"
my_assoc_array["key2"]="value2"

echo ${my_assoc_array["key1"]}  # value1 ကို ထုတ်ပေးမည်
echo ${my_assoc_array["key2"]}  # value2 ကို ထုတ်ပေးမည်
```

### 10. Array ထဲမှ value များကို sort လုပ်ခြင်း
Array ထဲမှ value များကို sort လုပ်ရန် `sort` command ကို အသုံးပြုနိုင်သည်။

```bash
sorted_array=($(for value in "${my_array[@]}"; do echo $value; done | sort))
echo ${sorted_array[@]}
```

### 11. Array ထဲမှ value များကို reverse sort လုပ်ခြင်း
Array ထဲမှ value များကို reverse sort လုပ်ရန် `sort -r` command ကို အသုံးပြုနိုင်သည်။

```bash

reverse_sorted_array=($(for value in "${my_array[@]}"; do echo $value; done | sort -r))
echo ${reverse_sorted_array[@]}

```

### 12. Array ထဲမှ value များကို unique လုပ်ခြင်း
Array ထဲမှ value များကို unique လုပ်ရန် `sort -u` command ကို အသုံးပြုနိုင်သည်။

```bash

unique_array=($(for value in "${my_array[@]}"; do echo $value; done | sort -u))
echo ${unique_array[@]}

```


---

# 📝 **Bash Associative Arrays (Key-Value Pairs)**
In Bash, associative arrays allow you to store data in **key-value pairs**, similar to dictionaries in Python or hash maps in other languages.  

### **🔹 Declaring an Associative Array**
Associative arrays are not enabled by default. You must explicitly declare them using `declare -A`.  
```bash
declare -A my_array
```

### **🔹 Assigning Values**
You can assign values using key-value pairs.  
```bash
my_array["name"]="Kyaw"
my_array["age"]=25
my_array["city"]="Yangon"
```

### **🔹 Accessing Values**
Use the key to retrieve the corresponding value.  
```bash
echo "Name: ${my_array["name"]}"
echo "Age: ${my_array["age"]}"
echo "City: ${my_array["city"]}"
```

### **🔹 Looping Through an Associative Array**
Use `!` to loop through keys and retrieve values.  
```bash
for key in "${!my_array[@]}"; do
    echo "$key => ${my_array[$key]}"
done
```

### **🔹 Checking If a Key Exists**
```bash
if [[ -v my_array["name"] ]]; then
    echo "Key 'name' exists!"
fi
```

### **🔹 Removing a Key**
```bash
unset my_array["age"]
```

### **🔹 Getting All Keys & Values**
```bash
echo "Keys: ${!my_array[@]}"
echo "Values: ${my_array[@]}"
```

### **🔹 Example: Storing & Retrieving Data**
```bash
#!/bin/bash

# Declare an associative array
declare -A user_info

# Assign values
user_info["username"]="kyaw_dev"
user_info["email"]="kyaw@example.com"
user_info["role"]="admin"

# Print values
echo "Username: ${user_info["username"]}"
echo "Email: ${user_info["email"]}"
echo "Role: ${user_info["role"]}"

# Loop through all key-value pairs
echo "User Info:"
for key in "${!user_info[@]}"; do
    echo "$key: ${user_info[$key]}"
done
```

### **🔹 Important Notes**
1. Associative arrays only work in **Bash 4.0+** (Check your version with `bash --version`).
2. You **must declare** an associative array with `declare -A`.
3. Unlike indexed arrays (`array=(val1 val2 val3)`), keys in associative arrays can be **strings**.

---

