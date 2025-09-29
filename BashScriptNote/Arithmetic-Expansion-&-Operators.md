
### Arithmetic Expansion & Operators
---

**Arithmetic Expansion** ဆိုတာက **Shell ထဲမှာ Mathematical Calculations** (ဂဏန်း တွက်ချက်မှု) တွေကို လုပ်ဆောင်ပေးတဲ့ နည်းလမ်းတစ်ခုပါ။ Shell ထဲမှာ **$((expression))** ဆိုတဲ့ Syntax ကို အသုံးပြုပြီး ဂဏန်းတွေကို တွက်ချက်နိုင်တယ်။

---

## **Arithmetic Expansion Syntax**
```bash
$((expression))
```

- **`$((...))`** သည် Arithmetic Expansion ကို ပြုလုပ်ရန် အသုံးပြုသည်။
- **`expression`** ထဲမှာ **Mathematical Operators** တွေကို သုံးနိုင်တယ်။

---

## **Arithmetic Operators in Bash**
Bash မှာ အသုံးပြုနိုင်တဲ့ **Arithmetic Operators** တွေက အောက်ပါအတိုင်းပါ:

| Operator | Description                 | Example           | Result   |
|----------|-----------------------------|-------------------|----------|
| `+`      | Addition                   | `5 + 3`          | `8`      |
| `-`      | Subtraction                | `5 - 3`          | `2`      |
| `*`      | Multiplication             | `5 * 3`          | `15`     |
| `/`      | Division                   | `5 / 2`          | `2` (Integer Division) |
| `%`      | Modulus (Remainder)        | `5 % 2`          | `1`      |
| `**`     | Exponentiation (Power)     | `5 ** 2`         | `25`     |
| `++`     | Increment (Add 1)          | `((x++))`         | Increment `x` by 1 |
| `--`     | Decrement (Subtract 1)     | `((x--))`         | Decrement `x` by 1 |
| `+=`     | Add and Assign             | `x += 3`         | Add `3` to `x` |
| `-=`     | Subtract and Assign        | `x -= 3`         | Subtract `3` from `x` |

---

## **Examples of Arithmetic Expansion**

### **1. Basic Calculations**
```bash
result=$((5 + 3))
echo $result
# Output: 8
```

### **2. Using Variables**
```bash
a=10
b=5
sum=$((a + b))
echo $sum
# Output: 15
```

### **3. Modulus (Remainder)**
```bash
remainder=$((10 % 3))
echo $remainder
# Output: 1
```

### **4. Increment/Decrement**
```bash
x=5
((x++))
echo $x
# Output: 6

((x--))
echo $x
# Output: 5
```

### **5. Complex Expressions**
```bash
result=$(( (5 + 3) * 2 - 1 ))
echo $result
# Output: 15
```

---

## **Comparison Operators in Arithmetic Expansion**
Bash Arithmetic Expansion မှာ **Comparison Operators** တွေကို သုံးပြီး Comparison လုပ်နိုင်တယ်။

| Operator | Description             | Example         | Result   |
|----------|-------------------------|-----------------|----------|
| `==`     | Equal To               | `5 == 3`       | `false`  |
| `!=`     | Not Equal To           | `5 != 3`       | `true`   |
| `<`      | Less Than              | `5 < 3`        | `false`  |
| `>`      | Greater Than           | `5 > 3`        | `true`   |
| `<=`     | Less Than or Equal To  | `5 <= 3`       | `false`  |
| `>=`     | Greater Than or Equal To | `5 >= 3`    | `true`   |

### **Example**
```bash
a=10
b=20
if ((a < b)); then
    echo "a is less than b"
else
    echo "a is not less than b"
fi
# Output: a is less than b
```

---

## **Practical Usages**
1. **Math Operations in Scripts**
   ```bash
   radius=7
   area=$((3 * radius ** 2))
   echo "Circle Area: $area"
   # Output: Circle Area: 147
   ```

2. **Looping with Arithmetic Expansion**
   ```bash
   for ((i=1; i<=5; i++)); do
       echo "Count: $i"
   done
   ```

3. **Condition Checking**
   ```bash
   age=18
   if ((age >= 18)); then
       echo "You are an adult."
   else
       echo "You are underage."
   fi
   ```

---
