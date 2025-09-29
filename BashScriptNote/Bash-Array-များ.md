

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
