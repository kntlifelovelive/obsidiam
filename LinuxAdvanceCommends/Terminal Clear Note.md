## **Terminal Clear Commands Notes**

### 1. **`printf "\ec"`**  
- **Description**: Terminal ကို **reset** လုပ်ပြီး buffer history အားလုံးကို ဖျက်ပစ်တယ်။  
- **Use Case**: Terminal ကို clean slate အနေအထားသို့ ပြန်ထားချင်တယ်။  
- **Example**:
```bash
printf "\ec"
  
```

---

### 2. **`printf "\x1Bc"`**  
- **Description**: **ANSI escape sequence** ကို အသုံးပြုပြီး **Terminal reset** လုပ်တယ်။  
- **Equivalent To**: `printf "\ec"`  
- **Use Case**: Terminal ကို **reset** လုပ်ပြီး စနေရာမှ စချင်တယ်။  
- **Example**:
  ```bash
  printf "\x1Bc"
  ```

---

#### 3. **`clear`**  
- **Description**: Terminal screen မှာ ဖော်ပြထားသမျှကိုဖျက်ပြီး ပုံမှန် shell prompt ကို ပြတယ်။  
- **Use Case**: Screen ကို သာသာလွန်ပြီး **buffer history** မဖျက်ချင်တဲ့အခါသုံးတယ်။  
- **Example**:
  ```bash
  clear
  ```

---

### 4. **`reset`**  
- **Description**: Terminal **settings** များအားလုံးကို reset လုပ်တယ်။ ဒီမှာ **screen clear** လုပ်ရုံမကဘဲ terminal mode, keybindings, font styles စသဖြင့် တစ်ပြိုင်နက်ပြင်ဆင်ပေးတယ်။  
- **Use Case**: Terminal settings တစ်ခုခု error ဖြစ်နေတဲ့အခါ သုံးတယ်။  
- **Example**:
  ```bash
  reset
  ```

---

### **Quick Comparison Table**

| Command         | Buffer Clear | Terminal Reset | Speed | Use Case                           |
|------------------|-------------|----------------|-------|------------------------------------|
| `printf "\ec"`   | ✅           | ✅              | Fast  | Full clear, reset terminal.      |
| `printf "\x1Bc"` | ✅           | ✅              | Fast  | Alternative to `\ec`.            |
| `clear`          | ❌           | ❌              | Fast  | Clear screen only.               |
| `reset`          | ✅           | ✅              | Slow  | Fix terminal issues completely.  |


**နောက်ထပ် အသုံးပြုရန်**:  
- Terminal settings အပြင်ဖျက်သိမ်းလိုချင်ရင် `reset` သုံးပါ။  
- Screen ဖယ်ရှားရုံအတွက် `clear` ။  


---
---
---


Terminal မှာ **`clear`** နဲ့ reset commands များကို အသုံးပြုတဲ့အခါ၊ တချို့ command တွေဟာ **terminal environment** ကို ပြောင်းလဲနိုင်ပြီး **history** များကိုလည်း ဖျက်နိုင်ပါတယ်။ ဤသို့နားလည်ရန် **clear commands** များကို **note** အဖြစ် သိမ်းထားဖို့အတွက်၊ ဤနေရာမှာ **တိကျတစ်ခုတည်း** သေချာထားပေးမည် ဖြစ်ပါတယ်။

### **Clear Commands Notes** (Terminal မှာ မလုပ်သင့်တဲ့ Command များ)

#### 1. **`reset`** 
- **Explanation**: 
  - Terminal **settings** နဲ့ **mode** များအားလုံးကို **reset** လုပ်ပြီး terminal ကို **initial state** ပြန်ထုတ်လွှင့်တယ်။
  - တစ်ခါတလေ **file permissions** နှင့် **configuration** များပြောင်းလဲနိုင်သေးတယ်။
  
- **Usage**:
  ```bash
  reset
  ```

#### 2. **`printf "\ec"`** 
- **Explanation**:
  - **DEC Private Mode Reset** ဖြစ်ပြီး **terminal screen** နှင့် **buffer** အားလုံးကို reset လုပ်တယ်။
  - **terminal buffer** များကို **reset** လုပ်နိုင်ပြီး **settings** များပြောင်းလဲနိုင်တယ်။

- **Usage**:
  ```bash
  printf "\ec"
  ```

### 3. **`printf "\x1Bc"`**
- **Explanation**:
  - **ANSI escape sequence** ဖြစ်ပြီး **reset terminal** လုပ်တာဖြစ်ပါတယ်။
  - **terminal buffer** များကို reset လုပ်ပြီး **cursor position** များကို ရှာနိုင်ပါတယ်။

- **Usage**:
  ```bash
  printf "\x1Bc"
  ```

### 4. **`clear`** / `printf "\033[H\033[2J"`
- **Explanation**:
  - **clear** က **screen** ကိုသာ ဖျက်ပြီး **terminal buffer** မဖျက်ပါဘူး။
  - **`printf "\033[H\033[2J"`** က **screen clear** command တစ်ခု ဖြစ်ပြီး **buffer** မဖျက်ပါ။

- **Usage**:
```bash
clear
# or
printf "\033[H\033[2J"

```

---

### **Summary**

| Command              | Function                         | Notes                                   |
|----------------------|----------------------------------|-----------------------------------------|
| `reset`              | Resets terminal settings, buffer, and mode | Can change configuration, affects environment |
| `printf "\ec"`       | Reset terminal screen and buffer | Resets terminal and buffer              |
| `printf "\x1Bc"`     | Reset terminal via ANSI escape  | Equivalent to `printf "\ec"`            |
| `clear`              | Clears screen only               | Does not affect buffer                  |
| `printf "\033[H\033[2J"` | Clears screen                   | Does not affect terminal buffer         |

---
### ထပ်ရှင်းလင်းချက် note

### 1. `reset`
- **Explanation**: Resets terminal settings, buffer, and environment.
- **Usage**:

```bash

reset

```

### 2. `printf "\ec"`

- **Explanation**: Resets terminal screen and buffer.
- **Usage**:

```bash

printf "\ec"
  
```

## 3. `printf "\x1Bc"`
- **Explanation**: Equivalent to `printf "\ec"`, resets terminal buffer and settings.
- **Usage**:
```bash

printf "\x1Bc"
  
```

## 4. `clear`
- **Explanation**: Clears terminal screen but does not affect buffer.
- **Usage**:

```bash

clear

```

## 5. `printf "\033[H\033[2J"`
- **Explanation**: Clears screen, does not affect terminal buffer.
- **Usage**:
```bash
  
printf "\033[H\033[2J"

```

---



