

### **Bash & Zsh Version of Number Guessing Game**  
(✅ **Bash & Zsh two-in-one version** – Both work the same way)  

---

## **Bash/Zsh Code (Save as `guess.sh`)**


```bash
#!/bin/bash

WINNINGNUM=$(( RANDOM % 10 + 1 )) # 1 to 10
GAMELEFT=5
ATTEMPTS=0

GUESSSET=() # Unique guess list
GUESSARRAY=() # Ordered guess list
declare -A GUESSCOUNT # Frequency tracking

echo "You have $GAMELEFT chances to guess the number between 1 to 10."

for ((CURRENTNUM=1; CURRENTNUM<=GAMELEFT; CURRENTNUM++)); do
    read -p "Game $CURRENTNUM: Enter your guess number = " GUESS

    # Check if input is a number
    if ! [[ "$GUESS" =~ ^[0-9]+$ ]]; then
        echo "❌ Invalid input! Please enter a valid number."
        continue
    fi

    ((ATTEMPTS++))

    # Add to ordered list
    GUESSARRAY+=("$GUESS")

    # Add to unique list
    if [[ ! " ${GUESSSET[@]} " =~ " $GUESS " ]]; then
        GUESSSET+=("$GUESS")
    fi

    # Count occurrences
    ((GUESSCOUNT["$GUESS"]++))

    if [[ "$GUESS" -eq "$WINNINGNUM" ]]; then
        echo "🎉 Congratulations! You guessed the correct number $WINNINGNUM in $ATTEMPTS attempts!"
        break
    elif [[ "$GUESS" -lt "$WINNINGNUM" ]]; then
        echo "📉 Too low! Try again."
    else
        echo "📈 Too high! Try again."
    fi
done

# **Game Over Logic**
if (( ATTEMPTS >= GAMELEFT )); then
    echo "😢 Game Over! The correct number was $WINNINGNUM."
fi

# **Results Analysis**
echo -e "\n📊 Game Result Analysis:"
echo "🔹 Your unique guesses (unordered) = ${GUESSSET[*]}"
echo "🔹 Your guesses in order = ${GUESSARRAY[*]}"
echo "🔹 Guess frequency:"
for key in "${!GUESSCOUNT[@]}"; do
    echo "  🔸 Number $key guessed ${GUESSCOUNT[$key]} time(s)"
done
```

---

## **Usage**
✅ **Run with Bash or Zsh**  

```bash
bash guess.sh   # If using Bash
zsh guess.sh    # If using Zsh
```

✅ **Or make it executable & run directly**
```bash
chmod +x guess.sh
./guess.sh
```

---

## **🔍 ဘာတွေပဲပြင်လိုက်လဲ?**
✔ **`$RANDOM % 10 + 1`** – Random number (1-10)  
✔ **Loop (for CURRENTNUM in 1..GAMELEFT)** – Game chances loop  
✔ **Check if input is a number (`[[ "$GUESS" =~ ^[0-9]+$ ]]`)**  
✔ **Array & Associative Array (Count guess frequency)**  
✔ **Store ordered guesses & unique guesses**  
✔ **Print final results after loop ends**  

---

## **Example Output**


```shell
You have 5 chances to guess the number between 1 to 10.
Game 1: Enter your guess number = 3
📉 Too low! Try again.
Game 2: Enter your guess number = 7
📉 Too low! Try again.
Game 3: Enter your guess number = 9
📈 Too high! Try again.
Game 4: Enter your guess number = 8
🎉 Congratulations! You guessed the correct number 8 in 4 attempts!

📊 Game Result Analysis:
🔹 Your unique guesses (unordered) = 3 7 9 8
🔹 Your guesses in order = 3 7 9 8
🔹 Guess frequency:
  🔸 Number 3 guessed 1 time(s)
  🔸 Number 7 guessed 1 time(s)
  🔸 Number 9 guessed 1 time(s)
  🔸 Number 8 guessed 1 time(s)
```

---
### **🔍 ပြင်လိုက်တဲ့ အချက်တွေ (Details with Examples)**  

ဒီ Bash & Zsh version ကို **Python version** နဲ့ **တူအောင်** ပြုပြင်ပေးထားပြီး **Bash/Zsh တွေမှာ အလုပ်လုပ်အောင် ပြောင်းထားတဲ့ Logic တွေ** ပါပါတယ်။ **တစ်ခုချင်းစီကို Example နဲ့ ရှင်းပြပေးမယ်။**  

---

## **1️⃣ Random Number Generation (Python → Bash)**  
Python မှာ `random.randint(1, 10)` ကိုသုံးတယ်။  
Bash မှာ **`$RANDOM`** ကိုသုံးပြီး **Modulo (`%`)** ဖြတ်တာဖြင့် **1 to 10** ကြားထွက်အောင်လုပ်မယ်။  

### **📌 Python Version**
```python
WINNINGNUM = random.randint(1, 10)
```
### **📌 Bash/Zsh Version**
```bash
WINNINGNUM=$(( RANDOM % 10 + 1 ))
```
**👉 Explanation:**  
- `$RANDOM` ဟာ **0 - 32767** ကြားက **အလိုကျဂဏန်း** ထုတ်ပေးနိုင်တယ်။  
- `% 10` နဲ့ **0 - 9** ဖြစ်အောင် **Modulo Operation** ပြုလုပ်မယ်။  
- `+ 1` နဲ့ **1 - 10** ဖြစ်အောင် **Offset** ပေးလိုက်မယ်။  

---

## **2️⃣ Loop for Game Attempts (Python `for` → Bash `for`)**  
Python မှာ `for` loop ကို `range(1, GAMELEFT + 1)` နဲ့သုံးတယ်။  
Bash မှာ `for ((...))` syntax ကိုသုံးပြီး **same logic** ဖြင့်ပြုလုပ်မယ်။  

### **📌 Python Version**
```python
for CURRENTNUM in range(1, GAMELEFT + 1):
```
### **📌 Bash/Zsh Version**
```bash
for ((CURRENTNUM=1; CURRENTNUM<=GAMELEFT; CURRENTNUM++)); do
```
**👉 Explanation:**  
- `CURRENTNUM=1` → Loop ကို **1 မှစတင်**  
- `CURRENTNUM<=GAMELEFT` → **GAMELEFT (5) ထိသာ run မယ်**  
- `CURRENTNUM++` → **Loop တစ်ခါစလှှတ်တိုင်း 1 တိုးမယ်**  

---

## **3️⃣ User Input Validation (Python `try-except` → Bash `if ! [[ ... ]]`)**  
Python မှာ `try-except` နဲ့ **number မဖြစ်ရင် exception** ကို handle တယ်။  
Bash မှာ **Regular Expression (Regex) `[0-9]+`** နဲ့ check လုပ်မယ်။  

### **📌 Python Version**
```python
try:
    GUESS = int(input("Enter your guess: "))
except ValueError:
    print("Invalid input! Enter a number.")
```
### **📌 Bash/Zsh Version**
```bash
read -p "Enter your guess: " GUESS

if ! [[ "$GUESS" =~ ^[0-9]+$ ]]; then
    echo "❌ Invalid input! Please enter a valid number."
    continue
fi
```
**👉 Explanation:**  
- `read -p "Enter your guess: " GUESS` → User input ကို GUESS ထဲသိမ်းမယ်  
- `[[ "$GUESS" =~ ^[0-9]+$ ]]` → **Regex check** (Only numbers allowed)  
- `! [[ ... ]]` → **Not condition** (number မဖြစ်ရင် `continue` ပြန်လုပ်မယ်)  

---

## **4️⃣ Checking Guess & Printing Hints (Python `if-elif` → Bash `if-elif`)**  
Python မှာ **if-elif-else** ကိုသုံးပြီး **guess ကို compare** လုပ်တယ်။  
Bash မှာ `if [[ ... ]]; then ... elif [[ ... ]]; then ... else` ကိုသုံးမယ်။  

### **📌 Python Version**
```python
if GUESS == WINNINGNUM:
    print("🎉 Correct!")
elif GUESS < WINNINGNUM:
    print("📉 Too low!")
else:
    print("📈 Too high!")
```
### **📌 Bash/Zsh Version**
```bash
if [[ "$GUESS" -eq "$WINNINGNUM" ]]; then
    echo "🎉 Congratulations! You guessed the correct number!"
    break
elif [[ "$GUESS" -lt "$WINNINGNUM" ]]; then
    echo "📉 Too low! Try again."
else
    echo "📈 Too high! Try again."
fi
```
**👉 Explanation:**  
- `[[ "$GUESS" -eq "$WINNINGNUM" ]]` → **Equal Check** (`-eq`)  
- `[[ "$GUESS" -lt "$WINNINGNUM" ]]` → **Less Than Check** (`-lt`)  
- `[[ "$GUESS" -gt "$WINNINGNUM" ]]` → **Greater Than Check** (`-gt`)  

---

## **5️⃣ Storing Unique & Ordered Guesses (Python List/Set → Bash Arrays)**  
Python မှာ  
✔ `set()` ကို **Unique guesses** သိမ်းဖို့သုံးတယ်  
✔ `list()` ကို **Ordered guesses** သိမ်းဖို့သုံးတယ်  

Bash မှာ  
✔ `GUESSSET=()` → **Unique guesses**  
✔ `GUESSARRAY=()` → **Ordered guesses**  

### **📌 Python Version**
```python
GUESSSET.add(GUESS)  # Unique guesses
GUESSARRAY.append(GUESS)  # Ordered guesses
```
### **📌 Bash/Zsh Version**
```bash
GUESSARRAY+=("$GUESS")  # Store ordered guesses

if [[ ! " ${GUESSSET[@]} " =~ " $GUESS " ]]; then
    GUESSSET+=("$GUESS")  # Store unique guesses
fi
```
**👉 Explanation:**  
- `+=("$GUESS")` → Bash မှာ **Array ထဲထပ်ထည့်ဖို့**  
- `if [[ ! " ${GUESSSET[@]} " =~ " $GUESS " ]]` → **Unique Check**  

---

## **6️⃣ Counting Guess Frequency (Python `Counter` → Bash `Associative Array`)**  
Python မှာ **Counter()** နဲ့ **guess count** တွေ သိမ်းတယ်။  
Bash မှာ **Associative Array (`declare -A`)** ကိုသုံးမယ်။  

### **📌 Python Version**
```python
from collections import Counter
GUESSCOUNT = Counter(GUESSARRAY)  # Count guess frequency
```
### **📌 Bash/Zsh Version**
```bash
declare -A GUESSCOUNT  # Declare associative array
((GUESSCOUNT["$GUESS"]++))  # Increment count
```
**👉 Explanation:**  
- `declare -A GUESSCOUNT` → **Bash မှာ dictionary တူတဲ့ structure**
- `((GUESSCOUNT["$GUESS"]++))` → **Count တိုးမယ်**  

---

## **7️⃣ Printing Final Results (Python `print` → Bash `echo`)**  
Python မှာ `print()` နဲ့ ပြပေးတယ်။  
Bash မှာ `echo` နဲ့ **Loop ဖြင့် frequency print** လုပ်မယ်။  

### **📌 Python Version**
```python
print(f"Your guesses: {GUESSARRAY}")
print(f"Guess Frequency: {GUESSCOUNT}")
```
### **📌 Bash/Zsh Version**
```bash
echo "🔹 Your guesses in order = ${GUESSARRAY[*]}"
echo "🔹 Guess frequency:"
for key in "${!GUESSCOUNT[@]}"; do
    echo "  🔸 Number $key guessed ${GUESSCOUNT[$key]} time(s)"
done
```
**👉 Explanation:**  
- `"${GUESSARRAY[*]}"` → **Ordered guesses print**  
- `for key in "${!GUESSCOUNT[@]}"; do ... done` → **Loop through dictionary**  

---

## **✅ Summary (Key Changes)**
| **Python Feature** | **Bash/Zsh Equivalent** |
|--------------------|------------------------|
| `random.randint(1, 10)` | `$(( RANDOM % 10 + 1 ))` |
| `for` loop | `for ((...))` |
| `try-except` | `if ! [[ ... ]]` |
| `set()` | `GUESSSET=()` |
| `list.append()` | `GUESSARRAY+=("$GUESS")` |
| `Counter()` | `declare -A GUESSCOUNT` |

---


## Python Script Guess Game

---

## **✅ Updated Code (Corrected Version)**

```python
import random
from array import array
from collections import Counter

WINNINGNUM = random.randint(1, 10)

GAMELEFT = 5
ATTEMPTS = 0

GUESSSET = set()  # Set for unique guesses
GUESSARRAY = array("i", [])  # Array for ordered guesses

print(f"You have {GAMELEFT} chances to guess the number between 1 to 10.")

for CURRENTNUM in range(1, GAMELEFT + 1):
    try:
        GUESS = int(input(f"Game {CURRENTNUM}: Enter your guess number = "))

        ATTEMPTS += 1

        # ✅ Guess ကို Set နဲ့ Array ထဲထည့်မယ်
        GUESSSET.add(GUESS)  
        GUESSARRAY.append(GUESS)  

        if GUESS == WINNINGNUM:
            print(f"🎉 Congratulations! You guessed the correct number {WINNINGNUM} in {ATTEMPTS} attempts!")
            break  # 🛑
        elif GUESS < WINNINGNUM:
            print("📉 Too low! Try again.")
        else:
            print("📈 Too high! Try again.")

    except ValueError:
        print("❌ Invalid input! Please enter a valid number.")

# **Game Over Logic**
if ATTEMPTS >= GAMELEFT:
    print(f"😢 Game Over! You've used all your chances. The correct number was {WINNINGNUM}.")

# ✅ Store Results
GUESSTUPLE = tuple(GUESSARRAY)
GUESSCOUNT = Counter(GUESSARRAY)

# ✅ Print Results
print("\n📊 Game Result Analysis:")
print(f"🔹 Your unique guesses (unordered) = {GUESSSET}")
print(f"🔹 Your guesses in order = {GUESSTUPLE}")
print(f"🔹 Guess frequency = {GUESSCOUNT}")
```

---

## **🔍 ဘာပြင်လိုက်သလဲ?**
1. **Loop ထဲမှာ**  
   ✅ `GUESSSET.add(GUESS)` -> Unique guess များကို Set ထဲထည့်  
   ✅ `GUESSARRAY.append(GUESS)` -> Guess order ကို Array ထဲထည့်  
   
2. **Loop ပြီးရင်**  
   ✅ `tuple(GUESSARRAY)` → Array ကို Tuple အနေနဲ့ပြောင်း  
   ✅ `Counter(GUESSARRAY)` → Number frequency ကို တွက်  

---

## **📌 Output Example**
```shell
You have 5 chances to guess the number between 1 to 10.
Game 1: Enter your guess number = 3
📉 Too low! Try again.
Game 2: Enter your guess number = 7
📉 Too low! Try again.
Game 3: Enter your guess number = 9
📈 Too high! Try again.
Game 4: Enter your guess number = 8
🎉 Congratulations! You guessed the correct number 8 in 4 attempts!

📊 Game Result Analysis:
🔹 Your unique guesses (unordered) = {8, 9, 3, 7}
🔹 Your guesses in order = (3, 7, 9, 8)
🔹 Guess frequency = Counter({3: 1, 7: 1, 9: 1, 8: 1})
```


---

